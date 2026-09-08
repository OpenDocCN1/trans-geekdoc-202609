Abstract

This book provides a detailed insight of the concepts, mechanics, functions, governance, and real-world applications of the blockchain technology. The book is divided into ten chapters – Introduction, Blockchain History, Blockchain Mechanics, Blockchain Functions, Blockchain Governance, Blockchain in Real World, Blockchain based cryptocurrency – Bitcoin, Blockchain based cryptocurrency – Ethereum, Blockchain Platforms, and Future of Blockchain. 

We start with an overview of blockchain in the ‘Introduction’ chapter. In the next chapter, we study brief history if internet (Web 1.0, 2.0, and 3.0). We look at blockchain history and how blockchain technology has change the internet from information exchange to value exchange. The we study Blockchain Mechanics wherein we understand the key features of blockchain like cryptography, transparency, immutability, and disintermediation effect. In the next chapter “Blockchain Functions”, we go deeper to understand how blockchain functions, gain an understanding of smart contracts, blockchain security, types of blockchain and their transaction flow, and the consensus protocol. In the next chapter “Blockchain Governance”, we look at the how blockchain is governed and how it enables anonymity of users. Now, once we have the understanding of blockchain concepts and ecosystem, we look at the real world applications of blockchain like cryptocurrencies, decentralized finance (DeFI), and Non-Fungible Tokens (NFTs). Then we look at blockchain based currencies like Bitcoin and Ethereum in the context of blockchain, and how blockchain has enabled them to become an alternative to the centralized banking system. In the next chapter “Blockchain Platforms”, we look at key blockchain platforms like IBM, Hyperledger, and Corda. In the final chapter, we study the key use cases of blockchain, and conclude by discussing the future of blockchain technology. 

Contents

