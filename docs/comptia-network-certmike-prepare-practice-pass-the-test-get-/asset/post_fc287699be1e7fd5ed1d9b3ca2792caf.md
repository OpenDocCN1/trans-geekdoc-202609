
30 seconds. Routers receiving the transmissions incorporate the information in their own routing tables, modifying the metric values to reflect the distance from the transit-routing router.

The first RIP standard was published in 1988, but it has since been enhanced several times, as follows:

- RIP Version 1 (RIPv1) Transmits the entire routing table using broadcast messages; supports classful addresses only; does not transmit subnet masks
- RIP Version 2 (RIPv2) Transmits the entire routing table using multicast messages, supports classless addressing; includes a subnet mask for each entry
- RIP Next Generation (RIPng) Transmits the entire routing table using IPv6-multicast messages

RIP is a distance vector routing protocol, which means it measures the distance between routers in terms of the number of hops between them. Each hop represents one router that packets must pass through to the destination. Therefore, traffic destined for a network that is 10 hops away must be forced by 10 routers to get there.

## Open Short Path First (OSPF)

Distance vector is not a precise way to measure the proximity of a router. A single hop could be a local area network (LAN) connection to 1,000 Mbps, or it could be a much slower area network (WAN) connection. This is why many of the other routing protocols use alternative measurements to calculate their metric values.

Open Short Path First (OSPF) is an open standard link routing protocol. Unlike distance vector protocols, link state protocols gather information about the network by transmitting messages. Using the information in the LSAs, the routers create a neighbor table and a topology table, essentially a map of the entire network. The routers then use information to build their routing tables.

Unlike distance vector protocols, link state protocols use various criteria to calculate the efficiency of routes through the network. In addition to hop counts, OSPF factors in the transmission speeds of the various network links, the current levels of traffic congestion on the various routes, and a cost specified by an administrator. The routers then use the Dijkstra algorithm to calculate the relative efficiency of routes to a given destination. OSPF routing tables supports multiple routes to the same destination with the same metric and administrative values. When this occurs, the router balances the outgoing traffic among duplicate routes.

Unlike RIP, OSPF does not transmit its entire routing table at regular intervals. Instead, it updates containing only the data that has changed, which conserves bandwidth and speeds up convergence. OSPF also does not have a hop limit, as RIP does. OSPF has many advantages over RIP, including route efficiency and convergence speed, but it also requires more processing power, memory, and storage from the router.

## Chapter 10 • Routing and Bandwidth Management

### Enhanced Interior Gateway Routing Protocol (EIGRP)

The Enhanced Interior Gateway Routing Protocol (EIGRP) is an updated version of the earlier Gateway Routing Protocol (IGP). Although ostensibly a distance vector protocol, EIGRP is sometimes referred to as a hybrid routing protocol because it includes both distance vector and link state routing characteristics.

EIGRP uses neighbor discovery to gather information about other routers. The protocol encapsulates its messages directly within IP datagrams; there is no TCP or UDP port number. Using the neighbor discovery information, the router creates a neighbor table and a topology table, much as in SPF. The topology table contains all the routes gathered from other routers. After calculating the best route to each network destination, the router places the entries in the routing table.

EIGRP does not rely solely on hop counts to calculate metrics; it also considers characteristics of the link to the destination network, including its bandwidth, traffic congestion, transmission delay, reliability, and its maximum transfer unit (MTU). To calculate the relative efficiency of a route, EIGRP uses the Diffusing Update Algorithm (DUAL).

RIP transmits distance updates to other routers. However, it does not send the entire routing table as RIP; it generates incremental updates containing only the information that changed, much like SPF.

Compared to RIP, EIGRP is much more scalable, due to its support for merging autonomous systems. An autonomous system (AS) is a group of adjacent routers that share their routing tables and the same routing protocol. This capability enables EIGRP to support large networks by splitting them into multiple AS.

## Border Gateway Protocol (BGP)

RIP, SPF, and EIGRP are all interior gateway protocols, meaning they are intended for use within an enterprise network. Border Gateway Protocol (BGP) is an exterior gateway protocol. In fact, BGP is the exterior gateway protocol, responsible for the IPv4 and IPv6 routing between autonomous systems all over the Internet. The routers in an AS with other routers using BGP are called border routers or edge routers.

BGP is classified as a path routing protocol. This is similar to distance vector protocols, except that it carries path information between autonomous systems. While it is possible to use BGP within an AS, it is primarily used to connect different autonomous systems. BGP is much more scalable than RIP, as it can handle much larger and more complex networks.

## Administrative Distance

| Route source | AD |
| :--- | :--- |
| Connected interface | 0 |
| Static | 1 |
| External BGP | 20 |
| Internal EIGRP | 90 |
| OSPF | 110 |
| RIP | 120 |
| External EIGRP | 170 |
| Internal BGP | 200 |
| Unknown | 255 |

## Bandwidth Management

Routers are network layer (layer 3) devices. The layer primarily responsible for end-to-end communication is the perfect place to implement technologies. One of these is bandwidth management, which refers to mechanisms for controlling the allocation of bandwidth to specific types of traffic. Networks carry different types of traffic with different requirements. For example, file transfers must be bit-perfect but can tolerate a delay some some packets. Web traffic can also tolerate delays and a few frames. Streaming audio and video can buffer their traffic and tolerate dropped frames. However, applications as Voice over IP (VoIP) work in real time; transmission delays and lost bits can result in calls being dropped. By managing the bandwidth, administrators ensure that traffic is prioritized.

## Traffic Shaping

Traffic shaping is a technique for delaying network traffic—usually in a buffer—to achieve an agreed-upon transmission rate. The technique can be applied to all traffic or to specific applications. For example, Internet service providers can use traffic shaping to limit the bandwidth used by peer-to-peer applications, allowing other types of traffic to proceed without limits. In other cases, service providers can use traffic shaping to ensure that their clients receive the bandwidth specified in their service level agreements. Enterprise administrators also use traffic shaping to monitor traffic on their networks to avoid additional charges. With that information, administrators can decide what limits need to be imposed and create rules to implement them. Traffic shaping can work by regulating either the bandwidth used to transmit data or the time during which the transmission occurs. For example, to prevent a 1 Gbps interface from exceeding a transmission speed of 500 Mbps, a router can transmit at its normal speed for half the time and buffer the outgoing data for the other half.
