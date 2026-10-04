When a NIC receives an Ethernet frame, it examines the destination MAC address to see if it matches the physical MAC address that is stored in RAM. If there is no match, the device discards the frame. In Figure 7-10, H2 and H4 discard the frame. The MAC address matches for H4, so H4 passes the frame up the OSI layers, where the de-encapsulation process takes place.

| Destination Address | Source Address | Data |
|---|---|---|
| CC:CC:CC:CC:CC:CC | AA:AA:AA:AA:AA:AA | Encapsulated data |
| Frame Addressing |  |  |

![](bbox=[0.22, 0.35, 0.9, 0.62])

Figure 7-10 All Devices Receive the Frame, but Only the Destination Processes It

# Note

Ethernet NICs also accept frames if the destination MAC address is a broadcast or a multicast group of which the host is a member.

Any device that is the source or destination of an Ethernet frame will have an Ethernet NIC and, therefore, a MAC address. This includes workstations, servers, printers, mobile devices, and routers.

# Unicast MAC Address (7.2.4)

In Ethernet, different MAC addresses are used for Layer 2 unicast, broadcast, and multicast communications.