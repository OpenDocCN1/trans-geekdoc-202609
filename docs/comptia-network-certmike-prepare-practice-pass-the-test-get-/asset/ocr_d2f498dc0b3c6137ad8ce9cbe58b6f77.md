# Chapter 2 · Network Topologies

Wide Area Network (WAN) A point-to-point link between two remote locations, typically provided by a third-party carrier. WANs are generally slower than LANs, but they can span longer distances. A WAN link can connect a single user to a remote LAN or connect two LANs, enabling users at each site to access resources at the other site.

Metropolitan Area Network (MAN) A collection of computers in a larger geographic area than a LAN, such as a neighborhood, district, or city. A MAN is essentially a collection of LANs connected together using WAN technology, such as fiber-optic links, to form an interconnect.

Personal Area Network (PAN) A collection of devices, such as smartphones, tablets, and laptops, that are in close proximity and usually belonging to a single person. A PAN is typically wireless, connecting the devices using a short-range medium such as infrared or Bluetooth, but it can also use cable connections, such as Universal Serial Bus (USB).

Campus Area Network (CAN) Larger than a LAN, but smaller than a MAN or WAN, which is a collection of LANs connected together using WAN links to service a school, enterprise, housing, or government campus. Unlike MANs or WANs, which typically rely on third-party service providers for their WAN connections, the networking equipment is usually owned by the campus tenant.

Storage Area Network (SAN) A collection of storage devices, such as disk arrays or network attached (SAN) units, connected to a network that provides servers with either direct block-level access or filesystem to the devices. The servers can access the storage as though it was installed locally. High-end SANs are typically fiber-optic networks dedicated to storage traffic, with block-level storage devices running a specialized protocol as Fibre Channel. However, there are lower-cost alternatives, such as iSI, which enables storage traffic to coexist with TCP/IP traffic on a standard Ethernet network.

> EXAM TIP

Objective 1.2 for the Network+ introduces some concepts that are explored in later chapters. For example, SANs receive only the most rudimentary coverage here but are examined further in Objective 1.7. Exam candidates should be conscious of these scattered topics so to evaluate how much time and preparation they deserve.

Software-Defined Wide Area Network (SDWAN) A type of wide area network in which the hardware providing the WAN connectivity is separated from links, that controls the traffic. This enables the network to combine various WAN technologies and dynamically route traffic by selecting the link that is most appropriate for the data being transmitted and the most efficient, based on current network conditions.