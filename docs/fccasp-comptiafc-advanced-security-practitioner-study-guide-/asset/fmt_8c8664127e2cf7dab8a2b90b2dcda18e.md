
### 3. Implement controls
The network should be designed with a series of technical controls, such as the following:

*   Intrusion detection system (IDS)/intrusion prevention system (IPS)
*   Firewalls
*   Network access control (NAC)

### 4. Harden your systems
Remove unnecessary services and applications.

### 5. Perform proper updates
Use patch management systems to roll out and deploy patches as needed.

### 6. Segment the infrastructure
Segment areas of the network where enterprise storage mechanisms are used.

### 7. Use encryption
Evaluate protection for data at rest and for data in transit.

### 8. Implement logging and auditing
Enterprise storage should have sufficient controls so that you can know who attempts to gain access, what requests fail, when changes to access are made, or when other suspicious activities occur.

### 9. Use change control
Use change control and IT change management to control all changes. Changes should occur in an ordered process.

### 10. Implement trunking security
Trunking security is typically used with VLANs. The concept is to block access to layer 2 devices based on their MAC address. Blocking the device by its MAC address effectively prevents the device from communicating through any network switch. This stops the device from propagating malicious traffic to any other network-connected devices.

Now that we've explored some of the security issues of enterprise storage, let's look at some of the technologies used in enterprise storage:

### 1. Virtual Storage
Over the last five to ten years there has been a growth in virtual storage options. These online entities typically focus either on storage or on sharing. The storage services are designed for storage of large files. Many companies are entering this market and now giving away storage, such as Microsoft's SkyDrive, Amazon's Cloud Drive, and Google Drive.

Virtual file sharing services are a second type of virtual storage. These services are not meant for long-term use. They allow users to transfer large files. Examples of these services include Dropbox, MediaFire, and Mozy. These virtual services work well if you are trying to share very large files or move information that is too big to fit as an attachment.

On the positive side, there are many great uses for these services, such as keeping a synchronized copy of your documents in the online collaboration; sharing documents; and synchronizing between desktops, laptops, tablets, and smartphones.

Disadvantages of these services include the fact that you are now placing assets outside the perimeter of the organization. There is also the issue of loss of control. If these providers go out of business, what happens to your data? Although these services do fill a gap, they can be used by individuals to move data illicitly. Another concern is the kind of controls placed on your data. Some of these services allow anyone to search sent files. An example is shown in [Figure 3.8](#c03.xhtml#c03-fig-0008).

In [Exercise 3.5](#c03.xhtml#c03-ex-05) you'll look at security issues involved in online storage.

### Network Attached Storage
`Network attached storage (NAS)` is a technology that contains or has slots for one or more hard drives. These hard drives are used for network storage. `NAS` is similar to direct access storage (`DAS`), but `DAS` is simply an extension of one system and has no networking capability.

Many `NAS` devices make use of the Linux OS and provide connectivity via network file sharing protocols. One of the most common protocols used is `Network File System (NFS)`. `NFS` is a standard designed to share files and applications over a network. `NFS` was developed by Sun Microsystems, back in the mid-1980s. The Windows-based counterpart used for file and application sharing is `Common Internet File System (CIFS)`; it is an open version of Microsoft's `Server Message Block (SMB)` protocol.

### 2. SAN
The Storage Network Industry Association (`SNIA`) defines a `SAN` as “a data storage system consisting of various storage elements, storage devices, computer systems, and/or appliances, plus all the control software, all communicating in efficient harmony over a network.” `SANs` are similar to `NAS`. One of the big differences is that a `NAS` appears to the client as a file server or stand-alone system. A `SAN` appears to the client OS as a local disk or volume that is available to be formatted and used locally as needed.

### 3. Virtual SAN
A `virtual SAN (VSAN)` is a `SAN` that offers isolation among devices that are physically connected to the same `SAN` fabric. A `VSAN` is sometimes called fabric virtualization. (`Fabric` can be defined as the structure of the `SAN`.) `VSANs` were developed to support independent virtual networking capability on a single switch. `VSANs` improve consolidation and simplify management by allowing for more efficient `SAN` utilization. `VSANs` allow a resource on any individual `VSAN` to be shared by other users on a different `VSAN` without merging the `SAN`'s fabrics.

### 4. Internet Small Computer System Interface (iSCSI)
`iSCSI` is a `SAN` standard used for connecting data storage facilities and allowing remote `SCSI` devices to communicate. Many see it as a replacement for Fibre Channel, because it does not require any special infrastructure and can run over existing IP LAN, MAN, or WAN networks. The idea behind `iSCSI` was to overcome `SCSI` limitations. `iSCSI` takes `SCSI` commands and encapsulates them inside `TCP/IP` packets. `iSCSI` scales to 10 Gb and is not as complex as Fiber Channel over Ethernet (`FCoE`). However, it does require some type of physical segmentation from the regular LAN.

### 5. Fiber Channel over Ethernet (FCoE)
`FCoE` is another transport protocol that is similar to `iSCSI`. `FCoE` can operate at speeds of 10 Gb per second and rides on top of the Ethernet protocol. Although it is fast, it has a disadvantage in that it is nonroutable. Because it operates higher up the stack, `iSCSI` is on top of the `TCP` and `UDP` protocols. Although `FCoE` has many advantages over `iSCSI`, it is susceptible to eavesdropping and DoS.

### 6. Host Bus Adapter (HBA) Allocation
The host bus adapter (`HBA`) is used to connect a host system to an enterprise storage device. `HBAs` can be allocated by either soft zoning or by persistent binding. Soft zoning is the most permissive, whereas persistent binding decreases address space and increases network complexity. To keep from having a single point of failure, more than one `HBA` adaptor may be used. The drawback is that this can make the system more complex and may require the use of multipathing. Microsoft's framework for multipathing is `Multipath I/O (MPIO)`. This technology is designed to reduce the effects of a failed `HBA` by offering an alternate data path between storage devices. This multipathing technique allows for up to 32 alternate paths to add redundancy and fault tolerance.

### 7. Logical Unit Number (LUN) Masking
`LUN` masking is implemented primarily at the `HBA` level. It is a number system that makes `LUN` numbers available to some but not to others. `LUN` masking implemented at this level is vulnerable to any attack that compromises the local adapter. Without `LUN` masking, every server would see all hard disks that the disk subsystem provides. `LUN` masking is a security feature in that it allows this information to be limited so that each server only sees what it needs and nothing more.

### 8. Redundancy (Location)
Location redundancy is the idea that content should be accessible from more than one location. An extra measure of redundancy can be provided by means of a replication service so that data is available even if the main storage backup system fails. This further enhances a company's resiliency and redundancy. Database shadowing, remote journaling, and electronic vaulting are all common methods used for redundancy. Some organizations use these techniques by themselves, whereas others combine these techniques with other backup methods.
