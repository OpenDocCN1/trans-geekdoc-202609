# Introduction (11.0)

Plenty of networks are still using IPv4 addressing today, while organizations are making the transition to IPv6. So it is still very important for network administrators to know everything they can about IPv4 addressing. This chapter covers the fundamental aspects of IPv4 addressing in detail. It covers how to segment a network into subnets and how to use variable-length subnet masking (VLSM) as part of an overall IPv4 addressing scheme. Subnetting is like cutting a pie into smaller and smaller pieces. Subnetting may seem overwhelming at first, but we show you some tricks to help you along the way. This chapter includes several videos, activities to help you practice subnetting, Packet Tracer activities, and labs. Once you get the hang of Pv4 addressing, you'll be on your way to network administration!

# IPv4 Address Structure (11.1)

This section presents the IPv4 address structure.

# Network and Host Portions (11.1.1)

An IPv4 address is a 32-bit hierarchical address that is made up of a network portion and a host portion. When determining the network portion versus the host portion, you must look at the 32-bit stream, as shown in Figure 11-1.

![](bbox=[0.2, 0.6, 0.8, 0.75])

Figure 11-1 Network and Host Portions of an IPv4 Address

The bits in the network portion of the address must be identical for all devices that reside in the same network. The bits in the host portion of the address must be unique to identify a specific host within a network. If two hosts have the same bit pattern in the specified network portion of the 32-bit stream, those two hosts reside in the same network.

But how do hosts know which portion of the 32 bits identifies the network and which identifies the host? That is the role of the subnet mask.