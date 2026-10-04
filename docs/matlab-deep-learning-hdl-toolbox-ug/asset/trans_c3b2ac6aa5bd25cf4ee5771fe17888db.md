

# 估计 LogoNet 性能

要估计 LogoNet 系列网络的性能，请使用 dlhdl.ProcessorConfig 对象的 estimatePerformance 函数。该函数返回估计的延迟、网络延迟以及以每秒帧数（Frames/s）计算的网络性能。

```matlab
hPC.estimatePerformance(snet)
```

创建了 3 个内存区域。

```
### Note: (Layer 1) 类型为 'nnet.cnn.layer.ImageInputLayer' 的 'imageinput' 是即时的
### Note: (Layer 14) 类型为 'nnet.cnn.layer.RegressionOutputLayer' 的 'output' 是重要的
### Note: (Layer 1) 类型为 'nnet.cnn.layer.ImageInputLayer' 的 'imageinput' 是即时的
### Note: (Layer 7) 类型为 'nnet.cnn.layer.RegressionOutputLayer' 的 'output' 是重要的
```

深度学习处理器估算器性能结果

| | LastFrame(Cycles) | LastLatency(seconds) | Frames | Total |
|---|---|---|---|---|
| Network conv_1 | 39864116 | 0.18120 | 1 | 398 |
| | maxpool_1 | 6825287 | 0.03102 | | |
| | conv_2 | 10440701 | 0.01707 | | |
| | maxpool_2 | 1447840 | 0.00746 | | |
| | conv_3 | 9393937 | 0.04270 | | |
| | maxpool_3 | 1765856 | 0.00803 | | |
| | conv_4 | 1770844 | 0.00505 | | |
| | maxpool_4 | 28098 | 0.00013 | | |
| | fc_1 | 2651286 | 0.01205 | | |
| | fc_2 | 1696936 | 0.00771 | | |
| | fc_3 | 89509 | 0.00041 | | |

> * DL 处理器的时钟频率为: 220MHz

估计的每秒帧数为 5.5 Frames/s。要提高网络性能，请修改自定义卷积模块的内核数据类型、卷积线程数以及全连接网络的内核线程数。有关关于这些参数的更多信息，请使用 getModuleProperty 和 setModuleProperty。

# 创建自定义处理器配置

要创建处理器配置，请使用 dlhdl.ProcessorConfig 对象。更多信息请参阅 dlhdl.ProcessorConfig。要了解处理器配置的可修改参数，请使用 setModuleProperty 和 setModuleProperty。

```matlab
hPCNew = dlhdl.ProcessorConfig;
hPCNew.TargetFrequency = 300;
hPCNew.setModuleProperty('conv', 'KernelDataType', 'int8');
hPCNew.setModuleProperty('conv', 'ConvThreadNumber', 64);
hPCNew.setModuleProperty('fc', 'KernelDataType', 'int8');
hPCNew.setModuleProperty('fc', 'FCThreadNumber', 16);
```

```text
Processing Module "conv"
ConvThreadNumber: 64
InputMemorySize: [227 227 3]
OutputMemorySize: [227 227 3]
```

# 10 个特色示例

```
FeatureSizeLimit: 2048
KernelDataType: 'int8'
```

```
Processing Module "fc"
ThreadNumber: 16
InputMemorySize: 25088
OutputMemorySize: 4096
KernelDataType: 'int8'
```

```
Processing Module "adder"
InputMemorySize: 40
OutputMemorySize: 40
KernelDataType: 'single'
```

```
System Level Properties
TargetPlatform: Xilinx Zynq UltraScale+ MPSoC CU102
TargetFrequency: 300
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream'
SynthesisChipFamily: 'Zynq UltraScale+'
SynthesisToolDevice: 'zc102'
SynthesisToolPackage: ''
```

# 量化 LogoNet 网络

要量化 LogoNet 网络，请输入：

```matlab
dquantObj = quantize(snet, 'ExecutionEnvironment', 'FPGA');
image = imageastore('logos.png', 'Labels', 'logos');
dquantObj.calibrate(image);
```

# 估计 LogoNet 性能

要估计 LogoNet 网络的性能，请使用 dlhdl.Workflow 对象的 estimatePerformance 函数。该函数返回估计的延迟、网络延迟以及以帧(s) 计算的网络性能。

```matlab
hPCNew.estimatePerformance(dquantObj)
```

创建了 3 个区域。

```
### Note: (Layer 1) 类型为 'nnet.cnn.layer.RegressionOutputLayer' 的 'imageinput' 是即时的
### Note: (Layer 14) 类型为 'nnet.cnn.layer.RegressionOutputLayer' 的 'output' 是重要的
### Note: (Layer 1) 类型为 'nnet.cnn.layer.InputLayer' 的 'imageinput' 是即时的
### Note: (Layer 7) 类型为 'nnet.cnn.layer.RegressionOutputLayer' 的 'output' 是重要的
```

深度学习处理器估算性能结果

| LastFrameLatency(cycles) | LastFrameLatency(seconds) | Frames | Total |
|---|---|---|---|---|
| Network conv_1 | 1415856 | 0.04718 | 1 | 147 |
| maxpool_1 | 3475319 | 0.01158 | | |
| conv_2 | 1876680 | 0.00626 | | |
| maxpool_2 | 2932291 | 0.00977 | | |
| conv_3 | 2581439 | 0.00860 | | |
| maxpool_3 | 882544 | 0.00294 | | |
| conv_4 | 521980 | 0.00174 | | |
| maxpool_4 | 14025 | 0.00005 | | |
| fc_1 | 665263 | 0.00222 | | |
| fc_2 | 425423 | 0.00142 | | |
| fc_3 | 56556 | 0.00019 | | |

* DL 处理器的时钟频率为: 300MHz

估计的每秒帧数为 .2 Frames/s。

# 生成自定义处理器和比特流

使用新的自定义配置构建并生成自定义处理器和比特流。使用自定义比特流将 LogoNet 网络部署到您的 FPGA 板上。

```matlab
% hdlsetpath('ToolName', 'Xilinx Vivado', 'ToolPath', 'C:\Xilinx\Vivado\2019.2\bin\vivado');
% dhdl.buildProcessor(hPCNew)
```

要了解生成的比特流文件，请参见第 9 页的“生成自定义比特流”。

示例中生成的比特流类似于 zcu102_int8。要使用 zcu102_int8 比特流部署量化的 LogoNet 网络，请参阅“获取量化 LogoNet 预测结果”。

# 部署量化网络示例

本示例展示了如何使用 Xilinx FPGA and SoC Support Package 训练、编译并部署一个具有量化 Alexnet 网络的 dldl.Workflow 对象。通过将网络层的权重、偏置和激活值量化为 8 位缩放整数类型，有助于减少深度网络的内存需求。使用 MATLAB™ 从目标设备检索预测结果。

# 所需产品

此示例需要：

- Deep Learning Toolbox™
- Deep Learning HDL Toolbox™
- Deep Learning Model Quantization Library
- Deep Learning HDL Support Package for Xilinx FPGA and SoC

# 加载预训练系列网络

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

此示例使用 logos 数据集。该集合包含 320 张图像。创建一个 augmentedImageDatastore 用于训练和验证。

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

