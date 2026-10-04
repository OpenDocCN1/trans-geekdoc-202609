
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

## Chapter 7

1. C. An Ethernet switch examines the destination MAC address and looks for a matching entry in its MAC address table to make a forwarding decision.

2. C. An Ethernet switch examines the destination MAC address and looks for a matching entry in its MAC address table to make a forwarding decision.

3. B. The LLC communicates with upper-layer protocols, such as IPv4 or IPv6.

4. C. The first 3 bytes of the MAC address, known as the OUI (organizationally unique identifier), are assigned to the vendor.

5. A. Cisco switches drop runt frames.

## Chapter 8

6. B and E. The minimum size of an Ethernet frame is 64 bytes. The expected maximum size of an Ethernet frame is 1518 bytes. The maximum might be higher, such as when VLAN tagging is required.

7. D. An Ethernet switch builds its MAC address table by examining and recording the source MAC addresses and incoming port numbers.

8. A and D. IEEE 802.3 is the IEEE standard for Ethernet. It uses unique MAC addresses to determine the Ethernet frame sent to and processed by the correct end device.

9. A. Although there are some situations in which duplicates may purposely occur, the vast majority of Ethernet MAC addresses are globally unique.

10. D. 01-00-5E means that this is a multicast Ethernet frame, and it is meant for devices belonging to this specific multicast group indicated by the following 24 bits.

11. A. The host will discard the frame. The destination MAC address is at the beginning of the frame so the device can immediately determine whether it is the destination of the frame.

12. D. Auto-MDIX allows the use of either a straight-through or crossover cable on a port.

13. A and C. The MAC sublayer is responsible for accessing the media, such as CSMA/CD with legacy hubs. It also adds framing, including both a header and trailer, to the encapsulated data.

14. D. 01-00-5E means that this is a multicast Ethernet frame, and it is meant for devices belonging to this specific multicast group indicated by the following 24 bits.

1. B. A router examines a packet's destination IP address to find the best match in the router's routing table.

2. B. If the destination IP address is on the same network as the sending host, then the packet is forwarded directly to the destination host. The default gateway is used only if the destination IP address is not on the same network segment as the sending host.

3. B. The router removes Layer 2 frames when the packet is received. The router encapsulates the packet in a new data link frame when forwarding the packet out the appropriate interface.

4. D. 127.0.0.1 is an IPv4 loopback address.

5. B. The upper-layer transport protocol TCP is responsible for reliability and for retransmitting any data that was not received.

6. B. IPv6 was developed primarily due to the exhaustion of IPv4 address space.

7. B. An IPv4 address is 32 bits.

8. C. A router examines a packet's destination IP address to find the best match in the router's routing table. The information in the routing table determines how to forward the packet.

9. B. When a router receives an IPv6 packet, it decrements the Hop Limit field by 1. If the Hop Limit equals 0, the router drops the packet.

10. C. The netstat -r command displays a routing table on a Windows host.

11. D. The OSI Layer 3 protocols IPv4 and IPv6 include the source and destination IP addresses.

12. C. The network layer MTU is based on the size of the MTU of the data link frame. IP was designed to be transmitted over many different lower-layer technologies.

13. B. The IPv6 header is a fixed length and has fewer fields than the IPv4 header. The IPv6 header does not include any fields for fragmentation or a payload length, which makes the processing of IPv6 packets more efficient.

## Chapter 9

1. C. The ARP request contains the known IPv4 address of the default gateway and requests the MAC address associated with this IPv4 address.

2. B. The ARP process maps known IPv4 addresses to MAC addresses on the same network.

3. A. The ARP table maps Layer 3 IPv4 addresses to Layer 2 MAC addresses.

4. C. The ARP process maps known IPv4 addresses to MAC addresses on the same network.

5. A. The routing table, ARP cache, and running configuration file are all maintained in RAM memory.

6. D. ARP tables contain mappings of IPv4 addresses to MAC addresses.

7. D. arp -a shows the MAC address used to reach a specific IPv4 address. The analyst can examine this information to see if it is the correct MAC address of the default gateway.

8. D. The ARP process maps known IPv4 addresses to unknown MAC addresses on the same network and stores this information in the local ARP table.

9. B. The ARP process maps known IPv4 addresses to MAC addresses on the same network and stores this information in the local ARP table. This information is then used to forward the Ethernet frame.

10. B. On a Layer 2 Ethernet switch, broadcast frames are forwarded out all ports except the incoming ports. Broadcast frames are not forwarded by routers.

11. C. ARP requests are sent as Ethernet broadcasts.

12. A. ICMPv6 Neighbor Solicitation messages are sent using special Ethernet and IPv6 multicast addresses. This allows the Ethernet NIC of the receiving device to determine whether the Neighbor Solicitation message is for itself without having to send it to the operating system for processing.

13. D. On a Layer 2 Ethernet switch, if the destination MAC address is not in the MAC address table, the frame is forwarded out all ports except the incoming ports. These frames are called unknown unicasts.

14. C and D. A Neighbor Solicitation message in IPv6 is the equivalent of an ARP request in IPv4, and a Neighbor Advertisement message in IPv6 is the equivalent of an ARP reply in IPv4.

## Chapter 10

1. C. Without a startup-config file stored in NVRAM, the router will boot up without any preconfigured commands.

2. B. The service password-encryption command encrypts all passwords in the
