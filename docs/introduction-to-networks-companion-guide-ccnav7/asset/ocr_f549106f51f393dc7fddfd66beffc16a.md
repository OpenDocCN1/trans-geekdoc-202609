![](bbox=[0.22, 0.12, 0.78, 0.38])

# Figure 9-7 H4 Sends a Unicast ARP Reply

# Video—ARP Request (9.2.3)

# Video

An ARP request is sent when a device needs to determine the MAC address that is associated with an IPv4 address, and it does not have an entry for the IPv4 address in its ARP table.

ARP messages are encapsulated directly within an Ethernet frame. There is no IPv4 header. An ARP request is encapsulated in an Ethernet frame using the following header fields:

+   - **Destination MAC Address**: This is a broadcast address FF-FF-FF-FF-FF-FF, which requires all Ethernet NICs on the LAN to accept and process the ARP request.
- **Source MAC Address**: This is the MAC address of the sender of the ARP request.
- **Type**: ARP messages have a Type field setting of 0x806. This informs the receiving NIC that the data portion of the frame needs to be passed to the ARP process.

Because ARP requests are broadcasts, a switch floods them out all ports except for the receiving port. All Ethernet NICs on the LAN process broadcasts and must deliver the ARP request to the device's operating system for processing. Every device must process the ARP request to see if the target IPv4 address matches its own. A router does not forward broadcasts out other interfaces.

Only one device on a LAN has an IPv4 address that matches the target IPv4 address in the ARP request. All other devices do not reply.

Refer to the online course to view this video.