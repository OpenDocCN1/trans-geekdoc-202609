![](bbox=[0.183, 0.093, 0.816, 0.375])

4.21 (a) Merkle tree is used to compress the information about multiple transaction into a single Merkle root; (b) Merkle tree can be used to obtain proof of inclusion allowing the user to verify that their account is included and their deposit is correct. For privacy, account information itself is hashed. The leaf node represents an account. If need occurs, it is revealed and all the nodes on the path from the leaf to the Merkle root are traced. Own graphics.

![](bbox=[0.446, 0.396, 0.804, 0.653])

# ### 4.11.3 Chain signatures combined with Merkle trees

Above, we have shown how to create blockchains by combining hash pointers and signatures. When blocks are non-uniform, we can add Merkle trees into the framework and consider the root of a large block to be signed and chained. This method creates non-alterable records containing numerous transactions; see Figure 4.23.