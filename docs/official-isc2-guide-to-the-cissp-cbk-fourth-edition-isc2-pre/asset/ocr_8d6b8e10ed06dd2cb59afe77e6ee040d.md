about bridges: They do not filter broadcasts.

Bridges do not prevent an intruder from intercepting traffic on the local segment. A common type of bridge for many organizations is a wireless bridge based upon one of the IEEE 802.11 standards. While wireless bridges offer compelling efficiencies, they can pose devastating security issues to organizations by effectively making all traffic crossing the bridge visible to anyone connected to the LAN. Wireless bridges must absolutely apply link-layer encryption and any other available native security features, such as access lists, to ensure secure operation.

Switches solve the same issues posed at the beginning of this section, except the solutions are more sophisticated and more expensive. Essentially, a basic switch is a multiport device to which LAN hosts connect. Switches forward frames only to the device specified in the frame’s destination MAC address, which greatly reduces unnecessary traffic. See Figure 4.9.

![](bbox=[0.18, 0.44, 0.82, 0.68])

Figure 4.9 – Simple switched network

In this very simple LAN, client A transmits traffic to the server. When the switch receives the traffic, it relays it out of the port to which the server is connected. Client B does not receive any of the traffic. On the other hand, if the switch were a hub, client B would receive the traffic transmitted between client A and the server.

Because client B does not receive the traffic between the other client and server, the likelihood of client B intercepting the traffic is reduced (there are sophisticated attacks that could trick a switch, especially a poorly configured one, into sending traffic to client B).