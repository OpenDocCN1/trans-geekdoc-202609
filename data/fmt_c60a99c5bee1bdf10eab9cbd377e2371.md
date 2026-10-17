
本示例展示了如何使用 Xilinx FPGA and SoC Support Package 训练、编译并部署一个具有量化 Alexnet 网络的 `dldl.Workflow` 对象。通过将网络层的权重、偏置和激活值量化为 8 位缩放整数类型，有助于减少深度网络的内存需求。使用 MATLAB™ 从目标设备检索预测结果。

# 所需产品

此示例需要：

- Deep Learning Toolbox™
- Deep Learning HDL Toolbox™
- Deep Learning Model Quantization Library
- Deep Learning HDL Support Package for Xilinx FPGA and SoC

## 加载预训练系列网络

要加载预训练系列网络 AlexNet：

```matlab
snet = alexnet;
```

要查看预训练系列网络的层，输入：

```matlab
analyzeNetwork(snet);
```

第一层图像输入层需要大小为 227x227x3 的输入图像，其中 3 是颜色通道数。

```matlab
inputSize = snet.Layers(1).InputSize;
inputSize = 1x3
227 227 3
```

# 定义训练和验证数据集

此示例使用 logos 数据集。该集合包含 320 张图像。创建一个 `augmentedImageDatastore` 用于训练和验证。

```matlab
curDir = pwd;
newDir = fullfile(matlabroot,'examples','deeplearning_shared','data','logos dataset.zip');
copyfile(newDir,curDir,'f');
unzip('logos_dataset.zip');
```

```matlab
imds = imageDatastore('logos dataset', ...
    'IncludeSubFolders',true,
    'LabelSource','fold');

[imdsTrain,imdsValidation] = splitEach(imds,'randomized');
```

# 替换最终层

预训练网络的最后三层配置为 1000 个类。这三层必须针对新的分类问题进行微调。从预训练网络中提取除最后层之外的所有层。

```matlab
layersTransfer = snet.Layers(1:end-3);
```

通过将最后三层替换为全连接层、softmax 层和分类输出层，将层转移到新的分类任务中。设置全连接层的大小与数据中类别的数量相同。

```matlab
numClasses = numel(categories(imdsTrain.Labels));
```

```matlab
layers = [
    layersTransfer
    fullyConnectedLayer(numClasses,'WeightLearnFactor',20,'BiasLearnFactor',20)
    softmaxLayer
    classificationLayer];
```

# 训练网络

网络需要大小为 227x227x3 的输入图像，但 datastore 中的图像大小不同。使用 augmented datastore 自动调整训练图像的大小。指定在训练图像上执行额外的增强操作，例如随机沿垂直轴翻转图像，并在水平和垂直方向上移动 30 像素。数据增强有助于防止网络过拟合并提取训练图像的细节。

```matlab
pixelRange = [-30 30];
imageAugmenter = imageDataAugmenter(
    RandReflection,'true',
    RandXdTranslation',pixelRange,
    RandYTranslation',pixelRange);
imgdsTrain = augmentedImageDataStore(inputSize(1:2),imdsTrain,
    'DataAugmentation',imageAugmenter);
```

要在不进行任何数据增强的情况下自动调整图像大小，请使用未指定预处理操作的增强图像 datastore。

```matlab
imgdsValidation = augmentedImageDataStore(inputSize(1.2));
```

指定训练选项。。对于迁移学习，保留预训练网络早期的特征（传输层）。要减慢传输层的学习速度，将初始学习率设置为小值。指定最小批量大小和验证数据。软件在训练期间每隔验证迭代都会验证网络。

```matlab
options = trainingOptions('sgd',
    'MinBatchSize',10,
    'MaxEpochs',6,
    'InitialLearnRate',1e-4,
    'Shuffle','every-epoch', ...);
```

## 特性示例

`'ValidationData',augdimsValidation, ...`

`'ValidationFrequency',3, ...`

`'Verbose',false, ...`

`'Plots','training_progress');`

