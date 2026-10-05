
In traditional routing networks, packets are cached and forwarded downstream. Therefore, if a routing node receives two packets from source it forwards one after another, and queues the others in the meantime, even if both are headed for the same destination. This requires separate transmissions for each and every message delivered, decreases network efficiency. In network coding, algorithms are used to merge those two messages and the accumulated result is forwarded to the destination. After receiving the accumulated message, it is decoded at the destination using the same algorithm.

In order for this technique to work, the destination node needs to be completely synchronized with the transmitting nodes.

Network coding is perceived to be useful in wireless mesh networks, messaging networks, storage networks, multicasting networks, file-sharing-peer networks and other networks where the same data needs to be transmitted to a number of destination nodes. The regular topology change that occurs in peer-to-peer networks poses a challenge to the network coding technique because it complicates network synchronization. In addition, the peers may need a large amount of processing time while trying to decode data.

## Purpose of Network coding

Network coding is based on a simple, yet far-reaching idea. In a packet network, rather than simply routing packets, intermediate nodes compute and transmit functions of the packets that they receive. Many now-standard results are reviewed, in particular: the multicast capacity of a network is given by the least-capacity separating the source from any of its destinations; the multicast capacity is achievable with linear network coding over a finite field of sufficiently large size, and there exists a computationally efficient algorithm to find a set of capacity-achieving linear network coding coefficients; the multicast capacity is achieved with high probability over a sufficiently large field when the linear network coding coefficients are chosen at random. Allowing the nodes in a network to perform coding permits the multicast capacity of a network to be achieved with linear network coding, with potentially unbounded advantage over routing. Unlike optimal routing solutions to a multicast problem, an optimal linear network coding solution can be found in polynomial time. In practice, the random linear network coding approach results in multicast protocols that are robust to changes in the underlying network topology. Despite its optimality for multicasting, it turns out linear network coding does not, in general, suffice to achieve optimal throughputs for general flow problems.

## Network Coding Helpful in P2P Content Distribution

What are the potential benefits of network coding for P2P content distribution? Recall that the difficulty of P2P content distribution is finding an optimal block scheduling algorithm, which should minimize the file downloading time in a distributed manner. This becomes even more challenging when the overlay network is changing dynamically.

Without network coding, each peer has to decide which blocks to download from which neighbors, based on local information only. This may be suboptimal due to lack of a global view, since local rarest blocks may not be rarest blocks. In contrast, with network coding, all coded blocks are almost equally useful to any peer, and there is no need to locate and request global rarest blocks in the system. As such, an information bottleneck is avoided, which in turn reduces the file downloading time.

Data blocks refer to discrete units of information that are stored together as a group. Various computing and information systems, data is organized into blocks for efficient storage, retrieval, and management.

Another important benefit of network coding is the robustness to peer departures. Without network coding, it is possible that a few data blocks are lost, due to departures of the server as well as the peers who have these data blocks. In this unfortunate event, the original file cannot be reconstructed by the remaining peers. On the other hand, with network coding, the risk of losing certain data blocks is no longer a concern. Intuitively, since data blocks are mixed together, each of them is spreading to a large number of coded blocks in the system.

In summary, the use of network coding solves the scheduling problem in a surprisingly simple and efficient manner, leading to a shorter downloading time. Moreover, it provides desirable robustness to peer departures. There is no need to worry about losing certain data blocks any all. All of these contribute to the usefulness of network coding in P2P content distribution. In the following, we will present a number of theoretical results to substantiate these claimed advantages of network coding.

## Theory behind Network Coding

This theorem states that in a flow network, where information flows from one node to the next, the maximum amount of flow from the source to the sink (max-flow) is equal to the minimum capacity that would not allow any flow to pass from the source to sink when cut/removed from the network in a specific way (min-cut). Basically, if all receivers have the same min-cut from the source, then NC would allow all nodes to achieve the min-cut simultaneously. This capacity would also correspond to the maximum flow rate that each receiver could get if it were the only receiving node in the network. The simplest example that demonstrates the key idea and the benefits of NC in the multicast case is the butterfly network depicted in Figure 1.

Core Concepts in Computer Science: Computer Networks

## Basics of Network Coding

Source:

![](img/f7819d05465fc14719b3ebbba980271a_260_0.png)

Network Nodes:

Sink Nodes:

Figure 1: Butterfly Network.

The two source nodes, nodes 1 and 2, have messages A and B respectively, that both need to be transmitted to the two destination/sink nodes, 5 and 6. Each edge in this network can only carry a single message. If nodes could only route/retransmit, the central link would only be able to carry message A or message B, but not both of them at the same time. Assuming we sent message A through the central link between nodes 3 and 4, then node 5 would receive message A twice and never receive message B. The same problem would occur at node 6 if we sent message B through the central link, with node 6 never receiving A. We can immediately see that routing would be insufficient to transmit both to both sink nodes. This is where the operation on relay nodes comes into play; a simple linear code is demonstrated here, in this example node 5 would receive both A and A+B, from which it can decode B by subtracting these two values. Node 6 would utilize the same procedure to decode A after receiving both B and A+B. From this example we can see that other encoding techniques could be applied to a varying number of packets, in various network configurations. These techniques could greatly increase the amount of information that could be transmitted in a single instance, thus significantly improving the throughput and power efficiency of networks with two simultaneous unicast connections as shown below: This result can also be applied to wireless networks as shown below:

Source:

![](img/f7819d05465fc14719b3ebbba980271a_261_0.png)

Network Nodes:

Sink Nodes:

Figure 2: Modified wireless butterfly network.

The modified wireless butterfly network shown in Figure 2 is different from the original butterfly network in the sense that packet transmissions can be transmitted from the source node to more than one node. Thus, transmissions are represented using hyper-arcs, instead of arcs.

We now a brief and hopefully accessible overview of the theory behind, and the nature of network coding.

## Network Coding Schemes

The manner in which nodes encode and decode the packets they transmit/receive can have a huge impact on the resulting throughput of the network. The majority of the NC schemes in use nowadays have their basis in algebraic theory. Earlier schemes, such as the traditional XOR-coding scheme and the Deterministic Linear Network Coding scheme are deterministic in nature, the more common schemes in use are non-deterministic, meaning they are free from the constraint of having feedback information for every transmitted packet from all the receivers.

## Random Linear Network Coding

Here, we shall once again utilize a network model for a general communication system that consists of source, network and sink nodes connected by channels that are potentially lossy. We can represent such a system as a directed graph G = {V ,
