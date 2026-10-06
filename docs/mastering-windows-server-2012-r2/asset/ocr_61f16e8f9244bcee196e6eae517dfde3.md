# SHARED STORAGE BASICS

Microsoft's iSCSI Initiator is a software component built into all Windows Server operating systems since 2008 and is also included in Windows 7 and Windows 8. The iSCSI Initiator enables the connections on your Windows devices to utilize this technology.

As with the other storage technologies we are going to talk about here, we won't get into detail about all of the scaling and performance options available. The purpose of this chapter is to introduce the protocols.

# Fiber Channel

Fiber Channel (FC) is a high-speed connectivity network link running over twisted-pair copper or fiber-optic cable. The connection to your servers and storage is handled through the host bus adapter (HBA) using a protocol similar to TCP, Fiber Channel Protocol (FCP).
HAs operate in a grouping of nodes with specific worldwide names, which essentially act like IP addresses. Fiber Channel connects your drives and storage through a fiber switch and is managed in nodes that are allocated to storage network interfaces. This has long been the fastest type of network storage connectivity option available to organizations, but it doesn't come cheap!

# SAS Enclosures

Attached SCSI is a way to access devices that employ a serial connection over locally connected cables. UnlikeSCSI and FC, there is no network connectivity in SAS enclosures. The SAS technology supports earlier SCSI technologies, including printers, scanners, and other peripherals. SAS enclosures are large devices similar to a SAN that have multiple disks using different RAID levels to provide redundancy in the event of disk failure.

# RAID

Redundant Array of Independent Disks consists of multiple disks grouped together. The array allows you to build out fault-tolerant disks and scale storage to get high levels of performance. Multiple types of RAID exist that offer many different methods of performance and failover. The RAID technologies are the backbone of the internal workings of SCSI, SAS, and Fiber Channel SAS enclosures. The following link provides evaluation of the types of RAID and what to use, plus a breakdown of the different types in more detail: http://technet.microsoft.com/en-us/library/cc768889(v=18).aspx.

# SMB 3.0

Server Message Block (SMB) is a protocol specifically designed for file sharing and scaling out file shares or clusters. It sits on top of TCP/IP but can utilize other network protocols. SMB is used for accessing data and applications on resources that exist on a remote server. SMB has some specific requirements for setup:

+   - Windows Server 2012/2012 R2 failover cluster with a minimum of two nodes
- File shares must be created with the Continuous Availability property, which is the default.
- Files need to be on CSV volumes.
- Client computers accessing these resources must be Windows 8 or higher.
- Servers utilizing or accessing them must be Windows Server 2012 or higher.

563