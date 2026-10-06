
# 588 CHAPTER 11 SHARED STORAGE AND CLUSTERING INTRODUCTION

- 1. Build out a minimum of two virtual machines.

- 2. Create two virtual network switches based on your requirements.

If you need access to additional resources, you will need to create additional networks that are externally external virtual switches.

- 3. Connect the associated storage solution to your VMs, such as your virtual Fiber, iSCSI, or SMB storage.

- 4. Install Windows Server 2012 R2 on your virtual machine.

- 5. Install the Failover Clustering feature on each of the VMs in cluster.

- 6. Connect your network and storage to the VMs.

- 7. Run the Validate Cluster Configuration Wizard and make sure you get a positive result.

Configuring your guest-based clusters is essentially the same as configuring your host cluster; you want to connect and configure all the settings with the exception of the Hyper-V role, because all Hyper-V guests. If you are feeling more knowledgeable now that you have gone through this introduction on shared storage and clustering, we highly recommend looking at the Clustering and High-Availability blog on TechNet at http://blogs/msdn.com/b/clustering/.

# The Bottom Line

Use the available storage options for clustering. With the release of Windows Server 2012 R2, many more storage options are available for your clustering and high-availability solutions.

**Master It** You want to build out a JBOD solution and need the most effective type of disk capacity. The failover doesn't matter as much as space and speed. What technology should you consider?

**Use quorum to help in clustering.** A quorum is the minimum number of members required to be present at an assembly or meeting before it can validly proceed to transact business. This definition holds true for the use of a quorum in clustering.

**Master It** You have chosen to deploy an odd-numbered cluster with five nodes, and once the cluster is up and running, you host an application. After the installation the application has a major memory leak and starts seizing the servers and shutting them down. How many nodes will you lose before the cluster is completely offline?

**Build out host and guest clusters.** Clustering is a mix of software and hardware and can be hosted on physical servers or virtual machines. Windows Server 2012 R2 has the components and tools built in it to help you deploy your clusters, including a handy prerequisites wizard to validate that you have all the components and configurations in to successfully set up a cluster.

**Master It** When planning your host- and guest-based clusters, excluding the Hyper-V role, what is the difference between the two in setting up a cluster?

# Chapter 12

# Windows 2012 R2 Storage: Storage Spaces, SANish Abilities, and Better Tools

For those who have some time to play with Storage Spaces in Windows Server 2012, I bet you are excited about the new changes in R2. But before we discuss them, let's do a quick recap of Storage Spaces for those who are new to this feature.

Storage Spaces was introduced in Windows Server 2012 as a native feature. Remember, this is not RAID but something new that was designed for full-blown enterprise use. The basic function of Storage Spaces is to allow you to take just a bunch of disks (JBOD) and configure them in a pool. From here you can create virtual disks (the actual storage space) and volumes with fault tolerances of varying degrees. This type of configuration network (SAN) gives you great flexibility.

Imagine not having to invest in a large, expensive storage area network or in specialized training that your administrators would need to configure and maintain it. A core goal of Spaces is to provide a cost-effective solution for mission-critical storage. Storage spaces and pools are designed to grow on demand. Here is a list of some of the features in Storage Spaces that are introduced in Windows Server 2012:

- Just-in-time provisioning
- Fault resiliency (mirroring and parity)
- Intelligent error correction
- Multi-tenancy support
- Integration with CSV to allow scale-out scenarios

In this chapter, you will learn to:

- Create a storage pool on a virtual disk
- Create additional storage on a virtual disk
- Use deduplication techniques to reduce file size

# What’s New in Windows Server 2012 R2?

Since this book is about Windows Server 2012 R2, we'll tell you what's new in storage. Microsoft has included technology in Storage Spaces that you previously saw only in expensive storage arrays. The following sections detail the new technology.

# CHAPTER 12 WINDOWS 2012 R2 STORAGE: STORAGE SPACES, SANISH ABILITIES, AND BETTER TOOLS

