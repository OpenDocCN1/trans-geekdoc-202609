
## 1.2.1 BLOCKCHAIN CONSENSUS MECHANISM

The PoW mechanism is based on solving a computationally intensive puzzle that requires carrying out resource-intensive computations. A user who can solve this puzzle first can publish the new block in the blockchain network. The checking of the correctness of the solution is done by all other miners to verify any new blocks before adding them to the blockchain and reject any block that does not satisfy the solution. In the PoW mechanism, it is hard to carry out a denial-of-service attack by flooding the blockchain network with malicious blocks. In theory, PoW enables a non-monopoly environment for all participants to contribute; however, this creates a difference in computational power and cost of electrical power, which creates an unfair situation among the users. The PoW implementation domain is a public cryptocurrency, such as BTC and Ethereum.

The PoS consensus mechanism is based on investors in a network. The likelihood that a PoS user will publish a new block in the network is based on the percentage of their stake in the total staked cryptocurrency in the blockchain network. When they invest in a stake, which is usually an amount of cryptocurrency, the possibility that they will destroy the network diminishes, and they will be more likely to help the system succeed. When the cryptocurrency is staked, the user will not be able to spend it. A user's stake is used by PoS blockchain networks to determine who can publish new blocks. The PoS mechanism has several advantages, one of which is, compared with PoW, it is computationally intensive. The PoS mechanism allows any interested user to stake on cryptocurrency; besides, the system is controlled by stakeholders, although this is sometimes a disadvantage if they form a pool to create a centralized base power. In contrast, the PoW mechanism is known for its unique issues, as the 'no nothing at stake' problem. This problem arises when, at some point, due to a temporary ledger conflict, multiple blockchains that are competing against one another appear. The appearance of these blockchains will cause different results from different blockchain versions to be published at almost the same time. In this case, the staked users can perform on every chain to increase their reward earning without joining a single branch. In addition, the PoS mechanism is vulnerable to a 51% attack by having sufficient financial power. The PoS implementation domain is public, such as Casper and Krypton.

The round-robin mechanism allows each user to take his or her turn to create the next block, which includes a time limit for each user to avoid the publication of blocks. This mechanism is used by some private and federated blockchain networks. This mechanism prevents users from making the blocks plurality, which is easy to understand and does not require high computational power, due to a lack of cryptographic puzzles. On the other hand, this mechanism requires a considerable amount of trust between users; therefore, it is useless in the public blockchain domain, which dominates the majority of current blockchain implementations. The great need for trust in this mechanism is because a malicious user might increase the number of users contributing to the network to raise the likelihood of publishing malicious new blocks to ruin the network. The round-robin implementation domain is a private and federated blockchain, such as MultiChain.

# A Taxonomy of Blockchain Threats and Vulnerabilities

The PoA mechanism is based on publishing users' partial trust, which relies on their real identities, which must be verified, proved, and included on the blockchain network. The central idea behind this mechanism is that publishing user's reputation or identity is being staked to publish new blocks. A publishing user's reputation is affected by other users in the network based on his or her behavior. If the blockchain user disagrees with the actions of a publishing user, who must adhere to the agreed manner on the network, will lose reputation, minimizing the user's chance of publishing a block. The confirmation time in this mechanism is fast, and the block production rates are dynamic. More, this mechanism can be used in hybrid systems, which draw on another consensus mechanism. In contrast, this mechanism assumes that the validating user is not compromised. In addition, the user's reputation is subject to possible high-risk exposure that can compromise the user at any time. This mechanism also leads to a single point of failure. The implementation domain of the PoA or PoI mechanism is a private and federated blockchain and includes hybrid systems such as Ethereum, Kovan Testnet, and POA Chain.

In the PoET mechanism, each publishing user requests a wait time within the hardware source, which is secured and installed in the user's system. The hardware produces a random wait time for the publishing user, and the user becomes inactive during the period of the wait. When publishing user is reactivated, the user publishes a block on the network, and all the users who are in the inactive state will stop waiting, and the whole process will begin again. In this mechanism, the wait time must be random; otherwise, the malicious user will dominate the system by keeping the wait time at a minimum amount. Besides, the publishing user in this mechanism must not start early by waiting for the actual given time. These challenges are resolved by executing an application in a trusted processing environment, such as Intel's Software Guard Extensions, which cannot be modified by external applications. This mechanism is computationally less expensive than PoW. However, the disadvantages of this mechanism are that it relies on hardware to produce random time and that it assumes the hardware is not compromised. The implementation domain of the PoET mechanism is a private and federated blockchain, such as Hyperledger Sawtooth.

## 1.2.2 BLOCKCHAIN BLOCK

A block consists of a header and a list of transactions and events ledger. Figure 1.2 shows the structure of a block in a blockchain. It is explained in the following:

### 1.2.2.1 Block Header

The block header consists of three different sets of metadata.

### 1.2.2.1.1 Version and Previous Block Hash

The version field (4 bytes) is for the tracking of software updates. The previous block hash field (32 bytes) is a reference to the hash of the previous block. The cryptographic hash algorithm is by applying SHA256 twice each time. In a blockchain, every block is linked from the previous block. The previous block's hash is used to create the new block's hash. The first block in the blockchain is known as the genesis block.

# Blockchain for Cybersecurity and Privacy

![](img/816c34830872ca25a809f80557c6d27_32_0.png)

Figure 1.2 Blockchain chaining process.

### 1.2.1.2 The Mining Competition Scheme

This set of metadata contains the timestamp (4 bytes), the nonce (4 bytes), and the difficulty target (4 bytes). The timestamp is the creation of the block. The nonce ('number used once') is a number added to a hashed block, when rehashed, meets the difficulty target restrictions. The nonce is the first number a blockchain miner needs to discover before solving for a block in the blockchain.

### 1.2.1.3 The Merkle Root Tree (32 Bytes)

This is the hash of the root of the Merkle tree, which contains a data structure of the transactions in the block. The Merkle tree is created by repeatedly hashing pairs of transaction nodes until only one hash is left. The process is performed from the bottom up, from hashes of individual transactions.

### 1.2.2.2 Block Data

A Merkle tree is a digital fingerprint of the entire set of transactions in a block, enabling a user to verify whether or not a transaction is included in a block. It helps to verify that later versions of the event log include all previous versions and that all data is recorded and presented in the chronological order. Block data contains a ledger of events and transactions included inside the block as well as other data for all authentic and validated transactions that have been published on the blockchain network.

### 1.2.2.3 Chaining of Blocks

The miners perform the adding of a new block. A block in the chain may come from any miner who gets the right to add the new block. The miner picks up the hash of the
