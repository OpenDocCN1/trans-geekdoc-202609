Figure 9-5 illustrates the problem when sending a frame to another host on the same segment on an IPv4 network.

![](bbox=[0.2, 0.18, 0.82, 0.47])

Figure 9-5 A Host Does Not Know the MAC Address for a Destination

To send a packet to another host on the same local IPv4 network, a host must know the IPv4 address and the MAC address of the destination device. Device destination IPv4 addresses are either known or resolved by device name. However, MAC addresses must be discovered.

A device uses ARP to determine the destination MAC address of a local device when it knows its IPv4 address.

ARP provides two basic functions:

+   - Resolving IPv4 addresses to MAC addresses
- Maintaining a table of IPv4-to-MAC address mappings

# ARP Functions (9.2.2)

When a packet is sent to the data link layer to be encapsulated into an Ethernet frame, the device refers to a table in its memory to find the MAC address that is mapped to the IPv4 address. This table, which is stored temporarily in RAM, is called the ARP table or the ARP cache.