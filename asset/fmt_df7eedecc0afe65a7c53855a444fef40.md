
### 正在为深度学习 FPGA 原型编译网络 ...
### 正在目标位 FPGA 位流 `zcul02_single` ...
### 网络包含以下层：

| 层名称 | 类型 | 详细信息 |
|---|---|---|
| 'data' | 图像输入 | 222x224x3 图像，带有 'zerocenter' |
| 'conv1' | 卷积 | 96 个 11x3 卷积，带有步长 |
| 'relu1' | ReLU | ReLU |
| 'norm1' | 交叉归一化 | 带有 5 的交叉归一化 |
| 'pool1' | 最大池化 | 步长为 [2 2] 的 3x3 最大池化 |
| 'conv2' | 分组卷积 | 2 组 128 5x5x48 卷积 |
| 'relu2' | ReLU | ReLU |
| 'norm2' | 交叉归一化 | 带有 5 的交叉归一化 |
| 'pool2' | 最大池化 | 步长为 [2 2] 的 3x3 最大池化 |
| 'conv3' | 卷积 | 384 个 3x3x256 卷积，带有步长 |
| 'relu3' | ReLU | ReLU |
| 'conv4' | 分组卷积 | 2 组 192 3x3 卷积 |
| 'relu4' | ReLU | ReLU |
| 'conv5' | 分组卷积 | 2 组 128 3x3192 卷积 |
| 'yolov2Conv1' | 卷积 | 256 3x3x256 卷积，带有步长 |
| 'yolov2Batch1' | 归一化 | 带有 256 通道的归一化 |
| 'relu5' | ReLU | ReLU |
| 'yolov2Conv2' | 卷积 | 256 3x3x256 卷积，带有步长 |
| 'yolov2Batch2' | 归一化 | 带有 256 通道的归一化 |
| 'relu6' | ReLU | ReLU |
| 'yolov2ClassConv' | 卷积 | 42 个 1x1x256 卷积，带有步长 |
| 'yolov2Transform' | YOLO v2 | 带有 7 的 YOLO v2 |
| 'yolov2Output' | YOLO v2 输出 | 带有 7 的 YOLO v2 输出 |

### 正在优化网络：将 'snet.cnn.NormalizationLayer' 合并到 'snet.cnn'。
创建内存区域
跳过: `data`
正在编译 `conv1`->`yolov2ClassConv`
正在编译 `conv1`->`yolov2ClassConv`
跳过: `yolov2OutputLayer`
创建调度...
调度...完成。
创建表...
创建表...完成。
创建状态...完成。
### 正在分配外部内存：

| 偏移名称 | 偏移地址 | 分配空间 |
|---|---|---|
| InputDataOffset | 0x0000000 | 24.0 MB |
| OutputResultOffset | 0x0100000 | 4.0 MB |
| SchedulerDataOffset | 0x01c0000 | 0.0 MB |
| SystemBufferOffset | 0x01c0000 | 28.0 MB |
| InstructionDataOffset | 0x0380000 | 4.0 MB |
| ConvWeightDataOffset | 0x03c0000 | 16.0 MB |
| EndOffset | 0x04c0000 | 总计: 76.6 MB |

```
mat
```

### 网络编译完成。

`dn` 字段:

`weights`: [1x struct]

`instructions`: [1x struct]

`registers`: [1x struct]

`syncInstructions`: [1x struct]

# 将位流传输到 FPGA 并下载网络 Zynq UltraScale+ MPSoC ZCU102

在 `dhdll.Workflow` 函数上使用编程函数运行 FPGA 板。该函数下载权重和偏置。部署函数检查 Xilinx Vivado 工具版本。它使用位流开始编程 FPGA 设备，显示消息并花费部署网络的时间。

`hW.`

```
mat
### 跳过 FPGA 位流编程，因为相同的位流已加载在
### 加载权重到卷积处理器。
### 卷积权重加载。当前时间为 2020-12-20 15:26:28
```

# 加载示例函数并运行预测

在 `dhdl.Workflow` 对象上执行预测函数并显示结果：

```mat
[prediction, speed] = HW.predict(I_re, 'Profile', 'on');
```

```mat
### 完成写入输入激活。
### 正在运行输入激活。
```

