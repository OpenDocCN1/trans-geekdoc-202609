
# Custom Processor Configuration Workflow

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

# Estimate ResNet-18 Performance for Custom Bitstream Configuration

To estimate the performance of the ResNet-18 DAG network, we use the estimateFunction of the dldhl.ProcessorConfig object. The function returns the estimated latency, network latency, and performance in frames per second (Frames/s).

```python
hpc_custom.estimatePerformance(snet)
```

### initializing series network: Fused 'ncnn.layer.BatchNormalizationLayer' into 'ncnn.layer'
5 Memory Regions created.

# Deep Learning Processor Emulator Performance Results

| Network | LastFrameLatency(cycles) | LastFrameLatency(seconds) | FramesNum | Total |
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

# Estimate Performance of Deep Learning Network

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

> * The clock frequency of the DL processor is: 200MHz

The performance of the ResNet-18 on the custom bit configuration is lower than the performance on the zcu102 single bit configuration. The difference between the custom bit configuration and the zcu102 single bit configuration is the target frequency.

# Modify Custom Processor Configuration

Modify the custom processor configuration to increase the target frequency. To learn about modifiable parameters of the processor configuration, see dhdl.ProcessorConfig.

```python
hpc_custom.TargetFrequency = 220;
hpc_custom =
```

```
Processing Module "conv"
ConvThreadNumber: 16
InputMemorySize: [227 227 3]
OutputMemorySize: [227 227 3]
FeatureSizeLimit: 2048
KernelDataType: 'single'
```

```
Processing Module "fc"
FcThreadNumber: 4
InputMemorySize: 4096
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
SynthesisToolChipFamily: 'Zynq UltraScale+'
SynthesisToolDeviceName: 'xcuz9eg-ffb1156-2-e'
SynthesisToolPackageName: ''
SynthesisToolSpeedValue: ''
```

# Re-estimate ResNet-18 Performance for Modified Custom Bitstream Configuration

Estimate the performance of the ResNet-18 DAG network on the modified custom bitstream configuration.

```python
hPC_custom.estimatePerformance(snet)
```

```
### Optimizing series network: Fused nnet.cnn.layer.BatchNormalizationLayer into "nnet.cnn.layer"
5 Memory Regions created.
```

# Deep Learning Processor Estimator Performance Results

| Network | LastLatency(cycles) | LastLatency(seconds) | FramesNum | |
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
| fc1000 | 287349 | 0.00104 | |

> * The clock frequency of the DL processor is: 200MHz

The performance of the ResNet-18 on the custom bit configuration is lower than the performance on the zcu102 single bit configuration. The difference between the custom bit configuration and the zcu102 single bit configuration is the target frequency.
