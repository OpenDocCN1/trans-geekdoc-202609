# # Visualize Activations of a Deep Learning Network by Using LogoNet

This example shows how to feed an image to a convolutional neural network and display the activations of the different layers of the network. Examine the activations and discover which features the network learns by comparing areas of activation to the original image. Channels in earlier layers learn features like color and edges, while channels in the deeper layers learn complex features. Identifying features in this way can help you understand what the network has learned.

# ## Logo Recognition Network

Logos assist in brand identification and recognition. Many companies incorporate their logos in advertising, documentation materials, and promotions. The logo recognition network (LogoNet) was developed in MATLAB and can recognize 32 logos under various lighting conditions and camera motions. Because this network focuses only on recognition, you can use it in applications where localization is not required.

# ## Prerequisites

+   * Arria10 SoC development kit
* Deep Learning HDL Toolbox™ Support Package for Intel FPGA and SoC
* Deep Learning Toolbox™
* Deep Vision HDL Toolbox™
* Computer Vision Toolbox™

# ## Load Pretrained Series Network

To load the pretrained series network LogoNet, enter:

snet = getLogoNetwork();

# ## Create Target Object

Create a target object that has a custom name for your target device and an interface to connect your target device to the host computer. Interface options are JTAG and Ethernet. To use JTAG, install Intel™ Quartus Prime Standard Edition 18.1. Use the path to your installed Intel Quartus Prime executable if it is not already set up. For example, to set the include, enter:

```
% hdlsetuptoolath('TargetName', 'Altera Quartus II', 'ToolPath', 'C:\alera\18.1\quartus\bin64');
```

To create the target object, enter:

```
hTarget = dhldl.Target('Intel', 'Interface', 'JTAG');
```

# ## Create Workflow Object

Create an object of the dhdl.Workflow class. When you create the object, specify the network and the bitstream name. Specify the saved pretrained LogoNet neural network, snet, as well. Make sure that the bitstream name matches the data type and the FPGA board that you are targeting. In this example, the target FPGA board is the Intel Arria10 SOC board. The bitstream uses a single data type.