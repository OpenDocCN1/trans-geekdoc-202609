

# 特色示例

```mat
curDir = pwd;
unzip('MerchData.zip');
imds = imageDatastore('MerchData', ...
'IncludeSubfolders',imds,true, ...
'LabelSource','foldername');
[imdsTrain,imdsValidation] = splitLabel(imds,0.7,'randomized');
```

# 替换层

预训练网络的全连接层和分类层并未配置为 1000 类。对于 ResNet-18，这两个层（`fc1000` 和 `ClassificationLayer_predictions`）包含了如何将网络提取的特征组合为类别概率和预测标签的信息。这两个层必须针对新的分类问题进行微调。除了预训练网络的所有层外，最后两层都需要重新调整。

```mat
lgraph = LayerGraph(snet)
lgraph = LayerGraphWithProperties(
Layers: {[71x1 nnet.cnn.Layer]}
Connections: {[78x2 table]}
InputNames:{data'}
OutputNames:{ClassificationLayer_predictions})
```

numClasses = num(category(classes))
numClasses = 5

```mat
newLearnableLayer = fullyConnectedLayer(numClasses,
'Name','new fc',
'WeightLearnRateFactor',10,
'BiasLearnRateFactor',10);
lgraph = replaceLayer(lgraph, 'fc1000',newLearnableLayer)
newLayer = classificationLayer('Name','new.classout')
lgraph = replaceLayer(lgraph,'ClassificationLayer_predictions',newLayer);
```

# 训练网络

网络需要尺寸为 224x22x3 的输入图像，但图像的大小不同。使用增强图像数据存储（augmented image datastore）自动调整训练图像的大小。指定在训练图像上执行额外的增强操作，例如沿垂直轴随机翻转图像，并沿水平和垂直方向随机平最多 30 像素。数据增强有助于防止网络过拟合并记住训练图像的精确细节。

```mat
pixelRange = [-30 30];
imageAugmenter = augmenter('RandReflection',true,
'RandTranslation',pixelRange,
'RandRotation',pixelRange);
```

要在不进行进一步数据增强的情况下自动调整验证图像的大小，可以使用未指定任何预处理操作的增强图像数据存储。

```mat
augdsTrain = augmentedImageDatastore(inputSize(2),imdsTrain, ...
'DataAugmentation',imageAugmenter);
augdsValidation = augmentedImageDatastore(inputSize(2),imdsValidation);
```

# 使用量化 DAG 网络在 FPGA 上分类图像

选择训练选项。对于迁移学习，保留预训练浅层的特征（迁移权重）。为了降低迁移层的速度，将初始学习率设置为小值。指定小批量大小和验证数据。软件会在训练期间每隔指定的频率验证网络。

```mat
options = trainingOptions('sgdm',
  'MiniBatchSize',10,
  'MaxEpochs',6,
  'InitialLearnRate',1e-4,
  'Shuffle','every-epoch',
  'ValidationData',augmentsValidation,
  'ValidationFrequency',3,
  'Verbose',false,
  'Plots','training-progress')
```

训练连接迁移层和新层的网络。默认情况下，如果有 GPU（Parallel Computing Toolbox）和一个支持的 GPU 设备，`trainNetwork` 将使用 GPU。更多信息，请参阅“各版本的 GPU 支持”（Parallel Computing Toolbox）。否则，可以使用 `trainOptions` 的 'ExecutionEnvironment' 名称值对参数来指定执行环境。