# 深度学习处理器性能结果

| 上一帧延迟 (周期) | 上一帧延迟 (秒) | 帧数 |
|---|---|---|

| Network | 861567 | 0.03916 | 1 |
| conv1 | 1357049 | 0.00617 |
| norm1 | 569406 | 0.00259 |
| pool1 | 205869 | 0.00094 |
| conv2 | 2207222 | 0.01003 |
| norm2 | 360973 | 0.00164 |
| pool2 | 197444 | 0.00080 |
| conv3 | 976419 | 0.00444 |
| conv4 | 761188 | 0.00346 |
| conv5 | 521782 | 0.00237 |
| yolov2Conv1 | 660213 | 0.00300 |
| yolov2Conv2 | 661162 | 0.00301 |
| yolov2ClassConv | 136816 | 0.00062 |

* DL 处理器的时频率为: 220MHz

显示预测结果。

```mat
[bboxes, scoresn, labelsn] = yolo_post_proc(prediction,I_pre,bboxes,{'Vehicle'});
I_new3 = insertObjectAnnotation(I,'rectangle',bboxes,scoresn);
figure
imshow(I_new3)
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_174_0.png)

# 满足性能要求的自定义学习器生成

此示例了了创建一个自定义处理器配置并估计预训练网络的性能。然后你可以修改自定义配置的参数并重新估计性能。一旦达到你的性能需求，就可以使用自定义配置生成自定义位流。

## 加载预训练系列网络

要加载预训练系列网络 LogoNet，输入：

```mat
snet = getLogoNetwork();
```

# 创建自定义处理器配置

要创建自定义配置，请使用 `dhdl.ProcessorConfig` 对象。更多信息请使用 `dhdl.ProcessorConfig` 了解处理器配置的可修改参数，使用 `getModuleProperty` 和 `setModuleProperty`。

```mat
hPC = dhdl.ProcessorConfig;
hPC.TargetFrequency = 220;
hPC =
```

```mat
hPC = 
Processing Module "conv"
ConvThreadNumber: 16
InputMemorySize: [227 227 3]
OutputMemorySize: [227 227 3]
FeatureSizeLimit: 2048
KernelDataType: 'single'

Processing Module "fc"
FcThreadNumber: 4
InputMemorySize: 25088
OutputMemorySize: 4096
KernelDataType: 'single'

Processing Module "adder"
InputMemorySize: 40
OutputMemorySize: 40
KernelDataType: 'single'
```

```mat
System Level Properties
TargetFormat: 'Xilinx Zynq UltraScale+ MPSoC ZCU102 Evaluation
TargetFrequency: 220
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream DDR Memory Access : 3-AXIM'
SynthesisToolFamily: 'Zynq UltraScale+'
SynthesisToolDeviceName: 'xczu9eg-ffvb1156-2-e'
SynthesisToolPackageName: ''
SynthesisToolSpeedValue: ''
```

# 估计 LogoNet 性能

要估计 LogoNet 系列网络的性能，请使用 `dlhdl.ProcessorConfig` 对象的 `estimatePerformance` 函数。该函数返回估计的延迟、网络延迟以及以每秒帧数（Frames/s）计算的网络性能。

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

估计的每秒帧数为 5.5 Frames/s。要提高网络性能，请修改自定义卷积模块的内核数据类型、卷积线程数以及全连接网络的内核线程数。有关关于这些参数的更多信息，请使用 `getModuleProperty` 和 `setModuleProperty`。

# 创建自定义处理器配置

要创建处理器配置，请使用 `dlhdl.ProcessorConfig` 对象。更多信息请参阅 `dlhdl.ProcessorConfig`。要了解处理器配置的可修改参数，请使用 `setModuleProperty` 和 `setModuleProperty`。

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

要估计 LogoNet 网络的性能，请使用 `dlhdl.Workflow` 对象的 `estimatePerformance` 函数。该函数返回估计的延迟、网络延迟以及以帧(s) 计算的网络性能。

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

示例中生成的比特流类似于 `zcu102_int8`。要使用 `zcu102_int8` 比特流部署量化的 LogoNet 网络，请参阅“获取量化 LogoNet 预测结果”。

# 部署量化网络示例
