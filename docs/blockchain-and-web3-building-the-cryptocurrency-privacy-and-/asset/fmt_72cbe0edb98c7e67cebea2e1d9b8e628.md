
# Figure 1.3 From Basic Internet to Web3 (Token Economy)

We argue that the future of Metaverse is built with seven layers of protocol like ISO internet standards, with blockchain technology at the heart of each layer to serve many functions, including governance protocol, incentive mechanism, global payment rail, trustless participation, and global immutable ledger for crucial activities in the Metaverse. In the following sections we will define those layers and describe blockchain's central role in all layers.

## Seven Layers of the Technology Stack

Similar to ISO internet standards, the Metaverse internet is composed of seven layers, from the physical and network layer at the bottom (the first layer) to the digital economy of the Metaverse at the seventh layer (see Figure 1.4). This section will dive down into each layer of the Metaverse. (For readers who are more interested in the Metaverse business applications, you may skip this section and come back to the technology stack discussion later.)

### Layer 1: The Physical and Network Layer

The physical layer includes IoT devices and AR/VR devices. The network layer includes the 5G/6G network and "mesh network." Because of the speed and pervasiveness of the 5G network, the blockchain transactions can be propagated much more efficiently and network bottlenecks can be reduced and thus improve the performance and scalability of blockchain. The data collected from IoT devices and from AR/VR devices can be propagated to the upper layers with data privacy and sovereignty protected using decentralized identity and then empower the Metaverse economy.

![Figure 1.4 The Seven-Layer Architecture for Metaverse](images/c01f004.png)

# Figure 1.4 The Seven-Layer Architecture for Metaverse

A mesh network allows network nodes to connect directly, dynamically, and nonhierarchically to as many other nodes as possible and cooperate with one another to efficiently route data from/to clients. This lack of dependency on one node allows for every node to participate in the relay of information. Mesh networks dynamically self-organize and self-configure, which can reduce installation overhead.

The ability to self-configure enables dynamic distribution of workloads, particularly in the event a few nodes should fail. This, in turn, contributes to fault-tolerance and reduced maintenance costs. Smart contract can be deployed on top of the mesh networks to incentivize workload execution, bandwidth sharing, and data sharing, which eventually serve as basic building blocks in the Metaverse internet. Blockchain technology can be used to enhance 5G security and enable mesh network connectivity and bandwidth via its immutability property, incentive mechanism, and global payment rail.

### Layer 2: The Decentralized Digital Identity Layer

Decentralized identity (DID) or self-sovereign identity solutions, such as Metaverse DNA digital identity Avatar, Serto, Sovrin, and many other DID implementations, are the initial attempt of allowing individuals to manage and control their own identity. The background is that traditional internet designs such as ISO's seven-layer protocol, and four-layer TCP/IP stack do not take into account digital identity. This is one of the main reasons why traditional internet security problems are frequent. That's why digital identities are now being suggested as the new firewall.

We still have time to structure Web3 with digital identity as the underlying core technology and ecological modules. The benefits of introducing DID in the second layer in the Web3 protocol include:

1.  **Increasing security** because of decentralized storage of identity data. There is no centralized database for identity, and each user holds and controls its own identity data. Hackers usually have more incentive to hack centralized identity data stores because of the sheer amount of identity data that can be acquired. For DID, the hacker will have less incentive because they have to hack each DID one by one.

2.  **Moving authentication** and access control from centralized policy store to end user's wallet application. This increases access control and promotes user awareness of security and privacy.

3.  **Enabling KYC/AML** (know your customer/anti-money laundering) with customer consent for metaverse applications. The majority of real-world metaverse applications will need KYC/AML in most countries to meet regulatory requirements. DID can be used to associate verifiable credentials granted from KYC/AML workflow to meet the regulatory requirements. Also, it's a mechanism to enable KYC once and then use everywhere, cutting the cost of regulatory compliance for metaverse applications.

4.  **Providing a foundational block** for data ownership authentication, which is critical for the data-sharing economy. In order for metaverse applications to reach their potential, the data must have the right ownership. In Web2.0, data sharing means "copy and paste," and data owners usually lose the ownership of data. In metaverse applications, the data can be shared with an expiration time and the data owner does not lose ownership of the data.

5.  **Authenticating off-chain data.** For off-chain data feeder or oracle, if the feeder and oracle are based on `decentralized` identity, the reputation of the oracle or data feeder can be established, and this enables on-chain smart contracts to get accurate data input for business applications.

### Layer 3: The Distributed Data Layer

The data will be stored in a distributed and decentralized fashion, using technologies such as IPFS, FileCoin, and BigChainDB. The decentralized peer-to-peer storage system has the following benefits:

1.  **Lower costs.** The decentralized data storage system leverages and incentivizes utilization of idle storage, using the token economics model, to reduce the waste of storage and thus reduce overall cost of storage. As decentralized storage markets mature, the overall cost of storage will be much lower compared to the centralized cloud storage system such as AWS S3 or other types of cloud storages. We see decentralized storage gradually taking over the centralized cloud storage market share in the next decade.

2.  **Higher reliability.** The data gets distributed and stored on multiple hosts in the decentralized network. The system saves copies of the original data (creating a deliberate data redundancy). In case of any loss or hardware failure, the system will present the backup copy. Additionally, chunks of all shared data can be separately encrypted using a unique hash. This extra security layer protects data from intruders. (The blockchain concept of "hash" will be explained in detail in later chapters.)

3.  **Increased speed.** Unlike a centralized storage system, decentralized storage systems use peer-to-peer technology. Data transmissions do not happen through the central server, which becomes slow at peak traffic times. With advanced routing and load balancing and caching algorithms, in the future, the speed can be improved further. In addition, since several copies of data get stored at multiple locations, downloads can become quicker.

4.  **Good price discovery and fair market pricing.** With millions of nodes present, the market for decentralized storage systems becomes a perfect competition. No single node can charge a premium price. This ensures good price discovery and fair pricing across the entire market. Such a market also guarantees that only good-quality nodes can compete and survive.

5.  **Increased security and privacy.** Most important of all, decentralized data storage systems provide a high level of security. They partition the data into smaller chunks, make copies of the original data, and then encrypt each portion separately using hashes or public-private keys. The whole process secures the data from bad actors.