[Introduction](#part0000.xhtml#_Toc100814731)

[What is Blockchain?](#part0000.xhtml#_Toc100814732)

[Private / Permissioned Blockchains](#part0000.xhtml#_Toc100814733)

[Bitcoin is NOT Blockchain](#part0000.xhtml#_Toc100814734)

[Blockchain History](#part0000.xhtml#_Toc100814735)

[The Early Internet](#part0000.xhtml#_Toc100814736)

[Web 1.0 – Internet of Connection](#part0000.xhtml#_Toc100814737)

[Web 2.0 – Internet of Information](#part0000.xhtml#_Toc100814738)

[Web 3.0 – Internet of Value](#part0000.xhtml#_Toc100814739)

[Blockchain History](#part0000.xhtml#_Toc100814740)

[Blockchain Features](#part0000.xhtml#_Toc100814741)

[Blockchain Use Cases Synopsis](#part0000.xhtml#_Toc100814742)

[Blockchain Mechanics](#part0000.xhtml#_Toc100814743)

[Accounting Systems](#part0000.xhtml#_Toc100814744)

[Ledger](#part0000.xhtml#_Toc100814745)

[Cryptography](#part0000.xhtml#_Toc100814746)

[History of Cryptography](#part0000.xhtml#_Toc100814747)

[Cryptography Concepts](#part0000.xhtml#_Toc100814748)

[Types of Cryptography](#part0000.xhtml#_Toc100814749)

[Disintermediation Effect](#part0000.xhtml#_Toc100814750)

[Transparency](#part0000.xhtml#_Toc100814751)

[Immutability](#part0000.xhtml#_Toc100814752)

[Blockchain Functions](#part0000.xhtml#_Toc100814753)

[Smart Contracts](#part0000.xhtml#_Toc100814754)

[Blockchain Security](#part0000.xhtml#_Toc100814755)

[Types of Blockchains](#part0000.xhtml#_Toc100814756)

[Blockchain Transaction Flow](#part0000.xhtml#_Toc100814757)

[Blockchain Consensus](#part0000.xhtml#_Toc100814758)

[Blockchain Governance](#part0000.xhtml#_Toc100814759)

[Open Source](#part0000.xhtml#_Toc100814760)

[Governance](#part0000.xhtml#_Toc100814761)

[Identity of the Blockchain](#part0000.xhtml#_Toc100814762)

[Anonymity in Blockchain](#part0000.xhtml#_Toc100814763)

[Blockchain in Real World](#part0000.xhtml#_Toc100814764)

[How Blockchain solves real-world problems](#part0000.xhtml#_Toc100814765)

[Cryptocurrencies](#part0000.xhtml#_Toc100814766)

[Decentralized Finance (DeFI)](#part0000.xhtml#_Toc100814767)

[Non-Fungible Tokens (NFTs)](#part0000.xhtml#_Toc100814768)

[Blockchain based cryptocurrency – Bitcoin](#part0000.xhtml#_Toc100814769)

[Bitcoin History](#part0000.xhtml#_Toc100814770)

[Bitcoin Identity](#part0000.xhtml#_Toc100814771)

[Bitcoin Consensus](#part0000.xhtml#_Toc100814772)

[Bitcoin Transaction Process](#part0000.xhtml#_Toc100814773)

[Bitcoin Script](#part0000.xhtml#_Toc100814774)

[Bitcoin Network](#part0000.xhtml#_Toc100814775)

[Bitcoin Wallets](#part0000.xhtml#_Toc100814776)

[Bitcoin Mining](#part0000.xhtml#_Toc100814777)

[Bitcoin Governance](#part0000.xhtml#_Toc100814778)

[Blockchain based cryptocurrency – Ethereum](#part0000.xhtml#_Toc100814779)

[Smart Contracts](#part0000.xhtml#_Toc100814780)

[Ethereum Overview](#part0000.xhtml#_Toc100814781)

[Ethereum Design](#part0000.xhtml#_Toc100814782)

[Ethereum Virtual Machine (EVM)](#part0000.xhtml#_Toc100814783)

[Ethereum Applications and Use Cases](#part0000.xhtml#_Toc100814784)

[Ethereum Ecosystem](#part0000.xhtml#_Toc100814785)

[Blockchain Platforms](#part0000.xhtml#_Toc100814786)

[Blockchain Use Cases](#part0000.xhtml#_Toc100814787)

[Enterprise Solutions](#part0000.xhtml#_Toc100814788)

[Public Sector Solutions](#part0000.xhtml#_Toc100814789)

[Platform Developer Solutions](#part0000.xhtml#_Toc100814790)

[End User Solutions](#part0000.xhtml#_Toc100814791)

[The Future of Blockchain](#part0000.xhtml#_Toc100814792)

[References](#part0000.xhtml#_Toc100814793)

# Introduction

## What is Blockchain?

Blockchain is a peer-to-peer ledger system that allows peers to transact directly with each other without the need of a central authority. The blockchain records information of these transactions in a decentralized way that makes it improbable to alter.

In order to understand Blockchain, first, let us understand what are blocks? Blocks are digital ledgers which hold batches of valid transactions. Each block contains a cryptographic hash of the previous block, a timestamp, and transaction data (generally represented as a Merkle tree). The timestamp proves that the transaction data existed when the block was published to get into its hash. To assure the integrity of a block and the data contained in it, the block is usually digitally signed.

The cryptographic hash of the prior block links the two blocks. As blocks contain information about the block before it, these linked blocks form a chain, with each additional block reinforcing the ones before it. This iterative process confirms the integrity of the previous block, all the way back to the initial block, which is known as the genesis block. Therefore, blockchains are resistant to modification of their data because once recorded, the data in any given block cannot be altered retroactively without altering all subsequent blocks.

In other words, Blockchain is a computerized database and uses strong cryptography to store the ownership records of cryptocurrencies, secure transaction records, and verify the transfer of currency ownership. The blockchain consists of blocks, that are linked together using cryptography. Each block contains a cryptographic hash of the previous block, a timestamp, and transaction data. Blockchain technology is poised to impact much of the world today, be it financial services, emerging technologies, energy, or digital identity, just to name a few. 

Blockchains are typically managed by a peer-to-peer network for use as a publicly distributed ledger, where nodes collectively adhere to a protocol to communicate and validate new blocks. Although blockchain records are not unalterable as forks are possible, blockchains may be considered secure by design and exemplify a distributed computing system with high Byzantine fault tolerance.

## Private / Permissioned Blockchains

Private blockchains are often referred to as 'permissioned' blockchains. Unlike public blockchains, where anyone can download the software, form a node, view the ledger and interact with the blockchain, private blockchains are often run and operated by an entity ("trusted intermediary"). As the trusted intermediary is in charge of running of the blockchain, it will control who can access the private blockchain and can also control the type of access rights each participant has. For example, some participants may be restricted to viewing (some or all of) the data on the ledger, whereas others may also have permission to submit new transactions for recording on the blockchain.  
Private blockchains have been proposed for business use. Computerworld called the marketing of such privatized blockchains without a proper security model "snake oil"; however, others have argued that permissioned blockchains, if carefully designed, may be more decentralized and therefore more secure in practice than permissionless ones.

The most common examples of private blockchains are Ripple (XRP) and Hyperledger.

## Bitcoin is NOT Blockchain

A lot of people believe that Bitcoin and Blockchain are one and the same. They are not!

Bitcoin is a cryptocurrency which utilizes blockchain technology. It is one of the most important use case of blockchain. It is a digital currency running on the top of Bitcoin blockchain, which is an open, public blockchain network. If a user has an internet connection and a bitcoin wallet application, he can receive and send bitcoin over the bitcoin blockchain network.

 

 

 

 

 

 

 

 

 

 

 

# Blockchain History

## The Early Internet

The Internet started in the 1960s as a way for government researchers to share information. The computers in that era were large and immobile and in order to make use of information stored in any one computer, one had to either travel to the site of the computer or have magnetic computer tapes sent through the conventional postal system.

Another catalyst in the formation of the Internet was the heating up of the Cold War between the US and Soviets. The Soviet Union's launch of the Sputnik satellite spurred the U.S. Defense Department to consider ways information could still be disseminated even after a nuclear attack. This led to the formation of the ARPANET (Advanced Research Projects Agency Network), the network that ultimately evolved into what we now know as the Internet. ARPANET was a great success but membership was limited to certain academic and research organizations who had contracts with the Defense Department. In response to this, other networks were created to provide information sharing.

ARPANET started a DARPA (Defense Advanced Research Project Agency) experiment in decentralized computing communications between two university labs in California in 1970. On 1st January 1983, this communications protocol became Transfer Control Protocol/Internetwork Protocol (TCP/IP), the standard in networking protocol or computer communications protocol, which is the backbone of today’s internet. Prior to this, the various computer networks did not have a standard way to communicate with each other. TCP/IP allowed different kinds of computers on different networks to "talk" to each other. ARPANET and the Defense Data Network officially changed to the TCP/IP standard on 1st January 1983, leading to the birth of the Internet. 

With the TCP/IP protocol in place, users had the ability to link hypertext documents in an information system accessible from any node or computer using this protocol. All networks could now be connected by a universal language. The resulting information system became today’s World Wide Web (www). With the birth of World Wide Web, expanded usages of this new technology arose with expanded business opportunities. Web servers, people which host and store the documents and web browsers, companies set up to help you view linked documents, help create a household need for this new technology, leading to the rise of the internet revolution.

The internet can be grouped into three distinct segments characterized by the way people interact with it.

*   Web 1.0 – Internet of Connection
*   Web 2.0 – Internet of Information
*   Web 3.0 – Internet of Value

## Web 1.0 – Internet of Connection

Web 1.0 refers to the first stage of the World Wide Web evolution. It was a content delivery network (CDN) that enabled the showcase of the piece of information on the websites. There were only a few content creators in Web 1.0 with a huge majority of users who were the consumers of content. Personal web pages were common, consisting mainly of static pages hosted on ISP-run web servers, or on free web hosting services. 

The web pages were static and built using Server Side Includes or Common Gateway Interface (CGI). Frames and Tables were used to position and align the elements on a page. The content was served from the server’s file system. It costed the user as per pages viewed and had directories that enabled users to retrieve a particular piece of information.

The essential characteristics of Web 1.0 were:

*   Development of a host of web-based applications, which fostered in online services, such as email
*   Content from the administrator
*   Managed by a central authority
*   Read-only information, that was ‘pushed’ to the users

![Figure A: A typical Web 1.0 Architecture B. Web 2.0 | Download Scientific Diagram](Images/image00230.jpeg)

Web 1.0 architecture; Source: researchgate.net

 

Email was the first widely adopted application on Web 1.0. Computers and their connectivity started becoming necessities. Technology advancement in computer technology brought on changes, floppy disks became hard disks, storage capacities increased from MB to GB to TB. Internet speed increased from kilobits per second (Kbps) to megabytes per second (Mbps) to gigabytes per second (Gbps), and RAM grew from KBs to GBs. 

Web 1.0 concluded with the development of the dotcom bubble. Startups appeared to cash in on this new technology, most notable being Netscape which developed the first commercial web browser.

## Web 2.0 – Internet of Information

Web 2.0 is an enhanced version of Web 1.0. It refers to worldwide websites that highlight user-generated content, usability, and interoperability for end users. Web 2.0 is also called the participative social web. It does not refer to a modification to any technical specification, but to modify the way Web pages are designed and used. 

Web 2.0 had dynamic content that is responsive to user input, in comparison to Web 1.0 which was static. It enabled free sorting of information, permitting users to retrieve and classify the information collectively. 

Web 2.0 enabled information flows between the site owner and site users by means of evaluation and online commenting. Interaction and collaboration between participants was allowed in a social media dialogue as the creator of user-generated content in a virtual community. Web 2.0 applications tend to interact much more with the end user. As such, the end user is not only a user of the application but also a participant by these 8 tools mentioned below:

*   Podcasting
*   Blogging
*   Tagging
*   Curating with RSS
*   Social bookmarking
*   Social networking
*   Social media
*   Web content voting

The essential characteristics of Web 2.0 were:

*   User-generated content
*   Read-write capability, enabling users to interact with information
*   Information became siloed
*   Data became a commodity

 

![](Images/image00231.gif)

Web 2.0 architecture; Source: researchgate.net

 

Web 2.0 saw emerging marketplaces that brought together unrelated buyers and sellers in a seamless low-cost environment. Data became a commodity collected, siloed and sold, and consumers started giving up their information at a frenzied pace. Websites allowed users to generate content, and social media became part of their lives. The social media contained a number of online tools and platforms where people shared their perspectives, opinions, thoughts and experiences. 

## Web 3.0 – Internet of Value

Web 3.0 is a term that is used to describe many evolutions of web usage and interaction among several paths. It refers to the evolution of web utilization and interaction which includes altering web into a database. It enables the upgradation of the back-end of the web, after a long time of focus on the front-end. In Web 3.0, data isn’t owned but instead shared, where services show different views for the same web / the same data. 

The Semantic Web (3.0) promises to establish “the world’s information” in a more reasonable way than Google can ever attain with their existing engine schema. This is particularly true from the perspective of machine conception as opposed to human understanding. 

The essential characteristics of Web 3.0 were:

*   Semantic Web – The semantic web improves web technologies in demand to create, share and connect content through search and analysis based on the capability to comprehend the meaning of words, rather than on keywords or numbers.
*   Artificial Intelligence – Combining this capability with natural language processing, in Web 3.0, computers can distinguish information like humans in order to provide faster and more relevant results. They become more intelligent to fulfill the requirements of users.
*   3D Graphics – The three-dimensional design is being used widely in websites and services in Web 3.0. Museum guides, computer games, e-commerce, geospatial contexts, etc. are all examples that use 3D graphics.
*   Connectivity – With Web 3.0, information is more connected via semantic metadata. As a result, the user experience evolves to another level of connectivity that leverages all the available information.
*   Ubiquity – Content is accessible by multiple applications, every device is connected to the web, the services can be used everywhere. 
*   Data Independence – Identity and information is held by the user, breaking data silos.

As a result, Web 3.0 is more connected, open, and intelligent. It enables community interaction and usage of distributed ledgers or blockchain technology, smart contracts, machine learning, and artificial intelligence.

Bitcoin has been the first widely accepted application of Web 3.0, just as email was the first big application of Web 1.0. Web 3.0 represents a world where value is exchanged at the speed in which information moves today. The new Web 3.0 browsers are being built to help users manage their cryptocurrencies, keys, passwords and other blockchain features.

![How Web 3.0 will impact higher education | Digital Communications team blog](Images/image00232.jpeg)

Evolution of the web

Key differences between Web 1.0, Web 2.0, and Web 3.0

 
| Web 1.0 || Web 2.0 || Web 3.0 |
| --- | --- | --- |
| Read only || Read-write || Read-write-execute |
| Company focus || Community focus || Individual focus |
| Client server || Peer-to-Peer || Portable personal web |
| Owning content || Sharing content || Consolidating content |
| Web pages || Web applications || Smart applications |
| Home pages || Blogs || Live-streams |
| Britannia online (static) || Wikipedia (can be updated by users) || Semantic web |
| Directories || Tagging || User behavior |
| Banner advertising || Interactive advertising || Behavioral advertising |
| Page views || Cost per click || User engagement |
| HTML, Portals || XML, RSS || RDF |

 

## Blockchain History

Cryptographer David Chaum first proposed a blockchain-like protocol in his 1982 dissertation "Computer Systems Established, Maintained, and Trusted by Mutually Suspicious Groups." Further work on a cryptographically secured chain of blocks was described in 1991 by Stuart Haber and W. Scott Stornetta, to implement a system wherein document timestamps could not be tampered with. In 1992, they incorporated Merkle trees to the design, which improved its efficiency by allowing several document certificates to be collected into one block. The first and the longest blockchain dates to 1995, when their company Surety added hashes to the documents that have been published in The New York Times every week since 1995.

However, it took another 13 years for the first decentralized blockchain to be conceptualized by a person (or group of people) known as Satoshi Nakamoto in 2008, to serve as the public transaction ledger of the cryptocurrency Bitcoin. The identity of Satoshi Nakamoto remains unknown to date. Nakamoto improved the design in an important way using a ‘hash-cash’ like method to timestamp blocks without requiring them to be signed by a trusted party and introducing a difficulty parameter to stabilize the rate at which blocks are added to the chain. The design was implemented the following year by Nakamoto as a core component of cryptocurrency bitcoin, where it serves as the public ledger for all transactions on the network. The implementation of the blockchain within bitcoin made it the first digital currency to solve the double-spending problem without the need of a trusted authority or central server. 

The bitcoin blockchain records bitcoin transactions and stores their history in an append-only ledger format, such that data can be added to the ledger, but cannot be deleted. It is implemented as a chain of blocks, each block containing a hash of the previous block up to the genesis block2 in the chain. The bitcoin design has inspired other applications and blockchains that are readable by the public and are widely used by cryptocurrencies. 

In August 2014, the bitcoin blockchain file size, containing records of all transactions that have occurred on the network, reached 20 GB, and from January 2016 to January 2017, the bitcoin blockchain grew from 50 GB to 100 GB in size. The ledger size had exceeded 200 GB by early 2020.

According to Accenture, an application of the diffusion of innovations theory suggests that blockchains attained a 13.5% adoption rate within financial services in 2016, therefore reaching the early adopters phase. Industry trade groups joined to create the Global Blockchain Forum in 2016, an initiative of the Chamber of Digital Commerce.

In May 2018, Gartner found that only 1% of CIOs indicated any kind of blockchain adoption within their organizations, and only 8% of CIOs were in the short-term "planning active experimentation with blockchain". In 2019, Gartner reported 5% of CIOs believed blockchain technology was a 'game-changer' for their business.

Blockchain Basics

Hearing the world ‘Blockchain’ now is comparable to hearing the word ‘Internet’ in the early 90s. It seemed elusive, like something that would not impact your daily life. But here we are, more than 25 years later, and internet has transformed businesses, commerce, communications, media and even how people connect with each other. We all carry internet in our pockets. We can transfer money, check weather, get directions, and even order food at the touch of a button.

The next technology to have that kind of impact isn’t big data, artificial intelligence, or social media.

It’s Blockchain!

Blockchain has the power to revolutionize how the businesses and people connect. It will enable every kind of asset, from tickets – money - media, to be stored, moved, exchanged, and transacted without an intermediary. These assets will no longer be required to store in a central place, but distributed across a global ledger, using the highest level of cryptography. When a transactions happens, it would broadcast across thousands of computers around the globe and recorded as blocks. There would no longer be a single point of failure, and this is what makes blockchain infinitely more secure than what we have today.

Blockchain isn’t just for assets. It extends to contracts as well. These are called Smart Contracts. A smart contract self-executed and handles enforcement, management, and performance of agreements between people, like insurance policies, loans, wills, records, and copyright content.

There are so many possible use cases of blockchain; not just now, but in future as well – scenarios we have not yet envisaged. 

What is Blockchain?

When you hear about blockchain, you probably think of new, high-emerging technology. In reality, blockchain is a combination of technologies that have existed for a long time. These technologies are combined in a new and creative way to give us an amazing new platform to build solutions.

Blockchain is often referred to as digital centralized ledgers. 

In order to understand blockchain, imagine it as a simple numbered notebook. The blocks would be pages of data in that notebook. 

We fill up this page with data, which is analogous to recording financial transactions or ledger on the block. Like we can write anything on the paper, we can record anything on the blockchain, like education degrees, certificates, contracts and agreements, voting records, land titles, medical records, or even notes of a song. Like all the pages on the notebook are numbered, so is the case of blockchain wherein all the records are linked. If I tear any page of the notebook, it is very obvious and easy to determine. Similarly, if I change data on any block, the links will break in a very obvious way. This key property of blockchain gives it an enhanced security and is known as ‘immutability’. 

Blockchain also gives us an incredible technology called smart contracts, which allow us to programmatically define the rules and steps to be performed whenever a certain type of event is recorded in the blockchain.

## Blockchain Features

There are seven key features of blockchain that has made this technology so revolutionary and popular.

Distributed Ledgers

A ledger is a collection of transactions. A ledger will provide every information about a transaction and the participant. It’s all out in the open, nowhere to hide. It is because with a digitally distributed ledger, no one owns the ledger. It is distributed among participants in the network, all running the same blockchain protocols. This distributes the computational power across the computers to ensure a better outcome.

This is the reason it’s considered one of the blockchain essential features. The result will always be a higher efficient ledger system that can take on the traditional ones.

Why it is one of the key Blockchain feature?

*   No Malicious Changes – Distributed ledger responds well to any suspicious activity or tamper. As no one can change the ledger and everything updates real fast, tracking what’s happening in the ledger is quite easy with all these nodes.
*   Ownership of Verification – The nodes act as verifiers of the ledger. If a user wants to add a new block, other participants will have to verify the transaction and then give the green signal.
*   No Special Favors – Everyone in the network must go through the usual channels to add their blocks. It’s not like someone has more power, so they will get more or special privileges.
*   Consensus – To make the blockchain features work, every active node must maintain the ledger and participate for validation.
*   Fast System Response – Removing the intermediates quickens the system response. Any change in the ledger is updated in minutes or even seconds. Traditional banking systems are quite slow. Sometimes it can take days to process a transaction after finalizing all settlements. It also can be corrupted quite easily. Blockchain offers a faster settlement compared to traditional banking systems. This way a user can transfer money relatively faster, which saves a lot of time in the long run.

Decentralized Technology

The blockchain network is decentralized; it does not have any governing authority, rather a group of nodes maintains the network. The ledger is stored, updated, and maintained by this per network.  Nodes form the infrastructure of this network. They store, distribute, and preserve the data. 

All the nodes on the network follow the same protocols, however they have different roles. A full node contains a copy and transaction history of the blockchain protocol, and aids in the maintenance of the blockchain. A lightweight node or Simple Payment Verification (SPV) node does not store the copy of the blockchain, and rely on full nodes to provide them with the necessary information while communicating with the blockchain. As they don’t store a copy of the chain, they only query the current status for which block is last, and broadcast transactions for processing.

As the system does not require any governing authority, the users can directly access the blockchain network from the web and store their assets, like cryptocurrencies, documents, contracts or other valuable digital assets. And with the help of blockchain, they have direct control over them using their private key. Hence, this decentralized structure is giving the users power and rights back on their assets.

Why it is one of the key Blockchain feature?

*   Less Failure – Everything in the blockchain is fully organized, and as it does not depend on human calculations. It’s highly fault-tolerant. So, accidental failures of this system are not a usual output.
*   User Control – With decentralization, users now have control over their data. They don’t have to rely on any 3rd party to maintain their data. 
*   Less Prone to Breakdown – As decentralized is one of the key features of blockchain technology, it can survive any malicious attack. This is because attacking the system is more expensive for hackers and not an easy solution. So, it’s less likely to breakdown.
*   No 3rd Party – Decentralized nature of the technology makes it a system that doesn’t rely on 3rd parties

Transparency

Blockchain makes data transparent in a way that has not existed in financial systems, which is why many argue that blockchain could be used as the new standard for transparency. How exactly is data made transparent on the blockchain? Network participants can access transactions of public addresses using a block explorer, and search the blocks of a blockchain, their contents, and their relevant details.

The users can see all the transactions that have occurred on the distributed ledger. A blockchain stores details of every transaction that occurred since the first transaction. This first transaction is a part of the first block of the blockchain and is known as ‘Genesis Block’. Since every node shares a copy of the agreed-upon ledger, every user has the same copy. In comparison, the centralized systems are not transparent, as the information of the ledger is controlled by one authority.

In the case of cybersecurity this means decentralized threat data can be made accessible. While some may argue that in-depth analyses and reports provide sufficient confidence that the security solutions are performing as they’re supposed to, bias may come into play since these companies are paying for the analysis reports, certifications, and other acknowledgements in the first place. With blockchain, any bias can be eliminated, thanks to this transparency.

Why it is one of the key Blockchain feature?

*   Zero Scams – As the system runs on algorithms, there is minimal chance for people to scam the users and utilize blockchain for their personal gains.
*   Minimize cyber attacks \- Transparency is just one of the many ways in which blockchain can benefit security vendors, regular end users, or even governments in the cybersecurity community. It’s not every day that we are presented with a technology that can guarantee the legitimacy of attacks and be made public at the same time.
*   Authenticity – Blockchain creates a transparent profile of every user. Every change on the blockchain is viewable and makes it more concrete. This nature of the system makes it a unique kind of system for every kind of person. And hackers will have a hard time cracking it.

Consensus

Blockchain ledgers are different from centralized ledgers because network participants have an agreement of the ledger. In order for the new blocks to be added, all the nodes need to agree that the transactions are accurate. As there is no central authority to validate the nodes, a new way to reach agreement or come to a ‘consensus’ is required.

This is enabled by the ‘consensus mechanism’. The architecture is cleverly designed, and consensus algorithms are at the core of this architecture. Every blockchain has a consensus to help the network make decisions. The ways in which each blockchain comes to a consensus is built into the protocol, and the rules built into the architecture that determine how the nodes will add ledger transactions. 

There are lots of different consensus algorithms for blockchains over the globe. Each has its own unique way to make decisions and perfecting previously introduces mistakes. The architecture creates a realm of fairness on the web. The bitcoin network uses a Proof-of-Work (PoW) consensus mechanism. PoW refers to the cryptographic mechanism that relies on participants being able to solve hard computational problems to have a higher stake in the network. PoW essentially is a distributed way for participants to determine the most valid block. Each participant attempts to find a hash value, which is a valid solution for the upcoming block of transactions. The winner who finds the hash value that meets the requirement, adds the proposal block to the chain, and obtains the reward.

Why it is one of the key Blockchain feature?

*   Decision-making Process – In simple terms, the consensus is a decision-making process for the group of nodes active on the network. Blockchain enables the nodes to an agreement quickly. When millions of nodes are validating a transaction, a consensus is necessary for a system to run smoothly. You could think of it as kind of a voting system, where the majority wins, and the minority has to support it.
*   Trustless – The consensus is responsible for the network being trustless. Nodes might not trust each other, but they can trust the algorithms that run at the core of it. That’s why every decision on the network is a winning scenario for the blockchain. It’s one of the key benefits of blockchain features.

Cryptography and Encryption

How does blockchain offers higher level of security compared to existing technologies? It is because of ‘Cryptography’. 

Cryptography is a complex mathematical algorithm that acts as a firewall for attacks. Every information on the blockchain is hashed cryptographically. In simple terms, the information on the network hides the true nature of the data. For this process, any input data gets through a mathematical algorithm that produces a cryptographic ‘hash’ which is a different value, but whose length is always fixed. 

Added with decentralization, encryption adds another layer of protection for users. The users have a private key to access the data and a public key to make transactions.

Why it is one of the key Blockchain feature?

*   Tamperproof – All the blocks in the ledger have a unique hash and contain the hash of the previous block. If someone tampers with the data in the block, that will change all the hashes of the linked blocks. IDs. And that’s what makes the data tamperproof.
*   Authenticity – Encryption and cryptography are combined with the blockchain technology to assure the information is authentic. Instead of relying on the 3rd party, trust is put into cryptographic algorithms that proves the provenance and authenticity of an attestation.
*   Irreversible – Hashing is quite complex, and it’s impossible to alter or reverse it. No one can take a public key and come up with a private key. Also, a single change in the input could lead to a completely different ID, so small changes aren’t a luxury in the system. If someone wants to corrupt the network, he/she would have to alter every data stored on every node in the network. There could be millions and millions of people, where everyone has the same copy of the ledger. Accessing and hacking millions of computers is next to impossible and costly. That’s why it’s one of the best blockchain features. As it’s too hard to bypass, you won’t have to worry about hackers taking all your digital assets from you.

Immutability

There are some exciting blockchain features but among them “Immutability” is undoubtedly one of the key features of blockchain technology. But why is this technology uncorrupted? Let’s start with a connecting blockchain with immutability.

Immutability means something that can’t be changed or altered. This is one of the top blockchain features that help to ensure that the technology will remain as it is – a permanent, unalterable network. But how does it maintain that way?

Blockchain technology works slightly different than the typical banking system. Instead of relying on centralized authorities, it ensures the blockchain features through a collection of nodes. Every node on the system has a copy of the digital ledger. To add a transaction every node needs to check its validity. If the majority thinks it’s valid, then it’s added to the ledger. This promotes transparency and makes it immutable. So, without the consent from the majority of nodes, no one can add any transaction blocks to the ledger.

Another fact, that backs up the list of key blockchain features is that, once the transaction blocks get added on the ledger, no one can just go back and change it. Thus, any user on the network won’t be able to edit, delete or update it.

Why it is one of the key Blockchain feature?

*   Trustless environment – Every year there’s a massive amount of money that gets hacked through regular channels. In many cases, there’s always an internal link for these hacks to know about all the security measures, so in the end, we pay the price for our trust. As you all know banks aren’t that trustable now and the global economy needs a trustless environment to fully overcome this issue.
*   Corruption-proof –If businesses start to integrate blockchain technology to maintain their internal networking system, no one would be able to hack into it or alter or even steal information. Public blockchains are a perfect example of this. Everyone in the public blockchain can see the transactions, so it is super transparent. On the other hand, private or federated blockchain could be best for enterprises that want to remain transparent among staff and protect their sensitive information along the way from public view.

Programmable

Some blockchains offer an additional feature, ‘smart contract’, that impose logic into the system. 

If you think of bitcoin blockchain as a calculator recording financial transactions, you can think of blockchains enabling smart contracts as computers. The first of these blockchains is ‘Ethereum’, which runs Ethereum Virtual Machine (EVM), which has the ability to impose digital agreements or ‘smart contracts’.

 A smart contract is a program that runs on the blockchain network, and can impose contractual agreements. Typically they work as digital agreements that enforce a specific set of rules, which are defined by computer code. This code is replicated and executed by all blockchain networks.

Why it is one of the key Blockchain feature?

*   Trustless protocols – Blockchain smart contracts allow for creation of trustless protocols. This means that the two parties can make commitments via blockchain, without having to know or trust each other. They can be sure that if the conditions are not fulfilled, the contract will not be executed. 
*   Remove 3rd party – The use of smart contracts can remove the need of intermediaries or 3rd parties, which would reduce operational costs significantly
*   Faster settlements – Smart contracts can allow making faster settlements for any kind of contract, with the 3rd party out of the way. This is one of the best benefits of blockchain features to this day. This way blockchain will impact the international trades too!

## Blockchain Use Cases Synopsis

There are numerous blockchain use cases that are currently being explored. For example, managing education certificates or personal health information, where these records could be accessible with your permission to anyone else. Let’s assume you are a US resident and travelling to India for a vacation. Suppose you fall ill and end up in a hospital there, wouldn’t it be great if the doctor treating you had full insight into your medical history, knows the allergy you have, or any medications you are on. This is a very big area and ties blockchain with identity management. 

Similarly, blockchain for voting is a big area to explore, to ensure integrity of elections and demonstrate that the results haven’t been tempered with. 

Another area of interest is blockchain for media and arts, wherein the content creators can use blockchain technology to distribute their work to public without the use of 3rd party or an intermediary, via multiple scenarios like non fungible tokens (NFT).

We are also seeing a lot of interest in blockchain for fractional asset ownership scenarios, wherein we can leverage blockchain tokens and NFTs to fractionalize the asset ownership.

And then, we have the traditional use cases, like blockchain for banking to ensure transparency and accuracy of transactions and avoid frauds; and blockchain for supply chain to track the supply, and origin of goods and services. Walmart is pioneering the use of blockchain technology in the supply chain field, by using blockchain to identify the origin of meat that is sold in the stores, in order to accelerate recalls in case of any issue, along with reducing the waste with insights to the supply chain.

On the public sector, there is a lot of interest in the blockchain technology for law enforcement purposes; how do we enable different government agencies to share data seamlessly, in a safe and secure environment, along with protecting users privacy and anonymity.

Blockchain Users

*   Business to Consumers (B2C) – A B2C business is conducted directly between a company and its consumers who are the end-users of its products or services. Benefits of blockchain for B2C segment is transparency to consumers, accountability from suppliers, sourcing validation, labor verification, and immutable contracts.

A real-world use case is of a firm called TrustChain, which uses blockchain to track and authenticate diamonds, and other precious metals across all stages of supply chain from mining to the end consumer. As a result, the jewelry industry can now track and authenticate diamonds and other precious metals through all stages of the supply chain. Blockchain would enable physical product verification, process verification, and would serve as a governance oversight.

*   Business to Business (B2B) – With a decentralized approach, blockchain removes the intermediary such as banks in business to business transactions, to facilitate faster and less expensive payments. The shared ledger approach also eliminates the need for multiple paper copies that need to be verified and updated constantly.

A real-world use case is of DLT Labs and Walmart Canada, who have initiated a tracking program to tackle dispute resolution in disparate invoicing system for freights. The blockchain solution connects all points on the supply chain with a shared trusted ledger. The carriers are a vital link in the Walmart’s supply chain and the DLT blockchain solution ensures that the invoicing system runs smoothly. As a result, dispute among the parties involved in freight management and Walmart has reduced by 95%.

*   Government to Consumers (G2C) – The public sector is the part of the economy composed of both the public and private sector companies operating on behalf of the public. Public sector includes all the government, military, police, public health, public education, infrastructure, housing, financial services, and other industries. The current systems are inherently insecure and costly, with in-efficient workflows. Blockchain technology would enable more secure, agile, and cost optimum platforms for public use.

A real-world example is of Smart Dubai 2021, wherein Dubai aims to move all government operations and record keeping into blockchain. The goal is to increase transparency and efficiency in the government operations. Blockchain is also becoming the enabling layer for a lot of other Smart Dubai initiatives, thereby creating a Smart City. For example, projects like automated traffic signals, registration of citizens for visas and public healthcare, etc. are all being pioneered on blockchain.

 

 

 

 

 

 

 

# Blockchain Mechanics

In this chapter, we will discuss the distributed ledger technology, its basic components and how it differs from the previous ledger storage technologies. We will gain an insight of how data sharing, storage, and cryptography are wrapped into the blockchain foundations, and how the hashing function and the Merkle tree data structure helps to immutably store data with transparency, without revealing all the details.

We will also get an insight into how the blockchain technology is fundamental in public-key cryptography where key pairs support privacy and authenticity by only exposing the public key, and keeping the private key secure. We will examine how this agreed-upon, append-upon distributed ledger technology guarantees transparency and immutability.

## Accounting Systems

The history of blockchain is tightly coupled with the history of accounting. 

Bookkeeping or accounting has its roots in ancient civilizations, some as old as 5000 years ago, wherein we have evidence of the single-entry accounting system, which was the world’s first methodology to prove the ownership of an asset. The ledger was associated with the owner. The single-entry accounting system mandated a centralized authority to control and govern the ledger. Single-Entry Accounting, on the one hand, was a simple, easy to maintain the system as it was a one-sided accounting system but on the other, it was impossible to authenticate or examine its accountability. Thus, with time, people realized that the procedure of accounting needed more transparency and accountability and should be able to answer questions like:

*   Who paid what?
*   Who owes how much?
*   Which debts are unpaid?
*   Why is money missing?

Further, for international transactions two central authorities were required. For example, if US has to do trade with UK, there would be an owner of the ledger in the US as well as in UK, calling for a central authority in both the countries. 

The drawbacks of the single-entry accounting became the trigger point to look for a more comprehensive structure and thus, came into being the Double-entry accounting. This new form was developed almost 600 years ago with the purpose of making the accounting system more comprehensive and hence, instead of maintaining one ledger, the accountant keeps two ledgers – one for incoming transactions and the other for outgoing transactions. Although the double-entry accounting method of bookkeeping was much more advanced and efficient than single-entry accounting, still there were several flaws in this too. As there was no connection between the different sets of accounting books, the records were separate and therefore, lacked in transparency and were difficult to verify. This led to a great trust deficit between the various stakeholders, like investors, lenders and/or the state.

The imperfections of the double-entry accounting led to the need of an economy-wide accounting system, one that would help in doing away with huge amounts of administration and pave the way for a foolproof and dependable accounting system.

And so, Triple-entry accounting came in, which is a step ahead of the traditional double-entry accounting; one that will relieve the bookkeepers and companies from tedious troubleshooting and help remove the mistrust, frauds or manipulations faced by them. Triple-entry accounting presents a framework for a new and complex way to do accounting. This concept was conceived by the late Yuji Ijiri, a professor at Carnegie Mellon University, and popularized by Ian Grigg who associated it with blockchain technology, and believed that accounting should no longer be completely private.

Blockchain is the very first implementation of triple-entry accounting system, where we have an asset being recorded on the ledger in the context of a transaction. In simple terms, blockchain refers to a digital ledger that is distributed among multiple locations in order to ensure security and ease of access globally. 

The term ‘Triple-entry accounting’ is somewhat misleading as there isn’t any 3rd entry; instead, a 3rd component is added to the debit and credit system. The common thread or the binding component is Blockchain that links the books together and helps in linking two separate double entries and can potentially be viewed for external auditing purposes. So, instead of individual firms having their own books for the transaction, they go through a contract which evidently includes every aspect of a transaction; what the product was, who is the seller, who is the buyer, etc. and above all, it’s digitally signed.

In the triple-entry accounting system, all accounting entries are cryptographically sealed by a 3rd entry and thus, it works as a deterrent towards manipulations and financial fraud. In traditional double-entry accounting a company’s ledger can be compromised by any of the weak human links – may be an employee / bookkeeper / auditor. But this unique system of triple-entry accounting leaves no space for any corrupt, weak human link and the cryptographic account of the transaction is stored permanently and immutably on the ledger.

As blockchains are completely automated and decentralized, once an entry is recorded, it cannot be edited, altered or removed. The highest level of encryption technology ensures the accuracy of each transaction, digitally signed, leaving no gaps for errors and at the same time verifiable by all. The transactions recorded on the blockchain using triple entry simplifies the entire double-entry accounting process as once a transaction is recorded on the blockchain by one of the two accountants, the other party can also view the particular double entry, easily review it, and have it recorded automatically in its own books.

Thus, the triple-entry accounting is set to potentially revolutionize the future of bookkeeping as Blockchain accounting will literally halve the double-entry transactions recorded. This will assist the bookkeepers greatly by saving their time and providing them the opportunity to focus more on value-added roles within the profession.

## Ledger

Ledger is one of the core components of the blockchain technology. A ledger is a collection of transactions, and records the transactions.

In blockchain the ledger is distributed and decentralized. There is a copy of the ledger that exists on every node of the blockchain network. Hence, every participant of the network owns the ledger. In simple terms, a blockchain ledger is a distributed immutable record of collection of transactions.

Bitcoin was the first popular asset to be recorded as a transaction on a blockchain ledger, and it remains the most popular. The modern cryptocurrencies like Ethereum not only record the transaction on the blockchain, they also allow the users to have a permanent and immutable collection of code, also know as a ‘Smart Contract’ that runs on their blockchain. So, the ledgers store the transactions on the blockchain, as well as hold the code – ‘Smart Contracts’.

A blockchain is a peer-to-peer network. Think of a public blockchain as the internet, complete with its own set of protocols; and a private blockchain as intranet. On each of these networks there are nodes, which are put together by a collection of protocols. Each blockchain has its own set of protocols that defines not only the nodes, but how they communicate with each other. These networks store the ledger, provide the updates, and effectively manage the ledger.

On a public blockchain, anyone is allowed to join the network. On a private blockchain, we can control who can join the network. In a blockchain network, every user needs to have a unique identity. It is achieved by the use of PKI to provide a ‘Public Key’, which represents the identity of the user. Each user also have a ‘Private Key’ by which they can prove their identity. This private key is stored in a wallet – collection of user credentials. 

In order to gain an insight into the blockchain ledger, let’s start with the history of the ledger.

*   Single Entry Ledger – Ledger first appeared around 3000 BC. Chanakya, an Indian economist created the first documented single-entry ledgers. They had only a single entry. 
*   Double Entry Ledger – Double entry ledgers first appeared in the 14th century. They tracked debits and credits, and told story of financial transactions from buyer’s as well as supplier’s point of view. Luca Pacioli, known as the father of accounting, was the first person to publish work on double-entry ledger, and introduce it in Italy.
*   Triple Entry Ledger – Triple entry ledger is an enhancement to the traditional double entry system, in which all the accounting entries involving two parties are cryptographically sealed by a third entity. It records all debits, credits as well as an immutable link to all past debits and credits. Triple-entry ledger first appeared in the Bitcoin whitepaper written by Satoshi Nakamoto in 2008. The key features of triple-entry ledger include tamper-proof records, distributed ledger, double-entry + cryptography, validated records, secure and private, and digitally signed receipts.

![Triple entry accounting : One of the greatest inventions in the last few centuries in the world of accounting | by Spathion | Medium](Images/image00233.jpeg)

Triple entry ledger; Source: medium.com

Distributed Ledgers

The concept of distributed ledgers has been around for hundreds of years. To understand the basics of blockchain, it’s important to understand how distributed ledgers work.

A distributed ledger is a collection of data with no central administrator that has been agreed upon by consensus.

To understand more details, let’s take a trip back to 1500 years, to the island of Yap. The people of Yap use a very unique form of currency – Rai stone. Each stone weighs around 200 kg, making them difficult to move. To exchange them as money for goods or services, the divide the stones into sections, and then, they would announce to everyone on the island who owned what part of the stone. Everyone on Yap island needs to keep the mental ledger of the ownership. 

Every time any person on Yap island conducted a transaction, an announcement is made to everyone on the island. Each member would then update their mental ledger. In today’s description, this would be distributed ledger. All Rai stone ownership is known to everyone on the island, and this knowledge is updated whenever a transaction is made.

So why doesn’t just one member keep the accounting of Rai stone? What if this accountant got sick, or is unable to do accounting, or is dishonest? If the only copy of the ledger is altered by any means, the wealth would be lost or gained unfairly. This distributed ledger system safeguards Rai stone from any tampering. Even if one member moves away, everyone still ha multiple copies of the ledger, making the ledger fault tolerant and difficult to alter or get lost. 

One day a stone fell into the ocean and the Yap people decided that the stone don’t need to be on Yap island to hold value, and could still be traded. This system of consensus by the majority of the adults on the island with no central administrator is one of the first examples of distributed ledger.

Let’s review this with an example – Let’s assume Alice agrees to trade Bob her stone in the ocean in exchange for all of his cattle. Alice and Bob announce their transaction to everyone on Yap island. Everyone updates their mental ledger, and come to a consensus that the stone in the ocean is owned by Bib from that point onwards. Now suppose Alice tries to corrupt Carol, such that Carol’s ledger shows that Alice never gave up ownership of the stone. However, Carol will be outvoted by the remaining people on Yap island, and her version of the ledger will not be accepted. Hence if Alice wants to cheat, she will need to convince more that 50% of the people on Yap island to accept an alternative ledger.

We went through history and saw how ledgers have evolved from stone tablets to double-entry ledgers. We even took a look at the earliest known examples of distributed ledgers.

Now, let’s discuss the evolution of the ledger in the modern world. Over the last few decades, ledgers have evolved from written for to digital form and digitalized databases. This has enabled us to be interconnected.

Today, the accounting system is being revolutionized again, going from digital realm or centralized databases to information being stored across multiple locations around the globe. This system of recording information across a global network is called a decentralized ledger. A decentralized ledger can be described as a ledger of any transaction supported by a decentralized network from across different locations and people, eliminating the need of a central authority.

When a transaction is made, every participant on the network is notified. They now own an identical copy of the record of transactions, identical to every other node on that network. 

Every piece of information on a blockchain can be traced back to the exact moment when it was created. So, if an audit is conducted, the information can easily be found and deemed reliable. This allows the blockchain to serve as a truly reliable storage of public records and transactions, and eliminate the need for a centralized authority of database of records. 

Now that we understand the foundational principle of blockchains – distributed ledgers, it’s important to understand another key element that makes blockchain so revolutionary ‘Trust’, which is created through two key principles – collaboration and cryptography.

## Cryptography

A great way to think of blockchain is to think of blockchain as another layer on the internet, a layer that enables secure and trusted records and transaction to occur, which is why a lot of people associate the word blockchain with ‘trust’.

Blockchain creates a layer of trust between two parties. Without blockchain to create trusted records and transaction, a 3rd party intermediary is required. Blockchain eliminates the need for a central authority to act as an intermediary between the two parties, and instead leverages cryptography and collaboration to create trust.

In the previous section, we discussed about collaboration through distributed ledger. Now we will take a further look at how cryptography is used in blockchain to create the second element necessary for blockchain to be a source of trust. 

Information on the blockchain is stored on the ledger using cryptography. It can be accessed using key and cryptographic signatures. Now, let’s analyze cryptography and some of its key concepts, that are utilized with blockchain.

## History of Cryptography

There have been three well-defined phases in the history of cryptology. 

The First Phase – Manual Cryptography

The first phase was the period of manual cryptography, starting with the origins of the subject in antiquity and continuing through World War I. The art of cryptography is considered to be born along with the art of writing. As civilizations evolved, human beings got organized in tribes, groups, and kingdoms. This led to the emergence of ideas such as power, battles, supremacy, and politics. These ideas further fueled the natural need of people to communicate secretly with selective recipient which in turn ensured the continuous evolution of cryptography as well.

The first known evidence of cryptography can be traced to the use of ‘hieroglyph’. Some 4000 years ago, the Egyptians used to communicate by messages written in hieroglyph. This code was the secret known only to the scribes who used to transmit messages on behalf of the kings. One such hieroglyph is shown below.

![Hieroglyph](Images/image00234.jpeg)

‘Heiroglyph’ cryptography; Source: https://www.tutorialspoint.com/cryptography

Later, the scholars moved on to using simple mono-alphabetic substitution ciphers during 500 to 600 BC. This involved replacing alphabets of message with other alphabets with some secret rule. This rule became a key to retrieve the message back from the garbled message. 

The earlier Roman method of cryptography, popularly known as the Caesar Shift Cipher, relies on shifting the letters of a message by an agreed number (three was a common choice), the recipient of this message would then shift the letters back by the same number and obtain the original message.

![Caesar Shift Cipher](Images/image00235.jpeg)

‘Caesarshift’ cipher; Source: https://www.tutorialspoint.com/cryptography

It is during and after the European Renaissance, various Italian and Papal states led the rapid proliferation of cryptographic techniques. Various analysis and attack techniques were researched in this era to break the secret codes, like the improved coding techniques such as ‘Vigenere Coding’ came into existence in the 15th century, which offered moving letters in the message with several variable places instead of moving them the same number of places.

Throughout this phase cryptography was limited by the complexity of what a code clerk could reasonably do aided by simple mnemonic devices. As a result, ciphers were limited to at most a few pages in size, i.e., to only a few thousands of characters. General principles for both cryptography and cryptanalysis were known, but the security that could be achieved was always limited by what could be done manually. Most systems could be cryptanalyzed, therefore, given sufficient ciphertext and effort. 

The Second Phase – Mechanization of Cryptography

The second phase, the mechanization of cryptography, began shortly after World War I and continues even today. During this phase, cryptography evolved from the ad hoc approaches to encryption to the more sophisticated art and science of information security. The applicable technology involved either telephone and telegraph communications or calculating machines such as the Brunsvigas, Marchants, Facits, and Friedens (employing gears, sprockets, ratchets, pawls, and cams).  

During the first two years of World War I, code systems were used for diplomatic communications, just as they had been for centuries, and cipher systems were used almost exclusively for tactical communications, however they lacked sophistication and security.

The communications needs’ of telegraphy and radio and the maturing of mechanical and electromechanical technology came together in the 1920s to bring about a major advance in crypto devices: the development of rotor cipher machines. Although the concept of a rotor had been anticipated in the older mechanical cipher disks, an American cryptographer Edward H. Hebern, recognized in 1917, that by hardwiring a monoalphabetic substitution in the connections from contacts on one side of an electrical disk (rotor) to contacts on the other side, and then cascading a collection of such rotors, polyalphabetic substitutions of almost arbitrary complexity could be realized. A set of these rotors is usually arranged in a stack called a basket; the rotation of each of the rotors in the stack causes the next one to rotate, much as the wheels in an odometer advance 1/10 of a revolution for every full revolution of its driving wheel. In operation, the rotors in the stack provide an electrical path from contact to contact through all the rotors. In a straight-through rotor system, closing the key contact on a typewriter-like keyboard sends a current to one of the contacts on the end rotor. The current then passes through the maze of interconnections defined by the remaining rotors in the stack and their relative rotational positions to a point on the output end plate, where it is connected to either a printer or an indicator, thereby outputting the ciphertext letter equivalent to the input plaintext letter.

Starting in 1921 and continuing through the next decade, Hebern constructed a series of steadily improving rotor machines. The 1920s were marked by a series of challenges by inventors of cipher machines to national cryptologic services and by one service to another, resulting in a steady improvement of both crypto machines and techniques for the analysis of machine ciphers. At almost the same time that Hebern was developing the rotor cipher machine in the United States, European engineers, notably Hugo A. Koch of the Netherlands and Arthur Scherbius of Germany, independently discovered the rotor concept and designed machines that became the precursors of the best-known cipher machine in history, the ‘Enigma rotor machines’ used by the participants in World War II. These machines could realize far more complex operations than were feasible manually and, more importantly, they could encrypt and decrypt faster and with less chance of error. 

 

![Enigma cipher machine of World War IIThe German navy employed various versions of the Enigma cipher machine during the war, including this four-rotor model.](Images/image00236.jpeg)

Enigma rotor machine; Source: https://www.britannica.com/topic/cryptology/

The greatest triumphs in the history of cryptanalysis were the Polish and British solution of the German Enigma ciphers, proposed by Alan Turing, whose output was code-named ‘Ultra’. These developments played a major role in the Allies’ conduct of World War II. 

In the years immediately following World War II, the electronic technology developed in support of radar and the recently discovered digital computer was adapted to crypto machines. The first such devices were little more than rotor machines in which rotors had been replaced by electronically realized substitutions. The advantage of these electronic machines was speed of operation; the disadvantages were the cryptanalytic weaknesses inherited from mechanical rotor machines and the principle of cyclically shifting simple substitutions for realizing more complex product substitutions. In fact, rotor machines and electronic machines coexisted into the 1970s and early ’80s. 

One class of electronic devices that function similar to rotors is the Fibonacci generator, named for the Fibonacci sequence of number theory. In the classical Fibonacci sequence 1, 1, 2, 3, 5, 8, 13…each successive term, beginning with 2, is the sum of the two terms to its left; i.e., Fi = Fi − 1 + Fi − 2. In an n-stage Fibonacci generator the contents of an n-bit shift register are shifted right one position at each step – the bit at the extreme right being shifted out and lost – and the new left-hand bit is determined by the logical sum (1 + 1 = 1, 0 + 1 = 1 + 0 = 0 + 0 = 0; symbolized by ⊕) of bits occurring in prescribed locations in the shift register before the shift was made. For example, for n = 5 and xi = xi − 1 ⊕ xi − 4 ⊕ xi − 5 one obtains the 31-bit cycle

0101110110001111100110100100001

which is the maximal-length sequence realizable with a five-stage generator. The relevance of Fibonacci generators to cryptography is seen if the sequence is read five bits at a time by successively shifting one bit position to the left. This yields a scrambled ordering of the integers 1 through 31 that resembles the scrambled ordering produced by rotors.

The cryptographic problem is that the combining operation used to determine successive states in the sequence is linear and hence easily invertible, even though the sequence can be 2n − 1 bits in length before repeating. Another problem is how the key is to be used. The obvious choice, i.e., simply to use the key to determine the number of steps in the cycle from the plaintext n-tuple to the ciphertext n-tuple – Is cryptographically insecure because a known plaintext cryptanalysis would quickly reveal the key. 

To avoid the problems associated with linearity, cryptographers have devised a number of nonlinear feedback logics that possess such desirable properties as diffusion of information (to spread the effects of small changes in the text) and large-cycle structure (to prevent exhaustive search) but which are computationally infeasible to invert working backward from the output sequence to the initial state(s), even with very many pairs of matched plaintext/ciphertext. The nonlinear feedback logic, used to determine the next bit in the sequence, can be employed in much the same way as linear feedback logic. The complicating effect of the key on the ciphertext in nonlinear logic, however, greatly contributes to the difficulty faced by the cryptanalyst. Electronic cipher machines of this general type were widely used, both commercially and by national cryptologic services.

The Third Phase – Data Encryption and Advanced Encryption Standard

The third phase, dating only to the last two decades of the 20th century, marked the most radical change of all – the dramatic extension of cryptology to the information age: digital signatures, authentication, shared or distributed capabilities to exercise cryptologic functions, and so on. It is tempting to equate this phase with the appearance of public-key cryptography, but that is too narrow a view. Cryptology’s third phase was the inevitable consequence of having to devise ways for electronic information to perform all the functions that had historically been done with the aid of tangible documents.

In 1973 the U.S. National Bureau of Standards, issued a public request for proposals for a crypto algorithm to be considered for a new cryptographic standard. A second request was issued in 1974, and International Business Machines (IBM) submitted the patented ‘Lucifer algorithm’ that had been devised by one of the company’s researchers, Horst Feistel, a few years earlier. The Lucifer algorithm was evaluated in secret consultations between the NBS and the National Security Agency (NSA). After some modifications to the internal functions and a shortening of the key size from 112 bits to 56 bits, the full details of the algorithm that was to become the Data Encryption Standard (DES) were published in the Federal Register in 1975.

The DES is a product block cipher in which 16 iterations, of substitution and permutation process are cascaded. The block size is 64 bits. The key, which controls the transformation, also consists of 64 bits; however, only 56 of these can be chosen by the user and are actually key bits. The remaining eight are parity check bits and hence totally redundant. At each intermediate stage of the transformation process, the cipher output from the preceding stage is partitioned into the 32 left-most bits, Li, and the 32 right-most bits, Ri. Ri is transposed to become the left-hand part of the next higher intermediate cipher, Li + 1. 

The right-hand half of the next cipher, Ri + 1, however, is a complex function, Li + f(Ri, Ki + 1), of a subset of the key bits, Ki + 1, and of the entire preceding intermediate cipher. The essential feature to the security of the DES is that ‘f’ involves a very special nonlinear substitution—i.e., f(A) + f(B) ≠ f(A + B)—specified by the Bureau of Standards in tabulated functions known as S boxes. This process is repeated 16 times.

![Flow diagram for the 16-step Data Encryption Standard (DES) operation.](Images/image00237.jpeg)

Flow diagram for 16-step Data Encryption Standard (DES) operation

Source: Data Encryption Standard, FIPS Publ. no. 46, National Bureau of Standards, 1977

 

This basic structure, in which at each iteration the cipher output from the preceding step is divided in half and the halves transposed with a complex function controlled by the key being performed on the right half and the result combined with the left half using the “exclusive-or” to form the new right half, is called a Feistel cipher and is widely used—and not just in the DES. One of the attractive things about Feistel ciphers—in addition to their security—is that if the key subsets are used in reverse order, repeating the “encryption” decrypts a ciphertext to recover the plaintext.

The standard was adopted at the end of 1976 and published at the beginning of 1977. It was mandated that the DES be used in unclassified U.S. government applications for the protection of binary-coded data during transmission and storage in computer systems and networks and on a case-by-case basis for the protection of classified information.

The use of the DES algorithm was made mandatory for all financial transactions of the U.S. government involving electronic fund transfer, including those conducted by member banks of the Federal Reserve System. Subsequent adoption of the DES by standards organizations worldwide caused the DES to become a de facto international standard for business and commercial data security as well.

The security of the DES is no greater than its work factor ‘the brute-force effort required to search 256 keys’. In 1977 that was considered an impossible computational task. In 1997, and in the following years, DES was broken by an exhaustive search attack. The main problem with DES was the small size of the encryption key. As computing power increased it became easy to brute force all different combinations of the key to obtain a possible plain text message.

In January 1997 the National Institute of Standards and Technology (NIST) issued a public request to submit candidates to replace the aging DES. This time 15 viable submissions from 12 countries were received. In October 2000 NIST announced that Rijndael, a program created by two Belgian cryptographers, Joan Daemen and Vincent Rijmen, had been accepted as the new standard, or the ‘Advanced Encryption Standard (AES)’. The NBS had expected the DES to be implemented in special-purpose hardware and hence had given little or no consideration to its efficient implementation in software, i.e., using general-purpose microprocessors. As a result, the DES was unable to take advantage of the rapid development in microprocessors that occurred in the last two decades of the 20th century. The AES specifications, on the other hand, emphasized hardware and software implementations equally. In part, this recognized the needs of smart cards and other point-of-sale equipment, which typically have very limited computational capabilities, but more important was a recognition of the growing needs of the Internet and e-commerce. Based on their experience with the DES, where improvements in computing simply overran the work factor of the fixed 56-bit key, NIST specifications for the AES also called for the algorithm to be capable of increasing the key length if necessary. Rijndael proved itself to be both small enough to be implemented on smart cards (at less than 10,000 bytes of code) and flexible enough to allow longer key lengths.

## Cryptography Concepts

Cryptography is one of the technologies that plays a pivotal role in making blockchain secure and immutable. 

Cryptography is defined as the science of sending messages back and forth from one party to another, in the presence of adversaries. Most cryptographic functions are two-way functions, meaning that we can take a data – encrypt it – and transmit it to someone, and then we can use that same process to decrypt this data at the other end of transmission. The key components of cryptography are:

*   The data or information we are trying to protect
*   The key, which is a piece of data attached to the information we are trying to protect
*   The function which attaches the data and the key, end ensures that the data could not be tampered with, while sending it back and forth between participants
*   Cipher, the encrypted message, which even if is intercepted by adversaries, they wouldn’t be able to know the real data or how to decrypt the cipher back into the original data

Cryptographic hashing is a special class of cryptographic functions. These are one-way functions, meaning they can only encrypt the secret. If I put data into a cryptographic hash, it attaches the data and the key as one entity, which is called the hash result, an encryption based on the data that is encoded. This hash result is mathematically impossible to reverse-engineer, making it a one-way function. If you put any data into a cryptographic has and transmit it to me, I can’t do anything beyond just randomly guessing and trying to recreate the original data. Cryptographic hashes are used in the scenarios where we want to validate a piece of data without actually sharing the data. For example – password management systems used by the banks, where they do not store user name or password of the users registered in the online banking system, just the hash output of the password. This way, if some of the user registered in the banking system enters a password to log in, this is easily validated by the hash of the password, without having to know the real password.

Let’s try to use a simple example to create the hash function

*   Data: “Cryptographic hash makes blockchain secure and immutable”
*   Function: Swap each letter in the data with a new letter as per the key
*   Key: +3
*   Cipher: “Fubswrjudsklf kdvk pdnhv eorfnfkdlq vhfxuh dqg lppxwdeoh”

Let’s deep-dive into the cryptographic hash functions, to understand how they make blockchain tamperproof.

## Types of Cryptography

To understand cryptography in blockchain, we must be able to differentiate between different cryptographic techniques. There are four key methods by which blockchain leverages cryptography.

Public Key Cryptography

This encryption method uses a pair of keys: an encryption key and a decryption key, named as public key and private key respectively. The key pair generated by this algorithm consists of a private key and a unique public key that is generated using the same algorithm. A person’s address on the blockchain is their public key. The transactions on blockchain include their public key and are digitally signed with sender’s private key, to verify the authorization of the transaction. 

Suppose if you want to send me a digital file of your new book to review. I should not be able to tamper it and change the author to myself. Digital signature ensures prevention of such things and integrity of the original message. It has both public and private keys. Public key is the key you give to the public to communicate with you, and private key is the secret key that only you own and use to access your account. Digital signatures can easily be verified using the corresponding public key, which is included in the transaction using a simple 3 step process:

*   Condense the attached message using the same method as the sender
*   Raise the attached signature to the user’s public key
*   Verify that the results of the previous two steps are identical

For example, Ethereum is a public blockchain where anyone can participate in. Here, a user’s identity is an address based on their public key. In comparison, Hyperledger is an enterprise blockchain (a private blockchain) where the participants must be granted access. Here, the identity is managed by X.509 certificates, which are only shared with the parties involved in the transaction.

Public key cryptography uses a pair of public key and private key to perform transactions. Public keys are widely distributed, whereas private keys are kept secret. Using someone’s public key, it is possible to encrypt the message such that the only person with the private key can decrypt and read it. Using a private key, a digital signature can be created such that anyone with the corresponding public key can verify that the message was created by the owner of the private key and has not been modified or tampered since.

![](Images/image00238.gif)

Zero-Knowledge Proofs

A new approach to protecting digital data that validates the knowledge of the information without reveling it.

Zero-Knowledge proofs authenticate the parties without the need to widely transmit private information online. A zero-knowledge proof (ZKP) is a cryptographic method that allows a party (the prover) to prove to another party (the verifier) that a given information is true, without conveying any additional information.

For example, there are two blocks identical in size and shape, except one is red and the other is blue. Tom, who is color-blind, holds the blocks behind his back. Tom then shows one of the blocks to Alice. Tome then hides this block behind his back and shows Alice the other block. Alice can consistently detect the switch because the blocks are different colors, but she never has to reveal the actual color of the blocks to Tom in order to validate the secret.

Zero-Knowledge Proofs are often called ‘zk-SNARKs’, meaning ‘Zero-Knowledge Succinct Non-Interactive Arguments of Knowledge’, or zk-SNARKs for short.

A great example of the Zero-Knowledge Proof is the cave door analogy. Pretend that there is a circular cave, with only one entrance or exit and at the back of this circular cave there is a door which can be unlocked using a secret code entered into a keypad. If I want to prove to you that I know the unlock code without revealing that unlock code to you, all I need to show is that I can walk into one end of the cave, open the door, and come out of the other end. If I have successfully demonstrated that, then you would know that I have been able to unlock the door, however I would not have to reveal the unlock code to you. This simple cave door analogy is a Zero-Knowledge Proof. 

Now, in blockchain a user might make a request to send some money to another user. The blockchain would want to ensure that before the transaction is done, the user sending the money actually has that much money in his account. However, blockchain doesn’t need to know who is sending the money or how much money they have. It only needs to be able to answer the question “Does the user who is sending the money has at-least that much amount to send”, without revealing the sender or his total wealth.

Cryptographic Hash Functions

This type of encryption doesn’t make use of keys. It uses a cipher to generate a hash value of fixed length. The function converts plain text (irrespective of the size) into a hash of fixed size. It is nearly impossible for the contents of plain text to be recovered from the cipher text. For example, our fingerprint and our eye-scan uniquely represent our identity, however we cannot reverse our fingerprint to recreate us. Now suppose you take a flight from London to New York. At the New York airport, the immigration officer scans your fingerprint and your eye. For the person next to you in the queue this fingerprint and eye scan changes. It becomes your unique identifier, which is difficult to forge and tamper. 

The same concept applies in blockchain. Except instead of fingerprints and eye-scans, you can replace yourself with a meaningful information, and your fingerprint with some pseudorandom output (a same random output for a unique input). If we can design a way to generate fingerprints of our meaningful data, we can ensure the integrity of our information. This is achieved by cryptographic hash functions.

A cryptographic hash function is a mathematical algorithm that takes an arbitrary amount of data input (consider yourself) and produces a fixed-size output of enciphered text called “hash” (consider your fingerprint). This hash can then be stored instead of the password itself, and later used to verify the user. A cryptographic hash function must be deterministic, meaning that the same message always results in the same hash.

![](Images/image00239.jpeg)

A cryptographic hash function (specifically SHA-1) at work. 

A small change in the input (in the word "over") drastically 

changes the output (digest). This is also known as 

‘Avalanche Effect’.

Source - Wikipedia

 

A cryptographic hash function has the following key properties:

*   Nonreversible – A good hash function should make it very hard to reconstruct the original password from the output or hash. This is achieved via ‘Preimage resistance’, which refers to the difficulty of finding an input given an output. Mathematically, given a hash value ‘H’, it should be difficult to find any message ‘x’ such that H = Hash(x).
*   Determinism – A given password must always generate the same hash value or enciphered text. This is achieved via the 2nd preimage resistance, which for any given input ‘x’, it should be computationally difficult to find a different input ‘y’, such that Hash (x) = Hash (y).
*   Collision resistance – It should be hard to find two different passwords that hash to the same enciphered text. In mathematical terminology, for a given hash function ‘H’, it is computationally difficult to find two different inputs ‘x’ and ‘y’, such that H(x) = H(y).
*   Non predictable – The hash value should not be predictable from the password.
*   Diffusion (Avalanche effect) – When a password is changed slightly, the output of enciphered text should change significantly and unpredictably.

Informally, these properties mean that a malicious attacker cannot replace or modify the input data without changing its digest. Thus, if two strings have the same digest, one can be very confident that they are identical. Second pre-image resistance prevents an attacker from crafting a document with the same hash as a document the attacker cannot control. Collision resistance prevents an attacker from creating two distinct documents with the same hash.

An illustration of the potential use of a cryptographic hash is as follows: Suppose you give me a tough computational problem to solve and claim that you have already solved it. I want to solve this problem, however I would like to ensure that you have actually solved this problem as well. So, you would write down your solution, compute its hash, and tell me the hash value (whilst keeping the solution secret). Let’s assume that I solve this problem in a week. Now you can prove that you solved it earlier by revealing the solution, which I can hash and validate with the hash value you gave me before.

An important application of secure hashes is the verification of message integrity. Comparing message digests (hash digests over the message) calculated before, and after, transmission can determine whether any changes have been made to the message or file. Using a cryptographic hash and a chain of trust detects malicious changes to the file. Almost all digital signature schemes require a cryptographic hash to be calculated over the message. This allows the signature calculation to be performed on the relatively small, statically sized hash digest. The message is considered authentic if the signature verification succeeds given the signature and recalculated hash digest over the message. So the message integrity property of the cryptographic hash is used to create secure and efficient digital signature schemes.

Bitcoin uses hash function ‘Security Hash Algorithm-256 (SHA-256)’ to validate the Proof-of-Work (PoW) protocols in its network. SHA-256 was originally designed by US National Security Agency (NSA). SHA-256 is a member of SHA-2 family of cryptographic has functions. It takes an input size less that 2^64 bits and produces a fixed size output of 256 bits. Bitcoin, in certain instances uses SHA-256d, meaning that SHA-256 is used twice in a row, once on the original message to be hashed and again on the output of the 1st hash. 

This system uses partial hash inversions to prove that work was done, unlock a mining reward in Bitcoin, and as a good-will token to send an e-mail in Hash-cash. The sender is required to find a message whose hash value begins with a certain number of zero bits. The average work that the sender needs to perform to find a valid message is exponential in the number of zero bits required in the hash value, while the recipient can verify the validity of the message by executing a single hash function. 

Merkle Trees

A data storage technique that compresses data for storing blockchains with a built-in tamper-free component. Merkle trees are built upon hashing principles in that each hash becomes part of the next hash to develop a tamper resistant data storage model.

In computer science terminology, a tree is a data structure that has a root node and some children, which may also be the roots of other trees. A binary tree is a tree in which every node has two children, as shown below.

![](Images/image00240.gif)

A Merkle Tree is a very specific version of Binary Tree, in which every "child" (node) is labelled with the cryptographic hash of a data block, and every node that is not a “child” is labelled with the cryptographic hash of the labels of its child nodes. A hash tree allows efficient and secure verification of the contents of a large data structure. The concept of a hash tree is named after Ralph Merkle, who patented it in 1979.

The following conditions need to be true for a tree to be a Merkle Tree:

*   There is a power of two children at the bottom most level
*   The lowest level is made of the hashes of the summarized information

The construction of the Merkle Tree consists of verified Data Blocks. Each of them is hashed to get a level of hashes.  Then 2 blocks are paired together and hashed, making a new level with half as many blocks. This process is continued till only one hash remains at the top. This has at the top is called the Merkle Root. This way any transaction change can be detected after commitment with the Merkle Root.

![](Images/image00241.gif)

Let’s assume that Block 3 is changed, then its hash will also change. Because of this the hash above will also change, propagating all the way up to the Merkle Root. Hence, if any transaction is changed, then the corresponding Merkle Root is also impacted.

We can validate any transaction with just one piece of information at each level. For example, we can validate Block 1 with Hash 0. This makes the network more and more efficient as the tree grows larger.

In case a Merkle Root somehow gets tampered, it changes the block header. This is turn alters the next block’s ‘previous block hash’, which will impact all the future block hashes as well. The rest of the network will reject the history proposed by this blockchain because they will not agree.

## Disintermediation Effect

Now that we have an understanding how ledgers and cryptography work together to create a layer of trust, let’s discuss how blockchain has a powerful disintermediation effect. 

The developers can create a distributed ledger on a blockchain, and use cryptography to give people secure space on that ledger, enabling people to own their data. You may be asking – “How this is different from traditional technology?” Today, organizations use / store / exchange / sell our data. Blockchain truly empowers the users with ownership of their data, and they can share only the information they desire. It also enables the users to transact peer-to-peer. For example, suppose you go out to eat at a restaurant and pay with your credit card, you are not paying the restaurant directly; instead a database record of your account at your bank is debited and the database record of the restaurant’s bank account is credited. Here, the value and data in the database belong to the intermediary, and not you or the restaurant. You are dependent on the credit card company and the bank to secure and validate the transaction, which shifts the power to these intermediaries. But in the blockchain world, every individual have their own ledger record, and the secure key to access it, hence eliminating the need of an intermediary. Hence, the transaction is simply debited from your record and credited directly to the restaurant’s record. 

Blockchain slows you to have the power to control more than just financial transactions, for example – smart contracts. And with blockchain, you can determine who can access these records.

In previous sections, we discussed how collaboration and cryptography creates trust. Now, let’s examine how peer-to-peer transactions create transparency, which leads to even another layer of trust in blockchain, and also enable to curb corruption as well as optimize costs.

The databases are generally inaccessible and do not communicate effectively with other systems. This makes it easier for people within centralized organizations (e.g. – banks) to manipulate these records. In order to avoid manipulation, many expensive safeguards are done through regulations and legal requirements, thereby creating expensive overhead costs and delays. Further, there are many necessary safeguards from external forces, since bad actors need to identify only one point of failure to access the network. The combination of one central point of storage and the storage of valuable data make these centralized database an enticing target for malicious actors.

With blockchain, these malicious actors would have to identify and target numerous points of failure until they control more than 51% of the network, which is known as consensus. It is nearly an insurmountable task.

Centralized databases need to constantly update and synchronize data, leading to high costs and vulnerability to bad actors. Hence, blockchain creates trust and offers financial benefits through transparency, immutability, and accessibility through ownership.

## Transparency

The blockchain is designed such that its entire history is visible and unchangeable. Transactions in blockchain cannot be modified after creation, and their complete history is publicly visible. This means that the blockchain is a completely transparent data structure with a useful property that the integrity of blockchain can easily be verified by any user.

One of the big benefits of blockchain, public or private, is ‘transparency’. In a public blockchain like Bitcoin or Ethereum, because they are anonymous and there in no concept of identity, there is no way of treating users differently. Hence, the data on a public blockchain is transparent and visible to all the participants. It adds a lot of value from the perspective of exchanging currency, because as long as the anonymity of the participants is protected, anybody is able to validate the details of any transaction on a ledger that is immutable, permanent, cannot be changed, and offers a high degree of trust. This also has a lot of potential use cases for public blockchain like voting, voter registration and tracking election results. On public blockchains, there is another kind of transparency, ‘full transparency’ into the smart contracts that execute on a blockchain. These smart contracts have the potential of working with other people’s money, and if you are going to entrust your money into someone else’s smart contract, you should have the ability to review the source code of that smart contract, to ensure that it is written fair, there are no security vulnerabilities, and that it does what it claims to do.

On the private blockchain, what we have is ‘permissioning’, and we can control how much data to share. We still have a lot of benefits of being able to share data in a shared infrastructure that a private blockchain creates. There are a lot of business networks and value chain relationships where the participants would be able to share more data and more information with consumers about business processes and service delivery. While technically conventional technology may be able to address these concerns, it is often seen that people are not able to come to consensus on questions of who owns the platform, who builds the platform, and who maintains the platform. If the participants leave the ecosystem, do they take all or part of the platform with them. Using private blockchain solutions like Hyperledger, many of these concerns can be alleviated and a truly shared technical infrastructure between organizations is enabled. This allows participants to track data as well as share data about creation, consumption and delivery of goods. It is estimated that over 1/3 of the food produced is wasted, as there is no clarity into its supply chain. For example, if a meat gets recalled due to contamination, a huge amount of perfectly good meat is discarded. Whereas if we had a greater visibility into where the product originated and how it went from production to purchase, then more accurate recalls can be enabled which will help reduce waste. Similarly if you are manufacturing and distributing clothing, and can demonstrate to the users that all clothing was sourced from places with fair labor practices, consumer will have more trust on your brand. So, these kind of transparency solutions are one of the biggest benefits of blockchain and one of the areas being most explored, because right now there are a lot of consumers who would want more visibility into the products and service the purchase; and blockchain can be a great solution for enabling that.

## Immutability

One of the big benefits of blockchain is ‘immutability’. The idea is that once a record gets committed to the blockchain or to the ledger, it is there permanently. 

In a traditional database, we can create, edit, and delete the records. However in a blockchain, there are only 2 possible operations: create a new record, and read existing records. This contributes to the idea of immutability, that once data is written in the blockchain it cannot be edited or deleted. In order to update the date, you need to append another record over the existing record showcasing that something about that data has changed.

This immutability is what make blockchain a secure and trustless solution, meaning that I do not have to trust anybody that I am interacting with on the blockchain, as long as we both trust in the blockchain and the data on the blockchain. Hence, we can transact back and forth seamlessly. 

The way immutability work in the blockchain is very inefficient. We are asking a large number of nodes on the network to perform exactly the same operation as every other node, resulting in duplication of work over and over again. The reason to do this is, because it ensures that the only way to change data on the blockchain is by changing that data on 51% or more of the nodes on that blockchain. Moreover, when the network becomes very large, Bitcoin for example having thousands of nodes, it becomes practically impossible to change data on the blockchain.

One important point to note is that blockchain does not do anything to validate that the information written on it is correct. It only validates that the information has not changes since it was originally written.

The immutability that blockchain provides is that data has not changed since it was originally written. Another part of this immutability is cryptographic hashing, and the way all the blocks are chained together. The blockchain is designed such that immutability is cumulative; each node is linked to every other node, creating a cohesive whole that becomes more difficult to tamper or alter. If I ever go back and try to change any information or prior transaction on the blockchain, I would break the chain in a very obvious way that anyone would immediately spot that data has been altered on the blockchain.

*   At the bottom level, transactions are digitally signed by their creators. An attacker cannot forge a transaction unless they steal a private key
*   A block structure is predefined. Attackers cannot modify it
*   Each block includes the hash of the previous block, creating a chain between each block in the blockchain, which will break if tampered
*   Each block is digitally signed by its creator. The creator is selected through blockchain consensus protocol, making it difficult for an attacker to be a legitimate creator.

All these four features make blockchain immutable and tamper proof.

 

 

 

 

 

 

 

 

# Blockchain Functions

In this chapter, we will focus on the blockchain functions. First, we will discuss smart contracts, how blockchain have the ability to store and run applications that can execute the terms of an agreement. These digital agreements stored and executed on the blockchains remove intermediaries and ambiguity, thereby reducing conflicts.

We will discuss how blockchain secure information and how the techniques differ from the traditional database security. Next, we will discuss different types of blockchains (public, private, and hybrid) and design principles for blockchain development. We will examine steps in a basic blockchain transaction from start to finish.

Finally, we will discuss blockchain consensus mechanisms and why they are backbone to the blockchain operations. We will compare Proof-of-Work (PoW) and Proof-of-Stake (PoS) consensus models, and discuss the differences and considerations. We will further discuss private blockchains and how ‘permissioning’ mechanisms are the basis for their ConsenSys models.

## Smart Contracts

 When we make a transaction on blockchain, there are only 3 types of transactions we can make. It can be referred to as Onion model. 

Let’s start with the outermost layer of this onion. This layer is used to do transactions of the blockchain, like trade cryptocurrencies back and forth. For example, I paid you 10 Bitcoins to purchase your home, and we use blockchain to conduct and record this transaction. This is the model that many of us start off with in blockchain and the one that is most familiar.

Now, if we peel the outer layer, and take away the idea of monetary transaction or exchange, we are left with 2 or more parties using the blockchain to record an event or an agreement. For example, I go to my doctor for health checkup and he prescribes me a new medicine. Suppose we are keeping our medical information on the blockchain, and so both my doctor and I agree to put this new prescription on the blockchain. In this case, we still need 2 or more parties, because it is very important that I, as a patient, do not have the ability to update and alter my medical record without a licensed medical professional involved. Similarly, my doctor should not be able to alter my medical record without my consent. So, here 2 or more parties are involve to record a data point, without the exchange of any monetary value.

Now, if we peel away this layer, we get the innermost layer wherein we can take away the idea of having 2 or more parties. We are left with just a single party announcing an event. This is the simples type of blockchain transaction, and also the most powerful. For example, in a supply chain scenario, we might have a producer of organic food announce a record to the blockchain that they have planted a crop. Now this is a single entity making a record on the blockchain., and here is where the smart contracts come in.

These smart contracts are just computer code that we can use to respond to any kind of event that gets captured on the blockchain. For example, in the previous example, if I need to notify someone that the new produce has been treated with organic pesticides, I can record that transaction on the blockchain and create traceability for the end consumer. Here I can use a smart contract that manages and defines the rules and steps that gets taken when that particular type of event occurs. This is where smart contracts come into play.

There is often a misconception when people hear the word contract that they think it is a legally binding agreement between 2 or more parties. It is not necessary the case. Smart contracts do not have to be legally binding and they do not have to involve multiple parties. 

You can think of smart contracts as a set of rules that get executed every time a certain type of event occurs. And this is where the real power of blockchain comes in that not only we have a permanent, unchangeable record of all the events that have occurred, we can also write computer codes to define exactly how the process is going to be managed and what steps need to be taken when that particular event occurs. This allows us to ensure process consistency.

So, when you hear smart contracts, just think of it as a computer code that you write to respond to different types of significant events. In computer language, you can also think of smart contract as a workflow tool, with the ability to work with money. These smart contracts are just a way for us to put our logic into the blockchain solutions to ensure consistency of execution.

Some key characteristics of smart contracts are:

*   Smart contracts are computer programs that can execute an action based on terms and conditions
*   Smart contracts have terms recorded in a computer language instead of legal language.
*   Smart contracts are not necessarily legal binding and do not need multiple participants
*   Each step of the smart contract can only be implemented after the execution of the immediate previous step
*   Once executed, the information in the smart contract is stored on the blockchain and cannot be altered
*   In the Ethereum platform, smart contracts are written in ‘Solidity’ programming language designed for developing smart contracts that run on Ethereum Virtual Machine (EVM)
*   Smart contracts act as a foundation to build decentralized applications (DApps)

Some key benefits of smart contracts are as follows:

*   Accuracy – Replacing human intermediaries with executable code removes any human error and ensures the accuracy of the process
*   Cost savings – Replacing intermediaries reduces operational costs
*   Efficiency – Removing intermediaries reduces redundant process steps as well as automates processes, resulting in significant process efficiency gains
*   Backup – A blockchain and smart contract deployed to it can provide a permanent record, allowing for auditing, insight, and traceability, even if the creator is no longer in business
*   Autonomy – Smart contracts can be developed by anyone. There is no need for intermediaries such as lawyers, brokers, or auditors

A use case of the smart contract can be for funding a startup. Let’s say that I have started up a new company and you intend to invest $ 1 million in my startup. Let’s say instead of investing $ 1 million directly, you write a smart contract on the blockchain to manage this investment, and you put $ 1 million into this smart contract. This smart contract has been programmed with the terms and conditions under which it releases $ 100,000 initially and then the next $ 100,000 on achievement of a milestone, like product go-live, and then the next $ 300,000 on another milestone, like hitting 10,000 customers, and then the final $ 500,000 on expanding to a new geography. This would put a lot of power in your hand and would keep me accountable for achieving the milestones that I promised in my startup pitch to raise funds. While such things are also possible with traditional technology, they are not very practical or feasible. In this case, blockchain based smart contracts puts the power back in the hands of the investors and has the potential to reform the startup funding ecosystem.

## Blockchain Security

 Blockchain is commonly called the future of computing. It takes a very different approach to data storage and processing and requires a very different perspective for security. In this section, we will discuss some of the ways in which blockchain security differs from traditional security.

In a traditional cybersecurity, we are very perimeter focused that we put trusted data and asset behind a strict perimeter. We assume that anyone we let inside that perimeter is trusted, either partially or fully, to see the data and access the resources inside that perimeter. The emphasis is on making sure that only authorized users get into the perimeter, and prevent any attacker or stranger from breaching the perimeter and accessing the data stored in it.

In blockchain its very different, as it runs on a massively decentralized peer-to-peer global network. Since there is no perimeter on blockchain, the security has to come from somewhere else. The security on blockchain comes from incredible amount of repetition. In blockchain, every node keeps the same copy of the ledger and periodically has to reach majority consensus, on what the data on the ledger should be. Hence, the amount of work an attacker would have to do in order to change, alter, or hack the ledger is practically impossible.

Another big difference between traditional cybersecurity and blockchain security is with conventional applications and conventional technology. In traditional cybersecurity, we either develop all our applications in-house or rely on a single, third party trusted provider to create the application for us. All the code, generally, comes from one place, and if we don’t write it ourselves, all we have to have is trust and faith in the third party providing the solution. In blockchain, often we write smart contracts which call code from other smart contracts, which may come from a variety of authors. 

So whereas in the traditional cybersecurity space, we rely on our own due diligence to write secure code or the due diligence of a third party application provider; in blockchain, we have to spend a lot more time and energy to ensure to ensure that the codes and contracts are safe and secure.

And the final big difference is that in conventional line of business system, all the applications either run directly on a trusted hardware that we own or run on a hardware with a high degree of trust provided by a third party like Microsoft Azure or Amazon Web Service. In blockchain, all codes run on untrusted resources, untrusted hardware that can be owned by anyone, anywhere in the world. This implies that we must ensure that all the trust in the blockchain solution comes from the protocol and the code layer itself, as it’s a distributed network, and we do not direct control or access into the hardware that supports it.

 
| Traditional Cyber Security || Blockchain Security |
| --- | --- |
| Centralized || Decentralized |
| Perimeter-focused || Distributed |
| Trusted or semi-trusted infrastructure || Trustless environment |

 

 

Security Attacks

*   Denial of Service – A denial of service (DoS) attack is when an attacker makes it impossible for a system to serve it users as designed. This can be accomplished by exploiting a flaw in the system, but, more commonly, is accomplished by performing legitimate actions at a rate higher than the target can handle. To be effective, denial-of-service attacks typically focus on the system’s weakest link or bottleneck. 

 
| Traditional Environment || Blockchain |
| --- | --- |
| Denial-of-service attacks target a company’s web server to prevent customers from accessing its services. This can be accomplished by making more connection requests than the server is capable of supporting. || Denial-of-service attack involves submitting more transactions to the blockchain than it can handle. Since many blockchains have fixed-size blocks created at a fixed rate and are stored in a distributed fashion, they have a maximum capacity that a determined attacker can exceed, rendering the blockchain unusable. |

 

*   Endpoint Security – Traditional infrastructure and blockchain environments also differ with regard to the endpoint security. Endpoint security originated to ensure multi-layer prevention against malware, fraud, cyber threats, and attempts to extract private information.

 
| Traditional Environment || Blockchain |
| --- | --- |
| Endpoints are under the control of the enterprise and have some level of heterogeneity. Heterogeneity can be dangerous because an attacker has more options for finding a vulnerability to exploit. || Endpoints are the nodes and may be completely homogeneous. While homogeneity means that a flaw in one system is a flaw in all of the systems, blockchains built in trust and data privacy feature guard against such attacks. |

 

*   Code Vulnerability – Computer applications are dependent on a reliable code. Another way traditional security and blockchain differs is in the level of trust in the code used in a company’s application.

 
| Traditional Environment || Blockchain |
| --- | --- |
| The company writes most of the code, and vulnerabilities can arise only from the code that the company controls. || Anyone can write a smart contract, and a flaw in the smart contract or the underlying platform code can have wide-reaching consequences. But since smart contracts can be vetted and reused, such inconsistency can be edited from the code.  |

 

*   Intentional misuse – Both traditional and blockchain environments are vulnerable to attacks based on the intentional misuse of the system.

 
| Traditional Environment || Blockchain |
| --- | --- |
| Insider attacks or intentional misuse of the system by clients are possible. In fact, a denial-of-service attack is a specific type of intentional misuse. || Blockchain systems are set up to incentivize network participants, miners or nodes, to do something that is in their best interest. A weakness is, if more than half of the network’s processing power is controlled by a single group, the network is controlled by that group.  |

 

*   Data protection – Traditional and blockchain environments differ in their goals regarding data protection.

 
| Traditional Environment || Blockchain |
| --- | --- |
| Data is siloed, and access is strictly controlled by the owners, placing responsibility for confidentiality, integrity, and availability in their hands. || Data is distributed, and the blockchain is relied upon to provide integrity and availability.  |

 

## Types of Blockchains

When people get into blockchains, there is a natural discussion about what type of blockchain, because they are of many types.

*   Public Blockchain – A public blockchain is open for anyone to join. Public blockchains are decentralized where no one has control over the network. These immutable and censorship resistant networks are ideal for participants who do not trust each other, but still interact in a network and take part in consensus. Public blockchains are permissionless, as anyone can effectively join the blockchain network. Bitcoin and Ethereum are examples of public, permissionless blockchains. 
*   Private Blockchains – Private blockchains define a user’s rights on the network prior to admittance. Restrictions are placed on activities such as who can write to the ledger and which transactions they can participate in. These blockchains are also called permissioned blockchains, as participation is permissioned by an organization or a consortium of organizations, who define which members can participate in certain transactions and consensus in the network. Hyperledger and Corda blockchains are examples of private, permissioned blockchains.
*   Open Blockchain – In an open blockchain everyone in the network can read the data. Everyone in the network can read all the transactions.
*   Closed Blockchain – Closed blockchains define a user’s rights to read the data on the network. Restrictions are placed on activities such as who can read which transactions.

When we talk about public and private blockchains, what we are really talking about is who is able to write data onto that blockchain or onto that immutable ledger. The open versus closed blockchains brings in to consideration who is able to read that data. 

It is important to consider both the parameters, so you know where on a possible solution quadrant your idea falls. So there are four type of solutions:

*   Public and Open
*   Public and Closed
*   Private and Open
*   Private and Closed

![](Images/image00242.gif)

Types of Blockchains

Public Open Blockchains

When we talk about public blockchains, what we are generally talking about is a public open blockchain, wherein anyone can write the data on to the blockchain, and anyone can read that data. 

The public blockchain platforms like Bitcoin, Ethereum, Litecoin are what we also refer to as permissionless blockchains platforms meaning that they really strive to, by design, increase and protect user’s anonymity. If we do not know who a user is and do not have a way of identifying users, we do not have any way of creating permission or access rules around that user. Hence, anyone can write data to the blockchain and anyone can come along and read data from that blockchain. So when you think of public blockchains like Bitcoin or Ethereum, understand that by default and by their nature, they are designed to protect anonymity.

In a public blockchain, since we do not know who the user is, we rely on economics and game theory incentives to ensure that everybody in the system behaves honestly and according to the rules. We set up situations through group consensus, through which honest participants are economically rewarded, and wherein dishonest ones only incur work or cost, with no possibility of ever recouping that cost.

Some key benefits of public blockchain are:

*   Ledger is distributed – The data base is not centralized like in a client-server model, and all nodes in the blockchain participate in transaction validation.
*   Immutable – When something is written to the blockchain, it cannot be changed.
*   Open consensus Model – No restriction placed on who can operate a node in the network.
*   Open read and write – Anyone can participate by submitting transactions to the blockchain, such as Bitcoin or Ethereum.
*   Low barrier to entry – Transactions on a public network can be accomplished with an internet connection and a cell phone.
*   Secure – With the 51% consensus protocol, the transactions are secure. Obtaining a majority of network power could potentially enable massive double spending, and the ability to prevent transaction confirmations, among other potentially nefarious acts. This has never been accomplished, as the computing power to stage such an attack would be too costly.

Private Closed Blockchain

The counterpart to the public blockchain is the private blockchain or permissioned blockchains.

When we talk about private blockchain solutions, we generally talk about private closed blockchains. We want to control who can write data to this blockchain, as well as control who can read data from this blockchain. 

In order to do that, the first step is identity management. Private blockchains tend to come with identity management tools or a modular architecture, where you can plug in your own identity management solution. This can be anything from an Active Directory deployment to an OAuth solution using Google, Facebook, LinkedIn, etc. 

The idea behind the private blockchain begins with understanding who the user is, because once we understand who a user is, we can determine what role they are in, and we can use that role to determine what information should they have access to.

In a private blockchain, we rely on the fact that we know who the user is, to ensure they behave honestly. We assume that these users are going to behave fairly honestly, because if not, we know exactly who is dishonest and can determine the consequences of dishonest behavior.

Some key benefits of private blockchain are:

*   Ledger is distributed – The data base is not centralized like in a client-server model, and all nodes in the blockchain participate in transaction validation.
*   Immutable – When something is written to the blockchain, it cannot be changed.
*   Compliance Support – As an enterprise, you likely would have compliance requirements to adhere to, and having control of your infrastructure would enable this requirement more seamlessly.
*   Faster Transactions – When you distribute the nodes locally, but also have much lesser nodes to participate in the ledger, the performance is faster.
*   More efficient consensus – Enterprise or private blockchains have less nodes and usually have a different consensus algorithm, such as Byzantine Fault Tolerance (BFT) versus Proof-of-Work (PoW).
*   Scalability – Being able to add nodes and services on demand can provide a great advantage to the enterprise.
*   Enterprise permissioned – The enterprise controls the resources and access to the blockchain, hence private and permissioned.

Blockchain considerations

Companies must consider multiple factors when deciding how blockchain will fit into their business model. There is not a “one size fits all” blockchain but rather a well-thought-out approach that considers these multiple options.

*   Governance – Governance of blockchains deals with a system for managing and implementing changes to blockchains.
*   Smart contract functionality – Each organization has unique needs when deciding on smart contract functionality. Such decisions as to the design, implementation and testing of these digital promises need to be determined. Can smart contract replace current work flows? Can a smart contract fit in the current business model?
*   Consensus algorithms – Consensus models change depending on the type of blockchain environment you are creating. In order for a blockchain to work, the participants must come to an agreement as to the transactions in the ledger or the state of the ledger. This agreement is called consensus. Public blockchains have miners that are incentivized to reach consensus whereas private blockchain set up enterprise nodes that agree to the state of the ledger.
*   Integration – Consideration for current work flows and how to bridge blockchain platforms with existing systems. How can blockchain add value to the current organization while leveraging current systems?
*   Cryptocurrency requirements – If and how the blockchain will exchange value among participants are important discussions that need to occur in the design phase.
*   Cost modeling – How to split the technology cost among participants in a fair and equitable manner?

Overall these decisions will be made by the following actors in the blockchain system:

*   System Architects – They design and build blockchain networks. They decide on the node types and membership rights.
*   System Developers – They design the smart contracts for users.
*   System Operators – They interact with the software, ‘permissioning’ and onboarding participants. This includes storing the ledger, creating wallets and managing credentials.
*   Blockchain users – They join a blockchain network by setting up a wallet and receiving permission to engage in a particular function.

## Blockchain Transaction Flow

Although blockchains differ in form and function, they follow a basic transaction flow.

![](Images/image00243.gif)

1.  User request – Let’s follow these steps with a basic Bitcoin transaction. If Alicia wants to send Billy some Bitcoins, she would go to a Bitcoin wallet application either on her phone or a computer where she has some Bitcoins stored. To initiate the transaction, Alicia would make a request to the system to send Bitcoin to Billy’s wallet by specifying the amount and Billy’s Bitcoin address.
2.  Smart contract enabled – When Alicia sends her transaction to the network, it triggers a smart contract that checks with the nodes on the network to make sure that Alicia has the currency to spend, and that she hasn’t already spent it. Once checked, the transaction is added to a proposed block.
3.  Transaction announced to the network – Proposed block in communicated to the network through the peer-to-peer protocols.
4.  Network agrees to the transaction – In order for the Bitcoin network to validate a block, nodes or miners must validate the accuracy of a block by completing a math problem first. The node that completes the Proof-of-Work (PoW) equation first is rewarded with some newly minted Bitcoins. Once a solution for the equation is reached, the other nodes can easily check its accuracy, thereby accepting the new block into the blockchain network.
5.  All copies of the ledger updated – The block is spread throughout the network through the same peer-to-peer communications that we used for the transaction. When the block operators receive a copy of the new block, they add it to their copy of the distributed ledger. This guaranteed that all members of the peer network agree on the current state of the blockchain’s distributed ledger.
6.  User notified of completed transaction – The user’s wallet monitors for the creation of new blocks that include transactions associated with the user. When a block containing the completed code from the user’s operation is received, an event is created to notify the user that the operation is complete. When the block containing Alicia’s Bitcoin transfer to Billy is added to the blockchain, an alert will be sent to the relevant wallets that the transaction was accepted and completed.

## Blockchain Consensus

Since blockchain information is stored by everyone in the network, a consensus is needed to ensure that everyone agrees on the transactions’ history. Not only do all the users need to agree on any transaction update, but they also need to agree on a valid transaction update to make sure that no corrupted information is acquired by the network. 

Consensus mechanism enables blockchain to move away from a centralized system where one entity keeps track of the ledger towards a decentralized system where trust does not rest with one entity but all entities and what they decide together. The blockchain is a distributed and decentralized system, which means that it needs to have a way of tracking the official current state of the system. Since the blockchain can include financial transactions and business agreements, it is important that all parties involved all in sync regarding the terms of the agreement.

As discussed in “Blockchain Consensus and Fault Tolerance in a Nutshell” article by Demiro Massessi, “The blockchain is designed to be a shared, synchronized historical ledger, meaning that there needs to be a final decision at some point on what should and shouldn’t be included in the official record. Since blockchain is decentralized, there is no higher authority that can rubber-stamp and finalize the contents of a blockchain block. The method that Satoshi Nakamoto, creator of the Bitcoin network, invented to achieve consensus is based on scarcity. In one way or another, blockchain consensus algorithms boil down to some kind of vote where the number of votes that a user has is tied to the amount of a limited resource that is under the user’s control. Based on the economic law of supply and demand, collecting enough of an asset to have a controlling share will drive up the price of the asset enough to make achieving that level of control unfeasibly expensive”.

In order to ensure that no one spends the same Bitcoin twice, Satoshi Nakamoto created the consensus algorithm called Proof-of-Work (PoW) for the Bitcoin network. 

Since them, several other consensus algorithms have been invented as per the requirements of the use cases. These include Proof-of-Stake (PoS), Delegated Proof-of-Stake, Practical Byzantine Fault Tolerance, and Proof of Elapsed Time. 

The most commonly used consensus algorithms are Proof-of-Work (PoW) and Proof-of-Stake (PoS).

Proof-of-Work (PoW)

Proof-of-Work (PoW) refers to the cryptographic mechanism that relies on participants being able to solve hard computational problems to have a higher stake in the network. PoW essentially is a distributed way for participants to determine the most valid block. Each participant attempts to find a hash value, which is a valid solution for the upcoming block of transactions. The winner who finds the hash value that meets the requirement, adds the proposal block to the chain, and obtains the reward.

Bitcoin Consensus Mechanism via Proof-of-Work (PoW)

The most common definition of Bitcoin’s consensus algorithm is proof-of-work (PoW), the consensus mechanism that relies on participants solving cryptographic puzzles to validate new information. However, PoW is part of a larger consensus algorithm that is commonly known as “Nakamoto Consensus.” Nakamoto Consensus is what made Bitcoin different from prior digital currency implementations.

Bitcoin uses ‘Hashcash Proof-of-Work’ to achieve consensus, using a hashing algorithm SHA-256. This involves finding a value ‘x’ such as that when ‘x’ is hashed with this algorithm, the required value is found. This is often an iterative process; nonces (numbers used once) are added to the end of the string being hashed each successive round until the required value is given. Once the participant manages to find a solution to the PoW, they broadcast their block to the rest of the network, where it is then approved if none of the transactions within have already been spent based on the timestamp. Participant then receives a reward in Bitcoin as compensation for the amount of computing power they spent in order to validate the next block of transactions.

Mining in Bitcoin is really the commitment of a certain amount of computing resources to the sole purpose of solving computationally hard problems and validating new blocks. The more computing power an individual node has, the more likely it is to find a correct value for the SHA-256 hash, and thus solve the cryptographic hash associated with that block’s PoW. 

PoW enables Bitcoin to be both fully decentralized and fully secure. Anyone can participate in the mining process, without needing to own a certain number of Bitcoin beforehand in order to do so. In fact, it is completely unknown who the winner of the next mining reward will be at any given point in time, with additional computing power only serving to increase the probability that an individual node will be successful. Furthermore, the mining process also incentivizes nodes to act honestly because of the rewards associated with broadcasting the correct block. This means that in order to take over the network, a malicious attacker has to control over 51% of the computing/hashing power on the network and prevent legitimate blocks from being validated. This is commonly known as a “51% attack.” Due to the Bitcoin network’s current size, the economic cost of accruing over 51% of the hashing power currently present in the network is huge, and thus extremely difficult.

The second part of Nakamoto Consensus is what allowed Bitcoin to be the first scalable cryptocurrency platform. Nakamoto Consensus places a large emphasis on the longest chain, arguing that the longest chain that is also valid according to timestamps is the most legitimate, as it had the largest amount of computational resources dedicated to it. This introduces trust in an otherwise trustless system, thus allowing the Bitcoin network to function without a centralized authority. For example, if a participant has been inactive, or has newly joined, they can simply accept the current longest chain as proof of what happened previously within the network. They do not need to rely on a 3rd party; rather simply start build upon the longest valid chain, thus gaining the ability to receive rewards by proposing a computationally valid block. In fact, the “longest chain rule”, as it has been dubbed by the cryptocurrency community, enabled Bitcoin to succeed where previous PoW digital currencies had failed. It allowed participants to have confidence in the network, as well as set a standard through which miners could begin to join and leave at will without having to defer to an authority. The longest chain rule has been adopted by numerous digital asset systems and blockchains that came after Bitcoin.

Proof-of-Stake (PoS)

Proof-of-Stake (PoS) is another type of consensus mechanism used to validate cryptocurrency transactions. With this system, owners of the cryptocurrency can stake their coins, which gives them the right to check new blocks of transactions and add them to the blockchain. The first functioning use of PoS for cryptocurrency was ‘Peercoin’ in 2012. 

For a blockchain transaction to be recognized, it must be appended to the blockchain. The miners adding the blocks receive a reward for doing so. For the blockchain to remain secure, it must have a mechanism to prevent a malicious user or group from taking over the validation. 

PoS accomplishes this by requiring that validators have some quantity of blockchain tokens, requiring potential attackers to acquire a large fraction of the tokens on the blockchain to mount an attack. PoS model allows owners of a cryptocurrency to stake27 coins and create their own validator nodes. 

When a block of transactions is ready to be processed, the cryptocurrency's PoS protocol will choose a validator node to review the block. The validator checks if the transactions in the block are accurate. If so, they add the block to the blockchain and receive crypto rewards for their contribution. However, if a validator proposes adding a block with inaccurate information, they lose some of their staked holdings as a penalty.

As an example, let's look at how PoS works with Cardano, a major cryptocurrency based on PoS protocol. Anyone who owns Cardano can stake it and set up their own validator node. When Cardano needs to verify blocks of transactions, its Ouroboros28 protocol selects a validator. The validator checks the block, adds it, and receives more Cardano for their effort.

Proof-of-Stake and Proof-of-Work are the two most common types of consensus mechanisms cryptocurrencies use. PoW was the method of choice for early cryptocurrencies, including Bitcoin and Ethereum, while PoS originated in 2012 with Peercoin  and has become a common choice for altcoins.

PoS uses validation of staking power to verify transactions, whereas PoW uses validation of computational prowess to verify transactions. 

Proof-of-Work (PoW) versus Proof-of-Stake (PoS)

The biggest difference between PoS and PoW is their energy usage. PoW requires miners to compete to solve complex mathematical problems. The first miner to solve the problem gets to add a block of transactions and earn rewards. This results in mining devices around the world computing the same problems and using substantial energy. Since PoS doesn't require validators to all solve complex equations, it's a much more eco-friendly way to verify transactions.

Comparisons between PoS and PoW:

 
| PoW || PoS |
| --- | --- |
| One computer, one vote || One coin, one vote |
| Anyone with computer can validate blocks || Only coin owners can validate blocks |
| Anonymous participation || Participants identified using digital signatures |
| Miners are randomly selected, in proportion to hash power || Validators are randomly selected, in proportion to stake |
| Reward is given to the 1st miner || Collect network fees as their reward |
| Huge energy cost in order to solve complex hash algorithms || Much more cost and energy efficient |

 

 

 

 

The pros and cons of PoS protocol are as follows:

 
| Pros || Cons |
| --- | --- |
| Energy efficient || Not as proven in terms of security as PoW |
| Fast and inexpensive transaction processing || Validators with large holdings can have excessive influence on transaction verification |
| Doesn’t require special equipment to solve complex has problems || Some PoS cryptocurrencies require locking up staked coins for a minimum amount of time |

 

PoS is uncertain for security risks as it is recent and not much experienced or accepted as PoW. PoW protocol is considered more secure regarding double-spending where continuous forking is discouraged by the miners as it makes the network unstable. While forking, miners must decide whether to follow original blockchain or adjust to the new blockchain. To maintain both the blockchain, miners distribute their computational resources to both original and the new blockchain. On the contrary, PoS called this problem as ‘nothing at stake’ problem. Here, validator receives a duplicate copy of stake on forked blockchain, and he can claim double transaction fee as reward after signing out from both the split blockchain. To solve this problem, this consensus required to enforce a deposit locked for certain periods. Casper is a protocol which encourages PoS protocol for the validators to participate with minimum deposit. The deposit could be taken away in case the protocol finds any violation by the validator while constant forking.

Consensus Mechanisms in Private Permissioned Blockchains

*   Hyperledger Fabric Consensus Model – Hyperledger Fabric is a private permissioned blockchain platform that breaks consensus into components, allowing users to pick a consensus algorithm for their particular situation. Instead of a predetermined consensus model, Hyperledger has an ordering service that performs consensus related events, this ordering component can pick the consensus model that best suits the blockchain needs. By approaching consensus in this modular fashion, Hyperledger DLT’s can change consensus models without huge overhauls to the code base.
*   Corda Consensus Mechanism – Corda is a private permissioned blockchain. Each Corda network has a notary service made up of independent parties that approve blocks using any applicable consensus algorithms. As mentioned in Jamiel Sheikh’s bool “Mastering Corda: Blockchain for Java Developers”, R3 PROVIDES A SET OF Corda applications called The Corda Business Network Toolkit to manage one or more Corda networks. Corda does not follow the standard blockchain model of transactions being bundled into blocks and then being finalized by the network as a whole. Instead, a Corda network contains one or more notaries consisting of several independent parties. Transactions in Corda are finalized by a notary with a multiparty digital signature using an algorithm like Raft.

 

 

# Blockchain Governance

In this chapter, we will cover blockchain governance. We will start by discussing the cooperative way blockchain companies share the computer code for this technology. We will also explore how this open source environment is fostering new innovations. And then we will examine who really is in charge of blockchains and hoe the network effect determines the direction a blockchain will take.

Next, we will take a look at how these trustless systems with open interactions are more secure than past systems. Finally, we will dive into the idea of collaboration among parties who do not trust each other and how blockchain technology is changing how they can interact. This new form of world wide collaboration can be the key to solving world’s toughest problems.

## Open Source

Blockchain technology and the developers who work with it reinforce the basic tenet of decentralization in many ways. Not only by decision making consensus models, but also the way in which it distributes the software code.

*   Proprietary / Closed source code – Software controlled by the person, team or organization who created it and maintains exclusive rights over it. Only the original authors can legally copy, inspect, and alter the software. Most users of proprietary software sign an agreement giving permission to use the software but not alter it. Microsoft Office is an example of proprietary software.
*   Open source code – Computer code that describes a specific approach to creating software. When describing tools for distributing open source code. Discipline Tool states, open source initiatives embrace and celebrate principles of open exchange, collaborative participation, rapid prototyping, transparency and community-oriented development. Open source software is code that anyone can inspect, modify and enhance. Much of the internet was built on open source technologies. Users of the computer software never interact with the source code, rather it is manipulated by programmers who improve and fix it. As with proprietary software, users must accept the terms of license, but they are dramatically different structurally. Linux and Kubernetes are examples of open source software.

Open source software fosters collaboration by sharing code and encouraging modifications and improvements. Instead of charging for the software program, software developers find it more lucrative to charge for service around developing and maintaining these open source projects.

Benefits from Open Source Software

Developing software in an open source environment means a willingness to share and collaborate in a transparent way.

*   Control – To a developer, open source means an individual can contribute to the direction the code takes. This open participation means coders who participate the most have more influence over the direction of the code.
*   Training – The ability to copy code and make your own changes in test environments act as invaluable hands-on training. This also fosters innovation as programmers can devise previously unthought-of functionality and code direction.
*   Security – In open source, software programs are considered more secure because they are open to peer review where errors can be spotted. Coders are encouraged to test code, find errors and develop fixes to bugs as long as they follow the process the network has in place.
*   Stability – Open source projects have a certain amount of code stability due to openness for public review. A publicly distributed source code is openly reviewed and can expose situations that may not have otherwise been tested.
*   Community – Open source inspires the community to get involved. When contributing to an open source project, you join a community of people that ultimately affects the software you are interested in.

The programming code for Bitcoin, Ethereum, Hyperledger and other blockchains is open source.

## Governance

The Oxford English Dictionary defines governance as “the action or fact of governing a nation, a person, an activity, one's desires, etc.; direction, rule; regulation.” A basic description of governance can be defined as a system by which behavior is directed. This direction is guided by a set of rules, and a mechanism to enforce these rules, which can take many forms from a dictator having complete control to a democratic governance model where the voice of the majority is recognized.

In an economics context, governance is defined as “the use of institutions, structures of authority and collaboration to allocate resources and coordinate the effort and activity in society or in the economy”.

On the other hand, from an IT perspective, governance is composed of the leadership and the set of structures and processes that guarantee that the IT of an organization provides support and extends the its strategy and objectives in a manner that is focused on achieving a better alignment between the business and IT. In other words, IT governance is a formal framework that provides a structure for organizations to ensure that technology investments support business objectives.

Blockchain governance can be regarded as the integration of norms and culture, the laws and the code, the people and the institutions that facilitate coordination and together determine a given organization.

Governance Models

Blockchain governance models reflect a democratic flavor due to the open source environment. Blockchains are composed of a community of users who work together to strengthen the system. The degree in which the majority rules can vary

*   Representative democracy – This type of governance has a few individuals, empowered by the group, to suggest new rules and guide future direction. The amount of authority the representative has is granted by the majority. The representatives selected reflect the views of the majority and are given authority to guide the community. The control comes from the community and representatives are presumed to act in the best interest of the governed. This type of governance is more efficient as only a few debate the issues and decide on the policy. Issues can occur when the majority opinion unevenly reflects the community, causing minority groups to be underserved. Also the assumption is that the representatives are acting on the best behalf of the group and not in their own best interests.
*   Direct democracy – All decisions regarding the governance of the group are voted on by the entire community. In this form of governance model, every vote counts and people have more control over the quality of policies. In this model, it is best to have an educated community where everyone is willing to participate for the good of the entire community.

Every blockchain ecosystem needs some kind of governance model in place. As discussed in “Bitcoin and Blockchain Governance: What it is and Why it Matters” article by Evan Karnoupakis, in traditional systems, laws are made and then enforced. In blockchain, when participants (miners, developers, and users) in the network are interacting, they are acting in a way that is best for the group. Being able to build a governance structure in a decentralized system has proven to be very difficult. 

Most governance structure in the blockchain ecosystem are looking to achieve the following goals:

*   Protocol changes and technical upgrades
*   Critical bug and vulnerability fixes
*   Using pooled funds for research and development

These goals can be achieved through different methods of governance. When designing a blockchain, there are 2 major choices:

*   On-chain governance – On-chain governance is a mechanism that enables a decentralized community to update a blockchain by voting directly on-chain. In the On-chain governance, the rules for instituting changes are encoded into the blockchain protocol. This means that any decision being made is automatically translated into the code. On-chain governance for a blockchain ecosystem typically takes place on Proof-of-Stake blockchains in the form of a vote, and you usually must hold the blockchain’s native coin to participate in its governance. The weight of your vote is determined by the number of coins you hold. The stakeholders in on-chain governance typically include users, developers, and transaction validators.

For example, if you hold MakerDAO’s MKR token, you can vote on governance actions proposed by the Maker community through its decentralized autonomous organization (DAO). These include things like adding a new type of collateral to MakerDAO’s debt system. Each proposal is coded into a smart contract and when it receives the required amount of votes, changes to the blockchain are executed immediately.

On-chain governance widens the group of people who participate in blockchain governance processes, limits the threat of chain splits and forks, and allows individual users to register their input. Some on-chain governance systems do retain off-chain characteristics. For example, though proposals may be encoded in smart contracts, they are often still discussed in forums, blog posts, and on Twitter before they are voted upon.

On-chain processes have been criticized as plutocratic because the amount of coins you hold determines the weight of your vote, which means whales often have disproportionate influence on the system. And critics worry that coin-rich whales will vote to make changes to the blockchain that are most profitable for them, instead of voting for what is best for the long-term health of the blockchain ecosystem. Likewise, despite having the option to vote, many token holders never participate in governance.

*   Off-chain governance – Off-chain governance can be seen as decision making that first takes place on a social level and is later actively encoded into the protocol by the developers. For example, Bitcoin developers share their improvement proposals through a mailing list, which are then reviewed.

Both Bitcoin and Ethereum utilize off-chain governance processes, as do most other Proof-of-Work blockchain systems. The core stakeholders of these blockchains are users, node operators, developers, and miners, and they all exert checks and balances on each other. Off-chain governance for a blockchain ecosystem functions when all stakeholders agree and make all relevant updates and implementations in unison. If consensus cannot be reached, the network is liable to fork, or split into two chains running different versions of the software, and the chain with the most transactional hashing power is considered to be the successor to the original chain.

With an off-chain model, protocol development takes place at conferences, on online forums, and through mailing lists, among other means. You must use these channels to get involved. A brief examination of the history of Bitcoin’s block size debate reveals the informal, off-chain processes that determine whether changes are made and the complications that sometimes accompany those processes. The block size debate was a dispute within the Bitcoin community about whether the size of Bitcoin blocks should be increased to accommodate more transactions so as to scale Bitcoin’s transaction processing capacity. Throughout the off-chain process, the block size debate raged and ranged across a variety of off-chain platforms and events. Over several years, agreements were inked and broken, multiple conferences were called to host in-person discussions, and blockchain forks were threatened and eventually executed. Bitcoin Cash is the most notable example of a digital asset that lost consensus with the main Bitcoin blockchain, and now exists as a separate and distinct blockchain with nearly identical code. The protracted and inefficient debate over Bitcoin scaling reveals two downsides to off-chain governance: that it can be difficult to register your input as an individual user and that changes can take a long time to implement.

Blockchain governance strategies

Several blockchain governance strategies have been proposed and implemented for different blockchains. Let’s review some of those strategies sorted from the fewest to the most members directly involved in the decision, as discussed in “Blockchain Governance in a Nutshell” article by Demiro Massessi:

*   Benevolent dictator for life – The original creator or the lead developer of the blockchain platform has the final say on all decisions. 
*   Core development team – A team of the most active developers decide what functionality should or should not be included in the blockchain platform. This strategy is commonly used in the open source programming projects, where the users are able to offer or request features, but the developers have the final say on what should or should not be included in the final release.
*   Open governance – The team making governance decisions for the blockchain is chosen by the users of the blockchain (representative democracy). Some blockchains use the open governance method of handling governance. 
*   On-chain governance – The rules for how the blockchain operates are stored on-chain in smart contracts with built-in capability and procedures for modifications (direct democracy). A blockchain-specific governance strategy in on-chain governance. In this form of blockchain governance, the rules describing how the blockchain should operate are stored in the blockchain itself. These regulations typically are implemented as smart contracts on the blockchain with built-in methods for users to modify the rules based upon their needs and the needs of the blockchain.

Bitcoin Governance

Bitcoin uses Proof-of-Work (PoW) consensus model, which governs the operations of its blockchain. But what happens when changes need to be made, and how do they get implemented? The Bitcoin community consists of three main players: developers, miners, and users. None of these participants have the ability to make emergency decisions when unexpected situations occur. Bitcoin uses an off-chain governance model where the decisions are balanced by the developers, miners, and users. The developers must write the code to change the blockchain. Without the consent of the miners and users, the developers have no way of enforcing the change. Miners and users must choose to adopt the new software changes.

When a change to the Bitcoin protocol is needed, developers will share the proposed change with other protocol developers. The improvement sharing could be in the form of an email to the bitcoin-dev mailing list, a formal white paper, and/or a Bitcoin Improvement Protocol (BIP). Code is written and tested that will enact the change. If developers approve the proposals and the resulting code, the proposal is put to a vote on the blockchain and the miners decide if the proposal is implemented. This occurs through a hard or soft fork.

This system is not without faults, as can be seen with the SegWit Improvement protocol which alters block size. The vision surrounding blockchain decentralization. By implementing the SegWit changes, a change in how the Bitcoin blockchain protocol operates, a central authority was responsible for enacting the change. To many in the community this decision went against the fundamental tenets of blockchain decentralized philosophy. As a result, the Bitcoin network split into two separate blockchains

*   Bitcoin (BTC) – The original Bitcoin blockchain
*   Bitcoin Classic (BCH)- The proposed hard fork from Bitcoin Core that proposed increasing the maximum size of transaction blocks. Despite the early successes, Bitcoin Classic has failed to be widely adopted by the bitcoin community and did not eventually materialize.

Ethereum Governance

Ethereum is based on the Bitcoin code, but includes a logic engine to execute smart contracts. By connecting computers using the Ethereum blockchain network, the computing power is aggregated creating the Ethereum Virtual Machine (EVM). Ethereum is not only a functioning blockchain with smart contract capabilities, but a platform for new blockchains to be built upon. 

Like Bitcoin, Ethreum’s three main players (developers, miners, and users) must update the code to improve on its functionality. Ethereum Improvement Proposals (EIP) are standards specifying potential new features for Ethereum blockchain. EIPs contain technical specifications for the proposed changes and act as the “source of truth” for the community. The Ethereum Request for Comment, ERC-20 introduced the standards for issuing utility tokens on blockchain based on Ethereum protocols. The Beacon Chain introduced the Proof-of-Stake (PoS) consensus model and the concept of ‘sharding’ – running parallel side chains to alleviate congestion of the network. The Berling Hard Fork and the London Fork are improvements to stabilize the fees paid to the miners, such that it does not fluctuate with the price of Ether. 

Ethereum uses the benevolent dictator for life mode of blockchain governance. While input from users and the development team is welcome for Ethereum, the final authority on decisions regarding Ethereum rest on its founder, Vitalik Buterin.

Hyperledger Governance

Hyperledger was introduced as an open source blockchain project sanctioned by Linux Foundation. Spearheaded by Brian Behlendorf, its mission is to provide the community with the tools and education to foster distributed ledger technology on an enterprise level. Hyperledger frameworks use an Open Governance model to make technical decisions regarding the Hyperledger environment. The Hyperledger Technical Steering Committee (TSC) is the final authority for technical decisions in Hyperledger. Each year, the member of this committee are selected from Hyperledger’s active contributors and maintainers, who submit themselves as potential candidates for the fifteen slots, and these slots are filled based on voting by the same group of contributors and maintainers. This model is designed to allow those with an active role in the Hyperledger development community to have a say in how Hyperledger is governed.

Corda Governance

Corda is an open source blockchain project designed for business. Developed by R3, an enterprise blockchain software firm, in collaboration with over 200 technology and industry partners. The Corda platform was developed in 2017.

Corda uses and Open Governance model to make technical decisions regarding its roadmap. The Corda Governing Body is selected to represent the interests of all users in Corda network.

## Identity of the Blockchain

Here we are going to discuss identity on the blockchain. Let’s start by understanding why we even need to have an identity on the blockchain.

Centralized systems can be coerced by other forms of authority to shut down their network.

Let’s take Napster for example. Napster had a decentralized network architecture, but they maintained a centralized authority. Therefore, the central authority could be attacked and, by taking out the central authority, could effectively control Napster. This is because Napster relied on that mix of centralized control over a decentralized network. This impacted identity because you need an identity to control.

Torrents on the other hand do not operate in the same fashion. They provide a decentralized network with a decentralized authority. This allows the nodes to manage identity differently. It is also the reason why torrents are still being used today, in spite of the entertainment industry’s best effort to stop it. Torrents remove the central authority.

So, this brings the question “Why didn’t peer-to-peer networks like torrents attain the same level of acclaim as blockchain?” Because there is no guarantee that the nodes would do the right thing. Nobody could guarantee that the nodes would cooperate with each other.

This leads to an extremely important question. How do you incentivize the nodes in the network to follow the rules? In a torrent system, anyone could download and share a file, but there is no real incentive for someone to be a good actor on the network. For example, what happens when people on the torrent network stop sharing a movie that occupies space on their computers? Now let’s replace ‘movie’ in torrent network with ‘money’ in bank network. In such a scenario, the transactions would never be processed reliably. Further, because of anonymity, you would not be able to reward or punish the actors.

Blockchain solved this problem using crypto economics, by incentivizing miners to create and maintain a decentralized self-contained network. This differed from earlier peer-to-peer networks as it offered economic incentives to the nodes that followed the rules, in the form of cryptocurrency. The nodes were also punished for tampering with the network or a past transaction or submitting a false transaction. This is why all public blockchains can operate without an authority. It is also the reason why cryptocurrency is mandatory for a public blockchain, and not for a private blockchain. Because you need a way to incentivize the actors on the network.

How these rewards and punishments work on the blockchain, and how the blockchain can determine what is valid and what is invalid without a central authority?

On the blockchain, identity is important. You have to be able to prove that your assets actually belong to you. Different blockchain use different systems for tracking identity and identity information, but most are based on the principles of public key cryptography.

The security of a public key cryptography is based on hard math problems, wherein it is easy for someone to calculate it, but hard for someone to reverse that calculation. For example in multiplication, you can multiple any two numbers and get the right answer. Factoring on the other hand is hard. The best way to factor a large number is to try every possible factor until you find the right one. Some public key cryptography algorithms are designed so that breaking the algorithm requires factoring very large, usually prime numbers. Similarly, another hard math problem used in public key cryptography is based on exponents and logarithms. While exponents are easy since its essentially multiplication, logarithms are hard since they are essentially factoring. Most public key algorithms that use exponents use a type called modular exponents, which means that when they are done calculating the exponent, they divide the result by a publicly known value called the modulus and keep only the remainder.

RSA is a commonly known public key cryptography algorithm. It is based on exponents and logarithms. RSA uses the power law of exponents, meaning that if you take a number and raise that number to a power, and then raise that result to another power, then you will get the same result as if you simply multiply the two exponents together and then raise the base to the result. An RSA user chooses two exponents such that any number raised to the product of the two exponents in a given modulus produces the original number. One of these is called a public key and is distributed freely, while the other is called a private key and is intended to be kept secret. If someone wants to send a private message to the user, they convert it to an integer using a publicly-known method. They raise it to the power of the user’s public exponent, and they send the result to the user. The user raises the received value to their private exponent producing the original message. RSA is secure because an attacker must be able to calculate a logarithm to determine the secret message. Since this takes guessing every possible value until the correct one is found, RSA is designed to make the number of potential value so large that finding the correct one is nearly close to impossible.

These algorithms are designed such that an authorized user only has to do the ‘easy calculations’, while the attacker has to do the ‘hard calculations’ and the algorithm is designed to make solving these ‘hard calculations’ virtually impossible.

Public key cryptography is how identity is managed on the blockchain. A user’s address on the blockchain is their public key. This has several useful properties. Users do not need to reveal their identity on the blockchain, but they can positively identify themselves, since determining their private key requires solving a ‘hard problem’.

Anyone can send a user an encrypted message, since they have easy access to their public key. Users can verify the validity of these transactions using their digital signatures. In RSA, anyone can send an encrypted message to a user by converting it to a number, raising it to their public exponent, and sending the result. The user’s public and private key are designed such that the users can retrieve the original message by raising the received message to their private component. RSA digital signature involves the opposite process. Users writes a message and raises a condensed form of this message to the power of their private exponent to create a signature, and then they publish this signature. Their public key and the message are both published together. Anyone can validate the signature using a simple three step process – condense the attached message using the same method as the message writer, raising the attached signature to the user’s public key, and verifying that the results of the previous two steps are identical.

Digital signature works for the same reason that encryption works in RSA. An attacker needs to know the user’s private key to perform either operation, and the algorithms are designed to make that process nearly close to impossible. 

This means that identity on the blockchain boils down to the possession of a user’s private key. So its very important to keep this private key safe. 

In Ethereum, a user’s identity is managed using a public key or address, the user can use the corresponding private key to sign transactions and read encrypted messages that are sent to them.

In Hyperledger and Corda, identity is encoded in x.509 certificates, which includes the user’s public key. In Corda, certificates can either be public, which means that they are published to the blockchain, or confidential, meaning that they are only shared with the parties that the owner performs transactions with.

## Anonymity in Blockchain

Anonymity in blockchain is a crucial part of its success in some applications. If individuals or organizations are performing transactions on blockchain, they may not wish this to be public. Different blockchains have different levels of anonymity and privacy built into the protocol. 

As discussed earlier, public key cryptography maintains identity on the blockchain, by using a pair of public and private keys to make encryption and digital signatures possible.

At this point, we need to take a look at the relationship between a user’s keys and their actual identity. The first thing to note is that there is nothing about a public key that ties to its corresponding private key. Since private keys are secret, it cannot be possible for someone to determine a private key from a public key, whereas you can calculate a public key from a private key. The other thing to keep in mind is that private keys are just numbers and cannot be tied to users actual identity. Identity on blockchain is just possession of the relevant private key, and even if someone guesses or steals a private key, they cannot learn its owner’s actual identity from the private key directly. 

Hence you cannot tie public keys to private keys or private keys to real-world identities, which means that blockchain users have a limited amount of built-in privacy. 

However, every transaction on blockchain is public and stored there forever. This means that a lot of information about the users’ identity could be learned through studying the data stored on the blockchain to obtain the metadata. Based on the repeated transactions to places like a restaurant or a coffee shop, someone could get an idea of where an individual lives and their habits. For businesses, repeated transactions may indicate business relationships that may lead to a loss of competitive advantage if leaked. 

On basic blockchain, anonymity goes only so far. The limited level of anonymity and privacy protections available on the original blockchain have inspired enhancements that increase privacy, while still allowing transactions to be verified and validated publicly on the blockchain. 

Some of the mechanisms developed and implemented to increase privacy protections are:

*   Zero knowledge proofs – They use cryptographic algorithms to allow a user to prove knowledge of a secret without revealing the actual secret. The validator proves the knowledge of the secret without actually revealing it. A common example includes a colorblind person and two identical object except for color. The colorblind person shows one object to the validator, conceals both objects, and the shows the one to the validator again. The validator then verifies whether or not it is the same object, without revealing the color of either object. 
*   Stealth approach – Stealth addresses involve using one-time addresses to perform transactions on the blockchain. A stealth address is just a one-time address that makes it impossible to link a transaction to a known account. What it does is prevents the data mining attacks on privacy of users.
*   Ring signatures – Blockchain transactions are digitally signed. With ring signatures, all that can be determined from a transaction is that a member of the group signed it, but not the actual member.
*   CoinJoin – The ability to see who is performing the transactions with whom is dangerous to user privacy and anonymity. CoinJoin mixes several transactions together such that it is difficult to pair senders with recipients.
*   Confidential transactions – Confidential transactions take advantage of homomorphic encryption, which makes it possible to perform mathematical operations on encrypted data. This means that the data contained in a transaction can be hidden from the public, while still allowing the network to validate the transaction.

Specific Anonymity Implementations

*   Ethereum – Ethereum is working on improving the zero-knowledge proofs, mixing and DAPPS (applications developed to improve anonymity)  to strengthen blockchain privacy. Also ConsesSys, the enterprise solution builder for Ethereum introduced QUORUM, a fork of the Ethereum blockchain which enables users to benefit from the public Ethereum blockchain while enjoying features from a private network. Developed by JP Morgan, it is a permissioned implementation.
*   Hyperledger 
    *   Channels – Subsections of the blockchain that make the transactions visible only to the members.
    *   Private transactions – Hashes of private data are stored to publicly verify it on the blockchain.
    *   Zero-knowledge Proof – One can demonstrate the knowledge of a secret without revealing the secret itself.
*   Hyperledger Besu – Besu is an Ethereum client that runs on the Ethereum public network, private networks, and test networks such as Rinkeby, Ropsten, and Gorli. Hyperledger Besu includes several consensus algorithms including PoW, PoA, and IBFT, and has comprehensive ‘permissioning’ schemes designed specifically for users in a consortium environment.
*   Corda – Party on the Corda network can be represented in one of the two ways: Party – A public key name and; Anonymous party – Only a public key. 

 

 

 

# Blockchain in Real World

In this chapter, we will discuss the real-world problems blockchain can solve. We will discuss the concept of immutability and how the append only blockchain brings new trust in shared information. Next, we will see how smart contracts bring autonomy to the systems that previously required human interaction. We will discuss how blockchain solves the double-spending issue. Next we will provide a brief insight on popular cryptocurrencies and the new business trends made possible by blockchain. Finally, we will discuss the emerging world of non-fungible tokens (NFTs) and how they enable owning unique rights to everything from music, sports, collectables and even photographs. 

## How Blockchain solves real-world problems

Immutability

Immutability simply refers to the permanence of data. Anything we call ‘immutable’ is permanent. One of the benefits of blockchain is immutability. The data recorded on a blockchain system can never be altered, edited, changed, or deleted once it has been recorded. As this data is stored in multiple locations, changing or removing a copy of this data in a single place, or a limited number of places poses no threats. 

Blockchain goes further than this. In addition to recording data points, blockchain also has the capacity to record who endorses or agrees with those facts. Let’s think of this as a difference between a piece of paper and a contract. A piece of paper can contain any data, true or false. A signed contract becomes more than that because the signatures represent who agreed with the facts recorded on the paper at the time of signing. Blockchain provides a digital implementation of this process, and can be an immeasurably valuable tool when you need to capture not only what happened, but who was involved as well. Imagine the new opportunities that arise when organizations can safely and securely share there most critical data with one another, with the trust that the data they are seeing has not been compromised or altered.

*   Traditional Database Immutability – The very nature of centrally operated databases can’t be completely immutable. A centrally run database can embed things into it with features that mention immutability. But is there is a central authority, they have the ability to override that feature. Just like immutability has been around for many years, just like the majority of the tech used via blockchain; it is the combination of these that makes it unique. 
*   Blockchain Immutability – Let’s review the aspects of the public blockchain that improve the chances of it being immutable. There are many different variables, but the main one is consensus. In a blockchain, it refers to the logs of transactions which are created by consensus among the blockchain’s participants. The basic notion is that once a blockchain transaction has received a sufficient level of validation and posted on the blockchain, it can almost never be replaces, reversed, or edited.

For example, if all the nodes within the Bitcoin blockchain network are working to solve a really hard math problem by running multiple computers simultaneously, the chances of anyone overriding that are slim to zero. But if someone wanted to undermine the immutability of the Bitcoin blockchain, here is how they would do it:

1.  Install more mining capacity than the rest of the network put together, creating a ‘51% attack’.
2.  Instead of openly participating in the mining process, they would mine their own ‘secret branch’, containing whichever transaction they approve and censoring the rest.
3.  When the desired amount of time has passed, they would anonymously broadcast their secret branch to the network.

Since the attacker has more mining power than the rest of the network, their branch will contain more Proof-of-Work (PoW) than the rest of the network. Every Bitcoin node will therefore switch over since the rules of Bitcoin state that the more difficult branch wins. Any previously confirmed transactions not in the secret branch will be reversed and the Bitcoin they spent could be sent elsewhere. The computing power required to achieve this is enormous and probably only theoretical, but it is important to consider.

One other less technical and malicious example would be from the Ethereum hard fork that directly happened after the DAO hack. In this example, the majority of the Ethereum nodes in the network decided to update the software preventing those hackers from withdrawing the cryptocurrency earned (stolen). This update could not be enforced, since every Ethereum user controls their own computer. Nonetheless, it was publicly supported by Vitalik Buterin, Ethereum’s founder, as well as many other community leaders. As a result, most users compiled, and the blockchain with the new rules kept the name “Ethereum”. A minority disagreed with the change and continued the blockchain according to its original rules, earning the title “Ethereum Classic”.

Transparency

Anything that is see-through is transparent. Just like immutability, transparency comes on a spectrum. Certain things are more transparent than others. In the context of technology, this can be seen as a way of operating that is easy for others to see the actions being performed. For example, in open source projects, all the source code is available for everyone.

In a traditional database, a client can perform four functions on data:

*   Create
*   Read
*   Update
*   Delete

There is usually an administrator, the authority giver who allows certain known participants in the database to do more than read/create; it allows them to update and/or delete. Due to the fact that administrator is controlling who has access and who doesn’t, it is easier to track these changes and prevent malicious actors from tampering. In the public blockchain, this isn’t necessarily the case.

Within blockchain, every full node on the network it its own administrator, where it can create, read; this is also known as read/write access (example append only). These nodes only add more data over time in the form of blocks, but all previous data is permanently stored and cannot be altered.

*   Read – Query (e.g. – search) and retrieve data from blockchain
*   Write – Add more data onto the blockchain

As explained in the “Blockchain versus Traditional Databases” article by Shaan Ray, ‘if the blockchain has recorded that my Bitcoin wallet has 1 million BTC, that figure is permanently store in blockchain. When I spend 200,000 BTC, that transaction is recorded onto the blockchain, bringing my balance to 800,000 BTC. However, since the blockchain can only be appended, my pre-transaction balance of 1 million BTC also remains on the blockchain permanently, for those who care to look. This is why the blockchain if often referred to as an immutable and a distributed ledger.’

Autonomy

Autonomy is defined as independence or freedom, the ability to make your own decisions without being controlled by anyone else. This freedom can be at macro level (country) or at microlevel (person).

Blockchain enables autonomy from intermediaries via automated smart contracts. 

In the traditional world of doing any transaction with another party, there tends to be a lot of administrative paper work, with third parties intervening every step. Most of this paperwork is actually not required and wastes a lot of time and effort which could be spent elsewhere. Depending on how complex a transaction is between two parties, designated specialists can design more efficient process. Multiple parties are involved in this process, from contract drafter, signatories, to regulators. If a dispute over the contract occurs, many parties can be involved, including the courts. This complexity can be seen within many sectors and industries.

Autonomy in blockchain can be seen from many different angles. We are going to focus solely on smart contract, due to the amount of autonomy they provide for everyone involved in the contract. The concept of smart contracts has been around for many years and was first proposed by Nick Szabo, who coined this term in 1994. 

Smart Contracts 

The most simplified explanation of smart contracts is – “IF THEN ELSE” statement, which means IF X happens, THEN do Y, ELSE do Z.

If this concept is applied to two or more parties, all interacting on a mutually agreed upon contract that executes based on their actions (or non-actions). An example of smart contract can be “if an event happens before the end of this year, then you pay me, else I pay you”.

The first generation of blockchain platforms “Blockchain 1.0” network, were capable of capturing and recording data, but not acting upon it. Bitcoin enabled capturing and recording the transfer of Bitcoins from one owner to the next. At that time, nobody envisioned blockchain as a platform on top of which applications and solutions could be built. The release of Ethereum in 2015 changed this concept. “Blockchain 2.0” was born, and now blockchain networks could not only capture data, but they could act upon it as well. All of this was made possible by the introduction of “Smart Contracts”, a computer code deployed to a blockchain network. Users can transact with the smart contract just as they would with another user, except that the rules of transacting with a smart contract are defined in the code and are used to process that transaction. This enables blockchain to manage and automate processes, and record their results on a permanent, immutable, secure ledger shared with all relevant parties. 

Let’s take an example of a used car. Alice lists her car for sale and offers a guarantee to any buyer that the car will be issue-free for next 10,000 miles. Bob wants to purchase this car and makes an offer of $5,000. Alice and Bob agree that Alice will take half of the purchase price now ($2,500) and the other half if the car has no major issue in the first 10,000 miles of Bob’s ownership. A smart contract could be created Alice and Bob. This smart contract would hold the remaining $2,500 of the purchase price in an escrow account, and if Bob had an issue with the car, he would report it to the smart contract. After 10,000 miles of Bob’s ownership, the smart contract would determine how much of the remaining fund is due to Alice and how much should be returned to Bob, using the rules Alice and Bob initially agreed upon. All the details about the transaction would be recorded on a permanent, decentralized ledger which could be used at any point in the future to answer any questions about the transaction between Alice and Bob.

Currently, the ‘smart’ contracts aren’t generally very smart. This is due to the simple explanation that because these contracts are “if, then, else” statements, they can vary in complexity based on how they are stacked. Currently, they cannot make decisions without human intervention of AI. Companies are emerging as reliable Oracles (a reliable source of information) that filter in real world facts to the blockchain, and blockchain makes that information immutable. 

Anyone can create their own smart contracts without a central authority giving the right to do so. These contracts are executed without too much human intervention, and they are stored on blockchain technology which provides a sense of permanence. These are three of the main attributes that can bring more autonomy to exchanging information between parties. Setting up a pre-agreed upon contract that is coded into a blockchain and executes automatically when certain actions are taken is one step in the direction of not only improving our autonomy as individuals or companies, bust shifting resources that are redundant, towards more impactful work.

Multi-Party Transactions

In traditional centralized ledger systems, accuracy is dependent on intermediaries who can change details of the centralized ledger. Data derived from the ledger can be siloed and misused. Distributed decentralized ledgers are not dependent on intermediaries who can manipulate the data. The data is secure and tamper resistant.

In the current ecosystem of transactions, there is always a third party to assist in connecting the sender to the receiver. This has always been the most efficient way to move something from point A to point B. But with a third party making the connection comes the need to trust that they will get whatever is being sent in an efficient, economical, and effective way. This trust is open to human and process error. Blockchain can enable removing the middlemen from a number of processes. There is a long list of examples for middlemen currently being removed, such as:

*   Energy distributors
*   Payment networks (Visa and Mastercard)
*   Over the top platforms and content distributors (YouTube, Facebook, Instagram, etc.)
*   Central exchanges (NYSE, NASDAQ, NSE, LSE, etc.)
*   Cloud database providers (AWS, Azure, etc.)

One example is cross-border payments. In sending money from one country to another, the transactions end up stopping off at 7 – 10 different checkpoint banks (buyers – buyer’s bank – country ‘A’ federal bank – country ‘A’ correspondent bank – country ‘B’ correspondent bank – country ‘B’ federal bank – seller’s bank – seller). This constant stopping delays the flow of money, makes its movement more expensive (as each bank takes a small fee), and less reliable (increase in malicious attack due to number of checkpoints). This type of transaction is heavily reliant upon third parties to facilitate the movement of money. Now, if we replace this ecosystem with blockchain, the trust is built via the consensus mechanism. This would incentivize all the participants to help secure and validate the transaction throughout the network. With this built-in “trustless” trust, we can remove the multiple intermediaries in this transaction that provide no additional value, thereby speeding up the process, optimizing the cost of transactions, and making the process more efficient.

Double Spend

Bitcoin was not the first attempt to create a digital currency, but the first which was able to solve a long-standing problem of “double spend”. A double spending attack is an attack where a cryptocurrency can be used more than once, by altering the blockchain network and inserting a special one that allows the user to reacquire a cryptocurrency. 

For example, Alice owes a debt of $5 to both Bob and Carol. Alice’s total debt is $10. Let’s assume that Alice only has $5 currently. If Alice’s transactions were recorded on two separate ledgers, it is possible that one ledger would show she paid $5 to Bob, while the second would show that she paid $5 to Carol. It would be impossible to tell who actually got paid. This is the double spend problem. Hence, any financial ledger must prevent Alice from spending her $5 more than once.

Digital assets are particularly more vulnerable to the double spend problem they are designed to be easy to copy and distribute. For example, you took a picture from your phone, it is easy to post one copy to Facebook, another to Instagram, ‘wattsapp’ a copy to your friends, and email a copy to your parents. Hence, we see that digital assets are easy to copy and distribute. However, a digital currency should not be easy to copy and distribute. It was overcoming this technical challenge that led to many failed attempts before Bitcoin like Digicash, Hashcash, etc.

Bitcoin Technology solves these problems though two inherent concepts

1.  Blockchain network enabled the transactions to be validated and broadcasted in the entire network using readily available software applications. When a transaction occurred, the network nodes validated these transactions, added them to their copy of the ledger, and then broadcasted these ledger additions to other nodes. Once these transactions are accepted in the network, they became a block. 
2.  Using the Proof-of-Work protocol, these blocks were added to the blockchain, and quickly published to all nodes, without requiring central oversight. This enables the network to determine when a particular bitcoin was spent, which is needed to prevent double-spending. 

These two concepts enable anyone with access to internet join the Bitcoin network, verify and audit transaction history on their own, as well as create Bitcoins through mining via Proof-of-Work.

## Cryptocurrencies

A cryptocurrency is a tradable digital asset or digital form of money, built on a blockchain. 

A cryptocurrency is a completely digital, decentralized currency that is built using the principles of computer science, cryptography, and economics. Cryptocurrencies does not exist in physical form, are not backed by or convertible into a commodity, and are typically not issued by a central authority, using decentralized control as opposed to central bank digital currency. Cryptocurrencies use encryption to authenticate and protect transactions, hence their name.

Bitcoin is considered the first and the most widely used cryptocurrency. Bitcoin can be defined as “a decentralized digital currency, which can be sent from one user to another on a peer-to-peer network, without the need for intermediaries or banking channel.” Bitcoin transactions are verified by network nodes through cryptography and recorded in blockchain, which records bitcoin transactions, and stores their history in an append-only ledger format, such that data can be added to the ledger, but cannot be deleted. It is implemented as a chain of blocks, each block containing a hash of the previous block up to the genesis block in the chain. 

How Bitcoin aims to replace banks?

In order to understand how Bitcoin serves as a substitute for the banks, we first need to understand how the banks function. 

The banks manage their user accounts and secure their money, such that only they can make transactions through their accounts. The banks does that by verifying and validating the identity of its users prior to any transactions. Thereafter the banks conduct transactions (deposits / transfers / withdrawals) on behalf of their users and record these transactions. The banks update their users account balance whenever they make a new transaction, and let them see the history of their activity and transactions. The users trust their banks to honestly record their activities, as they fall under their country economic and financial regulations.

However, what if the users can no longer trust banks or their governments, and start looking for alternatives. Here Bitcoin comes into picture. 

Bitcoin enable users to be completely anonymous. In Bitcoin, each user can create their own identity / avatar. Since the Bitcoin identity is completely discerned from their real world identity, it enables the users a high degree of privacy. Now, once the users create their identity and make transactions, these transactions can be made directly on the peer-to-peer network without the need of involving any central entity like the banks. Also as the transactions are recorded by the network via proof-of-work concept, the users can be confident that these transactions are honestly recorded. Thus the users can confidently send funds to one another knowing that the transaction will be validated by the entire network without the presence of a 3rd party. Finally, since the ledger can only be appended, the users can be confident that their existing records cannot be altered. To store the transaction information, each Bitcoin user have their individual copy of the ledger. The decentralized nature of Bitcoin ensures the integrity of data as well as prevent the risk of single point of failure. In the event that a particular node is hacked, since everyone is a record keeper, the other nodes can still ensure the integrity of data and keep the network running.

## Decentralized Finance (DeFI)

Decentralized Finance (DeFI) refers to a system of financial software that enables financial products to be made available to the public on decentralized blockchains. DeFi offers financial instruments without relying on intermediaries such as brokerages, exchanges, or banks by using smart contracts on a blockchain. DeFi platforms allow people to lend or borrow funds from others, speculate on price movements on assets using derivatives, trade cryptocurrencies, insure against risks, and earn interest in savings-like accounts.

Bitcoin in many ways was the first DeFi application. Bitcoin lets you really own and control value and send it anywhere around the world. It does this by providing a way for a large number of people, who don't trust each other, to agree on a ledger of accounts without the need for a trusted intermediary. Bitcoin's rules, like its scarcity and its openness, are written into the DeFI technology. DeFi takes the basic premise of Bitcoin “digital money” and expands on it, creating an entire digital alternative to Wall Street, but without all the associated costs (example – office towers, trading floors, banker salaries). This has the potential to create more open, free, and fair financial markets that are accessible to anyone with an internet connection.

Benefits of DeFI

DeFI leverages key principles of the Ethereum blockchain to increase financial security and transparency, unlock liquidity and growth opportunities, and support an integrated and standardized economic system.

 

*   Programmability – Highly programmable smart contracts automate execution and enable the creation of new financial instruments and digital assets.
*   Immutability – Tamper-proof data coordination across a blockchain’s decentralized architecture increases security and auditability.
*   Interoperability – Ethereum’s composable software stack ensures that DeFi protocols and applications are built to integrate and complement one another. With DeFi, developers and product teams have the flexibility to build on top of existing protocols, customize interfaces, and integrate third-party applications. For this reason, people often call DeFi protocols “money legos.”
*   Transparency – On the public Ethereum blockchain, every transaction is broadcast to and verified by other users on the network. This level of transparency around transaction data not only allows for rich data analysis but also ensures that network activity is available to any user. Ethereum and the DeFi protocols running on it are also built with open source code that is available for anyone to view, audit, and build upon.
*   Permissionless – Unlike traditional finance, DeFi is defined by its open, permissionless access: anyone with a crypto wallet and an Internet connection, regardless of their geography and often without any minimum amount of funds required, can access DeFi applications built on Ethereum.
*   Self Custody - By using Web3.0 wallets like MetaMask to interact with permissionless financial applications and protocols, DeFi market participants always keep custody of their assets and control of their personal data.

DeFI Use Cases

Users typically engage with DeFi via software called dapps (“decentralized apps”), most of which currently run on the Ethereum blockchain. Unlike a conventional bank, there is no application to fill out or account to open. 

Here are some of the ways dapps and DeFI protocols are already being used:

*   Traditional financial transactions – Anything from payments, trading securities and insurance, to lending and borrowing are already happening with DeFi.
*   Decentralized exchanges (DEXs) – Right now, most cryptocurrency investors use centralized exchanges like Coinbase or Gemini. DEXs facilitate peer-to-peer financial transactions and let users retain control over their money.
*   E-wallets – DeFi developers are creating digital wallets that can operate independently of the largest cryptocurrency exchanges and give investors access to everything from cryptocurrency to blockchain-based games.
*   Yield harvesting – Dubbed the “rocket fuel” of crypto, DeFi makes it possible for speculative investors to lend crypto and potentially reap big rewards when the proprietary coins DeFi borrowing platforms pay them for agreeing to the loan appreciate rapidly.
*   Flash loans – These are cryptocurrency loans that borrow and repay funds in the same transaction. Borrowers have the potential to make money by entering into a contract encoded on the Ethereum blockchain, executes a transaction and repay the loan instantly. If the transaction can’t be executed, or it’ll be at a loss, the funds automatically go back to the loaner. If you do make a profit, you can pocket it, minus any interest charges or fees. Think of flash loans as decentralized arbitrage.

Adoption of DeFi is powered by the omnipresent nature of blockchain. The moment a dapp is encoded on the blockchain, it’s globally available. 

Future of DeFI

From taking out the middleman to turning basketball clips into digital assets with monetary value, DeFi’s future looks bright. Investors will have more independence, which will allow them to deploy assets in creative ways that seem impossible today,

But for all its promise, DeFi has a long road ahead, especially when it comes to uptake by the public.

## Non-Fungible Tokens (NFTs)

You may have heard of the 24-year-old artist who made over $300,000 selling her art as Non-Fungible Tokens (NFTs) or Rob Gronkowski selling NFTs of his best Super Bowl moments. With this news hitting social media, it’s no surprise how NFTs have become the latest cryptocurrency sensation to go mainstream. 

A non-fungible token (NFT) is a non-interchangeable unit of data stored on a blockchain. Unlike cryptocurrencies, NFTs cannot be traded or exchanged because they are not identical to one another. NFTs are typically used to buy and sell digital items like digital files, digital media, digital art, collectibles, and virtual real estate. An NFT can be associated with a particular digital asset (video / photos / audio) or physical asset (physical file / physical object) and a license to use the asset for a specified purpose. This NFT (and, if applicable, the associated license to use, copy or display the underlying asset) can be traded and sold on digital markets. NFTs use a digital ledger to provide a public certificate of authenticity or proof of ownership, but do not restrict the sharing or copying of the underlying digital files or the re-creation of identical NFTs. 

NFTs function like cryptographic tokens, but, unlike cryptocurrencies such as Bitcoin or Ethereum, NFTs are not mutually interchangeable, hence not fungible. While all bitcoins are equal, each NFT may represent a different underlying asset and thus may have a different value.

NFTs are created when blockchains string records of cryptographic hash, a set of characters identifying a set of data, onto previous records therefore creating a chain of identifiable data blocks. This cryptographic transaction process ensures the authentication of each digital file by providing a digital signature that is used to track NFT ownership. However, data links that point to details such as where the art is stored can be affected by link rot. 

Ownership of an NFT does not inherently grant copyright or intellectual property rights to whatever digital asset the token represents. For example, while someone may sell an NFT representing their work, the buyer will not necessarily receive copyright privileges when ownership of the NFT is changed and so the original owner is allowed to create more NFTs of the same work. In such a sense, the NFT is merely a proof of ownership that is separate from a copyright.

NFTs have seen some use as a speculative investment, and they have drawn criticism with respect to the energy cost and carbon footprint associated with validating blockchain transactions as well as their frequent use in art scams.

How does and NFT work?

NFTs are typically held on the Ethereum blockchain, although other blockchains support them as well. An NFT is created, or “minted” from digital objects that represent both tangible and intangible items, including Art, GIFs, Videos and sports highlights, Collectibles, Virtual avatars and video game skins, Designer sneakers, and Music.

Even tweets count. Twitter co-founder Jack Dorsey sold his first ever tweet as an NFT for more than $2.9 million.

Essentially, NFTs are like physical collector’s items, only digital. So instead of getting an actual oil painting to hang on the wall, the buyer gets a digital file instead. They also get exclusive ownership rights, as NFTs can have only one owner at a time. NFTs’ unique data makes it easy to verify their ownership and transfer tokens between owners. The owner or creator can also store specific information inside them. For example, artists can sign their artwork by including their signature in an NFT’s metadata.

Uses of NFTs

*   Digital Files – NFTs have been used as a means of exchanging digital tokens that link to a digital file. Ownership of an NFT is often associated with a license to use the underlying digital asset, but generally does not confer copyright to the buyer. Some agreements only grant a license for personal, non-commercial use, while other licenses also allow commercial use of the underlying digital asset.
*   Digital art – Digital art is a common use case for NFTs. High-profile auctions of digital art as NFTs have received considerable public attention, with the work "Merge" by artist Pak being the most expensive NFT with a a price of $91.8 million dollars and Everydays: the First 5000 Days, by artist Mike Winkelmann, the second most expensive auction at $69.3 million in 2021.
*   Games – NFTs can be used to represent in-game assets, such as digital plots of land, which some commentators describe as being controlled "by the user" instead of the game developer by allowing assets to be traded on the 3rd party marketplaces without permission from the game developer. CryptoKitties was an early successful blockchain online game where players adopt and trade virtual cats. The monetization of NFTs within the game raised a $12.5 million investment, with some kitties selling for over $100,000 each. Following its success, CryptoKitties was added to the ERC-721 standard.

In December 2021, Ubisoft, the world’s leading gaming company, announced Ubisoft Quartz, “an NFT initiative which allows people to buy artificially scarce digital items using cryptocurrency". The announcement has raised significant criticism, with 96% dislike ratio over the YouTube announcement video, which has since been unlisted. Some Ubisoft developers have also raised their concern over the announcement.

*   Music – In February 2021, NFTs reportedly generated around $25 million within the music industry, with artists selling artwork and music as NFT tokens. On 28th February, 2021, electronic dance musician 3LAU sold a collection of 33 NFTs for a total of $11.7 million to commemorate the three-year anniversary of his Ultraviolet album. 
*   Film – In May 2018, 20th Century Fox partnered with Atom Tickets and released limited-edition Deadpool 2 digital posters to promote the film. They were available from OpenSea and the GFT exchange. In March 2021, Adam Benzine's 2015 documentary Claude Lanzmann: Spectres of the Shoah became the first motion picture and documentary film to be auctioned as an NFT. Other projects in the film industry using NFTs include the announcement that an exclusive NFT artwork collection will be released for Godzilla vs. Kong and director Kevin Smith announcing in April 2021 that his forthcoming horror movie Killroy Was Here would be released as an NFT. The 2021 film Zero Contact, directed by Rick Dugdale and starring Anthony Hopkins, was also released as an NFT. In November 2021, film director Quentin Tarantino released seven NFTs based on uncut scenes of Pulp Fiction. Miramax subsequently filed a lawsuit claiming that their film rights were violated.
*   Other associated files – Several internet memes have been associated with NFTs, which were minted and sold by their creators or by their subjects. For example, Doge wherein an image of a Shiba Inu dog whose NFT was sold for $4 million in June 2021.

Some virtual worlds, often marketed as metaverses, have incorporated NFTs as a means of trading virtual items and virtual real estate. The 2018 virtual world Decentraland is one example.

Tickets, for any type of event, have been suggested for sale as NFTs. Such proposals would enable event organizers or performers to garner royalties on resales.

*   Collectibles – In early 2020, the developer of CryptoKitties, Dapper Labs, released the beta version of NBA TopShot, a project to sell tokenized collectibles of NBA highlights. The project was built on top of Flow, a newer and more efficient blockchain compared to Ethereum. In 2019, Nike patented a system called CryptoKicks that would use NFTs to verify the authenticity of physical sneakers and give a virtual version of the shoe to the customer.
*   Speculation – NFTs representing certain digital collectables and artworks have seen considerable use as a speculative asset. 
*   Money laundering – NFTs, as with other blockchain securities and traditional art sales, can potentially be utilized for money laundering. 

How Is an NFT Different from Cryptocurrency?

NFT stands for non-fungible token. It’s generally built using the same kind of programming as cryptocurrency, like Bitcoin or Ethereum, but that’s where the similarity ends.

Cryptocurrencies are “fungible,” meaning they can be traded or exchanged for one another. They’re also equal in value. For example, one Bitcoin is always equal to another Bitcoin. Crypto’s fungibility makes it a trusted means of conducting transactions on the blockchain.

NFTs are different. Each has a digital signature that makes it impossible for NFTs to be exchanged for or equal to one another (hence, non-fungible). One NBA Top Shot clip, for example, is not equal to another NBA Top Shot clip, simply because they’re both NFTs.

History of NFTs

The first known NFT, Quantum, was created by Kevin McCoy and Anil Dash in May 2014, consisting of a video clip made by McCoy's wife Jennifer. McCoy registered the video on the Namecoin blockchain and sold it to Dash for $4, during a live presentation for the Seven on Seven conference at the New Museum in New York City. McCoy and Dash referred to the technology as "monetized graphics". A non-fungible, tradable blockchain marker was explicitly linked to a work of art, via on-chain metadata (enabled by Namecoin). This is in contrast to the multi-unit, fungible, metadata-less "colored coins" of other blockchains.

In October 2015, the first NFT project, Etheria, was launched and demonstrated at DEVCON 1 in London, Ethereum's first developer conference, three months after the launch of the Ethereum blockchain. Most of Etheria's 457 purchasable and tradable hexagonal tiles went unsold for more than five years until March 13, 2021, when renewed interest in NFTs sparked a buying frenzy. Within 24 hours, all tiles of the current version and a prior version, each hardcoded to 1 ETH ($0.43 at the time of launch), were sold for a total of $1.4 million.

The term "NFT" only gained currency with the ERC-721 standard, first proposed in 2017 via the Ethereum GitHub, following the launch of various NFT projects that year. These include Curio Cards, CryptoPunks and Decentraland platform. The 2017 online game CryptoKitties was monetized by selling tradable cat NFTs, and its success brought some public attention to NFTs.

The NFT market experienced rapid growth during 2020, with its value tripling to $250 million. In the early months of 2021, interest in NFTs increased after a number of high-profile sales and art auctions. In the first three months of 2021, more than $200 million were spent on NFTs.

What is the Future of NFTs? 

The future of any blockchain experiment is unknown. However, experts predict that NFTs are here to stay and will continue to grow beyond the art and gaming realm, especially if crypto enthusiasts and mainstream investors continue investing money. 

The growth of NFT can also be attributed to its features that can represent proof of ownership, provide social status, grant exclusive access, manage licensing, and certify authenticity. It allows you ownership of your products the way Bitcoin enables you to be your own banker. 

 

 

 

 

# Blockchain based cryptocurrency – Bitcoin

In this chapter, we will discuss Bitcoin and how it uses blockchain technology for distributed ledgers and to conduct transactions. We will start with Bitcoin history, and why it succeeded as a cryptocurrency. Then we will explore Bitcoin identity and its consensus protocol. We will gain insight of cryptographic hash function and merkle root, and how they make Bitcoin tamper-proof. We will learn about Bitcoin transaction process, and how Bitcoin codes are written via Bitcoin scripts. We will then gain an insight on Bitcoin users and their wallets. We will learn on the Bitcoin mining process. Finally, we will learn about the Bitcoin governance mechanisms.

## Bitcoin History

The origins of Bitcoin can be traced back to the Cypherpunk movement of the 1970s and 80s. In the 1970s people were living in an analog world, and encryption was primarily used for the military purposes. Very few people had computers, and someone could hardly imagine of a technology that would connect almost every human being on the planet – the internet. 

Two publications brought cryptography into the open, “Data Encryption Standard” published by the US Government, and “New Directions in Cryptography” white paper published by Dr. Whitfield Diffie and Dr. Martin Hellman, published in 1976. 

In the 1980s, Dr. David Chaum started writing on topics such as anonymous digital cash and pseudonymous reputation systems. This was the first step toward the digital currencies we see today. 

It wasn’t until 1992 that a group of cryptographers started meeting up on a regular basis to discuss their work and related ideas.  Besides their regular meetings, they also started the Cypherpunk mailing list in which they discussed many ideas. One of the idea was protection of privacy using cryptography, which led to the birth of Bitcoin.

The Cypherpunk manifesto stated that “Privacy is necessary for an open society in an electronic age. Privacy is not secrecy. A private matter is something one does not want the whole world to know, but a secret matter is something one does not want anybody to know. Privacy is the power to selectively reveal oneself to the world.”

Cypherpunks were not the only ones concerned about central entities becoming immensely powerful by accumulating unimaginable amount of data from millions of users. There was another group call crypto-anarchists who were concerned about the big banks and the governments diminishing the autonomy of average citizens, as well as influencing users’ psychology in unimaginable ways. Before the banking revolution, cash was anonymous and purely physical. However, as the banks became digital, they were able to track accounts balances and transactions of their users. So both these groups envisioned a need for an anonymous digital currency, giving their users the power to selectively reveal themselves to the world.

Several different companies and researchers attempted to invent a decentralized currency, however all of them failed, due to the inconsistencies with removal of centralization, like double spending attack – ‘an attack where a cryptocurrency can be used more than once, by altering the blockchain network and inserting a special one that allows user to reacquire cryptocurrency’. 

One of these companies was DigiCash, an electronic money corporation founded by David Chaum in 1989. DigiCash transactions were unique in that they were anonymous, promising complete privacy for users conducting digital transactions, and included a number of cryptographic protocols that prevented both governments and banks from tracing personal transactions. Due to the overwhelming burden and high costs to validate each and every digital signature in the system, DigiCash couldn’t survive and declared bankruptcy in 1998 and subsequently sold its assets to eCash Technologies, another digital currency company.

In 1997, Adam Back proposed a concept called Hashcash, and described more formally in 2002 paper "Hashcash - A Denial of Service Counter-Measure". Hashcash used a proof-of-work system to limit email spam and denial-of-service attacks. In order to send an email, a person would have to solve a cryptographic hash puzzle and provide a proof-of-work, with a Hashcash stamp added to the e-mail header. This Hashcash stamp would validate the e-mails as genuine and not spam. This proof-of-work would later become one of the integral concept on which Bitcoin was based. 

Similarly in 1998 Wei Dai published a paper “B-money, an anonymous, distributed, electronic cash system”. A proof-of-work function was used to create money. Everyone maintains a copy of the databases, and the work is verified by a collective ledger. All transactions are accomplished by collective book-keeping and authenticated by cryptographic hashes. These ideas would late influence the design of Bitcoin.

Invention of Bitcoin

Bitcoin adopted some key features from these inventions and learned from their mistakes. In 2008, Bitcoin became the first technology to succeed as cryptocurrency. The word Bitcoin is a compound of the words bit and coin. The domain name bitcoin.org was registered on 18th August 2008. 

On 31st October 2008, the Bitcoin whitepaper was published by an unknown person or group of people using the name Satoshi Nakamoto. This nine page whitepaper titled “Bitcoin: A Peer-to-Peer Electronic Cash System” was as proposal for framework of a peer-to-peer digital currency, where the network validates the transactions and stores the entire transaction history, enabling users not to rely on any financial institution to make safe transactions with one another. This whitepaper envisioned an anonymous, trustless, decentralized cryptocurrency which is not subject to any censorship or centralization, thus giving the users freedom to transact while protecting their privacy. 

Bitcoin was designed to be a deflationary currency, meaning there will only be a limited amount of Bitcoins that will ever exist, specifically 21 million. Every Bitcoin miner will get a block reward for finding a block, but this reward will decrease over time. Eventually the block reward will become 0, when 21 million bitcoins would have been mined.

Early Bitcoin Era

Bitcoin began use in 2009 when its implementation was released as open-source software. On 3rd January 2009, the bitcoin network was created when Nakamoto mined the starting block of the chain, known as the genesis block. The receiver of the first bitcoin transaction was Hal Finney, the creator of the first reusable proof-of-work system, who received 10 bitcoins from Nakamoto. In 2010, the first known commercial transaction using bitcoin occurred when programmer Laszlo Hanyecz bought two Papa John's pizzas for 10,000 Bitcoins from Jeremy Turdivant. At this point, Bitcoin turned into a cryptocurrency with real value from a worthless internet money. This purchase validated the use of Bitcoin as an actual currency. 

After early "proof-of-concept" transactions, the first major users of bitcoin were black markets, such as Silk Road, earning the reputation of “eBay of Drugs.” Silk Road leveraged an anonymous network protocol called Tor, which made rendered users identity anonymous, and used Bitcoins for transactions. network, Silk Road was shut down by FBI in 2013. Similarly mtgox.com, one of the largest Bitcoin exchanges during the early stages, was used by hackers to siphon of funds and had severe breaches of security, and was handling over 70% of all bitcoin transactions worldwide by 2014. However, due to severe breaches of security and loosing around 1 million of its customers Bitcoins, Mt. Gox suspended trading, closed its website and exchange service, and filed for bankruptcy protection from creditors in 2014. 

Bitcoin Rise and Mainstream Adoption

Between 2013 and 2015, Bitcoin price fluctuated heavily, skyrocketing from less than $14 in 2013 to more than $1000 in 2014, then again declining by 90% and falling to around $100. This was attributed to two factors – Chinese investors buying and selling Bitcon as speculative investments, and automated trading by Mt.gox which lasted till 2014. The Bitcoin Foundation was founded in September 2012 to promote bitcoin's development and uptake. Also, the transaction fees were reduced again by a factor of ten as a means to encourage microtransactions. In 2013, the US Financial Crimes Enforcement Network (FinCEN) established regulatory guidelines for "decentralized virtual currencies" such as bitcoin, classifying American bitcoin miners who sell their generated bitcoins as Money Service Businesses (MSBs), that are subject to registration or other legal obligations. Meanwhile the People's Bank of China prohibited Chinese financial institutions from using bitcoins, which led to decline in price again by 2015.

In 2014, several merchants started to accept Bitcoin as a mode of payment. Crypto exchanges and wallet firms were also popped letting users buy and sell Bitcoins, and merchants accept Bitcoin, without even having to personally join the Bitcoin network. In September that year, PayPal partnered with Coinbase, BitPay and GoCoin. 

Meanwhile Bitcoin was also releasing new upgrades to improve the efficiency of its software. In 2015, Bitcoin software release introduced a consensus library which gave programmers easy access to the rules governing consensus on the network. The developers could now add a new feature which allowed transactions to be made un-spendable until a specific time in the future. In October 2016, Bitcoin released a new feature to optimize its block-size, which would reduce the transaction fees as well as increase the maximum transaction capacity of the network. Thereafter the August 2017 release supported the Lightning Network as well as improved scalability. 

In 2018, the Bitcoin prices were negatively affected by several hacks or thefts from various cryptocurrency exchanges, including thefts from Coincheck in January 2018, Bithumb in June, and Bancor in July. Also, Bitcoin was struggling to scale as transactions were becoming less efficient and more time taking, due to limitations in block time and block size. In March 2018, a Bitcoin block was created every 10 minutes and could hold only 1 MB of transaction data, which is about 2000 transactions ~ 3 transactions per second. The transactions volume was exceeding Bitcoin network capacity, and transactions were being left unconfirmed as they were not able to be included in a block. Various increases to this limit have been proposed over Bitcoin's history. Bitcoin Cash has a block size of 32 MB and hence 32x more throughput than Bitcoin. Bitcoin SV removed the block size limit altogether. This led to another issue on decentralized governance, as no change mechanism was included in the Bitcoin protocol.

In September 2019 the Intercontinental Exchange (the owner of the NYSE) began trading of bitcoin futures on its exchange called Bakkt. On 13th March 2020, due to the onset of the COVID-19 pandemic, bitcoin fell below $4,000 during a broad market selloff from above $10,000 in February 2020, after 281,000 bitcoins were sold, held by owners for only thirty days. In August 2020, MicroStrategy invested $250 million in bitcoin as a treasury reserve asset. In October 2020, Square, Inc. placed approximately 1% of total assets ($50 million) in bitcoin. In November 2020, PayPal announced that US users could buy, hold, or sell bitcoin. In December 2020 Massachusetts Mutual Life Insurance Company announced a bitcoin purchase of USD $100 million, or roughly 0.04% of its general investment account. In February 2021 Tesla made a bitcoin purchase of USD $1.5 billion and announced the plan to start accepting bitcoin as payment for vehicles. However in May 2021, Tesla reversed course on 12 May 2021, saying they would no longer take Bitcoin due to concerns that "mining" the cryptocurrency was contributing to the consumption of fossil fuels and climate change. In September 2020, the Canton of Zug, Switzerland, announced to start to accepting tax payments in bitcoin by February 2021. In June 2021, the Legislative Assembly of El Salvador voted legislation to make Bitcoin legal tender in El Salvador, making it the 1st country to formally introduce Bitcoin as a legal tender. In October 2021, US SEC approved the ProShares Bitcoin Strategy ETF, a cash-settled futures exchange-traded fund (ETF). 

Why did Bitcoin Technology succeed as cryptocurrency?

Decentralized networks generally suffer from problems like having no central entities to ask for information about user accounts, or to identify malicious users, leading to certain inconsistencies between users and malicious entities infecting the network, the most popular attack being double spending attack. Bitcoin Technology solves these problems though two inherent concepts:

1.  Blockchain network which enables the transactions to be validated and broadcasted in the entire network using readily available software applications. When a transaction occurs, the network nodes validate these transactions, add them to their copy of the ledger, and then broadcast these ledger additions to other nodes. Once these transactions are accepted in the network, they become a block. Thereafter using the Proof-of-Work protocol, these blocks are added to the blockchain, and quickly published to all nodes, without requiring central oversight. This enables the network to determine when a particular bitcoin was spent, which is needed to prevent double-spending. 
2.  Proof-of-Work (PoW) protocol. To be accepted by the rest of the network, the ledger must contain a proof-of-work. The Proof-of-Work requires the Bitcoin miners to solve an arbitrary mathematical puzzle to find a number called a nonce or ‘number one’, which is a random arbitrary number issued in an authentication protocol to ensure that old communications cannot be reused in replay attacks. It can be used just once in a cryptographic communication, such that when the block content is hashed along with the nonce, the result is numerically smaller than the network's difficulty target. As a result, a new hash (a long string of characters) is generated that matches the target hash for the current block. This new block is added to the network and published to all the nodes, and the crypto miner who solves the problem this wins the right to add that block to the blockchain and receive rewards. Proof of work is this a form of adding new blocks of transactions to a cryptocurrency's blockchain. 

These two concepts enable anyone with access to internet join the Bitcoin network, verify and audit transaction history on their own, as well as create Bitcoins through mining via Proof-of-Work.

## Bitcoin Identity

In finance domain, identity is a means of authentication to ensure no one else acts on your behalf while accessing your financial accounts or conducting transactions. By authenticating, people can access their money as well as conduct financial transactions. If someone else tries to do implicate your identity and withdraw money from your bank, you can get a record of this, get the identity of the person trying to impersonate you, ban them from your network and get rid of such malicious activities in the future.

Now in the context of Bitcoin, if you want to send your friend 1 Bitcoin, he should not be able to add another 0 and make it 10 Bitcoins. He should also not be to replicate your signature. Bitcoin ensures prevention of such things and integrity of its network through digital signature. It has both public and private keys. Public key is the key you give to the public to communicate with you, and private key is the secret key that only you own and use to access your account.

![](Images/image00238.gif)

 

In context of Bitcoin, public key can be considered as a locker, and private key can be considered as a key. Public key is used for receiving money, and private key is used for redeeming money. Other users send Bitcoins to your Bitcoin address, which is derived from your public key. To generate an identity, the user selects a random15 private key and generates the public key from the private key, using a mathematical function. The public-private key concept ensure unique identity of users and their authentication in the Bitcoin space

## Bitcoin Consensus  

Since blockchain information is stored by everyone in the network, a consensus is needed to ensure that everyone agrees on the transactions history. Not only do all the users need to agree on any transaction update, but they also need to agree on a valid transaction update to make sure that no corrupted information is acquired by the network. 

One of Bitcoin’s most unique features is its consensus algorithm, which set the precedent for a Byzantine Fault Tolerant (BFT) peer-to-peer currency system. Byzantine Fault Tolerance is a mechanism that enables a decentralized, trustless network to function even in the presence of malfunctioning or malicious nodes. Byzantine fault tolerance can be achieved if the loyal (non-faulty) generals have a majority agreement on their strategy.

The most common definition of Bitcoin’s consensus algorithm is proof-of-work (PoW), the consensus mechanism that relies on participants solving cryptographic puzzles to validate new information. However, PoW is part of a larger consensus algorithm that is commonly known as “Nakamoto Consensus.” Nakamoto Consensus is what made Bitcoin different from prior digital currency implementations.

PoW refers to the cryptographic mechanism that relies on participants being able to solve hard computational problems to have a higher stake in the network. PoW essentially is a distributed way for participants to determine the most valid block. Each participant attempts to find a hash value, which is a valid solution for the upcoming block of transactions. The winner who finds the hash value that meets the requirement, adds the proposal block to the chain, and obtains the reward.

Hashcash proof-of-work is utilized using a hashing algorithm SHA-256. This involves finding a value ‘x’ such as that when ‘x’ is hashed with this algorithm, the required value is found. This is often an iterative process; nonces (numbers used once) are added to the end of the string being hashed each successive round until the required value is given. Once the participant manages to find a solution to the PoW, they broadcast their block to the rest of the network, where it is then approved if none of the transactions within have already been spent based on the timestamp. Participant then receives a reward in Bitcoin as compensation for the amount of computing power they spent in order to validate the next block of transactions.

Mining in Bitcoin is really the commitment of a certain amount of computing resources to the sole purpose of solving computationally hard problems and validating new blocks. The more computing power an individual node has, the more likely it is to find a correct value for the SHA-256 hash, and thus solve the cryptographic hash associated with that block’s PoW. 

PoW enables Bitcoin to be both fully decentralized and fully secure. Anyone can participate in the mining process, without needing to own a certain number of bitcoin beforehand in order to do so. In fact, it is completely unknown who the winner of the next mining reward will be at any given point in time, with additional computing power only serving to increase the probability that an individual node will be successful. Furthermore, the mining process also incentivizes nodes to act honestly because of the rewards associated with broadcasting the correct block. This means that in order to take over the network, a malicious attacker has to control over 51% of the computing/hashing power on the network and prevent legitimate blocks from being validated. This is commonly known as a “51% attack.” Due to the Bitcoin network’s current size, the economic cost of accruing over 51% of the hashing power currently present in the network is huge, and thus extremely difficult.

The second part of Nakamoto Consensus is what allowed Bitcoin to be the first scalable cryptocurrency platform. Nakamoto Consensus places a large emphasis on the longest chain, arguing that the longest chain that is also valid according to timestamps is the most legitimate, as it had the largest amount of computational resources dedicated to it. This introduces trust in an otherwise trustless system, thus allowing the Bitcoin network to function without a centralized authority. For example, if a participant has been inactive, or has newly joined, they can simply accept the current longest chain as proof of what happened previously within the network. They do not need to rely on a 3rd party; rather simply start build upon the longest valid chain, thus gaining the ability to receive rewards by proposing a computationally valid block. In fact, the “longest chain rule”, as it has been dubbed by the cryptocurrency community, enabled Bitcoin to succeed where previous PoW digital currencies had failed. It allowed participants to have confidence in the network, as well as set a standard through which miners could begin to join and leave at will without having to defer to an authority. The longest chain rule has been adopted by numerous digital asset systems and blockchains that came after Bitcoin.

Nakamoto Consensus ultimately revolutionized both digital currency and modern cryptography solution that was scalable, thus allowing Bitcoin to succeed as a trustless peer-to-peer transaction system. Specifically, Nakamoto Consensus managed to create a standard of measurement for the blockchain’s validity: the amount of computational resources spent on it. While the Nakamoto Consensus model has seen its fair share of criticism, largely due to its tendency to allow the chain to fork, it remains one of the most efficient and successful consensus mechanisms among decentralized networks. By attaching a scarce resource (computing power) to the blockchain, Nakamoto Consensus gives Bitcoin implicit value, security, and trust over other currency systems.

Cryptographic Hash Functions

Suppose you take a flight from London to New York. At the New York airport, the immigration officer scans your fingerprint and your eye. For the person next to you in the queue this fingerprint and eye scan changes. It becomes your unique identifier, which is difficult to forge and tamper. 

The same concept applies in Bitcoin. Except instead of fingerprints and eye-scans, you can replace yourself with a meaningful information, and your fingerprint with some pseudorandom output (a same random output for a unique input). If we can design a way to generate fingerprints of our meaningful data, we can ensure the integrity of our information. This is achieved by cryptographic hash functions.

A cryptographic hash function is a mathematical algorithm that takes an arbitrary amount of data input (consider yourself) and produces a fixed-size output of enciphered text called “hash” (consider your fingerprint). This hash can then be stored instead of the password itself, and later used to verify the user. A cryptographic hash function must be deterministic, meaning that the same message always results in the same hash.

![](Images/image00239.jpeg)

A cryptographic hash function (specifically SHA-1) at work. 

A small change in the input (in the word "over") drastically 

changes the output (digest). This is also known as 

‘Avalanche Effect’.

Source - Wikipedia

 

 

A cryptographic hash function has the following key properties:

*   Nonreversible – A good hash function should make it very hard to reconstruct the original password from the output or hash. This is achieved via ‘Preimage resistance’, which refers to the difficulty of finding an input given an output. Mathematically, given a hash value ‘H’, it should be difficult to find any message ‘x’ such that H = Hash(x).
*   Determinism – A given password must always generate the same hash value or enciphered text. This is achieved via the 2nd preimage resistance, which for any given input ‘x’, it should be computationally difficult to find a different input ‘y’, such that Hash (x) = Hash (y).
*   Collision resistance – It should be hard to find two different passwords that hash to the same enciphered text. In mathematical terminology, for a given hash function ‘H’, it is computationally difficult to find two different inputs ‘x’ and ‘y’, such that H(x) = H(y).
*   Non predictable – The hash value should not be predictable from the password.
*   Diffusion (Avalanche effect) – When a password is changed slightly, the output of enciphered text should change significantly and unpredictably.

Informally, these properties mean that a malicious attacker cannot replace or modify the input data without changing its digest. Thus, if two strings have the same digest, one can be very confident that they are identical. Second pre-image resistance prevents an attacker from crafting a document with the same hash as a document the attacker cannot control. Collision resistance prevents an attacker from creating two distinct documents with the same hash.

An illustration of the potential use of a cryptographic hash is as follows: Suppose you give me a tough computational problem to solve and claim that you have already solved it. I want to solve this problem, however I would like to ensure that you have actually solved this problem as well. So, you would write down your solution, compute its hash, and tell me the hash value (whilst keeping the solution secret). Let’s assume that I solve this problem in a week. Now you can prove that you solved it earlier by revealing the solution, which I can hash and validate with the hash value you gave me before.

An important application of secure hashes is the verification of message integrity. Comparing message digests (hash digests over the message) calculated before, and after, transmission can determine whether any changes have been made to the message or file. Using a cryptographic hash and a chain of trust detects malicious changes to the file. Almost all digital signature schemes require a cryptographic hash to be calculated over the message. This allows the signature calculation to be performed on the relatively small, statically sized hash digest. The message is considered authentic if the signature verification succeeds given the signature and recalculated hash digest over the message. So the message integrity property of the cryptographic hash is used to create secure and efficient digital signature schemes.

Bitcoin uses hash function ‘Security Hash Algorithm-256 (SHA-256)’ to validate PoW protocols in its network. SHA-256 was originally designed by US National Security Agency (NSA). SHA-256 is a member of SHA-2 family of cryptographic has functions. It takes an input size less that 2^64 bits and produces a fixed size output of 256 bits. Bitcoin, in certain instances uses SHA-256d, meaning that SHA-256 is used twice in a row, once on the original message to be hashed and again on the output of the 1st hash. 

This system uses partial hash inversions to prove that work was done, unlock a mining reward in Bitcoin, and as a good-will token to send an e-mail in Hash-cash. The sender is required to find a message whose hash value begins with a certain number of zero bits. The average work that the sender needs to perform to find a valid message is exponential in the number of zero bits required in the hash value, while the recipient can verify the validity of the message by executing a single hash function. 

Tamper Proofing

Now that we know how cryptographic hash functions ensure the integrity of data, the next step is to apply this concept to ensure that data are only accessed by authorized users. For this we require a method of tracking transactions, to govern who has access to data and when. Automatic, tamper-proof logging of transactions is a method for enabling oversight of how the data is being used.

Here is how a tamper evident block looks like conceptually.

![](Images/image00244.gif)

It has four main components:

*   Block Header – This field represents the metadata necessary for understanding the components
*   Block Size – This field represents the size of the block
*   Transaction Counter – This field represents the number of transactions contained in the block
*   Transactions – This field represents the actual transaction data

The tamper proofing of the block is achieved by the Block Header, through the application of the hash function.

Block Header

The Block Header refers to all metadata associated with any block. It consists of 6 fields as represented by the diagram below:

![](Images/image00245.gif)

*   Previous Block Hash – The previous block hash links to the previous block, or its parent block, effectively securing the chain. If any block is altered, then the block after will also be altered, and so all the blocks after that. Changing any part of the transaction history will change the entire future transactions after that. 
*   Merkle Root – The Merkle root is made up of all of the hashed transaction hashes within the transaction. 
*   Nonce – Nonce is the value that miners can alter to create different permutations and generate a correct hash in the sequence.
*   Timestamp – The timestamp is included so that everyone in the node will be able to see a permanent, encoded record of when a particular event occurred. It provides the date and time of day when the event occurred.
*   Target – The difficulty target is used, simply, to adjust how hard it is for the miners working to solve the block.
*   Version – The Bitcoin version number is useful in keeping track of changes and updates throughout the protocol.

Merkle Tree and Merkle Root

In computer science terminology, a tree is a data structure that has a root node and some children, which may also be the roots of other trees. A binary tree is a tree in which every node has two children, as shown below.

![](Images/image00246.gif)

A Merkle Tree is a very specific version of Binary Tree, in which every "child" (node) is labelled with the cryptographic hash of a data block, and every node that is not a “child” is labelled with the cryptographic hash of the labels of its child nodes. A hash tree allows efficient and secure verification of the contents of a large data structure. The concept of a hash tree is named after Ralph Merkle, who patented it in 1979.

The following conditions need to be true for a tree to be a Merkle Tree:

*   There is a power of two children at the bottom most level
*   The lowest level is made of the hashes of the summarized information

The construction of the Merkle Tree consists of verified Data Blocks. Each of them is hashed to get a level of hashes.  Then 2 blocks are paired together and hashed, making a new level with half as many blocks. This process is continued till only one hash remains at the top. This has at the top is called the Merkle Root. This way any transaction change can be detected after commitment with the Merkle Root.

![](Images/image00247.gif)

Let’s assume that Block 3 is changed, then its hash will also change. Because of this the hash above will also change, propagating all the way up to the Merkle Root. Hence, if any transaction is changed, then the corresponding Merkle Root is also impacted.

We can validate any transaction with just one piece of information at each level. For example, we can validate Block 1 with Hash 0. This makes the network more and more efficient as the tree grows larger.

In case a Merkle Root somehow gets tampered, it changes the block header. This is turn alters the next block’s ‘previous block hash’, which will impact all the future block hashes as well. The rest of the network will reject the history proposed by this blockchain because they will not agree.

Partial Preimage Hash Puzzle

The entities in the network need to prove that they have done some work before they can submit a vote to the network. They have to design a partial preimage hash puzzle for their computers to solve to prove that they have done work. Partial preimage means a partial input. In Bitcoin, we are given a part of the input, and we have to find the other part which produces some partial output, meeting the condition that the hash of the block header needs to be less than some target value. This is how Proof-of-Work (PoW) gets implemented in Bitcoin. These hash puzzles need to have three characteristics:

*   Computationally difficult – Ensure that the puzzle cannot be easily solved
*   Parameterizable – The difficulty of the puzzle should be adjustable to ensure that it never gets either too easy or too hard
*   Easily verifiable – Ensure that the computers in the network do not have to do too much work to validate the solution of the puzzle

Digital Signatures

Digital signatures ensure that the current transactions sent to the rest of the network are tamper proof as well. Digital signatures authenticate identity of the user, as it was signed with a specific private key, providing ownership of a public key to validate it.

For example, suppose you want to send your friend a message. How can you make sure that it is not tampered. So, before sending the message you sign it with your private key, authenticating your identity. Then you send the signed message to your friend. The message is the main payload and the digital signature is used to prove that it was you who created the exact message. Your friend is able to verify your signature with your public key. At any point, if this message is tampered with, the digital signature would not remain valid anymore. This is how digital signature make the message tamper proof.

Digital signatures have the following key properties:

*   Message origin – Recipient is able to verify that the original sender (owner of private key) has authorized the message
*   Non-repudiation – Original sender (owner of private key) cannot backtrack, undo or nullify the signature, after sending the message
*   Message integrity – Message cannot be modified after sending

In Bitcoin, private and public keys are generates through Elliptic Curve Digital Signature Algorithm (ECDSA). Elliptic-curve cryptography (ECC) is an approach to public-key cryptography based on the algebraic structure of elliptic curves over finite fields. ECC allows smaller keys compared to non-EC cryptography (based on plain Galois fields) to provide equivalent security. ECDSA offers a variant of the Digital Signature Algorithm (DSA) which uses elliptic curve cryptography. 

An elliptic curve is a mathematical curve defined by the equation:

y^2 = x^3 + ax + b

It is defined over a finite field to encode every value possible in a defined amount of space, so as to limit the key size.

There are certain unique properties of elliptic curves that help in creating a one-way function to generate public key from private keys, and not vice versa.

Suppose you want to send a your friend a signed message. Initially you both must agree on the curve parameters, as below:

*   Curve – The elliptic curve field and equation used
*   G – Elliptic curve base point, a point on the curve that generates a subgroup of large prime order n
*   n – Integer order of G, means that n \* G = O, where O is the identity element
*   dA – The private key (randomly selected)
*   QA – The public key (calculated by elliptic curve)
*   m – The message to send

You will create a key pair, consisting of a private key integer dA, randomly selected in the interval; and a public key curve point QA = dA \* G. You need to follow the following steps to send the message:

1.  Calculate hash of the message ‘m’
2.  Let z be the Ln leftmost bits of e, where Ln is the bit length of the group order n
3.  Select a cryptographically secure random integer k from \[1,n-1\]
4.  Calculate the curve point (x1, y1) = k \* G
5.  Calculate r = x1 mod n. If r = 0, go-to step 3
6.  Calculate s = k^(-1) \* (z + rdA) mod n. If s = 0, go-to step 3
7.  The signature is the pair (r,s)

For your friend to authenticate your signature, he must have a copy of your public-key curve point QA, and can verify it as a valid curve point as follows:

1.  Check that QA is not equal to the identity element O, and its coordinates are otherwise valid
2.  Check that QA lies on the curve
3.  Check that n \* QA = O

After that, he needs to follow these steps:

1.  Verify that r and s are integers in \[1,n-1\]. If not, the signature is invalid.
2.  Calculate hash of the message ‘m’, where hash is the same function used in the signature generation.
3.  Let z be the Ln leftmost bits of e.
4.  Calculate u1 \= zs^(-1) mod n and u2 = zs^(-1) mod n
5.  Calculate the curve point (x1, y1) = u1 \* G + u2 \* QA. If (x1, y1) = O, then the signature is invalid.
6.  The signature is valid if r = x1 (mod n), invalid otherwise.

As with elliptic-curve cryptography in general, the bit size of the public key believed to be needed for ECDSA is about twice the size of the security level, in bits. For example, at a security level of 80 bits, an attacker would require a maximum of about 2^80 operations to find the private key, the size of an ECDSA private key would be 160 bits, whereas the size of a DSA private key is at least 1024 bits. 

Bitcoin elliptic curve is called secp256k1. It equation is y^2 = x^3 +7. It has taken over a finite field to limit the key size. This curve is specified by a couple of parameters, including the curve formula, the field, and a generator point. On this elliptic curve, we can do point additions using lines and points. To add 2 points ‘P’ and ‘Q’, we draw a line through them, intersecting at a 3rd point ‘R’ across the x-axis, yielding our result ‘P+Q’. This is a one-way function, because for a given point ‘K’ that is ‘P + Q’, it is difficult to find the individual points ‘P’ and ‘Q’.

To send a Bitcoin transaction, a user generates a random number ‘n’ for his private key, and use the elliptic curve secp256k1 to his public key. To do so, he adds a known generator point ‘P’ which is built into secp256k1 specification, with itself n times. Given a public key ‘nP' it is computationally infeasible to get the private key, which makes the process for generating public key from private key secure.

Then to generate the address, we hash the public key ‘nP’ with SHA-256 first, and then with another hash function called RIPEMD-160. SHA-256 makes the address quantum resistant such that quantum computers cannot reverse the hash function. RIPEMD-160 then shortens the address size from 256 bits to 160 bits. Together, the combination of using SHA-256 and RIOEMD-160 is called “double hash” or HASH160.

After this, we have a public key hash. The next step is to make this public key hash more human friendly. First, we add a version byte in front of the previous RIPEMD-160 hash, wherein we specify which network we are on: the main Bitcoin network or a smaller test network. We then run a Base58Check encode, which converts this hash into Base 58 - an alphabet like the usual 62 character alphabet (A-Z, a-z, 0-9). Base 58 has all the digits 0 to 9 and all upper case and lower case letters, except the capital and lower case ‘O’, and also the capital and the lower case ‘I’ to avoid ambiguity. 

Then we calculate a checksum.

We perform SHA-256d on the extended RIPEMD-160 hash, running SHA-256 on it twice. We take the first 4 byte of SHA-256d hash as our checksum, and append it to the end of the extended RIPEMD-160 hash. After converting this result to Base 58, we finally get our Bitcoin address.

In this address, we have successfully encoded the public key hash which allows people to pay us, a version byte that mentions which network we are on, and a checksum that accounts for any human error. If someone copies the wrong address, then the address will not be valid given the checksum.

![](Images/image00248.gif)

## Bitcoin Transaction Process

For a transaction to be valid, it must have these three components

*   A proof of ownership
*   Sufficient funds
*   These funds are used only for this transaction

To enforce this, Bitcoin uses Unspent Transaction Output (UTXO) concept. A UTXO can be imagined as a box that contains Bitcoins and they can hold any amounts. Once you have some bitcoins, in the Blockchain all you have is a bunch of UTXOs. For all practical purposes, you can think of your UTXOs as your box full of piggybanks. Lets assume you want to transfer your friend 5 Bitcoins, so you put these 5 Bitcoins into a UTXO (a piggybank). Once you make that transaction, you break open that piggybank, which cannot be restored again. The total amount of Bitcoin you own is summation of the value of all your UTXOs. 

Suppose you transfer the 5 Bitcoins to your friend, the history of this transaction needs to be stored in the network to confirm the amount of Bitcoin owned by you and your friend currently, and to validate future transactions. This information is saved in the Bitcoin’s distributed database – Blockchain. Bitcoin blockchain is implemented as a chain of blocks, each block containing a hash of the previous block up to the genesis block in the chain. A network of communicating nodes running Bitcoin software maintains the blockchain. Every person in the node owns the ledger, and has as much right to vote on the validity of this transaction as anyone else in the network. Once you have transferred the 5 Bitcoins to your friend, this transaction is validated by the network nodes, which add this transaction to their copy of the ledger. Then they broadcast these ledger additions to other nodes. At varying intervals of time averaging to every 10 minutes, a new group of accepted transactions, called a block, is created, added to the blockchain, and quickly published to all nodes, without requiring central oversight.  By grouping data into blocks, the network is not strained as a result of updating every ledger after every transaction. Every block is an update, and a chain of block represent a history. The process is helpful for identifying discrepancies between different versions of the database, since every node can validate what actually happened in the ledger at any given time. Since every block is built off the previous one, it contains information about the previous block. If any block gets tampered, information within this block and all future blocks will change. This makes blockchain tamper evident, since tampering with a transaction from the past would invalidate any future blocks linking back to it. 

In Bitcoin, each transaction is an output from previous transactions and feeding into new transactions. Transactions contain the signature of the owner of the unspent funds. These unspent transactions are called UTXOs. So how do you spend your Bitcoin or UTXOs. For example, if you send me 1 Bitcoin, then in that transaction it is encoded that only 1 can redeem that UTXO, using a public key and a signature.

In Bitcoin, a transaction has 3 main sections:

*   Metadata – Contains some housekeeping data, a unique transaction ID, lock-time, and block size
*   Input – Contains a list of previously created UTXOs as well as the proof that I am eligible of redeeming this money
*   Output – Contains a list of new UTXOs that will be sent to a new address. This new address is a Bitcoin script that locks the transaction and makes it redeemable only by the specific proof that I specified in this transaction. 

![](Images/image00249.gif)

## Bitcoin Script

Bitcoin Script is the language Bitcoin uses to do everything it can do, from processing financial transactions between two entities to more complex multi-signature transactions. In other words, Bitcoin Script refers to a simple programming language used in Bitcoin for the processing of transactions that is read from left to right. Rather than connecting the public keys together, connecting inputs and outputs through Bitcoin scripts allows for potentially complex transactions.

The script language is stack-based, last-in-first-out (LIFO),  and is intentionally not Full Turing, as this prevents infinite or endless looping and error execution. 

A Bitcoin Script is essentially a list of instructions recorded with each Bitcoin transaction, that describe how the next person wanting to spend the Bitcoins being transferred can gain access to them. The script for transferring a Bitcoin to a destination address ‘X’ loads the future spending of the bitcoins with two things, which the sender must provide

*   A public key that, when hashed, yields destination address ‘X’ embedded in the script
*   A digital signature to prove ownership of the private key corresponding to the public key that the sender provided

A transaction is valid if nothing in the combined script triggers failure and the top stack item is True (non-zero) when the script exits. The original sender of the Bitcoins which is now being spent dictates the script operations that will occur last to release them for another transaction. The current sender must provide the input to the previously recorded script that results in the combined script completing execution with a true value on the top of the stack.

Operational Code (OP\_CODE)

In computing, an Operational Code or OP\_CODE is a portion of a machine language instruction that specifies the operation to be performed. 

Generally this processing is done by the computer hardware (usually a CPU). But it can also be software specially prepared to emulate the operation of a CPU and process these instructions. In general, a complete machine language instruction contains an OP\_CODE, on which the operation code must act. 

In Bitcoin, OP\_CODES are the backbone of the system to program transaction instructions. Bitcoin Script is actually a programming language where instructions are given in OP\_CODES that the Bitcoin network has defined beforehand for its operation. Bitcoin structure allows the possibility of defining 256 OP\_CODES, different of which start from number 0 to 255. Of these 256 OP\_CODES, currently 116 are active.

These OP\_CODES are the ones that allow you to carry out the different operations in Bitcoin and its transaction scheduling, such as data flow control, constant management, stack management, logical management, arithmetic, time lock, pseudo-words, cryptographic operations, and reserved words. The below table describes some of the key OP\_CODES of Bitcoin:

 
| Word || OP\_CODE || Hex || Input || Output || Description |
| --- | --- | --- | --- | --- | --- |
| OP\_0 || 0 || 0\*00 || Nothing || Empty || An empty array of bytes is pushed onto stack |
| OP\_IF || 99 || 0\*63 || If || Then / Else || If the top stack value is not False, the statements are executed. The top stack value is removed. |
| OP\_VERIFY || 105 || 0\*69 || True / False || Nothing / Fail || Marks transaction as invalid if top stack value is not true. The top stack value is removed. |
| OP\_EQUAL || 135 || 0\*87 || x1 x2 || True / False || Returns 1 if the inputs are exactly equal, 0 otherwise |
| OP\_ADD || 147 || 0\*93 || a b  || out || Adds a to b |
| OP\_SUB || 148 || 0\*94 || a b  || out || Subtracts b from a |
| OP\_NEGATE || 143 || 0\*8f || in || out || The sign of the input is flipped |
| OP\_ABS || 144 || 0\*90 || in || out || The input is made positive |
| OP\_NOT || 145 || 0\*91 || in || out || If input is 0 or 1, it is flipped. Else output is 0 |
| OP\_NUMEQUAL || 156 || 0\*9c || a b || out || Returns 1 if numbers are equal. Else 0 |
| OP\_RIPEMD160 || 166 || 0\*a6 || in || Hash || Input is hashed using RIPEMD-160 |
| OP\_SHA256 || 168 || 0\*a8 || in || Hash || Input is hashed using SHA-256 |
| OP\_HASH160 || 169 || 0\*a9 || in || Hash || Input is hashed twice. First with SHA-256, and then with RIPEMD-160 |
| OP\_HASH256 || 170 || 0\*aa || in || Hash || Input is hashed twice with SHA-256 |
| OP\_CHECKLOCKTIMEVERIFY || 177 || 0\*b1 || X || X / Fail || Marks transaction as invalid if the top stack item > the transaction's nLockTime field, otherwise script evaluation continues as though an OP\_NOP was executed |
| OP\_CHECKSEQUENCEVERIFY || 178 || 0\*b2 || X || X / Fail || Marks transaction as invalid if the relative lock time of the input is not equal to or longer than the value of the top stack item |

 

Script Template

Each Bitcoin Script is divided into two types of scripts to implement transactions: 

*   Unlocking script (scriptSig) – The scriptSig is the unlocking script found in the transaction input provided by the spender to redeem the output of a previous transaction. It requires a public key and a digital signature. The system only carry outs transactions if the signatures and their verification comply with a series of established rules that guarantee proper behavior on the network.
*   Locking script (scriptPubKey) – The scriptPubKey is the locking script found in the transaction output which specifies the requirements for redeeming the transaction. It contains a public key hash, also called a Bitcoin address. The scheduling of Bitcoin transactions as such is stored in this part of the script.

Script Examples

Suppose you want to send a Bitcoin to some address. The script will be:

scriptPubKey: OP\_DUP OP\_HASH160 <pubKeyHash> OP\_EQUALVERIFY OP\_CHECKSIG

scriptSig: <sig> <pubKey>

In this example, the locking script requires the user who wants to spend from a previous transaction must prove that he possess a private key that hashes to a specific address. For this reason, the script is called scriptPubKey. To make the unlocking and locking script work together, we put the unlocking script (scriptSig) on the top of the locking script (scriptPubKey) and run them together. The entire resulting script must execute successfully for the transaction to be considered valid.

Similarly, suppose you want to freeze your Bitcoins until a certain point in the future. The script will be:

scriptPubKey: <expiry time> OP\_CHECKLOCKTIMEVERIFY OP\_DROP OP\_DUP OP\_HASH160 <pubKeyHash> OP\_EQUALVERIFY OP\_CHECKSIG

scriptSig: <sig> <pubKey>

In this example, the locking script will mark the transaction as invalid if the transaction's date and time is less than the future date and time set by the user. 

The purpose of creating a script language in Bitcoin is to provide a series of easy and flexible parameters to enable a transaction. It is this programming language that determines whether or not an operation can be performed. Simply put, the creation of the Bitcoin Script is what gives the programmable nature of Bitcoin. This is what allows us, for example, to send a transaction that is validated only if certain conditions are met. This property is something unique to Bitcoin and cryptocurrencies, something that today's digital money cannot reach, let alone physical money. It is the evolution of money reached a point where even money can act independently and decentralized simply by attending to the programming embedded in it.

Moreover, The Bitcoin script also prevents the creation of errors in the system and the unnecessary use of very complex transactions. In fact, the script makes transactions relatively easy to calculate. 

Pay-to-Public-Key-Hash (P2PKH)

Pay-to-Public-Key-Hash (P2PKH) is a type of scriptPubKey which locks bitcoin to the hash of a public key. A P2PKH transaction is one where the inputs were locked using the P2PKH scriptPubKey. A public key hash is also known as an address, and P2PKH is the most common script type at present.

Lets’ go back to the previous example, wherein you want to send a Bitcoin to some address. The script will be:

scriptPubKey: OP\_DUP OP\_HASH160 <pubKeyHash> OP\_EQUALVERIFY OP\_CHECKSIG

scriptSig: <sig> <pubKey>

Since, Bitcoin script is stack-based last-in-first-out (LIFO), so we first put the signature on the stack and then the public key.

1.  OP\_DUP will duplicate the top item on the stack. 
2.  OP\_HASH160 will hash the previous item on the stack, first withSHA-256 and then with RIPEMD-160.  
3.  <pubKeyHash> is the actual public key hash specified by the previous transaction output. We put it on the stack
4.  OP\_EQUALVERIFY checks if the top two items on the stack are equal. If yes, the execution is continued; else the transaction is declared invalid and the execution stops
5.  OP\_CHECKSIG checks the validity of the signature with the given public key. If it is valid, then it will return the True value and the transaction will go through

The entire resulting script must execute successfully for the transaction to be considered valid.

Pay-to-Script-Hash (P2SH) 

Pay-to-Script-Hash (P2SH) is a type of scriptPubKey which allows for the spending of bitcoin based on the satisfaction of the script whose hash is specified within the transaction. P2SH is extremely flexible and customer friendly, because it allows users to construct and specify the scripts. For example, if you want to send me 1 Bitcoin in a P2SH transaction, you need to include the hash of the script required to spend the bitcoin in the transaction. When I want to spend this Bitcoin, I will reconstruct the script whose hash you used to send this Bitcoin and sign the transaction with any private keys required by the script. Additionally, I can privately construct my desired script and only send you the hash of that script, preserving my privacy for this Bitcoin transaction.

P2PKH vs P2SH

In P2PKH, the sender needs to have access to the receiver’s public key hash, such that he can send the Bitcoin to the receiver’s public key hash. Now to redeem this Bitcoin, the receiver must provide his digital signature and full public key, to prove his identity. 

![](Images/image00250.gif)

P2PKH process to transfer Bitcoin

Now, if the receiver wants to introduce some more functionality into this transaction, for example inserting a multi-sign or appending a time-lock, he needs to create a script, take its hash, and send it to the sender. To redeem the Bitcoin with this added functionality, he needs to provide his digital signature along with the full script that he has written, via P2SH.

![](Images/image00251.gif)

P2SH process to transfer Bitcoin

So, P2SH becomes quite helpful in a supplier – customer ecosystem, where the supplier is the recipient of Bitcoin, and customer is the sender. If the supplier wants to receive payments and use complex features like multisignature, they do not want to burden their customers by forcing them to write complex scripts just to make payments. Hence, they use P2SH to compose a locking script and share with their customers. The customer can use this script to make the payments and receive their product or service. 

Multisignature (Multisig)

One of the most widely used example of P2SH is multisignature (multisig), where specific number of pre-specified signatures are required to unlock a UTXO. ‘Multisig’ refers to requiring multiple keys to authorize a Bitcoin transaction, rather than a single signature from one key. A typical ‘multisig’ scheme is an m-of-n, where you need m of n signature users to sign-off on a transaction before it is considered valid. ‘Multisig’ has number of benefits:

*   Making it difficult for someone to steal Bitcoins by avoiding single-point of failure, as instead of unlocking one private key, now minimum ‘m’ of ‘n’ keys need to be unlocked to receive payments. 
*   m-of-n backup where loss of a single seed doesn't lead to loss of the wallet. Hence, it protects against Bitcoin losses, because if the owner of the Bitcoin looses a key, he can still unlock his funds from the remaining ‘m’ of ‘n’ keys. 
*   Dividing up responsibility for possession of bitcoins among multiple people

Lets assume you want to create a 2-of-3 ‘multisig’ address. It can be created by following these steps:

1.  Gather / generate 3 bitcoin addresses, on whichever machines will be participating, using GETNEWADDRESS or GETACCOUNTADDRESS RPC commands
2.  Get their public keys using the VALIDATEADDRESS RPC command 3 times.
3.  Then create a 2-of-3 ‘multisig’ address using ADDMULTISIGADDRESS

Time-lock

Time-locks are a functionality in Bitcoin that restrict spending of Bitcoin until a later time. Time in this case can be represented as timestamp, block height, or number of blocks built on the top of the block containing the transaction. Time-locks can be absolute or relative. 

*   Absolute time-lock specify an absolute point in future when the particular transaction becomes valid. This is done using a timestamp or block height. 
*   Relative time-lock specify a block depth, or the number of blocks built on the top of the current one. 

Time-locks can be transaction level or script level

*   A transaction level time-lock can impose time-lock on the transaction itself. This time-lock ensures that the transaction cannot be include in a valid block until a particular time in future
*   A script level time-lock can impose time-locks on specific UTXO and are specified using Bitcoin scripts. This UTXO level time-lock specifies that a UTXO cannot be spent until the specified time. This ensures that the sender cannot override the transaction by sending the UTXO to another address before the time-lock is unlocked.

## Bitcoin Network

Bitcoin is structured as a peer-to-peer (P2P) network architecture on top of the internet, meaning that the computers that participate in the Bitcoin network are all equal, that there are no “special” nodes, and that all nodes share the burden of providing network services. The network nodes interconnect in a mesh network with a “flat” topology. There is no server, no centralized service, and no hierarchy within the network. Nodes in a peer-to-peer network both provide and consume services at the same time with reciprocity acting as the incentive for participation. Peer-to-peer networks are inherently resilient, decentralized, and open.

The term “Bitcoin Network” refers to the collection of nodes running the Bitcoin P2P protocol. In addition to the Bitcoin P2P protocol, there are other protocols such as Stratum19, which are used for mining and mobile wallets. These additional protocols are provided by gateway routing servers that access the bitcoin network using the bitcoin P2P protocol, and then extend that network to nodes running other protocols. Extended Bitcoin Network” refers to the overall network that includes the Bitcoin P2P protocol, pool-mining protocols, the Stratum protocol, and any other related protocols connecting the components of the bitcoin system.

Although nodes in the bitcoin P2P network are equal, they may take on different roles depending on the functionality they are supporting. A bitcoin node is a collection of functions: Network Routing, Maintaining Blockchain Database, Mining, and Managing Wallet Services. A Full Node contains all these functions, and can autonomously and authoritatively verify any transaction without external reference. Some nodes maintain only a subset of the blockchain and verify transactions using a method called ‘Simplified Payment Verification’ (SPV) or Lightweight Nodes. Mining Nodes compete to create new blocks by running specialized hardware to solve the proof-of-work algorithm. Some mining nodes are Full Nodes, maintaining a full copy of the blockchain, while others are SPV participating in pool mining and depending on a pool server to maintain a full node. 

In addition to the main node types on the bitcoin P2P protocol, there are servers and nodes running other protocols, such as specialized mining pool protocols and lightweight client-access protocols.

![](Images/image00252.jpeg)

Bitcoin Transfer via Bitcoin Network

Source - Wikipedia

 

Types of Bitcoin users

There is plethora of different types of Bitcoin users, depending on how they interface with the Bitcoin network. The user experience in the Bitcoin network varies greatly depending if the user is a light user, owning a full node, solo miner, or running a mining farm. Not every user need to have the entire blockchain. 

There is a total of four functions in Bitcoin – Mining, Network routing, Maintaining blockchain, and wallet management, and the distinction between Bitcoin users is through these four functionalities

There are four type of Bitcoin users:

*   Light User – This type of user is the most common Bitcoin user. His focus on bitcoin’s potential as an investment, or a currency. He doesn’t need the entire copy of the blockchain. He primarily uses the Network Routing Node to send and receive Bitcoins with the rest of the network, and wallet functionality to help manage his keys.
*   Miner – This type of user is a computer programmer, and uses mining functionality and copy of the full Blockchain for solving hash puzzles in P-o-W protocol, and Network Routing Node functionality to broadcast to the entire network.
*   Full Node Owner – This user is responsible for owning the Bitcoin node, and uses Blockchain and Network Routing Node functionalities of the Bitcoin to validate transactions and check any anomaly in the network.
*   Running a mining farm – Such users are core to Bitcoin and use all the functionalities of the Bitcoin network.

## Bitcoin Wallets

A Bitcoin wallet stores the information necessary to transact bitcoins. A Bitcoin wallet is defined as “something that stores the digital credentials for your bitcoin holdings" and allows you to access and spend them. Hence, it is a method of storing and accessing your private key, which then allows you to transact the corresponding Bitcoin. The primary function of Bitcoin wallet is to keep track of your identity. Bitcoin wallet software stores all relevant information about the blockchain. 

The first wallet program, simply named Bitcoin, and sometimes referred to as the Satoshi client, was released in 2009 by Satoshi Nakamoto as open-source software. After the release of version 0.9, the software bundle was renamed Bitcoin Core to distinguish itself from the underlying network. Bitcoin Core is, perhaps, the best known implementation or client. Alternative clients exist, such as Bitcoin XT, Bitcoin Unlimited, and Parity Bitcoin.

Bitcoin wallets are classified into 2 key categories based on their connectivity to the internet. Hot wallets are connected to the internet and Cold wallets are not.

Hot Wallets

Hot wallets are the Bitcoin wallets which are connected to the internet. They are connected to the Bitcoin network via Full Client or Lightweight Client. 

Some examples of Hot wallets are smartphone apps like Mycelium / AirBitz, online web wallets like eToro.com / coinbase.com / blockchain.info

*   Full Clients verify transactions directly by downloading a full copy of the blockchain. They are the most secure and reliable way of using the network, as trust in external parties is not required. Full clients check the validity of mined blocks, preventing them from transacting on a chain that breaks or alters network rules. However, because of the enormous size and complexity, downloading and verifying the entire blockchain is not suitable for all computing devices.
*   Lightweight Clients consult full nodes to send and receive transactions without requiring a local copy of the entire blockchain. This makes them much faster to set up and allows them to be used on low-power, low-bandwidth devices such as smartphones. When using a Lightweight wallet, however, the user must trust full nodes, as it can report faulty values back to the user. Lightweight clients follow the longest blockchain and do not ensure it is valid, requiring trust in full nodes.
*   3rd party internet services called online wallets or web wallets offer similar functionality but may be easier to use. The credentials to access funds are stored with the online wallet provider rather than on the user's hardware. The user must have complete trust in the online wallet provider. A malicious provider or a breach in server security may cause entrusted bitcoins to be stolen , for example, the Mt. Gox security breach occurred in 2011.

Cold Wallets

Wallet software is targeted by hackers because of the lucrative potential for stealing bitcoins. A technique called "Cold Storage" keeps private keys out of reach of hackers; this is accomplished by always keeping private keys offline, by generating them on a device that is not connected to the internet.  

The credentials necessary to spend Bitcoins can be stored offline in several different ways, from specialized hardware wallets to simple paper printouts of the private key. 

*   Paper wallets – A paper wallet is created with a keypair generated on a computer with no internet connection; the private key is written or printed onto the paper and then erased from the computer. This paper wallet can then be stored in a safe physical location for later retrieval. Paper wallets can be generated on websites like bitcoinpaperwallet.com / bitaddress.org. These websites require to download the entire website and run the program locally after disconnecting the computer from the network. They also warn of smart printers and operating systems that might cache the file or be compromised. Physical wallets can also take the form of metal token coins with a private key accessible under a security hologram in a recess struck on the reverse side. The security hologram self-destructs when removed from the token, showing that the private key has been accessed. 
*   Hardware wallets – A hardware wallet is a computer peripheral that signs transactions as requested by the user. The hardware wallet store private keys and carry out signing and encryption in a trusted execution environment that run separately from the computer and never touches the internet. Hence, they do not share any sensitive information with the host computer except already digitally signed transactions. Because hardware wallets never expose their private keys, even computers that may be compromised by malware do not have a vector to access or steal them. The user sets a passcode when setting up a hardware wallet. As hardware wallets are tamper-resistant, the passcode will be needed to extract any money. Some example of hardware wallets are Ledger, Trezor, Case, and Keep Key, which are devices that plug into the computer via USB to digitally sign transactions. 

For enhanced security, to further lessen the probability of someone finding your private key, key stretching can be employed, which hashes the wallet several times. Not only the attacker would have to guess the initial passcode, he will have to guess how many times it has been hashed, making it exponentially difficult to guess the private key.

Lightweight Wallet Mechanics 

In case of lightweight or 3rd party clients, you do not need to download the entire Bitcoin blockchain. You can leverage Simple Payment Verification (SPV) method to verify if transactions are included in a block by simply downloading the block headers of each block instead of the entire block. This is very useful for clients that are constrained by storage capacity as they do not need to store the full blockchain. 

One assumption you need to make while using SPV is that incoming block headers are not from a false chain. In case the block headers are fake or from a false chain, then the transaction you see as valid may not be so, and someone can double spend you. However, as long as you are connected to multiple nodes, the probability of each node being controlled by a malicious entity is significantly low.

Wallet Backups

*   JBOK Wallets – In case you have multiple key, how do you manage them, especially if you make frequent transactions on Bitcoin? The traditional way to keep track of the keys is through JBOK (Just a Bunch of Keys) wallets. A JBOK wallet is a form of Bitcoin wallet which randomly generates new, unrelated keys as needed for the user. JBOK wallets were the earlier wallets that were introduced on the bitcoin blockchain, but proved cumbersome to use as the users would have to store every key pair.
*   Hierarchical Deterministic (HD) wallet – A Hierarchical Deterministic (HD) wallet is the term used to describe a wallet which uses a seed to derive public and private keys. HD wallets can be backed up by storing a single seed of 64 bytes. The term hierarchical describes the tree-like structure of the keys: the wallet seed derives a single master key, which is used to derive child keys, each which can derive their own children. Each child key in the tree can be described by its derivation path, which contains information about a key’s depth and index—where it resides within the tree structure. The derivation path tells a wallet how to derive a specific key.

## Bitcoin Mining

Bitcoin Mining is a record-keeping service done using computer processing power. Miners keep the blockchain consistent, complete, and unalterable by repeatedly grouping newly broadcast transactions into a block, which is then broadcast to the network and verified by recipient nodes. Each block contains a SHA-256 cryptographic hash of the previous block, thus linking it to the previous block and giving the blockchain its name. 

The steps of Bitcoin mining are as follows:

1.  Step 0: The preliminary step is downloading the entire Bitcoin blockchain. This allows the miner to know the Bitcoin history such that he can verify future transactions. 

This is known as Step 0 for two reasons

*   It only needs to be done once. Once a miner has a full Bitcoin blockchain history, he doesn’t need to download it again. He only needs to track the incoming blocks from other miners. 
*   Moreover, the miner with SPV node only needs to store the block headers and request information from full nodes for verifying transactions. Meaning this step is optional.

2.  Step 1 – This step is to verify the valid transactions in the network. Bitcoin users constantly send new transactions to the Bitcoin network, and it is the duty of miners to validate all these transactions. 

As miners receive transactions, they store them in a “mempool” where “mem” means memory and “pool” means supply of transactions. All pending transactions are stored in mempool before making there way into a block. Miners then choose which transaction to validate, based on their transaction fees, and verify the validity of transactions by running the unlocking script. This script successfully unlocks the previous Bitcoins, and the transaction goes through.

3.  Step 2 – After validating the transaction, it is time to generate a block with these transactions. There are several pieces of information needed to construct a block; like Merkle Root which is generated from the list of transactions, hash, time-stamp, version, and target address.

![](Images/image00253.gif)

*   Step 3 – This step entails the Proof-of-Work (PoW) by finding a number called a nonce (number used once) that solves the partial preimage hash puzzle. This nonce makes the hash of the block header less than some target value (when the block content is hashed along with the nonce, the result is numerically smaller than the network's difficulty target).

![](Images/image00254.gif)

By finding the nonce, the miner would have translated the energy burned in the computation directly into the voting power of the P-o-W consensus protocol. 

*   Step 4 – After finding the nonce, the miner broadcast his block as soon as possible to the entire network, if any competitor hasn’t yet broadcasted their block, and such that the other miners are aware that a new block has been found. These miners validate the block themselves before accepting it to their own blockchain, and then broadcast it again. By broadcasting this block, other miners abandon their previous block and start to mine on this new longest chain.

![](Images/image00255.gif)

Broadcasting of block by all modes; Source – CB Insights

 

*   Step 5 – Once the P-o-W is verified by the network, the block getting appended to the longest chain. Once this happens, the miner receives the block reward, represented by the coinbase transaction and the transaction fees. All the transaction within that block are added to the transaction history, and the miner receiving some Bitcoins as a profit.

A situation can arise when 2 blocks, that were submitted to the network at the same time, are competing with one another. In this case, the miners chose randomly between the 2 blocks. Also if the block is orphaned or not in the longest chain, then the miner gets no profit.

This proof is easy for any node in the network to verify, but extremely time-consuming to generate, as for a secure cryptographic hash, miners must try many different nonce values before a result happens to be less than the difficulty target. By adjusting this difficulty target, the amount of work needed to generate a block can be changed. Every 2,016 blocks (approximately 14 days given roughly 10 minutes per block), nodes deterministically adjust the difficulty target based on the recent rate of block generation, with the aim of keeping the average time between new blocks at ten minutes. In this way the system automatically adapts to the total amount of mining power on the network. 

The proof-of-work system, alongside the chaining of blocks, makes modifications of the blockchain extremely hard, as an attacker must modify all subsequent blocks in order for the modifications of one block to be accepted. As new blocks are mined all the time, the difficulty of modifying a block increases as time passes and the number of subsequent blocks (also called confirmations of the given block) increases.

Mining Incentives

Any type of incentive mechanism withing the blockchain protocol aligns personal profit with overall profit. Every miner in the network is trying to maximize the value of his profit. 

Bitcoin Profit = Bitcoin Revenue – Bitcoin Cost

Bitcoin Revenue = Block Reward + Transaction Fees

Bitcoin Cost = Fixed Cost + Variable Cost

*   Block Reward – Block Reward is the most significant source of revenue for the Bitcoin miners. It is the reward that the miner gets once his block is included in the longest chain.

Since the maximum number of bitcoins that can be is 21 million, and new blocks are created approximately every 10 minutes, so by design the number of bitcoins minted per block is reduced by 50% after every 210,000 blocks, or about once every four years. The Block Reward was 50 Bitcoins when Bitcoin was first established, and has since decreased to 6.25 Bitcoins as of May 2020.

The miner includes a special transaction to themselves, the coinbase transaction. It allows for minting of Bitcoins, as well as incentivizing honest actors to validate blocks. Because miners get rewarded for adding new blocks, they are incentivized to produce more blocks.

*   Transaction Fees – Every Bitcoin transaction spends 0 or more Bitcoins to 0 or more recipients. The difference between the amount being spent and the amount being received is the transaction fee. Bitcoin's design makes it easy and efficient for the spender to specify how much fee to pay, whereas it would be harder and less efficient for the recipient to specify the fee, so by custom the spender is almost always solely responsible for paying all necessary Bitcoin transaction fees. When a miner creates a block, he is entitled to specify where all the fees paid by the transactions in that block should be sent. If the transaction results in a valid block that becomes a part of the longest block chain, the fee income will be sent to the specified recipient. If a valid block does not collect all available fees, the amount not collected are permanently destroyed.
*   Fixed Costs – The cost of the hardware, that allows users to mine Bicoins, is the fixed cost. There are different types of hardware ranging from computation devices to specialized mining farms. The first type of mining hardware is the CPU (Central Processing Unit). As of late 2021, mining with CPU would take more than 10 million years to find a block. This is because there are much more powerful hardware, and it makes extremely hard for CPU to compete with them. The next type of hardware is GPU (Graphic Processing Unit). These devices are used for processing media and are also generic computation devices. They can hash 10 times faster than the CPU. It would take GPU ~ 1 million years to find a block. The third type of hardware is FPGA (Field Programmable Gate Arrays). They were the first specialized mining hardware and were optimized for mining Bitcoin. However FPGA were only used briefly as much powerful hardware came into the market in 2014. The fourth type of hardware is ASICS (Application Specific Integrated Circuits). They are fully specialized devices that only do Bitcoin mining. They can be heavily customized, ranging from choosing a lower base cost to higher electricity usage, or choosing a smaller device for a lower hash-rate. They have high upfront cost and need to be purchased in tremendous batches to make a reasonable profit. 
*   Operational Costs – The main component of the operational cost is the Energy cost. There are different type of costs of energy consumed in the process of Bitcoin mining, all of which are considerations for the cost of mining Bitcoin. There are three type of energy costs: Embodied energy is consumed to produce hardware, electricity is used to power hardware, and cooling is used to maintain hardware as it heats up. The electricity and the cooling are the variable energy costs that constitute the major portion of the operating cost. On top of that, there is infrastructure and overhead to maintain as well, such as rental cost and employee salary cost. 

ASICS

Bitcoin mining Application Specific Integrated Circuits (ASICs) are highly specialized and powerful computers used to mine Bitcoin. Nowadays, all the standard Bitcoin mining farms consist of ASICs. Otherwise, it is never profitable. 

![](Images/image00256.jpeg)

Bitcoin ASICS Mining Farm; Source: Bitcoin.com

The above picture illustrates that Bitcoin mining has become very industrial, in order to reduce costs and thereby increase profits. The racks are for systematic allocation of hardware, and the giant fans above the racks are for cooling. There are 2 methods of cooling: water cooling and air cooling. Water cooling is more expensive and offers better maintenance of hardware. In order to reduce the cost, miners choose places where the climate is cold and where the electricity costs are low.

One of the most powerful Bitcoin ASICS is Antminer S9, with the capacity of 14 trillion hashes per second. Its production company, BITMAN, claims that Antminer S9 has provided ~ 70% of the world’s mining power in hardware. However, even with such strong device it takes considerable time to find a block.

Mining Pool

A mining pool is a joint group of cryptocurrency miners who combine their computational resources over a network to increase the probability of finding a block. Hence, mining pools allow these miners to join their hash power together. If the mining pool is successful and receives a reward, that reward is divided among participants in the pool. These rewards are usually divided between the miners who contributed, according to the proportion of each miner's processing power or work relative to the whole group. In some cases, individual miners must show PoW to receive their rewards.

Mining pools are run by a pool manager, that takes care of running a full Bitcoin node and distributing jobs to the miners. The pool manager also takes a cut in rewards as compensation. This way, miners don’t even have to store the blockchain themselves: similar to cloud computing, they give the mining pool access to their hardware in exchange for a share of profit from the mining pool.

The miners in the mining pool are trying to solve the problem based on Merkle Root, and hashing everything in the block header.  The miners can prove that they are working for the mining pool through shares. Shares are defined as near-valid or valid blocks. For example, a miner just found a block hash with half as many leading zeroes as a valid block. Mining pool can use this information to gauge how much mining power this miner has contributed and reward him for valid shares. This way the miner gets paid even if he never finds a valid block, because these near-valid blocks are indicators that he at least tried to find a block. 

The rewards are given through a coinbase transaction. The hash puzzle contains a coinbase transaction that pays block reward to the pool manager. The pool manager redistributes this block reward to the miners. 

Mining Pool Payout Methods

There are a number of common protocols that govern many of the most popular mining pools.

*   Proportional Mining Pools – In this type of pool, miners contributing to the pool's processing power receive shares up until the point at which the pool succeeds in finding a block. After that, miners receive rewards proportional to the number of shares they submitted before the block was found. This method is more advantageous for the mining pool, as they do not need to pay more money than they get, but it leads to more variance and risks for miners.
*   Pay-per-share Pools – They operate somewhat similarly in that each miner receives shares for their contribution. However, these pools provide instant payouts regardless of when the block is found. A miner contributing to this type of pool can exchange shares for a proportional payout at any time. The payment is guaranteed and constant per share, regardless of how much reward the mining pools makes. Most mining pools use this method as it is easy to implement. 
*   Peer-to-peer Mining Pools – They integrate a separate blockchain related to the pool itself and designed to prevent the operators of the pool from cheating as well as the pool itself from failing due to a single central issue.

Benefits of a Mining Pool

While success in individual mining grants complete ownership of the reward, the odds of achieving success is very low because of high power and resource requirements. Mining is often not a profitable venture for individuals. Many cryptocurrencies have become increasingly difficult to mine in recent years as the popularity of these digital currencies has grown and the costs associated with expensive hardware necessary to be a competitive miner as well as electricity oftentimes outweigh the potential rewards. Mining pools require less of each individual participant in terms of hardware and electricity costs and increase the chances of profitability. Whereas an individual miner might stand little chance of successfully finding a block and receiving a mining reward, teaming up with others dramatically improves the success rate.

On top of that, software changes are easy to implement, as only one person is running a full node for the mining pool, and can upgrade on the behalf of the mining pool.

Disadvantages of a Mining Pool

By taking part in a mining pool, individuals give up some of their autonomy in the mining process. They are typically bound by terms set by the pool itself, which may dictate how the mining process is approached. They are also required to divide up any potential rewards, meaning that the share of profit is lower for an individual participating in a pool.

Also, the miners need to rely on the pool managers, not to misuse their mining power and not to withhold rewards. This is the consequence of centralization. A small number of mining pools, such as AntPool, Poolin, and F2Pool dominate the bitcoin mining process, according to blockchain.com. Although many pools do try to be decentralized, these groups consolidate much of the authority to govern the Bitcoin protocol. For some cryptocurrency proponents, the presence of a small number of powerful mining pools goes against the decentralized structure inherent in Bitcoin.

Another disadvantage is that a single entity might be hiding their total amount of mining power. This is known as laundering hashes, by hiding the original mining power. This allows the miner to leverage greater amount of mining power without revealing his prowess to the mining pool network and receive higher profits in return.

## Bitcoin Governance

One of the biggest feature of Bitcoin is Decentralization. However Bitcoin mining is becoming more and more centralized with the development of ASICs, mining pools, and mining farms. ASICs are centralized in a sense as they are very expensive and only very few people can acquire them. Mining pools and mining farms on the other hand are centralized as they are run by single entities.

This problem can be solved attempting to redesign the underlying hash puzzles. A puzzle should be hard to solve but easy to verify. This difficulty should be adjusted to account for the changes in the mining technology (e.g. – ASICs). A puzzle should also be “progress free” meaning that finding a hash does not make it easier to find the next hash. Lastly, the puzzle should be pseudo randomly generated.

ASIC Resistance

The original idea of Bitcoin mining was “1 CPU 1 Vote” making it truly decentralized. The rise of ASICs has diminished it, giving some people more votes than other. 

ASICs work because it is easy to create hardware to compute a certain puzzle. They are computation bound. A way to solve the problem of ASIC dominance is to make puzzles that not only rely on computation speed, but also on memory, giving rise to the notion of memory-hard and memory-bound problems. A memory-hard problem is the one that needs a large amount of requisite money to solve. A memory-bound problem is the problem that scales based on the amount of memory you have. These problems deter ASICs as optimizing computation power is useless if memory is the limit agent.

New cryptocurrencies like Dogecoin and Litecoin have implemented memory-bound hash function called Scrypt. They use a partial hash-preimage puzzle like in Bitcoin, just with a different hash function. Hence, Bitcoin ASICs cannot work for Dogecoin or Litcoin. 

Scrypt has 2 main steps:

1.  Fill a buffer with interdependent data
2.  Access that data in a pseudo random way

Scrypt was originally designed to secure passwords and make them hard to brute force, so a memory-bound type of problem makes sense. A password-based key derivation function (KDF) is generally designed to be computationally intensive, so that it takes a relatively long time to compute. Legitimate users only need to perform the function once per operation, and so the time required is negligible. However, a brute-force attack would likely need to perform the operation billions of times, at which point the time requirements become significant and, ideally, prohibitive. Previous password-based KDFs have relatively low resource demands, meaning they do not require elaborate hardware or very much memory to perform. This allows an attacker with sufficient resources to launch a large-scale parallel attack by building hundreds or even thousands of implementations of the algorithm in hardware and having each search a different subset of the key space. This divides the amount of time needed to complete a brute-force attack by the number of implementations available, very possibly bringing it down to a reasonable time frame.

The Scrypt function is designed to hinder such attempts by raising the resource demands of the algorithm. Specifically, the algorithm is designed to use a large amount of memory compared to other password-based KDFs, making the size and the cost of a hardware implementation much more expensive, and therefore limiting the amount of parallelism an attacker can use, for a given amount of financial resources.

However, Scrypt has its drawbacks too. It requires an equal amount of memory to verify, which is not ideal as the puzzles should be easy to verify. In addition, even though Scrypt was developed to be ASIC resistant, an ASIC has actually been developed for it.

Another idea to achieve ASIC resistance is to chain a multiple hash functions together, as it is much harder to create an ASIC that deals with multiple has function and not just one. This was the idea behind x11 and x13, which chain together 11 and 13 different hash functions. Another idea to make ASIC resistant systems was to design coins that periodically switched mining puzzles. Making it difficult to optimize. For example, switching from SHA-1 to SHA-3 to Scrypt every month. However, the overhead cost to create such an algorithm is very high and have deterred people from implementing it.

A counter argument to ASIC resistance is that since ASICs are designed solely to solve a cryptographic puzzle, they are incapable of anything else. Miners who own them are thus committed to the network. If a system with a large number of miners switch from ASIC switches to an ASIC resistant environment, then the exchange rate of Bitcoin will crash, and many miners will suddenly be left with useless ASIC devices with no incentive to mine anymore. 

Eliminating Waste

Since so much computational power is used to solve cryptographic puzzles, for just finding random numbers, why not make puzzles which can do useful task. For example, miners can search for large primes, stimulate proteins at atomic level, look for aliens, or generate predictive climate models. 

 
| Project || Founded || Goal || Impact |
| --- | --- | --- | --- |
| Great Internet Mersenne Prime Search || 1996 || Finding large Mersenne primes || Found the new ‘largest prime number’ 12 straight times |
| Distributed.net || 1997 || Cryptographic brute-force demos || First successful public brute-force of a 64 but cryptographic key |
| SETI || 1999 || Identifying signs of extraterrestrial life || Largest project to date with over 5 million participants |

 

These problems could be solved much faster by using the computational power of the Bitcoin network. 

However, there are some issues. These distributed computing problems are usually unsuitable for PoW and don’t work as cryptographic puzzles. There is fixed amount of data in the system, leading to a finite number of solutions to the problem. If someone finds a solution to a particular problem, what happens then? or if there is not enough data to find a solution?These puzzles cannot be used for PoW anymore.

In Bitcoin, since the puzzle is based on the previous block, the problem space is inexhaustible. In contrast, if we use SETI for our puzzle, we could run out of raw radio telescope data, leaving no problem to solve. Let’s assume you are looking for planets in the space. One part of the space can be more populated than others. However in the hash function of Bitcoin, it’s on an average equally difficult to find a solution. 

Lastly, these problems are governed by central entities, as opposed to Bitcoin, whose problems are created by its protocol. When we rely on a central entity to create a problem, it opens up potential for collusion or exploitation.

Hence, PoW is a great idea, but incredibly difficult to implement in real life scenarios.

Consensus Updates

The idea behind a consensus update is that Bitcoin is decentralized, no single entity can influence any updates in the protocol. Everyone is the network has to agree and come to a consensus for an update to happen.

This brings us to two ways that blockchains can be updated.

*   Hard forks – A hard fork result from a new protocol that does things not allowed in the old protocol. In other words, a hard fork is not backwards compatible. For example, Bitcoin Cash increasing the block size from 1 Mb to 8 Mb. The nodes on the old, legacy Bitcoin protocol are going to refuse the new 8 Mb blocks, leading to a permanent fork as shown in the figure.

![](Images/image00257.gif)

These 2 forks would then theoretically continue forever as long as both the blockchains have support, and miners who continuously run the software. 

*   Soft forks – In Soft forks, the rules of the new protocol are only restrained. For example, if a new Bitcoin fork were to reduce the block size by half Mb, then everything valid in the new protocol is still valid in the old protocol. However, the old protocol’s blocks are no longer valid in the new protocol, meaning that a soft fork is backward compatible but not forward compatible. As shown in the figure, the new and old nodes will accept blocks from the new protocol, but the old nodes will never have their blocks accepted into the longest chain mined by the new nodes. 

![](Images/image00258.gif)

Bitcoin Improvement Proposals (BIP)

In Bitcoin, changes to the protocols come in the form of Bitcoin Improvement Proposals (BIP). These can be changes in the network protocol, block or transaction validation, or anything affecting interoperability. Miners vote on the BIP by including a reference to that BIP in the block they mine. There are three type of BIPs:

*   Standard BIP – An actual upgrade or change to the Bitcoin protocol. This is how the Bitcoin ecosystem changes, and what the miners vote on.
*   Informational BIP – Guidelines on how people should do things in future, but no change to the Bitcoin protocol
*   Process BIP – Specific best practices to the Bitcoin protocol

 

# Blockchain based cryptocurrency – Ethereum 

After Bitcoin, the next most popular blockchain platform in Ethereum. 

In this chapter, we will discuss Ethereum and its history. We will learn about smart contracts and how they are enabled by Ethereum. We will gain an insight on Ethereum design and how it is different from Bitcoin. We will gain an insight on Ethereum mining and Ethereum Virtual Machine (EVM). Finally, we will discuss on Ethereum use cases across industries and the Ethereum ecosystem.

Bitcoin's primary use case is to store value and as a digital currency. Ethereum was also created as a mode of payment and to store value as a digital currency, however Ethereum network also makes it also possible to create and run decentralized applications and execute “peer-to-peer” Smart Contracts. 

Ethereum platform allows anyone to deploy permanent and immutable decentralized applications onto it, with which users can interact. 

*   This enables people to deploy Decentralized finance (DeFi) applications onto the Ethereum platform and provide variety of financial services without the need for intermediaries like brokerages, exchanges, or banks.
*   Ethereum also allows for the creation and exchange of Non Fungible Tokens (NFTs), which can be used to buy / sell digital products, digital media, digital art, or any other real-world items sold as a unique digital property. 
*   Ethereum platform also offers other cryptocurrencies to operate as ERC-20 tokens on top of the Ethereum blockchain.

Ether, the native cryptocurrency of the Ethereum platform, is second only to Bitcoin in market capitalization. 

## Smart Contracts

A “contract” is a written or spoken agreement that is intended to be enforced by law. For a contract to be valid, it must be agreed upon. Hence, a contract is in itself a consensus mechanism. Through consensus, all the parties involved in the contract should be able to agree upon the contents of the contract, as well as its execution.

What makes a contract smart? 

A smart contract is a self-executing contract with the terms of the agreement between buyer and seller being directly written into lines of code. This code facilitates, verifies, and enforces the execution of the contract. The code and the agreements contained therein exist across a distributed, decentralized blockchain network. The code controls the execution, and transactions are trackable and irreversible.

Like a traditional contract, a Smart contract carries a set of conditions / terms that must be fulfilled. The difference is that the execution and enforcement of the contract is done through carefully designed algorithms, and not through law. Hence, Smart contracts permit trusted transactions and agreements to be carried out among disparate, anonymous parties without the need for a central authority, legal system, or external enforcement mechanism.

Smart contracts were first proposed in 1994 by Nick Szabo, an American computer scientist who invented a virtual currency called "Bit Gold" in 1998, fully 10 years before the invention of bitcoin. Szabo defined smart contracts as computerized transaction protocols that execute terms of a contract. He wanted to extend the functionality of electronic transaction methods, such as POS (point of sale), to the digital realm. In his paper, he also proposed the execution of a contract for synthetic assets, such as derivatives and bonds. Szabo wrote: "These new securities are formed by combining securities (such as bonds) and derivatives (options and futures) in a wide variety of ways. Very complex term structures for payments can now be built into standardized contracts and traded with low transaction costs, due to computerized analysis of these complex term structures."

Smart contracts in Ethereum are like autonomous agents that live inside the Ethereum network. They react to the external world when they are poked by transactions, which cause specific functions. They have direct control over an internal Ether balance, internal contract state, and also permanent storage. They generally service four main purposes:

*   They can be used to store and maintain data. This data represents something useful to users or other contracts. For example, there could be a smart contract defining a new token currency, or a certain organization’s membership, etc.
*   They can be used to manage a contract or a relationship between untrusting users. Its simply running a regular contract but on the distributed Ethereum network. For example, you can have smart contracts that manage financial contracts, escrow accounts, or insurance premiums.
*   Smart contracts can be written to call other contracts, using them as a software library, leveraging the functionality of an existing contract.
*   Smart contracts can be used for complex authentication use cases. For example, you can define a ‘m’ of ‘n’ multi-signature using a smart contract.

## Ethereum Overview

Ethereum is a decentralized, open-source blockchain platform to run smart contracts. In short, it’s a distributed computer spread amongst multitude of nodes across the world executing codes that people feed into it, and because of this architecture, it can run unstoppable applications. Applications are run on the Ethereum platform exactly as programmed, without any possibility of downtime, censorship, fraud, or 3rd party intervention. Formally, Ethereum is implemented as a distributed state machine, and transaction on its network change the global state of the system. Nodes in the Ethereum network keep track of and come to consensus on the global system state, which includes data about who owns what.  

Like Bitcoin, Ethereum is trustless, immutable, uncensorable, pseudonymous, and has no central point of failure. It supports a Turing complete language.

Ethereum’s native cryptocurrency is Ether (ETH), which is the basis of value in the Ethereum ecosystem, and also crucial in aligning incentives. Amongst cryptocurrencies, Ether is second only to Bitcoin in market capitalization.

Ethereum History

Ethereum was first described by Vitalik Buterin, a programmer from University of Waterloo and co-founder of Bitcoin magazine, in late 2013, in a white paper with the objective of building decentralized applications. Buterin argued that the blockchain technology needed a more robust language for application development that could lead to attaching real-world assets, such as stocks and property, to the blockchain. He proposed the development of a new platform with a more robust scripting language—a Turing-complete protocol, that would eventually become Ethereum.

Ethereum was announced at the North American Bitcoin Conference in Miami, in January 2014. The platform had a token sale between July and August 2014 and sold 7.4 million ether for 3700 Bitcoins in the first 12 hours of its presale. 

Several codenamed prototypes of Ethereum were developed over 18 months in 2014 and 2015 by the Ethereum Foundation as part of their proof-of-concept series. The "Olympic" network was the last prototype and public beta pre-release, and provided users with 25,000 Ether for stress testing the limits of the Ethereum blockchain. The Ethereum blockchain officially went live on 30th July 2015 with creation of its genesis block, and by May 2016, the cumulative value of Ethereum tokens was more than $1 billion.

Around that time, the idea of Decentralized Autonomous Organizations (DAO), which were programs on the Ethereum blockchain that created a distributed government, became immensely popular. In 2016, a decentralized autonomous organization called The DAO, developed a set of smart contracts on the platform and raised $150 million to fund the project. However in July 2016, an unknown hacker exploited a bug in the underlying code, and stole around $120 million of Ether. The event sparked a debate in the crypto-community about whether Ethereum should defy the protocol and undo the hack, or not to undo the activity with the belief that “code is law”. 

This resulted in the network splitting into two blockchains: The split that reversed the theft is currently branded as Ethereum, and the split that continued on the original chain became know as Ethereum Classic. After the reversal, Ethereum subsequently reversed twice in the fourth quarter of 2016 to deal with other attacks.

In March 2017, various blockchain startups, research groups, and Fortune 500 companies announced the creation of the Enterprise Ethereum Alliance (EEA) with 30 founding members. The advent of cryptocurrency exchange-traded-funds (ETF) meant that an average person could now invest in cryptocurrency without having to worry about dealing with exchanges and storing the tokens. Ethereum platform also enabled multiple Initial Coin Offerings (ICO), raising around $ 1.3 billion with 150 ICOs in the third quarter of 2017. 

In December 2017, cryptocurrencies started attracting much more mainstream attention, and led to increase in the number of millennials investing in Ether. They did not want to miss in the next Bitcoin, and ended up investing in Ether, driving its price up in a feedback loop. In January 2018, Ethereum was the second largest cryptocurrency by market capitalization, behind Bitcoin. 

In March 2021, Visa Inc. announced that it began settling transactions using Ethereum. In April 2021, JP Morgan Chase, UBS, and MasterCard announced that they were investing $65 million into ConsenSys, a software development firm that builds Ethereum-related infrastructure.

There were two network upgrades in 2021. The first was the "Berlin" upgrade and the second was "London" upgrade. The “London” upgrade introduced a mechanism for reducing transaction fee volatility. The mechanism causes a portion of the Ether paid in transaction fees each block to be destroyed rather than given to the miner, reducing the inflation rate of Ether. 

As of 2022, Ether is the 2nd most valued cryptocurrency after Bitcoin, with a market cap of around $ 400 billion.

Open-source development is currently underway for a major upgrade to Ethereum known as Ethereum 2.0 or Eth2. The main purpose of the upgrade is to increase transaction throughput for the network from the current of about 15 transactions per second to up to tens of thousands of transactions per second, by splitting up the workload into many blockchains running in parallel (referred to as sharding) and then having them all share a common consensus Proof-of-Stake blockchain, so that to maliciously tamper with any singular chain would require one to tamper with the common consensus, which would cost the attacker far more than they could ever gain from an attack.

Ethereum 2.0 is designed to be launched in three phases:

*   "Phase 0" also known as "The Beacon Chain" was launched on 1 December 2020 and created the Beacon Chain, a Proof-of-Stake (PoS) blockchain that will act as the central coordination and consensus hub of Ethereum 2.0.
*   "Phase 1" also known as "The Merge" will merge the Beacon Chain with the current Ethereum network, transitioning its consensus mechanism from PoW to PoS. It is expected to be released in the first half of 2022.
*   "Phase 2" also known as "Shard chains" will implement state execution in the shard chains with the current Ethereum 1.0 chain expected to become one of the shards of Ethereum 2.0. Shard chains will spread the network's load across 64 new chains. It is expected to be released in 2022.

Design Overview

Ethereum is a permissionless, non-hierarchical network of computers (nodes) which build and come to consensus on an ever-growing series of "blocks" in the blockchain. Each block contains an identifier of the chain that must precede it if the block is to be considered valid. Whenever a node adds a block to its chain, it executes the transactions therein in their order, thereby altering the ETH balances and other storage values of Ethereum accounts. These balances and values, collectively known as the state, are maintained on the node's computer separately from the blockchain, in a Merkle tree.

Each node communicates with a relatively small subset of the network, known as its peers. Whenever a node wishes to include a new transaction in the blockchain, it sends the transaction to its peers, who then send it to their peers, and so on. In this way, it propagates throughout the network. Certain nodes, called miners, maintain a list of all these new transactions and use them to create new blocks, which they then send to the rest of the network. Whenever a node receives a block, it checks the validity of the block and of all the transactions therein and, if valid, adds it to its blockchain and executes all of said transactions. As the network is non-hierarchical, a node may receive competing blocks, which may form competing chains. The network comes to consensus on the blockchain by following the "longest-chain rule", which states that the chain with the most blocks at any given time is the canonical chain. This rule achieves consensus because miners do not want to expend their computational work trying to add blocks to a chain that will be abandoned by the network.

Ether

Ether (ETH) is the cryptocurrency generated by the Ethereum protocol as a reward to miners in a Proof-of-Work system for adding blocks to the blockchain. It is the only currency accepted in the payment of transaction fees, which also go to miners. The block reward together with the transaction fees provide the incentive to miners to keep the blockchain growing. Each Ethereum account has an ETH balance and may send ETH to any other account. There is currently no implemented hard cap on the total supply of Ether. The denominations of Ether are as follows:

*   1: wei
*   10^12: szabo
*   10^15: finney
*   10^18: ether

The issuance model was as follows:

*   Ether released in a currency sale at the price of 1000-2000 Ether per BTC, a mechanism intended to fund the Ethereum organization and pay for development that has been used with success by other platforms such as Mastercoin and NXT. The Bitcoin received from the sale used entirely to pay salaries and bounties to developers and invested into various for-profit and non-profit projects in the Ethereum and cryptocurrency ecosystem.
*   0.099x the total amount sold (60102216 ETH) allocated to the organization to compensate early contributors and pay Ether denominated expenses before the genesis block.
*   0.099x the total amount sold maintained as a long-term reserve.
*   0.26x the total amount sold allocated to miners per year forever after that point.

 
| Group || At launch || After 1 year || After 5 years |
| --- | --- | --- | --- |
| Currency units || 1.198X || 1.458X || 2.498X |
| Purchasers || 83.5% || 68.6% || 40% |
| Reserve spent pre-sale || 8.26% || 6.79% || 3.96% |
| Reserve used post-sale || 8.26% || 6.79% || 3.96% |
| Miners || 0% || 17.8% || 52% |

![Ethereum inflation](Images/image00259.jpeg)

Despite the linear currency issuance, just like with Bitcoin over time the supply growth rate nevertheless tends to zero;

 Source – Ethereum.org/whitepaper/

Addresses

Ethereum addresses are composed of the prefix "0x", a common identifier for hexadecimal, concatenated with the rightmost 20 bytes of the 256 hash of ECDSA public key. In hexadecimal, two digits represent a byte, meaning addresses contain 40 hexadecimal digits. Contract addresses are in the same format, however, they are determined by sender and creation transaction nonce.

Ethereum vs. Bitcoin

Ethereum and Bitcoin are the two most popular blockchain platforms in the world today. However, both have different goals. Bitcoin is the “gold standard” of blockchain. It has been around for the longest time, and its protocol has successfully supported an enormous number of transactions over the years. It’s intended purpose is solely to allow the transaction of Bitcoins. On the other hand, Ethereum is a Smart contract blockchain platform, a distributed world computer. Its native asset Ether exists to fund computation and to align incentives. Its primary purpose is not to act as a medium of exchange. 

Bitcoin is a global payment system. Ethereum has a much larger vision, and therefore supports many more features, like a much more powerful scripting language. Moreover, Bitcoin has a stack based primitive scripting language which is not Turing complete, meaning that the applications made on the Bitcoin platform are pretty limited. Ethereum on the other hand has a Turing-complete scripting language. So a wider variety of applications can be made on Ethereum platform compared to Bitcoin, making it more developers’ friendly. 

Another key difference is that Bitcoin is UTXO based, whereas Ethereum is account based.

In Bitcoin, private keys prove ownership of UTXOs. Whenever you spend your Bitcoin, you spend from previous transactions. And to calculate your current balance, you have to sum up all the UTXOs you own. The reason Bitcoin uses UTXOs is for easier transactions and to avoid double spending. 

In Ethereum, private keys prove ownership of an account, which tracks the current balance. Accounts are made more space efficient than UTXOs, since to calculate your balance, you only need to reference to your account, rather than summing up all your UTXOs. Also, since the ultimate goal is to support smart contracts, it is much cheaper and easier to look up an account balance, and transfer between accounts using an account model rather than a UTXO model.

## Ethereum Design

The intent of Ethereum is to create a protocol for building decentralized applications, providing a different set of tradeoffs that are very useful for a large class of decentralized applications, with particular emphasis on situations where rapid development time, security for small and rarely used applications, and the ability of different applications to very efficiently interact, are important. 

Ethereum does this by building what is essentially the ultimate abstract foundational layer: a blockchain with a built-in Turing-complete programming language, allowing anyone to write smart contracts and decentralized applications where they can create their own arbitrary rules for ownership, transaction formats and state transition functions. 

A bare-bones version of Namecoin can be written in two lines of code, and other protocols like currencies and reputation systems can be built in under twenty. 

Smart contracts, cryptographic "boxes" that contain value and only unlock it if certain conditions are met, can also be built on top of the platform, with vastly more power than that offered by Bitcoin scripting because of the added powers of Turing-completeness, value-awareness, blockchain-awareness and state.

Ethereum Accounts

In Ethereum, the state is made up of objects called "accounts", with each account having a 20-byte address and state transitions being direct transfers of value and information between accounts. 

An Ethereum account contains four fields:

*   The nonce, a counter used to make sure each transaction can only be processed once
*   The account's current Ether balance
*   The account's contract code, if present
*   The account's storage (empty by default)

In general, there are two types of accounts: externally owned accounts, controlled by private keys, and contract accounts, controlled by their contract code. 

*   Externally owned accounts – As their name suggest, owned by an external entity, outside the Ethereum network. Externally owned accounts use an address that they use to let people send them Ether, and also as a balance of Ether. This type of account can send transactions to transfer Ether or to trigger contract code. An externally owned account has no code, and one can send messages from an externally owned account by creating and signing a transaction
*   Contract accounts – They are owned by smart contracts. They contain an address, associated contract code, and also persistent storage. In a contract account, every time the contract account receives a message its code activates, allowing it to read and write to internal storage and send other messages or create contracts in turn. 

Note that "contracts" in Ethereum should not be seen as something that should be "fulfilled" or "complied with"; rather, they are more like "autonomous agents" that live inside of the Ethereum execution environment, always executing a specific piece of code when "poked" by a message or transaction, and having direct control over their own Ether balance and their own key/value store to keep track of persistent variables.

Transactions

The term "transaction" is used in Ethereum to refer to the signed data package that stores a message to be sent from an externally owned account. Transactions contain:

*   The recipient of the message
*   A signature identifying the sender
*   The amount of Ether to transfer from the sender to the recipient
*   An optional data field
*   A STARTGAS value, representing the maximum number of computational steps the transaction execution can take
*   A GASPRICE value, representing the fee the sender pays per computational step

The first three are standard fields expected in any cryptocurrency. The data field has no function by default, but the virtual machine has an OPCODE using which a contract can access the data; for example, if a contract is functioning as an on-blockchain domain registration service, then it may wish to interpret the data being passed to it as containing two "fields", the first field being a domain to register and the second field being the IP address to register it to. The contract would read these values from the message data and appropriately place them in storage.

The STARTGAS and GASPRICE fields are crucial for Ethereum's anti-denial of service model. In order to prevent accidental or hostile infinite loops or other computational wastage in code, each transaction is required to set a limit to how many computational steps of code execution it can use. The fundamental unit of computation is "gas"; usually, a computational step costs 1 gas, but some operations cost higher amounts of gas because they are more computationally expensive, or increase the amount of data that must be stored as part of the state. 

There is also a fee of 5 gas for every byte in the transaction data. The intent of the fee system is to require an attacker to pay proportionately for every resource that they consume, including computation, bandwidth and storage; hence, any transaction that leads to the network consuming a greater amount of any of these resources must have a gas fee roughly proportional to the increment.

 

 

Messages

Contracts have the ability to send "messages" to other contracts. Messages are virtual objects that are never serialized and exist only in the Ethereum execution environment. A message contains:

*   The sender of the message (implicit)
*   The recipient of the message
*   The amount of ether to transfer alongside the message
*   An optional data field
*   A STARTGAS value

Essentially, a message is like a transaction, except it is produced by a contract and not an external actor. A message is produced when a contract currently executing code executes the CALL OPCODE, which produces and executes a message. Like a transaction, a message leads to the recipient account running its code. Thus, contracts can have relationships with other contracts in the same way that external actors can.

Note that the gas allowance assigned by a transaction or contract applies to the total gas consumed by that transaction and all sub-executions. For example, if an external actor A sends a transaction to B with 1000 gas, and B consumes 600 gas before sending a message to C, and the internal execution of C consumes 300 gas before returning, then B can spend another 100 gas before running out of gas.

Ethereum State Transition Function

The Ethereum state transition function, APPLY(S,TX) -> S' can be defined in the following steps:

1.  Check if the transaction is well-formed (ie. has the right number of values), the signature is valid, and the nonce matches the nonce in the sender's account. If not, return an error.
2.  Calculate the transaction fee as STARTGAS \* GASPRICE, and determine the sending address from the signature. Subtract the fee from the sender's account balance and increment the sender's nonce. If there is not enough balance to spend, return an error.
3.  Initialize GAS = STARTGAS, and take off a certain quantity of gas per byte to pay for the bytes in the transaction.
4.  Transfer the transaction value from the sender's account to the receiving account. If the receiving account does not yet exist, create it. If the receiving account is a contract, run the contract's code either to completion or until the execution runs out of gas.
5.  If the value transfer failed because the sender did not have enough money, or the code execution ran out of gas, revert all state changes except the payment of the fees, and add the fees to the miner's account.
6.  Otherwise, refund the fees for all remaining gas to the sender, and send the fees paid for gas consumed to the miner.

For example, suppose that the contract's code is:

if !self.storage\[calldataload(0)\]:

    self.storage\[calldataload(0)\] = calldataload(32)

Suppose that the contract's storage starts off empty, and a transaction is sent with 10 Ether value, 2000 gas, 0.001 Ether GASPRICE, and 64 bytes of data, with bytes 0-31 representing the number 2 and bytes 32-63 representing the string CHARLIE. The process for the state transition function in this case is as follows: 

1.  Check that the transaction is valid and well formed.
2.  Check that the transaction sender has at least 2000 \* 0.001 = 2 ether. If it is, then subtract 2 ether from the sender's account.
3.  Initialize gas = 2000; assuming the transaction is 170 bytes long and the byte-fee is 5, subtract 850 so that there is 1150 gas left.
4.  Subtract 10 more ether from the sender's account, and add it to the contract's account.
5.  Run the code. In this case, this is simple: it checks if the contract's storage at index 2 is used, notices that it is not, and so it sets the storage at index 2 to the value CHARLIE. Suppose this takes 187 gas, so the remaining amount of gas is 1150 - 187 = 963
6.  Add 963 \* 0.001 = 0.963 ether back to the sender's account, and return the resulting state.

 

![Ether state transition](Images/image00260.jpeg)

Ethereum State Transition Function example; Source – Ethereum.org/whitepaper/

If there was no contract at the receiving end of the transaction, then the total transaction fee would simply be equal to the provided GASPRICE multiplied by the length of the transaction in bytes, and the data sent alongside the transaction would be irrelevant.

The messages work equivalently to transactions in terms of reverts: if a message execution runs out of gas, then that message's execution, and all other executions triggered by that execution, revert, but parent executions do not need to revert. This means that it is "safe" for a contract to call another contract, as if A calls B with G gas then A's execution is guaranteed to lose at most G gas. 

Note that there is an OPCODE, CREATE, that creates a contract; its execution mechanics are generally similar to CALL, with the exception that the output of the execution determines the code of a newly created contract.

Code Execution

The code in Ethereum contracts is written in a low-level, stack-based bytecode language, referred to as "Ethereum virtual machine code" or "EVM code". The code consists of a series of bytes, where each byte represents an operation. In general, code execution is an infinite loop that consists of repeatedly carrying out the operation at the current program counter (which begins at zero) and then incrementing the program counter by one, until the end of the code is reached or an error or STOP or RETURN instruction is detected. The operations have access to three types of space in which to store data:

*   The stack, a last-in-first-out (LIFO) container to which values can be pushed and popped
*   Memory, an infinitely expandable byte array
*   The contract's long-term storage, a key/value store. Unlike stack and memory, which reset after computation ends, storage persists for the long term.

The code can also access the value, sender and data of the incoming message, as well as block header data, and the code can also return a byte array of data as an output.

Ethereum Mining

![Ethereum apply block diagram](Images/image00261.jpeg)Ethereum Apply block diagram; Source – Ethereum.org/whitepaper/

The Ethereum blockchain is in many ways similar to the Bitcoin blockchain, although it does have some differences. The main difference between Ethereum and Bitcoin with regard to the blockchain architecture is that, unlike Bitcoin, Ethereum blocks contain a copy of both the transaction list and the most recent state. Aside from that, two other values, the block number and the difficulty, are also stored in the block. The basic block validation algorithm in Ethereum is as follows:

1.  Check if the previous block referenced exists and is valid.
2.  Check that the timestamp of the block is greater than that of the referenced previous block and less than 15 minutes into the future
3.  Check that the block number, difficulty, transaction root, uncle root and gas limit are valid.
4.  Check that the Proof-of-Work on the block is valid.
5.  Let S\[0\] be the state at the end of the previous block.
6.  Let TX be the block's transaction list, with n transactions. For all i in 0...n-1, set S\[i+1\] = APPLY(S\[i\],TX\[i\]). If any applications returns an error, or if the total gas consumed in the block up until this point exceeds the GASLIMIT, return an error.
7.  Let S\_FINAL be S\[n\], but adding the block reward paid to the miner.
8.  Check if the Merkle tree root of the state S\_FINAL is equal to the final state root provided in the block header. If it is, the block is valid; otherwise, it is not valid.

The state is stored in the tree structure, and after every block only a small part of the tree needs to be changed. Thus, in general, between two adjacent blocks most of the tree should be the same, and therefore the data can be stored once and referenced twice using pointers (ie. hashes of subtrees). 

A special kind of tree known as a "Patricia tree" is used to accomplish this, including a modification to the Merkle tree concept that allows for nodes to be inserted and deleted, and not just changed, efficiently. Additionally, because all the state information is part of the last block, there is no need to store the entire blockchain history - a strategy which, if it could be applied to Bitcoin, can be calculated to provide 5-20x savings in space.

A commonly asked question is "where" contract code is executed, in terms of physical hardware. This has a simple answer: the process of executing contract code is part of the definition of the state transition function, which is part of the block validation algorithm, so if a transaction is added into block B the code execution spawned by that transaction will be executed by all nodes, now and in the future, that download and validate block B.

Ethash

Ethash is the planned Proof-of-Work (PoW) algorithm for Ethereum. 

The general route that the algorithm takes is as follows:

1.  There exists a seed which can be computed for each block by scanning through the block headers up until that point.
2.  From the seed, one can compute a 16 MB pseudorandom cache. Light clients store the cache.
3.  From the cache, we can generate a 1 GB dataset, with the property that each item in the dataset depends on only a small number of items from the cache. Full clients and miners store the dataset. The dataset grows linearly with time.
4.  Mining involves grabbing random slices of the dataset and hashing them together. Verification can be done with low memory by using the cache to regenerate the specific pieces of the dataset that you need, so you only need to store the cache.

The large dataset is updated once every 30000 blocks, so the vast majority of a miner’s effort will be reading the dataset, not making changes to it. Ethash is memory bound and claims to be ASIC resistant.

## Ethereum Virtual Machine (EVM)

Ethereum smart contracts are generally written in high level programming languages. The most popular is Solidity, which is a mix between C++ and JavaScript. There is also Vyper, which is a newer language currently under development. Smart contract written in these high-level programming languages have to be compile down to the Ethereum Virtual Machine (EVM) code. 

![](Images/image00262.gif)

Hence, we go from a higher level, human readable language, and compile that down to an EVM code, which is a lower level, simpler language, and much easier for a machine to understand and execute.

After this code is compiled into EVM code, every node in the Ethereum network executes it. All the nodes execute the code in the same way, so long as they have an up-to-date version of the EVM software. Nodes them come to consensus on the new system state, by executing the Proof-of-Work protocol. By tying the voting power to the computational power via PoW, Sybil attacks (an attack on a computer network in which an attacker subverts the service's reputation system by creating a large number of pseudonymous identities and uses them to gain a disproportionately large influence) can be prevented. In Ethereum, block creation time is 15 seconds long, compared to 10 minutes in Bitcoin. This allows the execution of smart contracts to be done and finalized quickly. 

EVM Execution

Ethereum miners competitively create blocks by executing the EVM code and searching for a solution to the mining puzzle. Since PoW is a competition, only one miner is able to add the block to the Ethereum network, and claim the block reward.

Every Ethereum node runs the EVM as a part of its block verification process. Contract codes are run by EVM. This allows the contracts to live on the blockchain forever. 

Since EVM is a low level bytecode language, we can compile complex smart contract codes into simple machine understandable instructions in the form of EVM code, that all the nodes in the network can execute in same deterministic way, and come to a consensus.

Also, every EVM OPCODE requires ‘gas’ in order to execute, thereby preventing the infinite loop denial of service attack, where attackers trap the computers in the Ethereum network in a infinite loop, thereby making them unable to execute more meaningful contracts. 

Once the nodes come to a consensus on the network state, the code execution on the EVM changes the state. 

## Ethereum Applications and Use Cases

In general, there are three categories of applications on top of Ethereum. 

*   The first category is financial applications, providing users with more powerful ways of managing and entering into contracts using their money. This includes sub-currencies, financial derivatives, hedging contracts, savings wallets, wills, and ultimately even some classes of full-scale employment contracts. 
*   The second category is semi-financial applications, where money is involved but there is also a heavy non-monetary side to what is being done; a perfect example is self-enforcing bounties for solutions to computational problems. 
*   The third category is non financial applications, such as online voting and decentralized governance.

Few key applications of Ethereum are as follows:

Token Systems

On-blockchain token systems have many applications ranging from sub-currencies representing assets such as dollar or gold to company stocks, individual tokens representing smart property, secure unforgeable coupons, and even token systems with no ties to conventional value at all, used as point systems for incentivization. Token systems are surprisingly easy to implement in Ethereum. 

The key point to understand is that all a currency, or token system, fundamentally is, is a database with one operation: subtract X units from A and give X units to B, with the provision that 

1.  A had at least X units before the transaction and 
2.  The transaction is approved by A. 

All that it takes to implement a token system is to implement this logic into a contract. The basic code for implementing a token system in Serpent looks as follows:

def send(to, value):

    if self.storage\[msg.sender\] >= value:

        self.storage\[msg.sender\] = self.storage\[msg.sender\] - value

        self.storage\[to\] = self.storage\[to\] + value

This is essentially a literal implementation of the "banking system" state transition function described further above in this document. A few extra lines of code need to be added to provide for the initial step of distributing the currency units in the first place and a few other edge cases, and ideally a function would be added to let other contracts query for the balance of an address. But that's all there is to it. 

Theoretically, Ethereum-based token systems acting can potentially include another important feature that on-chain Bitcoin-based meta-currencies lack: the ability to pay transaction fees directly in that currency. The way this would be implemented is that the contract would maintain an Ether balance with which it would refund Ether used to pay fees to the sender, and it would refill this balance by collecting the internal currency units that it takes in fees and reselling them in a constant running auction. Users would thus need to "activate" their accounts with Ether, but once the Ether is there it would be reusable because the contract would refund it each time. 

Currently there are two types of tokens which are based on Ethereum:

*   ERC-20 Tokens – The ERC-20 (Ethereum Request for Comments 20) Token Standard allows for fungible tokens on the Ethereum blockchain. The standard, proposed by Fabian Vogelsteller in November 2015, implements an API for tokens within smart contracts. The standard provides functions including the transfer of tokens from one account to another, getting the current token balance of an account and getting the total supply of the token available on the network. Smart contracts that correctly implement ERC-20 processes are called ERC-20 Token Contracts and help keep track of the created tokens on Ethereum. Numerous cryptocurrencies have launched as ERC-20 tokens and have been distributed through initial coin offerings. Fees to send ERC-20 tokens must be paid with Ether.
*   Non-fungible Tokens (NFTs) – Ethereum also allows for the creation of unique and indivisible tokens, called non-fungible tokens (NFTs). Since tokens of this type are unique, they have been used to represent such things as collectibles, digital art, sports memorabilia, virtual real estate, and items within games. Land, buildings and avatars in blockchain-based virtual worlds can also be bought and sold as NFTs, sometimes for hundreds of thousands of dollars. The first NFT project, Etheria, a 3D map of tradable and customizable hexagonal tiles, was deployed to the network in October 2015 and demonstrated live at DEVCON1 in November of that year. In 2021, Christie's sold a digital image with an NFT by Beeple for $69.3 million, making him the 3rd most valuable living artist in terms of auction prices at the time. 

Financial derivatives and Stable-Value Currencies

Financial derivatives are the most common application of a "smart contract", and one of the simplest to implement in code. The main challenge in implementing financial contracts is that the majority of them require reference to an external price ticker; for example, a very desirable application is a smart contract that hedges against the volatility of Ether with respect to the US dollar, but doing this requires the contract to know what the value of ETH/USD is. The simplest way to do this is through a "data feed" contract maintained by a specific party, for example, NASDAQ, designed so that that party has the ability to update the contract as needed, and providing an interface that allows other contracts to send a message to that contract and get back a response that provides the price.

Given that critical ingredient, the hedging contract would look as follows:

1.  Wait for party A to input 1000 Ether.
2.  Wait for party B to input 1000 Ether.
3.  Record the US $ value of 1000 Ether, calculated by querying the data feed contract, in storage, say this is $ x.
4.  After 30 days, allow A or B to "reactivate" the contract to send $x worth of ether to A and the rest to B.

Such a contract would have significant potential in crypto-commerce.

One of the main problems cited about cryptocurrency is the fact that it's volatile; although many users and merchants may want the security and convenience of dealing with cryptographic assets, they many not wish to face that prospect of losing, let’s say, 23% of the value of their funds in a single day. The most commonly proposed solution has been issuer-backed assets; such that an issuer creates a sub-currency in which they have the right to issue and revoke units, and provide one unit of the currency to anyone who provides them with one unit of a specified underlying asset (eg. gold, US $). The issuer then promises to provide one unit of the underlying asset to anyone who sends back one unit of the crypto-asset. In practice, however, issuers are not always trustworthy, and in some cases the banking infrastructure is too weak, or too hostile, for such services to exist. 

Financial derivatives provide an alternative. Here, instead of a single issuer providing the funds to back up an asset, a decentralized market of speculators, betting that the price of a cryptographic reference asset (eg. ETH) will go up, plays that role. Unlike issuers, speculators have no option to default on their side of the bargain because the hedging contract holds their funds in escrow. Note that this approach is not fully decentralized, because a trusted source is still needed to provide the price ticker, although arguably even still this is a massive improvement in terms of reducing infrastructure requirements as well as reducing the potential for fraud.

Multi-signature

We can leverage the Ethereum’s built-in authentication protocol to build a multi party authentication wallet. This functionality allows us to have an ‘m’ of ‘n’ signature scheme, in which ‘m’ out of the total ‘n’ owners of the wallet are required to sign off on every transaction. Even though the logic is fairly easy, the Solidity implementation is pretty complex. 

Decentralized finance (DeFi)

Decentralized finance (DeFi) is a use case of Ethereum. It offers traditional financial instruments in a decentralized architecture, outside of companies' and governments' control, such as money market funds which let users earn interest. Decentralized finance applications are typically accessed through a Web3-enabled browser extension or application, such as MetaMask, which allows users to directly interact with the Ethereum blockchain through a website. Many of these DApps can connect and work together to create complex financial services.

Additionally, through a process called "wrapping", certain DeFi protocols allow synthetic versions of various assets (like as Bitcoin, Gold and Oil) to become available and tradeable on Ethereum and also compatible with all of Ethereum's major wallets and applications.

Examples of DeFi platforms include MakerDAO and Compound. Uniswap, a decentralized exchange for tokens on Ethereum grew from $20 million in liquidity to $2.9 billion in 2020. As of October 2020, over $11 billion was invested in various DeFi protocols.

Identity and Reputation Systems

The earliest alternative cryptocurrency of all, Namecoin, attempted to use a Bitcoin-like blockchain to provide a name registration system, where users can register their names in a public database alongside other data. 

The major cited use case is for a DNS system, mapping domain names like "bitcoin.org" to an IP address. Other use cases include email authentication and potentially more advanced reputation systems. Here is the basic contract to provide a Namecoin-like name registration system on Ethereum:

def register(name, value):

    if !self.storage\[name\]:

        self.storage\[name\] = value

The contract is very simple – A database inside the Ethereum network that can be added to, but not modified or removed from. Anyone can register a name with some value, and that registration then sticks forever. A more sophisticated name registration contract will also have a "function clause" allowing other contracts to query it, as well as a mechanism for the "owner" (ie. the first registerer) of a name to change the data or transfer ownership. One can even add reputation and web-of-trust functionality on top.

Decentralized Autonomous Organizations (DAO)

The general concept of a "decentralized autonomous organization" is that of a virtual entity that has a certain set of members or shareholders which, perhaps with a 67% majority, have the right to spend the entity's funds and modify its code. The members would collectively decide on how the organization should allocate its funds. Methods for allocating a DAO's funds could range from bounties, salaries to even more exotic mechanisms such as an internal currency to reward work. This essentially replicates the legal trappings of a traditional company or nonprofit but using only cryptographic blockchain technology for enforcement. 

A general outline for how to code a DAO is as follows. The simplest design is simply a piece of self-modifying code that changes if two thirds of members agree on a change. Although code is theoretically immutable, one can easily get around this and have de-facto mutability by having chunks of the code in separate contracts and having the address of which contracts to call stored in the modifiable storage.

Proof-of-Existence

Let’s say we came up with an amazing innovation “3D printing artificial intelligence on the blockchain.” We wanted to prove that we came up with this innovation before a particular date, but we do not want to reveal it to the public yet. How do we do it in a way that everyone trusts? By combining the hash function and the trustless blockchain. We store a hash of our document into the blockchain, such that we could prove to everyone at any later date that we were the ones who included this hash on the blockchain, and that the information has not been changed.

By doing so, we now have “Proof-of-Existence” of some piece of information at some point in time. With “Proof-of-Existence”, we leverage both the public auditability and immutability of the blockchain. 

This is an example of a record keeping use case. One of such use case is document ownership. We can prove that we own some document at some time through a commitment scheme – hash the document with some random number, then we have our hash commitment, and we can reveal this input later to prove our ownership, as shown in the next use case.  

Land Titles

A problem that several countries face is a broken land titles system. Flawed paperwork, forged signature, and unclear documents make it difficult to trace the ownership of land. In addition, it is difficult for the governments to build infrastructure for each of their citizens. The pitfalls which keep the governments from solving this problem is mistrust between citizens and these central parties. Corrupt officials are susceptible to take bribes and tamper records. In addition, most citizens do not trust non-government organizations either, making centralized options infeasible. So how do we solve this problem? By decentralization.

We can track the ownership of the documents using Proof-of-Existence. We can create an association between the users and document hashes. By associating their addresses to document hashes, users can provide their digital signature to prove ownership of land. This provides transparency and immutability, since information about all document ownership is public and on the blockchain, and also limits centralization because no single entity decides which person owns which land titles. 

However, there is a caveat that affects this Ethereum use case. In computer science, one of the most popular acronym is “GIGO” – Garbage In, Garbage Out. 

A blockchain is good at handling internal data through its public auditability, but it cannot reach into the real world and validate inputs. If the inputs from the real world are incorrect, then the output is also going to be incorrect. 

This requires some system for validating inputs into the blockchain. We refer to such entities sending information from the real world to the blockchain network as “Oracles.” However this sends us back to centralization as we need some trusted 3rd parties to serve as oracles and provide correct information into the blockchain whenever someone creates a land title. This problem is yet to be solved. 

Smart Energy Grids

One of the biggest real world scenarios to leverage smart contracts is infrastructure sector. A common infrastructure problem is that of smart energy grids. Energy flows from a plant to houses, but what if a house has excess energy?

Let’s say house A has excess energy, and house B lacks energy. How can we build an infrastructure from house A to house B without relying on a central party?

The solution is in smart contracts. We can make a smart contract to guarantee the financial commitments for transfer of energy from house A to house B. House A can create a smart contract, put in $1000, and assuming if house B and another house C also commit $1000, then a contractor can redeem this money in exchange for building a smart energy grid. 

This immutable commitment scheme allows anyone to leverage smart money property to the fullest. Through smart contracts, we can coordinate between untrusting parties without a central entity. In places where the government cannot contribute to infrastructure, the citizens are able to do it themselves if they have the capital but not the system to securely combine their resources. This is one of the most revolutionary concepts of blockchain, giving users the ability to become their own service provider.

## Ethereum Ecosystem

The Leaders

Just like Bitcoin, the Ethereum ecosystem is constantly changing. However, Ethereum is a bit more politically centralized than Bitcoin. For example, we know that its founder it Vitalik Buterin, who is the biggest face in Ethereum. He is personally driving Ethereum forward, his opinions can easily shape the entire Ethereum space, and he controls a lot of influence. 

Vitalik currently leads the Ethereum’s research team, which contains another key player, Vlad Zamfir. Notably, Vitalik and Vlad have different versions for Ethereum’s upgrade to the Proof-of-Stake protocol. 

Another key player of Ethereum is Gavin Wood, who is famous for originally proposing Solidity as Ethereum’s high level programming language on top of the EVM.

Nick Szabo is a researcher in digital contracts, and is known for coining the term “Smart Contract.”

ConsenSys

ConsenSys can be best described as a software foundry. It facilitates a variety of applications which operate of the Ethereum blockchain, and coordinates, incubates, accelerates, and spawns what it calls “spoke ventures.” For example, there is uPort, which is identity management, the popular Truffle development suite, MetaMask, which links your web browser to Ethereum, and Gnosis, the prediction market platform. These are all spoke ventures of ConsenSys.

The Ethereum community also spawns a lot of original research. Most notable is Casper, the Ethereum’s PoS implementation protocol. There is also Plasma, a proposed scalability upgrade to Ethereum inspired by a similar scalability proposal for Bitcoin, called Lightning. 

There have been efforts to port Ethereum over to another blockchain platform called Cosmos, which claims to be the internet of blockchains. 

Ethereum Governance

In October 2015, a development governance was proposed as the Ethereum Improvement Proposal (EIP), standardized on EIP-1. The core development group and community were to gain consensus by a process regulated EIP. 

Ethereum Improvement Proposals (EIPs) describe standards for the Ethereum platform, including core protocol specifications, client APIs, and contract standards. Network upgrades are discussed separately in the Ethereum Project Management repository.

EIP status terms

*   Idea – An idea that is pre-draft. This is not tracked within the EIP Repository.
*   Draft – The first formally tracked stage of an EIP in development. 
*   Review – An EIP Author marks an EIP as ready for and requesting Peer Review.
*   Last Call – The final review window for an EIP before moving to Final stage.. An EIP editor will assign Last Call status and set a review end date (\`last-call-deadline\`), typically 14 days later. 
*   Final – This EIP represents the final standard. A Final EIP exists in a state of finality and should only be updated to correct errata and add non-normative clarifications.
*   Stagnant – Any EIP in Draft or Review, if inactive for a period of more than 6 months, is moved to Stagnant. An EIP may be resurrected from this state by through moving it back to Draft.
*   Withdrawn – The EIP Author(s) have withdrawn the proposed EIP. If the idea is pursued at later date it is considered a new proposal.
*   Living – A special status for EIPs that are designed to be continually updated and not reach a state of finality. 

EIPs are separated into a number of types, and each has its own list of EIPs.

*   Standard Track – Describes any change that affects most or all Ethereum implementations, such as a change to the network protocol, a change in block or transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using Ethereum. 
*   Core – Improvements requiring a consensus fork (e.g. EIP-5, EIP-101), as well as changes that are not necessarily consensus critical but may be relevant to “core dev” discussions.
*   Networking – Includes improvements around Light Ethereum Subprotocol, as well as proposed improvements to network protocol specifications of whisper and swarm.
*   Interface – Includes improvements around client API/RPC specifications and standards, and also certain language-level standards like method names (EIP-6) and contract ABIs.
*   ERC – Application-level standards and conventions, including contract standards such as token standards (ERC-20), name registries (ERC-137), URI schemes (ERC-681), library/package formats (EIP190), and wallet formats (EIP-85).
*   Meta – Describes a process surrounding Ethereum or proposes a change to (or an event in) a process. Meta EIP or Process EIPs are like Standards Track EIPs but apply to areas other than the Ethereum protocol itself. Examples include procedures, guidelines, changes to the decision-making process, and changes to the tools or environment used in Ethereum development.
*   Informational – Describes a Ethereum design issue, or provides general guidelines or information to the Ethereum community, but does not propose a new feature. Informational EIPs do not necessarily represent Ethereum community consensus or a recommendation, so users and implementers are free to ignore Informational EIPs or follow their advice.

 

 

 

 

 

# Blockchain Platforms

In this chapter, we will focus on the different blockchain platforms currently in use, gain an insight on their design features, and learn about their pros and cons.

Blockchain platforms are the underlying tools to develop decentralized applications on blockchain technology (e.g. - enabling decentralized applications pertaining to multiparty cooperation or data exchange). These platforms are being used for generalized distributed value exchange, consisting of an expanding list of cryptographically signed, irrevocable transactional records shared by all participants in a network. Each record contains a time stamp and reference links to previous transactions. It is a decentralized state transition machine that manages the life cycle of digitalized assets and immutably records operations in a distributed ledger.

Blockchain platforms have the ability to disrupt legacy supply chain businesses and technology processes. For example, U.S. requirements for pharmaceutical companies to track and trace medicines call for a new approach for supply chain participants to share and transact data more efficiently and more transparently. Blockchain technology could be the answer.

Interest in blockchain platforms has been growing significantly to streamline supply chains, improve traceability, simplify trade, and improve financial transactions. A lot of this interest started with the speculative frenzy surrounding Bitcoin, which is based on an older blockchain platform that faces challenges with energy consumption and speed. Modern blockchain platforms have been developed to help overcome these limitations and provide practical value for other business uses and applications. 

The top three blockchain frameworks for these use cases are R3 Corda, Hyperledger and Ethereum, with EOSIO and Quorum gaining ground.

Key features to consider for blockchain platform evaluation

Blockchain platforms consist of a wide range of components, which enables enterprises to select the appropriate components for different kinds of capabilities.

However, it useful to examine these four key features when evaluating blockchain platforms and components:

*   Public (Open) or Private (Closed) Platform – Whether a platform is open (that is, a public blockchain) or closed (a private blockchain) and how that affects speed and security. Anyone can join a public blockchain, which can make it easier to set up for small-business users, such as farmers. The downside is that public blockchains are not as fast. Also the private platforms provide more data security for organizations. Many of the blockchain code bases can be modified to be either open or closed.
*   Consensus mechanism – Whether the platform leverages Proof-of-Work (PoW), Proof-of-Stake (PoS) or Byzantine fault tolerance as its consensus mechanism. Proof-of-work is the older mechanism used in Bitcoin and Ethereum, however its slower compared to Proof-of-Stake, which is newer and less proven but faster and more efficient.
*   Ledger technology and how it records the transactions – This relates to how the blockchain keeps track of information. Popular approaches include an account model and UTXO. An account model records the balance, whereas the UTXO model is analogous to cash with serial numbers in your wallet. The account model is used in the blockchain platforms Ethereum, Stellar, Tron and EOSIO. IBM Blockchain, Hyperledger Fabric and Hyperledger Sawtooth use UTXO.
*   Programming language and functions – Smart contract functions for capturing business logic on the blockchain. Popular programming languages include Ethereum Solidity for Ethereum blockchain, WebAssembly languages for IBM, and Digital Asset Modeling Language.

The most popular blockchain platforms are as follows:

1\. Ethereum

Introduced in 2013, Ethereum is one of the oldest and most established blockchain platforms, which has been offering developers an open-source distributed computing platform where they can discover all the benefits of blockchain. Ethereum uses a peer-to-peer approach, where users can write codes to control digital values, runs exactly as programmed, and is accessible anywhere in the world.               

It provides a truly decentralized blockchain that is comparable to the Bitcoin blockchain network. It enables true decentralization with support for smart contracts. Besides its role as a blockchain platform that underpins enterprise applications, it has its own cryptocurrency called Ether.

The Ethereum platform has seen widespread adoption by technologists who build decentralized applications, or dApps, on the Ethereum network. For example, there are numerous platforms and exchanges for nonfungible tokens (NFTs) -- a type of digital asset that can be exchanged on a blockchain. It has a mature ecosystem of tools for writing smart contracts using the Solidity programming environment, which runs on the Ethereum Virtual Machine. 

However, its key weaknesses include slow processing times and higher transaction processing costs compared to other platforms. Alternative blockchain networks can process transactions much faster at potentially lower cost than Ethereum, though many observers expect this to change after Ethereum moves to Proof-of-Stake consensus mechanism, and adopts a more efficient security mechanism.

2\. IBM Blockchain

IBM Blockchain is a private, decentralized blockchain network that has been the most successful with enterprise clients who are less risk-averse. He sees the biggest opportunities in using it to link into enterprise cloud and legacy technologies more seamlessly than is possible in other decentralized networks.

The IBM Blockchain developer tool was designed to be flexible, functional and customizable. IBM has also invested in creating a user-friendly interface to simplify critical tasks, such as setting up, testing and rapidly deploying smart contracts.

IBM blockchain platform has seen significant adoption in financial services and banking, as well as supply chain. Some examples of successful blockchain apps include IBM Food Trust, which has completed more than 18 million transactions representing more than 17,000 products, and Blockchain Community Initiative in Thailand, which supports services like payment obligations and enterprise auctions for 22 Thai banks.

3\. Hyperledger Fabric

Hyperledger Fabric is a set of tools that help create blockchain applications championed by IBM and The Linux Foundation. It was built from the ground up with enterprise distributed ledger uses. It has a rich ecosystem of components that can be plugged into a modular architecture. It works well in closed blockchain deployments, which can improve security and speed. It also supports an open smart contract model that can support various data models, such as account and unspent transaction output, or UTXO, models.

Hyperledger Fabric can also improve data privacy by isolating transactions in channels or enabling the sharing of private data on a need-to-know basis in private data collections. It also enables high-speed transactions with low latency of finality and confirmation, according to its proponents.

The latest updates add support for an organization to join a channel without copying the whole history of the ledger. This enables a quicker startup process with less storage required. There is an active and diverse community around Hyperledger Fabric that is working on adding more features related to consensus algorithms, additional privacy options for GDPR compliance and operational improvements.

4\. Hyperledger Sawtooth

Another open source blockchain initiative hosted by Hyperledger and the Linux Foundation, Hyperledger Sawtooth uses a novel consensus mechanism called Proof of Elapsed Time that can integrate with hardware-based security technologies to allow "trusted execution environments" of program code to run in secure enclaves, which are protected areas of computer memory.

The most common applications are for developing supply chain systems and customizing Sawtooth for specific purposes, such as novel consensus algorithms.

Work has started on a Sawtooth Library that will enable developers of custom distributed ledgers to pick and choose which pieces of Sawtooth they use in their application. At the same time, Sawtooth is adopting Splinter for networking, which will provide dynamic private circuits (groups of nodes); Hyperledger Transact for transaction processing, which will extend smart contract capabilities; and Augrim for consensus, which will expand the number of supported algorithms.

5\. R3 Corda

There is some debate whether R3 Corda is technically a blockchain or an alternative type of distributed ledger. It uses a novel consensus mechanism in which transactions are cryptographically linked but does not periodically batch multiple transactions into a block. Even the official Corda site describes it as "both a blockchain and not a blockchain." One of the key benefits of this approach is that all transactions are processed in real time, which can improve performance compared to other types of blockchains.

The R3 consortium has a strong following in the financial industry, since Corda provides an attractive approach for financial transactions and smart contracts with strong security. Leading proponents include Bank of America, HSBC, Intel and Microsoft. It has a strong chance of becoming the de facto network of insurance-related transaction processing. However, it faces competition from other federated blockchain networks that can process transactions faster and cheaper. 

6\. Tezos

In development since 2014, Tezos is an older platform that supports decentralized applications, smart contracts and novel financial instruments, such as NFTs, which can be thought of as a modern variation on trading cards that are tied to digital assets. The platform supports a dynamically upgradeable protocol and modular software clients that enable it to adapt to new uses. The Tezos community has been upgrading the platform at a rapid clip, with recent enhancements that have improved performance and increased the size limit on smart contracts.

7\. EOSIO

The EOSIO blockchain platform was first launched as an open source project in 2018. It is optimized for developing decentralized applications and smart contracts. It uses a complex consensus mechanism based on PoS that provides better performance than older mechanisms like Ethereum, according to its proponents. It also includes support for a governance feature for voting on changes to the platform.

Key strengths include fast transactions and advanced account permission features for deploying applications. Over 400 applications have been developed on the platform, including identity management, supply chain management and gaming.

8\. Stellar

Stellar is a newer blockchain platform optimized for various kinds of decentralized finance applications. It uses the Stellar Consensus Protocol, which purportedly can speed the time required to process and finalize transactions on a public blockchain network. 

Its blockchain network allows for storing and moving of money. It facilitates users to create, trade and send digital representations of all forms of money, like dollar, bitcoin, etc.

It also includes security mechanisms for shutting out bad or questionable actors in a financial transaction. It has been adopted by several companies for international trade and exchanging money across borders.

The key features of Stellar include:

*   Enables thousands of transactions per second
*   Allows multi signatures and Smart contracts
*   Has 1% annual inflation

 

9\. Quorum

Quorum is a customized version of Ethereum pioneered by JPMorgan. It takes advantage of the core work on the Ethereum blockchain platform and repackages it into a hardened environment suitable for banks. It has been optimized to support high-speed transactions between institutions like banks and insurance companies on a private network. It also adds various privacy enhancements to Ethereum to improve support for regulations like GDPR in Europe and CCPA in California.

 

 

 

 

 

 

 

 

 

 

 

 

 

# Blockchain Use Cases

This chapter examines blockchain in action. We will see how blockchain provides solutions for business, governments and social projects. Businesses fueled by blockchain are developing new relationships for more efficient communication and trust among the untrusting parties, fostering new business models. Next we will discuss the impact blockchain is having in developing countries by offering transparency and accountability. We will blockchain based new technologies and emerging breakthroughs. Finally, we will gain an insight on the use cases designed to improve the user’s experience, decentralized gaming platforms and new marketplaces inventing new worlds to interact in.

Blockchain Use Case Categories

Let’s take a look at how blockchain is improving the way we interact with each other. In blockchain, identity management is the key to all the use cases. We will characterize these use cases by who is developing the solutions, starting with large enterprise solutions to smartphone and web browser applications powered by blockchain that pur control back on user’s hands.

*   Enterprise solutions – Business and organizations are implementing blockchain to overcome obstacles in transparency and trust forging new associations with global implications.
*   Public sector solutions – Governments are using blockchain solutions to improve services that they provide to their citizens. Digital identity solutions, central bank digital currencies and transparent workflows are bringing efficiency to the public sector system with an end result that benefits citizens.
*   Social impact solutions – Social impact blockchain solutions address social and environmental challenges. Backed by 17 UN Sustainable Development Goals blockchain developers, investors, philanthropists, government agencies and foundations are developing solutions that tackle these global problems.
*   Platform developer solutions – Blockchain is a new technology that is constantly improving. Developers are creating standards and new platforms to bring this technology into the mainstream.
*   End user solutions – Everyday solutions emerge that put decentralized blockchains and all the benefits they promise in the hands of individuals from new decentralized marketplaces to new ways to express music, art, and even trade property built inside a game.

## Enterprise Solutions

Business fueled by blockchain solutions are developing new relationships for more efficient communications and workflows, fostering new business models, and solving problems with how transact online, to the cost of doing business.

Global Supply Chains

Supply chain data is not always visible or trusted. In recent times of disruption supply chains matter more than ever. Global supply chains and blockchain are working to secure systems to better handle these disruptions. The Covid-19 pandemic shed light on the frailty of our supply chains which accelerated the discussion over blockchain solutions.

Global trade functions much as it has since the introduction of the shipping container in 1956. Manual, paper-based processes are still common and information about the status of goods is locked away in organization silos. Today, 90% of goods in global trade are carried by the shipping industry with the supply chain slowed by the complexity and sheer volume of point-to-point communication across a loosely coupled web of land transportation providers, freight forwarders, custom brokers, governments, ports, and ocean carriers. 

IBM and Maersk are addressing this problem with a distributes permissioned platform accessible by the supply chain ecosystem designed to exchange event data and handle document workflows. They are employing blockchain technology to create a global tamperproof system for digitizing trade workflow and tracking shipments end-to-end, eliminating frictions including costly point-to-point communications. The collaboration will launch with the potential ability to track millions of container journeys per year and integrate with custom authorities on selected trade lanes. 

In a recent test by Maersk, shipping a single container of flowers from Kenya to the port of Rotterdam resulted in a stack of nearly 200 communications. Using this example, we will examine how blockchain has been implemented to create trust and security in the digitize document workflow and improve the efficiency of global supply chains. The distinct entities involved in the transaction are the rowers, export authorities, ports, customers, and importers. Shipping from the port of Mombasa requires signatures from three different agencies approving the export and six documents that describe the origin, chemical treatments, product quality, and custom duties. First, using a PC or a mobile phone the Kenyan farm submits a packing list that becomes visible to all participants. This action initiates a smart contract that enforces an export approval workflow between the three agencies. As each agency signs, the status is updated for everyone to see. Simultaneously, information about the inspection of the flowers, the sealing of the refrigerated container, the pickup by the trucker, and the approval from the customs is communicated to the port of Mombasa allowing them to prepare for the container. All actions relating to the documents and the physical goods are captured and shared – which documents were submitted, when and by whom, where the flowers are, who is in the possession of them, and the next steps in the journey. As flowers are perishable, do it is crucial that there are minimum delays at every step. Blockchain provides secure data exchange, and a tamperproof repository for these documents and shipping events. This system could significantly reduce delays and frauds saving billions of dollars annually. According to WTO, reducing barriers within the international supply chain could increase the total trade volume by 15% and worldwide GDP by almost 5%.

Food Industry

In the food industry, farms are complicated ecosystems with many moving parts, careful timing, and seasonal financing structures. However, once the agricultural products leave the farm, they become part of a wide-reaching supply chain with a lot of parties. Buyers, sellers, distributors, and grocery chains – all of them want to know where the agricultural product has been before it is served on your dinner table. The trend toward blockchain agriculture promises to make each step of growing and distributing food simpler. It offers all parties involved a single source of truth for the agricultural supply chain.

When customers shops for food items in a store, they expect great prices and a good customer service, but an unspoken expectation is that the products in the store should be safe to consume. The food product is guilty until proves innocent. In case of a food getting event or a food scare, all the product is pulled until the implicated product is found then the safe product can be put back. However if it takes too much time to identify the implicated product, the entire stock is discarded as food is a perishable item. Now imagine if the stores could pinpoint with certainty, within minutes that which was the implicated product, it would save a lot of food wastage and optimize costs. Walmart and IBM are working to make that a reality. 

The food ecosystem involves farmers, processors, distributors, and each participant traces the food system in their own way. Mostly it is done on paper and there is minimal interaction between different players in the ecosystem, and these stakeholders cannot have a full view of what is happening in the food ecosystem. Walmart is planning to leverage blockchain to bring all the stakeholders in the food ecosystem together such that they can collaborate quickly and efficiently. Blockchain allows the different segments in the food system to capture information about the product, what they have done to it, and where the product has been. If we link that data with the other data points, all this information will provide us an insight that will enable a safer, more affordable and sustainable food system. 

However, the ultimate goal of blockchain implementation in the food ecosystem is transparency. Blockchain will enable the stakeholders to not only track where the food came from, but how it was produced, was it produced safely, responsibly, was it sustainable grown, and how many days of shelf life are left on that product. 

Healthcare

Blockchain is transforming the healthcare industry. Some challenges the healthcare industry faces are counterfeit drugs, siloed data, health record management to name a few. Blockchain can solve these issues with interoperability, data integrity and security.

Moderna uses blockchain to support its smart COVID vaccine management. SAP has an exiting solution unrelated to blockchain called Advanced Track and Trace for Pharmaceuticals (ATTP) which generates the unique identifiers. Also, Pfizer has been using blockchain in transparent clinical trials. 

Finance Markets

Reduction of settlement times will improve the flow of money through ‘fintech’ companies. 

Swiss Exchange, SIX has a solution that solves the issue in the trade markets of long settlement times. The new blockchain platform runs parallel to the existing SIX platform, which involves three steps to complete a trade, often over several days. Two of those steps vanish in a blockchain distributed ledger, meaning a transaction can be completed in a fraction of a second.

Trade finance is showing promise for blockchain solutions in letter of credits by making available financial mechanisms previously excluded for most people. In the paper from Andrea Frosinini, “Reshaping Trade Finance: Towards a ‘New’ Line of Credit”, he supplied trade finance paired with blockchain that provides delivery and payment assurance to buyers and sellers, reducing operational and transactional cost and opening up market opportunities.  

Voltron Trade Finance was co-founded by eight member banks including Bangkok Bank, BNP Paribas, CTBC, HSBC, ING, Natwest, SEB and Standard Chartered Bank. This consortium has since grown to more than 50 banks and corporations. The platform is built on Corda blockchain and solves the problem to reduce transaction time. Most letter of credits are based on paper and take 5 to 10 days. By using blockchain, the letter of credits can be efficiently transacted within 24 hours.

## Public Sector Solutions

Blockchain benefits of security, efficiency and speed have government leaders research the far reaching implications that will improve lives and accelerate global blockchain solutions. Public sector can be characterized by public administration, public service, land and community, and government. According to a presentation by Bobbi Muscara, Saptarshi Choudhury and Sean O’Kelly, “Rethinking Public Sector through Blockchain”, all blockchain public sector projects must consider the four design factors:

*   Identity management for governments
*   Interactions for regulated transactions
*   Regulations
*   Governance

Smart Dubai

A real-world example of public sector blockchain solution is of Smart Dubai 2021, wherein Dubai aims to move all government operations and record keeping into blockchain. The goal is to increase transparency and efficiency in the government operations. Blockchain is also becoming the enabling layer for a lot of other Smart Dubai initiatives, thereby creating a Smart City. For example, projects like automated traffic signals, registration of citizens for visas and public healthcare, etc. are all being pioneered on blockchain.

Dutch Blockchain Coalition

Dutch Blockchain Coalition established three pillars of society working together to build a blockchain future:

*   Developing building blocks – digital identities
*   Realizing the conditions for utilizing blockchain
*   Developing and realizing the Human Capital Agenda

Wyoming

Wyoming has enacted a total of 13 blockchain laws, making it the only US state to provide a comprehensive, legal framework that enables blockchain technology for both individuals and companies.

Social Impact Solutions

The blockchain for social impact coalition (BSIC) is a not-for-profit organization that incubates, develops, and collaborates on blockchain products and solutions that can address social and environmental challenges across the United Nations Sustainable Development Goals. The aim is to inspire, federate, and create bridges between NGOs, and government agencies, foundations, impact investors, philanthropists, and technologists.

According to the “7 ways Blockchain can be used for Social Good” article by Kayla Matthews, areas that are seeing blockchain social impact projects are:

*   Philanthropy and remittances
*   Financial empowerment
*   Identity and land rights
*   Governance and democracy
*   Supply chain and environmental protections

Kiva

More that 1.7 billion people around the world are unbanked and cannot access the financial services. Kiva is an international nonprofit organization, founded in 2005 in San Francisco, with a mission to expand financial access to help the underserved communities. Kiva accomplishes this by crowdfunding loans and unlocking capital for the underserved, improving the quality and cost of financial services, and addressing the underlying barriers to financial access around the world. Through Kiva’s work, students can pay for education, women can start businesses, farmers are able to invest in equipment, and families can afford emergency care.

Rohingya Project

The mission of the Rohingya Project is to create the foundation for a viable future for the stateless Rohingya people by connecting them digitally with opportunities to learn, equip, and empower themselves. Through the creation of a financial and social inclusion platform, the Rohingyas who have been sidelined for years can be given access to a wide range of virtual services including online education, digital identity, and reward tokens. 

The platform will tap into the potential of the Rohingya community and other marginalized people and offer options to counter their exclusion from the mainstream.

## Platform Developer Solutions

ConsenSys

ConsesSys Mesh companies offer solutions to help build out the Ethereum ecosystem. ConsesSys Mesh acts as an incubator for Ethereum based projects:

*   Codefi – Finance and commerce blockchain applications
*   Diligence – Ethereum based smart contract audits
*   INFURA – Manage scaling and performance issues
*   Metamask – Cryptocurrency wallet application
*   Quorum – Open source blockchain platforms
*   Truffle – Application builder

Hyperledger

Hyperledger is an open source project with blockchain to build solutions on, and has tools to support these blockchains. We discussed about Hyperledger Fabric and Hyperledger Sawtooth in the earlier chapter. Some other examples Hyperledger based platforms are, Hyperledger Aries, Hyperledger Transact, Hyperledger Ursa, Hyperledger Besu, Hyperledger Iroha, and Hyperledger Indy.

Daml

Daml is a development framework for creating systems of records that securely connect across business processes and data boundaries while retaining privacy, guaranteeing data integrity, and enforcing strict authorization. Allowing such systems to cross boundaries – legal, regulatory, organizational, or other – enables them to for seamless economic networks.

*   Daml Connect – It is a complete development and application stack allowing you to build, integrate, deploy, and maintain full-stack multi party solutions with a minimum of boilerplate code.
*   Daml Drivers – They allow you to deploy your applications using distributed ledgers, blockchains, or databases. Migration between ledger drivers without any code changes as the business needs evolve.
*   Daml Hub – It is a cloud service that enables rapid distribution application deployment with an always available, easy-to-use, and fully managed cloud environment.

SIMBA Chain

SIMBA Chain was founded in 2017 from a grant awarded by the Defense Advanced Research Projects Agency (DARPA) to Indiana Technology and Manufacturing Companies (ITAMCO) and the Center for Research Computing (CRC) at the University of Notre Dame in order to develop a secure, un-hackable messaging and transaction platform for the United States military. SIMBA Chain is a cloud-based, smart-contract-as-a-service (SCaaS) platform, enabling users across a variety of skill sets to implement decentralized applications. These applications allow secure, direct connections between users and providers, eliminating third parties. The easy-to-use platform is tailored for users, developers, government, and enterprises to quickly develop blockchain applications for their enterprise.

*   SIMBA’s Smart Contract Designer – It allows anyone to quickly and easily create smart contracts. The interface allows users to easily build a graph of the relationships between assets and transactions. This graphical model is then converted to Solidity Smart Contract that can be executed on the blockchain.

## End User Solutions

Identity

Identity management is vital for blockchain operation. Identifying objects that will interact with a blockchain such as people, places, things (IoT) is the first step and consideration when developing a blockchain.

One solution is the Verifiable Organizations Network (VON) project that enables organizations – and the people running these organizations – to conduct business online is a trusted environment. The core challenge is that on the internet, we can’t tell if we are talking to you, or if someone is pretending to be you. We need a reliable way to verify the identity of an individual in a manner appropriate for the type of transaction and in a privacy-preserving manner.

Marketplace

Marketplace exist to shop renewable energies to make sustainable solutions available on open markets. Everyone knows there are countless inefficiencies in the energy grid, stemming from the highly centralized nature of our utility systems. With the advent of at-home energy production and storage through affordable solar panels and home batteries, many users are storing energy surpluses at home without a way to ‘sell’ clean energy.

Power Ledger solution offers a peer-to-peer energy trading platform. It builds global blockchain energy solutions to provide communities access to affordable electricity that is also renewable. By increasing the transparency for energy origins, Power Ledger could assist with providing customers more choices for where their energy comes from. They accomplish these goals through peer-to-peer energy trading, carbon product trading, and microgrids management.

Music and Films

Now there are new ways for artists, producers, and labels, to get paid on time, in full royalties going directly back to the artists, via Non Fungible Tokens (NFTs). 

NFTs are typically held on the Ethereum blockchain, although other blockchains support them as well. An NFT is created, or “minted” from digital objects that represent both tangible and intangible items, including Art, GIFs, Videos and sports highlights, Collectibles, Virtual avatars and video game skins, Designer sneakers, and Music.

In February 2021, NFTs reportedly generated around $25 million within the music industry, with artists selling artwork and music as NFT tokens. 

Gaming

The days of video games being just a form of entertainment are long gone. Most of the new video games have in-app purchases and loot box features in them. These features enable users to use real-life currency to buy new skins and weapons for their characters and tools. With the use of DeFi, game developers can implement the newer incentive or reward models with DeFi coins. In fact, gaming and eSports will likely become one of the major markets as users are more tech-savvy and open to newer technologies.

NFTs can be used to represent in-game assets, such as digital plots of land, which some commentators describe as being controlled "by the user" instead of the game developer by allowing assets to be traded on the 3rd party marketplaces without permission from the game developer. CryptoKitties was an early successful blockchain online game where players adopt and trade virtual cats. The monetization of NFTs within the game raised a $12.5 million investment, with some kitties selling for over $100,000 each. Following its success, CryptoKitties was added to the ERC-721 standard.

Decentraland

Decentraland is a virtual world built on the top of the Ethereum blockchain. A fully decentralized world where users can interact, build and exchange items, enjoy a concert with virtual friends. Decentraland is run by a DOA, decentralized organization built with smart contracts and decentralized applications (dapps).

## The Future of Blockchain

What is the future of blockchain? This is a big question. 

Blockchain is in an exciting place right now. 

Blockchain tends to get talked about in the context of a lot of other exciting emerging technologies like Internet of Things (IoT), Artificial intelligence (AI), Augmented Reality (AI), and 3D Printing. Blockchain is likely to become an enabling layer for many of these technological revolutions. For example, having a smart refrigerator that analyze my milk intake and automatically reorders milk as it starts to get low. People are getting nervous on the idea of implementing many of thee technologies, because how do we protect them, how do we ensure privacy and protect any frauds. How to we ensure that the data in these systems is immutable and secure? Blockchain is the solution to that. We are going to see a lot of growth in the emerging technologies as blockchain continues to evolve.

In long term, blockchain will become an enabling layer for a multi-planetary human economy. In 2018, SpaceX launched a program to send humans to Mars. In the next 40 to 50 years, we might see a human colony in Mars. Now Mars is really far away. At the fastest, it is a 26 minute round trip at the speed of light. Hence, centralized models of internet are not going to work. Hence, technologies like blockchain will be the enablers to allow humans to continue to trade and interact with each other as we become a multi-planetary society.

Hence, there is a huge potential in blockchain and it is something really exciting and a place to be right now.

 

‘

 

 

 

 

 

# References

*   [https://builtin.com/blockchain](https://builtin.com/blockchain)
*   [https://toshitimes.com/the-longest-running-blockchain-has-existed-on-nyt-pages-since-1995/](https://toshitimes.com/the-longest-running-blockchain-has-existed-on-nyt-pages-since-1995/)
*   [https://skyseo.co.nz/web-1-0-vs-web-2-0-vs-web-3-0-vs-web-4-0-vs-web-5-0/](https://skyseo.co.nz/web-1-0-vs-web-2-0-vs-web-3-0-vs-web-4-0-vs-web-5-0/)
*   [https://www.geeksforgeeks.org/web-1-0-web-2-0-and-web-3-0-with-their-difference/](https://www.geeksforgeeks.org/web-1-0-web-2-0-and-web-3-0-with-their-difference/)
*   [https://101blockchains.com/introduction-to-blockchain-features/](https://101blockchains.com/introduction-to-blockchain-features/) 
*   [https://www.ibm.com/blogs/blockchain/2019/04/how-transparency-through-blockchain-helps-the-cybersecurity-community/](https://www.ibm.com/blogs/blockchain/2019/04/how-transparency-through-blockchain-helps-the-cybersecurity-community/)
*   [https://www.britannica.com/topic/cryptology/Developments-during-World-Wars-I-and-II](https://www.britannica.com/topic/cryptology/Developments-during-World-Wars-I-and-II)
*   [https://nodes.com/](https://nodes.com/)
*   [https://medium.com/coinmonks/blockchain-what-is-a-node-or-masternode-and-what-does-it-do-4d9a4200938f](https://medium.com/coinmonks/blockchain-what-is-a-node-or-masternode-and-what-does-it-do-4d9a4200938f)
*   [https://medium.com/dataseries/triple-entry-accounting-system-a-revolution-with-blockchain-768f4d8cabd8](https://medium.com/dataseries/triple-entry-accounting-system-a-revolution-with-blockchain-768f4d8cabd8)
*   [https://www.twobirds.com/~/media/pdfs/in-focus/blockchain/private-blockchain-briefing-note.pdf](https://www.twobirds.com/~/media/pdfs/in-focus/blockchain/private-blockchain-briefing-note.pdf)
*   [https://www.techtarget.com/searchcio/feature/Top-9-blockchain-platforms-to-consider](https://www.techtarget.com/searchcio/feature/Top-9-blockchain-platforms-to-consider)
*   [https://www.synopsys.com/blogs/software-security/cryptographic-hash-functions/](https://www.synopsys.com/blogs/software-security/cryptographic-hash-functions/) 
*   [https://www.nasdaq.com/articles/what-is-nakamoto-consensus-and-how-does-it-power-bitcoin-2021-11-08](https://www.nasdaq.com/articles/what-is-nakamoto-consensus-and-how-does-it-power-bitcoin-2021-11-08)  
*   [https://en.wikipedia.org/wiki/Unspent\_transaction\_output](https://en.wikipedia.org/wiki/Unspent_transaction_output)
*   [https://en.wikipedia.org/wiki/Elliptic-curve\_cryptography](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography)
*   [https://academy.bit2me.com/en/what-is-bitcoin-script/](https://academy.bit2me.com/en/what-is-bitcoin-script/)
*   [https://www.cs.odu.edu/~zeil/cs390/latest/Public/turing-complete/index.html](https://www.cs.odu.edu/~zeil/cs390/latest/Public/turing-complete/index.html)
*   [https://www.cbinsights.com/research/what-is-blockchain-technology/](https://www.cbinsights.com/research/what-is-blockchain-technology/)
*   [https://www.investopedia.com/terms/b/bitcoin-mining.asp](https://www.investopedia.com/terms/b/bitcoin-mining.asp)
*   [https://ethereum.org/en/whitepaper/](https://ethereum.org/en/whitepaper/)
*   [https://eth.wiki/en/concepts/ethash/ethash](https://eth.wiki/en/concepts/ethash/ethash) 
*   [https://eips.ethereum.org/](https://eips.ethereum.org/) 
*   [https://www.oreilly.com/library/view/mastering-bitcoin/9781491902639/ch06.html](https://www.oreilly.com/library/view/mastering-bitcoin/9781491902639/ch06.html)
*   [https://web.stanford.edu/class/ee374/downloads/notes13.pdf](https://web.stanford.edu/class/ee374/downloads/notes13.pdf) 
*   [https://policyreview.info/glossary/blockchain-governance](https://policyreview.info/glossary/blockchain-governance) 
*   [https://www.gemini.com/cryptopedia/blockchain-governance-mechanisms#section-off-chain-governance-mechanisms](https://www.gemini.com/cryptopedia/blockchain-governance-mechanisms#section-off-chain-governance-mechanisms) 
*   [https://www.forbes.com/advisor/investing/cryptocurrency/defi-decentralized-finance/](https://www.forbes.com/advisor/investing/cryptocurrency/defi-decentralized-finance/)
*   [https://consensys.net/blockchain-use-cases/decentralized-finance/](https://consensys.net/blockchain-use-cases/decentralized-finance/)
*   [https://www.coinbase.com/learn/crypto-basics/what-is-defi](https://www.coinbase.com/learn/crypto-basics/what-is-defi)
*   [https://www.analyticsinsight.net/what-is-nft-and-how-to-earn-with-it/#:~:text=Sell%20Non%2DFungible%20Token%20on,Axie%20Marketplace](https://www.analyticsinsight.net/what-is-nft-and-how-to-earn-with-it/#:~:text=Sell%20Non%2DFungible%20Token%20on,Axie%20Marketplace)