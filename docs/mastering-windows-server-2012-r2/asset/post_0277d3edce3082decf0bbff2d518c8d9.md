
# CHAPTER 11 SHARED STORAGE AND CLUSTERING INTRODUCTION

Shared VHD One of the new features is shared VHD (virtual hard disk) for guest clusters, giving you the ability in Hyper-V environment to use .vhdx as your shared storage solution.

Virtual Machine Drain in Shutdown The VM drain shutdown enables the Hyper-V host to start a specific node and moving all of the VMs to a new host. This will also happen if the VM shuts down during an outage.

VM Network Health Monitoring VM network health monitoring allows you to migrate VMs even if a disconnect occurs on your virtual network. Additional new features permit to things the Cluster dashboard and node health detection that get into that dashboard.

Live Migrations Previous to Windows Server 2012, to do a live migration with no downtime required a shared storage in place that were leveraging. Windows Server 2012 allows you to move the VMs from host to host or without a cluster, and with the addition of SMB 3.0 file shares, the files you set up for this doesn't need to sit on a SAN. You can do live migrations from VMs that are on local disks attached to the server.

One of the most important factors to understanding in clustering is the quorum-what it does, why you need it, and what improvements have been made to Windows Server 2012 R2 to improve the quorum's resiliency. In the next section we'll explain what a quorum is and what you can gain a deeper understanding of its use in clustering.

# Understanding Quorum

According to Webster's New World College Dictionary, Third Edition, a quorum is (the minimum number of members required to be present at an assembly or meeting before it can validly proceed to business.) This definition holds true for the term quorum as it pertains to a cluster. The best way to start gathering the technical needs for your cluster is to understand what a quorum is and what it's used for.

The quorum has been around since the inception of clustering and has been a major component and an unsung hero of starts. In each revision of Windows Server, improvements to the quorum have been made to us where we are now with extremely advanced quorum capabilities in Windows Server 2012. The quorum is the setting that determines the number of failures a cluster can sustain and keep the cluster (services) online. Once you have exceeded the quorum threshold, that cluster goes offline.

The cluster does not count the nodes and resources, it doesn't look at the cluster capacity and decide to shut the services down. Think of it like this: There are 100 nodes in a cluster; that does not aware of the cluster what content or resources are over- or under-utilized. Unfortunately, if 50 of them down, the cluster shuts... responsibility of the quorum is to help prevent an anomaly called split-brain, where two nodes in a cluster are attempting to write the same file or ownership of the resources, potentially causing corruption.

The job of the quorum in capacity is to prevent the problem from happening and essentially decide whether the cluster can or should function, stopping a problematic node's service until it can communicate with the rest of the clusters. When the issue is resolved, the quorum will allow the problematic node to join the cluster group and restart all the needed services. The quorum decision is done through votes; each node in a cluster has a single vote, and the cluster itself can be configured as a witness node. The witness can be a file share or a disk (as a best practice from the Cluster team at Microsoft, you should always configure a cluster with an odd number of members). The odd number of nodes gives you the ability to have an even number of quorum votes, and the odd resource can be the witness for outages. Adding this additional node ensures that if the cluster goes down, the witness node will keep it alive.

# Highly Available Storage

Having a highly virtual infrastructure is a major factor in the success of your HA plan. Considerations for storage options and how to connect the storage to your virtual machines so they run uninterrupted when hardware failures are imperative. Design considerations include how to store your VMs and what kinds of components are required to provide the benefits for fault tolerance. The following is a list of highly available storage options:

- **Hardware** Most important is for the storage, SAN or iSCSI or JBOD (just a bunch of disks).
- **Power** You need stable and redundant power supplies. If you can provide secondary pathways, that is a plus.
- **Disks** HA storage should be able to tolerate a disk failure and continue to meet your needs.
- **Storage Network Hardware** Creating a highly available hardware solution involves removing the single points of failure, including the storage network components such as HBAs or networks adapters.
- **Storage Spaces** This new storage virtualization feature introduced in Windows Server 2012 allows you to use USB, Fiber Channel, iSCSI, SAS and SATA attached disks to create a virtual disk that you can use mirroring for protection, which allows for a disk failure without losing your data. The important part to understand is that this is best utilized by spanning your storage pools across heterogeneous disk types.
- **Multipath Input/Output** Multipath Input/Output (MPIO) is a Windows feature that allows your Fiber Channel and iSCSI storage to be accessible via multiple paths or for client Hyper-V to have HA as it accesses your storage solution. By having multiple paths, MPIO sees both storage as a location device, and it supports failover. MPIO does all of the work for you; if something goes offline, it will handle the immediate rerouting over the other connection.
- **Network Teaming and Fault Tolerance** If you are connecting Hyper-V hosts to storage, it is highly recommended that you set up the hosts with multiple network cards and pathways. You want want leverage redundancy with network teaming on any of your clustered resources, and when you use SMB/SMB Multichannel it will give you the best available bandwidth.

# Storage Spaces

Storage Spaces is considered one of the new features of Windows Server 2012 and Server 2012 R2. The main advantage is the ability to manage a bunch of disks as a single disk drive. The virtual disk type dictates how data is written across the physical disks.

# CHAPTER 11 SHARED STORAGE AND CLUSTERING INTRODUCTION

Currently there are three choices:

**Simple** As the name implies, this is a simple stripe without parity. Consider this for a RAID 0. A simple layout provides no redundancy, so any disk failure can cause problems with data access. It is used primarily to increase throughput and maximize capacity, example.

**Mirror** This is a RAID 1 configuration that increases reliability by using two disks (for example), which allows one to fail without causing interruption. The major drawback is the loss of disk space because one of the disks is used as a copy (mirror) of the other.

**Parity** This is similar to a RAID5 configuration; it is a striped set of data across disks with distributed parity. Striping data and information across multiple disks, it increases the reliability. With RAID 5, you need a minimum of three disks.

If you are unfamiliar with disk RAID I recommend you look at the following site for information on the background of RAID and RAID levels: http://en.wikipedia.org/wiki/RAID. Storage Spaces has three basic components:

**Physical Disks** If you are leveraging physical disks for your storage pools, here are the requirements:

- Minimum of one physical disk.
- Two disks to create a resilient virtual disk.
- Three physical disks for resilient mirroring with parity.
- Five physical disks for three-way mirroring.
- All hard disks must be unformatted.
- iSCSI, SATA, SAS, SCSI, and USB are supported disk types.

**Storage Pool** A storage pool consists of one or more physical disks to create a virtual pool. An unformatted disk can be added to a storage pool at any time.

**Virtual Disks** These are considered the same as physical disks for an application or user service. The benefit is that virtual disks are far more flexible, and they have the resiliency of physical disks with built-in mirroring.

Storage Spaces offers different types of provisioning that determine how much space is being used and how to allocate to the virtual disks. You can define the performance type and what you are to utilize to achieve it. Many design factors are involved in an increase or decrease in performance, such as disk size, speed, and type. Having a great plan and design will increase the performance type of your system.

The provisioning type is determined by how space is allocated to and your performance choices:

**Thin** provisioning allows you to allocate space using only the amount of space you needs. It provides flexibility but can reduce performance when the storage has to move and pull disk space from the pool as the size increases.

**Fixed** is reserved targeted space. For example, if you define 40 GB, that is the maximum that the virtual disk gets. It cannot be larger than the disk space of the pool. You can extend the fixed size by adding more disks to your storage pool, and the only performance impact you will see is if you add disks and extend an already defined disk. It takes a little resource time to spin all that.
