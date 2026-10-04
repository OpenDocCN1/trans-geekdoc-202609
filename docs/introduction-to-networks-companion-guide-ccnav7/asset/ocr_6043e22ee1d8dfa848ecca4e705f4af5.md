# IPv6 Neighbor Discovery—Address Resolution (9.3.3)

Much as with ARP for IPv4, IPv6 devices use IPv6 ND to determine the MAC address of a device that has a known IPv6 address.

ICMPv6 Neighbor Solicitation and Neighbor Advertisement messages are used for MAC address resolution. This is similar to ARP requests and ARP replies used by ARP for IPv4. For example, say that PC1 wants to ping PC2 at IPv6 address 2001:db8:acad:1:1. To determine the MAC address for the known IPv6 address, PC1 sends an ICMPv6 Neighbor Solicitation message, as illustrated in Figure 9-13.

![](bbox=[0.24, 0.3, 0.86, 0.7])

Figure 9-13 IPv6 Neighbor Discovery Process

ICMPv6 Neighbor Solicitation messages are sent using special Ethernet and IPv6 multicast addresses. This allows the Ethernet NIC of the receiving device to determine whether the Neighbor Solicitation message is for itself without having to send it to the operating system for processing.

PC2 replies to the request with an ICMPv6 Neighbor Advertisement message, which includes its MAC address.