path to a destination.

RIP v1 allows routers to update their routing tables at programmable intervals. The default interval is 30 seconds. The continual sending of routing updates by RIP v1 means that network traffic builds up quickly. To prevent a packet from looping infinitely, RIP allows a maximum hop count of 15. If the destination network is more than 15 routers away, the network is considered unreachable and the packet is dropped.

The RIP v2 standard is defined in RFC 1723 and updated for cryptographic authentication by RFC 4822.⁶ RIP v2 provides the following advances over RIP v1:

+   - Carries a subnet mask.
+   - Supports password authentication security.
+   - Specifies the next hop address.
+   - Does not require that routes be aggregated on the network boundary.

# Open Shortest Path First (OSPF) versions 1 and 2

The OSPF v1 standard is defined in RFC 1131.⁷ Open Shortest Path First is an interior gateway routing protocol developed for IP networks based on the shortest path first or link-state algorithm. Routers use link-state algorithms to send routing information to all nodes in an internetwork by calculating the shortest path to each node based on a topography of the Internet constructed by each node. Each router sends that portion of the routing table (keeps track of routes to particular network destinations) that describes the state of its own links, and it also sends the complete routing structure (topography).

The advantage of shortest path first algorithms is that their use results in smaller, more frequent updates everywhere. They converge quickly, thus preventing such problems as routing loops and Count-to-Infinity (when routers continuously increment the hop count to a particular network). This makes for a more stable network. The disadvantage of shortest path first algorithms is that they require large amounts of CPU power and memory.

OSPF v2 is defined in RFC 1583 and updated by RFC 2328.⁸ It is used to allow routers to dynamically learn routes from other routers and to advertise routes to other routers. Advertisements containing routes are referred to as Link State Advertisements (LSAs) in OSPF. OSPF routers keep track of the state of all the various network connections (links) between itself and a network it is trying to send data to. This is the behavior that makes it a link-state routing protocol.

OSPF supports the use of classless IP address ranges and is very efficient. OSPF uses