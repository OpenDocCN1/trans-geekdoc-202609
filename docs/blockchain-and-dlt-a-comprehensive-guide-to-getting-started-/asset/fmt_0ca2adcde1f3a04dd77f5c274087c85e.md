
∘ Each participant, or potential buyer, is assigned a unique identifier. This could be their Ethereum wallet address or any other unique identifier associated with their account.

• Creating a whitelist:

∘ The organizer of the NFT sale generates a whitelist containing the unique identifiers of participants eligible for the exclusive event. This whitelist is essentially a list of addresses allowed to participate.

• Hashing participant identifiers:

∘ The unique identifiers (addresses) of participants are hashed individually. This can be achieved using a hash function (for example, `SHA-256`), resulting in a hash for each identifier.

• Building the Merkle tree:

∘ The hashed identifiers are organized into a Merkle tree structure. The Merkle tree is constructed by pairing and hashing the individual hashes until a single root hash is obtained.

• Publishing the Merkle root:

∘ The organizer publishes the root hash of the Merkle tree. This hash serves as a concise and secure representation of the entire whitelist.

• Participant verification:

∘ Participants interested in the NFT sale can check their eligibility by hashing their identifier and comparing it to the published Merkle root. If the hash matches, the participant is on the whitelist.

• Efficient verification process:

∘ Verifying eligibility through the Merkle tree is computationally efficient. Participants do not need to reveal their identifier; they only need to present the hashed value. This ensures privacy while allowing efficient validation.

• Event Access:

∘ During the NFT sale or event, only participants with identifiers on the whitelist (matching the Merkle root) are granted access. This creates an exclusive environment for whitelisted participants.

By using a Merkle tree in this way, the NFT sale organizer can efficiently manage large whitelists and ensure that only eligible participants gain access to exclusive events. The process also maintains privacy for participants by not requiring the exposure of their actual identifiers during the verification process.

## Conclusion

Blockchain has emerged as a paradigm shift in the last decade. This decentralized system has revolutionized the essence of digital trust and collaboration. The journey of this chapter has unveiled the foundational concepts of blockchain, their types, and their applications. A strong understanding of technical concepts, like a `Merkle tree`, block header hash, block height, and more, will make it easy to decipher the ideas explored in the next chapter.

The next chapter will provide readers with a detailed knowledge of Bitcoin. It will explain Bitcoin's origins, evolution, and other fundamental concepts behind the King cryptocurrency. Readers will get to learn about Bitcoin concepts, like cryptographic keys, wallets, and addresses. Besides, advanced Bitcoin features like multi-signature addresses and `Base58` encoding are also covered in the next chapter.

## Questions and answers

1. How does blockchain ensure security?

Ans.: Blockchain network ensures security through cryptographic techniques, including encryption and hashing. Under this, each block contains a cryptographic hash of the previous block. This creates an immutable chain.

2. What are the different types of blockchains?

Ans.: Blockchains can primarily be categorized into three types – Public blockchains, which are open to anyone; Private blockchains, which offer restricted access; Consortium blockchains, which are semi-decentralized.

3. What are the applications of blockchain?

Ans.: Blockchain technology has usability in various industries, including but not limited to finance and banking, healthcare, supply chain management, gaming, streaming, and more.

4. What role does consensus play in a blockchain network?

Ans.: Consensus mechanisms are deployed to ensure agreement among parties on the validity of transactions. They play a vital role in decentralized decision-making and preventing fraudulent transactions.

5. How does a blockchain network validate transactions?

Ans.: A blockchain network validates transactions through consensus mechanisms such as `PoW` and `PoS` or any other algorithms developed for that purpose. Miners or validators verify transactions before they are added to the blockchain.

## Multiple choice question

1. What is the fundamental concept of blockchain technology?

a. Centralized data storage

b. Hierarchical database structure

c. Peer-to-peer networking

d. Decentralized ledger system

2. Which data structure is crucial to blockchain formation?

a. Arrays

b. Trees

c. Linked lists

d. Stacks

3. Which blockchain type allows anyone to participate without permission?

a. Permissioned blockchain

b. Public blockchain

c. Private blockchain

d. Consortium blockchain

4. What role does a Merkle tree have in blockchain technology?

a. It encrypts data within blocks

b. It validates the integrity of transactions

c. It manages user permissions

d. It ensures decentralized consensus

5. What makes blockchain technology resistant to tampering?

a. User authentication

b. Redundant data storage

c. Encrypted transmission protocols

d. Cryptographic hashing

## Answers

| 1. | | d |
| --- | --- | --- |
| 2. | | d |
| 3. | | b |
| 4. | | b |
| 5. | | d |

**Join our book's Discord space**

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![](images/Discord.png)

# CHAPTER 3  

Bitcoin

## Introduction

In the past few decades, hardly a phenomenon has been able to capture as much attention as Bitcoin. It has evolved from a cryptographic experiment into a global digital currency. Moreover, it has disrupted the way we perceive and interact with money.

Bitcoin is a decentralized and transparent form of digital currency. It does not have any physical form, and its existence is in the digital world. Since Bitcoin is a decentralized currency, it is free from the control of any central authority. It is powered by blockchain technology and is based on the concepts of decentralization, cryptography, and immutable ledgers. Notably, Bitcoin aims to foster trust in financial transactions.

In this chapter, we will explore the multifaceted nature of Bitcoin, its origins, core principles, and technological intricacies. The chapter will shed light on how this digital currency has made its way to wider acceptance and integration into mainstream financial conversations.

## Structure

This chapter contains the following topics:

• Bitcoin

• Consensus mechanism

• Encrypted private keys in blockchain

• Pay-to-script address

• Multi-sig addresses

• Vanity address

• Bitcoin wallet

• Transaction script

• Bitcoin mining

• Structure of a block

• Bitcoin relay network

• Blockchain fork

• Bitcoin testnet

• Basis of Bitcoin forensic

## Objectives

The chapter aims to provide readers with a comprehensive understanding of Bitcoin. It will define and elucidate the fundamental principles that lie behind the meteoric rise of the King coin. It will also evaluate the broader implications of Bitcoin in the global financial sphere. The chapter will highlight emerging trends, innovative applications, and the disruptive potential of Bitcoin in shaping financial transactions in various industries. Thus, readers will get to learn the future prospects of Bitcoin and equip themselves with all the nitty-gritty of this digital currency.

## Bitcoin
