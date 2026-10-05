# Basics of Network Coding

Source:

![](bbox=[0.295, 0.095, 0.755, 0.535])

Network Nodes:

Sink Nodes:

Figure 1: Butterfly Network.

The two source nodes, nodes 1 and 2, have messages A and B respectively, that both need to be transmitted to the two destination/sink nodes, 5 and 6. Each edge in this network can only carry a single message. If nodes could only route/retransmit, the central link would only be able to carry message A or message B, but not both of them at the same time. Assuming we sent message A through the central link between nodes 3 and 4, then node 5 would receive message A twice and never receive message B. The same problem would occur at node 6 if we sent message B through the central link, with node 6 never receiving message A. We can immediately see that routing would be insufficient to transmit both messages since no routing scheme could simultaneously transmit A and B to both sink nodes. This is where the operation on relay nodes comes into play; a simple linear code is demonstrated here, in this example node 5 would receive both A and A+B, from which it can decode B by subtracting these two values. Node 6 would utilize the same procedure to decode A after receiving both B and A+B. From this example we can see that other encoding techniques could be applied to a varying number of packets, in various network configurations. These techniques could greatly increase the amount of information that could be transmitted in a single instance, thus significantly improving the throughput and power efficiency of networks with two simultaneous unicast connections as shown below: This result can also be applied to wireless networks as shown below: