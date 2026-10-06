Private With private virtual switches, VMs are connected to each other but cannot see the host. Effectively, they are completely isolated from the physical network. Again, this idea is useful for testing. For instance, when you test the DHCP features of Windows Server 2012 R2, you wouldn't want to try this on a physical network. In some cases, a private switch is the safest option for testing.

A useful feature of virtual switches is that you can change their scopes and functionality. You might start a switch as internal and connect it to a physical external NIC later.

Using virtual switches brings a great deal of flexibility to your VMs, and you can generate quite complicated networks inside the host. Using three virtual switches, you could, for instance, build a classic DMZ setup: one for the outside interface connected to a physical NIC, and one for the DMZ hosts, and one switch for the internal LAN.

# Creating a Virtual Switch

There are two paths to configure virtual networking: virtual NICs and virtual switches. The virtual NICs are managed through the VM settings window, which we will discuss later, and the virtual switch is configured through the Virtual Switch Manager.

To create a virtual switch, you need to follow these steps:

+   1. Open Hyper-V Manager and click Virtual Switch Manager in the Actions pane.

+   2. As shown in Figure 27.21, click to select the "New network switch" option.

+   3. In the "Virtual switch" section, choose the type of virtual switch you want to create (External, Internal, or Private), and then click the Create Virtual Switch button.

In Figure 27.22, the virtual switch VMEXT1 is selected. This switch was created when we installed the Hyper-V role and told the wizard which NICs to use for VM traffic. Look back to Figure 27.11 to see what this means.

![](bbox=[0.095, 0.593, 0.904, 0.803])