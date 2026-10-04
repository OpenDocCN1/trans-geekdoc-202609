

# 估计自定义处理器配置的资源利用率

```
{'fc Bias' } ('fc') "Bias" -0.011837
{'imageinput'} {'imageinput'} "Activations"
{'imageinput_normalization'} {'imageinput'} "Activations"
{'conv 1' } {'batchnorm_1'} "Activations" -22.566
{'relu 1' } {'relu 1'} "Activations" -7.916
{'maxpool 1' } {'maxpool 1'} "Activations"
{'conv 2' } {'batchnorm 2'} "Activations"
{'relu 2' } {'relu 2'} "Activations" -8.461
{'maxpool_2' } {'maxpool_2'} "Activations"
```

# 获取 zcu102_int8 位流配置

要获取 zcu102_int8 位流配置，请使用 `dhldl.ProcessorConfig` 对象。欲需更多信息，请使用 `dhldl.ProcessorConfig` 学习处理器配置的可修改参数、`getModuleProperty` 和 `setModuleProperty`。

hPC_reference = dhldl.ProcessorConfig('Bitstream', 'zcu102_int8')

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
TargetPlatform: Xilinx Zynq UltraScale+ MPSOC ZCU102 Evaluation K
TargetFrequency: 250
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream DDR Memory Access :3-AXIM'
SynthesisChipFamily: 'Zynq UltraScale+'
SynthesisDeviceName: 'zcueg-9-ffvb116-2-e'
SynthesisToolPackage: ''
SynthesisToolSpeedValue:

# 估计 zcu102_int8 位流配置的网络性能和资源利用率

要估计数字系列网络的性能，请使用 `dhldl.ProcessorConfig` 对象的 `estimatePerformance` 函数。该函数返回估计的层延迟、网络延迟以及每秒帧（Frames/s）计算的网络性能。

8-11

# 自定义处理器配置工作

要估计 zcu102_int8 位流的资源使用，请使用 `dlhdl.ProcessorConfig` 对象的 `estimateResources` 函数。该函数返回估计的 DSP slice 和 BRAM 使用量。

```
hPC_reference.estimatePerformance(dlquantObj)
### optimizing network series: Fused 'nnet.cnn.layer.BatchNormalizationLayer' into 'nnet.cnn.layer' 3 Memory Regions created.
```

深度学习处理器估算器性能结果

| Network | LastFrameLatency(cycles) | LastFrameLatency(seconds) | FrameNum |
| --- | --- | --- | --- |
| conv_1 | 57955 | 0.00023 | 1 |
| maxpool_1 | 4391 | 0.00002 | |
| conv_2 | 2877 | 0.00001 | |
| maxpool_2 | 2351 | 0.00001 | |
| conv_3 | 2265 | 0.00001 | |
| fc | 2507 | 0.00001 | |
| | 43564 | 0.00017 | |

- * DL 处理器的时钟频率为：250MHz

```
hPC_reference.estimateResources
```

深度学习处理器估算器资源结果

| DSPs | Block RAM |
| --- | --- |
| DL Processor | 768 | 386 |
| conv_module | 647 | 315 |
| fc_module | 97 | 50 |
| adder_module | 24 | 12 |
| debug_module | 0 | 8 |
| said_module | 0 | 1 |

- * Block RAM 代表 Xinx 设备中的 Block RAM 以及 Intel 设备中的 Block RAM bits

估计的性能为 4314 FPS，估计的资源计数为：

- * 数字信号处理器 (DSP) slice 计数 - 768
- * 随机访问内存 (BRAM) 计数 - 386

估计的 DSP slice 和 BRAM 计数超过了目标设备的资源预算。自定义位流配置以减少资源使用。

# 创建位流配置

要创建自定义处理器配置，请使用 `dlhdl.ProcessorConfig` 对象。欲需更多信息，请使用 `dlhdl.ProcessorConfig`。要学习处理器配置的可修改参数，请使用 `getProperty` 和 `setModuleProperty`。

要减少自定义位流的资源，请修改 conv、fc 和 adder 模块的 `KernelDataType`。修改 `ConvThreadNumber` 以减少 DSP slice 计数。减少 conv 模块的 `InputMemorySize` 和 `OutputMemorySize` 以减少 BRAM 计数。

```
hPC_custom = dlhdl.ProcessorConfig;
hPC_custom.setModuleProperty('conv','KernelDataType','int8');
```

hPC_custom.setModuleProperty('fc', 'KernelDataType', 'int8');
hPC_custom.setModuleProperty('adder', 'KernelDataType', 'int8');
hPC_custom.setModuleProperty('conv', 'ConvThreadNumber', 4);
hPC_custom.setModuleProperty('conv', 'InputMemorySize', [30 30 1]);
hPC_custom.setModuleProperty('conv', 'OutputMemorySize', [30 30 1]);

hPC_custom =

Processing Module "conv"
ConvThreadNumber: 4
InputMemorySize: [30 30 1]
OutputMemorySize: [30 30 1]
FeatureSizeLimit: 2048
KernelDataType: 'int8'

Processing Module "fc"
FCThreadNumber: 4
InputMemorySize: 25088
OutputMemorySize: 4096
KernelDataType: 'int8'

Processing Module "adder"
InputMemorySize: 40
OutputMemorySize: 40
KernelDataType: 'int8'

System Level Properties
TargetPlatform: 'Xilinx Zynq UltraScale+ MPSoC ZCU12 Evaluation K
TargetFrequency: 200
SynthesisTool: 'Xilinx'
ReferenceDesign: 'AXI-Stream DDR Memory Access : 3-AXIM'
SynthesisToolChipFamily: 'Zynq UltraScale+'
SynthesisToolDeviceName: 'xczu9eg-fv01156-2-e'
SynthesisToolPackageName: -
SynthesisToolSpeedValue: 

# 估计自定义位流配置的性能和资源利用率

要估计数字网络的性能，请使用 `dhdhl.ProcessorConfig` 对象的 `estimatePerformance` 函数。该函数返回估计的层延迟、网络延迟以及每秒帧（Frames/s）的网络性能。

要估计 hPC 自定义直播的使用，请使用 `dhdhl.ProcessorConfig` 对象的 `estimateResources` 函数。该函数返回估计的 DSP slice 和 BRAM 使用量。

hPC_custom.estimatePerformance(dliquantObj)

```
### Optimizing series network: Fused nnet.cnn.layer.BatchNormLayer' into 'nnet.cnn.layer
3 Memory Regions created.
```

深度学习处理器估算器性能结果

LastFrameLatency(cycles) LastFrameLatency(seconds) FramesNum Total |8-13

# 自定义处理器配置工作

# hPC_custom.estimateResources

深度学习处理器估算器资源结果

> * Block RAM 代表 Xinx 设备中的 Block RAM 以及 Intel 设备中的 Block RAM bits

估计性能为 574 FPS，估计的资源计数为：

- 数字信号处理器 (DSP) slice 计数 - 120
- 随机访问内存 (BRAM) 计数 - 108

自定义位流的估计资源符合目标设备预算，且估计性能符合目标网络性能。

# 参见

dl1.ProcessorConfig | estimatePerformance | estimateResources | getModuleProperty | setModuleProperty

# 更多关于

- “估计深度学习网络”第 8-3 页
- “自定义处理器参数对性能和资源利用率的影响”第 8-15 页

# 自定义处理器参数对性能和资源利用率的影响

分析深度学习处理器参数如何影响深度学习网络性能和位流资源占用。识别有助于性能并减少资源使用的参数。

下表列出了深度学习处理器参数及其对性能和资源利用率的影响。

| 深度学习处理器参数 | 深度学习处理器模块 | 参数操作 | 对性能的影响 | 对资源利用率的影响 |
|---|---|---|---|---|
| "TargetFrequency" | Base module | 增加目标频率。 | 提升性能。 | 查找表 (LUT) 利用率增加。 |
| "ConvThreadNumber" | conv | 增加线程数。 | 提升性能。 | 增加资源占用。 |
| "InputMemorySize" | conv | 增加输入内存大小。 | 提升性能。 | 增加 RAM (BRAM) 利用率。 |
| "OutputMemorySize" | conv | 增加输出内存大小。 | 提升性能。 | 增加块 RAM (BRAM) 利用率。 |
| "FeatureLimit" | conv | 增大限制。 | 提升具有大量特征层的性能。 | 增加块 RAM (BRAM) 利用率。 |
| "KernelDataType" | conv | 将数据类型更改为 int8。 | 提升性能。可能会可能会下降。 | 减少资源占用。 |
| "FCThreadNumber" | fc | 增加线程数。 | 提升性能。 | 增加资源占用。 |
| "InputMemorySize" | fc | 增加输入内存大小。 | 提升性能。 | 增加块 RAM (BRAM) 利用率。 |
| "OutputMemorySize" | fc | 增加输出内存大小。 | 提升性能。 | 增加块 RAM (BRAM) 利用率。 |

