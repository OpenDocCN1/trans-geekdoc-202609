
53. Swan, M. Blockchain thinking: The brain as a decentralized autonomous corporation. *IEEE Technol. Soc. Mag.* 34(4), 41–52. doi: 10.1109/MTS.2015.2449358, 2015.
54. Sy Lim, P., Liu, F., Marcelo, A. and Fontelo, P. Blockchain technology for detecting falsified and substandard drugs in distribution: Pharmaceutical supply chain intervention. *JMIR Res. Protoc.* 7(9), e10163. doi: 10.2196/10163, 2018.
55. Taylor, P. Applying Blockchain Technology to Medicine Traceability. Available at: https://www.securingindustry.com/pharmaceuticals/applying-blockchain-technology-to-medicinetraceability/s40/a2766/, 2016.
56. Trujillo, G. and Guillermo, C. The Role of Blockchain in the Pharmaceutical Industry Supply Chain as a Tool for Reducing the Flow of Counterfeit Drugs. Ph.D. Thesis, Dublin Business School, Dublin, Ireland, 2018.
57. Tschorsch, F. and Scheuermann, B. Bitcoin and beyond: A technical survey on decentralized digital currencies. *IEEE Commun. Surveys Tutorials.* 18(3), 2084–2123, 2016.
58. Wang, F. Y. and Wong, P. K. Intelligent systems and technology for integrative and predictive medicine: An ACP approach. *ACM Trans. Intell. Syst. Technol.* 4(2), 1–16, 2013.
59. Wang, S., Wang, J., Wang, X., Qiu, T., Yuan, Y., et al. Blockchain-powered parallel healthcare systems based on the ACP approach. *IEEE Trans. Comput. Soc. Syst.* 99, 1–9. doi: 10.1109/TCSS.2018.2865526, 2018.
60. Witchey, N. J. Healthcare transaction validation via blockchain proof-of-work, systems and methods. US patent US20150332283 A1, 2015.
61. Wood, G. Ethereum: A Secure Decentralised Generalised Transaction Ledger; Yellow Paper: Ethereum Foundation (Stiftung Ethereum): Zug, Switzerland. Available at: https://gavwood.com/paper.pdf, 2014.
62. Xia, Q., Sifah, E. B., Asamoah, K. O., Gao, J., Du, X. and Guizani, M. MeDShare: Trust-less medical data sharing among cloud service providers via blockchain. *IEEE Access* 5, 14757–14767. doi: 10.1109/ACCESS.2017.2730843, 2017.
63. Yue, X., Wang, H., Jin, D., Li, M. and Jiang, W. Healthcare data gateways: Found healthcare intelligence on blockchain with novel privacy risk control. *J. Med. Syst.* 40(10), 218. doi: 10.1007/s10916-016-0574-6, 2016.
64. Zhang, J., Xue, N. and Huang, X. A. Secure System for Pervasive Social Network Based Healthcare. *IEEE Access.* 4, 9239–9250, 2016.
65. Zhang, P., White, J., Schmidt, D. C., Lenz, G. and Rosenbloom, S. T. Fhirchain: Applying blockchain to securely and scalably share clinical data. *Comput. Struct. Biotechnol. J.* 267–278. doi: 10.1016/j.csbj.2018.07.004, 2018.
66. Zheng, Z., Xie, S., Dai, H., Chen, X. and Wang, H. An overview of blockchain technology: Architecture, consensus, and future trends. In Proceedings of the 2017 IEEE International Congress on Big Data (BigData Congress), Honolulu, HI, USA. Available at: https://www.researchgate.org/paper/An-Overview-of-Blockchain-Technology%3A-Architecture%2C-Zheng-Xie/ee177faa39b981d6dd21994ac33269f3298e3f68, 2017.

## 11 Blockchain Theories and Its Applications

Jaipal Dhobale and Vaibhav Mishra
ICFAI Business School

## CONTENTS

- 11.1 Introduction ........................................................... 183
- 11.2 Blockchain Working ....................................................... 184
- 11.3 Types of Blockchain ....................................................... 188
- 11.3.1 Characteristics of Blockchain ........................................... 188
- 11.3.2 Challenges of Blockchain ................................................ 189
- 11.4 History and Development of Blockchain ................................... 189
- 11.4.1 Applications of Blockchain ............................................... 190
- References ................................................................. 191

### 11.1 INTRODUCTION

