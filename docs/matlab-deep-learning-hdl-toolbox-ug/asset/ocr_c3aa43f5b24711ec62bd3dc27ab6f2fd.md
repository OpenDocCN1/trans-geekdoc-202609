information. use "GPU Support by Release (Parallel Computing Toolbox). Otherwise, the network uses a CPU (requires MATLAB Coder Interface for deep learning Libraries). You can also specify the execution environment by using 'ExecutionEnvironment' name-value of trainingOptions.

netTransfer = trainNetwork(augmindsTrain, Igraph, options);

![](bbox=[0.072, 0.219, 0.893, 0.599])

# Create Target Object

Use the dlhdTarget class to create a target object with a custom name for your target device to the host computer. Interface options are JTAG and Ethernet. To use JTAG,Install Xinx Vivado™ Design Suite 2019.2. To set the Xinx Vivado toolpath, enter:

```
$ dlhdtoolpath('ToolName', 'Xilinx Vivado', 'ToolPath', 'C:\Xilinx\Vivado\2019.2\bin')nhTarget = dlhd.Target('Xilinx', 'Interface', 'Ethernet');
```

# Create Workflow Object

Use the dlhd.Workflow class to create an object. When you create the object, specify the network and the bitstream name. Specify the pretrained alexnet neural network as network. Make sure that the bitstream matches the data type and the FPGA board that you are targeting. In this example, the FPGA board is the Xinx ZCU102 SoC board. The bitstream uses a single data type.

```
hW = dlhd.Workflow('Network', netTransfer, 'Bitstream', 'zcu102_single', 'Target', hTarget);
```