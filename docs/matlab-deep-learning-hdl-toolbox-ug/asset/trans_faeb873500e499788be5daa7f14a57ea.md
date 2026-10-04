

# 10 个特性示例

细节，我们预训练的深度神经网络）。此示例使用 ResNet-18 进行特征提取。根据应用需求，你也可以使用其他预训练网络，例如 MobileNet v2 或 ResNet-50。与特征提取相比，检测子网络是一个较小的 CNN，由几个卷积层和专门用于 YOLO v2 的层组成。

使用 `yolov2Layers` 函数在给定预训练的 ResNet-18 特征提取网络的情况下自动创建 YOLO v2 检测网络。`yolov2Layers` 要求你指定几个参数来参数化 YOLO v2 网络：

- 网络输入大小
- 锚框 (Anchor boxes)
- 特征提取网络

首先，指定网络输入大小和类别数量。在选择网络输入大小时，请考虑网络本身所需的最小尺寸、训练图像的大小以及处理所选尺寸数据时引入的计算成本。在可行的情况下，选择一个接近训练图像尺寸且大于网络所需输入尺寸的网络输入大小。为了减少运行示例的计算成本，请指定网络输入大小为 `[224 224 3]`，这是运行网络所需的最小尺寸。

```
inputSize = {224 224 3};
```

定义要检测的对象类别数。
`numClasses = width(vehicleDataset)-1;`

注意，此示例中使用的训练图像大于 224x224 尺寸各异，因此你必须在训练之前的预处理步骤中调整图像大小。

接下来，使用 `estimateAnchorBoxes` 根据训练数据中对象的大小估计锚框。为了考虑到训练前先验的调整，请为估计锚框调整训练数据。使用 `transform` 预处理训练数据，然后定义锚框数量并估计锚框。使用 `ypreprocessData` 函数将训练数据调整为网络的输入图像大小。

```
trainingDataForEstimation = transform(trainingData,@data)yolo_preprocessData(data,inputSize);
Anchors = 7;
meanIoU = estimateAnchorBoxes(trainingDataForEstimation,numAnchors)
```

```
anchorBoxes = 7x2

145 126
91 86
161 132
41 34
67 64
136 111
23
```

```
meanIoU = 0.8651
```

有关如何选择锚框的更多信息，请参见 [Estimate Anchor Boxes From Training Data (Computer Vision Toolbox (Computer Vision Toolbox™))] 和 [Anchor Boxes for Object Detection (Computer Vision Toolbox)]。

# 使用部署到 FPGA 的基于 DAG 网络 YOLO v2 进行车辆检测

现在，使用 `resnet18` 加载预训练的 ResNet-18 模型。

```
featureExtractionNetwork = resnet18;
```

选择 'res4b_relu' 作为特征提取层，用检测子网络替换 'res4b_relu' 之后的层。该特征提取层输出下采样率为 16 倍的图。这种下采样量是空间分辨率与提取特征强度之间的权衡，因为在网络更深处提取的特征以牺牲空间分辨率为代价编码了更强的图像特征。选择的特征提取层需要经验分析。

```
featureLayer = res4b_relu;
```

创建 YOLO v2 对象检测网络。

```
lgraph = yolov2Layers(inputSize,numClasses,anchorBoxes,featureExtractionNetwork,featureLayer);
```

你可以使用 Deep Learning Toolbox 中的 `analyzeNetwork` 或 Deep Network Designer 可视化网络。

如果需要对 YOLO v2 架构进行更多控制，请使用 Deep Network Designer 手动设计 YOLO v2 检测网络。更多信息请参见 [Design a YOLO v2 Detection Network (Computer Vision Toolbox)]。

# 数据增强

数据增强用于通过在训练期间随机转换原始数据来提高网络准确性。通过使用数据增强，你可以在不实际增加标记样本的情况下增加数据的多样性。

使用 `transform` 通过随机翻转图像和关联标签来增强数据。注意数据增强不应用于测试和验证数据。理想情况下，测试和验证数据应该是原始数据的代表且保持不变以进行评估。

```
augmentedTrainingData = transform(trainingData,@yolo_augment);
```

# 预处理训练数据并训练 YOLO v2 检测器

