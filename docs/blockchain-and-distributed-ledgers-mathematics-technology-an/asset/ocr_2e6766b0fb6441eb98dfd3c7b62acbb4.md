# Blockchain and Distributed Ledgers: Mathematics, Technology, Economics

These examples clearly show that “small” changes in the input make the output unrecognizable, as intended.

# 4.11 Merkle trees and hash pointers

# 4.11.1 Merkle trees

The idea of a hash, combined with padding for efficiency, is beneficial for making data simultaneously immutable and compressed. Suppose we have a set of $N$ data blocks. We can pad them to make the total number of blocks a multiple of 2, say $2^n$. Then we can hash them sequentially until we reach the root node; see Merkle (1987). These constructs are called Merkle trees and are very useful in cryptography in general and blockchains in particular. In the next chapter, we show how Bitcoin and Ethereum protocols (as examples) use Merkle trees.

A typicalkle tree is shown in Figure 4.21 (a). By construction, Merkle trees are tamper-proof, in a sense that any leaf along the path to the root will change the root itself beyond recognition. This property is helpful if, for example, we wish to verify that a particular data point, say a transaction, belongs to a particular Merkle tree. Using Merkle trees, we can verify membership of a transaction in a set in $O(\ln(N))$ steps. This is illustrated in Figure 4.21 (b).

In Table 4.6, we use hashes of the first seven transactions from the Bitcoin Block 600,000 and build a balanced tree, instead of a padded tree to speed up the process. In other words, to get to the root of the tree, we combine transactions as follows: $(0,1),(2,3),(4,5);(012),(345);(6);(0123456)$. In the second column, we show the actual root. In the third column, we show a hypothetical root, with slightly modified inputs — for transaction 0, the very last hexadecimal number 3 is replaced with 0. The table shows that the resulting root is completely different from the correct one, which allows us to find instances of tampered inputs.

# 4.11.2 Hash pointers and chain signatures

Hash pointers are beneficial for chaining blocks of data together and making them immutable. Not only do they link the past and the present, but they also make changing the past impossible, see Figure 4.22.

Given the nature of good hash functions, any change in previous blocks will completely change the old hash to a new one, thus destroying all calculations (such as puzzle-solving) based on the old hash. Figure 4.22 (a) illustrates this graphically. Naturally, we can combine hashing and signing to create immutable and unbreakable chains of events. By signing a block of data and hashing the pair $(m, sign(h(m)))$ we create a hash pointer. In turn, this pointer becomes an integral part of the next block. Thus, we create a blockchain