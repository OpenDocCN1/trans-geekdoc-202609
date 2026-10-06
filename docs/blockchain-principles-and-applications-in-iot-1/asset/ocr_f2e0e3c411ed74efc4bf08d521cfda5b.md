# Techniques Supporting Privacy and Security

# 203

| Block | | |
|---|---|---||
| Hash of Previous Block Header | Nonce | |
| ... | ... | ... |

| | | |
|---|---|---||
| Add | Hash of Previous Block Header | Nonce |
| ... | ... | ... |

| Proof of Elapsed Time | |
|---|---|
| Validate | Miner with Shortest Wait Time |
| Wait | Miners |

FIGURE 11.12
Proof of elapsed time.

# 11.5.7 Proof of Activity

Proof of activity is a hybrid method that incorporates both WoW and PoS. Cryptographic puzzles were solved by miner in the way they did in Pow before switching to PoS. Blocks, rather than transactions, contain templates that include header information as well as the address of the reward for mining. In this technique, the blocks are established by limiting the time it takes to create a block to the shortest amount of time possible for allowing maximum number of blocks to be added to the chain. As a result, the network is protected from spam transactions, avoiding floods. This approach makes it impossible for the Bitcoin network to be hacked. It also prevents the likelihood of a 51% attack, like in PoS [60].

# 11.5.8 Proof of Space

Proof of space is a consensus technique that works in a similar way to PoW. This method validates transactions using disk storage instead of computing resources and rewards miners who have the largest disk space allocated to a block. For anti-spam and denial-of-service attack protection, proofs of space might be employed instead of Pow. Proof of space has also been used to identify malware [64]. Proof of space is described in detail in the reference [65].

# 11.5.9 Proof of Importance (Pol)

Pol is a consensus blockchain used to decide which nodes are qualified to add a block to the blockchain and it was first developed by the New Economy Movement (NEM). Pol, which is based on PoS, rewards users who actively transact on the network. Pol requires nodes to invest a certain amount of currency in order to be eligible to generate blocks, and nodes are chosen to create blocks based on a score that quantifies their contribution to the network. Nodes with a higher significance score have a better chance of getting picked to create a block [60,66].