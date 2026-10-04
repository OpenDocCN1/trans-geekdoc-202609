
# 10 Featured Examples

ReferenceDesign: 'AXI-Stream DDR Memory Access'
SynthesisTool: ''
ChipFamily: 'Zynq UltraScale+'
SynthesisToolDeviceName: 'xczu9eg-ffvbl115-26-e'
SynthesisToolPackageName: ''
SynthesisToolSpeedValue: ''

# Estimate ResNet-18 Performance for zcu102-single Bitstream Configuration

To estimate the performance of the ResNet-18 DAG network, use the estimatePerformance function of the dlhdl.ProcessorConfig object. The function returns the estimated latency, network latency, and performance frames per second (Frames/s).

hPC_shipping.estimatePerformance(snet)

```
### Optimizing series network: Fused 'nnet.cnn.layer.BatchNormalizationLayer' into 'nnet.cnn.layer'. 
5 Memory Regions created.
```

# Deep Learning Latency Estimator Performance

| | LastLatency(cycles) | LastLatency(seconds) | FramesNum |
|---|---|---|---|
| Network | conv1 | 22576184 | 0.10262 | |
| | pool | 2165372 | 0.00984 | 1 |
| | pool | 646226 | 0.00294 | |
| | res2a brancha | 966221 | 0.00439 | |
| | res2a branchb | 966221 | 0.00439 | |
| | res2b brancha | 966221 | 0.00439 | |
| | res2b branchb | 966221 | 0.00439 | |
| | res3a brancha | 757716 | 0.00344 | |
| | res3a branchb | 919117 | 0.00418 | |
| | res3a branch1 | 540749 | 0.00246 | |
| | res3b brancha | 919117 | 0.00418 | |
| | res3b branchb | 919117 | 0.00418 | |
| | res4a brancha | 509261 | 0.00231 | |
| | res4a branchb | 905421 | 0.00412 | |
| | res4b brancha | 509261 | 0.00231 | |
| | res4b branchb | 905421 | 0.00412 | |
| | res5a brancha | 1013837 | 0.00461 | |
| | res5a branchb | 1939661 | 0.00882 | |
| | res5b brancha | 1013837 | 0.00461 | |
| | res5b branchb | 1939661 | 0.00882 | |
| | pool5 | 54594 | 0.00025 | |
| | fc1000 | 207850 | 0.00094 | |

> * The clock frequency of the DL processor is: 220MHz

# Create Custom Processor Configuration

To create a processor configuration, use the dlhdl.ProcessorConfig object. To learn about modifiable parameters of the processor configuration, see getModuleProperty and setModuleProperty.

```
hPC_custom = dlhdl.ProcessorConfig
```

# Evaluate Performance of Deep Learning Network on Custom Processor Configuration

hPC_custom =

```
Processing Module "conv"
ConvThreadNumber: 16
InputSize: [227 227 3]
OutputSize: [227 227 3]
FeatureSizeLimit: 2040
KernelDataType: 'single'
Processing Module "fc"
FcThreadNumber: 4
InputSize: 25088
OutputSize: 4096
KernelDataType: 'single'
Processing Module "adder"
InputSize: 40
OutputSize: 40
KernelDataType: 'single'
System Level Properties
TargetPlatform: 'Xilinx UltraScale+ MPSoC ZCU102 Evaluation Kit'
TargetFrequency: 200
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream DDR Memory Access : 3-AXIM'
SynthesisChipFamily: 'Zynq UltraScale+'
SynthesisDeviceName: 'xczuq-fevbl156-2-e'
SynthesisPackageName: ''
SynthesisToolValue: ''
```

# Estimate ResNet-18 Performance for Custom Bus Configuration

To estimate the performance of the ResNet-18 DAG network, we use the estimatePerformance of the dlh.ProcessorConfig object. The function returns the estimated latency, network latency, and memory per frame (Frames/).

hPC_custom.estimatePerformance(snet)

```
### Optimizing series network: Fused 'resnet.cnn.layer.BatchNormalization' into 'resnet.cnn.layer'.
5 Memory Regions created.
```

# Deep Learning Processor Estimator Results

