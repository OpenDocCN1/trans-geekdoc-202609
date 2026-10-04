Table 8-1 shows the pertinent information from the R1 routing table.

# Table 8-1  R1 Routing Table

| Route | Next Hop or Exit Interface |
|---|---|
| 192.168.10.0/24 | G0/0/0 |
| 209.165.200.224/30 | G0/0/1 |
| 10.1.1.0/24 | Through R2 |
| Default Route 0.0.0.0/0 | Through R2 |

# IP Router Routing Table (8.5.2)

The routing table of a router contains network route entries that list all the possible known network destinations.

The routing table stores three types of route entries:

+   - *Directly connected networks*: These network route entries are active router interfaces. A router adds a directly connected route when an interface is configured with an IP address and is activated. Each router interface is connected to a different network segment. In Figure 8-15, the directly connected networks in the R1 IPv4 routing table would be 192.168.10.0/24 and 209.165.200.224/30.
- *Remote networks*: These network route entries are connected to other routers. Routers learn about remote networks either by being explicitly configured by an administrator or by exchanging route information using a dynamic routing protocol. In Figure 8-15, the remote network in the R1 IPv4 routing table would be 10.1.1.0/24.
- *Default route*: Like a host, most routers also include a default route entry, a gateway of last resort. The default route is used when there is no better (longer) match in the IP routing table. In Figure 8-15, the R1 IPv4 routing table would most likely include a default route to forward all packets to router R2.

Figure 8-15 identifies the directly connected and remote networks of router R1.

In Figure 8-15, R1 has two directly connect networks:

+   - 192.168.10.0/24
- 209.165.200.224/30

R1 also has remote networks (that is, 10.1.1.0/24 and the internet) that it can learn about.