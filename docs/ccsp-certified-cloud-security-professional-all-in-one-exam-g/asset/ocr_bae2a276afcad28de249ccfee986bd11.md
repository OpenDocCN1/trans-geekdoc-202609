# Chapter 6: Operations

201

compromise systems. In some instances, if the immediate patching is not possible based on the use and demands of the server, other mitigating efforts may be such as restricting access or temporarily disabling some services or components, until patching can serve to lower risk and exposure, depending on the classification of data within a system and the risk appetite of management. Patching in this sense applies to any and all software employed on a server, whether it is the operating system itself or software packages run within it.

+   EXAM TIP Make sure to remember the concept of applying mitigating factors which cannot be deployed immediately, such as temporarily disabling services or restricting access to services and APIs.

Along with patching, regular or continual scanning should be used with updated signatures to proactively discover any unpatched systems, validate whether patching has been successfully supplied, and potentially discover additional vulnerabilities through penetration testing.

# Storage Communication

With a cloud environment being completely virtualized, all communications are done via networked devices and connectivity, and this also applies to storage devices and communication with them. With a traditional data center, physical servers and hosts have storage directly integrated with them on dedicated hardware, or are connected to storage networks via controllers or fiber networks. Much like networks on physical appliances, storage communications with servers is done via dedicated hardware and cables that are not shared by other hosts; physical servers use their own cables and dedicated switches on storage networks.

With virtualized systems, storage traffic should, wherever possible, be segregated and isolated on its own LAN. Because of heavy network utilization and importance, should be considered LAN traffic and not WAN traffic, as latency issues are a major concern for storage systems versus typical network traffic, which is more resilient and flexible. While web service and general application typically have encrypted communications capabilities built in, can be added easily, this is often not the case with storage systems. In the instances where vendors supply this capability, should always be used, but in cases where it is not possible or supportable, having the storage traffic separated to a different LAN from application and user traffic will allow for great security and confidentiality of data transmissions.

The most prevalent communications protocol for network-based storage is iSCSI, which allows SCSI commands and features over TCP-based network. Whereas a traditional data center will have SAN (storage area network) setups with dedicated fiber channels, cables, and switches, in a cloud data center this is not possible with the use of virtualized hosts. In this case, iSCSI allows systems to use block-level storage that looks and behaves like a SAN with physical servers, but leverages the TCP network within a virtualized environment and cloud.