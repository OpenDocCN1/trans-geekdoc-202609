![cover](OEBPS/images/cover.jpg)

![image](OEBPS/images/cover.jpg)

# Ultimate Cardano  
Smart Contracts

![](OEBPS/images/line.jpg)

# Unlock the Full Potential of the Cardano  
Blockchain by Developing Real-World Web 3.0  
Projects Using Plutus Smart Contracts, and  
App Development

![](OEBPS/images/line.jpg)

# Lawrence Arthur Ley

![](OEBPS/images/logo.jpg)

[www.orangeava.com](http://www.orangeava.com)

Copyright © 2024 Orange Education Pvt Ltd, AVA™

All rights reserved. No part of this book may be reproduced, stored in a retrieval system, or transmitted in any form or by any means, without the prior written permission of the publisher, except in the case of brief quotations embedded in critical articles or reviews.

Every effort has been made in the preparation of this book to ensure the accuracy of the information presented. However, the information contained in this book is sold without warranty, either express or implied. Neither the author nor **Orange Education Pvt Ltd** or its dealers and distributors, will be held liable for any damages caused or alleged to have been caused directly or indirectly by this book.

**Orange Education Pvt Ltd** has endeavored to provide trademark information about all of the companies and products mentioned in this book by the appropriate use of capital. However, **Orange Education Pvt Ltd** cannot guarantee the accuracy of this information. The use of general descriptive names, registered names, trademarks, service marks, etc. in this publication does not imply, even in the absence of a specific statement, that such names are exempt from the relevant protective laws and regulations and therefore free for general use.

**First published:** June 2024

**Published by:** Orange Education Pvt Ltd, AVA™

**Address:** 9, Daryaganj, Delhi, 110002, India

275 New North Road Islington Suite 1314 London,

N1 7AA, United Kingdom

**ISBN:** 978-81-97396-53-3

[www.orangeava.com](http://www.orangeava.com)

# Dedicated To

*My Children:  
Daniel, Sofi, Josie*

*And their Future*

# About the Author

**Lawrence Arthur Ley** has a Computer Science degree from the University of Toronto and over 20 years of IT industry experience. He is passionate about learning new technologies and how they can make a positive impact. His Cardano journey started in 2021 with the Plutus Pioneers program, and he has worked on several open-source Cardano impact projects. Lawrence is a professor in the Blockchain Development Program at George Brown College in Toronto and runs the Cardano Blockchain Toronto monthly meetup with over 500 members.

His professional experience includes IT consulting in the telecommunications, banking, and retail industries. He has a proven track record of building and managing complex, integrated, highly scalable consumer and retail applications. His first experiences with cryptocurrencies involved mining Bitcoin and participating in local meetups where he met Ethereum co-founders Vitalik Buterin and Anthony Di Iorio.

In July 2023, Lawrence was invited to attend the Cardano CIP-1694 Governance Workshop in Edinburgh, Scotland, where he met Cardano co-founder Charles Hoskinson. He was deeply honored to participate in the governance workshops with many highly esteemed individuals from the Cardano ecosystem. He continues to be active in the Cardano community, exploring new technologies and helping others along the way.

# About the Technical Reviewer

**Venu Kumar Borra** is a highly accomplished Technical Architect specializing in distributed computing, smart contracts, and digital assets. He has extensive experience with both public and private blockchains, including Cardano, Ripple, Ethereum, Hyperledger, Corda, and Directed Acyclic Graphs (DAGs). His expertise spans fintech, supply chain, agri-tech, and healthcare.

A strong advocate for Self-Sovereign Identity (SSI) and Zero Knowledge proofs, Venu has practical experience in ZK implementations. He is also a Cryptographic Researcher and Podcast Creator, underscoring his commitment to blockchain technology. Venu’s proficiency in tokenization and tokenomics principles enhances business operations and drives innovation.

His technical skills include programming in Solidity, Go-lang, Python, Kotlin, and Haskell, and using development tools like Hardhat and Brownie. Venu is also skilled in emerging technologies such as AI, machine learning, IoT integration, and Distributed Ledger Technology (DLT).

In his current role, Venu focuses on the architecture, design, and development of blockchain systems, emphasizing Explainable AI (XAI), auditability, and transparency solutions. He manages GenAI solutions, leveraging Large Language Models (LLMs) and building Minimum Viable Products (MVPs) using the RAG approach.

As a Board of Trustees member for the Blockchain For Productivity Forum (BCPF), Venu promotes blockchain adoption and implements innovative solutions for social welfare projects in India and internationally. Previously, as the Managing Director of Blocmatrix IT Solutions Pvt Ltd, he delivered cutting-edge solutions across various industries.

Venu holds an MBA in Executive Marketing from NIBM, India, and a Bachelor’s degree in Mathematics from the University of Madras, India. His competencies include solution design and development, product management, cloud deployment, consulting, project management, quality assurance, team leadership, training, and technical documentation. Venu excels at translating complex business requirements into innovative technological solutions, consistently driving success and efficiency.

# Acknowledgements

I wrote this book to help others learn how blockchain works and create decentralized applications on the Cardano Blockchain. Blockchain is a fascinating technology that can significantly disrupt existing business models. Writing a book about rapidly changing technology, however, is not easy because a lot can change from when you start the book to when it is finally published. Therefore, this book will provide sufficient foundational knowledge and techniques applicable in the foreseeable future, although language features and versions will change over time.

This book only exists because of the true pioneers creating alternative languages such as Aiken and Helios. Although these two projects have different approaches and priorities, both were born out of necessity to create a better Cardano Smart Contract development experience. I am genuinely grateful for this, as is the larger Cardano developer ecosystem.

I wish to thank my family, who endured me constantly working on ‘the book.’ Their support and understanding were a constant source of inspiration.

Finally, I thank Orange AVA Publishing for their continuous support. This book would not have been possible without them.

Lastly, to the readers, thank you for choosing this book to help you Master Cardano Smart Contracts. May it be an invaluable resource as you discover this new and profound technology.

# Preface

Deciding what blockchain to use when building a decentralized application is a big decision. There are many considerations, and switching to a different blockchain may take time and effort. *Ultimate Cardano Smart Contracts* aims to help demonstrate Cardano's features and provide a hands-on approach to writing Smart Contracts. Using this knowledge and insight, you will understand the benefits of building on Cardano and why there is such a large and passionate Cardano community.

This book comprises 14 chapters, each building upon the previous chapters. We will start with the fundamentals of blockchain and then move into writing smart contracts. The book will close with an overview of the Cardano ecosystem and ethos. The book includes technical and non-technical material, so it will appeal to experienced developers and non-technical entrepreneurs looking to improve their knowledge and understanding.

**[Chapter 1. Blockchain Evolution](#c01.xhtml)**: This chapter will introduce blockchain and distributed ledger technology, focusing on prior implementations and challenges to overcome. We will look at the Bitcoin and Ethereum whitepapers and how they paved the way for the third-generation blockchain, Cardano. The blockchain trilemma will be examined, along with a review of tokenomics and Cardano’s native currency, Ada. Finally, we will finish the chapter by discussing the Cardano roadmap and blockchain use cases.

**[Chapter 2. Cryptography and Consensus Algorithms Overview](#c02.xhtml)**: This chapter will briefly introduce cryptography and how it is used in blockchain technology. We will first look at securing a blockchain using the Proof of Work consensus protocol. Then, we will look at Proof of Stake and its benefits over Proof of Work. Finally, we will review Ouroboros, the Proof-of-Stake consensus protocol used by Cardano.

**[Chapter 3. Transactions](#c03.xhtml)**: This chapter will examine Cardano addresses and the UTXO architecture. It will also introduce Smart Contracts and explain how they are executed and evaluated. We will see how Redeemers and Datums pass data into Plutus scripts and where Datums are also used for data storage and persistence. Finally, we will examine the transaction Witness Set and how it authorizes the spending of transaction inputs.

**[Chapter 4. Plutus](#c04.xhtml)**: In this chapter, we will examine the Plutus core specification, Untyped Plutus Core (UPLC), used for executing Cardano Smart Contracts. We will also explore the different data structures used in Plutus and how to serialize them using the Concise Binary Object Representation (CBOR) format. Next, we will calculate the CPU and memory units using the Plutus cost model and explain why we need to include collateral in a transaction.

**[Chapter 5. Transaction Builder](#c05.xhtml):** This chapter will combine our knowledge of on-chain Plutus scripts and how to lock Ada into a smart contract using off-chain code. We will look at Cardano wallets, the gateway to interacting with the blockchain and smart contracts. Next, we will look at tooling to help build and submit transactions like Demeter. run. Then, we will make a simple, smart contract for vesting using two popular approaches: Helios and Lucid + Aiken.

**[Chapter 6. Validators:](#c06.xhtml)** In this chapter, we will look in detail at what a validator is and why they are so important. We will show how to spend UTXOs locked at a validator script address and how to access data provided in a Redeemer or Datum. Next, we will dive deep into understanding what ScriptContext is and how it is used to access all inputs and outputs associated with a transaction. The chapter will review on-chain and off-chain code examples using two different approaches: Helios and Lucid + Aiken.

**[Chapter 7. Minting:](#c07.xhtml)** This chapter will examine Cardano native assets and how they differ from Ethereum tokens created using the ERC-20 standard. We will discuss the concept of token bundles and how to optimize coin selection. We will then dive deep into minting Cardano native tokens, the differences between Non-Fungible Tokens (NFTs) and Fungible Tokens (FTs), and the metadata standards CIP-25 and CIP-68. We will combine this with a working minting policy use case and demo.

**[Chapter 8. Tooling:](#c08.xhtml)** In this chapter, we will review the tools and service providers you can use for off-chain development. We will look at Cardano Blockchain API providers such as Blockfrost, Maestro, Koios, and Dandelion. Then, we will look at hosted environments with Demeter.run to set up services like Cardano Node, Ogmios, and Kupo. Finally, we will look at how to set up a local Devnet for rapid development and prototyping with the Yaci DevKit.

**[Chapter 9. Ticket Application Design:](#c09.xhtml)** This chapter reviews Smart Contract design patterns that leverage and utilize the UTXO architecture. Anti-patterns are also examined, which should be avoided and lead to poor application performance and UTXO contention. We look at Cardano Improvement Proposals (CIPs) and how they apply to the application design. Next, we will create state machine diagrams to model the event ticket application, looking at the inputs and outputs required for a successful transaction. Finally, we will conclude the chapter by reviewing sequence diagrams showing each use case's interaction between system components.

**[Chapter 10. Ticket Application Implementation:](#c10.xhtml)** In this chapter, we will walk through the implementation of a ticket application, including blockchain integration. We will look at the application stack, which includes CharkraUI, Next.js, Redis DB, and Blockfrost. Next, we will inspect the front-end off-chain code used to build and submit transactions. Then, we will review the corresponding Smart Contract on-chain code, business logic, and validation rules. Finally, we will run through an end-to-end demo of the application.

**[Chapter 11. Testing, Security, and Scaling:](#c11.xhtml)** This chapter will show how to test Smart Contracts and include them in a popular testing framework such as Vitest. We will look at both the traditional testing and property-based testing approaches. Next, we will focus on security and review vulnerabilities identified in real-world Cardano application audits. We will look at code examples of how to make your Smart Contracts more robust and more resilient to any such attacks. Finally, we will close the chapter by discussing scaling and some tools and techniques to improve dApp performance.

**[Chapter 12. Troubleshooting:](#c12.xhtml)** This chapter will walk through the debugging tools and techniques for Helios and Aiken. We will look at how to generate CBOR for a transaction and compare data types against the formal specification. We will look at techniques to reduce the computational overhead of a Plutus script that exceeds the execution budget. We will also examine compiler errors and how transaction builders provide robust error-handling support. Finally, we will look at Cardano Node and Browser Wallet errors and how to diagnose them accordingly.

**[Chapter 13. Cardano Ecosystem:](#c13.xhtml)** This chapter will review the state of Cardano and the GitHub repositories that contain all of the Cardano source code and specifications. We will look at the Cardano Improvement Process (CIP) and how to make changes and improvements to the Cardano blockchain. Next, we will explore the era of Voltaire and CIP-1694 regarding Cardano governance. We will also review Project Catalyst, one of the largest decentralized innovation platforms that provides grant funding to Cardano projects. Finally, we will look at Cardano partner chain frameworks such as Midnight, a data-protection blockchain.

**[Chapter 14. Closing Remarks:](#c14.xhtml)** This chapter will review the ethos of Cardano. We will examine the software industry standards and how these standards fall short for high assurance software. We will see how **IOG** (**IOHK**) used semi-formal methods to build Cardano and how cryptographic associations like IACR facilitate peer review. Through real-world examples, we will explore Cardano's potential to drive positive social change. We will also discuss regulatory and compliance risks. Finally, we will review the five stages of technology adoption and the Cardano journey.

# Downloading the code  
bundles and colored images

Please follow the link or scan the QR code to download the  
***Code Bundles and Images*** of the book:

# [https://github.com/ava-orange-education/Ultimate-Cardano-Smart-Contracts](https://github.com/ava-orange-education/Ultimate-Cardano-Smart-Contracts)

![](OEBPS/images/qr.jpg)

The code bundles and images of the book are also hosted on  
**[*https://rebrand.ly/ad614f*](https://rebrand.ly/ad614f)**

![](OEBPS/images/qr1.jpg)

In case there’s an update to the code, it will be updated on the existing GitHub repository.

# Errata

We take immense pride in our work at **Orange Education Pvt Ltd** and follow best practices to ensure the accuracy of our content to provide an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at :

**[errata@orangeava.com](mailto:errata@orangeava.com)**

Your support, suggestions, and feedback are highly appreciated.

# DID YOU KNOW

Did you know that Orange Education Pvt Ltd offers eBook versions of every book published, with PDF and ePub files available? You can upgrade to the eBook version at [**www.orangeava.com**](http://www.orangeava.com) and as a print book customer, you are entitled to a discount on the eBook copy. Get in touch with us at: **[info@orangeava.com](mailto:info@orangeava.com)** for more details.

At **[www.orangeava.com](http://www.orangeava.com)**, you can also read a collection of free technical articles, sign up for a range of free newsletters, and receive exclusive discounts and offers on AVA™ Books and eBooks.

# PIRACY

If you come across any illegal copies of our works in any form on the internet, we would be grateful if you would provide us with the location address or website name. Please contact us at **[info@orangeava.com](mailto:info@orangeava.com)** with a link to the material.

# ARE YOU INTERESTED IN AUTHORING WITH US?

If there is a topic that you have expertise in, and you are interested in either writing or contributing to a book, please write to us at [**business@orangeava.com**](mailto:business@orangeava.com). We are on a journey to help developers and tech professionals to gain insights on the present technological advancements and innovations happening across the globe and build a community that believes Knowledge is best acquired by sharing and learning with others. Please reach out to us to learn what our audience demands and how you can be part of this educational reform. We also welcome ideas from tech experts and help them build learning and development content for their domains.

# REVIEWS

Please leave a review. Once you have read and used this book, why not leave a review on the site that you purchased it from? Potential readers can then see and use your unbiased opinion to make purchase decisions. We at Orange Education would love to know what you think about our products, and our authors can learn from your feedback. Thank you!

For more information about Orange Education, please visit **[www.orangeava.com](http://www.orangeava.com)**.

# [CHAPTER 1](#toc.xhtml#c01)

# [Blockchain Evolution](#toc.xhtml#c01)

# [Introduction](#toc.xhtml#s1a)

This chapter will introduce blockchain and distributed ledger technology, focusing on prior implementations and challenges to overcome. We will look at the landmark Bitcoin whitepaper and how it ushered in a new era of digital currencies. Next, we will introduce the Ethereum whitepaper, how the concept of smart contracts was born, and the problems that Ethereum was addressing. This chapter will also review the key takeaways from the famous Charles whiteboard video that led many to dig deeper into the Cardano ecosystem. We will then explore the classic Blockchain Trilemma of decentralization, security, and scalability. There will also be a review of tokenomics and Cardano’s native currency, Ada. Finally, we will finish the chapter discussing the Cardano roadmap and blockchain use cases.

# [Structure](#toc.xhtml#s2a)

In this chapter, we will discuss the following topics:

*   Distributed Ledger Technology
*   Bitcoin Whitepaper
*   Ethereum Whitepaper
*   Charles Hoskinson Whiteboard Video 
    *   Scalability
    *   Interoperability
    *   Sustainability
*   Blockchain Trilemma
*   Tokenomics 
    *   Token Allocation
    *   Token Distribution
    *   Token Allocation Comparison
    *   Cardano Inflation Rate
*   Cardano Roadmap
*   Blockchain Use Cases

# [Distributed Ledger Technology](#toc.xhtml#s3a)

The concept of using a ledger to record credit and debit transactions has existed for thousands of years.[¹](#c01.xhtml#ftn1) With the advent of distributed computing, the concept of the ledger was extended, where multiple parties can see and update a ledger using computers connected to a network. The difference between a centralized and a decentralized distributed ledger, as shown in *[Figure 1.1](#c01.xhtml#fig1_1)*, is that you no longer have a single central authority. The issue, however, is that you still need a way to ensure the correct ordering of immutable transactions. In 1991, **Stuart Haber** and **W. Scott Stornetta** wrote “*How to Time-Stamp a Digital Document,*” which described an approach using timestamps and cryptographic hashes to prove when a digital document had been created or if it had been modified.[²](#c01.xhtml#ftn2) This approach was used to check for immutability.

![](OEBPS/images/Figure-1.1.jpg)

**1.1:** Types of Ledgers

# [Byzantine Generals Problem](#toc.xhtml#s4a)

Another core aspect of distributed ledger technology is ensuring the data stored on each node is correct in a network that may include malicious or unavailable nodes. This problem is known as the Byzantine Generals Problem (BGP).[³](#c01.xhtml#ftn3) BGP describes a scenario where generals surround a castle for an attack and must communicate and coordinate with each other via messengers. The attack will only succeed if all generals attack simultaneously, using the messengers to signal the attack. The risk, however, is that the attack signal may or may not be received correctly by all generals because the messengers may have been killed or bribed. A network resistant to these types of failures is called Crash Fault-Tolerant (CFT) and Byzantine Fault-Tolerant (BFT), respectively.

The paper “*Building Secure File Systems Out of Byzantine Storage*” by **Mazières** and **Shasha** introduces a Byzantine fault-tolerant (**BFT**) algorithm that allows a distributed network to reach a consensus on the state of data in an untrusted network.[⁴](#c01.xhtml#ftn4) The authors created a consistency protocol called **SUNDR** (Secure Untrusted Data Repository) by leveraging redundancy to handle Byzantine failures and using digital signatures. If a discrepancy is discovered, the protocol will detect malicious behavior and partition file system data blocks into forks.

# [Network Consensus](#toc.xhtml#s5a)

For a network to agree on a common state, it needs to use a consensus algorithm that has two key properties:

*   **Liveness**: Must continue to make progress in deciding the network state.
*   **Safety**: Once honest nodes have confirmed the network state, they must remain committed to this decision.

When dealing with decentralized ledger networks, it is vital for the network’s security that the majority of nodes participating in the consensus algorithm are honest. If not, then this is known as a 51% attack, where a single entity controls the majority of nodes. When this happens, the attacker can control the consensus outcome and undo past (or deny future) transactions that may benefit the attacker.

The concept of using computation cycles for solving puzzles in decentralized consensus was first introduced in 1998 by **Wei Dai**’s b-money.[⁵](#c01.xhtml#ftn5) The benefit of this approach is that it does not require a centralized authority to create money. “*In 2005,* ***Hal Finney*** *introduced the concept of ‘reusable proofs of work’*[⁶](#c01.xhtml#ftn6)*, a system that uses ideas from b-money together with* ***Adam Back****’s computationally difficult Hashcash puzzles to create a concept for a cryptocurrency*.”[⁷](#c01.xhtml#ftn7) This approach, unfortunately, still relied on a trusted back-end,[⁸](#c01.xhtml#ftn8) so it did not meet the goal of trustless, decentralized money.

# [Bitcoin Whitepaper](#toc.xhtml#s6a)

In 2008, the pseudonym **Satoshi Nakamoto** published “*Bitcoin: A Peer-to-Peer Electronic Cash System”* to address the double spending problem with a decentralized, peer-to-peer electronic cash system, as shown in *[Figure 1.2](#c01.xhtml#fig1_2)*. In this landmark paper, Satoshi proposed “*a peer-to-peer network using proof-of-work to record a public history of transactions that quickly becomes computationally impractical for an attacker to change if honest nodes control a majority of CPU power*.”[⁹](#c01.xhtml#ftn9) This is accomplished by using network timestamp transactions and “*by hashing them into an ongoing chain of hash-based proof-of-work, forming a record that cannot be changed without redoing the proof-of-work. The longest chain not only serves as proof of the sequence of events witnessed but also as proof that it came from the largest pool of CPU power. As long as a majority of CPU power is controlled by nodes that are not cooperating to attack the network, they’ll generate the longest chain and outpace attackers*.”[^(10)](#c01.xhtml#ftn10)

![](OEBPS/images/Figure-1.2.jpg)

**Figure 1.2:** Bitcoin Ledger

Bitcoin’s **Proof-of-Work** implementation was innovative because it solved two problems at the same time. First, it provided a simple and moderately effective consensus algorithm, allowing nodes in the network to collectively agree on a set of canonical updates to the state of the Bitcoin ledger.[^(11)](#c01.xhtml#ftn11) Second, it provided a mechanism for allowing free entry into the consensus process, solving the political problem of deciding who gets to influence the consensus while simultaneously preventing Sybill attacks.[^(12)](#c01.xhtml#ftn12)

On January 3rd, 2009, the first Bitcoin block was minted, and a new era of permissionless and trustless digital currency was born. In the subsequent chapters on *Cryptography and Consensus Algorithms Overview* and *Transactions,* we will explore the Bitcoin whitepaper in more detail.

# [Ethereum Whitepaper](#toc.xhtml#s7a)

The Ethereum whitepaper by **Vitalik Buterin,** published in 2014, introduced a new way of using blockchain technology to create a more general-purpose distributed computing platform. In particular, he described the concept of a Smart Contract, which can be considered as cryptographic “*boxes*” that contain value and only unlock it if certain conditions are met.[^(13)](#c01.xhtml#ftn13) Unlike Bitcoin scripts, Ethereum Smart Contracts would be Turing-complete and have access to a global state and persistence storage, as shown in *[Figure 1.3](#c01.xhtml#fig1_3)*. The Smart Contract running in the Ethereum Virtual Machine (**EVM**) would be value-aware and could read the Ether (ETH) amount at the contract account.

![](OEBPS/images/Figure-1.3.jpg)

**Figure 1.3:** Ethereum Ledger

The global state in Ethereum contains two types of accounts: externally owned accounts, controlled by private keys, and contract accounts, controlled by their Smart Contract code.[^(14)](#c01.xhtml#ftn14) Smart Contracts are self-executing since they contain all the information they need within a single node. By using a global state, Ethereum has the advantage that it does not need to recreate all previous transactions to determine the current state of the network. It only has to apply the current transactions in the most recent block to the last global state stored on the node.

Transactions in Ethereum refers to a signed data package that stores a message sent from an externally owned account. Contracts can send messages to other contracts, where messages are virtual objects that are never serialized and exist only in the Ethereum execution environment.[^(15)](#c01.xhtml#ftn15) Ethereum is also considered non-deterministic because of the use of a global state. In contrast, Bitcoin and Cardano are deterministic since they only use a local state in transactions.

Ethereum smart contracts have the risk of infinite loops because they are Turing-complete scripts. To address this, Ethereum uses the concept of gas fees that are consumed when a smart contract (or chain of smart contracts) is executed. When a transaction is submitted, it must include the maximum amount of gas it will consume to safeguard against an infinite loop code execution.

# [Charles Hoskinson’s Whiteboard Video](#toc.xhtml#s8a)

The popular whiteboard video by **Charles Hoskinson,** with over 1M views,[^(16)](#c01.xhtml#ftn16) introduces the concept that Cardano is a third-generation blockchain, with Bitcoin being the first generation and Ethereum being the second generation. Cardano builds upon the first- and second-generation blockchains and addresses some of the key pain points from each, namely:

*   Scalability
*   Interoperability
*   Sustainability

# [Scalability](#toc.xhtml#s9a)

Charles indicates that neither Bitcoin nor Ethereum can scale to billions of users, and to improve scalability, one must focus on three key areas:

*   **TPS**: Transaction per second.
*   **Network**: Network bandwidth required to use and share the network.
*   **Storage**: The size of the blockchain that needs to be saved persistently.

Cardano has created, published, and released Ouroboros, a Provable secure Proof-of-Stake Protocol to increase TPS. This protocol requires significantly fewer resources than Proof-of-Work, so parallelism and sidechains can be introduced to increase **TPS**. Cryptographic compression algorithms, in addition to sidechains, will reduce the size of the blockchain that needs to be transmitted and stored, improving both **network** and **storage** scalability. The concept of sidechains allows the base layer of Cardano to act as a settlement layer, while sidechains act as computation layers. When scaling to billions of users, it is not feasible or practicable to broadcast, relay, and store every transaction to all nodes on a settlement layer.

# [Interoperability](#toc.xhtml#s10a)

Another area that Cardano aims to address is how a blockchain interacts with other blockchains and legacy systems. In particular, Charles sees a future where multiple blockchains exist, and Cardano can interoperate with each other so value can flow between them. Additionally, there needs to be awareness and the ability to transact with traditional financial systems. To do so, a blockchain needs to have the following capabilities:

*   **Metadata**: The story behind a transaction.
*   **Attribution**: Identity of senders and receivers.
*   **Compliance**: KYC and anti-money laundering.

![](OEBPS/images/Figure-1.4.jpg)

**Figure 1.4:** Cardano Interoperability

Each of these topics is highly sensitive and contentious in the blockchain space. Great care must be exercised when dealing with these items since they may contain personal information stored on an immutable blockchain.

# [Sustainability](#toc.xhtml#s11a)

The last area to address is how a blockchain will grow, be funded, and be governed. Will it be a patronage model susceptible to being co-opted by large entities motivated by self-interest? Or will it be a one-time initial coin offering (ICO), which is finite and will run out of funds at some point? The approach taken with Cardano is to build into the protocol a self-sustaining treasury that is funded by initial token supply distribution and ongoing transaction fees. Equally, if not more important, is the question of who decides and how the funds are spent. This falls into the Governance phase in Cardano, which Charles indicates will be the hardest of all the phases in Cardano. The concept is that Ada holders can vote on treasury spending along with governance actions on features or improvements to the protocol over time.

# [The Blockchain Trilemma](#toc.xhtml#s12a)

The Blockchain Trilemma refers to a widely held belief that decentralized networks can only provide two of the three benefits at any given time concerning decentralization, security, and scalability.[^(17)](#c01.xhtml#ftn17)

![](OEBPS/images/Figure-1.5.jpg)

**Figure 1.5:** Blockchain Trilemma

*   **Decentralization:** Creating a blockchain that avoids a central point of control.
*   **Scalability**: The blockchain must be able to handle an increasing number of users and transactions.
*   **Security**: A blockchain must operate as expected, and defend itself from attacks, bugs, and other unforeseen issues.[^(18)](#c01.xhtml#ftn18)

Cardano aims to address each of these dimensions using the following approaches:

*   Promote decentralization by ensuring that a stake pool securing the network can be run with ordinary hardware and a typical internet connection.
*   Address scalability with side chains, cryptographic roll-ups, and parallelism (pipelining), increasing the speed at which transactions are processed**.**
*   For high-assurance software and security, use a scientific approach, including a peer review process and formal verification of the Ouroboros Proof-of-Stake protocol**.**

# [Tokenomics](#toc.xhtml#s13a)

The last topic in the chapter is a brief review of tokenomics. A cryptocurrency token is critical in establishing value for a cryptocurrency ecosystem. This is important because running and supporting a network will take real-world resources and costs. Therefore, it is essential to understand the initial token distribution and monetary policy, such as the maximum supply and inflation rate, and how they influence price and market capitalization. Finally, as with the stock market, price and value are frequently misaligned. So, be cautious when evaluating an ecosystem based on the price of the cryptocurrency token. The price may have less to do with the utility or value of that ecosystem and more to do with price manipulation and market sentiment.

# [Token Allocation](#toc.xhtml#s14a)

Cardano’s native token is Ada, which currently has a circulating supply of 35,125,959,544 ADA and a maximum supply of 45,000,000,000 ADA.[^(19)](#c01.xhtml#ftn19) The Cardano ICO was completed between October 2015 and January 2017,[^(20)](#c01.xhtml#ftn20) with the distribution shown in *[Figure 1.6](#c01.xhtml#fig1_6)*.

![](OEBPS/images/Figure-1.6.jpg)

**Figure 1.6:** Initial Token Distribution

There are three founding entities of Cardano:[^(21)](#c01.xhtml#ftn21)

*   **IOHK (IOG)** is a research and engineering company and venture studio that builds blockchain and Web3 products to empower everyone, everywhere.[^(22)](#c01.xhtml#ftn22)
*   **Emurgo** is a for-profit arm that develops, supports, and incubates commercial opportunities and helps integrate businesses into the Cardano blockchain system.
*   **Cardano Foundation** is an independent, Swiss-based not-for-profit organization that promotes and advances the Cardano platform for financial and social systems.

# [Token Distribution](#toc.xhtml#s15a)

Since there is a maximum supply of Ada, we can see the token distribution at any given time. This is helpful for comparison with other cryptocurrencies because a high allocation of a token not in the circulating supply means there may be downward pressure on the price when the token is released to the public.

![](OEBPS/images/Figure-1.7.jpg)

**Figure 1.7:** Ada Token Distribution[^(23)](#c01.xhtml#ftn23)

The **reserve** is the amount of Ada used for **staking** rewards and funding the treasury, as shown in *[Figure 1.7](#c01.xhtml#fig1_7)*. The treasury pays for ecosystem improvements and maintenance. Proof-of-stake networks use staking to allow users to stake their Ada to help secure the network. In return, they receive rewards proportional to the amount of Ada a user stakes vs. all Ada staked in the network. Staking rewards and treasury funding also include transaction fees generated from network activity.

# [Token Allocation Comparison](#toc.xhtml#s16a)

*[Figure 1.8](#c01.xhtml#fig1_8)* compares the initial token allocation of the top cryptocurrencies by market capitalization, as of September 27th, 2023. Interestingly, the amount of initial insider + foundation allocation has an upward trend as cryptocurrencies launch over time.

![](OEBPS/images/Figure-1.8.jpg)

**Figure 1.8:** Top 10 Crypto Market Cap Initial Token Allocations[^(24)](#c01.xhtml#ftn24)

# [Inflation Rate](#toc.xhtml#s17a)

The last metric we will look at is the Cardano inflation rate of 0.3%.[^(25)](#c01.xhtml#ftn25) It is the amount of Ada being released from the reserve into the active supply through staking and funding the treasury. The inflation rate for Cardano is similar to that of Bitcoin, which starts out at the highest amount at launch and then exponentially reduces over time, as shown in *[Figure 1.9](#c01.xhtml#fig1_9)*.

![](OEBPS/images/Figure-1.9.jpg)

**Figure 1.9:** Cardano Inflation Rate

# [Cardano Roadmap](#toc.xhtml#s18a)

The Cardano roadmap has been organized into five themes or phases: Byron, Shelley, Goguen, Basho, and Voltaire.[^(26)](#c01.xhtml#ftn26) Each theme is focused on a set of capabilities that will be delivered across multiple code releases.[^(27)](#c01.xhtml#ftn27) Each development theme has one or more eras with a specific set of ledger rules, as shown in *[Tables 1.1](#c01.xhtml#tab1_1)* and *[1.2](#c01.xhtml#tab1_2)*.

| **Phase** || **Theme** || **Ledger Era** || **Description** |
| --- | --- | --- | --- |
| Byron || Foundation || Byron || The first version of a federated Cardano blockchain using the Ouroboros Proof-of-Stake protocol[^(28)](#c01.xhtml#ftn28) |
| Shelley || Decentralization || Shelley || The roll-out of upgrades improving decentralization and introducing staking delegation and rewards[^(29)](#c01.xhtml#ftn29) |
| Goguen || Smart Contracts || Allegra || Introduced token locking support |
|  ||  || Mary || Enabled native tokens and multi-assets |
|  ||  || Alonzo || Launched Smart Contract capability |
|  ||  || Babbage || Implemented features such as inline datums, reference scripts, and reference inputs |
| Basho || Scaling || N/A || Improve scalability and interoperability of the Cardano network[^(30)](#c01.xhtml#ftn30) |
| Voltaire || Governance || Conway || Allow the Cardano blockchain to become a self-sustaining system with network participants using their staked Ada and voting rights to influence the future development of the network[^(31)](#c01.xhtml#ftn31) |

**Table 1.1:** Cardano Roadmap[^(32)](#c01.xhtml#ftn32)

| **Date** || **Phase** || **Era** || **Epoch Number** || **Consensus Mechanism** |
| --- | --- | --- | --- | --- |
| 2017/09 || Byron || Byron || 0 || Ouroboros Classic |
| 2020/02 || Byron || Byron || 176 || Ouroboros BFT |
| 2020/07 || Shelley || Shelley || 208 || Ouroboros Praos |
| 2020/12 || Goguen || Allegra || 236 || Ouroboros Praos |
| 2021/03 || Goguen || Mary || 251 || Ouroboros Praos |
| 2021/09 || Goguen || Alonzo || 290 || Ouroboros Praos |
| 2021/10 || Goguen || Alonzo || 298 || Ouroboros Praos |
| 2022/09 || Goguen || Babbage || 365 || Ouroboros Praos |
| 2023/02 || Goguen || Babbage || 394 || Ouroboros Praos |

**Table 1.2:** Cardano Timeline[^(33)](#c01.xhtml#ftn33)

# [Blockchain Use Cases](#toc.xhtml#s19a)

To wrap up this introductory chapter, it is helpful to understand some of the blockchain use cases that demonstrate the potential of blockchain technology:

*   **Capital Markets**: more efficient flow of capital[^(34)](#c01.xhtml#ftn34)
*   **Tokenization**: representing assets such as gold, stocks, bonds, property, or fiat currencies
*   **Rewards:** the ability to use rewards or points to incentivize behavior
*   **Decentralized Exchange (DEX)**: non-custodial exchanges for asset and derivative swaps
*   **Marketplaces**: to buy and sell tokenized assets
*   **Financial Products**: such as lending and borrowing
*   **Identity Systems**: Self-Sovereign Identity (**SSI)** solutions
*   **Insurance**: using smart contracts and data feeds for claim processing
*   **Media and Entertainment**: track and monetize the life cycle of authentic digital content and distribution[^(35)](#c01.xhtml#ftn35)
*   **Decentralized Storage:** leverage token incentivization models for peer-to-peer decentralized storage
*   **Decentralized Autonomous Organizations (DAO):** for governance and voting

# [Conclusion](#toc.xhtml#s20a)

We should now have a high-level understanding of the evolution of blockchain technology, from the origins of distributed ledgers to the famous Whiteboard Video by Charles Hoskinson, encapsulating the purpose and goals for Cardano. We introduced the Bitcoin and Ethereum whitepapers and will examine both Proof-of-Work and Proof-of-Stake consensus models in more detail in the next chapter. Additionally, we reviewed fundamental blockchain concepts such as the Blockchain Trilemma, tokenomics, Cardano roadmap, and blockchain use cases. In the next chapter, we will take a deeper technical dive into cryptography and consensus algorithms and explore how they make a blockchain secure.

# [Points to Remember](#toc.xhtml#s21a)

*   Networks can be either centralized or decentralized.
*   The difficulty of a decentralized network is that it must not have a central authority.
*   A Byzantine fault is where a network node is either unavailable or trying to harm the network.
*   A network uses a consensus algorithm to agree on the correct state of the network.
*   A 51% attack occurs when a single entity controls the majority of nodes in a decentralized ledger network.
*   The Bitcoin whitepaper solved two problems at the same time: 
    *   Provided a simple and efficient consensus algorithm.
    *   Anyone can participate in the consensus algorithm, eliminating the need for a central authority.
*   The Ethereum whitepaper introduced the concept of Turing-complete scripts that can access the ledger’s global state.
*   Cardano is considered a third-generation blockchain with the goals of addressing scalability, interoperability, and sustainability.
*   The price and value of a token are frequently misaligned, so when evaluating a cryptocurrency, it is important to consider fundamental principles such as decentralization, security, and scalability.
*   Cardano has five development themes or phases: Byron, Shelley, Goguen, Basho, and Voltaire.

# [Multiple Choice Questions](#toc.xhtml#s22a)

1.  What kind of network does not need central authority? 
    1.  Centralized
    2.  Decentralized
    3.  Distributed
    4.  Anonymous
2.  What innovative concept did Wei Dai publish that Bitcoin uses today? 
    1.  Computation work by solving puzzles
    2.  Computation work by CPU power
    3.  Computation work by network power
    4.  Computation work by consensus
3.  Why was Hal Finney’s “*reusable proofs of work*” not widely adopted? 
    1.  It was based on Proof-of-Work (POW)
    2.  It was not decentralized
    3.  Relied on a trusted back-end
    4.  Insecure cryptography
4.  Bitcoin’s Proof-of-Work was innovative because it was: 
    1.  A time-based consensus algorithm
    2.  A hash-based consensus protocol
    3.  A time- and hash-based consensus protocol
    4.  An efficient and open consensus protocol
5.  Why Turing-complete scripts were not used in Bitcoin? 
    1.  There was no suitable computer language to write it at the time
    2.  There was a risk of an infinite loop
    3.  It needed to be a functional programming language
    4.  Bitcoin does not use scripts
6.  What are the three key pain points of the first- and second-generation blockchains? 
    1.  Scalability, Interoperability, Sustainability
    2.  Scalability, Decentralization, Sustainability
    3.  Decentralization, Scalability, Consensus
    4.  Sustainability, Consensus, Programmability
7.  What are the three dimensions of the Blockchain Trilemma? 
    1.  Security, Consensus, Decentralization
    2.  Programmability, Security, Consensus
    3.  Decentralization, Scalability, Security
    4.  Security, Scalability, Programmability

# [Answers](#toc.xhtml#s23a)

1.  b
2.  a
3.  c
4.  d
5.  b
6.  a
7.  c

# [Questions](#toc.xhtml#s24a)

1.  What problems are decentralized ledgers trying to solve?
2.  Why is decentralization so crucial to a consensus protocol?
3.  What is a Byzantine fault and how to mitigate it?
4.  What was the motivation for the Bitcoin whitepaper?
5.  Why did Vitalik Buterin write the Ethereum whitepaper?
6.  What are the goals of Cardano?
7.  Why is tokenomics important?

# [Key Terms](#toc.xhtml#s25a)

*   **Attribution:** Identity of senders and receivers.
*   **BFT:** Byzantine fault-tolerant
*   **CFT:** Crash fault-tolerant
*   **Compliance:** KYC and anti-money laundering.
*   **Consensus:** The ability of network nodes to agree on the network state.
*   **Decentralized**: A network that does not have a central authority.
*   **Metadata:** The story behind a transaction.
*   **Reserve:** The amount of cryptocurrency used for staking rewards over time.
*   **Scalable**: The ability of a blockchain system to scale network transactions.
*   **Secure**: The ability of a blockchain to remain trustworthy.
*   **Attribution**: Identity of senders and receivers.
*   **Staking**: Using Ada to help secure the Cardano blockchain and receive Ada rewards.
*   **Treasury**: The amount of Ada that is used for maintenance and upgrades.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c01.xhtml#ftn1a) Lyn Alden, “Broken Money,” 1-2.

[²](#c01.xhtml#ftn2a) Stuart Haber et al., “How to Time-Stamp a Digital Document.”

[³](#c01.xhtml#ftn3a) Leslie Lampor et al., “The Byzantine Generals Problem.”

[⁴](#c01.xhtml#ftn4a) David Mazieres et al., “Building Secure File Systems Out of Byzantine Storage.”

[⁵](#c01.xhtml#ftn5a) Wei Dai, “b-money.”

[⁶](#c01.xhtml#ftn6a) Hal Finney, “RPOW - Reusable Proofs of Work.”

[⁷](#c01.xhtml#ftn7a) Vitalik Buterin, “A Next-Generation Smart Contract and Decentralized Application Platform,” 4.

[⁸](#c01.xhtml#ftn8a) Vitalik Buterin, “A Next-Generation Smart Contract and Decentralized Application Platform,” 4.

[⁹](#c01.xhtml#ftn9a) Satoshi Nakamoto, “Bitcoin: A Peer-to-Peer Electronic Cash System,” 8.

[^(10)](#c01.xhtml#ftn10a) Satoshi Nakamoto, “Bitcoin: A Peer-to-Peer Electronic Cash System,” 1.

[^(11)](#c01.xhtml#ftn11a) Vitalik Buterin, “A Next-Generation Smart Contract and Decentralized Application Platform,” 4.

[^(12)](#c01.xhtml#ftn12a) Vitalik Buterin, “A Next-Generation Smart Contract and Decentralized Application Platform,” 4.

[^(13)](#c01.xhtml#ftn13a) Vitalik Buterin, “A Next-Generation Smart Contract and Decentralized Application Platform,” 13.

[^(14)](#c01.xhtml#ftn14a) Vitalik Buterin, “A Next-Generation Smart Contract and Decentralized Application Platform,” 13.

[^(15)](#c01.xhtml#ftn15a) Vitalik Buterin, “A Next-Generation Smart Contract and Decentralized Application Platform,” 13.

[^(16)](#c01.xhtml#ftn16a) Charles Hoskinson, “Cardano whiteboard; overview with Charles Hoskinson.”

[^(17)](#c01.xhtml#ftn17a) Cryptopedia, “The Blockchain Trilemma: Fast, Secure, and Scalable Networks.”

[^(18)](#c01.xhtml#ftn18a) [https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3](https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3)

[^(19)](#c01.xhtml#ftn19a) [https://coinmarketcap.com/currencies/cardano/#About](https://coinmarketcap.com/currencies/cardano/#About)

[^(20)](#c01.xhtml#ftn20a) [https://cardano.org/genesis/#audit](https://cardano.org/genesis/#audit)

[^(21)](#c01.xhtml#ftn21a) [https://cardano.org/partners/](https://cardano.org/partners/)

[^(22)](#c01.xhtml#ftn22a) [https://cardano.org/partners?tab=iog](https://cardano.org/partners?tab=iog)

[^(23)](#c01.xhtml#ftn23a) cardanians.io, “There is 1.23B ADA in Cardano’s.”

[^(24)](#c01.xhtml#ftn24a) Source data from:

[https://www.investopedia.com/what-is-xrp-6362550#toc-xrp-ledger-and-xrp](https://www.investopedia.com/what-is-xrp-6362550#toc-xrp-ledger-and-xrp)

[https://coinmarketcap.com/currencies/dogecoin/#About](https://coinmarketcap.com/currencies/dogecoin/#About)

[https://www.coingecko.com/en/coins/ethereum/tokenomics](https://www.coingecko.com/en/coins/ethereum/tokenomics)

[https://coinmarketcap.com/currencies/cardano/#About](https://coinmarketcap.com/currencies/cardano/#About)

[https://www.coingecko.com/en/coins/polkadot/tokenomics](https://www.coingecko.com/en/coins/polkadot/tokenomics)

[https://coinmarketcap.com/currencies/polygon/#About](https://coinmarketcap.com/currencies/polygon/#About)

[https://coinmarketcap.com/currencies/bnb/#About](https://coinmarketcap.com/currencies/bnb/#About)

[https://coinmarketcap.com/currencies/toncoin/](https://coinmarketcap.com/currencies/toncoin/)

[https://coinmarketcap.com/currencies/solana/#About](https://coinmarketcap.com/currencies/solana/#About)

[^(25)](#c01.xhtml#ftn25a) [https://docs.cardano.org/explore-cardano/monetary-policy/](https://docs.cardano.org/explore-cardano/monetary-policy/)

[^(26)](#c01.xhtml#ftn26a) [https://docs.cardano.org/about-cardano/evolution/eras-and-phases/](https://docs.cardano.org/about-cardano/evolution/eras-and-phases/)

[^(27)](#c01.xhtml#ftn27a) [https://roadmap.cardano.org/en/](https://roadmap.cardano.org/en/)

[^(28)](#c01.xhtml#ftn28a) [https://roadmap.cardano.org/en/byron/](https://roadmap.cardano.org/en/byron/)

[^(29)](#c01.xhtml#ftn29a) [https://roadmap.cardano.org/en/shelley/](https://roadmap.cardano.org/en/shelley/)

[^(30)](#c01.xhtml#ftn30a) [https://roadmap.cardano.org/en/basho/](https://roadmap.cardano.org/en/basho/)

[^(31)](#c01.xhtml#ftn31a) [https://roadmap.cardano.org/en/voltaire/](https://roadmap.cardano.org/en/voltaire/)

[^(32)](#c01.xhtml#ftn32a) [https://docs.cardano.org/explore-cardano/eras-and-phases/](https://docs.cardano.org/explore-cardano/eras-and-phases/)

[^(33)](#c01.xhtml#ftn33a) [https://github.com/cardano-foundation/CIPs/blob/master/CIP-0059/feature-table.md](https://github.com/cardano-foundation/CIPs/blob/master/CIP-0059/feature-table.md)

[^(34)](#c01.xhtml#ftn34a) [https://consensys.io/blockchain-use-cases/capital-markets](https://consensys.io/blockchain-use-cases/capital-markets)

[^(35)](#c01.xhtml#ftn35a) [https://consensys.io/blockchain-use-cases/media-and-entertainment](https://consensys.io/blockchain-use-cases/media-and-entertainment)

# [CHAPTER 2](#toc.xhtml#c02)

# [Cryptography and Consensus Algorithms Overview](#toc.xhtml#c02)

# [Introduction](#toc.xhtml#s26a)

In this chapter, we will introduce cryptography and cryptographic hashes. We will show how cryptographic hashes are made and used in blockchain technology. Next, we will explore the Proof-of-Work consensus protocol used by the Bitcoin blockchain. We will show how a prover and verifier work together to secure a blockchain. Next, we will examine Proof-of-Stake and its benefits over Proof-of-Work. Finally, we will review Ouroboros, Cardano’s Proof-of-Stake consensus protocol.

# [Structure](#toc.xhtml#s27a)

In this chapter, we will discuss the following topics:

*   Cryptography 
    *   Public Key Encryption
    *   Hashes
*   Digital Signatures 
    *   Chain of Ownership
*   Proof-of-Work 
    *   Mining
*   Proof-of-Stake 
    *   Probabilistic Finality (Chain-based)
    *   Absolute Finality (PBFT)
*   Ouroboros 
    *   Ouroboros Classic
    *   Ouroboros BFT
    *   Ouroboros Praos
    *   Ouroboros Genesis
    *   Ouroboros Crypsinous
    *   Ouroboros Chronos
    *   Ouroboros Protocol Lifecycle

# [Cryptography](#toc.xhtml#s28a)

“*The first recorded use of cryptography for correspondence was by the Spartans, who, as early as 400 BC, employed a cipher device*”[¹](#c02.xhtml#ftn1) for secret communication. A cipher is any method of transforming a message to conceal its meaning.[²](#c02.xhtml#ftn2) Before the mid-1970s, all cipher systems used symmetric key algorithms, in which the same cryptographic key is used with the underlying algorithm by both the sender and the recipient, who must both keep it secret.[³](#c02.xhtml#ftn3) The challenge with **symmetric** encryption is that the secret key must be transmitted securely beforehand, which does not scale when there are many keys to manage or a prior secure channel does not exist.[⁴](#c02.xhtml#ftn4) This limitation was addressed by **asymmetric** encryption, used in **public key encryption** and **digital signatures**.

# [Public Key Encryption](#toc.xhtml#s29a)

The first step in the process of using public key encryption is to generate a pair of public and private keys using a mathematically based one-way cryptographic algorithm.[⁵](#c02.xhtml#ftn5) The classic cryptography example refers to Alice trying to send an encrypted message to Bob in *[Figure 2.1](#c02.xhtml#fig2_1).* In this case, Alice needs to use Bob’s public key to encrypt the message. The message is unreadable to everyone except for Bob, who holds the private key. When Bob receives the encrypted message, he decrypts it using his private key and reads the original message sent by Alice.

![](OEBPS/images/Figure-2.1.jpg)

**Figure 2.1:** Public Key Encryption

# [Hashes](#toc.xhtml#s30a)

Cryptographic hashes are generated using a mathematical function that takes an input of arbitrary size and generates a fixed-length output.[⁶](#c02.xhtml#ftn6) This is known as a one-way hash and cannot be decoded to reveal the original contents of the input. The generated output will always be the same for the same set of inputs. If there is even the smallest change in the inputs, the generated hash will be entirely different, known as the avalanche effect.[⁷](#c02.xhtml#ftn7) The avalanche effect ensures collision resistance and tamper detection, which is used extensively in blockchains.

The BLAKE2b-256 cryptographic hash algorithm is used in Cardano to generate an address,[⁸](#c02.xhtml#ftn8) and BLAKE2b-224 is used to generate public key hashes. Hash functions are also used in blockchains to generate a hash of a block containing the list of transactions. This helps check and ensure immutability since any change in the transactions contained in a block will change the block hash.

# [Digital Signatures](#toc.xhtml#s31a)

**Digital signatures** provide a way for Alice to sign a message so that the signature can be later verified by anyone using Alice’s public key.[⁹](#c02.xhtml#ftn9) The message is not encrypted like public key encryption, instead, a digital signature proves that Alice and only Alice signed this message. In the context of blockchain, the message is a transaction and Alice is the owner of a blockchain address. When a transaction is signed by Alice’s private key, anyone else on the blockchain can verify by using Alice’s public key, as shown in *[Figure 2.2](#c02.xhtml#fig2_2)*.

![](OEBPS/images/Figure-2.2.jpg)

**Figure 2.2:** Digital Signatures

The first commonly used digital signature was Rivest-Shamir-Asleman (RSA), created in 1977, which uses the property that factoring two large primes is difficult. In 1991, the Digital Signature Algorithm (DSA) was created, leveraging the fact that solving the discrete log problem (x ^ y = z) is difficult. Given x and z, solving for y is difficult when y is a large enough number. An elliptic curve signature algorithm was added to DSA, creating the Elliptic Curve Digital Signature Algorithm (ECDSA), which has a smaller key size and faster operations.[^(10)](#c02.xhtml#ftn10) Cardano uses the Edwards-curve Digital Signature Algorithm (EdDSA), which has the following benefits[^(11)](#c02.xhtml#ftn11):

*   Fast signing and verification
*   High level of security
*   Small signatures
*   Small keys

*[Table 2.1](#c02.xhtml#tab2_1)* summarizes the different signature algorithms used in Bitcoin, Ethereum, and Cardano:

| **Blockchain** || **Signing Algorithm** || **Elliptic Curve** || **Hash Function** |
| --- | --- | --- | --- |
| Bitcoin || ECDSA || Secp256k1 || SHA-256 |
| Ethereum || ECDSA || Secp256k1 || Keccak-256 |
| Cardano || EdDSA || Curve25519 || BLAKE2b |

**Table 2.1:** Digital signatures[^(12)](#c02.xhtml#ftn12)

# [Chain of Ownership](#toc.xhtml#s32a)

An electronic coin, as defined in the Bitcoin whitepaper, is a chain of digital signatures.[^(13)](#c02.xhtml#ftn13) A Bitcoin is transferred digitally by signing the previous transaction’s hash and the next owner’s public key. A transaction will only be approved if the signature matches the public key included in the previous transaction. By linking these together, the **chain of ownership** can be verified, as shown in *[Figure 2.3](#c02.xhtml#fig2_3)*.

![](OEBPS/images/Figure-2.3.jpg)

**Figure 2.3:** Chain of Ownership[^(14)](#c02.xhtml#ftn14)

# [Proof-of-Work (PoW)](#toc.xhtml#s33a)

In the Bitcoin whitepaper, the double-spend problem is where Bob tries to create two transactions to spend the same amount twice. To solve this issue, a timestamp or timeline is introduced. Each block hash is linked to the previous block hash, creating a chain of blocks and ordering transactions, as shown in *[Figure 2.4](#c02.xhtml#fig2_4)*. The ledger can now confirm if a transaction is trying to double-spend outputs that have already been spent and reject it accordingly.

To help regulate the frequency of block production, a nonce is used and incremented to find a block hash with a required number of zero bits. The Bitcoin network monitors the pace of block production, and if blocks are produced too fast, the number of required zero bits increases. Conversely, if the number of blocks being produced takes too long, the number of required zero bits decreases. The adjustment of the required number of zero bits is also known as **difficulty**.[^(15)](#c02.xhtml#ftn15) The level of CPU effort increases exponentially as the **difficulty** increases. Because the blocks are chained together, undoing a previous transaction requires changing all the previous blocks, which becomes practically impossible as more blocks are confirmed by the network.

![](OEBPS/images/Figure-2.4.jpg)

**Figure 2.4:** Proof-of-Work

# [Mining](#toc.xhtml#s34a)

The last issue to solve is to provide an incentive for creating new blocks called mining and encourage miners to be honest and not attack the network. This is accomplished by distributing new Bitcoins in the first transaction in each block to the miner who created the block. The number of new Bitcoins created decreases exponentially over time, which controls Bitcoin’s inflation rate. Additionally, if the output value of the transaction is less than the input value, this is considered a transaction fee and awarded to the miner.[^(16)](#c02.xhtml#ftn16) The new Bitcoins plus the transaction fee will make it more profitable for the miner to act honestly rather than try to subvert the network with an invalid block.

# [Proof-of-Stake (PoS)](#toc.xhtml#s35a)

With the growing popularity of Bitcoin, the difficulty has increased exponentially. As a result, the **PoW** consensus protocol requires a lot of energy for miners to produce a block. **PoS**, on the other hand, is significantly more energy efficient by selecting block producers randomly and proportionally to the amount of Ada they have staked on the network. Stakeholders can delegate their stake to a Stake Pool Operator (**SPO**) to aggregate Stake together and increase the chances for block production. In a PoS protocol, there is no need to generate computationally intensive puzzles; meanwhile, the security and permissionless properties are still comparable to **PoW**.[^(17)](#c02.xhtml#ftn17)

**PoS**, however, introduces a different threat vector for determining the block (slot) leader. To achieve a fair randomized election among stakeholders, **entropy** must be introduced into the system and may be prone to manipulation by an adversary.[^(18)](#c02.xhtml#ftn18) Ouroboros **PoS** protocol mitigates this risk by using an entropy parameter that represents something unpredictable outside the Cardano ecosystem.[^(19)](#c02.xhtml#ftn19) “*The value of this parameter is calculated based on events that could not have been known in advance, or that anyone could have had insider information about*.”[^(20)](#c02.xhtml#ftn20)

We will look into the Ouroboros protocol in more detail in the next section and will complete the **PoS** overview by examining the two major categories of **PoS** protocols:[^(21)](#c02.xhtml#ftn21)

*   **Probabilistic Finality** (Chain-based)
*   **Absolute Finality** (PBFT)

# [Probabilistic Finality (Chain-based)](#toc.xhtml#s36a)

**Probabilistic** or chain-based finality attempts to simulate the **PoW** Nakamoto consensus protocol used in Bitcoin. As more blocks are linked together, they form the longest chain and become probabilistically final.[^(22)](#c02.xhtml#ftn22) Typically, waiting until 6 blocks have been linked together is sufficient for probabilistic finality, with a high likelihood that a transaction will not be reverted or rolled back. One of the key advantages of a probabilistic finality mechanism is that it prioritizes network **availability** for continuous and permissionless access.

# [Absolute Finality (PBFT)](#toc.xhtml#s37a)

In an **Absolute Finality** or Practical Byzantine Fault Tolerant (**PBFT**) protocol, a validator is randomly chosen to propose a new block. The validators then vote on the inclusion of this new block, and consensus is achieved when the required number of validators agree on accepting a new block.[^(23)](#c02.xhtml#ftn23) Additionally, **PoS** blockchains like Ethereum implement an economic penalty that makes it prohibitively expensive for validators who are unavailable or act maliciously against the network. By using **Absolute** and **Economic Finality**, the protocol prioritizes the **consistency** of the network and would halt the network rather than accept an invalid transaction for any length of time.[^(24)](#c02.xhtml#ftn24)

# [Ouroboros Protocol](#toc.xhtml#s38a)

Ouroboros is the first provably secure **PoS** protocol and the first blockchain protocol based on peer-reviewed research.[^(25)](#c02.xhtml#ftn25) It consists of a family of PoS protocols, including:

*   Ouroboros Classic
*   Ouroboros BFT
*   Ouroboros Praos
*   Ouroboros Genesis
*   Ouroboros Crypsinous
*   Ouroboros Chronos

# [Ouroboros Classic](#toc.xhtml#s39a)

Ouroboros Classic was the first Ouroboros protocol published in July 2017.[^(26)](#c02.xhtml#ftn26) The paper defined the protocol as an energy-efficient rival to **PoW**, introduced the mathematical framework to analyze PoS, and introduced a novel incentive mechanism to reward participants in a PoS setting.[^(27)](#c02.xhtml#ftn27) What distinguishes Ouroboros from other blockchain protocols is its ability to generate unbiased randomness in its leader selection algorithm with security assurances.[^(28)](#c02.xhtml#ftn28) Let’s examine this in more detail.

“*Ouroboros divides time on Cardano into epochs, where each epoch is divided into slots. A slot is a short period of time in which a block can be created, and grouping slots into epochs is central to adjusting the leader election process to the dynamically changing stake distribution. A slot leader is elected for each slot, responsible for adding a block to the chain and passing it to the next slot leader. To protect against adversarial attempts to subvert the protocol, each new slot leader must consider the last few blocks of the received chain as transient: only the chain that precedes the prespecified number of transient blocks is considered settled*.”[^(29)](#c02.xhtml#ftn29)

# [Ouroboros BFT](#toc.xhtml#s40a)

The Ouroboros Byzantine Fault Tolerance (**BFT**) was a simplified protocol[^(30)](#c02.xhtml#ftn30) based on Ouroboros Classic and was used primarily to help with one of the most significant milestones in Cardano known as the Shelly release. It transitioned the network to a federated model to avoid requiring all nodes to be online all the time.[^(31)](#c02.xhtml#ftn31)

# [Ouroboros Praos](#toc.xhtml#s41a)

Praos introduces a verifiable random function (**VRF**) on the current timestamp and a nonce for a specific epoch.[^(32)](#c02.xhtml#ftn32) Given a private key and an input, a **VRF** outputs a pseudo-random number and a proof.[^(33)](#c02.xhtml#ftn33) The corresponding public key can verify the proof and random number. Additionally, this approach prevents anyone except the proposed slot leader from knowing the slot leader for a specific slot in advance. This is important to avoid **DDoS** or targeted attacks, where a slot leader is publicly known in advance.[^(34)](#c02.xhtml#ftn34)

# [Ouroboros Genesis](#toc.xhtml#s42a)

The Bitcoin **PoW** consensus protocol has the advantage that any participant can join the network and participate using only the Genesis block. This is a very important feature of any blockchain, as it does not rely on any trusted notion or checkpoints of the correct state of the network. Ouroboros Genesis addresses this limitation with the Ouroboros **PoS** protocols by using a novel chain selection rule that allows new or offline participants to join the network using only the genesis block.[^(35)](#c02.xhtml#ftn35) This approach is called “*bootstrapping from genesis*,” and the Ouroboros Genesis paper proves that it can still retain the prior security assurances while using this approach. The paper also provides proof of the protocol’s Universal Composability, showing that it retains its security properties even when used in different protocol configurations.[^(36)](#c02.xhtml#ftn36)

# [Ouroboros Crypsinous](#toc.xhtml#s43a)

Ouroboros Crypsinous is the first formally analyzed privacy-preserving PoS blockchain protocol.[^(37)](#c02.xhtml#ftn37) Using SNARKs and key-private forward secure encryption, the paper uses a novel coin evolution technique to prove the network is secure against adaptive attacks.[^(38)](#c02.xhtml#ftn38) This protocol is not intended to be implemented on the main Cardano settlement layer but may be used in a side chain such as Midnight, a privacy-preserving blockchain.

# [Ouroboros Chronos](#toc.xhtml#s44a)

Ouroboros Chronos demonstrates how blockchain protocols can synchronize clocks securely via a novel time synchronization mechanism, thereby becoming independent of external time services.[^(39)](#c02.xhtml#ftn39) The paper aims to make the ledger more resistant to attacks that target time information.[^(40)](#c02.xhtml#ftn40)

# [Ouroboros Protocol Lifecycle](#toc.xhtml#s45a)

Let’s walk through the Ouroboros protocol lifecycle to provide a step-by-step example of how everything fits together.

# [Time](#toc.xhtml#s46a)

The first block in the Cardano blockchain is the genesis block, which is the beginning of time from a blockchain perspective. Cardano uses the concept of slots, which occur approximately every second, where at most one block can be created. The expected block production frequency is 0.05, meaning that, on average, a block will be produced every 20 seconds.[^(41)](#c02.xhtml#ftn41) Only a slot leader can create a block for a given slot. There are precisely 432,000 slots in every epoch, equivalent to every 5 days.

# [Register](#toc.xhtml#s47a)

The first step in participating in the Cardano network is registering the stake key associated with the Ada to be staked. This typically refers to the registration of Ada to a specific Stake Pool Operator (**SPO)**. The amount staked is used to calculate rewards and distribute proportionally back to the staking addresses. The **SPO** will handle (among other things) the stake pool registration process, as shown in *[Figure 2.5](#c02.xhtml#fig2_5)*:

1.  Synchronize with the network ledger.
2.  Obtain the current slot.
3.  Obtain the global random oracle.

# [Staking](#toc.xhtml#s48a)

1.  At the start of each epoch, each stake pool operator queries the blockchain to obtain the stake distribution of a previous block, which was two epochs ago.
2.  Using a **VRF** generated from the first ⅔ slots in the previous epoch, the stakeholder with their private key can produce an output in the current epoch to determine if they can be a slot leader.[^(42)](#c02.xhtml#ftn42)
3.  If the **VRF** output value is below a certain threshold, they can become the slot leader for that block.
4.  Slot Leader Responsibilities:[^(43)](#c02.xhtml#ftn43) 
    1.  Assemble the transactions that should be included in the block.
    2.  Include in the block the random value (v) and proof (π) obtained from the VRF output.
    3.  Generate a new private key and delete the old one so it is impossible to forge signatures with the old private key.
    4.  Broadcast the new block to the network.
5.  The rewards are calculated at the end of the epoch and then distributed to the reward addresses in the next block.
    
    ![](OEBPS/images/Figure-2.5.jpg)
    
    **Figure 2.5:** Ouroboros Protocol Lifecycle
    

# [Conclusion](#toc.xhtml#s49a)

This chapter introduced cryptography with a focus on public key hash algorithms. We saw how this extended to a concept called digital signatures, which underpins cryptocurrencies today. By linking digital signatures, a blockchain can create proof-of-ownership for the movement of a digital coin like Bitcoin. We looked deeper at Proof-of-Work and how mining a block incentivizes miners to be honest and prevent network attacks. We then looked at the energy-efficient Proof-of-Stake and how to mitigate the risk associated with predicting random number generation, along with the differences and tradeoffs between Probabilistic and Absolute Finality. Finally, we reviewed the Ouroboros family of protocols and the current protocol lifecycle on the Cardano Mainnet today. Using our knowledge of cryptography and how **PoS** blockchains work, we will explore how to transfer value using transactions in the next chapter.

# [Points to Remember](#toc.xhtml#s50a)

*   Using public key encryption requires generating a pair of public and private keys.
*   If a transaction is signed by a private key, anyone on the blockchain can verify it using the corresponding public key.
*   Bitcoin is transferred digitally by signing the previous transaction’s hash and including the next owner’s public key.
*   To solve the double-spend problem, a timestamp is included in the hash of each block, and more timestamps are included in the chain of blocks, securing the prior blocks.
*   Bitcoin mining incentivizes honest behavior by distributing new Bitcoins and transaction fees as the first transaction in each block to the miner who created the block.
*   Proof-of-Stake is significantly more energy efficient than Proof-of-Work.
*   Proof-of-Stake selects block producers (validators) randomly and proportionally to the native currency they have staked on the network.
*   Entropy must be introduced into the system to achieve a fair randomized election among Proof-of-Stake stakeholders.
*   With security assurances, Ouroboros can generate unbiased randomness in the protocol’s leader selection algorithm.
*   Probabilistic finality occurs as more blocks are linked, forming the longest chain.
*   Validators vote on including a new block, and the outcome is considered final, achieving Absolute Finality.

# [Multiple Choice Questions](#toc.xhtml#s51a)

1.  What type of encryption does public key cryptography use? 
    1.  Symmetric
    2.  Asymmetric
    3.  Bi-Symmetric
    4.  Anonymous
2.  How do you verify a signature? 
    1.  Use both private and public keys
    2.  Use the private key
    3.  Use the symmetric key
    4.  Use the public key associated with the private key
3.  How did Bitcoin solve the double-spend problem? 
    1.  Used timestamps to order transactions
    2.  Used a distributed ledger to record transactions
    3.  Used cryptography to sign a transaction
    4.  Used blocks to record transactions
4.  Proof-of-Stake is more energy efficient because: 
    1.  Block leader selection is not needed
    2.  Randomness is not needed
    3.  Solving computational puzzles is not needed
    4.  Forming the longest chain is not needed
5.  What risk occurs in both Proof-of-Stake and Proof-of-Work? 
    1.  Centralization
    2.  Randomness Bias
    3.  Plutocracy
    4.  Environmental

# [Answers](#toc.xhtml#s52a)

1.  b
2.  d
3.  a
4.  c
5.  a

# [Questions](#toc.xhtml#s53a)

1.  Why is cryptography important to blockchains?
2.  What problems did the Bitcoin whitepaper solve?
3.  How much more energy efficient is Cardano PoS compared to Bitcoin PoW?
4.  What are the advantages and disadvantages of Absolute Finality?
5.  Why is it essential that Ouroboros is provably secure?
6.  How does Ouroboros ensure the correct chain is chosen when a client joins the network?

# [Key Terms](#toc.xhtml#s54a)

*   **Block:** Contains zero or more transactions.
*   **Chain of Ownership:** Links digital signatures together.
*   **DDos:** Distributed denial of service.
*   **Difficulty:** The increasing rate of computation required to create a block.
*   **Digital Signature:** Signed message using a private key.
*   **Entropy:** The amount of randomness in a system.
*   **Epoch:** A unit of time that contains a fixed number of slots.
*   **Finality:** A state that can be considered final and irreversible.
*   **Mining:** Incentives paid to miners for creating a block.
*   **Public Key Encryption:** Generates a pair of public and private keys.
*   **PoS:** Proof-of-Stake
*   **PoW:** Proof-of-Work
*   **Slot:** Occurs every second and may contain at most one block.
*   **SPO:** Stake Pool Operator
*   **VRF:** Verifiable Random Function

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c02.xhtml#ftn1a) Gustavus J. Simmons, “History of cryptography.”

[²](#c02.xhtml#ftn2a) Encyclopaedia of Britannica, “cipher.”

[³](#c02.xhtml#ftn3a) [https://en.wikipedia.org/wiki/Public-key\_cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)

[⁴](#c02.xhtml#ftn4a) A. Menezes, “Handbook of Applied Cryptography,” 283.

[⁵](#c02.xhtml#ftn5a) A. Menezes, “Handbook of Applied Cryptography,” 286.

[⁶](#c02.xhtml#ftn6a) Prashant P. Pittalia, “A comparative study of hash algorithms in cryptography,” 147.

[⁷](#c02.xhtml#ftn7a) Darshana Upadhyay, et al., “Investigating the Avalanche Effect of Various Cryptographically Secure Hash Functions and Hash-Based Applications,” 112472–112486.

[⁸](#c02.xhtml#ftn8a) [https://docs.cardano.org/learn/cardano-addresses/](https://docs.cardano.org/learn/cardano-addresses/)

[⁹](#c02.xhtml#ftn9a) Shafi Goldwasser, “Chapter 10: Digital signatures” (PDF). Lecture Notes on Cryptography,” 168.

[^(10)](#c02.xhtml#ftn10a) [https://academy.cardanofoundation.org/](https://academy.cardanofoundation.org/), “Different Digital Signature Algorithms.”

[^(11)](#c02.xhtml#ftn11a) Daniel, J. Bernstein, et. al. “High-speed high-security signatures.” J Cryptogr Eng 2, 77–89 (2012).

[^(12)](#c02.xhtml#ftn12a) [https://www.susanka.eu/coins-crypto/](https://www.susanka.eu/coins-crypto/)

[^(13)](#c02.xhtml#ftn13a) Satoshi Nakamoto, “Bitcoin: A Peer-to-Peer Electronic Cash System,” 2.

[^(14)](#c02.xhtml#ftn14a) Satoshi Nakamoto, “Bitcoin: A Peer-to-Peer Electronic Cash System,” 2.

[^(15)](#c02.xhtml#ftn15a) Satoshi Nakamoto, “Bitcoin: A Peer-to-Peer Electronic Cash System.” 2.

[^(16)](#c02.xhtml#ftn16a) Satoshi Nakamoto, “Bitcoin: A Peer-to-Peer Electronic Cash System,” 4.

[^(17)](#c02.xhtml#ftn17a) Aggelos Kiayias, et al., “Ouroboros: A Provably Secure Proof-of-Stake Blockchain Protocol,” 1.

[^(18)](#c02.xhtml#ftn18a) Aggelos Kiayias, et al., “Ouroboros: A Provably Secure Proof-of-Stake Blockchain Protocol,” 1.

[^(19)](#c02.xhtml#ftn19a) [https://docs.cardano.org/explore-cardano/cardano-entropy/](https://docs.cardano.org/explore-cardano/cardano-entropy/)

[^(20)](#c02.xhtml#ftn20a) [https://docs.cardano.org/explore-cardano/cardano-entropy/](https://docs.cardano.org/explore-cardano/cardano-entropy/)

[^(21)](#c02.xhtml#ftn21a) Alexis Gauba, “Finality in Blockchain Consensus.”

[^(22)](#c02.xhtml#ftn22a) Shehar Bano, et al., “SoK: Consensus in the Age of Blockchains,” 2.

[^(23)](#c02.xhtml#ftn23a) Shehar Bano, et al., “SoK: Consensus in the Age of Blockchains,” 4.

[^(24)](#c02.xhtml#ftn24a) Alexis Gauba, “Finality in Blockchain Consensus.”

[^(25)](#c02.xhtml#ftn25a) [https://docs.cardano.org/learn/ouroboros-overview/](https://docs.cardano.org/learn/ouroboros-overview/)

[^(26)](#c02.xhtml#ftn26a) Aggelos Kiayias, et al., “Ouroboros: A Provably Secure Proof-of-Stake Blockchain Protocol,” 1.

[^(27)](#c02.xhtml#ftn27a) Olga Hryniuk, “From Classic to Chronos: the implementations of Ouroboros explained.”

[^(28)](#c02.xhtml#ftn28a) [https://docs.cardano.org/learn/ouroboros-overview/](https://docs.cardano.org/learn/ouroboros-overview/)

[^(29)](#c02.xhtml#ftn29a) Olga Hryniuk, “From Classic to Chronos: the implementations of Ouroboros explained.”

[^(30)](#c02.xhtml#ftn30a) Aggelos Kiayias, et al., “Ouroboros-BFT:A Simple Byzantine Fault Tolerant Consensus Protocol,” 1.

[^(31)](#c02.xhtml#ftn31a) Olga Hryniuk, “From Classic to Chronos: the implementations of Ouroboros explained.”

[^(32)](#c02.xhtml#ftn32a) Bernardo David, et al. “Ouroboros Praos: An adaptively-secure, semi-synchronous proof-of-stake blockchain”

[^(33)](#c02.xhtml#ftn33a) LLFOURN, “Introduction To Ouroboros.”

[^(34)](#c02.xhtml#ftn34a) Peter Gaži, “Presenting Ouroboros at MIT.”

[^(35)](#c02.xhtml#ftn35a) Christian Badertscher, et al., “Ouroboros Genesis: Composable Proof-of-Stake Blockchains with Dynamic Availability,” 1.

[^(36)](#c02.xhtml#ftn36a) Olga Hryniuk, “From Classic to Chronos: the implementations of Ouroboros explained.”

[^(37)](#c02.xhtml#ftn37a) Thomas Kerber, et al., “Ouroboros Crypsinous: Privacy-Preserving Proof-of-Stake,” 1.

[^(38)](#c02.xhtml#ftn38a) Thomas Kerber, “Ouroboros Crypsinous: Privacy-Preserving Proof-of-Stake,” 1.

[^(39)](#c02.xhtml#ftn39a) Olga Hryniuk, “From Classic to Chronos: the implementations of Ouroboros explained.”

[^(40)](#c02.xhtml#ftn40a) Christian Badertscher, et al., “Ouroboros Chronos: Permissionless Clock Synchronization via Proof-of-Stake,” 1.

[^(41)](#c02.xhtml#ftn41a) Arnaud Bailly, “Time handling on Cardano, part 1. About Ouroboros and the importance of determinism.”

[^(42)](#c02.xhtml#ftn42a) Crypto Carlos, “Ourobors protocol. The heart of Cardano.”

[^(43)](#c02.xhtml#ftn43a) [https://developers.cardano.org/docs/operate-a-stake-pool/introduction-to-cardano/](https://developers.cardano.org/docs/operate-a-stake-pool/introduction-to-cardano/)

# [CHAPTER 3](#toc.xhtml#c03)

# [Transactions](#toc.xhtml#c03)

# [Introduction](#toc.xhtml#s55a)

In this chapter, we will first look at Cardano Addresses, how they are built, and the data inside them. Next, we will look at the UTXO architecture and show how transactions are created, along with optional metadata. We will also introduce how Smart Contracts, known as Plutus scripts, are executed and evaluated. We will see how Redeemers pass data into Plutus scripts and how Datums are used for data storage and persistence. Finally, we will look at the transaction Witness Set and how it authorizes the spending of transaction inputs.

# [Structure](#toc.xhtml#s56a)

In this chapter, we will discuss the following topics:

*   Addresses 
    *   Network Tag
    *   Base Address
    *   Enterprise Address
    *   Reward (Staking) Address
*   UTXO 
    *   Transaction Inputs
    *   Transaction Outputs
*   Metadata
*   Plutus Scripts
*   Datum
*   Redeemer
*   Witness Set

# [Addresses](#toc.xhtml#s57a)

A Cardano (Shelly) address is a sequence of bytes encoded using Bech32.[¹](#c03.xhtml#ftn1) There are three types of addresses that you will typically interact with on Cardano:

*   Base Addresses
*   Enterprise Addresses
*   Reward (Stake) Addresses

The structure of a Cardano address is shown in *[Figure 3.1](#c03.xhtml#fig3_1)*:

![](OEBPS/images/Figure-3.1.jpg)

**Figure 3.1:** Cardano Address Structure

The header type indicates what type of address (or payload), and the network tag indicates what network this address is associated with.

# [Network Tag](#toc.xhtml#s58a)

| **Header Bits** || **Network** |
| --- | --- |
| `xxxx0000` || Testnet(s) |
| `xxxx0001` || Mainnet |

**Table 3.1:** Network Tag

# [Base Address](#toc.xhtml#s59a)

A base address is the most common type of address, as shown in *[Table 3.2](#c03.xhtml#tab3_2)*. When the payment part is a `PaymentKeyHash`, the transaction must be signed with the corresponding private key for this address. When the payment part is a `ScriptHash`, a script with a matching hash must be executed and evaluated to true to spend from this address. The delegation part is similar to the payment part but is used to register (and delegate) a staking certificate for Ada that is locked at this address. As we recall from the previous chapter, staking is the mechanism that helps secure a Proof-of-Stake blockchain and receive rewards for doing so.

| **Header Bits** || **Payment Part** || **Delegation Part** |
| --- | --- | --- |
| `0000xxxx` || `PaymentKeyHash` || `StakeKeyHash` |
| `0001xxxx` || `ScriptHash` || `StakeKeyHash` |
| `0010xxxx` || `PaymentKeyHash` || `ScriptHash` |
| `0011xxxx` || `ScriptHash` || `ScriptHash` |

**Table 3.2:** Base Address

# [Enterprise Address](#toc.xhtml#s60a)

An enterprise address is similar to a base address, except there is no delegation part. The header types for enterprise addresses are listed in *[Table 3.3](#c03.xhtml#tab3_3)*.

| **Header Bits** || **Payment Part** || **Delegation Part** |
| --- | --- | --- |
| `0110xxxx` || `PaymentKeyHash` || N/A |
| `0111xxxx` || `ScriptHash` || N/A |

**Table 3.3:** Enterprise Address

# [Reward (Stake) Addresses](#toc.xhtml#s61a)

Reward addresses are used to distribute rewards for staking in the Proof-of-Stake protocol and have the following properties:[²](#c03.xhtml#ftn2)

*   It uses account-style accounting and not UTXO.
*   Account balances are only increased when staking rewards are distributed.
*   To transfer out the Ada locked at a Reward Address, a withdrawal-type transaction is required to release the funds and zero out the balance of the rewards address.
*   A one-to-one relationship exists between a registered staking key and a reward account address.

 
| **Header Bits** || **Stake Reference** |
| --- | --- |
| `1110xxxx` || `StakeKeyHash` |
| `1111xxxx` || `ScriptHash` |

**Table 3.4:** Reward (Stake) Address

To put it all together, the following output is generated by the `cardano-address address inspect` command line tool. Note that in an address, a chain pointer may exist that refers to an on-chain location containing a stake key registration certificate.[³](#c03.xhtml#ftn3) Pointers, however, are rarely used, and, in the following example, we can see that the `stake_reference` is “`by_value`”, indicating that the staking certificate is at this staking address and not a pointer.

**Shelly Base Address (base 32):**

`addr_test1qqq40ucy70wms9p7tku6ntcamzuuxnsaejal7p82qcahh3ryswkc5djr3z37lhv3zjytgyfpf8en2pa4cfuvqdz4za8syv5dnc`

`$ echo addr_test1qqq40ucy70wms9p7tku6ntcamzuuxnsaejal7p82qcahh3ryswkc5djr3z37lhv3zjytgyfpf8en2pa4cfuvqdz4za8syv5dnc | cardano-address address inspect`

`{`

`"address_style": "Shelley",`

`"address_type": 0,`

`"network_tag": 0,`

`"spending_key_hash": "0157f304f3ddb8143e5db9a9af1dd8b9c34e1dccbbff04ea063b7bc4",`

`"spending_key_hash_bech32": "addr_vkh1q9tlxp8nmkupg0jahx5678wch8p5u8wvh0lsf6sx8daug8cyak6",`

`"stake_key_hash": "6483ad8a364388a3efdd911488b4112149f33507b5c278c03455174f",`

`"stake_key_hash_bech32": "stake_vkh1vjp6mz3kgwy28m7ajy2g3dq3y9ylxdg8khp83sp525t57tzwkxk",`

`"stake_reference": "by value"`

`}`

Convert a Raw Base Address (base 16) with the header bits in bold:

`$ bech32 <<<`

`addr_test1qqq40ucy70wms9p7tku6ntcamzuuxnsaejal7p82qcahh3ryswkc5djr3z37lhv3zjytgyfpf8en2pa4cfuvqdz4za8syv5dnc`

`000157f304f3ddb8143e5db9a9af1dd8b9c34e1dccbbff04ea063b7bc46483ad8a364388a3efdd911488b4112149f33507b5c278c03455174f`

Convert a Raw Stake Address (base 16) with the header bits in bold:

`$ bech32 <<< stake_test1upjg8tv2xepc3gl0mkg3fz95zys5nue4q76uy7xqx323wncxv6f68`

`e06483ad8a364388a3efdd911488b4112149f33507b5c278c03455174f`

 
| **Hex** || **Binary** || **Hex** || **Binary** || **Hex** || **Binary** || **Hex** || **Binary** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 || 0 || 4 || 100 || 8 || 1000 || C || 1100 |
| 1 || 1 || 5 || 101 || 9 || 1001 || D || 1101 |
| 2 || 10 || 6 || 110 || A || 1010 || E || 1110 |
| 3 || 11 || 7 || 111 || B || 1011 || F || 1111 |

**Table 3.5:** Hexadecimal Conversion

# [UTXO](#toc.xhtml#s62a)

Cardano and Bitcoin use a similar unspent transaction output (UTXO) model, whereas a blockchain like Ethereum uses an account-based model. In a UTXO model, a transaction consumes one or more UTXOs as inputs and then produces one or more UTXOs as outputs, where each UTXO is locked at an address. A UTXO can only be spent (used) once and is no longer an *unspent* transaction output if it has already been used as a transaction input. The amount of assets at an address is the sum of all the UTXOs at a particular address. Additionally, only Alice can spend the UTXO at Alice’s address because she has the private key and can create a `signature` to prove it.

![](OEBPS/images/Figure-3.2.jpg)

**Figure 3.2:** UTXO Model

In *[Figure 3.2](#c03.xhtml#fig3_2)*, Alice has a UTXO with 10 Ada and wants to send 2 Ada to Bob. A transaction is created, and the UTXO with the 10 Ada is used as the input, and 2 new UTXOs are created as the outputs. The UTXO with 2 Ada will go to Bob’s address, 0.17 Ada will pay for transaction fees, and the remaining Ada (change) will be the UTXO that goes back to Alice. This works the same way as using a physical wallet when trying to pay with a 10-dollar bill at a store for a 2-dollar bottle of water.

Using a blockchain explorer, we can see what this transaction looks like on the Cardano blockchain, as shown in *[Figure 3.3](#c03.xhtml#fig3_3)*: [https://preprod.cexplorer.io/tx/c9e6dc1e7ecdf7110747c91d0d638ce896435a504e745025996230533ae9f548](https://preprod.cexplorer.io/tx/c9e6dc1e7ecdf7110747c91d0d638ce896435a504e745025996230533ae9f548)

![](OEBPS/images/Figure-3.3.jpg)

**Figure 3.3:** Block Explorer Transaction View

# [Transaction Input](#toc.xhtml#s63a)

A transaction input simply points to a transaction hash on the ledger and index since there may be more than one transaction output for a specific transaction.

![](OEBPS/images/Figure-3.4.jpg)

**Figure 3.4:** Transaction Input

The ledger specification[⁴](#c03.xhtml#ftn4) for an input is defined as:

`transaction_input = [ transaction_id : $hash32`

`, index : uint`

`]`

# [Transaction Output](#toc.xhtml#s64a)

Before the Alonzo Era of smart contracts, a transaction output contained the following:

*   Address that the output is locked at
*   Value of Ada and any Cardano native tokens
*   Optional `datum` used for storing a persistent data hash

The ability to store a `datum` value with a UTXO is how Cardano uses a EUTXO model, whereas Bitcoin only uses a UTXO model.

Here is an example of 2 EUTXOs at an address on Cardano\*:

`$ cardano-cli query utxo --address addr_test1vzu…dxn7 --cardano-mode --testnet-magic 1`

`TxHash TxIx Amount`

`--------------------------------------------------------------------`

`158…925 0 3551912116 lovelace + TxOutDatumNone`

`b4e…0d2 0 5000000 lovelace + TxOutDatumNone`

*\*Please note that the address and TxHash have been truncated for formatting.*

Observations:

*   In this example, there are 2 UTXOs.
*   Transaction hash 158…925 with index 0 has 3,551,912,116 lovelace.
*   Transaction hash b4e…0d2 with index 0 has 5,000,000 lovelace.
*   There is 1,000,000 lovelace in 1 Ada.
*   The amount of Ada locked at the address is:
    
    `3,551.912116`
    
    `+ 5.000000`
    
    `3,556.912116`
    
*   There is no datum associated with these UTXOs.

Post Alonzo, additional fields were added to the outputs. In the current Conway Era, we have the following output fields:

*   Address that the output is locked at
*   Amount of Ada and any Cardano native tokens
*   Optional `datum` used for storing a persistent data hash on-chain
*   Optional `inline datum` used for storing persistent data value on-chain
*   Optional `reference` `script` that allows a smart contract to be stored on-chain

Here is an example of a UTXO in the Conway era:

`$ cardano-cli query utxo --tx-in 5f07cfe475c846a7a644850f7174d98d281b09d3a780a0e51d06d1adff0cdcf7#4 --cardano-mode --testnet-magic 1 --out-file utxo.out`

`$ cat utxo.out`

`{`

`"5f07cfe475c846a7a644850f7174d98d281b09d3a780a0e51d06d1adff0cdcf7#4"`

`: {`

`"address":`

`"addr_test1qrazs4ngp8vl0h2qaexugnm4lhjts0g7l94d780pyx99f87m76rh0cewyp03f8w9e2lemp96jtqk0hyjqtg5528pn9tsyqhfr5",`

`"datum": null,`

`"datumhash": null,`

`"inlineDatum": null,`

`"referenceScript": null,`

`"value": {`

`"lovelace": 981840654`

`}`

`}`

The datum field contains the datum value attached to a transaction when it is submitted to the Cardano blockchain. If an `inlineDatum` is used, the datum value is stored on-chain, otherwise, only the `datumhash` is recorded on-chain.

Looking at the ledger specification,[⁵](#c03.xhtml#ftn5) the output is defined as follows:

`post_alonzo_transaction_output =`

`{ 0 : address`

`, 1 : value`

`, ? 2 : datum_option ; datum option`

`, ? 3 : script_ref ; script reference`

`}`

`datum_option = [ 0, $hash32 // 1, data ]`

# [Metadata](#toc.xhtml#s65a)

A transaction can have metadata and is optionally included when submitting a transaction to the network. Only the hash of the metadata contents is stored on-chain and *is* *not* accessible to smart contracts. Blockchain indexers, however, capture, store, and retrieve the full contents of the transaction metadata, which are used for off-chain transaction building. CIP-25,[⁶](#c03.xhtml#ftn6) using label 721, was the first transaction metadata standard for minting transactions of Non-Fungible Tokens or NFTs.

A minimal structure for an NFT using CIP-25, version 1, is as follows:

`{`

` "721": {`

`"<policy_id>": {`

`"<asset_name>": {`

`"name": <string>,`

`"image": <uri | array>`

`}`

`}`

` }`

`}`

An example of this standard being used and viewed with a blockchain explorer[⁷](#c03.xhtml#ftn7) is shown in *[Figure 3.5](#c03.xhtml#fig3_5)*:

![](OEBPS/images/Figure-3.5.jpg)

**Figure 3.5:** Transaction Metadata

Where:

*   policy\_id is 63733059deaddff620870b22f1ff6a9907bcd103e70d5dfcc53bbb14
*   asset\_name is Mad Dog
*   **NFT** name is Mad Dog
*   **NFT** image is QmckPQPzthJjkS9GRSxdw2SzSinAwdDW34xXDZd26MrV5S
*   **NFT** description is Crazy dog that loves treats

# [Plutus Scripts](#toc.xhtml#s66a)

Up to this point, we have only looked at transactions that send (spend) assets from an address owned by a user with a corresponding public and private key. In Cardano, we have Smart Contracts that use a Turing-complete scripting language called Plutus. A Plutus script can spend or mint successfully only if the evaluated result returns true. The script is included when submitting a transaction so it can be evaluated by the **Plutus Core Evaluator** inside a Cardano node. As we recall, the network comprises connected nodes that form a consensus on valid blocks. So, when a transaction is submitted, each node must execute the included script and confirm the result. If true, the node will accept the transaction into the block and become part of the blockchain.

Typically, a Plutus script is either a `spending` **(validator)** or a `minting` script. A `spending` script involves spending UTXOs locked at a script address. The script address is simply a hash of the script itself and the appropriate address header byte value. A `minting` script involves minting (adding) or burning (removing) native tokens in the Cardano ledger. When a minting script is used to mint, the new tokens must be included in a UTXO(s) as output(s) and sent to an address. Conversely, when a minting script is used to burn, the tokens must be included in UTXO(s) as input(s).

# [Datums](#toc.xhtml#s67a)

When we looked at transaction outputs, we observed that you can include a datum value for data persistence. This datum value can be read by a Plutus spending script that examines the transaction UTXO input. Since a UTXO can only be spent once as an input, the datum value must be recreated and included in the UTXO output if used by another script. If using a reference input, however, the UTXO is read-only, so the datum value can be reused for any number of transactions serially or in parallel.

# [Redeemers](#toc.xhtml#s68a)

Redeemers can provide information to a Plutus script during script evaluation within a transaction. For example, the ability to specify what type of mint operation (minting or burning) a transaction will execute. Redeemers can also pass information to a Plutus script that is only known at run time and does not need to be persistent.

The following are the different types of Redeemers from the ledger specification[⁸](#c03.xhtml#ftn8):

`redeemer_tag =`

`0 ; Spending`

`/ 1 ; Minting`

`/ 2 ; Certifying`

`/ 3 ; Rewarding`

`/ 4 ; Voting`

`/ 5 ; Proposing`

We reviewed the `Spending` and `Minting` Reedmer tags, so now let’s look at Certifying and `Rewarding`. A `Certifying` Redeemer is used for publishing certificates to the network. This is used, for example, when registering a staking key to the network for staking. A Rewarding Redeemer is used for withdrawing staking rewards locked at a stake key address. Recall that a staking address is not a UTXO-based address and is only used to receive staking rewards. At the time of writing, Voting and Proposing Redeemer tags will be used for on-chain governance and voting.

Putting this all together is a simplified diagram (without a transaction fee), as shown in *[Figure 3.6](#c03.xhtml#fig3_6),* of the inputs and outputs to create a transaction using a Plutus Script, which spends 2 Ada.

![](OEBPS/images/Figure-3.6.jpg)

**Figure 3.6:** Simplified Script Transaction

# [Witness Set](#toc.xhtml#s69a)

All transactions include a witness set that includes the witnesses required to spend a UTXO. In this chapter, we have focused on the following types of witnesses:

*   Signature
*   Redeemer
*   Datum
*   Plutus Script

Therefore, when looking at the ledger specification,[⁹](#c03.xhtml#ftn9) all transactions must have the following high-level structure:

`transaction =`

`[ transaction_body`

`, transaction_witness_set`

`, bool`

`, auxiliary_data / null`

`]`

Where:

*   `Transaction_body` contains, among other things, a fee, the UTXO inputs and outputs, metadata hash, script hash, and minting value if any.
*   `Transaction_witness_set` contains any witnesses required for spending UTXO inputs
*   `Bool` indicates if this is a valid transaction
*   `Auxiliary_data` optionally contains transaction metadata

# [Conclusion](#toc.xhtml#s70a)

We reviewed the different types of Cardano addresses and how they are constructed and deconstructed. We looked at the UTXO architecture, how inputs and outputs are used, and how UTXOs are locked at an address. We looked at an example of transaction metadata and how it is stored and linked to an on-chain transaction. Next, we looked at the Datum and Redeemer and how it provides information to a Plutus script as part of a transaction. Finally, we reviewed the concept of a Witness Set that allows a transaction to spend UTXO inputs. In the next chapter, we will look at Plutus scripts in more detail and how to use them in a transaction.

# [Points to Remember](#toc.xhtml#s71a)

*   There are three main types of addresses: Base, Enterprise, and Reward.
*   A transaction header type determines the type of address.
*   A transaction network tag determines the network a transaction is associated with (Mainnet or Testnet).
*   A transaction contains a Payment Part and an optional Delegation Part.
*   The Payment or Delegation Part can be either a `PaymentKeyHash` (public key hash) or a `ScriptHash`.
*   A reward address is a special type of account-based address only used for staking rewards.
*   A transaction consumes one or more UTXOs as inputs and must produce one or more UTXOs as outputs.
*   A signature is proof that the transaction was signed by the correct private key.
*   A transaction input includes an index because there may be more than one output UTXO for a given transaction.
*   A Datum is used to store persistent data on-chain and is included in a UTXO.
*   A Datum value can be stored as a hash or in full as an inline datum.
*   The Plutus Core Evaluator evaluates a Plutus script to see if it returns true.
*   A Plutus script is typically a spending (validator) or minting script.
*   A Plutus spending (validator) script spends UTXOs locked at a script address.
*   A Plutus minting script is used to mint or burn Cardano native tokens.
*   A UTXO can also be a reference input, a read-only UTXO that cannot be spent.
*   A redeemer provides information to a script during a transaction evaluation.
*   The witness set may contain a signature, redeemer, datum, or Plutus scripts.

# [Multiple Choice Questions](#toc.xhtml#s72a)

1.  What is not a valid Cardano Address? 
    1.  Base
    2.  Enterprise
    3.  Reward
    4.  UTXO
2.  A script address is derived from? 
    1.  Public key hash
    2.  Plutus script hash
    3.  Private stake key hash
    4.  Private key hash
3.  What does a signature prove? 
    1.  A transaction is signed with a valid public key
    2.  A transaction is signed with a valid staking key
    3.  A transaction is signed with a valid private key
    4.  A transaction is signed with a valid reward key
4.  A Plutus script evaluates to? 
    1.  A boolean value
    2.  A binary value
    3.  A hexadecimal value
    4.  Non-zero value
5.  What is a Redeemer? 
    1.  Used for identifying reference scripts
    2.  Used for transaction balancing
    3.  Provides information to a script at runtime
    4.  Halts a transaction if false

# [Answers](#toc.xhtml#s73a)

1.  d
2.  b
3.  c
4.  a
5.  c

# [Questions](#toc.xhtml#s74a)

1.  Why can’t you lock a UTXO at a reward address?
2.  What is the process for claiming staking rewards?
3.  Why do you include a Plutus script as a witness in the witness set and what can it prove?
4.  Why not store all metadata data on-chain, not just the metadata hash?
5.  Why is a Plutus spending script also known as a validator?

# [Key Terms](#toc.xhtml#s75a)

*   **Base Address:** Address that includes both the payment and staking keys.
*   **Datum:** It is used to store the datum hash on-chain.
*   **Enterprise Address:** Address that only includes the payment key.
*   **Inline datum:** It is used to store the actual datum value on-chain.
*   **Metadata:** Data that describes a transaction.
*   **Minting script:** A Plutus script used to mint or burn Cardano native tokens.
*   **NFT:** Non-Fungible Token.
*   **PaymentKeyHash:** The hash digest of a public key.
*   **Plutus Core Evaluator:** The component in a node that evaluates a plutus script.
*   **Plutus script:** A Turing-complete language that is executed on the node.
*   **Redeemer:** Redeemer is used to pass information into a script at runtime.
*   **Reference script:** A read-only UTXO that cannot be spent.
*   **Reward Address:** It is used for distributing and receiving staking rewards.
*   **ScriptHash:** The hash digest of a Plutus script.
*   **Signature:** The cryptographic hash signature of a transaction hash.
*   **Spending (validator) script:** A Plutus script used to spend UTXOs locked at a script address.
*   **UTXO:** An unspent transaction output.
*   **Witness:** It provides proof that the transaction can spend UTXO inputs.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c03.xhtml#ftn1a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0019](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0019)

[²](#c03.xhtml#ftn2a) [https://docs.cardano.org/learn/cardano-addresses/](https://docs.cardano.org/learn/cardano-addresses/)

[³](#c03.xhtml#ftn3a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0019](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0019)

[⁴](#c03.xhtml#ftn4a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

[⁵](#c03.xhtml#ftn5a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

[⁶](#c03.xhtml#ftn6a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0025](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0025)

[⁷](#c03.xhtml#ftn7a) [https://preprod.cexplorer.io/tx/33767caa19d9dd1eaef3eab06264b1f909ecf726f074913855b7ca84fa7fb31e](https://preprod.cexplorer.io/tx/33767caa19d9dd1eaef3eab06264b1f909ecf726f074913855b7ca84fa7fb31e)

[⁸](#c03.xhtml#ftn8a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

[⁹](#c03.xhtml#ftn9a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

# [CHAPTER 4](#toc.xhtml#c04)

# [Plutus](#toc.xhtml#c04)

# [Introduction](#toc.xhtml#s76a)

Plutus, the Smart Contract language for Cardano, is compiled and executed as an Untyped Plutus Core (**UPLC**) program. The first Plutus smart contracts were written in Haskell using the PlutusTx Haskell module. Unfortunately, PlutusTx was not optimized and created a very challenging development experience when Cardano smart contracts first launched. Shortly thereafter, alternative Plutus scripting languages, such as Aiken ([https://aiken-lang.org/](https://aiken-lang.org/)) and Helios ([https://github.com/Hyperion-BT/helios](https://github.com/Hyperion-BT/helios)), emerged, which were significantly more performant and used syntax and coding styles similar to popular programming languages like Rust or C.

In this chapter, we will look at the Plutus core specification in detail and how the Cardano ledger executes a Lambda Calculus program. We will examine the different data structures used in Plutus and how the data is serialized and transmitted using the Concise Binary Object Representation (**CBOR**) format. Next, we will look at the Plutus cost model and how it is used to calculate the CPU and memory units, which must not exceed the maximum values. Finally, we will discuss collateral and its role in a transaction.

# [Structure](#toc.xhtml#s77a)

In this chapter, we will discuss the following topics:

*   Plutus Specification
*   Concise Binary Representation (**CBOR**) 
    *   Transaction
    *   Redeemer
    *   Plutus Script
    *   Datum
*   Plutus Execution Budget
*   Collateral

# [Plutus Specification](#toc.xhtml#s78a)

The first generation of scripts on Cardano were **native scripts**,[¹](#c04.xhtml#ftn1) followed by Plutus.[²](#c04.xhtml#ftn2) Native (phase-1) scripts have very limited functionality and are executed internally within the ledger. Plutus, a Turing-complete scripting language, executes outside the ledger but requires a successful evaluation to spend a UTXO locked by a Plutus script.[³](#c04.xhtml#ftn3) The ledger must support multiple Plutus script versions, so each script includes the version number in the script itself. This way, the ledger will know how to evaluate a script, each with its own version. *[Table 4.1](#c04.xhtml#tab4_1)* summarizes the Plutus versions known at the time of writing, and we will only focus on **PlutusV2** and **Plutus Core Version 1.0.0** for this book.

| **Era** || **Ledger Language (Id)** || **Plutus Core Version** || **Protocol Version** || **Date** |
| --- | --- | --- | --- | --- |
| Alonzo || PlutusV1 (0) || 1.0.0 || 5.0 || Sep, 2021 |
| Vasil || PlutusV2 (1) || 1.0.0 || 7.0 || Jun, 2022 |
| Valentine || PlutusV2 (1) || 1.0.0 || 8.0 || Feb, 2023 |
| Conway || PlutusV3 (2) || 1.1.0 || 9.0 || Upcoming |

**Table 4.1:** Plutus Versions

The objective of the Plutus specification was to create a simple scripting language that can be evaluated with minimal (and constrained) computational footprint on the Cardano Node. Unlike the Ethereum Virtual Machine, which has a long and complicated proof, the Plutus abstract state machine is short and succinct.[⁴](#c04.xhtml#ftn4) This is a very desirable property when building a highly stable blockchain to minimize hard fork upgrades. Plutus scripts are written using a language called Untyped Plutus Core or **UPLC**, which was derived from System F, a form of **Lambda Calculus**.[⁵](#c04.xhtml#ftn5) Fortunately, Smart Contract Plutus development uses **higher-level programming** languages that compile and generate the **UPLC** for us.

***Note***: Learning **UPLC** or Lambda Calculus is not required to write Cardano smart contracts. The remainder of this section is optional but may be helpful to readers looking for more details on how generated UPLC code maps to the Plutus Core specification. For an introduction to Lambda Calculus, please look at the video “*Lambda Calculus - Fundamentals of Lambda Calculus & Functional Programming in JavaScript*.”[⁶](#c04.xhtml#ftn6)

# [UPLC Primitive Types](#toc.xhtml#s79a)

**UPLC** uses a simple language syntax with a limited set of atomic types, listed in *[Table 4.2](#c04.xhtml#tab4_2)*:

| **Type** || **Syntax** |
| --- | --- |
| `integer` || `-?[0-9]+` |
| `bytestring` || `#([0-9A-Fa-f][0-9A-Fa-f])*` |
| `string` || `UTF-8 characters, enclosed in double quotes "` `"` |
| `bool` || `True | False` |
| `unit` || `()` |
| **Type** || **Denotation** |
| `Data` || `data Data =``Constr Integer [Data]``| Map [(Data, Data)]``| List [Data]``| I Integer``| B ByteString` |

**Table 4.2:** UPLC Atomic Types

In addition to the atomic data types, there are two types of operators included in UPLC, as shown in *[Table 4.3](#c04.xhtml#tab4_3)*:

| **Operator op** || **|op|** || **Denotation** |
| --- | --- | --- |
| `list` || `1` || `[list(t)] = [t]` |
| `pair` || `2` || `[pair(t1,t2)] = [t1] x [t2]` |

**Table 4.3:** UPLC Type Operators

The `con` keyword defines constants, followed by the type declaration and the value. *[Table 4.4](#c04.xhtml#tab4_4)* provides some usage examples:[⁷](#c04.xhtml#ftn7)

| **Type** || **Example** |
| --- | --- |
| `unit` || `con unit ()` |
| `bool` || `con bool False` |
| `integer` || `con integer 123` |
| `bytestring` || `con bytestring #abc123` |
| `string` || `con string "GM Cardano"` |
| `pair` || `con pair<bool, integer> [True, 123]` |
| `list` || `list<bytestring> [#0d, #f3]` |

**Table 4.4:** UPLC Type Examples[⁸](#c04.xhtml#ftn8)

A lambda function uses the keyword `lam` and is passed a variable name and returns a term that can be either a constant, a function, or a well-formed value of any type. The UPLC program must not contain any free variables and, therefore, be considered a “*closed term*.”[⁹](#c04.xhtml#ftn9) For example, `(program 1.0.0 (lam x x))` is a valid program, but `(program 1.0.0 (lam x y))` is not. Please note that all Plutus scripts must include a `program` and `version`.

Plutus Core has no arithmetic operators but uses built-in functions for arithmetic operations. Some `builtin` functions are domain-specific to the Cardano blockchain, while other `builtin` functions may be added over time. The last items we will review are the `force` and `delay` directives. The force directive is applied to a polymorphic function to force the instantiation of a typed parameter.[^(10)](#c04.xhtml#ftn10) The `delay` directive is used for **lazy evaluation** of a branch condition, which preserves type abstraction.[^(11)](#c04.xhtml#ftn11) **Lazy evaluation** allows for more efficient code execution because values are only computed if they are used. This also allows for the creation of infinite data structures that are impossible to create in languages like C.

# [UPLC Grammar](#toc.xhtml#s80a)

Putting this all together, we define the grammar of a **UPLC** program, as shown in *[Figure 4.1](#c04.xhtml#fig4_1)*:

![](OEBPS/images/Figure-4.1.jpg)

**Figure 4.1:** UPLC Grammar (Plutus Core Version 1.0.0)[^(12)](#c04.xhtml#ftn12)

# [UPLC Example](#toc.xhtml#s81a)

Looking at a simplified example, we can see how a higher-level language, such as Aiken, generates a UPLC program. *[Table 4.5](#c04.xhtml#tab4_5)* has a simple validator script that always returns true. The program uses lambda (`lam`) functions to evaluate and return the constant `True`.

**Higher Level Language**

![](OEBPS/images/tab5.2.jpg)

**Table 4.5:** UPLC Example

# [Concise Binary Representation (CBOR)](#toc.xhtml#s82a)

**CBOR** is a binary and encoding format defined in the Internet standard RFC 8949.[^(13)](#c04.xhtml#ftn13) In the previous chapter on *Transactions*, we looked at the Cardano ledger **CDDL** specification,[^(14)](#c04.xhtml#ftn14) which defines the format of a transaction. When a transaction is submitted to the network, the entire transaction and all relevant data are **serialized** and encoded in **CBOR**. We will examine a transaction in detail and **deserialize** it to see the UPLC Plutus code and related data (redeemer and datum).

For example, *[Figure 4.2](#c04.xhtml#fig4_2)* shows a transaction executing a Plutus validator script:

[https://preprod.cexplorer.io/tx/99c529355ebd1f410517457b6ff04e66c2de28b8667b9428ec232e03efa22c29](https://preprod.cexplorer.io/tx/99c529355ebd1f410517457b6ff04e66c2de28b8667b9428ec232e03efa22c29)

![](OEBPS/images/Figure-4.2.jpg)

**Figure 4.2:** Transaction Example

# [Transaction](#toc.xhtml#s83a)

The **CBOR** hexadecimal format for this transaction that was submitted to the network is as follows:

`84a80082825820d9b02da5897bd1ff9e2fdab008334d2804ea1accab`

`c7c3962e33771ed9f1a8d500825820d9b02da5897bd1ff9e2fdab008334d2804ea1a`

`ccabc7c3962e33771ed9f1a8d501018182581d606d04be153546d63c8a33`

`e0c11ec44cf790803f31c2f893fc241529531a05eb1244021a0002`

`d9250b582031e6c463846e3c0afe2aebfc9993355dbe8ce4dab892a7`

`af0e397a75df3509b90d81825820d9b02da5897bd1ff9e2fdab008334d2804ea1a`

`ccabc7c3962e33771ed9f1a8d5010e81581c6d04be153546d63c8a33e0c11e`

`c44cf790803f31c2f893fc241529531082581d606d04be153546d63c8a33e0c11`

`ec44cf790803f31c2f893fc241529531a05d9dd11111a000445b8a30081825820`

`fc6500742705cfe8c2f0822e73e2ab09c43285973adffe8aa06bd12d1fa6051f584`

`0ec7f53a69852e6daa868a3f221114435544ab2851bc6f2f42abe9772507b30064a1`

`f012ddab23153644703047ea2faf9132390e91937b82389626404d7adfd0105818`

`40000d8799f4d48656c6c6f2c20576f726c6421ff821977151a009daaac068158f258`

`f0010000323232323232323222232325333008323232533300b002100114a066446`

`46600200200644a66602200229404c8c94ccc040cdc78010028a511330040040013`

`014002375c60240026eb0c038c03cc03cc03cc03cc03cc03cc03cc03cc020c008c0`

`20014dd71801180400399b8f375c6002600e00a91010d48656c6c6f2c20576f726`

`c6421002300d001149858c94ccc020cdc3a400000226464a66601a601e0042930b1ba`

`e300d00130060041630060033253330073370e900000089919299980618070010a4`

`c2c6eb8c030004c01401058c01400c8c014dd5000918019baa0015734aae7555cf2a`

`b9f5742ae89f5f6`

When we decode this to a diagnostic form using [https://cbor.nemo157.com/](https://cbor.nemo157.com/)*,* we can see the transaction details, as illustrated in *[Figures 4.3](#c04.xhtml#fig4_3)* and *[4.4](#c04.xhtml#fig4_4)*. *[Figure 4.3](#c04.xhtml#fig4_3)* shows the UTXO inputs and outputs and the required signatures for this transaction:

![](OEBPS/images/Figure-4.3.jpg)

**Figure 4.3:** CBOR Transaction Part 1

*[Figure 4.4](#c04.xhtml#fig4_4)* shows the collateral required, the public key, Redeemer, and Plutus script witnesses. This transaction does not contain auxiliary data or metadata, and the transaction validity flag is set to true.

![](OEBPS/images/Figure-4.4.jpg)

**Figure 4.4:** CBOR Transaction Part 2

# [Redeemer](#toc.xhtml#s84a)

To get a human-readable version of the Redeemer, we need to convert from the Hex ByteString to a UTF-8 string. Plutus, however, will use the ByteString directly during script execution. Here is an example of using xxd to convert a Hex-encoded ByteString to a normal string:

`$ echo 48656c6c6f2c20576f726c6421 | xxd -p -r`

`$ Hello, World!`

# [Plutus Script](#toc.xhtml#s85a)

The Plutus script is double encoded (CBOR + flat), meaning we need to deserialize it twice to get it into UPLC. So, the first step is to decode it using a CBOR decoder,[^(15)](#c04.xhtml#ftn15) and save it to a file called `plutus.flat`:

`$ cat plutus.flat`

`010000323232323232323222232325333008323232533300b002100114a066446466002`

`00200644a66602200229404c8c94ccc040cdc78010028a511330040040013014002375c`

`60240026eb0c038c03cc03cc03cc03cc03cc03cc03cc03cc020c008c020014dd7180118`

`0400399b8f375c6002600e00a91010d48656c6c6f2c20576f726c6421002300d0011498`

`58c94ccc020cdc3a400000226464a66601a601e0042930b1bae300d0013006004163006`

`0033253330073370e900000089919299980618070010a4c2c6eb8c030004c01401058c0`

`1400c8c014dd5000918019baa0015734aae7555cf2ab9f5742ae8`

Next, we need to convert it from hex to UPLC using the Aiken utility tool to decode it:

`$ aiken uplc decode --hex plutus.flat`

`(program`

`1.0.0`

`[`

`(lam`

`i_0`

`[`

`(lam`

`i_1`

`…`

`)`

`(force (builtin headList))`

`]`

`)`

`(force (builtin tailList))`

`]`

`)`

# [Datum](#toc.xhtml#s86a)

Next, we will look at a Datum in *[Figure 4.5](#c04.xhtml#fig4_5)* using `cexplorer.io`:[^(16)](#c04.xhtml#ftn16)

![](OEBPS/images/Figure-4.5.jpg)

**Figure 4.5:** Datum Example

The datum in *[Figure 4.5](#c04.xhtml#fig4_5)* is an inline datum, so the value is stored on-chain and locked at a UTXO that we want to spend. If we look at the UTXO, we will see that the value is encoded in CBOR hex format:

`d8799f581c6d04be153546d63c8a33e0c11ec44cf790803f31c2f893fc24152953ff`

When we decode the datum CBOR hex value, we get the following output of a byte array:

`121_0([_`

`h'6d04be153546d63c8a33e0c11ec44cf790803f31c2f893fc24152953',`

`])`

In this example, the datum value represents a public key hash.

# [Plutus Execution Budget](#toc.xhtml#s87a)

Looking at the Redeemer Witness of the transaction in *[Figure 4.4](#c04.xhtml#fig4_4)*, we will notice an execution budget for the attached plutus script:

`[30485_1, 10332844_2]`

These values refer to the memory and CPU (steps) execution units, which are defined in the Plutus ledger specification:

`ex_units = [mem: uint, steps: uint]`

The `mem` and `steps` are calculated and submitted with the transaction, then verified by the Plutus Core Evaluator during script execution. If either of the values exceeds the maximum limits during script execution, then an error will be raised:

`Error: The budget when the machine terminated was:\n({ cpu: -84834\n| mem: 17553\n}`

In this example, the `cpu/steps` value was exceeded and resulted in a negative number. As a result, the execution was halted, and the validation failed. To calculate the `mem` and `cpu/step` costs for a given Plutus script, a `cost model`[^(17)](#c04.xhtml#ftn17) is used to map the `execution cost` for each Plutus operation. The cost model is located in the network protocol parameters and can be changed over time via network updates. To see the `protocol parameters`, you can use the cardano-cli tool:

`$ cardano-cli query protocol-parameters --testnet-magic 1`

`{`

`"collateralPercentage": 150,`

`"costModels": {`

`…`

`"PlutusScriptV2": {`

`"addInteger-cpu-arguments-intercept": 205665,`

`"addInteger-cpu-arguments-slope": 812,`

`"addInteger-memory-arguments-intercept": 1,`

`"addInteger-memory-arguments-slope": 1,`

`…`

`"maxTxExecutionUnits": {`

`"memory": 14000000,`

`"steps": 10000000000`

`},`

`"maxTxSize": 16384,`

`…`

The protocol parameters specify, among other things, the execution cost of each Plutus operation, the maximum `memory` and `steps` units per transaction, and the maximum overall transaction size (`maxTxSize`) in KB.

# [Collateral](#toc.xhtml#s88a)

The last topic we will look at is collateral included in a transaction. Collateral is a small amount of Lovelace (1.5 × Transaction Fee) that will be used if there is a phase-2 Plutus script failure.[^(18)](#c04.xhtml#ftn18) Any change left over from the collateral inputs is returned to the user and is called the **collateral return**. However, Plutus script evaluation is usually done locally before submitting it to the network. This will catch and prevent the submission of an invalid Plutus script. The role of collateral is to help protect the network from malicious or spam transactions.

# [Conclusion](#toc.xhtml#s89a)

The reader should now understand the Plutus core specification and the **UPLC** code used for Plutus script execution and evaluation. We examined a **CBOR** transaction, how to deserialize it, and looked into the transaction details. We also looked at the Plutus script execution budget and how it is calculated using the **cost model**. Lastly, we discussed collateral, which is used during a phase-2 Plutus script evaluation failure. The next chapter will explore the off-chain code used to create and submit a transaction. We will also look at the user wallet, which is the gateway to interacting with the Cardano blockchain and smart contracts.

# [Points to Remember](#toc.xhtml#s90a)

*   The first generation of scripts on Cardano was native scripts that were evaluated inside the ledger.
*   A Plutus script is a phase-2 script that evaluates outside of the ledger.
*   Untyped Plutus Core or UPLC is a form of Lambda Calculus.
*   UPLC is the low-level language that is executed on the node.
*   Writing smart contracts is done with a higher-level language that generates the low-level UPLC.
*   UPLC programs must be closed with all terms properly defined.
*   A UPLC program can take advantage of the lazy evaluation found in Lambda Calculus.
*   CBOR is a binary standard for serializing and deserializing data structures.
*   Cardano transactions are serialized to CBOR when submitted to the network and deserialized during Cardano node validation.
*   The Redeemer in a transaction contains the memory and step/cpu units that a script will consume.
*   During Plutus script evaluation, the script will halt and fail if the memory or step/cpu units exceed the maximum allowable units.
*   The cost model in the network parameters contains the cost for each Plutus operation and the maximum memory and step/cpu unit allowed in a transaction.
*   Collateral must be provided in a transaction and is designed to protect the network from malicious and spam transactions.

# [Multiple Choice Questions](#toc.xhtml#s91a)

1.  The first generation of scripts on Cardano are? 
    1.  PlutusV1
    2.  PlutusV2
    3.  Native Scripts
    4.  Smart Scripts
2.  What statement is false about Native Scripts and Plutus Scripts? 
    1.  Both must be evaluated to be true to spend a UTXO locked by the script
    2.  Both can create a multi-sig script address
    3.  Both are Turing-complete
    4.  Native scripts are a phase-1 script
3.  What is lam in UPLC? 
    1.  A lambda function abstraction
    2.  A lambda function application
    3.  A lambda function permutation
    4.  A lambda function association
4.  Why is lazy evaluation desirable? 
    1.  Less efficient code execution
    2.  More efficient code execution
    3.  Forces evaluation of all declared variables
    4.  Cannot create infinite data structures
5.  Where is the current Plutus cost model located? 
    1.  Node configuration
    2.  Plutus script configuration
    3.  Plutus evaluator configuration
    4.  Protocol parameters

# [Answers](#toc.xhtml#s92a)

1.  c
2.  c
3.  a
4.  b
5.  d

# [Questions](#toc.xhtml#s93a)

1.  What are the advantages of Lambda Calculus?
2.  Are Turing-complete and Lambda Calculus programs formally equivalent?
3.  What are the differences between CBOR and flat encoding?
4.  Why are the memory and cpu/step units included in the Redeemer in a transaction?
5.  What are the similarities and differences between step-1 and step-2 scripts?
6.  What inputs can be used for collateral?

# [Key Terms](#toc.xhtml#s94a)

*   **CBOR**: Concise Binary Object Representation
*   **Collateral Return:** The amount of Ada change returned if collateral is used during a transaction.
*   **CDDL:** Concise Data Definition Library
*   **Cost Model:** The execution cost parameters for each Plutus operation.
*   **Deserialize:** The process of decoding code and data structures from a binary format.
*   **Execution Cost:** The amount of memory and cpu/step units used for each Plutus operation.
*   **Higher Level Programming:** A language that allows the use of more complex functions and data structures to make the code more readable.
*   **Lambda Calculus:** A minimal language to define functions and applications.
*   **Lazy Evaluation:** Only instantiate variables that are used in code execution.
*   **Native Scripts:** Simple scripts that are used in phase-1 evaluation.
*   **Protocol Parameters:** A file with parameters and settings that is used by the network.
*   **Serialize:** The process of encoding code and data structures to a binary format.
*   **UPLC:** Untyped Plutus Core

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c04.xhtml#ftn1a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0029](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0029)

[²](#c04.xhtml#ftn2a) lutus Core Team, “Formal Specification of the Plutus Core Language.” 24.

[³](#c04.xhtml#ftn3a) Andre Knispel, et al., “A Formal Specification of the Cardano Ledger integrating Plutus Core,” 3.

[⁴](#c04.xhtml#ftn4a) Philip Wadler, “Functional smart contracts on Cardano.”

[⁵](#c04.xhtml#ftn5a) James Chapman, et al., “System F in Agda, for fun and profit.”

[⁶](#c04.xhtml#ftn6a) Gabriel Lebec, “Lambda Calculus - Fundamentals of Lambda Calculus & Functional Programming in JavaScript.”

[⁷](#c04.xhtml#ftn7a) Plutus Core Team, “Formal Specification of the Plutus Core Language,” 26.

[⁸](#c04.xhtml#ftn8a) [https://aiken-lang.org/uplc/syntax#primitive-types](https://aiken-lang.org/uplc/syntax#primitive-types)

[⁹](#c04.xhtml#ftn9a) Plutus Core Team, “Formal Specification of the Plutus Core Language,” 6.

[^(10)](#c04.xhtml#ftn10a) Plutus Core Team, “Formal Specification of the Plutus Core Language,” 11.

[^(11)](#c04.xhtml#ftn11a) [https://aiken-lang.org/uplc/syntax#delay--force](https://aiken-lang.org/uplc/syntax#delay--force)

[^(12)](#c04.xhtml#ftn12a) Plutus Core Team, “Formal Specification of the Plutus Core Language,” 6

[^(13)](#c04.xhtml#ftn13a) [https://www.rfc-editor.org/rfc/rfc8949.html](https://www.rfc-editor.org/rfc/rfc8949.html)

[^(14)](#c04.xhtml#ftn14a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/conway/impl/cddl-files/conway.cddl)

[^(15)](#c04.xhtml#ftn15a) [https://cbor.nemo157.com/](https://cbor.nemo157.com/)

[^(16)](#c04.xhtml#ftn16a) [https://preprod.cexplorer.io/datum/a5b09d918a1fd954e14ca4609ae4216ec3cad02fda81b70a9eb87c5ab9a71854](https://preprod.cexplorer.io/datum/a5b09d918a1fd954e14ca4609ae4216ec3cad02fda81b70a9eb87c5ab9a71854)

[^(17)](#c04.xhtml#ftn17a) [https://plutus-apps.readthedocs.io/en/latest/reference/cost-model-parameters.html](https://plutus-apps.readthedocs.io/en/latest/reference/cost-model-parameters.html)

[^(18)](#c04.xhtml#ftn18a) Andre Knispel, et al., “A Formal Specification of the Cardano Ledger integrating Plutus Core,” 6.

# [CHAPTER 5](#toc.xhtml#c05)

# [Transaction Builder](#toc.xhtml#c05)

# [Introduction](#toc.xhtml#s95a)

This chapter will combine our knowledge of on-chain Plutus scripts and how to lock Ada into a smart contract using off-chain code. We will look at Cardano wallets, the gateway to interacting with the blockchain and Smart Contracts. Next, we will look at some of the tools to help build and submit transactions, such as `Demeter.run`. Then, we will build a simple vesting smart contract using two popular approaches: Helios and Lucid + Aiken.

# [Structure](#toc.xhtml#s96a)

In this chapter, we will discuss the following topics:

*   Transaction Lifecycle
*   Wallets 
    *   Seed Phrase
    *   Testnet Faucet
    *   Address Derivation
    *   Staking
    *   CIP-30
*   Demeter.run
*   Off-Chain Code Examples 
    *   Helios
    *   Lucid + Aiken

# [Transaction Lifecycle](#toc.xhtml#s97a)

In the previous chapter, we looked at how the Cardano node and ledger evaluate a Plutus script. This chapter will focus on how to build and submit a transaction that includes a Plutus script. The building of a transaction is assembling the UTXO inputs and outputs, attaching scripts we want to run, and adding redeemers, datums, and metadata, if any. Once the transaction is assembled, we must get it signed and include the signature as a witness. *[Figure 5.1](#c05.xhtml#fig5_1)* shows the off-chain steps of building, signing, serializing, and submitting a transaction to the network.

![](OEBPS/images/Figure-5.1.jpg)

**Figure 5.1:** Transaction Lifecycle

# [Wallets](#toc.xhtml#s98a)

In cryptocurrencies, a wallet is the user interface that interacts with the blockchain. A wallet typically allows users to create an account, which is a collection of UTXOs locked at a public key address. This type of **account abstraction** helps users visualize familiar concepts such as account balances and transaction history. Many wallets also allow users to select stake pools and register their stake key to collect staking rewards. *[Table 5.1](#c05.xhtml#tab5_1)* lists some of the wallet providers on the Cardano network in alphabetical order.

| **Name** || **Full Node** || **Hardware Wallet Support** || **Mobile App** || **Open Source** |
| --- | --- | --- | --- | --- |
| `Daedalus` || **✔** || **✔** || **✖** || **✔** |
| `Eternl` || **✖** || **✔** || **✔** || **✖** |
| `Flint` || **✖** || **✔** || **✔** || **✔** |
| `GameChanger` || **✖** || **✖** || **✖** || **✔** |
| `GeroWallet` || **✖** || **✔** || **✖** || **✖** |
| `Lace` || **✖** || **✔** || **✖** || **✔** |
| `Ledger` || **✖** || **✔** || **✖** || **✔** |
| `Nami` || **✖** || **✖** || **✖** || **✔** |
| `NuFi` || **✖** || **✔** || **✖** || **✖** |
| `Typhon` || **✖** || **✔** || **✖** || **✔** |
| `VESPR` || **✖** || **✖** || **✔** || **✔** |

**Table 5.1:** Cardano Wallets[¹](#c05.xhtml#ftn1)

**Full Node:** A wallet that includes a full Cardano node and does not use any third-party service to look up transactions on the blockchain.

**Hardware Wallet Support**: A wallet that supports hardware devices in signing transactions.

**Mobile App:** A wallet with a native mobile app on iOS or Android devices.

**Open Source:** The wallet’s open-source code is available on GitHub.

# [Seed Phrase](#toc.xhtml#s99a)

To create an account with a wallet, you must either create a new seed phrase or import an existing one. If we recall from *[Chapter 3, Transactions](#c03.xhtml)*, a private key is needed to sign a transaction. To create this private key, wallets typically use a **seed phrase** to generate a random private key. This is a two-step process, whereby, a mnemonic sentence or a group of words is used to create a random seed.[²](#c05.xhtml#ftn2) This random seed is then used to derive the public and private key pairs.[³](#c05.xhtml#ftn3)

# [Testnet Faucet](#toc.xhtml#s100a)

Cardano typically has two Testnets used for end-to-end testing before Mainnet.[⁴](#c05.xhtml#ftn4) Please be mindful of what network you are connecting to when sending and receiving funds.

*   **Preview Testnet:** The epoch has been shortened to 1 day and is ahead of a Mainnet fork by at least 4 weeks.
*   **Preprod Testnet:** This network is used for release candidate testing for mainnet launches. It mimics production as closely as possible and is the more stable Testnet network.

We will use the Testnet faucet to acquire test Ada and send it to our wallet address. In this book, we will use the `Eternl` wallet, and *[Figure 5.2](#c05.xhtml#fig5_2)* shows how to get an address to receive funds.

![](OEBPS/images/Figure-5.2.jpg)

**Figure 5.2:** Eternl Wallet Receives Funds

Copy the address and paste it into the Testnet faucet form on [https://docs.cardano.org/cardano-testnet/tools/faucet/](https://docs.cardano.org/cardano-testnet/tools/faucet/), as shown in *[Figure 5.3](#c05.xhtml#fig5_3).*

![](OEBPS/images/Figure-5.3.jpg)

**Figure 5.3:** Testnet Faucet Request

Select “`Request Funds`,” and you should see the “`Success`” message, which includes a transaction hash that you can use on [https://preprod.cexplorer.io/](https://preprod.cexplorer.io/) to verify the status.

![](OEBPS/images/Figure-5.4.jpg)

**Figure 5.4:** Testnet Faucet Submitted

After 10–60 seconds, you should see 10,000 test Ada (`tAda`) in the `Eternl` wallet.

![](OEBPS/images/Figure-5.5.jpg)

**Figure 5.5:** Eternl Wallet Account Summary

# [Address Derivation](#toc.xhtml#s101a)

The **Hierarchy for Deterministic** (**HD**) wallets, such as `Eternl`, follows the specification in CIP-1852[⁵](#c05.xhtml#ftn5) for the derivation path:

`m / purpose' / coin_type' / account' / role / index`

In *[Figure 5.5](#c05.xhtml#fig5_5),* we can see the derivation path for the receiving address is:

`m/1852'/1815'/0'/0/0`

*[Table 5.2](#c05.xhtml#tab5_2)* explains each of the derivation path elements:

| **Name** || **Value** || **Notes** |
| --- | --- | --- |
| Purpose || 1852 || Specification name (for example, CIP-1852) |
| Coin Type || 1815 || Different value for each cryptocurrency (for example, Ada Lovelace birth) |
| Account || 0 || Allows for creating separate wallet accounts |
| Role || 0 || 0 = External Chain (receiving payments)1 = Internal Chain (change address)2 = Staking Key |
| Index || 0 || Address index starting at 0 |

**Table 5.2:** Derivation Path

You can create different addresses for the same private key to receive payments (and change) using HD wallets. In practice, however, using a “`single address mode`” is generally preferable, where the same address is re-used. Creating a new address for each transaction helps anonymize it so it cannot be linked to the wallet account. With Cardano, however, as soon as a stake key is registered for a wallet address, all transactions from that address can be linked via the stake key. Having multiple addresses for the receiving and change addresses adds additional dApp complexity, which is why some wallets only support single address mode. To switch (or keep) `Eternl` to use single address mode is shown in *[Figure 5.6](#c05.xhtml#fig5_6)*.

![](OEBPS/images/Figure-5.6.jpg)

**Figure 5.6:** Eternl Single Address Mode

# [Staking](#toc.xhtml#s102a)

One of the most important features of the Cardano network is the ability to stake from your wallet easily. This is known as liquid, non-custodial staking, and it is why Cardano has a high level of staking on the network, which contributes to its security and decentralization. To stake, a user goes to the staking tab, chooses a stake pool, and selects “`Delegate`,” as shown in *[Figure 5.7](#c05.xhtml#fig5_7)*.

![](OEBPS/images/Figure-5.7.jpg)

**Figure 5.7:** Stake Pool Delegation

Next, the user must sign a transaction that registers the stake key and stake pool delegation to the network, as shown in *[Figure 5.8](#c05.xhtml#fig5_8).*

![](OEBPS/images/Figure-5.8.jpg)

**Figure 5.8:** Stake Pool Registration

When a transaction with the stake key registration certificate and stake pool delegation certificate has been confirmed, the user will receive staking rewards as per the Ouroboros lifecycle discussed in *[Chapter 2, Cryptography and Consensus Algorithms Overview](#c02.xhtml).*

# [CIP-30](#toc.xhtml#s103a)

For a dApp to connect to a browser extension wallet such as `Eternl`, the dApp should follow the CIP-30 standard.[⁶](#c05.xhtml#ftn6) This standard describes a webpage-based communication bridge to allow webpages to interact with the browser extension wallet. This is implemented by injecting JavaScript code into the webpage that is being rendered. The webpage or dApp can then call the JavaScript code with predefined public methods to retrieve and submit data to the wallet. In the off-chain code examples, we will see how to interact with the wallet using CIP-30 later in this chapter.

# [Demeter.run](#toc.xhtml#s104a)

Before we dive into our first off-chain smart contract examples, we must get an environment up and running quickly. This is where `Demeter.run` can help. It is a fully hosted solution that can spin up a variety of Cardano environments. Cardano is fully open source, so you can install and run Cardano components locally or in a cloud environment. For this book, we will use `Demeter.run` to focus more on the concepts and application logic and spend less time on environment setup and configuration.

To set up an environment to be used for the examples in this book, follow these steps:

1.  Go to [https://demeter.run/](https://demeter.run/)
2.  Start a free trial.
3.  Sign-up/login.
4.  Create an organization.
5.  Create a new project, as shown in *[Figure 5.9](#c05.xhtml#fig5_9)*. 
    
    ![](OEBPS/images/Figure-5.9.jpg)
    
    **Figure 5.9:** Demeter.run New Project
    
6.  You can start with a free tier, but depending on usage, you may need to move to a paid tier or buy additional DCUs. Each plan purchased is associated with a specific project.
    
    ![](OEBPS/images/Figure-5.10.jpg)
    
    **Figure 5.10:** Demeter.run Project View
    
7.  Select `ADD APIS` `&` `SERVICES`, as shown in *[Figure 5.10](#c05.xhtml#fig5_10)*.
8.  Scroll down and create a new workspace.
9.  Select “`Clone an existing repository`”.
10.  Paste the GitHub URL in the text box: `https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts.git`
11.  Keep the branch default as the main.
12.  Select Node.js as the toolchain.
13.  Select Workspace `small` size.
14.  Select the `Pre-prod` network.
15.  Select `Create` at the bottom of the page.
16.  If you scroll to the top of the page, you will see the workspace being provisioned and will be completed, as shown in *[Figure 5.11](#c05.xhtml#fig5_11).*
     
     ![](OEBPS/images/Figure-5.11.jpg)
     
     **Figure 5.11:** Demeter.run Project Provisioning
     
17.  Scroll down the page and `EDIT` Exposed Ports.
18.  Enter Name as `Next.js`.
19.  Enter Number `3000`.
20.  Select `Expose`.
21.  Scroll back up to the top of the page and select the VS code icon to launch the VS code editor.
22.  Authorize trusted access so you can use VS code web to edit your code.
23.  Select `Terminal` -> `New` `Terminal` to create a terminal window to execute commands on the common line, as shown in *[Figure 5.12](#c05.xhtml#fig5_12)*.
     
     ![](OEBPS/images/Figure-5.12.jpg)
     
     **Figure 5.12:** Visual Studio Code Web
     

# [Off-Chain Examples](#toc.xhtml#s105a)

This section will show two approaches to building the off-chain code for a simple vesting smart contract. Each approach will use Next.js for the application framework. For more information on Next.js, the reader is encouraged to check out the Next.js documentation at [https://nextjs.org/docs](https://nextjs.org/docs).

# [Helios](#toc.xhtml#s106a)

Helios is both an off-chain JavaScript/TypeScript SDK and an on-chain functional, strongly typed programming language. It prioritizes readability and ease of use for an optimal developer experience. One of the main advantages of Helios is that it is a single JavaScript file with no third-party libraries, which improves the auditability and transparency of the smart contract being executed.

# [Initialize](#toc.xhtml#s107a)

We will refer to the GitHub code examples with a fully functional end-to-end example to execute your first off-chain code. In the Visual Studio web setup in the prior section with a Demeter.run workspace, select a new Terminal window and perform the following steps:

`$ cd chapter_05/helios/vesting`

`$ nvm install 18.17.0`

`$ npm install`

`$ npm run dev`

This will start up Next.js and run on the default port of 3000. Ignore any prompts from Visual Studio about port forwarding, since we will access the port using the exposed port URL. You can go into the workspace on `Demeter.run` and select the URL for the exposed port to access the Next.js web application. In your browser, you should see something like *[Figure 5.13](#c05.xhtml#fig5_13)*.

![](OEBPS/images/Figure-5.13.jpg)

**Figure 5.13:** Helios Transaction Builder

Please ensure you have either `Eternl` (or Nami) browser wallet extensions installed on your Chrome browser before selecting a wallet. You may need to refresh the page if you just installed or enabled the browser wallet extension. On the `Helios Tx Builder` page, when a wallet is selected, the wallet will prompt the user to confirm if it is okay to connect to this site if has not already connected to it previously. Confirm ok, and then you will see the wallet balance of the selected wallet, as shown in *[Figure 5.14](#c05.xhtml#fig5_14)*.

![](OEBPS/images/Figure-5.14.jpg)

**Figure 5.14:** Helios Wallet Selector

# [Lock](#toc.xhtml#s108a)

In *[Figure 5.14](#c05.xhtml#fig5_14)*, you will notice a “`Lock UTXO`” button at the bottom of the screen. This button will create an off-chain transaction to lock 2 Ada and a Datum at a script address. Let’s look at the code required to submit an on-chain transaction in the following steps.

# [Step 1](#toc.xhtml#s109a)

To connect to the browser wallet API, we will create a `WalletConnector.tsx` component within the Next.js application. In *[Figure 5.15](#c05.xhtml#fig5_15)*, on lines 52 and 53, the code first confirms if the browser plugin exists. If yes, then it updates the `walletAPI` state variable on line 56 so that the rest of the application can access it.

![](OEBPS/images/Figure-5.15.jpg)

**Figure 5.15:** Wallet API[⁷](#c05.xhtml#ftn7)

# [Step 2](#toc.xhtml#s110a)

Once we have access to the `walletAPI`, we can query the wallet for available UTXOs and change the address, as seen on lines 89 and 92 in *[Figure 5.16](#c05.xhtml#fig5_16)*. Helios uses a `walletHelper` class that wraps the `walletAPI` object to provide convenience functions and automatic conversions to Helios data types.

![](OEBPS/images/Figure-5.16.jpg)

**Figure 5.16:** Helios WalletHelper[⁸](#c05.xhtml#ftn8)

Next, we must compile the Plutus script to confirm the script address. This can be done via client-side JavaScript, as seen on line 104 in *[Figure 5.17](#c05.xhtml#fig5_17)*. On line 107, we can see how easy it is to import the Datum structure from the on-chain code and create the appropriate Datum off-chain. Next, we construct the UTXO output on lines 113 to 117 using the script address and the amount of Lovelace (2 Ada), and attach the Datum as an inline datum.

![](OEBPS/images/Figure-5.17.jpg)

**Figure 5.17:** Helios Program[⁹](#c05.xhtml#ftn9)

# [Step 3](#toc.xhtml#s111a)

The last step before we sign the transaction is to get the current network parameters, including the current epoch, cost model, max `tx` size, and more. This is needed for internal validation of the script while it is being constructed. In this example, we are simply sending (locking) Ada at the script address, so we do not need to evaluate the Plutus script. We will, however, evaluate the Plutus script in the next chapter on *Validators*. On line 124 in *[Figure 5.18](#c05.xhtml#fig5_18)*, the transaction is finalized, which balances the transaction inputs and outputs and returns any change to the wallet if needed. Once the transaction has been finalized, we ask the wallet to prompt the user to sign the transaction. The fully signed transaction is submitted to the network on line 131.

![](OEBPS/images/Figure-5.18.jpg)

**Figure 5.18:** Helios Submit Transaction[^(10)](#c05.xhtml#ftn10)

The user is prompted to sign the transaction using the `Eternl` wallet, as shown in *[Figure 5.19](#c05.xhtml#fig5_19)*.

![](OEBPS/images/Figure-5.19.jpg)

**Figure 5.19:** Eternl Wallet Sign Transaction

After successfully signing the transaction with the browser wallet, a transaction hash (`TxId`) will be shown with a link to a blockchain explorer, as shown in *[Figure 5.20](#c05.xhtml#fig5_20)*.

![](OEBPS/images/Figure-5.20.jpg)

**Figure 5.20:** Transaction Successful

If we select the link to the blockchain explorer, we can see the transaction including the attached inline datum, as shown in *[Figure 5.21](#c05.xhtml#fig5_21)*.

![](OEBPS/images/Figure-5.21.jpg)

**Figure 5.21:** Blockchain Explorer[^(11)](#c05.xhtml#ftn11)

# [Lucid + Aiken](#toc.xhtml#s112a)

Lucid + Aiken combo has the advantage of broader adoption and usage within the Cardano community. The Aiken team has also been focused on excellent developer experience and has created several utilities to help the Smart Contract developer lifecycle. This section will focus on building an off-chain transaction using Lucid to lock a UTXO at an Aiken script address.

Unlike Helios, which has the option to compile a Plutus script at run-time, Aiken follows the more typical two-phase deployment process:

1.  Compile an Aiken script using the Rust-based Aiken compiler to generate artifacts such as the compiled Plutus script and script hash into a file known as a **blueprint**.
2.  The Lucid off-chain code reads the compiled script in the **blueprint** file and any contract parameters that may be required.

# [Blockfrost API](#toc.xhtml#s113a)

In our examples, we will use Blockfrost API to interact with the Cardano Preprod network. Therefore, you must obtain an API key and set it as an environment variable.

1.  Go to [https://blockfrost.io/](https://blockfrost.io/)
2.  Create a free account and create an API key for the Cardano Preprod network.

# [Initialize](#toc.xhtml#s114a)

For the Lucid off-chain code example, we will refer to the GitHub code that can be run with the following steps:

`$ cd chapter_05/aiken/vesting`

`$ nvm install 18.17.0`

`$ npm install`

`$ echo export NEXT_PUBLIC_BLOCKFROST_API=https://cardano-preprod.blockfrost.io/api/v0 >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_BLOCKFROST_KEY=your-blockfrost-API-key >> ~/.bashrc`

`$ source ~/.bashrc`

`$ npm run dev`

This will launch Next.js and provide the same experience we saw using the Helios Transaction Builder. For this chapter, the Aiken contract has already been pre-compiled, and we will discuss the Aiken installation and build steps in *[Chapter 6, Validators](#c06.xhtml).*

*[Figures 5.22](#c05.xhtml#fig5_22), [5.23](#c05.xhtml#fig5_23),* and *[5.24](#c05.xhtml#fig5_24)* show the blueprint file’s contents. It describes the Aiken Validator and the datum and redeemer data types.

![](OEBPS/images/Figure-5.22.jpg)

**Figure 5.22:** Aiken Blueprint Validator

![](OEBPS/images/Figure-5.23.jpg)

**Figure 5.23:** Aiken Blueprint Datum Definition

![](OEBPS/images/Figure-5.24.jpg)

**Figure 5.24:** Aiken Blueprint Redeemer Definition

# [Lucid Off-Chain Code](#toc.xhtml#s115a)

The `WalletConnect.tsx` component will get the `walletAPI` the same way as the Helios off-chain code example. The difference with Lucid is that it also needs to use a blockchain API provider such as `Blockfrost`. Once the provider has been created on lines 32-35 in *[Figure 5.25](#c05.xhtml#fig5_25),* the `walletAPI` is passed to it on line 118 in *[Figure 5.26](#c05.xhtml#fig5_26)*.

![](OEBPS/images/Figure-5.25.jpg)

**Figure 5.25:** Lucid Blockfrost Provider[^(12)](#c05.xhtml#ftn12)

The Datum is manually constructed, and the Plutus validator script is read from the blueprint file on lines 126 and 129, respectively, in *[Figure 5.26](#c05.xhtml#fig5_26)*. Finally, the transaction is built, signed, and submitted on lines 133, 139, and 142.

![](OEBPS/images/Figure-5.26.jpg)

**Figure 5.26:** Lucid Submit Transaction[^(13)](#c05.xhtml#ftn13)

***Tip:*** *If you only have 1 UTXO in your wallet, the balance may show 0 lovelace because your wallet has excluded it and reserved it for collateral. For Lucid, you must explicitly set collateral in your wallet. For Eternl, you can set collateral by going to the Wallet Settings tab, selecting the Collateral dropdown, and then pressing the Set Collateral button.*

# [Conclusion](#toc.xhtml#s116a)

We started the chapter with a walkthrough of the transaction lifecycle and the wallets typically used in Cardano. We then proceeded into off-chain transaction building using two different approaches: Helios and Lucid + Aiken. The same user experience was created for each approach to highlight the code differences between them. We also demonstrated how useful tools like `Demeter.run` are used for standing up a development environment and how you register your stake to a stake pool using a wallet. Looking ahead, we are ready to review the on-chain code and execute it as part of a transaction.

# [Points to Remember](#toc.xhtml#s117a)

*   The transaction lifecycle involves building, signing, and submitting.
*   Transactions are serialized when submitted to the network using the CBOR format.
*   Wallets are the gateway to the blockchain and Smart Contracts.
*   A seed phrase is used to generate a private key.
*   A Testnet faucet is used to get test Ada (`tAda`) for the preview and pre-prod networks.
*   Address derivation is used to derive multiple addresses using the same private key.
*   Staking from a wallet will submit a stake registration and stake pool delegation certificate.
*   CIP-30 is a Cardano standard for connecting to browser extension wallets.
*   Demeter Run is an on-demand hosting platform for Cardano environments.
*   Helios is both an off-chain and on-chain library.
*   Helios and Lucid can be used in a client browser.
*   Blueprints are created during the Aiken build process and contain the compiled script, metadata, and type definitions for the Datum and Redeemer.

# [Multiple Choice Questions](#toc.xhtml#s118a)

1.  What is required to delegate to a stake pool? 
    1.  Stake pool delegation certificate
    2.  Withdraw certificate
    3.  Use a wallet
    4.  Stake registration certificate
2.  Which statement is true regarding a receiving and a change address? 
    1.  Both are internal addresses
    2.  One is an internal and the other is a variable
    3.  One is external and the other is internal
    4.  Both are external addresses
3.  What CIP among the following is a Cardano browser wallet connection standard? 
    1.  CIP-22
    2.  CIP-42
    3.  CIP-30
    4.  CIP-32
4.  What is used when generating a private key? 
    1.  Network
    2.  Seed phrase
    3.  Password
    4.  None of the above
5.  What is the Aiken blueprint used for in Lucid? 
    1.  UTXOs locked at a script address
    2.  Current Epoch
    3.  Compiled Plutus script and parameters
    4.  ADA price

# [Answers](#toc.xhtml#s119a)

1.  a
2.  c
3.  c
4.  b
5.  c

# [Questions](#toc.xhtml#s120a)

1.  What are the advantages and disadvantages of Single Address Mode wallets?
2.  Can Helios or Lucid + Aiken be used in a server-side model?
3.  What other languages and frameworks can you use to write Cardano off-chain code?
4.  Why are Aiken blueprints helpful?
5.  Are seed phrases required to make a private key?

# [Key Terms](#toc.xhtml#s121a)

*   **Assembled Transaction**: Create a transaction with inputs, outputs, Datums, and Redeemers.
*   **Account Abstraction**: Create a view or model of an account with a balance and transaction history.
*   **Full Node:** A Cardano node and does not use any third-party service to look up transactions on the blockchain.
*   **Seed Phrase**: Used to help generate a private key.
*   **Hierarchy for Deterministic Walle**t: Used to derive multiple addresses from the same private key.
*   **Single Address Mode:** Reuses the same network address.
*   **Auditability:** The ability to confirm that the smart contract has been audited.
*   **Transparency:** How to ensure the smart contract being executed is the correct one.
*   **WalletAPI:** JavaScript object to interact with CIP-30 compliant browser wallet.
*   **Blockfrost:** An API service provided to query the Cardano blockchain.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c05.xhtml#ftn1a) [https://www.cardanocube.com/cardano-ecosystem-interactive-map](https://www.cardanocube.com/cardano-ecosystem-interactive-map)

[²](#c05.xhtml#ftn2a) [https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)

[³](#c05.xhtml#ftn3a) [https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)

[⁴](#c05.xhtml#ftn4a) [https://book.world.dev.cardano.org/environments.html](https://book.world.dev.cardano.org/environments.html)

[⁵](#c05.xhtml#ftn5a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-1852](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1852)

[⁶](#c05.xhtml#ftn6a) [https://cips.cardano.org/cips/cip30/](https://cips.cardano.org/cips/cip30/)

[⁷](#c05.xhtml#ftn7a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_05/helios/vesting/components/WalletConnector.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/components/WalletConnector.tsx)

[⁸](#c05.xhtml#ftn8a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_05/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/pages/index.tsx)

[⁹](#c05.xhtml#ftn9a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_05/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/pages/index.tsx)

[^(10)](#c05.xhtml#ftn10a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_05/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/helios/vesting/pages/index.tsx)

[^(11)](#c05.xhtml#ftn11a) [https://preprod.cexplorer.io/tx/32a447855aa33edd50454eb897054a5c89b8cea1019e958a340c3f03302daf3f](https://preprod.cexplorer.io/tx/32a447855aa33edd50454eb897054a5c89b8cea1019e958a340c3f03302daf3f)

[^(12)](#c05.xhtml#ftn12a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_05/aiken/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/aiken/vesting/pages/index.tsx)

[^(13)](#c05.xhtml#ftn13a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_05/aiken/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_05/aiken/vesting/pages/index.tsx)

# [CHAPTER 6](#toc.xhtml#c06)

# [Validators](#toc.xhtml#c06)

# [Introduction](#toc.xhtml#s122a)

This chapter will examine what a validator is and why they are so important. We will show how to spend UTXOs locked at a validator script address and how to access data provided in a Redeemer and Datum. Next will be a deep dive into understanding the `ScriptContext` and how it is used to access inputs and outputs associated with a transaction. The chapter will also review code examples using two different approaches: Helios and Lucid + Aiken.

# [Structure](#toc.xhtml#s123a)

In this chapter, we will discuss the following topics:

*   Validators
*   Helios 
    *   Helios On-Chain Validator
    *   Helios Off-Chain Unlock
    *   Helios Off-Chain Cancel
*   Lucid + Aiken 
    *   Aiken On-Chain Validator
    *   Lucid Off-Chain Unlock
    *   Lucid Off-Chain Cancel

# [Validators](#toc.xhtml#s124a)

Validators are fundamental to Cardano Smart Contracts because they specify the on-chain conditions required to spend a UTXO locked at a script address. Once a validator is on-chain, it is immutable where code becomes “*law*”. A typical use case for validators is a vesting contract where funds are locked into a contract until the specific condition(s) are met. We will further build on our vesting example in the upcoming chapters and look at both the on-chain and off-chain codes. Validators consist of two components: the on-chain code that defines the rules and logic, and the off-chain code that creates and submits the transaction.

# [Helios](#toc.xhtml#s125a)

We first saw how to build an off-chain transaction using Helios in *[Chapter 5, Transaction Builder](#c05.xhtml)*. In this chapter, we will first look at the code to build the on-chain validator and then the off-chain code required to spend a UTXO locked at the script address. The Helios language for on-chain code is a strongly typed, functional programming language with similar code quality benefits from languages like Haskell or Aiken. The Helios compiler, however, is written in JavaScript and has the unique advantage of compiling at run-time using only JavaScript. This makes the setup and installation trivial since all you need is a recent version of Node.js, which is widely available on many operating systems.

# [Helios On-Chain Validator](#toc.xhtml#s126a)

The first line of a Helios on-chain validator specifies the purpose of the Plutus script. In this case, it is a `spending` script, and the name of the script is called `vesting.` In *[Figure 6.1](#c06.xhtml#fig6_1)*, on line 7, a Datum is defined as a `struct` with an` owner` variable using a `PubKeyHash` data type. This will be stored on-chain within a UTXO locked at the script address. We previously saw an example of this type of Datum in *[Chapter 4, Plutus](#c04.xhtml), [Figure 4.5](#c04.xhtml#fig4_5)*. On line 15 in *[Figure 6.1](#c06.xhtml#fig6_1)*, there is a Redeemer with an `enum` data type that contains two elements: `Cancel` and `Claim`. The `Claim` element has a `msg` variable that is used to pass a message to the validator at runtime.

![](OEBPS/images/Figure-6.1.jpg)

**Figure 6.1:** Helios On-Chain Validator Declarations[¹](#c06.xhtml#ftn1)

**Note**: When running locally, a Helios Visual Studio Code extension (`ext:hl`) is available for syntax highlighting. For Visual Studio Web, you must associate the `.hl` extension with C #.

On line 23 in *[Figure 6.2](#c06.xhtml#fig6_2)*, a **contract parameter** `MESSAGE` is declared that will be hard coded into the Plutus script. A **contract parameter** is a UPLC value that precedes the main validator function and can be updated dynamically at compile time or run-time if required.

![](OEBPS/images/Figure-6.2.jpg)

**Figure 6.2:** Helios On-Chain Validator Body[²](#c06.xhtml#ftn2)

The main validator function is defined on line 26 in *[Figure 6.2](#c06.xhtml#fig6_2).* We can see that three parameters, `Datum`, `Redeemer`, and `ScriptContext`, are passed to the main function. A validator may use none or any of these arguments depending on the validator logic. We have already discussed `Datum` and `Redeemer` in *[Chapter 4, Plutus](#c04.xhtml)*, so we will look into the `ScriptContext` in more detail. The `ScriptContext` includes the script purpose and all information related to the submitted transaction, except for **auxiliary data (metadata)**.

As we recall from *[Chapter 3, Transactions](#c03.xhtml)*, a script purpose is specified in the redeemer for each UTXO locked at a script address. Therefore, the four script purposes that may be used in the `ScriptContext` are as follows:

*   `Spending`: used for validating the spending of a UTXO locked at a script address.
*   `Minting`: used for minting or burning native tokens.
*   `Certifying`: used for stake key registration and delegating stake to a stake pool.
*   `Rewarding`: used for withdrawing staking rewards.

In *[Figure 6.2](#c06.xhtml#fig6_2)*, line 27, we define a local variable `tx`, which gets all of the transaction information from the current transaction being executed. This will then be used to extract the required signers of this transaction. Next, we use a `switch` statement on the Redeemer to execute different codes based on the value of the Redeemer. If the Redeemer is a `Cancel`, then we look at the required signatures in the transaction to see if they match the public key hash in the datum. If this is true, the validator allows the owner to do whatever he wants with this UTXO. If the Redeemer is a `Claim,` then we return `true` if the message in the redeemer matches the contract parameter `MESSAGE` value. If the Redeemer does not match either a `Cancel` or `Claim` or returns a false value, the validator will return` false` and the transaction will fail.

# [Helios Off-Chain Unlock](#toc.xhtml#s127a)

First, we will create an `Unlock.tsx` component that will allow the user to enter the text for the Redeemer and select a button to build the unlock transaction, as shown in *[Figure 6.3](#c06.xhtml#fig6_3)*.

![](OEBPS/images/Figure-6.3.jpg)

**Figure 6.3:** Unlock UI Component[³](#c06.xhtml#ftn3)

Then, we create the unlock function in our main` index.tsx` page that takes the Redeemer parameter and builds the transaction. The unlock function in *[Figure 6.4](#c06.xhtml#fig6_4)* is similar to the lock function, but we need to get a receiving address on line 171 to send the unlocked funds. On line 186, we attach the validator script to the transaction to be included as a script witness.

![](OEBPS/images/Figure-6.4.jpg)

**Figure 6.4:** Unlock Function Vesting Program[⁴](#c06.xhtml#ftn4)

Next, in *[Figure 6.5](#c06.xhtml#fig6_5),* we need to get a UTXO locked at the script address on line 189 and construct the Redeemer on line 193. In Helios, we can simply import the Redeemer type from the on-chain code and generate the UPLC code with the `_toUplcData()` function. We then add the UTXO input and the Redeemer on line 198, which will be linked together as a Redeemer witness. A UTXO output on line 206 is also created for 2 Ada to be sent to the receiving address once the UTXO locked at the script address is spent.

![](OEBPS/images/Figure-6.5.jpg)

**Figure 6.5:** Unlock Function Inputs and Outputs[⁵](#c06.xhtml#ftn5)

The `getVestingUtxo` function on line 189 makes a network call to a Next.js API created to query the blockchain for UTXOs at the script address. The Next.js API uses `Blockfrost`, a third-party Blockchain API provider, and is executed on the server. There are other providers and approaches to querying the Cardano blockchain, such as Maestro, Ogmios, and Koios. We will review other blockchain API providers in *[Chapter 8, Tooling](#c08.xhtml)*. The advantage of using the `Blockfrost` API server-side is that it avoids API key leakage when calling the API directly from the browser. Additionally, this avoids network calls to a different domain, which can result in browser CORS errors. *[Figure 6.6](#c06.xhtml#fig6_6)* shows the code of the Next.js `vestingUtxo` API that is called by the function `getVestingUtxo` in `index.tsx`.

![](OEBPS/images/Figure-6.6.jpg)

**Figure 6.6:** getVestingUtxo API[⁶](#c06.xhtml#ftn6)

The remainder of the unlock function is the same as the lock function, which assembles, signs, and submits the transaction to the network. The new UI with the Unlock button and the Redeemer message input is shown in *[Figure 6.7](#c06.xhtml#fig6_7)*.

![](OEBPS/images/Figure-6.7.jpg)

**Figure 6.7:** Helios Unlock UTXO

# [Off-Chain Cancel](#toc.xhtml#s128a)

We create a `Cancel.tsx` component and a cancel function inside `index.tsx`, which will be almost identical to the `Lock.tsx` component and the `unlock` function. There are only a few changes between the unlock and the cancel function. Can you spot the differences in *[Figure 6.8](#c06.xhtml#fig6_8)*?

![](OEBPS/images/Figure-6.8.jpg)

**Figure 6.8:** Helios Cancel UTXO[⁷](#c06.xhtml#ftn7)

One difference is that we must explicitly add the required signer for the transaction. The `.addSigner()` function, on line 294, will add the wallet’s public key hash to the transaction and include it as a required signer. The Cardano Node will ensure that any required signers have a corresponding valid signature in the witness set. The on-chain code then looks up the public key hash in the list of required signers to see if there is a match.

# [Test Drive](#toc.xhtml#s129a)

To run the demo, you need to execute the following commands; unless you change the version number or the `vesting` script, the validator script address will be the same for everyone:

`$ cd chapter_06/helios/vesting`

`$ npm install`

`$ echo export BLOCKFROST_KEY=your-blockfrost-API-key >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_ENV="dev" >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_HOST="demeter-run-host" >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_PROTOCOL="https" >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_PORT="" >> ~/.bashrc`

`$ source ~/.bashrc`

`$ npm run dev`

You should now be able to access the application using the exposed port URL. You can lock the 2 Ada and either claim (unlock) using the correct Redeemer value or cancel it. *[Figure 6.9](#c06.xhtml#fig6_9)* shows a successful transaction claiming the 2 Ada using the correct Redeemer value.

![](OEBPS/images/Figure-6.9.jpg)

**Figure 6.9:** Helios Vesting Claim[⁸](#c06.xhtml#ftn8)

# [Aiken](#toc.xhtml#s130a)

Aiken is a functional programming language with a compiler written in Rust, and we will compile an Aiken script using the `aiken build` command. This generates the compiled Plutus code and a **blueprint** file containing metadata and type definitions. To install Aiken in your `Demeter.run` workspace, you first need to download the installer:

`$ curl -sSfL https://install.aiken-lang.org | bash`

`$ echo export PATH=:/config/.aiken/bin:$PATH >> ~/.bashrc`

`$ source ~/.bashrc`

Then, run the following command:

`aikup`

With `aiken` installed, you can use the help switch to see the following available options:

`$ aiken --help`

`Cardano smart contract language and toolchain`

`Usage: aiken <COMMAND>`

`Commands:`

`new         Create a new Aiken project`

`fmt         Format an Aiken project`

`build       Build an Aiken project`

`address     Compute a validator's address`

`check       Type-check an Aiken project`

`docs        Build the documentation for an Aiken project`

`add         Add a new project package as dependency`

`blueprint   Commands for working with Plutus blueprints`

`packages    Managing project dependencies`

`tx          Commands for working with transactions`

`uplc        Commands for working with untyped Plutus-core`

`completion  Generates shell completion scripts`

`help        Print this message or the help of the given subcommand(s)`

You can create a new project with the following command:

`aiken new aiken-lang/new-project`

This will create the following project files and folders:

`└── new-project`

`├── aiken.toml`

`├── lib`

`│   └── new-project`

`├── README.md`

`└── validators`

`aiken.toml` contains information about your project, including libraries and the GitHub repo. The validators folder contains the on-chain Aiken source code, and the lib directory contains any project libraries needed or created for this project. You can run a quick test to confirm everything is installed correctly by executing `aiken build` and `aiken check` inside the new-project directory.

In the examples in this book, we place all of the Aiken on-chain validator code and artifacts in the `contracts` directory within each chapter project(s). For example:

`chapter_06/aiken/vesting/contracts`

If you want to learn more about setup and installation tasks including IDE language configurations, please refer to the Aiken online documentation.[⁹](#c06.xhtml#ftn9)

# [Aiken On-Chain Validator](#toc.xhtml#s131a)

Now, we are ready to look at our first Aiken validator script, as shown in *[Figure 6.10](#c06.xhtml#fig6_10)*:

![](OEBPS/images/Figure-6.10.jpg)

**Figure 6.10:** Aiken On-Chain Validator Declarations[^(10)](#c06.xhtml#ftn10)

The first 5 lines, in *[Figure 6.10](#c06.xhtml#fig6_10),* are the explicit import of classes we will use, followed by the Datum and Redeemer types. The Datum includes a Hash object, which contains a `Blake2b_224` and `VerificationKey` object. It should be noted that this is stored on-chain as a single `ByteArray` representing the public key hash. On line 15, the Redeemer contains two conditions (Cancel and Claim) to spend the UTXOs locked at this script address. The Claim redeemer also contains a `msg` payload using the `ByteArray` data type. On line 21, we hard-coded the “`Hello World!`” message as a script constant.

Next, in *[Figure 6.11](#c06.xhtml#fig6_11)*, we define the validator function on line 23 and create the vesting function with the `Datum`, `Redeemer`, and `ScriptContext` as arguments:

![](OEBPS/images/Figure-6.11.jpg)

**Figure 6.11:** Aiken On-Chain Validator Body[^(11)](#c06.xhtml#ftn11)

On line 26, we determine the type of Redeemer provided for a particular transaction. In the case of Cancel, the code on line 29 looks through the list of required signers and confirms if there is a public key hash matching the public key hash in the datum. If true, then the validator evaluates to true and allows the spending of the UTXO locked at the script address. If the Redeemer is a Claim, we compare the `msg` payload to the hard-coded message constant on line 32. If there are no matches for the Redeemer, then the validator will fail and not allow the spending of the UTXO locked at the script address.

# [Lucid Off-Chain Unlock](#toc.xhtml#s132a)

We will create the same `Unlock.tsx` component that we did with Helios and an `unlock function` in `index.tsx`. We need to create a Redeemer for the unlock function but don’t need to create a Datum since it is already part of the UTXO we want to spend. The Redeemer on line 172, in *[Figure 6.12](#c06.xhtml#fig6_12),* creates a Plutus Data object corresponding to the UPLC Datatypes we saw in *[Chapter 4, Plutus](#c04.xhtml).* In this case, we are creating a `Constr` at index 1, containing a hexadecimal-encoded string. When the script is evaluated, this hexadecimal-encoded string will be converted into the Redeemer Claim ByteArray payload. We specify an index of 1 because the Redeemer `Cancel` was the first Redeemer defined in the Plutus script with an index of 0. The next Redeemer in order will have an index of 1, the Claim Redeemer.

![](OEBPS/images/Figure-6.12.jpg)

**Figure 6.12:** Lucid Off-Chain Unlock[^(12)](#c06.xhtml#ftn12)

On line 175, the UTXOs locked at the script address are obtained by calling the` lucid.utxosAt` function, which uses the Blockfrost API to query the blockchain. Next, we build the transaction and specify the input UTXO on line 182 and the Validator script on line 183. The lucid transaction can now be assembled using the `.complete()` method. There is a lot of activity behind the scenes to assemble and finalize a transaction. We will focus on the more commonly used `lucid tx` methods to build and submit a transaction. Once the transaction has been finalized, the wallet will ask the user to sign it and submit it to the network.

# [Lucid Off-Chain Cancel](#toc.xhtml#s133a)

Lastly, we will create a new `Cancel.tsx` component and a cancel function in` index.tsx`. The `Cancel.tsx` component is almost identical to the Lock.tsx component, the main difference being the required signatures in the transaction on line 226 in *[Figure 6.13](#c06.xhtml#fig6_13)*. This is needed because the on-chain code looks to see if the required public key hash matches the public key hash stored in the datum.

![](OEBPS/images/Figure-6.13.jpg)

**Figure 6.13:** Lucid Off-Chain Cancel[^(13)](#c06.xhtml#ftn13)

# [Test Drive](#toc.xhtml#s134a)

To try out the example, run the following steps:

`$ cd chapter_06/aiken/vesting/contracts`

`$ aiken build`

`$ cd ..`

`$ echo export NEXT_PUBLIC_BLOCKFROST_API=https://cardano-preprod.blockfrost.io/api/v0 >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_BLOCKFROST_KEY=your-blockfrost-API-key >> ~/.bashrc`

`$ source ~/.bashrc`

`$ npm install`

`$ npm run dev`

# [Conclusion](#toc.xhtml#s135a)

We looked at our first on-chain Plutus validators built using the languages Helios and Aiken. We then looked at the corresponding off-chain code to execute these validators using Helios and Lucid, respectively. We looked at how to initialize a project using Aiken and how to compile an Aiken Smart Contract. Then, the `ScriptContext` was examined and how it contains key transaction information such as inputs, outputs, script purpose, and more. We also looked at the Datum and Redeemer definitions on-chain and how they are accessed during script execution. The creation of an Off-chain Redeemer and required signers was also demonstrated in the examples. The next chapter will dive into Minting Policies, parameterized smart contracts, and minting native tokens.

# [Points to Remember](#toc.xhtml#s136a)

*   Helios is used for both on-chain and off-chain code.
*   Helios on-chain code can be compiled on the fly because the Helios compiler is written in JavaScript.
*   Aiken is used for on-chain code and is compiled prior to run-time using the rust-based` aiken` compiler.
*   Aiken also generates a blueprint file that contains Plutus script metadata and type definitions.
*   The `aiken` program has several convenient utility functions that may be used during smart contract development.
*   Lucid is used for the off-chain code and is frequently used in combination with Aiken.
*   Lucid and Helios off-chain code rely on a blockchain API provider to obtain blockchain information such as UTXOs locked at a script address.
*   The Helios off-chain code can import the Helios on-chain code, allowing for sharing type definitions.
*   Helios off-chain code does not require any third-party libraries and is consolidated into one JavaScript file.
*   When spending a UTXO, a Redeemer must be provided for each UTXO locked at a script address.
*   A required signer must include a signature in the witness set for a transaction.

# [Multiple Choice Questions](#toc.xhtml#s137a)

1.  What is required to spend a UTXO at a Plutus script address? 
    1.  Datum Only
    2.  Minting Script
    3.  Datum and Redeemer
    4.  Epoch
2.  What activity must occur during transaction finalization? 
    1.  Balance the inputs and the outputs
    2.  Specify the Redeemer
    3.  Specify the Datum
    4.  Sign the transaction
3.  How does off-chain code access blockchain data? 
    1.  Makes a direct RPC call to the node
    2.  Usually not needed
    3.  Uses an API provider (for example, `Blockfrost`, `Ogmios`, and more)
    4.  CIP-30 wallet connector
4.  What is the typical sequence for on-chain code execution? 
    1.  Local evaluator, Node for `tx` submission, All blockchain nodes
    2.  All blockchain nodes only
    3.  Node for `tx` submission only
    4.  Local evaluator then All blockchain nodes
5.  What are the four different script purposes? 
    1.  ` Validate`, `Mint`, `Reward`, `Cert`
    2.  ` Spend`, `Burn`, `Cert`, `Reward`
    3.  ` Spend`, `Mint`, `Burn`, `Context`
    4.  ` Spend`, `Mint`, `Cert`, `Reward`

# [Answers](#toc.xhtml#s138a)

1.  c
2.  a
3.  c
4.  a
5.  d

# [Questions](#toc.xhtml#s139a)

1.  How could you improve the auditability of a smart contract that is executed?
2.  Why are most smart contracts deployed before run-time?
3.  What is the role of `Datum` and `ScriptData` hashes?
4.  Why must you always specify a redeemer when executing a smart contract?
5.  How are the Plutus cost models retrieved by off-chain frameworks such as Lucid and Helios?
6.  What is the CDDL specification identifier for the required signers of a transaction?

# [Key Terms](#toc.xhtml#s140a)

*   **Auxiliary Data:** Metadata about the transaction where only the metadata hash is stored on-chain.
*   **Blake2b:** A hash algorithm that generates a hash based on an input of bytes.
*   **Blueprint:** An Aiken-generated file that contains Plutus script metadata and type definitions.
*   `Blockfrost`**:** An API Provider for blockchain data.
*   `ByteArray`**:** An array of bytes encoded using a hexadecimal format.
*   **Contract Parameter:** A variable on-chain that can be updated during compilation or at run-time.
*   `Enum`**:** A data type that can be enumerated and used in a switch/case statement.
*   `ScriptContext`**:** Contains all information about the current transaction being evaluated except for Auxiliary Data.
*   `Spending` **script:** Type of validator for spending UTXO locked at a script address.
*   `Switch` **Statement:** Used to evaluate different Enum combinations.
*   `VerificationKey`**:** The public key of the corresponding private key.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c06.xhtml#ftn1a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/helios/vesting/contracts/vesting.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl)

[²](#c06.xhtml#ftn2a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/helios/vesting/contracts/vesting.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl)

[³](#c06.xhtml#ftn3a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/helios/vesting/components/Unlock.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/components/Unlock.tsx)

[⁴](#c06.xhtml#ftn4a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx)

[⁵](#c06.xhtml#ftn5a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx)

[⁶](#c06.xhtml#ftn6a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/helios/vesting/pages/api/vestingUtxo.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/api/vestingUtxo.ts)

[⁷](#c06.xhtml#ftn7a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx)

[⁸](#c06.xhtml#ftn8a) [https://preprod.cexplorer.io/address/addr\_test1wp4gwgtnyp8grwhzjj47qy7k60hxfv9p2wymjcwkzgw6r9cp0ctvs/tx#data](https://preprod.cexplorer.io/address/addr_test1wp4gwgtnyp8grwhzjj47qy7k60hxfv9p2wymjcwkzgw6r9cp0ctvs/tx#data)

[⁹](#c06.xhtml#ftn9a) [https://aiken-lang.org/installation-instructions](https://aiken-lang.org/installation-instructions)

[^(10)](#c06.xhtml#ftn10a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/aiken/vesting/contracts/validators/vesting.ak](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak)

[^(11)](#c06.xhtml#ftn11a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/aiken/vesting/contracts/validators/vesting.ak](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak)

[^(12)](#c06.xhtml#ftn12a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/aiken/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx)

[^(13)](#c06.xhtml#ftn13a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_06/aiken/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx)

# [CHAPTER 7](#toc.xhtml#c07)

# [Minting](#toc.xhtml#c07)

# [Introduction](#toc.xhtml#s141a)

In this chapter, we will examine Cardano native assets and how they are different from tokens on Ethereum created using the ERC-20 and ERC-721 standards. We will discuss the concept of token bundles and how to optimize coin selection. Next, we will deep dive into how Cardano native tokens are minted and the differences between Non-Fungible Tokens (NFTs) and Fungible Tokens (FTs). We will also review the NFT and FT metadata standards CIP-25 and CIP-68 and how to implement them when minting. Finally, we will introduce the Cardano Token Registry and explore its benefits for the end-user wallet experience. We will put this all together with a working minting policy use case and demo.

# [Structure](#toc.xhtml#s142a)

In this chapter, we will discuss the following topics:

*   Tokens 
    *   Native Assets
    *   Token Bundles
*   Minting Policy 
    *   Fungible Tokens
    *   Non-Fungible Tokens
    *   Token Registry
    *   NFT Metadata Standards 
        *   CIP-25
        *   CIP-68
*   Coin Selection 
    *   Minting Policy Use Case

# [Tokens](#toc.xhtml#s143a)

On March 1st, 2021, as part of the Mary hard fork, Cardano was upgraded to a multi-asset ledger. This was a significant event because custom native tokens can now leverage the secure, peer-reviewed, ledger rules used for Ada, Cardano’s native currency. This is much different than in Ethereum, which requires a custom ledger code for each token following either the ERC-20 or ERC-721 standards. Additionally, there are no requirements for special fees or additional event-handling logic to track transactions associated with a Cardano native asset.[¹](#c07.xhtml#ftn1)

# [Native Assets](#toc.xhtml#s144a)

A Native asset is a custom token on Cardano that operates in the same manner as the base layer currency, Ada. The only requirement is that a native asset must always have a minimum amount of Ada included. CIP-55[²](#c07.xhtml#ftn2) simplified the minimum Ada calculation and used the number of CBOR bytes of a UTXO, which includes all of the native assets locked in a particular UTXO.

Assets represent value such as 1 Ada (1,000,000 lovelace) or 100 gold coins. Each asset token is always made of three components^(\*):

*   **Policy Identifier (ID):** A unique identifier that is the hash of the Minting Policy Plutus script.
*   **Asset Name:** An immutable token name on-chain for a specific minting policy.
*   **Quantity**: The accounting unit.

^(\*) Ada is the only asset token where the Policy ID is an empty string.

# [Token Bundles](#toc.xhtml#s145a)

A token bundle is a collection of tokens that may be the same or different from each other. Token bundles organize tokens into a particular structure that properly defines the Minting Policy ID, Token Name, and quantity of each of the tokens in a **collection**. Let’s look at the following example:

`{`

`"lovelace": "1646420",`

`"assets": {`

`"Game Monetary Policy ID": {`

`"Gold": "100",`

`"Silver": "1,000",`

`"Bronze": "10,000",`

`},`

`"Game Character Policy ID": {`

`"Dracula": "1"`

`}`

`}`

In the preceding example, we have a collection of tokens that each represents value locked at a UTXO. The `Game Monetary Policy ID` is a unique Minting Policy ID, and the player holds a collection of 100 Gold, 1,000 Silver, and 10,000 Bronze tokens. So, a user would be able to spend up to 100 Gold, up to 1,000 Silver, and up to 10,000 Bronze tokens in a single transaction. Since this player only has 1 Dracula token, they can only send (spend) 1 Dracula token to another player. There always needs to be a minimum amount of Ada in a token bundle, and in this case, it is 1,646,420 lovelace.

# [Minting Policy](#toc.xhtml#s146a)

There are two different types of minting policies on Cardano:

*   A native script minting policy that is created using the `cardano-cli` tool and uses a private and public key.
*   A minting policy that is a plutus script.

The `cardano-cli` approach[³](#c07.xhtml#ftn3) was first used before smart contracts were introduced, but this approach is still used today because it is a proven and secure technique. Using `cardano-cli` with native script provides the ability to specify time-locks and multi-signature conditions.[⁴](#c07.xhtml#ftn4)

A minting policy is written in a similar way to how we would write a validator script. The difference between a validator script and a minting policy is that a minting policy uses a `minting` script purpose and does not use a datum. The `minting` script purpose allows the minting policy to mint or burn native tokens as part of a transaction. Only the conditions to mint or burn are defined in the custom logic of a minting policy.

# [Fungible Tokens](#toc.xhtml#s147a)

You may want to create a **monetary policy** with a fixed supply of 1,000,000 tokens. The minting policy would only allow a one-time minting of 1,000,000 tokens, with each token having the same name. This allows each to token be fungible or tradable with each other, similar to how fiat currency operates today.

# [Non-Fungible Tokens](#toc.xhtml#s148a)

A Non-Fungible Token (**NFT**) is where each token is unique and distinct. There are two approaches to making a unique token on Cardano.

*   **Option 1**: Time-lock, where a token can only be minted before a specific date and time.
*   **Option 2**: Minting Policy logic that checks for the existence of a UTXO in the input that has to be spent.

The second option is preferred because it leverages the unique properties of the Cardano UTXO architecture. Once a UTXO is spent, it can never be spent again, and there will not be another UTXO with the same hash. By hard coding this condition into the minting policy and also ensuring that only one token is minted, we guarantee that the token is unique. A time-lock approach was used before smart contract functionality was available, but this method is still used when creating large NFT collections.

# [Token Registry](#toc.xhtml#s149a)

The Token Registry[⁵](#c07.xhtml#ftn5) is used to store off-chain metadata for a minting policy ID and token name. A minting policy ID is a hexadecimal hash value, so it is helpful to have a mapping of human-readable information about a specific Minting Policy and token. The registry provides an API that wallets and other applications can use to look up a token image URL, decimal precision, and other metadata. With the adoption of CIP-68 increasing, the need for a centralized off-chain token registry will be phased out over time. For a step-by-step guide to register a token, please visit the following URL:

[https://github.com/cardano-foundation/cardano-token-registry/wiki](https://github.com/cardano-foundation/cardano-token-registry/wiki)

# [NFT Metadata Standards](#toc.xhtml#s150a)

When minting an NFT, you can take advantage of transaction metadata that can be included in any transaction on the Cardano network. The first Cardano metadata standard was documented in CIP-25[⁶](#c07.xhtml#ftn6), which specifies the standard fields for NFT metadata. A notable difference between the Ethereum ERC-721 token metadata is that CIP-25 metadata is linked to the minting transaction and not the minting policy. So, the process to look up the metadata using CIP-25 is to look at the original minting transaction for a particular minting policy.

# [CIP-25](#toc.xhtml#s151a)

The format for CIP-25 NFT metadata is illustrated in *[Figure 7.1](#c07.xhtml#fig7_1)*:

![](OEBPS/images/Figure-7.1.jpg)

**Figure 7.1:** CIP-25 NFT Metadata Format

The label 721 indicates that this is token metadata, and the format is flexible, allowing you to add additional elements as required. To test out and verify valid transaction metadata in production, you can use a tool like `Pool.pm` test metadata tool.[⁷](#c07.xhtml#ftn7)

# [CIP-68](#toc.xhtml#s152a)

The disadvantage of CIP-25 is that it is created with the original Mint transaction and is not updateable or accessible to a Plutus script. CIP-68[⁸](#c07.xhtml#ftn8) addresses this by using the concept of a reference token that is created at the same time when an **NFT** or **FT** is created. The reference token can be either locked at an unspendable script address to be immutable, or locked at a spending script address if there is a requirement for it to be updateable. The metadata is stored in a datum included with the reference token UTXO output. Therefore, it can be accessible to a Plutus script by reading the datum values. With the Vasil hard fork in September 2022, **reference inputs** were introduced that allowed a Plutus script to include a UTXO input as read-only and not have to spend it. Therefore, any number of transactions (even in parallel) can include a read-only CIP-68 reference token UTXO without any concurrency issues.

In *[Figure 7.2](#c07.xhtml#fig7_2)*, we can see how a mint transaction generates a user token and a reference token, which are linked using the same token name and minting policy ID. The token name is prefixed with 222 to indicate an NFT token, and 100 to indicate a reference token. For fungible tokens, the prefix of 333 is used. It should be noted that the reference token and the NFT or FT tokens do not need to be minted at the same time.

![](OEBPS/images/Figure-7.2.jpg)

**Figure 7.2:** CIP-68 Datum Metadata

In *[Chapter 9, Ticket Application Design](#c09.xhtml),* we will discuss the process of creating and using CIP-68 metadata datum in more detail, with a real-world example.

# [Coin Selection](#toc.xhtml#s153a)

Coin selection is the process of determining what UTXO inputs are required to cover the cost of the UTXO outputs, including network fees. There are a number of constraints that we need to be aware of during the coin selection process, which are as follows:[⁹](#c07.xhtml#ftn9)

*   The maximum size limit of a transaction is where each UTXO, either as an input or an output, increases the overall transaction size.
*   The accumulation of very small UTXOs (**dust**) that are unspendable because you can’t combine enough of them together to cover the transaction cost.
*   A UTXO cannot be partially spent; it must be fully spent as part of a transaction.

Therefore, the goal of a coin selection algorithm is to avoid **dust** and create usable UTXOs. Coin selection algorithm considerations apply to both Ada and native tokens. The most common approaches for coin selection are Largest-first and Random Improve.[^(10)](#c07.xhtml#ftn10) Largest-first selects UTXO inputs in the order from the largest value to the smallest value. The Random Improve algorithm uses two phases. The first phase cycles through a descending ordered list of UTXO inputs, and randomly selects UTXOs until the required amount of output value is obtained. In the second phase, the algorithm again chooses randomly from the descending order list of UTXO inputs until it is approximately twice the amount of output value. Coin selection is typically implemented by the wallet and/or the transaction builder framework. That said, it is important to understand the coin selection algorithms when selecting UTXO inputs. Also, you need to be aware that users may run into issues related to **dust** or UTXO fragmentation caused by too many UTXOs required as inputs.

# [Minting Policy Use Case](#toc.xhtml#s154a)

Next, we are going to look at a real-world use case for minting on the Cardano blockchain. In this example, we will use a minting policy to create a fixed number of tickets for an event.

Minting event ticket tokens have the following blockchain advantages, outlined in *[Table 7.1](#c07.xhtml#tab7_1)*:

 
| **Blockchain Feature** || **Who** || **Benefit** |
| Number of tickets minted is fixed and cannot be changed || Performer || Knows exactly how many tickets were issued for a particular event |
| Attendee || The value of a ticket cannot be diluted by additional tickets being created after the initial allocation |
| Minting and Cardano ledger rules || Attendee || If an attendee has a valid ticket, then this is a genuine ticket and cannot be fake |
| Seller || For secondary market sales, the ticket can be verified by examining the blockchain to confirm that it is a genuine ticket |
| Performer || The movement of tickets is recorded on the blockchain so it is easy to audit how many tickets have actually been sold or canceled (burned) |

**Table 7.1:** Minting Use Case Benefits

# [Helios On-Chain Minting Policy](#toc.xhtml#s155a)

The on-chain Helios minting policy on line 1, *[Figure 7.3](#c07.xhtml#fig7_3)*, states the purpose of the script as `minting` and the name of the script called` ticket.` There are two Redeemer conditions, Mint and Burn, on lines 7 and 8. The contract parameters on lines 11–16 will be updated dynamically at run-time. So, for now, they are initialized with dummy values and will be updated in the off-chain code.

![](OEBPS/images/Figure-7.3.jpg)

**Figure 7.3:** Helios On-Chain Minting Redeemer and Parameters[^(11)](#c07.xhtml#ftn11)

Next, in *[Figure 7.4](#c07.xhtml#fig7_4)*, we can see the main function contains the minting policy logic. First, note that only a `Redeemer` and `ScriptContext` are passed as arguments. On line 20, we create the `MintingPolicyHash` dynamically, which takes into account the contract parameters that have been passed into the script at run-time. We then create an `AssetClass` that will be used to verify what is minted. On line 25, we pull out the minted value that was part of this transaction. Now, we have the information we need to handle the Redeemer conditions.

![](OEBPS/images/Figure-7.4.jpg)

**Figure 7.4:** Helios On-Chain Minting Logic[^(12)](#c07.xhtml#ftn12)

On line 30, in *[Figure 7.4](#c07.xhtml#fig7_4),* we confirm that the token minted in the transaction matches the token name and amount in the contract parameters. Lines 31 and 32 check that the UTXO specified in the contract parameter is included in the inputs. Since a UTXO can only be spent once, the minting policy will only allow it to be minted once, which guarantees uniqueness. Finally, on line 38, we allow the burning as long as the token belongs to the minting policy and has a negative quantity.

# [Helios Off-Chain Mint](#toc.xhtml#s156a)

We will highlight the differences between the off-chain code in this example and the previous validator example was shown in *[Chapter 6, Validators](#c06.xhtml)*. On line 119 in *[Figure 7.5](#c07.xhtml#fig7_5)*, we create the minting policy program and then apply the contract parameters on lines 120–123. Only after the parameters have been applied, can we compile the script and attach it to the transaction on line 129. We also construct the Mint Redeemer on line 132, which uses the Redeemer type specified in the on-chain code.

![](OEBPS/images/Figure-7.5.jpg)

**Figure 7.5:** Helios Off-Chain Contract Parameters[^(13)](#c07.xhtml#ftn13)

In *[Figure 7.6](#c07.xhtml#fig7_6),* an array of tokens on line 136 uses the ticket name and qty passed in from the user input to create the assets that we will mint, as shown on lines 139–141. Next, we specify the tokens to mint in the transaction on line 145. We use the `MintingPolicyHash` from the compiled script and include both the tokens and the Redeemer created previously. We also create an output, where we send the minted ticket tokens to an `address` from the user input, as shown on lines 153–156.

![](OEBPS/images/Figure-7.6.jpg)

**Figure 7.6:** Helios Off-Chain Mint Tokens[^(14)](#c07.xhtml#ftn14)

In this minting use case, we also make use of transaction metadata following the CIP-25 standard. On line 160 in *[Figure 7.7](#c07.xhtml#fig7_7)*, we make a call to `generateMetadata`, which returns a JSON-like record for the data passed in the arguments. The `name, qty, utxoId,` and` utxoIdx` will be stored in the metadata and can be used to reconstruct the minting policy later if burning is required. The `mintingPolicyHash`,` name`,` description`, and` image` are used off-chain for displaying the token in wallets, dApps and blockchain explorers.

![](OEBPS/images/Figure-7.7.jpg)

**Figure 7.7:** Helios Off-Chain Metadata[^(15)](#c07.xhtml#ftn15)

# [Helios Off-Chain Burn](#toc.xhtml#s157a)

There may be a scenario requiring the burning of unsold ticket tokens. Since the Cardano ledger tracks and avoids any double spending of native assets, the burning of ticket tokens can only be done if the ticket tokens actually exist in the transaction inputs. Therefore, the only way to burn a token is to actually have possession of that token in your wallet, so it can be spent as a transaction input.

We will first look at line 230 in *[Figure 7.8](#c07.xhtml#fig7_8)*, which queries the blockchain to get the mint metadata for a particular token. As we recall, we need the token` name`,` qty`,` utxoId`, and `utxoIdx` as contract parameters to rebuild the correct minting policy. Now that we have the contract parameters, we can compile the script and attach it to the transaction. We also create a Burn Redeemer on line 246 that allows the burning of the ticket tokens accordingly.

![](OEBPS/images/Figure-7.8.jpg)

**Figure 7.8:** Helios Off-Chain Metadata Query[^(16)](#c07.xhtml#ftn16)

Lastly, we build the `MintingPolicyHash` from the `policyId` stored in the metadata and then add the token to burn by using a negative` qty` number on line 252, as shown in *[Figure 7.9](#c07.xhtml#fig7_9)*.

![](OEBPS/images/Figure-7.9.jpg)

**Figure 7.9:** Helios Off-Chain Burn Tokens[^(17)](#c07.xhtml#ftn17)

# [Aiken On-Chain Minting Policy](#toc.xhtml#s158a)

The Aiken on-chain minting policy uses `token_name, qty,` and `utxo_ref` as contract parameters that are applied during run-time on line 15, as shown in *[Figure 7.10](#c07.xhtml#fig7_10)*. Only the Redeemer and `ScriptContext` are passed to the ticket function, which contains the minting policy logic. On line 18, the expect statement is used to create a new binding for `policy_id` from the script `purpose`. On line 19, we deconstruct the Transaction type and pull out both the inputs and the minted value from the transaction. We then use the expect statement on line 22 to bind `asset_name` and `amount` with a tuple from the mint value and match the `policy_id`. Now we have all the information we need to execute the Redeemer conditions. On lines 31 and 32, we check that the input contains the `utxo_ref` that was passed in the contract parameter. On line 34, we confirm that the asset name and amount match what was provided as contract parameters. The Burn Redeemer on line 37 allows the burning of any negative amount as long as the `asset_name` within this script minting policy is included in the transaction.

![](OEBPS/images/Figure-7.10.jpg)

**Figure 7.10:** Aiken On-Chain Minting Policy[^(18)](#c07.xhtml#ftn18)

# [Lucid Off-Chain Mint](#toc.xhtml#s159a)

The Lucid off-chain code is very similar to the Helios off-chain code, and we will only show the differences between the two approaches. In particular, the way contract parameters are applied is different, as shown in *[Figure 7.11](#c07.xhtml#fig7_11)*. On line 89, a custom function takes in the contract parameters and then applies them to the Plutus minting policy script on line 96. The Plutus script is read from the blueprint file, which was generated from the `aiken build` command.

![](OEBPS/images/Figure-7.11.jpg)

**Figure 7.11:** Lucid Applied Contract Parameters[^(19)](#c07.xhtml#ftn19)

In *[Figure 7.12](#c07.xhtml#fig7_12)*, the validator (minting policy) is returned on line 132 using the `name`,` qty`, and `outRef` calculated from the UTXO in the wallet. On line 135, the `Redeemer` is manually constructed to match the `Redeemer` in the on-chain Aiken code. The `policyId` and `assetName` are constructed using the `validator` Script and `name`, respectively, on lines 138 and 139.

![](OEBPS/images/Figure-7.12.jpg)

**Figure 7.12:** Lucid Minting Policy ID and Asset Name[^(20)](#c07.xhtml#ftn20)

The last step is to generate the metadata on line 142, in *[Figure 7.13](#c07.xhtml#fig7_13),* and build the transaction on lines 150–160. The validator script, metadata, and minted assets are attached to the transaction on lines 153, 154, and 155 accordingly. Finally, the output is created to send the ticket tokens to the address provided by the user input on line 159.

![](OEBPS/images/Figure-7.13.jpg)

**Figure 7.13:** Lucid Minting Metadata[^(21)](#c07.xhtml#ftn21)

The Lucid-off chain Burn is similar to Mint, except that `mintAssets()` uses a negative quantity and has no metadata or transaction output.

# [Wallet Info](#toc.xhtml#s160a)

Since we are dealing with native assets, we modified the `WalletInfo` component to show both Lovelace and any native assets at the user’s wallet address. This requires calling the `Blockfrost` API to get the list of assets and then populating an array that will be displayed on the UI, as shown in *[Figure 7.14](#c07.xhtml#fig7_14)*.

![](OEBPS/images/Figure-7.14.jpg)

**Figure 7.14:** Lucid getWalletInfo[^(22)](#c07.xhtml#ftn22)

# [Setup](#toc.xhtml#s161a)

To set up the `Demeter.run` environment to run the Lucid + Aiken demo, please execute the following commands in a terminal window (if you have not already done so from *[Chapter 6, Validators](#c06.xhtml)*).

`$ echo export NEXT_PUBLIC_BLOCKFROST_API=https://cardano-preprod.blockfrost.io/api/v0 >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_BLOCKFROST_KEY=your-blockfrost-API-key >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_ENV="dev" >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_HOST="demeter-run-host" >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_PROTOCOL="https" >> ~/.bashrc`

`$ echo export NEXT_PUBLIC_PORT="" >> ~/.bashrc`

`$ source ~/.bashrc`

`$ npm install`

`$ npm run dev`

# [Demo](#toc.xhtml#s162a)

*[Figure 7.15](#c07.xhtml#fig7_15)* shows the new `WalletInfo` component with 100 “`Dog Show 1`” ticket tokens already at the wallet address.

![](OEBPS/images/Figure-7.15.jpg)

**Figure 7.15:** Lucid Wallet Info

To mint a new batch of tickets, the user enters the destination address, token name, token description, **IPFS** image content identifier, and quantity, as shown in *[Figure 7.16](#c07.xhtml#fig7_16):*

![](OEBPS/images/Figure-7.16.jpg)

**Figure 7.16:** Lucid Mint

After selecting the `Mint Ticket` button and signing the transaction with your wallet, as shown in *[Figure 7.16](#c07.xhtml#fig7_16)*, a transaction success message should appear.

![](OEBPS/images/Figure-7.17.jpg)

**Figure 7.17:** Lucid Mint Transaction Success

If you select the `TxId` link, you will be able to see the transaction on Preprod once it has been confirmed on the network. In *[Figure 7.18](#c07.xhtml#fig7_18)*, you can see that a new 150 `Dog Show 2` tokens were created and sent back to the wallet address.

![](OEBPS/images/Figure-7.18.jpg)

**Figure 7.18:** Cardano Explorer Mint Transaction Detail[^(23)](#c07.xhtml#ftn23)

We can also verify the metadata on the Cardano Explorer in *[Figure 7.19](#c07.xhtml#fig7_19)*:

![](OEBPS/images/Figure-7.19.jpg)

**Figure 7.19:** Cardano Explorer Mint Transaction Metadata[^(24)](#c07.xhtml#ftn24)

Next, we will try to burn (cancel) 20 tickets because they needed to make more room for the dogs at the event. The user needs to enter the Minting `Policy ID`, the `Token Name`, and the amount of tokens to burn, as shown in *[Figure 7.1](#c07.xhtml#fig7_1)*9\. This will only succeed if the user has the event tokens in their wallet.

![](OEBPS/images/Figure-7.20.jpg)

**Figure 7.20:** Lucid Burn Token

A successful transaction message should appear, and the transaction can be seen on the Cardano Explorer link. In *[Figure 7.21](#c07.xhtml#fig7_21)*, 20 ticket tokens have been burned, with only 130 remaining.

![](OEBPS/images/Figure-7.21.jpg)

**Figure 7.21:** Burn Token Transaction[^(25)](#c07.xhtml#ftn25)

The blockchain explorers and APIs can be queried to find the total number of assets in circulation, as shown in *[Figure 7.22](#c07.xhtml#fig7_22)*.

![](OEBPS/images/Figure-7.22.jpg)

**Figure 7.22:** Minting Policy Asset Accounting[^(26)](#c07.xhtml#ftn26)

# [Conclusion](#toc.xhtml#s163a)

We reviewed what a Cardano native asset is and how it is different from an Ethereum ERC-20 token. We explored the concept of token bundles and how they are used to group a collection of tokens together inside a UTXO. Next, we understood the role of the minting policy and how to mint Cardano native asset tokens. The differences between Non-Fungible Tokens (**NFT**s) and Fungible Tokens (**FT**s) were discussed, where **NFT**s represent a unique asset and **FT**s represent assets that are identical to each other. The CIP-25 and CIP-68 metadata standards were also reviewed with examples of what CIP-25 metadata looks like. We briefly discussed the role of the Token Registry, as well as the importance of using an optimal coin selection algorithm. We finished up the chapter by looking at a real-world use case involving minting ticket tokens for an event. The next chapter will focus on Cardano tooling used for blockchain development, queries, and monitoring.

# [Points to Remember](#toc.xhtml#s164a)

*   Cardano native assets use the Cardano ledger to prevent double spending of tokens.
*   A minting policy hash will be unique if a UTXO is used as a contract parameter and is spent in the mint transaction.
*   A token bundle includes one or more tokens and must always include a minimum amount of Ada.
*   Tokens are included in a UTXO and can be locked at a Base, Enterprise, or Plutus Script address.
*   A minting policy only controls the minting or burning of tokens.
*   A minting policy does not manage the ledger state of the token or the circulating supply.
*   An off-chain code is required to determine the circulating supply by examining all the mint and burn operations for a specific minting policy.
*   Non-fungible tokens (**NFT**s) are unique and distinct assets that are not interchangeable with each other.
*   Fungible Tokens (**FT**s) are identical and can be exchanged with each other.
*   CIP-25 is a metadata standard that is used when submitting a transaction.
*   CIP-68 uses a reference token and a datum value that can be either immutable or updateable, depending on the use case.
*   The Token Registry registers a minting policy and token name to provide metadata about the token, which is used by wallets, blockchain explorers, and exchanges.
*   Using a proper coin selection algorithm is important to avoid dust, which is a small amount of UTXOs that cannot be spent because the cost of doing so exceeds their combined value.

# [Multiple Choice Questions](#toc.xhtml#s165a)

1.  Which of the following statements is false? 
    1.  Cardano native tokens are identical to ERC-20 Tokens
    2.  Cardano native assets use the base ledger to avoid double spending
    3.  A Cardano minting policy typically uses less code than an ERC-20 contract
    4.  A Cardano minting policy is typically more secure than an ERC-20 contract
2.  How does a one-time Minting Policy create the initial circulating supply? 
    1.  Custom code inside the minting policy
    2.  Queries the Cardano ledger
    3.  Queries the minting policy metadata
    4.  None of the above
3.  How is CIP-25 metadata stored on-chain? 
    1.  As a hash value on-chain and included as auxiliary data as part of a transaction
    2.  In JSON format and stored fully on-chain
    3.  Nothing is stored on-chain
    4.  Content is stored in a UTXO datum
4.  How do you specify the precision units of a Fungible Token (FT)? 
    1.  Only possible using CIP-25
    2.  In the Token Registry or CIP-68
    3.  Inside the minting policy
    4.  None of the above
5.  What is UTXO fragmentation? 
    1.  There are too many UTXOs on the blockchain
    2.  There are too many UTXO needed as inputs to satisfy the outputs
    3.  There are too many UTXO outputs
    4.  There are too many assets locked into one UTXO

# [Answers](#toc.xhtml#s166a)

1.  a
2.  a
3.  a
4.  b
5.  b

# [Questions](#toc.xhtml#s167a)

1.  What are some other possible use cases for minting on Cardano?
2.  In what situations would you use CIP-25 or CIP-68?
3.  What are the ways to make a Minting Policy ID or Token Name unique?
4.  For a given native token, is it possible to know the current Address where the UTXO is locked at and how can this be done?
5.  Can you describe other coin selection algorithms besides Largest-first and Random Improve?

# [Key Terms](#toc.xhtml#s168a)

*   **Asset Name**: An immutable token name on-chain of a specific minting policy.
*   **CIP-25:** Metadata standard using transaction metadata.
*   **CIP-68**: Metadata standard using a reference token and datum.
*   **Collection:** The grouping of tokens together in a token bundle.
*   **Dust:** A very small value UTXO that cannot be spent.
*   **ERC-20:** Ethereum FT token standard
*   **ERC-721:** Ethereum NFT token standard
*   **Monetary Policy**: Specifies the amount of tokens in circulation and the inflation or deflation rate.
*   **Policy Identifier (ID):** A unique identifier that is the hash of a Minting Policy script.
*   **Quantity:** The accounting unit.
*   **Reference Inputs**: Read-only UTXOs that are included as transaction inputs but cannot be spent.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c07.xhtml#ftn1a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/doc/explanations/features.rst](https://github.com/IntersectMBO/cardano-ledger/blob/master/doc/explanations/features.rst)

[²](#c07.xhtml#ftn2a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0055](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0055)

[³](#c07.xhtml#ftn3a) [https://developers.cardano.org/docs/native-tokens/minting/](https://developers.cardano.org/docs/native-tokens/minting/)

[⁴](#c07.xhtml#ftn4a) [https://github.com/IntersectMBO/cardano-node/blob/1.35.7/doc/reference/simple-scripts.md](https://github.com/IntersectMBO/cardano-node/blob/1.35.7/doc/reference/simple-scripts.md)

[⁵](#c07.xhtml#ftn5a) [https://github.com/cardano-foundation/cardano-token-registry](https://github.com/cardano-foundation/cardano-token-registry)

[⁶](#c07.xhtml#ftn6a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0025](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0025)

[⁷](#c07.xhtml#ftn7a) [https://pool.pm/test/metadata](https://pool.pm/test/metadata)

[⁸](#c07.xhtml#ftn8a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0068](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0068)

[⁹](#c07.xhtml#ftn9a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0002](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0002)

[^(10)](#c07.xhtml#ftn10a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0002#algorithms](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0002#algorithms)

[^(11)](#c07.xhtml#ftn11a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/helios/ticket/contracts/ticket.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/helios/ticket/contracts/ticket.hl)

[^(12)](#c07.xhtml#ftn12a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/helios/ticket/contracts/ticket.h](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/helios/ticket/contracts/ticket.h)

[^(13)](#c07.xhtml#ftn13a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/helios/ticket/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/helios/ticket/pages/index.tsx)

[^(14)](#c07.xhtml#ftn14a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/helios/ticket/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/helios/ticket/pages/index.tsx)

[^(15)](#c07.xhtml#ftn15a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/helios/ticket/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/helios/ticket/pages/index.tsx)

[^(16)](#c07.xhtml#ftn16a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/helios/ticket/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/helios/ticket/pages/index.tsx)

[^(17)](#c07.xhtml#ftn17a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/helios/ticket/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/helios/ticket/pages/index.tsx)

[^(18)](#c07.xhtml#ftn18a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/aiken/ticket/contracts/validators/ticket.ak](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/aiken/ticket/contracts/validators/ticket.ak)

[^(19)](#c07.xhtml#ftn19a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/aiken/ticket/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/aiken/ticket/pages/index.tsx)

[^(20)](#c07.xhtml#ftn20a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/aiken/ticket/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/aiken/ticket/pages/index.tsx)

[^(21)](#c07.xhtml#ftn21a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/aiken/ticket/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/aiken/ticket/pages/index.tsx)

[^(22)](#c07.xhtml#ftn22a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_07/aiken/ticket/pages/api/getWalletInfo.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_07/aiken/ticket/pages/api/getWalletInfo.ts)

[^(23)](#c07.xhtml#ftn23a) [https://preprod.cexplorer.io/tx/e70ec36e15d6335c5023363112474b3ecea560e28af5707b126937cb33fc2946](https://preprod.cexplorer.io/tx/e70ec36e15d6335c5023363112474b3ecea560e28af5707b126937cb33fc2946)

[^(24)](#c07.xhtml#ftn24a) [https://preprod.cexplorer.io/tx/e70ec36e15d6335c5023363112474b3ecea560e28af5707b126937cb33fc2946/metadata#data](https://preprod.cexplorer.io/tx/e70ec36e15d6335c5023363112474b3ecea560e28af5707b126937cb33fc2946/metadata#data)

[^(25)](#c07.xhtml#ftn25a) [https://preprod.cexplorer.io/tx/bda3ee0f670f4a334116969867a46d9fe509939f893d274d3a98489e44cb91b6](https://preprod.cexplorer.io/tx/bda3ee0f670f4a334116969867a46d9fe509939f893d274d3a98489e44cb91b6)

[^(26)](#c07.xhtml#ftn26a) [https://preprod.cexplorer.io/policy/fbf3e7d0c79bb9bece6277c0560fe2af49b37f3f1a2ad6afd9f9cb3d/mint](https://preprod.cexplorer.io/policy/fbf3e7d0c79bb9bece6277c0560fe2af49b37f3f1a2ad6afd9f9cb3d/mint)

# [CHAPTER 8](#toc.xhtml#c08)

# [Tooling](#toc.xhtml#c08)

# [Introduction](#toc.xhtml#s169a)

Developing smart contracts often involves working with code that exists outside the blockchain (off-chain) and integrating it seamlessly with the Cardano network. In this chapter, we will review some of the tools and **service providers** you can use to help accomplish these tasks. First, we will delve into Cardano Blockchain API providers such as Blockfrost, Maestro, Koios, and Dandelion. Next, we will explore hosted environments with `Demeter.run` to set up services like Cardano Node, Ogmios, and Kupo. Finally, we will learn how to set up a local Devnet for rapid development and prototyping with the Yaci DevKit.

# [Structure](#toc.xhtml#s170a)

In this chapter, we will discuss the following topics:

*   Blockchain API/Monitoring Providers 
    *   Blockfrost
    *   Maestro
    *   Koios
    *   Dandelion
*   Tooling Components 
    *   Cardano-node
    *   Ogmios
    *   Kupo
    *   Local Devnet
    *   Additional Resources

# [Blockchain API/Monitoring Providers](#toc.xhtml#s171a)

The examples throughout this book demonstrate the use of Blockfrost API to query the blockchain and submit transactions. In this section, however, we will look at additional widely used blockchain service providers and tooling that help avoid a centralized point of failure within the Cardano ecosystem.

# [Blockfrost](#toc.xhtml#s172a)

Blockfrost ([https://blockfrost.io/](https://blockfrost.io/)) was one of the first providers in Cardano and has earned the trust of a large user base with over 100M+ daily requests and 20K+ developers.[¹](#c08.xhtml#ftn1) Blockfrost has excellent API documentation and a wide range of services, from simple blockchain queries to **webhook** callbacks for your application. They have free entry-level plans that allow you to test out APIs for your application. You can make HTTP REST calls to their API or use their convenient **SDKs** for Node.js, Python, Rust, C#, Go, and more. Blockfrost supports Mainnet, Preprod, and Preview networks, and you can run your own instance from their GitHub Repo.[²](#c08.xhtml#ftn2)

# [Maestro](#toc.xhtml#s173a)

On July 19, 2023, Maestro ([https://www.gomaestro.org/](https://www.gomaestro.org/)) released V1 of their dApp platform with new features that significantly improved Cardano blockchain integration:[³](#c08.xhtml#ftn3)

*   **Turbo Transactions**: Accelerate **transaction finality** with Maestro’s transaction propagation system.
*   **New Blockchain Indexer**: High performance, low latency, optimized Cardano blockchain indexer with convenient and efficient APIs.
*   **Transaction Manager:** A transaction monitoring system with automatic retries and zero-delay pending, on-chain, and rollback notifications.[⁴](#c08.xhtml#ftn4)

# [Code Example](#toc.xhtml#s174a)

In our vesting and ticket examples, we change the Lucid provider in `pages/index.tsx` to use Maestro, which is included in the Lucid library, as shown in *[Figure 8.1](#c08.xhtml#fig8_1)*.

![](OEBPS/images/Figure-8.1.jpg)

**Figure 8.1:** Lucid Maestro Provider[⁵](#c08.xhtml#ftn5)

For the ticket minting example, we also needed to change the blockchain query in `getTicketMetadata.ts` in the `pages/api` folder. We use the Node.js API provided by Maestro, as shown in *[Figure 8.2](#c08.xhtml#fig8_2)*.

![](OEBPS/images/Figure-8.2.jpg)

**Figure 8.2:** Maestro TypeScript API[⁶](#c08.xhtml#ftn6)

In *[Figure 8.2](#c08.xhtml#fig8_2)*, on line 18, we create the Maestro client and then call `maestroClient.assets` on line 27 to get the metadata for the asset.

# [Setup](#toc.xhtml#s175a)

To set up the Demeter.run environment to run the Maestro demo, execute the following commands in a terminal window:

`$ export NEXT_PUBLIC_MAESTRO_API_KEY=your-maestro-key-here`

`$ export NEXT_PUBLIC_ENV="dev"`

`$ export NEXT_PUBLIC_HOST="your-demeter-run-host"`

`$ export NEXT_PUBLIC_PROTOCOL="https"`

`$ export NEXT_PUBLIC_PORT=""`

# [Koios](#toc.xhtml#s176a)

Koios[⁷](#c08.xhtml#ftn7) is a distributed, open-source, **RESTful** APIs for querying and submitting to the Cardano blockchain. It is built and maintained by the highly respected Cardano Stakepool Guild Operators.[⁸](#c08.xhtml#ftn8) Koios promotes decentralization by using distributed processing architecture, a core value of Cardano. A typescript Koios provider client can also be used directly from the Helios library.

# [Dandelion](#toc.xhtml#s177a)

Dandelion[⁹](#c08.xhtml#ftn9) is a collection of Cardano Blockchain APIs as a free community service. The services include:

*   GraphQL[^(10)](#c08.xhtml#ftn10)
*   Ogmios[^(11)](#c08.xhtml#ftn11)
*   Cardano DB Sync/Postgres API [^(12)](#c08.xhtml#ftn12)
*   Rosetta API[^(13)](#c08.xhtml#ftn13)

# [Tooling Components](#toc.xhtml#s178a)

One of the major benefits of Cardano is that the code is open source, and you have the ability to download, build, and run all the required components yourself. Or, you can use a third-party provider to manage and host these components. We have already seen how to set up an environment for the examples in this book with Demeter.run, but they offer many other Cardano components and services. We will look at some of the more popular components used for Cardano blockchain integration.

Tooling components are used to query, react, or transact with a blockchain. A typical, off-chain tooling setup is illustrated in *[Figure 8.3](#c08.xhtml#fig8_3)*, where Cardano DB Sync processes blocks from a Cardano Node and stores data in a Postgres Database. An application can then query the database or react to blockchain events accordingly.

![](OEBPS/images/Figure-8.3.jpg)

**Figure 8.3:** DB Sync Off-Chain Indexing

The challenge with DB Sync is that it is difficult to set up and requires significant hardware resources for Mainnet. Fortunately, Demeter.run provides hosted instances that you can easily deploy with no manual configuration. This is great for networks like Mainnet or Preprod but not well-suited for custom networks or local testing environments.

# [Cardano Node](#toc.xhtml#s179a)

The core component of the Cardano blockchain is the Cardano Node and the source code is located on GitHub.[^(14)](#c08.xhtml#ftn14) You can download and compile the source code, run the static binaries, or use docker containers. Demeter.run also has an extension to provision a Cardano Node as follows:

1.  Go to [https://demeter.run/](https://demeter.run/)
2.  Choose the project you want to deploy to. We will enable this extension for a workspace already created in *[Chapter 5, Transaction Builder](#c05.xhtml).*
3.  Once the workspace is provisioned in *[Figure 8.4](#c08.xhtml#fig8_4)*, you must enable the Cardano Node by selecting the Connected Extensions by scrolling down the page. 
    
    ![](OEBPS/images/Figure-8.4.jpg)
    
    **Figure 8.4:** Demeter.run Cardano Workspace
    
4.  Select Browse Extensions.
5.  Find the Nodes box, select `Deploy`, and then `Provision Resource`.
6.  Scroll down, select `Preprod`, and select the `Create Resource` button at the bottom of the page.
7.  When you go back to the `Project Overview` you should see the Node extension connected, as shown in *[Figure 8.5](#c08.xhtml#fig8_5).*
    
    ![](OEBPS/images/Figure-8.5.jpg)
    
    **Figure 8.5:** Demeter.run Cardano Node Connected
    
8.  Select the workspace you previously provisioned.
9.  Select the `Visual Studio Code` icon on the workspace to launch the Visual Studio web client.
10.  From the hamburger menu, select `Terminal` -> `New`.

To verify that your cardano-node is connected to the network, type the following command and you should see `syncProgress` at 100%.

`~/workspace/repo$ cardano-cli query tip --testnet-magic 1`

`{`

`"block": 1595041,`

`"epoch": 106,`

`“era”: “Babbage”,`

`"hash": "ed3be308f9538fe59241f5d90b333de06ddc581ee783ba0002d0c911b3b`

`df3f6",`

`"slot": 44370786,`

`"slotInEpoch": 220386,`

`"slotsToEpochEnd": 211614,`

`"syncProgress": "100.00"`

`}`

Most of the tooling that connects to the `Cardano Node` uses a socket and you can find out the location of the socket by printing out the shell environment variable:

`~/workspace/repo$ echo $CARDANO_NODE_SOCKET_PATH`

`/ipc/node.socket`

The `cardano-cli` is the Swiss army knife of Cardano and there are lots of resources on its usage and would suggest starting here.[^(15)](#c08.xhtml#ftn15) Type `cardano-cli` to see the following list of top-level common options. Use the `--help` flag to get additional usage info for each command.

`~/workspace/repo$ cardano-cli`

`cardano-cli - General purpose command-line utility to interact with`

`cardano-node. Provides specific commands to manage keys, addresses, build & submit transactions, certificates, etc.`

`Usage: cardano-cli (Era based commands | byron | ping | version)`

`Available options:`

`--version               Show the cardano-cli version`

`-h,--help               Show this help text`

`Era based commands`

`address                 Payment address commands`

`stake-address           Stake address commands`

`key                     Key utility commands`

`transaction             Transaction commands`

`node                    Node operation commands`

`stake-pool              Stake pool commands`

`query                   Node query commands.`

`                      Will query the local node whose`

`                        Unix domain socket is obtained from the`

`                        CARDANO_NODE_SOCKET_PATH environment variable.`

`genesis                 Genesis block commands`

`governance              Governance commands`

`text-view                Commands for dealing with Shelley TextView files.`

`                        Transactions, addresses`

`                      etc are stored on disk as`

`                        TextView files.`

`Byron specific commands`

`byron                    Byron specific commands`

`Available commands:`

`ping                     Ping a cardano node either using node-to-node or node-to-client protocol. It negotiates a handshake and keeps sending keep alive messages.`

`Miscellaneous commands`

`help                     Show all help`

`version                  Show the cardano-cli version`

You can now access command-line utility tools such as `cardano-address` and `bech32`.

`~/workspace/repo$ cardano-address`

`Usage: cardano-address ((-v|--version) | COMMAND)`

`Command-line for address and key manipulation in Cardano.`

`Available options:`

`-h,--help                Show this help text`

`-v,--version             Show the software current version and build revision.`

`Available commands:`

`version                  Show the software current version and build revision.`

`recovery-phrase          About recovery phrases`

`key                      About public/private keys`

`address                  About addresses`

`script                   About scripts`

`~/workspace/repo$ bech32 --help`

`Usage: bech32 [PREFIX]`

`Convert to and from bech32 strings. Data are read from standard input.`

`Available options:`

`-h,--help               Show this help text`

`PREFIX                  An optional human-readable prefix (e.g. 'addr').`

`                        - When provided, the input text is decoded from various encoding formats and re-encoded to bech32 using the given prefix.`

`                        - When omitted, the input text is decoded from bech32 to base16.`

`-v,--version             output version information and exit`

`Supported encoding formats: Base16, Bech32 & Base58.`

`Examples:`

`To Bech32:`

`$ bech32 base16_ <<< 706174617465`

`base16_1wpshgct5v5r5mxh0`

`$ bech32 base58_ <<< Ae2tdPwUPEYy`

`base58_1p58rejhd9592uusa8pzj2`

`$ bech32 new_prefix <<< old_prefix1wpshgcg2s33x3`

`new_prefix1wpshgcgeak9mv`

`From Bech32:`

`$ bech32 <<< base16_1wpshgct5v5r5mxh0`

`706174617465`

# [Ogmios](#toc.xhtml#s180a)

Ogmios[^(16)](#c08.xhtml#ftn16) is one of the most widely used and popular tools for Cardano developers, and it has excellent documentation. It is a translation layer that exposes the Cardano node capability via a REST API or Web RPC interface. Ogmios is open source and can be downloaded, built, and installed locally from GitHub,[^(17)](#c08.xhtml#ftn17) or by a docker container. We will deploy the hosted version using Demeter.run, so we can quickly demonstrate how to interact with it using our examples.

To add an Ogmios extension:

1.  Go to the `Project` page, scroll down, and select `BROWSE EXTENSIONS`, as shown in *[Figure 8.6](#c08.xhtml#fig8_6).* 
    
    ![](OEBPS/images/Figure-8.6.jpg)
    
    **Figure 8.6:** Demeter.run Project View
    
2.  Select Ogmios Deploy.
3.  Select `Create Resource` and the `Preprod` network.
4.  Select v5 as the version and the `CREATE RESOURCE` button.  
5.  You see the instance running, as shown in *[Figure 8.7](#c08.xhtml#fig8_7)*.
    
    ![](OEBPS/images/Figure-8.7.jpg)
    
    **Figure 8.7:** Demeter.run Ogmios Live
    

Now, let’s try out the `Ogmios` API using a web tool like Hoppscotch.[^(18)](#c08.xhtml#ftn18)

1.  Go to the URL: [https://hoppscotch.io/realtime/websocket](https://hoppscotch.io/realtime/websocket).
2.  Paste in the public https hostname for Ogmios and prefix wss:// to the address.
3.  Select `Connect`*.*
4.  Then paste the following query and select `Send`:
    
    `{`
    
    `"type": "jsonwsp/request",`
    
    `"version": "1.0",`
    
    `"servicename": "ogmios",`
    
    `"methodname": "Query",`
    
    `"args": {`
    
    `"query": "ledgerTip"`
    
    `}`
    
    `}`
    
5.  You should see the successful result, as shown in *[Figure 8.8](#c08.xhtml#fig8_8).*
    
    ![](OEBPS/images/Figure-8.8.jpg)
    
    **Figure 8.8:** Hoppscotch Ogmios Success
    

# [Kupo](#toc.xhtml#s181a)

Kupo[^(19)](#c08.xhtml#ftn19) is an open-source Cardano blockchain indexer that is fast, lightweight, and configurable. The API documentation[^(20)](#c08.xhtml#ftn20) is excellent and is the go-to choice for many Cardano development teams who prefer to use in-house tools. Blockchains are designed to be a sequence of blocks connected together, forming a chain. This, however, makes it very difficult to perform efficient data queries. This is why we have indexers that take in blockchain data and store it in a database. This data can be indexed and then queried, filtered, and analyzed. Kupo can be downloaded, built, and installed locally, but it can also be set up as a hosted service using Demeter.run.

We will again go to the Project page and add another resource, this time a Kupo resource. Select deploy and create the resource for the preprod network. Next, copy the https URL for future reference. We should see four resources: Workspace, Node, Ogmios, and Kupo, as shown in *[Figure 8.9](#c08.xhtml#fig8_9)*.

![](OEBPS/images/Figure-8.9.jpg)

**Figure 8.9:** Demeter.run Resources

To do a quick test to confirm Kupo is working correctly, you can execute the following command and replace the hostname with the hostname copied from the `Demeter.run` Kupo resource.

`$ curl -fsSL https://dmtr_kupo12e…mph005.preprod-v2.kupo-m1.demeter.run/health`

`# TYPE kupo_configuration_indexes gauge`

`kupo_configuration_indexes  1.0`

`# TYPE kupo_connection_status gauge`

`kupo_connection_status  1.0`

`# TYPE kupo_most_recent_checkpoint counter`

`kupo_most_recent_checkpoint  59235759`

`# TYPE kupo_most_recent_node_tip counter`

`kupo_most_recent_node_tip  59235759`

In this case, the Kupo instance is healthy and you can see the most recent `checkpoint` and `node tip`. Checkpoints are blocks on-chain that have been processed by Kupo and are mainly used to synchronize with the blockchain after a restart.[^(21)](#c08.xhtml#ftn21)

# [Code Example](#toc.xhtml#s182a)

Now, we are ready to update the vesting and ticket code examples to use Ogmios and Kupo together. Lucid has a provider we can use for this exact purpose, called `kupmios`, as shown in *[Figure 8.10](#c08.xhtml#fig8_10)*.

![](OEBPS/images/Figure-8.10.jpg)

**Figure 8.10:** Lucid Kupmios[^(22)](#c08.xhtml#ftn22)

The vesting example will work without any other changes by switching to the Kupmios provider. The ticket example, however, requires changes to the pages/API` getTicketMetadata.ts`, as shown in *[Figure 8.11](#c08.xhtml#fig8_11).*

![](OEBPS/images/Figure-8.11.jpg)

**Figure 8.11:** Kupo getMetadata[^(23)](#c08.xhtml#ftn23)

To retrieve metadata from Kupo, first get the transaction associated with the mint transaction. The token asset is provided on line 70, and the results are sorted by the order of the transactions that occurred on the blockchain. Therefore, the mint is the first transaction, so use the first transaction ID and then look up the metadata on that specific transaction on line 73. Lines 76–81 parse the metadata object and return the results to the front end.

# [Setup](#toc.xhtml#s183a)

To set up the Demeter.run environment to run the Kupo + Ogmios demo, please execute the following commands in a terminal window.

`$ export NEXT_PUBLIC_KUPO_API=https://dmtr_kupo12e…mph005.preprod-v2.kupo-m1.demeter.run`

`$ export NEXT_PUBLIC_OGMIOS_API=wss://dmtr_ogmios1v…g0t6mk.preprod-v5.ogmios-m1.demeter.run`

`$ export NEXT_PUBLIC_ENV="dev"`

`$ export NEXT_PUBLIC_HOST="your-demeter-run-host"`

`$ export NEXT_PUBLIC_PROTOCOL="https"`

`$ export NEXT_PUBLIC_PORT=""`

# [Local Devnet](#toc.xhtml#s184a)

Thanks to the awesome work from BoxBean[^(24)](#c08.xhtml#ftn24); it is now easy to install a local Devnet, similar to Hardhat for Ethereum. The Yaci Devkit uses lightweight components for indexing and querying blockchain data. In particular, BoxBean created Yaci, a modular, Java-based Ouroboros min-protocol that listens to incoming blocks, monitors the local mempool, and submits transactions.[^(25)](#c08.xhtml#ftn25) The team also created Yaci Store, a Java-based solution that provides an API to query indexed data and handle rollbacks.[^(26)](#c08.xhtml#ftn26) To enable integration with a browser extension wallet like Nami and Helios for off-chain transaction building, the local Devnet will also use a local Cardano DB Sync to feed blockchain data to a local Blockfrost API provider.

The following five steps are required to set up a local devnet:

1.  Set up YaciDevkit[^(27)](#c08.xhtml#ftn27)
2.  Set up Cardano DB Sync
3.  Set up Blockfrost backend RYO (Run Your Own)
4.  Build and install Nami browser wallet with a local Testnet network
5.  Top up wallet with funds

# [Environment](#toc.xhtml#s185a)

The following setup instructions have been tested on Ubuntu Linux 20.04.1. You may require additional setup for other operating systems.

# [Install Docker](#toc.xhtml#s186a)

`$ sudo apt -y install apt-transport-https ca-certificates curl`

`software-properties-common`

`$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`

`$ echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_`

`release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`

`$ sudo apt update`

`$ sudo apt -y install docker-ce docker-ce-cli containerd.io`

`$ sudo usermod -aG docker $USER`

`$ newgrp docker`

`$ docker run hello-world`

**Step 1: Setting up Yaci Devkit**

Once docker is installed, you can cd into the `yaci-devit` directory, so that we can install the following two docker images.[^(28)](#c08.xhtml#ftn28) We will install the following images as part of the setup process:

`REPOSITORY             TAG             IMAGE ID          SIZE`

`bloxbean/yaci-cli      0.0.20-beta1    0b5f0541f396      1.2GB`

`bloxbean/yaci-viewer   0.0.9           73b52df24dfb      579MB`

`$ git clone https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts.git --recurse-submodules`

`$ cd Mastering-Cardano-Smart-Contracts/chapter_08/local-devnet/yaci`

`-devkit`

`$ sudo ./start.sh`

`$ sudo ./yaci-cli.sh`

To start up a new cluster, use the command `create-node -o --start`

`yaci-cli:>create-node -o --start`

`[Success] Delete existing folder`

`[Success] Create cluster folder !!!`

`[Success] Slot length updated in genesis.json`

`[Success] Updated configuration.yaml`

`[Success] Update ports`

`[Success] Create Cluster : default`

`###### Node Details (Container) ######`

`[Node port] 3001`

`[Node Socket Paths]`

`/clusters/default/node-spo1/node.sock`

`[Submit Api Port] 8090`

`[Protocol Magic] 42`

`[Block Time] 1.0 sec`

`[Slot Length] 1.0 sec`

`[Start Time] 0`

`#################### URLS (Host) ####################`

`[Yaci Viewer] http://localhost:5173`

`[Yaci Store Swagger UI] http://localhost:8080/swagger-ui.html`

`[Yaci Store Api URL] http://localhost:8080/api/v1/`

`[Pool Id] pool1wvqhvyrgwch4jq9aa84hc8q4kzvyq2z3xr6mpafkqmx9wce39zy`

`…`

`[OK] Yaci Store Started`

`devnet:default>`

For more information regarding startup options and configuration, please consult the GitHub repository: [https://github.com/bloxbean/yaci-devkit](https://github.com/bloxbean/yaci-devkit).

**Step 2: Starting DB Sync**

In a new terminal window:

`$ cd chapter_08/local-devnet/yaci-devkit`

`$ ./start-db-sync.sh`

If successful, you should see the following output.

`…`

`cardano-db-sync_1   | [db-sync-node:Info:65] [2024-05-08 10:15:13.01 UTC] Insert Babbage Block: epoch 0, slot 244, block 244, hash 74ec222296e80d0dae52fd7723c7317746928144fdbf8b9f5fd31a7ca6daf095`

`cardano-db-sync_1   | [db-sync-node:Info:65] [2024-05-08 10:15:14.00 UTC] Insert Babbage Block: epoch 0, slot 245, block 245, hash e13b22299709d612d8381bc6292a75ef04f5fa912a308c97ad8f804c8044fc94`

`cardano-db-sync_1   | [db-sync-node:Info:65] [2024-05-08 10:15:15.00 UTC] Insert Babbage Block: epoch 0, slot 246, block 246, hash 888f504744cef550755ebd88a6cd6e9b5ad27f3ddcba11076ac8a00a9d04a258`

`cardano-db-sync_1   | [db-sync-node:Info:65] [2024-05-08 10:15:16.00 UTC] Insert Babbage Block: epoch 0, slot 247, block 247, hash be35c0eb241b0369af4a869480e9340a6c079fc25a3e8f96273fa633a22b4da9`

`…`

**Step 3: Starting The Blockfrost-RYO**

In another new terminal window:

`$ cd chapter_08/local-devnet/blockfrost-backend-ryo`

`$ nvm install 20.9.0.`

`$ yarn install`

`$ yarn run dev-testnet`

**Step 4: Installing the Nami Local Devnet Version**

Open up another terminal window and go into the Nami directory.

`$ cd chapter_08/local-devnet/nami`

`$ nvm use 20.9.0`

`$ npm install`

`$ npm run build`

This will create a build directory that can be loaded into the Chrome browser. Open a Chrome browser tab extension window `chrome://extensions/` and select “Load Unpacked” at the top left side of the window. Then navigate to the `nami/build` directory that was just created and select it. The Nami wallet should now be installed, and you can launch the browser extension. It will first ask you to create a new wallet and a passphrase. You will need to switch to the Testnet network and can do that by selecting the avatar at the top right of the window. Next, select Settings, Network, and choose Testnet from the Network dropdown menu, as shown in *[Figure 8.12](#c08.xhtml#fig8_12)*. Also, enable Custom Node and enter `http://localhost:8090/api/submit/tx` as the URL. You can confirm you are on the correct network by seeing the Testnet label on the bottom left of the Nami pop-up window.

![](OEBPS/images/Figure-8.12.jpg)

**Figure 8.12:** Nami Wallet Devnet

**Tip**: *If you installed the Nami wallet using the unpack method and closed down the browser, you may need to follow the unpack instructions again. If you have also re-created the new local Devnet network, then you will need to create a new Nami account or explicitly remove the Nami wallet browser plugin to clear cached Nami account data.*

**Step 5: Top Up Wallet with Funds**

With the Nami wallet open, select the receive button, and copy the receiving address. Then, go into the `yaci-cli` terminal, type the `topup` command, and paste the receiving address and the amount of Ada to send, as shown in *[Figure 8.13](#c08.xhtml#fig8_13)*.

![](OEBPS/images/Figure-8.13.jpg)

**Figure 8.13:** Yaci DevKit Top-up

You can confirm in your Nami wallet that you have received this amount, as presented in *[Figure 8.14](#c08.xhtml#fig8_14)*.

![](OEBPS/images/Figure-8.14.jpg)

**Figure 8.14:** Nami Wallet Top-up

# [Example Test Drive](#toc.xhtml#s187a)

Now we can try out a previous ticket example using the local devnet. Using another terminal window, execute the following commands:

`$ cd chapter_08/local-devnet/ticket`

`$ npm install`

`$ npm run dev`

Next, mint some new tickets on the local devnet, as illustrated in *[Figure 8.15](#c08.xhtml#fig8_15)*.

![](OEBPS/images/Figure-8.15.jpg)

**Figure 8.15:** Minting on Local Devnet

We can now see the transaction details on the local Yaci DevKit blockchain explorer under the transactions tab, as shown in *[Figure 8.16](#c08.xhtml#fig8_16)*.

![](OEBPS/images/Figure-8.16.jpg)

**Figure 8.16:** Local Devnet Explorer Transaction View

We can also view the smart contract details including the Redeemer values in *[Figure 8.17](#c08.xhtml#fig8_17)*.

![](OEBPS/images/Figure-8.17.jpg)

**Figure 8.17:** Local Devnet Explorer Contract View

# [Additional Resources](#toc.xhtml#s188a)

Additional approaches and solutions exist to query and react to Cadano blockchain data. *[Table 8.1](#c08.xhtml#tab8_1)* provides an overview of the more popular Cardano tooling options.

| **Name** || **Description** || **Technology Stack** |
| --- | --- | --- |
| DB Sync[^(29)](#c08.xhtml#ftn29) || Cardano Blockchain Indexer || HaskellPostgress SQL DB |
| Kupo[^(30)](#c08.xhtml#ftn30) || Cardano Blockchain indexer || Haskell |
| Ogmios[^(31)](#c08.xhtml#ftn31) || Lightweight interface to Cardano Node || Haskell |
| Yaci Store[^(32)](#c08.xhtml#ftn32) || Cardan Blockchain indexer and real-time monitoring || Java, RDBMS or Redis/MongoDB |
| Carp[^(33)](#c08.xhtml#ftn33) || Cardano Blockchain indexer || Rust, Typescript, Oura, Cardano Multiplatform Lib,PostgresDB |
| Scrolls[^(34)](#c08.xhtml#ftn34) || Blockchain crawler, aggregator with real-time updates || Rust, Redis |
| Ouroboros Network JS[^(35)](#c08.xhtml#ftn35) || Ouroboros network library written in typescript with Node.js streaming for chain sync, tx monitoring and submission || Typescript |
| GraphQL[^(36)](#c08.xhtml#ftn36) || Cross-platform, typed, and queryable API for Cardano || Typescript, Cardano DB Sync |
| Oura[^(37)](#c08.xhtml#ftn37) || Realtime blockchain monitoring and alerting || Rust, Pallas[^(38)](#c08.xhtml#ftn38) |

**Table 8.1:** Blockchain Tooling

# [Conclusion](#toc.xhtml#s189a)

This chapter provided an overview of some of the more popular Cardano off-chain providers and tooling available to developers. First, we explored Cardano Blockchain providers such as Blockfrost, Maestro, Koios, and Dandelion. Next, we understood some of the Cardano infrastructure components and tooling, such as Cardano Node, Ogmios, and Kupo, and how to provision them with Demeter.run. We also learned how to deploy a local devnet using Yaci DevKit to test both the on-chain and off-chain code. Finally, we provided an overview of the most popular tooling components for completeness. We are now ready for the next chapter to use our knowledge of off-chain tooling to build a complete end-to-end blockchain application.

# [Points to Remember](#toc.xhtml#s190a)

*   Multiple blockchain API service providers and tooling options help promote decentralization and avoid a single point of failure in the ecosystem.
*   Blockfrost was one of the first Cardano API service providers and is the most used API service provider in the Cardano ecosystem.
*   Maestro recently launched a new version of its APIs with low latency, high-performance chain index queries, transaction state management, and optimized transaction submission.
*   Koios is a decentralized, distributed platform that provides Cardano Blockchain API services.
*   Off-chain tooling components are used to query, react, or submit blockchain data.
*   Cardano Node can be run from a docker container, static binaries, or by compiling the source code.
*   Demeter.run has resources such as Cardano Node that can be run and attached to a workspace
*   `cardano-cli` is the Swiss army knife of Cardano with multiple uses and functionality
*   Ogmios is popular because it exposes Cardano node functionality using REST APIs or a Web RPC interface.
*   Kupo is also a popular open-source Cardano Blockchain indexer that captures and saves blockchain data quickly to an in-memory database.
*   Lucid has a built-in Kupo and Ogmios provider that can connect to a Kupo and Ogmios instance for blockchain data lookups and transaction submissions.
*   Yaci DevKit can set up a local devnet similar to Hardhat for Ethereum.

# [Multiple Choice Questions](#toc.xhtml#s191a)

1.  Why is blockchain tooling needed? 
    1.  Used by on-chain in validator logic
    2.  Used by the Cardano Ledger
    3.  Needed to start/stop the Cardano Blockchain
    4.  Access blockchain data efficiently
2.  What functionality cannot be done using `cardano-cli`? 
    1.  Start/Stop a cardano node
    2.  Submit a transaction
    3.  Query the Cardano Blockchain tip
    4.  See the contents of a UTXO
3.  How do you access Ogmios? 
    1.  Node socket
    2.  SQL query
    3.  HTTP REST API
    4.  HTTP REST API or RPC Web Socket
4.  What are some of the features of the Yaci Devkit? 
    1.  A blockchain explorer, Kupo and Ogmios APIs
    2.  Token registry
    3.  Mainnet network
    4.  GraphQL
5.  Which tool can submit a transaction? 
    1.  Kupo
    2.  Oura
    3.  Carp
    4.  ouroboros-network-js

# [Answers](#toc.xhtml#s192a)

1.  d
2.  a
3.  d
4.  a
5.  d

# [Questions](#toc.xhtml#s193a)

1.  What are the centralization risks to any blockchain?
2.  Why is blockchain technology generally not efficient for direct data access?
3.  How does tooling speed up access to data queries?
4.  What did Maestro do to help improve the finality times for a submitted transaction?
5.  What are some of the advantages of using a local Testnet or devnet?

# [Key Terms](#toc.xhtml#s194a)

*   **Node Tip:** The latest (highest) confirmed block in the blockchain.
*   **RESTful:** It uses HTTP requests to access and set data between a client and server.
*   **SDK**: Software Development Kit makes it more convenient for developers to access service providers’ APIs.
*   **Service Provider**: A company that provides off-chain blockchain API services.
*   **Transaction Finality:** The time it takes to finalize a transaction on the blockchain.
*   **Webhook:** A callback function that will make a network call to an application when a certain condition is met.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c08.xhtml#ftn1a) [https://blockfrost.io/](https://blockfrost.io/)

[²](#c08.xhtml#ftn2a) [https://github.com/blockfrost/blockfrost-backend-ryo](https://github.com/blockfrost/blockfrost-backend-ryo)

[³](#c08.xhtml#ftn3a) [https://www.gomaestro.org/dapp-platform](https://www.gomaestro.org/dapp-platform)

[⁴](#c08.xhtml#ftn4a) [https://twitter.com/GoMaestroOrg/status/1681685533314142209](https://twitter.com/GoMaestroOrg/status/1681685533314142209)

[⁵](#c08.xhtml#ftn5a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_08/maestro/ticket/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_08/maestro/ticket/pages/index.tsx)

[⁶](#c08.xhtml#ftn6a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_08/maestro/ticket/pages/api/getTicketMetadata.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_08/maestro/ticket/pages/api/getTicketMetadata.ts)

[⁷](#c08.xhtml#ftn7a) [https://koios.rest/](https://koios.rest/)

[⁸](#c08.xhtml#ftn8a) [https://cardano-community.github.io/guild-operators/](https://cardano-community.github.io/guild-operators/)

[⁹](#c08.xhtml#ftn9a) [https://dandelion.link/](https://dandelion.link/)

[^(10)](#c08.xhtml#ftn10a) [https://github.com/cardano-foundation/cardano-graphql](https://github.com/cardano-foundation/cardano-graphql)

[^(11)](#c08.xhtml#ftn11a) [https://ogmios.dev/](https://ogmios.dev/)

[^(12)](#c08.xhtml#ftn12a) [https://github.com/IntersectMBO/cardano-db-sync](https://github.com/IntersectMBO/cardano-db-sync)

[^(13)](#c08.xhtml#ftn13a) [https://github.com/cardano-foundation/cardano-rosetta](https://github.com/cardano-foundation/cardano-rosetta)

[^(14)](#c08.xhtml#ftn14a) [https://github.com/IntersectMBO/cardano-node](https://github.com/IntersectMBO/cardano-node)

[^(15)](#c08.xhtml#ftn15a) [https://github.com/input-output-hk/cardano-node-wiki/blob/main/docs/getting-started/cli.md](https://github.com/input-output-hk/cardano-node-wiki/blob/main/docs/getting-started/cli.md)

[^(16)](#c08.xhtml#ftn16a) [https://ogmios.dev/](https://ogmios.dev/)

[^(17)](#c08.xhtml#ftn17a) [https://github.com/CardanoSolutions/ogmios](https://github.com/CardanoSolutions/ogmios)

[^(18)](#c08.xhtml#ftn18a) [https://hoppscotch.io/](https://hoppscotch.io/)

[^(19)](#c08.xhtml#ftn19a) [https://github.com/CardanoSolutions/kupo](https://github.com/CardanoSolutions/kupo)

[^(20)](#c08.xhtml#ftn20a) [https://cardanosolutions.github.io/kupo/](https://cardanosolutions.github.io/kupo/)

[^(21)](#c08.xhtml#ftn21a) [https://cardanosolutions.github.io/kupo/#tag/Checkpoints](https://cardanosolutions.github.io/kupo/#tag/Checkpoints)

[^(22)](#c08.xhtml#ftn22a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_08/ogmios-kupo/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_08/ogmios-kupo/vesting/pages/index.tsx)

[^(23)](#c08.xhtml#ftn23a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_08/ogmios-kupo/ticket/pages/api/getTicketMetadata.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_08/ogmios-kupo/ticket/pages/api/getTicketMetadata.ts)

[^(24)](#c08.xhtml#ftn24a) [https://github.com/bloxbean](https://github.com/bloxbean)

[^(25)](#c08.xhtml#ftn25a) [https://github.com/bloxbean/yaci](https://github.com/bloxbean/yaci)

[^(26)](#c08.xhtml#ftn26a) [https://github.com/bloxbean/yaci-store/blob/main/docs/design.md](https://github.com/bloxbean/yaci-store/blob/main/docs/design.md)

[^(27)](#c08.xhtml#ftn27a) [https://github.com/bloxbean/yaci-devkit](https://github.com/bloxbean/yaci-devkit)

[^(28)](#c08.xhtml#ftn28a) [https://hub.docker.com/r/bloxbean/yaci-cli/tags](https://hub.docker.com/r/bloxbean/yaci-cli/tags)

[^(29)](#c08.xhtml#ftn29a) [https://github.com/IntersectMBO/cardano-db-sync](https://github.com/IntersectMBO/cardano-db-sync)

[^(30)](#c08.xhtml#ftn30a) [https://github.com/CardanoSolutions/kupo](https://github.com/CardanoSolutions/kupo)

[^(31)](#c08.xhtml#ftn31a) [https://ogmios.dev/](https://ogmios.dev/)

[^(32)](#c08.xhtml#ftn32a) [https://github.com/bloxbean/yaci-store](https://github.com/bloxbean/yaci-store)

[^(33)](#c08.xhtml#ftn33a) [https://github.com/dcSpark/carp](https://github.com/dcSpark/carp)

[^(34)](#c08.xhtml#ftn34a) [https://github.com/txpipe/scrolls](https://github.com/txpipe/scrolls)

[^(35)](#c08.xhtml#ftn35a) [https://github.com/StricaHQ/ouroboros-network-js](https://github.com/StricaHQ/ouroboros-network-js)

[^(36)](#c08.xhtml#ftn36a) [https://github.com/cardano-foundation/cardano-graphql](https://github.com/cardano-foundation/cardano-graphql)

[^(37)](#c08.xhtml#ftn37a) [https://github.com/txpipe/oura](https://github.com/txpipe/oura)

[^(38)](#c08.xhtml#ftn38a) [https://github.com/txpipe/pallas](https://github.com/txpipe/pallas)

# [CHAPTER 9](#toc.xhtml#c09)

# [Ticket Application Design](#toc.xhtml#c09)

# [Introduction](#toc.xhtml#s195a)

This chapter will discuss Smart Contract design patterns that leverage and utilize the Cardano UTXO architecture. **Anti-patterns** are also examined which should be avoided and lead to poor application performance and **UTXO contention**. We will discuss Cardano Improvement Proposals (CIPs) and where they will be applied to the application design. Next, we will examine a state machine diagram to see how the entire event ticket lifecycle works. Then we will explore state transitions looking at the inputs and outputs required for a successful transaction. Finally, we will summarize the chapter by reviewing sequence diagrams showing each use case’s interaction between system components.

# [Structure](#toc.xhtml#s196a)

In this chapter, we will discuss the following topics:

*   Design Patterns 
    *   Thread Token
    *   Beacon Token
    *   Order Book
*   Anti-Patterns 
    *   Liquidity Pools
    *   Batchers
*   Cardano Improvement Proposals 
    *   CIP-0003 Wallet Key Generation
    *   CIP-0030 Cardano dApp-Wallet Web Bridge
    *   CIP-0032 Inline Datums
    *   CIP-0040 Explicit Collateral Output
    *   CIP-0068 Datum Metadata Standard
*   The Application Architecture 
    *   On-Chain State Machines
    *   Off-Chain Sequence Diagrams

# [Design Patterns](#toc.xhtml#s197a)

By now, you are aware of the significant differences between a UTXO and an account model blockchain. In particular, many account-based blockchain design patterns are not optimal for UTXO blockchains and are called anti-patterns. Let’s first examine common UTXO design patterns and then contrast them with anti-patterns.

# [Thread Token](#toc.xhtml#s198a)

One of the first and most common design patterns involves using a thread token. A unique token is minted and included in a UTXO locked at a script address. The script can only be spent if the transaction includes this thread token, as shown in *[Figure 9.1](#c09.xhtml#fig9_1)*. It is critical that this token is unique, so it is created using a minting policy that requires a specific UTXO as an input. By leveraging the underlying uniqueness of UTXOs, it can only be spent once, and we can guarantee that the thread token will be unique.

![](OEBPS/images/Figure-9.1.jpg)

**Figure 9.1:** Thread Token Example

A thread token can be used to control the sequence of validator script execution. Every transaction must include the thread token, guaranteeing that only one transaction can be executed at any time. This is useful if you are trying to update some type of state and need the validator to ensure the correct before and after state transitions (refer to *[Figure 9.1](#c09.xhtml#fig9_1))*. This is also useful to confirm preconditions such as whether a token has been minted in a separate transaction. By using a thread token, Smart Contracts can communicate with each other using the existence (or absence) of a particular token in a transaction.

# [Beacon Token](#toc.xhtml#s199a)

A Beacon Token[¹](#c09.xhtml#ftn1) is used to easily identify the address of a specific UTXO that contains a Beacon Token. There are many examples where UTXOs are created, and the off-chain application needs to keep track of these UTXOs. As we saw in *[Chapter 8, Tooling](#c08.xhtml)*, chain indexers can capture the minting transaction information and record the UTXO and address containing a token. The indexers can also monitor token movement and be able to provide the current address where a token resides. This is useful if you need to provide a list of UTXOs that match a specific Beacon Token. A Beacon Token can also be used as a Thread Token, combining both the Thread Token and Beacon Token design patterns.

# [Order Book](#toc.xhtml#s200a)

To take advantage of the EUTXO model for concurrency and scalability, you need to design your application, which will scale as the number of users grows. Fortunately, the EUTXO architecture can facilitate this because it uses local state and is fully deterministic. This means that multiple concurrent users can interact with your application, each with their own UTXOs that are independent of each other. Therefore, as more users use the application, there is no centralized access that will limit throughput as in global state systems. Additionally, local state is well suited for creating **state channels** and **zero-knowledge proofs** to segment a set of UTXOs for scaling solutions.[²](#c09.xhtml#ftn2) We will discuss scaling solutions such as Hydra in *[Chapter 11, Testing, Security, and Scaling](#c11.xhtml).*

An Order Book design is an example of leveraging EUTXO architecture’s benefits. In particular, the design involves a three-step process:

**Step 1**: Place an order on-chain with a UTXO locked at a contract script address

**Step 2**: Identify or monitor the orders off-chain for a match

**Step 3**: Submit a transaction to fill (or cancel) the order

In a simplified example, as shown in *[Figure 9.2](#c09.xhtml#fig9_2)*, a swap script address uses a parameter to record the asked asset, the offered asset, Beacon Token and the public key hash (`PKH`) of the user wallet. This creates a unique swap address for each asset pair. The `PKH` is used, so only the wallet that placed the order can cancel it. A unique Beacon Token is attached to each order UTXO so that off-chain code can easily find all swaps when looking for order matches.

![](OEBPS/images/Figure-9.2.jpg)

**Figure 9.2:** Simplified Order Book Example

Alice and Bob have positions that can be swapped without any third-party intermediary. A swap position can be partially filled, or swap positions can be aggregated together to fill multiple swaps. This is known as composability, and teams like Cardano Swaps[³](#c09.xhtml#ftn3) advocate order book design standards to enable swap composability across the Cardano ecosystem.

In *[Figure 9.2](#c09.xhtml#fig9_2),* Alice offers 100 Ada for 50 WMT tokens, and Bob offers 50 WMT tokens for 100 Ada. This valid swap is detected off-chain, and a Fill Order transaction is submitted on-chain to execute the swap. Once the Fill Order is completed, the Ada and WMT tokens in the swaps are transferred to each party. Bob gets 100 Ada, and Alice receives 50 WMT tokens. Charlie decides to cancel his swap position without any third-party intermediary and is allowed to do so because he can sign the transaction with the required public key hash (`PKH`).

The Order Book design pattern works well because of the following Cardano EUTXO architecture principles[⁴](#c09.xhtml#ftn4):

*   Local state
*   Independent and unique wallet UTXOs and smart contracts
*   Immutable UTXOs
*   Determinism
*   On-chain verification and Off-chain computation
*   Parallel transaction processing

An Order Book design can be applied to many different use cases that involve exchanging value between two or more parties.

# [Anti-Patterns](#toc.xhtml#s201a)

Now that we have looked at design patterns that take advantage of EUTXO architecture, let’s look at some design patterns we should avoid. Most of the anti-patterns are design approaches that come from an account model such as Ethereum.

# [Liquidity Pools](#toc.xhtml#s202a)

The concept of a centralized liquidity pool was introduced, where users can pool their liquidity in trading pairs. This would create an automated market maker (AMM) for market orders, as shown in *[Figure 9.3](#c09.xhtml#fig9_3)*.

![](OEBPS/images/Figure-9.3.jpg)

**Figure 9.3:** Liquidity Pools

The disadvantage of this approach is that liquidity is aggregated into a centralized pool and typically involves custodial ownership. It means that someone else has the keys to spend your funds and you no longer have direct control over them. This also makes for an excellent attack vector, which is why we saw over $3.1 billion USD stolen in 2022 from DeFi protocols.[⁵](#c09.xhtml#ftn5) In this model, we must also introduce **Liquidity Provider (LP)** pools where LP tokens are staked to incentivize liquidity providers. This is not required in an order book design pattern and adds complexity. Finally, the negative side effect of impermanent loss only occurs with centralized AMM pools. This worsens the more significant change (+/-) in the price of an asset pair being provided as liquidity.[⁶](#c09.xhtml#ftn6)

# [Batchers](#toc.xhtml#s203a)

To make matters worse, when this design pattern is used in an EUTXO architecture, the centralized liquidity pools create UTXO contention and scalability is impacted as more users are added. To mitigate this, another anti-pattern involves Batchers processing an order on the user’s behalf, as shown in *[Figure 9.4](#c09.xhtml#fig9_4)*.

![](OEBPS/images/Figure-9.4.jpg)

**Figure 9.4:** Batchers

Batchers, unfortunately, introduces centralization where typically only approved entities can run a Batcher and add liquidity to a pool or execute a swap. This can also lead to front-running transactions to the detriment of users trying to get the best price for a swap. On Ethereum, this is known as miner extractable value (MEV).

# [Cardano Improvement Proposals](#toc.xhtml#s204a)

**Cardano Improvement Proposals (CIPs)**[⁷](#c09.xhtml#ftn7) are standards or references for design and implementation best practices. We will review the following CIPs and how they apply to our application design.

# [CIP-0003 Wallet Key Generation](#toc.xhtml#s205a)

In our ticket application design, the application will need to sign a transaction in addition to the signatures from the end user. For an application to sign a transaction, we must create a private and public key following the standards defined in CIP-0003.[⁸](#c09.xhtml#ftn8) CIP-0003 references BIP-39 which uses a mnemonic seed phrase to generate a wallet and is used for entropy. The CIP also references HD Wallets already covered in *[Chapter 3, Transactions](#c03.xhtml).*

# [CIP-0030 Cardano dApp-Wallet Web Bridge](#toc.xhtml#s206a)

CIP-0030[⁹](#c09.xhtml#ftn9) is a standard for browser-based, wallet integration. It specifies the JavaScript APIs that are injected into the browser window and how a web application can interact with them. We will use CIP-0030 in our application design, but it should be noted that there is a newer standard under review that allows for **P2P** wallet communication and is documented in CIP-0045.[^(10)](#c09.xhtml#ftn10)

# [CIP-0032 Inline Datums](#toc.xhtml#s207a)

CIP-0032[^(11)](#c09.xhtml#ftn11) improved Cardano Smart Contract development and efficiency. Before CIP-0032, only a Datum hash could be stored on-chain, not the actual Datum values. This meant that an application would have to recreate the Datum value, which made it challenging for other Smart Contracts to use it. With CIP-0032, the Datum value can reside on-chain so applications can simply reference the on-chain value. The Datum value is locked inside a UTXO, which Smart Contracts can access as part of a transaction. Combining CIP-0032 and CIP-0031 (reference inputs) allows for read-only data values on-chain and is frequently used by Oracle data providers today.

# [CIP-0040 Explicit Collateral Output](#toc.xhtml#s208a)

A new type of output, called Collateral Outputs, was introduced with CIP-0040.[^(12)](#c09.xhtml#ftn12) Collateral, as we recall from *[Chapter 4, Plutus](#c04.xhtml)*, is required as a deposit that is used if a Plutus script phase two evaluation fails. Although this helps to protect the network against spam or malicious attacks, it also introduces an additional Ada requirement to submit a transaction. Using collateral outputs, a transaction can be constructed so that we can use any UTXO as collateral, but only consume the deposit amount if needed and return the change as a collateral return output. Before CIP-0040, a pure UTXO with only Ada could only be used as the collateral input.

# [CIP-0068 Datum Metadata Standard](#toc.xhtml#s209a)

CIP-0068[^(13)](#c09.xhtml#ftn13) is a standard that defines a way to store token metadata using a datum. This is different from CIP-0025, which stores token metadata using transaction metadata. The advantage of using a Datum is that it can be updated and read directly by a smart contract. This standard applies to Non-Fungible Tokens (**NFT**s) or Fungible Tokens (**FT**s). CIP-0068 involves creating a reference token linked to the original token(s) minted, as shown in *[Figure 9.5](#c09.xhtml#fig9_5)*. This design allows the **NFT**s or **FT**s to move around on the blockchain, but the reference token remains in one location.

![](OEBPS/images/Figure-9.5.jpg)

**Figure 9.5:** CIP-0068

The token naming convention is to prefix hex-encoded labels such as 222 for **NFT**s and 100 for the reference token. The common labels to prefix are listed in *[Table 9.1](#c09.xhtml#tab9_1).*

| **Label** || **Class** || **Description** || **Hex Encoded Label** |
| --- | --- | --- | --- |
| 100 || NFT || Reference Token located at reference token address || `000643b0` |
| 222 || NFT || Non-Fungible Token at wallet or script address || `000de140` |
| 333 || FT || Fungible Token at wallet or script address || `0014df10` |
| 444 || RFT || Rich-Fungible Token at wallet or script address. This can be used to represent fractional NFT ownership || `001BC280` |

**Table 9.1:** CIP-0068 Labels[^(14)](#c09.xhtml#ftn14)

The token name must be identical, allowing the two tokens to be linked to or reference each other. For more detailed information and with basic examples, please review CIP-0068 on GitHub.[^(15)](#c09.xhtml#ftn15)

The steps to create your own label are[^(16)](#c09.xhtml#ftn16):

1.  Convert the decimal label to hex[^(17)](#c09.xhtml#ftn17)
2.  Get the checksum of the hex[^(18)](#c09.xhtml#ftn18)
3.  Drop the 0x and use the last 2 digits
4.  Concat the 4-digit hex and the 2-digit checksum, then add a zero to the start and end

# [The Application Architecture](#toc.xhtml#s210a)

Using our knowledge of EUTXO design patterns and standards, we are now ready to create the application architecture for a ticket application where users can mint, burn, buy, sell and redeem event tickets.

# [On-Chain State Machine Diagrams](#toc.xhtml#s211a)

The complete **state machine** diagram for the ticket token lifecycle is shown in *[Figure 9.6](#c09.xhtml#fig9_6).* We will look at how the application transitions to each state in detail.

![](OEBPS/images/Figure-9.6.jpg)

**Figure 9.6:** Ticket State Machine

# [Minting Tickets](#toc.xhtml#s212a)

Tickets for an event must be first minted and sent to the holding validator script, as shown in *[Figure 9.6](#c09.xhtml#fig9_6).* The Ticket Minting Policy in *[Figure 9.7](#c09.xhtml#fig9_7),* shows the script parameters that will be used including the UTXO input, name of event, show time, number of tickets minted, stake and payment `PKH`, holding validator address, and the minimum amount of lovelace. The ticket holding script requires the stake key signature to move the ticket tokens locked at this script address. Transaction metadata is created to record the minting policy script parameters which can be used for future minting policy-related transactions (for example, burn or convert). The payment PKH will be used for the payment address when the ticket is sold (converted).

![](OEBPS/images/Figure-9.7.jpg)

**Figure 9.7:** Mint Tickets Transaction

# [Burning Tickets](#toc.xhtml#s213a)

The minting policy will allow the burn of any token that belongs to the minting policy, as shown in *[Figure 9.8](#c09.xhtml#fig9_8)*. Unsold tickets may be burned to reduce the supply of event tickets. The mint is a one-time event, but the burn can happen any time after the mint. Typically, however, an event organizer will not want to burn purchased/converted ticket tokens, which could be used for rewards, special access to content, or future events.

![](OEBPS/images/Figure-9.8.jpg)

**Figure 9.8:** Burn Ticket Transaction

# [Opening Swap](#toc.xhtml#s214a)

Opening a swap requires executing both a spending and a minting script within the same transaction. In this case, we must execute Transfer Tickets, as detailed in *[Figure 9.9](#c09.xhtml#fig9_9),* and Mint Beacon outlined in *[Figure 9.10](#c09.xhtml#fig9_10)*. The price of the swap is specified in the Datum and is updateable. For example, if the `askedAsset` is set to 10 Ada, the swap can only be executed if 10 Ada is paid for each ticket token.

![](OEBPS/images/Figure-9.9.jpg)

**Figure 9.9:** Transfer Tickets Transaction

As we recall from the previous section, the Beacon Token is used to easily find off-chain the swap script UTXOs. The Beacon Token minting policy outlined in *[Figure 9.10](#c09.xhtml#fig9_10)* will be the same for all Beacons related to the marketplace owner, but each Beacon token name will be linked to a unique UTXO that is spent as part of the mint transaction. This is how we ensure the uniqueness of each Beacon Token. The stake `PKH` used to mint the event tickets must also sign the transaction when transferring ticket tokens to open a swap position.

![](OEBPS/images/Figure-9.10.jpg)

**Figure 9.10:** Mint Beacon Transaction

# [Updating Swap](#toc.xhtml#s215a)

The user can update a swap position at any time if the following two conditions are true:

*   The stake PKH of the wallet matches the stake `PKH` in the swap contract parameter.
*   The Beacon Token specified as in the swap contract parameter is always returned to the script address.

If both conditions are true, then the smart contract will allow an update to the price, as shown in *[Figure 9.11](#c09.xhtml#fig9_11)*. The types of assets being swapped, however, cannot be changed since this is hardcoded as a contract parameter.

![](OEBPS/images/Figure-9.11.jpg)

**Figure 9.11:** Update Swap Transaction

# [Executing Swap](#toc.xhtml#s216a)

Anyone can execute a swap provided that the price of `askedAsset` is met. The amount of `offeredAsset` (ticket tokens) available to purchase will be the amount of the ticket tokens locked in the swap UTXO, as shown in *[Figure 9.12](#c09.xhtml#fig9_12)*. The swap validator will also ensure that the Beacon Token is always sent back to the validator script address, the seller receives the correct amount of `askedAsset` and the buyer receives the correct amount of `offeredAsset` (ticket tokens).

![](OEBPS/images/Figure-9.12.jpg)

**Figure 9.12:** Execute Swap Transaction

During the swap Execute transaction, we must also convert the ticket token into a unique ticket token that can be marked *used* when entering the venue. We do this by both burning the original ticket token and minting a new one within the same transaction, as illustrated in *[Figure 9.13](#c09.xhtml#fig9_13).* The Reference Token Datum value is initially set to an empty string but will be populated with the payment PKH when the user prints their ticket.

![](OEBPS/images/Figure-9.13.jpg)

**Figure 9.13:** Convert Ticket Transaction

# [Closing Swap](#toc.xhtml#s217a)

A swap can be closed anytime by the seller, as shown in *[Figure 9.14](#c09.xhtml#fig9_14)*.

![](OEBPS/images/Figure-9.14.jpg)

**Figure 9.14:** Close Swap Transaction

The ticket tokens must be returned to the token holding script address, defined as a swap script parameter. The Burn Beacon transaction detailed in *[Figure 9.15](#c09.xhtml#fig9_15)* must also be included in the Close Swap transaction.

![](OEBPS/images/Figure-9.15.jpg)

**Figure 9.15:** Burn Beacon Token Transaction

# [Print Ticket](#toc.xhtml#s218a)

To access an event, the user must prove that they, in fact, own the ticket token. This is done by using the Print Ticket transaction that will update the reference token datum with the spending PKH signed as part of the transaction, as shown in *[Figure 9.16](#c09.xhtml#fig9_16)*. The application will create a QR code that can be shown later which includes a digital signature of the transaction.

![](OEBPS/images/Figure-9.16.jpg)

**Figure 9.16:** Print Ticket

# [Off-Chain Sequence Diagrams](#toc.xhtml#s219a)

The next section will review the high-level, happy path sequence diagrams that describe how different components within the application interact. Transactions are denoted by `[]`, and any values passed between components, if shown, are denoted by a `()`.

# [Minting Tickets](#toc.xhtml#s220a)

Minting event tickets using the application is shown in *[Figure 9.17](#c09.xhtml#fig9_17)*. The first step is to get a list of UTXOs from the wallet and then build the Mint Ticket transaction. The user will sign the transaction with both their spending key to pay for the transaction costs and the staking key to prove they actually own the staking key. Once the transaction has been successfully submitted, the application database is updated to link the stake key with the new minting policy ID. An Event record is also created to show the new event to the user in the application.

![](OEBPS/images/Figure-9.17.jpg)

**Figure 9.17:** Mint Tickets

# [Connected Wallet](#toc.xhtml#s221a)

When a user connects with their wallet, they can see the list of events they have created, as shown in *[Figure 9.18](#c09.xhtml#fig9_18)*. Additional security measures could be implemented such as requiring the user to sign with their stake key to see the list of events.

![](OEBPS/images/Figure-9.18.jpg)

**Figure 9.18:** Connect Wallet

# [Opening Swap](#toc.xhtml#s222a)

After the tickets have been minted, the user can then decide to open a swap position and sell tickets, as shown in *[Figure 9.19](#c09.xhtml#fig9_19).* The first step is to determine what event Minting Policy Hashes (`MPH`s) belong to the user. Next, we rebuild the Ticket Holding validator to get the script address and UTXO. We then build the Transfer Ticket and Mint Beacon transaction using the wallet UTXOs, Ticket Holding UTXO, Ticket Holding, and Beacon Minting Policy scripts. The application must also sign the transaction with the owner `PKH` to be able to mint the beacon token. This is not required, but allows the application owner, if they need to, control who gets to sell tickets on the application. This could be used for a paywall, `KYC`, or fraud prevention.

![](OEBPS/images/Figure-9.19.jpg)

**Figure 9.19:** Open Swap

# [Viewing Swaps](#toc.xhtml#s223a)

All open swaps created by the application are available by querying the blockchain with the Beacon minting policy, as illustrated in *[Figure 9.20](#c09.xhtml#fig9_20)*. The Beacon minting policy is derived from the application owner’s public key hash, so anyone can query it and rebuild the minting policy script. Blockfrost will return all assets that belong to the beacon minting policy ID, which corresponds to all of the open swap positions. For our application, however, we have stored event and swap information in a database to reduce the latency and costs of each request. So, in our case, we will query the database directly to get the list of swaps, but remember that the blockchain is always the source of truth.

![](OEBPS/images/Figure-9.20.jpg)

**Figure 9.20:** View Swaps

When using data replication in a local database, we need to make sure that we receive updates from the blockchain so we have current and accurate information, as shown in *[Figure 9.21](#c09.xhtml#fig9_21)*.

![](OEBPS/images/Figure-9.21.jpg)

**Figure 9.21:** Blockchain Swap Updates

# [Updating Swap](#toc.xhtml#s224a)

The user can, at any time, update a swap position to change the price. They would select a swap from their own swaps, and update it with the new price (refer to *[Figure 9.22](#c09.xhtml#fig9_22))*. The Beacon token for a swap is used to find the UTXO (and metadata) for a particular swap. Using the wallet UTXOs, swap UTXOS, swap metadata, and the swap script, the transaction can be built and submitted.

![](OEBPS/images/Figure-9.22.jpg)

**Figure 9.22:** Update Swap

# [Executing Swap](#toc.xhtml#s225a)

A buyer can now go to the ticket application and view all available tickets for sale. If the price being paid is what is being asked for, and there is sufficient quantity for the order, then the swap will go through, as shown in *[Figure 9.23](#c09.xhtml#fig9_23)*. Using the wallet UTXOs and the swap UTXO, the value paid for the ticket is sent directly to the seller’s address and the buyer receives the ticket token(s). During the ticket conversion, a reference token is created for each unique ticket token minted. This reference token can only be updated by the application and contains a flag to indicate if a token has been used or not at an event.

![](OEBPS/images/Figure-9.23.jpg)

**Figure 9.23:** Execute Swap

# [Closing Swap](#toc.xhtml#s226a)

A seller will want to close a swap when either the amount of tickets in the swap is zero, or if they no longer want to make the tickets available for sale (refer to *[Figure 9.24](#c09.xhtml#fig9_24))*. The Beacon asset is used to get the swap UTXO needed to build the swap transaction and send the ticket tokens (if any) back to the ticket holding address. The Beacon token is also burned as part of the close transaction, so the swap will no longer appear in the list of available swaps.

![](OEBPS/images/Figure-9.24.jpg)

**Figure 9.24:** Close Swap

# [Print Ticket](#toc.xhtml#s227a)

The ticket application is also used to redeem event tickets to access an event. A user will show a QR code that verifies ownership and this can be done any time before (or at) the event. The QR code is a digital signature that is generated when they have signed a transaction with a wallet that has the ticket token. During the Print Ticket transaction, the reference token datum is updated with the wallet spending PKH. This is then used at the event to validate the spending PKH with the QR code shown. After verifying the QR code at the event, the ticket will be marked used in the application DB, as shown in *[Figure 9.25](#c09.xhtml#fig9_25)*.

![](OEBPS/images/Figure-9.25.jpg)

**Figure 9.25:** Show Ticket

# [Verifying Ticket](#toc.xhtml#s228a)

QR code generation can be done in advance. This avoids having the user bring their wallet to the event venue and submit blockchain transactions at the time of entry. Since the reference token datum may be updated with a payment `PKH` if printed, it is important that the ticket is verified before any secondary transfer. The application has an API that allows for querying the blockchain to confirm if a ticket has been shown or if it has been used to access an event, as shown in *[Figure 9.26](#c09.xhtml#fig9_26)*.

![](OEBPS/images/Figure-9.26.jpg)

**Figure 9.26:** Verify Ticket

# [Conclusion](#toc.xhtml#s229a)

In this chapter, we understood the Thread Token, Beacon Token, and Order Book design patterns and how they leverage the benefits of EUTXO architecture. We looked at anti-patterns such as pools and batchers that typically lead to sub-optimal designs on UTXO blockchains such as Cardano. We explored several Cardano Improvement Proposals (CIPs) and how they relate to our application design. In particular, CIP-0068 was reviewed, as to how it provides a different way to store token metadata using datums. We then started to work on the design for the ticket application using the design patterns and standards reviewed in this chapter. Next, we created state transition diagrams with inputs and outputs for each use case. Then, we created sequence diagrams showing the interactions between system components. We are ready to implement the ticket application in the next chapter, *[Chapter 10, Ticket Application Implementation](#c10.xhtml).*

# [Points to Remember](#toc.xhtml#s230a)

*   Account model design patterns are generally not well suited for an EUTXO architecture.
*   The Thread Token design pattern uses a unique token to help isolate a specific UTXO locked at a script address.
*   A Beacon Token design pattern uses a unique token to easily identify a particular UTXO off-chain.
*   A Beacon Token can be used for both the Thread Token and Beacon Token design patterns.
*   The Order Book design pattern is well suited for the EUTXO architecture because UTXOs are immutable, unique, and independent of each other.
*   Identifying atomic swap pairs can be done using off-chain computation.
*   A Swap is executed on-chain and does not involve any third party intermediary.
*   Atomic swaps retain full self-custody and can be canceled at any time.
*   An Order Book design pattern can be applied to many different use cases
*   Liquidity Pools and Batches are examples of anti-patterns with sub-optimal performance and scalability
*   The CIP-0068 Metadata standard uses Datums to store metadata for NFTs or FTs which can be updateable.
*   The Mint Ticket transaction uses CIP-0025 transaction metadata to publish the minting script parameters.
*   The Open Swap transaction needs to include both Transfer Ticket (`ticket.hl`) and Mint Beacon (`beacon.hl`) in the same transaction.
*   The Execute Swap transaction needs to include both Execute Swap (`swap.hl`) and Convert Token (`ticket.hl`) in the same transaction.
*   Convert Ticket uses CIP-0068 with a Datum value to save a payment PKH for event ticket verification.
*   Update Swap and Close Swap can only be done by the wallet that created the swap and can be done at any time.
*   When printing a ticket for an event, the user must sign a transaction with the wallet’s public key to prove ownership of the ticket token.

# [Multiple Choice Questions](#toc.xhtml#s231a)

1.  How can a Plutus script ensure a correct state transition? 
    1.  Use an on-chain oracle
    2.  Use off-chain metadata
    3.  Use a Thread Token
    4.  Use a Reference Script
2.  Why is EUTXO architecture well suited for Order Books? 
    1.  Uses an account model
    2.  Uses local state
    3.  Uses global state
    4.  UTXO contention
3.  What CIP allows a Smart Contract access to metadata? 
    1.  CIP-0068
    2.  CIP-0031
    3.  CIP-0025
    4.  CIP-0033
4.  How are Order Book swaps usually identified? 
    1.  Thread Token
    2.  Metadata
    3.  Beacon Token
    4.  UTXO
5.  Why must a user sign a transaction to verify ticket token ownership? 
    1.  Prove the ticket token is unique
    2.  Show that the ticket has not already been used
    3.  Prove that the ticket is located at the spending address of the wallet
    4.  To prevent the ticket from being burned

# [Answers](#toc.xhtml#s232a)

1.  c
2.  b
3.  a
4.  c
5.  c

# [Questions](#toc.xhtml#s233a)

1.  What are some of the disadvantages of the Order Book design pattern?
2.  When do you want to use Reference Scripts?
3.  What was the motivation behind CIP-0068?
4.  How do we avoid double spending when processing tickets at an event?
5.  What will happen to the application if a blockchain rollback occurs?

# [Key Terms](#toc.xhtml#s234a)

*   **Anti-Patterns:** Design patterns that should be avoided.
*   **FT:** Fungible Token
*   **KYC:** Know Your Customer
*   **MPH:** Minting Policy Hash
*   **NFT:** Non-Fungible Token
*   **PKH:** Public Key Hash
*   **P2P:** Peer-to-Peer communication
*   **State Channel:** Segmenting a set of UTXOs to be processed off-chain chain that mirrors the same protocol as the base layer.
*   **State Machine:** Describes system state transition lifecycles.
*   **UTXO:** Unspent Transaction Outputs
*   **UTXO Contention:** A concurrency issue with more than one transaction is trying to spend a UTXO input.
*   **Zero Knowledge**: Uses cryptography to prove a claim without revealing the details of the claim.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c09.xhtml#ftn1a) [https://github.com/cardano-foundation/CIPs/pull/466](https://github.com/cardano-foundation/CIPs/pull/466)

[²](#c09.xhtml#ftn2a) Jarek Hirniak, “Axo Protocol Whitepaper: The New era of trading”

[³](#c09.xhtml#ftn3a) [https://github.com/fallen-icarus/cardano-swaps](https://github.com/fallen-icarus/cardano-swaps)

[⁴](#c09.xhtml#ftn4a) Lars Brunjes et al., “Building UTxO optimized Dapps”

[⁵](#c09.xhtml#ftn5a) Chainalysis, “2022 Biggest Year Ever For Crypto Hacking with $3.8 Billion Stolen…”

[⁶](#c09.xhtml#ftn6a) Jarek Hirniak, “Axo Protocol Whitepaper: The New era of trading”, 19

[⁷](#c09.xhtml#ftn7a) [https://cips.cardano.org/](https://cips.cardano.org/)

[⁸](#c09.xhtml#ftn8a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0003](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0003)

[⁹](#c09.xhtml#ftn9a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0030](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0030)

[^(10)](#c09.xhtml#ftn10a) [https://github.com/cardano-foundation/CIPs/pull/395](https://github.com/cardano-foundation/CIPs/pull/395)

[^(11)](#c09.xhtml#ftn11a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0032](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0032)

[^(12)](#c09.xhtml#ftn12a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0040](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0040)

[^(13)](#c09.xhtml#ftn13a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0068](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0068)

[^(14)](#c09.xhtml#ftn14a) [https://developers.cardano.org/docs/governance/cardano-improvement-proposals/cip-0068/](https://developers.cardano.org/docs/governance/cardano-improvement-proposals/cip-0068/)

[^(15)](#c09.xhtml#ftn15a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0068](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0068)

[^(16)](#c09.xhtml#ftn16a) [https://github.com/inimrod/cip68-fungible-token-demo/blob/main/src/lib/init-vars.ts](https://github.com/inimrod/cip68-fungible-token-demo/blob/main/src/lib/init-vars.ts)

[^(17)](#c09.xhtml#ftn17a) [https://www.rapidtables.com/convert/number/decimal-to-hex.html](https://www.rapidtables.com/convert/number/decimal-to-hex.html)

[^(18)](#c09.xhtml#ftn18a) [https://crccalc.com/](https://crccalc.com/)

# [CHAPTER 10](#toc.xhtml#c10)

# [Ticket Application Implementation](#toc.xhtml#c10)

# [Introduction](#toc.xhtml#s235a)

In this chapter, we will walk through the implementation of the ticket application, including blockchain integration. We will start with an overview of the system components and application stack, which include CharkraUI, Next.js, Redis DB, and Blockfrost. Next, we will look at the front-end and off-chain code that is used to build the transactions that we defined in *[Chapter 9, Ticket Application Design](#c09.xhtml)*. Then, we will examine the corresponding Smart Contract on-chain code, business logic, and validation rules. We will look at the back-end components, such as the Redis DB schema set up to cache and query relevant blockchain data. We will also look at the application APIs and Blockfrost webhooks that are called when a blockchain event occurs. Finally, we will run through an end-to-end demo of the application.

# [Structure](#toc.xhtml#s236a)

In this chapter, we will discuss the following topics:

*   Application Stack
*   Application Resources
*   Front-end Components
*   Smart Contracts
*   Back-end Components
*   Application Demo
*   Blockchain Benefits

# [Application Stack](#toc.xhtml#s237a)

In our ticketing application, we need the ability to search and filter on an arbitrary number of swaps that contain tickets for sale. This can be done efficiently if we store the swap details in an application database with indexes for quick access. The source of truth, however, will always be the blockchain, and the database is simply a cached copy of the blockchain data. By introducing data replication, we must ensure that the database is updated accordingly when a transaction is submitted to the blockchain. *[Figure 10.1](#c10.xhtml#fig10_1)* shows how swap searches are queried against the local application database, which is continually updated as new relevant blockchain data arrives via a Blockfrost webhook.

![](OEBPS/images/Figure-10.1.jpg)

**Figure 10.1:** System Components

Next.js will be used as the application server framework for building the html and JavaScript components. The application will also use a Redis DB with a **full stack JSON** and search modules for fast, in-memory database storage and retrieval. For improved error handling and troubleshooting, all transactions will be submitted using the Blockfrost API. This approach allows us to easily change the blockchain API service provider if required to do so. We will also use Blockfrost webhooks to monitor the blockchain for transaction confirmations that involve a swap created by the end user.

# [Application Resources](#toc.xhtml#s238a)

The application uses the Next.js directory structure, as shown in *[Figure 10.2](#c10.xhtml#fig10_2)*.

![](OEBPS/images/Figure-10.2.jpg)

**Figure 10.2:** Next.js Directory Structure

# [Common](#toc.xhtml#s239a)

The `common` folder contains client-side JavaScript code that may be used by one or more UI components. The following files are found in this directory:

*   `metadata.ts`: used for creating transaction metadata
*   `network.ts`**:** used for interacting with network APIs
*   `orders.ts`**:** used for order calculations
*   `types.ts`**:** defines custom data types
*   `utils.ts`**:** includes utility functions

# [Components](#toc.xhtml#s240a)

All React **functional components** are located in this folder, which are used to build out the application web pages or popup windows.

# [Config](#toc.xhtml#s241a)

This folder defines the application settings, which include the list of supported wallets, network, theme settings, and compilation flags, if applicable.

# [Init](#toc.xhtml#s242a)

The `init` folder contains a command line script for generating the application owner’s public and private keys. The owner public key is used when minting the beacon token so that we can identify all swaps created by this application instance.

# [Lib](#toc.xhtml#s243a)

The `lib` folder contains JavaScript libraries needed by the Redis connection library.

# [Node Modules](#toc.xhtml#s244a)

This folder stores all of the npm node modules and is created automatically when the `npm` `install` command is executed.

# [Pages](#toc.xhtml#s245a)

The `pages` folder contains all of the web pages and popup windows that are used in the application.

# [Pages / API](#toc.xhtml#s246a)

The `api` folder includes all of the application API interfaces called by client-side JavaScript and any webhooks called by Blockfrost. All client-side JavaScript network calls are made through these application APIs to avoid browser CORS errors and API key leakage.

# [Public](#toc.xhtml#s247a)

The public folder contains all static, publicly available resources such as icons and images.

# [Public/Contracts](#toc.xhtml#s248a)

The `contracts` folder contains all of the Smart Contract on-chain code. In particular, it contains all the business logic for the Smart Contracts that we need for this application:

*   `beacon.hl`: Smart Contract for the beacon minting policy
*   `holding.hl`: Smart Contract for the ticket holding validator
*   `swap.hl`**:** Smart Contract for all swap operations (open, update, close, and execute)
*   `ticket.hl`**:** Smart Contract for the ticket minting policy

# [Schema](#toc.xhtml#s249a)

The `schema` folder contains the database schemas used to define the data structures that will be stored in the Redis database. These include the following:

*   `beacon.ts`**:** This schema is used to store and keep track of beacons created by the application so they can be retrieved easily.
*   `event.ts`**:** The event schema is used to store event information locally that is linked to the stake key hash of the user.
*   `stake.ts`**:** The stake schema maps all of the event assets created to a user’s wallet stake key.
*   `swap.ts`**:** The swap schema stores swap information so that the swap can be quickly retrieved, filtered, and shown to the user.

# [Front-end Application](#toc.xhtml#s250a)

The full source code is located on the GitHub repository, so this section will look at only code fragments to highlight the key aspects of the application. The application is a single-page application with React functional components, as shown in *[Figure 10.3](#c10.xhtml#fig10_3)*. Chakra UI was chosen for its ease of use and out-of-the-box components and is used for all of the styles and front-end UI components. For more information on Chakra, please see their documentation.[¹](#c10.xhtml#ftn1)

![](OEBPS/images/Figure-10.3.jpg)

**Figure 10.3:** React Functional Components

The main entry point to the application is located in `pages/index.tsx` with a tab navigation containing the Get Tickets, My Events, and My Tickets views. The `index.tsx` page also contains the following global state variable information:

*   `walletAPI`**:** The `walletAPI` JavaScript object for the browser extension wallet.
*   `walletInfo` lists the wallet base address, stake address, lovelace balance, and event assets associated with this wallet.
*   `swapViewRefresh` will trigger a `useEffect` to refresh the list of swaps to show to the user. This is called when a change is made to a swap such as opening, updating, or closing a swap.

# [Header and Footer](#toc.xhtml#s251a)

The Header and Footer components are included in the `components/layout.tsx` file and contain static information only.

# [Wallet Connector](#toc.xhtml#s252a)

The wallet connector is a key component and contains the logic to connect to the `walletAPI` object and saves the wallet information to a `useState` variable in `pages/index.tsx`. The `walletAPI` and `walletInfo` variables are made available to all other components by passing them as props to every child and sub-child component. We build upon the same code and logic for connecting to a user wallet as discussed in *[Chapter 5, Transaction Builder](#c05.xhtml).* To improve the user experience, a list of installed and supported browser wallets is presented to the user to select from, as shown in *[Figure 10.4](#c10.xhtml#fig10_4).*

![](OEBPS/images/Figure-10.4.jpg)

**Figure 10.4:** Get Available Wallets[²](#c10.xhtml#ftn2)

There also exists a Wallet Connect[³](#c10.xhtml#ftn3) component created by the Cardano Foundation. However, due to overlap and duplication with the off-chain transaction builder frameworks, we will not be using it.

# [Swap View](#toc.xhtml#s253a)

The swap view component obtains a list of swaps by calling `getFilterSwaps()` on line 43 in *[Figure 10.5](#c10.xhtml#fig10_5).* Filters will only be applied if they are set by the user using the `Filter` Button on the Get Tickets tab. SWR[⁴](#c10.xhtml#ftn4) is used to cache the list of Swaps unless the `getFilterSwaps()` returns a different result.

![](OEBPS/images/Figure-10.5.jpg)

**Figure 10.5:** Get FilterSwaps[⁵](#c10.xhtml#ftn5)

The array of swaps returned populates each swap card and paginates the view if necessary. Filter parameters are defined as state variables in the `SwapView` component and applied to the database query. The list of filter parameters is shown in *[Figure 10.6](#c10.xhtml#fig10_6)*.

![](OEBPS/images/Figure-10.6.jpg)

**Figure 10.6:** Filter Parameters[⁶](#c10.xhtml#ftn6)

The API call to `pages/api/getFilterSwaps.ts` first creates a record object of the key/value filter parameters, as shown in *[Figure 10.7](#c10.xhtml#fig10_7).*

![](OEBPS/images/Figure-10.7.jpg)

**Figure 10.7:** getFilterSwaps API[⁷](#c10.xhtml#ftn7)

The record object is then passed to the `dynamicQuery()` function in *[Figure 10.8](#c10.xhtml#fig10_8)*, which dynamically constructs the Redis database query and returns a filtered list of swaps.

![](OEBPS/images/Figure-10.8.jpg)

**Figure 10.8:** Redis Database Dynamic Query[⁸](#c10.xhtml#ftn8)

# [Swap Card](#toc.xhtml#s254a)

Each Swap Card is passed the `swap`, `walletAPI`, `walletInfo`, and `setSwapViewRefresh` as props, as shown in *[Figure 10.9](#c10.xhtml#fig10_9)*. These variables and functions display the Swap Card and are also passed to the `ExecuteSwap`, `UpdateSwap`, or `Close` `Swap` popup windows to build and submit a transaction.

![](OEBPS/images/Figure-10.9.jpg)

**Figure 10.9:** SwapCardProps Interface[⁹](#c10.xhtml#ftn9)

To execute a swap, a user selects the “`Buy`” button that changes the `buySwapOpen` variable to true. When this occurs, the `ExecuteSwapPopup` page component is shown to the user (see *[Figure 10.10](#c10.xhtml#fig10_10)*).

![](OEBPS/images/Figure-10.10.jpg)

**Figure 10.10:** Execute Swap Popup Component[^(10)](#c10.xhtml#ftn10)

# [Event View](#toc.xhtml#s255a)

The layout of the event page is similar to the swap view but requires the user to connect their wallet. Each event is linked to the wallet’s stake key, so we must connect the wallet first before creating a new event or seeing events already created.

# [Event Card](#toc.xhtml#s256a)

The Event View contains Event Cards for each event linked to the connected wallet. The user can either sell tickets or archive the event. It also displays event statistics, such as the number of tickets allocated, released, and converted. All of this information is available on the blockchain, but we also update the database directly to provide faster, real-time updates within the application.

# [My Tickets](#toc.xhtml#s257a)

On the `My Tickets` screen, the user is able to see the tickets that they currently have in their browser wallet with relevant metadata information such as event image, name, location, and showtime. This is also where the user can print each ticket and view the verification QR code, as shown in *[Figure 10.11](#c10.xhtml#fig10_11).* The NFT event tickets are Cardano native tokens, so they can also be viewed directly within the wallet or transferred to any other wallet or dApp, just like Ada.

![](OEBPS/images/Figure-10.11.jpg)

**Figure 10.11:** My Tickets View

# [Print Tickets](#toc.xhtml#s258a)

When the `Print Ticket` Button is selected, a `Print Ticket` popup window will appear and allow the user to generate the QR code. Once the transaction is signed and the reference ticket CIP-68 metadata is updated, the QR code will be displayed. The signing of the transaction proves that they control the private key corresponding to the public key that the ticket asset is locked at. When the QR code is presented to the venue, the unique ticket will be marked used in the application DB to prevent double-redeeming of the ticket.

The `Verify` Button in *[Figure 10.11](#c10.xhtml#fig10_11)* can be used to simulate a ticket redemption and granting access to an event. The QR code can be generated and saved in advance, which avoids having the user bring their wallet to the event venue and submitting a blockchain transaction at the time of entry. If the event ticket token is subsequently transferred to another person, the reference token datum history should be checked to confirm that it has not already been printed (or redeemed). The QR code is a string that includes the ticket asset name (minting policy hash + token name), the transaction hash, and the **witness signature** for the transaction that was signed and submitted, as shown in *[Figure 10.12](#c10.xhtml#fig10_12)*.

![](OEBPS/images/Figure-10.12.jpg)

**Figure 10.12:** QR Code Generation[^(11)](#c10.xhtml#ftn11)

# [Transaction Builder](#toc.xhtml#s259a)

The off-chain transaction builder code for swap operations such as open, update, execute, and close is done inside a popup window. When a popup window is enabled, a `useEffect` is triggered to call the appropriate function to build the off-chain transactions, as shown in *[Figure 10.13](#c10.xhtml#fig10_13)*.

![](OEBPS/images/Figure-10.13.jpg)

**Figure 10.13:** Execute Swap useEffect[^(12)](#c10.xhtml#ftn12)

The off-chain code follows a similar pattern to the off-chain builder code in previous chapters. For an Execute Swap transaction, we will apply the contract parameters to build the Plutus script. If the swap validation is successful, we use the ticket minting policy to convert each ticket. Following the CIP-68 Metadata NFT standard, both the NFT token and the reference token are minted. On lines 224–227 in *[Figure 10.14](#c10.xhtml#fig10_14),* both the NFT tokens and the reference tokens are added to arrays that contain the total number of tokens to mint.

![](OEBPS/images/Figure-10.14.jpg)

**Figure 10.14:** Convert Tickets[^(13)](#c10.xhtml#ftn13)

During the swap transaction, we update the datum and create the outputs that will satisfy the business logic in the swap validator. This will ensure that the asking price and the amount of offered assets are correct. The `calcOrderDetails()` function determines the values that must be sent to the buyer and seller and returned to the swap, as shown in *[Figure 10.15](#c10.xhtml#fig10_15)*.

![](OEBPS/images/Figure-10.15.jpg)

**Figure 10.15:** Calc Order Details[^(14)](#c10.xhtml#ftn14)

In the ticket application, we also introduce the concept of time to ensure that a swap transaction is executed within a specific period of time. It is best practice to explicitly set the **time interval,** which must be set when checking for time constraints within a Plutus script. *[Figure 10.16](#c10.xhtml#fig10_16)* shows a typical off-chain validity interval.

![](OEBPS/images/Figure-10.16.jpg)

**Figure 10.16:** Time Validity Interval[^(15)](#c10.xhtml#ftn15)

Once a validity interval has been set, a Plutus script can determine if a transaction occurs before, after, or during a specified time interval. In the next section, we will look at the on-chain code since we need to ensure the swap does not execute after a specific deadline (for example, showtime).

If the transaction is successfully built, signed, and submitted then we update the application database to increment the ticket converted amount and decrement the offered quantity in the swap. We will also include the transaction ID and set the confirmation flag to false on lines 481–482 in *[Figure 10.17](#c10.xhtml#fig10_17)*. There will be a Blockfrost webhook to make a callback to the application after 3 block confirmations and to set the confirm flag to `true`. Finally, a call to `handleClose()` on line 493 is used to force a refresh of the swaps and events in the `Swap View` and `Event View`, respectively.

![](OEBPS/images/Figure-10.17.jpg)

**Figure 10.17:** Swap and Event DB Updates[^(16)](#c10.xhtml#ftn16)

# [Smart Contracts](#toc.xhtml#s260a)

The ticket application on-chain code involves the following Plutus scripts:

*   Beacon Minting Policy
*   Ticket Minting Policy
*   Holding Validator
*   Swap Validator

# [Beacon Minting Policy](#toc.xhtml#s261a)

The beacon on-chain code is passed a transaction ID and index via the Redeemer to create a unique token name so we can easily locate all swaps. This is a different approach than what we saw in *[Chapter 7, Minting](#c07.xhtml)*, where we used the transaction ID and index as contract parameters. The application owner’s PKH is the only contract parameter in the beacon minting policy, as shown in *[Figure 10.18](#c10.xhtml#fig10_18).*

![](OEBPS/images/Figure-10.18.jpg)

**Figure 10.18:** Beacon Redeemer[^(17)](#c10.xhtml#ftn17)

In *[Figure 10.19](#c10.xhtml#fig10_19),* we determine the value of what was minted on line 22, and the value of the minting policy hash for the script itself on line 23. On line 28, we combine both the `TxId` and `TxIdx`, and then hash them using the `blake2b` hash algorithm. This follows what we do in the off-chain code so that the token names being minted are the same as the on-chain code. We also check that only 1 token was minted on line 36 and that no other tokens are minted as part of this minting policy.

![](OEBPS/images/Figure-10.19.jpg)

**Figure 10.19:** Beacon Minting Policy[^(18)](#c10.xhtml#ftn18)

The Redeemer Mint code on lines 38–43 in *[Figure 10.19](#c10.xhtml#fig10_19)* confirms that the min transaction is signed by the application owner PKH and that the transaction ID and index correspond to a UTXO input. Requiring the owner’s signature helps ensure that the PKH provided in the contract parameters is actually owned by the entity submitting the transaction. The Redeemer Burn allows the burning of any token that belongs to this minting policy, as shown in *[Figure 10.20](#c10.xhtml#fig10_20)*.

![](OEBPS/images/Figure-10.20.jpg)

**Figure 10.20:** Beacon Burn

# [Ticket Minting Policy](#toc.xhtml#s262a)

The Ticket Minting Policy has a Mint, Convert, and Burn Redeemer. The Convert Redeemer passes a number of tickets to convert, and a list of unique ticket tokens is minted, as shown in *[Figure 10.21](#c10.xhtml#fig10_21)*. It should be noted that careful consideration is required when passing a list of an arbitrary length. The budget costs for executing this script will depend on how many tickets are included in the `userTicketTokenName` array. In our case, this is required because we are explicitly minting individual unique NFT tokens. Therefore, we need to know each ticket’s name to be able to mint and validate them in the minting and validator script accordingly.

![](OEBPS/images/Figure-10.21.jpg)

**Figure 10.21:** Ticket Minting Policy[^(19)](#c10.xhtml#ftn19)

In *[Figure 10.22](#c10.xhtml#fig10_22),* on lines 27 and 28, a `TxOutputId` is created using the `TX_ID` and `TX_IDX` contract parameters. This will be used to ensure that the minting policy is unique for each event. The `totalAssetVal` function on line 31 is a recursive function that combines all of the NFT tokens and reference tokens into one Value.

![](OEBPS/images/Figure-10.22.jpg)

**Figure 10.22:** Token List Value[^(20)](#c10.xhtml#ftn20)

The Mint Redeemer in *[Figure 10.23](#c10.xhtml#fig10_23)*, lines 68 and 69, confirms that the `TX_ID` and `TX_IDX` contract parameters match a UTXO that is included as an input. On lines 73 and 75, the minting policy confirms that the transaction is signed by the event owner’s stake key and the minted output is sent to the holding validator script. There is also an additional check on line 77 that will cause the transaction to fail if the mint occurs after the event showtime.

![](OEBPS/images/Figure-10.23.jpg)

**Figure 10.23:** Ticket Mint Redeemer[^(21)](#c10.xhtml#ftn21)

The Convert Redeemer calls the `totalAssetVal` function on line 84 in *[Figure 10.24](#c10.xhtml#fig10_24)* and combines the NFT ticket tokens and reference tokens into one Value. By adding the minted NFT and reference tokens with the burned released tokens, we get the total amount minted and burned in this transaction. We also do a safety check to ensure that the quantity passed in the redeemer is always greater than 0 on line 91.

![](OEBPS/images/Figure-10.24.jpg)

**Figure 10.24:** Ticket Convert Redeemer[^(22)](#c10.xhtml#ftn22)

The Burn Redeemer, in *[Figure 10.24](#c10.xhtml#fig10_24)*, allows any amount of allocated, released, or converted tokens to be burned, but this transaction needs to be signed by the event owner’s stake key.

# [Holding Validator](#toc.xhtml#s263a)

The `Holding` Validator script acts as a staging area for ticket tokens that have been minted but not yet released into swaps. They can only be spent by the event owner’s stake key, which is hard-coded as a contract parameter, as shown in *[Figure 10.25](#c10.xhtml#fig10_25)*. The implementation of the holding validator script was somewhat tricky because we wanted to ensure that there was no leakage of tokens when transferring back and forth to the swaps. The challenge is, that when the holding validator is created, the swap address is unknown. So, we run into the scenario with a **circular reference** where the holding script needs to know the swap address, the swap address needs to know the holding address and both should be contract parameters for each other.

To help mitigate this issue, we leverage the beacon token minting policy, which can be calculated in advance. As seen in *[Figure 10.18](#c10.xhtml#fig10_18)*, the `beaconMPH` is set as a contract parameter on line 16. In *[Figure 10.25](#c10.xhtml#fig10_25),* we introduce a new helper function on line 19 called `checkTokenOut` that will return `true` if there are any tokens contained within a set of outputs, which will be used to check for token leakage.

![](OEBPS/images/Figure-10.25.jpg)

**Figure 10.25:** Holding Validator checkTokensOut[^(23)](#c10.xhtml#ftn23)

As seen in *[Figure 10.26](#c10.xhtml#fig10_26)*, the `Transfer` Redeemer is used to transfer the ticket tokens from the holding script to a swap. The transaction must be signed by the event owners’ stake key and must also contain a beacon token. As we recall, every swap must have a beacon token, which will help to ensure that these tickets go to a swap and nowhere else. Only outputs going to the swap and optional holding validator script for change should contain tokens. This rule is enforced on lines 43–49.

![](OEBPS/images/Figure-10.26.jpg)

**Figure 10.26:** Holding Validator Transfer Redeemer[^(24)](#c10.xhtml#ftn24)

The `Return` Redeemer is similar to the `Transfer` redeemer and is used to validate that the ticket tokens from a closed swap are sent back directly to the holding script address. When a swap is closed, the beacon token is always burned, so we check for this condition in the transaction, as shown in *Figure* 10.27, on line 56. There is also only one output going to the holding script address, so we will make sure that this condition is true on line 62. We double-check that no other tokens are in any other outputs on line 64.

![](OEBPS/images/Figure-10.27.jpg)

**Figure 10.27:** Holding Validator Return Redeemer[^(25)](#c10.xhtml#ftn25)

The `Burn` Redeemer simply checks that the transaction is signed by the event owner’s stake key and that no tokens exist in the outputs. When we archive an event, we burn all remaining allocated tokens.

# [Swap Validator](#toc.xhtml#s264a)

We define the datum of the `swap` validator to only contain two Values, the `askedAssetVal` and the `offeredAssetVal`, as shown in *[Figure 10.28](#c10.xhtml#fig10_28).* The `askedAssetVal` contains the asset class (in this case Ada) that we are asking for. The price for an offered asset is the amount set in `askedAssetVal`. So, `askedAssetVal` contains both the type of asset being asked for and the price for each offered asset. The swaps are designed so that an event owner (seller) can update the price of a swap at any time. If the user wants to change the asset they are selling or asking for, then they need to close the swap and create a new one.

The `offeredAssetVal` is used to indicate the asset that is for sale and the amount that is locked in the swap. The `offeredAssetVal` gets updated according to the amount of offered assets that leave the swap. *[Figure 10.28](#c10.xhtml#fig10_28)* shows the datum struct as well as the Redeemer for the swap script. The `Swap` Redeemer is passed a buyer public key hash as well as the quantity and token names that will be converted (minted) in this transaction on lines 11–14.

![](OEBPS/images/Figure-10.28.jpg)

**Figure 10.28:** Swap Validator Datum and Redeemer[^(26)](#c10.xhtml#ftn26)

*[Figure 10.29](#c10.xhtml#fig10_29)* shows the contract parameters and global variables used in the swap validator.

![](OEBPS/images/Figure-10.29.jpg)

**Figure 10.29:** Swap Validator Contract Parameters[^(27)](#c10.xhtml#ftn27)

The `checkAdaVal` function, on line 38 in *[Figure 10.30](#c10.xhtml#fig10_30),* is used to add the minimum amount of Ada (lovelace) if a value contains a native token. For simplicity, we use a fixed minimum of 2,000,000 lovelace for all smart contract token interactions. As we recall, we can only send a native asset so long as there is a minimum amount of lovelace included. The exact amount of lovelace can be determined by calculating the bytes used in a particular UTXO. This amount can be larger or smaller depending on how many tokens are included in a UTXO. Therefore, we tightly control the outputs when sending native tokens to ensure that the correct minimum lovelace is always included.

We also create a function called `totalAssetVal` on line 46, in *[Figure 10.30](#c10.xhtml#fig10_30)*, which is similar to the `totalAssetVal` in the ticket minting policy. For the `Swap` validator, however, we only need to include and validate the ticket tokens and not the reference tokens.

![](OEBPS/images/Figure-10.30.jpg)

**Figure 10.30:** Swap Validator totalAssetVal[^(28)](#c10.xhtml#ftn28)

Inside the main swap validator function, we start off by obtaining the `ScriptContext` and the hash of the validator in *[Figure 10.31](#c10.xhtml#fig10_31)*. Next, we create an `AssetClass` for both the asked assets and the offered assets, which will be used later in the program. On line 84, we get an array of all of the outputs locked at the swap address for this transaction. Fortunately, the order of the outputs is always set explicitly during the off-chain transaction construction. The same cannot be said about inputs that may be re-ordered canonically, so we try to avoid inspecting inputs as much as possible.

![](OEBPS/images/Figure-10.31.jpg)

**Figure 10.31:** Swap Validator main function[^(29)](#c10.xhtml#ftn29)

The `Close` Redeemer in *[Figure 10.32](#c10.xhtml#fig10_32)* checks that the beacon token is burned, no outputs are sent back to the script address, and any offered assets are returned to the holding script address. It also confirms that only a transaction signed with the event owner’s stake key can close a swap position.

![](OEBPS/images/Figure-10.32.jpg)

**Figure 10.32:** Swap Validator Close Redeemer[^(30)](#c10.xhtml#ftn30)

The `Swap` Redeemer creates the beacon and ticket token values that will be part of the transaction outputs in *[Figure 10.33](#c10.xhtml#fig10_33)*. Using the buyer’s PKH and the event owner’s PKH, we obtain the outputs that are sent to the buyer and event owner (seller) addresses, respectively. On lines 121—127, we pull out the required values from the input and output datums, which will be used to validate the swap’s spending conditions.

![](OEBPS/images/Figure-10.33.jpg)

**Figure 10.33:** Swap Validator Swap Redeemer Datum Values[^(31)](#c10.xhtml#ftn31)

Now, we are ready to validate the core swap logic in *[Figure 10.34](#c10.xhtml#fig10_34)*. On line 130, we first check that the asked asset does not change between the input and output datum. On lines 133—136, we check that the *asked asset* in the datum matches what was specified as the contract parameter. On line 140, we also check that the *offered asset* in the datum matches what was specified as a contract parameter as well. Lines 143—149 are the most critical business logic checks that ensure the correct values are sent to the swap, buyer, and seller, respectively. Finally, on line 152, we check that the amount of tokens to be converted matches what is recorded in the datums.

![](OEBPS/images/Figure-10.34.jpg)

**Figure 10.34:** Swap Validator Swap Redeemer Logic[^(32)](#c10.xhtml#ftn32)

The `Update` Redeemer in *[Figure 10.35](#c10.xhtml#fig10_35)* verifies that the transaction is signed by the event owner’s stake `PKH` on line 170. Any changes to the *asked assets* or *offered assets* will require a new swap and are checked on lines 176, 179, and 183. Similar to the Swap Redeemer, the Datum and output values are calculated on lines 165—168. Finally, the swap value is verified to return to the swap address on line 173.

![](OEBPS/images/Figure-10.35.jpg)

**Figure 10.35:** Swap Validator Swap Update Redeemer[^(33)](#c10.xhtml#ftn33)

# [Back-end Application](#toc.xhtml#s265a)

The following sections describe the back-end components that interact with the front-end code to provide blockchain data and state information.

# [Redis DB](#toc.xhtml#s266a)

*[Figure 10.36](#c10.xhtml#fig10_36)* shows the Redis DB schemas to support blockchain data replication and application state management. Access to the Redis DB is only done through API calls and is not directly accessed by the front-end code. Each schema has a corresponding class defined in `common/types.ts`. These classes help serialize and transmit the data structure from the front-end to the back-end API code.

![](OEBPS/images/Figure-10.36.jpg)

**Figure 10.36:** Redis DB Schemas

# [APIs](#toc.xhtml#s267a)

The following is a list of the APIs used to allow communication between the front-end and the back-end application components, such as the Redis DB and Blockfrost.

`$ tree pages/api`

`pages/api`

`├── closeSwap.ts`

`├── getAssetUtxo.ts`

`├── getEvent.ts`

`├── getEvents.ts`

`├── getFilterSwaps.ts`

`├── getTicketMetadataCIP25.ts`

`├── getTicketMetadataCIP68.ts`

`├── getTicketPkh.ts`

`├── getWalletInfo.ts`

`├── printTicket.ts`

`├── setBeacon.ts`

`├── setEvent.ts`

`├── setStakeKey.ts`

`├── setSwap.ts`

`├── signSubmitTx.ts`

`├── submitTx.ts`

`├── updateEvent.ts`

`├── updateSwap.ts`

`├── updateTxStatus.ts`

`└── verifyTicket.ts`

All front-end API calls are made from the `common/network.ts` file, which uses axios[^(34)](#c10.xhtml#ftn34) to make HTTP GET or POST requests. The Blockfrost webhook `updateTxStatus.ts` is called when there is a blockchain transaction matching the beacon minting policy. The webhook is configured to fire after three **blockchain confirmations**. When the Blockfrost webhook is called, it will update the event and swap that has the corresponding transaction ID and mark it confirmed.

# [Redis DB Setup](#toc.xhtml#s268a)

Before running the demo, a Redis DB instance with JSON stack must be created locally or using a cloud instance.

1.  Go to [https://redis.io/](https://redis.io/)
2.  Sign in or create an account.
3.  Create a `$0` subscription.
4.  Create a new Redis Stack database (includes JSON stack).
5.  Select the Databases navigation link on the left-hand side of the page.
6.  Select `Connect` under the Endpoint column.
7.  Then select `Redis` `Client` to obtain your credential information, as shown in *[Figure 10.37](#c10.xhtml#fig10_37)*.

![](OEBPS/images/Figure-10.37.jpg)

**Figure 10.37:** Redis DB Setup

# [Blockfrost Setup](#toc.xhtml#s269a)

1.  Log into the Blockfrost dashboard and create a webhook.
2.  Enter the URL of your application as the Endpoint URL:
    
    `https://your.host.domain.name/api/updateTxStatus`
    
3.  Set the required number of blockchain confirmations.
4.  Enter the Beacon Minting Policy ID as a trigger condition:
    
    `policy id = 421dacdd…e5ad68e76a6`
    
5.  Create another webhook and use the same Endpoint URL, but use the event owner’s stake key as the sender:
    
    `sender = stake_test1uqk6gt…6a5pj6p5qh6lc8v`
    
6.  Copy the Auth Token and add it to the application environment variables:
    
    `export WEBHOOK_AUTH_TOKEN=8e81d5…24e0f5`
    

# [Application Owner Public/Private Key](#toc.xhtml#s270a)

You can use the `generatePrivateKey.mjs` utility in the init folder to create the application owner’s public and private keys.

`$ cd chapter_10/helios/ticket-app`

`$ nvm use 18.17.0`

`$ npm install`

`$ export ENTROPY="put your 24 word seed phrase here"`

`$ node ./init/generatePriveKey.mjs`

`$ export OWNER_PRIVATE_KEY=383be…b632341a4e`

`$ export NEXT_PUBLIC_OWNER_PKH=61942b…653a7d3cdb0`

# [Demo](#toc.xhtml#s271a)

We will now run the application to demo the functionality of the ticket application on the Cardano preprod network. Please ensure the following bash environment variables are set with correct values before starting the application:

`$ cat ~/.bashrc`

`export NEXT_PUBLIC_HOST=localhost`

`export NEXT_PUBLIC_PORT=:3000`

`export NEXT_PUBLIC_PROTOCOL=http`

`export NEXT_PUBLIC_ENV=dev`

`export NEXT_PUBLIC_NETWORK=preprod`

`export REDIS_PASSWORD=CnitD9…9UsOAQ`

`export REDIS_HOST=redis-13…labs.com`

`export REDIS_PORT=13633`

`export BLOCKFROST_API_KEY="prepro…hE1aMi"`

`export BLOCKFROST_API="https://cardano-preprod.blockfrost.io/api/v0"`

`export WEBHOOK_AUTH_TOKEN=8e81d5…24e0f5`

`export OWNER_PRIVATE_KEY=889c4a…7cf5d5`

`export NEXT_PUBLIC_OWNER_PKH=18b022…9e3aeb`

Start the development server:

`$ source ~/.bashrc`

`$ npm run dev`

Use a browser and go to the external port to access the application.

# [Initial Startup](#toc.xhtml#s272a)

*[Figure 10.38](#c10.xhtml#fig10_38)* shows the initial view of the `Get Tickets` page when no swaps have been created. To first create an event, the user connects their wallet and selects the `My Events` tab.

![](OEBPS/images/Figure-10.38.jpg)

**Figure 10.38:** Default Initial Ticket View

# [Connect Wallet](#toc.xhtml#s273a)

When the user selects `Connect` `Wallet`, they are presented with a list of browser wallets that are supported and installed, as shown in *[Figure 10.39](#c10.xhtml#fig10_39)*.

![](OEBPS/images/Figure-10.39.jpg)

**Figure 10.39:** Connect Wallet

# [My Events](#toc.xhtml#s274a)

After the user has connected to their wallet, they can go to the `My Events` tab and will see the list of events they have created. Since we have not yet created any, we will see an empty list of events, as shown in *[Figure 10.40](#c10.xhtml#fig10_40).*

![](OEBPS/images/Figure-10.40.jpg)

**Figure 10.40:** My Events

# [New Event](#toc.xhtml#s275a)

When a user selects the `New Event` button, they will see a popup window that allows them to enter the event details, as shown in *[Figure 10.41](#c10.xhtml#fig10_41)*. When selecting the `Mint Tickets` button, the allocated tickets will be minted and sent to the ticket holding address. In addition, please note that there is a link to view the smart contract at the bottom of the popup window if a user wants to verify the smart contract independently.

![](OEBPS/images/Figure-10.41.jpg)

**Figure 10.41:** New Event

After the `Mint Tickets` button is pressed, the wallet prompts the user to sign a transaction to mint the event tickets. *[Figure 10.42](#c10.xhtml#fig10_42)* shows the successful minting of a batch of 1000 tickets that are sent to the ticket holding script address.

![](OEBPS/images/Figure-10.42.jpg)

**Figure 10.42:** Allocated Tickets

# [Open Swap](#toc.xhtml#s276a)

Next, the tickets are made available for sale by opening a swap position, as shown in *[Figure 10.43](#c10.xhtml#fig10_43).* A description is also added and can be modified for each swap that is opened. The user may release some or all of the tickets from the ticket holding script and put them into the swap position. In this case, we will select 700 tickets to sell now.

![](OEBPS/images/Figure-10.43.jpg)

**Figure 10.43:** Sell Tickets

# [Get Tickets](#toc.xhtml#s277a)

After the user signs the open swap transaction, the tickets will appear in the `Get Ticket` screen, as shown in *[Figure 10.44](#c10.xhtml#fig10_44)*. If the user is still connected to their wallet, the swap will show the ability to either update or close it. This is only available to the owner of the swap position with the correct staking key.

![](OEBPS/images/Figure-10.44.jpg)

**Figure 10.44:** Released Tickets

# [Update Swap](#toc.xhtml#s278a)

Next, we will update the swap and change the price from 12 Ada to 15 Ada on the `Get Tickets` page. The update transaction is successful, as shown in *[Figure 10.45](#c10.xhtml#fig10_45).*

![](OEBPS/images/Figure-10.45.jpg)

**Figure 10.45:** Update Swap

# [Buy Tickets](#toc.xhtml#s279a)

After connecting with the buyer’s wallet, we select the `Buy Tickets` button, as shown in *[Figure 10.46](#c10.xhtml#fig10_46)*. Remember to enable the buyer wallet account with dApp access if this is required in your wallet.

![](OEBPS/images/Figure-10.46.jpg)

**Figure 10.46:** Buy Tickets

We will enter a quantity of four tickets and then select the `Buy Tickets` button. After signing the buy transaction, a purchase success message will appear. The current inventory available in the swap has changed to `696` since we purchased four tickets, as shown in *[Figure 10.47](#c10.xhtml#fig10_47)*.

![](OEBPS/images/Figure-10.47.jpg)

**Figure 10.47:** Buy Tickets

In the wallet transaction history shown in *[Figure 10.48](#c10.xhtml#fig10_48)*, we can also see that 2 Plutus scripts were executed. This allowed us to burn 4 released tickets and mint 4 ticket tokens plus 4 reference tokens. This can also be viewed on a Cardano block explorer.[^(35)](#c10.xhtml#ftn35)

![](OEBPS/images/Figure-10.48.jpg)

**Figure 10.48:** Buy Tickets Wallet Transaction

# [My Tickets](#toc.xhtml#s280a)

Once the transaction has been confirmed on the blockchain, the user can go to the `My Tickets` page to see the tickets in their wallet, as shown in *[Figure 10.49](#c10.xhtml#fig10_49)*. Since the user owns the ticket tokens, they can also send them to another wallet or list them on a Cardano **DEX** for resale. Closer to the time of the event, the user will print their tickets to generate a unique QR code that they present at the event. The QR code is used to verify the ticket and will be marked as used when verified.

![](OEBPS/images/Figure-10.49.jpg)

**Figure 10.49:** My Tickets

# [Print Ticket](#toc.xhtml#s281a)

When the user selects a `Print Ticket` button, they will need to sign a transaction that updates the reference token with the public key hash of the wallet. This way we know for sure that the user actually owns the ticket at the time of printing. If this transaction is successful, the user will be presented with a QR Code that they can save for later and present at the event, as shown in *[Figure 10.50](#c10.xhtml#fig10_50).*

![](OEBPS/images/Figure-10.50.jpg)

**Figure 10.50:** Print Tickets

# [Verify Ticket](#toc.xhtml#s282a)

To simulate verifying a ticket at an event, the `Print Ticket` popup window has a `Verify Ticket` button. When selected, it will check the QR Code signature and message to confirm that they match the public key hash in the database or reference token datum, as shown in *[Figure 10.51](#c10.xhtml#fig10_51).* Only a user with the corresponding private key could have generated this QR Code.

![](OEBPS/images/Figure-10.51.jpg)

**Figure 10.51:** Verify Ticket

# [Close Swap](#toc.xhtml#s283a)

The last part of the demo is to close a swap position. Therefore, we will switch wallets back to the event owner wallet and go to the `My Events` page, as shown in *[Figure 10.52](#c10.xhtml#fig10_52)*. We can now see that 4 tickets have been converted, 696 tickets are in released status, and 300 tickets are in the holding script.

![](OEBPS/images/Figure-10.52.jpg)

**Figure 10.52:** Converted Tickets

On the `Get Tickets` page, using the event owner’s wallet, the swaps are displayed with a `Close Swap` button that returns the tickets back to the holding script, as shown in *[Figure 10.53](#c10.xhtml#fig10_53).*

![](OEBPS/images/Figure-10.53.jpg)

**Figure 10.53:** Close Swap

After the `Close Swap` transaction has been completed, the event owner will see that the number of tickets in the holding script is `996`, as shown in *[Figure 10.54](#c10.xhtml#fig10_54)*.

![](OEBPS/images/Figure-10.54.jpg)

**Figure 10.54:** Holding Tickets

# [Search](#toc.xhtml#s284a)

The user is also able to search for open swaps using either a text-based search or filter on showtime or the number of tickets. In our demo, we now have two swaps open and will text search “`Jane Town`”, which is only found in one of the swaps, as shown in *[Figure 10.55](#c10.xhtml#fig10_55)*.

![](OEBPS/images/Figure-10.55.jpg)

**Figure 10.55:** Search Swaps

Once the user has selected the `Apply Filter` button, only the ticket swaps that match the text are displayed, as shown in *[Figure 10.56](#c10.xhtml#fig10_56)*. We are able to filter the swaps because we have replicated the blockchain swap data and metadata into our application database.

![](OEBPS/images/Figure-10.56.jpg)

**Figure 10.56:** Search Swaps

# [Browser Wallet](#toc.xhtml#s285a)

The ticket tokens can also be viewed directly in the browser wallet, as shown in *[Figure 10.57](#c10.xhtml#fig10_57)*. As previously mentioned, the ticket tokens are Cardano NFT native tokens and can be sent to another wallet or dApp directly without requiring a third party to facilitate the transaction.

![](OEBPS/images/Figure-10.57.jpg)

**Figure 10.57:** Browser Wallet Tokens

# [Blockchain Benefits](#toc.xhtml#s286a)

Currently, we have centralized, close-door event ticket providers with monopolistic control in the market that limits and stifles competition. Using blockchain, an event organizer can create their own ticket sales and redemption processes, leveraging the security and decentralization properties of blockchain. In particular, the advantages of a blockchain solution are as follows:

*   Event data immutability
*   Ticket asset uniqueness and authenticity
*   Fair and transparent ticket allocation and distribution
*   Genuine ticket resale verification
*   Permissionless (or Permissioned) ticket token resellers
*   Trustless auditing of ticket sales and attendance
*   Ticket tokens can also be used for rewards and loyalty points
*   Avoids third-party payment processors and settlement

# [Conclusion](#toc.xhtml#s287a)

In this chapter, we reviewed the implementation details of a more complex, multi-validator blockchain-based application. We explored the concepts of data replication to improve the user experience when dealing with blockchain data and events. We leveraged the technical stack of ChakraUI, Next.js, Redis DB, and Blockfrost to create a fully functional ticketing application. This included managing the complete ticketing lifecycle (mint, sell, buy, redeem). Using a QR code, we showed how the application is able to generate a digital signature to prove the ownership of a ticket for event redemptions. We also looked at some of the typical challenges with Smart Contract development such as circular references, inspecting inputs and outputs, and blockchain confirmations. We looked at how to implement a Redis DB schema to support the searching of blockchain swaps and creating APIs to support a dynamic blockchain-based React application. Finally, we finished with an end-to-end demo showcasing the features and benefits of a blockchain application. In the next chapter, we will look at testing techniques and how to write secure and scalable blockchain applications.

# [Points to Remember](#toc.xhtml#s288a)

*   Pure client-side blockchain applications are more true to the principles of blockchain and provide the best transparency and auditability.
*   The Redis DB contains the data models used by the application and is a copy of the relevant blockchain data.
*   Redis DB is an in-memory database that allows for extremely fast read operations.
*   Replicating blockchain data and metadata into an application database allows for an improved user experience and rich UI features such as multi-dimensional filters and searches.
*   Global state information in Next.js is passed into child React components using props such as the walletAPI JavaScript object.
*   UI changes can trigger real-time application and database changes while the application listens for blockchain block confirmations.
*   The CIP-68 metadata standard prefixes a hex label to the token name to distinguish between a user token and a reference token.
*   The swap datum contains an `askedAssetValue` and an `offeredAssetValue`.
*   The `askedAssetValue` specifies the asset being asked for and the price for each of the offered assets.
*   The `offeredAssetValue` specifies the asset being offered and the amount of the asset currently locked in the swap.
*   Time validity intervals are needed when trying to evaluate deadline conditions within a Smart Contract.
*   A thread token can be created using the transaction ID and index as contract parameters or as the token name.
*   Circular references occur when a smart contract depends on knowing in advance the address of another smart contract and vice versa.
*   A Blockfrost webhook calls the application when a blockchain event involving a beacon policy occurs.
*   Ticket tokens once minted and converted are unique Cardano NFT native tokens.

# [Multiple Choice Questions](#toc.xhtml#s289a)

1.  What are the advantages of a pure client-side blockchain application? 
    1.  Faster response times
    2.  Easier to audit and trust
    3.  Easier to build
    4.  Does not require a browser
2.  What are the advantages of replicating blockchain data in blockchain applications? 
    1.  Simplified architecture
    2.  Improve decentralization
    3.  Better user experience
    4.  Better vendor support
3.  What is the difference between CIP-25 and CIP-68? 
    1.  They are the same and both record transaction metadata
    2.  CIP-25 uses a datum to record transaction metadata
    3.  CIP-68 uses transaction metadata to record NFT metadata
    4.  CIP-68 uses a reference token with a datum to record NFT metadata
4.  Why are time validity intervals needed? 
    1.  The Cardano blockchain can only confirm if a range of time is valid for a particular transaction
    2.  The Cardano blockchain uses Oracles for time
    3.  The Cardano blockchain is non-deterministic
    4.  A Cardano Block is created approximately every 20 seconds
5.  When can a circular reference occur? 
    1.  A Plutus Script uses a reference script
    2.  Cardano is deterministic, so this is not a valid scenario
    3.  A Plutus script references another Plutus script and vice versa
    4.  Using a pointer address

# [Answers](#toc.xhtml#s290a)

1.  b
2.  c
3.  d
4.  a
5.  c

# [Questions](#toc.xhtml#s291a)

1.  What are some of the approaches to improve the user experience while maintaining audibility and transparency?
2.  How do CIP-0067 and CIP-0068 relate to each other?
3.  How do you calculate the correct minimum lovelace for a particular UTXO?
4.  How are inputs sorted, and why is it difficult to know in advance?
5.  Are there other approaches to resolving the circular reference problem?

# [Key Terms](#toc.xhtml#s292a)

*   **Blake2B:** Produces cryptographic hashes optimized for 64-bit architectures.
*   **Blockchain Confirmation:** The acceptance of a block to the Cardano blockchain network.
*   **DEX:** Decentralized Exchange.
*   **Functional Components:** A React UI component.
*   **Redis JSON full stack:** Optional components to the Redis DB to store JSON objects.
*   **Time Interval:** The start and end time in milliseconds.
*   **Trustless Model:** Ability to self-audit and does not require trusting an application.
*   `useEffect`**:** Triggers and actions based on a page mount or variable change.
*   **Witness Signature:** Contains both the message and the signature and proves the message was signed by the given public key.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c10.xhtml#ftn1a) [https://chakra-ui.com/](https://chakra-ui.com/)

[²](#c10.xhtml#ftn2a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/pages/WalletPopup.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/WalletPopup.tsx)

[³](#c10.xhtml#ftn3a) [https://github.com/cardano-foundation/cardano-connect-with-wallet](https://github.com/cardano-foundation/cardano-connect-with-wallet)

[⁴](#c10.xhtml#ftn4a) [https://swr.vercel.app/](https://swr.vercel.app/)

[⁵](#c10.xhtml#ftn5a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/components/SwapView.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapView.tsx)

[⁶](#c10.xhtml#ftn6a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/components/SwapView.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapView.tsx)

[⁷](#c10.xhtml#ftn7a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/pages/api/getFilterSwaps.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/api/getFilterSwaps.ts)

[⁸](#c10.xhtml#ftn8a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/pages/api/getFilterSwaps.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/api/getFilterSwaps.ts)

[⁹](#c10.xhtml#ftn9a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/components/SwapCard.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapCard.tsx)

[^(10)](#c10.xhtml#ftn10a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/components/SwapCard.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapCard.tsx)

[^(11)](#c10.xhtml#ftn11a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/pages/PrintTicketPopup.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/PrintTicketPopup.tsx)

[^(12)](#c10.xhtml#ftn12a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx)

[^(13)](#c10.xhtml#ftn13a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx)

[^(14)](#c10.xhtml#ftn14a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx)

[^(15)](#c10.xhtml#ftn15a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx)

[^(16)](#c10.xhtml#ftn16a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/ExecuteSwapPopup.tsx)

[^(17)](#c10.xhtml#ftn17a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/beacon.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/beacon.hl)

[^(18)](#c10.xhtml#ftn18a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/beacon.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/beacon.hl)

[^(19)](#c10.xhtml#ftn19a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/ticket.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/ticket.hl)

[^(20)](#c10.xhtml#ftn20a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/ticket.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/ticket.hl)

[^(21)](#c10.xhtml#ftn21a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/ticket.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/ticket.hl)

[^(22)](#c10.xhtml#ftn22a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/ticket.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/ticket.hl)

[^(23)](#c10.xhtml#ftn23a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/holding.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/holding.hl)

[^(24)](#c10.xhtml#ftn24a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/holding.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/holding.hl)

[^(25)](#c10.xhtml#ftn25a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/holding.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/holding.hl)

[^(26)](#c10.xhtml#ftn26a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/swap.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/swap.hl)

[^(27)](#c10.xhtml#ftn27a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/swap.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/swap.hl)

[^(28)](#c10.xhtml#ftn28a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/swap.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/swap.hl)

[^(29)](#c10.xhtml#ftn29a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/swap.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/swap.hl)

[^(30)](#c10.xhtml#ftn30a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/swap.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/swap.hl)

[^(31)](#c10.xhtml#ftn31a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/swap.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/swap.hl)

[^(32)](#c10.xhtml#ftn32a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/swap.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/swap.hl)

[^(33)](#c10.xhtml#ftn33a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_10/helios/ticket-app/public/contracts/swap.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/public/contracts/swap.hl)

[^(34)](#c10.xhtml#ftn34a) [https://www.npmjs.com/package/axios](https://www.npmjs.com/package/axios)

[^(35)](#c10.xhtml#ftn35a) [https://preprod.cexplorer.io/tx/aedd04b41e50585fb30236b3f83010fa82cef70f6f5569face03a084cf67f5bd](https://preprod.cexplorer.io/tx/aedd04b41e50585fb30236b3f83010fa82cef70f6f5569face03a084cf67f5bd)

# [CHAPTER 11](#toc.xhtml#c11)

# [Testing, Security, and Scaling](#toc.xhtml#c11)

# [Introduction](#toc.xhtml#s293a)

This chapter will show how to test Smart Contracts and include them in a popular testing framework such as Vitest. We will look at both the traditional testing and property-based testing approaches. Next, we will focus on security and review vulnerabilities that have been identified in real-world audits of Cardano applications. We will look in detail with code examples of how to make your Smart Contract code more robust and more resilient to such attacks. Finally, we will close the chapter with a discussion around scaling and some tools and techniques to improve dApp performance.

# [Structure](#toc.xhtml#s294a)

In this chapter, we will discuss the following topics:

*   Testing Frameworks 
    *   Test Strategy
    *   Test Cases
    *   Property-Based Testing
*   Secure Smart Contracts 
    *   Double Satisfaction
    *   Invalid Datums
    *   Token Leakage
    *   Audits
*   Scaling 
    *   Avoiding UTXO Contention
    *   Reference Scripts
    *   Advanced Smart Contract Designs
    *   Hydra
    *   Mithril
    *   Input Endorsers

# [Testing Frameworks](#toc.xhtml#s295a)

Testing Smart Contracts is always tricky because code is executed on distributed nodes across the Cardano network. Fortunately, most Smart Contract developer tooling includes a local emulator that allows us to catch many errors that would otherwise occur on the node. Typically this involves generating traces when the code is executed. Traces are, however, disabled by default and removed for production builds to optimize performance. That said, there may be situations where an error only occurs in production and in those cases, you may need to turn on traces to obtain additional debugging information. Traces are enabled for Helios when the `optimization` flag is set to `false`, and for Aiken by executing `aiken build` with the flags `--trace-level` or` --filter-traces.`

In this section, we will look at how to use Vitest,[¹](#c11.xhtml#ftn1) a popular testing framework, to test both the on-chain and off-chain code. Vitest is fast and has an interactive web page for inspecting passed and failed test cases. It is suitable for watching any changes in off-chain code and re-running the tests automatically. Vitest can also be part of an overall application testing framework that can test the entire application and not just the Smart Contracts. A disadvantage of Vitest is that it does not work well with Webpack because Vitest uses Vite, which does not use Webpack. There are other testing frameworks such as Jest[²](#c11.xhtml#ftn2) that do support Webpack, but Jest has its own challenges with setup and configuration.

We will use the vesting example in *[Chapter 6, Validators](#c06.xhtml),* to demonstrate how to use Vitest and test Smart Contracts. Before we can start, we first need to refactor the code to pull out the off-chain code from the front-end user interface (**UI**) code. This has two benefits:

*   Clean separation of the **UI** from off-chain transaction building.
*   Creates functions that can be used by the front-end and testing framework without any modifications.

The new folder structure to support this separation of **UI** and off-chain code is shown in *[Figure 11.1](#c11.xhtml#fig11_1)*.

![](OEBPS/images/Figure-11.1.jpg)

**Figure 11.1:** Refactored Vesting Project

All **UI** code is located in the `pages/index.tsx` and components directory. The **UI** code will contain all **UI** elements and application state information, such as what wallet is connected, wallet balance, and more. All off-chain code is located in `contracts/off-chain,` and the on-chain code is located in `contracts/validators` directories. The `contracts/config` folder defines the network we connect to (for example, Mainnet, Preprod, and so on) and the protocol parameters.

# [Testing Strategy](#toc.xhtml#s296a)

The testing strategy uses both traditional testing and property-based testing.[³](#c11.xhtml#ftn3) Traditional testing involves creating specific test cases to confirm that the Smart Contract correctly implements the requirements. This can include both positive and negative test cases. Property-based testing will attempt to exploit inputs into the Smart Contract and test conditions that are not expected.[⁴](#c11.xhtml#ftn4) We will use fast-check[⁵](#c11.xhtml#ftn5) for typescript that integrates well with Vitest. One consideration in doing this type of testing is that the off-chain transaction builder framework performs validity checks before **UPLC** evaluation. So, some of your failed tests will be the error handling of the off-chain transaction builder and not the Smart Contract. A potential solution is to have off-chain tooling to avoid any checks while still building and submitting a transaction. Making this type of change is outside of the scope of this book, but it may be considered as a future feature request to enable this option. With Aiken, you can modify the script context for traditional and property-based testing. However, the downside to this approach is that it does not integrate well into a testing framework such as Vitest and is time-consuming to set up.

The test cases for the vesting application are shown in *[Figure 11.2](#c11.xhtml#fig11_2).*

![](OEBPS/images/Figure-11.2.jpg)

**Figure 11.2:** Vesting Test Cases

The test cases that confirm the business logic and negative test cases are located in `cancel.test.ts,` `lock.test.ts`, and `unlock.test.ts`. The property-based tests are located in `lock.property.test.ts` and `unlock.property.test.ts`**.** The `vitest.config.*` files specify what tests are included in each test run. To execute a test run locally, issue the following commands:

`$ cd chapter_11/helios/vesting`

`$ npm install`

`$ npm run test:ui`

This will start up Vitest in watcher mode and display the test execution results, as shown in *[Figure 11.3](#c11.xhtml#fig11_3)*.

![](OEBPS/images/Figure-11.3.jpg)

**Figure 11.3:** Vitest Watcher

We can then drill down into any passed or failed scenarios to see each individual test execution, as shown in *[Figure 11.4](#c11.xhtml#fig11_4)*.

![](OEBPS/images/Figure-11.4.jpg)

**Figure 11.4:** Vitest Test Details

In [Figure 11.4](#c11.xhtml#fig11_4), we selected the unlock test scenario, which executed three test cases:

*   Lock 2 Ada test case
*   Unlock 2 Ada with an incorrect redeemer
*   Unlock 2 Ada with a correct redeemer

The console view on the right shows the executed transactions and the fee, CPU, and memory costs. Locking 2 Ada to a vesting script address does not invoke the Smart Contract, so no script execution units are used. Only the unlock (or cancel) transactions invoke the Smart Contract and will show `cpu` and `mem` values. We have also included trace information inside the Smart Contract, which is shown on the console view in *[Figure 11.4](#c11.xhtml#fig11_4)*. This allows us to easily find what in the validator script is failing.

# [Test Cases](#toc.xhtml#s297a)

The Helios and Lucid + Aiken test case source code and setup are almost identical. The Lucid provider, however, is slightly easier to switch between a real network and an emulator network. Therefore, we will show the Lucid + Aiken code in this section. In *[Figure 11.5](#c11.xhtml#fig11_5)*, the first step is to create an emulator with two test accounts, as shown on lines 41 and 42.

![](OEBPS/images/Figure-11.5.jpg)

**Figure 11.5:** unlock.test.ts[⁶](#c11.xhtml#ftn6)

On line 49, we specify the test scenario, which includes one or more test cases. The lucid provider created on line 54 will use the emulator instance we created on line 51. The first test case is to lock Ada on line 63 in *[Figure 11.6](#c11.xhtml#fig11_6)*. We test for pre-conditions to ensure that the amount locked at the Smart Contract and wallet balance beforehand is correct.

![](OEBPS/images/Figure-11.6.jpg)

**Figure 11.6:** Lock 2 Ada Test Case Part 1[⁷](#c11.xhtml#ftn7)

The next step is to call the `lock` off-chain function on line 81 in [Figure 11.7](#c11.xhtml#fig11_7). This is the same function that is called from the front-end **UI**, except that the lucid provider is connected to an emulator network. Once the `lock` function has been executed, we check if the return status is true on line 86 and then update the execution cost counters, which will be used in the test case reports. We must also manually create an emulator block on line 89. Finally, we check that the 2 Ada has been successfully locked at the Smart Contract address on line 99.

![](OEBPS/images/Figure-11.7.jpg)

**Figure 11.7:** Lock 2 Ada Test Case Part 2[⁸](#c11.xhtml#ftn8)

The unlock (or cancel) test case is very similar to the lock test case, except that we need to pass a message to the redeemer on line 168 in *[Figure 11.8](#c11.xhtml#fig11_8)*. We also include pre- and post-conditions for the user’s wallet to confirm that the user (or owner for cancel) received the locked 2 Ada, minus the transaction fees.

![](OEBPS/images/Figure-11.8.jpg)

**Figure 11.8:** Unlock 2 Ada Test Case[⁹](#c11.xhtml#ftn9)

# [Property-Based Testing](#toc.xhtml#s298a)

To perform property testing, we typically need to build the transaction using off-chain code to directly feed inputs into the Smart Contract redeemer, datum, or contract parameters. The unlock test case, as shown in *[Figure 11.9](#c11.xhtml#fig11_9),* involves sending invalid redeemer messages to the off-chain unlock function. To use the fast-check library, we must call `fc.assert` on line 163, which will wrap the `fc.asyncProperty.` It is inside the `asyncProperty` that fast-check will generate pseudo-random strings that we can pass into the unlock function as the message. We expect this to fail every time, so the property test passes when every execution attempt fails.

![](OEBPS/images/Figure-11.9.jpg)

**Figure 11.9:** Unlock Property Test Case[^(10)](#c11.xhtml#ftn10)

Both Helios and Aiken also have native property-based testing frameworks. Helios has a helper class called FuzzyTest[^(11)](#c11.xhtml#ftn11) that allows you to create randomized data, which can be fed into your Plutus script. Aiken has excellent support for unit- and property-based testing, including a report coverage report. The following is an example of an Aiken unit test and a fuzzy test:[^(12)](#c11.xhtml#ftn12)

`use aiken/fuzz`

`fn answer_of_life(n: Int) -> Bool {`

`n == 42`

`}`

`test question_of_life() {`

` answer_of_life(42) == True`

`}`

`test prop_bool_distribution(predicate via fuzz.bool()) {`

`fuzz.label(`

`if predicate {`

`@"True"`

`} else {`

`@"False"`

`},`

`)`

`True`

`}`

When the `aiken check` command is run, the following report will be generated:

`┍━ aiken_test ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━`

`│ PASS [mem: 1802, cpu: 680589] question_of_life`

`│ PASS [after 100 tests] prop_bool_distribution`

`│ · with coverage`

`│ | False  53.0%`

`│ | True   47.0%`

`┕ with --seed=4272986809 → 2 tests | 2 passed | 0 failed`

`Summary 101 checks, 0 errors, 0 warnings`

Aiken property tests allow you to specify a predicate to evaluate, which is included in the report. In this example, we can verify that `True` and `False` values are generated and have a good distribution.

# [Secure Smart Contracts](#toc.xhtml#s299a)

The most important aspect of Smart Contract development is security. Smart contracts can be responsible for the value transfer of millions of dollars or for validating the results of an election. Therefore, special consideration is required in designing and writing Smart Contracts in the most secure way possible. This can only be done if you are aware of what *not to do* and examples and best practices on what *to do*. This section will review some of the common pitfalls that have been identified through audits on Cardano.

# [Double Satisfaction](#toc.xhtml#s300a)

One of the most frequent vulnerabilities in Cardano Smart Contracts is the double satisfaction vulnerability, as shown in *[Figure 11.10](#c11.xhtml#fig11_10)*. In this simple NFT swap implementation, the validator script looks at the datum values in each swap to validate the business logic. The assumption is that only one NFT swap is executed at one time. However, there is nothing preventing a transaction from having two swaps included in the same transaction. When this occurs, the swap validator validates each UTXO separately and both hold true so the amount of Ada that goes to Alice is double counted. She should receive 250 Ada for both NFTs but only receives 150 Ada. This is because the higher amount of 150 Ada satisfies both the NFT swap conditions, hence the double satisfaction vulnerability.

![](OEBPS/images/Figure-11.10.jpg)

**Figure 11.10:** Double Satisfaction Validator

There are several approaches we can take to address this exploit:

1.  Create a unique address for each swap script corresponding to the NFT being sold.
2.  Match inputs to outputs so there is a one-to-one correspondence between them.
3.  Verify and restrict the outputs that if Alice gets 150 Ada, Bob only gets one NFT B.
4.  Use a validity token such that if it is present, the transaction can proceed because validation has occurred elsewhere.
5.  We should also restrict other transaction types such as Minting and Withdraws unless there is specific business logic.

*[Figure 11.11](#c11.xhtml#fig11_11)* shows a code example written in Helios for this vulnerability. On line 15, the check to see if the amount sent to the seller is at or above the price is performed.

![](OEBPS/images/Figure-11.11.jpg)

**Figure 11.11:** Double Satisfaction Code Exploit[^(13)](#c11.xhtml#ftn13)

To fix this code and avoid the double satisfaction vulnerability, we add a few additional checks, as shown in *[Figure 11.12](#c11.xhtml#fig11_12)*. First, we require the `PKH` of the buyer in the redeemer on line 8. Second, we define contract parameters to hard code the `NFT` minting policy hash and token name for the validator script on lines 10 and 11. We also create a utility function on line 15 to recursively go through the given outputs and return the total value. Inside the main function, we check that the `NFT` value is sent to the buyer’s address using the `PKH` provided by the redeemer. Then, we calculate the total value of all of the outputs, subtract the `NFT` going to the buyer, and verify the remaining value. If the remaining value contains no other tokens, we know that the transaction only had one `NFT` in the outputs and that it went to the buyer.

![](OEBPS/images/Figure-11.12.jpg)

**Figure 11.12:** Double Satisfaction Fix[^(14)](#c11.xhtml#ftn14)

# [Invalid Datums](#toc.xhtml#s301a)

We saw in the design patterns in *[Chapter 9, Ticket Application Design](#c09.xhtml)*, that a state machine is frequently used in UTXO architecture. It involves maintaining the state in a datum and ensuring the correct datum state is updated as part of a transaction. It is always important to remember that anyone can create a UTXO and lock it at a script address with a malicious datum. Therefore, it is extremely important that a Plutus script always checks whether the inbound and outbound datums are valid. The example we will look at is a multi-sig contract for controlling when the funds can be spent by a beneficiary. It is a two-step process to exploit the vulnerability. The first step is for each required signature to sign a transaction and update the datum with their `PKH`, as shown in *[Figure 11.13](#c11.xhtml#fig11_13).*

![](OEBPS/images/Figure-11.13.jpg)

**Figure 11.13:** Invalid Datum Sign Tx

Although there is a check that the `PKH` of the signer is included in the outbound Datun, there is no check that the other Datum fields are not modified. This leads to the exploit where Carol changes the required number of signers from 2 to 1. Now, Bob the beneficiary can release the funds and not have to wait for the second signature, as shown in *[Figure 11.14](#c11.xhtml#fig11_14)*.

![](OEBPS/images/Figure-11.14.jpg)

**Figure 11.14:** Invalid Datum Withdraw Tx

Let’s examine the code that contains the vulnerability, as shown in *[Figure 11.15](#c11.xhtml#fig11_15).* We define the `Datum` on line 3 and the `Redeemer` on line 9 accordingly. The two signatures allowed to sign and update the datum are hard coded as contract parameters.

![](OEBPS/images/Figure-11.15.jpg)

**Figure 11.15:** Invalid Datum Exploit Datum[^(15)](#c11.xhtml#ftn15)

The business logic is contained in the main function in *[Figure 11.16](#c11.xhtml#fig11_16)*. In particular, line 31 checks that the datum created for the output contains the signers `PKH` in the signatures array.

![](OEBPS/images/Figure-11.16.jpg)

**Figure 11.16:** Invalid Datum Exploit[^(16)](#c11.xhtml#ftn16)

As we can see, the exploit allows the signer (Carol in this case) to change the required number of signatures so that Alice’s signature is no longer required. Fixing this vulnerability requires checking *all* datum values and not just the one that is getting updated. In *[Figure 11.17](#c11.xhtml#fig11_17),* we create what the output Datum is supposed to look like on line 24. We only look for an output UTXO that matches the new datum on line 30. We perform the same check that the signing `PKH` is included in the updated signatures array on line 32 but tighten the restriction to make sure there are no duplicate signatures on line 38. Finally, we ensure that the signatures list has increased by 1 on line 39.

![](OEBPS/images/Figure-11.17.jpg)

**Figure 11.17:** Invalid Datum Fix[^(17)](#c11.xhtml#ftn17)

# [Token Leakage](#toc.xhtml#s302a)

Another common vulnerability we will delve into is token leakage. This can seriously impact state machines or liquidity pools that rely on a unique token being minted. Smart Contracts may incorrectly validate a transaction if more than one unique token is minted. A high-profile Cardano example was with MinSwap,[^(18)](#c11.xhtml#ftn18) where this type of vulnerability was identified. Fortunately, no funds were lost, thanks to WingRiders[^(19)](#c11.xhtml#ftn19) and their quick action. An excellent write-up was provided by Tweag, who performed an audit on the code.[^(20)](#c11.xhtml#ftn20)

There are variations of this type of vulnerability, and we will look at one particular type in [Figure 11.18](#c11.xhtml#fig11_18). It can be difficult to spot these types of vulnerabilities in multi-contract, complex applications.

![](OEBPS/images/Figure-11.18.jpg)

**Figure 11.18:** Token Leakage

The code in *[Figure 11.19](#c11.xhtml#fig11_19)* contains an exploit allowing an attacker to mint their thread token. The `Mint Redeemer` correctly tests that the Value of what is being minted is the thread token and is a quantity of one. So, the vulnerability actually lies in the Burn redeemer used for burning a thread token. The Burn allows any token to be burned as long as it has the minting policy on line 29.

![](OEBPS/images/Figure-11.19.jpg)

**Figure 11.19:** Thread Token Exploit[^(21)](#c11.xhtml#ftn21)

The issue is that we are not checking the token quantity that is actually being burned; only the minted value contains a particular minting policy. To fix this issue, explicitly check the quantity that is being minted and confirm that it is negative. The code for the fix is shown in *[Figure 11.20](#c11.xhtml#fig11_20)*, lines 29—31. It looks at the value that is being minted and then iterates through a `map` to check that every entry has a value of negative one.

![](OEBPS/images/Figure-11.20.jpg)

**Figure 11.20:** Thread Token Fix[^(22)](#c11.xhtml#ftn22)

# [Audits](#toc.xhtml#s303a)

It is very important to have an extra pair of eyes to review your code to help spot and identify potential vulnerabilities. This is typically the role of an auditor, and there are several auditing companies that can help with Cardano Smart Contracts.[^(23)](#c11.xhtml#ftn23) It is also highly recommend to explore the excellent repository by Vacuum Labs, which provides more examples of vulnerabilities from real-world audits using Aiken.[^(24)](#c11.xhtml#ftn24) Finally, you should also review completed audits to understand the types of common vulnerabilities known to exist fully. Although the Smart Contract code language may be different, such as Haskell or Plutarch, the concepts are the same. The following is a list of published audits for further reading:

*   Vacuum Labs[^(25)](#c11.xhtml#ftn25)
*   Tweag[^(26)](#c11.xhtml#ftn26)
*   Mlabs[^(27)](#c11.xhtml#ftn27)

# [Scaling](#toc.xhtml#s304a)

There are several ways to scale smart contracts on the Cardano Blockchain, which we will review in this section. When improving scalability, one must typically consider the trade-offs between decentralization and security. An application is always constrained by the underlying blockchain architecture and that is why choosing what blockchain to use is critical. As we know, Cardano uses the UTXO architecture, which in turn uses local state and not global state. We will leverage this property to increase the scalability of our application.

# [Avoiding UTXO Contention](#toc.xhtml#s305a)

For the ticket application in *[Chapter 10, Ticket Application Implementation](#c10.xhtml)*, we can easily handle many events running simultaneously without any UTXO contention or bottlenecks. However, if there was an extremely popular event, there could be UTXO contention if all of the event tickets were located in one swap UTXO. The way to mitigate this is by creating multiple swaps with batches of tickets that can be accessed in parallel. Much like having multiple ticket windows at a stadium, the off-chain code would need to be modified to route or surface swaps not currently waiting for block confirmations. By distributing event tickets across multiple swaps without any changes to the Smart Contracts, the application scaling limits would directly depend on the underlying blockchain block size and frequency.

# [Reference Scripts](#toc.xhtml#s306a)

All of the examples we have looked at so far require spending the UTXO inputs as part of a transaction. With the Vasil hard fork in September 2022, Reference Inputs[^(28)](#c11.xhtml#ftn28) were introduced, allowing read-only UTXOs to be included in a transaction and not have to be spent. This is particularly useful if you only need to read a datum value and not update it. It dramatically improves concurrency because multiple scripts can simultaneously include and use a reference input. The final benefit paved the way for Reference Scripts,[^(29)](#c11.xhtml#ftn29) which allows a Plutus script to be included in a UTXO on-chain. By using reference scripts, a transaction does not need to include the Plutus CBOR payload, which will reduce the overall transaction size. As long as the Plutus script is included as a UTXO Reference Input, the transaction will be able to evaluate and execute the Plutus script that is stored on-chain.

Using the vesting example, we will show how to submit a reference script with Helios in *[Figure 11.21](#c11.xhtml#fig11_21).* The reference script is put on-chain as a one-time activity inside the l`ock` function. On line 89, we first check to see if there already exists a reference script, and if not, then build the output that contains the compiled Plutus script (`compiledProgram`) on line 91. We must also evaluate the cost of storing the Plutus script on-chain on line 99. The fee is included in the overall transaction costs and is calculated using the `coinsPerUTxOWord` from the network parameters.

![](OEBPS/images/Figure-11.21.jpg)

**Figure 11.21:** Lock With Reference Script[^(30)](#c11.xhtml#ftn30)

Once the reference script has been submitted on-chain, we create a reference input in *[Figure 11.22](#c11.xhtml#fig11_22)*. On line 83, inside the UnLock function, we query the blockchain for the reference script UTXO. Then, on line 88, we add it to the transaction using `addRefInput`, which includes the reference script UTXO and a copy of the original **UPLC** script (`uplcProgram)`. The included script will not be submitted to the network and is only used for local evaluation to ensure the transaction is valid before submitting it to the network.

![](OEBPS/images/Figure-11.22.jpg)

**Figure 11.22:** UnLock With Reference Script[^(31)](#c11.xhtml#ftn31)

# [Advanced Smart Contract Designs](#toc.xhtml#s307a)

When Smart Contracts were first launched on Cardano, the inefficient Plutus scripts made creating and deploying real-world decentralized applications very difficult. As a result, there were a number of clever ways to reduce the Plutus script size and computation overhead. Some of these advanced techniques are still applicable today, but they come at a cost of added complexity and reduced readability. In situations that require additional performance gains beyond applying the best practices in this chapter, please look at the excellent examples provided by Anastasia Labs[^(32)](#c11.xhtml#ftn32) for further study.

# [Hydra](#toc.xhtml#s308a)

There are two general approaches to scaling a layer 1 blockchain: rollups and layer 2 side chains. Rollups involve processing transactions off-chain, which can be done faster and more efficiently and then applied as one transaction at a later point in time. Layer 2 side chains involve creating a blockchain network similar to layer 1, with faster block creation and settlement times but less decentralization and security. Hydra is a layer 2 scaling solution that creates isomorphic state channels.[^(33)](#c11.xhtml#ftn33) This means that it has similar ledger rules and a Plutus evaluator that can run most Smart Contracts without any modifications. Hydra is a suite of protocols with the Hydra Head protocol involving the creation (and destruction) of a layer 2 network and the transferring of value back and forth to layer 1.[^(34)](#c11.xhtml#ftn34)

Hydra’s design traces back to the original concepts of the settlement layer and the computation layer for Cardano. There will be situations that require a dedicated layer for computation at the expense of decentralization and security. For example, a Hydra Head could be created for the ticket application discussed in *[Chapters 9](#c09.xhtml)* and *[10](#c10.xhtml)* when there is a planned high-demand ticket sale, as shown in *Figure* 11.23. The Hydra head would be managed by the application with a potential use case as follows:

1.  Users who want to participate in a high-profile ticket sale would lock Ada into a Hydra Smart Contract and obtain vouchers (tokens inside the Hydra Head) representing the amount of Ada they have locked.
2.  The ticket tokens would be minted in advance on the Cardano layer 1 network and locked into a Hydra Head Smart Contract, so that they are available for sale inside the Hydra Head.
3.  Users would interact with the ticket swaps running in the Hydra Head using a custodial wallet managed by the Ticket Application.
4.  Once the ticket sale is over, the tickets purchased in the Hydra Head are transferred back to the Cardano layer 1 blockchain to the new owners.
5.  Any unspent vouchers are converted to Ada on layer 1 and returned to the original owner.

![](OEBPS/images/Figure-11.23.jpg)

**Figure 11.23:** Hydra Head

The disadvantage of this type of architecture is that the user needs to trust the application owner while the Hydra head is being used. Hydra is currently available for Mainnet but is still early in adoption and maturity. For more information on Hydra, please check out their documentation and discord channel.[^(35)](#c11.xhtml#ftn35)

# [Mithril](#toc.xhtml#s309a)

Mithril is an important development for blockchain scalability, wallets, and Stake Pool Operators (SPOs). It is a solution that allows a client to obtain the current state of the blockchain without having to download and replay all of the transactions from the Genesis block.[^(36)](#c11.xhtml#ftn36) The core innovation behind Mithril is using stake-based threshold multisignatures[^(37)](#c11.xhtml#ftn37) (**STM**) to create a certificate by an honest majority of stakeholders that a Cardano snapshot is valid. Using this certificate, a light client or SPO can verify a snapshot with security properties that are similar to a fully synchronized node.[^(38)](#c11.xhtml#ftn38)

# [Input Endorsers](#toc.xhtml#s310a)

Input Endorsers, as documented in Ouroboros Leios, are an ambitious and profound design extension of the Cardano Ouroboros protocol.[^(39)](#c11.xhtml#ftn39) In particular, it focuses on maximizing the utilization of the network by parallelizing block production and transaction selection.[^(40)](#c11.xhtml#ftn40) This would significantly increase block production throughput while minimizing additional resource demands on the network. *[Figure 11.24](#c11.xhtml#fig11_24)* illustrates the current underutilization of the Cardano network and areas for optimization.

![](OEBPS/images/Figure-11.24.jpg)

**Figure 11.24:** Network Utilization[^(41)](#c11.xhtml#ftn41)

Ouroboros Leios introduces three new block types:

*   Input Blocks
*   Endorsement Blocks
*   Ranking Blocks

At a high level, Input Blocks contain the list of transactions taken from the mempool of a block-producing node. This can be done asynchronously during the idle periods, as shown in *[Figure 11.24](#c11.xhtml#fig11_24).* Endorsement Blocks then generate certificates of valid Input Blocks. Ranking Blocks then use Endorsement certificates and form a chain of Endorsement Blocks. The ledger state is then based on the order of the Ranking Blocks. It should be noted that Input Endorsers do not change the consensus mechanism of determining the longest chain.[^(42)](#c11.xhtml#ftn42) For a more detailed and thorough description of Input Endorsers, please refer to the Ouroboros Leios research paper.[^(43)](#c11.xhtml#ftn43)

# [Conclusion](#toc.xhtml#s311a)

We should now have a good understanding of how to test Smart Contracts and include them as part of an overall testing framework. Traditional and property-based testing were examined using tools like Vitest and fast-check. Next, we reviewed code examples from real-world audits and how to avoid common Smart Contract vulnerabilities. Finally, we discussed scaling and some tools and techniques such as avoiding UTXO contention, Reference Scripts, Hydra, and Mithril. We also reviewed layer 1 scalability improvements using Input Endorsers that will significantly increase block production while maintaining security and minimizing additional network resource demands. In the next chapter, we will review troubleshooting tools and techniques that can be used when writing Cardano Smart Contracts.

# [Points to Remember](#toc.xhtml#s312a)

*   Testing Smart Contracts is difficult because code is executed on distributed nodes across the network.
*   Application design best practices separate UI code from off-chain and back-end code.
*   A test strategy can include both traditional testing and property-based testing.
*   Security is the most important aspect of Smart Contract development.
*   A Double Satisfaction vulnerability involves spending two or more inputs while only validating (satisfying) one input condition.
*   An Invalid Datum vulnerability occurs when not all datum fields are checked and verified.
*   Token Leakage involves minting more than one unique Thread or Validity token.
*   Audits are a key part of production readiness and should be used to review Smart Contract source code.
*   Application scaling techniques include avoiding UTXO contention and making use of Reference Scripts.
*   Hydra is a layer 2 scaling solution but impacts security and decentralization properties.
*   Input Endorsers is a Cardano layer 1 scaling solution to significantly increase block production throughput.

# [Multiple Choice Questions](#toc.xhtml#s313a)

1.  What techniques would you use to debug a Smart Contract in production? 
    1.  Use VS Code debugger
    2.  Open a support ticket
    3.  Enable tracing in production
    4.  Restart the Cardano node
2.  Property testing test is used for? 
    1.  Testing unexpected inputs
    2.  Testing expected inputs
    3.  Regression testing
    4.  Non-functional testing
3.  Where can Token leakage occur? 
    1.  Minting script only
    2.  Validator or Minting scripts
    3.  Validator scripts only
    4.  None of the above
4.  Reference Scripts are only possible because of \_\_\_\_\_\_\_. 
    1.  Native Assets
    2.  Determinism
    3.  Shelly Hard Fork
    4.  Reference Inputs
5.  What statement about Hydra is correct? 
    1.  Only a limited number of Hydra heads can be opened
    2.  An unlimited number of Hydra heads can be opened
    3.  Joining a Hydra head is permissionless
    4.  Minted tokens on a Hydra network will be created in the base layer

# [Answers](#toc.xhtml#s314a)

1.  c
2.  a
3.  b
4.  d
5.  a

# [Questions](#toc.xhtml#s315a)

1.  What are other approaches to testing Smart Contracts?
2.  Can you list three other documented vulnerabilities and describe what was involved in the exploit?
3.  What are some other use cases for Hydra?
4.  What else can Mithril be used for?
5.  What are some of the potential risks of Input Endorsers?

# [Key Terms](#toc.xhtml#s316a)

*   **UPLC:** Untype Plutus Core, the compiled language generated from Helios or Aiken.
*   **Map**: A dictionary data type that contains a list of key and value pairs.
*   **PKH:** Public Key Hash
*   **NFT:** Non-Fungible Token
*   **SPO:** Stake Pool Operator
*   **STM:** Stake-based Threshold Multi-signatures
*   **UI:** User Interface
*   **UTXO:** Unspent Transaction Output

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c11.xhtml#ftn1a) [https://vitest.dev/](https://vitest.dev/)

[²](#c11.xhtml#ftn2a) [https://jestjs.io/](https://jestjs.io/)

[³](#c11.xhtml#ftn3a) Gabriel Lebec, “The Magic of Generative Testing: Fast-Check in JavaScript”

[⁴](#c11.xhtml#ftn4a) John Hughes, “Testing smart contracts with QuickCheck by John Hughes”

[⁵](#c11.xhtml#ftn5a) [https://fast-check.dev/](https://fast-check.dev/)

[⁶](#c11.xhtml#ftn6a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/aiken/vesting/contracts/tests/unlock.test.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)

[⁷](#c11.xhtml#ftn7a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/aiken/vesting/contracts/tests/unlock.test.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)

[⁸](#c11.xhtml#ftn8a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/aiken/vesting/contracts/tests/unlock.test.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)

[⁹](#c11.xhtml#ftn9a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/aiken/vesting/contracts/tests/unlock.test.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.test.ts)

[^(10)](#c11.xhtml#ftn10a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/aiken/vesting/contracts/tests/unlock.property.test.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/aiken/vesting/contracts/tests/unlock.property.test.ts)

[^(11)](#c11.xhtml#ftn11a) [https://www.hyperion-bt.org/helios-book/api/reference/classes/FuzzyTest.html](https://www.hyperion-bt.org/helios-book/api/reference/classes/FuzzyTest.html)

[^(12)](#c11.xhtml#ftn12a) [https://aiken-lang.org/language-tour/tests](https://aiken-lang.org/language-tour/tests)

[^(13)](#c11.xhtml#ftn13a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/helios/double-satisfaction-exploit/buy.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/double-satisfaction-exploit/buy.hl)

[^(14)](#c11.xhtml#ftn14a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/helios/double-satisfaction-fix/buy.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/double-satisfaction-fix/buy.hl)

[^(15)](#c11.xhtml#ftn15a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/helios/invalid-datum-exploit/multisig.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/invalid-datum-exploit/multisig.hl)

[^(16)](#c11.xhtml#ftn16a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/helios/invalid-datum-exploit/multisig.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/invalid-datum-exploit/multisig.hl)

[^(17)](#c11.xhtml#ftn17a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/helios/invalid-datum-fix/multisig.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/invalid-datum-fix/multisig.hl)

[^(18)](#c11.xhtml#ftn18a) [https://minswap.org/](https://minswap.org/)

[^(19)](#c11.xhtml#ftn19a) [https://www.wingriders.com/](https://www.wingriders.com/)

[^(20)](#c11.xhtml#ftn20a) [https://www.tweag.io/blog/2022-03-25-minswap-lp-vulnerability/](https://www.tweag.io/blog/2022-03-25-minswap-lp-vulnerability/)

[^(21)](#c11.xhtml#ftn21a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/helios/token-leakage-exploit/threadToken.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/token-leakage-exploit/threadToken.hl)

[^(22)](#c11.xhtml#ftn22a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/helios/token-leakage-fix/threadToken.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/token-leakage-fix/threadToken.hl)

[^(23)](#c11.xhtml#ftn23a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0052](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0052)

[^(24)](#c11.xhtml#ftn24a) [https://github.com/vacuumlabs/cardano-ctf/tree/main](https://github.com/vacuumlabs/cardano-ctf/tree/main)

[^(25)](#c11.xhtml#ftn25a) [https://github.com/vacuumlabs/audits](https://github.com/vacuumlabs/audits)

[^(26)](#c11.xhtml#ftn26a) [https://github.com/tweag/tweag-audit-reports](https://github.com/tweag/tweag-audit-reports)

[^(27)](#c11.xhtml#ftn27a) [https://library.mlabs.city/common-plutus-security-vulnerabilities](https://library.mlabs.city/common-plutus-security-vulnerabilities)

[^(28)](#c11.xhtml#ftn28a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0031](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0031)

[^(29)](#c11.xhtml#ftn29a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0033](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0033)

[^(30)](#c11.xhtml#ftn30a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/helios/vesting-reference-script/contracts/off-chain/lock.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/vesting-reference-script/contracts/off-chain/lock.ts)

[^(31)](#c11.xhtml#ftn31a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter\_11/helios/vesting-reference-script/contracts/off-chain/unlock.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_11/helios/vesting-reference-script/contracts/off-chain/unlock.ts)

[^(32)](#c11.xhtml#ftn32a) [https://github.com/Anastasia-Labs/design-patterns](https://github.com/Anastasia-Labs/design-patterns)

[^(33)](#c11.xhtml#ftn33a) [https://iohk.io/en/blog/posts/2022/08/05/layer-1-layer-2-all-you-need-to-know/](https://iohk.io/en/blog/posts/2022/08/05/layer-1-layer-2-all-you-need-to-know/)

[^(34)](#c11.xhtml#ftn34a) [https://iohk.io/en/blog/posts/2021/09/17/hydra-cardano-s-solution-for-ultimate-scalability/](https://iohk.io/en/blog/posts/2021/09/17/hydra-cardano-s-solution-for-ultimate-scalability/)

[^(35)](#c11.xhtml#ftn35a) [https://hydra.family/head-protocol/](https://hydra.family/head-protocol/)

[^(36)](#c11.xhtml#ftn36a) Jean-Philippe Raynaud, “Light, fast, efficient, and secure - Mithril”

[^(37)](#c11.xhtml#ftn37a) Pyrros Chaidos et al., “Mithril: Stake-based Threshold Multisignatures”, 1

[^(38)](#c11.xhtml#ftn38a) Olga Hryniuk, “How Mithril facilitates strong security settings”

[^(39)](#c11.xhtml#ftn39a) Duncan Coutts, et al., “Ouroboros Leios: design goals and concepts”, 1

[^(40)](#c11.xhtml#ftn40a) Duncan Coutts, et al., “Ouroboros Leios: design goals and concepts”, 7

[^(41)](#c11.xhtml#ftn41a) Duncan Coutts, et al., “Ouroboros Leios: design goals and concepts”, 4

[^(42)](#c11.xhtml#ftn42a) Cardaniansio, “Understanding Input Endorsers”

[^(43)](#c11.xhtml#ftn43a) Duncan Coutts, et al., “Ouroboros Leios: design goals and concepts”,

# [CHAPTER 12](#toc.xhtml#c12)

# [Troubleshooting](#toc.xhtml#c12)

# [Introduction](#toc.xhtml#s317a)

This chapter aims to walk through debugging tools and techniques for Helios and Lucid + Aiken. We will look at generating CBOR for a transaction and comparing data types against formal specifications. We will address reducing the computational overhead of a Plutus script that exceeds the execution budget. We will also examine compiler errors and how transaction builders provide robust error-handling support. Furthermore, Cardano Node errors will be discussed, along with the best strategies for understanding them if they occur. Finally, the chapter will conclude with a brief review of browser-based wallet errors.

# [Structure](#toc.xhtml#s318a)

In this chapter, we will discuss the following topics:

*   Trace and Print 
    *   Helios
    *   Aiken
*   CBOR Analysis 
    *   Helios
    *   Lucid + Aiken
*   Execution Budget Errors
*   Compiler Errors
*   Transaction Builder Errors
*   Cardano Node Errors
*   Wallet Errors

# [Trace and Print](#toc.xhtml#s319a)

When your smart contract is not working correctly, the best way (at the time of writing) to troubleshoot is to use print and traces inside your smart contract. This allows you to write the console log and see what is getting executed in your Smart Contract. We will focus on the Helios and Lucid + Aiken Smart Contract development toolkits used in this book.

# [Helios](#toc.xhtml#s320a)

For Helios, as an example, you can print out the value being minted with a particular transaction using the `print` and `show` functions. The Helios `optimize` flag must be set to false to enable tracing.

`func main(redeemer: Redeemer, ctx: ScriptContext) -> Bool {`

`tx: Tx = ctx.tx;`

`print("tx.minted: " + tx.minted.show());`

This will generate the following output when running the Plutus script.

`INFO (ticket:13:10) tx.minted: lovelace: 0`

`INFO (ticket:13:10) 0af9021a0…d93cba53ecf15.54687265616420546f6b656e: 2`

The line number of the Helios script is also shown in the `INFO` brackets. The `trace()` function can also be used to emit an output to test a boolean condition.

`value_minted.contains_policy(mph).trace("TTP3: ")`

This will generate an output of the evaluation when the Plutus script is executed.

`INFO (ticket:33:52) TTP3: true`

If the Smart Contract fails and returns a false boolean value, a stack trace is generated in *[Figure 12.1](#c12.xhtml#fig12_1)*, which allows you to see where and why it failed.

![](OEBPS/images/Figure-12.1.jpg)

**Figure 12.1:** Helios Trace()

# [Aiken](#toc.xhtml#s321a)

When you build an Aiken script you can specify what type of tracing you want to include, as illustrated in *[Figure 12.2](#c12.xhtml#fig12_2).*

![](OEBPS/images/Figure-12.2.jpg)

**Figure 12.2:** Aiken Build Trace Options

To emit `print` statements, use the `trace` function.

`trace "redeemer message: "`

`trace string.from_bytearray(msg)`

To emit a trace when a condition is evaluated to be false, you use the `?` operator.

`some_expression_a? && some_expression_b?`

In this example, it can help isolate what expression is failing because if either condition evaluates to false, the entire script will fail.

An example of emitting `trace` information is shown in *[Figure 12.3](#c12.xhtml#fig12_3).*

![](OEBPS/images/Figure-12.3.jpg)

**Figure 12.3:** Aiken Traces

The validator script is compiled using the `-t` flag.

`$ aiken build -t verbose`

The following output is generated when the script is executed when the validator fails, as shown in *[Figure 12.4](#c12.xhtml#fig12_4)*.

![](OEBPS/images/Figure-12.4.jpg)

**Figure 12.4:** Aiken Traces

# [CBOR Analysis](#toc.xhtml#s322a)

As we learned in previous chapters, a Plutus script is compiled into **UPLC** and converted into the **CBOR** format. We typically inspect **CBOR** using the hexadecimal representation of the underlying bytes. This binary format is stored and executed on-chain, so looking at this when troubleshooting is helpful.

# [Helios](#toc.xhtml#s323a)

Helios has excellent support for **CBOR** serialization and deserialization and you can easily view any part of the transaction in **CBOR** format.

`await tx.finalize(networkParams, alice.address, utxos);`

`console.log("tx final: ", tx.toCborHex());`

You can also easily deserialize a transaction or any transaction component back into a Helios object using `fromCbor().`

`const txCbor = tx.toCborHex();`

`const newTx = Tx.fromCbor(txCbor);`

`console.log("tx from cbor: ", newTx.dump());`

# [Lucid + Aiken](#toc.xhtml#s324a)

Aiken provides the `cbor.diagnostic()` function to help generate **CBOR** that can be used for troubleshooting. To print out the **CBOR** representation of the `msg` in *[Figure 12.3](#c12.xhtml#fig12_3)*, we can use:

`trace cbor.diagnostic(msg)`

This will generate the **CBOR** representation of a bytearray:

`h'596F7520526F636B21'`

We can also print out the **CBOR** representation of the entire transaction easily using Lucid.

`const signedTx = await tx.sign().complete();`

`console.log("signedTx: ", signedTx.toString());`

The **CBOR** output in hexadecimal can then be used in [https://cbor.nemo157.com/](https://cbor.nemo157.com/) to inspect and analyze the **CBOR** elements. Once you have the **CBOR** elements, you can compare them against the formal **CDDL** specifications[¹](#c12.xhtml#ftn1) to see if there are any discrepancies. As we can recall from *[Chapter 5, Transactions](#c05.xhtml)*, the **CDDL** is the Concise Data Definition Language used to describe the structure of a transaction.

# [Execution Budget Errors](#toc.xhtml#s325a)

If you have not encountered execution budget errors, you will eventually.

`CekError An error has occurred: User error:\\\\nThe machine terminated part way through evaluation due to overspending the budget.\\\\nThe budget when the machine terminated was:\\\\n({ cpu: -447572\\\\n| mem: 5302\\\\n}`

Execution budget errors are typically detected during transaction construction, so the off-chain transaction builder framework generates a more user-friendly error. The preceding error *can also* occur when the off-chain framework has not supplied the correct budget values in the redeemer for each Plutus script being executed. This will result in an execution budget mismatch, which the Cardano node rejects.

There is another scenario where the order of the inputs is different between what is executed locally and what is executed on the Node. The order of the inputs will be re-ordered to follow the canonical **CBOR** order format.[²](#c12.xhtml#ftn2) However, the ordering of the *outputs* will remain the same as when they were created during off-chain transaction construction. This is why it is preferred to inspect outputs rather than inputs. For more information on this subject, please refer to CIP-0021[³](#c12.xhtml#ftn3), which documents the canonical ordering and how it relates to hardware wallets and tokens.

In the previous chapter, we showed how to include CPU and memory units in your testing so you can keep track of a transaction’s execution budget. Remember that a Plutus script is resource-constrained to minimize the hardware requirements for the node operators. This, in turn, promotes decentralization since anyone can run a node without requiring specialized hardware or infrastructure.

When you trigger a CPU or memory execution limit error using Helios, the error message will be displayed, as shown in *[Figure 12.5](#c12.xhtml#fig12_5)*. It indicates what was exceeded and the current values of the protocol parameters during the evaluation. This is helpful so you can isolate exactly what contributes to the `cpu` and `mem` units and tune accordingly.

![](OEBPS/images/Figure-12.5.jpg)

**Figure 12.5:** Helios Execution Units Error

Protocol parameters can be changed by network updates, so it is best to query the network to get the current value. This can be done using a tool like [https://cexplorer.io/params](https://cexplorer.io/params) or `cardano-cli`, as shown in *[Figure 12.6](#c12.xhtml#fig12_6)*.

![](OEBPS/images/Figure-12.6.jpg)

**Figure 12.6:** Network Protocol Parameters

In general, the following guidelines will help you optimize your Plutus script:

*   Compile Helios scripts with `optimize=true` and `aiken build` without any traces or logging levels.
*   Avoid unnecessary data conversions and work directly with the serialized data structures.
*   Avoid iterating through the list of UTXO inputs if possible and focus on specific UTXO outputs.
*   If you encounter script size or CPU and memory execution limit errors, split out validator logic across multiple scripts using separate transactions.
*   Use reference scripts to reduce the transaction size.

# [Compiler Errors](#toc.xhtml#s326a)

Both Helios and Aiken handle errors well during script compilation. A typical error generated using Helios creates a stack trace that shows you exactly what and where the error occurred.

Here is an example of invalid syntax for assigning a variable using Helios.

`tx = ctx.tx;`

*[Figure 12.7](#c12.xhtml#fig12_7)* shows the error message, which states the type of error, the script name, and the line number.

![](OEBPS/images/Figure-12.7.jpg)

**Figure 12.7:** Helios Builder Error

Here is an example of an invalid variable assignment for Aiken.

`let { transaction, purpose } = context`

This will generate an error and indicate the line number and reason for the error (refer to *[Figure 12.8](#c12.xhtml#fig12_8)*).

![](OEBPS/images/Figure-12.8.jpg)

**Figure 12.8:** Aiken Builder Error

# [Transaction Builder Errors](#toc.xhtml#s327a)

Both Helios and Lucid have good transaction-building error messages, and there are a lot of error conditions and different reasons why an error may occur. The most common error is insufficient funds because a transaction is not balanced. This can occur because there is insufficient Ada to cover transaction fees or if there are not enough tokens being minted to match the outputs. Luckily these errors can be debugged using a local debugger and you should be able to identify the problem. If you still have issues, search and ask questions on the Cardano stack exchange[⁴](#c12.xhtml#ftn4) or the Helios[⁵](#c12.xhtml#ftn5) and Lucid/Translucent[⁶](#c12.xhtml#ftn6) discord channels accordingly.

# [Cardano Node Errors](#toc.xhtml#s328a)

Unfortunately, Cardano Node (Ledger) errors are the most challenging to diagnose. This is because you will see unfamiliar error messages that are poorly formatted, making them difficult to read[⁷](#c12.xhtml#ftn7) and understand. *[Figure 12.9](#c12.xhtml#fig12_9)* provides an example of a Cardano Node error you may see when a transaction fails.

![](OEBPS/images/Figure-12.9.jpg)

**Figure 12.9:** Cardano Node Error

To better understand what the error messages mean, you may need to refer to the Cardano Ledger[⁸](#c12.xhtml#ftn8) source code written in Haskell. You will see the code and comments that can explain why an error occurs. The example in *[Figure 12.9](#c12.xhtml#fig12_9)* is fairly straightforward and is an execution budget error. There are other errors not as obvious and may require looking at the code to understand what the error means. Fortunately, most of these errors are now caught by the off-chain transaction builder, so encountering Cardano Node errors is not as common as it used to be.

# [Wallet Errors](#toc.xhtml#s329a)

The last type of error we will review is wallet error. These occur when using a browser extension wallet and are listed in *[Table 12.1](#c12.xhtml#tab12_1)*.

| **Error Types** || **Error Name** || **Description** || **Value** |
| --- | --- | --- | --- |
| API Error || `InvalidRequest` || Inputs are not valid and do not conform to the CIP-0030 specification || \-1 |
|  || `InternalError` || An internal error occurred during this request || \-2 |
|  || `Refused` || The dApp was not approved to access the browser wallet || \-3 |
|  || `AccountChange` || The wallet account has been changed || \-4 |
| Data Sign Error || `ProofGeneration` || The data could not be signed by the wallet || 1 |
|  || `AddressNotPK` || The address was invalid and not a public key hash address || 2 |
|  || `UserDeclined` || The user declined to sign the data || 3 |
| PaginateError || `maxSize` || The maximum size supported for pagination. Will return the amount supported if the amount requested has exceeded the limit || maxSize |
| Tx Send Error || `Refused` || The wallet refuses to send the tx (for example, it could be rate limiting) || 1 |
|  || Failure || The Wallet could not send the tx || 2 |
| Tx Sign Error || `ProofGeneration` || The Wallet was not able to sign the transaction || 1 |
|  || `UserDeclined` || The user declined to sign the transaction || 2 |

**Table 12.1:** Browser Extension Wallet Errors[⁹](#c12.xhtml#ftn9)

# [Conclusion](#toc.xhtml#s330a)

This chapter provided an overview of debugging tools and techniques for Helios and Lucid + Aiken. We explored how to generate **CBOR** for a transaction and data types to compare it against formal specifications. We also looked at what to do if the Plutus script exceeds the CPU and memory execution limits and suggestions to improve script performance. We then explored how Helios and Lucid + Aiken frameworks provide error messages when we build and submit a transaction. Cardano Node errors were also examined and why we may need to look at the Cardano Ledger source code to troubleshoot if they occur. Finally, we closed the chapter by reviewing browser-based wallet errors that follow the CIP-0030 specification. In the next chapter, we will explore and review the Cardano ecosystem and the resources available to help you build an application on the Cardano blockchain.

# [Points to Remember](#toc.xhtml#s331a)

*   Debugging Smart Contracts involves emitting traces that can print variables and state information.
*   Both Helios and Aiken support traces and have the capability to trace boolean expressions.
*   `Trace` and `print` statements in Helios are removed if the `optimize` flag is set to `true`.
*   Traces in Aiken are removed by default and only present if enabled during the `aiken build`.
*   Converting a transaction to **CBOR** is helpful because you can then compare the transaction structure to the **CDDL** specifications for correctness.
*   CPU and memory execution budget errors are usually detected by the off-chain transaction builder framework.
*   By querying the chain using cardano-cli or blockchain explorers, you can find the current protocol parameters.
*   Unbalanced transactions are the most common error when using off-chain transaction builders.
*   Errors occurring only on the Cardano Node and not caught by the off-chain transaction builder are rare but can happen.
*   Wallet errors are well-documented and return a status code that will map back to a well-defined error message and description.

# [Multiple Choice Questions](#toc.xhtml#s332a)

1.  When can you use a local IDE debugger to help troubleshoot a Smart Contract? 
    1.  An error that only occurs on the Cardano Node
    2.  Off-chain transaction builder error
    3.  Plutus smart contact error
    4.  All of the above
2.  When would you want to turn on traces in production? 
    1.  To help troubleshoot a production issue
    2.  To improve performance
    3.  To capture user analytics
    4.  None of the above
3.  Where can you find the latest protocol parameters? 
    1.  The `shelley-genesis.json` file
    2.  The `alonzo-genesis.json` file
    3.  The node `config.json` file
    4.  An active Cardano network
4.  Execution budget errors can occur because? 
    1.  A difference between what was calculated locally and the Cardano node
    2.  Cardano is non-deterministic
    3.  It depends on what Cardano node is executing the script
    4.  Different Cardano node versions
5.  CBOR uses what type of ordering? 
    1.  FIFO
    2.  Lexical
    3.  LIFO
    4.  Canonical

# [Answers](#toc.xhtml#s333a)

1.  b
2.  a
3.  d
4.  a
5.  d

# [Questions](#toc.xhtml#s334a)

1.  What are other common sources of errors when writing Cardano Smart Contracts?
2.  What additional optimization techniques exist to improve Plutus script performance?
3.  Why was the Cardano Node written in Haskell?
4.  Why are outputs and inputs sorted differently?
5.  What are some new ways to help debug Plutus scripts?

# [Key Terms](#toc.xhtml#s335a)

*   **UPLC:** Untype Plutus Core, the compiled language generated from Helios or Aiken
*   **CBOR:** Concise Binary Object Representation
*   **CDDL**: Concise Data Definition Library
*   **UTXO**: Unspent Transaction Output

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c12.xhtml#ftn1a) [https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/babbage/impl/cddl-files/babbage.cddl](https://github.com/IntersectMBO/cardano-ledger/blob/master/eras/babbage/impl/cddl-files/babbage.cddl)

[²](#c12.xhtml#ftn2a) [https://datatracker.ietf.org/doc/html/rfc7049#section-3.9](https://datatracker.ietf.org/doc/html/rfc7049#section-3.9)

[³](#c12.xhtml#ftn3a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0021](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0021)

[⁴](#c12.xhtml#ftn4a) [https://cardano.stackexchange.com/](https://cardano.stackexchange.com/)

[⁵](#c12.xhtml#ftn5a) [https://discord.gg/uARRRGXNRr](https://discord.gg/uARRRGXNRr)

[⁶](#c12.xhtml#ftn6a) [https://discord.gg/A4cpwNXzEC](https://discord.gg/A4cpwNXzEC)

[⁷](#c12.xhtml#ftn7a) [https://github.com/IntersectMBO/cardano-node/issues/3126](https://github.com/IntersectMBO/cardano-node/issues/3126)

[⁸](#c12.xhtml#ftn8a) [https://github.com/IntersectMBO/cardano-ledger/tree/master/eras/babbage/impl/src/Cardano/Ledger/Babbage/Rules](https://github.com/IntersectMBO/cardano-ledger/tree/master/eras/babbage/impl/src/Cardano/Ledger/Babbage/Rules)

[⁹](#c12.xhtml#ftn9a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0030#error-types](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0030#error-types)

# [CHAPTER 13](#toc.xhtml#c13)

# [Cardano Ecosystem](#toc.xhtml#c13)

# [Introduction](#toc.xhtml#s336a)

This chapter will first review the state of Cardano with the most recently published report by Messari[¹](#c13.xhtml#ftn1). Next, we will look at the Cardano GitHub repositories containing all the source code and specifications for the Cardano blockchain. We will examine the Cardano Improvement Process (**CIP**) and how the Cardano blockchain changes and improvements are made. Then, we will look at the newly created Intersect and the creation of a Members-Based Organization (**MBO**) for Cardano. Next, we will explore the era of Voltaire and CIP-1694 regarding Cardano governance. We will then discuss on-chain governance actions such as protocol parameter changes, hard forks, and treasury withdrawals. We will also review the Stake Pool Operator’s (SPO) role and where to find additional information on them. Furthermore, we will also examine Project Catalyst, one of the largest decentralized innovation platforms that provides grant funding to Cardano projects. Next, we will review Atala Prism, which enables decentralized identity and provides Self Sovereign Identity (**SSI**) solutions. We will also look at Midnight, a data-protection sidechain being built using the Cardano partner chain framework. Finally, we will discuss additional Cardano Smart Contract development languages and learning resources.

# [Structure](#toc.xhtml#s337a)

In this chapter, we will discuss the following topics:

*   State of Cardano
*   Cardano GitHub Repositories
*   Cardano Improvement Process (**CIP**)
*   Member Based Organization (Intersect)
*   CIP-1694
*   Stake Pool Operators
*   Project Catalyst
*   Atala Prism (HyperLedger Identus)
*   Midnight
*   Additional Smart Contract Languages
*   Learning Resources

# [State of Cardano](#toc.xhtml#s338a)

Messari released its latest Q4, 2023 report on Cardano, and it is worth reviewing some of the key insights of that report.[²](#c13.xhtml#ftn2)

*   The Cardano Total Value Locked (TVL) of Ada in DeFi protocols increased 223.6% year over year. When converted to USD, this ranked Cardano TVL 11th compared to all other blockchains. It is important to mention that staking is not included in Cardano TVL, whereas it is on other blockchains.
*   Circulating market capitalization is at 21.1B USD, a 145.3% YoY increase
*   The Treasury balance is 1.43B Ada (or 861.4M USD)
*   The Nakamoto coefficient was at 31 which is higher (better) than other **PoS** blockchains. It is important to be aware that it is not always possible to determine if multiple pools are in fact operated by the same entity.[³](#c13.xhtml#ftn3) This was one of the reasons why the Edinburgh Decentralization Index (**EDI**) was created.[⁴](#c13.xhtml#ftn4)

One of the best ways to explore the Cardano ecosystem is to use a website like Cardano Cube.[⁵](#c13.xhtml#ftn5) The website breaks down the ecosystem into the following categories and has project logos and links in each category, including:

*   AI
*   Community and DAO
*   DeFi
*   Developer Tools
*   Dex - Liquidity
*   Education
*   Gaming
*   Identity and Data
*   Infrastructure
*   Launchpad
*   Lending and Borrowing
*   Marketplaces
*   Meme Coins
*   Metaverse
*   Payment and Stablecoins
*   Social
*   Tools and Explorers
*   Wallets

Year after year, the Cardano ecosystem continues to expand, grow, and mature.

# [Cardano GitHub Repositories](#toc.xhtml#s339a)

The Cardano blockchain was built by **IOG** (formerly IOHK), and they controlled and maintained the Cardano GitHub repositories. In Q4 of 2023, these repositories were handed over to Intersect, which oversees the Cardano Membership Based Organization (**MBO**). The Cardano blockchain source code is fully open-source and built with Haskell. Haskell is a very powerful functional programming language and an excellent choice for building high-assurance, complex software that can be linked back to a formal verification or specification.[⁶](#c13.xhtml#ftn6) The following is a list of the core Cardano blockchain GitHub repositories[⁷](#c13.xhtml#ftn7):

*   Cardano API[⁸](#c13.xhtml#ftn8)
*   Cardano Base[⁹](#c13.xhtml#ftn9)
*   Cardano Ledger[^(10)](#c13.xhtml#ftn10)
*   Cardano Node[^(11)](#c13.xhtml#ftn11)
*   Formal Ledger Specifications[^(12)](#c13.xhtml#ftn12)
*   Ouroboros Consensus[^(13)](#c13.xhtml#ftn13)
*   Ouroboros Network[^(14)](#c13.xhtml#ftn14)
*   Plutus Core[^(15)](#c13.xhtml#ftn15)

# [Cardano Improvement Process (CIP)](#toc.xhtml#s340a)

The Cardano Improvement Process is the mechanism to request and implement changes on the Cardano blockchain. It is important to mention that the **CIP** process focuses on how to get changes done on the Cardano blockchain and not the governance or prioritization of what changes should be done and when. The **CIPs** are located on GitHub[^(16)](#c13.xhtml#ftn16) and have the following states:

*   **Proposed:** Meets all of the **CIP** criteria but not yet active
*   **Active:** Is ready for, or in production
*   **Inactive**: No longer relevant or has been withdrawn
*   **Draft**: Is no longer used, but some older **CIP**s may still be in this state. It is similar to a Proposed **CIP** pull request that has not been merged due to missing or incomplete information.

The onus to obtain feedback and alignment from impacted teams is on the **CIP** author. Cardano is a large, complex system so it may not always be clear who the impacted teams are and they may change over time. That said, the steps to get a **CIP** from concept to implementation are as follows:

1.  The **CIP** author opens a pull request with the required CIP information and format.
2.  The **CIP** author seeks feedback and input from impacted teams.
3.  **CIP** editors review incoming **CIP**s and respond with feedback.
4.  **CIP** editors may invite authors and other relevant teams/individuals for reviews to facilitate discussions, feedback, and alignment.
5.  Once the **CIP** pull request contains all required information, including sufficient detail, feedback, impact analysis, and a path to active, it will be merged with the main CIP branch.
6.  When the **CIP** status changes to Active, it will be implemented following the **CIP**’s documented implementation plan.

**CIP** Editors are responsible for safeguarding the **CIP** process and will form groups to help enforce the standards outlined in CIP-0001.[^(17)](#c13.xhtml#ftn17) **CIP** Reviewers may be subject matter experts who are engaged to provide feedback and review a particular **CIP**. **CIP** Editors are not expected to be experts in all areas of Cardano, and it is the responsibility of the **CIP** author to ensure the satisfactory involvement of the required reviewer(s) of a **CIP**. **CIP** Editors can be nominated by existing **CIP** editors or community members if they have shown active contributions to the **CIP** process regularly.[^(18)](#c13.xhtml#ftn18)

There is a lot more detailed information on **CIP**s and the **CIP** process that the reader must review[^(19)](#c13.xhtml#ftn19) thoroughly before proceeding with a **CIP** pull request. A Cardano Problem Statement (**CPS**)[^(20)](#c13.xhtml#ftn20) has also been introduced to help capture and document a particular problem, which can be used to help create a **CIP**. A **CPS** is not required but is advisable when requesting a change via the **CIP** process.

# [Member-Based Organization (Intersect)](#toc.xhtml#s341a)

Intersect was launched in July 2023 and is the Member-Based Organization (**MBO**) of Cardano. Using community governance, Intersect will prioritize and allocate Cardano treasury funding for future maintenance and development of the Cardano Blockchain. To achieve this goal, Intersect focuses on five key areas[^(21)](#c13.xhtml#ftn21):

*   Support the community and growth of the Cardano ecosystem.
*   Administer and advocate on-chain governance as documented by CIP-1694.[^(22)](#c13.xhtml#ftn22)
*   Oversee the delivery of the Cardano Technical Roadmap.
*   Facilitate the continuity of Cardano system stability.
*   Coordinate open-source development of Cardano core technologies.

Intersect is a non-profit corporation based in Wyoming, United States. Wyoming has favorable legislation[^(23)](#c13.xhtml#ftn23) regarding the legal structure of a decentralized autonomous organization (**DAO**), and that is why Intersect was incorporated in that state.[^(24)](#c13.xhtml#ftn24) There is a board of directors for Intersect, and they meet monthly with meeting notes published on the Intersect website.[^(25)](#c13.xhtml#ftn25) Any Ada holder can join Intersect[^(26)](#c13.xhtml#ftn26) with community announcements, committee working groups, and meeting information shared on Discord once you become a member.

# [CIP-1694](#toc.xhtml#s342a)

Cardano is now in the Voltaire era of the Cardano roadmap which will use on-chain governance to allow the Cardano network to become a self-sustaining system.[^(27)](#c13.xhtml#ftn27) CIP-1694 documents how an on-chain governance system should work and what would be required for an initial bootstrapping phase known as Minimal Viable Governance (**MVG)**. The most important aspect of CIP-1694 is the confirmation that one Ada equals one vote when on-chain voting occurs.

There are three governing bodies documented in CIP-1694 and each play a key role in the governance process.[^(28)](#c13.xhtml#ftn28)

*   Delegated Representative (**DRep)**
*   Stake Pool Operator (**SPO**)
*   Constitutional Committee (**CC**)

These governing bodies will vote to approve or reject an on-chain proposal depending on the type of proposal being voted on. On-chain governance tooling is currently (as of writing) being tested on the Sanchonet Testnet.[^(29)](#c13.xhtml#ftn29) Tooling is needed to allow **DReps** and **SPOs** to participate in on-chain governance easily and conveniently.

# [Delegated Representatives (DReps)](#toc.xhtml#s343a)

For an Ada holder to vote on an on-chain proposal, they would delegate their voting power like a user delegates their staked Ada to a Stake Pool Operator. Any Ada holder can submit an on-chain proposal, but typically **DReps** with their delegated Ada voting power will cast votes. **DReps** will then vote on proposals and the outcome will indicate whether the vote has been approved or not by the **DRep** governing body.

# [Stake Pool Operators (SPOs)](#toc.xhtml#s344a)

SPOs play a critical role in maintaining the network’s security by operating the nodes that process and distribute blocks in the Cardano blockchain. As a result, they will have a vote when there are on-chain proposals that involve a hard fork which in turn requires upgrading a network node.[^(30)](#c13.xhtml#ftn30) They also participate in votes regarding changes to the constitutional committee. Similar to DReps, the collective **SPO** voting power is used to determine if a vote has been approved or not by the **SPO** governing body.

# [Constitutional Committee (CC)](#toc.xhtml#s345a)

The **CC** is a group of members elected to the committee for a fixed period. The role of the **CC** is to vote only on the constitutionality of a particular proposal.[^(31)](#c13.xhtml#ftn31) For example, if the constitution states that a treasury must always exist with 0.125% of all Ada in circulation, then the CC would be opposed to a vote withdrawing Ada from the treasury that violates this threshold. The **CC** can be dissolved at any time with a vote of no confidence, on which only **DRep**s and **SPO**s can vote. The **CC** quorum parameters will be used to determine if a vote has been approved or not by the **CC** governing body.

There are seven governance actions documented in CIP-1694 and shown in *[Table 13.1](#c13.xhtml#tab13_1):*

| **Governance Action** || **Purpose** || **Who Can Vote** |
| --- | --- | --- |
| Motion of no-confidence || Used to dissolve the CC || DRep, SPO |
| New CC or CC threshold changes || Elect members to the CC or change the CC quorum requirements or term limits || DRep, SPO |
| Update to the Constitution || Make changes to the constitution || DRep, CC |
| Hard-fork initiation || Approval for a hard fork || DRep, SPO, CC |
| Protocol parameter changes || Approval for protocol parameter changes || DRep, CC |
| Treasury withdrawal || Approval to make a withdrawal from the treasury || DRep, CC |
| Info || Creates on-chain info only record || DRep, CC |

**Table 13.1:** Governance Actions[^(32)](#c13.xhtml#ftn32)

# [Stake Pool Operators](#toc.xhtml#s346a)

A key aspect of the success of Cardano’s Proof-Of-Stake protocol is the role of the staking and the Stake Pool Operator (**SPO**). A lot of analysis and design went into the mechanics of how an Ada holder can easily and securely delegate their Ada to a stake pool operator while still retaining self-custody. As a result, there is now a large community of Stake Pool Operators that you can stake your Ada with. Most Cardano wallets will provide you with a list of Stakepool operators ranked by Return Of Stake (**ROS**) that you can choose. The following is a list of online tools that allow searching and filtering of Cardano **SPO**s:

*   PoolTool[^(33)](#c13.xhtml#ftn33)
*   ADASTAT[^(34)](#c13.xhtml#ftn34)
*   CExplorer[^(35)](#c13.xhtml#ftn35)
*   AdaPool[^(36)](#c13.xhtml#ftn36)
*   CardanoScan[^(37)](#c13.xhtml#ftn37)
*   Pool.pm[^(38)](#c13.xhtml#ftn38)

Setting up a Stake Pool is outside of the scope of this book, but there are a lot of great resources online and communities that can help you get started:

*   Operate A Stake Pool[^(39)](#c13.xhtml#ftn39)
*   Guild Operators[^(40)](#c13.xhtml#ftn40)
*   CoinCashew[^(41)](#c13.xhtml#ftn41)
*   IOG Academy[^(42)](#c13.xhtml#ftn42)

# [Project Catalyst](#toc.xhtml#s347a)

One of the most interesting aspects of the Cardano ecosystem is Project Catalyst. Project Catalyst started as an experiment to give grants to projects based on voting by Ada holders. There have been 11 Funding rounds, with Fund 1 announced in September 2020[^(43)](#c13.xhtml#ftn43). The amount of funding has increased between Fund 1 and Fund 9 and is now currently set at 50 Million Ada per funding round. Using the IdeaScale platform[^(44)](#c13.xhtml#ftn44) Project Catalyst claims to be one of the largest decentralized innovation funds in the world.[^(45)](#c13.xhtml#ftn45)

A funding round typically lasts approximately 4 months, allowing the community to participate in various ways and receive compensation in Ada. The community can participate as reviewers, project submitters, voters, or milestone verifiers. The format has changed over time and will continue to evolve based on community feedback and input. Anyone can submit a proposal and form a team; this is one of the main drivers of attracting and retaining talent in the ecosystem. Please refer the following for more information on project catalyst:

*   Cardano IdeaScale[^(46)](#c13.xhtml#ftn46)
*   Project Catalyst Website[^(47)](#c13.xhtml#ftn47)
*   **IOG** (**IOHK**) YouTube Channel[^(48)](#c13.xhtml#ftn48)
*   Project Catalyst Announcements Telegram Channel[^(49)](#c13.xhtml#ftn49)

A typical Project Catalyst timeline is shown in *[Figure 13.1](#c13.xhtml#fig13_1):*

![](OEBPS/images/Figure-13.1.jpg)

**Figure 13.1:** Fund 11 Timeline

# [Atala Prism (HyperLedger Identus)](#toc.xhtml#s348a)

Digital Identity and Self-Sovereign Identity (**SSI**) have the potential to become the next killer app in the blockchain space. Using a secure and decentralized blockchain, an identity solution can allow users to control and own their identity. This is a significant shift from today where a handful of tech companies own your digital identity and where you have no control over how it is used. Furthermore, social media platforms are littered with bots, scammers, and impersonators because **SSI** systems are not used. Social media companies are not financially incentivized to fix this issue because their revenue is based on users on the platform, whether real people or not.

The challenge and the opportunity is that people will start demanding assurances that the person or entity they are interacting with is genuine and accurate. Second, users will want to control who has access to their identity. The Atala Prism **SSI** framework which follows the **W3C**\-**DID** standard[^(50)](#c13.xhtml#ftn50), allows you to build secure, private, and verifiable interactions.[^(51)](#c13.xhtml#ftn51) Using **SSI**, you can solve both problems, verify who you are dealing with, and control who has access to your identity. Atala Prism has recently been open-sourced and renamed to HyperLedger Identus.[^(52)](#c13.xhtml#ftn52)

# [Midnight](#toc.xhtml#s349a)

Midnight is a data-protection blockchain using zero-knowledge proofs to transact with a public permissionless blockchain while keeping sensitive data private.[^(53)](#c13.xhtml#ftn53) This has several advantages and can be used in use cases such as identity verification, tokenized asset privacy, AI modules, credit scoring, and voting.[^(54)](#c13.xhtml#ftn54) Midnight is being built using Parity Technologies’ Substrate stack which lays the foundation for additional partner chains in the future.[^(55)](#c13.xhtml#ftn55) The concept of partner chains will help realize the goal of separation of the Cardano Settlement Layer (**CSL**) and the Cardano Computation Layer (**CCL**).[^(56)](#c13.xhtml#ftn56) Cardano also has other side chains[^(57)](#c13.xhtml#ftn57) such as Milkomeda C1[^(58)](#c13.xhtml#ftn58), Wanchain[^(59)](#c13.xhtml#ftn59), and World Mobile[^(60)](#c13.xhtml#ftn60).

# [Additional Cardano Smart Contract Languages](#toc.xhtml#s350a)

Although this book has focused on Helios and Lucid + Aiken for Cardano Smart Contract development, other options are available to developers, including:

*   **PlutusTx** is a Haskell Module and was the first way to write Cardano Smart Contracts. Several resources, including the Plutus Developer Portal[^(61)](#c13.xhtml#ftn61) and the Plutus Pioneer Program[^(62)](#c13.xhtml#ftn62), are available for writing smart contracts using PlutusTx in Haskell.
*   **PyCardano + OpShin**[^(63)](#c13.xhtml#ftn63) allows you to write Cardano Smart Contracts using Python for both the off-chain and on-chain code respectively.
*   **Plu-ts**[^(64)](#c13.xhtml#ftn64) also allows you to write both the on-chain and off-chain code for Cardano Smart Contracts but in typescript.

# [Learning Resources](#toc.xhtml#s351a)

There are many excellent resources available to help you learn about Cardano.

*   **Cardano Academy**[^(65)](#c13.xhtml#ftn65)**,** created by the Cardano Foundation is an excellent all-around resource on blockchain and Cardano.
*   **IOG Academy**[^(66)](#c13.xhtml#ftn66), created by IOG (IOHK), contains a collection of videos on Cardano, Haskell, and the Plutus Pioneers Program.
*   **Emurgo Academy**[^(67)](#c13.xhtml#ftn67), created by Emurgo is a paid program with some of the best developer resources in the ecosystem.
*   **Gimbalabs**[^(68)](#c13.xhtml#ftn68), a pioneer in the open education space in Cardano, focuses on project-based learning and online coding sessions for learning and collaboration.
*   **Learn Cardano**[^(69)](#c13.xhtml#ftn69) always has great topics and speakers on its show, making it a go-to resource for keeping up to date on the Cardano ecosystem.
*   **Cardano With Paul**[^(70)](#c13.xhtml#ftn70) has been creating great Cardano content for years. It continues to showcase exciting new projects and keeps up-to-date with the latest developments in Cardano.
*   And many more…

# [Conclusion](#toc.xhtml#s352a)

We started the chapter by reviewing the state of Cardano and looking at the published Messari Q4, 2023 report. Next, we reviewed the public GitHub repositories transferred to Intersect, which contained the Cardano blockchain source code. The **CIP** process and how changes are made to the Cardano blockchain using a CIP pull request, with the required information, were examined in the correct format. Intersect, the Cardano Members Based Organization (**MBO**), and the five areas it focuses on were also discussed. Next, we discussed the Voltaire era and how CIP-1694 captures the mechanics of on-chain voting for Cardano governance. We reviewed the list of governance actions such as protocol parameter changes, hard forks, and treasury withdrawals. We also looked at **SPO** return on stake (ROS) rankings and the role of Project Catalyst in the Cardano ecosystem. We also introduced Atala Prism, a Self-Sovereign Identity (**SSI**) solution built on Cardano, and the benefits and opportunities it can provide. Finally, we discussed Midnight, the first type of partner chain on Cardano, as well as additional Smart Contract languages and learning resources. The next and final chapter will discuss the ethos and social impact of Cardano and how blockchain is following the five stages of technology adoption.

# [Points to Remember](#toc.xhtml#s353a)

*   Cardano Total Value Locked (**TVL**) does not include the 22.68B Ada staked in the Cardano network.
*   Nakamoto coefficients can be misleading because the entities controlling a stake pool are not always known.
*   The public Cardano GitHub repositories are now managed by Intersect.
*   The **CIP** process is about making changes on the Cardano network, not governing or prioritizing such requests.
*   The **CIP** author is responsible for securing feedback and alignment on a proposed **CIP**.
*   Intersect, a non-profit **DAO** is the Cardano Members Based Organization.
*   CIP-1694 documents how Cardano on-chain voting should work and the initial bootstrapping phase known as Minimal Viable Governance (**MVG**).
*   **DRep**, **SPO**, and **CC** are the three governing bodies of on-chain voting.
*   Different governing bodies will be required to vote depending on the governance action.
*   **DRep**s use delegated voting power from Ada holders to cast a vote, which is aggregated into a yes or no DRep vote for a governance action.
*   The **CC** can be dissolved when a governance action of no confidence is passed.
*   The **CC** members, quorum requirements, and term limits are voted on by DReps and **SPO**s.
*   Project Catalyst, one of the largest decentralized innovation funds in the world, allows Ada holders to vote on projects that will receive grant funding from the treasury.
*   There have been 11 Project Catalyst funds, with the last two funds having 50M in Ada available for grants.
*   Atala Prism is a Self-Sovereign Identity (**SSI**) solution built on the Cardano blockchain.
*   **SSI** allows users to control their identity and who has access to it.
*   Midnight is a data protection side chain built using zero-knowledge-proof technology.
*   Midnight is an example of a Cardano partner chain that separates the Cardano Settlement Layer from the Cardano Computation Layer.

# [Multiple Choice Questions](#toc.xhtml#s354a)

1.  Who manages the Cardano open-source code repositories? 
    1.  Intersect
    2.  IOHK
    3.  Cardano Foundation
    4.  All of the above
2.  What example would not be well suited for a CIP? 
    1.  Suggest a change to the ledger to accommodate a feature request
    2.  Suggest a change to the protocol parameters to improve performance
    3.  Request a treasury funding withdrawal
    4.  Document on-chain governance processes
3.  What is the goal of CIP-1694? 
    1.  Create the Cardano constitution
    2.  Finalize Cardano governance and end the Voltaire era
    3.  Elect members to the constitutional committee
    4.  Document the on-chain governance processes and establish MVG
4.  What is false about DReps? 
    1.  Ada holders will be able to delegate their Ada voting power to a DRep
    2.  Ada holders will not be able to change their Ada delegation to a DRep
    3.  Ada holders can change or withdraw their Ada delegation by submitting a transaction
    4.  Ada holders will be able to see what governance actions their DRep has voted on
5.  What statement is true about Project Catalyst? 
    1.  Project catalyst controls the funds in the Cardano Treasury
    2.  Most of the Cardano treasury is spent by Project Catalyst
    3.  20% of transaction fees go to Project Catalyst
    4.  The Project Catalyst operations team is funded by Project Catalyst

# [Answers](#toc.xhtml#s355a)

1.  a
2.  c
3.  d
4.  b
5.  d

# [Questions](#toc.xhtml#s356a)

1.  Why did IOG (formerly IOHK) decide to transfer ownership of the Cardano open-source repositories to Intersect?
2.  What improvements or suggestions do you have for the CIP process?
3.  What other jurisdictions would have been suitable to incorporate Intersect in?
4.  Why is CIP-1694 only focused on Minimal Viable Governance?
5.  Can a user be a DRep, Stake Pool Operator, and CC member simultaneously? If so, why is this (or not) an issue?
6.  What are some of the difficulties and challenges of running Project Catalyst?
7.  What are the barriers to widespread adoption of SSI?
8.  What are the risks of using data-protection blockchains?

# [Key Terms](#toc.xhtml#s357a)

*   **CC:** Constitutionals Committee
*   **CCL:** Cardano Computation Layer
*   **CIP:** Cardano Improvement Process
*   **CPS**: Cardano Problem Statement
*   **CSL:** Cardano Settlement Layer
*   **DAO:** Decentralized Autonomous Organization
*   **DID:** Decentralized Identifier
*   **DReps:** Delegated Representatives
*   **IOG:** Input Output Global
*   **IOHK:** Input Output Hong Kong
*   **MBO:** Members Based Organization
*   **MVG:** Minimal Viable Governance
*   **ROS:** Return On Stake
*   **SPO:** Stake Pool Operator
*   **SSI:** Self Sovereign Identity
*   **TVL:** Total Value Locked
*   **W3C:** World Wide Web Consortium

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c13.xhtml#ftn1a) [https://messari.io/](https://messari.io/)

[²](#c13.xhtml#ftn2a) Red Sheehan, “State of Cardano Q4 2023”

[³](#c13.xhtml#ftn3a) [https://nakaflow.io/](https://nakaflow.io/)

[⁴](#c13.xhtml#ftn4a) [https://www.ed.ac.uk/informatics/blockchain/edi](https://www.ed.ac.uk/informatics/blockchain/edi)

[⁵](#c13.xhtml#ftn5a) [https://www.cardanocube.com/cardano-ecosystem-interactive-map](https://www.cardanocube.com/cardano-ecosystem-interactive-map)

[⁶](#c13.xhtml#ftn6a) [https://why.cardano.org/en/science-and-engineering/formal-specification-and-verification/](https://why.cardano.org/en/science-and-engineering/formal-specification-and-verification/)

[⁷](#c13.xhtml#ftn7a) [https://github.com/orgs/IntersectMBO/repositories](https://github.com/orgs/IntersectMBO/repositories)

[⁸](#c13.xhtml#ftn8a) [https://github.com/IntersectMBO/cardano-api.git](https://github.com/IntersectMBO/cardano-api.git)

[⁹](#c13.xhtml#ftn9a) [https://github.com/IntersectMBO/cardano-base.git](https://github.com/IntersectMBO/cardano-base.git)

[^(10)](#c13.xhtml#ftn10a) [https://github.com/IntersectMBO/cardano-ledger.git](https://github.com/IntersectMBO/cardano-ledger.git)

[^(11)](#c13.xhtml#ftn11a) [https://github.com/IntersectMBO/cardano-node.git](https://github.com/IntersectMBO/cardano-node.git)

[^(12)](#c13.xhtml#ftn12a) [https://github.com/IntersectMBO/formal-ledger-specifications.git](https://github.com/IntersectMBO/formal-ledger-specifications.git)

[^(13)](#c13.xhtml#ftn13a) [https://github.com/IntersectMBO/ouroboros-consensus.git](https://github.com/IntersectMBO/ouroboros-consensus.git)

[^(14)](#c13.xhtml#ftn14a) [https://github.com/IntersectMBO/ouroboros-network.git](https://github.com/IntersectMBO/ouroboros-network.git)

[^(15)](#c13.xhtml#ftn15a) [https://github.com/IntersectMBO/plutus](https://github.com/IntersectMBO/plutus)

[^(16)](#c13.xhtml#ftn16a) [https://github.com/cardano-foundation/CIPs](https://github.com/cardano-foundation/CIPs)

[^(17)](#c13.xhtml#ftn17a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0001#editors](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0001#editors)

[^(18)](#c13.xhtml#ftn18a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0001#nomination](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0001#nomination)

[^(19)](#c13.xhtml#ftn19a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-0001](https://github.com/cardano-foundation/CIPs/tree/master/CIP-0001)

[^(20)](#c13.xhtml#ftn20a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-9999](https://github.com/cardano-foundation/CIPs/tree/master/CIP-9999)

[^(21)](#c13.xhtml#ftn21a) [https://docs.intersectmbo.org/intersect-overview/what-is-intersect](https://docs.intersectmbo.org/intersect-overview/what-is-intersect)

[^(22)](#c13.xhtml#ftn22a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694)

[^(23)](#c13.xhtml#ftn23a) Taras Zharun, “Wyoming LLC as a DAO Legal Wrapper: What You Need to Know

[^(24)](#c13.xhtml#ftn24a) [https://docs.intersectmbo.org/intersect-overview/intersects-structure](https://docs.intersectmbo.org/intersect-overview/intersects-structure)

[^(25)](#c13.xhtml#ftn25a) [https://docs.intersectmbo.org/intersect-overview/intersects-structure/intersect-governance/governing-board-meetings](https://docs.intersectmbo.org/intersect-overview/intersects-structure/intersect-governance/governing-board-meetings)

[^(26)](#c13.xhtml#ftn26a) [https://www.intersectmbo.org/join](https://www.intersectmbo.org/join)

[^(27)](#c13.xhtml#ftn27a) [https://roadmap.cardano.org/en/voltaire/](https://roadmap.cardano.org/en/voltaire/)

[^(28)](#c13.xhtml#ftn28a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694)

[^(29)](#c13.xhtml#ftn29a) [https://sancho.network/](https://sancho.network/)

[^(30)](#c13.xhtml#ftn30a) [https://www.essentialcardano.io/infographic/cip-1694-in-a-nutshell](https://www.essentialcardano.io/infographic/cip-1694-in-a-nutshell)

[^(31)](#c13.xhtml#ftn31a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#the-constitutional-committee](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#the-constitutional-committee)

[^(32)](#c13.xhtml#ftn32a) [https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#governance-actions](https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694#governance-actions)

[^(33)](#c13.xhtml#ftn33a) [https://pooltool.io/](https://pooltool.io/)

[^(34)](#c13.xhtml#ftn34a) [https://adastat.net/pools](https://adastat.net/pools)

[^(35)](#c13.xhtml#ftn35a) [https://cexplorer.io/pool](https://cexplorer.io/pool)

[^(36)](#c13.xhtml#ftn36a) [https://adapools.org/pool](https://adapools.org/pool)

[^(37)](#c13.xhtml#ftn37a) [https://cardanoscan.io/pools](https://cardanoscan.io/pools)

[^(38)](#c13.xhtml#ftn38a) [https://pool.pm/](https://pool.pm/)

[^(39)](#c13.xhtml#ftn39a) [https://developers.cardano.org/docs/operate-a-stake-pool/](https://developers.cardano.org/docs/operate-a-stake-pool/)

[^(40)](#c13.xhtml#ftn40a) [https://cardano-community.github.io/guild-operators/](https://cardano-community.github.io/guild-operators/)

[^(41)](#c13.xhtml#ftn41a) [https://www.coincashew.com/coins/overview-ada/guide-how-to-build-a-haskell-stakepool-node](https://www.coincashew.com/coins/overview-ada/guide-how-to-build-a-haskell-stakepool-node)

[^(42)](#c13.xhtml#ftn42a) Crypto Carlos, “Node course | Creating a stake pool, the setup”

[^(43)](#c13.xhtml#ftn43a) [https://iohk.io/en/blog/posts/2020/09/16/project-catalyst-introducing-our-first-public-fund-for-cardano-community-innovation/](https://iohk.io/en/blog/posts/2020/09/16/project-catalyst-introducing-our-first-public-fund-for-cardano-community-innovation/)

[^(44)](#c13.xhtml#ftn44a) [https://cardano.ideascale.com/c/landing](https://cardano.ideascale.com/c/landing)

[^(45)](#c13.xhtml#ftn45a) Tim Richmond, “Project Catalyst - A virtuous cycle of Cardano ecosystem development”

[^(46)](#c13.xhtml#ftn46a) [https://cardano.ideascale.com/c/landing](https://cardano.ideascale.com/c/landing)

[^(47)](#c13.xhtml#ftn47a) [https://projectcatalyst.io/](https://projectcatalyst.io/)

[^(48)](#c13.xhtml#ftn48a) [https://www.youtube.com/@IohkIo](https://www.youtube.com/@IohkIo)

[^(49)](#c13.xhtml#ftn49a) [https://t.me/cardanocatalyst](https://t.me/cardanocatalyst)

[^(50)](#c13.xhtml#ftn50a) [https://www.w3.org/TR/did-core/](https://www.w3.org/TR/did-core/)

[^(51)](#c13.xhtml#ftn51a) [https://atalaprism.io/#why](https://atalaprism.io/#why)

[^(52)](#c13.xhtml#ftn52a) [https://github.com/hyperledger/identus](https://github.com/hyperledger/identus)

[^(53)](#c13.xhtml#ftn53a) [https://midnight.network/](https://midnight.network/)

[^(54)](#c13.xhtml#ftn54a) Neil Burgess, "Calling trailblazers to Midnight"

[^(55)](#c13.xhtml#ftn55a) Mike Ward, "Partner chains are coming to Cardano"

[^(56)](#c13.xhtml#ftn56a) Mike Ward, "Partner chains are coming to Cardano"

[^(57)](#c13.xhtml#ftn57a) Red Sheehan, "State of Cardano Q4 2023"

[^(58)](#c13.xhtml#ftn58a) [https://milkomeda.com/](https://milkomeda.com/)

[^(59)](#c13.xhtml#ftn59a) [https://www.wanchain.org/](https://www.wanchain.org/)

[^(60)](#c13.xhtml#ftn60a) [https://worldmobile.io/en](https://worldmobile.io/en)

[^(61)](#c13.xhtml#ftn61a) [https://developers.cardano.org/docs/smart-contracts/plutus](https://developers.cardano.org/docs/smart-contracts/plutus)

[^(62)](#c13.xhtml#ftn62a) [https://www.youtube.com/playlist?list=PLnPTB0CuBOBypVDf1oGcsvnJGJg8h-LII](https://www.youtube.com/playlist?list=PLnPTB0CuBOBypVDf1oGcsvnJGJg8h-LII)

[^(63)](#c13.xhtml#ftn63a) [https://developers.cardano.org/docs/smart-contracts/opshin](https://developers.cardano.org/docs/smart-contracts/opshin)

[^(64)](#c13.xhtml#ftn64a) [https://developers.cardano.org/docs/smart-contracts/plu-ts](https://developers.cardano.org/docs/smart-contracts/plu-ts)

[^(65)](#c13.xhtml#ftn65a) [https://academy.cardanofoundation.org/](https://academy.cardanofoundation.org/)

[^(66)](#c13.xhtml#ftn66a) [https://www.youtube.com/channel/UCX9j\_\_vYOJu00iqBrCzecVw](https://www.youtube.com/channel/UCX9j__vYOJu00iqBrCzecVw)

[^(67)](#c13.xhtml#ftn67a) [https://education.emurgo.io/](https://education.emurgo.io/)

[^(68)](#c13.xhtml#ftn68a) [https://gimbalabs.com/gimbalgrid](https://gimbalabs.com/gimbalgrid)

[^(69)](#c13.xhtml#ftn69a) [https://www.youtube.com/@LearnCardano](https://www.youtube.com/@LearnCardano)

[^(70)](#c13.xhtml#ftn70a) [https://www.youtube.com/@CardanoWithPaul](https://www.youtube.com/@CardanoWithPaul)

# [CHAPTER 14](#toc.xhtml#c14)

# [Closing Remarks](#toc.xhtml#c14)

# [Introduction](#toc.xhtml#s358a)

This chapter will review the ethos of Cardano and how it relates to the peer review process and formal methods. We will examine the software industry standards and how these standards fall short for high-assurance software. We will see how semi-formal methods were used to build Cardano and how cryptographic associations like **IACR** facilitate the peer review process. Next, we will look at the potential for social good using Cardano with real-world examples. We will also discuss regulatory and compliance risks and what to be aware of. Then, we will review the five stages of technology adoption and how they apply to blockchain. Finally, we will discuss the Cardano journey and the road to get here.

# [Structure](#toc.xhtml#s359a)

In this chapter, we will discuss the following topics:

*   Cardano Ethos
*   Software Industry Standards 
    *   Blockchain Risks
    *   Semi-Formal Methods
    *   IACR
*   Potential For Social Good
*   Regulatory and Compliance Risks
*   Technology Adoption
*   The Cardano Journey

# [Cardano Ethos](#toc.xhtml#s360a)

Openness and transparency are the ethos of Cardano[¹](#c14.xhtml#ftn1) and are one of the reasons why there is such an emphasis on peer review and formal methods. The peer review process for organizations such as The International Association for Cryptographic Research (**IACR**)[²](#c14.xhtml#ftn2) uses a double-blind process that makes both the author and the reviewer anonymous to each other.[³](#c14.xhtml#ftn3) This helps eliminate biases and promotes fairness and transparency during the review process. In addition to the peer review process, **IOG** (**IOHK**) applies formal methods that rigorously use mathematical techniques to ensure that software works as intended.[⁴](#c14.xhtml#ftn4) For example, the Cardano ledger code, written in Haskell, can be linked back to the formal specification which has been peer-reviewed. This level of traceability and transparency is unparalleled in the blockchain industry and is typically only used in high-assurance software found in the space, airline, and financial industries.[⁵](#c14.xhtml#ftn5)

Fundamentally, blockchain technology is about giving agency and self-control to the edges. The benefits of empowering the edges (people or employees) lead to higher productivity, better engagement, and social outcomes.[⁶](#c14.xhtml#ftn6) Since the underlying cryptocurrency token is free to trade, this will, however, result in speculation. This speculation is frequently abused where blockchains (and projects) masquerade as permissionless and decentralized with the primary purpose of extracting value. This has been an issue since the earliest days of Bitcoin with ICOs.[⁷](#c14.xhtml#ftn7) Therefore, it is advisable to align with blockchains and projects that focus on the service of others, eventually leading to correct price discovery, value, and market fit.

# [Software Industry Standards](#toc.xhtml#s361a)

Quality, resilience, and bug-free are not typically associated with most software, particularly that has been recently released. This “*Industry Standard*” is a low bar and is usually addressed by regular software updates to improve the quality of the software over time. This approach does not work well for blockchains! Blockchains, by their nature, are immutable, and once deployed, a *true* decentralized and permissionless blockchain cannot be stopped, reset, or patched by a central authority. Furthermore, blockchains can involve millions of dollars of value that can be stolen by exploiting a bug found in the software.

# [Blockchain Risks](#toc.xhtml#s362a)

Let us first look at what can go wrong when designing and deploying a blockchain. The following is a list of issues that could occur:[⁸](#c14.xhtml#ftn8)

*   Flawed protocol design
*   Incorrect implementation of the design
*   Typical software mistakes
*   Amateur cryptography implementations
*   Missing performance deadlines
*   Collapse under load
*   Failure to scale
*   DoS failures
*   Vulnerability to economic attacks
*   Social or voting collapse
*   Macroeconomic collapse
*   and more…

# [Semi-Formal Methods](#toc.xhtml#s363a)

As we can see, there are many pitfalls when designing and building a permissionless and decentralized blockchain. **IOG** (**IOHK**) mitigated these issues by linking together a semi-formal specification, a Haskell specification, and the Haskell implementation code, as illustrated in *[Figure 14.1](#c14.xhtml#fig14_1)*.

![](OEBPS/images/Figure-14.1.jpg)

**Figure 14.1:** Chain Of Evidence[⁹](#c14.xhtml#ftn9)

A semi-formal specification for the ledger defines transition types and transition rules which make it formal, but not machine-checked.[^(10)](#c14.xhtml#ftn10) By creating a Haskell specification, test cases can be run that compare the outputs of the specification executable to those created by the implementation executable. If the two outputs match, we can have reasonably high assurances that the implementation code implements the semi-formal specification. **IOG** continues to improve the formal verification process and has recently released a paper titled, “*Formal specification of the Cardano blockchain ledger, mechanized in Agda*.”[^(11)](#c14.xhtml#ftn11) The goal is to use Agda to create formal specifications going forward, with a work-in-progress version located on GitHub.[^(12)](#c14.xhtml#ftn12)

# [IACR](#toc.xhtml#s364a)

The International Association for Cryptographic Research (**IACR)** is a non-profit scientific organization that advances cryptology and related fields.[^(13)](#c14.xhtml#ftn13) It organizes three leading conferences that are used by academics in the field to present and review scientific papers:

*   Crypto
*   Eurocrypt
*   Asiacrypt

**IACR** also runs four additional specialized conferences, one symposium, and a series of cryptography training schools.[^(14)](#c14.xhtml#ftn14) The Journal of Cryptography is the flagship journal of the **IACR** and provides a forum for the publication of original work in modern information security.[^(15)](#c14.xhtml#ftn15)

# [Potential for Social Good](#toc.xhtml#s365a)

Cardano’s mission to bank the unbanked goes back to Charles Hoskinson’s TED talk in 2014 before Cardano even existed.[^(16)](#c14.xhtml#ftn16) Cardano began with a vision of a world without intermediaries, where individuals have control over their own data and how they can transact.[^(17)](#c14.xhtml#ftn17) This has resonated with many in the Cardano community and is why there are great synergies with companies like World Mobile, which are connecting the unconnected.[^(18)](#c14.xhtml#ftn18) Aspiring to be the financial operating system of the world,[^(19)](#c14.xhtml#ftn19) Cardano has significant potential for social good.

# [World Mobile](#toc.xhtml#s366a)

There are almost 3 billion people unconnected in the world, with 40% in developing countries not having access to a mobile network.[^(20)](#c14.xhtml#ftn20) World Mobile is creating a sharing economy for telecommunications which is only possible because of blockchain.[^(21)](#c14.xhtml#ftn21) World Mobile nodes can be purchased and receive World Mobile Tokens (WMT) from network transaction fees and token staking that incentivizes the network buildout. The mobile network is a Cardano sidechain that uses Decentralized Identifiers (**DID**s) for provisioning and billing.[^(22)](#c14.xhtml#ftn22) World Mobile has deployed networks in countries such as Tanzania and Zanzibar.[^(23)](#c14.xhtml#ftn23)

# [Empowa](#toc.xhtml#s367a)

Homeownership in Africa is out of reach for most people because of the high cost of borrowing (45%), which in turn leads to a housing supply shortage.[^(24)](#c14.xhtml#ftn24) Empowa is a decentralized property development and collectibles platform that provides microfinancing to underserved communities in Africa.[^(25)](#c14.xhtml#ftn25) Empowa has used the Cardano blockchain to finance affordable homes in Mozambique.[^(26)](#c14.xhtml#ftn26)

# [Crypto Green Research](#toc.xhtml#s368a)

Cardano ranks as one of the highest-scoring blockchains from an **ESG** perspective.[^(27)](#c14.xhtml#ftn27) It has very low energy consumption and electronic waste. It is best in class in transparent governance, with a good distribution of token assets and a low barrier to entry.[^(28)](#c14.xhtml#ftn28) As a result, Cardano scores on the following blockchain metrics.

*   **Environment:** A-
*   **Social:** A-
*   **Governance:** A+

# [Social Good Projects](#toc.xhtml#s369a)

Following is a list of additional examples of using Cardano for social good:

*   **IOG** (**IOHK)** issues digital identities to Ethiopian students as a pilot program with the Education Ministry in Ethiopia[^(29)](#c14.xhtml#ftn29).
*   Community groups such as **WADA** focus on blockchain education hubs in Ghana, and Cameroon and future plans for other countries in West and Central Africa.[^(30)](#c14.xhtml#ftn30)
*   A community of stake pool operators called Climate Neutral Cardano is committed to using 100% renewable energy.[^(31)](#c14.xhtml#ftn31)
*   UNHCR awarded the Cardano Foundation and Switzerland recognition for allowing 80% of staking rewards to go toward refugees in pressing need.[^(32)](#c14.xhtml#ftn32)
*   Sustainable Ada maintains a repository of social impact Cardano projects.[^(33)](#c14.xhtml#ftn33)
*   AdaFilms has a collection of short documentaries on real, impactful use cases using the Cardano blockchain.[^(34)](#c14.xhtml#ftn34)

# [Regulatory and Compliance Risks](#toc.xhtml#s370a)

The regulatory climate in the US has been particularly difficult and challenging for all blockchain companies located there. This is why most blockchain companies or foundations have headquarters outside the US in crypto-favorable jurisdictions such as Switzerland. Regulatory clarity has improved over the last few years and will continue to do so as legitimate use cases are realized and the benefits of blockchain are advocated.

Compliance risks, particularly KYC and AML regulations, are not always compatible with a pseudonymous, decentralized, permissionless blockchain. The Cardano blockchain is a toolbox with many tools that can address various functional and non-functional requirements, including KYC and AML if required. So, always be aware of your users’ regulatory environment and tailor your solution accordingly. Also, be aware that there may be reporting requirements or outright bans on holding cryptocurrency assets in certain jurisdictions.

# [Technology Adoption](#toc.xhtml#s371a)

Blockchain appears to be following a similar trajectory to other disruptive innovations such as cell phones, the Internet, and social media, as illustrated in *[Figure 14.2](#c14.xhtml#fig14_2).* The innovators are first in this space, pioneering and championing the first iterations of the technology. Then comes the early adopters who see the potential and evangelize the benefits. Next, the expectation is that the early majority will arrive and that this will usher in a new era with mass adoption.

![](OEBPS/images/Figure-14.2.jpg)

**Figure 14.2:** Technology Adoption Curve

Unfortunately, this does not happen and instead, the chasm occurs. The early interest and excitement fade and the technology is discarded by many as a passing fad. But the builders keep building during this phase, strong with conviction that this new technology has significant potential. At some point in the future, “*killer*” applications are created that realize the unique value proposition of this new technology. It fundamentally changes how society views solutions to previously unsolvable problems. At this point, the early majority arrives and mass adoption occurs at scale. By the late majority phase, the technology is no longer novel and is accepted as the new normal. Finally, there will be the laggards who will remain skeptical of the technology but will have no choice but to use it to stay connected with the rest of the world.

# [The Cardano Journey](#toc.xhtml#s372a)

The road to get here was not easy for the teams involved in building and deploying the Cardano blockchain. Delays, setbacks, resets, and pivots caused a lot of friction and frustration. This is not uncommon for new, complex, highly integrated systems. What made this and other cryptocurrency projects more challenging than most, is that it is built in public with many people having a direct financial stake in the outcome. Throughout it all, however, **IOG** (**IOHK**)[^(35)](#c14.xhtml#ftn35) and Charles Hoskinson[^(36)](#c14.xhtml#ftn36) provided regular updates on YouTube and blog posts. Constantly having to dispel the naysayers, respond to the critics, and reassure the community that progress was being made. It was truly amazing to be part of this journey, watching and participating in it in real-time, and looking forward to what comes next.

# [Conclusion](#toc.xhtml#s373a)

In this chapter, we reviewed the ethos of Cardano and why there is such an emphasis on the peer review process and formal methods. We looked closely at software industry standards and how the current quality mitigation approaches are unsuitable for blockchains. We looked at how semi-formal methods are used to link high-assurance software back to the formal specification. We also examined how cryptographic associations like **IACR** promote and advance cryptographic research through conferences and publications. Next, we looked at how Cardano has significant potential for social good with real-world examples. We discussed the regulatory and compliance risks when creating a blockchain-based application. We also reviewed the five stages of technology adoption and how it applies to blockchain. Finally, we discussed the road to get here as part of the Cardano journey.

# [Points to Remember](#toc.xhtml#s374a)

*   The Cardano ethos is openness and transparency.
*   The peer review process is important to Cardano because it aligns with the Cardano ethos and best practices for high-assurance software.
*   Haskell was chosen as the language to write the Cardano blockchain because of its similarity to the mathematical proofs of correctness.
*   Blockchain empowers and gives agency to the edges of the network.
*   Blockchains (and projects) focusing on the service others will typically succeed in the long run and the market will determine price, value, and product fit.
*   The current software industry standards for quality are unsuitable for high-assurance software.
*   A true decentralized and permissionless blockchain has no central authority to shut down, restart, or patch a network.
*   A blockchain software bug can result in millions of dollars lost or stolen.
*   A semi-formal method is an approach used by **IOG** (**IOHK**), in which a specification executable generates outputs that can be compared to implementation executable outputs.
*   The International Association of Cryptographic Research (**IACR**) is a non-profit organization that advances cryptography.
*   Cardano’s mission to bank the unbanked goes back to the earliest days of Cardano.
*   The potential for social good using Cardano is significant, and many real-world examples exist.
*   Regulatory risks need to be monitored and assessed for each jurisdiction that is applicable to an application.
*   Understanding **KYC** and **AML** regulations for a system or application’s users is important for a project’s success.
*   The five stages of technology adoption include the innovators, early adopters, early majority, late majority, and the laggards.
*   The chasm typically occurs between the early adopters and the early majority, a period when expected growth and user adoption do not occur at the expected pace.
*   The Cardano journey has been long and has faced many challenges, which are not uncommon when creating a new, complex, and highly integrated platform.

# [Multiple Choice Questions](#toc.xhtml#s375a)

1.  What is the ethos of Cardano? 
    1.  Creating value
    2.  Banking the unbanked
    3.  Openness and transparency
    4.  All of the above
2.  What are the benefits of the peer review process? 
    1.  Facilitates the sharing and collaboration of ideas
    2.  Provides unbiased feedback and review of published papers
    3.  Advances the field through scientific study and research
    4.  All of the above
3.  What statement is false? 
    1.  Software industry standards are suitable for high-assurance software
    2.  Blockchain gives agency to the edges of the network
    3.  IACR is a non-profit organization
    4.  Cryptocurrency speculation first started with ICOs
4.  What are the five stages of technology adoption? 
    1.  Innovators, Early Adopters, Early Majority, Late Majority, Laggards
    2.  Innovators, Early Majority, Later Majority, Late Adopters, Laggards
    3.  Early Adopters, Early Innovators, Early Majority, Late Majority, Laggards
    4.  Innovators, Early Adopters, Early Majority, Middle Majority, Laggards
5.  Why is it difficult to build a blockchain? 
    1.  A cryptocurrency token will include speculation and financial stakeholders
    2.  Building is done in public where anyone can see the last open-source code
    3.  It is a highly complex, secure, and integrated system
    4.  All of the above

# [Answers](#toc.xhtml#s376a)

1.  c
2.  d
3.  a
4.  a
5.  d

# [Questions](#toc.xhtml#s377a)

1.  Why is the peer review process not typically done in other blockchains?
2.  What other languages could have Cardano been written in and what are the pros and cons of each?
3.  Why are 3 billion people in the world unbanked?
4.  What are the difficulties of using formal methods in software development?
5.  Can agile software development methodologies and formal methods coexist?
6.  Why does the chasm appear in the five stages of technology adoption?

# [Key Terms](#toc.xhtml#s378a)

*   **AML:** Anti-Money Laundering
*   **DID:** Decentralized Identifier
*   **ESG:** Environmental, Social and Governance
*   **IACR:** International Association of Cryptographic Research
*   **ICO:** Initial Coin Offering
*   **IOG:** Input Output Global
*   **IOHK:** Input Output Hong Kong
*   **KYC:** Know Your Customer
*   **UNHCR:** United National High Commissioner for Refugees
*   **WADA:** Africa, Diaspora and Beyond

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#c14.xhtml#ftn1a) [https://roadmap.cardano.org/en/](https://roadmap.cardano.org/en/)

[²](#c14.xhtml#ftn2a) [https://iacr.org/](https://iacr.org/)

[³](#c14.xhtml#ftn3a) Aggelos Kiayias, "Why Peer Review?"

[⁴](#c14.xhtml#ftn4a) [https://roadmap.cardano.org/en/](https://roadmap.cardano.org/en/)

[⁵](#c14.xhtml#ftn5a) [https://en.wikipedia.org/wiki/Formal\_methods](https://en.wikipedia.org/wiki/Formal_methods)

[⁶](#c14.xhtml#ftn6a) David Marquet, "How Great Leaders Serve Others: David Marquet at TEDxScottAFB"

[⁷](#c14.xhtml#ftn7a) Joi Ito, "Highlight: Joi Ito on ICOs at Scaling Bitcoin"

[⁸](#c14.xhtml#ftn8a) Duncan Coutts, "IOHK PlutusFest 2018 | Duncan Coutts Presentation & Rebecca Valentine Closing Remarks"

[⁹](#c14.xhtml#ftn9a) Duncan Coutts, "IOHK PlutusFest 2018 | Duncan Coutts Presentation & Rebecca Valentine Closing Remarks"

[^(10)](#c14.xhtml#ftn10a) Philipp Kant et al., "Flexible Formality Practical Experience with Agile Formal Methods", 104

[^(11)](#c14.xhtml#ftn11a) Andre Knispel, et. all., "Formal specification of the Cardano blockchain ledger, mechanized in Agda"

[^(12)](#c14.xhtml#ftn12a) [https://github.com/IntersectMBO/formal-ledger-specifications](https://github.com/IntersectMBO/formal-ledger-specifications)

[^(13)](#c14.xhtml#ftn13a) [https://iacr.org/](https://iacr.org/)

[^(14)](#c14.xhtml#ftn14a) [https://iacr.org/meetings/](https://iacr.org/meetings/)

[^(15)](#c14.xhtml#ftn15a) [https://iacr.org/jofc/](https://iacr.org/jofc/)

[^(16)](#c14.xhtml#ftn16a) Charles Hoskinson, "The future will be decentralized | Charles Hoskinson | TEDxBermuda"

[^(17)](#c14.xhtml#ftn17a) [https://cardano.org/discover-cardano#purpose](https://cardano.org/discover-cardano#purpose)

[^(18)](#c14.xhtml#ftn18a) Alex Hamilton, "Connecting the unconnected, banking the unbanked"

[^(19)](#c14.xhtml#ftn19a) Input Output, "How Do You Explain The Mission Of Cardano?"

[^(20)](#c14.xhtml#ftn20a) [https://worldmobile.io/en](https://worldmobile.io/en)

[^(21)](#c14.xhtml#ftn21a) [https://worldmobiletoken.com/WhitePaper.pdf](https://worldmobiletoken.com/WhitePaper.pdf), p2

[^(22)](#c14.xhtml#ftn22a) [https://worldmobiletoken.com/WhitePaper.pdf](https://worldmobiletoken.com/WhitePaper.pdf), p3

[^(23)](#c14.xhtml#ftn23a) [https://worldmobile.io/en](https://worldmobile.io/en)

[^(24)](#c14.xhtml#ftn24a) [https://empowa.io/our-mission/](https://empowa.io/our-mission/)

[^(25)](#c14.xhtml#ftn25a) mpowa Whitepaper, "Empowering African Communities"

[^(26)](#c14.xhtml#ftn26a) [https://empowa.io/](https://empowa.io/)

[^(27)](#c14.xhtml#ftn27a) [https://www.greencryptoresearch.com/blockchains](https://www.greencryptoresearch.com/blockchains)

[^(28)](#c14.xhtml#ftn28a) [https://www.greencryptoresearch.com/blockchains/cardano-(ada)](https://www.greencryptoresearch.com/blockchains/cardano-\(ada\))

[^(29)](#c14.xhtml#ftn29a) Olga Hryniuk, "Atala PRISM: pioneering digital identity with decentralized solutions"

[^(30)](#c14.xhtml#ftn30a) [https://www.wada.org/](https://www.wada.org/)

[^(31)](#c14.xhtml#ftn31a) [https://climateneutralcardano.org/](https://climateneutralcardano.org/)

[^(32)](#c14.xhtml#ftn32a) Alex Maaza, "Cardano Foundation and Switzerland for UNHCR Recognized for Philanthropy Innovation"

[^(33)](#c14.xhtml#ftn33a) [https://sustainableada.com/](https://sustainableada.com/)

[^(34)](#c14.xhtml#ftn34a) [https://www.adafilms.art/](https://www.adafilms.art/)

[^(35)](#c14.xhtml#ftn35a) [https://www.youtube.com/c/iohkio](https://www.youtube.com/c/iohkio)

[^(36)](#c14.xhtml#ftn36a) [https://www.youtube.com/user/charleshoskinson](https://www.youtube.com/user/charleshoskinson)

# [Bibliography](#toc.xhtml#bib)

Alden, L., “Broken Money.”

Timestamp Press, 2023

Badertscher, C., Gazi1 C.,Kiayias A.,Russell A. and Zikas V., “Ouroboros Chronos: Permissionless Clock Synchronization via Proof-of-Stake”

IACR, May 15, 2019

Available online via: [https://eprint.iacr.org/2018/1132.pdf](https://eprint.iacr.org/2018/1132.pdf)

Badertscher, C.,Gazi, P., Kiayias, A., Russell, A. and Zikas V, “Ouroboros Genesis: Composable Proof-of-Stake Blockchains with Dynamic Availability”

IACR, February 22, 2019

Available online via: [https://eprint.iacr.org/2018/378.pdf](https://eprint.iacr.org/2018/378.pdf)

Bailly, A., “Time handling on Cardano, part 1. About Ouroboros and the importance of determinism”

IOHK, December 6, 2022

Available online via: [https://iohk.io/en/blog/posts/2022/12/07/time-handling-on-cardano-part-1-about-ouroboros-and-the-importance-of-determinism/](https://iohk.io/en/blog/posts/2022/12/07/time-handling-on-cardano-part-1-about-ouroboros-and-the-importance-of-determinism/)

Bano S., Sonnino A., Al-Bassam M.,Azouvi S.,McCorry P.,Meiklejohn S. and Danezis1 D. “SoK: Consensus in the Age of Blockchains”

November 14, 2017

Available online via: [https://arxiv.org/pdf/1711.03936.pdf](https://arxiv.org/pdf/1711.03936.pdf)

Britannica, Encyclopaedia of, “cipher”

Encyclopaedia of Britannica, Jan 03, 2008

Available online via: [https://www.britannica.com/topic/cipher](https://www.britannica.com/topic/cipher)

Bernstein, D.J., Duif, N., Lange, T. et al. “High-speed high-security signatures.”

J Cryptogr Eng 2, 77–89 (2012).

Available online via: [https://doi.org/10.1007/s13389-012-0027-1](https://doi.org/10.1007/s13389-012-0027-1)

Brunjes, L. and Betrin, M. “Building UTxO optimized Dapps”

Genius Yield, December 8, 2022

Available online via: [https://www.youtube.com/watch?v=MYMha1C0o1g](https://www.youtube.com/watch?v=MYMha1C0o1g)

Burgess, N., “Calling trailblazers to Midnight”

IOHK, October 4, 2023

Available online via: [https://iohk.io/en/blog/posts/2023/10/05/calling-trailblazers-to-midnight/](https://iohk.io/en/blog/posts/2023/10/05/calling-trailblazers-to-midnight/)

Buterin, V., “Ethereum: A Next-Generation Smart Contract and Decentralized Application Platform”

Ethereum.org, 2014

Available online via: [https://ethereum.org/content/whitepaper/whitepaper-pdf/Ethereum\_Whitepaper\_-\_Buterin\_2014.pdf](https://ethereum.org/content/whitepaper/whitepaper-pdf/Ethereum_Whitepaper_-_Buterin_2014.pdf)

Cardanians.io, “Understanding Input Endorsers”

CExplorer.io, June 10, 2023

Available online via: [https://cexplorer.io/article/understanding-input-endorsers](https://cexplorer.io/article/understanding-input-endorsers)

Cardanians.io, “There is 1.23B ADA in Cardano’s treasury”

CExporer.io, November, 11, 2023

Available online via: [https://cexplorer.io/article/there-is-1-23b-ada-in-cardano-s-treasury](https://cexplorer.io/article/there-is-1-23b-ada-in-cardano-s-treasury)

CertiK, “The Blockchain Trilemma: Decentralized, Scalable, and Secure?”

Medium, October 4, 2019

Available online via: [https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3](https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3)

Chaidos, P. and Kiaias, A., “Mithril: Stake-based Threshold Multisignatures”

IACR, May, 2021

Available online via: [https://eprint.iacr.org/2021/916.pdf](https://eprint.iacr.org/2021/916.pdf)

Chainalysis, “2022 Biggest Year Ever For Crypto Hacking with $3.8 Billion Stolen, Primarily from DeFi Protocols and by North Korea-linked Attackers”

Chainalysis.com, February 1, 2023

Available online via: [https://www.chainalysis.com/blog/2022-biggest-year-ever-for-crypto-hacking/](https://www.chainalysis.com/blog/2022-biggest-year-ever-for-crypto-hacking/)

Chapman, J.,Kireev R.,Nester C.,Wadler, P., “System F in Agda, for fun and profit”

Mathematics of Program Construction: 13th International Conference, MPC 2019, Porto, Portugal, October 7–9, 2019, Proceedings

10.1007/978-3-030-33636-3\_10

Available online via: [https://iohk.io/en/research/library/papers/system-f-in-agda-for-fun-and-profit/](https://iohk.io/en/research/library/papers/system-f-in-agda-for-fun-and-profit/)

Coutts, D., “IOHK PlutusFest 2018 | Duncan Coutts Presentation & Rebecca Valentine Closing Remarks”

Input Output, January 30, 2019

Available online via: [https://www.youtube.com/watch?v=wW1CI9zt1tg](https://www.youtube.com/watch?v=wW1CI9zt1tg)

Coutts, D., Panagiotakos, G. and Fitzi, M., “Ouroboros Leios: design goals and concepts”

IOHK, October, 2022

Available online via: [https://iohk.io/en/research/library/papers/ouroboros-leios-design-goals-and-concepts/](https://iohk.io/en/research/library/papers/ouroboros-leios-design-goals-and-concepts/)

Crypto Carlos, “Node course | Creating a stake pool, the setup”

IOG Academy, March 21, 2023

Available online via: [https://www.youtube.com/watch?v=6AQaPdmxnfo](https://www.youtube.com/watch?v=6AQaPdmxnfo)

Crypto Carlos., “Ourobors protocol. The heart of Cardano”

Crypto Carlos, May 21, 2019

Available online via: [https://www.youtube.com/watch?v=U92Ks8rucDQ](https://www.youtube.com/watch?v=U92Ks8rucDQ)

Cryptopedia, “The Blockchain Trilemma: Fast, Secure, and Scalable Networks”

Gemini.com, June 28, 2022,

Available online via: [https://www.gemini.com/cryptopedia/blockchain-trilemma-decentralization-scalability-definition](https://www.gemini.com/cryptopedia/blockchain-trilemma-decentralization-scalability-definition)

Dai, W., “b-money”

Weidia.com, February 19, 1999

Available online via: [http://www.weidai.com/bmoney.txt](http://www.weidai.com/bmoney.txt)

David B., Gazi P., Kiayias A. and Russell A., “Ouroboros Praos: An adaptively-secure, semi-synchronous proof-of-stake blockchain”

IACR, April 27, 2023

Available online via: [https://eprint.iacr.org/2017/573.pdf](https://eprint.iacr.org/2017/573.pdf)

Empowa Whitepaper, “Empowering African Communities”

Empowa.io, 2021,

Available online via: [https://drive.google.com/filed/1ei\_0eQFCK5wKGMQgVcyNlTQYUQ4ky-xT/edit](https://drive.google.com/filed/1ei_0eQFCK5wKGMQgVcyNlTQYUQ4ky-xT/edit)

Finney, H. “RPOW - Reusable Proofs of Work”

Satoshi Nakamoto Institute, August 15, 2004

Available online via: [https://nakamotoinstitute.org/rpow/](https://nakamotoinstitute.org/rpow/)

Kiayias, A., “Why Peer Review?”

Input Output, June 22, 2018

Available online via: [https://www.youtube.com/watch?v=MV8ANlktGoI](https://www.youtube.com/watch?v=MV8ANlktGoI)

Knispel, A., Melkonian, O., Chapman, J., Hill, A., Jääger, J., DeMeo, W., Norell, U., “Formal specification of the Cardano blockchain ledger, mechanized in Agda”

Input Output, March 2024

Available online via: [https://iohk.io/en/research/library/papers/formal-specification-of-the-cardano-blockchain-ledger-mechanized-in-agda/](https://iohk.io/en/research/library/papers/formal-specification-of-the-cardano-blockchain-ledger-mechanized-in-agda/)

Gauba A., Finality in Blockchain Consensus

Medium, Aug 30, 2018

Available online: [https://medium.com/mechanism-labs/finality-in-blockchain-consensus-d1f83c120a9a](https://medium.com/mechanism-labs/finality-in-blockchain-consensus-d1f83c120a9a)

Gaži, P., “Presenting Ouroboros at MIT”

Input Output, March 13, 2018

Available online via: [https://www.youtube.com/watch?v=PoNaw-Mtxgo](https://www.youtube.com/watch?v=PoNaw-Mtxgo)

Goldwasser, S. and Mihir, B., “Lecture Notes on Cryptography”

MIT, July 2008

Available online via: [https://cseweb.ucsd.edu/~mihir/papers/gb.pdf](https://cseweb.ucsd.edu/~mihir/papers/gb.pdf)

Haber, S. and Stornetta, W. S., “How To Time-Stamp a Digital Document.”

Journal of Cryptology, 1991

Available online via: [https://link.springer.com/article/10.1007/BF00196791](https://link.springer.com/article/10.1007/BF00196791)

Hamilton, A., “Connecting the unconnected, banking the unbanked”

IOHK, August 10, 2021

Available online via: [https://iohk.io/en/blog/posts/2021/08/11/connecting-the-unconnected-banking-the-unbanked/](https://iohk.io/en/blog/posts/2021/08/11/connecting-the-unconnected-banking-the-unbanked/)

Hirniak, J., “Axo Protocol Whitepaper: The New era of trading”

axo.trade, October 21, 2021

Available online via: [https://www.axo.trade/whitepaper.pdf](https://www.axo.trade/whitepaper.pdf)

Hoskinson, C. “Cardano whiteboard; overview with Charles Hoskinson”

Input Output, October 26, 2017

Available online via: [https://www.youtube.com/watch?v=Ja9D0kpksxw](https://www.youtube.com/watch?v=Ja9D0kpksxw)

Hoskinson, C., “The future will be decentralized | Charles Hoskinson | TEDxBermuda”

TEDx Talks, December 4, 2014

Available online via: [https://www.youtube.com/watch?v=97ufCT6lQcY](https://www.youtube.com/watch?v=97ufCT6lQcY)

Hryniuk, O., “Atala PRISM: pioneering digital identity with decentralized solutions”

IOHK, May 10, 2023

Available online via: [https://iohk.io/en/blog/posts/2023/05/11/atala-prism-pioneering-digital-identity-with-decentralized-solutions/](https://iohk.io/en/blog/posts/2023/05/11/atala-prism-pioneering-digital-identity-with-decentralized-solutions/)

Hryniuk, O., “How Mithril facilitates strong security settings”

IOHK, August 22, 2023

Available online via: [https://iohk.io/en/blog/posts/2023/08/23/how-mithril-facilitates-strong-security-settings/](https://iohk.io/en/blog/posts/2023/08/23/how-mithril-facilitates-strong-security-settings/)

Hryniuk O., “From Classic to Chronos: the implementations of Ouroboros explained”

IOHK, June 2, 2022

Available online vai: [https://iohk.io/en/blog/posts/2022/06/03/from-classic-to-chronos-the-implementations-of-ouroboros-explained/](https://iohk.io/en/blog/posts/2022/06/03/from-classic-to-chronos-the-implementations-of-ouroboros-explained/)

Hughes, J., “Testing smart contracts with QuickCheck by John Hughes”

Func Prog Sweden, May 27, 2021

Available online via: [https://www.youtube.com/watch?v=V9\_14jjJiuQ](https://www.youtube.com/watch?v=V9_14jjJiuQ)

Input Output, “How Do You Explain The Mission Of Cardano?”

Input Output, January 29, 2021

Available online via: [https://www.youtube.com/watch?v=l\_Nv0-PVrnM](https://www.youtube.com/watch?v=l_Nv0-PVrnM)

Ito, J., “Highlight: Joi Ito on ICOs at Scaling Bitcoin”

Seoul Bitcoin, June 15, 2018

Available online via: [https://www.youtube.com/watch?v=-whIh7n4Yqc](https://www.youtube.com/watch?v=-whIh7n4Yqc)

Kant, P. et al., “Flexible Formality Practical Experience with Agile Formal Methods.”

In: Byrski, A., Hughes, J. (eds) Trends in Functional Programming. TFP 2020. Lecture Notes in Computer Science(), vol 12222. Springer, Cham.

Available online via: [https://doi.org/10.1007/978-3-030-57761-2\_5](https://doi.org/10.1007/978-3-030-57761-2_5)

Kerber, T., Kohlweiss†, M., Kiayias, A. and Zikas V. “Ouroboros Crypsinous: Privacy-Preserving Proof-of-Stake”

IACR, May 15, 2019

Available online via: [https://eprint.iacr.org/2018/1132.pdf](https://eprint.iacr.org/2018/1132.pdf)

Khovratovich, D. and Law, J., “BIP32-Ed25519: Hierarchical Deterministic Keys over a Non-linear Keyspace,”

2017 IEEE European Symposium on Security and Privacy Workshops (EuroS&PW), Paris, France, 2017, pp. 27-31, doi: 10.1109/EuroSPW.2017.47. keywords: {Public key;Bitcoin;Proposals;Privacy;Standards;Encoding},

Available online via: [https://input-output-hk.github.io/adrestia/static/Ed25519\_BIP.pdf](https://input-output-hk.github.io/adrestia/static/Ed25519_BIP.pdf)

Kiayias, A. and Russell A., “Ouroboros-BFT:A Simple Byzantine Fault Tolerant Consensus Protocol”

IACR, November 26, 2018

Available online via: [https://eprint.iacr.org/2018/1049.pdf](https://eprint.iacr.org/2018/1049.pdf)

Kiayias, A., Russell A., David B. and Oliynyko R., “Ouroboros: A Provably Secure Proof-of-Stake Blockchain Protocol”

IACR, July 20, 2019

Available online via: [https://eprint.iacr.org/2016/889.pdf](https://eprint.iacr.org/2016/889.pdf)

Knispel, A., Vinogradova, P., “Formal Specification of the Cardano Ledger with Plutus Integration”,

IOHK, February 28th, 2021

Available online via: [https://github.com/input-output-hk/cardano-ledger/releases/latest/download/alonzo-ledger.pdf](https://github.com/input-output-hk/cardano-ledger/releases/latest/download/alonzo-ledger.pdf)

Lamport, L.; Shostak, R.; Pease, M., “The Byzantine Generals Problem.”

ACM Transactions on Programming Languages and Systems. 4 (3): 382–401. July 1982.

Available online via: [https://lamport.azurewebsites.net/pubs/byz.pdf](https://lamport.azurewebsites.net/pubs/byz.pdf)

Lebec, G., “Lambda Calculus - Fundamentals of Lambda Calculus & Functional Programming in JavaScript”

Fullstack Academy, August 25, 2017

Available online via: [https://www.youtube.com/watch?v=3VQ382QG-y4](https://www.youtube.com/watch?v=3VQ382QG-y4)

Lebec, G., “The Magic of Generative Testing: Fast-Check in JavaScript”

Fullstack Academy, July 2, 2019

Available online via: [https://www.youtube.com/watch?v=a2J\_FSkxWKo](https://www.youtube.com/watch?v=a2J_FSkxWKo)

LLFOURN, “Introduction To Ouroboros”

Medium, Feb 17, 2018

Available online via: [https://medium.com/unraveling-the-ouroboros/introduction-to-ouroboros-1c2324912193](https://medium.com/unraveling-the-ouroboros/introduction-to-ouroboros-1c2324912193)

Maaza, A., “Cardano Foundation and Switzerland for UNHCR Recognized for Philanthropy Innovation”

Cardano Foundation, February 6, 2024

Available online via: [https://cardanofoundation.org/blog/cardano-foundation-and-switzerland-for-unhcr-recognized-for-philanthropy-innovation/](https://cardanofoundation.org/blog/cardano-foundation-and-switzerland-for-unhcr-recognized-for-philanthropy-innovation/)

Marquet, D., “How Great Leaders Serve Others: David Marquet at TEDxScottAFB”

TEDx Talks, June 21, 2012

Available online via: [https://www.youtube.com/watch?v=DLRH5J\_93LQ](https://www.youtube.com/watch?v=DLRH5J_93LQ)

Mazieres, D. and Shasha, D., “Building secure file systems out of Byzantine storage.”

NYU Department of Computer Science, 2006

Available online via: [https://cs.nyu.edu/~shasha/papers/mazpodc.pdf](https://cs.nyu.edu/~shasha/papers/mazpodc.pdf)

Menezes, A., Oorschot, P. van and Vanstone, S. “Handbook of Applied Cryptography”

CRC Press, 1996

Available online via: [https://cacr.uwaterloo.ca/hac/about/chap8.pdf](https://cacr.uwaterloo.ca/hac/about/chap8.pdf)

Nakamoto, S., “Bitcoin: A Peer-to-Peer Electronic Cash System”

Bitcoin.org, October 31st, 2008

Available online via: [https://bitcoin.org/bitcoin.pdf](https://bitcoin.org/bitcoin.pdf)

Pittalia, P. P., “A comparative study of hash algorithms in cryptography”

Int. J. Comput. Sci. Mobile Comput., vol. 8, no. 6, pp. 147-152, 2019

Available online via: [https://ijcsmc.com/docs/papers/June2019/V8I6201928.pdf](https://ijcsmc.com/docs/papers/June2019/V8I6201928.pdf)

Plutus Core Team, DRAFT “Formal Specification of the Plutus Core Language”

IOHK, September 1st, 2023

Available online: [https://ci.iog.io/build/1230997/download/1/plutus-core-specification.pdf](https://ci.iog.io/build/1230997/download/1/plutus-core-specification.pdf)

Raynaud, J., “Light, fast, efficient, and secure - Mithril”

Input Output, December 7, 2022

Available online via: [https://www.youtube.com/watch?v=VyxsqwNWZt4](https://www.youtube.com/watch?v=VyxsqwNWZt4)

Richmond, T., “Project Catalyst - A virtuous cycle of Cardano ecosystem development”

IOHK, May 9, 2022

Available online via: [https://iohk.io/en/blog/posts/2022/05/10/project-catalyst-a-virtuous-cycle-of-cardano-ecosystem-development-investing-in-great-ideas-to-make-positive-real-world-changes/](https://iohk.io/en/blog/posts/2022/05/10/project-catalyst-a-virtuous-cycle-of-cardano-ecosystem-development-investing-in-great-ideas-to-make-positive-real-world-changes/)

Sheehan, R., “State of Cardano Q4 2023”

Messari.io, Feb 14, 2024

Available online via: [https://messari.io/report/state-of-cardano-q4-2023](https://messari.io/report/state-of-cardano-q4-2023)

Simmons, G. J., “History of cryptography”

Encyclopedia Britannica, Apr 15, 2004

Available online via: [https://www.britannica.com/topic/cryptology/The-Data-Encryption-Standard-and-the-Advanced-Encryption-Standard](https://www.britannica.com/topic/cryptology/The-Data-Encryption-Standard-and-the-Advanced-Encryption-Standard)

Upadhyay, D., Gaikwad, N., Zaman, M. and Sampalli, S., “Investigating the Avalanche Effect of Various Cryptographically Secure Hash Functions and Hash-Based Applications,”

IEEE Access, vol. 10, pp. 112472-112486, 2022, doi: 10.1109/ACCESS.2022.3215778.

Available online via: [https://ieeexplore.ieee.org/document/9923931](https://ieeexplore.ieee.org/document/9923931)

Wadler, P., “Functional smart contracts on Cardano”

Input Output, July 21, 2020

Available online via: [https://www.youtube.com/watch?v=MpWeg6Fg0t8](https://www.youtube.com/watch?v=MpWeg6Fg0t8)

Ward, M., “Partner chains are coming to Cardano”

IOHK, November 2, 2023

Available online via: [https://iohk.io/en/blog/posts/2023/11/03/partner-chains-are-coming-to-cardano/](https://iohk.io/en/blog/posts/2023/11/03/partner-chains-are-coming-to-cardano/)

Zharun, T., “Wyoming LLC as a DAO Legal Wrapper: What You Need to Know”

Legal Nodes, January 26, 2024

Available online via: [https://legalnodes.com/article/wyoming-dao-llc](https://legalnodes.com/article/wyoming-dao-llc)

# [Index](#toc.xhtml#ind)

A

Absolute Finality (PBFT) [23](#c02.xhtml#page23)

address [32](#c03.xhtml#page32)

address, types

base address [32](#c03.xhtml#page32), [33](#c03.xhtml#page33)

enterprise address [33](#c03.xhtml#page33)

reward address [33](#c03.xhtml#page33), [34](#c03.xhtml#page34)

Aiken [92](#c06.xhtml#page92), [93](#c06.xhtml#page93)

Aiken, libraries

lucid cancel, function [95](#c06.xhtml#page95)

lucid off-chain, unlocking [94](#c06.xhtml#page94), [95](#c06.xhtml#page95)

on-chain, validating [93](#c06.xhtml#page93), [94](#c06.xhtml#page94)

anti-pattern, approaches

batchers, utilizing [155](#c09.xhtml#page155)

liquidity, pools [154](#c09.xhtml#page154)

AssetClass [107](#c07.xhtml#page107)

B

back-end, components

Blockfrost setup [204](#c10.xhtml#page204)

public key, optimizing [205](#c10.xhtml#page205)

Redis DB [202](#c10.xhtml#page202)

Beacon Token [152](#c09.xhtml#page152)

Bitcoin Whitepaper [3](#c01.xhtml#page3), [4](#c01.xhtml#page4)

Blockchain, Benefits [223](#c10.xhtml#page223), [224](#c10.xhtml#page224)

Blockchain Trilemma

about [7](#c01.xhtml#page7)

approaches [8](#c01.xhtml#page8)

decentralizing [8](#c01.xhtml#page8)

scalability [8](#c01.xhtml#page8)

security [8](#c01.xhtml#page8)

Blockchain, use cases

DAO [13](#c01.xhtml#page13)

DEX [13](#c01.xhtml#page13)

financial, products [13](#c01.xhtml#page13)

insurance [13](#c01.xhtml#page13)

market, capital [13](#c01.xhtml#page13)

marketplaces [13](#c01.xhtml#page13)

media, entertaining [13](#c01.xhtml#page13)

reward [13](#c01.xhtml#page13)

storage, decentralizing [13](#c01.xhtml#page13)

system, identity [13](#c01.xhtml#page13)

tokenization [13](#c01.xhtml#page13)

Blockfrost

reference link [125](#c08.xhtml#page125)

builtin [49](#c04.xhtml#page49)

Byzantine Generals Problem (BGP) [2](#c01.xhtml#page2)

C

Cancel.tsx [95](#c06.xhtml#page95)

Cardano

GitHub repositories, preventing [267](#c13.xhtml#page267)

history [286](#c14.xhtml#page286)

resources, learning [274](#c13.xhtml#page274), [275](#c13.xhtml#page275)

state, utilizing [266](#c13.xhtml#page266), [267](#c13.xhtml#page267)

Cardano Blockchain

about [127](#c08.xhtml#page127)

challenge [128](#c08.xhtml#page128)

Kupo [136](#c08.xhtml#page136)\-[138](#c08.xhtml#page138)

node, component [128](#c08.xhtml#page128)\-[130](#c08.xhtml#page130)

Ogmios [133](#c08.xhtml#page133)\-[135](#c08.xhtml#page135)

setup [138](#c08.xhtml#page138)

Cardano Blockchain, aspects

endorsers, containing [247](#c11.xhtml#page247), [248](#c11.xhtml#page248)

Hydra, analyzing [246](#c11.xhtml#page246), [247](#c11.xhtml#page247)

Mithril [247](#c11.xhtml#page247)

scripts, referencing [244](#c11.xhtml#page244)

smart contract, preventing [246](#c11.xhtml#page246)

UTXO Contention, avoiding [244](#c11.xhtml#page244), [245](#c11.xhtml#page245)

cardano-cli [130](#c08.xhtml#page130)

Cardano Improvement Process (CIP)

about [268](#c13.xhtml#page268)

concepts [268](#c13.xhtml#page268), [269](#c13.xhtml#page269)

states [268](#c13.xhtml#page268)

Cardano, industries

Crypto research, optimizing [284](#c14.xhtml#page284)

Empowa [284](#c14.xhtml#page284)

social project, utilizing [284](#c14.xhtml#page284), [285](#c14.xhtml#page285)

World Mobile Tokens (WMT) [284](#c14.xhtml#page284)

Cardano Node [259](#c12.xhtml#page259), [260](#c12.xhtml#page260)

Cardano, risks [285](#c14.xhtml#page285)

Cardano Roadmap [11](#c01.xhtml#page11)

Cardano Testnet

reference link [63](#c05.xhtml#page63)

chain sequence diagram, concepts

application, executing [170](#c09.xhtml#page170)

Becon, viewing [167](#c09.xhtml#page167), [168](#c09.xhtml#page168)

swap, closing [171](#c09.xhtml#page171)

swap, opening [166](#c09.xhtml#page166)

swap, updating [169](#c09.xhtml#page169)

ticket, printing [171](#c09.xhtml#page171)

tickets, minting [165](#c09.xhtml#page165)

transaction, verifying [172](#c09.xhtml#page172)

wallet, connecting [166](#c09.xhtml#page166)

Charles Hoskinson

concepts [6](#c01.xhtml#page6)

interoperability [6](#c01.xhtml#page6), [7](#c01.xhtml#page7)

scalability [6](#c01.xhtml#page6)

sustainability [7](#c01.xhtml#page7)

CIP-1694 [269](#c13.xhtml#page269)

CIP-1694, key role

Constitutional Committee (CC) [270](#c13.xhtml#page270)

Delegated Representatives (DReps) [270](#c13.xhtml#page270)

Stake Pool Operators (SPOs) [270](#c13.xhtml#page270)

CIPs, best practices

CIP-0003 Key, generating [155](#c09.xhtml#page155)

CIP-0030 Web, bridging [156](#c09.xhtml#page156)

CIP-0032 Inline, datums [156](#c09.xhtml#page156)

CIP-0040 Collateral, expliciting [156](#c09.xhtml#page156)

CIP-0068 Metadata [156](#c09.xhtml#page156), [157](#c09.xhtml#page157)

Coin Selection

about [105](#c07.xhtml#page105)

process, utilizing [106](#c07.xhtml#page106)

Collateral [56](#c04.xhtml#page56)

Concise Binary Representation (CBOR)

about [50](#c04.xhtml#page50)

Datum, configuring [54](#c04.xhtml#page54)

Plutus, scripting [53](#c04.xhtml#page53)

Redeemer, utilizing [53](#c04.xhtml#page53)

transaction, analyzing [51](#c04.xhtml#page51), [52](#c04.xhtml#page52)

Cryptography

about [18](#c02.xhtml#page18)

Hashes [19](#c02.xhtml#page19)

Public Key Encryption [18](#c02.xhtml#page18)

D

Dandelion [127](#c08.xhtml#page127)

Datums [40](#c03.xhtml#page40)

Demeter.run [60](#c05.xhtml#page60), [67](#c05.xhtml#page67)

Design Patterns

about [151](#c09.xhtml#page151)

Beacon Token [152](#c09.xhtml#page152)

order book [152](#c09.xhtml#page152), [153](#c09.xhtml#page153)

thread token [151](#c09.xhtml#page151)

Digital Signatures [19](#c02.xhtml#page19), [20](#c02.xhtml#page20)

Distributed Ledger Technology

about [2](#c01.xhtml#page2)

Byzantine Generals Problem (BGP) [2](#c01.xhtml#page2), [3](#c01.xhtml#page3)

concept [3](#c01.xhtml#page3)

dynamicQuery() [183](#c10.xhtml#page183)

E

Ethereum Whitepaper [4](#c01.xhtml#page4), [5](#c01.xhtml#page5)

EUTXO Design Patterns

architecture, utilizing [158](#c09.xhtml#page158)

chain sequence diagram [165](#c09.xhtml#page165)

state machine diagram [158](#c09.xhtml#page158)

Execution budget errors [256](#c12.xhtml#page256)\-[258](#c12.xhtml#page258)

F

Front-end UI, components

event, viewing [185](#c10.xhtml#page185)

header/footer [181](#c10.xhtml#page181)

swap card, containing [184](#c10.xhtml#page184)

swap, viewing [182](#c10.xhtml#page182), [183](#c10.xhtml#page183)

tickets, printing [185](#c10.xhtml#page185), [186](#c10.xhtml#page186)

transaction, building [187](#c10.xhtml#page187)\-[189](#c10.xhtml#page189)

wallet, connecting [181](#c10.xhtml#page181), [182](#c10.xhtml#page182)

H

Hashes [19](#c02.xhtml#page19)

Helios

about [70](#c05.xhtml#page70)

GitHub, initializing [71](#c05.xhtml#page71)

UTXO, locking [72](#c05.xhtml#page72)

J

JavaScript Application

common folder, analyzing [179](#c10.xhtml#page179)

components [179](#c10.xhtml#page179)

init folder, optimizing [179](#c10.xhtml#page179)

lib, containing [179](#c10.xhtml#page179)

models, preventing [179](#c10.xhtml#page179)

Pages/API, utilizing [179](#c10.xhtml#page179)

public/contracts [180](#c10.xhtml#page180)

schema, analyzing [180](#c10.xhtml#page180)

wallet, configuring [179](#c10.xhtml#page179)

K

Koios [127](#c08.xhtml#page127)

Kupo [136](#c08.xhtml#page136)\-[138](#c08.xhtml#page138)

L

lam function [49](#c04.xhtml#page49)

Local Devnet

about [138](#c08.xhtml#page138), [139](#c08.xhtml#page139)

docker, installing [139](#c08.xhtml#page139)\-[143](#c08.xhtml#page143)

environment, utilizing [139](#c08.xhtml#page139)

resources, utilizing [146](#c08.xhtml#page146)

Lucid + Aiken

advantage [77](#c05.xhtml#page77)

Blockfrost API, utilizing [77](#c05.xhtml#page77)

code, initializing [77](#c05.xhtml#page77), [78](#c05.xhtml#page78)

off-chain, coding [79](#c05.xhtml#page79), [80](#c05.xhtml#page80)

M

Maestro [125](#c08.xhtml#page125)

Maestro, features

Blockchain, indexing [125](#c08.xhtml#page125)

transaction, managing [125](#c08.xhtml#page125)

turbo, transaction [125](#c08.xhtml#page125)

Member-Based Organization (MBO) [269](#c13.xhtml#page269)

Metadata [38](#c03.xhtml#page38), [39](#c03.xhtml#page39)

Midnight [274](#c13.xhtml#page274)

Minting Policy, use case

Aiken On-Chain [111](#c07.xhtml#page111), [112](#c07.xhtml#page112)

Lucid Off-Chain [112](#c07.xhtml#page112)\-[114](#c07.xhtml#page114)

Off-Chain, burning [110](#c07.xhtml#page110), [111](#c07.xhtml#page111)

Off-chain, minting [108](#c07.xhtml#page108)\-[110](#c07.xhtml#page110)

On-chain Helios [107](#c07.xhtml#page107), [108](#c07.xhtml#page108)

Mithril [247](#c11.xhtml#page247)

N

Next.js

reference link [70](#c05.xhtml#page70)

Non-Fungible Token (NFT)

about [103](#c07.xhtml#page103)

approaches [103](#c07.xhtml#page103)

metadata, utilizing [103](#c07.xhtml#page103)

validator, setup [115](#c07.xhtml#page115)\-[119](#c07.xhtml#page119)

O

off-chain, coding [70](#c05.xhtml#page70)

offeredAssetVal [197](#c10.xhtml#page197)

Ogmios [133](#c08.xhtml#page133), [134](#c08.xhtml#page134)

order book, principles [153](#c09.xhtml#page153)

order book, process [152](#c09.xhtml#page152)

Ouroboros PoS, protocol

Byzantine Fault Tolerance (BFT) [24](#c02.xhtml#page24)

chronos [26](#c02.xhtml#page26)

classic [24](#c02.xhtml#page24)

crypsinous [25](#c02.xhtml#page25)

genesis, addressing [25](#c02.xhtml#page25)

Verifiable Random Function (VRF) [25](#c02.xhtml#page25)

Ouroboros Protocol, lifecycle

register [26](#c02.xhtml#page26)

staking [26](#c02.xhtml#page26), [27](#c02.xhtml#page27)

time [26](#c02.xhtml#page26)

P

Plutus Budget, executing [55](#c04.xhtml#page55), [56](#c04.xhtml#page56)

Plutus Script, concepts

Beacon Policy, minting [190](#c10.xhtml#page190), [191](#c10.xhtml#page191)

ticket policy, minting [191](#c10.xhtml#page191)\-[194](#c10.xhtml#page194)

validator, holding [194](#c10.xhtml#page194)\-[196](#c10.xhtml#page196)

validator, swapping [196](#c10.xhtml#page196)\-[201](#c10.xhtml#page201)

Plutus Scripts [40](#c03.xhtml#page40)

Preprod Testnet

reference link [63](#c05.xhtml#page63)

Probabilistic Finality (Chain-based) [23](#c02.xhtml#page23)

Proof-of-Stake (PoS) [22](#c02.xhtml#page22), [23](#c02.xhtml#page23)

Proof-of-Stake, protocols

Absolute Finality (PBFT) [23](#c02.xhtml#page23)

Probabilistic Finality (Chain-based) [23](#c02.xhtml#page23)

Proof-of-Work (PoW) [21](#c02.xhtml#page21), [22](#c02.xhtml#page22)

PubKeyHash [85](#c06.xhtml#page85)

Public Key Encryption [18](#c02.xhtml#page18)

R

Redeemers [40](#c03.xhtml#page40), [41](#c03.xhtml#page41)

Redis DB

about [202](#c10.xhtml#page202)

API, utilizing [203](#c10.xhtml#page203)

setup [203](#c10.xhtml#page203), [204](#c10.xhtml#page204)

S

ScriptContext [84](#c06.xhtml#page84), [86](#c06.xhtml#page86)

ScriptHash [32](#c03.xhtml#page32)

smart contract, aspect

Aiken [254](#c12.xhtml#page254), [255](#c12.xhtml#page255)

Helios [253](#c12.xhtml#page253)

Smart Contract development [236](#c11.xhtml#page236)

Smart Contract development, concept

audits, optimizing [243](#c11.xhtml#page243)

datum, analyzing [239](#c11.xhtml#page239)\-[241](#c11.xhtml#page241)

token, leakage [241](#c11.xhtml#page241)\-[243](#c11.xhtml#page243)

vulnerabilities, satisfying [236](#c11.xhtml#page236)\-[238](#c11.xhtml#page238)

Software Industry, trends

Blockchain, risks [281](#c14.xhtml#page281)

IACR [283](#c14.xhtml#page283)

semi-formal method, specifying [282](#c14.xhtml#page282), [283](#c14.xhtml#page283)

Stake Pool Operator (SPO)

about [271](#c13.xhtml#page271)

project, varifying [272](#c13.xhtml#page272)

tools [271](#c13.xhtml#page271)

stake\_reference [34](#c03.xhtml#page34)

state machine diagram, concepts

asset, executing [162](#c09.xhtml#page162), [163](#c09.xhtml#page163)

burning [159](#c09.xhtml#page159)

print, transaction [164](#c09.xhtml#page164)

swap, closing [163](#c09.xhtml#page163), [164](#c09.xhtml#page164)

swap, opening [160](#c09.xhtml#page160), [161](#c09.xhtml#page161)

swap, updating [161](#c09.xhtml#page161)

ticket, minting [159](#c09.xhtml#page159)

swap, setup

even, organizing [206](#c10.xhtml#page206)

script, modifying [208](#c10.xhtml#page208)

ticket, converting [217](#c10.xhtml#page217)\-[219](#c10.xhtml#page219)

ticket, getting [209](#c10.xhtml#page209)

tickets, buying [211](#c10.xhtml#page211)\-[213](#c10.xhtml#page213)

ticket, verifying [216](#c10.xhtml#page216)

transaction, updating [210](#c10.xhtml#page210)

wallet, connecting [206](#c10.xhtml#page206)

T

testing framework

about [229](#c11.xhtml#page229)

benefits [229](#c11.xhtml#page229)

directory, utilizing [230](#c11.xhtml#page230)

property, testing [235](#c11.xhtml#page235), [236](#c11.xhtml#page236)

strategies [230](#c11.xhtml#page230)\-[232](#c11.xhtml#page232)

test, cases [232](#c11.xhtml#page232)\-[234](#c11.xhtml#page234)

Testnet, types

preprod [62](#c05.xhtml#page62)

preview [62](#c05.xhtml#page62)

thread token [151](#c09.xhtml#page151)

Token

about [101](#c07.xhtml#page101)

CIP-25 [104](#c07.xhtml#page104)

CIP-68 [105](#c07.xhtml#page105)

minting, policy [102](#c07.xhtml#page102)

Native Assets [101](#c07.xhtml#page101)

Non-Fungible Token (NFT) [103](#c07.xhtml#page103)

Token Bundles [101](#c07.xhtml#page101), [102](#c07.xhtml#page102)

Token, components

naming [101](#c07.xhtml#page101)

policy, identifying [101](#c07.xhtml#page101)

quantity, utilizing [101](#c07.xhtml#page101)

Tokenomics

about [8](#c01.xhtml#page8)

rate, inflation [11](#c01.xhtml#page11)

Token, allocating [8](#c01.xhtml#page8)

Token, comparing [10](#c01.xhtml#page10)

Token, distributing [9](#c01.xhtml#page9)

Token Registry [103](#c07.xhtml#page103)

Transaction Builder Errors [259](#c12.xhtml#page259)

U

Unlock.tsx [87](#c06.xhtml#page87)

Untyped Plutus Lambda Core (UPLC)

about [47](#c04.xhtml#page47)

example, simplifying [50](#c04.xhtml#page50)

grammar, utilizing [49](#c04.xhtml#page49)

types [48](#c04.xhtml#page48)

UTXO

about [35](#c03.xhtml#page35)

input, transaction [36](#c03.xhtml#page36)

output, transaction [36](#c03.xhtml#page36)\-[38](#c03.xhtml#page38)

UTXO, lifecycle [60](#c05.xhtml#page60), [61](#c05.xhtml#page61)

UTXO, script purposes

certifying [86](#c06.xhtml#page86)

minting [86](#c06.xhtml#page86)

rewarding [86](#c06.xhtml#page86)

spending [86](#c06.xhtml#page86)

V

Validators [84](#c06.xhtml#page84)

Validators, components

function, analyzing [90](#c06.xhtml#page90), [91](#c06.xhtml#page91)

off-chain, code [87](#c06.xhtml#page87)\-[89](#c06.xhtml#page89)

on-chain, code [85](#c06.xhtml#page85)\-[87](#c06.xhtml#page87)

URL, scripting [91](#c06.xhtml#page91)

W

wallet

about [61](#c05.xhtml#page61), [62](#c05.xhtml#page62)

CIP-30 [67](#c05.xhtml#page67)

path, derivating [64](#c05.xhtml#page64), [65](#c05.xhtml#page65)

seed, phrasing [62](#c05.xhtml#page62)

staking [65](#c05.xhtml#page65), [66](#c05.xhtml#page66)

Testnets [62](#c05.xhtml#page62)\-[64](#c05.xhtml#page64)

walletAPI [72](#c05.xhtml#page72)

WalletConnect.tsx [79](#c05.xhtml#page79)

WalletInfo [114](#c07.xhtml#page114)

witnesses, types [41](#c03.xhtml#page41), [42](#c03.xhtml#page42)