# Image Category Classification by Using Deep Learning

Deep Learning Network Analyzer
snet
Analysis date: 10-Jul-2020 17:01:54

| Name | Type | Activations | Learnables |
|---|---|---|---|
| conv1 | Image Input | 227*227*3 images with stride [1] and padding [0 0 0] | Convolution | 55*55*96 | Weights: 11*11*3*96 Bias: 1*96 |
| relu | | ReLU | 55*55*96 | Bias: 1*96 |
| pool1 | | Max Pooling | 27*27*96 |
| conv2 | cross normalization with 5 elements per channel | Cross Normalization | 55*55*96 |
| pool2 | | Max Pooling | 27*27*96 |
| conv3 | 2 groups of 128*54*40 convolutions with stride [1] and padding [1] | Grouped Convolution | 27*27*256 | Weights: 5*5*240*128 Bias: 1*128 |
| relu | | ReLU | 27*27*256 |
| conv4 | cross normalization with 5 elements per channel | Cross Normalization | 13*13*256 |
| pool3 | 3x3 max pooling with stride [2] and padding [0 0 0] | | 13*13*256 |
| conv5 | 164*34*30 convolutions with stride [1] and padding [1 1 1] | Convolution | 13*13*384 | Weights: 3*3*3*384 Bias: 1*384 |
| relu | | ReLU | 13*13*384 | Bias: 1*384 |
| conv6 | 2 groups of 128*31*192 convolutions with stride [1] and padding [...] | Grouped Convolution | 13*13*512 | Weights: 3*3*192*256 Bias: 1*512 |
| relu | | ReLU | 13*13*512 | Bias: 1*512 |
| conv7 | 2 groups of 128*31*192 convolutions with stride [1] and padding [...] | Grouped Convolution | 13*13*512 | Weights: 3*3*192*256 Bias: 1*512 |
| relu | | ReLU | 13*13*512 |
| pool4 | 2x2 max pooling with stride [2] and padding [0 0 0] | Max Pooling | 6*6 |
| fc1 | | Fully Connected | 1*44096 | Weights: 4096*1024 Bias: 1*1024 |

# # Create Object

Use dlhl.Target to create a target object with a custom name for your target device and an interface to connect your target device to the host device. Interface options are JTAG and Ethernet. Use JTAG,Install Xilinx Vivado™ Design Suite 2019.2. Use the Xilinx Vivado target, output:

```
% dlhlsettoolpath('TargetName','Xilinx Vivado', 'ToolPath', 'C:\Xilinx\Vivado\2019.2\bin\vivado.')
hTarget = dlhl.Target('Xilinx', 'Interface', 'Ethernet');
```

# # Create Workflow Object

Use dlhl.Workflow to create an object. When you create the object, specify the network and the bitstream name. Make sure the bitstream name matches the data type and the FPGA board that you are targeting. In this example, the target FPGA board is the Xilinx ZCU102 SoC board. The bitstream uses a single type, enter:

```
hw = dlhl.Workflow('Network', 'snet', 'Bitstream', 'zcu102_single', 'Target',hTarget);
```

# # Compile the Analytics network

To compile the Analytics network run, run the compile method of the dlhl.Workflow object. You can optionally specify the maximum number of input frames.

10-19