# Network Segmentation

In an Ethernet LAN, devices locate other devices by using ARP. A switch propagates a broadcast out all interfaces except the interface on which it was received. Routers do not propagate broadcasts; instead, each router interface connects a broadcast domain, and broadcasts are propagated only within that specific domain. A large broadcast domain is a network that connects many hosts. A problem with a large broadcast domain is that the hosts can generate excessive broadcasts and negatively affect the network. The solution is to reduce the size of the network to create smaller broadcast domains in a process called subnetting. These smaller network spaces are called subnets. Subnetting reduces overall network traffic and improves network performance. An administrator may subnet by location, between networks, or by device type.

# Subnet an IPv4 Network

IPv4 subnets are created by using one or more of the host bits as network bits. This is done by extending the subnet mask to borrow some of the bits from the host portion of the address to create additional network bits. The more host bits that are borrowed, the more subnets that can be defined. The more bits that are borrowed to increase the number of subnets, the smaller the number of hosts per subnet. Networks are most easily subnetted at the octet boundaries: /8, /16, and /24. Subnets can borrow bits from any host bit position to create other masks.

# Subnet a /16 and a /8 Prefix

A situation requiring a larger number of subnets calls for an IPv4 network that has more host bits available to borrow. To create subnets, you must borrow bits from the host portion of the IPv4 address of the existing internetwork. Starting from the left with the first available host bit, borrow a single bit at a time until you reach the number of bits necessary to create the number of subnets required. When borrowing bits from a /16 address, start borrowing bits in the third octet, going from left to right. The first address is reserved for the network address, and the last address is reserved for the broadcast address.

# Subnet to Meet Requirements

A typical enterprise network contains an intranet and a DMZ, both of which have subnetting requirements and challenges. An intranet uses private IPv4 addressing space. The 10.0.0.0/8 network can also be subnetted using any other number of prefix lengths, such as /12, /18, /20, and so on, which means the network administrator has many options. Because devices in the DMZ need to be publicly accessible from the internet, these devices require public IPv4 addresses. An organization must maximize its own limited supply of public IPv4 addresses. To reduce the number of unused