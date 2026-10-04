# Customize Bitstream Configuration to Meet Resource Use Requirements

The user wants to deploy a digit recognition network with a target performance of 500 frames per second (FPS) to a Xilinx ZU102 Z4CG device. The target device resource counts are:

+   - Digital signal processor (DSP) slice count - 240
- Block random access memory (BRAM) count -128

The reference (shipping) zcu102_int8 bitstream configuration is for a Xilinx ZU102 Z9EG device. The default board resource counts are:

+   - Digital signal processor (DSP) slice count - 2520
- Block random access memory (BRAM) count -912

The default resource counts exceed the user resource budget and is on the higher end of the cost spectrum. You can achieve target performance and resource use budget by quantizing the deep learning network and customizing the custom default bitstream configuration.

In this example create a custom bitstream configuration to match your resource budget and performance requirements.

# Prerequisites

+   - Deep Learning HDL Toolbox™ Support Package for Xilinx FPGA and SoC
- Deep Learning Toolbox™
- Deep Learning HDL Toolbox™
- Deep Learning Toolbox Model Quantization Library

# Load Pretrained Network

To load the pretrained series network, that has been trained on the Modified National Institute Standards of Technology (MNIST) database, enter:

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

| Optimized Layer Name | Network Layer Name | Learnables / Activations | MinValue |
|---|---|---|-|
| {conv_1_Weights} | {batchnorm_1} | "Weights" | -0.017061 |
| {conv_1_Bias} | {batchnorm_1} | "Bias" | -0.025344 |
| {conv_2_Weights} | {batchnorm_2} | "Weights" | -0.543444 |
| {conv_2_Bias} | {batchnorm_2} | "Bias" | -1.1787 |
| {conv_3_Weights} | {batchnorm_3} | "Weights" | -0.39927 |
| {conv_3_Bias} | {batchnorm_3} | "Bias" | -0.85118 |