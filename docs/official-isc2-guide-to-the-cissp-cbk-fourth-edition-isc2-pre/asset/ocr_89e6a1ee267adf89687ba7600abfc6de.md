fact. TraceRoute is a tool that maps network routes by sending packets with small TTL values and watching the ICMP timeout announcements.

# Internet Group Management Protocol (IGMP)

IGMP is used to manage multicasting groups, which are a set of hosts anywhere on a network that are interested in a particular multicast. Multicast agents administer multicast groups, and hosts send IGMP messages to local agents to join and leave groups. There are three versions of IGMP, as highlighted below:10

+   - **Version 1 –** Multicast agents periodically send queries to a host on its network to update its database of multicast groups’ membership. Hosts stagger their replies to prevent a storm of traffic to the agent. When replies no longer come from a group, agents will stop forwarding multicasts to that group.
+   - **Version 2 –** This version extends the functionality of version 1. It defines two types of queries: a general query to determine membership of all groups and a group-specific query to determine the membership of a particular group. In addition, a member can notify all multicast routers that it wishes to leave a group.
+   - **Version 3 –** This version further enhances IGMP by allowing hosts to specify from which sources they want to receive multicasts.

For a listing of protocols associated with layer 3 of the OSI model, see the following:

+   - **IPv4/IPv6 –** Internet Protocol
+   - **DVMRP –** Distance Vector Multicast Routing Protocol
+   - **ICMP –** Internet Control Message Protocol
+   - **IGMP –** Internet Group Multicast Protocol
+   - **IPsec –** Internet Protocol Security
+   - **IPX –** Internetwork Packet Exchange
+   - **DDP –** Datagram Delivery Protocol
+   - **SPB –** Shortest Path Bridging

# Layer 4: Transport Layer

The transport layer creates an end-to-end transport between peer hosts. User Datagram Protocol (UDP) and Transmission Control Protocol (TCP) are important transport layer protocols in the TCP/IP suite. UDP does not ensure that transmissions are received without errors, and therefore it is classified as a connectionless, unreliable protocol. This