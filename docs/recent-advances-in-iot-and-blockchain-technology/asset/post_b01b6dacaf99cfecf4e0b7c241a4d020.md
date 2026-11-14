
However, Zilliqa is the first public blockchain to implement sharding, ensuring no difficulty to be encountered while sharing information among shards. It has achieved 2828 TPS, which is higher than Ethereum and Bitcoin blockchains. Zilliqa doesn't shard the nodes completely. It implements two types of data. One stores the state of blockchain. It is small on storage and integrates with all nodes on the network easily. The other is the history of the blockchain which is bulkier and sharded. This history can be queried by inter-node communication to obtain the necessary information from the relevant shards allowing Zilliqa to be scalable and decentralized at the same time. Near is a blockchain ecosystem allowing developers to make and deploy decentralized applications also called Dapps. It calls itself a “sharded, developer-friendly, proof of stake blockchain”. Sharding makes nodes remain small enough to run on cloud-hosted instances and maybe mobile phones in the future. Facebook has proposed a blockchain-based payment system, Libra, which might use some form of blockchain partitioning. The development team from Chainspace, recently acquired by Facebook, is mainly focused on blockchain sharding [10].

## P2P NETWORK

Peer-to-peer network (P2P) is a network of computer systems that can exchange files and data directly with each other without storing it in a separate server (client-server model). P2P enables any two computer systems or more to interconnect with each other without any intervention of a third party. In such a network, each computer system is called a node or “peer” [11]. It can take the role of a client and a server as well. Privileges and the distribution of tasks among the nodes are equal. InterPlanetary File System (IPFS) is an example of P2P network used in blockchain.

Let us understand file sharing on a P2P network with the help of BitTorrent. The BitTorrent platform is built on the P2P network. On BitTorrent, sharing and downloading files can be done efficiently. The computer that stores the data to be shared or downloaded is called seed. It then splits the file into a lot of pieces. Any node on the network who wants the file uses the BitTorrent client platform. This node would receive one part of the file. Over some time, it would receive the remaining chunks from other nodes. At a particular time, a peer would be downloading parts of the file that it does not have and simultaneously uploading other parts to some other peer on the same network. There is no sequential way for it. It is random in the process. Hence at any time, cooperation is required among the peers. Such a group of nodes is called a swarm. An enormous swarm means a popular file. The cooperation among peers makes the overall process faster. Eventually, every client on the network receives a complete copy of the file. Seeding is the process of uploading files to other nodes on the network once your copy of the file has finished downloading. However, quitting the swarm after your download is complete is called leeching. If every node leeches, BitTorrent would not work at all [12].

### Types of P2P Network

### Unstructured Network

An unstructured network does not follow any specific structure. As shown in Fig. (3), nodes which are depicted by circles, are connected randomly to each other. A new peer who wants to join the network can copy existing links of another node and forms its links over time. It is easy to build an unstructured peer-to-peer network. However, not having a definite structure is its limitation. A peer floods the network with queries to find desired data. At times it becomes difficult for peers to find out the desired data. Flooding of queries does not always give desirable results and hence becomes a bottleneck for network traffic.

![](img/acd73a27093a44d669c4d9968aa1626b_31_0.png)

Fig. (3). Unstructured peer-to-peer network layout.

### Structured Network

Structured peer-to-peer network overcomes the issue of unstructured networks by maintaining proper structure. The most common type of P2P network implements a distributed Hash table (DHT) [11]. It maintains the information in the network. A hash function is used by this network to assign values to all the content residing in a peer. Thus, hash table (Key, Value) determines which Peer is responsible for which content. Whenever a Peer wants to search for some data it uses the Hash table (Global Protocol) to determine the Peers responsible for the data and then directs the search towards the responsible Peers. Hence, we get good network traffic in this scenario [13].

As we can see in Fig. (4), hash value is assigned to the content inside every node (circle) in a structured peer-to-peer network and stored in the Distributed Hash Table (DHT), used to locate the node and its resources.

![](img/acd73a27093a44d669c4d9968aa1626b_32_0.png)

Fig. (4). Structured peer-to-peer network layout.

### Hybrid P2P Network

The hybrid model is a combination of pure P2P network and client-server model. The central server in this model keeps the information of peers helping peers to find each other. Currently, hybrid networks are better than both pure structured and unstructured P2P network in terms of performance [11].

In the client-server model, the client would request data retrieval from the server via the internet. If the server accepts the request, then it sends data packets back to the concerned client. The client does not have to share any of its resources. For example, a user wants to download some files from a website. The computer of the user is the client. The server provides it with the required resources.

Now consider a scenario where many users want to download the same file from the same website. The server would have to provide each client with a copy of the file so the working of the server becomes costly. Since all downloading is taking place at the same time, the server divides its power so that each client receives the file slowing the downloading speed. But in a P2P network, each node is a server and client when a client needs a lot of data than several other nodes collectively provide it. Therefore, the client can download data at a faster pace. A loss of connection between server and client in a centralized network would cause failure.

However, in a decentralized P2P architecture, all connections among the nodes must be broken to prevent complete data sharing.

The participation of peers in the network should be encouraged. Cooperation among them is vital for storage performance. The selfish behavior of any node would hamper the performance of the entire P2P network. It might be limited resources like storage and bandwidth that provoke such a self-centered attitude in peers. Data retrieval at any time is the prime goal for a P2P storage network [14]. Since there is no centralized server, all data should be available to peers present on the network even though some peers might be inactive. Availability of data can be made sure by various data redundancy processes.

Even a P2P storage system is vulnerable to various attacks. Let us look into a few of them and try to understand different possible defense mechanisms.

### Denial-of-Service (DoS) Attacks

DoS attacks can interfere with the storage application on the network leading to loss of services. It may use security measures such as verifications to carry out its attack. The attackers flood the target node with verification requests preventing sincere traffic on the network. Such is the most common form of DoS attack on a P2P network. DoS attacks are unquestionably hard to block as the number of computers the attacker involves is enormous, making it burdensome to trace back the attacker's origin. “Pricing” is commonly used to curb DoS attacks. It requires its clients to solve a complex puzzle that usually requires expensive computation. If the system senses to be under attack, the difficulty of the puzzle should be increased. It would reduce the magnitude of the attack [15]. However, this is only useful for smaller attacks but would fail against a massive distributed attack. Also, honest clients would require more computation power to solve puzzles that are not economically feasible and will waste a lot of power.

### Man-in-the-Middle Attacks

In this attack, the attacker inserts himself in a network node and does not reveal itself. It spies and influences the communication among these nodes. It may be responsible for spoofing and transmit false data in the network. It can also farm some private data and leave the network unsuspected. In a P2P network, it is impossible to identify a man-in-the-middle attack as there is no central authority for the network. Fortunately, this attack is useless in a P2P network. Nodes have same logic for authentication and data is shared to every node on the network. Ultimately spoofing becomes useless. However, if the authentication logic varies in the network, the implication of this attack would depend on the logic itself [15].