Blockchain! Nowadays, it has become a buzzword. What is special about it? Why and how blockchain is a breakthrough technology? Before finding answers to these questions, we will understand the different problems faced by the enterprises during the time. Prior to 2008, enterprises specifically working with database applications over the networks were facing problems like nonrepudiation, maintaining transparency, unauthorized updation/alteration, and security of these transactions against unauthorized utilization. These enterprises were heavily dependent on third parties to tackle these issues. Although we are discussing about enterprises in general, specifically financial institutions were the major concern about these problems and their solutions. This is the reason in 2008, blockchain technology was introduced to the world in the form of cryptocurrency application [1].

Blockchain is a technology that breaks these process hurdles and gets through the transactions successfully in a cost-effective and efficient way. This is the reason why it is a breakthrough technology. It is a chain of uneditable blocks of fixed sizes. These blocks are holding the transaction data up to 1MB [2]. Before preparing the blocks of transactions, these transactions were approved by the users in the network. Such prepared blocks are then attached to the previously created blocks to continue as a chain of blocks. Transaction information after adding every block in the chain is distributed across networks and is available to everyone. This process is carried out without intermediaries like financial institutions, government and non-government organizations. Blockchain carries all the work with encryption-based hash values. All the users in the network are sharing the details on the basis of peer-to-peer (P2P) network, where all the nodes are working at the same level. Every user in the blockchain network saves local copy of the blockchain. When consensus validates the transaction in the group, then it will be added as the block of transaction in the blockchain. All this is done by taking care of privacy of the resources involved in the transaction. This technology involves "smart contracts" [3] automatically through computer programs.

The specialty of the blockchain is the availability of this uneditable information to everyone giving transparency to the transactions across business applications. This is really beneficial to both enterprises and their stakeholders, where enterprises are delivering values through networks. It is like Distributed Ledger Technology (DLT) [4] but a bit different from it [5]. Both these technologies are working with decentralized networks, but in DLT, the owner/user is having more control over the networks, and information in the network is stored on different servers. In DLT, every node in the network will have its ledger and it will get updated immediately after the transaction at node level independently. In blockchain after approving transaction by consensus, blocks are prepared in cryptic format, and these are added to the chains of blocks based on certain hash functions to form the blockchain. We can say blockchain is one of the DLT. Figure 11.1 depicts the philosophy.

### 11.2 BLOCKCHAIN WORKING

Blockchain is decentralized and distributed ledger of blocks. These blocks are nothing but validated transactions by the participating nodes in the networks that cannot be modified or deleted after creating blocks. Blocks in the blockchain hold:

- Transaction data – Block version number, timestamp, and transaction details.
- Signature of the last block.
- A Nonce is the abbreviation of a number used only once and is a random string of number generated by miner, which is appended to encrypted block.

Figure 11.2 depicts the typical block in the blockchain.

![](img/115a7d47166d21dfa1d1dc5986da244b_202_0.png)

FIGURE 11.1 DLT and blockchain relationship.

![](img/115a7d47166d21dfa1d1dc5986da244b_203_0.png)

FIGURE 11.2 Typical block structure in blockchain.

Sufficient miners from the network nodes approve these transactions. Miner node with sufficient computational power can find the eligible signature to generate the blocks. These miner nodes use special hardware to attain computational power. This process is nothing but mining process. Mining process is done with proof-of-work (PoW) philosophy/protocol [3]. PoW is a protocol that calculates random hash value data from the block, which is very complicated and time-consuming computation process. After approval of transactions from miner, block will be appended to the chain as a new block. Miners upon creating new blocks will be rewarded with some sort of incentives in the form of Bitcoin.

As PoW is complicated computation and consumes a lot of computational resources, “Proof of Stake” (PoS) philosophy/protocol [6] was used as an alternate option, where miners were rewarded based on how much stake they are holding while mining the block.

“Delegate Proof of Stake” (DPoS) [7] is another form of PoS [8] in which blockchain users elect their delegate. This elected delegate node can generate and validate the blocks.

“Practical Byzantine Fault Tolerance” (PBFT) [7] is another protocol to mine the block. This protocol is used to take care of malicious activity in the blockchain. Blocks are mined in the rounds. In each round, rule-based new primary will be selected. This primary is responsible for mining the block. This process will be conducted in three steps – pre-prepared, prepared, and commit. To prevent malicious activity during each step in a round, primary has to receive consent of two-thirds of total nodes.
