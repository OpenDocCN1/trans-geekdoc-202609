A unicast MAC address is a unique address that is used when a frame is sent from a single transmitting device to a single destination device.

In Figure 7-11, the destination MAC address and the destination IP address are both unicast.

![](bbox=[0.23, 0.21, 0.88, 0.56])

# Figure 7-11 Unicast Frame Transmission

A host with IPv4 address 192.168.1.5 (source) requests a web page from the server at IPv4 unicast address 192.168.1.200. For a unicast packet to be sent and received, a destination IP address must be in the IP packet header. A corresponding destination MAC address must also be present in the Ethernet frame header. The IP address and MAC address combine to deliver data to one specific destination host.

The process that a source host uses to determine the destination MAC address associated with an IPv4 address is known as Address Resolution Protocol (ARP). The process that a source host uses to determine the destination MAC address associated with an IPv6 address is known as Neighbor Discovery (ND).

# Note

The source MAC address must always be a unicast address.