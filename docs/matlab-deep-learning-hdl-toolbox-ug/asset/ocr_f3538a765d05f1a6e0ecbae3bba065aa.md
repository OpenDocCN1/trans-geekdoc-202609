```
Compiling leg: conv1>>pool5 ... complete.
Compiling leg: fc6>>fc8 ...
Compiling leg: fc6>>fc8 ... complete.
Skipping: prob
Skipping: output
Creating Schedule...
...
Creating Schedule...complete.
Creating Status Table...
...
Creating Status Table...complete.
Emitting Status...
...
Emitting Schedule...complete.
Emitting Status Table...
...
Emitting Status Table...complete.
```

# ### Allocating external memory buffers:

| InputDataOffset | 0x00000000 | 8.0 MB |
| OutputResultOffset | 0x00000000 | 4.0 MB |
| SchedulerDataOffset | 0x00c00000 | 4.0 MB |
| SystemBufferOffset | 0x01000000 | 28.0 MB |
| InstructionDataOffset | 0x02000000 | 4.0 MB |
| WeightDataOffset | 0x03000000 | 12.0 MB |
| FCWeightDataOffset | 0x03c00000 | 84.0 MB |
| EndOffset | 0x09000000 | *Total: 144.0 MB |

# ### Network compilation complete.

```
ans = struct with fields:
    weights: [1 struct]
    instructions: [1 struct]
    registers: [1 struct]
    SyncInstructions: [1 struct];
```

# Program Bitstream onto FPGA and Download Network Weights

To deploy the network on the Xilinx ZCU100 SoC hardware, run the deploy function of the dhl1. Workflow object uses the output compile function to program the FPGA board using the programming file. It also downloads the network weights and biases. The deploy function starts programming the FPGA device, displays progress messages, and it takes time to deploy the network.

HW.deploy

```
### Programming FPGA Bitstream using Ethernet...
Downloading target device configuration over Ethernet to SD card ...
# Copied /tmp/hdlcoder rd to /mnt/hdlcoder_rd
# Copying Bitstream to hdlcoder_rd/hdlcoder_system.bit
# Set Bitstream to hdlcoder_rd
# Copying Devicetree_devicetree_dhl1.dt to /mnt/hdlcoder_rd
# Set Devicetree to hdlcoder_rd/devicetree_dhl1.dtb
```