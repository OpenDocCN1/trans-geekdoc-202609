
# 8 A Complete Study on the Major Protocols of Blockchain

S. Palanikumar and Sivaprasad Abirami
Noorul Islam Centre for Higher Education Shah and Anchor Kutchhi Engineering College

# CONTENTS

- 8.1 Introduction ............................................................................................ 120
- 8.2 Blockchain Basics ................................................................................... 120
- 8.2.1 Peer-to-Peer Network (P2P) ................................................................ 121
- 8.2.2 Distributed Ledger System ................................................................... 121
- 8.2.3 Key Cryptography ................................................................................ 121
- 8.2.4 Hashing ............................................................................................ 122
- 8.2.5 Proof of Work ..................................................................................... 122
- 8.3 Blockchain Protocols ............................................................................... 122
- 8.3.1 Bitcoin Protocol .................................................................................. 123
- 8.3.1.1 What Is Bitcoin?...................................................................... 123
- 8.3.1.2 Why Bitcoin?.................................................................. 123
- 8.3.1.3 Features of Bitcoin ................................................................ 124
- 8.3.1.4 Transactions ................................................................................... 124
- 8.3.2 Ethereum Protocol ................................................................................ 128
- 8.3.2.1 What Is Ethereum?............................................................... 128
- 8.3.2.2 Why Ethereum?.................................................................. 128
- 8.3.2.3 Transaction ................................................................... 128
- 8.3.3 Ripple Protocol ................................................................................ 131
- 8.3.3.1 What Is Ripple?............................................................... 131
- 8.3.3.2 Why Ripple?.................................................................. 131
- 8.3.3.3 Transaction ................................................................ 131
- 8.3.4 Litecoin Protocol ............................................................................ 132
- 8.3.4.1 What Is Litecoin?............................................................... 132
- 8.3.4.2 Why Litecoin?.................................................................. 132
- 8.3.4.3 Transaction ................................................................ 133
- 8.4 Conclusion ............................................................................................ 133

References ................................................................................................................... 133

# 8.1 INTRODUCTION

The following are the major problems with bank transactions:

- The technical issues
- The account might be hacked
- Exceeded transfer limits
- High transfer charges

The above problems can be solved by cryptocurrency.
Before we start with the introduction of blockchain, it is very important to understand the difference between two major terms: bitcoin and blockchain.
**Bitcoin:** It is a cryptocurrency that is established globally to store values and was started in 2009[1–3].
**Blockchain:** It is a backbone technology adapted by the digital cryptocurrency for secured transactions. Blockchain technology was commercially implemented first by bitcoin. Blockchain was introduced in 2008[1–3].

Blockchain provides a decentralized architecture on a peer-to-peer network. It is a ledger of transaction shared among multiple peers on a distributed environment to avoid security faults. All peers participate in the transaction and inspect the whole process instead of using a single user control that ensures authentication and avoids any hacker to mislead the transaction with the help of public key cryptography and the hash function [1,3].
In recent years, blockchain has been adapted in varies fields such as medical, financial, government, and many more [4].

# 8.2 BLOCKCHAIN BASICS

Let us understand the basic elements of blockchain, which is illustrated in Figure 8.1.

| Key Elements of Blockchain |
| :--- |
| Peer-to-Peer Network | Distributed Ledger System | Key Cryptography | Hashing | Proof-of-Work |

FIGURE 8.1 Key elements of blockchain.

# Major Protocols of Blockchain

![](img/5197498995d15589ead293656bce20db_135_0.png)

FIGURE 8.2 Various network models. (a) Centralized network, (b) decentralized network, and (c) distributed network.

# 8.2.1 PEER-TO-PEER NETWORK (P2P)

This network is distributive in nature and is in a decentralized manner. There is no concept of centralized service, instead all the nodes are linked with each other to make the transaction or data transfer (Figure 8.2) [5].

# 8.2.2 DISTRIBUTED LEDGER SYSTEM

In the distributed ledger system, all nodes keep a copy of the data record instead like a centralized system where the single centralized node keeps the data record. All nodes participate in the data transfer or transaction, for which all nodes carry the updated copies of the ledger or the data record in the blockchain network. All the participating nodes of the transaction will have the same copy of the data record and the record of each other node. As everyone has updated the copy of the data record, no one can manipulate/falsify the transaction.

# 8.2.3 KEY CRYPTOGRAPHY

During the transaction in a blockchain, the confidentiality, authentication, and integrity are provided with the help of an asymmetric key cryptography. In asymmetric key cryptography, two keys are used: the private key, which is used to encrypt the data/transaction that is available with the intended user to do the transaction, and the public key, which is distributed over all the participants using the elliptic curve Diffie–Hellman–Merkle and is used to decrypt the data/transaction. The combination of private and public key ensures the data security.

# Blockchain Technology

![](img/5197498995d15589ead293656bce20db_136_0.png)

FIGURE 8.3 Hashing techniques.

# 8.2.4 HASHING

It is a method of nonreversible encryption used in blockchain to improve the transaction security. Hashing converts the variable length data into fixed length data as output using the secure hash algorithm SHA 256 (SHA 256) (Figure 8.3).

# 8.2.5 PROOF OF WORK

The proof of work from each node of the decentralized peer-to-peer network performs the transaction. All the participants are supposed to do complex computations to validate themselves as a valid participant. The computational power of the legitimate participant to be greater than the hacker computational power to make a legal transaction. The Sybil attack and the doubling problems that discussed in the later part are removed with the help of proof of work.

The proof of work contains a complex mathematical calculation that is identical to Adam Back's hash scan [7]. The proof of work scan is a special value called nonce (number only used once), which is a number added to the hashed value in the target will set the number of zero bits. The hash with many zero bits will set the required number of zero bits. The output hash contains zeros in the beginning, which should be less than that of the target. The proof of work is verified by incrementing the nonce to achieve the target number of zeros bits in the starting of the hash. Once the computation is completed, it cannot be changed. If the hacker tries to change the computation, the verification will be done by all the other blocks involved in the transaction since all wishes to change a different hash value than the hacked value. If the hacker wishes to change the block, he or she should have a very high computational power to change the hash value in all the blocks that participate in the transaction (Figure 8.4).

# 8.3 BLOCKCHAIN PROTOCOLS

Blockchain is growing and popular technology. After the growth and spread of bitcoin protocol, many other protocols have been designed for various applications in different domains. In this chapter, the major protocols are explained with the features, the transaction method, and the advantages and the disadvantages. The major protocols are illustrated in Figure 8.5.
