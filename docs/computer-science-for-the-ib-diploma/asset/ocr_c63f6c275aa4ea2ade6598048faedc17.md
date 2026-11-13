+   **Packet header**: The header of each packet contains information that helps ensure the efficient and reliable transmission of the packet across the network, such as the source and destination IP addresses. Additionally, each packet contains a sequence number that is used to reorder the packets at the destination into their correct sequence, so that the content of the data file is not jumbled. The header also contains error-checking information such as checksums, which calculate whether the packet has arrived correctly, or whether the source has to be asked to retransmit it.

+   **Routing**: Each packet is sent through the computer network independently of any of the other packets associated with it. This means that packets for the same file may travel different paths across the network, based on conditions such as congestion and route availability. This flexibility in routing helps networks optimize usage and provide for a robust environment that is more tolerant of failures within the network.

+   **Routers**: These devices determine the optimal path for each packet passing through to reach its destination. They inspect the packet destination address and use routing tables and algorithms to decide the next hop in the network to forward each packet to.

+   **Switches**: These devices are typically operated within local area networks and direct packets between devices on the same network. They use the MAC addresses to process and forward packets.

+   **Reassembly**: Once the packet has reached its destination, it is checked for sequencing information and then reassembled into the original file in the correct order. Importantly, because no two packets are guaranteed to be transmitted along the same path, it is impossible to assume that packets have arrived in the correct order. Additionally, some packets may have been lost or corrupted in transmission, so the source needs to be requested to retransmit those packets.

# ## A2.3.4 Static routing and dynamic routing in local area networks (HL)

> **Routing**: the process of selecting paths along a computer network to send network traffic, based on the routing table, network performance and protocols.

Network routing refers to the algorithms that determine the path for traffic in a network, or between and across multiple networks. Within local area networks, routing decisions can be handled by one of two methods: static or dynamic routing.

# ### Static routing

Static routing is where the network routes are manually configured and entered into a routing table by the network administrator. These routes do not change except by manual update.

This method is easy to implement in small networks where the routes do not change much, but can be too complex to manage in networks with hundreds or thousands of nodes. Static routing provides predictability in the behaviour of your network, and does not require additional processing or bandwidth due to one router communicating with another for route discovery and optimization.

In addition to the challenge of scale, other issues around static routing include the lack of fault tolerance as, if a connection fails, static routing does not automatically attempt to find a workaround; and the maintenance workload associated with it, as every small change in the network requires manual updating of the routing table.