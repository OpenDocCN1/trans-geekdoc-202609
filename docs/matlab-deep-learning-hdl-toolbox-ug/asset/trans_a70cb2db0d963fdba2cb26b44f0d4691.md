

# 自定义处理器配置工作流

```
ConvThreadNumber: 16
InputMemorySize: [227 227 3]
OutputMemorySize: [227 227 3]
FeatureSizeDataLimit: 2048
KernelDataType: 'single'
```

```
Processing Module "fc"
FCTThreadNumber: 4
InputMemorySize: 25088
OutputMemorySize: 4096
KernelDataType: 'single'
```

```
Processing Module "adder"
InputMemorySize: 40
OutputMemorySize: 40
KernelDataType: 'single'
```

```
System Level Properties
TargetPlatform: 'Xilinx Zynq UltraScale+ MPSoC ZCU102 Evaluation'
TargetFrequency: 200
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream DDR Memory Access : 3-AXIM'
SynthesisChipFamily: 'Zynq UltraScale+'
SynthesisToolDeviceName: 'xczueg-ffvb1156-2-e'
SynthesisToolPackageName: ''
SynthesisToolSpeedValue: ''
```

# 为自定义比特流配置估计 ResNet-18 性能

为了估计 ResNet-18 DAG 网络的性能，我们使用 `dldhl.ProcessorConfig` 对象的 `estimateFunction`。该函数返回估计的延迟、网络延迟以及每秒帧数（Frames/s）性能。

```python
hpc_custom.estimatePerformance(snet)
```

### 初始化序列网络：将 'ncnn.layer.BatchNormalizationLayer' 融合到 'ncnn.layer'
创建了 5 个内存区域。

# 深度学习处理器仿真器性能结果

| 网络 | 上帧延迟(周期周期) | 上帧延迟(秒) | 帧数 | 总计 |
|---|---|---|---|---|
| conv | 22575683 | 0.11288 | 1 | 222 |
| | 21653372 | 0.01083 | | |
| pool | 646226 | 0.00323 | | |
| res2a brancha | 966221 | 0.00483 | | |
| res2a branchb | 966221 | 0.00483 | | |
| res2b brancha | 966221 | 0.00483 | | |
| res2b branchb | 966221 | 0.00483 | | |
| res3a brancha | 757716 | 0.00379 | | |
| res3a branchb | 919117 | 0.00460 | | |
| res3abranch1 | 540749 | 0.00270 | | |
| res3bbranch5 | 919117 | 0.00460 | | |
| res3bbranchb | 919117 | 0.00460 | | |
| res4a_brancha | 509261 | 0.00255 | | |

# 深度学习网络性能估计

| | | |
|---|---|---|
| res4a branch2b | 905421 | 0.00453 |
| res4a branch11 | 509261 | 0.00255 |
| res4b branch2a | 905421 | 0.00453 |
| res4b branch2b | 905421 | 0.00453 |
| res5a branch2a | 1013837 | 0.00507 |
| res5a branch2b | 1939661 | 0.00970 |
| res5a branch1 | 1013837 | 0.00507 |
| res5b branch2a | 1939661 | 0.00970 |
| res5b branch2b | 1939661 | 0.00970 |
| pool5 | 54594 | 0.00027 |
| fc1000 | 287349 | 0.00104 |

> * DL 处理器的时钟频率为：200MHz

自定义比特流配置的 ResNet-18 性能低于 zcu102 单比特配置。自定义比特流配置与 zcu102 单比特配置之间的差异在于目标频率。

# 修改自定义处理器配置

修改自定义处理器配置以增加目标频率。关于处理器配置的可修改参数，请参阅 `dhdl.ProcessorConfig`。

```python
hpc_custom.TargetFrequency = 220;
hpc_custom =
```

```
Processing Module "conv"
ConvThreadNumber: 16
InputMemorySize: [227 227 3]
OutputMemorySize: [227 227 3]
FeatureSizeDataLimit: 2048
KernelDataType: 'single'
```

```
Processing Module "fc"
FcThreadNumber: 4
InputMemorySize: 4096
OutputMemorySize: 4096
KernelDataType: 'single'
```

```
Processing Module "adder"
InputMemorySize: 40
OutputMemorySize: 40
KernelDataType: 'single'
```

```
System Level Properties
TargetPlatform: 'Xilinx Zynq UltraScale+ MPSOC ZCU102 Evaluation'
TargetFrequency: 220
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream DDR Memory Access : 3-AXIM'
SynthesisChipFamily: 'Zynq UltraScale+'
SynthesisToolDeviceName: 'xcuz9eg-ffb1156-2-e'
SynthesisToolPackageName: ''
SynthesisToolSpeedValue: ''
```

# 为修改后的比特流配置重新估计 ResNet-18 性能

估计修改后的比特流配置下 ResNet-18 DAG 网络的性能。

```python
hPC_custom.estimatePerformance(snet)
```

```
### 优化序列网络：将 nnet.cnn.layer.BatchNormalizationLayer 融合到 "nnet.cnn.layer"
创建了 5 个内存区域。
```

# 深度学习处理器估计器性能结果

| 网络 | 延迟(周期) | 延迟(秒) | 帧数 | |
|---|---|---|---|---|
| convl | 22576184 | 0.10262 | 1 | |
| pool | 21653372 | 0.10094 | | |
| pool | 64626 | 0.00294 | | |
| res2a branch2a | 96621 | 0.00439 | | |
| res2a branch2b | 96621 | 0.00439 | | |
| res2b branch2a | 96621 | 0.00439 | | |
| res2b branch2b | 96621 | 0.00439 | | |
| res3a branch2a | 757716 | 0.00379 | | |
| res3a branch2b | 919117 | 0.00460 | | |
| res3abranch1 | 540749 | 0.00270 | | |
| res3bbranch5 | 919117 | 0.00460 | | |
| res3bbranchb | 919117 | 0.00460 | | |
| res4a_brancha | 509261 | 0.00255 | | |
| res4a branch2b | 905421 | 0.00453 | | |
| res4a branch11 | 509261 | 0.00255 | | |
| res4b branch2a | 905421 | 0.00453 | | |
| res4b branch2b | 905421 | 0.00453 | | |
| res5a branch2a | 1013837 | 0.00507 | | |
| res5a branch2b | 1939661 | 0.00970 | | |
| res5a branch1 | 1013837 | 0.00507 | | |
| res5b branch2a | 1939661 | 0.00970 | | |
| res5b branch2b | 1939661 | 0.00970 | | |
| pool5 | 54594 | 0.00027 | | |
| fc1000 | 287349 | 0.00104 | | |