# Tiered Storage Spaces

There are several classifications of disks in today's world storage, including Server Advance Technology Attachment (SATA), Serial Attached SCSI (SAS), Solid State Drive (SSD), and Fibre Channel. Choosing the correct storage for the job is essential. For example, if you need a file server, SSD is not a good choice: SSD is designed for speed, not capacity, and because file servers generally need capacity but not speed, SATA, which was designed for capacity rather than speed, is the better choice.

In Windows 2012 R2 you can have a maximum of two storage tiers, essentially a fast and a slow tier. These tiers use SSD for fast tier and SATA in slow tier automatically. The clever thing here is that an administrator doesn't have to decide where to place the data. Tiers Management Service will automatically analyze the data of your disks in 1 MB. It has two categories for assignment: hot spots and cold spots. Hot spots are areas of data that are accessed frequently; the assumption here is that since data is active, it is a “hot topic.” Cold spots are the opposite data that has not been accessed regularly. After the analysis, hot spots will be moved to the SSD tier and any identified cold spots will be assigned to the SATA tier. Analysis happens daily at 1:00 a.m. by default, but you can configure it, if you use Figure 12.1. If a bit needs to be on the fast tier all of the time, the administrator can “pin” the file to the fast tier.

FIGURE 12.1
Tiered Storage Management service in the Task Scheduler

![](img/41a83208e6906a3732620203b836cea7_625_0.png)

# Write-back cache

Write-back cache refers to how data is written to disk. Data is written to the cache first and will be stored until it is time to be flushed and committed. In general, writing and storing data in cache gives better performance and is considered another type of. If an app is written to the cache, it can hang off its I/O handle quickly and get back to other tasks. Certain workloads traditionally do not write-back caching because when the app writes data, it must be written to disk to avoid corruption. Hyper-V, for example, requires write-through. Tiered storage can be used in conjunction with a virtual disk (not VHD/VHDX in relation to Hyper-V and virtual machines in this case, but a virtual disk from a Storage Spaces perspective) to absorb any spikes in writes. The fast tier can then overcome the spike and allow Hyper-V to use write-back caching.

# Parallelized Repair

When a disk in a traditional RAID set, if you have a hot spot (a disk that can instantly take over the job of a failed disk in a RAID set), this hot spot will kick and the RAID array will start rebuilding the data on this disk. A performance impact on the disk subsystem is inevitable during the rebuild because all the data is being written to a single disk. The paralyzed process in Storage Spaces is a different. If a disk fails, the remaining healthy disks that have capability take ownership of the data that was stored on the failed disk and will serve users' requests across all spindles. Since all disks are now helping out, there should be impact. The repair process can bring in the hot spot or the administrator can replace the failed disk, and in the background it can be brought into the storage space.

# Low-level Improvement: Native 4K Sector Support

Originally, hard disks used a 512-byte-per-sector format, and with came limitations in storage size and performance. With ever-increasing demand on capacity and speed, a change was needed, and over the course of a few 4K sector disks became standard. However, software (such as file system utilities, operating systems, and database engines) was not necessarily quick to catch up. Most manufacturers emulated 4K sector disks 512-byte sectors for compatibility. This requires a bit of overhead because the entire 4K sector is read into memory, and then written back. Since there is a degree of manipulation happening, there is also a performance impact, which is acceptable in this case.

With 4K sector support, the data industry no longer emulates 512-byte sectors, which means the performance impact is gone.
The following list shows some of the apps and scenarios for 4K sector support:

- Ability to install Windows and boot from a 4K sector disk without emulation (4K native disk)
- New VHDX file format
- Full Hyper-V support
- Windows backup
- Full support with the New Technology File System (NTFS)
- Full support with the new Resilient File System (ReFS)
- Full support with Storage Spaces
- Full support with Windows Defender
- Inbox application support