| LastFrameLatency(cycles) | LastFrameLatency(seconds) | FrameNum | Total |
|---|---|---|---|
| Network | 22576183 | 0.11288 | 1 | 229 |
| conv1 | 2165372 | 0.01083 | | |
| pool1 | 646226 | 0.00323 | | |
| res2a brancha | 966221 | 0.00483 | | |
| res2a branchb | 966221 | 0.00483 | | |
| res2b brancha | 966221 | 0.00483 | | |
| res2b branchb | 966221 | 0.00483 | | |
| res3a brancha | 757716 | 0.00379 | | |
| res3a branchb | 919117 | 0.00460 | | |
| res3a branch1 | 540749 | 0.00270 | | |
| res3b brancha | 919117 | 0.00460 | | |
| res3b branchb | 919117 | 0.00460 | | |
| res4a brancha | 509261 | 0.00255 | | |
| res4a branchb | 905421 | 0.00453 | | |
| res4b brancha | 509261 | 0.00255 | | |
| res4b branchb | 905421 | 0.00453 | | |
| res5a brancha | 1013837 | 0.00507 | | |
| res5a branchb | 1939661 | 0.00970 | | |
| res5b brancha | 1013837 | 0.00507 | | |
| res5b branchb | 1939661 | 0.00970 | | |
| pool5 | 54594 | 0.00027 | | |
| fc1000 | 207349 | 0.00104 | | |

# Modify Processor Configuration

Modify the custom processor configuration to increase the target frequency. To learn about modifiable parameters of the processor configuration, see dlhdl.ProcessorConfig.

```
hpc_custom.TargetFrequency = 220;
```

```
hpc_custom =
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
System Level Properties
TargetPlatform: Xilinx Zynq UltraScale+ MPSoC ZCU102
TargetFrequency: 220
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'Stream DDR Memory Access : 3-AXIM'
SynthesisToolChipFamily: 'Zynq UltraScale+'
SynthesisToolDeviceName: 'xczu9eg-ffb1156-2-e'
SynthesisToolPackageName: ''
SynthesisToolSpeedValue: ''
```

# Evaluate Performance of Deep Learning Network on Custom Processor Configuration

# Re-estimate ResNet-18 Performance for Modified Custom Bitstream Configuration

Estimate the performance of the ResNet-18 DAG network on the modified custom bitstream configuration.

hPC_custom.estimatePerformance(snet)

```
### Optimizing series network: Fused nnet.cnn.layer.BatchNormalizationLayer into 'nnet.cnn.layer'.
5 Memory Regions created.
```

# Deep Learning Processor Estimator Performance Results

| Network | LastFrameLatency(cycles) | LastFrameLatency(seconds) | FramesNum |
|---|---|---|---|
| conv1 | 22576184 | 0.01026 | 1 |
| pool | 2165372 | 0.00908 | | |
| pool | 64626 | 0.00024 | | |
| res2a branch2a | 96621 | 0.00439 | | |
| res2a branch2b | 96621 | 0.00439 | | |
| res2b branch2a | 96621 | 0.00439 | | |
| res2b branch2b | 96621 | 0.00439 | | |
| res3a branch2a | 757716 | 0.00379 | | |
| res3a branch2b | 919117 | 0.00460 | | |
| res3a branch1 | 540749 | 0.00270 | | |
| res3b branch2a | 919117 | 0.00460 | | |
| res3b branch2b | 919117 | 0.00460 | | |
| res4a branch2a | 509261 | 0.00255 | | |
| res4a branch2b | 905421 | 0.00453 | | |
| res4b branch2a | 509261 | 0.00255 | | |
| res4b branch2b | 905421 | 0.00453 | | |
| res5a branch2a | 1013837 | 0.00507 | | |
| res5a branch2b | 1939661 | 0.00970 | | |
| res5b branch2a | 1013837 | 0.00507 | | |
| res5b branch2b | 1939661 | 0.00970 | | |
| pool5 | 54594 | 0.00027 | | |
| fc1000 | 207349 | 0.00104 | | |

> * The clock frequency of the DL processor is: 220MHz

The performance of the ResNet-18 network on the bitstream configuration is lower than the performance on the zcu102_single bitstream configuration. The difference between the bitstream configuration and the zcu102_single bitstream configuration is the target frequency.

# Customize Bitstream Configuration to Meet Resource Requirements

The user wants to deploy a digit recognition network with a target performance of 500 frames per second (FPS) to a Xilinx ZCU102 device. The default resource counts exceed the user budget and is on the higher end of the cost spectrum. You can achieve target performance and resource budget by quantizing the deep learning network and customizing the default bitstream configuration.

In this example create a custom bitstream configuration to match your resource budget and performance.

# Prerequisites

+- Deep Learning HDL Toolbox Support Package for Xilinx FPGA and SoC
- Deep Learning Toolbox
- Deep Learning HDL Toolbox
- Deep Learning Toolbox Model Quantization Library

# Load Pretrained Network

To load the pretrained series network, that has been trained on the Modified Institute of Standards of Technology (MNIST) database, enter:

```
snet = getDigitsNetwork;
```

# Quantize Network

To quantize the MNIST based network, enter:

```
dquantObj = dquantizer(snet, 'ExecutionEnvironment', 'FPGA');
Image = imageDatastore('five_228.png', 'Labels', 'five');
dquantObj.calibrate(image)
```
