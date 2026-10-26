
## 3.12 Payment Verification

In the Bitcoin network, simplified payment verification nodes will have a subset of the blockchain, i.e., only block headers. Simplified payment verification (SPV) nodes largely use Merkle trees. To check whether a transaction is added in a block, it uses a Merkle path or authentication path. This eliminates the need to download all the transactions. Consider, for example, an SPV [12] node that is willing to receive payments to an address in its wallet. A Bloom filter is mounted on its peer-related connections by an SPV node to restrict the transactions received to those with addresses of interest only. A merkleblock message will be used to submit the block if a peer recognizes a transaction that matches the Bloom filter. The merkleblock message contains a Merkle path that connects the transaction to the Merkle root of the block and a block header. The SPV node can use this Merkle path to connect the transaction to the block and can ensure that the transaction is included in the chain. An SPV node uses the block header to connect the block to the rest of the blockchain. The ties between block and transaction and the connection between block and blockchain indicate that the transaction is inserted in the blockchain.

## 3.13 Benefits and Challenges

### 3.13.1 Benefits

#### 3.13.1.1 Decentralization

There is no third-party intervention during transactions. Whatever cryptocurrency the user owns, it belongs only to the users. No central authority can own or handle it. Decentralized network provides protection against corruption and tampering.

### 3.13.2 Transparent and Anonymous

It is not easy to trace down a user’s address unless the user shares the wallet address. Even if the user publicizes, it is easy to generate another wallet address. Hence, the privacy of the user will be maintained. Simultaneously, as all blockchain transactions are registered in a public ledger, blockchain retains confidentiality without losing the transparent nature. While few research works have said that a transaction in blockchain can be traced back using clustering and flow analysis technologies, many research studies have suggested different schemes to boost anonymity property.

### 3.13.3 Less Transaction Fee and No Taxes

As blockchain transactions are decentralized and anonymous in nature, there is no practical way to apply any tax, and for instant transactions, there is no cost involved. Even if there is any cost involved, it is much less than a credit card, PayPal, or bank transfer [7].

### 3.13.4 Theft Resistance

It is not possible to steal Bitcoins from any user unless the rival knows the private key that is associated with the user’s wallet. However, if the user loses the private key associated with his/her wallet by any means, the bitcoins in the wallet are also lost forever and can never be recovered.

Though blockchain has numerous benefits for the betterment of the Internet, it does have to face some technical challenges as well.

### 3.13.5 Scalability

Scalability is a big challenge. The size of a Bitcoin block is limited to 1 MB, and mining a block takes 10 minutes. The Bitcoin network is incapable of dealing with high-frequency trading since it is limited to a rate of seven transactions per second. However, if the size of the block is increased, the storage space will also be increased and it will slow down the network speed. This results in centralization because fewer consumers want such large networks to be managed. The tradeoff between security and block size was therefore of major concern.

### 3.13.6 High Energy Consumption

The blockchain network uses the PoW model to achieve consensus. Although the PoW model protects the mining process from various security threats such as Sybil [8] attacks and double spending, it requires a great deal of energy and computing resources to calculate the required hash value for a block.

### 3.13.7 Selfish Mining

In blockchain, selfish mining strategy allows a miner to achieve larger revenue than the fair share. Miners may in the future hide their mined blocks for more revenue. This can lead to many divisions of blockchain and hinder the growth of blockchain.

### 3.13.8 Privacy Leakage

Privacy at a certain level can be achieved through public and private key pairs. Users transact through this key pair without knowing the real identity. Transactional privacy is not guaranteed by blockchain since the transactions and balances for each public key are available in public. In addition to this, the identity of the user can also be monitored through his/her transactions.

## Conclusion

Blockchain, in simple words, can be defined as a series of immutable, time-stamped data blocks managed by a set of computers not owned by any single entity. Data are encrypted in each of these blocks and clustered together using cryptographic principles. The blockchain network has no central authority – the very definition of a decentralized system. As it is a public and permanent ledger, the information contained in it is open for access by anyone and all. So, anything that is developed on the blockchain is transparent, and their actions are accountable to everyone concerned.

There is no central authority to issue or control the Bitcoins, but it is created by a process called *mining*. Mining is a process in which all legitimate transactions are stored in blocks and included in the register called “blockchain.” The added blocks are linked to the previous blocks so that reusing of Bitcoins can be prohibited. To add a block to the blockchain, a peer requires a nonce value that satisfies a particular equation using SHA-256 cryptographic hash function. Finding a nonce value is a computationally expensive task. So, a node who finds the suitable nonce value will be rewarded with an incentive. Nevertheless, this method of verifying a transaction might be confusing when each node attempts to relay its found block. Hence, to avoid such a situation, a consensus algorithm is made between all peers in the network to decide which blocks should be added, which peers should be allowed to include the block, and so on.

Consensus algorithms aim to safely update replicated distributed states and are the key piece of the puzzle in the operating principles of the blockchain. Consensus protocol assures that copies of the shared state are synchronized and accepted in blockchain at any given time. According to Refs. [1] and [2], the deterministic consensus in entirely asynchronous models of communication cannot recognize any faults. Therefore, partial synchronization assumptions are required with maximum transaction propagation latency thresholds. Cryptography and partial synchrony, digital currency and precursor designs are some of the previous works on consensus protocols. These were the building blocks of blockchain networks to create “decentralized” consensus algorithms.

Several consensus algorithms have been proposed till date, which will be discussed in later sections of this chapter.

In 2009, many variations of Bitcoin, such as Ethereum [3] and Nxtcoin [4], were introduced. A variant in which anyone can join and leave the network anytime is called “public blockchain.” Since the nodes can join and leave anytime, it is hard to predict the exact number of nodes; hence, applying the concept of consensus is difficult. In case the number of nodes is too high, exchanging the agreement and taking consensus of all nodes is even more difficult. On the other hand, to add a block in a blockchain, the nodes have to prove their quality compared with other nodes. Hence, a consensus algorithm named “proof-based consensus” was proposed.

Proof of work (PoW) [5] is the first version of a proof-based algorithm. In this consensus algorithm, a node can broadcast their blocks over the network using their computing resources. Later several other proof-based algorithms such as Proof-of-Stake (PoS), Proof-of-Elapsed Time, Proof-of-Space, and Proof-of-Luck were also proposed. Noticing blockchain’s ability, many major organizations such as JP Morgan and IBM have begun to explore the technology. This gave rise to many other platforms in blockchain like private blockchain, consortium blockchain, etc. Unlike public blockchain, private blockchain allows nodes only from a single organization to involve in the verification process. In consortium blockchain, the nodes can be from different consortiums, but only permitted nodes are allowed in the network. Consensuses on these platforms are based on the results of majority. Hence, they are otherwise called as “voting-based consensus algorithm.” Nodes following voting-based consensus algorithm can either be (i) crash fault tolerance or
