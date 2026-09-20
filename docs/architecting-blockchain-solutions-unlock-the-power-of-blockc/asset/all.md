![](images/cover.jpg)

![image](images/cover.jpg)

# Architecting  
Blockchain  
Solutions

![](images/line.jpg)

# *Unlock the power of Blockchain to build Trustless  
networks, dApps, Tokens, and Virtual world*

![](images/line.jpg)

# Sathvik Vishwanath

![](images/logo.jpg)

[www.bpbonline.com](http://www.bpbonline.com)

Copyright © 2023 BPB Online

*All rights reserved.* No part of this book may be reproduced, stored in a retrieval system, or transmitted in any form or by any means, without the prior written permission of the publisher, except in the case of brief quotations embedded in critical articles or reviews.

Every effort has been made in the preparation of this book to ensure the accuracy of the information presented. However, the information contained in this book is sold without warranty, either express or implied. Neither the author, nor BPB Online or its dealers and distributors, will be held liable for any damages caused or alleged to have been caused directly or indirectly by this book.

BPB Online has endeavored to provide trademark information about all of the companies and products mentioned in this book by the appropriate use of capitals. However, BPB Online cannot guarantee the accuracy of this information.

**First published:** 2023

Published by BPB Online

WeWork

119 Marylebone Road

London NW1 5PU

**UK | UAE | INDIA | SINGAPORE**

ISBN 978-93-5551-322-9

**[www.bpbonline.com](http://www.bpbonline.com)**

# Dedicated to

*My beloved Parents:*

***Shri N K Vishwanath Gupta** and*

***Sahana Vishwanath***

*and to*

***Satoshi Nakamoto***

# About the Author

**Sathvik Vishwanath** is a successful entrepreneur and has always put his heart into innovative & disruptive technology! He has been the co-founder and CEO of Unocoin, one of India's leading cryptocurrency exchanges for nine years. He has been involved in the cryptocurrency and blockchain space since 2012, at a time when cryptocurrency was still a relatively new and little-understood concept in the country, and he has been instrumental in bringing Bitcoin and other digital assets to the mainstream in India.

Vishwanath has an engineering and entrepreneurship background and has founded several successful technology startups. He has a deep understanding of the technical, financial and political aspects of cryptocurrencies and blockchain technology, as well as its potential to disrupt traditional financial systems and enable new forms of value transfer.

Under Vishwanath's leadership, Unocoin has grown to become one of the largest and most reputable cryptocurrency exchanges in India, with over 2.5 million users. In addition to running the exchange, Vishwanath is also a vocal advocate for the adoption of cryptocurrency and blockchain technology in India and has worked closely with regulators and policymakers to shape the regulatory landscape for digital assets in the country.

Overall, Sathvik Vishwanath is a pioneer and thought leader in the Indian cryptocurrency and blockchain space. He has been featured in numerous media outlets, including the Economic Times and Business Insider, and has spoken on the topic at numerous conferences, events, and at TedX.

Vishwanath holds a bachelor's degree in electronics and communications from the Siddaganga Institute of Technology, Tumkur. He is also an alumnus of the prestigious Melbourne Business School, where he completed his Masters in Business and Information Technology.

# About the Reviewer

**Utkarsh Katiyar** is a passionate Software Developer with extensive professional experience in the domain of development of 4G/5G technology, building financial systems, NoSql and graph databases, blockchain technology, Byzantine-fault tolerant (P-BFT) based consensus algorithm in blockchain, end to end development and deployment of production grade blockchain systems, performance improvement of blockchain based systems, machine learning and inference performance optimizations for deep neural networks .

Utkarsh specializes in working with C and C++ 11, 17 programming languages with skills in various other programming languages such as Python, Java and Rust.

He has worked with companies likes Reliance Jio, Goldman Sachs and VMWare as a senior software engineer. Currently he is working with AMD as software system design engineer and part of ZenDNN CPU-Edge-inference team.

# Acknowledgement

There are a few people I want to thank for the continued and ongoing support they have given me during the writing of this book. First and foremost, I would like to thank my parents and my spouse Deepti Sathvik for continuously encouraging me for writing this book — I could have never completed this book without their support.

I am also thankful to numerous websites and published material on the web that has done its best to explain the various features of blockchain and its architecture. While this topic continues to be quite unorganized, my colleagues Shreya Jain and my editor Shashank Yabbot have done their best to get this book in shape in spite of the technology and its implementation is evolving every single day.

My gratitude also goes to the team at BPB Publications for being supportive enough to provide me quite a long time to finish the book as some of the topics in the book needed real-time updation while it is being written and edited. Without this, it was impossible to deep-dive into different categories of architecture into a single book, especially by not making it too voluminous.

Finally, I want to acknowledge my dedication to this revolutionary technology's torchbearers who make sure that it gets used wherever appropriate to bring the disruption.

Thank you

*\- Sathvik Vishwanath*

# Preface

This book provides a comprehensive overview of Blockchain technology and its architecture. It covers the fundamentals of Blockchain, including its origins and key concepts, as well as its potential applications in various industries.

The book is divided into 16 chapters, each focusing on a different aspect of Blockchain technology. The first few chapters provide a general overview of Blockchain and its key features, such as decentralization, immutability, and security. These chapters also explain the basics of Blockchain architecture and its various components, such as nodes, blocks, and consensus mechanisms.

In later chapters, the book delves into more advanced topics, such as different types of blockchains, their use cases, and various programming languages that can be used to implement them. These chapters also provide detailed, step-by-step guides on how to become a Blockchain architect while designing and implementing a Blockchain-based database for a specific project.

Throughout the book, real-life examples are used to illustrate the various concepts and techniques discussed. These examples help to bring the material to life and provide a deeper understanding of the potential of Blockchain technology.

Overall, this book is an excellent resource for anyone looking to learn about Blockchain technology and its architecture from the ground up. It is comprehensive, well-structured, and easy to understand, making it an excellent guide for beginners and experts alike. The overview of chapters covered is as per below:

**[Chapter 1](#c01.xhtml)** will cover essential topics like the history and origin of Blockchain, followed by the Importance and types of blockchain architecture.

**[Chapter 2](#c02.xhtml)** will cover database systems in general and their types. It also explains the difference between blockchains and databases.

**[Chapter 3](#c03.xhtml)** will introduce network architecture in general and the difference between centralized, decentralized, and distributed databases, followed by the components needed to run the blockchain.

**[Chapter 4](#c04.xhtml)** will cover cryptography and encryption in detail, followed by important concepts like hashing and Merkle needed to implement blockchain solutions.

**[Chapter 5](#c05.xhtml)** will cover basic concepts like the present digital era for transactions, bartering, basics of money, and banking.

**[Chapter 6](#c06.xhtml)** will cover various successful implementations of blockchains like Bitcoin, Ethereum, DeFi, Tokenization, and NFTs.

**[Chapter 7](#c07.xhtml)** continues to explain blockchain use cases in finance, government, and businesses in general.

**[Chapter 8](#c08.xhtml)** goes in-depth regarding nodes, then about types of nodes, and finally explores the Blockchain As A Service (BaaS) service providers that could be of help.

**[Chapter 9](#c09.xhtml)** covers the detailed study of consensus mechanisms including algorithms, proof of work, and energy problems surrounding blockchains. The later part of the chapter also focuses on different alternatives to proof of work and their advantages.

**[Chapter 10](#c10.xhtml)** is a detailed study of the necessary skills required to become a blockchain architect. It moves on to explain different examinations and certificates that can help someone become a blockchain architect.

**[Chapter 11](#c11.xhtml)** covers a few different programming languages like Python, JAVA, C++, Golang, Rust, Solidity and Viper that can be used to implement blockchains.

**[Chapter 12](#c12.xhtml)** covers another set of programming languages for blockchain implementation.

**[Chapter 13](#c13.xhtml)** covers the basics of IDEs, their types, and some widely used IDEs for various blockchain applications. It also covers setting up the online Remix IDE for solidity based smart contract development.

**[Chapter 14](#c14.xhtml)** explains how all the learnings so far come together to help the design, development, and implementation of blockchain.

**[Chapter 15](#c15.xhtml)** covers hands-on exercises of creating one's own ERC-20 tokens and NFTs on Ethereum blockchain.

**[Chapter 16](#c16.xhtml)** covers the recap of all previous chapters, the traits required to become a blockchain architect, its present job market outlook, and statistics, followed by the most popular positions in the industry and their salary structure.

# Code Bundle and Coloured Images

Please follow the link to download the  
***Code Bundle*** and the ***Coloured Images*** of the book:

# [https://rebrand.ly/5ugh1np](https://rebrand.ly/5ugh1np)

The code bundle for the book is also hosted on GitHub at **[https://github.com/bpbpublications/Architecting-Blockchain-Solutions](https://github.com/bpbpublications/Architecting-Blockchain-Solutions)**. In case there's an update to the code, it will be updated on the existing GitHub repository.

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

# [The Genesis of Blockchain](#toc.xhtml#c01)

# [Introduction](#toc.xhtml#s1a)

If you are aware of what cryptocurrencies are, there is a good chance you have heard of the term *blockchain*. For the uninitiated—blockchain is a mechanism in which virtual "*blocks"* are created linearly, all linked to each other, and where each of these blocks contains unique data like transaction details. The best-known use case of said technology so far is the Bitcoin blockchain. Even though blockchain technology originated as the base for a number of cryptocurrencies, in the years since its introduction, the tech has trickled into other businesses and industries, with several attributes that said businesses can benefit from. Indeed, in today's world, as everything around us steadily alters course to take up the digital road, blockchain solutions have proven to be integral for businesses that want to not only survive but also thrive.

We welcome you to the very first segment of our journey to learn about blockchain solutions and how they can be architected. In this chapter, we will go over blockchain's basics and why and how one should join in as blockchain radicalizes industries around the world as we know it.

# [Structure](#toc.xhtml#s2a)

The following topics will be covered in this chapter:

*   What is blockchain?
*   The background of blockchain: history and origin
*   The underlying architecture of a blockchain 
    *   Components of a blockchain architecture
*   How does a blockchain function?
*   Attributes of blockchain
*   Industries where blockchain solutions can be applied
*   How can blockchain solutions be useful for businesses? 
    *   Why can blockchain benefit businesses?
    *   Probable applications of blockchain for businesses
    *   Real-world use cases of blockchain in different businesses
    *   Blockchain as a service
*   The importance of architecting blockchain solutions 
    *   Types of blockchain architectures
*   How can you become a certified blockchain architect?
*   Who is a blockchain architect?
*   Why is becoming a blockchain architect a good career choice?
*   What skills do you need to become a blockchain architect?
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s3a)

In this chapter, we will be finding out about all the basic and important tidbits regarding blockchains, their underlying technology, and their properties, which will prove critical for all looking to make a career in blockchain. Then, we will see how blockchain solutions can benefit a range of businesses to understand its implications in various industries outside of the crypto space. The last part of this chapter will contain the importance of architecting blockchain solutions and how one can go about becoming a blockchain architect.

By the end of the chapter, we hope to impart all the benefits of a career in blockchain to you and help you figure out how to build that career.

# [First things first—understand what the blockchain is](#toc.xhtml#s4a)

As you can probably glean from its name, a blockchain is a series of virtual blocks containing data that are linked together by a digital chain. *Block + chain.*

The data stored on a blockchain is verified, updated in real-time, and encrypted. It gets distributed among users from a number of geographic locations. More information is added to a blockchain in the form of new blocks that are always added chronologically at the end of the chain, and any data once entered on a blockchain cannot be erased or changed. There are multiple types of blockchain, but the easiest way to understand the concepts of blockchain is to learn these in the context of Public blockchain. We shall be learning about the other types later in this chapter.

# [The background of blockchain: its history and origin](#toc.xhtml#s5a)

You might think of blockchain as a relatively young technology, but in truth, the origin of blockchain can be traced to decades back in 1982, when a cryptographer named David Chaum came up with the idea of a protocol similar to the blockchain we know today. In his dissertation, he talks about *"Computer Systems Established, Maintained, and Trusted by Mutually Suspicious Groups".* Then, in 1991, Stuart Haber and W. Scott Stornetta wanted to invent a mechanism to timestamp digital documents so they would be impossible to backdate or meddle with, and the idea they described also talked about a chain made of encrypted blocks. Immediately after, in 1992, Haber, Stornetta, and Dave Bayer further improved the design to create a system that let a number of document certificates are accumulated into one single block.

This technology of blocks secured by cryptography remained unused for over a decade after that, and then came Satoshi Nakamoto, the infamous anonymous creator of the OG cryptocurrency Bitcoin, that would go on to radicalize the world of finance.

What Nakamoto did in 2008 was to play with the old design and make it so that it would timestamp blocks without needing verification from a trusted party; they also stabilized the speed at which new blocks are added to the chain. Nakamoto now uses this technology to power Bitcoin and function as a distributed ledger that records all transactions performed on the Bitcoin network.

# [The underlying architecture of a blockchain](#toc.xhtml#s6a)

A blockchain is a decentralized network that ties together computing devices from all across the world—the devices are called nodes. So, a blockchain network does not need a centralized authority figure or an institution to authorize any transactions happening on the chain; the nodes act as network administrators instead. The blocks on the chain are timestamped and contain links to the blocks right before them.

Following these links would lead one all the way up to the first block in the chain.

# [The components of a blockchain architecture](#toc.xhtml#s7a)

The primary elements of a blockchain architecture are the following:

*   **Block:** A block on the chain keeps records of a number of transactions and the counterparties involved. A block contains its own hash, the hash code from the block before it, and a set of data that varies as per the nature of the blockchain (for instance, the blocks on the Bitcoin chain contain transaction details).
*   **Hash:** The hash of a block is sort of like a unique identification number. A block's hash is a mathematical function that transforms the input of any length into a fixed-length encrypted output. The hash for a block is calculated after its creation, and if a hacker tampers with the block somehow, its hash will change since the slightest change in the structure of the input would affect the output greatly. Therefore, if there is an attack on a blockchain, nodes can quickly identify it. The hash function is not an encryption that can be decrypted later. It is technically not possible to construct back the message by using the hash.
*   **Node:** As we have mentioned before, a node is a computing device on the blockchain network that participates in blockchain administration. Every node on a blockchain has a copy of the blockchain ledger.
*   **Miners:** These are the nodes that validate transactions, accumulate them into blocks, hash the blocks, and then add the blocks to the chain. A miner may have to solve complex mathematical problems as a part of the job, and they require special mining hardware and software for that.
*   **Consensus algorithm:** There is a set of rules, conditions, and agreements on every blockchain that all participants must follow while operating on the chain.

# [Functioning of a Blockchain](#toc.xhtml#s8a)

Let us see how a blockchain operates through an example.

Suppose there are three blocks on a chain, where each one contains its own hash and the hash of the previous block. Now, naturally, Block 1 will be an exception because it will not contain the hash of the block before it. The first block on a chain is known as the genesis block.

Now, if a hacker tries to manipulate the second block, its hash will change. This will make the next block being Block 3, and all subsequent blocks become invalid as the hash that the Block 3 is storing representing all the blocks till Block 2 will now contradict Block 3's new hash. The miners will neglect any blocks that are invalid.

Hashing and the consensus algorithm of a blockchain give it maximum security, along with its distributed peer-to-peer (P2P) structure. On a P2P network, anyone with an internet connection can participate—as long as the blockchain is public. And when a new participant comes up and becomes a node, they get a copy of the blockchain ledger, which they can use to verify the information stored on the blockchain and help keep the network secure.

When a miner creates a new block, all nodes on the network are alerted. They all then verify the block and, once satisfied, add it to their own copies of the blockchain ledger. This is how the nodes validate a block: they arrive at a consensus and collectively brand a block, legitimate or otherwise.

Now, nodes that are online are receiving, broadcasting, and saving all the latest blocks from and to other nodes, but any offline nodes are not able to do that. So, when an offline node comes back up online, it needs to catch up with the blockchain first thing by downloading all the blocks that were added to the chain while it was down. This procedure is referred to as "*synchronizing with the blockchain*".

# [Attributes of Blockchain](#toc.xhtml#s9a)

Now, let us take a look at the various qualities of blockchain that not only make it suitable for cryptocurrencies but also justify its widespread adoption across multiple industries.

*   **Cryptography:** Information on a blockchain is cryptographically secured, which makes it trustworthy.
*   **Decentralized:** The P2P network of nodes can access the distributed database, and a consensus algorithm takes care of network administration; therefore, no centralized authority can hoard power. Further, since there is no central storage of information, it takes a hacker an implausible amount of effort to hack a blockchain.
*   **Immutability:** As we know, data stored in the blocks cannot be altered or deleted.
*   **Transparency:** Of course, all users on the blockchain network can see and verify the information stored. Every node on a blockchain has the potential to store a complete copy of the blockchain ledger, and because all users on a blockchain are not nodes, nodes may occasionally be requested to send a copy of certain parts of their ledger or just the hash of previous blocks to a user, to ensure complete transparency. This way, nodes can also confirm for themselves that other nodes also have the exact same copy of the blockchain as them.
*   **Anonymity:** Every participant on a blockchain is given an address, which keeps them anonymous, protecting their personal data, especially on a public blockchain.
*   **Smart contracts:** Smart contracts are self-executing contracts stored on a blockchain that automatically execute when all predetermined terms and conditions are met. This makes transactions more trustworthy for the counterparties and further increases the security of a blockchain.
*   **Cost-effective:** As there are no centralized authorities or intermediaries on a blockchain, they reduce operational costs significantly.

# [Industries where blockchain solutions can be applied](#toc.xhtml#s10a)

Apart from the crypto industry, where the origin of blockchain tech lies, blockchain can work wonders in a number of other industries. In this part, we see some industries that can greatly benefit from the integration of blockchain solutions.

*   **The financial sector:** Now, this is one industry that stands to benefit immensely from the use of blockchain. Blockchain can do away with the security issues already plaguing financial institutions. Whether a transaction is done within the borders or internationally, blockchain can make it happen as quickly as it takes to create a new block (which could only be a few minutes). A blockchain operates 24/7 around the year since it is run by thousands of computers from all over the world, and even when a few of them are down, the other nodes keep the blockchain active. So in traditional finance, where users would have to wait around for hours to days for a transaction to complete in case, there is a holiday, blockchain renders that waiting unnecessarily. Plus, with blockchain, the transaction costs are also much lower.
*   **Healthcare and medical records keeping:** In healthcare, blockchain can be used to securely store patients' medical records. The decentralized records management system would do away with the need for an organization to administer patients' access to their records. Other advantages of blockchain in healthcare include the ability to pull up and verify prescriptions at any given point in time or automatically identify any possibilities of damaging drug interactions.
*   **Records of property:** The traditional method of documenting property rights involves a lot of paperwork, costs an unfortunate amount of time, and is entirely inefficient. However, blockchain here would help with faster and digital record keeping, and since the records would be transparent and there would be clear timestamps, it would be infinitely easier to scan documents and verify property rights.
*   **Know your customer (KYC) and anti-money laundering (AML):** In traditional finance and even with online retail stores, there are multi-step KYC and even AML procedures the institutions have to complete for every customer. However, with blockchain integrated here, when one institution does a KYC/AML check on a customer, instead of keeping it in a centralized database, it could be made available to other similar organizations through a blockchain. This would make the whole process easier for both the institutions and the customers.

# [How can blockchain solutions be useful for businesses?](#toc.xhtml#s11a)

We already know that blockchain can prove incredibly helpful for a wide range of businesses. Now we see why that is, some plausible applications of blockchain in business and even some real-world use cases.

# [Why can blockchain benefit businesses?](#toc.xhtml#s12a)

We have mentioned before that blockchain can prove incredibly helpful for a wide range of businesses. Now we see why that is.

Blockchain in businesses increases trust among the many entities that transact among themselves. There are four unique primary characteristics of blockchain that make it suitable for businesses.

*   First, with its distributed ledger, the participants on the network can access all information whenever they want, which both improves efficiency and builds trust.
*   Then there is the consensus algorithm, so the shared ledgers get updated only when a block is validated by all associated parties.
*   The immutability of the blockchain ensures that while more blocks can be added, none can be removed, and all transactions are permanently recorded.
*   Finally, a blockchain provides the maximum possible security, so on a blockchain meant for a business, only authorized entities would be allowed to create new blocks or access them. So all important information would stay between the trusted partners only.

Therefore, the primary benefit blockchain would give businesses is the aspect of utter and complete trust between the business partners. In businesses that deal with products ranging from financial services to food to logistics, blockchains can increase trust by helping all involved parties transact together and validate and share the stored records on a ledger share.

Blockchain also brings smart contracts into business. The transactions between partners or with customers are made easier with these automated contracts, that had only conclude when all the conditions set by both counterparties are made. Plus, blockchain integration in businesses also means there is little to no paperwork, not to mention a smoother experience for the customers. So there is efficiency all around.

# [Probable applications of blockchain in businesses](#toc.xhtml#s13a)

Across the world, the financial services industry and even some governments have already made good use of blockchain. By 2018 itself, 91% of the banks worldwide had started investing in blockchain solutions. Blockchain is used to register land titles in Georgia, and there are even platforms like Follow My Vote that make use of blockchain in the electoral process. As for other industries, blockchain can be very useful in businesses that deal with food distribution and retail, and of course, blockchain can be good for supply chain management for all businesses.

In the case of food distribution, farmers, processors, distributors, and retailers can all keep in constant touch through blockchain so as to make sure the food stays in good condition. This would lengthen their shelf lives and reduce wastage, among other benefits like better connections and tracking.

Plus, previously, the food industry has witnessed outbreaks of *E. Coli*, Typhoid, and other diseases through harmful content coming in contact with food accidentally. However, with blockchain, a portion of food can be tracked right from its origin to its delivery, so any contaminated food can be traced back to its origin. This would allow the companies to identify the root of the problem, saving many lives.

Speaking of tracking, blockchain can help track every step of the way when it comes to shipping. By digitizing and automating paperwork across supply chains, blockchain would make it easier to manage documents across borders or different organizations. Therefore, blockchain can help at every level—from the shippers, the customs services, and the logistics providers to the banks and insurance companies.

Further, blockchain can be used by suppliers to keep records of the origins of any material they buy and to help different companies and their customers verify the authenticity of various products.

# [Real-world use cases of blockchain in different businesses](#toc.xhtml#s14a)

One of the most well-known use cases of blockchain in business till date is the Walmart case. Walmart tried out a food traceability system based on the Hyperledger Fabric—a blockchain-based system for use within private organizations. In association with IBM, Walmart tested two of these projects—one to track the mangoes sold in the US Walmarts and the other for the pork sold in Chinese Walmarts.

Previously, tracing the mangoes sold in the US Walmarts used to take around a week, but the blockchain-based food traceability system brought that time down to just 2.2 seconds! Similarly, in China, tracing the source of the pork became effortless. Walmart now uses the same Hyperledger Fabric-powered blockchain systems to keep track of over 25 products, including poultry, dairy, packaged food, and fresh produce.

IBM has helped quite a few other businesses with blockchain solutions. *Vetrax*, a Connecticut-based company, is a leader in supply chain management solutions for the oil and gas bulk liquid distribution industry. The *Vertrax* *Blockchain*—a multi-cloud blockchain solution built on the IBM Blockchain platform helps prevent supply chain disruptions due to extreme weather or other such disasters.

Indeed, supply chain management is a sector that benefits greatly from the deployment of blockchain. Due to its shared, decentralized network infrastructure, a supply chain using blockchain facilitates improved communication and collaboration for all parties involved. The greater traceability and transparency minimize waste and duplicate orders and eliminate things like invoice fraud and rogue spend. Uncertainty and risks are also reduced, and the processing time is lowered. Further, blockchain makes it easier to verify where goods come from and where they end up, as the Walmart use case demonstrates.

Golden State Foods is another organization to use blockchain solutions and help quick-serve restaurants track their food items' journey right up to the customer, again in association with IBM.

Some more well-known organizations to deploy blockchain solutions for businesses include Pfizer, AIG, Siemens, Unilever, and more.

# [Blockchain as a service](#toc.xhtml#s15a)

Here, we will quickly mention BaaS, or Blockchain as a Service. Many of the major IT providers have come up with BaaS offerings. Blockchain as a Service is a cloud-based solution that is here to help businesses with the deployment of blockchain technology, so they would not need to start from scratch. You can find BaaS offerings in the form of the Amazon Managed Blockchain, Samsung Nexledger, Oracle Blockchain Applications Cloud, HPE Mission Critical Distributed Ledger Technology, HPE Pointnext, Azure Blockchain Workbench, SAP Cloud Platform Blockchain, and of course, the IBM Blockchain.

# [The importance of architecting blockchain solutions](#toc.xhtml#s16a)

As we have seen so far, blockchain solutions can indeed prove indispensable for businesses if you want to stay ahead of the pack in the increasingly digital world we are finding ourselves in today.

Adopting a blockchain solution requires functional specification, as well as a well-thought-out architectural plan. When one or multiple businesses decide to create or integrate with a blockchain solution, there is already automatically a network of participants formed. A blockchain solution would link them together in a peer-to-peer network that had provide them access to better communication and develop a transparent system.

However, before adopting blockchain for your business, you need to understand the few types of blockchain architectures there are.

# [Types of blockchain architectures](#toc.xhtml#s17a)

Blockchain architectures are varied based on various factors, such as the level of decentralization. A blockchain can be considered more centralized or decentralized, judging by who is in control of the ledger. Blockchain architecture can mainly be of three kinds, which are:

*   **Public blockchain architecture:** A public blockchain architecture uses **Proof of Work** or **PoW** as its consensus algorithm (where a miner has to prove others they have spent a specific amount of computational effort in the creation of a block). It is open-source—so all participants can verify its underlying code, and permissionless. With a public blockchain, anyone can download the code and check the transactions made on the network; the blockchain is transparent, yet users can make anonymous transactions. 
    *   Some examples of a public blockchain would be the Bitcoin, Ethereum, and Litecoin blockchains. A public blockchain is open; therefore, it is decentralized. However, these blockchains are less efficient than the private kind since they take a relatively larger amount of time for new records to be accepted.
*   **Private blockchain architecture:** With a private blockchain architecture, there is only a selected group of nodes that are allowed to access the data stored on the blockchain, as opposed to a public one, where everyone can see the stored data. Proof of Stake or PoS is the usual consensus algorithm used by private blockchains—in a PoS network, and a participant can validate transactions according to how many native coins of the network they hold. Private blockchains are used by institutions that aim for maximum efficiency. A private blockchain is obviously considered centralized since it is managed by a group of participants.
*   **Consortium blockchain architecture:** Though not as common as the private or public blockchain architectures, consortium blockchain architecture aims for a public permissioned blockchain. How this works is that while anyone with an internet connection can connect to the blockchain, a participant can only add data or attach a node to the network with permission from other participants. These blockchains also mainly use the PoS algorithm. Organizations go for consortium blockchains when they are trying to increase trust among consumers or even the broader society.

# [Becoming a certified blockchain architect](#toc.xhtml#s18a)

In today's time, a career in blockchain can open up a horizon of opportunities. And the position of a blockchain architect is one of the best ones you can opt for within the industry, both because of the creative liberty you will have and the quite high remuneration. But before we see the perks of becoming a blockchain architect, let us first see what being a blockchain architect entails.

# [Who is a blockchain architect?](#toc.xhtml#s19a)

If we had to put it in one sentence, we have to say a blockchain architect is the backbone of a particular blockchain solution. As a blockchain architect, you have to be in charge of all the solution signifies.

A blockchain architect has to work with the technology and research and development teams to design and build blockchain solutions that leverage cross-asset frameworks and concepts. You would have to work on innovative technologies and create performance standards for measuring blockchain performance. A blockchain architect's job might also include building client systems and applications and developing storage solutions.

So a blockchain architect is basically charged with leading all blockchain-based projects and also outlining a project roadmap for the entire team. As a blockchain architect, you will not only have to code or build the system, but you will also be required to take into consideration the business perspectives and even communicate with potential clients.

# [Now, why is becoming a blockchain architect a good career choice?](#toc.xhtml#s20a)

We know blockchain is a relatively new technology, one that a sizable part of the general populace still is not even aware of. We have not seen many use cases of blockchain in the real world so far, so it is perfectly natural to wonder why you should choose a career where you will work with a technology that does not seem to have much visible purchase in the world around us just yet.

So, now we present to you some undeniable benefits of entering the world of blockchain as a blockchain architect.

*   **Major demands for blockchain architect:** As more and more businesses look to adopt blockchain solutions, the demand for blockchain architects also gets higher. Plus, there is already only a handful of people skilled enough to shoulder the responsibilities of a blockchain architect. So if you have the necessary skills, you are bound to get hired soon.
*   **High compensation:** Almost every position in blockchain starts out with a fairly high salary since most require tech experts. And since a blockchain architect is the head of a blockchain-based project, you can definitely expect an even higher salary than the other positions on offer in the market. Once you get some experience, you will likely see a pay raise. Plus, your position should also come with more vacation times with incentives.
*   **More flexibility:** As the one all but running the project, you will get a team of your own and the scope and space to let your ideas flourish exactly the way you want. That is more than most career options would get you, do not you think?
*   **Be a part of a technological revolution:** With all the hype surrounding blockchain tech out there, it is only a matter of time before blockchain truly revolutionizes the world as we know it. So, as blockchain reshapes business models and helps them run with more efficiency than ever imagined, you will get to work with this new technology. That is definitely a chance of a lifetime, and what is more, some of the innovations that would bring about the revolution could be yours too.

Now that you know why becoming a blockchain architect would be a wonderful career choice, you might be curious about the skills you will have to acquire to earn that very position. In the next part, we will answer your question.

# [What skills do you need to become a blockchain architect?](#toc.xhtml#s21a)

In this final part of the chapter, we try listing out the needed skillsets toward becoming a Blockchain Architect as it is known today.

*   **Find out in thorough detail about the fundamentals of blockchain:** You will need to acquire technical knowledge to become a blockchain architect, but you start with the basics: everything from the definition of all the terms associated with blockchain to the primary components that make up a blockchain system to the qualities and usabilities of blockchain—nothing is insignificant. If you do not get the basics right, you will have difficulty fully processing the technical nuances.
*   **Read up on the blockchain architecture and how it works:** Well, this one you knew. Get your concepts clear about blockchain architecture and how the technology functions. A good way to do this, after clearing the basics and the common concepts, is to study the whitepapers of various enterprise blockchain platforms so as to figure out where the structures differ. This would help you formulate your own unique ideas in the future.
*   **Understand data structures:** Blockchains come with unique forms of data structure, and they are complex enough for even experts to require a long time to figure them out. This is why you must possess a comprehensive knowledge of data structures, how they make up a blockchain, as well as an applicative sense of data structure so you figure out how it fits with your ideas for a blockchain solution.
*   **Learn multiple programming languages:** This is one of the basic requirements of a blockchain architect; you need to have significant expertise in several programming languages. For this, you can find many online and offline courses. Basic languages like Python, Java, and C++ are obviously mandatory; once done with those, learn Solidity- the programming language for smart contracts. Once you are done, you will need to develop a blockchain app to check your familiarity with the languages.
*   **Learn smart contract development:** Another necessary requirement of a blockchain architect, this skill is one of the highest-demanded features of many businesses. So you need to be aware of how to develop self-executing contracts.
*   **Be efficient in cryptography:** Cryptography secures a blockchain; without it, a blockchain system would fall into pieces. Therefore, learning cryptography is also a must, so you can add maximum security and immutability to your blockchain solution.
*   **Study up on different blockchain platforms:** Understand the distinctions between the public, private, and consortium blockchain architectures, and understand their workings.
*   **Learn blockchain interoperability:** True interoperability is not a feature many blockchain platforms possess at the moment, but it is about to become one of the highest-demanded characteristics of blockchain solutions in the very near future. Therefore, do not forget to study how that works, so you can figure out how to implement it in your design.
*   **Learn to utilize blockchain development tools:** This is rather for your own benefit. These tools would help accelerate your project, and you can test your ideas out with them. You also need to know these tools well to find out which ones fit your project.
*   **Figure out how to interconnect blockchain and business:** Well, this is really one of your prime responsibilities as a blockchain architect. You would have to come up with a business model that can be different from a general one to keep up with the blockchain solution, but you need to be careful it does not affect the revenue. This is a crucial skill upon which the success of the project depends.
*   **Find out how to develop blockchain product specifications:** As a blockchain architect, you will have to take into consideration both your clients' demands and your company's consumer demands. Therefore you need to be fluent in developing blockchain product specifications.
*   **Acquire expertise in front-end and back-end Web development:** This one is also quite important for this career; while you might not have to do the coding yourself while working on your project, without knowing the how's and why's of Web development, you cannot get your designs right.
*   **Make sure you also have the necessary leadership skills:** As a blockchain architect, you will be leading a team of professionals. Therefore, you must possess leadership skills for that.
*   **Acquire quick thinking and problem-solving skills:** As you take up a whole new project and build a blockchain solution from scratch, you will definitely be faced with problems and challenges. In that case, you will have to bear responsibility and solve them swiftly.
*   **Get a relevant degree or diploma:** It would be great if you could enter a blockchain architect training program—you can find many online. The second best thing is a degree in computer science engineering. It will teach you all about software development and programming and prove your qualifications to your potential employers.

As blockchain changes our world bit by bit, new, exciting career opportunities are also opening up with every passing day. You can check out up-and-coming open-source blockchain projects to develop an understanding of how the technicalities work and maybe even contribute to them.

If you do decide to pursue a career in this field, do stay with me as we tell you more about architecting blockchain solutions.

# [Conclusion](#toc.xhtml#s22a)

It is true that blockchain was introduced first as the technology behind cryptocurrencies, and the crypto space is where its use cases remained constrained for a while. However, blockchains can prove to be useful outside of the crypto space as well, as it comes suited to address many pain points of quite a few mainstream industries, and in this digital era, blockchain can surely help businesses get ahead of the pack. Further, blockchain's adoption in businesses from various industries opens up a wide, new range of career opportunities, such as that of a blockchain architect. With the right skills, anyone can partake in the revolution that blockchain tech is about to bring across industries.

Now that we have gone over that, in the upcoming chapter, we will look at the differences between blockchain and traditional databases.

# [Questions](#toc.xhtml#s23a)

1.  **How did the concept of blockchain come about?**
    
    In 2008, when Bitcoin was started, which was based on a paper written in 1982 by David Chaum
    
2.  **What are the different types of blockchain architecture?**
    
    Public, private, and consortium
    
3.  **What are the various components of a blockchain?**
    
    Block, hash, consensus algorithm, miners, and so on.
    
4.  **What is a hash?**
    
    Hash is a unique identification number for a block. It is irreversible in nature, meaning once the hash is generated for a block, we cannot find the content of the blocks using the hash.
    
5.  **What properties of blockchain make it suitable for businesses?**
    
    Security, distributed ledger, immutability, consensus algorithm
    
6.  **How can blockchain be used in businesses?**
    
    Supply chain, food distribution, electoral process, and so on.
    
7.  **What does a blockchain architect do?**
    
    Work with the latest technology, research, and develop blockchain-based infrastructure
    
8.  **Why is becoming a blockchain architect a profitable career option?**
    
    Latest in-demand technology, high compensation, and many future use-cases
    
9.  **What are the most important skills required to become a blockchain architect?**
    
    Knowledge of multiple programming languages, cryptography, back-end, front end Web development, data structures, and algorithms.
    

# [Key terms](#toc.xhtml#s24a)

*   **Blockchain:** A blockchain is a series of virtual blocks containing data that are linked together by a digital chain. The data stored on a blockchain is verified by participants, updated in real-time, and encrypted. a blockchain is decentralized.
*   **Block:** A block on a blockchain is a virtual storage containing information about the transactions happening on the chain.
*   **Hash:** A block's hash is a mathematical function that transforms the input of any length into a fixed-length encrypted output.
*   **Node:** A node is a device connected to a blockchain network and operated by a participant on the network. Nodes keep copies of the blockchain ledger.
*   **Consensus Algorithm:** This is a set of rules that all nodes on a blockchain have to follow for proper on-chain governance.

# [CHAPTER 2](#toc.xhtml#c02)

# [Architecting Blockchain Solutions From Scratch](#toc.xhtml#c02)

# [Introduction](#toc.xhtml#s25a)

Now that we have covered the genesis of blockchains, in brief, it becomes extremely crucial that we understand why such technology was made necessary in the first place. Why go to the lengths to create something so unique and complex to perform actions, which can be accomplished, to the eyes of a novice using, say, a traditional database solution? To truly understand the necessity, it is crucial to understand what databases are and how traditional databases differ from blockchain solutions.

The concepts we will cover in this chapter might seem a little basic to you, but you are urged to read and focus on the aspects highlighted, as that is the foundation of your journey to become a blockchain architect.

# [Structure](#toc.xhtml#s26a)

In this chapter, we will cover the following topics:

*   Database systems
*   Different types of database models
*   Blockchains versus databases
*   Blockchains and scalability
*   Purposes of using blockchains
*   Purposes of traditional databases
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s27a)

The importance of understanding the differences between blockchains and databases can simply not be emphasized enough. After going through this chapter, you will be able to understand the various nuances between blockchains and databases and when we should opt for blockchains as opposed to traditional database models.

# [Database systems](#toc.xhtml#s28a)

There is a quite common quote that gathered some traction sometime around 2017—"The world's most valuable resource is no longer oil, but data". Data has become the single most important cog in the success of any entity—commercial or otherwise. However, what good is data if we cannot store them reliably, access them when we want to, modify them as per our requirements, and retrieve them for later use?

For much of the 20^(th) century, computers were seen as rather sophisticated calculators used to run complex algorithms and calculations. The information that came out of these giant calculators was stored in the form of punch cards, a rather ingenious solution credited to one Herman Hollerith. However, as cutting-edge as it may have been at the time, it was quite a tedious task to manage even a few kilobytes of data, as you can imagine.

That changed in the 1960s, however, when a Database Management System named "*Integrated Database System*" was created by Charles W Bachman with the sole intention to collect, organize, and store information. In due course of time, computers became much more than giant calculators, and as a direct result, database management has also become much more than storing and accessing data at will. In the 1970s, Edgar Codd, a revolutionary in the field, came up with the following list of purposes a Database Management System should provide:

*   Data storage, retrieval, and updation
*   User-accessible catalog or data dictionary
*   Support for transactions and concurrency
*   Facilities for recovering damaged data
*   Support for authorization/compartmentalization of data
*   Support for remote access
*   Enforcing constraints to ensure data abides by certain rules (for instance, if the database captures the age of a person, text inputs should be disallowed)

In the wake of the 21^(st) century, databases have become far more sophisticated, with the inclusion of several additional features and utilities that allows ease of access, including import/export of data, monitoring, and other security measures, encryptions, defragmentation, configuration parameters, **Application Programming Interfaces** (**APIs**) to name a few of the developments. Various applications can now interact with database systems, using either SQL or APIs, allowing for some very interesting use cases. For instance, e-commerce stores, on your authorization, access your bank's database and instruct it to transfer the specified sum to the specified account.

Popular Database Management Systems include MySQL, Microsoft SQL Server, Oracle Database, PostgreSQL, and Microsoft Access, among others.

# [Different types of database models](#toc.xhtml#s29a)

Although there are multiple iterations and types of database management systems currently in use, pundits categorize DBMS into the following eight categories. Keep in mind that these eight categories are not mutually exclusive, and one database can check the boxes to fit into multiple categories.

*   **Centralized database**: This is the most commonly used type of Database Management system. The centralized databases allow the database admin to control who has access to the information on the database. The centralized databases allow for user segregation and privacy measures and work on a client-server architecture. We will proceed to learn more about Centralized and Decentralized databases in detail in a bit. 
    *   Examples of Centralized databases may include databases used in schools, colleges, libraries, hospitals, and companies (for internal use).
*   **Distributed database**: These databases are not centralized, where data is distributed (hence the name) among multiple database systems of an organization. The distributed databases ensure that even if one server is lost due to one reason or the other, the entire data set is not affected and offers agile scalability. 
    
    One point of importance to note here is that while blockchain uses distributed ledger network architecture, they are fundamentally different from distributional databases. These databases still do store the data using the tabular format and do not offer nearly the same levels of security or decentralization as the peer-to-peer network architecture of blockchain.
    
*   **Relational database**: Remember Edgar Codd? The person we talked about a few paragraphs ago, who came up with a list of functionalities, a database should provide. He came up with relational databases in 1970, which use SQL for storing, manipulating, and maintaining data (*[figure 2.1](#c02.xhtml#fig2_1)*) in the now popular tabular format. The rows (called tuples) and the columns (attributes) come together and form a table—called the relation. Many popular databases, including MySQL, Oracle, and so on, belong in this category. Please refer to the following figure: 
    
    ![](images/Figure-2.1.jpg)
    
    **Figure 2.1:** Relational databases
    
*   These databases have to adhere to a certain set of rules, with the mnemonic "**ACID**" as follows:  
    *   **Atomicity:** A data operation should be completed with success or with failure. There is no in-between.
    *   **Consistency:** The values of data, before and after operations, should be preserved, and the results should be generated according to a fixed set of algorithms and logic. In other words, the results should be able to be broadly trusted for accuracy owing to the database rules.
    *   **Isolation:** Concurrent users may be accessing different data from the same database. The effects of the transaction should be isolated and visible to those who have access.
    *   **Durability:** Once the operation is complete and data is entered/modified, the changes should remain permanent.
*   **NoSQL database**: With the growth in technology in recent years, data came from new sources. From social media to AI, unstructured data became a lot more prevalent, which was tough for SQL databases to process. In order to enable this additional supply of data, we saw the evolution of NoSQL (called not only SQL database). NoSQL databases, unlike SQL databases, do not operate in tabular form. Instead, they store key-value pairs, document-based, or even operate as graph databases. Given this flexibility and different architecture, the NoSQL databases (*[figure 2.2](#c02.xhtml#fig2_2)*) can support a higher level of scalability (since they do not rely on singular tabular storage), increased performance speed, a higher degree of availability, and the capability to manage big data when compared to traditional SQL databases. As a result, they are ideal for mobile apps or any sort of unstructured data. 
    
    Popular NoSQL databases include MongoDB, CouchDB, Hbase, and Oracle NoSQL Database. Please refer to the following figure:
    
    ![](images/Figure-2.2.jpg)
    
    **Figure 2.2:** Benefits of NoSQL database
    
*   **Cloud database**: Another development in the field came in the form of cloud computing. Cloud computing offers users the ability to host highly capable databases at a fraction of the infrastructure and maintenance requirements along with other cloud computing services. Examples include Oracle, Azure, and so on. 
    
    **Trivia: Do you know the company that started out as an online bookstore is now one of the leading cloud computing/database service providers? Brownie points for you if you guessed Amazon. Amazon Web Services holds a staggering 32% market share, followed by Microsoft's Azure at 19% in the cloud computing sector.**
    
*   **Object-oriented database**: Similar to **Object-Oriented Programming Languages** (**OOPs**) such as Java, Perl, and C++, Objected-Oriented Databases (OODs) approach storing data in an object-based model (*[figure 2.3](#c02.xhtml#fig2_3)*). OODs allow you to work with complex data objects, very similar to those used in OOPs. All data objects are stored with the relevant properties, even after the program is terminated. Industries that typically work using OOPs while looking to maintain high levels of efficiency when working with complex data structures opt for OODs. MongoDB Realm is the most popular OOD in the sector as of now. Please refer to the following figure: 
    
    ![](images/Figure-2.3.jpg)
    
    **Figure 2.3:** OOD's approach to storing data
    
*   **Hierarchical database**: These databases represent data in a fashion very similar to a single-gender family tree (*[figure 2.4](#c02.xhtml#fig2_4)*). The relationship between records is what is called a "*one-to-many*" relationship. One parent can have many child nodes, but each child node can have only one parent node. Examples of hierarchical databases include the IBM **Information Management System** (**IMS**) or RDM Mobile. Please refer to the following figure: 
    
    ![](images/Figure-2.4.jpg)
    
    **Figure 2.4:** Hierarchical database model
    
*   **Network database**: These databases allow each record to have multiple parent/child nodes, allowing a flexible relationship model (unlike hierarchical databases—*[figure 2.5](#c02.xhtml#fig2_5)*). The network databases were considered an enhancement to the hierarchical databases—both of which are mostly obsolete due to the increasing popularity of SQL and NoSQL databases. Examples include IDS and IDMS.
*   **Graph databases**: These databases, like NoSQL database, do away with a tabular approach to storing data. Instead, they store the relationships between the data, much like a flow chart on a whiteboard. This approach, featuring nodes, edges, and data properties, allows for capabilities that standard relational databases cannot deliver. For example, movie streaming services use graph databases to track the movies users have watched by storing their relationship to different titles. 
    
    ![](images/Figure-2.5.jpg)
    
    **Figure 2.5:** The network database model
    

# [Blockchains versus databases](#toc.xhtml#s30a)

We talked extensively about what a blockchain is in the first chapter, especially about how data is stored in the form of blocks in a chain. We also discussed how the data is immutable, that once a transaction is entered into the blockchain, it is impossible to undo it or modify it under any circumstances, and how blockchains can be decentralized. However, in the case of traditional databases, the data is stored in the form of tables controlled by central authorities, and these central authorities can read, write and modify data as the requirements may be.

Typically, databases use a client-server architecture, which has proven to be highly effective in diverse environments, regardless of scale. The client-side acts as the receivers, while the servers are the centralized processors of data. The database administrator controls every single aspect of the database and is highly centralized. The access is permissioned—meaning only those authorized by the database administrator will be privy to and capable of modifying the data.

We will be discussing the nuances of blockchain architecture in the upcoming chapter, but for now, understand that blockchain uses what is called distributed ledger network architecture. Blockchain uses a peer-to-peer network, where all the computers in a network are connected to each other and secured by cryptographic protocols. Since there is no centralized server, all nodes (computers) can take part in the consensus algorithm. This consensus helps maintain the integrity of the data stored in the blockchain database. Blockchain can be permissioned (as in the case of private blockchains and consortium/hybrid blockchains—more on this later) or permissionless, as the case may be. However, the main bottleneck of blockchain technology comes in the form of scalability. Bitcoin, one of the famous use cases of blockchain technology, is capable of only handle seven transactions per second, as opposed to Visa (the American Financial Company), which transacts over 1,700 transactions per second. Please refer to the following figure:

![](images/Figure-2.6.jpg)

**Figure 2.6:** Summary

In summary (*[figure 2.6](#c02.xhtml#fig2_6)*), the key differences between blockchains and traditional databases are as follows:

*   **Centralization**: Blockchains use distributed ledger network architecture and can be completely decentralized, whereas traditional databases are centralized
*   **Architecture**: Traditional databases use a client-server architecture, whereas blockchains use distributed ledger, peer-to-peer network architecture
*   **Data Handling:** Blockchains can use only read and write operations, whereas traditional databases can support what is called Create, Read, Update and Delete (CRUD).
*   **Data Integrity:** Data is immutable and cannot be modified at all in the case of blockchain, whereas it is possible for errors and malicious actors can tamper with data in a traditional database.
*   **Data Transparency:** Data is completely transparent in the case of public blockchains, whereas access to data is determined by the database administrator in the case of traditional databases.
*   **Scalability and Cost**: Blockchain networks are costlier to implement, maintain, and reach a bottleneck when it comes to scalability due to complex consensus algorithms. Traditional databases are relatively cheaper and highly scalable.

# [Blockchains and scalability](#toc.xhtml#s31a)

Although blockchains are undeniably more secure and reliable, they are also notoriously slow and, as a result, are not highly scalable as of now. It is important to understand that blockchain is relatively in its infancy when compared to the development of traditional databases and still needs a lot of time to evolve to compete with traditional databases in the case of scalability. In fact, even at present, there are plenty of amazing perspective solutions that are being tested out to solve this problem. Right now, it is essential to understand why scalability is an issue in blockchains which is explained as follows:

*   **Cryptographic Verification:** In order to ensure security, blockchain transactions are cryptographically signed using complex cryptographic algorithms. The verification of this cryptographic signature can act as a bottleneck.
*   **Consensus Mechanisms:** In a decentralized, democratized network, consensus between the users is essential to validate transactions on the blockchain. There are different types of consensus methods used (some faster than others), but it adds additional time to a transaction when compared to traditional centralized databases.
*   **Redundancy of Data:** Since blockchain functions on a distributed ledger, peer-to-peer network, each node verifies and stores all the data in the blockchain. Although this improves data reliability a lot, this comes at the cost of a huge redundancy.

These three factors are the main reasons why blockchains are slow. Even if the blockchain application is highly efficient, these factors invariably come into play, making blockchains a slightly less desirable alternative when it comes to pure performance.

# [Purposes of using blockchains](#toc.xhtml#s32a)

![](images/Figure-2.7.jpg)

**Figure 2.7:** As blockchains use distributed ledger technology, they eliminate a single point of failure.

When it comes to trust and transparency, blockchains are the go-to solutions. This is the reason why cryptocurrencies, which thrive on trust, transparency, and decentralization, run effectively on the blockchain. The transfer or store of value and monetary transactions are the best use cases of blockchains for a reason.

Blockchains are extremely useful to eliminate a single point of failure (*[figure 2.7](#c02.xhtml#fig2_7)*). When we were first introduced to the concept of blockchains, we were introduced to an oversimplified example which makes this concept easier to grasp.

Say you have just landed in India from France with your aging mother. Being an ardent techie, you carry around the latest smartphone, and its clock is automatically updated to the Indian Standard time. You set out for your day, leaving your mother behind at the hotel to rest, and ask her to meet you at the lobby by 5 p.m. However, the tired, jet-lagged lady forgot to update her wristwatch to the IST and slept through. While this was definitely not an intentional malicious act, it is proof that errors are unavoidable, even if you completely trust the other person involved. To complete this analogy, blockchain acts similar to your smartphone and automatically corrects the error in the network—a feat achieved through the consensus of the majority of the participants in a network.

When data errors can be automatically identified and corrected based on smart contracts and consensus, all the parties involved need not place their trust in a single trusted party and can instead blindly trust the data. Even if one of the parties intentionally wanted to maliciously change the data, it would be downright impossible.

Usually, when two businesses work together, they usually do not share a database with a single set of records, as the records will usually be maintained by a fiduciary—say, a database administrator. This database administrator becomes a single point of failure, as any errors on his side will compromise the integrity and reliability of the data. When blockchain is incorporated, there will not be a necessity for this single point of failure. If someone does maliciously try to add an additional entry or provide a wrong chain of events, the automatic correction of data is ensured by the indication of which party attempted to modify the records.

In essence, B2B transactions like supply chain management, inventory management, and so on, where transparency is of utmost importance, without having to add additional complexities, blockchain technology can be extremely useful.

Permissioned blockchains—which are accessible and modifiable only by administrators or with approvals—are not nearly as talked about as public blockchains but can make processes such as voting incredibly easy and bring transparency and trust to the entire process.

Use cases like escrows and automation within a platform can be accomplished using smart contracts.

# [Purposes of traditional database](#toc.xhtml#s33a)

If centralization of data leads to data manipulations and single points of failure, why even go for traditional databases? It is established that data from blockchains are more reliable because of their immutability and consensus mechanisms—then why even go for centralized databases?

Traditional databases offer functionalities far and beyond what blockchains can offer. While yes, blockchains do offer several undeniable benefits, they do not cover all the use cases of what traditional databases offer. For instance, traditional databases are extremely user-friendly and cater to a wide variety of necessities. Scalability is definitely one of the major advantages of centralized databases, and as is, the blockchain is not ideal for storing a significant amount of data since it is immutable. Changes in data are added, not modified, leading to the need for larger and larger storage space. Regular modification of data cannot be done using blockchains. Some databases require user control separation and data confidentiality, which, again, is not supported by blockchains.

One of the less talked about benefits of traditional databases is the amount of energy it consumes. Blockchains are power-hungry, and the Proof of Work consensus algorithm is particularly reliant on large amounts of energy to function.

In some other cases, blockchain might simply be overkill. In a basic database, where user verification is not necessary or when the cost is a factor to be considered, traditional databases do come head and shoulders above blockchains.

# [Conclusion](#toc.xhtml#s34a)

While blockchains are technically databases, they are very different from traditional databases in many regards, from network architecture to use cases. While blockchain focuses more on decentralization, trust and data integrity, traditional database aces in accuracy, speed, utility, confidentiality, and user segregation. If your enterprise requires a database solution that requires trust, transparency, decentralization, or verification, then choose blockchains. In contrast, databases are ideal for highly scalable, cost-effective solutions, which are also suitable for apps and services. In the upcoming chapter, we will go through the nuances of the different types of blockchain architecture.

# [Questions](#toc.xhtml#s35a)

After reading this chapter, ensure that you have a thorough grasp of these concepts.

1.  **Why were Databases necessary?**
    
    To permanently store the data for later access/modification, and so on.
    
2.  **What are the important characteristics that define a proper database system?**
    
    It should follow ACID properties.
    
3.  **What are the different types of database systems?**
    
    Close to eight models are described in this chapter, to name a few-> Relational, NoSQL, distributed, network, cloud, and so on.
    
4.  **What are the similarities and differences between traditional database systems and blockchains?**
    
    **Similarities:** Both store data
    
    **Differences:** Blockchain is a decentralized database that is highly secure on the one hand but power-hungry, low performance, and hard to scale on the other hand. Traditional databases are centralized, easy to set up and maintain, high performance, and lower cost.
    
5.  **Why do blockchains face an issue with scalability?**
    
    A consensus algorithm, proof of work.
    
6.  **Which use cases best suit blockchains?**
    
    Electoral voting, supply chain management, banking. Where trust and data integrity is a requirement.
    
7.  **Which use cases best suit traditional database systems?**
    
    Apps and services which do not require trust, transparency, decentralization, and verification.
    

# [Key terms](#toc.xhtml#s36a)

*   **Database System:** A collection of digital tools/software that enable data storage, retrieval, and updation, User accessibility, remote access, and enforcement of constraints on the data they deal with.
*   **Centralized Database:** A database that enables its administrator to control information access, set usage policies, and enforce other rules.
*   **Distributed Database**: A database where data is stored among multiple database systems, ensuring protection against single points of failure and superior scalability.
*   **Relational Database:** Databases that use SQL for storing, manipulating, and maintaining data in a tabular format. The rows (called tuples) and the columns (attributes) come together and form a table - called the relation.
*   **NoSQL Database:** Short term for Not Only SQL Database, a NoSQL database delivers an improved level of scalability, performance speed, availability, and capability to manage big data compared to traditional SQL databases.
*   **Cloud Database:** A database stored in usually far-located infrastructure, typically managed by a service provider offering a similar service to other organizations.
*   **Consensus Mechanism:** The algorithm or manner by which users on a blockchain come to an agreement for validating transactions. There are different types of consensus methods used (some faster than others).
*   **Data Integrity:** The property of a database or blockchain to maintain the immutability and resistance to change of the data that it stores.

# [CHAPTER 3](#toc.xhtml#c03)

# [Components of Blockchain Architecture and Its Types](#toc.xhtml#c03)

# [Introduction](#toc.xhtml#s37a)

In the previous chapter, we promised to delve more into the nuances of blockchain architecture. We discussed how Blockchain uses something known as a distributed ledger network architecture and how it effectively runs on a peer-to-peer network model. For some of my readers, who have worked with networking/databases before, the concepts that we have chosen to cover in this topic might be a bit basic. However, we will still recommend that you pay close attention to these introductory chapters, as we have compiled only those topics which are absolutely crucial toward ensuring that your fundamentals are strong on your journey to becoming a Blockchain Architect.

# [Structure](#toc.xhtml#s38a)

In this chapter, we will cover the following topics:

*   Introduction to network architecture  
    *   Client/server architecture
    *   Peer-to-peer network architecture
*   Centralized versus decentralized versus distributed databases
*   Database architecture versus Blockchain architecture
*   Data structures used in Blockchains
*   Advantages of Blockchain data structure
*   Characteristics of Blockchain architecture
*   Components of Blockchain architecture
*   Types of Blockchain networks  
    *   Public Blockchain architecture  
        *   Proof of work consensus algorithm
    *   Private Blockchain architecture  
        *   Proof of stake consensus algorithm
        *   Byzantine fault tolerance
    *   Consortium Blockchain architecture
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s39a)

After going through this chapter, apart from understanding the different types of network architectures, you will also get a clear picture of the different components and types of blockchain architectures, their use cases, and, most importantly, a crucial component called consensus algorithms. We will also learn the best use cases for the different types of blockchain architecture when you deploy one. Without further ado, let us start discussing the fundamentals.

# [Introduction to network architecture](#toc.xhtml#s40a)

Blockchain, as we have talked about previously, uses a peer-to-peer network architecture to achieve high levels of decentralization, reliability, and security. But before going into the nuances of peer-to-peer network architecture, it is important that we understand what a network architecture is and the two types of network architecture, to truly grasp how blockchain architecture works.

Network architecture can be defined as the design of a computer network, which provides a rigid framework for all the components in the network. These components include physical components like hardware and related infrastructure (including the geographic span and the decision to make a network wired/wireless) and logical components such as protocols, software, and the medium of data transmission within a network. Cutting the jargon down, network architecture refers to how computers are arranged and organized within a network and how the various tasks are allocated.

Each type of network architecture offers a different method of transferring data efficiently without compromising on reliability. This decision affects not only the network topology but also defines how different nodes in the network access the media. In the early days of data transmission and communication systems, communications were strictly between the DTE^() and the host computer, and transmission control protocols were more than sufficient to facilitate this process. However, as tech developed, computer systems linked with other systems to form a network necessitated the requirement of multiple protocols for various different purposes, giving birth to the requirement for the different types of network architecture that we see today.

Although there are multiple different types of network architecture, each with a different strategy to conduct information over the network, we need to focus on the two broad categorizations for the purposes of this discussion.

These two categories are as follows:

*   Client/Server Architecture (Also called tiered network architecture)
*   Peer-to-Peer Network Architecture (Also called P2P).

# [Client/server architecture](#toc.xhtml#s41a)

This type of network architecture contains multiple remote processors (called clients) that request and receive media/information/services from a centralized host computer (called the server). The client computers act as an interface to the end-users, and they allow users to request services and data from the main server. Traditional databases usually use a client-server infrastructure, where a central server is used for storing, modifying, manipulating, and retrieving data, whereas the computers used merely acts as an in-between to ensure that data is available as and when needed. Here is an illustration of what it may look like:

![](images/Figure-3.1.jpg)

**Figure 3.1:** Client/server architecture

This model is extremely effective when the client computers are needed to perform multiple tasks, more than acting as a mere terminal for a central mainframe. For instance, your workstation might be connected to a central database and can still function as a regular computer (for instance, sending and receiving e-mails, running IDEs, and so on). Both client and server computers are considered independent devices, and this model is very different from the DTE-Host computer model that we touched upon earlier.

# [Advantages of client-server architecture](#toc.xhtml#s42a)

A client-server model offers the following benefits:

*   Resources and data security (including User Access Controls) can be directly controlled through the server. No requirement for consensus of all the nodes involved.
*   Scalability is not a concern, as Client/Server networks can handle high numbers of remote processors accessing data from a single, more powerful server. Or they even scale horizontally by adding several servers to the network.
*   Easy access to the data, irrespective of the platform.

# [Disadvantages of client-server architecture](#toc.xhtml#s43a)

Simultaneously, there are some drawbacks of the client-server model to keep in mind:

*   Cost-ineffective. Requires a lot of capital investment in servers, **Networking Operating Systems** (**NOS**), hubs, routers, and switches, among others.
*   Single point of failure in the form of a centralized server—multiple backups are always necessary, and physical threat to data is ever-looming.
*   Maintenance is necessary round the clock (further increasing cost) and brings upon the necessity to employ a server technician full-time. Potential slip-ups could lead to hours of downtime, which could disrupt the entire business flow.
*   The requirement for a central intermediary could pose direct threats to data integrity.

# [Peer-to-peer network architecture](#toc.xhtml#s44a)

Unlike a client-server network architecture, a peer-to-peer network is created without any hierarchies. All the nodes in the network are created equal (*[figure 3.2](#c03.xhtml#fig3_2)*) (as peers, hence, the term peer-to-peer) without having to go through a separate server. A peer-to-peer network can be as simple as an ad-hoc Bluetooth connection between your smartphone and your PC, or much more grandiose, as we see in the form of Blockchain. Please refer to the following figure:

![](images/Figure-3.2.jpg)

**Figure 3.2:** Peer-to-peer network

As mentioned earlier, there are no hierarchies, as all nodes are created equal. This means effectively, all the computers in a network are both servers and clients at the same time, eliminating the necessity for a special networking operating system on a centralized server. Of course, data access control can still be achieved, but this is admittedly not the best use case for P2P network architecture.

# [Advantages of a peer-to-peer network](#toc.xhtml#s45a)

*   Not as costly as a client-server model, as there is no requirement for dedicated servers, NOS, routers, hubs, and so on.
*   Robust—even if one system fails, the rest of the network remains functional.
*   Installation and setup are traditionally easy, as most Operating Systems contain built-in support.
*   Suitable for networks demanding high levels of data integrity.

# [Disadvantages of a peer-to-peer network](#toc.xhtml#s46a)

*   Scalability is a prominent issue, as peer-to-peer networks were traditionally designed for a small group of computers. Yes, evolving technology has made it possible to increase the number to potentially thousands of computers, but it still remains an issue to date.
*   In terms of pure performance, the client-server network model is undoubtedly superior.

# [Centralized versus decentralized versus distributed databases](#toc.xhtml#s47a)

Primarily, depending on the network architecture, the databases can differ into three broad categories, namely, centralized, decentralized, and distributed network architecture (*[figure 3.3](#c03.xhtml#fig3_3)*).

![](images/Figure-3.3.jpg)

**Figure 3.3:** Centralized, decentralized, and distributed network topologies

A client/server network architecture usually uses the centralized model, where all clients are connected to a single centralized server. A decentralized network, on the other hand, is spread across multiple locations, where the data is stored in various different locations. The best example of a decentralized database is the internet, wherein users can send/receive data from multiple different servers from all across the world. Decentralized data networks are neither peer-to-peer (as there are multiple centralized servers and a real hierarchy of the systems within a network) nor are they client-server (as there are multiple centralized servers), but are rather considered a P2P network of multiple client-server networks.

Distributed databases, on the other hand, are true P2P networks, where data is available to all the users within the network, regardless of the physical location of each network. Most traditional use cases (such as hospital databases or logistics databases) would not require a distributed model, as data segregation is a crucial factor.

# [Database architecture versus Blockchain architecture](#toc.xhtml#s48a)

Although we had gone through this topic briefly in the previous chapter, we talked briefly about how different architecture is between traditional databases and blockchains. We found it prudent to introduce the nuances here after we have explained the fundamentals of network architecture.

As we have covered, traditional databases use the client/server network architecture, where the centralized server keeps track of all the information in a single place. This makes the process of manipulating, storing, and retrieving (and even deleting) information easy, as the changes are to be made in a single centralized server (controlled by administrators, and permissions, of course). However, as Blockchain uses a distributed ledger architecture, each participant within a network functions to maintain, approve and update new entries (recall that we had discussed how manipulation and deletion of data are not possible in the Blockchain). Please refer to the following figure:

![](images/Figure-3.4.jpg)

**Figure 3.4:** Database architecture versus Blockchain architecture

The key to truly understanding the difference between the architecture of traditional databases and architecture is to realize that in Blockchain, every member is responsible to ensure all the records are in order, ensuring data integrity through consensus. This ensures that parties, who may not necessarily trust each other, will be able to rely on the integrity of the data recorded in the Blockchain, creating a trustless environment (recall the use case of blockchains in B2B transactions, where businesses, potentially rivals, may need to work together, that we had discussed in the previous chapter).

The structure of a Blockchain is represented by a chain of blocks, with transactions recorded in a particle order, whereas traditional databases store data in the form of tables and relations.

# [Data structures used in Blockchains](#toc.xhtml#s49a)

There are two major data structures that are employed in Blockchains as follows:

*   **Pointers**: Pointers are variables in a block (*[figure 3.5](#c03.xhtml#fig3_5)*) that point to information about the location of another variable (in the case of blockchains, typically the next block). Please refer to the following figure: 
    
    ![](images/Figure-3.5.jpg)
    
    **Figure 3.5:** Pointers
    
*   **Linked lists**: Linked lists are a sequence of blocks, which ensures that each block contains unique data and is linked to the block, making use of pointers.

Combining these two data structures, we are able to arrive at how a blockchain's data structure looks on a rudimentary level (*[figure 3.6](#c03.xhtml#fig3_6)*).

![](images/Figure-3.6.jpg)

**Figure 3.6:** Data structure of a blockchain

# [Advantages of Blockchain data structure](#toc.xhtml#s50a)

Blockchain data structure offers the following benefits:

*   **Cost savings**: Central databases such as those of banks and governments inherently require significant capital to keep the data flow secure away from malicious actors, such as cybercriminals and corrupt officials. This distributed, immutable structure eliminates all such costs, as the structure is inherently secure
*   **History of data and provenance**: In a Blockchain structure, at any given time, one can check the history of any current transactions. Centralized databases, on the other hand, are merely a snapshot of information at a specific point in time.
*   **Data validity and security**: Blockchains are inherently immutable, and achieves higher levels of data validity, security and integrity, albeit at the cost of some performance speed.

# [Characteristics of Blockchain architecture](#toc.xhtml#s51a)

Blockchain architecture relies on several concepts to operate practically. They are as follows:

*   **Cryptography**: In a blockchain, all transactions are recorded securely, making use of complex cryptographic computations, which are validated by all the stakeholders.
*   **Decentralized**: Blockchain uses a distributed ledger network architecture, ensuring all users have access to all data.
*   **Provenance**: A complete history of any particular transaction can be tracked and monitored at any point in time.
*   **Immutability**: Once data is recorded in a blockchain, it cannot be deleted or modified.
*   **Pseudonymity**: Every user in a blockchain has an address generated by the system and does not necessarily have identities. This characteristic may not necessarily be true in the case of private blockchains.
*   **Transparency**: Since the data is decentralized, and every member has access to the system and the data, complete transparency can be maintained.

# [Components of a Blockchain architecture](#toc.xhtml#s52a)

Each Blockchain should consist of the following main components.

*   **Nodes**: Computers in the blockchain network, wherein each node has an independent copy of the entire blockchain ledger (*[figure 3.7](#c03.xhtml#fig3_7)*). 
    
    ![](images/Figure-3.7.jpg)
    
    **Figure 3.7:** Nodes in a Blockchain
    
*   **Transactions**: Data record verified by all the participants in a Blockchain network, functioning as an immutable confirmation of authenticity (*[figure 3.8](#c03.xhtml#fig3_8)*). 
    
    ![](images/Figure-3.8.jpg)
    
    **Figure 3.8:** Transactions on a public Blockchain
    
*   **Block**: A data compartment that contains a native hash (identifying the present block), hash code from the previous block from the Blockchain, and a set of all time stamped transactions. Each block is sealed, and cannot be tampered with.
*   **Chain**: A sequential list of blocks.
*   **Validators/Miners**: Particular nodes that run the blockchain software to validate the blocks before adding them to the Blockchain.
*   **Consensus**: Rules and agreements (protocols) for performing Blockchain operations (*[figure 3.9](#c03.xhtml#fig3_9)*). 
    
    ![](images/Figure-3.9.jpg)
    
    **Figure 3.9:** Consensus on a Blockchain
    

# [Types of Blockchain structure](#toc.xhtml#s53a)

Fundamentally, there are three different types (*[figure 3.10](#c03.xhtml#fig3_10)*) of blockchain structures, namely,

*   Public Blockchains
*   Private Blockchains
*   Consortium Blockchains

Please refer to the following figure:

![](images/Figure-3.10.jpg)

**Figure 3.10:** The three types of Blockchain architecture

# [Public Blockchain architecture](#toc.xhtml#s54a)

A public blockchain is an open-sourced, permissionless blockchain that operates on what is called a **Proof of Work** (**PoW**) consensus algorithm. Everyone has access to the source code and can check the transactions on the network at any point in time. Consensus is arrived at by all miners and offers the highest levels of immutability (but is also the least efficient) across the different types of Blockchain architectures. Refer to *[figure 3.11](#c03.xhtml#fig3_11):*

![](images/Figure-3.11.jpg)

**Figure 3.11:** Public versus private Blockchains

Examples of public Blockchains include Bitcoin, Ethereum, and Litecoin.

# [Proof of Work (PoW) Consensus Algorithm](#toc.xhtml#s55a)

The PoW consensus algorithm requires miners to solve a complex computational/mathematical puzzle to add new blocks to the network. Miners are required to guess the particular 256-bit hash propagated by the SHA256 hashing algorithm. This process may take millions of guesses to verify the hash, requiring a lot of work (hence, the name Proof of Work).

# [Private Blockchain architecture](#toc.xhtml#s56a)

A private blockchain allows only a certain group of participants to access data with the aim of increasing efficiency and scalability. The reliability is ensured through consensus algorithms like **Proof of Stake** (**PoS**) and **Byzantine Fault Tolerance** (**BFT**), and anonymity is not a major factor in this type. This is considered more centralized than other forms of blockchains, as a certain group of participants controls the flow of data.

While in *[figure 3.10](#c03.xhtml#fig3_10)*, it has been said that the data on a private blockchain is not as immutable as a public blockchain, and thus, could be tampered with, it's to be noted that if the set of private nodes on a private blockchain are all running a consensus algorithm like the ones mentioned previously, it would be fairly impossible to make any changes to data without alerting everyone.

# [Proof of Stake Consensus Algorithm](#toc.xhtml#s57a)

In the case of PoS (*[figure 3.12](#c03.xhtml#fig3_12)*), the Blockchain considers all the nodes in the systems as validators (unlike PoW, where only specific nodes are considered validators). The protocol randomly selects these nodes to validate the blocks, where the probability of selection depends on the amount of stake each node has. Please refer to the following figure:

![](images/Figure-3.12.jpg)

**Figure 3.12:** How Proof of Stake works

# [Byzantine fault tolerance](#toc.xhtml#s58a)

**Byzantine fault tolerance** or **BFT** creates a system that can operate even if some of the nodes fail or turn malicious. The term is derived from the "*Byzantine Generals' Problem"*, which describes a situation where to prevent a system from crashing, the system's actors have to agree on a concerted strategy, despite some of these actors being unreliable.

In the case of the BFT protocol, a single node termed "*the party*" bundles all the proposed transactions to create a new block in the Blockchain. When a minimum number of other nodes rectifies (agrees/disagrees) this block, a consensus is achieved. Please refer to the following figure:

![](images/Figure-3.13.jpg)

**Figure 3.13:** Byzantine fault tolerance

# [Consortium Blockchain architecture](#toc.xhtml#s59a)

Consortium architecture can be described as a hybrid between the two types. Also called the public permissioned blockchain architecture, anyone can connect and view the Blockchain, but participants can add data or connect a node only with the permission of a majority/all the participants, as the case may be. Consortium Blockchains (*[figure 3.14](#c03.xhtml#fig3_14)*) also depend on PoS and BFT consensus algorithms, just like Private Blockchains. Please refer to the following figure:

![](images/Figure-3.14.jpg)

**Figure 3.14:** Consortium Blockchain

# [Conclusion](#toc.xhtml#s60a)

In this chapter, we have discussed the different types of network architecture and how Blockchain's data architecture is different from the client/server architecture of traditional databases. We have also seen how certain types of blockchains can be more centralized, and how the blockchain architecture can be customized to suit the required use case. We have understood the fundamentals of the different consensus algorithms, and have discussed the various components of a blockchain data structure.

In the upcoming chapter, we will explore some crucial concepts of blockchains—cryptography, encryption, hashing, and the Merkle tree.

# [Questions](#toc.xhtml#s61a)

After reading this chapter, ensure that you have a thorough grasp of these concepts.

1.  **What are the different types of Network Architecture?**
    
    Client-server and P2P
    
2.  **What is a P2P network?**
    
    P2P network is also called a peer-to-peer network. In this network, all network nodes are considered equal and can be client and server at the same time.
    
3.  **What are the differences between centralized, decentralized, and distributed databases?**
    
    Centralized databases have all the data stored in a central place. Decentralized databases store data across multiple locations, for example, internet. Distributed databases are P2P networks where data is available at each network nodes.
    
4.  **What are the various components of a blockchain architecture?**
    
    Nodes, transactions, blocks, consensus algorithm, and so on.
    
5.  **What are the different types of Blockchains?**
    
    Public, Private, and Consortium.
    
6.  **What are the different Consensus Algorithms?**
    
    P-BFT, PoW, and PoS.
    

# [Key Terms](#toc.xhtml#s62a)

1.  **Network topology**: Network topology is the physical arrangement of computers in a network.
2.  **DTE**: Data Terminal Equipment, an end instrument that stores/processes data.
3.  **Networking Operating Systems**: Special operating system that contains the necessary features to facilitate the smooth operation of a server.

# [CHAPTER 4](#toc.xhtml#c04)

# [Blockchain Basics—Cryptography, Encryption, Hashing, and Merkle Tree](#toc.xhtml#c04)

# [Introduction](#toc.xhtml#s63a)

Now that we have been through the components of blockchain architecture and its various types, in this chapter, we will be going through some basic and integral concepts of blockchain technology, which are cryptography, encryption, hashing, and the Merkle tree.

This chapter is divided into three parts; the first part will cover thorough details about the what's and how's of cryptography and encryption, the second bit will explain hashing, and the final part will contain everything you need to know about a Merkle tree.

Now, it is likely that the topics we will be talking about in this chapter are familiar to you—especially the cryptography and encryption bit. So, you might want to skip out on this segment altogether. However, we will be going into depth about these concepts, so there just might be some things you have been unaware of so far; we will implore you to read through the chapter carefully.

# [Structure](#toc.xhtml#s64a)

The following topics will be covered in this chapter:

*   **Part 1: Cryptography and encryption** 
    *   What is cryptography?
    *   Concepts related to cryptography  
        *   Encryption
        *   Decryption
        *   Cipher
        *   Key
    *   Types of encryption
    *   Why is encryption necessary
    *   How does cryptography work?
    *   Methods of cryptography
    *   Cryptography in blockchain
*   **Part 2: Hashing** 
    *   What is a hash?
    *   Cryptographic hash functions
    *   Properties of cryptographic hash functions
    *   Hashing in blockchain
*   **Part 3: Merkle tree** 
    *   What is a Merkle tree?
    *   Forming of a Merkle tree and its functions
    *   Benefits of a Merkle tree in blockchain
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s65a)

Cryptography, encryption, Hashing, and Merkle tree—all four of these elements make up the core of a blockchain, attributing to its secure nature. As a blockchain architect, all of it is included in the fundamental knowledge you are required to possess, and by the end of the chapter, we hope that you will have gained a thorough understanding of the topics discussed.

# [Part 1: Cryptography and encryption](#toc.xhtml#s66a)

Cryptography and encryption are the most central of requirements for developing a blockchain, and in this part, we will see what they are and why they are important.

# [What is cryptography?](#toc.xhtml#s67a)

The term cryptography comes from the amalgamation of two Greek words, which are Kryptos and Graphein. Kryptos means "*hidden"*, and Graphein translates into "*to write*". A blockchain possesses a secure and anonymous nature, which comes from the use of cryptography and its various tools. The term "*crypto"* means concealed, which in the context of blockchains translates into anonymous.

In one sentence: Cryptography is the method of encrypting and decrypting information kept in private messages. To elaborate on that definition: cryptography is essentially a way of creating some techniques and protocols so as to prevent anyone except the intended recipient(s) from accessing the information laid out in private messages during communication.

# [Concepts related to cryptography](#toc.xhtml#s68a)

There are some components related to the concept of cryptography, the primary of which is encryption, and there are other elements associated with encryption. Let us take a look at all these concepts of cryptography:

# [Encryption](#toc.xhtml#s69a)

Encryption is the method with the help of which information in a message is converted into a secret code so the information's true meaning is hidden. Unencrypted information is called plaintext, whereas encrypted data is known as ciphertext. Therefore, encryption is simply the process of turning plaintext into ciphertext.

Encryption is an age-old way of protecting sensitive information; it has been historically used by militaries and governments. Data can be encrypted "*at rest*", as in when it is stored, or it can also be encrypted "*in transit*", as in while it is being transferred to one or multiple receivers.

# [Decryption](#toc.xhtml#s70a)

Decryption is exactly the inverse process of encryption, which means this method converts ciphertext into plaintext.

What is the basic difference between encryption and decryption? Encryption, the method which encodes and hides the contents of a message, is carried out by the sender of a message. On the other hand, decryption, the process of decoding an encrypted message, is performed by the recipient of a particular message.

# [Cipher](#toc.xhtml#s71a)

As we know, the formula or the cryptographic algorithm used to both encode and decode the contents of a private message is known as a cipher. So, a cipher converts plaintext to ciphertext and vice versa.

To do its job right, a cipher includes a variable as part of the algorithm. This variable, which is called a key (more on that later), is responsible for making a cipher's output unique. Suppose an encrypted message gets intercepted by an unwanted third party, then this intruder has to guess which cipher the sender of the message had used to encrypt the message, as well as which keys have been used as variables. Because this is quite difficult and time-consuming to do, cipher makes encryption an invaluable security tool.

# [Key](#toc.xhtml#s72a)

A cryptographic key is invaluable in encryption: it is a string of characters and mathematical values used in an encryption algorithm that both the sender and the intended receiver of an encrypted message agree upon. Like a real-world key, it locks or encrypts information so only a person with the right key can unlock or decrypt it. When the right receiver receives an encrypted message, they would possess the correct key for decrypting the data, turning it back into the actual message.

Secure encryption uses keys so complex that it is made impossible for an illegitimate third party to decrypt the ciphertext in a message.

# [Types of encryption](#toc.xhtml#s73a)

There are two basic kinds of encryption: symmetric encryption and asymmetric encryption. The basic difference between the two is that in symmetric encryption, there is only one key, and all parties involved in the communication use one key for both encryption and decryption of the message. In asymmetric encryption, though, there are two keys: one of them is used for encryption, and the other is for decryption. The decryption key is the one that is kept private (so it is called a private key), whereas the encryption key is shared publicly for any willing party to use (and therefore is called a public key).

# [Why is encryption important?](#toc.xhtml#s74a)

Encryption is necessary for a number of reasons, some of them being:

*   **Confidentiality:** Of course, the primary purpose of encryption is to keep the data being stored on a system or being transmitted over a communication network safe and private. Encryption ensures no one can read the data the sender has encoded but the intended recipients. This prevents any unwanted third party from intercepting and reading any private information.
*   **Maximized security:** Encryption prevents data hacking at all times. It, of course, keeps the encoded data safe during transit or while it is being kept in storage; additionally, if a device is somehow stolen, if it is hard to drive remains properly encrypted, the data the device contains would be secure anyway.
*   **Authenticity:** Encryption verifies the origin of a message.
*   **Data Integrity:** Encryption maintains data integrity, as in when data is sent across the internet to the intended recipients through cryptography; encryption makes sure that the message does not get tampered with.
*   **Regulations:** Encryption helps meet compliance regulations quite often. For instance, some organizations require sensitive information to be encrypted so it remains private and secure.

# [How does cryptography work?](#toc.xhtml#s75a)

Now that we understand what encryption is let us see how cryptography itself works.

Using cryptography, secure messages can be sent between two or more trusted participants. Here is what a sender does to send a private message using cryptography—first, they encrypt a message using a type of key and the cryptographic algorithm of their choice, send this encrypted form of the real message to the receiver, and the recipient then decrypts it with their key to make out the original message.

It can be said that encryption keys are perhaps the most valuable aspect of cryptography. Since they render any encrypted data absolutely unreadable to any intruder, the message can only be decoded by the intended recipient or group of recipients. Therefore, the key is what makes the information "*crypto"*, as in secret.

# [Methods of cryptography](#toc.xhtml#s76a)

There are several methods for encryption in cryptography, three of which we will discuss here. Remember the two types of encryption: symmetric encryption and asymmetric encryption? There are two types of cryptography based on those two encryption types-symmetric encryption cryptography and asymmetric encryption cryptography. And then, there is hashing.

Let us find out about these in detail, shall we?

*   **Symmetric encryption cryptography:** As mentioned before, in this method of cryptography, a single key is used for encrypting a message at the source, transferring it to the recipient, and then decrypting the message once it reaches the right person. This is also called a secret key. 
    
    A simple example of symmetric encryption cryptography is putting alphabets as their equivalent numbers like A is "01", D is "04", and Z is "26". Following this, "HI" can be encrypted as 0809.
    
    While this one is quite simple and, frankly, very easily decodable, numerous complex variations of symmetric encryption cryptography exist for enhanced security. Although this method is very simple to use, symmetric encryption cryptography does face the issue of security due to the shared key and scalability problems. Plus, it is possible to guess the key using the brute force approach, which is less than ideal.
    
*   **Asymmetric encryption cryptography:** As we know, this method of encryption uses a pair of keys, one for encryption or the public key and one for decryption or the private key. The public key, in the case of a blockchain used for cryptocurrency transactions, is the wallet address of a fund receiver, whereas the private key is known only to the owner of the wallet. 
    
    Using asymmetric encryption cryptography, you can encrypt a message using the recipient's public key, but it can only be decrypted by the recipient's private key. Since the public key helps verify the paired private key for the actual sender of an encrypted message, even though the verifier does not have a private key itself, asymmetric encryption cryptography helps maintain authenticity.
    
    The Bitcoin blockchain uses asymmetric encryption cryptography for its keys. The specific method is called secp256k1.
    
*   **Hashing:** Hashing, which we will discuss more in-depth later, is a cryptography method that does not need a key for encryption at all. Instead, the hash method uses a cipher to come up with a hash value of a certain length out of the plaintext. This method makes it near impossible for the contents of the original or plaintext to be decoded from the ciphertext.

# [Cryptography in Blockchain](#toc.xhtml#s77a)

Most tools and techniques of cryptography have been deployed in the workings of various blockchains since Bitcoin's introduction. While most blockchains till date do not really use hidden messages, cryptography has many other purposes in the functioning of a blockchain.

Based on the type of blockchain, the cryptography used in a blockchain gives users pseudo or full anonymity. Cryptography in blockchain can guarantee the security and authenticity of both the transactions made on the chain and the counterparties involved in the transaction.

Cryptography in the blockchain is also used to control the generation of new cryptocurrency coins and to provide protection from the threat of double-spending (copying a particular crypto coin and using it, instead of the real coin, in transactions over and over again). Further, cryptography ensures that users can perform a transaction without requiring a central authority.

One more thing, blockchains replicate the concept of real-world signatures to some extent with the use of cryptography techniques like encryption. Therefore, on a blockchain, data or any digital asset is transmitted in a secure form. Only those whom the asset or information is intended for can receive and process it. This way, with a digital signature, the authenticity of a transaction and the participants involved are ensured through cryptography.

In cryptocurrencies, there are public–private key pairs in use so as to manage the addresses of the users on the blockchain. With the help of cryptography, the public key represents the address of a particular user on a blockchain. This public key, as the name signifies, is visible publicly, so every person on the blockchain can see it. The private key, on the other hand, is kept a secret value and can be used to access data regarding an address.

Digital signatures are also used in cryptocurrencies; they can approve transactions on blockchain by signing them offline and securely and are also deployed for multi-signature contracts and digital wallets on a blockchain. When executing any operation from these multi-signature contracts or digital wallets, digital signatures from all parties involved are needed.

Here is how private and public keys help users sign and verify the legitimacy of a transaction on a blockchain:

![](images/Figure-4.1.jpg)

**Figure 4.1:** How public and private keys work to facilitate blockchain transactions

And that was all about cryptography and encryption—their types and functions, and roles in the workings of a blockchain. Now, we get into details regarding the hash function, which we have already mentioned once before as a type of cryptography.

# [Part 2: Hashing](#toc.xhtml#s78a)

To really understand a blockchain's working, another important notion to grasp is that of the hash function and all related terminologies. Let us see what a hash is first.

# [What is a hash?](#toc.xhtml#s79a)

A hash function is essentially a mathematical function; it transforms a particular input of arbitrary length into an output of a fixed size, also called the "hash value".

No matter what the size of the original input is, the unique hash value will always be the same size. Plus, for cryptographic hash functions, hashes cannot be used to derive the input from the hashed output through reverse engineering because these hash functions are always one-way.

A hash function uses complex mathematical algorithms to convert a set of data into a hash value of a certain length. Therefore, if you change even a single bit anywhere in the original input, the entire hash value is changed. Hence, the hash function is good for verifying the integrity of any input.

Let us see an example of hashing now. It is probably known to you that SHA-256 is the algorithm the Bitcoin blockchain uses for hashing. The algorithm always produces an output of a 256-bit hash. So if you take an mp3 file of 5 megabytes and hash it using SHA-256, the output will be a hash of 256 bits in length. Take an mp4 file of 700 megabytes or a jpg file of 1 megabyte, and the output hash for both would remain 256 bits. The only difference between the outputs would be that their hash patterns would never be identical.

Since hashes ensure maximized security, they are used frequently to maintain security online. Hashes are used in functions ranging from password protection to checking the fidelity of a file downloaded.

# [Cryptographic hash functions](#toc.xhtml#s80a)

What is the basic difference between a general hash function and a cryptographic hash function?

Usual hash functions only take inputs of various lengths to produce outputs of a fixed length. But a cryptographic hash function adds security properties to the typical message-passing capabilities of hash functions. This way, it is more difficult to read the contents of a message or gather information about the senders or the recipients.

# [Properties of cryptographic hash functions:](#toc.xhtml#s81a)

For a cryptographic hash function to be considered safe, there are some certain characteristics they must exhibit. After all, without these properties, a cryptographic hash function cannot be considered suitable for blockchains. Here are some of these mandatory properties of a cryptographic hash function:

*   **They have to be deterministic**: This means that regardless of how many times you run an input through a hash function, the output would remain of the same length. Although the hashes will be random and of different patterns, they will always be of the same length. This way, it is easier to keep track of input data using the hash.
*   **They should be able to perform quick computations**: Ideally, a cryptographic hash function should be performing swift computations for every input, regardless of its size. This means a 5 megabyte file and a 50 megabyte file should be processed with equal speed.
*   **The cryptographic hash function should produce different hashes for every single input**: Even if the information in the inputs are only differentiated by a single character, the hash function should be producing completely different outputs for them. This is because if the patterns in the hash were similar or only slightly different, it would be easier to find the input from them.
*   **The hash function should be one-way**: A cryptographic hash function has to be one-way to provide maximum possible security. So if you see a hash for a certain transaction, it should be implausible to root out the original input from this output you have. The only imaginable way of finding the original input data would be to hash all the possible combinations of input data until you eventually stumble upon the right input. And even then, since the input information is randomized, decoding a hash is basically unthinkable.
*   **Cryptographic hash functions should be collision-free**. What this means is that the hash function should not be giving similar outputs for two completely different inputs.

# [Hashing in Blockchain](#toc.xhtml#s82a)

Hashing is essential to a blockchain, and it can be said that the cryptographic hash function forms the backbone of the blockchain network.

Hashes are used in quite a few parts of a blockchain. First, all blocks contain the hash of the block header from the block right before it, which ensures no data stored in the previous blocks has been tampered with as new blocks are added (because if a block has been meddled with, its header would immediately change, showing the intrusion).

Further, blockchains that use a proof-of-work algorithm for mining (like the Bitcoin blockchain) use the hashing of randomly generated numbers so as to create a certain hashed value that contains a series of leading zeroes. This makes it even more difficult for a hacker or a bad actor to invade the blockchain network.

The hashing function is also important in crypto mining because it takes the computing of several hashes to discover a valid nonce. During mining, finding the hash for a new block starts with the data in the block header and what is basically a complex mathematical problem. Each block header has a version number, a timestamp, the hash used in the previous block, the hash of the Merkle Root (more on that to come), the nonce, and the target hash. The miner has to focus on the nonce, which is a string of numbers appended to the hashed contents of the last block in the chain, which is then hashed. If the new hash is less than or similar to the target hash, it is accepted as the solution, and the new block is added to the chain.

As for further use of hashing in blockchain, addresses on blockchains are found through hashing (like Bitcoin addresses, use SHA-256 and RIPEMD 160). Hashing helps to define cryptographic signatures, which are used to determine whether transactions are valid or not. The hash of a particular transaction makes it super easy to trace it among the blockchain records. Moreover, the hashing function keeps the permanent data storage light.

And now that we know all the fundamentals of the cryptographic hash function, its properties, and its uses in blockchain, it is time to jump into details regarding the Merkle tree. You will find the concept of a Merkle tree is thoroughly intertwined with that of the cryptographic hash function.

# [Part 3: The Merkle tree](#toc.xhtml#s83a)

The Merkle tree also called a hash tree, is an integral part of blockchain tech. Before we see what purpose they serve on a blockchain, let us first get a clear idea of what a Merkle tree is.

# [What is a Merkle tree?](#toc.xhtml#s84a)

The Merkle Tree is named after Ralph Merkle, who proposed the concept of them in a paper called "*A Digital Signature Based on a Conventional Encryption Function*". The same man is also the person to have invented the cryptographic hash function; he patented the idea of a hash tree back in 1979.

What is a Merkle tree, really? It is a mathematical data structure made up of the hashes of various blocks of data; the Merkle tree essentially acts as a summary of every transaction included in a block.

A Merkle tree allows the deft and secure verification of all the contents in quite a large body of data. Plus, the Merkle tree also lets you verify the consistency of all the data included. Blockchains of popular cryptocurrencies—such as Bitcoin and Ethereum, use the Merkle tree structure to encode the data stored on the blockchains with more security and efficacy and to save up on blockchain storage space.

# [Forming of a Merkle tree and its functions](#toc.xhtml#s85a)

Here is a practical example of how a Merkle tree is created: In the Bitcoin blockchain, a whole block of transactions is taken through a complex algorithm to create a hash. It is to be noted that since an average block contains at least 500 transactions, all the transactions cannot be taken through the algorithm at once; instead, each of the transactions in the block is hashed, and then two of the transactions are paired up and sent through the algorithm together. This way, hashing pairs are calculated until one hash is produced for the entire block.

When visualized, the whole structure looks a lot like a tree. Hence, it has been named the Merkle tree. The Merkle trees are always made up in a bottom-up approach. All the hashes on the bottom-most row are known as the "*leaves*", the intermediate hashes are called the "*branches*", and the hash at the very top is dubbed the "*root*". In fact, the topmost hash is also the ultimate hash that emerges at the very end of the whole block. This hash is named the Merkle Root, as mentioned once before; alternatively, it is also known as the Root Hash.

Every hash in the bottom row, or the leaves, are hashes of transactional data. All the non-leaf hashes are generated from previous hashes. The Merkle trees are binary trees, which means they need an even number of "*leaves"* to function as they are supposed to. In case there is an odd number of these leaves, the very last hash is usually duplicated once so as to come up with an even number of leaves.

The hash called the Merkle Root gets stored in the block header as part of the mining process on proof-of-work blockchains. The block header of a block on the chain is supposed to contain the hash of the last block, a Nonce, and the Root Hash that came out of the hashing of all the transactions in the current block found in its respective Merkle tree.

Once combined with other information (that is, the previous block's hash, the timestamp, the difficulty target, and the nonce), the Merkle Root is run through the cryptographic hash function again to turn up the block's unique hash.

Now, this hash is not included in the same block for which the Root Hash was derived. Instead, it is sent to the next block and is featured in that block's header. Therefore, a block's unique hash is different from the Merkle Root.

The one in the following image is the simplest form of a Merkle tree, which is called the Binary Merkle Tree. There are four transactions in a block—TX1, TX2, TX3, and TX4. As you might have noticed, the hash on the top is the hash of the whole tree, or the Merkle Root/Root Hash. Please refer to the following figure:

![](images/Figure-4.2.jpg)

**Figure 4.2:** How the Merkle root is deduced

Each of these is hashed again and again and then stored in every leaf node, resulting in the hashes 0, 1, 2, and 3. Next, consecutive pairs of leaf nodes are put into a parent node by hashing. Hash0 and Hash1 result in Hash01, and similarly, Hash2 and Hash3 become Hash23. These two new hashes are once again hashed to come up with the Root Hash or the Merkle Root.

Putting the Merkle Root in a block's header, as shown in the following image, helps secure the blockchain. Please refer to the following figure:

![](images/Figure-4.3.jpg)

**Figure 4.3:** The Merkle root is put in a block's header to save storage space

Since the Merkle Root contains the hashes of every transaction included in its block, they also help save storage space on the blockchain. The concept is, therefore, both a critical security measure and an efficiency booster for blockchain networks, helping such networks scale and grow more easily.

# [Benefits of a Merkle tree in blockchain](#toc.xhtml#s86a)

Merkle trees are quite advantageous for blockchains for many reasons, some of them are as follows:

*   The Merkle tree provides blockchain tech with the means to maintain data integrity and confirm its validity. If any changes are made regarding even the minutest details of a transaction or the order of transactions in a block, the change is immediately reflected in the hash for that transaction and the block. This is because the change goes right up the Merkle Tree to the Merkle Root, changing the Root Hash, and thus, rendering the block itself invalidated. So Merkle trees contribute to the security of a blockchain by pointing out any glitch. Why prefer Merkle trees over other data structures? Because they are significantly more efficient on verification of data integrity. They are easier to store and transmit, and verifying their proof also takes up less space.
*   The Merkle tree helps blockchains in saving storage space, as we mentioned before.
*   The Merkle tree allows participants on a blockchain to verify a particular transaction without having to download the whole blockchain; since they can be broken down into small pieces of data for verification. **Simple Payment Verification** (**SPV**) is used for this verification—where the proof of inclusion is requested via a Merkle branch in the tree. Only the block headers are required to be checked for this verification. If the transaction can be linked to the tree in this manner, it exists.
*   The Merkle tree essentially generates a digital equivalent of a fingerprint for all the transactions in a block taken together. It lets the user verify if a certain transaction is included in a block or not.

And that were all the basic facts you should know about a Merkle tree as someone applying for the position of a blockchain architect.

# [Conclusion](#toc.xhtml#s87a)

In this chapter, we explored the concepts of cryptography, encryption, hashing, and the Merkle tree. In the context of a blockchain's basic architecture, it is easy to see that all four of these concepts are interrelated and are all responsible, in their own ways, for strengthening the security aspect of a blockchain, in addition to maintaining data integrity, protecting users' personal information, expanding storage capacity, and a lot more.

Whether you are a beginner in the blockchain field with the hopes of joining the industry as a blockchain architect or someone who is already aware of the basics of blockchain, we do hope this chapter has added to your knowledge.

Now, in the upcoming chapter, we will learn about some more of the basic concepts related to blockchain—transactions, banking, ledger accounting, and distributed ledger technology (DLT).

# [Questions](#toc.xhtml#s88a)

1.  **What is cryptography?**
    
    Cryptography is a field of computer science where we talk about the encryption and decryption of data, so that data can be securely stored/transmitted.
    
2.  **What is encryption?**
    
    Encryption is a technique using which data is transformed in a different format than the original format, making it difficult for others to guess the original data.
    
3.  **What is a cryptographic key?**
    
    Cryptographic key is an input to encryption/decryption algorithms using which data is encrypted/decrypted.
    
4.  **What is the fundamental difference between encryption and decryption?**
    
    In encryption, we convert the data being sent into a different format, whereas in decryption, we convert the encrypted data back to the original data.
    
5.  **What are the various methods of cryptography?**
    
    Symmetric and Asymmetric
    
6.  **How is cryptography used in blockchain?**
    
    Cryptography is used in blockchain to give security and authenticity.
    
7.  **What is a hash?**
    
    A hash is a unique value that is associated with one particular data. If we change even one bit of that data, the hash should also change.
    
8.  **What are some qualities an ideal cryptographic hash function should have?**
    
    An ideal hash function should result in a completely different hash result if even a single bit of data is changed.
    
9.  **What roles does hashing play in blockchain?**
    
    Each block stores the hash of the previous block
    
    Crypto mining
    
    Blockchain addresses
    
10.  **What is a Merkle tree?**
     
     A Merkle tree stores the hashes of all the transactions in a block. And then it also calculates hashes of those hashes in a bottom up manner.
     
11.  **What benefits does a Merkle tree have on a blockchain?**
     
     Merkel trees provide security, storage saving, and verifiability of blockchain easier.
     

# [Key terms](#toc.xhtml#s89a)

*   **Cryptography:** This is the method through which private messages are encrypted and decrypted.
*   **Hashing:** Hashing is a mathematical function that transforms a particular input of arbitrary length into an output of a fixed size, also called the ‘hash value'.
*   **Merkle Tree:** A Merkle tree is a mathematical data structure made up of the hashes of blocks of data, so it is basically the summary of every transaction included in a block**.**

# [CHAPTER 5](#toc.xhtml#c05)

# [Blockchain Basics II —Transactions, Banking, Ledger Accounting, and DLTs](#toc.xhtml#c05)

# [Introduction](#toc.xhtml#s90a)

In the previous chapter, we covered some basic concepts of blockchain technology that strengthen its security. Now, in this chapter, we look through what the digital era is and the history of money, banking, and transactions. Further, we have explained how centralized influence in traditional finance has left much to be desired and why decentralized solutions can solve the problems, such as single point of failure, lack of transparency and accountability, financial freedom, and plaguing traditional finance.

With people looking for decentralization systems instead of traditional financial structures and procedures, the simultaneous rise in popularity of the blockchain and Distributed Ledger Technology or DLT offers up an easy and fortuitous solution to be combined with fiat finance or even to create entirely new financial products and services. That is why at the end of this chapter, we have also tried to give you all the crucial details you would need to know about distributed ledgers and the DLT.

# [Structure](#toc.xhtml#s91a)

The following topics will be covered in this chapter:

*   What is the digital era?
*   What is bartering?  
    *   The definition of bartering
    *   Benefits of bartering
*   What is money?  
    *   The definition of money
    *   Categories of money
    *   How is money created?
*   What is banking?  
    *   What is a bank, and what does banking mean?
    *   Importance of banking
*   Understanding transaction and traditional methods of accounting  
    *   What is a transaction?
    *   What is accounting?
    *   Types of traditional accounting (accrual accounting, cash accounting)
    *   Ledger accounting
*   Central influence in traditional finance
*   Distributed ledger technology  
    *   What is a distributed ledger?
    *   What is DLT or distributed ledger technology?
    *   Properties, advantages, and uses of the distributed ledger technology
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s92a)

To grasp the notions of blockchain and decentralized finance, you will also understand the core concepts of currency, transactions, and traditional banking. With this chapter, you will have a better understanding, along with a solid idea of decentralized ledgers and Decentralized Ledger Technology. Without further ado, let us start with what the digital era constitutes.

# [What is the digital era?](#toc.xhtml#s93a)

The beginning of the ongoing digital era is characterized by the major shift from the industrial revolution to the economic domination of information and communications technology (ICT) that occurred in the 21st century. The digital era has come to be synonymous with the information age.

Defining components of the digital era include technological innovations such as the internet, microprocessors, digital cellular phones, cloud computing, the IoT or the Internet of Things, virtual reality, and so on.

The biggest achievement of the digital era so far, without a doubt, has been the widespread adoption of the internet. While technically, Tim Berners-Lee invented the World Wide Web back in 1989, it was not until 2005 that it truly reached the average population across the globe. Cloud computing, on the other hand, went mainstream only in the early 2010s. As of 2020, around 67% of the entire globe's population was reported to be connected through the internet.

# [What is bartering?](#toc.xhtml#s94a)

Now that we know what the digital era consists of, it is time to get into the core concepts of finance. We start with the idea of bartering and its advantages.

# [Definition of bartering](#toc.xhtml#s95a)

Bartering is essentially the act of trading some goods or services without using money or any monetary medium at all. Therefore, bartering includes the exchanging of a product by one party in return for another product from a counterparty. This is the simple, basic idea of bartering: when two parties each have an item the other wants, they negotiate to determine and agree upon the relative value of the goods that they wish to trade, so the transaction can be an even one. Practically, any item can be eligible for bartering as long as your bartering partner agrees to the terms of the trade. The defining aspect of bartering is that it is cashless.

Examples of bartering can be found even in the earliest history of humankind since it is the oldest form of commerce. To this day, people and companies barter various products or services among each other based on the equivalent estimates of other products and services. With access to the internet, you can barter with anyone from any corner of the globe; therefore, the digital era makes the act of bartering a super easy one.

Since the financial crisis of 2008, bartering has become extremely popular with small businesses in particular. In fact, a report from the New York Times suggested that barter exchanges saw double-digit gains in membership in 2008 alone. The barter economy at the time of the financial crisis supposedly reached $3 billion.

# [Benefits of bartering](#toc.xhtml#s96a)

Bartering is a very good way to reduce debt in case you do not have the funds to buy a product, but it is also generally a very good solution if you want to save up on your money. Bartering allows you to swap out items you own but remain unused for items you actually need, and you can save your funds for any future expenses or emergency situations.

Aside from individuals, businesses and other entities might want to participate in bartering for a number of reasons. Bartering enables businesses to find new customers for their existing products and use their unused inventory to access any products or services they truly need. Companies might wish to barter away a product they own for another product that they do not have the cash or the credit to purchase. Bartering is a super-efficient way of trading for small businesses because any risks associated with foreign exchange platforms are done away with this way. A good example of a business-to-business barter would be the exchange of advertising time and space. Companies often trade the power of advertising in one another's business spaces.

What is more, even national governments might partake in bartering in case there is a lack of funds or if they are already in debt. They export various products in exchange for the products the country is in need of.

The act of bartering can facilitate an optimal distribution of resources by allowing the exchange of products and services in quantities that stand for equal values. Therefore, because with bartering demand and supply are balanced out nicely, the process can help economies achieve parity.

Experts also claim there is a psychological benefit to bartering: the act of bartering can help develop a deep personal relationship between the counterparties involved, as opposed to a monetized transaction through a centralized financial institution. This way, bartering can help people build successful professional networks and create a great market for their own businesses.

# [What is money?](#toc.xhtml#s97a)

So now we know all about bartering and what benefits it can give you as an alternative to monetary exchange. However, while bartering is all well and good, money is figuratively what makes the earth spin on its axis every day in today's world. Money is what everyone, from the average populace to the national governments, relies on to keep the global economy running.

In this part, we define money, see its various categories, and also where the money comes from.

# [The definition of money](#toc.xhtml#s98a)

Money—like the US dollar and the Indian Rupee, is a unit of account and a medium of exchange. Money is usually a socially accepted unit that determines how things are valued. Basically, money allows everyone to obtain any goods or services they need in exchange for it.

Historically, the currency has changed forms a lot, from grains to silk to metal coins and paper money. However, the primary purpose of money has not changed with time: **money, first and foremost, remains a medium of exchange**.

Fiat money, like the INR, is issued by a nation's government. While some forms of money can be backed by physical commodities like precious metals (i.e., gold and silver), fiat money is only backed by the good trust and faith in the government that issues it. It can be said that money only has value because people believe it stands for something valuable.

In the 20th century, fiat money was backed by gold reserves, but the limited amount of gold in central bank reserves was not enough to back the new value that was being created, causing disruptions in global commerce. While fiat currency allows the government to manage the money supply and monetary policies in the country, the faulty policies and incessant currency printing of by the government may lead to hyperinflation and financial instability in the economy.

In the previous section, we discussed bartering and its benefits. Before money came about, bartering was how everyone acquired goods. Where bartering falls short, though, is that it does not provide the easy transferability or divisibility of money. The shortcomings make the act of bartering pretty inefficient; however, money solves all those problems.

# [Categories of money](#toc.xhtml#s99a)

Commodity money was what came before the fiat money of today. Commodity money is essentially some kind of good that acts like currency. Commodities that have been used as money include metals such as gold, silver, and copper; food items; and beverages including salt, peppercorns, tea, alcohol, cocoa beans, candy, barley, and other items such as shells and silk.

Since these commodities possessed values that were socially accepted, they served as physical tokens of wealth and were used in trading. Other characteristics of commodity money include portability, durability, and ease of storage.

Aside from commodity money, there is, of course, fiat money. Fiat currency is not backed by any physical commodity; as said before, fiat money came about because precious assets being used as currency were becoming scarce. In today's time, the value of fiat money is decided by its purchasing ability. Even though technically, governments are allowed to print new money as per necessity, it does not mean simply creating new money will make a country wealthy. Money is created only with the perfect balance between tangible things, people's demand for them, and their abstract belief in the value of a particular fiat currency. Again, money has value only because we need it to and believe so, and we need money only to get an item or a service we require or want.

If governments engage in reckless currency printing, it will lead to inflation, leading to erosion of the currency's value. Money is a facilitator/medium of exchange, and printing it more cannot get an economy out of recession, nor will it create more value in terms of goods and services. For instance, if a government prints more money and the output remains the same, the same thing would cost more, or, in other words, you would be paying more for the same thing. The value of a currency note will decline, and if the printing continues, the fiat currency may get unstable or drop to zero in value. The financial crisis in Sri Lanka \[**[https://en.wikipedia.org/wiki/2019-present\_Sri\_Lankan\_economic\_crisis](https://en.wikipedia.org/wiki/2019-present_Sri_Lankan_economic_crisis)**\] could be an example of complications that may arise due to money creation.

It is important to measure money to deduce whether there is inflation or deflation. Inflation refers to the increase in prices of goods and services in an economy. It leads to a reduction in the purchasing power of a consumer. On the other hand, deflation implies the decrease in prices of goods and services and a subsequent increase in the purchasing power of a consumer. For measurement purposes, money is usually divided into three classes, which are as follows:

*   **M1:** M1 money or active money is basically the entire value of coins and paper notes in circulation. This number keeps fluctuating seasonally, monthly, or even on a daily basis, sometimes since the demand for cash keeps changing as well. Once banks lend out money to their clients, they become active money—as in, they are then actively circulated. Among the three categories of money, this one is the narrowest.
*   **M2:** The M2 category is all about the money that can be transferred into cash readily. The M2 category money adds the money in M1 to time-related deposits, savings account deposits, and non-institutional money market funds.
*   **M3:** As opposed to M2, this one is the broadest category of money. M3 takes M2 money and adds it to all large-time deposits, institutional money market funds, short-term repurchase agreements, and many other larger liquid assets.

All three categories together represent the entire amount of money in an economy.

# [How is money created?](#toc.xhtml#s100a)

The creation of fiat money is heavily influenced by centralized authorities (like the Reserve Bank of India \[RBI\]). Indeed, a country's central bank can affect and manipulate the supply of money.

For the most part, this is how the act of printing out new money goes: as long as the people believe in a particular fiat currency, the central bank in the country can generate more money as needed. However, it is important to remember that if a central bank puts out too much money at once, the value of the fiat currency will drop consistently because only no new value but currencies are being created. The same value will now be shared by a larger number of units of currencies. So while a central bank has the power to generate new money, it cannot actually do it relentlessly.

# [What is banking?](#toc.xhtml#s101a)

So now that we possess an idea of what money is and how new money comes into circulation let us get into the concept of banks and banking.

# [What is a bank, and what does banking mean?](#toc.xhtml#s102a)

A bank is a financial organization that is licensed to take in deposits and create loans. There are three primary and most common types of banks, the central banks, the commercial or retail banks, and the investment banks.

Depending on the type, banks provide a number of financial products and services. The central banks, as you already know, are responsible for price stability; they can manage inflation or deflation, come up with and dictate monetary policies, and supervise the market supply and demand of a fiat currency.

Although price stability refers to a stable price level or low level of inflation, monetary policies that a government forms refer to policies concerning economic stability and growth by managing money supply.

The commercial or retail banks offer quite a few services like letting clients create basic checking and saving accounts, managing money deposits and withdrawals, giving out certificates of deposit, allowing debit and credit cards to clients that are qualified, supplying short- and long-term loans such as car loans, home mortgages or equity line of credits. Finally, investment banks, in particular, target mainly corporate clients. Services they provide include merger, acquisition activity, and underwriting, naming only a few.

As for what banking means, banking is a term that refers to the industry that handles and processes cash, credit, and essentially all sorts of financial transactions. Banking includes the acts of accepting and protecting the money owned by various individuals and organizations and then loaning the aforementioned money out so as to use the interest as a good way to make a profit and cover the many operating expenses that incur.

# [Importance of banking](#toc.xhtml#s103a)

Banking is a huge part of the current global economy, and for good reasons too. First, banks accept deposits from various entities and forward them as loans to eligible people in need, which is one of the major aspects of banking that make it integral in today's economy. Moreover, banks offer another feature called "creating credits", which basically means there is additional money for lending purposes.

Banks act as intermediaries while clients conduct transactions between themselves, whether domestic or global. Your deposits are usually withdrawable on demand through cheques or other specified methods.

In the past few years, the banking sector has also incorporated internet services, and banking has made it easier for clients to trade money among themselves. Banks help you manage and plan your finances with meticulous record-keeping. With banks, you can get your liquid assets insured, invest your money and earn interest on your deposits, and use both debit and credit card services. Finally, banks can help you build a credit history that would help you in the future should you require to take out any loans.

# [Understanding transaction and traditional methods of accounting](#toc.xhtml#s104a)

After getting to know the basics of banking and the many operations of banks, now, we will be going into details regarding the monetary transactions we conduct on a regular basis, and the process of recording said transactions—known as accounting.

# [What is a transaction?](#toc.xhtml#s105a)

A transaction is basically a concord between counterparties to exchange any goods, services, or some sort of financial assets. For instance, when you are buying a product from a grocery store, the transaction that occurs is pretty straightforward—you pay the shopkeeper in exchange for the particular product, they agree on the terms of the transaction, and the transaction is carried out.

Of course, not all transactions go down this simply. For instance, a company might agree to a deal for which the transaction would only be settled at a specific point of time in the future. Businesses might have revenues and expenses that are due at a later date. A third-party transaction—which is again a business deal that involves other individuals or organizations aside from the main participants (like a bank), is also more complex than your usual transaction.

Transactions and accounting are concepts that go hand-in-hand because they are intricately linked. Now, we see what accounting is.

# [What is accounting?](#toc.xhtml#s106a)

The simple definition is exactly what we said before—accounting is the process of documenting financial transactions. Accounting is the umbrella term for the acts of measuring, processing, and communicating financial information regarding economic entities like various companies and businesses.

Accounting for a business includes creating financial statements that feature a complete and precise record of the business's financial transactions over a certain period (like one year), and these transactions refer to the many operations it has performed, its financial position, and cash flows (cash flow refers to the total amount of money moving in and out of business in the form of payments or receipts). All this financial information is summed up, analyzed, and reported to various oversight agencies, regulators, and tax collectors.

Depending on the type of accounting a business uses, a particular transaction can be recorded earlier (like when a deal has been struck but will get carried out in the future) or later (after the deal has been closed). The type of accounting, therefore, also impacts a company's financial and tax reporting.

# [Types of traditional accounting](#toc.xhtml#s107a)

There are two basic types when it comes to traditional accounting, which are as follows:

*   **Accrual accounting:** When accrual accounting is used, a company only records a transaction when it occurs, regardless of when the money is received or paid. With accrual accounting, a company records income when completing a service or delivering a product. If the company purchases goods on credit in the month of June, the transaction is also recorded among the expenses in June, even if the business does not actually make the payment until August.
*   **Cash Accounting:** With the cash accounting method, transactions are recorded only when the actual payment is done. So income is recorded when cash, cheque, or credit/debit card payments are received from clients, and expenses are recorded at the time of the payment.

Cash accounting is mostly used by small businesses, companies that have less than $1 million in sales annually. Accrual accounting, on the other hand, is used by businesses that have gross receipts of over $1 million a year.

Accrual accounting operates on the idea of matching revenue with expenses. While cash accounting does not acknowledge a transaction until they are completed, most of the businesses today have an inventory and makes sales on credit. In order to have a true and precise picture of the company's operations, both the inventory, for which a business incurs expense and credit sales, for which the business will receive payments in the near future should be counted. Hence, accrual accounting is a better method of accounting.

# [Ledger accounting](#toc.xhtml#s108a)

The ledger in accounting contains all the financial information that is needed to build financial statements. A ledger represents accounts for assets, liabilities, revenue, expenses, and owners' equity. This list of accounts is called the chart of accounts. The transactions that are recorded across the year are done by debiting and crediting all these accounts, and they are caused mostly by the usual business operations like billing clients or through the act of adjusting entries.

Usually, businesses that use the double-entry bookkeeping method (a procedure where each new entry to an account must have a corresponding entry to at least one other account) for recording transactions make use of the accounting ledger. Each entry in the ledger has a debit and a credit transaction recorded in two columns; the debit entries are on the left, and the credit entries are on the right.

The basic accounts contained in a general ledger include:

*   Asset accounts like:  
    *   Fixed assets
    *   Prepaid expenses
    *   Accounts receivable
    *   Cash
*   Liability accounts like:  
    *   Payable notes
    *   Lines of credit
    *   Accounts payable
    *   Debt
*   Revenue accounts
*   Expense accounts
*   Stockholders' equity accounts

Accounting ledgers can sometimes contain written records, and if accounting software packages are in use, they might also be electronically recorded.

The arrangement of entries in an accounting ledger groups transactions together into specified accounts so as to help you pull up the details of all your transactions whenever needed and evaluate the information in the future for internal economic and accounting reasons. Accounting ledgers are also used to develop the trial balance, which is the source of financial statements like the income statement and the balance sheet.

# [Central influence in traditional finance](#toc.xhtml#s109a)

At this point, we know a lot about the various key concepts of traditional finance, like money and banking and transactions, and we have a general idea of how centralized finance works. Now, in this section, we discuss one of the primary shortcomings of traditional finance, which is the massive central influence you have to deal with when fiat money is used.

To begin with, we have already seen how a country's central bank is capable of controlling its respective fiat currency. That means there are many ways for a central bank to control the supply of money in a country. For instance, if a central bank decides to boost economic activity in the country, it can add to the amount of money already being circulated by printing out new money.

Moreover, to increase the supply of money, a country's central bank can buy government fixed-income securities available in the market. Securities are tradable financial instruments used to raise money in the financial market. By purchasing all these government securities, the central bank channels more money into the marketplace, and in turn, it reaches the general public. While that's all well and good, the real question that comes to mind is how exactly does a central bank pay for all the securities? Weirdly enough, the bank is in a position to simply generate new money to buy the securities with.

On the other hand, to reduce the monetary supply and discourage inflation, the central bank can also sell government securities. The money that the buyers transfer to the central bank is then taken out of circulation, to put it simply.

What more can a central bank do to manipulate the monetary supply in a nation? It can lower interest rates, which gives banks the power to extend low-cost loans and credit (this particular phenomenon is known as cheap money), and which then stimulates both various companies and individuals to borrow and spend more.

However, it is still to be noted that despite all this power, a central bank ultimately cannot keep printing out new money without any limits. There is the fact that if they issue too much money at once or even back to back, the value of that particular fiat currency will go down as per the laws of supply and demand.

There is still more to centralized influence in traditional finance. When you are performing a transaction with your credit or debit card or through a cheque, there is a bank involved to watch over and allow this trade. In case you have to make an international transaction, there will be several financial institutions involved to facilitate and see the trade through, and you have to pay additional fees and wait a long time waiting for the transaction to get completed. So in traditional finance, you simply cannot avoid the interference of a third party or an intermediary, and your money is always supervised by a centralized organization.

Also, since banks store all their data on centralized servers, there are greater chances of a system failure or hack causing a breakdown in the functioning of a bank. Centralized databases are vulnerable as the banks have a single point of failure. Also, these records are prone to manipulation, and many get destroyed as a result of a hack or attack. When we bring distributed ledgers into context—they store multiple copies of the same database, which store data immutably, i.e., once written, the data cannot be altered or erased easily.

All these reasons and yet more mean that centralized finance takes your control over your own money away—at least to some extent. A decentralized solution, on the other hand, gives you full control over your own money, and you can perform your transactions without having to wait for a centralized authority figure to approve it or wait for your transaction to get fulfilled. This is the primary reason why, lately, more and more people are leaning toward decentralized finance and incorporating blockchain tech and the DLT in existing financial systems.

# [Distributed ledger technology](#toc.xhtml#s110a)

Now in this part, we see what exactly is this DLT or Distributed Ledger Technology and what it is used for. But first, let us go through what a distributed ledger is.

# [What is a distributed ledger?](#toc.xhtml#s111a)

We already know what purpose a ledger serves in accounting. Now, as for a distributed ledger, it is a database consensually distributed and synchronized across a number of different sites, organizations, individuals, and geographic locations, and it is made accessible to multiple participants.

Distributed ledgers use the same technology as blockchain since blockchain is basically a distributed ledger that Satoshi Nakamoto deployed as the underlying technology of the first crypto Bitcoin.

A distributed ledger allows the transactions recorded on it to have public witnesses. The participants on the ledger can see all the records documented on the network and own an identical copy of the records each. If any changes or new records are made to the ledger, all copies with the participants are updated almost instantaneously. The distributed ledger allows the participants anonymity since they are not required to share any personal details. But every transaction done by the participant's wallet address is completely traceable as the transaction is now immutable and stored in the distributed ledger.

The Ethereum network is one of the best examples of a distributed ledger protocol.

# [What is Distributed Ledger Technology (DLT)?](#toc.xhtml#s112a)

The Distributed Ledger Technology is based on the basic principle of the distributed ledger—the DLT is a technological infrastructure that allows many participants from across the world to access it and facilitates the recording of information in an immutable fashion across the network. The DLT ensures the safety of a virtual, decentralized database, and by nature they do not require a centralized authority figure or any third-party entity to intervene or supervise.

The following diagram depicts the distributed ledger technology at play. The distributed database here is shared among a variety of nodes or participants, including banks, businesses, individuals, group of individuals, and so on. Please refer to the following figure:

![](images/Figure-5.1.jpg)

**Figure 5.1:** A diagram depicting distributed ledger technology

The DLT was introduced by the cryptocurrency Bitcoin, but it has already spread across many other industries aside from cryptocurrency, including supply chain, real estate, healthcare, education, accounting, and cloud storage, among others.

# [Properties, advantages, and uses of the distributed ledger technology](#toc.xhtml#s113a)

You would already be aware of the many properties of the DLT that make it so beneficial across a range of industries, but the basic attributes of DLT have been summarized anyway in the image as follows:

![](images/Figure-5.2.jpg)

**Figure 5.2:** Important properties of Distributed Ledger Technology (DLT)

As opposed to the centralized ledger we discussed before, Distributed Ledger Technology does not leave a singular, central point of failure; distributed ledgers are, therefore, inherently more difficult to manipulate, as all its copies with all the participants must be attacked at once for the attack to be a success. With Distributed Ledger Technology, the threats of a cyber-attack or financial fraud are decreased by a significant margin.

Plus, all the information on distributed ledgers is securely stored with cryptography. The intended participants can only access the information using keys and cryptographic signatures.

What is more, once information is stored on a distributed ledger, it becomes immutable since that is one of the basic properties of a distributed ledger. The DLT also facilitates increased transparency because of the decentralized aspect.

Distributed ledgers accelerate transactions and grandly reduce the amount of time a usual fiat transaction would need to complete. They also operate 24/7, and the peer-to-peer sharing and updating of records essentially reduce the total expenses of the participants using them.

Aside from finance, the DLT is already in use across several other industries, such as gold, diamond, and other precious metals, the entertainment sector, supply chains for a range of commodities, and so on.

Distributed ledgers have the potential to reform the way national governments operate; they can prove to be of great use in things such as tax collection, passport, various licenses issuance, recording land registries, and electoral events.

# [Conclusion](#toc.xhtml#s114a)

And that was all about the basics of centralized finance and what benefits the DLT can bring over the traditional ways of finance.

When seeing the notions of money, banking, and traditional transactions, it is easy to see how at all times, your money is being controlled by centralized entities, and you have very limited power over your own funds.

On the other hand, with the idea of decentralization at its core, the DLT can revolutionize finance (and other industries) altogether while also giving you full power over the money you own. We hope this chapter has enhanced your knowledge of some primary components of traditional economics and strengthened your concept of DLT.

In the upcoming chapter, we see a comparison between the way Bitcoin and Ethereum work, focusing on the growth of decentralized finance, tokenization, and Initial Coin Offerings (ICOs).

# [Questions](#toc.xhtml#s115a)

1.  **What is the digital era?**
    
    Digital era is defined by technological innovations such as the internet, microprocessors, digital cellular phones, cloud computing, Internet of Things, virtual reality, and so on.
    
2.  **What is bartering?**
    
    Act of exchanging goods and services
    
3.  **What are some benefits of bartering?**
    
    No need for central/flat currency. Does not require cash.
    
4.  **What is money?**
    
    Medium of socially accepted exchange
    
5.  **What are commodity money and fiat money?**
    
    Commodity money is backed by gold, silver, and so on. Flat money is backed by central authority and accepted by people.
    
6.  **How many categories can fiat money be divided into? What are the categories?**
    
    M1, M2, and M3.
    
7.  **Who has the power to generate new fiat money, and in what conditions can they do so?**
    
    Central bank/government. When inflation increases/government needs more money.
    
8.  **What is a bank?**
    
    Bank is a central system that takes deposits and gives money on credit to people who need it.
    
9.  **What are some benefits of banking?**
    
    You can take a loan when you have a shortage of money and also invest/deposit excess money.
    
10.  **What is a transaction?**
     
     Transferring money from one account to other accounts.
     
11.  **How many types of accounting are there?**
     
     Accrual and cash accounting
     
12.  **What is an accounting ledger? What purpose does it serve?**
     
     Maintains database/history of transactions.
     
13.  **How does centralized influence in traditional finance work?**
     
     Increase/decrease/manipulate monetary supply.
     
14.  **What is a distributed ledger?**
     
     Ledger is maintained by many participants across the world.
     
15.  **What are the benefits of Distributed Ledger Technology?**
     
     No centralized influence, secure, quick transaction, and so on.
     

# [Key terms](#toc.xhtml#s116a)

*   **Bartering:** This is the act of exchanging a product by one party in return for another product from a counterparty.
*   **Money:** This is a unit of account and a medium of exchange.
*   **Bank:** This is a financial organization licensed to take in deposits and create loans.
*   **Transaction:** A transaction is a way to exchange any goods, services, or some sort of financial assets between two or more parties.
*   **Accounting:** This is a comprehensive term for the acts of measuring, processing, and communicating financial information regarding economic entities like various companies and businesses.
*   **Distributed Ledger:** It is a database consensually distributed and synchronized across a number of different sites, organizations, or individuals, and geographic locations, and it's made accessible to multiple participants.

# [CHAPTER 6](#toc.xhtml#c06)

# [Blockchain Use Cases - Bitcoin, Ethereum, DeFi, and Tokenization](#toc.xhtml#c06)

# [Introduction](#toc.xhtml#s117a)

In the previous chapter, we covered some core concepts of traditional finance, as well as learned about Distributed Ledger Technology. Now, this chapter is all about some of the best and the most popular use cases of blockchain.

We start with two of the prime use cases of blockchain tech—the cryptocurrencies Bitcoin and Ethereum and their respective ecosystems. We witnessed the advent of cryptocurrencies back in 2008, which was subsequently followed by the Bitcoin whitepaper composed by Satoshi Nakamoto. These two events took the world of finance by storm. In this chapter, we are about to learn about the journey Bitcoin has had so far, as well as about Ethereum, which has been mislabeled as a rival to Bitcoin. We find out how these two cryptocurrencies are totally different from each other while also learning about their similarities.

Our next topic of discussion would be the decentralized finance (DeFi) movement and its growth. Ethereum is central in the DeFi space with its capabilities to support the creation and operation of various dApps (decentralized applications); therefore, DeFi is an integral point to cover when speaking of Ethereum.

In recent times, DeFi's growth has been accelerated—quite unexpectedly—by the global Covid-19 pandemic, as governments across the world have insisted upon the need for decentralized solutions, both in the financial sector and outside of it.

Blockchain's popular use cases also include tokenization and the very recent initiation of NFTs (non-fungible tokens). So finally, in this chapter, we also go through the procedure of tokenization, Ethereum's ERC20 token standard that has been dominating Initial Coin Offerings (ICOs), and then the unique concept of NFTs.

# [Structure](#toc.xhtml#s118a)

The following topics will be covered in this chapter:

*   **Part 1: Bitcoin and Ethereum** 
    *   Bitcoin: a history
    *   Ethereum: a history
    *   Bitcoin and Ethereum: a comparison
*   **Part 2: DeFi** 
    *   DeFi: a brief overview
    *   Growth of DeFi
    *   Use cases of DeFi and future outlook
*   **Part 3: Tokenization and NFTs** 
    *   Understanding tokenization  
        *   Types of assets that are tokenized
    *   ERC20 tokens explained  
        *   The need for ERC20 tokens
*   **What are NFTs?** 
    *   Working of non-fungible token trades
    *   Future of non-fungible tokens
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s119a)

This chapter is divided into three parts, each one covering different kinds of use cases of blockchain technology. When you aim to become a blockchain architect, it is crucial that you possess some knowledge of how the technology has already been used to build different types of platforms that support a varied range of functionalities. In this chapter, we intend to impart you with exactly that insight.

# [Part 1: Bitcoin and Ethereum](#toc.xhtml#s120a)

When it comes to use cases of blockchain, Bitcoin and Ethereum are two cryptocurrencies that are bound to come to your mind first. With vastly different objectives, both these ecosystems are built in widely different ways, and yet they share some basic likenesses. In this section, we explore both cryptocurrencies briefly and then stack them against each other to see their similarities and dissimilarities.

# [Bitcoin: a history](#toc.xhtml#s121a)

Bitcoin is a virtual currency, and it is the very first cryptocurrency that came about. A creator or group of creators using the pseudonym of Satoshi Nakamoto was behind the creation of Bitcoin. Bitcoin is purely a virtual phenomenon, open-source software based on blockchain technology.

Over the years, Bitcoin has become a successful, decentralized payment network, an asset class, and a store of value. Even as many more cryptocurrencies have been introduced in the years since Bitcoin's initiation, Bitcoin remains the biggest crypto worldwide by market capitalization, and its popularity is unmatched so far.

The Bitcoin network follows all the basics of blockchain: it is decentralized, so no central authority figure is needed to watch over the transactions made with bitcoin. It is distributed across a **Peer-To-Peer** (**P2P**) network of nodes.

Transactions on the Bitcoin blockchain are verified by said nodes and recorded on the Bitcoin blockchain, which functions as a distributed ledger, and every node holds a copy of that ledger. Bitcoin miners perform the act of gathering the transactions and putting them into blocks, which are then added to the chain. The miners are rewarded with a set amount of bitcoins for their efforts.

The security of the Bitcoin network is ensured by its trustless nature. As it is decentralized, all nodes keep the others in check. To carry out a hacking effort, over 51% of a network's nodes have to band up with a specific wrong consensus at the same time, which is very unlikely to happen. Further, cryptographic measures are, of course, in place to keep the Bitcoin blockchain safe. Bitcoin uses three cryptographic measures to ensure the security of transactions:

*   Hashing
*   A combination of the public and private key
*   Proof-of-Work consensus

All Bitcoin users are issued a private key (equivalent to your e-mail password), which then uses "*hashing"* to generate a public key (equivalent to the e-mail ID). Hashing involves processing a string of data through an algorithm to produce a unique number which will be the public key. It is impossible to reverse this process or use it to procure the private key of a user. Bitcoin uses SHA-256 for hashing all operations.

The public key can be freely given to people who want to send bitcoins to the users' wallet address (the public key is the wallet address). User can access their funds in a wallet only via their private key. If they lose their private key, they lose their bitcoins forever.

On the Bitcoin blockchain, a new block needs about 10 minutes to be added to the blockchain. Since all nodes have real-time records of all transactions happening on the Bitcoin blockchain, whenever a transaction occurs, the nodes cross-check the database to verify whether the conditions for the transaction are met, that is, whether the wallet contains enough bitcoin value to provide for the requested amount to be transferred to another wallet. This is then validated by most of the nodes to reach a consensus. Once the transaction is validated, it forms a part of the block (group of transactions) in the blockchain.

Bitcoin uses the PoW or Proof-of-Work consensus mechanism, which requires some nodes to perform Bitcoin mining to keep the network safe and running smoothly. Bitcoin mining is, as mentioned, the act of solving complex mathematical puzzles to add new blocks to the Bitcoin blockchain. These puzzles involve validating a batch of transactions and generating a hash every time a new block of transactions is added to the blockchain.

Understand it like this, Picture an assembly line and workers putting together batches of 20 into one box. After sealing the box, it is provided with a unique reference number which would be used to track its progress. Now, take this in the context of blockchain; miners receive a batch of bitcoin transactions that they need to validate. This validation involves finding the unique number or hash, which will be assigned to the block and by which the block will be represented within the blockchain.

Miners need special hardware to solve the said puzzles. The Bitcoin network's software also adjusts the difficulty levels for miners so as to limit the network to producing only one new block every 10 minutes on average, and keep the volume of transactions under control. For validating transactions, miners are rewarded with newly minted bitcoins. Miners put in their time and resources in the network, leaving less room for bad players who will not be interested in entering the network for want of expensive machines and resources.

As we discussed in the previous chapters, a currency gets value from the people accepting it as a mode of exchange. Similarly, the participants on the Bitcoin network use the bitcoins to transact among themselves in a peer-to-peer fashion. As the number of people on the network grows, so does its utility and value. Today thousands of e-commerce merchants accept bitcoins as payment.

Bitcoin is a deflationary cryptocurrency, and the total number of bitcoins that will ever be in supply has been capped at 21 million. The amount of bitcoins miners receive as the reward is cut in half every four years or so, as every 210,000 blocks get mined. This particular feature of the Bitcoin blockchain is known as "*halving"*. Bitcoin halving serves to manage the rate at which new bitcoin units are brought into circulation, boosts the crypto's **stock-to-flow ratio**, and lowers its inflation.

Bitcoin halving ensures that bitcoin units as a reward for Bitcoin mining will continue until the year 2140, and everything will stay as it is right now. However, once all Bitcoin is out in circulation, miners will still receive the network fees as an incentive for Bitcoin mining.

When Bitcoin was launched first in 2009, the amount of bitcoins miners received for creating a new block on the chan was 50 BTC. After the first Bitcoin halving in 2012, the reward per block became 25 BTC, which was then again halved to 12.5 bitcoins four years later in 2016.

The most recent Bitcoin halving took place on May 11, 2020, and as of 2021, the amount of Bitcoin miners receive for mining every block on the Bitcoin blockchain is 6.25 bitcoins. Please refer to the following figure:

![](images/Figure-6.1.jpg)

**Figure 6.1:** Bitcoin reward for mining after bitcoin halving during various years

# [Ethereum: a history](#toc.xhtml#s122a)

In terms of popularity and market cap, Ethereum is right next to Bitcoin, establishing itself as the second-largest cryptocurrency. Just like Bitcoin, Ethereum is also an open-source, decentralized, distributed ledger that allows users to record verified transactions.

Ethereum originated in July 2015, and the primary figures behind its creation are Joe Lubin- the founder of ConsenSys, and Vitalik Buterin, who also serves as the Ethereum CEO. The Ethereum blockchain has ETH or Ether as its native crypto coin and Solidity as its very own programming language.

Ethereum is at the core of the DeFi movement as of right now since it allows the simple and efficient creation of new decentralized applications (dApps) in fields such as financial products and services, business, and entertainment. Ethereum users can develop, publish, use, and monetize these dApps on the blockchain, using ETH as the mode of payment.

In fact, Ethereum was first created with the very intention of enabling developers to build smart contracts and decentralized applications that users can benefit from without answering to a centralized authority figure or fearing the frauds and hacking attacks associated with storing personal information over the internet. Smart contracts are self-executing contracts; that is, they execute themselves automatically when a set of predetermined conditions are met.

There is no demarcations regarding how many ETH can be in circulation in the long run. The number of ETHs being traded has already gotten past 100 million in the year 2018. The fees that users on the Ethereum blockchain pay to use the decentralized applications on the platform is called "gas"; the amount of gas used varies based on the amount of computational power that gets used for executing that smart contract.

Currently, the Ethereum blockchain is going through an upgrade to Ethereum 2.0. Due to the large number of dApps residing on it, Ethereum has been dealing with network congestion issues for a while now. Aside from its inability to scale up, the congestion problem has also caused the gas price to go significantly higher. In fact, as of early 2021, the median gas fee was reportedly over $10 per transaction on the Ethereum platform.

All these reasons compelled the Ethereum developers to decide on the upgrade. Ethereum 2.0, sometime in 2021–22, will shift from the previous **Proof-of-Work** (**PoW**) to a new **Proof-of-Stake** (**PoS**) consensus mechanism, aside from other significant changes. Please refer to the following figure:

![](images/Figure-6.2.jpg)

**Figure 6.2:** Interactions between various network components of the proposed Ethereum upgrade

# [Bitcoin and Ethereum: a comparison](#toc.xhtml#s123a)

Ethereum and Bitcoin are both use cases for blockchain technology, and the platforms have utilized the tech in quite different ways; therefore, there is no real reason for these two to be pitted against each other any more than they are put against any other blockchain-based platform.

However, it is mainly the popularity of Ethereum that brings about so much comparison, along with the fact that many crypto enthusiasts have labeled it an apt replacement for Bitcoin.

The basic differences between the two blockchain networks have been summarized in the following picture:

![](images/Figure-6.3.jpg)

**Figure 6.3:** Differences between Ethereum and Bitcoin network

At the very basic, Bitcoin and Ethereum do seem quite similar. They are both virtual currencies based upon blockchain technology: decentralized, distributed, and stretching across a peer-to-peer network of nodes. They both have operated with proof-of-work consensus mechanisms so far, even though Ethereum 2.0 will soon be changing over to a proof-of-stake system.

For both Ethereum and Bitcoin, the verification and confirmation of transactions performed on the respective blockchains require nodes throughout the network to be in concord. This is why both Bitcoin and Ethereum are slower than the majority of other blockchains out there when it comes to the processing of transactions.

Speaking of swiftness, though, Ethereum is still marginally faster than Bitcoin at processing transactions; where the Bitcoin blockchain can process only about 5–7 per second, Ethereum can take up to 10–15 transactions per second. Moreover, when Ethereum 2.0 is fully in business, we will very likely get to see the blockchain processing transactions lightning fast.

The Ethereum blockchain brought about the use of smart contracts (self-executing digital agreements that are concluded once all specified terms and conditions are met) and decentralized applications; thus, it is better using blockchain tech than Bitcoin has done since the beginning.

However, Ethereum does not yet have anything near the large ecosystem or the huge community of loyal followers. Bitcoin has been acquired, and therefore, Bitcoin rules the market. Bitcoin and Ethereum also differ regarding the hashing algorithm they run on—while Bitcoin has incorporated the SHA-256 algorithm, the one Ethereum uses is called Ethash.

Ethash is a hashing algorithm used to perform Proof of Work on the Ethereum blockchain. Ethash uses a combination of two cryptographic functions, namely, SHA-3 and Keccak. Ethash, unlike Bitcoin's SHA-256, is resistant to ASICs but can be used to verify and execute transactions quickly.

However, the primary and most important difference between Bitcoin and Ethereum is the objectives with which they were created. Satoshi Nakamoto introduced Bitcoin after the global financial crisis of 2008–2009 as an alternative to fiat currency and a store of value. But Ethereum never strived to be a cryptocurrency that will eventually replace traditional currency. Instead, Ethereum clearly states itself as a programmable blockchain platform that aims to aid the creation of decentralized applications and act as a marketplace for all sorts of decentralized products and services.

Much unlike Bitcoin, the Ethereum blockchain was not created with the sole purpose to elevate ETH as a cryptocurrency. In fact, ETH is mainly just a native currency built to be exchanged between users and applications on the Ethereum platform. So, Ethereum and Bitcoin's ambitions are broadly different at the very core.

Bitcoin and Ethereum may both be virtual currencies, but while Bitcoin is gunning to be a mainstream medium of exchange, Ethereum does not intend to be an alternative currency. Rather, the blockchain's goal is to facilitate the operations of smart contracts and decentralized applications.

# [Part 2: DeFi](#toc.xhtml#s124a)

The DeFi, or decentralized finance movement, came about as a means to carry out the mission to bank the unbanked or hard-to-bank population across the globe. Since the initiation of DeFi, 2020 was the year when DeFi was seen at its best so far, with a slew of brand new, innovative projects, and an astonishing TVL (total value locked). In quarter three of 2020, the TVL in DeFi climbed over $11 billion, finishing the year at a TVL of $16 billion.

As a blockchain architect, you would be expected to possess in-depth knowledge about the fundamentals of DeFi and its use cases. In this section, we give you exactly that.

# [DeFi: a brief overview](#toc.xhtml#s125a)

Decentralized finance consists of all sorts of decentralized financial products and services built with the help of blockchain technology, usually governed by their communities of users and developers. Many name Bitcoin as the first known use case of DeFi, as it was developed as a decentralized monetary system. However, since then, many advanced and more decentralized platforms have emerged within the DeFi space that allows users to perform a number of actions other than sending funds to one another.

The Ethereum blockchain is intricately linked with the concept of DeFi. Even the term "DeFi" itself was created in the summer of 2018 when a Telegram chat was taking place between Ethereum developers and entrepreneurs who were discussing a name for the revolutionary movement brought about by the open financial applications being built on top of the Ethereum blockchain. The term DeFi was chosen due to the fact that it sounds like "defy".

The goal of decentralized finance is to provide an alternative, decentralized financial solutions to the general populace, so they can have the maximum possible power over their finances. Most decentralized applications are built with the objective of refurbishing traditional financial goods, services, and institutions, namely, banks and exchange platforms.

The range of services DeFi has offered so far includes decentralized takes on concepts of traditional finance such as payments, lending and borrowing, money issuance, insurance, asset management, and so on, and wholly new financial services like AMMs or Automated Market Makers, staking, and yield farming.

# [The growth of DeFi](#toc.xhtml#s126a)

Since the summer of 2020, DeFi has seen a significant amount of growth, that too amidst a global pandemic. This growth has been attributed, at least to some extent, to the Ethereum-based DeFi lending platform Compound and the launch of their native governance token COMP in the May of 2020. The compound provides COMP tokens to its liquidity providers (crypto holders who act as lenders on the platform).

Compound brought the concept of yield farming (the act of providing liquidity to exchange to maximize governance token rewards) to the mainstream with the introduction of COMP and another platform called Yearn.finance followed suit with their native token YFI. These platforms gave the decentralized finance movement as a whole the boost it needed.

The TVL or Total Value Locked figure is typically one of the most important and accurate indicators to figure out the growth rate of decentralized finance. TVL refers to the total value of the funds users across the world who have locked up on various DeFi platforms. Notably, in early 2020, the TVL in DeFi was around $1 billion, but by the middle of 2021, the TVL had already gone over $70 billion. Analysts have noted that this extent of consumer interest has not been witnessed within the crypto world since the Bitcoin hype back in 2017.

Another factor to have fueled the growth of DeFi would be stablecoins, which are virtual currencies backed by fiat currency, valued assets such as precious metals or even cryptocurrencies. The value of a stablecoin is tied to its underlying asset; for instance, Tether or the USDT is backed by the US dollar, so 1 USDT= $1. Stablecoins were created to serve as a bridge connecting the growing virtual economy and traditional finance, and they are far less volatile than the average cryptocurrency.

Stablecoins are playing an integral role in the DeFi space, accelerating the growth of decentralized finance in the process. Many decentralized exchanges use stablecoins as the quoted currency, so they can make trading more convenient for users. Further, DeFi applications like lending platforms use stablecoins to manage the volatility in crypto markets and assure investors.

# [Use cases of DeFi, and future outlook](#toc.xhtml#s127a)

DeFi is still in its earliest stages, and it is needless to say that the movement has a long road ahead of it. However, we have already witnessed some pretty prominent use cases of DeFi. Following are some of these use cases:

*   **Decentralized trading:** One of the first things decentralized finance introduced was a decentralized way of trading funds or assets for the general populace. Across decentralized exchange platforms and decentralized marketplaces, many, many trades happen within the DeFi sector. These trades include simple token exchanges to spot trading to derivatives trading to token swaps, among other trades.  
    *   Spot Trading refers to buying and selling cryptocurrencies at real-time prices with a profit motive.
    *   Derivatives trading involves an agreement between a buyer and a seller to buy/sell a particular cryptocurrency at a predecided price on a future date. The parties do not actually own the underlying cryptocurrency in the agreement.
    *   Token swaps involve the direct exchange of a certain amount of cryptocurrency for another cryptocurrency between two users.
*   **Decentralized Payments:** Peer-to-peer payments are a basic quality of the blockchain tech, and therefore, it is obviously one of the primary use cases of decentralized finance. Decentralized payment networks allow users to trade directly amongst themselves without requiring any intermediary to intervene. DeFi payment solutions can create an easily accessible, convenient financial system to exclusively help the unbanked or underbanked population across the globe.
*   **Decentralized Exchange Platforms (DEX):** Decentralized exchange protocols are one of the most popular use cases of decentralized finance so far. Decentralized exchanges are essentially cryptocurrency exchange platforms that let users buy or sell their crypto assets and perform peer-to-peer transactions between themselves; like all aspects of decentralized finance, decentralized exchanges allow users to have full control over their funds and have no centralized entity to answer to.  
    *   Decentralized exchange platforms provide an increased rate of liquidity (the ease with which tokens can be swapped for other tokens in a cryptocurrency market) and also lower the threats of market manipulation (the act of artificially controlling or affecting the prices of cryptocurrencies in the market). Plus, some decentralized exchange protocols might also allow you to tokenize physical assets you own and exchange those tokens; that way, the trades are quicker and much more secure, as opposed to real-world trades.
*   **Decentralized lending and borrowing platforms:** This is one of the most widely sought-out use cases of DeFi. DeFi lending platforms allow crypto holders to act as lenders and give out loans to individuals or organizations in a trustless fashion without needing a centralized authority, given they stake equivalent collateral first, of course. Lenders get to generate an income by earning interest in the form of crypto on the funds they have lent out.  
    *   Aside from the fact that DeFi lending and borrowing platforms require no third-party interference, they come with several other advantages over traditional lending and borrowing organizations. For one, DeFi lending protocols are far easier to access for both parties. Due to being blockchain-based, decentralized lending and borrowing platforms also allow instant fund settlements, increased transparency regarding the fund flow, decreased threats, and overall more flexibility in both lending and borrowing. Interest rates are usually more attractive than traditional lending, and the entry barrier for borrowing is lower too.
    *   The Ethereum-based DeFi lending protocol Compound is a really good example of this sort of platform.
*   **Decentralized asset management:** When it comes to asset management as part of traditional finance, it involves a long and overly complicated process of finding the best financial institutions, strategizing and dividing your assets for portfolio diversification, and then tracking all those investments and trades performed across several platforms. However, decentralized asset management comes with a range of instruments to make the whole thing easier for you; the tools include digital wallets and apps for handling the many assets on behalf of the user, which involves storing, buying, selling, and moving assets from one system to another should the need arise, and even earning and storing the interest on the deposited assets.
*   **Decentralized insurance:** Within the crypto space, users have to deal with many vulnerabilities, like smart contract breaches, hacking of personal information and money, and compromised private keys. Plus, since blockchains are immutable, it is usually quite difficult to reverse any losses suffered when it comes to cryptocurrencies. This is where decentralized insurance comes in. Decentralized insurance gives crypto users maximized safety by providing insurance on crypto assets, smart contracts, or their funds overall, and also attracts more and more users to DeFi and crypto in general.

Further use cases of DeFi include synthetic assets, DeFi derivatives, tokenization (more on that later), decentralized marketplaces, and more.

*   Synthetic assets are derivatives that are tokenized as assets/tokens on a blockchain.
*   Tokenization refers to the process whereby anything of value, whether a real-world asset, stock, or real estate, is converted into a digital token/s, representing the asset's value over a blockchain.
*   Decentralized marketplaces allow buyers, sellers, and other market players to deal directly with each other without the requirement of a middleman or a central authority.

The growth of DeFi so far really says a lot about all the possibilities of crypto assets and decentralized platforms, and above all, blockchain tech should be implemented in mainstream applications. The decentralized finance movement is creating a foundation for blockchain-based, permissionless, decentralized financial services on par with the emerging digital economy.

As the DeFi space continues coming up with incredibly innovative products, token models, and governance structures with every passing day, it is safe to say that decentralized finance will keep seeing immense enhancement in the coming times.

# [Part 3: Tokenization and NFTs](#toc.xhtml#s128a)

The blockchain technology's use cases include tokenization and then NFTs, which have become one of the latest hype trains within the crypto world. In this section, we take a look at what tokenization is, Ethereum's ERC20 token standard, and finally, NFTs.

# [Understanding tokenization](#toc.xhtml#s129a)

Tokenization is the process through which various assets are turned into virtual tokens to be stored, recorded, and traded on a blockchain. The token created through tokenization stands for the value of the underlying asset and represents the asset on the blockchain. For example, you can convert a valuable painting into a digital token to trade it with someone halfway across the world through a blockchain platform; this way, your asset remains safe, and the trade is conducted quickly.

You might wonder why tokenization is even necessary. Well, the most valuable assets in the world are quite difficult to divide into small shares or transfer from one place to another. So, traders exchange documents representing those very assets in the real world.

Now, the problem with papers is that they involve a lengthy process of carrying out legal agreements, they can be lost easily, and they can prove to be extremely hard and time-consuming to track. Tokenization does away with this whole procedure, concluding the trade swiftly and keeping updated records that can be accessed whenever the need arises.

# [Types of assets that are tokenized](#toc.xhtml#s130a)

Theoretically, there are endless scopes for the tokenization of all sorts of assets. However, assets for tokenization can still be classified into three broad categories, which are the following:

*   **Intangible assets:** This category includes assets that exist only because of the operation of law and not as tangible objects. For instance, copyrights, carbon credits, and patents are all intangible assets. When it comes to tokenizing these assets, you have to ensure that the blockchain system's model of the transfer of assets is on the same page as the transfer model for the same in the real world, and you also might have to deal with jurisdictional distinctions. However, intangible assets are still far easier to tokenize than other assets since you do not need to worry about storage or shipment.
*   **Fungible assets:** The definition of fungible assets suggests that these are assets that can be exchanged for an identical asset. Examples of fungible assets include grain, gold, any other precious metal, and so on. Fungible assets are quite easy to tokenize as they can be divided into smaller units with ease, and they can also be grouped together so one single token can represent a collection of them, such as a pile of gold.
*   **Non-Fungible assets:** Non-fungible assets, as opposed to fungible assets, cannot be interchanged with another identical item because they are one of their kind. Non-fungible assets include paintings, sculptures, real estate, and so on. It is understandable that non-fungible assets cannot be divided into smaller pieces in the real world; however, tokenization makes that possible. Through tokenization, non-fungible assets can be broken down into digital shares that can be traded entirely or limitedly. Therefore, tokenization allows fractional ownership of non-fungible assets, which can prove to be quite difficult in the real world.

# [ERC20 tokens explained](#toc.xhtml#s131a)

Now that we know about the concept of tokenization, we will be getting to know in detail about Ethereum's ERC20 tokens. The ERC20 tokens are exclusive to Ethereum, and they follow the ERC20 token standard of the platform.

The ERC20 token standard lays down a set of regulations for all Ethereum tokens to follow, so they can be easily transferred and traded. The standard also regulates things like how the ERC20 tokens are to be traded, how the transactions are approved, how users can have access to information about a specific token, and the maximum supply of a particular token that will ever be in circulation. The ERC20 token standard is accepted as the general technical standard on Ethereum, and it is used by every smart contract on Ethereum for new token integration. You can essentially call ERC20 the universal language for all the crypto tokens on the Ethereum blockchain.

As mentioned before, smart contracts are used on the Ethereum blockchain to generate new ERC20 tokens and also to allow those tokens to be transferred and record their balances of them in an account. When it comes to the features of ERC20 tokens, they are not very different from Bitcoin or any of the well-known altcoins. ERC20 tokens are also a blockchain-based digital currency that holds a set value and can be swapped out between traders or stored in crypto wallets. The only real difference is the fact that the ERC20 tokens are issued and used only within the Ethereum ecosystem.

# [The need for ERC20 tokens](#toc.xhtml#s132a)

First, the ERC20 token standard renders the jobs of project developers and crypto investors alike much easier. This is because before a specific standard for Ethereum tokens was put in place, developers were bound to be using various terminologies in their codes, which inevitably reduced the compatibility between different blockchain platforms. This also means that the various cryptocurrency exchange platforms and wallets also had to constantly update their systems to accommodate the codes for as many crypto tokens as possible and for new tokens to be added to the platforms. However, with ERC20, the new Ethereum tokens are all compatible with every project within the Ethereum ecosystem.

Moreover, ERC20 tokens allow developers on Ethereum to visualize how new tokens they introduce to the Ethereum blockchain will perform, and overall makes it easy for developers to create new Ethereum tokens. Indeed, the ERC20 token standard plays no small part in cementing Ethereum's position as the most popular blockchain platform among dApp developers.

As of the middle of 2021, there are already nearly 400,000 ERC20 tokens on the Ethereum blockchain. Some of the more popular ones include MakerDAO (MKR), EOS (EOS), Tron (TRX), and the **Basic Attention Token** (**BAT**).

# [What are NFTs?](#toc.xhtml#s133a)

Finally, it is time to get into the concept of NFT, which is the acronym for "*non-fungible token*". Non-fungible tokens, as you can probably guess, are the tokenized form of non-fungible assets.

NFTs are indivisible and unique crypto tokens, and they are not interchangeable with any other crypto token. Each NFT carries a unique, computerized code that establishes it as the one and only token with that specific virtual identity. An NFT cannot be mistaken for another, and neither can an NFT be divided into a number of units. NFT might also have additional characteristics to differentiate it from others, such as metadata, visuals, and so on. The value of an NFT is decided on the basis of the demand for its unique characteristics among the traders.

Making a non-fungible asset into an NFT is a really good way to prove the authenticity and origin of rare assets, whether virtual or real. NFTs open up a broad scope for creating and exchanging digital assets.

Most non-fungible tokens follow the ERC721 Token Standard, which discusses a specific set of features each NFT should have. However, it does not limit the unique attributes a developer might want to put into their NFT.

So far, we have seen a variety of assets being turned into NFTs, including music and videos, original artworks, collectibles, trading cards, domain names, and even tweets. Twitter co-founder Jack Dorsey's very first tweet sold as an NFT in March 2021 for $2.9 million. Popular NFT crypto projects include CryptoKitties, Blockchain Heroes, and Prospectors.

# [Working of non-fungible token trades](#toc.xhtml#s134a)

Just like any blockchain transaction, an NFT transaction is recorded into its respective blockchain ledger. The entry consists of an address to the NFT so as to document the precise ownership of that particular token.

When an NFT is sent across from Trader A to Trader B, the token code is also attributed to B. Therefore, you can confirm the ownership of an NFT by checking the blockchain ledger. The blockchain immutably records the transfer of ownership from A to B, disallowing A, the original holder of the NFT, to make any more use of the NFT now that the asset's ownership has been transferred. The owners of an NFT can add metadata or any other information regarding the underlying asset in the NFT. The additional data can be in a variety of formats, such as JPG, MP3, MP4, GIFs, and more.

# [Future of non-fungible tokens](#toc.xhtml#s135a)

In 2021, NFT presented itself as a prime growth sector within the blockchain space, and it has been attracting a great number of users to the DeFi space too. Even though it was initially mostly used for gaming, the use cases of NFTs are gradually expanding. Many projects within the crypto space and mainstream organizations alike are looking into the possibilities of using NFTs for identifying, certifying, and granting fractional ownership of different kinds of assets. Judging by all that, we can safely say that NFTs are just getting started, and there are even brighter times ahead for these particular tokens.

# [Conclusion](#toc.xhtml#s136a)

In this chapter, we learned about varied use cases of blockchain tech. Starting with two popular blockchain-based cryptocurrencies, we explored how they have used the same technology in both similar and vastly different ways. We learned about the growth and use cases of DeFi, and we found out about tokenization and two particular kinds of tokens within the blockchain space. We hope this chapter has been able to add to your knowledge of all these different use cases of blockchain tech.

In the upcoming chapter, we will learn about some further use cases of blockchain.

# [Questions](#toc.xhtml#s137a)

1.  **What is Bitcoin halving?**
    
    The process of halving the payout for miners for mining a new block
    
2.  **What will be the miners' incentive to continue mining Bitcoin once all coins are released into circulation?**
    
    They can still receive network fees as an incentive.
    
3.  **Why was Ethereum created in the first place?**
    
    Ethereum was created to allow the simple and efficient creation of new decentralized applications (dApps) in fields like financial products and services, business, and entertainment.
    
4.  **Why did Ethereum 2.0 come about?**
    
    Due to the large number of dApps, Ethereum has been dealing with network congestion issues. To solve this, Etherium 2.0 came, which will use a new Proof of Stake algorithm in place of the Proof of Work algorithm.
    
5.  **Why are Bitcoin and Ethereum compared so frequently?**
    
    Popularity of Ethereum
    
6.  **What is the basic difference between the Bitcoin and Ethereum blockchains?**
    
    Basic difference between Bitcoin and Ethereum is the objectives with which they were created. Bitcoin was created after the global financial crisis of 2008–2009 as an alternative to fiat currency and a store of value. But Ethereum never strived to be a cryptocurrency that will eventually replace traditional currency
    
7.  **What is DeFi?**
    
    DeFi consists of all sorts of decentralized financial products and services built with the help of the blockchain technology
    
8.  **What are some use cases of decentralized finance we have seen so far?**
    
    Decentralized trading, payments, exchanges, and so on.
    
9.  **What is tokenization?**
    
    Tokenization is the process through which various assets are turned into virtual tokens to be stored, recorded, and traded on a blockchain.
    
10.  **What are the different kinds of assets that can be tokenized?**
     
     Intangible, Fungible, and non-fungible assets.
     
11.  **What are ERC20 tokens?**
     
     The ERC20 token standard lays down a set of regulations for all Ethereum tokens to follow, so they can be easily transferred and traded.
     
12.  **What are some benefits of the ERC20 token standard?**
     
     With ERC20, the new Ethereum tokens are all compatible with every project within the Ethereum ecosystem. Also, it makes it easy for developers to create new tokens on Ethereum.
     
13.  **What is an NFT?**
     
     NFTs are tokenized forms of non-fungible assets. They are indivisible and unique crypto tokens, and they are not interchangeable with any other crypto token.
     

# [Key terms](#toc.xhtml#s138a)

*   **DeFi:** The decentralized finance movement is a mission to bank the unbanked or hard-to-bank population across the globe. DeFi consists of all sorts of decentralized financial products and services built with the help of the blockchain technology, usually governed by their communities of users and developers.
*   **Tokenization:** Tokenization is the process through which various assets are turned into virtual tokens to be stored, recorded, and traded on a blockchain.
*   **NFT:** NFTs or non-fungible tokens are the tokenized form of non-fungible assets. They are indivisible and unique crypto tokens, and they are not interchangeable with any other crypto token.

# [CHAPTER 7](#toc.xhtml#c07)

# [Other Use Cases](#toc.xhtml#c07)

# [Introduction](#toc.xhtml#s139a)

The previous chapter was all about the use cases of Bitcoin and Ethereum and tokenization and NFTs. In this chapter, we will look at various other use cases of blockchain, which, if implemented in the right way, can potentially change the face of the world. From individuals building their own solutions to enterprises leveraging blockchain technology, everyone is on board with using blockchain to transform some of the world's biggest challenges into humanity's biggest triumphs.

# [Structure](#toc.xhtml#s140a)

The following topics will be covered in this chapter:

*   Blockchain use cases in finance  
    *   Cross-border payments
    *   Lending platforms
    *   Fundraising and capital markets
*   Blockchain use cases for governments  
    *   Digital identity management
    *   Regulation
    *   Administration
    *   Reducing corruption
    *   Eliminating voter fraud
*   Blockchain for businesses  
    *   Supply chain management
    *   Internet-of-Things (IoT)
    *   Automation of tasks with smart contracts
    *   Real estate
    *   Retail operations
    *   Inventory management
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s141a)

To better comprehend why blockchain technology is nothing short of a revolution, we need to look beyond its original intended scope as the underpinning technology for cryptocurrencies. In this chapter, we hope to provide you with that insight by offering various real-world examples of how blockchain technology may be used to disrupt industries.

# [Blockchain for good](#toc.xhtml#s142a)

Given how many people believe that the applications of blockchain tech are mostly limited to Bitcoin, it is critical to recognize that blockchain applications extend far beyond cryptocurrency and Bitcoin. With its ability to increase transparency and accountability while saving organizations time and money, this revolutionary technology has a significant impact across many industries.

The promise of a decentralized, public, yet highly secure ledger for recording transactions is the major driving force behind blockchain and its potential to become one of the most revolutionary technologies in the recent decade. A blockchain network's inherent immutability, or inability to change data, makes the technology a viable alternative for enterprises attempting to build a trustworthy environment for their business ecosystems. Smart contracts, which are digital agreements between numerous parties that require authentication and approval at every level to ensure transparency and trustworthiness among permitted unknown parties, are also enabled by this decentralized paradigm.

Let us now look at some of the most prominent blockchain use cases for businesses, institutions, and governments.

# [Blockchain use cases in finance](#toc.xhtml#s143a)

By 2022, the financial services industry is expected to be worth $2.6 trillion. Every day, the global financial system handles trillions of dollars and provides services to about a billion people. With such tremendous peaks come a slew of issues that the finance industry has been grappling with for a long time.

In fact, these difficulties can also be considered the primary cause of the large amounts of losses that the sector experiences each year, ranging from the high expense of various stakeholders to delays, needless paperwork, and data breaches. Even today, most financial services in the world are centralized. Financial data is typically housed in centralized systems and must pass through several intermediaries, including the front office, back office, and other departments.

With data protection exclusively reliant on intermediaries and database security, the system is severely lacking in transparency. And even if databases are well-protected, there is still a significant risk of data leaks and server hacking. Moreover, the lack of transparency in the system also raises concerns about security because no one knows what is going on until something goes wrong or data is compromised.

Thanks to the immutability of the blockchain, altering data is practically impossible. As a result, all data in the system can be guaranteed to be secure, authentic, and correct. In addition, the blockchain system typically has two keys: a public key and a private key. While the public key is accessible to all network users, the private key is only shared among the parties involved in the transaction. This guarantees that the system maintains transparency while simultaneously safeguarding the confidential financial information of stakeholders.

Blockchain tech can also reduce risks in the financial services sector, especially credit risk due to information asymmetry, distrust of intermediaries, and the counterparty not being able to meet its obligations.

Let us now move on to the various use cases of blockchain in the financial services sector.

# [Cross-border payments](#toc.xhtml#s144a)

According to the World Bank, cross-border transactions are still one of the most difficult consumer transactions, with long processing delays, infamously high fees, and a concerning lack of transparency. Many of the problems with traditional cross-border payments emerge as a result of the large number of intermediaries engaged in transaction processing. Each extra intermediary raises the processing charge, the number of failure points, and the chance of fraud somewhere along the payment stream. Over the last decade, the G20 nations have prioritized reducing the cost of cross-border remittances, and a payment system based on blockchain appears to be a potential solution to achieve this.

Blockchain technology has a lot of potential for cross-border payments since it employs encrypted distributed ledgers to allow real-time transaction verification without the need for intermediaries like correspondent banks or other third parties.

# [Lending platforms](#toc.xhtml#s145a)

Blockchain technology has replaced the need for intermediaries, which traditionally created a trust and enabled transactions in financial systems. Thanks to blockchain in finance, borrowers can now directly negotiate the rate of interest, installments, and duration of the transaction with lenders with the help of immutable smart contracts. Smart contracts essentially simplify loan operations by allowing for real-time document verification, streamlined credit prediction, and automated funds transfer. Please refer to the following figure:

![](images/Figure-7.1.jpg)

**Figure 7.1:** How DeFi lending platforms transact crypto loans

People can also receive faster mortgages since the blockchain will facilitate the streamlining of mortgage lending by serving as a single, decentralized point of document access on which signatures can be collected, thereby reducing the time and expenses associated with paper-based methods. The blockchain, acting as a unified database of financial records, promises to simplify the loan verification, and approval process.

Blockchain-enabled platforms may also aid in the expansion of the network of lenders and borrowers in different regions of the world, allowing for more competitive lending rates in a transparent, efficient environment with fewer fees and intermediaries. Blockchain tech can also be used to encourage the adoption of crypto-backed fiat loans, reduce mortgage fraud, and develop accurate and transparent credit profiles.

# [Fundraising](#toc.xhtml#s146a)

Fundraising is one of the most challenging activities in the financial sector because it involves a lengthy procedure that includes entrepreneur collaboration, participation in extended meetings with partners, and hours-long equity and valuation negotiations. Please refer to the following figure:

![](images/Figure-7.2.jpg)

**Figure 7.2:** The process of fundraising via a blockchain

By speeding up processes and introducing alternatives to conventional fundraising, blockchain has decreased the pain points in fundraising through solutions such as **Equity Token Offerings** (**ETOs**), **Initial Exchange Offerings** (**IEOs**), and **Security Token Offerings** (**STOs**).

ETOs are events during which companies offer equity tokens, representing equity or stake in the company, for sale to investors.

IEOs are facilitated by a crypto exchange and involve the exchange overseeing the sale of tokens by a verified crypto project to investors interested in the project.

STOs are tokenized IPOs or public sales where security tokens, or coins representing the value of an external asset or stake in a company, are sold to investors. Security tokens are digital representations of stocks, bonds, and equities.

# [Capital markets](#toc.xhtml#s147a)

Blockchain enables easier, cheaper, and faster access to funding in capital markets. It lowers the barriers to the issuance and allows peer-to-peer trading, as well as faster and more transparent settlement, lowers costs, lowers counterparty risks, and eases auditing and compliance. It also allows for a consolidated audit trail and general operational improvements.

These are only some of the major applications of blockchain tech in the finance sector, and there is a lot more that blockchain can do in finance to automate processes and bring efficiency. We will now look at the various use cases of blockchain for governments.

# [Blockchain use cases for governments](#toc.xhtml#s148a)

The adoption of blockchain by governments can be viewed from the perspectives of regulators, consumers, and developers. In some cases, governments may be interested in monitoring how blockchains are used, as in the case of cryptocurrencies. In other cases, governments and public sector organizations may use blockchain technology to move away from inefficient centralized systems.

Just like several other large organizations, governments worldwide also find it difficult to coordinate processes across disparate stakeholders. However, governments are required to give greater transparency, impartiality, and accountability to the public than most other institutions. Data management is crucial to success in these endeavors, particularly in the digital age. Regrettably, traditional centralized data management systems are inadequate to tackle the issues that governments today face. Data security is compromised by the traditional client-server approach, and transparency is difficult to achieve when government databases are centralized. As a result, operations become slow, inefficient, and ambiguous.

Because current methods are insecure and expensive, blockchain networks can provide more secure, adaptive, and cost-effective alternatives. There is no denying that the future is digital, and a blockchain-based digital government can safeguard data, streamline procedures, eliminate fraud, waste, and abuse while also boosting trust and accountability. It will also help avoid a single point of failure and safeguard public and government data.

The distributed ledger format can be leveraged to support an array of government and public sector applications, including identity management, regulation, administration, reducing corruption, and eliminating voter fraud.

Let us look at how they are implemented.

# [Digital identity management](#toc.xhtml#s149a)

Identity management is a critical component of government services; however, traditional data management technologies have fallen short of providing a secure, easily accessible, and updateable identity. Identity management based on blockchain technology provides citizens with a self-sovereign identity, where citizens have granular control over their ID, and the information contained within it is instantly verifiable. Please refer to the following figure:

![](images/Figure-7.3.jpg)

**Figure 7.3:** Universal identity over a blockchain grants users complete control over their personal information

Many more initiatives are built on top of a blockchain-based self-sovereign digital ID, including:

*   **Verification of academic credentials**: Fake academic credentials are quite easy to fabricate in today's society; verification of the credential by the issuer is, therefore, essential. Typically, verification of academic credentials involves both the candidate and the certificate issuer, and the process might take days or weeks. This issue can be solved by storing digital certificates on the blockchain. Transactions on the blockchain platform are immutable and publicly verifiable, and blockchain assets can be used to create digital certificates that are easy to verify and anti-counterfeit. 
    
    By automating paperwork transfers and facilitating smoother degree certifications, blockchain also makes it easier to transfer schools and study abroad.
    
*   **Electronic Health Records** (**EHRs**): Electronic health records allow patients to manage and share their health records to easily access healthcare services and prescriptions from wherever they are. A blockchain-based EHR may also support the following uses:  
    *   Access to healthcare without restriction
    *   Elimination of redundant onboarding tests and procedures
    *   Easy screening of digital prescriptions for possible adverse reactions
    *   Personalized healthcare
    *   Citizens taking ownership of their health data
    *   Automated payments for healthcare providers and vendors.
*   **Streamlined KYC**: KYC procedures are typically not only time-consuming and difficult, but they also differ from one institution to the next. On a basic level, routine operations like opening a bank account or transferring payments necessitate meeting specific criteria, and the burden of ensuring that you do so is entirely on the institutions providing the services. In addition, current KYC methods rely on intermediaries to authenticate user identity, which adds another layer of data sharing and risk. This archaic approach may be addressed with trustless blockchain technology, which allows users to authenticate their identity securely while still maintaining control over their data.

# [Regulation](#toc.xhtml#s150a)

The challenge of enforcing regulations is pretty huge for governments all over the world. The inadequacy of existing systems in managing the data required for both enforcement and compliance with regulations is a large part of the problem. In this situation, blockchain-based distributed ledgers can help to expedite regulation and improve response capacity. The following are some examples of industries that could benefit from blockchain-based regulation:

*   Aviation parts
*   Pharmaceuticals
*   Medical equipment
*   Securities
*   Food supply

# [Administration](#toc.xhtml#s151a)

From pension systems to health care, education, defense, and government-managed programs typically require coordination between multiple parties and the protection of sensitive data. With blockchain-supported administration systems, participants can coordinate in real-time, allowing for transparency in more than one way. Here are some areas in government administration where blockchain solutions can be effectively implemented:

*   Efficient management of government contracts
*   Administration of sovereign wealth funds
*   Pension administration

# [Reducing corruption](#toc.xhtml#s152a)

It is no secret that the public is never given complete facts on how government funds are spent. However, we may trace what happens to these funds if they are released via a blockchain, and the transactions on the blockchain are made available to the public. We can also learn how these funds are put to use.

# [Eliminating voter fraud](#toc.xhtml#s153a)

Blockchain technology has the potential to make voting more accessible while also increasing security. Every democratic government faces the issue of counting votes in a fast, secure, and transparent manner. In this case, blockchain can help voters by increasing transparency and immutability during the collation period. Please refer to the following figure:

![](images/Figure-7.4.jpg)

**Figure 7.4:** How a blockchain voting system differed from a traditional voting system

Hackers would stand no chance against blockchain technology since they could not be able to affect other nodes even if they gained access to the terminal. Each vote would be associated with a single ID, and because creating a false ID in a way that it goes unidentifiable would be impossible, government employees would be able to tally votes more swiftly and effectively.

Let us now move on to some of the enterprise use cases of blockchain.

# [Blockchain for businesses](#toc.xhtml#s154a)

Blockchain provides businesses with a secure, immutable, and distributed ledger system. Through its innovative safety methodology, consumers can take greater control over their own information, leading to greater fraud protection. Additionally, the technology can provide businesses with significant cost savings by reducing transaction times and costs while improving accuracy, transparency, reliability, accountability, and security in a digital marketplace.

# [Supply chain management](#toc.xhtml#s155a)

Digitizing physical assets can help organizations create a decentralized, immutable record of all transactions, making it possible to track assets from production to delivery. Both businesses and consumers benefit from this increased supply chain transparency. By decreasing or eliminating the impact of counterfeit items, blockchain may help organizations understand how ingredients and completed goods are passed through each subcontractor, lowering profit losses from counterfeit and grey market transactions and increasing confidence in end-market consumers. Please refer to the following figure:

![](images/Figure-7.5.jpg)

**Figure 7.5:** How supply chain management takes place over a blockchain

Because blockchain gives all participants in a supply chain access to the same information, businesses can maintain more control over outsourced contract manufacturing. Less time can be spent confirming data, and more time can be spent delivering goods and services and improving quality.

Finally, by providing an effective audit of supply chain data, blockchain can also reduce administrative operations and decrease expenses. Processes needing manual compliance checks, which presently take weeks, can be sped up using a distributed ledger that stores all essential data.

# [Internet-of-Things (IoT)](#toc.xhtml#s156a)

The **Internet of Things** (**IoT**) provides organizations with numerous chances to execute smart operations. Given how every device around us now has sensors and is constantly transmitting data to the cloud, merging blockchain and IoT can help to improve the efficiency of systems and processes.

Here are a few examples of how merging IoT and Blockchain can greatly influence various industries.

*   **Automotive industry**: The automotive industry can use IoT-enabled sensors to produce fully automated vehicles. It can also integrate IoT solutions to allow multiple users to easily and quickly exchange critical information.
*   **Smart homes**: Smart IoT-enabled devices are playing an increasingly important part in our daily lives. However, the typical centralized way to exchange data collected by IoT devices is not secure. By addressing major security concerns and eliminating the centralized infrastructure, blockchain has the potential to take smart homes to the next level.
*   **Pharmaceutical industry**: The dangers of counterfeit drugs in the pharmaceutical industry are getting worse by the day. The transparent and traceable characteristics of blockchain technology can aid in monitoring drug shipments from the point of origin to the point of destination in the supply chain and reducing counterfeiting.
*   **Agriculture**: The combination of blockchain and IoT can completely transform the food production industry, from farms to grocery stores to individual households. Installing IoT sensors in farms and transferring the data straight to the blockchain can also improve the food supply chain.

# [Automation of tasks with smart contracts](#toc.xhtml#s157a)

Smart contracts simplify corporate tasks and save capital (and other resources) by eliminating the need for intermediaries. Smart contracts on the blockchain can be implemented without the need for third-party approval, which can eliminate human error. Bill payments, financial trades such as stocks and bonds, land title transfers, and voting rights are just a few examples of smart contract applications.

# [Real estate](#toc.xhtml#s158a)

Real estate is a fast-growing industry, but centralization is one of its many drawbacks. Due to the amount of documentation involved, real estate is a time-consuming procedure with no reliable means to check documents or determine whether or not someone owns the property. Please refer to the following figure:

![](images/Figure-7.6.jpg)

**Figure 7.6:** Property deeds stored in smart contracts over Ethereum in a real estate transaction

Accurate land titles and deed records, tokenization, capital and asset management, investor and tenant identities, real-time accounting, and leasing and payments are some of the use cases of blockchain in real estate.

# [Retail operations](#toc.xhtml#s159a)

Many of the difficulties that retailers face today are addressed by blockchain business applications. Here are some instances of how blockchain might be used in retail to improve procedures and boost customer loyalty.

*   Ensure a transparent supply chain for the customer
*   Offer cryptocurrency payments
*   Share browsing and purchase data to improve customer identity
*   Enhance the process of obtaining tax refunds from retail purchases
*   Reduce cyber-hacking

# [Inventory management](#toc.xhtml#s160a)

Traditional inventory management relies on either a reactive approach, in which replenishments are ordered once inventory is exhausted, or a predictive model, in which inventory is forecasted before it runs out. With blockchain, however, warehouses, manufacturers, suppliers, production sites, distribution centers, and retail partners can all link to each other through a permanent record of transactions where all records are saved and made available to everyone on the network.

Such degrees of transparency allow manufacturers to better manage product origins and track demand at the consumer level in real-time, thereby allowing them to estimate demand and schedule manufacturing and replenishment correctly. Because blockchain-based warehouse inventory management can properly estimate demand and always have the right type and quantity of stock needed to satisfy expected demand, it can optimize revenue and profitability while lowering the risk of lost sales.

# [Conclusion](#toc.xhtml#s161a)

There is no doubt that with institutions and governments recognizing the power of blockchain, several industries have already begun to investigate how blockchain may be used to increase efficiency and automate processes. In this chapter, we covered some real-world applications of blockchain technology, extending beyond the scope of Bitcoin and other cryptocurrencies. However, keep in mind that this list is not exhaustive and does not contain all blockchain applications and systems that are currently in existence.

In the upcoming chapter, we will cover advanced topics such as blockchain nodes, instances and service providers.

# [Questions](#toc.xhtml#s162a)

1.  **What are the core characteristics of blockchain that allow it to be applicable for various use cases in a variety of industries?**
    
    Decentralization, secure, immutable ledger, and so on.
    
2.  **What are the challenges in traditional financial systems?**
    
    Needless paperwork and data breaches.
    
3.  **How can blockchain be used to enhance lending platforms and mechanisms?**
    
    Eliminating the need for intermediaries and the use of smart contracts.
    
4.  **How is blockchain used in digital identity management?**
    
    Each user can have their identity on the blockchain, which others can verify easily.
    
5.  **How to streamline processes in supply chain management with blockchain?**
    
    Digitizing physical assets can help organizations create a decentralized, immutable record of all transactions, making it possible to track assets from production to delivery.
    
6.  **How can blockchain coupled with IoT be used in various sectors such as agriculture and pharmaceuticals?**
    
    Installing IoT sensors in farms and transferring the data straight to the blockchain can be useful. The transparent and traceable characteristics of blockchain technology can aid in monitoring drug shipments from the point of origin to the point of destination in the supply chain and reducing counterfeiting.
    
7.  **What are the benefits of streamlining KYC procedures with blockchain?**
    
    Lesser error-prone and frauds. Easy and less time needed to do KYC.
    
8.  **How does blockchain benefit inventory management?**
    
    Blockchain technology will allow manufacturers to better manage product origins and track demand at the consumer level in real-time, thereby allowing them to estimate demand and schedule manufacturing and replenishment correctly.
    

# [Key terms](#toc.xhtml#s163a)

*   **Cross-border payments:** Payments sent from one country to another. Traditional cross-border payments involve a large number of intermediaries, which makes them quite inefficient.
*   **IoT/ Internet of Things:** The internet of things is a technology that brings about devices with sensors that can connect and exchange information with other devices over the internet, or any particular communications network they are a part of.

# [CHAPTER 8](#toc.xhtml#c08)

# [Blockchain Advanced—Nodes, Instances, and Service Providers](#toc.xhtml#c08)

# [Introduction](#toc.xhtml#s164a)

We have covered in detail how beneficial blockchains can be, along with how successful their applications are; now, it is time to learn more about how we can go about creating our own blockchains.

In this chapter, we will be covering the building blocks of blockchains in detail—blockchain nodes. In earlier chapters, we had briefly mentioned nodes and called them "*A computing device on the blockchain that participates in blockchain administration, every Node on a blockchain has a copy of the blockchain ledger*" while also mentioning that we will go into detail later. In this chapter, we will not only go into detail on what nodes are but also how you can deploy your own Blockchain instance and talk about Blockchain as a Service.

# [Structure](#toc.xhtml#s165a)

*   Blockchain Nodes—What are they?
*   Purposes of blockchain nodes
*   Functions of a blockchain node  
    *   Transaction processing
    *   Accommodating growth
    *   Accessibility
    *   Point of communication
    *   Storage
*   Types of nodes in blockchain  
    *   Full nodes  
        *   Pruned
        *   Archival  
            *   Authority
            *   Miner
            *   Master nodes
            *   Staking nodes
        *   Light nodes
        *   Supernodes
        *   Lightning Nodes
*   Deploying blockchain nodes
*   Technical difficulties
*   Blockchain as a Service
*   Some examples of BaaS providers
*   How to select the right BaaSp
*   Deploying a Blockchain instance using the example of AWS' managed blockchains.
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s166a)

On the completion of this chapter, you will have a thorough grasp of the concept of nodes, the purposes they serve, the different types of nodes that exist, the process of deploying nodes, and the surrounding technical difficulties. You will also have a general idea of how you can choose Blockchain Service Providers (and Blockchain as a Service, in general) and how you can successfully deploy a blockchain instance using Amazon Web Services.

# [Blockchain nodes—what are they?](#toc.xhtml#s167a)

Now that you are in [Chapter 8](#c08.xhtml) already, you should be pretty clear on the fact that blockchains are commonly referred to as a shared, P2P, and immutable ledger. If you have ever wondered who/what is responsible for this "*sharing*", a quick Google search would point to a crucial component of every blockchain system—the nodes.

We often compare blockchains with sports to make it easier for people to understand the different concepts. Take the sport of cricket, for example. As a viewer, it is essential that you understand the rules of the game (analogous to understanding how blockchain works) and know and support the different teams (blockchain applications) to fully appreciate the game. However, what good would the rules and the teams be if there is no ground for the players to play in?

If you have not caught on already, yes, we are comparing cricket grounds to nodes. Irrespective of whether a blockchain is public, private, or hybrid or which consensus algorithm it follows, every single blockchain has nodes that play a vital role in the functioning of a blockchain. To put it mildly, blockchain nodes make the blockchain.

Analogies aside, how can we actually define these nodes? We have already compared them with building blocks and cricket grounds, but what is the exact definition of nodes?

Apart from the same old "*nodes are computers that make up the blockchain*" that you have read a million times already, we cannot further define nodes without understanding the purposes they serve. The definition of nodes can vary from one application to another, and the purpose of the node. While people love to define nodes as "*electronic devices that are connected to the blockchain with an active IP address*", that definition is a bit misleading.

Yes, it is true that all nodes are electronic devices that are connected to the blockchain, and possess an active IP address. However, not all electronic devices that are connected to the blockchain with an IP address is a nodes. This seems to be quite a common misconception plaguing the blockchain space. Just because you are a user interacting with a blockchain, you need not be a node!

Consider the following example:

You use your computer to purchase 1 BTC online. Your computer, with an active internet connection, briefly connects to the Bitcoin network. During this transaction, your computer has ticked all three boxes on this misconceived definition of nodes

*   Your computer is connected to the Bitcoin Network
*   Your computer is an electronic device
*   Your computer has an active IP address.

However, your computer is not a Bitcoin node. It does not receive a copy of transactions, nor does it validate other transactions on the Bitcoin network.

This is the exact reason why we prefer not to define nodes as a whole but rather define them (and classify them) based on the purpose they serve.

However, to give you a starting point, we will give you a general definition of nodes. Note that this is not an exclusive definition (as all nodes need not provide the same functionality to a blockchain network) but rather a suggestive one. Usually, nodes can be defined as communication endpoints. Any application or user who wants to interact with a blockchain can do so by communicating through these nodes, like a communication redistribution center. Generally, nodes are also responsible for maintaining transaction records in a blockchain (there are other nodes which does not see a single transaction, let alone maintain the transaction records).

Now, to understand nodes better, let us learn the purposes they serve.

# [Purposes of blockchain nodes](#toc.xhtml#s168a)

Nodes enable blockchain to be distributed and have a decentralized presence. Nodes allow for the data to be stored in different locations all across the world, enabling permanent (barring the explosion of the entire planet, at which point, transactions and blockchains would be the least of our concern) and immutable records of transactions. Even if a whole country decided to go back to the stone age, as long as one node continues to exist, the blockchain and data would continue to exist.

Without these nodes, blockchains would merely be cryptographically encrypted databases. As we have discussed previously, this creates a single point of failure in the system, enabling hackers to focus on this vulnerability. The immutability is lost, and frankly, so does all the advantages that a blockchain system provides. The very concept of blockchain is that all blocks are cryptographically connected to the next block, and modifying one chain will have 0 results, as that chain will be weeded out using the different consensus algorithms.

However, if this chain was conveniently located only in a single location, or a single computer, anyone with half a brain could figure out how to permanently harm the data stored. Nodes are, thus, necessary for the very existence (and the success) of blockchain technology.

How does a node do all this? What are the different functions it serves? Answering all this and more in the next section.

# [Functions of a blockchain node](#toc.xhtml#s169a)

Depending on what your blockchain needs, nodes can achieve a wider array of tasks. However, these seemingly innumerable roles can be broadly categorized into the following five functionalities

*   Transaction processing
*   Accommodating growth
*   Accessibility
*   Point of communication
*   Storage

# [Transaction processing](#toc.xhtml#s170a)

All transactions done on the blockchain are sent to the transaction nodes of that blockchain network. Some nodes (in some cases, all nodes) take part in the consensus algorithm of the network to validate transactions, and some nodes may be responsible for keeping records of the different transactions (or even chains of transactions).

The workflow of a node responsible for processing transactions is fairly straightforward

*   Receive transaction
*   Accept/reject a transaction
*   Record the data (depending on your requirements, only the accepted transactions. Some blockchains also store a list of rejected transactions.)
*   Transmit the data to the other nodes (to maintain synchronization)

# [Accommodating growth](#toc.xhtml#s171a)

Nodes are also responsible for the growth of a blockchain. Every additional block of data occupies extra space in the nodes, and thus, nodes are often a bottleneck as well. In order to accommodate growth, it is essential that a mix of nodes with a memory limit and nodes containing all transactional data exists.

# [Accessibility](#toc.xhtml#s172a)

Nodes act as a point of access to the blockchain ledger and are responsible to fetch the necessary data that is queried by the end-user. The node provides access to the data in the blockchain, and not the data stored by the node itself (the two sets of data will be different if someone attempts to tamper with that particular node).

# [Point of communication](#toc.xhtml#s173a)

Nodes act as a communication endpoint—not only as access points, as seen earlier. They are responsible for synchronicity and are essential to protecting the integrity of the data.

# [Storage](#toc.xhtml#s174a)

Nodes are responsible for storing the data in the blockchain, enabling decentralization, and immutability. Depending on the memory limit, a node can either be deployed to store recent transactions or all transactions. It is recommended that there is a healthy mix of the two types.

# [Types of nodes in blockchain](#toc.xhtml#s175a)

Based on the requirements of a blockchain network (and on how the ledger is stored), nodes can be of many types but can be broadly categorized into two types:

*   Full nodes
*   Light nodes

These nodes are further categorized into different types, each of which has been explained in detail in the following section.

# [Full nodes](#toc.xhtml#s176a)

Full nodes can be defined as the servers of a blockchain, similar to how servers function in any network. These full nodes are an integral part of the blockchain's governance model, irrespective of the type of governance model. In fact, any major changes, including improvements (or changes of governance models), occur only after a majority (at least 51%) of full nodes agree to the changes. Full nodes have the right to vote in a blockchain network.

In the cases where a significant proportion of the full nodes vote for a change but not enough to be a majority, there is a very significant chance that we see a hard fork. The blockchain splits into two different blockchains—the old one exists as is, while the new blockchain will exist with the incorporated changes.

An extremely common example of a hard fork is that of Ethereum and Ethereum Classic, post the infamous DAO hack in July 2016.

Based on the memory limit, full nodes are further categorized into two.

# [Pruned](#toc.xhtml#s177a)

Pruned nodes have a defined memory limit, beyond which the node won't be responsible for storing data. While there is no limit on the number of blocks that can be added to a blockchain, pruned full nodes can place a limit on the number of blocks that are stored. Just like other full nodes, pruned full nodes also download the blocks from the blockchain to maintain the ledger. However, when the memory limit is reached, these nodes delete the oldest blocks to enable adding new ones.

Do not worry, the older transactions are not technically lost, even in pruned nodes, as the necessary metadata for all blocks (indirectly, this would include hash references to all past transactions) will make its way to newer blocks, staying true to the permanency principles of blockchains.

# [Archival](#toc.xhtml#s178a)

Unlike Pruned nodes, Archival nodes have no memory limit on how many blocks can be stored. These nodes are the most common type of nodes to date. However, as your blockchain grows and begins to take up a lot of data, you might consider maintaining a healthy mix of two and ensuring that the storage capacity does not become a chokepoint.

However, even blockchains as big as Bitcoin take up only about 380 Gigabytes of storage (as of 2021), so storage constraints are not the biggest of worries to kick-start the process of architecting blockchain.

Archival nodes can be further classified into four types.

# [Authority](#toc.xhtml#s179a)

Authority nodes are specific to private blockchains. These full nodes govern the access control for the data contained within the blockchain. The authority nodes are responsible for authorizing new nodes and enabling access to the data contained within the blockchain. In some blockchains, authority nodes can even give partial authority and access and can even create a partial authority node.

# [Miner](#toc.xhtml#s180a)

Specific to Proof-of-Work blockchains. Miner nodes are responsible for the process of mining. These nodes solve complex math puzzles and validate transactions on a blockchain network. The puzzles are generally to identify a random number that fits into an equation whose result would be one among a specific subset. Hashing is used in the process, which makes reverse calculation impossible. Varying the subset size would make the problem easy or difficult. These nodes require significant computational power and energy requirements.

# [Master nodes](#toc.xhtml#s181a)

These nodes do not contain the authority to add new nodes but merely act as storage nodes. Master nodes maintain the blockchain ledger and validate transactions.

# [Staking nodes](#toc.xhtml#s182a)

In blockchains using the Proof Of Stake Consensus algorithm, Staking nodes are responsible for validating the transactions. These nodes ensure that the users stake their crypto assets, validate transactions, and provide rewards for the staking process. Unlike mining nodes, staking nodes do not require as much computational power and electricity.

# [Light nodes](#toc.xhtml#s183a)

A light node can be considered a mini server. These nodes contain only the necessary data to facilitate the day-to-day functions of the blockchain and are not involved in the process of validating blocks. These nodes are also called Simplified Payment Verification nodes. Light nodes are extremely limited in their functionality and are not that common in the blockchain world.

While these are the most popular types of nodes, you should also know about super nodes and lightning nodes.

# [Supernodes](#toc.xhtml#s184a)

Supernodes are created for the specific purpose of carrying out special tasks in a blockchain network. Maintaining blockchain rules or even implementing new protocols in an existing blockchain is done through Supernodes.

# [Lightning nodes](#toc.xhtml#s185a)

Blockchains are becoming extremely notorious for congestion, leading to increased gas fees in blockchains like Ethereum. To solve this issue, nodes that create a separate network with transactions that are then pushed to the main blockchain were created. This lessens the congestion, cost, and load on the network while maintaining decentralization and immutability.

# [Deploying blockchain nodes](#toc.xhtml#s186a)

Now that we know the different types of nodes, let us move on to deploying your own Bitcoin node to get a taste of nodes. There are a number of requirements that must be taken into account to launch a node.

For instance, hardware is a major limitation in deploying a node. Bitcoin, for one, requires:

*   The latest version of Windows, Mac OSX, or Linux
*   500 Gigs or more of disk space, with a read speed of 100 Megabytes a second
*   Solid State Drive with at least 68 MB/s random write and 30.9 MB/s random read. (minimum 112 gigs)
*   8 Gigs of RAM
*   And an internet connection with a minimum download speed of 400 KBPS.

To install a bitcoin node, you need to create a folder to store the blockchain data in your file system. Install the full node from the bitcoin.org website. Once the installation is successful, your client should start the blockchain sync process. You need to allow an incoming connection through port 8333 in your firewall.

# [Technical difficulties](#toc.xhtml#s187a)

*   Bandwidth limitations: Bandwidth limitations are a huge issue when deploying your own node. Bitcoin requires you to download about 380 gigabytes of data, for which you might have to pay an additional cost. If network sync is interrupted, you will have to restart the node
*   Computer viruses and antivirus software affect the functioning of a bitcoin node. Antivirus software is particularly notorious for moving some data to quarantine, impeding the functions of nodes.
*   Hackers are often on the lookout for new nodes and may attempt to hack them.

In essence, you will be taking financial responsibility to purchase the necessary equipment and an active internet connection. You will also need the ability and skill to use the command line.

# [Blockchain as a Service](#toc.xhtml#s188a)

In order to remove the technical difficulties involved in setting up a node, Blockchain as a Service is becoming extremely popular. Based on your requirements, your provider can assume all responsibilities of your node and can provide access to popular networks such as Bitcoin, Ethereum, Monero, and Litecoin, among others.

You do not have to invest in the infrastructure or have the necessary skill to run the blockchains, as they are managed by the BaaS providers themselves.

# [Some examples of BaaS providers](#toc.xhtml#s189a)

There are many Blockchain as a Service Providers in the space right now. Here are 10 popular BaaS providers that you should know about.

*   IBM
*   Amazon Web Services
*   Tatum.io
*   R3
*   Hewlett Packard (HP)
*   Infura
*   GetBlock
*   Alchemy
*   Blockdaemon
*   Quiknode

We are not going into detail on the advantages and disadvantages of these platforms, but a simple Google search should help you out.

# [How to select the right BaaSp](#toc.xhtml#s190a)

Selecting the right BaaSp is essential, and you should look for the following things when choosing your blockchain partner.

*   **Backend services**: make sure the systems and processes proposed are user-friendly, and provide tangible benefits to your products
*   **Pricing support**: Let us face it, costs are important. Compare the pricing offered by the different service providers, but do not compromise on the quality
*   **Security**: One of the major reasons why you are outsourcing your nodes to a service provider is to increase security. Ensure that your BaaSp has an amazing track record.
*   **Experience**: Experience matters. Look at the previous projects that your BaaSp has undertaken, especially in deploying blockchain technologies in environments similar to that of your business.

# [Deploying a Blockchain instance using the example of AWS' managed blockchains](#toc.xhtml#s191a)

Creating and deploying a blockchain instance on Amazon Web Services, or AWS, is extremely easy. You are enabled to quickly create a blockchain network accessible through multiple AWS accounts, enabling multiple groups of people to transact and share data without having to rely on a single central authority.

Usually, deploying a self-hosted blockchain involves a lot of overlays in the form of hardware, turning software, setting up networking and security protocols, and so on.

However, by making use of Amazon's managed blockchains, the entire process of setting up a blockchain network becomes as easy as signing up for an AWS account. You get the choice of deploying a public blockchain (on the Ethereum network) or a private blockchain (on Hyperledger Fabric) and taking things from there. New members can be added through a voting process with the integrated voting API (which can also be used to vote for new proposals or anything else that you may need).

With the pay-as-you-use model, AWS is also pretty easy and economical to scale. Make sure to choose the appropriate selection of instances, memory, and CPU to support the workload necessary, and you will be good to go.

The process of deploying your first blockchain instance on AWS is simple. Sign up to a new AWS account (or login into an existing account) and navigate to the "managed blockchain console". Once in, you will be asked to choose between the two frameworks (Private—Hyperledger Fabric, Public—Ethereum). If you have chosen the Hyperledger fabric, you have to invite new members to your blockchain instance. You are also required to set the voting criteria here and choose "*create network and members*". This process will take approximately 15–20 minutes.

The next step is to provision the appropriate number and types of nodes, each of which will store a copy of your blockchain instance. Each member that you have created will require its own peer nodes. Select each member, click on create "Peer node", and provide the necessary details.

Congratulations. You have set up your very first blockchain instance. All that is left for you to do is to create and deploy decentralized applications that your organization needs, and you are good to go!

# [Conclusion](#toc.xhtml#s192a)

By the end of this chapter, hopefully, we have learned all that we need to know about nodes, their functions and purposes, and the different types of nodes that exist. We have also glanced at how to deploy nodes and the process of selecting the right Blockchain as a Service Provider. In the upcoming chapter, we will go into detail on the different consensus algorithms and how to choose the perfect consensus algorithm that suits your business needs.

# [Questions](#toc.xhtml#s193a)

1.  **Name the different types of nodes.**
    
    Full nodes, lightning nodes, super nodes, master nodes, and archival nodes.
    
2.  **What are the differences between an archival node and a pruned node?**
    
    Archival nodes have no memory limit, and they should be able to use huge amounts of data, whereas pruned nodes have a memory limit beyond which they cannot contain any more data.
    
3.  **What are the different types of archival nodes?**
    
    Authority, miner, master, and staking.
    
4.  **Name some technical difficulties involved in deploying blockchain instances.**
    
    Hardware capacity, huge memory requirements, huge bandwidth requirements, virus-antivirus issues, and hacking issues.
    
5.  **What is Blockchain as a Service?**
    
    Provider provides all facilities to setup a blockchain node instead of the user doing it themselves.
    
6.  **How do we choose an appropriate BaaSp?**
    
    Should have good backend services, a pricing model should not be costly, should be able to provide increased security, and should have some experience deploying some blockchain services.
    
7.  **What are the steps involved in deploying a blockchain instance on AWS?**
    
    Signup for AWS, navigate to managed blockchain console, and select blockchain type and provision number and type of nodes.
    

# [Key terms](#toc.xhtml#s194a)

*   **Blockchain Nodes:** These are devices connected to a blockchain network that serve a range of purposes in the working of the chain, such as validating new transactions and adding them to a block.
*   **Full Nodes:** These are the servers of a blockchain, and they can vote in the network.
*   **Light Nodes:** A light blockchain node can be considered a mini server. These nodes contain only the necessary data to facilitate the day-to-day functions of the blockchain and are not involved in the process of validating blocks.
*   **Super Nodes:** Super nodes carry out special tasks in a blockchain network.
*   **Lightning Nodes:** Lightning nodes create a separate network with transactions that are then pushed to the main blockchain.

# [CHAPTER 9](#toc.xhtml#c09)

# [Blockchain Advanced—Consensus Mechanisms](#toc.xhtml#c09)

# [Introduction](#toc.xhtml#s195a)

Although we have covered consensus algorithms briefly in one of the previous chapters, we have not really discussed the alternatives and how to choose the appropriate consensus protocol for your blockchain solution. Chances are, you will not need to build the next Bitcoin—a public blockchain with a costly, energy-consuming consensus mechanism for your business needs. As private and permissioned blockchains are simpler solutions to exist, which can not only tremendously impact the throughput of the blockchain but also reduce the cost required to operate one.

# [Objectives](#toc.xhtml#s196a)

In a decentralized blockchain, the consensus mechanism used has a major impact on the efficiency and effectiveness of the network. We will be addressing the different consensus algorithms: **Proof Of Work, Proof of Stake, and Delegated Proof of Stake**. We will also discuss private blockchain protocols that require much less energy and are used only by whitelisted users. After this chapter, you will have in-depth knowledge of the different consensus algorithms and choose the right one.

# [Structure](#toc.xhtml#s197a)

*   Consensus algorithms—What are they?
*   Proof of work—The original consensus algorithm  
    *   Advantages and disadvantages of PoW
*   The energy problem surrounding blockchains—The bitcoin problem, the Ethereum Solution
*   The case of private blockchains—Is proof of work necessary?
*   The alternatives—Proof of stake, delegated proof of stake  
    *   Advantages and disadvantages of the alternatives
*   Conclusion
*   Questions
*   Key terms

# [Consensus algorithms—What are they?](#toc.xhtml#s198a)

In a previous chapter, we studied how fundamentally different blockchains were from traditional databases. One of the key points of difference that we kept harping on was the decentralization that comes with blockchains which are absent in centralized databases. In order for these centralized databases to function efficiently, there was the necessity to trust the central authority to do his/her job properly. The task of validating the transactions usually lies within this central authority.

However, for all the benefits that we had discussed in detail when shifting to a decentralized system, a protocol to validate these transactions is extremely essential. The records in a blockchain are maintained and validated by hundreds and thousands of computers. In this environment, where transactions could be happening every single second, an efficient, stable, reliable, and secure mechanism that validates the transactions and ensures that all the participants in the network agree on the state of the ledger is extremely crucial.

Blockchain consensus algorithms allow you to do just that. These protocols ensure that whenever a new block is added, the information present is the definitive truth and is agreed on by all the nodes in the network. A consensus mechanism can thus be defined as a fault-tolerant set of rules used in blockchains (sometimes even in other computer systems) with the simple motive to achieve the required agreement on a data set.

While there are different consensus algorithms used for different purposes, they all follow similar characteristics and objectives.

*   Consensus mechanisms should be safe. Every single node in the network should be able to not only follow the rules in the protocol but also should be able to do so without putting the network at risk.
*   Every single node should be able to participate and have a (direct or indirect) say in the modifications being made. However, there can exist certain nodes that do not participate in the governance but act merely as storage units (Master Nodes). The algorithm, however, should ensure that every node has the ability to participate in the voting process. (Think of it as master nodes as specific nodes that abstain from voting but not from doing their work)
*   The consensus mechanism should be fault-tolerant. We had briefly touched upon Byzantine Fault tolerance before, but there is also one more type of fault that blockchains should be tolerant to.  
    *   **Byzantine Fault Tolerance**—Byzantine Failure is said to occur when one node (or group of nodes) misbehaves due to many reasons, including bugs or being compromised by people with ill intentions. This corrupted node(s), called the byzantine node, can arbitrarily send deceptive messages to other nodes and cause serious issues in blockchain security.
    *   **Crash Failure Tolerance**—Sometimes, nodes can fail to respond due to hardware or software crashes. Even with pristine maintenance, crashes and failures do happen, and it is extremely important that these contingencies are taken care of.

In public blockchains like Bitcoin and Ethereum, this consensus process is incentivized. The nodes validating transactions and adding new blocks are economically rewarded in the form of cryptocurrencies (The process which is commonly referred to as mining cryptocurrencies). Since anyone can hook up to a public blockchain network, these incentives are necessary to ensure that all the participating nodes follow the consensus protocol.

On the other hand, in the case of private, permissioned blockchain networks, where a degree of decentralization is necessary, say, to promote collaboration between competing organizations, it becomes unnecessary to involve additional economic incentives to help follow consensus mechanisms. These types of protocols are commonly called non-incentivized protocols.

# [Proof of work—The original consensus algorithm](#toc.xhtml#s199a)

Probably the single most popular consensus algorithm, thanks to Bitcoin's popularity, is proof of work. Contrary to popular belief, it was not introduced by the pseudonymous Satoshi Nakamoto in his (or her or their) Bitcoin whitepaper in 2008. In fact, the first time concept of Proof of Work was introduced way back in 1993 by Cynthia Dwork and Moni Naor.

PoW systems require the participating nodes to put in significant work and energy to validate transactions. The nodes work on solving a completely arbitrary math puzzle to prevent malicious actors from attempting to game/manipulate the system (Byzantine Fault). Please refer to the following figure:

![](images/Figure-9.1.jpg)

**Figure 9.1:** Proof of work incentive mechanism

# [How do math puzzles prevent Byzantine failures?](#toc.xhtml#s200a)

The explanation is fairly simple. We had previously talked about what hashes are, and we will do so again now. A hash can be defined as a math function that changes or encrypts any input of any length to a unique output of a fixed length. This means regardless of the size of data involved in the blocks, and the hash size will always be the same.

If you use the same hash function on the same data, the hash obtained will be the same, making it easy to validate that the data is unchanged, provided you already know the hash. However, it is impossible to convert or reverse engineer the hashes back to their original data.

For example, as seen in the image as follows:

![](images/Figure-9.2.jpg)

**Figure 9.2:** Components included in every block of the bitcoin blockchain  
**Source:** Mycryptopedia

In Proof of Work Systems like Bitcoin, where the transactions are encoded with SHA-256 encryptions, each block will carry its own unique hash. For instance:

*   Block number #6600000 was mined on 4 December 2020.
*   Its unique hash code is 00000000000000000008eddcaf078f12c69a439dde30d bb5aac3d9d94e9c18f6.
*   The block will only contain 745 transactions and only the transactions pertaining to 1,666 bitcoins (The header of the previous block is just info and not transaction ).
*   If anyone attempts to pocket even 1 Satoshi more, the resultant hash will be completely different, enabling the network to identify that the malicious nodes' version of events is false and will be discarded.

Whenever a new block is to be "*mined*", nodes all over the world compete to solve the hash of the new block. In simple words, this means the computers should generate random numbers and plug it into pending transactions that are yet to be confirmed and generate a hash for that entire data. Then the hash is supposed to be less than the specific number agreed upon by the network. If the hash is greater than this number, then the computers will discard that random number and hash, and then start with a new random number till the lesser than condition is achieved. Whenever a computer finds this kind of random number, it will immediately broadcast this to the entire network, and this is when all other computers also verify if that broadcasted random number fits into the criteria. If it does, then it forms the next block in the blockchain.

In the case of Bitcoin, a new block is created approximately every 10 minutes, and the first node successful in computing the hash will be rewarded additional Bitcoin. Once a valid hash is computed, it is broadcasted to the entire network, creating a new block in the bitcoin blockchain.

# [Advantages and disadvantages of PoW](#toc.xhtml#s201a)

Proof of Work is by far the most secure consensus algorithm that is known to man yet. This consensus algorithm makes it next to impossible for a 51% attack to be carried on due to increased difficulty, as well as costs involved in the attempt. Proof of Work also offers the highest levels of decentralization when compared to the other consensus mechanisms that are popularly in use.

However, the harsh reality is the fact that Proof of Work is perhaps too wasteful for many blockchains. All participatory nodes expend significant computational power and energy, but only one node is rewarded for calculating the hash and validating the new block. This leads to the wastage of energy that went redundant in completing this calculation. Scaling becomes incredibly hard to achieve with a Proof of Work model.

A Proof of Work model should only be considered by large, public blockchains looking to provide the highest levels of security and decentralization. Even then, popular blockchains are moving away from Proof of Work.

![](images/Figure-9.3.jpg)

**Figure 9.3:** Possibility of 51% attack on blockchain  
**Source:** Andrew Butler on Hacker Noon

The most popular vulnerability in blockchains utilizing the Proof of Work consensus mechanism is probably the 51% attack. Blockchains like Krypton, shift, and Bitcoin gold have been subject to the 51%. The attack is fairly self-explanatory:

*   By controlling a 51% majority of all mining nodes, it is possible for malicious actors to interfere with the validation process and make the mining process a monopoly.
*   Double spending would be extremely prominent (the process of spending a coin and reversing the transaction in a later stage to be spent again is called double-spending).

However, even after a 51% attack, it is still impossible to alter historical transactions which were locked in before the attack. Users of the network can choose to create a hard fork after altering the effects of the 51% attack, maintaining the integrity of the blockchain.

However, in the case of big blockchains which do use PoW consensus mechanisms—like Bitcoin, the computational power required to grasp 51% of the total hashing power is monumental and would require billions of dollars to achieve something of little benefit.

# [The energy problem surrounding Blockchains—The bitcoin problem, the Ethereum solution.](#toc.xhtml#s202a)

Unless you have been living under a rock, you have probably heard of all the public outcry against Bitcoin and how harmful it is to the environment in the long run. This comes as no surprise to anyone, as the Bitcoin network, thanks to its PoW consensus mechanism, used up as much energy as Pakistan did in the year 2020. Although there are many miners committed to staying carbon neutral, and using only green, renewable sources of energy, the fact that such a significant amount of energy has been used cannot (and did not) bode well with the rest of the community.

However, it is fundamentally essential that Bitcoin remains the most secure and reliable cryptocurrency out there, making an extremely valid argument for continuing to use the Proof of Work consensus model, despite the popular backlash (and the ever-plaguing scalability issues).

Ethereum, the second most popular cryptocurrency and blockchain system, also uses the wasteful PoW consensus algorithm. However, with the necessity to scale up for accommodating increasing demand, along with the need to reduce energy consumption levels, Ethereum is shifting into the Proof of Stake Consensus model, which is rumored to be sometime in the year 2022. Proof of Stake, and some of the other (albeit marginally less decentralized) consensus mechanisms, are beginning to become extremely popular.

# [The case of private blockchains—Is Proof of Work necessary?](#toc.xhtml#s203a)

In the case of private blockchains, **Proof of Work** (or even Proof of Stake and Delegated Proof of Stake) might be a little too much. It would be like using C4 explosives to get past a fence with gaps wide enough to fit elephants in. In fact, using PoW or PoS might do more harm than good. Not only will the maintenance costs be extremely high, but the speed at which the transactions are validated will also be slower than some of the other consensus mechanisms that can be used.

In the case of private blockchains, the following are certain factors that you need to take into account before choosing an appropriate consensus algorithm.

*   The speed at which new blocks would be needed to be added to the blockchain. Speed and trust guarantees are inversely related.
*   The number of nodes and miners in the network.
*   The finality of the blocks. Some consensus protocols can be used, which can treat the block decisions to be conditional on future actions. Some other protocols would allow for the finality to be eventual rather than immediate.
*   How much trust is placed on the nodes? Is the objective of the blockchain is to simply create a crash-tolerant network, or is there a high risk of the nodes being hacked?

Depending on your answers to these questions, you might land up on something far more efficient (Like Proof of Authority, Unique Node List, or Practical Byzantine Fault Tolerance) to meet your needs. Just, for example, VMware is currently using this P-BFT consensus algorithm in their enterprise blockchain solution.

# [The alternatives—Proof of stake, delegated proof of stake](#toc.xhtml#s204a)

Please refer to the following figure:

![](images/Figure-9.4.jpg)

**Figure 9.4:** Proof of Stake incentive mechanism

While there are more than 50 other consensus mechanisms that exist to date, the most popular ones are Proof of Stake and Delegated Proof of Stake.

Instead of a competition to arrive at the node, a random node is selected (like a lottery) to compute the hash value in the case of a Proof of Stake network. In order to ensure that the selected node does not validate fraudulently or erroneously, each node has to stake a ratio of coins to be even considered in this lottery. Other nodes can cross-verify the transactions and can "call out" the mistaken node for its erroneous version of events, leading to the staked coins being lost as a punishment.

In most Proof of Stake networks, the chances for a particular node to be selected in this "lottery" will be directly proportionate to the number of coins staked.

However, for a Proof of Stake to function, nodes will still need significant computing power to actually compute the hash value. This might lead to participants with subpar competing power being inactive towards the whole validation process. In order to accommodate these situations, a special type of consensus algorithm called Delegated Proof of Stake was developed.

In a DPoS system, the actual validators will be limited to a small percentage of the nodes. All other participants can stake their tokens on behalf of one of these nodes to validate the transactions on the behalf of them. (Interestingly, this type of consensus is how most governments work in the current era. Citizens vote for Members of Parliaments, who, in turn, vote for the laws and regulations on behalf of the members).

# [Advantages and disadvantages of the alternatives](#toc.xhtml#s205a)

![](images/Figure-9.5.jpg)

**Figure 9.5:** Pros and Cons of various consensus algorithm mechanisms during crypto mining

For one, Proof of Stake and Delegated Proof of Stake consensus mechanisms are marginally less secured and decentralized. In Delegated Proof of Stake systems, in particular, the element of trust begins to creep back in, albeit to a much lesser degree when compared to a centralized solution. PoS and DPoS are significantly more scalable and can process more transactions in a limited period of time when compared to PoW.

Currently, for public blockchains, the common consensus is that Proof of Stake consensus mechanisms offers the best of both worlds. Proof of Stake offers high levels of decentralization (albeit marginally lesser levels when compared to PoW), high levels of security, and scalability while operating at a fraction of the energy that is required to run a Proof of Work blockchain.

(Postscript)

*   Proof of Authority—consensus algorithm similar to PoS, but instead of staking coins, the node stakes its reputation and authority within the network. Extremely fast.
*   Unique Node List—In a network with trusted nodes, the selected nodes can validate transactions without having to stake anything. One of the fastest consensus algorithms but also the least secure.
*   Practical Byzantine Fault Tolerance—Each node participates in a voting process after considering the new data to determine which version of the data is valid. Moderately secure, moderately fast.

# [Conclusion](#toc.xhtml#s206a)

Consensus algorithms are the methods that a blockchain network uses to finalize a transaction, making the system truly decentralized. There are many different types of consensus algorithms, with Proof of Work and Proof of Stake being the most common ones. Each type of consensus algorithm comes with its own set of advantages and disadvantages. In the case of private blockchains, the Proof of Work consensus algorithm might just be overkill. PBFT or POA might be the way to go for your use case, depending on multiple different factors like scalability and speed of finality of a transaction.

# [Questions](#toc.xhtml#s207a)

1.  **What is a consensus Algorithm?**
    
    An algorithm is followed by blockchain network nodes in order to finalize a transaction.
    
2.  **Why are consensus Algorithms necessary?**
    
    To avoid malicious activity in blockchain network by providing the highest level of correctness and security to a blockchain network.
    
3.  **Name some types of commonly used consensus algorithms.**
    
    Proof of work, proof of stake, Practical byzantine fault tolerance
    
4.  **What is Proof of Work?**
    
    Every node in the blockchain network tries to compute the hash of the next block; the one doing it first is awarded some bitcoins in the case of a bitcoin network.
    
5.  **What is Proof of Stake?**
    
    Every node participating in PoS consensus has to stake some coins in order to compute the hash of the next block. Other nodes can cross-verify the transaction
    
6.  **What is Practical Byzantine Fault Tolerance?**
    
    Each node participates in a voting process after considering the new data to determine which version of the data is valid. Moderately secure, moderately fast.
    
7.  **What is Proof of Authority?**
    
    It is a consensus algorithm similar to PoS, but instead of staking coins, the node stakes its reputation and authority
    
8.  **State some advantages and disadvantages of Proof of Work.**
    
    Advantages-> Most secure, impossible to perform 51% attack
    
    Disadvantage-> wasteful of resources, difficult to scale
    
9.  **State some advantages and disadvantages of alternatives like Proof of Stake.**
    
    Advantages-> Better use of resources, energy-efficient, more decentralized
    
    Disadvantages-> Less secure, nothing at stake problem
    

# [Key terms](#toc.xhtml#s208a)

*   **Consensus Algorithm:** These systems are a fault-tolerant set of rules that make sure that whenever a new block is added on the chain, the information present is the definitive truth, and is agreed on by all the nodes in the network.
*   **Proof of Work:** PoW is a consensus algorithm that requires the participating nodes on the blockchain to put in significant work and energy to validate transactions. The nodes work on solving a completely arbitrary math puzzle to prevent malicious actors from attempting to game/manipulate the system.
*   **51% Attack:** This is a kind of attack carried on a blockchain where a bad actor attempts to control a 51% majority of all mining nodes. This way, the mining process can be made a monopoly.

# [CHAPTER 10](#toc.xhtml#c10)

# [Architecting Blockchain Solutions From Scratch](#toc.xhtml#c10)

# [Blockchain Architecture: The Groundwork](#toc.xhtml#s209a)

# [Introduction](#toc.xhtml#s210a)

As we are well aware, blockchain, in general, has become one of the fastest-growing sectors in recent years as more and more companies are looking to go digital and seek out blockchain professionals to upgrade their existing mechanisms with blockchain implementations or even create entirely new systems from scratch. Therefore, right now is a fantastic time to become a blockchain professional and take part in this latest technological revolution. With all the context we have had so far, it is time to get more technical and get our hands dirty.

For those of you who aspire to join this industry as blockchain architects, you have already acquired a lot of the basic knowledge you are expected to have as a blockchain architect on our journey so far. In the very first chapter, we learned a little about how you can become a blockchain architect. Now, in this chapter, we will be discussing in detail the process you will need to go through to become a professional blockchain architect—the skills, the global certifications, the right platform, and the groundwork for blockchain development—the whole nine yards.

# [Structure](#toc.xhtml#s211a)

The following topics will be covered in this chapter:

*   The necessary skill set to become a blockchain architect:  
    *   A good grasp on cryptography
    *   Knowledge of multiple programming languages
    *   Smart contract development
    *   Extensive knowledge of data structures
    *   Web development
*   Certifications and examinations to become a blockchain architect
*   Groundwork for developing a blockchain architecture  
    *   Types of blockchain architecture:
    *   How to develop a private blockchain architecture?
    *   What purposes can a blockchain serve?
    *   How to create a blockchain network?
    *   How to choose the suitable consensus mechanism for your blockchain?
    *   Types of consensus mechanism for blockchains
    *   How to pick the right platform to aid the development of your blockchain?
    *   What are some popular blockchain platforms among blockchain architects?
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s212a)

Blockchain architecture is an extremely alluring field for upcoming blockchain enthusiasts, and in this chapter, we will be covering the procedure to become a certified blockchain architect. Starting with the different skills required to become a blockchain architect, we will look through the method of getting global certification as a blockchain architect and the process of laying the groundwork for our very own blockchain architecture.

# [The necessary skill set to become a blockchain architect](#toc.xhtml#s213a)

Blockchain architects have quite a lot of responsibilities; as discussed in chapter one, a blockchain architect is the backbone of a particular blockchain solution and is responsible for everything the solution embodies—from research to execution and everything in between. In this section, we discuss the primary skills you need to be a blockchain architect.

# [A good grasp on cryptography](#toc.xhtml#s214a)

We already know why cryptography is important to the structure of a blockchain and how it works to give the blockchain, the data, and the transactions on it with the maximum possible security. Along with hashing, cryptography is integral in the functioning of a blockchain. Therefore, to become a blockchain architect, it is important to study thoroughly about cryptography and make yourself familiar with all the fundamentals of it and how it is integrated with the blockchain structure.

# [Knowledge of multiple programming languages](#toc.xhtml#s215a)

As a blockchain architect, you will be expected to know more than one programming language. Just in case you are wondering which ones you should learn, the following is a list of some popular programming languages you can start with:

*   **Python:** Python is a versatile and very easily readable programming language because its syntax is very similar to that of the English language. You might want to start with Python if you are still deciding which programming languages to learn, as Python is quite user-friendly.
*   **Java:** Java is one of the older programming languages, as it has been around since 1995. However, despite being old, Java remains relevant to technology till date; in fact, it is quite popular among many blockchain professionals, and there is a number of reasons for that. While Java is relatively easier to learn, it can help you develop many complex protocols and solutions. New Economy Movement (NEM), a well-known cryptocurrency platform, was built using Java as a programming language.
*   **C++:** Another popular programming language, C++ is also used widely by blockchain professionals as a base for a wide range of applications. It is to be noted that since the Bitcoin team used this particular programming language to create Bitcoin core, it is generally expected of an aspiring blockchain architect to know C++ in particular.
*   **JavaScript:** JavaScript, also known as JS, is not to be confused with the aforementioned Java. Even though the title and even the syntax are quite similar for the two, they are actually quite different in their features. JavaScript, which was initially got developed to make Web pages interactive at the browser level, eventually made its way as the server-side and application programming language as well.

# [Smart contract development](#toc.xhtml#s216a)

Smart contracts are a significant part of any modern blockchain solution, therefore, as a blockchain architect, you are required to be familiar with smart contracts and their underlying mechanisms, and also programming languages specializing in smart contract development, such as Chaincode and Viper, is a requirement.

# [Extensive knowledge of data structures](#toc.xhtml#s217a)

As we know, blockchains are made up of multiple data structures, and they are fundamental to the working of a blockchain. So, as you conceptualize and create blockchain solutions as a blockchain architect, you would need to work with various data structures on a regular basis, which is why you should definitely have extensive knowledge of them.

# [Web development](#toc.xhtml#s218a)

As a blockchain architect, you should also possess in-depth knowledge of web design, development, and the programming of applications, as you and your team will surely be required to build easy-to-use and aesthetically pleasing Web applications.

# [Certifications and examinations to become a blockchain architect](#toc.xhtml#s219a)

There are a few steps you need to go through to acquire the proper certifications to become a blockchain architect. To have a career as a blockchain architect, you can start by taking a course in various aspects of blockchain—there is a wide range of course options available on the internet that you can look through to select one to your liking. Blockchain certification courses can give you an in-depth understanding of the technology and even allow you to work on various projects that provide you with hands-on experience and industry exposure.

Blockchain courses may contain the following modules:

*   **Fundamentals of blockchain:** that is a deep knowledge of the tech, crypto tokens, and mining, among other things
*   Real-world applications of blockchain and industry use cases
*   Building and implementing blockchain projects
*   Creating blockchain networks
*   Writing smart contracts
*   Creating a cryptocurrency in the form of coins or tokens

It is to be noted that for most of these blockchain courses, you will be expected to have a high school or even graduate-level certifications in mathematics, physics, or any engineering stream. In some cases, you might also be required to have knowledge of programming languages like Python so as to be eligible for the practical aspects of the courses.

# [Groundwork for developing a blockchain architecture](#toc.xhtml#s220a)

Blockchains are being architected for broad use across a number of industries, and they serve a variety of purposes, such as helping with cost reduction, providing a distributed database, and immutable data recording, for starters. In this section, we will learn the basics of how to go about developing a blockchain architecture, starting with types of blockchain architecture.

# [Types of blockchain architecture](#toc.xhtml#s221a)

There are three basic kinds of blockchain architecture, which are as follows:

*   **Public Architecture:** This is the most decentralized kind of blockchain architecture, and all participating nodes on a public blockchain are given access to the data stored on the chain. Both the Bitcoin and Ethereum networks are public blockchains.
*   **Private Architecture:** This kind of blockchain is not decentralized and instead is kept private. These systems are managed and accessed only by a group of authorized users. Sawtooth and Fabric are well-known examples of private blockchains. Please refer to the following figure: 
    
    ![](images/Figure-10.1.jpg)
    
    **Figure 10.1:** Nodes in public versus private blockchains  
    (**Source**: [https://mlsdev.com/blog/156-how-to-build-your-own-blockchain-architecture](https://mlsdev.com/blog/156-how-to-build-your-own-blockchain-architecture))
    
*   **Consortium Architecture:** Although this kind of blockchain is not fully decentralized, it can consist of users from multiple organizations, and the system is managed by selected users. The Energy Web Foundation is a good example of a consortium blockchain architecture.

# [How to develop a private blockchain architecture?](#toc.xhtml#s222a)

To start off the development of a private blockchain architecture, you will need to know and decide on the following:

*   Specific goals and functions of the blockchain you are about to build, the nodes (people or entities running the nodes), the blockchain network will be distributed among specific user roles, and the system flow and interactions between users and data stored on-chain, the UX/UI designs, the consensus mechanism suitable for the project, the tools and platform you will be using for the development of your blockchain application, and, of course, an architecture plan after taking the aforementioned information into account.

Now, in the following sections, we will expand upon the possible functions of a blockchain, how to create a blockchain network and pick the right consensus mechanism, and how to choose the right platform for your blockchain development.

# [What purposes can a blockchain serve?](#toc.xhtml#s223a)

We already know about blockchain's use in the crypto industry, so let us look at some other diverse functions a blockchain you have to conceptualize might serve. This time we would also be looking at these from the application level than just the industry level.

*   **Banking and Finance:** This is an obvious one you already know about. In finance, a blockchain solution would be eliminating the security issues of traditional finance and accelerating procedures like Know Your Customer (KYC) and Anti-Money Laundering (AML) with a distributed database multiple financial organizations can access. A few other noteworthy services here can be clearing, settlements, and wealth management.
*   **Medical Record Keeping:** In the healthcare industry, a blockchain application will have to securely store private and confidential patient records and also allow multiple healthcare facilities to facilitate a simple-to-access and secure way to exchange and seek outpatient data.
*   **The Travel Industry:** In travel, a blockchain solution might need to help with tasks such as luggage tracking (especially when there are multiple flights in one itinerary or international flights) and identifying passengers in a way that consumes far less time than the traditional way.
*   **Online Voting:** In online voting, a blockchain application would have to facilitate the casting of ballots in a decentralized and traceable way, so the process is transparent and less time-consuming.
*   **The Music Industry:** In the music industry, a blockchain solution would have to work so that an artist can share their music with their intended audience while protecting themselves from piracy, and the blockchain would have to have a mechanism in place so as to allow the artists to be compensated for sharing their songs and albums.
*   **Supply Chain Operations:** When it comes to blockchain in supply chain operations, it increases accurate tracking of goods and promotes better transparency. On top of this, the architect would need to keep in mind security and regulatory compliance due to multiple parties being involved.
*   **Human Resources:** In HR, a blockchain solution might have to tackle tasks like tracking employee payments and company expenses and simplifying the act of paying taxes for a company and its individual employees.

# [How to create a blockchain network?](#toc.xhtml#s224a)

With all the users a particular organization wants participating in their blockchain, a blockchain will generally form a peer-to-peer or P2P network to build a transparent system, where every participant has a real-time copy of the blockchain ledger that updates itself every time some new record is added to the chain.

# [How to choose the suitable consensus mechanism for your blockchain?](#toc.xhtml#s225a)

A consensus mechanism or algorithm in a blockchain helps it maintain a distributed ledger in real-time. Since there is no centralized authority on a blockchain network to verify the transactions to be added to the blockchain or update the ledger, the participants require a mechanism to decide which transactions should be added to the chain; this is exactly where a blockchain consensus mechanism comes in.

A consensus mechanism is a crucial part of a blockchain, and therefore, it is important that as a blockchain architect, you possess proper and intensive knowledge regarding different kinds of consensus mechanisms so as to be able to choose the suitable one for your specific blockchain design. In the following section, we discuss some popular types of consensus mechanism in brief detail.

# [Types of consensus mechanism for blockchains:](#toc.xhtml#s226a)

The many types of blockchain consensus mechanisms, while having entirely too similar goals, vary on the basis of the method they choose to achieve consensus. While there is no single consensus mechanism that we can claim to be the most reliable one for a blockchain architect, each of the ones discussed as follows has so far proven to be tactful, though they are not without their faults.

*   **Proof of Work or PoW:** You might have recognized this one as the consensus mechanism behind Bitcoin; PoW is also known as mining. Miners (specific nodes) on a Proof of Work blockchain use various kinds of mining equipment and tools such as CPU mining, GPU mining, FPGA mining, mining pools, ASIC mining, and many others to solve complex mathematical problems. These problems are solved by repeatedly generating a random number and, along with transactional data, creating a hash to know if the result falls into the criteria. For this, miners need a large amount of computational power to generate a random number and solve the problem before anyone else. Moreover, the difficulty level of these mathematical problems increases as the speed at which blocks are being mined goes up. This adjustment will help to maintain the time needed for creating new blocks even when more miners join the network on a PoW blockchain. 
    
    Once a particular miner succeeds in solving a mathematical problem, they get to add a new block to the Proof of Work blockchain ledger and get rewarded for their efforts. For the Bitcoin blockchain, as we know, a miner gets rewarded with a certain number of bitcoins after successfully adding a new block to the chain, along with a portion of the transaction fees the blockchain acquires.
    
*   **Proof of Stake or PoS:** In Ethereum 2.0, the new structure of the platforms shifts the blockchain from a PoW consensus mechanism to a Proof of Stake one. A PoS blockchain uses a randomized method to choose which participant on the chain would get to generate the next block and add it to the chain. 
    
    On a PoS blockchain, there is usually two roles a participant can take up. The first is that of the validator, where a user has to lock up a certain number of tokens for a set amount of time, and in exchange, they are given the power of producing blocks. While different PoS blockchains may have different procedures for selecting validators from all the participants, usually, the people who have the biggest stakes and/or lock up their coins for the longest periods of time are chosen to be validators. A validator maintains the PoS blockchain network and is rewarded with all or part of the fees the blockchain receives from all the transactions included in a particular block.
    
    The other important role in a Proof of Stake blockchain is that of the delegator. Participants who cannot afford to stake the amount of money it takes to be a validator can choose to delegate the tokens they can spare to a validator of their choice and, in return, get an equivalent part of the reward the validator receives.
    
*   **Proof of Activity or PoA:** This one is a combination of Proof of Work and Proof of Stake. Just like a normal PoW blockchain, in a Proof of Activity, chain miners have to find the solution to a complex mathematical problem to create a new block. However, the blocks thus created are only simple templates with a mining reward address and header information. This header information is, in turn, used to pick out a group of validators to sign a block. Like a PoS blockchain, these validators are selected based on the size of their stake. The signed block is then added to the blockchain. The miner who generates the block and the group of validators who sign it are rewarded with a portion of the network fees. Two well-known blockchains using this algorithm are Espers and Decred coin.
*   **Delegated Proof of Stake or DPoS:** Delegated Proof of Stake is quite a bit faster than the average Proof of Stake blockchain. On a DPoS blockchain, a user can stake their tokens and earn the right to vote for a certain number of delegates. The bigger a user's stake, the more important their vote would have. Blockchains such as Cardano, EOS, and Tron uses this consensus mechanism. 
    
    After the voting, the delegate who receives the highest number of votes would get to generate new blocks on the chain. Just like any Proof of Stake blockchain, a delegate on a Delegated Proof of Stake blockchain receives a set amount of tokens or a part of the transaction fees the chain accumulates as a reward.
    
*   **Proof of Authority or PoA:** The Proof of Authority consensus mechanism is essentially a somewhat modified version of the Proof of Stake mechanism where instead of tokens, their identities are what network validators are staking. On a PoA network, the number of validators is quite small compared to a general PoS blockchain, and validators are incentivized in much the same fashion as a PoS protocol. This consensus mechanism is not popular as it is seen to be unreasonably centralized as compared to other consensus mechanisms.
*   **Proof of Capacity or PoC:** For this one, the solutions to the mathematical problems nodes on a blockchain need to be solved are stored in various digital storages, like hard disks, through a process known as plotting. Once a particular storage device has been filled with solutions to complex mathematical problems, users on the blockchain can use it to try and generate new blocks on the chain. Again, the user who can reach the right solution to a puzzle the quickest gets to produce a new block; therefore, for a PoC blockchain, those users with the highest storage capacities will have higher chances of getting to create a new block. This consensus mechanism is used by Storj, Spacemint, and Burstcoin networks.
*   **Proof of Identity or PoI:** This particular consensus mechanism matches a user's private key with an authorized identity. So any user who has been identified on the network is allowed to create a new block that they can then present to all the users in the network. A Proof of Identity blockchain makes sure of the integrity and authenticity of the data stored in a particular block. There are no well-known implementations of this consensus mechanism on public blockchains yet.
*   **Proof of Elapsed Time or PoET:** On a Proof of Elapsed Time blockchain, the creator of a new block is decided based on the amount of time they have waited to be chosen. To elaborate, the mechanism on a PoET blockchain comes up with a randomized waiting period for every user, and the user whose waiting period is over at the earliest gets the opportunity to create a new block. There is no successful implementation of this algorithm in any public blockchain yet.

# [How to pick the right platform to aid the development of your blockchain?](#toc.xhtml#s227a)

Most blockchain platforms contain a broad assortment of components, and as a blockchain architect, it would fall on you to select a platform that would offer all the suitable components on par with your blockchain's particular requirements. Here, we have compiled a list of essential features that can be focused on while evaluating the merit of a certain blockchain platform and its components on offer.

# Whether the blockchain is public or private

First, you must check whether a blockchain platform is open (that is, public) or closed (private). This particular factor affects two integral elements: the blockchain's speed and security. Public blockchains—since they are open to everyone, are both less swift and less secure than private platforms.

# Consensus mechanism

As we have seen in just the previous section, there are many methods through which a blockchain achieves consensus. While selecting a platform for your project, you will need to consider whether a platform's consensus mechanism suits your needs or not.

# The ledger technology in use

As a blockchain architect, you must look into a blockchain platform's ledger technology—as in what procedure is in action in keeping records regarding transactions and other information. For instance, two popular technologies for this very purpose are UTXO and an account model. The UTXO model (used by Bitcoin) does not require accounts or balances; tokens or UTXOs are directly exchanged between users like tangible money instead. On the contrary, an account model keeps records of the balance. Ethereum is a prominent blockchain to use the account model.

# Smart contracts

As a significant part of a blockchain platform's value originates from the programmability and automation of its smart contracts, it is important for a blockchain architect to consider this particular feature of a platform.

# Development tools

Another feature you should evaluate is the range of tools a platform offers to support blockchain application developers.

# A blockchain platform's maturity

As more mature blockchain platforms usually have more interoperability, vendor support, and stronger and wider developer communities, you should choose to go with one of the mature ones if it otherwise suits your project's needs.

# [What are some popular blockchain platforms among blockchain architects?](#toc.xhtml#s228a)

**Ethereum** has, of course, being the most popular choice among project developers since its inception back in 2013. Ethereum facilitates true decentralization, has a mature collection of tools for developers, and the platform also provides strong support for smart contracts using the Solidity programming language environment, running on the EVM or the Ethereum Virtual Machine. Not to mention Ethereum's wide developer community consists of over 250 members, which includes organizations like Microsoft, Intel, and JPMorgan.

Among Ethereum's downsides are the relatively slower transaction processing period compared to some more recent blockchain platforms and the higher platform fees. However, with Ethereum 2.0, both these issues are expected to be solved.

Next up is the **IBM Blockchain**, which provides a private and decentralized blockchain platform. The developer tools on the platform are flexible and customizable, and the user-friendly interface simplifies many tasks for project developers, such as setting up, testing, or swiftly using smart contracts.

Another popular and mature blockchain platform is **Tezos**, which provides support for decentralized projects and smart contracts. The flexibility of the platform and its modular software clients make sure the platform is easily adaptable to developers. Recent upgrades on Tezos have further improved its performance quality and the size limit on Tezos smart contracts.

# [Conclusion](#toc.xhtml#s229a)

And there was all the basic information that will get you started on your way to becoming a certified blockchain architect. In this chapter, we found out what primary skills you require to become a blockchain architect, how you can get the necessary certification, and finally, the path to laying the groundwork to develop your own blockchain architecture. Now, in the upcoming chapter, we will be finding out some more about a blockchain's architecture-regarding programming languages and libraries, to be specific.

# [Questions](#toc.xhtml#s230a)

1.  **What are some necessary skills a blockchain architect is required to have?**
    
    Knowledge about cryptography, smart contract, multiple programming languages, web development, and extensive knowledge of data structures.
    
2.  **Name two programming languages used in smart contract development.**
    
    Solidity, JavaScript.
    
3.  **What are the three basic kinds of blockchain architecture?**
    
    Public, private, and consortium.
    
4.  **What is a blockchain consensus mechanism?**
    
    A consensus mechanism helps the blockchain maintain a distributed ledger in real time, and whatever data is to be committed to the blockchain is decided by the consensus algorithm.
    
5.  **What are some types of blockchain consensus mechanisms a blockchain architect can choose from?**
    
    Proof of work, proof of stake, DPos, PoA, and PoC.
    
6.  **How is a Delegated Proof of Stake blockchain different from an average Proof of Stake blockchain?**
    
    On a DPoS blockchain, a user can stake their tokens and earn the right to vote for a certain number of delegates.
    
7.  **How does the Proof of Activity consensus mechanism combine features of Proof of Work and Proof of Stake blockchains?**
    
    Not much is clear from the chapter.
    
8.  **What are some necessary conditions a blockchain architect should keep in mind when selecting a blockchain platform for project development?**
    
    DLT technology, consensus algorithm, smart contract development, and so on.
    

# [Key terms](#toc.xhtml#s231a)

*   **Public Blockchain Architecture:** This is the most decentralized kind of blockchain architecture and all participating nodes on a public blockchain are given access to the data stored on the chain.
*   **Private Blockchain Architecture:** These systems are managed and accessed only by a group of authorized users.
*   **Consortium Architecture:** These blockchains can consist of users from multiple organizations and the system is managed by selected users.

# [CHAPTER 11](#toc.xhtml#c11)

# [Blockchain Architecture—Languages and Libraries - Part 1](#toc.xhtml#c11)

# [Introduction](#toc.xhtml#s232a)

In the previous chapter, we learned about the necessary skills you need to build, certification courses you need to take to build a career as a blockchain architect, some blockchain platforms you can use to develop your blockchain application, and more. Now that the groundwork is out of the way, it is time to find out more about the different programming languages we discussed very briefly in the previous chapter. Therefore, in this chapter, we go through the fundamentals of some well-known programming languages and some essential components of programming languages.

# [Structure](#toc.xhtml#s233a)

The following topics will be covered in this chapter:

*   Popular programming languages:  
    *   Python
    *   Java
    *   C++
    *   Golang
    *   Solidity
    *   Vyper
*   Flowcharts
*   Pseudocode
*   Programming language libraries
*   Summary
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s234a)

In this chapter, we have put together the essentials regarding six very well-known programming languages, which are Python, Java, C++, Golang, Solidity, and Vyper. All six of these languages are broadly used by blockchain professionals to fabricate various aspects of the applications they build. We hope this chapter will help you understand why these languages can prove to be beneficial to learn and also help you decide which ones you want to learn first. Without further ado, let us get into the chapter.

# [Popular programming languages](#toc.xhtml#s235a)

As you must already know, a programming language is a language used in computer programming to implement different algorithms and to produce certain intended outputs. Now that the definition is out of the way let us get into the detailed discussions of some programming languages blockchain professionals use often.

# [Python](#toc.xhtml#s236a)

Python, as mentioned in the previous chapter, is a super easily readable language, as its syntax is very similar to that of the English language. The programming language was created back in the 1980s by Guido van Rossum.

Python is a high-level, interpreted, object-oriented, open-source programming language with a broad range of applications. The high-level, built-in data structures of Python, along with dynamic typing and binding, make it a perfectly suitable language for Rapid Application Development and for connecting existing applications together. Furthermore, Python supports modules and packages, which facilitates both program modularity and the reuse of codes.

Python has been used in, aside from blockchain applications, industries such as engineering, data analytics, machine learning, artificial intelligence, and computational science. Indeed, many of the major websites in the current time have been created with Python, such as Instagram, Google, Reddit, Quora, Spotify, and YouTube.

There are quite a few reasons as to why Python's popularity among developers only keeps increasing with every passing day. These factors include the following:

*   Python is simple to learn but has widespread usage, and therefore, it is good for beginners and experienced professionals alike.
*   Portability is one of the aspects that makes Python incredibly well-used.
*   Python provides increased productivity compared to most other programming languages in business right now. As there is no compilation step, the edit-test-debug cycle for Python happens to be super-fast. Debugging a Python program is fairly simple too; the fastest way to debug a Python program is to add a few print statements to the source.
*   Python has quite a huge collection of libraries for new users to work with, aside from the extensive standard library that is available free of charge on most major platforms and can also be freely distributed.

# [Python code example](#toc.xhtml#s237a)

**Python program to add two numbers**: A user is first asked for two numbers, and the input is scanned with the `input()` function and stored in the two variables number1 and number2. Now, these two variables are added using the arithmetic operator "`+`", and the result is then stored in the variable sum.

Here is the Python program for adding two numbers:

`# Python3 program to add two numbers`

`num1 = input()`

`num2 = input()`

`# Adding two numbers`

`sum = num1 + num2`

`# printing values`

`print("Sum of {0} and {1} is {2}" .format(num1, num2, sum))`

# [Java](#toc.xhtml#s238a)

Java, as we have learned in the previous chapter, is another one of the oldest programming languages, along with Python. Java was developed by James Gosling from Sun Microsystems, and the language was released back in 1995 as one of the core elements of Sun Microsystems' Java platform. Gosling made Java with a syntax that is quite similar to that of C and C++, so if you know C or C++, you can learn Java with relative ease and vice versa.

Java was designed by Gosling as a high-level, class-based, general-purpose, and object-oriented programming language; it was made so that it had very few implementation dependencies. Java applications are usually compiled to a bytecode so that they can run on any JVM or Java Virtual Machine. Moreover, Java code, once written, can be run on all platforms with Java support without any need for rewriting; this particular feature of Java is known as WORA or "Write Once, Run Anywhere".

The Java runtime provides the language with some exclusive features that are not usually available in other traditional programming languages, such as reflection and runtime code modification. Another key feature of Java is its large and exuberant standard library.

# [Java code example](#toc.xhtml#s239a)

**Java program to add two numbers:** The following program takes two numbers entered by a user, and then calculates the sum, and proceeds to print it.

Here is the Java program for adding two numbers:

`import java.util.Scanner;`

`public class AddTwoNumbers2 {`

`public static void main(String[] args) {`

`int num1, num2, sum;`

`Scanner sc = new Scanner(System.in);`

`System.out.println("Enter First Number: ");`

`num1 = sc.nextInt();`

`System.out.println("Enter Second Number: ");`

`num2 = sc.nextInt();`

`sc.close();`

`sum = num1 + num2;`

`System.out.println("Sum of these numbers: "+sum);`

`}`

`}`

# [C++](#toc.xhtml#s240a)

As mentioned before, the syntax of the programming language C++ is quite similar to that of Java, even though the latter has fewer low-level facilities than the former. However, due to the similarities, if you know Java, it becomes very easy for you to learn and switch to C++, and vice versa.

C++ is an object-oriented, general-purpose, and cross-platform programming language that is used by developers to design high-performance applications and protocols across industries. The programming language was created by Bjarne Stroustrup as an extension to the popular programming language C. The language has expanded and been updated majorly several times, and the C++ we have currently come with generic, object-oriented, functional features, as well as the ability for low-level memory manipulation. Indeed, one of the primary things that are great about C++ is that the language gives programmers a pretty high level of control over system resources and memory.

C++ was designed, so it is especially oriented towards system programming and embedded, resource-constrained software and large systems, with performance, deftness, and flexible usability being some of the aspects the design of the language focuses on. C++ is used pretty widely in today's time and is nearly always implemented as a compiled language. The programming language provides programs with a clean structure and lets users reuse a particular code. Furthermore, C++ is portable, and applications made with C++ can be adapted to several platforms that support the language.

# [C++ code example](#toc.xhtml#s241a)

**C++ program to add two numbers**: A user is first asked for two numbers, and the numbers are stored in the two variables `firstNumber` and `secondNumber`. These two variables are added using the "+" operator, and the result is then stored in the variable `sumOfTwoNumbers`.

Here is the C++ program for adding two numbers:

`#include <iostream.h>;`

`#include <stdio.h>;`

`using namespace std;`

`int main()`

`{`

`int firstNumber, secondNumber, sumOfTwoNumbers;`

`cout << "Enter two integers: ";`

`cin >> firstNumber >> secondNumber;`

`// sum of two numbers in stored in variable sumOfTwoNumbers`

`sumOfTwoNumbers = firstNumber + secondNumber;`

`// Prints sum`

`cout << firstNumber << " + " << secondNumber << " = " << sumOfTwoNumbers;`

`return 0;`

`}`

# [Golang](#toc.xhtml#s242a)

The Go programming language is a procedural, sturdy, and general-purpose programming language. The language was actually developed back in 2007 by Google employees Robert Griesemer, Rob Pike, and Ken Thompson; however, Go was only launched in 2009 as an open-source programming language. With the Go language, programs are fabricated with the use of packages so as to maintain efficient management of dependencies. At its core, the Go programming language is an effort to bring together the ease that comes from programming using an interpreted, dynamically typed language with both the efficiency and security of a statically typed and compiled language. Plus, the Go language also works to be modern and provides support for multicore and networked computing.

Compared to most of its contender programming languages, Go is quite concise and simple to interact with. Go also comes with concurrency assistance—as it allows more than one process to run at once and yet smoothly. The Go programming language's compilation time is also very less, so it provides super quick outcomes, and of course, Go also has a rich standard language library. Moreover, garbage collection is another integral feature of the Go language; Go provides users with a whole lot of control over the memory allocation procedure, and the language has managed to drastically reduce latency in the latest versions of the garbage collector application.

# [Golang code example](#toc.xhtml#s243a)

**Golang program to add two numbers**: Again, a user is asked to provide two numbers. The first value is stored in variable a, and the second value is stored in variable `b`. These two variables are then added and stored into a third and final variable.

Here is the Golang program for adding two numbers:

`package main`

`import (`

`"fmt"`

`)`

`func add_values(a int, b int) int {`

`var c = a + b`

`return c`

`}`

`func main() {`

`var a, b, c int`

`fmt.Println("Enter 1st Number: ")`

`fmt.Scan(&a)`

`fmt.Println("Enter 2nd Number: ")`

`fmt.Scan(&b)`

`c = add_values(a, b)`

`fmt.Printf("Sum: %d \n", c)`

`}`

Now that we have learned about four of the languages programmers use across numerous industries and their associated libraries, we would like to introduce two programming languages to you that are used exclusively in the blockchain—the Ethereum blockchain, in particular, and there is a good chance you have heard of one or both of them, among Solidity and Vyper.

On top of the Ethereum blockchain, smart contracts can be programmed using languages that are developer-friendly; this is because the syntaxes for these languages share a lot of similarities with Python and other curly-bracket languages (a programming language whose syntax uses curly brackets to enclose blocks of code). Therefore, if you are experienced in using one or more of the popular general programming languages, there is a good chance that you will be able to grasp smart contract programming languages on Ethereum with comparative ease. Vyper and Solidity are two of the incredibly active and consistently maintained programming languages for Ethereum smart contracts, and both of them target the EVM or the Ethereum Virtual Machine. Now, let us jump into some details regarding both these languages.

# [Solidity](#toc.xhtml#s244a)

Solidity is an object-oriented, high-level programming language for creating and integrating smart contracts within the Ethereum ecosystem. Solidity is a curly-bracket language that is quite visibly influenced by mainstream programming languages like C++ in particular, but also Python, and JavaScript. Solidity also loosely borrows its syntax from the languages C and JavaScript.

The Solidity language is statically typed, so the type of a variable is known at the time of compilation; the language supports inheritance (so one can extend other smart contracts), language libraries, and complicated user-defined types, among other things. Solidity lets a user develop smart contracts for varied use cases—for instance, voting, auctions, crowdfunding, and multi-signature wallets.

Solidity is a very good option for you if you are a beginner to the world of programming languages and intend to join the blockchain industry since this particular language has a relatively simpler syntax, and the developer community that has built up surrounding the language is already quite huge, so you would have a lot of help should you ever get stuck or have queries.

**Solidity program to add two numbers:** Again, a user is asked to provide two numbers on the interface. Then on clicking the add button, the sum gets displayed.

`contract gfgMathPlus`

`{`

`// Declaring the state variables`

`uint firstNo ;`

`uint secondNo ;`

`// Defining the function to set the value of the first variable`

`function firstNoSet(uint x) public`

`{`

`firstNo = x;`

`}`

`// Defining the function to set the value of the second variable`

`function secondNoSet(uint y) public`

`{`

`secondNo = y;`

`}`

`// Defining the function to add the two variables`

`function add() view public returns (uint)`

`{`

`uint Sum = firstNo + secondNo ;`

`// Sum of two variables`

`return Sum;`

`}`

`}`

# [Vyper](#toc.xhtml#s245a)

This one is a contract-oriented, Pythonic programming language. Vyper is a strongly typed programming language and comes with a small and easily understandable compiler code. Compared to Solidity, Vyper has comparatively fewer features; instead, this programming language aims to make smart contracts more secure and more easily auditable.

As mentioned before, one of Vyper's primary goals is to strengthen the security aspect of smart contracts. Vyper also intends to make the language and the compiler implementation much simpler. What is more, Vyper prioritizes auditability and makes the written code easier for readers than for writers, so it is a very friendly language to users who have low or zero prior experience with Vyper in particular and programming languages in general. The Vyper code is made to be largely human-readable, and it is very difficult to create misleading code in Vyper.

Integral properties of the Vyper programming language include bounds and overflow checking and the support for signed integers and decimal fixed point numbers. Further, the tools on Vyper make it possible to calculate an accurate upper bound for the amount of gas consumption of a certain Vyper function call. Plus, Vyper has limited support for pure functions, and Vyper does not support features like modifiers, inheritance, inline assembly, function overloading, operator overloading, recursive calling, infinite-length loops, and binary fixed points.

Once you are familiar with the programming language Python, it should be incredibly easy for you to learn Vyper and get started with smart contract creation. The fewer features of Vyper make sure the language is perfect for the quick prototyping of any ideas.

So now that we know some basics of all six of the programming languages we are discussing in this chapter, in the next section, we will learn about some of the integral components of programming languages—namely, flowcharts, pseudocode, and programming language libraries.

# [Flowcharts](#toc.xhtml#s246a)

Flowcharts are basically graphic representations of the flow of a particular program or algorithm. Programmers use flowcharts as an easier way to lay down the solution to a problem. There are four shapes usually drawn in a flowchart, which are connected according to the flow of information in a particular algorithm.

The four basic shapes in a flowchart are the following:

*   **Oval**, used to signify the start, stop, and halt. This is both the first and last symbol in a flowchart.
*   **Parallelogram**, shows input/output. Program instructions that carry input and output are represented with this symbol.
*   **Rectangle**, for calculations and any arithmetic instructions.
*   **Diamond**, used to show selection structures and decision-based operations.

In a flowchart, these four shapes are connected with arrows.

![](images/Figure-11.1.jpg)

**Figure 11.1:** Basic components used in a flowchart

# [Flowchart example](#toc.xhtml#s247a)

Now, we will see the description of a program, followed by a flowchart that describes the program and a particular code in the programming language Python that corresponds to it.

**Program description:** The program starts. Now it asks a certain user for a number. If the given number is greater than zero, the program has to print "`Greater than 0`", and then it ends.

**Flowchart:**

![](images/Figure-11.2.jpg)

**Figure 11.2:** Basic flowchart to print a message based on a condition

Python code corresponding to this flowchart:

`# start`

`num = input("Enter a number: ")`

`num = float(num)`

`if num>0:`

`print("Greater than 0")`

`# end`

# [Pseudo code](#toc.xhtml#s248a)

Coming to pseudocode, it is the term for a method that also lets a programmer represent the implementation of an algorithm, but in a vastly different way than a flowchart. Pseudocodes are false codes written in plain English for actual codes in various programming languages. Usually, algorithms are shown with pseudo codes so they can be understood by any programmer regardless of the extent of their knowledge of programming languages. Pseudo codes, therefore, do not have any syntax like programming languages and cannot be compiled or interpreted by the computer in the usual fashion.

# [Example of pseudocode](#toc.xhtml#s249a)

In the following, we will see a code in the language Java, and then we will see it turned into a pseudocode that can be easily understood by new and inexperienced programmers.

Java code:

`// This program calculates the Lowest Common multiple`

`// for excessively long input values`

`import java.util.*;`

`public class LowestCommonMultiple {`

`private static long`

`lcmNaive(long numberOne, long numberTwo)`

`{`

`long lowestCommonMultiple;`

`lowestCommonMultiple`

`= (numberOne * numberTwo)`

`/ greatestCommonDivisor(numberOne, numberTwo);`

`return lowestCommonMultiple;`

`}`

`private static long`

`greatestCommonDivisor(long numberOne, long numberTwo)`

`{`

`if (numberTwo == 0)`

`return numberOne;`

`return greatestCommonDivisor(numberTwo, numberOne % numberTwo);`

`}`

`public static void main(String args[])`

`{`

`Scanner scanner = new Scanner(System.in);`

`System.out.println("Enter the inputs");`

`long numberOne = scanner.nextInt();`

`long numberTwo = scanner.nextInt();`

`System.out.println(lcmNaive(numberOne, numberTwo));`

`}`

`}`

Pseudo code for the preceding code:

`This program calculates the Lowest Common multiple`

`for excessively long input values`

`function lcmNaive(Argument one, Argument two){`

`Calculate the lowest common variable of Argument`

`1 and Argument 2 by dividing their product by their`

`Greatest common divisor product`

`return lowest common multiple`

`end`

`}`

`function greatestCommonDivisor(Argument one, Argument two){`

`if Argument two is equal to zero`

`then return Argument one`

`return the greatest common divisor`

`end`

`}`

`{`

`In the main function`

`print prompt "Input two numbers"`

`Take the first number from the user`

`Take the second number from the user`

`Send the first number and second number`

`to the lcmNaive function and print`

`the result to the user`

`}`

# [Programming language libraries](#toc.xhtml#s250a)

For the uninitiated, a library in a programming language is simply a collection of prewritten code that a programmer can use to optimize various tasks. The many language libraries out there serve a range of purposes, and it would help you, as a blockchain architect, to know which ones will be the best for your project. So, here we discuss some of the more popular language libraries for Python, Java, C++, and Golang, apart from the standard ones.

# [TensorFlow](#toc.xhtml#s251a)

Developed by Google in collaboration with the Brain Team, TensorFlow is a well-known open-source library that has been used in almost every Google application for machine learning (for example, Google Voice Search and Google Photos are two prominent use cases of TensorFlow). **Python** and **C++** are the two primary languages of TensorFlow.

This particular library helps developers in writing new algorithms, which involve a large number of tensor operations; TensorFlow is also optimized for speed, and it uses techniques like XLA to complete quick linear algebra operations. TensorFlow is also very flexible in its operability and is quite easily trainable on both the CPU and GPU for distributed computing.

TensorFlow also offers pipelining—a user can train multiple neural networks and GPUs, making the models efficient enough for large-scale systems. An additional benefit of TensorFlow is that, since it was developed by Google, the library already has quite a sizable team of software engineers who work to implement new upgrades constantly.

# [PyTorch](#toc.xhtml#s252a)

PyTorch is another machine learning library based on Torch (that is an open-source machine library that is implemented in the programming language C) that lets users perform tensor computations with GPU acceleration, create computational graphs and calculate gradients automatically. PyTorch comes with rich APIs that help with solving application issues associated with neural networks.

Since its inception back in 2017, PyTorch has emerged as one of the toughest contenders of TensorFlow, as they both serve similar purposes and share some similar features. Properties of PyTorch include a hybrid front-end that provides both easy usability and flexibility in eager mode, all the while effortlessly shifting to graph mode for speed, optimization, and increased functionality in C++ runtime environments. However, it is important to remember that despite the C++ framework, PyTorch was built to be integrated with Python so it can be used alongside other popular language libraries.

Just like TensorFlow, PyTorch also has an active and loyal community of users who have come together to build a wide ecosystem of tools and libraries for expanding PyTorch and backing development in various areas like computer vision and reinforcement learning.

# [Numpy](#toc.xhtml#s253a)

Numpy is one of the more popular machine-learning libraries in the Python language. Numpy is used by other libraries like TensorFlow quite often to execute various operations on Tensors.

Important features of Numpy include the array interface (also known as the array protocol), which was developed back in 2005 so as to allow array-like Python objects to make use of one another's data buffers if need be. Further properties of the Numpy library consist of the fact that it is one of the more interactive and easier-to-use libraries, it helps the users grasp alien concepts of coding in the simplest possible way and also simplifies complex mathematical implementations, and Numpy also has a significant community of users.

# [Scikit-Learn](#toc.xhtml#s254a)

This one is a Python language library closely associated with the previously mentioned Numpy and is said to be one of the top libraries if a user is handling some complex data. The Scikit-Learn library is made up of a large number of algorithms to help users implement various machine learning and data mining operations such as regression, reducing dimensionality, model selection, clustering factor analysis, principal component analysis, and classification.

The many interesting and helpful features of Scikit-Learn include cross-validation, unsupervised learning algorithms, and feature extraction (used to extract various features from images and text).

# [Keras](#toc.xhtml#s255a)

Keras has become very popular among developers as it has proven to be one of the more fun machine-learning libraries in Python, even though it is relatively slower than its contemporaries. Keras has been used in many popular applications we make use of on a daily basis, such as Netflix, Uber, Yelp, and many more. Notably, Keras has also been adopted by researchers at organizations like CERN and NASA.

Keras is totally Python-centered, and therefore, it is quite easy to debug and explore. Keras runs effortlessly on both CPU and GPU, just like TensorFlow. The library also supports most of the models of a neural network, and these models can further be put together to create some more complex models. Keras is also very expressive and flexible due to being modular in nature, and it has proven effective for innovative research, as proven by its use in organizations like NASA.

# [Google Guava](#toc.xhtml#s256a)

Again a library developed by Google, Google Guava is another well-known and broadly utilized general-purpose Java language library. This open-source project was initially designed by software engineer and author Joshua Bloch, but with time, engineers outside of Google have also come to contribute to the platform. Google Guava is modular and consists of quite a few distinct libraries, and the platform comes with essential utilities such as string manipulation, hashing, I/O utils, concurrency utilities, graph libraries, and a lot more.

Primary properties of Google Guava consist of the Java collections framework extension, caching, hashing, I/O utilities, and concurrency assistance, along with string utilities, and many more.

# [Apache Commons](#toc.xhtml#s257a)

This one is widely popular across industries and extends many of the Java Core libraries; in fact, Apache Commons can almost be called the unofficial Java Standard library enhancement at this point. Even though it shares many of Google Guava's features and the software design for Apache Commons is frankly not as good as that of Google Guava's, it is still worth looking into as a blockchain architect. Further, Apache Commons consists of 43 modular libraries that encompass many domains like collections, math, classes, database, caching, and I/O utils.

Aside from the extension of the Java collections framework, features of Apache Commons include the mathematics and statistics components, JDBC helper, Java classes, I/O utilities, and logging utilities.

# [Jackson](#toc.xhtml#s258a)

Jackson comprises a suite of data processing libraries for the programming language Java. You would know that in software development, one has to process differently formatted data; you have to load or save or transfer data in various formats. While there are quite a few common data formats (such as XML, Avro, YAML, CSV, Protobuf, BSON, Smile, and CBOR), JSON is the default format for the exchange of data in modern software development. Now, the Jackson platform is essentially the de facto streaming JSON compiler generator library. However, Jackson also supports additional data formats like the ones mentioned previously and various third-party data types such as Joda, Guava, PCollections, Yandex Bolts, GeoJSON, Lombok, MongoDB, and many more.

Moreover, the Jackson platform also comes with features like data-binding and annotations. The Jackson annotations can help you turn POJO (Plain Old Java Object) into data or vice versa; in fact, if you have to work with data format—which is a necessity in a lot of cases, Jackson is a language library you must be familiar with. Jackson is highly modular and comes with core modules that support the JSON data format and offer basic functionalities and various extension modules. There are also special modules for other data formats such as CBOR, Smile, XML, YAML, Protobuf, CSV, Avro, Ion, and more, as mentioned before.

# [JAXB](#toc.xhtml#s259a)

We mentioned the data type XML while talking about the Jackson language library. XML is a prominent data format that offers relatively stricter validation, storage support, and the transportation of data. The Java standard language library supported the XML data format up to Java 8; however, since Java 9 came about, the XML processing capabilities have been moved from the standard Java library to a specific, separate language library called JAXB. The JAXB platform comes with every functionality you might need while working with the XML data type in the Java language. JAXB offers an effective way of moving between the XML and Java codes. Plus, the platform also helps with annotation-based data binding.

The main features of the JAXB library include its support for all W3C XML Schema features and of course, annotation-based Java-to-XML data binding.

# [Mockito](#toc.xhtml#s260a)

In software development, unit/integration testing is a super important section of the process. It often happens that you want to test out a single class (SUT), but it relies on some heavyweight classes or external functionalities like database operations or I/O functionalities. In a case like this, one good way to write the unit/Integration test is Mocking. This way, one can mock the operations of other external service calls and focus entirely on the particular class they are required to test out. Mockito is a Java language library that is broadly used by developers to serve the mocking purpose. Mockito comes with an easy and clean API and helps you keep your unit/integration tests neat. From a small project to a complex and elaborate one, Mockito can prove to be of help with everything.

Prominent properties of the Mockito platform include the smart and simple API, a simplified stubbing model, partial mocking via spy, annotation-based mock/spy injection, and a behavior-driven development syntax with the use of BDDMockito.

# [SFML, or the Simple and Fast Multimedia Library](#toc.xhtml#s261a)

The SFML has C++ as its primary programming language. The Simple and Fast Multimedia Library is a programming language library that allows the development of images and sound effects and is able to build a connection between two or more computers.

# [GORM](#toc.xhtml#s262a)

This Go language library is used by developers to convert data between two different systems in the case that they are not compatible with each other. This super effective and developer-friendly tool manages the aforementioned conversion with its RAW SQL and SQL builders, the expandable write plugins based on GORM callbacks for total customization, and its auto migration tools. Moreover, every feature of the GORM platform is accompanied by its tests, so users can bring new implementations—if they want, without messing up the whole system in case it backfires.

# [Go Kit](#toc.xhtml#s263a)

Go Kit is a Go library from Github that specializes in support for Go-related microservices. The instrument works to fill various gaps in operations like infrastructure integration, program design, RPC safety, and system observability. Go Kit allows developers to adopt microservices with ease by providing them with guidance to create various distributed protocols that create solutions for commonplace issues. What is more, this particular language library being slightly opinionated, can be customized by developers with ease so as to suit their particular project.

# [Vegeta](#toc.xhtml#s264a)

Vegeta is another well-known Go language library; this one is quite a versatile tool that aids with HTTP load testing. Indeed, Vegeta was developed with the priority of facilitating the testing of HTTP services with a consistent request rate.

# [Fuzzy](#toc.xhtml#s265a)

Fuzzy is a dependency-free Go language library that, true to its name, helps to match fuzzy strings. The library is specially optimized for file names and code symbols. The Fuzzy platform facilitates the fast and intuitive matching of fuzzy strings lightning fast. The tool is Unicode aware and is capable of parsing VScode, IntelliJ IDEA, Sublime Text, and more.

# [Cli](#toc.xhtml#s266a)

Cli is a Go language library that provides developers with swift and efficient tools for creating distributable command-line apps for the Go programming language. The Cli platform renders the act of generating flags easy; for instance, bash-completion routines and generated help texts.

# [Conclusion](#toc.xhtml#s267a)

And that was a brief introduction to six of the most integral programming languages a blockchain architect can learn and some of the essential components of programming languages. We do hope this helps you understand the basic features of the languages, along with their backgrounds, and also helps you pick which ones you would like to learn and use for yourself. Now, in the upcoming chapter, we will be looking into six more of these programming languages, which are C#, JavaScript, Simplicity, Rholang, eWASM, and Ethereum Bytecode.

# [Questions](#toc.xhtml#s268a)

1.  **Which programming languages have a syntax similar to that of Java's?**
    
    C and C++
    
2.  **What are some similarities between the programming languages Solidity and Vyper?**
    
    Solidity and Python are both similar to Python and are used in smart contract development.
    
3.  **Differentiate between Solidity and Vyper.**
    
    Solidity is object-oriented, whereas viper is contract oriented.
    
4.  **Why is Vyper a good programming language to learn for programmers with little to no experience?–**
    
    Because viper code is human-readable and it is very difficult to create misleading code in Vyper.
    
5.  **What is a flowchart?**
    
    Flowcharts are graphic representations of the flow of a particular program or an algorithm.
    
6.  **What are the primary symbols used in a flowchart, and what do they stand for?**
    
    Oval: to show the start, stop, or halt state of the program
    
    Parallelogram: shows input/output
    
    Rectangle: for arithmetic calculations
    
    Diamond: for making a selection
    
7.  **What is pseudo code?**
    
    Pseudocodes are false codes written in plain English for actual codes in various programming languages.
    
8.  **What is a programming language library?**
    
    Already written code that accomplishes some tasks in that language.
    
9.  **What are the primary programming languages on the TensorFlow platform?**
    
    Python and C++.
    

# [Key terms](#toc.xhtml#s269a)

*   **Programming Languages:** A programming language is a language used in computer programming, to implement different algorithms and to produce certain intended output.
*   **Pseudo Code:** These are false codes written in plain English that stand for actual codes in some programming languages.
*   **Programming Language Library:** A programming language library comes up with already written code in the same language so developers have an easier time.

# [CHAPTER 12](#toc.xhtml#c12)

# [Blockchain Architecture—Languages and Libraries - Part 2](#toc.xhtml#c12)

# [Introduction](#toc.xhtml#s270a)

As a continuation of the previous chapter, in this chapter too, we have chosen six more programming languages to discuss, the ones we consider to be important for a blockchain architect to be familiar with.

# [Structure](#toc.xhtml#s271a)

The following topics will be covered in this chapter:

*   C#
*   JavaScript
*   Simplicity
*   Rholang
*   eWASM
*   Ethereum Bytecode
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s272a)

The objective of this chapter is to go through the previously mentioned six languages one by one.

# [C#](#toc.xhtml#s273a)

The C# programming language was fabricated by Microsoft. The type-safe programming language allows developers to build a range of applications that run in .NET, which is a digital execution system named after CLR or the Common Language Runtime and a set of class libraries. The language C# bears great similarity to what is called the C family of programming languages, and even the languages Java and JavaScript have some common elements with C; therefore, developers possessing knowledge of any of these languages will be able to learn C# with ease.

The main objective of the C# language developers was to combine object-oriented functionality with a syntax like that of the language C. C#, which is pronounced as "See Sharp", has had a huge part in the developments of various Windows applications. At the moment, C# is quite popular among developers to create mobile apps, and you can find C# courses being offered across a great number of portals.

Features of the C# programming language include the following:

*   The garbage collection feature works to automatically reclaim memory previously used by unreachable and unused objects.
*   Nullable types provide protection against any variables that do not refer to any particular allocated object.
*   Exception handling allows for a structured and comprehensive method of error detection and recovery.
*   Lambda expressions provide support for functional programming techniques.
*   The LINQ or the Language Integrated Query syntax makes up a common pattern so programmers can work with data from quite a few sources.
*   Further, the language support for asynchronous operations provides programmers with the syntax for building a distributed system.
*   The C# language comes with a unified type system. Every C# type is inherited from a singular root object type. All C# types share a set of general operations. Values of any of these types can be kept, moved, and operated upon in a consistent fashion.
*   What is more, the C# language backs both a user-defined reference type and a value type.
*   C# allows the dynamic allocation of objects and also in-line storage for any lightweight structures.
*   The C# language also provides iterators, which allow the implementers of collection classes to outline custom behaviors for client code.
*   Finally, C# focuses on versioning so as to be compatible with the gradual evolution of any programs and libraries.

At the moment, C# is quite popular among developers to create mobile apps. Other fields that frequently use C# include game development and VR. You can find C# courses being offered across a great number of portals over the internet.

# [C# code example](#toc.xhtml#s274a)

**C# program to determine the sum of n number of digits**: The program for the sum of any number of digits in the C# programming language can be written only with the help of a loop and mathematical operations.

Here is the C# program for determining the sum of n number of digits:

`using System;`

`public class SumExample`

`{`

`public static void Main(string[] args)`

` {`

`int n,sum=0,m;`

`Console.Write("Enter a number (between 0 and 2,147,483,647): ");`

`n= int.Parse(Console.ReadLine());`

`while(n>0)`

`{`

`m=n%10;`

`sum=sum+m;`

`n=n/10;`

`}`

`Console.Write("Sum is= "+sum);`

`}`

`}`

# [JavaScript](#toc.xhtml#s275a)

JavaScript—often called JS in short—is a lightweight, interpreted, and often just-in-time compiled programming language that has first-class functions. The programming language is prototype-based, multi-paradigm, single-threaded, and dynamically typed, and it has curly-bracket syntax.

Now, JavaScript probably reminds you of the Java programming language we discussed in the last chapter. Both the languages Java and JS are registered trademarks of Oracle in the USA and other countries. It is to be noted that although there are quite a few similarities between JavaScript and Java language, including language name and even the standard libraries, the two programming languages are not to be confused with each other, as they differ quite a lot in both design and features; they possess quite a distinct syntax, semantics, and use cases too.

The two standards for the JavaScript programming language are the ECMAScript Language Specification or ECMA-262 and the ECMAScript Internationalization API specification or ECMA-402.

As a multi-paradigm language, The JS programming language provides support for event-driven, functional, and imperative programming styles. JavaScript comes with APIs for working with dates, text, regular expressions, standard data structures, and the DOM or Document Object Model.

JavaScript engines originally started out as the programming language behind several Web browsers; indeed, aside from HTML and CSS, JavaScript is one of the integral technologies at the core of the World Wide Web. At the moment, more than 97% of websites use JS on the client-side for Web page behavior. A majority of Web browsers also has a devoted JavaScript engine to execute the code on a user's device.

In addition to Web browsers, JavaScript engines are now core to other software systems as well, such as various servers and a broad assortment of applications. JavaScript has essentially come to be the front-end Web development counterpart to Python's backend development. Well-used social media websites such as Gmail, Twitter, Facebook, and YouTube make use of JS in the fabrication of engaging and innovative user interfaces.

A couple of the JavaScript language's better-known front-end frameworks are Angular JavaScript and React JavaScript. Angular JS is mostly used to create dynamic Web apps, and React JS is a JS library that is used in structuring user interface components.

# [JavaScript code example](#toc.xhtml#s276a)

**JavaScript program to determine the sum of two numbers entered by the user**: A user is first asked for two numbers, and then the following code is used to calculate the sum of the two numbers.

Here is the JavaScript program for determining the sum of two numbers entered by the user. You can try to run this on an online javascript editor like **[https://playcode.io/javascript/](https://playcode.io/javascript/)**

`// store input numbers`

`const num1 = parseInt(prompt('Enter the first number '));`

`const num2 = parseInt(prompt('Enter the second number '));`

`//add two numbers`

`const sum = num1 + num2;`

`// display the sum`

``console.log(`The sum of ${num1} and ${num2} is ${sum}`);``

Now, after C# and JavaScript, we will be taking a look at some programming languages used exclusively in blockchains. As blockchain architects, the four languages mentioned in the upcoming parts of the chapter will definitely prove important for you to be familiar with. The blockchain languages we will be talking about are Simplicity, Rholang, eWASM, and Ethereum Bytecode. Without further ado, let us take a look at Simplicity first.

# [Simplicity](#toc.xhtml#s277a)

Simplicity, a programming language specifically designed by Blockstream for blockchain applications, is a typed, combinator-based, functional language that does not have loops and recursion. A combinator-based functional language supports structured programming. Such languages act as a bridge between programmers and machine requirements for symbolic computation for a language and a machine architecture that does not have loops and recursion. Simplicity is a low-level programming language and machine model uniquely created for blockchain-based smart contracts. Simplicity, true to its name, has been designed to have simple semantics, which allows for static analysis and reasoning by formal methods.

The Simplicity language is defined by its implementation in the Coq proof assistant. Simplicity has formal denotational semantics laid down in Coq, which is a general-purpose software proof assistant.

Simplicity is made for direct execution, and it is more similar to assembler language than to traditional programming languages such as Python or Java. Simplicity empowers users to create formal proof of correctness for their smart contracts.

With Simplicity, its developers aimed to do away with the issues faced by most of its contemporary blockchain-specific languages, such as Bitcoin Script and Ethereum's EVM. Blockchains pose a number of challenges that traditional programming languages find difficult to solve; for example, on a blockchain, all users on the chain have to agree on the result of a particular computation in all environments. Every single party in a smart contract must be made aware of any and all probable results of a program at the beginning and the costs for the execution of their program for all possible inputs too.

Moreover, all users involved have to be capable of preventing any denial of service attacks that would take up too much memory or computation time.

As for languages designed for blockchains exclusively—like the aforementioned EVM—they face these challenges too. Very recently, an EVM upgrade failed while the testing was going on, as the newer implementations did not agree on the output of a particular computation.

However, Simplicity has been built to improve upon the limitations discussed previously—it comes with the flexibility and expressiveness for any computations you need while also not compromising on the security or costs of a smart contract.

Before Simplicity, blockchain programming languages were usually making tradeoffs between the aspects of expressiveness and reliability, and you could either build a smart contract that was unreliable but complex or one that, while reliable, was very basic. However, Simplicity allows developers to fabricate smart contracts that balance the two aspects smoothly.

Further, Simplicity comes with operational semantics, which is defined with an abstract machine known as the Bit Machine. The Bit Machine is used as an instrument for calculating the computational space and time that are required to evaluate a Simplicity program. Due to its Turing incompleteness, the Simplicity language is compliant with static analysis, which can be used to determine upper bounds on the computational resources required before execution.

Turing completeness refers to the capability of a programming language to replicate a Turing machine. By this, we mean that the language will run any program or solve any problem just like any Turing Machine does. If a programming language is incapable of doing so, we call it Turing incomplete.

You should note that even though Simplicity is Turing incomplete, the blockchain language can express any finitary function, which makes it perfectly suitable for developing smart contracts for a wide range of blockchain applications.

# [Simplicity code example](#toc.xhtml#s278a)

**Enum:** Solidity is a language that supports enumerables; they prove useful in modeling choice and keeping track of state. Enums can be declared outside of a smart contract.

Find the program as follows:

`// SPDX-License-Identifier: MIT`

`pragma solidity ^0.8.10;`

`contract Enum {`

`// Enum representing shipping status`

`enum Status {`

`Pending,`

`Shipped,`

`Accepted,`

`Rejected,`

`Canceled`

`}`

`// Default value is the first element listed in`

`// definition of the type, in this case "Pending"`

`Status public status;`

`// Returns uint`

`// Pending - 0`

`// Shipped - 1`

`// Accepted - 2`

`// Rejected - 3`

`// Canceled - 4`

`function get() public view returns (Status) {`

`return status;`

`}`

`// Update status by passing uint into input`

`function set(Status _status) public {`

`status = _status;`

`}`

`// You can update to a specific enum like this`

`function cancel() public {`

`status = Status.Canceled;`

`}`

`// delete resets the enum to its first value, 0`

`function reset() public {`

`delete status;`

`}`

`}`

Declaring and importing Enum:

*File which the enum is declared in:*

`// SPDX-License-Identifier: MIT`

`pragma solidity ^0.8.10;`

`// This is saved 'EnumDeclaration.sol'`

`enum Status {`

`Pending,`

`Shipped,`

`Accepted,`

`Rejected,`

`Canceled`

`}`

File which imports the enum above:

`// SPDX-License-Identifier: MIT`

`pragma solidity ^0.8.10;`

`import "./EnumDeclaration.sol";`

`contract Enum {`

`Status public status;`

`}`

# [Rholang](#toc.xhtml#s279a)

Next on our list of blockchain languages to be discussed in this chapter is Rholang, developed by RChain. Rholang is an open and scalable blockchain language for distributed systems. The blockchain language has been designed with two primary aspects in mind: speed and reliability. It is a behaviorally typed, concurrent programming language with a focus on the feature of message-passing and formally modeled by the ρ-calculus (which is a reflective, higher-order extension of the π-calculus).

While Rholang is a language initially designed to be used in integrating various protocols and smart contracts with a general-purpose blockchain, it can, in fact, be used in some other settings as well.

Rholang is a process-oriented language, which means all computation is done through the aforementioned message passing. These messages are passed on what are called channels, not very unlike message queues. The primary difference is that these channels act in a way more similar to bags or multisets instead of message queues, as there is not any implicit ordering on the messages. Every one of these channels has a name, and every one of the names, of course, denotes a unique channel.

Moreover, Rholang is fully asynchronous, which suggests that while the system allows you to read a message from a certain channel and then take certain actions in accordance with it, you are not capable of sending a message and taking action after it has been received—or at least you cannot do so without first waiting for an explicit acknowledgment message from the person who received the message.

Rholang is still in the early stage of its development.

# [eWASM](#toc.xhtml#s280a)

eWASM or Ethereum WebAssembly, is the new Ethereum 2.0's version of the older WebAssembly. eWASM is one of the recent innovations that Ethereum is integrating with Ethereum 2.0 so as to make way for a quicker, more scalable, and flexible platform that would allow developers to build more complex smart contracts and applications within the Ethereum ecosystem. Please refer to the following figure:

![](images/Figure-12.1.jpg)

**Figure 12.1:** Programming languages compile into WebAssembly  
**(Source:** [https://academy.ivanontech.com/blog/breaking-down-eth-2-0-ewasm-and-evm-explained](https://academy.ivanontech.com/blog/breaking-down-eth-2-0-ewasm-and-evm-explained))

WebAssembly was developed and defined by the World Wide Web Consortium (W3C), and the code is very compatible with modern browsers. This is because WASM is supported by several JavaScript engines and runtime environments, and therefore, it is executable in most modern browsers. WASM has a stack-based, low-level binary format that is small and can load and execute swiftly. Once a browser downloads a WASM code, it can very quickly turn the code into any machine's assembly.

Other programming languages, such as Golang, Rust, C, and C++, can compile directly into WASM too. WASM runs close to native speed on most systems and can adapt to any machine-level architecture quickly and with ease, making it even more high-performing.

Coming to the more recent eWASM or Ethereum WebAssembly, the team behind this upgraded code describes it in the following fashion:

*eWASM = WASM – nondeterminism (floating point) + metering + EEI methods (used to interact with Ethereum).*

Ethereum WebAssembly is developed in accordance with the World Wide Web standards and has more compilers as well as a broader range of developer tools when compared to the older WebAssembly. Plus, a good number of projects are already making use of eWASM, so it has developed a wide and diverse developer community.

Ethereum WebAssembly is still in the development stage, but the design goals for eWASM include creating an EVM transcompiler and a metering injector as an eWASM contract, developing an eWASM backend for the solc compiler, coming up with instructions and a library so as to help developers write smart contracts with ease in C and Rust, and laying down a clear specification of both the Ethereum interface and the Ethereum WebAssembly contract details.

Ethereum WebAssembly has already acquired native support from a majority of the important JavaScript engines such as Microsoft's Chakra engine (Microsoft Edge), Google's V8 engine (Node.js and Chromium-based browsers), and Mozilla's Spidermonkey engine (Firefox and Thunderbird). As for eWASM's non-browser implementations, the language provides support for the following: ml-proto, the OCaml reference interpreter; wasm-jit-prototype, an LLVM backend-using standalone VM; and wabt, a stack-based interpreter.

# [Ethereum Bytecode](#toc.xhtml#s281a)

Finally, the last blockchain language we will be talking about in this chapter is Ethereum Bytecode. Ethereum Bytecode is required when writing a smart contract within the Ethereum ecosystem. Now, while there are two basic types of bytecode on Ethereum, there are actually five different names in use to describe these two types. Please refer to the following figure:

![](images/Figure-12.2.jpg)

**Figure 12.2:** Writing contracts to Ethereum and Reading contracts from Ethereum  
**Source:** eiki on Medium

The terminology in association with Ethereum Bytecode in the Ethereum community adds to the complexity of the language. The five names used to describe Ethereum Bytecode among the developers and users are as follows:

*   Creation Bytecode
*   Runtime Bytecode
*   Bytecode
*   Deployed Bytecode
*   Init Code

Now, we will talk a little about what these five distinct names signify.

*   **Creation Bytecode:** This one is actually the bytecode most people are referring to when they say Ethereum Bytecode. Creation bytecode generates the runtime bytecode we will be discussing as follows. Creation bytecode includes the constructor logic and constructor parameters of a smart contract. The creation bytecode is the equivalent of the input data of the transaction, which creates a smart contract—given that the purpose of the transaction is to generate the smart contract, of course. 
    
    Creation bytecode works so that when one compiles a smart contract, the creation bytecode is generated for them.
    
    The creation bytecode can be retrieved on Ethereum by using Solidity's type information (**[https://solidity.readthedocs.io/en/v0.5.11/units-and-global-variables.html#type-information](https://solidity.readthedocs.io/en/v0.5.11/units-and-global-variables.html#type-information)**). The particular Solidity code to retrieve the code is `type(ContractName).creationCode.`
    
    Furthermore, the creation bytecode can be retrieved off-chain by the *getTransactionByHash* JSON RPC call.
    
*   **Runtime Bytecode:** Runtime bytecode is the particular code that describes the smart contract and is stored on-chain. However, since either the constructor logic or the constructor parameters of a smart contract are not relevant to the actual code that was used to generate the smart contract, a runtime bytecode does not include them. 
    
    The runtime bytecode for a smart contract can be retrieved on top of the Ethereum blockchain by using an assembly block and calling `extcodecopy(a)`. The hash of the runtime bytecode is returned from `extcodehash(a)`.
    
    This code can be retrieved on Ethereum using `type(ContractName).runtimeCode`. and as for off-chain retrieval, it can be done with the JSON RPC call, `getCode`.
    
*   **Bytecode:** Bytecode is actually an umbrella term that can mean either runtime bytecode or creation bytecode. However, it is to be noted that the term "bytecode" usually refers to the runtime bytecode.
*   **Deployed Bytecode:** This particular term is used only by truffle-generated ABIs and points exclusively to a smart contract's runtime bytecode.
*   **Init Code:** This term is sometimes used in lieu of the creation bytecode mentioned first, and so init code is also the one that generates the specific bytecode stored on top of the blockchain.

# [Conclusion](#toc.xhtml#s282a)

And that was all the basics you need to know regarding programming languages, blockchain languages, and their various aspects to start your journey to become a certified blockchain architect. In the upcoming chapter, we will be learning about another part of a blockchain's architecture: setting up the development environment.

# [Questions](#toc.xhtml#s283a)

1.  **Name some use cases of the C# programming language.**
    
    Creating mobile apps, game development, and VR
    
2.  **What are some advantageous features of the C# language?**
    
    Garbage collection, lambda expressions, LINQ support, and exception handling
    
3.  **What is the JavaScript language best known for?**
    
    For front end development
    
4.  **What challenges of a blockchain does Simplicity attempt to solve?**
    
    Simplicity tries to solve challenges such as—every single party in a smart contract must be made aware of any and all probable results to a program in the beginning and the costs for the execution of their program for all possible inputs too
    
5.  **How is Simplicity different from traditional programming languages?**
    
    Simplicity is turning incomplete
    
6.  **What is eWASM?**
    
    eWASM is one of the recent innovations that Ethereum is integrating with Ethereum 2.0 so as to make way for a quicker, more scalable, and flexible platform that would allow developers to build more complex smart contracts and applications within the Ethereum ecosystem
    
7.  **What is Ethereum bytecode? What are the primary terms associated with bytecode?**
    
    Ethereum Bytecode is required when writing a smart contract within the Ethereum ecosystem. Primary terms associated with it are as follows:
    
    *   Creation Bytecode
    *   Runtime Bytecode
    *   Bytecode
    *   Deployed Bytecode
    *   Init Code

# [Key terms](#toc.xhtml#s284a)

*   **eWASM:** eWASM is Ethereum 2.0's version of the older WebAssembly, and it is one of the recent innovations that Ethereum is integrating with Ethereum 2.0.

# [CHAPTER 13](#toc.xhtml#c13)

# [Blockchain Architecture—Setting Up Development Environment](#toc.xhtml#c13)

# [Introduction](#toc.xhtml#s285a)

To achieve your goal of becoming a blockchain architect, among many things, you must be aware of how to go about setting up the right environment for the development of your particular blockchain project. Since we have already learned about some integral programming languages and the various fundamental components associated with them in the past couple of chapters, it is time for us to find out how to create the perfect development environment as per the requirements of a certain blockchain application.

Therefore, in this chapter, we are going to dive deep into the basics of an IDE, some IDEs that might prove to be optimal for your needs, and a guide on how to pick the right IDE for your project. To top it all off, we will be taking a look at the REMIX Online IDE and finding out how to set up the Remix IDE for Solidity development.

# [Structure](#toc.xhtml#s286a)

The following topics will be covered in this chapter:

*   Objectives
*   IDEs—a Brief Intro
*   The various types of IDEs:
*   Choosing the right IDE for your project
*   Some well-known and widely used IDEs:  
    *   Eclipse
    *   MPLAB X
    *   Arduino IDE
    *   IntelliJ IDE
    *   Remix Online IDE
*   Setting up the online Remix IDE for solidity smart contract development
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s287a)

As a blockchain architect, setting up a development environment will most likely be your very first application-oriented step toward architecting a blockchain solution. We hope the topics discussed in this chapter can show you an example of what the actual job of setting up a blockchain development environment would be like.

# [IDEs-a brief intro](#toc.xhtml#s288a)

In case you were not aware, IDE is the acronym for an Integrated Development Environment. An integrated development environment is software that is used in creating applications that bring together various common developer tools into one single GUI or Graphical User Interface.

Why are these IDEs so important, you might be wondering? Well, an integrated development environment enables a developer to begin the programming of new applications quickly, as this way, many of the utilities do not require to be manually configured or integrated when it comes to the setup process. Plus, with IDEs, developers do not have to waste time separately learning how to make use of all the different tools when every single utility is brought out on the same workbench. This particular feature is even more useful when new developers are involved since they can trust an integrated development environment to bring them up to speed with the standard tools and workflows of the rest of the team.

An IDE may come with a range of distinct features, most of which are integrated to save up precious time, such as intelligent code completion and automated code generation, which renders the act of typing out entire character sequences unnecessarily.

The general components of an integrated development environment include the following:

*   **A source code editor:** This element brings a text editor, which provides help with writing software code in association with properties like syntax highlighting with visual cues, coming up with language-specific auto-completion, as well as checking for bugs while a code is being developed.
*   **Local build automation:** This contains different utilities, which work to automate easy and often repeated actions as part of fabricating a local build of certain software to be used by the developer. These actions include compiling computer source code into binary code, packaging binary code, and running various automated tests.
*   **Debugger:** This program is used in testing other programs, which are able to graphically display the position of any bug in the original code. This means when you use a debugger, it acts as breakpoints in the running code. These breakpoints help examine the code flow along with function calls and values of different variables.

Aside from the aforementioned three, there are quite a few other common IDE features, which are built to provide developers with the utmost help when it comes to organizing their workflow and solving various issues. An integrated development environment parses a certain code as it gets written so as to root out any bugs caused by human error in real-time. Because the many utilities of an IDE are represented by one single GUI, a developer can also carry out functions without having to switch between applications. Syntax highlighting is another common feature of most IDEs; the feature makes use of visual cues to distinguish grammar in the text editor. What is more, quite a few integrated development environments also come with class and object browsers, along with class hierarchy diagrams for various languages.

# [The various types of IDEs](#toc.xhtml#s289a)

Nowadays, most project developers choose to go with a pre-configured IDE they find the most suitable for their particular project. To be able to make a wise decision when it comes to picking the right integrated development environment for your project as a blockchain architect, you first need to know about the different kinds of IDEs that are the most used at the moment.

For starters, there are **mobile development IDEs**. As the popularity of smartphones and tablets constantly goes up, most organizations have to develop mobile phone-specific applications to keep up with the digital age. When it comes to the development of mobile apps, the choice of platforms is an integral factor. If a certain app is meant to be used by people with iOS and Android devices, it would be a good idea, to begin with an integrated development environment that provides cross-platform support for several operating systems.

Then there are **cloud IDEs**\- integrated development environments that are presented as a cloud-based **Software-as-a-Service** (**SaaS**). These cloud IDEs give a range of additional benefits when compared with local development environments.

With a cloud IDE, there is no need for downloading software and configuring local environments and dependencies; therefore, a developer can begin actually contributing to projects without any unnecessary delays. This means a level of standardization is also brought about across the individual environments of team members, and since the entire common development environment is managed centrally, there is no code that resides on a single developer's computer, which reduces intellectual property and security concerns.

With cloud IDEs, the way various processes affect local machines is also quite different. For instance, procedures like running builds and testing suites are generally compute-intensive, which means developers are rendered incapable of using workstations while a certain procedure is running. However, a SaaS IDE is able to dispatch long-running jobs without compromising the computing resources of a local machine. Likewise, cloud-integrated development environments are also usually platform-agnostic, which allows the connection to different cloud vendors.

# [Choosing the right IDE for your project](#toc.xhtml#s290a)

As varied as the many use cases for IDEs in the market are at the moment, it is no surprise that there are just as many proprietary and open-source IDE options available to choose from too. Before you go ahead and choose the right IDE for your application, you first need to think about which tools and features you need for that integrated development environment to have. Some central characteristics that can dictate what kind of IDEs you can pick include:

*   **Debugging:** This goes without saying, as debugging is one of the most vital aspects you should keep in mind while choosing an integrated development environment for your project. Debugging, of course, allows a programmer to run a certain program step by step and also set breakpoints that would act to pause the program in the key spots. Debuggers further allow a user to look out for variable values, which proves particularly useful when one is trying to figure out the exact reason why a program might have produced a different outcome than expected or even crashed.  
    *   Most popular integrated development environments provide some kind of debugging, but there are still some well-known ones that do not have any form of the debugger.
*   **The expenses:** While most integrated development environments available on the market come free of charge, add-ons are not always free. IDEs like Arduino IDE and Python IDLE may be entirely free and open-source, but packages such as the IAR Embedded Workbench are proprietary, and they cost quite a lot.  
    *   The open-source packages are obviously more beneficial if you consider the financial angle, and they also usually have huge communities behind them; however, the packages you have to pay for do contain unique features, are well supported, and they also provide consumer support which may come in handy when anything goes wrong. You must keep in mind, though, that closed-source software always depends on the company fixing any bugs and also bringing upgrades regularly, and in case that fails to happen, an integrated development environment can be rendered simply unusable for quite some time.
*   **Speed:** This is one of the biggest factors to consider when picking out an integrated development environment for your project. Naturally, the IDEs, which have comparatively fewer features, are also quite a bit faster than most of their contemporaries. One of the speediest IDEs available out there is the Python IDLE, as it is one of the lower-feature IDEs.
*   **The number of programming languages supported:** Some integrated development environments specialize in a single programming language, and hence, are better fit for a specified programming paradigm. There is the IDE IntelliJ, for example, which is essentially a Java IDE. Meanwhile, there are other IDEs that provide support for multiple programming languages. For instance, the Eclipse integrated development environment supports the languages Python, Java, XML, and yet more.
*   **Operating systems supported:** A developer's specific operating system already narrows down the choice of IDEs (that is, unless the IDE in question is cloud-based). Furthermore, if the application that is being developed is intended for an end user who has a certain operating system (such as Android or iOS), that adds an extra constraining factor.
*   **Any additional features:** Even though most IDEs come with the three key features mentioned previously (which are source code editor, build automation, and debugger), many of them might also include additional features such as refactoring, code search, and continuous integration and continuous deployment (CI/CD) tools, which you might want to be on the lookout for.
*   **The impact on system performance:** An integrated development environment's memory footprint might be a factor you would want to account for in case you need to run other memory-intensive application(s) alongside.
*   **Plugins and extensions:** Some integrated development environments come with the ability to customize workflows to match up with a certain developer's preferences and requirements.
*   **Associated packages and libraries:** While there are some IDEs that have a vast amount of library backing and yet are pretty simple to use (likely because they also have library managers that allow you to look for a specific library, language, board, or tool that you need for your project, and even automatically install everything you require), most integrated development environments that contain a good number of packages and/or libraries are in turn quite hard to use. This is something you would want to keep in mind while choosing an IDE for your application, as IDEs that are easier to use usually prove more efficient in the long run.

In conclusion, you must always pick an integrated development environment that would get your job done in the simplest way possible while also having the features you need.

# [Some well-known and widely used IDEs](#toc.xhtml#s291a)

Here we have included a list of some commonly used integrated development environments that have sizable communities growing around them. Without further ado, let us get into the list:

# [Eclipse](#toc.xhtml#s292a)

Eclipse is an IDE that supports the languages Python, Java, C, C++, Perl, PHP, and Ruby, among others. This particular integrated development environment comes with features that would be equally helpful for both beginner and experienced programmers. This IDE has quite a big library of plugins, so it can, of course, be used with quite a few programming languages. The following is a screenshot of the Eclipse interface. Please refer to the following figure:

![](images/Figure-13.1.jpg)

**Figure 13.1:** The eclipse interface  
**Source:** Eclipse foundation

Eclipse also comes with a number of helpful code suggestions or completions so as to help speed up the projects being developed. Further, the workspaces and hierarchy of folders work to separate and organize different projects and parts, so they are very easy to find.

It should be noted that while this integrated development environment can be used across platforms, Eclipse needs a JRE or Java Runtime Environment, as well as a JDK or Java Development Kit to compile and run a Java code.

# [MPLAB X](#toc.xhtml#s293a)

The MPLAB X IDE supports C, C++, assembly, and a bunch of more languages. The integrated development environment is especially known for embedded development for PIC microcontrollers developed by Microchip. The IDE is based on the aforementioned Eclipse, and it can run on any personal computer that provides support for Windows, Mac OS, and Linux. The following is a screenshot of the MPLAB X interface:

![](images/Figure-13.2.jpg)

**Figure 13.2:** The MPLAB X interface  
**Source:** Microchip

Aside from C/C++ compilers, other useful properties of MPLAB are a debugging tool, macros, third-party tools, complex breakpoints, auto-completion, and even a live syntax checker, which can immediately point out any common errors.

# [Arduino IDE](#toc.xhtml#s294a)

This one, in particular, is quite possibly the best-integrated development environment out there for beginners. The Arduino IDE is an open-source IDE that gives you a range of features- as well as a number of libraries, which make embedded programming a lot more easy. While the Arduino IDE is optimized to work along with the Microchip ATmega328P microcontrollers on Arduino boards, it can, in fact, go with a good number of different microcontrollers in the market. The following is a screenshot of the Arduino IDE interface. Please refer to the following figure:

![](images/Figure-13.3.jpg)

**Figure 13.3:** The Arduino IDE interface  
**Source:** Arduino Project Hub

The Arduino IDE has its own programming language based on the language C, and the integrated development environment is quite intuitive and straightforward, which makes Arduino good for learning further while you work on your project. Programming languages supported by Arduino include C and C++. What is more, Arduino is an integrated development environment that benefits from having ready-to-use boards for developers to build projects on; plus, the platform has open-source hardware and software and also a huge and helpful community.

# [IntelliJ IDE](#toc.xhtml#s295a)

This integrated development environment is very much a developer-centered IDE that provides support for languages such as HTML, JavaScript, Node JS, and many more. The IntelliJ IDE brings a wide and variable range of tools to help developers complete a particular code, look for any errors in their code, and make the necessary changes. The following is a screenshot of the IntelliJ IDE interface:

![](images/Figure-13.4.jpg)

**Figure 13.4:** The IntelliJ IDE interface  
**Source:** JetBrains

Additional features include version control that would help you keep the edits of your code organized, an inline debugger that would display any changes in variable values, quick fixes that would point out any potential mistakes and also the solutions to them, and refactorings for swiftly changing the names of classes, methods, variables, and anything else along the lines.

# [Remix online IDE](#toc.xhtml#s296a)

Now this one is a browser-based compiler and an integrated development environment that allows a user to create Ethereum-based smart contracts with the help of the Solidity programming language we learned about previously and also to debug transactions. While the Remix IDE finds its primary use case in smart contract development on top of the Ethereum platform, it is, at the same time, a protocol that is good for teaching, learning, and in general, getting familiar with the Ethereum ecosystem. The following is a screenshot of the Remix Online IDE interface:

![](images/Figure-13.5.jpg)

**Figure** **13.5:** The remix online IDE interface  
**Source:** ResearchGate

This particular integrated development environment is an open-source Web and desktop application that sets in motion a quite fast development cycle and comes with a notable amount of plugins with intuitive GUIs. The online Remix IDE comes with a varied set of modules for functions such as testing, debugging, the deployment of smart contracts, and many more yet. Notably, the application has been written in JavaScript, another pretty popular programming language we have already covered in the former sections of this book.

In the upcoming portion of the chapter, we will be learning how to set up the online Remix IDE for the purpose of Solidity development, as promised at the beginning.

# [Setting up the online Remix IDE for solidity smart contract development](#toc.xhtml#s297a)

When writing smart contracts in the Solidity language, the Remix online IDE is a very trustworthy application to use. In this section, we can do away with a step-by-step tutorial on how to set up the online Remix IDE. It is best that we head over to their official website and follow the fairly self-explanatory instructions. These instructions are dynamic and can change from time to time, so it is best to refer to on the website directly.

So, you are now all set! You can go to your browser and start coding with Solidity on your personal copy of the online Remix integrated development environment!

# [Conclusion](#toc.xhtml#s298a)

As someone aiming to become a blockchain architect, you have to know that setting up a development environment is a central part of the work you will be doing. That is why in this chapter, we have gone through the basics of what an IDE or an integrated development environment is, followed by types of IDEs, tips on how you can pick an IDE that will be the best suited to your work, and some well-known IDEs you can rely on, to begin with. Finally, we have looked through the Remix online IDE and how to set up that particular application for smart contract development in the language Solidity. Now, in the upcoming chapter, we will learn more about design development and integrations.

# [Questions](#toc.xhtml#s299a)

1.  **What does the acronym IDE stand for? What is an IDE?**
    
    Integrated development environment. An IDE is software that is used to build various applications, and they facilitate easy and faster code development.
    
2.  **Name some different types of IDEs.**
    
    Eclipse, IntelliJ, MPLab X, Arduino, and so on.
    
3.  **What are some features of IDEs that can help you pick the right IDE for your project?**
    
    Debugging support, programming languages and OS support, Cost, Speed, Plugins, and extensions.
    
4.  **What is the Remix IDE?**
    
    Remix is a browser-based IDE that allows a user to create Ethereum-based smart contracts with the help of the Solidity programming language.
    

# [Key terms](#toc.xhtml#s300a)

*   **IDE:** An IDE or an integrated development environment is a software that is used in creating applications. They compile various common developer tools into one single GUI or Graphical User Interface.

# [CHAPTER 14](#toc.xhtml#c14)

# [Blockchain Architecture—Design Development and Integrations](#toc.xhtml#c14)

# [Introduction](#toc.xhtml#s301a)

In the last few chapters, we have learned about laying the groundwork for architecting a blockchain, programming languages and libraries a blockchain architect should be aware of, and setting up the correct development environment for a certain blockchain. Now that we have covered some significant background knowledge on how to architect a blockchain, it is time for us to get into the actual designing and developing, as in architecting, of blockchain solutions.

In this chapter, initially we go through the essentials of designing blockchain nodes and what roles various nodes have to play on a blockchain, and then we check out how several popular blockchains have set up their nodes and what are their responsibilities within these blockchain ecosystems. Next, we see an example of setting up some core components of a blockchain structure. Finally, we will also be learning about building APIs through another example.

# [Structure](#toc.xhtml#s302a)

The following topics will be covered in this chapter:

*   Designing blockchain nodes
*   Node structures of popular blockchains
*   Setting up a blockchain
*   Nodes
*   Clearing server
*   The smartphone app
*   Blockchain network setup
*   Summary
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s303a)

We hope you can take away a clear understanding of designing blockchain nodes, setting up and configuring a full blockchain, and building APIs.

# [Designing blockchain nodes](#toc.xhtml#s304a)

Nodes are a part of the most fundamental structure of a blockchain, and yet the many types of them and the wide range of purposes a node might have to serve creates quite a lot of complications when it comes to designing nodes for a blockchain. As a blockchain architect, when you are creating a secure blockchain network for a specific purpose within the public or private sector, you must remember that there is no one set of rules like "all nodes are created equal" or "*all nodes must be able to see all data at all times*", or no set features when it comes to designing nodes for the blockchain. According to the needs of the organization, you can, in fact, deploy a variety of designs for different actions.

A blockchain network must represent a unified and effectual ecosystem that functions in a way all involved parties agree upon. It is important to realize that it would not be cost-efficient for every node to perform all kinds of operations—whether administrative or functional. On the other hand, dividing all responsibilities between the nodes can help minimize duplications of effort and promote economies of scale.

Therefore, it can be said that a diverse set of server nodes with separate, unique roles and responsibilities is integral in the making of a well-functioning blockchain network. Furthermore, the variety can also help with increasing the efficiency of the ecosystem overall.

As a blockchain architect, you should be aiming for a well-balanced governance model that would include nodes in charge of verifying and maintaining aspects such as security, identity, trust, and performance. For instance, you can start with a **founder node**, which essentially stands for the organization and its team, who will be directly involved in driving the creation and maintenance of the blockchain network. The founder node is placed to lead the consortium of all other nodes on the blockchain, and it can guide the entire ecosystem by approving participation and assigning operational roles. The founder node will become the network administrator and make sure every other node on the blockchain has a stake in the game.

As quite a few blockchains are doing lately, you can integrate one or several **controllers** or **custodian** or **master nodes** too. This controller or master node(s) can be selected from the organization the blockchain belongs to or from the outside. The position will be responsible for performing tasks on behalf of all the participants and must be aware of industry regulations, business rules, network operations, and suchlike.

The custodian node may be held responsible for the following governance-related functions:

*   Assigning and regulating positions that will, in turn, be authorizing node activity to trusted and efficient participants on the blockchain
*   Encrypting information on the blockchain with chosen cryptographic methods
*   Keeping records of tasks, a particular node has been assigned, and its degrees of success
*   Documenting service level agreements (that is, performance, uptime, and so on), as has been approved by the founder node
*   Coming up with and deploying consensus validation algorithms
*   Storing the rules which represent the smart contracts on the chain
*   Securing all public and private keys belonging to the many participants for authentication and authorizations requirements

Furthermore, the controller node will be keeping track of and sustaining overall network performance by undertaking actions as follows:

*   Dividing workload equally among all nodes and maintaining balance
*   Detecting threats to the blockchain ecosystem and noting any malicious activity immediately
*   Making sure that all nodes are operational and synchronized
*   Evaluating a certain node's processing performance against any service level agreement measurements

As for other basic node roles, there are some factors you can use to discern which node is capable of holding what kind of position within your blockchain ecosystem. For example, servers can be distinguished by their:

*   Vested interest; for instance, their consensus work
*   Degree of involvement within the network
*   Capacity regarding things such as processing, storage, and interconnectivity
*   Reputation judged based on their overall performance

What is more, node roles can change based on the blockchain network's purpose and industry. For instance, if we talk about architecting a blockchain for the administration and management of electronic medical records within the healthcare industry, usual participants on the network would include people like medical providers, claims processors, billing departments, patients, and regulators. If made nodes, they will each have a vested interest to make sure the data stored on the chain is verified, processed efficiently, and kept secure. Now, based on their level of involvement, their processing and storage capacities, and their efficiency and performance, they can be assigned different node roles on the network.

In the particular aforementioned scenario, on a permissioned blockchain with founder and custodian nodes, the other node roles can go like this:

*   **Transactor:** This node will be responsible for generating transactions to document on the blockchain's ledger. Billing department staff, medical providers, and insurance claims processors usually generate different kinds of operational transactions.
*   **Endorser:** This role is for the ones performing, reconciling, and proofing functions that will authenticate the source—as in, confirm proof of ownership, or ensure all transactions are received in the right sequence—as in, confirm proof of order. This way, a block of transactions can be cryptographically sealed and transmitted.
*   **Validator:** Validators will vote to confirm the endorsers' work of forming the blocks on the chain is valid, thus finalizing a block's inclusion in the blockchain ledger. An insurer will be a good choice, for example, to vote on whether a medical process is legitimate or not.
*   **Partial (or Light) and Full Record Maintainer:** These roles go to those who either hold a headers-only version of each validated block (partial maintainer) or store a full copy of the blockchain ledger (full maintainer). These roles will be easier to assign once you know which participants might need to carry around a detailed history of blockchain transactions; while the staff in the billing department will not need complete copies of doctors' notes, an insurance claims unit will definitely need full details, including historical transactions.
*   **Viewer:** A patient is the kind of node which can just do with viewing rights.
*   **Enforcer:** This node will inspect blockchain records for auditing or regulation purposes. For example, a federal government auditor may come in as an enforcer on a blockchain to make sure the patients' privacy is being maintained.

As Satoshi Nakamoto stated in the Bitcoin whitepaper, a node "only requires to read the heads of blocks to check if a transaction is legitimate or not", as in most nodes can do by being light clients and avoiding the storage conundrum that might arise from being a full node. What is more, it is important to keep in mind that adding a major number of full nodes to a blockchain network will increase the requirements on both storage and computation resources, in turn adding to the overall expenses. From a cost perspective, therefore, it is tactical to have as few full nodes as possible on your blockchain network. However, it is still important to keep enough full nodes to ensure the blockchain functions and scales right and also remains secure.

Light clients just verify the integrity of a block from a full node by using a lighter but secure hashing method. However, depending on your design, full nodes may typically do the following:

*   Just download the entire blockchain history
*   Both download and validate the ledger
*   Download and validate the blockchain ledger while also participating in the consensus mechanism
*   Hold administrative rights (such as granting and revoking a node's access) along with the aforementioned responsibilities

# [Node structures on popular blockchains](#toc.xhtml#s305a)

The aforementioned concepts of light clients and full nodes are broadly in use across various existing blockchain frameworks and implementations. For instance, the **Bitcoin and Ethereum platforms offer light clients** called SPV or Simplified Payment Verification clients.

However, light clients need to download data from full nodes, and therefore, require placing trust in said full nodes. To implement security measures to protect light clients, the **Ethereum blockchain has introduced a solution called "fraud proof"**. A light client on Ethereum can request fraud-proof from a full node based upon the cryptographic properties of the Merkle tree we have discussed previously; thus, a specific transaction or state can be verified as part of the chain after all.

Now, let us see how some other well-known blockchain networks divide their node roles. Hyperledger Fabric is a blockchain designed for private enterprises. **A Hyperledger network consists of three separate node types**. The network is secured by "peers", who can also have an "*endorser"* role so they can generate new blocks. Transactions on the chain are both ordered and delivered through nodes called the ordering service nodes. Finally, there are the submitting clients who invoke transactions with the endorsers. Clients have to rely on the peer for the read and write operations and can connect to as many peers as they want, which in turn check and validate the client transactions.

This is how the process goes:

*   A client sends a certain transaction to a number of connected peers
*   The endorsing peers validate and simulate said transaction
*   Once that process is successful, each of those connected peers generates a certificate and passes it on to the client, stating their endorsement
*   Once a certain number of peers (as dictated by the constitution) endorse a transaction, the client relays this transaction with the signatures to the ordering service
*   The ordering service now broadcasts the finished transaction to all endorsing peers, who verify the endorsements themselves and then record the changed state to the ledger

Moreover, the Hyperledger Fabric network relies on "Certificate Authorities", which have to be configured to generate certificates and send them to the administrators and network nodes. Members of the network identify, authenticate, and sign messages through a mechanism known as "*Membership Services*".

Another popular blockchain project would be MultiChain—a fork of the Bitcoin protocol, which allows the regulation of access for private or consortial deployment purposes and does away with the original mining process of Bitcoin. **Nodes on MultiChain can have various sets of permissions and purposes**, such as:

*   The "*admin"* permission includes the ability to vote on proposed changes to the network and even add other admins or other higher-level permissions
*   The "*mining"* permission lets nodes participate in the consensus of adding new blocks to the chain
*   For communication between parties on the network, there is the stream function, to which the node responsible may allow or revoke access as per requirements

While MultiChain does not offer any native light clients due to being a Bitcoin fork, the platform does allow the deployment of the SPV mechanism previously mentioned to connect with a MultiChain network in a lightweight manner.

# [Setting up a blockchain](#toc.xhtml#s306a)

Now that we have discussed how various existing blockchains design and structure their nodes, it is time to see a practical example of how a blockchain system can be designed and set up. The blockchain solution structure we will be analyzing here is in use by different energy providers and network operators, such as the Austrian Smart Grid Model region Köstendorf in Salzburg and Böheimkirchen in Lower Austria.

In the section as follows, we discuss in detail three core elements of the blockchain structure: the nodes, the clearing server, and the smartphone app. Notably, the clearing servers are useful only for this particular use case in the energy industry and not for actually running the blockchain.

In the figure as follows, the blockchain system and its main components are shown:

![](images/Figure-14.1.jpg)

**Figure 14.1:** A Blockchain's basic structure

Every participant on the blockchain has a node installed in their device(s) that runs the blockchain node software, along with an app that lets them send commands to the nodes. All nodes are connected within a Virtual Private Network or VPN so that they can connect with each other without using public IP addresses.

At every utility's premises, a clearing server is installed. The server is connected to a node, which is listening on the blockchain and also reading the portions of the utility's many clients so as to calculate the net energy consumption of every participant.

The app that each customer will have gets connected to a node (for sending across new transactions and receiving confirmations) and also to the clearing server (for billing). New transactions (Tx in the image) are held in a pool with other unconfirmed transactions until a node mines them and adds them to a block. The clearing server connects to the blockchain to retrieve data and sends billing information to the apps on customers' smartphones.

# [Nodes](#toc.xhtml#s307a)

In the following figure, the fundamental architecture of the node implementation for this particular blockchain is shown. The internal state is shown with two primary data structures—a tree and a state table. The tree stores a representation of the blockchain as seen by the node at the moment, and the state table is a tabular view of time slots and the corresponding portions for every client. The second is deduced from incoming valid transactions. On startup, the node reads the last persisted state from the disk and initializes the internal tree data structure, which represents the blockchain along with the state table and connected auxiliary data structures. Then the node starts the watchdog for the server threads to keep a lookout for incoming messages from other known participants. Please refer to the following figure:

![](images/Figure-14.2.jpg)

**Figure 14.2:** Node structure for a certain blockchain

The mining thread, the "*up to n*" server threads, and the "*up to n*" client threads operate on the core tree data structure that represents the blockchain and the state table that represents the assignments of portions. The state of the data structure and the additional representations, such as time-slot-accurate portion assignments, are held on the disk. Server and client threads include watchdogs that can detect and even continue any connections to other nodes that might have been lost. It also starts the mining thread that does the processing of unconfirmed transactions and combines them into blocks that are affixed to the tree data structure.

The mining thread, meanwhile, can be described as an infinite loop that waits on unconfirmed transactions, verifies their integrity and validity, and creates a new block afterward. A block can be considered legitimate when the numeric interpretation of its cryptographic hash (SHA-256) is under a predefined level.

After mining is done successfully, known nodes are made aware of the newly mined block through client threads. There is one of these threads for every peer. Watchdogs ensure any connection timeouts or remote failures can be turned into a re-initialization of the connection in question.

The central tree data structure that stands for the blockchain can be read from and written to by all the threads simultaneously. Keeping this tree data structure up-to-date decreases run-time memory usage, as this way, there is just a small part of the tree in the internal memory, and the branches and blocks can be loaded from the disk when required.

To achieve consensus among all nodes, blocks and transactions require validation before being stored in the tree structure. Therefore, the incoming blocks from other nodes and the blocks for mining all pass through a conformity check before being added and broadcast. In this process, a block's integrity is checked by verifying its signature and recomputing its hash. Then, it is determined that the block hash satisfies the currently active difficulty level, and the block can be added to the current tree.

After that, another process is undertaken to check the transaction validity, which goes like this:

*   Attaching the block to the tree temporarily to check whether it changes the longest chain or not
*   If the longest chain changes, the first common parent node for the branch of the previous longest chain and the current longest chain needs to be found
*   All transactions now have to be temporarily reverted (as in removed from the stable table) from the previous branch up to this common parent node
*   All the transactions from the current longest branch, starting with the common parent node, should now be processed
*   In case a single transaction in the newly added block turns out to be invalid (whether due to double spending or because of unknown recipients), the entire process has to be reverted, and the new block must be discarded

Once the block has been added successfully after executing the procedures previously mentioned, the longest chain and the state table will represent the current state of the entire system, as in all the portions of all the participants for all possible time slots. This information can be queried with the smartphone app and the clearing server through the node's API.

# [Clearing server](#toc.xhtml#s308a)

The clearing server utilizes the node's API to enquire about the current distribution of portions so as to use the portions held by every customer for each time slot for billing. The resulting values are displayed in the customers' smartphone apps.

# [The smartphone app](#toc.xhtml#s309a)

The app focuses on achieving a high degree of usability. It is connected to a node and the particular clearing server of a customer's utility provider. The app can use its connection to the node to send new transactions to the network and to receive data regarding incoming portions. To do that, the app requests a list of the blocks from the longest chain and then filters all transactions to visualize those relevant to the individual customers.

# [The blockchain network setup](#toc.xhtml#s310a)

The nodes connect among each other, as well as the app and the clearing server over TCP/IP and XML messages on top of the application layer. Using the text-based protocol makes it easy for debugging, and illustrates messages suited for non-technical people. The nodes' API defines four primary types of messages, which are:

*   The block messages might be informing about a newly mined block or be a response to a block request from another node
*   The transaction messages that are sent across by the smartphone app indicate a new shift of portions
*   The utility transaction messages; are sent by the clearing servers placed at each utility that have the permission to create new power plants and also assign customers and default distributions to them
*   Finally, the status messages are used to display the node status to clients, along with being used for debugging purposes

All messages are signed by their senders, and since this is a permissioned blockchain structure, the public keys of all the nodes are known to each other, and any messages with invalid signatures are discarded. As for the communication link between the clearing server and the smartphone app, it uses out-of-the-box HTTPS with authentication and encryption.

# [Conclusion](#toc.xhtml#s311a)

After learning about setting up the right development environment for a blockchain, in this chapter, we have focused on designing blockchain nodes, node structures well-known blockchains of our time have in place, and setting up essential components of a blockchain. And just like that, we have taken another step toward our goal of entering the blockchain development industry.

In the upcoming chapter, we find out in detail how cryptocurrency networks and **Non Fungible Tokens** (**NFTs**) are created.

# [Questions](#toc.xhtml#s312a)

1.  **What kind of roles can a node have on a blockchain?**
    
    Nodes can have roles such as founder, custodian, transactor, endorser, validator, and so on.
    
2.  **What are some factors that can help you decide which role to attribute to a particular node on the blockchain?**
    
    Vested interest.
    
    Degree of involvement within the network.
    
    Capacity regarding things such as processing, storage, and interconnectivity.
    
    Reputation-based on performance, and so on.
    
3.  **What is the main difference between partial and full nodes?**
    
    Partial nodes store only partial information about blocks of blockchain, such as only header information. Full nodes store complete blocks of the blockchain network.
    
4.  **Why can it prove beneficial to have a limited number of full nodes while designing a blockchain?**
    
    We should have only a limited number of nodes as full nodes so that it does not compromise on the security aspect of the blockchain and, at the same time, saves the storage and compute requirements.
    
5.  **What measures has the Ethereum blockchain taken to protect its light clients?**
    
    Ethereum has introduced a feature called fraud-proof to protect its light client.
    
6.  **What are the node types seen on a Hyperledger blockchain?**
    
    Endorsers, ordering service nodes, and submitting clients.
    
7.  **What permissions can nodes on Multichain have?**
    
    Admin, mining, and communication.
    

# [Key terms](#toc.xhtml#s313a)

*   **Node Structure:** This is the way light, full, and other types of nodes are put to use on a blockchain.
*   **The Mining Thread:** This is an infinite loop that waits on unconfirmed transactions, verifies their integrity and validity, and creates a new block afterwards.

# [CHAPTER 15](#toc.xhtml#c15)

# [Blockchain Bonus—Creating Cryptocurrencies and NFTs](#toc.xhtml#c15)

# [Introduction](#toc.xhtml#s314a)

Over the expanse of this book so far, we have learned much about the mechanism of a blockchain and how a blockchain architect can go about making a blockchain of their own. Now, near the end of our journey, we will be learning about **Ethereum Request for Comments** (**ERC**) and two particular ERC standards—the ERC 20 standard and the ERC 721 standard. Then, we will see a demonstration of building a cryptocurrency following the ERC 20 standard, as well as an explanation regarding the process of creating an NFT or a non-fungible Token.

# [Structure](#toc.xhtml#s315a)

The following topics will be covered in this chapter:

*   Ethereum's ERC standards  
    *   The ERC 20 Token Standard
    *   The ERC 721 Token Standard
*   Developing your own cryptocurrency on the Ethereum blockchain  
    *   Creating an ERC 20 Token
    *   Functioning of an ERC 20 Token Smart Contract
    *   The dependencies we will need to install
    *   Writing the ERC 20 Token smart contract
    *   Testing the smart contract
*   Creating a non-fungible token (NFT)?  
    *   Storing your NFT's metadata
    *   Building the NFT
    *   Building the smart contract for NFTs
    *   Building the metadata for NFTs
    *   Deploying your NFTs
*   Conclusion
*   Questions
*   Key terms

# [Objectives](#toc.xhtml#s316a)

With this chapter, we hope to impart to you the knowledge of Ethereum's ERC standards. Additionally, we hope the examples of the coding you will need to create a cryptocurrency and an NFT will prove useful for you.

Now, without further ado, let us get into the concept of ERC standards.

# [Ethereum's ERC standards](#toc.xhtml#s317a)

ERC, as mentioned earlier, is an acronym for "Ethereum Request for Comments". ERC standards are essential for providing guidance to developers regarding token construction. A developer can create an ERC by submitting an EIP or an Ethereum Improvement Proposal.

Aside from the ERC 20 and ERC 721 standards, we will also be discussing in detail in the following sections other final Ethereum Requests for Comments, including ERC-55, ERC-137, ERC-162, ERC-165, ERC-181, ERC-190, and ERC-1167.

# [The ERC 20 token standard](#toc.xhtml#s318a)

One of the most significant standards many Ethereum blockchain-based cryptocurrencies follow is the ERC 20 token standard (**[https://ethereum.org/en/developers/docs/standards/tokens/erc-20/](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/)**). The standard was proposed back in November 2015 by Ethereum developer Fabian Vogelsteller. The ERC 20 token standard has become the prime technical standard used by all smart contracts for the implementation of tokens within the Ethereum ecosystem. Notably, by August 2021, there were already about 442,647 ERC 20 crypto tokens on top of the Ethereum blockchain.

Ethereum's ERC 20 standard is an API specification governing how Ethereum tokens should be built. The ERC 20 token standard is a community-adopted standard that lets Ethereum tokens support a wide range of use cases. It lays down a basic set of rules for all crypto tokens built on top of the Ethereum blockchain. These rules make sure the various Ethereum tokens with different functions are able to interact and perform uniformly within the broader Ethereum ecosystem. What is more, all platforms and digital wallets that support the ETH token are also able to support any ERC 20 standard-compliant tokens.

The ERC 20 specification basically dictates the interface that the smart contract for an Ethereum token has to respond to and states the structure of the said smart contract, as well as the various kinds of functions this smart contract must have. Specifically, ERC 20 clarifies six basic coding functions which are crucial for user/token implementation. These functions are as follows:

*   the total supply of tokens,
*   the storing and returning of balances,
*   the allowance or access permissions, which assigns any third party the right to carry out a transaction with a certain portion of the tokens a user owns without giving away the private key,
*   the transfer of a token between users,
*   the method of approval of transactions,
*   and how users can look at all the information regarding a token.

Using the ERC 20 token standard ensures that an Ethereum token is compliant with use cases such as wallet transfers, buying and selling cryptocurrencies on exchange platforms, and purchasing tokens in **Initial Coin Offerings** (**ICOs**).

The ERC 20 token standard effectively eases development for everyone, from crypto developers to the many blockchain platforms to the various crypto exchanges and wallets. Before a universal standard for all Ethereum tokens was defined, developers were using different terms in their codes, reducing compatibility between different blockchains. Moreover, crypto exchanges and wallets had to modify their platforms again and again for new Ethereum tokens to be added.

However, the ERC 20 token standard ensures none of that is required anymore. ERC 20 compliance brings compatibility between all Ethereum tokens; plus, the standard helps crypto developers understand how a new token will work within the overall Ethereum ecosystem.

Well-known cryptocurrencies to abide by the ERC 20 token standard include **MakerDAO** (**MKR**), **EOS** (**EOS**), **Tron** (**TRX**), the **Basic Attention Token** (**BAT**), **Augur** (**REP**), and **OmiseGO** (**OMG**).

Now, we learn about another, more recent ERC standard: the ERC 721 token standard.

# [The ERC 721 token standard](#toc.xhtml#s319a)

The ERC 721 token standard (**[https://ethereum.org/en/developers/docs/standards/tokens/erc-721/](https://ethereum.org/en/developers/docs/standards/tokens/erc-721/)**) is a free and open standard that lays down rules for the development of non-fungible tokens within the Ethereum ecosystem. Non-fungible tokens (NFTs) are cryptographic assets based on a blockchain. These assets have unique identification codes and metadata that make them distinct from each other, unlike cryptocurrencies which are fungible tokens. In layman's terms, a crypto token is replaceable with another crypto token, but an NFT, being unique in itself, cannot be replaced with another NFT.

ERC 721 tokens are unique, one-of-a-kind ones. The ERC 721 token standard, also known as the non-fungible token standard, was brought forth by William Entriken, Dieter Shirley, Jacob Evans, and Nastassia Sachs in January 2018 to deal with the interface incapabilities of the ERC 20 standard.

ERC 721 tokens are different from ERC 20 tokens in that the ERC 721 tokens are all—as mentioned previously—non-fungible and, therefore, unique, so ERC 721 tokens are not interchangeable. But ERC 20 tokens are, of course, fungible, and they can be traded for another token of their kind.

NFTs have become all the rage in recent times; all these NFTs are typically based on the ERC-721 Token Standard. Cryptokitties, the Ethereum-based blockchain game that first brought NFTs into the limelight, made use of the ERC 721 token standard to develop unique digital collectables in the form of virtual cats. On Cryptokitties, none of these cats was the same as another, and all of them were differently priced, as determined by the users on the platform.

The ERC 721 standard defines a minimum interface that a smart contract on the Ethereum blockchain must deploy so as to allow for these unique tokens to be created, owned, managed, and transferred. However, the token standard does not regulate or limit any potential additional attributes (token metadata, supplemental functions, and so on) a developer may want to implement in their non-fungible tokens.

NFTs can be made out of both physical and digital assets. For example, a blockchain-based non-fungible token can represent:

*   Real estate
*   Artworks and sculptures
*   Vehicles
*   Assets with a negative value, such as loans
*   Virtual collectables such as character cards, game pieces, and so on.

Note that to create an ERC-721 crypto token, a smart contract has to comply with both the ERC-721 and ERC-165 interfaces. An ERC-165 standard is used in cases where contract-to-contract interaction is needed. It is a standard to publish and detect the interfaces a smart contract implements.

Following well so far? We now know what the ERC 20 and ERC 721 token standards are about; let us see how one can develop a cryptocurrency adhering to the ERC 20 token standard within the Ethereum ecosystem.

# [Developing your own cryptocurrency on the Ethereum blockchain](#toc.xhtml#s320a)

ERC 20 tokens, just like any other crypto, are blockchain-based assets that possess a certain amount of value and can be sent across directly from one user to another as payment in a similar fashion as any other crypto. Similarly, they can be bought, sold, and traded out on a crypto exchange, and they can also be purchased in sales like an initial coin offering.

However, the biggest difference between ERC 20 crypto coins and cryptocurrencies like Bitcoin is that ERC 20 tokens are issued within the Ethereum network instead of having their respective blockchains. Basically, ERC 20 tokens are smart contracts that use the Ethereum blockchain.

In this section, we learn how to create an ERC-20 token on the Ethereum blockchain. Plus, we will see how to test out the smart contract we create.

# [Creating an ERC 20 token](#toc.xhtml#s321a)

The Ethereum blockchain shares many properties with blockchains like Bitcoin; for instance, just like the Bitcoin blockchain, Ethereum records and monitors account balances for all ETH holders. However, unlike the Bitcoin blockchain, the Ethereum blockchain also allows you to create your own crypto token without creating an entire blockchain to base it off.

Creating an ERC 20 crypto token on Ethereum is easy with a smart contract. The ERC 20 token standard, as we know it now, defines how this smart contract we will be building for our new Ethereum token should work. The ERC 20 smart contract governs all the functionalities of the token.

# [Functioning of an ERC 20 token smart contract](#toc.xhtml#s322a)

On the Ethereum platform, developers can write applications that run on the blockchain with smart contracts, which allow us to read and write information on the blockchain, along with executing code. As we know, these Ethereum smart contracts are written in the Solidity programming language.

As for how a particular ERC 20 token smart contract operates conceptually, let us see an example with this visualization for a real estate purchase.

![](images/Figure-15.1.jpg)

**Figure 15.1:** How a smart contract works in the context of a real estate transaction  
**Source:** Blockgeeks

Now, moving to how a smart contract actually works under the hood, let us change the context to the creation of a crypto token. Suppose we are trying to create an Ethereum token named "*Token X*", and our symbol for this token would be "*TKX*". Further, let us say we want there to be a total of 100,000,000 of these TKX tokens in existence.

To begin with, the smart contract we will create for this token will keep track of some of the basic attributes of the TKX token. For instance, the smart token records the name we have decided on—"*Token X*", and the symbol TKX that will be displayed on cryptocurrency exchanges the token will be traded on, along with the total number of TKX tokens that will ever be in existence. Further, our smart contract will also monitor the owners of Token X and how many tokens each of them hold.

In the following, we can see an example implementation of the ERC20 token standard's specified transfer function. This function is required by the smart contract, and it is responsible for governing how a user can send a certain ERC 20 token from their own private wallet to another wallet address.

`contract ERC20Token {`

`// …`

`function transfer(address _to, uint256 _value) public returns (bool success) {`

`require(balanceOf[msg.sender] >= _value);`

`balanceOf[msg.sender] -= _value;`

`balanceOf[_to] += _value;`

`Transfer(msg.sender, _to, _value);`

`return true;`

`}`

`// …`

`}`

Now, this function implements the ERC 20 token standard in several ways, which are specified as follows:

*   The function exists and bears all the correct arguments.
*   The function fails in case the user making the transaction does not have the necessary number of tokens required to make the transfer.
*   The function transfers the specified amount from the sender's address to the receiver's address.
*   The function triggers a selling event.
*   The function returns the right value.

# [Writing the ERC 20 token smart contract](#toc.xhtml#s323a)

So now that we are done with installing the needed dependencies, we can get into the actual process of building our ERC 20 token.

In the following, you can find the complete Solidity code for the ERC 20 token smart contract:

`pragma solidity ^0.4.2;`

`contract DappToken {`

`string public name = "DApp Token";`

`string public symbol = "DAPP";`

`string public standard = "DApp Token v1.0";`

`uint256 public totalSupply;`

`event Transfer(`

`address indexed _from,`

`address indexed _to,`

`uint256 _value`

`);`

`event Approval(`

`address indexed _owner,`

`address indexed _spender,`

`uint256 _value`

`);`

`mapping(address => uint256) public balanceOf;`

`mapping(address => mapping(address => uint256)) public allowance;`

`function DappToken (uint256 _initialSupply) public {`

`balanceOf[msg.sender] = _initialSupply;`

`totalSupply = _initialSupply;`

`}`

`function transfer(address _to, uint256 _value) public returns (bool success) {`

`require(balanceOf[msg.sender] >= _value);`

`balanceOf[msg.sender] -= _value;`

`balanceOf[_to] += _value;`

`Transfer(msg.sender, _to, _value);`

`return true;`

`}`

`function approve(address _spender, uint256 _value) public returns (bool success) {`

`allowance[msg.sender][_spender] = _value;`

`Approval(msg.sender, _spender, _value);`

`return true;`

`}`

`function transferFrom(address _from, address _to, uint256 _value) public returns (bool success) {`

`require(_value <= balanceOf[_from]);`

`require(_value <= allowance[_from][msg.sender]);`

`balanceOf[_from] -= _value;`

`balanceOf[_to] += _value;`

`allowance[_from][msg.sender] -= _value;`

`Transfer(_from, _to, _value);`

`return true;`

`}`

`}`

Now, let us discuss what this smart contract we just wrote does and how it deploys the ERC 20 token standard:

*   In Line 4, the smart contract stores the token name; `string public name = "DApp Token"`.
*   In Line 5, the smart contract also stores the token symbol for cryptocurrency exchanges; `string public symbol = "DAPP".`
*   In Line 7, the smart contract stores the entire supply of tokens in existence; `uint256 public totalSupply.`
*   Line 21 onwards, the smart contract relies on a Solidity mapping to save the balance of each account, which holds ownership over these tokens; `mapping(address => uint256) public balanceOf.`
*   In Line 35, it integrates a `transfer` function that would allow a user to send these tokens from their account to another user's account.
*   The smart contract also has an `approval` function that would allow a third-party account to spend tokens on someone's behalf, such as on a cryptocurrency exchange. This updates the allowance mapping to specify how much that account has been allowed to spend.
*   In Line 48, the smart contract includes a `transferFrom` that allows a third-party account to transfer these tokens.

# [Creating a non-fungible token (NFT)](#toc.xhtml#s324a)

We know non-fungible tokens are like rare digital collectables, and we can turn both physical and digital assets into NFTs you users can trade, purchase, and sell across blockchain networks. As mentioned before, most non-fungible tokens follow Ethereum's—"non fungible token standard", or ERC 721. In the section as follows, we will be going through some steps you need to follow to create your very own NFT.

By creating a non-fungible token, you will be publishing a unique token on a blockchain platform like Ethereum. The NFT smart contract has to abide by the ERC 721 standard. Each token possesses a unique token URI, which consists of metadata of your asset in a JSON file that would conform to a certain schema. The metadata, of course, is where you will be storing information regarding your NFT, like its title, any images, description, and other such properties.

Here is an example JSON file for the "*ERC721 Metadata Schema*", inspired by code that can be found on several available forums:

`{`

` "attributes": [`

`{`

`"trait_type": "Shape",`

`"value": "Square"`

`},`

`{`

`"trait_type": "Mood",`

`"value": "Happy"`

`}`

` ],`

` "description": "A happy square.",`

` "image": "https://linkgoeshere.com/hello.jpeg",`

` "name": "Happy Square"`

`}`

# [Storing your NFT's metadata](#toc.xhtml#s325a)

There are two basic ways to achieve this, which are as follows:

*   You can go for storing all the data on the blockchain you are using (Ethereum in this case).
*   You can have your API return the JSON file. This generally comes from the centralized servers (sometimes called oracle), which maintain the attributes of various NFTs and is ready to reply to any query regarding the same.

# [The prerequisites](#toc.xhtml#s326a)

As for the applications we will need to help with building our NFT, they will be the following:

*   **Metamask**: This is needed since we need an Ethereum address to interact with our smart contract. We will need the Metamask mobile app too, along with the chrome extension, as the latter does not display your NFTs.
*   **Alchemy**: You could choose to either run your own Ethereum node or use nodes-as-a-service providers like Alchemy.
*   **NodeJS/NPM**: You should already be familiar with this one.

Furthermore, you can use the "*Ropsten Test Network*" for development purposes.

# [Building the NFT](#toc.xhtml#s327a)

Head over to the REMIX online IDE, where we will begin constructing our NFT.

Our smart contract will declare the token type we are dealing with, construct the NFT, and mints it. It will go like the following:

`// SPDX-License-Identifier: MIT`

`pragma solidity ^0.8.0;`

`import "@openzeppelin/contracts/token/ERC721/ERC721.sol";`

`import "@openzeppelin/contracts/utils/Counters.sol";`

`contract EmotionalShapes is ERC721 {`

`using Counters for Counters.Counter;`

`Counters.Counter private _tokenIdCounter;`

`constructor() ERC721("EmotionalShapes", "ESS") {}`

`function _baseURI() internal pure override returns (string memory) {`

`return "YOUR_API_URL/api/erc721/";`

`}`

`function mint(address to)`

`public returns (uint256)`

`{`

`require(_tokenIdCounter.current() < 3);`

`_tokenIdCounter.increment();`

`_safeMint(to, _tokenIdCounter.current());`

`return _tokenIdCounter.current();`

`}`

`}`

# [Deploying our NFT](#toc.xhtml#s328a)

To begin deployment of our NFT on the blockchain, we follow the following steps:

**Step 1: Install metamask**: a crypto wallet that will also allow you to connect to various testnets and run blockchain applications. The installation instructions should be available and fairly straightforward on its official website.

**Step 2**: Head over to any working faucet and get some ETH on an available testnet.

**Step 3**: Switch the network on your Metamask application to ropsten.

**Step 4**: Now, head over to Remix and copy-paste the contracts you have.

**Step 5**: Hit the compile option.

**Step 6**: Select the deploy option. You should then see the following on your screen:

![](images/Figure-15.2.jpg)

**Figure 15.2:** Preparing Remix IDE to deploy NFT

Select injected Web3 provider.

Then, click on the deploy button. You will then see this:

![](images/Figure-15.3.jpg)

**Figure 15.3:** Deploying NFT using Remix IDE

**Step 8**: Click on copy button to copy the contract address

In your terminal, you should be seeing `EmotionalShapes deployed: [SOME_ADDRESS]`. This is where you can find your Smart Contract deployed on the ropsten test network. By visiting https://ropsten.etherscan.io/address/\[SOME\_ADDRESS\] - here replace *\[SOME\_ADDRESS\]* with the smart contract address you got in the previous step, and then you should be able to see the newly deployed NFT.

# [Conclusion](#toc.xhtml#s329a)

After learning the structure of blockchains and how to create a blockchain of your own, in this chapter, you have also learned about two of the most important Ethereum standards that tokens on the platform have to follow and found out how you can create your own ERC 20 crypto and an NFT. We hope this knowledge will aid you as you make your way into the world of blockchains and become a blockchain architect.

In the upcoming chapter, we will recap bits of what we have learned throughout this entire book for you, in addition to telling you about the global blockchain market and how you can start looking for jobs.

# [Questions](#toc.xhtml#s330a)

1.  **What does ERC stand for?**
    
    Ethereum Request for Comments. It provides guidance to developers regarding token construction on the Ethereum blockchain.
    
2.  **What is the ERC 20 token standard?**
    
    ERC 20 standard is an API specification governing how Ethereum tokens should be built. It dictates the interface that the smart contract for an Ethereum token has to respond to.
    
3.  **What are the primary rules laid down in the ERC 20 token standard?**
    
    the total supply of tokens,
    
    the storing and returning of balances,
    
    the allowance or access permissions
    
    the transfer of a token between users,
    
    the method of approval of transactions, and
    
    how users can look at all the information regarding a token.
    
4.  **What does the ERC 721 token standard entail?**
    
    ERC 721 is a free and open standard that lays down rules for the development of non-fungible tokens within the Ethereum ecosystem.
    
5.  **What is the biggest difference between the ERC 20 and the ERC 721 token standards?**
    
    ERC20 tokens are fungible and interchangeable, whereas ERC 721 tokens are non-fungible, unique, and not interchangeable.
    

# [Key terms](#toc.xhtml#s331a)

*   **ERC:** ERC stands for Ethereum Request for Comments. The ERC provides guidance to developers when it comes to creating tokens on Ethereum.
*   **ERC 20 Standard:** Ethereum's ERC 20 standard is an API specification governing how Ethereum tokens should be built.
*   **ERC 721 Standard:** This is a free and open standard that lays down rules for the development of non fungible tokens within the Ethereum ecosystem.

# [CHAPTER 16](#toc.xhtml#c16)

# [What Next? The Roadmap to Your Blockchain Architect](#toc.xhtml#c16)

# [Introduction](#toc.xhtml#s332a)

In this book, we have covered all the basics of what you need to begin your journey as a blockchain architect. We have learned the basic framework of a blockchain and how to create it, we have learned the requirements for becoming a certified blockchain architect, and as a bonus, in this last chapter, we have even learned how to make a cryptocurrency and an NFT.

In this last chapter, we take a look back at what we have already found out about becoming a blockchain architect throughout our journey together. In addition to that, we also lay out the current situation of the global blockchain market for you, so you would have an easier time hunting for jobs in the vast blockchain space.

# [Structure](#toc.xhtml#s333a)

The following topics will be covered in this chapter:

*   **Section 1:** The global blockchain job market  
    *   The booming blockchain job market and the growing demand for blockchain professionals
    *   Job market outlook and statistics
    *   Most popular positions in the blockchain space
*   **Section 2:** Recap  
    *   Why is becoming a blockchain architect strategically a good career choice?
    *   Steps to follow to become a certified blockchain architect
*   **Section 3:** Looking for jobs  
    *   What are the most in-demand blockchain skills at the moment?
    *   Searching for blockchain jobs: who is recruiting? Where to find them?
    *   Largest employers in the blockchain space
*   Summary

# [Objectives](#toc.xhtml#s334a)

This book is only just the beginning of your path to become a blockchain architect, so with this chapter, we hope to give you an apt roadmap to becoming a well-renowned blockchain architect. This chapter will be divided into three sections; Section 1 is where we discuss the global blockchain job market; in Section 2, you will find a brief recap of what you have found out about the steps to become a blockchain architect in this book; and finally, in Section 3, we will tell you how to go about job-hunting in the field of blockchain.

Without further ado, let us get into the chapter!

# [Section 1: The global blockchain job market](#toc.xhtml#s335a)

Even though blockchain started out as a base for the crypto Bitcoin, it has been a long time since blockchain broke out of the crypto industry and found widespread use cases in numerous other fields—from finance and healthcare to supply chain optimization to cloud computing, stock trading, real estate, and even government services.

Companies belonging to multiple industries across the globe are gradually seeing the merit of the decentralized ledger, signified by the massive wave of blockchain adoption among companies and businesses across the world meant to do away with critical pain points.

Even back in 2018, a survey conducted by PwC on 600 executives from 15 different regions showed that about 84% of these respondents were already using blockchain technology in some way or the other. A while later, in 2020, Deloitte surveyed 1,488 senior executives from various companies based in different parts of the world, and 39% of them had already integrated blockchain applications in varied ways into their existing products and services.

At present, as organizations in both the government and private sectors are expressing interest in this emerging technology, the job market for blockchain is burgeoning across the globe.

# [The booming blockchain job market and the growing demand for blockchain professionals](#toc.xhtml#s336a)

As the rate of blockchain adoption grows and grows around the world, naturally, career prospects for those possessing relevant skill sets are also booming. As you are aware, the "*relevant skill set*" for working in the blockchain is essentially a combination of the already existing programming technologies and concepts (for example, object-oriented programming and ledger economics) and a clear understanding of cryptography. While techies are very much in demand for the creation of blockchain applications, the demand for other roles like product managers and requirements specialists is also increasing within the industry.

# [The limited talent pool in the blockchain domain](#toc.xhtml#s337a)

What makes the blockchain sector an even more lucrative industry to become involved in is that since blockchain is still an emerging technology that had just started to gain traction in the latter half of the 2010s, blockchain-specific talent is still harder to find than other tech talents. It is true that blockchain has become one of the fastest-growing skill sets in the 2020s, but jobs within the industry are also growing at an astounding pace, and the salaries of blockchain architects and developers are also significantly higher than your usual developer jobs in other industries.

# [Job market outlook and statistics](#toc.xhtml#s338a)

It has been witnessed already that large organizations (such as Walmart, IBM, Oracle, JPMorgan Chase, Microsoft, Amazon, and American Express), as well as many medium and even smaller companies, are using, or have plans to deploy, blockchain-based mechanisms \[**[https://www.forbes.com/sites/michaeldelcastillo/2019/04/16/blockchain-goes-to-work/](https://www.forbes.com/sites/michaeldelcastillo/2019/04/16/blockchain-goes-to-work/)**\] to optimize various procedures. A Glassdoor study \[**[https://www.glassdoor.com/research/rise-in-bitcoin-jobs/](https://www.glassdoor.com/research/rise-in-bitcoin-jobs/)**\] from back in 2018 showed 1,775 unique blockchain and crypto jobs within the United States alone, which was a 300% increase compared to the August of 2017 when there were only 446 job openings of the sort.

A while later, in 2019, there were 1,135 jobs posted on the website Cryptocurrency Jobs from 472 companies and startups. According to statistics, the most needed roles within these postings were in blockchain engineering (31%), operations (17%), marketing (13%), design (10%), sales (9%), and customer support (7%). There were some jobs aside from these ones, which rounded up about 13% of the most in-demand blockchain roles. Please refer to the following figure:

![](images/Figure-16.1.jpg)

**Figure 16.1:** In-demand blockchain roles categorized by type, 2019.

Based on a report from Microsoft's employment-oriented social networking site LinkedIn, blockchain had been at the top of the list when the top ten hard skills of 2020 were evaluated. The role of a blockchain developer was the most emerging job in 2020, with an increase of 33x.

Furthermore, reportedly the increase in demand for blockchain developers across the globe was up by 300%–500% in 2021 \[**[https://theblockchaintest.com/uploads/resources/the](https://theblockchaintest.com/uploads/resources/the) Blockchain Academy**—**the Global Blockchain Employment Report**—**2022 March.pdf**\] as compared to that of 2020, as per Global Blockchain Employment Report 2021. While the United States happens to be at the lead when it comes to the list of countries with the highest openings for blockchain-related jobs, it is immediately followed by the UK and then India. In the United States, New York City and San Francisco have most of these job openings; as for the European market, London and Berlin are at the top in terms of blockchain-specific job offerings. In Asia, Singapore and Hong Kong have most of the blockchain job openings, and in Latin America, it is Buenos Aires.

Coming back to the LinkedIn report from 2020 \[**https://business.linkedin.com/content/dam/me/business/en-us/talent-solutions/emerging-jobs-report/India\_EJR\_2020\_Final.pdf**\] that listed the position of a blockchain developer as the most emerging job of 2020 and named blockchain one of the top ten hard skills, the report did not mention any particular hard skill highly connected to the role in question.

If you are wondering what hard skills are, they are essentially one's individual ability to come up with a solution for a particular problem. Soft skills, on the other hand, are those related to things like collaboration, decision-making, and adaptability.

The LinkedIn report in question established that while soft skills are evolving gradually over the span of several years, hard skills transform all at once and drastically as technology evolves. As the report named "*blockchain"* as the skill set that topped the list of hard skills in 2020, it had quite a critical effect on blockchain career prospects throughout the world.

Notably, a factor that is thought to affect the demand for blockchain professionals is the price of Bitcoin. Devin Banerjee, a senior financial services editor at LinkedIn, showed the interrelation of new blockchain developer hires with the monthly price of BTC. As you can see in the graph as follows, there is a high correlation between the monthly price of Bitcoin and the number of new hires; the number of new hires peaks just slightly after a shift in Bitcoin's price. Please refer to the following figure:

![](images/Figure-16.2.jpg)

**Figure 16.2:** The interrelation of new blockchain developer hires with the monthly price of BTC  
(**Source**: Devin Banerjee, LinkedIn)

However, despite the several decreases in Bitcoin's price and the natural high volatility that comes with cryptocurrencies, more and more people have taken an interest in the crypto space, and the demand for blockchain talent has remained high throughout the years.

Meanwhile, UpWork, the biggest freelancing platform, also rated blockchain skills as the topmost and fastest-growing skill set of 2020, with an increase of a solid 6,000%.

# [An estimation of the annual salary of a blockchain professional](#toc.xhtml#s339a)

If we look at some statistics for the kind of salary blockchain professionals receive, the skyrocketing demand for blockchain talent in recent years has also caused a significant hike in salaries for those working within the blockchain industry. Case in point, data from the online job-hunting site Hired shows the average salary for blockchain developers has come to between $150,000 and $175,000 \[**[https://www.dappuniversity.com/articles/blockchain-developer-salary](https://www.dappuniversity.com/articles/blockchain-developer-salary)**\]; you might be able to tell that this range is around $15,000 to $40,000 higher than what is the standard salary for an average software engineer. In fact, this salary range for blockchain jobs puts blockchain techies in a similar position as another group that is also high in demand at the moment—those who possess some sort of expertise in AI or artificial intelligence.

What is more, due to the lack of tech talent and relevant skills within the blockchain domain, employers are, of course, paying quite high remunerations to blockchain professionals. At the moment, the average annual income in the USA **\[[https://cryptocurrencyjobs.co/salaries/blockchain-developer/](https://cryptocurrencyjobs.co/salaries/blockchain-developer/)**\] for a blockchain developer happens to be $136,000, which is followed by an average of $87,500 within Asia and that of $73,300 per annum within the Europe markets. Remote blockchain developers can reportedly earn around $123,750 per year. In India, the average salary of a blockchain developer \[**[https://www.upgrad.com/blog/blockchain-developer-salary-india/](https://www.upgrad.com/blog/blockchain-developer-salary-india/)**\] can be anywhere between Rs. 5,00,000 and Rs. 30,00,000 LPA.

It goes without saying that the higher your experience and the more profound your particular set of blockchain skills, the higher your yearly income will be. Plus, depending on whether a candidate possesses advanced certifications or not, the salary package varies.

As for forecasts for the blockchain job market around the world, according to Gartner, worldwide spending in the blockchain sector is anticipated to grow to $15.9 billion by 2023, as compared to the $1.5 billion estimated back in 2018. Blockchain job openings are expected to increase on par with that growth.

# [Most popular positions in the blockchain space](#toc.xhtml#s340a)

As mentioned, while those affluent in technological knowledge can get an annual salary similar to what an AI developer would make within the blockchain industry, it is not the only kind of skill demanded in the space. In fact, over 40% of the blockchain jobs are non-technical, and since the talent pool for blockchain is very limited, the demand for people in the know about this particular niche is always high.

Let us see which roles make up the most in-demand blockchain jobs, shall we?

*   **Blockchain Architect:** Of course, as a blockchain architect, you are responsible for designing blockchain solutions, assigning roles, and keeping the entire team, which might consist of blockchain developers, network administrators, UX designers, and IT specialists, connected. This is one of the most integral roles in the making of a blockchain solution.
*   **Blockchain Developer:** Blockchain developers who can help companies and businesses explore various blockchain platforms are also in great demand. Blockchain developers are usually required to possess quite a lot of experience working with core programming languages such as C++, Python, and JavaScript.
*   **Blockchain Project Manager:** This role comes with the responsibility of connecting blockchain projects to those developing blockchain solutions. A blockchain project manager has to be equipped with the skills possessed by a conventional cloud project manager, along with superb communication skills.
*   **Blockchain UX Designer:** The job here, of course, is to shape a user interface that is both attractive and easy to use.
*   **Blockchain Quality Engineer:** A blockchain quality engineer is responsible for testing and ensuring that all areas of a certain project are of the expected quality. Essentially, they conduct the testing, as well as the automation of the frameworks for a blockchain project.
*   **Blockchain Legal Consultant:** As various businesses try to understand the intricacies of blockchain tech for the purpose of adoption, they look for legal expertise on what factors to consider while making an investment. Additionally, they might also require help with realizing the implications of their actions, finding out how to take care of their finances, and managing their identities. Good communication skills are required to become a blockchain legal consultant, along with a good grasp of relevant international laws.

Aside from the ones mentioned previously, other roles always in need of fulfillment within the blockchain-adjacent industry include those of accountants, public relations, marketers, crypto journalists and brokers, analysts, ICO advisors, and many more.

Now that you are aware of the current situation of the blockchain jobs market and have knowledge of the many varied career opportunities existing within the blockchain space, the next step in your roadmap to becoming a blockchain architect is, of course, to acquire the relevant skills. This is where we get into a recap of what we have already learned in this book about the benefits of becoming a blockchain architect and the steps to follow to achieve that goal.

# [Section 2: Recap](#toc.xhtml#s341a)

Why is the role of a blockchain architect one of the most lucrative career choices within the industry, and what are the steps you should take to join the ranks of the many well-accomplished blockchain architects active in today's time? You already know the answers, of course, but here is a quick recap anyway to help you plot out your roadmap to become a blockchain architect.

# [Why is becoming a blockchain architect strategically a good career choice?](#toc.xhtml#s342a)

Preparing for a career as a blockchain architect takes time and patience and might seem grueling at times. So, make sure to remind yourself time and again of the many benefits of entering the world of blockchain as a blockchain architect to keep yourself motivated!

The aforementioned benefits include:

# [The exceptionally high demand for blockchain architects](#toc.xhtml#s343a)

We know there is high demand for all sorts of blockchain professionals within the industry at the moment, so why become a blockchain architect in particular? Well, the demand for blockchain architects is even higher than those for most other professionals because there are very few people who can pull off designing an entire blockchain solution. Combine that skill with the leadership skills required of blockchain architects, and there are not really many people who can strike a balance of those two aspects well enough.

A blockchain architect has to be an especially innovative thinker to make designs for blockchain solutions that will drive a company's revenue. If you acquire the right skills, you will be in great demand within the blockchain space and can take your pick of jobs.

# [The incredible salary options](#toc.xhtml#s344a)

It is a no-brainer that being in high demand means the role of a blockchain architect also comes with similarly high salary options. Of course, that is true for all blockchain roles, as the high salaries for blockchain professionals result from a combination of the ever-increasing demand for blockchain professionals and the short supply of blockchain talent.

Once you have gathered some experience, you can expect enterprises to pay you a lot more to design a blockchain solution. Plus, you will be likely to get a lot more vacation time with incentives.

# [You have a lot of flexibility](#toc.xhtml#s345a)

As the head of a project, a blockchain architect has a lot of flexibility. Plus, you can even work remotely under certain conditions as a blockchain architect, which cannot be said for many other blockchain roles.

# [You can help bring in a technological revolution](#toc.xhtml#s346a)

It goes without saying that blockchain is a technological revolution reshaping existing business models and bringing greater efficiency to various existing business procedures. As a blockchain architect, you get to be an active part of this revolution.

# [Steps to follow to become a certified blockchain architect](#toc.xhtml#s347a)

Now, let us go through the steps you need to follow to become a blockchain architect once more:

*   Acquire thorough knowledge of blockchain fundamentals and know-how of the basic architectural design of a blockchain works
*   Be proficient in cryptography
*   Brush up your leadership skills, and make sure you possess strategic skills for faster problem solving
*   Possess some applicative knowledge of data structures
*   Acquire some expertise in front-end and back-end Web development
*   Master some programming languages
*   Know about different blockchain platforms, so you can pick the best one for your project
*   Acquire efficiency in smart contract development
*   Try to master blockchain interoperability
*   Gather expertise in blockchain development tools
*   Get certified by enrolling in an enterprise blockchain certification program
*   Keep up with industry trends

Again, reaching a position as important and responsible as that of a blockchain architect can take a long time. Make sure to remind yourself now and then of your love for blockchain technology and why you chose to make a career in blockchain in the first place.

Once you have acquired all the relevant skills to become a blockchain architect, you need to actually find that much-coveted job. So now we get to the part where we find out how you go about job-hunting in the blockchain space.

# [Section 3: looking for jobs](#toc.xhtml#s348a)

While blockchain technology is being deployed across a range of industries, finance is still the leading sector, immediately followed by healthcare, energy, and food or agriculture. Exchange platforms, development, and mining firms currently account for 85% of blockchain professionals employed. In this section, we learn where you can search for blockchain jobs and who the biggest employers are.

# [What are the most in-demand blockchain skills at the moment?](#toc.xhtml#s349a)

The most in-demand blockchain skills as of right now would be Hyperledger, Solidity, Ripple, and Ethereum. However, due to the relatively newness of the blockchain space, many companies often employ professionals with relevant skillsets for blockchain roles. For instance, someone with a bachelor's degree in mathematics or computer science who possess a basic knowledge of mathematics and algorithms and is well-versed in programming languages such as C, C++, Java, Rust, and Python can be chosen for the role of blockchain developer.

Another thing to keep in mind when looking for a blockchain job is that while you might expect that you will not get hired as a blockchain architect without any previous experience within the blockchain industry, in particular, there are many employers who will take into consideration prior work experience in other industries and prioritize your passion for the blockchain technology. Therefore, you should always apply for a position in a blockchain project you are interested in.

# [Searching for blockchain jobs: who is recruiting? Where to find them?](#toc.xhtml#s350a)

There are four significant types of employers in the blockchain job market who belong to any of the following categories:

*   **Industries**: Big companies from both private and public sectors, including banks, accountancy firms, oil and gas, insurance, retailers, law offices, and so on, make up this category of employers.
*   **Startups**: Of course, there are independent businesses creating a lot of job opportunities for blockchain professionals.
*   **Tech Firms**: As these companies might end up losing a lot once blockchain takes over the tech world, they look for blockchain expertise as they attempt to shift over to a decentralized system.
*   **Governments**: As more and more governments from many countries across the world warm up to the concepts of the decentralized ledger and cryptocurrencies, they are also hiring blockchain and crypto experts to advise them.

When it comes to looking for blockchain jobs, aside from checking the regular job-hunting websites like LinkedIn, you should also check out cryptojobslist.com, a platform that lists almost all major blockchain and Web3 jobs across the globe. You can choose from both remote and in-office working opportunities.

# [Largest employers in the blockchain space](#toc.xhtml#s351a)

Crypto exchanges are the biggest employers in the blockchain jobs markets, followed by development and mining firms. The biggest employers when it comes to blockchain job postings usually include Deloitte, IBM, Accenture, Cisco, and Collins aerospace. Among other top positions, holders are also Ernst & Young, Coinbase, Huobi Global, OKEx, Overstock.com, Ripple, Verizon, Circle, Kraken, ConsenSys, JPMorgan Chase, and Signature Bank. Please refer to the following figure:

![](images/Figure-16.3.jpg)

**Figure 16.3:** The top employers in the blockchain jobs market  
(**Source**: Glassdoor)

# [Conclusion](#toc.xhtml#s352a)

Blockchain technology continues to evolve with every passing day, and it is expected that the more mature the technology grows, the more professional opportunities it will create. Therefore, blockchain expertise will stay in demand for years to come.

The position of a blockchain architect is that of a leader in a blockchain project, so as varied use cases of the technology continue to pop up, there will be exciting opportunities for you to innovate, and you will also have the space and the flexibility to try out new things. The experience of watching your ideas come to life is unique to an architect, and more than anything else, we hope you achieve your goal of becoming a blockchain architect just so you can live that experience too.

We wish you good luck on your journey to becoming a blockchain architect and reaching the very top.

# [Index](#toc.xhtml#ind)

A

accrual accounting [73](#c05.xhtml#page73), [74](#c05.xhtml#page74)

Alchemy [227](#c15.xhtml#page227)

Apache Commons [174](#c11.xhtml#page174), [175](#c11.xhtml#page175)

Application Programming Interfaces (APIs) [19](#c02.xhtml#page19)

archival node [125](#c08.xhtml#page125)

Arduino IDE [200](#c13.xhtml#page200), [201](#c13.xhtml#page201)

asset types

fungible assets [96](#c06.xhtml#page96)

intangible assets [96](#c06.xhtml#page96)

non-fungible assets [96](#c06.xhtml#page96)

asymmetric encryption [52](#c04.xhtml#page52)

asymmetric encryption cryptography [54](#c04.xhtml#page54)

attributes, blockchain

anonymity [6](#c01.xhtml#page6)

cost-effective [6](#c01.xhtml#page6)

cryptography [5](#c01.xhtml#page5)

decentralized [5](#c01.xhtml#page5)

immutability [6](#c01.xhtml#page6)

smart contracts [6](#c01.xhtml#page6)

transparency [6](#c01.xhtml#page6)

Augur (REP) [220](#c15.xhtml#page220)

authority node [125](#c08.xhtml#page125)

AWS managed blockchains

used, for deploying blockchain instance [129](#c08.xhtml#page129)

B

BaaSp

backend services [128](#c08.xhtml#page128)

experience [129](#c08.xhtml#page129)

pricing support [128](#c08.xhtml#page128)

security [128](#c08.xhtml#page128)

selecting [128](#c08.xhtml#page128)

BaaS providers

examples [128](#c08.xhtml#page128)

banking

about [71](#c05.xhtml#page71)

importance [72](#c05.xhtml#page72)

bartering

about [67](#c05.xhtml#page67)

benefits [68](#c05.xhtml#page68)

defining [67](#c05.xhtml#page67)

Basic Attention Token (BAT) [98](#c06.xhtml#page98), [220](#c15.xhtml#page220)

Bitcoin

about [85](#c06.xhtml#page85)

cryptographic measures [85](#c06.xhtml#page85)

history [85](#c06.xhtml#page85)\-[87](#c06.xhtml#page87)

versus Ethereum [89](#c06.xhtml#page89)\-[91](#c06.xhtml#page91)

blockchain

about [3](#c01.xhtml#page3), [104](#c07.xhtml#page104)

attributes [5](#c01.xhtml#page5)

bitcoin problem [140](#c09.xhtml#page140)

clearing server [214](#c14.xhtml#page214)

consensus mechanism [152](#c10.xhtml#page152)

consensus mechanism types [152](#c10.xhtml#page152)

cryptography [54](#c04.xhtml#page54)\-[56](#c04.xhtml#page56)

Ethereum solution [140](#c09.xhtml#page140)

finance use cases [105](#c07.xhtml#page105)

functioning [5](#c01.xhtml#page5)

government use cases [108](#c07.xhtml#page108)

hashing [58](#c04.xhtml#page58), [59](#c04.xhtml#page59)

history [3](#c01.xhtml#page3)

network setup [214](#c14.xhtml#page214), [215](#c14.xhtml#page215)

nodes [212](#c14.xhtml#page212)\-[214](#c14.xhtml#page214)

node structure [209](#c14.xhtml#page209), [210](#c14.xhtml#page210)

origin [3](#c01.xhtml#page3)

purposes [27](#c02.xhtml#page27), [28](#c02.xhtml#page28)

setting up [211](#c14.xhtml#page211), [212](#c14.xhtml#page212)

smartphone app [214](#c14.xhtml#page214)

versus database [24](#c02.xhtml#page24)\-[26](#c02.xhtml#page26)

blockchain architecture

about [4](#c01.xhtml#page4), [147](#c10.xhtml#page147), [239](#c16.xhtml#page239), [240](#c16.xhtml#page240)

benefits [240](#c16.xhtml#page240)

blockchain data structure [38](#c03.xhtml#page38)

blockchain platform [156](#c10.xhtml#page156)

career selection [12](#c01.xhtml#page12), [240](#c16.xhtml#page240)

certification [11](#c01.xhtml#page11), [149](#c10.xhtml#page149), [241](#c16.xhtml#page241), [242](#c16.xhtml#page242)

certifications [148](#c10.xhtml#page148)

characteristics [40](#c03.xhtml#page40)

components [4](#c01.xhtml#page4), [40](#c03.xhtml#page40), [41](#c03.xhtml#page41), [42](#c03.xhtml#page42)

consortium blockchain architecture [11](#c01.xhtml#page11)

cryptography [147](#c10.xhtml#page147)

data structure [148](#c10.xhtml#page148)

developing [149](#c10.xhtml#page149)

examination [148](#c10.xhtml#page148), [149](#c10.xhtml#page149)

flexibility [241](#c16.xhtml#page241)

importance [10](#c01.xhtml#page10)

multiple programming languages [147](#c10.xhtml#page147)

need for [11](#c01.xhtml#page11), [12](#c01.xhtml#page12)

private blockchain architecture [11](#c01.xhtml#page11)

public blockchain architecture [10](#c01.xhtml#page10)

salary options [240](#c16.xhtml#page240)

skills [13](#c01.xhtml#page13)\-[15](#c01.xhtml#page15)

smart contract development [148](#c10.xhtml#page148)

technology revolution [241](#c16.xhtml#page241)

types [10](#c01.xhtml#page10), [42](#c03.xhtml#page42), [43](#c03.xhtml#page43), [149](#c10.xhtml#page149)

versus database architecture [37](#c03.xhtml#page37), [38](#c03.xhtml#page38)

web development [148](#c10.xhtml#page148)

Blockchain as a Service (BaaS) [10](#c01.xhtml#page10), [127](#c08.xhtml#page127)

blockchain data structure

about [38](#c03.xhtml#page38)

advantages [39](#c03.xhtml#page39), [40](#c03.xhtml#page40)

linked lists [39](#c03.xhtml#page39)

pointers [38](#c03.xhtml#page38)

blockchain developer [239](#c16.xhtml#page239)

blockchain for businesses

about [112](#c07.xhtml#page112)

Internet-of-Things (IoT) [113](#c07.xhtml#page113)

supply chain management [113](#c07.xhtml#page113)

blockchain instance

deploying, with AWS managed blockchains [129](#c08.xhtml#page129)

blockchain job market

about [234](#c16.xhtml#page234), [235](#c16.xhtml#page235)

annual salary, estimating [238](#c16.xhtml#page238)

growth [235](#c16.xhtml#page235)

outlook and statistics [235](#c16.xhtml#page235)\-[237](#c16.xhtml#page237)

positions [238](#c16.xhtml#page238), [239](#c16.xhtml#page239)

skills [235](#c16.xhtml#page235)

blockchain legal consultant [239](#c16.xhtml#page239)

blockchain network

creating [152](#c10.xhtml#page152)

blockchain node

about [121](#c08.xhtml#page121), [122](#c08.xhtml#page122)

accessibility [123](#c08.xhtml#page123)

deploying [127](#c08.xhtml#page127)

full nodes [124](#c08.xhtml#page124)

functions [123](#c08.xhtml#page123)

growth accommodation [123](#c08.xhtml#page123)

point of communication [124](#c08.xhtml#page124)

purposes [122](#c08.xhtml#page122)

storage [124](#c08.xhtml#page124)

transaction processing [123](#c08.xhtml#page123)

types [124](#c08.xhtml#page124)

blockchain nodes

designing [206](#c14.xhtml#page206)\-[209](#c14.xhtml#page209)

blockchain platform

developing [155](#c10.xhtml#page155), [156](#c10.xhtml#page156)

blockchain project manager [239](#c16.xhtml#page239)

blockchain quality engineer [239](#c16.xhtml#page239)

blockchain serve

purposes [151](#c10.xhtml#page151)

blockchain solutions

benefits [6](#c01.xhtml#page6), [7](#c01.xhtml#page7)

integrating [6](#c01.xhtml#page6)

blockchain solutions for businesses [7](#c01.xhtml#page7)

applications [8](#c01.xhtml#page8), [9](#c01.xhtml#page9)

benefits [7](#c01.xhtml#page7), [8](#c01.xhtml#page8)

use cases [9](#c01.xhtml#page9)

blockchain technology

about [242](#c16.xhtml#page242)

job emloyers [243](#c16.xhtml#page243)

jobs [242](#c16.xhtml#page242), [243](#c16.xhtml#page243)

skills [242](#c16.xhtml#page242)

blockchain UX Designer [239](#c16.xhtml#page239)

blockchain, versus database

architecture [26](#c02.xhtml#page26)

centralization [26](#c02.xhtml#page26)

data handling [26](#c02.xhtml#page26)

data integrity [26](#c02.xhtml#page26)

data transparency [26](#c02.xhtml#page26)

scalability and cost [26](#c02.xhtml#page26)

bytecode [190](#c12.xhtml#page190)

Byzantine Fault Tolerance (BFT) [44](#c03.xhtml#page44), [45](#c03.xhtml#page45), [135](#c09.xhtml#page135), [143](#c09.xhtml#page143)

C

C++

about [163](#c11.xhtml#page163)

code example [163](#c11.xhtml#page163)

cash accounting [73](#c05.xhtml#page73)

central influence

in traditional finance [75](#c05.xhtml#page75), [76](#c05.xhtml#page76)

centralized database

about [19](#c02.xhtml#page19)

versus decentralized database [36](#c03.xhtml#page36), [37](#c03.xhtml#page37)

versus distributed database [36](#c03.xhtml#page36), [37](#c03.xhtml#page37)

cipher [52](#c04.xhtml#page52)

clearing server [214](#c14.xhtml#page214)

Cli [177](#c11.xhtml#page177)

client-server architecture

about [33](#c03.xhtml#page33), [34](#c03.xhtml#page34)

advantages [34](#c03.xhtml#page34)

disadvantages [35](#c03.xhtml#page35)

peer-to-peer network architecture [35](#c03.xhtml#page35), [36](#c03.xhtml#page36)

cloud database [22](#c02.xhtml#page22)

cloud IDEs [196](#c13.xhtml#page196)

components, blockchain architecture

block [4](#c01.xhtml#page4)

consensus algorithm [4](#c01.xhtml#page4)

hash [4](#c01.xhtml#page4)

miners [4](#c01.xhtml#page4)

node [4](#c01.xhtml#page4)

consensus algorithms [134](#c09.xhtml#page134), [135](#c09.xhtml#page135)

consensus mechanism types

Delegated Proof of Stake (DPoS) [153](#c10.xhtml#page153)

Proof of Activity (PoA) [153](#c10.xhtml#page153)

Proof of Authority (PoA) [154](#c10.xhtml#page154)

Proof of Capacity (PoC) [154](#c10.xhtml#page154)

Proof of Elapsed Time (PoET) [154](#c10.xhtml#page154)

Proof of Identity (PoI) [154](#c10.xhtml#page154)

Proof of Work (PoW) [152](#c10.xhtml#page152)

consortium architecture [150](#c10.xhtml#page150)

consortium blockchain architecture [11](#c01.xhtml#page11), [46](#c03.xhtml#page46)

controller node [207](#c14.xhtml#page207)

C# programming language

about [180](#c12.xhtml#page180)

code example [181](#c12.xhtml#page181)

features [180](#c12.xhtml#page180), [181](#c12.xhtml#page181)

Crash Failure Tolerance [135](#c09.xhtml#page135)

creation bytecode [189](#c12.xhtml#page189)

cryptocurrency

developing, on Ethereum blockchain [221](#c15.xhtml#page221)

cryptographic hash function

about [57](#c04.xhtml#page57)

properties [57](#c04.xhtml#page57), [58](#c04.xhtml#page58)

cryptography

about [51](#c04.xhtml#page51)

in blockchain [54](#c04.xhtml#page54)\-[56](#c04.xhtml#page56)

methods [53](#c04.xhtml#page53)

need for [147](#c10.xhtml#page147)

working [53](#c04.xhtml#page53)

cryptography concepts

about [51](#c04.xhtml#page51)

cipher [52](#c04.xhtml#page52)

decryption [51](#c04.xhtml#page51)

encryption [51](#c04.xhtml#page51)

key [52](#c04.xhtml#page52)

custodian node [207](#c14.xhtml#page207)

D

database architecture

versus blockchain architecture [37](#c03.xhtml#page37), [38](#c03.xhtml#page38)

database model types

about [19](#c02.xhtml#page19)

centralized database [19](#c02.xhtml#page19)

cloud database [22](#c02.xhtml#page22)

distributed database [19](#c02.xhtml#page19)

graph database [23](#c02.xhtml#page23)

hierarchical database [22](#c02.xhtml#page22)

network database [23](#c02.xhtml#page23)

NoSQL database [21](#c02.xhtml#page21)

object-oriented database [22](#c02.xhtml#page22)

relational database [20](#c02.xhtml#page20)

database systems [18](#c02.xhtml#page18)

data structure [148](#c10.xhtml#page148)

decentralized database

versus centralized database [36](#c03.xhtml#page36), [37](#c03.xhtml#page37)

versus distributed database [36](#c03.xhtml#page36), [37](#c03.xhtml#page37)

decentralized finance (DeFi)

about [91](#c06.xhtml#page91)

growth [92](#c06.xhtml#page92), [93](#c06.xhtml#page93)

overview [91](#c06.xhtml#page91), [92](#c06.xhtml#page92)

use cases [93](#c06.xhtml#page93)

decryption [51](#c04.xhtml#page51)

Delegated Proof of Stake [142](#c09.xhtml#page142)

Delegated Proof of Stake (PoS) [143](#c09.xhtml#page143)

advantages [142](#c09.xhtml#page142)

deployed bytecode [190](#c12.xhtml#page190)

digital era [67](#c05.xhtml#page67)

distributed database

about [19](#c02.xhtml#page19)

versus centralized database [36](#c03.xhtml#page36), [37](#c03.xhtml#page37)

versus decentralized database [36](#c03.xhtml#page36), [37](#c03.xhtml#page37)

Distributed Ledger Technology (DLT) [76](#c05.xhtml#page76), [77](#c05.xhtml#page77)

advantages [78](#c05.xhtml#page78), [79](#c05.xhtml#page79)

properties [78](#c05.xhtml#page78), [79](#c05.xhtml#page79)

usage [78](#c05.xhtml#page78), [79](#c05.xhtml#page79)

E

Eclipse [198](#c13.xhtml#page198), [199](#c13.xhtml#page199)

encryption

about [51](#c04.xhtml#page51)

need for [52](#c04.xhtml#page52), [53](#c04.xhtml#page53)

types [52](#c04.xhtml#page52)

endorser [208](#c14.xhtml#page208)

enforcer [209](#c14.xhtml#page209)

EOS (EOS) [220](#c15.xhtml#page220)

Equity Token Offerings (ETOs) [107](#c07.xhtml#page107)

ERC [20](#c02.xhtml#page20) token

about [97](#c06.xhtml#page97)

creating [221](#c15.xhtml#page221)

need for [97](#c06.xhtml#page97), [98](#c06.xhtml#page98)

smart contract, functioning [222](#c15.xhtml#page222), [223](#c15.xhtml#page223)

smart contract, writing [223](#c15.xhtml#page223)\-[226](#c15.xhtml#page226)

ERC [20](#c02.xhtml#page20) token standard

about [218](#c15.xhtml#page218), [219](#c15.xhtml#page219)

functions [219](#c15.xhtml#page219)

reference link [218](#c15.xhtml#page218)

ERC 721 token standard

about [220](#c15.xhtml#page220), [221](#c15.xhtml#page221)

reference link [220](#c15.xhtml#page220)

Ethereum [156](#c10.xhtml#page156)

about [85](#c06.xhtml#page85)

history [88](#c06.xhtml#page88), [89](#c06.xhtml#page89)

versus Bitcoin [89](#c06.xhtml#page89)\-[91](#c06.xhtml#page91)

Ethereum blockchain

cryptocurrency, developing [221](#c15.xhtml#page221)

Ethereum Bytecode

about [188](#c12.xhtml#page188), [189](#c12.xhtml#page189)

bytecode [190](#c12.xhtml#page190)

creation bytecode [189](#c12.xhtml#page189)

deployed bytecode [190](#c12.xhtml#page190)

init code [190](#c12.xhtml#page190)

runtime bytecode [190](#c12.xhtml#page190)

Ethereum Request for Comments (ERC) [217](#c15.xhtml#page217)

Ethereum's ERC standards [218](#c15.xhtml#page218)

Ethereum WebAssembly (eWASM) [187](#c12.xhtml#page187), [188](#c12.xhtml#page188)

F

finance use cases, blockchain

capital markets [108](#c07.xhtml#page108)

cross-border payments [105](#c07.xhtml#page105), [106](#c07.xhtml#page106)

fundraising [107](#c07.xhtml#page107), [108](#c07.xhtml#page108)

lending platforms [106](#c07.xhtml#page106), [107](#c07.xhtml#page107)

flowchart

about [168](#c11.xhtml#page168)

example [169](#c11.xhtml#page169)

shapes [168](#c11.xhtml#page168)

founder node [207](#c14.xhtml#page207)

fraud proof [209](#c14.xhtml#page209)

full maintainer [208](#c14.xhtml#page208)

full nodes

about [124](#c08.xhtml#page124)

archival node [125](#c08.xhtml#page125)

authority node [125](#c08.xhtml#page125)

pruned node [125](#c08.xhtml#page125)

fundamentals of blockchain [149](#c10.xhtml#page149)

fungible assets [96](#c06.xhtml#page96)

Fuzzy [177](#c11.xhtml#page177)

G

Go Kit [176](#c11.xhtml#page176)

Google Guava [174](#c11.xhtml#page174)

Go programming language (Golang)

about [164](#c11.xhtml#page164)

code example [165](#c11.xhtml#page165)

GORM [176](#c11.xhtml#page176)

government use cases, blockchain

administration [111](#c07.xhtml#page111)

corruption, reducing [111](#c07.xhtml#page111)

digital identity management [109](#c07.xhtml#page109)

regulation [110](#c07.xhtml#page110)

voter fraud, eliminating [111](#c07.xhtml#page111), [112](#c07.xhtml#page112)

graph database [23](#c02.xhtml#page23)

H

hash function [56](#c04.xhtml#page56), [57](#c04.xhtml#page57)

hashing

about [54](#c04.xhtml#page54), [56](#c04.xhtml#page56)

in blockchain [58](#c04.xhtml#page58), [59](#c04.xhtml#page59)

hash tree [59](#c04.xhtml#page59)

hierarchical database [22](#c02.xhtml#page22)

Hyperledger Fabric [210](#c14.xhtml#page210)

I

IBM Blockchain [156](#c10.xhtml#page156)

Information Management System (IMS) [23](#c02.xhtml#page23)

init code [190](#c12.xhtml#page190)

Initial Coin Offerings (ICOs) [219](#c15.xhtml#page219)

Initial Exchange Offerings (IEOs) [107](#c07.xhtml#page107)

intangible assets [96](#c06.xhtml#page96)

integrated development environments (IDEs)

about [194](#c13.xhtml#page194)

Arduino IDE [200](#c13.xhtml#page200), [201](#c13.xhtml#page201)

characteristics [196](#c13.xhtml#page196)\-[198](#c13.xhtml#page198)

components [195](#c13.xhtml#page195)

Eclipse [198](#c13.xhtml#page198), [199](#c13.xhtml#page199)

IntelliJ IDE [201](#c13.xhtml#page201), [202](#c13.xhtml#page202)

MPLAB X [200](#c13.xhtml#page200)

online Remix IDE [202](#c13.xhtml#page202), [203](#c13.xhtml#page203)

types [195](#c13.xhtml#page195), [196](#c13.xhtml#page196)

IntelliJ IDE [201](#c13.xhtml#page201), [202](#c13.xhtml#page202)

Internet-of-Things (IoT) [113](#c07.xhtml#page113)

agriculture [114](#c07.xhtml#page114)

automotive industry [114](#c07.xhtml#page114)

pharmaceutical industry [114](#c07.xhtml#page114)

smart homes [114](#c07.xhtml#page114)

J

Jackson [175](#c11.xhtml#page175)

Java

about [162](#c11.xhtml#page162)

code example [162](#c11.xhtml#page162)

JavaScript [182](#c12.xhtml#page182)

code example [182](#c12.xhtml#page182), [183](#c12.xhtml#page183)

JAXB [175](#c11.xhtml#page175)

K

Keras [174](#c11.xhtml#page174)

key [52](#c04.xhtml#page52)

L

ledger accounting [74](#c05.xhtml#page74), [75](#c05.xhtml#page75)

lightning nodes [126](#c08.xhtml#page126)

light node [126](#c08.xhtml#page126)

linked lists [39](#c03.xhtml#page39)

M

MakerDAO (MKR) [220](#c15.xhtml#page220)

master node [126](#c08.xhtml#page126), [207](#c14.xhtml#page207)

math puzzles

used, for preventing Byzantine failures [136](#c09.xhtml#page136)\-[138](#c09.xhtml#page138)

Merkle tree

about [59](#c04.xhtml#page59)

benefits, in blockchain [61](#c04.xhtml#page61), [62](#c04.xhtml#page62)

creating [59](#c04.xhtml#page59)\-[61](#c04.xhtml#page61)

functions [59](#c04.xhtml#page59)

Metamask [227](#c15.xhtml#page227)

miner node [125](#c08.xhtml#page125)

mobile development IDEs [195](#c13.xhtml#page195)

Mockito [176](#c11.xhtml#page176)

money

about [68](#c05.xhtml#page68)

categories [69](#c05.xhtml#page69), [70](#c05.xhtml#page70)

creating [71](#c05.xhtml#page71)

defining [69](#c05.xhtml#page69)

money classes

M1 [70](#c05.xhtml#page70)

M2 [70](#c05.xhtml#page70)

M3 [70](#c05.xhtml#page70)

MPLAB X [200](#c13.xhtml#page200)

MultiChain [210](#c14.xhtml#page210)

multiple programming languages

about [147](#c10.xhtml#page147)

C++ [147](#c10.xhtml#page147)

Java [147](#c10.xhtml#page147)

JavaScript [148](#c10.xhtml#page148)

Python [147](#c10.xhtml#page147)

N

network architecture

about [32](#c03.xhtml#page32), [33](#c03.xhtml#page33)

client/server architecture [33](#c03.xhtml#page33), [34](#c03.xhtml#page34)

network database [23](#c02.xhtml#page23)

Networking Operating Systems (NOS) [35](#c03.xhtml#page35)

NodeJS/NPM [227](#c15.xhtml#page227)

nodes [212](#c14.xhtml#page212)\-[214](#c14.xhtml#page214)

node structure

on blockchain [209](#c14.xhtml#page209), [210](#c14.xhtml#page210)

non-fungible assets [96](#c06.xhtml#page96)

non-fungible token (NFT)

about [95](#c06.xhtml#page95), [98](#c06.xhtml#page98)

building [227](#c15.xhtml#page227)

creating [226](#c15.xhtml#page226)

deploying [228](#c15.xhtml#page228)\-[230](#c15.xhtml#page230)

future [99](#c06.xhtml#page99)

metadata, storing [227](#c15.xhtml#page227)

prerequisites [227](#c15.xhtml#page227)

trades, working [98](#c06.xhtml#page98)

NoSQL database [21](#c02.xhtml#page21)

Numpy [173](#c11.xhtml#page173)

O

object-oriented database [22](#c02.xhtml#page22)

Object-Oriented Programming Languages (OOPs) [22](#c02.xhtml#page22)

OmiseGO (OMG) [220](#c15.xhtml#page220)

one-to-many relationship [22](#c02.xhtml#page22)

online Remix IDE

setting up, for solidity smart contract development [203](#c13.xhtml#page203)

P

partial maintainer [208](#c14.xhtml#page208)

peer-to-peer network architecture [35](#c03.xhtml#page35), [36](#c03.xhtml#page36)

advantages [36](#c03.xhtml#page36)

disadvantages [36](#c03.xhtml#page36)

Peer-To-Peer (P2P) [85](#c06.xhtml#page85)

pointers [38](#c03.xhtml#page38)

private blockchain [140](#c09.xhtml#page140), [141](#c09.xhtml#page141)

private blockchain architecture [11](#c01.xhtml#page11), [44](#c03.xhtml#page44)

Byzantine Fault Tolerance (BFT) [45](#c03.xhtml#page45)

developing [150](#c10.xhtml#page150)

programming language libraries

about [172](#c11.xhtml#page172)

Numpy [173](#c11.xhtml#page173)

PyTorch [173](#c11.xhtml#page173)

Scikit-Learn [174](#c11.xhtml#page174)

TensorFlow [172](#c11.xhtml#page172)

programming languages [160](#c11.xhtml#page160)

Proof of Authority [143](#c09.xhtml#page143)

Proof of Stake (PoS) [44](#c03.xhtml#page44), [89](#c06.xhtml#page89), [141](#c09.xhtml#page141), [143](#c09.xhtml#page143)

advantages [142](#c09.xhtml#page142)

Proof of Stake (PoS) consensus algorithm [44](#c03.xhtml#page44)

Proof of Work (PoW) [89](#c06.xhtml#page89), [140](#c09.xhtml#page140)

advantages [138](#c09.xhtml#page138), [139](#c09.xhtml#page139)

disadvantages [138](#c09.xhtml#page138), [139](#c09.xhtml#page139)

Proof of Work (PoW) consensus algorithm [10](#c01.xhtml#page10), [43](#c03.xhtml#page43), [44](#c03.xhtml#page44), [135](#c09.xhtml#page135), [136](#c09.xhtml#page136)

pruned node [125](#c08.xhtml#page125)

lightning nodes [126](#c08.xhtml#page126)

light node [126](#c08.xhtml#page126)

master node [126](#c08.xhtml#page126)

miner node [125](#c08.xhtml#page125)

staking node [126](#c08.xhtml#page126)

supernodes [126](#c08.xhtml#page126)

pseudocode

about [170](#c11.xhtml#page170)

example [170](#c11.xhtml#page170), [171](#c11.xhtml#page171)

public architecture [149](#c10.xhtml#page149)

public blockchain architecture [10](#c01.xhtml#page10), [43](#c03.xhtml#page43)

Python

about [160](#c11.xhtml#page160)

code example [161](#c11.xhtml#page161)

factors [161](#c11.xhtml#page161)

PyTorch [173](#c11.xhtml#page173)

R

relational database [20](#c02.xhtml#page20)

Remix Online IDE [202](#c13.xhtml#page202), [203](#c13.xhtml#page203)

Rholang [186](#c12.xhtml#page186), [187](#c12.xhtml#page187)

runtime bytecode [190](#c12.xhtml#page190)

S

scalability

about [26](#c02.xhtml#page26)

consensus mechanisms [26](#c02.xhtml#page26)

cryptographic verification [26](#c02.xhtml#page26)

redundancy of data [27](#c02.xhtml#page27)

Scikit-Learn [174](#c11.xhtml#page174)

Apache Commons [174](#c11.xhtml#page174), [175](#c11.xhtml#page175)

Cli [177](#c11.xhtml#page177)

Fuzzy [177](#c11.xhtml#page177)

Go Kit [176](#c11.xhtml#page176)

Google Guava [174](#c11.xhtml#page174)

GORM [176](#c11.xhtml#page176)

Jackson [175](#c11.xhtml#page175)

JAXB [175](#c11.xhtml#page175)

Keras [174](#c11.xhtml#page174)

Mockito [176](#c11.xhtml#page176)

Simple and Fast Multimedia Library (SFML) [176](#c11.xhtml#page176)

Vegeta [177](#c11.xhtml#page177)

Security Token Offerings (STOs) [107](#c07.xhtml#page107)

self-sovereign digital ID

electronic health records (EHRs) [110](#c07.xhtml#page110)

streamlined KYC [110](#c07.xhtml#page110)

verification of academic credentials [109](#c07.xhtml#page109), [110](#c07.xhtml#page110)

Simple and Fast Multimedia Library (SFML) [176](#c11.xhtml#page176)

Simple Payment Verification (SPV) [62](#c04.xhtml#page62)

Simplicity

about [183](#c12.xhtml#page183), [184](#c12.xhtml#page184)

code example [184](#c12.xhtml#page184)\-[186](#c12.xhtml#page186)

Simplified Payment Verification (SPV) [209](#c14.xhtml#page209)

smart contract development [148](#c10.xhtml#page148)

smart contracts, automation tasks

about [114](#c07.xhtml#page114)

inventory management [116](#c07.xhtml#page116)

real estate [114](#c07.xhtml#page114), [115](#c07.xhtml#page115)

retail operations [115](#c07.xhtml#page115)

smartphone app [214](#c14.xhtml#page214)

Software-as-a-Service (SaaS) [196](#c13.xhtml#page196)

Solidity [166](#c11.xhtml#page166)

solidity smart contract development

online Remix IDE, setting up [203](#c13.xhtml#page203)

staking node [126](#c08.xhtml#page126)

supernodes [126](#c08.xhtml#page126)

symmetric encryption [52](#c04.xhtml#page52)

symmetric encryption cryptography [54](#c04.xhtml#page54)

T

technical problems

antivirus software [127](#c08.xhtml#page127)

bandwidth limitations [127](#c08.xhtml#page127)

hackers [127](#c08.xhtml#page127)

TensorFlow [172](#c11.xhtml#page172)

Tezos [156](#c10.xhtml#page156)

tiered network architecture [33](#c03.xhtml#page33)

tokenization

about [95](#c06.xhtml#page95), [96](#c06.xhtml#page96)

asset types [96](#c06.xhtml#page96)

traditional accounting

about [73](#c05.xhtml#page73)

accrual accounting [73](#c05.xhtml#page73)

cash accounting [73](#c05.xhtml#page73)

methods [72](#c05.xhtml#page72)

types [73](#c05.xhtml#page73)

traditional database

purposes [28](#c02.xhtml#page28), [29](#c02.xhtml#page29)

versus blockchain [24](#c02.xhtml#page24)\-[26](#c02.xhtml#page26)

traditional finance

central influence [75](#c05.xhtml#page75), [76](#c05.xhtml#page76)

transaction [72](#c05.xhtml#page72), [73](#c05.xhtml#page73)

transactor [208](#c14.xhtml#page208)

Tron (TRX) [220](#c15.xhtml#page220)

types, blockchain architecture

consortium architecture [150](#c10.xhtml#page150)

private architecture [149](#c10.xhtml#page149)

public architecture [149](#c10.xhtml#page149)

U

Unique Node List [143](#c09.xhtml#page143)

use cases, decentralized finance (DeFi)

decentralized asset management [94](#c06.xhtml#page94)

decentralized exchange platforms (DEX) [94](#c06.xhtml#page94)

decentralized insurance [95](#c06.xhtml#page95)

decentralized lending and borrowing platforms [94](#c06.xhtml#page94)

decentralized marketplaces [95](#c06.xhtml#page95)

decentralized payments [93](#c06.xhtml#page93)

decentralized trading [93](#c06.xhtml#page93)

synthetic assets [95](#c06.xhtml#page95)

tokenization [95](#c06.xhtml#page95)

V

validator [208](#c14.xhtml#page208)

Vegeta [177](#c11.xhtml#page177)

viewer [209](#c14.xhtml#page209)

Vyper [167](#c11.xhtml#page167)

W

web development [148](#c10.xhtml#page148)