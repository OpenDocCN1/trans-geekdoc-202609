
## 82 - 2 Decentralized applications

the network. We could set and manage event filters used with smart contracts in the network through the API, or manage the mining if it was enabled in the node.

### 2.5.2.2 Hyperledger Fabric REST API

Hyperledger nodes facilitate a RESTful API service. The CoreAPI is composed of several endpoints, which reflects the APIs functionality. As the select the appropriate HTTP method to choose between creating, reading, and deleting the selected resources.

The root endpoints are /block, /chain, /chaincode, /network, /registrar/, and transactions. We use /block API to retrieve various blocks from the blockchain and the /chain API for the current state of the network. The /chaincode endpoint is used to deploy, invoke, and query a target chaincode, as the Hyperledger smart contracts. It implements the JSON RPC 2.0 specification and must have the required fields supplied within the payload. The /network gives information about the network of peer nodes comprising the blockchain network. As the HLF networks are permitted, the /registrar manages end-user registrations. We can use the /transactions/[UUID] endpoint to retrieve an individual transaction matching the UUID from blockchain.

### 2.5.2.3 Hyperledger Sawtooth REST API

Hyperledger Sawtooth also relies on the proven RESTful service approach. It systematically utilizes HTTP status codes to provide detailed feedback about the execution of a particular API call.

## 2.6 Distributed and support services

Several services extend the functions of the DLT and its on-chain logic in smart contracts. These services are not mandatory for DL network and DApp operation but make it easy, provide more control, and facilitate architectural refinements, welcome by the users.

Decentralized blockchain storage facilitates large quantities of data that would be unusable or impractical for the storage limitations of a regular blockchain. Name services add an additional layer of addressing or naming in DLT. They abstract the immutable DL network addresses and enable user-friendly naming. These names can be remapped to new DL network addresses if, for example, a smart contract address has changed. For smart contracts to interact with off-chain external data sources, special trusted gateways called oracles are needed. Moreover.

### 2.6.1 DL-based storage

The core application of blockchain technologies, a distributed ledger, is just distributed, safe, and trustworthy data storage. As we discussed, this has many different users in a variety of applications. However, many other applications require bulk data storage or file storage. This data cannot be written directly to the blockchain because it would greatly inflate the size of the ledger itself, hurting the performance of the chain in the long term.

There are several distributed blockchain-based storage solutions available, with its characteristics [43]. Some core concepts are shared between them. These concepts storage methods, replication, and incentives for hosts. Data is stored in a very similar way. Each file is split into small pieces called shards. Each shard is encrypted before being stored on a machine that is part of the storage network (not the actual blockchain network). Only the locations and hashes of these shards are then stored on the blockchain network. Having relatively small and uniform pieces of data also helps improve storage and transmission efficiency. The machines that these shards are stored on eventually have many shards of data of identical size.

Another shared concept is data replication. The data needs to be protected in the case of network failures. All shards need to be replicated across several machines. The exact number of replicas varies, but 3 is, generally, the minimum used. Since the shards do not have an easily identifiable connection between them, there must be a mechanism to ensure that the data is sufficiently replicated across the network.

In cloud storage infrastructure, files are stored with a company that can charge for the services provided. Public distributed systems are composed of many different hosts and no single entity to carry out actions like issuing invoices. Therefore, each distributed data storage system needs to have a way of rewarding the hosts of files. This varies from technology to technology, but some examples reward the owners with tokens or cryptocurrency that have value or give them more power to vote on the system.

Swarm is Ethereum's answer to blockchain-based storage and is designed to work in the Web3 ecosystem. Shards (called chunks in Swarm) of files are stored across multiple Swarm nodes, with a manifest stored in the main Ethereum blockchain network. Swarm nodes are just Ethereum nodes with an extra enabled mode of operation. They keep shards of files and make sure the shards are securely stored and accessible.

Files in the system can never actually be changed or deleted by the user. Instead, the user uploads a new file and changes the ENS reference to point to the new file. Swarm uses Ethereum's cryptocurrency to charge users for storage and reward hosts.

IPFS or Interplanetary File System is a more general distributed file system. It can be used with various blockchain networks or can be standalone. To access IPFS, a user must install an IPFS client. Once installed, users and applications interact with IPFS with HTTP requests to this client. Protocol Labs, the organization behind IPFS, is also working on Filecoin, designed to be the incentivization layer, providing nodes with an incentive to host data reliably.

- Storj is designed to look and perform like object storage from traditional cloud providers, but with a decentralized backend. Applications generally interact with its S3-compatible API. It uses its blockchain-based system with STORJ tokens as an incentivization method.

### 2.6.2 Oracles

The deterministic smart contract code is executed in a blockchain virtual machine. The execution is isolated from external, real-world environments, and the contract state is maintained and determined by actors inside the blockchain systems [44].

Despite the decentralized and trustless architectures of the blockchain systems, smart contracts on their own cannot access data from the external world. Oracles are needed to integrate smart contracts with the real world, if the non-deterministic smart contract code requires external information to make decisions. The real world, in case, implies external software, hardware, or actors and they are providing to be the on-chain application parts. Software resources can be, for example, Web APIs from a weather data provider or real-time or historic price-pairs for financial applications. Hardware resources could be an IoT sensor device, contributing sensory inputs, for example, RFID tag values, for a supply chain or a manufacturing management DApp. Hardware actors can provide inputs in the form of an answer to questions, their voting decisions, and the like.

Oracles collect and provide data feeds and input to smart contracts. On the blockchain, oracles are represented by smart contracts that serve data requests from other smart contracts. Oracles assure data attestation for these diverse off-chain sources and bring external data into the blockchain system in a trusted, verifiable way.

Figure 2.11 depicts the high-level oracle architecture. Decentralized application (see Section 2.2) comprises a blockchain network with a smart contract execution environment, blockchain-aware user interfaces, and DApp smart contracts. Oracle is an intermediary between the smart contract execution and external resources. It can request data from external sources, receive external data feeds, or keep historical records data values. It assures the validity of this data and serves it to the DApp smart contracts when needed.

![](img/0a07f1fa1a7ff1beaaa3170e7e172821_106_0.png)

Fig. 2.11: High-level oracle architecture.

There are two key trust models available to verify and validate the external data. In the centralized oracle trust model, only one node is used by the oracle solution to get data into a smart contract. Therefore, this node needs to be trusted. This model is appropriate for data in the external world that cannot be independently validated by multiple distributed parties, for instance, because the data has restricted access or transient sensor data. Examples of centralized validations in oracles are authenticity proofs (TLSNotary) for software oracles and trusted execution environments (TEE) for hardware oracles. The alternative is the decentralized oracle trust model. Here, the methods such as decentralized reputation, voting, or consensus-based decisions ensure a common agreement about the external data. Both models are used in practical oracle implementations to distinguish the features of various external sources.

In any case, oracles are off-chain architecture components that could be points of failure in whole blockchain-based systems. Even if the DL network and the on-chain smart contract application are highly reliable and trustworthy, there is a risk of oracles providing corrupt, malicious, or inaccurate data. Oracle security is, therefore, an emerging research area. Several oracle solutions have been proposed and implemented.
