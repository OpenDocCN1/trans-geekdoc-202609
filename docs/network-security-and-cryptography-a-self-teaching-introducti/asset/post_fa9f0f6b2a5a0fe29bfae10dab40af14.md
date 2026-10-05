
530 • NETWORK SECURITY AND CRYPTOGRAPHY

## 14.9 SECURITY OF BLOCKCHAIN

- Blockchain (BC) technology is a type of distributed digital ledger that uses encryption to make entries permanent and tamper-proof and can be programmed to record financial transactions. It is used for secure transfer of money, assets, and information via a computer network without requiring a third-party intermediary. Blockchain promises to solve this problem.

- Blockchain, also known as "distributed ledger technology" is a peer-to-peer network that sits on top of the Internet. Bitcoin is the first application of Blockchain technology.

- Bitcoin is an electronic payment system that purports to be the world's first cryptocurrency. It has become the most talked about cryptocurrency. The software is completely open source so any developer can download it, modify it, and create his own version of the software.

- The Blockchain could bring everything that is good about Bitcoin and translate it into decentralized applications. Blockchain refers to new applications of a distributed database technology that builds on a tamper-proof records of time-stamped transactions. By decentralizing it, Blockchain makes data transparent to everyone involved and eliminates the risks that can come with data being held centrally. A Blockchain facilitates secure online transactions.

- Blockchain refers to the way Blockchain stores transaction data in "blocks" that are linked together to form a "chain." The chain grows as the number of transactions increases. A block is created whenever a transaction is made. A block is the "current" part of Blockchain, which records some or all of the recent transactions. The block is broadcasted to all nodes for validation. Once completed, a block goes into the Blockchain as a permanent database. Each time a block gets completed, a new one is generated. Each data item in a BC has a timestamp. A BC is an ordered chain of blocks. All data of transactions are traceable based on the chain structure of BC. The Blockchain was designed so these transactions are immutable, i.e. they cannot be deleted. Thus, Blockchains are secure and tamper-free by design. Data can be distributed, but not copied. When it comes to digital assets and transactions, you can put almost anything on a Blockchain. Different scenarios call for different Blockchains.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_555_0.png)

FIGURE 14.15 Blockchain concept

### 14.9.1 Features of Blockchain Technology

Peer-to-Peer (P2P) network: The first requirement of BC is a network, an infrastructure shared by multiple parties. This can be a LAN at a small scale or the Internet at a large scale. Communication occurs directly between peers instead of through a central node. All nodes participating in a BC are connected in a decentralized P2P network. Transactions are broadcast to the P2P network. Due to some limitations of P2P networks, some vendors have provided cloud-based BCs.

Cascaded encryption: A BC uses encryption to protect transaction data. Blocks are encrypted in a cascaded manner, i.e. the encryption result of the previous block is used in encrypting the current block. The BC is secured by public key cryptography, with each peer generating its own public-private key pairs.

Distributed Database: A BC is digitally distributed across a number of computers. Each party on a BC has access to the entire database and no single party controls the data or the information. Since BC is decentralized, there is no need for central authorities such as banks.

Transparency with pseudonymity: Each node or participant on a blockchain has a unique 30-plus-character alphanumeric address that identifies it. Users can choose to remain anonymous or provide proof of their identity to others.

Irreversibility of records: Once a transaction is entered in the data-base and the accounts are updated, the records cannot be altered. Records on the database is permanent, chronologically ordered, and available to all others on the network.

- There are two types of Blockchains: public and private.

- Public Blockchains are cryptocurrencies such as Bitcoin, enabling peer-to-peer transactions.

- Private Blockchains use Blockchain-based platforms such as Ethereum or Blockchain-as-a-service (BaaS) platforms running on private cloud infrastructure. They limit access to the predefined list of known individuals. A private BC is an intranet, while a public BC is the Internet. Companies will be disrupted by the public Blockchains.

- BCs may be permitted or permissionless.

- In Permissioned BC, each participant has a unique identity.

- Permissionless BCs allow anyone to join, participate or leave the protocol execution without seeking permission from a centralized or distributed authority.

### 14.9.2 Benefits and Challenges of Blockchain

- BC is a great solution to the age-old human problem of trust. It enables trustless networks by allowing parties to conduct transactions even though they do not trust each other. The absence of a trusted middle results in faster reconciliation between parties. BC removes the intermediary and moves towards democratization and decentralization.

- By allowing digital information to be distributed but not copied, BC technology has created the backbone of a new form of Internet. There is no single point of failure from which digital assets can be hacked or corrupted.

- The decentralized nature of BCs makes them an equality technology that can be used to expand freedom, virtualization, and realization of all entities, both human and machine. The potential benefits of BC extend into business, political, humanitarian, social, technological, and scientific realms. These benefits make some to believe that BC has the fifth disruptive computing paradigm after mainframes, PCs, the Internet, and mobile/social networking.

- A major challenge of BC is security. Companies need to have security standards and systems to protect them from attackers or bad actors.

- Managing the Blockchains requires substantial computational power in order to maintain security.

- Regulating andizing digital currency and money transmission is difficult. There are legal challenges surrounding Blockchain. Blockchain will disrupt all kinds of legal work, notary publics, contracts, lawyers, and judges.

- Other real challenges include complexity, politics, regulatory approval, security of online transactions, and consumer privacy.

- The ever-growing size of the Blockchain is considered by some to be a problem, creating issues of storage and complexity.

### 14.9.3 Advantages of Blockchain for Security

- Tamper-proofing: The advantage of tamper-proofing is achieved by the unique date structure and writing mechanism of blockchain. Once a record, which is known as a transaction, is being created in the chained data structure of blockchain, a new timestamp will be recorded at the same time, as in Figure 14.16. Also, any modification of data created before that timestamp will not be allowed any more.

534 • NETWORK SECURITY AND CRYPTOGRAPHY

![](img/d3b56042c756fbcc011ff06f1b9f53f0_558_0.png)

FIGURE 14.16. Tamper-proofing mechanism of blockchain

- Disaster Recovery: Blockchain performs data recording and storing synchronously at all users' side by constructing open source sharing protocols. Unlike the traditional centralized database which stores data in one or several centers. In an application built on blockchain, every user has the right to generate data and keep a full copy of data.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_558_1.png)

FIGURE 14.17. Decentralized and distributed storage of blockchain

- Privacy Protection: Blockchain adopts asymmetric encryption mechanism to enable users to encrypt data with their own private key. In addition, the hash value of a user's public key is calculated and perform as the ID indicator of the user. On one hand, the hash value has no relation
