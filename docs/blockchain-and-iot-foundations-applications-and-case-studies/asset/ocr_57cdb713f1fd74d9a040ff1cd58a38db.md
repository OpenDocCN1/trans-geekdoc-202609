# Blockchain-Driven Solutions for IoT Data Security in Healthcare

+   * It does not yield a result.
* Draws an incorrect assumption.
* Responds with a purposely misleading result.
* Replies that various system components have varying effects.

In a blockchain peer-to-peer (P2P) network, each node maintains a copy of the entire blockchain ledger, and each new transaction that occurs on the network is broadcast to all nodes in the network. This ensures that all nodes have the same version of the blockchain and that all nodes are aware of all transactions. When a new block is added to the blockchain, each node in the network verifies the transactions in the block and checks that the block has been added in a valid way according to the consensus rules of the network. If the block is valid, it is added to each node's copy of the blockchain, and the process continues. Because the network is decentralized, there is no central authority that controls the blockchain, and transactions can be validated without the need for intermediaries. This makes the blockchain P2P network secure and resilient, it is not vulnerable to a single point of failure or attack.

# STEPS TO CONNECT BLOCKCHAIN IN A P2P NETWORK:

+    Consider the number of nodes to be connected in the network.
* Each node acts as a client-server node.
* Make an IP address for each node to be connected.
* Search for the new state command on the command prompt to find out the available port address.
* Run the blockchain program to establish the P2P network over the edge server.

# PROPOSED WORK

A simulation test is made where pseudo electronic health care data is generated and blockchain is applied to each patient's details. These secured details are connected in a distributed network using P2P network. This P2P is implemented using the Python program. Each node is completely checked with the available port address for the edge server and the Byzantine fault tolerance algorithm is implemented in all the nodes. This is depicted as the model for the proposed work in Figure 9.7.

Figure 9.8 shows the simulation result of implementing blockchain to the patient health detail. In Figure 9.9 the results of node 2 without applying BFT are shown and Figure 9.10 shows results of applying BFT in the P2P network. It is observed that node 2 is connected to the P2P network takes a minimum of 2 ms, maximum of 3 ms, and average of 2 ms to send data. When node 2 is connected using Byzantine fault tolerance the time taken to send data is a minimum of 1 ms, maximum of 3 ms, and average of 1 ms. So the transaction in BFT algorithm takes less time to commit the message. Results show that the blockchain transactions without the Byzantine fault tolerance algorithm in the P2P network take more time when compared with the Byzantine fault tolerance algorithm.