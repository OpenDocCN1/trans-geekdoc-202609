
with transactions is less likely in private or consortium blockchains due to the smaller number of users.

- 4. **Efficiency:** Because the public blockchain infrastructure is so vast, the dissemination of blocks and transactions takes some time. This results in low transaction throughput and significant delays. Consortium blockchains and private blockchains could function better with fewer validators.

- 5. **Centralized:** Each blockchain type has different characteristics: While the public blockchain is entirely decentralized, the consortium blockchain has a degree of centralization, and the private blockchain, which a single firm governs, has no decentralization.

- 6. **Consensus Process:** Public members can participate in the blockchain’s consensus process anywhere globally. Permissioned blockchains, such as consortium and private blockchains, are distinct from public blockchains in several ways.

Since everyone worldwide may join a public blockchain, numerous users and vibrant communities often exist. Every day, new public blockchains appear. Consortium blockchain has a wide range of potential uses in the business world. For the time being, Hyperledger is developing blockchain frameworks for business networks. To aid in the creation of consortium blockchains, Ethereum has provided the necessary technology.

## 3.1.4 RELATED WORK

There are two brief reviews of projects that showcase work that does similar things using IoT and blockchain technology.

An approach to Recharging Electric Vehicle Batteries using the Ethereum Blockchain to facilitate exchanging batteries in a system for recharging electric car power packs [9]. It developed a network of connected devices based on the Ethereum blockchain. It was suggested that a “rich-thin-client” approach be used instead. Wealthy clients are machines that have the power to store the whole blockchain ledger and take part in mining operations. Thin clients are low-powered computers that can only keep the blockchain data directly applicable to them. This allows low-powered IoT nodes to participate in the blockchain network without shouldering the burden of the network’s cumbersome consensus procedures.

Connecting Battery-Powered IoT devices to a distributed ledger may interact with a blockchain network without becoming nodes themselves. A gateway node is a computer on the blockchain network that receives messages from computers that do not have blockchain software installed. Messages are processed at the gateway before being sent to the blockchain. This proof-of-concept gateway shows that even small IoT devices may interact with the blockchain network without becoming nodes in the network itself. According to Eyal [10], blockchain is used in the banking and healthcare industries to store and secure user account information and patient records. Users are no longer restricted to their physical locations for data access because of the decentralized nature of the network.

Blockchain technology may help businesses save money on transaction fees, improve efficiency in their core operations, and increase the transparency and ease with which they are compensated for using their intellectual property. A competitive edge for businesses is possible [11]. Bitcoin and other virtual currencies backed by blockchain technology provide a potential solution to the funding issues faced by enterprises. To provide one example, cryptocurrency may help businesses who wish to switch to accepting electronic payments. Automation in electronic transaction management enhances internal and external financial company execution control [12].

Because information is essential to every business, blockchain allows for secure data storage and seamless sharing [13]. Blockchain’s advantages as a distributed and encrypted ledger make it a good fit for managing digital assets at various businesses [14]. Due to the immutability of the blockchain, decentralized data storage eliminates the need to trust a single entity with your information. Instead, it makes available to users all over the globe. A firm might utilize the blockchain to store data, making it more transparent, secure, and less vulnerable to manipulation.

The distributed ledger technology known as blockchain might completely alter the logistics industry [15]. Improvements in supply-chain provenance have been made possible by recent implementations of blockchain technology and the IoT [16]. Suppose information about a product's journey from the factory to the consumer is stored on the blockchain. In that case, businesses will have a much earlier time tracing the origins of their goods and keeping an eye on the quality of the finished goods.

Blockchain is often used to establish company collaborations and inter-organizational business procedures, which businesses may use to create smart contracts. Companies may use smart contracts on blockchains to conduct automated transactions without requiring human verification. Under smart contracts, firms, for instance, may automatically submit tax returns [17].

The authors in Ref. [18] discuss the securities industry's possible use of blockchain technology. They delve into concerns about the regulation and security of European financial markets. Their paper is less of a how-guide and more of a place to air their thoughts on the possibility of such technology being used in the securities business within the context of European standards' social and legislative restrictions. As a result, they refrain from drawing any firm conclusions and concluding that such technology into practice would be challenging at best and so is unlikely shortly.

The term "smart city" refers to city planning that emphasizes three key elements necessary for a city to flourish via the collaborative production and consumption of products and services. The three main variables are humans, technological advancements and implementations, and urban coordination [9].

Most people live in urban areas, and another 2.5 billion people are projected to move by 2050. Consequently, numerous problems, such as pollution, traffic, and trash, will likely intensify. At the very least, issues like fraud and liability caused by incompetent service providers may be eliminated using blockchain technology. Third, a blockchain platform supported by the local government and geared towards documenting and organizing all of these interactions might provide the assurance needed for such a smart city to materialize if the potential rewards outweigh the potential risks.

## 3.2 BLOCKCHAIN ARCHITECTURE

This technology of Blockchain is the backbone of the present and future information-sharing business world. This is the technology behind cryptocurrency, secured healthcare, Supply Chain Management, and so on. Before understanding Blockchain's architecture, let us deeply understand its components and parameters.

## 3.2.1 BLOCKCHAIN COMPONENTS AND PARAMETERS

If we up the word Blockchain, we conveniently get two words: Block and Chain. Block is a data structure responsible for holding transactions and related data. Why are we using a Block data structure? Why don't we store data in one prominent data structure as in the cloud? In the cloud, we store data on one single centralized server. In Blockchain, we have multiple small blocks to store the data. The primary concern here is due to security reasons. The security aspect of Blockchain has been explained in detail in the later part of this and the next section.

Transactions generated at a particular point in time are gathered in one block. After some time, new transactions generated would be concluded in new blocks. Publishing transactions in new blocks is a continuous process and keeps on happening forever and ever. Each time a transaction is generated, it comes and sits inside a block and is published in the main blockchain ledger, as depicted in Figure 3.3.

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_107_0.png)

## FIGURE 3.3 Chain of blocks.

A block holds the transactions, and when we hear the word “transaction,” most transactions that come to mind are financial transactions like funds transfers, financial asset transfers, etc. However, this is different from what happens in the blockchain. In this, along with financial transactions, even information is part of it. Anything or everything that happens in the blockchain environment is a transaction. Everything is initiated as a transaction, stored as a transaction, and recognized as a transaction.

Blocks are recognized in the blockchain network uniquely with a block hash. It has one more critical parameter, which is the block ID or number. The very first block of the blockchain network is the Genesis Block. The block number is the position of the current block from the Genesis Block. The block hash is a unique hash provided to each block. Specific hashing algorithms are used for calculating the hash for each block. Each block has a unique set of data which generates a unique hash. Take an example of the Ethereum blockchain network [12, 13 and 14], as depicted in Figure 3.4. It is one of the famous block explorers of blockchain.
