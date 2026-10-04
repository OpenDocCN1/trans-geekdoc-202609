# 10 Featured Examples

![](bbox=[0.078, 0.115, 0.922, 0.503])

# Create Target Object

Create a target object that has a custom name for your target device and an interface to connect your target device to the host computer. Interface options use JTAG and Ethernet. To use the JTAG connection, install the Xilinx™ Vivado™ Design Suite 2020.

To set the Xilinx Vivado toolpath:

```
# hdlsetutoolpath('ToolName', 'Xilinx', 'Vivado', 'ToolPath', 'C:\Xilinx\Vivado\2020.1\bin\vivado.')
hT = dhdl.Target('Xilinx', 'Interface', 'Ethernet')
```

hT =
Target with properties:

+   - Vendor: 'Xilinx'
Interface: Ethernet
IPAddress: '192.168.1.101'
Username: 'root'
Port: 22

# Create Workflow Object for trainedDefNet Network

Create an object of the dhdl.Workflow class. When you create the object, specify the network and the bitstream name. Specify the saved pretrained trainedDefNet as the network. Make sure that

10-26