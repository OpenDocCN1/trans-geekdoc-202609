how transaction flow happens in the Blockchain network. A detailed description is defined in Figure 3.14.

![](bbox=[0.175, 0.178, 0.825, 0.246])

FIGURE 3.13 Time frame ΔT.

![](bbox=[0.175, 0.297, 0.825, 0.503])

FIGURE 3.14 Transaction flow.

All the transactions in the blockchain are part of the Mempool. A Mempool can be compared to the local storage area of the miner responsible for holding unvalidated and unconfirmed transactions (Tans) from where the miner picks them. A core responsibility of the miner is to validate a transaction and create a block. Miner is a type of node responsible for creating blocks out of transactions. Miner validates them and, in turn, will receive some reward. Miner puts it in its block, which is known as a candidate block. It is not an fundamental block updated in the central ledger. All the candidate blocks will be competing with each other. And at the end, the block that wins the race will be updated in the final central ledger.

In reality, thousands and thousands of miners are there. In Figure 3.14, let us assume Miner 2 finds the solution to the Puzzle. Each and every time, the Consensus Algorithm launches the Puzzle. That particular Puzzle has