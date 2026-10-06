
# CHAPTER 12 WINDOWS 2012 R2 STORAGE: STORAGE SPACES, SAN ABILITIES, AND BETTER TOOLS

FIGURE 12-47

Sample output of get-physical disk for creating storage tiers

| PhysicalDisk | MediaType | FriendlyName | OperationalStatus | HealthStatus |
|---|---|---|---|---|
| Disk0 | SSD | Disk0 | OK | Healthy |
| Disk1 | SSD | Disk1 | OK | Healthy |
| Disk2 | HDD | Disk2 | OK | Healthy |
| Disk3 | HDD | Disk3 | OK | Healthy |

# CREATING SSD AND HDD POOLS

As you can see, we have SSD and HDD drives in our environment. Now we'll create our storage tiers. We're creating two tiers in our example (which is also the maximum), and then we'll create a virtual disk that will be allocated across the tiers. We will partition and format the disk for use:

```
$ssdtier = new-StorageTier -StoragePoolName "TestPool" FriendlyName SSD_Tier -Mediatype SSD
```

For the HDD tier we use the following syntax:

```
$hddtier = new-StorageTier -StoragePoolName "TestPool" FriendlyName HDD_Tier -Mediatype HDD
```

The next step is to create a virtual disk and tie it to the storage tiers. After you whether you can remap an existing virtual disk to a storage tier, the answer is no.

With in mind, we'll create a virtual disk, which we will tie to our storage tiers. Here is the syntax to use:

```
New-VirtualDisk -StoragePoolName TestPool -FriendlyName Tiered_VDisk -StorageTiers(@ssdtier, $hddtier) -StorageSizes(@10GB, 50GB) -ResiliencySetting Simple
```

FIGURE 12-48

Output of creating a virtual disk in storage tiers

| FriendlyName | ResiliencySetting | OperationalStatus | HealthStatus | IsManualAttach | Size |
|---|---|---|---|---|---|
| Tiered_Disk | Simple | OK | Healthy | False | 60 GB |

Most of the options will be familiar from creating a virtual disk earlier. However, we have two options to relating a virtual disk in a storage tier:

StorageTiers(@ssdtier, $hddtier) specifies the tiers you can use. This is not a hash table, so be careful not to use curly brackets. We have stored our tiers in separate variables for ease of reference.

StorageSizes(@10GB, 50GB) specifies the size of each tier and is referenced in the order you use in the -StorageTier option. As you can see in Figure 12-48, the total size is 60 GB, which is 10 GB + 50 GB.

# CREATING A STORAGE SPACE

From here you would need to create a volume as before storing data. We'll show you a quick PowerShell trick you can use to create a 20 GB volume on the disk and format it in all line! Here is the syntax:

```
Get-VirtualDisk | Get-Disk | New-Partition -Size 20GB -AssignDriveLetter | Format-Volume -Force -confirm:$false
```

See Figure 12.4 for the output of the command. Now you can navigate to the drive letter and copy a file.

# FIGURE 12.4

Creating a new partition and formatting it in PowerShell

| DriveLetter | FileSystemLabel | DriveType | Size | SizeRemaining | Format |
|---|---|---|---|---|---|
| | NTFS | Fixed | Healthy | 19.9 GB | 20 GB |
| C:\Windows | | | | | |

Take a moment to review the properties of the virtual disk we previously created. In Figure 12.50 notice how the capacity is split because it is between the different tiers.

# FIGURE 12.50

Properties of a tiered virtual disk

![](img/41a83208e6906a3732620203b836cea7_656_0.png)

# USING THE WRITE-BACK CACHE

Now we'll show you how to use one of the last features of Storage Spaces in Windows Server 2012 R2, the write-back cache. With storage tiers, you cannot enable this via the GUI; it must be done via PowerShell. Remember, the write-back cache can speed up applications because writing to cache is quick and doesn't have to wait for storage to commit the write.

The PowerShell command we used to build our storage tier and modify the name and the StorageTierSiers options. Add the -WriteCacheSize option with a size setting; in this case you want a write-back cache size of 2 GB.

```
VirtualDisk -StoragePoolFriendlyName TestPool -FriendlyTier_VDISK -StorageTiers($ssthtier) -StorageTiers($20GB, 70GB)-ResiliencySettingName Simple -WriteCacheSize 2GB
```

