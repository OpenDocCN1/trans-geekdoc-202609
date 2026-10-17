
`hPC_custom.setModuleProperty('fc', 'KernelDataType', 'int8');`

`hPC_custom.setModuleProperty('adder', 'KernelDataType', 'int8');`

`hPC_custom.setModuleProperty('conv', 'ConvThreadNumber', 4);`

`hPC_custom.setModuleProperty('conv', 'InputMemorySize', [30 30 1]);`

`hPC_custom.setModuleProperty('conv', 'OutputMemorySize', [30 30 1]);`

`hPC_custom =`

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

## 估计自定义位流配置的性能和资源利用率

要估计数字网络的性能，请使用 `dhdhl.ProcessorConfig` 对象的 `estimatePerformance` 函数。该函数返回估计的层延迟、网络延迟以及每秒帧（Frames/s）的网络性能。

要估计 hPC 自定义直播的使用，请使用 `dhdhl.ProcessorConfig` 对象的 `estimateResources` 函数。该函数返回估计的 DSP slice 和 BRAM 使用量。

`hPC_custom.estimatePerformance(dliquantObj)`

```
### Optimizing series network: Fused nnet.cnn.layer.BatchNormLayer' into 'nnet.cnn.layer
3 Memory Regions created.
```

深度学习处理器估算器性能结果

LastFrameLatency(cycles) LastFrameLatency(seconds) FramesNum Total |8-13

# 自定义处理器配置工作

# `hPC_custom.estimateResources`

深度学习处理器估算器资源结果

> * Block RAM 代表 Xinx 设备中的 Block RAM 以及 Intel 设备中的 Block RAM bits

估计性能为 574 FPS，估计的资源计数为：

- 数字信号处理器 (DSP) slice 计数 - 120
- 随机访问内存 (BRAM) 计数 - 108

自定义位流的估计资源符合目标设备预算，且估计性能符合目标网络性能。

## 参见

`dl1.ProcessorConfig` | `estimatePerformance` | `estimateResources` | `getModuleProperty` | `setModuleProperty`

## 更多关于

- “估计深度学习网络”第 8-3 页
- “自定义处理器参数对性能和资源利用率的影响”第 8-15 页

## 自定义处理器参数对性能和资源利用率的影响

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
| :--- | :--- | :--- | :--- | :--- |
| "KernelDataType" | fc | 将数据类型更改为 int8。 | 提高性能。可能会导致精度下降。 | 减少资源占用。 |
| "InputMemorySize" | adder | | | |
| "" | | | 增加输入内存大小 | 仅提高 DAG 网络的性能。 | 仅增加 DAG 网络的资源占用。 |
| "OutputMemorySize" | adder | 增加输出内存大小 | 仅提高 DAG 网络的性能。 | 仅增加 DAG 网络的资源占用。 |
| "KernelDataType" | adder | 将数据类型更改为 int8。 | 提高性能。可能会导致精度下降。 | 减少资源占用。 |

## 参见

`dldl.ProcessorConfig` | `estimatePerformance` | `estimateResources` | `getModuleProperty` | `setModuleProperty`

## 更多信息

- 第 8-3 页：“深度学习网络性能估计”
- 第 8-9 页：“自定义处理器配置的资源利用率估计”
- 第 8-15 页：“自定义深度学习处理器参数对性能和利用率的影响”

## 自定义处理器代码生成流

- 第 9-2 页：“生成自定义位流”
- 第 9-4 页：“生成自定义处理器 IP”

## 生成自定义位流

要生成自定义位流以将深度学习网络部署到目标设备，请使用 `dhldl.ProcessorConfig` 对象。

1. 创建 `dhldl.ProcessorConfig` 对象。

```matlab
hPC = dhldl.ProcessorConfig;
```

2. 设置设计工具的路径。例如，设置 Vivado® 设计工具的路径，输入：

```matlab
dissetuppath('Toolname','Xilinx Vivado','ToolPath','C:\Xilinx\Vivado\2019.2\bin\vivado.bat');
```

3. 生成自定义位流。

```matlab
dhldl.buildProcessor(hPC);
```

