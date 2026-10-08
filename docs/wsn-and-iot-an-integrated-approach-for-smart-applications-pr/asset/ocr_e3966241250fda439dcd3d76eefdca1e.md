# Blockchain-Based Communication Frameworks for Smart Vehicles

| Block 1 Header | Block 2 Header | Block 3 Header |
| --- | --- | --- |
| Hash of Block 0 Header | Hash of Block 1 Header | Hash of Block 2 Header |
| Hash of Block 1 Transactions | Hash of Block 2 Transactions | Hash of Block 3 Transactions |
| Block 1 Transactions | Block 2 Transactions | Block 3 Transactions |
| txn 735... | txn x6h... | txn 099... |
| txn b76... | txn 9kz... | txn p3... |
| txn 3c2... | txn 232... | txn 47w... |
| ... | ... | ... |
| Block 1 | Block 2 | Block 3 |

**Figure 5.10** Blocks, headers, and transactions in a blockchain.

metadata. Once validated and included in a block, transactions become part of the permanent record on the blockchain.
**Consensus mechanisms:** These are protocols or algorithms that allow agree-ment among network participants to validate network and order of transactions being added to the blockchain. Consensus is necessary in decentralized systems to ensure that all participants reach a common understanding of the state of the blockchain, as shown in Figure 5.1H. Different consensus mechanisms have different approaches to achieving agreement. Some popular consensus algorithms include:

+   * **Proof of work (PoW):** In WoW, participants (miners) compete to solve complex mathematical puzzles to validate transactions and add blocks to the blockchain. The solution requires significant power, and the miner who finds the first solution is rewarded. This mechanism is used by cryptocurrencies like Bitcoin.

+   * **Proof of stake (PoS):** PoS selects block validators by the number of coins they hold or have as collateral. Validators are chosen to create new blocks based on their stake, and the probability of selection is proportional to their stake. PoS consumes less energy than PoW and is used by cryptocurrencies like Ethereum.

+   * **Practical Byzantine fault tolerance (PBFT):** PBFT is a consensus mechanism used in permitted blockchains. It requires a predetermined set of trusted validators, and consensus is achieved through multiple rounds of voting. PBFT ensures Byzantine fault tolerance, where a certain number of faulty or malicious nodes cannot disrupt the consensus process.

+   * **Delegated proof of stake (DPoS):** DPoS is a variant of PoS where a smaller number of participants, known as “delegates,” are elected to validate transactions and produce blocks. Delegates take turns producing blocks in a deterministic order. DPoS is used by cryptocurrencies like EOS [10].