![](bbox=[0.05, 0.08, 0.95, 0.55])

# EXHIBIT 6.17 LAN Scenario

a hub to which they each attach via a Cat 5 UTP cable. In this scenario, the hub could actually implement 10BASE-T or 100BASE-T Ethernet, or even a token ring.

The external and internal networks are connected through the firewall, which, in this case, will have two NICs. The two networks are separate and distinct; the firewall does not extend the broadcast domain of either network, and, in fact, these two networks would have different IP network identifiers.

The internal network at the main site is a collection of servers and user workstations that are interconnected via a set of switches. In this example, these are 8-port 100-Mbps Ethernet switches. Since there are more than 8 devices, the switches themselves need to be interconnected. There are several options for that:

+   - Stackable switches physically attach to each other, extending the switch’s backplane to create a larger switch (in this case, a 16-port switch).
+   - An optical fiber link can be used to interconnect the switch, usually at backplane speeds in the 1+-Gbps range.
+   - A UTP link might be used to interconnect the switches via two of the 100-Mbps ports.

To connect the LAN in Building #2 with the LAN at the main site, a point-to-point connection between a pair of bridges would suffice. In this case, the buildings are several kilometers apart, necessitating use of optical fiber.

In Building #2, there is another hub-based LAN, with a laptop using wireless technology, communicating with an access node that is also attached to the hub.

This chapter has only skimmed the surface of LAN concepts, standards, and technologies. Their study is important to the security professional, however, because LANs are the basis of all networking. As a network of networks, the Internet comprises