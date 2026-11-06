
The IoT system in its early evolution was based on a client/server model which is a centralized architecture. The entire communication must pass through the cloud servers. These servers authenticate the devices and connect them after identification to offer huge storage capacities and processing power. This centralized system suffers from the lack of flexibility for network expansion and rising costs to scale the infrastructure. Moreover, the centralized clouds require high maintenance costs, networking equipment, and larger server farms.

The expansion of IoT devices is required to hold the increasing amount of communications, and thus raises the subsequent cost to handle these communications. The major drawback of the centralized architecture is the bottleneck condition that arises because of increased load of communication and the low fault tolerance due to single point of failure. This eventually crashes the entire network. There are less technical experts for the IoT framework, and the centralized IoT model poses the issue of cost regarding life cycle management and its maintenance.

Hence, to address and face these issues of the centralized IoT model, there is a need to develop and improve security technologies. The concept of Blockchain is a promising technology and could answer the shortcomings of the centralized approach.

### 5.2.1 Blockchain Technology
Blockchain was invented in 2008 by Satoshi Nakamoto for use in the crypto currency bit coin, as its public transaction ledger. Blockchain can be abstracted as a database to keep track of ever growing records of data. The data here refer to the transactions involved in the business processes. The key feature of Blockchain is its distributed nature, ([Figure 5.1](#Ch05.xhtml#fig5_1)), which means that there is no single or master device to hold a chain of transactions. It rather keeps a copy of chain of data records on each participating node.

![Figure 5.1 Blockchain in IoT.](`Images/fig5_1.jpg`)

[Figure 5.1](#Ch05.xhtml#bck_fig5_1) Blockchain in IoT.

The fundamental concepts of Blockchain are those which already exist. It uses the techniques of public key cryptography, hashing, and digital signature. Public/private key pair is the basis of communication. Any node initiating a transaction signs by its private key. The identity of nodes is their public key, rather than their IP address. Distributed ledger along with the process of hashed keys on the blocks makes Blockchain strong models among its competitors.

A Blockchain consists of two types of elements:
1. Transactions are the actions created by the participants in the system.
2. Blocks record these transactions and make sure that they are in the correct sequence and have not been tampered with.

### 5.2.2 Functioning of Blockchain
When a node initiates a transaction, and wishes to add that transaction in the chain, the rest of the nodes in the network will validate it. The validity is verified by applying algorithms to the transactions. A transaction which is valid for one system may not be verified as valid by another system. Thus, the valid transactions differ among systems.

A block in Blockchain is a set of transactions which are valid, and then these transactions are sent to all the nodes in the network. They, in turn, validate the new block ([Figure 5.2](#Ch05.xhtml#fig5_2)). Each next block that is being generated contains a unique fingerprint (hash) of the previously block.

![Figure 5.2 Transaction management in Blockchain.](`Images/fig5_2.jpg`)

[Figure 5.2](#Ch05.xhtml#bck_fig5_2) Transaction management in Blockchain.

In an IoT network, the Blockchain can keep an immutable record of the history of smart devices. This feature enables the autonomous functioning of smart devices without the need for centralized authority. As a result, the Blockchain opens the door to a series of IoT scenarios that were remarkably difficult, or even impossible to implement without it.

### 5.2.3 Construction of Blocks
Blocks are the basic elements of a database in a Blockchain. These are identified by the hash identifier. Each block contains a timestamp and list of its own transactions. A block can contain multiple transactions in the form of a Merkle tree. A Merkle hash is the root of Merkle tree.

Each node of the tree keeps a copy of the Blockchain and these copies are all in synchronization with each other, so as to ensure confidentiality and to confirm a benchmark that all nodes keep the same copy of transactions at the same level. This way, Blockchain manages all the security aspects of an IoT network by ensuring its integrity, transparency, authenticity, and availability.

By leveraging the Blockchain, IoT solutions can enable secure, trusted, and authentic messaging between devices in an IoT network. In this model, the Blockchain will treat message exchanges between devices similar to financial transactions in a Bitcoin network. To enable message exchanges, devices will leverage smart contracts which then model the agreement/disagreement between the two parties.

The “distributed ledger” concept of Blockchain is growing as a topic of great interest in the tech industry and beyond. The ledger assigns a valid tag to the transaction and arranges them according to the timestamp of their generation.

Blockchain technology offers a solution of recording transactions or any digital interaction in a way that is designed to be secure and transparent, and is also highly resistant to node failures, provides greater efficiency, and as such, it carries the possibility of renewing the business themes in industries and enabling new models for business processes.

Blockchains use complex mathematical functions to create a secure and definitive record of who owns what, when. In other words, Blockchains keep a ledger – which businesses can also use to track credits, debits, and other transactions.

#### Example: Cooperatively Owned Self-driving Cars
Using current technologies, a company like Uber ([Figure 5.3](#Ch05.xhtml#fig5_3)) or Google maintains the servers necessary to run a self-driving car.

![Figure 5.3 Current system where we connect to a server for booking up a car.](`Images/fig5_3.jpg`)

[Figure 5.3](#Ch05.xhtml#bck_fig5_3) Current system where we connect to a server for booking up a car.

* Data are centralized with the service provider.
* Service providers compete to aggregate the most data to service the most customer.

Using a Blockchain-based service, any number of individuals could form an agreement between themselves to purchase a self-driving vehicle and share its maintenance among themselves (Figure5.4). Each cooperative group could form contracts with other groups and share usage of their vehicles among a wider group of peers.

* Individuals enter into smart contracts that define the ownership of machines, maintenance, requirement, and proper usage.
* Each group has their own agreement, and can enter into a new agreement with other groups.
* Reputation protocols allow for fluid exchange of information, services, and resources within and between groups.

![Figure 5.4 Blockchain system: Sharing machines.](`Images/fig5_4.jpg`)

Figure 5.4 Blockchain system: Sharing machines.

These groups can set their own rules and enforce them using reputation standards. For example, a group could create a monthly maintenance checkup requirement that each must fulfill at least once per year – if they had not completed that duty, then the car would not unlock for that individual ([Figure 5.5](#Ch05.xhtml#fig5_5)). The community could go a step further and block that individual’s access to other services if that was encoded in their rules.

![Figure 5.5 Blockchain system: Sharing machines like self-driving cars.](`Images/fig5_5.jpg`)

[Figure 5.5](#Ch05.xhtml#bck_fig5_5) Sharing machines like self-driving cars.
