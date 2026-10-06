# 7.1 Introduction

Blockchain is a technology that enables decentralized storage of data across multiple notes. Each note stores a copy of the data (also called a ledger) and hence it is also known as distributed ledger technology. Blockchain is immutable, i.e., once any data is stored on the blockchain, it cannot be altered or modified. Because of the intentionally introduced redundancy, it is not feasible to alter any data that is once stored on the blockchain. This makes the system highly secure and users can trust that the data is stored.

The process of producing new blocks in a blockchain is called “mining” and the hardware used for this task is termed “miner.” The process of mining is associated with solving a cryptographic puzzle that is resource intensive. It is possible to use special integrated circuits that are designed solely for the purpose of mining new blocks. Such circuits are used only for the purpose of producing new blocks and the design of an ASIC miner will be based on the specifications of the blockchain that it will be used in. ASIC miners consume low power and resource when compared with any other alternative for mining blocks in a blockchain.

# 7.2 Present Problem and Proposed Solution Overview

When a blockchain network is set, it is important to design how the process of producing new blocks will be carried out. If the network relies on a small number of validator nodes that are responsible for the process of block producing then it centralises the network to some extent. This makes the network highly vulnerable to 51% of attacks [1]. Also, if traditional single board computers are used for the mining process, they are vulnerable to a wide spectrum of security threats [2].

We recommend the use of popular PoW (proof of work) consensus mechanism popularized by Bitcoin because it doesn't rely on centralized nodes; rather, every node in the network can participate in the block-producing process. We also recommend the use of ASIC miners because besides being highly efficient, they are also less vulnerable to various security threats. Since ASICs are designed specifically to perform a particular task, the attack surface is significantly low and hence they can’t be hacked.

# 7.3 Understanding Blockchain

Blockchain is a way of storing data in a decentralized fashion so there is not one single point of failure in the entire network. The term “blockchain” is derived from two terms: “block” and “chain.” The data is stored in form of small blocks of fixed size and are linked with one another by their hashes. This forms a chain-like structure, hence the term “blockchain” is used (Figure 7.1).