由传输层和新层组成的训练网络。默认情况下，如果可用 GPU，`trainNetwork` 将使用 GPU（需要 Parallel Computing Toolbox™ 和支持的 GPU 设备）。更多信息，请参阅“GPU Support by Release”（Parallel Computing Toolbox）。否则，网络将使用 CPU（需要 MATLAB Code Interface for Deep Libraries™）。你还可以通过使用 `trainingOptions` 的 `'ExecutionEnvironment'` 名称-值对来指定执行环境。

```matlab
netTransfer = trainNetwork(augmLTrain,Layers,options);
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_181_0.png)

| 结果 | |
|---|---|
| 验证准确率 | 99.62% |
| 训练结束 | 达到最终迭代 |
| 开始时间 | 2020-12-17 11:01:47 |
| 持续时间 | 2 min 02 sec |
| 训练周期 | |
| 轮次 (Epoch) | 6 / 6 |
| 每轮迭代次数 | 22 |
| 最大迭代次数 | 22 |
| 验证 | |
| 迭代 | 9 次迭代 |
| 其他信息 | |
| 硬件资源 | 单 GPU |
| 学习率 | 0.0091 |

# 创建 dquantizer 对象

创建一个 `dquantizer` 对象并指定要量化的网络。指定执行环境为 FPGA。

```matlab
dlQuantObj = dquantizer(netTransfer, 'ExecutionEnvironment', 'FPGA');
```

# 校准网络量化

`dquantizer` 对象使用校准数据收集网络卷积层和全连接层学习参数的动态范围。

为了获得最佳量化效果，校准数据必须 LogoNet 网络预测的所有输入的代表。通过将校准数据集减少到 20 张图像来加速校准过程。

```matlab
imageData = imageDatastore(fullfile(curDir, 'logos dataset'), ... 
'IncludeSubfolders',true, 'FileExtensions', '.JPG', 'LabelSource', 'folder');
```

```matlab
imageData_reduced = imageData.subset(1:20);
dlQuantObj.calibrate(imageData_reduced)
```

## 创建目标对象

为你的目标设备创建一个自定义名称的对象，并将目标设备连接到主机连接器：接口支持 JTAG 和以太网。要使用 JTAG，请安装 Xilinx™ Vivado™ Design Suite 2020.1。设置 Xilinx Vivado 工具路径：

```matlab
% hsetuptoolpath('ToolName', 'Xilinx Vivado', 'ToolPath', 'C:\Xilinx\Vivado\2020.1\bin\vivado.')
```

创建目标对象，输入：

```matlab
hTarget = dhldl.Target('Xilinx','Interface','Ethernet');
```

或者，你可以使用 JTAG 接口。

```matlab
% hTarget = dhldl.Target('Xilinx', 'Interface', 'JTAG');
```

# 创建流对象

创建 `dhldl.workflow` 类的对象。当你创建该类时，会指定 `dligquantizer` 对象的实例、位流名称和目标信息。将 `dlQuantObj` 指定为网络。确保位流名称与数据类型以及你目标的 FPGA 板相匹配。在此示例中，目标 FPGA 板是 Xilinx ZCU102 SOC 板，位流使用 int8 数据类型。

```matlab
hW = dhldl.Workflow('Network', dlQuantObj, 'Bitstream', 'zcu102 int8', 'Target',hTarget);
```

# 编译量化系列网络

要编译量化的 AlexNet 系列网络，运行 `dhldl.Workflow` 对象的 `compile` 函数。

```matlab
dn = hW.compile
```

```matlab
% 为深度学习 FPGA 原型进行编译
% 目标 FPGA 位流 zcu102 int8
% 网络包含以下层：
```

| 索引 | 名称 | 类型 | 描述 |
|---|---|---|---|
| 1 | 'data' | 输入 | 具有 'zerocenter' 归归一化的 227x227x3 图像 |
| 2 | 'conv1' | 卷积 | 96 个 11x11x3 卷积，步长为 [4 4] |
| 3 | 'relu1' | ReLU | ReLU |
| 4 | 'norm1' | 交叉归一化 | 5 通道的交叉归一化，带步长 [2] 和填充的 3x3 最大池化 |
| 5 | 'pool1' | 最大池化 | 2 组 128 个 5x5 卷积， |
| 6 | 'conv2' | 分组卷积 | |
| 7 | 'relu2' | ReLU | |
| 8 | 'norm2' | 交叉归一化 | 5 通道的交叉归一化 | |
| 9 | 'pool2' | 最大池化 | 带步长 [2] 和填充的 3x3 最大池化 |
| 10 | 'conv3' | 卷积 | 384 个 3x3x256 卷积，步长为 [1] |
| 11 | 'relu3' | ReLU | ReLU |
| 12 | 'conv4' | 分组卷积 | 2 组 192 个 3x3x192 卷积， |
| 13 | 'relu4' | ReLU | ReLU |
| 14 | 'conv5' | 分组卷积 | 2 组 128 个 3x3x192 卷积， |
| 15 | 'relu5' | ReLU | ReLU |
| 16 | 'pool5' | 最大池化 | 带步长 [2] 和填充的 3x3 最大池化 |
| 17 | 'fc6' | 全连接 | 4096 连接层 |
| 18 | 'relu6' | ReLU | ReLU |
| 19 | 'drop6' | Dropout | 50% dropout |
| 20 | 'fc7' | 全连接 | 4096 连接层 |
| 21 | 'relu7' | ReLU | ReLU |
| 22 | 'drop7' | Dropout | 50% dropout |
| 23 | 'fc' | 全连接 | 32 连接层 |
| 24 | 'softmax' | Softmax | softmax |
| 25 | 'classoutput' | 输出 | 带 'adidas' 的交叉熵和 |

3 个内存区域创建。

跳过 data

编译: conv1->pool5

编译: conv1->pool5 ... 完成。

编译: fc6->fc

编译: fc6->fc ... 完成。

跳过 softmax

跳过 classoutput

创建 Schedule...

创建 Schedule... 完成。

创建 Status Table...

创建 Status Table... 完成。

发布 Schedule...

发布 Schedule... 完成。

发布 Status Table...

发布 Status Table... 完成。

### 分配外部内存：

| offset_name | offset_address | 分配空间 |
|---|---|---|
| InputDataOffset | 0x0000000 | 48.0 MB |
| OutputResultOffset | 0x030000 | 4.0 MB |
| SchedulerDataOffset | 0x034000 | 4.0 MB |
| SystemBufferOffset | 0x038000 | 28.0 MB |
| InstructionDataOffset | 0x054000 | 4.0 MB |
| ConvWeightDataOffset | 0x058000 | 8.0 MB |
| FCWeightDataOffset | 0x060000 | 56.0 MB |
| EndOffset | 0x090000 | 总计 152.0 MB |

### 网络编译完成。

```matlab
dn struct 包含字段:
    weights: [1x struct]
    instructions: [1x struct]
    registers: [1x struct]
    syncInstructions: [1x struct];
