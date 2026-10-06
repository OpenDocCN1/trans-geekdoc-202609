
# TABLE 27-5: Hyper-V Host System

| SETTING | CONFIGURATION |
| --- | --- |
| Internal memory | 8 GB; 4 GB is the minimum. |
| Hard disks | Two 200 GB or more. One disk is acceptable for a test system, but expect low performance. |
| Partitions | Disk 1: System on C: \ Disk 2: Reserved for Hyper-V on D: \\ |
| Network | 2 Gb NICs for production. One NIC is acceptable for a test system but not production. |
| Operating system | Hyper-V–enabled editions of Windows Server 2012 R2 or Windows Server 2012. |
| Installation type | Full GUI is required to follow the examples. |
| Hostname | HOST2012DEMO if you want to follow the examples; anything you like is fine. |
| IP configuration | Address:192.168.1.54/24 Gateway: 192.168.1.1. DNS: 192.168.1.51. |
| Active Directory | Domain-joined recommended for production. Workgroup is workable for testing, although configuring remote management is difficult and far easier if you just use Active Directory. |

Just about the only thing you need to decide before you install the Hyper-V role is which NIC to use for managing the Hyper-V host. The idea is to have at least two NICs in the host, although you can make do with two NICs available, dedicate one to managing the host and the second for VM network traffic. To make this obvious, one trick is to rename the network connections, as shown in Figure 27.10.

# FIGURE 27.10 Renaming the network connections to reflect the role in the Hyper-V host

| Organize | Enable this network device Diagnose this connection Rename |
| --- | --- | --- | --- |
| MGMTNIC | VMEXT1 | VMEXT2 | VMTEAMEXT |

Let's start with the installation of the Hyper-V role:

- 1. Install the server using the parameters in Table 27.5 as a guide for the server, server name, IP configuration, and so on.
- 2. Join the computer to the domain if you want to follow some of the later examples. The domain bigform is used throughout this book.

After you install the Hyper-V host server operating system, you are ready to install the Hyper-V role. During installation, the network connection will be broken or twice because of upgraded network components.

- 3. Log on to your Windows Server 2012 R2 installation with an account that has domain administrative permissions, and from the Server Manager > Local Server > Manage menu, choose the Roles and Features option.
- 4. In the Before Begin dialog box, click Next.
- 5. Ensure Role-Based or Feature-Based Installation is selected in the Select Selection dialog box, then click Next.
- 6. Under Select Destination, leave the default option of Select from the Server Pool checked; confirm that your server is highlighted in the Server Pool section and then Next, continue.
- 7. When you reach the Select Roles dialog box, scroll down until you find the Hyper-V option from the Roles list, and check the box beside it.

You'll then be prompted to add some required features here such as the Hyper-V Management Tools.

- 8. Click the Add Features from the window that pops up.
- 9. Click Next to continue.
- 10. Leave the features as they are in the Select Features dialog box; then click Next.
- 11. In the Create Virtual Switches dialog box shown in Figure 27.11, choose each NIC for a virtual switch that you are going to use with your VMs.

You'll find the details later in this chapter, but briefly, for each NIC you select, one virtual switch will be created. If you have NICs or more, you should leave one blank—we are leaving our MGMN here. An unselected NIC will not have a switch associated with it and can be used to manage the host. If you have only one NIC, select it. If you don't select any NIC, your VMs have no way to communicate with the outside world, although you could correct this later. Because we remembered to give sensible names to the network connections, it's now easy to select the one we will use for VM network traffic.

# 1362 CHAPTER 27 SERVER VIRTUALIZATION WITH HYPER-V

FIGURE 27.11
Select one NIC to VM traffic. The unselected NIC is used to manage the Hyper-V host.

![](img/41a83208e6906a3732620203b836cea7_1397_0.png)

- 12. Click Next, and you'll be presented with the Virtual Machine migration.
- 13. Leave the option unselected (we'll come back to this later in the chapter) and click Next.
- 14. Be careful with the Default Stores dialog box shown in Figure 27.12. It's here that you need to specify where your virtual hard disks and VM configuration files will be stored on your host.
If you have more than one disk or volume, it's best to modify the default locations to store these files on a volume that has enough disk space to host your VMs. In a test or lab environment, you don't want your system C:\ partition running out of disk space as your virtual machines.
- 15. Click Next, confirm your installation selections, and then Install.
- 16. Once the installation is finished, reboot the server;
- 17. After Server Manager initializes, log in using an administrator account.

When it comes back, you should see the Hyper-V role on Server Manager light green, indicating the installation was successful.

# FIGURE 27.12
Choosing the default store for VM files

![](img/41a83208e6906a3732620203b836cea7_1398_0.png)

# HYPER-V PRACTICES CHECKLIST

If you want to ensure that you're building environments in accordance with best-practice recommendations, take a look at this useful blog post by PFE Osborne that I normally use as a checklist for the customer deployments: http://blogs.technnet.com/b/askpfe/archive/2013/03/10/windows-server-2012-hyper-v-best-practices-in-easy-checklist.

# Working with the Console

Take a look at what you have now. Start the console from Server Manager > Tools > Hyper-V Manager. You have a console that allows you to manage virtualization settings, as shown in Figure 27.13. The left pane holds the Hyper-V host you want to manage. Since the current server is HOST2012DEMO, you can have more than one server listed.

# Virtual Machines

This section lists the VMs on this host with some relevant parameters such as their state (running, off, saved, and so on).

# 1364 CHAPTER 27 SERVER VIRTUALIZATION WITH HYPER-V

FIGURE 27.13
The Hyper-V management console

![](img/41a83208e6906a3732620203b836cea7_1399_0.png)

Checkpoints As mentioned earlier, these are point-in-time disk images, including memory and CPU states. You might create a checkpoint of a server if you want to be able to roll back to such an image after deploying a service pack or hotfix that could break more things than it fixes or you use that VM for demo purposes and want to reset to its original state.

Details This section contains extra information on the currently selected VM (if any), such as summary, memory, networking, and replication.

The Actions on the right is the most interesting for now. It allows you to manage various aspects of your Hyper-V environment. Some actions are pretty obvious, such as starting or stopping the Hyper-V Virtual Machine management service or removing the current server from the console. Others such as the Virtual Switch Manager, Virtual SAN Manager, Edit Disk, and Inspect Disk are not so obvious if you're new to the virtualization game.

# Exploring the Actions Pane

If you want to manage Hyper-V through the GUI with native tools, you'll need to utilize the Actions pane of the Hyper-V management console. The New Wizard and Import Virtual Machine Wizard deal with creating VMs and virtual disks, so we'll leave them for the next sections.

Clicking the Hyper-V Settings option opens the dialog box to set parameters for Hyper-V such as virtual disk and VM configuration locations, live and storage migrations, enhanced session mode, and replication.
