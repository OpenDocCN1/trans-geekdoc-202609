# Figure 1.9 Hash

You can generate a hash online using the following link:
https://passwordsgenerator.net/sha256-hash-generator/

A hash has the following properties:

+   - Given an input has a precisely predictable output of a specified length, usually but not necessarily shorter than the input.
- Even if the input is only slightly changed, the output differs dramatically.
- If the hash function is of the cryptographic variety, it is exceedingly difficult, if not practically impossible, to infer the original input given only the output. The degree of difficulty/impossibility depends on the strength of the encryption used.

Every transaction occurring on the blockchain network is encoded to produce a hash that is impossible to decrypt. Hashes are used to represent the current state of the blockchain. It means all the transactions that have taken place so far have been hashed, and the resulting output hash represents the current state of the blockchain. The hash is used for all parties to agree that the state is the same.

The purpose of the hash is for validation. Data on the blockchain is “hashed” in each block. Each block is linked with the previous block via the hash value. If someone tampers with a block, everyone will know the block is corrupted. Therefore, it preserves the integrity and immutability of the blockchain.