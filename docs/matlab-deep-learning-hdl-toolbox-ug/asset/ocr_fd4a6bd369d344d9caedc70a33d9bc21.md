# Running Convolution-Only Networks by using FPGA Deployment

# Create Workflow Object

Create an object of the dlhdl.Workflow class. When you create the object, specify the network and the bitstream name. Specify the saved pretrained ResNet50 subset network, snet, the network. Make sure that the bitstream name matches the data type and the FPGA board that you are targeting. In the target FPGA board is the Xilinx ZCU102 SOC board. The bitstream uses a single data type.

```
hw = dlhdl.Workflow('network', snet, 'Bitstream', 'zcu102_single', 'Target',hTarget);
```

# Compile Modified Resnet-50 Series Network

To compile the modified Resnet-50 series network, run the compile function of the dlhdl.Workflow

```
Hw.compile
d = Hw.compile
```

```
### Optimizing series network: Fused nnet.cnn.layer.BatchNormLayer into 'nnet.cnn.layers'
offset_name offset_address allocated_space
```

| InputDataOffset | 0x00000000 | "24.0 MB" |
| OutputResultOffset | 0x01800000 | "24.0 MB" |
| SystemBufferOffset | 0x03000000 | "28.0 MB" |
| InstructionDataOffset | 0x04c00000 | "4.0 MB" |
| ConvWeightDataOffset | 0x05000000 | "4.0 MB" |
| EndOffset | 0x05400000 | "Total: 84.0 MB" |

```
dn = struct with fields:
  Operators: [1 struct]
LayerConfigs: [1 struct]
NetConfigs: [1 struct]
```

# Program Bitstream onto FPGA and Download Network Weights

To deploy the network on the Xilinx ZCU102 hardware, run the deploy function of the dlhdl.Workflow object. This function uses the output of the compile function to program the FPGA board by the programming function. It also downloads the network weights and biases. The deploy function programs the FPGA device, displays progress messages, and the time it takes to deploy the network.

```
hw.deploy
```

```
### FPGA bitstream programming has been skipped as the bitstream is already loaded on the
### Deep learning network programming has been skipped as the same network is already loaded on
```

# Load Image Example

Load and display an image to use as an input image to the series network.

```
I = imread('daisy.jpg');nimshow(I)
```

10-73