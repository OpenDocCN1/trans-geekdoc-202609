

# 定制位流配置以满足资源需求

```
{'fc Weights'} ('fc') "Weights" -0.02558
{'fc_Bias'} ('fc') "Bias" -0.011837
{'imageinput'} ('imageinput') "Activations" 0
{'imageinput_normalization'} ('imageinput') "Activations" -22.566
{'conv_1'} ('batchnorm_1') "Activations" -7.9196
{'relu_1'} ('relu_1') "Activations" 0
{'maxpool_1'} ('maxpool_1') "Activations" 0
{'conv_2'} ('batchnorm_2') "Activations" -8.6461
{'relu_2'} ('relu_2') "Activations" 0
{'maxpool_2'} ('maxpool_2') "Activations" 0
```

# 获取 zcu102_int 位流配置

要获取 zcu102_int 位流配置，请使用 `dhldl.ProcessorConfig` 对象。更多信息请参阅 `dhldl.ProcessorConfig`。要了解处理器配置的可修改参数，请使用 `getModuleProperty` 和 `setModuleProperty`。

```python
hPC_reference = dhldl.ProcessorConfig('Bitstream', zcu102_int8)

Processing Module "conv"
ConvThreadNumber: 64
InputMemorySize: [227 227 3]
OutputMemorySize: [227 227 3]
FeatureSizeLimit: 2048
KernelDataType: 'int8'

Processing Module "fc"
FCTThreadNumber: 16
InputMemorySize: 25088
OutputMemorySize: 4096
KernelDataType: 'int8'

Processing Module "adder"
InputMemorySize: 40
OutputMemorySize: 40
KernelDataType: 'int8'

System Level Properties
TargetPlatform: 'Xilinx Zynq UltraScale+ MPSoC ZCU102 Evaluation Kit
TargetFrequency: 250
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream DDR Memory Access : 3-AXIM'
SynthesisToolChipFamily: 'Zynq UltraScale+'
SynthesisToolDeviceName: 'xcu9eg-ffbv116-2-e'
SynthesisToolPackageName: ''
SynthesisToolSpeedValue: ''
```

# 估计 zcu102_int8 位流配置的网络性能和资源利用率

要估计数字系列网络的性能，请使用 `dhldl.ProcessorConfig` 对象的 `estimatePerformance` 函数。该函数返回估计的层延迟、网络延迟以及以每秒帧（Frames）计算的网络性能。

要估算 zcu102 int8 位流的资源消耗，请使用 `dlhdl.ProcessorConfig` 对象的 `estimateResources` 函数。该函数返回估计的 DSP 切片和 BRAM 使用量。

```python
hPC_reference.estimatePerformance(dlquantObj)
```

### 优化系列网络：将 'nnet.cnn.layer.BatchNormLayer' 融合到 'nnet.cnn.layer'。创建了 3 个内存区域。

# 深度学习处理器性能结果

| LastFrameLatency(cycles) | LastFrameLatency(seconds) | FramesNum |
| --- | --- | --- |
| Network | 57955 | 0.00023 | 1 |
| conv_1 | 4391 | 0.00002 | |
| maxpool_1 | 2877 | 0.00001 | |
| conv_2 | 2351 | 0.00001 | |
| maxpool_2 | 2265 | 0.00001 | |
| conv_3 | 2507 | 0.00001 | |
| fc | 43564 | 0.00017 | |

* 深度学习处理器的时钟为：250MHz

```python
hPC_reference.estimateResources
```

# 深度学习处理器估算结果

| DSPs | Block RAM* |
| --- | --- |
| DL Processor | 768 | 386 |
| conv_module | 647 | 315 |
| fc_module | 97 | 50 |
| adder_module | 24 | 12 |
| debug_module | 0 | 8 |
| shared_module | 0 | 1 |

* Block RAM 代表 Xilinx 设备中的 Block tiles 和 Intel 设备中的 Block RAM bits

估计的性能为 4314 FPS，资源使用计数为：

- 数字信号处理器 (DSP) 切片数量 - 768
- 随机访问存储器 (BRAM) 数量 - 386

DSP 切片和 BRAM 数量超过了目标设备的预算。自定义位流配置以减少资源消耗。

# 创建位流配置

要创建处理器配置，请使用 `dlhdl.ProcessorConfig`。更多信息请参阅 `dlhdl.ProcessorConfig`。要了解处理器配置的可修改参数，请使用 `getProperty` 和 `setProperty`。

要减少自定义位流的消耗，请修改 conv、fc 和 adder 模块的 `KernelDataType`。修改 `ConvThreadNumber` 以减少 DSP 切片数量。减少 conv 模块的 `InputMemorySize` 和 `OutputMemorySize` 以减少 BRAM 数量。

```python
hPC_custom = dlhdl.ProcessorConfig;
hPC_custom.setProperty('KernelDataType', 'int8');
hPC_custom.setModuleProperty('fc', 'int8');
hPC_custom.setModuleProperty('adder', 'int8');
hPC_custom.setModuleProperty('conv', 'ConvThreadNumber', 4);
hPC_custom.setModuleProperty('conv', 'InputMemorySize', [30 30 1]);
hPC_custom.setModuleProperty('conv', 'OutputMemorySize', [30 30 1]);
```

