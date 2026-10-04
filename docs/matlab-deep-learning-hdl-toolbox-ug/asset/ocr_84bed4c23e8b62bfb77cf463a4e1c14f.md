# Custom Processor Configuration Workflow

# Evaluate Performance of Deep Learning Network on Custom Processor Configuration

Benchmark the performance of a deep learning network on a custom bitstream configuration by comparing it to the performance on a reference (shipping) bitstream configuration. Use the comparison results to adjust your custom deep learning processor parameters to achieve optimum performance.

In this example compare the performance of the ResNet-18 network on the zcu102_single bitstream configuration on the default custom bitstream configuration.

# Prerequisites

+   - Deep Learning Toolbox™ Support Package for Xilinx FPGA and SoC
- Deep Learning Toolbox™
- Deep Learning Toolbox Model for ResNet-18 Network

# Load Pretrained Network

Load the pretrained network.

```
snet = resnet18;
```

# Retrieve zcu102_single Bitstream Configuration

To retrieve the zcu102_single bitstream configuration, use the dhldl.ProcessorConfig object. For more information, see about modifiable parameters of the processor configuration, see getModuleProperty and setModuleProperty.

```
hPC_shipping = dhldl.ProcessorConfig('Bitstream', 'zcu102_single')
```

```
Processing Module: 'conv'
ConvThreadNumber: 16
InputMemorySize: [227 227 3]
OutputMemorySize: [227 227 3]
FeatureSizeLimit: 2048
KernelDataType: 'single'
```

```
Processing Module: 'fc'
FCTThreadNumber: 4
InputMemorySize: 25088
OutputMemorySize: 4096
KernelDataType: 'single'
```

```
Processing Module: 'adder'
InputMemorySize: 40
OutputMemorySize: 40
KernelDataType: 'single'
```

```
System Level Properties
TargetPlatform: 'Xilinx Zynq UltraScale+ MPSoC ZCU102 Evaluation K
TargetFrequency: 220
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream DDR Memory Access : 3-AXIM'
```

8-4