预处理增强数据和验证数据以准备训练。

```
preprocessedTrainingData = transform(augmentedTrainingData,@data)yolo_preprocessData(data,inputSize));
```

使用 `trainingOptions` 指定网络选项。将 'ValidationData' 设置为临时位置 'CheckpointPath'。这允许在训练过程中保存部分训练的检测器。如果训练因断电或系统故障中断，可以从保存的检查点继续训练。

```
options = trainingOptions('sgdm',
'MiniBatchSize',16,...
'InitialLearnRate',1e-3,...
'MaxEpochs',20,...
'CheckpointPath', tempdir,...
'Shuffle', 'never');
```

使用 `trainYOLO2ObjectDetector` 函数训练 YOLO v2 检测器。

```
[detector,info] = trainYOLO2ObjectDetector(preprocessedTrainingData,lgraph,options);
```

正在为以下对象类别训练 YOLO v2 检测器：

- vehicle
在单 CPU 上训练。初始化数据归一化。

| Epoch | Iteration | Time Elapsed (hh:mm:ss) | Mini-batch RMSE | Mini-batch Loss | Base Learning Rate |
|---|---|---|---|---|---|
| 1 | 1 | 00:00:02 | 8.43 | 7.1 | 0.0010 |
| 5 | 50 | 00:01:26 | 0.71 | 0.5 | 0.0010 |
| 10 | 100 | 00:02:46 | 0.75 | 0.6 | 0.0010 |
| 14 | 150 | 00:04:04 | 0.53 | 0.3 | 0.0010 |
| 19 | 200 | 00:05:23 | 0.48 | 0.2 | 0.0010 |
| 20 | 220 | 00:05:53 | 0.57 | 0.3 | 0.0010 |

检测器完成。

作为快速测试，在单幅图像上运行检测器。

```
[bboxes,scores] = detect(detector,I);
```

显示结果。
`I_new = insertObjectAnnotation(I,'rectangle',bboxes);`
`figure`
`imshow(I_new)`

img/7bfd428a7e091f2763cc5d

# 加载预训练网络

加载预训练网络。

```
snet = detector;
```

使用 `analyzeNetwork` 获取网络层的信息：

```
analyzeNetwork(snet)
```

# 创建目标对象

为你的目标设备创建一个带有供应商名称和连接到主机计算机接口的目标对象。使用安装的 Vivado Design Suite 通过以太网对设备进行编程。

```
hTarget = dhdl.Target('Xilinx', 'Interface', 'Ethernet');
```

# 创建 Workflow 对象

创建 `dhdl.Workflow` 类对象。创建对象时，指定网络和位流名称。指定保存的预训练网络 `snet` 作为网络。确保位流名称与你的目标 FPGA 板板匹配。在本示例中，FPGA 板是 Zynq UltraScale+ MPSOC ZCU102。位流使用单类型数据。

```
hw = dhdl.Workflow('Network', snet, 'Bitstream', 'zcu102 single', 'Target', hTarget)
hw
```

具有属性的 Workflow：
Network: [1x1 DAGNetwork]
Bitstream: ['zcu102_single']
ProcessorConfig: []
Target: [1x1 dhdl.Target]

# 编译 YOLO v2 对象检测器

要编译 `snet` 系列网络，运行 `dhdl.Workflow` 对象的函数。

```
dn = hw.compile

```

正在为深度学习 FPGA 原型编译 ...
目标 FPGA 位流 zcu102 single ...
网络包含以下层：

| 'data' | 图像输入 | 224x224x3 使用'zscore' 归一化的图像 |
|---|---|---|
| 'conv1' | 卷积 | 64 7x7 卷积，步长 [2] |
| 'bn conv1' | 批量归一化 | 64 通道的批量归一化 |
| 'conv1_relu' | ReLU | ReLU |
| 'pool1' | 最大池化 | 3x3 最大池化，步长 [2] |
| 'res2a_branch2a' | 卷积 | 64 3x6 卷积，步长 |
| 'res2a_branch2a' | 批量归一化 | 64 通道的批量归一化 |
| 'res2a_branch2a_relu' | ReLU | ReLU |
| 'res2a_branch2b' | 卷积 | 64 3x6 卷积，步长 |

```

