will be developed in the future. The open specification of VHDX and VHD files means that they can be used for virtualization products from other companies and anyone can write tools to handle them.

Windows accesses disks through controllers and a VM running on Hyper-V is present: The usual types are present IDE and SCSI. In a physical machine, SCSI systems generally perform better on a server. Not only are SCSI disks faster than IDE disks (generally speaking), but the SCSI interface was designed to handle multiple I/O requests at the same time. In an enlightened VM, both IDE and SCSI data transfers are quickly translated to VBus requests that turn depend on the storage system of the host. In fact, .vhd file has no knowledge of its controller. This means that the same .vhd file can be used with an IDE and SCSI controller.

# FIXED OR DYNAMIC VHDX: WHICH VIRTUAL DISK TYPE IS?

If're familiar with Hyper-V, and you've carried out your research on virtual disk types in Windows Server 2012 R2 and can't make your up as to whether to use fixed, dynamic, or even pass-through disks, you're not alone. In earlier versions of the legacy VHD format, the general consensus was that you wanted the best performance, then you also had to use fixed VHD. Dynamic VHDs were the cause of untold performance issues, but when Windows Server 2012 was released, Microsoft was encouraging people to use dynamic disks with their new VHDX format since the performance issues of the past had been resolved.

There's a bit of a divide, inside the Hyper-V community as the performance gains or losses between a divide and dynamic VHDX disks and the practicality of using each one. You only have to look at this blog post from Irish Hyper-V MVP Aidan Finn, http://www.aidann.com/tp-1238, to see that he says about all else. For a different perspective, see this post from another well-regarded Hyper-V MVP, Thomas Maurer, http://www.thomas-mauer.com/2012/11/windows-server-2012-hyper-v-virtual-disk-vhd-vhdx-recommendations/, who prefers using dynamic VHDX for the majority of instances.

My own preference for Windows 2012 R2 is to use dynamic VHDX disks for low-utilization VMs (such as domain controllers, print servers, and so on) and fixed VHDX disks for any VM that requires a higher level of I/O (such as SQL and Exchange Server). That way, I get the best of both worlds in terms of performance and storage management.

# Creating a New Virtual Disk

You can create a virtual disk during the deployment of a new VM, editing the configuration of a VM, or as a stand-alone disk whenever you want. In this section we'll walk you through the process of creating a new fixed-size, stand-alone VHDX disk by making use of the New Virtual Hard Disk Wizard in the Hyper-V console.

+   1. To begin, open Hyper-V Manager, click New from the Actions pane, and then choose Hard Disk from the resulting menu to start the New Virtual Hard Disk Wizard.

+   2. Click Next.

+   3. In the Choose Format dialog box showing you 27:16, select the VHDX option.
Click Next.