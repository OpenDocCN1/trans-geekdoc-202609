file. Seeding is the process of uploading files to other nodes on the network once your copy of the file has finished downloading. However, quitting the swarm after your download is complete is called leeching. If every node leeches, BitTorrent would not work at all [12].

# Types of P2P Network

# Unstructured Network

An unstructured network does not follow any specific structure. As shown in Fig. (3), nodes which are depicted by circles, are connected randomly to each other. A new peer who wants to join the network can copy existing links of another node and forms its links over time. It is easy to build an unstructured peer-to-peer network. However, not having a definite structure is its limitation. A peer floods the network with queries to find desired data. At times it becomes difficult for peers to find out the desired data. Flooding of queries does not always give desirable results and hence becomes a bottleneck for network traffic.

![](bbox=[0.34, 0.445, 0.645, 0.635])

Fig. (3). Unstructured peer-2-peer network layout.

# Structured Network

Structured peer-to-peer network overcomes the issue of unstructured networks by maintaining proper structure. The most common type of P2P network implements a distributed Hash table (DHT) [11]. It maintains the information in the network. A hash function is used by this network to assign values to all the content residing in a peer. Thus, hash table (Key, Value) determines which Peer is responsible for which content. Whenever a Peer wants to search for some data it uses the Hash table (Global Protocol) to determine the Peers responsible for the data and then directs the search towards the responsible Peers. Hence, we get good network traffic in this scenario [13].