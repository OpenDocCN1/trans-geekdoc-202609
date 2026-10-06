# Block Header

| Hash of Previous Block Header | Block Version |

| Nonce | Time stamp |

| Merkle Root Hash |

Block Body

| Transaction Counter |

| Hash(es) |

| Transaction(s) |

FIGURE 11.1
The structure of a block.

| Block (1) 
 Hash of Block (0) Header |

| Block (2) 
 Hash of Block (1) Header |

| Block (3) 
 Hash of Block (2) Header |

FIGURE 11.2
A sample of blockchain.

+   - **Consensus Layer** – Because a blockchain is a decentralized network, there is no trusted third party to verify a node’s authenticity. To solve this, a consensus method is utilized for decentralized nodes. The consensus layer ensures network nodes consensus and transaction records consistency among the network nodes by using a variety of consensus protocols such as “proof-of-work (PoW), proof-of-stake (PoS), proof-of-authority (PoA),” etc. [8–10].
- **Incentive Layer** When When miner completes the verification process and adds a block to a chain, he or she will be rewarded for their efforts. Miners will be