You will now create a virtual disk that will use storage tiers, with write-back cache enabled.

# STORAGE TIERS OPTIMIZATION

The final thing we discussed about storage tiers at the start of this chapter is that every night at 1:00 AM, it will run a job to reprioritize the storage and move around what needs to be in the fast tier versus the slow tier.

In Scheduler, choose Task Library > Microsoft > Windows > Storage Tiers Management. Task Scheduler lists a job Storage Tiers Optimization, as shown in Figure 12.51.

# FIGURE 12.51 Storage Tiers Optimization task

![](img/41a83208e6906a3732620203b836cea7_657_0.png)

You can modify the task or manually trigger it if necessary.

# iSCSI on Storage Spaces

iSCSI spaces are incredibly useful for providing scalable and reliable back-end storage. Think of the amount of money a company would have to invest to get the abilities we have already outlined. What would be really useful now is to combine all this powerful storage technology with iSCSI you can also manage systems (such as file servers, mail systems, virtualization clusters, and the like) to benefit from these features.

iSCSI requires a few elements to be configured in order for it to present logical unit numbers (LUNs) to remove machines. First, we'll explain a few items that make you iSCSI from a host server and remote server perspective that you'll need to know in order to understand the example we'll use:

- iSCSI Target Server: This allows iSCSI initiators to make a connection to the target service, which in turns the syntax for a VHD that is located on a target server's volume. To the target operating system, this appears as a VHD file. You can configure access control to secure the disk appropriately.

- iSCSI Virtual Disk: The iSCSI virtual disk in this case is an actual VHD when viewed on the target server, but when viewed from a client server or initiator point of view, it appears as a disk that can be mounted online or offline with volumes created on.

- iSCSI Initiator: The initiator is the client software to connect to a target server and access whichever iSCSI virtual disks have been presented and it is authorized to access.

This technology is commonplace in most businesses today, and it them them to create clusters for all sorts of business reasons. In my previous place of employment we used a Windows server with the iSCSI target server to create a Hyper-V cluster to run our production network. In the next section we'll walk you through an example of setting up the iSCSI target service, creating a virtual disk, and presenting it to a remote system.

# Adding the iSCSI Target Service

By default, the iSCSI target service is not enabled. You must add it, and you'll do this via PowerShell. The syntax for adding the Windows feature is:

```
Add-windowsfeature iSCITargetServer -IncludeManagementTools
```

A server reboot may be required after adding the feature. The iSCSI Target server is a File and Storage Services subfeature, and that means you can administer it via Server Manager console, as shown in Figure 12.52.

# CHAPTER 12 WINDOWS 2012 R2 STORAGE: STORAGE SPACES, SAN ABILITIES, AND BETTER TOOLS

# FIGURE 12.52
iSCSI target management

![](img/41a83208e6906a3732620203b836cea7_659_0.png)

# CREATING AN iSCSI VIRTUAL DISK

As you can see from Figure 12.52, there are two screens: iSCSI Virtual disks and iSCSI Targets. As we have already said, a target will present the iSCSI virtual disks that have been created. (Don't confuse them with virtual disks in Storage Spaces. They are different; iSCSI virtual appears as VHD files on the target server).

To demonstrate this, let's create an iSCSI virtual disk. In this example we will be using the E drive we created earlier from our tiered storage pool. Don't worry if you haven't set it up; all you need is a driver and folder to store the VHD you are going to create.

- 1. In the center of the iSCSI Virtual disks shown in Figure 12.52, click "Create an iSCSI virtual disk Wizard."

- 2. Select the Target server that's listed and a volume where you want to store the iSCSI virtual disk.

In this example this will be E as shown in Figure 12.53.

- 3. Give the iSCSI virtual disk a descriptive name; for example, if it's for a Hyper-V cluster, type VMCluster_VDisk. Notice the path in Figure 12.54.

- 4. Next, enter the size of the virtual disk; for our example type 50 GB.

Notice the options; you can choose whether you want to provision all the space at once using the fixed option, provision a dynamically expanding disk, or use a differing disk. These options will seem familiar if you are used to Hyper-V.

- 5. Choose Dynamically Expanding in this case.
