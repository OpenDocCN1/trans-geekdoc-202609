
## Switches

A switch performs in much the same way as a hub; however, switches are considered intelligent devices. A switch segments traffic by observing the source and destination MAC addresses of each data frame. In the classical sense, switches are OSI Layer 2 devices; modern switches can operate at higher layers and have the capability to work with different headers.

A sample technology that bridges Layer 2 and Layer 3 is known as Multiprotocol Label Switching (MPLS). MPLS is an OSI Layer 2 protocol. MPLS works with high-speed switches.

Commercial switches also offer virtual LAN (VLAN) capabilities. Such switches can operate at Layer 3 of the OSI model. A VLAN allows a group of devices on different physical LAN segments to communicate with each other as if they were all on the same logical LAN.

> The basic difference between Layer 2 switches and switches that work at higher layers is in the way they deal with addresses and tags.

Switches operate by storing MAC addresses in a lookup table that is located in random-access memory (RAM). This lookup table, which is also referred to as content-addressable memory (CAM), contains the information needed to match each MAC address to the corresponding port it is connected to. When the data frame enters the switch, it finds the target MAC address in the lookup table and matches it to the switch port the computer is attached to. The frame is forwarded to only that switch port; therefore, computers on all other ports never see the traffic. Switches offer the following advantages:

- They provide higher throughput than hubs.
- They provide VLAN capabilities.
- They can be configured for full duplex.
- They can be configured to span a port to support intrusion detection systems/intrusion prevention systems (IDSs/IPSs), network feeds, or monitoring.

> **Note**
> Microsegmentation allows you to segment networks even further. With microsegmentation, every node can have access to the entire bandwidth available in the transmission channel rather than sharing the bandwidth with others. Microsegmentation enables the creation of dedicated or private segments.

Not all switches are made the same. Switches can process an incoming frame in three ways:

- **Store-and-forward**: After a frame is completely input into the switch, the destination MAC address is analyzed to block or forward the frame.
- **Cut-through**: This faster design is similar to the store-and-forward design, but it examines only the first 6 bytes and then forwards the packet to its rightful owner.
- **Fragment free**: This is a Cisco Systems design that has a lower error rate than the other designs.

> **Note**
> Originally, switches were Layer 2 devices; today, switches can be found at Layer 3 of the OSI model and can work up to Layer 7. Higher-layer switches are known as content switches, content-services switches, or application switches.

## Mirrored Ports and Network Taps

Monitoring devices have a harder time examining traffic on switched networks than on non-switched networks. To overcome this problem, port mirroring is used. Different vendors use different names for this technology. For example, Cisco Systems offers Switched Port Analyzer (SPAN), and 3Com offers Roving Analysis Port (RAP).

Port mirroring is used to send a copy of network packets from one switch port to a network monitoring connection on another switch port. Therefore, if you are using a managed switch, you can configure port mirroring to easily capture and analyze traffic. Although this works well in corporate environments and in situations where you have control of the managed switch, it is not as useful when a switch is unmanaged or where someone does not have access to the switch. In such cases, network taps can be used. A network tap provides another way to monitor a network and see all traffic, much like a hub. This functionality acts as a point to intercept traffic. For example, a Throwing Star LAN tap is a simple device that allows anyone to easily monitor Ethernet communications (see greatscottgadgets.com/throwingstar/).

## VLANs

Virtual LANs (VLANs) are used to segment network traffic to create smaller broadcast domains. VLANs reduce network congestion and increase bandwidth, and they do not need to be isolated to a single switch; a VLAN can span many switches throughout an organization.

You can extend VLANs by using a trunking protocol. A trunking protocol propagates the definition of a VLAN to the entire LAN. Trunking protocols work by encapsulating Ethernet frames. Two common trunking protocols are the 802.1Q standard and Cisco's proprietary Inter-Switch Link (ISL). The 802.1Q standard places information inside an Ethernet frame, whereas ISL wraps an Ethernet frame.

> **Note**
> Spanning Tree Protocol (STP), which is another protocol that can be used in a VLAN, is used to prevent networking loops, build active paths, and provide for backup paths in the event that an active path or link fails. The newest version is Rapid Spanning Tree Protocol (RSTP), which is backward compatible with STP and provides significantly faster spanning tree convergence.

Virtual Extensible LAN (VXLAN) is a technology designed to provide the same Ethernet Layer 2 network services as a VLAN but with greater extensibility and flexibility. VXLAN supports the virtualization of a data center network while addressing the needs of multi-tenant data centers by providing the necessary segmentation on a large scale.

> **Note**
> VXLAN is an encapsulation protocol that provides mechanisms to aggregate and tunnel multiple Layer 2 subnetworks across a Layer 3 infrastructure.

Trunking security is an important concern in VLANs. A trunk is simply a link between two switches that carries the data of more than one VLAN. A security professional should be aware that an attacker who can get access to a trunked connection can potentially jump from one VLAN to another. This is called VLAN hopping. It is very important to ensure that trunked connections are secure so that malicious activity cannot occur.

> **ExamAlert**
> VLAN hopping is a hacking technique that enables attackers to send packets outside a VLAN. These attacks are generally launched by tagging the traffic with a VLAN ID that is outside the attacker's VLAN.

## Routers

Routers reside at Layer 3 of the OSI model. Routers are usually associated with IP, which sends blocks of data that have been formatted into packets. IP is considered a best-effort delivery protocol, and IP packets are examined and processed by routers. Routers can connect networks that have the same or different media types.

A router’s primary purpose is to forward IP packets toward their destination through a process known as *routing*. Whereas bridges and switches examine the physical frame, routers focus on the information in the IP header. One important item in the IP header is the IP address. As mentioned earlier, an IP address is a logical address; it is laid out in dotted-decimal notation format. The IPv4 address format is four decimal numbers separated by decimal points. Each of these decimal numbers is 1 byte in length, supporting values from 0 to 255. IPv4 addresses are separated into the following classes:

- Class A: A Class A network consists of up to 16,777,214 client devices. The address range can extend from 1 to 126.
- Class B: A Class B network consists of up to 65,534 client devices. The address range can extend from 128 to 191.
- Class C: A Class C network can have 245 devices. The address range can extend from 192 to 223.
- Class D: A Class D network is reserved for multicasting. The address range can extend from 224 to 239.
- Class E: A Class E network is reserved for experimental purposes. The addresses range from 240 to 254.

> **ExamAlert**
>
> You may have noticed that the 127.0.0.0 address range is missing from the preceding list. Although officially part of the class A address range, it is used for loopback. The CISSP exam may test you on such details.
