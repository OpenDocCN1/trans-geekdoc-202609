
# Intrusion Detection System for RPL Protocol Attacks in IoT

**Routing Table Overhead:** The proactive nature of RPL implies that the storing mode is activated, they generate and produce routing tables. Routing overflow involves false routes using DAO messages to overload a node’s routing table. This limits legitimate route building, affects network performance, and might cause memory overflow.

10.3.1.2 Indirect Attacks: These attacks are those in which the hostile node attacks another node to an overloaded network. It consists of three types of attacks:

**Increasing Rank Attack:** It intentionally increasing the RPL node’s rank to cause network loops. When the node wishes to modify its rank, it requires updating its node’s list by removing nodes with a higher rank with a low-rank value. When sending a packet to the root node, a node in a DODAG selects a parent from this list to reduce routing costs. A malicious node promotes a greater rank than it really has, which may lead to an attack if no loop avoidance method is used.

**Inconsistency Attack:** An DAG node identifies a RPL inconsistency when the packet arrives with a ‘O’ bit from a higher rank and vice versa [14], the node does not maintain the rank relationship. This could lead to loop formation in the graph. This problem is managed via the Rank-Error ‘R’ flag bit. One of two ways may occur when a node detects an inconsistency: (i) the node rejects the packet and (ii) the node rejects the packet and restarts the timer. Consequently, control messages can be issued frequently. The malicious node only needs to change the flags or add new flags to the header to compromise the integrity of the network. The direct result of this attack is a reset of the targeted node’s DIO trickle timer. This also depletes the batteries of the nodes neighbourhood and influences the availability of connections. The attack affects the node’s whole neighbourhood because it needs to filter excessive traffic. Furthermore, tampering with genuine traffic makes a target node can discard all packets. This can lead to a black hole attack.

**Version Number Modification:** The version number is sent down the DODAG graph without being altered in any, and the root node is the sole node that increases whenever there is a need for the rebuilding of the DODAG (also known as “global repair”). An earlier value implies that the node has not been updated to the new DODAG graph, whenever a DIO message is sent to the neighbours, an attacker may modify the version number by maliciously increasing this. An attack of this kind necessitates the needless rebuilding of the entire DODAG graph which can lead to exhaustion of node resources and congestion in the network. This attack has the possibility of causing several loops, leading to packet loss.

# 10.3.2 ATTACKS ON TOPOLOGY

Additionally, the RPL protocol is susceptible to topological assaults, which may be further classified into the following two categories:

# Network Optimization in Intelligent IoT Applications

10.3.2.1 Sub-Optimization Attacks: These attacks affect the network's optimum convergence capability; that, they inhibit the construction of optimal routes, hence impacting network traffic and degrading network services.

Routing Table Falsification: An adversary may attack by falsifying/forging the DAO control messages, forcing legitimate nodes to construct nonexistent downstream routes. As a result, when authorised nodes attempt to send data to nonexistent nodes, consequences can lead to unnecessary packet latency, packet drop, DAO inconsistency, and high control overhead results. This attack is only possible if the storage mode is enabled.

Sinkhole: An attack of this kind is made in two parts (i) the malicious node pulls a large amount of traffic by advertising false information data; (ii) after receiving the traffic in an illegal way, it alters or drops it. In RPL networks, this attack may be executed by altering the rank value. Due to this forged advertising, other nodes wrongly choose a malicious node as an appropriate partner, while delivering higher performance. The attack changes the network's topology or reduces its performance. Furthermore, the attacker can perform a blackhole attack if it decides to drop all communications [15].

Wormhole: Wormhole attack uses two RPL attacker nodes, considered as nodes 1 and 2, joined by a private network. Each packet received by node 1 is routed via the wormhole to node 2 and replayed afterwards. Wormhole attacks disrupt the routing route and are especially dangerous in RPL networks. When an adversary sends routing information through a tunnel to another portion of the network, that are truly false perceive each other as if they were neighbours. Consequently, based on the objective function, they cannot construct any optimal routes.

Routing Information Reply: Valid control messages received from other nodes are saved by a node and sent later in the network. This attack is highly harmful because the topology and routing routes are frequently updated in dynamic networks. It will result in a topology.

Worst Parent: This attack is the result of a “Rank attack,” which entails selecting the least preferred parent based is not optimized, leading to performance degradation. This attack is difficult to deal with child nodes depend on their parents to route packets, and neighbours cannot monitor it.

10.3.2.2 Isolation Attacks: These types of attacks on the topology isolate either a single node or a group of nodes in the RPL network. This implies that such types of nodes cannot interact with their parents or the root

Black hole: A malicious node discards all packets to transmit in a black hole attack. In combination with a sinkhole attack, this attack may be extremely harmful, and consequently, result in the loss of a substantial portion of the traffic. There is

also a grey hole (or selective forwarding attack) form of this technique in which the attacker discards a selective subset of the network trace.

DAO Inconsistency: It arises when a node has a previously learned downward route from a DAO message, but this specific route is not valid in the child node, hence delivers to a neighbour.

# Intrusion Detection System for RPL Protocol Attacks in IoT 179

# 10.3.3 ATTACKS ON TRAFFIC

10.3.3.1 Eavesdropping Attacks: The pervasiveness of RPL networks may enable the placement of malicious nodes engaged in eavesdropping activity such as:

**Sniffing:** This attack involves listening to the network traffic. This attack seems quite frequent in wired and wireless networks, and it threatens communication confidentiality. The attacker could use a compromised device or a shared medium to directly capture packets to carry out this attack. Because of its passive nature, this attack is hard to detect. When the attacker is external, the only option to avoid sniffing is to secure communications.

10.3.3.2 Traffic Analysis: This attack is possible when the packets are encrypted. Similar to sniffing attacks, by identifying parent-child links, the objective is to get information regarding the RPL network. A malicious node could be able to initiate further attacks using the information collected as a result of this attack. The consequences are dependent on the attacker's node rank.

10.3.3.3 Misappropriation Attacks: The identity of a valid node is stolen in misation attacks, and performance is overwhelmed. The RPL network is not significantly affected by these attacks. They enable the attacker to understand the network's topology better, gain high access, or intercept a huge proportion of the traffic. They are, however, often utilized as a preliminary to other types of attacks, like those found in the earlier categories.

10.3.3.4 Increased Rank: The lower the rank in a DODAG graph, the closer the node is to the root, and it is expected to manage more traffic. Misrepresenting its performance occurs when a malicious node purposefully broadcasts a lower value than possesses. Consequently, the attacker connects several valid nodes to the DODAG and brings in a significant portion of the traffic. An attacker may modify the rank value of the RPL protocol by falsifying DIO messages which lead to sinks and eavesdropping attacks.

10.3.3.5 Identity Attack: Identity attacks are a combination of spoofing and Sybil attacks.

A spoofing attack, also known as a clone ID attack, happens when a malicious node masquerades as a legal entity. The root node in an RPL network is essential in DODAG graph. It constructs and maintains the topology by transmitting routing details. The network traffic is sniffed by the attacker to find the root
