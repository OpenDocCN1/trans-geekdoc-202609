
## 3.1 Distributed ledgers for IoT security 105

the blockchain transactions are utilized as a transport mechanism for encrypted content and decrypted out-of-chain. This approach enhances the confidentiality of user data in transactions but limits the use of user data in smart contracts.

Besides, information about users and usage patterns can be disclosed from blockchain transaction traffic too. We can carry out data analysis of the publicly available chain data and DApp usage patterns. These approaches are being used to analyze transaction linkability, transaction mixing, crypto laundering, and smart contract use, impacting user privacy.

One direction of blockchain research [48] aims to provide zero-knowledge proofs, which reveal nothing about a transaction, except that it is valid, to increase privacy in blockchains. Through complex cryptographic methods, zero-knowledge proof proves something without having to reveal exactly what it is. One of the first examples was ZK-SNARK, in Zcash. Apart from zero-knowledge proofs, zero-knowledge methods have been used as a baseline to enable privacy preservation in blockchain, including secure multi-party computation, commitment schemes, ZSNARK, ZKSTARK, ring signatures, and homomorphic hiding. ZK-SNARKs require a trusted party or to set up the zero-knowledge proof system, initially. These trusted parties can violate the privacy of the entire system. ZK-STARKs improve upon this technology by removing the need for a trusted setup. Integration of ZK-STARK is being considered as one of the possible features in Ethereum 2.0.

### 3.1.2 Availability

Distributed ledger network attacks are usually the basis for further attacks that impact integrity. They target the governance or operation of a DL network, with the objective of taking control of most nodes and thus, the ledger (e.g., 51% attack). Network attacks might also try to partition the DL network into separate and inconsistent partitions or isolate a selected node from the remaining trusted nodes (Eclipse attack, Sybil).

This is then followed by presenting the node under attack with a deceptive state of the ledger, often by manipulating the node's time perception under attack (e.g., Timejacking, Delay attack).

Mining nodes and consensus mechanisms are vulnerable too. A mining node can be dishonest and selfishly withhold some of the already mined blocks (e.g., Selfish mining, Block withholding). In this manner, miners attempt to increase their share of the reward. Effective countermeasures include the application of block timers or increasing the randomness of the miner pool assignments.

## 3.2 Data management

Although blockchains are distributed databases, public blockchain networks cannot not directly meet the back-end database requirements in IoT systems. The transaction structure is optimized for blockchain operation. With distributed consensus, new entries are added to storage to ensure the distributed nature, immutability, and the absence of central authorities. However, it cannot meet the high throughput, low latency, rich permissioning, or query capabilities of traditional or distributed databases [47].

Some of the blockchain protocols facilitate the placement of additional data in a transaction. These can be parameters in a smart contract or arbitrary data, for example, a JSON input file in an Ethereum transaction. However, extensive data included in transactions would result in extensive chain data and costs for storing data in the chain.

IoT applications generate large volumes of traffic and are often latency-sensitive. Therefore, it is not surprising that most blockchain-based IoT data management approaches such as IPS, FairAccess, ENIGMA, or BigChainDB take a hybrid approach. These combine off-chain storage and blockchain capabilities with management functions assigned to the blockchain to ensure integrity and transparency, in applications that require audible records. Only smaller pieces of information are stored in the chain, such as hash values of off-chain data or access control information. Despite offloading large part of traffic from the blockchain networks, these approaches still need to provide lower latency and higher throughput record-keeping than public blockchain networks; so, private or consortium blockchains are used.

BigChainDB.59 for example, starts with a big data distributed database and then adds blockchain characteristics such as decentralized control via a federation of voting, immutability, and transfer of digital assets. Once stored, data cannot be changed or deleted. At the same time, it facilitates MongoDB query to search the contents of all transactions, assets, metadata, and blocks.

As shown in Fig. 3.2, BigChainDB can be seamlessly integrated into the traditional application as a blockchain database for decentralized timestamping, certificates, smart contracts, and transactions. At the same time, it can be part of a fully decentralized application, where processing and file storage are decentralized.

They took a hybrid approach in an IoT blockchain platform for sensing data integrity [49], where large files are stored in off-chain.

## 3.3 Authentication and authorization

As shown in Fig. 3.2, BigChainDB can be seamlessly integrated into the traditional application as a blockchain database for decentralized timestamping, certificates, smart contracts, and transactions. At the same time, it can be part of a fully decentralized application, where processing and file storage are decentralized.

They took a hybrid approach in an IoT blockchain platform for sensing data integrity [49], where large files are stored in off-chain.

| Application | Application |
|---|---|
| Platform | Platform |
| Processing logic | Decentralized Processing logic |
| File System Bigchain | Decentralized File System |

**Fig. 3.2:** Reference stack for

### 3.3.2

Authentication and authorization are two fundamental steps in any system. In the IoT, the registration is for the devices by the blockchain. It is particularly critical for the blockchain, to the users and services. Based on blockchain capabilities, it grants the immutable history of the device.

### 3.3.1 Identification and enrollment

For authentication and authorization, users, devices in any IoT system need unique. For devices, this can be in the form of hardware assigned by the manufacturer (e.g., Media Access-Control address for Ethernet or Bluetooth for mobile devices) or an identifier that

In the IoT, the enrollment phase for new devices can be rather challenging. It is to be reliable, secure, and yet minimize any human intervention. The backend for the enrollment may or not rely on blockchain technology. In IoT systems that are not based on hardware, the device owner usually executes the enrollment. If, for example, a blockchain address is used to identify a device, it is assigned manually. Often, details about wallet control in the device are not explained. This can lead to hardware security risks, similar to those related to PKI key management. It is, therefore, not surprising that many blockchain-based IoT systems predominantly focus on authentication and authorization of users and services.

An approach towards a simplified, and automated enrollment of IoT devices, where a device is granted a unique blockchain-based address for identification, could mimic, for example, Easy Connect approach. It simplifies device configuration using QR codes, tags, downloaded device information from the cloud, or a user-chosen configurator such as a smartphone. A result of a blockchain-based adaptation of this onboarding procedure would be a unique blockchain address registered in the backend system and assigned to the device for authorization.

For users and services, known identification principles can be adapted to leverage blockchain technology in the backend. Self-sovereign identity (SSI) is an emerging-approach for establishing digital identity on decentralized technologies. Unlike the centralized identity paradigm where some central trusted issuer provides identities, SSI users control the scope and use of their verifiable information. SSI is user-centric and privacy-aware, and reduces the unintended sharing of personal data. In an SSI system, entities are identified by decentralized identifiers (DID). The trust and management of DIDs are assured by blockchain technology, and DIDs can be decoupled from centralized registries. Although initial motivation for SSI was to increase the security and privacy of digital citizens, the same framework can be adapted for non-person subjects and, thus, for IoT [50] too. Anything can be a DID subject: a person, group, an organization, a material thing, a digital thing, a logical thing, which
