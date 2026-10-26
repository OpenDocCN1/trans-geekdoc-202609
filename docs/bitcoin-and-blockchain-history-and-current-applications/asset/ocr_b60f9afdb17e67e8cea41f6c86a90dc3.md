+   iii. Timestamp: current universal time in seconds as of 1 January 1970.
+   iv. nBits: target threshold of a valid hash block.
+   v. Nonce: A 4-byte field, usually starting at 0 and rising for each hash estimation.
+   vi. Parent block hash: a hash value of 256 bits that points to the previous block.

The block body is composed of a counter and transactions. The block size and the size of each transaction determine the total number of transactions a block can hold. The authentication of transactions is validated using an asymmetric cryptography method [3]. A fork will be created in the blockchain, if multiple nodes of the blockchain network produce valid blocks simultaneously. Under such a circumstance, the network chooses the longest chain as original and discards all the blocks in the other fork. A high-level view of blockchain is presented in Figure 3.3.

Blockchain is a P2P model where all peers are equally important. The transactions can be made between all nodes whenever they are generated. The nodes validate the transactions based on already-defined specifications. The transactions are forwarded only if they are valid. In this way, every node in the blockchain will have only valid transactions in its local copy. The validation of transaction authentication is based on digital signatures [4].

The layer above network layer is the consensus layer. In a decentralized environment and among non-trustworthy nodes, the process of achieving consensus is handled by the consensus layer. The consensus layer is comprised of different consensus algorithms. The four major consensus algorithms are Proof of Work, Proof of Stake, Delegated Proof of Stake (DPoS), and Practical Byzantine Fault Tolerance (PBFT). Apart from these algorithms, there are few less popular consensus algorithms such as Stellar, Proof of Bandwidth (PoB), Tendermint, Ripple, Proof of Authority (PoA), Proof of Burn, Proof of Elapsed Time (PoET), Proof of Space, Proof of Retrievability, Proof of Activity, Proof of Trust, BFT-SMART, Proof of Luck, and Scalable BFT.

The incentive layer takes care of the economic factors of the blockchain network. It encourages the nodes to provide their contribution for verifying the data by integrating the incentives allocation mechanism and incentive issuance process. Thus, the incentive layer acts as a motivating force of the blockchain network.

The programming part of the blockchain is handled by the contract layer. Smart contracts, various algorithms, and scripts are all dealt in this layer. A smart contract

![](bbox=[0.12, 0.78, 0.9, 0.9])

FIGURE 3.3 Blockchain structure.