Storage, and the ability to provide controlled access to it, is one of the most common requirements of any organization. Many different storage options are available. Before we get into the options available in Windows Server 2012 R2, review the basic components:

+   * iSCSI SAN
* Fiber Channel SAN
* SAS enclosures
* SMB 3.0 2012

With the feature advancements in Windows Server 2012 R2 specific to storage, you can start utilizing these components on the infrastructure you already own. Let's dig into these technologies for a fiber overview.

# Storage Area Network

A storage area network is a network-connected entity that is dedicated to storage. SAN technology is just a basic framework, and each type of SAN solution presents storage in its own unique way. What we are really talking about block-level storage that is available to resources over the network. SAN is typically a large device with numerous hard drives, and we divide and format them to connect to servers and computers over the network.

In addition, a SAN doesn't have to be a traditional network; it could be fiber Channel, for example. With Fiber Channel, the same basic principle applies; it is a device with disks but the network is fiber optic. In most organizations the storage network has a network switch dedicated and optimized for SAN. The data transfer to a SAN is typically known as the storage fabric. The main purpose of a SAN is to allow different types of servers, applications, and users from multiple places to access a storage pool, which can be accessed from any devices that interconnect with that storage fabric. Part of the storage is the host bus adapter (HBA). HBAs are the network interface cards (NICs) that connect the storage fabric to the resources that access the storage.

Many organizations it believe that a SAN provides the flexibility to deploy and redeploy servers and storage in a more dynamic fashion. Servers can boot directly from a SAN, while operating the operating system and its configurations in a larger, highly available location. If the physical server goes down, a new one can be put in its place, the operating system and the associated disks can be pointed to the new server much faster than rebuilding and restoring from tape.

We recommend you spend some time investigating these topics at a much deeper level, and if you have an existing SAN, you should start reading through the deployment and administration guides that accompany it.

# iSCSI

Internet Small Computer System Interface (iSCSI) has been around for many years and has been used as a way to allow computers or servers to communicate with disk drives or other storage devices as tape libraries. As iSCSI has adapted, the network infrastructure connecting your servers and computers. Gigabit-based networks are much more commonplace and allow you to run storage connections natively through these higher-bandwidth connections. iSCSI is used to facilitate the transfer of data over a TCP/IP (Ethernet) network. The iSCSI protocol lets you present the disk drives located in your SAN over an existing network to your servers.