# Blockchain and IoT

is attained through a voting process, where nodes in the network vote on the validity of new transactions and the ordering of those transactions in the blockchain. One common approach to BFT consensus is the practical Byzantine fault tolerance (PBFT) protocol. In PBFT, a designated leader node is responsible for proposing new transactions to the network. The other nodes vote on the validity of the proposed transactions, and a new block representing a transaction is only added to the blockchain when a certain number of nodes have validated it.

Other BFT-based consensus mechanisms have been developed in recent years, such as the Tender Mint consensus used by the Cosmos network and the Clique consensus protocol used by the Ethereum network. BFT consensus mechanisms provide a significant level of security and resilience. Making them suitable for applications where trust and reliability are critical. However, BFT-based consensus mechanisms can be computationally expensive and may require a high degree of network coordination, making them less suitable for smaller networks or applications with low transaction volumes.

Many ideas from the Byzantine error tolerance algorithm used in distributed systems are carried over into the practical version of blockchain. In this instance, an agreement is reached to determine if a block is genuine. System nodes communicate with one another to add blocks to the chain. In this scenario, malicious nodes might alert about blocks, thus the network accepts the block as genuine if it is accepted by the maximum number of nodes [15].

Distributed systems are more prone to Byzantine disinformation than centralized ones. These problems are a result of system node disinformation. The members of distributed systems are largely unaware of the causes of these errors or false information. It is so challenging to identify this node as malicious or flawed because it may be acting weirdly and providing various responses to nodes in the network. Thus, to identify a faulty node, the system's hosts must reach an agreement. A mechanism that reaches a decision unaffected by a bad or malfunctioning node is referred to as a system with Byzantine fault tolerance [30].

> The BFT consensus consists of three steps:

+   1. Pre-prepare: Each backup node receives a notification from the leader node via a prewritten message.
2. Prepare: Upon getting the pre-prepared response from the leader, the backup nodes reply to all the remaining nodes, even the leader, with the prepared message. A node cannot be prepared until it has observed (f + 1) prepared data from the other nodes and has acquired pre-prepared information from the leader.
3. Commit: The nodes send a message called a commit if they are prepared. If a node sees (f + 1) committed messages, it will carry out the client's request.

Two main categories of Byzantine failures are arbitrary node failure and fail-stop failure. Several illustrations of random node failures are: