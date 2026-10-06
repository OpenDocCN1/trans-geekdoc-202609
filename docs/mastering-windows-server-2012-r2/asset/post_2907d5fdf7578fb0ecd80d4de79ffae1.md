
A second, more subtle point is that of the virtual network configuration. How does the VM know which virtual switches to use on the new host? Internally, each virtual switch is known by its GUID, allowing you to give any name you like without interfering with its relations to virtual NICs. But if you create a virtual switch on another host, it will have a different GUID. Hyper-V has one little trick to get around this. On import, it looks for virtual switches with exactly the same name (including character case) as the ones included in the export files. If it finds them, the virtual NICs are connected. If not, the imported VM will be disconnected from switches.

Let's walk through an example where you export and import a VM. Any VM will do, but in this case we will use WS50212R2-SRV1. Ideally you would have a second Hyper-V host for, but the export works with one.

Assume you have a shared folder; we'll use VMHOST with a descriptive name like ImportedVMs. The required share permissions for this folder are a bit tricky. The export process runs as SYSTEM, not as you. So, the share should have permissions for the host computer to write data. Use either the computer account of the source host (VMHOST1-SRV in our example) or the Everyone security to write access. Then, start the export process on the source host:

- 1. On the Hyper-V management console, select the VM to export, which is WS5021R2-SRV1 in this.
- 2. With the VM still running, choose the Export option from the Actions pane.
- 3. Enter a destination path for your export.

This can be a local drive, USB drive, or a remote location. This time, we will export directly to another Hyper-V host: \vmhost2-srv\ImportedVMs. If the path does not exist, the wizard will create it. Whatever path you specify here, the wizard will create a subdirectory with the VM.

After the export procedure is finished, you import the VM. You can do this from the Hyper-V management console on the server side by adding the target host as an additional machine, but for example you will log on to the target:

- 1. Log on to VMHOST2-SRV with an administrative account and open the Hyper-V management console.
- 2. If you want the virtual NICs to connect automatically on import, make sure there are virtual switches on both hosts with exactly the same names.

In our example, we use MGMTNIC for management and VMEXT1 for external connectivity.

- 3. From the Actions pane in the Hyper-V management console, select Import Virtual Machine; then click Next.
- 4. In the Locate Folder dialog box, input or browse for the path where the exported VM is stored as D:\ImportedVMs\W50212R2-SRV1 and then click Next.
- 5. In the Select Virtual Machine dialog box, ensure you select the correct version of the VM to import; then click Next to move on.

The default settings in the Choose Import Type dialog box (as shown earlier in Figure 28.5) deserve some attention:

If you register the VM, Hyper-V will bring the VM online and presume that you are content with the stored location of your VM files. This is not always ideal because most likely you will have your files located in a folder as ImportedVMs, and maybe you want to keep all your VMs together in a library or on a particular volume. Before selecting this option, ensure your VM files are where you want them.

When you choose the Restore option, you get to select a location to store the VM files, as shown in Figure 28.7.

### Figure 28.7
Choosing the import type allows you to select locations for your VM files.

![](img/41a83208e6906a3732620203b836cea7_1444_0.png)

The Copy option allows you to import the VM multiple times from a template and will create a new unique ID for each copied VM.

- Make your decision; then click Next to move on.
- In the Summary dialog box, click Finish to begin the import process.

It will take just a few seconds and come back with a status update. If there was a problem, you need to search the event log. A common issue is that no matching virtual switch was found, leaving the NICs unconnected.

- Select the newly imported VM.

You will see that all checkpoints you had have also imported.

- 9. Check the VM properties, and note the paths to the virtual disks.
- 10. Verify the connection state of the NICs.
- 11. When ready, click Start from the pane to bring the VM back online.

Just remember, though that you have now effectively cloned the old VM. If the old one is still running on another host and you bring this newly imported online, you'll have two identical machines on the network, which will certainly cause you problems!

You may be interested in how Hyper-V keeps track of VM configuration. When you create a VM, you tell it where to put the top-level folder containing the VM configuration. Figure 28.8 shows the configuration of VM on Hyper-V host VMHOST1-SRV.

### Figure 28.8
VM configuration files

![](img/41a83208e6906a3732620203b836cea7_1445_0.png)

