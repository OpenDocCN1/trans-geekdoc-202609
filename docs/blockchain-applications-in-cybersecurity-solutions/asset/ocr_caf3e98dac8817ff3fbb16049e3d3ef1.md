the data integrity. If a trusted hash of the data is provided, it is possible to compute the hash of the data and verify the two values. If they match, then the data has not been changed since the original hash is formed.

![](bbox=[0.385, 0.21, 0.62, 0.664])

**Fig. (2).** Block in a Blockchain.

The first block is called a genesis block and is created at the beginning with the set of records and its Merkle root.

Merkle trees are the basic blocks of blockchain technology. It is a structure that permits verification of the consistency of content in a secure and efficient way. Bitcoin and Ethereum use Merkle trees. A Merkle tree produces a fingerprint of the summary of all the transactions in a block. It enables a user to verify whether a transaction is part of a block. Repeated hashing of pairs of nodes is performed from the bottom up, until only one hash is left as depicted in Fig. (3). This hash is