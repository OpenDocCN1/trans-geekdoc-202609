ISOC oversees the Internet Architecture Board (IAB), and EIA helps define electrical characteristics for data transmission.

3. C. The data link layer encapsulates data, usually Layer 3 packets, to be transmitted over different types of media such as Ethernet or Wi-Fi.

4. D. Logical topologies typically include the devices and types of networks used to transfer data between devices, such as an Ethernet LAN.

5. C. In a star topology, a central device is used to connect all end devices.

6. C. In a mesh network or full-mesh network, all end devices (or nodes) are connected to all other end devices.

7. B. Half-duplex is a type of transmission that can occur in either direction, but the data can flow in only one direction at a time.

8. C. The LLC is the sublayer used to identify which Layer 3 or network layer protocol, such as IPv6, is encapsulated within the Layer 2 frame.

9. A. CSMA/CD is used by legacy Ethernet hubs. Because today’s Ethernet LANs use full-duplex Ethernet switches, CSMA/CD is not required and is not used.

10. C and E. The two sublayers of the data link layer are LLC and MAC. The LLC sublayer takes the network protocol data, which is typically an IPv4 or IPv6 packet, and adds Layer 2 control information to help deliver the packet to the destination node. The MAC sublayer controls the NIC and other hardware that is responsible for sending and receiving data on the wired or wireless LAN/MAN medium.

11. C. Wireless networks (specified in IEEE 802.11) use CSMA/CA to manage access to the shared wireless medium.

12. B and C. The data link layer encapsulates Layer 3 packets (that is, IPv4 or IPv6 packets) into a Layer 2 data link frame such as Ethernet. The data link layer is also responsible for accessing the media, such as Ethernet or a wireless LAN, and for performing error detection.

13. C. Ethernet is a data link layer protocol that uses the MAC address to transmit an Ethernet frame from one Ethernet NIC to another Ethernet NIC on the same network.

14. C. CSMA/CD is used to contend for access on a shared, half-duplex media. The use of full-duplex switches means that Ethernet NICs can operate in full-duplex and no longer have to contend for access.

# Chapter 7

1. C. An Ethernet switch examines the destination MAC address and looks for a matching entry in its MAC address table to make a forwarding decision.

2. C. An Ethernet switch examines the destination MAC address and looks for a matching entry in its MAC address table to make a forwarding decision.

3. B. The LLC communicates with upper-layer protocols, such as IPv4 or IPv6.

4. C. The first 3 bytes of the MAC address, known as the OUI (organizationally unique identifier), are assigned to the vendor.

5. A. Cisco switches drop runt frames.