4. 位流生成完成后，您可以在 `cwd\dhldl_prj\vivado_ip.prj\runs\impl_1\` 找到位流文件，其中 `cwd` 是您的当前工作目录。位流文件名为 `system_top_wrapper.bit`。相关的 `system_wrapper.mat` 文件位于 `cwd` 的顶层。

要将生成的位流用于支持的 Xilinx 板卡，应将 `system_top_wrapper.bit` 和 `system_top_wrapper.mat` 文件拷贝到同一个文件夹。

| 名称 | 日期 | 类型 | 大小 |
| :--- | :--- | :--- | :--- |
| codegen | 7/14/2020 4:10 AM | 文件文件夹 | |
| dhldl_prj | 7/14/2020 5:02 AM | 文件文件夹 | |
| hdlsrc | 7/14/2020 4:57 AM | 文件文件夹 | |
| slprj | 7/14/2020 4:57 AM | 文件文件夹 | |
| cksm_Network | 7/14/2020 4:10 AM | MATLAB 数据 | 6 KB |
| DeployableNetwork | 7/14/2020 4:10 AM | MATLAB 数据 | 6 KB |
| inputP1_seqimg | 7/14/2020 4:10 AM | MATLAB 数据 | 1 KB |
| inputP1_seqResult | 7/14/2020 4:10 AM | MATLAB 数据 | 1 KB |
| OPOthResult | 7/14/2020 4:41 AM | MATLAB 数据 | 205 KB |
| system_top_wrapper.bit | 7/14/2020 7:09 AM | BIT 文件 | 25,890 KB |
| system_top_wrapper | 7/14/2020 5:06 AM | MATLAB 数据 | 15 KB |

要将生成的位流用于支持的 Intel 板卡，应将 `system_core.rbf`、`system.mat`、`system_periph.rbf` 和 `system.so` 文件拷贝到同一个文件夹。

| 名称 | 日期 | 类型 | 大小 |
| :--- | :--- | :--- | :--- |
| codegen | 7/14/2020 4:10 AM | 文件文件夹 | |
| dlhdl_prj | 7/14/2020 5:04 AM | 文件文件夹 | |
| hdlsrc | 7/14/2020 4:16 AM | 文件文件夹 | |
| slprj | 7/14/2020 5:01 AM | 文件文件夹 | |
| cksm_Network | 7/14/2020 4:10 AM | MATLAB 数据 | 7 KB |
| DeployableNetwork | 7/14/2020 4:10 AM | MATLAB 数据 | 6 KB |
| inputP1_seqlm | 7/14/2020 4:10 AM | MATLAB 数据 | 1 KB |
| inputP1_seqResult | 7/14/2020 4:10 AM | MATLAB 数据 | 1 KB |
| QPObtbResult | 7/14/2020 4:41 AM | MATLAB 数据 | 205 KB |
| system.core/rbf | 7/14/2020 6:30 AM | RBF 文件 | 14,657 KB |
| system | 7/14/2020 5:07 AM | MATLAB 数据 | 16 KB |
| system.periph.rbf | 7/14/2020 6:30 AM | RBF 文件 | 353 KB |
| system.sof | 7/14/2020 6:25 AM | SOF 文件 | 25,989 KB |

5. 将自定义位流和深度学习网络部署到目标设备。

```matlab
htarget = dlhd.Target('xilinx');
smet = alexinet;
hw = dlhd.Workflow('Network',smet, 'Bitstream','system_top_wrapper.bit', 'Target',htarget);
% 如果您的自定义位流文件在不同的文件夹，请使用：
hw = dlhd.Workflow('Network',smet, 'Bitstream','system_top_wrapper.bit', 'Target',htarget);
```

# 在 Intel Arria 10 SoC 上开始深度学习 FPGA 部署

```
hW =
Workflow with properties:
Network: [1x1 SeriesNetwork]
Bitstream: 'arria10soc_single'
ProcessorConfig: []
Target: [1x1 dlhdl.Target]
```

## 编译 MNIST 系列网络

要编译 MNIST 系列网络，请运行 `dlhdl.Workflow` 对象的 `compile` 函数。

`d = hw.compile;`

### 正在优化系列网络：将 `cnet.layer.BatchNormalizationLayer` 合并到 'cnet.layer.'

offset_address offset_address allocated_space

| InputDataOffset | 0x00000000 | 4.0 MB |
| OutputResultOffset | 0x04000000 | 4.0 MB |
| SystemBufferOffset | 0x08000000 | 28.0 MB |
| InstructionDataOffset | 0x02400000 | 4.0 MB |
| ConvWeightDataOffset | 0x02800000 | 4.0 MB |
| FCWeightDataOffset | 0x02C00000 | 4.0 MB |
| EndOffset | 0x03000000 | Total: 48.0 MB |

# 在 FPGA 上固程序位流并部署网络权重

若要在 Intel Arria 10 硬件上部署网络，请运行 `dlhdl.Workflow` 对象的 `deploy` 函数。该函数使用 `compile` 函数的输出通过编程文件对 FPGA 板进行编程。它还会下载网络权重和偏置。`deploy` 函数开始为 FPGA 设备编程，显示进度消息以及部署网络所需的时间。

```
hW.deploy
### FPGA 位流编程已跳过，因为目标上已加载相同的位流
### 正在加载权重到 FC 处理器。当前时间为 2020年6月30日 13:45:67
```

## 为示例图像运行预测

要加载示例图像，执行 `dlhdl.Workflow` 对象的 `predict` 函数，然后显示 FPGA 结果：

```
inputImg = imread('five_28x28.pgm');
imshow(inputImg);
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_82_0.png)

使用配置 'on' 运行预测，以获取延迟和吞吐量结果。

```
[prediction, speed] = hW.predict(single(inputImg), 'Profile', 'on');
```

```
### 完成完成输入激活值。
### 正在运行单个输入激活值。
```

深度学习处理器分析器性能结果

| | LayerLatency(cycles) | LastLatency(seconds) | FramesNum |
|---|---|---|--|
| Network | 49243 | 0.00033 | 1 |
| conv_module | 25983 | 0.00017 | |
| conv_1 | 6813 | 0.00005 | |
| maxpool_1 | 4705 | 0.00003 | |
| conv_2 | 5205 | 0.00003 | |
| maxpool_2 | 3839 | 0.00003 | |
| conv_3 | 5481 | 0.00004 | |
| fc_module | 23260 | 0.00016 | |
| fc | 23260 | 0.00016 | |

* DL 处理器的时钟频率为: 150MHz

```
[val, idx] = max(prediction);
printf('The prediction result is %d\n', idx-1);
```

预测结果为 5

# 另

## 更多关于

- "检查主机计算机与 FPGA 板的连接"
- "创建用于分类的简单深度学习网络"

# 在 Xilinx ZCU102 SoC 上开始深度学习 FPGA 部署

此示例展示了如何使用针对 Xilinx FPGA 和 SoC 的 Deep HDL Toolbox™ 支持包创建、编译并部署一个 `dlhd.Workflow` 对象，该对象以手写字符检测系列网络作为网络对象。使用 MATLAB™ 从目标设备获取预测。

## 先决条件

- Xilinx ZCU102 SoC 开发套。
- Deep Learning HDL Toolbox™