The screenshot shows three folders: Snapshots, Virtual Hard Disks, and Virtual Machines. Each has virtual machines registered here its GUID, which is the real name of the virtual machine. For instance, the folder name corresponds to WS5021R2-SRV1. This folder contains the current memory state. Each VM also has an XML document named after the GUID of the VM. This document is fully readable, although you should not edit it manually. If you look through it you will find the entire configuration of the VM. The XML file has all the virtual switches the VM is connected to listed by the GUID, not by the friendly name.

The Snapshot (this is the old term used for checkpoint) folder containing state information of each checkpoint: the current configuration of the processes and virtual hardware in .v file and all virtual memory in .bin file. The difference files of checkpoints are saved as .vhdx in Virtual Hard Disk folder.

When creating a VM or virtual disk, you can do it basically like any place. So, how does Hyper-V know to find everything? It uses symbolic links, which are very small files that refer to files in a way that is transparent to applications. Also, all relevant symbolic links are in the central location for Hyper-V: %systemroot%\ProgramData\Microsoft\Hyper-V. The folder ProgramData is hidden; visible only if you tell Windows Explorer not to hide files. Starting with Windows Server 2012 R2, you can actually view symbolic links such as Explorer. In Figure 28.9, you can see the description between symbolic links and ordinary files. The file size of symbolic links goes in 0 bytes.

### FIGURE 28.9
![](img/41a83208e6906a3732620203b836cea7_1446_0.png)

## Quick Migration and Live Migration

It is impossible to have full disclosure of server virtualization without mentioning quick migration and live migration. These are related but different technologies to move virtual machines between hosts. In previous versions of Hyper-V, you had the option to use shared storage with high-speed networks. In this section, we'll introduce you to quick migration and traditional live migration, and later we will discuss the new Shared Live Migration.

Quick migration works by saving the state of the VM, transferring control to another node, and restarting on that node. This process is predictable and reliable but not so fast that it passes unnoticed. Time is lost during saving and restoring the VM state, and it may take a number of minutes for VMs with a lot of memory.

Live Migration The second technology is live migration, called that because it is fast enough to move a VM to another node without loss of service. In Chapter 27, “Server Virtualization with Hyper-V,” we discussed some of the new enhancements to live migration in this release of Windows Server, including unlimited simultaneous live migrations, out-of-the-box compression, SMB Multichannel, and SMB Direct. Its key feature is that the unavailability of the VM during the actual move is very short and can be measured in subseconds. In other words, anyone using that VM will at most notice a second delay, but everything keeps working.

Live migration works roughly like this:

- 1. The migration is initiated. The VM configuration is transferred to the destination host, which builds a skeleton VM.
- 2. The memory store of the VM is locked, and a difference file is started.
- 3. The memory store of the VM is transferred to the destination node using the shared network. Clearly, this network should be as fast as possible. The destination node starts loading this memory into the skeleton VM.
- 4. The first difference file is locked, and a second one is started. The first difference file is transferred to the destination node. This process repeats until the difference files become small.
- 5. Up to now, the VM has kept running, but at this point, the VM is frozen, and the final difference file is transferred as well.
- 6. Control of the VHDX files of the VM is transferred to the destination node. This happens quickly.
- 7. The VM configuration is removed from the original node and registered on the destination node.
- 8. The VM starts running on the destination.

For obvious reasons, live migration is the more frequently used of the two migration technologies. The ability to move VMs between hosts opens up some interesting scenarios:

**VM Drain on Shutdown** If you are running a Hyper-V cluster, then you will find this feature useful. Any time you need to do something on a host that requires downtime, you can move all VMs away without downtime for VMs on Shutdown. This is extremely useful when using hardware maintenance like adding memory, patching, and so on. Essentially, when you shut down a Hyper-V host that is part of a Windows Server 2012 R2 virtual Machine failover cluster (even without putting it into maintenance mode), the VMs hosted on that node will automatically live-migrate to another node.

**On-demand Resource Allocation** You may have VMs that are running “hot” and are using a lot of CPU or disk I/O resources. With live migration, you can quickly move these VMs to a lightly loaded host, or alternatively, get other VMs out of the way. If you deploy System Center 2012, you can configure it to move these VMs automatically at times of heavy load.
