# CreateWorkFlow Object

Create an object of the dhldl.Workflow class. When you create the object, specify the network and the bitstream name. Make the saved pretrained neural network, snet, as the network. Make sure that the bitstream name matches the data type and the board that you are targeting. In this example the target FPGA board is the Xilinx ZCU102 SOC board. The bitstream uses a single data type.

```
hw = dhldl.Workflow('Network', snet, 'Bitstream', 'zcu102_single', 'Target', hTarget);
% If running on Xilinx ZCU76 board, instead of the above command,
% uncomment the command below.
% hw = dhldl.Workflow('Network', snet, 'Bitstream', 'z7c06_single', 'Target', hTarget);
```

# Compile MNIST Series Network

To compile the MNIST series network, run the compile function of the dhldl.Workflow.
dn = hw.compile;

```
### Initializing series network: Fused .net.cnn.layer.BatchNormLayer into .net.cnn.layer
    offset_address allocated_space
```

| InputDataOffset | 0x00000000 | 4.0 MB |
| OutputResultOffset | 0x00400000 | 4.0 MB |
| SystemBufferOffset | 0x00800000 | 28.0 MB |
| InstructionDataOffset | 0x02040000 | 4.0 MB |
| ConvWeightDataOffset | 0x02080000 | 4.0 MB |
| FCWeightDataOffset | 0x02c80000 | 4.0 MB |
| EndOffset | 0x03080000 | Total: 48.0 MB |

# Program Bitstream to FPGA and Download Network Weights

To deploy the network on the Xilinx ZCU102 SoC hardware, run the deploy function of the dhldl.Workflow object. This function uses the output of the compile function to program the FPGA by using the programming file. It also downloads the weights and biases.

```
hw.deploy;

### Programming FPGA bitstream over Ethernet...
Downloading target FPGA device configuration over Ethernet to SD card ...
% Copied /tmp/hdlcoder_rd to /mnt/hdlcoder_rd
% Copying Bitstream hdlcoder.bit to /mnt/hdlcoder_rd
% Set bitstream to hdlcoder_rd/hdlcoder.system.bit
% Copying Devicetree dhldl.dtb to /mnt/hdlcoder_rd
% Set Devicetree to hdlcoder_rd/devicetree_dtb/devicetree_dhldl
% Set up boot for Reference Design: 'AXI-Stream DDR Memory Access : 3-AXIM'
```

Downloading target FPGA device configuration over Ethernet to SD card. The system will now show Programming the FPGA bitstream has been completed successfully.
### Loading weights to FC Processor.
### FC Weights loaded. Current time is 28-Jun-2020 12:24:21