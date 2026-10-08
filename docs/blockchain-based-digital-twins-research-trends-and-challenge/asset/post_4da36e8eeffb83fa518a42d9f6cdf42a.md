
familiar with one another, cryptocurrency is not required to establish transactions. A certain amount of authority is also allocated among the participants. The network must keep up the shared ledger.

The members of the permitted network have access to the shared ledger, but only those transactions they are permitted to read are visible to them. A certain amount of restriction is placed on the blockchain network by the permitted blockchain. The most popular method for managing keys for cryptography in blockchains is distributed public key infrastructure (PKI) based on blockchains [8]. PKI methods based on blockchains lack a trusted third-party or central access point. Furthermore, these methods provide transparency in the public system without presupposing any particular degree of trustworthiness on the side of the system's nodes or participants.

### 3.1.2 REQUIREMENT OF THE BLOCKCHAIN

Transparency can be achieved through sharing data and using blockchain technology. These methods clarify the public system without presupposing any particular degree of trustworthiness on the side of the system's nodes or participants. Some of the factors that make blockchain technology popular across numerous industries include the ones listed below:

- 1. Transparency is ensured. This is the only one who can change your blockchain data since the technology is open source. The immutability of blockchain-stored data increases the system's security, making it easier for early adopters to create and provide solutions.
- 2. Transaction costs are drastically decreased. On a blockchain, transactions between individuals and companies may be finalized without a trusted third party. The procedure moves more quickly because no middlemen are engaged in the deal.
- 3. Compared to conventional banks, which are limited by their business hours and established procedures, blockchain technology enables immediate settlement of transactions. Location in different parts of the globe also influences the lag time. Blockchain, on the other hand, doesn't have such restrictions. Therefore, it can settle transactions far more quickly.
- 4. Since there is no central data hub, it encourages decentralization. This makes it possible to authenticate certain transactions. Even if data is updated on numerous servers and confronts threats, a small quantity of data will be lost.
- 5. It monitors the flow of products, resulting in transparency. Additionally, this streamlines various other management procedures.
- 6. When abnormalities are found, it is always possible to return to the source, simplifying investigations and for the quick execution of necessary steps. This results in quality control.
- 7. Human mistake is eliminated by blockchain technology since it stores data and prevents tampering. Accuracy is ensured when records are checked off as they go from node to node. Because of this, a sense of responsibility is developed.
- 8. Blockchain technology makes validating, signing, and enforcing complex and intelligent contracts simple.
- 9. By eliminating electoral fraud, blockchain technology improves transparency.
- 10. Blockchain technology's dependability is considered for stock exchanges.
- 11. The supply of energy can be precisely monitored.
- 12. Blockchain technology promotes international peer-to-peer trade. Transactions with cryptocurrencies are quick, safe, and affordable. Astonishing products that sweep out the existing and competing products.
- 13. Blockchain helps slow market development leading to a dip and the technology uptake to establish the market.
- 14. By using blockchain technology, data becomes objective. In addition to maintaining data integrity, it can notify users when data has been changed. Even if a company’s data is breached, it cannot be used in any way that would undermine security. Therefore, the two do not conflict.
- 15. Using blockchain technology, we can verify the authenticity of devices in 15 different ways. Potentially eliminating the need for human contact, passwords might soon become obsolete. This is so that centralized architecture is not encouraged.
- 16. Non-repudiation is emphasized by digitally timestamping and signing each transaction. Even in the most recent version of the system, all historical data will be preserved in the log. It also results in traceability.

### 3.1.3 BLOCKCHAIN ARCHITECTURE

Like a traditional ledger, blockchain consists of blocks that include transaction information. As seen in Figure 3.1, a blockchain is an example of a distributed ledger system. Each block has just one parent, and that parent’s hash is included in the block header. Remember that the hashes of uncle blocks (the offspring of ancestor block) The transaction details would also be added to the Ethereum ledger. There is no parent block to the first block on a blockchain, called the “genesis block.” In subsections, we go deep into the workings of blockchain.

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_99_0.png)

FIGURE 3.1 The blocks in this sample blockchain are linked together in a linear fashion.

### 3.1.3.1 BLOCK

It is clear from looking at Figure 3.2 that each block has both a header and a data section. The block header includes:

| Block Version | Merkle Tree Root Hash | Time stamp | nBits | Nonce | Parent Block Hash |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Transaction Counter | | | | | |
| TX | TX | TX | TX | TX | TX | | | | | |

FIGURE 3.2 Block structure.

- i. **Block Version:** Identifies the collection of rules for validating blocks.
- ii. **Merkle Tree Root Hash:** Calculated by adding up each transaction’s soup in the block.
- iii. **Timestamp:** Time in seconds since January 1, 1970, at midnight UTC.
- iv. **nBits:** 4 bytes that increase value by 1 with each hash.
- v. **Parent Block Hash:** 256-bit hash value that references the previous block.

A transaction counter and the data encoding those transactions make up the bulk of the block. How many transactions may fit within a block is determined by the block size and the size of each transaction. To verify the 예정이다 of transactions, blockchain relies on asymmetric cryptography. Asymmetric cryptography-based digital signatures are utilized in suspicious settings. Next, we provide a quick example of a digital signature.

### 3.1.3.2 DIGITAL SIGNATURE

Private and public keys are associated with each user. They were sharing the signed transactions with everyone on the network. Digital signatures generally consist of two steps: signing and verification. Let's say Alice is interested in contacting user Bob. The signature method involves Alice encrypting some information with her private key and sending the encrypted and unencrypted copies to Bob. Bob could quickly determine whether the data has been altered. Digital signature algorithms are crucial to blockchains, and the most widely used method of digital signature generation is based on elliptic curves.

### 3.1.3.3 KEY CHARACTERISTICS OF BLOCKCHAIN

In a nutshell, the following are some of blockchain's most distinguishing features:

- 1. **Decentralization**: Traditional centralized transaction solutions add additional expenses and have the core servers sluggish since the central trusted agency must validate each transaction. Unlike the old centralized system, blockchain technology removes the requirement for a centralized server or trusted third party to process transactions. Blockchain uses consensus techniques to ensure data integrity over a decentralized network that cannot provide absolute privacy protection (details will be discussed in Section 3.4).

- **Auditability:** Using the Unspent Transaction Output architecture, the Bitcoin blockchain keeps information on user balances: An unutilized transaction must be referenced in any transaction. When a new blockchain transaction is added, any unspent transactions it references automatically transition from unspent to spent. Therefore, confirming and keeping tabs on your transactions would be simple.

### 3.1.3.4 TAXONOMY OF BLOCKCHAIN SYSTEMS

Today's blockchain infrastructures may be broken down into three distinct types. A public blockchain lets everyone see and verify past transactions and work to establish a consensus. On the contrary, a consortium blockchain would have just chosen a few nodes to participate in the consensus process. Private blockchains restrict participation in the consensus process to nodes belonging to a single company.

Since only one entity has authority over the nodes in a private blockchain, the network is highly concentrated. Because a subset of nodes would be used to reach an agreement, the consortium blockchain proposed by numerous organizations is not decentralized:

- 1. **Consensus Determination:** Any participant node in a public blockchain may forge a consensus. Only some of the nodes in a consortium blockchain verify the addition of each new block. On the other hand, private chains are managed entirely by one entity, which also has the power to set the rules for reaching a consensus.

- 2. **Read Permission:** The public can see all transactions made on a public blockchain; however, this is only sometimes the case on a private or consortium blockchain.

- 3. **Immutability:** Due to the distributed nature of the ledger, altering a transaction on a public blockchain is very difficult. In contrast, tampering
