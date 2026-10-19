Once the transaction takes place, it is communicated across all the nodes of Bitcoin, which has to be verified first and then registered. The validity of each transaction is a must before it is added to the public ledger. To record a transaction, a node must verify two things:

+   - The cryptocurrency is actually owned by the spender. This is done by verifying the digital signature.
+   - The spender is equipped with sufficient cryptocurrency to carry out the transaction. This could be done by checking every transaction recorded in the spender’s account.

The illustration in Figure 6.4 exhibits the working mechanism of blockchain technology.

![](bbox=[0.15, 0.3, 0.88, 0.6])

Figure 6.4 Cryptocurrency transaction using blockchain technology.

Blockchain technology was the result of developing a mechanism for Bitcoin transactions that the entire network would agree to. Initially, before blockchain technology was developed, and only bitcoins prevailed, transactions did not always come in order; thus, there was a need to eliminate double spending of the cryptocurrency. The transactions are passed from node to node in a bitcoin network; hence, the order in which the transactions are received at a node, might not be the actual order of the transactions taking place. For example, Transaction A might occur before Transaction B, but the number of nodes Transaction A has to pass could be more than that of Transaction B, thus leading to Transaction B being recorded in a node first. This was a challenge in a distributed network and Bitcoin solved this problem using blockchain technology. The transactions were then placed in blocks, thus leading to blockchains. This means that all the transactions taking place in a block have occured at the same time. The blocks are then arranged linearly in a chronological manner, in such a way that a given block is linked to the previous block by its hash value.