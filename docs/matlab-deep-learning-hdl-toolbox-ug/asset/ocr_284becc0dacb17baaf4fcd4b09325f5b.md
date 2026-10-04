imageData reduced = imageData.subset(1:20);
dlQuantObj.calibrate(imageData_reduced)

# Create Target Object

Create a target object with a custom name for your target device and to connect to your
target device to the host connector: Interface supports JTAG and Ethernet. To use JTAG, install
Xilinx™ Vivado™ Design Suite 2020.1. To set the Xilinx Vivado toolpath:

```
% hsetuptoolpath('ToolName', 'Xilinx Vivado', 'ToolPath', 'C:\Xilinx\Vivado\2020.1\bin\vivado.')
```

To create the target object, enter:

```
hTarget = dhldl.Target('Xilinx','Interface','Ethernet');
```

Alternatively, you can use the JTAG interface.

```
% hTarget = dhldl.Target('Xilinx', 'Interface', 'JAG');
```

# Create Workflow Object

Create an object of the dhldl.workflow class. When you create the class, an instance of
dligquantizer object, the bitstream name, and target information are specified. Specify
dlQuantObj as network. Make sure that the bitstream name matches the data type and the
FPGA board that you are targeting. In this example, the target FPGA board is the Xilinx ZCU102 SOC
board and the bitstream uses int8 data type.

```
hW = dhldl.Workflow('Network', dlQuantObj, 'Bitstream', 'zcu102 int8', 'Target',hTarget);
```

# Compile the Quantized Series Network

To compile the quantized AlexNet series network, run the compile function of the dhldl.Workflow
object.

```
dn = hW.compile
```

```
% Compiling for Deep Learning FPGA prototyping
% Targeting FPGA bitstream zcu102 int8
% The network includes the following layers:
```

| 1 'data' Input | 227x227x3 images with 'zerocenter' normal |
| 2 'conv1' | Convolution | 96 11x11x3 convolutions with stride [4 4 |
| 3 'relu1' | ReLU | ReLU |
| 4 'norm1' | Cross Normalization | cross normalization with 5 channels
 3x3 max pooling with stride [2] and padding |
| 5 'pool1' | Max Pooling | 2 groups of 128 5x5 convolutions with |
| 6 'conv2' | Grouped Convolution | |
| 7 'relu2' | ReLU | |
| 8 'norm2' | Cross Normalization | cross normalization with 5 channels |
| 9 'pool2' | Max Pooling | 3x3 max pooling with stride [2] and padding |
| 10 'conv3' | Convolution | 384 3x3x256 convolutions with stride [1 |
| 11 'relu3' | ReLU | ReLU |
| 12 'conv4' | Grouped Convolution | 2 groups of 192 3x3x192 convolutions with |
| 13 'relu4' | ReLU | ReLU |
| 14 'conv5' | Grouped Convolution | 2 groups of 128 3x3x192 convolutions with |
| 15 'relu5' | ReLU | ReLU |
| 16 'pool5' | Max Pooling | 3x3 max pooling with stride [2] and padding |
| 17 'fc6' | Fully Connected | 4096 fully connected layer |
| 18 'relu6' | ReLU | ReLU |