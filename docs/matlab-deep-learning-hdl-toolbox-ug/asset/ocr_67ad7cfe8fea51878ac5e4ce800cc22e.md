# 10 Featured Examples

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
TargetPlatform: Xilinx Zynq UltraScale+ MPSoC ZCU102 Evaluation
TargetFrequency: 300
SynthesisTool: 'Xilinx Vivado'
ReferenceDesign: 'AXI-Stream Memory Access : 3-AXIM'
SynthesisChipFamily: 'Zynq UltraScale+'
SynthesisToolDevice: 'xczueg-ffvb1156-2-e'
SynthesisToolPackageName: ''
```

# Quantize LoNet Network Performance

To quantify the LoNet network, enter:

```
dquantObj = dquantize(snet, 'ExecutionEnvironment', 'FPGA');
Image = imageDatastore('heineken.png', 'Labels', 'Heineken');
dquantObj.calibrate(image);
```

# Estimate LoNet Performance

To estimate the performance of the LoNet network series, use the estimate function of dhl1.Workflow object. The function returns the estimated layer latency, network latency, and network performance in frames (Frames).

```
hPCNew.estimatePerformance(dquantObj)
```

3 Regions created.

```
### Notice: (Layer 1) The layer 'imageinput' with type 'nnet.cnn.layer.RegressionOutputLayer' is imp
### Notice: (Layer 14) The layer 'output' with type 'nnet.cnn.layer.RegressionOutputLayer' is imp
### Notice: (Layer 1) The layer 'imageinput' with type 'nnet.cnn.layer.InputLayer' is imp
### Notice: (Layer 7) The layer 'output' with type 'nnet.cnn.layer.RegressionOutputLayer' is imp
```

Deep Learning Processor Estimator Performance Results

| LastFrameLatency(cycles) | LastFrameLatency(seconds) | Frames | Total |
| --- | --- | --- | --- |
| Network conv 1 | 14115856 | 0.04718 | 1 | 147 |
| maxpool_1 | 3475319 | 0.01158 | | |
| conv_2 | 1876680 | 0.00626 | | |
| maxpool_2 | 2932291 | 0.00977 | | |

10-98