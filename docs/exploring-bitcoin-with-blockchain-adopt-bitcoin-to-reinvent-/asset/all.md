![](images/cover.jpg)

![image](images/cover.jpg)

# Exploring Bitcoin  
with  
Blockchain

![](images/line.jpg)

# *Adopt Bitcoin to Reinvent Business  
Scaling with Lower Transaction  
Costs and Better Fraud Prevention*

![](images/line.jpg)

# Vizeet Srivastava

![](images/logo.jpg)

[www.bpbonline.com](http://www.bpbonline.com)

Copyright © 2022 BPB Online

*All rights reserved.* No part of this book may be reproduced, stored in a retrieval system, or transmitted in any form or by any means, without the prior written permission of the publisher, except in the case of brief quotations embedded in critical articles or reviews.

Every effort has been made in the preparation of this book to ensure the accuracy of the information presented. However, the information contained in this book is sold without warranty, either express or implied. Neither the author, nor BPB Online or its dealers and distributors, will be held liable for any damages caused or alleged to have been caused directly or indirectly by this book.

BPB Online has endeavored to provide trademark information about all of the companies and products mentioned in this book by the appropriate use of capitals. However, BPB Online cannot guarantee the accuracy of this information.

**Group Product Manager:** Marianne Conor

**Publishing Product Manager:** Eva Brawn

**Senior Editor:** Connell

**Content Development Editor:** Melissa Monroe

**Technical Editor:** Anne Stokes

**Copy Editor:** Joe Austin

**Language Support Editor:** Justin Baldwin

**Project Coordinator:** Tyler Horan

**Proofreader:** Khloe Styles

**Indexer:** V. Krishnamurthy

**Production Designer:** Malcolm D'Souza

**Marketing Coordinator:** Kristen Kramer

**First published:** July 2022

Published by BPB Online

WeWork, 119 Marylebone Road

London NW1 5PU

**UK | UAE | INDIA | SINGAPORE**

ISBN 978-93-55512-789

**[www.bpbonline.com](http://www.bpbonline.com)**

# Dedicated to

*My beloved*

*Wife **Rati** and Daughter **Aruvyaa***

# About the Author

I am **Vizeet Srivastava**. I have over 20 years of experience in all phases of product development lifecycle. I have experience in wide range of technologies starting from Telecom, Datacom, and Windows device drivers, and now for last ten years I am into Big Data and Cloud Platform technologies.

My role has been to architect and design solution and work with team to bring the solution to completion. As a Data Engineer I have worked with multi-channel disparate data sources to perform Complex Event Processing, create State Machine, flow control and build graphical relationship. As a Cloud Engineer I have worked on automation of cloud migration, automation of data ingestion, cleansing, transformation, and consumption of transformed data.

I am certified Hyperledger developer and consultant.

Currently, I am a proprietor of HyperVerse Global Consulting company in Serbia, and I am providing software consulting services related to Big Data and Cloud platform to clients.

# About the Reviewer

**Priyank Jani** has more than 7+ years of Blockchain experience and 14+ years of software industry experience. Presently he is working with Icertis as a Blockchain Architect. Priyank believes in Blockchain just not as a technology but as an idea, to change, to improve, to sustain, and to create new opportunities. Passionate about blockchain, Priyank has founded a community called “LetsBlockchain”, which enables businesses and individuals in adopting blockchain technologies. He is a member of the Government Blockchain Association and drives the Pune chapter.

# Acknowledgement

There are a few people I want to thank for the continued and ongoing support they have given me during the writing of this book. First and foremost, I would like to thank my wife and daughter for their continuous support, encouragements and sacrifices they have made in my self-learning journey without it I could have never completed this book.

I am grateful to Satoshi Nakamoto who gave us hope of financial inclusion for over 1 billion people who are being neglected by the current financial system. I am also grateful to Andreas Antonopoulos for his book “Mastering Bitcoin: Programming the Open Blockchain” and his YouTube videos which enlightened me and gave me technical perspective of Bitcoin. I am also grateful to Vijay Boyapati and Michael J Saylor for his book “The Bullish Case for Bitcoin” which gave me financial perspective of Bitcoin.

I am grateful to everyone who directly or indirectly helped me with all the material I needed to learn Bitcoin — I could not have learned Bitcoin and completed this book without their contribution.

I gratefully acknowledge Mr. Priyank Jani and Samanyu Chopra for their kind technical scrutiny for this book.

My gratitude also goes to the team at BPB Publications for being supportive enough to provide me quite a long time to finish the the book since Bitcoin blockchain is the core of cryptocurrency and blockchain technology space it required a lot of research to bring the details, connection with other components in the ecosystem and benefit to the readers without making the book too voluminous.

# Preface

The book takes the reader step by step and layer by layer deeper into the technological side of Bitcoin so that someone with no prior knowledge of Bitcoin or someone with intermediate knowledge both gets benefited. The book gives greater weightage towards explanation of concepts and fundamentals than programing. Though programing Bitcoin is important part of this book, more than half of the chapters do not contain any programs and are focused on explanation. The book uses Python programs, simple language, examples, charts and illustrations to explain each section and chapters.

The book is written for people with average programming skill and has interest towards understand basics of Bitcoin. Basic knowledge of Python programming is necessary. The book uses simple procedural programming which may be understood by anyone with average programming even if he has only little prior experience of Python.

The book is written keeping in mind the needs of college students and colleges. It includes question and programming assignments. It will be useful for person with no knowledge, beginner and have intermediate knowledge of Bitcoin.

It is important to realize that investment in bitcoin comes with a risk and is often attributed for financial losses. The book does not provide any financial advice and does not aim to influence reader’s financial decisions. It is purely a technical book and is only targeted to readers who has interest in the technical aspect of Bitcoin. Having said that the book does build a case in favor of Bitcoin as a technological milestone and its importance in our future.

The book is an effort to grow Bitcoin developer community by making the knowledge of Bitcoin internals easily accessible to the masses. This is the reason why the book focuses on theory and uses simple procedural programs written in Python. The programs in this book are only created for learning purposes, they are not gone through elaborate testing and so are not ready for production environments where real bitcoins are used for payments.

The book uses private keys and seed phrase in the programs. These private keys and seed phrases should not be used anywhere in wallet or for sending and receiving real bitcoins as they will get stolen.

The goal of this book is achieved when readers of this book start using the concepts explained in this book and can adopt new concepts such as taproot and develop their own viewpoint about Bitcoin enhancements and features or start contributing to the Bitcoin ecosystem.

*The book consists of 13 chapters and chapters are classified in the following four sections:*

**Introduction** will be the first section and consists of four chapters. Will focus on familiarizing readers about Bitcoin. Will cover the blockchain ecosystem, other cryptocurrencies and blockchain projects, definition, need and necessity of Bitcoin, overview of topology and consensus mechanisms and use cases.

**[Chapter 1](#c01.xhtml)** will give the readers glimpse of ecosystem to which Bitcoin is the part and introduces readers to other cryptocurrencies and blockchain projects and overall Bitcoin ecosystem.

**[Chapter 2](#c02.xhtml)** will understand the technologies enhancements that were taking place which resulted in the inception of Bitcoin network and the major events happened since Bitcoin came into existence. Will also explain the meaning and purpose of Bitcoin, the impact it may have on our future and why learning Bitcoin is still important.

**[Chapter 3](#c03.xhtml)** will understand about the network topology of Bitcoin and will understand Bitcoin consensus network. The Bitcoin network topology will include types of nodes, their interactions. The Bitcoin consensus network will include its components, their interactions and a high-level view of how payments in bitcoin can be seen as transaction creation, transaction signing, propagations, and finally inclusion into blockchain.

**[Chapter 4](#c04.xhtml)** will understand about different ways people and organizations use Bitcoin and interact with Bitcoin network.

**Bitcoin Consensus Network** will be the second section consisting of four chapters. Will focus on understanding the basics of Bitcoin’s proof of work consensus mechanism by explaining Bitcoin Whitepaper, verifying blocks in blockchain, building and verifying transactions, understanding the process of mining and finally understanding the strength and weakness of Bitcoin in detail.

**[Chapter 5](#c05.xhtml)** will understand the Bitcoin Whitepaper section by section in detail.

**[Chapter 6](#c06.xhtml)** will analyze Bitcoin blockchain, block and transaction structure, understand different indexes used by Bitcoin Core software, understand mining in greater detail and try to build a solo miner.

**[Chapter 7](#c07.xhtml)** will dive deep into the node-to-node communication. Will include establishing Bitcoin network, discover nodes, broadcast transactions and blocks, and learn to download and synchronization of blockchain.

**[Chapter 8](#c08.xhtml)** will understand the limitation, vulnerabilities and the potential threats for Bitcoin. Will understand that the scaling and privacy limitations were introduced in the design and during implementation and were necessary and different ways it can be overcome. Will understand different ways Bitcoin network may be attacked or may become vulnerable to attacks in the future and how this may be mitigated or may not be an issue. Will also understand other forms of attacks or mistake due to which individuals can lose bitcoins.

**Programming Bitcoin** will be the third section consisting of three chapters. Will go into details of Bitcoin scripting and use them to build more complex use cases including smart contracts. Will also dive deep into wallets for receiving and accessing bitcoins.

**[Chapter 9](#c09.xhtml)** will learn to access and secure bitcoins. Will learn to generate private keys from random number which is used in signing a transaction before sending it to the network. Will learn to generate public keys and addresses which are used for receiving bitcoins. Will also learn to create deterministic wallet which will help simplify receiving, sending and securing bitcoins.

**[Chapter 10](#c10.xhtml)** will deep dive into transaction verification and creation. Will learn to parse a transaction and learn about the scripting language used to lock and unlock bitcoins in a transaction. Will create the standard transactions and publish them over the network.

**[Chapter 11](#c11.xhtml)** will understand to use scripting for creating variety of useful use cases which can be used in building more complex smart contract.

**Scaling Bitcoin** will be the fourth and final section of the book which consists of two chapters. The first of the two chapters will focus on segregated witness enhancement while the second one focusses on Lightning Network which is the layer two protocol added to the Bitcoin blockchain. Both chapters will provide different approaches to scale Bitcoin. Each chapter will go deeper into explaining the topic and will not be limited to scaling. Lightning Network will not include programming.

**[Chapter 12](#c12.xhtml)** will understand Segregated Witness enhancement. Will understand the different benefits of the enhancement. Will also learn to parse segregated witness transactions.

**[Chapter 13](#c13.xhtml)** will understand Lightning Network the second layer added to the Bitcoin protocol. Will understand the Lightning Network channel management and smart contract in some detail. Will also understand channel monitoring, routing mechanism and user experience with Lightning Network.

# Code Bundle and Coloured Images

Please follow the link to download the  
***Code Bundle*** and the ***Coloured Images*** of the book:

# [https://rebrand.ly/j0y87d1](https://rebrand.ly/j0y87d1)

The code bundle for the book is also hosted on GitHub at **[https://github.com/bpbpublications/Exploring-Bitcoin-with-Blockchain](https://github.com/bpbpublications/Exploring-Bitcoin-with-Blockchain)**. In case there's an update to the code, it will be updated on the existing GitHub repository.

We have code bundles from our rich catalogue of books and videos available at **[https://github.com/bpbpublications](https://github.com/bpbpublications)**. Check them out!

# Errata

We take immense pride in our work at BPB Publications and follow best practices to ensure the accuracy of our content to provide with an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at :

**[errata@bpbonline.com](mailto:errata@bpbonline.com)**

Your support, suggestions and feedbacks are highly appreciated by the BPB Publications’ Family.

Did you know that BPB offers eBook versions of every book published, with PDF and ePub files available? You can upgrade to the eBook version at **[www.bpbonline.com](http://www.bpbonline.com)** and as a print book customer, you are entitled to a discount on the eBook copy. Get in touch with us at: **[business@bpbonline.com](mailto:business@bpbonline.com)** for more details.

At **[www.bpbonline.com](http://www.bpbonline.com)**, you can also read a collection of free technical articles, sign up for a range of free newsletters, and receive exclusive discounts and offers on BPB books and eBooks.

# Piracy

If you come across any illegal copies of our works in any form on the internet, we would be grateful if you would provide us with the location address or website name. Please contact us at [**business@bpbonline.com**](mailto:business@bpbonline.com) with a link to the material.

# If you are interested in becoming an author

If there is a topic that you have expertise in, and you are interested in either writing or contributing to a book, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/) We have worked with thousands of developers and tech professionals, just like you, to help them share their insights with the global tech community. You can make a general application, apply for a specific hot topic that we are recruiting an author for, or submit your own idea.

# Reviews

Please leave a review. Once you have read and used this book, why not leave a review on the site that you purchased it from? Potential readers can then see and use your unbiased opinion to make purchase decisions. We at BPB can understand what you think about our products, and our authors can see your feedback on their book. Thank you!

For more information about BPB, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# [CHAPTER 1](#toc.xhtml#c01)

# [Introduction](#toc.xhtml#c01)

As this book is written, Bitcoin has been live for more than 13 years. And what a decade it has been! Bitcoin is the first purely decentralized currency that does not need any trusted third-party to mediate a transaction, making it the digital equivalent of physical cash. Today, there are thousands of cryptocurrencies, and many are having different value propositions. And it is not just cryptocurrencies; the whole ecosystem continues to evolve, bringing fresh innovations.

In this chapter, we will try to get a glimpse of the scale of the ecosystem that surrounds cryptocurrencies and blockchain technologies. You will understand the different kinds of cryptocurrencies and each part that makes up this ecosystem.

# [Structure](#toc.xhtml#s1a)

In this chapter, we will be discussing the following topics:

*   The cryptocurrency, and blockchain ecosystem 
    *   Distributed Ledger Technology (DLT)
    *   Cryptocurrencies and their value proposition 
        *   Smart contract and token platforms
        *   Payments, store-of-value and alternate finance
        *   Privacy
        *   Oracles and multichain connectors
        *   Stablecoins
    *   Blockchain ecosystem 
        *   Medium of exchange and store of value
        *   Private and public blockchains
        *   Permissioned and permissionless blockchains
        *   Compliance, record keeping, and auditing
        *   Tokens
        *   Decentralized applications
        *   Fungible and non-fungible tokens
        *   Decentralized finance
    *   The Bitcoin ecosystem 
        *   Bitcoin education, training, and online help materials
        *   Nodes and wallets
    *   Mining and mining pools 
        *   Payments
        *   Exchanges

# [Objectives](#toc.xhtml#s2a)

The primary objective of this chapter is to provide an overview of blockchain and the Bitcoin ecosystem to help readers understand the scale of innovation taking place in this field.

After reading this chapter, you will have some idea of the different purposes blockchain technology and cryptocurrencies serve.

# [The cryptocurrency and blockchain ecosystem](#toc.xhtml#s3a)

Let’s look at the numbers to understand the scale and size of the ecosystem.

There are now more than 9,000 cryptocurrencies. The market capitalization of all the cryptocurrencies combined is $1.8 trillion. There are a few hundred thousand tokens written over various cryptocurrencies. There are over 500 exchanges where you can buy or sell cryptocurrencies. There are over 10,000 cryptocurrency ATMs running globally. There are tens of thousands of jobs related to cryptocurrency and blockchain. And there are over 100 million users worldwide. This is now a booming industry.

When Bitcoin was created, it was the only cryptocurrency. As more cryptocurrencies and other technologies appeared, we started classifying them into different classes, and then those classes grew.

Cryptocurrencies work as a distributed ledger of transactions. A transaction is a record of the transfer of the cryptocurrency between the funding parties and the receiving parties. Later, we built other distributed ledgers storing asset transfer information and self-enforcing agreements between parties. These distributed ledger systems relied on the blockchain. Then, a few innovative ideas appeared based on other methods.

# [Distributed Ledger Technology (DLT)](#toc.xhtml#s4a)

Bitcoin uses blockchain, which is the linked list of blocks wherein each block consists of immutable lists of transactions or smart contracts. Similar to a ledger, it is a book of records. It is shared with others in the network. DLT is an umbrella term, and blockchain falls under it. DLT stands for **Distributed Ledger Technology** (**DLT**); it can be classified as blockchain-based implementations and non-blockchain-based implementations. Few cryptocurrencies use some other methods of storing records; for example, IOTA uses **Directed Acyclic Graph** (**DAG**). Hashgraph is yet another technology used for distributed record keeping. These are also referred to as DLT.

When corporates started getting involved in the concept, they created blockchain implementations and platforms that had access control and were built to keep records safe behind firewalls. These blockchain implementations were created for use within an organization or between a consortium of organizations, and they are called private blockchains. The private blockchain implementations for consortiums provide federated architecture consisting of multiple chains.

The following is the illustration of the preceding description:

![](images/Figure-1.1.jpg)

**Figure 1.1:** Classification of distributed ledger technology

# [Cryptocurrencies and their value proposition](#toc.xhtml#s5a)

Bitcoin was designed as a currency with limited and controlled supply. In economics, an inflation rate is a rate at which the prices of goods and services rise over a period. In Bitcoin terminology, inflation is the rate at which new bitcoin is mined or minted, or created. Inflation is controlled by an algorithm, and it reduces by half nearly every 4 years. Different cryptocurrencies have different inflation rules.

Bitcoin was originally designed for the purpose of peer-to-peer payment. Originally, transferring a bitcoin did not require payment to Bitcoin miners as anyone could mint a bitcoin on their laptop. Large supply, low value, zero transaction fee, and global presence made Bitcoin a good medium of payment. However, as time passed, bitcoin value increased, network fees increased, and supply started going down, which made it an incredibly good appreciating asset. It is still used as medium-of-exchange, and many merchants across the globe accept it.

The following are the top cryptocurrency and token projects that are known for their specific qualities:

![](images/28.jpg)![](images/29.jpg)

**Table 1.1:** Top cryptocurrencies/Tokens mapped with their specific qualities

# [Smart contract and token platforms](#toc.xhtml#s6a)

The smart contract is a self-enforcing agreement coded in a blockchain and written using a programming language.

Bitcoin provides a simple programming language, which can be used to write a smart contract. The scripting language is very primitive and does not provide a viable platform for building complex real-world contracts. To address this, *Vitalik Buterin* created a cryptocurrency called Ethereum that supported Turing complete *solidity language* for writing contracts. This language allowed developers to create tokens much faster than creating a cryptocurrency. This led to **Initial Coin Offering** (**ICO**) for raising funds through a token sale, Security Tokens, Utility Tokens, **Decentralized Finance** (**DeFi**), and recently **non-fungible tokens** (**NFT**). This attracted massive interest in blockchain technology to solve real-world problems.

However, RSK is a layer 2 solution of Bitcoin that provides smart contract capability like Ethereum. Like Ethereum, RSK allows smart contracts to be written in *Solidity*.

# [Payments, store-of-value, and alternate finance](#toc.xhtml#s7a)

As Bitcoin became valuable and mining started becoming difficult in personal computers, and laptops around 2013, the first ASIC hardware hit the market, raising network fees. It became clear that if network fees keep on increasing, bitcoin as a payment instrument for buying low-value items like coffee will not remain viable. The Bitcoin development community was divided on whether to increase block size for reducing transaction fees or to keep it the same so that the Bitcoin network does not have to compromise on security.

Alternatively, Ethereum, Litecoin, and a few other cryptocurrencies used the ASIC-resistant mining algorithm. The idea was to use algorithms that require memory instead of faster processing as ASIC hardware is efficient at solving CPU-intensive problems and not good for memory-hard problems.

Bitcoin Cash was one of the Bitcoin hard forks created primarily to reduce transaction fees by increasing block size.

Other cryptocurrencies such as Litecoin and Dogecoin provide shorter confirmation time, making them better suited for cash-like payments.

XRP is a cryptocurrency that provides near real-time payments across the world. Its main goal was to provide financial institutions with a medium of exchange. It claims to provide payment processing capability like SWIFT.

# [Privacy](#toc.xhtml#s8a)

Bitcoin transactions are in blockchain, and anyone can look at them. When we buy bitcoin from an exchange, we need to provide KYC to the exchange. The exchange knows about your transactions, and all related transactions are also on the blockchain. Exchanges can leak this information to criminals, hackers, foreign governments, advertisers, etc. Exchanges can also link other transactions on the blockchain, and you may lose your financial privacy. There are a few methods that provide ways to make Bitcoin transactions more private, but these are not as good as cryptocurrencies, which are designed with privacy as the goal. Monero, Dash, Zcash, and Zcoin are some of the cryptocurrencies designed specifically with privacy as the goal.

# [Oracles and multichain connectors](#toc.xhtml#s9a)

Smart contracts enforce agreements, but these agreements are based on real-world information, which is not present on the blockchain. This information is provided by entities called *Oracle*. These entities are mostly centralized third parties. Polkadot and Chainlink provide decentralized mechanisms to provide external real-world information. Polkadot and Chainlink can interface between multiple blockchains allowing them to interchange information. This has led to interesting projects in this space. These concepts are still maturing, and we might see many more advancements in this space.

# [Stablecoins](#toc.xhtml#s10a)

A Stablecoin is a cryptocurrency that has value pegged with another asset such as USD, Euro, or Bitcoin, physical assets like gold, and so on.

Cryptocurrencies are bought and sold at exchanges in exchange for currencies. This attracts fees charged by the exchanges. For traders who want to take advantage of volatility in the crypto market but find the fees high can park their crypto investments into stablecoins and use them when they need to buy crypto.

Additionally, most people in the world do not have access to currencies such as the US Dollars and Euro, which are considered more stable. They can buy stablecoins, which are pegged with these currencies.

# [Blockchain ecosystem](#toc.xhtml#s11a)

The blockchain ecosystem consists of cryptocurrencies, private and public blockchains, exchanges, and other services created over them or related to them.

The following is a broad overview of the blockchain ecosystem. Keep in mind that the blockchain ecosystem is very wide, and everything cannot be shown here:

![](images/Figure-1.2.jpg)

**Figure 1.2:** Blockchain Ecosystem

# [Medium of exchange and store of value](#toc.xhtml#s12a)

We learned that cryptocurrencies are created to target specific requirements. All cryptocurrencies require developers; they need exchanges. Cryptocurrencies that became popular as medium-of-exchange need payment processors, wallets, and merchants who would accept them.

Cryptocurrencies that became popular as store-of-value or SoV require extremely secure methods of storing them for the long-term, so the vaults and hardware wallets are needed, asset managers are needed that can provide custody services, and ETFs are needed so that non-technical investors can rely on financial institutions for the security of funds.

# [Private and public blockchains](#toc.xhtml#s13a)

Private blockchains like Hyperledger Fabric were created to provide immutability and access control of organization data, which could be verified by an auditor. Private blockchain technology such as Hyperledger Fabric also provides a federated structure, where each organization can have a separate blockchain created using Hyperledger Fabric, and data and code can be transferred across chains. This allowed a consortium of organizations with similar interests to come together and share data to improve the supply chain, transparency, and auditability. This also provides access control mechanism to the consortium, which provides certain rights to a certain set of entities.

# [Permissioned and permissionless blockchains](#toc.xhtml#s14a)

Permissioned blockchain implementations are created for internal use within an organization or between a consortium of organizations. Only specified or predefined entities can be part of it. Like office internet, only specified parties can use it and it cannot be used by general public.

Permissionless blockchains, on the other hand, do not require any permission for joining or interacting with the blockchain. Anyone with internet access can start using it.

# [Compliance, record keeping, and auditing](#toc.xhtml#s15a)

Financial institutions have used private blockchains to store the KYC/AML data of their clients. Since blockchains are immutable, they provide easy auditing, which helps meet compliance requirements. Private blockchains have also been used for record-keeping, like medical records.

# [Tokens](#toc.xhtml#s16a)

Public blockchains like Ethereum (which eased writing smart contracts in easy-to-develop languages) allowed the development of tokens, distributed application development, transaction and valuation of digital assets, and supply chain management. The development of tokens helped create **Initial Coin Offering** (**ICO**) and **Security Token Offering** (**STO**), which were used to raise funds for startups. Utility tokens helped in digitizing coupons or tickets.

# [Decentralized applications](#toc.xhtml#s17a)

Distributed applications or DApps are applications built on a decentralized network, which uses Smart Contract and UI to behave like any hosted application. DApps are used to build applications that can help build platforms and marketplaces. These marketplaces and platforms work as decentralized organizations. DApps can also provide censorship resistance and privacy.

# [Fungible and non-fungible tokens](#toc.xhtml#s18a)

Fungible tokens are like currencies. If a token is fungible, it is indistinguishable from other identical tokens. All cryptocurrencies are fungible. Sometimes the game has certain articles that are universally limited and are equally valuable for all players at any level; these can also be considered fungible.

NFTs stands for *non-fungible tokens*. A non-fungible token is the opposite of fungible tokens, which means their value depends on circumstances and individual preferences, like the cost of a seat in a movie theater, which may vary based on the location of that seat. They are useful for the digitization of assets like art, short films, music, etc., or for digital assets like digital artwork and collectibles.

# [Decentralized finance](#toc.xhtml#s19a)

Decentralized finance or DeFi are financial contracts created on the blockchain using a smart contract. The smart contract can be used for lending, insurance, trading, and derivative markets, among many others. Decentralized finance can also involve digital assets or currencies for settlement or mortgage.

# [The Bitcoin ecosystem](#toc.xhtml#s20a)

As cryptocurrencies and blockchain implementations were evolving, the Bitcoin ecosystem also evolved. Many services have been built to improve user and developer experience. There are services specifically designed for Bitcoin, and there are also services built for cryptocurrencies, tokens, and blockchains, which, in turn, benefit Bitcoin.

The following is an illustration of the Bitcoin ecosystem:

![](images/Figure-1.3.jpg)

**Figure 1.3:** Building blocks of Bitcoin Ecosystem

# [Bitcoin education, training, and online help materials](#toc.xhtml#s21a)

There are several websites that provide us with learning material, information about blockchain, information about price, mining pools, trends, etc. There are several online courses provided by MOOC providers on Bitcoin. Even reputed colleges like MIT are providing online courses on Bitcoin. There are also classroom courses conducted by training institutions and individuals. There are also websites providing testing platforms providing converters, calculators, and verification tools. Apart from this, many utility libraries written in Python, Node.js, Golang, etc. are available in git. There are also many videos on YouTube explaining several aspects of the Bitcoin blockchain. Apart from this, one can ask technical questions on stack exchange and may get a response from core developers.

# [Nodes and wallets](#toc.xhtml#s22a)

There are many Bitcoin-node-software available, some providing full node capability, while others providing SPV nodes. Bitcoin is accessed by the software called wallet. There are online wallets provided by exchanges and payment processors, and there are also hardware wallets, desktop wallets, mobile wallets, and light wallets.

# [Mining and mining pools](#toc.xhtml#s23a)

When miners solve mathematical problem and create the next block, they are rewarded with bitcoin. Miners compete to solve the hard problem. Companies also compete to build mining devices, which provide better computing power at lower costs. As more miners enter the market and mining equipment companies build more efficient mining devices, the Bitcoin network adjusts the difficulty of the hard problem. This reduces return from older devices, and they become obsolete.

As bitcoin prices have risen at an exponential rate, mining difficulty has also increased tremendously. Due to this, there is a negligible chance that anyone can solve a difficult problem all alone, even if they have hundreds of the world’s best pieces of equipment. This is the current state of mining. As a solution to this, anyone who intends to make money out of mining must join a mining pool. There are several mining pools that pay the miners based on their contribution once a block is mined by the pool.

# [Payments](#toc.xhtml#s24a)

Bitcoin wallets can receive or send bitcoin to other Bitcoin wallets. One can use bitcoin associated with their wallet and send it to another Bitcoin address, which will be associated with the receiver’s wallet. It is recommended that we always use new addresses for receiving bitcoin. For payments, this is an overly complex thing to achieve. So, Bitcoin provides a secure and private way of transferring payments, which are called PayNyms.

There are also payment gateways like BitPay, and exchanges like Coinbase also provide payment gateways that allow the easy transfer of bitcoin for commercial purposes such as purchases. Payment gateways like Paypal allow clients to load wallets with bitcoin and pay to the merchants in dollars or other currencies.

Bitcoin transactions, on average, take 10 minutes to get confirmed if an adequate network fee is paid, which can be a couple of dollars. Confirmation means getting the transaction in a block. Due to the high network fee, buying coffee is not viable. To solve this issue, Bitcoin has a layer-2 network called **Lightning Network**, which allows merchants to create channels with clients. If enough transactions are made on this channel, then the effective network fee gets low enough to make the transaction viable. Lightning Network transactions are also instant.

# [Exchanges](#toc.xhtml#s25a)

It’s the exchanges that give bitcoin a monetary value. Exchanges are the place where cryptocurrencies are bought, traded, and sold. There are buyers in exchanges, who are looking to buy bitcoin at a certain asking price, and there are sellers bidding for their bitcoin at certain prices. Centralized exchanges use asking and bidding to move prices up and down in order to discover the right price for bitcoin. Exchanges also take risks as prices can fluctuate rapidly, and they may lose due to this. So, centralized exchanges charge spread fees based on the market volatility, but not all exchanges are like this. Peer-to-peer exchanges do not have enough volume that they could trace cryptocurrency value, so they provide buyers and sellers with a platform to buy directly from each other and charge fixed commissions.

Exchanges can also be classified as follows:

*   **Custodial exchange**: Exchange that hold bitcoin in a wallet
*   **Non-custodial exchange**: Exchange that do not hold bitcoin in a wallet

# [Conclusion](#toc.xhtml#s26a)

At the beginning of the chapter, we explored the developments related to Bitcoin, Blockchain, and DLT. This gave us a good idea of what constitutes the ecosystem, how it is progressing, and how much impact it has or will have on our lives.

In the next chapter, you will understand a bit of history that helped Satoshi build Bitcoin, and then you will learn how it has grown. You will also understand the definition of Bitcoin, the game theory problem it solves, and the impact of solving the problem in the coming future. Additionally, we will go through the basic properties of Bitcoin.

# [Points to remember](#toc.xhtml#s27a)

*   When Bitcoin was created, it was the only cryptocurrency.
*   Satoshi Nakamoto is a pseudonym who published Bitcoin Whitepaper on 31^(st) October 2008, release code, and deployed network on 3^(rd) January 2009. He was active till December 2010. His identity stays unknown till date.
*   Bitcoin has a primitive scripting language that is sufficient to write smart contract.
*   DLT is Decentralized Ledger Technology that includes blockchain, Hashgraph, Directed Acyclic Graphs, etc.
*   Private blockchains operate within an organization.
*   Public blockchains are open networks, and anyone anywhere in the world can interact with them.
*   Permissioned blockchain implementations were created for internal use within an organization or between a consortium of organizations.
*   Permissionless blockchains do not require any permission for joining or interacting with the blockchain.
*   Cryptocurrencies can be classified based on their value propositions.
*   Few cryptocurrencies provide Turing complete scripting or programming language support, which makes it easier to write a smart contract and build tokens on it.
*   Fungible tokens are like currencies. If a token is fungible, it is indistinguishable from other same tokens.
*   NFTs are Non-Fungible Tokens. A non-fungible token is the opposite of a fungible token, which means their value depends on circumstances and individual preferences.
*   Decentralized Finance or DeFi are financial contracts created on the blockchain using a smart contract.
*   A Stablecoin is a cryptocurrency that has value pegged with another asset such as USD, Euro, Bitcoin or physical assets like gold.
*   Distributed applications or DApps are applications built on a decentralized network that uses smart contract and user interface to behave like any hosted application.
*   Custodial exchanges hold bitcoin in their wallet.
*   Non-custodial exchanges do not hold bitcoin; users of these exchanges send and receive bitcoin directly from the wallets held outside the exchange by them.
*   Cryptocurrencies, which are suitable for small purchases, classify as currencies or Medium-of-exchange.
*   Cryptocurrencies that have high transaction costs and have built confidence among users that they will be safe, secure, and protect value for the long term can be considered store-of-value.
*   A smart contract is a self-enforcing agreement coded in a blockchain and written using a programming language.
*   Initial Coin Offerings (ICOs) were used for fundraising like IPO but used tokens created over cryptocurrencies like Ethereum. This was used by startups offering products and services in the cryptocurrency and blockchain space.
*   Security Token Offerings (STOs) are public offerings like ICOs but are sold at exchanges as digital securities, which are legally binding, and so, make them the better option for investors.
*   Utility tokens are given by companies in the form of coupons or tickets that are limited in supply. These coupons can be redeemed later, or the tickets can be used for a concert.
*   Exchanges are the marketplaces where cryptocurrencies get their value.
*   Wallets contain a collection of addresses that can receive cryptocurrencies. Wallets can also access these cryptocurrencies for sending them to other addresses and wallets.
*   A full node is a program that verifies all the blocks and transactions.
*   Mining nodes compete with other mining nodes in solving a cryptographic puzzle by using computational power.
*   The mining node that solves the cryptographic puzzle creates a block adding transactions from mempool, and the miner receives bitcoin as a block reward.
*   Miners join mining pools to cooperate instead of competing in solving a cryptographic puzzle. Each miner is paid in the portion of mined cryptocurrency according to their contribution in the computational power.

# [Questions](#toc.xhtml#s28a)

1.  How is DApp different from hosted apps?
2.  What were the drawbacks of ICO that led to their failure as an instrument for raising funds, and how do STOs solve that problem?
3.  Why does Bitcoin mining consume a lot of energy?
4.  How does the term ledger relate to blockchain?
5.  What is the difference between layer 2 and sidechains?
6.  What is Turing complete language?
7.  Give five examples of fungible and non-fungible goods.
8.  Give five applications of utility tokens.
9.  Match the most important property of blockchain with the listed applications:
    
    **Properties:**
    
    1.  Immutability
    2.  Smart contract
    3.  Decentralized
    4.  Consensus
    5.  Ledger
    6.  Chronological order
    
    **Applications:**
    
    1.  Recordkeeping, auditing
    2.  Transactions, payments
    3.  Marketplace
    4.  Timestamping
    5.  Agreements
    6.  Voting
10.  Fill in the blanks: 
     1.  DApps are applications built on the \_\_\_\_\_\_\_\_\_\_\_ network using \_\_\_\_\_\_\_ contract and \_\_\_\_\_\_\_\_\_\_\_\_.
     2.  \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ was the first cryptocurrency launched decades before Bitcoin.
     3.  Bitcoin is not \_\_\_\_\_\_\_\_\_\_ coin, but it is \_\_\_\_\_\_\_\_\_\_\_\_\_ resistant.
     4.  \_\_\_\_\_\_\_\_\_\_\_\_ helps smart contract interact with real-world resources.
     5.  First blockchain was used for reliable decentralized \_\_\_\_\_\_\_\_\_\_\_.
     6.  Ethereum provides \_\_\_\_\_\_\_\_\_\_\_\_\_\_ language for its smart contract called Solidity.
11.  True/False: 
     1.  Blockchains do not need to have a value associated with transactions.
     2.  Bitcoin script language does not support smart contracts.
     3.  Hardware wallets contain cryptocurrencies and losing them means losing all the stored currencies.

# [CHAPTER 2](#toc.xhtml#c02)

# [Overview of Bitcoin](#toc.xhtml#c02)

In the previous chapter, you got a basic understanding of Bitcoin and the blockchain ecosystem. You also learned about basic terminologies that are often used in the technology space.

In this chapter, you will understand what lead to the development of Bitcoin, what developments were happening, and what the successes and failures were. Then, we will investigate what happened in the last 13 years, i.e., what were the important milestones, what were the important achievements that help Bitcoin become popular and what were the events which caused setback to the adoption of Bitcoin.

You will then understand what Bitcoin is, what problem it solves, how it solves the problem, and the scale of the impact of solving that problem. We will then understand why understanding Bitcoin is important and how knowing about it can help us.

You will also understand the characteristics of Bitcoin that give it value.

# [Structure](#toc.xhtml#s29a)

In this chapter, we will be discussing the following topics:

*   The case for learning Bitcoin
*   Developments leading to Bitcoin
*   The rise of Bitcoin
*   Defining Bitcoin 
    *   Byzantine general problem
    *   Bitcoin as a solution to Byzantines general problem
    *   Bitcoin property as a digital asset

# [Objectives](#toc.xhtml#s30a)

The primary objective of this chapter is to build a case for learning Bitcoin. We want readers to fully appreciate Bitcoin as a concept before we drill deeper into the technology in the upcoming chapters.

For a reader to fully appreciate Bitcoin, they need to be aware of its growth and achievements. So, in this chapter, we will learn about the history of Bitcoin and technologies that led to the development of Bitcoin. We will also understand Bitcoin’s value proposition.

After reading this chapter, readers will know why learning about Bitcoin is important.

# [The case for learning Bitcoin](#toc.xhtml#s31a)

Now, we have a good idea about how large the DLT ecosystem has become in 13 years. So, there may arise a question, “If Distributed Ledger Technology has evolved so much, then why do we want to learn about an outdated technology?”

Even though there are so many cryptocurrencies, Bitcoin still leads in certain aspects, such as the following:

*   Bitcoin network is the most secure network because of the mining computational power contributing to its security.
*   Bitcoin has the highest market dominance compared to all other cryptocurrencies and even tokens.
*   Since Bitcoin does not have a known creator, it can be considered more decentralized than any other cryptocurrency or token project.
*   Bitcoin’s enhancement process is quite stringent, which means enhancements only get accepted when a majority of stakeholders are fully convinced about the feature. This means only the best features that are aligned to Bitcoin’s character are the ones that get accepted.
*   Bitcoin network is the most monitored cryptocurrency network, which acts as an early warning system to detect anomalies before catastrophic events.
*   Bitcoin network has one of the largest developer bases in the cryptocurrency space, second only to Ethereum.
*   Bitcoin, being the oldest cryptocurrency, has an advantage over other cryptocurrencies. It has lived through all kinds of attacks, such as technological, social, and political. Due to this, it has built its reputation with global leaders and is one of the most accepted cryptocurrencies among hedge fund managers, top public listed companies, governments, and so on.

This may be clear now that Bitcoin isn’t outdated and is doing well, but we still need to see why it’s important to learn about Bitcoin.

As mentioned earlier, Bitcoin is the oldest cryptocurrency, so its code is used by most cryptocurrencies. Bitcoin is the foundation for most other cryptocurrencies and blockchain. This means it can help you understand the inner working of other cryptocurrencies and blockchain technologies. This might help you understand Ethereum, Hyperledger, or other popular technologies, which gives better opportunities for software engineers and entrepreneurs.

Knowing Bitcoin internals also helps you secure your cryptocurrency investment, and knowing its long-term value encourages you to hold it for the long-term and not get into panic buying and selling.

# [Developments leading to Bitcoin](#toc.xhtml#s32a)

Satoshi is/was a genius, but he/she wasn’t the first to create a cryptocurrency or think about it. He built a cryptocurrency that was better than earlier implementations and brought in the right people to work on it. Bitcoin is the culmination of everything that was happening in the world of cryptography.

The following is the timeline of advancements in the cryptographic space and experiments of centralized and decentralized currencies that happened along the way:

![](images/Figure-2.1.jpg)

**Figure 2.1:** History of cryptographic developments leading to Bitcoin

In November 1976, a paper titled *New Directions in Cryptography* was published by *Whitefield Diffie* and *Martin E. Hellman*. It suggested a method that consists of two keys: one for encrypting a message that is public and can be shared with others, and another for decrypting the message that is private and held securely by the owner of the key. The paper also proposed the concept of digital signature. It says that like physical signatures, digital signatures will be attached to the document, which could be created by the owner of the signature and also be verified by anyone for both content and the person who signed it.

This was the concept that later led to the first proposal of implementation in 1978 in a paper titled, *A Method for Obtaining Digital Signatures and Public-Key Cryptosystems by R.L. Rivest, A. Shamir*, and *L. Adleman.* Today, RSA and other asymmetric public-key cryptographic algorithms are widely used to transfer secrets and secure internet connections through SSL.

In 1980, *Ralph C. Merkle* published a paper titled *Protocols for Public Key Cryptosystems.* This paper is important as it suggested a way to verify the integrity of individual elements of a message by means of iterative hashing, which you will learn about later. This came to be called *Merkle Tree root*. It helps Bitcoin blockchain by ensuring the integrity of transactions in a block.

In 1982, *David Chaum* published a paper titled *Blind Signatures for Untraceable Payments*. The paper tried to tackle the privacy issue associated with digital payments. *David Chaum* could foresee the dangers of digital payments, and today, we know that financial privacy is important. He launched DigiCash, the first cryptocurrency, in 1989, which was quite successful at the time. However, it failed because it wasn’t decentralized.

In 1985, *Victor S. Miller* published a paper titled *Use of Elliptic Curves in Cryptography*, which explained how elliptic curves in the finite field can be used in public-key cryptography. Bitcoin uses elliptic curve cryptography with digital signatures.

It is worth mentioning that the Bitcoin Whitepaper has 8 references, of which 3 references are about papers written by *W.S. Stornetta*. Starting in 1991, he authored multiple papers on digital timestamping without involving central timestamping authority. *W.S. Stornetta, D. Bayer*, and *S. Haber* in the process created the first blockchain (it was not called blockchain then). They created a sequence of immutable records interlinked to a linear hash chain.

In 1994, *Nick Szabo* proposed the idea of a smart contract. In 1998, he proposed an idea of a decentralized cryptocurrency called Bit-gold. It was never launched, but it laid the foundation on cryptocurrencies, which led to the development of Bitcoin. In 2002, he wrote a draft of the paper, *A Formal Language for Analyzing Contracts* describing the language of the smart contract.

The year 1998 was an interesting year. PayPal was launched (which provided an alternate payment system and is still popular), Bit gold was conceptualized, and *Wei Dai* proposed the idea of b-Money. which conceptualized proof –of work and proof –of stake, in this year. Proof of work is used by Bitcoin and many other cryptocurrencies as a consensus algorithm while proof –of stake is used by Cardano and will be used by Ethereum in the future.

Many digital currencies were launched in the late 1990s till early 2000, and all of them failed. There were web currencies, and there were game currencies, which were used within the game. Second-life has a currency that could be bought by real money, and you could make money in the game and then convert it back into real money.

In 2002, *Adam Back* published a paper, *Hashcash - A Denial of Service Counter-Measure. This paper is quoted within* the *Bitcoin Whitepaper. The paper provides a mechanism to make systematic abuse* of internet resources costly. One of the applications is email spam. It uses CPU power to discourage spam mails or any similar abuse over internet resources.

In 2004, *Hal Finney* published the code of *RPOW - Reusable Proofs of Work*. This was probably the last missing piece that Satoshi needed to create Bitcoin. Earlier, proof –of work could be used to generate a token, which can help perform a single transaction. RPOW allowed the receiver of the token to regenerate a new token, which it can send to the next person, and so on. This way, the token generated by proof –of work works like a currency. RPOW uses Hashcash as a proof –of work token. The receiver of the Hashcash token generates RSA signed token called RPOW token in exchange for the Hashcash token, which it sends to the next receiver and repeats the process to move it further.

It is worth noting that there was a substantial number of digital currencies or digital payment methods launched since the 1980s, but except for a few gaming currencies, only PayPal survived. Several companies tried to replicate the PayPal model, but they all failed. The most successful among the failed attempt was e-gold. Anyone could create an account and convert their gold and silver to e-gold.

When Satoshi wrote Bitcoin Whitepaper, all ingredients needed to build Bitcoin already existed. The first working cryptocurrency would have come into existence even if Satoshi had not done it. Satoshi was a genius, but not a superhuman. His whitepaper is incredibly easy to understand, which is why it attracted many people. This is partly because all the complexity was already taken care of in the earlier works done by equally smart people.

Satoshi must be credited for not just creating the first cryptocurrency, which anyway would have happened, but for designing it with the right mindset, which has allowed it to dominate cryptocurrency market in terms of market capitalization even after 13 years and probably will dominate for years to come.

In the end, Satoshi probably had all the information about what was happening in cryptography and what had happened to anyone who launched a currency or payment system. He was smart enough to create something truly decentralized and censorship-resistant and simultaneously hide his own identity.

# [The rise of Bitcoin](#toc.xhtml#s33a)

On 31^(st) October 2008, *Satoshi Nakamoto* published Bitcoin Whitepaper titled *Bitcoin: A Peer-to-Peer Electronic Cash System* on the cryptography mailing list at metzdowd.com. On 9^(th) January 2009, Satoshi released Bitcoin code on *SourceForge* and launched the network by mining the second and further blocks. The first block is not mined as it is hardcoded in the code itself and the first block of any blockchain is called the genesis block. Satoshi worked with quite a few smart people in cryptography, including *Hal Finney, Adam Back, Gavin Andresen*. Satoshi worked closely with Hal Finney, and the first transaction was sent on 12^(th) January between them.

It is remarkable how quickly Bitcoin got noticed. On 5^(th) October, the world’s first Bitcoin exchange was launched, and $1 could buy 1309.03 BTC. On 22^(nd) May 2010, two Pizzas were bought with 10000![](images/Bitcoin.jpg). This day is remembered as Bitcoin Pizza Day.

It is not true that the Bitcoin network never stopped working. It happened twice. The first time, an inflation bug (a bug that allows an increase in supply of a cryptocurrency) was found, but before it could be fixed, someone used it to generate bitcoin. This was resolved within hours, making the extra bitcoin invalid. The second time was in March 2013, when a Bitcoin software upgrade resulted in a network split. It was soon resolved as Pools and node owners actively moved back to the older version.

Initially, anyone could easily mine bitcoin on personal computers or laptops. And since there were only a few miners, it would not take much time to mine a block. However, as more people started mining, it took a long time to mine a block. On 27^(th) November 2010^, Slushpool launched the first mining pool in which miners would jointly mine a block, and once mined, the reward would be shared among miners based on their contribution. Later, mining pools became the only viable way to mine a block, and few mining pools almost completely took over the computational power of the network. Even today, this is the case. In July 2014, a mining pool briefly acquired more than 50% mining power of the network. The mining pool did not try to do a 51% mining attack, but it realized that this could affect the overall creditability of the network and committed to never crossing 40% of the total mining power.

Namecoin was the first cryptocurrency launched after Bitcoin. In the same year, Litecoin was also launched, and it continues to be popular even today. In 2013, when ASIC miners hit the market, computational requirements became too high, making mining difficult for smaller players. At that time, many miners switched to mining Namecoins, Litecoins, and other coins.

In May 2011, Bitpay became the first payment processor that allowed merchants to accept Bitcoin as payment.

On 28^(th) March 2013, the first US cryptocurrency regulations were put in place. The FinCEN brought regulations.

On 29^(th) October 2013, the first Bitcoin ATM opened in Vancouver, Canada.

Bitcoin exchanges has a history of hacking events, and a lot of people have lost their bitcoin. However, the biggest impact happened to bitcoin prices and confidence when MtGox was hacked in February 2014. It was the biggest Bitcoin exchange at the time.

On 10^(th) June 2014, *Mike Hearn* created BIP 64. In December, he released the software leading to the first hardfork and creation of Bitcoin XT.

In 2010, Satoshi secretly introduced a 1MB limit to the block size. Since each block is generated every 10 min, the 1MB block size limit was the big limiting factor in Bitcoin scaling. With a 1MB limit, Bitcoin could, at most, have 7 transactions per second. Some developers proposed to increase this limit as early as 2011.

In 2015, BIP 100 and BIP101 were introduced to enhance that limit. Many Bitcoin hard forks were related to an increase in this limit. With segregated witness softfork, this limit was increased.

Bitcoin had multiple hype cycles when prices jumped and dropped. The hype cycles were seen in 2011, twice in 2013, and in 2017, . These hype cycles have given Bitcoin media coverage and helped improve adoption. In August 2020, MicroStrategy became the first public traded company to hold bitcoin in its treasury. This has given Bitcoin legitimacy as store-of-value.

Here is an illustration of the timeline of events and achievements Bitcoin made since then:

![](images/Figure-2.2.jpg)

**Figure 2.2:** Timeline and milestones since the publication of Bitcoin Whitepaper

# [Defining Bitcoin](#toc.xhtml#s34a)

Bitcoin is not one thing but two, and the following are their definitions:

**Bitcoin is a permissionless, verifiable, peer-to-peer, supply inelastic and evolutionary asset.**

and

**A decentralized network designed to create, store and transfer bitcoin in an insecure environment without intermediaries.**

Bitcoin is also designed to scale and have layers above and side of it. Bitcoin has the highest accumulated proof –of work compared with any existing network. In future applications, assets, currencies, and tokens will be able to secure themselves and have partial backing of value from Bitcoin. Due to its design, open-source, decentralized nature, value, and accumulated proof of work, it might someday become an essential part of the internet. In the future, Bitcoin may have the following definition:

**A layer of trust within the internet.**

# [Byzantine general problem](#toc.xhtml#s35a)

The Bitcoin network uses a proof –of work consensus mechanism to generate bitcoin and uses a script, cryptography, and proof –of work to transfer it from subsequent receivers.

The Bitcoin proof –of work consensus mechanism tries to build consensus in a hostile environment where attackers may be collaborating to attack the network by including or excluding messages having transaction information that could help them. This is the reason this book has a tagline:

**Building trust in a trustless environment**

This is, essentially, a solution to the 1982 paper titled, *The Byzantine Generals Problem* published by *Leslie Lamport, Robert Shostak, and Marshall Pease*. It’s an important game theory problem, and the condition of the problem is as follows:

1.  Byzantine army is planning an attack on a city.
2.  The Byzantine army has several divisions, each of which is commanded by a general. These generals are stationed outside the city at distances.
3.  No two generals can communicate with each other directly, and they need to rely on couriers who transfer their messages.
4.  To win an attack on the city, they need to establish a consensus on the plan of attack. This requires a lot of correspondence.
5.  Now the problem is that there may be traitors among them who will try to sabotage the plan by spreading misinformation.
6.  A coordinated attack will lead to victory.
7.  A non-coordinated attack will be lost.

The following is the pictorial representation of the winning and losing condition of The Byzantine general problem:

![](images/Figure-2.3.jpg)

**Figure 2.3:** Illustration of Byzantine general problem

In the case of Bitcoin, most participating nodes agree on transaction messages, their order, and linking with previously accepted messages based on defined consensus rules. Each node acts as the general here. Unlike the Byzantine general problem, the aim is to protect the network. If the network is sabotaged, then the attacker (traitor) can double spend, exclude or include messages, and change the order of messages. This will affect the credit value of the network.

Now, we understand how the Bitcoin consensus mechanism essentially solves The Byzantine general problem.

The same Byzantine general problem can be considered to have the following characteristics to use for similar problems requiring cooperation:

1.  Any number of generals can be traitors if a majority is cooperating. This makes it a democratic system.
2.  Each general may have a different role to play to succeed in the plan. This may be agreed upon.
3.  Consensus is reached without the need of a leader.

This has implications on the real world because in most matters’ when an agreement needs to be made, a central trusted authority is needed. So, the implications of this go beyond payments.

As an example, if we want to build a cab aggregator network, there will be riders, drivers, car owners, and the car itself. All four of them need to get into an agreement in the form of consensus rules written in the form of smart contract, where:

1.  The driver will carry the rider to his specific location in the least time-consuming path,
2.  The car will be maintained by the owner and gas will be filled whenever needed by the driver,
3.  The rider will pay the car owner after reaching the destination, and
4.  The driver will get his monthly salary from the car owner.

Even though there is a clear distinction between driver, rider, car owner, and car, once the rule of agreement is established, each one is equal in rank. The records of each transaction are kept in an immutable sequence of records, ensuring easy audit. No central authority is needed to lead the platform.

The following figure shows a car aggregator network:

![](images/Figure-2.4.jpg)

**Figure 2.4:** Decentralized car aggregator network

# [Bitcoin as a solution to Byzantines general problem](#toc.xhtml#s36a)

In order to solve this problem, Bitcoin needs to:

*   Maintain all transactions in an immutable sequence of records in the order of their occurrence.
*   Make sure that transactions are easily verifiable in terms of immutability and order and any consensus rule or contract.
*   Be able to resolve any race condition that may arise because two records are generated at the same time.
*   Move messages quickly so that the race condition mentioned earlier does not make confirmation time longer.

This is the reason Bitcoin has the following characteristics:

*   **Proof –of work** makes transactions immutable by attaching cost on its creation.
*   **Blockchain** is made up of blocks having transactions such that each block knows the previous block, and each block is arranged in time sequence.
*   Bitcoin proof –of work algorithm makes it **easy to verify** blocks but exceedingly difficult to create them. This ensures that Transactions are propagated fast enough so that race condition leading to the creation of blocks by two distant nodes simultaneously is solved by the time the block reaches a depth of six.
*   Each transaction is linked to a previous transaction by **cryptography** and script enforcing order, consensus rules, and contract.
*   **Validating nodes** or Full nodes are like observers watching matches played by the Bitcoin miners. They don’t confirm a transaction by creating a block and adding the transaction to the block by the proof –of work algorithm. Instead, they verify all the consensus rules, smart contract clauses, time sequence of blocks, sending of bitcoin from sender to receiver, and funding of bitcoin from the previous transaction.

# [Bitcoin property as a digital asset](#toc.xhtml#s37a)

The Bitcoin network needs to collect fees so that it can fund the cost of mining as mining is the proof –of work that secures the network. Satoshi devised an intelligent way to achieve this:

*   When a miner solves the cryptographic puzzle needed to mine a block, he is paid in newly minted bitcoin. This reward reduces by half after every 210,000 blocks are mined, that is, around 4 years.
*   Later, as the network becomes valuable, miners will charge fees to include the transaction in a block.

This ensures that bitcoin supply is perfectly inelastic, which means its supply is predetermined. Bitcoin supply is also reducing at an exponential rate, which means when it becomes popular, there won’t be enough supply.

Block reward has reduced from 50 ![](images/Bitcoin.jpg)at the inception to 6.25 ![](images/Bitcoin.jpg)at the time of authoring this book, and network fees have gone up significantly from zero at the beginning. This has made Bitcoin less attractive for speculation.

Bitcoin is also highly divisible with satoshi as the lowest denomination, which has the following value:

![](images/53.jpg)

Bitcoin does not require intermediaries, which makes it the digital equivalent of physical cash.

Bitcoin is neither a privacy coin, nor does it disclose your identity. Characteristics of privacy in Bitcoin can be understood as follows:

*   Bitcoin does not link a person to an identity; instead, bitcoins are attached to addresses.
*   Bitcoin can be bought from exchanges, miners, or a person directly. This makes bitcoin difficult to track.
*   Bitcoin can be bought from exchanges. Most exchanges follow KYC norms and so, link identity with the address. When we transfer our bitcoin from an exchange, it is aware of receiving addresses.
*   All transactions in the Bitcoin blockchain are transparent, contain information such as the previous transaction, paid to address, and amount of funding address and receiving address. This way, each transaction has a history that can leave clues of the sender or receivers’ identity.
*   There are a few techniques that can make finding identity quite difficult.

Overall, Bitcoin privacy is a very personal thing. Consequently, when government regulates bitcoin and incentivizes its use, Bitcoin addresses become more transparent and easier to track, but when government penalizes its users, Bitcoin addresses become opaque and more difficult to track. This makes Bitcoin censorship-resistant.

Bitcoin is on the network, and wallets only hold its private keys. This makes bitcoin location-independent and so, easily transferable between people at opposite ends of the globe.

Bitcoin value is decided at exchanges. Since it is easy to transfer bitcoin anywhere in the world, its value in every currency is nearly the same. In some cases, when government imposes restrictions on cryptocurrency or when there is currency control on local currency, bitcoin value can be a bit higher than the international value.

Bitcoin is a number on the network associated with an address. If an address is linked with criminals or hackers, exchanges may block such addresses, and it can affect the value of that bitcoin in the next transaction. But in a later transaction, if it is mixed with other bitcoin, then it becomes indistinguishable from any other coin. Since bitcoin is almost never distinguishable, it makes them quite fungible.

All valid Bitcoin transactions are either in mempool (in memory of each full node on the Bitcoin network) or in blockchain. These are verified by nodes. Anyone can view a transaction by either having a node or by looking at one of the popular websites.

This gives bitcoin the following properties:

*   Scarce
*   Divisible
*   Censorship-resistant
*   Easily transferable
*   Fungible
*   Verifiable

Also, it makes Bitcoin:

*   Less suitable for speculation
*   More suitable for holding or saving

# [Conclusion](#toc.xhtml#s38a)

In this chapter, we looked at the history of developments in cryptography that led to the development of Bitcoin. Then, we looked at the timeline since the time whitepaper was published till the authoring of this book.

After this, we defined Bitcoin and the game theory problem the Byzantine generals problem it solves. You learned how it solves the game theory problem and how the solution to the problem can change the fundamental structure of organizations. We then used this knowledge to list the fundamental characteristics of bitcoin.

In the next chapter, you will understand the structure of the Bitcoin network. We will relate each part of the network to the fundamentals of Bitcoin we learned in this chapter.

# [Points to remember](#toc.xhtml#s39a)

*   Cryptographic advancements have been happening for almost 3 decades prior to Bitcoin led to its development.
*   DigiCash was the first known working cryptocurrency launched in 1989.
*   W.S. Stornetta, D. Bayer, and S. Haber created the first blockchain.
*   Wei Dai proposed the idea of b-Money, which conceptualized proof –of work and proof –of stake.
*   Proof of work makes transactions immutable by attaching cost on its creation.

# [Questions](#toc.xhtml#s40a)

1.  Explain why bitcoin is more suitable for saving and less suitable for speculation.
2.  Explain each of the following properties and how these are related to bitcoin currency: 
    1.  Scarce
    2.  Divisible
    3.  Censorship-resistant
    4.  Easily transferable
    5.  Fungible
    6.  Verifiable
3.  Explain each of the following elements of Bitcoin: 
    1.  Proof –of work
    2.  Blockchain
    3.  Validating nodes
4.  Fill in the blanks: 
    1.  RPOW uses \_\_\_\_\_\_\_\_\_\_ as proof –of work token.
    2.  \_\_\_\_\_\_\_\_\_\_ proposed the idea of smart contract.
    3.  Bitcoin uses \_\_\_\_\_\_\_\_\_\_\_\_ asymmetric cryptography.
    4.  \_\_\_\_\_\_\_\_\_ is the first public traded company to hold bitcoin in their treasury.
    5.  1 MB block size limit was set by \_\_\_\_\_\_\_\_\_\_.
5.  True/False 
    1.  Bitcoin blocks are easy to verify but extremely difficult to mine.
    2.  Bitcoin is not the most secure network.
    3.  Bitcoin is a currency and not an asset.

# [CHAPTER 3](#toc.xhtml#c03)

# [Understanding the Bitcoin Network](#toc.xhtml#c03)

In the previous chapter, you learned about technological developments that led to the development of Bitcoin. You also learned about the events that happened since the Bitcoin Whitepaper was written and tried to understand the need for Bitcoin, the problem it solves, and how solving the problem may change the world.

When we pay bitcoin from our wallet to someone else’s address, a transaction is created and broadcasted on the Bitcoin network. This goes into mempool, and a miner mines a block in which this transaction gets included. To make this happen, the Bitcoin network needs to communicate with each other and publish these transactions and blocks on the network. Bitcoin network plays an important role in making the network decentralized.

In this chapter, we will first learn about the different types of nodes that constitute the Bitcoin network. We will understand why different types of nodes are required and how they interact with each other. We will then understand the Bitcoin consensus network, its building blocks, and why each component of the consensus network is required.

# [Structure](#toc.xhtml#s41a)

In this chapter, we will cover the following topics:

*   Bitcoin physical network topology 
    *   Mining nodes 
        *   Pool mining
        *   Solo mining
    *   Full node
    *   Simplified Payment Verification (SPV)
*   Bitcoin consensus network 
    *   Transactions
    *   Blockchain
    *   Consensus rules
    *   Proof –of work (PoW)
    *   Verifying nodes
    *   Mempool
    *   Cryptography
    *   Gossip protocol
*   Bitcoin network security

# [Objectives](#toc.xhtml#s42a)

The objective of this chapter is to give readers a high-level understanding of the Bitcoin network. This will give you an understanding of the depth of Bitcoin’s core concepts, like decentralization and censorship resistance, are integrated into its design. Additionally, it will help you visualize and grasp the content in the upcoming chapters, where we will go deeper into the technology and do programming.

It will also help you understand what might be going on in the background when you make a payment and how transactions get included in the blockchain.

# [Bitcoin physical network topology](#toc.xhtml#s43a)

The Bitcoin network consists of nodes that interact with each other to send and receive transactions and blocks. A node can join or leave the Bitcoin network anytime.

A transaction is like a ledger entry containing the source of funding, the receiver of funds, and the amount transferred. These transactions are added to the block by a miner and broadcast to other nodes.

The following illustration shows Bitcoin network topology:

![](images/Figure-3.1.jpg)

**Figure 3.1:** Bitcoin network topology

In the preceding figure, miners create a block and forward it to other nodes. A solo miner also receives blocks because it is also a full node. Full nodes are responsible for verifying transactions and blocks and forwarding them. SPV nodes are lightweight nodes that depend on the full nodes for receiving the necessary information.

Pool mining nodes connect with the mining pool server. The pool mining nodes receive jobs from the server and try to mine blocks based on the job they receive. If it is successful, Pool miner sends the block to the server. The mining pool server also receives blocks and transactions from other nodes, which is why there is an arrow from the pool mining node to the mining pool server. Bitcoin network is otherwise peer-to-peer and non-hierarchical.

# [Mining nodes](#toc.xhtml#s44a)

Mining nodes compete in solving a cryptographic puzzle and whichever node solves the puzzle is able to construct a block with choosen transactions. A transaction gets confirmed when it gets included in a block. So, mining is an act of transaction confirmation.

Solving a cryptographic puzzle to confirm a transaction by using computation power is called **proof –of work**.

A miner can decide to do solo mining or join a mining pool.

The following is an image of mining equipment:

![](images/Figure-3.2.jpg)

**Figure 3.2:** Mining equipment in action

# [Pool mining](#toc.xhtml#s45a)

Mining is only profitable nowadays if done in a pool. In this case, miners join a mining pool to collaborate in the mining effort. Each miner in the pool tries to solve a cryptographic puzzle, and the mining pool is aware of the computational power contributed by the miner. Miners solve the cryptographic puzzle, and the mining pool gets the block reward. The mining pool then shares the block reward with all the miners in the pool by dividing it based on their contribution to computational power. Miners who solve the cryptographic puzzle do not get any special advantage. This setup is beneficial for all the miners because solving the puzzle is based on probability determined by the contribution in computation power. Miners do not interact with the network directly; instead, they are given a job by the mining pool server.

# [Solo mining](#toc.xhtml#s46a)

Bitcoin computation requirement has become so high that it is virtually impossible to be able to mine blocks individually. However, there is one benefit. Currently, there are a few mining pools that have almost all the computational power of the network. It will only take a few mining pools to join hands, and the Bitcoin network will have a 51% attack. If most nodes were solo miners, this was not possible. So, by doing solo mining, we can make mining more decentralized.

# [Full node](#toc.xhtml#s47a)

Full nodes are the verifying nodes that keep the copy of the blockchain and verify all the transactions and blocks received by them. They also forward blocks and transactions to other nodes.

# [Simplified Payment Verification (SPV)](#toc.xhtml#s48a)

SPV nodes are lightweight nodes, which means they do not maintain the whole blockchain and cannot verify a block without the help of the Full node. SPVs require very little disk space and can be set up on embedded devices or can execute in memory, making them cheaper to maintain and carry.

# [Bitcoin consensus network](#toc.xhtml#s49a)

Bitcoin consensus network is based on the proof –of work consensus mechanism. Transactions are created and published on the network using gossip protocol with the help of a node. Verifying nodes or full nodes verify the received transaction and then add it to their mempool. A miner uses their computational power to solve a cryptographic puzzle in order to create a block containing the transactions it wants to include in the block. The block is chained with the previous block. The created block is the proof –of work, and the chain of blocks forms blockchain. The miner then publishes the newly created block to the Bitcoin network using the gossip protocol. Verifying nodes then receive the block, verify it based on consensus rules, and forward it to the connected nodes again using the gossip protocol. All these activities use cryptography.

Here’s the illustration of the Bitcoin consensus network:

![](images/Figure-3.3.jpg)

**Figure 3.3:** Bitcoin Consensus Network

Key components of the Bitcoin consensus network are as follows:

*   Transactions
*   Blockchain
*   Consensus rules
*   Proof –of work
*   Validating nodes
*   Mempool
*   Cryptography
*   Gossip protocol

These are explained in the following sections.

# [Transactions](#toc.xhtml#s50a)

Transaction is the single record of spending. It contains three things:

*   Sources of funding
*   Receivers of the fund
*   The amount received by each of the receivers

The following is an illustration of transaction:

![](images/Figure-3.4.jpg)

**Figure 3.4:** Bitcoin transaction funding and payments

# [Blockchain](#toc.xhtml#s51a)

Blockchain is the immutable sequence of blocks that records transactions. The chain of blocks also is in time sequence. Each block is linked to its previous block. The end of the chain is the recent block.

The following is the illustration of blockchain based on what you have learned:

![](images/Figure-3.5.jpg)

**Figure 3.5:** Structure of a blockchain

# [Consensus rules](#toc.xhtml#s52a)

Bitcoin network, like a network protocol, has agreed-upon rules for blocks and transactions. These rules are supposed to be protected by the Miners through the proof –of work consensus mechanism.

# [Proof of work (PoW)](#toc.xhtml#s53a)

Proof –of work or PoW is a mechanism that was created to prevent denial-of-service attacks by forcing the attacker to spend computational power. This makes denial-of-service attack non-viable for the attacker. Bitcoin uses proof –of work to make double-spending very difficult and costly.

This can be understood with the following analogy:

In the olden times, there were houses, temples, wells, etc., which were easy to replicate, but there were also monuments, fortresses, and so on, which were unique. Monuments such as the pyramids in Egypt, the Great Wall of China, and the Kailasa Temple in Ellora, India, are among the greatest monuments that, after hundreds of years, are still very difficult to replicate. The thing that is common to all of them is the difficulty of making them. The difficulty has kept them unique over centuries. The structures themselves are the evidence of the hard work that has been undertaken to construct them. The evidence of work is called proof –of work.

The following figure shows two of the famous monuments:

![](images/Figure-3.6.jpg)

**Figure 3.6:** Unique and famous monuments

Each miner competes in computational power to solve the cryptographic puzzle and create a block of the transaction as the next block in the blockchain. After a certain number of blocks are created, the difficulty of the cryptographic puzzle is adjusted to increase or decrease the average time to solve a cryptographic puzzle. Due to this mining equipment, manufacturing companies also compete in their cost-effectiveness. This battle in the mining arena keeps the network secure and protects it from double-spending.

**It is a mechanism in which a party needs to prove to the verifier that it has performed the desired work (or computational power) in order to be allowed to perform some tasks.**

The difficulty to change any block increases exponentially as the block gets deeper into the chain. Even though miners are competing to create a block, they are agreeing to the terms of consensus rules. This is the reason why it is called the *proof –of work* consensus mechanism. Many cryptocurrencies and blockchain technologies use other forms of consensus mechanisms, such as *proof –of stake, proof –of authority, practical Byzantine fault tolerance,* and so on.

Mining can be defined as p*roof* –*of* w*ork in action*.

We know that miners join and form a pool. A few mining pools control most of the network computational power. If two to three top miners join, they can out-compete the rest of the miners.

In July 2014, *Ghash.io* reached more than half of the network computational power, but it later agreed that it will never cross the 50% computational power. It is important to understand why we never had such a scenario since and why any miner would agree not to take over the network.

Mining also adds value to the network, which means even though miners can join and block transactions from specific countries or exchanges, they will not do anything that will get noticed and will affect the network that is their source of earning.

# [Validating nodes](#toc.xhtml#s54a)

Bitcoin doesn’t fully depend on mining nodes to protect against double-spending; instead, it also has validating nodes that verify all the transactions and blocks received. The verifying nodes are also called full nodes, and these nodes further broadcast transactions and blocks.

# [Mempool](#toc.xhtml#s55a)

Mempool is the in-memory store for an unconfirmed transaction. A miner picks up transactions from mempool, and only valid transactions are stored in mempool. A transaction may expire because it did not get included in the blockchain for a very long time. A mempool transaction is not confirmed and can become invalid due to race conditions.

# [Cryptography](#toc.xhtml#s56a)

Cryptography is the heart of Bitcoin. It is used in proof –of work, transaction, blockchain, and verification.

Here are the uses of cryptography in the Bitcoin network:

*   Mining nodes need to solve the cryptographic puzzle in order to create a block of transactions.
*   Each block uses cryptography to protect all transactions from modification.
*   Each block uses the cryptographic hash to protect the chain of blocks from modification.
*   The transaction uses cryptography to unlock funds from the source and lock it for the receiver to claim.

# [Gossip protocol](#toc.xhtml#s57a)

Bitcoin transactions and blocks need to reach quickly to almost all nodes. Bitcoin nodes are always listening to the connected nodes and make them aware of the blocks in the Bitcoin blockchain it has. When a block or a transaction is received by a node, it verifies it according to consensus rules and then sends it to the nodes which need it. Gossip protocol is the method of communication between nodes using messages containing command and payload.

Here’s an illustration of the gossip protocol in message broadcast:

![](images/Figure-3.7.jpg)

**Figure 3.7:** Simple representation of gossip protocol in a message broadcast

# [Bitcoin network security](#toc.xhtml#s58a)

Securing a network is not only a mathematical or cryptographic problem but also a game theory problem. Bitcoin network is secured by both cryptography and game theory. So, there are many factors that work together to secure the network:

*   Mining makes it difficult to modify a block, and the difficulty increases exponentially as the block gets deeper into the blockchain.
*   Mining difficulty adds to the value of the network. Its value is not only in terms of computational power but also in terms of cost and time.
*   Mining equipment companies compete in the cost-effectiveness of their equipment.
*   Verifying nodes watch the network and make sure that the network behaves as expected.
*   Many block exploration websites and independent enthusiasts are also observing the network in different ways. They are constantly observing nodes, blockchain, and mempool.

# [Conclusion](#toc.xhtml#s59a)

In this chapter, you learned the network topology of the Bitcoin network. You learned about the different types of nodes that are present in the Bitcoin network and their roles and need. Then, you understood how the Bitcoin consensus mechanism works and what the different components that form the Bitcoin consensus network are. We also covered each of those components to give us a fair understanding of the structure and functioning of the Bitcoin network without getting in-depth into its real functioning.

In the next chapter, you will understand how bitcoin is used in the real world and learn about the regulation on use of bitcoin in different countries.

# [Points to remember](#toc.xhtml#s60a)

*   Mining is proof –of work in action.
*   The Bitcoin network consists of mining pool server, pool miner nodes, solo miners, full nodes, and SPV nodes.
*   Pool Miner nodes do not interact with the Bitcoin network directly; instead, they depend on the mining pool server for jobs.
*   Solo mining has a negligible chance in solving a cryptographic puzzle.
*   Full nodes are also called validating nodes as they verify blocks and transactions based on consensus rules.
*   Gossip protocol is the method of communication between nodes using messages containing command and payload.

# [Questions](#toc.xhtml#s61a)

1.  How is block validation different from block confirmation? Which node is responsible for block validation, and which one is for block confirmation?
2.  What are the top four mining pools, and what is their current share of network computational power?
3.  If you are planning to buy Bitcoin mining equipment, what parameters will you look for, and how will you judge which equipment is better for you?
4.  If a miner cannot accommodate all received transactions in a mempool into the next block, on what basis will it select a transaction for adding to the next block?
5.  Fill in the blanks: 
    1.  The Bitcoin network is a \_\_\_\_\_\_\_\_\_\_\_\_ network, which means there are no servers and clients and no hierarchy.
    2.  In pool mining, \_\_\_\_\_\_\_\_\_ solves cryptographic puzzle and \_\_\_\_\_\_\_\_\_ connects with Bitcoin network for blocks.
    3.  SPV needs \_\_\_\_\_\_\_\_\_\_\_\_ node to verify incoming blocks.
6.  True/False: 
    1.  The mining node does not require mempool.
    2.  Nodes can join and leave the Bitcoin network anytime.
    3.  Each full node maintains a copy of the blockchain.

# [CHAPTER 4](#toc.xhtml#c04)

# [Bitcoin in the Real World](#toc.xhtml#c04)

In the previous chapter, you learned about the Bitcoin network structure and the basics of consensus networks. This gave us the basic idea of the working and structure of the Bitcoin network.

In this chapter, you will understand how bitcoin is used by different people and organizations. You will learn the diverse ways we interact with the network. You will learn how traders, investors, businesses, and digital nomads use bitcoin. Additonally, you will learn about the different types of exchanges, and a bit about bitcoin regulations.

# [Structure](#toc.xhtml#s62a)

In this chapter, we will cover the following topics:

*   Different types of exchanges
*   Bitcoin use cases 
    *   Trading in bitcoin
    *   Investing and saving in bitcoin 
        *   Accepting bitcoins by an online merchant
        *   Accepting bitcoins at a brick-and-mortar store
        *   Paying or receiving bitcoin as salary
        *   Using bitcoins for expenses and traveling
        *   Bitcoin for remittance
        *   Bitcoin for social cause
        *   Mining bitcoins
*   Bitcoin and cryptocurrency regulations

# [Objectives](#toc.xhtml#s63a)

The primary objective of this chapter is to give readers a fair idea of how Bitcoin fits into the real world and how they can use it. We will look at the Bitcoin ecosystem from different viewpoints. Though the book is aimed at technical audience, we believe that solutions are always built for the audience. So, knowing the needs of the audience helps build the right solutions. Additionally, this helps widen our perspective of Bitcoin technology.

Since the previous chapter focused on the structure and working of networks and this chapter will focus on Bitcoin’s linkage with the real world, you will have an inner as well as an outer view of the Bitcoin network and currency/asset after reading this chapter.

# [Different types of exchanges](#toc.xhtml#s64a)

Cryptocurrency exchanges allow cryptocurrencies to be exchanged for other cryptocurrencies or regular currencies. Cryptocurrency exchanges can be classified in several ways based on different factors.

Exchanges can also be classified as follows based on custody of cryptocurrencies:

*   **Custodial exchange**: Exchange that hold bitcoins in a wallet
*   **Non-custodial exchange**: Exchange that do not hold bitcoin in a wallet

At exchanges, sellers need to find buyers to sell their cryptocurrency. This can be done with the escrow method using exchange as a platform, or this can be hidden from users, and exchanges take care of moving cryptocurrency between buyers and sellers. These types of exchanges can be classified as follows:

*   **Peer-to-peer exchanges**: In peer-to-peer exchange, the exchange works as an escrow. Till payment is received by a seller, the exchange holds cryptocurrency to be sold in an escrow account. Once the seller confirms that they have received the desired money, the exchange releases cryptocurrency to the buyer’s account. Otherwise, this may go into dispute, and the exchange employs people to individually handle disputes. A buyer or a seller publish their price, and the other party browses to select the right candidate based on price, likes, testimonies, and recommendations. *Paxful and* L*ocal*B*itcoins* are examples of peer-to-peer exchanges.
*   **Retail exchanges**: Retail exchanges are the most common form of exchanges. They allow buyers to *bid* for the highest price they can pay for cryptocurrency while allowing sellers to *ask* for the lowest price it can accept for their cryptocurrency. The rest is managed by the exchange. These exchanges are custodial and maintain a spread between the buy and sell to manage profitability under market volatility. Zebpay, WazirX, Unocoin, Coinbase, and Kraken are some examples of retail exchanges.
*   **Instant exchangers**: These exchanges have fixed buy and sell prices and need not be custodial. This makes them simple to implement, and it is quite easy to run such exchanges. InstaBitco.in, Changelly, and ShapeShift are examples of instant exchanges. 
    *   **Bitcoin ATM:** These are instant exchangers that convert cash to bitcoin or can disperse cash after receiving bitcoins.

Retail exchanges play an important role in giving cryptocurrencies their value. These are also the most trader-friendly as these exchanges provide real-time charts and APIs for developing trading apps. Peer-to-peer exchanges, on the other hand, provide some privacy and allow payments in cash.

Exchanges can also be classified as follows:

*   **Centralized exchanges**: Centralized exchanges are hosted and managed by a company or an organization that takes profits, provides customer case, and solve disputes if they arise.
*   **Decentralized exchanges (DEX)**: Decentralized exchanges are non-managed peer-to-peer exchanges. These are also non-custodial exchanges. These are launched as **Decentralized Autonomous Organizations** or **DAO**, and because of their decentralized nature, these exchanges provide censorship resistance. They do not require KYC or AML. *Bisq* is an example of peer-to-peer exchange.

# [Bitcoin use cases](#toc.xhtml#s65a)

In this topic, you will learn the different ways traders, investors, travelers, freelancers, and miners interact with the Bitcoin network.

# [Trading in bitcoin](#toc.xhtml#s66a)

This topic is not about trading advice; instead, you will understand how a trader can trade in bitcoin.

The objective of trading is to earn money from the volatility of trading instruments. This is done with a lot of analysis of the current and historical price movements of cryptocurrencies and collecting indicators from real events like economic and political events and conditions.

So, a trader needs to do the following:

*   Analyse historical and current price movements.
*   Time the movement of money between currency, stable coins, and other cryptocurrencies based on price or other events.
*   Add and withdraw money.

As a result, traders require exchanges that provide the following features:

*   Multiple cryptocurrencies
*   Stable currencies and easy movement between cryptocurrency and stable currencies such as EUR, USD, YEN, or GBP
*   Ability to place bid and ask
*   Custodial wallets

Web APIs to buy, sell, and bid nd ask could be useful

So, a non-custodial exchange or P2P exchange does not help a trader. A trader needs a custodial exchange that provides them with the ability to place a bid and ask. Support for trading APIs is quite useful as it can integrate into the trader’s applications, which can get necessary data from the exchange to decide target price for bid and ask or move currencies into other cryptocurrencies, stable currencies, or stable cryptocurrencies.

The following is the Bitcoin’s historical price chart:

![](images/Figure-4.1.jpg)

**Figure 4.1:** Bitcoin’s historical price chart

# [Investing and saving in bitcoin](#toc.xhtml#s67a)

An investor is interested in long-term gains, while a saver sees Bitcoin as store-of-value, which can be useful for their children and grandchildren. Investors and savers are not focused on short-term price fluctuations. For them, security is a bigger concern, and small differences in price do not matter much.

An investor or a saver needs the following:

*   Hold bitcoins in a secure vault or wallet
*   Have private keys in their control
*   An investor may additionally want to have a future price target for selling

So, an investor or a trader will buy bitcoin from a reliable and secure exchange and move the bitcoin to their hardware wallet. And whenever they need to sell, they can move the required bitcoin to exchange again and sell it.

Here’s an illustration of investors buying and selling bitcoins:

![](images/Figure-4.2.jpg)

**Figure 4.2:** An investor buying and selling in a retail exchange

# [Accepting bitcoins by an online merchant](#toc.xhtml#s68a)

It is easy to accept bitcoins as a merchant: just place a Bitcoin address and its QR code on your website. The problem with this approach is that you will not know who paid and how much, and it is not recommended that you accept all payments on one address.

There are quite a few payment processors that can be integrated into your websites, such as Coinbase Commerce, coingate, btcpay, bitpay, etc. Alternatively, if you are creating your website, you can use Shopify or WooCommerce to build websites that provide options to integrate with many popular payment processors.

Here is an illustration of an online website with cryptocurrency integration:

![](images/Figure-4.3.jpg)

**Figure 4.3:** Website integration with third-party Payment Processor

BTCPay is an open-source, self-hosted payment processor that can integrate with a few popular hardware wallets. There are benefits of using a self-hosted open-source payment processor integrated with a hardware wallet. We may need to use a fixed Bitcoin address, or we may need to use a wallet service provided by a centralized payment processor. Online wallets are at risk of hacking.

On the other hand, a centralized payment processor is convenient and often cheaper as a self-hosted server will need cloud hosting. Additionally, BTCPay only supports Bitcoin payments, which are quite limiting for an online store.

The following is an illustration of a self-hosted payment processor integrated with a hardware wallet:

![](images/Figure-4.4.jpg)

**Figure 4.4:** Website integration with self-hosted Payment Processor

Big brands and aggregator companies that have frequent transactions with suppliers, service providers, and customers can have payment channels over Lightning Networks. This will allow them to reduce the cost of individual transactions.

**Lightning Network**

Lightning Network is a layer two solution over the Bitcoin network. In the Lightning Network, a channel between sender and receiver is created, on which bitcoins are locked.

![](images/Figure-4.5.jpg)

**Figure 4.5:** Creation of lightning channel

Then, the sender can send as long as there is balance in the channel.

![](images/Figure-4.6.jpg)

**Figure 4.6:** Using channel to make payments

The sender or receiver can close the channel anytime. On closing the channel, the accumulated result of all previous transactions gets to the Bitcoin blockchain, and at this time, network fees must be paid.

![](images/Figure-4.7.jpg)

**Figure 4.7:** Closing the channel and publishing the final balance to blockchain

The more transactions happen on this channel before closing, the lesser is the effective fees per transaction. This reduces effective network fees, making smaller value transactions viable.

# [Accepting bitcoins at a brick-and-mortar store](#toc.xhtml#s69a)

Bitcoin is no more suitable for buying coffee as the transaction fee has gone up quite significantly. While authoring this book, the average transaction fee is $15. It is still viable for buying costlier items.

Since there are only a few people who would pay in bitcoins, the best approach is to place a QR code of the Bitcoin address and change it every day.

Alternatively, Bitcoin wallets, such as Samourai wallet, support Reusable Payment Codes called PayNyms, which can be used for receiving payments. This could be an alternative approach only as PayNyms are not supported by most wallets.

The following is the illustration of a brick-and-mortar store receiving payments in bitcoin using PayNyms:

![](images/Figure-4.8.jpg)

**Figure 4.8:** Using PayNym supported Mobile wallets at a retail store

# [Paying or receiving bitcoin as salary](#toc.xhtml#s70a)

There are many around the world who are paid in cryptocurrencies. Most of them are independent contractors or freelancers who are location independent and require just an internet connection and a laptop to work. They can generate Bitcoin addresses from this hardware and receive payments in their wallets.

This is great for one-to-one payments but is difficult for a company that has a dozen employees. Plus, not all employees will be interested in one type of currency. Each employee can require a different type of currency, such as local currency or bitcoin, Ethereum or XRP.

Bitwage is one application that can make it work. It allows employers to pay in whichever currency that suits them, and the employee can receive the amount in whichever currency they need. Following is the illustration of wage payment distribution between employer and employees:

![](images/Figure-4.9.jpg)

**Figure 4.9:** Employer paying to the globally distributed team using BitWage

Bitwage also allows you to convert your regular payment to a bank to cryptocurrencies.

# [Using bitcoin for expenses and traveling](#toc.xhtml#s71a)

Bitcoin price has risen exponentially, and many have made large profits. Additionally, there are location-independent contract workers who are paid in bitcoin or other cryptocurrencies.

People who are paid in bitcoin or have made large profits because they were invested in bitcoin may travel the world using their bitcoin.

Since bitcoin is not suitable for small payments, a bitcoin holder can buy gift cards that they can use in stores or hotels or to buy flight tickets. Gift card providers like *Bitrefill, eGifter, Gyft, etc.* provide easy conversion of bitcoin to gift cards. Some providers even provide Lightning Network support, and by creating channels, effective Bitcoin network fees can be reduced.

Here’s an illustration of using bitcoin to buy a gift card and then spend it:

![](images/Figure-4.10.jpg)

**Figure 4.10:** Buy Gift Cards from bitcoin and use it in shopping

# [Bitcoin for remittance](#toc.xhtml#s72a)

Bitcoin is also used in transferring money across borders for remittance. Remittance is a non-commercial transfer of money by foreign workers and residents and citizens with ties abroad, for supporting their family there. Bitcoin allows money transfers to be made directly to the receiver’s wallet, which can be a hardware wallet, mobile wallet, or wallet at a custodial exchange. There are specialized services such as *BitPesa*, *which are designed for remittance. In BitPesa*, a sender can send bitcoin, and the receiver will receive money in their bank account or mobile wallet.

The following is the illustration of the BitPesa remittance network:

![](images/Figure-4.11.jpg)

**Figure 4.11:** BitPesa helping African migrants send money home

# [Bitcoin for social cause](#toc.xhtml#s73a)

Social service organizations need to work in areas and with people who have limited access to the banking system. Many a time, these places are in war zones, under autocracy, military rule, etc. Consequently, the legal and financial systems do not work in favor of the people who need to be protected. So, social service organizations must ignore the existing systems and use their own resources. Bitcoin helps in these circumstances as it is censorship-resistant. Many reputed global social service organizations support payments in cryptocurrency. UNICEF is one such organization; it has launched a cryptocurrency fund for receiving cryptocurrencies as donations.

# [Mining bitcoin](#toc.xhtml#s74a)

Bitcoin mining is one of the ways to earn bitcoins. It is very price sensitive, so mining bitcoin with a regular electrical connection is not financially viable, even with the most efficient equipment. For Bitcoin mining to be profitable, electricity cost needs to be incredibly low, or it is an extra power that would otherwise go waste.

Bitcoin mining also generates a lot of heat and sound. If heat is used to heat homes or water, it might further improve its financial viability. In colder countries, Bitcoin mining is used by some people to heat their homes and supply heat to vegetation in addition to the greenhouse.

So, the following are the different ways in which Bitcoin mining cost is often reduced:

*   Use cheap sources of energy like solar panels and wind turbines without battery storage.
*   Oil wells use waste gases as the energy source for mining.
*   Excess energy is generated by electricity generation plants.
*   Using generated heat. 
    *   For heating water as geysers
    *   For heating house
    *   For supplying heat to greenhouse farms
*   Select the most efficient Bitcoin mining equipment.
*   Join a mining pool.

Bitcoin mining also requires mining equipment to be regularly upgraded as their profitability reduces over time.

# [Bitcoin and cryptocurrency regulations](#toc.xhtml#s75a)

All the use cases we discussed in the previous topic are subject to country-specific laws. Be aware of your country’s laws before using bitcoin for any activity.

Remember that cryptocurrencies are rarely allowed as legal tender. So, even in countries where bitcoin use is legal, its use as legal tender is illegal. Legal tender can be defined as follows:

*A legal tender is anything that can be used to settle financial disputes such as debt payment etc.*

Cryptocurrency regulations can be broadly classified into:

*   **Permissive**: Countries where cryptocurrency is well regulated and individuals can trade, purchase goods, mine, and receive payments.
*   **Restrictive**: Countries where certain activities related to cryptocurrency are not allowed. Many countries do not allow the conversion of cryptocurrency to local currency or vice versa. There may be restrictions on the sale and purchase of goods or payments. There could also be restrictions on businesses to deal in cryptocurrency. Alternatively, banks may not be allowed to launch cryptocurrency-related financial instruments.
*   **Contentious**: Countries where cryptocurrencies are unregulated.
*   **Prohibitive**: Some countries have imposed a complete ban on dealing with cryptocurrencies. Some countries even make it a punishable offense.

There are many countries that are planning to regulate cryptocurrencies, so a country that does not regulate it today may do so in the future. This is a dynamic area.

The following is the current state of regulation in various countries:

![](images/Figure-4.12.jpg)

**Figure 4.12:** International Bitcoin Regulations

Remember, the above information may be already outdated by the time this book reaches the market.

In India, cryptocurrency regulations are not clear currently. In April 2018, the Reserve Bank of India, which is the country’s central bank, published a circular in which it stopped banks from dealing in cryptocurrencies. This resulted in the freezing of bank accounts of anyone who bought cryptocurrencies from exchanges using registered bank accounts. This made dealing in cryptocurrencies difficult, and many businesses and exchanges went bankrupt or closed shops. Despite this, Bitcoin was never banned in India; so, some exchanges used a legal workaround by providing a peer-to-peer platform for trading.

In March 2020, the Supreme Court of India, which is the country’s apex court, squashed RBI’s circular and allowed cryptocurrencies to be traded using bank accounts. Anyone dealing in cryptocurrency has always been required to pay taxes on profits, although which sections of tax law will apply is not clear.

In Union Budget 2022 the finance minister of India gave guidance on taxation on cryptocurrencies. Even though cryptocurrencies are now regulated it is still not considered legal. And still, it is difficult to deal with cryptocurrencies.

Many developed countries like the US, the EU countries, and Japan have proper regulations in place that protect investors and entrepreneurs.

# [Conclusion](#toc.xhtml#s76a)

In this chapter, you learned about the way we interact with Bitcoin and Bitcoin network. You first learned about the different types of exchanges, their characteristics, and the benefits they provide to users, and then we saw how traders, investors, freelancers, travelers, and miners interact with the Bitcoin network. We also suggested useful ways in which different people may use bitcoin. Then, we tried to categorize international regulations and looked at the state of regulations in India.

This brings us to the end of the section that was focused on the user view of the Bitcoin ecosystem. We already covered the overview of Bitcoin in the first chapter. After reading this chapter, you would have got a basic yet broad understanding of Bitcoin, the Bitcoin network, and the Bitcoin ecosystem.

In the next chapter, we will go through the Bitcoin Whitepaper and help you understand it in detail.

# [Points to remember](#toc.xhtml#s77a)

*   Peer-to-peer exchange works on an escrow model, where the exchange acts as a third party.
*   Retail exchanges allow buyers to *bid* for the highest price they can pay for cryptocurrency while allowing sellers to *ask* for the lowest price they can accept for their cryptocurrency.
*   Retail exchanges try to discover the value of cryptocurrencies by bid and ask. This helps the cryptocurrency get its value.
*   Bitcoin ATMs are instant exchanges that deal in cash.
*   Decentralized Exchanges (DEX) are unmanaged peer-to-peer exchanges.
*   Traders earn money from the volatility of trading instruments.
*   Investors look for longer-term gains by holding cryptocurrencies.
*   Savers consider cryptocurrency as Store-of-Value.
*   Cryptocurrency payment processors can be integrated into a website to enable cryptocurrency payments.
*   Lightning Network allows multiple off-chain transactions to be made between parties before the cumulative transaction is added to the blockchain.
*   PayNyms are publicly shareable Reusable Payment Codes that generate unique unused addresses.
*   Gift cards are the easiest way to utilize bitcoins for retail purchases.
*   Bitcoin miners require cheap energy sources and utilize generated heat.
*   Bitcoin miners need to always update their equipment with the most efficient devices in the market.
*   A legal tender is anything that can be used to settle financial disputes.

# [Questions](#toc.xhtml#s78a)

1.  How is retail exchange different from peer-to-peer exchange?
2.  What is the meaning of the phrase “Not your keys, not your bitcoin”?
3.  Randomly select 10 countries and categorize them based on the legal status of cryptocurrency in those countries.
4.  Investigate and understand why BitPesa is so successful in Africa.
5.  Match the following:
    
    1.  Remittance
    2.  Salary
    3.  Instant Exchanger
    4.  Merchants
    
    With:
    
    1.  BtcPay
    2.  BitWage
    3.  ATM
    4.  BitPesa
6.  True/False: 
    1.  Custodial exchanges do not insure Bitcoin wallets against the hacking event.
    2.  Store-of-Value means value in the financial instrument is secure.
    3.  If a country does not regulate cryptocurrency, no taxes need to be paid.

# [CHAPTER 5](#toc.xhtml#c05)

# [The Whitepaper](#toc.xhtml#c05)

*Satoshi Nakamoto* published the Bitcoin Whitepaper titled “*Bitcoin: A Peer-to-Peer Electronic Cash System*”. This paper is available at **[https://bitcoin.org/bitcoin.pdf](https://bitcoin.org/bitcoin.pdf)**. Bitcoin and most cryptocurrencies are based on this whitepaper. It is important to understand the whitepaper thoroughly to be able to understand the content in the upcoming chapters. This chapter focuses on explaining the content in the whitepaper.

The whitepaper is not under any copyright protection as the creator of the paper was anonymous and never claimed any copyright on the paper. So, anyone can easily copy or refer to the paper. The Bitcoin Whitepaper is also in the blockchain, from where it can always be retrieved. Other than that, there are multiple other websites where the whitepaper is available. It is even available on the following Estonian government website:

q-

**[https://www.e-resident.gov.ee/bitcoin-whitepaper/](https://www.e-resident.gov.ee/bitcoin-whitepaper/)**

And on the following US government website:

**[https://www.ussc.gov/sites/default/files/pdf/training/annual-national-training-seminar/2018/Emerging\_Tech\_Bitcoin\_Crypto.pdf](https://www.ussc.gov/sites/default/files/pdf/training/annual-national-training-seminar/2018/Emerging_Tech_Bitcoin_Crypto.pdf)**

# [Structure](#toc.xhtml#s79a)

In this chapter, we will cover the following topics:

*   Abstract section of the whitepaper
*   Introduction section of the whitepaper
*   Transaction section of the whitepaper
*   Timestamp Server section of the whitepaper
*   Proofof-Work section of the whitepaper
*   Network section of the whitepaper
*   Incentive section of the whitepaper
*   Reclaiming Disk Space section of the whitepaper
*   Simplified Payment Verification section of the whitepaper
*   Combining and Splitting Value section of the whitepaper
*   Privacy section of the whitepaper
*   Calculations section of the whitepaper
*   Conclusion section of the whitepaper

# [Objective](#toc.xhtml#s80a)

The primary objective of this chapter is to help readers understand the Bitcoin Whitepaper in depth.

# [Abstract section of the whitepaper](#toc.xhtml#s81a)

![](images/Figure-5.1.jpg)

**Figure 5.1:** Abstract section of the whitepaper

Bitcoin is electronic cash that is completely peer-to-peer. There were a few cryptographic trials in the past that provided an electronic cash system. These implementations were centralized, and some of them failed. These implementations required a third party to avoid the double-spending problem. Bitcoin does not need third parties as it uses an immutable chain of blocks where each block contains a list of transactions, a hash confirming the integrity of transactions, and a timestamp. The chain of blocks maintains immutability by using hash-based proof of work.

Bitcoin is a cooperating system where nodes either comply with the consensus rules or are cooperating to attack the network. The cooperating systems form a pool of CPU power, which adds blocks to the existing chain. The longest chain stores the greatest CPU power and so, is considered the actual blockchain, and the other chain is discarded. This mechanism assumes that the greatest CPU power is owned by honest nodes. This assumption fails if the whole network is compromised. In the upcoming chapters, we will explain how this is not a problem anymore.

The Bitcoin network maintains trail-of-truth (blockchain) and so, allows any node to leave or join the network at will. The joining nodes sync up their local chain at the time of joining the network. If a node goes offline for some time, it will also need to sync up its local chain. If we look at the whitepaper, it is quite simple to understand and implement. Consequently, thousands of cryptocurrencies have come up, most using the almost original design.

# [Introduction section of the whitepaper](#toc.xhtml#s82a)

![](images/Figure-5.2.jpg)

**Figure 5.2:** Introduction section of the whitepaper

The introduction section explains the drawback of a trusted third party that exists today. Trusted third parties are mostly large financial institutions that facilitate dispute resolution. Many a time, these disputes lead to transaction reversal, litigations, and losses. For a high-value transaction or transactions where services and payments can be reversed, these additional costs benefit them as not being able to reverse a transaction can lead to large losses. On the other hand, for small transactions or transactions where services and payments are non-reversible, these costs are unnecessary. Both these transactions are normally catered to by the same payment processors. The losses these payment processors must bear are born by both kinds of transactions, so the cost affects both transactions. In short, the cost of having trusted the third party is universal.

A peer-to-peer cash system intends to remove the need for trusted third parties, thereby removing the possibility of transaction reversal. An escrow mechanism can still be implemented to protect buyers. This mechanism can separate small non-reversal transactions that are akin to cash transactions from large transactions that need mediations and can have a separate escrow mechanism provided by a trusted third party without impacting the cost to the network itself.

# [Transactions section of the whitepaper](#toc.xhtml#s83a)

![](images/Figure-5.3.jpg)

**Figure 5.3:** Transaction section of the whitepaper

The transaction section explains transactions as a trail of digital signatures that leads to the flow of bitcoin between parties. To understand this, we need to understand terms like Hashing and Digital Signatures.

**Hashing**

**Hashing is a non-reversible** **process that generates a fixed byte output for a large text. The fixed byte output is called hash-code. Hashing has certain properties that make it very useful in applications such as bucketing for randomly distributing data in buckets. It is also useful in safely storing and transferring passwords. It is also used in network handshaking for sending challenge code. The hash-code output is deterministic, which means the same text will always generate the same hash-code. These pieces of code are very well randomized, so they cannot be determined by brute force or other more sophisticated attacks.**

![](images/Figure-5.4.jpg)

**Figure 5.4:** Illustr ation of the irreversibility of hashing algorithm

**Digital Signatures**

**Digital Signatures are like physical** **signatures as they ensure the integrity of the document, and they also ensure that the document is signed by the signer (authenticity). Digital Signature uses “Public and Private key cryptography”. A document is signed by the sender’s private key. This creates a signature that is a code, and it is kept along with the document for others to verify.**

**The following is the Digital Signing process:**

![](images/Figure-5.5.jpg)

**Figure 5.5:** Illustration of the Digital signing process

The signature is verified by using the Sender’s public key. The verification algorithm uses Document content, Signature, and Sender’s public key for verification.

The following is the signature verification process.

![](images/Figure-5.6.jpg)

**Figure 5.6:** Illustration of the digital signing verification process

A transaction in Bitcoin has two sections: ins and outs. Input transactions carry information about the previous transaction, along with the signature of sender and its public key for verification. Out contains information of bitcoin to be transferred along with public key of the receiver. Only the receiver knows private keys and so, can unlock the bitcoin locked in the previous transaction and send it to the next receiver. This creates a chain of ownership. To understand this, let’s look at how Alice pays Bob.

![](images/Figure-5.7.jpg)

**Figure 5.7:** Illustration of transactions creation and broadcast

Alice wants to pay Bob. For this, Alice looks for her unspent transactions. She creates a transaction input by signing the hash of previous unspent transactions with her private key. This releases bitcoins locked in the previous transaction. She now creates out-of-transaction by adding a message for Bob along with Bob’s public key. For Bob to pay Dave, he needs to do the same: pick up his previous unspent transaction, hash it, and sign it with his private key to release locked bitcoin. And then he needs to create a message for Dave along with Dave’s public key. For these transactions to be considered valid, these and the trail of all previous transactions carrying value need to be validated by a majority of nodes in the Bitcoin network.

The Bitcoin network consists of nodes that maintain verified copies of all previous transactions. When a new transaction is performed, it is broadcasted on the network, and all the participating nodes verify its validity based on all the existing unspent transactions already received. This mechanism does not leave any chance of missing a concerned transaction, avoiding the chance of double-spending by mistake or on purpose.

# [Timestamp Server section of the whitepaper](#toc.xhtml#s84a)

![](images/Figure-5.8.jpg)

**Figure 5.8:** Timestamp Server section of the whitepaper

Timestamp Server is the node that is creating a block of transactions and putting timestamps to the block. After creating the block, the timestamp server widely publishes block-hash. Each block also contains a block-hash of the previous block header. Since the newly created block contains a block-hash of the previous block header that includes the timestamp of the creation of the previous block, the new block cannot have a timestamp older than the included block-hash. This method, consequently, imposes the necessity of chronological order on the blockchain. Thus, there is no need for reliance on an external source to impose the accuracy of the timestamp.

![](images/Figure-5.9.jpg)

**Figure 5.9:** Block structure with Timestamp

In the preceding figure, we can see that the N+1^(th) block contains a hash of the N^(th) block. Since N^(th) block-hash has a timestamp, the N+1^(th) block timestamp must have been created after the timestamp on the N^(th) block. This ensures that:

*N+1^(th) block timestamp>N^(th) block timestamp*

Thus, it imposes chronological order on the blockchain.

# [Proof-of-Work section of the whitepaper](#toc.xhtml#s85a)

![](images/Figure-5.10.jpg)

**Figure 5.10:** Proof-of-Work section of the whitepaper

Bitcoin uses a proof of work mechanism to ensure the integrity of the blockchain. The proof –of work algorithm necessitates CPU usage (work) in order to create a block. Any attacker who wants to modify an existing transaction will need to redo the work, create the block containing the transactions, and redo work to create blocks after it. The idea here is that a non-cooperating node needs to compete with cooperating nodes in the amount of work done in terms of CPU power. *Satoshi Nakamoto* suggests a simple proof of work mechanism that involves counting starting zeroes in a hash of the block. The logic here is as follows:

The probability of getting “0…..” binary hash value is 1/2.

The probability of getting “00….” binary hash value is 1/4.

The probability of getting “000…” binary hash value is 1/8.

The CPU power required to achieve the binary hash value is inverse of probability, i.e., as follows:

*work≈1/probability*

*Satoshi Nakamoto* also suggests changing the required work based on how quickly blocks have been getting created, thus maintaining block creation time.

So, the block now looks like the following illustration:

![](images/Figure-5.11.jpg)

**Figure 5.11:** Block structure with Nonce, timestamp, and previous block hash

Here, Target proof –of work necessitates the timestamp server to use the required amount of CPU work in order to create a block. This is calculated by taking the moving average of time to create each block and increasing or decreasing the value if blocks are taking lesser or longer time to create. The following equation shows how Target work is calculated:

*D[n]: Target Proof-of-work of Block with Height n*

*T[n]: Timestamp of n^(th) Block*

*ΔT: Expected Time to create Block*

![](images/c05eq-1.jpg)

The following flowchart shows how a Timestamp server finds the right nonce for block creation:

![](images/Figure-5.12.jpg)

**Figure 5.12:** Process of mining a block by finding the required nonce

Timestamp server increments Nonce and calculates block hash. If block-hash achieves the required work, the block is published to the Bitcoin network; otherwise, Timestamp server increments the Nonce till it achieves the required work or some other node publishes the block with the right nonce.

# [Network section of the whitepaper](#toc.xhtml#s86a)

![](images/Figure-5.13.jpg)

**Figure 5.13:** Network section of the whitepaper

The term node used here is the same as the timestamp server used in previous sections. Now, we do not use the term node to describe nodes that create a block; instead, we call them mining nodes.

Each node is connected to multiple nodes, and those nodes are connected to several other nodes. This creates a network of nodes. Each node tries to find nonce for the next block to be created in the blockchain. When a new transaction is created, like “*Alice pays Bob*”, it is sent to its peers. Each receiving node checks whether the transaction is valid and not trying to create an illegal transaction or trying to spend an already spent transaction. It is then sent to their peers and so on; this gets broadcasted to the whole network. Each receiving node adds a transaction to the block and races to find nonce. Whichever node finds the nonce first creates the block and sends the block to its peers. All the receiving nodes verify the block timestamp, transactions, nonce, and next target proof –of work. The receiving nodes then forward it to their peers and so on; this gets broadcasted. After receiving the block, each node starts working on the next nonce. This is the way the process continues.

The following image shows how blocks and transactions propagate:

![](images/Figure-5.14.jpg)

**Figure 5.14:** Transaction propagation on Bitcoin network

A ping takes nearly 200ms to reach to cover the longest distance on earth. Block broadcast involves verification at each hop; so, to cover 95% of the network, propagation delay can be up to a minute. Due to this reason, multiple nodes can create a valid block without knowing the existence of an already created block. This creates branching on the blockchain. Depending on the location, nodes may choose different nodes as valid for the same block height. Since no node can know which block is to be considered and which one is to be rejected, they need to start working on the first one received but also save the other valid blocks. Now, there are multiple sets of nodes calculating nonce for different chains, so they may continue to create next blocks in their respective chains. To solve this issue of branching, the nodes must continue this process till one of the competing chains becomes longer than the rest. The nodes will then accept the longest chain as the correct one and discard the other chain. As the time, to find the nonce is significantly higher than the block propagation delay; the nodes competing for the next block will not be many.

Here’s an illustration of chain branching:

![](images/Figure-5.15.jpg)

**Figure 5.15:** Illustration of block branching due to almost simultaneous mining of blocks

If, for some reason, blocks are not received by a node and a new block is received, the node can request for missed blocks from its peers. Since not receiving a block is not a problem, a block does not need to reach all nodes either.

![](images/Figure-5.16.jpg)

**Figure 5.16:** Node requested missing block peer

# [Incentive section of the whitepaper](#toc.xhtml#s87a)

![](images/Figure-5.17.jpg)

**Figure 5.17:** Incentive section of the whitepaper

This section explains the incentive a node has in creating blocks and supporting the Bitcoin network. A node that successfully creates a block is incentivized in two ways:

*   Each newly created block awards bitcoin to the node that successfully finds Nonce.
*   Additionally, in a transaction, input value minus output value also adds to the block reward collected by the node creating the block.

A node uses CPU power in trying to find nonce, which leads to power consumption. Since many nodes will be competing in finding a nonce, this process will mostly lead to failed attempts. The cost of energy used in this process will need to be recovered when the node succeeds. The node also needs to make revenue to run a profitable business as this is a business for the node owner. A block reward makes sure that the node has enough incentives to continue to find nonce.

If a group of nodes decides not to cooperate with the network and double-spend or change rules of acceptance of block/transaction or attack network in some way, then those nodes will form their own network. The network that will provide better incentives and where nodes play by the rules will provide better value for publishing transactions. Consequently, the reward will have a higher credit value. This will encourage nodes to cooperate and support the network instead of attacking it.

The node is free to include or exclude a transaction or not cooperate with the network. By including the reward, the creator of a transaction encourages the node to include the transaction in the block. As more and more transactions are included in the block, transaction reward will become the main driver of revenue for the mining node, and so, the need for block reward will diminish. The network implements a mechanism to reduce block rewards over time.

The following figure illustrates transaction rewards:

![](images/Figure-5.18.jpg)

**Figure 5.18:** Illustration of transaction reward payment

Also, Block reward is the only source of minting bitcoin. This leads to predefined inflation.

The following is bitcoin inflation plotted for past and future:

![](images/Figure-5.19.jpg)

**Figure 5.19:** Bitcoin inflation of past and future

# [Reclaiming Disk Space section of the whitepaper](#toc.xhtml#s88a)

![](images/Figure-5.20.jpg)

**Figure 5.20:** Reclaiming Disk Space section of the whitepaper

This section explains how we can compact stored blocks in the blockchain and, thus, reclaim disk space. Merkle Tree is a method of deriving code (called Merkle root) from a list of transactions. This code confirms the integrity of transactions included in the block. Merkle Root, being part of the Block header, also ensures that proof –of work protects it against modification.

The updated Block Header is now as follows:

![](images/Figure-5.21.jpg)

**Figure 5.21:** Illustration of Bitcoin Block structure

We can see that as transactions were not used in the calculation of Block hash, their integrity could not have been protected without Merkle root.

Calculation of Merkle Root can be understood from the following illustration:

![](images/Figure-5.22.jpg)

**Figure 5.22:** Calculation of Merkle Tree Root

In the preceding illustration, the first Hashes of each transaction are calculated. Then, recursively, pairs of hashes are concatenated and hashed to get hash for the upper level. If a pair is not available, the hash is concatenated with itself.

Each node verifies a block as it receives over the network and stores it on the disk. When enough blocks are saved on the disk and the node is confident that the older blocks will not change because of branching, the node can remove sent transactions from the older blocks and only keep headers and unspent transactions. This way, nodes can save a significant amount of disk space.

# [Simplified Payment Verification section of the whitepaper](#toc.xhtml#s89a)

![](images/Figure-5.23.jpg)

**Figure 5.23:** Simplified Payment Verification section of the whitepaper

This section explains how a node that does not maintain full blocks can still verify received blocks. A node implementing Simplified Payment Verification only keeps Block headers for the longest chain, which means there are no competing chains, and the longest chain is already found. The node takes help from other nodes in its network that are maintaining full blockchain to verify blocks.

It uses a technique called *Merkle proof,* explained as follows:

![](images/Figure-5.24.jpg)

**Figure 5.24:** Illustration of Merkle proof

SPV node requests full node for Hashes related to T4. The full node sends the hashes required to verify Merkle root. Since H34 can be derived from H3 and H4, H1234 can be derived from H34 and H12. H12345555 can be derived from H1234 and H5555. By giving H3, H4, H12, and H5555 and Merkle root H12345555, SPV node can verify the presence of T4 in the block with Merkle root H12345555.

![](images/Figure-5.25.jpg)

**Figure 5.25:** Communication between SPV Node and Full Node

However, attackers can form a network, and since SPV node depends on full nodes for verification, it may not know if the node it is communicating is fraudulent. Consequently, it can continue receiving fabricated transactions. This kind of attack can be handled if a node broadcast alerts for presence of invalid block when it sees on network.

# [Combining and Splitting Value section of the whitepaper](#toc.xhtml#s90a)

![](images/Figure-5.26.jpg)

**Figure 5.26:** Combining and Splitting Value section of the whitepaper

This section explains the concept of combining and splitting of value in Bitcoin transactions instead of having one transaction for each bitcoin or fraction of bitcoin. If Alice needs to pay Bob, she needs to use unspent transactions paid to her that have combined value greater than or equal to the amount she needs to pay to Bob and pay herself back the remaining (change) value.

If the unspent transaction is bigger than the required amount, then the transaction will be split into the amount to be paid and the remaining change. If unspent transactions are smaller, then the value of multiple transactions needs to be combined to make the input value bigger than or equal to the required amount. If the input value is the same as the required amount, then output is only one transaction, which is the amount to be paid to Bob. However, if the input value is bigger, then Alice needs to pay herself the change. If the output is smaller than the input, then the remaining value is paid to the mining node, as we learned in one of the previous sections. This can be understood from *[Figure 5.18](#c05.xhtml#fig5_18)*.

# [Privacy section of the whitepaper](#toc.xhtml#s91a)

![](images/Figure-5.27.jpg)

**Figure 5.27:** Privacy section of the whitepaper

This section explains how privacy can be achieved in the Bitcoin network even though all transactions are broadcasted. A user can keep its public keys anonymous this way. Although transactions are public, no one will know who the transaction belongs to. However, since change needs to be sent back to the owner of the transaction, its value and transaction details can be derived. To solve this, the owner of the transaction can send change to a different public key. This means a new key pair needs to be used every time. However, transaction history can still reveal the owner’s chain of transactions if their identity is revealed in one of the existing transactions.

The following is the illustration of the method of improving privacy in a transaction:

![](images/Figure-5.28.jpg)

**Figure 5.28:** Method of improving the privacy of the sender in a transaction

# [Calculations section of the whitepaper](#toc.xhtml#s92a)

![](images/Figure-5.29.jpg)

**Figure 5.29:** Calculations section of the whitepaper

This section explains the condition when an attacker or group of attackers tries to mine more blocks than an honest node. If the attackers manage to have more CPU processing power and can mine more blocks, the attacker will be part of the network, which means it will have to depend on honest nodes to accept the blocks.

Consequently:

1.  The attacker cannot change block reward, so they cannot increase bitcoin supply.
2.  The attacker cannot change the content of transactions from others’ payments as it cannot sign their transactions.
3.  The attacker cannot stop honest nodes from broadcasting transactions.

The attacker can, however, change its own transaction, censor transactions by not including them, or reverse a transaction that was recently included.

Now, consider a situation wherein an attacker who may or may not hold the majority CPU power tries to attack a network. This situation is like Gambler’s Ruin Problem, and the solution is derived by using Binomial Random Walk.

The attacker wants to change a transaction at z-1 depth, so it will start from z depth. If they can mine a block before honest node, gap reduces by z-1, but if honest node mines the block, gap increases to z+1. We are trying to find the probability of the attacker being able to create the longest chain.

In Gambler’s Ruin Problem, Gambler competes with the opponent and tries to win all fortune from the opponent. It is an iterative betting game in which either party wins or loses $1 on every bet. In the end, one party loses all its fortune.

At first, looking at Gambler’s ruin problem.

*q: Probability of Gambler winning a single bet*

*p: Probability of Gambler losing a single bet*

*i: Initial fortune of Gambler*

*p=1-q*

*0< i< N*

![](images/Figure-5.30.jpg)

**Figure 5.30:** Illustration of Gambler’s ruin problem

The probability of Gambler winning the game can be calculated as the sum of the following probabilities after the bet:

*   If Gambler wins a bet with probability q, then the new game-winning probability is .
*   If Gambler loses a bet with probability p, then the new game-winning probability is.

Using Law of total probability, i.e., .

The probability of the gambler winning the game is the sum of probability of winning the game after winning or losing the current bet. This can be represented as follows:

![](images/107.jpg)

![](images/c05eq-4.jpg)

In a winning situation, *P[N] = 1 and i = N - 1*

![](images/c05eq-5.jpg)

Now, consider the case of Bitcoin mining in which attacker can mine blocks forever to defeat honest nodes. It is Gambler’s ruin problem with a difference. Attacker has infinite dollars and infinite time, and to win, attacker needs to create bigger chain by adding blocks more than honest node. At the beginning, attacker wants to be able to modify a transaction at z-1depth, so it starts at z depth.

The following figure explains this:

![](images/Figure-5.31.jpg)

**Figure 5.31:** Illustration of an attacker successfully mining longer chain

Considering,

*p: Probability of an honest node finding the next block*

*q: Probability of the attacker finding the next block*

*z: Blocks attacker has to add more than honest node*

*i: Number of additional blocks attacker can lose to honest node*

*q[z]: probability of the attacker to ever beat honest node*

*So, N= i + z*

*Here, i* → *∞ since Gambler started with infinite resources.*

![](images/c05eq-6.jpg)

![](images/c05eq-7.jpg)

This is how we reached the equation given in this section of the whitepaper.

Assuming that the attacker has a lower probability of finding the block than the honest node, i.e., the attacker’s chance of catching up goes down exponentially.

Now, we are going a step ahead here and trying to determine the probability of the attacker being able to double spend if the merchant waits for z confirmations. Satoshi Nakamoto considers the probability distribution of the number of winning events in each time period as Poisson’s distribution because of the following reasons:

*   Mining events can occur any number of times during each interval.
*   Each event occurs independently and does not affect the probability of other events.
*   The average rate of the event is constant as we know since block time is constant, and the probability of block mining is proportional to the ratio of CPU power, so it is also constant.
*   Two events occurring at the exact same time is not possible as nodes judge based on arrival time, and if they do occur, they wait till the longest chain is found. So, two events occurring at the same time are rare and even if they occur, they can be safely considered different.

Considering,

*T: Average block time*

*z: Required depth of transaction in blockchain to consider spent*

*P[p]: Probability of mining a block by honest node every T minutes*

*P[q]: Probability of mining a block by attacker node every T minutes*

*p: Number of blocks mined by honest node every T minutes*

*q: Number of blocks mined by attacker every T minutes*

*T[z]: Average Time interval for mining z blocks*

*T[z]\= T\*z*

The quantities p and q are inverse of their respective probabilities of mining a block within time interval T.

Therefore,

![](images/c05eq-8.jpg)

Attacker can mine q blocks in T minutes, so it can mine:

![](images/c05eq-9.jpg)

The probability of k successes happening in an interval is given by Poisson density function

![](images/111.jpg)

As a more general case, we want to know the overall probability of attack successes for the merchant to accept a modified transaction in a block in the future if not in the current interval. So basically, even if the attacker has k successes in an interval, it can still achieve z-k blocks in the future and modify the future blocks in an interval.

This can be solved by using the Law of total probability, i.e., *P(A)= ∑[n]P(A|B[n] )P(B[n])*

*P[s]: Total probability of successes*

![](images/c05eq-10.jpg)![](images/c05eq-11.jpg)

This is the equation Satoshi Nakamoto used to write code and demonstrate that the probability drops exponentially.

From the equation, we can deduce that the probability of an attacker successfully mining z blocks reduces exponentially with the increase in value of z if the attacker does not control a majority of hash power. Therefore, it is important to wait for few blocks before confirming a transaction.

It is recommended that a merchant should confirm a payment only after the transaction is at the depth of 6 in the blockchain.

# [Conclusion section of the whitepaper](#toc.xhtml#s93a)

![](images/Figure-5.32.jpg)

**Figure 5.32:** Conclusion section of the whitepaper

This section explains what we achieved in the paper. This can be listed as follows:

*   A peer-to-peer payment system that protects against double-spending and does not require a trusted third party.
*   A digital signature provides ownership of the transaction.
*   If honest nodes control the majority of CPU power, then proof of work makes it impractical for an attacker to modify enough blocks in blockchain to cause double-spending.
*   Nodes work independently with only little need for coordination. Nodes can leave and join the network independently. They do need to communicate, but their state does not depend on other nodes, and there is no need for routing, etc.
*   Nodes do not need to reveal their identity.
*   Nodes votes with their CPU power, and so, compete in CPU power to mine blocks. Successful nodes get the incentive to support the network.
*   Consensus rules are enforced through majority support and participation.

# [Conclusion](#toc.xhtml#s94a)

In this chapter, you learned about the content of the whitepaper in detail. You also learned about the calculations used in the whitepaper by deriving them.

In the next chapter, you will understand the structure of blocks in the blockchain by writing actual programs for parsing blocks and indexes stored in the filesystem by Bitcoin software. You will also understand mining in detail again through programming.

# [Points to remember](#toc.xhtml#s95a)

*   The Bitcoin network does not require any intermediaries to send bitcoin between two parties.
*   Blockchain is a trail of truth that every node maintains.
*   Trusted third parties have a cost included in all the transactions, even if a transaction does not require dispute resolution.
*   Bitcoin transactions can optionally have a trusted third party as escrow implementation rather than by rule.
*   Transactions are a trail of digital signature linking the amount paid to the previous transaction and finally, leading to the mined coins.
*   Hashing is irreversible.
*   The digital signature ensures the integrity and authenticity of the document.
*   Transactions once created are broadcast to the Bitcoin network.
*   Each block in the blockchain is arranged in chronological order.
*   A nonce is a random value found by the miner so that it is within target proof –of work, and hence, acceptable.
*   Bitcoin maintains block time by adjusting the target proof –of work.
*   New blocks are published to the network.
*   In case two blocks are mined almost simultaneously, there will be multiple competing chains in a branch in the blockchain.
*   The longer chain in the competing branch is accepted, and the other one is rejected.
*   A miner who finds the required nonce is awarded a block reward.
*   Additionally, miners collect a transaction fee from the included transaction in the block.
*   Miners have an incentive to protect the network instead of attacking it.
*   Bitcoin inflation is predetermined.
*   A node can prune older blocks by removing included transactions once enough newer blocks are received.
*   Simplified Payment Verification node keeps only block headers of the longest chain with only the required transactions.
*   SPV node takes help from full nodes to verify blocks and transactions using Merkle proof.
*   Payers of bitcoin can combine its unused bitcoin transaction output or split its previous unspent output.
*   One can enhance their privacy by never reusing their addresses.
*   The probability of malicious miners successfully reversing a transaction already included in the blockchain reduces exponentially as the depth of the block increases.

# [Questions](#toc.xhtml#s96a)

*   How does a node know that it has missed a block? How can it get the missed block?
*   Why are there mostly one or two outs of a transaction?
*   What makes blockchain immutable? (Tick the correct answer) 
    *   Merkle root
    *   Digital Signature
    *   Proof –of work
    *   Copy of blockchain
*   True or False 
    *   The greater the value of the Block-header hash, the greater is proof-of-work.
    *   The success of SPV block verification depends on the honesty of its peers.
*   Bitcoins are created by \_\_\_\_\_\_\_.
*   Why does sending bitcoin change back to the same public key reduce privacy?
*   In Gamber’s Ruin Problem: Ria starts with i = $2 and has a probability of winning a bet p = 0.7. 
    *   What is the probability of Ria winning a total fortune of N = $6?
    *   What is the probability of Ria becoming infinitely rich?
*   An attacker has the mining power of 20% of the entire network. An online store requires a bitcoin transaction to reach the depth of 6 in blockchain before they release the item. 
    *   What is the probability of the attacker mining 3 blocks during this time?
    *   What is the probability of the attacker being able to produce the longest chain by mining 3 blocks during the confirmation time and additional blocks afterward?

# [CHAPTER 6](#toc.xhtml#c06)

# [Blockchain, Transactions, and Mining](#toc.xhtml#c06)

In the previous chapter, we tried to understand the content of the Bitcoin Whitepaper in detail. The Bitcoin Whitepaper was released on October 31, 2008. It provided a conceptual design of internet money that could work like cash. As we saw, the design was quite detailed but did not provide specifics like block reward or block time or details about transaction messages, hashing, or signature algorithms. The whitepaper is more like a template for cryptocurrency design. So, the paper we call Bitcoin Whitepaper should ideally be called cryptocurrency whitepaper.

In this chapter, we will analyze Bitcoin protocol implementation. The Bitcoin software we will use is written in a quite complicated C++ program. For an average programmer who is trying to understand Bitcoin, looking at and understanding the Bitcoin software code is a daunting task. Even for a very good C++ programmer, understanding the Bitcoin program is a very difficult task. In today’s age of the internet, going through websites and blogs simplifies this task. And Python comes in handy in trying to understand and verify our learnings. The purpose of this chapter is to learn by coding and not try to build the most efficient solution.

Before diving deeper into the actual implementation of the Bitcoin protocol, we need to have software installed and blockchain and indexes synchronized with the network.

# [Structure](#toc.xhtml#s97a)

We will cover the following topics in this chapter:

*   Bitcoin software 
    *   Bitcoin Core installation 
        *   Running the Bitcoin Core server
        *   Bitcoin Core client
        *   Querying indexes in Python
*   Blockchain 
    *   Genesis block
    *   Blocks and indexes
    *   Block header 
        *   Block version
        *   Previous block hash
        *   Timestamp
        *   Merkle root
        *   Bits and nonce
    *   Serialized block 
        *   Magic number
        *   Block file
        *   Block traversal using block indexes
*   Transactions 
    *   UTXO
*   Mining 
    *   Mining profitability 
        *   Block reward
        *   Transaction fee
        *   Coinbase transaction amount verification
        *   Mining cost
    *   Mempool

# [Objectives](#toc.xhtml#s98a)

The objectives of this chapter are to help you understand the structure of Bitcoin blockchain, how Bitcoin software store and organize the blockchain, how blocks and transactions are indexed, and the structure of mempool data, and how to use them and UTXO to perform mining.

The chapter uses Python programming to understand Bitcoin blockchain, blockfile, indexes, UTXO, and mining.

# [Bitcoin software](#toc.xhtml#s99a)

There are mainly three software that provide full verification: Armory, Bitcoin Core, and Bitcoin Knots. Of these, Bitcoin Core is the most widely used software, and it is also the most updated. Satoshi Nakamoto created this software and after him, it has been managed by the Bitcoin Core team. It is also called Satoshi client. According to some estimates, as much as 95% of the full nodes run this software. So, we will use this for our development and learning.

# [Bitcoin Core installation](#toc.xhtml#s100a)

Installation instruction for Bitcoin Core can be found under the following:

**[https://bitcoin.org/en/full-node](https://bitcoin.org/en/full-node)**

On the left-hand side, you can find the instructions for the installation of Linux, Mac OS and Windows. Additionally, the Bitcoin Core can be installed on Linux using Snap Store. Bitcoin Core can also be installed on Docker. It is important to always use authentic software because if you use the software for generating private keys or receive bitcoins those private keys will be known to the attacker or attacking software who will use it to steal your bitcoins protected by the private keys. Downloading software from an authentic site and validating hash at multiple unrelated websites are the best ways to be secure.

# [Running the Bitcoin Core server](#toc.xhtml#s101a)

The Bitcoin Core server can run from GUI or command line. For the GUI version, we can run `bitcoin-qt –daemon`, and for the command line, we can run `bitcoind`. We will use the command line for running daemon and client. It may take one or more days to sync all the blocks along with all the indexes. A greater memory, better internet, and faster disk can speed up download and index generation.

The following is the sample command to start the daemon:

`bitcoind -printtoconsole -txindex=1 -dbcache=8392`

`dbcache` is the database cache size in memory. It improves block verification time and reduces the time to download the blockchain.

`txindex=1` means transaction indexes will be created in addition to the necessary ones.

# [Bitcoin Core client](#toc.xhtml#s102a)

We can connect to the daemon using the following command:

`bitcoin-cli [options] <command> [params]`

We can also connect to the daemon using `bitcoinrpc` for Python. The following is the pip package information:

![](images/Figure-6.1.jpg)

**Figure 6.1:** Python pip package to create Python client for Bitcoin Core Daemon

# [Querying indexes in Python](#toc.xhtml#s103a)

Bitcoin Core uses LevelDB to store its indexes. LevelDB is an on-disk key-value store that uses a binary file to store key-value pairs. It facilitates fast iteration over stored keys and fast access to value using keys. Even though LevelDB provides a very fast query, it has limited use as it provides no pattern search and no filtering. To query the database, we need the following pip package to be installed:

![](images/Figure-6.2.jpg)

**Figure 6.2:** Python package for LevelDB

The following are the keys and values stored in LevelDB databases:

![](images/121.jpg)

![](images/122.jpg)

**Table 6.1:** Bitcoin blockchain LevelDB indexes

We will use the `plyvel` package in `Python 3.6` to explore these values.

# [Blockchain](#toc.xhtml#s104a)

Blockchain is the trail of blocks where each block is a collection of transactions. The blockchain contains all the transactions that took place since the beginning of the Bitcoin network.

# [Genesis block](#toc.xhtml#s105a)

A genesis block is defined as follows:

*The first block in any blockchain is called the genesis block.*

On 3^(rd) January 2009, the Bitcoin network came to life. Satoshi mined blocks for several months. There were few other developers who also mined blocks during that time, but the first block in the Bitcoin blockchain is different. It is not mined; it is hardcoded in Bitcoin software. The blockchain, after traversing using the previous block hash, ends in this block, which means we can create a different chain and so, a new coin, by changing this block. The block carries a special message to the world to justify Bitcoin’s existence.

The following is the hex code of the genesis block:

![](images/Figure-6.3.jpg)

**Figure 6.3:** Shows block hex-dump of the genesis block

This hex code, when printed as byte dump, gives the following output:

![](images/Figure-6.4.jpg)

**Figure 6.4:** Shows binary form of genesis block hash dump

We can see the message with date and origin:

![](images/Figure-6.5.jpg)

**Figure 6.5:** Displays message stored in the genesis block

On 3^(rd) January 2009, a cover story was run in *The Times* in London with the title, Chancellor on brink of second bailout for banks. The message was an attempt by Satoshi to justify the launch of Bitcoin. It pointed out to the world that the current financial system does not have a strong foundation; it requires interventions to sustain, and these interventions are acts of manipulation to benefit certain businesses, such as big banks, but there is no intervention from bankers or the government that provides relief to the common man, many of whom also lost jobs as a result of the great recession in 2008. Satoshi envisioned Bitcoin as an alternative as it provides an intervention-free monetary system that is driven by a set of rules that cannot be modified by the will of a group of people.

# [Blocks and indexes](#toc.xhtml#s106a)

Bitcoin Core daemon, while running, creates several directories and files under the default directory `~/.bitcoin`. Here is the list of files and directories and their functions:

![](images/124.jpg)

**Table 6.2:** List of files and directories used by Bitcoin Core and their functions

The blockchain is quite large, which makes it necessary to maintain indexes to improve the efficiency of the verification of new blocks and transactions and certain other operations required by consensus rules.

# [Block header](#toc.xhtml#s107a)

Bitcoin blocks are generated every 10 minutes on an average. The following is the Block Header structure:

![](images/Figure-6.6.jpg)

**Figure 6.6:** Structure of block header

At the time of writing, the block height is `726556`. Bitcoin-cli gives the latest verified block height using the following command:

![](images/Figure-6.7.jpg)

**Figure 6.7:** Current block height in Bitcoin blockchain

We can use the block height information to get block hash:

![](images/Figure-6.8.jpg)

**Figure 6.8:** Getting block hash from block height

Since we know that the block header is 80 bytes long, we can get block header using block hash. The following is the block header we got by reading the first 80 bytes of block content:

![](images/Figure-6.9.jpg)

**Figure 6.9:** Block header content from block hash using Bitcoin Core CLI

If we take hash of the content of Block header by applying the sha256 algorithm twice, we get block hash. The following program does this:

`import hashlib`

`blk_b = bytes.fromhex(‘040020200a377a6ce7bfbd5efdbe087801fbef9a8a7b6815c3eb08000000000000000000ead1c751f9b4fedd1ff1ab37f7dccec13fc4cdfd6df4406fdd72cd44655fd2fa9389286273370a1739264fbc’)`

`h1 = hashlib.sha256(blk_b).digest()`

`h2 = hashlib.sha256(h1).digest()`

`print(h2[::-1].hex())`

**Program 6.1:** Program to get block hash from the block header

Running this gets us the following hash value, which, as we saw, is the same as the block hash that gave us the block header:

![](images/Figure-6.10.jpg)

**Figure 6.10:** Shows calculated block hash

Block elements are stored in little-endian, so to be able to use the values, we need to reverse byte-order. The following is the small program that takes the hex code of block header and annotates header elements:

`def getBlockHeader(blk: bytes):`

`block = {}`

`block[‘version’] = blk[0:4][::-1].hex()`

`blk = blk[4:]`

`block[‘prev_blockhash’] = blk[0:32][::-1].hex()`

`blk = blk[32:]`

`block[‘merkle_root’] = blk[0:32][::-1].hex()`

`blk = blk[32:]`

`block[‘time’] =int.from_bytes(blk[0:4], byteorder=’little’)`

`blk = blk[4:]`

`block[‘bits’] = blk[0:4][::-1].hex()`

`blk = blk[4:]`

`block[‘nonce’] = blk[0:4][::-1].hex()`

`return block`

**Program 6.2:** Program to get block header structure from block header bytes

We call the method as follows:

`blkhdr = bytes.fromhex(“040020200a377a6ce7bfbd5efdbe087801fbef9a8a7b6815c3eb08000000000000000000ead1c751f9b4fedd1ff1ab37f7dccec13fc4cdfd6df4406fdd72cd44655fd2fa9389286273370a1739264fbc”)`

`jsonobj = getBlockHeader(blkhdr)`

`print(json.dumps(jsonobj, indent = 4))`

This gives the following result:

![](images/Figure-6.11.jpg)

**Figure 6.11:** Shows block header structure from executed program

We can use the collected information for further analysis.

# [Block version](#toc.xhtml#s108a)

The *version* field indicates miner support for an enhancement. In Bitcoin, protocol enhancements that affect consensus rules of verification of blocks or transactions and are backward compatible (does not cause chain split) are called softforks. Bitcoin block consensus mechanism has changed from `IsSuperMajority()` or ISM to Version Bits.

Version 1 to 4 was called `IsSuperMajority()` softfork. In this consensus system, a new version is activated for 950 out of 1,000 consecutive blocks. Once this activation has happened, blocks with older versions are rejected.

The introduction of Segregated witness Bitcoin network has upgraded to a newer consensus mechanism that uses version bits. This mechanism was proposed in Bitcoin Improvement Proposal BIP-9. A list of all the Bitcoin Improvement Proposals can be found at **[https://github.com/bitcoin/bips](https://github.com/bitcoin/bips)**. Version bits allow multiple softforks to wait for acceptance and finally deploy.

In this mechanism, a softfork goes through a workflow. The following flowchart shows the lifecycle of a softfork. (Source **[https://github.com/bitcoin/bips/blob/master/bip-0009.mediawiki](https://github.com/bitcoin/bips/blob/master/bip-0009.mediawiki)**)

![](images/Figure-6.12.jpg)

**Figure 6.12:** Image is taken from BIP 9 showing the soft-fork workflow

When a developer proposes a softfork, it is debated in developer forums and drafted in a BIP. As the BIP implementation is defined and is ready for deployment, the softfork moves to the Defined state. After this, the miner who supports the upgrade readies themselves for the upgrade. The ready miners signal their readiness by setting the corresponding version bit. At that time, softfork reaches the Started state and needs to achieve 95% support in the last 2016 blocks within the next 1 year. If the softfork does not reach 95% acceptance in 1 year, it is considered failed and is withdrawn, which means the blocks supporting it will be rejected. If the softfork achieves 95% acceptance, it reaches a *locked\_in* state and will become a rule after 2016 blocks.

If an enhancement is important and the miner community does not reach a consensus, the developer community can enforce the change in a particular block by enabling BIP148.

A version bit has a `0x20000000` set, and any other set bit denotes readiness for a softfork proposal. If Alice proposes an upgrade and 0x1 bit denotes his softfork, then the miner supporting and ready for the upgrade creates a block with version `0x20000001.` If Bob also proposes an upgrade and` 0x4` bit denotes his softfork, then a miner can vote by setting 0x4 bit, i.e.,` 0x20000100`. If the miner votes for both upgrades, they will set both bits, so the version will be `0x20000101.`

# [Previous block hash](#toc.xhtml#s109a)

In the preceding program, we got a block header structure in which one field was the previous block hash. We can get the same block hash by querying Bitcoin Core software for block hash using one less block height, as follows:

![](images/Figure-6.13.jpg)

**Figure 6.13:** Shows Block hash of the previous block obtained by block header and block height and compared

# [Timestamp](#toc.xhtml#s110a)

Using time, we can get the timestamp of the block using the following bash shell command:

![](images/Figure-6.14.jpg)

**Figure 6.14:** Shows date time obtained from the time field in the block header

# [Merkle root](#toc.xhtml#s111a)

To calculate Merkle Root, we need a list of transactions in a block. We get the list of transactions from the block structure of a block using the following CLI command:

![](images/Figure-6.15.jpg)

**Figure 6.15:** Block structure as shown by Bitcoin Core CLI command

As you learned in *[Chapter 5, The Whitepaper](#c05.xhtml), [figure 5.22](#c05.xhtml#fig5_22)*, Hash of Merkle Root is calculated by repeatedly hashing and concatenating consecutive pairs of transactions. The following Python program does the same:

`def hashOfJoinedStr(a:str, b:str):`

`# Reverse inputs before and after hashing due to big-endian / little-endian nonsense`

`a١ = bytes.fromhex(a)[::-1]`

`b١ = bytes.fromhex(b)[::-1]`

`h = hashlib.sha256(hashlib.sha256(a1 + b1).digest()).digest()`

`return h`

`def buildMerkleRoot(hash_list: list):`

`if len(hash_list) < 2:`

`return hash_list[0]`

`new_hash_list = []`

`# Process pairs. For odd length, the last is skipped`

`for i in range(0, len(hash_list) - 1, 2):`

`new_hash_list.append(hashOfJoinedStr(hash_list[i], hash_list[i + 1])[::-1].hex())`

`# odd, hash last item twice`

`if len(hash_list) % 2 == 1:`

`new_hash_list.append(hashOfJoinedStr(hash_list[-1], hash_list[-1])[::-1].hex())`

`return buildMerkleRoot(new_hash_list)`

**Program 6.3:** Program to build Merkle Root from Transaction hashes

We include the following lines in the code to make RPC calls to Bitcoin Core Server:

`from bitcoinrpc.authproxy import AuthServiceProxy, JSONRPCException`

`rpc_connection = AuthServiceProxy(“http://%s:%s@127.0.0.1:8332”%(<username>, <password>))We call the above-mentioned method as follows:`

`if __name__ == ‘__main__’:`

`block_hash = rpc_connection.getblockhash(715735)`

`block = rpc_connection.getblock(block_hash)`

`print(‘Merkle Root from RPC call\t = %s’ % block[‘merkleroot’])`

`hash_merkle_root = buildMerkleRoot(block[‘tx’])`

`print(‘Calculated Merkle Root\t = %s’ % hash_merkle_root)`

This gives us the following result:

![](images/Figure-6.16.jpg)

**Figure 6.16:** Program execution showing the calculated value of Merkle Root as equal to the value in the header

# [Bits and nonce](#toc.xhtml#s112a)

The next field to understand is Bits. Bits are a compressed representation of the Target Threshold. Block hash needs to be less than Target Threshold to be accepted as a valid block.

The following is the un-compression equation:

*b[1] b[2] b[3] b[4]: Four bytes of Bits*

*Target Threshold T= b[2] b[3] b[4].256^(b1-3))*

Let us see if the next Block, which has a block height of `715735`, has a block hash less than the target threshold.

*h: Block Hash*

*T: Target Threshold*

*h= 0000000000000000004db407202aff54e9ace0efb72588bb73a2beebb248c28*

*b[1] b[2] b[3] b[4] = 170b98ab*

*b[1]\=0x17,b[2] = 0x0b,b[3] = 0x98,b[4] = 0xab*

*T=0x0b98ab.256^(0x17-0x03)*

⇒*T=0x0b98ab.256^(0x14)*

Block is valid if *T* `>` *h*

The following program converts bits to get the target threshold:

`def getTargetThreshold(bits: bytes):`

`shift = bits[3]`

`value = int.from_bytes(bits[0:3], byteorder=’little’)`

`target_threshold = value * 2 ** (8 * (shift - 3))`

`return target_threshold`

**Program 6.4:** Program to convert bits in block header into Target Threshold

The following code calls this method and verifies that block hash has the needed proof-of-work:

`bits = bytes.fromhex(“170b98ab”)[::-1]`

`target_threshold = getTargetThreshold(bits)`

`print(‘Target Threshold = %x’ % target_threshold)`

`block_hash = 0x00000000000000000004db407202aff54e9ace0efb72588bb73a2beebb248c28`

`print(‘Block Hash = %x’ % block_hash)`

`print(‘Valid’ if target_threshold > block_hash else ‘Invalid’)`

This gives us the following result:

![](images/Figure-6.17.jpg)

**Figure 6.17:** Shows calculated value of Target Threshold from bits in the block header

# [Serialized block](#toc.xhtml#s113a)

Bitcoin serialized block also contains fields other than block header and transactions. These are the following fields:

*   Magic Number
*   Block Size

The following is the illustration of a serialized block:

![](images/Figure-6.18.jpg)

**Figure 6.18:** Figure shows the structure of serialized block

# [Magic number](#toc.xhtml#s114a)

Block hash is the hash of the block header. The magic number is the identifier of the network. If a node is connected to the same peer for multiple different coin networks, a block magic number can act as an identifier, and the node will not have to verify block consensus rules for multiple networks. This improves efficiency.

The public Bitcoin network on which bitcoin is transferred is also called *m*`ainnet`. There is also the testnet and regtest network, which is used for testing. Each of these networks has defined magic numbers and different port numbers to connect to peers.

![](images/133.jpg)

**Table 6.3:** Table showing magic numbers and TCP Port assigned for different Bitcoin networks

# [Block file](#toc.xhtml#s115a)

Bitcoin Core stores blockchain in a directory in the form of block files, and each block file contains multiple blocks in binary format. Block files are represented as follows:

![](images/Figure-6.19.jpg)

**Figure 6.19:** Illustration of block file structure

We can parse all the blocks in a block file by using block size from a serialized block. This helps in skipping any junk characters that may exist between two blocks. A block file will always start with the start of a serialized block, so we know that the first 4 bytes represent a magic number. From the block index, we can get the block count for a block file.

To access values using keys from the LevelDB indexes, we need to understand their structure. As we have learned, LevelDB is a binary key-value database that stores data in the filesystem. Bitcoin utilizes LevelDB to store multiple values and sometimes, multiple keys. To store variable length keys and values, Bitcoin uses a variable length integer format encoding. In this encoding, if the most significant bit in a byte is set, then the next byte is also included.

To encode, 7-bit is stored in a byte array, removed from the number, and then reduced by 1. This process is repeated till the bit becomes zero. The most significant bits of all bytes are set, except the last one.

![](images/Figure-6.20.jpg)

**Figure 6.20:** Illustration showing b128 varint encoding mechanism

The following is the implementation of the encoder:

`def b128_varint_encode(n: int):`

`l = 0`

`b = []`

`while True:`

`# Take 7 bits and set MSB if not last byte`

`b.append((n & 0x7F)| (0x80 if l != 0 else 0x00))`

`if n <= 0x7F:`

`break`

`n = (n >> 7) - 1`

`l += 1`

`return bytes(bytearray(b[::-1]))`

**Program 6.5:** Program to encode a number into b128 varint

The following code decodes variable length integer:

`def b128_varint_decode(b: bytes, pos = 0):`

`n = 0`

`while True:`

`data = b[pos]`

`pos += 1`

`# unset MSB bit`

`n = (n << 7) | (data & 0x7f)`

`if data & 0x80 == 0:`

`return (n, pos)`

`n += 1`

**Program 6.6:** Program to decode b128 varint into an integer

By running the preceding code, we get the following encoded and decoded integer pairs:

![](images/136.jpg)

![](images/137.jpg)

**Table 6.4:** Sample b128 varint encoded numbers

To parse blocks in block files, we need to get block file information from the block index. Block file index contains the following information:

*   `count`: Number of blocks stored in the block file
*   `filesize`: Size of block file in bytes
*   `undofilesize`: Size of undo file in bytes
*   `lowest`: Contains blocks from this block height
*   `highest`: Contains blocks till this block height
*   `Lowest_timestamp`: Contains blocks from this block timestamp
*   `highest_timestamp`: Contains blocks till this block timestamp

The following code gets block-file information from block index:

`block_db_g = plyvel.DB(os.getenv(‘BLOCK_INDEX_DB’), compression=None)`

`blocks_path_g = os.getenv(‘BLOCKS_PATH’)`

`def getBlockFileIndex(n_file: int, block_db):`

`key = b’f’ + (n_file).to_bytes(4, byteorder=’little’)`

`value = block_db.get(key)`

`jsonobj = {}`

`jsonobj[‘count’], pos = b128_varint_decode(value)`

`jsonobj[‘filesize’], pos = b128_varint_decode(value, pos)`

`jsonobj[‘undofilesize’], pos = b128_varint_decode(value, pos)`

`jsonobj[‘lowest’], pos = b128_varint_decode(value, pos)`

`jsonobj[‘highest’], pos = b128_varint_decode(value, pos)`

`jsonobj[‘lowest_timestamp’], pos = b128_varint_decode(value, pos)`

`jsonobj[‘highest_timestamp’], pos = b128_varint_decode(value, pos)`

`return jsonobj`

**Program 6.7:** Program to query Block DB to get block file index

We call this method with the following parameters:

`blk_index = getBlockFileIndex(138, block_db_g)`

Before executing the preceding program, we need to setup following environment variables:

`BITCOIN_HOME: Path of Bitcoin working directory.`

`BLOCK_INDEX_DB: This by default is $BITCOIN_HOME/blocks/index`

`BLOCKS_PATH: This by default is $BITCOIN_HOME/blocks/`

`CHAINSTATE_DB: This by default is $BITCOIN_HOME/chainstate`

`TX_INDEX_DB: This by default is $BITCOIN_HOME/indexes/txindex`

This gives the following result:

![](images/Figure-6.21.jpg)

**Figure 6.21:** Shows block file index structure obtained by running the program

Now, using the above-mentioned information, we have written the following code to parse the block file:

`def parseSerialisedBlock(block_f):`

`serialized_blk = {}`

`serialized_blk[‘magic_num’] = block_f.read(4)[::-1].hex()`

`serialized_blk[‘blk_size’] = int.from_bytes(block_f.read(4), byteorder=’little’)`

`serialized_blk[‘version’] = block_f.read(4)[::-1].hex()`

`prev_blkhash_b = block_f.read(32)`

`serialized_blk[‘prev_blkhash’] = prev_blkhash_b[::-1].hex()`

`serialized_blk[‘merkle_root_hash’] = block_f.read(32)[::-1].hex()`

`serialized_blk[‘time’] = int.from_bytes(block_f.read(4), byteorder=’little’)`

`serialized_blk[‘bits’] = block_f.read(4)[::-1].hex()`

`serialized_blk[‘nonce’] = block_f.read(4)[::-1].hex()`

`return serialized_blk`

**Program 6.8:** Program to get block header along with the magic number and block size

We iterate over the blockfile, finding all the blocks inside the file using the block information we get from the preceding method:

`if __name__ == ‘__main__’:`

`n_file = 138`

`block_filepath = os.path.join(blocks_path_g, ‘blk%05d.dat’ % n_file)`

`block_f = open(block_filepath, ‘rb’)`

`blk_index = getBlockFileIndex(n_file, block_db_g)`

`print(blk_index)`

`for i in range(blk_index[‘count’]):`

`# moves file pointer to the end of block header`

`serialized_blk = parseSerialisedBlock(block_f)`

`next_blk_loc = block_f.tell() - 80 + serialized_blk[‘blk_size’]`

`block_f.seek(next_blk_loc)`

`print(‘serialized_blk = %s’ % serialized_blk)`

Here is the information of the first two blocks in the block file:

![](images/Figure-6.22.jpg)

**Figure 6.22:** Shows the first two blocks in a block file and other information of the file

This method of parsing is useful in rescanning blocks for indexes.

# [Block traversal using block indexes](#toc.xhtml#s116a)

LevelDB indexes are helpful in several ways. They are helpful in the faster verification of blocks and transactions. We can use them to traverse blockchain, which is useful in case a fixed number of blocks need to be parsed, as in softfork deployment. Traversing blockchain using block file numbers and block file index is a more efficient method in other cases.

The following figure shows the block traversal steps:

![](images/Figure-6.23.jpg)

**Figure 6.23:** Illustration of method of traversing block file using LevelDB indexes

One thing we need to keep in mind is that blocks in a block file are not always in order, which means we always need to use previous block hash in a block header to get the location of the previous block.

Chainstate database is encoded, unlike other databases. This is because in the past, character sequence in the chainstate database had triggered anti-virus software. In this encoding method, each byte is XORed with bytes in obfuscate-key. Obfuscate key is stored in chainstate database under the b’\\x0e\\x00’ key.

The following code applies to obfuscate key to all the bytes and returns decoded chainstate values:

`def getObfuscationKey(chainstate_db):`

`value = chainstate_db.get(b’\x0e\x00’ + b’obfuscate_key’)`

`print(‘obfuscation key = %s’ % value)`

`obfuscation_key = value[1:]`

`return obfuscation_key`

`def applyObfuscationKey(data: bytes, chainstate_db):`

`obfuscation_key = getObfuscationKey(chainstate_db)`

`new_val = bytes(data[index] ^ obfuscation_key[index % len(obfuscation_key)] for index in range(len(data)))`

`return new_val`

**Program 6.9:** Program to decode LevelDB for chainstate using Obfuscation key

Now, we have enough understanding to traverse blockchain. Let us see how we can do that:

**Step 1:** Query last block hash from chainstate database.

**Step 2:** Query block hash in block index database to get block index.

**Step 3:** Block index has information on the location of the block. Using that, we read the correct block file or undo file and read data from the offset location to get block data.

**Step 4** From the block data, we get the block hash of the previous block and then repeat steps 2-4.

The following is the block index information obtained from the Block index database:

*   `version`: The version number of the client (Not the block).
*   `height`: Height of the block.
*   `status`: Indicates the kind of data it contains. It may be BLOCK_HAVE_DATA or BLOCK_HAVE_UNDO, indicating whether it forward patches or reverse patches chainstate data.
*   `txcount`: Transaction count in the block.
*   `n_file`: File number of the block file containing the block.
*   `data_pos`: Byte position of the data block.
*   `undo_pos`: Byte position of the undo block.
*   `header`: Block header content.

In the above-mentioned information, we come across reverse patching via the undo block. To understand this, we need to understand that blocks in Bitcoin blockchain may be competing to get the next spot. This happens because miners may mine a block almost at the same time, and one of the blocks will be accepted later as one of the competing chains will become longer. When this happens, undo blocks are used to reverse chainstate indexes.

Here’s the code to traverse the blockchain using LevelDB indexes:

1.  Get LevelDB databases:
    
    `block_db_g = plyvel.DB(os.getenv(‘BLOCK_INDEX_DB’), compression=None)`
    
    `chainstate_db_g = plyvel.DB(os.getenv(‘CHAINSTATE_DB’), compression=None)`
    
2.  Get last block hash from chainstate database:
    
    `def getRecentBlockHash(chainstate_db):`
    
    `key = b’B’`
    
    `block_hash_b = chainstate_db.get(key)`
    
    ` block_hash_b = applyObfuscationKey(block_hash_b, chainstate_db)`
    
    `return block_hash_b`
    
    **Program 6.10:** Program to get recent block from Chainstate DB
    
3.  Get block index from Block index database:
    
    `BLOCK_HAVE_DATA = 8`
    
    `BLOCK_HAVE_UNDO = 16`
    
    `def getBlockIndex(block_hash_b: bytes, block_db):`
    
    `key = b’b’ + block_hash_b`
    
    `value = block_db.get(key)`
    
    `jsonobj = {}`
    
    `jsonobj[‘version’], pos = b128_varint_decode(value)`
    
    `jsonobj[‘height’], pos = b128_varint_decode(value, pos)`
    
    `jsonobj[‘status’], pos = b128_varint_decode(value, pos)`
    
    `jsonobj[‘tx_count’], pos = b128_varint_decode(value, pos)`
    
    `if jsonobj[‘status’] & (BLOCK_HAVE_DATA | BLOCK_HAVE_UNDO):`
    
    ` jsonobj[‘n_file’], pos = b128_varint_decode(value, pos)`
    
    `if jsonobj[‘status’] & BLOCK_HAVE_DATA:`
    
    ` jsonobj[‘data_pos’], pos = b128_varint_decode(value, pos)`
    
    `if jsonobj[‘status’] & BLOCK_HAVE_UNDO:`
    
    ` jsonobj[‘undo_pos’], pos = b128_varint_decode(value, pos)`
    
    `jsonobj[‘header’] = {}`
    
    `jsonobj[‘header’][‘version’] = value[pos:pos+4][::-1].hex()`
    
    `jsonobj[‘header’][‘prevblockhash’] = value[pos+4:pos+36][::-1].hex()`
    
    `jsonobj[‘header’][‘merkleroot’] = value[pos+36:pos+68][::-1].hex()`
    
    `jsonobj[‘header’][‘time’] = value[pos+68:pos+72][::-1].hex()`
    
    `jsonobj[‘header’][‘bits’] = value[pos+72:pos+76][::-1].hex()`
    
    `jsonobj[‘header’][‘nonce’] = value[pos+76:pos+80][::-1].hex()`
    
    `return jsonobj`
    
    **Program 6.11:** Program to get block index structure from Block DB
    
4.  The following program parses block bytes to get block header information:
    
    `def getTransactionCount(mptr: mmap):`
    
    `prefix = int.from_bytes(mptr.read(1), byteorder=’little’)`
    
    `b_cnt_m = {‘fd’: 2, ‘fe’: 4, ‘ff’: 8}`
    
    `if prefix < 0xFD:`
    
    `tx_cnt = prefix`
    
    `else:`
    
    `b_cnt = b_cnt_m[‘%x’ % prefix]`
    
    `tx_cnt = int.from_bytes(mptr.read(b_cnt), byteorder=’little’)`
    
    `return tx_cnt`
    
    `def parseBlockHeader(mptr: mmap, start: int, height: int):`
    
    `seek = start-8`
    
    `mptr.seek(seek)`
    
    `block_header = {}`
    
    `block_header[‘magic_number’] = int.from_bytes(mptr.read(4), byteorder=’little’)`
    
    `block_header[‘block_size’] = int.from_bytes(mptr.read(4), byteorder=’little’)`
    
    `block_header[‘version’] = int.from_bytes(mptr.read(4), byteorder=’little’)`
    
    `prev_block_header_hash = mptr.read(32)`
    
    `block_header[‘prev_block_hash’] = prev_block_header_hash[::-1].hex()`
    
    `block_header[‘merkle_tree_root’] = mptr.read(32)[::-1].hex()`
    
    `block_header[‘timestamp’] = int.from_bytes(mptr.read(4), byteorder=’little’)`
    
    `block_header[‘date_time’] = datetime.datetime.fromtimestamp(block_header[‘timestamp’]).strftime(‘%Y-%m-%d %H:%M:%S’)`
    
    `block_header[‘bits’] = int.from_bytes(mptr.read(4), byteorder=’little’)`
    
    `block_header[‘nonce’] = int.from_bytes(mptr.read(4), byteorder=’little’)`
    
    `txcount = getTransactionCount(mptr)`
    
    `return block_header, prev_block_header_hash`
    
    **Program 6.12:** Program to get block header information
    

The following program uses the block index information to get block content and then finds the previous block using its block hash and the block index:

`def traverseBlockChain():`

`df = pd.DataFrame()`

`prev_blockhash_bigendian_b = getRecentBlockHash(chainstate_db_g)`

`blockheader_list = []`

`while True:`

` jsonobj = getBlockIndex(prev_blockhash_bigendian_b, block_db_g)`

`print(jsonobj[‘n_file’])`

`if ‘data_pos’ in jsonobj:`

`block_filepath = os.path.join(blocks_path_g, ‘blk%05d.dat’ % jsonobj[‘n_file’])`

`start = jsonobj[‘data_pos’]`

`print(‘height = %d’ % jsonobj[‘height’])`

`elif ‘undo_pos’ in jsonobj:`

`block_filepath = os.path.join(blocks_path_g, ‘rev%05d.dat’ % jsonobj[‘n_file’])`

`start = jsonobj[‘undo_pos’]`

`# load file to memory`

`with open(block_filepath, ‘rb’) as block_file:`

`with mmap.mmap(block_file.fileno(), 0, prot = mmap.PROT_READ, flags = mmap.MAP_PRIVATE) as mptr: #File is open read-only`

`blockheader, prev_blockhash_bigendian_b = parseBlockHeader(mptr, start, jsonobj[‘height’])`

`blockheader[‘height’] = jsonobj[‘height’]`

`blockheader[‘tx_count’] = jsonobj[‘tx_count’]`

`blockheader_list.append(blockheader)`

`if jsonobj[‘height’] == 1:`

`break`

`df = pd.DataFrame(blockheader_list)`

`df.to_csv(‘out.csv’, index=False)`

**Program 6.13:** Program to traverse Bitcoin blockchain

We call the preceding program as follows:

`if __name__ == ‘__main__’:`

`traverseBlockChain()`

We get `out.csv`, which contains a portion of the following few rows:

![](images/Figure-6.24.jpg)

**Figure 6.24:** Shows the first few traversed block information

This completes the blockchain section. You understood the structure of blockchain, how these blocks are stored and how these blocks can be read, traversed, and parsed to get header and preheader fields.

# [Transactions](#toc.xhtml#s117a)

When one party pays another in bitcoin, the sender creates a transaction and publishes it to the Bitcoin network. We discussed this in *[Chapter 5, The Whitepaper](#c05.xhtml),* in detail.

In this section, we will look at how transactions are stored, their format, how they are verified, and other related information.

Transactions are stored one after the other in the block after transaction count. Block has its own variable length integer format. This is different from the LevelDB variable integer format we learned about in the previous section. This is a bit simpler. A prefix indicates the length of the integer.

![](images/Figure-6.25.jpg)

**Figure 6.25:** Variable integer format used by LevelDB index value structure

In the preceding subtopic ***Block traversal using block indexes*** we used a method name `getTransactionCount`.

To call `getTransactionCount`, we pass bytes of trimmed block with block hash. The following is the calling code:

`blk_h = ‘00e0ff376a2079af63073c47184cd091819d506f12cb6b68887c040000000000000000001036e0b1059b1ec79cb36897ccf8bc5aef4c7996897b83754ab590bb2774bc2726c0475fea0710178ffaf153fda4090100000000010100000000000000000000’`

`blk_b = bytes.fromhex(blk_h)`

`blk_m = mmap.mmap(-1, len(blk_b) + 1)`

`blk_m.write(blk_b)`

`blk_m.seek(80)`

`tx_count = getTransactionCount(blk_m)`

`print(‘Transaction Count = %d’ % tx_count)`

On running this, we get the following result:

![](images/Figure-6.26.jpg)

**Figure 6.26:** Shows transaction count in a block from the preceding program

In the list of transactions, the first transaction is the coinbase transaction. This is a special transaction because it is created by a miner to pay itself block reward and transaction fees collected from transactions in the block. This transaction also adds bitcoin to the supply of coins. The transaction has no input txouts.

The structure of this transaction is as follows:

![](images/Figure-6.27.jpg)

**Figure 6.27:** Coinbase transaction structure

The following program parses coinbase transaction:

`import mmap`

`import json`

`def getVarInt(blk_m: mmap):`

`b_cnt_d = {‘fd’: 2, ‘fe’: 4, ‘ff’: 8}`

`prefix = int.from_bytes(blk_m.read(1), byteorder=’little’)`

`if prefix < 0xFD:`

`return prefix`

`else:`

`b_cnt = b_cnt_d[‘%x’ % prefix]`

`size = int.from_bytes(blk_m.read(b_cnt), byteorder=’little’)`

`return size`

`def getCoinbaseTransactionInfo(blk_m: mmap):`

`tx = {}`

`tx[‘version’] = blk_m.read(4)[::-1].hex()`

`tx[‘inp_cnt’] = getVarInt(blk_m)`

`inp_l = []`

`for i in range(tx[‘inp_cnt’]):`

`inp = {}`

`inp[‘prev_tx_hash’] = blk_m.read(32)[::-1].hex()`

`inp[‘prev_tx_out_index’] = int.from_bytes(blk_m.read(4), byteorder = ‘little’)`

`inp[‘bytes_coinbase_data’] = getVarInt(blk_m)`

`pos = blk_m.tell()`

`inp[‘bytes_height’] = getVarInt(blk_m)`

`inp[‘height’] = int.from_bytes(blk_m.read(inp[‘bytes_height’]), byteorder=’little’)`

`size = blk_m.tell() - pos`

`coinbase_arb_data_size = inp[‘bytes_coinbase_data’] - size`

`inp[‘coinbase_arb_data’] = blk_m.read(coinbase_arb_data_size).hex()`

`inp[‘sequence’] = int.from_bytes(blk_m.read(4), byteorder = ‘little’)`

`inp_l.append(inp)`

`tx[‘inputs’] = inp_l`

`tx[‘out_cnt’] = getVarInt(blk_m)`

`out_l = []`

`for i in range(tx[‘out_cnt’]):`

`out = {}`

`out[‘satoshis’] = int.from_bytes(blk_m.read(8), byteorder=’little’)`

`out[‘bytes_scriptpubkey’] = getVarInt(blk_m)`

`out[‘scriptpubkey’] = blk_m.read(out[‘bytes_scriptpubkey’]).hex()`

`out_l.append(out)`

`tx[‘outs’] = out_l`

`tx[‘locktime’] = int.from_bytes(blk_m.read(4), byteorder=’little’)`

`return tx`

**Program 6.14:** Program to get transaction structure from block bytes

To get the transaction information, we use a trimmed block byte, create a memory-mapped file object, and pass the object to `getCoinbaseTransactionInfo` as a parameter. Here’s the calling code:

`if __name__ == ‘__main__’:`

`# trimmed block for block hash 000000000000000004ec466ce4732fe6f1ed1cddc2ed4b328fff5224276e3f6f`

`blk_b = bytes.fromhex(‘0400000039fa821848781f027a2e6dfabbf6bda920d9ae61b63400030000000000000000ecae536a304042e3154be0e3e9a8220e5568c3433a9ab49ac4cbb74f8df8e8b0cc2acf569fb9061806652c27fd7c0601000000010000000000000000000000000000000000000000000000000000000000000000ffffffff3f03801a060004cc2acf560433c30f37085d4a39ad543b0c000a425720537570706f727420384d200a666973686572206a696e78696e092f425720506f6f6c2fffffffff012fd8ff96000000001976a914721afdf638d570285d02d3076d8be6a03ee0794d88ac00000000’)`

`blk_m = mmap.mmap(-1, len(blk_b) + 1)`

`blk_m.write(blk_b)`

`blk_m.seek(0)`

`blkhdr = blk_m.read(80)`

`blk_size = getVarInt(blk_m)`

`tx = getCoinbaseTransactionInfo(blk_m)`

` print(json.dumps(tx, indent = 4))`

On running the code, we get the following transaction structure:

![](images/Figure-6.28.jpg)

**Figure 6.28:** Shows coinbase transaction structure obtained using the program

As we can see, the version of the transaction is 1. The Bitcoin network, as of today, allows both version 1 and version 2. Version 2 must be used if the BIP-68 feature is used in the transaction script; otherwise, there is no difference in both versions.

The transaction has 1 input and 1 output. Since it is a coinbase transaction, there is no input transaction, and the input contains transaction hash as zeroes and index as 0xffffffff. This indicates that this is a coinbase transaction.

Next is the size of `coinbase_data`. This includes the height of the block since block version 2.

The `coinbase_arb_data field in the coinbase transaction is an arbitrary sequence of bytes which` can be anything that the miner wants to put. Sometimes, miners add a message to show their support for certain enhancements. If we convert the hex code to bytes, we can see the hidden message:

![](images/Figure-6.29.jpg)

**Figure 6.29:** Shows content on coinbase arbitrary data

We can see the message `BW Support 8M fisher jinxin /BW Pool/`. The block is mined by BW Pool, and they support an 8 MB block size.

In the outputs, the first 8 bytes are bitcoin paid by the miner to its Bitcoin addresses. This value is represented as satoshi, which is the smallest denomination in bitcoin:

1 bitcoin=10⁸ satoshi

1 bitcoin=10⁶ μ₿

1 bitcoin=10³ m₿

So, the combined value of all the `satoshis` in outputs is equal to the sum of block reward and transaction fees collected by adding transactions in the block.

The payment to the Bitcoin address is done through a script called `scriptPubKey`. We will understand the scripting that Bitcoin transaction uses in the upcoming chapters.

Other transactions are illustrated as follows:

![](images/Figure-6.30.jpg)

**Figure 6.30:** Structure of other transactions in a block

Locktime locks the transaction till the specified time or block height. This means the transaction will remain in mempool and not be included in the blockchain. Specified time is median time past instead of block time. It is recommended that this field be set. For locktime to be used, at least one Sequence field among Inputs should not be equal to 0xffffffff.

The inputs contain the previous transaction hash, also called Transaction ID, and its unspent output from which value needs to be taken to pay the outputs. The transaction hash is obtained by applying SHA256 twice, so it is 32 bytes in length. ScriptSig is the script containing a signature to prove that the bitcoin held in the previous transaction output belongs to the person who created the transaction input in this transaction.

The following code parses the other transactions of the block:

`def getTransactionInfo(blk_m: mmap):`

`tx = {}`

`tx[‘version’] = blk_m.read(4)[::-1].hex()`

`tx[‘inp_cnt’] = getVarInt(blk_m)`

`inp_l = []`

`for i in range(tx[‘inp_cnt’]):`

`inp = {}`

`inp[‘prev_tx_hash’] = blk_m.read(32)[::-1].hex()`

`inp[‘prev_tx_out_index’] = int.from_bytes(blk_m.read(4), byteorder=’little’)`

`inp[‘bytes_scriptsig’] = getVarInt(blk_m)`

`inp[‘scriptsig’] = blk_m.read(inp[‘bytes_scriptsig’]).hex()`

`inp[‘sequence’] = int.from_bytes(blk_m.read(4), byteorder=’little’)`

`inp_l.append(inp)`

`tx[‘inputs’] = inp_l`

`tx[‘out_cnt’] = getVarInt(blk_m)`

`out_l = []`

`for i in range(tx[‘out_cnt’]):`

`out = {}`

`out[‘satoshis’] = int.from_bytes(blk_m.read(8), byteorder=’little’)`

`out[‘bytes_scriptpubkey’] = getVarInt(blk_m)`

`out[‘scriptpubkey’] = blk_m.read(out[‘bytes_scriptpubkey’]).hex()`

`out_l.append(out)`

`tx[‘outs’] = out_l`

`tx[‘locktime’] = int.from_bytes(blk_m.read(4), byteorder=’little’)`

`return tx`

**Program 6.15:** Program to parse transactions

To call the method, we need to provide a `getTransactionInfo` memory map of bytes of `bblock`. The following is the code to call the method:

`if __name__ == ‘__main__’:`

` # trimmed block for block hash 000000000000000082ccf8f1557c5d40b21edabb18d2d691cfbf87118bac7254`

`blk_b = bytes.fromhex(‘020000007ef055e1674d2e6551dba41cd214debbee34ae b544c7ec670000000000000000d3998963f80c5bab43fe8c26228e98d030edf4dcbe48a666f5c39e2d7a885c9102c86d536c890019593a470ded01000000010000000000000000000000000000000000000000000000000000000000000000ffffffff4803e09304062f503253482f0403c86d53087ceca141295a00002e522cfabe6d6d7561cf262313da1144026c8f7a43e3899c44f6145f39a36507d36679a8b7006104000000000000000000000001c8704095000000001976a91480ad90d403581fa3bf46086a91b2d9d4125db6c188ac0000000001000000014dff4050dcee16672e48d755c6dd25d324492b5ea306f85a3ab23b4df26e16e9000000008c493046022100cb6dc911ef0bae0ab0e6265a45f25e081fc7ea4975517c9f848f82bc2b80a909022100e30fb6bb4fb64f414c351ed3abaed7491b8f0b1b9bcd75286036df8bfabc3ea5014104b70574006425b61867d2cbb8de7c26095fbc00ba4041b061cf75b85699cb2b449c6758741f640adffa356406632610efb267cb1efa0442c207059dd7fd652eeaffffffff020049d971020000001976a91461cf5af7bb84348df3fd695672e53c7d5b3f3db988ac30601c0c060000001976a914fd4ed114ef85d350d6d40ed3f6dc23743f8f99c488ac00000000’)`

`blk_m = mmap.mmap(-1, len(blk_b) + 1)`

`blk_m.write(blk_b)`

`blk_m.seek(80)`

`tx_cnt = getVarInt(blk_m)`

`coinbase_tx = getCoinbaseTransactionInfo(blk_m)`

`tx = getTransactionInfo(blk_m)`

`print(‘Transaction:’)`

`print(json.dumps(tx, indent=4))`

This gives out the following content of the first transaction after coinbase transaction:

![](images/Figure-6.31.jpg)

**Figure 6.31:** Shows a transaction structure

To calculate transaction hash, we need to get the transaction bytes and hash by applying SHA256 twice and reverse byte order. The following method calculates transaction hash from transaction bytes:

`def getTransactionHash(start: int, end: int, blk_b: bytes):`

`b = blk_b[start: end]`

`h١ = hashlib.sha256(b).digest()`

`h٢ = hashlib.sha256(h1).digest()`

`tx_hash = h2[::-1].hex()`

`return tx_hash`

**Program 6.16:** Program to get Transaction ID from transaction bytes

The following code calls the method:

`if __name__ == ‘__main__’:`

`# trimmed block for block hash 000000000000000082ccf8f1557c5d40b21edabb18d2d691cfbf87118bac7254`

`blk_b = bytes.fromhex(‘020000007ef055e1674d2e6551dba41cd214debbee34ae b544c7ec670000000000000000d3998963f80c5bab43fe8c26228e98d030edf4dcbe48a666f5c39e2d7a885c9102c86d536c890019593a470ded01000000010000000000000000000000000000000000000000000000000000000000000000ffffffff4803e09304062f503253482f0403c86d53087ceca141295a00002e522cfabe6d6d7561cf262313da1144026c8f7a43e3899c44f6145f39a36507d36679a8b7006104000000000000000000000001c8704095000000001976a91480ad90d403581fa3bf46086a91b2d9d4125db6c188ac0000000001000000014dff4050dcee16672e48d755c6dd25d324492b5ea306f85a3ab23b4df26e16e9000000008c493046022100cb6dc911ef0bae0ab0e6265a45f25e081fc7ea4975517c9f848f82bc2b80a909022100e30fb6bb4fb64f414c351ed3abaed7491b8f0b1b9bcd75286036df8bfabc3ea5014104b70574006425b61867d2cbb8de7c26095fbc00ba4041b061cf75b85699cb2b449c6758741f640adffa356406632610efb267cb1efa0442c207059dd7fd652eeaffffffff020049d971020000001976a91461cf5af7bb84348df3fd695672e53c7d5b3f3db988ac30601c0c060000001976a914fd4ed114ef85d350d6d40ed3f6dc23743f8f99c488ac00000000’)`

`blk_m = mmap.mmap(-1, len(blk_b) + 1)`

`blk_m.write(blk_b)`

`blk_m.seek(80)`

`tx_cnt = getVarInt(blk_m)`

`coinbase_tx = getCoinbaseTransactionInfo(blk_m)`

`stb = blk_m.tell()`

`tx = getTransactionInfo(blk_m)`

`endb = blk_m.tell()`

`tx_hash = getTransactionHash(stb, endb, blk_b)`

`print(‘Transaction Hash = %s’ % tx_hash)`

This gives us the following result:

![](images/Figure-6.32.jpg)

**Figure 6.32:** Shows transaction hash obtained from transaction bytes using the program

We can search this transaction in `txindex` by using the following code:

`txindex_db_g = plyvel.DB(os.getenv(‘TX_INDEX_DB’), compression=None)`

`BLOCK_HEADER_SIZE = 80`

`def getTransactionIndex(tx_hash: bytes, txindex_db):`

`key = b’t’ + tx_hash`

`value = txindex_db.get(key)`

`jsonobj = {}`

`jsonobj[‘n_file’], pos = b128_varint_decode(value)`

`jsonobj[‘block_offset’], pos = b128_varint_decode(value, pos)`

`jsonobj[‘file_offset’], pos = b128_varint_decode(value, pos)`

`print(jsonobj)`

`return jsonobj`

`def findTransaction(tx_hash: bytes, txindex_db):`

`jsonobj = getTransactionIndex(tx_hash, txindex_db)`

`print(‘Transaction Index:’)`

`print(json.dumps(jsonobj, indent=4))`

`block_filepath = os.path.join(blocks_path_g, ‘blk%05d.dat’ % jsonobj[‘n_file’])`

`with open(block_filepath, ‘r+b’) as blk_f:`

`blk_m = mmap.mmap(blk_f.fileno(), 0) # map whole file`

`blk_m.seek(jsonobj[‘block_offset’] + BLOCK_HEADER_SIZE + jsonobj[‘file_offset’])`

`tx = getTransactionInfo(blk_m)`

`blk_m.close()`

`return tx`

**Program 6.17:** Program to find transaction using transaction index in DB

The `findTransaction` method takes transaction hash in the little-endian format and chainstate database for querying the index. The following is the example code:

`if __name__ == ‘__main__’:`

`tx_hash = bytes.fromhex(‘7301b595279ece985f0c415e420e425451fcf7f684fcce087ba14d10ffec1121’)[::-1]`

`tx = findTransaction(tx_hash, txindex_db_g)`

` print(“Transaction Info:\n”, json.dumps(tx, indent = 4))`

Running this code gives us the following information about the location of the transaction in the block file and also a portion of a parsed transaction:

![](images/Figure-6.33.jpg)

**Figure 6.33:** Shows information required to read transaction in a block file and shows a portion of a parsed transaction

# [UTXO](#toc.xhtml#s118a)

UTXO stands for **Unspent Transaction Output**. The primary purpose of the chainstate database is to store this information so that a new transaction can be efficiently verified.

To parse UTXO information from the chainstate database, we need to understand a few more things. Transaction output has an amount field that is encoded to compress its value. The following is the compression program:

`def amount_compress(n: int):`

`if n == 0:`

`return 0;`

`e = 0`

`while ((n % 10) == 0) and e < 9:`

`n //= 10`

`e += 1`

`if e < 9:`

`d = n ٪ 10`

`assert d >= 1 and d <= 9`

`n //= 10`

`return 1 + (n*9 + d - 1)*10 + e`

`else:`

`return 1 + (n - 1)*10 + 9`

**Program 6.18:** Program to compress amount in UTXO

And here’s the program to decompress value:

`def amount_decompress(x):`

` if x == 0:`

` return 0`

`x -= 1`

`e = x ٪ 10`

`x //= 10`

`if e < 9:`

`d = (x ٪ 9) + 1`

`x //= 9`

`n = x * 10 + d`

`else:`

`n = x + 1`

`while e > 0:`

`n *= 10`

`e -= 1`

`return n`

**Program 6.19:** Program to decompress amount in UTXO

*[Table 6.1](#c06.xhtml#tab6_1)* gives information about transaction output available in the chainstate database. To concatenate transaction ID without index, we need to encode it using b128 encoding. Additionally, the script field is not encoded in b128 encoding as it is a fixed-size field.

The following program gets stored values related to UTXO:

`def getUnspentTransactions(tx_hash: bytes, out_index: int,chainstate_db):`

`key = b’C’ + tx_hash + b128_varint_encode(out_index)`

`value_obf_b = chainstate_db.get(key)`

`value_obf_b = applyObfuscationKey(value_obf_b, chainstate_db)`

`jsonobj = {}`

`code, pos = b١٢٨_varint_decode(value_obf_b)`

`jsonobj[‘is_coinbase’] = code & 0x01`

`jsonobj[‘block_height’] = code >> 1`

`compressed_amount, pos = b128_varint_decode(value_obf_b, pos)`

`jsonobj[‘unspent_amount’] = amount_decompress(compressed_amount)`

`jsonobj[‘script_type’], pos = b128_varint_decode(value_obf_b, pos)`

`jsonobj[‘scriptPubKey’]= value_obf_b[pos:].hex()`

`return jsonobj`

**Program 6.20:** Program to get the structure of UTXO

The preceding method, `getUnspentTransactions`, takes transaction hash, output index that is unspent, and chainstate database. The following is the example of a calling statement:

`if __name__ == ‘__main__’:`

`tx = bytes.fromhex(‘a23203c053852755c97b87e354d1e9053a6d1a20d32892e8ee45dfa2c3105f94’)[::-1]`

`jsonobj = getUnspentTransactions(tx, 0, chainstate_db_g)`

`print(jsonobj)`

This is the result:

![](images/Figure-6.34.jpg)

**Figure 6.34:** Shows information stored in Chainstate DB for a UTXO

In the preceding result, `scriptPubKey` is not a full script; it needs script type to get the full script. The following code prints full `scriptPubKey` for script type 0:

`def uncompressScriptType0(script_data: bytes):`

`script = bytes([`

` 0x76, # OP_DUP`

` 0xa9, # OP_HASH160`

` 20 # size`

` ]) + script_data + bytes([`

` 0x88, # OP_EQUALVERIFY`

` 0xac # OP_CHECKSIG`

` ])`

`return script`

**Program 6.21:** Program to get scriptPubKey using script types and script data

We have not covered other scripts as the transaction scripting is left for the upcoming chapters.

The following is the code for calling the preceding method:

`if __name__ == ‘__main__’:`

`script_data = bytes.fromhex(‘3eba92179cd0b4caff74e3e81a14399e3c1b7ca3’)`

`script = uncompressScriptType٠(script_data)`

`print(‘script = %s’ % script.hex())`

This gives us the following script:

![](images/Figure-6.35.jpg)

**Figure 6.35:** Shows the scriptPubKey obtained by uncompressing script data

This concludes this section on transactions. In this section, we were primarily focused on transaction format and transaction indexes in databases. Scripting has been left for the upcoming chapters.

# [Mining](#toc.xhtml#s119a)

Mining is the process of finding nonce and creating a block. We have learned a few things in previous sections and chapters that will be useful in understanding the mining process.

Mining involves the following:

*   Spending energy to find nonce, which is required to create block hash that has value less than the target threshold.
*   Knowledge of block reward.
*   Selecting transactions from mempool to maximize transaction reward within the block size limit.
*   Creation of coinbase transaction using block reward, transaction fee, block height, and scriptPubKey for paying the rewards to own address.
*   Finding Merkle Root.
*   Finding Target threshold for the next block.
*   Readying and supporting softforks.
*   Creating other fields in the block header.

In this section, we will investigate each of these.

# [Mining profitability](#toc.xhtml#s120a)

To calculate mining profitability, we need to understand how much energy is required to find nonce using popular mining devices and how much is the block reward and total transaction fee earned in each transaction.

# [Block reward](#toc.xhtml#s121a)

Block reward is a mechanism by which bitcoin are created. Block reward is decreasing with time. When the Bitcoin network was created, block reward was 50![](images/Bitcoin.jpg)in each block. Currently, it is 6.25![](images/Bitcoin.jpg). After every 210,000 blocks, the block reward becomes half. This reduces the supply of newly minted bitcoin.

The following program gives block reward for given block height:

`def getBlockReward(block_height):`

`halving_count = block_height // 210000`

`block_reward = 50/(2**halving_count)`

`return block_reward`

**Program 6.22:** Program to get block reward for a given block height

We call this method for given block height, as follows:

`if __name__ == ‘__main__’:`

`block_reward = getBlockReward(645675)`

`print(block_reward)`

This gives us the following result:

![](images/Figure-6.36.jpg)

**Figure 6.36:** Shows block reward obtained by running the preceding program

This means the block reward for the block that has a height of `645675` is `6.25₿`.

# [Transaction fee](#toc.xhtml#s122a)

We can calculate the transaction fee of a transaction with the following equation:

*f : Transaction Fee*

*i[n]: n^(th) input*

*o[n]: n^(th) output*

*f = ∑[n]i[n] - ∑[n]o[n] (1)*

To write a program to calculate the transaction fee for a transaction, we need to look up the previous transaction in txindex. A node always verifies transactions against previously unspent transaction output that is stored in chainstate database or is in mempool. All transactions in a block are already verified. A node only needs to verify the block header and Merkle root hash from the list of transactions included in the block. Since we are trying to look for previous transaction output of already verified and confirmed transactions, we need txindex to look for the transaction.

The following method returns the value of bitcoin locked in a transaction output:

`def getTransactionOutAmount(tx_hash: bytes, out_index: int, txindex_db):`

`tx = findTransaction(tx_hash, txindex_db)`

`return tx[‘outs’][out_index][‘satoshis’]`

**Program 6.23:** Program gets UTXO amount from txindex

The method calls `findTransaction` defined in *program 6.17*.

The following method uses the value locked in a transaction input from the preceding method and returns the transaction fee associated with the transaction:

`def getTransactionFee(tx: dict):`

`inp_val = 0`

`for inp in tx[‘inputs’]:`

`prev_tx_hash = bytes.fromhex(inp[‘prev_tx_hash’])[::-1]`

`inp_val += getTransactionOutAmount(prev_tx_hash, inp[‘prev_tx_out_index’], txindex_db_g)`

`out_val = 0`

`for out in tx[‘outs’]:`

`out_val += out[‘satoshis’]`

`tx_fee = inp_val - out_val`

`return tx_fee`

**Program 6.24:** Program gets transaction fee collected by a miner for the given transaction

Now, we can add all the transaction fees collected from the transaction list in a block. The following is the program that calculates the fee reward collected by a block miner:

`def getBlockFeeReward(block_hash: bytes, block_db):`

`block_index = getBlockIndex(block_hash, block_db)`

`if ‘data_pos’ in block_index:`

`block_filepath = os.path.join(blocks_path_g, ‘blk%05d.dat’ % block_index[‘n_file’])`

`start = block_index[‘data_pos’]`

`elif ‘undo_pos’ in block_index:`

`block_filepath = os.path.join(blocks_path_g, ‘rev%05d.dat’ % block_index[‘n_file’])`

`start = block_index[‘undo_pos’]`

`with open(block_filepath, ‘r+b’) as block_f:`

`blk_m = mmap.mmap(block_f.fileno(), 0)`

`blk_m.seek(start + BLOCK_HEADER_SIZE)`

`tx_cnt = getVarInt(blk_m)`

`print(tx_cnt)`

`coinbase_tx = getCoinbaseTransactionInfo(blk_m)`

`print(coinbase_tx)`

`fee_reward = 0`

`for i in range(1, tx_cnt):`

` print(i)`

` start = blk_m.tell()`

` tx = getTransactionInfo(blk_m)`

` end = blk_m.tell()`

` tx_fee = getTransactionFee(tx)`

` print(tx_fee)`

` fee_reward += tx_fee`

`return fee_reward`

**Program 6.25:** Program to calculate transaction fee collected by a miner for mining a block

In the preceding code, `getCoinbaseTransactionInfo` and `getTransactionInfo` are defined in *program 6.14* and *program 6.15*.

We call the method by executing the following code:

`if __name__ == ‘__main__’:`

`block_hash_b = bytes.fromhex(‘000000000000000004ec466ce4732fe6f1ed1cddc2ed4b328fff5224276e3f6f’)[::-1]`

`total_tx_fee = getBlockFeeReward(block_hash_b, block_db_g)`

`print(‘Fee Reward = %d’ % total_tx_fee)`

On running the code, we get the following result:

![](images/Figure-6.37.jpg)

**Figure 6.37:** Shows transaction fee collected by a miner for mining the given block

The block hash we used is of the block with block height `400000`, which had a mining reward of `2500000000` satoshi.

# [Coinbase transaction amount verification](#toc.xhtml#s123a)

Using block reward and the sum of transaction fees, we can verify that the total bitcoin collected by the miner is correct, and they have not paid themselves extra. The sum of satoshi of outputs of coinbase transaction gives us the amount that the miner paid to themselves. The following is the total reward the miner paid to themselves:

![](images/Figure-6.38.jpg)

**Figure 6.38:** Shows coinbase transaction output value paid to the miner

We can see that the miner paid themselves `2533349423 satoshi`, which is equal to the sum of the block reward and fee reward we calculated.

# [Mining cost](#toc.xhtml#s124a)

Miners find nonce by continuously trying new values, which requires a lot of CPU processing and, consequently, energy. Mining equipment also produces a lot of noise and heat, which a miner needs to manage. The high-energy equipment also requires sufficient electricity load, fire safety, and maintenance. Additionally, as interest in mining has historically gone up and better mining equipment has been produced, mining profitability has gone down. Depending on the cost of electricity consumed and bitcoin mined by the equipment, there is a possibility that older equipment starts leading to losses and so, upgradation of equipment might become a necessity.

So, anyone getting into mining must ensure that the cost of electricity is low, and apart from spending on maintenance and security, they also should spend a significant portion of the profit on mining equipment upgradation and expansion.

To calculate electricity cost, we need to understand the network hash power needed to find the required nonce. Network hash power needed to find the nonce is the consequence of the difficulty in finding the nonce, so it depends on the probability that the block hash will fall below the target threshold. Since hashing generates a random 256-bit code, there are possible outcomes.

Possible values of nonce less than 1 are only 0, so the probability of finding them is .

Possible values of nonce less than 2 are 0 and 1, so the probability of finding them is .

This gives us:

*p: probability of finding nonce*

*T: Target Threshold*

*p=T/2*^(256) (1)

Mining equipment tries to find the hashes at an extremely fast rate.

The hash rate of 1 TH/s is hashes per second. The following calculation finds the hash rate of the Bitcoin network:

*t[b]: Block time in seconds*

*H[network]: Hash rate of network*

*(1)* ⇒ *Number of trials required = H[network] t[b]\=2^(256)/T*

⇒*H[network] = 2^(256) / Tt[b]*

Using the preceding equation, we can find the current hash rate of network:

Target threshold of block with block height *645675* is

*T = 0x1007ea0000000000000000000000000000000000000000*

*H[network] = 2256/(600\*T)=125,686,927,612,715,270,144*

As we can see, the value is 125 exa-hashes per second. This has grown exponentially over time. The following is the chart showing the rise in network hashrate over time:

![](images/Figure-6.39.jpg)

**Figure 6.39:** Bitcoin network hashrate over the years

Even though network hashrate has gone up exponentially, there have been short durations when the hashrate has fallen. This has happened when miners started losing money and had to stop mining. This is a crucial difference between Bitcoin mining and commodity mining. The cost of mining in bitcoin is quite elastic and adjusts based on mining profitability, while in regular mining, a fall in profit does not lead to a fall in the cost of mining. Additionally, commodity miners need to continue mining as shutting the mines and reopening is costly and sometimes difficult. So, regular commodity mining always runs a risk that if no further cheap reserves are found, then mining would need to be abandoned or prices must rise. Thus, price rise leads to more supply. In contrast, in bitcoin, inflation is fixed by the algorithm, so mining profitability and network hashrate do not cause changes in bitcoin production. This secures bitcoin inflation from any external influence like bans or restrictions.

The mining equipment cost thousands of dollars. The equipment with the highest hash power has crossed 100 Tera hashes per second (TH/s). For a miner to mine a block using equipment with 100 Tera hashes, they will need:

![](images/c06eq-1.jpg)

As we can see, even 100 TH/s is not sufficient to mine a block. For this reason, mining is almost never done solo. To perform mining as a business, a miner needs to join a mining pool. Mining pools operate by trying to find nonce collectively. Each participant contributes to the pool their CPU power to find nonce. It makes no difference who in the pool successfully finds nonce. The pool uses the nonce to prepare a block and then shares the profit with all the participants in the pool according to their contribution of mining hash power. This is a very democratic system, but it makes mining more centralized. Since profits are only shared when the nonce is found, every miner prefers to join a mining pool that has the highest accumulated hash power as this increases the probability of finding a nonce and more frequent sharing of profit. Consequently, the Bitcoin network has some big mining pools, and if only they join hands to dominate the consensus rules, then the developers and other stakeholders may lose their value, and the network will be taken over by only a few players.

At the time of authoring this book, the following are the few top mining pools:

*   Foundry USA
*   AntPool
*   Fool
*   Poolin
*   Binance Pool
*   VIABLE
*   BTC.com
*   SlushPool

Bitcoin mining is done using ASIC miners, which are specifically designed to perform SHA256 operations at an extremely fast rate. Choosing the right miner depends on several factors, such as input cost, power consumption, the amount of heat and noise produced, efficiency, the source of electricity, and time to breakeven.

A new miner may be more power efficient but may cost an exorbitant amount of money, which can push time to breakeven farther. A cheap or free power source can make low-efficiency equipment more economical.

Plus, the following two popular pooled mining protocols can be used for mining:

*   Stratum
*   Stratum V2

As the name suggests, Stratum V2 is the newer version of Stratum protocol. These are open protocols and are widely used for pooled mining. Stratum V2 is two to three times more efficient than version 1. Version 2 also gives better control to individual miners in terms of customization of block template, which can allow miners to individually decide the enhancements it intends to support or not support.

There are also the popular pool mining software:

*   Nice Hash
*   Better Hash
*   Cuddle Miner

Each of the above-mentioned software have advantages and disadvantages and will depend on individual requirements.

Most mining pools leave their signature in the arbitrary data of coinbase transactions when they create a block. Using these signatures, we can figure out the percentage of blocks mined by each mining pool.

Using the cost of electricity, we can calculate the average monthly profit of mining equipment.

First, we need to define mining hash rate, electricity expense and current sell price of bitcoin:

`MINER_HASH_RATE = 96 * 10**12`

`MINER_POWER_WATT = 2832`

`electricity_rates = {“rate_slabs”: [{“min”: 1, “max”: 30, “unit_price”: 4}, {“min”: 31, “max”: 100, “unit_price”: 5.45}, {“min”: 101, “max”: 200, “unit_price”: 7}, {“min”: 201, “unit_price”: 8.05}]}`

`CURRENT_SELL_PRICE = 3070000`

`def getPriceFromUnit(unit: float):`

`rate_slabs = electricity_rates[‘rate_slabs’]`

`price = 0`

`for slab in rate_slabs:`

`if slab[‘min’] > unit:`

`countinue`

`elif (‘max’ in slab and slab[‘max’]) > unit or ‘max’ not in slab:`

`price += (unit - slab[‘min’]) * slab[‘unit_price’]`

`else:`

`price += (slab[‘max’] - slab[‘min’]) * slab[‘unit_price’]`

`return price`

**Program 6.26:** Program to define miner hashrate, electricity expense and price of bitcoin

We also need to calculate network hash rate:

`def getTargetThreshold(bits: bytes):`

`shift = bits[3]`

`value = int.from_bytes(bits[0:3], byteorder=’little’)`

`target_threshold = value * 2 ** (8 * (shift - 3))`

`return target_threshold`

`def getNetworkHashRate(target_threshold: int):`

`network_hashrate = (1<<256)/(600*target_threshold)`

`return network_hashrate`

**Program 6.27:** Program to calculate network hashrate

Using hash rate of mining equipment, we can get number of blocks the miner mines in 10 minutes:

`def getBlockMiningRatePer10Min(hashrate: int, target_threshold: int):`

`network_hashrate = getNetworkHashRate(target_threshold)`

`block_mining_rate = hashrate/network_hashrate`

`return block_mining_rate`

**Program 6.28:** Program to calculate the number of blocks mined per 10 minutes

As we know the number of bitcoin created in each block, we can calculate bitcoin mined in 10 minutes:

`def getBitcoinMiningRate(hashrate: int, bits: bytes, blk_reward: int):`

`tgt_threshold = getTargetThreshold(bits)`

`block_mining_rate = getBlockMiningRatePer10Min(hashrate, tgt_threshold)`

`bitcoin_mining_rate = block_mining_rate * blk_reward`

`return bitcoin_mining_rate`

**Program 6.29:** Program to calculate bitcoin mined per 10 minutes by a mining equipment

This can be used to calculate bitcoin mined in a month:

`def getBitcoinMinedPerMonth(hashrate: int, bits: bytes, blk_reward: int):`

` btc_mined_per_month = getBitcoinMiningRate(hashrate, bits, blk_reward) * 6 * 24 * 30`

`return btc_mined_per_month`

**Program 6.30:** Program to calculate bitcoin mined per month using the mining equipment

Now, to calculate mining expense, we need to know miner’s power consumption in Watt:

`def getUnitFromPower(power: float):`

`unit = power * 24 * 30 / 1000`

`return unit`

`def getMiningPowerExpense(power: float):`

`unit = getUnitFromPower(power)`

`expense = getPriceFromUnit(unit)`

`return expense`

**Program 6.31:** Program to calculate expense electric power

Using the number of bitcoin mined in a month and mining expense, we can get the profit made by a miner in a month:

`def miningReturn(power: float, hashrate: int, bits: bytes, blk_reward: int):`

`expense = getMiningPowerExpense(power)`

`btc_mined_per_month = getBitcoinMinedPerMonth(hashrate, bits, blk_reward)`

`revenue = btc_mined_per_month * CURRENT_SELL_PRICE`

`profit = revenue - expense`

`return profit`

**Program 6.32:** Program to calculate monthly mining profit for a single miner

The following is the code to call the `miningReturn` method to get mining profit:

`def getBlockHeaderBytes(blk_hash: bytes):`

`jsonobj = getBlockIndex(blk_hash, block_db_g)`

`if ‘data_pos’ in jsonobj:`

`block_filepath = os.path.join(blocks_path_g, ‘blk%05d.dat’ % jsonobj[‘n_file’])`

`start = jsonobj[‘data_pos’]`

`elif ‘undo_pos’ in jsonobj:`

`block_filepath = os.path.join(blocks_path_g, ‘rev%05d.dat’ % jsonobj[‘n_file’])`

`start = jsonobj[‘undo_pos’]`

`# load file to memory`

`with open(block_filepath, ‘rb’) as blk_f:`

`blk_f.seek(start)`

`return blk_f.read(80)`

`if __name__ == ‘__main__’:`

`blk_hash = bytes.fromhex(‘000000000000000000079dc864537510659e14439ff5f4a208231bcf276358ba’)[::-1]`

`blk_index = getBlockIndex(blk_hash, block_db_g)`

`blk_hdr_b = getBlockHeaderBytes(blk_hash)`

`jsonobj = getBlockHeader(blk_hdr_b)`

`blk_reward = getBlockReward(blk_index[‘height’])`

`bits_b = bytes.fromhex(jsonobj[‘bits’])[::-1]`

`mining_return = miningReturn(MINER_POWER_WATT, MINER_HASH_RATE, bits_b, blk_reward)`

`print(“Mining Return Per Month = %s” % (mining_return))`

This gives us the following mining return per month:

![](images/Figure-6.40.jpg)

**Figure 6.40:** Shows current monthly mining profit calculated for mining in Bengaluru for the equipment

# [Mempool](#toc.xhtml#s125a)

The transactions broadcasted on the Bitcoin network are verified by each node and stored in memory in a data structure called mempool. To create a block, the miner selects transactions from mempool. The transaction count needs to remain within a limit such that block size does not cross the block size limit of 1MB. So, the miner selects the transactions from mempool that give them the greatest profit.

We need to use the following Bitcoin client APIs to access mempool data:

![](images/Figure-6.41.jpg)

**Figure 6.41:** Shows a portion of the list of mempool transactions

The following is the part of the output of API getrawmempool:

![](images/Figure-6.42.jpg)

**Figure 6.42:** Shows detailed information of a single mempool transaction

Here, we want to write a program that selects mempool transactions to maximize the fee reward for the miner. To achieve that, we need to select transactions that have the highest satoshi per byte fees because we have limited space of 1 MB, and if a transaction is taking more bytes, it needs to pay more to get accommodated in the limited block size. Sometimes, transaction inputs are themselves in mempool. We can’t have transactions added to a block that depends on bitcoin that are still in mempool. So, we need to ensure that if a transaction is added to blocks, then all its ancestors are also added to the block that is in mempool.

In the mempool json, `ancestorcount` includes current transactions, and so does `descendantcount`. Additionally, depends is the list of ancestors, and `spentby` is a list of descendants.

To write a program that selects transactions to maximize returns, we can use the following algorithm:

1.  Calculate satoshi/byte for all transactions in mempool by including the amount and bytes of its ancestors.
2.  Sort them in descending order of satoshi/byte.
3.  Exclude transactions if total size becomes more than 1MB, and exclude ancestors of transactions that are already included in 1MB.
4.  Add ancestor transactions to the list.

The following program lists the transaction hashes that provide the highest bitcoin per byte to the miner and whose combined size is less than 1MB:

1.  We need to import the following packages:
    
    `from bitcoinrpc.authproxy import AuthServiceProxy, JSONRPCException`
    
    `import json`
    
    `import pandas as pd`
    
    `from pandas import DataFrame`
    
    `import numpy as np`
    
    `import copy`
    
    `import hashlib`
    
2.  As a first step, we need to get all transactions from mempool and calculate Satoshi/byte:
    
    `def findAllDependentTx(mempool: dict, k: str):`
    
    `tx_l = [k]`
    
    `vsize = mempool[k][‘vsize’]`
    
    `fee = mempool[k][‘fees’][‘base’]`
    
    `if len(mempool[k][‘depends’]) == 0:`
    
    `return tx_l, vsize, fee`
    
    `for dependent in mempool[k][‘depends’]:`
    
    `dep_tx_l, dep_vsize, dep_fee = findAllDependentTx(mempool, dependent)`
    
    `tx_l.extend(dep_tx_l)`
    
    `vsize += dep_vsize`
    
    `fee += dep_fee`
    
    `return tx_l, vsize, fee`
    
    `def getMempoolTxList():`
    
    `mempool = rpc_connection.getrawmempool(True)`
    
    `tx_l = []`
    
    `for k, v in mempool.items():`
    
    `dep_l, vsize, fee = findAllDependentTx(mempool, k)`
    
    `dep_l.remove(k) # remove itself from list of dependents`
    
    `sats_per_byte = fee*10**8/vsize`
    
    `tx_l.append({‘txid’: k, ‘sats_per_byte’: sats_per_byte, ‘vsize’: vsize, ‘depends’: dep_l})`
    
    `return tx_l, mempool`
    
    **Program 6.33:** Program to transaction list with vsize and Satoshi/byte
    
3.  The following is the method sorting them in descending order of satoshi/byte:
    
    `def getSortedDF(tx_l: list):`
    
    ` df = pd.DataFrame(tx_l)`
    
    ` df = df.sort_values(by=[‘sats_per_byte’], ascending = False)`
    
    ` df = df.reset_index(drop=True)`
    
    `return df`
    
    **Program 6.34:** Program to sort transaction list based on Satoshi/byte
    
4.  Exclude transactions if the total size becomes more than 1MB, and exclude ancestors of transactions that are already included in 1MB. The following method does this:
    
    `def pruneDF(df):`
    
    `vsize = 0`
    
    `mb = 1 << 20`
    
    `inc_l = []`
    
    `for index, row in df.iterrows():`
    
    `if row[‘vsize’] + vsize > mb:`
    
    `df.drop(index, inplace=True)`
    
    `else:`
    
    `if row[‘txid’] in inc_l:`
    
    `df.drop(index, inplace=True)`
    
    `continue`
    
    `inc_l.extend(row[‘depends’])`
    
    `vsize += row[‘vsize’]`
    
    `return df, inc_l`
    
    **Program 6.35:** Program to remove transactions from a list based on Satoshi/byte and vsize
    
5.  The following program adds ancestor transactions to the list of transactions to be included:
    
    `def updateWithDepends(df, depend_l: list, mempool):`
    
    `tx_l = []`
    
    `for dep in depend_l:`
    
    `vsize = mempool[dep][‘vsize’]`
    
    `fee = mempool[dep][‘fees’][‘base’]`
    
    `sats_per_byte = fee*10**8/vsize`
    
    `tx_l.append({‘txid’: dep,`
    
    `‘sats_per_byte’: sats_per_byte,`
    
    `‘vsize’: vsize,`
    
    `‘depends’: []}) # ignore dependents`
    
    `df٢ = pd.DataFrame(tx_l)`
    
    `df.append(df2, ignore_index = True)`
    
    `return df`
    
    **Program 6.36:** Program to add dependent transactions to the list
    
6.  The following program is the main method that joins all the previous steps:
    
    `def getMempoolTx():`
    
    `tx_l, mempool = getMempoolTxList()`
    
    `df = getSortedDF(tx_l)`
    
    `df, depend_l = pruneDF(df)`
    
    `df = updateWithDepends(df, depend_l, mempool)`
    
    `final_tx_l = df[‘txid’].tolist()`
    
    `sum_vsize = 0`
    
    `for tx in final_tx_l:`
    
    `sum_vsize += mempool[tx][‘vsize’]`
    
    `print(‘sum_vsize = ‘, sum_vsize)`
    
    `print(‘tx count = ‘, len(final_tx_l))`
    
    `return(final_tx_l)`
    
    **Program 6.37:** Program to get final transaction list to be included in a new block
    

From the list of transaction hashes, we can get transaction content by using the following method:

`def getRawTransaction(txid: str):`

`rawtx = rpc_connection.getrawtransaction(txid)`

`return rawtx`

**Program 6.38:** Program to get raw transactions from transaction-id

Now, we can use the information to mine bitcoin. This has an infinitesimally low probability of success. We need to fill each field in the block header and then find nonce. So, let’s do this as follows:

1.  Version:
    
    `def getVersionBytes(supported_softfork_bits: int):`
    
    `version = 0x20000000 | supported_softfork_bits`
    
    `v_bytes = bytes.fromhex(hex(version))[::-1]`
    
    `return v_bytes`
    
    **Program 6.39:** Program to get version bytes using supported softfork bits
    
2.  Time:
    
    `def getTimeBytes():`
    
    `t = time.time()`
    
    `time_b = bytes.fromhex(hex(t))[::-1]`
    
    `return time_b`
    
    **Program 6.40:** Program to get time in bytes for block field
    
3.  Next is `bits`. `Bits` are updated only when block height is a multiple of 2016. To calculate `bits`, we need to calculate the target threshold. We take the block time of the last 2016 blocks and then adjust the target threshold. In the form of a mathematical equation:
    
    ![](images/c06eq-2.jpg)
    
    Using this equation in code:
    
    `def calculateNextTargetThreshold():`
    
    `block_hash = rpc_connection.getblockhash(height)`
    
    `block = rpc_connection.getblock(block_hash, 0)`
    
    `blkhdr = getBlockHeader(bytes.fromhex(block))`
    
    `bits = bytes.fromhex(blkhdr[‘bits’])[::-1]`
    
    `tt_old = getTargetThreshold(bits)`
    
    `block_hash_٢٠١٥ = rpc_connection.getblockhash(height-2015)`
    
    `block_٢٠١٥ = rpc_connection.getblock(block_hash_2015, 0)`
    
    `blkhdr_٢٠١٥ = getBlockHeader(bytes.fromhex(block_2015))`
    
    `delta_t = blkhdr[‘time’] - blkhdr_2015[‘time’]`
    
    `tt_new = tt_old * (blkhdr[‘time’] - blkhdr_2015[‘time’])//(2016 * 600)`
    
    `return tt_new`
    
    **Program 6.41:** Program to calculate next target threshold
    
4.  To convert the target threshold to bits, we need to use the following compression logic:
    
    1.  Convert Target Threshold to bytes, which is a base 256 number.
    2.  If the most significant bit is greater than 0x7F, then prepend the bytes with b’\\x00’.
    3.  The first byte is the length of the bytes.
    4.  The next 3 bytes are the three most significant numbers in the base 256 number.
    
    ![](images/Figure-6.43.jpg)
    
    **Figure 6.43:** Illustration of conversion of target threshold to bits
    
    `def targetThreshold2bits(tt: int):`
    
    `tt_b = tt.to_bytes((tt.bit_length() + 7) // 8, ‘big’)`
    
    `print(tt_b.hex())`
    
    `prepend = b”0” if tt_b[0] > 0x7f else b””`
    
    `tt_b = prepend + tt_b`
    
    `b١ = bytes([len(tt_b)])`
    
    `tt_b = tt_b + bytes(2)`
    
    `tt_b = tt_b[0:3]`
    
    `bits = b١ + tt_b`
    
    `return bits`
    
    **Program 6.42:** Program to convert target threshold to bits
    

Bits are only updated when block height is in multiples of 2016. The following code returns bits based on block height:

`def getBits():`

`if height % 2016 != 0:`

`block_hash = rpc_connection.getblockhash(height)`

`blkhdr = getBlockHeader(bytes.fromhex(block))`

`return bytes.fromhex(blkhdr[‘bits’])[::-1]`

`tt = calculateNextTargetThreshold()`

`bits = targetThreshold٢bits(tt)`

`return bits`

**Program 6.43:** Program to return bits if next block height in multiples of 2016

Now, we can use the above-mentioned header elements to find nonce and build blocks. We also need to update transactions and Merkle root. We can calculate the Merkle root of the new block by using the transaction list we already got in *program 6.37*. We will leave this for you to implement the final mining code.

This brings us to the end of this chapter.

# [Conclusion](#toc.xhtml#s126a)

In this chapter, we started with setting up Bitcoin software and syncing of blockchain. You learned to use the Bitcoin Core CLI and Python RPC client. You also investigated the structure of blocks and indexes. You learned how to query data from indexes. We wrote short programs to understand the structure of block files, and you also learned about content in mempool, its role, and how it is used to mine blocks.

Bitcoin is transformational as it eliminates the need for intermediaries in any transaction. Consequently, we have a cryptocurrency that behaves like cash. This was the goal that many cryptographic experts aimed at for decades. Most of us know this is deterrence. It feels like we are into rocket science. But as we saw in this chapter, the thinking is just a deterrence. The Bitcoin protocol is amazingly simple. This chapter is the first chapter that dives into programming. We only used Bitcoin software client, block files, indexes, and a bit of basic knowledge of protocol to enhance your understanding of the existing implementation of the Bitcoin protocol. We have left certain important topics, such as transaction scripting and segregated witness, for the upcoming chapters.

Knowing that such an impactful technology can be learned with ease allows us to build confidence in our ability. It allows us to trust ourselves to understand things. It removes the need for experts and allows us to find an expert within ourselves. It changes the way we look at the world at a fundamental level.

In the next chapter, you will understand the Bitcoin protocol messaging. You will understand how Bitcoin nodes find other nodes, connect with them, synchronize their blockchain, and broadcast blocks and transactions.

# [Points to remember](#toc.xhtml#s127a)

*   Bitcoin Core is the most popular Bitcoin software maintained by the Bitcoin Core team, and it was originally created by Satoshi Nakamoto.
*   Blocks are mined every 10 minutes on average.
*   Every block in the Bitcoin blockchain contains hashed block header of the previous block. This makes the blockchain more like a stack.
*   Block header contains Merkle Root Hash, which, along with proof-of-work algorithm, secures the integrity of transactions included in the block.
*   Proof-of-work also protects the integrity of other block header fields, such as time, version, previous block hash, and target threshold.
*   Block version indicates miner support and readiness of a protocol enhancement, also called a softfork. Such types of softforks are also called Miner Initiated Softforks.
*   If an enhancement is important for the future of Bitcoin, the Bitcoin developer community can initiate BIP 148 and enforce miners to move to the softfork.
*   Hash of Block header should be less than target threshold calculated from bits field in the block header.
*   Target Threshold is adjusted only at every 2016^(th) block in the blockchain.
*   The new target threshold is calculated by modifying the existing target threshold by taking block time of previous 2016 blocks such that the next 2016 blocks are mined on an average of 10 minutes.
*   Blocks are stored in block files, and the information related to block files and blocks are stored in the block index.
*   Chainstate database stores unspent transaction outputs (UTXOs).
*   Block indexes and UTXO indexes both help in the quick verification of blocks.
*   There is another index called transaction index or txindex, which is not used by the Bitcoin software. It is optional and stores indexes related to transactions stored in blocks.
*   Mining is the process of finding nonce so that the newly created block header hash is less than the target threshold.
*   Bitcoin mining is a costly process, and like in commodity mining where miners need to invest in exploration, in Bitcoin mining, miners need to continuously invest in equipment to remain viable.
*   Solo mining is only for developers who are learning Bitcoin or who want to reduce mining centralization by adding their hashrate to the overall network hashrate.
*   For-profit mining can only be done in a pool. Miners would join one of the few famous pools.
*   Mining pools use a combined hashrate of miners to find nonce. Once the nonce is found, the pool pays miners according to their hashrate contribution.

# [Questions](#toc.xhtml#s128a)

1.  Calculate the current bitcoin supply. Additionally, calculate the current bitcoin supply as the percentage of maximum supply.
2.  Find the expected year, month, and date of the next Bitcoin halving (when block reward becomes half of the current reward).
3.  Create a table of Bitcoin mining equipment, their cost, and the profixt per month.
4.  Create a table of the average annual transaction count per block.
5.  Complete the solo mining program that has been left incomplete.
6.  True/False: 
    1.  Softforks are enhancements that are not backward compatible, which is why miners need to vote for its support.
    2.  Network hashrate can only go up in the long run even if the bitcoin price continues to fall.
    3.  Mempool stores unconfirmed transactions in memory.
7.  Fill in the blanks: 
    1.  After \_\_\_\_\_\_\_ blocks, a miner can use bitcoin locked in coinbase transaction.
    2.  Compressed form of transaction count 2,597 is \_\_\_\_\_\_\_\_\_\_.
    3.  Compressed form of 0.25 BTC is \_\_\_\_\_\_\_.
    4.  Bits value 0x1715a35c means target threshold of \_\_\_\_\_\_\_\_\_\_\_\_\_\_.
    5.  Block size limit is \_\_\_\_\_\_\_\_\_\_\_\_ MB.

# [CHAPTER 7](#toc.xhtml#c07)

# [Node Communication](#toc.xhtml#c07)

In the previous chapter, you learned about the structure of data stored at the nodes and their method of verification, creation, and versioning. In this chapter, we are investigating communication between nodes.

The Bitcoin network is a peer-to-peer network where there is no master or server and no slave or client. To establish communication, a TCP connection is established, which is based on the server-client model. Once a connection is established, there is no difference for a node if it initiated a connection or accepted a connection request. Once the TCP connection is established, the Bitcoin network connection needs to be established. The Bitcoin network is a very democratic network, and nodes can choose their peers. The decision depends on the version or services the peer is going to offer. Once both sides agree, the connection is established, and they can then exchange information.

There are nearly 10,000 known active nodes at almost any time, which is enough to allow most nodes to find and choose multiple suitable peers.

Being an open peer-to-peer network, each node relies on its peers to get information about other available peers so that it can connect with them too. It also needs to broadcast transactions and blocks and help propagate them across the network. Additionally, it needs to keep itself in sync with the network, which translates to having the blockchain updated with the latest blocks and mempool with the latest transactions. And it needs to verify transactions and blocks and help SPVs verify transactions.

In this chapter, you will understand the Bitcoin network topology, network nodes, and detailed information about how these nodes communicate with each other.

# [Structure](#toc.xhtml#s129a)

The following topics will be covered in this chapter:

*   Bitcoin network topology
*   Node bootstrapping
*   Network messaging 
    *   Message format
    *   Establishing connection
    *   Disconnecting with inactive peer
    *   Node discovery
    *   Receiving full blockchain
    *   Synchronizing blockchain
    *   Transaction broadcasting
    *   Block broadcasting 
        *   Unsolicited Block Push
        *   Direct Headers Announcements
        *   Compact Block Announcements
            
            ![](images/ent.jpg)High Bandwidth Compact Block Announcements
            
            ![](images/ent.jpg)Low Bandwidth Compact Block Announcements
            

# [Objectives](#toc.xhtml#s130a)

The objective of this chapter is to help you learn about the Bitcoin network, which includes network topology and node communication as well as the progression of protocol messages.

In this chapter, you will learn about the different types of nodes and their role in the Bitcoin network. You will learn about the mechanism by which each node discovers other nodes. You will also understand how to create and establish a connection with other nodes and exchange protocol messages. Plus, you will understand the different types of payload that protocol messages carry, their purpose, and the expected sequence of message types. Further on in the chapter, we will discuss node versions and their role in establishing connection and communication with peers, and you will understand connection termination.

# [Bitcoin network topology](#toc.xhtml#s131a)

The Bitcoin network allows nodes running different versions of code to communicate and find peers who are fine with their version and the services they offer or request. For instance, a node may be an SPV and may need to communicate with only full nodes. A full node may not be interested in connection with SPV and so, may be disconnected. The following figure shows how the nodes are distributed. We can see that most nodes are in the US and Germany.

![](images/Figure-7.1.jpg)

**Figure 7.1:** Illustration of global node distribution

A Bitcoin node establishes a connection with its peer using a TCP handshake. It can have IPv4 or IPv6 IP Addresses. A node can even connect with its peer on the Tor network, which is an anonymous network and protects the node against surveillance and tracking. If we are running Tor in our system at port 9050, then our node can connect or accept connection using the Tor network with the following command-line option:

`-proxy=127.0.0.1:9050`

The following chart shows the distribution of Bitcoin network connections based on the connection type and the address type:

![](images/Figure-7.2.jpg)

**Figure 7.2:** Chart showing the distribution of nodes based on connection type and address type

We have different kind of nodes in the network, some of which are as follows:

*   A Full node with complete blockchain, which is also called archival node.
*   A Full node verifies all the blocks but does not maintain the full blockchain. It is still full node because, by definition, full node verifies the full blockchain, which this node does. These are also called pruned nodes.
*   A SPV node maintains a chain of block headers with only the required transactions. It needs to talk to full nodes, which can help it verify blocks, but since it does not verify blocks themselves, they also do not relay transactions.
*   A Full node that does not communicate with SPV nodes.
*   A Full node that only accepts blocks and not transactions.

So, there are quite a few variations among nodes. In addition, they can have different versions of software running. There could be an attacker node or group of attacker nodes that network or targeted nodes need to identify and blacklist.

# [Node bootstrapping](#toc.xhtml#s132a)

As you have learned, Bitcoin doesn’t have a centralized server, so finding a node to connect is a challenge. To solve this problem, Bitcoin Core has hard-coded DNS Seeder addresses. These are called seed servers. These servers provide a list of addresses that may or may not be active. We need to iteratively find active address that we can connect with. The seed servers may get updated in the future.

Here are the hardcoded DNS seeds:

![](images/187.jpg)

**Table 7.1:** List of hardcoded DNS seeds

We are going to use following package to get the addresses from DNS seed node:

![](images/Figure-7.3.jpg)

**Figure 7.3:** Python package to communicate with DNS servers

The following program generates addresses from DNS seeds:

`import dns.name`

`import dns.message`

`import dns.query`

`import dns.flags`

`import ipaddress`

`def getNodeAddresses(dnsseed: str):`

`dest = ‘8.8.8.8’`

`rdclass = 65535`

`domain = dns.name.from_text(dnsseed)`

`if not domain.is_absolute():`

`domain = domain.concatenate(dns.name.root)`

`request = dns.message.make_query(`

`domain,`

`dns.rdatatype.A,`

`dns.rdataclass.IN)`

`request.flags |= dns.flags.RD|dns.flags.RA|dns.flags.AD`

`request.find_rrset(request.additional, dns.name.root, rdclass, dns.rdatatype.OPT, create=True, force_unique=True)`

`responseudp = dns.query.udp(request, dest)`

`rrset = responseudp.answer`

`rrset_l = []`

`for rrset_val in rrset:`

`rrset_l.extend(str(rrset_val).split(“\n”))`

`ipaddr_l = []`

`for rrset_s in rrset_l:`

`ipaddr_l.append(rrset_s.split(“ “)[4])`

`return ipaddr_l`

`def getTestnetPeers():`

`port = 18333`

`dns_seeds = [`

`“testnet-seed.bitcoin.jonasschnelli.ch”,`

`“seed.tbtc.petertodd.org”,`

`“seed.testnet.bitcoin.sprovoost.nl”,`

`“testnet-seed.bluematt.me”`

`]`

`ipaddr_l = []`

`for seed in dns_seeds:`

xwi

`ipaddr_l.extend(getNodeAddresses(seed))`

`peers = []`

`for ipaddr in ipaddr_l:`

`peers.append((ipaddr, port))`

`return peers`

**Program 7.1:** Program to get list of addresses from DNS seed

We call the preceding method as follows to get the list of the first five address and port numbers:

`if __name__ == ‘__main__’:`

`peers = getTestnetPeers()`

`for index in range(5):`

`print(peers[index])`

This gives us the following first five IP addresses and port numbers:

![](images/Figure-7.4.jpg)

**Figure 7.4:** List of a few IP addresses and port numbers generated using DNS seed

There are also hardcoded IP Addresses in the Bitcoin Core source, which are used only as the last resort if the govt. blocks the connection to the known DNS seeds. These addresses are in the following file:

`chainparamsseeds.h`

Bitcoin Core also maintains the `peers.dat` file, which maintains active addresses that it is connected to and since when. This helps in reconnecting to nodes after the connection is broken. Bitcoin Core daemon also has an `addnode` command option to specify a peer for connecting. This peer is treated at par with other peers.

This information is specific to Bitcoin Core. In addition to utilizing the Bitcoin node bootstrapping method, we can connect to addresses available from other websites, such as **[https://bitnodes.io/api/v1/snapshots/latest](https://bitnodes.io/api/v1/snapshots/latest)**.

The following code gets lists of nodes from this URL:

`import requests`

`import socket`

`from urllib.parse import urlparse`

`def isValidIPv6Addr(addr: str):`

`try:`

`socket.inet_pton(socket.AF_INET6, addr)`

`except socket.error:`

` return False`

`return True`

`def parseNodeInfo(ip_port: str, nodeinfo: dict):`

`node = {}`

`node[‘selected’] = False`

`node[‘port’] = int(ip_port.split(‘:’)[-1])`

`val = ip_port.rsplit(‘:’, 1)[0]`

`parsed = urlparse(‘//{}’.format(val))`

`addr = parsed.hostname`

`if isValidIPv6Addr(addr) == False:`

`return node`

`node[‘selected’] = True`

`node[‘ipaddr’] = addr`

`node[‘type’] = nodeinfo[11]`

`node[‘time’] = nodeinfo[2]`

`return node`

`def getMainnetPeers():`

`url = ‘https://bitnodes.io/api/v1/snapshots/latest/’`

`headers = {‘Accept’: ‘application/json’}`

`r = requests.get(url=url, headers=headers)`

`jsonobj = r.json()`

`peers = []`

`for k, v in jsonobj[‘nodes’].items():`

`node = parseNodeInfo(k, v)`

`if node[‘selected’] == True:`

`peers.append(node)`

`return peers`

**Program 7.2:** Program to get the list of nodes using an external URL

We call the above-mentioned methods to get peers as follows:

`if __name__ == ‘__main__’:`

`peers = getMainnetPeers()`

`for peer in peers:`

`print(‘%s\t\t\t%d’ % (peer[‘ipaddr’], peer[‘port’]))`

This gives us the following first five peers:

![](images/Figure-7.5.jpg)

**Figure 7.5:** List of IP addresses and port numbers of peers obtained from an external website

# [Network messaging](#toc.xhtml#s133a)

Bitcoin network nodes communicate with each other for various reasons, like to learn about some other peers, to be sure that the connection is still active, to help other nodes to sync with itself, or ask for missing blocks, or to broadcast any new received block or transaction. In this topic, you will learn in detail about the messaging and its format, and program it by writing a client.

# [Message format](#toc.xhtml#s134a)

Messages exchanged over the network have headers and payload, and the payload is dependent on the command.

Here’s the message format:

![](images/Figure-7.6.jpg)

**Figure 7.6:** Illustration of protocol message format

*The following is the explanation of each field of the message format:*

*   **Magic** is the same as we learned in the block structure in ***[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml)*** and we can look at its values in [table 6.3](#c06.xhtml#tab6_3).
*   **Command** is the command sent in ASCII padded with all zeroes i.e. b’\\0’.
*   **Length** is the length of the payload.
*   **Checksum** is the checksum of the payload.
*   **Payload** is the parameters of the command sent.

The following is the method that creates this message:

`def createMessage(command, payload):`

`magic = 0x0709110B`

`checksum = hashlib.sha256(hashlib.sha256(payload).digest()).digest()[0:4]`

`magic_b = struct.pack(‘<L’, magic)`

`cmd_b = struct.pack(‘<12s’, command.encode(‘ascii’))`

`payload_len_b = struct.pack(‘<L’, len(payload))`

`checksum_b = struct.pack(‘<4s’, checksum)`

`msg = magic_b + cmd_b + payload_len_b + checksum + payload`

`return msg`

**Program 7.3:** A method for creating protocol message

# [Establishing connection](#toc.xhtml#s135a)

Bitcoin establishes a connection by first exchanging versions and then acknowledging their acceptance. Before acknowledging the version, a node needs to send its own version. So, the network handshake looks as follows:

![](images/Figure-7.7.jpg)

**Figure 7.7:** An illustration of the sequence of message transfers to establish Bitcoin connection

The f*ollowing is the* `version` *message payload* structure:

![](images/Figure-7.8.jpg)

**Figure 7.8:** Version message payload structure

*The following is the explanation of each field of the `version` message:*

*   `Version` is the Protocol version running on a host.
*   **Service** is the service supported by the sending node. Here’s the list of service codes:

 
| **Byte Code** || **Service Offered** || **Description** |
| --- | --- | --- |
| 1 || NODE\_NETWORK || Full Node |
| 2 || NODE\_GETUTXO || BIP 0064: Supports getutxos and utxos |
| 4 || NODE\_BLOOM || BIP 0111: Supports Bloom filters |
| 8 || NODE\_WITNESS || BIP 0144: Supports Segregated Witness |
| 1024 || NODE\_NETWORK\_LIMITED || BIP 0159: Pruned node |

**Table 7.2:** List of service codes required by Version message

*   **Timestamp** is the Unix epoch time of the payload.
*   **Addr Recv** is the address of the connection receiving node. So, the node sending the `version` payload will have the address and port of the peer it is connecting to. The Services field is normally set to zeroes.
*   **Addr from** is the address of the connection originating node. So, the node sending the `version` payload will have its own address and port. It also includes services offered by the sender.
*   **Nonce** is a random number that is useful in identifying whether we are not connected to ourselves.
*   **User Agent** is used to identify the software running at the node. It is defined in BIP-0014.
*   **Start Height** is the current block height at the node blockchain.
*   **Relay** is an optional Boolean value that is set by SPV to false to indicate that the node will not participate in relaying a message. This means it does not want peers to advertise `inv` messages with MSG_BLOCK. This protects the node from getting flooded by `inv` messages. This is defined in BIP 0037.

The following is the distribution of version of nodes at the time of writing:

![](images/Figure-7.9.jpg)

**Figure 7.9:** Chart showing the distribution of the version of nodes on the Bitcoin network

The following is the distribution of User Agents in the Bitcoin network:

![](images/Figure-7.10.jpg)

**Figure 7.10:** Bar chart showing the distribution of user agents in the Bitcoin network

The following is the program that creates `version` payload:

`from bitcoinrpc.authproxy import AuthServiceProxy, JSONRPCException`

`import struct`

`import random`

`rpc_connection = AuthServiceProxy(“http://%s:%s@127.0.0.1:18332”%(‘test’, ‘test’))`

`def setVarInt(n: int):`

`if n < 0xfd:`

`n_h = ‘%02x’ % n`

`elif n > 0xfd and n < 0xffff:`

`n_h = ‘fd%04x’ % n`

`elif n > 0xffff and n < 0xFFFFFFFF:`

`n_h = ‘fe%08x’ % n`

`else:`

`n_h = ‘ff%016x’ % n`

`return bytes.fromhex(n_h)`

`def getLastBlockHeight():`

`height = rpc_connection.getblockcount()`

`return height`

`def createUserAgent():`

`sub_version = “/MyTestAgent:0.0.1/”`

`sub_version_b = sub_version.encode()`

`len_b = setVarInt(len(sub_version_b))`

`return len_b + sub_version_b`

`def createRecvIPAddress(ip, port):`

`service_b = struct.pack(‘<Q’, 1)`

`ip_b = socket.inet_aton(ip)`

`ipv4_to_ipv6 = bytearray.fromhex(“00000000000000000000ffff”) + ip_b`

`ipv6addr_b = struct.pack(‘>16s’, ipv4_to_ipv6)`

`port_b = struct.pack(‘>H’, port)`

`addr_b = service_b + ipv6addr_b + port_b`

`return(addr_b)`

`def createTransIPAddress():`

`service_b = struct.pack(‘<Q’, 1)`

`ip_b = socket.inet_aton(“0.0.0.0”)`

`ipv4_to_ipv6 = bytearray.fromhex(“000000000000000000000000”) + ip_b`

`ipv6addr_b = struct.pack(‘>16s’, ipv4_to_ipv6)`

`port_b = struct.pack(‘>H’, 0)`

`addr_b = service_b + ipv6addr_b + port_b`

`return(addr_b)`

`def createVersionPayload(s: socket, version: int):`

`version_b = struct.pack(‘<L’, version)`

`services_b = struct.pack(‘<Q’, 1)`

`timestamp_b = struct.pack(‘<Q’, int(time.time()))`

`myip, myport = s.getsockname()`

`addr_recv_b = struct.pack(‘<26s’, createRecvIPAddress(myip, myport))`

`addr_trans_b = struct.pack(‘<26s’, createTransIPAddress())`

`nonce_b = struct.pack(‘<Q’, random.getrandbits(64))`

`user_agent = createUserAgent()`

`user_agent_b = struct.pack(‘<%ds’ % len(user_agent), user_agent)`

`start_height_b = struct.pack(‘<L’, getLastBlockHeight())`

`payload = version_b \`

`+ services_b \`

`+ timestamp_b \`

`+ addr_recv_b \`

`+ addr_trans_b \`

`+ nonce_b \`

`+ user_agent_b \`

`+ start_height_b`

`return payload`

**Program 7.4:** Program for creating Version message payload

To create the message payload, we use the Python struct pack. The following are the symbols and their meanings:

 
| **Symbols** || **Represents** |
| --- | --- |
| < || Little Endian |
| \> || Big Endian |
| B || 1-byte Unsigned Integer |
| H || 2-byte Unsigned Integer |
| L || 4-byte Unsigned Integer |
| Q || 8-byte Unsigned Integer |
| xs || Byte array of size x |

**Table 7.3:** List of Python struct pack symbols and their meanings

You can check out the Python docs for more details:

**[https://docs.python.org/3.8/library/struct.html](https://docs.python.org/3.8/library/struct.html)**

IP address and port are in big endian, while the rest of the message is in the little-endian format. When we pack an ASCII string, it converts it into a byte array and pads it with zeroes.

We call the preceding methods as follows:

`if __name__ == ‘__main__’:`

`peers = getTestnetPeers()`

`p = random.choice(peers)`

`s = None`

`peerinfo = {}`

`print(“Trying to connect to “, p)`

`s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)`

`err = s.connect(p)`

`print(‘TCP Connection Established’)`

`payload = createVersionPayload(s, 70015)`

`print(‘Version payload: ‘, payload.hex())`

`s.close()`

This creates the following payload in hex string:

![](images/Figure-7.11.jpg)

**Figure 7.11:** Shows version payload created by the CreateVersionPayload program

When we receive the `version` message, we do the following:

1.  We first receive the message header, verify the magic number and checksum, and identify the command:
    
    `flog = open(‘communication.log’, ‘wt+’)`
    
    `def calculateChecksum(b: bytes):`
    
    `checksum = hashlib.sha256(hashlib.sha256(b).digest()).digest()[0:4]`
    
    `return checksum`
    
    `def checkMessage(msghdr: dict, payload_b: bytes):`
    
    `if msghdr[‘magic’] == ‘0709110b’:`
    
    `print(‘Magic check passed’, file=flog)`
    
    `else:`
    
    `print(‘Magic check failed’, file=flog)`
    
    `print(‘magic = %s’ % msghdr[‘magic’], file=flog)`
    
    `raise Exception(‘Invalid Magic’, file=flog)`
    
    `checksum_calc = calculateChecksum(payload_b)`
    
    `if msghdr[‘checksum’] == checksum_calc:`
    
    `print(‘checksum check passed’, file=flog)`
    
    `else:`
    
    `print(‘checksum check failed’, file=flog)`
    
    `print(‘payload = %s’ % payload_b.hex(), file=flog)`
    
    `print(‘expected checksum = %s’ % msghdr[‘checksum’].hex(), file=flog)`
    
    `print(‘received checksum = %s’ % checksum_calc.hex(), file=flog)`
    
    `raise Exception(‘Invalid Checksum’)`
    
    `def parseMsgHdr(msghdr_b: bytes):`
    
    `msghdr = {}`
    
    `msghdr[‘magic’] = msghdr_b[0:4][::-1].hex()`
    
    `msghdr[‘command’] = msghdr_b[4:16].decode(“ascii”).strip(‘\0’)`
    
    `msghdr[‘length’] = int.from_bytes(msghdr_b[16:20], byteorder=’little’)`
    
    `msghdr[‘checksum’] = msghdr_b[20:24]`
    
    `return msghdr`
    
    **Program 7.5:** Program for parsing message header
    
    We can see that the program checksum only contains the first 4 bytes of the double SHA256 hash; to get the command, we strip it.
    
2.  Next, we receive a message again from the socket and call the parser of the `version` payload. To do this, we call the method by name. We will create dummy methods for the ones not required by the subsequent programs:
    
    `MSGHDR_SIZE = 24`
    
    `CMD_FN_MAP = {`
    
    `‘version’: parseVersionPayload,`
    
    `‘addr’: parseAddrPayload,`
    
    `‘filterload’: parseFilterLoadPayload,`
    
    `‘filteradd’: parseFilterAddPayload,`
    
    `‘merkleblock’: parseMerkleBlockPayload,`
    
    `‘ping’: parsePingPongPayload,`
    
    `‘pong’: parsePingPongPayload,`
    
    `‘feefilter’: parseFeeFilterPayload,`
    
    `‘inv’: parseInvPayload,`
    
    `‘getdata’: parseInvPayload,`
    
    `‘notfound’: parseInvPayload,`
    
    `‘tx’: parseTxPayload,`
    
    `‘block’: parseBlockPayload,`
    
    `‘getblocks’: parseGetBlocksGetHeadersPayload,`
    
    `‘getheaders’: parseGetBlocksGetHeadersPayload,`
    
    `‘headers’: parseHeadersPayload,`
    
    `‘reject’: parseRejectPayload,`
    
    `‘sendcmpct’: parseSendCompactPayload,`
    
    `‘cmpctblock’: parseCompactBlockPayload,`
    
    `‘getblocktxn’: parseGetBlockTxnPayload,`
    
    `‘blocktxn’: parseBlockTxnPayload`
    
    `}`
    
    `def recvAll(s: socket, payloadlen: int):`
    
    `payload_b = b’’`
    
    `length = payloadlen`
    
    `while True:`
    
    `recvd_b = s.recv(length)`
    
    `payload_b += recvd_b`
    
    `if len(payload_b) == payloadlen:`
    
    `break`
    
    `length = payloadlen - len(payload_b)`
    
    `return payload_b`
    
    `def recvMsg(s: socket):`
    
    `msghdr_b = s.recv(MSGHDR_SIZE)`
    
    `msg = parseMsgHdr(msghdr_b)`
    
    `payloadlen = msg[‘length’]`
    
    `payload_b = recvAll(s, payloadlen)`
    
    `checkMessage(msg, payload_b)`
    
    `payload_m = mmap.mmap(-1, payloadlen + 1)`
    
    `payload_m.write(payload_b)`
    
    `payload_m.seek(0)`
    
    `msg[‘payload’] = {}`
    
    `if payloadlen > 0:`
    
    `msg[‘payload’] = CMD_FN_MAP[msg[‘command’]](payload_m, payloadlen)`
    
    `print(‘<== msg = %s’ % msg, file=flog)`
    
    `return msg`
    
    **Program 7.6:** Program to receive and process messages based on command
    
3.  The following code parses the `version` payload:
    
    `import ipaddress`
    
    `import datetime`
    
    `def parseIPAddress(ip_m: mmap):`
    
    `addr = {}`
    
    `addr[‘service’] = int.from_bytes(ip_m.read(8), byteorder=’little’)`
    
    `parseServices(addr[‘service’])`
    
    `ip = ip_m.read(16)`
    
    `if ip[0:12].hex() == “00000000000000000000ffff”:`
    
    `addr[‘version’] = ‘IPv4’`
    
    `addr[‘address’] = str(ipaddress.IPv4Address(ip[12:16]))`
    
    `else:`
    
    `addr[‘version’] = ‘IPv6’`
    
    `addr[‘address’] = str(ipaddress.IPv6Address(ip[0:16]))`
    
    `addr[‘port’] = int.from_bytes(ip_m.read(2), byteorder=’big’)`
    
    `return addr`
    
    `def parseServices(services: int):`
    
    `service_l = []`
    
    `if services == 0x00:`
    
    `service_l.append(‘Unnamed’)`
    
    `if services & 0x01 == 0x01:`
    
    `service_l.append(‘NODE_NETWORK’)`
    
    `if services & 0x02:`
    
    `service_l.append(‘NODE_GETUTXO’)`
    
    `if services & 0x04:`
    
    `service_l.append(‘NODE_BLOOM’)`
    
    `if services & 0x08:`
    
    `service_l.append(‘NODE_WITNESS’)`
    
    `if services & 1024:`
    
    `service_l.append(‘NODE_NETWORK_LIMITED’)`
    
    `print(‘Services: %d implies: %s’ % (services, service_l), file=flog)`
    
    `def parseVersionPayload(payload_m: mmap, payloadlen: int):`
    
    `payload = {}`
    
    `start = payload_m.tell()`
    
    `payload[‘version’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`
    
    `payload[‘services’] = int.from_bytes(payload_m.read(8), byteorder=’little’)`
    
    `parseServices(payload[‘services’])`
    
    `payload[‘timestamp’] = int.from_bytes(payload_m.read(8), byteorder=’little’)`
    
    `payload[‘dt’] = datetime.datetime.fromtimestamp(payload[‘timestamp’]).strftime(‘%Y-%m-%d %H:%M:%S’)`
    
    `payload[‘addr_recv’] = parseIPAddress(payload_m)`
    
    `payload[‘addr_trans’] = parseIPAddress(payload_m)`
    
    `payload[‘nonce’] = int.from_bytes(payload_m.read(8), byteorder=’little’)`
    
    `payload[‘user_agent_size’] = getVarInt(payload_m)`
    
    `payload[‘user_agent’] = payload_m.read(payload[‘user_agent_size’])`
    
    `payload[‘block_height’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`
    
    `if payload_m.tell() - start != payloadlen:`
    
    `payload[‘relay’] = int.from_bytes(payload_m.read(1), byteorder=’little’)`
    
    `return payload`
    
    **Program 7.7:** Program to parse version payload
    

Bitcoin network messaging uses the same variable integer format as we had discussed in *[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml), [figure 6.25](#c06.xhtml#fig6_25)*.

The `verack` message has no payload. It is an acknowledgment of the `version` received.

Once the `version` message is sent and received and `verack` message is sent and received, we consider the connection to have been established and are ready to send and receive other types of messages.

The following is the code for establishing a Bitcoin connection:

`def sendVersionMessage(s: socket, version: int):`

`sndcmd = ‘version’`

`payload = createVersionPayload(s, version)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`return True`

`def waitForVersion(s: socket):`

`recvmsg = recvMsg(s)`

`vers_recvd = False`

`if recvmsg[‘command’] != ‘version’:`

`print(‘Invalid Response’)`

`return False`

`services = recvmsg[‘payload’][‘services’]`

`if services & 1 == 0x00:`

`print(‘Peer is not full node’)`

`return False`

`return True`

`def sendVerackMessage(s: socket):`

`sndcmd = ‘verack’`

`payload = b’’`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`return True`

`def waitForVerack(s: socket):`

`recvmsg = recvMsg(s)`

`verack_recvd = False`

`if recvmsg[‘command’] != ‘verack’:`

`return False`

`return True`

`def establishConnection(s: socket, version: int):`

`vers_sent = sendVersionMessage(s, version)`

`vers_recvd = waitForVersion(s)`

`if vers_recvd == False:`

`return False`

`verack_sent = sendVerackMessage(s)`

`verack_recvd = waitForVerack(s)`

`if vers_sent and vers_recvd and verack_sent and verack_recvd:`

`print(‘Connection is established’, file=flog)`

`return True`

`return False`

**Program 7.8:** Program to establish Bitcoin connection

We call the preceding method using the following program:

`if __name__ == ‘__main__’:`

`peers = getTestnetPeers()`

`p = random.choice(peers)`

`s = None`

`peerinfo = {}`

`print(“Trying to connect to “, p, file=flog)`

`s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)`

`err = s.connect(p)`

`print(‘connected’, file=flog)`

`if establishConnection(s, 70015) == False:`

`print(‘Establish connection failed’, file=flog)`

`s.close()`

`flog.close()`

We get the following communication log:

![](images/Figure-7.12.jpg)

**Figure 7.12:** Communication log of message exchange during Bitcoin connection establishment

In this subtopic, you learned to establish a Bitcoin connection.

# [Disconnecting with inactive peer](#toc.xhtml#s136a)

TCP/IP connection can become inactive without the knowledge of a peer. To disconnect an inactive connection, the node sends `ping` and expects `pong` as a response. The `ping` message contains an 8-byte nonce, which is a random number. In the response `pong` message, the receiving node sends back the same nonce message that it had received as part of the `ping` message.

The following method parses the `ping` message and respond with the `pong` message:

`def parsePingPongPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`payload[‘nonce’] = int.from_bytes(payload_m.read(8), byteorder=’little’)`

`return payload`

`def createPongPayload(nonce: int):`

`nonce_b = struct.pack(‘<Q’, nonce)`

`return nonce_b`

`def sendPongMessage(s: socket, recvmsg: dict):`

`# send pong message`

`sndcmd = ‘pong’`

`nonce = recvmsg[‘payload’][‘nonce’]`

`payload = createPongPayload(nonce)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

**Program 7.9:** Program for sending ping and receiving pong messages

If the peer responds with a different nonce or does not respond, then we can safely assume that it is not active, and we can disconnect the connection.

# [Node discovery](#toc.xhtml#s137a)

As you have learned, there are almost 10,000 active nodes on average, it is important to distribute load across the network. Almost 95% of the full nodes run Bitcoin Core, which has some hardcoded DNS seeds, so if these nodes only depend on addresses from the DNS seeds, then those addresses can get overloaded. This will hamper the decentralized nature of the Bitcoin network, will affect performance, and will be prone to **Denial-of-Service** (**DoS**) *attacks*.

To find new peers, we have the following sequence diagram:

![](images/Figure-7.13.jpg)

**Figure 7.13:** Sequence diagram showing the steps to receive addresses of nodes from peer

As in `verack`, `getaddr` doesn’t have a payload. Here’s the payload structure of the `addr` message:

![](images/Figure-7.14.jpg)

**Figure 7.14:** Payload structure of addr

Now, we will try to get the `addr` message from a peer. To get an `addr` message, we will need to handle a few more messages as these might be sent by the peer. Also, we will send a lower version to avoid getting the `sendcmpct` request. We will use version *70013*. The following is the program that sends `getaddr` and receives `addr`:

`def parseAddrPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`payload[‘count’] = getVarInt(payload_m)`

`payload[‘addrs’] = []`

`for i in range(payload[‘count’]):`

`addr = {}`

`addr[‘timestamp’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`

`addr[‘addr’] = parseIPAddress(payload_m)`

`payload[‘addrs’].append(addr)`

`return payload`

`def sendrecvHandler(s: socket, version: int):`

`if establishConnection(s, version) == False:`

`print(‘Establish connection failed’, file=flog)`

`return`

`# send getaddr message`

`sndcmd = ‘getaddr’`

`payload = b’’`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`while True:`

`recvmsg = recvMsg(s)`

`if recvmsg[‘command’] == ‘addr’:`

`break`

`elif recvmsg[‘command’] == ‘ping’:`

`# send pong message`

`sndcmd = ‘pong’`

`nonce = recvmsg[‘payload’][‘nonce’]`

`payload = createPongPayload(nonce)`

`elif recvmsg[‘command’] == ‘getheaders’:`

`# send header message`

`sndcmd = ‘headers’`

`hashes = recvmsg[‘payload’][‘block locator hashes’]`

`stophash = recvmsg[‘payload’][‘hash_stop’]`

`payload = createHeadersPayload(hashes, stophash)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`if recvmsg[‘command’] == ‘addr’:`

`print(‘Received Addr’, file=flog)`

**Program 7.10:** Program for sending getaddr and receiving addr

We need to also handle the `getheaders` requests, which you will understand in the next and upcoming subtopics.

We use following code to call the preceding methods. The same calling code will be used to call the upcoming methods:

`if __name__ == ‘__main__’:`

`peers = getTestnetPeers()`

`print(peers)`

`p = random.choice(peers)`

`s = None`

`peerinfo = {}`

`print(“Trying to connect to “, p, file=flog)`

`s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)`

`err = s.connect(p)`

`print(‘connected’, file=flog)`

`sendrecvHandler(s, 70013)`

`s.close()`

`flog.close()`

We get the following communication log:

![](images/Figure-7.15.jpg)

**Figure 7.15:** Communication log of receiving addr from peer

# [Receiving full blockchain](#toc.xhtml#s138a)

When we install Bitcoin software and it first connects to the network, it syncs all the existing blocks of the blockchain. It tells its peers that its block height is zero and requests its peers to give blocks. This is called **Initial Block Download** (**IBD**). Since Bitcoin Core version 0.10.0, we are using the IBD method called **Headers First**.

The following figure shows the steps involved in this:

![](images/Figure-7.16.jpg)

**Figure 7.16:** Sequence diagram showing steps involved in IBD

The new node initially only has a genesis block. It sends this block’s hash in the `getheaders` requests. The peer responds with `headers` message containing a list of header hashes. Bitcoin Core sends a list of up to 2,000 block hashes. On receiving the block hashes, the node verifies the block hash and then sends `getdata` requests to its peers with a part of the header hashes it has received. Since the node is connected with multiple peers, it can ask all its peers for different sets of block hashes. The requested peer responds with all the blocks one by one. Once the node has received the requested blocks, it can again make a `getdata` request with a list of received block hashes. This process continues till the node receives all the blocks and the node’s blockchain is fully synchronized with the network.

The following is the structure of the `getheaders`, `headers`*,* and `getdata` messages:

![](images/Figure-7.17.jpg)

**Figure 7.17:** Payload structure of getheaders and getdata

The structure of the `block` is the same as we discussed in *[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml)* in *[figure 6.6](#c06.xhtml#fig6_6)*.

In the following code, we are only sending two `getheaders` requests: the first one is with only the genesis block hash, and the next one has hashes of 32 received blocks. This means we expect to receive two sets of 2000 blocks. We are making multiple `getdata` requests for each `headers` response. In the following code, each `getdata` request contains 16 block header hashes.

`def getGenesisBlockHash():`

`blkhash = rpc_connection.getblockhash(0)`

` return blkhash`

`def parseSendCompactPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`payload[‘announce’] = int.from_bytes(payload_m.read(1), byteorder=’little’)`

`payload[‘version’] = int.from_bytes(payload_m.read(8), byteorder=’little’)`

`return payload`

`def parseFeeFilterPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`payload[‘feerate’] = int.from_bytes(payload_m.read(8), byteorder=’little’)`

`return payload`

`mempool_l_g = []`

`def parseInvPayload(payload_m: mmap, payloadlen = 0):`

`MSG_TX = 1`

`payload = {}`

`payload[‘count’] = getVarInt(payload_m)`

`payload[‘inventory’] = []`

`for i in range(payload[‘count’]):`

`inv = {}`

`inv[‘type’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`

`if inv[‘type’] == MSG_TX:`

` mempool = rpc_connection.getrawmempool(True)`

` if (len(mempool_l_g) > 0):`

` new_tx = set(mempool.keys()) ^ set(mempool_l_g[-1].keys())`

` if len(new_tx) > 0:`

`mempool_l_g.append(mempool)`

`print(‘inserted mempool’, file=flog)`

` else:`

` mempool_l_g.append(mempool)`

` print(‘inserted mempool’, file=flog)`

`inv[‘hash’] = payload_m.read(32)[::-1].hex()`

`payload[‘inventory’].append(inv)`

`return payload`

`def parseBlockHeader(payload_m: mmap):`

`hdr = {}`

`hdr[‘version’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`

`hdr[‘prev_blockhash’] = payload_m.read(32)[::-1].hex()`

`hdr[‘merkle_root’] = payload_m.read(32)[::-1].hex()`

`hdr[‘timestamp’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`

`hdr[‘bits’] = payload_m.read(4)[::-1].hex()`

`hdr[‘nonce’] = payload_m.read(4)[::-1].hex()`

`return hdr`

`def parseGetBlocksGetHeadersPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`payload[‘version’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`

`payload[‘hash count’] = getVarInt(payload_m)`

`payload[‘block locator hashes’] = []`

`for i in range(payload[‘hash count’]):`

`h = payload_m.read(32)[::-1].hex()`

`payload[‘block locator hashes’].append(h)`

`payload[‘hash_stop’] = payload_m.read(32)[::-1].hex()`

`return payload`

`def parseHeadersPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`payload[‘count’] = getVarInt(payload_m)`

`payload[‘headers’] = []`

`for i in range(payload[‘count’]):`

`hdr = {}`

`start = payload_m.tell()`

`h_b = hashlib.sha256(payload_m.read(80)).digest()`

`hdr[‘blkhash’] = hashlib.sha256(h_b).digest()[::-1].hex()`

`payload_m.seek(start)`

`hdr[‘header’] = parseBlockHeader(payload_m)`

`hdr[‘txn_count’] = getVarInt(payload_m)`

`payload[‘headers’].append(hdr)`

`return payload`

`def parseTxPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`payload[‘version’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`

`payload[‘tx_in count’] = getVarInt(payload_m)`

`payload[‘tx_in’] = []`

`for i in range(payload[‘tx_in count’]):`

`txin = {}`

`txin[‘prev_tx_hash’] = payload_m.read(32)[::-1].hex()`

`txin[‘prev_tx_out_index’] = int.from_bytes(payload_m.read(4),`

` byteorder=’little’)`

`txin[‘bytes_scriptsig’] = getVarInt(payload_m)`

`txin[‘sriptsig’] = payload_m.read(txin[‘bytes_scriptsig’]).hex()`

`txin[‘sequence’] = payload_m.read(4)[::-1].hex()`

`payload[‘tx_in’].append(txin)`

`payload[‘tx_out count’] = getVarInt(payload_m)`

`payload[‘tx_out’] = []`

`for i in range(payload[‘tx_out count’]):`

`txout = {}`

`txout[‘satoshis’] = int.from_bytes(payload_m.read(8), byteorder=’little’)`

`txout[‘bytes_scriptpubkey’] = getVarInt(payload_m)`

`txout[‘scriptpubkey’] = payload_m.read(txout[‘bytes_scriptpubkey’]).hex()`

`payload[‘tx_out’].append(txout)`

`payload[‘locktime’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`

`return payload`

`def parseBlockPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`payload[‘version’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`

`payload[‘prev_blockhash’] = payload_m.read(32)[::-1].hex()`

`payload[‘merkle_root’] = payload_m.read(32)[::-1].hex()`

`payload[‘timestamp’] = int.from_bytes(payload_m.read(4), byteorder=’little’)`

`payload[‘bits’] = payload_m.read(4)[::-1].hex()`

`payload[‘nonce’] = payload_m.read(4)[::-1].hex()`

`payload[‘txn_count’] = getVarInt(payload_m)`

`payload[‘txns’] = []`

`for i in range(payload[‘txn_count’]):`

`payload[‘txns’].append(parseTxPayload(payload_m))`

`return payload`

`def createGetHeadersPayload(hdr_info_l: list, version: int):`

`version_b = struct.pack(‘<L’, version)`

`blk_locator_hashes_b = b’’`

`count = 0`

`for i in range(len(hdr_info_l) - 1, len(hdr_info_l) - 32, -1):`

`if i < 1: # assuming first block is genesis`

` break`

`blk_locator_hashes_b += bytes.fromhex(hdr_info_l[i][‘blkhash’])[::-1]`

`count += 1`

`blk_locator_hashes_b += bytes.fromhex(getGenesisBlockHash())[::-1]`

`count += 1`

`hash_count_b = setVarInt(count)`

`stop_hash_b = bytes(32)`

`payload = version_b \`

` + hash_count_b \`

` + blk_locator_hashes_b \`

` + stop_hash_b`

`return payload`

`def waitForBlock(s: socket):`

`while True:`

`recvmsg = recvMsg(s)`

`if recvmsg[‘command’] == ‘block’:`

`break`

`elif recvmsg[‘command’] == ‘ping’:`

` sendPongMessage(s, recvmsg)`

`return recvmsg`

`def sendGetHeadersMessage(s: socket, hdr_info_l: list, version: int):`

`sndcmd = ‘getheaders’`

`payload = createGetHeadersPayload(hdr_info_l, version)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`def waitForHeaders(s: socket):`

`while True:`

`recvmsg = recvMsg(s)`

`if recvmsg[‘command’] == ‘headers’:`

` break`

`elif recvmsg[‘command’] == ‘ping’:`

` sendPongMessage(s, recvmsg)`

`return recvmsg`

`def createGetDataPayload(count: int, hash_l: list):`

`MSG_BLOCK = 2`

`hash_count_b = setVarInt(count)`

`hashes_b = b’’`

`for i in range(count):`

`type_b = struct.pack(‘<L’, MSG_BLOCK)`

`hashes_b += type_b + bytes.fromhex(hash_l[i][‘blkhash’])[::-1]`

`payload_b = hash_count_b + hashes_b`

`return payload_b`

`def sendGetDataMessage(s: socket, count: int, hash_l: list):`

`sndcmd = ‘getdata’`

`payload = createGetDataPayload(count, hash_l)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`def sendAndHandleGetHeaders(s: socket, hdr_info_l: list, version: int):`

`sendGetHeadersMessage(s, hdr_info_l, version)`

`recvmsg = waitForHeaders(s)`

`count = recvmsg[‘payload’][‘count’]`

`for i in range(0, count, 16):`

`lindex = i + 16 if i + 16 < count else count`

`print(i, lindex)`

`blk_l = recvmsg[‘payload’][‘headers’][i:lindex]`

`sendGetDataMessage(s, lindex - i, blk_l)`

`for j in range(i, lindex):`

` waitForBlock(s)`

`return recvmsg`

`def sendrecvHeadersData(s: socket, version: int):`

`recvmsg = sendAndHandleGetHeaders(s, [], version)`

`sendAndHandleGetHeaders(s, recvmsg[‘payload’][‘headers’], version)`

`def sendrecvHandler(s: socket, version: int):`

`if establishConnection(s, version) == False:`

`print(‘Establish connection failed’, file=flog)`

`return`

`sendrecvHeadersData(s, version)`

**Program 7.11:** Program for making IBD request to peer and receiving blocks

This gives the following output. First, we send the `getheaders` request with genesis block hash and no hash stop:

![](images/Figure-7.18.jpg)

**Figure 7.18:** getheaders request sent to the peer

The following is the truncated ***headers*** response containing 2,000 headers:

![](images/Figure-7.19.jpg)

**Figure 7.19:** Received headers response from the peer

We responded with `getdata` requesting 16 blocks. Here’s the request:

![](images/Figure-7.20.jpg)

**Figure 7.20:** Sent getdata request to the peer

We got 16 blocks, and the following is one of them:

![](images/Figure-7.21.jpg)

**Figure 7.21:** Received block in response from the peer

After 16 blocks are received, we requested the next 16 blocks and again got 16 blocks. This continued till all 2,000 blocks are received. A node also needs to verify each block according to the consensus rules. Some of these consensus rules were covered in *[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml)*.

After receiving 2,000 blocks, we again send `getheaders` requests with a list of the last 31 block hashes and the genesis block hash, making it 32 hashes. The following is the part of the request:

![](images/Figure-7.22.jpg)

**Figure 7.22:** Truncated getheaders request made to the peer

We again got the next 2,000 block `headers`*,* and we repeated the process. This can be continued till we receive all the blocks. Once less than 2,000 `headers` are received, we can also send `getheaders` request to other peers. By sending `getheaders` requests to other peers, we can guess the best blockchain and keep blocks in different chains to be able to undo blocks.

The IBD method is also used to synchronize blocks if blockchain is more than 24 hours behind.

# [Synchronizing blockchain](#toc.xhtml#s139a)

If our node is less than 24 hours behind, we must consider the possibility that there may be competing chains. In this case, we need to get blocks from different peers and keep the blocks in competing chains to undo them if the other chain becomes longer. We use the same method to get blocks as in the last subtopic, the only difference here is that we are getting blocks from multiple peers. Our node also needs to decide which chain it needs to consider best and generally, the longer chain is preferred.

# [Transaction broadcasting](#toc.xhtml#s140a)

As we know, to spend an unspent output available as UTXO, we create a transaction and send it to the peer. We may also receive a transaction from our peers, which we may need to send to other peers. In this subtopic, we will understand how a node receives a transaction.

The following figure shows the steps involved in getting transactions:

![](images/Figure-7.23.jpg)

**Figure 7.23:** Sequence diagram showing the steps involved in transaction broadcast

When a node receives a transaction, it sends an `inv` message to its peer. The peer node checks whether it has seen the transaction earlier. If not, it sends back `getdata` requests with option `MSG_TX` and the `txid`. The node that had sent the `inv` message responds with the actual raw transaction.

`inv` has the same payload structure as `getdata`. The `tx` message has the same message structure as the Bitcoin transaction we discussed in *[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml), [figure 6.30](#c06.xhtml#fig6_30)*.

The following code processes the `inv` message if it has the option `MSG_TX`:

`def createGetDataTxPayload(payload: dict):`

`MSG_TX = 1`

`data_b = b’’`

`count = 0`

`for i in range(payload[‘count’]):`

`# we only request data for tx`

`if payload[‘inventory’][i][‘type’] == MSG_TX:`

`type_b = struct.pack(‘<L’, payload[‘inventory’][i][‘type’])`

`hash_b = bytes.fromhex(payload[‘inventory’][i][‘hash’])[::-1]`

`data_b += type_b + hash_b`

`count += 1`

`count_b = setVarInt(count)`

`payload_b = count_b + data_b`

`return count, payload_b`

`def waitForInvMessage(s: socket):`

`while True:`

`recvmsg = recvMsg(s)`

`if recvmsg[‘command’] == ‘inv’:`

`break`

`elif recvmsg[‘command’] == ‘ping’:`

`sendPongMessage(s, recvmsg)`

`print(‘Received INV’, file=flog)`

`return recvmsg`

`def waitForTxMsg(s: socket):`

`while True:`

`recvmsg = recvMsg(s)`

`if recvmsg[‘command’] == ‘tx’:`

`break`

`elif recvmsg[‘command’] == ‘ping’:`

`sendPongMessage(s, recvmsg)`

`def sendGetDataMessageWithTx(s: socket, recvmsg: dict):`

`sndcmd = ‘getdata’`

`count, payload = createGetDataTxPayload(recvmsg[‘payload’])`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`return count`

`def waitAndHandleInvTxnMessage(s: socket):`

`recvmsg = waitForInvMessage(s)`

`count = sendGetDataMessageWithTx(s, recvmsg)`

`for i in range(count):`

`waitForTxMsg(s)`

`def sendrecvHeadersData(s: socket):`

`waitAndHandleInvTxnMessage(s)`

`def sendrecvHandler(s: socket, version: int):`

`if establishConnection(s, version) == False:`

`print(‘Establish connection failed’, file=flog)`

`return`

`sendrecvHeadersData(s)`

**Program 7.12:** Program for receiving and processing inv messages for transactions

The following are the communication logs showing the received `inv` message and the sent `getdata` message with a request for two transactions:

![](images/Figure-7.24.jpg)

**Figure 7.24:** The inv message received from peer and the getdata request made to the peer in response

We received two transactions as requested by our node:

![](images/Figure-7.25.jpg)

**Figure 7.25:** tx messages containing transactions received from the peer in response to the getdata request

Our node can send a received transaction to other connected nodes by first sending an `inv` message with the transaction IDs of the received transactions. This process continues till all active nodes have received the transaction.

In this subtopic, you learned how a transaction is broadcast on the Bitcoin network.

# [Block broadcasting](#toc.xhtml#s141a)

Blocks also need to be propagated on the network as quickly as possible so that even the farthest node receives it in a reasonable time and, consequently, does not create too many or too long competing branches. Before we can receive recent blocks, we need to synchronize our node with the connected peer so that the peer is aware that our node is not lagging, and our node will be able to verify the recently received block.

Once blockchain is synchronized, we are ready for live updates from peers.

Here are the different methods to broadcast blocks:

*   A miner that has mined a new block instead just broadcasts the new block via `block` message. This is called **Unsolicited Block Push**.
*   For a normal node, there are three methods to receive new blocks. These methods are called **Direct Headers Announcements**. This is enabled either by the `sendheaders` method or the `sendcmpct` message. The `sendheaders` method is the legacy Direct headers announcement method, which is available since 70012, while the `sendcmpct` method was introduced in 70014. The following sub-points explain them: 
    *   The node sends `sendheaders` immediately after the connection is established. This indicates to the peer that whenever it receives a new block, it can send *headers*. Based on `headers`, we can request `getdata`. And as a response to `getdata`*,* the peer sends blocks.
    *   Relay latency can be further reduced by requesting compact blocks. The `sendcmpct` message can be sent immediately after the connection is established. There are two methods: 
        *   **High Bandwidth Relay:** Whenever the peer receives a block, it sends `cmpctblock`. It contains a header and a list of short IDs. We look at `mempool` for a list of transaction IDs based on short IDs and reconstruct the block. If there are missing transactions in `mempool`, we request only those missing transactions by sending `getblocktxn`. And the peer responds with a `blocktxn` message containing the transactions.
        *   **Low Bandwidth Relay:** Whenever the peer receives a block, it sends a `headers` message. We send a `getdata` *message with the* `MSG_CMPCT_BLOCK` type as a response. The peer responds with `cmpctblock`, and further processing is like in **high bandwidth relay**.

# [Unsolicited Block Push](#toc.xhtml#s142a)

The following figure shows an **unsolicited block push** by the miner, which has successfully mined a block. A miner does not need to first send ***headers*** messages as it knows the peer will not have it. It also does not need to synchronize its node with peers as it can only mine a block if it is aware of the previous node in the chain.

![](images/Figure-7.26.jpg)

**Figure 7.26:** Illustration of miner broadcasting newly generated block to peers using Unsolicited Block Push

We can see that in the figure, a miner just pushes the newly mined block to all the connected peers. A miner does not require any other communication.

# [Direct Headers Announcements](#toc.xhtml#s143a)

The following figure shows Direct headers announcements (Legacy):

![](images/Figure-7.27.jpg)

**Figure 7.27:** Sequence diagram of the steps involved in Direct headers announcements (Legacy)

After a connection is established, we immediately send the `sendheaders` message to a peer to make the peer aware that instead of `inv` messages, the peer can directly send `headers` message for recently received new blocks. Before the peer can broadcast new blocks, we need to make the peer aware of the list of blocks we are holding. For this, we need to send a list of block hashes in reverse order, starting with recently received blocks and ending with the genesis block in `getheaders` requests. This is the same as we learned in the previous subtopic. As a response, the peer sends all the missing blocks in the blockchain. If there are no new blocks with the peer, then it sends a **headers** message as a response with count zero.

Once the peer is aware of the blockchain we are holding and has all the blocks in sync with the peer, we can receive new blocks from the peer. Note that our best blockchain may be different from peers’ best blockchain, so we need to be receiving blocks from different peers.

In the following piece of code, the connection is already established and now we are sending and handling requests required for receiving new blocks:

`def sendSendHeadersMessage(s: socket):`

`sndcmd = ‘sendheaders’`

`payload = b’’`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`def createHeadersPayloadNoHeaders():`

`cnt_b = setVarInt(0)`

`headers_b = b’’`

`payload = cnt_b + headers_b`

`return payload`

`def createHeadersPayload(hashes, stophash):`

`b_cnt_d = {‘fd’: 2, ‘fe’: 4, ‘ff’: 8}`

`found = False`

`for blk_hash in hashes:`

`try:`

`blk = rpc_connection.getblock(blk_hash)`

`found = True`

`break`

`except Exception as e:`

`continue`

`if found == True:`

`txcnt = 0`

`txcnt_b = setVarInt(txcnt)`

`headers_b = b’’`

`count = 0`

`while True:`

`# returns block hex`

`print(‘block_hash = %s’ % blk_hash, file=flog)`

`blk = rpc_connection.getblock(blk_hash, False)`

`blk_b = bytes.fromhex(blk)`

`blkhdr_b = blk_b[:80]`

`headers_b += blkhdr_b + txcnt_b`

`blk = rpc_connection.getblock(blk_hash)`

`count += 1`

`if count == 2000 or ‘nextblockhash’ not in blk or stophash == blk_hash:`

`print(count, file=flog)`

`print(stophash, file=flog)`

`break`

`blk_hash = blk[‘nextblockhash’]`

`cnt_b = setVarInt(count)`

`payload = cnt_b + headers_b`

`else:`

`cnt_b = setVarInt(0)`

`headers_b = b’’`

`payload = cnt_b + headers_b`

`return payload`

`def waitForHeaders(s: socket):`

`while True:`

`recvmsg = recvMsg(s)`

`if recvmsg[‘command’] == ‘headers’:`

`break`

`elif recvmsg[‘command’] == ‘ping’:`

`sendPongMessage(s, recvmsg)`

`elif recvmsg[‘command’] == ‘getheaders’:`

`sendHeadersMessage(s)`

`return recvmsg`

`def waitAndHandleHeaderResponse(s: socket):`

`recvmsg = waitForHeaders(s)`

`count = recvmsg[‘payload’][‘count’]`

`for i in range(0, count, 16):`

`lindex = i + 16 if i + 16 < count else count`

`blk_l = recvmsg[‘payload’][‘headers’][i:lindex]`

`sendGetDataMessage(s, lindex - i, blk_l)`

`for j in range(i, lindex):`

`waitForBlock(s)`

`def getBlockHashListFromCoreClient():`

`blkhash_l = []`

`height = getLastBlockHeight()`

`for i in range(31, -1, -1):`

`d = {}`

`d[‘blkhash’] = rpc_connection.getblockhash(height - i)`

`blkhash_l.append(d)`

`return blkhash_l`

`def sendrecvHeadersData(s: socket, version: int):`

`sendSendHeadersMessage(s)`

`blkhash_l = getBlockHashListFromCoreClient()`

`sendAndHandleGetHeaders(s, blkhash_l, version)`

`waitAndHandleHeaderResponse(s)`

`def sendrecvHandler(s: socket, version: int):`

`if establishConnection(s, version) == False:`

`print(‘Establish connection failed’, file=flog)`

`return`

`sendrecvHeadersData(s, version)`

**Program 7.13:** Program to receive blocks using Direct Header Announcements (Legacy)

This gives us the following sequence of message exchanges between our node and the peer.

First, we send `sendheaders` to the peer to indicate that we expect `headers` message instead of `inv` to receive blocks:

![](images/Figure-7.28.jpg)

**Figure 7.28:** The getheaders message sent to the peer indicating that our node accepts direct header announcements

We then sync the blockchain by sending the `getheaders` message with a list of recent blocks of best chain:

![](images/Figure-7.29.jpg)

**Figure 7.29:** getheaders request made to sync with the peer

Since the peer didn’t have any recent block, it responds with the following empty `headers` message:

![](images/Figure-7.30.jpg)

**Figure 7.30:** Peer responds with headers message with a list of headers

The peer sends us an empty `headers` response as it does not have any new blocks.

After this, we wait for the peer to send us new blocks whenever it receives them:

![](images/Figure-7.31.jpg)

**Figure 7.31:** Peer sends a list of headers to our node after receiving a new block

If we don’t have the block already, we request the peer to send the missing block. This is done by sending a `getblock` message to the peer with the block header hash which we received in the `headers` message.

![](images/Figure-7.32.jpg)

**Figure 7.32:** Our node sends a getdata request to peer for blocks

The peer responds with the raw block in a `block` message. The following is the truncated `block` message:

![](images/Figure-7.33.jpg)

**Figure 7.33:** Peer responds with the block message containing full block

In this subtopic, you learned how the original direct headers announcements method worked. In the next subtopic, you will understand the improved method of broadcasting recently received blocks.

# [Compact Block Announcements](#toc.xhtml#s144a)

We are aware that blocks are a collection of transactions. Most of the transactions that a block is made up of are already received by almost all the peers. So, sending the whole block will not be required if we could send a compressed transaction list along with the block header. This is the idea behind the compact Block announcement. So, since, version 70014, Direct Headers Broadcasting has been replaced with `cmpctblock`*.* and now two methods are used:

1.  For high bandwidth communication: This method is normally enabled for only a few peers as it requires more processing.
2.  For low bandwidth communication: This method is enabled for other peers.

After the connection is established, we instantly send a `sendheaders` message to a peer to make our peer aware that instead of `inv` messages, the peer can directly send `headers` message for new incoming blocks. Then, we send a `sendcmpct` message to make our peer aware that for both segregated witness and non-segregated witness transactions, we expect `headers` or `cmpctblock` messages.

The following is the structure of the `sendcmpct` payload:

![](images/Figure-7.34.jpg)

**Figure 7.34:** Structure of a sendcmpct message

In the `sendcmpct` message, there are two fields:

**Announce** is a one-byte Boolean value. Value **0** indicates support for low bandwidth relay, while value **1** indicates support for high bandwidth relay.

**Version** is an 8-byte field; currently, it can have either of the following:

*   Value 1, which indicates support for `wtxid`, which is witness transaction ID in segregated witness.
*   Value 0, which indicates support for other transactions that have transaction IDs as this.

We will cover segregated witness transactions in an upcoming chapter.

The next subtopic covers each of these relay methods.

# High Bandwidth Compact Block Announcements

The following is the sequence of message exchanges in the activity diagram:

![](images/Figure-7.35.jpg)

**Figure 7.35:** Sequence Diagram of Compact Block Announcement for High Bandwidth Relay

After receiving `sendcmpct` request for both segregated witness and non-segregated witness transactions, we send a `getheaders` request with a list of recent blocks and genesis block and synchronize our node with the peer, as we did in the previous subtopic with heading **synchronizing blocks**.

Once the peer is aware that we have all the blocks in the blockchain which it considers as the best blockchain, we can be ready to receive new blocks from the peer. Note that our best blockchain may be different from peers’ best blockchain because we will be receiving blocks from multiple peers. The best blockchain means the chain with the highest accumulated proof-of-work. This can be calculated by adding the difficulty recorded in each block in the chain. The difficulty adjustment happens only after every 2016 blocks, so the chain with the highest accumulated proof-of-work is generally the chain with more blocks.

When the peer receives a new block, it sends a `cmpctblock` message containing compressed or short IDs of all the transactions in the block. To parse and generate short IDs, we need to install the following Python package:

![](images/Figure-7.36.jpg)

**Figure 7.36:** pip package to generate and parse short IDs

The following are the structures of the `cmpctblock`, `getblocktxn`, and `blocktxn` messages:

![](images/Figure-7.37.jpg)

**Figure 7.37:** Payload structure of cmpctblock, getblocktxn and blocktxn

The following are the details of these message payloads:

![](images/233.jpg)

**Table 7.4:** List of compact messages and their description

In the following code, the connection is already established, and now we are sending and handling requests required for receiving new blocks:

`def parseShortIds(payload_m: mmap, shortids_len: int):`

`shortids = []`

`for i in range(shortids_len):`

`shortids.append(payload_m.read(6).hex())`

`return shortids`

`def parsePrefilledTxn(payload_m: mmap, prefilledtxn_len: int):`

`prefilledtxn_l = []`

`for i in range(prefilledtxn_len):`

`prefilledtxn = {}`

`prefilledtxn[‘index’] = getVarInt(payload_m)`

`prefilledtxn[‘tx’] = parseTxPayload(payload_m)`

`prefilledtxn_l.append(prefilledtxn)`

`return prefilledtxn_l`

`def parseCmpctBlockPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`pos = payload_m.tell()`

`payload[‘hdr_nonce’] = payload_m.read(88).hex()`

`payload_m.seek(pos)`

`payload[‘header’] = parseBlockHeader(payload_m)`

`payload[‘nonce’] = payload_m.read(8)[::-1].hex()`

`payload[‘shortids_length’] = getVarInt(payload_m)`

`payload[‘shortids’] = parseShortIds(payload_m, payload[‘shortids_length’])`

`payload[‘prefilledtxn_length’] = getVarInt(payload_m)`

`payload[‘prefilledtxn’] = parsePrefilledTxn(payload_m, payload[‘prefilledtxn_length’])`

`return payload`

`def parseBlockTxnPayload(payload_m: mmap, payloadlen = 0):`

`payload = {}`

`payload[‘blkhash’] = payload_m.read(32)[::-1].hex()`

`payload[‘txn_len’] = getVarInt(payload_m)`

`payload[‘txn’] = []`

`for i in range(payload[‘txn_len’]):`

`txn = parseTxPayload(payload_m)`

`payload[‘txn’].append(txn)`

`return payload`

`def createSendCompactPayload(announce: int, version: int):`

`announce_b = struct.pack(‘<B’, announce)`

`version_b = struct.pack(‘<Q’, version)`

`payload = announce_b + version_b`

`return payload`

`def createHeadersPayloadNoHeaders():`

`cnt_b = setVarInt(0)`

`headers_b = b’’`

`payload = cnt_b + headers_b`

`return payload`

`def createGetBlockTxnPayload(payload: dict, shortIDs_index_l: list):`

`hdr_b = bytes.fromhex(payload[‘hdr_nonce’])[0:80] #header`

`blkhash_b = hashlib.sha256(hashlib.sha256(hdr_b).digest()).digest()`

`print(‘blkhash = %s’ % blkhash_b[::-1].hex())`

`indexes_len_b = setVarInt(len(shortIDs_index_l))`

`indexes_b = b’’`

`for shortIDs_index in shortIDs_index_l:`

`indexes_b += setVarInt(shortIDs_index)`

`payload = blkhash_b + indexes_len_b + indexes_b`

`return payload`

`def sendSendCompactMessage(s: socket):`

`# send sendcmpct message for Segwit`

`sndcmd = ‘sendcmpct’`

`payload = createSendCompactPayload(1, 2)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`# send sendcmpct message for others`

`sndcmd = ‘sendcmpct’`

`payload = createSendCompactPayload(1, 1)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`def sendHeadersMessage(s: socket):`

`# send header message`

`sndcmd = ‘headers’`

`payload = createHeadersPayloadNoHeaders()`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`def convertTxIDs2ShortIDs(payload: dict, txid_l: list):`

`hdr_nonce_b = bytes.fromhex(payload[‘hdr_nonce’])`

`shortids_l = []`

`for txid in txid_l:`

`txid_b = bytes.fromhex(txid)[::-1]`

`h_b = hashlib.sha256(hdr_nonce_b).digest()[0:16]`

`sip = siphash.SipHash_2_4(h_b, txid_b)`

`siphash_b = sip.digest()`

`shortid = siphash_b[:-2].hex()`

`shortid_l = siphash_b[2:].hex()`

`shortids_l.append(shortid)`

`return shortids_l`

`def findMissingShortIDs(payload: dict):`

`for i in range(len(mempool_l_g)):`

`stored_mempool = mempool_l_g[-1-i]`

`txid_l = []`

`for k, v in stored_mempool.items():`

`if ‘wtxid’ in v:`

` txid_l.append(v[‘wtxid’])`

`else:`

`txid_l.append(k)`

`shortIDs = convertTxIDs2ShortIDs(payload, txid_l)`

`shortIDs_index_l = []`

`for recvd_shortID in payload[‘shortids’]:`

`if recvd_shortID not in shortIDs:`

`shortIDs_index_l.append(payload[‘shortids’].index(recvd_shortID) + 1)`

`if len(shortIDs_index_l) > 0:`

`break`

`return shortIDs_index_l`

`def waitForCmpctBlock(s: socket):`

`while True:`

`recvmsg = recvMsg(s)`

`if recvmsg[‘command’] == ‘cmpctblock’:`

`return recvmsg`

`elif recvmsg[‘command’] == ‘ping’:`

`sendPongMessage(s, recvmsg)`

` return recvmsg`

`def sendGetBlockTxn(s: socket, recvmsg: dict, shortIDs_index_l):`

`sndcmd = ‘getblocktxn’`

`payload = createGetBlockTxnPayload(recvmsg[‘payload’], shortIDs_index_l)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`def waitForBlockTxn(s: socket):`

`while True:`

`recvmsg = recvMsg(s)`

`if recvmsg[‘command’] == ‘blocktxn’:`

`return recvmsg`

`elif recvmsg[‘command’] == ‘ping’:`

`sendPongMessage(s, recvmsg)`

`def waitAndHandleHeaderResponse(s: socket):`

`recvmsg = waitForCmpctBlock(s)`

`shortIDs_index_l = findMissingShortIDs(recvmsg[‘payload’])`

`if len(shortIDs_index_l) > 0:`

`sendGetBlockTxn(s, recvmsg, shortIDs_index_l)`

`waitForBlockTxn(s)`

`def sendrecvHeadersData(s: socket, version: int):`

`sendSendHeadersMessage(s)`

`sendSendCompactMessage(s)`

`blkhash_l = getBlockHashListFromCoreClient()`

`sendAndHandleGetHeaders(s, blkhash_l, version)`

`waitAndHandleHeaderResponse(s)`

`def sendrecvHandler(s: socket, version: int):`

`if establishConnection(s, version) == False:`

`print(‘Establish connection failed’, file=flog)`

`return`

`sendrecvHeadersData(s, version)`

**Program 7.14:** Program for receiving and processing compact messages for High Bandwidth relay

We executed the above-mentioned code and got the following communication messages. I have ignored other messages, such as `ping` or `addr` or `inv`.

First, we sent `sendheaders` and `sendcpmct` for segwit and `sendcmpct` for non-segwit:

![](images/Figure-7.38.jpg)

**Figure 7.38:** Messages sent to peer that our node accepts compact messages for both segwit and non-segwit payload

Then, we sent a `getheaders` message and received **headers** message. The following is the truncated `getheaders` message and received `headers` message:

![](images/Figure-7.39.jpg)

**Figure 7.39:** Truncated getheaders request sent to peer with a list of block hashes

We get a list of headers in response, which is empty, in the following incoming message:

![](images/Figure-7.40.jpg)

**Figure 7.40:** Peer responds with a list of recent headers, not in getheaders request

The peer responded with `headers` messages without any *headers* with count zero.

Next, we waited for the peer to send us a `cmpctblock` message. Meanwhile, we received `inv` messages having transactions. The following is the truncated `cmpctblock` message we received:

![](images/Figure-7.41.jpg)

**Figure 7.41:** Peer sends cmpctblock message on receiving a new block

On receiving the `cmpctblock` message, we search received short IDs in mempool by generating short IDs for each `txid` and `wtxid`. If there are any missing transactions, we send a `getblocktxn` request message to a peer with the index of missing short IDs in the `cmpctblock` message. The following is the transaction message we sent:

![](images/Figure-7.42.jpg)

**Figure 7.42:** Our node sends getblocktxn request to peer with a list of missing short ID indexes

On receiving the `getblocktxn`*,* the peer sends a `blocktxn` message with only the missing transaction it received in the `getblocktxn` message. The following is the truncated `blocktxn` message received from a peer:

![](images/Figure-7.43.jpg)

**Figure 7.43:** Peer responds with blocktxn message containing the missing transaction

# Low Bandwidth Compact Block Announcements

The following is the sequence of message exchanges between the host and its peer in the form of an activity diagram:

![](images/Figure-7.44.jpg)

**Figure 7.44:** Sequence Diagram of Compact Block Announcement for Low Bandwith Relay

In the low bandwidth compact block announcement method, we set to announce as 0 in the `sendcmpct` message and send a `sendcmpct` message for both segregated witness and non-segregated witness transactions. Once the blockchain is synchronized, we wait for the `headers` message from the peer. In response to the `headers` message, we send a `getdata` message with `MSG_CMPCT_BLOCK` as the response.

The following code does this:

`def sendSendCompactMessage(s: socket):`

`# send sendcmpct message for Segwit`

`sndcmd = ‘sendcmpct’`

`payload = createSendCompactPayload(0, 2)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`# send sendcmpct message for others`

`sndcmd = ‘sendcmpct’`

`payload = createSendCompactPayload(0, 1)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`def createGetDataPayloadCMPCTBlock(hash_l: list):`

`MSG_CMPCT_BLOCK = 4`

`count = len(hash_l)`

`hash_count_b = setVarInt(count)`

`hashes_b = b’’`

`for i in range(count):`

`type_b = struct.pack(‘<L’, MSG_CMPCT_BLOCK)`

`hashes_b += type_b + bytes.fromhex(hash_l[i][‘blkhash’])[::-1]`

`payload_b = hash_count_b + hashes_b`

`return payload_b`

`def sendGetDataMessage(s: socket, recvmsg: dict):`

`sndcmd = ‘getdata’`

`blk_l = recvmsg[‘payload’][‘headers’]`

`payload = createGetDataPayloadCMPCTBlock(blk_l)`

`sndmsg = createMessage(sndcmd, payload)`

`s.send(sndmsg)`

`print(‘==> cmd = %s, msg = %s’ % (sndcmd, sndmsg.hex()), file=flog)`

`def waitAndHandleHeaderResponse(s: socket):`

`recvmsg = waitForHeaders(s)`

`sendGetDataMessage(s, recvmsg)`

`recvmsg = waitForCmpctBlock(s)`

`shortIDs_index_l = findMissingShortIDs(recvmsg[‘payload’])`

`if len(shortIDs_index_l) > 0:`

`sendGetBlockTxn(s, recvmsg, shortIDs_index_l)`

`waitForBlockTxn(s)`

`def sendrecvHandler(s: socket, version: int):`

`if establishConnection(s, version) == False:`

`print(‘Establish connection failed’, file=flog)`

`return`

`sendrecvHeadersData(s, version)`

**Program 7.15:** Program for receiving and processing compact messages for low bandwith relay

We execute the preceding code and get the communication log. First, our node sends `sendheader` and `sendcmpct` messages to let it know that our node supports Direct Header Announcements. When the peer receives a new block, it sends our node the following `headers` message:

![](images/Figure-7.45.jpg)

**Figure 7.45:** Received headers message from a peer with a list of blockhash and header

We respond with the following `getdata` message containing the `MSG_CMPCT_BLOCK` flag and a list of blockhash we expect from the peer:

![](images/Figure-7.46.jpg)

**Figure 7.46:** getdata request sent to the peer with a list of blockhash

The peer responds with the following `cmpctblock` message containing block header and list of short IDs for included transactions:

![](images/Figure-7.47.jpg)

**Figure 7.47:** Peer sends cmpctblock message with a list of short IDs

After receiving the list of short IDs and block header, our node responds to the peer with the following `getblocktxn` message with a list of short IDs representing the missing transaction in our node’s mempool:

![](images/Figure-7.48.jpg)

**Figure 7.48:** getblocktxn request sent to the peer with a list of missing short IDs indexes

The peer then responds with a `blocktxn` message containing only the required transactions:

![](images/Figure-7.49.jpg)

**Figure 7.49:** Peer sent blocktxn message with a requested list of transactions

This brings us to the end of this chapter.

# [Conclusion](#toc.xhtml#s145a)

In this chapter, you started off by learning about Bitcoin network topology, and you learned that nodes run different versions and may be of different types, like an archival node, a pruned node, or SPV. You also learned how a node finds out addresses of peers to connect and understood how a node gets all the blocks when it first connects with its peers and how it gets all the competing blockchain branches. Next, you learned how a node broadcasts transactions and block messages to all the remaining nodes. We did not cover network communication done by the SPV node to receive the required transactions and verify blocks. We also did not cover segregated witness transactions.

In the next chapter, you will understand the limitations of technology, its impact on nature, and the potential risks, and vulnerabilities that exist because of the design. We will thoroughly look at them and gauge whether they are real, risky, or just a myth.

# [Points to remember](#toc.xhtml#s146a)

*   Bitcoin is a peer-to-peer network that needs a TCP connection or a tor network to connect to a peer.
*   Bitcoin network is nonhierarchical, which means all nodes are equal, and there are no masters or servers. There will be TCP servers but not Bitcoin network servers.
*   Nodes can connect and disconnect anytime and can choose which nodes they need to connect.
*   Nodes require an initial set of addresses, or we need to provide initial addresses so that they can make the initial connection to peers.
*   `Version` message is the first message each node sends. If a node is fine with the information it received in the `version` message, it responds with `verack`.
*   Once `version` and `verack` messages are exchanged, the connection is considered established. Before that, nodes do not receive any other message.
*   A node can send a `ping` message to a peer anytime to know if a peer is still connected.
*   A node should reduce dependency on hardcoded DNS seeds by storing active addresses locally and requesting new addresses from its peer.
*   The first time a node is starting, it fetches a list of all block headers till the 24 hours older block. After it has received them, it needs to get headers from all the connected nodes to get all the competing chains.
*   Once the node’s blockchain is synchronized with all the peers, it is ready to receive new blocks and transactions.

# [Questions](#toc.xhtml#s147a)

1.  How do we understand that the peer is sending Bitcoin blocks or blocks in a different network?
2.  Why does a node need to receive recent blocks from multiple peers?
3.  How does the Initial Block Download method differ from Blockchain synchronization?
4.  When do you think we should use pruned node instead of an archival node?
5.  When does a node send `sendheaders` and `sendcmpct` messages?
6.  Programming questions: 
    1.  Write a program that connects with multiple peers and sends the address of one peer to another.
    2.  Write a program to receive multiple TCP connections and limit active connections.
    3.  Write a program to relay blocks to other connected nodes.
    4.  Create a raw transaction using Bitcoin Core wallet and publish it using your own program.
7.  True/False: 
    1.  It is necessary for a node to respond to `cmpctblock` message to the sending peer.
    2.  Transaction `inv` messages need the node blockchain to be synchronized with the peer blockchain.
    3.  During the initial block download, we send `getdata` request to multiple peers to improve download performance.
8.  Fill in the blanks: 
    1.  In high bandwidth compact block announcements, a node sends \_\_\_\_\_\_\_\_\_\_ message after receiving block instead of \_\_\_\_\_\_\_\_\_\_ message.
    2.  The `inv` messages are not used for broadcasting _________ anymore.
    3.  Unsolicited block push method is only ffused by the \_\_\_\_\_\_\_ node to publish \_\_\_\_\_\_\_.

# [CHAPTER 8](#toc.xhtml#c08)

# [Technology Limitations, Threats, and Vulnerabilities](#toc.xhtml#c08)

In the previous chapter, you learned the technical details of communication between nodes. This helped you understand the way transactions and blocks are propagated over the network, the way nodes find peers, and the way nodes determine which nodes to connect with.

Now that you have learned Bitcoin protocol in-depth, you can understand its limitations and vulnerabilities from a technical point of view.

In this chapter, we will learn how Bitcoin design and implementation create limitations for its use. We will understand why these limitations are important and how it gives Bitcoin its characteristics. We will also learn different ways in which the Bitcoin network can or may be compromised and why it is still secure and may not get attacked anytime soon. Additionally, we will discuss the vulnerabilities that seem to be secure today but may become potential risks for its security in the future.

# [Structure](#toc.xhtml#s148a)

In this chapter, we will cover the following topics:

*   Design limitations 
    *   Block size limitation 
        *   Effect on transaction verification
            
            ![](images/ent.jpg)FIBER: Fast Internet Bitcoin Relay Engine
            
        *   Effect on blockchain size
    *   Block time limitation
    *   Privacy limitation
    *   Solutions to privacy and scaling 
        *   Improved hardware
        *   Utreexo accumulators
        *   Signature aggregation
        *   MAST: Merklized Abstract Syntax Trees
        *   Taproot
        *   Lightning Network
        *   CoinJoin
        *   Tumbler services
*   Bitcoin mining energy usage
*   Threats to individuals and network 
    *   Threats from governments
    *   Threats from central banks
    *   Malicious hackers 
        *   Bitcoin theft
            
            ![](images/ent.jpg)Exploiting cryptographic weaknesses
            
            ![](images/ent.jpg)Malware
            
        *   Ransomware
    *   Losing private keys or seed phrase
    *   Threat due to vulnerabilities 
        *   Transaction malleability
        *   Dusting attack
        *   Mempool flood attack
        *   Selfish mining
        *   BGP hijacking attack
            
            ![](images/ent.jpg)Network partitioning attack
            
            ![](images/ent.jpg)Delay attack
            
        *   0-confirmation attack
        *   Hiding hash rate
        *   Blacklist addresses
        *   Replay attack
        *   Empty block mining
        *   Bitcoin mining centralization
            
            ![](images/ent.jpg)51% Attack
            
        *   Sybil attack
        *   Denial-of-Service (DoS) attack
        *   Quantum computing attack
        *   Hidden bugs, bug exploit, and reorg
    *   Frauds and robbery

# [Objectives](#toc.xhtml#s149a)

The main objective of this chapter is to allow readers to question Bitcoin legitimacy, necessity, and value from technological and non-technical points of view.

Additionally, knowing the attack vector of technology can help you better prepare for it and take precautions so that it will have less impact on you.

So, we will try to answer the following questions in this chapter:

*   Why doesn’t Bitcoin have very big block sizes?
*   Why doesn’t Bitcoin have a shorter block time?
*   Does Bitcoin really need to consume so much energy, and how does this impact the environment?
*   What are different ways Bitcoin network can be attacked? How serious are those attack vectors?
*   Are there any future risks to the technology?
*   Apart from technical vulnerability, what may be the other vulnerabilities?

# [Design limitations](#toc.xhtml#s150a)

Bitcoin blocks are mined every 10 minutes, and each block is limited to 1MB size for pre-SegWit and 1MB of v-size for SegWit. This leads to a low transaction rate. The following is a chart of a historic number of transactions per second:

![](images/Figure-8.1.jpg)

**Figure 8.1:** Average transactions per second

We can see that the Bitcoin transaction rate reached 18 transactions per sec. Even if blocks have all SegWit transactions, it will only reach an average of 25 transactions per sec. In comparison, Visa processes 2,000 transactions per sec on an average. This means Bitcoin is not suitable for small value payments on a global scale. To compete with Visa, Bitcoin requires a hundred times the current block size, or it needs to generate blocks in less than 10 seconds.

Bitcoin is also not very good at providing privacy. Since all transactions are on the blockchain and most bitcoin buying and selling happens through exchanges that work under regulations, almost all transactions can be linked by performing big data analysis.

# [Block size limitation](#toc.xhtml#s151a)

Increasing the block size or decreasing block time has a similar impact on the network and blockchain size. Increasing block size by 10 times or reducing block time by 10 times causes a similar increase in network traffic due to block propagation and a similar rise in blockchain size.

# [Effect on transaction verification](#toc.xhtml#s152a)

Mining nodes are competing to solve a cryptographic puzzle to mine a block. When a block is mined, it is published on the network. The block needs to reach all the nodes quickly. If during the propagation of the block, another node solves the cryptographic puzzle and publishes its block, there will be disagreement between nodes on the next block of the Bitcoin blockchain. So, two competing chains are formed, which compete to prove that they are the right chain. A chain with higher accumulated *PoW* is considered the longer chain and is accepted, while the other chain is discarded.

As you can imagine, if block propagation doesn’t happen quickly, multiple competing chains can get formed, and the time to resolve the correct chain may increase exponentially with an increase in propagation delay.

The following is the chart of Block propagation delay since 2015. There are some gaps in the chart as some data is missing:

![](images/Figure-8.2.jpg)

**Figure 8.2:** 30-day rolling average for time for the block to reach 90% nodes

As you can see, block propagation delay got reduced from 15 seconds in 2015 to 2 seconds in 2018. Since 2016, there have been multiple enhancements introduced in P2P Bitcoin network protocol messages. This might be the reason propagation delay has rapidly reduced.

It is standard practice to wait for 6 confirmations before accepting a transaction. This is because if a race condition arises due to simultaneous mining of blocks, it normally gets resolved before the sixth confirmation.

If the race condition arises because of simultaneous mining of blocks but does not get resolved within the next six blocks, then it will impact the overall confidence of a confirmed transaction.

So, block size is an important factor in propagation delay and confidence in the Bitcoin network.

# FIBRE: Fast Internet Bitcoin Relay Engine

**Fast Internet Bitcoin Relay Engine** (**FIBRE**) is a protocol designed with an intention to deliver Bitcoin blocks to the connected nodes with delays comparable to the physical limit of the connection. It depends on a well-managed network to deliver the intended outcome.

With FIBRE, it becomes far less likely that there will be two competing chains. This makes selfish mining difficult and makes the network fairer.

# [Effect on blockchain size](#toc.xhtml#s153a)

As you have learned by improving gossip protocol, we can greatly reduce propagation delay and, consequently, allow block size to increase. However, blockchain size is another important barrier in increasing block size. Currently, the Bitcoin blockchain is already 400GB, which has increased nearly 60GB in the last year.

The following is the chart of rise in the blockchain size with year:

![](images/Figure-8.3.jpg)

**Figure 8.3:** Change in blockchain size over the years

If we also include all the indexes, this number goes up to 390GB. If the number of transactions goes even higher, then we may see up to 100GB addition every year. This is a significant number, which makes it a bit costly to run full node now. For most Bitcoin enthusiasts, to run full node means giving up 400GB of disk space, and this may increase by 100GB every year. In 2 years, it will become 500GB of spare storage and 1TB in a few more years. To allow college students or enthusiasts to maintain full node, disk storage costs should come down, and higher than 1TB becomes the norm in laptops.

The following chart shows how blockchain size is adding up every 365 days:

![](images/Figure-8.4.jpg)

**Figure 8.4:** Blockchain size change rate (365-day rolling sum)

As an alternative, Bitcoin Core provides an option to prune blockchain and limit it to a much smaller size. Bitcoin Core maintains indexes of unspent transactions and blocks, so a prune node can still verify transactions and blocks and is still considered a full node. However, it cannot reconstruct a pruned block and cannot fulfill the block request for peer nodes. Since each block contains a reference to older blocks, this is not a problem if recent blocks are maintained, and there are enough nodes maintaining the full blockchain.

Pruned nodes have several advantages. A pruned node can be created with just 288 blocks, which will not be more than 1GB. So, using pruned node, we can have a full node running on embedded devices.

However, this still does not help increase block size as blockchain verification takes days to complete. So, blockchain size on disk is not the main limiting factor in increasing block size; instead, blockchain verification time itself is the main factor stopping us from increasing block size.

Currently, it takes between 1 and 7 days to download the whole blockchain because of verification time.

To reduce the blockchain verification time, we either need to wait till better-performing computers will be able to reduce the verification time, or we need to find a more efficient block verification algorithm.

# [Block time limitation](#toc.xhtml#s154a)

Block time adjustment happens every 2016 block and is based on network hash rate. Network hash rate is not very well distributed, so it gets affected by environmental disasters and govt. controls.

The following is the average time to mine a block with a rolling average of 2016 blocks:

![](images/Figure-8.5.jpg)

**Figure 8.5:** Average time to mine a block (Rolling average of 2016 blocks)

A few incidents in the past have caused the hash rate to drop:

In August 2020, heavy rainstorms in China lead to a 15% drop in the Hash rate.

In June 2021, China enforced ban on cryptocurrency mining which led to the drop of more than 50% in the network hash rate. We can see the corresponding rise in block time of more than 15 min in the preceding figure.

A drop in the hash rate causes block-time to increase, which leads to more transactions reaching mempool before getting included in a block. Since more transactions compete for entry into blockchain, the transaction fee rises. However, this problem goes away after the next difficulty adjustment, which happens after every 2016 blocks or nearly 2 weeks. A drop in hash rate extends block time, so 2016 blocks may take more than 2 weeks.

The following is an illustration of how the number of transactions waiting to get added to a block grows as the block time increases:

![](images/Figure-8.6.jpg)

**Figure 8.6:** Dependence of mempool size on Block time

This is an inconvenient disruption that lasts for more than 2 weeks. A solution for this problem could be to adjust the difficulty in every block by taking the rolling average of 2016 blocks.

However, there is a reason this is not implemented in Bitcoin. Since only a few mining pools control almost all the Bitcoin network hashrate, a sophisticated DDOS attack on those large miners can bring down the hashrate of the network, which will give an attacker a window to compromise the network. For the greater good of security, this inconvenience is a necessary evil.

# [Privacy limitation](#toc.xhtml#s155a)

Bitcoin is not a privacy coin. It does not support Privacy protocols such as Zero Knowledge Proof. So, we need to realize that Bitcoin does record trails of information in the blockchain and exchanges from where we buy them and online merchants/websites we use them at. However, Bitcoin does provide ways to hide identity by using CoinJoin or tumbler services, by simply buying from individuals directly, and so on.

# [Solutions to privacy and scaling](#toc.xhtml#s156a)

In the previous subtopics, you learned that the major reason we do not want block size to rise is the initial block download verification time. There are quite a few developments happening that might help Bitcoin to scale and as well as improve its privacy.

Criminals can hack into data in exchanges and merchants and relate them with information in blockchain to obtain insights about individuals. A totalitarian government can also get information from exchanges and merchants. They can ultimately use that information against the individuals whose information is revealed. Therefore, bitcoin is sometimes considered *pseudo-anonymous.*

Bitcoin does provide ways to hide identity. Here are a few ways identity can be made hidden:

1.  The simplest method of hiding information is never to use an address twice.
2.  Some wallets, like the Samourai wallet and the Wasabi wallet, provide variations of CoinJoin to make a transaction fungible.
3.  A person can also send or receive transactions directly from another person or a miner.

These are some of the ways to maintain privacy*.* It depends on the individual how well they can manage their privacy, and under political pressure, individuals can be forced to make their transactions more private and hidden. Therefore, bitcoin is also considered *censorship-resistant*.

The following are the different privacy and scaling solutions that are already in use or are under development:

![](images/254.jpg)

**Table 8.1:** Impact of different solutions on the privacy and scalability of the Bitcoin network and transaction

# [Improved hardware](#toc.xhtml#s157a)

Improvement in chip technology and miniaturization can reduce time to verify blocks, reducing initial block download time. There is a possibility that we may be able to develop microprocessors with 2nm technology and have improved RISC architecture and other hardware design elements that will produce more performant hardware, which will verify blockchain in lesser time.

# [Utreexo accumulators](#toc.xhtml#s158a)

Utreexo makes improvements in the transaction and block verification by changing the structure of UTXO indexes. The feature is still in development and has shown promising results. If successful, it will allow an increase in the block size by reducing the blockchain verification time for Initial Block Download.

# [Signature aggregation](#toc.xhtml#s159a)

Bitcoin is going through a lot of changes, though it is quite difficult to get an enhancement into the consensus rules. Enhancements are important as it makes the technology future-proof. At the same time, enhancements related to the consensus rules are not reversible, and there is a very high cost to the network if a wrong enhancement is introduced. Plus, consensus rules need to be backward compatible, so every change needs to be introduced as a soft fork, which makes consensus rules more complicated with each enhancement.

Bitcoin is going to have a new signature scheme called Schnorr signature. Unlike ECDSA, Schnorr signatures are linear, which means Signatures can be aggregated into a new Signature without affecting its size.

This can be understood as follows:

![](images/Figure-8.7.jpg)

**Figure 8.7:** Signature aggregation using Schnorr Signature

As we know, signatures take quite a bit of space in a transaction, so we can reduce the effective size of a transaction by aggregating multiple signatures in a Multisig input. This will help accommodate more transactions in a block, increasing Bitcoin’s transaction rate.

Additionally, since signature aggregation allows multiple signatures and public keys to be aggregated into a single signature and public key, it becomes difficult to know if funds are held by a single person or a group of persons. This makes tracing of the consumers of bitcoin difficult without compromising the verifiability of the transaction.

# [MAST: Merklized Abstract Syntax Trees](#toc.xhtml#s160a)

In P2SH transactions, we can embed complex scripts with conditions and sub-conditions. When the transaction is spent, only a portion of the nesting of multiple conditionals gets executed. The spender must reveal the script to utilize the locked fund. This has unnecessary high costs and is bad for privacy.

To understand conditionals and sub-conditionals, a script can be represented as an Abstract Syntax Tree. This kind of notation is commonly used by compilers to compile a programing language. As an example, the common script we use is 2-3-multisig. Considering, 2-3-multisig between Alice, Bob, and Carol, we can represent it as the following conditional statement:

`(Alice AND Bob) OR (Bob AND Carol) OR (Carol AND Alice)`

The following is a representation of the Abstract Syntax Tree for the 2-of-3-multisig between Alice, Bob, and Carol:

![](images/Figure-8.8.jpg)

**Figure 8.8:** Abstract Syntax Tree for the 2-of-3-multisig

MAST uses the Merkle tree to represent the Bitcoin script. The Merkle tree is a modification of the Abstract Syntax tree, in which each side of a condition is joined by the concatenated hash of both sides. This separates each condition in such a way that a transaction spender only needs to reveal the conditionals required for Merkle proof and leave other conditionals hidden. So, this is like Merkle Proof, which was explained in *[Chapter 5, The Whitepaper](#c05.xhtml),* under the topic ***Simplified Payment Verification*** *section of the whitepaper*. MAST is a concept that does not have direct use in Bitcoin transactions. There is no such thing as Pay-2-Script-Merkle-Root. It is just a concept to understand MAST, but MAST does get used in Taproot, so this is important to understand.

So, in a hypothetical P2SMR transaction, the following will happen:

![](images/Figure-8.9.jpg)

**Figure 8.9:** A hypothetical P2SMR transaction based on MAST

Since only a part of the script is revealed, it reduces the number of bytes used in the transaction, which helps in scaling, and it improves privacy since it does not reveal the whole script.

# [Taproot](#toc.xhtml#s161a)

Taproot goes even further. It hides a whole script or most parts of the script under the public key signature pair. So, we can have a complex script with multiple conditionals and parties hidden under the address. This reduces transaction size, and a complex script takes the space of only a P2PKH transaction or a bit more for script hashes. And the transaction hides all the details of a script within a public key and a signature so that an observer cannot determine that it is a single signature or a multisig or a complex smart contract. Therefore, it is great for privacy as well.

The following is the illustration for funding transaction:

![](images/Figure-8.10.jpg)

**Figure 8.10:** Funding transaction for Taproot

To spend the P2TR UTXO, we can either sign the transaction with a private key or tweak the public key, which only Alice and Bob will know, or we will need to provide the required hashes, as in Merkle Proof, along with Signature.

So, there are two possible transactions created using P2TR UTXO:

1.  When Alice and Bob sign the transaction, in this case, since they have created a tweak public key, they can also create Aggregated signature. Here’s the illustration:
    
    ![](images/Figure-8.11.jpg)
    
    **Figure 8.11:** Taproot Spending transaction with the main condition
    
2.  When Bob and Carol or Carol and Alice sign the transaction, since they have not created a tweak public key, they need to provide hashes as in Merkle Proof to allow validation. Here’s the illustration:
    
    ![](images/Figure-8.12.jpg)
    
    **Figure 8.12:** Taproot Spending transaction for other conditions
    

# [Lightning Network](#toc.xhtml#s162a)

Any of the enhancements or changes in block size can only have a limited effect on the increase in the number of transactions per second. Even if we could increase the block size by 10 times, the number of transactions per second will only reach 200 to 250 transactions per second, which is still much smaller than credit cards. Visa handles 65,000 transactions per second as per records.

Lightning Network is a layer 2 protocol on Bitcoin blockchain. We already covered the Lightning Network in [Chapter 4](#c04.xhtml) titled *Bitcoin in the real world* and Topic *Accepting bitcoins by an online merchant.*

The lightning Network allows transactions to happen off-chain. And since it is between individuals through a route involving a few more hops, there is no constrained-on number of transactions that can happen in a second. This enhances Bitcoin’s ability to complete a substantial number of transactions and compete with MasterCard and Visa Card.

Since there could be any number of transactions between parties without recording them on the blockchain and only the final transaction is recorded, it improves the privacy of payments between two parties.

Schnorr Signature will further reduce the cost of creating and closing a Lightning Network channel by integrating the signatures of both parties into a single signature. We can even have multiparty channels as we can now aggregate signatures.

# [CoinJoin](#toc.xhtml#s163a)

CoinJoin is a method of making bitcoin fungible by joining multiple transactions in such a way that it is difficult to know which outputs are receiving coins from which UTXO. There are diverse ways to achieve this.

One way is to divide values in inputs and join values in output such that output values are matched. This way, it becomes difficult to match inputs with outputs.

For example, the following are the three required transactions:

![](images/Figure-8.13.jpg)

**Figure 8.13:** Transactions to be in a CoinJoin

To do the CoinJoin, we try to join all three transactions into one transaction such that it is difficult to know which UTXOs are going to which recipient. This removes identity from bitcoin, making them similar to cash.

Here’s an example of the CoinJoin transaction:

![](images/Figure-8.14.jpg)

**Figure 8.14:** Example of a CoinJoin

In the preceding example, it is impossible to know which addresses belong to Bob, Dave, and Kirsten and who paid in which output.

# [Tumbler services](#toc.xhtml#s164a)

Tumbler services are provided by anonymous exchanges and are not traceable as they mostly use the TOR network. They charge fees for mixing transactions. The tumbler services take the bitcoin from the sender and forward them to the receiver, but in between, they mix them with other transactions or their own transactions and move them between multiple addresses. This makes them impossible to track.

This can be understood from the following illustration:

![](images/Figure-8.15.jpg)

**Figure 8.15:** Example of a Tumbler service

In the preceding illustration, there is no way to know that Alice is paying Bob or Carol is paying Dave or John is paying Kirsten because all are separate and unrelated fully mixed transactions.

Unlike CoinJoin, which is provided by some popular wallets, Tumbler services are not provided by any known entity. This is the very nature of their operations. Consequently, such services are risky as they can steal your coins.

# [Bitcoin mining energy usage](#toc.xhtml#s165a)

Bitcoin has a bad image because of its high energy usage, and that is true, as we can see in the following image:

![](images/Figure-8.16.jpg)

**Figure 8.16:** Bitcoin mining energy usage compared to top electricity consuming nations

The preceding image shows the 50 highest energy-consuming countries. Bitcoin currently occupies the 24^(th) place, and it is nearly equal to the Poland, which is a rich and developed country in Europe.

In contrast, global energy usage is 23000 TWh, and Bitcoin energy usage is only 154TWh, which is less than 1.0%. Bitcoin energy usage is related to growth in the currency. As the interest in Bitcoin grows, so will be the energy usage by the Bitcoin network.

We will do some calculations to understand why it is not as bad as it appears to be.

To not promote mining equipment, we will not disclose the name of mining equipment we are using as a reference.

Consider that I am using mining equipment in a location in Bengaluru city, which currently has the following power costs:

![](images/262.jpg)

**Table 8.2:** Electricity charges in Bengaluru City

We use the same programs as in *[Chapter 6, Blockchain, Transactions and Mining](#c06.xhtml),* under topic *Mining cost*.

We take a miner with a hash rate of 90 TH/s and Energy consumption of 3050W, which is defined as follows:

`def getMinerHashRate():`

`return 100 * 10**12`

`def getMinerPowerWatt():`

`return 3050`

`We define unit price as follows:`

`electricity_rates = {“rate_slabs”: [{“min”: 1, “max”: 30, “unit_price”: 4}, {“min”: 31, “max”: 100, “unit_price”: 5.45}, {“min”: 101, “max”: 200, “unit_price”: 7}, {“min”: 201, “unit_price”: 8.05}]}`

If the current price of bitcoin is ₹28,05,753, which is defined as follows:

`def getCurrentSellPrice():`

`return 2805753`

And following is the code to call the `miningReturn` method to get mining profit:

`blk_hash = ‘000000000000000000016acc33775c2ea52abeb4407381b84fee5f7af97fdd8b’`

`blk_hash_b = bytes.fromhex(blk_hash)[::-1]`

`blk_index = getBlockIndex(blk_hash, block_db_g)`

`blk_hdr_b = getBlockHeaderBytes(blk_hash_b)`

`jsonobj = getBlockHeader(blk_hdr_b)`

`blk_reward = getBlockReward(blk_index[‘height’])`

`miner_hashrate = getMinerHashRate()`

`print(“Miner hashrate = %d” % (miner_hashrate))`

`miner_power = getMinerPowerWatt()`

`print (“Miner Power in Watt = %f” % (miner_power))`

`expense = getMiningPowerExpense(miner_power)`

`print (“Miner Power Expense Per Month = %.2f” % (expense))`

`bits_b = bytes.fromhex(jsonobj[‘bits’])[::-1]`

`mining_return = miningReturn(miner_power, miner_hashrate, bits_b, blk_reward)`

`print(“Mining Return Per Month = %s” % (mining_return))`

On running it, we get the following result:

![](images/Figure-8.17.jpg)

**Figure 8.17:** Mining profitability of test miner in Bangalore

The equipment cost nearly ₹9,00,000/-.

If mining reward remains constant, it will take 3 years to achieve breakeven with the equipment. This looks like reasonable returns, but considering that the mining hash-rate might double during this period, it might reduce the monthly mining returns to between 0 and ₹5,000, which is negligible, and you will need to buy another equipment, which might be more costly and might consume more power. Consequently, you might never reach breakeven. On the positive side, in 3 years, the price of bitcoin may rise and mining remains profitable.

This makes mining a bit risky unless you get subsidized power, power from a cheap source, or power source that comes from wasted fuel or energy.

Consequently, large miners are mostly situated in countries where electricity is subsidized. Additionally, many powers generation companies and fossil fuel companies are also mining bitcoin to utilize their excess power and fuel. Natural gas and oil drilling companies are using waste gas for bitcoin mining, which is especially good for the environment as methane is a much bigger greenhouse gas than carbon dioxide.

The fuel efficiency of wind and solar power is better than non-renewable energy sources, except natural gas and nuclear power. Additionally, off-grid power saves energy wastage due to transmission which further improves mining profitability. This makes off-grid renewable energy the energy of choice for non-subsidized mining.

And for governments subsidizing power for bitcoin, mining is costly as it hardly creates any jobs, so governments tend to attack such facilities, like in China and Iran.

So, contrary to contemporary belief, we learned that bitcoin mining is good for the environment because of the following reasons:

*   Miners prefer off-grid renewable energy as a source of electricity.
*   Waste fuel, which consists of the most potent greenhouse gases, is utilized for bitcoin mining and converted to a less potent greenhouse gas, i.e., carbon dioxide.
*   Bitcoin mining discourages governments to subsidize power to mining companies.

# [Threats to individuals and network](#toc.xhtml#s166a)

Till now in this chapter, you learned about the design limitations and how the Bitcoin developer community is working to overcome those limitations. You also learned about how large energy consumption in bitcoin mining is not a big problem for the environment.

Bitcoin, being a decentralized peer-to-peer open network for value transfer, is both lucrative for an attacker and perceived as a threat to the existing global monetary system. So, the Bitcoin network and bitcoin investors may have to deal with various attacks, such as attacks from governments, central banks, malicious hackers, fraudsters, or robbery.

However, threats may not always be because of diverse types of attacks but may also be because of risk and potential vulnerabilities that exist today or may be a problem in the future.

# [Threats from governments](#toc.xhtml#s167a)

As we saw in ***[Chapter 4, Bitcoin in the Real World](#c04.xhtml)****,* under the topic ***Bitcoin and*** *c****ryptocurrency*** ***egulations***, in most countries around the world, the laws on cryptocurrencies are not clear or are non-existent. This gives authorities extra judicial powers to handle cryptocurrencies, which sometimes involve threat and corruption. Sometimes, taxes are to be paid, but the clause to pay taxes is not clear. This is the problem in India, like in many other countries. This affects exchanges, traders, investors, and merchants, leading to inflated prices of cryptocurrencies and related services and risk of loss of investments or business.

There is also no legal protection, which is sometimes misused by miscreates through extortions and frauds.

Ban on dealing in bitcoin is a potential risk, and some countries do take that route, which means anyone dealing in cryptocurrencies gets punished. However, this has been done by very few countries.

# [Threats from central banks](#toc.xhtml#s168a)

Most countries, developed or developing, do not have fully convertible currencies, and they see stronger currencies as a threat. The fear is that the central banks will lose control, and their currencies may become weak and lose value. This is a legitimate concern, mostly because of the weakness in the fiscal policies of a country. There is also a risk that central banks may not be able to know the use of funds for illicit activities. So, as a precautionary measure, KYC and AML norms are strongly enforced by all financial institutions.

Cryptocurrencies are quite fluid, and they can easily slip through regulatory loopholes. This is why central banks are wary of their widespread use. In many countries, we have seen a banking ban exists and, in some countries, large institutions are also not allowed to deal in cryptocurrencies. On the other hand, in some countries, certain activities related to cryptocurrencies are prohibited.

As we have learned, unlike most other cryptocurrencies, bitcoin is not really a good speculative instrument and is more of an asset like gold. Like gold, bitcoin should not be seen as a threat to the global monetary system, and central banks should recognize that the risk of money laundering is the lack of regulation, so each country needs more regulation, not less.

# [Malicious hackers](#toc.xhtml#s169a)

Hackers may attack individuals, exchanges, and networks in various ways. Hacking may be stealing, robbery, or exploiting protocol weaknesses. Stealing could be done by trying to crack security by brute force or knowledge-based attacks, or it could be through social engineering, among other ways. Robbery can also involve social engineering and ransomware.

# [Bitcoin theft](#toc.xhtml#s170a)

Bitcoin theft can happen by weakness in cryptography being used by the bitcoin wallet. Theft can also happen by other methods through malware, spyware, or social engineering.

# Exploiting cryptographic weaknesses

The Hashing and ECDSA algorithm used by Bitcoin is quite safe, but there are still some risks because of the selection of entropy, salt, or other parameters in cryptographic algorithms.

*   **Brute force attack**
    
    A 256-bit ECDSA cryptography used in Bitcoin has the same security strength as the 3072-bit RSA cryptography. It will take billions of years to crack 256-bit ECDSA cryptography used by Bitcoin by just brute force. There is still a possibility that in a few decades, we may learn the way to crack cryptography. When that happens, Bitcoin will need to shift to a new algorithm.
    
*   **Low entropy attack**
    
    The signature algorithm used by Bitcoin is very secure and cannot be broken by even the most advanced computers in millions of years. However, the security of a private key depends on the entropy of the random generator used to generate the private key. If a low entropy system is used to generate the private key, then the private key can be guessed by brute force.
    
*   **Collision attack**
    
    SHA256 is considered collision-resistant, which means it is almost impossible to generate two messages with the same hash value. So, Bitcoin is secure from such attacks.
    
*   **Precomputed hashes or rainbow tables**
    
    The PBKDF2-HMAC-SHA512 algorithm is used in hierarchical deterministic wallets for the generation of private and public keys. The algorithm requires a large number of iterations to generate secure keys, and it must be used with salt, else the generated keys are prone to attacks using precomputed hashes. Additionally, the iterations or rounds should be at least 2048 but are expected to be 10,000 or even higher. Using high computational power, a lower round generated key can be derived and all bitcoin in the wallet can be stolen.
    

# Malware

Malware is a malicious program that intends to steal information or damage the computer or network. Malware could be used to steal information by **spyware or trojan**. Malware can be installed through some form of **social engineering**, which can use urgency, greed, and fear to make you click on a link or download from a link in mail or web page. Malware can also be installed through a fake website that looks real. These malware are called **trojan**.

A malware called **spyware** then gets installed in the computer without the user’s knowledge and can read files, collect information from websites, and read keystrokes from the keyboard.

# Ransomware

Ransomware is a new form of hacking where an attacker encrypts files on the system after getting access to a system through malware. After that, the attacker asks for bitcoin as ransom in exchange for decrypting the files.

The following are the steps taken by ransomware to rob bitcoin:

![](images/Figure-8.18.jpg)

**Figure 8.18:** Steps taken by the attacker to perform a ransomware attack

# [Losing private keys or seed phrase](#toc.xhtml#s171a)

Losing private keys and wallet seed is so common that it is estimated that 20% of all bitcoin are lost and will never be recovered. When bitcoin was new and it had little to no value, people did not care about the private keys that much, so losing bitcoin was easy. Even after bitcoin started becoming a valuable wallet, software were not easy to use, and losing a private key was still easy.

With Hierarchical Deterministic wallets, it has become easier to manage private keys, but people still forget where they saved the seed and so, lose their bitcoin forever. Since hardware wallets have become quite common, it has become a lot less common to lose Bitcoins. Nevertheless, people do lose their bitcoin because of carelessness, natural disasters, or other such circumstances.

# [Threat due to vulnerabilities](#toc.xhtml#s172a)

The Bitcoin network does have certain risks because of design and ongoing technology improvements.

# [Transaction malleability](#toc.xhtml#s173a)

Transaction malleability will be discussed in detail in *[Chapter 12, Segregated Witness](#c12.xhtml)*, so we are not discussing it here.

# [Dusting attack](#toc.xhtml#s174a)

A dusting attack is used to deanonymize the user. An attacker sends dust transactions or extremely low-value transactions to a substantial number of target addresses. The attacker then tracks the funds to determine which addresses belong to the same wallet and then tries to deanonymize the user to which the wallet belongs. This requires a sophisticated analysis of transactions related to dust transactions. Once user identity is found, the attacker performs a phishing or malware attack on the target user.

This can be understood from the following illustration:

![](images/Figure-8.19.jpg)

**Figure 8.19:** Steps taken by the attacker to perform dusting attack

Dusting may be used for other purposes; for example, money launderers can send dust transactions to a substantial number of recipients to make such transactions difficult to track.

To prevent dusting attacks, a wallet should not accept small value transactions. Bitcoin nodes do not forward transactions with network fees smaller than the relay fee, which is 5000 satoshis for many nodes. This is quite high, so the relay fee should be itself a deterrent for dusting attacks.

# [Mempool flood attack](#toc.xhtml#s175a)

Mempool flood attack is a type of DoS attack in which a mempool of nodes is filled with low-value unconfirmed transactions. This type of attack has happened on the Bitcoin network, which caused network fees to rise.

The attack was first reported in July 2015, and in May, August, and November 2017, such attacks again happened on the Bitcoin network. It is suspected that these attacks were done to influence support for larger block sizes within Bitcoin developers, miners, and exchanges.

Bitcoin nodes avoid this attack by configuring the minimum relay fee a transaction needs to pay to get it broadcasted to the network. In Bitcoin core, this is set to 5000 satoshi by default. Currently, its value is nearly $2, which is still a significant amount to deter an attacker. Also, unlike in 2017, the transaction fee is much higher now as bitcoin prices have gone up, so such an attack is not possible anymore.

# [Selfish mining](#toc.xhtml#s176a)

Selfish mining is a malicious mining attack where there are only a few miners with high mining power, but none has more than 50% mining hash power. In this attack, the selfish miner gets a greater hash power share by inflicting cost to the competing miners.

Mining hash power share is the average probability of a miner to find a block. Since it is an average probability, a miner with a lower probability can sometimes find a block faster than it would on an average. A selfish miner utilizes this to inflict a cost on other miners.

Consider a scenario in which there are three miners:

Alice: 40%, Bob: 25%, and Carol: 35%

Suppose Carol is the selfish miner. When Carol finds a block, instead of publishing the block immediately, it holds it for some time and tries to find another block.

If Carol is lucky and finds another block, then she waits for another miner to publish a block while trying to find another block. If in the meantime, Bob or Alice publishes a block, then Carol publishes both the blocks. Since Carol has a longer chain, the other block published by Bob or Alice gets rejected. This inflicts a cost on the other miner, which is greater than the cost Carol has paid by holding block.

If Carol finds three blocks, then she waits for two blocks to get published by other miners. If Carol finds four blocks, then she waits for three blocks to get published by other miners.

On the other hand, if Carol is not lucky and Alice or Bob publishes their block before Carol, then Carol immediately publishes the block held by her and does not propagate the competing block. So, even though Alice or Bob published the block first, some nodes will still receive Carol’s block first and will consider the other block as the competing chain. In this case, which chain wins depends on probability and the advantage Carol has in block propagation delay. Even if Carol has a very low chance of winning this and if her hash rate is more than 33% of the share of network hash rate, she still will be able to increase her affective probability of mining a block as a selfish miner.

We can see that selfish mining does not reduce the cost of mining new blocks. In fact, it increases the cost of mining a block, even for Carol. Since it inflicts more cost on the competing miners, Carol gets the advantage.

This may have multiple consequences:

1.  Competing miners will stop their loss-making mining equipment, which will increase Carol’s share of the network.
2.  Competing nodes will join Carol and start mining with her, giving her more than a 51% share of the network hash rate.
3.  The competing node will go bankrupt and stop operation altogether, leading pool miners to switch to other remaining miners, which might lead Carol to have more than a 51% hash rate.
4.  Competing nodes will upgrade their loss-making equipment, which will cost them a fortune, but in the end, other miners will remain profitable and continue.

Here’s the flowchart of the selfish mining scenario:

![](images/Figure-8.20.jpg)

**Figure 8.20:** Flowchart of the steps taken by the miner to perform selfish mining attack

It is easy to identify if a miner is involved in selfish mining as selfish mining increases the likelihood of the existence of competing chains compared to the normal case when there is no selfish miner.

Selfish mining gives the advantage to a selfish miner. but there are multiple reasons why miners will not want to do it:

*   Selfish mining can be easily identified. which will affect Bitcoin network reputation and consequently, bitcoin’s long-term value.
*   Mining has extremely high input costs and most of the time, profit margins are slim. So, a miner needs to look at the long term and would not want to engage in anything that affects bitcoin’s value.
*   Mining is done by pools that depend on pool miners. A bad reputation of the pool may cause pool-miners to switch to a different pool, so the pool will ultimately lose hash rate.

The Bitcoin network has largely avoided this kind of attack in the past, even though there may have been one or two such incidents.

The bitcoin developer community has been pushing for the adoption of the FIBRE protocol to reduce block propagation delay. If FIBRE is widely used, it will become exceedingly difficult for miners to attack networks by selfish mining.

# [BGP hijacking attack](#toc.xhtml#s177a)

BGP stands for **Border Gateway Protocol**. It is a gateway protocol that exchanges reachability information between Autonomous Systems or AS. AS is like the network created by an ISP or Internet Service Provider.

There are multiple ways BGP hacking can be used to attack Bitcoin networks. The reason this attack is possible is bitcoin mining is highly centralized as there are only a few mining pools controlling most of the network hash rate. Additionally, Bitcoin network messages are unencrypted and so, can be modified by an attacker.

By hacking the BGP server in AS, attackers can delay, modify, or even drop Bitcoin network messages. This can be used to perform multiple types of attacks.

# Network partitioning attack

Network partitioning means disconnecting nodes in such a way that it creates a disjoint network.

If an attacker gets control of ISP servers responsible for sending BGP routing messages, it can effectively partition the network into two disjoint networks.

Because of partition attacks, mining pools can unknowingly start working on separate chains. This will appear as a DoS attack as the mining hash-rate share between mining pools will change, and it will be quickly known to the world.

However, till the issue gets resolved, the attacker can broadcast two different transactions that use the same UTXOs in both the network and perform a double-spend attack. If the issue does not get resolved till six confirmations are received, then both the retailers would have accepted the payment, essentially double-spending. When the network partition gets removed, the chain with the greater accumulated Proof-of-work gets accepted and the other chain gets rejected. The merchant whose transaction was rejected will be at a loss.

This can be understood with the following illustration:

![](images/Figure-8.21.jpg)

**Figure 8.21:** Illustration of network partition by BGP hijacking attack

If you are a merchant, it makes sense to watch hash rate distribution among mining pools.

# Delay attack

A variant of the partitioning attack is the delay attack. In this type of attack, instead of creating disjoint networks, the attacker delays messages from one set of AS to another set of AS, essentially giving an advantage to some AS over others.

In this attack, the attacker keeps the victim uninformed about the latest blocks. If the victim is a merchant, then the merchant will not know that the spending is already done by the attacker and so, will successfully double-spend. If the victim is a miner, then the miner will be working on an obsolete chain wasting hash power leading to losses.

If you are a merchant, then it makes sense to monitor the latest blocks through applications running on different AS such as cloud platforms or web-APIs provided by popular websites.

# [0-confirmation attack:](#toc.xhtml#s178a)

A zero-confirmation attack can be executed if a merchant does not wait for transaction confirmation. To execute this attack, the attacker creates two different transactions utilizing the same UTXO: one for paying the merchant, and the other for moving the value to a different address. The attacker publishes the transaction for the merchant only to the merchant’s node while publishing the other transaction simultaneously to other nodes.

The merchant nodes accept the transaction it received first, which is the transaction paid to him, and rejects the other one. If the other transaction gets into a block, then the transaction containing payment to the merchant is rejected, and the merchant loses the payment.

The attacker can connect to multiple distant nodes to publish the other transaction to improve the probability of success.

The following is the illustration of the attack:

![](images/Figure-8.22.jpg)

**Figure 8.22:** Steps that an attacker takes to perform a 0-confirmation attack

To execute this attack, the attacker needs to know the merchant’s node address and needs to connect to it. This attack becomes easier if the merchant is not hiding its IP address using the TOR network. The attacker can find out the merchant’s IP address by pinging on his website. Alternatively, if it’s a physical store that provides WIFI, then the attacker can find IP addresses through the public network. There could be other ways to find IP addresses, like using phishing attacks.

# [Hiding hash rate](#toc.xhtml#s179a)

In *[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml)* under Topic ***Coinbase*** *t****ransaction*,** you learned that miner adds fingerprint in the mined block. This fingerprint can be used to determine the relative hash rate contribution of each mining pool. Since we can calculate network hash rate, we can utilize this information to calculate the hash rate of each mining pool.

However, this happens because miners tell us when they have successfully mined a block. If they don’t, then they can easily increase their hash-rate contribution without anyone knowing it, except its pool miner who rarely bothers to know. Pool miners don’t even try to know if they are really mining Bitcoin or Bitcoin Cash or Bitcoin SV.

# [Blacklist addresses](#toc.xhtml#s180a)

According to estimates prior to mining crackdown, Chinese miners contributed almost two-thirds of the Bitcoin network hash rate. Consequently, the Bitcoin network was prone to Chinese political decisions. For instance, China could blacklist Bitcoin addresses belonging to a specific entity, such as businesses, institutions, or individuals.

As a clarification, this attack is not about China, because if the mining hash rate of another country or a group of countries was higher than 50% of the network hash rate, then those countries could also blacklist addresses belonging to specific entities.

Since China’s hash rate was greater than 50%, it could ignore any block, which includes transactions originating from or received by certain entities, and it would be always able to mine longer chains. Consequently, other miners would also have to comply with Chinese law enforcement, otherwise they would make losses on mined blocks and will soon become bankrupt.

A country with high network hash rate can also perform a variation of Blacklist attack where even with lower than 50% mining hash power it can enforce blacklisting by utilizing selfish mining technique.

We have seen recently that a miner accepted **Office of Foreign Assets Control** (**OFAC**) compliance norms. OFAC is a financial intelligence and enforcement agency of the US. Consequently, the miner blacklisted non-compliant transactions for sometime but the miner later agreed to not enforce OFAC

# [Replay attack](#toc.xhtml#s181a)

When the Bitcoin network has a hard-fork and a new type of cryptocurrency is created, the new type of coin is akin to a new coin created from scratch. except that it shares the same history as the parent cryptocurrency. It is an unnecessary burden for a new cryptocurrency to have a history that is not useful. However, the benefit is that the new currency can have a name like the original coin so that it looks familiar and can easily get recognized.

The following is an illustration of a hardfork:

![](images/Figure-8.23.jpg)

**Figure 8.23:** illustration of a hardfork

If the new cryptocurrency maintains the same addressing scheme as the parent cryptocurrency, then it doesn’t need to onboard users as the users of parent cryptocurrency automatically become users of new cryptocurrency. Additionally, their UTXO is valid on both chains.

However, this has issues as people can mistakenly send coins to the receiver on a different chain and lose the payment.

Additionally, if transaction format or address schemes are not changed, then a transaction that is valid in one network will be also valid in another network. These valid transactions can be replayed in different networks and coins can be stolen. This is called a ***Replay attack***.

When a hardfork happens, many users realize that they have additional coins in the new forked network. They transfer or sell their coins in order to make quick money, but this transaction can be replayed by the attacker on the original higher valued network and since the transaction has a much higher value on the original network, the attacker gets a bigger value.

This can be understood from the following illustration:

![](images/Figure-8.24.jpg)

**Figure 8.24:** Bob performing a replay attack

In our view, it is unethical for a cryptocurrency to not implement a new addressing scheme and transaction format.

# [Empty block mining](#toc.xhtml#s182a)

Bitcoin consensus rules do not stop miners from mining empty blocks. This means in the race to find the correct nonce, a miner can just mine an empty block, and it will have the advantage over other miners, which will be using additional processing power in selecting, adding transactions to blocks, and calculating total network fees they have collected.

The following chart shows the transaction fees as a percentage of block reward:

![](images/Figure-8.25.jpg)

**Figure 8.25:** Transaction fee as a percentage of Block Reward

After the recent block reward update, block reward in each block is 6.25![](images/Bitcoin.jpg)and network fees collected per block is nearly 0.7![](images/Bitcoin.jpg), which is significantly large, and no miner will want to lose that amount.

The following chart shows the number of empty blocks mines each year:

![](images/Figure-8.26.jpg)

**Figure 8.26:** Count of Empty blocks mined each year

We also need to realize that mining has become more competitive over the years, which means miners have to spend a lot of money to buy the most efficient equipment. Due to this, mining empty blocks is not in the interest of the miners. Consequently, as we can see in the preceding chart, the number of empty blocks has reduced over the years.

# [Bitcoin mining centralization](#toc.xhtml#s183a)

We know that miners join and form a pool. Few Mining pools control most of the network computational power.

The following image shows the distribution of mining hash rate among mining pools:

![](images/Figure-8.27.jpg)

**Figure 8.27:** Hash rate distribution of each mining pool

At the time of authoring the book, the top 4 mining pools were F2Pool, AntPool, Poolin, and BTC.com.

It is expected mining should get more decentralized over time. In fact, it has already become more decentralized in the last 2-3 years. There are two reasons why it might happen:

*   Mining pools are mostly located at colder places where electricity is subsidized. This affects the people of those places. As mining energy need increases, it will discourage the government to subsidize power and encourage them to move to the off-grid energy source. This will allow miners to move to locations that get more sunlight or wind or waste energy from natural gas or oil mines.
*   Chip miniaturization allows producing more efficient microprocessors, which improve ASIC machines to have better energy efficiency. Since ASIC machines were improving quite rapidly, the miners closer to chip manufacturing had the advantage over miners which were far away as transportation adds to cost and time. As chip miniaturization is hitting the limits, efficiency improvements have slowed down and so, the advantage is quickly going away. This will allow miners from other locations to compete with Chinese miners, leading to further decentralization of mining hash power.

# 51% Attack

A 51% attack is the attack in which a miner has more than half of the network hash rate. In such a condition, the miner can do the following:

*   Remove a transaction from a block in the blockchain by mining an already mined block.
*   Censor individuals by not including transactions that send or receive bitcoin belonging to addresses owned by specific blacklisted addresses of businesses, institutions, or individuals.
*   Change its own recent transactions.

If the top four miners join hands, their combined hash rate will be more than 50%, and they can out-compete the rest of the miners and perform a 51% attack.

In July 2014, Ghash.io reached more than half of the network computational power, but it later agreed that it will never cross 50% computational power. It is important to understand why we never had such a scenario since then and why any miner would agree to not take over the network.

Mining also adds value to the network, which means even though miners can join and block transactions from specific countries or exchanges, they will not do anything that will get noticed and will affect the network, which is their source of earning.

# [Sybil attack](#toc.xhtml#s184a)

In the case of the Sybil attack, the attacker creates a substantial number of nodes. The victim node will only connect to an attacker node. The attacker nodes do not forward transactions and blocks to the target node, essentially disconnecting it from the network. The attacker can send the blocks it has created to the target node containing transactions that the attacker wants the node to get. Since the target node is only getting blocks from attacking nodes, it considers the transaction valid even though it was already spent in the actual network.

To avoid Sybil attack, Bitcoin core client only makes one connection in /16 addresses, which means attacking nodes will need to be widely distributed and be in multiple /16 addresses and still isolate the node, which is not possible as then the attacker will have to take over the entire Bitcoin network.

# [Denial-of-Service (DoS) Attack](#toc.xhtml#s185a)

A denial-of-service attack or DoS attack is an attack in which the attacker floods the target with lots of data, which makes it busy and so the target is unable to provide the service it needs to provide.

Bitcoin nodes are robust in handling denial-of-service attacks, but this does not mean that DoS attacks can’t happen to Bitcoin nodes. If malicious nodes try to flood a node, it will simply blacklist those connections and close them. Flooding with a valid message is costly, and invalid messages get quickly rejected. Additionally, there are limits being set on transactions, relay fees, and block size by nodes to avoid such attacks.

Here are some of the ways nodes avoid being flooded by DoS messages:

*   Transactions greater than 100 Kbytes are considered nonstandard.
*   Block size is limited to 1MB vsize.
*   Nodes do not accept or forward transactions with network fees lesser than the relay fee set by the node.
*   Nodes do not forward a double spent transaction.
*   Nodes do not forward orphan transactions. Transactions that do not have known unspent transactions.
*   Nodes limit the number of orphan transactions.
*   Nodes ignore big orphan transactions.
*   Nodes do not forward orphan blocks, i.e., blocks that do not have known the previous block.
*   Nodes do not forward blocks that have already been seen or forwarded.
*   Bans IP Addresses that misbehaves for 24 hours by default.
*   Maintains DoS score for each connected node and disconnects if a node misbehaves multiple times.
*   Nodes have an upper limit of the number of signatures they can accommodate in the signature cache.
*   Limits the size of the script.
*   Limits the keys in OP\_CHECKMULTISIG operation.
*   Limits the size of each value in a transaction.
*   Only UTXOs are stored in memory.
*   Limits the number of signature checks a transaction input may request.

For more detailed information, refer to:

**[https://en.bitcoin.it/wiki/Weaknesses#Denial\_of\_Service\_.28DoS.29\_attacks](https://en.bitcoin.it/wiki/Weaknesses#Denial_of_Service_.28DoS.29_attacks)**.

# [Quantum computing attack](#toc.xhtml#s186a)

Quantum computers use superimposition of electron states and entanglement of electrons to perform complex operations, which are not possible by classical computers. However, quantum computers are not general-purpose computers, and they are useful for only certain types of operations.

Unlike conventional computers, quantum computers use qubits instead of bits. While bits can be either 0 or 1, qubits can be both 0 and 1 at the same time. So, one qubit has 2 superpositions of states, and N qubits will have 2 to the power N superposition of states. This makes N qubit quantum computer equivalent to the 2^N bit classical computers. A 500-qubit quantum computer is a 2^500 classical computer, which is more than the number of atoms in the whole universe.

However, there is a catch: the moment we try to find the quantum states, the superposition is lost, and the qubits become normal bits. This is called **quantum decoherence**. So, any quantum computation must finally result in non-superimposed bits. This makes Quantum computers difficult to program and requires a complete redesign of the way computation happens right from the gates to programming language. Additionally, it is only suitable for calculations that require a very high level of parallelism but results in a relatively short value.

The following algorithms that can be used by attackers against Bitcoin:

*   Shor’s algorithm, which, according to estimates, will need nearly 2500 qubits to crack the 256-bit ECDSA algorithm used by Bitcoin.
*   Grover’s algorithm can exponentially speed up Bitcoin mining.

The SHA-256 hashing used by Bitcoin is safe from Quantum computers.

In December 2020, Chinese researchers achieved 76 qubit systems. There are still problems with Quantum computers. The biggest problem that Quantum Computer faces is Quantum Decoherence, which leads to errors and loss of coherence (superposition).

Quantum decoherence can arise from any environmental factors, such as thermal fluctuations, radiations, and magnetic fields. This makes a qubit very unstable, and superimposition can be lost within a fraction of milliseconds. Researchers try to increase decoherence time by creating an environment that has a very low temperature, very low radiation, and a very low magnetic field. We have not been successful in achieving that, and as of now, a Quantum computer, irrespective of its qubit count, cannot perform any deep operation, which makes them almost useless for any real-world applications.

The problem of noise-induced quantum error can be solved by quantum error correction.

This may change in the future as we become better at controlling these environmental factors. However, we don’t know when or if quantum computers will ever be a threat to asymmetric cryptography.

If we can build significantly reliable quantum computers with several thousand qubits sufficient to crack 256-bit ECDSA used for Bitcoin, then it would only affect bitcoins, which is held in addresses with known public keys. As you learned in the previous chapters, it is advisable not to reuse addresses. If we don’t reuse addresses, hackers cannot use quantum computing to steal bitcoin.

If quantum computers can crack Bitcoin public keys, then Bitcoin can move to quantum-resistant algorithms such as Lamport signatures.

On the other hand, Grover’s algorithm can only accelerate nonce search and give an advantage to the miner using quantum computers. However, like other mining devices, it will be competing against other quantum computers doing the mining. The scenario will be like the situation when ASIC miners introduced mining advantage. This does not affect the network; instead, over time, it improves the security of the network.

# [Hidden bugs, bug exploit, and reorg](#toc.xhtml#s187a)

It is always possible that there exists an unidentified bug in the Bitcoin core software, consensus rules, etc. which may get exploited by an attacker. This could be an inflation bug that would allow an attacker to pay themselves extra bitcoin and would lead to an increase in bitcoin supply. It could lock unspent transactions indefinitely. It can affect the miner or user.

If a bug is exploited, then it needs to be identified immediately or within a few blocks. Once identified bug needs to be fixed, it may be required for the Bitcoin community to plan Bitcoin blockchain reorg. Blockchain reorg means convincing Miners to upgrade Bitcoin software, invalidating the blocks from the exploited blocks, and restart mining.

When a block is mined, the miner cannot immediately move the newly minted bitcoin. The miner needs to wait for 100 blocks before they can move it. This allows developers to fix the bug and convince miners to reorg before 100 blocks get mined, which is roughly 16 hours and 40 minutes. The transactions that were confirmed during this time will need to wait to get confirmed again. It is also possible that the transaction that was confirmed earlier may not get confirmed again before getting dropped by the mempool of most nodes. This will negatively affect the Bitcoin network’s credibility.

# [Frauds and robbery](#toc.xhtml#s188a)

Bitcoin is very valuable, so it attracts criminals. Like gold, bitcoin is sometimes robbed at gunpoint.

Bitcoin can also be stolen by fraudsters through social engineering like using rewards, urgency, and fear or through fake services. The frauds could be like banking frauds where one gains access to crypto exchange through OTP. A fraudster can ask you to fill in details and can take your PIN or wallet seeds. A fraudster can also ask you to transfer coins to your wallet in return for service.

# [Conclusion](#toc.xhtml#s189a)

In this chapter, you learned about the limitations of Bitcoin design, why those limitations are necessary, and what developments are happening to address those limitations. You also learned about the different ways bitcoin holders and networks could be attacked, the different ways by which merchants, miners, and holders of Bitcoin can mitigate most of those risks, and why some of the risks are not really a risk because those are either too difficult or are financially unviable for an attacker.

We discussed how Bitcoin centralization is both bad for network security and good for getting enhancement accepted by the Bitcoin mining community. We also saw how Bitcoin energy usage is good for the environment.

In the next chapter, you will learn about the Bitcoin address format and understand how to generate the private key, public key, and addresses. You will also learn about how you can create your bitcoin wallet and how you can protect the wallet from hackers.

# [Points to remember](#toc.xhtml#s190a)

*   Blockchain verification time is the most important reason due to which Bitcoin block size is limited to 1MB to 4 MB.
*   By replacing multiple signatures and complex scripts with a single public key and signature using Taproot, signature aggregation, and Schnorr signatures, we can accommodate more transactions in a block and have better privacy.
*   Lightning Network is a layer two payment protocol.
*   Lightning Network provides privacy as individual transactions are not recorded on the Bitcoin blockchain.
*   Lightning Network provides scaling as an unlimited number of transactions can happen between peers.
*   Bitcoin mining helps lower carbon footprint by encouraging the use of off-grid renewable energy sources and utilizing waste energy.
*   Bitcoin mining difficulty is adjusted at every 2016 block.
*   Mining pools being centralized are prone to natural disasters, power failures, government crackdowns, or DDoS attacks, which leads to drop in network hash rate.
*   A sudden drop-in hash rate causes block time to increase and network fees to spike.
*   Lack of legal protection encourages fraud and illegal activities in bitcoin.
*   Most central banks discourage the use of bitcoin and other cryptocurrencies to protect their currencies against capital flight.
*   High entropy random number generators help generate private keys that are safe from brute force attacks.
*   SHA256 is collision-resistant.
*   Salt protects against rainbow table attacks.
*   Low-round PBKDF2-HMAC-SHA512 algorithms are prone to brute force attacks.
*   Hierarchical Deterministic Wallets, along with 12- to 24-word mnemonic code, eases securing of private keys.
*   A trojan is a malware that disguises itself as legitimate software.
*   Spyware is malicious software that gets installed without the victim’s knowledge and steals information and sends it to attackers.
*   Social Engineering is the use of psychological manipulations in order to collect private information.
*   Transaction malleability bug affects the non-SegWit transactions.
*   BIP62 solves most of the transaction malleability issues.
*   Bitcoin nodes, by default, enforce a minimum transaction fee on all the received transactions in order to accept and forward them. This fee is called the relay fee.
*   Relay fee protects addresses from dusting attacks.
*   To protect against dusting attacks, a wallet should not accept very small value transactions.
*   In mempool flood attack, an attacker publishes a large number of small value transactions, which increases network fees.
*   Mempool flood attacks have become unviable because even relay fee is not cheap.
*   In selfish mining, a malicious mining pool takes greater control over the network hash rate by inflicting cost to the competing mining pools.
*   Selfish mining is easy to identify as it causes a greater occurrence of competing chains.
*   FIBRE stands for Fast Internet Bitcoin Relay Engine.
*   FIBRE is a protocol design that can achieve propagation delay nearly close to the physical limit with the help of a well-managed network.
*   FIBRE reduces propagation delay to less than a second, which gives little room for a malicious mining pool to attack networks using selfish mining.
*   Mining pools being centralized are also prone to network partitioning and delay attacks using BGP hijacking.
*   Unconfirmed transactions, even if those are SegWit, are prone to double-spend attacks.
*   Always run a full node to connect using Tor routing.
*   Miners add fingerprints in the coinbase transaction of a newly mined block, which helps the network know the mining hash rate of each miner.
*   A miner can hide its real hash rate and can mine over 51% hash rate if it does not add its fingerprints.
*   Since Bitcoin mining is not well distributed across geographies, it is easy for governments to enforce blacklisting of addresses based on their political agenda.
*   A hardfork on Bitcoin consensus can lead investors to replay attacks who try to take the profit out of newly added coins.
*   Hardfork coin having the same address and transaction format as the parent coin is the reason for the existence of Replay attacks.
*   If the top four mining pools join hands, then they can execute a 51% attack on the network.
*   A 51% attacker can force the network to blacklist addresses or double-spend the transactions it controls.
*   In a Sybil attack, the attacker eclipses the entire network for a victim by launching a large number of nodes.
*   Bitcoin core client only makes one connection in /16 addresses to prevent Sybil attack.
*   In a DoS attack, the attacker floods the victim with lots of data, which prevents the victim from providing the intended service.
*   Quantum computers use superimposition of electron states and entanglement of electrons to perform complex reversible operations, which are not possible by classical computers.
*   Quantum computers are prone to even the smallest environmental disturbances, which cause waveform collapse, and this phenomenon is called quantum decoherence.
*   Quantum computers can theoretically crack the 256-bit ECDSA algorithm used by Bitcoin using few thousand qubits.
*   Quantum computers can use Grover’s algorithm to accelerate Nonce search in bitcoin mining.
*   The miner needs to wait for 100 blocks to use the minted coins, which gives a window of several hours for developers to fix an exploit and reorg the blockchain.

# [Questions](#toc.xhtml#s191a)

1.  Explain how block size affects Initial Block Download (IBD).
2.  How will the decentralization of Bitcoin mining secure the Bitcoin network?
3.  Explain all the necessary precautions a retailer should take to protect itself from double-spend attacks.
4.  Explain all the necessary precautions a miner should take to protect against different types of attacks and improve profitability.
5.  Explain all the necessary precautions a Bitcoin user should take to protect against different types of attacks.
6.  Explain why privacy is important, and explain the different ways in which Bitcoin user can protect their privacy.
7.  True/False: 
    1.  SegWit transactions are safe against 0-confirmation attacks.
    2.  Bitcoin is fungible because it is replaceable by an equal quantity of bitcoin received from different sources.
    3.  CoinJoin is better than mixer services because mixers can steal your coins.
    4.  SHA256 is safe against quantum computation attacks.
    5.  Grover’s algorithm will end bitcoin mining, and Bitcoin will need to change the mining algorithm.
8.  Fill in the blanks: 
    1.  In a \_\_\_\_\_\_\_\_\_ attack, the attacker floods a node with messages, so the node fails to serve other legitimate nodes.
    2.  In a \_\_\_\_\_\_\_\_ attack, the attacker floods the Bitcoin network with transaction messages, which increases transaction fees.
    3.  An attacker can partition Bitcoin network by hijacking \_\_\_\_\_\_\_\_\_.
    4.  Replay attack happens when hard forked coin uses the same \_\_\_\_\_\_\_\_\_\_ format and \_\_\_\_\_\_\_\_\_\_\_ scheme.
    5.  By \_\_\_\_\_\_\_\_\_\_ mining, a mining pool with a hash rate greater than 25% can take greater control over network hash power.
    6.  Transaction \_\_\_\_\_\_\_\_\_\_\_\_\_\_ was resolved with \_\_\_\_\_\_\_\_\_\_\_\_\_ witness enhancement.

# [CHAPTER 9](#toc.xhtml#c09)

# [Wallets and Addresses](#toc.xhtml#c09)

In the previous chapter, we looked at Bitcoin as a network protocol, its strength that makes it a great technological innovation, and its limitations and conditions that pose risks to its long-term existence.

In this chapter, you will learn to access your bitcoins, send them to single or multiple addresses, and execute a smart agreement between parties.

To access your bitcoins, you need a software program that can generate addresses for receiving bitcoins and the software can sign a transaction in order to transfer it to the receiving parties. This software program is called a ***wallet***. This chapter focuses on private keys, public keys, addresses, and wallets. We will cover transactions and signing of transactions in detail in the next chapter. The signing of a transaction is also an essential part of wallet functionality. So, a wallet has three essential functionalities:

*   It provides information about bitcoins you are holding.
*   It provides addresses to receive bitcoins.
*   It helps sign a transaction so that it can be published on the network.

Wallets can be classified in several ways. The following are the types of wallets based on the medium of usage:

*   **Mobile wallets:** These are installed on mobile phones. Some of the famous ones are Electrum, Mycelium, Samourai, etc.
*   **Desktop wallets:** These are installed on the desktop. Some of the famous ones are Bitcoin Core, Armory, Electrum, etc.
*   **Hardware wallets:** These are separate hardware devices that are security-focused and considered to provide better security. Two companies mostly dominate this market: Ledger Nano and Trezor.

Apart from the preceding wallet types, wallet services are also provided by most exchanges.

Wallets can also be classified based on keys as follows:

*   **Deterministic wallets:** These wallets allow a user to generate keys deterministically using a seed. These wallets don’t need to store keys and so are safe from hacking and are also safe from the risk of losing the keys.
*   **Non-Deterministic wallets:** These wallets store collections of keys. These are also called **Just a Bunch of Keys (JBOK)**.

Wallets can also be classified as hot and cold:

*   **Cold wallets** store private keys offline, and the signing of transactions happens offline, which makes them very secure. Hardware wallets are examples of cold wallets.
*   **Hot wallets** encrypt private keys but keep them online. These wallets also sign transactions online. Most of the mobile and desktop wallets are online wallets. Bitcoin Core provides an online wallet.

In this chapter, we will build a deterministic wallet. In the next chapter, you will learn how to use the wallet for signing a transaction offline.

*\*\*\*\* Never use private keys or mnemonic code used anywhere in this book. Your bitcoins will get stolen \*\*\*\**

# [Structure](#toc.xhtml#s192a)

In this chapter, we will cover the following topics:

*   Mnemonic code
*   Format and generation of private key, public key, and address 
    *   Private key
    *   Public key
    *   Address
*   Hierarchical Deterministic (HD) wallet 
    *   Master key generation
    *   Key derivation 
        *   Parent private key -> Child private key
        *   Parent public key -> Child public key
        *   Child private key -> Parent private key (Wallet private key leak)
        *   Deriving hardened child keys
    *   Extended keys 
        *   Master extended public and private keys
        *   Extended public and private keys
    *   Key derivation path

# [Objectives](#toc.xhtml#s193a)

The objective of this chapter is to help you understand wallet, public keys, private keys, and Bitcoin addresses both in terms of functionality and implementation.

We will discuss the functions of wallets. Additionally, you will understand the different ways to classify them and learn to create your own hierarchical deterministic wallet and generate their seed. You will also learn about security related to wallets.

This chapter also covers the format of private keys, public keys, and addresses, and you will also learn to generate them.

# [Mnemonic code](#toc.xhtml#s194a)

To create a deterministic wallet, you first need to learn to generate a random seed. This seed will help you generate private key and public key pairs. The random number you choose determines how secure the private key is against brute force or knowledge-based attacks. A good random number is truly random, which means it does not follow a pattern that an attacker can determine. Additionally, it is preferable that generation is well distributed, which means if we keep on generating it over a finite field, then after a significantly long time, the finite field is very well distributed, does not have large patches of density, and is not quite uniform. So, a random number needs to protect against both brute force attacks and intelligent attacks involving inferring patterns. This requires choosing the right source of randomness, also called the *source of entropy*. This is mostly collected from hardware sources such as fan noise or mouse movement. We can also use background noise as a source of entropy.

We will implement a program to generate the random seed using BIP 39.

Link: **[https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)**

The document describes the method of generating seed, which consists of 12/18/24 common English words. The set of words is not just a purely random sequence; it also contains checksum, and so, it cannot be randomly generated without following the method described in BIP.

There are 2048 mnemonic words with which seed is generated, which translates to 11 bits. The whole list of mnemonic words can be found at **[https://github.com/bitcoin/bips/blob/master/bip-0039/english.txt](https://github.com/bitcoin/bips/blob/master/bip-0039/english.txt)**.

If we are preparing 12-word mnemonic code, we require 11\*12 bits, which are 132 bits.

132 bits consists of a 128-bit random number and 4-bit as its checksum.

We will refer to the bits in random numbers as entropy bits. Here’s an illustration of the process of getting a 12-word mnemonic seed:

![](images/Figure-9.1.jpg)

**Figure 9.1:** Illustration of mnemonic code generation from entropy

The following formula is used to calculate the required bits:

*Entropy Bit Count = Mnemonic Word count \* 32 / 3*

Here’s the formula for **checksum\_bit\_count**:

*Checksum Bit Count = Mnemonic Word count/ 3*

This is the code to get the **checksum\_bit\_count** and **entropy\_it\_count**:

`def getChecksumBitCount(mnemonic_length: int):`

`if (mnemonic_length % 3) != 0:`

`raise ValueError(‘Invalid Mnemonic code length’)`

`checksum_bit_count = mnemonic_length // 3`

`return checksum_bit_count`

`def getEntropyBitCount(mnemonic_length: int):`

`if (mnemonic_length % 3) != 0:`

`raise ValueError(‘Invalid Mnemonic code length’)`

`entropy_bit_count = (mnemonic_length * 32) // 3`

`return entropy_bit_count`

**Program 9.1:** Program to get checksum bit count and entropy bit count from mnemonic seed length

The following is the code to generate entropy bits:

`def getRandomNumberBits(bit_count: int):`

`r = random.SystemRandom().randrange(0, 1 << 32)`

`r_b = r.to_bytes((r.bit_length() + 7) // 8, ‘big’)`

`h = hashlib.sha256()`

`h.update(r_b)`

`h_b = h.digest()`

`byte_count = bit_count // 8`

`rand_num_b = h_b[0:byte_count]`

`return rand_num_b`

**Program 9.2:** Program to generate random numbers

After this, we append checksum bits to the random number bits. Here’s the code to generate the bits:

`def getMSBChecksumBits(checksum: int, checksum_bit_count: int):`

`msb_checksum = checksum >> (256 - checksum_bit_count)`

`return msb_checksum`

`def getEntropyWithChecksum(random_number: int,`

`msb_checksum: int,`

`checksum_bit_count: int):`

`shifted_random_number = random_number << checksum_bit_count`

`entropy_check_i = shifted_random_number | msb_checksum`

`return entropy_check_i`

`def convertIntToBytes(num: int, bit_count: int):`

`size_bytes = math.ceil(bit_count / 8)`

`num_s = (‘%x’ % num).zfill(size_bytes * 2)`

`num_b = bytes.fromhex(num_s)`

`return num_b`

`def getChecksum(b: bytes):`

`return int.from_bytes(hashlib.sha256(b).digest(), byteorder=’big’)`

`def getEntropyCheckBits(mnemonic_length: int):`

`entropy_bit_count = getEntropyBitCount(mnemonic_length)`

`random_number_b = getRandomNumberBits(entropy_bit_count)`

`checksum_bit_count = getChecksumBitCount(mnemonic_length)`

`checksum = getChecksum(random_number_b)`

`msb_checksum = getMSBChecksumBits(checksum, checksum_bit_count)`

`random_number = int.from_bytes(random_number_b, byteorder=’big’)`

`entropy_check_i = getEntropyWithChecksum(random_number, msb_checksum, checksum_bit_count)`

`bit_count = entropy_bit_count + checksum_bit_count`

`entropy_check_b = convertIntToBytes(entropy_check_i, bit_count)`

`return entropy_check_b`

**Program 9.3:** Program to get entropy bits appended with checksum

After this, we need to use these bits to select words from the list of 2048 mnemonic word lists. This works by breaking the **entropycheck bits** into the 11-bit list. Given here is the code that does this:

`def getMnemonicWordList():`

`word_list = []`

`with open(‘mnemonic_word_list_english.txt’, ‘rt’) as word_file:`

`word_list = word_file.read().splitlines()`

`return word_list`

`def entropyCheckBits2List(entropy_check_b: bytes, size: int):`

`selector_int = int.from_bytes(entropy_check_b, byteorder=’big’)`

`selector_list = []`

`while size >= 11:`

`selector_list.append(selector_int & 0x07FF)`

`selector_int = selector_int >> 11`

`size -= 11`

`return selector_list[::-1]`

`def getMnemonicWordCodeString(mnemonic_length: int):`

`entropy_bit_count = getEntropyBitCount(mnemonic_length)`

`checksum_bit_count = getChecksumBitCount(mnemonic_length)`

`entropy_check_bit_count = entropy_bit_count + checksum_bit_count`

`entropy_check_b = getEntropyCheckBits(mnemonic_length)`

`selector_list = entropyCheckBits2List(entropy_check_b,`

`entropy_check_bit_count)`

`mnemonic_word_list = getMnemonicWordList()`

`word_key_list = []`

`for selector in selector_list:`

`word = mnemonic_word_list[selector]`

`word_key_list.append(word)`

`return word_key_list`

**Program 9.4:** Program to generate mnemonic word code in list

In this subtopic, you learned to generate the mnemonic seed. You can use it to generate a mnemonic seed of 12, 18, or 24 words. There is a tradeoff here: a 24-word seed gives more security, but it is more difficult to remember than a 12- or an 18-word code. In the next section, we will discuss private key, public key, and the address format used by Bitcoin.

# [Format and generation of private key, public key, and address](#toc.xhtml#s195a)

In this subtopic, you will understand the format of private keys and address and learn to generate them.

# [Private key](#toc.xhtml#s196a)

Private keys can be almost any 256-bit value. They can be between *0x1* to *0xFFFF FFFF FFFF FFFF FFFF FFFF FFFF FFFE BAAE DCE6 AF48 A03B BFD2 5E8C D036 4140*.

Private keys are represented in **Wallet Import Format (WIF)** format. This is the base58 format with a prefix and checksum.

Base58 scheme is defined in the following document:

**[https://tools.ietf.org/id/draft-msporny-base58-01.html](https://tools.ietf.org/id/draft-msporny-base58-01.html)**

Public keys can be compressed or uncompressed. Both compressed and uncompressed public keys lead to different addresses, so the private key must carry the information regarding whether the public key it will generate will be compressed or uncompressed. To generate WIF format for the private key, we need to have information about the coin, network, and compression in the WIF format so that the resulting address belongs to a specific network and is deterministic.

The following is the prefix information:

![](images/296.jpg)

**Table 9.1:** Private key prefixes

As seen in the preceding table, regtest uses the same private key prefixes as testnet.

To generate WIF format for the compressed public key, we add b’\\01’ as a suffix to the generated private key.

Base58 encoding string consists of the following characters:

*123456789ABCDEFGHJKLMNPQRSTUVWXYZabcdefghijkmnopqrstuvwxyz*

There are 58 characters as the name suggests. To get the encoded string, we iteratively divide the number by 58 and subsequent quotients, convert remainders to base58 characters in each step, and concatenate encoded characters to get the final encoded string.

The following illustration shows the logic to get WIF encoded private key for testnet:

![](images/Figure-9.2.jpg)

**Figure 9.2:** Illustration of method of WIF encoding

The following program encodes a number in base58 string:

`g_alphabet=’123456789ABCDEFGHJKLMNPQRSTUVWXYZabcdefghijkmnopqrstuvwxyz’`

`g_base_count = len(g_alphabet)`

`def hash256(bstr: bytes):`

`return hashlib.sha256(hashlib.sha256(bstr).digest()).digest()`

`def base58_encode(num: int):`

`encode = ‘’`

`if (num < 0):`

`return ‘’`

`while (num >= g_base_count):`

`mod = num % g_base_count`

`encode = g_alphabet[mod] + encode`

`num = num // g_base_count`

`if (num >= 0):`

`encode = g_alphabet[num] + encode`

`return encode`

**Program 9.5:** Program to encode number into base58 string

The following program postfix four bytes of checksum to the number before base58 encoding to generate base58check encoding:

`def base58checkEncode(prefix: bytes, b: bytes):`

`with_prefix = prefix + b`

`with_checksum = with_prefix + hash256(with_prefix)[0:4]`

`val = int.from_bytes(with_checksum, byteorder=’big’)`

`encode = base58_encode(val)`

`if prefix == b’\x00’:`

`encoded_prefix = base58_encode(0)`

`encode = encoded_prefix + encode`

`return encode`

**Program 9.6:** Program to encode a number into Base-58-Check-Encode

The following program converts private key hex code WIF format. It takes hex code of private key and a Boolean value stating if the key is supposed to be used to generate a compressed public key:

`PRIVKEY_PREFIX_MAINNET=0x80`

`WIF_PREFIX_MAINNET_COMPRESSED=[‘L’, ‘K’]`

`WIF_PREFIX_MAINNET_UNCOMPRESSED=[‘5’]`

`PRIVKEY_PREFIX_TESTNET=0xEF`

`WIF_PREFIX_TESTNET_COMPRESSED=[‘c’]`

`WIF_PREFIX_TESTNET_UNCOMPRESSED=[‘9’]`

`def encodeWifPrivkey(privkey: int, for_compressed_pubkey: bool):`

`prefix_b = bytes.fromhex(‘%02x’ % PRIVKEY_PREFIX_TESTNET)`

`privkey_b = bytes.fromhex(‘%064x’ % privkey)`

`if for_compressed_pubkey == True:`

`privkey_b = privkey_b + b’\01’`

`wif_encoded = base58checkEncode(prefix_b, privkey_b)`

`return wif_encoded`

**Program 9.7:** Method to generate WIF encoded private key

We call this method for compressed public key as follows:

`if __name__ == ‘__main__’:`

`h = 0x1f4b9c36e4f466464de890a341eba483eb3ed95932d797b0841afa1d8d83c420`

`wif = encodeWifPrivkey(h, True)`

`print(wif)`

We get the following:

![](images/Figure-9.3.jpg)

**Figure 9.3:** Shows the generated WIF encoded private key for compressed public key

We call it for uncompressed public key as follows:

`if __name__ == ‘__main__’:`

`h = 0x1f4b9c36e4f466464de890a341eba483eb3ed95932d797b0841afa1d8d83c420`

`wif = encodeWifPrivkey(h, False)`

`print(wif)`

We get the following:

![](images/Figure-9.4.jpg)

**Figure 9.4:** Shows the generate WIF encoded private key for uncompressed public key

# [Public key](#toc.xhtml#s197a)

A private key is normally represented in WIF encoding. We use the WIF encoded private key to generate the public key and address. To generate public key from WIF encoded private key, we need to convert the private key back to hex code. The reason why we use WIF encoded string and not hex code is the size. Private key is presented as a 64-digit hex code or 53-character string. So, using WIF encode means 11 digits less to type.

First, we decode the WIF string and, along with the decoded hex-coded private key, we also get whether it is for testnet or mainnet and whether it is for compressed public key or uncompressed public key. Here’s the code to decode the WIF string:

`def base58_decode(s: str):`

`decoded = 0`

`multi = 1`

`s = s[::-1]`

`for char in s:`

`decoded += multi * g_alphabet.index(char)`

`multi = multi * g_base_count`

`return decoded`

`def base58checkDecode(s: str):`

`with_checksum_int = base58_decode(s)`

`with_checksum_b = bytes.fromhex(‘%x’ % with_checksum_int)`

`decode_b = with_checksum_b[1:-4]`

`return decode_b`

`def base58checkVerify(wif: str):`

`decoded_wif = base58_decode(wif)`

`wif_str = ‘%02x’ % decoded_wif`

`if len(wif_str) % 2 == 1:`

`wif_str = ‘0’ + wif_str`

`postfix = bytes.fromhex(wif_str)[-4:]`

`wif_without_postfix = bytes.fromhex(wif_str)[0:-4]`

`h = hash256(wif_without_postfix)[0:4]`

`if h == postfix:`

`return True`

`return False`

`def getNetworkNCompression(wif_prefix: str):`

`if wif_prefix in WIF_PREFIX_MAINNET_COMPRESSED:`

`return ‘mainnet’, True`

`elif wif_prefix in WIF_PREFIX_MAINNET_UNCOMPRESSED:`

`return ‘mainnet’, False`

`elif wif_prefix in WIF_PREFIX_TESTNET_COMPRESSED:`

`return ‘testnet’, True`

`elif wif_prefix in WIF_PREFIX_TESTNET_UNCOMPRESSED:`

`return ‘testnet’, False`

`def privkeyWif2Hex(privkey_wif: str):`

`assert base58checkVerify(privkey_wif)`

`wif_prefix = privkey_wif[0:1]`

`network, compress = getNetworkNCompression(wif_prefix)`

`privkey_b = base58checkDecode(privkey_wif)`

`privkey_i = int.from_bytes(privkey_b, byteorder=’big’)`

`if compress == True:`

`privkey_s = ‘%066x’ % privkey_i`

`else:`

`privkey_s = ‘%064x’ % privkey_i`

`return privkey_s, network, compress`

**Program 9.8:** Program to encode private key into WIF encoding scheme

Bitcoin private key public key cryptography is based on **Elliptic Curve Digital Signature Algorithm (ECDSA)**. **Elliptic** c**urve** d**igital** s**ignature** a**lgorithm** uses e**lliptic** c**urve** c**ryptography**. As the name suggests, elliptic curve is a geometric representation of the following equation:

*y² = x³\+ ax + b*

Elliptic curve cryptography is based on an elliptic curve over a finite field, also called **Galois Fields**. Galois field can be a prime field or a binary field. Bitcoin uses a specific elliptic curve over a finite prime field called ***secp256k1***. Here’s the equation for *secp256k1*:

*y² = x² + ax + b*

Here

p = 2^(256) - 2^(32) - 2⁹ - 2⁸ - 2⁷ - 2⁶ - 2⁴\-1

p = 0xfffffffffffffffffffffffffffffffffffffffffffffffffffffffefffffc2f

There is also a variable called **Generation Point,** and its value is:

`G = (79BE667E F9DCBBAC 55A06295 CE870B07 029BFCDB 2DCE28D9 59F2815B 16F81798, 483ADA77 26A3C465 5DA4FBFC 0E1108A8 FD17B448 A6855419 9C47D08F FB10D4B8)`

We use the ecdsa package in Python to generate public keys from private key hex code. Once the WIF private key is decoded, we use the ecdsa *package.* The e*cdsa* package uses signing key to denote private key and verifying key to denote public key.

The following is the ecdsa package we use in the :

![](images/Figure-9.5.jpg)

**Figure 9.5:** The pip3 package information about installed ecdsa package

We also use cryptotools package for secp256k1 related operations. The following program converts WIF encoded private key to public key:

`from ecdsa import SigningKey, SECP256k1`

`def compressPubkey(pubkey: bytes):`

`x_b = pubkey[1:33]`

`y_b = pubkey[33:65]`

`if (y_b[31] & 0x01) == 0: # even`

`compressed_pubkey = b’\x02’ + x_b`

`else:`

`compressed_pubkey = b’\x03’ + x_b`

`return compressed_pubkey`

`def privkeyHex2pubkey(privkey_s: str, compress: bool):`

` if compress == True:`

`privkey_s = privkey_s[0:64]`

`privkey_b = bytes.fromhex(privkey_s)`

`sk = SigningKey.from_string(privkey_b, curve=SECP256k1)`

`vk = sk.get_verifying_key()`

`pubkey_b = b’\x04’ + vk.to_string()`

`if compress == True:`

`pubkey_b = compressPubkey(pubkey_b)`

`return pubkey_b`

`def privkeyWif2pubkey(privkey: str):`

`privkey_s, network, compress = privkeyWif2Hex(privkey)`

`pubkey = privkeyHex2pubkey(privkey_s, compress)`

`return pubkey`

**Program 9.9:** Program to get public key from WIF encoded private key

In the preceding code, b’\\x04’ is a prefix in the uncompressed public key, and b’\\x02’ and n’\\x03’ are used as a prefix in the compressed public key.

We call the preceding program by executing the following code:

`if __name__ == ‘__main__’:`

`privkey_wif = ‘cNdY2QGfetwijtrqzCK5tAoc78NtGkQJ8smYVaugDW6puLXJvLZG’`

`print(‘privkey(WIF) = ‘, privkey_wif)`

`privkey_s, network, compress = privkeyWif2Hex(privkey_wif)`

`pubkey_b = privkeyWif2pubkey(privkey_wif)`

`print(‘pubkey = %s’ % pubkey_b.hex())`

`print(‘-----------------------------------------------------------’)`

`privkey_wif = ‘91phZVP8Q5yMLEZbD41vfnGYWwEZuxbjQ5huSxiPUkkTiQw8SL2’`

`print(‘privkey(WIF) = ‘, privkey_wif)`

`privkey_s, network, compress = privkeyWif2Hex(privkey_wif)`

`pubkey_b = privkeyWif2pubkey(privkey_wif)`

`print(‘pubkey = %s’ % pubkey_b.hex())`

And we get the following public keys:

![](images/Figure-9.6.jpg)

**Figure 9.6:** Shows public key generated from WIF enconded private keys

# [Address](#toc.xhtml#s198a)

When a merchant or a trader requests bitcoins against their service or product, they provide their Bitcoin address. We transfer the requested bitcoins to their address, and save any change left to a different address. In this subtopic, we will understand and generate addresses from the public key.

The following illustration shows how public-key-hash address is generated:

![](images/Figure-9.7.jpg)

**Figure 9.7:** Illustration of Address Generation mechanism

The public key to address conversion is a two-step process. In the first step, we calculate the hash of the public key, which is ***PKH*** or **public-key-hash**. In the second step, we encode PKH with the base58check algorithm. One important benefit of using checksum is that it is almost impossible to make a typing mistake and still generate a valid address. This is an important safety feature of Bitcoin. Mnemonic code also uses the base58check algorithm, and it provides the same benefit. Putting wrong order, or a wrong or repeated word will almost never lead to loss of funds.

Using hash160 and address instead of the public key provides enhanced security. If, in the future, quantum computers can translate public key to private key, then hashing public key will be still secure. So, unless we have exposed our public key, our bitcoins will be still secure. And this is significant as the breakdown of public key private key encryption will lead to mayhem for almost everything on the internet.

It is possible to have a script instead of a public key. In that case, the public key is replaced by the script in the preceding figure. The public key address is called **Pay-to-Public-Key-Hash** or **P2PKH** address, and the script address is called **Pay-to-Script-Hash** or **P2SH** address.

The following table lists the version prefixes related to network and address type:

![](images/306.jpg)

**Table 9.2:** Table for address prefixes

In the preceding table, we can see that `testnet` *and* `regtest` use the same version prefix.

The following program converts public key to address:

`PKH_MAINNET_PREFIX = 0x00`

`SH_MAINNET_PREFIX = 0x05`

`PKH_TESTNET_PREFIX = 0x6F`

`SH_TESTNET_PREFIX = 0xC4`

`PKH_REGTEST_PREFIX = 0x6F`

`SH_REGTEST_PREFIX = 0xC4`

`def hash160(secret: bytes):`

`secrethash = hashlib.sha256(secret).digest()`

`h = hashlib.new(‘ripemd160’)`

`h.update(secrethash)`

`secret_hash160 = h.digest()`

`return secret_hash160`

`def pkh2address(pkh: bytes):`

`prefix = PKH_TESTNET_PREFIX`

`address = base58checkEncode(bytes.fromhex(‘%02x’ % prefix), pkh)`

`return address`

`def sh2address(sh: bytes):`

`prefix = SH_TESTNET_PREFIX`

`address = base58checkEncode(bytes.fromhex(‘%02x’ % prefix), pkh)`

`return address`

`def pubkey2address(pubkey: bytes):`

`pkh = hash160(pubkey)`

`address = pkh2address(pkh)`

`return address`

**Program 9.10:** Program to convert public key into addresses

We call the preceding method using the following program to get address from compressed as well as uncompressed public keys:

`if __name__ == ‘__main__’:`

`pubkey = ‘0240bb63da114aa89f4d2cf35d695d3e52e6add7a4bae06f190d947bef5c62b5e0’`

`pubkey_b = bytes.fromhex(pubkey)`

`print(‘Compressed PubKey = ‘, pubkey_b.hex())`

`address = pubkey2address(pubkey_b)`

`print(‘Address = ‘, address)`

`print(‘-----------------------------------------------’)`

`pubkey = ‘0440bb63da114aa89f4d2cf35d695d3e52e6add7a4bae06f190d947bef5c62b5e0e99601851593a9e54e2059a25d76512698acf60089935dedc015f1bb2bc81eda’`

`pubkey_b = bytes.fromhex(pubkey)`

`print(‘Uncompressed PubKey = ‘, pubkey_b.hex())`

`address = pubkey2address(pubkey_b)`

`print(‘Address = ‘, address)`

And we get the following result:

![](images/Figure-9.8.jpg)

**Figure 9.8:** Shows addresses generated from public keys

# [Hierarchical Deterministic (HD) wallet](#toc.xhtml#s199a)

In the earlier version, a wallet used to be a collection of private key public key pairs stored in a file. The file was required to be backed up multiple times and secured at multiple places. This was cumbersome and has led to the loss of coins for many in the initial years. However, there was one advantage: since these are not generated from a single seed, accidentally exposing the secret will not lead to loss of all the coins in the derived addresses. These were non-deterministic wallets.

The alternative to this is deterministic wallets, which are generated using a single seed and an index. Hierarchical deterministic wallets require a string representing the hierarchical location of keys instead of the index value. This allows the generation of a very large number of keys from a single seed. Additionally, it provides a way to group addresses for different purposes by selecting a different hierarchical location in the hierarchy.

Hierarchical deterministic wallet uses 12-, 18- or 24-word mnemonic code, which makes it easier to remember seed and at the same time, provides similar security as any complex password. It is easier to remember and type 12 words. This is useful if the wallet requires typing them every time or you don’t want to write on paper. A 24-word code is more secure and recommended in most cases.

Using the deterministic wallet as defined in BIP32 makes it easier to generate the private key and public key pair or just public keys whenever required. This eliminates the need for the physical form of a wallet. So, while we are traveling and spending or trading, we can generate addresses and private keys as we require. There is still a risk that we can accidentally expose mnemonic code and lose all our savings, but if we always generate keys or addresses offline, we can almost remove this risk. There are specialized devices called hardware wallets that do just that and so, are considered the best way to store bitcoins.

The following figure illustrates the keys generation using mnemonic code word list using BIP32 specification for hierarchical deterministic wallet:

![](images/Figure-9.9.jpg)

**Figure 9.9:** Illustration of key generation using Mnemonic Code Word List

BIP32 specification uses the pbkdf2-hmac algorithm to generate private keys. **pbkdf2** stands for **Password-Based Key Derivation Function 2**. pbkdf2 requires hashing algorithm as an input. We use SHA512 as the hashing algorithm required by pbkdf2. Additionally, pbkdf2 is an iterative process of key derivation; the higher the number of iterations, the more secure is the derived key against brute force attacks, but a higher number also takes a long time to generate. If we generate a sufficiently large number of private key public key pairs once so that we don’t require to run the program again and again, we can have a much higher iteration count. Bitcoin Core does this and generates 100 private keys, public keys, and addresses in the first run. Once the keys and addresses are generated, wallet file is like a JBOK for the user. It is recommended that the iteration count should be more than 10,000. Bitcoin Core uses 25,000 iterations, but there are quite popular wallets that use an iteration count of just 2048, which probably means 2048 must be ok if we don’t want to create a JBOK wallet file and use it efficiently. We will use 10,000 to balance both time and security.

The following figure shows how the seed is generated:

![](images/Figure-9.10.jpg)

**Figure 9.10:** Illustration of the mechanism of generation of seed from Mnemonic Code word list

To do this in Python code, we require hmac and pbkdf2 packages. We use the pbkdf2 source from the following source code:

**[https://github.com/sfstpala/python3-pbkdf2](https://github.com/sfstpala/python3-pbkdf2)**

We also need to use following package for secp256k1 elliptic curve cryptography:

![](images/Figure-9.11.jpg)

**Figure 9.11:** The pip3 package information about installed cryptotools package

The following code generates seed from the mnemonic code word list:

`import pbkdf2`

`import hashlib`

`import hmac`

`import struct`

`from cryptotools.ECDSA.secp256k1 import PublicKey, \`

`PrivateKey, Point, G as secp256k1_G, \`

`N as secp256k1_n, CURVE`

`iterations_g = 10000`

`dklen_g = 64 # derived key length`

`def genSeedFromStr(password: str, salt: str):`

`password_b = password.encode(‘utf-8’)`

`salt_b = salt.encode(‘utf-8’)`

`seed = pbkdf2.pbkdf2(hashlib.sha512, password_b, salt_b, iterations_g, dklen_g)`

`return seed`

**Program 9.11:** Program to generate seed from Mnemonic Code word list and salt string

We passed a mnemonic code word list and a passcode to the seed generation method, as follows:

`if __name__ == ‘__main__’:`

`mnemonic_code_l = [‘moral’, ‘submit’, ‘comfort’, ‘cupboard’, ‘organ’,`

`‘expand’, ‘home’, ‘bid’, ‘dawn’, ‘ozone’, ‘omit’, ‘helmet’]`

`mnemonic_code = ‘ ‘.join(mnemonic_code_l)`

`print(‘Mnemonic Code = ‘, mnemonic_code)`

`seed = genSeedFromStr(mnemonic_code, ‘mnemonic’ + ‘mycomplexpasscode’)`

`print(‘seed = %s’ % seed.hex())`

And we get 512-bit seed as a result:

![](images/Figure-9.12.jpg)

**Figure 9.12:** Shows the seed and mnemonic code generated from the program

Once the seed is derived from mnemonic code using pbkdf2, we use the key to generate the master key pair and then further children’s key pairs. We use the HMAC code to generate these keys. HMAC stands for **Hash-based Message Authentication Code**.

# HMAC : Hash-based message authentication code

Following figure illustrates hash-based message authentication:

![](images/Figure-9.13.jpg)

**Figure 9.13:** Illustration of HMAC-based authentication mechanism

Bob shares secret with Alice, so Bob and Alice only know the secret. Bob needs to send a message (m) to Alice. He uses the HMAC-SHA512 hashing algorithm to generate hash (h) and sends it to Alice along with the message. When Alice receives the message, she again generates hash using same HMAC-SHA512 algorithm. If calculated hash is the same as received hash, she is sure that the message has not been tampered with.

We use the HMAC-SHA512 algorithm for the generation of master key pairs and subsequent children’s key pairs.

# [Master key generation](#toc.xhtml#s200a)

The following figure illustrates master private key generation and master chaincode generation, which will be required to generate children at the next level in the hierarchy of key pairs:

![](images/Figure-9.14.jpg)

**Figure 9.14:** Illustration of generation of master key address from seed bytes

Here’s the program:

`def genMasterKeys(seed: bytes):`

`h = hmac.new(bytes(“Bitcoin seed”, ‘utf-8’),`

`seed,`

`hashlib.sha512).digest()`

`private_key = int.from_bytes((h[0:32]), byteorder=’big’)`

`chaincode = h[32:64]`

`return private_key, chaincode`

**Program 9.12:** Program to generate master private key and Chaincode pair

We call this method as follows:

`privkey, chaincode = genMasterKeys(seed)`

`privkey_s = ‘%064x’ % privkey`

`print(‘master privkey = %s’ % privkey_s)`

`print(‘master chaincode = %s’ % chaincode.hex())`

This generates the following master private key and chaincode:

![](images/Figure-9.15.jpg)

**Figure 9.15:** Shows master private key and master chaincode generated from the program

# [Key derivation](#toc.xhtml#s201a)

# [Parent private key -> Child private key](#toc.xhtml#s202a)

Each key pair at a tree location can generate children’s key pairs. For the first children, we have the following child private key derivation mechanisms:

![](images/Figure-9.16.jpg)

**Figure 9.16:** Illustration of child private key derivation mechanism

To derive child private key and child chaincode, we need parent private key, parent public key, parent chaincode, and index of the child to be derived. This method is used to derive child from index 0 to 2^(31) - 1.

The following code implements the child key derivation procedure:

`def finiteFieldAddition(a: int, b: int, modulo: int):`

`return (a + b) % modulo`

`def genNormalChildPrivKey(privkey: int, chaincode: bytes, index: int):`

`privkey_s = ‘%064x’ % privkey`

`pubkey_b = privkeyHex2pubkey(privkey_s, True)`

`index_b = struct.pack(‘>L’, index)`

`h = hmac.new(chaincode, pubkey_b + index_b, hashlib.sha512).digest()`

`h256 = int.from_bytes(h[0:32], byteorder=’big’)`

`child_privkey = finiteFieldAddition(h256, privkey, secp256k1_n)`

`child_chaincode = h[32:64]`

`return child_privkey, child_chaincode`

**Program 9.13:** Program to generate child’s private key and chaincode from parent’s private key and chaincode

The preceding code is run as follows:

`child_privkey_i, child_chaincode = genNormalChildPrivKey(privkey, chaincode, 1)`

`child_privkey_wif = encodeWifPrivkey(child_privkey_i, True)`

`print(“child privkey = %s” % child_privkey_wif)`

`print(“child chaincode = %s” % child_chaincode.hex())`

It gives us the following results:

![](images/Figure-9.17.jpg)

**Figure 9.17:** Shows child private key and child chaincode generated from the program

# [Parent public key -> Child public key](#toc.xhtml#s203a)

One of the important reasons why BIP32 is so useful is that we can derive child public keys and addresses without knowing parent private keys. This protects against accidentally exposing private keys; therefore, private keys for all the subsequent children.

This is based on the following logic:

*P[p]: Parent Private Key*

*U[p]: Parent Public Key*

*P[C]: Child Private Key*

*U[C]: Child Public Key*

*H[0-31]: 32 MSB of hmac(sha512) hash obtained from parent chaincode,public key and child index*

*G: Generation point in finite field elliptic curve*

As we learned in child private key derivation:

⇒ *P[P]+H[0-31] = P[C] (1)*

Multiplying both sides by generation point G:

*P[P] G + H[0-31] G = P[C].G*

In the elliptic curve cryptography public key is derived as follows:

⇒*U[x] = P[x].G (2)*

*(1), (2)* ⇒ *U[P] + H[0-31] .G = U[C]*

G is a vector on the x, y coordinate in the finite field. Multiplying G with scalar hash requires elliptic curve finite field point multiplication, and addition of and requires elliptic curve finite field point addition. Plus, if the public key we are using is compressed, then we will require an un-compression algorithm using elliptic curve cryptography.

The following figure illustrates this:

![](images/Figure-9.18.jpg)

**Figure 9.18:** Illustration of the derivation of child public key from parent public key and chaincode

The following Python implementation generates child public key from parent public key:

`G_p = Point(secp256k1_G[0], secp256k1_G[1])`

`def compressPubkey(pubkey_b: bytes):`

`pubkey_P = PublicKey.decode(pubkey_b)`

`pubkey_b = PublicKey.encode(pubkey_P, compressed=True)`

` return pubkey_b`

`def genNormalChildPubKey(pubkey_b: bytes, chaincode: bytes, index: int):`

`index_b = struct.pack(‘>L’, index)`

`h = hmac.new(chaincode, pubkey_b + index_b, hashlib.sha512).digest()`

`h256 = int.from_bytes(h[0:32], byteorder=’big’)`

`h256G = CURVE.point_mul(G_p, h256)`

`pubkey_b = compressPubkey(pubkey_b)`

`pubkey_point = Point.from_compact(pubkey_b[1:])`

`child_pubkey_point = h256G + pubkey_point`

`child_pubkey_b = PublicKey.encode(child_pubkey_point, compressed=True)`

`child_chaincode = h[32:64]`

`return child_pubkey_b, child_chaincode`

**Program 9.14:** Program to derive child public key and chaincode from parent public key and chaincode

We call the preceding code as follows:

`pubkey_b = privkeyHex2pubkey(privkey_s, True)`

`child_pubkey_b, child_chaincode = genNormalChildPubKey(pubkey_b,`

`chaincode, 1)`

`print(“child pubkey key = %s” % child_pubkey_b.hex())`

`print(“child chaincode = %s”% child_chaincode.hex())`

This gives us the following result:

![](images/Figure-9.19.jpg)

**Figure 9.19:** Shows the generated child public key and chaincode

We can see that the child chaincode derived with the private key is the same as the chaincode derived with the public key.

# [Child private key -> Parent private key (Wallet private key leak)](#toc.xhtml#s204a)

There exists a risk when we use xpub. If we accidentally expose a child’s private key to an attacker who has access to the xpub of the parent, they can find all the private keys in the wallet and drain all the stored bitcoins.

The following equation explains how this happens:

*P[p] + H[0-31] = P[C]*

⇒ *P[C] - H\_[0-31] =P[P]*

This shows that by knowing the HMAC-SHA256 hash and private key of the child, we can get the private key of the parent. And since we got the parent’s private key, we can get the private key of the parent’s parent by the same mechanism. Additionally, once the parent private key is known, we can derive the private keys of all its children. This means just by losing one private key and the corresponding xpub of the parent, the whole wallet can be drained of bitcoins.

The following figure illustrates the stages of exposure:

![](images/Figure-9.20.jpg)

**Figure 9.20:** Illustration of an attacker deriving all the private keys using a single private key

When someone has got hold of your private key, they can derive more and more private keys from it, and finally, reach the master key and derive all keys, as we have done with the private key derivation.

The following program derives the private key of parent from child private key:

`def genNormalParentPrivKey(child_privkey_i: int,`

`pubkey_b: bytes,`

`chaincode: bytes,`

`index: int):`

`index_b = struct.pack(‘>L’, index)`

`h = hmac.new(chaincode, pubkey_b + index_b, hashlib.sha512).digest()`

`h256 = int.from_bytes(h[0:32], byteorder=’big’)`

`privkey = finiteFieldAddition(-h256, child_privkey_i, secp256k1_n)`

`return privkey`

**Program 9.15:** Program to derive Parent Private Key from Child Private Key

We call the preceding code as follows:

`p_privkey_i = genNormalParentPrivKey(child_privkey_i,`

`pubkey_b, chaincode, 1)`

`p_privkey_wif = encodeWifPrivkey(p_privkey_i, True)`

`print(‘parent privkey = %064x’ % p_privkey_i)`

This gives us the following result:

![](images/Figure-9.21.jpg)

**Figure 9.21:** Shows parent private key obtained using child private key, public key and chaincode

We can see here that we derived the same master private key that we had got from the seed.

# [Deriving hardened child keys](#toc.xhtml#s205a)

In the previous sections, you learned normal key derivation, and you also learned that we could lose all bitcoin stored in the wallet by an easy-to-make mistake. To avoid this, BIP32 also suggests a modification to child derivation algorithms called hardened derivation.

The following figure illustrates the procedure of hardened derivation:

![](images/Figure-9.22.jpg)

**Figure 9.22:** Illustration of the derivation of Child Private Key from Hardened Parent Private Key

We see here that in hardened derivation, parent private key is used with byte 0x00 as suffix to it instead of parent public key. The child index for hardened derivation is from 2^31 to 2^32-1:

`def genHardenedChildPrivKey(privkey: int, chaincode: bytes, index: int):`

`index_b = struct.pack(‘>L’, index)`

`privkey_b = bytes.fromhex(‘%064x’ % privkey)`

`h = hmac.new(chaincode, b’\x00’ + privkey_b + index_b, hashlib.sha512).digest()`

`h256 = int.from_bytes(h[0:32], byteorder=’big’)`

`child_privkey = finiteFieldAddition(h256, privkey, secp256k1_n)`

`child_chaincode = h[32:64]`

`return child_privkey, child_chaincode`

**Program 9.16:** Program to derive child private key from hardened parent private key

We call the preceding code as follows:

`index = ((1<<31) + 1) # 2^31 + 1`

`child_privkey_i, child_chaincode = genHardenedChildPrivKey(privkey, chaincode, index)`

`child_privkey_wif = encodeWifPrivkey(child_privkey_i, True)`

`print(“child privkey = %s” % child_privkey_wif)`

`print(“child chaincode = %s” % child_chaincode.hex())`

We get the following result:

![](images/Figure-9.23.jpg)

**Figure 9.23:** Shows hardened child private key and chaincode

Unlike normal, child hardened children derivation does not support xpub or extended public keys. Consequently, to watch child addresses, we cannot use xpub; instead, we need to generate public keys and addresses offline and then pass them to the online wallet to watch them. This is a bit inconvenient compared to normal derivation, but as this is much more secure, it is recommended over normal derivation. In the next section, we will see how we can combine both to have a better tradeoff between security and convenience.

# [Extended keys](#toc.xhtml#s206a)

BIP32 also describes xpub and xprv for mainnet and tpub and tprv for testnet. These are used by wallets to generate child keys and addresses. The xpub and tpub are used to generate only public keys, while xprv and tprv are used to generate private keys. The generated xpub or tpub can be given to the wallet to watch generated addresses without exposing private keys or seeds. The generated xprv or tprv can be given to the wallet to generate private keys. This makes HD Wallets convenient to use, and that is the reason BIP32 specification is used by almost all wallet software today, like Bitcoin Core, electrum, and hard wallets like nano or trezor.

The following illustration shows xprv derivation:

![](images/Figure-9.24.jpg)

**Figure 9.24:** Illustration of the derivation of extended private key

The following illustration shows xpub derivation:

![](images/Figure-9.25.jpg)

**Figure 9.25:** Illustration of the derivation of extended public key

For the Master xpub and xprv, depth is zero and parent fingerprint is 4-byte of zeroes.

# [Master extended public and private keys](#toc.xhtml#s207a)

Master is the root of all keys, and knowing its xpub key will allow generating all subsequent keys. You should never have any reason to generate xpub or xprv for root. However, in this section, you learn to generate xpub and xprv.

The following code prepares master xpub and xprv:

`XPUB_VERSION = ‘0488B21E’`

`XPRV_VERSION = ‘0488ADE4’`

`TPUB_VERSION = ‘043587CF’`

`TPRV_VERSION = ‘04358394’`

`def getMasterXPrv(chaincode_b: bytes, privkey: int):`

`version_b = bytes.fromhex(TPRV_VERSION)`

`depth_b = b’\x00’`

`fingerprint_p_b = bytes(4)`

`index_b = bytes(4)`

`privkey_b = bytes.fromhex(‘%066x’ % privkey)`

`raw_xprv = depth_b + fingerprint_p_b + index_b + chaincode_b + privkey_b`

`xprv = base58checkEncode(version_b, raw_xprv)`

`return xprv`

`def getMasterXPub(chaincode_b: bytes, pubkey: str):`

`version_b = bytes.fromhex(TPUB_VERSION)`

`depth_b = b’\x00’`

`fingerprint_p_b = bytes(4)`

`index_b = bytes(4)`

`pubkey_b = bytes.fromhex(pubkey)`

`raw_xpub = depth_b + fingerprint_p_b + index_b + chaincode_b + pubkey_b`

`xpub = base58checkEncode(version_b, raw_xpub)`

`return xpub`

**Program 9.17:** Program to derive master XPrv and master XPub

We call the method as follows:

`xprv = getMasterXPrv(chaincode, privkey)`

`print(‘xprv=%s’ % xprv)`

`pubkey_b = privkeyHex2pubkey(privkey_s, True)`

`xpub = getMasterXPub(chaincode, pubkey_b.hex())`

`print(‘xprv=%s’ % xpub)`

We get the following master xpub and xprv:

![](images/Figure-9.26.jpg)

**Figure 9.26:** Shows xprv and xpub for master

# [Extended public and private keys](#toc.xhtml#s208a)

We can generate xpub and xprv for a depth and index in the key derivation hierarchy if we have the key and chaincode of the root.

In the following code, we generate xprv and xpub for a given depth and index:

`def getXPrv(p_pubkey: str,`

`chaincode_b: bytes,`

`privkey: int,`

`depth: int,`

`index: int):`

`version_b = bytes.fromhex(TPRV_VERSION)`

`p_pubkey_b = bytes.fromhex(p_pubkey)`

`privkey_b = bytes.fromhex(‘%066x’ % privkey)`

`depth_b = bytes([depth])`

`p_fingerprint_b = hash160(p_pubkey_b)[0:4]`

`index_b = struct.pack(‘>L’, index)`

`raw_xprv = depth_b + p_fingerprint_b + index_b + chaincode_b + privkey_b`

`xprv = base58checkEncode(version_b, raw_xprv)`

`return xprv`

`def getXPub(p_pubkey: str,`

`chaincode_b: bytes,`

`pubkey: str,`

`depth: int,`

`index: int):`

`version_b = bytes.fromhex(TPUB_VERSION)`

`p_pubkey_b = bytes.fromhex(p_pubkey)`

`pubkey_b = bytes.fromhex(pubkey)`

`depth_b = bytes([depth])`

`p_fingerprint_b = hash160(p_pubkey_b)[0:4]`

`index_b = struct.pack(‘>L’, index)`

`raw_xpub = depth_b + p_fingerprint_b + index_b + chaincode_b + pubkey_b`

`xpub = base58checkEncode(version_b, raw_xpub)`

`return xpub`

**Program 9.18:** Program to generate XPub and XPrv for a given depth and index

We call the method as follows:

`# We are calculating for index=1 and depth=1`

`child_xprv = getXPrv(pubkey_b.hex(), child_chaincode, child_privkey_i, 1, 1)`

`print(‘child xprv:’)`

`print(child_xprv)`

`child_xpub = getXPub(pubkey_b.hex(), child_chaincode, child_pubkey_b.hex(),1, 1)`

`print(‘child xpub:’)`

`print(child_xpub)`

We get the following xprv and xpub for the given keys:

![](images/Figure-9.27.jpg)

**Figure 9.27:** Shows child xprv and child xpub

We can register xpub with wallets in order to watch transactions in which the generated addresses are involved. BitcoinJ is one of the wallets that accepts xpub for watching addresses. The generated xprv can be used to generate child private key public key pairs for signing transactions. You should never expose or use xprv anywhere and even avoid using xpub. Always generate those addresses privately and register individual addresses with wallets to watch. This will protect against the risk of losing bitcoins.

# [Key derivation path](#toc.xhtml#s209a)

As we know now, the beauty of a hierarchical deterministic wallet is that we can derive keys at any depth and any index deterministically. To be able to locate a key on a hierarchy, HD wallets use a notation called key derivation path.

Here’s the notation for the key derivation path:

*   The master key is denoted by m.
*   The normal key is denoted by the index number 0 to 2^(31)\-1.
*   The hardened key is denoted by the index numbers 2^(31) to 2^(32)\-1.
*   The depth separator is forward slash /.

As an example, key derivation path could be as follows:

*m/45/78’/56/9’*

Here, 78’ and 9’ are hardened keys, and 45 and 56 are normal keys.

The following illustration shows key derivation including hardened keys:

![](images/Figure-9.28.jpg)

**Figure 9.28:** Key derivation with hardened keys

In the previous section, you learned that hardened keys are more secure but also less convenient to use.

**Tip: To reduce the risk, we can have bottom level as normal derivations, which means xpub will help generate child indexes. However, we will also have parent as hardened, so if one child private key is exposed, it will expose the keys of other children of the same parent. But since the parent is hardened, it will not allow derivation of private keys of other indexes at the parent’s depth. We can keep the number of children under one parent limited to a small number like 20. So, on each exposure of private key, we lose 20 addresses. We can further keep only limited bitcoins in each address so that losing them is not a large loss.**

**This may be a convenient compromise, but it is not a good option for Bitcoin, as Bitcoin is a high-value and high-network-fee cryptocurrency. This means storing in very small quantities is quite costly and losing even small denominations is a significant loss. In short, Bitcoin is not suitable for smaller transactions, trading, and having lower security. This strategy might work for other cryptocurrencies where network fees are not high.**

# [Conclusion](#toc.xhtml#s210a)

In this chapter, you started by learning about the need for a wallet. You then learned the different ways we can classify wallets and focused on implementing a hierarchical deterministic wallet based on the BIP32 specification. In the process of implementation, you learned about private key generation and structure. You learned to derive public key and address and generate P2PKH and P2PSH addresses for `mainnet` *and* `testnet`. You also learned to generate easy-to-remember, save, and write passwords called mnemonic code word lists. You used the mnemonic code to generate private keys deterministically by using the derivation path. In this chapter, we also discussed how to deal with security and convenience. We did not discuss elliptic curve cryptography as we will look at it in more detail in the upcoming chapters.

In the next chapter, you will learn to create the most widely used transaction types. You will learn to sign the transactions and validate a received transaction. The validation process will involve looking at the mempool and utxos stored in the LevelDB database.

# [Points to remember](#toc.xhtml#s211a)

*   A wallet is a software program that stores the private key, public key, and addresses or has the ability to generate them on request.
*   A wallet can tell the number of bitcoins a person is holding, and it can also sign a transaction before publishing it on the network.
*   The mnemonic code word list can be 12/18/24 words. It is easier to remember and type 12 words, but a 24-word code is more secure.
*   To generate a secure mnemonic code, we need to generate a good random number. To generate a good random number, we need to find the right source of entropy.
*   Pbkdf2 is an iterative process of key derivation, the higher is the number of iterations, the more secure is the derived key against brute force attacks.
*   The recommended number of Pbkdf2 iterations is greater than 10000, but the higher the number, the more is the time taken to generate it.
*   Extended Keys provide an encoding method, which, if supported, can allow the wallet to generate the required private keys or public keys using given extended keys.
*   BIP32 HD wallets supports the derivation of Normal Keys and Hardened Keys.
*   If the private key of any of the child is exposed along with xpub, then someone can drain bitcoins stored in all the addresses of the wallet.
*   Hardened keys do not allow the use of xpub, and losing one private key will not expose any other address.

# [Questions](#toc.xhtml#s212a)

1.  Why are hardware wallets considered the safest way to store coins?
2.  What are the three functions of a wallet program?
3.  What are the pros and cons of using deterministic wallets?
4.  What are the benefits of using a mnemonic code word list?
5.  Explain the use of extended keys.
6.  Programming Questions: 
    1.  BIP44 is based on BIP32 HD wallet that specifies derivation path for generating keys based on the following derivation path:
        
        m / purpose’ / coin\_type’ / account’ / change / address\_index
        
        purpose = 44’
        
        cointype = 0’ for Bitcoin m*ainnet*
        
        account: identifier for the user account (Hardened)
        
        change = 0 (Normal) is for external address and 1 is for internal (change) address
        
        address\_index: Addresses are from index 0 (Normal) and upwards in sequence.
        
        Write a program to implement HD wallet for BIP44.
        
    2.  Write a program to generate 100 child addresses from given xpub.
    3.  Write a program to parse xprv and xpub.
7.  True/False: 
    1.  Hardened derivation makes it harder to derive a child private key from the parent private key.
    2.  Base58Check encoding protects the sender from typing the wrong address and consequently, paying to the wrong address.
    3.  If I accidentally write a mnemonic code word list in the wrong sequence, I will always generate the wrong keys and the wrong address.
8.  Fill in the blanks: 
    1.  A 24-word mnemonic code consists of \_\_\_\_-bit random number and \_\_\_-bit as its checksum.
    2.  The maximum possible depth of the BIP32 HD wallet key is \_\_\_\_\_\_.
    3.  The full form of P2PSH is \_\_\_\_\_\_\_\_\_\_\_ and that of P2PKH is \_\_\_\_\_\_\_\_\_\_\_\_.

# [CHAPTER 10](#toc.xhtml#c10)

# [Create and Validate Transactions](#toc.xhtml#c10)

In the previous chapter, you learned about Wallets, Private Keys, Public Keys, and Addresses and understood how to generate them. You learned to create a Hierarchical Deterministic wallet and understood how HD wallets simplify the generation of private keys, public keys, and addresses, and help us secure our wallets and simplify the management of our privacy.

The most fundamental reason why Bitcoin exists is to transfer and store value. This means when you pay bitcoin to another person, bitcoin have to move from your wallet to the other person’s wallet. And if you don’t transfer bitcoin from your wallet to another person’s wallet, it has to sit in your wallet as long as you want. Additionally, when the other person receives bitcoin, they should be able to send a portion of it to yet another person or add additional bitcoin while sending.

We transfer bitcoin by creating transactions and publishing them to the network. Even though we create transactions to pay to the other person, the transaction is not just known to us; it is known to everyone on the network. It’s like making a payment and then shouting so that everyone knows that the transaction is done. So, everyone on the network is a witness to the transaction.

In this chapter, our focus will be on transactions. We will parse a real transaction in a block and learn about its format and scripting language and verify the signature. We will then build our own transaction and publish it over the network. We will also look at common transaction types and ways to secure them.

# [Structure](#toc.xhtml#s213a)

In this chapter, we will cover the following topics:

*   Scripting Bitcoin transactions 
    *   OPCODES
    *   Signature verification 
        *   Hash type – SIGHASH\_ALL
        *   Hash type – SIGHASH\_NONE, SIGHASH\_SINGLE, SIGHASH\_ANYONECANPAY
        *   Standard Bitcoin script – P2PK
        *   Standard Bitcoin script – P2PKH
            
            ![](images/ent.jpg)Prepare signature preimage
            
        *   Standard Bitcoin script – P2MS
        *   Standard Bitcoin script – P2SH
*   Building transactions 
    *   Building P2PKH transaction
    *   Building P2SH transaction

# [Objectives](#toc.xhtml#s214a)

The objective of this chapter is to help readers learn to verify and create a transaction. In this chapter, you will learn about the scripting language used by the blockchain to fund a transaction and secure the fund at the destination address. You will also learn how a transaction is verified by a node. You will then learn to create a transaction and publish it over the Bitcoin network.

You will learn how the Bitcoin script gets executed, and you will also learn about the most used scripts and understand them in detail, both in transaction verification and transaction creation.

# [Scripting Bitcoin transactions](#toc.xhtml#s215a)

Bitcoin transactions have two sections: inputs and outputs. Input consists of unlocking script called `scriptSig`, and output consists of a locking script called `scriptPubKey`. Script `scriptSig` normally consists of signature required to unlock previously locked transaction and public-key or script to allow verification of the signature. Script `scriptPubKey` is based on the name of an earlier script called *P2PK* or *Pay-2-Pubkey*. Now, the *P2PK* script is not recommended and is rarely used. So, `scriptPubKey` is a misnomer now. Currently, *P2PKH, P2SH, P2SH-P2WPKH*, and *P2SH-P2WSH* are the most used scripts. Here, *W* denotes witness, which was introduced as part of s*egregated* w*itness* enhancement. We have a separate chapter to cover it in detail, so we will not cover s*egregated* w*itness* in this chapter.

To verify the script portion of a transaction, `scriptSig` is executed first, and then `scriptPubKey` is executed in sequence. The script language is a stack-based reverse polish language. Language semantics is like reverse polish notation.

# [Reverse Polish notation](#toc.xhtml#s216a)

Reverse polish notation is also called *post fix notation*. The following is an example of reverse polish notation:

7+ 9 in reverse polish notation is 7 9 +

To solve this, 7 and 9 go into the stack, and + is the operator to perform the operation:

![](images/Figure-10.1.jpg)

**Figure 10.1:** Reverse Polish notation operation execution

When we create a new transaction, we utilize UTXOs to fund the transaction. Inputs of the new transaction contain an unlocking script that is required to release funds locked by the `scriptPubKey` in the UTXOs. Once both scripts are executed, a Boolean value is left on the top of the stack, which denotes whether the script finally succeeded. These scripts are executed just like reverse polish notation.

# [OPCODES](#toc.xhtml#s217a)

A script consists of data and operators. These operators have defined opcodes. An operator has defined functionality. Data is preceded by a `pushdata` operator, which denotes the number of bytes in the following data.

The following are some of the opcodes:

 
| **Word** || **HEX** |
| --- | --- |
| OP\_DUP || 0x76 |
| OP\_HASH160 || 0xa9 |
| OP\_EQUALVERIFY || 0x88 |
| OP\_EQUAL || 0x87 |
| OP\_CHECKSIG || 0xac |
| Pushdata bytelength || 0x01-0x4b |
| OP\_PUSHDATA1 || 0x4c |
| OP\_PUSHDATA2 || 0x4d |
| OP\_PUSHDATA4 || 0x4e |

**Table 10.1:** OPCODES

The full list of opcodes can be found at following URL:

**[https://en.bitcoin.it/wiki/Script](https://en.bitcoin.it/wiki/Script)**

The hex values from 0x01 to 0x4b denote the size of the data. OP\_PUSHDATA1 denotes the size of data in the next 1 byte, OP\_PUSHADATA2 denotes the size of data in the next 2 bytes, and OP\_PUSHDATA4 denotes the size of data in the next 4 bytes. Here’s the illustration of the `pushdata` and the data:

![](images/Figure-10.2.jpg)

**Figure 10.2:** Pushdata size encoding

We use the preceding table to convert script hex-code to get the readable script:

`op_d = {‘76’: ‘OP_DUP’, ‘a9’: ‘OP_HASH160’, ‘88’: ‘OP_EQUALVERIFY’, ‘87’: ‘OP_EQUAL’, ‘ac’: ‘OP_CHECKSIG’, ‘ae’: ‘OP_CHECKMULTISIG’, ‘00’: ‘OP_0’, ‘51’: ‘OP_1’, ‘52’: ‘OP_2’, ‘53’: ‘OP_3’, ‘54’: ‘OP_4’, ‘55’: ‘OP_5’, ‘56’: ‘OP_6’, ‘57’: ‘OP_7’, ‘58’: ‘OP_8’, ‘59’: ‘OP_9’, ‘5a’: ‘OP_10’, ‘5b’: ‘OP_11’, ‘5c’: ‘OP_12’, ‘5d’: ‘OP_13’, ‘5e’: ‘OP_14’, ‘5f’: ‘OP_15’, ‘60’: ‘OP_16’, ‘6a’: ‘OP_RETURN’, ‘4c’: ‘OP_PUSHDATA1’, ‘4d’: ‘OP_PUSHDATA2’, ‘4e’: ‘OP_PUSHDATA4’}`

`OP_PUSHDATA1 = 0x4c`

`OP_PUSHDATA2 = 0x4d`

`OP_PUSHDATA4 = 0x4e`

`g_pushdata = range(0x01, 0x4c)`

`def prepare_readable_script(script_b: bytes):`

`script_len = len(script_b)`

`script_sl = []`

`i = 0`

`while i < script_len:`

`if script_b[i] in g_pushdata:`

`script_sl.append(script_b[i: i + 1].hex())`

`script_sl.append(script_b[i+1: i+script_b[i]+1].hex())`

`i += 1 + script_b[i]`

`elif script_b[i] == OP_PUSHDATA1:`

`script_sl.append(op_d[script_b[i:i+1].hex()])`

`datasize_b = script_b[i + 1: i + 2]`

`script_sl.append(datasize_b.hex())`

`datasize = int.from_bytes(datasize_b, byteorder=’little’)`

`script_sl.append(script_b[i + 2: i + 2 + datasize].hex())`

`i += 2 + datasize`

`elif script_b[i] == OP_PUSHDATA2:`

`script_sl.append(op_d[script_b[i:i+1].hex()])`

`datasize_b = script_b[i + 1: i + 3]`

`script_sl.append(datasize_b.hex())`

`datasize = int.from_bytes(datasize_b, byteorder=’little’)`

`script_sl.append(script_b[i + 3: i + 3 + datasize].hex())`

`i += 3 + datasize`

`elif script_b[i] == OP_PUSHDATA4:`

`script_sl.append(op_d[script_b[i:i+1].hex()])`

`datasize_b = script_b[i + 1: i + 5]`

`script_sl.append(datasize_b.hex())`

`datasize = int.from_bytes(datasize_b, byteorder=’little’)`

`script_sl.append(script_b[i + 5: i + 5 + datasize].hex())`

`i += 5 + data_size`

`else:`

`op_s = op_d[script_b[i:i+1].hex()]`

`script_sl.append(op_s)`

`i += 1`

`script_str = ‘ ‘.join(script_sl)`

`return script_str`

**Program 10.1:** Hex code to get the readable script

In the preceding program, the first byte of the script represents the script size in bytes. We have taken a few of the opcodes and mapped them with their hex codes.

We convert hex code to readable script by calling the preceding method as follows:

`if __name__ == ‘__main__’:`

`data_s = ‘76a91461cf5af7bb84348df3fd695672e53c7d5b3f3db988ac’`

`print(‘pushdata: ‘, data_s)`

`script_b = bytes.fromhex(data_s)`

`print(‘Decoded Script: ‘, prepare_readable_script(script_b))`

`print(‘====================================================’)`

`data_s = ‘6a4c500029282c0002c5164b82ab2b42044dbe2b8573c969cc10d9e0bd03646ccf1e7497c4bf69678a7b6a99ce4f8dda595a2ed353f27c6195bdfd0528ff229f2619002759d5b9d236d1458d1ad7e7640b5948’`

`print(‘PUSHDATA1: ‘, data_s)`

`script_b = bytes.fromhex(data_s)`

`print(‘Decoded Script: ‘, prepare_readable_script(script_b))`

`print(‘====================================================’)`

`data_s = ‘47304402201f46c0a476592d44192773fb0ac385d5ab0fc286882016b220e055314989d70f0220151e45313207ef60d7e91b66f03bbaade27ad0fb0a78ca692ccdb4fa36202a66014d33014d0701434e54525052545903000800157934c4b76dd4598533af398d4600bc62c30e20001de8e1db9ab1622fb8b35eae514f6a2b848dec9000489ad6851b31a59f042593c28f49976ffe17abc6005d3d7d62a84e90b0cfcb455c4f73bc795115a5f2005eac6a674669c6c0de63177ae4b3f8f21579a5e90068430e5056f9b75beb0dbf415a8aa2c65305a89e00687fd8a1bcc5a7f48c540591a4e3521fe7a5d67300a393004b7d01b3ad81276898afb8203c1b631b8a40000085ecef53f53d0000000000000001808000000000000000300c0000000000000006030000000000000000c01000000000000000180e00000000000000030080000000000000006000000000000000000c00752103cff10054cf9cf2dbda64adb01ccfc46c3dee8fcf4a9ba7eb14015ebe97cc31f3ad0075740087’`

`print(‘PUSHDATA2: ‘, data_s)`

`script_b = bytes.fromhex(data_s)`

`print(‘Decoded Script: ‘, prepare_readable_script(script_b))`

This gives us the following result:

![](images/Figure-10.3.jpg)

**Figure 10.3:** Shows script parsed by the program

# [Signature verification](#toc.xhtml#s218a)

When a node gets a transaction, it needs to verify it against consensus rules, which includes verifying the signature and public key against the locking script, which is P2PKH or P2PSH, or any other type of script. You have learned Signature verification in *[Chapter 5, The Whitepaper](#c05.xhtml)*, in a note named *Digital Signature.* You have learned that for signature verification, we require two inputs to the given signature: a public key and a message. The message, in this case, consists of version, input count, inputs, locktime, sighash type, output count, and outputs.

Here, sighash type indicates the structure of the message being signed by the new transaction.

The following are the sighash types that can be used:

 
| **SIGHASH Types** || **Hex code** || **Meaning** |
| --- | --- | --- |
| SIGHASH\_ALL || 0x01 || Signs all inputs and outputs |
| SIGHASH\_NONE || 0x02 || Signs all inputs and no outputs |
| SIGHASH\_SINGLE || 0x03 || Signs all inputs and single output |
| SIGHASH\_ALL|SIGHASH\_ANYONECANPAY || 0x81 || Signs one input and all outputs |
| SIGHASH\_NONE|SIGHASH\_ANYONECANPAY || 0x82 || Signs one input and no outputs |
| SIGHASH\_SINGLE|SIGHASH\_ANYONECANPAY || 0x83 || Signs one input and one output |

**Table 10.2:** Sighash types

Here’s the description of each of the preceding sighash types:

*   `SIGHASH_ALL`: Signing all outputs is needed to make sure someone does not change the output and steals the bitcoins. Consequently, every transaction needs to have at least one input signed with `SIGHASH_ALL`*.*
*   `SIGHASH_NONE`: This is mostly used with `SIGHASH_ANYONECANPAY`, but it is valid to use this sighash type without `SIGHASH_ANYONECANPAY` when all inputs are known.
*   `SIGHASH_SINGLE`: This is mostly used with `SIGHASH_ANYONECANPAY.` Similar to `SIGHASH_NONE`, this sighash type can also be used without `SIGHASH_ANYONECANPAY.`
*   `SIGHASH_ALL|SIGHASH_ANYONECANPAY`: This is useful if each one is contributing to specific purposes, like collectively paying for buying a gift from a gift shop. In this case, everyone knows where the funds are going and in what quantity, and everyone knows how much they need to contribute.
*   `SIGHASH_NONE|SIGHASH_ANYONECANPAY`: This is useful when a coordinator is collecting funds for certain purposes. The collector knows where the funds need to go, so they will sign all inputs and outputs with their private key while creating a signature of one input. Others will not know where funds are to be used, so they will sign by `SIGHASH_NONE|SIGHASH_ANYONECANPAY`*.*
*   `SIGHASH_SINGLE|SIGHASH_ANYONECANPAY`: This is useful for merging independent transactions where each transaction has one input and one output. There needs to be one input that signs all outputs. The biggest issue here is that output value is normally fixed, so excess value needs to be paid as change. This can only be useful if the input and output match or if the input is less than output. We can call a transaction partial if the input is less than the output. In this case, each one makes a partial transaction, and the collector adds the remaining bitcoins in order to complete the transaction. As an example, this can be used if the payment is subsidized by another entity, who finally completes the transaction by signing all outputs.

# [Hash type – SIGHASH\_ALL](#toc.xhtml#s219a)

The following illustration shows how signature in scriptSig is created for `SIGHASH_ALL`:

![](images/Figure-10.4.jpg)

**Figure 10.4:** Transaction creation for SIGHASH\_ALL

The preceding figure shows how the signature is created by using the message and private key. In the case of `SIGHASH_ALL`, we create the message by taking all the elements of the new transaction. We then replace scriptSig and scriptSig length with the executing script, which, in the case of P2PKH, is the previous scriptPubKey and scriptPubKey length for the input index to be signed. For the other inputs, scriptSig length is replaced with zero as those inputs are not getting signed. For P2SH script, scriptSig and its length are replaced with redeem script and its length. At the end of the message, we add sighash type.

# [Hash type – SIGHASH\_NONE, SIGHASH\_SINGLE, SIGHASH\_ANYONECANPAY](#toc.xhtml#s220a)

The following illustration shows the message structure to be signed for other sighash types:

![](images/Figure-10.5.jpg)

**Figure 10.5:** Signature preimage for sighash types other than SIGHASH\_ALL

In the case of `SIGHASH_ANYONECANPAY`, only the signed input is part of the message to be signed, and other inputs are not included. In the case of `SIGHASH_NONE`, none of the outputs are included, and in the case of `SIGHASH_SINGLE`, only one output is included. We can observe that the output index in the case, `SIGHASH_SINGLE`, corresponds to the input that is being signed. This means, if input 0 is signed, then output 0 is included and output 1 is excluded. If input 1 is signed, then output 1 is included and output 0 is excluded. If the excluded output is not the last output of the message, then we need to keep the excluded output as a placeholder by just having `0xFFFFFFFFFFFFFFFF` and `0x00` as is in the figure. In both `SIGHASH_NONE` and SIGHASH_SINGLE, the sequences of inputs that are not signed are replaced by `0x00000000`.

# [Standard Bitcoin script - P2PK](#toc.xhtml#s221a)

P2PK is not recommended for use. P2PK stands for ***Pay-2-Public-Key***.

In this script, `scriptsig` is:

` <Signature>`

and `scriptpubkey` is:

` <Public Key> OP_CHECKSIG`

It has simple execution: first, `scriptSig` gets executed, in which signature is pushed into stack, and then `scriptPubKey` gets executed, which pushes public-key to stack, and then `OP_CHECKSIG` checks the signature by popping out the signature and the public-key and pushes back the result to the stack.

This script had a few drawbacks:

*   Compressed Public Keys are 32-bytes long, while the hash used by the P2PKH script is 20-byte long, so its hex is 40-character long, which is much easier to type. An address generated from 20-bytes using base58check encoding is 34-character long.
*   If quantum computers can utilize a quantum technique called Shor’s algorithm, it is expected that they will be able to derive private keys from public keys. For Bitcoin to remain secure in the future, we should not expose our public keys on the networks that are still holding bitcoins. By having a public key hash, we have multiple levels of security to secure our funds.

Since this script is not recommended, there is no point in going deeper into understanding it.

# [Standard Bitcoin script – P2PKH](#toc.xhtml#s222a)

P2PKH is the most widely used Bitcoin script. P2PKH stands for ***Pay-2-Public-Key-Hash***. In the script, the sender locks the transaction output using the hash of the public key, and it requires the receiver to provide the public key when it needs to use the funds locked in transaction output. The hash is 20-byte long, which is smaller than the 32-byte long compressed public key. And it generates a 34-character long address, which includes a checksum. This makes it easier to type, and since it contains a checksum, it is not possible to accidentally type the wrong address.

The `scriptSig` in P2PKH is:

` <Signature> <Public Key Hash>`

and the `scriptPubKey` is:

` OP_DUP OP_HASH160 <20-byte pubkey hash> OP_EQUALVERIFY OP_CHECKSIG`

Since `<Signature>` and `<Public Key Hash>` both are data, both go into the stack. Once `scriptSig` is executed, `scriptPubKey` is executed.

The following illustration shows the execution of P2PKH:

![](images/Figure-10.6.jpg)

**Figure 10.6:** Execution of P2PKH

# Prepare signature preimage

All messages include sighash type at the end. Once the message is signed, the sighash type is appended to the signature to help the verifying node reconstruct the message before verification.

Now, we are ready to verify a real transaction script. We take following transaction ID:

`83eeaecaf531e5239ffc3ba7ff583c696f7dbe3610f0d672d41e0b9443632c82`

Since the transaction is in the Bitcoin blockchain, we get the raw transaction by calling `getrawtransaction` in Bitcoin Core CLI, as follows:

![](images/Figure-10.7.jpg)

**Figure 10.7:** Shows the Bitcoin Core CLI command for getting transaction bytes

This gives us the following raw transaction:

![](images/Figure-10.8.jpg)

**Figure 10.8:** Shows the hex data of the traansaction-ID

We can use the transaction and parse it using the `getTransactionInfo` method written in *[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml),* under the topic *Transactions* and the subtopic *Other transaction* in *Program 6.15,* to get scriptSig.

This gives us the following information:

`Transaction = {‘version’: ‘00000001’, ‘inp_cnt’: 2, ‘inputs’: [{‘prev_tx_hash’: ‘15b91bcf8b2b9ea46d0daab60aaa2e99b15a5fb37d9d4568d4c060e515e13130’, ‘prev_tx_out_index’: ‘00000001’, ‘bytes_scriptsig’: 106, ‘scriptsig’: ‘47304402205535a9ac25844514828bff3580120d5add488e09b7a6e62018fc265aabf95fe302200b66d4eb23fc348b31d58729b479ae73db9dfc467edf38f8dfd927c48cb46b5801210219fbee4b9cc12188598f244ff0ee352b124cbf9046180a1b25e020c0258f9d64’, ‘sequence’: ‘ffffffff’}, {‘prev_tx_hash’: ‘840ac7a55498c6746b9d7460a348f79e2f35db4a9696bef762d975e7e1deeff2’, ‘prev_tx_out_index’: ‘0000000c’, ‘bytes_scriptsig’: 106, ‘scriptsig’: ‘47304402203a28d10c786907fcb71c7bf69c507d58884ea9af2e7fa3b413d4e2867eca601502205fb253d82e4daa2672842ec031584ea7a215774422aa7de3cf8928c240e2faa60121030be5aa6d5de8c6dd89d6ac4d0e2a112caf5b12801349ab30fbdf2b205f0b94b8’, ‘sequence’: ‘ffffffff’}], ‘out_cnt’: 2, ‘outs’: [{‘satoshis’: 69302, ‘bytes_scriptpubkey’: 25, ‘scriptpubkey’: ‘76a914f133f0339987cd84b6017517de2a93f009728d7e88ac’}, {‘satoshis’: 12900349, ‘bytes_scriptpubkey’: 25, ‘scriptpubkey’: ‘76a91406c3bc40cde01312e2b24f8d2c23e68ea7d572f888ac’}], ‘locktime’: 0}`

The following program further parses `scriptSig` to get signature, `sighash` type, and public key:

`OP_PUSHDATA1 = 0x4c`

`OP_PUSHDATA2 = 0x4d`

`OP_PUSHDATA4 = 0x4e`

`SIGHASH_ALL = 0x01`

`SIGHASH_NONE = 0x02`

`SIGHASH_SINGLE = 0x03`

`SIGHASH_ANYONECANPAY = 0x80`

`def getHashTypeInWords(hashtype: int):`

`hashtype_s = “”`

`if hashtype & SIGHASH_SINGLE == 0x03:`

`hashtype_s = “SIGHASH_SINGLE”`

`elif hashtype & SIGHASH_NONE == 0x02:`

`hashtype_s = “SIGHASH_NONE”`

`elif hashtype & SIGHASH_ALL == 0x01:`

`hashtype_s = “SIGHASH_ALL”`

`if hashtype & SIGHASH_ANYONECANPAY == 0x80:`

`hashtype_s = hashtype_s + “|” + “SIGHASH_ANYONECANPAY”`

`return hashtype_s`

`def decodePushdata(script_m: mmap):`

`length = int.from_bytes(script_m.read(1), byteorder=’little’)`

`if length == OP_PUSHDATA1:`

`length = int.from_bytes(script_m.read(1), byteorder=’little’)`

`elif length == OP_PUSHDATA2:`

`length = int.from_bytes(script_m.read(2), byteorder=’little’)`

`elif length == OP_PUSHDATA4:`

`length = int.from_bytes(script_m.read(4), byteorder=’little’)`

`return length`

`def parseScriptSig(script_m: mmap):`

`scriptsig = {}`

`scriptsig[‘bytes_sig’] = decodePushdata(script_m)`

`scriptsig[‘sig’] = script_m.read(scriptsig[‘bytes_sig’] - 1).hex()`

`scriptsig[‘hash_type’] = int.from_bytes(script_m.read(1), byteorder=’little’)`

`scriptsig[‘hash_type_name’] = getHashTypeInWords(scriptsig[‘hash_type’])`

`scriptsig[‘bytes_pubkey’] = decodePushdata(script_m)`

`scriptsig[‘pubkey’] = script_m.read(scriptsig[‘bytes_pubkey’]).hex()`

`return scriptsig`

**Program 10.2:** Scriptsig parser

We call the preceding method as follows:

`script_b = bytes.fromhex(‘47304402203a28d10c786907fcb71c7bf69c507d58884ea9af2e7fa3b413d4e2867eca601502205fb253d82e4daa2672842ec031584ea7a215774422aa7de3cf8928c240e2faa60121030be5aa6d5de8c6dd89d6ac4d0e2a112caf5b12801349ab30fbdf2b205f0b94b8’)`

`script_m = mmap.mmap(-1, len(script_b) + 1)`

`script_m.write(script_b)`

`script_m.seek(0)`

`scriptsig = parseScriptSig(script_m)`

`print(json.dumps(scriptsig, indent=4))`

This gives us the following results:

![](images/Figure-10.9.jpg)

**Figure 10.9:** Shows the JSON output by running the parseScriptSig program

We will use the preceding information to verify the transaction. We first implement script operations. Then, we use the list as a stack and use pop and append operations:

`st = []`

`def opHash160():`

`v = st.pop()`

`h = hash160(v)`

`st.append(h)`

`def opDup():`

`v = st.pop()`

`st.append(v)`

`st.append(v)`

`def opEqualVerify():`

`v1 = st.pop()`

`v2 = st.pop()`

`if v1 == v2:`

`return True`

`else:`

`return False`

`g_pushdata = range(0x01, 0x4f)`

`def pushdata(d: bytes):`

`st.append(d)`

`def opCheckSig(script_b: bytes, inp_index: int, tx: dict):`

`pubkey_b = st.pop()`

`sig_b = st.pop()`

`v = sigcheck(sig_b, pubkey_b, script_b, inp_index, tx)`

`st.append(v)`

**Program 10.3:** Bitcoin script operations for P2PKH

The `OP_CheckSig` operation verifies transaction messages using a signature and a public key that is on the stack. To create the signature preimage, we take the transaction bytes and replace the input signature needed to be verified by executing the script. This is shown in *[figures 10.4](#c10.xhtml#fig10_4)* and *[10.5](#c10.xhtml#fig10_5)*. This is the reason we pass script bytes and input index as its arguments.

We call the script operators using the following method, which reads script bytes till the whole script is executed:

`def execScript(script_b: bytes, inp_index: int, tx: dict):`

`l = len(script_b)`

`script_m = bytes2Mmap(script_b)`

`while script_m.tell() < l:`

`v = script_m.read(1)`

`b = int.from_bytes(v, byteorder=’little’)`

` if b in g_pushdata:`

`script_m.seek(-1, 1)`

`b = decodePushdata(script_m)`

`d = script_m.read(b)`

`pushdata(d)`

`elif v == b’\x76’:`

`opDup()`

`elif v == b’\xa9’:`

`opHash160()`

`elif v == b’\x88’:`

`opEqualVerify()`

`elif v == b’\xac’:`

`opCheckSig(script_b, inp_index, tx)`

**Program 10.4:** P2PKH script execution

The `opCheckSig` method calls the `sigcheck` method, which performs signature verification using the `ecdsa` package. To understand signature verification, we need to understand the format of signature used by Bitcoin transactions.

We use the created message and the private key to verify the signature. The signature we get in the transaction is in the *DER encoding*. **DER** stands for **Distinguished Encoding Rules**. Here’s the structure of DER encoding:

![](images/Figure-10.10.jpg)

**Figure 10.10:** DER encoding

The following is the description of the components of DER encoding:

*   0x30 byte: Indicates compound structure
*   Data Size: Size of data following this byte
*   0x02: Indicates integer
*   R value size: Size of R may include 0x00 prefix
*   R: This may include 0x00 prefix
*   S value size: Size of S may include 0x00 prefix
*   S: This may include 0x00 prefix

The `ecdsa` package we are using requires a signature to be a concatenation of *R* and *S*.

The following code returns concatenated *R* and *S:*

`def getRandSFromSig(sig_b: bytes):`

`sig_m = bytes2Mmap(sig_b)`

`struct = sig_m.read(1)`

`size = sig_m.read(1)`

`rheader = sig_m.read(1)`

`rsize_b = sig_m.read(1)`

`rsize = int.from_bytes(rsize_b, byteorder=’little’)`

`if rsize == 33:`

`sig_m.read(1)`

`r = sig_m.read(32)`

`sheader = sig_m.read(1)`

`ssize_b = sig_m.read(1)`

`ssize = int.from_bytes(ssize_b, byteorder=’little’)`

`if ssize == 33:`

`sig_m.read(1)`

`s = sig_m.read(32)`

`return r + s`

**Program 10.5:** Get concatenated R and S bytes

We need to build signature preimage to verify signatures using input index and current executing script. The following code does this:

`def bytes2Mmap(b: bytes):`

`m = mmap.mmap(-1, len(b) + 1)`

`m.write(b)`

`m.seek(0)`

`return m`

`# This method returns both value of variable integer and also the variable integer bytes`

`def setVarInt(n: int):`

`if n < 0xfd:`

`n_h = ‘%02x’ % n`

`elif n > 0xfd and n < 0xffff:`

`n_h = ‘fd%04x’ % n`

`elif n > 0xffff and n < 0xFFFFFFFF:`

`n_h = ‘fe%08x’ % n`

`else:`

`n_h = ‘ff%016x’ % n`

`return bytes.fromhex(n_h)`

`def createMsgInputsForSig(tx: dict, script_b: bytes,`

`inp_index: int,`

`sighash_type: int,`

`inp_cnt: int):`

`msg_b = b’’`

`for i in range(inp_cnt):`

`tx_inp = tx[‘inputs’][i]`

`inp_b = bytes.fromhex(tx_inp[‘prev_tx_hash’])[::-1]`

`inp_b += struct.pack(‘<L’, tx_inp[‘prev_tx_out_index’])`

`if i == inp_index:`

`inp_b += bytes.fromhex(‘%02x’ % len(script_b))`

`inp_b += script_b`

`inp_b += struct.pack(‘<L’, tx_inp[‘sequence’]) # sequence`

`else:`

`inp_b += bytes(1)`

`inp_b += struct.pack(‘<L’, tx_inp[‘sequence’]) # sequence`

`msg_b += inp_b`

`return msg_b`

`def createMsgOutsForSig(tx: dict, inp_index: int, sighash_type: int):`

`msg_b = b’’`

`msg_b += setVarInt(tx[‘out_cnt’])`

`for o in range(tx[‘out_cnt’]):`

`tx_out = tx[‘outs’][o]`

`msg_b += struct.pack(‘<Q’, tx_out[‘satoshis’])`

`msg_b += setVarInt(tx_out[‘bytes_scriptpubkey’])`

`msg_b += bytes.fromhex(tx_out[‘scriptpubkey’])`

`return msg_b`

`def createMsgForSig(tx: dict, script_b: bytes, inp_index: int, sighash_type: int):`

`msg_b = bytes.fromhex(tx[‘version’])[::-1]`

`inp_cnt = tx[‘inp_cnt’]`

`msg_b += setVarInt(inp_cnt)`

`msg_b += createMsgInputsForSig(tx, script_b, inp_index, sighash_type, inp_cnt)`

`msg_b += createMsgOutsForSig(tx, inp_index, sighash_type)`

`msg_b += struct.pack(‘<L’, tx[‘locktime’])`

`msg_b += struct.pack(‘<L’, sighash_type)`

 return` msg_b`

**Program 10.6:** Create signature preimage

We use the message generated by calling the preceding method and using the public key to verify the signature. We have written the following method to verify the transaction signature at the given input index:

`from cryptotools.ECDSA.secp256k1 import PublicKey`

`def uncompressPubkey(pubkey_b: bytes):`

`pubkey_P = PublicKey.decode(pubkey_b)`

`pubkey_b = PublicKey.encode(pubkey_P, compressed=False)`

`return pubkey_b`

`def sigcheck(sig_b: bytes, pubkey_b: bytes, script_b: bytes, inp_index: int, tx: dict):`

`sighash_type = sig_b[-1]`

`msg_b = createMsgForSig(tx, script_b, inp_index, sighash_type)`

`msg_h = hashlib.sha256(msg_b).digest()`

`prefix = pubkey_b[0:1]`

`if prefix == b”\x02” or prefix == b”\x03”:`

`fullpubkey_b = uncompressPubkey(pubkey_b)[1:]`

`elif prefix == b”\x04”:`

`fullpubkey_b = pubkey_b[1:]`

`rs_b = getRandSFromSig(sig_b)`

`vk = ecdsa.VerifyingKey.from_string(fullpubkey_b, curve=ecdsa.SECP256k1)`

`try:`

`if vk.verify(rs_b, msg_h, hashlib.sha256) == True:`

`print(“Signature is Valid”)`

`return b’\x01’`

`else:`

`print(“Signature is not Valid”)`

`return b’\x00’`

`except ecdsa.keys.BadSignatureError:`

`print(“Signature is not Valid”)`

`return b’\x00’`

**Program 10.7:** Signature verification method

We can use the preceding program to verify transaction signature related P2PKH address.The following the methods required to verify P2PKH script:

`def getScriptSig(tx: dict, inp_index: int):`

`return bytes.fromhex(tx[‘inputs’][inp_index][‘scriptsig’])`

`def getPrevScriptPubKey(tx: dict, inp_index: int):`

`prevtx_rb = bytes.fromhex(tx[‘inputs’][inp_index][‘prev_tx_hash’])[::-1]`

`prevtx_outindex = tx[‘inputs’][inp_index][‘prev_tx_out_index’]`

`prevtx = findTransaction(prevtx_rb, txindex_db_g)`

`prevScriptPubkey = prevtx[‘outs’][prevtx_outindex][‘scriptpubkey’]`

`prevScriptPubkey_b = bytes.fromhex(prevScriptPubkey)`

`return prevScriptPubkey_b`

`def verifyScript(tx: dict, inp_index: int):`

`scriptsig_b = getScriptSig(tx, inp_index)`

`execScript(scriptsig_b, inp_index, tx)`

`prev_scriptpubkey_b = getPrevScriptPubKey(tx, inp_index)`

`execScript(prev_scriptpubkey_b, inp_index, tx)`

`status = st.pop()`

`if status == b’\x01’:`

`print(‘1st Script succeeded’)`

`elif status == b’\x01’:`

`print(‘1st Script Failed’)`

`else:`

`print(‘1st Invalid state’)`

**Program 10.8:** Methods to verify P2PKH script

We call the preceding method as follows to verify a transaction scriptSig:

`if __name__ == ‘__main__’:`

`txid_s = ‘2df97b379c9ce9e4a60529f555b9742c04f90b922c2fcff846ebae41206b93f9’`

`inp_index = 1`

`txid_b = bytes.fromhex(txid_s)[::-1]`

`tx = findTransaction(txid_b, txindex_db_g)`

`verifyScript(tx, inp_index)`

# [Standard Bitcoin script – P2MS](#toc.xhtml#s223a)

P2MS stands for ***Pay-2-Multisig***. This script allows the use of multiple signatures in order to access the locked bitcoin.

The script looks as follows:

**ScriptPubKey:** `OP_n <Public Key 1><Public Key 2>…<Public Key m>OP_m<Multisig>`

**ScriptSig:** `OP_0 <Signature 1><Signature 2>… <Signature n>`

In a 2-of-3-multisig, two of the three signatures are required to claim the funds locked by `scriptPubKey`.

This means when we create a transaction, we need to have multiple public keys in the script. These have the following disadvantages:

1.  Transaction will consume many more bytes than the normal P2PKH script, so the sender will have to pay a higher transaction fee.
2.  A sender will need to form a complex script by taking multiple public keys even though it is sending it to just one receiver. This is an overhead for the sender.
3.  Public keys may not remain secure if quantum computers are able to utilize Shor’s algorithm to break private key public key cryptography.

In 2012, P2SH was introduced as a softfork that solved the preceding disadvantages, so we are not going deeper into this script.

# [Standard Bitcoin script – P2SH](#toc.xhtml#s224a)

P2SH stands for ***Pay-2-Script-Hash***. As the name suggests, there is a script embedded in the hash, which must satisfy for payment to be made. This is mostly used to allow the use of multiple signatures in order to access bitcoin. It was introduced as a softfork in 2012.

The P2SH script replaced the multisig script with a script hash, so the sender does not need to pay extra to the miner for including their transaction.

For P2SH, the `scriptSig` is:

` <Signatures> <Redeem Scripts>`

and the `scriptPubKey` is:

` OP_HASH160 <20-byte Redeem Script hash> OP_EQUAL`

The Redeem Script for the 2-of-3-multisig is as follows:

` <2><Public Key 1><Public Key 2><Public Key 3><3><Multisig>`

In P2SH, two scripts need to get executed, i.e., the `scriptPubKey` and redeem script, along with the given list of signatures. This is a special script and executes a bit differently. In this case, a copy of the stack is maintained, and once `scriptPubKey` gets executed, the redeem script starts executing.

As `scriptPubKey` in P2SH script contains a 20-byte hash of script, and we can hide complex scripts within the hash. The sender will not know what the rules are for claiming the funds; they will only have a normal-looking address to transfer his coins. This greatly simplifies and, at the same time, imposes complex rules for claiming the locked bitcoin. These complex rules work as a contract between parties. These contracts lead to the origin of the smart contract, which we will learn more about in the next chapter.

The following illustration explains the execution of P2SH:

![](images/Figure-10.11.jpg)

**Figure 10.11:** P2SH execution

To write a program that could verify signature against P2SH transaction output, we need to be able to identify P2SH as it involves three consecutive executions of scripts. Here are the three execution scripts:

*   OP\_0 <signature 1> <signature 2> … <signature m> <Redeem Script>
*   OP\_HASH160 <Redeem Script Hash> OP\_EQUAL
*   Redeem script: OP\_m <Public Key 1> <Public Key 2> … <Public Key n> OP\_n OP\_MULTISIG

For P2SH, the signature preimage remains the same, so we extend the program covered in the previous section on P2PKH to include redeem script handling and to also have handling for `OP_CHECKMULTISIG`.

`g_pushnumber = range(0x51, 0x61) # excludes 0x61`

`def opEqual():`

`v1 = st.pop()`

`v2 = st.pop()`

`if v1 == v2:`

`st.append(b’\x01’)`

`else:`

`st.append(b’\x00’)`

`def opNum(b: int):`

`num = b - 0x50`

`st.append(bytes([num]))`

`def opCheckMultisig(script_b: bytes, inp_index: int, tx: dict):`

`pubkey_cnt = int.from_bytes(st.pop(), byteorder=’little’)`

`pubkey_l = [st.pop() for i in range(pubkey_cnt)][::-1]`

`sig_cnt = int.from_bytes(st.pop(), byteorder=’little’)`

`sig_l = [st.pop() for i in range(sig_cnt)][::-1]`

`sig_index = 0`

`for pubkey_b in pubkey_l:`

`v = sigcheck(sig_l[sig_index], pubkey_b, script_b, inp_index, tx)`

`if v == b’\x01’:`

`sig_index += 1`

`if sig_index == sig_cnt:`

`break`

`# convert True/False to b’\x01’ or b’\x00’`

`b = bytes([int(sig_index == sig_cnt and v == b’\x01’)])`

`st.append(b)`

**Program 10.9:** Bitcoin script operations for P2SH

The following program identifies if we were executing P2SH script. This method is called after `scriptSig` is executed:

`def checkWrappedMultisig(st):`

`script_b = st[-1]`

`val = script_b[-2]`

`if bytes([script_b[-1]]) == b’\xae’ and val in g_pushnumber:`

`return True`

`else:`

`return False`

**Program 10.10:** Identify P2SH script

The following is the updated `execScript` method that handles additional opcodes:

`def execScript(script_b: bytes, inp_index: int, tx: dict):`

`l = len(script_b)`

`script_m = bytes2Mmap(script_b)`

`while script_m.tell() < l:`

`v = script_m.read(1)`

`b = int.from_bytes(v, byteorder=’little’)`

`if b == 0x00:`

`pass`

`elif b < 0x4f:`

`script_m.seek(-1, 1)`

`b = decodePushdata(script_m)`

`d = script_m.read(b)`

`pushdata(d)`

`elif v == b’\x76’:`

`opDup()`

`elif v == b’\xa9’:`

`opHash160()`

`elif b in g_pushnumber:`

`opNum(b)`

`elif v == b’\x87’:`

`opEqual()`

`elif v == b’\x88’:`

`opEqualVerify()`

`elif v == b’\xac’:`

`opCheckSig(script_b, inp_index, tx)`

`elif v == b’\xae’:`

`opCheckMultisig(script_b, inp_index, tx)`

**Program 10.11:** P2SH script execution

The following method performs P2SH script verification:

`def verifyScript(tx: dict, inp_index: int):`

`isP2SH = False`

`scriptsig_b = getScriptSig(tx, inp_index)`

`execScript(scriptsig_b, inp_index, tx)`

`prev_scriptpubkey_b = getPrevScriptPubKey(tx, inp_index)`

`if checkWrappedMultisig(st) == True:`

`redeemscript_b = st[-1]`

`isP2SH = True`

`execScript(prev_scriptpubkey_b, inp_index, tx)`

`status = st.pop()`

`if status == b’\x01’:`

`print(‘1st Script succeeded’)`

`elif status == b’\x01’:`

`print(‘1st Script Failed’)`

`else:`

`print(‘1st Invalid state’)`

`if isP2SH == True:`

`execScript(redeemscript_b, inp_index, tx)`

`status = st.pop()`

`if status == b’\x01’:`

`print(‘2nd Script succeeded’)`

`elif status == b’\x01’:`

`print(‘2nd Script Failed’)`

`else:`

`print(‘2nd Invalid state’)`

**Program 10.12:** P2SH verification method

We call the preceding method as follows to verify a transaction scriptSig:

`if __name__ == ‘__main__’:`

`txid_s = ‘8b3e54e345d0b3e9278a27f1ab2aa2566aba8cbe7cf44b9aa1836c9d0fcc2625’`

`inp_index = 0`

`txid_b = bytes.fromhex(txid_s)[::-1]`

`tx = findTransaction(txid_b, txindex_db_g)`

`verifyScript(tx, inp_index)`

Since you have understood how transactions are verified, we will now create transactions and move the `regtest` bitcoin from one address to another.

# [Building transactions](#toc.xhtml#s225a)

We are trying to create a transaction in this subtopic. To build a transaction, we need to fund the transaction from the previous transaction. Since we don’t want to use real bitcoin and want to easily mine a block, we are using a `regtest` environment. The transaction output we are using needs to be unspent. If the transaction is already confirmed, we can find the transaction in the *chainstate database*. If the funding transaction is not confirmed, it will be in the mempool. We are using the funding transaction from the chainstate database and not looking at mempool. We have already defined the method to retrieve UTXO from the chainstate database. The following method is used to get unspent output information:

`getUnspentTransactions`

We can look at the method implementation in ***[Chapter 6, Blockchain, Transactions, and Mining](#c06.xhtml)****,* **under** the s**ubtopic** ***UTXO***, ***Program 6.****20*. We use this method to get `scriptPubKey` for P2PKH transactions.

The following program returns the execution script that is required in the creation of P2SH transaction and in signing preimage for both P2SH and P2PKH. In the following program, the first argument is the transaction structure, which is a `dict` containing the information required to build the required transaction. The following method will be used later to get bytes from the hex string of script given in the transaction structure:

`def getExecutionScript(txn_struct: dict, inp_index: int):`

`inp = txn_struct[‘inputs’][inp_index]`

`script_type = inp[‘script_type’]`

` if script_type[:4] == ‘P2SH’:`

`script_b = bytes.fromhex(inp[‘redeem_script’])`

`elif script_type == ‘P2PKH’:`

`script_b = bytes.fromhex(inp[‘script_pubkey’])`

`return script_b`

**Program 10.13:** Get execution script for substituting Signature in Preimage

The bytes of script we obtained in the preceding method is an input to the `createSignaturePreimage` method*.*

In the following methods, we will generate script in bytes from given address. We have already taken a look at the structure of P2PKH and P2SH in the preceding sections, where we discussed P2PKH and P2H scripts:

`def getScriptPubkeyP2PKH(address: str):`

`pkh_b = address2PubkeyHash(address)`

`pkhSize_b = encodePushdata(len(pkh_b))`

`scriptPubkey_b = bytes([OP_DUP, OP_HASH160]) \`

`+ pkhSize_b + pkh_b \`

`+ bytes([OP_EQUALVERIFY]) \`

`+ bytes([OP_CHECKSIG])`

`return scriptPubkey_b`

`def getScriptPubkeyP2SH(address: str):`

`sh_b = address2PubkeyHash(address)`

`shSize_b = encodePushdata(len(sh_b))`

`scriptPubkey_b = bytes([OP_HASH160]) \`

` + shSize_b \`

` + sh_b \`

` + bytes([OP_EQUAL])`

`return scriptPubkey_b`

`def getScriptPubkeyFromAddress(address: str):`

`pkh_b = address2PubkeyHash(address)`

`pkhSize_b = encodePushdata(len(pkh_b))`

`script_type = getScriptTypeFromAddress(address)`

`if script_type == ‘P2PKH’:`

`scriptPubkey_b = getScriptPubkeyP2PKH(address)`

`elif script_type == ‘P2SH’:`

`scriptPubkey_b = getScriptPubkeyP2SH(address)`

`return scriptPubkey_b`

**Program 10.14:** Prepare Script Pubkey from Address

The following method generates sequence in bytes for transaction inputs based on the `locktime` field:

`def getSequence(txn_struct: dict):`

`if txn_struct[‘locktime’] > 0:`

`sequence_b = bytes([0xfe, 0xff, 0xff, 0xff])`

`else:`

`sequence_b = bytes([0xff, 0xff, 0xff, 0xff])`

`return sequence_b`

**Program 10.15:** Return sequence using given locktime

The following are the utility methods which are used in the succeeding methods:

`def createVarInt(i: int):`

`if i < 0xfd:`

`return bytes([i])`

`elif i < 0xffff:`

`return b’\xfd’ + struct.pack(‘<H’, i)`

`elif i < 0xffffffff:`

`return b’\xfe’ + struct.pack(‘<L’, i)`

`elif i < 0xffffffffffffffff:`

`return b’\xff’ + struct.pack(‘<Q’, i)`

`def address2PubkeyHash(address: str):`

`pkh = base58checkDecode(address)`

`return pkh`

`def encodePushdata(length: int):`

`if length <= 0x4b:`

`return bytes([length])`

`if length <= 0xff:`

`return bytes([OP_PUSHDATA1, length])`

`if length <= 0xffff:`

`return bytes([OP_PUSHDATA2]) + struct.pack(‘<H’, length)`

`if length <= 0xffffffff:`

`return bytes([OP_PUSHDATA4]) + struct.pack(‘<L’, length)`

`def getScriptTypeFromAddress(address: str):`

`if address[0] in [‘m’, ‘n’] or address[0] == ‘1’:`

`return “P2PKH”`

`elif address[0] == ‘2’ or address[0] == ‘3’:`

`return “P2SH”`

*[Figure 10.16:](#c10.xhtml#fig10_16)* Utility methods required for building transactions

Following are the opcodes used by the methods to create transaction:

`OP_0 = 0x00`

`OP_DUP = 0x76`

`OP_EQUAL = 0x87`

`OP_EQUALVERIFY = 0x88`

`OP_HASH160 = 0xa9`

`OP_CHECKSIG = 0xac`

`OP_CHECKMULTISIG = 0xae`

The signature preimage is the message that is signed using the private key of the sender. The following method generates signature preimage using the preceding methods:

`def createSignaturePreimage(txn_struct: dict,`

` script_b: bytes,`

` inp_index: int):`

`preimage_b = b’’`

`preimage_b += struct.pack(‘<L’, txn_struct[‘version’])`

`preimage_b += createVarInt(txn_struct[‘input_count’])`

`for i in range(txn_struct[‘input_count’]):`

`inp = txn_struct[‘inputs’][i]`

`preimage_b += bytes.fromhex(inp[‘prevtxn’])[::-1]`

`preimage_b += struct.pack(‘<L’, inp[‘prevtxnindex’])`

`if i == inp_index:`

`preimage_b += createVarInt(len(script_b))`

`preimage_b += script_b`

`else:`

`preimage_b += b’\x00’`

`preimage_b += getSequence(txn_struct)`

`preimage_b += createVarInt(txn_struct[‘out_count’])`

`for out in range(txn_struct[‘out_count’]):`

`satoshis = txn_struct[‘outputs’][out][‘satoshis’]`

`preimage_b += struct.pack(‘<Q’, satoshis)`

`address = txn_struct[‘outputs’][out][‘address’]`

`scriptPubkey_b = getScriptPubkeyFromAddress(address)`

`preimage_b += createVarInt(len(scriptPubkey_b))`

`preimage_b += scriptPubkey_b`

`preimage_b += struct.pack(‘<L’, txn_struct[‘locktime’])`

`hashtype = txn_struct[‘inputs’][inp_index][‘hash_type’]`

`preimage_b += struct.pack(‘<L’, hashtype)`

`print(‘preimage = ‘, preimage_b.hex())`

`return preimage_b`

**Program 10.17:** Prepare Signature Preimage

We generate a signature by signing the signature preimage using the private key. The signature is appended with `hash_type`.

Here’s the code:

`from ecdsa import SigningKey, SECP256k1`

`from ecdsa.util import sigencode_der_canonize`

`def signMessage(preimage_b: bytes,`

`privkey_wif: str,`

`hash_type: int):`

`hash_preimage = hash256(preimage_b)`

`privkey_s, network, compress = privkeyWif2Hex(privkey_wif)`

`if privkey_s.__len__() % 2 == 1:`

`privkey_s = “0{}”.format(privkey_s)`

`if compress == True:`

`print(‘compress is true’)`

`privkey_b = bytes.fromhex(privkey_s)[:-1]`

`else:`

`privkey_b = bytes.fromhex(privkey_s)`

`sk = SigningKey.from_string(privkey_b, curve=SECP256k1)`

`sig_b = sk.sign_digest(hash_preimage,`

` sigencode=sigencode_der_canonize) \`

`+ bytes([hash_type])`

`return sig_b`

**Program 10.18:** Method for signing message

In the preceding code, we call the following method in the `ecdsa` package:

`sk.sign_digest(hash_preimage,`

` sigencode=sigencode_der_canonize)`

This method generates a signature using a hash of preimage and private key. We know that the generated signature consists of R and S. Since Bitcoin uses elliptic curve algorithm `SECP256k1`, which is symmetric on the X-axis, it is possible to get the same signature using –S. This means there are two valid signatures for the same private key and message. Since the signature is part of the transaction, it makes two transaction IDs to represent the same transaction, which is a security problem, also called **transaction malleability**. There are other ways in which transaction malleability can occur. To avoid this problem, we use smaller of the S and –S. This is the reason we pass the `sigencode_der_canonize` argument to the method, which only generates **low S**.

As we have seen, `ScriptSig` has the following structure:

*   **P2PKH:** `<Signature> <Public Key>`
*   **P2SH:** `OP_0 <Signature 1><Signature 2> … <Signature N> <Redeem Script>`

We create the scriptSig for each funding transaction output:

`def getSignaturesAndExecScripts(txn_struct: dict):`

`signgrp_l = []`

`script_l = []`

`for inp_index in range(txn_struct[‘input_count’]):`

`inp = txn_struct[‘inputs’][inp_index]`

`script_b = getExecutionScript(txn_struct, inp_index)`

`preimage_b = createSignaturePreimage(txn_struct, script_b, inp_index)`

`inp = txn_struct[‘inputs’][inp_index]`

`signgrp = []`

`for privkey in inp[‘privkeys’]:`

`hashtype = inp[‘hash_type’]`

`sign_b = signMessage(preimage_b, privkey, hashtype)`

`signgrp.append(sign_b)`

`signgrp_l.append(signgrp)`

`script_l.append(script_b)`

`return txn_struct, signgrp_l, script_l`

**Program 10.19:** Method for preparing a list of signatures and scripts

We use the list of `scriptSig` and transaction structure to prepare the required transaction, as follows:

`def getWithPushdata(data_b: bytes):`

`pushdata_b = encodePushdata(len(data_b))`

`return pushdata_b + data_b`

`def createScriptSigForMultiSig(signgrp: list, script_b: bytes):`

`scriptSig_b = bytes([OP_0])`

`for sign_b in signgrp:`

`scriptSig_b += getWithPushdata(sign_b)`

`scriptSig_b += getWithPushdata(script_b)`

`return scriptSig_b`

`def createScriptSigForP2PKH(txn_input: dict, signgrp: list):`

`sign_b = signgrp[0] # it’s not a group.. just one signature`

`scriptSig_b = getWithPushdata(sign_b)`

`privkey = txn_input[‘privkeys’][0]`

`pubkey_b = privkeyWif2pubkey(privkey)`

`scriptSig_b += getWithPushdata(pubkey_b)`

`return scriptSig_b`

`def createSignedInput(txn_input: dict, signgrp, script_b: bytes):`

`prevtxn = txn_input[‘prevtxn’]`

`prevtx_rb = bytes.fromhex(prevtxn)[::-1]`

`prevtxnindex = txn_input[‘prevtxnindex’]`

`sgntxnin_b = prevtx_rb + struct.pack(‘<L’, prevtxnindex)`

`if txn_input[‘script_type’] == ‘P2SH_Multisig’:`

`scriptSig_b = createScriptSigForMultiSig(signgrp, script_b)`

`elif txn_input[‘script_type’] == ‘P2PKH’:`

`scriptSig_b = createScriptSigForP2PKH(txn_input, signgrp)`

`sgntxnin_b += createVarInt(len(scriptSig_b)) + scriptSig_b`

`return sgntxnin_b`

`# In P2PKH script scriptSig is signature + pubkey`

`def scriptSigFromSignNPubkey(sign_b: bytes, pubkey_b: bytes):`

`scriptSig_b = getWithPushdata(sign_b)`

`scriptSig_b += getWithPushdata(pubkey_b)`

`return scriptSig_b`

`def createSignedTransaction(txn_struct: dict, signgrp_l: list, script_l: list):`

`sgntxn_b = b’’`

`sgntxn_b += struct.pack(‘<L’, txn_struct[‘version’])`

`sgntxn_b += createVarInt(txn_struct[‘input_count’])`

`for i in range(txn_struct[‘input_count’]):`

`txn_input = txn_struct[‘inputs’][i]`

`sgntxn_b += createSignedInput(txn_input, signgrp_l[i], script_l[i])`

`sgntxn_b += getSequence(txn_struct)`

`sgntxn_b += createVarInt(txn_struct[‘out_count’])`

`for out in range(txn_struct[‘out_count’]):`

`satoshis = txn_struct[‘outputs’][out][‘satoshis’]`

`sgntxn_b += struct.pack(‘<Q’, satoshis)`

`address = txn_struct[‘outputs’][out][‘address’]`

`scriptPubkey_b = getScriptPubkeyFromAddress(address)`

`sgntxn_b += createVarInt(len(scriptPubkey_b))`

`sgntxn_b += scriptPubkey_b`

`sgntxn_b += struct.pack(‘<L’, txn_struct[‘locktime’])`

`return sgntxn_b`

**Program 10.20:** Create signed transaction

Now, we can create a transaction for both P2PKH and P2SH and publish it on the Bitcoin network. For this, we will require private keys, public keys, and addresses.

We generate the keys and addresses using the method described in *[Chapter 9, Wallets and Addresses](#c09.xhtml),* **under** the s**ubtopic** *Format and generation of private key, publickey, and address*.

We will use the following private key, public key, and addresses:

 
| **Private Keys** || **Public Keys** || **Addresses** |
| --- | --- | --- |
| KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53 || 0281238fc6d981efce6aa1b3ccb8556a1b115a40f8ab3315c003f415ceedc3defe || msMV395AdBAk2SfdDhBLq4uJZRS7doCn5T |
| L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ || 037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7 || n1WvYkKU9i5RymcHeKFT4UworwqS6BKFSf |
| KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG || 02fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d0 || miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo |
| KyWeQEcM2YdirR2E7JwxSRjfgNuWyt4DR3v4sGtPvmeZqhTxWVrp || 02d50250aa629914e3146a 5123a362a516c8aa95e5f0a6f3a078bd31fabe383abc || msV23rBcHAtQWSkWV9ph91DV65VduWi1Vt |
| Ky5CYfpeMkfFku7K4FvzeEwRmTJhWqD2eFiMnjLT7uw2oUVMgyg6 || 0319b4b9ab4732e78dab0e48c2c54fd57dd35350a0269f8c041807c3b798aa1872 || mnhWcUMqe9J1G4t3NMqNmLUqxfPTgwv7NK |
| L1cnATDVZyvuo9m6tprCmbr14vm3JeCbkc4Z2397ZM7P96N3d8GA || 039d5dbb6e052631c46e046c6d11fb95d257eae5093117d2c265aeb784dba4acf6 || mtRkMmpT6uhM9LXVPRk4ck9Gcaz9iuQgmZ |
| KyP1xynRgwrCUThXATVy5kbKqteAxisDFY74zrHozSGhb75hJ3M6 || 02dfa818542ab4685284f7c222d541e218aed0712fc9e63ca2802b15bb418383c9 || n2DfL6uEmPiwJBYjJRzyqUYDSTqxF8XSNS |

**Table 10.3:** Few test addresses, public keys, and private keys

We start the Bitcoin Core daemon for `regtest` as shown here:

`bitcoind -regtest -printtoconsole –rpcuser=test –rpcpassword=test -txindex=1`

# [Building P2PKH transaction](#toc.xhtml#s226a)

We then connect the daemon and generate two blocks, sending bitcoin to a particular `regtest` address.

To do this, run Bitcoin Core CLI with the `regtest` option, giving optional parameters `rpcuser` and `rpcpassword`. The `rpcuser` and `rpcpassword` options allow a client to make `rpc` connections. This is required for connecting using Python package but not for connecting using CLI.

In the following CLI statement, we are generating two blocks, and each newly created block pays 50![](images/Bitcoin.jpg)to the given address. The payment transactions are coinbase transactions that are included in each generated block.

![](images/Figure-10.12.jpg)

**Figure 10.12:** Shows the generated blocks that pay to the given address

We get the coinbase transactions from the block hashes:

![](images/Figure-10.13.jpg)

**Figure 10.13:** Shows the coinbase transactions of the generated blocks

So, we have two transactions now holding 50 regtest bitcoins each:

`5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f`

`53793974d074e57305575d711fd0acd1d39f406264de234e686542ad2d0ddbfb`

We also get `scriptPubKey` from the first transaction output as follows:

![](images/Figure-10.14.jpg)

**Figure 10.14:** Shows the scriptPubKey obtained from the first output of funding transaction

Now, we have two blocks in the blockchain each with 50![](images/Bitcoin.jpg). There is a rule that a coinbase transaction cannot be spent for the next 100 blocks. This rule is useful if there is an attack on the network or if there is any critical bug and it becomes necessary to reorg the Bitcoin blockchain. This means we need to invalidate the previous version of the software, which has mined recent blocks, and deploy the new software, which fixes the issue. We may also need to invalidate some blocks that are already mined. The 100 blocks give nearly 16 hours to developers to fix the network. In the past, Bitcoin developers had to perform reorg twice once in 2010 and once in 2013. This obviously affects the creditability of the network, and we don’t want it to happen again.

We will just mine another 100 blocks, as follows, to be able to use the preceding transactions:

![](images/Figure-10.15.jpg)

**Figure 10.15:** Shows the commpand executed to generate 100 blocks

We will use the locked bitcoins in two transactions and send them to two different addresses and leave 0.0001 regtest bitcoins as network fees. We first create a raw transaction without a signature. The following code defines the structure of the raw transaction:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 2`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = \`

`‘5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2PKH’`

`input0[‘privkeys’] = [‘KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53’]`

`input0[‘script_pubkey’] = ‘76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac’`

`input0[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input0)`

`input1 = {}`

`input1[‘prevtxn’] = ‘53793974d074e57305575d711fd0acd1d39f406264de234e686542ad2d0ddbfb’`

`input1[‘prevtxnindex’] = 0`

`input1[‘script_type’] = ‘P2PKH’`

`input1[‘privkeys’] = [‘KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53’]`

`input1[‘script_pubkey’] = ‘76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac’`

`input1[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input1)`

`txn[‘out_count’] = 2`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 40*(10**8)`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 599999*(10**4)`

`output1[‘script_type’] = ‘P2PKH’`

`output1[‘address’] = ‘miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo’`

`txn[‘outputs’].append(output1)`

`txn[‘locktime’] = 110 # block height`

`return txn`

**Program 10.21:** Method creating transaction structure to be used as input for P2PKH transaction creation

We call the methods to get signed transaction using the following code:

`if __name__ == ‘__main__’:`

`txn_struct = createTransactionStruct()`

`txn_struct, signgrp_l, script_l = getSignaturesAndExecScripts(txn_struct)`

`signed_txn_b = createSignedTransaction(txn_struct, signgrp_l, script_l)`

`print(signed_txn_b.hex())`

Here’s the signed transaction:

![](images/Figure-10.16.jpg)

**Figure 10.16:** Shows the signed transaction created by the program

We start the Bitcoin Core daemon for `regtest` by using the *–*`regtest` option. We execute the client as follows:

![](images/Figure-10.17.jpg)

**Figure 10.17:** Shows the transaction failed to publish

We got an error message non-final because locktime is higher than the current block count:

![](images/Figure-10.18.jpg)

**Figure 10.18:** Shows the command to get latest block height

We create 8 more blocks and then publish the transaction again:

![](images/Figure-10.19.jpg)

**Figure 10.19:** Shows the transaction is published once the locktime condition is fulfilled

This time, the transaction was successfully published, and we got the transaction ID:

`efc4b90d71ff1e726924a5719fdbe9a548910aae20988c3dfa398575992100d6`

We can see the transaction that was published by executing the following command:

![](images/Figure-10.20.jpg)

**Figure 10.20:** Shows transaction hex data in mempool using Bitcoin Core CLI command

To get this transaction into the block, we generate another block, as follows:

![](images/Figure-10.21.jpg)

**Figure 10.21:** Shows the next block is mined

Now, we can see that the published transaction is added to the new block:

![](images/Figure-10.22.jpg)

**Figure 10.22:** Shows the transaction in mined in the next block

We can see that on generating a block, the new transaction we created is added to the newly generated block. Now, the transaction is confirmed, and its depth is 1.

The next section will explain the creation and publishing of P2PKH transactions.

# [Building P2SH transaction](#toc.xhtml#s227a)

In this section, we will create a transaction and publish it. To do that, we need to generate a block that pays to a P2SH address. The P2SH address is generated by generating hash160 of redeem script.

We use the following method to generate redeem script:

`OP_CHECKMULTISIG = 0xae`

`def createRedeemScript(pubkey_l: list, sigcount: int):`

`redeem_script_b = bytes([0x50 + sigcount])`

`for pubkey in pubkey_l:`

`pubkey_b = bytes.fromhex(pubkey)`

`redeem_script_b += encodePushdata(len(pubkey_b)) + pubkey_b`

`redeem_script_b += bytes([0x50 + len(pubkey_l), OP_CHECKMULTISIG])`

`return redeem_script_b`

**Program 10.22:** Method to create redeem scripts for multisig

We are creating redeem script, which requires two signatures using private keys related to the three public keys. So, we are going to use 2-of-3 `multisig`.

We pass three public keys, and the required count of signature is 2 in the following code:

`if __name__ == ‘__main__’:`

`pubkey_l = [‘037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7’, ‘02fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d0’, ‘02d50250aa629914e3146a5123a362a516c8aa95e5f0a6f3a078bd31fabe383abc’]`

`redeem_script_b = createRedeemScript(pubkey_l, 2)`

`print(‘redeem script = %s’ % redeem_script_b.hex())`

`sh = hash160(redeem_script_b)`

`address = sh2address(sh)`

`print(‘P2SH address = %s’ % address)`

On executing the preceding lines of code, we get the following result:

![](images/Figure-10.23.jpg)

**Figure 10.23:** Shows the P2SH address generated using redeem script

We use the preceding address to generate a block and receive bitcoin, as follows:

![](images/Figure-10.24.jpg)

**Figure 10.24:** Shows the generated block that pays to the P2SH address

Next, we use the blockhash in the preceding Bitcoin Core CLI command to get the transaction-ID of the coinbase transaction:

![](images/Figure-10.25.jpg)

**Figure 10.25:** Shows the coinbase transaction that will pay to the P2SH transaction

We need to get the structure of the generated transaction since we need to use the transaction output in a transaction.

We get raw transaction by executing the following command:

![](images/Figure-10.26.jpg)

**Figure 10.26:** Shows the hex data of the coinbase transaction that pays to the P2SH address

By executing the following command, we get transaction structure from the raw transaction:

![](images/Figure-10.27.jpg)

**Figure 10.27:** Shows the command to get content in the transaction hex data

The following is the structure of the raw transaction generated from the preceding command:

![](images/Figure-10.28.jpg)

**Figure 10.28:** Shows the decoded transaction data

We create a transaction structure using the transaction IDs of generated transaction for P2SH transaction, as follows:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = \`

`‘de32b06aeb0103381df84d2cc5ea80a35b60bce0c6393bd9436cb395e3f47a5d’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2SH_Multisig’`

`input0[‘privkeys’] = \`

`[‘L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ’,`

` ‘KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG’]`

`input0[‘redeem_script’] = ‘5221037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f72102fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d02102d50250aa629914e3146a5123a362a516c8aa95e5f0a6f3a078bd31fabe383abc53ae’`

`input0[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 2`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 10*(10**8)`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 399999*(10**4)`

`output1[‘script_type’] = ‘P2PKH’`

`output1[‘address’] = ‘miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo’`

`txn[‘outputs’].append(output1)`

`txn[‘locktime’] = 0 # block height`

`return txn`

`if __name__ == ‘__main__’:`

`txn_struct = createTransactionStruct()`

`txn_struct, signgrp_l, script_l = getSignaturesAndExecScripts(txn_struct)`

`signed_txn_b = createSignedTransaction(txn_struct, signgrp_l, script_l)`

`print(signed_txn_b.hex())`

**Program 10.23:** Method creating transaction structure to be used as input for P2SH transaction creation

This gives the following signed transaction:

![](images/Figure-10.29.jpg)

**Figure 10.29:** Shows the signed transaction moving bitcoin from P2SH address

We need to mine 100 blocks before we can fund a transaction from coinbase transaction output, so we will again execute CLI command `generatetoaddress`. Before publishing a transaction, we can test whether a transaction is valid. We can do it by running the following Bitcoin CLI command:

![](images/Figure-10.30.jpg)

**Figure 10.30:** Shows if the transaction is valid and is acceptable to mempool

We can see that the transaction is valid, and if sent, will be accepted by the mempool. If we were working on real bitcoin, this command could save us by verifying that everything is just fine.

Now, we can publish the transaction as follows:

![](images/Figure-10.31.jpg)

**Figure 10.31:** Shows the transaction moving bitcoin from P2SH address is published

We got `66ce54d909c9309d8bee5035b261c639ee8e274947b15a6ea2d540a12beea5d2` as the transaction ID. So, we were able to successfully build and publish P2SH transaction.

In this section, you learned to build and publish transaction using information provided in a transaction structure.

This brings us to the end of the chapter.

# [Conclusion](#toc.xhtml#s228a)

In this chapter, you learned about the Bitcoin scripting language, its features, and its execution. You learned how the scripting language is used in transaction verification. You learned about the different types of Scripts used by Bitcoin and understood the why and how of Bitcoin scripting. Additionally, you learned to create a transaction and publish it to the Bitcoin network. The chapter involved quite a bit of coding.

In the next chapter, you will learn and create smart contracts and other useful transactions.

# [Points to remember](#toc.xhtml#s229a)

*   Bitcoin transactions are secured by locking scripts that contain a hash, and if we want to use the transaction to fund the newly created transaction, then we need to present the corresponding script or public key.
*   To create a new transaction, we also need to provide a signature by signing a message based on the format required by the script type and hash-type.
*   Bitcoin scripting language is based on R*everse Posix* n*otation*.
*   When a node receives a newly created transaction, it needs to verify it against consensus rules and needs to verify that the `scriptSig` used to unlock funds locked by `scriptPubKey`.
*   For the P2PKH script, `scriptSig` gets executed first, and then the same stack is used to execute the `scriptPubKey` from the previous transaction output. The result is at the top of the stack.
*   For the P2SH script in the first pass, `scriptSig` is executed, and then `scriptPubKey` is executed. In the third pass, the signatures are first pushed to the stack, and then redeem script is executed.
*   The newly created transaction can be published to the Bitcoin network by using the Bitcoin Core command `sendrawtransaction`.
*   If you don’t want to maintain a full node, you can still publish the newly created transaction using SPV software. Additionally, several online sites can push the new transactions.
*   Before sending the transaction, we can decode it using the Bitcoin Core command `decoderawtransaction`, allowing us to manually verify the transaction we created.
*   We can also check that the created transaction is valid by using the Bitcoin Core command `testmempoolaccept`.
*   P2PKH and P2SH scripts hide public keys till the locked funds are used in a transaction.
*   Scripting language provides a large number of operations that can be used to write complex smart contracts, but P2SH hides those complexities from the sender.

# [Questions](#toc.xhtml#s230a)

1.  Write programs to create transactions: 
    1.  Create a P2PKH transaction with three inputs and three outputs; all of them have sighash type as SIGHASH\_ALL|SIGHASH\_ANYONECANPAY.
    2.  Create a P2PKH transaction with three inputs and three outputs. Two inputs have sighash type as SIGHASH\_NONE|SIGHASH\_ANYONECANPAY, and the third input has sighash type SIGHASH\_ALL.
    3.  Create a P2PKH transaction with three inputs and three outputs. Two inputs have sighash type as SIGHASH\_SINGLE|SIGHASH\_ANYONECANPAY, and the third input has sighash type SIGHASH\_ALL
2.  Write a generic program to convert the hex code of any Bitcoin transaction script to a readable script.
3.  Why should all transactions have at least one input signed with SIGHASH\_ALL?
4.  Calculate the transaction fees for a transaction that unlocks two P2PKH outputs from the previous transactions and locks output to two P2PKH scripts if the transaction fee per byte is 10 satoshi per byte.
5.  Choose the right sighash type: 
    
    1.  SIGHASH\_NONE|SIGHASH\_ANYONECANPAY
    2.  SIGHASH\_SINGLE|SIGHASH\_ANYONECANPAY
    3.  SIGHASH\_ALL|SIGHASH\_ANYONECANPAY
    
    1.  Renuka got a job in a different country. Her friends planned and jointly bought a watch from a shop that accepts bitcoin as payment.
    2.  A social service organization is buying clothes and food for earthquake victims. It requires people to contribute to them by giving signed transaction inputs.
    3.  A school wants to send its bright student to participate in a national academic conference. The participation fees are high, and the school wants to help the parents by subsidizing the cost of participation.
6.  True/False: 
    1.  P2SH script of 1-of-1 multisig is not valid.
    2.  P2PKH does not allow the use of an uncompressed public key.
    3.  When creating a signature, we get two values of S, of which we select the smaller value of S.
7.  Fill in the blanks: 
    1.  An exchange platform works as an escrow between buyers and sellers of bitcoin. A seller locks their bitcoin such that if any two among buyer, seller, and escrow agrees that the seller has received money then the bitcoin is released to the buyer. The platform implements \_\_\_\_\_ of \_\_\_\_\_ multisig.
    2.  An address is related to P2PKH or P2SH script can be determined by looking at \_\_\_\_\_\_\_\_\_\_ of address which is \_\_\_\_\_ for mainnet P2PKH and \_\_\_\_\_\_\_ for mainnet P2SH script.
    3.  A P2SH script is verified after executing \_\_\_\_\_\_\_\_\_\_\_ script in addition to scriptSig and scriptPubKey.

# [CHAPTER 11](#toc.xhtml#c11)

# [Smart Contract and Other Useful Transactions](#toc.xhtml#c11)

In the previous chapter, you learnt to verify and create transactions. You also learnt how to check their inputs and outputs and correctness before publishing and understood the different ways to publish a transaction. In this chapter, you will learn scripting in more detail. You will learn how simple but interesting use cases can be implemented using scripting language and other properties of Bitcoin transactions.

When we think about smart contract, we think about Ethereum, Cardano, Binance Smart Chain, etc. We ignore the network that pioneered in smart contract, which is Bitcoin. Bitcoin is the most secure cryptocurrency network. As smart contract and digital properties might be very valuable, securing them on Bitcoin network could be the best option if it is technically feasible.

In this chapter, we will go deeper into scripting and build use cases for a few useful smart contracts using Bitcoin scripting language. We will also implement some other use cases that are not contracts between parties but are useful in solving real requirements.

# [Structure](#toc.xhtml#s231a)

In this chapter, we will cover the following topics:

*   Script opcodes
*   Digital property 
    *   Document timestamping
*   Time locked transactions 
    *   Time locked payment
    *   Payment with relative locktime
*   Smart contract 
    *   Solution to trust issue in payments 
        *   Simple multi-signature payment
        *   Improved payment with relative locktime
        *   Payments involving escrow
    *   Payment involving secret identifier
*   Collaborative transactions 
    *   Charity use case
    *   Subsidy use case
    *   Planned contribution within a group

# [Objectives](#toc.xhtml#s232a)

The objective of this chapter is to help you understand the broader scope of Bitcoin scripting language. Additionally, it will help you learn to create transactions for different scenarios, including smart contract and other useful transactions that were not covered in the previous chapters.

# [Script opcodes](#toc.xhtml#s233a)

In the previous chapter, we used only a few opcodes that are used in standard P2PKH and m-of-n-multisig P2SH scripts. While these are sufficient for basic money transfers between individuals and groups, a more complex script might be needed. In this chapter, we will use a few more opcodes.

# [Digital property](#toc.xhtml#s234a)

Digital asset or digital property is the digital representation of an asset. The property can be represented as QR code or identifier or hash of specification or value. The asset ownership can be changed by the owner of the asset. It can also be lent or rented online. Using Bitcoin transaction and scripting language, we can implement some of those features. Timestamping is one of the important properties of digital asset management, which we will cover in this subtopic.

# [Document timestamping](#toc.xhtml#s235a)

Timestamping a document is necessary for it to be legally binding and for it to be part of a contract. Transactions in a block can be associated with the timestamp of the block, and it is immutable. If a transaction holds hash of the content of a document, then we can consider the document as timestamped. However, for this to be legally binding, governments need to recognize Bitcoin blockchain as both immutable and having the correct timestamp.

The following is a short story written by my daughter, for which we are generating a hash and will add it to a transaction:

Best Friend Lunch Party: One day two best friends, a monkey and a crocodile decided to have lunch together in a farm. The next day, they passed the river and reached the farm. After a heavy meal the monkey got up and started growling loudly. The frightened crocodile pleaded the monkey to stop. But the monkey said, ‘I have a habit of growling after every meal, I cannot help it’. The monkey was on the crocodile’s back while crossing the river back home. When they were halfway through the river, the crocodile took a dip in the water. When the monkey was frightened, the crocodile said, ‘I have a habit of taking a dip in the water after every meal, I cannot help it’. Monkey understood his mistake.

SHA256 of this story:

`3365b392ee14def189190638a532f6042446b74c98f186e9b595f77e47817e05`

The following is the code to get the hash of the preceding story:

`def contentHash(story: str):`

`content_h = hashlib.sha256(story.encode(‘ascii’)).digest()`

`return content_h`

To add this to a transaction, we need to pay a small network fee, transfer bitcoins from one address to another, and use `OP_RETURN` to capture the above hash.

We generate the first block and send the newly mined bitcoins to an address as shown in *[figure 11.1](#c11.xhtml#fig11_1)*:

![](images/Figure-11.1.jpg)

**Figure 11.1:** Generated Block hash

The following are the transactions included in the newly mined block:

![](images/Figure-11.2.jpg)

**Figure 11.2:** Transaction ID of coinbase transaction

In *[Chapter 10, Create and Validate Transactions](#c10.xhtml)* under the topic *Building P2PKH transaction*, we have created P2PKH transaction with two inputs and two outputs. We modify the code to also support `OP_RETURN` output.

This is the code that provides transaction structure to the transaction builder program:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = ‘5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2PKH’`

`input0[‘privkeys’] = [‘KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53’]`

`input0[‘script_pubkey’] = ‘76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac’`

`input0[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 2`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 4999900000`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 0`

`output1[‘script_type’] = ‘OP_RETURN’`

`output1[‘content_hash256’] = ‘3365b392ee14def189190638a532f6042446b74c98f186e9b595f77e47817e05’`

`txn[‘outputs’].append(output1)`

`txn[‘locktime’] = 0`

`return txn`

**Program 11.1:** Transaction structure definition of document timestamping

The following is the value of OP\_RETURN opcode:

`OP_RETURN = 0x6a`

In *[Chapter 10, Create and Validate Transactions](#c10.xhtml)* under topic ***Building transactions*** we have defined method `createSignaturePreimage and createSignedTransaction`. We add following lines to the method to handle OP_RETURN script type:

`if outp[‘script_type’] == ‘OP_RETURN’:`

`content_b = bytes.fromhex(outp[‘content_hash256’])`

`scriptPubkey_b = bytes([OP_RETURN]) \`

` + getWithPushdata(content_b)`

As we did in *[Chapter 10, Create and Validate Transactions](#c10.xhtml)*, we execute this program and get raw transaction hex code, as shown in *[figure 11.3](#c11.xhtml#fig11_3)*:

![](images/Figure-11.3.jpg)

**Figure 11.3:** Hex code of transaction created for document stamping

The following is the output of the newly created transaction:

![](images/Figure-11.4.jpg)

**Figure 11.4:** Output of transaction created for document timestamping

Now, we need to mine another 100 blocks so that the mined bitcoins we are using are ready for transfer:

![](images/Figure-11.5.jpg)

**Figure 11.5:** Next 100 blocks are mined

Now, publish the newly created transaction:

![](images/Figure-11.6.jpg)

**Figure 11.6:** Publish transaction for document timestamping

Now, we mine a single block again to add the transaction to the newly mined block:

![](images/Figure-11.7.jpg)

**Figure 11.7:** Mine the next block to include published transaction

The following in the newly mined block. We can see that the block contains the newly added transaction:

![](images/Figure-11.8.jpg)

**Figure 11.8:** Published transaction appears in the new block

# [Time locked transactions](#toc.xhtml#s236a)

Bitcoin allows you to lock a transaction for certain time or block height. It allows transactions to be locked in a fixed time or time relative to the funding transaction.

In the following subsections, we will cover a use case for both fixed and the relative timelock.

# [Time locked payment](#toc.xhtml#s237a)

We can also create transactions that cannot be spent before given timestamp. This is done by setting the nLockTime field in a transaction. The nLockTime field can either be set to denote block height or to denote Unix epoch time. In the case of epoch time, it denotes mean time past instead of the block’s timestamp.

The `nLockTime` field has the following rules:

*   `nLockTime` < 500000000 denotes block-height
*   Otherwise, it denotes median time past

It is recommended that `nLockTime` is not set to zero or past block height or past block-time.

*Median time past = Medium of (Tn-1, Tn-2, Tn-3, Tn-4, … Tn-10, Tn-11)*

The following code provides transaction structure to the transaction builder program:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = ‘5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2PKH’`

`input0[‘privkeys’] = [‘KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53’]`

`input0[‘script_pubkey’] = ‘76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac’`

`input0[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 1`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 4999900000`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ’`

`txn[‘outputs’].append(output0)`

`txn[‘locktime’] = 1624196667`

`return txn`

**Program 11.2:** Transaction structure definition of time locked payment

We get the following signed transaction for the preceding transaction structure:

![](images/Figure-11.9.jpg)

**Figure 11.9:** Create transaction for time locked payment

To be able to publish the preceding transaction, the bitcoin in the newly created block needs to be available for spend. For this, we create another 100 blocks.

We now try to publish the transaction, as shown in *[figure 11.10](#c11.xhtml#fig11_10)*:

![](images/Figure-11.10.jpg)

**Figure 11.10:** Publishing the time locked transaction fails

Publishing of the transaction fails as the block median timestamp is smaller than the locktime we have set:

![](images/Figure-11.11.jpg)

**Figure 11.11:** Current timestamp and last block timestamp

The median timestamp is calculated by taking the median of the timestamp in a block for the last 11 blocks. To get the median timestamp value as a value greater than the locktime set in the transaction, we wait for a few minutes and create another 11 blocks:

![](images/Figure-11.12.jpg)

**Figure 11.12:** Mine next eleven block to change median time past

Now, the median time of the last generated block is as follows:

![](images/Figure-11.13.jpg)

**Figure 11.13:** Get median time past

This timestamp is greater than 1624196667:

![](images/Figure-11.14.jpg)

**Figure 11.14:** Median time past to date

We again try publishing the transaction:

![](images/Figure-11.15.jpg)

**Figure 11.15:** Publishing the transaction is now successful

We can see that the transaction was not valid until the median timestamp of the latest block was not less than or equal to lock-time.

# [Payment with relative locktime](#toc.xhtml#s238a)

The `nLockTime` field in a transaction is set for static block height or static epoch time. If the newly created transaction needs to wait for time or block count relative to block count or timestamp of depending block, then we use `OP_CHECKSEQUENCEVERIFY`.

The relative lock-time contract is implemented using the `OP_CHECKSEQUENCEVERIFY` opcode as a script, so we use P2SH with redeem script. The opcode requires that the sequence is set for the corresponding transaction input.

The relative locktime was a softfork, which required version number of transactions to be set as 2. It also led to changes in the way `nSequence` is evaluated.

Prior to the softfork:

*   If nSequence is 0xFFFFFFFE, it denotes that nLockTime is set.
*   If nSequence is 0xFFFFFFFF, it denotes that nLockTime is not set.

The following illustration shows the way nSequence is evaluated post softfork:

![](images/Figure-11.16.jpg)

**Figure 11.16:** Illustration of nSequence evaluation

Listed here are the conditions based on which sequence value needs to be set:

*   If nSequence > 0xEFFFFFFF, then it is not defined and so, the transaction can be included in any block.
*   If nSequence <= 0xEFFFFFFF, then bit-22 determines if 0-15 bits denote block height or timestamp. 
    *   If bit-22 is set, then 0-15 bits denote block height.
    *   If bit-22 is not set, then 0-15 bits denotes medium time past.

This is implemented in the following code:

`def getSequence(txn_struct: dict, i: int):`

`inp = txn_struct[‘inputs’][i]`

`if ‘sequence_type’ in inp:`

`if inp[‘sequence_type’] == ‘time’:`

`sequence = inp[‘sequence’] | (1 << 22)`

`else:`

`sequence = inp[‘sequence’]`

`sequence_b = struct.pack(‘<L’, sequence)`

`else:`

`if txn_struct[‘locktime’] > 0:`

`# sequence`

`sequence_b = bytes([0xfe, 0xff, 0xff, 0xff])`

`else:`

`# sequence`

`sequence_b = bytes([0xff, 0xff, 0xff, 0xff])`

`return sequence_b`

**Program 11.3:** Method to calculate nSequence

To implement a simple use case with relative lock-time, in our use case, a newly created transaction can only be mined 105 blocks after the funding transaction are confirmed.

Here’s the redeem script for the transaction:

`# 105 OP_CHECKSEQUENCEVERIFY OP_DROP`

`# <Alice pubkey> CHECKSIG`

These are the opcodes we require in this transaction:

`OP_CHECKSEQUENCEVERIFY = 0xb2`

`OP_DROP = 0x75`

`OP_CHECKSIG = 0xac`

The following code is used to generate redeem script hex code:

`def createRedeemScript(pubkey_alice: str):`

`redeem_script_b = bytes([0x01,`

`105, # after 105 blocks`

`OP_CHECKSEQUENCEVERIFY, OP_DROP])`

`pubkey_b = bytes.fromhex(pubkey_alice)`

`redeem_script_b += createVarInt(len(pubkey_b)) + pubkey_b`

`redeem_script_b += bytes([OP_CHECKSIG])`

`return redeem_script_b`

**Program 11.4:** Method to create redeem script for relative lock-time

We call the preceding method as follows:

`if __name__ == ‘__main__’:`

`pubkey_alice = ‘037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7’`

`redeem_script_b = createRedeemScript(pubkey_alice)`

`print(‘redeem script = %s’ % redeem_script_b.hex())`

`sh = hash160(redeem_script_b)`

`address = sh2address(sh)`

`print(‘P2SH address = %s’ % address)`

We execute it and get following result:

![](images/Figure-11.17.jpg)

**Figure 11.17:** Generate Redeem script for relative timelock

We generate a block to pay to the contract indicated by the preceding redeem script and then get the transaction ID:

![](images/Figure-11.18.jpg)

**Figure 11.18:** Transaction ID for relative timelock funding transaction

We now create a new transaction using the following code:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 2`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = \`

`‘e6a31b5c7e39a31bb12c68055c1dd6dcb6554d1546a8621e889f1026e10264c8’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2SH_RelativeTimeLock’`

`input0[‘privkeys’] = \`

`[‘L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ’]`

`input0[‘redeem_script’] = ‘0169b27521037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7ac’`

`input0[‘hash_type’] = SIGHASH_ALL`

`input0[‘sequence’] = 105`

`input0[‘sequence_type’] = ‘block’`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 2`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 10*(10**8)`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 399999*(10**4)`

`output1[‘script_type’] = ‘P2PKH’`

`output1[‘address’] = ‘miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo’`

`txn[‘outputs’].append(output1)`

`txn[‘locktime’] = 0`

`return txn`

**Program 11.5:** Method to create transaction for relative lock-time

To claim the locked funds in the previous transaction, we provide `scriptSig`, which consists of the required signature along with redeem script. Here’s the code for `scriptSig`:

`def createScriptSigForRelTimeLock(signgrp: list, script_b: bytes):`

`scriptSig_b = getWithPushdata(signgrp[0])`

`scriptSig_b += getWithPushdata(script_b)`

`return scriptSig_b`

**Program 11.6:** Method to create scriptSig for relative lock-time

In *[Chapter 10, Create and Validate Transactions](#c10.xhtml)* under topic ***Building transactions*** we have defined method `createSignedInput`. We add following lines to the method to handle *relative-timelock* script type:

`elif txn_input[‘script_type’] == ‘P2SH_RelativeTimeLock’:`

`scriptSig_b = createScriptSigForRelTimeLock(signgrp, script_b)`

We execute the code and get the signed raw transaction:

![](images/Figure-11.19.jpg)

**Figure 11.19:** Create hex code for relative timelock transaction

If we publish the preceding transaction before 105 blocks are mined, we get the following error:

![](images/Figure-11.20.jpg)

**Figure 11.20:** Publishing relative timelock transaction before the required block height

Once we have mined 105 blocks after the input transaction, we can publish the preceding transaction:

![](images/Figure-11.21.jpg)

**Figure 11.21:** Publishing relative timelock transaction after the required block height

# [Smart contract](#toc.xhtml#s239a)

*Smart Contract* is a contract between two or more parties that is written in the form of an executable computer program. It executes only when the contract allows its execution, and on execution, smart contract follows the conditions defined in the contract.

Bitcoin provides a primitive scripting language based on reverse polish notation. The script is not Turing complete, which means it cannot solve all computational problems. Since smart contracts are contracts modelled in a program, they can become more complex with loops and state variables that the Bitcoin script does not allow.

It has a large number of opcodes that can be used to create a variety of smart contracts. Even though there are large number of opcodes, not everything can be done by scripting.

Additionally, Bitcoin transaction itself imposes limitations on the scripts. And since Bitcoin transaction fee is calculated based on per vBytes and is reasonably high, a complicated and large redeem script can make a smart contract financially non-viable.

Here are some of the limitations of smart contract on Bitcoin:

*   In a transaction, smart contract can only affect a single input. 
    *   A smart contract can only fund the transaction from a single UTXO that has a fixed value.
    *   Transaction outputs cannot be modified based on smart contract.
    *   Output scripts are standard and can only be one of the standard scripts such as P2SH, P2PKH, OP\_RETURN, P2PK, or P2MS and standard segwit scripts, which we will cover in the next chapter.
*   Bitcoin script is not a Turing complete language, and it does not have options to: 
    *   Have nondeterministic operations such as loops
    *   Work as a state machine and perform operations based on its state.
*   Bitcoin script is limited to the opcode it provides.
*   Scripting on Bitcoin is costly, and the complexity of a smart contract also depends on its financial viability.

# [Solution to trust issue in payments](#toc.xhtml#s240a)

We know that the simple method of payment is to transfer bitcoins to the recipient’s address. It would be done in your mobile wallet by scanning the QR code. This is great for small payments, but as the transaction fee has increased with increase in bitcoin price, making payments for low-priced goods is not financially viable.

For large value payments, we need to improve the security of payments. We will improve the security of payments in the following subtopics as we tackle one issue at a time.

# [Simple multi-signature payment](#toc.xhtml#s241a)

A 2-of-2-multisig between the buyer and seller is a way to secure payments when the trusted party needs to depend on the services provided by the non-trusted entity. As an example, consider a reputed business that needs to get a service from an unregulated small vendor.

In this case, the business locks funds in a 2-of-2-multisig address and only completes the payment once it has received the service from the small vendor. The locked funds act as the smart contract between the business and the vendor. This gives surety to the small vendor that they will get paid as there is no way the large business can take the money back.

# [Improved payment with relative locktime](#toc.xhtml#s242a)

The problem in the above payment use case is when the small vendor delays in providing the required service. They know that the funds are locked, so they can be bit careless about their job.

To solve this issue, there must be a way the business should be able to revoke. However, the business should not be able to revoke the payment at will. This can be achieved by relative lock-time so that both parties know that bitcoins are locked, but there is a time limit. If the vendor does not get service within time, it will get revoked.

The use case can be understood with the help of the following illustration. Here, Alice represents the trusted business, and Bob represents a small non-trusted vendor:

![](images/Figure-11.22.jpg)

**Figure 11.22:** Improved payment with relative lock time

To achieve this, we use the P2SH transaction with the following redeem script:

`#IF`

`# OP_2 <Alice’s pubkey> <Bob’s pubkey> OP_2 CHECKMULTISIG`

`#ELSE`

`# 105 CHECKSEQUENCEVERIFY DROP`

`# <Alice’s pubkey> CHECKSIG`

`#ENDIF`

In a normal condition, i.e., when there is no dispute, both sides sign the transaction that pays Bob. If there is a dispute, Alice waits for the timeout and then creates a transaction signed by her own private key, which transfers the locked amount to her address.

One thing to remember is that a condition once valid is always valid. So, if Alice wants to give extra time to Bob, she can still do it.

The following are the required opcodes to create redeem script:

`OP_2 = 0x52`

`OP_IF = 0x63`

`OP_ELSE = 0x67`

`OP_ENDIF = 0x68`

`OP_CHECKSEQUENCEVERIFY = 0xb2`

`OP_DROP = 0x75`

`OP_CHECKMULTISIG = 0xae`

`OP_CHECKSIG = 0xac`

Redeem script is used to generate the contract address where contract amount is locked. The following code is used to generate redeem script:

`def createRedeemScript2_2_seqcheck(pubkey_l: list):`

`redeem_script_b = bytes([OP_IF, OP_2])`

`for pubkey in pubkey_l: # Alice + Bob`

`pubkey_b = bytes.fromhex(pubkey)`

`redeem_script_b += createVarInt(len(pubkey_b)) + pubkey_b`

`redeem_script_b += bytes([OP_2, OP_CHECKMULTISIG])`

`redeem_script_b += bytes([OP_ELSE, 0x01,`

`105, # after 105 blocks`

`OP_CHECKSEQUENCEVERIFY, OP_DROP])`

`pubkey_b = bytes.fromhex(pubkey_l[0]) # Alice pubkey`

`redeem_script_b += createVarInt(len(pubkey_b)) + pubkey_b`

`redeem_script_b += bytes([OP_CHECKSIG, OP_ENDIF])`

`return redeem_script_b`

**Program 11.7:** Redeem script for payment with relative lock-time

We call the method using the following script:

`if __name__ == ‘__main__’:`

`pubkey_l = [‘037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7’, ‘02fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d0’]`

`redeem_script_b = createRedeemScript2_2_seqcheck(pubkey_l)`

`print(‘redeem script = %s’ % redeem_script_b.hex())`

`sh = hash160(redeem_script_b)`

`address = sh2address(sh)`

`print(‘P2SH address = %s’ % address)`

On calling the method, we get the following redeem script and address:

![](images/Figure-11.23.jpg)

**Figure 11.23:** Generate redeem script for payment with relative locktime

We generate a block to pay to this address:

![](images/Figure-11.24.jpg)

**Figure 11.24:** Generate block that pays redeem script

We get transaction ID from block hash:

![](images/Figure-11.25.jpg)

**Figure 11.25:** Get transaction-id from the generated block

We generate another 100 blocks so that this transaction is available for payment. As you have learnt, there are two possible outcomes of this contract.

Additionally, `OP_CHECKSEQUENCEVERIFY` was a soft-fork that needed the transaction version to be equal to or greater than 2. So, in the following transaction structure, we will use the version as 2:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 2`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = \`

`‘624d92839eb89104d0909df89f95785cb8bb77f0fec66c6c40cf3ad2804a3966’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2SH_Condition’`

`input0[‘condition’] = True`

`input0[‘privkeys’] = \`

`[‘L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ’,`

` ‘KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG’]`

`input0[‘redeem_script’] = ‘635221037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f72102fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d052ae670169b27521037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7ac68’`

`input0[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 2`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 10*(10**8)`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 399999*(10**4)`

`output1[‘script_type’] = ‘P2PKH’`

`output1[‘address’] = ‘miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo’`

`txn[‘outputs’].append(output1)`

`txn[‘locktime’] = 0 # block height`

`return txn`

**Program 11.8:** Method to create transaction for True condition

To the redeem script, we need to provide public keys of both Alice and Bob as in the normal multi-sig script. Here, we also need to provide `OP_1` or True to the script.

So, the `scriptSig` with included redeem script is as follows:

`#OP_0`

`#<Alice’s Signature>`

`#<Bob’s Signature>`

`#OP_1 (True)`

`#IF`

`# OP_2 <Alice’s pubkey> <Bob’s pubkey> OP_2 CHECKMULTISIG`

`#ELSE`

`# 105 CHECKSEQUENCEVERIFY DROP`

`# <Alice’s pubkey> CHECKSIG`

`#ENDIF`

We further add the following condition in the method `createSignedInput` to handle `script_type` *P2SH\_Condition* for the preceding conditional scripts:

`elif txn_input[‘script_type’] == ‘P2SH_Condition’:`

`scriptSig_b = createScriptSigForCond(signgrp,`

`script_b,`

`txn_input[‘condition’])`

We also create `scriptSig` for custom condition, as follows:

`OP_FALSE = 0x00`

`OP_TRUE = 0x51`

`#########################`

`#True Case`

`#OP_0`

`#<Alice’s Signature>`

`#<Bob’s Signature>`

`#OP_TRUE (True)`

`#########################`

`#False Case`

`#<Alice’s Signature>`

`#OP_FALSE (False)`

`#########################`

`#Needs to be customized based on use case`

`def createScriptSigForCond`(signgrp: `list`,

`script_b: bytes,`

`cond: bool):`

`if cond:`

`scriptSig_b = bytes([OP_0])`

`for sign_b in signgrp:`

`scriptSig_b += getWithPushdata(sign_b)`

`scriptSig_b += bytes([OP_TRUE])`

`scriptSig_b += getWithPushdata(script_b)`

`else:`

`scriptSig_b = encodePushdata(len(signgrp[0])) + signgrp[0]`

`scriptSig_b += bytes([OP_FALSE])`

`scriptSig_b += encodePushdata(len(script_b)) + script_b`

`return scriptSig_b`

**Program 11.9:** ScriptSig for condition handling

On executing the code, we get the following signed raw transaction:

![](images/Figure-11.26.jpg)

**Figure 11.26:** Create transaction hex code for payment with relative locktime

We decode the preceding script and get the following decoded script:

![](images/Figure-11.27.jpg)

**Figure 11.27:** ScriptSig in the transaction for payment with relative lock

We publish the transaction we just created as follows:

![](images/Figure-11.28.jpg)

**Figure 11.28:** Transaction for payment with relative lock is published

This shows how the script works in normal conditions. In the condition of dispute, the `OP_ELSE` condition gets executed, and we need to hold the transaction in the mempool till the `OP_CHECKSEQUENCEVERIFY` condition is met. If we publish the transaction before the due time, it gets rejected. For this, we need to additionally set sequence greater than 105.

So, we modify the transaction structure as follows:

`#2-of-2-multisig with condition`

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 2`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = \`

`‘624d92839eb89104d0909df89f95785cb8bb77f0fec66c6c40cf3ad2804a3966’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2SH_Condition’`

`input0[‘condition’] = False`

`input0[‘privkeys’] = \`

`[‘L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ’]`

`input0[‘redeem_script’] = ‘635221037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f72102fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d052ae670169b27521037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7ac68’`

`input0[‘hash_type’] = SIGHASH_ALL`

`input0[‘sequence’] = 110`

`input0[‘sequence_type’] = ‘block’`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 2`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 10*(10**8)`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 399999*(10**4)`

`output1[‘script_type’] = ‘P2PKH’`

`output1[‘address’] = ‘miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo’`

`txn[‘outputs’].append(output1)`

`txn[‘locktime’] = 0 # block height`

`return txn`

**Program 11.10:** Method to create transaction for False condition

On executing the modified code, we get the following signed transaction:

![](images/Figure-11.29.jpg)

**Figure 11.29:** Transaction for payment with relative lock is published

If we try to execute this script before 106 blocks are mined, we get the following error:

![](images/Figure-11.30.jpg)

**Figure 11.30:** Payment with relative lock fails to publish before required block height

But once 110 blocks are mined, we can publish it, as shown in the following screenshot:

![](images/Figure-11.31.jpg)

**Figure 11.31:** Payment with relative lock published after the required block height

You learnt how you can have conditional payments in the contract. Conditionals are an important part of a contract, and by learning this, we can think about more complex smart contracts.

# [Payments involving escrow](#toc.xhtml#s243a)

If both parties are not trustworthy, we need a trusted third party to resolve the dispute. This is like decentralized exchanges in which the buyers and seller gets into a trade, and when the payment is received by the seller, it releases bitcoin.

The following flowchart shows the steps and conditions involved in the entire payment process:

![](images/Figure-11.32.jpg)

**Figure 11.32:** Flow chart for payment involving escrow

For programming this, we only need to have 2-of-3-multisig instead of 2-of-2-multisig with relative timeout, which we discussed in the previous subtopic.

So, the new redeem script will be as follows:

`#IF`

`# OP_2 <Alice’s pubkey><Bob’s pubkey><escrow’s pubkey> OP_3 OP_CHECKMULTISIG`

`#ELSE`

`# 105 CHECKSEQUENCEVERIFY DROP`

`# <Alice’s pubkey> CHECKSIG`

`#ENDIF`

We will have this as an assignment for the readers.

# [Payment involving secret identifier](#toc.xhtml#s244a)

Consider a case where a secret agent is on a mission in the enemy territory. Some items need to be transferred to them so that the mission can be carried out. If they receive that package, then the mission is carried out; otherwise, it is aborted. To carry out the mission, they need to be paid. So, they can only claim the payment when they have received the package.

In this case, a contract needs to be created with a relative locktime and in successful condition, the agent needs to reveal the secret.

The following is the redeem script for the contract:

`#IF`

`# OP_SHA256 <secret_hash> OP_EQUALVERIFY`

`# <Agent’s pubkey> CHECKSIG`

`#ELSE`

`# 105 CHECKSEQUENCEVERIFY DROP`

`# <Agency’s pubkey> CHECKSIG`

`#ENDIF`

The following are the opcodes and their hex values:

`OP_2 = 0x52`

`OP_IF = 0x63`

`OP_ELSE = 0x67`

`OP_ENDIF = 0x68`

`OP_CHECKSEQUENCEVERIFY = 0xb2`

`OP_EQUALVERIFY = 0x88`

`OP_DROP = 0x75`

`OP_SHA256 = 0xa8`

`OP_CHECKSIG = 0xac`

**Program 11.11:** Opcodes used in redeem script for payment with secret

The following is the code to generate redeem-script:

`def createRedeemScriptWithSecretHash(pubkey_agency: str, pubkey_agent: str, secret_h: bytes):`

`redeem_script_b = bytes([OP_IF, OP_SHA256])`

`redeem_script_b += createVarInt(len(secret_h)) + secret_h`

`redeem_script_b += bytes([OP_EQUALVERIFY])`

`pubkey_b = bytes.fromhex(pubkey_agent)`

`redeem_script_b += createVarInt(len(pubkey_b)) + pubkey_b`

`redeem_script_b += bytes([OP_CHECKSIG])`

`redeem_script_b += bytes([OP_ELSE, 0x01,`

`105, # after 105 blocks`

`OP_CHECKSEQUENCEVERIFY, OP_DROP])`

`pubkey_b = bytes.fromhex(pubkey_agency)`

`redeem_script_b += createVarInt(len(pubkey_b)) + pubkey_b`

`redeem_script_b += bytes([OP_CHECKSIG, OP_ENDIF])`

`return redeem_script_b`

**Program 11.12:** Method to create redeem script for payment with secret

We call the method by passing public keys and secret, and generate address in the following code:

`if __name__ == ‘__main__’:`

`pubkey_agency = ‘037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7’`

`pubkey_agent = ‘02fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d0’`

`secret = ‘She sells seashells on the seashore’`

`secret_h = hashlib.sha256(secret.encode(‘utf-8’)).digest()`

`redeem_script_b = createRedeemScriptWithSecretHash(pubkey_agency, pubkey_agent, secret_h)`

`print(‘redeem script = %s’ % redeem_script_b.hex())`

`sh = hash160(redeem_script_b)`

`address = sh2address(sh)`

`print(‘P2SH address = %s’ % address)`

On calling the method and then generating address for the redeem script, we get the following:

![](images/Figure-11.33.jpg)

**Figure 11.33:** Redeem script for payment involving secret code

In the following screenshot, we generate a block to pay to the P2SH address and then get the transaction-id for the created coinbase transaction:

![](images/Figure-11.34.jpg)

**Figure 11.34:** Coinbase transaction-id for funding payment involving secret code

If the package reaches the agent, they can use the secret code to receive the payment. In that case, the True part of the condition in redeem script is executed. We create the transaction structure that provides secret as follows:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = \`

`‘5bdcb4a0ff46b4443cfa1ff8002a8ccff06e56a8100a259fbfbd4b0ab660d481’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2SH_WithSecret’`

`input0[‘privkeys’] = \`

` [‘KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG’]`

`input0[‘redeem_script’] = ‘63a82009b5eb7277b9d5062d91fe20f141ad4dd81970fd0baa72d31ee346a7c48d5b8c882102fcb1c7507db15576ab35cd7c9b1ea570141a8b81c9938dae0320392b0f7034d0ac670169b27521037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7ac68’`

`input0[‘secret’] = ‘She sells seashells on the seashore’`

`input0[‘condition’] = True`

`input0[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 2`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 10*(10**8)`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘mxzmMmVycLDgAA48VtHDeh389eDAwiJqwQ’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 399999*(10**4)`

`output1[‘script_type’] = ‘P2PKH’`

`output1[‘address’] = ‘miSFmBeKXf5Wp7Luj46XTu3Yh57nAwhZAo’`

`txn[‘outputs’].append(output1)`

`txn[‘locktime’] = 0 # block height`

`return txn`

**Program 11.13:** Method to create transaction for payment with secret

This is done by having the following `scriptSig`:

`#<Agent’s signature>`

`#<secret>`

`#OP_1`

`#IF`

`# OP_SHA256 <secret_hash> OP_EQUALVERIFY`

`# <Agent’s pubkey> CHECKSIG`

`#ELSE`

`# 105 CHECKSEQUENCEVERIFY DROP`

`# <Agency’s pubkey> CHECKSIG`

`#ENDIF`

This is done in the following code:

`def createScriptSigWithSecret(signgrp: list, script_b: bytes, secret: str, cond: bool):`

`if cond:`

`scriptSig_b = getWithPushdata(signgrp[0])`

`secret_b = secret.encode(‘utf-8’)`

`scriptSig_b += getWithPushdata(secret_b)`

`scriptSig_b += bytes([OP_TRUE])`

`else:`

`scriptSig_b = getWithPushdata(signgrp[0])`

`scriptSig_b += bytes([OP_FALSE])`

`scriptSig_b += getWithPushdata(script_b)`

`return scriptSig_b`

**Program 11.14:** Method to prepare scriptSig for the secret identifier use case

The scripts associated with each of the smart contracts discussed in this chapter may require separate handling of scriptSig. Each of these methods are added to `createSignedInput` method as a new condition.

To handle condition with secret discussed in this subtopic we further add the following condition in the method `createSignedInput` to handle `script_type` *P2SH\_WithSecret* for the preceding conditional scripts:

`elif txn_input[‘script_type’] == ‘P2SH_WithSecret’:`

`if txn_input[‘condition’]:`

`scriptSig_b = createScriptSigWithSecret(signgrp, script_b, txn_input[‘secret’], True)`

`else:`

`scriptSig_b = createScriptSigWithSecret(signgrp, script_b, ‘’, False)`

We execute the code and get signed raw transaction:

![](images/Figure-11.35.jpg)

**Figure 11.35:** Created transaction for payment involving secret code

This gives us the following `scriptSig`:

![](images/Figure-11.36.jpg)

**Figure 11.36:** ScriptSig of transaction for funding payment involving secret code

We publish it as follows:

![](images/Figure-11.37.jpg)

**Figure 11.37:** Transaction for payment involving secret code is published

# [Collaborative transactions](#toc.xhtml#s245a)

In some cases, there are multiple contributors of a single transaction. The contributors may not be aware of other parts of the transaction. So, they can only sign a portion of the transaction. This is done through different SIGHASH types.

In *[Chapter 10, Create and Validate Transactions](#c10.xhtml),* under the topic ***Signature*** *v****erification*,** you learnt about different SIGHASH types and their uses.

In a collaborative transaction, each party creates their transaction and sends it to a person or authority that has the responsibility to create and publish the final transaction.

For individual transactions, the following code contains the changes required to generate signature preimage:

`def createSignaturePreimage(txn_struct: dict,`

`script_b: bytes,`

`inp_index: int):`

`preimage_b = b’’`

`preimage_b += struct.pack(‘<L’, txn_struct[‘version’])`

`hashtype = txn_struct[‘inputs’][inp_index][‘hash_type’]`

`if hashtype & SIGHASH_ANYONECANPAY:`

`preimage_b += createVarInt(1)`

`inputs = [inp_index] # only current input is processed`

`else:`

`preimage_b += createVarInt(txn_struct[‘input_count’])`

`inputs = range(txn_struct[‘input_count’])`

`for i in inputs:`

`inp = txn_struct[‘inputs’][i]`

`preimage_b += bytes.fromhex(inp[‘prevtxn’])[::-1]`

`preimage_b += struct.pack(‘<L’, inp[‘prevtxnindex’])`

`if i == inp_index:`

`preimage_b += createVarInt(len(script_b))`

`preimage_b += script_b`

`else:`

`preimage_b += b’\x00’`

`preimage_b += getSequence(txn_struct, i)`

`# remove SIGHASH_ANYONECANPAY`

`if hashtype & 0x0F == SIGHASH_NONE:`

`preimage_b += createVarInt(0)`

`else:`

`# remove SIGHASH_ANYONECANPAY`

`if hashtype & 0x0F == SIGHASH_SINGLE:`

` preimage_b += createVarInt(inp[‘input_index’] + 1)`

` outputs = range(inp[‘input_index’] + 1)`

`else:`

`preimage_b += createVarInt(txn_struct[‘out_count’])`

`outputs = range(txn_struct[‘out_count’])`

`for out in outputs:`

`outp = txn_struct[‘outputs’][out]`

`preimage_b += struct.pack(‘<Q’, outp[‘satoshis’])`

`if outp[‘script_type’] == ‘OP_RETURN’:`

`content_b = bytes.fromhex(outp[‘content_hash256’])`

`scriptPubkey_b = bytes([OP_RETURN]) \ + getWithPushdata(content_b)`

`else:`

`scriptPubkey_b = \`

`getScriptPubkeyFromAddress(outp[‘address’])`

`preimage_b += createVarInt(len(scriptPubkey_b))`

`preimage_b += scriptPubkey_b`

`preimage_b += struct.pack(‘<L’, txn_struct[‘locktime’])`

`preimage_b += struct.pack(‘<L’, hashtype)`

`return preimage_b`

**Program 11.15:** Method to create signature preimage for all sighash types

The following is the createSignedInput method updated after accumulating all the conditions we had used in the preceding use cases:

`def createSignedInput(txn_input: dict, signgrp, script_b: bytes):`

`prevtxn = txn_input[‘prevtxn’]`

`prevtx_rb = bytes.fromhex(prevtxn)[::-1]`

`prevtxnindex = txn_input[‘prevtxnindex’]`

`sgntxnin_b = prevtx_rb + struct.pack(‘<L’, prevtxnindex)`

`if ‘input_txn’ in txn_input: #added`

`scriptSig = txn_input[‘scriptsig’]`

`scriptSig_b = bytes.fromhex(scriptSig)`

`elif txn_input[‘script_type’] == ‘P2SH_Multisig’:`

`scriptSig_b = createScriptSigForMultiSig(signgrp, script_b)`

`elif txn_input[‘script_type’] == ‘P2SH_RelativeTimeLock’:`

`scriptSig_b = createScriptSigForRelTimeLock(signgrp, script_b)`

`elif txn_input[‘script_type’] == ‘P2SH_Condition’:`

`scriptSig_b = createScriptSigForCond(signgrp,`

`script_b,`

`txn_input[‘condition’])`

`elif txn_input[‘script_type’] == ‘P2SH_WithSecret’:`

`if txn_input[‘condition’]:`

`scriptSig_b = createScriptSigWithSecret(signgrp, script_b, txn_input[‘secret’], True)`

`else:`

`scriptSig_b = createScriptSigWithSecret(signgrp, script_b, ‘’, False)`

`elif txn_input[‘script_type’] == ‘P2PKH’:`

`scriptSig_b = createScriptSigForP2PKH(txn_input, signgrp)`

`sgntxnin_b += createVarInt(len(scriptSig_b)) + scriptSig_b`

`return sgntxnin_b`

**Program 11.16:** Method to prepare inputs for signed transaction

The transactions are generated by each individual and sent to someone to collate. Each transaction goes into a new field, `input_txn`, in the transaction structure.

We need code to parse and populate transaction structure with previous the transaction-ID, the previous transaction output `index`, and `scriptSig`. The following method does this:

`def updateTxnStructInput(txn_struct: dict, index: int):`

`txn_s = txn_struct[‘inputs’][index][‘input_txn’]`

`txn_b = bytes.fromhex(txn_s)`

`with mmap.mmap(-1, len(txn_b)) as txn_m:`

`txn_m.write(txn_b)`

`txn_m.seek(0)`

`inp = getTransactionInfo(txn_m)`

`txn_input = txn_struct[‘inputs’][index]`

`txn_input[‘prevtxn’] = inp[‘inputs’][0][‘prev_tx_hash’]`

`txn_input[‘prevtxnindex’] = inp[‘inputs’][0][‘prev_tx_out_index’]`

`txn_input[‘scriptsig’] = inp[‘inputs’][0][‘scriptsig’]`

`return txn_struct`

**Program 11.17:** Update transaction structure from input transaction hex string

`The update structure is called within the following program:`

`def getSignaturesAndExecScripts(txn_struct: dict):`

`signgrp_l = []`

`script_l = []`

`for inp_index in range(txn_struct[‘input_count’]):`

`inp = txn_struct[‘inputs’][inp_index]`

`if ‘input_txn’ in inp:`

`txn_struct = updateTxnStructInput(txn_struct, inp_index)`

`signgrp_l.append([])`

`script_l.append(b’’)`

`else:`

`script_b = getExecutionScript(txn_struct, inp_index)`

`preimage_b = createSignaturePreimage(txn_struct, script_b, inp_index)`

`signgrp = []`

`for privkey in inp[‘privkeys’]:`

`hashtype = inp[‘hash_type’]`

`sign_b = signMessage(preimage_b, privkey, hashtype)`

`signgrp.append(sign_b)`

`signgrp_l.append(signgrp)`

`script_l.append(script_b)`

`return txn_struct, signgrp_l, script_l`

**Program 11.18:** Modified method on signatures and scripts to also include modified transaction structure

The preceding method now returns the updated structure as well.

There are different conditions in which collaborative transactions may be required. Some of these are discussed here.

# [Charity use case](#toc.xhtml#s246a)

In the case of charity, people donate money to the organization, and the organization then uses those funds and funds from its reserve to perform social service activities. Those funds are also used to pay salaries to the regular employees.

In this case, we are using `SIGHASH_NONE|SIGHASH_ANYONECANPAY` as donors do not know where the funds will be used and so, they cannot sign the outputs.

In this use case, the individuals donating will create a transaction without outputs and send it to the charitable trust. This transaction will include signature. Then, the charitable trust will add additional funds from its reserves and pay the vendor, which will provide food, clothing, etc. to the destitute children of the organization.

The following is an illustration of charity:

![](images/Figure-11.38.jpg)

**Figure 11.38:** Charity use case

We write code in which Alice and Bob pay 50 ![](images/Bitcoin.jpg)each to the trust, and the trust pays 125 ![](images/Bitcoin.jpg)to the merchant after adding their 50![](images/Bitcoin.jpg)as additional contribution and pays back the rest to itself as change after deducting network fee.

For Alice, we create code with the following transaction structure method:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = ‘5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2PKH’`

`input0[‘privkeys’] = [‘KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53’]`

`input0[‘script_pubkey’] = ‘76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac’`

`input0[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_NONE`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 0`

`txn[‘locktime’] = 0`

`return txn`

**Program 11.19:** Method to define transaction structure for Alice in charity use case

On executing the program, we get the following transaction:

![](images/Figure-11.39.jpg)

**Figure 11.39:** Transaction hex code for Alice in charity use case

Here’s the script in the transaction:

![](images/Figure-11.40.jpg)

**Figure 11.40:** ScriptSig for transaction created for Alice in charity use case

In the case of sighash-type `ANYONECANPAY`, the spender is not aware of how many other transactions are going to get merged. So, the input index is 0 even though it may fall in a different index in the final transaction.

Similarly, we create a transaction for Bob by having the following fields in the transaction structure:

`input0[‘prevtxn’]=’7995c6e08aee1fb5ddb21c7b84ff949bdb2bd98183623606aa1732a61200c12f’`

`input0[‘privkeys’] = [‘L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ’]`

`input0[‘script_pubkey’] = ‘76a914db610ec1429ecb422044ee4ea92f11bc080fdb3d88ac’`

On executing, we get the following raw transaction:

![](images/Figure-11.41.jpg)

**Figure 11.41:** Create a transaction for Bob in the charity use case

Now, the charitable trust pays 125 ![](images/Bitcoin.jpg)to a merchant by contributing its own 25 ![](images/Bitcoin.jpg).

Till now, the `createTransactionStruct` method consisted of previous transaction-ID and output indices. Now, to fund the final transaction, we already have two signed transactions from Alice and Bob. Consequently, this requires some modification to the existing code.

The charitable trust pays 125 ![](images/Bitcoin.jpg)to merchant with address:

` mnhWcUMqe9J1G4t3NMqNmLUqxfPTgwv7NK`

And the change is paid to the following address:

` mtRkMmpT6uhM9LXVPRk4ck9Gcaz9iuQgmZ`

The following is the modified transaction structure:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 3`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘input_txn’] = ‘01000000018f99caaceba9a1b3890b34e7a6565c8c3dfb593a5b4f89c4b961f0324ef0fc5e000000006a47304402200a4ae1b5ddc7c49859001b9e2ff86bd4be57f44ce49571d6dc68e9942a86c990022054fa2e3446219e8dd6a4ba434d69bde460c7374228e6c529aaa95bb460e3ad2082210281238fc6d981efce6aa1b3ccb8556a1b115a40f8ab3315c003f415ceedc3defeffffffff0000000000’`

`input0[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_NONE`

`txn[‘inputs’].append(input0)`

`input1 = {}`

`input1[‘input_txn’] = ‘01000000012fc10012a63217aa0636628381d92bdb9b94ff847b1cb2ddb51fee8ae0c69579000000006a4730440220152ecb49937c026ba62afd18604e916a515cb7727780b2e6b981cb0cb717a9940220197a071705e4f929b53e6aadefd477336765cb323ef77b86a3b6882669775d858221037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7ffffffff0000000000’`

`input1[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_NONE`

`txn[‘inputs’].append(input1)`

`input2 = {}`

`input2[‘prevtxn’] = ‘c83e8dc76b2139f84235d38907291ebe2470786b2d5977302a63aff1c5d99649’`

`input2[‘prevtxnindex’] = 0`

`input2[‘script_type’] = ‘P2PKH’`

`input2[‘privkeys’] = [‘KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG’]`

`input2[‘script_pubkey’] = ‘76a9142004e0ff6a6f08115d048fd9af177fae702f681a88ac’`

`input2[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input2)`

`txn[‘out_count’] = 2`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 12500000000`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘mnhWcUMqe9J1G4t3NMqNmLUqxfPTgwv7NK’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 2499900000`

`output1[‘script_type’] = ‘P2PKH’`

`output1[‘address’] = ‘mtRkMmpT6uhM9LXVPRk4ck9Gcaz9iuQgmZ’`

`txn[‘outputs’].append(output1)`

`txn[‘locktime’] = 0`

`return txn`

**Program 11.20:** Method to define combined transaction structure in charity use case

We execute the preceding program to obtain the final transaction. On decoding the final transaction, we get the following `scriptSig` for corresponding inputs:

**Input 0:**

![](images/Figure-11.42.jpg)

**Figure 11.42:** ScriptSig of first input for transaction in the charity use case

**Input 1:**

![](images/Figure-11.43.jpg)

**Figure 11.43:** ScriptSig of second input for transaction in the charity use case

**Input 2:**

![](images/Figure-11.44.jpg)

**Figure 11.44:** ScriptSig of third input for transaction in the charity use case

The following screenshot shows the transaction published successfully to the network:

![](images/Figure-11.45.jpg)

**Figure 11.45:** Transaction in charity use case is successfully published

# [Subsidy use case](#toc.xhtml#s247a)

This use case solves the requirement where a person or organization partially sponsors or subsidizes payment for another individual.

In this case, we use `SIGHASH_SINGLE|SIGHASH_ANYONECANPAY` as only one input and one output are known by an individual.

In this case, the individual receiving subsidy only pays discounted price for the service or product. However, the merchant or service provider receives full payment, as the rest of the amount is added by the sponsoring person or organization.

This use case has limited benefit as it is not useful for the following conditions:

*   Individual needs funds from multiple addresses
*   Individual needs to pay from a single address to multiple payees

If more than one person is being subsidized, then everyone who is being subsidized also gets an index that relates to the index of the final transaction output where their transaction will be added.

We consider an example use case in which two students are selected for an educational trip. The school is sponsoring 25% of the cost of their trip. Since there is more than one beneficiary of the subsidy and one final transaction is created, one student gets index value as 0, and the other gets index value as 1.

The following is the illustration of the use case where one person’s purchase is subsidized by another person:

![](images/Figure-11.46.jpg)

**Figure 11.46:** Subsidy use case

In this case, Alice must prepare a transaction for index 0. So, she does not need to make any changes to the code, except transaction structure. The following code is for transaction structure for Alice:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = ‘5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2PKH’`

`input0[‘privkeys’] = [‘KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53’]`

`input0[‘script_pubkey’] = ‘76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac’`

`input0[‘input_index’] = 0`

`input0[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_SINGLE`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 1`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 6667000000`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘msV23rBcHAtQWSkWV9ph91DV65VduWi1Vt’`

`txn[‘outputs’].append(output0)`

`txn[‘locktime’] = 0`

`return txn`

**Program 11.21:** Method to define transaction structure for Alice in the subsidy use case

We execute it to get Alice a signed transaction:

![](images/Figure-11.47.jpg)

**Figure 11.47:** Created transaction for Alice in the subsidy use case

In the case of Bob, since index is 1, Bob will need to have empty output at index 0. This needs to be handled in the code.

Here’s the code for the transaction structure:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = ‘7995c6e08aee1fb5ddb21c7b84ff949bdb2bd98183623606aa1732a61200c12f’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2PKH’`

`input0[‘privkeys’] = [‘L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ’]`

`input0[‘script_pubkey’] = ‘76a914db610ec1429ecb422044ee4ea92f11bc080fdb3d88ac’`

`input0[‘input_index’] = 1`

`input0[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_SINGLE`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 2`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘script_type’] = ‘’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 6667000000`

`output1[‘script_type’] = ‘P2PKH’`

`output1[‘address’] = ‘mnhWcUMqe9J1G4t3NMqNmLUqxfPTgwv7NK’`

`txn[‘outputs’].append(output1)`

`txn[‘locktime’] = 0`

`return txn`

**Program 11.22:** Method to define transaction structure for Bob in subsidy use case

As you can see, we have introduced new `script_type`. This needs to be handled when we create signature preimage and signed transaction.

The following code creates signature preimage:

`def createSignaturePreimage(txn_struct: dict,`

`script_b: bytes,`

`inp_index: int):`

`preimage_b = b’’`

`preimage_b += struct.pack(‘<L’, txn_struct[‘version’])`

`hashtype = txn_struct[‘inputs’][inp_index][‘hash_type’]`

`if hashtype & SIGHASH_ANYONECANPAY:`

`preimage_b += createVarInt(1)`

`inputs = [inp_index] # only current input is processed`

`else:`

`preimage_b += createVarInt(txn_struct[‘input_count’])`

`inputs = range(txn_struct[‘input_count’])`

`for i in inputs:`

`inp = txn_struct[‘inputs’][i]`

`preimage_b += bytes.fromhex(inp[‘prevtxn’])[::-1]`

`preimage_b += struct.pack(‘<L’, inp[‘prevtxnindex’])`

`if i == inp_index:`

`preimage_b += createVarInt(len(script_b))`

`preimage_b += script_b`

`else:`

`preimage_b += b’\x00’`

`preimage_b += getSequence(txn_struct, i)`

`# remove SIGHASH_ANYONECANPAY`

`if hashtype & 0x0F == SIGHASH_NONE:`

`preimage_b += createVarInt(0)`

`else:`

`# remove SIGHASH_ANYONECANPAY`

`if hashtype & 0x0F == SIGHASH_SINGLE:`

`preimage_b += createVarInt(inp[‘input_index’] + 1)`

`outputs = range(inp[‘input_index’] + 1)`

`else:`

`preimage_b += createVarInt(txn_struct[‘out_count’])`

`outputs = range(txn_struct[‘out_count’])`

`for out in outputs:`

`outp = txn_struct[‘outputs’][out]`

`if outp[‘script_type’] == ‘’:`

`preimage_b += bytes([0xff])*8`

`preimage_b += bytes([0x00])`

`else:`

`preimage_b += struct.pack(‘<Q’, outp[‘satoshis’])`

`if outp[‘script_type’] == ‘OP_RETURN’:`

`content_b = bytes.fromhex(outp[‘content_hash256’])`

`scriptPubkey_b = bytes([OP_RETURN]) \ + getWithPushdata(content_b)`

`else:`

`scriptPubkey_b = \ getScriptPubkeyFromAddress(outp[‘address’])`

`preimage_b += createVarInt(len(scriptPubkey_b))`

`preimage_b += scriptPubkey_b`

`preimage_b += struct.pack(‘<L’, txn_struct[‘locktime’])`

`preimage_b += struct.pack(‘<L’, hashtype)`

`return preimage_b`

**Program 11.23:** Method to create preimage with additional support for empty script type

Here’s the code for creating signed transaction:

`def createSignedTransaction(txn_struct: dict,`

`signgrp_l: list,`

`script_l: list):`

`sgntxn_b = b’’`

`sgntxn_b += struct.pack(‘<L’, txn_struct[‘version’])`

`sgntxn_b += createVarInt(txn_struct[‘input_count’])`

`for i in range(txn_struct[‘input_count’]):`

`txn_input = txn_struct[‘inputs’][i]`

`sgntxn_b += createSignedInput(txn_input, signgrp_l[i], script_l[i])`

`sgntxn_b += getSequence(txn_struct, i)`

`sgntxn_b += createVarInt(txn_struct[‘out_count’])`

`for out in range(txn_struct[‘out_count’]):`

`outp = txn_struct[‘outputs’][out]`

`if outp[‘script_type’] == ‘’:`

`sgntxn_b += bytes([0xff])*8`

`sgntxn_b += bytes([0x00])`

`else:`

`sgntxn_b += struct.pack(‘<Q’, outp[‘satoshis’])`

`if outp[‘script_type’] == ‘OP_RETURN’:`

`content_b = bytes.fromhex(outp[‘content_hash256’])`

`scriptPubkey_b = bytes([OP_RETURN]) \ + getWithPushdata(content_b)`

`else:`

`scriptPubkey_b = \ getScriptPubkeyFromAddress(outp[‘address’])`

`sgntxn_b += createVarInt(len(scriptPubkey_b))`

`sgntxn_b += scriptPubkey_b`

`sgntxn_b += struct.pack(‘<L’, txn_struct[‘locktime’])`

`return sgntxn_b`

**Program 11.24:** Method to create signed transaction with additional support for empty script type

We get the following signed transaction for Bob:

![](images/Figure-11.48.jpg)

**Figure 11.48:** Created transaction for Bob in the subsidy use case

Alice and Bob give the transaction they created to the College. The College includes those transactions in the final transaction and publishes it.

Here’s the transaction structure of the final transaction:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 3`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘input_txn’] = ‘01000000018f99caaceba9a1b3890b34e7a6565c8c3dfb593a5b4f89c4b961f0324ef0fc5e000000006b483045022100ff8125ed9e52def07818aa14607ab73ede3fdbc2c0aba0721b6645f9522bac050220419d776c4f291e255cc1dead6fd6543ddd39f2cb65274858c50564b92ae3449683210281238fc6d981efce6aa1b3ccb8556a1b115a40f8ab3315c003f415ceedc3defeffffffff01c058628d010000001976a9148343cfe3998d8a49bcfeea63dcbe12643a8e884788ac00000000’`

`input0[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_SINGLE`

`txn[‘inputs’].append(input0)`

`input1 = {}`

`input1[‘input_txn’] = ‘01000000012fc10012a63217aa0636628381d92bdb9b94ff847b1cb2ddb51fee8ae0c69579000000006a47304402205a2a89a88e5de4f7198369b0eb01a327a5a737f5d7b80167780c8d492c353e480220497f122aa2fb3fcab3f41a2dcaea67d6f2a68d1b690b121e68eb78b4c19bcbab8321037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7ffffffff02ffffffffffffffff00c058628d010000001976a9144ec804774aba76cb4685b5152d6924d8ce5c87ae88ac00000000’`

`input1[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_SINGLE`

`txn[‘inputs’].append(input1)`

`input2 = {}`

`input2[‘prevtxn’] = ‘c83e8dc76b2139f84235d38907291ebe2470786b2d5977302a63aff1c5d99649’`

`input2[‘prevtxnindex’] = 0`

`input2[‘script_type’] = ‘P2PKH’`

`input2[‘privkeys’] = [‘KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG’]`

`input2[‘script_pubkey’] = ‘76a9142004e0ff6a6f08115d048fd9af177fae702f681a88ac’`

`input2[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input2)`

`txn[‘out_count’] = 3`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 6667000000`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘msV23rBcHAtQWSkWV9ph91DV65VduWi1Vt’`

`txn[‘outputs’].append(output0)`

`output1 = {}`

`output1[‘satoshis’] = 6667000000`

`output1[‘script_type’] = ‘P2PKH’`

`output1[‘address’] = ‘mnhWcUMqe9J1G4t3NMqNmLUqxfPTgwv7NK’`

`txn[‘outputs’].append(output1)`

`output2 = {}`

`output2[‘satoshis’] = 1665990000`

`output2[‘script_type’] = ‘P2PKH’`

`output2[‘address’] = ‘mtRkMmpT6uhM9LXVPRk4ck9Gcaz9iuQgmZ’`

`txn[‘outputs’].append(output2)`

`txn[‘locktime’] = 0`

`return txn`

**Program 11.25:** Method to define combined transaction structure in the charity use case

We execute the code to create the final transaction, as follows:

![](images/Figure-11.49.jpg)

**Figure 11.49:** Created transaction in the subsidy use case

We publish this transaction using Bitcoin Core software, as follows:

![](images/Figure-11.50.jpg)

**Figure 11.50:** Subsidy use case transaction published successfully

# [Planned contribution within a group](#toc.xhtml#s248a)

Unlike subsidy or charity, in this case, the involved participants are contributing for a known purpose, like buying a gift for a teacher. Everyone contributes their portion or fair share for buying the gift, and everyone knows how they are paying.

In this case, we are using `SIGHASH_ALL|SIGHASH_ANYONECANPAY` as donors know where the funds will be used and so, sign the outputs.

In this case, one person will create a raw transaction message containing all inputs and outputs that everyone signs, and the final signed transaction is then published.

This can be understood from the following illustration:

![](images/Figure-11.51.jpg)

**Figure 11.51:** Planned group transaction

In the preceding illustration, Alice, Bob, and Carol are buying a gift together for their teacher. Alice and Bob create a transaction of paying a merchant and give the transaction to Carol. Carol creates the final transaction using the transaction received from Alice and Bob and adds her contribution to the final transaction. Carol signs the final transaction before publishing it to the Bitcoin network. The following is the code for the transaction structure of Alice:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 1`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘prevtxn’] = ‘5efcf04e32f061b9c4894f5b3a59fb3d8c5c56a6e7340b89b3a1a9ebacca998f’`

`input0[‘prevtxnindex’] = 0`

`input0[‘script_type’] = ‘P2PKH’`

`input0[‘privkeys’] = [‘KwfxnwxpPG1RmhU8jaU8Ron4m1KZGymLAFNaMnSTonoZ7AQfnV53’]`

`input0[‘script_pubkey’] = ‘76a91481d7033c19dcec645cb3f86ce41678756850ba4d88ac’`

`input0[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_ALL`

`txn[‘inputs’].append(input0)`

`txn[‘out_count’] = 1`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 14999990000`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘msV23rBcHAtQWSkWV9ph91DV65VduWi1Vt’`

`txn[‘outputs’].append(output0)`

`txn[‘locktime’] = 0`

`return txn`

**Program 11.26:** Method to define transaction structure for Alice in planned group transaction

Alice creates the following transaction:

![](images/Figure-11.52.jpg)

**Figure 11.52:** Transaction hex code for Alice in planned group transaction

We modify the following fields in the code for the transaction structure to make it for Bob:

`input0[‘prevtxn’] = ‘7995c6e08aee1fb5ddb21c7b84ff949bdb2bd98183623606aa1732a61200c12f’`

`input0[‘privkeys’] = [‘L26JcHRhqEQv8V9DaAmE4bdszwqXS7tHznGYJPp7fxEoEQxxBPcQ’]`

`input0[‘script_pubkey’] = ‘76a914db610ec1429ecb422044ee4ea92f11bc080fdb3d88ac’`

**Program 11.34:** Updated field for Bob in method to define transaction structure in planned group transaction

Bob creates the following transaction:

![](images/Figure-11.53.jpg)

**Figure 11.53:** Transaction hex code for Bob in planned group transaction

Carol adds her own input and combines Alice’s and Bob’s transaction in the following transaction structure:

`def createTransactionStruct():`

`txn = {}`

`txn[‘version’] = 1`

`txn[‘input_count’] = 3`

`txn[‘inputs’] = []`

`input0 = {}`

`input0[‘input_txn’] = ‘01000000018f99caaceba9a1b3890b34e7a6565c8c3dfb593a5b4f89c4b961f0324ef0fc5e000000006a473044022073ecf25c06ffe90cb03951db885defb1a12aaf50f7b068a94dc6fa3f8dd69cf9022070f3b386c9ec95a24f475bb6b5add578591985320b4ab6424886612cd830b9c581210281238fc6d981efce6aa1b3ccb8556a1b115a40f8ab3315c003f415ceedc3defeffffffff01f0ae117e030000001976a9148343cfe3998d8a49bcfeea63dcbe12643a8e884788ac00000000’`

`input0[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_ALL`

`txn[‘inputs’].append(input0)`

`input1 = {}`

`input1[‘input_txn’] = ‘01000000012fc10012a63217aa0636628381d92bdb9b94ff847b1cb2ddb51fee8ae0c69579000000006a473044022002388c5d0d89d73697abead51ae87cb6d9421662ecb513d620e76b90118307ff02206fe1b65fb514bb1e47c279047fe226b9aedd7ced45902cb377bbb70d60e49fb58121037fadaea6edf196bf70af16cefb2bd3c830e54c0a6e9a00bf7806b241933547f7ffffffff01f0ae117e030000001976a9148343cfe3998d8a49bcfeea63dcbe12643a8e884788ac00000000’`

`input1[‘hash_type’] = SIGHASH_ANYONECANPAY|SIGHASH_ALL`

`txn[‘inputs’].append(input1)`

`input2 = {}`

`input2[‘prevtxn’] = ‘c83e8dc76b2139f84235d38907291ebe2470786b2d5977302a63aff1c5d99649’`

`input2[‘prevtxnindex’] = 0`

`input2[‘script_type’] = ‘P2PKH’`

`input2[‘privkeys’] = [‘KxR8HHyfAwFPidCw2vXThXqT4vSMNeufirHFapnfCfkzLaohtujG’]`

`input2[‘script_pubkey’] = ‘76a9142004e0ff6a6f08115d048fd9af177fae702f681a88ac’`

`input2[‘hash_type’] = SIGHASH_ALL`

`txn[‘inputs’].append(input2)`

`txn[‘out_count’] = 1`

`txn[‘outputs’] = []`

`output0 = {}`

`output0[‘satoshis’] = 14999990000`

`output0[‘script_type’] = ‘P2PKH’`

`output0[‘address’] = ‘msV23rBcHAtQWSkWV9ph91DV65VduWi1Vt’`

`txn[‘outputs’].append(output0)`

`txn[‘locktime’] = 0`

`return txn`

**Program 11.27:** Method to define combined transaction structure in planned group transaction

Carol creates the following transaction:

![](images/Figure-11.54.jpg)

**Figure 11.54:** Transaction hex code for Carol in planned group transaction

And then she publishes the transaction as follows:

![](images/Figure-11.55.jpg)

**Figure 11.55:** Planned group transaction is published successfully

With these collaborative transactions, you learnt how multiple individuals can collaborate to form a collated transaction.

# [Conclusion](#toc.xhtml#s249a)

In this chapter, you learnt about the different ways in which we can use transaction and scripting. You also learnt how to timestamp a digital property and how to lock a transaction until a block height or time is reached. Further on in the chapter, you learnt how to ensure the security of payment, which can lead to building peer-to-peer exchange. Additionally, you learnt how to contribute to a transaction and collate contributed transactions into a final transaction.

In the next chapter, you will learn about an important softfork: segregated witness.

# [Points to remember](#toc.xhtml#s250a)

*   Digital asset or digital property is the digital representation of a property.
*   Digital property is unique and is linked to the owner’s Bitcoin address at any point.
*   Digital property can have marketable value and can be sold, auctioned, or mortgaged.
*   The` OP_RETURN` opcode is used to store data in a transaction.
*   The` OP_RETURN` opcode is non spendable and stays associated with the transaction only.
*   A transaction can be locked till the medium time past is less than the locktime or till block height is reached.
*   A transaction can also be locked based on relative locktime from funding transaction in terms of either block height or medium time past.
*   Relative locktime is a softfork and is used in a script.
*   Relative locktime modifies the method of evolution of the `nSequence` field.
*   Smart contract is a contract between two or more parties written in the form of an executable program.
*   Bitcoin smart contract has certain limitations and cannot do everything that a few other smart contract platforms can do.
*   Bitcoin smart contract provides enough flexibility to help overcome most of its limitations.

# [Questions](#toc.xhtml#s251a)

1.  Write a program to implement a collaborative use case in which Alice and Bob bet on their respective teams winning in a football match. If team A wins, Alice pays Bob 45 ![](images/Bitcoin.jpg). If team B wins, Bob pays Alice 45 ![](images/Bitcoin.jpg). Both lock 50 ![](images/Bitcoin.jpg)in a contract. To settle the bet, Carol takes his fees, which is 4.9999 ![](images/Bitcoin.jpg). The remaining 0.0001 ![](images/Bitcoin.jpg)are paid as fees to the network. Carol will provide the required condition to contract for transferring 95 ![](images/Bitcoin.jpg)to the winner, which is 45 ![](images/Bitcoin.jpg)as winning amount and 50 ![](images/Bitcoin.jpg)as own money.
2.  Write a program to implement peer-to-peer exchange involving escrow. The program needs to have 2-of-3-multisig with `nLockTime`. In the program, you need to implement the flow chart illustrated in *[figure 11.32](#c11.xhtml#fig11_32)*.
3.  Write a program to sell digital asset from one person to another such that the transfer of asset only happens if the receiver reveals the secret shared by the seller on the Bitcoin network. The following illustration describes the scenario:
    
    ![](images/Figure-11.56.jpg)
    
    **Figure 11.56:** Scenario
    
4.  True/False: 
    1.  `OP_RETURN` opcode does not need a nValue. So, it does not cost anything to add them in a transaction.
    2.  Digital property is an asset that is owned by only one person at a time and can be transferred from one wallet address to another.
    3.  A condition in a contract that, once valid, cannot become invalid in the future.
5.  Fill in the blanks: 
    1.  Medium time past is calculated by taking the median of the timestamps of the previous \_\_\_\_\_\_\_\_ blocks.
    2.  Sequence value must be \_\_\_\_\_\_\_\_ than or equal to `OP_CHECKSEQUENCEVERIFY` for a transaction to be valid.
    3.  To collate multiple SIGHASH\_SINGLE transactions into a single final transaction, each individual transaction needs to have outputs at the right \_\_\_\_\_\_\_\_\_\_\_\_.

# [CHAPTER 12](#toc.xhtml#c12)

# [Segregated Witness](#toc.xhtml#c12)

Till now, you have learned about Bitcoin and its building blocks, whitepaper, network protocol, network messaging, database indexing, transaction creation, transaction scripting, and smart contracts. This covers Bitcoin from all aspects of its functionality and implementation.

In this section, we will look at some of the advanced topics that make Bitcoin even more interesting.

We will start this chapter with segregated witness, also called *SegWit*. Segregated witness is one of the biggest enhancements in the history of Bitcoin, and it is the only enhancement that somewhat modifies the Bitcoin Whitepaper, solves long-standing transaction malleability bug, increases the capacity of a block that Satoshi made limited to 1MB, changes the way miners calculate network fee, and changes the way enhancements were traditionally accepted, opening a new way of looking at feature activation. All this happened in one enhancement, so it requires a chapter dedicated to it.

# [Structure](#toc.xhtml#s252a)

In this chapter, we will cover the following topics:

*   Understanding segregated witness 
    *   Transaction malleability
    *   Segregated witness 
        *   User Activated Soft Fork (UASF)
        *   Transaction structure 
            *   Coinbase transaction
            *   Other transactions
        *   Segregated witness as scaling solution
        *   Transaction fee calculation
*   New standard scripts 
    *   Native SegWit transaction scripts 
        *   Native P2WPKH
        *   Native P2WSH
    *   Wrapped SegWit scripts 
        *   Wrapped P2WPKH or P2SH-P2WPKH
        *   Wrapped P2WSH or P2SH-P2WSH
*   Signature verification
*   Address format and generation

# [Objectives](#toc.xhtml#s253a)

In this chapter, you will learn about the segregated witness enhancement, why it was required, what problems it solved, what its features are, how to identify a SegWit transaction, how to verify and create script types introduced by SegWit, and how to calculate network fees for SegWit transactions.

We will go into great depth to understand each aspect of this enhancement by understanding how the bug is resolved and how the change is made to the original whitepaper, understanding the BIP enhancements that were introduced covering each script type in detail, and verifying and creating transactions using them.

# [Understanding segregated witness](#toc.xhtml#s254a)

Segregated witness was introduced primarily to fix multiple *transaction malleability* bugs. In this section, you will understand what *transaction malleability* bugs had kept the Bitcoin network vulnerable for several years and how exchanges had to place hacks to avoid the issues arising due to the bugs.

# [Transaction malleability](#toc.xhtml#s255a)

Transaction malleability is a scenario when the same transaction can have different transaction IDs, which in turn, means two different transactions that represent the same transaction.

Consequently, it was not possible to depend on an unconfirmed transaction even though it was signed by the same person. For instance, someone could just modify a mempool transaction and publish it, which may get mined. This means it is not possible to chain unconfirmed transactions even if they are your own.

It is also possible that a wallet may be waiting for a different transaction ID but receives a different transaction ID and so, it ignores the transaction. This would lead a wallet to believe that it is processing a different transaction, so it may consider your transaction as unconfirmed even though it was confirmed. This may be used by a hacker to misguide a wallet or an exchange.

A transaction malleability bug can be used by the signer (first party), or it can be used by the second or the thi^(rd) party, which receives or knows about the transaction and modifies it.

The following are the transaction malleability issues that existed when the Bitcoin network initially came into existence.

*   Malleability bug used by second or third party: 
    *   In the elliptic curve cryptography used by Bitcoin, (R, S) and (R, -S) are both valid points on the curve. Prior to the SegWit enhancement, this was taken care of by considering the smaller of two valid values of S.
    *   In the initial years, Non-DER encoded signatures were valid. These were made illegal, and the DER format was enforced strictly.
    *   Leading zeroes in front of signature.
    *   Several script-related modifications that do not change their intended validity are also sources of malleability. As an example, opcode OP\_0 pushes zero bytes to stack, which means doing nothing, so inserting OP\_0 doesn’t change script behavior.
*   Malleability bug used by first party: 
    *   While signing a message, a signer needs to generate a random number. This random leads to different but valid signatures. This issue is resolved by RFC6979, which specifies deterministic digital signature generation procedure. However, this cannot be verified, so it still causes malleability.

It is possible to solve second- and third-party malleability by introducing rules that are enforced on scripting and signature format, but this does not solve the malleability bug misused by the signer themselves to deceive the wallet of exchange. BIP-62 tried to solve the transaction malleability problems arising by second or third party misuse of malleability, but its implementation was quite complicated as it was trying to solve so many issues.

**Tip: If you are sending Bitcoins through a pre-SegWit transaction, then you need to be aware that anyone can change your transaction-ID. Additionally, you should not chain transactions that are not confirmed.**

Even though BIP-62 solved most problems, it was not perfect, so unconfirmed transactions could not be chained. This means a dependent transaction could become invalid if a modified parent transaction gets accepted.

The following diagram shows how transaction malleability affects dependent unconfirmed transactions:

![](images/Figure-12.1.jpg)

**Figure 12.1:** Effect of transaction malleability on unconfirmed transaction

The following sequence explains how this can happen:

1.  Alice creates transaction TxA, which pays Bob.
2.  Alice tells Bob that she had made payment and that the transaction ID is TxA.
3.  The attacker creates transaction TxA’ and publishes it on the Bitcoin network just after receiving TxA.
4.  Alice creates transaction TxB, paying Carol from the change collected in TxA.
5.  TxA’ gets added to Bitcoin blockchain.
6.  Bob never receives a confirmation for TxA and considers that it failed.
7.  Similarly, Carol never receives payment as TxA’ was not input to TxB.
8.  Alice pays Bob and Carol again, not knowing that her transaction to Bob was successful.
9.  Bob received payment twice and Alice now needs to get it back, provided Bob agrees.

In 2014, the world’s biggest exchange was hacked, and people lost a massive amount of money. It is considered that the attacker used transaction malleability to hack their exchange. However, we know how these things happened and why they happened, so exchanges and wallet software are aware of these issues, and they have taken steps to not fall into the trap.

Transaction malleability was finally resolved with the implementation of segregated witness enhancement.

# [Segregated witness](#toc.xhtml#s256a)

Segregated witness is the solution to the long-lasting transaction malleability issue. It moves the signature out of the transaction ID calculation, solving all forms of transaction malleability issues.

The following diagram shows how SegWit changes the whitepaper:

![](images/Figure-12.2.jpg)

**Figure 12.2:** Segwit transaction diagram showing the difference in the whitepaper

In the preceding diagram, you can see that the case of SegWit transaction signature is not part of the transaction anymore. It is sent along with the transaction as an extension.

SegWit allowed transactions to be chained while they are unconfirmed, and we can rely on transaction ID. This allowed two individuals to send offline transactions if both have signed the payment contract. Consequently, Lightning Network became feasible, which changed the way payments can be done across the globe. We will discuss this further in the next chapter.

When SegWit was planned, the 1MB block limit appeared as a scalability issue because blocks were hitting the limit, mempool was getting full, and network fees would spike.

Since SegWit was a softfork, older nodes ignore the signatures in a SegWit transaction, so they are not part of the 1MB block calculation. This allowed the incorporation of the required increase in block size into the enhancement. This increase in block size for SegWit transactions also reduced the transaction fees for those transactions.

In the modified block size calculation for the upgraded node, the bytes related to the SegWit in a transaction are considered a quarter of a byte. Additionally, with SegWit, new standard scriptPubKey were introduced, which further reduced byte requirements in a transaction. Both these things made SegWit transactions more economical.

SegWit activation had impact the way we look at the value of Bitcoin, network, and enhancements. There existed a thinking that major enhancements should happen through hard fork and that voting on enhancements should be based on hash power.

Since SegWit activation was a major change, it affected everyone in the ecosystem, and everyone had to make a choice, which many tried to delay. SegWit activation followed BIP 9 and entered the *start* phase on 15^(th) November, 2016. So, timeout was set at 1 year after the start date, before which consensus needed to be reached; otherwise, the activation was to be marked as failed.

By August 2017, a vast majority of nodes were SegWit ready, but consensus was not reached among miners. The Bitcoin developer community saw this as a misalignment between the economic majority and the hash power majority. With the rise of mining pools, the hash power majority did not represent the economic majority as few mining pools owned most of the hash power, and this was evident in user support for new enhancement. To allow other stakeholders to play a role in decision-making, we needed to change the way enhancements get activated. This led to the new activation mechanism called **User-Activated-Soft-Fork** (**UASF**).

# [User Activated Soft Fork (UASF)](#toc.xhtml#s257a)

User Activated Soft Fork is an activation rule enforced by economic majority instead of hash power majority, as was done by miners. The economic majority is representative of the will of full nodes.

BIP 148 was created to enforce SegWit deployment if the hash power majority does not activate segregated witness-related BIPs, which were BIP 141, BIP 143, and BIP 147.

# [Transaction structure](#toc.xhtml#s258a)

Segregated witness moves signature out of the transaction ID calculation and so, modifies transaction structure. You have learned that the integrity of transactions included in a block is verified by adding Merkle –root to the block header. The Merkle –root is calculated using transaction ID for all the block transactions in the order. Since segregated witness moves signature out of transaction-ID calculation, Merkle root also does not verify the integrity of signatures in a block. But why should we care if it does not help the attacker as it cannot change transaction ID? The answer to this is that the attacker can use this as Denial-of-Service attack. An attacker can take a valid block and create millions of valid blocks and broadcast them over the network. This will make the Bitcoin network unable to verify transactions and blocks and will bring the whole network down.

The Bitcoin block contains segregated witness Merkle root or witness root in one of the coinbase transaction outputs. This ensures the integrity of the full content of all the transactions, including signatures. The segregated witnessMerkle root is Merkle root of the whole transaction, unlike Merkle root in block header, which uses transaction ID of all the transactions to calculate Merkle root.

We will first understand the structure of normal transaction ID, and then we will calculate *wtxid* and then use it to get witness root.

# Coinbase transaction

The following diagram shows coinbase transaction with additional information related to SegWit:

![](images/Figure-12.3.jpg)

**Figure 12.3:** Coinbase transaction structure

In the preceding diagram, there are a few things to remember:

*   Number of witnesses = Number of inputs
*   SegWit Marker is 0x00
*   For SegWit transaction, SegWit Flag is set to 0x01
*   Number of Inputs = 1
*   Commitment Hash = hash256 (Witness Root Hash || Witness Reserved Value)
*   Witness root hash is the Merkle root of the witness transaction ID or hash256 of full transaction
*   Witness Reserved Value is the 32-byte witness in the coinbase transaction. Since there is real input in a coinbase transaction the witness reserved value could be anything. Since everyone can look at the value in witnessing, the commitment hash can be verified.

**Transaction ID** (**txid**) is calculated by taking hash256 of the following sections of a transaction:

`txid = hash256([version][input count][inputs][output count][outputs] [locktime])`

Witness Transaction ID (*wtxid*) is calculated by taking hash256 of the full transaction, as follows:

`wtxid = hash256([version][segwit marker][segwit flag][input count][inputs] [output count][outputs][witness data][locktime])`

The following program parses a coinbase translation in a recent block:

`def getCoinbaseTransactionInfo(txn_m: mmap):`

`tx = {}`

`startloc = txn_m.tell()`

`tx[‘version’] = txn_m.read(4)[::-1].hex()`

`tx[‘inp_cnt’] = getVarInt(txn_m)`

`tx[‘is_segwit’] = False`

`if tx[‘inp_cnt’] == 0:`

`# check segwit flag`

`tx[‘is_segwit’] = (int.from_bytes(txn_m.read(1), byteorder=’little’) == 1)`

`if tx[‘is_segwit’] == True:`

`tx[‘inp_cnt’] = getVarInt(txn_m)`

`inp_l = []`

`for i in range(tx[‘inp_cnt’]):`

`inp = {}`

`inp[‘prev_tx_hash’] = txn_m.read(32)[::-1].hex()`

`inp[‘prev_tx_out_index’] = txn_m.read(4)[::-1].hex()`

`inp[‘bytes_coinbase_data’] = getVarInt(txn_m)`

`pos = txn_m.tell()`

`inp[‘bytes_height’] = getVarInt(txn_m)`

`inp[‘height’] = int.from_bytes(txn_m.read(inp[‘bytes_height’]), byteorder=’little’)`

`size = txn_m.tell() - pos`

`coinbase_arb_data_size = inp[‘bytes_coinbase_data’] - size`

`inp[‘coinbase_arb_data’] = txn_m.read(coinbase_arb_data_size).hex()`

`inp[‘sequence’] = txn_m.read(4)[::-1].hex()`

`inp_l.append(inp)`

`tx[‘inputs’] = inp_l`

`tx[‘out_cnt’] = getVarInt(txn_m)`

`out_l = []`

`for i in range(tx[‘out_cnt’]):`

`out = {}`

`out[‘satoshis’] = int.from_bytes(txn_m.read(8), byteorder=’little’)`

`out[‘bytes_scriptpubkey’] = getVarInt(txn_m)`

`out[‘scriptpubkey’] = txn_m.read(out[‘bytes_scriptpubkey’]).hex()`

`out_l.append(out)`

`tx[‘outs’] = out_l`

`curloc = txn_m.tell()`

`txn_m.seek(startloc)`

`txid_b = txn_m.read(curloc - startloc)`

`if tx[‘is_segwit’] == True:`

`# if segflag is true than remove segwit marker and flag from txhash calculation`

`txid_b = txid_b[:4] + txid_b[6:]`

`for i in range(tx[‘inp_cnt’]):`

`tx[‘inputs’][i][‘witness_cnt’] = getVarInt(txn_m)`

`witness_cnt = tx[‘inputs’][i][‘witness_cnt’]`

`witness_l = []`

`for j in range(witness_cnt):`

`witness = {}`

`witness[‘size’] = getVarInt(txn_m)`

`witness[‘witness’] = txn_m.read(witness[‘size’]).hex()`

`witness_l.append(witness)`

`tx[‘inputs’][i][‘witnesses’] = witness_l`

`locktime_b = txn_m.read(4)`

`txid_b += locktime_b`

`tx[‘locktime’] = int.from_bytes(locktime_b, byteorder=’little’)`

`tx[‘txid’] = hash256(txid_b)[::-1].hex()`

`return tx`

**Program 12.1:** Parser for coinbase transaction

To get the coinbase transaction hex code for a block at height 668000, we first get the transaction hash of the coinbase transaction, which is the first transaction in the list of transactions in a block.

![](images/Figure-12.4.jpg)

**Figure 12.4:** CLI Commands to get coinbase transaction ID

We then get the coinbase transaction hex-code by using Bitcoin Core CLI as follows:

![](images/Figure-12.5.jpg)

**Figure 12.5:** CLI Command to get coinbase transaction hex code from its transaction ID

We call the preceding method using coinbase transaction bytes, as follows:

`txn_b = bytes.fromhex(‘010000000001010000000000000000000000000000000000000000000000000000000000000000ffffffff400360310a040e5012602f706f6f6c696e2e636f6d2f746170726f6f742f626970392f57414aa61d1d79f4d92b134a2172611e120154741700bd36220000000000ffffffff041d066c260000000017a9149837b6ca944b36f71b94d19cf1e1acd179726424870000000000000000266a24b9e11b6db14323c98fb36550f3bf4d5ce2ea5fcb878ec778a849a99add2cc2e76141432b0000000000000000266a24aa21a9ed1cb4ceb5ec7fef10b852514760a409539056be66601f589c5539e443fbbfdcfc00000000000000002b6a2952534b424c4f434b3a68894f43c4cff546f6ee51f9e9475bcd2bfff279283cb6de9fc47c2c002eb263012000000000000000000000000000000000000000000000000000000000000000006b6066c1’)`

`txn_m = mmap.mmap(-1, len(txn_b) + 1)`

`txn_m.write(txn_b)`

`txn_m.seek(0)`

`tx = getCoinbaseTransactionInfo(txn_m)`

`print(json.dumps(tx))`

And we get following coinbase transaction information:

![](images/Figure-12.6.jpg)

**Figure 12.6:** Coinbase transaction information obtained from executing the Python program

# Other transactions

Here’s the illustration of SegWit transaction:

![](images/Figure-12.7.jpg)

**Figure 12.7:** Segregated witness transaction structure

The preceding transaction diagram shows that witness data contains scriptSig information.

# [Segregated witness as scaling solution](#toc.xhtml#s259a)

Segregated witness enhancement also allowed blocks to finally be larger than 1 MB. It changed the way we calculate transaction byte size, now called weight. The new block size limit calculated in terms of weight is 4MB. The actual maximum block size is not really 4MB; it is much less. It is somewhere between 2 to 3 MB. Here’s how we calculate weight:

`weight = (4 * sizeof ([version][input count][inputs][output count][outputs] [locktime])) + sizeof ([segwit marker][segwit flag] [witness data])`

A miner is in the business of maximizing profit. For them, every byte counts, and they pick up transactions that ultimately lead to maximum accumulated network fees. When the miner sees a SegWit transaction, they know that weight is what matters and so they look for transactions with the highest bitcoin per weight paid.

We use the transaction structure diagram and the learnings about `txid`, `wtxid`, and `weight` to write a program to parse a SegWit transaction and calculate these values:

`def getTransactionInfo(txn_m: mmap):`

`tx = {}`

`startloc = txn_m.tell()`

`tx[‘version’] = txn_m.read(4)[::-1].hex()`

`tx[‘inp_cnt’] = getVarInt(txn_m)`

`tx[‘is_segwit’] = False`

`if tx[‘inp_cnt’] == 0:`

`# check segwit flag`

`tx[‘is_segwit’] = (int.from_bytes(txn_m.read(1), byteorder=’little’) == 1)`

`if tx[‘is_segwit’] == True:`

`tx[‘inp_cnt’] = getVarInt(txn_m)`

`inp_l = []`

`for i in range(tx[‘inp_cnt’]):`

`inp = {}`

`inp[‘prev_tx_hash’] = txn_m.read(32)[::-1].hex()`

`inp[‘prev_tx_out_index’] = txn_m.read(4)[::-1].hex()`

`inp[‘bytes_scriptsig’] = getVarInt(txn_m)`

`inp[‘scriptsig’] = txn_m.read(inp[‘bytes_scriptsig’]).hex()`

`inp[‘sequence’] = txn_m.read(4)[::-1].hex()`

`inp_l.append(inp)`

`tx[‘inputs’] = inp_l`

`tx[‘out_cnt’] = getVarInt(txn_m)`

`out_l = []`

`for i in range(tx[‘out_cnt’]):`

`out = {}`

`out[‘satoshis’] = int.from_bytes(txn_m.read(8), byteorder=’little’)`

`out[‘bytes_scriptpubkey’] = getVarInt(txn_m)`

`out[‘scriptpubkey’] = txn_m.read(out[‘bytes_scriptpubkey’]).hex()`

`out_l.append(out)`

`tx[‘outs’] = out_l`

`curloc = txn_m.tell()`

`txn_m.seek(startloc)`

`txid_b = txn_m.read(curloc - startloc)`

`if tx[‘is_segwit’] == True:`

`# if SegWit flag is true than remove SegWit marker and flag from txhash calculation`

`txid_b = txid_b[:4] + txid_b[6:]`

`for i in range(tx[‘inp_cnt’]):`

`tx[‘inputs’][i][‘witness_cnt’] = getVarInt(txn_m)`

`witness_l = []`

`witness_cnt = tx[‘inputs’][i][‘witness_cnt’]`

`for j in range(witness_cnt):`

`witness = {}`

`witness[‘size’] = getVarInt(txn_m)`

`witness[‘witness’] = txn_m.read(witness[‘size’]).hex()`

`witness_l.append(witness)`

`tx[‘inputs’][i][‘witnesses’] = witness_l`

`locktime_b = txn_m.read(4)`

`txid_b += locktime_b`

`tx[‘locktime’] = int.from_bytes(locktime_b, byteorder=’little’)`

`tx[‘txid’] = hash256(txid_b)[::-1].hex()`

`curloc = txn_m.tell()`

`txn_m.seek(startloc)`

`wtxid_b = txn_m.read(curloc - startloc)`

`tx[‘wtxid’] = hash256(wtxid_b)[::-1].hex()`

`tx[‘bytes’] = len(wtxid_b)`

`tx[‘weight’] = (len(wtxid_b) - len(txid_b)) + (len(txid_b) * 4)`

`return tx`

**Program 12.2:** Parser for transaction

The preceding program gives us transaction information of a given SegWit transaction. We are using the program to parse transaction with `txid`:

`c6176c811328a9fd82a3a71da78e73781bc5c9a6580fdee4cf4392b165b1a072`

We can get `wtxid` or transaction hash using Bitcoin Core as follows:

![](images/Figure-12.8.jpg)

**Figure 12.8:** CLI command to get wtxid from txid

We call the method as follows:

`txn_b = bytes.fromhex(‘02000000000102dc0f4a1601bd6bfec4241fede438bee45958773fe5d95f88ec890e2363983e0c0100000000ffffffff904d74d770c0ef5ce91190750b235d7ffb340b82b392812ba8e6ad5f0a8c4ca70000000000ffffffff02f31f0a00000000001600140c986c1d8ad520c072ee1aa0a151615c891ef71455b8180000000000160014097e656deb55afa3786c600a87d990dcab86fc2d024730440220685234e91eb14e6d1717c543193181700b1cbf5fecddbee79ed9b6b0bbf24077022033dac5cc679dca810327dcac4b84ba2b007a3a4fda6fb2cbc6099ae91c53804f01210277bed123bc0c0f9883b0bc14014f0385d39eac7ac7212d8c9928fa4121a191f4024730440220635eb52780098e3bd1e39a630a23f553ac62b97d0cd0356fa34ceb47cb0195250220599b83d8872ff173781b83b36bf159b59ed7685f73811f449fa1df814fbef15c0121022cd4d498f1ed0ee382eefe4b6e1d8c5aa678d47b693389ccdf77559b3220c5fa00000000’)`

`txn_m = mmap.mmap(-1, len(txn_b) + 1)`

`txn_m.write(txn_b)`

`txn_m.seek(0)`

`tx = getTransactionInfo(txn_m)`

`print(json.dumps(tx))`

We get following transaction information:

![](images/Figure-12.9.jpg)

**Figure 12.9:** Transaction information obtained by executing the Python program

In the preceding program, `vsize` is calculated as follows:

`vsize = weight / 4`

The preceding program also gives us `wtxid`. To ensure the integrity of the whole transaction along with witness data, we calculate commitment hash. This commitment hash is derived using segregated witness –Merkle root, which is calculated by using `wtxid` of all the transactions in a block. When the miner is adding commitment hash to coinbase transaction, they cannot know `wtxid` of coinbase transaction. This is the reason we don’t calculate `wtxid` of the coinbase transaction. Instead, we give it a 32-byte value consisting of all zeroes. Additionally, we need witness reserve value, which is the first witness of the first input.

In the following program, we calculate the commitment hash:

`def getWitnessReservedValue(cb_tx: dict):`

`return cb_tx[‘inputs’][0][‘witnesses’][0][‘witness’]`

`def getRootHashes(txn_m):`

`txcount = getVarInt(txn_m)`

`wtxid_l = []`

`txid_l = []`

`cb_tx = getCoinbaseTransactionInfo(txn_m)`

`txid_l.append(cb_tx[‘txid’])`

`wtxid_l.append(bytes(32).hex())`

`for txindex in range(txcount - 1):`

`tx = getTransactionInfo(txn_m)`

`wtxid_l.append(tx[‘wtxid’])`

`txid_l.append(tx[‘txid’])`

`witness_merkle_root_h = buildMerkleRoot(wtxid_l)`

`merkle_root_h = buildMerkleRoot(txid_l)`

`return merkle_root_h, witness_merkle_root_h, cb_tx`

`def calculateCommitmentHash(blkhash_b: bytes, block_db):`

`jsonobj = getBlockIndex(blkhash_b, block_db)`

`if ‘data_pos’ in jsonobj:`

`txn_filepath = os.path.join(blocks_path_g, ‘blk%05d.dat’ % jsonobj[‘n_file’])`

`start = jsonobj[‘data_pos’]`

`elif ‘undo_pos’ in jsonobj:`

`txn_filepath = os.path.join(blocks_path_g, ‘rev%05d.dat’ % jsonobj[‘n_file’])`

`start = jsonobj[‘undo_pos’]`

`# load file to memory`

`with open(txn_filepath, ‘rb’) as txn_file:`

`#File is open read-only`

`with mmap.mmap(txn_file.fileno(), 0, prot = mmap.PROT_READ, flags = mmap.MAP_PRIVATE) as txn_m:`

`txn_m.seek(start)`

`blkhdr = getBlockHeader(txn_m.read(80))`

`merkle_root_h, witness_merkle_root_h, cb_tx = getRootHashes(txn_m)`

`print(‘Calculated Witness Merkle Root Hash\t = %s’ % witness_merkle_root_h)`

`print(‘Calculated Merkle Root Hash\t = %s’ % merkle_root_h)`

`witness_reserved_value = getWitnessReservedValue(cb_tx)`

`print(‘witness_reserved_value = ‘, witness_reserved_value)`

`# calculate commitment hash`

`commitment_hb = hashOfJoinedStr(witness_merkle_root_h, witness_reserved_value)`

`commitment_h = commitment_hb.hex()`

`print(‘calculated commitment hash = ‘, commitment_h)`

`return commitment_h, cb_tx`

**Program 12.3:** Calculate commitment hash

To verify that the calculated transaction hash is correct, we use the output index that has scriptPubKey starting with ‘`6a24aa21a9ed`’:

`def getCommitmentHashInCbTx(cb_tx: dict):`

`for output in cb_tx[‘outs’]:`

`if output[‘scriptpubkey’][:12] == ‘6a24aa21a9ed’:`

`commitment_h = output[‘scriptpubkey’][12:]`

`print(‘Actual commitment hash = ‘, commitment_h)`

`return commitment_h`

`def verifyCommitmentHash(cb_tx: dict, commitment_h: str):`

`if getCommitmentHashInCbTx(cb_tx) == commitment_h:`

`print(‘Commitment hash matches’)`

`else:`

`print(‘Invalid commitment hash’)`

**Program 12.4:** Verify commitment hash

We call the preceding programs as follows to calculate commitment hash and verify its correctness:

`if __name__ == ‘__main__’:`

`blk_hb = bytes.fromhex(‘00000000000000000000f608724d1e152a875384e5ed06ae4a889c5a6c19c2f1’)[::-1]`

`commitment_h, cb_tx = calculateCommitmentHash(blk_hb, block_db_g)`

`verifyCommitmentHash(cb_tx, commitment_h)`

This gives us the following result:

![](images/Figure-12.10.jpg)

**Figure 12.10:** Commitment hash obtained by executing the Python program

# [Transaction fee calculation](#toc.xhtml#s260a)

Bitcoin Core provides us fee estimates based on factors such as transaction fees collected in each transaction, which are in mempool, mempool size, and mempool clearing.

The following Bitcoin Core CLI command gives us a fee estimate:

![](images/Figure-12.11.jpg)

**Figure 12.11:** CLI command to get recommended transaction fee rate

This shows that to get a transaction included within the next six blocks, we need to pay 0.00075062 per kilo-vbytes. The vbytes here are the same as vsize we get in the Bitcoin Core CLI output.

The following program calculates the **Estimated Minimum Fee** required for getting the transaction confirmed:

`def calculateTransactionFee(vsize: int, feerate: float):`

`return feerate * vsize/1000`

**Program 12.5:** Program to calculate transaction fee

We call the preceding method with the fee-rate estimation we got using Bitcoin Core CLI and `vsize` we got after dividing weight by 4:

`feerate = 0.00075062`

`vsize = 208`

`fee = calculateTransactionFee(vsize, feerate)`

`print(‘Estimated Minimum Fee in bitcoin = ‘, fee)`

We get following result:

![](images/Figure-12.12.jpg)

**Figure 12.12:** Calculated transaction fee based on recommended fee rate and vsize

In US Dollars, this comes to $4.75 as current market price of 1![](images/Bitcoin.jpg)is $30425.

# [New standard scripts](#toc.xhtml#s261a)

Segregated witnesses introduced four new standard scripts. The scripts are defined in BIP 143 and can be found at the following URL:

**[https://github.com/bitcoin/bips/blob/master/bip-0143.mediawiki](https://github.com/bitcoin/bips/blob/master/bip-0143.mediawiki)**

In the next section, we will understand each of these scripts and build programs to verify the transaction on mainnet blockchain.

# [Native SegWit transaction scripts](#toc.xhtml#s262a)

SegWit transaction, in addition to protecting fund transfer from transaction malleability, provides direct monetary benefit in terms of reduced transaction fee.

A native SegWit transaction looks as follows:

`Previous scriptPubKey: <1-byte witness version> <2-40 bytes witness program>`

`ScriptSig: (empty)`

`Witness Data: <witness data>`

We can see that the `previous scriptPubKey` consists of two parts: witness version and witness program. This suggests that each witness version can have different programs. This is a scalable structure and allows future enhancements. In this chapter, we are discussing the scripts introduced in the first version of Segwit enhancement. The next version is used for Taproot and Schnorr signatures.

# [Native P2WPKH](#toc.xhtml#s263a)

As the name suggests, P2WPKH is the SegWit alternate to the P2PKH script, which we already covered in *[Chapter 10, Create and Validate Transactions](#c10.xhtml)*.

The P2WPKH transaction is as follows:

`Previous scriptPubKey: 0 <20-byte-PublicKeyHash>`

`ScriptSig: (empty)`

`Witness data:`

`<Signature>`

`<PublicKey>`

We can see that witness data is the same as `scriptSig` in P2PKH. So, we only need to make small modifications in the script execution. We need to do the following:

1.  Convert `previous scriptPubKey` to P2PKH standard script.
2.  Add witness data to the stack before processing `previous scriptPubKey`.

We modified the program used in P2SH in *[Chapter 10, Create and Validate Transactions](#c04.xhtml)* to perform this exact activity to include the verification of P2WPKH transactions.

We modify `verifyScript` to include a check for P2WPKH by following these steps.

1.  If `scriptsig_b` is an empty string, add all elements of witness data corresponding to the required input index:
    
    `if scriptsig_b == b’’`:
    
    `# native segwit`
    
    `print(‘native segwit’)`
    
    `witness_l = getWitnessList(tx, inp_index)`
    
    `pushWitnessData(witness_l)`
    
    `else:`
    
    `execScript(scriptsig_b, inp_index, tx)`
    
2.  Convert `Previous scriptPubKey` to standard P2PKH script:
    
    `if isP2WPKH(prev_scriptpubkey_b) == True:`
    
    `print(‘P2WPKH’)`
    
    `# convert 0 <20-byte PKH> to OP_DUP OP_HASH160 <PKH> OP_EQUALVERIFY`
    
    `prev_scriptpubkey_b = bytes([0x76, 0xa9, 0x14]) + prev_scriptpubkey_b[2:] + bytes([0x88, 0xac])`
    
    `is_segwit = True`
    

The following is the definition of all the methods used in the preceding changes:

`def pushWitnessData(witness_l: list):`

`for data in witness_l:`

`st.append(bytes.fromhex(data[‘witness’]))`

`def getWitnessList(tx: dict, inp_index: int):`

`return tx[‘inputs’][inp_index][‘witnesses’]`

`def isP2WPKH(prev_scriptpubkey_b: bytes):`

`#0014<20 bytes>`

`if len(prev_scriptpubkey_b) == 22 and prev_scriptpubkey_b[0:2] == b’\x00\x14’:`

`return True`

`return False`

**Program 12.6:** Updates in program to verify P2WPKH script

Here’s the code to call `verifyScript` to verify P2WPKH script:

`#txid :: 808767ec8b388a7d6c34b9658e573e39034831fea49f0f22911393d6f8e195fb`

`tx_s = ‘0100000000010240fc776263b1a4104da05cf069c8e7b0aeb7f7e4c686062906df9ab5d384716f0100000000ffffffff86ab7969a4d661aeaf8845f49eb2e5d30f6fb657d7694b8289224658158a62870000000000ffffffff02ea430000000000001976a9145d57c599fd94fce0cec607e15716f46468cb281b88aca47e000000000000160014f57aed6b1c121a10bec610987cbf414fb168778402483045022100eb6c3485c4ff17390dfbe35be9940b442783bd103095219c285331372b18913b02205bcbc7ce889823af020030d075832f314d1cc905269edf295e813dc7238dc37301210359522a87dc9c907d1669811b7254faf96d7ffcb1f22736bfcd0168fb19b9c98602483045022100acefd6d2ad0b56ad5837cd9d75b49c9f36f5deb6b12e290bbdc14076a38017cd02207a1add2928912d900756874e487d49b49defc7fc6f9805e9777afa929de5ffcb012102948374b79fa597475cab313e63d61d3d546288e6b9b3f80bd1ecc1a514dc382a00000000’`

`tx_b = bytes.fromhex(tx_s)`

`tx_m = bytes2Mmap(tx_b)`

`tx = getTransactionInfo(tx_m)`

`verifyScript(tx, 0)`

We will cover signature verification later in the chapter. Signature verification is defined in detail in BIP 143. We execute the preceding program, which verifies script, and we get the following results:

![](images/Figure-12.13.jpg)

**Figure 12.13:** Executing the Python program shows that the signature is valid

Though the result says signature is valid, we haven’t discussed in this subtopic and should be ignored.

# [Native P2WSH](#toc.xhtml#s264a)

P2WSH is SegWit alternative to P2SH. The P2WSH transaction is as follows:

`Previous scriptPubKey: 0 <32-byte Redeem-Script-Hash>`

`ScriptSig: (empty)`

`Witness:`

`<Signature 1>`

`<Signature 2>`

`…`

`<redeemScript>`

Here, P2SH-P2WSH uses a hash256 hashing algorithm. So, we convert `previous scriptPubKey` to the following script:

`OP_SHA256 <32-byte-redeemScriptHash> OP_EQUAL`

We modify `verifyScript` to include check for P2WSH:

`if isP2WSH(prev_scriptpubkey_b) == True:`

` print(‘P2WSH’)`

`prev_scriptpubkey_b = bytes([0xa8, 0x20]) + prev_scriptpubkey_b[2:] + bytes([0x87])`

Here’s the implementation of `isP2WSH`:

`def isP2WSH(prev_scriptpubkey_b: bytes):`

`#0020<32 bytes>`

`if len(prev_scriptpubkey_b) == 34 and prev_scriptpubkey_b[0:2] == b’\x00\x20’:`

`return True`

`return False`

We also need to handle OP\_SHA256. We need to add a check to the `execScript` method, as follows:

`def opSha256():`

`v = st.pop()`

`h = hashlib.sha256(v).digest()`

`st.append(h)`

`def execScript(script_b: bytes, inp_index: int, tx: dict):`

`l = len(script_b)`

`script_m = bytes2Mmap(script_b)`

`while script_m.tell() < l:`

`v = script_m.read(1)`

`b = int.from_bytes(v, byteorder=’big’)`

`if b in g_pushdata:`

`script_m.seek(-1, 1)`

`b = decodePushdata(script_m)`

`d = script_m.read(b)`

`pushdata(d)`

`elif v == b’\x76’:`

`opDup()`

`elif v == b’\xa8’:`

`opSha256()`

`elif v == b’\xa9’:`

`opHash160()`

`elif b in g_pushnumber:`

`opNum(b)`

`elif v == b’\x87’:`

`opEqual()`

`elif v == b’\x88’:`

`opEqualVerify()`

`elif v == b’\xac’:`

`opCheckSig(script_b, inp_index, tx)`

`elif v == b’\xae’:`

`opCheckMultisig(script_b, inp_index, tx)`

**Program 12.7:** Updates in program to verify P2WSH script

We call the program with changes, as follows:

`#txid :: dffe1dc8f36cbc39c0f40b090912c5a00da13e3534f97aec0ef5bfe552019897`

`tx_s = ‘02000000000102c2aa999f988ded79cb8021420a01469212fa67e666c7d4078a2aaba1b13adf5c0100000000000000007d2ac99074ba44aac9afc79449d9aa29ae206136b511b12cbe699137740424f80100000000000000000220f31d01000000001976a9143913ef9cfc2bbf68665d735b89538dfb883b59f488ac48c70f0b000000002200209705cdfcbc459a220e7f39ffe547a31335505c2357f452ae12a22b9ae36ea59d040047304402205ca8ff900fd03ca9cba763eccb0888ec943269257286a852e9ba96cbc7da340a02206b84aff30cc2c7669fa4133a317fd9c04b013c1d1f42a647b400f62c9f61343101473044022041e2797e0a4b63878b03ff68d4fce8d6b31909e940024dcfd1c0eea33b7a5a160220140aca6751de16c377ea972e47cfc238b3d6d56477f348fa193588828e51e0030169522103ac79bbcf0ff2204220fbd0f906a8c0ae35ad0c1863852102f83af40e7af36cba2102cf85157ae613db5b445594e76f971cf21a0e26d0e70a85c447d3506fe678ddc721035f32d7cc9b710d8e5084dd93aa67efe95c6d32ba2a71b833fb035063ee40efd953ae0400473044022054c259d498dd1f32a449d7a53c597be64ed6331b32f9e9b2a96a098333d993660220789c04d6f69af4919ac97a963dbf2920df287fd4b5fb9ce595290acae3a59e6301473044022009f219deb061a83bf9505c3642efbdb3ef1af9dbef873c118d757d336a63ab0802201763f0ede288e3c7e1993263e47da73d3f43fa00a58c58bcc85e72c743076caf0169522102e67ce679d617d674d68eea95ecb166c67b4b5520105c4745adf37ce8a40b92dc21029ff54b8bf26dbddd7bd4336593d2ff17519d5374989f36a6f5f8239675ff79a421039000ee2853c6db4bd956e80b1ecfb8711bf3e0a9a8886d15450c29458b60473153ae00000000’`

`tx_b = bytes.fromhex(tx_s)`

`tx_m = bytes2Mmap(tx_b)`

`tx = getTransactionInfo(tx_m)`

`verifyScript(tx, 0)`

On executing the preceding program, we get the following results:

![](images/Figure-12.14.jpg)

**Figure 12.14:** Executing the Python program shows that P2WSH Script is valid

# [Wrapped SegWit scripts](#toc.xhtml#s265a)

The native SegWit scripts explained in the previous subtopics can also be wrapped inside P2SH. This allows easier migration to a newer format as a wrapped SegWit script still works with exchanges that have not yet upgraded to SegWit. Since SegWit solved the long-standing issue and was in the interest of the Bitcoin developer community to provide Bitcoin users a mechanism to migrate even before exchanges have migrated.

If we want to move bitcoin to a Segwit wallet, then since Wrapped Segwit address is a P2SH address, the current exchange has no problem transferring bitcoin. Instead, if we try to send it to the native SegWit address, the current exchange will not understand the new addressing format, so the transaction will not be carried out.

# [Wrapped P2WPKH or P2SH-P2WPKH](#toc.xhtml#s266a)

P2SH-P2WPKH transaction has the following scripts:

`Previous scriptPubKey: OP_HASH160 <20-byte Redeem-Script-Hash> OP_EQUAL`

`ScriptSig: 0 <20-byte-PublicKeyHash>`

`Witness:`

`<Signature>`

`<PublicKey>`

`Redeem Script: scriptSig`

We modify `verifyScript` to include a check for wrapped P2WPKH, as follows:

`if checkWrappedP2WPKH(st) == True:`

`prev_scriptpubkey_b = st[-1]`

`st.pop()`

`witness_l = getWitnessList(tx, inp_index)`

`pushWitnessData(witness_l)`

`print(‘P2SH_P2WPKH’)`

This `checkWrappedP2WPKH` is implemented as follows:

`def checkWrappedP2WPKH(st):`

`script_b = st[-1]`

`if script_b[:2] == b’\x00\x14’ and len(script_b) == 22:`

`return True`

`else:`

`return False`

**Program 12.8:** Method to check is script is P2SH\_P2WPKH

We call the updated method with transaction containing P2SH-P2WPKH script as follows:

`#txid :: c137ca3dc53cd1562da3fd5ceea22c8902c3cfd28b5303ecc70675dfff71ec2d`

`tx_s = ‘020000000001027b806bcadab5c41bd3ccab867112fa041b36e0a8aff518296713721e36aed9f10000000017160014a5736b5f1caaf929de80829ec3acc2e13187f2c5feffffff7cbecb8841826bdb493bac6706be865731e414309d3640631f3571090abfdf20000000001716001405a7ef9d2ab852d55c58e42ac2d60202b2b6c9b0feffffff0234553d00000000001976a914265d799ec0fc523faba0ec8f5ee6f0621140a78588ac9cc911000000000017a9144bc6f0e3b0b3a26135ec3e5c6f88edb80881ce2c8702473044022072ddd8d42edee4662e388b8433c15516097d3bdb8a9ccec0acc21a7f7d068132022012f0ecfeb8682236c27fb8a591512102dfd8387a99111dad25a92fe65641841b01210335c4cfa33717ecea14e644ef938c9ecbcb7bd8569e8f407a014d835a8fb94efe02483045022100c038dd6cdf67aee993416e8471664a019f1d3204602e2acf759cf3cf3852d57c022017a84cdbc515de745587d62bb2b10597800c1b20f382a5b116ea8a0424ea242d012102e5692a54cbc71cb19cbc50b886305f0df9f462eae91125b39a85804cfe7a48012b310a00’`

`tx_b = bytes.fromhex(tx_s)`

`tx_m = bytes2Mmap(tx_b)`

`tx = getTransactionInfo(tx_m)`

`verifyScript(tx, 0)`

On executing the preceding program, we get the following result:

![](images/Figure-12.15.jpg)

**Figure 12.15:** Executing the Python program shows that signature is valid

# [Wrapped P2WSH or P2SH-P2WSH](#toc.xhtml#s267a)

P2SH-P2WSH transaction has the following scripts:

`Previous scriptPubKey: OP_HASH160 <20-byte-P2SH-RedeemScriptHash> OP_EQUAL`

`ScriptSig: 0 <32-byte P2WSH-Redeem-Script-Hash>`

`Witness:`

`<witness items>`

`<P2WSH-Redeem-Script>`

`P2SH RedeemScript: scriptSig`

We modify `verifyScript` to include check for wrapped P2WSH as follows:

`if checkWrappedP2WSH(st) == True:`

`prev_scriptpubkey_b = st[-1]`

`st.pop()`

`witness_l = getWitnessList(tx, inp_index)`

`pushWitnessData(witness_l)`

`print(‘P2SH_P2SH’)`

The `checkWrappedP2WSH method` is implemented as follows:

`def checkWrappedP2WSH(st):`

`script_b = st[-1]`

`if script_b[:2] == b’\x00\x20’ and len(script_b) == 34:`

`return True`

`else:`

`return False`

**Program 12.9:** Method to check is script is P2SH\_P2WSH

The combined changes made in the current and previous subtopics of SegWit transactions gives us the following `verifyScript`:

`def getPrevScriptPubKey(tx: dict, inp_index: int):`

`prevtx_rb = bytes.fromhex(tx[‘inputs’][inp_index][‘prev_tx_hash’])[::-1]`

`prevtx_outindex = tx[‘inputs’][inp_index][‘prev_tx_out_index’]`

`prevtx = findTransaction(prevtx_rb, txindex_db_g)`

`prevScriptPubkey = prevtx[‘outs’][prevtx_outindex][‘scriptpubkey’]`

`prevScriptPubkey_b = bytes.fromhex(prevScriptPubkey)`

`return prevScriptPubkey_b`

`def verifyScript(tx: dict, inp_index: int):`

`scriptsig_b = getScriptSig(tx, inp_index)`

`if scriptsig_b == b’’:`

`# native segwit`

`print(‘native segwit’)`

`witness_l = getWitnessList(tx, inp_index)`

`pushWitnessData(witness_l)`

`else:`

`execScript(scriptsig_b, inp_index, tx)`

`prev_scriptpubkey_b = getPrevScriptPubKey(tx, inp_index)`

`isP2SH = False`

`if checkWrappedP2WPKH(st) == True:`

`prev_scriptpubkey_b = st[-1]`

`st.pop()`

`witness_l = getWitnessList(tx, inp_index)`

`pushWitnessData(witness_l)`

`print(‘P2SH_P2WPKH’)`

`if checkWrappedP2WSH(st) == True:`

`prev_scriptpubkey_b = st[-1]`

`st.pop()`

`witness_l = getWitnessList(tx, inp_index)`

`pushWitnessData(witness_l)`

`print(‘P2SH_P2WSH’)`

`if checkWrappedMultisig(st) == True:`

`redeemscript_b = st[-1]`

`isP2SH = True`

`print(‘P2SH’)`

`if isP2WPKH(prev_scriptpubkey_b) == True:`

`print(‘P2WPKH’)`

`prev_scriptpubkey_b = bytes([0x76, 0xa9, 0x14]) + prev_scriptpubkey_b[2:] + bytes([0x88, 0xac])`

`if isP2WSH(prev_scriptpubkey_b) == True:`

`print(‘P2WSH’)`

`prev_scriptpubkey_b = bytes([0xa8, 0x20]) + prev_scriptpubkey_b[2:] + bytes([0x87])`

`print(‘previous scriptpubkey = ‘, prev_scriptpubkey_b.hex())`

`execScript(prev_scriptpubkey_b, inp_index, tx)`

`status = st.pop()`

`if status == b’\x01’:`

`print(‘1st Script succeeded’)`

`elif status == b’\x01’:`

`print(‘1st Script Failed’)`

`return`

`else:`

`print(‘1st Invalid state’)`

`return`

`if isP2SH == True:`

`execScript(redeemscript_b, inp_index, tx)`

`status = st.pop()`

`if status == b’\x01’:`

`print(‘2nd Script succeeded’)`

`elif status == b’\x01’:`

`print(‘2nd Script Failed’)`

`else:`

`print(‘2nd Invalid state’)`

**Program 12.10:** Updated Program to verify SegWit transaction

We call the updated method with transaction containing P2SH-P2WSH script as follows:

`#txid :: c6ab739d8455cd5133e9f93f542f70a2ccef0c7fb05de998db817dd680af3a91`

`tx_s = ‘010000000001024e453d886f11e3af494ce6073956b0de6eaed80865529ab45f778d660459907e2500000023220020ffc74359d1e79a79b94319a1695a68810e439e4c32e4c1be2b0b7c915ca78536ffffffff4e453d886f11e3af494ce6073956b0de6eaed80865529ab45f778d660459907e29000000232200207a21661b84ac4a34a6afc034030faba8ce8344635ebaf34cde31083f186bf871ffffffff02b02a02000000000017a9147b60c1eebfc2c78c9993668dab556344bf1f78d187d9df0500000000002200206f50cccbc64ea3f6cc434d5878bbe45a609e5592026ce6704f586a0e795a6ae40300483045022100d168fa78728fda205eee72ad7b789bc3153adeec982b2588a1526509aa1e2ae8022010443c0652848492dad4904f45258f5452256bfe23d9c715bf052d908154de6e0125512102972c9ea94bfcd5956220f2e99776b3c5ebcca9373a2eccb3fb5fff8bbc9f999451ae03004830450221009691361fa2953e54bc5287306c023fc2d098aa6e85ed1a66d3369e93781260b102201fb639437128d361a12ea385a61bd49247d25c254d1efc03d5272dd368c0acfa01255121027c6cbed24ad235fe147413272ba92cfd61d5ab338c4dabd74cbfb7d11746da5451ae00000000’`

`tx_b = bytes.fromhex(tx_s)`

`tx_m = bytes2Mmap(tx_b)`

`tx = getTransactionInfo(tx_m)`

`verifyScript(tx, 0)`

Running the preceding code gives us the following result:

![](images/Figure-12.16.jpg)

**Figure 12.16:** Executing the Python program shows that P2SH\_P2WSH Script is valid

We learned that with simple modifications to the P2PKH/P2SH transaction verification program, we can also verify SegWit transactions. We still haven’t learned to create the right message for signature verification, so we will look at that in the next topic.

# [Signature verification](#toc.xhtml#s268a)

In this section, we will understand BIP 143 to create the correct signature preimage. All SegWit transactions with the same sighash type have the same method of creating a signature preimage.

A signature preimage has the following structure:

![](images/Figure-12.17.jpg)

**Figure 12.17:** Signature preimage structure for SegWit transaction

Each part of the preimage is defined as follows:

Considering,

***TxIDprev: TxID of previous transaction***

***TxOutIndexprev: Output index of previous transaction in inputs***

***output:*** *output of the transaction*

***‖:*** *concatenation*

***Hash256:*** *double SHA256 hash*

We have the following definition of each part of a signature preimage for sighash type `SIGHASH_ALL`:

*hashPrevouts = Hash256(‖(TxID\_prev∥ TxOutIndex[prev] ))*

*hashSequence = Hash256(‖(nSequence))*

*outpoint = TxID[prev] TxOutIndex[prev]*

*scriptCode = executing script*

*hashOutputs = Hash256(‖(output))*

We use this information to modify the P2SH transaction verification method written in *[Chapter 10, Create and Validate Transactions](#c10.xhtml)* in order to include SegWit transactions. This is done as follows:

`def setVarInt(n: int):`

`if n < 0xfd:`

`n_h = ‘%02x’ % n`

`elif n > 0xfd and n < 0xffff:`

`n_h = ‘fd%04x’ % n`

`elif n > 0xffff and n < 0xFFFFFFFF:`

`n_h = ‘fe%08x’ % n`

`else:`

`n_h = ‘ff%016x’ % n`

`return bytes.fromhex(n_h)`

`def getAmountFromPrevout(prev_tx_hash_b: bytes, prev_tx_out_index_b: bytes):`

`prevtx = findTransaction(prev_tx_hash_b, txindex_db_g)`

`prevtx_outindex = int.from_bytes(prev_tx_out_index_b, byteorder = ‘little’)`

`prevAmount = prevtx[‘outs’][prevtx_outindex][‘satoshis’]`

`amount_b = struct.pack(“<Q”, prevAmount)`

`return amount_b`

`def createMsgForSigForSegwit(tx: dict, script_b: bytes, inp_index: int, sighash_type: int):`

`version_b = bytes.fromhex(tx[‘version’])[::-1]`

`inp_cnt = tx[‘inp_cnt’]`

`prevouts_b = b’’`

`sequences_b = b’’`

`for i in range(inp_cnt):`

`tx_inp = tx[‘inputs’][i]`

`prev_tx_hash_b = bytes.fromhex(tx_inp[‘prev_tx_hash’])[::-1]`

`prev_tx_out_index_b = struct.pack(‘<L’, tx_inp[‘prev_tx_out_index’])`

`sequences_b += struct.pack(‘<L’, tx_inp[‘sequence’])`

`prevouts_b += prev_tx_hash_b + prev_tx_out_index_b`

`if i == inp_index:`

`outpoint_b = prev_tx_hash_b + prev_tx_out_index_b`

`print(‘script = ‘, script_b.hex())`

`scriptCode_b = bytes.fromhex(‘%x’ % len(script_b)) + script_b`

`amount_b = getAmountFromPrevout(prev_tx_hash_b, prev_tx_out_index_b)`

`sequence_b = struct.pack(‘<L’, tx_inp[‘sequence’])`

`out_cnt = tx[‘out_cnt’]`

`outputs_b = b’’`

`for o in range(out_cnt):`

`tx_out = tx[‘outs’][o]`

`satoshis_b = struct.pack(‘<Q’, tx_out[‘satoshis’])`

`bytes_scriptpubkey_b = setVarInt(tx_out[‘bytes_scriptpubkey’])`

`scriptpubkey_b = bytes.fromhex(tx_out[‘scriptpubkey’])`

`outputs_b += satoshis_b + bytes_scriptpubkey_b + scriptpubkey_b`

`locktime_b = struct.pack(‘<L’, tx[‘locktime’])`

`hashPrevouts_b = hash256(prevouts_b)`

`hashSequence_b = hash256(sequences_b)`

`hashOutputs_b = hash256(outputs_b)`

`hashType_b = struct.pack(‘<L’, sighash_type)`

`msg_b = version_b + hashPrevouts_b + hashSequence_b + outpoint_b + scriptCode_b + amount_b + sequence_b + hashOutputs_b + locktime_b + hashType_b`

`return msg_b`

**Program 12.11:** Create a signature preimage for SegWit transaction

The method is called from the following `sigcheck` method if the transaction has segregated witness:

`def uncompressPubkey(pubkey_b: bytes):`

`pubkey_P = PublicKey.decode(pubkey_b)`

`pubkey_b = PublicKey.encode(pubkey_P, compressed=False)`

` return pubkey_b`

`def sigcheck(sig_b: bytes, pubkey_b: bytes,`

`script_b: bytes, inp_index: int, tx: dict):`

`sighash_type = sig_b[-1]`

`if tx[‘is_segwit’] == True:`

`msg_b = createMsgForSigForSegwit(tx, script_b, inp_index, sighash_type)`

`else:`

`msg_b = createMsgForSig(tx, script_b, inp_index, sighash_type)`

`print(‘sig = %s’ % sig_b.hex())`

`print(‘pubkey = %s’ % pubkey_b.hex())`

`print(‘msg = %s’ % msg_b.hex())`

`msg_h = hashlib.sha256(msg_b).digest()`

`print(‘msg_h = %s’ % msg_h.hex())`

`prefix = pubkey_b[0:1]`

`if prefix == b”\x02” or prefix == b”\x03”:`

`fullpubkey_b = uncompressPubkey(pubkey_b)[1:]`

`elif prefix == b”\x04”:`

`fullpubkey_b = pubkey_b[1:]`

`rs_b = getRandSFromSig(sig_b)`

`print(‘rs = %s’ % rs_b.hex())`

`vk = ecdsa.VerifyingKey.from_string(fullpubkey_b, curve=ecdsa.SECP256k1)`

`if vk.verify(rs_b, msg_h, hashlib.sha256) == True:`

`print(“Signature is Valid”)`

`return b’\x01’`

`else:`

`print(“Signature is not Valid”)`

`return b’\x00’`

**Program 12.12:** Verify signature in SegWit transaction

For other sighash types, we use the following mathematical expressions:

*   *For sighash type SIGHASH\_NONE:*
    
    *hashPrevouts = Hash256(‖(TxID[prev] TxOutIndex[prev] ))*
    
    *hashSequence = 32 byte of zeroes*
    
    *hashOutputs = 32 byte of zeroes*
    
*   For sighash type SIGHASH\_SINGLE:
    
    *hashPrevouts = Hash256(‖(TxID[prev] TxOutIndex[prev] ))*
    
    *hashSequence = 32 bytes of zeroes*
    
    *hashOutputs = Hash256(output[inputindex] )*
    
*   For sighash type SIGHASH\_ALL|SIGHASH\_ANYONECANPAY:
    
    *hashPrevouts = 32 bytes of zeroes*
    
    *hashSequence = 32 bytes of zeroes*
    
    *hashOutputs = Hash256(‖(output))*
    
*   For sighash type SIGHASH\_NONE|SIGHASH\_ANYONECANPAY:
    
    *hashPrevouts = 32 bytes of zeroes*
    
    *hashSequence = 32 bytes of zeroes*
    
    *hashOutputs = 32 bytes of zeroes*
    
*   For sighash\_type SIGHASH\_SINGLE|SIGHASH\_ANYONECANPAY:
    
    *hashPrevouts=32 bytes of zeroes*
    
    *hashSequence=32 bytes of zeroes*
    
    *hashOutputs=Hash256(output[inputindex] )*
    

As we have learned to create signature preimage for SIGHASH\_ALL, we can similarly build preimage using the preceding information for other sighash types.

# [Address format and generation](#toc.xhtml#s269a)

Segregated witnesses introduced a shorter address format based on the bech32 algorithm. The BIP 173 provides information about the bech32 format used in Bitcoin SegWit addressing. Listed here are a few advantages of bech32 over the base58check algorithm used in non-SegWit transactions:

*   Base58 needs a lot of space in QR codes, as it cannot use the *alphanumeric mode*.
*   The mixed case in base58 makes it inconvenient to reliably write down, type on mobile keyboards, or read out loud.
*   The double SHA256 checksum is slow and has no error-detection guarantees.
*   Most of the research on error-detecting codes only applies to character-set sizes that are a prime power, which 58 is not.
*   Base58 decoding is complicated and relatively slow.

A bech32 string is at most 90 characters long and consists of the following:

*   The ***human-readable*** **part** is intended to convey the type of data or anything else that is relevant to the reader. This part MUST contain 1-83 US-ASCII characters, with each character having a value in the range \[33-126\]. HRP validity may be further restricted by specific applications.
*   The ***separator*** is always “1”. In case “1” is allowed inside the human-readable part, the last one in the string is the separator.
*   The ***data part*** is at least 6 characters long and only consists of alphanumeric characters, excluding “1”, “b”, “i”, and “o”.

We will use the following Python library for bech32 encoding and decoding:

![](images/Figure-12.18.jpg)

**Figure 12.18:** Required PIP package for the new Segwit addresses

As we have learned, in the case of native SegWit transaction the `previous scriptPubKey` has the following format:

`<1-byte witness version> <2-40 bytes witness program>`

The current version is 0, for P2WPKH, witness program is 20-byte in size, and for P2WSH, witness program is 32-byte in size.

The following is the previous scriptPubkey in the native P2WPKH transaction example we discussed in the one of the previous sections:

`Previous scriptPubkey: 0x0014122bf8b77dceee01c0fa1f2b36d155fea2a5b016`

`=> witness version = 0x00`

`=> witness program size = 0x14 = 20-bytes`

`=> witness program = 0x122bf8b77dceee01c0fa1f2b36d155fea2a5b016`

The following program encodes witness program and prints address:

`import bech32`

`witprog = bytes.fromhex(‘122bf8b77dceee01c0fa1f2b36d155fea2a5b016’)`

`witver = 0x00`

`hrp = ‘bc’`

`address = bech32.encode(hrp, witver, witprog)`

`print(address)`

**Program 12.13:** Generate bech32 address for Native SegWit address

In the preceding program, `hrp` stands for **human-readable-part**. The following are the HRP codes corresponding to the network:

 
| **HRP codes** || **Network** |
| --- | --- |
| bc || Mainnet |
| tb || Testnet |
| tb || Regtest |

**Table 12.1:** HRP codes for Bitcoin networks

On running the program, we get the following address:

![](images/Figure-12.19.jpg)

**Figure 12.19:** Generated bech32 address from the private key

We can check whether the address is correct by looking at the corresponding transaction in blockchain using Bitcoin Core client. The following is the output index 1 of `txid 6f7184d3b59adf06290686c6e4f7b7aeb0e7c869f05ca04d10a4b1636277fc40`:

![](images/Figure-12.20.jpg)

**Figure 12.20:** Shows the bech32 address in transaction output

Now, we will do it for native P2WSH. We are using the P2WSH transaction used in the example in a previous section, where:

`Previous scriptPubkey = 0020d0862d6e40d240ea1711f6d897f5e7b07e974a593704077edffb7b67fd34b091`

So,

`witness version = 0x00`

`=> witness program size = 0x20 = 32-bytes`

`=> witness program =`

`0xd0862d6e40d240ea1711f6d897f5e7b07e974a593704077edffb7b67fd34b091`

Here’s the program to get bech32 address corresponding to P2WSH:

`witprog = bytes.fromhex(‘d0862d6e40d240ea1711f6d897f5e7b07e974a593704077edffb7b67fd34b091’)`

`witver = 0x00`

`hrp = ‘bc’`

`address = bech32.encode(hrp, witver, witprog)`

`print(address)`

This gives us the following address:

![](images/Figure-12.21.jpg)

**Figure 12.21:** Generated bech32 address from the private key

In the preceding program, we are looking at previous `txid` at index 0 of `txid`*:*

`dffe1dc8f36cbc39c0f40b090912c5a00da13e3534f97aec0ef5bfe552019897`

By looking at `outindex` of the previous `txid` using Bitcoin Core client, we get the following previous scriptPubkey and the corresponding address:

![](images/Figure-12.22.jpg)

**Figure 12.22:** Shows the bech32 address in transaction output

The following is the code to decrypt bech32 addresses:

`witver, witprog_l = bech32.decode(address[:2], address)`

`witprog_b = bytes(witprog_l)`

`scriptpubkey_b = bytes([witver]) + bytes([len(witprog_b)]) + witprog_b`

`print(‘scriptpubkey = ‘, scriptpubkey_b.hex())`

**Program 12.14:** Decode bech32 address to getscriptpubkey

Using it to decode bech32 address for the P2WPKH in the following execution:

![](images/Figure-12.23.jpg)

**Figure 12.23:** Decoded bech32 address to get scriptpubkey

And using it to decode the bech32 address for the P2WSH in the following execution:

![](images/Figure-12.24.jpg)

**Figure 12.24:** Decoded bech32 address to get scriptpubkey

This brings us to the end of this chapter, wherein we have likely covered all the aspects of segregated witness enhancements.

# [Conclusion](#toc.xhtml#s270a)

In this chapter, you learned about segregated witness enhancement. You learned why it was important and the impact it has on overall Bitcoin. Additionally, you learned about the several changes that happened along with this enhancement, like we changed the way we see network enhancements. The chapter covered the new address encoding algorithms and taught you to encode and decode addresses. You learned to verify the new standard transaction scripts introduced by SegWit, learned the structure of transactions, and verify them along with signatures.

In the next chapter, we will cover the Lightning Network, which is both a part of Bitcoin and still a separate development. It’s a layer-two protocol that can provide Bitcoin speed, which Bitcoin lacks by design. It is an important development in scalability.

# [Points to remember](#toc.xhtml#s271a)

*   Bitcoin originally had multiple transaction malleability bugs.
*   BIP62 was the original workaround for the transaction malleability issue, which was cumbersome to implement.
*   Transaction malleability made unconfirmed transactions unreliable even for the signer of the transaction.
*   Segregated witness solved all transaction malleability issues by moving signature out of the transaction ID calculation. The section that is not part of the transaction ID calculation is called witness data.
*   Segregated witness was implemented as a softfork.
*   SegWit activation followed BIP 9.
*   BIP 148 was created to enforce SegWit deployment if the hash power majority does not activate segregated witness related BIPs, which were BIP 141, BIP 143, and BIP 147. This was the first time **User Activated Soft Fork** (**UASF**) was used to enforce feature activation.
*   UASF is an activation rule enforced by the economic majority instead of the hash power majority.
*   Segregated witness Merkle oot is calculated by taking the hash of the whole transaction of all the transactions in the block, prepending the hash with 32-byte zeros and calculating Merkle root.
*   Hash of calculated segregated witness –Merkle oot concatenated with witness-reserve-value (provided by a miner in the first input of coinbase transaction) determines commitment-hash, which is in one of the outputs of coinbase transaction.
*   SegWit allowed blocks to be larger than 1 MB as the bytes within witness data are considered one-fourth of their size. So, Bitcoin software changes the way it counts bytes. In this counting, size remains within 1 MB even though it may actually be bigger than 1 MB.
*   Using segregated witness for creating transactions reduces the amount of required network fees.
*   SegWit introduced four new standard scripts: P2WPKH, P2WSH, P2SH-P2WPKH, and P2SH-P2WSH.
*   Native SegWit script hash and public key hash are encoded using bech32.
*   SegWit address has a scalable scheme, contains version, and the current version is 0.
*   SegWit transaction signature is generated using a message format different from non-SegWit transactions. This message format is defined in BIP143.

# [Questions](#toc.xhtml#s272a)

1.  Calculate the approximate vsize of P2PKH, P2SH-P2WPKH, and P2WPKH transactions with 1 input and 1 output. Compare them and determine percentage saving by using SegWit transactions.
2.  Calculate approximate vsize of 2-2 multisig P2SH, P2SH-P2WSH, and P2WSH transactions with 1 input and 1 output. Compare them and determine percentage saving by using SegWit transactions.
3.  Write programs to create transactions: 
    1.  Write a program to create a P2WPKH transaction.
    2.  Write a program to create a P2WSH transaction.
    3.  Write a program to create a P2SH-P2WPKH transaction.
    4.  Write a program to create P2SH-P2WSH transactions.
4.  Fill in the blanks: 
    1.  BIP \_\_\_\_\_\_ contains details of UASF for enforcing SegWit related BIPs.
    2.  Before SegWit BIP \_\_\_\_\_\_\_ provided a workaround for the transaction malleability bug.
    3.  Transaction malleability bugs originate as for a transaction, \_\_\_\_\_\_\_\_\_\_\_\_\_ can be different but still valid.
5.  True/False: 
    1.  After SegWit softfork was activated, a non SegWit transaction became invalid and was rejected by the network.
    2.  BIP 148 replaced BIP 9 activation on the Bitcoin network.
    3.  Bech32 encoding generates alphanumeric characters meaning either capital or small alphabets and/or numbers.

# [CHAPTER 13](#toc.xhtml#c13)

# [Lightning Network](#toc.xhtml#c13)

In the previous chapter, you learned about an important enhancement called **Segregated Witness**. The enhancement eliminated the possibility of transaction malleability by moving the signature out of transaction ID calculation. This improvement helped exchanges and wallets by enhancing their security.

The enhancement also opened the possibility of secure off-chain transaction, leading to development of layer two protocols such as **Lightning Network**.

In this chapter, we will cover the most successful layer two protocol, called Lightning Network. Lightning Network is based on the creation of channels by adding fund of both parties and performing off-chain transaction. This was first conceptualized by *Satoshi Nakamoto* himself. Later in 2015, it was first proposed by *Thaddeus Dryja* and *Joseph Poon* in a paper titled **The Bitcoin Lightning Network. The paper is available for public at** the **following** weblink:

**[https://lightning.network/lightning-network-paper.pdf](https://lightning.network/lightning-network-paper.pdf)**

A few months after SegWit was activated in October 2017, Lightning Labs launched the beta version of Lightning Network in March 2018.

Lightning Network works by routing payments over Lightning node channels. The more widespread the network, the better is the user experience. Due to this, its growth has been parabolic, slow in the beginning and rapid now. To help the technology grow, a pseudonymous Twitter user launched Lightning Torch in January 2019. It was based on the concept of relay race in Olympics. It was quite successful and lasted for 4 months, but beyond that, adoption remained slow at the global scale.

Things changed in 2021 because of more than 2 years of work of Bitcoin Beach, a surfing community, and Jack Mallers’ launch of strike, a Lightning Network wallet, in *El Salvador*. After that, Bitcoin got Legal Tender status with the support of *Nayib Bukele*, the president of *El Salvador*. Additionally, Chivo, a Lightning Network wallet, was launched by the government, covering whole country of more than a million people in *El Salvador*. Since then, Lightning adoption has been rapid.

In 2021, Twitter also integrated Lightning payment.

Lightning Network is an essential element to build circular economy based on Bitcoin. In this chapter, you will learn what makes Lightning Network so special.

# [Structure](#toc.xhtml#s273a)

In this chapter, we will cover the following topics:

*   Simplified working of Lightning Network 
    *   Payment between connected peers
    *   Payment though multiple channels
*   Bolt specifications
*   Contracts involved in Lightning Network 
    *   Offline payments between connected peers 
        *   Channel creation
            
            ![](images/ent.jpg)Instant or turbo channels
            
        *   Offline transactions
        *   Channel closure
            
            ![](images/ent.jpg)Mutually agreed close
            
            ![](images/ent.jpg)Unilateral close
            
            ![](images/ent.jpg)Revoked transaction closure
            
    *   Bidirectional dual funded channel 
        *   Channel creation
        *   Offline payments involving intermediaries
*   Monitoring of channels 
    *   Watchtower 
        *   Drawback of justice transaction
*   Routing mechanism and considerations 
    *   Trampoline nodes
    *   Channel management 
        *   Circular rebalancing
        *   Splicing
        *   Lightning Loop or submarine swaps
    *   Multi-Part Payments or MPP
*   End user experience 
    *   Lightning wallets
    *   Lightning invoice
    *   LNURL
    *   Merchant integration
    *   Social media integrations
    *   Adoption by exchanges
*   Other cryptocurrencies 
    *   Cross-chain atomic swap
*   Network topology

# [Objectives](#toc.xhtml#s274a)

In this chapter, we will focus on learning about Lightning Network and touch upon its internals a bit. Lightning Network protocol specifications are defined as the BOLT specifications. Each BOLT specification defines specific network abstraction.

Bitcoin network only contributes to Lightning Network by providing scripting opcodes in the same way a computer microprocessor provides machine instructions to high-level language compilers. As a result, Lightning Network can add complexity without needing changes in the base layer.

Consequently, the development in Lightning Network is quite dynamic, and the protocol is evolving rapidly, allowing improvement and extension of use-cases. This requires quicker software development and testing cycle, which is different from the way Bitcoin development happens.

Since Lightning Network is quite a wide and dynamic topic, there is a possibility that by the time the readers will be reading this chapter, there are already quite a few changes in the specifications. We will try to cover as much as possible within the limits of this chapter.

# [Simplified working of Lightning Network](#toc.xhtml#s275a)

We discussed Lightning Network in *[Chapter 4, Bitcoin in the Real World](#c04.xhtml)* under a highlighted section of *Lightning Network*.

The following is the summary of what you learned in *[Chapter 4, Bitcoin in the Real World](#c04.xhtml)*:

*   Two parties create a channel by locking their bitcoins.
*   Any party can send bitcoins to the other party if the current balance on their side of the channel still has funds.
*   Payment between the parties is peer-to-peer and does not involve the Bitcoin network.
*   Any party can close the channel anytime by broadcasting the final cumulative transaction over the Bitcoin network.

This is the simplest view of Lightning payment between two parties. Since Lightning Network is a complex protocol, it is lot more than simple peer to peer payment. This time, we are going deeper into the working of protocol.

# [Payment between connected peers](#toc.xhtml#s276a)

If Amazon had the option to pay with lightning as a buyer or seller, we could open a channel and continue making transaction with Amazon till there is balance in the channel.

As an example, Alice creates a channel with milk vendor Bob by loading 0.001![](images/Bitcoin.jpg)at her side. In this case, Alice uses UTXOs to fund a transaction that is paying 2-of-2-multisig contract. This transaction needs to pay network fees and be confirmed by getting included in the Bitcoin blockchain.

Here’s the illustration of the creation of a channel:

![](images/Figure-13.1.jpg)

**Figure 13.1:** Creation of channel

In this, Alice buys milk from Bob every day, and she pays him every day as she buys milk.

Consider that she pays 0.0001![](images/Bitcoin.jpg)for 5 days and mutually agrees with Bob to close the channel.

The following illustration shows the three days of intermediate transactions:

![](images/Figure-13.2.jpg)

**Figure 13.2:** Offline transactions sent each time

Each new transaction needs to invalidate the previous transaction so that Alice cannot publish it and cheat Bob. None of the intermediate transactions sent by Alice to Bob gets published.

Alice and Bob mutually agree and publish transactions after 5 days.

The following is the published transaction that closes the channel:

![](images/Figure-13.3.jpg)

**Figure 13.3:** Transaction published on-chain

The illustration does not include the transaction fees, which is also paid along with the output. In the actual closing of the channel, Alice and Bob cooperate on network fees they wish to pay, and then the transaction which is the cumulative sum of all preceding transactions gets published.

# [Payment though multiple channels](#toc.xhtml#s277a)

In the real-world scenario, each node will have few channels, so it will be connected to only a few other nodes. As the network grows, there will be billions of nodes. So, for anyone to connect to others, there will be routing like the one we have with internet.

This means there are going to be intermediaries that will facilitate payment between nodes. Additionally, there will be multiple routes between source and destination, and the protocol will need to make smart decision in selecting the routing path. The nodes provide better connectivity, and latency and funds will be favored by routing algorithms, so the node will try to incentivize this service by charging a routing fee.

To make this possible, nodes in Lightning Network can make payment through the intermediate nodes, and intermediate nodes can charge fees.

Consider that Alice wants to pay Carol, but she does not have direct channel with Carol. However, Alice can pay Bob and Bob can pay Carol. We also need to make sure Bob cannot steal the money.

This can work only if Alice and Bob create contract between them such that Bob can redeem bitcoins only if he can prove that he has paid Carol. This means first Bob pays Carol, and then Bob proves to Alice that he has paid.

To achieve this, Carol creates a secret and both Bob and Alice know its hash. The contract between Alice and Bob requires secret, which Bob obtains after paying to Carol. And Carol can only redeem the bitcoin she is being paid when she reveals the secret. This mechanism ensures that no one can cheat the other person.

The following is the illustration of routing of payment from Alice to Carol via Bob:

![](images/Figure-13.4.jpg)

**Figure 13.4:** Payment through intermediaries

# [Bolt specifications](#toc.xhtml#s278a)

Lightning Network requires nodes to communicate through messages. They need to set conditions to manage failures and attacks, discover each other and remain anonymous, and also pass receipts.

Since Lightning Network is open and decentralized, the software implementation needs specifications. Bolt is the set of specifications that Lightning Network Software follows so that a node using one Lightning Network software can interact with nodes running different Lightning Network software.

Bolt stands for ***Basis of Lightning Technology***.

Here’s the active list of Bolt specification:

 
| **Bolt Specification Number** || **Information** |
| --- | --- |
| Bolt 1 || Base Layer |
| Bolt 2 || Peer Protocol for Channel Management |
| Bolt 3 || Bitcoin Transaction and Script Formats |
| Bolt 4 || Onion Routing Protocol |
| Bolt 5 || Recommendations for On-chain Transaction Handling |
| Bolt 7 || P2P Node and Channel Discovery |
| Bolt 8 || Encrypted and Authenticated Transport |
| Bolt 9 || Assigned Feature Flags |
| Bolt 10 || DNS Bootstrap and Assisted Node Location |
| Bolt 11 || Invoice Protocol for Lightning Payments |

**Table 13.1:** Bolt specifications

Bolt 6 was removed and replaced by Bolt 7.

# [Contracts involved in Lightning Network](#toc.xhtml#s279a)

In the previous section, you learned the basic working of Lightning Network. Now, we will look at the actual contract and the way in which different situations are handled.

# [Offline payments between connected peers](#toc.xhtml#s280a)

First, we will look at the condition when payment happens on a single channel between connected peers. We look at actual contracts involved in the creation of channel, structure of offline transactions, and the different ways by which a channel can be closed and funds settled on-chain.

We will also understand how fees is paid at the time of channel creation and channel closure, and how each off-chain transaction takes this into consideration. We will also understand how the protocol handles cheating through contract.

# [Channel creation](#toc.xhtml#s281a)

Alice is a client of Bob and wants to create channel with Bob so that she can continue paying Bob and pay little fees. As Alice is the client, and she is the one who is going to pay, and Bob is always going to receive bitcoins. The channel is created such that only Alice has balance at her side of the channel.

Once the channel is created and intermediate off-chain transaction happens, anyone should be able to close the channel unilaterally. Closing a channel requires network fees to be paid so that at the time of opening a channel, network fee needs to be negotiated.

The nodes communicate by interchanging defined message formats. The message format is defined in Bolt 2 specification. This facilitates network fee negotiation, channel establishments, etc.

The contract value is defined as sum of fund locked in channel and network fee. The sum locked in channel is only used for transferring value from Alice to Bob.

The following is the illustration of contract value and its composition:

![](images/Figure-13.5.jpg)

**Figure 13.5:** Contract value compositions

Initially, the fund locked in channel is fully on Alice’s side as she funded the 2-of-2-multisig contract between Alice and Bob. This is represented as follows:

![](images/Figure-13.6.jpg)

**Figure 13.6:** Payment channel

Here’s the funding transaction that goes into Bitcoin blockchain:

![](images/Figure-13.7.jpg)

**Figure 13.7:** Funding transaction

# Instant or turbo channels

In Lightning Network, it is expected that fully funded channel will be on chain before off-chain transactions may happen. However, channel mostly gets opened at the time of payment, and to wait for half an hour may lead to bad customer experience.

We saw that when the transaction malleability bug was fixed by segregated witness softfork, unconfirmed transaction became quite reliable. There is still a risk of 0-confirmation attack, in which attacker can publish two transactions simultaneously. As most channels do not hold large value on a single channel, relying on an unconfirmed channel is a fair tradeoff between security and customer experience.

Not waiting for funding transaction confirmation has one important advantage. A low network fee can be paid. Just by waiting for a few hours for confirmation can significantly reduce fees.

# [Offline transactions](#toc.xhtml#s282a)

Once the funds are locked in 2-of-2-multisig contract, Alice can pay Bob if there is balance at the Alice’s side of the channel.

However, Alice can publish an older transaction that gives greater value to her. To protect Bob from getting cheated by Alice, all the older transactions need to be invalidated before performing the next transaction.

To invalidate the latest transaction, Alice needs to provide revocation key to Bob before she can make the next transaction. The revocation key gives Bob the power to claim all the funds locked in the channel before Alice could take away her claim of funds. To avoid Alice from taking away her share, the new contract doesn’t allow Alice to take away her share of funds before a specific duration of time has lapsed.

The following are the first two commitment transactions, including revocation for initial commitment transaction:

![](images/Figure-13.8.jpg)

**Figure 13.8:** Commitment transactions and revocation key sharing

Here, we are only protecting only Bob from being cheated by Alice because Alice cannot be cheated by Bob. If Alice and Bob had bidirectional payment channel, there would be different commitment transaction for Bob and Alice, and revocation would also be shared both ways.

In the commitment transaction, we can observe that if Alice tries to cheat Bob, then he can use the revocation key to claim Alice’s share of the funds immediately.

# [Channel closure](#toc.xhtml#s283a)

There are three ways to close a channel:

1.  A channel can be closed by mutual coordination between parties. This way, the fees can be renegotiated.
2.  A channel can be closed unilaterally. This means any one of the parties can publish their last transaction.
3.  One party can cheat the other party by publishing the older state of a transaction.

The Bolt 2 specification also details closing of channels.

# Mutually agreed close

In the case of mutually negotiated closing, Alice and Bob send protocol messages to decide on fees and then recreate and sign the last transaction. Alice and Bob then publish the transaction on the Bitcoin blockchain. Unlike unilateral close, the mutually coordinated closure transaction does not have any relative time lock, so Alice gets her funds immediately by paying lower fees.

The following is the illustration of mutually negotiated final transaction:

![](images/Figure-13.9.jpg)

**Figure 13.9:** Mutually negotiated channel closure

# Unilateral close

In the case of unilateral close, the last transaction is published, and Bob can take his funds immediately, while Alice must wait till the relative time lock expires.

Here’s the illustration of unilateral close:

![](images/Figure-13.10.jpg)

**Figure 13.10:** Unilateral channel closure

In this case, revocation key was never shared. So, Bob cannot take out his funds, but Alice must wait till the relative time lock expires to claim her share.

# Revoked transaction closure

If Alice publishes an old transaction that is already revoked, then Bob can create a transaction to claim all of Alice’s funds.

The following is the transaction published by Alice:

![](images/Figure-13.11.jpg)

**Figure 13.11:** Revoked transaction published by Alice

Bob then creates another transaction to punish Alice using his revocation key. This transaction is called **j*ustice*** **t*ransaction***. Here’s the illustration:

![](images/Figure-13.12.jpg)

**Figure 13.12:** Justice transaction published by Bob

If Bob has lost the revocation key, then Alice can move the locked funds to her address after 1 day has passed. Here’s the illustration:

![](images/Figure-13.13.jpg)

**Figure 13.13:** Alice moves funds to her address after 1 day

# [Bidirectional dual-funded channel](#toc.xhtml#s284a)

The case we discussed in the previous sections only involved unidirectional payment. Many times, payments between peers can be bidirectional. In this case, the new channel is created by using funds from both Alice and Bob.

# [Channel creation](#toc.xhtml#s285a)

The following is the illustration of a dual-funded channel:

![](images/Figure-13.14.jpg)

**Figure 13.14:** Funding transaction for dual-funded channel

In this case, at the time of payments between Alice and Bob, both create a transaction and send it to the other party, and to revoke the transaction, both parties transfer the revocation key to their counterpart. This happens at every instance, irrespective of who pays to whom.

This can be understood with the help of the following illustration:

![](images/Figure-13.15.jpg)

**Figure 13.15:** Commitment transactions and revocation sequence

In the preceding transaction, Alice needs to send 10 m![](images/Bitcoin.jpg)to Bob to buy coffee. As Bob is the receiver in the previous transaction, Alice will be having more funds than Bob. So, Alice can cheat Bob by posting the previous transaction. To avoid the risk of getting cheated, Bob needs to get a signed transaction from Alice for the coffee, and only then he can revoke his previous transaction and sign Alice’s transaction.

This allows Alice and Bob to have bidirectional channel funded by both parties. Closing of the channel remains the same as we learned in the previous section.

# [Offline payments involving intermediaries](#toc.xhtml#s286a)

In this case, Alice wants to pay Carol 10mB, but she only has a channel with Bob, and Bob has a channel with Carol. Bob charges fees to forward the transaction through his node, and Alice needs to pay to Bob this fee because she is paying Carol. In Lightning Network payment, it is expected that the sender will pay for the fees.

Bob uses Lightning Network protocol messages to inform Alice about the fee she needs to pay.

As we learned in one of the previous topics, Carol needs to generate a secret and give hash of its secret. Carol only needs to share hash of secret with Alice, and when Alice and Bob create contract, Bob gets to know the hash of secret, which he can use to create contract with Carol or another intermediary.

When Carol reveals the secret to Bob, Carol can claim her funds. This allows Bob to know the secret, which he reveals to Alice to claim his funds. Since Bob can only reveal secret to Alice, when Carol has revealed secret to Bob, the timeout in transaction between Bob and Carol needs to be less than transaction between Alice and Bob.

To achieve this, offline transactions have ***Hash Time Locked Contract*** (**HTLC**). HTLC is a class of contract that requires either hash condition or time condition to be met; otherwise, the locked funds can be forfeited. HTLC is the additional output in offline transactions.

The following is the illustration of transactions held at each end for channels:

![](images/Figure-13.16.jpg)

**Figure 13.16:** Contract exchange for offline transactions through intermediaries

In the preceding transaction, we can see that in the HTLC output, if secret is not revealed and revocation key is not used, then Alice can take back her funds in the channel with Bob 14 days after 1,000 blocks are mined, and Bob can take his funds in the channel with Carol 13 days after 1,000 blocks are mined.

HTLC is a separate output, so it adds to the cost of transaction and mostly carries small value. This means when this transaction is published, the UTXO value of the HTLC may make it less usable. To avoid HTLC in final transaction, after Bob gets the secret from Carol and he verifies it, a new transaction is created by removing HTLC output and merging it with the receiver output.

The following is the sequence diagram of secret and hash sharing:

![](images/Figure-13.17.jpg)

**Figure 13.17:** Sequence diagram of payment through intermediaries

In the following illustration, the new modified transaction after secret is shared with Bob by Carol:

![](images/Figure-13.18.jpg)

**Figure 13.18:** Removal of HTLC output after secret is known by Bob

After this, Bob shares secret with Alice, and both agree to remove HTLC from transaction.

![](images/Figure-13.19.jpg)

**Figure 13.19:** Removal of HTLC output after secret is known by Alice

We can see that the preceding updated transaction eliminates the need for settlement of transactions.

# [Monitoring of channels](#toc.xhtml#s287a)

Lightning Network has one drawback: nodes need to be online all the time to monitor their channels; otherwise, a peer will have a window of opportunity to breach channel. This is because if a channel breach happens and the affected peer is offline, then it will not know that the breach has happened, and the attacker will successfully steal the funds. However, if the victim of channel breach was online, it would know that the breach has occurred, and it would have punished the attacker by publishing the required justice transaction.

But in a real-world scenario, the nodes can go offline because of several reasons like hurricane, internet connection disruption, fire or electric short circuit, or simply because of switching off the power supply by mistake.

To avoid this, Lightning Nodes can pay nodes that can monitor its channels. These monitoring nodes are called **Watchtowers**.

# [Watchtower](#toc.xhtml#s288a)

Watchtower is a Lightning Network node that maintains state of channels for its client and can publish punishment or justice transaction against channel breaches if its client is offline.

Watchtower is supposed to always be online and monitor blockchain all the time. The client of watchtower needs to update the watchtower every time a new transaction is made by its client or revocation key is shared by its client.

The working of watchtower can be understood with the help of the following sequence diagram:

![](images/Figure-13.20.jpg)

**Figure 13.20:** Functioning of watchtower

In the preceding sequence diagram, we can see that the client of watchtower keeps the watchtower server updated about the changes in state of all its channels. So, in the event of channel breach, the watchtower publishes the justice transaction, and the client can claim the punishment transaction.

# [Drawback of justice transaction](#toc.xhtml#s289a)

As you have learned, the Lightning Network provides a mechanism to punish a node that tries to breach a channel by publishing a non-recent transaction. This punishment mechanism is called ***LN-penalty*** and is done by publishing a justice transaction. This sounds like a great idea, but in reality, most nodes that get punished are not cheating. Most breaches happen because a node did not maintain the latest transaction.

It is not right to punish a node for its mistake, so a different mechanism is being researched, called ***Eltoo.*** Eltoo might be a future enhancement in Lightning Network. It will depend on a new hash-type called `SIGHASH_ANYPREVOUT`. Until `SIGHASH_ANYPREVOUT` does not get added to Bitcoin script, Eltoo cannot be implemented. Bitcoin has very stringent enhancement mechanism where most stakeholders need to agree on a new enhancements and especially its large developer community which means if `SIGHASH_ANYPREVOUT` has unacceptable risks it may never get accepted. Or a different enhancement may solve this problem. Till that time, we need to live with the drawback and take enough precautions to not lose funds.

# [Routing mechanism and considerations](#toc.xhtml#s290a)

When Alice wants to pay Dave, she will need to find route to Dave in such a way that paying side of each channel in the route has enough funds so that the payment is successful. This is called ***source-routing***. As Alice’s node tries to find route to Dave, it looks for channel capacity, which is the combined value locked in the channel. Sometimes channel capacity is high enough, but the sending end of the channel does not have enough funds; this may lead to failure to process.

This information needs to be collected so that the channel can be avoided the next time a similar payment requirement arises. Additionally, nodes and channels can be rated based on past breaches.

The following are the considerations that need to be made while finding the route to the target receiver:

*   Channel capacity is high enough
*   Past failures due to the lack of paying side funds
*   Past channel breaches by nodes
*   Fee charged by node to forward payment request

# [Trampoline nodes](#toc.xhtml#s291a)

One of the challenges nodes face is finding a route that is cheap and holds enough capacity at each channel. This requires constant update of network topology. This is fine till the network is not big, but as we are seeing a rapid rise in adoption, this is becoming a problem.

Trampoline nodes are special nodes in Lightning Networks that have the sole responsibility of maintaining the current network topology by updating it frequently. So, a node needs to maintain partial network topology only to connect to trampoline nodes or to all nearby nodes.

A trampoline node maintains information about all the nodes in Lightning Network and may depend on other Trampoline nodes to extend routing beyond its subnet. This way, no node needs to maintain information about the whole network.

Trampoline nodes allow non-custodial mobile wallets to instantly send Lighting payments across the globe, without the need for large memory and processing.

Payment routing using trampoline node is illustrated in the following diagram:

![](images/Figure-13.21.jpg)

**Figure 13.21:** Sending node taking help of trampoline node to find a route to receiving node

# [Channel management](#toc.xhtml#s292a)

A channel can be created only to serve requests between peers and is mostly hidden from the rest of the network. These are called **private channels**. On the other hand, a channel can also be public and can be used by other nodes to make routing connections with the rest of the network.

For a public channel, it is important that funds at both ends are balanced so that routing does not fail because of a lack of funds at the paying side. This requires active channel management and collaboration with peers. There are multiple ways to achieve this.

# [Circular rebalancing](#toc.xhtml#s293a)

One way to rebalance a channel is to pay to ourselves from one of our other channels.

This can be understood with the help of the following illustration:

![](images/Figure-13.22.jpg)

**Figure 13.22:** Circular rebalancing mechanism

Circular rebalancing is cheap as only off-chain transactions happen, but it requires at least one channel to be loaded at the opposite side.

# [Splicing](#toc.xhtml#s294a)

Circular rebalancing is the preferred rebalancing method, but it is not useful for merchants because merchants might be only receiving and not sending and so, may not have any channel to move funds to other channels.

Splicing allows change in channel capacity without the need to close or reopen a channel. Splicing requires modification of funding transaction while accepting all the incoming payment requests. This makes it quite complex to implement.

Splice-in means increasing the capacity of a channel. The following is splice-in in a nutshell:

![](images/Figure-13.23.jpg)

**Figure 13.23:** Splice-in in a nutshell

Splice-out means reducing the capacity of a channel. The following illustration is splice-out in a nutshell:

![](images/Figure-13.24.jpg)

**Figure 13.24:** Splice-out in a nutshell

This is only simplified representation of splice-in and splice-out. In-reality, the implementation will be more complex.

# [Lightning Loop or submarine swaps](#toc.xhtml#s295a)

Submarine swap, also called Lightning Loop, is another way to manage channels by moving funds in and out of a channel. Lightning Loop is based on the principle that HTLC can work on both on-chain and off-chain, and so, a swap provider can help move funds between off-chain and on-chain in a trustless manner.

Lightning Loop is another way a merchant can move funds to the other side of a channel without the complexity of splicing.

To move funds out of channel, a node sends funds through the channel through multiple hops to swap provider, which sends funds back to the node on chain, in effect, removing the funds from chain.

This can be understood with the help of the following illustration:

![](images/Figure-13.25.jpg)

**Figure 13.25:** Moving funds from channel to on-chain using Submarine Swap

The same method can be used to add funds from on chain using swap provider by carrying out the preceding process in the reverse direction.

Here’s the illustration of using Lightning Loop to move funds to my side of the channel from on-chain:

![](images/Figure-13.26.jpg)

**Figure 13.26:** Moving funds from on-chain to channel using Submarine Swap

# [Multi-Part Payments or MPP](#toc.xhtml#s296a)

Lightning Network is not suitable for transferring large value over channel network. This because to transfer value over channel network, only the channels that have sufficient balance at the sender’s side can be selected, and channels with large capacity are rare. So, it is difficult to build a route between sender and receiver if large value needs to be transferred. To overcome this problem, Lightning Network software sometimes splits value over multiple channels and finds separate routes for each split value. This is called ***Multi-Part Payments***.

This can be understood with the help of the following illustration:

![](images/Figure-13.27.jpg)

**Figure 13.27:** Multi-part payment

In the preceding diagram, Alice wants to send 100 m![](images/Bitcoin.jpg)to Bob, but there is no route to transfer it. To achieve this, Alice breaks the amount into 20 m![](images/Bitcoin.jpg), 30 m![](images/Bitcoin.jpg)`,` and 50 m![](images/Bitcoin.jpg)and then sends it through different routes. This way, Bob can receive 100 m![](images/Bitcoin.jpg)offline without the need to perform on-chain transactions.

# [End user experience](#toc.xhtml#s297a)

When we use Lightning Network to pay for a service, we need to create a channel to pay the peer as many times as we want till there is balance on the payee side of channel.

To make a payment or receive payments, we need to establish channel between our node and a few other nodes in the network. This requires channel management and may involve the following activities:

*   Create a channel with funds on our side, at the peer side, or at both ends.
*   Create turbo channels or wait for 3-6 confirmations before accepting or sending payments.
*   Actively balance channels so that payments can be sent as well as received.
*   Keep network topology up-to-date or use trampoline nodes to find the best routes.
*   Use watchtower service to avoid being cheated by peers.
*   Mutually or unilaterally close channels and monitor Bitcoin blockchain for a channel closure/breach event.

This might look scary, but many Lightning Network wallets take care of all these internally, and the user experience is seamless.

# [Lightning wallets](#toc.xhtml#s298a)

Lightning wallets are Bitcoin wallets, which also open and manage channels. A wallet may give more control to the user by allowing them to allocate funds and manage channels, or it may hide all the complexities from the user, making the experience seamless. A wallet may be custodial, in which funds are controlled by the wallet and the user only logs in and approves a transaction. On the other hand, in a non-custodial wallet, seed and keys for creating the wallet are with the user.

As Lightning wallets are creating and managing channels, they are also called **Lightning Nodes**.

Here are some of the popular Lightning wallets:

*Zap wallet, Muun wallet, Bluewallet, Breez wallet, Wallet of Satoshi, Bitcoin Lightning Wallet (BLW), Éclair Mobile, etc.*

# [Lightning invoice](#toc.xhtml#s299a)

You have learnt that when Alice purchases coffee from Bob, Bob generates secret hash so that Alice can make the payment. To achieve this, Bolt 11 explains the structure of the message that Bob needs to share with Alice, and it is called Lightning invoice.

Here, we have generated a lightning invoice from a merchant application and used an open-source application to decode it. Here’s a screenshot of the application:

![](images/Figure-13.28.jpg)

**Figure 13.28:** Lightning invoice information

We can see all the information it contains, and it will help Alice to create a transaction and send it to a channel through which the payment will get routed and reach Bob.

The requested string is just the QR code that Bob shares with Alice. So, Alice goes to Bob’s coffee shop. Bob requests payment by showing the QR code in his mobile phone wallet. Alice scans the QR code from her mobile wallet and makes the payment. This happens in a minute.

The following is the illustration of Lightning Network payment:

![](images/Figure-13.29.jpg)

**Figure 13.29:** Lightning network payment

# [LNURL](#toc.xhtml#s300a)

LNURL is a third layer over Lightning Network. It goes a step further and allows you to use Lightning Network to create a channel, make and receive payments, and even use it for authentication in a website.

LNURL pay links are reusable, so it does not require rescanning of invoice on every purchase. LNURL involves a server, and when the QR code is scanned, the scanning application contacts the LNURL server to perform the required service. This way, the sending of invoice happens without user interaction.

This allows to use Lightning Network for not just payments but also authentication. LNURL is used to implement a few other services, which are specified in the following URL:

**[https://github.com/fiatjaf/lnurl-rfc](https://github.com/fiatjaf/lnurl-rfc)**

LNURL Auth is one such service enabled by LNURL that allows you to log in to a website using Lightning wallet.

We will use the following website to demonstrate LNURL Auth:

**[https://lightninglogin.live/login](https://lightninglogin.live/login)**

The following is the LNURL:

![](images/Figure-13.30.jpg)

**Figure 13.30:** LNURL Auth for login to website

This decodes to the following:

lightNING:LNURL1DP68GURN8GHJ7MRFVA58GMNFDENKCMM8D9HZUMRFWEJJ7MR0VA5KU0MTXY7N2WTRX4JNYENXVVMXZVTZV43RWCN9XPSKVDECXY6NWEPHXG6KVCNYXEJRXWRPXVUNSVFK893K2CF5XENRXVNRVEJKVCFSVVURYDPCXCN8GCT884KX7EMFDCSMESJ7

We used an online application to decode this, and obtained the following URL:

**[https://lightninglogin.live/login?k1=59c5e2ffc6a1beb7be0af78157d725fbd6d38a398169cea46f32cfefa0c82486&tag=login](https://lightninglogin.live/login?k1=59c5e2ffc6a1beb7be0af78157d725fbd6d38a398169cea46f32cfefa0c82486&tag=login)**

A wallet that supports LNURL’s authentication service will be able to coordinate with the LNURL server to authenticate and log in to the server. A simple scanning of the QR code can allow a user to log in to a website, and they will not need any traditional methods of login.

# [Merchant integration](#toc.xhtml#s301a)

Lightning Network wallets allow any brick-and-mortar store to simply install a mobile wallet and accept payments. For online businesses, the BTCPay server provides easy integration of Lightning Wallet with online payment webpage. BTCPay is an open-source project. There are others, such as wooCommerce or CoinGate, that also provide Lightning Network integration.

# [Social media integrations](#toc.xhtml#s302a)

Twitter recently integrated with strike wallet. As of now, anyone with a strike wallet can receive bitcoins over Lightning Network channels, and anyone with a Lightning wallet can send bitcoins. This mean people can collaborate on a global scale and get paid for their services. Additionally, social service organizations can directly reach out to people working under tyrannical regimes and help them by paying bitcoins directly to them.

Telegram also has Lightning Network bot called **LNTXBOT,** which can be used to pay or request payments.

# [Adoption by exchanges](#toc.xhtml#s303a)

Some exchanges were quick to adopt Lightning Network. Zebpay, an Indian exchange, is one of them. There are many exchanges globally that also support the exchange of bitcoins with other currencies or cryptocurrencies using Lightning Network. Some of the popular exchanges are Bitfinex, Strike, OKEx, CashApp, Paxful, and so on.

# [Other cryptocurrencies](#toc.xhtml#s304a)

Lightning Network requires certain enhancements such as segregated witness to overcome the risk of transaction malleability and so on. There are many cryptocurrencies that use almost the same codebase and scripting language as Bitcoin. The enhancements that enabled Lightning Network on Bitcoin network may also enable Lightning Network on many other cryptocurrencies.

As of now, Litecoin is the only other cryptocurrency that has enabled Lightning Network on its network. A few other cryptocurrencies have shown interest, but none have added the required support for Lightning till date.

# [Cross-chain atomic swap](#toc.xhtml#s305a)

You learned how HTLC can be used to swap off-chain balance with on-chain balance using Submarine Swaps. Similarly, HTLC can be used to perform cross-chain swaps with another cryptocurrency. This has been demonstrated with Litecoin by the Litecoin founder Charlie Lee on 16 September, 2017. A 2-minute demo is available on YouTube titled `Lightning Cross-Blockchain Swap Between Bitcoin and Litecoin`:

**https://www.youtube.com/watch?v=cBVcgzEuJ7Q**

# [Network topology](#toc.xhtml#s306a)

Lightning Network is still evolving, and the structure of the network may change in the future. However, it seems that the overall network is trying to imitate postal network where individuals connect to a wallet provider, the wallet maintains channels with bigger hops, and bigger hops are connected to a few other similar hops to simplify forwarding.

As an end user, we never need to close our channel with the wallet. If we send and receive funds, this channel can continue for extended period; thus, the overall fee paid is negligible.

The following is the illustration of Lightning Network topology:

![](images/Figure-13.31.jpg)

**Figure 13.31:** Lightning network topology

In the preceding figure, we can see that there are thousands of nodes connected with channels. These are public channels, so they can be found and used to update topology.

# [Conclusion](#toc.xhtml#s307a)

In this chapter, you learned about the Lightning Network protocol, a layer-two protocol of Bitcoin. You learned how Bitcoin’s primitive scripting language makes reliable instant transaction possible and understood that Lightning Network has its open specification and messaging system to allow different software implementations to talk to each other.

You also learned about the nodes that help in routing payments or rebalancing of channels and about the ecosystem that is being built for and on Lightning Network.

This brings us to the end of the book. The intention of this book is to help build developer community for Bitcoin by making the reader aware of internal details of Bitcoin protocol, network, blockchain, transactions, enhancements etc. The more developer enters the Bitcoin development community the more secure and better Bitcoin will become which gives us hope for more decentralized future.

# [Points to remember](#toc.xhtml#s308a)

*   Lightning Network is layer-two protocol and uses Bitcoin transaction scripting.
*   It allows instant offline payment of bitcoins.
*   To perform offline transactions using Lightning Network, a channel is created between the sender and the receiver.
*   Offline transactions can be performed if the required funds are available at the sender’s end of channel.
*   Channels can be unilaterally closed, or a mutual closure can happen.
*   A channel breach is when an attacker closes a channel by publishing an older transaction.
*   Victim of a channel breach punishes attacker by publishing justice transaction, which contains revocation key provided by the attacker to pay itself the attacker’s funds.
*   A unidirectional channel has funds only at the sender’s end when the channel is created.
*   A bidirectional channel has funds locked at both ends of a channel.
*   A channel is created by locking funds in 2-of-2-multisig.
*   A payment can be made between two individuals who do not have direct channels by routing payments over multiple nodes passing through a sequence of channels.
*   Source routing is when the sender communicates with nodes to build network topology to find the best route to the destination.
*   Trampoline nodes help the sender find the best route.
*   Trampoline nodes maintain updated network topology, and the sender only needs partial topology.
*   Nodes need to remain online all the time; otherwise, a peer can publish an old transaction, and the offline node will lose funds.
*   Watchtower nodes can serve nodes by monitoring on-chain all the time and publish justice transaction if required.
*   Nodes can connect to watchtower server and update it regularly about channel states and justice transaction.
*   Circular rebalancing is a method in which a node can balance a channel by moving funds to its other channel, which is loaded at the peer side.
*   Submarine swaps or Lightning Loop node helps move on-chain funds to nodes at the end of channel or vice versa.
*   Splicing allows you to dynamically add or reduce capacity of a channel without bringing a channel offline.
*   Adding capacity of channel is called splice-in, and reducing capacity is called splice-out.
*   Multi-part payment allows a sender to send large value transactions over Lightning Network by splitting the amount into smaller values and sending them over different channels and routes.
*   Lightning Invoice is generated by merchant or receiver and can be in the form of QR code. It is used by a sender to make payment.
*   LNURL is a layer-three protocol.
*   LNURL provides a way to repeatedly make payment using single QR code.
*   With LNURL, one can perform various other tasks like authentication and creation of channels.

# [Questions](#toc.xhtml#s309a)

1.  Explain the difference between the exchange of messages between unidirectional and bidirectional channels.
2.  Why is it important for public routing nodes to keep the channel balanced?
3.  What are the benefits of using Trampoline nodes over source routing?
4.  Explain the benefits of using MPP.
5.  Fill in the blanks: 
    1.  Capacity of a channel can be increased by channel management technique called \_\_\_\_\_\_\_\_\_\_\_ .
    2.  Lightning Network can be used for authenticating a site by using LNURL \_\_\_\_\_\_\_ .
    3.  Lightning Network has been demonstrated to perform \_\_\_\_\_\_\_ \_\_\_\_\_\_ of values between Bitcoin node and Litecoin node.
6.  True/False: 
    1.  LNURL is layer-three protocol because it has its own messaging protocol that helps establish and perform Lightning Network operations.
    2.  Circular rebalancing is the best suited channel balancing method for merchants as they mostly always receive funds.
    3.  Turbo channels are without risks, so high-capacity channel can be opened.
    4.  Lightning Network usability depends on how well nodes are interconnected, which depends on its popularity.
7.  Create lists of custodial and non-custodial wallets.
8.  Install Lightning Network wallet, make a payment, and try to guess the steps that have happened in the background.

# [Index](#toc.xhtml#ind)

Symbols

51% attack [255](#c08.xhtml#page255)

A

Abstract section [62](#c05.xhtml#page62), [63](#c05.xhtml#page63)

address [280](#c09.xhtml#page280)\-[283](#c09.xhtml#page283)

address format [272](#c09.xhtml#page272), [450](#c12.xhtml#page450)\-[454](#c12.xhtml#page454)

address generation [450](#c12.xhtml#page450)\-[454](#c12.xhtml#page454)

B

bech32 format

advantages [450](#c12.xhtml#page450)

bech32 string

characters [451](#c12.xhtml#page451)

BGP hijacking attack [248](#c08.xhtml#page248)

bidirectional dual-funded channel

about [469](#c13.xhtml#page469)

channel creation [470](#c13.xhtml#page470), [471](#c13.xhtml#page471)

Bitcoin

about [56](#c04.xhtml#page56)

Byzantine general problem [25](#c02.xhtml#page25)\-[27](#c02.xhtml#page27)

Byzantine general problem solving [28](#c02.xhtml#page28)

characteristics [28](#c02.xhtml#page28)

defining [25](#c02.xhtml#page25)

developments [19](#c02.xhtml#page19)\-[22](#c02.xhtml#page22)

digital asset [28](#c02.xhtml#page28)\-[30](#c02.xhtml#page30)

learning [18](#c02.xhtml#page18), [19](#c02.xhtml#page19)

mining energy usage [238](#c08.xhtml#page238)\-[240](#c08.xhtml#page240)

overview [22](#c02.xhtml#page22)\-[24](#c02.xhtml#page24)

Bitcoin consensus network

about [37](#c03.xhtml#page37)

Blockchain [39](#c03.xhtml#page39)

consensus rules [39](#c03.xhtml#page39)

cryptography [41](#c03.xhtml#page41)

gossip protocol [42](#c03.xhtml#page42)

mempool [41](#c03.xhtml#page41)

proof of work (PoW) [39](#c03.xhtml#page39)\-[41](#c03.xhtml#page41)

protocol [41](#c03.xhtml#page41)

transaction [38](#c03.xhtml#page38)

validating nodes [41](#c03.xhtml#page41)

Bitcoin Core

installing [95](#c06.xhtml#page95)

Bitcoin Core client [96](#c06.xhtml#page96)

Bitcoin Core server

running [95](#c06.xhtml#page95)

Bitcoin ecosystem

about [9](#c01.xhtml#page9)

education [10](#c01.xhtml#page10)

exchanges [11](#c01.xhtml#page11)

mining [10](#c01.xhtml#page10), [11](#c01.xhtml#page11)

mining pools [10](#c01.xhtml#page10), [11](#c01.xhtml#page11)

nodes [10](#c01.xhtml#page10)

online help [10](#c01.xhtml#page10)

payments [11](#c01.xhtml#page11)

training [10](#c01.xhtml#page10)

wallets [10](#c01.xhtml#page10)

Bitcoin mining [55](#c04.xhtml#page55), [56](#c04.xhtml#page56)

Bitcoin mining centralization [254](#c08.xhtml#page254)

Bitcoin network security

about [42](#c03.xhtml#page42)

factors [42](#c03.xhtml#page42), [43](#c03.xhtml#page43)

Bitcoin network topology

about [34](#c03.xhtml#page34), [35](#c03.xhtml#page35), [161](#c07.xhtml#page161)

mining nodes [35](#c03.xhtml#page35), [36](#c03.xhtml#page36)

nodes [162](#c07.xhtml#page162)

Simplified Payment Verification (SPV) [37](#c03.xhtml#page37)

Bitcoin software [95](#c06.xhtml#page95)

Bitcoin theft [242](#c08.xhtml#page242)

Bitcoin transactions

scripting [308](#c10.xhtml#page308)

Bitcoin, use cases

about [47](#c04.xhtml#page47)

bitcoin at brick-and-mortar store [52](#c04.xhtml#page52)

bitcoin by online merchant [49](#c04.xhtml#page49)\-[52](#c04.xhtml#page52)

bitcoin for expenses, using [54](#c04.xhtml#page54)

Bitcoin for remittance [54](#c04.xhtml#page54), [55](#c04.xhtml#page55)

Bitcoin for social cause [55](#c04.xhtml#page55)

bitcoin for traveling, using [54](#c04.xhtml#page54)

Bitcoin mining [55](#c04.xhtml#page55), [56](#c04.xhtml#page56)

bitcoin, paying as salary [53](#c04.xhtml#page53)

bitcoin, receiving as salary [53](#c04.xhtml#page53)

investing [49](#c04.xhtml#page49)

saving [49](#c04.xhtml#page49)

trading [47](#c04.xhtml#page47), [48](#c04.xhtml#page48)

Bit-gold [21](#c02.xhtml#page21)

bits [107](#c06.xhtml#page107), [108](#c06.xhtml#page108)

blacklist addresses [251](#c08.xhtml#page251)

block broadcasting

about [199](#c07.xhtml#page199)

compact block announcements [206](#c07.xhtml#page206), [207](#c07.xhtml#page207)

direct headers announcements [201](#c07.xhtml#page201), [202](#c07.xhtml#page202), [205](#c07.xhtml#page205), [206](#c07.xhtml#page206)

methods [199](#c07.xhtml#page199)

unsolicited block push [200](#c07.xhtml#page200), [201](#c07.xhtml#page201)

Blockchain

about [98](#c06.xhtml#page98)

block header [100](#c06.xhtml#page100)\-[102](#c06.xhtml#page102)

blocks and indexes [99](#c06.xhtml#page99), [100](#c06.xhtml#page100)

block version [103](#c06.xhtml#page103), [104](#c06.xhtml#page104)

genesis block [98](#c06.xhtml#page98), [99](#c06.xhtml#page99)

timestamp [105](#c06.xhtml#page105)

blockchain ecosystem

about [2](#c01.xhtml#page2), [7](#c01.xhtml#page7)

auditing [8](#c01.xhtml#page8)

compliance [8](#c01.xhtml#page8)

decentralized applications (DApps) [9](#c01.xhtml#page9)

decentralized finance (DeFi) [9](#c01.xhtml#page9)

fungible token [9](#c01.xhtml#page9)

medium of exchange [8](#c01.xhtml#page8)

non-fungible token (NFT) [9](#c01.xhtml#page9)

permissioned blockchain [8](#c01.xhtml#page8)

permissionless blockchain [8](#c01.xhtml#page8)

private blockchain [8](#c01.xhtml#page8)

public blockchain [8](#c01.xhtml#page8)

record keeping [8](#c01.xhtml#page8)

store-of-value [8](#c01.xhtml#page8)

tokens [9](#c01.xhtml#page9)

block header

about [100](#c06.xhtml#page100)\-[102](#c06.xhtml#page102)

bits [107](#c06.xhtml#page107), [108](#c06.xhtml#page108)

Merkle Root [105](#c06.xhtml#page105)\-[107](#c06.xhtml#page107)

nonce [107](#c06.xhtml#page107), [108](#c06.xhtml#page108)

previous block hash [104](#c06.xhtml#page104)

block reward [137](#c06.xhtml#page137), [138](#c06.xhtml#page138)

block size limitation

about [224](#c08.xhtml#page224)

blockchain size effect [226](#c08.xhtml#page226), [227](#c08.xhtml#page227)

transaction verification effect [224](#c08.xhtml#page224), [225](#c08.xhtml#page225)

block time limitation [227](#c08.xhtml#page227)\-[229](#c08.xhtml#page229)

block version [103](#c06.xhtml#page103), [104](#c06.xhtml#page104)

Bolt specification [463](#c13.xhtml#page463)

Border Gateway Protocol (BGP) [248](#c08.xhtml#page248)

brute force attack [242](#c08.xhtml#page242)

bug exploit [258](#c08.xhtml#page258)

Byzantine general problem [25](#c02.xhtml#page25)\-[27](#c02.xhtml#page27)

C

Calculation section [81](#c05.xhtml#page81)\-[88](#c05.xhtml#page88)

centralized exchanges [47](#c04.xhtml#page47)

channel closure

about [467](#c13.xhtml#page467)

mutually agreed close [467](#c13.xhtml#page467)

revoked transaction close [468](#c13.xhtml#page468), [469](#c13.xhtml#page469)

unilateral close [468](#c13.xhtml#page468)

channel management

about [478](#c13.xhtml#page478)

circular rebalancing [478](#c13.xhtml#page478), [479](#c13.xhtml#page479)

Lightning Loop [480](#c13.xhtml#page480), [481](#c13.xhtml#page481)

splicing [479](#c13.xhtml#page479), [480](#c13.xhtml#page480)

submarine swaps [480](#c13.xhtml#page480), [481](#c13.xhtml#page481)

channel monitoring

about [475](#c13.xhtml#page475)

watchtower [475](#c13.xhtml#page475), [476](#c13.xhtml#page476)

charity use case [393](#c11.xhtml#page393)\-[397](#c11.xhtml#page397)

child private key [290](#c09.xhtml#page290)\-[295](#c09.xhtml#page295)

child public key [291](#c09.xhtml#page291)\-[293](#c09.xhtml#page293)

circular rebalancing [478](#c13.xhtml#page478)

CoinJoin [236](#c08.xhtml#page236)

collaborative transactions

about [388](#c11.xhtml#page388)\-[392](#c11.xhtml#page392)

charity use case [393](#c11.xhtml#page393)\-[397](#c11.xhtml#page397)

planned contribution, within group [406](#c11.xhtml#page406)\-[410](#c11.xhtml#page410)

subsidy use case [397](#c11.xhtml#page397)\-[406](#c11.xhtml#page406)

collision attack [243](#c08.xhtml#page243)

Combining Value section [79](#c05.xhtml#page79)

compact block announcements [206](#c07.xhtml#page206), [207](#c07.xhtml#page207)

Conclusion section [89](#c05.xhtml#page89)

connected peers, offline payment

about [464](#c13.xhtml#page464)

channel closure [467](#c13.xhtml#page467)

channel creation [464](#c13.xhtml#page464), [465](#c13.xhtml#page465)

offline transactions [465](#c13.xhtml#page465)\-[467](#c13.xhtml#page467)

cryptocurrency

about [2](#c01.xhtml#page2)\-[4](#c01.xhtml#page4), [486](#c13.xhtml#page486)

cross-chain atomic swap [487](#c13.xhtml#page487)

finance [5](#c01.xhtml#page5), [6](#c01.xhtml#page6)

multichain connectors [6](#c01.xhtml#page6)

Oracle [6](#c01.xhtml#page6)

payments [5](#c01.xhtml#page5), [6](#c01.xhtml#page6)

privacy [6](#c01.xhtml#page6)

Stablecoin [6](#c01.xhtml#page6)

store-of-value [5](#c01.xhtml#page5), [6](#c01.xhtml#page6)

token platforms [5](#c01.xhtml#page5)

value proposition [4](#c01.xhtml#page4)

cryptocurrency regulations

about [56](#c04.xhtml#page56)\-[58](#c04.xhtml#page58)

contentious [57](#c04.xhtml#page57)

permissive [56](#c04.xhtml#page56)

prohibitive [57](#c04.xhtml#page57)

restrictive [56](#c04.xhtml#page56)

cryptographic

exploiting [242](#c08.xhtml#page242)

D

decentralized applications (DApps) [9](#c01.xhtml#page9)

Decentralized Autonomous Organizations (DAO) [47](#c04.xhtml#page47)

decentralized exchanges (DEX) [47](#c04.xhtml#page47)

decentralized finance (DeFi) [5](#c01.xhtml#page5), [9](#c01.xhtml#page9)

delay attack [249](#c08.xhtml#page249)

Denial-of-Service (DoS) attack [183](#c07.xhtml#page183), [256](#c08.xhtml#page256)

DER encoding

components [324](#c10.xhtml#page324)

design limitations

about [224](#c08.xhtml#page224)

block size limitation [224](#c08.xhtml#page224)

block time limitation [227](#c08.xhtml#page227)\-[229](#c08.xhtml#page229)

privacy and scaling solutions [229](#c08.xhtml#page229)

privacy limitation [229](#c08.xhtml#page229)

digital property

about [358](#c11.xhtml#page358)

document timestamping [360](#c11.xhtml#page360)\-[363](#c11.xhtml#page363)

Digital Signatures [65](#c05.xhtml#page65)

Directed Acyclic Graph (DAG) [3](#c01.xhtml#page3)

direct headers announcements [201](#c07.xhtml#page201)\-[206](#c07.xhtml#page206)

Direct Headers Announcements [200](#c07.xhtml#page200)

Disk Space section [76](#c05.xhtml#page76)

Distinguished Encoding Rules (DER) [323](#c10.xhtml#page323)

Distributed Ledger Technology (DLT) [3](#c01.xhtml#page3)

document timestamping [359](#c11.xhtml#page359)\-[363](#c11.xhtml#page363)

dusting attack [244](#c08.xhtml#page244), [245](#c08.xhtml#page245)

E

elliptic curve cryptography [278](#c09.xhtml#page278)

Elliptic Curve Digital Signature Algorithm (ECDSA) [278](#c09.xhtml#page278)

empty block mining [252](#c08.xhtml#page252), [253](#c08.xhtml#page253)

end user experience

about [482](#c13.xhtml#page482), [483](#c13.xhtml#page483)

exchange, adopting [486](#c13.xhtml#page486)

Lightning invoice [483](#c13.xhtml#page483), [484](#c13.xhtml#page484)

Lightning wallets [483](#c13.xhtml#page483)

LNURL [485](#c13.xhtml#page485)

merchant integration [486](#c13.xhtml#page486)

social media integration [486](#c13.xhtml#page486)

Ethereum [5](#c01.xhtml#page5)

exchanges

about [11](#c01.xhtml#page11)

custodial exchange [12](#c01.xhtml#page12)

non-custodial exchange [12](#c01.xhtml#page12)

types [46](#c04.xhtml#page46)

extended keys

about [297](#c09.xhtml#page297), [298](#c09.xhtml#page298)

extended private keys [300](#c09.xhtml#page300)\-[302](#c09.xhtml#page302)

extended public keys [300](#c09.xhtml#page300)\-[302](#c09.xhtml#page302)

master extended public keys [299](#c09.xhtml#page299)

extended private keys [300](#c09.xhtml#page300)\-[302](#c09.xhtml#page302)

extended public keys [300](#c09.xhtml#page300)\-[302](#c09.xhtml#page302)

F

Fast Internet Bitcoin Relay Engine (FIBRE) [226](#c08.xhtml#page226)

frauds and robbery [259](#c08.xhtml#page259)

full node [37](#c03.xhtml#page37)

G

Galois field [278](#c09.xhtml#page278)

genesis block [98](#c06.xhtml#page98)

H

hardened child keys

deriving [295](#c09.xhtml#page295)\-[297](#c09.xhtml#page297)

hardened derivation [295](#c09.xhtml#page295)

Hash-based Message Authentication Code (HMAC) [287](#c09.xhtml#page287)

Hashing [65](#c05.xhtml#page65)

hash rate [250](#c08.xhtml#page250)

Hash Time Locked Contract (HTLC) [471](#c13.xhtml#page471)

Headers First method [186](#c07.xhtml#page186)

hidden bugs [258](#c08.xhtml#page258)

Hierarchical Deterministic (HD) wallet

about [284](#c09.xhtml#page284)\-[288](#c09.xhtml#page288)

extended keys [297](#c09.xhtml#page297), [298](#c09.xhtml#page298)

key derivation path [302](#c09.xhtml#page302), [303](#c09.xhtml#page303)

master key generation [288](#c09.xhtml#page288), [289](#c09.xhtml#page289)

High Bandwidth Compact Block Announcements [207](#c07.xhtml#page207)\-[209](#c07.xhtml#page209), [214](#c07.xhtml#page214), [215](#c07.xhtml#page215)

High Bandwidth Relay [200](#c07.xhtml#page200)

Hyperledger Fabric [8](#c01.xhtml#page8)

I

Incentive section [74](#c05.xhtml#page74), [75](#c05.xhtml#page75)

Initial Block Download (IBD) [186](#c07.xhtml#page186)

Initial Coin Offering (ICO) [5](#c01.xhtml#page5), [9](#c01.xhtml#page9)

instant exchange [47](#c04.xhtml#page47)

J

justice transaction

about [469](#c13.xhtml#page469)

drawback [477](#c13.xhtml#page477)

justice transaction

drawback [476](#c13.xhtml#page476)

K

key derivation

child private key [290](#c09.xhtml#page290), [291](#c09.xhtml#page291), [294](#c09.xhtml#page294), [295](#c09.xhtml#page295)

child public key [291](#c09.xhtml#page291)\-[293](#c09.xhtml#page293)

hardened child keys, deriving [295](#c09.xhtml#page295)\-[297](#c09.xhtml#page297)

parent private key [290](#c09.xhtml#page290)\-[295](#c09.xhtml#page295)

parent public key [291](#c09.xhtml#page291)\-[293](#c09.xhtml#page293)

key derivation path [302](#c09.xhtml#page302), [303](#c09.xhtml#page303)

L

Lightning invoice [484](#c13.xhtml#page484)

Lightning Loop [480](#c13.xhtml#page480), [481](#c13.xhtml#page481)

Lightning Network

about [11](#c01.xhtml#page11), [51](#c04.xhtml#page51), [235](#c08.xhtml#page235)

connected peers payment [460](#c13.xhtml#page460)\-[462](#c13.xhtml#page462)

multiple channel payment [462](#c13.xhtml#page462), [463](#c13.xhtml#page463)

working [460](#c13.xhtml#page460)

Lightning Network bot (LNTXBOT) [486](#c13.xhtml#page486)

Lightning Network, contract

about [464](#c13.xhtml#page464)

bidirectional dual-funded channel [469](#c13.xhtml#page469)

connected peers, offline payments [464](#c13.xhtml#page464)

intermediaries [471](#c13.xhtml#page471)\-[474](#c13.xhtml#page474)

Lightning network topology [487](#c13.xhtml#page487)

Lightning Nodes [483](#c13.xhtml#page483)

LN-penalty [476](#c13.xhtml#page476)

LNURL [485](#c13.xhtml#page485)

Low Bandwidth Compact Block Announcements [215](#c07.xhtml#page215)\-[218](#c07.xhtml#page218)

Low Bandwidth Relay [200](#c07.xhtml#page200)

low entropy attack [242](#c08.xhtml#page242)

M

malicious hackers [242](#c08.xhtml#page242)

malware [243](#c08.xhtml#page243)

master extended public keys [299](#c09.xhtml#page299)

master key generation [288](#c09.xhtml#page288), [289](#c09.xhtml#page289)

mempool [148](#c06.xhtml#page148)\-[155](#c06.xhtml#page155)

mempool flood attack [245](#c08.xhtml#page245)

Merkle proof [78](#c05.xhtml#page78)

Merkle Root [105](#c06.xhtml#page105), [106](#c06.xhtml#page106), [107](#c06.xhtml#page107)

Merklized Abstract Syntax Trees (MAST) [231](#c08.xhtml#page231)\-[233](#c08.xhtml#page233)

mining [136](#c06.xhtml#page136), [137](#c06.xhtml#page137)

mining nodes

full node [37](#c03.xhtml#page37)

pool mining [36](#c03.xhtml#page36)

solo mining [36](#c03.xhtml#page36)

mining profitability

about [137](#c06.xhtml#page137)

block reward [137](#c06.xhtml#page137), [138](#c06.xhtml#page138)

coinbase transaction amount verification [140](#c06.xhtml#page140)

mining cost [141](#c06.xhtml#page141)\-[148](#c06.xhtml#page148)

transaction fee [138](#c06.xhtml#page138)\-[140](#c06.xhtml#page140)

mnemonic code [267](#c09.xhtml#page267)\-[271](#c09.xhtml#page271)

Multi-Part Payments (MPP) [481](#c13.xhtml#page481), [482](#c13.xhtml#page482)

N

Native P2WPKH [433](#c12.xhtml#page433)\-[436](#c12.xhtml#page436)

Native P2WSH [436](#c12.xhtml#page436)\-[439](#c12.xhtml#page439)

Native SegWit transaction scripts

about [433](#c12.xhtml#page433)

Native P2WPKH [433](#c12.xhtml#page433)\-[436](#c12.xhtml#page436)

Native P2WSH [436](#c12.xhtml#page436)\-[439](#c12.xhtml#page439)

network messaging

about [167](#c07.xhtml#page167)

block broadcasting [199](#c07.xhtml#page199)

blockchain, synchronizing [195](#c07.xhtml#page195)

connection, establishing [168](#c07.xhtml#page168)\-[182](#c07.xhtml#page182)

disconnecting, with inactive peer [182](#c07.xhtml#page182), [183](#c07.xhtml#page183)

full blockchain, receiving [186](#c07.xhtml#page186)\-[188](#c07.xhtml#page188), [193](#c07.xhtml#page193)\-[195](#c07.xhtml#page195)

message format [167](#c07.xhtml#page167), [168](#c07.xhtml#page168)

node discovery [183](#c07.xhtml#page183)\-[186](#c07.xhtml#page186)

transaction broadcasting [195](#c07.xhtml#page195)\-[199](#c07.xhtml#page199)

network partitioning [248](#c08.xhtml#page248)

network partitioning attack [248](#c08.xhtml#page248), [249](#c08.xhtml#page249)

Network section [70](#c05.xhtml#page70)\-[72](#c05.xhtml#page72)

node bootstrapping [162](#c07.xhtml#page162)\-[167](#c07.xhtml#page167)

nonce [107](#c06.xhtml#page107), [108](#c06.xhtml#page108)

non-fungible token (NFT) [5](#c01.xhtml#page5), [9](#c01.xhtml#page9)

O

opcodes [309](#c10.xhtml#page309)\-[313](#c10.xhtml#page313)

Oracle [6](#c01.xhtml#page6)

P

P2PKH transaction

building [343](#c10.xhtml#page343)\-[348](#c10.xhtml#page348)

P2SH transaction

building [348](#c10.xhtml#page348)\-[354](#c10.xhtml#page354)

parent private key [290](#c09.xhtml#page290)\-[295](#c09.xhtml#page295)

parent public key [291](#c09.xhtml#page291)\-[293](#c09.xhtml#page293)

Pay-2-Multisig (P2MS) [328](#c10.xhtml#page328), [329](#c10.xhtml#page329)

Pay-2-Script-Hash (P2SH) [329](#c10.xhtml#page329)

payment solution, smart contract

escrow payment [382](#c11.xhtml#page382)

multi-signature payment [372](#c11.xhtml#page372)

relative locktime payment, improvement [373](#c11.xhtml#page373)\-[381](#c11.xhtml#page381)

Pay-to-Public-Key-Hash (P2PKH) [282](#c09.xhtml#page282), [317](#c10.xhtml#page317), [318](#c10.xhtml#page318)

Pay-to-Public-Key (P2PK)

about [317](#c10.xhtml#page317)

drawbacks [317](#c10.xhtml#page317)

Pay-to-Script-Hash (P2SH) [282](#c09.xhtml#page282), [330](#c10.xhtml#page330)\-[334](#c10.xhtml#page334)

peer-to-peer exchange [46](#c04.xhtml#page46)

permissioned blockchain [8](#c01.xhtml#page8)

permissionless blockchain [8](#c01.xhtml#page8)

pool mining [36](#c03.xhtml#page36)

post fix notation [309](#c10.xhtml#page309)

precomputed hashes [243](#c08.xhtml#page243)

previous block hash [104](#c06.xhtml#page104)

privacy and scaling solutions

CoinJoin [236](#c08.xhtml#page236)

hardware improvement [230](#c08.xhtml#page230)

Lightning Network [235](#c08.xhtml#page235)

Merklized Abstract Syntax Trees (MAST) [231](#c08.xhtml#page231)\-[233](#c08.xhtml#page233)

signature aggregation [230](#c08.xhtml#page230), [231](#c08.xhtml#page231)

Taproot [233](#c08.xhtml#page233)\-[235](#c08.xhtml#page235)

Tumbler services [237](#c08.xhtml#page237)

Utreexo accumulators [230](#c08.xhtml#page230)

privacy limitation [229](#c08.xhtml#page229)

Privacy section [80](#c05.xhtml#page80), [81](#c05.xhtml#page81)

private blockchain [8](#c01.xhtml#page8)

private channels [478](#c13.xhtml#page478)

private key

about [272](#c09.xhtml#page272)\-[275](#c09.xhtml#page275)

format [272](#c09.xhtml#page272)

proof of work [35](#c03.xhtml#page35)

Proof-of-Work section [68](#c05.xhtml#page68)\-[70](#c05.xhtml#page70)

public blockchain [8](#c01.xhtml#page8)

public key

about [276](#c09.xhtml#page276)\-[280](#c09.xhtml#page280)

format [272](#c09.xhtml#page272)

public-key-hash (PKH) [281](#c09.xhtml#page281)

Python

indexes, querying [96](#c06.xhtml#page96)\-[98](#c06.xhtml#page98)

Q

quantum computing attack [257](#c08.xhtml#page257), [258](#c08.xhtml#page258)

quantum decoherence [257](#c08.xhtml#page257)

R

rainbow tables [243](#c08.xhtml#page243)

ransomware [243](#c08.xhtml#page243)

reorg [258](#c08.xhtml#page258)

replay attack [251](#c08.xhtml#page251), [252](#c08.xhtml#page252)

retail exchange [47](#c04.xhtml#page47)

reverse polish notation [309](#c10.xhtml#page309)

routing considerations [477](#c13.xhtml#page477)

routing mechanism

about [477](#c13.xhtml#page477)

channel management [478](#c13.xhtml#page478)

Multi-Part Payments (MPP) [481](#c13.xhtml#page481), [482](#c13.xhtml#page482)

trampoline node [477](#c13.xhtml#page477), [478](#c13.xhtml#page478)

S

script opcodes [358](#c11.xhtml#page358)

scriptSig [308](#c10.xhtml#page308)

Security Token Offering (STO) [9](#c01.xhtml#page9)

seed server [163](#c07.xhtml#page163)

segregated witness

about [414](#c12.xhtml#page414), [417](#c12.xhtml#page417)\-[419](#c12.xhtml#page419)

coinbase transaction [420](#c12.xhtml#page420)\-[425](#c12.xhtml#page425)

scaling solution [426](#c12.xhtml#page426)\-[432](#c12.xhtml#page432)

transaction fee calculation [432](#c12.xhtml#page432), [433](#c12.xhtml#page433)

transaction structure [419](#c12.xhtml#page419)

User Activated Soft Fork (UASF) [419](#c12.xhtml#page419)

selfish mining [245](#c08.xhtml#page245)\-[247](#c08.xhtml#page247)

serialized block

about [108](#c06.xhtml#page108)

block file [110](#c06.xhtml#page110)\-[115](#c06.xhtml#page115)

block traversal, with block indexes [116](#c06.xhtml#page116)\-[121](#c06.xhtml#page121)

magic number [109](#c06.xhtml#page109)

sigcheck method [448](#c12.xhtml#page448)

sighash types

about [314](#c10.xhtml#page314)

SIGHASH\_ALL [315](#c10.xhtml#page315), [316](#c10.xhtml#page316)

signature preimage

preparing [319](#c10.xhtml#page319)\-[328](#c10.xhtml#page328)

signature verification

about [313](#c10.xhtml#page313), [314](#c10.xhtml#page314), [446](#c12.xhtml#page446)\-[450](#c12.xhtml#page450)

Pay-to-Multisig (P2MS) [328](#c10.xhtml#page328), [329](#c10.xhtml#page329)

Pay-to-Public-Key-Hash (P2PKH) [317](#c10.xhtml#page317), [318](#c10.xhtml#page318)

Pay-to-Public-Key (P2PK) [317](#c10.xhtml#page317)

Pay-to-Script-Hash (P2SH) [329](#c10.xhtml#page329)\-[334](#c10.xhtml#page334)

SIGHASH\_ANYONECANPAY [316](#c10.xhtml#page316), [317](#c10.xhtml#page317)

SIGHASH\_NONE [316](#c10.xhtml#page316), [317](#c10.xhtml#page317)

SIGHASH\_SINGLE [316](#c10.xhtml#page316), [317](#c10.xhtml#page317)

Simplified Payment Verification section [77](#c05.xhtml#page77), [78](#c05.xhtml#page78)

Simplified Payment Verification (SPV) [37](#c03.xhtml#page37)

smart contract

about [5](#c01.xhtml#page5), [371](#c11.xhtml#page371)

limitations, on Bitcoin [372](#c11.xhtml#page372)

payment solution [372](#c11.xhtml#page372)

secret identifier [382](#c11.xhtml#page382)\-[388](#c11.xhtml#page388)

social media integration [486](#c13.xhtml#page486)

solo mining [36](#c03.xhtml#page36)

source-routing [477](#c13.xhtml#page477)

splicing [480](#c13.xhtml#page480)

Splitting Value section [79](#c05.xhtml#page79)

spyware [243](#c08.xhtml#page243)

Stablecoin [6](#c01.xhtml#page6)

standard scripts

about [433](#c12.xhtml#page433)

Native SegWit transaction scripts [433](#c12.xhtml#page433)

Wrapped SegWit scripts [439](#c12.xhtml#page439), [440](#c12.xhtml#page440)

submarine swaps [480](#c13.xhtml#page480), [481](#c13.xhtml#page481)

subsidy use case [397](#c11.xhtml#page397)\-[406](#c11.xhtml#page406)

Sybil attack [255](#c08.xhtml#page255)

T

Taproot [233](#c08.xhtml#page233)\-[235](#c08.xhtml#page235)

threats

about [241](#c08.xhtml#page241)

Bitcoin theft [242](#c08.xhtml#page242)

from central banks [241](#c08.xhtml#page241), [242](#c08.xhtml#page242)

from governments [241](#c08.xhtml#page241)

malicious hackers [242](#c08.xhtml#page242)

private keys, losing [244](#c08.xhtml#page244)

seed phrase, losing [244](#c08.xhtml#page244)

vulnerabilities [244](#c08.xhtml#page244)

time locked payment [363](#c11.xhtml#page363)\-[366](#c11.xhtml#page366)

time locked transactions

about [363](#c11.xhtml#page363)

relative locktime payment [366](#c11.xhtml#page366)\-[371](#c11.xhtml#page371)

time locked payment [363](#c11.xhtml#page363)\-[366](#c11.xhtml#page366)

timestamp [105](#c06.xhtml#page105)

Timestamp Server section [67](#c05.xhtml#page67), [68](#c05.xhtml#page68)

trampoline node [477](#c13.xhtml#page477), [478](#c13.xhtml#page478)

transaction malleability [244](#c08.xhtml#page244), [415](#c12.xhtml#page415)\-[417](#c12.xhtml#page417)

transactions

about [122](#c06.xhtml#page122)\-[133](#c06.xhtml#page133)

building [334](#c10.xhtml#page334)\-[343](#c10.xhtml#page343)

P2PKH transaction, building [343](#c10.xhtml#page343)\-[348](#c10.xhtml#page348)

P2SH transaction, building [348](#c10.xhtml#page348)\-[354](#c10.xhtml#page354)

Transaction section [64](#c05.xhtml#page64)\-[67](#c05.xhtml#page67)

trojan [243](#c08.xhtml#page243)

Tumbler services [237](#c08.xhtml#page237)

U

unsolicited block push [200](#c07.xhtml#page200), [201](#c07.xhtml#page201)

Unsolicited Block Push [199](#c07.xhtml#page199)

Unspent Transaction Output (UTXO) [133](#c06.xhtml#page133)\-[136](#c06.xhtml#page136)

User Activated Soft Fork (UASF) [419](#c12.xhtml#page419)

V

version message

field [170](#c07.xhtml#page170)

vulnerabilities, threats

BGP hijacking attack [248](#c08.xhtml#page248)

Bitcoin mining centralization [254](#c08.xhtml#page254)

blacklist addresses [251](#c08.xhtml#page251)

bug exploit [258](#c08.xhtml#page258)

delay attack [249](#c08.xhtml#page249)

Denial-of-Service (DoS) attack [256](#c08.xhtml#page256)

dusting attack [244](#c08.xhtml#page244), [245](#c08.xhtml#page245)

empty block mining [252](#c08.xhtml#page252), [253](#c08.xhtml#page253)

frauds and robbery [259](#c08.xhtml#page259)

hash rate, hiding [250](#c08.xhtml#page250)

hidden bugs [258](#c08.xhtml#page258)

mempool flood attack [245](#c08.xhtml#page245)

network partitioning attack [248](#c08.xhtml#page248), [249](#c08.xhtml#page249)

quantum computing attack [257](#c08.xhtml#page257), [258](#c08.xhtml#page258)

reorg [258](#c08.xhtml#page258)

replay attack [251](#c08.xhtml#page251), [252](#c08.xhtml#page252)

selfish mining [245](#c08.xhtml#page245)\-[247](#c08.xhtml#page247)

transaction malleability [244](#c08.xhtml#page244)

zero-confirmation attack [249](#c08.xhtml#page249), [250](#c08.xhtml#page250)

W

Wallet Import Format (WIF) [272](#c09.xhtml#page272)

watchtower [475](#c13.xhtml#page475), [476](#c13.xhtml#page476)

whitepaper

about [63](#c05.xhtml#page63), [64](#c05.xhtml#page64)

Abstract section [62](#c05.xhtml#page62), [63](#c05.xhtml#page63)

Calculation section [81](#c05.xhtml#page81)\-[88](#c05.xhtml#page88)

Combining Value section [79](#c05.xhtml#page79)

Conclusion section [89](#c05.xhtml#page89)

Disk Space section, reclaiming [76](#c05.xhtml#page76)

Incentive section [74](#c05.xhtml#page74), [75](#c05.xhtml#page75)

Network section [70](#c05.xhtml#page70)\-[72](#c05.xhtml#page72)

Privacy section [80](#c05.xhtml#page80), [81](#c05.xhtml#page81)

Proof-of-Work section [68](#c05.xhtml#page68)\-[70](#c05.xhtml#page70)

Simplified Payment Verification section [77](#c05.xhtml#page77), [78](#c05.xhtml#page78)

Splitting Value section [79](#c05.xhtml#page79)

Timestamp Server section [67](#c05.xhtml#page67), [68](#c05.xhtml#page68)

Transaction section [64](#c05.xhtml#page64)\-[67](#c05.xhtml#page67)

Wrapped SegWit scripts

about [439](#c12.xhtml#page439)

Wrapped P2WPKH or P2SH-P2WPKH [440](#c12.xhtml#page440), [441](#c12.xhtml#page441)

Wrapped P2WSH or P2SH-P2WSH [441](#c12.xhtml#page441)\-[445](#c12.xhtml#page445)

Z

zero-confirmation attack [249](#c08.xhtml#page249), [250](#c08.xhtml#page250)