# 定制位流配置以满足资源需求

```python
Processing Module "conv"
ConvThreadNumber: 4
InputMemorySize: [30 30 1]
OutputMemorySize: [30 30 1]
FeatureSizeLimit: 2048
KernelDataType: 'int8'

Processing Module "fc"
FCTThreadNumber: 4
InputMemorySize: 25088
OutputMemorySize: 4096
KernelDataType: 'int8'

Processing Module "adder"
InputMemorySize: 40
OutputMemorySize: 40
KernelDataType: 'int8'

System Level Properties
TargetPlatform: 'Xilinx Zynq UltraScale+ MPSoC ZCU102 Evaluation Kit
TargetFrequency: 250
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream DDR Memory Access : 3-AXIM'
SynthesisToolChipFamily: 'Zynq UltraScale+'
SynthesisToolDeviceName: 'xcu9eg-ffbv116-2-e'
SynthesisToolPackageName: ''
SynthesisToolSpeedValue: ''
```

# 自定义位流的网络性能和资源利用率

要估计数字系列网络的性能，请使用 `dhldl.ProcessorConfig` 对象的 `estimatePerformance` 函数。该函数返回估计的层延迟、网络延迟以及每秒帧（Frames/s）的网络性能。

要估计自定义位流的使用，请使用 `dlhdl.ProcessorConfig` 对象的 `estimateResources` 函数。该函数返回估计的 DSP 切片使用情况。

```python
hPC_custom.estimatePerformance(dlquantObj)
```

# 深度学习处理器估算结果

| LastFrameLatency(cycles) | LastFrameLatency(seconds) | FramesNum |
| --- | --- | --- |
| conv_1 | 348511 | 0.00174 | 1 |
| maxpool_1 | 27250 | 0.00014 | |
| conv_2 | 42337 | 0.00021 | |
| maxpool_2 | 45869 | 0.00023 | |
| conv_3 | 60153 | 0.00024 | |
| fc | 121493 | 0.00061 | |
| | 43409 | 0.00022 | |

* 深度学习处理器的时钟为：200MHz

| DSPs | Block RAM* |
| --- | --- |
| DL Processor | 120 | 108 |
| conv_module | 89 | 63 |
| fc_module | 25 | 33 |
| adder_module | 6 | 3 |
| debug_module | 0 | 8 |
| shared_module | 0 | 1 |

* Block RAM 代表 Xilinx 设备中的 Block tiles 和 Intel 设备中的 Block RAM bits

估计的性能为 574 FPS，估计的使用计数为：

- 数字信号处理器 (DSP) 切片数量 - 120
- 随机访问存储器 (BRAM) 数量 - 108

自定义位流的估计资源符合目标设备预算，估计性能符合目标网络性能。

# 部署到 FPGA 的车辆检测 YOLO v2

此示例显示了如何训练和部署 YOLO v2 检测器。

深度学习是一种强大的机器学习技术，你可以用它训练健壮的目标检测器。存在多种目标检测技术，包括 Faster-CNN 和 YOLO v2。此示例使用 `trainYOLOv2objectDetector` 函数训练 YOLO v2 车辆检测器。

# 加载数据集

此示例使用包含 295 张图像的小型车辆数据集。其中许多图像来自 Caltech Cars 1999 和 2001 数据集（可在 Computational Vision 网站获取由 Pietro Perona 创建并获得许可）。每张图像包含一个或两个标记的车辆实例。小型数据集对于探索 YOLO v2 训练很有用，但在实践中，需要更多标记图像来训练健壮检测器。解压车辆真值数据。

```python
unzip DatasetImages.zip
data = load('vehicleGroundTruth.mat');
vehicleDataset = data.vehicleDataset;
```

车辆数据存储在双列表中，第一列包含图像文件路径，第二列包含车辆边界框。

```matlab
% 将完整路径添加到本地数据文件夹。
vehicleDataset.imageFilename = fullfile(pwd,vehicleDataset.imageFilename);
```

将数据集分为训练集和测试集。选择 60% 的数据用于训练，其余用于训练后的检测器。

```matlab
rng(0);
shuffledIndices = randperm(height(vehicleDataset));
idx = floor(0.6 * length(shuffledIndices));
trainingDataTb = vehicleDataset(shuffledIndices(1:idx));
testDataTb = vehicleDataset(shuffledIndices(idx+1:end));
```

使用 imageastore 和 labelastore 创建用于训练和评估加载图像和标签数据的存储器。

```matlab
mdsTrain = imageastore(trainingDataTb(:,,'imageFilename'));
bldsTrain = labelastore(trainingDataTb(:,'vehicle'));
mdsTest = imageastore(testDataTb(:,,'imageFilename'));
bldsTest = labelastore(testDataTb(:,'vehicle'));
```

合并图像和标签存储器。

```matlab
trainingData = combine(mdsTrain,bldsTrain);
testData = combine(mdsTest,bldsTest);
```

# 创建 YOLO v2 检测网络

YOLO v2 检测网络由两个子网络组成。跟随检测网络。特征提取网络通常是预训练的 CNN（对于

