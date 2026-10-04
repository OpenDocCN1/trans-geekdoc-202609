Source: 172.16.4.1/24
Destination: 172.16.4.253/24

![](bbox=[0.2, 0.15, 0.85, 0.48])

Figure 11-7 Unicast Transmission

IPv4 unicast host addresses are in the address range 1.1.1.1 to 223.255.255.255.
However, within this range are many addresses that are reserved for special purposes.
These special-purpose addresses are discussed later in this chapter.

# Broadcast (11.2.2)

Broadcast transmission refers to a device sending a message to all the devices on a network in one-to-all communications.

A broadcast packet has a destination IP address with all 1s in the host portion, or 32 1 bits.

> **Note**

IPv4 uses broadcast packets. However, there are no broadcast packets with IPv6.

A broadcast packet must be processed by all devices in the same broadcast domain.
A broadcast domain identifies all hosts on the same network segment. A broadcast may be directed or limited. A directed broadcast is sent to all hosts on a specific