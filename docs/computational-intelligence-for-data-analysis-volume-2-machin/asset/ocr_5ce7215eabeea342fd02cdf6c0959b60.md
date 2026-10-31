Stake (PoS), Proof of Importance (PoI), Byzantine Fault Tolerance (BFT), and Proof of Elapsed Time (PoET) [13].

In Blockchain, each block stores the hash value of its Block and the previous block hash. Any changes to any block generate a different hash result. The Blockchain network can easily track these manipulated blocks, and manipulated blocks get discarded. To change any block, one has to change the current block hash and all hash values of all forward blocks. An attacker could change the block value of any single node, but to reflect changes, the attacker has to change the Blockchain of more than 51% of nodes, which is almost impossible to do without being caught. As Blockchain is distributed, each node maintains a separate copy of Blockchain. It is also tough to do so because it requires a massive amount of computing resources, and the cost of doing so would be huge.

# How Does Blockchain Address Privacy Issues?

The Blockchain supports anonymity and eliminates the need for a trusted third party, but anonymous transactions could be troublesome if this technology is used for wrongdoing. This is the biggest concern of various law enforcement authorities, but there are ways to address it without compromising anonymity using Blockchain technology. Without revealing the private key, a wallet application only exposes the wallet address, not the private key or any personal identity of the wallet holder, to protect the privacy of wallet owners. The wallet application providers can facilitate the Know Your Customer (KYC) process and issue digital identities in the form of wallet addresses without compromising owners' privacy. The digital identity can only be revealed to law enforcement agencies when needed to avoid misuse of Blockchain Technology.

# Preventing PHR, EMR Manipulation, and Sharing Records Securely using Blockchain

In Blockchain-based PHR/EMR systems transaction process, reliability and security are maintained at the following level:

+   1. Submission of transaction or origination of data-source from trusted and authentic uses. A private key is issued to the user to sign messages digitally. Nodes verify the digital signature of the messages against the public key to ensure a trusted party initiates the transaction.
+   
+   2. Inter-Node communication is done through remote procedure calls in peer-to-peer distributed Blockchain networks. The communication channel is protected using a secure socket layer to ensure end-to-end encryption.