These hashes are not stored in a sequential order on the block, rather in the form of a tree-like structure such that each hash is linked to its parent following a parent-child tree-like relation. The hashing will go on until it produces a singular hash, the Merkle root. This Merkle root is the hash of the block and it is stored on the header of the block. The process is illustrated in Figure 1.11.

![](bbox=[0.135, 0.363, 0.833, 0.626])

Figure 1.11

The Merkle Tree structure will enable the quick verification of blockchain data and quick movement of large amounts of data from one computer node to the other on the peer-to-peer blockchain network.