```mat
netTransfer = trainNetwork(augmentsTrain,Lgraph,options)
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_228_0.png)

# 量化网络

创建一个量化对象并指定要量化的网络。

```mat
dlquantObj = dlquantizer(netTransfer, 'ExecutionEnvironment', 'FPGA');
```

# 校准量化对象

使用 `calibrate` 函数使用输入运行网络并收集范围。`calibrate` 函数运行并收集卷积层和全连接层权重的动态范围以及网络所有层激活值的动态范围。`calibrate` 函数返回一个表格。表格的每一行包含量化网络可学习参数的范围信息。

```mat
dquantobj.calibrate(augTrain)
```

| 优化名称 | 网络名称 | 可学习 / 激活值 | 数值 |
| --- | --- |--- | --- |
| 'conv1 Weights' | 'bn1' | 'Weights' | -0.8605 |
| 'conv1 Bias' | 'bn1' | 'Bias' | -0.6676 |
| 'res2a2a Weights' | 'bn2a2a' | 'Weights' | -0.4034 |
| 'res2a2a Bias' | 'bn2a2a' | 'Bias' | -0.7954 |
| 'res2a2b Weights' | 'bn2a2b' | 'Weights' | -0.7585 |
| 'res2a2b Bias' | 'bn2a2b' | 'Bias' | -1.1606 |
| 'conv2b Weights' | 'bn2b' | 'Weights' | -0.3244 |
| 'conv2b Bias' | 'bn2b' | 'Bias' | -1.1616 |
| 'res2b3 Weights' | 'bn2b3' | 'Weights' | -0.1736 |
| 'res2b3 Bias' | 'bn2b3' | 'Bias' | -0.1942 |
| 'res3a Weights' | 'bn3a' | 'Weights' | -0.5386 |
| 'res3a Bias' | 'bn3a' | 'Bias' | -0.5381 |
| 'res3c1 Weights' | 'bn3c1' | 'Weights' | -0.6457 |
| 'res3c1 Bias' | 'bn3c1' | 'Bias' | -0.6405 |
| | | 'Weights' | -0.9258 |

# 创建目标对象

使用 `dhdl.Target` 为你的目标设备创建一个带有自定义名称的目标对象，并一个将目标设备连接到主机的接口。接口选项有 JTAG 和以。设置 Xilinx Vivado 对象，使用：

```mat
hTarget = dhdl.Target('ToolName', 'Xilinx', 'ToolPath', 'C:\Xilinx\Vivado\2019.2\bin\vivado.', 'Interface', 'Ethernet');
```

使用 `dl.Workflow` 创建对象。创建对象时，指定网络和比特流名称。确保比特流名称与目标类型和 FPGA 匹配。在本例中，FPGA 板是 Xilinx ZCU102。比特流使用单一数据类型。

```mat
hw = dl.Workflow('Network', dquantobj, 'Bitstream', 'zcu102int8', 'Target', hTarget);
```

使用 `dl.Workflow` 对象的 `compile` 方法编译 netTransfer DAG 网络。你可以指定最大输入帧。

```mat
dn = hw.compile('InputFrameLimit');
```

# 使用量化网络在 FPGA 上分类

深度学习原型设计...网络包含以下层：

| # | 层 | 类型 | 描述 |
| --- | --- | --- | --- |
| 1 | 'data' | 输入 | 224×224×3 图像 |
| 2 | 'conv1' | 卷积 | 7×7 卷积，步长 [2] |
| 3 | 'bn1' | 归一化 | 64 通道 |
| 4 | 'conv1_relu' | ReLU | ReLU |
| 5 | 'pool1' | 最大池化 | 3×3 最大池化，步长 [2] |
| 6 | 'res2a2a' | 卷积 | 3×3 卷积，步长 [1] |
| 7 | 'bn2a2a' | 归一化 | 64 通道 |
| 8 | 'res2a2a_relu' | ReLU | ReLU |
| 9 | 'res2a2b' | 卷积 | 3×3 卷积，步长 [1] |
| 10 | 'bn2a2b' | 归一化 | 64 通道 |
| 11 | 加 | | 2 个输入的逐元素相加 |
| 12 | 'res2a_relu' | ReLU | ReLU |
| 13 | 'res2b_branch2a' | 卷积 | 3×3 卷积，步长 [1] |
| 14 | 'bn2b_2a' | 归一化 | 64 通道 |
| 15 | 'res2b_relu' | ReLU | ReLU |
| 16 | 'res2b_2b' | 卷积 | 3×3 卷积，步长 [1] |
| 17 | 'bn2b_2b' | 归一化 | 64 通道 |
| 18 | 加 | | |
| 19 | 'res2b_relu' | ReLU | ReLU |
| 20 | 'res3a2a' | 卷积 | 3×3 卷积，步长 [1] |
| 21 | 'bn3a2a' | 归一化 | 64 通道 |
| 22 | 'res3a_relu' | ReLU | ReLU |
| 23 | 'res3a2b' | 卷积 | 3×3 卷积，步长 [1] |
| 24 | 'bn3a2b' | 归一化 | 64 通道 |
| 25 | 加 | | |
| 26 | 'res2a_relu' | ReLU | ReLU |
| 27 | 'res3c1' | 卷积 | 3×3 卷积，步长 [1] |
| 28 | 'bn3c1' | 归一化 | 64 通道 |
| 29 | 'res2b_2a' | 卷积 | 3×3 卷积，步长 [1] |
| 30 | 'bn2b_2a' | 归一化 | 64 通道 |
| 31 | 'res2b_relu' | ReLU | ReLU |
| 32 | 'res2b_2b' | 卷积 | 3×3 卷积，步长 [1] |
| 33 | 'bn2b_2b' | 归一化 | 64 通道 |
| 34 | 加 | | |
| 35 | 'res2b_relu' | ReLU | ReLU |
| 36 | 'res3a2a' | 卷积 | 3×3 卷积，步长 [1] |
| 37 | 'bn3a2a' | 归一化 | 64 通道 |
| 38 | 'res3a_relu' | ReLU | ReLU |
| 39 | 'res3a2b' | 卷积 | 3×3 卷积，步长 [1] |
| 40 | 'bn3a2b' | 归一化 | 64 通道 |
| 41 | 加 | | |
| 42 | 'res3a_relu' | ReLU | ReLU |
| 43 | 'res3c1' | 卷积 | 3×3 卷积，步长 [1] |
| 44 | 'bn3c1' | 归一化 | 64 通道 |
| 45 | 'res3b_2a' | 卷积 | 3×3 卷积，步长 [1] |
| 46 | 'bn3b_2a' | 归一化 | 64 通道 |
| 47 | 'res3b_relu' | ReLU | ReLU |
| 48 | 'res3b_2b' | 卷积 | 3×3 卷积，步长 [1] |
| 49 | 'bn3b_2b' | 归一化 | 64 通道 |
| 50 | 加 | | |
| 51 | 'res3b_relu' | ReLU | ReLU |
| 52 | 'res4a_2a' | 卷积 | 3×3 卷积，步长 [1] |