```

10-104

# 量化网络示例

# 将位流写入 FPGA 并下载权重

在 Xilinx ZCU102 硬件上部署网络，运行 `dhldl.workflow` 对象的 `deploy` 函数。该函数使用 `compile` 函数的输出通过编程文件 FPGA FPGA。还会下载权重和偏置。`deploy` 函数开始编程 FPGA 设备，显示进度以及部署网络所需。

```matlab
HW.deploy
```

### FPGA 位流编程已跳过，因为相同的位流已加载在

### 正在加载权重到 Conv Processor。

### 当前权重已加载。时间是 2020-12-17 11:06:56

### 正在加载权重到 FC Processor。

### 完成 33%，时间是 2020-12-17 11:06:57。

### 完成 67%，时间是 2020-12-17 11:06:59。

### FC 权重已加载。时间是 2020-12-17 11:06:59

```

# 加载示例图像并运行预测

加载示例图像，执行 `dhldl.workflow` 对象的 `predict` 函数，要部署 FPGA 结果，执行：

```matlab
idx = randperm(numel(imdsValidation.Files),4)

figure

for i = 1:4

    subplot(2,2,i)

    I = readimage(imdsValidation,idx(i))

    imshow(I)

    [prediction, speed] = HW.predict(single(I), 'Profile','on')

    [val, index] = max(prediction)

    netTransfer.Layers(end).ClassNames(index)

    label = netTransfer.Layers(end).ClassNames(index)

    title(string(label))

end
```
