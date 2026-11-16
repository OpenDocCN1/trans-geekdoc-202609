# Mirrored Ports and Network Taps

Monitoring devices have a harder time examining traffic on switched networks than on non-switched networks. To overcome this problem, port mirroring is used. Different vendors use different names for this technology. For example, Cisco Systems offers Switched Port Analyzer (SPAN), and 3Com offers Roving Analysis Port (RAP).

Port mirroring is used to send a copy of network packets from one switch port to a network monitoring connection on another switch port. Therefore, if you are using a managed switch, you can configure port mirroring to easily capture and analyze traffic. Although this works well in corporate environments and in situations where you have control of the managed switch, it is not as useful when a switch is unmanaged or where someone does not have access to the switch. In such cases, network taps can be used. A network tap provides another way to monitor a network and see all traffic, much like a hub. This functionality acts as a point to intercept traffic. For example, a Throwing Star LAN tap is a simple device that allows anyone to easily monitor Ethernet communications (see greatscottgadgets.com/throwingstar/).

# VLANs

Virtual LANs (VLANs) are used to segment network traffic to create smaller broadcast domains. VLANs reduce network congestion and increase bandwidth, and they do not need to be isolated to a single switch; a VLAN can span many switches throughout an organization.

You can extend VLANs by using a trunking protocol. A trunking protocol propagates the definition of a VLAN to the entire LAN. Trunking protocols work by encapsulating Ethernet frames. Two common trunking protocols are the 802.1Q standard and Cisco's proprietary Inter-Switch Link (ISL). The 802.1Q standard places information inside an Ethernet frame, whereas ISL wraps an Ethernet frame.

> Note
> Spanning Tree Protocol (STP), which is another protocol that can be