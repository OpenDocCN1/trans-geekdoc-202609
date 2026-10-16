
## Chapter 1: Introduction to Blockchain Technology

N. Devi¹*, P.L. Rani¹ and A.R.G. Gokul¹

Department of Information Technology, Sri Venkateswara College of Engineering, Sriperumbudur, India

### Abstract

A blockchain is a linked set of records maintained in a decentralized environment. The records in blockchain are publicly available but cryptographically secured. The interesting property exhibited by blockchain is that once some information is recorded, it is infeasible to modify the information. Blockchain is generated as a chain of blocks that contains time-stamped digital documents so that it is infeasible to back date them or tamper the documents. These time-stamped digital documents are stored as a collection of records and grouped as a set of blocks, chronologically linked in order of time.

A new block is created and appended to the existing blockchain, whenever there is a need for updating the blockchain. Every block in the blockchain comprises of a hash of the preceding block, collections of records of its own, and the hashed value records known as Merkle tree. The information inside the blocks varies depending on the nature of blockchain. For example, when the nature of blockchain is bitcoin, they are supposed to store the details about a transaction viz., sender, receiver and amount of coins whereas blockchain used for medical records stores the complete health history of a patient over time. Since blockchain is stored in a distributed way, efficient hashing techniques are used to ensure the integrity and robustness of blockchain. This chapter describes the nuances of blockchain technology along with the protocol stack and the most common consensus mechanisms. Furthermore, recent advances, challenges and future trends of blockchain are discussed.

### Keywords

- Bitcoin
- Blockchain
- Cryptography
- Distributed
- Decentralized
- Hash
- Merkle Tree
- Robustness
- Time Stamp
- Transaction

### Introduction

A blockchain [1] is a decentralized distributed ledger of records that is cryptographically secured and accessible unlimitedly to all. It possesses a fascinating characteristic: when an information is stored inside a blockchain, it is infeasible to modify the recorded information. The blockchain is generated as a chain of blocks that contains time-stamped digital documents. These time-stamped digital documents are stored as a collection of records and grouped as a set of blocks. These blocks are then linked together in chronological order of time in a continuous line. To update, a new block is created and appended to the existing blockchain, thus, providing blockchain, a non-destructive way to track data changes over time. Every block in the blockchain comprises a hash of the preceding block, collections of records of its own, and the hashed value records known as Merkle tree. The information stored inside the blockchain depends on the type of blockchain. For example, the blockchain used in bitcoin records the information of a transaction viz., number of coins, contributor and receiver whereas the blockchain used for medical records stores the complete health history of a patient over time. Since blockchain is stored in a distributed way, efficient hashing techniques are used to ensure the integrity and robustness of the blockchain. The main characteristics of blockchain are depicted in Fig. (1). This section describes the nuances of blockchain technology.

![](img/1b14bb2748aa86be47fb2952ff28da51_17_0.png)

Fig. (1). Different Aspects of Blockchain.

### Block

A block in a blockchain is a collection of various items such as the hash of its preceding block, the Merkle root and its own records as shown in Fig. (2). A Merkle tree for a block is formed by placing the hash of the individual records of that block as the leaf nodes and the non-leaf nodes are the combined hash of their own children. Using hash ensures data integrity and also helps in ensuring the correctness of the data at any given time. A hash function accepts an input of any length and converts it into a fixed length. The hash function may produce a 32-bit or 64-bit or 128-bit or 256-bit fixed length called a hash. Hash functions protects the data integrity. If a trusted hash of the data is provided, it is possible to compute the hash of the data and verify the two values. If they match, then the data has not been changed since the original hash is formed.

![](img/1b14bb2748aa86be47fb2952ff28da51_18_0.png)

**Fig. (2).** Block in a Blockchain.

The first block is called a genesis block and is created at the beginning with the set of records and its Merkle root.

Merkle trees are the basic blocks of blockchain technology. It is a structure that permits verification of the consistency of content in a secure and efficient way. Bitcoin and Ethereum use Merkle trees. A Merkle tree produces a fingerprint of the summary of all the transactions in a block. It enables a user to verify whether a transaction is part of a block. Repeated hashing of pairs of nodes is performed from the bottom up, until only one hash is left as depicted in Fig. (3). This hash is

- Web/Mobile Application
- Support System
- Open Source API
- Commercial API
- Decentralized Protocols
- Social
- Asset Mapping
- Verify Certi
- Communication
- Shared Protocol Layer
  - Overlay Networks
  - Smart Contract
  - Storage
  - Side Chains
- Shared Data Layer
  - Blockchain(s)

Fig. (5). Blockchain Protocol Stack.

### Tamper Resistant

The blockchain protocol running on the nodes of a P2P network performs the validation process of a transaction as depicted in Fig. (6) without involving third-party agents [6]. The validation process is done by majority vote consensus. This protocol is responsible for administering all the nodes to participate in validating the transaction through a set of pre-defined governance rules.

![](img/1b14bb2748aa86be47fb2952ff28da51_23_0.png)

The pre-defined governance rules of the network oversee how the nodes in the P2P network cooperate with one another to validate the transaction. These rules elucidate:

- The criteria based on which the transaction is said to be valid.
- The cost incurred during the transaction.
- Validating the transaction using game theory and cryptographic techniques.
- Procedures to update the predefined rules as and when necessary.

Consider a bitcoin scenario; the financial transactions are validated through a majority vote with the help of bitcoin protocols instead of validating manually through ledgers stored in servers in a traditional banking application.

### Consensus Protocol

A consensus mechanism in a blockchain is a robust mechanism to achieve common agreement on a specific state among the nodes in a P2P network. This mechanism involves a set of predefined rules for synchronizing the nodes during transactions that are trusted and recorded in the blockchain. The purpose of these rules is to assure the validity and legitimacy of the transactions. Some of the widely used consensus mechanisms [7] viz., PoW, PoS, DPoS, pBFT, PoC, PoA, PoR, PoI, PoB, PoET, PoId and PoAu are described in this section.

## Blockchain Applications in Cybersecurity Solutions

### Proof of Stake (PoS)

PoS employs a randomized procedure to find out who has the likelihood to produce the subsequent block [9]. Blockchain users can hold their tokens for a certain duration to become a validator. The nodes are not only involved in validating process as a validator, but sometimes generate a new block and become a contributor. The nodes that act as validators are changed from time to time depending on their active involvement in rendering the blockchain. The probability at which the nodes generate new blocks depends on the number of coins or stakes they possess. The validator node involved in the validating process of a transaction gets a reward amount depending on their level of involvement in forming the block. On the other hand, due to inflation, validators may get a particular amount of coins. These rewards allow retaining the validators in the blockchain network. PoS is more efficient in conserving energy compared to any other consensus mechanisms.

### Delegated Proof of Stake (DPoS)

DPoS allows the users to gamble with their stakes to cast votes to different representatives in a transaction [10]. Each user’s vote has a different weightage in the transaction depending on how much stake they have used for casting the vote to a delegate. The vote of user ‘X’ had more weightage than the vote of user ‘Y’, when user ‘X’ used his 100 stakes for casting the vote whereas user ‘Y’ uses only 25. The representatives who secured more votes are given the right to generate a new block. The representatives receive a reward of a certain amount of stakes as transaction fee as in other consensus mechanisms. DPoS is faster and deals with more number of transactions. This mechanism is considered to provide digital democracy as it follows a voting system based on stake-weighted votes.

### Practical Byzantine Fault Tolerance (pBFT)

In P2P networks, undisputed concurrences among trustworthy and non-faulty nodes help in accomplishing consensus. The basis of BFT is observable in a situation where all nodes reiterate an incoming message [11]. If a node keeps repeating the incoming message, then it evidently signifies that it does not have any fault. Alternatively, if the receivers replicate the incoming message, the network could effortlessly rule out the prospect of Byzantine nodes. Byzantine node denotes the traitor nodes which lie or mislead other nodes in the network deliberately. The byzantine node could also lie to the nodes that are concerned with the consensus protocol. An absolutely functional blockchain network would make sure that Byzantine Fault Tolerance in blockchain assists it in dealing with
