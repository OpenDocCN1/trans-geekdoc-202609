
# Live Boot Media

**Live boot media** is a live operating system you boot off from a DVD or USB drive. Examples would be a WinPE disk or a live version of Ubuntu that allows you to boot to the operating system that resides on the removable media. Live media allows you to run tools from the live operating system but does not permanently store data after shutting the system down.

When you’re implementing any of these redundancy technologies, it is important to ensure diversity in your solution. Diversity adds to the security by ensuring that if one part of the solution is attacked and compromised, then the same attack will not be successful with the next part of the solution. There are many ways to incorporate diversity into your security solutions:

- **Technologies**: Use different technologies. For example, you can use NIC teaming to put redundancy on the network cards of each server, use clustering to give high availability to a database service, and use RAID on the storage drives that are used to hold the database files.
- **Vendors**: Use products from different vendors to add diversity. A great example is with firewalls—look to using firewall products from different vendors at different layers of the network.
- **Crypto**: Use different cryptographic algorithms and different keys with each implementation so that if the encryption is cracked, then the same crack will not work on each use of crypto.
- **Controls**: Use a mix of different types of security controls to protect your assets. For example, at the endpoints (workstations), you should patch systems, use antivirus/anti-malware software, use a host-based firewall, and ensure that users are educated on good computing and Internet practices. Each of these controls add to the security of the workstation.

## Understanding RAID

Performing a data backup is a great idea, and storing a copy of that backup offsite is an even better idea to help ensure that you can recover from any type of disaster. One of the problems with relying only on a backup solution is that if a drive fails on the server, users will need to wait for you to replace the drive and then to restore all the data—this could take hours, depending on the amount of data you are restoring.

To avoid having to replace the drive and to restore the data in the middle of the day during business hours, you could take advantage of fault-tolerant solutions such as *redundant array of inexpensive disks (RAID)*, also referred to as *redundant array of independent disks (RAID)*. RAID is a technology that duplicates data across drives so that if a drive fails, the other drives in the solution can provide the data. The benefit is that if a drive fails, you can wait to fix the problem at the end of the business day, knowing that the redundancy of your solution will ensure that no data is lost (except in the case of RAID 0).

![Image](exam.jpg)

> **For the Security+ exam, know that to protect disks from disasters, you need to configure the disks in a RAID solution.**

RAID has different types, known as levels, and each level provides a different benefit with a different type of redundancy. The following subsections describe popular RAID levels supported by different network operating systems.

### RAID 0

RAID level 0 is called *striping* or *striped volumes*. With RAID 0, multiple disks are used to create a volume; when data is saved to the volume, the data is split up and spread across all disks in the volume. The benefit of striped volumes is that all disks are written to at the same time, giving you a performance benefit. For example, if you are saving a 12MB file to drive D:, and drive D: is a striped volume made up of four disks, we can generalize the save operation by saying that each disk will save 3MB of data, and all disks will work at the same time to do that save operation that totals 12MB. If you had only one disk working for that 12MB save operation, it would take four times longer.

The disadvantage of RAID 0 is that no duplication of data occurs; therefore, if one of your hard drives fails within the volume, you can’t read any of the data. RAID 0 is strictly for the performance benefit in the read and write operations. [Figure 18-2](#ch18.xhtml#ch18fig2) shows an example of a RAID 0 setup.

![Image](f0720-01.jpg)

**FIGURE 18-2**  
Looking at RAID 0

![Images](job.jpg)

> **As an IT professional, I frequently create virtual machines, and I want those VMs to run as quickly as possible. My system at home has Hyper-V in Windows 10 installed, and I have created a RAID 0 volume that I run all my VMs from. Since I began doing this, my VMs are running five times faster!**

#### Configuring RAID 0 on a Windows System

Windows systems offer a software RAID feature, which means that the operating system is responsible for the creation and management of the RAID volume. A hardware RAID solution would offer a better-performing solution, but it would be more expensive.

Before you can start creating fault-tolerant volumes, you must have multiple hard drives installed on the systems with available space to create the RAID volume.

**EXERCISE 18-2**

![Images](video.jpg)

**Configuring RAID 0 on a Windows System**

In this exercise you configure a RAID 0 volume on the Windows Server system.

1. Log on to ServerA and then launch the Computer Management console.
2. In the Computer Management console, select Disk Management on the left side under Storage.
3. Right-click an area of unallocated space on disk 1 and choose New Striped Volume, as shown here:
   ![Image](f0721-01.jpg)
4. The New Striped Volume Wizard appears. Click Next.
5. You now need to choose the disks that will participate in the striped volume solution. Select disk 2 on the left, and click Add to add disk 2 to the striped volume. Notice that the disk you started the creation of the volume on was already selected as a member of the volume. Since we started the volume on disk 1 and added disk 2, we will have two disks in this solution.
6. Once you have added each disk, at the bottom of the dialog box, type the amount of space you want to use on each disk for the volume. Type `200` in the Select the Amount of Space in MB box and notice that each disk will use 200MB—for a total of 400MB for the entire volume, as indicated in the Total Volume Size in Megabytes (MB) box.
7. Click Next.
8. Assign a drive letter of `S` for Striped and then click Next.
9. On the Format Volume screen, ensure that NTFS is the file system and type a Volume Label of `Striped`. Ensure that Perform a Quick Format is selected and then click Next to format the volume for NTFS.
10. Click Finish, and the new striped volume will be created. Notice that drive S: shows multiple times because it is made up of multiple disks.
11. Close all windows.

Notice that the disks have been converted from basic disks to dynamic disks. Windows requires dynamic disks in order to use the RAID volume types. Older versions of Windows required you to convert the disk from basic disk to dynamic disk before being able to create the RAID volumes, but newer versions of Windows do it automatically for you when you create the RAID volume.

![Image](exam.jpg)

> **RAID 0, known as disk striping, splits the data across all disks in the volume. RAID 0 writes to all disks at the same time, decreasing the time it takes to read or write the data. There is no fault tolerance in RAID 0; it is strictly for performance benefits.**

### RAID 1

RAID 1 is known as *disk mirroring*. Disk mirroring uses two hard drives and duplicates the data from one drive to another. The fact that RAID 1 stores a second copy of the data on another member of the volume means that this solution does offer fault tolerance. *Fault tolerance* is the concept that if one part of the solution fails, another part will pick up the workload and the solution will continue to function with no data loss.
