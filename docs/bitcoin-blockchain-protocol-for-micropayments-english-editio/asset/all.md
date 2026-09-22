![](images/cover.jpg)

![image](images/cover.jpg)

# BitCoin  
Blockchain

![](images/line.jpg)

# *Protocol for Micropayments*

![](images/line.jpg)

# Kapil Jain

![](images/logo.jpg)

**FIRST EDITION 2020**

**Copyright © BPB Publications, India**

**ISBN: 978-93-89898-095**

All Rights Reserved. No part of this publication may be reproduced or distributed in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication.

**LIMITS OF LIABILITY AND DISCLAIMER OF WARRANTY**

The information contained in this book is true to correct and the best of author’s & publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners but BPB Publications cannot guarantee the accuracy of this information.

**Distributors:**

**BPB PUBLICATIONS**

20, Ansari Road, Darya Ganj

New Delhi-110002

Ph: 23254990/23254991

**MICRO MEDIA**

Shop No. 5, Mahendra Chambers,

150 DN Rd. Next to Capital Cinema,

V.T. (C.S.T.) Station, MUMBAI-400 001

Ph: 22078296/22078297

**DECCAN AGENCIES**

4-3-329, Bank Street,

Hyderabad-500195

Ph: 24756967/24756400

**BPB BOOK CENTRE**

376 Old Lajpat Rai Market,

Delhi-110006

Ph: 23861747

Published by Manish Jain for BPB Publications, 20 Ansari Road, Darya Ganj, New Delhi-110002 and Printed by him at Repro India Ltd, Mumbai

[www.bpbonline.com](http://www.bpbonline.com/)

# About the Author

**Kapil Jain** is a technology professional working in the IT departments of large US and European organizations in the Banking and Financial industry. He has done his engineering degree from Sri GS institute of technology and sciences, Indore, and has played the role of programmer, business analyst, architect, project, and program manager over the 18 years of his experience in the industry.

He has a wealth of experience in Financial applications built on Mainframes and works to modernize those applications using Microsoft and Java based tech stacks, cloud infrastructure, including building serverless applications. He has also developed applications with Open source tech stack like MERN and experimented with AI/ML algorithms. He has been deeply involved in the Bitcoin protocol for the last 3 years and also has experimented with various other blockchains like Ethrereum along with EEA (Permissioned version of Ethereum), Hyperledger and Ripple.

He has also been a panel member at a couple of conferences organized by Alliance University on blockchain and AI. In his leisure time, he likes to attend workshops and conferences and likes to play chess.

# About the Reviewer

**Jason Fernandes** is an entrepreneur, speaker and blockchain industry figure. Fernandes founded FinTech media outlet TokenJay.TV, internet portal ZeoCities.com and co-invented the world’s first Internet-based DVR, RecordTV. In 2019, Fernandes was conferred with the Karmaveer Chakra, a United Nations global civilian award for his work promoting financial inclusion through blockchain. Fernandes has featured in international outlets like the BBC, LA Times, Associated Press, MTV, ChannelNewsAsia, and national outlets like India Today, ZeeTV and the Times of India.

# Acknowledgement

I have written this book in my journey to learn the bitcoin protocol. During this journey, I have read many books, blogs, and also sometimes code and training from various blockchain projects, which made me sure about what my views are about the bitcoin blockchain and its protocol. I wanted to acknowledge and thank, first and foremost, Satoshi Nakamoto, whose writings I have read to get the initial and basic understanding of the protocol.

Behind the monikar, there is someone who is not so silent and a genius with numerous certifications, 17 university degrees and counting, 1000+ patents filed with 100s granted, going by the name of *Dr. Craig Steven Wright*. Everything I know about bitcoin is because of all the literature that I have gone through again and again that *Dr. Craig Wright* has so prolifically been publishing all these years. I could not thank him more than to say, if not for him, there would not have been this entire space. He is an inspiration to me personally to look up to someone who has done and created so much that I never thought was even possible to do for a human being. His depth in understanding all spheres of life is as good as humanly possible. In addition to his writings, there are many presentations by him available on bitcoin protocol on youtube published by CoinGeek during various conferences, which are a good reference along with the patents that he has created on blockchain technology available online. I could not have been able to write this book or understand bitcoin protocol, if not for *Dr. Wright*. Thanks again for all of your hard work *Dr. Wright*.

The next person I wanted to thank is someone behind the avatar Unwriter. A lot of tools and utilities and early application layer protocols on bitcoin were created by Unwriter, and I have dedicated many pages to them in the book. It was a journey for me as well to learn those application protocols and frameworks while writing about them and would like to thank Unwriter for her creations, which I have been inspired and learning a lot from. Those who have read Ayn Rand’s book, *Atlas Shrugged*, will be able to relate to the mythology of the 20th century motor company, and *John Galt*. Unwriter seems to play with this mythology as well and has left the chatroom she created in 2018 called 21st century motor company, to create a slack developer group called Atlantis where she was able to continue work without the bureaucracy that throttled innovation. Much like *John Galt*, Unwriter has not stopped working and has created a company called Planaria Corp, and if you end up being a bitcoin developer you can come and join Atlantis: **[https://atlantis.planaria.network](https://atlantis.planaria.network)**

The next person I wanted to thank is *Ryan X Charles*. He is one of the first sane voices that I found when I started listening, reading, and exploring the bitcoin ecosystem. He had created a company called Yours.org that time (2017) which was a bitcoin micropayment based content creation platform for user blogs. It still exists, but only in the form, it was many years ago as Ryan went on to create moneybutton while solving a problem of how to not have static bitcoin addresses on Yours.org. Ryan has also created the javascript BSV library of cryptographic tools needed for basic bitcoin development, and it is a very good starting point for any developer working with cryptography and how it is used in bitcoin. Moneybutton has been one of the first applications a new user will come across while using bitcoin. It still stands out for both educational resources, easy to use tools, and one of the pioneering companies in this space.

I would specifically like to thank the few members from the nChain team whose videos and blogs I have read to learn from, namely *Steve Shadders* and *Jack Davis*. In addition to that, I would like to thank many many contributors and voices in the Bitcoin SV ecosystem who I had been reading silently over these years and learning from them.

Further on, I would like to thank many many names that I have come across and learned a lot from the overall open source developer and business ecosystem in Bitcoin SV.

I want to also thank BPB Publication for giving me the opportunity to write this book. I would specially like to thank their very professional and supportive team that gave me guidance and creative freedom throughout writing of this book.

Finally, I would like to thank and acknowledge my parents, who have always motivated and supported me in all of my endeavors in life.

# Preface

If you have picked up this book, you are probably aware of the extraordinary progress that blockchain has made in the last decade since its inception with the bitcoin whitepaper. I see that as the tip of an iceberg, and my aim in this book is to walk you through the intricacies to demonstrate the full potential of what really is a blockchain and why it is an innovation that stands to change the world of the internet as we know it.

There is a large amount of investment and work ongoing as we talk today in not just the enterprise and government space, but also in a passionate and very talented open source developer community. Bitcoin SV or Satoshi vision is an attempt to go back to the original protocol, which was released by Satoshi Nakamoto back in 2008. It has taken 3 years (2017 to 2020) to remove all of the limitations that were introduced in the system, contradicting the economic utility of the original system of electronic peer to peer cash system. There are still minor things that need to be rolled back, and doing so, with keeping backward compatibility, is an arduous task that is currently being done by the bitcoin node software developer team at nChain.

Working in Banking, I have been involved with traditional payment solutions, including the legacy systems that were built in the 80s and are still operational. There is a large overhead due to the amount of technical debt built over the years and backward compatibility considerations apart from the issue of local payment types and message formats that each country has. This creates a huge amount of complexity in a core payment engine, which is used by banks to process these payments. With the more and more digital transformation of economies, the cost of processing a payment is becoming quite large when many of these payments are not supposed to have any fees. I was introduced to blockchain in the year 2016 when my employer wanted to explore permissioned blockchain solutions for smart contracts. We were part of the R3 consortium and did some work to explore the technology. We had little success wherein many POC and MVPs were built, but they never picked up commercially in terms of user adoption. I moved on to other technologies like data science for different use cases. It was not until 2017 during the first hard fork of bitcoin when I got myself starting to explore bitcoin for the first time. I did not take it seriously until 2018 when I realized what is the original bitcoin protocol and read the white paper again, but this time it took me weeks to read and understand it.

Over the last decade there has been an emergence of the protocol forks like Bitcoin Core - BTC, Bitcoin Cash - BCH and Bitcoin - BSV apart from a whole lot of others which are not even of any value to mention, there are developer groups taking the base protocol, changing some major things, and creating a completely new system of the public blockchain. We will talk about these limitations over the course of this book a lot, but in short, when I started looking into the blockchain ecosystem, I did not start with bitcoin, why? because my first “hearsay” based impression was that it is mainly something used for anonymous and illegal transactions in the dark net. From that point to come to the understanding that it is actually a system which is opposite of what my initial impression was, a system to create honestly in trade and transactions by introducing unbreakable traceability. This shows as a fact when you read the whitepaper, which mentions honesty about 14 times but has no mention of things like the name Blockchain, and anonymous or anything against the legal system.

With the emergence of private or permissioned blockchains that have been currently the space where most of the current enterprise blockchain investments are going into, have seen a little adoption even among the participants who joined hands. There are many reasons for it, but to me, the purpose of a blockchain is lost if its permissioned, because it will need the same set of rules and procedures as it is there in the current systems including the information security aspect which is becoming more and more critical as the tools at the disposal of hackers are getting more and more sophisticated. With over a decade of interest, passion, and work going into space, we still long to see a real world application that has come out of blockchain space and being adopted by common users. This stands to change now due to the power of the original, the original Bitcoin, which is also the original global public blockchain.

Bitcoin protocol achieves security of the network by its properties of publically storing information that is done in such a way that even if it is stored in cleartext and is open for verification by anyone, it still is able to protect the identity and transactions of the owners. We will see the methods during the course of this book on how it achieves it. This book aims to clear the fog which has clouded the overall space withholding the true understanding of this technology, which in the history of time will stand out as big innovation as much as the internet or as much as building the first internal combustion engine for automobiles was.

Over the last two years, the number of projects has risen exponentially, and Bitcoin SV blockchain now is seen as the only public or for that matter private blockchain that can scale up to millions to 100s of millions of transactions per second and has probably the best set of patents (about 1000 and counting, patents like threshold signatures, SPV, Rabin signatures, R puzzles, secret sharing with multiparty communications and a whole lot more) for blockchain technology available for free via an OPEN BSV license to build (allowed to build only on Bitcoin SV blockchain).

I bring this book as a learning guide for someone who has been interested but has not either been able to start reading and learning or has been overwhelmed by the sheer amount of same old wine in new bottle versions of numerous blockchains to take a step back and have a look at what was the original idea that created this industry and what really is bitcoin, a protocol for micropayments, data storage, and open trade which is real time (instant), cheap (1/1000th of cent fees), and truly secure (by being Byzentyne fault tolerant using POW system).

I wanted to reiterate that I see this book as a compilation of a lot of information and literature available in the ecosystem and it is my attempt to make it in a way that would enable someone who has never heard of bitcoin to read through and learn to become a developer, creator, builder, writer, or a user of the bitcoin blockchain.

I hope you’ll find this book valuable and that it will enable you to begin building intelligent applications and solve the problems that matter to you.

*—Kapil Jain*

# About this Book

This book was written for anyone who wishes to explore Bitcoin protocol from scratch or broaden their understanding of Blockchain overall. Whether you’re a practicing blockchain professional or a thought leader, an executive, a technology professional, or a student with no or little background on blockchain, you’ll find value in these pages.

This book offers a practical deep dive into every aspect of the bitcoin blockchain, including the maths behind the cryptography and intricacies of the protocol. It focuses on core principles and fundamental concepts to explain the constructs of a blockchain type system, giving a detailed overview of the protocol, applications, and utilities that can be built using it. Links are provided at every place where there is more than can be explored by developers for getting more hands-on exposure.

I wanted to reiterate that this book does not need you to have any background at all on the blockchain, just a keen curiosity and hunger to learn a new way of thinking. It not only covers the ideas and concepts which have been knit together to create an innovation that stands to change the world of IT products and services which exist today but also defines and leads the way future applications will be developed. Existing systems face many limitations when it comes to scaling, cost of operations, and IT security. This book provides a view into how using bitcoin blockchain can provide a solution to these limitations while still being able to create IT applications for every possible scenario and business use cases. All is done with rational, economic, and legal reasons behind it. With that in mind, this book will appeal to:

*   Developers who are interested in developing web and mobile applications and are looking to explore blockchain technology
*   Architects, Technology Managers involved in IT application and product development who are interested in going into the depth of blockchain architecture and how they can transform their existing applications to a blockchain based system gaining efficiencies in cost, scalability, security, and robustness.
*   Consultants and Executives can benefit immensely from understanding the breadth of the transformation that can be brought upon by the usage of the bitcoin blockchain. They will get a deeper view of how existing and future business use cases can be built for the B2C and B2B ecosystem, including some cases that were not possible with traditional and legacy technology architectures.

It will be best suited for the audience who has some web application development or technical background, but awareness of computer sciences is sufficient to understand the book. The bitcoin protocol is implemented in JavaScript, C++, Java, Python, but the protocol is just a set of rules and functions, and the applications can be implemented in any language making the protocol itself language agnostic. In the current ecosystem, most of the tools and utilities use open-source technologies such as JavaScript/Node JS and MongoDB for their development, so audiences with similar experience will have easy navigation through them.

**I have structured this book into three sections.**

The first section ([Chapters 1](#c01.xhtml) to [6](#c06.xhtml)) focuses on the past and gives an in depth and comprehensive overview of the protocol, and its economic incentive structure. It goes into details of cryptography, addresses, wallets, transactions, network, and mining.

**[Chapter 1](#c01.xhtml)** starts with a summary and overview of the bitcoin protocol with an explanation of what it is as it was described in the bitcoin whitepaper. It starts from the history of electronic cash systems and introduces what a blockchain is, what a transaction is, and what is a block along with what are the key aspects of a blockchain. It also introduces the bitcoin immutable public ledger and its properties.

**[Chapter 2](#c02.xhtml)** delves into the exclusiveness of what makes bitcoin work, its economic model, which enables honesty. What is the structure and utility of a network with money built in the system and describes the network structure of bitcoin and goes into details of the idea of decentralization and what it means.

**[Chapter 3](#c03.xhtml)** goes back to the basics and starts with the explanation of the mathematics and the cryptographic concepts used in bitcoin. It covers the details of ECDSA infrastructure that is used in bitcoin protocol and how the signatures and verification of signatures work. The chapter also covers the steps of generating a bitcoin address and how public and private key works in bitcoin.

**[Chapter 4](#c04.xhtml)** talks about wallets. It explains the concepts behind the wallets and the UTXO system, which is a replacement of the account based systems that exist in the current times in any financial system. It talks about various types of wallets and how they are used in bitcoin. This chapter also discusses in detail the idea of SPV(simple payment verification), which differentiates the bitcoin blockchain with every other blockchain that exists, including the bitcoin core (BTC) blockchain.

**[Chapter 5](#c05.xhtml)** takes a deep dive into transactions and an inbuilt programming language in bitcoin called Script. It details out various internal workings and mathematics behind the construction of a transaction along with various number formats used in bitcoin. It discusses the various OP Codes that are part of the Script language and how the various instructions in the scripts (input and output) are processed when a transaction is executed.

**[Chapter 6](#c06.xhtml)** concludes the [Section I](#p01.xhtml) with the discussion of Miners and mining consensus network in bitcoin. It goes into the basics of the network consensus, including the BFT algorithm and the block creation process used by the miners. It goes into various attack vectors that are possible on the bitcoin network and a bit of history of what happened with the network when these attacks happened, including the history behind various forks like BTC and BCH. It also talks a little about the history and current state of mining as a business.

**[Section II](#p02.xhtml)** of the book focuses on the present of the bitcoin ecosystem. It talks about what is happening now in terms of application protocol development, which works on the top of the bitcoin blockchain. It can also be considered as the backend development for bitcoin based applications.

**[Chapter 7](#c07.xhtml)** starts with the game changing application layer protocol called Metanet. Metanet is a protocol that is to be used on the top of the bitcoin protocol and works as an identity and information exchange method to build systems. Longer term goal is for this protocol to be the one where applications will be built to give users the privacy of their data back into their hands and to move away from the advertising based model of the current Internet.

**[Chapter 8](#c08.xhtml)** starts the discussion of various application layer protocols that are built over the period in time, which will create the base infrastructure of building any application using bitcoin blockchain as a means for data storage, transaction, and authentication (identity) layer.

**[Chapter 9](#c09.xhtml)** looks at how the blockchain works as a data store and looks at the BitDB framework in detail, along with the query language. This was one of the first formal data structure frameworks to use blockchain as a database. We also look at various other utilities that help in the CRUD operations for the bitcoin blockchain, which are part of the BitDB framework.

**[Chapter 10](#c10.xhtml)** is more focused on a lot of infrastructure-level protocols in the Planaria system of utilities that are not just focused on building consumer-focused applications but also equally usable for building large scale enterprise or, for that matter, government usage applications. This chapter will also look into the larger vision of application development using the bitcoin blockchain and what are the vast amount of possibilities available with this new technology.

**[Chapter 11](#c11.xhtml)** takes you down a lane where we walk through the bitcoin application development ecosystem of 100s of projects in each and every sphere of life and internet based trade and business community building up solutions that are using bitcoin blockchain along with other protocols that we have discussed. This chapter demonstrates a lot of theories that we have been discussing until now implemented in real consumer and business/enterprises based applications.

**[Chapter 12](#c12.xhtml)** moves back to looking at advanced level identity system creation of bitcoin blockchain and payment protocols like an idea called paymail which aims to simplify the usage of addresses which are large numbers to make them something like email addresses which are used not just by technically sound users, but also the common man. It also covers BIP270 in brief, which is another P2P payment protocol.

**[Chapter 13](#c13.xhtml)** takes a deep look into the various tokenization protocols which are being developed and also implemented on the bitcoin blockchain. This is very different from the current token and smart contract ecosystem in terms of creating legal tokens and smart contracts which do not require any new laws as opposed to the common misconceptions. This chapter also concludes the section in a way covering all of the application layer protocols that are currently existing on the bitcoin blockchain. This does not mean that a new protocol will not come in the future, but this gives a very detailed view of what is possible today.

**[Section III](#p03.xhtml)** of the book focuses on the future in terms of advanced applications using various emerging technologies that are currently being explored in the software development industry. We also look at what is to come in terms of law and regulatory aspects, which will define the make and break of the blockchain industry as a whole.

**[Chapter 14](#c14.xhtml)** takes a brief look into how blockchain usage will enhance using AI and machine learning by using high quality data provided by the bitcoin blockchain. We will look at various other concepts like cellular automata, IoT, big data, and creating autonomous agents that are integrated with the bitcoin blockchain.

**[Chapter 15](#c15.xhtml)**, the last chapter of the book, goes back to look at how blockchains are seen from the legal perspective by revisiting various terms and concepts that have been discussed during the course of the book. It also looks at what attributes of legality are yet to be implemented when it comes to regulation and how taxation will apply to bitcoin. It also looks at what are permissioned blockchain and one of the first use cases that central banks are exploring, CBDC. With that, the book is concluded.

After reading this book, you’ll have a solid understanding of what bitcoin blockchain and protocol is and will have a good overview of tools, protocols, and utilities that will help build your real world enterprise and consumer applications. Having this overview will enable you to quickly understand not just bitcoin but any blockchain that exists due to the fact that all of them have their core concepts created by inspiration taken from bitcoin.

If you’re a graduate student studying blockchain in an informal or a formal setting, you’ll find this book to be a practical complement to your education, helping you build intuition around the fundamental concepts that lead to the invention of the bitcoin blockchain network and familiarizing you with key best practices.

You can also learn a lot more about bitcoin by going to the various project and education resources mentioned in the appendix of this book.

With that, I wish to take you to a journey of a new way of using the internet, money, and application development, and I hope that you enjoy this journey.

# Errata

We take immense pride in our work at BPB Publications and follow best practices to ensure the accuracy of our content to provide with an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors if any, occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at:

**[errata@bpbonline.com](mailto:errata@bpbonline.com)**

Your support, suggestions and feedbacks are highly appreciated by the BPB Publications’ Family.

Did you know that BPB offers eBook versions of every book published, with PDF and ePub files available? You can upgrade to the eBook version at **[www.bpbonline.com](http://www.bpbonline.com)** and as a print book customer, you are entitled to a discount on the eBook copy. Get in touch with us at **[business@bpbonline.com](mailto:business@bpbonline.com)** for more details.

At **[www.bpbonline.com](http://www.bpbonline.com)**, you can also read a collection of free technical articles, sign up for a range of free newsletters, and receive exclusive discounts and offers on BPB books and eBooks.

# BPB is searching for authors like you

If you're interested in becoming an author for BPB, please visit [**www.bpbonline.com**](http://www.bpbonline.com/) and apply today. We have worked with thousands of developers and tech professionals, just like you, to help them share their insight with the global tech community. You can make a general application, apply for a specific hot topic that we are recruiting an author for, or submit your own idea.

The code bundle for the book is also hosted on GitHub at **[https://github.com/bpbpublications/Bitcoin-Blockchain](https://github.com/bpbpublications/Bitcoin-Blockchain)**. In case there's an update to the code, it will be updated on the existing GitHub repository.

We also have other code bundles from our rich catalog of books and videos available at **[https://github.com/bpbpublications](https://github.com/bpbpublications)**. Check them out!

# PIRACY

If you come across any illegal copies of our works in any form on the internet, we would be grateful if you would provide us with the location address or website name. Please contact us at [**business@bpbonline.com**](mailto:business@bpbonline.com) with a link to the material.

# If you are interested in becoming an author

If there is a topic that you have expertise in, and you are interested in either writing or contributing to a book, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# REVIEWS

Please leave a review. Once you have read and used this book, why not leave a review on the site that you purchased it from? Potential readers can then see and use your unbiased opinion to make purchase decisions, we at BPB can understand what you think about our products, and our authors can see your feedback on their book. Thank you!

For more information about BPB, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# [Section - I](#toc.xhtml#p01)

# [CHAPTER 1](#toc.xhtml#c01)

# [Bitcoin Protocol: Origins and Concept](#toc.xhtml#c01)

**“On the road from the City of Skepticism, I had to pass through the Valley of Ambiguity.”**

*\- Adam Smith*

Bitcoin is a new paradigm in terms of how a technology protocol can be built, implemented, and how it can change the world of internet-based applications and their architecture. This is very different from existing design patterns, architecture, and database structures that have been used by users and enterprises until now. This chapter will take you to the roots of the concept of Bitcoin protocol, a bird’s eye view of the overall structure, and some of the founding principles of the creation of Bitcoin Blockchain.

# [Structure](#toc.xhtml#s1a)

*   Skepticism to the solution, a Bitcoin road called the blockchain
*   History of electronic cash systems
*   Bitcoin as the protocol for value exchange network
*   What is blockchain and how Bitcoin works
*   Bitcoin is an economic system

# [Objective](#toc.xhtml#s2a)

After studying this chapter, you should be able to understand a bit of history and early attempts to create electronic cash systems. An overview of the Bitcoin blockchain and the transaction management system in Bitcoin. You will also learn about the ideas behind why Bitcoin is an economic system more than a cryptographic system and an immutable evidence trail. You will also learn more about a block and how the blocks are chained together forming a timestamped server storing transaction information.

# [Bitcoin: A Peer-to-Peer Electronic Cash System](#toc.xhtml#s3a)

There are few creations in the world that have brought about changes so large to human society, touching everyone’s life that it changes the way we think, we live and we interact with each other. These changes when they happen go through the phases of ignorance and rejection, contempt and resistance, notice and acknowledgment, and then wait and watch before they become accepted and adopted. Electricity is one such example, and so is the creation of the internet.

I believe we are at a place in time where we are going to witness another such invention happening right before our eyes which is going to take over the existing norms as the Internet did. This will enable a more transparent, independent, instant, and accountable medium of exchange of value, creating the perfect tool which the free market trade requires giving a real sense of financial sovereignty to an individual. It can help create organizations where decisions and power structure looks very different and not centralized, it can help make the governance of society much more transparent and efficient, it can help make an internet which is not based on advertising model but incentive model, and it can force-start a revolution in innovative hardware and software principles and architecture.

Yes, my build-up might bring the greatest skeptic thoughts to fore, but this is the journey I intend to take you in this book, going both into the technical and economic aspects of this once in a lifetime opportunity of creating a truly free market commodity and a completely new way of designing applications that don’t depend on monolithic silos. It comes with a public datastore (ledger) where no entry can be deleted to mask corruption or to have the possibility to associate every click of a button or a user action to be a microtransaction for things like content creation, gaming, and IoT but is having an almost guaranteed security model to beat the best possible implementation that currently exists but with a fraction of the cost. Let’s start this journey called Bitcoin which I feel is possible to be a ride filled with ambiguity to start with as it challenges many existing norms, but that is what every creation bringing fundamental change does.

*   **Bit**: A bit is the basic unit of information in information theory, computing, and digital communications. The name is a portmanteau of binary digit.
*   **Coin**: A coin is a small, flat, (usually, depending on the country, or value) round piece of metal or plastic used primarily as a medium of exchange or legal tender. They are most often issued by a government.
*   **BitCoin:** Bit of information and a coin which is money. Bitcoin with its transaction structure of Inputs and outputs is a carrier of both, Money and Information, at the same time. (Hence the emphasis on writing Bitcoin as Bit-Coin). The smallest unit is called satoshi and 1 Bitcoin represents 100000000 satoshis. Satoshi is a non-divisible integer value.

Bitcoin is like a smartphone, the phone/calling aspect is just one use case, but it can do a whole lot of things no one had imagined, similar to that, Bitcoin treated as money is only one use case but it can do a whole lot more things that no one has imagined. We will be exploring those features and use cases of Bitcoin in this book.

# [History](#toc.xhtml#s4a)

Since the advent of computers, there was always the thought that physical or paper money can at some time in the future be replaced by electronic money. This became more mainstream since the 1980s where a bunch of attempts was made to create this fabled electronic money. I will cover the few notable attempts in order to preview the thought process which made some impressions and these attempts, although not successful, did create an impact as an early effort to make electronic cash.

# [Ecash](#toc.xhtml#s5a)

Ecash was one of the earliest attempts towards creating electronic money. It was conceived by *David Chum* who is an *American Cryptographer.* He created Ecash as Anonymous electronic money based on a cryptographic electronic cash system in 1983. He did this work under the corporation named Digicash which later on went to collaborate with a few banks (Mark Twain Bank, Deutsche Bank) to provide them with a micropayment system in the USA, Australia, and Europe from 1995 to 1998. It met limited success with the best results coming from the US bank reaching up to about 5000 customers. The US bank was bought by another bank who was a large issuer of credit cards and eventually they stopped using Ecash. One of the main reasons it was shut down was due to the fact that it was anonymous and the credit card system was not, making the better solution win. Digicash went bankrupt in 1998 despite the flourishing e-commerce industry at the time where the credit card solution won the battle of currency of choice.

# [B Money](#toc.xhtml#s6a)

B Money was a hypothetical approach that got recognition for a few ideas which were good as they proposed another serious possible way to implement an electronic money system. It was conceived by *Wei Dai*, a computer engineer and a graduate of the University of Washington. He published a paper in the year 1998 introducing the idea of B-Money. He was trying to conceive of this system heavily inspired by Tim May’s idealistic crypto-anarchy world where governments are not just temporarily destroyed but permanently forbidden and permanently unnecessary. It hypothesized a community that uses its own, 1. The medium of exchange and 2. A way to enforce contracts. Both of these services traditionally provided by the government in effect replacing the government with this new system. It involved an assumption of the existence of an untraceable network in which senders and receivers are identified via public keys and every message is signed by its sender and encrypted to its receiver (pseudonyms).

Money in this proposed system could be created by anyone who can provide a solution to a previously unsolved computational problem, the money unit created proportionate to the amount of computing effort done. Transfer of money can happen by broadcasting the proposed transaction on the network by the sender and receiver. It required all users running a computer system connected to the network by default. It also involved a 3rd party who will do arbitration in case of a need for enforcing contracts. The problem of how to set up an Arbitrator (third-party) was solved by a proposal that a second protocol is used for keeping the accounts ledger by a subset of participants who needs to be trusted to a certain degree. The mechanism to keep a check on this subset, they were required to deposit a certain amount of money units to a special account which was to be later used as fines in case of misconduct.

This system was never implemented due to various challenges in terms of the right approach for money creation, the non-existence of the proposed network, and the overall complexity of usage.

**Reference: [http://www.weidai.com/bmoney.txt](http://www.weidai.com/bmoney.txt),** W. Dai, “b-money”, 1998.

# [Ripple Pay](#toc.xhtml#s7a)

*Ryan Fugger* created a community-driven open source project called Ripple Pay (2004), as defined by him, *Ripple is a project to build a new kind of monetary system based on the trust present in our ordinary social and business relationships:*

*   My IOU will only be accepted by my friends who trust me. I cannot pay strangers.
*   Each of my friends will only accept an IOU from me up to a certain amount, depending on how much each one trusts me (measured by how much credit each will offer me).
*   If my friends accept my IOU, they cannot use it as a currency outside the circle of my trusted friends.

Creating a social barter system application run by communities who trust each other rather than trusting an institution like the Bank. This became the basis for the future cryptocurrency implementation of Ripple and XRP.

**Reference: [http://ripple.ryanfugger.com/decentralizedcurrency.pdf](http://ripple.ryanfugger.com/decentralizedcurrency.pdf)** Ryan Fugger. Money as IOUs in Social Trust Networks & A Proposal for a Decentralized Currency Network Protocol. April 18, 2004

There were few other attempts to create electronic cash/decentralized money such as Mojo Nation (m-net), Edonkey, and Liberty reserve but those also attained only little success in small groups. Both Ecash and Liberty reserve which achieved some success eventually were shut down by governments as they were trying to bypass regulations or creating a provision of anonymous money which poses a risk of facilitating criminal behavior or an alternate currency in competition to the government-issued legal tender. A lot of the above ideas have their roots in the Crypto-Anarchist movement or an inherent dissatisfaction with the existing government or the finance and banking system. It was described in a lot more details in the Ripple Pay system as the reason for it to exist is to not trust who (institutions) we are forced to trust but to trust who (friends and family or community) we already trust and create a barter system based currency.

These ideas, albeit quite idealistically attractive but were not as practical as the solution to the problem of the government or banking system not working as expected. They cannot solve it by being a system outside it, but only by a system working inside it. One can start to root for a world without government, and it could be argued that it is a possible or ideal way to go, not the less, in reality not possible.

And then came the Whitepaper. A message was posted and shared to a cryptography mailing list which goes something like this:

![](images/Fig_1.1.jpg)

**Figure 1.1:** First ever post related to Bitcoin by pseudonym Satoshi Nakamoto published the Bitcoin whitepaper

Bitcoin whitepaper was circulated in November 2008 to a cryptography mailing list and communities for peer reviews and feedback before the final launch of the network that happened in January 2009.

**Reference: [https://papers.ssrn.com/sol3/papers.cfm?abstract\_id=3440802](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3440802)** *Wright, C. (Pseudonym: Nakamoto, S).* Bitcoin: A Peer-to-Peer Electronic Cash System; Whitepaper: Sydney, Australia, October 2008.

The abstract documented in the whitepaper is probably the best description of bitcoin protocol which creates a unique network for value exchange, Peer to Peer electronic cash system. As I have described the earlier attempts where the proposed systems either did not pick up or failed and was found lacking something from the system architecture perspective incompleteness of functionality and security or lacking the business architecture view where it can become an enterprise-grade solution to be used. Bitcoin was something that addressed both. The simplicity of a system which breaks down the problem of transferring a message securely between two non-trusted parties, and also ensuring there are economic incentives for keeping the non-trusted parties engaged in the system. To understand Bitcoin, you need to look both from a technical perspective of things, and also from the economic perspective of things as the full proof aspect of the security model of Bitcoin is not technical, not cryptographic, but economic.

# [Introduction to Bitcoin](#toc.xhtml#s8a)

The internet has revolutionized trade. E-Commerce has been an exponentially growing industry and that is just one form of trade. Supply chain, banking services, and content creation for information (media, entertainment, news, education, FMCG) all industries are going through a phase where they have embraced the internet to expand their outreach and user experience of their services. Currently, the payments/monetization of services is heavily dependent on financial institutions serving as trusted third parties to process electronic payments. And to quote from the whitepaper:

*“While the system works well enough for most transactions, it still suffers from the inherent weaknesses of the trust-based model. Completely non-reversible transactions are not really possible since financial institutions cannot avoid mediating disputes. The cost of mediation increases transaction costs, limiting the minimum practical transaction size and cutting off the possibility for small casual transactions, and there is a broader cost in the loss of ability to make non-reversible payments for non-reversible services. With the possibility of reversal, the need for trust spreads. Merchants must be wary of their customers, hassling them for more information than they would otherwise need.”*

The core idea to challenge the system above is not to subvert the reporting of the information to the concerned legal entities or the government, but the system that exists right now was made to mirror the manual, paper-based systems that existed before the invention of the internet and computers and it was but the natural first step to migrate that manual business processes by automating them. After decades of having those systems now we are starting to see their limitations due to exponential increase in both the volume and usage of the exchange of information or even payments. In a country like India, we are also moving away from a cash-based system to a digital system where all of the payments that are of more than a certain amount are being mandated to be in digital form. The future holds even a larger volume of transaction requirements with things like IoT coming into day to day and household usage.

Let me pull up the overview of the current financial network and how they work to illustrate the number of hops and the number of parties that are involved in a simple payment done. I will take a typical example here. This is to give you an overview of how the two systems compare and stand when it comes to an individual. Due to the nature of the trusted system, the whole structure becomes quite complex with many trusted third parties getting involved who share part of the risk for the transaction and hence also receive a fee from the transaction. (*[Figure 1.2](#c01.xhtml#fig1_2)*)

In Bitcoin, the transaction happens **Peer to Peer (P2P)** and the recording of transaction happens on a publically shared common record book called ledger or blockchain. But a bit differently from the existing systems, as the third-party is trustless.

Let’s have a look at the figures below for the existing and the new system that can be made with Bitcoin:

![](images/Fig_1.2.jpg)

**Figure 1.2:** A typical Credit card transaction process flow

In a Bitcoin network the above system works in a bit different manner, as shown in *[Figure 1.3](#c01.xhtml#fig1_3):*

![](images/Fig_1.3.jpg)

**Figure 1.3:** A typical and high-level transaction process flow using the Bitcoin blockchain

There are the following things that have changed from *[Figure 1.2](#c01.xhtml#fig1_2) to [Figure 1.3](#c01.xhtml#fig1_3)* but the same result of money being transferred from the customer to merchant has happened:

*   In place of multiple third parties (banking institutions, intermediary and settlement bank) we have only one third-party which is played by a number of competing miners reducing the number of hops a transaction has to take to reach the intended recipient.
*   There is always more than one miner (typically 3 to 10s) mining and hosting the blockchain’s public ledger at any point in time making it distributed public ledger, who works as the non-trusted validators for transactions and maintain the integrity of the underpaying public ledger.
*   The customer only has to send the transaction via his software to the public ledger. Once updated in the ledger, the merchant owns the money so this simplifies the overall business process and again removes the reversibility of the transaction.
*   In place of user accounts and the various sets of the payment transaction and network, all coins are associated with a private key and there are standardized transaction types used for the exchange of coins between two users using the public key for the intended recipient, making it completely secured.
*   Transactions that are computationally impractical to reverse would protect sellers from fraud, and routine escrow mechanisms could easily be implemented to protect buyers.
*   Then of course if there is a legal dispute due to which the transaction can become invalid, we can reverse the transaction but typically that will only happen for something that is ordered by a court of law and is significant in value due to the huge effort involved in it.
*   The ledger where the accounting entries are made (Bitcoin public ledger) is distributed across the globe making it resilient to any single point of failure scenarios.

# [Transactions](#toc.xhtml#s9a)

An electronic coin is defined as a chain of digital signatures and an owner transfers the coin to the new owner by a transaction. A transaction consists of an input record (owner digitally signing the hash of the previous transaction) and the public key for the next owner (recipient):

![](images/Fig_1.4.jpg)

**Figure 1.4:** Transactions in Bitcoin, Source - Bitcoin Whitepaper

This diagram above shows how a transaction is in terms of its components and ownership of the coins that a transaction is made to transfer. The Cryptography used for generating the public and the private key is not the commonly used PKI but ECC which will be discussed in detail in a chapter later in the book.

Payee or recipient of a transaction can always verify the validity of the transaction by using his private key to validate the transfer of ownership via this transaction as shown above. Typically the trusted 3rd party like Financial institution acts as the verifier of the validity of a transaction to address (something that is commonly called the double-spending problem) to ensure that the owner of coins is not signing the same coins to more than one receiver. This is Bitcoin is achieved using a timestamp server which stores the log of all of these mentioned transactions, with time-stamped and digitally signed chain of ownership of all coins at any point in time, in time-stamped blocks which again are connected with each other in reference just as the transactions shown in the above picture. This server came to be known more commonly as a blockchain:

![](images/Fig_1.5.jpg)

**Figure 1.5:** A representational view of the blockchain

A blockchain is a public book of record that can be verified by anyone if they are willing to put in the work for the infrastructure setup like downloading the complete blockchain and running a *node* but is typically done by a new type of entity which is referred to as **miners**. Mining is an analogy of physical miners who dig through mountains of pieces of gold and the better equipment and investment they have in mining, the better their chances are to be able to find gold. In Bitcoin, these mentioned transactions are grouped into a block. This will be discussed in detail in the chapter when we discuss mining, but it’s miners who work in competition with each other in a game of adding the next block every 10 mins and win a *coinbase* transaction which is similar to a reward winning them 6.25 bitcoin at the current times. Miners also are paid a small amount of fee (typically 1/100th of a cent of a USD per transaction) for the mining verification service they provide for users of the blockchain. Needless to say, the economic incentive for miners is coming via both, the mining reward and the transaction fees.

# [Transaction block](#toc.xhtml#s10a)

Let us look a bit more into the details of a block of transactions. A block is a collection of transactions that happened in the stipulated amount of time available from the previous block. The Transactions that made it to the block in that time period are put in the order they have been received (by the miner) and each transaction when created is always represented by a hash. A hash is part of many cryptographic tools that Bitcoin uses to achieve security as it has a unique property as described below.

A Hash is a cryptographic function with its unique property that it can transform a given input to a fixed number of alphanumeric strings. The input provided can be numeric, alphanumeric, media files, and binary files. The output hash can be chosen to be 64-bit, 128-bit, 128-bit, or 256-bit depending on the choice of the hash algorithm. Another unique property of this hash function is that it is a one-way function, which means there is no way to generate the data if someone has the hash with them. This effectively means that even a one-character change in the input data can completely change the value of the hash output. These two unique properties enable the use of this hash function as a digital fingerprint for the data processed through the function.

Each transaction once created, will have a hash generated for it using the SHA256 algorithm and this is how the content and a transaction looks like for transaction with Hash: `828ef3b079f9c23829c56fe86e85b4a69d9e06e5b54ea597 eef5fb3ffef509fe`

**([https://whatsonchain.com/](https://whatsonchain.com/))**

![](images/Fig_1.6.jpg)

**Figure 1.6:** A typical Bitcoin transaction

As you can see each transaction has some metadata for it (timestamp, confirmations, the fee paid, block number) and then there are details of input and output for the transaction. All the data that belongs to the transaction is put through the SHA256 hash function (twice!!) and a 32 byte and 64 character length hash for the transaction is created.

Any block contains a large number of transactions, and now with increasing block sizes of a possible supported block, this could go into a million and plan is to make the block size unlimited so that miners can benefit the most when the block rewards are not providing sufficient value for their work to earn more rewards by the fees present in the large transaction volume. The structure of a block looks like this:

![](images/Fig_1.7.jpg)

**Figure 1.7:** Structure of a block

Each block consists of a few fields which are described in the below table with the properties for each of the fields present in the block:

 
| **Block Size** || **The size of the block, in bytes** || **4 bytes** |
| --- | --- | --- |
| Block Header || Block Identification details

*   Version:
*   PrevBlock :
*   MerkleRoot:
*   Time:
*   Bits:
*   Nonce:

 || 80 bytes |
| Transaction Counter || How many transactions are present in the block || 1-9 bytes (`VarInt`) |
| Coinbase Transaction || The first transaction of each block. This transaction contains the Block reward for the miners. Currently, this reward is 12.5 BSV || variable |
| Transactions || User transactions which contain input, output, and fees || variable |

**Table 1.1:** Block field details

Once a block is created, the miners go through the mining process to add it to the blockchain to win the block reward and the transaction fees for their effort for preparing this block. There is however one more important concept called **Merkle root** that should be discussed regarding the block header information mentioned in *[Figure 1.8](#c01.xhtml#fig1_8).*

The transactions that are stored in the block are made immutable to prevent any malicious attempt to change the entries made in the blockchain using the idea/concept of storing all of the transaction hash that is in the block in a Merkle tree structure. This acts as a checksum and even if a small character in a single transaction changes will break the integrity of this information and the change will render the block invalid and hence not accepted by the consensus/validation process of miners.

In cryptography and computer science, a hash tree or Merkle tree is a binary tree in which every leaf node is labeled with the hash of a data block. This is shown as the Hash (tx1), Hash (tx2), etc. in *[Figure 1.8](#c01.xhtml#fig1_8)*. Every non-leaf node is labeled with the cryptographic hash of the labels of its child nodes. This is shown in *[Figure 1.8](#c01.xhtml#fig1_8)* as Hash 1-2 and Hash 3-4. Hash trees allow efficient and secure verification of the contents of large data structures. Demonstrating that a leaf node is a part of a given Merkle tree requires computing a number of hashes proportional to the logarithm of the number of leaf nodes of the tree.

Let us look at it with a diagram:

![](images/Fig_1.8.jpg)

**Figure 1.8:** A Merkle root hash representation for a block with 4 transactions.

If there are an odd number of transactions, suppose there is no **tx4**, the hash 3-4 will just be the hash 3-3 by using **tx3** hash twice and the same process applies. Now that we have a view on what is a block, let us go back to the idea of the timestamp server that we started this description with and define what a blockchain is.

Once the hash of the transactions is stored in a block with the timestamp, it becomes a publically stored record of truth which cannot be tampered with by any means. These blocks stored chained with each other act as a timestamped server for the information stored in them. It is not just published publicly but also implemented as a distributed timestamp server on a peer-to-peer basis using a proof of work system.

The proof-of-work is a system that is designed to make a set of competing miners use computational power to generate a hash for the next block that they are competing to add to the existing blockchain. This new hash to be generated is controlled in terms of how complex it is to generate by one of the fields mentioned in the block header called the nonce. Miners use this computational power, continuously scanning for a value that when hashed, such as with SHA-256, the hash begins with a number of zero bits. The nonce defines these leading numbers of zero bits to control the difficulty of this process and is done by incrementing it in a block until a value is found that gives the block’s hash the required zero bits. The average work required is exponential in the number of zero bits required and can be verified by executing a single hash.

This process of using a proof of work system to make a block ensures that the block cannot be changed once generated without redoing the same amount of computational work. You can also see that as there are more blocks chained after any block, the work to change said block will include changing all of these blocks that are chained as well and this way the work to alter the block increases exponentially as the depth of the block increases in the blockchain:

![](images/Fig_1.9.jpg)

**Figure 1.9:** Blocks chained with each other and their chaining with past block

The last step in the selection of block involves a number of miners coming to an agreement that the winning miner block is what they all agree to add to the blockchain by a network consensus proved by the winning miner’s proof of work. This essentially is the system that replaces a trusted network to validate the correctness of a transaction which we discussed in *[Figure 1.2](#c01.xhtml#fig1_2).* All of the miners who are investing their CPUs vote in this network consensus to decide on the majority decision for the next block addition and block winner among them by a consensus method described as Nakamoto consensus which essentially is: Proof-of-work is essentially one-CPU-one-vote.

There is always a possibility that multiple miners solve the hash puzzle at the same time and the blockchain may have a fork happening from time to time. This automatically will resolve as the network will keep adding new blocks to one or the other fork and the majority of (miners) decisions will be represented by the longest chain demonstrating greatest proof of work:

![](images/Fig_1.10.jpg)

**Figure 1.10:** A temporary fork or orphaning of a block in the Bitcoin blockchain network

The network splits are possible but eventually, the longest chain is the one that survives and these forks die off. These are meant to be uncommon but perfectly natural scenarios. The block is usually referred to as orphan block and usually block 3 and 4 will be added to something called an **orphan pool** and it’s only when the next block is added one of the orphan blocks becomes the confirmed block. In short, an orphan block has a parent block but no children blocks.

The obvious concern here in the case of chain death scenario is that what happens to the transactions that were included in block 4 but not in block 3, do those transactions also die along with that fork? The answer is quite simple. A number of miners receive the transactions from individual wallets or business nodes, not all at the same time. All of these transactions are collected in something called a **mempool**. This can be considered as a temporary storage area where miners pick up transactions to make the new block. If the miner who mined block 3 did not pick up some transactions that were included in block 4, a miner who has (during network consensus) agreed to the transactions included in the block 3, will consider those transactions not yet included in the blockchain and hence a valid transaction and will include them in the block 5.

The last bit about mining is the concept of the nonce. This is a parameter that is used to control the difficulty of the block hash that is to be generated. The value is relooked at every two weeks and is determined by a moving average targeting an average number of blocks per hour. If they’re generated too fast, the difficulty increases and vice versa to keep block generation to an average of one block every 10 mins.

Bitcoin block is approximated to be added every 10 mins. For Bitcoin to work correctly it needs to be somewhere between five minutes and 20. The exact ideal optimal time is not calculable because it varies by time of day, season, use, electricity price, and many other factors that are not standard. This 10 mins time period was set primarily for introducing a sufficient amount of difficulty so that a minimum CPU power is invested to ensure the security of the network. A miner has to perform a set of tasks (Validate for veracity so that only valid blocks are propagated) before a new block can be added.

In validating a block, the miner will perform the following functions:

*   Block’s data structure is in the correct format.
*   Hash of block’s header is less than or equal to the target difficulty set for the ongoing two-week period.
*   The size of the block is less than or equal to the maximum block size permitted (e.g., currently 2 GB).
*   The first transaction of the block is a coinbase transaction, which pays the winning miner and only one coinbase transaction is present.
*   Each transaction in the block is valid. Each transaction, as well as its hash, must be individually checked and validated for also being accurate in terms of input and output amount of coins it has.

The concept of block size mentioned above became one of the key discussions and contention points in the Bitcoin ecosystem in the recent few years causing multiple forks of the original Bitcoin chain creating a demerger sort of event in prevalent terminology. The block size defines the capacity of Bitcoin blockchain defining what is the maximum number of transactions that are being processed every second, in turn defining the solution of the issue of scaling. I will briefly mention below the 3 major forks of Bitcoin which are based on few attributes either limited scaling or another concept related to privacy and anonymity which will be discussed in detail towards the end of this chapter:

*   **BTC**: This fork is currently having a block size of 1 MB as maximum limiting it to process a maximum of 3-5 transactions per sec. This also caused the introduction of RBF (replaced by fee) concept to enable a higher fee to expedite the inclusion of a transaction to get priority in processing. This rendered BTC not suitable for microtransactions.
*   **BCH**: This fork currently has a limit of the block size of 32 MB and is more focused on anonymous transactions by using concepts like schnorr signatures and coin mixers. It partially is suitable for microtransactions but has limited capacity due to limited block size making it unsuitable for enterprise adoption. Legally, historically, fully anonymous transactions are banned eventually (like Ecash).
*   **BSV**: This fork which continues to implement the original design of Bitcoin created and defined the whitepaper. In 2019 the block size was 2 GB enabling it to process about 14,000 transactions per sec and is most suitable to allow and enable microtransactions making it the most suitable candidate to solve the scaling issue for blockchains. This version is also following the original protocol as defined by Satoshi, and with an upgrade in 2020, called Genesis, it can now support unlimited block size. This means that it is left to the miners to decide what block size they produce dependent mainly on the current state of network and mempool. In this version, the Bitcoin protocol will be locked down to the original design and provide stability for applications to be built on top of a stable protocol (like IPV4 and IPV6). Anonymous transactions are not supported but private transactions are possible, supported, and recommended. Low fees and stable protocol has created a Cambrian explosion of new application and solution development in BSV which will be discussed in great detail in the coming chapters and this book is focused on this version of the fork in all reference to Bitcoin.

# [Bitcoin public ledger: what makes it work?](#toc.xhtml#s11a)

Let’s take a step back absorbing what we have discussed up till now and try to see what is Bitcoin and what is Bitcoin blockchain.

Bitcoin is a protocol which is implemented using a large set of cryptographic tools and clever economic formulations to create a global, instant, cheap, and peer to peer value exchange via electronic cash. The Bitcoin blockchain is a global, public double-entry accounting ledger that is open to audit, update, and manage by anyone willing to put the right investments for the right use case they want to engage in.

A little description of what is a ledger, it is a book which records financial transactions. A general ledger is a double-entry bookkeeping method — where each financial transaction is posted as a debit and a credit entry. Typically these ledgers are kept summed up on the main ledger to show the full view of net assets with the further breakdown of the entries maintained separately in a sub-ledger, which can always be rolled up to produce the overall general ledger.

Bitcoin as it was created was one single global public commodity ledger that comes with a sophisticated protocol to do CRUD operations (Create, Read, Update, Delete) on it using its native value exchange mechanism, satoshi. It is probably the first tech architecture that is inspired by naturally existing biological systems that are quite simple but elegant in design, works in an open, and transparent way, and incentivized by ruthless competitiveness. These are the same principles that for the first time in the history of technology have been implemented to create a system that has worked in the past 11 years of its existence flawlessly. Even though you might have heard many hacks related to Bitcoin but those all were always hacking done at the entry and exit points called Cryptocurrency exchanges, and never done on the Bitcoin blockchain.

The security model of Bitcoin is not cryptographic, but economic. When I say this, it does not mean that the cryptographic tools that we have discussed till now and a lot more which we will be discussing more are not adding to security, but breaking the security model would require a large investment which grows exponentially as the complexity of the nature of intent. One of the basic problems that Bitcoin solves is the problem of double-spending. What if I spend the same coins that I have twice, how is that protected by economic incentive? I have described this situation briefly when I was talking about blockchain so if I want to do double-spending, let’s see what I need to do:

1.  Perform the first transaction and get that included in a block.
2.  Get 51% of network hash power to be able to control next blocks and network consensus (this is called 51% attack).
3.  Create the double-spend transaction for the address he (or they) control.
4.  Another option will be to create empty blocks to keep getting mining rewards.

To gain control of hash power to do a 51% itself will mean a very large investment either by one entity or many miners forming a cartel to do this attack and to quote satoshi, \[*the miner\] would have to choose between using it to defraud people by stealing back his payments, or using it to generate new coins.*

And satoshi continues, *He ought to find it more profitable to play by the rules, such rules that favor him with more new coins than everyone else combined, than to undermine the system and the validity of his wealth.*

For example, if the attacker chooses option 4, then since this being a public ledger, all will know about this attack and the value of the coin will drastically reduce. If he chooses option 3, the attack surface is limited to his coins and again, it is not always possible for the same miner to mine all future blocks and the network eventually will know about this ongoing attack soon enough, which makes it more profitable for the attacker to use this hash power to mine new coins rather than attack the network. This is what I meant by the economic model providing the needed security to the Bitcoin blockchain.

# [Bitcoin is an immutable evidence trail](#toc.xhtml#s12a)

This is rather a very bold headline which I have included intentionally to emphasize for the fact of what Bitcoin is contrary to what is the popular perception of what it is.

The whole idea is that this hash when published on a publicly available source like the blockchain signed using the digital signature (which is tied back to identity) can never be hacked, changed, or forged making it the best possible security that exists today. Currently, there is a billion dollars industry exists that secures records for accounting purposes. This now can be done for fractions of cents using the Bitcoin blockchain. You take the data and make a hash, upload this hash on the blockchain using a transaction and that is it. The hash here is an index which means that even if a character changes in the source of data the hash value is completely different making that validation against the uploaded has failed. This is a provably better and secure way to do accounting and record-keeping. Also if there is a new version of the document created for example, then you update the entry on the blockchain with a new transaction along with the audit trail for this change. This is simply a use case for every government, corporation, and any company that exists and wants to do a simpler recordkeeping saving potentially billions in cost.

Going back to the roots of Bitcoin, let me show the message that was included in the first block that was ever mined which had one Coinbase transaction in it and that transaction has a message included by Satoshi who mined that block.

![](images/Fig_1.11.jpg)

**Figure 1.11:** Genesis block mined by Satoshi: “ The Times 03/Jan/22009 Chancellor on brink of second bailout for banks”

There were two significant aspects that were presented in this message:

*   Ensuring the timestamp for the block contains the current date and the news article headline from *The Times* to signify that the block was not mined before the said date,
*   The philosophy behind Bitcoin.

The message created an impression that Bitcoin is a response to the financial crisis that happened during 2008 and is a solution to counter the fractional reserve and other financial misappropriations done by existing financial system entities giving an impression that it is a system to replace banks and government’s control of the financial system or an anarchist system, while the truth being quite far from it.

Let’s have a look at the full article which was published on the said date in the newspaper:

![](images/Fig_1.12.jpg)

**Figure 1.12:** The Times newspaper article which was referred to by Satoshi in the genesis block

The year 2008 was a year of great trouble globally for the financial system which indulged way too heavily in the toxic debts of their own making. This created many financial institutions to collapse to bankruptcy and many were bailed out by the government nationalizing their toxic debts, and this not just happened in the USA or UK but across the world. The root cause of this lied in incentivization of the bad behavior that the banks indulged in by flouting honest banking practices and going for the quick buck for the moment and pushing the real problem down the road for someone else to handle it.

In this article, it was discussed that a second bailout was needed to keep the banking systems sustained by buying their debts with options like - a bad bank would be created to dispose of bad debts. The treasury would take bad loans off the hands of troubled banks, perhaps swapping them for government bonds. The toxic assets, blamed for poisoning the financial system, would be parked in a state vehicle or bad bank that would manage them and attempt to dispose of them while detoxifying the main-stream banking system.

Effectively governments decided to provide more liquidity to banks when they were trying to be conservative in terms of their lending in a way making them continue the same old ways which caused the problems in the first place. The solutions never really were considered but again the problem was bandaged and postponed via these measures. Governments saw this as something that cannot be left to the market to make sure they can get re-elected by this inflationary process driven by the government rather than giving time for markets to take self-correcting measures.

The fact, as conveyed in the message, was that Bitcoin was never anti-banking. It was against the intervention by governments in the free market, making it more of a libertarian and that being the free-market approach to capitalism, unlike the Keynesian approach which was being followed.

This message in a way that attracted the first set of adopters to Bitcoin, some of who understood the message and a whole lot more who saw this as an anti-banking system of money giving them an alternative to subvert the AML and other regulatory mandates that banking made them follow.

The first big step in the wrong path was the adoption and usage of Bitcoin by WikiLeaks which satoshi himself spoke against on Bitcoin talk forums just a little while before he disappeared. Since then the path of adoption of Bitcoin went to dark markets, things like dark markets of silk road and hydra where it became the currency of choice due to no or weak regulatory oversight at the entry and exit gateways that came to be known as crypto exchanges and crypto OTC desks. The price of the Bitcoin surged due to this unfortunate utility that is found among the community which was trying to subvert the banking system.

Another set of users who adopted Bitcoin during that period (2011 - 2015) were black hat hackers who also found solace in a currency that they can easily move around using things like coin mixers in addition to it being a complete digitized form of money. It was also used as one of the tools to move money across to countries that were blocked due to sanctions like Iran and North Korea which did not have access to the SWIFT network. Another big event was a large hack that happened at one of the biggest cryptocurrency exchange called **Mt. Gox** which was one of the main Exchanges used by things like Silk Road users along with its scams that happened during this period.

However, later as things turned out, the usage of Bitcoin provided law enforcement an immutable evidence trail of the money, it took some time for the law to catch up, but soon they were able to shut down things like Silk Road. It is an interesting court case to study how Bitcoin helped in tracing the funds to various hands and pinning down the perpetrators who were caught and jailed.

Former Department of Justice prosecutor, *Katie Haun* who set up the first-ever *cryptocurrency task force* for the U.S. government and also led the investigations into the Mt. Gox hack and the corrupt agents on the Silk Road task force. This was the first case of the U.S. government using the Bitcoin blockchain to fight fraud, not just against criminals but against their own. The investigator details out how Bitcoin was used in this case to trace the perpetrators in this video presentation:

**[https://youtu.be/19oYvXhQbWc](https://youtu.be/19oYvXhQbWc)**

She describes in detail how when the law enforcement agent who himself turned out to be a criminal erased all the book entries at the traditional financial institutions but due to him using Bitcoin for these transactions, they were able to trace the money and able to produce the complete evidence trail in the court of law which was accepted as well:

![](images/Fig_1.13.jpg)

**Figure 1.13:** convoluted web of Bitcoin transactions that the undercover FBI agent who himself was corrupt and trying to delete could not do so on blockchain and was eventually caught. Copyright with a16z ([https://a16z.com/](https://a16z.com/))

She now teaches crypto/blockchain at Stanford business school. This is what I meant when I said, bitcoin is a mass surveillance system that provides an immutable trail of evidence.

Bitcoin is pseudonymous. This means that it is private but not anonymous. It publishes all the transactions on a public blockchain in cleartext for anyone to audit and run things like machine learning algorithms to perform tracing analytics on it. It however is private, which means that unless there is a need to know (like a court order) and if the user is using it with the intent to keep their financial transaction private (by not reusing their public addresses multiple times) as privacy is built-in.

This subject can itself be written about at length but since that is not the focus of the book I will leave this subject here and focus on the technical protocol details from now on. I felt this was needed to be detailed out to counter many narratives that are present in the current times.

The intent for the inclusion of these details was that the mainstream view of Bitcoin being a currency that is anonymous is factually incorrect. On the contrary, it works as a transparent open ledger and this created a space for a whole new set of cryptocurrencies blockchains focusing on being anonymous like monero, zcash, and a few others. At the time this book went to print regulatory clarity continues to elude the concept of the public blockchain, but many countries are actively working on legislation.

One last aspect of Bitcoin that I have intentionally not discussed up till now is the idea of decentralization. The Bitcoin public ledger is considered decentralized as it is distributed across nodes who are willing to host the blockchain across the world. This provides for another big security feature with respect to the destruction of any single node which is hosting the data as a single point of failure which is a basic need for any enterprise data center. The usual solution these enterprises (like banks, financial institutions) have to address this (referred to as disaster recovery) is to keep multiple copies for their whole system/application hosted on data centers at multiple locations. This is a huge cost duplication that is needed for the security of data that Bitcoin achieves just by its native architectural design.

# [Conclusion](#toc.xhtml#s13a)

It might feel intimidating when you start to look at the vast concepts present in this chapter at first, and especially if you are completely new to Bitcoin. It might also be the case that you may feel things that are different are not making that much sense, but as we keep going further down into details, you will see that all of these concepts, open questions and ideas will get tied together to form a base layer protocol which has the potential to be the plumbing system for the new age financial network which was needed to be built on top of the internet. The next chapter will start with a description and digging a bit deeper into the economic model and the network structure of Bitcoin.

# [Questions](#toc.xhtml#s14a)

1.  What were the main reasons that early attempts to electronic cash systems were not successful?
2.  What is the difference between anonymous and private?
3.  Why is a public ledger like Bitcoin also private?
4.  What is a blockchain and why timestamps and digital signatures are important to be present in transactions?
5.  Why did Satoshi say, the protocol for Bitcoin is set in stone?

# [CHAPTER 2](#toc.xhtml#c02)

# [Economic Model and Network Structure](#toc.xhtml#c02)

**"The first lesson of economics is scarcity: There is never enough of anything to satisfy all those who want it. The first lesson of politics is to disregard the first lesson of economics."**

*― Thomas Sowell*

Now that we have a good idea of what is a blockchain, what is Bitcoin, and a bit of an idea about Bitcoin blockchain, in this chapter we will look at the overall economic view of this system? Bitcoin as a peer to peer network is a network of miner peers who act in competition for economic incentives and why was the need for money being built in the system. We will also look at the network structure of Bitcoin, where it is the first large scale implementation of a small world network and what that means. How do user nodes come into the picture of this network and overall interactions of various entities in the network and its various attack vectors.

# [Structure](#toc.xhtml#s15a)

*   Bitcoin as money or cryptocurrency
*   The economic model of Bitcoin
*   The network structure of Bitcoin
*   Bitcoin as decentralization and distributed network

# [Objective](#toc.xhtml#s16a)

After studying this chapter, you should be able to understand why the Bitcoin blockchain is an economic system more than a technological breakthrough. You will learn what it means when Bitcoin is considered a currency, money, or a network of densely connected nodes. You will also learn about the deflationary nature of Bitcoin as money.

# [Supply of coins](#toc.xhtml#s17a)

The maximum number of Bitcoins that can ever be created is 21 million. Currently, about 18,000,000 Bitcoins are already mined and are in circulation. As per the mining schedule, by the year 2140, all of the possible Bitcoins will be mined and from then miners will purely have to depend on transaction fees for their rewards.

To be able to fully understand Bitcoin, its limited supply, and the economics behind it, we will need to have a look at the past and try to see what money is.

# [Value of money](#toc.xhtml#s18a)

Money is solidified trust. What this means is that with something that is money, you do not need to prove explicitly that, the thing which holds that value, can be trusted to deliver the promised value. The reason anyone trusts that a USD 10 note holds the mentioned value is because a central bank promises that value to be the case. So a USD 10 note, can be trusted by anyone and everyone irrespective of who holds that note, to deliver the value of USD 10 at any point in time.

Money is something that people trust is possible to use as a means of exchange between people who do not trust each other but agree that it has the value that it carries. At some point in time, the pound sterling was one pound of sterling (silver). This ensured that the value it promises was present in reserve storage at someplace. Some countries had their currencies pegged with gold but the idea was to not carry a large bag of gold or silver around and in place of that you carry something that is a guarantee that you can replace it by a certain amount of gold or silver. This ensured or solidified the trust in money by anyone who participates in a money's exchange of hands.

Of course, that peg has been devalued over the period of time and most countries now do not have the peg existing due to the introduction of fractional reserve systems (when the USA closed this, they had 5% of gold reserves pegged for all currency that existed). But if we say in short, money is a unit of account which represents the fractional percentage of the total issued unit of account from that one common ledger (usually a central bank would have that maintained it).

In the current times, every country has its currency and it is something that has been authorized and protected for its value by the legal system of that country, hence its name or reference as a legal tender. It means that the authority who is withholding the law, typically a government promises the value of the money by an oath and a legal system to enforce that value. So when I have a USD 100 note, I know that the government has certified the inherent value in the measurement of a unit of USD is 100 units and it will be the same value across the world for this note. Each note has an identity and even if no one in the world is willing to accept my note, I hold the right given by law that the government has to accept that note from me as the rightful unit of account.

If I have to summarize, the currency is issued by a government or a similar system to materialize as the unit of account of money.

Another form of money is a commodity earning its value for its utility. There are many commodities that have gained a certain amount of value over time like gold, silver, and even oil. All of these commodities derive their value because they have certain utility. In case of gold, it is used for its properties of being the most malleable metal on the planet and is used for various things like printing money as coins (been done for 10s of 1000s of years and earliest known usage), jewelry, electronics industry for fabrication of corrosion-free electrical connectors in computers, medicine, and even food in some places. Gold derives its utility from its properties of being corrosion free, malleable, the 1000s of years it takes for the natural process to create it or the amount of money to be invested in extracting it, but not just because it takes so many efforts and money to extract it, the value is only coming for the utility of what can be done using gold.

The value of money that is brought about due to a lot of people agreeing to it without any utility is speculation. The speculation as it stands, will stay till a large group is backing that speculation and as soon as they move on to new speculation, the value goes to what it's worth at the end, non-existent. One example of that is multi-level marketing or a pyramid scheme. The way it works is that you have initial adopters of an item (for example a company's stock) who speculate the value, and they bring in the next set of people who then bring in the next. It goes on till you are able to bring in the next group of people and collapses when that is not the case. Till then the initial group of people would have exited from their positions leaving behind a whole lot of people with worthless items.

One other example of this is the devaluation of a nation's currency. The much-fabled Zimbabwe's national currency lost its value so much that they had to print trillion dollars bills and that would be equivalent to a single USD because they just kept printing more and more money making it a speculative asset rather than creating a utility based on goods and trade which is how a country's currency needs to be measured against. The same thing happened with Venezuela recently, hyperinflation is nothing but loss of utility.

So even with fiat, the value is not derived completely out of thin air and if that happens eventually the value in it will evaporate leaving banknotes worthless as happened in Zimbabwe and Venezuela. Countries have to produce goods and services so that their value can be ascribed to the fiat currency for the country based on its overall GDP.

# [So is Bitcoin money?](#toc.xhtml#s19a)

Yes, money is a use case that can be achieved using Bitcoin as it is a value exchange unit. In place of it being governed by a government or a central bank, it is governed by a competitive POW process which does not work by trusting it, but by competition. Miners create new Bitcoin every block they add, referred to as a coinbase transaction. Anyone miner can be trusted as the only way to cheat the system is by consensus of all miners involved in the system, making it trustless. It is referred to as Peer to Peer electronic cash system and that is exactly what it is. The P2P system allows the transfer of money from any place on earth to any other place on earth instantly and with a very low fee, making it one of the most efficient, and secured forms of money.

The inherent value for Bitcoin is governed by its utility. There is always a speculative element as well but that is not sustainable and eventually its value will be governed by its utility. Suppose a world where Bitcoin blockchain's public ledger is used for all e-commerce trade transactions, that comes to billions of transactions per day and if all that volume goes through, that will mean that a whole lot of trade is dependent on the Bitcoin blockchain working and people needing Bitcoin to be able to trade using that blockchain. That value when it comes will give inherent value to the Bitcoin system.

Bitcoin by itself does not have any value as it was something that was created as per a coded protocol. That is the reason back in 2009 when the first coins were put into circulation by the process of mining, it did not have any value. There is a famous incident of someone buying two pizzas for 10,000 Bitcoins. That was the first time a value was assigned due to its utility of being able to buy a Pizza. Over the last decade, there was business and utilities created which assigned dollar value to Bitcoin. This is where a lot of usage of Bitcoin as anonymous currency also came into being with the notion that it was money that is beyond the control of governments and the users who use this do not need to follow the law of the land of the goods that they use it to buy. It turned out to be the opposite of what it was perceived as initially which is the reason there were changes introduced to the Bitcoin protocol like segwit and lightning network so that there comes a possibility of being able to lose records of transactions.

It is argued a lot that due to the miners putting investment by running nodes brings value to Bitcoin in proportion to the cost incurred by miners to run the network. This is not the case. The value only comes from it being used for trade and commerce not because there is a set of people investing in hardware to run it. It is the opposite. The value brought in by utility brings the set of people to invest in businesses that are mining nodes so that they can earn a profit by running the network.

Bitcoin is similar to a commodity where its public ledger entries are made for a small cost (of transaction fees) and that public ledger provides a whole lot of utility to run commerce and trade accounting. It also provides an excellent data storage capacity which is another property that is considered valuable for people to use. These utilities provide value to Bitcoin and in turn, can be used as money.

# [Is Bitcoin a Currency (crypto)?](#toc.xhtml#s20a)

Bitcoin is certainly not a currency and it has been also established by Supreme Court judgments in India and other countries. So the term used to refer Bitcoin and others as cryptocurrency is a misnomer will be corrected in due time. The court's ruling was these assets fall under the category of commodities.

A new term called virtual currency has emerged as well which is defined by European Banking Authority as *a digital representation of value that is neither issued by a central bank or a public authority, nor necessarily attached to a fiat currency, but is accepted by natural or legal persons as a means of payment and can be transferred, stored or traded electronically.* By contrast, a digital currency that is issued by a central bank is defined as a central bank digital currency.

So what about cryptocurrency and the exchanges that offer trading on them? Well, that goes back to the usage of these digital assets back in 2013-14 where many *cryptocurrency exchanges* came into being which offered non-KYC based users to be created and they being able to exchange money on these platforms. Currently, most of these non-KYC based exchanges are either shut down or will be shut down once the money laundering laws catch up to them. The creation of value also happened with 1000s of Bitcoin clones, forks, and alternatives that currently exist claiming there is a different blockchain needed for every other use case that seems to have not delivered anything yet that is of value. This created value resembles more of MLMs or pyramid schemes like chit funds and will eventually be shut down when they grow to a sizable number.

When it comes to Bitcoin the same rule applies. Currently, there is an average transaction volume of 1 million per day in BSV blockchain and with the reduction of subsidy of coins every four years in the next 10 years, either there will be 100s of millions of transactions or none or Bitcoin will shut down as well.

Currently, most of the transactions in BSV blockchain are coming from various utility applications and the way this ecosystem is growing the author expects a once in a lifetime transformation of many industries using internet-based applications to move their businesses to use blockchain resulting in actual utility and value.

# [The economic model of Bitcoin](#toc.xhtml#s21a)

**It is not from the benevolence of the butcher, the brewer, or the baker that we expect our dinner, but from their regard to their own self-interest. We address ourselves not to their humanity but to their self-love, and never talk to them of our own necessities, but of their advantages**

*\- Adam Smith*

Bitcoin is a tool that supports free trade. It supports effective and optimized trading instruments combined with the immutable ledger, it provides the perfect system for trading and storing the needed legal documentation as per the law of the land needs (sometimes up till 20 years is a legal requirement based on local jurisdiction needs). Let's take a step back and look at the overall economic model of Bitcoin with respect to the various entities that are involved in the network as participants.

Bitcoin has been created as a libertarian form of money, which supports free trade as its primary method of engagement for any participants big or small by leveling their paying or engagement field. It is possible in this system for an individual to challenge a billionaire by providing the same service as a large corporation and stand a chance purely on the merit of services provided for the masses. This is facilitated by the open-source and open public ledger of the Bitcoin economy. We have seen the rise of large corporations with their walled gardens like Apple, Facebook, Google, and Amazon or even Salesforce which makes it not possible for a small size company trying to compete due to sheer limitations on the capability to acquire similar resources in comparison to these large corporations. Bitcoin changes this by providing a large chunk of resources in terms of infrastructure to build an application balancing the competitive advantage and resources that larger corporations acquire due to their past success. It does not mean that the value of past success is any less, but if they have to succeed in the future, they will be needed to work the same amount as the new players who are trying to compete today.

Bitcoin incentive models are heavily influenced by the game theory principles which in the developer community is usually referred to as Bitcoin is a red queen's race. This is a reference to the famous works of Lewis Carroll's Through the Looking-Glass wherein one specific instance, Alice is with Red Queen and they are trying to get over the hill.

*Well, in our country,' said Alice, still panting a little, ‘you'd generally get to somewhere else—if you ran very fast for a long time, as we've been doing.*

*A slow sort of country!' said the Queen. ‘Now, here, you see, it takes all the running you can do, to keep in the same place. If you want to get somewhere else, you must run at least twice as fast as that!'*

This is what is the underlying idea of proof of work, which is what you constantly have to do to be able to stay competitive and if you want to get ahead you will have to work harder than the competitor to get ahead of them. We will discuss this in detail when we talk about mining in Bitcoin.

Let's start with a few concepts one by one to understand how the economics of the system impact the rewards and also the behavior of the participants in turn.

# [Inflation of the economy](#toc.xhtml#s22a)

We all have one way or the other faced the fact that the value of money or what we can buy with the money in year 0 is different than what we can buy with the same amount of money in the year 10. Typically it will be the case that what you get in year 10 will be less than what you were able to get in the year 0. This is one highly oversimplified way to describe inflation. All of the current economic frameworks across the globe governments are using one way or the other to face this issue. It can be considered as a slow devaluation of the currency that usually creates a loss of capital for an individual. I will take an example of what I have seen in my experience in the IT industry for the last 2 decades (I am using the numbers as approximation averages and they are not in any way represent real data).

When a fresh out of college graduate engineer, who completed engineering from an average institute spending about a total of Rs. 10000 over the course of his education in fees, joined a company with an annual CTC starting package of Rs. 200000 per annum or 15,000 per month after tax and other deductions. This was the case around 20 years ago for the IT Industry. The average living expenses in a fairly large city was about 7000 Rs. per month allowing the same person to be able to save 8000 per month. I was looking at the same data for current times, the fees now have increased to be about 100000, the living expense will now be coming to around 15,000 and the initial salary on a similar level will be around 250000 Rs. This has eroded any opportunity of the same skilled fresh graduate for any possible savings.

This is inflation in the economy which is typically seen as hidden tax and if we oversimplify, why it happens, is because there is more of the same currency available today than what it was available 20 years ago. Printing of money is in most countries a direct monopoly of the governments and the inflation rate decides how much more of the money the government will be printing which in turn will devalue the existing overall value of what currency supply that exists today.

Below image shows India's inflation rate in the past 10 years to give a picture of how inflation varies year on year for a country:

![](images/Fig-2.1.jpg)

**Figure 2.1:** India inflation rate in the last 10 years. Copyright - tradingeconomics.com

Suppose if the inflation rate is set by the government at 3% for a year, and suppose the total money supply in the economy is 1000 Rs (it's usually in lakh crore of rupees but assuming this for simplicity), at the end of the year the total money supply will be 1030 Rs. The government or RBI in case if India will have printed Rs. 30 more in that year increasing the total money supply by that number but no additional productivity was added. This money was printed out of thin air (mostly as now government fiat currencies are mostly decoupled with gold reserves) making the reward for the productivity of the same effort lesser by 3% that year. This is what I meant when I say Inflation is like a hidden tax which erodes the value of the money that is earned typically by hard work by approximately 3% apart from the other direct/indirect taxes that the government charges to a productive member of society.

Bitcoin, if used as money is created with such economic architecture that the above problem of inflation is not possible by design.

Let us look at how new coins are minted in Bitcoin and understand the statement mentioned above. The total supply of Bitcoin is fixed to 21,000,000 Bitcoins. This is what I meant that Bitcoin is taking care of the issue of inflation by design. Now that the total supply is fixed and also the release of new coins is done via the block reward or the coinbase transactions.

This block reward or what is commonly known as block subsidy keeps decreasing with time and the whole system is governed by decreasing order of subsidy and increasing the reward system of work (transaction fees by increasing the volume of transactions).

![](images/Fig-2.2.jpg)

**Figure 2.2:** Halving of Bitcoin block rewards every 4 years. Currently, about 18 million Bitcoins have been mined

If we consider percentage-wise, the first 50% of all supply of coins are mined in first block halving, then the next 25% of all coins supply is mined in the next or second block halving, the 3rd block halving will mine 12.5% of all the supply of coins and upcoming 3rd halving will start the new phase where 6.25% of all of the coins will be mined. This will keep reducing every 4 years and the last coin will be mined in the year 2140. By the time of next halving in 2020, 87.75% of all coins will be mined and only 12.25% of all coins remain to be mined. This reduced dependency of the miners every 4 years in the future is an incentive model that requires miners to find out other means for earning as the block subsidy will not be sufficient to keep their business profitable beyond a point. Miners will have two revenue streams:

*   Price in terms of fiat for a single Bitcoin, so even though the number of coins decreases in the future, the price of a single Bitcoin balances it a little as well.
*   A number of transactions that pay a fee to miners. The volume of transactions is governed by the block size of a block and as trade transactions grow, the network is capable of supporting millions of transactions per block and the goal is to keep refining infrastructure to support potentially billions of transactions and in turn, increase their fee revenue. The planned Teranode upgrade is the same protocol implementation but with highly parallelized microservice-based architecture to enable billions of TPS. This will enable the right incentives and new business infrastructure for miners and businesses alike.

This model of new coin generation is at the core of the design that addresses the inflation issue that we have discussed in detail earlier. This mechanism of using miners' investment in work rather than the government's model of generating new money based on their inflation targets creates accountability in the system to generate new money and on the other side, limits the total money that can ever be created. This is to be seen as a way to implement a monetary system that is independent of the possible corruption of rules by a government and on the other side, the scarcity of the total money in the system increases the value of existing coins. This property by the design of Bitcoin makes it a deflationary form of money. I wanted to add since Bitcoin is not a legal tender it cannot be something which can in immediate future become currency for a country, but it can be seen as a system which currently can be seen as a secure, stable and reliable system on which a government can create a tokenized form of their currency's electronic or digital version. This will be much more efficient to transact, traceable, auditable, electronic cash platforms in comparison to current paper printing methods which are prone to malicious fake currency creation and consume a large cost to ensure that it is not misused. Even developing countries like India are now moving more and more into digital transactions to move away from the informal cash economy and also move away from traditional systems.

In this context, Bitcoin should be seen as oil which is more of a commodity than the currency which powers an efficient underlying financial system.

# [Economics of participation](#toc.xhtml#s23a)

Any individual or business that engages in new technology or system needs an incentive to do so and most of the cases it is an economic incentive. There are various participants in the Bitcoin network which are defined with the unique economic incentives that get offered to them to contribute to the network or use the network. Let us look at various participants of the Bitcoin blockchain network and see how are they are incentivized in terms of the economic activity they perform.

# [Individual](#toc.xhtml#s24a)

Bitcoin network incentivizes an individual to participate in it by providing a better payment and utility mechanism for electronic cash transfers, cost-effective data storage system, and providing the reach of an individual to advertising in a direct way in place of via a middleman like the current world applications (e.g., Facebook, Twitter, etc.). Bitcoin in a way also acts as a potential investment since the past performance of price has shown. The value of a coin will be directly dependent on the utility of the system and more participation, more utility will be built, and more the valuation of coins.

Individuals can benefit or be incentivized for a larger use case of providing data to the network. The current model of free social media applications is advertising based where the users of the applications serve as potential consumers of advertising and that is done using their personal data to identify, categorize, and target via focus grouping the set of users with relevant advertising. A lot of activity that happens in current social media is using this model with sponsoring trends, creating viral marketing campaigns, and click-based revenue models. The limitations or the downside of these models are that the actual consumers of advertising, the users who do get a small share at times (like YouTube advertising) but a larger chunk is taken by the platform who is providing these services for free. With the enablement of microtransactions, Bitcoin blockchain enables a different model for these applications where there is a direct connection between the advertiser and the user creating a much stronger incentive for user participation.

There are a few more use cases which can be called advanced use cases which will take some time to get realized like, auto tax payment for user transactions, using blockchain's open audit capability for faster conflict resolution of disputes, and truly peer to peer money transfer to two individuals across the world at minuscule fee considering the cross border remittance which typically right now is quite expensive to do due to many intermediary service providers charging their fee component.

One big incentive which is probably a hidden incentive to start with is data security and privacy of an individual stand a chance for the first time to be fully possible with blockchain-based systems allowing an individual to stand to gain a lot more than loose in adopting Bitcoin-based applications.

# [Businesses](#toc.xhtml#s25a)

One of the main themes currently with large to small businesses is to optimize the cost of operations. There are few themes of current times that are being fiercely pursued by a business, small or large alike as mentioned below:

*   Faster time to market
*   Reduce the cost of operations and IT operation costs
*   Competitive pricing of products
*   Constantly upgrading user engagement and user experience
*   Ensuring IT security at low cost
*   No disaster recovery IT setup and cost

All of the above themes can see a radical transformation if the global financial network is using Bitcoin blockchain for their system of records and transaction layer. This might sound a bit of a stretch to someone but this is what is possible with a protocol layer system like metanet built over Bitcoin blockchain which can enable the use of Bitcoin blockchain as the serverless layer for building client-side applications. We will be discussing the metanet protocol and these use cases with examples in extensive details in chapters later in the book.

Metanet is a protocol to use the Bitcoin blockchain as a platform (database, executables, code repository) which enables an individual to start a lean business that stands to compete with larger businesses just by the virtue of the superiority of the product frontend. If I have to make an app right now, I need to host my application in a serverless setup including buying processing and storage in the cloud (unless I want to set up a data center). As the ecosystem matures, it will be possible to build products as serverless applications using the Bitcoin blockchain for backend providing similar usability as it exists with cloud-based solutions.

# [Miners, the non-trusted third parties](#toc.xhtml#s26a)

The proof of the work model of Bitcoin has created an entirely new industry of businesses called miners. What Bitcoin blockchain does to the technology innovation aspect of things, miners are doing that to the computer hardware, and processing units side of things, disrupting the overall computer hardware industry. Most of the large corporations like Intel, AMD, Samsung, and many others are currently actively working on creating the best possible ASICs for hash mining along with many new companies that have been born in the last decade.

Miners work as the most important and the most actively incentivized participants for the Bitcoin blockchain system. They are also the ones who are working on each second basis to generate new blocks in competition with each other and if I have to summarize, execute the following functions to gain the defined incentives for them (block rewards and transaction fees):

*   Access mempool (first place of transactions to be placed) in the network to collect transactions and validate their integrity and sanity.
*   Participate in network consensus to add a new block.
*   Host blockchain nodes for anyone to access the blockchain data.

Miners get incentivized by the functions that are mentioned above to have the possibility of better earnings based on how much hash power they have and how best and optimized they can execute the functions that they are responsible for.

Miners have a secondary incentive model to sell services that can be built on blockchain's data like data analytics services, data pruning services, and most importantly data provider services for new generation applications like running automation or AI/ML type system on the blockchain.

If I have to summarize, Bitcoin's economic model is an implementation that incentivizes usage, and the value of incentives increases as the usage increases. It is a kind of self-reinforcing system where more and more usage and cooperation increases the value of network and profitability for all of the participants involved. In some ways Bitcoin blockchain rewards greed and if it is honest greed, it is even further rewarded, but if you are dishonest in the greed you might end up losing on the possible incentives or profits.

# [The protocol set in stone](#toc.xhtml#s27a)

Since the release of the Bitcoin first version back in 2009, there has been a lot of discussions, changes, and divergence of the original incentive model of Bitcoin implementation which in turn created a network split in form of various chains (predominantly BTC, BCH, and then the BSV which restores the original protocol as defined in the whitepaper). This is due to the fact that early adopters for Bitcoin were development communities and Satoshi himself disappeared leaving no central authority in terms of guidance or approval of changes like it happens for the open-source Linux community even today. With the BSV chain of Bitcoin implementation after the Genesis upgrade, the complete protocol defined in the original whitepaper is almost in entirety restored removing many things like an artificial limit on the blocksize, disabled opcodes, non-standard transactions and more, taking back Bitcoin blockchain to be a fully functional, on-chain scalable and a protocol layer implementation. This is the version that is going to be set in stone as defined by Satoshi in his earlier communication with the developer community back in the year 2010 when he was participating in various technical and protocol level discussions with the members of the forum, bitcointalk.org. Link - **[https://bitcointalk.org/index.php?topic=195.msg1611#msg1611](https://bitcointalk.org/index.php?topic=195.msg1611#msg1611)**

The whole discussion can be read via the mentioned link but the crux of the matter is shown in *[Figure 2.3](#c02.xhtml#fig2_3)*. This also signifies the importance that there is no need for any second or alternate implementation for the Bitcoin protocol:

![](images/Fig-2.3.jpg)

**Figure 2.3:** Bitcoin protocol is set in stone from version 0.1 which provides for all possible use cases without needing any alternate implementation or changes to the protocol

# [The network structure of Bitcoin](#toc.xhtml#s28a)

To become part of the Bitcoin network, anyone can download a node implementation software and set up a node. I said to anyone as it is possible for anyone to participate, but typically this is a function that is done by the miners. Miners are businesses that invest to run a node for the possible incentives that are defined above. Effectively what the network becomes is - a whole bunch of mining nodes, some non-mining nodes (for e.g. a block explorer service provider like whatsonchain will need to run a node). They form the central structure in the Bitcoin network as they are incentivized to be connected in such a way that the message propagation time from a node to all other nodes in the network is as minimum as possible. This is significant when the process of network consensus happens during the mining process. This creates a network centrality for all of these mining nodes which are incentivized for hyperconnectivity between them.

# [Bitcoin as a small-world network](#toc.xhtml#s29a)

In terms of graph theory, Bitcoin is a small world network which is densely connected at the center (mining nodes being those central hyperconnected points). Bitcoin can be argued as one of the first biologically inspired networks which I will explain a lot more, but let's go back and see the Bitcoin network structure first.

Bitcoin is an overlay network that sits on the top of any network, be it public networks like the internet or private network of telecom operators like SMS and for that matter, any private satellite-based networks as well. In effect, we can say that the underlying network is anything you can think of and the Bitcoin network on top of it.

In-network graph theory, a graph is a set of points (called **nodes**) that are connected with each other through lines (called **edges**). There are many simple and complex graphs that exist and to give an example, one of the simplest forms of the graph is a linked list. A complex graph is the entire World Wide Web, where items are documents and references (links) are connections. A network consists of sites that send and receive messages of various types.

Let's look at the typical communication network topology to understand the difference with Bitcoin network topology:

![](images/Fig-2.4.jpg)

**Figure 2.4:** Network topologies.

For more details on Network topologies. Ref: *Baran, Paul*. On Distributed Communication Networks: I. Introduction to Distributed Communications Networks. *Santa Monica*, CA

**[https://www.rand.org/pubs/research\_memoranda/RM3420/RM3420-chapter1.html](https://www.rand.org/pubs/research_memoranda/RM3420/RM3420-chapter1.html)**

Unlike the above-shown topology, the Bitcoin network is none of the above. Bitcoin network structure is a small-world network. It comes to something called Mandala network:

![](images/Fig-2.5.jpg)

**Figure 2.5:** Mandala Networks: Ultra-small-world and highly sparse graphs.

For more details refer to *Sampaio, Cesar & Moreira, Andre & Andrade, Roberto & Herrmann, Hans & Jr, José*. (2014). Mandala Networks: Ultra-small-world and highly sparse graphs. Scientific reports. 5\. 10.1038/srep09082.

In a mandala network, the central nodes are highly connected to each other as shown above. It is a near-complete graph in practice, which means that the nodes are connected with all other nodes that are present either directly or via another node. The central space in the network is shown as the miner nodes denoted as **M** in *[Figure 2.6](#c02.xhtml#fig2_6).* These mining nodes are incentivized to be hyper-connected with all of the other mining nodes so that they get the transaction propagated or to communicate with other miners with extremely fast connectivity. User nodes are not as incentivized to be connected to all miners and hence are connected to a few of the mining nodes.

Both mining nodes and user nodes are shown below in a network which is densely connected at the center but sparsely connected at far outside as shown in the below figure:

![](images/Fig-2.6.jpg)

**Figure 2.6:** Bitcoin network structure in which miners are densely interconnected in a super-peer network. Users nodes connect to some of the miners in their peer network

Let's go back and look at the definitions in the whitepaper about what are the functions and specifications of a network to understand it better:

![](images/Fig-2.7.jpg)

**Figure 2.7:** Network functions as defined in the specifications from Bitcoin whitepaper

Now as shown in *[Figure 2.6](#c02.xhtml#fig2_6)* if a user creates the transaction, it will broadcast it to the miner nodes it is connected with and then the miner node will propagate the transaction to all of the other miner nodes it is connected with making a total network distance for propagating the transaction to a maximum of 3 hops (typically it will be wallet sending to the connected mining node which is 2 hops and in some cases if one of the miners does not receive it, it will receive it when another miner propagates making it a maximum of 3 hops). This makes the Bitcoin network like a small world network where the network distance between any two entities is always less than 3 hops.

In a complete graph system like Bitcoin network, all nodes (miners) will not just be interconnected but also will be a system which is sufficiently powerful (much more than a typical home pc) to be able to perform the function steps 1 - 6 mentioned in *[Figure 2.7](#c02.xhtml#fig2_7)* as it requires a time-critical and large amount on communication as well (to many other systems) apart from the mining function making the user nodes almost no usable for doing transaction validation and typically they are something called SPV nodes (will be discussed in detail in a later chapter). From now on we will refer to nodes as mining nodes in the book.

Nodes also keep a log of the IP addresses that they have previously connected to and also they exchange node lists which makes them not act as a pre random graph, but effectively collects and remember other nodes making this network closer to a complete graph rendering higher efficiency and security.

A typical discussion that happens around the security of the network is a Sybil attack. Sybil Attack is a type of attack that is done to a peer-to-peer network where a node in the network simulates multiple identities at the same time by destroying the integrity of a reputation system and gaining the majority of influence in the network. This is mostly done to carry out illegal (or breaching the rules set in the network) actions in the system. To outside observers of the network, these multiple fake identities simulated in a Sybil attack appear to come off as real identities.

When it comes to the Bitcoin network, the Sybil attack is not feasible due to the network structure. Simulating a non-mining user node will have no impact on the network as they are not actively participating in any of the validation processes for transactions as we discussed. If you look at the process a miner node has to follow in Bitcoin as described below, it makes sure that Sybil is pretty much not possible:

*   Once a mining node discovers a block, it propagates it to the network.
*   Due to dense connectivity, all of the mining nodes receive this block instantaneously.
*   The miner node with a valid node setup attempting to Sybil (selfish miner) receives and validates the block found by the other node.
*   The selfish miner then sends an alternative block to all nodes after the earlier block sent by a different node.
*   This selfish miner sending block has a delay and not instantaneous as the earlier honest miner making the first miner get a higher probability to be accepted in the network.
*   The selfish miner is acting following a time delay and is not instantaneous. This makes the selfish mining node always loose during the network propagation process for blocks.

Due to the fact that the network distance in Bitcoin being less than 3 makes it Sybil resistant which typically is possible when there are networks where distance is larger than 3.

# [Decentralized and distributed network](#toc.xhtml#s30a)

Bitcoin's public ledger is hosted by each of the mining nodes, basically making them keep one complete copy of everything present in the blockchain. This means that at any point in time, for any possible reason, if one node goes down, that has close to no impact to the overall network. This is unthinkable in terms of current businesses where they have limited disaster recovery systems (most times 2) where the breakdown of one of the systems will pose a significant cost to the business and risk to their normal operations. This is one of the game-changing aspects of Bitcoin blockchain that due to its non-centrality, it is impossible to destroy the network. This is what is meant by the Bitcoin blockchain is a distributed network.

It also has one aspect which is decentralization. This aspect has been debated a lot and many times used as an argument to discuss whether that kind of makes the blockchains independent of government and legal system or they are democratizing finance. I, however, am of the view that particular argument does not hold much water as if the government wants they can anytime make Bitcoin illegal and shut down all of the nodes spread across the world (of course they will have to collaborate with the various governments of the world to do so, uncommon but has happened in the past when liberty reserve decentralized network with about 30,000 on-ramp fiat nodes was taken down globally by 42 governments coming together).

Bitcoin in its origin, in its structure, in its economic incentive mechanism is capitalistic. Not the kind of capitalism where one elite group of companies who have initially won the competition and become rich can stifle any competitors and monopolize the domain, but the capitalist system which gives equal opportunity to unequal participants. It is a protocol which is once set in stone with its original version, is frozen and no one, and I mean no one can then change it to lean it to favor any other entities anytime in the future. The developers cannot make any changes to it, the governments cannot make any changes to it, and in becoming a central, frozen, freely available system of public commodity Bitcoin becomes decentralized, where it is available for all with equal opportunity by being locked and stable in its design. Any authority or any leverage will come to people who will build on the top of the protocol with creating applications and software which are addressing real free market trade use cases, real applications that are used by everyone.

The real decentralization aspect which is never discussed about Bitcoin is what it truly does. Bitcoin decentralized power from money. Bitcoin with its locked protocol takes away the power out of money, this is what Bitcoin is really about. Right now, across the world money circulation and money creation is inherently owned by a centralized system, which mostly is either controlled or directed by politicians or bureaucrats, or an institution which is a mix of both. With Bitcoin, it takes away the trusted third party out of the process of the creation of new money. Not just that, it also provides a transparent real-time audit system that takes away the possibility of information being either manipulated or hidden. It makes everyone using it accountable for what they use it for and decentralizes power.

Another aspect of decentralization is the number of nodes that are running in the mining node network. The mining difficulty of Bitcoin is recalibrated every 2016 blocks (approximately 2 weeks). This provides the upper limits to the number of mining nodes that can exist to 2016 (assuming every miner mines one block in a cycle). More nodes than that are not needed in the network as that will be just redundant and waste of energy/investments. It is currently said that there are 10,000 nodes in Bitcoin, the fallacy in that argument is that if a node is not producing and distributing blocks they just watch and do nothing making them of no value altogether. This is why the nodes are expected to land in data centers with very sophisticated hardware and software for mining so that they stay relevant and are able to mine blocks.

We have up till now discussed various introductory concepts and overall nature of Bitcoin protocol, the network structure, the blockchain, and the overall inventive model of the economics of Bitcoin and its participating entities. We will now start to go into details of the various new concepts that have been utilized in Bitcoin to replace the traditional account number or address model which has been typically used to denote an account held by an individual. We will be going into the details of how ECDSA is used in Bitcoin to create a highly secure network and user keys.

# [Conclusion](#toc.xhtml#s31a)

We have seen various aspects of the economic structure of Bitcoin along with its network and its incentive model for various types of participants. This chapter was more focused on the principles and the overall philosophy of Bitcoin which is deep-rooted in all of the concepts that are used in Bitcoin. It changes the way we see value in money in traditional forms of currency that are prone to inflation by bad policies. It offers for the first time in the history of commerce deflationary money where the value of it is tied to economic utility and commerce. We also see what a commodity like Bitcoin with its advanced but yet simple economic incentive structure and thousandths of a cent fee can do to the economics of a country, company, and an individual. In the next chapter, we will be going deeper into the cryptographic aspects of Bitcoin blockchain along with some of the mathematical concepts that are used in Bitcoin.

# [Questions](#toc.xhtml#s32a)

1.  Is Bitcoin Money or a cryptocurrency?
2.  What are the incentive models for individuals and businesses in Bitcoin
3.  What is a distributed system, is Bitcoin distributed system and why is it so?
4.  What is decentralization in Bitcoin blockchain?
5.  Why is a protocol set in stone, which no one can change beneficial for utility and development?

# [CHAPTER 3](#toc.xhtml#c03)

# [Cryptography, ECDSA, and Bitcoin Addresses](#toc.xhtml#c03)

**"Fully secure systems don't exist today and they won't exist in the future"**

*\- Adi Shamir, Israeli cryptographer.*

Cryptography and complex mathematics is something that is quite a daunting task for anyone to read and understand. This poses one of the biggest reasons why Bitcoin is so much misunderstood by early adopters and the overall current blockchain ecosystem as the learning curve is quite high to start understanding these things. I have tried to keep things at a simpler level but still capture the essence of the overall usage of the cryptography and keys in Bitcoin. These concepts will build a solid foundation for you to understand various intricacies of a blockchain so it will be a good idea to put some effort to understand it to make sure you can grasp the intelligent usage of these cryptographic tools in Bitcoin.

# [Structure](#toc.xhtml#s33a)

*   Cryptography basics
*   Diffie Hellman and RSA key exchange
*   Elliptic Curve Cryptography (ECC)
*   ECDSA in Bitcoin
*   Bitcoin addresses generation via public and private key

# [Objective](#toc.xhtml#s34a)

After studying this chapter, you should be able to understand the ECC, ECDSA, public and private keys conceptually, and implementation details in Bitcoin blockchain. You will also get an overview of what is cryptography and the math behind it.

# [Cryptography](#toc.xhtml#s35a)

Cryptography (*crypto* means hidden or secret, and *graphy* means study) is a branch of computer science which is focusing on methods and techniques for creating secure communication between two entities. There is a huge history of cryptography with the earliest use seen in ancient history like ancient Egyptians using complex hieroglyphics to Roman emperor *Julius Caesar* using ciphers. It has been extensively used in wars specially and modern cryptography also has roots in WWI and WWII with things like enigma machines and the rest.

Cryptography is closely associated with encryption, which is the act of encoding ordinary text into what's known as ciphertext by the sender and then decoding the text back again by the recipient. In addition, cryptography also covers the obfuscation of information so that only then intended entities are able to access the information. There is a lot that can be written but broadly it is classified as symmetric and asymmetric cryptography.

The symmetric key typically will have both sender and receiver already sharing a common key (or have a computational relationship between their keys) which they use to encode and decode the message, while the asymmetric key is something which uses a pair of keys or introduces a concept of public and private key to encode and decode the messages. The asymmetric key is also known as public-key cryptography was proposed as a solution to the limitation to symmetric key in a 1976 paper by *Whitfield Diffie and Martin Hellman*. They proposed the notion of using a pair of keys, which are mathematically related to each other — a public key and a private key. Since then, most of the internet and secure communications use an asymmetric cryptography, and so does Bitcoin blockchain.

# [Secured key exchanges](#toc.xhtml#s36a)

The key exchange problem became one of the fundamental problems to be solved as a limitation of symmetric key cryptography which needed a common key to be shared between the two communicating entities. The result was the invention of public-key cryptography or asymmetric key cryptography which rather than using just one single key uses a key pair, a public key that can be disseminated openly and a private key that is kept secret with its owner.

Since then public key algorithms have become fundamental security ingredients in modern cryptosystems, applications, and protocols assuring the confidentiality, authenticity, and non-reputability of electronic communications and data storage.

Largely most of the internet standards **(Transport Layer Security (TLS)**, S/MIME, PGP, and GPG) now use public-key cryptography, and most commonly used are Diffie–Hellman key exchange protocol and RSA encryption. The complete set of standards was developed and called **PKI (public key infrastructure)** for secure communication and digital signatures done over insecure public infrastructure.

A standard PKI implementation required a central authority that needed to issue the certificate and maintain them. This, therefore, was not the best-suited implementation for a protocol like Bitcoin which was trying to create a system without using a centralized authority. But this was not the only system that could provide an asymmetric cryptography solution and another variant came to be as a solution for the use case needed in Bitcoin. Before we go further, I also wanted to touch upon a few concepts like Elliptic curve cryptography, public key exchange algorithm, and digital signing algorithm.

# [Diffie-Hellman key exchange algorithm](#toc.xhtml#s37a)

Diffie-Hellman key exchange algorithms become some of the first widely used key exchange algorithms. It however required the two parties communicating to know each other prior to communicating needed those to exchange a shared key that any one of them can use to encrypt or decrypt a message (considered synchronous).

The way Diffie-Hellman key exchange works is by using a common or base key which is known to both the participating entities, suppose, *G* and the two entities being *Alice (Private Key a and Public Key A)* and *Bob ((Private Key b and Public Key B),* both are able to share the secret message by encoding and decoding using below-mentioned fact:

*a B = a b G = b a G = b A where { A = a G and B = b G}*

We will discuss this further when we talk more about how this is used in Bitcoin.

# [RSA algorithm](#toc.xhtml#s38a)

*Ron Rivest, Adi Shamir, and Leonard Adleman* created a cryptographic algorithm, which implements both, a public-key cryptosystem, as well as digital signatures. It was one of the first implementations to solve asymmetric key cryptography and came to be widely used in applications. The public key (of the pair) can be given to anyway and decrypted with the other, which is kept private. *[Figure 3.1](#c03.xhtml#fig3_1)* depicts this type of exchange.

Diffie-Hellman is commonly used for TLS for protecting secure web pages and RSA is commonly used for digital signatures to verify a sender's identity. Public-key cryptography is primarily based on the idea that the key that you use to encrypt your data can be made public while the key that is used to decrypt your data can be kept private. A typical message transmission looks like as shown in the diagram below:

![](images/Fig-3.1.jpg)

**Figure 3.1:** Public-key cryptography

# [Cryptography basic concepts](#toc.xhtml#s39a)

I will be covering a quick snapshot of various aspects of cryptography in this section but I will say it is an optional section since it will involve a bit of mathematics and it is possible that you can skip this section directly to jump to the next section where we talk about Elliptic Curve Cryptography in Bitcoin.

Public key cryptography is based on using certain algorithms implementing mathematical functions that have a very unique property of being intractable, but before we go further, let's have a look at what are intractable problems and what is a trapdoor function.

# [Tractable and intractable problems](#toc.xhtml#s40a)

A problem is called tractable if there is an efficient (i.e. polynomial-time) algorithm that solves it. Conversely, a problem is called intractable if there is no efficient algorithm that solves it.

Some examples of tractable problems (ones with known polynomial-time algorithms):

*   Searching an unordered or an ordered list
*   Sorting a list
*   Multiplication of integers is easy

Some examples of intractable problems (ones with known polynomial-time algorithms):

*   List all permutations of n numbers
*   Decomposition of a composite number into a product of smaller integers

So to summarize, typically intractable problems may have a theoretical way to solve them but there is no practical way to solve them due to the fact that the most common method of brute-forcing would require exponentially large time in terms of the complexity.

# [Modulus arithmetic](#toc.xhtml#s41a)

Modulus arithmetic is one of the most fundamental components of cryptography and it is essential to understand what it is before we move to other components. So let's have a look at the statement below:

3 ≡5 mod (2) or in simple words, 3 is congruent to 5 mod 2

This means that in the world of mod 2, 3, and 5 are equivalent. This is due to the fact that it is in the world of mod 2. Mod 2 means that there are only two values, 0 and 1. Effectively in Mod 2, the acceptable values are {0, 1}. For a Mod (n), the value set will be {0, 1 …, (n-1)}

Now if we look back at our original statement, 3 ≡5 mod (2) on the number line, as you can see here 3 is the same as 5:

![](images/Fig-3.2.jpg)

**Figure 3.2:** number line showing mod 2 calculations

If we look at this, in terms of a finite field (we will talk more about it, but in short, a group which is possible to be defined by a finite set), an example will be, a finite field defined by a set of integers mod p. p here is a prime number. The set of integers mod *p* consists of all the integers from 0 to *p*\-1.

# [Trapdoor function](#toc.xhtml#s42a)

A trapdoor function is a function that combines the features of a tractable problem and intractable problem. This function is tractable in one direction and intractable in the opposite direction but with a special secret, it is possible to solve it quite easily.

If *f* is a trapdoor function, then *y* =(*x*) is easy to compute but *x* = *f*^(\-1) (*y*) is very hard to compute without the knowledge of *k*. Given *k*, then it is easy to compute *y* = *f*^(\-1) (*x*,).

The name trapdoor comes from the analogy that it is very easy to fall through the trapdoor but a ladder is needed to climb back out of it. RSA algorithms use factoring a large number as the trapdoor function.

Once the usage of RSA became prevalent, so did the length of the key size, due to the invention of many algorithms that were solving the problem of prime factorization, It made it easier for breaking the trapdoor function used in RSA and effectively the key sizes started becoming larger and larger to secure better. The future of cryptography could not depend on this trapdoor function for long and it became abundantly clear that a new better trapdoor function was needed. The solution was found in an obscure mathematical branch called elliptic curves.

# [Elliptic curves](#toc.xhtml#s43a)

The emergence of using elliptic curves in cryptography is not new and they have been seen used in TLS, SSH, and PGP cryptosystems due to some of their unique properties. An elliptic curve is a plane curve over a finite field which is also a group.

Real numbers, for example, are an infinite field but if you collect a set of numbers like { 3, 4, 543, 42, 56, 78, 2020 } it will be a group of finite numbers and hence, finite field/group. Another type of finite field will be all of the integers belonging to a modulo (*p*).

An elliptic curve is a set of points that forms a curve defined by an equation of the form.

*y²\=x³\+ ax+ b* where *4a³\+ 27b²≠0* to exclude singular curves, (x,y ∈ R2 ) and including a point 0 (zero) at infinity, an elliptic curve can be defined as a curve satisfying the equation below:

*{(x,y)* ∈*R2 |y²\=x³\+ ax+ b, 4a³\+ 27b²≠0} U{0}* and has the following properties

*   *x³\+ ax+ b* has distinct roots (All the solutions of the equation are not equal to each other). This ensures that the curve is non-singular.
*   Are a group, which means it has:  
    *   **Closure**: If a and b are in a group G, then a + b is in the group G
    *   **Associativity**: (a + b) + c = a + (b + c)
    *   **Identity element**: a + 0 = 0 + a = a
    *   **Inverse for each element**: a + b = 0
    *   Specifically, Abelian group, which means it has Commutativity: 
        
        a + b = b + a
        

With the usual notion of addition, the set of integer numbers *ℤ* is a group (moreover, it's an Abelian group). The set of natural numbers *ℕ* however is not a group, as the fourth property can't be satisfied. These unique properties of the group, including things like inverse, became important attributes that were very useful in creating trapdoor functions which we will see later on.

Let's have a look at how these curves look when a and b assume different values *([Figure 3.3](#c03.xhtml#fig3_3)):*

![](images/Fig-3.3.jpg)

**Figure 3.3:** A typical elliptic curve where b = 1 and a takes values from 2 to -3

The singularities are excluded as they are not considered as valid elliptic curves, which look like as shown in the picture below:

![](images/Fig-3.4.jpg)

**Figure 3.4:** A curve at the cusp y²\=x³ and self-intersection y²\=x³\- 3x+ 2, both not being an elliptic curve

Now that we have understood some of the properties of the elliptic curve, and how they are adhering to the properties of an Abelian group, let's have a look deeper to the group laws and how that applies to elliptic curves.

One of the most important properties of elliptic curves being an Abelian group is that if you draw a line which is intersecting two non-tangent points on the curve, it will always intersect the curve on a third point which follows the below-mentioned property:

*   Given three aligned, non-zero points P, Q and R, their sum is P+Q+R=0 and (P+Q) + R = P + (Q+R) = Q + (P + R)

Which means that P + Q = -R.

![](images/Fig-3.5.jpg)

**Figure 3.5:** Plotting elliptic curve with 3 points which are aligned showing property, P + Q = - R. Try your own with a tool created by Andrea [https://andrea.corbellini.name/ecc/interactive/reals-add.html](https://andrea.corbellini.name/ecc/interactive/reals-add.html)

We can define a group over elliptic curves. Specifically:

*   The elements of the group are the points of an elliptic curve;
*   The identity element is the point at infinity 0;
*   The inverse of a point P is the one symmetric about the X-axis;
*   The addition is given by the following rule: given three aligned, non-zero points P, Q and R, their sum is P+Q+R=0.

Please refer to Andrea’s Blog mentioned above for a detailed mathematical analysis of these properties of elliptic curves, but there are two main properties which are used in Bitcoin which we will focus on:

*   For 3 aligned pints, their sum is zero, P + Q + R = 0, which we have looked at above in *[Figure 3.5](#c03.xhtml#fig3_5).*
*   Scalar multiplication applies: nP = (P + P + ….. \+ P) (P is added n times).

# [Elliptic curves over finite fields](#toc.xhtml#s44a)

One additional aspect as briefly discussed earlier is, we need a finite version of this curve, for which we use modulus arithmetic. Due to that, instead of the curve going to infinity (point 0 as discussed earlier), the points are defined in a finite field. Apart from that, in terms of definitions, the Order of an elliptic curve is defined as the number of points that are present in the elliptic curve.

Let's restrict the elliptic curves to finite fields to understand the impact of using both together, we can write the elliptic curve equation we saw earlier for real numbers limited by the finite field of modulus *p (F[p]) {(x,y)* ∈*(Fp)²* *|y²\=x³\+ ax+ b* mod *p, 4a³\+ 27b²≠0 mod p} U{0} |* where 0 is still the point at ∞, and a and b are two integers in Fp.

Now let us look back at the 3 aligned points we spoke about, P + Q + R = 0, and what does this mean for these points to be aligned in F[p]? We can say that they are aligned if there's a line that connects all of them

The elliptic curve defined over F[p] has a finite number of points. The number of points in that group is known as the order of the group and typically denoted by n.

# [Cyclic subgroups and base point](#toc.xhtml#s45a)

Let us look at what is point addition, doubling, and scalar multiplication in elliptic curves.

**Point addition:** we have seen earlier, a line passing through two points on an elliptic curve will pass through a third point and the equation to calculate this third point was P + Q =-R

**Point doubling:** If P is tangent to the elliptic curve, then it means that P = Q. So the above equation becomes - P + P = -R or 2P = -R

The scalar multiplication property is based on the fact that computing nP (P is a point on the curve) requires n additions and typically an algorithm known as double and add is used for performing this computation. This is an interesting property of the elliptic curve which is described below:

If n = 7, in binary it will be 2²+2¹\+ 2⁰

So when we have to do 7P, it can be broken down to - 2² P+2¹ P+ 2⁰ P

Or R = (P + (P + (P + (P + (P + (P + P)))))), basically known as "double and add".

The set of multiples of P also has the property of being a cyclic subgroup of the group formed by the elliptic curve. This means that the values of nP repeat after a certain number of cycles of multiplication is done. The point P is called the generator or the base point for the cyclic subgroup. Now let's see what are cofactor and order of a subgroup.

Based on Lagrange's theorem, we define the cofactor of a Group with order N and subgroup order n as:

*h = N/n, h* will always be an integer because n is a divisor of N. Also, for every point in the elliptic curve, *NP = 0*

So, we can say, *n(hP) = 0*

Now suppose that *n* is a prime number, above equation, written in the form *G = hP* generates a subgroup of order n except when *G = hP = 0* (subgroup has order 1).

G here becomes a generator of a subgroup with order *n* and cofactor *h*.

With the above explanation in mind, we can now define what is called the domain parameters for the elliptic curve. These are:

*   Prime *p* which specifies the size of the finite field
*   *a and b* which are present in the elliptic curve equation
*   Base Point *G* which generates the subgroup
*   Subgroup order *n* and Cofactor *h* of the subgroup

Together these domain parameters are the sextuple *{p,a,b,G,n,h}* for an elliptic curve

# [Discrete logarithm problem](#toc.xhtml#s46a)

If we know P and Q in the elliptic curve, what can be a possible value of *k* which can satisfy the below equation:

*Q = kP*

This is the problem in elliptic curves which is believed to be an intractable problem where currently there is no known algorithm that can solve it in polynomial time. This acts as the trapdoor function which is very hard to break and comes as the ideal utility to use in creating public and private keys for key exchange cryptography.

# [Elliptic Curve Cryptography (ECC)](#toc.xhtml#s47a)

Finally, we are at a point where we can discuss how above-explained concepts are used in elliptic curve cryptography:

A private key is a random number *k* chosen from subgroup with an order of *n* from *{1,…,n-1}*

Public Key is a point, *P = kG,G* being the base point of the subgroup

So if we know *k* and *G*, along with other domain parameters, calculating *P* is quite easy, but if we only know *P* and *G*, it is quite difficult to find out *k* due to the discrete logarithm problem we discussed earlier.

This same concept is used in ECDH (elliptic curve Diffie Hellman) which is used in TLS which we will not be discussing and also in ECDSA which is used in Bitcoin for key generation and exchange.

If we recall the Diffie - Hellman key exchange described earlier, that is the same concept that works in place of prime factorization, it uses elliptic curves to create the common secret *G* as we have learned. In terms of digital signing algorithms, we have a process of signing and verifying messages and let us have a look at both one-by-one.

# [Signing with ECDSA](#toc.xhtml#s48a)

Suppose Alice wants to sign a message m with her private key d[a] and Bob who is the receiver wants to verify the authenticity of the message (z, which is a hash and truncated to be the order of *n-1*) using Alice's public key H[a], it goes as shown below:

*   Select random integer k from finite group {1, …, n-1)
*   Calculate P = *k*G
*   Calculate r = x[p] (mod n) ( x[p] is the x coordinate of P), if r = 0 then choose another k.
*   Calculate s = *k^(\-1)* (z + *rd*[a]) (mod *n*), where z is a hash of the message. If *s = 0* then choose another k.

The (r, s) forms the signature. Bob who will receive (r,s) and z, will be able to verify the correctness of the message by validating this with Alice's public key H[a].

# [Verifying with ECDSA](#toc.xhtml#s49a)

In order to verify signatures, Bob will need Alice's public key H[a], the hash z and the signature (r, s):

*    Calculate the integer *u[1]* *\= s^(\-1) z* (mod *n*).
*   Calculate the integer u[2] = s^(\-1) *r* (mod *n*).
*   Calculate the point *P = u[1]G + u[2]* *H[a].*

The signature is valid only if r = x[p](mod n).

# [Hash functions](#toc.xhtml#s50a)

There are many hash functions available in cryptography but we will limit ourselves here to the ones that are used in Bitcoin.

Bitcoin makes extensive use of cryptographic hash functions as we have seen in earlier chapters e.g. the ID of a block is the reverse double SHA256 hash of the block. The id of a transaction is also a double SHA256 hash. An address is the RIPEMD160 hash of a SHA256 hash. And last but not least, digital signatures involve hashing a transaction to sign and verify. Below is the list of Hash Functions used extensively in the Bitcoin protocol:

 
| **Hash function** || **Output length** || **Description** |
| --- | --- | --- |
| SHA256 || 32 bytes || Generates unique 256-bit value for a text |
| SHA256SHA256 || 32 bytes || SHA256 hash of the SHA256 hash. |
| SHA512 || 64 bytes || Generates unique 512-bit value for a text |
| SHA1 || 20 bytes || Generates unique 160-bit value for a text |
| RIPEMD160 || 20 bytes || Generates unique 160-bit value for a text |
| SHA256RIPEMD160 || 20 bytes || RIPEMD160 hash of the SH256 hash. |

**Table 3.1:** Various Hash functions used in the Bitcoin protocol

# [Elliptic Curve Cryptography in Bitcoin](#toc.xhtml#s51a)

Now that we have looked at overall basics on elliptic curves and cryptographic tools, lets now zero into how these tools are used in Bitcoin to generate private and public keys and Bitcoin addresses.

Bitcoin uses a very specific elliptic curve, namely Koblitz curves defined under the secp256k1 standard. For these curves, the sextuple parameters, {*p, a, b, G, n, h*} assume very specific values mentioned in the below table:

 
| **Parameter** || **Value** |
| --- | --- |
| p || FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFE FFFFFC2F or 2²⁵⁶ - 2³² - 2⁹ - 2⁸ - 2⁷ - 2⁶ - 2⁴ - 1 which is a really large number |
| a || 0x00 |
| b || 0x07 |
| G, Compressed || 02 79BE667E F9DCBBAC 55A06295 CE870B07 029BFCDB 2DCE28D9 59F2815B 16F81798 |
| G || 04 79BE667E F9DCBBAC 55A06295 CE870B07 029BFCDB 2DCE28D9 59F2815B 16F81798 483ADA77 26A3C465 5DA4FBFC 0E1108A8 FD17B448 A6855419 9C47D08F FB10D4B8 |
| n || FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFE BAAEDCE6 AF48A03B BFD25E8C D0364141 |
| h || 0x01 |

**Table 3.2:** Domain parameter values used in secp256k1 standard

When we assign the values to the elliptic curve equation, we get the final reduced equation for Bitcoin:

y²\=(x³+7) *mod p*

To be able to create a private key, first, we need to select a random number *k* which is to be selected from the finite group *(1, …, n-1)*, typically 256 bit or 32 bytes.

The selection of a proper random number is quite critical as even though the trapdoor function is "hard" but still possible to be solved in polynomial time and if the randomness is not enough it becomes easy for a malicious hacker to guess or calculate it using brute force or other techniques. Typically many tools are available which create randomness like `math.random()` function but that is most times, not the preferred way to do it in Bitcoin. Typically a tool like random character selector as shown in (**[www.bitaddress.org](http://www.bitaddress.org)**) is used which creates a collection of random words to be used with enough entropy for generating the random number *k*

A very simple way to do it is to select a bunch of random words, pass it through a SHA256 algorithm. This will ensure that you can have a random word group which can be converted into key and key being SHA256 hash, is complex enough and will be in the range of {1, …, (n - 1)}, where n = 2^256 is the largest value that can be returned by SHA256 function).

Let us do it right now by selecting a random set of words:

Passphrase *k = "This is a sample Bitcoin private key generation using a group of words"*

SHA256 of the words above:

`54a8d569ff66b826fa51ab99754b5da5ad6c489bc39aaa4151f0add43de6d0c7`

Typically, in code you use the function `Crypto.getRandomValues()` to provide cryptographically strong random values. There are many tools available for this at this point.

Most times the private key is not used in the raw form but is encoded into a more standardized format using a standard called WIF (wallet import format). This was done to enable some identifiable characteristics and ease of use for the Bitcoin private, public keys, and addresses.

There are various steps in this format to add metadata to this key as mentioned in the below steps:

*   Add the prefix of version number. For private keys it is a byte with hex value 0x80 to the key, it becomes: 
    
    `80 54a8d569ff66b826fa51ab99754b5da5ad6c489bc39aaa4151f0add43de6d0c7`
    
*   Append compression flag, with the following values: 
    
    1.  0x00 uncompressed
    2.  0x01 compressed
    
    In the original version of Bitcoin, keys were not compressed, which resulted in public keys of 65 bytes in place of the compressed 33-byte format. There is no specific technical reason for it but more ease of use. Compressed public keys use only the X coordinate value (32 bytes) appended with 1 byte identifying if the Y coordinate value is odd or not making it 33 bytes.
    
    `80 54a8d569ff66b826fa51ab99754b5da5ad6c489bc39aaa4151f0add43de6d0c7 01`
    
*   Calculate and append the SHA256 private key with its checksum at the end, which for us is value: A0AEEB98. This is calculated using the first four bytes of a double SHA256 hash process that takes the private key of whatever is being validated by the checksum. 
    
    `80 54a8d569ff66b826fa51ab99754b5da5ad6c489bc39aaa4151f0add43de6d0c7 01 A0AEEB98`
    
*   The last step is that a Base 58 encoding is done to convert the binary to text and will generate the final form of the private key. Due to the fact that we have prepended a version number, that makes the available range of values for private keys limited to always start either from the letter K or L, with the below-mentioned value range 
    
    1.  **Lowest possible value:** `KwDiBf89QgGbjEhKnhXJuH7LrciVrZi3qYjgd9M7rFU73Nd2Mcv1`
    2.  **Highest possible value:** `L5oLkpV3aqBjhki6LmvChTCq73v9gyymzzMpBbhDLjDpKCuAXpsi`
    
     Lastly, the reason Base 58 encoding and not the more logically sensible base 64 encoding was used is due to a special property of this encoding scheme. The output of this encoding does not contain any ambiguous characters are omitted: 0 (zero), O (capital o), I (capital i) and l (lower case L) as well as the non-alphanumeric characters + (plus) and / (slash) and = (equal to)
    
     So after the encoding, the final private key for us will be:
    
    `Kz4H575ewcuaZ4bsjDYX2RruzMKgWy7vddCYpLBcA9Tm4Vsvz9sm`
    

This is the private key d for the above-mentioned passphrase.

# [Public key generation](#toc.xhtml#s52a)

 If we recall from earlier, the cyclic subgroup and scalar multiplication properties, we choose the base point and then multiply (scaler) times to achieve a public key. This key *Q = (xQ, yQ)* forms the point *Q* on the elliptic curve. So we have:

Q = *d G,* where

*   *Q:* Represents the public key
*   *d :* Represents the private key
*   *G:* The elliptic curve point generator parameter with values as defined in *[Table 3.2](#c03.xhtml#tab3_2)* secp256k1 specifications

The public key, Q here, comprises both the x and y coordinate in the elliptic curve as it is a point in it. This is a 65-byte long value which consists of a leading value '0x04' and then x and y coordinates which are 32 bytes each.

Let us continue with our example and multiply *d*, the private key with base point *G* mentioned above, we get

Q (x, y):

`x = 9ad3f8cd0fbcf8b6c881db33755890557c5cc773cf5809db7b349a283baa9b6b`

`y = 83ade22b984dfa3121844a6b5b0375620ed0abc3639fa35a87e8864d5c12950d`

Public key is represented in compressed form as the X coordinate and a byte representing if the Y coordinate is odd or not. Getting the parity of the Y coordinate. (An even parity is 02 and an odd parity is 03) and the above mentioned y coordinate is odd, so adding odd parity value 03.

Full public key representation now can be represented as:

`03 9ad3f8cd0fbcf8b6c881db33755890557c5cc773cf5809db7b349a283baa9b6b`

Applying first SHA256 and then RIPEMD160 to the above value we get:

`d73d2906c6b48b7f42e364f0e6b455733df73803`

Bitcoin addresses are an encoded version of the above mentioned key. Following are the steps done for the encoding of key.

Add version no. '00' to the key to say this is for main network and a checksum at the end which is the first four bytes of a double SHA of the above key.

`00 d73d2906c6b48b7f42e364f0e6b455733df73803 D9442399`

Convert the result from a byte string into a base58 string using Base58Check encoding giving us the final address which is commonly used by mostly all wallets.

`Final Bitcoin Address: 1Ld5YjWQVQr8HwM7E1E1RcfGUmV9DJtuDA`

Each private key is associated with two possible public keys, the compressed version which we derived right now and also it is possible to use the uncompressed key.

This is a lot easier to copy and use address format which has been used from the inception in Bitcoin for a decade but now with much more innovation happening in the protocol, even more, the advanced protocol has been developed where the addresses are not used in the native form as mentioned above, but human-like characters are used like` $mybitcoinaddress` or `1mybitcoinaddress`. There has also been an email type format called paymail address (e.g., `mybitcoinaddress@mydomain.com`) which was launched very recently to make the user interface easier for non-technical users. We will be discussing this later in the book in detail when we talk about the paymail protocol.

# [Signatures and verification](#toc.xhtml#s53a)

As we have learned in ECDSA, Bitcoin uses these key pairs, (d, Q) extensively not just to create a chain of digital signatures (or blockchain) but also these signatures are used in the signing of messages. We will keep learning more and more as we go along to find more utilization of the signing and verification using ECDSA. It is similar to DSA as well but the only difference being, the key infrastructure is based on ECC and not something like RSA. The below picture shows both the signing and the verification process in Bitcoin:

![](images/Fig-3.6.jpg)

**Figure 3.6:** ECDSA Overview: Signing and Verification

# [BIP32 and BIP39](#toc.xhtml#s54a)

Over the period since Bitcoin was launched, one of the issues most users faced was the maintenance of the keys. You can imagine that if every time you share your public key to someone for a transaction, you are identified with that key forever and not that it is an issue, but if all of my banking transactions are published on a public ledger for anyone and everyone to see, it will in a way be a breach of my privacy. This is different from anonymous where there is no way to trace an address to an identity, but more like the tracing is possible but not for anyone else, this requires that people use many different private keys and eventually they keep losing their keys and in turn the money which the keys hold. This was the time when Satoshi disappeared, and the issue was resolved by many possible solutions proposed by various developers in the community and code maintenance team. Two of those **BIPs (Bitcoin Improvement Proposal)** which ended up adopted in an overwhelming way were BIP32 and BIP39.

As mentioned earlier, a single key works great but there were limitations like privacy and loss of keys if you maintain multiple keys. Ideally, the solution would have been advanced wallets (we will discuss a lot more about wallets in the next chapters) which are **SPV (simple payment verification)** and manage keys for the user but somehow the development happened not completely in that direction. One of those solutions was BIP32 which provided this scaling of keys at the cost of security but still, as of now, this is one very common method adopted, especially by cryptocurrency exchanges. Other Solution, BIT39 used a basket of words (12 specifically) to generate the private key and hence provide an easy paraphrase for the generation of the private key. Let's look at it in more detail.

# [BIP32: Hierarchical deterministic keys](#toc.xhtml#s55a)

In place of one key, we use a bag of keys based on this proposal, which solves the privacy issue (using a new address every time you do a new transaction) the key management is done by the wallet software.

The mathematics behind the idea is:

Q = d G - master private key. We define now, C as

C = c G - a sharable key pair or chain code

n C = n c G - multiple shared key pair where n is a positive integer.

Q' = (Q + n C) = ( d G + n c G) = (d + n c) G = d' G

With the above in mind, we can see now that, anyone can generate new public keys: Q' = Q + n C but only the master private key holder can derive new private key d' = (d + n c).

This is not the most secure way to handle keys in Bitcoin protocol as in an obvious way you can see the breach of access to one private key allows access to all private keys. Apart from that, it is also possible to derive other keys if one of the private keys is shared.

# [BIP39: Mnemonics](#toc.xhtml#s56a)

This proposal is to address the storage or ease of remembering, storing a particular private key. If you see, it is very hard to write down by pen a paper a private key as shown below:

`Private Key = KzdumWTQsUo8gt1P86yy8cVKfMFmSpV6A3tGj7yUaMgUzK1EEZzc`

But it will be quite easy to store a key which is shown as below:

`mnemonic = 'aware report movie exile buyer drum poverty supreme gym oppose float elegantly'`

That is what this proposal does in a very brief way. These above words are what a user needs to back up in place of the complex private key and the key can be generated anytime using these seed words. These words are not just any words but are pulled up from a specifically created word list called the BIP39 word list. These seed words are chosen randomly by the wallet when you create a new wallet. Again this word list was created to make sure the words are mostly random since it was considered that humans are not very good at creating random words on their own. There are few other details that we will discuss in a later chapter when we talk about wallets in detail.

# [Conclusion](#toc.xhtml#s57a)

We have gone through a whole lot of complex protocol level details in this chapter, which is mostly not visible to a developer or a user since now a much better set of open source libraries and tools are available for developing applications using Bitcoin. The purpose of the details in this chapter was to introduce and give a snapshot of some of the basic tools and concepts used in Bitcoin, especially in terms of private and public keys which are the heart of Bitcoin system and also to explain the kind of thought process which has gone behind the creation of a system which is smart, elegant and entirely based on the idea of having a security model which is always more expensive to break than to participate. One of the classic examples of this is the usage of the double hash in public keys. Hashing with two algorithms like SHA256 and RIPEMD160 makes the security more robust that even if one algorithm gets broken it will still be protected.

In the next chapter, we will continue where we left here and start looking at wallets and overall key management for users, what different wallet formats are there, what is an SPV wallet, and how new protocols are being developed to simplify usage and storage of these keys so that day to day non-technical user can be shielded from the underlying complexities that we discussed in this chapter.

# [Questions](#toc.xhtml#s58a)

1.  What is the difference between RSA and ECC?
2.  What are hash functions, trapdoor functions, and modulus arithmetic?
3.  What is the Diffie Hellman key exchange algorithm?
4.  What are the domain parameters for Bitcoin implementation of elliptic curve cryptography?
5.  What is a Bitcoin address and how is it generated?

# [CHAPTER 4](#toc.xhtml#c04)

# [All About Wallets](#toc.xhtml#c04)

**"Lost coins only make everyone else's coins worth slightly more. Think of it as a donation to everyone."**

*\- Satoshi Nakamoto*

This chapter of the book will cover the concept of a wallet. Bitcoin, as a system is in the true sense, peer to -peer electronic cash system, and hence acts as such. The concept of the wallet is similar to what the idea of physical wallet or purse is, it holds money as cash of various denominations and so does a Bitcoin wallet that holds keys to **various unspent transaction output (UTXOs)** which hold the coins of various values. We will look at how to create and manage wallets and various types of wallets, along with various features the new generation wallets provide. Then we will go into looking at the concept of SPV or simple payment verification which is an exclusive feature that makes it possible for a normal and non-technical user to be able to use wallets and Bitcoin transactions without the need to run a full node.

# [Structure](#toc.xhtml#s59a)

*   Concept of a wallet and use of wallets
*   Basic wallets for cold storage
*   New generation wallets and features
*   Simple Payment Verification

# [Objective](#toc.xhtml#s60a)

After studying this chapter you will be able to understand the overall concept of a wallet, and **simple payment verification (SPV)**, details of commonly used wallets like paper wallets for cold storage, and hot wallets. We will at the end discuss one simple way to store coins safely using an old Android phone for cold storage.

# [Concept of a wallet](#toc.xhtml#s61a)

Now that we understand what private and public keys are, let us look at how do we store and manage keys and the more important part, these keys are used to create digital signatures which are in turn associated with the stored coins on the blockchain. Wallets are software which does not just key management but key generation and transactions for a user. But before we go there, let us try to answer the question, does a wallet ever store coins?

The answer is quite simple, no, a wallet never stores coins. It stores keys and it is key management software. It is also a software that provides the functionality to create and receive transactions, sign messages, and decrypt messages. It is in all ways quite similar to any wallet app or software that your bank provides, the wallet itself does not store the money, but provides an interface to use your money.

So where are the coins stored? This must be easy to answer, the coins are stored in the blockchain as unspent transaction outputs or UTXO as they are commonly called. Let us see the below list of transactions starting from the point where coins are created, by a Coinbase transaction which if you remember from earlier, happens to be the first transaction of every block and contains newly minted coins as block reward awarded to the miner who wins the 10 mins game of finding out the next block hash. Coins from Coinbase are created by getting stored in a transaction on the block, which is locked by the private key of the miner. This is to say, now the miner has ownership of the property of 12.5 BSV coins stored in the blockchain. The below picture shows a few transactions that miner does once he receives the Coinbase transaction after mining a block and creates multiple outputs by splitting the 12.5 BSV he got:

![](images/Fig-4.1.jpg)

**Figure 4.1:** A miner spending coinbase coins via multiple transactions

In the above figure, we see that a newly minted coin from the miner which will be generated from a transaction that will be stored in the Bitcoin blockchain ledger possible to be unlocked by the miners' private key. The figure goes on to show two more transactions done by miners to buy a computer and a TV using Bitcoin ( for a very nominal price of 2 BSV) and remains with two different outputs. The one set of coins, 12.5 which were locked with one private key are now distributed into various outputs, with the miner himself retaining many of those outputs locked further on with different private keys. These outputs that are unspent and remaining stored on the blockchain as a record associated with a private key are called **UTXOs**, or unspent transaction output, and the complete transaction process is a typical function of an application or software called a wallet. Typically a wallet will provide users with one passphrase or mnemonic which will act as user password and the bunch of private keys along with the functions of creating transactions will be done by the wallet software.

Wallets have had a long process of evolution from the time Bitcoin was launched. We will start with basic to various versions of wallet software leading to the concept of how an SPV wallet is expected to work as per whitepaper. We will also go through a process to create a simple cold storage wallet using an old Android phone and various other strategies to store keys/paraphrases.

# [Cold storage wallets](#toc.xhtml#s62a)

Cold storage wallets mean a way to store your private keys so that they are not online. The safest way would be that they were never online, not even during the time they were created. Typically there are many tools available online which are JavaScript code most times that can be downloaded as to be available offline. The safest way would be (this is again for super secured solution) to have the tool downloaded from GitHub: **[https://github.com/pointbiz/bitaddress.org](https://github.com/pointbiz/bitaddress.org)** and use it in a machine that is never been online, that will be the safest to ensure there is no hidden malware on the machine. Once you have the code available on that machine, you can generate private keys in a secure way ensuring no one has access to it or seen it (except for if anyone is there with you while doing this setup).

Once you have generated the private keys by any of the methods that will be discussed further on, you can take a pen and paper to write these down. You can use an offline printer as well but make sure to clean up the data once done. Due to this reason, the approach using mnemonic or a brain wallet is considered the easiest and best for it. Typically writing down a long alphanumeric private key is a difficult and tedious task which is also susceptible to mistakes so that is not the most recommended approach. There is a slight difference between a seed and mnemonic but many times they are used interchangeably, the way I see, the difference is mnemonic is something user will be able to remember and seed is usually a random collection which user will have to store at his end and not needed to remember.

# [Paper wallet](#toc.xhtml#s63a)

The first set of wallets that emerged with the invention of Bitcoin blockchain were called a paper wallet because they were a paper printout of the public and private key. Till today these are considered to be the most secure way to store your keys (given you have followed the certain process to create them) and probably the easiest to generate and use.

The idea is very simple, and most software is a simple JavaScript code that can be run offline as well. It involves following as process:

1.  Generate a random entropy of words, phrases, or characters using either a random number generator function or a nice and easy way as to present in **[www.bitaddress.org](http://www.bitaddress.org)** where it allows users to move the mouse through a random character grid and captures those characters till it has enough length and entropy. The below picture shows how a wallet generator script works taking input from the randomly selected characters (shown by green dots) creating a completely random word set to generate the private key: 
    
    ![](images/Fig-4.2.jpg)
    
    **Figure 4.2:** A random character set generator using mouse movement to create private key
    
2.  The above character list will be used to create a public and private key as described in the last chapter. Below a set of private and public keys are shown, both as QR code and also the actual values. This is an actual wallet and can be used for transferring money to it: 
    
    ![](images/Fig-4.3.jpg)
    
    **Figure 4.3:** A paper wallet with the public and private key which can be printed and used
    
3.  The wallet shown above is a paper wallet with a single set of keys. This is typically printed out with the same offline machine and stored in a safe and secure location, like a bank safe deposit, or for that matter, in bunkers as one case may be of a company offering that service.

Various types of wallets can be generated for cold storage with alternate security features to address the complexity of storing private keys in the native form. The above paper wallet is not the easiest to store and reuse since it requires either writing down or using a key which is a long string of alphanumeric characters and even a single character incorrect will lock you out of your wallet.

# [Brain wallet](#toc.xhtml#s64a)

A brain wallet is based on a large complex paraphrase which is to be used for creating a private key. This provides ease of use as paraphrase can be something that can be easily remembered by the user and not needed to be stored anywhere or can be stored at safe storage in any form. One of the most interesting things about this is that it can get quite difficult to guess done right and can be done with things out in plain sight, making it a very attractive way to store coins in cold storage. Typically this involves coming up with a complex passphrase which is not so easy to guess by anyone. Below picture shows a sample passphrase (which is quite simple and should never be used as one) and how the brain wallet is generated by using the passphrase seed:

![](images/Fig-4.4.jpg)

**Figure 4.4:** Using a passphrase to generate a Private and Public key and a paper wallet.

Even though people think this is not a great idea but you can find these can be incredibly secure if you follow a good approach. An example is a challenge issued with hints given for a brain wallet that holds 50 Bitcoins (before the split so all 3 versions, BTC, BCH, and BSV) which has never been cracked. The link to that challenge is given below.

**Brain wallet unsolved puzzle: [https://medium.com/predict/how-to-make-a-brain-wallet-a8040b7c1993](https://medium.com/predict/how-to-make-a-brain-wallet-a8040b7c1993)**

# [Mnemonic wallet](#toc.xhtml#s65a)

Another way to create a secure and stable cold storage wallet is by using a split process with mnemonic keywords. Typically new-age wallets are using a 12-word mnemonic which acts as the passphrase for generating the private key for a wallet.

The splitting approach is to split these 12 words mnemonic into 3 parts in such a way that any of the two parts are needed to re-create a full key. This provides a security feature that is not present in earlier discussed cold storage wallets by not storing the full key in one place. Let me explain how is it done. Suppose below are the 12 words that are used for creating a wallet.

Switch collapse practice feed shame open despair creek road again ice least. To now create the 3 sets of cards with the above-mentioned wordset, you can follow the below-mentioned steps:

1.  Assign identifiers to each of these words (A, B, and C for 4 words each) as shown in the below *[Table 4.1](#c04.xhtml#tab4_1).*
2.  Create 3 sets using two identifier groups, Set 1: (A, B), Set 2: (B, C), and Set 3: (C, A).
3.  You now have your 3 sets of partial keys.

The below table shows how will you create the 3 sets of word list that we created:

 
| **Set 1** || **Set 2** || **Set 3** |
| A || Switch || B || shame || C || road |
| A || collapse || B || open || C || again |
| A || Practice || B || despair || C || ice |
| A || Feed || B || creek || C || least |
| B || Shame || C || road || A || Switch |
| B || Open || C || again || A || collapse |
| B || Despair || C || ice || A || practice |
| B || Creek || C || least || A || feed |

**Table 4.1:** Splitting mnemonics into 3 parts for safe storage

The 3 splits above, as you can see have the property that any two of these splits can be used to recreate a full key anytime but never possible to do so with only one. This way you can print and store these three different sets of split cards into three different storage places and not risking your keys fully in one place.

There are few other versions of these wallets mentioned above like vanity wallet, split wallets, etc which are not covered in detail due to the face they are some version of key manipulation and regeneration as discussed above.

# [Hardware wallets](#toc.xhtml#s66a)

Another set of wallets that emerged was called hardware wallets. These were small pluggable devices that are isolated and not connected to the internet for many versions but now a days few wireless versions are also available. They typically have a small processing unit like a microcontroller where the wallet code and keys are stored and a way to connect to the computer, which could be USB, Wireless, NFC, or Bluetooth. Their main properties are:

*   Most times since these are offline devices, they are protected from viruses, malware, etc.
*   Security - the private keys are often stored in a protected area of a microcontroller, typically encrypted so they block exporting of keys in plaintext.
*   Most times they use open-source code allowing for an independent audit of the software.

Any computing or storage device can be used to create a hardware wallet on your own as well so if you are well versed with computers there is not much need for your to do so, but these are excellent for non-technical users. Towards the end of this chapter, I will walk you through to create a similar hardware wallet using an old android phone which is to be kept offline.

# [New generation wallets](#toc.xhtml#s67a)

As the ecosystem for Bitcoin has grown, there was onboarding of a lot of new users who are predominantly non-technical. In addition to that, there are many services now available which allow users to use payment via Bitcoin so that created a need for not just cold storage wallets but also wallets that can be used in day to day transactions like paying for coffee. There are many wallets that have come up with are available for free to use which have come with a new and easier way to implement storing of these private and public keys along with other functions like transaction creation, signing, and verification, encrypting, and decrypting messages using the same keys. Few wallets have created a few innovative solutions as well which I will go through in brief and discuss an open-source wallet which is based on an electron framework in detail.

# [Handle system wallets](#toc.xhtml#s68a)

Handle system wallets were something that has come up in the last few years which changed the user onboarding and experience completely for Bitcoin. There are many wallets using this and let's have a look at what they are and how they work.

One big difference between Bitcoin and a traditional money handling system is the concept of accounts. The current financial industry and businesses are always identifying a user via an account number. This is very different from Bitcoin where the money that is associated is with UTXOs as we saw earlier, and there is no concept of account altogether.

The handle system wallets have kind of done that exact thing. They have created an accounting system that sits on top of the key system and the wallet does the key management invisible for the users. Typically every time the app is used for either sending or receiving a transaction, a new key pair is generated by the wallet and used for the transaction. This ensures that the privacy of the user is maintained for the user in the blockchain but still maintaining the legal compliance requirements that are done for the user and user transactions at the wallet end. All of these wallets typically use a 12-word seed which is used as the passphrase for generating these key pairs for user transactions. They also do not store the seed words in their servers typically so that they do not have to act as custodian for the user funds stored in the wallet.

# [HandCash](#toc.xhtml#s69a)

Handcash was the first Bitcoin wallet that came up with a smooth and easy onboarding and a key management system that did not require any technical know hows. They have called this system the handle system. The *handle system* represents user identity by a handle as shown below:

`$myhandlename`

The `myhandlename` is similar to a user name that a user chooses after installing the handcash app where he is needed to register with basic details. The `myhandlename` identity of the user is tied back to a set of private keys and public keys which are generated as a new key for each transaction. The complete key generation and management process are transparent to the user.

HandCash also provides an API for integrating and creating a payment integration available for a website using their open-source SDK called **cashport**. It is the way to enable using of handcash user handles and simple to integrate for your web application and there is simple TS code available on GitHub for doing this integration at **[https://github.com/HandCash/cashport-sdk-typescript](https://github.com/HandCash/cashport-sdk-typescript) :**

![](images/Fig-4.5.jpg)

**Figure 4.5:** HandCash wallet UI and UX which was one of the first to launch easy to use wallets.

There are few other wallets that have come up since then which are very similar to handcash like relayx wallet which uses a system that is very similar to handle system. There is Centabee which associated phone numbers with keys and uses that as the identity for users.

# [Money button](#toc.xhtml#s70a)

Another open-source free application that created a system that is user friendly was a wallet, which acts as a button. Money button was one of the first wallets that were designed purely as an object for being able to be integrated into a website with just a few lines of code and vola, you can enable content monetization for your website, put a payment wall for an article, or just about anything that you can think of. MoneyButton is similar to handle system in a way as it is also providing users an ID that is internal to the application and provides an abstraction to the internal key pair and transaction management.

Money button is like the Facebook like button, but with money instead of likes.

The money button is one of the most commonly used open-source tools in Bitcoin for integrating payments for either a user action or simply payment method for an application. It is quite advanced because using it provides the functionality of built-in currency conversion, authentication, smart contracts, support for multiple outputs, and the ability to write data such as files, receipts, or invoices to the blockchain.

In addition to this, the money button as also created an open-source library of crypto and Bitcoin tools called BSV library (GitHub: **[https://github.com/moneybutton/bsv](https://github.com/moneybutton/bsv)**). Using BSV library and money button API there are many applications that have implemented and it is a good tool for beginners and sometimes very advanced applications as well. We will be using the money button in many tools that are discussed in chapters further on so it will be a good idea to go through the code sample here to show how easy it is to integrate Bitcoin in a simple web application.

`npm install --save --save-exact bsv`

Below is the code for adding a money button which sends INR 5.29 each time swept to an address mentioned in the data-to field. This code added in your HTML page can enable users to donate money to an address mentioned in the data-to field:

`<!-- This line should go where you want to put your button -->`

`<div class="money-button"`

`data-to="16X9LKyuQ5N9QiR7iMD1NgdrdKd6RLN5an"`

`data-amount="5.29"`

`data-currency="INR"`

`data-label=""`

`data-client-identifier="a65023353f4a69a96a959fe5f909749c"`

`data-button-id="1569412161321"`

`data-button-data="{}"`

`data-type="tip"`

`></div>`

`<!-- This line can go anywhere -->`

`<script src="https://www.moneybutton.com/moneybutton.js"></script>`

The generated money button looks something like as shown below:

![](images/Fig-4.6.jpg)

**Figure 4.6:** Money button

Detailed documentation for using money button with HTML, JavaScript, and React is present at the link: **[https://docs.moneybutton.com/docs/mb-html.html](https://docs.moneybutton.com/docs/mb-html.html)**

We will keep looking at the details of the money button as a utility for application development in later chapters.

# [Desktop and multi-feature wallets](#toc.xhtml#s71a)

Full feature wallets are another category that has been present in the space pretty much from the start. Typically these wallets will have a fully functioning key management functionality, but also additional features like message signing, verification, encryption, and decryption plus a bunch of other features depending on the specific wallet while keeping the actual keys and sensitive data offline.

Electrum wallet is one of the wallets that we will discuss in this section. It has been based on something called the electrum framework and the client is a fairly simple UI. This wallet is written in python and maintained as an open-source project by a group of developers. The first version of Electrum wallet was launched back in 2011 with the following list of features:

*   **Password encrypted wallet:** Apart from the seed phrases, the user will encrypt the wallet with a password making it quite secure.
*   **BIP32/BIT39 key generation:** Wallet is possible to be regenerated by seed phrase even if the user forgets the password.
*   **Partial SPV but real-time synchronization with blockchain:** This wallet does not require the full blockchain to be downloaded so quite light weight, it does need specific nodes which host blockchain called electrum servers and the wallet syncs with the real-time. The client will also have the block headers downloaded but maintains a real-time connection with a full blockchain node as well.
*   All data is stored locally and transactions are also signed locally so at no time any private data is stored on servers.
*   Cold storage feature is built-in where the user can keep private keys offline and use the watch only mode for online use.
*   The wallet supports multisignature wallet, hardware wallet integration, and a list of servers that wallet can connect to so that there is no single point of trust and failure.
*   Wallet connects to block explorers etc. to show transaction details. It also provides a CLI interface to simulate Bitcoind. Bitcoind is a daemon program that is one of the main components of the Bitcoin network node software which simulates the Bitcoin protocol via command line.

The picture below shows how a typical wallet home screen looks like with various transactions and features that are provided by the wallet. The Electrum SV wallet code repository present at **[https://github.com/electrumsv/electrumsv](https://github.com/electrumsv/electrumsv)**

![](images/Fig-4.7.jpg)

**Figure 4.7:** Electrum SV and various features of the wallet.

# [Signing and verifying messages](#toc.xhtml#s72a)

We have looked at the standard functions and features of the wallet, but there are a few other sets of functionalities that are also possible using the key pairs that are stored in the wallet. The most obvious usage is using these keys to sign messages of arbitrary (non-transaction) data. This is then possible for anyone to validate the signing via the public key. This usage can be used for various scenarios as proof of signature:

*   You can sign a file to prove to anyone that you created it.
*   You can sign a message to someone for secure communication with the recipient.
*   Maybe sign an application or anything existing digitally to prove you created/built it.
*   Proving ownership of a specific Bitcoin address by signing a message with the same keys.

Electrum wallet provides this functionality as a feature of the wallet. You can both, sign/verify, encrypt, and decrypt a message using this wallet.

# [Hot wallets and multisig or split wallets](#toc.xhtml#s73a)

One of the first industries that spun in the Bitcoin community was the most obvious one, a cryptocurrency exchange where users can buy and sell Bitcoin. Typically these were places where users would include miners (who create the coins) and buyers and traders dealing in Bitcoin. At the start, these exchanges were quite disorganized and non-compliant in terms of legal verification and KYC but over a period of a decade since the launch, more and more KYC compliant exchanges have come up. These exchanges, unlike the stock market exchanges, are online 24/7 and allow users to buy and sell apart from other advanced trading features like margin trading and options trading. Typically these exchanges will have a wallet where the users will hold their funds and these wallets are referred to as hot wallets. In reality, any wallet which is always online can be considered a hot wallet.

Another type of wallet is called a **split wallet.** Typically this type of wallet will split the private key or the mnemonic seed into multiple shares so that at any point two or more of these shares are needed to restore the private key. There are multiple ways to do this from a very simple way of splitting seed words to fairly complex schemes to create multi-sig (short for multisignature) wallets using a known cryptographic algorithm called *Shamir's Secret Sharing Scheme.* You can read more about this implementation of the 2 of 3 key at the link present below.

*Gavin Anderson* GitHub: **[https://gist.github.com/gavinandresen/3966071](https://gist.github.com/gavinandresen/3966071)**

# [Simple Payment Verification (SPV)](#toc.xhtml#s74a)

Typically most of the wallet services have to connect to a node that is running a full node implementation of the Bitcoin blockchain or they run it themselves. Running a full node requires a significant amount of investment in the infrastructure and also cost involved with it. Why do wallets need to run a full node or need access to a full node, multiple reasons:

*   Getting full details of the current UTXO set for the given private key
*   Verifying the validity of the UTXO set (previous signatures, ownership of UTXO, etc.)
*   Creating and Sending new transactions to the blockchain

This requirement of running a full node is not mandatory since there is an alternative approach for doing this implementation dubbed as SPV or simple payment verification. If you remember from *[Chapter 1: Bitcoin Protocol: Origins and Concept](#c01.xhtml)*, each of the block maintains a Merkle tree of all transaction hashes in the block header. This is what is the trick, in place of downloading a full node and blockchain, if a node just downloads the block headers, they can perform the same checks of verification and validation that they have to do with full nodes using these block headers. This in the way recommended by the whitepaper to have wallets for individual users. Businesses that need to do a large number and frequent transactions still are recommended to run a full node wallet. There is an inbuilt wallet in the Bitcoin client software which is typically used by miners are businesses that are running full nodes.

Using an SPV, a user will at all times have a copy of the block headers containing the Merkle chain. This makes the SPV wallet just doing the key management which again is done at user's device or locally for each user making it a lightweight UI client which connects to blockchain the way a front end application does to a serverless AWS cloud APIs for getting the data and writing the data:

*   SPVs will connect to a network node that is hosting the longest chain.
*   SPV will be having a list of public address which it can query to the network nodes to get the UTXO balances.
*   To list the transactions associated with the keys it host, it can query the connected node to obtain the Merkle branch in which the transaction as shown below:

![](images/Fig-4.8.jpg)

**Figure 4.8:** Block headers from blockchain and tracing via Merkle chain validity of transaction Tx3

Any true SPV wallet will require to download the block headers and hence will do sync when the wallets are set up. There are a few other concepts in terms of wallets that are still to be discussed but we will keep the scope of this chapter at this right now and will be revisiting some advanced concepts in terms of new generation wallets along with BIP270 protocol) and true SPV wallets in [section 2](#p02.xhtml) when we talk about paymail and identity management.

# [Hardware wallet using an Android phone](#toc.xhtml#s75a)

An easy way to store coins is a hardware wallet and it can be created quite simply by using an old Android phone or a new Android phone as suitable. Let's look at the steps below:

*   Remove the sim card if any from the phone.
*   Do a factory reset the phone so that any possible app which could be malicious is removed.
*   Do the basic setup of the phone by creating a fresh new Google account (do not use an existing account).
*   During setup, don't back up your phone to any cloud services, nor Google's servers, don't select to stay up to date, don't enable any of the offered services like backups, location, bug reporting, etc. Pretty much do not allow any connectivity or services or billing information or any other information at all.
*   Setup a layer of security by using a large pin as possible for your phone and ease. The longer the better.
*   Uninstall any possible app that will not be of use (mostly uninstall everything possible to be uninstalled).
*   Once that is done, you can encrypt the phone so that it adds an extra layer of security.
*   Connect to Wi-Fi and only from play store install an SPV wallet like *simply.cash* or any other wallet with similar features.
*   Once the wallet is installed and keys are backed up, you can use the active wallet or hot wallet to send the needed coins to be put into cold storage.
*   Simply.Cash also provides a feature to create a watch-only wallet - this is a wallet which works like any other normal wallet does except when you try to send a transaction it will create a QR code representing an unsigned transaction. To sign this transaction from the offline phone, scan this QR code, it will generate another QR code which will be the signed transaction. Finally, the online phone can scan this new QR code from an offline phone which will then broadcast this signed transaction completing the sending of the transaction.

Below screens show how a typical wallet looks for this product and how the process of creating cold wallet works in the wallet:

![](images/Fig-4.9.jpg)

**Figure 4.9:** Simply cash wallet to be used for creating cold storage hardware wallet

Why is it so safe? Being offline the attack surface for the wallet is extremely small. It is also easier to set up and use than most hardware wallets available and most times less expensive than a typical hardware wallet like Ledger, Trezor, and keepkey.

# [Conclusion](#toc.xhtml#s76a)

We have not gone into technical details of creating and management of a wallet or the wallet architecture in this chapter as those details typically are not something that you will need to use when creating applications. Most times you will be able to use their product out of the box (like moneybutton) when developing apps or can use their integration SDKs like cashport. The one main thing that needs to be mentioned here to recap is that most times when you are creating an application you will be focusing on using the SPV method, which requires not to be a full node, but a node which is a lightweight client storing only the block headers. We will be discussing SPVs in detail later in the book as well when we discuss application development. In addition to that Electrum SV code is available as it is open source and that can be looked into if you want to understand the details of implementing a wallet.

You would now have a good idea of what wallets are and also a detailed overview of how to make simple wallets for storing coins that are offline for cold storage, various wallet options, and what is an SPV along with other things. Wallets overall are just interfaces that give you key management capabilities but there are always many ways to do that and know that the coins by itself are always stored in the blockchain locked by your keys. These coins can be unlocked only by transactions which are the entries of assets into the Bitcoin ledger.

In the next chapter, we will start to dig into the real specific details on transactions like their structure, creation, and broadcasting of a transaction, an assembly level language native to Bitcoin called transaction script and how to use it for creating not just simple transaction but also complex transactions like smart contracts and more.

# [Questions](#toc.xhtml#s77a)

1.  What is the need for a wallet and what is meant by key management, why is it useful to have different keys for different coins and not just have one key and store all coins at one address?
2.  What is the difference between cold and hot wallet?
3.  What is an SPV wallet and why is Electrum SV not a full SPV wallet?
4.  How will you create a multi-sig wallet and why is it safe to use?

# [CHAPTER 5](#toc.xhtml#c05)

# [Transactions and Transaction Script](#toc.xhtml#c05)

**"We can only see a short distance ahead, but we can see plenty there that needs to be done"**

*\- Alan Turing*

At the heart of Bitcoin, everything is transactions. In this chapter, we will look at how these transactions are constructed, what they are made of, and are various types of transactions supported by Bitcoin protocol. We will look at a special assembly language like programming done in Bitcoin using a completely new language called **script**. Turing completeness of Bitcoin and how Bitcoin solves the double-spending problem for the first time in the history of electronic cash systems. The chapter will show a little amount of code in JavaScript and some code snippets of nodeJs as well, but that part is optional to explore.

# [Structure](#toc.xhtml#s78a)

*   What are a transaction and UTXOs
*   Various types of transactions, data carrier transactions
*   Bitwise details of a transaction
*   Transaction script, a language for programming with the stack
*   OP-codes and how to use them in script

# [Objective](#toc.xhtml#s79a)

After studying this chapter, you will be able to understand the construction of transactions, what is the data structure of a transaction, what is transaction scripting language called transaction script and it's instruction set called **op-codes** to construct complex transactions like smart contracts and multi-sig transactions.

# [Transactions in Bitcoin](#toc.xhtml#s80a)

If there is one thing that can be called the heart of Bitcoin, that will be the transaction protocol that was created and implemented in Bitcoin, and transactions are like cells in the human body if I have to take an analogy, everything is made up of transactions. Everything else is just abstractions built on top of transactions. Bitcoin public ledger is a state machine, which is storing the state of UTXOs (or coins) at any point in time and transactions are the means which move the state from one point to another. This state of UTXOs at any point in time shows a ledger which accounts for all Bitcoin's that exist.

Let us have a look at the structure of a transaction to start with. As obvious as it can get, it contains an input and an output. Input to a transaction is the UTXO which this transaction will be spending, digitally signed by the owner of the UTXO by his private key, and output which contains the coins assigned to one or more public address who will be receiving these coins assigned via their public keys. The Basic construction and correlation of transactions are shown earlier in *[Chapter 1: Bitcoin Protocol: Origins and Concept](#c01.xhtml)* in *[Figure 1.4](#c01.xhtml#fig1_4).* But a transaction contains a bit more information apart from that, but before we go there, let us start with some basics.

If you remember, Bitcoin itself doesn't exist as a unit, the actual unit is called a **satoshi**. Bitcoin is an abstraction which is made up of 10⁸ *satoshi*. A satoshi is a non-divisible integer unit or the actual coin. In a typical transaction that is usually present in a bank account, there is one input and one output. It is significantly different in Bitcoin as if you remember there is no concept of an account, but the coins are held in UTXOs which means that I will have a set of private keys unlocking or giving me access to an address which holds my coins. A wallet typically does show aggregated coins for all the private keys that are held by a given wallet and this gives the possibility that when creating a transaction, there can be a need to get coins from not just one UTXO but more than one. Similarly, every transaction effectively will spend all of your coins from the UTXO it spends which means more than one output. In addition to that, every transaction also has a small fee associated with it, which goes to the miner. In short, a Bitcoin transaction has multiple inputs and multiple outputs and the coins always transfer all of the UTXO set that comes in the input to various outputs, it is possible that you can reuse the same input address which holds the original coins but that will come as a cost of privacy of the user and typically not recommended.

A typical way to understand Bitcoin transactions is to see them as Cash. If you are paying $ 70 to someone and you have a $ 100 bill with you, you will spend fully $ 100 and get a change of $ 30 back, but the original $ 100 bill is dissolved from your end and you are going to be left with a new note of $ 10 and $ 20 with you. So, when constructing transactions this has to be accounted for.

There are few concepts that should be understood before we jump into the details of transactions as these concepts are used heavily in transactions. We will be using a JavaScript library called BSV which provides an excellent tool kit for these operations that we will be discussing. The GitHub page for the library is

**[https://github.com/moneybutton/bsv](https://github.com/moneybutton/bsv)** and you can install the library using `npm` (package manager for Nodejs but you can use it in vanilla JavaScript as well):

`npm install --save --save-exact bsv`

# [Big numbers](#toc.xhtml#s81a)

Bitcoin uses very large numbers for various keys as we saw in *[Chapter 2: Economic Model and Network Structure](#c02.xhtml)* and these numbers require special functions to be able to perform any arithmetic operations on them. Pretty much anything involving cryptography uses big numbers and so does Bitcoin. This is the reason that special library and functions are used in Bitcoin as well for handling these numbers and most times this happens behind the scenes. Typically, when you create a private key, it is created using a big number. The specification, secp256k1 uses 32 bytes (256 bits) for most of the domain parameters and so does a hash.

The BSV library contains the tools for big numbers in `bn.js` and this enables you to do basic arithmetic operations like `add, sub, mul, div, mod, invm` (addition, subtraction, multiplication, modulus, inverse modulus) and comparison operators like eq, gt, lt, `cmp` (equal to, greater than, less than, compare). You can use `bsv.crypto.BN` to create the big number of variables.

# [Number formats](#toc.xhtml#s82a)

Bitcoin is very much designed in such a way that all of the code is prioritizing performance the most, which makes the programming quite complex. Number formats that Bitcoin uses is a demonstration of this. Bitcoin uses a whole number of formats, some similar to assembly level programming directly on X86 microprocessor if you have a background in that sort of thing, modulus) and comparison operators like `eq, gt, lt, cmp` (equal to, greater than, less than, compare). You can get an idea from the below table about what number formats are used and why:

 
| **Format type** || **Description** || **Usage in Bitcoin** |
| --- | --- | --- |
| Big endian || In computing, Big-endian is an order in which the most significant value is stored first, i.e. from right to left when writing (normally you see this representation when you see numbers) || keys, signatures |
| Little endian || Little-endian is an order in which the least significant value is stored first. || Hashes |
| Sign+magnitude || In this notation, the most significant bit represents the sign, 0 for positive and 1 negative. || bigints |
| Two's complement || This is something that microprocessor X86 uses, and a two's complement of a n bit number x is = 2^n\- x || ints |
| Fixed point || A fixed point means there are a fixed number of decimal places. Typically, bitcoin is written in fixed point, e.g. 1 satoshi = 0.00000001 bitcoin || bsv, satoshis |
| Floating point || Floating-point means the number of decimal places can change || mining |
| String || String of characters || display, RPCs, APIs |
| VarInt || Var int format with \[header byte\] - \[0 - 8 bytes\], varies in size from 1 byte for small numbers ( in this case header byte is the number) and 9 bytes for big numbers, stored as little endian, unsigned || Opcodes |
| ScriptNum || Used in Script programming language, typically for stack numerical operations. Normally 0 - 4 bytes but can overflow to 5-8 bytes as well. || Script language |

**Table 5.1:** Number formats used in Bitcoin transactions

Bitcoin uses all of the above formats to make the process simpler and faster by feeding the inputs the same way as it understands, but this makes programming a bit harder when you look at it. Normally a programmer will not have to care about this but explained to understand how Bitcoin processor architecture is.

# [Signature formats](#toc.xhtml#s83a)

One last bit which is sort of an extension of the things we have looked at in the last chapter is the signatures in Bitcoin are encoded in certain formats called DER (in Bitcoin transactions) and compact (in Bitcoin signed messages). This is different from signing a message that we discussed in the last chapter as when a message is signed, a prefix *Bitcoin Signed Message:/n* is always added to the message so that you can never sign a transaction in place of a message by mistake.

# [DER format](#toc.xhtml#s84a)

A signature consists of two big numbers (r, s) which are derived from the private key and a random number (256 bit) k as we saw in the earlier chapter. The way a signature is in the bitcoin transactions, it follows the format open SSL uses and it looks like the format mentioned below and is typical of 70 bytes or so: \[header, length, r-header, r-length, r, s-header, s-length, s\]:

*   The header is always 0x30
*   Length is the total length of what follows, including s and r
*   r-header and s-header both, have the value 0x02
*   r-length and s-length are the length of r and s respectively and typically 32 bytes
*   Both r and s are encoded in big endian sign-magnitude format

In a transaction, the signature is always appended by another field named as sighash and is present in the format \[der, sighash\]. Sighash is 1 byte and it describes how the transaction was hashed depending on what you are trying to do. You can blank the transaction signature, inputs, and outputs and depend on what you have chosen to do, needs to be specified in the value Sighash can take as shown below:

*   `SIGHASH_ALL = 0x01:` This means you are signing the entire transaction, as specified during the signing
*   `SIGHASH_NONE = 0x02:` This means you sign all the inputs but don't care what the outputs are
*   `SIGHASH_ANYONECANPAY = 0x03:` This means you care about the outputs but don't care about the inputs.
*   `SIGHASH_SINGLE = 0x80:` This means only sign this input and corresponding output
*   `SIGHASH_FORKID = 0x40:` This was something introduced during the forking of the BSV chain and a mandatory field in BSV for replay protection with forks BTC and BCH

# [COMPACT format](#toc.xhtml#s85a)

This format signature is used for off-chain standards that use Bitcoin cryptography or on-chain but inside of an `OP_Return` (we will be discussing this later in the chapter when we discuss op-codes) where the signature is not part of the metadata of the transaction. This is of a 65 bytes constant length in the format.

\[i,r,s\] where i is of 1 byte and is used to recover the public key from the signature. The entire thing will be using base 64 encodings to create the Compact format signature which is used to sign Bitcoin messages.

# [OPcodes](#toc.xhtml#s86a)

**Opcodes (operational codes)** are special one-byte instruction codes present in the transaction script that is understood by the Bitcoin protocol for performing a specific function on the stack for executing transaction instructions. These are understood and executed when a transaction is processed to perform various functions which we will be discussing in more detail when we talk about transaction script.

You can see them analogous to arithmetic instruction set for an x86 microprocessor. Bitcoin has about 175 opcodes which are used for various specific functions. Some of the examples of opcodes are shown below:

*   `OP_FALSE`: pushes zeros to the stack, value 0x00
*   `OP_RETURN`: signifies that the following data to the code is files for data storage and this transaction does not need processing. Value 0x6a
*   `OP_PUSHDATA1, 2` and 4 with values 0x4c, 0x4d and 0x4e where 0x4e or `OP_PUSHDATA4` says that the following four bytes are used to signify the length of the data meaning you can push up to 4.2 GB of data in a single transaction
*   There are a bunch of codes like `OP_IF: 0x63, OP_NOTIF: 0x64, OP_ELSE: 0x67, OP_ENDIF: 0x68`, and more for allowing coding of business logic when maybe creating smart contracts in a scripting language.

# [Scripts](#toc.xhtml#s87a)

Apart from the metadata like version, number everything in the Bitcoin transaction is a script, coded in a language again called **script** which uses various opcodes mentioned above. The way the compiler reads the script is from left to right and uses a stack-based processing system for these instructions. We will discuss a lot more on the script a bit later in the chapter.

# [Transaction inputs](#toc.xhtml#s88a)

As we have seen, there can be one or more inputs in the transaction which will be one or more UTXOs that you will be spending for the current transaction. All Inputs to a transaction are a script apart from the metadata and are present in the below-mentioned format. Each input record for a transaction follows the below-mentioned format:

`[txhashprv][txoutno][scriptln][script][seqnum]`

*   \[`txhashprv]: 256 bits:` hash of the previous transaction which this input will be spending, basically signifying where the money historically is coming from.
*   `[txoutno]: Unsigned integer, 32 bit little-endian:` The output no. of the previous transaction that this input will be spending bringing down to specify the exact UTXO. It is executed to validate a transaction.
*   `[scriptln]: var int`: length of the script which follows.
*   `[script]: Script:` instructions with signature signifying ownership of the UTXO. Typically called SigScript as it contains the DER format signature signed using the UTXO owner's private key. This is one part of the script used in the transaction along with the other part which is present in prior output (where this input UTXO was formed) called **SigPubKey**. This is also known as an unlocking script as it will unlock the UTXO and allow it to be spent.
*   \[`seqnum]: Unsigned integer, 32 bits, little-endian:` Original idea for sequence number was for payment channels. This is a concept for aggregating transactions before the coins are spent which we will discuss later in the book when we discuss advanced details, but in short, you can have the same transaction iterate up to 0xffffffff before this input will be spent. Typically for normal transactions, this field gets the default value of 0xffffffff so that input can be spent.

Needless to say, there will be one or more inputs possible in a transaction but all of them follow the above-mentioned format.

# [Transaction outputs](#toc.xhtml#s89a)

Now that we know what is present in the input, let us look at what is present in the transaction output. There can always be one or more output (normally there is one output of transaction fees, and others for the recipient and one for change if any). Below is the structure of a typical output record:

*   `[coins][scriptln][script]`
*   `[coins]: Unsigned integer, 64 bit little-endian:` number of satoshis's to be sent.
*   `[scriptln]: var int:` length of the script which follows
*   `[script]: Script:` instructions with the public key of the recipient for receiving the coins. Typically called SigPubKey script and this component of the script will be executed when the owner of this public key spends these coins in a future transaction. This script is also known as a locking script as this will lock the UTXO to be only possible to be unlocked by the corresponding private keys. Think of the locking script as a puzzle and the unlocking script as the solution to the puzzle. If you can solve the puzzle you are authorized to spend the Bitcoin.

# [Transaction format](#toc.xhtml#s90a)

Now that we have looked at various underlying concepts and what a transaction is made up of, let us look at on a high level what is the structure of a transaction:

`[Version] [TxInCount] [TxIns] [TxOutCount] [TxOuts] [nLockTime]`

*   `[Version]: Unsigned integer,` 32 bit little-endian: presently this has a value of 1.
*   `[TxInCount]: Var Int:` signifying the total number of inputs in the transaction that follows this field.
*   `[TxIns]:` The inputs of the transaction in the format we discussed above, concatenated with each other one-by-one.
*   `[TxOutCount]: Var Int:` signifying the total number of outputs in the transaction that follows this field.
*   `[TxOuts]:` The outputs of the transaction in the format we discussed above, concatenated with each other one-by-one.
*   `[nLockTime]: Unsigned integer, 32 bit little-endian:` The block no. or time after which this transaction will become valid. This is a special feature used to make a future dated transaction and the only time any transaction becomes aware of what block the transaction will be in. Usually, for a normal transaction, this field has a value of 0 which means always valid. We will discuss more this at a later point in this chapter.

There is no defined constraint on how many inputs and outputs a transaction can have. The only limit is that a transaction cannot be more than 1 MB and within that constraint, you can have as many inputs and outputs as you like.

# [Transaction](#toc.xhtml#s91a)

Overall apart from the details, we have discussed now, each transaction will have a transaction id which is the reverse (due to conversion to big-endian from little-endian) of the hash (double SHA256) of transaction data. To repeat, the above transaction structure will be the transaction data, then a double SHA256 is done on this data to create a transaction hash which will be in Little Endian format, and then a reverse of the hash is done to come up with the transaction ID.

A transaction is stored on the blockchain looks like as shown below. This is a transaction I did on with following details:

`Block: 00000000000000000790112f841d8d99a5fd5bca27a31f5c6e2935c4687c2125 (#596373)`

`Timestamp: 2019-08-20 14:27:15 utc`

`Version: 1`

`Size: 371 B`

`Confirmations: 7,003`

`Fee Paid: 0.00000372 BSV`

`Fee Rate: 1.003 sat/B`

The transaction had two inputs and two outputs. The two inputs are the two UTXO's which I had the private key for and the two output is 0.06588378 which is the change I kept in a new address and 0.007 BSV which was transferred to the intended recipient as shown in the below picture:

![](images/Fig-5.1.jpg)

**Figure 5.1:** A snapshot of my transaction ID: 832e8a70024a24c2513401c7daba3e81 62d84488821b720d6ad2de1deacf5297 from whatsonchain.com

And the transaction in hex looks like below:

`"0100000002c00d9b004c40d3817d8a1299b403d8a9d8839afbba42c0cbe08a88f76a9 1efc8010000006b483045022100ba66019c176aa678666afcf1ac0dd1a 5f3a3383 e7f5036 aaa330cd15b3a7fe8c022077c9d6fbd5ce469f43bf69be2bdfe48d03751b0 6b5c5d9c1abd54982115a5aa9412102f4b5c5129322369e40b329df637077f89e94 fae55a323c226a03e3a46d7116a1fffff fff7d1e49723a4b9a7f98e3811f3 002e0a9d26167cb7814b71024254da9 b70a870a000000004730440220 1c78d f6077ba0fa642baa11715ba01836ef 225d34daddb13452772b1d 7af5cae02205 934fa7ce07f0f24d6e1924cb4c1 931cd44e47388c19e0b89f9 e0a6e09ad4633412102bed3decad92 5f9aaf f8663d76c10 859544d3bd310dc 3118 c0f6ab8a294450902ffffffff02da876400 000000001976a914b651de8b3e 89d1276 cf1bbd8554ec 7d720da248888ac60ae0a000000000017a914996cd 7093efb1c9776e238ceb0e4 c47c5a36caf58700000000"`

As you can see above, the highlighted fields at the start and end are 4 bytes mentioning the version number and the `nLockTime` field. In between, there are the remaining transaction details which are not so easy to read and understand. Typically most libraries (like BSV library that was mentioned earlier) can do the parsing and formatting and so does any blockchain explorer like whatsonchain (open source, free to use).

If we see in more readable format the same transaction - first of the two inputs is shown below along with the `ScriptSig` which is tagged as `asm` shown below:

`{`

`"coinbase": "",`

`"txid": "c8ef916af7888ae0cbc042bafb9a83d8a9d803b499128a7d81d3404c009b0dc0",`

`"vout": 1,`

`"scriptSig": {`

`"asm": "3045022100ba66019c176aa678666afcf1ac0dd1a5f3a3383e7f5036aaa33 0cd15b3a7f e8c022077c9d6fbd5ce469f43bf69be2bdf e48d03751b06b5 c5d9c1abd549821 15a5aa9[ALL|FORKID] 02f4b5c5129322369e40b329df637077f89e 94fae55a323c226a03e3a46d7116a1",`

`"hex": "483045022100ba66019c176aa678666afcf1ac0dd1a5f3a3383e7f503 6aaa330cd15b3a7fe8c022077c9d6fbd5ce469f43bf69be2bdfe48d03751b06b 5c5d9c1abd54982115a5aa9412102f4b5c5129322369e40b329df637077f89e9 4fae55a323c226a03e3a46d7116a1"`

`},`

`"sequence": 4294967295`

`}`

The first output is shown below. This contains a `ScriptPubKey` as the output script and the public address of the recipient which the value of `0.007` is being transferred to:

`{`

`"value": 0.007,`

`"n": 1,`

`"scriptPubKey": {`

`"asm": "OP_HASH160 996cd7093efb1c9776e238ceb0e4c47c5a36caf5 OP_EQUAL",`

`"hex": "a914996cd7093efb1c9776e238ceb0e4c47c5a36caf587",`

`"reqSigs": 1,`

`"type": "scripthash",`

`"addresses": [`

` "3FgFhED2mX2MgdZ5dhUrjn4V1Vu5RKNbp8"`

`]`

`}`

`}`

There are a few different types of transaction outputs and inputs which we looked at when we talked about sighash which takes different values based on what type of transaction is being created.

# [Transaction verification](#toc.xhtml#s92a)

Now that we have visited all of the underlying ideas and data structures for a transaction or rather I would say, bitwise details of what a transaction constitutes, let's revisit how a transaction looks overall and what SPV is and how the transaction verification is to work when using an SPV method. If you remember we have touched about the concept of SPV as defined in the whitepaper in *[Chapter 4: All about Wallets](#c04.xhtml).* Here we go into more details as I wanted to first discuss transactions and then talk about the SPV verification of the transaction process and this is where the peer-2-peer aspect of implementing Bitcoin protocol comes into life. Peer to Peer electronic cash system as Bitcoin is defined in the title of the white paper means that a transaction can be done between two (let's say Alice and Bob) as a direct exchange between the two. Not via any third-party. And when Alice creates and sends a transaction to Bob, what she does is she creates a signed transaction for the UTXO that are locked by her private key and puts the output script with a public key owned by Bob. Bob can validate it by verifying the transaction using his private key and presence of the intended funds that the corresponding public key holds and send it to the blockchain for clearing and settlement (in other words, updating of the transaction on Bitcoin ledger via mining process). Both Alice and Bob are only required to maintain a copy of the block header currently around 50 MB in size) using which they can compare transactions rather than hosting a full node by themselves or connecting to a third-party which hosts a non-mining node.

So suppose Alice has a bunch of coins, they will be present with her in the form of signed transactions from the previous owner of the coins and a `SigPubKey` script with public keys that Alice owns private key for. Each of these transactions can be treated as digital coins that Alice has. Suppose one of these digital coins is in the form of **Tx1** as shown in the below picture and she has made a transaction **Tx2** for paying for her coffee to a merchant Bob. Below picture shows both **Tx1** and **Tx2** along with the Merkle path that needs to be passed on along with transaction:

![](images/Fig-5.2.jpg)

**Figure 5.2:** Merkle path for Tx2 and Tx1 along with the previous transaction to be sent by Alice to Bob

Suppose Alice buys a coffee from a coffee shop owned by Bob who is the merchant accepting money in the form of Bitcoin. Alice (using SPV wallet) will make a transaction which she will construct using her private key (**Tx2**) consisting of an input coin received in **Tx1 (1NyA…Td4nJ,** called *In*[1] which will be the output of **Tx1**. To maintain her privacy (to not reveal her IP address) Alice does not submit the transaction to the blockchain for settlement but she hands it over to Bob along with the Merkle path of the input coins (Merkle path of **Tx1**). Bob who now has the input coin's transaction, hashes the transaction ID to come up with the hash value and adds it to the Merkle path provided by Alice to come up with his value of the Merkle root and then he validates it with the block header he has with him for that same block. This ensures that the transaction and Merkle path he received from Alice is accurate and the coins are spendable (hence valid). Bob's wallet (SPV again) will validate the details and submit the transaction to the blockchain and voila, a transaction is complete.

There is a valid question here that the transaction is just submitted and not yet mined/verified and included in a block then how is the transaction complete. The process is similar to clearing and settlement in the traditional financial system. We will talk more about this in the next chapter when we talk about mining and 0-confirmation transactions and why this is a safe and secure way to do the instant transaction.

SPV method of verifying transactions and using the Bitcoin network is at the center of creating highly scalable applications on Bitcoin protocol. This enables lightweight applications since the amount of data to be stored for this type of verification is minimal *{public and private key, transactions, merkle path of transactions, and optionally the block headers}* at the user wallet end. So if an application e.g. an e-commerce website needs to have a user wallet it can still make the wallet non-custodial (in short, the user will own his financial data) but still have their app use this wallet just as easily as a typical loyalty points wallet works, but with real money in place of points. Typically, applications and wallets using SPV can approach this in the following ways as shown in the below picture:

![](images/Fig-5.3.jpg)

**Figure 5.3:** Two methods of transaction execution in SPV

Alice can do the above-described transaction in two ways, as shown in the figure above:

1.  When Alice transmits the transaction to the network and bob verifies the transaction from the network
2.  Also called Peer to Peer or IP to IP when Alice constructs and sends transaction details along with Merkle path to Bob. Bob can verify and transmit the transaction to the blockchain network.

The method **b** here is called IP to IP or Peer to Peer as this protects user privacy when making transactions. Miners or anyone for that matter except bob will not know who is Alice. This enables a user to own their data and privacy at all times, but in case of a legal dispute, it is possible to trace back to Alice via bob when the court order requires so. The title of white paper, Peer to Peer electronic cash system refers to this aspect as being peer to peer.

Double spending issue is one of the most common issues discussed when doing something like partial transaction (e.g. what if Alice gives the same transaction by being offline to both Bob and Charlie). This if you see will not be possible as when bob verifies the transaction Alice gives to him, he can identify that the coins are valid and the only way an attack can happen is when an attacker can overpower the network (with hash power) and will have to build a block deep enough to be able to double spend and again he can only double spend his coins. We will discuss this in more detail in the next chapter.

Now that we have looked into all basic information about the transaction, let us look at a transaction again fully and what it looks like including the script which is present in the transaction which will be what we will talk in detail next. Below picture shows the JSON format representation of a transaction:

![](images/Fig-5.4.jpg)

**Figure 5.4:** Transaction structure looking in a block explorer with various components (JSON format)

*   **Hash**: The hash of everything present in the transaction.
*   **Size**: The size of a transaction.

We already have spoken about all of the remaining fields that are shown above when we discussed the structure earlier `[Version] [TxInCount] [TxIns] [TxOutCount] [TxOuts] [nLockTime]`

Typically, a JSON structure is used to structure transactions and this is what is used in many application-level protocol and development methods so we will keep seeing more details as we go further on in the book.

There is only one transaction that does not have an input, which is the coinbase transaction. We have discussed this earlier as well and it is the result of a successful mining process and the first transaction in a block that contains newly minted coins.

One interesting thing to notice above marked in red outline is the `scriptPubKey` value which is a script. You can see that the value it takes is made up of a set of words. That is what we will discuss in detail now.

# [Transaction script or simply "script"](#toc.xhtml#s93a)

**"The script is a predicate. It's just an equation that evaluates to true or false. The predicate is a long and unfamiliar word so I called it script."**

*\- Satoshi Nakamoto*

The script is a special language or a scripting system used in Bitcoin transactions which acts as an instruction manual for transaction processing in Bitcoin. It is quite important to understand script as everything in Bitcoin transactions is executed by scripts. The script is very similar to a language called forth which was used historically for low-level programming of microprocessors. It uses a concept of the stack which is used for computing and uses words (similar to opcodes in the script) for the instruction set. When a script is to be processed, the processor works using a stack for pushing the instructions in it and processes the script from left to right.

The script as a language is a simple to set of machine-level instructions, which also means that it does not have all of the functionality that high-level languages like C, C++, Java, or Python have like there are no loops possible in the script. It is designed such a way for two main reasons as I see:

*   Processing power or CPU needed to execute the script is very thin, no to minimal compilation needed as the code is already machine level (almost).
*   All of the scripts end or execute in a finite and predictable and limited amount of time as there are no loops.

During the validation of the transaction, the `TxIn` Script (which is the signature) is prefixed to the output script present in the previous transaction which created this UTXO (`ScriptPubKey` of the previous transaction). Script processing happens and if the conclusion of the processing is evaluated to be true (we will discuss in detail how this happens later in the chapter) the transaction validation is successful. If the script processing ends with False, it means that the transaction validation failed and it will not be processed. A good analogy for how this works is that the output scripts are puzzles that specify in which conditions can those Bitcoins be spent. The input scripts provide the correct data to make those output scripts evaluate to true. In the whitepaper, *Satoshi Nakamoto* dubbed the Bitcoin script as it is a predicate, and this is the reason why is that so, it's processing always ends in a result which is either true or false.

The script is a highly efficient language that has many properties that are not yet utilized and unknown due to a lot of limitations that were imposed in the protocol for many years. These limitations we will discuss later in terms of op-code and also the usage of the stack which was done to limit the overall set of use cases and complex scriptwriting during the BTC phase (the year 2013 - 2018). With the genesis upgrade in Feb 2020, these limitations were removed and the original protocol was restored allowing things like non-standard scripts and a whole lot more, but first, let us have a look at the misunderstanding of Bitcoin script not being Turing complete.

# [Turing complete "script"](#toc.xhtml#s94a)

Turing completeness of Bitcoin script is a highly debated topic and most places where you will read about it or know about it, it will be mentioned that the script is not Turing complete. The concept of turning complete itself is quite misinformed and misunderstood. In one line, Turing complete just means it is possible to do a calculation in unbounded time (not infinite time as the misconception goes).

Turing completeness is a measure that is used in computer science for about the last 100 years to define a system that can compute every Turing-computable function. As per *Alan Turing:*

*It is possible to invent the single machine which can be used to compute any computable sequence. If this machine U is supplied with a tape on the beginning of which is written the standard description of an action table of some computing machine M, then U will compute the same sequence as M.*

Script system is Turing complete and it is possible to do Turing complete calculations with Bitcoin script and it allows not only for primitive recursion, but also to build complex evolutionary code done in cellular automata systems and **PSOs (particle swarm optimization**) programming. Bitcoin is a highly efficient Turing complete machine. The functional blocks are looped and when during processing these loops are unrolled by using two stacks (called main stack and alt stack) that are available in the script. Bitcoin is a dual-stack machine or a two-stack PDA and anyone who has gone through the details of if knows very well that a two-stack PDA system is a Turing complete system. We will not go into the proofs of this but anyone interested can look at link : **[https://papers.ssrn.com/sol3/papers.cfm?abstract\_id=3160279](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3160279)** for the paper for the proof of Bitcoin being 2 stack PDA and Turing complete.

In a somewhat oversimplified way, Bitcoin can make Turing complete computations in the following ways:

*   Unrolling a loop inside a script using the two stacks. This means that the same instructions that need to be looped into are put in n times (if the loop goes from 1 to n). This is quite similar to how a loop is unrolled in a typical compilation process and the code (assembly-level code) that is input to the microprocessor. A loop is just a compact way to write a program or logic but in effect, it operates always by unrolling it.
*   Typically for large complex scripts, there are other ways to make Turing complete computations as well by incentivizing the loop via multiple transactions
*   Looping inside of a payment channel can be done using the `nSequence` field. You can run the script by using it as the count for the number of times you want to iterate.

Just to point out (in the original version of bitcoin codebase) there is not just one stack in the script, there are three stacks available:

1.  The main stack,
2.  The alt stack and
3.  The `if` stack which is used to determine whether conditional branches in code are executed or not.

In the current version of transaction processing, the only main stack is used to process script using the unlocking script and locking script due to various limitations that were imposed over the years on the script capabilities.

You can read more about the stacks and also details on what went on for the removal of limitations with the genesis upgrade at the team’s official blog:

**[https://bitcoinsv.io/2019/07/27/the-return-of-op\_return-roadmap-to-genesis-part-4/](https://bitcoinsv.io/2019/07/27/the-return-of-op_return-roadmap-to-genesis-part-4/)**

With genesis upgrade, the usage of full script became possible and many interesting transactions were created using full script capabilities like the dead man switch: **[https://twitter.com/Stas33496/status/1230838632115732485](https://twitter.com/Stas33496/status/1230838632115732485)**

# [Script instruction set](#toc.xhtml#s95a)

The Script instruction set is quite similar in terms of various commands, etc. to any of those present in common programming languages like the standard arithmetic operations, logical operations like if-else, error handling, and function return instructions.

Each instruction is a one-byte little-endian `VarInt` signed integer. The instructions can be classified broadly into below-mentioned types:

*   **Data based instructions:** some of the instructions are to push data on the stack while processing of script, typically data follows the instruction.
*   **Opcodes: OPcodes (operational codes)** are function which a specific operation on the data present on the stack while processing. Typically, an OP code will take the top item on the stack which most times are data and does some form of processing and places the result back on the stack. 
    
    The OP-codes in turn is of varied types and varied purposes. These were carefully selected and designed so that most of the functionality that is possible in any language can be done using clever use of these opcodes. There are few classifications and let's take them one-by-one.
    
*   **Op-codes for pushing values:** These set of opcodes are specifically used for pushing various values to the stack. The special codes are also described in the picture below: 
    
    ![](images/Fig-5.5.jpg)
    
    **Figure 5.5:** Push opcodes along with their hex values
    
*   **Op-codes for control:** These set of opcodes typically are used for various control operations like `OP_NOP` does nothing and `if-else` statements. `OP_RETURN` will be discussed in large detail in a later chapter when we talk about data storage in Bitcoin blockchain. The `OP_RETURN` code is also used to create a lost-value transaction and will be discussed in large detail in a later chapter when we talk about data storage in Bitcoin blockchain. The below picture shows a list of various opcodes and also their corresponding hex values. 
    
    ![](images/Fig-5.6.jpg)
    
    **Figure 5.6:** Control opcodes along with their hex values
    
*   **Op-codes for stack-based operations:** These set of opcodes typically are used for various control operations like `OP_NOP` does nothing and `if-else` statements. The picture below shows the list of various operation codes which are used in the script: 
    
    ![](images/Fig-5.7.jpg)
    
    **Figure 5.7:** Opcodes for stack operations and functions
    
*   **Crypto-related Opcodes:** There are various opcodes that do a cryptographic operation on the stack items as described in the below table: 
    
    ![](images/Fig-5.8.jpg)
    
    **Figure 5.8:** Opcodes for stack operations and functions
    
*   **Op-codes for arithmetic operations and miscellaneous operations:** There are a whole set of opcodes that are available for doing basic arithmetic operations like add, subtract, multiply and divide along with a whole set of operations. These can be found in the GitHub library of the node implementation software under `script.h:`
    
    **[https://github.com/bitcoin-sv/bitcoin-sv/blob/master/src/script/script.h](https://github.com/bitcoin-sv/bitcoin-sv/blob/master/src/script/script.h)**
    
    The commonly used ones in this batch are the following two:
    
    *   **OP\_EQUAL 0x87**: Push TRUE (1) if the top two items are exactly equal, push FALSE (0) otherwise
    *   **OP\_EQUALVERIFY 0x88:** Same as `OP_EQUAL`, but run `OP_VERIFY`
*   **Op-codes reserved for future use:** There are about 13 opcodes `OP_NOP(X)` and `OP_RESERVED(X)` which are reserved for future usage. Some of those reserved codes have been used for various new operations in the recent past but a majority of them are still unused and reserved.

The `OP_NOP(x)` opcodes were reserved to replace the hash variables within Bitcoin in the future. `OP_SHA1` is already at a point that it is not considered `sfet` to use since there are new algorithms developed which can break it and it has now also been compromised. Similarly, `OP_RIPEMD160` is not expected to last more than a decade due to weakness in the underlying RipeMD algorithm. Other than `OP_HASH160` also uses the same requiring change in the future as well.

In time `OP_NOP2` and `OP_NOP3` were assigned below mentioned operations:

`OP_NOP2 = OP_CHECKLOCKTIMEVERIFY = 0xb1`

`OP_NOP3 = OP_CHECKSEQUENCEVERIFY = 0xb2`

Commonly known as **CLTV (check lock time verify)** and CSV was added to implement lightening protocol in the BTC which had carried over in the current BSV implementation. Much better on-chain payment channels can be built using `nLocktime` than the use of CLTV which has some security issues and does not do anything more than what can be achieved by `nLocktime`. Both the CLTV and CSV opcodes were reset/removed with the genesis upgrade in Feb 2020 from BSV blockchain.

Other reserved opcodes are `OP_RESERVED, OP_RESERVE1`, and `OP_RESERVE2` which are also expected to be used in the future for similar purposes.

# [Execution of the script](#toc.xhtml#s96a)

When the script is executed, a temporary stack data buffer is created during processing. This stack allows only push and pop operations and instructions can perform both. Since it is a stack, the items follow the LIFO method.

Let us take an example of one of the most common Bitcoin script, from *[Figure 5.4](#c05.xhtml#fig5_4)* the output script or the locking script that is marked in red and suppose we have the unlocking script called `ScriptSig` which is the input to a future transaction spending the coin received in the locking script called `ScriptPubKey`. The below picture shows the script from *[Figure 5.4](#c05.xhtml#fig5_4).* We show the visualization of the stack and also various legends to be used in this and the following pictures showing the processing of the script:

![](images/Fig-5.9.jpg)

**Figure 5.9:** ScriptSig and ScriptPubKey from the Tx1 and Tx2 which we discussed. Alice is making Tx2 to Bob to pay for her coffee.

During execution, the sequence of steps is, first the `ScriptSig` will be added before the `OP_DUP` instruction in the `ScriptPubKey` shown in the above picture making the instruction set like shown in *[Figure 5.10](#c05.xhtml#fig5_10):*

![](images/Fig-5.10.jpg)

**Figure 5.10:** Script will be executed left to right by pushing one item at a time. Note that stack is FILO

As can be intuitively guessed by looking at the series of instructions in the figure above, first the `ScriptSig` or private key will be pushed to the stack, then the `PubKey` will be pushed. Then we duplicate the item on the top of the stack with instruction `OP_DUP`, effectively we simply push a copy of the public key again onto the stack data structure:

![](images/Fig-5.11.jpg)

**Figure 5.11:** OP\_DUP will duplicate item on top, the PubKey

This instruction is followed by OP HASH160 which basically pops the top value and computes the cryptographic hash and then pushes the result onto the stack. Which means that the `PubKey` will be replaced by the address as we have seen in *[Figure 5.11](#c05.xhtml#fig5_11):*

![](images/Fig-5.12.jpg)

**Figure 5.12:** Final steps in processing script

Next, the Bitcoin address will be pushed to the stack and then the instruction `OP_EQUALVERIFY` will pop out the top item (Address) and validate that both values are equal if so it will move to the next instruction that is the `OP_CHECKSIG` will pop out the top two items, validate the public key and private key match and give an answer, true or false. If the answer is true then the script is executed successfully and if not, the script failed and the transaction will not be processed.

# [Standard and non-standard scripts](#toc.xhtml#s97a)

In the last many years the usage of script instructions was quite limited due to an idea or a restriction imposed or agreed upon for the acceptance of scripts by miners. This was done for many reasons which are beyond the scope of this book but that limited the possible use of most of the script functionality. This idea was called the standard and non-standard scripts and at some points only accepted scripts by miners were decided to be standard scripts. This does not mean that you cannot write non-standard scripts in your transaction but those transactions would be rejected by most of the miners making the usage invalid. So what are these standards? The code-level details of this is present in functions `IsStandard`() and `IsStandardTx`() under `policy.cpp:`

**[https://github.com/bitcoin-sv/bitcoin-sv/blob/master/src/policy/policy.cpp](https://github.com/bitcoin-sv/bitcoin-sv/blob/master/src/policy/policy.cpp)**

# [Script creation](#toc.xhtml#s98a)

There are currently 5 different types of transaction scripts that are used. They differ in terms of what type of output they are creating. Let us look at each of them one by one along with code using the **[https://github.com/moneybutton/bsv](https://github.com/moneybutton/bsv)** Bitcoin SV JavaScript library.

# [Pay to public key hash (p2pkh)](#toc.xhtml#s99a)

This is the most commonly used transaction output script. It's used to pay to a Bitcoin address (a Bitcoin address is a public key hash encoded in base58check). This is the same process we looked into details in *[Chapter 3: Cryptography, ECDSA, and Bitcoin Address](#c03.xhtml)* are shown below in *[Figure 5.13](#c05.xhtml#fig5_13)* are a process diagram:

![](images/Fig-5.13.jpg)

**Figure 5.13:** Building a P2PKH Address

`// create a new p2pkh paying to a specific address`

`var address = Address.fromString('1NaTVwXDDUJaXDQajoa9MqHhz4uTxtgK14');`

`var script = Script.buildPublicKeyHashOut(address);`

`assert(script.toString() === 'OP_DUP OP_HASH160 20 0xecae7d092947b7ee4998e254aa48900d26d2ce1d OP_EQUALVERIFY OP_CHECKSIG');`

# [Pay to public key (p2pk)](#toc.xhtml#s100a)

Pay to public key scripts are a simplified form of the `p2pkh`, but aren't commonly used in new transactions anymore, because `p2pkh` scripts are more secure (the public key is not revealed until the output is spent):

`// create a new p2pk paying to a specific public key`

`var pubkey = new PublicKey('022df8750480ad5b26950b25c7ba79 d3e37d75f640f8e5d9bcd5b150a0f85014da');var script = Script.buildPubli cKeyOut(pubkey);assert(script.toString() === '33 0x022df8750480ad5b26950b25c7ba79d3e37d75f640 f8e5d9bcd5b150a0f8 5014da OP_CHECKSIG');`

# [Pay to multi-sig (p2ms)](#toc.xhtml#s101a)

Pay to multi-sig is used for the scenarios when you have to create an output that should allow multiple keys to be sharing the control of the output funds, and the unlocking script will also need all of the key signatures to spend the output further on. Typically this is done as an output with n public keys of which m are required to sign to spend, known as m-of-n output. It is possible to custom assign values to n and m (like 2 of 3 or 2 of 5). This is a very rarely used method and in later time will be replaced by a better technology called threshold signatures:

`// create a new 2-of-3 multisig output from 3 given public keys`

`var pubkeys = [`

`new PublicKey('022df8750480ad5b26950b25c7ba79d3e37 d75f640f8e5d9bcd5b150a0f85014da'),`

`new PublicKey('03e3818b65bcc73a7d64064106a859cc1a5a 728c4345ff0b641209fba0d90de6e9'),`

`new PublicKey('021f2f6e1e50cb6a953935c3601284925decd 3fd21bc445712576873fb8c6ebc18'),`

`];`

`var threshold = 2;`

`var script = Script.buildMultisigOut(pubkeys, threshold);`

`assert(script.toString() === 'OP_2 33 0x022df8750480ad5b26950b25c7ba79d3e37d75f640f8e5d9bcd5b150a0f85014da'`

`+ ' 33 0x03e3818b65bcc73a7d64064106a859cc1a5a728c4345ff0b641209fba0d90de6e9'`

`+ ' 33 0x021f2f6e1e50cb6a953935c3601284925decd3fd21bc445712576873fb8c6ebc18 OP_3 OP_CHECKMULTISIG');`

# [Pay to script hash (p2sh)](#toc.xhtml#s102a)

Pay to script hash is a method which was introduced later in Bitcoin and most of the current wallets use this approach, especially the cryptocurrency exchanges use this quite heavily. This method, the output is paid to a special script called **redeem script.** It was implemented in the year 2012 via BIP70 and discontinued with the genesis upgrade in Feb 2020.

![](images/Fig-5.14.jpg)

**Figure 5.14:** Building a P2SH address

Challenge or unlocking script:

`OP_HASH160 <RedeemScriptHash> OP_EQUAL`

Locking or response script:

`<Response To Redeem Script> <Redeem Script>`

Example:

*   1-of-2 multi-sig challenge script: 
    
    `OP_1 <PubKey1> <PubKey2> OP_2 OP_CHECKMULTISIG`
    
*   1-of-2 multi-sig response script: 
    
    `OP_0 <Sig1>`
    
    `// create a p2sh multisig output`
    
    `var pubkeys = [`
    
    `new PublicKey('022df8750480ad5b26950b25c7b a79d3e37d75f640f8e5d9bcd5b150a0f85014da'),`
    
    `new PublicKey('03e3818b65b cc73a7d64064106a859cc1a5a728c4345ff0b641209fba0d90de6e9'),`
    
    `new PublicKey('021f2f6e1e50cb 6a953935c3601284925decd3fd21bc445712576873fb8c6ebc18'),`
    
    `];`
    
    `var redeemScript = Script.buildMultisigOut(pubkeys, 2);`
    
    `var script = redeemScript.toScriptHashOut();`
    
    `assert(script.toString() === 'OP_HASH160 20 0x620a6eeaf538ec9eb89b6ae83f2ed8ef98566a03 OP_EQUAL');`
    

# [Data output using OP\_RETURN (also called null data)](#toc.xhtml#s103a)

We have discussed this already in a bit detail earlier, and we will be discussing a lot more about data output in later chapters. This type of output pushes data on the blockchain, and uses `OP_RETURN` to stop the script processing signifying the bytes following the `OP_RETURN` is arbitrary data. Currently, it is possible to push up to 100KB data per transaction in the BSV blockchain:

`var data = 'hello world!!!';`

`var script = Script.buildDataOut(data);`

`assert(script.toString() === 'OP_RETURN 14 0x68656c6c6f20776f726c64212121'`

# [Non-standard scripts](#toc.xhtml#s104a)

It is possible to create pretty much any type of script rather than limiting to the above mentioned standard scripts in the original version of Bitcoin. This will become more and more useful when after genesis upgrade miners will start to accept any type of scripts and the check of functions `IsStandard`() and `IsStandardTx`() under `policy`.cpp is removed in the node software implementation used by miners:

`var script = Script()`

`.add('OP_IF') // add an opcode by name`

`.prepend(114) // add OP_2SWAP by code`

`.add(Opcode.OP_NOT) // add an opcode object`

`.add(Buffer.from('bacacafe', 'hex')) // add a data buffer (will append the size of the push operation first)`

`assert(script.toString() === 'OP_2SWAP OP_IF OP_NOT 4 0xbacacafe');`

# [Conclusion](#toc.xhtml#s105a)

We have looked at almost bitwise details of what a transaction is made up of, what type of formats and various representations of values are used in Bitcoin along with the primitive but very powerful programming language built in the Bitcoin software. These are vital details for developing any application over Bitcoin, however, now many libraries are available like the BSV library which provides out of the box functions to use for doing these complicated tasks. The knowledge of these concepts however remains central to understand how Bitcoin works. Script has been severely kept limited in its capabilities due to either the early developers who were part of the Bitcoin code software development team did not fully understand Bitcoin (like the idea of Turing completeness of script) or there were other factors driving many of these decisions. Bitcoin as per the first version that was released can handle perfectly legal (based on current laws) and complex smart contract construction as well. We will be discussing all those things in the next section when we talk about the various protocols that have been developed which work on the top of the Bitcoin protocol layer.

The next chapter will be covering the final but central part of Bitcoin blockchain which is the proof of work concept and the miners who are the non-trusted entities that engage in this proof of work to do transaction verification and create new blocks and maintain the blockchain.

# [Questions](#toc.xhtml#s106a)

1.  What are the various types of data types used in Bitcoin?
2.  What is ScriptSig and why is it called the unlocking script?
3.  What is ScriptPubKey and why is it called the locking script?
4.  Why is Bitcoin script Turing complete?
5.  Construct a Bitcoin script to add 4 and 5 using the ideas discussed in the chapter.

# [CHAPTER 6](#toc.xhtml#c06)

# [Mining and Network Consensus](#toc.xhtml#c06)

**“The design supports letting users just be users. The more burden it is to run a node, the fewer nodes there will be. Those few nodes will be big server farms”**

*\- Satoshi Nakamoto*

The biggest innovation that happened with Bitcoin was that it replaced the need for a trusted third party in the financial exchange of value to a non-trusted third party. This was until now not done in the history of any monetary or any other value exchange system. This also gave birth to a new industry and business known as Miners. In this chapter, we will focus on this new non-trusted third party, Miners, along with details of what happens in the process of mining, what miners have to do and how they compete with each other. We will then discuss various attacks that are possible, the idea of Nakamoto consensus mining as an overall industry. We will also discuss briefly the future of the mining industry.

# [Structure](#toc.xhtml#s107a)

*   Proof of work system and the concepts behind it
*   Mining as a new industry, the complementary nature of Bitcoin software and mining hardware innovations
*   Technical overview of mining and the overall process of mining
*   Miners as enforcers of rules in the Bitcoin ecosystem

# [Objective](#toc.xhtml#s108a)

After studying this chapter you will be able to understand the concept behind the proof of work mining system, what miners do in terms of their roles and responsibilities in the Bitcoin ecosystem, the process of mining, and various types of mining attacks possible. You will also learn the internal working details of the mining process and enforcement of rules via mining software.

# [The Byzantine generals problem](#toc.xhtml#s109a)

One of the century-old problems in computer science is known as the Byzantine Generals problem which is considered to be an unsolvable problem. This changed after Bitcoin as the solution was given in terms of the proof of work mining system that Bitcoin invented.

Let us first look at what is Byzantine generals' problem.

There are 8 surrounding and captured states of the Byzantine empire and were being oppressed by the empire. They want to revolt and overthrow the empire represented in the middle in *[Figure 6.1](#c06.xhtml#fig6_1)* below. The Army of the empire is quite strong and can resist any attack as long as it is done with less than half of the surrounding state armies. So if 4 out of 8 army generals coordinated an attack on the same day, they would lose. But if 5+ of the army generals coordinated the attack on the same day, they will be victorious and will divide the whole empire's land among each other.

If we consider the decision in hand for the generals, when they have to decide, they face a risk. Each general, if they attack and lose, then the emperor will execute them and then divide up their lands and grant them to the other generals who did not support their attack.

So while a general attacking will gain much if he could mount a successful rebellion against the emperor, he stands to also gain if the rebellion fails to garner a majority of the generals' support, and thus the revolting defeated generals' lands will be bequeathed to them.

How to send a reliable message to many generals at once, that cannot be corrupted? This scenario is shown below in *[Figure 6.1](#c06.xhtml#fig6_1):*

![](images/Fig-6.1.jpg)

**Figure 6.1:** Scenarios for a Byzantine generals problem

There is also a game theory aspect of this problem which is there is an incentive for rebel army generals to lie. They may lie about the day of attack proposed the time a message was received, and proposals that they had agreed to or disagreed with as if the attack fails, the Byzantine empire will reward them with the defeated army general's land.

Bitcoin blockchain needs a new block to be added every 10 mins and all of the participating miners should agree or come to a network consensus that the proposed new block by a certain miner is the right block and it can be added to the blockchain making it part of the immutable storing of information. The revolting army generals are the miners and the Byzantine fortress is the new block. Miners represent themselves by their hashing power as their vote or decision towards the addition of the next block. Victory is the successful addition of the new block and this happens every 10 mins by design. This problem overall was solved using proof-of-work and an immutable ledger.

In 1993, something called **Proof of Work (PoW)** was invented by *Cynthia Dwork & Moni Naor.* PoW meant that you can make your computer do a provable amount of work before you can send a message. If a message arrived without proof of sufficient work (by solving something called a hash puzzle), you disregard the message. Further details about this invention are present at:

Pricing via Processing or Combatting Junk Mail by *Cynthia Dwork* and *Moni Naor* **[http://www.wisdom.weizmann.ac.il/~naor/PAPERS/pvp.pdf](http://www.wisdom.weizmann.ac.il/~naor/PAPERS/pvp.pdf)**

This enabled a system where a message will be valid only if there is the needed proof of work involved with it, else its outright invalid. The PoW problem is kept sufficiently hard so that re-doing it during the given time is impossible and more expensive to do in comparison to what effort will it take to be honest in this endeavor.

So to go back to the analogy, now when one general signals a message to the remaining 7 generals, about the date of the attack, he can do it only once and redoing it will require him to do a large amount of work to write a new message. This is how the first part of the problem was solved in Bitcoin.

Coming to the second part, the game theory aspect, was to address the dis-incentivization of lying also meant the solution to the famous double-spending problem in electronic cash systems in the past. Double-spending is just spending the same coin twice, by sending the same coin to Alice, and Bob.

Before Bitcoin, a central coordinator or authority was needed to prevent double-spending of coins. This is similar to the game theory problem we discussed earlier where generals can lie about the date of the attack. Bitcoin's proof of work system solves the problem of lying by making lying costly (The amount of work to be done to redo the solving the proof of work and transmitting the dishonest message in this system is much more than accepting the honest message).

Needless to say, this was a simplified explanation of the proof of work system and we will now go into details of how this system works and various scenarios that the system is resilient too.

We have already seen that miners are hyper-connected peers in the Bitcoin network in *[Chapter 2: Economic Model and Network Structure](#c02.xhtml)* and the structure of a block in *[Chapter 1: Bitcoin Protocol: Origins and Concept](#c01.xhtml).* Let us look now at the process in detail of how the miners work to create these blocks again.

# [Block creation process](#toc.xhtml#s110a)

A block is created when the miner(s) solve the hash puzzle and calculate the hash for the new block. To solve the hash puzzle each of the miner will take the following and calculates the hash puzzle as shown in *[Figure 6.2](#c06.xhtml#fig6_2):*

![](images/Fig-6.2.jpg)

**Figure 6.2:** High-level description of the mining process

Let us look at each of the components shown in the diagram and understand mining.

# [Transactions in MemoryPool](#toc.xhtml#s111a)

When a node receives transactions, it will keep them in a secondary area or a temporary buffer area called the Mempool where they are stored until they get included in the next candidate block. Every node maintains this buffer which stores the transactions that are in the queue for getting processed once it receives them. Each miner takes the transactions it has received present in the mempool and prepares this list of transactions that then gets included in the candidate block which it uses to solve the PoW hash puzzle.

The concept of Memory pool or Mempool as it is usually referred to was not part of the original design of Bitcoin. It was added back in 2012 by the addition of BIP35, an improvement protocol which added this centralization of transaction pooling contrary to the Bitcoin approach of using the network in a completely decentralized way. In the initial design, miners will receive transactions from SPV or full nodes connected to them in first-seen order, mined them, and sent blocks out to be built upon. The unconfirmed transaction set (UCTS) would sit in the RAM of various miners, then settle and build forward on top of confirmed blocks.

Keeping the mempool in memory works when blocks are small and lightly used, but the concept doesn't scale up with small hardware, and the UCTS certainly doesn't need to be kept in memory just because that's how it was done before! This is why Bitcoin Unlimited and other early big-block implementations started working on parallelization and other optimizations at the dawn of the scaling debate. But these optimizations were maligned by Bitcoin Core who created bottlenecks (the mempool is just one example) that created the fee market, delayed transactions, and created an opportunity for RBF, P2SH, Segwit, and Lightning Network—all predicated on the false notion that Bitcoin was inefficient. A future implementation of teranode software upgrade plans to remove the need to have mempool in the system.

# [Order of transactions](#toc.xhtml#s112a)

When we saw the structure of the block, it was described as a pretty frozen state with all transactions verified, validated, and also the order of transactions stored in the Merkle tree format stored in the Merkle root. This could give the impression that there is a certain implicit order that the transactions are added by miners in the block, which is not the case. The structure and order are fixed once the block is mined (hash puzzle is solved), and the block remains to be the one that is regarded by miners as the winning block to be added to chain after consensus, it's only then the block is frozen. Most likely all of the miners before they have solved the puzzle will have the order of transactions which will be very different from each other and that is the natural process of the system.

An alternative strategy to using a nonce to solve the hash puzzle is this order of transactions. Since when we do hash even a change of a single byte from its position can change the value of hash significantly, it is possible for miners to keep changing the order of transaction to keep trying to generate a new hash and see if that can be qualified based on the target value and wins the puzzle solution. This however is not the commonly used strategy by miners to solve the hash puzzle.

# [Candidate block](#toc.xhtml#s113a)

Each miner prepares a proposed block which if they win the hash puzzle they will be adding as the next block in the blockchain. This proposed block is typically referred to as a candidate block for that miner. Each miner will have a different candidate block as it depends on the way they have structured their block mining process apart from the order in which they have picked up the transactions from the mempool. A candidate block will have a set of transactions that the miner has in his mempool. Once he has selected the transactions, He will add the Coinbase transaction which is the only type of transaction which does not have any input UTXO but will have an output UTXO pointing to miner's address with an amount equal to the block reward (also known as block subsidy in the code). The miner then will construct the block header. The block header contains the following components if you recall from *[Chapter 1: Bitcoin Protocol: Origins and Concept](#c01.xhtml)* details:

*   `[Version]`**:** Version number of the block structure, currently it's 1.
*   `[PrevBlock]:` Previous block hash is used in the construction of the new block as this will ensure that no miner is preparing a whole lot of future blocks in advance. This ensures that the time available for a miner to create the block hash to solve the hash puzzle starts from the time or as soon as the new block gets discovered and he now gets the field value to start the calculation of the new block hash.
*   `[MerkleRoot]`**:** We have already looked at the transactions and each miner will pick a list of transactions from their mempool. Once they have picked up the final list the software will create the Merkle tree and the Merkle root.
*   `[Time]:` We have already discussed earlier that a block also acts as a timestamping server. The time (stamp) for each block is calculated as per the specifications described in the IEEE open-source IEC 61850 uint32\_t implementation (also known as Unix time): 32-bit calculation of the number of seconds since 1970.

There is flexibility allowed in the protocol for having a latency between different nodes as long as that difference is within an acceptable range. The latency or discrepancy allowed in Bitcoin for timestamps between miners is calculated based on two factors:

*   The timestamp in a block needs to be greater than the statistical median distance from the timestamps stored in the last 11 mined blocks, approximately this means that you can't have a time lower than the time stored in the 6th block before the candidate block. (The minimum value limit).
*   It must be lower than the *network-adjusted time* plus 7,200 seconds. (The maximum value limit). Your node software will keep track of the time (Unix time) difference between all the nodes it is connected to. It takes all of these times and calculates a median of these and the current Unix time +/- the median gives the network adjusted time.

`[Bit]:` It is a compact representation of the target value which is calculated as, \[first 3 significant bytes/first 6 bits, offset of the start of these bytes from right\] of the target value. E.g.:

Satoshi used 0x00ffff0000000000000000000000000000000000000000000000000000 as the first target during the network launch. Using the above method, lets calculate the bits (or `nBit` as in variable name in the code, `chain.h).`

Offset = 29 bytes or 1d in hex

Significant bytes = 00ffff

Bit value = 0x1d00ffff

`[Nonce]:` Nonce is a number typically designed to be used for incrementing and changing the value generated for the block hash when solving the hash puzzle. As seen in *[Figure 6.2](#c06.xhtml#fig6_2)*, a miner will keep incrementing the value of nonce until they find a block hash that is below the target value. The lower the target value, the more difficult it is to generate a hash that is lower than the target. This again is a 4-byte number.

There are few other network parameters that are present in the block header like the difficulty, which is a global parameter the same for all miners and is calculated every 2016 blocks. This is to ensure that the approximate time taken to mine a block remains around the period of 10 mins. The parameter is calculated based on the current network state and how long it takes for miners to mine a block.

*[Figure 6.2](#c06.xhtml#fig6_2)* summarizes the full process on a very high level for mining. This process is done by every miner that is participating in the network to solve the hash puzzle. Once a miner has found the new block hash successfully, they declare their win to all of the mining peers via transmitting the candidate block to be submitted for validation and verification to all the other miners. If the network consensus is achieved (more than 51% of the miners signal that the proposed candidate block is valid) the block is approved and added to the blockchain, and mines go on to mine the next block. This is a simple way to say it as there are scenarios when two miners are able to find the has around the same time, then what? These scenarios are also accounted for and let's discuss these scenarios in a bit more detail along with the idea of bad players trying to manipulate and destroy the network, called selfish mining and various scenarios of attack possibilities from malicious miners. Before we discuss that, there is one more concept we need to go into detail that is related to transactions and blocks, called block confirmations and zero-conf or 0-conf transactions.

# [Block confirmations](#toc.xhtml#s114a)

Blocks are added every 10 mins when a miner solves the hash puzzle, but if you remember there are 1-n number of miners who are making their candidate blocks and are trying to solve the puzzle, what happens when one or more solves the puzzle at the same time, and I mean the same to the milliseconds. What happens when there are two or more miners with valid solutions adding their block to the blockchain and what happens to the transactions which are present in one block and not in the other block? We will discuss these scenarios a lot more in detail later in the chapter, but right now there is one aspect we wanted to focus on which is called block confirmation. It is defined as a term for each transaction, on how many blocks have been confirmed with that transaction in it. It will be one confirmation when the block containing the transaction is confirmed and added to the blockchain. The more the number of blocks that are added on top of this block, the more the number of confirmation.

Typically most transactions are considered secure with zero-confirmation. This means that once a transaction is propagated to the network of miners, even though the transaction is not yet included in a block, but only confirmed by a miner, it is secure enough to be considered a valid transaction. There is maybe one in a billion chance that a highly resourceful miner can do a double spend of the transaction, but that too with a downside of adding a crime (provable with evidence on the blockchain) on his name. Most times all of the small transactions are considered safe to be with 0-confirmations and this is how the instant transactions are achieved in Bitcoin blockchain. Before we go into the process of 0-conf, typically for large transactions, it is recommended that one should wait for 6 confirmations. This is also called the depth, which means, how deep the transaction is buried in the Bitcoin blockchain. Another example is that coinbase transactions are mandated to wait for a depth of 100 blocks before they are allowed to be spent.

The reason for waiting for a few confirmations (like 6 confirmations for large transactions) is to give time for the network to stabilize. Bitcoin is as we discussed very much like organic network, it will allow for many errors to co-exist but the most powerful one wins, which means that even if two miners find the block at the same time, and both then have to continue to keep fighting to add not just this current block, but the netblock to that so that this temporary split that has happened in the network chain, can be decided by the criteria, *the longest chain wins*. The possibility of orphan blocks happens in these scenarios where some blocks could be created as temporary network splits and later on when the network is stable and a longer chain is formed, the shorter forks are discarded as invalid. Till that happens, all of the miners will store and maintain all of the chain splits and orphan blocks.

# [0-conf or instant transactions](#toc.xhtml#s115a)

Bitcoin is meant to be not just a P2P electronic cash system, but it is an economic system as well. So when we have a 10 mins block addition time period, it will be highly unwanted and impractical to wait for 10 mins to buy your coffee and pay using Bitcoin. That is not the case as well, Bitcoin transactions get confirmed in real-time, instantaneously. In fact, when compared to current digital payment systems, they not just get confirmed instantly, but also get cleared and settled in 10 mins time period (typical real-time payments in current systems gets cleared and settled in a day).

When Alice goes to buy a coffee at a coffee shop and payes using Bitcoin, below is how this process is supposed to work.

Bob informs Alice the price of coffee at $2.00. Alice informs Bob that she intends to use Bitcoin for this payment. Bob (who accepts Bitcoin and has infrastructure setup for accepting it) will first find out the exchange rate for the time, suppose it is 1 BSV = $100. Using that Bob will hand over a template transaction to Alice, with details as shown below:

 
| Input 1 || Empty || Output 1 || Coffee Price |
| --- | --- | --- | --- |
| Input 2 || Empty || Output 2 || VAT at 20% |
|  ||  || Output 3 || Miner fees (ex.$0.0001) |
|  ||  || Output 4 || Tips |
|  ||  || Scripts and conditions ||  |
|  ||  || Output 5 || Change address |

**Table 6.1:** A sample invoice to be used by a coffee shop accepting Bitcoin using an SPV wallet

Alice's wallet will receive this invoice and evaluate to find the coins (UTXOs) which will be used to make this payment. In this case, suppose there are two input UTXOs being used, which hold 0.001 and 0.004 BSV ($1 and $4 in the exchange rate mentioned for that day). When Alice's wallet processes the invoice (it can happen offline as well if a proper SPV is used), it will fill in the needed details from Alice and hand over the updated transaction to Bob's SPV wallet software:

 
| Input 1 || Alice's Coin 1: 0.001 BSV || Output 1 || 0.002 BSV |
| --- | --- | --- | --- |
| Input 2 || Alice's Coin 2: 0.004 BSV || Output 2 || VAT at 20%: 0.0004BSV |
|  ||  || Output 3 || Miner fees (ex.$0.0001) |
|  ||  || Output 4 || Tips: 0.0001 |
|  ||  || Scripts and conditions || Signatures needed to spend UTXOs |
|  ||  || Output 5 || Change address : 0.0024 BSV |

**Table 6.2:** Alice will fill in her UTXO details along with her signature and sends filled invoice to Bob

This signed transaction is now handed over to Bob (along with Merkle path if Alice does this offline, SPV) and Bob will validate the details being correct, Bob will send the transaction to miner's mempool for verification and validation of the transactions. Bob does the following checks when receiving transaction details from Alice:

*   Confirms that the inputs in the transactions are not spent/valid using the Merkle path by querying the nodes
*   Ensures the completeness of the information provided by Alice along with enough coins to pay for miner fees.

Once satisfied, Bob will relay the transaction to as many miner nodes as possible so that the certainty of this transaction is frozen as soon as possible. A typical network will be able to ensure that a transaction is once verified, valid, and confirmed in a short time span of 2 seconds. So the miner will once after sending once, re-check the input UTXOs with miners making his transaction being valid twice.

Once all of the above is done, Bob can give the coffee to Alice now that he has confirmed twice that the transaction is valid and the inputs that Alice had provided are not spent. In case Bob finds that Alice is trying to double spend, he has a valid case of fraud and can take Alice to the court of law for a committed fraud (with evidence already being with him in the transaction, making the case open and shut).

This is all the process and approximately this process will take less than 2 seconds. Miners in this period will validate any attempts of fraud like double spend as well making the transaction secure and full proof and in the meanwhile, also giving a real-time payment, clearing, and settlement. This is for the scenarios where the purchases are happening for physical stores like restaurants, supermarkets, etc. In case if the purchase is online, it's even easier for merchants to protect themselves from any attempts of fraud as if the transaction is no good, they can cancel the delivery of the intended goods.

The issue of double-spend has been quite a concern and discussion in the early days of Bitcoin and even now since it was one of the innovations which Bitcoin has brought about for implementing an electronic cash system. In the above scenario, Alice can do a double spend only by colluding with a miner in such a way that the miner is so large and controls so much of the network that he is able to prevent Bob validating twice of any conflicting transactions that Alice has propagated to the network.

In case Bob has detected a double-spent transaction from Alice, that should happen within the first 2 seconds. Bob can make a choice to wait and see which one of the two transactions spending the same coins from Alice goes through the network confirmation or rejects the money transaction from Alice as soon as he detects a double spend. Either way, Bob has not lost anything as he has not given his goods to Alice and in addition to that, he has evidence of fraud committed by Alice. This issue was discussed in detail during the initial Satoshi discussions on bitcointalk.org: **[https://bitcointalk.org/index.php?topic=423.msg3819#msg3819](https://bitcointalk.org/index.php?topic=423.msg3819#msg3819)**

![](images/Fig-6.3.jpg)

**Figure 6.3:** Satoshi explaining double-spend transactions

A nice mining simulator to give an experience of how mining works is present at Mining simulator: **[https://yogh.io/#mine:last](https://yogh.io/#mine:last)** for more curious readers to explore. A full feature bitcoin simulator is present at:

**[https://bitsim.planaria.network/#/?id=bitsim](https://bitsim.planaria.network/#/?id=bitsim)** for getting a complete bitcoin simulation environment to explore.

# [Orphan blocks](#toc.xhtml#s116a)

Most times the issue of Orphan blocks and reorgs are discussed in conjunction with double-spend alluding that a foul playing miner can create very many double-spend transactions by doing a block reorg leaving valid blocks orphan. These are highly hypothetical scenarios that will never be possible in real life, purely based on economic and for that matter, practical reasons.

Bitcoin is considered as malleable. It is not a pure 100% secured cryptography system, but it uses cryptographic tools to secure the system in a *good enough* manner. The compromise of the security is done with a tradeoff of those attacks to the network that are rendered very expensively to do making it pointless to be creating extra code/work to secure against.

A good analogy is of iron and steel. Iron is pure metal but not so useful to make many applications like a knife. Steel is not pure, but it is malleable and used for these applications where iron which is brittle will break down. Bitcoin is such a system. Its flaws are things that make it resilient. Block Reorgs and Orphan blocks are such impurities that make Bitcoin a strong system that is not economical to break, and due to that, it will not be broken.

The way Bitcoin works are that orphan blocks are expected to happen as a normal outcome of multiple miners trying to win over each other to add the next block. This keeps the protocol code simple and still resilient to any orphan block related attacks by making it a property of the system and no more a flaw rendering it irrelevant to the reward structure.

The impact of orphan blocks does not do anything to change the reward structure of Bitcoin. On average 2016 blocks are created every 2 weeks, which is also the same period the network difficulty of mining is revisited and adjusted. The network can have 1, 2 or for that matter 20 orphan blocks in this period of two weeks of 2016 block creation, the number will still say the same, 2016, nothing more. So in terms of reward, a miner is incentivized not to focus too much on creating and maintaining an orphan block. It will only exist for a small period when two miners are (after solving the hash puzzle at the same time) competing by propagating their block to the network and making other miners accept their block as the block to build the next block on. This makes miners not just focus on the hash power to be able to create blocks, but also to build the right infrastructure to be able to propagate the blocks in the smallest possible timeframe to all the rest of miners to claim the reward.

This is an implementation of a game theory model called *stag hunt* where the participants can either jointly hunt a stag or individually hunt a rabbit. Needless to say, that stag is a much more significant and large reward than that of a rabbit and requires so, a more significant amount of effort and mutual cooperation of participants.

Same is the case with Bitcoin miners, the system is designed such that it costs incrementally different to follow different actions making it cost more to deviate from the *honest* strategy. Mining is not just about discovering new blocks by solving the hash puzzle, but it is about propagating the discovered block as well.

In this scenario, it's not just the network hash that miners bring to the table, but also how densely they are connected with their peers, how good connectivity is to propagate large blocks plays an equally important role in terms of miners winning a block reward. This also means that if I was a minor receives a new block from another miner, will want to propagate the same block forward so that I can start mining the next block on top of this block. This block can orphan if there is not enough network consensus of this being the block that wins the reward. Till the time this block is under enough depth in the chain, it is not certain and a parallel chain can co-exist for a period of time where this disagreement sustains. This is one of the reasons the Coinbase transactions have a restriction to be spent before 100 block confirmations.

Bitcoin *stag* is defined as a desire to create a near-complete small-world network (as we discussed in *[Chapter 2: Economic Model and Network Structure](#c02.xhtml))* and the rabbit is focusing only on increasing hash power. A miner has to create an optimized state not just in hash power but also network connectivity to be able to stay competitive else he will incur larger costs to operate at the same level as others who are doing both. This is due to the fact the network of Bitcoin is not a mesh or any other structure, but an almost complete graph shown in the picture below:

![](images/Fig-6.4.jpg)

**Figure 6.4:** Bitcoin is a densely connected almost a complete graph network of miners.

Let us see how this impacts by taking an example. Alice and Bob are two miners who have the same hash power with them, to explore how the network connectivity plays a role, let us assume these are the only two miners are competing with each other using two different strategies.

Suppose both have 100 units of hash power, but Alice has focused on network infrastructure quite a lot and has achieved a connection speed of being able to connect to all miners in the network within less than 0.2 seconds (even for large GB blocks). Bob however has focused more on mining hash power and has not invested that much on the network infrastructure achieving a network connectivity speed requiring about 3.2 seconds to propagate any block. We have a block time of 10 mins or 600 seconds on average. The time difference between Alice and Bob to get the block out to the network is 3 sec (3.2 - 0.2) or about 0.5 % (3/600) gain to Alice.

This means that in effect in place of both Alice and Bob acting like 50% miners Alice is acting as 50.5% miner. To be able to gain back this same amount of advantage, Bob has to increase his hash power in a larger proportion to match Alice's advantage (approximately 21 units more to gain 0.5% advantage).

The purpose of the above example was to show the asymmetric nature of Bitcoin mining competition and rewards attached to minor actions. A miner has to constantly not just focus on mining hash, but network infrastructure, high bandwidth and low latency network connectivity, security, and a good network management system working optimally at all times to stay competitive.

The other point is, if a miner's block is orphaned, it is a loss of money for his business (due to loss of hash power vested in it and also the loss of block reward). Orphans are how the miners vote, it is during this network consensus when they choose a valid block or orphan a block they assert their choice via this voting to the network.

This is what we saw as Bitcoin being a malleable system and not brittle, like steel not iron.

# [10 minutes interval](#toc.xhtml#s117a)

One thing that could come as a question to the curious readers that we have discussed just as an arbitrary number was the 10 minutes timeframe of the block creation process. Why did this configuration use 10 minutes and not 1 or 100 minutes block intervals?

There is a good amount of thought process gone behind this selection of intervals, based on modeling of monetary transactions and their distribution in global systems. These models are used in automated fraud detection systems in the traditional financial industry and interested readers can read through the below-mentioned research paper for more details.

Testing Homogeneity of Variance by *Dr. Craig S Wright.*

**[https://papers.ssrn.com/sol3/papers.cfm?abstract\_id=2953900](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2953900)**

This is relevant because of the way nodes validate the transactions and block. if two blocks are mined at nearly the same time, the first block to be received by a node is included and is verified by that node. The next block is placed in the *orphan pool* and is validated only after the initially received block. This *orphan pool* is added to the main chain for that node only when a further block is added to that *orphan pool* making that chain the longest and legitimate.

When a block is received that has a transaction the miner is missing, the mining node needs to download a copy of the transaction before it can complete validation of that received block. Each node validates the block (transactions, completeness, and a list of parameters done by Bitcoin core client in node software) before it propagates a block to the network.

To put forth these arguments in a simpler manner, there are two things about block mining, one is about finding a solution to the hash puzzle and the second is about propagating the block to peer nodes. When propagating the block to nodes, this distribution is approximately exponential, which means that if the block times are kept large, it will allow for a larger number of small miners and when the block times are very small, it will only allow for a small set of miners who will be able to compete. At a minute block interval, the orphan rate for blocks is around 2.5 to 3 times that exhibited at a 10-minute block interval, and at 10 mins block interval, the orphan rate moves closer to zero. Changing settlement (block times) to less alters the distribution and ends up favoring larger miners more than the small which in turn skews profitability.

Going not too much into the mathematics of these models, the optimal working of the Bitcoin network is achieved if the block interval is between 5 to 20 minutes. It is not possible to calculate the exact optimal time interval as that will depend on the time of the day, season, use, electricity price, and many other such factors. So the 10-minute interval was a guess, an approximation which was good enough at the point in time and it has been shown to work well in the last decade of the stability of network functioning. It was a tradeoff to achieve enough to make a system that is workable with the price incentive structure for mining nodes.

# [Block reorgs, forks, and various attacks](#toc.xhtml#s118a)

The current industry has come to assume that forks are a normal part of a blockchain or it is something that is to increase the value of the people who have invested in the coins (the concept of holding coins and waiting for it to increase in value). This has resulted in alternative chains but in doing so, each of these chains has moved away from being Bitcoin. Let us look at these scenarios.

# [Forks or chain splits](#toc.xhtml#s119a)

Forks or chain splits are in some ways an attack on the network as they take away value out of the network. This has happened a few times in a more significant way, but if we see the overall history, there have been 100s of forks that have happened for Bitcoin. Each time the network forks, they have to change some or the other rules to create a separate chain. For example, Litecoin has copied pretty much all of the Bitcoin protocol, but changed the Hashing algorithm to sCrypt and the block time to 2.5 mins in place of 10 mins and created a completely new system. These systems, maybe good for tech playground, add no economic or technical improvements to the protocol and in effect take away value from the Bitcoin protocol by either creating alternate competing protocols or the reputation of the network.

Due to a lack of overall understanding of the technology and economic model, the public perception was more focused on the ticker symbol rather than the underlying protocol. This has caused quite a lot of delay and even loss of brand value of Bitcoin in the last 10 years. Bitcoin became the preferred method of hackers and criminals at some point due to this misunderstanding causing a lot of setbacks in terms of mainstream adoption of the technology. It also resulted in the creation of alternative blockchains and projects, which only took some parts of Bitcoin protocol (like blockchain data storage method in hyperledger) and that resulted in the state of the ecosystem as we see it now with 1000s of blockchains, with many of them without any working product or any substantiated output, trying to sell coins on marginally legal cryptocurrency exchanges.

*[Figure 6.5](#c06.xhtml#fig6_5)* shows a snapshot of the major forks of the Bitcoin blockchain in terms of the chain, ticker name, and protocol:

![](images/Fig-6.5.jpg)

**Figure 6.5:** The Bitcoin fork story

Bitcoin was one system (with Ticker symbol BTC) since the launch but was gradually being restricted on an ongoing basis as we saw during *[Chapter 5: Transactions and Transaction Script](#c05.xhtml)* with Script. It became centralized due to the code developers (known as Bitcoin core development team) kept changing the protocol which made it impossible for application developers to keep building new applications on Bitcoin. When started there were many groups developing and maintaining different implementations of the node software (like Bitcoin Core, Bitcoin XT, etc.) but gradually all the alternative development teams died off and at some point, only the Bitcoin core software development team was keeping afloat making Bitcoin protocol governed by one single group of developers.

One of the biggest contentions was the block size limit of 1 MB which throttled the network to be able to scale to process billions of transactions. Instead, it was used as a feature to charge customers higher and higher fees (called RBF, replaced by fees) to be able to get their transaction processed. That process enabled users to bid with increasingly higher fees to prioritize their transactions, at one point in 2017 during network congestion the fees per transaction went up to 50 USD, compared to the one-thousandth USD of fees which should be the case. A 1 MB block only allows 5-7 TPS (transactions per sec) when Bitcoin is expected to support billions of transactions per sec. This could have only happened if the limits imposed on block size were to be removed. This killed the complete set of use cases which can be enabled using microtransactions with low fees. This was a disaster to be able to create a global financial system.

In addition to this, the other proposed change was to remove the digital signatures from the transactions that are stored in a block and store them with a link to the transaction to save space and keep the 1 MB block size. This was dubbed as Segwit or segregated witness. Segwit did not go well with many others who were not in agreement with these changes done to the protocol.

Segwit was to be implemented optionally to ensure the conversion of the Bitcoin BTC system to become a store of value like digital gold in place of peer to peer electronic cash system. The 1 MB block size limit was to be kept to limit transactions on Bitcoin main chain and subsequently move the bulk of transactions to a layer 2 payment channel solution called the **lightning network.**

This would introduce another set of centrally controlled enterprises which will be very similar to the current banking system. Not just that, these systems could lose transactions and money due to moving transactions off the chain by creating a secondary ledger and also making it prone to commit fraud (due to alternate books to be maintained). It has been many years since this proposal was implemented, and few of the lightning network implementations still struggle to make a legal and scalable solution which is in line with what was anticipated by the conflicting camps of miners and developers.

The other developer camp wanted to restore the original protocol and remove all the limits not just on the block size, but also on the script and in fact, use the `nSequence` field to implement payment channels to keep everything on-chain. We will see how to do that later in the book, but during that period, the miners agreed to split the chain into two, the BTC following their proposed changes of Segwit and the rest, and Bitcoin cash with the idea to restore the original protocol. This happened in August 2017 block no. #`478559`.

With Bitcoin Cash, the protocol restoration process started with the implementation of 32 MB blocks but again there was a situation where the developers got into a conflict over the restoration of the protocol where one camp wanted to implement changes to support things like pre-ordering of transactions by doing a pre-consensus of miners before blocks are created, moving the process of mining from POW to **POS (Proof of Stake).** In addition to that, they also wanted to implement changes to enable a different kind of layer 2 solutions called *wormhole* which involved token creation on Bitcoin by burning Bitcoin into addresses that do not have a private key and things to enable completely anonymous transactions. This resulted into the first hash war ( we will discuss a bit more when talking about attacks on the network) where this time it was not pre-decided that a chain split should happen and miners and protocol developers from both sides were asserting their claim to the chain by use of hash power they control. As a result, a further network split happened with two chains, BCH and BSV. BSV has finally started restoring all of the original design that was present in the whitepaper and the genesis upgrade finally removed most of the limitations from the code barring a few minor exceptions which needed to be kept for ensuring backward compatibility but does not impact the economic model of the protocol. There are few minor upgrades that will happen to restore things like the alert key system but overall the protocol is pretty much locked down for long term stability of building on the top of the Bitcoin network.

Just removing the limit of enabling 100kb of data with `OP_Return` created an explosion of innovation in terms of application development as we will see in later chapters. In terms of block size, currently, the BSV network supports 2 GB size blocks with a transaction capacity of at least 13000 TPS. With the limits removed, it is possible for miners (miner choice) to create any size blocks enabling at least millions of TPS if not more. It is proven by a few recent blocks in May 2020 in the BSV network, which mined about 1.3 million transactions with a size of about 350 MB. This is not even 1% of what the network is capable of, as we have been discussing, it needs to and is being prepared for not just GB blocks, but TB size blocks. Along with the freezing of the protocol, it will not be possible from then on to make any changes or to split the chain restoring the originally envisioned implementation by Satoshi Nakamoto and the only way Bitcoin can work as a one true global financial network, the same way internet is one global communication network.

One other central point is, block size needs to be as big as possible due to the fact that the block reward or also known as block subsidy is a measure also done to keep the incentive of miners intact to keep mining and it decreases by 50% every 4 years. The number of coins that exist today is already 18 million so total remaining coins are only 3 million which means that the miners need to be paid in other ways than just the coinbase transactions or block subsidies. That happens by transaction fees. But charging a high fee will pretty much kill the use case of microtransactions, and also the purpose of an electronic cash system which is cheap to use, but if there are a million transactions present in the block, that compensates the reduction of the block subsidy every 4 years. That is the most important and central point of large blocks, and at some point, unlimited block size so miners choose how much transactions they can put into the block to maximize their fees gained in the block.

Below *[Figure 6.6](#c06.xhtml#fig6_6)* snapshots a brief history of what has happened over the course of time in terms of the changes done to add limitations to the original protocol that was released by Satoshi in 2009 over the period destroying the economic model of Bitcoin:

![](images/Fig-6.6.jpg)

**Figure 6.6:** Timeline of changes made to Bitcoin protocol

The economic impact of these splits is obvious, it results in adding inflation to the system. Where there is one chain, there is one value set. With multiple chains, the value is split, so if Bitcoin overall was valued at 100 units, and there are 21 million Bitcoins, the total valuation would be 2100 million units, but with the chain split, we have 21 million BTC, 21 million BCH and 21 million BSV adding a lot of inflation in a similar way a fiat currency is inflated.

The learning from the above splits is quite simple but still profound. For something to be truly decentralized, and truly peer to peer, it has to be one single set of rules which no one has the power to change. Just like nature operates, there is one set of rules for everything and everyone and no one has the power to change it, implying the obvious assertion that Bitcoin is a biologically inspired network.

We have already discussed the double-spending attack in detail. There are few other attacks that are in theory possible but have never happened and are secured by the economic security model of Bitcoin. Let us have a quick look at those.

# [Sybil attack](#toc.xhtml#s120a)

A Sybil attack in computer security is a scenario when an attacker subverts a reputation system of a network or a service by creating a large number of pseudonymous identities and gains an undue influence in the network via controlling all these identities. This type of attack is typically done by malicious actors trying to take control of a peer to peer network like Bitcoin.

Bitcoin type network is by design Sybil resistant due to the nature of the nodes that hold any value being only the mining node. Only the mining nodes are involved or hold any value in terms of the transaction verification so even if any actor creates a huge number of pseudonymous identities with nodes unless they do mining which requires actual investment in mining and hashes power investment, they are considered of no value in the network. Also due to the hyperconnectivity of all mining nodes with each other, it is very easy to detect and subvert this type of attack. There has not been any instance of this attack in the timeline of Bitcoin till now. In fact, due to the concept of difficulty adjustment, there is an upper cap on how many miners can be there in the system at any time. The difficulty adjusts after every 2016 blocks are mined which makes the upper limit to the number of miners being that number because after that, the complete rules of the game are reset and a new cycle starts. It is largely misinformation which is shown as a proof to say about the decentralization of Bitcoin that there are maybe for example 10,000 nodes in the network, but most of those are user nodes which do not have the infrastructure to be able to mine any block, or even propagate the blocks fast enough to be of any value to the network. These blocks are just bystanders which don't count as they are not participating in the network making them irrelevant. Typically these are the nodes that are purported to say that Sybil attacks can happen to Bitcoin, but over 10 years and not one single instance of this being successful proves the robustness along with the underlying mathematics and economics proofs that it is not the case.

# [51% attack, selfish miner attack](#toc.xhtml#s121a)

This is an attack on a network where miners who control more than 50% of the mining hash decide to collude together and they can start to add any kind of blocks they wish along with changing the rules of the protocol. During the period of Aug 2018 - Nov 2018 a similar situation happened with the two mining camps got into a disagreement over the protocol changes that were proposed by one of the node software development groups. The proposed changes were to pre-order transactions by a pre-consensus among miners. This was not just the one change proposal, there were few other points of contentions like keeping the block size capped at 32 MB, Adding Schnorr signatures to allow anonymity, etc. Ultimately it resulted in a situation where two opposing groups of miners got into something that was dubbed as Hash War.

The process of consensus of the network is dubbed as Nakamoto consensus and miners are to vote using their node to signal their intention in terms of what changes they are supporting. There effectively were two mining camps with the (later to be) BSV camp which held more than 51% mining power during the days leading to the event of fork/network split on Nov 15th, 2018 at block # 556766. The opposing mining side had mining pools which were earlier mining in BTC network which they redirected at last day to mine BCH increasing their hash share temporarily to more than 51% and once they had that share they implemented a checkpoint which was to freeze the state of blockchain (similar to commit, and no changes possible in blockchain before that commit) along with protocol changes to have this commit checkpoint every 10 blocks. This eventually caused a hard fork of the network chain of BCH into two, BCH chain and BSV chain creating a demerger airdrop of BCH from the Bitcoin network. Nakamoto consensus did not come fully into play due to few factors like rented hash, checkpoint code changes which were more like a 51% attack on the Bitcoin network. Since then the split, the two forks have existed as separate protocols, Bitcoin and Bitcoin Cash.

The fork with BTC chain happened in a more planned and collaborative manner where two sets of miners agreed that they can no longer agree to same protocol changes (called segwit or segregated witness, which removed digital signatures from the transactions when storing on the blockchain) resulting into a fork airdrop of BTC from the Bitcoin chain (then named Bitcoin cash).

# [Block Reorgs and large miner attack](#toc.xhtml#s122a)

This is the hypothetical but most expensive and resourceful attack scenario to the Bitcoin network, where an attacker is trying to generate an alternate chain faster than the honest chain. It should be obvious by now that this will not be an easy endeavor to take up but still, if someone with enough resources and motive does so, it will not throw the Bitcoin system to arbitrary changes. The other honest nodes in the system will never accept any block containing invalid transactions as payment and any block that is containing these transactions. The attacker can only succeed in changing the transaction that he has spent to take his money back.

Details for proving the probability of the attacker chain taking over by not just finding the next block, but also catching up the n blocks that are left behind to catch up while trying to take over the network decreases exponentially as the value of n increases.

The reason these large miner attack doesn't work on B is shown with mathematical proof in the whitepaper's last section, section 11 named as Calculations:

*“The race between the honest chain and an attacker chain can be characterized as a Binomial Random Walk. The success event is the honest chain being extended by one block, increasing its lead by +1, and the failure event is the attacker's chain being extended by one block, reducing the gap by -1.”*

The probability calculation is shown in section 11 of the Bitcoin whitepaper along with the C code which proves that with the increase in the number of blocks z mined after the block where the attacker has started to make his alternate chain, the probability of attacker being able to catch up with the original chain in terms of being the longest chain rapidly drops towards zero. The code is shown below showing the probability calculations:

`#include <math.h>`

`double AttackerSuccessProbability(double q, int z) {`

`double p = 1.0 - q;`

`double lambda = z * (q / p); double sum = 1.0;`

`int i, k;`

`for (k = 0; k <= z; k++)`

`{`

`double poisson = exp(-lambda); for (i = 1; i <= k; i++)`

`poisson *= lambda / i;`

`sum -= poisson * (1 - pow(q / p, z - k));`

`}`

`return sum; }`

# [Energy consumption](#toc.xhtml#s123a)

One type of attack that the mining industry, proof of work, and Bitcoin faces quite often is the idea that it consumes as much energy as it is needed for the country of Denmark. This also asserts and marks mining as a wasteful industry and process as it consumes a lot of energy.

The arguments mentioned regarding the energy consumption seem to be similar to *Strawman fallacy* Bitcoin is painted as a wasteful system that uses too much electricity but the question of Bitcoin's efficiency can only be answered by addressing whether it is more or less efficient than the options with which it competes. If we compare it with Google, Amazon, or Facebook, they consume a lot more (1000 times energy consumption of Denmark) or for that matter, the top 100 US banks consume almost twice the energy projected to be consumed by the Bitcoin network by 2020.

# [Mining as an industry](#toc.xhtml#s124a)

Miners are the central non-trusted rule enforcement entities in the Bitcoin network. This is different from the general ideas of decentralization which is why I mentioned they are central entities. Miners are enforcers of rules in the Bitcoin public ledger and also the central point of control of what goes in the ledger.

There is a myth propagated that Bitcoin is permissionless because it is decentralized, which does not mean anything if you try to see what it is. It is not permissionless because if I choose to make a transaction and for some reason, miners choose not to process it (maybe due to no fee in it for example) then I cannot make that transaction, it is miners who act as the approver body.

Regarding decentralization, the problem is just because nodes are distributed does not mean it is decentralized. Centralization refers to control by a central body, which is exactly what the mining business does. The current financial system is more decentralized than Bitcoin, Bitcoin is quite centralized, so much that it is perfectly decentralizing power, it has one set of protocols with rules that are set in stone so no one can change it. It has one proof of work process which no one can change. It is one central global system to do financial transactions, very similar to what the internet and TCP/IP is, in reality, as we see, the Internet is not permissionless. As long as you follow the protocol and rules of the internet protocol (TCP/IP), you may have permission. The same applies to Bitcoin. If you follow the rules of the network and do not seek to change or subvert them, you have permission to build.

Bitcoin is a centralized currency with distributed, non-trusted governing body controlling it using proof of work, and it can easily handle any malicious attempts to influence any kind of deterrence from the rule set that is defined in the protocol which is again, as I said, set in stone from the genesis upgrade onwards. This is the security model of Bitcoin, the rules and protocol which are resilient are set in stone and not anyone can change it. When no one can change Bitcoin and the rules it operates on, it is then it becomes a truly open and free system for anyone to use and becomes decentralized.

Bitcoin is a centralized system that is decentralized in terms of usage. Bitcoin decouples power from money, so that money becomes a non-manipulatable, stable, honest, and fairly working system which is the same for all, no corrupt government, no large corporation, no powerful individual, nor any future force can change it, this is what Bitcoin is. When that is achieved when every person in the globe uses it becomes truly open-source, public, and open to use for all commodity ledgers which runs using a currency called Bitcoin.

With that understanding, let us look at mining as an industry and what is its evolution in the last 11 years of mining history. How it currently happening and what is in store for the future? Let us look at the history, present, and future of mining in the next section.

# [History of mining](#toc.xhtml#s125a)

The mining process started with the launch of the Bitcoin network in 2009. Initially, it was only Satoshi and a couple of others who were mining and the first version of Bitcoin following the genesis block broke down. The genesis block is dated 3rd January 2009 while the first mined block came about on 9th January. Initially, when the network was small and difficulty low in terms of the target, it was possible to do mining on CPU and it was done using windows servers running Bitcoin nodes. During 2009 - 2011 about 10 machines were mining. Gradually as the network kept growing, more and more people started mining and it reached a point when mining with CPU was not possible or was not resulting in winning blocks due to increased difficulty and more hash power was needed.

**GPUs (graphic processing units)** came to the rescue and were quickly adopted by miners as primary means to mine Bitcoin. GPUs provided larger processing capabilities for a while but as the competition kept growing miners started employing more and more powerful GPUs ultimately finding them at a point that more specialized hardware became the need of the hour.

Next were FPGAs (field-programmable gate array) which are integrated circuits that can be configured for a specific purpose by the end-user customer after the manufacturing is done. But as the nature of mining is, more specialized hardware was needed. The below picture shows a mining FPGA chip and components.

That led to the usage of **ASICs (Application-specific Integrated circuit)**. ASICs are specially designed hardware that can do only one specific type of processing, they have been in existence since the 1980s including some of the first personal computers were ASICs. Basically while manufacturing the programming is done in these hardware machines. So a SHA256d ASIC can only mine currencies that use the SHA256 algorithm and such. ASICs started to take over the mining industry and a war of creating better and better ASIC started.

Since the usage of ASICs mining industry has taken off in a big way where large commercial enterprises now have emerged which focus on specialized mining hardware and also software and both. This is something now done in large proportions across the globe where mining farms have come up to do mining.

![](images/Fig-6.7.jpg)

**Figure 6.7:** A mining farm used for mining Bitcoin using SHA256d algorithm

Another set of mining commercial enterprises that got created as a new industry was mining pools. Since the mining industry started becoming large, and it was not profitable or possible to mine individually, a new type of entity started to come into the picture being called mining pools. It involved individuals across the globe to buy one or a few miners and together they created a web of mining ASICs and collectively mine Bitcoin. The rewards they get are distributed to all of the mining individuals in proportion to their mining hash contributions.

Mining as an industry will in future professionalize a lot more than what it is now with things like transaction pricing and removal or lowering of the block reward making the miners depend more and more on the transaction fees that they receive from each block. This model will work only when the volume of transactions becomes huge so as to keep the individual transaction fee still low, but keeping the mining of blocks profitable. Even the role of miners from being a passive entity in terms of network operation will change to them coming more on the forefront as the enforcers of rules of the Bitcoin network. This will make the mining industry as a business which is working on cutting edge hardware and software trying to optimize operations constantly to stay ahead of their competitors, but also ensuring the Bitcoin network's integrity and robustness apart from other things like enforcing legal and AML compliance on the transactions before processing or even after processing them.

# [Evolution of Miners](#toc.xhtml#s126a)

Mining as an industry has evolved quite a bit since its inception. The first mining was done using standard Windows XP machines by Satoshi and then user computers during the initial years of Bitcoin. With the evolution of mining and the competitiveness making mining only possible by large ASIC miners and actually by mining farms it became impossible for users to be able to mine on the network. This gave rise to another kind of business called mining pools.

These mining pools are a distributed set of users/miners across the globe, running their mining rig, but pointing or making their hash power from their mining rig available to a common node running the mining software using that hash power. This collective network mining pool that merges the computing power of all participants to form a new block works by distributing the earned block reward (Fee + block subsidy) to the participating single miners their share based on their hash rate resource contribution.

Another version of this is Cloud Mining which allows the user to buy the output of cryptocurrency mining hardware located in remote data centers. This is more analogous to renting the equipment for mining by setting up a contract for mining bitcoin for a certain period for the defined fee. With all mining done remotely, this removes the issues faced by miners using powerful platforms, including sizable power usage, heat, insulation, and of course, maintenance. This type of mining is probably good for individuals who want to participate in mining but do not have the infrastructure and skills for doing the full setup by themselves. Cloud mining has certain disadvantages like lower profits than own hashing systems, open to the possibility of fraud because one central entity controls the mining and is a central point of failure and fraud. This has happened in the past where these pools engaged in scamming the individuals.

The key takeaway from the past is that there is an overdue need for miners to professionalize which has started to happen now and also the realization that is coming with the reduction of block subsidy to 6.25 coins per block, that it is the transaction fees that will be key to sustain mining as an industry and miners need to become businesses that work in the ecosystem to enable large transaction volumes in the system. For an enterprise to send its transaction to the Bitcoin network for a business-critical application they need to have a deal with a mining entity to ensure that they have a responsible risk hedge and an accountable entity to go to when something goes wrong. However, there are some huge benefits to the single miners that they can offload responsibility and hard work of running a mining operation to the cloud provider. They're maintaining the equipment, keeping it cool, and delivering you a potentially profitable service for your subscription fees. If you're unable to afford the space and time to manage these things yourself, because you're still a student or living in a small family home, for example, these become massively important pros.

# [Miners as Transaction Processors](#toc.xhtml#s127a)

Bitcoin has a built-in inflation block subsidy schedule hardcoded into the protocol itself as we have spoken about and that was to incentivize early supporters (block producers/miners) of the network to run hardware and act as a network node. This business model was inherently risky and temporary as there was no real basis of value in the token that they were getting as a reward. This was also initial times when there was overall uncertainty towards profitability due to the underlying value in coins being questionable. This old regime is changing, and Bitcoin now is positioning itself as an enterprise public blockchain where today there are about a million transactions at least produced by various businesses/applications that are producing real-world products for people.

Consequently, there is a need for *miners* to convert to the transaction processing business now by professionalizing mining. This requires a lot of changes to the way currently mining is done, and not just that, also how it is perceived. The whole idea of miners becoming more formal and legally regulated entities is what will bring professionalism to the mining industry and the mining companies involved with Bitcoin (SV) have started to do just that. With that, they will also need to offer standardized services that enterprises cannot work without. Some of them are discussed below:

*   **SLA or Service level agreements:** One of the fundamental things about traditional payment and financial networks is the notion of the **End-Of-Day (EOD)** transaction settlement. If Bitcoin is to become a foundational technology platform for financial settlements the technology must guarantee that transactions will be settled or finalized (minimally) by EOD. Therefore there is an inherent need for Transaction Processors to provide enterprise clients with Service Level Agreements that will guarantee transactions are confirmed and reflected on the blockchain in a set period of time.
*   **Fiat-based Fees:** Enterprises that will think of using a public blockchain will face the biggest challenge of transaction fees being denominated in satoshi and not in dollars or the local currency of their country. This creates a risk for them in terms of the price fluctuations in the market and a variable operating cost. Not just that they need to adhere to the corporate policies for maybe not being able to hold assets in digital assets.

As part of the professionalization of miners to become Transaction Processors, a protocol was launched known as MinerID to establish a reputation system for miners. Detail specs of this protocol are present at

**[https://github.com/bitcoin-sv-specs/brfc-minerid](https://github.com/bitcoin-sv-specs/brfc-minerid)**

MinerID protocol is an optional protocol for enabling users to identify and securely transact with mining nodes. For this, the mining nodes assign themselves a cryptographically verifiable identity and mark the blocks produced by them with this identity by embedding something called a **Coinbase Document** in the transactions that they mine with they win a block. This enables a verifiable reputation for miners based on transparency and performance.

Merchant API is another such professionalization of mining service. This API schema is a protocol defined for miners to be able to talk in a standardized format with wallets, customer, and enterprise applications. The current iteration of this API includes features like fee discovery and direct transaction submissions. Fee discovery allows parties the ability to know in advance the fee levels required from miners to guarantee the needed service level when creating transactions. Direct transaction submission allows for users to avoid outer layers of the Bitcoin network and submit transactions directly to miners. This mitigates many of the propagation issues in transactions due to unreliable network policies for users.

More detail specifications are present at

**[https://github.com/bitcoin-sv-specs/brfcmerchantapi](https://github.com/bitcoin-sv-specs/brfcmerchantapi)**. An excellent tool to interact with miner API is available at

**[https://minercraft.network/#/?id=minercraft](https://minercraft.network/#/?id=minercraft)** for the interested readers to explore

This idea of professionalizing miners is also tied to them taking up the responsibility of being the enforcers of rules in the Bitcoin network. This will need them to be a lot more accountable and under the regulatory purview as they are responsible for accepting any transaction and the data that comes with these transactions making them also responsible for executing any legal and court rulings on the Bitcoin network. That is needed for any network to be even remotely being established as a place where large financial transactions can happen across the globe. Miners acting with such responsibility can refuse to process and freeze any coins that were proceeds of a crime and keep them blocked until the original owner of those coins gets them back turing the mythical fable of gold turning to lead when not with the original master and back to gold when with the master again.

These are only the initial steps in this industry which is now starting to take a form. The expectation is that this will become a large scale industry as the current settlement and clearing companies which these miners are for global transactions.

To conclude, I wanted to quote the conclusion from the whitepaper. This is the best possible one-paragraph description of the Bitcoin protocol, it's working, and what it does. The highlighted text shows and describes the function of miners and how they operate as the enforcers of rules and law in the Bitcoin ecosystem.

![](images/Fig-6.8.jpg)

**Figure 6.8:** Conclusion text summarizing the crux of the Bitcoin network and the role miners play in network

It is important to note here that CPU power does not mean that every participating user votes from the pool, but the pool's vote will be counted as one vote. That is quite a misunderstood idea in the ecosystem today still after a decade of Bitcoin in existence. Mining is always meant for ending in large businesses running mining farms in data centers and that is what the future holds for this industry.

# [Conclusion](#toc.xhtml#s128a)

We have looked at a detailed overview of mining and network operational details and how consensus happens. We have looked at various types of attacks and what caused forks and network split and why the Bitcoin security model needs a large network so that it can never again be challenged or split using various means.

At the end of this chapter, we conclude to discuss the Bitcoin protocol in detail, its architecture, and various components like wallets, cryptography, and mining. We also looked at the details on what are transactions and the programming language script. This brings us to the place where we can start looking at the application layer from now on rather than the protocol details as it is pretty much going to be frozen from now on. The whole point of building on Bitcoin will not mean keep building updates or features to the protocol, but focusing on building applications with a new kind of architecture which uses Bitcoin blockchain for various features like storing data, microtransactions, identity management, IoT systems, Oracles, and AI components which do event-based tasks, and a whole lot of other things that haven't yet been thought out. We will go step by step in the next chapters to discuss all of these use cases which are right now having many companies and developers engaged in developing solutions for.

Next chapter, we will start the discussion with the first idea of building an internet that has money built into the system architecture. This changes the way we interact in the current form of the internet and how we build applications on the internet.

# [Questions](#toc.xhtml#s129a)

1.  Why is the order of transactions in a block not important and what happens if a transaction is not included in a block by the miner who discovered the new block but was included in a candidate block of another miner?
2.  What are instant or 0-conf transactions and why is it so important to have them. Are they secure?
3.  Why are miners considered as enforcers of rules in the Bitcoin network?
4.  Why splitting of the chain, forks that are made by changing rules called inflation, and also take value away from the Bitcoin network?
5.  Why are miners called non-trusted third parties in the Bitcoin network?

# [Section - II](#toc.xhtml#p02)

# [CHAPTER 7](#toc.xhtml#c07)

# [Metanet Protocol: Data Structures on Bitcoin](#toc.xhtml#c07)

**"All truth passes through three stages.**

**First, it is ridiculed.**

**Second, it is violently opposed.**

**Third, it is accepted as being self-evident. "**

*\- Arthur Schopenhauer*

A typical internet-based application works on various layers of protocols running on top of the physical layer. Bitcoin comes as a new kind of layer that works on top of the physical layer and can be replaced by the network, transport, and part of the application layer when done correctly. This is what the ideas of Metanet protocol bring in providing deep integration of built-in money and data storage capabilities. In this chapter, we talk about Metanet, a data structure protocol that operates on top of Bitcoin protocol enabling a new way to build internet applications where user identity, data ownership, and value exchange can be done securely like never before possible.

# [Structure](#toc.xhtml#s130a)

*   What is the Metanet and what does it do to be dubbed as replacement of internet
*   What is the nature of a data structure built on Bitcoin blockchain
*   How to build metanet applications
*   Data ownership in the Metanet world.

# [Objective](#toc.xhtml#s131a)

After studying this chapter you will be able to understand the basic concept of what is Metanet. How can it at some point in the future be the default way of developing applications and in effect work as a replacement of the current form of the internet? You will also learn how the data is structured in Metanet applications and how it is different from the current applications. We will also discuss the issue of data ownership and privacy to give a context of why is Metanet a paradigm shift from the current internet technology when building applications.

# [Introduction to MetaNet](#toc.xhtml#s132a)

One of the interesting attributes of Bitcoin transactions is that apart from transferring value, they have some properties which are unique and they can be exploited not just for value transfer but many different usages as well. So rather than thinking of a transaction as just what it does to make a payment, we can use specific instructions via `OP_RETURN` data field to assign more attributes and hence create the possibility to use it for more purposes.

So if we think of Bitcoin as a data storage protocol, which stores data in the immutable ledger, we can think of the idea of creating virtual data structures on the top of this data storage protocol. If you have worked with databases, you can think of it as an alias of data that is stored in various tables. The view just shows the data in a virtual table format which belongs potentially to many different tables in actual physical storage prospective. This idea of creating virtual data storage is formalized in the form of a standardized protocol which was named Metanet.

Metanet can be considered as a layer 2 (layer 1 being the Bitcoin blockchain) protocol and framework which specifies how to write data-carrying transactions and as a result create structured on-chain applications, creating an alternate form of the internet built on Bitcoin blockchain. User keys still can be managed via the wallets providing excellent privacy and security features of ECDSA key management enabling users and content creators to be fully in control of their data solving the large and ever-growing issue of the current internet, user privacy.

The current version of the internet is providing largely free services free due to their Ad based model where the users and content creators are the products whose data is then sold to custom advertising. This has been largely the reason for many billions of dollars of fines to large corporations like Google and Facebook due to breaching and leakage of private and sensitive user data. Apart from that, there is a large black market that exists (specifically called deep net and darknet) which enables a whole lot of criminal activities, largely due to the fact that most things can be made untraceable by exploiting the loopholes present on the internet as it exists.

Solution for the problems of the current Internet is described in a simple use case below:

I make about 10 searches during my day using the Google search engine. The first page of my search typically starts with a sponsored search result followed by a supposedly random, but highly customized set of results. This sponsored result and following search results are again based on the personalization Google has done for me using my historical data that it has captured and made a profile for me. Once personalization is done, they prioritize their advertisers to appear first in terms of the same keywords I have searched. In place of random, I get carefully curated results by Google based on who have associated with them in terms of their commercial association of advertising. In fact, more than half of the pages I get in my Google search results are based on that. I would have liked to have a much-focused keyword search. Why does Google do it? They offer search services for free, and they do spend a large amount of money to create, maintain, and enhance their search services. They need a revenue source and in the current form, it is advertising.

Considering the metanet world alternative, Google now charges me 0.001 cents for a search. Now Google has a revenue source in me using the search. If 10 billion searches happen a day, that itself gives Google revenue of 0.5 million USD. Apart from that Google can put ads separately for providing users to view ads and make money. These are representative numbers to show a new way of doing business where most probably Google will end up making more money by providing a paid search than the current model. Not just that, it will win back old loyal customers who are moving away due to privacy concerns from Google.

This is what Metanet proposes to solve.

# [Metanet protocol](#toc.xhtml#s133a)

Before we get into details, let us revisit some computer science concepts which are used in the metanet protocol.

# [Graphs](#toc.xhtml#s134a)

In computer science, Graph data structures are collections of things and the connections or relationships between them. The data or object in a graph are called nodes or vertices and the connections between the nodes are called edges. One example of a graph is a social network, where nodes are the people/individuals, and edges will be whether they are friends with each other.

Graphs are further classified into two types, Directed and Undirected. Both types are shown in the below picture:

![](images/Figure-7.1.jpg)

**Figure 7.1:** Nodes A, B, and C along with Edges shown for both directed and undirected graph

Undirected graphs are structures without any directions in the edges between nodes, while directed graphs are structures that have a specific direction in its edges.

Graphs are used to model and represent various objects and their relationships with each other in terms of representing real-life scenarios as a data structure. Representing things in these structures allows the use of algorithms to perform various operations like search quite comfortably using standard methods.

Some of the properties of Graphs are described below and also shown in the diagram below:

![](images/Figure-7.2.jpg)

**Figure 7.2:** Nodes A, B, and C along with Edges shown for both directed and undirected graph

In the above diagram, we have the following:

*   **Weighted Graphs:** edges can be assigned different weights or costs assigning differences in terms of traversing these edges.
*   **Self-loop edge**: when both the endpoints of an edge are at the same node for e.g., a web page redirecting to itself presents this property
*   **Multiedge graphs:** where there are multiple or parallel edges between the same nodes, for e.g., multiple flights between two cities represented in this data structure
*   **Walk**: A sequence of nodes where each adjacent pair is connected by an edge.
*   **Closed Walk**: It starts and ends at the same node.
*   **Path (simple):** A walk where no nodes and hence no edges are repeated.
*   **Simple Cycle:** A path where no nodes are repeated except the start and end node.
*   **Acyclic Graph**: A Graph with which does not have a path that starts and ends on the same node. A binary tree will be an acyclic graph.

One final concept that we need to cover is the in-degree and out-degree for a node, which means the number of edges that go into and out of a node.

# [Directed Acyclic Graph (DAG)](#toc.xhtml#s135a)

When it comes to metanet we are more interested in Directed graphs where we have a specific relationship assigned in the connections along with a direction. A DAG is:

*   **D: Directed** - The edges always have a direction.
*   **A: Acyclic -** The Graph will not have any cycles while traversing the path.
*   **G: Graph** - Needless to say, have nodes and edges.

With that being said, DAGs are quite common structures when it comes to representing nature, like for example, a family tree representation will be a DAG. The Bitcoin blockchain is a DAG.

# [BitCoin DAGs](#toc.xhtml#s136a)

Now that we have covered the base concepts, let us come to how all that applies to Bitcoin blockchain. There are different data structures in Bitcoin that are DAGs and let us look at two obvious ones.

# [Block DAG](#toc.xhtml#s137a)

The bitcoin blockchain as we have defined it is a chain of digital signatures linking blocks of data that have a set direction which is one way (previous to current) and is one dimensional, i.e. acyclic satisfying all of the properties we have discussed regarding DAG. (see *[Figure 1.5](#c01.xhtml#fig1_5)).* Each of the blocks forms a node and the cryptographic hash of the previous block represents the edge.

# [Transaction DAG](#toc.xhtml#s138a)

We have seen that the transactions in the block are again stored and indexed via their hash using a Merkle tree. Apart from that, the other relationship that exists in transactions is their connection towards other transactions in the same or different blocks via the UTXOs that they spend. This forms a very different and more complex graph structure when compared with block DAG which was quite similar to a linked list or a linear graph structure.

The following figure shows a sample transaction DAG. Needless to say, in a real blockchain, a transaction DAG can become quite complex with 100s of transactions that form various nodes and their previous transaction output to input relationship via the UTXO that they spend forming the edges. In addition to this, and also as you can see in the figure, there is no limit to the in-degree and out-degree for a node:

![](images/Figure-7.3.jpg)

**Figure 7.3:** Transaction DAG showing various transactions in time spending UTXO from the previous tx

You can see in the below figure a real transaction graph created using a visualizer present at the website: **[https://www.bitgraph.network/](https://www.bitgraph.network/)** for a transaction

`#tx/01b17c892e57bf4fba3b3cbe4a766201586ea5a221e2ec18aeb16e9e8b20505e`

![](images/Figure-7.4.jpg)

**Figure 7.4:** Transaction DAG in real blockchain

These visualizations of Bitcoin transfers from one address to others and overall flow of coins from source to destination is quite handy and useful when doing a transaction analysis, analytics, and traceability analysis for specific transactions and addresses.

# [Metanet DAG](#toc.xhtml#s139a)

Similar to transaction DAG which uses a set of rules to represent transaction data in a DAG form, Metanet is another protocol which uses certain attributes (which are needed to be added in transactions to become part of metanet protocol) to define another type of DAG which is being called as Metanet Graph. The choice of using a DAG for metanet graph structure was due to the structural similarity to the underlying DAG of transactions apart from other features of it being ideal to use for storing internet application data which we will discuss later in the chapter.

Metanet protocol specifies requirements for defining how a metanet transaction is to be built. Building a transaction in such a way will enable you to create a data structure local for your application and can be thought of as a layer 2 protocol that sits on the top of blockchain and can be used to store data immutably. It also allows easy access to it in terms of searching and comes with a completely inbuilt security model using the public key infrastructure. Further on we will talk about the specifications of the Metanet transaction protocol and its various features.

To summarize, the aim of metanet transaction protocol to be defined as DAG is:

*   Associate content in various transactions with correct relationships using edges.
*   Allow easy searchability for the metanet content (fast and reliable).
*   Build a blockchain analogous structure for servers to enable Client - Blockchain as a server model of applications.

# [Nodes and edges](#toc.xhtml#s140a)

The nodes are transactions that follow the metanet ruleset. A node transaction will be used to store content and that is done using the OP code which has been spoken about earlier called `OP_RETURN`. The data/content present in the transaction to qualify for metanet rules should have:

*   **Metanet flag:** A 4-byte identifier prefix to be used in every Metanet transaction.
*   **Attributes:** Relevant metadata for the content data like indexing, permissions, and encoding information.
*   **Content:** The payload data of interest. This data could be a web page, link URL, raw byte stream, or a file, basically any data that needs to be stored.

`OP_RETURN` opcode, which is used to push arbitrary data on a blockchain is used for the implementation of these protocol level details of metanet. What this means is that every metanet compatible transaction will have in its output script, `OP_RETURN` code, followed with the data that is to be pushed to the blockchain in that transaction. In this data, is where we add specific metanet protocol identifiers enabling the identification of that transaction as a metanet node.

In terms of a node, they can be defined as a parent or child and that depends on the direction of the edge, for example, let us take node A and node B. Typically the direction of the edge will be going from one node to another if it goes from A to B, or A —> B then A is the parent node and B is the child node. With that understanding, we define the nodes and edges.

**Node:** A transaction associated with the metanet protocol

Each node contains a public key, *P[node]* and an `OP_RETURN` followed by a metanet flag. A metanet node is referred to using this public key and the transaction ID.

*ID[node]:= (P[node]||TxID[node])* of a Metanet node.

**Edge:** An association of a child with a parent node using Signatures. Edges do not involve direct spending.

An edge is created using the signature *sig P[parent]* in the input of a Metanet transaction, implying that only a parent can give permission to create an edge. All nodes may have at most one parent, and a parent node may have an arbitrary number of children. This effectively means that the in-degree for a metanet node will at most be 1 and there can be an arbitrary number in terms of out-degree.

In effect a typical Metanet transaction or Node is structured as below mentioned format:

*TxID[node] :* \[ Inputs, Outputs \], Where

 
| **Inputs** || **Outputs** |
| --- | --- |
| *< <Sig P[parent]\> <P[parent]\>* || OP\_RETURN <Metanet Flag> *<P[node]\> <TxID[parent]\>* |

**Table 7.1:** A metanet node inputs and outputs

Where:

*TxID[node]* : Transaction ID for the node

*Sig P[parent]* : A signature created by the parent node

*P[parent]* : Address defining the parent node

Metanet Flag : A protocol value, `META` as a flag to mark that it is a metanet transaction

*P[node]* : Address defining the node

*TxID[parent]* : transaction id of the parent of that node

Please note due to protocol changes, `OP_RETURN` now is used always as `OP_FALSE OP_RETURN` in actual code. But for simplicity's sake, we will use `OP_RETURN` to refer to this. The reasons will be explained when we talk about `OP_RETURN` in detail in a later chapter.

One attribute that will be unique to the root or the first transaction of a metanet graph will be that the *TxID[parent]* will be null for this node. Please note that there will always be exactly one parent node for each child node.

When it comes to Edges, it is defined in this context as it is created from parent to child node by signing the child node by using the parent's key pair (Sig P and P of the parent as defined in *[Table 7.1](#c07.xhtml#tab7_1)*).

One critical point here to notice is, the metanet edge does not require spending of transactions. Since the information is present in the `OP_RETURN` data (output in OP-RETURN data is un-spendable always which is why it is used to store data) in terms of the Public Address which belongs to the child node. This means that it is possible to have a metanet output having a public key in one transaction and a Bitcoin spending transaction which created the UTXO associated with that public key separately. This is shown in *[Figure 7.5](#c07.xhtml#fig7_5)* where the same parent node key is also associated with another transaction which spends the UTXO:

![](images/Figure-7.5.jpg)

**Figure 7.5:** Metanet Edge between two transactions

If we summarize what we have learned about metanet protocol up till now, Metanet:

*   Specifies how to create by structuring a metanet transaction with nodes and edges
*   Write permission is controlled by digital signatures (functions as WORM media, Write Once, Read Many)
*   Read Permission controlled by encrypted keys
*   Highly customizable and generic protocol to support all kinds of applications.
*   Usable and compatible with alternate protocols like B://C://, AMP, AIP, Bit://, etc. We will discuss these protocols later in the book.

# [Names and domains](#toc.xhtml#s141a)

Structuring transactions in this way achieves the following in terms of permissions and ownership of nodes/data associated with nodes:

1.  Permissions and user authentication are now built-in as only parent node owners can create child nodes.
2.  This enables a cascading hierarchy of permissions on each layer of the nodes allowing.

*[Figure 7.6](#c07.xhtml#fig7_6)* demonstrates the metanet graph for a set of nodes and its hierarchy along with the permissions that each parent node has to create child nodes. Each of these nodes will have their unique IDs which can help locate them to find out which version (permission) by the public key we are using for the node. One key thing to notice is that in the naming convention of the node identifier we spoke earlier about, we get a clarity always about the version (who has created the node and the public key of the node both as shown below for TxID0, TxID1, and TxID1,1 from *[Figure 7.6](#c07.xhtml#fig7_6):*

*ID0 = Hash of ( P0 || TxID0 )*

*ID1 = Hash of ( P1 || TxID1 )*

*ID1,1 = Hash of ( P1,1 || TxID1,1 )*

The domain of each owner is shown by dotted lines in the below figure:

![](images/Figure-7.6.jpg)

**Figure 7.6:** Metanet graph and domains demonstrating separation of ownership of node data

In *[Figure 7.6](#c07.xhtml#fig7_6)* we have discussed how the creation of child nodes and further sub-child nodes are structured in terms of the domain. A domain defines what keys are needed to write and read operations on this graph.

The word Domain is used intentionally here, as it resembles the domain structure of the current internet pages and subpages for a website. With metanet suppose if the above *[Figure 7.6](#c07.xhtml#fig7_6)* represents an information website which is controlled by 3 different offices, the Prime Minister, the Home Minister, and Finance minister. Domain P0 will then be the PM office and all press releases from it can be displayed as a child node for each instance, like P3, P4, P5, and so on. Domain P1 belonging to home ministry will have separate access and permission for that domain, requiring its own set of keys to create new press releases for home ministry. The same is true for P2 which is a finance ministry that has its subdomain and controls its resources. This structuring establishes inbuilt access, permission, and encryption infrastructure which can help create a completely secure and private website.

The central point here is about mapping the real-world identities to metanet graphs so that the graph's inherent hierarchical relationship structure can be used for mimicking real business cases.

Once we have identities assigned to the metanet graph, then we can create a custom URL like resource locator path for each of the nodes in the metanet graph. In the above example, if the home ministry issued a new press release, that being the creation of node P1,2 they can provide a URL equivalent of the metanet, MURL link to the node P1,2. Below is how the naming convention will look like:

`P1,2 := [mnp://RootDomain/path/file…]`

In the example it will be: mnp:`//PMOffice/HomeMinisry/PressRelease2`

Where,

`mnp` - Protocol Identifier for metanet protocol

`RootDomain` - a domain which has been mapped to a real-world identity

`Path` - the hierarchy of subdomains under which the file lies.

`File` - the name of the target node

Below *[Figure 7.7](#c07.xhtml#fig7_7)* shows a representation of the example and its corresponding `url` and `murl`:

![](images/Figure-7.7.jpg)

**Figure 7.7:** structuring a domain with hierarchical data ownership in metanet

This structuring allows for easy access and searchability for the resource allowing inherently efficient traversing in DAG structures.

The use cases of this are many. Imagine social media, where the *P1* is a user, and all of the data he creates as child nodes and edges all fall under his ownership as he owns the key *P1*. This can deterministically solve the privacy issue that general social media companies face from time to time.

# [Searching Metanet](#toc.xhtml#s142a)

Searching the Metanet is just like searching a hierarchical database. The search key can be constructed based on the parent and the path. Typical MongoDB finds like a query can be made as shown below.

Node attributes:

`{`

`index: 𝐻(𝑃𝑛𝑜𝑑𝑒||𝑇𝑥𝐼𝐷𝑛𝑜𝑑𝑒);`

`index of parent: 𝐻(𝑃𝑝𝑎𝑟𝑒𝑛𝑡||𝑇𝑥𝐼𝐷𝑝𝑎𝑟𝑒𝑛𝑡); (NULL if orphan)`

`name: 'domain name';`

`kwd1: 'keyword1';`

`kwd2: 'keyword2';`

`⋮`

`}`

In the above example, this query for finding the press release 2 will have the following syntax:

`News release 2 is a Sub-department page node P1,2,`

`MURL: mnp://PMOffice/HomeMinisry/PressRelease2`

`{`

`index: 𝐻(𝑃1,2||𝑇𝑥𝐼𝐷1,2);`

`index of parent: 𝐻(𝑃1||𝑇𝑥𝐼𝐷1);`

`name: 'PressRelease2';`

`kwd1: 'India';`

`kwd2: 'Government';`

`⋮`

`}`

# [Data insertion](#toc.xhtml#s143a)

Metanet writing of new nodes is already described earlier, and to add a new node, a transaction can be done which stores the required content in the `OP_RETURN` payload or using another method to upload data which is done via `[Data][OP_DROP]` syntax in the script. You can add data to a transaction using `OP_Pushdata` and when executing the script use `OP_DROP` which drops the top item on the stack so that the script key verification continues correctly. So you can use one or the other, and both in conjunction to do metanet transactions.

The format is shown in the below table for both of these types of transaction:

 
| *TxID[node]* |
| **Inputs** || **Outputs** |
| <Sig P[\_parent]\> <P[parent]\> || OP\_RETURN <Metanetflag><P[node]\><TxID[parent]\>         <file name><file type>         <file data> |

**Table 7.2:** Metanet transaction for creating a node with a file: "filename" and with data "file data"

A similar transaction using both `OP_RETURN` and `OP_DROP` will be in the below format which uses both in conjunction:

 
| *TxID[node]* |
| Inputs || Outputs |
| < Sig P[parent]\> <P[parent]\> || OP\_RETURN <Metanetflag><P[node]\><TxID[parent]\>         <sub-protocol identifier>         <file name><file type>         <recombination scheme> |
|  ||       <file\_data 1> OP\_DROP |
|  ||       <file\_data 2> OP\_DROP |

**Table 7.3:** Metanet transaction using OP\_DROP opcode and OP\_RETURN together

Typically the general attributes like metadata of the file are stored in the `OP_RETURN` and the actual file split into two in the above table, `file_data1` and `file_data2` are stored using `OP_PUSHDATA` opcode and written in the script using `OP_DROP` (so that the file data is dropped from getting processed in the stack).

One aspect that is not detailed out is the idea of Metanet protocol supporting sub-protocols as well. So if another protocol (take the example of B:// protocol, which we will discuss in a later chapter) is used in the transaction, metanet protocol can be used as the parent protocol and B:// protocol can be used as a sub-protocol for the same transaction. This flexibility of metanet protocol allows it to be used in conjunction with any other defined or undefined protocol as well.

This property of metanet protocol is called protocol locality.

# [Final thoughts](#toc.xhtml#s144a)

Here the table below shows a summary of an analogy of how the data looks for the internet and how it looks for metanet:

 
| **Internet** || **Metanet** |
| --- | --- |
| Website || Node |
| Owner || Public Key, Pnode |
| IP Address (non-unique) || Node Index IDnode = H(Pnode||TxIDnode |
| Domain Structure || Node Tree structure |
| DNS or Domain Name system || Map from root node name to node index |
| URL || MURL |

**Table 7.4:** Analogy and comparison of various attributes of the internet with metanet

As you can see above, the complete structure of the internet can be replicated with additional advantageous features when built using metanet.

Details of the Metanet protocol with an excellent blog by the creators of the protocol are mentioned in the links provided below:

*   **Metanet Protocol documentation:**
    
    **[https://nchain.com/app/uploads/2019/06/The-Metanet-Technical-Summary-v1.0.pdf](https://nchain.com/app/uploads/2019/06/The-Metanet-Technical-Summary-v1.0.pdf)**
    
*   **Metanet Edge Cases:** Blog on metanet protocol along with various examples: 
    
    **[https://medium.com/@jack.d](https://medium.com/@jack.d)**
    
*   **The Metanet Starts:** Blog by Unwriter: 
    
    **[https://medium.com/@\_unwriter/the-metanet-starts-84f255a65782](https://medium.com/@_unwriter/the-metanet-starts-84f255a65782)**
    

# [Conclusion](#toc.xhtml#s145a)

Metanet is a new approach to build the internet and web-based content. This chapter has covered basic protocol and conceptual level details of the metanet and how the base layer protocol looks for building an internet where every piece of data created has explicit ownership and rights present for the creator and any usage needs to be authorized, and on the flip side, any misinformation or misdirection kind of data created will be having an identity assigned. Both scenarios are something very different from the current internet and how it operates where there is no accountability of a person or a business which has caused a lot of issues in terms of the social fabric of the world. The other big aspect of monetization is resolved using metanet type structures, similar to the solution of metering of electricity, now data can be metered as well using this protocol.

In the next chapter, we will start looking at another set of protocols that are used in conjunction with metanet protocol for specific domain registration information logging for application development on Bitcoin blockchain.

# [Questions](#toc.xhtml#s146a)

1.  What is a node and what is an edge in metanet DAG? Are they the same?
2.  How do you store data in a node?
3.  What are the various analogous components of the internet and Metanet when registering a website?
4.  Why is the distribution of ownership to parent and child in metanet providing separation of data ownership?

# [CHAPTER 8](#toc.xhtml#c08)

# [Bitcom and Other Application Protocols](#toc.xhtml#c08)

**"The Internet will become a sidechain of bitcoin (using metanet)"**

*\- Dr. Craig S Wright, creator of Metanet protocol.*

To build applications on Bitcoin, it will be nice if they have to have a unique identifier that they can use to separate their data from all other applications that use the same Bitcoin blockchain as well. This created a need for some open agreement infrastructure where again, we can use Bitcoin to publish it in an immutable way, so everyone knows who is using which key to identify their transaction data. This is what was the next step to use Bitcoin, and metanet is one such example we saw of doing this application registration on the blockchain. When metanet is a more generic protocol, something more specific was needed (if you consider the vision of the entire internet restructured into metanet protocol DAGs, it is as generic as TCP or IP protocol for current internet). That is where Bitcom and a few other attempts were made by various open-source developers and that is what we will be discussing in this chapter.

# [Structure](#toc.xhtml#s147a)

*   Using Bitcoin address as a prefix
*   Decentralized registry
*   Bit, AIP, MAP, BCAT, B, C, and D protocol
*   Using Unix pipeline with protocols
*   Bottle browser

# [Objective](#toc.xhtml#s148a)

After studying this chapter you will be able to understand how to register your application and use Bitcom, B://, MAP, and a few other protocols related to OP\_RETURN for storing data/files on the blockchain. In a way, this is the write operation method in terms of thinking of blockchain as data storage and think of CRUD operations. You will also understand the need for these protocol(s) and how to use them.

# [Bitcom: BitCoin Computer](#toc.xhtml#s149a)

With an explosion of application development, many felt the need for unique identifiers for the transactions that these applications are creating, so that they have an easy to search and index method for their transactions and application-specific usage. It is something that was already being done in the past with things like Memo protocol for an early version of social media. Bitcom is one such protocol that is a protocol to be used by any application or a protocol to identify its transactions.

Bitcom was a clever way to use cryptography in Bitcoin. This is the real benefit of a highly generic system like Bitcoin. `OP_RETURN` transactions have historically been used to add arbitrary data and there were attempts made to come up with a common naming system like memo protocol (memo is an IM like chat messaging protocol). This was used with identifying their messages by using a prefix (hex value 0x6dXX, where XX = 1,2,3,…so on) to all of the memo protocol related transactions.

Bitcom was a formal and generic approach of finding and assigning this prefix which applications can use for their transaction data but also can claim it in a central open registry. This is exactly what Bitcom does. It provides a unique and random way to generate application prefixes and is open code for anyone to use.

Quoting \_unwriter, who created this protocol:

*"Bitcom is an open-ended OP\_RETURN protocol for creating a universal virtual computer on top of Bitcoin.*

*Bitcom is an open-ended OP\_RETURN protocol for creating a universal virtual computer on top of Bitcoin. Bitcom borrows from the UNIX file system metaphor to represent a global directory of Bitcoin application protocols, where:*

*   *Each "account" is represented as a root folder with a Bitcoin address as the name*
*   *Each "account" is an application protocol controlled by the private key holder of the address.*

*Thanks to the simplicity of the protocol, you can generate these transactions yourself easily."*

Bitcom is an open convention that can be used to build application protocols by yourself and publish it for claiming that namespace, and being sure that no one else will have a conflicting namespace generated as it uses Bitcoin address as a namespace identity. It comes with the benefit of NEVER having to worry about namespace problems in the future.

This explosion of utility happened with Bitcoin SV's Block 566476, until then `OP_RETURN` transactions have been limited to around 220bytes making it not possible to store any meaningful data on the chain using it. This limit was changed to 100kb per `OP_RETURN` transaction creating an explosion of use cases. With this approach, the prefix itself can be used for putting all kinds of things on the blockchain, from text to image to a website to audio, providing a permissionless, decentralized, collision-free, ownerless way of storing data.

# [Bitcoin address as prefix:](#toc.xhtml#s150a)

Instead of using a predefined prefix value, Bitcom provides a function to generate a new Bitcoin address which becomes the protocol prefix. This way there is no namespace collision possible. It is available to install using an NPM package:

![](images/p187.jpg)

Once the above transaction is confirmed on the Bitcoin blockchain, you have reserved a namespace in the Bitcoin blockchain. Detailed instruction set and steps to use Bitcom to register and build an application are present in the link: **[https://bitcom.planaria.network/](https://bitcom.planaria.network/)** from its author.

The Biggest benefit of using a protocol like Bitcom is that it is compatible to use with any other protocol so if you want to build a file transfer app, you can register using Bitcom protocol for the app and then use another protocol like B:// for file transfer. Before we demo that use case, let us look at a few other attempts for various protocols by various open-source developers.

# [What can you do with Bitcom?](#toc.xhtml#s151a)

Apart from the main use case of providing a decentralized open registry for Bitcoin applications, which is scalable, reliable, and available 24/7 is a good start towards building sustainable large scale applications. Just using this registration property applications will get the following additional benefits to use Bitcom.

Decentralized registry(using Bitquerry): Easy search method to query Bitcoin blockchain in a MongoDB like syntax. This will be discussed in detail in the next chapter. A typical bitquery is shown in the below figure:

![](images/Figure-8.1.jpg)

**Figure 8.1:** discovering application owner via a Bitcoin address using bitquery language

# Decentralized router over Bitcoin:

Basically you can create a local protocol to run your application using a framework ( Bit and C framework) with Bitcom registration on Bitcoin making your application This will be discussed in detail when we talk later about a bit and C protocol. The detailed specs of building a router are provided by unwriter at the main documentation page: **[https://bitcom.bitdb.network/#/](https://bitcom.bitdb.network/#/)**

# [B:// protocol](#toc.xhtml#s152a)

B protocol or in detail, Bitcoin data protocol is an approach and tool to easily store and reference data on the Bitcoin blockchain.

Quoting unwriter, who created this protocol:

*"B is an OP\_RETURN protocol to store and reference arbitrary data on Bitcoin. The design goal:*

*   *The simplest protocol to upload arbitrary media to the blockchain*
*   *A protocol to reference previously uploaded media from another on-chain media."*

The prefix for B is `19HxigV4QyBv3tHpQVcUEQyq1pzZVdoAut`, generated using Bitcom. The method to write the data on blockchain is using the `OP_RETURN` code in the script and then followed by a schema for making it B:// compatible:

![](images/p188.jpg)

Once you make a transaction to for example upload an image to blockchain using B, you can reference it back using a URL kind of reference text provided by their transaction ID. For example, an image which is uploaded on Bitcoin blockchain using B protocol and the process is shown below:

![](images/Figure-8.2.jpg)

**Figure 8.2:** Whatsonchain used to view the above image that was uploaded using B protocol. This image was uploaded using **[https://b.bitdb.network/](https://b.bitdb.network/)**

To refer this image just like URL, you can use the following formats:

1.  As transaction ID - `b://[txid]`
2.  Using in HTML code: 
    
    `<html>`
    
    `<body>`
    
    `<img src='b://9c675af043f9442e23489506dd3a5e7e20fd88cced94ef10036bf 0d24d065f 3'>`
    
    `</body>`
    
    `</html>`
    
3.  A markdown image: 
    
    `![image](b://9c675af043f9442e2348 9506dd3a5e7e20fd88cced94ef10036bf0d24d0a65f3)`
    

One other way to reference, which was developed along with B is the C protocol which we will be going into details as the next topic.

# [C:// protocol](#toc.xhtml#s153a)

With the simple B protocol, we can *write* any type of data blob which is static to the blockchain. C protocol is to create a unique uniform resource locator or URL notation for the content stored in the blockchain using the B protocol hence providing a scheme to *read* data from the blockchain.

Why have C? It provides an immutable URI or Uniform resource identifier, by providing a method to create these URIs for data in the transactions on the blockchain. It is considering Bitcom being the computer, C being the file system for data stored on the computer.

How?

C:// generates filenames by SHA256-hashing the content uploaded through Bitcoin and creating the mentioned URI for the content stored. This will be a link that will exist immutably on blockchain for no further cost. This is the idea behind Bitcoin used here, economics. We have one global system which can store data with one time cost, offering an alternative to cloud storage with cost-efficiency.

This means there's exactly one universal filename per unique content. (known as Content Addressable Storage).

# Making links trustless:

If you are using native B protocol methods to access content, you still have to rely on a third party, like in our case, whatsonchain.com who is a service provider. With Bitcoin, that also is not needed since it is available for anyone to access openly. When we use C protocol links, hashing will create a unique URI defined by the actual content making the data integrity tied with the link URI itself. This means if you have a C protocol URI of the Bitcoin independence day picture we stored in the example, if anyone tries to change any part of the image, that will change the URI, and in turn making it impossible to change the content for anyone.

Everything is a file, even applications. This enables a large number of use cases for various business needs when you have a permanent way to store files on timestamped public storage privately. You can provide access to that resource via a URI for being used for many purposes. You can see what the public data here is on whatsonchain page for the transaction.

**[https://whatsonchain.com/tx/9c675af043f9442e23489506dd3a5e7e20fd88cced94ef10036bf0d24d0a65f3](https://whatsonchain.com/tx/9c675af043f9442e23489506dd3a5e7e20fd88cced94ef10036bf0d24d0a65f3)**

![](images/Figure-8.3.jpg)

**Figure 8.3:** A C protocol naming system steps

# Referencing from code:

Once the URI is generated, it can be referenced as a file from any code. Common references from HTML are shown below:

`<html>`

`<head>`

`<link href="c://9c675af043f9442e234 89506dd3a5e7e20fd88cced94ef10036bf0d24d0a65f3" rel="stylesheet">`

`<script src="c://9c675af043f9442e23489506dd3 a5e7e20fd88cced94ef10036bf0d24d0a65f3"></script>`

`</head>`

`<body>`

`<img src="c://9c675af043f9442e23489506dd3a5e 7e20fd88cced94ef10036bf0d24d0a65f3">`

`</body>`

`</html>`

Once you have an ability to store an image, document, or even application files on Bitcoin blockchain, which can be referenced from code to be used for application development, you can think of millions of business use cases for building frontends, static websites, and images or a personal album app where user data privacy never gets breached. This will certainly help in any small and medium-size business company to be for, ex, GDPR compliant, SOC Compliant, and much more.

All details and algorithm pseudo-code is present on the creator's website. Unwriter is a pseudonym used by inventor of Planaria Corp business entity who is the creator of the following protocols:

*   **[https://bitcom.bitdb.network/#/](https://bitcom.bitdb.network/#/)**
*   **[https://b.bitdb.network/](https://b.bitdb.network/)**
*   **[https://c.bitdb.network/](https://c.bitdb.network/)**
*   **[https://github.com/unwriter/B](https://github.com/unwriter/B)**

An implementation of a content search tool using C protocol can be found at **[https://c.planaria.network](https://c.planaria.network)** for the curious. This tool allows the user to search for any file on the Bitcoin blockchain and provides an easy interface to upload files to the blockchain.

# [D:// protocol](#toc.xhtml#s154a)

With the simple B protocol, we can upload any type of data blob which is static to the blockchain. With D protocol, we can do all of these things with an added option of using a payment channel. This payment channel is also referred to as nakamoto payment channel to differentiate it from the lightning network payment channels which are off-chain creating sub-ledger books. This payment channel is an on-chain payment channel, which is done using the field `nSequence` number.

**Schema:**

`OP_FALSE OP_RETURN`

`19iG3WTYSsbyos3uJ733yK4zEioi1FesNU`

`[key]`

`[value]`

`[type]`

`[sequence]`

`Usage:`

`OP_FALSE OP_RETURN`

`19iG3WTYSsbyos3uJ733yK4zEioi1FesNU`

`"bsvindependence.jpeg"`

`9c675af043f9442e23489506dd3a5e7e20fd88cced94ef10036bf0d24d0a65f3`

`tx`

`1`

In the above example, the same picture from C protocol, which is a picture of the celebration of BSV completing a year after the hash war that resulted in two separate protocols of bitcoin cash chain. If this image was uploaded using D protocol, you can create a URI which uses `nSequence` to open a payment channel for this transaction. So when you want to update it in the next year, it can be year 2 image and done simply by uploading a new image in Nov 2020 using d protocol to override the last transaction data.

It is dubbed as D protocol for the Dynamic content payment channel for any file nature of the protocol. Bitcoin dynamic content protocol enables utility when you are constructing an application where you want to do a version of files. In the mainframe world, most developers will have used something called the GDG versioning system. This is used heavily in storing daily financial data from their customers. Using D protocol you can build a dataset storage system for your storage needs. Imagine, a private, secure system to store your customer financial transaction data every day, with cost efficiency which will go to the thousandth of current levels.

More details and some usage scenarios are present on the creator's website:

**[https://github.com/bitcoineler/D](https://github.com/bitcoineler/D)**

# [BCAT protocol](#toc.xhtml#s155a)

Currently using the B protocol, in a single transaction there is an upper limit to the size of data 100kb) that can be stored with `OP_RETURN`. B Cat protocol signifies a concatenated version of B protocol where you can use this schema to store roughly about 270 MB of data.

`Schema:`

`OP_FALSE OP_RETURN`

`15DHFxWZJT58f9nhyGnsRBqrgwK4W6h4Up`

`[info]`

`[media type]`

`[charset]`

`[name]`

`[flag]`

`[txid part 1]`

`[txid part 2]`

`…`

`[txid part n]`

B Cat protocol overcomes the limit by splitting the data (which is of size more than 100kb) into chunks of 100kb slices, stored via an individual transaction in the blockchain. Each of the transactions mentioned in the above schema will be in turn using the B protocol format.

More details and some usage scenarios are present on the creator's website: **[http://bcat.bico.media/](http://bcat.bico.media/)**

# [AIP protocol](#toc.xhtml#s156a)

**Author identity protocol (AIP)** allows for users to sign arbitrary `OP_RETURN` data in a single transaction. This means that a user can add signing details to transaction data to claim their ownership.

This unique way also allows for multiple signatures to use it for agreements and contracts.

Schema:

`OP_RETURN`

`19HxigV4QyBv3tHpQVcUEQyq1pzZVdoAut`

`[Data]`

`[Media Type]`

`[Encoding]`

`[Filename]`

`|`

`15PciHG22SNLQJXMoSUaWVi7WSqc7hCfva`

`[Signing Algorithm]`

`[Signing Address]`

`[Signature]`

`[Field Index 0] // Optional. 0 based index means the OP_RETURN (0x6a) is signed itself`

`[Field Index 1] // Optional.`

`… // If the Field Indexes are omitted, then it's assumed that all fields to the left of the AUTHOR_IDENTITY prefix are signed.`

More details and some usage scenarios are present on the creator's website:

**[https://github.com/BitcoinFiles/AUTHOR\_IDENTITY\_PROTOCOL](https://github.com/BitcoinFiles/AUTHOR_IDENTITY_PROTOCOL)**

# [MAP protocol](#toc.xhtml#s157a)

**Magic Attribute Protocol (MAP)** is used, most times in conjunction with B and AIP protocol to chain or associate or create a relationship between chunks of data stored in a single transaction. Each chunk can potentially have its owner. MAP does this by assigning key-value pairs to data.

Schema:

`<OP_RETURN | <input>>`

`MAP`

`<SET | DELETE>`

`<key>`

`<value>`

Suppose if you want to associate a geolocation to a photograph to prove the location and time of the photograph being authentic, this can be done using MAP protocol. It can also be used to store chat data or replies to a comment by chaining the data together. The input stream flows from the left and can be piped like Unix commands. It is possible to chain content from B protocol and map it to some global identifier (`txhash, url, etc.)`, and finally sign that using the Author Identity protocol.

An example is shown below. Please notice hos multiple protocols are being used together by using pipe "|" like done in Unix command:

`OP_RETURN`

`19HxigV4QyBv3tHpQVcUEQyq1pzZVdoAut (B)`

`"## Hello small world"`

`text/markdown`

`utf8`

`|`

`1PuQa7K62MiKCtssSLKy1kh56WWU7MtUR5 (MAP)`

`'SET'`

`'url'`

`'https://map.sv'`

`|`

`15PciHG22SNLQJXMoSUaWVi7WSqc7hCfva (AUTHOR_IDENTITY)`

`'BITCOIN_ECDSA'`

`<pubkey>`

`<signature>`

More details and some usage scenarios are present on the creator's website:

**[https://github.com/rohenaz/MAP](https://github.com/rohenaz/MAP)**

# [BAP protocol](#toc.xhtml#s158a)

Inspired by AIP, BAP, or Bitcoin Attestation protocol provides a more generic attestation of data, without the need of publishing the data itself.

**Schema:**

`1BAPSuaPnfGnSBM3GLV9yhxUdYe4vGbdMT`

`[ID|ATTEST|REVOKE]`

`[URN Attestation Hash]`

`[Sequence|Address]`

`|`

`[AIP protocol address]`

`[AIP Signing Algorithm]`

`[AIP Signing Address]`

`[AIP Signature]`

BAP protocol allows for linking a unique identity (keypair) to a specific Bitcoin signing address. Identity keys could be any random hex string but at least 64 characters (256 bit). This protocol can be used for many real-life use cases like creating a BAP identity system, creating the power of attorney, etc.

More details and some usage scenarios are present on the creator's website: **[https://github.com/icellan/bap](https://github.com/icellan/bap)**

# [Unix pipeline between protocol](#toc.xhtml#s159a)

We have discussed many protocols by now. These are quite strong and useful in their utilities, but they show the powerful nature when used in conjunction with each other.

The UNIX pipeline allows the interoperability between these protocols. This is done using the Unix pipeline character "|" to add multiple protocols together. The protocol allows for passing message information from one protocol to another.

**Schema:**

`OP_FALSE OP_RETURN`

`[Bitcom Protocol 1]`

`|`

`[Bitcom Protocol 2]`

`|`

`[Bitcom Protocol 3]`

`|`

`…`

The point being these protocols can be mixed and matched as you would like to use them based on the specific application requirement. This is also similar to how we discussed that metanet can be a generic protocol and we can use any one of these above-mentioned protocols in conjunction with metanet protocol.

**D piped into B**

Below is an example of d protocol for versioning data and b protocol for storing data, we create a schema for uploading explicitly versioned data to the blockchain like GDG as we discussed earlier as well:

`OP_FALSE OP_RETURN`

`19HxigV4QyBv3tHpQVcUEQyq1pzZVdoAut`

`[DATA]`

`[MEDIA TYPE]`

`[ENCODING] or NULL`

`[FILENAME] or NULL`

`|`

`19iG3WTYSsbyos3uJ733yK4zEioi1FesNU`

`[key]`

`NULL`

`b`

`[sequence]`

More details for the protocol is present at the creator's website:

**[https://github.com/unwriter/Bitcom/issues/2](https://github.com/unwriter/Bitcom/issues/2)**

# [Bottle - A Bitcoin browser](#toc.xhtml#s160a)

We have looked at the URI schemes which create a Bitcoin-based content URL like identifier (B:// or C://). This enables a different kind of opportunity to access the content stored on the blockchain, where everything is stored as a data blob and can be accessed as a file using the URI. If you think about it, everything is a file when it comes to software applications. It could be static content like document, audio, video, images, and such, or it could be codebase files. Everything can be thought of as a file, and if there is a file, it can be stored on the blockchain, and if it's stored on the blockchain, it can be accessed using the URI schemes that exist now or might be developed in future.

It is the next logical step to have a browser for this content which is different from the traditional browser which is made specifically for HTTP/HTTPS traffic. This is what Bottle is.

The bottle is the first Bitcoin native browser which not just supports the static content like images, but also hypermedia files and it does it using Bitcoin native protocols.

You can build your HTML page without using any HTTP and serving things like CSS, Images, videos, and even JavaScript files using URI links of the content stored on Bitcoin blockchain:

![](images/Figure-8.4.jpg)

**Figure 8.4:** Bottle browser plugging into a B:\\\\ endpoint node to display a URI. Image Source: [https://bottle.bitdb.network](https://bottle.bitdb.network)

Bottle in backend uses Bitquery kind of syntax to query Bitcoin blockchain using the URIs generated by the B:// or C:// protocol to a backend that can be built using planaria, or any other method, which then is served on the browser interface for the user. You can simply write the URI with the protocol identifier on the browser to access the content. It is powered by Electron (**[https://electronjs.org](https://electronjs.org))** which makes it have all the usual browser features but in addition to it, it can browse Bitcoin blockchain.

You can read more about it at **[https://github.com/interplanaria/bottle](https://github.com/interplanaria/bottle)**

# [Bit protocol](#toc.xhtml#s161a)

Bit protocol is defined as a protocol of protocol. It is kind of fitting to discuss this, in the end, to bring closure to the first step we took using Bitcom to define a decentralized protocol registry, It does not define a way on how the protocols are referenced and processed amongst interlinked Bitcoin-native documents and applications.

Bit Proposes to solve this issue. It closes the loop on the manual attention and intervention required if we just keep using the earlier seen protocol by their registration keys. In the traditional web, we have IANA (**[https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xml](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xml)**) which does the centralized monitoring, registration, and monitoring of namespace collisions. Bit is a similar system that does remove the need for monitoring and any namespace collision possibilities.

What I mean by namespace collision is, what if I take B protocol registration id, which is `19HxigV4QyBv3tHpQVcUEQyq1pzZVdoAut` and start using it for my application which is a social media chat application. How do we make sure that these prefixes are being used for what they are intended to be used for? This is done by Bit protocol.

Bit Protocol solves this problem by solving the following 3 parts:

*   **Generic URI scheme:** A new URI scheme that can custom-reference any application protocol object on the Bitcoin blockchain.
*   **Decentralized router:** A decentralized routing engine that maps the generic URI scheme to real-world service providers who implement each protocol, using Bitcom.
*   **Authentication:** A two-way mechanism to connect service endpoints to the router with provable ownership and affiliation, using Bitcoin Sticker protocol.

**Schema**:

`bit://[B: Bitcom Address]/[Transaction ID]`

`//(the scheme, bit, the authority : bitcom address and the path to resource, the transaction id.`

So the file from our example from b protocol image, the bit URI for that image will be:

`bit://19HxigV4QyBv3tHpQVcUEQyq1pzZVdoAut/b://9c675af043f9442e23489506dd3a5e7e20fd88cced94ef10036bf0d24d0a65f3`

This scheme is flexible (you can make multiple level path as well below scheme:

`bit://[B Bitcom Address]/file/[txid]`

Automated routing (this is the reason why we do not need a manual step in terms of maintaining this centralized registry, when it is automated and needs no manual interruption, it becomes fully open and decentralized:

*   `bit://1PuQa7K62MiKCtssSLKy1kh56WWU7MtUR5/user/15PciHG22SN LQJXMoSUaWVi7WSqc7hCfva` 
    *   **Behavior**: route to service endpoints that return all MAP protocol usage from user `15PciHG22SNLQJXMoSUaWVi7WSqc7hCfva`
*   `bit://1PuQa7K62MiKCtssSLKy1kh56WWU7MtUR5/tx/bbdc98852 b99aaecef24925883c 960457932affc83972f128e0c2361a444aace` 
    *   **Behavior:** route to service endpoints that return the MAP portion of the transaction bbdc98852b99aaece f24925883c960457932affc83972f1 28e0c2361a444aace

More details and some usage scenarios are present on the creator's website:

**[https://bit.planaria.network/#/](https://bit.planaria.network/#/)**

# [Conclusion](#toc.xhtml#s162a)

We have seen a lot of protocols in this chapter. The reason behind that is Bitcoin is working as a native layer providing a method to do data storage and value exchange. These protocols that we discussed in this chapter are like system conventions that can be followed on top of Bitcoin protocol that works 100% of the time and will be always as they are open source and decentralized. These protocols enable the use of Bitcoin blockchain as an alternative to cloud storage for most possible use cases that currently exists for a very low fee. Security and auditability provides a stable single source of verifiable information.

We have looked at a bunch of protocols by now with metanet being the overall most generic protocol which not only supports its graphs, but it allows for using multiple protocols in conjunction with each other providing all possible functionalities that are needed to be done using Bitcoin blockchain.

In the next chapter, we will look at how the data can be accessed in a much more organized way rather than what we have currently seen in terms of a lot of hexadecimal numbers. From now on we will start to provide more and more data structure models working with the protocols we discussed in this chapter to do write and read operations on the Bitcoin blockchain.

# [Questions](#toc.xhtml#s163a)

1.  Can you use metanet protocol and b protocol together, can a file uploaded using b protocol also be metanet valid?
2.  What is the purpose of a centralized registry system like Bitcom
3.  What is the difference between C and D protocol and what are payment channels?
4.  Why does referencing using bit protocol remove the need for a central authority maintaining namespace collision issues between protocol URI links?

# [CHAPTER 9](#toc.xhtml#c09)

# [Data Carrier Transactions: Bitcoin as Infinite Database](#toc.xhtml#c09)

**"A good idea is an idea that solves several things at the same time."**

*\- Linus Torvalds, creator of Linux.*

We have looked at various protocols in the last chapter to give you an idea of how we do basic operations using blockchain as a data store, in this chapter we will bring more formal structures to the data stored in the blockchain. This is done by defining a schema which we will use to read and write to the blockchain. We will create database structures, define and learn a query language, and will be focusing on the use cases for the tools we have learned till now. We will also be focusing on how these tools are being used to implement innovative and serverless Bitcoin applications where blockchain is being used to store application-specific data including but not limited to storing videos, audio, and any other files.

# [Structure](#toc.xhtml#s164a)

*   BitDB database structure on Bitcoin
*   BitQuery, Indexer, and Crawler
*   Euler, Babel, Chronos, Genesis, and the neonGenesis
*   Datapay, BitPipe, BitIndex, Bitsocket, and other utilities

# [Objective](#toc.xhtml#s165a)

After studying this chapter, you will be able to build a database schema for your application using blockchain as storage media, access, and search the data stored in the database, using Bitcoin blockchain as an API for accessing data and a SQL type query language for Bitcoin blockchain.

# [Data on Bitcoin](#toc.xhtml#s166a)

Bitcoin today is seen more about money, currency or payments. This is just one use case and ignoring the complete remaining design of Bitcoin. Bitcoin from the start allowed data in transactions. With Bitcoin, a new world for storing data was opened up and it was there from the start in Bitcoin by design. There are designated opcodes that are there to push data on the blockchain. Let us see what codes they are:

 
| **Name** || **Maximum data supported** || **Description** |
| --- | --- | --- |
| `OP_PUSHDATA1` || 255 Bytes || The next byte contains the number of bytes to be pushed onto the stack. |
| `OP_PUSHDATA2` || 65k || The next two bytes contain the number of bytes to be pushed onto the stack in little-endian order. |
| `OP_PUSHDATA4` || 4.3 GB || The next four bytes contain the number of bytes to be pushed onto the stack |

**Table 9.1:** Opcodes that allow data to be pushed and stored with a transaction in Bitcoin blockchain.

The obvious question that comes is if these opcodes are present, why can we not use it today? The answer lies in history again, if you remember, there were limitations added later on to Bitcoin, and there were two hard limitations:

1.  Standard transactions only. This made most of the opcodes present in the Bitcoin script dead including the above `PUSHDATA` opcodes.
2.  Soft limit on the `OP_RETURN`, miners allowed for a long period 223 bytes of data (40 and 83 bytes at different times as well). Even this was not allowed in the earlier stages as a standard script, but later in time when people started burning Bitcoins to store hash and text messages in place of the public key hash in the output script, it was made a standard script. A limit however was added to keep the size of data restricted which was raised to 100kb in 2018 when BSV came into being.

As you can see that a feature in a way, was made a bug and suppressed with the idea that Bitcoin blockchain is not meant to store arbitrary data, which was so not the case to anyone who has a look at the original design of script opcodes. Even when restricted users found novel ways to encode small size data and messages with things like using fake multisig public keys and use that byte store space to pass messages even at times at the cost of burning Bitcoin permanently due to the output script containing a fake public key. A study found back in 2017 that about 250 Bitcoins were burned to store about 9 MB of data since the start of the network. A standard Bitcoin transaction is limited in size to 100KB with each input script limited to 1650 bytes.

Once the script is executed, it must contain exactly one non-false element for a successful execution (remember, Bitcoin script being a predicate). Any single element being pushed to the stack is limited to 520 bytes. All of these limitations can be found in the `IsStandard()` function which was added to Bitcoin code later on after Satoshi left. This limit was removed after the genesis upgrade and that has opened up the blockchain to support large data uploads. There is currently a miner price point of 0.5 Satoshi per byte which is the current rate to upload the data on the blockchain. Miners already are looking at 0.25 Satoshi per byte for bulk transaction processing deals with customers. It is expected that these fees will go down a lot more significantly making storage cheaper as miners professionalize and become more of transaction processors looking for better business models.

Needless to say, that is why we will not go into details of various data insertion methods that were tried out to bypass `IsStandard()` function limits (One such method was the usage of `OP_RETUN` which became and still is a default method for adding protocol identifiers, files, etc. With the opening up of `PUSHDATA` Opcodes, which can enable storage of up to 4.3 GB data in a single transaction, make Bitcoin blockchain competition to traditional cloud services as well.

Looking more closely at the Bitcoin script data storage using `OP_RETURN` let us look at the details of how the Bitcoin script is executed. The Bitcoin script life cycle if we say, has two stages:

1.  Stage 1 is when it is created. When you do a transaction you spend your UTXO and provide a public key in the `ScriptPubKey` script or output or locking script in the transaction. This is the creation of a script that is stored in the Bitcoin blockchain.
2.  Stage 2 is when the script is spent. To spend the UTXO or coins which were transferred to the public key in the script is to be spent when the UTXOs are spent as money or value exchange. This is when the output script is combined with input script (unlocking script, or ScriptSig) and spent. Once the output UTXO is spent, this script loses its meaning.

Typically when you use `OP_RETURN`, what it does is, it informs that no processing is needed post this. This means that `OP_RETURN` fails the script. If you remember from *[Chapter 5: Transactions and Transaction Script](#c05.xhtml)*, to be able to spend any UTXO the script validation needs to be true so that the unlocking of the locking script happens and the UTXO is transferred to the next owner. With `OP_RETURN`, the script fails immediately. If you recall, the script is a predicate, so it always returns true or false. If successful completion of the running script gives true, and if script run fails it returns false.

The most interesting part of this is, Bitcoin does not have any other code which does any type of validation on the script. So literally, when the script fails with `OP_RETURN`, whatever is the data post that is added in the script, stays there forever and does not get looked at by miners. Even the limit of a script length which is max size 520 bytes is not checked as well when a transaction with `OP_RETURN` is validated by the miners. Reference: Bitcoin Code repository:

**[https://github.com/bitcoin-sv/bitcoin-sv/blob/master/src/script/script.h](https://github.com/bitcoin-sv/bitcoin-sv/blob/master/src/script/script.h)**

To explain this more clearly, let us take a transaction output which contains an `OP_RETURN` with a few bytes message so that we understand how this works:

`{`

`"value" : 0.00000000,`

`"n" : 0,`

`"scriptPubKey" : {`

`"asm" : "OP_RETURN 636361726c6579206c6f76657320",`

`"hex" : "6a12636361726c6579206c6f76657320",`

`"type" : "nulldata"`

`}`

`}`

In the above snapshot, we have an `OP_RETURN`, and a few bytes after that is what we have as the added data post `OP_RETURN` in the script. `OP_RETURN` hex is 0x6a, the byte next to it represents the length of the data, so 0x12 = 18 bytes. Then the 12 bytes of data are stored.

This is a simplified version, as you can imagine, when you store 100kb data, it will be quite a large hex and script to show here. You can find many transactions if you want to look at how they look at whatsonchain.com. One example is: **[https://whatsonchain.com/tx/ffe19e5da1f54735c5981cc8a25dc5bb349f2d3575d3f0f23a3df9fb67ae62b5](https://whatsonchain.com/tx/ffe19e5da1f54735c5981cc8a25dc5bb349f2d3575d3f0f23a3df9fb67ae62b5)**

Detailed usage of PUSHDATA is present at the Bitcoin SV GitHub page:

**[https://github.com/bitcoin-sv-specs/op\_return/blob/master/01-PUSHDATA-data-element-framing.md](https://github.com/bitcoin-sv-specs/op_return/blob/master/01-PUSHDATA-data-element-framing.md)**

The original design of the Bitcoin codebase did not need `OP_RETURN` to add data to the blockchain. The `PUSHDATA` opcodes were the ones that had been designed to store data on the blockchain, and PUSHDATA4 can store about 4.3 GB data in one single transaction. If we just look at using the script, shown in the below example:

`48656c6c6f20776f726c6421 OP_DROP OP_DUP OP_HASH160 4cd91d791372e0b0660kre34e8dd84fc65c2c123 OP_EQUALVERIFY OP_CHECKSIG`

The above script will push a stream of bytes `48656c6c6f20776f726c6421` ("`hello world`!") to the stack, then `OP_DROP` will remove the data stream and the remaining script is just a standard validation script which we have seen earlier. This is one way to store streams of bytes but will be limited by the maximum script length and to store more than just this, we use the `PUSHDATA` codes which we discussed earlier.

The way `PUSHDATA` is used is shown in the below-mentioned example, where we are storing a picture using the B protocol which we saw in the last chapter:

`OP_PUSHDATA4 B_PROTOCOL_DATA OP_DROP OP_DUP OP_HASH160 4cd91d791372e0b0660kre34e8dd84fc65c2c123 OP_EQUALVERIFY OP_CHECKSIG`

Another difference here from using `OP_RETURN` is that the output UTXO here could be spendable so as to ensure that the transaction is not pruned by miners. This requires a bit more explaining so as to understand how the Bitcoin protocol works. This also addresses the concern that how large the Bitcoin blockchain will get if global financial or even cat picture data is stored on the blockchain. It also addresses the myth that anything that you store as data on blockchain will be there forever. It is quite explained in detail in the Bitcoin whitepaper, section 7. More details of this idea are documented in an excellent blog writeup present at:

**[https://blog.bsv.sh/the-prunability-and-non-permanency-of-your-data-the-case-of-op\_return/](https://blog.bsv.sh/the-prunability-and-non-permanency-of-your-data-the-case-of-op_return/)**

**[https://medium.com/@jolon/issues-surrounding-bsv-data-permanence-and-proposed-solution-4f0f904ae5a8](https://medium.com/@jolon/issues-surrounding-bsv-data-permanence-and-proposed-solution-4f0f904ae5a8)**

The snapshot in *[Figure 9.1](#c09.xhtml#fig9_1)* shows what the whitepaper describes in terms of the pruning of transaction data from the blockchain and how that is managed while still keeping the integrity of the Merkel tree and path intact for being able to keep all historical Bitcoin block and headers same but removing the transaction data from the node storing the blockchain.

![](images/Figure-9.1.jpg)

**Figure 9.1:** Pruning of transaction data and replacing by Hash

This concept gives a method to miners to be able to delete data stored in transactions on the blockchain if that is required either by law or due to miner preferences. These two cases are explained below:

*   **Court order:** Many times it is possible that someone can store illegal data on the blockchain which could be as a proof of the crime, what if a court order comes for purging that data? Can the court accept the reasoning that since it's a blockchain it cannot be deleted? Most reasonably a court will shut down the blockchain rather than taking that argument on its face value, these are the situations where it is needed to delete the data, and the above-shown pruning method will just do so dispelling the myth that blockchain is immutable. It is subject to legal restrictions which when comes miners as legitimate businesses, will oblige and purn the data.
*   **Selective pruning:** Many times and many miners may or may not be interested in storing all of the data depending on what kind of business/service they provide. They could choose to not store the transactions which are of zero value but contain data which is typically the case with `OP+RETURN` transactions. I expect this as a quite common way of storing blockchain by miners when the size of the blockchain becomes large (petabytes of data).

The most certain way to store data will be to have some UTXO present and using PUSHDATA opcodes so that there is an incentive (UTXO) for miners to make sure they don't purn the data.

# [Database on Bitcoin: BitDB](#toc.xhtml#s167a)

One of the first new ideas that were implemented on the newly formed Bitcoin cash blockchain back in 2018 was done by a prolific developer who goes by a pseudonym Unwriter. We have looked at some of his work in the last chapter, but I am going back into history a little bit before I come back to present in terms of what is happening in the ecosystem.

Back in early 2018, the first attempt for creating a structure on top of the Bitcoin blockchain was done in the form of a NoSQL database that continuously synchronizes itself with the Bitcoin blockchain.

What does this mean?

If you think of Bitcoin as a hard disk BitDB is like RAM which brings a subset of Bitcoin blockchain in a formal structure for application usage. Original Bitcoin software came with a JSON-RPC client which is still there, but BitDB takes it to a new level by providing sustained in-memory data which was not done until now. BitDB uses MongoDB for its implementation, query, and search features. BitDB is a read-only database that provides a subset of the Bitcoin blockchain in a user-defined manner. It comes with 3 components:

*   Crawler
*   Indexer
*   Query

The below figure shows the basic architecture diagram of how the setup of BitDB works along with the interactions with blockchain and client:

![](images/Figure-9.2.jpg)

**Figure 9.2:** Architecture diagram for BitDB with its components

BitDB is a subset of the transactions present in the blockchain, quoting Unwriter who created BitDB:

*"Humans can't directly write to BitDB. The only "user" with "write" permission to BitDB is Bitcoin itself.*

*BitDB utilizes Bitcoin as the single source of truth and doesn't require any human intervention once it starts running as an autonomous daemon because it's a self-contained crawler + parser + indexer + query engine, all in one.*

*Because BitDB is backed by Bitcoin as canonical storage, it comes with all the benefits of Bitcoin's decentralization (Anyone can reconstruct and run a BitDB node from scratch as long as they have a Bitcoin node). Because BitDB is powered by MongoDB as an index, it comes with all the benefits of NoSQL databases, such as a highly flexible and portable query interface and better user experience."*

Let us now look at various components of BitDB.

# [Crawler](#toc.xhtml#s168a)

A Crawler will crawl the Bitcoin blockchain in time (Bitcoin is a timestamp server). Just like when you search the web, it goes through the available web page links and then indexes those links based on the internal algorithm prioritization to display the results to the user as she desired, a crawling in Bitcoin will be going through blocks by blocks to index the data that is requested by the user. Just like the search engine will index the web pages based on the keywords to create a search index, BitDB indexes structured data (Bitcoin Transactions) to create a knowledge index.

# [Indexer](#toc.xhtml#s169a)

Indexing in BitDB will take raw Bitcoin transactions which are identified by the crawler, and then transforms them into a structured data format. This makes it possible to store the data into a database and query the data.

Steps to structure raw Bitcoin transactions are mentioned below:

1.  **Step 1.** Raw Transaction: 
    
    `0100000001b08acdbdad97ad6670c83cee6794bfbd1e9bb1220b9e6b3116b754 bca2459 326010000006a47304402201c6039241540945c8c65f3d3ba116dd7 b77ea2ca8 9afac33 ef49a8bfa66dafef022035f906ffc1a12613cab7ee1 ec9443674f594039c09fc e6e59b4 f1781e18086f8412103d6d364d 316 6682 1548044723f6a8b 15f43e6c7dc5edcc 2fc3cf 7831b3e81095cffffffff020000000000000000176a026d0212706f737 420746 f206d65 6d6f2e636173682108420000000 00000197 6a91419b26abab87de1a5d07d34a1 2f232f5 b75c7caf188ac00000000`
    
2.  **Step 2 :** Deserialize the raw transaction: 
    
    `# INPUT:`
    
    `71 0x304402201c6039241540945c8c65f3d3ba116dd7b77ea2ca89af ac33ef49a8bfa 66dafef022035f906ffc1a12613cab7ee1ec944 3674f594039c09fce6 e59b4f1781e18086f841330x03d6d364d31666 821548044723f6a8b15f43e6c7dc5edcc2fc3cf7831b3e 81095c`
    
    `# OUTPUT:`
    
    `OP_RETURN 2 0x6d02 18 0x706f737420746f206d656d6f2e6361736821`
    
    `OP_DUP OP_HASH160 20 0x19b26abab87de1a5d07d34a12f232f5b75c7caf1 OP_EQUALVERIFY OP_CHECKSIG`
    
    `The above format is fairly readable but still not possible to query the data in the above format. This is done by converting the above data into a JSON type format as mentioned in step 3.`
    
3.  **Step 3:** In this step, we will add metadata to the existing transactions so that we can identify and tag the fields present in the transaction so that we can query them using those tags at a later point in time. This reformatted transaction will be stored as a MongoDB document in the local storage making it easy to search. 
    
    The document structure used for this is detailed out as a template for a transaction below. Metadata is divided into three major chunks for block information, transaction input and output information respectively: blk.i (block index), blk.h (block hash), blk.t (block time) as shown in the below-mentioned template:
    
    `{`
    
    `"tx": {`
    
    `"h": [TRANSACTION HASH]`
    
    `},`
    
    `"blk" {`
    
    `"i": [BLOCK INDEX],`
    
    `"h": [BLOCK HASH],`
    
    `"t": [BLOCK TIME]`
    
    `},`
    
    `"in": [`
    
    `INPUT1,`
    
    `INPUT2,`
    
    `INPUT3,`
    
    `…`
    
    `],`
    
    `"out": [`
    
    `OUTPUT1,`
    
    `OUTPUT2,`
    
    `OUTPUT3,`
    
    `…`
    
    `]`
    
    `}`
    

Once a transaction is formatted in the above template metadata, it is stored in BitDB as a document/row. Readers can refer to the below links for further reading and understanding.

**BitDB: [https://bitdb.network/](https://bitdb.network/)**

**Indexer for BitDB: [https://docs.bitdb.network/docs/indexer](https://docs.bitdb.network/docs/indexer) and [https://bitdb.network/dashboard](https://bitdb.network/dashboard)**

# [Bitquery](#toc.xhtml#s170a)

This is where we come to the utility of BitDB. Now you can query the Bitcoin blockchain using various attributes, not just the transaction id or the UTXO addresses, as it is done in most of the block explorer but using various other attributes of a transaction including the protocols that are being used in the transaction or even various other fields present in input and output of a transaction.

![](images/Figure-9.3.jpg)

**Figure 9.3:** Syntax for the bitquery language as described by unwriter

An example of bitquery is shown below:

"Find 100 transactions with an output `OP_RETURN` script that starts with 0x6d02 (`memo.cash`). And then return only its block index, block time, and content."

`{`

`"v": 3,`

`"q": {`

`"find": { "out.h1": "6d02" },`

`"limit": 100`

`},`

`"r": {`

`"f": "[{ block: .blk.i?, timestamp: .blk.t?, content: .out[1].s2 }]"`

`}`

`}`

Querying by using multiple addresses to find all transactions sent from the address:

`{`

`"v": 3,`

`"q": {`

`"find": {`

` "in.e.a": "14xMz8rKm4L83RuZdmsHXD2jvENZbv72vR",`

` "out.e.a": "14xMz8rKm4L83RuZdmsHXD2jvENZbv72vR"`

`},`

`"limit": 10`

`}`

`}`

The details of how BitDB works under the hood and various practice queries can be found at below links:

**Bitquery: [https://docs.bitdb.network/docs/query\_v3](https://docs.bitdb.network/docs/query_v3) and visualizer:**

**[https://bitgraph.network](https://bitgraph.network)**

# [Genesis, Babel, Chronos, and Meta](#toc.xhtml#s171a)

The idea of having a data structure for doing various operations is quite powerful and that is a large step towards building infrastructure on Bitcoin blockchain. With the above ideas, Unwriter went ahead and created various versions of BitDB which are available for anyone to access and use.

If you have worked in an enterprise database setup you will be aware of some of the structures of databases used: a version that stores all history, a version that stores daily or current data. Similar to that there are few implementations of BitDB provided out of the box which does similar use cases. Let us look at them one by one.

# [Genesis](#toc.xhtml#s172a)

We can think of this as the base version of BitDB the only difference being the first step change to use the original format of UTXO address and not the version called Cash Address (this being a legacy feature now more commonly used in Bitcoin cash BCH version of Bitcoin). It is everything BitDB and an additional feature providing API endpoint for easy access for your application (HTML/NodeJS example shown at source website: **[https://medium.com/@\_unwriter/genesis-a25b121e0575](https://medium.com/@_unwriter/genesis-a25b121e0575)**

# [Babel](#toc.xhtml#s173a)

This is another subset of BitDB, with a specific purpose enabling users to query arbitrary data written in the `OP_RETURN` to the chain. It can be thought of as a lighter version of the Genesis node which ignores the scripts and remaining transaction data and focuses only on the data that is stored in transactions using `OP_RETURN` making it a subset of Genesis: Source website for more details:

**[https://medium.com/@\_unwriter/babel-230f73ed5dcb](https://medium.com/@_unwriter/babel-230f73ed5dcb)**

# [Chronos](#toc.xhtml#s174a)

This is a special version of BitDB which stores a sliding 24 hours of transactions along with additional attributes of time for each transaction by adding two time-related fields timestamp and timeago, which records the Unix timestamp and how long ago the transaction was discovered. Chronos timestamps transactions based on when the host Bitcoin node discovered those transactions, instead of using the block time which means every Chronos node will have different timestamp data from one another because every node discovers transactions independently from one another.

And THIS is the tradeoff Chronos makes. By supporting the real world timestamp, it loses a bit of determinism. But that's OK for many apps, and Chronos is still very useful for various use cases.

More details at source website:

**[https://medium.com/@\_unwriter/chronos-f0f751669fef](https://medium.com/@_unwriter/chronos-f0f751669fef)**

# [Meta](#toc.xhtml#s175a)

Meta is another version of BitDB which focuses on the metadata of blocks like the block height, block difficulty, timestamps starting from the first block mined on the blockchain. This is quite fast to access due to storing only the metadata and can be used for applications to code logic based on block attributes and some additional attributes that meta adds like timeago and chainwork.

All in all the idea of talking about these versions of BitDB show that there is so much to do to build custom applications over the data present in the Bitcoin blockchain making it a universal data store along with an infrastructure that can beat IT security, availability, reliability of any best in industry enterprise application and that is made available for just anyone to use.

Even though there are upgraded versions of BitDB has been released, with a bunch of new utilities (Planaria (Neon, Grid), BOB, MOM, Eventchain, etc., which we will discuss in the next chapter), it is important to understand the concepts of BitDB and using Subquery which forms the basis of all these tools. We will be covering a snapshot of key ideas about bitquery but it is recommended that you do a bit of hands-on and reading bitquery documentation for a detailed understanding of basics. More details are present at source website:

**[https://medium.com/@\_unwriter/meta-be3c18582ec7](https://medium.com/@_unwriter/meta-be3c18582ec7)**

# [Bitsocket](#toc.xhtml#s176a)

Bitsocket is a powerful Bitcoin blockchain push notification service that can be thought of loosely as the Bitcoin version of a WebSocket but goes further and provides rules to make **Server-sent events (SSE)** using the Bitcoin blockchain. It does this by transforming the Bitcoin transactions into events and in turn into push notifications.

It works in three steps, step 1 is to transform the Bitcoin transaction into a structure (using bitquery). Then by taking the application or user-defined filters, it will create events from the criteria defined by that application (application-specific custom query). These events could be, for example, a new transaction to a specific Bitcoin address (when a new payment comes to my Bitcoin address, I can send myself an email). Each of these defined events will be pushed to the corresponding application as SSE (making it possible for a server (Bitcoin blockchain in this case) to send new data to a web page (of your application) at any time, by pushing messages to the web page.

Bitsocket lets you monitor real-time Bitcoin networks in a completely custom-defined manner, and this can be for monitoring of the entire blockchain, not just any specific address or transaction or block. An example is shown below:

`// Write a bitquery`

`var query = {`

`"v": 3, "q": { "find": {} }`

`}`

`// Encode it in base64 format`

`var b64 = btoa(JSON.stringify(query))`

`// Subscribe`

`var bitsocket = new EventSource('https://genesis.bitdb.network/s/1FnauZ9aUH2Bex6JzdcV4eNX7oLSSEbxtN/'+b64)`

`// Event handler`

`bitsocket.onmessage = function(e) {`

`console.log(e.data)`

`}`

# [Datapay and bitindex (write and read data)](#toc.xhtml#s177a)

Let us have a look at two very simple yet very powerful libraries for reading and writing of data on the blockchain.

# [Datapay](#toc.xhtml#s178a)

Datapay is a method to write data to the Bitcoin blockchain. It provides you a very simple way to write data to the blockchain. It gives you a very simple few lines of code to write `OP_RETURN` data to the blockchain. It is powered by a library we saw in the earlier chapter called bsv. It is an open-source library that is used by companies like moneybutton and a large set of programmers who are starting to build applications as the first step to learn to build on blockchain. It is quite easy to use and provides a full set of crypto and various functions related to creating and sending transactions to the BSV blockchain.

Datapay is different from usual libraries as it focuses on sending data rather than sending money in a transaction. It has two methods:

*   **Build:** for constructing a transaction
*   **Send:** for sending the transaction constructed using build.

Details on how to build and send transactions along with code examples can be found at **[https://github.com/unwriter/datapay](https://github.com/unwriter/datapay)** but to just specify how simple datapay makes to write data, below is an example of posting of a transaction using datapay to the blockchain using memo protocol:

`{`

`"data": ["0x6d02", "post to memo.cash!"],`

`"pay": {`

`"key": "Private Key value"`

`}`

`}`

The above 3 lines of code can post data *post to memo cash* to BSV blockchain.

It is also possible to make elaborate transactions including data and money both using datapay as well. Below code snippet shows the full featured transaction build using databay library:

`var config = {`

`safe: true,`

`data: ["0x6d02", "hello from datapay"],`

`pay: {`

`key: "PrivateKey",`

`rpc: "https://api.bitindex.network",`

`fee: 10,`

`to: [{`

` address: "PubAddress",`

` value: 100`

`}]`

`}`

`}`

**Here the safe:** true parameter is defined for the usage of `OP_FALSE OP_RETURN` which is the updated usage needed for `OP_RETURN` going forward.

The above code posts a message using `memo.cash` network paying fees of 10 satoshis signed using the `PrivateKey` through JSON-RPC endpoint while also tipping another user, `PubAddress` 100 satoshis.

# [Bitindex](#toc.xhtml#s179a)

Bitindex is a JavaScript-based Rest API or JSON-RPC method to easily query balances, blocks, xpubs, UTXOs, and transactions on the BSV blockchain. It has now been updated to a new version called Mattercloud JS but the overall concept and idea remain the same.

It is a full feature JavaScript library to interact with BSV blockchain. More details and usage of the library is present at the source documentation and GitHub links mentioned below:

**[https://developers.mattercloud.net/#introduction](https://developers.mattercloud.net/#introduction)**

**[https://github.com/MatterCloud/mattercloudjs](https://github.com/MatterCloud/mattercloudjs)**

# [Bitpipe](#toc.xhtml#s180a)

One of the magnificent examples of a microservice implementation of the Datapay protocol is Bitpipe, a Bitcoin transaction broadcast microservice. The biggest feature of bitpipe is it allows you for broadcasting unsigned transactions to create unique service models for your application (community paid chat service like bitchat or creating a freemium model of applications, where you pay for initial transactions of users and later change based on usage). If you think about it, it also provides a unique way to pay for your application's users in Bitcoin while charging your users in fiat currency.

Bitpipe sets up a web server that can accept datapay payloads in various formats as needed and defined in the datapay protocol for composing transactions. On top of that, you can even override the payload on the server to create a transforming pipe creating an extremely flexible service.

You can read about the various features like:

*   Creating signed raw transactions
*   Creating unsigned raw transactions
*   Creating filters and map (transforming of data by using a mapping function)
*   Multiparty Unix like pipe system

Details describing all these features can be found in the GitHub page along with code for bitpipe: **[https://github.com/unwriter/bitpipe](https://github.com/unwriter/bitpipe)**

# [Bitchat](#toc.xhtml#s181a)

Bitchat is a multiplayer, decentralized real-time chat using the `OP_RETURN` data, powered by BitDB, Bitsocket, and Bitpipe that can be built on the BSV blockchain. Details and code are present at the GitHub repository **[https://github.com/unwriter/bitchat](https://github.com/unwriter/bitchat)** and this being built using bitpipe leverages the usage of unsigned transactions that are broadcasted by users who chat but paid by someone else (or using something like a community funded wallet).

# [Bitfs](#toc.xhtml#s182a)

Bitfs is a Bitcoin filing system, which crawls the Bitcoin blockchain to find and store all the bitcoin script pushdata chunks larger than 512 bytes. This is an autonomous file system constructed using Bitcoin blockchain and the key differentiating factor is that it focuses on pushdata based data stored in the blockchain which is larger than 512 bytes.

Details on how bitfs works are present at following links along with the actual results that biffs read in real-time and displays:

**[https://view.bitfs.network](https://view.bitfs.network)**

**[https://bitfs.network/about](https://bitfs.network/about)**

# [Toychain](#toc.xhtml#s183a)

Toychain is a distributed version control system for Bitcoin (transactions). Literally, it provides you a version control system for individual transactions and works very similar to how Git works for a code repository, just the difference being it does it for Bitcoin:

![](images/Figure-9.4.jpg)

**Figure 9.4:** Toychain branching of a Bitcoin transaction and its working similar to how Git works for the codebase. Image source: [https://toychain.network/#/?id=toychain](https://toychain.network/#/?id=toychain)

So you can take up individual transactions and clone it, keep adding more transactions on the top of it to build a transaction graph as needed by your application, and then push the final transaction when you are ready. A very elaborate and detailed documentation and example/usage of this utility is present at the creator's website: **[https://toychain.network/](https://toychain.network/)**

# [Conclusion](#toc.xhtml#s184a)

We have seen a set of first versions of application development which was done on the BSV blockchain. With things like BitDB, datapay, bitindex a large set of developers started building and using these protocols for building real-life applications but since these were the very first attempts, most of them have now evolved into a much more sophisticated applications/protocols in time. You would notice that most of the above GitHub repositories will have a comment mentioning they are being deprecated and replaced by a new version of it.

The intent of still going through these initial attempts was to understand the basic concepts and evolution of application development on the Bitcoin blockchain. This also reflects the large spectrum of features and functionality that is possible to be built upon the blockchain which only leaves imagination and action as the remaining elements a developer or organization needs to bring in and build.

In the next chapter, we will look at the next version of these applications and a whole lot of toolsets that can be used to build enterprise-level applications.

# [Questions](#toc.xhtml#s185a)

1.  What is the difference between using `OP_RETURN` and `PUSHDATA` for adding data to the blockchain?
2.  Why is `OP_FALSE OP_RETURN` used, how does it enable backward compatibility?
3.  Why is keeping a sizeable UTXO along with data transactions helps in ensuring that it will not be pruned by miners?
4.  What are the most unique features of datapay and bitpipe which helps you build community-funded chat rooms?

# [CHAPTER 10](#toc.xhtml#c10)

# [Planaria Application Development Framework](#toc.xhtml#c10)

**"Simple programs can produce a high level of complexity, and in fact it turns out, these programs can reproduce many features of biological organisms."**

*\- Stephen Wolfram*

Bitcoin is a system that is based on simple rules (transaction, script instructions), working together to demonstrate complex behavior. This is the reason for the cheap and highly efficient transaction processing system that Bitcoin is which can scale to billions of transactions per block. We saw some simple systems in the last chapter which were initial ideas of implementing small but powerful functionalities on top of Bitcoin, and those ideas lead to the development of actual frameworks and tools which can be used to build quote complex applications. In this chapter, we will look at various frameworks that were built on the top of the ideas we discussed in the last chapter and more.

# [Structure](#toc.xhtml#s186a)

*   Neon Planaria, bitbus, and overall planaria framework
*   Advanced ideas built using neon and grid planaria, MOM, BOB, eventlog
*   Overpool, payment channels, and off-chain transactions connecting on-chain.

# [Objective](#toc.xhtml#s187a)

After studying this chapter you will be able to understand how to use the planaria framework to build the backend of your application. You will also understand various toolsets used to read and write to your planaria node and overall Bitcoin blockchain. Once you are completed with reading this chapter you will be ready to start building your application using Bitcoin blockchain as a backend in a client-server-blockchain model of development.

# [Planaria framework](#toc.xhtml#s188a)

The initial idea of BitDB and its components provide a powerful structure to build on top of Bitcoin and its more formal framework was built by Unwriter named Planaria. Planaria can be thought of as an infinite API and as a Bitcoin equivalent of API frameworks like Ruby on Rails, Django, Laravel, Spring, etc.

Using this framework is again optional but this framework provides an easy methodology to build your own containerized API microservice powered 100% by Bitcoin. Using these frameworks introduces an additional third-party dependency (when you build an application you will be running your own planaria node which will make you the third party which application users will be dependent on).

# [Basic concepts](#toc.xhtml#s189a)

As you would have noticed, in [section II](#p02.xhtml) and the last few chapters, we are moving away from thinking of Bitcoin as money more and more but as a network with a set of capabilities. With planaria, we are moving further away and thinking of Bitcoin as an infinite motor, which (based on its algorithm) is capturing transactions by navigating in time and producing them as events. Infinite as this process will continue till the network is running obviously but the assumption is, that it will be forever unless it's shut down in entirety due to some unforeseeable reason.

To quote Unwriter:

*"Bitcoin == Motor*

*We can think about how to build a machine with a motor (Bitcoin). But first, what exactly is a "machine"?*

*A machine is a function. A machine takes the motor as the constant source of energy and transforms the energy into various forms that can be consumed by humans or other machines.*

*Machine = F(Motor)*

*You can create an infinite number of "machines" from a single reliable motor, which is Bitcoin."*

Once you have a motor, you can build any type of machine that uses that motor. Planaria is a framework that helps you do that. It helps you build state machines.

State machines are quite extensively used in designing real-life applications and are abstract mathematical models that exist in a specific state at any given point in time. When the conditions or external input is changed the state machines go from one state to another. Simple examples in real life are vending machines that dispense products when a certain number of coins are inserted or elevators which start moving when you step on the first step. State machine diagrams are widely used when designing software applications to create a logical flow of defining rules of application behavior using UML diagrams or such.

State machines can be **finite state machines (FSM)** or infinite state machines depending on the design of the machine. Typically most of the real-world applications are designed as FSM as they are in exactly one finite-state at any given time. *[Figure 10.1](#c10.xhtml#fig10_1)* shows a generic state machine and the flow of various interactions between components. It is possible to build this complete system using Planaria and Bitcoin:

![](images/Figure-10.1.jpg)

**Figure 10.1:** A generic state machine and its components, Source: [https://docs.planaria.network/#/intro](https://docs.planaria.network/#/intro)

*   **Input**: An event listener that listens to real-time events/states from Bitcoin
*   **Transition logic**: Program that will handle the state change using CRUD operations API
*   **State Memory**: A memory to persist the state attributes and updates
*   **Output Logic**: An event producer that publishes custom programmable events for other modules and SSE

A traffic light system can be taken as an example of an FSM. It contains three light bulbs which are red-green-yellow based on the current state and each state is dependent on the last state and follows a strict sequence of state change done by the event or input of the time clock.

# [Planaria implementation](#toc.xhtml#s190a)

Planaria implements all of the above-discussed concepts in simple JavaScript code and powered by Bitcoin. Planaria is a framework effectively to build your own custom BitDB (Genesis, Babel, Chronos, and Meta are custom planaria nodes) and technically planaria is a containerized MongoDB instance. It also provides powerful CRUD APIs using Bitcoin events as inputs and storing states in MongoDB. All of the components discussed above are implemented using Bitcoin in planaria framework and providing various APIs for these operations (input, transition logic, state storage, and output logic) as shown in *[Figure 10.2](#c10.xhtml#fig10_2):*

![](images/Figure-10.2.jpg)

**Figure 10.2:** Planaria APIs for various state machine components. Source: **[https://docs.planaria.network/#/intro](https://docs.planaria.network/#/intro)**

As you can see that planaria provide a complete set of APIs to use bitcoin as a data storage for any application. This is not it, there are few other features of planaria that can help you build a full-scale backend for your application as we will discuss further. Code-level details are present at the link:

**[https://docs.planaria.network/#/api?id=anatomy-of-a-planaria](https://docs.planaria.network/#/api?id=anatomy-of-a-planaria)**

Planaria has the following set of APIs that can be constructed:

*   **Attributes**: When you build a planaria node, you will be defining the various attributes of the data that you will use to store and you can build APIs to serve your data based on those attributes.
*   **Event Handlers:** You can build APIs listening to events (which are usually new transactions that will bring about a state change for the FSM built with planaria).
*   **State APIs:** state CRUD APIs.
*   **Publish APIs:** output APIs for publishing events.

Unwriter who has created the framework provides many notes running these framework based nodes for other users to use like some of the BitDB nodes we saw in the last chapter (Genesis, Chronos, Babel, and Meta). Similarly, he is making available few other nodes built on the planaria framework as well like Neon Genesis which can be explored further via below mentioned links:

**[https://medium.com/@\_unwriter/neon-genesis-387fd2f122de](https://medium.com/@_unwriter/neon-genesis-387fd2f122de)**

**[https://neongenesis.bitdb.network/](https://neongenesis.bitdb.network/)**

# [Planaria file system](#toc.xhtml#s191a)

We have already discussed that planaria provide an API for writing, this property can be further extended to store files by writing data to the blockchain as well. Details of the implementation are present at the link:

**[https://docs.planaria.network/#/api?id=\_5-file-serve-api](https://docs.planaria.network/#/api?id=_5-file-serve-api)**

This property can be used to create a file serve API which can be used to write static files as well. Unwriter demonstrated this by creating a blockchain version of Instagram called bitstagram which became fairly popular to store images and provide an Instagram like a timeline of images. **[https://bitstagram.bitdb.network/](https://bitstagram.bitdb.network/)**

**[https://planaria.network/@1BvPxwDoz6DR9qedZrKJjWio6Gm7UCPGXU](https://planaria.network/@1BvPxwDoz6DR9qedZrKJjWio6Gm7UCPGXU)**

# [The version control system on Bitcoin](#toc.xhtml#s192a)

Being able to store files on Bitcoin also provides a whole new set of use cases and one such a use case is a version control system like Git on the blockchain. If you have used Git/GitHub which has become the most popular and default go-to tool for the version control system (apart from other things) for developers, that is something that can now be built on Bitcoin blockchain with added advantages of having the codebase stored on a blockchain.

Once we have a file system there are a plethora of use cases possible for applications including using this system for private file store system, flat-file database, storing machine learning models and training them using Bitcoin transactions, 3D printing model files, models and files for building analytics model for data visualization and many more, only ideas are needed to use this infrastructure.

# [Neon Planaria](#toc.xhtml#s193a)

Neon planaria are the current version of planaria which is the same as what we have discussed till now, just that it is the final base version to be used which removes some limitations of initial planaria to build a full-scale Bitcoin backend. There is not much difference between the two, with neon being the next version of the first by removing limitations like using MongoDB and Docker container specializations and making them generic. Let us re-look at the neon planaria framework from the perspective of building a backend and also allowing for building a lightweight version of planaria using bitbus. There are two main components of the framework:

*   **Planaria**: These set of functions are used to create your planaria state machine. Planaria keeps synchronizing itself in real-time with blockchain programmatically. This process (using event listening to record new transactions) keeps the state machine updated based on the criteria it was created. You also transform and store relevant transactions in the desired format for easy access to data later on.
*   **Planarium**: This component provides a set of functions that can be used to create API endpoints from the generated Planaria state machine. Planarium provides an explorer and an API endpoint, along with a built-in convention to design your JSON query language like Bitquery.

*[Figure 10.3](#c10.xhtml#fig10_3)* shows a high-level interaction setup for an application using planaria/Bitcoin blockchain:

![](images/Figure-10.3.jpg)

**Figure 10.3:** Bitcoin blockchain - Planaria - Application interconnection

In the above diagram, **f()** is the function that defines a filter for the data to be specified for a certain application, **p** is the neon planaria node catering to the application as a backend.

Neon planaria can be thought of as a simple node.js app that requires no containers, ports, or firewall setup using a feature called BitBus to replace the work needed to set up a Bitcoin node making it minimalistic and easy to learn and build.

# [Bitbus](#toc.xhtml#s194a)

Creating the backend infrastructure has been considered always quite a specialized and cumbersome task even in traditional application architectures leading to the whole idea of serverless computing where IaaS providers have taken a lead and fasten the application development in turn in doing so.

Bitbus is the same idea implementation on Bitcoin. Bitbus is *serverless* for Bitcoin or in other words, *bitcoinless* application development. It removes the need for application developers to run a full node for their applications.

Quoting Unwriter

*"Bitbus is a simple one-way Bitcoin synchronization service which lets you replicate a filtered version of the entire blockchain to your local machine in real-time. No need to run and manage your own Bitcoin node. No need to store the entire blockchain. With Bitbus, you can*

*   *Filter and Synchronize ONLY the parts of the blockchain you want, through a query language (Bitquery).*
*   *Cache them as files.*
*   *Build your Bitcoin backend from the cache.*

*All this without running a full bitcoin node. It also comes with an instant HTTP endpoint and an explorer which displays all the locally synchronized data for your "instant blockchain". Bitbus backend is made up of multiple modules, one of which is a Planaria node. More specifically, it's backed by a custom Neon Genesis instance."*

A bitbus filter in basic version uses below format:

`{`

`"bitbus": 1,`

`"name": <YOUR BITBUS NAME>,`

`"host": {`

`"bitbus": <BITBUS ENDPOINT>`

`},`

`"from": <BLOCK HEIGHT TO SYNC FROM>,`

`"q": <BITQUERY>`

`}`

*[Figure 10.4](#c10.xhtml#fig10_4)* shows the idea on a high level. Using the bitquery crawling functionality, you crawl the Bitcoin blockchain to get only the application-specific data blocks identified and storing their block data as provided after going through the custom application-specific query filter removing the need for storing any other data from the blockchain except what your application needs:

![](images/Figure-10.4.jpg)

**Figure 10.4:** Bitbus as the minimalistic data filter for feeding to neon planaria and creating a serverless infrastructure for applications using bitcoin as a backend.

Once you have your bitbus setup ready you can build your planaria node on the top of bitbus. It could also be a complete custom data store as needed not limited by using MongoDB but any type of data store like using a relational database (like PostgreSQL, MySQL, Oracle, etc.) or a NoSQL database (like Hbase or Casandra, etc.). Once your application datastore is set up (using planaria) you can use data access APIs (CRUD) from planaria and pretty much all kinds of APIs needed for the backend of your application.

Details of implementing Bitbus can be found at

**[https://bitbus.network/docs#/?id=programmatic-usage](https://bitbus.network/docs#/?id=programmatic-usage)**

# [Neon Planaria and Bitcoin as Tape](#toc.xhtml#s195a)

When the limitations of the planaria version were removed, there were larger use cases that came about and one of them conceptually was to use Bitcoin as tape in terms of a turing machine.

To read more details on Turing machines and tape you can refer to the below-mentioned links:

**[https://www.cs.odu.edu/~toida/nerzic/390teched/tm/othertms.html](https://www.cs.odu.edu/~toida/nerzic/390teched/tm/othertms.html)**

**[http://mathworld.wolfram.com/TuringMachine.html](http://mathworld.wolfram.com/TuringMachine.html)**

Using a data store abstraction of Bitcoin as the tape is similar to a theoretical turing machine concept which uses tape for task execution, except Bitcoin works as a never-ending tape which moves only forward and grows every 10 mins or so by a method called proof of work. Bitbus makes for a sub-set tape but with a head that keeps synchronizing with Bitcoin blockchain and in turn, planaria are further on subset tape which synchronizes with bitbus tape. Of course, the subset part depends on the filter you have defined to select the data from the Bitcoin blockchain. One benefit of this structuring is that even if your Bitbus or planaria crashes, it can always be restored as bitcoin tape is something that is never crashing or unavailable. It provides for a 24/7 availability and very easy disaster recovery of your application infrastructure. On the same lines, if some of your data is corrupted, all you have to do is to rewind the planaria/bitbus tape to resynchronize with the blockchain, and your application is fully recovered and running fine post a crash like an event.

The benefit of using the tape like abstraction is that you can build multiple different planaria tapes for your application that can interact with each other using the same common bitbus tape for initial filtering of transactions for your application and even not use bitbus for that matter and build multiple planaria nodes working on top of Bitcoin blockchain as well.

You can read through setting up a planaria system using bitbus and other details at the below documentation link: **[https://neon.planaria.network/#/?id=syntax](https://neon.planaria.network/#/?id=syntax)**

One key thing to note is that these frameworks that we have discussed till now are something that is available for you to use to build up your backend infrastructure from scratch or there are many nodes provided by the creator which are ready to use for building your application without having to run a node (currently free, but of course for a cost at some point). It is very similar to a cloud hosting service like GCP or AWS which even currently are becoming a norm when building scalable enterprise or heavy usage applications.

The node implementation available using neon planaria framework for usage is called neon genesis and you can find more details about it here:

**[https://planaria.network/@1HcBPzWoKDL2FhCMbocQmLuFTYsiD73u1j](https://planaria.network/@1HcBPzWoKDL2FhCMbocQmLuFTYsiD73u1j)**

# [Bitcoin Op\_RETURN Bytecode or BOB](#toc.xhtml#s196a)

Bitcoin transactions are stored as bytes and from BitDB till neon Planaria, the common way was to deserialize the transaction bytes into a JSON-like document object format called TXO or transaction object format.

Bob is another way to format the transactions which adopt the tape metaphor which treats `OP_RETURN` data as a procedure call. Before we understand what it means, let us look at the basics.

# [TXO](#toc.xhtml#s197a)

As we have seen in the last chapter when we discussed BitDB and BitQuery, the approach taken was to convert the string of bytes in a transaction to a JSON like a format. What that did was added tags to each byte which is present in the transaction, so we can say it is an approach to deserialize data in the Bitcoin transaction and structure it with tags to convert it into a document format so that it is easy to read and query. A typical transaction once formatted into JSON/BitQuery format looks as it is shown in the picture below:

![](images/Figure-10.5.jpg)

**Figure 10.5:** A TXO format transaction, image source: [https://github.com/interplanaria/txo](https://github.com/interplanaria/txo)

Detailed understanding and formatting for TXO format can be looked into at the below GitHub link along with installation details:

**[https://github.com/interplanaria/txo](https://github.com/interplanaria/txo)**

On a high level, a transaction gets transformed to below-described format:

**Transaction:** { Tx {}, Blk{}, in{}, Out{} }

**Scripts:** in contains the input scripts

              out contains output scripts

**Graph:** The input and output scripts are represented via arrays with an attribute called e ("edge") which contains the graph structure of each transaction, similar to edge concept used in metanet.

**in.e:** or "incoming edge" is the previously linked transaction. in contains 1-n input scripts

**out.e:** "outgoing edge" is the next linked transaction. out contains 1-n output scripts

Now the scripts themselves are also structured with tags which are common for either, and described below:

*   **i:** Index of the current script (input or output) within its parent transaction.
*   **b0, b1, b2, … and lb0, lb1, lb2, …:** base64 encoded representation of each push data. "b" variable is used normally and "lb" is used when the pushdata size is more than 512 bytes. There are two rules:  
    *   If a push data is an opcode, it's stored as a JSON object with a single key "op" and its value which corresponds to Bitcoin opcode (Bitcoin opcode table) - (Example: { "b0": { "op": 106 } } is an OP\_RETURN opcode)
    *   If a push data is a non-opcode, it's stored as a base64 encoded string.
*   **s0, s1, s2, … and ls0, ls1, ls2, …:** UTF8 encoded representation of each push data. "s" variable is used normally and "ls" is used when the pushdata size is more than 512 bytes. Used for full text search as well as simple string matching. Only stored if the push data is not an opcode.
*   **str:** Full string representation of the script
*   **e:** (for inputs) Stands for "graph edge". An array of previous outputs linking to the current transaction.  
    *   **h:** The hash of the transaction that contains the previous output.
    *   **i:** The index of the previous output within its transaction output set.
    *   **a:** The sender address in case it can be parsed into an address
*   **e:** (for outputs) Stands for "graph edge". An array of all outgoing outputs from the current transaction. More in the next section.  
    *   **v:** The number of satoshis sent
    *   **i:** The output index within the transaction
    *   **a:** The receiver address if the output is linking to an address

For understanding more on the notations for large, you can refer to Unriter's article on this subject: **[https://medium.com/@\_unwriter/l-is-for-large-6e632280c5e3](https://medium.com/@_unwriter/l-is-for-large-6e632280c5e3)**

Bitcom and Bitcom pipeline typically will introduce a protocol identifier as we have seen in *[Chapter 8: Bitcom and Other Application Protocols](#c08.xhtml)* and to be able to support querying and filtering of the transaction using these protocol identifiers, it was needed that a new format is devised which can support the Bitcom Unix pipeline natively including the cases where a dynamic length pipeline is used like `MAP` where the protocol itself has the variable number of arguments. An example of this is shown below which has used B://, MAP, and API protocols brought together using the Unix pipeline for `OP_RETURN`:

![](images/Figure-10.6.jpg)

**Figure 10.6:** Example of a transaction OP\_RETURN with multiple protocols

BOB was created to be exactly that. It provides a data structure schema for being able to structure and tag multiple protocol identities for `OP_RETURN`.

# [Introducing BOB](#toc.xhtml#s198a)

BOB or Bitcoin `OP_RETURN` byte-code is a schema that treats the `OP_RETURN` outputs not as data but as procedure calls in a positional sort of way, i.e. the first pushdata being the procedure name, and the next remaining set of pushdata being the parameters for that procedure.

A typical procedure looks like `Procedure_name (parameter 1, parameter 2, …).` To implement this on the `OP_RETURN`, we go back to the idea we discussed earlier of tape but this time not the blockchain or bitbus with the transaction as one unit of tape, but each of the parameters in the `OP_RETURN` used as one cell of the tape as shown in the below diagram:

![](images/Figure-10.7.jpg)

**Figure 10.7:** Tape typically can be used to build an abstract computer

In this model, we will be using a cell as a single unit of computation while tape provides the set of computations that this abstract computer will do. Similar to that, if we treat the output and input scripts as tape and each of the cells as one single computation for a protocol, the script in the *[Figure 10.6](#c10.xhtml#fig10_6)* now comprises 4 cells as shown in *[Figure 10.8](#c10.xhtml#fig10_8)* below:

![](images/Figure-10.8.jpg)

**Figure 10.8:** Output script as a tape

Each cell above represents a procedure call, so basically using the Bitcom protocol based Bitcoin address as shown above (19HxigV4QyBv3tHpQVcUEQyq1pzZVdoAut = B:\\\\ protocol Bitcoin identifier ) tells which procedure (protocol) is used, and the pushdata which that the protocol uses can be represented as the arguments this procedure takes in. This is the BOB structure or format. It stores Bitcoin transactions in a tape+cell format as shown below:

`tape := [`

`{`

`cell: [`

` {op:0,ops:"OP_0","ii":0,"i":0},`

` {op:106,ops:"OP_RETURN","ii":1,"i":1}`

`]`

`},`

`{`

`cell: [`

` {s:"19HxigV4QyBv3tHpQVcUEQyq1pzZVdoAut","ii":2,"i":0},`

` {b:<file-base64>,s: <file-utf8>,"ii":3,"i":1},`

` {b:<mediatype-base64>,s:<mediatype-utf8>,"ii":4,"i":2},`

` {b:<encoding-base64>,s:<encoding-utf8>,"ii":5,"i":3},`

` {b:<filename-base64>,s:<filename-utf8>,"ii":6,"i":4}`

`]`

`},`

`{`

`cell: [`

` {s:"1PuQa7K62MiKCtssSLKy1kh56WWU7MtUR5","ii":8,"i":0},`

` {s:"name","ii":9,"i":1},`

` {s:"Heuristically Programmed ALgorithmic Computer","ii":10,"i":2}`

`]`

`},`

`{`

`cell: [`

` {s:"15PciHG22SNLQJXMoSUaWVi7WSqc7hCfva","ii":12,"i":0},`

` {s:"BITCOIN_ECDSA","ii":13,"i":1},`

` {s:…,"ii":14,"i":2}`

`]`

`}`

`]`

Bob moves away from many limitations of TXO format and removes some information (like str) which was redundant. In doing so, BOB can let you filter transactions based on protocol prefix, building complex queries with local or global positions/tags used for search, and removing a user to worry about the correct usage in `OP_ FALSE OP_RETURN` as post genesis the usage (unlike today) will go back to using as it was originally intended (as a return statement in execution) and not for data storage as it has been used in the last many years. More details about BOB and actual query node is available via the excellent writeup by Unwriter: **[https://medium.com/@\_unwriter/hello-bob-94701d278afb](https://medium.com/@_unwriter/hello-bob-94701d278afb)**

# [Bitcoin Processing Unit (BPU)](#toc.xhtml#s199a)

BPU is a library to create your custom BOB like nested structures of tape and cells from bitcoin transactions. It can be thought of as a form of a generic version of BOB where the user gets more freedom to define the tape and cell structure. It can cater to large use cases of building integration components for e.g. To connect to a local enterprise ERP system or a host system.

More details can be read at the creator's GitHub page:

**[https://github.com/interplanaria/bpu](https://github.com/interplanaria/bpu)**

# [Metanet Object Model (MOM)](#toc.xhtml#s200a)

Now that we have discussed BOB and how multiple protocols can be used for one transaction, it is but logical to integrate Metanet protocol with planaria or any other protocol using this idea. With BOB allowing the query to handle multiple protocols, we can easily now do so. Metanet object model or MOM is exactly that. If you remember from *[Chapter 7: Metanet Protocol: Data Structures on Bitcoin](#c07.xhtml)* where we discussed metanet protocol, what it needs is just the basic inclusion of metanet keywords in the output script as shown in *[Figure 10.9](#c10.xhtml#fig10_9):*

![](images/Figure-10.9.jpg)

**Figure 10.9:** Metanet protocol spec for a transaction (node)

The specification above mentions the mandatory fields for the node and the edge will be created with the child nodes. The subprotocol identifier will enable using any other protocol like Bitcom or `MAP` and still using the data structure of metanet with it. So the same transaction we saw in *[Figure 10.6](#c10.xhtml#fig10_6)* can now become a metanet enabled transaction just by adding metanet attributes to it as shown below in *[Figure 10.10](#c10.xhtml#fig10_10):*

![](images/Figure-10.10.jpg)

**Figure 10.10:** Metanet transaction along with other sub-protocols. Image Source: [https://medium.com/@\_unwriter/mom-8ef894910e63](https://medium.com/@_unwriter/mom-8ef894910e63)

Please note that the pipe symbol is always ignored by both BOB and MOM when queries are made. MOM is a combination of the two:

*   **Data Structure:** Metanet Planaria
*   **Data Schema:** BOB Planaria

This way of structuring applications will enable them to use both, BOB queries and also metanet queries. To support metanet queries, Unwriter has created a metanet planaria version as well which supports the graph structures of metanet along with traversing and query the subgraphs of metanet structures.

Metanet transactions are already available to see in the neon genesis node of planaria which is the neon planaria version implementation of the genesis bitdb node. The special thing about neon genesis node is that it can traverse transactions across blocks and allows them to query them irrespective of which block they are in. It allows for something called topological transaction ordering of transactions.

Let us take these concepts one by one starting with Neon Genesis.

# [Neon Genesis](#toc.xhtml#s201a)

Time in the Bitcoin world flows a bit differently than in the real world. I can do multiple transactions but they will become valid only once a block containing them is added to the blockchain. This kind of makes a block (or 10 mins) a single unit of time in the Bitcoin world and everything that happens in a block can be considered to have happened simultaneously. What this means is that the Unix timestamp in all the transactions that are present in a block have the same timestamp. But again this creates a situation that each miner who is preparing the candidate block will have a different timestamp for the transactions and also a different ordering of transactions inside the block. Unwriter has made a fabulous explanation of this using the Schoridenger's cat metaphor with multiple alternate realities existing for a transaction (inside each miner's block) until a final commit happens when the block is agreed upon by all miners and is committed to the blockchain. This is when the finality of the state of transactions happen along with the assignment of a Unix timestamp for that block. You can read more details about it at the original author's blog: **[https://medium.com/@\_unwriter/neon-genesis-387fd2f122de](https://medium.com/@_unwriter/neon-genesis-387fd2f122de)**

What neon genesis does is, it supports transaction topology, which is a relative timeline, and provides a method to access transactions using this relative timeline.

Quoting Unwriter –

*"Until now, there have been three chronological ways to sort transactions throughout various Planarian nodes:*

*   *Block Time: blk.t in Genesis, Babel, etc.*
*   *Block Height: blk.i in Genesis, Babel, etc.*
*   *Real-World Time: timestamp in Chronos*

*Note that blk.t and timestamp are absolute times, whereas blk.i is relative time"*

The detailed explanation of the concept behind topology and how that creates a causal relationship between the transaction and order of transaction is explained in detail in the above-mentioned link, but the crux of the matter is that when you order the transaction in such a manner, associating a time component with them, you can now query transaction going across the blocks by using the index (i). This creates a sorted transaction list ready to be used using a simple query spanning across the blocks avoiding the need for handling block index and transaction inside separately.

This can be used to create time-based social media feed, logs, or any application feature which requires timeline-based ordering.

# [Metanet Planaria](#toc.xhtml#s202a)

Metanet Planaria, as the name suggests, is a component/node which acts in between the application and Bitcoin blockchain keeping itself synchronized with blockchain at all time serving all metanet transactions (Meta protocol transactions). Metanet in its usage has two parts:

1.  Data provider
2.  SPV (simple payment verification) for verification of data authenticity.

*[Figure 10.11](#c10.xhtml#fig10_11)* below is taken straight from the metanet presentation present at the creator's website (`nchain`) which describes the above-mentioned functionality from the perspective of application architecture.

**[https://nchain.com/app/uploads/2019/06/The-Metanet-Coingeek-Toronto-29-05-2019.pdf](https://nchain.com/app/uploads/2019/06/The-Metanet-Coingeek-Toronto-29-05-2019.pdf)**

![](images/Figure-10.11.jpg)

**Figure 10.11:** Metanet working as an application cloud storage. Image source nChain(2019)

The database shown in the above figure is where metanet planaria come in. It is exactly the data store shown in the above figure. It does two things:

*   **Only Indexes Metanet:** All meta prefixed transactions and nothing more.
*   **Graph traversal**: Ability to only query a subgraph of the Metanet.

This means you'll get the global Metanet from the metanet planaria when you simply query:

`{`

`"v": 3,`

`"q": {`

`"find": {}`

`}`

`}`

And with the domain separation aspect of metanet, the same can be done using a metanet version of Bitquery which enables searching metanet transactions using not just the meta protocol ID, but also traversing subgraph or child nodes with below-mentioned syntax.

It selects a node by any of its three attributes:

*   **"a":** address
*   **"tx":** transaction\_id
*   **"id":** H(address||transaction\_id)

More details of Metanet planaria can be found at the source link: **[https://medium.com/@\_unwriter/the-metanet-starts-84f255a65782](https://medium.com/@_unwriter/the-metanet-starts-84f255a65782)**

With that background, we can go back to talking about MOM, which is metanet planaria which supports BOB format for query and transaction schema.

*BOB + Metanet = MOM*

This merging of Bitcom and Metanet creates numerous possible protocol combinations ending up leaving for imagination and creation as the possibility. All this with meta *protocol* attributes of graph structure and identity and domain structuring creates perfect tools for creating a backend of a new generation of internet applications where the parent can be using one set of Meta+bitcom protocol and child nodes using another combination of meta+bitcom protocols.

The other glaring benefit that MOM allows is of multi-inheritance making, apart from procedure calls schema of BOB, Bitcom can work like modules that you inherit from. This is similar to the concept of protocols in object-oriented programming languages. Just like we can instantiate two views from a class and create a meaningful link between the two, we can instantiate a data object using Bitcom, and connect them using Metanet. It also allows you to move your existing application by just adding meta prefix (as per metanet specs) and gaining all the benefits of using metanet protocol not even from the start but at any point in time. Metanet also provides for backward compatibility with the usage of `OP_0 OP_RETURN` as we discussed earlier in BOB section, but also makes it future proof for the usage of `OP_PUSHDATA/OP_DROP` options as shown in the below diagram taken from the metanet specs:

![](images/Figure-10.12.jpg)

**Figure 10.12:** Metanet working as an application cloud storage. Image source nChain(2019)

With the genesis upgrade, the above opcodes will be enabled for users to store data and will open up large possibilities for building real serverless storage using Bitcoin blockchain and metanet, in turn creating a new model of building enterprise or consumer-facing applications.

# [Grid Planaria](#toc.xhtml#s203a)

Neon Planaria was a light node version upgrade for planaria base version, and grid planaria is a full node created for heavy-duty infrastructure construction which in turn can host many light nodes. This is something specific for heavy load-bearing enterprise applications. Basically, you can think of this as version 2.0 of the basic planaria which was deconstructed into Grid and Neon planaria, Grid to replace the full node version and neon for lightweight node both focused towards different user cases of building your backend server v/s using a serverless setup.

Grid planaria are the next version by removing a few complexities and becoming simpler in terms of components and code. It removes the docker container coupling as well making it more flexible in terms of containerization, database, and API restrictions.

It uses another library called Bitwork to abstract the data from Bitcoin blockchain to treat Bitcoin like HTTP.

Let us see what bitwork is first in detail.

# [Bitwork](#toc.xhtml#s204a)

Bitwork library converts the low-level networking APIs present in the Bitcoin network (JSON-RPC and P2P protocol) into a unified interface for easy usage:

![](images/Figure-10.13.jpg)

**Figure 10.13:** Bitwork working with blockchain providing read and listen APIs replacing the Bitcoin default methods for better and consistent usability

Bitcoin CLI (command level interface) provides a terminal-like interface to the Bitcoin node if you are running one. This provides a way to use shell commands to interact with the Bitcoin blockchain which is done in background using the JSON-RPC and other networking APIs. Bitcoin original code and the current version supports all commands using Bitcoin CLI and the code can be read through below mentioned GitHub link if you are interested:

**[https://github.com/bitcoin-sv/bitcoin-sv/tree/master/src/rpc](https://github.com/bitcoin-sv/bitcoin-sv/tree/master/src/rpc)**

Since this is quite a low level and more relevant to miners who are running a full node of Bitcoin, we will keep a discussion of this out of the scope of this book, and this is exactly the reason for the creation of the bitwork library. It provides a much more user-friendly interface and methods to access JSON-RPC commands. It also has a built-in data processing engine which parses the incoming transaction byte stream into structured programmable objects which makes programmers' jobs significantly easier.

Bitwork comes with the following APIs:

*   get: fetch data from the blockchain like get mempool transactions, get block, get header (many attributes possible, get JSON-RPC, etc.)
*   on: listen to data from the blockchain (mempool or block e.g.) by creating an event listener
*   use: attach middleware (parsing, filtering, and map or transforming of transactions) You can read the excellent explaining of how to install and create your custom bitwork instances using the tutorial present at the creator's website: **[https://www.bitwork.network/#/](https://www.bitwork.network/#/)**

Moving back to Grid Planaria. I am republishing the excellent analogy published by Unwriter along with the creation of Grid Planaria because it explains entirely the idea and utility of grid planaria by comparing it to the traditional electricity creation and distribution system as shown in *[Figure 10.14](#c10.xhtml#fig10_14)* below:

![](images/Figure-10.14.jpg)

**Figure 10.14:** Grid Planaria powering neon planaria for building applications like electricity grid is powering hope or an enterprise electricity needs (image source: [https://grid.planaria.network/#/](https://grid.planaria.network/#/))

Of course, the actual implementation will be a lot more distributed with multiple grid planaria nodes running as is also the case for electricity distribution systems.

The main features of grid planaria are explained by Unwriter in the documentation as quoted below:

*"Instead of acting as a one-stop shop that aims to take care of everything, Grid Planaria only does what it's good at:*

*   *Event Emitter: Triggers onstart, on-block, onmempool events.*
*   *Progress Tracker: Keeps track of state machine progress with an abstraction called "tape", which works the same way as Neon Planaria.*
*   *Chain Management: Keeps its own cached blockchain which allows for asynchronous streaming based data processing, which keeps the memory usage low and makes everything efficient."*

A detailed implementation guide is also present at the source document which can be referred via the link: **[https://grid.planaria.network/#/](https://grid.planaria.network/#/)**

# [Eventchain](#toc.xhtml#s205a)

Eventchain is an event logging mechanism that monitors, filters, and stores the events on Bitcoin in a file. It is also an append-only log, just like Bitcoin is, and it is self-updating so it is quite lightweight in terms of building code and maintaining it. The file is also a plain text so it is left to the developer to use and format the data the way they want making it compatible with any type of codebase, and database depending on the application needs. You can use it to read events and build your backend any way you wish to, which if you think about it, can be easily integrated into even an existing application which is currently not using Bitcoin but if needed can integrate some features of it to be built using Bitcoin and event processing enabling large possibilities overall. *[Figure 10.15](#c10.xhtml#fig10_15)* below shows overall view of eventchain when used along with other components:

![](images/Figure-10.15.jpg)

**Figure 10.15:** Eventchain used with bitbus for capturing and publishing events from the bitcoin blockchain

Eventchain is as you can see in the above figure, powered by Bitbus, works as a bitcoinless Bitcoin event emitter (no requirement to run full Bitcoin node). It also stores events which give the developer flexibility from the requirement to build event handlers for building state machine backends. It by default uses bitbus so no need for doing the work needed for building bitbus and provides an alternative to planaria. Its architecture is designed with the following qualities in mind, and as described in the product documentation by the creator.

Quoting Unwriter

*"Eventchain is*

*   *Portable: The Eventchain is deliberately stored as a plain text file, there is no complicated system to ensure immutability because that part is taken care of by Bitcoin.*
*   *Robust: If you have been using Bitsocket to filter application specific blockchain events in realtime, you may have wanted a way to store the events first and then process them next, instead of processing them all in realtime in an ephemeral manner. This is what Eventchain lets you do.*
*   *Business Friendly: Because all events are stored first before being processed, businesses can be sure they have all the trace of the events they processed, allowing them to implement accountability.*
*   *Convertible: Currently Eventchain is powered by Bitbus, but in the future it will support both Bitbus AND Bitcoin as host (once Neon Planaria supports this feature), so developers have the option to switch back and forth between running their own Bitcoin full node and using Bitbus."*

In addition to this, it is Language agnostic, purnable, flexible, and easy to reconstruct. You can read through the implementation details at the documentation link present at **[https://e.planaria.network/#/](https://e.planaria.network/#/)**

At the time of writing this book, there is work ongoing to develop Bitbus grid and bitbus grid support for both, neon planaria and Eventchain. But the overall ideas and concepts will remain the same as we have discussed up till now.

The last piece of this planaria framework is a concept which is quite different from what we have been talking up till now and it is so powerful in its own that the use cases single-handedly can cover everything that ethereum, lightning network payment channels, and private blockchains all combined are trying to do. It is another base-level infrastructure (Bitwork and Grid Planaria being the other two) but focused on building a turing complete computational machine or a decentralized computer or a bitcoin analog of a Java virtual machine or ethereum virtual machine. Let's jump right into it.

# [Overpool](#toc.xhtml#s206a)

Overpool is a Turing-complete Decentralized Ledger of Off-chain Bitcoin Transactions. This is an alternative method for doing turing complete computation by using Bitcoin as a replicated state machine. What does this mean, and why is it so powerful?

Almost all software application architecture (SOA, Event-driven) are designed in the form of state machines, where the data store in its current form at any time is in one state, and an event or user action which changes the data stored brings the application to a new state, creating the state transition from one state to another is typically drawn using state machine diagrams and pretty much every application that currently exists can be described using this abstraction:

![](images/Figure-10.16.jpg)

**Figure 10.16:** FSP or Finite-state processes, and the state machine of replica process Source: May, Nicholas & Schmidt, Heinrich (Heinz) & Thomas, Ian. (2009). Service Redundancy Strategies in Service-Oriented Architectures. 383-387.

This calls for a computer that is running an application to be able to perform not just basic instruction sets but also complex functions like looping so as to enable a full-scale functioning for performing complete computations. This is how the ethereum virtual machine works. It uses a full computing machine running on a node to process a JavaScript-like language called **Solidity** which is used to build complex programs like smart contracts. It is due to this exact overhead ethereum is unable to scale beyond a point and the network fees rise when the transaction volume rises. The solution was not to build a full-scale computing node, but do the computing elsewhere and use the main chain for storing computation results but in such a manner that no transaction/computation is lost. This is what Overpool is doing. Coming back to Overpool and why is it a Turing complete distributed off-chain ledger.

Overpool creates an overlay layer on top of Bitcoin, or you can call it a layer 2 solution or a pre-mempool for transactions. What it does is provide a way to create a sub-ledger that uses Bitcoin main chain for clearing and settlement and uses sub-ledger for non-final entries.

![](images/Figure-10.17.jpg)

**Figure 10.17:** Overpool visualization and properties

Overpool provides the crucial point of distribution in the overall grid scheme of planaria that we have discussed earlier. It can be thought of as a microgrid that connects to the bitbus/planaria grid and provides a distribution mechanism to local endpoints. Grid Planaria adopts a top-down approach where it creates a globally distributed Bitcoin data grid from the blockchain. But there is a catch, if you remember, the data on the blockchain can be pruned out creating a situation where the global state is not preserved. Taking an example of BitTorrent, once a torrent loses popularity, the seeders of torrent go away and the data gets lost. Imagine if that can be solved by somehow storing the initial state of a torrent where there are a lot of seeders forever so that the data is available at all times in the future, even though popularity is down or gone. That is the goal of the Planaria grid systems so as to create that resiliency from all future scenarios and maintain the global state of data. If Bitbus/Grid Planaria is a top-down Bitcoin data grid, Overpool is a bottom-up Microgrid.

What this means in our analogy of the electricity grid is that above and beyond the central grid, there is local energy creating sources which then are collated by these microgrids and provide that energy to the central grid in a bottom-up approach adding to the existing centralized energy production sources. These microgrids are self-sustaining, autonomous, and localized electricity sources that connect and synchronize with traditional wide area synchronous grid macrogrid but can also disconnect and work independently as well depending on economic and physical conditions.

Similarly, it is overpool. As we have seen *[Figure 10.17](#c10.xhtml#fig10_17)*, overpool deals with a different state of data and what happens before the transactions have been broadcasted working as a decentralized microgrid. It enables you to create your *local tentative state* before you broadcast the transaction to the blockchain and see it in the mempool.

Quoting Unwriter:

*"It lets you build extremely flexible apps where you may create a state machine out of transactions which have not even been broadcasted, and later update the state again when it's finally broadcasted and mined into a block, by listening to Bitbus. The point is that developers have options to mix and match what makes most sense to them, creating synergy"*

Overpool follows the same tape protocol implemented by other frameworks and systems such as Bitbus, Neon Planaria, and Grid Planaria. By adopting the uniform interface everything can work in concert and create synergy.

However, this doesn't mean Overpool solves everything. After all, it isn't *truth* until it's written on the blockchain. And you still need to broadcast transactions to the blockchain if you want the transaction to get recorded. Furthermore, the *single source of truth* is always the blockchain itself. Also, developers who want to build an aggregation application or need a more holistic view of the blockchain need the Central grid

In another analogy, it allows for a discussion between the two parties in terms of unconfirmed transactions to do back and forth on what is that all parties consider to be the final truth (transaction) and once an agreement is reached, the *truth* or final transaction can be broadcasted to the blockchain.

Let us look at various features of overpool and its internals one by one.

# [Overpool Ledger attributes](#toc.xhtml#s207a)

Main features of the overpool ledger are:

*   Work as a pre-broadcasting transaction storage/repository and
*   Performing turing complete computation

Overpool technically provides a microservice endpoint for users to submit signed or unsigned transactions over HTTP and store them in a file-based ledger. The ledger here acts similar to tape as it does in case of bitbus and planaria, the difference being, there is looping through many interim states of the transaction before it is committed to the *tape*.

When you combine Neon Planaria with Overpool, what you get is a possibility of creating a state machine and ability to create a state only when you are sure that you have reached to the desired state via the *onoverpool*, the event handler. What it does is two main functions:

*   **Looping**: Loop as many times as you want by resubmitting transactions to Overpool from onoverpool handler.
*   **Committing**: Broadcast to Bitcoin inside onoverpool once you're ready to commit.

Commitment happens when the looping is concluded and the final state is ready to be broadcasted. Once that is reached, the commitment is made by broadcasting the final transaction to the Bitcoin blockchain. The process is shown in *[Figure 10.18](#c10.xhtml#fig10_18)* below:

![](images/Figure-10.18.jpg)

**Figure 10.18:** Looping and committing using overpool and planaria. Image Source: [https://overpool.network/#](https://overpool.network/#)

Of course, the overall business logic will be built along with looping when you write code for onoverpool handler, which will decide if the transaction should be ignored, looped, or committed to the blockchain. The committing of the transaction is done using libraries that provide features of building a transaction like:

*   BSV **([https://github.com/moneybutton/bsv](https://github.com/moneybutton/bsv))**
*   Datapay **([https://github.com/unwriter/datapay](https://github.com/unwriter/datapay))**

There are a couple of other protocols made earlier than overpool to handle pre-broadcasting transactions as well that can be looked into to understand more basic ideas like bitpipe which we discussed earlier but worth revisiting at this point as well for better understanding.

*   **Fat URI: [https://github.com/unwriter/faturi](https://github.com/unwriter/faturi)**
*   **Bitpipe: [https://github.com/unwriter/bitpipe](https://github.com/unwriter/bitpipe)**
*   **Bitchat: [https://github.com/unwriter/bitchat](https://github.com/unwriter/bitchat)**
*   **Eli Bot: [https://github.com/unwriter/eli](https://github.com/unwriter/eli)**
*   **Button Page: [https://button.bitdb.network](https://button.bitdb.network)**
*   **BitBtn: [https://bitsent.net/bitbtn.html](https://bitsent.net/bitbtn.html)**

All the above links describe various earlier attempts but overpool adds persistence on top of all those ideas by creating a sub-ledger making it a lot more powerful. Coming to the other attribute of overpool which enables the famed Peer to Peer aspect of Bitcoin is the creation of an overlay P2P network for sharing of the pool (sub-ledger) in a decentralized manner.

Let us know how that works.

BIP270 is a protocol which was developed as a result of a community workshop for establishing a common format for communication between a payment host (usually either a merchant, a payment processor, or simply the recipient's wallet) and their customers (the sender of the funds), enabling both better customer experience, simpler wallet infrastructure, more advanced features such as multiple outputs, and better security against man-in-the-middle attacks on the payment process.

This BIP describes payment protocol messages encoded using JSON, authenticated, and communicated using HTTPS or other authentication systems and communication systems (such as the blockchain itself). Future BIPs might extend this payment protocol to other encodings, PKI systems, or transport protocols.

BIP270 details: **[https://github.com/moneybutton/bips/blob/master/bip-0270.mediawiki](https://github.com/moneybutton/bips/blob/master/bip-0270.mediawiki)**

Overpool is compatible with BIP270, and in fact even more generic (It not only supports signed transactions as suggested by BIP270 but also lets you store even unsigned transactions). *[Figure 10.19](#c10.xhtml#fig10_19)* details the various interactions handled under BIP270 and where overpool will fit in in terms of future usage and adoption of BIP270 protocol for interaction with a larger ecosystem.

![](images/Figure-10.19.jpg)

**Figure 10.19:** Overpool adoption of BIP270 features (for signed transactions)

Coming to the last but the most important feature of overpool, Overpool utilizes DAT protocol to allow each service to share their user transaction pool in a decentralized manner using Distributed Hash Table, which can be used to create a global decentralized overlay network of PRE-BROADCAST Bitcoin Transactions.

You can read more about DAT protocol via the link: **[https://datprotocol.github.io/how-dat-works/](https://datprotocol.github.io/how-dat-works/)**

**Distributed hash table (DHT)** is a distributed and lookup system of Hash and key (key, value) pair published on a common public network and has been quite extensively used in P2P networks like BitTorrent and used to build overlay networks.

Let us look at what this means by looking at a scenario with Alice, Bob, Charlie, and Dave are four developers working on a common codebase and maintaining their versions of code in their respective transaction overpool (A, B, C, and D) which is with themselves. All want to know if anyone of them updates their branch so they subscribe to each others overpool as well. The idea is Only The owners can add new transactions (with updated code) in their overpool but can read other overpools so as to react based on events done by others (code updates).

A similar representation of this is shown in *[Figure 10.20](#c10.xhtml#fig10_20).* The use case is four different SaaS product users who maintain the same code base but for different demographics for a company. They can choose to react or not based on changes made in one demographic (this case A and B). This is just one overly simplified example but there could be many uses of this type of overlay network in terms of creating and maintaining social media feeds, company inter-department communication, etc.:

![](images/Figure-10.20.jpg)

**Figure 10.20:** Various overpools doing discovery and replication of events via connected pools

Quoting Unwriter again, about the benefits of publishing pools:

*" Just to emphasize, publishing your pool may be beneficial because:*

*   *Open API: You can provide an open API endpoint for your own Overpool. With an open approach you can grow the developer ecosystem and bring in more users.*
*   *Efficient API: Since DAT allows for decentralized replication (vs. a server-client replication), the more API usage you get, the more you will save money, since everyone syncing from your Overpool will share the network traffic load.*
*   *Interoperability: You can use Overpool to allow other apps to interact with your app's local state easily."*

Overpool can be used for applications implementing event-driven architectures (pub-sub etc.) and even though right now these ideas and frameworks are still in development, the individual components are ready to be used in production-grade enterprise applications.

Another attempt or a fork of overpool which is a simple implementation to create off-chain bitcoin ledger is Localchain.

# [Localchain](#toc.xhtml#s208a)

Localchain is a simplified and modularized version of overpool, which breaks down some of the features of overpool and focuses only on one thing, maintaining append-only logs of off-chain Bitcoin transactions. Other features like the HTTP server or decentralized replication, etc. which are present in overpool are left for the users to build upon localchain. It only does one thing and does it with minimal code and setup while having the ability to create as many logs as needed and can be used for listening to events from a global log or local logs as user designs and implements it.

More details are present at:

**[https://localchain.planaria.network/#/](https://localchain.planaria.network/#/)**

It is a simpler and modularized version of overpool and more focused on the core function, storing and maintaining an append-only log of off-chain Bitcoin transactions.

# [Closing thoughts](#toc.xhtml#s209a)

These frameworks work together and give the possibility and flexibility of working either ways, top-down central grid (bitcoin -> bitbus), bottom up microgrid (Overpool -> bitcoin) and a combination of both, a hybrid grid as shown in *[Figure 10.21](#c10.xhtml#fig10_21):*

![](images/Figure-10.21.jpg)

**Figure 10.21:** A hybrid grid structure using the best of both (bitcoin -> bitbus and overpool -> bitcoin): image source: **[https://medium.com/@\_unwriter/ip-to-ip-bitcoin-machine-network-eed3414b1b](https://medium.com/@_unwriter/ip-to-ip-bitcoin-machine-network-eed3414b1b)**

The final goal is to create a global Bitcoin data grid that can store a lot of common information like user identity, and user data which can be shared across various applications. Think of those integration components that exist today which let you post on one social media platform (like LinkedIn) and replicate the same over various other platforms (Twitter, Facebook, Instagram, etc.)

Some of the closing thoughts also include infrastructure for IP to IP machine transactions which are described in detail with some wonderful examples by Unwriter in the below-mentioned link. I would highly recommend reading it:

**[https://medium.com/@\_unwriter/ip-to-ip-bitcoin-machine-network-eed3414b1b](https://medium.com/@_unwriter/ip-to-ip-bitcoin-machine-network-eed3414b1b)**

In the world of IoT and machine to machine transactions and communication, these frameworks will play a large role and some of that is described in the above-mentioned article.

# [Conclusion](#toc.xhtml#s210a)

This chapter has gone into some very powerful infrastructure components which will in the future become base for many globally adopted applications and will play a large role in the development of secure (with ECDSA, Bitcoin security infrastructure) internet software for the globe. I had taken a lot of liberty in writing this chapter in terms of using materials from Unwriter's various publications and quoted his text to keep the integrity and intent of his creations as close to what they are created for. Almost all of the framework and protocols are available under open BSV license (except Overpool which is under Open MIT) which enables and gives freedom to anyone who feels there is a better way to do it to take it and create something of their own.

The central idea is that these systems are built for a new age of the internet which is quite different from the current internet which is closed, ad-based, and allows for spam and incorrect information without accountability. The new Internet will be based on truth, security that is unmatched, and unbreakable (if you build the applications right aka Bitcoin's security and ECDSA for data ownership) and open for all. Above all this, if you see the GitHub pages for this framework, and compare the codebase needed in traditional applications, you will see the real benefit of using a common open system like Bitcoin which will change not just the way software development happens currently but also how even small companies with limited resources can compete with large corporations with unlimited resources.

In the next chapter, we will look at various other resources, utilities, and some real-world applications that are built using Bitcoin either for storage (Blockchain as a Service, Database, and storage), microtransactions, or general ledger. These user cases will demonstrate how Bitcoin blockchain can enable and make life easy for application development on Bitcoin blockchain.

# [Questions](#toc.xhtml#s211a)

1.  What is the functionality of planaria nodes which they provide for building applications? What is the query language they use?
2.  What is the difference between TxO and BOB schemes of reading Bitcoin blockchain
3.  What is the benefit of using MOM over BOB and plain TxO?
4.  What are localchain and overpool used for? Will they store transactions on-chain or off-chain?
5.  What is the meaning of the finality of a transaction? Why is it important?
6.  What is BIP270 and what are its main features?

# [CHAPTER 11](#toc.xhtml#c11)

# [Real-world Applications](#toc.xhtml#c11)

**"The task is not to see what has never been seen before, but to think what has never been thought before about what you see every day"**

*\- Erwin Schrodinger*

We have thus far looked at Bitcoin protocol, metanet protocol, and building backend services with planaria and other protocols which enable CRUD operations using Bitcoin as a database with event-driven architectures and building backend services/APIs. The understanding will not be complete until we look at the applications using Bitcoin as storage/backend and look at what real-world applications are doing with this technology. In this chapter, we will look at various business areas and industries and how there are many projects utilizing this technology to build real-world solutions and applications. We will also look at some tools, including various implementations of the Bitcoin code (to support various languages), and libraries which are very useful for developers for building their applications.

# [Structure](#toc.xhtml#s212a)

*   Real-world scenarios, various use cases in real-world applications where applications based on Bitcoin SV can be built along with examples of projects doing so.
*   Nakasendo, BSV, and other libraries
*   Utilities and SDKs (Operate, Scrypt, HandCash connect, mattercloud, etc.)

# [Objective](#toc.xhtml#s213a)

After studying this chapter you will get an overview of various real-world applications that are either already built or being built for consumers, and enterprises that are using various features of the Bitcoin blockchain. You will also learn how usage of a blockchain type system can transform pretty much every industry that exists on the internet today and how the real benefit will be for the users, creators and overall how privacy-related features of Bitcoin can help build a new age of internet applications that are much more secure, reliable, and always available.

# [Real-world applications](#toc.xhtml#s214a)

We have looked at and talked about all the technical and economic aspects of using Bitcoin blockchain till now, but how is it going to change the way application development/Internet is working or being used right now? What is the impact of this new technology?

I will try and address these questions in the remaining chapter now. I will be talking about many startups and companies or even developer projects that are trying to use this technology now on, the intent of which is to show how various ideas we discussed in the book till now are being implemented and not to say that specific implementation is the best. The truth is the same as it is for any technology, 100s of projects will try to implement 100s of ideas, many will succeed and many will not. Let us now jump right into it.

# [Payments](#toc.xhtml#s215a)

The most obvious and common implementation of digital currency or virtual currency is the usage for domestic and cross border payments. The existing payment systems in various countries are based on their native legal tender (native currency) and typically a payment goes through a complex process of initiation, validation, enrichment, and execution, and later on clearing and settlement. This is a large and complex process that becomes more complex when it comes to payments that are done across countries due to the inclusion of legal and anti-money laundering regulations involved for each end (sender and receiver). One of the other big challenges is the schema/structure/format of the payment and other messages involved in this process. There has been excellent advancement with things like ISO20022 standards but still, there is a long way in the adoption of these standards across the world.

Payments are the most obvious use case for Bitcoin blockchain. By the invention, Bitcoin is an electronic cash system, which means that it has a complete payment processing engine built-in using a minimalistic format of these payment transactions (done as a byte stream). It provides for easy and efficient clearing and settlement engine for global payments and the work required by each local financial institution will be to convert the Bitcoin payment message to the local format that they use. It brings great advantages like:

*   Cost of processing payment (cost of operation, infrastructure, etc.) reduced to more than a 1000th of what it is currently
*   Usage of a common infrastructure for payment processing, clearing and settlement will create a globally transparent and auditable system making it much easy to implement AML regulations
*   Complete removal of large IT teams for the development and maintenance of these IT systems in multiple places makes it a highly efficient and energy-saving venture. Think of it as one bank doing all global payment processing, reducing the consumption of electricity by large proportions making it eco-friendly.
*   Huge reduction in the complexity of the overall payment creation, processing, clearing, and settlement (including removal of things like different clearing like TIPS and TARGET2 in European regions e.g.) and simplifying the system by replacing it with an instant payment and settlement system. The only reason there are so much complexity and multiple systems is that the capacity of a clearing and settlement system is limited (maybe millions of transactions) which is easily replaced by Bitcoins scaled version of teranode blocks processing millions of transactions per second.

![](images/Figure-11.1.jpg)

**Figure 11.1:** A traditional common payment processing value chain v/s Bitcoin-based payment (in blue)

*[Figure 11.1](#c11.xhtml#fig11_1)* shows a comparison of the existing payment processing system as compared to what it would be if the same system is implemented using the Bitcoin-based pipeline. Please bear in mind that I have shown only one end to end flow in the existing system, in reality, there are 100s of indirect participants and numerous direct participant banks as well which serve millions of end customers. That would make the same diagram look a lot more complex than what it is right now, but in the case of a Bitcoin-based payment and settlement network, this complexity is reduced as the settlement happens in real-time. In traditional systems, this is done via batching and to reduce the number of transactions to be settled (via a process called netting where bank's positions are netted in terms of transactions they did) before settlement. In the real world, this is the most commonly used and propagated use case for digital currencies. With Bitcoin, there are many companies doing this solution, the most focused one being driveway which is looking to offer this complete end to end clearing and settlement services across the global corridor.

Some projects working on this space are:

**Drivepay: [https://drivepay.com](https://drivepay.com)** for a complete end to end payment clearing and settlement network.

**Centbee: [https://www.centbee.com](https://www.centbee.com)** offering a host of products and services.

**Handcash: [https://www.handcash.io](https://www.handcash.io)**

**RelayX: [https://www.relayx.io](https://www.relayx.io)**

Little Rocket POS and Handcash POS are also products that are being built for POS services and a whole bunch of other projects which are working on both, wallet services and also merchant wallets and Point of Sale applications.

It's not just payments that are transformed using this system. It is the complete financial industry that exists today which can be transformed with this new system for payments, clearing, and settlement. And not just this, it is all of the global financial activity that can benefit, with things like issuing of security tokens and digital currencies on blockchain to a voting system protected by the unmatched ECDSA security that exists (unlike PKI), to issuing of financial derivatives like bonds, shares and the rest, to issuing of something very simple like a movie ticket or a setup for loyalty points. Everything can be done only limited by the imagination and the work that goes behind building such a system.

# [Supply chain management](#toc.xhtml#s216a)

The system currently existing for supply chain management also suffers from similar issues like the ones we have discussed in the previous section related to payments. Typically these systems are also isolated/broken as well apart from other issues like very expensive to build and maintain and not being inclusive for supporting micro deliveries / small value item tracking.

It also includes an implementation of a blockchain-based solution of sharing electronics documents, typically known as EDI or Electronic data interchange, which is typically the secure data exchange network for businesses to exchange automated and other messages needed to execute a trade (orders, deliverance, settlements, custom clearance using various message formats like FTP/CSV, X12, EDIFACT, etc.). A blockchain equivalent of EDI is being built by nChain and is termed as **BDI (blockchain data interchange)** which could enable the complete data exchange between global business in a traceable, secure and using one central system removing all redundancies and siloes requiring a lot of integration making it one seamless experience for global trade.

**UNISOT**: There is one implementation of this being built on Bitcoin blockchain by a Norwegian company called UNISOT. **[https://unisot.com](https://unisot.com)** venturing into this space with a host of products.

The UNISOT *Enterprise Business Network and the UNISOT Collaboration Cockpit* enables a 360° overview of the entire supply chain topology in real-time. Companies will, therefore, be able to proactively react to external information, actions, and issues before it will impact their performance in the supply chain. This will reduce latency and costs considerably. This is a global trade enabling space where there are huge amounts of inefficiencies in the complete process including the paper invoices and again as much complex if not more, systems that are spread across the globe for doing this for various goods container shipments that are transferred across the world.

One of their first products is already launched for tracking seafood from acquiring the fishes till their consumption ensuring full transparency in this supply chain (provenance tracing). It's called the SeafoodChain: **[https://seafoodchain.no/](https://seafoodchain.no/)**

This product enables data-capturing and -monitoring from all parts of this supply chain; from a fisherman's smartphone app or the extraction of data from fish egg production plants – to automatic IoT sensors, Computer Vision, ERP-Plugins, Big Data Analytics, and Machine Learning.

# [Social media](#toc.xhtml#s217a)

The Internet-enabled a change in the way that information is disseminated across the globe by the creation of various digital mediums of expression. From the digital or web-based news and media platforms to social media enabling not just one-way information propagation, but also a voice to individuals across the globe via platforms like Wikipedia, Facebook, and Twitter among many others. It has been so successful that the print medium/newspapers, etc. are almost on the verge of closing down and everything moving to digital mediums. This is a very powerful and large change in behavior but it suffers from one fatal flaw. All of these platforms providing access to everyone for free, but requiring a large number of funds to operate their businesses, required a business model to function which was not present as they were providing their services for free. This made the companies look for something else to earn money and that is where data came into the picture. Take Wikipedia for example, it was one of the first places where everyone started going in the initial days of the internet to know about various topics or events. According to the annual reports published by the Wikimedia Foundation, the total expenses for 2011-2012 were about $27.2 Mn. How does Wikipedia make money to raise the funds to operate? They adopted a model of seeking donations from users for raising the funds to operate, and they are a non-profit organization. What happens when this is taken to for-profit public companies like Facebook and Twitter. The way these companies started to raise funds was not via donations but advertising on their platforms. In fact, as of today, they consider themselves as digital marketing companies who have a very large user base and businesses pay money to promote them on these platforms. This model has created a situation where user privacy is non-existent and most times the users are being treated as a product (by users I mean user data) and sold to advertising companies and middlemen who use the data for targeted advertising.

What if the model can be turned upside down? Where users who create the data are the owners of the data and the platform gets paid when users use the platform services for any user actions? This is possible only if there is a way to enable very small payments or as they are called micropayments that follow every user action. This raises two main challenges: a payment system that can handle this large number of microtransactions (billions of user actions will generate billions of microtransactions every hour/day) and a security system that can provide users the ownership of the data on micro-level keeping the privacy of users intact. It is obvious to say that Bitcoin does solve both of these challenges and it is pretty good at it (metanet domain hierarchy, large blocks with millions of TPS enabling large numbers of microtransactions).

There are many applications being developed doing exactly this using Bitcoin blockchain. Let's look at some of them:

*   **Twetch**: Twetch is a social media platform which is enabling users to take control of their data by publishing every user-created content on a blockchain via a transaction. **([https://www.twetch.app/](https://www.twetch.app/)).** Needless to say, it involves a small payment to be done for all types of user actions like posting a message, picture or meme, liking it, replying to the post, and branching a post. All users who are involved with a post get paid for every new further interaction.
*   **BitQ&A:** BitQ&A is a content creation platform that enables users to post questions and answer questions involving small payments. Users seeking answers can place a bounty for the right/good answer and the users answering gets the bounty if their answer is accepted by the user who has put out the question **([https://bitqa.app/](https://bitqa.app/)).**
    
    **Bitstagram**: Bitstagram is an open-source POC which enables users to post a picture. Obviously, since it was a proof of concept it never has gone into a complete development stage, but it did show how easy and lightweight code can build a large functioning application on the blockchain. **([https://bitstagram.bitdb.network/](https://bitstagram.bitdb.network/)).**
    
*   **Metalens Extension:** This is a browser extension that lets you post a comment on any website. All the comments will be stored on the blockchain: **https://chrome.google.com/webstore/detail/metalens-extension/odoinflckdonpofihlicjjknlgnhhaem**
*   **Open directory**: Open directory was one of the first applications that were released which are fully built using BSV blockchain as backend. It is a way for organizing links on the Bitcoin blockchain and can be thought of like a craigslist or a Reddit but in addition to the functional aspect of it, it was built as an information system with an incentive system built in which will keep engaging users with chain tips for user engagement like upvotes, cascading tip to all of the contributors. It is one of the most interesting examples of building an incentive system for a social media platform. It is also open source so you can always spin-off your version using the codebase and experiment to make your application. It uses react for frontend and bitcom, planaria, B:\\\\, and moneybutton for various CRUD operations with Bitcoin blockchain (**[https://dir.sv/](https://dir.sv/)**).
*   **True Reviews:** we see many traditional review websites and a lot of online purchases and even something like Yelp which is heavily dependent on user reviews of businesses. The only flip side is that users do not have any incentive, to be honest in their reviews nor are they incentivized to post a review. TrueReview project is trying to solve this problem. It is a platform that incentivizes users to post reviews of any place that is available on Google Maps. Every review is stored on blockchain so it is possible to not just post a permanent review but also adds to the accountability of users who post the reviews. This provides an honest alternative to the problem of paid review postings, and user accountability and credibility and overall enhancing the experience of reviews for a business and also for users who are consuming the reviews by maintaining a tokenized reputation system. (**[https://truereviews.io](https://truereviews.io)**).
*   **Freelancing**: Showjob and Fivebucks : they both are a freelancing platform for jobs and hiring freelancers where you can pay people using BSV. **[https://www.showjob.app](https://www.showjob.app) and [https://fivebucks.com/](https://fivebucks.com/)**
*   **Webpage Archival:** It can be easily done using a moneybutton paywall as used in **[https://pageshot.bitcoinsv.si](https://pageshot.bitcoinsv.si)** for doing a screenshot for a web page or **[http://codeonchain.network](http://codeonchain.network)** which allows you to store your codebase on the blockchain. All of these utilities use moneybutton as the payment gateway and it is quite simple to use and build.

# [Content creation](#toc.xhtml#s218a)

Creating a paywall or pay per use model where the money goes directly to the content creator is a very large opportunity and use case which can enable decentralization of platforms to directly pay to people who are doing the real work rather than giving a large share to the platform provider. Yours.org and Literatus: These are two experiments with creating a blogging platform with the incentive system using Bitcoin microtransactions built-in. (**[https://www.yours.org/](https://www.yours.org/) and [https://en.literatus.org/](https://en.literatus.org/)**).

Mediopay and Anypay provide a service to have a payment gateway for your businesses created on Wordpress and WooCommerce website creation platforms. **[https://www.mediopay.com/](https://www.mediopay.com/)** and **[https://anypayinc.com](https://anypayinc.com)**

Another such implementation is Bit SV **([https://bit.sv](https://bit.sv))** which is another platform being built for content creators and their audiences both incentivized for using the platform. It will allow for collaboration and curation or signal boosting the existing content by sharing and becoming a content promoter.

There are many more examples that have projects that are either built which are similar to existing applications with an incentive model of micropayments built-in or something which does not exist right now like pay per view or pay as you watch model of streamanity. Space currently is budding with lot of project ideas which are being explored and if we see, almost all of the internet giants (Facebook, Google, Amazon, etc.) are companies that did not exist 20 years ago and are now the largest companies across the world, I expect to see a similar scope for right businesses that are built on Bitcoin blockchain as infrastructure and financial transactions infrastructure.

# [Advertising](#toc.xhtml#s219a)

Bitcoin blockchain cannot just be a boon for the content creators but also the businesses that are currently spending a huge amount on marketing and advertising to be able to reach an audience. All of these businesses have to pay multiple middlemen for reaching out to potential audiences which can be changed using microtransaction based advertising model where if not other things, users can get paid to consume the advertising while they browse their favorite websites:

*   **TonicPow:** It is a unique advertising platform built with integrated micropayments infrastructure where advertisers can post bounties for user engagements, and promoters can share those links to earn. The complete technical platform is free, and the creators who need advertising can put the bounties which the promoters share in their social network or any other platforms to get users to use/view the content. All three, content creator, promoter and the platform earns revenue by a share of the earnings and enables users to directly connect with advertisers and more: 
    
    **[https://tonicpow.com](https://tonicpow.com)**
    
*   **Marketplaces**: Things like **[https://classifiedsv.com](https://classifiedsv.com)** or 
    
    **[https://www.zeroconfs.com](https://www.zeroconfs.com)** which are using Bitcoin as money for payments of their product offerings.
    

A completely different kind of implementation of using blockchain was done by another project called **CityOnChain** which is providing a physical to blockchain city space association and making these cities across the world available for trade and advertising for users to connect. Even though right now there is not so much of actual trade happening but this is similar to an implementation of craigslist on blockchain but in place of all city advertising space controlled by a central entity, it is controlled by users who purchase the city rights on the platform and all this is tracked using Bitcoin blockchain for an immutable registration:

**[https://cityonchain.com](https://cityonchain.com)**

A very similar idea, but not so much focused on advertising, but the overall creation of a metanet layer on top of the physical world is called **Metavibe**. This is quite an ambitious project and details are present at their GitHub page for interested readers/developers: **[https://github.com/Kohze/Metavibe](https://github.com/Kohze/Metavibe)**

# [Gaming and gambling](#toc.xhtml#s220a)

Gaming is another space that is kind of something that has been always experimenting with virtual coins or loyalty points apart from many of these games having an inbuilt marketplace for gaming accessories. Casinos still use their casino tokens or chips which are redeemable only at their casinos to represent real money. When these physical Casinos go online, they have huge regulatory and legal requirements to meet when it comes to issuing such a digitalized version of physical tokens. This is where Bitcoin provides an ideal platform for the gaming industry. Micropayments in combination with legal and absolute record keeping of all user transactions enable legal gaming and casinos to be built using the Bitcoin blockchain public ledger. If we look at it, after the financial industry, the gaming industry is another space that is very heavily regulated and has to comply with a large set of regulatory and compliance needs (recordkeeping, archival, KYC) just to keep afloat.

Before we go further, if we see how that industry currently looks, we can see many places or use cases where Bitcoin blockchain can be used. Known as iGaming or Internet Gaming, the industry has flourished and expanded with various online and social media platforms made available by being online. Typically the iGaming industry is classified into the below-mentioned types:

*   Sports betting
*   Casino games
*   Poker
*   Bingo
*   Lottery
*   Horse racing betting
*   Mobile gambling

Usage of something like Bitcoin blockchain stands to change this industry altogether with the support of highly secure, KYC enabled instant microtransactions, low fee, and a global network that is available and resilient. The early version of Bitcoin code had a marketplace and poker game built-in which says that it was always the intent that Bitcoin is an ideal solution for the gaming industry. The public ledger of all transactions enables many properties for online auditing of records making it quite easy for governments and regulators to audit, monitor, and license gaming and gambling activities of companies and get their tax payments instantly rather than waiting for the end of the month, quarter, or year. Some of the benefits that are unmatched with the current system are:

*   Online gaming operations can get their random number generators tested and audited by licensing bodies to prove the fairness of their gaming system.
*   Publishing of all records in a public blockchain further reduces the motive to cheat as these records will be immutable entries open for validating not just once but anytime in the future.
*   Automating the complete audit process using oracle systems and automated smart contracts.

There are multiple companies on creating iGaming systems/applications on a small scale to large gaming enterprise software. They are using various utilities and properties of Bitcoin blockchain (an example is a random hash of a block that is generated when a new block is added providing a provably fair random number). Let's look at various implementations of this gaming software which are currently ongoing, some released some under development. The ruleset and overall gaming events are again stored on the blockchain making them fully transparent to the users who will be putting a significant amount of money on these bets giving them the ultimate provable confirmation of fairness and honesty of the gaming application:

*   **Kronoverse** : Kronoverse is a complete gaming platform being built with Bitcoin SV being the system of records for various user attributes like identity management, game management, funds/key management, smart contracts (using RUN tokenization framework) and much more written in standard JavaScript. It also provides a lot of automation for configuration and management using bots and oracles. This platform also uses payment channels for providing ultra-fast transaction speed and instant validation to match gaming needs. Above all, it will also integrate with Unity framework, web, iOS, and Android. 
    
    This platform will be available for developers to build games upon when released. The same company is building its own multiplayer role-play game called CryptoFights which will show their platform's capabilities and more. More details at **[https://www.kronoverse.io/](https://www.kronoverse.io/)**
    
*   **BitBoss**: Another company working on gaming and specific solutions for iGaming gambling and casino industry is Bitboss. They have built a wallet along with the integration of token solutions to be used in various platforms using another tokenization framework called Tokenized. The company is also building its own block explorer focused on its own gaming transaction user interface. They have various technology solutions built for various iGaming classifications we saw above and more details are present at **[https://bitboss.io](https://bitboss.io)**

There are various other gambling projects that have come about which are using Bitcoin blockchain for funds movement, randomness generation, rules and results in documentation and storage and fairness of the platform like Peergame a provably fair online casino running on Bitcoin blockchain with many game options for users to bet on and play. Many other platforms are there which provide poker and other games with not just Bitcoin but other cryptocurrencies as well but not all of them will have a fully legal and regulatory framework integrated as the professional platforms like Kronoverse and Bitboss we discussed above.

# [Health care](#toc.xhtml#s221a)

One of the industries that work with and produces the largest amount of data as critical as the lives of real human beings depending on it is the healthcare industry. Big data infrastructure needs for something like DNA sequencing is being seeked after more than ever. In addition to that, there are real issues that the world is facing today like the opioid crisis where the distributed silos of patient information and a patient seeing different doctors being prone to be prescribed medicines which can adversely affect their overall system due to non-compatibility of medicines that person intakes for different ailments.

When it comes to healthcare, a system of record which enables storing of all prescriptions given to a patient will bring a lot of benefits to provide the patient's history of medication to a doctor who is sitting in front of a patient prescribing him/her a new set of medication for an ailment. This also makes it but obvious that a global health record database for all patients will be another huge use case for a Bitcoin-like blockchain which not only creates a single source of truth about medical history for a patient but also provides unmatched security and privacy with the confidence that their data cannot be sold to other companies like it currently happens when this data is existing in siloes. Using Metanet's hierarchical ownership structure, a patient cannot just own his data but also now provides another opportunity for patients across the world to participate in with only the needed data in clinical trials with pharma companies and earn money from it rather than the company who sells their data and makes money off it.

Currently, nChain is working with a leading pharmacy software development company called EHR data to create solutions to the above use cases I have described. You can see how these use cases are such badly needed systems in the current healthcare industry and it is only patients who will immensely benefit from such a system. You can read more about it at **[https://ehrdata.com](https://ehrdata.com).**

# [Business infrastructure](#toc.xhtml#s222a)

There are a lot of use cases where the traditional solutions can be replaced by usage of the blockchain/ledger and various other aspects of Bitcoin like identity management and microtransactions. We explore more here on various aspects of a business infrastructure that can be applied not just to the industries mentioned below, but any business that is using the Internet for its infrastructure.

# [Document management](#toc.xhtml#s223a)

Using a platform like Bitcoin blockchain for enterprise data store and archival is a very large use case for reducing the cost of operations for any business. In addition to that, clubbing it with the business data storage capabilities provides another large use case for businesses. One of the implementations of this use case is **[https://legallychained.com](https://legallychained.com)** which provides the solution built on metanet.

# [PIMS and CMS](#toc.xhtml#s224a)

Another large use case for SME segment businesses is Product information management systems and content management systems. Again clubbed with metanet and Bitcoinc's native data and file storage capabilities, these use cases can be implemented on it.

# [PaaS](#toc.xhtml#s225a)

We have seen planaria grid infrastructure which aims to be a full-scale PaaS for building enterprise IT applications on the Bitcoin blockchain. HandCash connect offers a similar service for app developers abstracting most of the Bitcoin functionality underneath so that the app developers can focus on only the App and not the Bitcoin-related development.

# [IaaS](#toc.xhtml#s226a)

Cloud infrastructure can also be built on Bitcoin blockchain and one of the projects doing that is mattercloud: **[https://www.mattercloud.net](https://www.mattercloud.net)**

# [E-commerce platforms](#toc.xhtml#s227a)

Salesforce is a large infrastructure provider for a large number of businesses running their e-commerce business and this is a very large use case for enterprises to use as using a Bitcoin blockchain can enable huge cost savings in terms of running a long term e-commerce application.

Media and entertainment

Needless to say, when you can store files, and monetize them, on a micro-level, this provides the ideal platform for the media and entertainment industry. The use case is straightforward and many projects and businesses are currently starting to realize the potential of using Bitcoin blockchain for these use cases. Some of the implementations are:

*   **Audiob** **([https://www.audiob.app](https://www.audiob.app)):** Audiob is a platform for independent artists and podcasters for publishing their original works and earn money via micropayments from their audience.
*   **Streamanity ([https://streamanity.com/](https://streamanity.com/)):** This is a video hosting platform that enables users to post video content and the viewers get changed for watching the videos in microtransactions based on how many seconds of a particular video they have watched.

Similar to audio, videos can be uploaded too and with the pushdata opcodes you can now upload up to 4 GB of file size in one transaction. It will now be possible for independent artists to publish their videos on the Bitcoin blockchain as well and monetize it. One of the implementations as an alternative for video streaming platforms is still not uploading videos on-chain as of now, but that I suppose they will do once some of the storage cost comes down. As at the time I write, the cost is 0.5 Satoshi per byte of data set by miners, but when the miner competition starts, it is expected that this cost will come down drastically.

# [News and digital publications](#toc.xhtml#s228a)

Since content can be published and monetized on a blockchain, this provides a unique opportunity for news and digital media companies for disrupting and reinventing their businesses. Most of these companies currently are using advertising for the revenue for the content in terms of news that they publish, which they can change to a new model of pay per view using the microtransactions capabilities of Bitcoin blockchain.

# [Data storage](#toc.xhtml#s229a)

Needless to say, the Bitcoin blockchain is perfect to store files. There are many applications and tools that can be used to do so, some we have seen (storing using B, C protocol) but there are many services that use the mentioned protocols to store files on the blockchain:

**Bico.Media: [https://bico.media](https://bico.media)**

Bico.Media was one of the first utilities/services made available for Bitcoin blockchain which can be used to store data/files on the using a varied set of protocols. It also provides easy access to files, and its static data while providing a dynamic experience by combining, joining, and merging content.

Bico.Media is actively involved in driving the process of maturing the description of the following initiatives and protocols:

*   Inject content from one transaction into another with B://inject
*   Muctache templating for blockchain content and data B://eard
*   Liquid templating for blockchain content and data B://iquid
*   Update content but keep the same URL with B://ynamic
*   Concatenate content from the blockchain with B://cat
*   Embracing templating engines with B://emplate
*   Keeping content off the grid with Metapoint

All of the Bico.Media services are using moneybutton as the method of payment for transactions and fees to store data on the blockchain.

**Bitpaste: [https://www.bitpaste.app](https://www.bitpaste.app)**

Bitpaste is an easy and simple interface service to store text (write text online as well), files, and code using moneybutton on the Bitcoin blockchain.

**Preserve: [https://preserve.bitpaste.app/getting-started](https://preserve.bitpaste.app/getting-started)**

Preserve provides a CLI based tool to deploy HTML pages, static assets, and entire websites to the Bitcoin blockchain.

**Etched: [https://etched.page](https://etched.page)**

Etched is an internet archival tool that permanently timestamps and stores web pages on the Bitcoin blockchain. The difference from traditional web archival methods compared to etched is that the website is stored permanently even if ethed (third-party) shuts down, the archived data will be available.

**Immortalize:**

**E-cat: [https://beta.ecat.media](https://beta.ecat.media)**

E-cat is an immutable, and encrypted file storage solution on the Bitcoin blockchain. E-cat protocol does a little more than storing the files by encrypting them, but it also allows for the sharing of this encrypted data for non-technical users (focused on artists and content creators) by tokenizing the file/data/content. This allows them to manage what type of access they grant to their consumers. Pay per stream, download, and give one time access to a file and many more access types are possible. It also prevents unauthorized access to the file content.

It provides easy to use interfaces for creating sales channels to distribute your content globally.

# [Micropayments](#toc.xhtml#s230a)

Peer to peer micropayments enables a completely new kind of incentive and non-existing ecosystem which was not possible before Bitcoin. We will discuss a lot of these use cases in the next section, *[Chapter 14: Going into Future: AI/ML, Big Data, and IoT](#c14.xhtml)*, where we talk about AI, Big Data, and IoT which is pretty much the ideal use cases for using a blockchain-based system. In the sections above, we have looked at most of the existing businesses that can hugely benefit using Bitcoin-based microtransactions already so will not look at those again but there are many new projects like Codugh **([https://www.codugh.com/](https://www.codugh.com/))** which is an API marketplace where developers can publish their APIs and monetize them using these micropayments/microtransactions. All you have to do is publish your APIs endpoints on the Codugh marketplace and you can get paid for each call that is made for your APIs by anyone. Another example of such a new kind of business is Bitping **([https://bitping.com/](https://bitping.com/)),** which is a distributed crowdsource network intelligence and monitoring system where the data is collected from real global user base who are running the bitping nodes for participating in this system and getting paid in microtransactions for running these nodes. These nodes are available to run, both for individual users and for enterprises.

All of the above use cases that we have been discussing are the traditional businesses that exist today and how they can disrupt and reinvent themselves to become more cost-effective in business operations cost, IT infrastructure cost and overall benefit to users where their data is not used for target advertising making them a product improving the user experiences multifold. I am sure I have not covered every industry that exists today but the idea was to give a view of how everything that currently is built on the internet can exist in a much more evolved manner using an immutable blockchain like Bitcoin and microtransactions.

# [Utilities and SDK](#toc.xhtml#s231a)

As you can observe, there is almost a Cambrian explosion of development and business activities happening on the Bitcoin blockchain since the protocol stability and removal of limitations have happened with the forking away of BCH and BTC chains and development groups. There is a whole lot of development toolsets now getting developed and published to make developing small to large scale customer and enterprise applications and the ecosystem is expected to mature a lot more as time passes. To give a brief idea, of the amount of work that is happening, *[Figure 11.2](#c11.xhtml#fig11_2)* shows the overall development landscape by the time of writing of this book (April 2020):

![](images/Figure-11.2.jpg)

**Figure 11.2:** Bitcoin ecosystem chart. Image source: [https://twitter.com/PeergameCom](https://twitter.com/PeergameCom)

We will however not be able to discuss everything that is being developed or all utilities and tools but in the next sections, we will look at some of the most used and relevant tools and resources.

# [Nakasendo SDK](#toc.xhtml#s232a)

Over the period of the last 11 years, there have been many versions of node software implementations for the Bitcoin protocol in pretty much all languages (C++, Java, Javascript, Python, Go, etc.) that are used in common application development. Nakasendo stands out as it is developed in C++ which was also the same language used in the initial version of code released by Satoshi Nakamoto. It also is developed by nChain which is the most focused research and development organization developing and offering a portfolio of patents and research assistance for the Bitcoin ecosystem.

Nakasendo SDK: **[https://nakasendoproject.org/](https://nakasendoproject.org/)**

Nakasendo documentation: **[https://nakasendoproject.org/docs/index.html](https://nakasendoproject.org/docs/index.html)**

One of the innovations that have happened (with patents from nChain: PCT application number PCT/IB2017/050829) was the creation of a threshold signature scheme. This SDK provides tools that can be used to create threshold signatures. A brief explanation of the scheme is shown in *[Figure 11.3](#c11.xhtml#fig11_3):*

![](images/Figure-11.3.jpg)

**Figure 11.3:** Threshold scheme explained by Dr. Craig Wright, Chief Scientist at nChain who created the scheme. More details at [https://craigwright.net/blog/bitcoin-blockchain-tech/secure-wallet-systems/](https://craigwright.net/blog/bitcoin-blockchain-tech/secure-wallet-systems/)

Following are the key features of the threshold signature scheme which was never possible before:

*   **Backups and key recovery**: Since the key never exists, the whole set of issues with the backup of keys/mnemonics/passphrase goes away removing one of the biggest issues due to which people have lost their coins/money, human error. Threshold signatures use an idea of using t out of n shares of secret generated at maximum to regenerate the secret key on the fly as shown in *[Figure 11.3](#c11.xhtml#fig11_3).*
*   **Public Signing**: The t out of n required to sign system enables a different type of public signing where even the participants who sign do not know who all have signed and who has not. The transaction is not published until the signing has happened. These shares can even be distributed across countries making it fully robust and once the threshold number has been signed, the transaction is created as a general transaction where no one knows who created it making it completely private. There is no difference between the public address (type 1 or starting with 1\*\*\*\* in place of starting with 3\*\*\*\* which was how it was for multisig address currently as we saw in earlier chapters).
*   **Flexible participants:** The "t' set of owners of the shares of the private key are not fixed, they can be added, deleted as well making it very flexible in terms of maintainability.
*   **Threshold hierarchies**: It will be possible to set up a vero system where one person can veto everyone else's threshold. So that one key that can veto can stop the signing of the transaction by all participants but not sign a transaction to create it by itself. It is also possible to deploy an uneven allocation process allowing to add weighting on the shares as well. Again, the allocations of the shares/slices of the key are also extensible.

A complete code level walkthrough along with code is present at nakasendo documentation present at **[https://nakasendoproject.org/docs/HighLevelFunctions/index.html#threshold-signatures](https://nakasendoproject.org/docs/HighLevelFunctions/index.html#threshold-signatures)**

Along with this, all of the cryptographic functions and their usage details are also available at the above-mentioned link to Nakasendo docs.

# [BSV library](#toc.xhtml#s233a)

Created and maintained by the moneybutton team, this is one of the most referred to implementations of the Bitcoin code. It also provides a great set of libraries and tools for many cryptographic functions.

BSV is a JavaScript library for managing user keys, building and signing Bitcoin transactions (including inputs, outputs, and scripts), signing generic data, encrypting generic data, or doing anything that a client-side web wallet is likely to need to do. Advanced applications will often want to do sophisticated low-level Bitcoin operations that need a library for that purpose, BSV library does exactly that. It is also a library that provides moneybutton which is currently still the easiest and common way for applications to write data on Bitcoin blockchain using the `OP_RETURN` data.

JavaScript library: BSV: **[https://github.com/moneybutton/bsv](https://github.com/moneybutton/bsv)**

Excellent documentation and tutorials are available at the moneybutton documentation website for using this library and moneybutton itself.

**[https://docs.moneybutton.com/docs/bsv-overview.html](https://docs.moneybutton.com/docs/bsv-overview.html)**

Most of the cryptographic functions that are available with Nakasendo are also available with the BSV library.

# [Operate toolkit](#toc.xhtml#s234a)

We have looked at a whole lot of tools and protocols till now which encapsulate the complexities of the Bitcoin system and provide developers with easy to use tools without going too much into the intricacies of the Bitcoin protocol. These protocol layer tools provide developers the ability to focus on developing code for business functions rather than reinventing the wheel which is the main reason that there are many protocols so that all of the base functionality has easy access methods for developers to use.

Operate is a system that lets you put functions on-chain. It is a toolset that can help developers to build on-chain functions called Ops which enables transactions to become small but powerful programs, capable of delivering new classes of services layered over Bitcoin. Using these Ops, you can build transactions by reusing these functions.

Operate itself is built using a not so commonly used, but highly efficient scripting language called Lua. Operates Design is cross-compatible with Bitcom, and takes advantage of two other protocols developed by Unwrtier that we have seen in the last chapter, Bitcom Pipeline, and BOB. Operate provides agents (in elixir and JavaScript) that are used to load and run programs from transactions. You will be needed to install an agent in your applications and add it to your list of dependencies.

This idea is very similar to library functions or reusable standard modules that are present in any programming language or platform. Operates it for Bitcoin blockchain.

Operate works as a layer on top of Bitcoin blockchain and as a function that takes a number of parameters and returns a result called *state*. This state can be passed as an argument to the next Op along with any other parameters as needed and returns a new state as shown above. A cell/tape metaphor that was used in BOB is borrowed from it to represent each `OP_RETURN` cell as an Op:

This is shown in *[Figure 11.4](#c11.xhtml#fig11_4)* below:

![](images/Figure-11.4.jpg)

**Figure 11.4:** Operate and Ops function as a cell/tape metaphor

Data present in these Bitcoin transactions can be mapped to create structured objects using Operate Ops and it is fully compatible with the Planaria tools so the reading of data created using Ops will be easily available to read via the planaria toolsets.

**Resources:**

**Main website and documentation: [https://www.operatebsv.org](https://www.operatebsv.org)**

It also contains a library that documents all Ops functions that are published on Bitcoin blockchain.

**Examples and articles explaining Ops: [https://www.operatebsv.org/blog/data-mapping-structured-objects/](https://www.operatebsv.org/blog/data-mapping-structured-objects/)**

**[https://www.operatebsv.org/blog/interopable-signature-protocols/](https://www.operatebsv.org/blog/interopable-signature-protocols/)**

**Detailed code level documentation:**

**[https://hexdocs.pm/operate/Operate.VM.html#content](https://hexdocs.pm/operate/Operate.VM.html#content)**

**GitHub: [https://github.com/operate-bsv](https://github.com/operate-bsv)**

Another great tool from the same creator, Aaron Russell provides one of the simplest way to let your users fund data transactions in your BSV app. More details at : **[https://www.paypresto.co](https://www.paypresto.co)**

In addition to the above tools, another tool released by the same author is a very efficient Elixir Bitcoin Tx storage schema. You can find further details via the links mentioned below.

code: **[http://github.com/libitx/txbox](http://github.com/libitx/txbox)**

docs: **[http://hexdocs.pm/txbox](http://hexdocs.pm/txbox)**

# [Scrypt](#toc.xhtml#s235a)

We have looked at the transaction script in [chapter 6](#c06.xhtml) which is the Bitcoin's native language for writing various instructions inside Bitcoin transactions. This is a full-feature language that is based on an old language called Forth which primarily was used in the 70s and 80s for programming microprocessors. It is quite powerful and can run on low processing needs which is why the Bitcoin script language is quite powerful and well suited for low processing capabilities (simple computing) in the Bitcoin blockchain. Bitcoin, if thought as a computer, can be thought of as a simplistic or primitive computing machine that can efficiently run instruction sets but not third or fourth-generation programming languages that need compilation and more.

The downside of this is that you need specialized skills to be able to write complex business logic and functions with Bitcoin script. It is also difficult to find that skill set in the current market/industry as most programmers are using high-level languages like JavaScript now for development. Scrypt is exactly that, it provides the ability to write the smart contracts that are needed for writing business functions in a JavaScript-like language.

So for example, if you have to write a smart contract, now you can do that using scrypt's JavaScript-like interface, and compiling it gives you the instruction set generated in Bitcoin script which then can be added to your Bitcoin transaction.

It allows for writing, for example, a pay to public key hash rather than writing in the standard script you can write as shown below:

`contract DemoP2PKH {`

`Ripemd160 pubKeyHash;`

`constructor(Ripemd160 pubKeyHash) {`

`this.pubKeyHash = pubKeyHash;`

`}`

`public function unlock(Sig sig, PubKey pubKey) {`

`require(hash160(pubKey) == this.pubKeyHash);`

`require(checkSig(sig, pubKey));`

`}`

`}`

The full documentation of this tool is present at the documentation repository: **[https://scryptdoc.readthedocs.io](https://scryptdoc.readthedocs.io)**

A web-based SDE is present at **[http://scrypt.studio](http://scrypt.studio)**

You can also download the Scrypt extension in Visual studio code.

# [Bitmesh and Metaglue](#toc.xhtml#s236a)

Bitmesh is another project that is working on creating metanet based applications. Currently, they have an encrypted email service and a platform called Metaglue for building metanet applications.

Their email services use Bitcoin messaging infrastructure for sending and receiving emails. This makes the email services incredibly secure and each message will be costing a small payment (dust amount) so it kind of takes care of the prevention/restriction spam in terms of emails as well, by incentivizing you to receive a payment if someone wants to spam you.

Metaglue allows developers to build Metanet applications allowing them to leverage the wallet service provided already by Bitmesh. Metaglue solution also allows developers to customize their payment button styles to ensure the button looks aligned with the overall design language of the product/application they are building.

Code-level details and explanation of usage is present in their documentation website: **[https://doc.bitmesh.com/#/introduce](https://doc.bitmesh.com/#/introduce)**

# [Mattercloud and Matterpool](#toc.xhtml#s237a)

We have looked into the Bitintex API service, which has now been revamped to a full-scale development platform and toolset library for developers and is offered now as Mattercloud library. It provides a set of SDKs and tools and a set of Bitcoin APIs for reading and writing to the blockchain with various parameters. Based on the features available, with respect to the planaria tools, mattercloud SDK offers a comparable set of tools for developers. It is a fully developed infrastructure service for both individuals and businesses offering the platform for usage.

Complete developer documentation is available at the following links:

**Javascript SDK: [https://developers.mattercloud.net/#introduction](https://developers.mattercloud.net/#introduction)**

Matterpool is a full node block explorer offering Bitcoin blockchain reading services with all of the standard block explorer features.

# [Bitsv and Polyglot](#toc.xhtml#s238a)

Bitsv is the python implementation of Bitcoin original code, which comes with the exclusive features of being quite fast (100 times) and is distributed on PyPI as a universal wheel and is available on Linux/macOS and windows. It requires Python 3.5 + and pip version 8.1.2 or a later release.

GitHub with source code: **[https://github.com/AustEcon/bitsv](https://github.com/AustEcon/bitsv)**

A work in progress, polyglot is for developers who are working with python. It offers a large set of features and SDK and supports metanet protocols through python. It supports B and BCAT protocol for writing data to Bitcoin blockchain, and complete UTXO management features along with many other features for reading using the B, C, and D, MAP and AIP protocol identifiers is work in progress. You can find code and other details at the GitHub page for the project:

**[https://austecon.github.io/polyglot/index.html](https://austecon.github.io/polyglot/index.html)**

# [HandCash Connect toolkit](#toc.xhtml#s239a)

Handcash has launched a new SDK called to connect in addition to the wallet, POS services that they are providing at this point. Connect will package all of the relevant tools that an app developer will need and is an extension of their original idea of Cashport SDK. Connect is an all-in-one toolkit with tools to handle all of the Bitcoin-related code so as to cover as much as 90% of the work needed for developing the backend infrastructure for general mobile app developers.

This SDK will also feature an App store for featuring the Apps that are developed using connect SDK and will be released in the spring of 2020 for developers to use officially but if you have a project that needs early access you can connect with the team to get it as well. Apart from everything, this will be a non-custodial wallet implementation for new app developers so that they are not tied down for doing a huge amount of work to become a custody service? MAB for complying with the legal framework of a custodian.

More details are present at **[https://connect.handcash.io](https://connect.handcash.io)**

# [Mempool and tokens with DOT wallet](#toc.xhtml#s240a)

We have discussed many wallet solutions, but DOT is building an open-source platform for wallets that are built using the tokenized protocol, supporting tokens for Bitcoin SV. We will be looking in details of the tokenized protocol in a later chapter, but this effectively means that you can issue any tokens and use the DOT wallet for managing tokens. Along with other things, it offers the BSV wallet integration with the WeChat platform. More details are present at **[https://www.dotwallet.com/en/](https://www.dotwallet.com/en/)**

GitHub:

**[https://github.com/mempoolTeam/dotwallet-platform/blob/master/README.en.md](https://github.com/mempoolTeam/dotwallet-platform/blob/master/README.en.md)**

The parent company is a mining group called mempool which also is working on an overall Bitcoin protocol implementation of Bitcoin with nodejs. They are also working and have released a bitdb implementation in Go lang. Links are below:

**[https://github.com/mempoolTeam/bcoinsv](https://github.com/mempoolTeam/bcoinsv)**

Bitcoin database (similar to BitDB) implementation for creating Bitcoin-based database structures using Go. **[https://github.com/mempoolTeam/go-svdb](https://github.com/mempoolTeam/go-svdb)**

# [Bitsent tools](#toc.xhtml#s241a)

Another project working on various toolset for Bitcoin SV is bitsent and you can find their tools in various repositories present at their GitHub page:

**[https://github.com/bitsent](https://github.com/bitsent)**

One of the products they have offered is a moneybutton like a button, but it is a fully customizable UI button. It is written in pure JavaScript with no dependencies: **[https://github.com/bitsent/BitBtn](https://github.com/bitsent/BitBtn)**

There are few other projects which have published tools that are very useful, below are their GitHub pages for reference.

*   **Tiddlybit**: A JavaScript library for constructing, parsing, and serializing Bitcoin scripts: 
    
    **[https://github.com/libitx/tiddlybit](https://github.com/libitx/tiddlybit)**
    
*   **Treehugger**: A metanet traversal tool: **[https://github.com/libitx/tree-hugger](https://github.com/libitx/tree-hugger)**
*   **Bitssocket-connect**: a plug and play bitsocket connection for node js and browser: [https://github.com/jonaird/bitsocket-connect](https://github.com/jonaird/bitsocket-connect)
*   **Planariette**: lightweight planaria for Node JS: **[https://github.com/jonaird/planariette](https://github.com/jonaird/planariette)**
*   **SymRe**: is a short URL creator like TinyURL where all the URLs are stored on the Bitcoin blockchain accessible for everyone: **[https://sym.re/create](https://sym.re/create)**
    
    **[https://github.com/torusJKL/SymRe/blob/master/documentation/README.md](https://github.com/torusJKL/SymRe/blob/master/documentation/README.md)**
    

# [Conclusion](#toc.xhtml#s242a)

We have looked at a huge number of projects that are currently building for real-world applications using the Bitcoin blockchain in this chapter. There will be many other projects that are not yet public and have not been covered here, but the intent of talking about all these projects was to give an idea for any developer, startup or an enterprise to look at what are the business vertical they fall in and how can they leverage the overall work that is done on the Bitcoin protocol along with how specific implementations are working right now. The tool kits and SDKs that are discussed in the chapter will provide a starting point for developers to kickstart and test their ideas on how they want to set up their application architecture.

With the genesis protocol upgrade and removal of many limitations (like the removal of standard script mandate in the code) has opened up a \[plethora of opportunities to build complex programs using a script or to use the Bitcoin blockchain as an alternative to cloud storage or as a datastore which provides much better reliability, availability and permanency (storage for a lifetime, with no downtime) making it ideal for business/enterprises as well as individual users. There is a lot of potential in this technology which should be looked at by every existing enterprise and the future enterprises to build on a scalable technology that will be defining the future of trade and the internet.

In the next chapter, we will look at an identity solution and a replacement of traditional Bitcoin address and naming systems which are quite technical for general public use called paymail. It aims to replace the current email services and promises emails built on Bitcoin blockchain which will offer spam free, encrypted, and completely private email services unlike what it is today where you have invasive advertising in your mailbox if you are a free email service user.

# [Questions](#toc.xhtml#s243a)

1.  Why is Bitcoin clearing and settlement happening in real-time when the traditional process takes a full day to more than days in doing so?
2.  How will the supply chain industry be able to optimize cost using a public blockchain like Bitcoin?
3.  How are Bitcoin microtransactions enabling a completely private user experience on the internet and how do users stand to be able to earn by creating content on the blockchain?
4.  What is a threshold signature scheme and how is that more secure from the traditional multi-signature scheme?
5.  Develop a script called dead man switch using the scrypt library. Example is present in the documentation.

# [CHAPTER 12](#toc.xhtml#c12)

# [Identity and Authentication on Bitcoin](#toc.xhtml#c12)

**“Google may talk a good game about privacy, but private data is the mortal enemy of its system and the world.”**

*\- George Gilder*

The biggest challenge apparently of the current internet is that data is a commodity and sold for profit. The collection of data however is not so regulated which we hear constantly about in terms of data breaches, privacy becoming non-existent, and everything about a person who is online being logged and stored to be used for personalization of what that person will be served in advertising as a service.

We will focus on how identity and privacy work in the world of Bitcoin and how it is possible to solve the issue of the current internet using the Bitcoin privacy model, not just that but how can anyone truly gain by getting paid for providing data to, for example, advertising companies. The opportunities are limitless if we build a system that supports privacy.

# [Structure](#toc.xhtml#s244a)

*   Bitcoin's Privacy model
*   Bitcoin addresses and identities, reusing addresses
*   Paymail and wallet systems supporting privacy
*   Metalink and BIP270

# [Objective](#toc.xhtml#s245a)

After studying this chapter, you will be able to understand the Bitcoin identity and privacy model. You will also learn how the paymail solution is used to solve the problem of privacy and also how to use the Bitcoin addresses in the right manner along with using them in SPV way. You will also learn how a universal user database called bitkey was built to create an on-chain user identity registry for all users.

# [Basics of privacy model](#toc.xhtml#s246a)

In the traditional model, user identities are proved using a formal process such as KYC/AML in which the user submits a provable identity document (most cases a government-issued identity document) to a third party such as Bank. It is only when this is established can a user perform a transaction via this particular third party. This third party now sits in the middle and documents details of all financial transactions in and out of the account which is tied to a specific identity. If a breach happens at that third party, all the information is at risk and has potentially catastrophic consequences like the loss of funds due to identity thefts, and much more.

PIIs (personally identifiable information, also is protected by strict regulations across the world, and data breach is heavily penalized. One such example is in early 2018, Facebook Inc. (FB) was embroiled in a major data breach. The profiles of 50 million Facebook users were collected without their consent by an outside company called Cambridge Analytica. Apart from what was the apparent loss for the users, even Facebook incurred $3 billion in legal expenses apart from the loss of reputation.

This model is quite fragile with siloes and single points of failure. Data is the most valuable information that is in many scenarios sold at a premium by these third parties to influence consumer behavior further on to make the customers more of an advertising commodity.

The Bitcoin whitepaper describes this as shown in the below picture:

![](images/Figure-12.1.jpg)

**Figure 12.1:** Bitcoin model of identity and privacy

On the left of *[Figure 12.1](#c12.xhtml#fig12_1)* shows the parts of the system that are private. On the right, are the parts that are open and seen publicly making Bitcoin a peer-to-peer private system.

This is what Bitcoin solves by making all transactions public and detaching them for identities. This mechanism, in addition to solving the double-spending problem by making all transactions public, also solves the problem of user identity and privacy as an added benefit. Every transaction needs to be done using a new key pair making it impossible for any company which works with data analytics to use the public transaction data for customer or merchant behavior analysis. This is the ONLY thing Bitcoin does which is completely new and innovative, rest everything including usage of timestamped server called blockchain, cryptography, etc. are things that already existed.

If this is compared to existing identity management systems, Bitcoin moves away from the whole concept of *Accounts* to a new model where each transaction happens from one key to another and that is it. If you compare with the existing model's point of failure in the current model where when I make a payment, the various trusted parties who have access to this payment information as shown in *[Figure 12.1](#c12.xhtml#fig12_1)* also are the points of failure when it comes to the data breach. In the Bitcoin world, the same transaction is done detached from identities but only the two parties (consumer and the merchant) are aware of the identities of transacting parties.

The merchant will still print the same invoice or billing details for the mentioned transaction for record-keeping, taxation, and accounting purposes but no one apart from the two knows by looking at transactions about who was involved in the value exchange. Later for dispute resolution or legal needs, the merchant or the consumer system of record can be used to tie identity to the transaction, As such, the disputants would not even be required to attend court, and could file documents online.

In the future when the ecosystem is more widely adopted, this scenario can be extended a lot further, where we could see a world where international trade and commerce could be conducted with distributed jurisdictional options linked to blockchain-based technology and contracting. It would provide much-needed governance from within the technology delivered through Bitcoin.

One of the key ideas here which is not to be missed is that to maintain privacy, it is not recommended to reuse the same address again. This effectively means, no more static, or constant Bitcoin address. This approach has been implemented in the Bitcoin SV wallets lately with few techniques like the handle system we saw when we discussed wallets, which provides a single identity (in terms of a handle) but behind the scene implement a mechanism to generate a new address/key for every new transaction. It is also recommended.

Another aspect of privacy is governed by volume. The more the number of transactions going through the network, the more private network and identity will be. If there are just 10 transactions it will be quite easy and cheap to trace through as compared to if there are a million which will make it expensive to trace.

With that in mind, the best way to keep identity private is to split your coins before you spend them into small units and large numbers of UTXOs. Suppose if I wanted to do online shopping but want to be more private in terms of my activities online, I would first split my UTXOs from 1 BSV from Level 0 to Level 1 as shown in the below *[Figure 12.2](#c12.xhtml#fig12_2)*. In a single block (approx 5 - 20 mins), we now have many split transactions when I make quick purchases with different merchants in a few mins. A merchant cannot tell when this has been split to another merchant nor if it is just dividing your coins making it difficult to guess upfront who made the transaction. *[Figure 12.2](#c12.xhtml#fig12_2)* shows this process below:

![](images/Figure-12.2.jpg)

**Figure 12.2:** Doing online shopping in a single block

You can make this much more private by doing this process a bit more randomly if you use multiple inputs and outputs, and if the change is not joined again, there is no simple way to link the various spending. This same process is applicable to merchants as well. A merchant who creates a new address for each new transaction improves the privacy of not just his own, but his customers as well. For e-commerce retailers, they have 100s of transactions per second, and if each transaction uses a unique key pair, you can imagine it is quite difficult for any sophisticated computer analysis system as well.

Wallet providers can provide this process as a service which in a way gave birth to BIP 270, and a protocol called paymail, which is doing exactly what we have described on a very high level above. If you combine paymail with the concept of SPV, this makes up for excellent privacy and a system which can be quite easy to use by sending payments like you send an email.

Before we go into details of the paymail protocol, there is one more concept which needs to be covered is the idea of Bitcoin transactions being similar to cash. We have discussed a little about this earlier, but based on what we have read and known till now, it is not hard to imagine, that when you create a transaction with type `SIGHASH_NONE` where the receiver of the transaction can add their Bitcoin address later in time, you mimic cash. This is what makes Bitcoin an ideal system to build cash upon. The Internet initially was intended to have special features which would allow secure exchange of money, but that was never implemented/adopted, that is what Bitcoin as electronic cash system does, it provides a highly secure and optimally working system that can be used to replace the existing system of cash which requires printing of currency and paper. In other words, Bitcoin would become very similar to oil, which is a way to run cars, Bitcoin will be the oil which is used to store data and overall everything on the internet, making the whole idea of cryptocurrency which is currently prevalent as a misconception. It is never meant to replace currency, it is a system to enable honest and auditable currency.

# [Paymail and BIP270 specifications](#toc.xhtml#s247a)

Paymail and BIP270 specs provide a currently underdevelopment protocol to solve the issue of user experience with the complexities involved in Bitcoin and peer to peer transactions. Let us have a look at them one by one.

# [Paymail](#toc.xhtml#s248a)

One of the biggest barriers when it comes to the adoption of Bitcoin for mainstream usage is, it is still very low level or very technical. The whole idea of using a complex address like `16g12bUuoiJV3R8ynNYvrDgSfGEWknuQee` scares most of the mainstream users who are not expected to use copy-paste by default for doing any money-based transactions. It is rather surprising that it has taken a decade for the developer community in Bitcoin to come up with a simpler usable alias system like paymail which also explains why Bitcoin has been limited in terms of adoption till now.

Paymail recommends the following format to be used for an address:

`<alias>@<domain>.<tld>`

For example, moneybutton which launched one of the first implementations of paymail, If I create my paymail using their service, it will look as `kapil@moneybutton.com`

Where an alias is the indented user name, `domain.tld` is the paymail service provider's domain address.

This is my paymail hosted by moneybutton and it is possible for anyone to send me money in the form of Bitcoin by sending it to this email like an address. Paymail is a protocol that uses DNS and HTTPS queries to give new functionality of Bitcoin or Bitcoin support to email addresses.

The simplicity of this alias also is brilliant in terms of supporting existing email service providers to have the option to roll out simple paymail protocol for all of their existing user base. Think of Gmail adding the paymail functionality to their existing user base, just by adopting the protocol and now users with minimal technical capabilities can use paymail address to send and receive money in the form of Bitcoin.

The goals of the paymail protocol are:

*   User-friendly payment addresses/handles
*   Permissionless implementation
*   Self-hosted or delegated to a managed service
*   Automatic service discovery/location
*   PKI infrastructure
*   Cross-wallet exchange of single-use transaction output scripts of any construction
*   Request and response authentication
*   Security and policy management
*   Capability extensibility and discovery

The details of the paymail protocol are present at **[https://bsvalias.org/](https://bsvalias.org/)** and it is designed to be extensible. The bsvalias ecosystem supports for future expansion of paymail and related protocol specifications now and in the future in a decentralized manner where it's open for anyone to propose and extend along with the publishing of their specific implementation of paymail protocol details via BRFC (Bitcoin SV request for comments). Currently following specifications have been published which details how a provider can set up the paymail services for their users. These specifications are detailed out in the above URL and the below table shows a little bit of information about what these BRFC were doing after being proposed:

 
| **BRFC No.** || **Title** || **Comments** |
| --- | --- | --- |
| b2aa66e26b43 || bsvalias Service Discovery || This BRFC describes the process of DNS discovery and then capability discovery for that host |
| 0c4339ef99c2 || bsvalias Public Key Infrastructure || Each paymail handle `<alias>@<domain>.<tld>` MUST be issued a stable ECDSA public key that SHOULD NOT be used as part of any on-chain transaction |
| 759684b1a19a || bsvalias Payment Addressing (Basic Address Resolution) || Given a sender and a receiver, where the sender knows the receiver's paymail handle `<alias>@<domain>.<tld>`, the sender can perform Service Discovery against the receiver and request a payment destination from the receiver's paymail service. |

**Table 12.1:** BRFC under bsvalias.org an open-source community-driven protocol specifications

The usage of SRV record in service discovery step allows for third-party hosting of a local domain name based paymail, allowing for wallet providers to offer paymail hosting as a service, just for the paymail capabilities.

There are few more features documented with additional BRFCs which can be read through at the above-mentioned website along with the code and implementation details which moneybutton has done using JavaScript (nodeJs and express) at:

**[https://github.com/moneybutton/express-paymail](https://github.com/moneybutton/express-paymail)**

**[https://github.com/moneybutton/paymail-client](https://github.com/moneybutton/paymail-client)**

A detailed video explaining the above code is published by the same company, moneybutton on YouTube: **[https://www.youtube.com/watch?v=WFuArXVe3bM](https://www.youtube.com/watch?v=WFuArXVe3bM)**

It is also possible for anyone to take the above code and spin-off their own paymail based wallet system. One key aspect to note is that paymail has two sets of keys:

1.  The identity key is attached to the paymail address.
2.  Keys that are associated with this master identity key generated either using a method we discussed briefly in [chapter 3](#c03.xhtml) called BIP32 (Hierarchical Deterministic (HD) key or threshold signature depending on the specific implementation chosen by the wallet.

The way these protocol works is described in the below *[Figure 12.3](#c12.xhtml#fig12_3)* on a high level. You can read complete technical implementation of this along with the flows of each of the steps at the developer documentation present at **[https://bsvalias.org/](https://bsvalias.org/)** which was created and written by nChain and Moneybutton with open BSV license:

![](images/Figure-12.3.jpg)

**Figure 12.3:** Bob sending money to Alice using paymail address including BIP270 protocol to post the payment peer to peer

# [BIP270: Peer to Peer Payments](#toc.xhtml#s249a)

BIP270 provides the specification for sending payment directly to an endpoint so that two different wallets can send payments to each other. It defines how one wallet sends an invoice for payment to another wallet and the other wallet pays that invoice. It is a low level detailing of how to construct the payment invoice by wallets and how to make the payment transactions so that all wallets are using a common protocol to be able to talk to each other. This is still a work in progress but representative implementation is mentioned in *[Figure 12.3](#c12.xhtml#fig12_3)* in step 4 which will enable some peer to peer aspect of the transaction to the recipient paymail address.

One other use case for this paymail is to send an encrypted message to someone. If you recall from *[Chapter 3: Cryptography, ECDSA, and Bitcoin Addresses](#c03.xhtml)* where we discussed wallets, it is possible to encrypt not just payment using the same keys but also message data which along with paymail provides the very obvious usage of sending fully end to send encrypted messages to other users. This allows paymail to act really like an email and full encryption makes it completely secure email. An excellent implementation of this is done as well which is called baemail (before anything else mail). Below figure shows a typical inbox interface with not just allows email capability but also to send money with mail allowing for features like priority mail based on how much the user is paying someone to read their message and all the messages will be stored on-chain making it completely reliable, available and secure way of communication:

![](images/Figure-12.4.jpg)

**Figure 12.4:** Baemail using moneybutton paymail solution to provide email and money functionality

This is only in the last 6 months and since this is an extensible protocol, I expect to see a huge amount of development happening in the future using this protocol making it quite important for any company building solutions with wallets to support this protocol.

# [User identity v/s keys](#toc.xhtml#s250a)

It is quite important to understand one key point in creating a system like paymail. The identity/name stored as `username@paymaildomain.com` for example is different from keys. The wallet service behind the scenes has to create a system which associates this particular paymail ID with a or a set of keys which will be used to access the coins. It is possible for a user to lose their coins if they lose their keys and still retain their paymail domain name. This could happen by a possible hacking attack or if the wallets do not store an alternative way to recover their users' password if they forget it. This happens quite often and unless there is a system built in for key recovery keys will be lost forever but the user can still claim their paymail by resetting the keys and the password associated with their identity.

# [SPV and Paymail](#toc.xhtml#s251a)

SPV is the method for scaling transaction delivery systems in Bitcoin. Current implementations of paymail are not SPV which is the true innovation of Bitcoin to make transactions truly peer to peer or like cash. The whole idea of using a paymail is nice, but it not being SPV does not use full feature privacy capability of Bitcoin. Ideally, Alice should handover her transaction along with its Merkle path to bob and not send it to the blockchain directly. Not doing so creates a situation where user privacy is partially compromised because they are sending the transaction to the network exposing their IP. When Alice sends the data to Bob, only Bob will know who created the transaction. The idea is that small value transaction done this way act as cash does, that doesn't need the user to identify them self making them quite private.

Alice handing the transaction to Bob does not even require an active internet connection, Alice can do it using her phone's NFC/Bluetooth or any other method like even SMS. It also reduces the redundant process of Alice first sending the transaction to blockchain and bob later verifying it after waiting for miners to confirm to Alice reducing the number of overall steps. Using block header and Merkle path is what enables large scaling as the processing and storage needed to use block header is much less than running a node and validating via that (even if the node is run by waller provider making a 3rd party dependency limiting scaling).

A fully scalable SPV is not that easy to implement right now as current internet technology is IPV4 based and use of DNS/HTTPS is needed creating still the mandated need of a third-party like moneybutton providing the DNS resolution service, but in future when internet fully moves to IPV6 it will be possible to implement full SPV for peer to peer transactions. Till then the semi-trusted third party (like moneybutton) will have to do for using a paymail type alias system but the transaction delivery system can be made SPV where Alice can handover the transaction and Merkle path to bob or vice versa and the recipient propagates the message to the blockchain.

A Peer to Peer but a bit different implementation of SPV was recently done by Moneybutton team in collaboration with HandCash team to make transactions between them P2P and also solve scalability issues by optimizing the process. The original Bitcoin code had a technology called pay-to-ip, which was later removed by the Bitcoin Core developers. This technology was restored and rebuilt in a more secure and user-friendly way on top of paymail by this implementation. In this method, to send a transaction to a paymail endpoint, the first query the address using the existing paymail endpoint (sender's end), then build and sign the transaction, and then deliver the transaction to the new paymail transaction receive endpoint (receiver's end).

By this method, the receiver doesn't have to now scan the blockchain to look for the transaction sent by the sender saving a good amount of processing and time enabling a large volume of small size transactions between these two wallets. This is a partial implementation of BIP 270 focused on a practical problem of scaling which needed to be solved keeping the true spirit of P2P alive (a complete invoice, authentication, and p2p transaction system). **[https://blog.moneybutton.com/2020/03/30/handcash-and-money-button-restore-peer-to-peer-electronic-cash/](https://blog.moneybutton.com/2020/03/30/handcash-and-money-button-restore-peer-to-peer-electronic-cash/)**

# [Paymail Key Registry on Bitcoin](#toc.xhtml#s252a)

This was all fine to implement but there still was one catch, the users still have to depend on the wallet service provider or a third party for their paymail service. This makes it similar to the existing system where banks provide an account number or in case of India, something very similar, a UPI address (which incidentally looks very much like paymail, `e.g. kapil@upi)`. So there is a dependency on a third party paymail service provider like moneybutton to provide and maintain my identity. This creates a need for explicit trust, which is what Bitcoin is trying to get away from so can this be solved using Bitcoin?

This issue could be partially resolved in a way by putting the identity key of paymail on to the blockchain to make at least the identity verification on-chain so that becomes independent of the trusted third party and create more trust on the on-chain identity including people who trust vouching for the identity by signing with their keys.

The first on-chain registry system was implemented in an application called bitkey which was again created by \_unwriter and its implementation is described in detail in the application documentation at the URL: **[https://bitkey.network/how](https://bitkey.network/how)**

Bitkey has following advantages/features:

*   **Open**: Anyone can make use of this global user database because it's on the blockchain.
*   **Reverse lookup**: Given a pubkey, you can find its paymail address
*   **Bulk query**: Instead of having to query one paymail or one public key at a time, you can query multiple at once, even for paymails that span multiple service providers.
*   **Cross-platform**: Because it's a globally shared database made up of any paymail provider, stored on the blockchain, nobody can restrict access to this global user database.
*   **History**: You can record the entire history of a paymail address and its associated public keys.
*   **Efficient**: You don't have to include both paymail and pubkey in every signed data transaction because the *bitkey user table* takes care of the paymail-pubkey association.

Let's take an example, suppose Alice wants to send a payment to Bob this time and uses the paymail mentioned in the last example. Alice now can query the public key for Bob on this register in addition to the verification done by the paymail service provider. This is more relevant to address use cases where the paymail is used for user identity than for doing payment transactions. Currently many applications that use OAuth 2 type identity verification using moneybutton paymail service can switch to this on-chain identity verification. One additional aspect is, currently when the app is using paymail based verification, they use both the paymail and the associated public key to be passed for verification. This is redundant and using the on-chain key registry can be split by putting the paymail and public key relationship on-chain and then only use paymail for identity verification.

One straightforward method for further increasing the authenticity of this on-chain registry is by creating a web of trust where multiple users sign someone's identity to provide additional verification of the correctness of the public key associated with the mentioned paymail identity. This is similar to how DNSSEC/SSL is currently implementing various trusted authorities verifying the authenticity of a domain name. These features will be eventually built on paymail protocol or provide an opportunity for application developers to build these extensions as a business.

# [Metalink and BIP270](#toc.xhtml#s253a)

Metalink proposal is an alternative to a lot of approaches we have seen until now and focuses fully on the P2P aspect of using Bitcoin blockchain and wallets. The proposal contains three main parts:

1.  Metalink ID
2.  BSVABI
3.  Unplanaria

Metalink ID is an identity protocol which is a decentralized and pseudonymous system using transaction IDs to represent unique identities with both an owner and an activation key. It is done by adding the public key(s) of the owner(s) after the `OP_0 OP_RETURN` in a transaction, a minimalistic implementation of a unique ID system is done which is verifiable on-chain.

Full details of this protocol: **[https://bsvabi.org/#/?id=4-future-possibilities](https://bsvabi.org/#/?id=4-future-possibilities)**

# [Conclusion](#toc.xhtml#s254a)

There are several other developers working on more identity/authentication solutions which if not be better will implement many more features and take this protocol further. It remains to be seen but this is a protocol that immensely simplifies the user interface of Bitcoin which has been a roadblock till now for mainstream adoption of Bitcoin.

In the next chapter, we will deep dive into the most sought after the idea of smart contracts and tokens on Bitcoin. The number of use cases that are possible with tokenization of assets and the open-source protocol which can be used for tokenizing everything possible on the Bitcoin blockchain while still being legally compliant with existing security regulations.

# [Questions](#toc.xhtml#s255a)

1.  What is the difference between the privacy model of Bitcoin and that of the current internet, which is more private?
2.  Why is the ownership of data important for consideration in terms of developing software applications?
3.  How is the current advertising-based model of internet misusing user data?
4.  Why paymail is a solution to the user experience problem of Bitcoin?
5.  What is the benefit of using a key registration system published on-chain as compared to hosted by a third-party service provider?

# [CHAPTER 13](#toc.xhtml#c13)

# [Smart Contracts and Tokens](#toc.xhtml#c13)

**"Economics is not about things and tangible material objects; it is about men, their meanings, and actions."**

*\- Ludwig Von Mises*

One of the features of the scripting language in Bitcoin is that it allows for simple deterministically running programs in a transaction which can allow for complex business logic to be added directly inside a transaction. In addition to that, it is possible to do Turing complete computation quite efficiently with Bitcoin Script. These properties allow for creating legal or otherwise, any type of business contract on Bitcoin. These are what are now referred to as Smart Contracts in the ecosystem. Using these properties including the tokenization of assets, a new global service economy can be created now based on Bitcoin smart contracts. We will discuss how to do it using the open-source protocol in this chapter.

# [Structure](#toc.xhtml#s256a)

*   Concept and basics of a legally enforceable and otherwise, electronic contracting
*   Why what and how of Smart Contracts on the blockchain
*   Basic concepts of cryptography, business process, and tokens
*   Tokenized protocol
*   Run protocol
*   Bitcoin computer protocol and system

# [Objective](#toc.xhtml#s257a)

After studying this chapter you will be able to understand what smart contracts are, how to convert, and create any type of smart contracts on the Bitcoin blockchain. You will also understand the methods for sharing secrets between two non-trusted parties using an extension of the simple ECDSA method. You will learn various concepts about tokens, and business aspects of the trades, tokenized, run, and Bitcoin computer protocols and use it for creating various tokens which are stored on the Bitcoin blockchain.

# [Electronic contracting](#toc.xhtml#s258a)

With increasing reliance on the internet for trade, commerce and communication domestically or cross the border, has increased the need for creating a structure which not just accepted domestically but also across multiple legal jurisdictions.

In addition to the two parties who are engaging in the contract, the third party which is providing the web/online platform/transaction engines for these parties to contract also needs to be placed in proper legal standing as if they sometimes even become a legal third party to the contract. If there is a lack of specific legislation detailing the legal position of an electronic contract, acceptance and the terms of a contract created using the Internet will establish itself as a legal document by means of the general law of contract. Whether conducted by writing, orally or implied from the conduct of parties, contractual negotiations are formed in a similar manner whether completed by telephone, face to face, or over the internet (using methods such as email or the web). There is little fundamental difference in the process of offer and acceptance in the *real-world* to the internet.

![](images/Figure-13.1.jpg)

**Figure 13.1:** Comparison of an existing system of contracting v/s a smart contract

Currently, the most common form of contracts is called clickwrap or clickthrough contracts which you typically see when using a new mobile app or when installing new software on your computer, these type of contracts make a very appropriate use case for using an immutable entry in blockchain making it quite a resilient way to store a contract. One of the features of these contracts is that they are mostly static once created. Few features of this type of contract are that the user is expected to either click on the I agree button to agree to the terms of the contract or write his/her name written or printed in the document. These types of contracts are heavily used and are needed to be signed one time and stored for reference for all future.

# [Smart Contract](#toc.xhtml#s259a)

A smart contract solution for such a contract is quite simple to do if a blockchain like Bitcoin is used. For a contract to be legally binding, it is sufficient for the party to have downloaded the contract and agree to be bound by that contract. One such implementation can be done by requiring the contracting party to provide the hash of terms and conditions to be able to use the product/application as shown below:

Hash("Terms and Conditions" || "I agree")

In case the agreement is such that user needs to put some personally identifiable information (PII) then the additional condition can be added as shown below:

Hash("Terms and Conditions" || "I agree" || <Bitcoin Address>)

In either of the cases, a smart contract can be built to require the user to provide the above information to be able to unlock the media/program/software application/product they have purchased. In providing this data, the user would have to download the terms and conditions document, convert it into the hash and add the text `I Agree` (most cases the application requires can also do it for the user by making him click or manually write the text) legally proving that user indeed has seen the terms and conditions. The unlocking script added in a Bitcoin transaction can require the user to provide the above details.

This way, a small value transaction containing a custom script puzzle requiring an unlocking script can work as a smart contract that will be stored immutably on a blockchain for any future reference for a fraction of the current cost.

This was just a very straightforward contract implementation using the Bitcoin blockchain. The script program in Bitcoin provides for documenting various possible business rules, contract negotiations, and multiple parties involved for multiple steps in the overall creation of smart contracts. Such contracts typically are called dynamic contracts. They can keep changing periodically or frequently along with having attributes associated with time as well which can be achieved using `nLocktime` parameters in a Bitcoin transaction.

Let us take a step back from this point to understand many concepts that are involved in Smart contracts, Tokens, Cryptography, and the overall business processes that are involved in the trade where there smart contracts and tokens will be used to solve real-world problems.

# [Basic concepts](#toc.xhtml#s260a)

We will now look at various concepts that are involved in this overall process.

# [Cryptography](#toc.xhtml#s261a)

We are aware of the ECDSA and digital signature which are at the heart of Bitcoin transactions, these smart contracts and tokens to be able to work with similar cryptographic security, needs more than a single key pair that we have been using in Bitcoin transactions. That leads us to one concept which we need to cover in terms of the digital signing of a contract and what is needed for signing and verification by the parties involved.

A typical flow of digital signing between a sender and receiver is shown below in *[Figure 13.2](#c13.xhtml#fig13_2):*

![](images/Figure-13.2.jpg)

**Figure 13.2:** Method of digital signing and sending of a document between two untrusted parties

For two untrusted parties to share a communication channel with each other ( like a customer and merchant, or client and server), they need to use a cryptographic scheme to secure their communication, in this case, the proposed method is from the patent by nChain with Open BSV license:

**http://patentimages.storage.googleapis.com/c3/36/52/827fc3bbe90e26/WO2017145004A1.pdf**)

The method described in the above patent allows for not just creating a single sub-key as shown in the below *[Figure 13.3](#c13.xhtml#fig13_3)* but it allows for sharing a hierarchy of subkeys which are perfectly secured (by ECC) and can be used for communication of messages between the two:

![](images/Figure-13.3.jpg)

**Figure 13.3:** Method for creating sub-keys from a shared secret between untrusted parties (see patent)

Alice now creates a shared common secret, S using the above-described process by calculating it with Bob when she visits the store (could be based on web session ID, invoice number, or anything else). Alice now will prepare a transaction which is a dust value transaction (low value) and will add an actual transaction that transfers the funds to Bob's derived public key (from the master key). She will then encrypt the message using shared secret S and add that in the dust transaction's `OP_RETURN` or Script and send it to Bob. Bob will take that transaction and decrypt the message to find out the public key that Alice has used to send the transaction and gain access to the funds using the corresponding derived private key. The complete process is shown in *[Figure 13.4](#c13.xhtml#fig13_4)* with the details:

![](images/Figure-13.4.jpg)

**Figure 13.4:** Method for creating sub-keys from a shared secret between untrusted parties

Hierarchy of hashes can be used (in place of a single hash shown above, doing hashing again and again)) to create further derived keys for creating next-generation messages. Details of this process are present in the patent mentioned above for the curious readers, but the idea is to use M' (=Hash(M)) in place of M and Hash (M') for the hashing aspect, and create a new derived pair of keys from the master key. This could be done any number of times to create a number of derived keys from the same master key.

Using the above process it becomes possible to have a payment made, with a complete audit trail of record being linked to invoice fulfilling the required legislative requirements/compliance for Bob. If needed, Bob can have a split address where he can directly send the VAT and other slates taxes to the government as he gets paid avoiding the need for money and time-consuming audit processes at the end of the year, better, record is immutable. There is no place for accounting frauds and also, you can reverse transactions, but doing so requires a return of funds to the originating source.

In fact, the complete process for a Buyer and a seller shown in *[Figure 13.4](#c13.xhtml#fig13_4)* can be created with the above-mentioned processes to work on blockchain. Bob can hold a series of hierarchical addresses that record all stages of the order — from invoicing and payment to sending and delivery.

If Bob now has a sub-master key for each client (see the patent above), he can also construct a separate subkey, that is known to himself, the client, and the tax authority for audit purposes, but no others, allowing him to retain an absolute level of privacy, where other clients and suppliers do not even know how many transactions he is doing. Moreover, he can construct payments in a manner that allows him to isolate internal employees and have them know only the information related to their departments.

# [Business processes](#toc.xhtml#s262a)

Once we understand the basics above, we can build the solution for the complete process of a commercial transaction between Alice and Bob for the business process shown below using the above methods:

![](images/Figure-13.5.jpg)

**Figure 13.5:** Alice and Bob can record the entire commercial process of trade on the blockchain

A very detailed explanation of these business processes and how to implement smart contracts on a blockchain along with various technicalities and the use cases with the success scenarios of these implementations are detailed out in the below-mentioned blog. It is recommended to read through the blog for getting an understanding of a formal legal smart contracting solution:

**[https://craigwright.net/blog/Bitcoin-blockchain-tech/creating-a-smart-contract-registry/](https://craigwright.net/blog/Bitcoin-blockchain-tech/creating-a-smart-contract-registry/)**

Most of the financial messages currently use EDI is an existing encoding scheme for commerce. We can see the ANSI and EDIFACT message formats in *[Figure 13.6](#c13.xhtml#fig13_6)* below:

![](images/Figure-13.6.jpg)

**Figure 13.6:** EDI messages (ANSI and EDIFACT formats) currently used in commercial trades

In our system, we can use the same formats of data mentioned above in *[Figure 13.6](#c13.xhtml#fig13_6)* and add them to the Bitcoin transactions (as messages). Again the usage of Bitcoin blockchain removes the need for something called an Interchange envelope or message which is typically a trusted middleman which now can be removed when using such a messaging scheme which is secure. Full implementation of the process on the blockchain will look something like as shown in *[Figure 13.7](#c13.xhtml#fig13_7):*

![](images/Figure-13.7.jpg)

**Figure 13.7:** Entire commercial process of trade on the blockchain without the middleman (interchange envelope)

With that understanding, we can now move on to the implementation of these ideas on creating tokens, financial messages, and even digital currency on the Bitcoin blockchain and how that is being done.

# [Tokens and Bitcoin](#toc.xhtml#s263a)

Tokens were always meant to be part of what Bitcoin has been designed to achieve. The very first attempt towards this direction was done back in 2012-2013 as something called colored coins.

Colored coins were an idea to add information such as a certificate in a Bitcoin transaction which acts as a legal promise to pay to the receiver by the sender. The sender in this case becomes an issuer of this certificate which is stored as a transaction on the Bitcoin blockchain.

One of the first ideas of building a smart contract came out of the movement towards building colored coins, in fact, ethereum was also born out of this movement as Vitalik was involved with work that was being done with colored coins. Ethereum took the route of taking this idea of doing something more than payments to building and running any program that can be run on a normal computer to be allowed to be run on an ethereum supercomputer. To enable that, ethereum must provide a large compilation and computing mechanism which was done in a form of **Ethereum virtual machine (EVM)** to be run by all of the miner nodes. This is still the bottleneck for ethereum network being able to scale to very large volumes as all computation on ethereum is replicated 1000s of times (same as the number of miner/nodes) producing the same results which are quite a redundant process if you see from a larger perspective making it impossible for ethereum to be able to solve the scaling problem.

So how do we implement tokens on Bitcoin blockchain?

The basic operations required for implementing tokens on a blockchain provides the underlying solution to double-spending and overall ledger aspect of things. In addition to that there are three basic operations that are needed to be done for implementing tokens:

*   Issue a token
*   Transfer tokens (send and receive tokens)
*   Monitor tokens (check balances, monitor transfers, etc.)

Let us look at these operations one by one.

# [Issuing a token](#toc.xhtml#s264a)

To issue a token, there will be a few steps involved:

*   Issuer broadcasts issuance transaction (transaction with metadata added to the transaction)
*   Issuance transaction contains information about tokens such as Token name, number of tokens, and the protocol used for the token issuance.

# [Transfer tokens](#toc.xhtml#s265a)

To transfer tokens, token owners will construct a Bitcoin transaction that will have the instructions of the number of tokens to be transferred along with the information about the sender and receiver of tokens. This could be done by adding this data either in the script` (PUSHDATA)` or` OP_RETURN` data.

# [Monitor tokens](#toc.xhtml#s266a)

There needs to be a mechanism that will monitor the blockchain at all times for transactions that have any metadata related to the tokens that are issued. This monitoring will also involve an element of validating if these transfer instructions are valid and complying to the rules defined while issuing the tokens so as to make sure no fraud happens:

![](images/Figure-13.8.jpg)

**Figure 13.8:** A typical standard implementing tokens on Bitcoin blockchain and various operations involved

All of these ideas were there in Bitcoin since 2012 but due to various limitations that were imposed on the protocol, not much was done. `OP_RETURN` was the only way to implement tokens and that severely restricted the number of bytes that could be written for various functions for the tokens. In that duration around 2015 ethereum was launched and the complete movement of developers creating these smart contracts and tokens shifted to ethereum. After the chain splits and removal of imposed limitations from Bitcoin, there is a lot of progress made in terms of making these ideas into a much more formal and legal manner when it comes to implementation in the real world. The most formal attempt for this is our next topic known as the Tokenized protocol which does a whole lot more than just providing coloring of coins for asset registry and certificate issuance.

# [Tokenized protocol](#toc.xhtml#s267a)

Smart Contracts not just can provide a solution to a lot of use cases where actual contracts are negotiated and created as we have seen, the tokenized protocol provides for a broader range of use cases and a full-featured application layer protocol utilizing Bitcoin blockchain for passing and storing messages. As defined in the documentation for the protocol, quoting:

*"The protocol focuses on data (aka records) captured from financial, legal, commercial, and accounting activities for all types of legal entities and ownership structures. It aims to replace current financial messaging (e.g. bank to bank (SWIFT), security exchanges (FIX), and fiat payment systems (credit cards, e-money, etc.), as well as other EDI standards like X12, etc. However, it also provides the framework for issuing any kind of token for any type of use case.*

*The protocol utilizes smart contracts, tokens, registers, and messages as the building blocks to provide users and issuers with all of the tools required to manage their financial and legal lives in a more secure, private, and low-cost way - while at the same time providing streamlined user experience."*

# [Details of the tokenized protocol](#toc.xhtml#s268a)

Tokenized protocol, as the name says, is a protocol that is created to create and manage tokens on top of Bitcoin blockchain. It has two components, an autonomous manager of these tokens called Smart Contract and a Tokenized wallet which does the management of tokens.

Before we go further, we need to also have a look at what is a token. As the meaning of the word goes, it is a representation of an underlying asset. The tokenized protocol is an open-source (Open BSV license) method built on top of Bitcoin blockchain (using metanet data structures) to provide a full-scale solution for creating, managing, and accounting of these tokens which represents an underlying asset. We will here on, focus, and define all the terms in the way the tokenized protocol treats these words and explore in detail how the complete system works.

A token is a digital record of ownership that is managed by a smart contract. A smart contract in this system is an electronic contract that is a dynamic contract (as we saw in the above section) which is managed by an autonomous agent (off-chain daemon) using the methods defined in the tokenized protocol. It acts on behalf of the issuer of the contract to perform all of the administrative tasks associated with creating, maintaining, and updating the contracts on-chain records. A token could represent the ownership of property, shares of a company, movie tickets, loyalty points, and much more.

A Smart contract does the records management for a token which uses Bitcoin blockchain for storage and that being only a small part of the system. Commerce requires receipts, purchase orders, invoices, titles, contracts, securities, etc. for the participants involved and all this can be done using this proposed system in a safe, easy and affordable manner.

All of these records are generated as a result of various relationships that are formed between various entities when commerce happens. A typical structure of these relationships are shown in the below diagram:

![](images/Figure-13.9.jpg)

**Figure 13.9:** Typical relationships with various entities a business maintains (using contracts, documents)

The private company shown in the above can use smart contracts and tokens for the management of various administrative and accounting tasks of an issued contract. When done that, it becomes an Issuer. Tokens are issued by this issuer and is the legal owner of the assets and liabilities associated with the issued tokens. Once the smart contract is created and tokens issued, the smart contract can work with other autonomous agents working on behalf of the issuer or other contracting parties to fully automate the business processes and tasks associated with the formation and performance of that contract.

On the technical side of things, the tokenized protocol has two main components:

*   **Smart Contract:** An autonomous agent service, hosted by the issuer or a third-party provider on behalf of the issuer.
*   **Tokenized Wallet**: An enhanced Bitcoin wallet, operated by the user or administration of the contract issuer.

A tokenized smart contract is written in Go (language) and is a fully open-source with an Open BSV license. The complete codebase is present at their GitHub repo at **[https://github.com/tokenized](https://github.com/tokenized)**

We will not be going into the implementation details as that information is present and documented in their GitHub and website but we will look at the concepts described for understanding this implementation so as to understand how smart contracts can be created, managed and monitored in a perfectly legal way using the Bitcoin blockchain.

Tokenized has a whole set of business processes and entities defined in the protocol to match up to various real-world entities and business functions for business processes. The smart contract exists as a state published on the Bitcoin blockchain and monitored by oracles. Various user and admin actions change the state of the smart contract assets from one state to another which is again captured in entirety on the blockchain. The diagram, *[Figure 13.10](#c13.xhtml#fig13_10)* below shows on a very high-level various entities and tasks associated with a smart contract, and the system tokenized protocol proposes for creating and maintaining such a system.

![](images/Figure-13.10.jpg)

**Figure 13.10:** A very high-level overview of various entities, operations, and participants of a smart contract managed on a blockchain

The tokenized protocol defines all possible business functions and participants for a smart contract which can be managed using the Bitcoin blockchain as the immutable storage media for the dynamic contract in the discussion. The above diagram shows a very high-level representation of this implementation. Let us understand this diagram with various concepts around it as shown in diagram one by one.

# [Contract operator](#toc.xhtml#s269a)

An issuer can operate their contract or they can appoint a contract operator (typically a technical service provider) to operate a contract on their behalf. A typical analogy will be the outsourcing of email management to Gmail who is a technical service provider for email infrastructure for organizations.

A contract operator will manage the following operations:

*   Creating a contract using a contract offer ( with info such as name, governing law, jurisdiction, contract rules, voting system, identity details of the issuer, and other entities.
*   Contract formation (in response to contract offer)
*   Updating a contract
*   Contract amendments
*   Contract address changes (like public address and keys that might get misplaced, lost)

# [Token Holders](#toc.xhtml#s270a)

Token Holders are entities (users or participants using tokens, shown in the right of *[Figure 13.10](#c13.xhtml#fig13_10))* that legally own the asset represented by the token held (in a Bitcoin address).

They are the owner of the property that the tokens represent. If the tokens are for a movie screening, the tickets that are issued on the blockchain as a token are distributed by sale to people who want to see that movie making them token holders. But in a more standard setting, a company tokenizing their shares will make a shareholder a token holder.

# [Transactions](#toc.xhtml#s271a)

All Tokenized transactions are Bitcoin P2PKH transactions (pay to a public key hash) and use `OP_RETURN` to add the tokenized actions in the transaction. We have seen that the `OP_RETURN` output transactions become unspendable due to the script stopping the processing as it encounters `OP_RETURN` opcode. Typically the unspendable output values present in the transaction still need to be of the lowest value possible known as dust value (546 satoshi). Dust value transactions are dependent on the minimum allowed fee by the miners to process a transaction, and miners charge fee based on the number of bytes (1 P2PKH input ~148 bytes, 1P2PKH output ~34 bytes = 182 bytes) and was fixed at some point in time to be 3 times (182\*3 = 546 satoshi) of the min bytes possible in a transaction. The expectation is that this dust limit will go down significantly once the number of transactions scale-up and miners have significant fee earnings from the transaction volumes.

All user and administration driven actions are initiated by sending a request to the smart contract on the Bitcoin blockchain, to perform a certain action. If the request is valid, the smart contract will respond by sending a response transaction containing updated information about the contract or asset (new balances, updated revision data, etc).

All of the above-mentioned request and response actions in this system are Bitcoin transactions with data structure embedded in the `OP_RETURN` for contract level information again, structured using something called envelope protocol which can be read in more details via the link: **[https://github.com/tokenized/envelope](https://github.com/tokenized/envelope)**

The data structure describes the actual format of the `OP_RETURN` script:

**[https://github.com/tokenized/envelope#data-structure](https://github.com/tokenized/envelope#data-structure)**

The transactions are BitDB compliant in their format, i.e. they can be queried using Bitquery. The envelope protocol system supports Metanet protocol by allowing you to specify that a public key in the input is the metnet node identifier. More details are present in the above links.

A great explanation and example of the process of Mary sending some tokens to her friend bill are explained in a visual format in the tokenized documentation which is essential to look at to get an understanding of how the transactions, dust limits, and token transfer is done. Below diagram shows the basics of a transaction which is used by Mary (who has 155,000 tokens to transfer 15,000 tokens to Bill):

![](images/Figure-13.11.jpg)

**Figure 13.11:** Typical Tokenized transaction (image source: [https://tokenized.com/docs/concepts/transactions](https://tokenized.com/docs/concepts/transactions))

# [Operations](#toc.xhtml#s272a)

The tokenized protocol operates on a request and response mechanism whereby operations are carried out in 2 steps called **actions**. The only exceptions to this rule are the Message action and the Register actions where each action does not work on the request and response model. They are 1 step actions where no response is required.

The request and response actions are always initiated by two different classes of actors, the requester, and the responder, and the definitions are as follows:

*   **Requester**: The issuer, user or contract operator (on behalf of the issuer)
*   **Responder**: The smart contract instance

There are various operations defined which are related to Contract, Asset, Transfer (of tokens), Governance, Enforcement, Register, and message operations which are described in details at the protocol documentation if you are interested into details: **[https://tokenized.com/docs/concepts](https://tokenized.com/docs/concepts)**

The documentation provides the details of all of the various operations and rules that are present to create and administer a contract which can be gone through using the above-mentioned link and also present in the *[Figure 13.3](#c13.xhtml#fig13_3)* which change the state of a contract from one to another which can be read through in the documentation:

*   Rules
*   Governance
*   Enforcement
*   Permissions
*   Registers
*   Messaging

# [Tokens](#toc.xhtml#s273a)

A token is defined as a digital record of ownership that is managed by a smart contract, which can be thought of as a digital entry in the ledger that records ownership rights for a certain entity for a given asset, including any subsequent changes to this ownership. All this is recorded on the Bitcoin blockchain. The owner of the asset controls the ownership using the private key for the public key the tokens are associated with in terms of ownership.

There are various types of tokens that can be created using the Tokenized protocol like:

*   Coupons
*   Loyalty points
*   Membership
*   Common share
*   Admission ticket
*   Currency

The tokenized protocol provides a detailed administration (Asset Management, Asset transfers) of these tokens and the details are present in the product documentation if you want to read a more detailed overview of all operations and actions for Asset Management and Asset transfers aspects for these tokens:

**[https://tokenized.com/docs/concepts/tokens](https://tokenized.com/docs/concepts/tokens)**

# [Oracles](#toc.xhtml#s274a)

An oracle in the context is an agent that monitors, manages, and verifies real-world events/people /information (off-chain data) and provides a trusted source of data feed to the smart contract. They provide the necessary link from the blockchain to the real world.

There are various types of oracles:

*   **Identity Oracles**: The smart contract interacts with a trusted source of data and that is ensured by identity oracle. They manage a database with user identities which are verified (it could be pseudomonas as the only oracle will know the actual user identity, no one else). The many use cases include restrictions of token transfer to ID-verified users (who are KYC, AML, GDPR compliant, restricting transfers to certain age groups, regions, countries, etc. Oracles will allow the transfer only when there are no restrictions, else they respond with a not-permitted flag.
*   **Authority Oracles**: These types of Oracles can work on enforcing various governance and regulatory rules like enforcing court system rules, and documenting on-chain proofs for the wrongful conduct like stolen tokens in property disputes, etc. This is currently not implemented in the protocol but will be in a future time.
*   **Event Oracles:** These are oracles that will track the results of real-world events like a cricket game result, weather condition change, etc. 
    
    The above overview of the tokenized protocol gives a brief overview of something which is a very detailed protocol with excellent documentation with examples including the creation of an actual smart contract for a frequent flyer and movie ticket token issuance. All those details are available at the documentation present on the product documentation page and I would highly recommend going through it in a detailed way to be able to implement this protocol for your specific use case. The tokenized protocol is for the first time a detailed implementation of a legal and regulatory compliant framework with automated contract management which can bring a huge amount of value to so many business use cases that one can think of in financial, asset management, Governance (like election voting) and many more industries, leaving only imagination as the limit. All that with perfect storage and metanet like hierarchical ownership management providing unmatched security features will certainly become one of the sought after implementations by businesses in the future and will lay down the base for creating a new financial system which is on-chain.
    
    Tokenized protocol is one of the most mature and legal framework for issuing tokens on any blockchain (unlike ICOs on ERC20 token protocol which are now being established in courts as illegal securities). This protocol is expected to be used for plethora of use cases but the most important one being issuing of a digital currency or CBDC for a country/central bank.
    

# [Run platform](#toc.xhtml#s275a)

Run is a platform to build Apps and tokens on Bitcoin. Run lets you put pieces of your application/software on the chain like your code, views, APIs, Functions, Data, and something they defined called Jigs on the Bitcoin blockchain to enable reuse of all of these components. Jigs are defined by the platform as interactive objects that people own, so it could be tokens, assets (like tickets, posts, cards, votes, battles in a video game, etc.). It's defined as interactive as these Jigs are interchangeable. So in other words what RUN does is, it converts every component of application software into these Jigs (by tokenizing them and converting them to Jigs) and allowing various developers, creators to club them together by retaining their rights of creating using the Jigs and making the application as a whole with these components.

![](images/Figure-13.12.jpg)

**Figure 13.12:** A Run platform collaborating in an application using Jigs

It could enable democratizing of overall software development where artists can simply create small components and make them available on sale using these Jigs for anyone to use these components. A good example would be, a twitter thread, in which the creator talks about developments happening in quantum computing and she keeps it updated now and then running it for years. She will be the content creator, the viewer/readers/advertiser will be the Users and the twitter platform will be developers. Right now, it is the twitter platform which has a business model and is monetizing it and earning revenue from this interaction. In the new model, an advertiser can decide to compensate the creator for this content directly by sponsoring the thread, the readers and viewers of the thread and the platform hosting the thread, all three can get the share of this advertising revenue.

The most important aspect of this platform is that it does not need any new language (like solidity) but simply is built using JavaScript. The complete set of functionality is provided by a Run.js library that can enable you to create jigs just by simply extending the class (of your asset) and defining your digital property. You can also create tokens just by extending the property class you created using Tokens as shown below:

![](images/Figure-13.13.jpg)

**Figure 13.13:** code snippet creating new asset and tokens using simple JavaScript and just a few lines of code

Run does a lot more than just these features and it is possible to use anywhere you can use JavaScript, your browser to your NodeJS server, and comes with full function SDK. Currently many projects like Cryptofights, True reviews, etc. are few examples of projects that are using the Run platform for tokenization and smart contracts on Bitcoin blockchain. More details are present at **[http://runonBitcoin.com](http://runonBitcoin.com)**

# [Bitcoin | Computer](#toc.xhtml#s276a)

Bitcoin Computer is a project that has been in making for a few years since 2018 where the initial idea was implemented as a protocol called **The Bitcoin Token.** The project was then morphed into what is now called Bitcoin Computer, and let's have a look at what it is and how it works.

A typical computer can be broken into components like CPU, a message exchange bus, and memory to store computation results and data. *[Figure 13.13](#c13.xhtml#fig13_13)* shows a representation of a traditional computer that can do computation using CPU, stores data using memory, and provides Input and Output as desired. A parallel to the blockchain is in place of CPU, the computation and validation are done by a miner network, and storage happens on a much more advanced form of memory of blockchain. The difference being, the computation power of miners is quite small.

![](images/Figure-13.14.jpg)

**Figure 13.14:** A traditional computer components compared with Blockchain like Bitcoin

In a system like ethereum this component is the same as the traditional computer where a full-scale CPU kind of computing is available with miners. Bitcoin Computer in a way does what ethereum can do (high-level computation) with Bitcoin blockchain by combining the below shown two systems and creating a syncing method that is used to store the results of the computation done on a traditional computer on the blockchain as shown in the *[Figure 13.4](#c13.xhtml#fig13_4)*. In addition to the idea of a single user, since blockchain is something that is built for a multi-user environment, this kind of system can allow a multiuser system working on its own, using blockchain to share common information. *[Figure 13.15](#c13.xhtml#fig13_15)* below shows a diagrammatic representation of such a system. The diagram showed two users but you can easily see this could be n number of users working simultaneously with the same blockchain:

![](images/Figure-13.15.jpg)

**Figure 13.15:** A representational model of a Bitcoin|Computer system

If you see in the above diagram, the multiple users using the middle system in the blockchain can share the same code and by synching it, they can pretty much see the same code in real-time. This is quite a powerful idea which in effect makes the Bitcoin computer in a way like one single computer which can be used by any number of users across the world. The Bitcoin computer brings two huge benefits apart from the standard attributes of a computer, One, Money which is inbuilt in the system as we know and Two, the property of storing the ownership of the money (UTXOs).

The attempt for enabling things like smart contracts on a blockchain that Ethereum made had a large benefit which was the programming language called Solidity which is very similar to JavaScript creating a very small learning curve for existing developer pool to start looking at and using a blockchain platform but it still needed a learning curve for developers and enterprises face the challenge of finding developers who are versed with this tech skill set. Bitcoin Computer eliminates this curve by enabling the use of JavaScript as the programming language. Now when you create an object (asset to register to be tokenized) and create tokens, it all can be done in simple JavaScript code.

The way Bitcoin Computer implements using of local laptop/computer in conjunction with blockchain is that, whatever code a user creates for a smart contract, is pushed to blockchain along with the identity and ownership via public key, any other party can access the same code once it is synced (using Bitcoin transaction) with blockchain. The object classes can be constructed such that the editing ownership of the same piece of content can be transferred from one user to another enabling not just simpler use cases but also real-time contracting for example in games. This enables the multi-user collaboration with the same piece of code, content, or a document, which could be a business contract enabling the whole gambit of smart contracts, tokens, and much more possible to be built on the Bitcoin computer system. More than everything else, it is possible to build just using vanilla JavaScript.

Implementation details of this system are explained in the documentation of the project present at GitHub link: **[https://Bitcoin-computer.gitbook.io/docs/](https://Bitcoin-computer.gitbook.io/docs/)**

NPM package: **[https://www.npmjs.com/package/Bitcoin-computer](https://www.npmjs.com/package/Bitcoin-computer)**

# [Conclusion](#toc.xhtml#s277a)

We have reached to the point where we have looked at most of the advanced protocol and concepts which are needed to be understood and learned to be able to architect and design an application which could be BaaS (blockchain as a service), Serverless, or completely built on blockchain (both frontend and backend). We have looked at how complex business contracts can be implemented much more efficiently, securely, and deterministically using the advanced attributes that a blockchain like Bitcoin provides. There are very large goals that some of the projects we have discussed in this chapter carry, like Tokenized which aim to replace all of the existing methods of the supply chain, financial dealings from the traditional silo/paper-based systems to a shared ledger of Bitcoin blockchain to make overall business operations cost-efficient, transparent and real-time. With services like BDI (blockchain data interchange) replacing EDI (electronic data interchanges) we see a silent revolution in the offing for the world which currently struggles with many limitations of application infrastructure with lacks the kind of security, availability, and resilience that real-time real large scale applications need without spending a very huge amount of money to run and maintain them.

We have learned most of the prominent protocols in this chapter to create and maintain smart contracts and tokens. There were few other attempts which were made in the last ten years which could not go further beyond an MVP stage (like SLP or simple ledger protocol, Colored coins, Bitcoin token, Gear SV smart contract, etc.), but the learnings from them have been taking forward in the future projects that came into being. This is going to continue in an emerging technology space where, I would say, the sky is the limit.

In the next section and chapters, we will start concluding the book with a discussion on how blockchain is an ideal data structure for implementing an AI and how the whole industry will benefit hugely with the data structures provided by the blockchain. We will also discuss how emerging industries like IoT and smart devices are the ideal use case for a blockchain like Bitcoin which supports microtransactions. We will also look at the legal and regulatory aspects of it all before we conclude the book.

# [Questions](#toc.xhtml#s278a)

1.  Why is it so necessary to have legal smart contracts, why can't just be the agreements coded and uploaded on the blockchain?
2.  What is the key difference between Tokenized and Bitcoin | Computer protocols? Think of which use cases where they will be more suited for and not.
3.  Why are oracles needed for automating tasks in smart contracts and how do they optimize cost for maintenance for these contracts?
4.  How do token holders establish ownership legally for their tokens in the tokenized protocol?
5.  Why does a protocol like Run is best suited for gaming user actions being tokenized?

# [Section - III](#toc.xhtml#p03)

# [CHAPTER 14](#toc.xhtml#c14)

# [Going into Future: AI/ML, Big Data, and IoT](#toc.xhtml#c14)

**"In life, unlike chess, the game continues after checkmate."**

*― Isaac Asimov*

The future is constantly evolving, what I mean by that is we create the future by building what it will be, but it is evolving which means that there is a certain element of randomness which is always present and that provides for the possibility of exploring and finding something new and destroying old. What will be the future, will continue in the current model of the internet, or it will be where Bitcoin is used for global applications, is yet to be seen, but a lot will depend on what this ecosystem will create. Today as we stand, we see that devices are becoming smart, data is becoming huge (not just big) and machine learning is yearning to be AI. With all that going on, how will Bitcoin blockchain play a role in it? Will it provide a system that will harness the core benefits of a blockchain (user privacy, cost-effective transaction system, and traceable record keeping) to enable the building of applications of the future, or will another system be used for those emerging technology landscapes? This chapter looks into the details of the assertion that Bitcoin blockchain will become the de-facto standard for building these systems.

# [Structure](#toc.xhtml#s279a)

*   Automata on blockchain and various other concepts
*   Autonomous agents and DACs using the Bitcoin blockchain
*   IoT and Bitcoin blockchain
*   Big Data and solving the data breaches

# [Objective](#toc.xhtml#s280a)

After studying this chapter, you will be able to understand the basics concepts of building automata on the blockchain, how a blockchain is an ideal backend infrastructure for building AI/ML and neural nets. You will also learn about IoT based infrastructure that is built on blockchain and how blockchain-based mini OS are ideally suited for small and any size devices and are looking to transform the IoT industry.

# [Artificial Intelligence and Blockchain](#toc.xhtml#s281a)

Data scientists have struggled since long even till today, about one thing, when they work on creating models using machine learning or any AI-based solution, that is, the quality of the dataset/data they have either is always low, or too expensive making it very difficult for them to be able to work with it.

On the other side, blockchain as a highly secure, reliable, and always available storage medium presents a first of a kind opportunity where its immutability protects data integrity providing a high-quality data repository.

Artificial intelligence and blockchain the two fields which can converge and have been largely speculated that they are the ideal match for each other. However, their intersection needs a bridge to connect them, which is big data. AI and Machine learning neural nets are hungry for data and the better-structured data the better they perform. That is where a blockchain like Bitcoin which records everything (like user actions, events, financial transactions) all in a well-defined and structured manner comes as the missing link that these AI/ML algorithms are hungry for.

The biggest challenge of data either being isolated in siloes, unstructured data, and distributed systems not being able to talk to each other are things that are a big struggle for these algorithms to work efficiently. For a blockchain to provide for this, it needs not just big transaction capacity (millions of transactions per second) but also large data storage capabilities which you can guess by now, Bitcoin becomes the only blockchain that exists today that provides. Once you have the data dictionary and the data in a structured format, the possibility becomes immense for building many different types of automata/autonomous agents/oracles, running neural nets, building PSOs, building CNN/RNN and pretty much any other implementation of machine learning algorithms facilitated by high-quality data.

A combination of AI and Blockchain could provide the ideal solution for the Internet of things (IoT), building decentralized organizations managed by agents for operations, and much more. As a turing complete machine is built using Bitcoin script there are a plethora of opportunities that open up once we look at Bitcoin as an immutable and unbounded turing tape offering the perfect platform for implementing evolutionary algorithms.

Let us look at some basic concepts of building these automated agents and algorithms on a blockchain and how that process will work.

# [Automata on blockchain](#toc.xhtml#s282a)

People who have been working in the space of AI and Machine learning will be familiar with the concept of automata, but for the ones who are new, let us start with what is an automaton.

The concept of Automata comes from Cellular automaton (singular) or Cellular automata (plural) was introduced by *John von Neumann* back in 1951. It was described as a discrete model that consists of a simple two-state, one-dimensional grid of cells that can be either on or off. Later in 1970, *John Conway* introduced a two-state, two-dimensional cellular automaton named Game of Life. It was later in the 1980s when *Stephen Wolfram* came into this field and became almost the pioneer of this study. He saw it as such a large field of science which was much unexplored, lacking tools and methods overall that he had to invent new mathematics and in a way new science to study these computational models. The complete work is published and available online as The *new kind of science,* which is available at the resources website: **[https://www.wolframscience.com/nks/](https://www.wolframscience.com/nks/)**

Wolfram for the first time did a systematic study of two-state one dimensional cellular automata and called them elementary cellular automata which he proved are turing complete. He went on to define various types of these elementary cellular automata which using certain rules can change their state from one to next and in doing so can demonstrate complex behavior (simple systems working together to manifest complex behavior, like nature or biology). He classified these rules as Rule 30, Rule 110, Rule 250, Rule 90, and so on. Each rule made the cellular automata to manifest a different pattern/property as shown in *[Figure 14.1](#c14.xhtml#fig14_1):*

![](images/Figure-14.1.jpg)

**Figure 14.1:** Behavior of cellular automata following different rules to change state from one to other simulated 1000s of times using a simulation program.

You can read more about how this simulation works in the book, new kind of science, *[Chapter 2: Economic Model and Network Structure](#c02.xhtml)* if you are more interested in learning this and we will keep the details out of scope for this book.

Overall, it is possible to design a blockchain-enabled system of autonomous agents that can perform a variety of functions, in commonly known terms these autonomous agents are also known as bots (shorthand for Robot, used for external autonomous agent) comes with attributes like it is external to the system that it runs on, it is autonomous, which means it is self-controlled stand-alone and an agent, meaning it is running or executing logic on behalf of a client.

Typically bot is used in conjunction with many other bots, forming a bot-net that typically operates on many interconnected (using the internet) computers. This bot-network can run on another peer-to-peer network in parallel to the Bitcoin blockchain with an overlap due to its interaction with the blockchain.

One such detailed implementation of blockchain automata is described with detailed specifications by *Dr. Craig Wright* in his blog including how a company can implement such a system. *[Figure 14.2](#c14.xhtml#fig14_2)* shows a brief snapshot of such a process.

More details: **[https://craigwright.net/blog/Bitcoin-blockchain-tech/managing-blockchain-automata/](https://craigwright.net/blog/Bitcoin-blockchain-tech/managing-blockchain-automata/)**

![](images/Figure-14.2.jpg)

**Figure 14.2:** A setup for implementing the automata management system of botnets using a service provider

Needless to say that a technically equipped client can set up all of this on their own but that is just a choice. The above-mentioned link also contains an example and details of how each of the above-shown components will work, most of the technology is protected with patents and available with Open BSV license for building on the Bitcoin blockchain.

# [Deterministic Finite Automata (DFA)](#toc.xhtml#s283a)

DFA is a technology innovation that details the techniques for implementation of automation for executing tasks, processes, contract execution (smart contracts), and more on a blockchain system. This invention can be viewed as an implementation of a state machine on a blockchain by using the UTXO system to represent the state of a machine and transaction which changes the state of the machine from one to another.

The details of the technology are present in the patent for interested readers: **[https://patentscope.wipo.int/search/en/detail.jsf?docId=WO2018078584](https://patentscope.wipo.int/search/en/detail.jsf?docId=WO2018078584)**

A good explanation for the same is presented for readers in the below-mentioned articles by *Dr. Craig S Wright* who holds the above-mentioned patent.

The main intention of this paper is a codification scheme which allows the determination of the state of a DFA on the fly and is described in details in the below-mentioned link by the creator of the scheme:

**[https://craigwright.net/blog/economics/a-codification-scheme-for-state-machines/](https://craigwright.net/blog/economics/a-codification-scheme-for-state-machines/)**

With this codification mechanism, an explanation of the compilation and execution of a DFA is described in the below-mentioned link:

**[https://craigwright.net/blog/Bitcoin-blockchain-tech/dfa-compilation-and-execution/](https://craigwright.net/blog/Bitcoin-blockchain-tech/dfa-compilation-and-execution/)**

The above set of technologies (Automata, DFA, etc.) implemented on a Bitcoin-like blockchain can act as oracles (similar to what we discussed in *[Chapter 13: Smart contracts and Tokens](#c13.xhtml)*) and can perform most of the administration and management of certain business functions on behalf of a user/client. These type of systems and automation are also possible in a traditional system but the problem is that their implementation and maintenance cost becomes quite high due to the work needed to define and create such a system, find the niche skillset of personals who can implement and then maintain this kind of system, including the operational cost of the infrastructure. Such an implementation on a blockchain is quite a low cost and robust alternative.

# [Decentralized Autonomous Corporations](#toc.xhtml#s284a)

DACs or also sometimes referred to as Decentralised autonomous organizations or DAOs are a much seeked after achievement to implement using a blockchain due to the inherently decentralized non-trust based system like Bitcoin blockchain. Being able to create such an entity will eliminate the centralized nature of the currently existing large corporate organization making them more transparent and fairly governed.

At least that was the idea when such an implementation of a DAO was done on the ethereum blockchain, which was famed to be the hallmark of using smart contracts to create encoded rule-based governance making an organization fully decentralized, and in theory, this particular implementation was meant to operate like a venture capital fund for cryptocurrencies which is governed by a fully decentralized ruleset coded as a smart contract implemented on ethereum blockchain. Its launch back in May 2016 attracted huge attention with people using ether to buy DAO tokens reaching up to crowdfunding of 12.7 Million ether or about 250 million (20 USD per ether during that time). The idea was that this fund will be given to anyone who can pitch their idea to the community and get funded via DAO tokens. It however did not last long as in June 2016, a hacker who found a loophole in the code of DAO drained about 3.6 million ether (about 70 million USD). The hacker used recursive calls to the smart contract to withdraw the same funds again and again before the ledger was updated exposing multiple flaws in the codebase of DAO. This was one of the times when the world saw that a ledger can be reversed and in this case, it was done by forking the ethereum chain into a new chain (ETH) and leaving the old (ETC) chain which was the original chain with hacked transactions. This also caught the attention of the US SEC and they classified DAO tokens as securities subjecting them to a full set of regulatory oversights as a company's IPO. This was pretty much the end of a utopian idea that decentralized organizations can be created which do not need to follow regulations like a traditional company has to.

This is possible to implement on the Bitcoin blockchain where it is possible to build a robust and secure system. A DAC in this setup is defined as a corporation without the need for any central point of control, with a certain business goal, plan, and protocol. Many decisions could be made in advance and coded for autonomous agents to execute them making it possible for no need of human interaction, still keeping the ownership of the entities with humans making it possible for them to keep the capital and decisions with them but in a decentralized manner using a voting agent system (all rules would be defined at the creation of such a system). Setting up an **Autonomous agent (AA)** it is possible to create the signing of transactions based on a multi-signature voting system (for e.g. 501 of 1000 etc.) making the decisions completely decentralized. This is made possible by novel **secure multiparty computation (SMC)** protocol, named as threshold signatures which we discussed in *[Chapter 11: Real-World Applications](#c11.xhtml)* described in detail at the link: **[https://nakasendoproject.org/Threshold-Signatures-whitepaper-nchain.pdf](https://nakasendoproject.org/Threshold-Signatures-whitepaper-nchain.pdf)**

SMC is what differentiates Bitcoin blockchain-based DACs with what was implemented in ethereum as DAO or any other implementations. Using the SMC protocol, Autonomous agents and smart contracts on Bitcoin blockchain, it is possible to build companies which are distributed corporations (could be the size of a large multinational corporation like distributed Amazon) where it literally can do on even if a particular data center is for some reason destroyed/removed/made redundant.

As long as you are able to create complete secrecy between agents for the same corporation, you only need two nodes to run securely computation (unlike ethereum where it runs the same computation on every node EVM runs on) and can ensure the validity of computation by XOR'ing the results. So if you have two oracles, and they are unaware of each other, that is all is needed for computation.

These AAs are purely software, typically written in a programming language called **PAPAL (ProgrAmming Language)**. These AAs cannot act (to write code, manufacture a product, etc.) without the actors in the physical world dictating so. They are purely agents that work with the predefined ruleset. Typically these AAs are classified into two classes, voting-AAs, and task-AAs.

To elaborate on how big a breakthrough this is, you can set up these voting agents for not just decisions of a corporation, but even for countries like India which is possible as the idea of threshold multiparty signatures is scalable to that extent. It can also be used to issue company shares and shareholders can be given Tokens (which can be used as voting rights) that can act as shares, equities, the grant of ownership, etc. which again, is security in terms of legal classifications, but that is the use case overall with these tokens issued on any blockchain or otherwise.

Voting AAs are empowered to vote, typically a DAC will issue tokens (1 - n) which are like company shares granting ownership of DAC along with voting rights in the same proportion to tokens. Once the ownership is set up using the Voting AAs, task AAs can be deployed which search for unfulfilled tasks and perform them by its ordering preferences. All this could be set up to require human decisions using the voting system by for example publishing a questionnaire for a decision tree type of setup sent to every shareholder making them actively involved in the decision for the organization. The voting will be private and secure since it uses the SMC/Threshold signatures which enables pseudonymous voting enabling autonomy for the shareholders who vote.

This enables setting up global corporations that act based on agents, electronic use, AI, etc. A detailed implementation of such a DAC with an example of an application of digital asset management is present at the below-mentioned link and shown below in *[Figure 14.3](#c14.xhtml#fig14_3)* as a snapshot of various AAs that will become the distributed agent organization:

![](images/Figure-14.3.jpg)

**Figure 14.3:** Digital asset management using various AAs in a DAC. Image source: Article and research paper summary link: [https://craigwright.net/blog/Bitcoin-blockchain-tech/blockchain-based-decentralised-autonomous-corporations-an-overview/](https://craigwright.net/blog/Bitcoin-blockchain-tech/blockchain-based-decentralised-autonomous-corporations-an-overview/)

In the above architecture, various AAs are working on behalf of humans making the organization's operations and ruleset constant and fair for all participants introducing full transparency. However this is only touching the AI aspect of things working with blockchain, and a lot more can be done as we discuss in the next topic.

# [Decision making using Neural Networks](#toc.xhtml#s285a)

We have looked into automated agents and basic automata till now. The same ideas can be taken to do a lot more. The decision making explained in the DACs above can also be done using neural networks / deep learning algorithms which could be used to make decisions in place of the defined ruleset in a DAC. These use cases are dependent if the shareholders do not wish to get involved in the decision-making process and want to use the voting AAs to do that on their behalf or cases when the decision is to be done for making a trade, buy, sell stocks, etc. which can be done better using algorithms and not human decisions.

The decision making can be done using decision trees with a difference to be tied back to Bitcoin by adding a component of option nodes in addition to decision nodes and leaf nodes. Option nodes can allow multiple branching instead of single branching per node based on various criteria (like if a parameter falls between 40-60% times option 1, 60-80% means go with option 2 and so on). Even things like clustering algorithms (like k-mean) can be used to plot the human profiles and strategies stored in a database (blockchain) to be used to make decisions. Another approach could be to use neural networks for decision making instead of using deduction or a collection of rules.

Neural networks rely on the ability to recognize patterns through experience and training and that can be used to make business decisions. It typically is based on inputs, weights assigned to inputs, hidden layers, error functions, etc.

Neural network approaches can be used for voting as well where input data vectors that feed the neural network may be boolean variables, numeric values, stochastic oscillator indicators, or input coming from a set of questions provided to shareholders derived to provide a certain direction to the decisions.

![](images/Figure-14.4.jpg)

**Figure 14.4:** Single perceptron with passive input layer nodes and active output layer nodes using weights to inputs and a sigmoid function to generate output

The implementation of such a neural network will involve a complex network of perceptrons and training of the DAC system with trends and forecasts of possible decisions with error function and bias as in the normal setup of a neural network.

Any system engineering approach can be automated with various inputs and formulas can become the input to neural network algorithms. Equations for insurance, risk, etc. modeling can be done using a 3 layer network as shown in *[Figure 14.4](#c14.xhtml#fig14_4)* below with each node acting as a perceptron and a vote or firing sequence based on the use of threshold and addresses:

![](images/Figure-14.5.jpg)

**Figure 14.5:** A multilayer neural network implemented to make decisions

A multi-layer neural network like the one shown in *[Figure 14.5](#c14.xhtml#fig14_5)* can be used for example to accept data from a risk model and automatically update the risk profile for a customer/organization. Using a blockchain allows for nodes to be funded using Bitcoin and the inputs use the threshold system to send signed transactions to the next layer based on external inputs or other events. It also allows for auditing of the system and the ability to validate the inputs and ensure the integrity of the system.

# [Evolutionary Algorithms](#toc.xhtml#s286a)

Evolutionary algorithms are defined as algorithms defined by mechanisms that are inspired by biology and evolution as it manifests in nature. Typically implementations of these processes are done using genetic algorithms that emulate the way nature's evolution has happened over billions of years.

The implementations of genetic algorithms are mimicking a standard structure of a neuron and various other connections to it by an implementation of a neuron by a cellular automaton (singular). It is little known that one of the first such implementations on a blockchain was done on the Bitcoin blockchain by Satoshi of rule 110 cellular automaton. Working as a tape, Bitcoin forms a 2pda or *two stacks push down automata*' a special case of a probabilistic turing machine that is controlled using the scripting language. Details of how it is possible to implement a rule 110 type 2pda on Bitcoin blockchain is presented in detail in the following research papers.

**Theory:**

*Sgantzos*, K. Implementing a Church-Turing-Deutsch Principle Machine on a Blockchain. In Proceedings of the 12th Hellenic Society for Computational Biology and Bioinformatics Conference, Athens, Greece, 11–13 October 2017; Available online: **https://sites.google.com/site/hscbb17/program/HSCBB17-Booklet.pdf.**

**Practice:**

Implementation of a Rule 110 automata algorithm using Script-like language on a UTXO based blockchain like Bitcoin: *Chepurnoy, A.; Kharin, V.; Meshkov,* D. Self-Reproducing Coins as Universal Turing Machine. 2018\. Available online: **[https://arxiv.org/pdf/1806.10116.pdf](https://arxiv.org/pdf/1806.10116.pdf).**

A lot of this work is still at a very nascent stage and a lot of ongoing work will be coming out in the future but the general idea remains the same as we have been discussing regarding the implementation of AAs on the blockchain. Neural networks like CNN (convolutional neural networks) need good quality data and that dataset that is possible to create on a blockchain is the missing link that will enable these learning algorithms to realize their full potential and what comes out of that potential will be something that will certainly define the future of intelligent systems. In addition to the quality dataset storage medium for these deep learning algorithms, blockchain like Bitcoin also provides the best possible safeguard against any adversarial interference due to security using ECDSA cryptography ensuring security, integrity, and traceability (using the triple entry accounting and provenance). And not just the datasets, even the trained models themselves can also be stored on the blockchain making them fully transparent, and verifiable.

These models once created and present on the blockchain can be made available using a pay per use setup by using the dataset which can also be pay per use. Many applications are already starting to store general data on blockchain like WeatherSV **([https://weathersv.app](https://weathersv.app))** which stores historical location-based climate data on the blockchain or RateSV **([https://ratesv.com](https://ratesv.com))** which stores historical financial data creates excellent immutable dataset for these deep learning algorithms to work on. WeatherSV already offers weather prediction to users in their selected territory by utilizing the data collected by a set of global IoT sensors. This kind of live data feed can be used for many other use cases like logistic management using live data from supply chains for manufacturing, agriculture, or a demographic. Creating a Smart city that is a goal for many governments but not yet able to achieve it, can be made possible with the kind of infrastructure that Bitcoin blockchain provides using storing of data coming from sensors and observers collecting traffic, demographic, supply chain, health, and real-time events and using deep learning algorithms and AAs to come up with decisions that are not possible to be corrupted by any malfeasance.

This has a very large use case in diagnostic medicine as we have seen (*[Chapter 11: Real-World Applications](#c11.xhtml))* EHR data creating a global health record on Bitcoin blockchain, when that data is used, a lot of personalized diagnostic medicine can become a reality without the fear that data being misused for alternate scenarios which are the case right now. It could also mean that patients can sell their data to medical research companies creating new employment and earning opportunities when the traditional job profiles go away.

One thing to note here is that we have looked at evolutionary algorithms, meaning these algorithms learn and evolve by themselves by learning, and Bitcoin from the start had two PSOs running on it, and implementation of rule 110 machine or a wang B machine (effectively a WORM tape turing machine) and rule 30 (randomness generator) for a few years till when the fees of Bitcoin protocol was changed by the concept of RBF causing them to become high and running these self-evolving code (PSOs) was no longer optimal. Since then BSV has restored the original version without script limitations and low fees enabling the running of such algorithms possible again.

# [Machine to Machine communication](#toc.xhtml#s287a)

IoT or Internet of things seems to be the next frontier where it's not just the smart devices, but sensors and machines like drones, monitoring CCTV, driverless cars, and much more. All of these devices capture data and currently that data is stored in central siloes. Storing this data on the blockchain and using it in conjunction with the fundamental property of a Bitcoin system, micropayments solves the age-old problem of a secure and simple system that the machines can use to run.

One of the main features of smart devices is that they are not a fully functional computer, and do not need the complete feature set and processing power as for example something like your smartphone would. Needless to say that modern appliances like television and refrigerator are becoming smarter and smarter with better processing in the systems built in them, but still there will be a large number of devices which will have the need for a mini OS which can run on them with a limited feature set - similar to a limited version of the functionality that runs on wearable devices like a smart watch. In fact, in most of the cases, the IoT devices embedded with electronic circuits, software, sensors, and networking capabilities to enable them to communicate in many cases will be having limited processing and memory capability and will not be able to support large software installation. Further to that, one of the biggest concern based on recent happenings have a large potential to be tempered with and IT security becomes a primary concern (for e.g., Tesla's autopilot was shown to be vulnerable to remote root privilege attacks that could control the steering system and disturb the *autowipers* function).

The ideal solution would be similar to the creation of Watch OS (for apple) or a Wear OS (for Android) for wearable devices by making a slim version of iOS and Android to run on these low memory and processing capability devices. Thus the creation of a generic OS that can be run on IoT devices operating against Bitcoin blockchain would provide a simple, efficient, and robust control functionality while retaining strong cybersecurity along with payment processing capability. A Bitcoin-like blockchain that is perfectly suited for micropayments enables this to support even action or event wise capturing by associating those with a micropayment and storing on the immutable blockchain. In addition to micropayments, things like payment channels or an overpool (*[Chapter 10: Planaria Application Development Framework](#c10.xhtml)*) like a system which can provide a perfect platform to these IoT devices for creating their application architecture which is fast, cheap, secure, and reliable.

Such an invention of a thin OS can revolutionize the potentially billions of smart devices that are expected to come online in the very near future. Such an OS and its implementation are described in the below mentioned in nChain's patent number WO 2017/187397 Al:

**http://patentimages.storage.googleapis.com/92/ea/a4/24bf8330cdf7a3/WO2017187397A1.pdf**

Key elements of such a system are:

*   An OS, purposefully small size and generic to be possible to run on any IoT device.
*   Instruction set which is easily upgradable by not being stored on the device but a secure repository like a DHT (distributed hash table) and loaded to the device from it. The advantage of using a blockchain here is that a tamper-proof recording is done of the location of this DHT enhancing security and verification.
*   Managed by an autonomous agent (either resident on the IoT or external).
*   Interfaces with the blockchain to enable functions including the processing of payments.
*   Robust security (ECC in this case).

Going into the implementation of a sample of such a system is described in the above-mentioned patent, which is also shown in *[Figure 14.6](#c14.xhtml#fig14_6)* below showing a blockchain-implemented method for control and distribution of digital:

![](images/Figure-14.6.jpg)

**Figure 14.6:** An typical IoT device operating system using the Bitcoin blockchain. Image source: nChain's patent number WO 2017/187397 Al.

A BID (blockchain IoT device) is an agent that will manage the IoT device and execute instructions that are stored at another place like a DHT and act as the control agent for the IoT device. Typically the BID will be residing on the IoT device itself. The BID will have its key and IP address so that it can securely communicate with other devices, DHTs, and so on. *[Figure 14.6](#c14.xhtml#fig14_6)*, shows a hypothetical scenario of an IoT device feeding two dogs, A and B who can be fine in each other's presence except when they are being fed. If they get food in the presence of each other they get very aggressive and fight with each other. The BID control system takes instructions from DHT (which will have a truth table with monitoring of both of the dog's sensors and dispense food only when both are not together coming for it.

As you can see in *[Figure 14.6](#c14.xhtml#fig14_6)*, this auto feeder system for dogs will have its instruction set stored in the DHT (a truth table with instructions of reading the sensors of the two dogs, Archimedes and Bernard), Transactions set up to hold a set of instructions to control the IoT and a generic agent. Blockchain is used to store information like the number of feeding, what time that happened, which dog ate, has maximum food dispensed, etc. as per the truth table stored in the DHT.

To discuss the specifics of the implementation of such a device, this auto-feeder of food (for A and B) is a Blockchain IoT device, which is designed to monitor its state and information and act based on it using communication sensors (RFID planted on both Dogs collars). Each RFID associated with A and B is identified using two secret values (S1 and S2) received from a separate control agent as depicted in *[Figure 14.6](#c14.xhtml#fig14_6).*

The BID will keep monitoring the signals from the dog's RFID and when it notices a change in the status of either of the signal, it will retrieve the new instruction set from the DHT to make a decision on what should be its next state. This is simplified here for illustration purposes but in a real device, there will be more instructions to handle attributes like time of the day, number of times to feed, etc. Once the new instruction is received, it will send a signal to a generic agent acting as its control agent (see *[Figure 14.6](#c14.xhtml#fig14_6)*).

The control agent will have stored the feeding action encoded or locked using the locking script for both A and B with their secret value S1 or S2. If the right signal is received, for example, A is nearby but B is far, making the instruction true to feed A, the RFID signal will unlock the locking script present for S1 and effectively it will enable the feeding of A. This also means that every time an unlocking is done, it consumes a Bitcoin transaction and the control agent is going to be set up such that once the transaction is spent, it will create a new transaction for the next iteration.

The step level implementation details are described in the above patent link along with the Bitcoin script that could be used to create such a locking script for the feeder device. There are many finer details that are presented in the patent setwise along with how to create the script which we will keep out of the scope of this book, but interested readers can follow through the patent document to read more from page 9 onwards.

Such a system can be used for many use cases and can provide a solution that is secure and resilient for IoT devices working with Bitcoin blockchain. As the ecosystem matures and more tools and utilities are built, I would expect that this process will become a standard software implementation for IoT due to the unmatched security (ECDSA in Bitcoin transactions) it solves the main concern when it comes to smart devices and its software. This implementation also has the benefit of being a low cost for maintenance to enable a large scale public usage.

# [Big Data](#toc.xhtml#s288a)

The problem with current big data business models is that the data breaches which compromises millions of users' data as we have seen in last few years: Yahoo (1 billion), Marriott (500 million), eBay (145 million), Target (110 million), Uber (57 million), and JP Morgan (75 million). In the case of Equifax 143 million people had their Social Security numbers, addresses, and driver's license numbers stolen. Facebook has personal data on 32% of the world's population. These big data repositories stored centrally at various companies that supposedly need to protect but fail to do so most times of data that is voluntarily handed by users to them put every user of their application at various levels of risk, both financial and life-threatening (in case of medical data).

The role of Bitcoin-like blockchain can be critical, as being the only blockchain which not just stores financial data, but also allows for storage of non-financial data. The beauty of using Bitcoin is that you can give the data to anyone, without losing the ownership and repository of that data by yourself. This is not possible till now and that changes the whole idea of big data the way it is done right now.

Currently, there are many big data solutions that already exist, and with the ever-increasing capturing of data (in the last couple of years, we have created more data than in the last two decades) the question will be how to migrate the existing big data to the Bitcoin blockchain to create a financially incentivized user-owned big data. Companies like Google, Facebook, and twitter who collect petabytes of data every day are taking these big data sets and selling it to advertisers (AdSense makes up the majority of the revenue earned by Google for e.g.). Basically, they are working as data brokerage companies that offer free services to encourage populous data generation and capture the huge sea of data, redefine and repackage that data and sell it to highest bidders.

This particular business model and practices have led to the creation of a lot of concerns as well as regulations like GDPR and the effort to give the ownership of the user data back in the hands of the users. Until now even if a user wants to opt-out of an ad-based system like Google, most alternatives also following the same business model gives hardly any choice. Bitcoin for the first time offers an alternative with a metanet based internet where this model changes to users owning their data. In addition to that, the data store in Bitcoin can be probably the most reliable and available model coming with a security model that will be difficult to breach (ECDSA is much more secure than RSA as well). This creates the solution that big data currently struggles with and the users stand to gain in terms of monetizing their data and for once even able to earn money directly from the advertisers rather than a data broker who makes a bulk of the earning.

This is not just the only case to use Bitcoin's big data capability, in fact, any asset registry system (could be for e.g. Government vehicle registration system or for that matter, voting systems) will stand to gain a lot using this new system of record or ledger. It is not just this side of data, but there will be a completely new data economy where we will see enterprises coming up with new business models for making data available stored in the blockchain and providing it to consumers of data. The EHR data project for creating a global healthcare database on Bitcoin is another use case where Bitcoin's big data capabilities are used.

# [Conclusion](#toc.xhtml#s289a)

We have seen some new ideas and some old ideas implemented on Bitcoin blockchain but have not gone into the details of these implementations beyond a point. That stands for readers to explore further on with the starting points that are covered in this chapter but it should be clear to the reader on some of the basics on how using a blockchain provides an edge overusing the same algorithms and automated agents on a traditional system. Adding the secure identity and ownership of data provided by the blockchain makes it the missing link to the overall future of applications to be built. The hope is that we will see a lot of innovation and implementation on the few basic ideas that we have discussed (DACs and PSOs) making possible distributed oracles for doing calculations and other things that we have discussed in this chapter. This chapter also brings us to the conclusion of the overall discussion of the ideas and application development journey using the Bitcoin blockchain and the Bitcoin protocol.

This Book has tried to keep the discussion and detailing of the protocol to a certain level of abstraction and it is always possible for interested readers to follow the links mentioned for detailed implementation work.

In the next chapter, we will discuss the conclusive aspect of law and Bitcoin blockchain which right now is seen as the biggest roadblock in the mainstream adoption of a public blockchain due to the presence of a coin/money which is not issued by a government.

# [Questions](#toc.xhtml#s290a)

1.  What is a DAC and what are the two main agents needed to create a DAC?
2.  What is a Genetic algorithm and how is it different from cellular automata?
3.  What is the use of an autonomous agent in voting by shareholders for a DAC?
4.  Why is a blockchain-based OS the best-suited system for an IoT device, what are the key components which make them different from a typical non-blockchain implementation?

# [CHAPTER 15](#toc.xhtml#c15)

# [Bitcoin and Law](#toc.xhtml#c15)

**"Government is not, as some people like to say, a necessary evil; it is not evil, but a means, the only means available to make peaceful human coexistence possible."**

*― Ludwig von Mises, Liberty and Property*

The future of any technology lies in its adoption and usage, Bitcoin blockchain is no different from it. Today as it stands the biggest hurdle this technology has to cross is that of law and the regulatory system that currently looks at the technology named Distributed ledger technology or blockchain but not as Bitcoin blockchain as a whole. This is a perception that has held back the adoption of this technology immensely apart from other issues that this tech has faced since its inception. We have looked at many of these issues during the course of this book which we will not revisit, but in this chapter, we will evaluate this technology from the lens of law and how it fits in the regulatory system.

# [Structure](#toc.xhtml#s291a)

*   Bitcoin as property rights
*   Laws and applicability, myths and truths
*   Bitcoin blockchain as a public ledger, a commodity
*   Tax liabilities
*   Permissioned Blockchains
*   Stablecoins and CBDC

# [Objective](#toc.xhtml#s292a)

We will look at the idea on which Bitcoin was created, it being a property right and not what it is perceived to be, a currency. We will also look at the real innovation, a secure public ledger, and how the law applies to such an entity. We will then look at the various myths, separation of Bitcoin and blockchain giving life to the idea of DLT, and why today none of the blockchain/DLT implementations are working on a large scale in production environments used by day to day customers.

# [Bitcoin as property rights](#toc.xhtml#s293a)

One important idea and probably the only completely innovative aspect of Bitcoin is that the public ledger represents a resource set which is available for anyone to update, by making a payment in the form of Bitcoin or Satoshi. This public ledger falls into regulatory ideas similar to that of a property. That becomes the central point of what the Bitcoin blockchain is and what is Bitcoin.

Cryptopia was a New Zealand based exchange for cryptocurrencies. There were two back to back hacking incidents that happened in Jan 2019 which amounted to a loss of USD 18 million leading the exchange to liquidation. The liquidators assessed that the exchange held cryptocurrencies worth USD 100 million giving rise to a dispute regarding those funds. A court case was filed described in the court document as:

*"Effectively, the tussle which is before the Court is one between the creditors of Cryptopia on the one hand and the account holders who have invested in the various digital assets ("the accountholders") on the other."*

**Reference: [https://www.grantthornton.co.nz/globalassets/1.-member-firms/new-zealand/pdfs/cryptopia/civ-2019-409-000544---ruscoe-and-moore-v-cryptopia-limited-in-liquidation.pdf](https://www.grantthornton.co.nz/globalassets/1.-member-firms/new-zealand/pdfs/cryptopia/civ-2019-409-000544---ruscoe-and-moore-v-cryptopia-limited-in-liquidation.pdf)**

At the end the high court ruled that the crypto assets are property even though intangible, and come under the companies' law and the judge, quotes:

*"\[120\] I am satisfied that cryptocurrencies meet the standard criteria outlined by Lord Wilberforce to be considered a species of "property". They are a type of intangible property as a result of the combination of three interdependent features. They obtain their definition as a result of the public key recording the unit of currency. The control and stability necessary to ownership and for creating a market in the coins are provided by the other two features – the private key attached to the corresponding public key and the generation of a fresh private key upon a transfer of the relevant coin.*

*…\[133\] The answer to the question posed at \[46\](a) above is yes. I find that, for the reasons outlined above, all of the various cryptocurrencies are "property" within the definition outlined in s 2 of the Companies Act and also probably more generally. In addition, these digital assets, I find, being property, are capable of forming the subject matter of trust. "*

In defining this, the judge also ruled that the exchange holding the customer coins acts as a trust holding the assets (property) and ruled in favor of the accountholders and the customers of the exchange are entitled to the funds.

This was not the first instance, in 2018, a Chinese court ruled a similar ruling:

"The Hangzhou Internet Court believes that Bitcoin has the value, scarcity, and controllability of property as an object of rights, and it should determine its virtual property status."

**Link: [http://m.caijing.com.cn/api/show?contentid=4603403](http://m.caijing.com.cn/api/show?contentid=4603403)**

A similar ruling was also observed in Russia, a couple of years ago recognizing cryptocurrency as property as well. Link:

**[https://www.rbc.ru/finances/07/05/2018/5af0280d9a7947165a6e8c22](https://www.rbc.ru/finances/07/05/2018/5af0280d9a7947165a6e8c22)**

Why is this definition so important? Because the most fundamental human right is the right to hold property. To be able to live a life with a respected amount of freedom, one needs to be able to control their property and ensure the security and integrity of such rights. Once the ownership of Bitcoin is seen as property rights, the following bundle of rights that are associated with the property also are applicable to its ownership: There is a standard bundle of rights associated with the property:

*   The right to control the use of the property,
*   The right to receive benefit from the property,
*   The right to assign, transfer, or sell the property,
*   And the right to exclude others from the property.

Bitcoin is the property and not just a mere bearer instrument due to identity being integrated with coins (unlike bearer bonds/instruments). Typically small transactions which are similar to cash can be done without any mandate of the capture of identity but for transactions beyond a certain value (every country has designated value for such, like 50,000 Rs. in India) there will be a mandate to have the transactions coming with full KYC via exchange or other wallet providers.

When now looked at Bitcoin being property and ownership of these coins subject to the same rules as for the property rights, come various other aspects which have not been so clear till now.

# [Uncensorable by governments](#toc.xhtml#s294a)

The popular notion of Bitcoin not possible to freeze is one such idea. We had discussed one such incident in the previous chapter for the case of Ethereum when it had to fork into ETH from ETC to rollback the blockchain and remove the transactions which stole funds. There was a much simpler way to do it. That would be a court order, for a particular UTXO or address being frozen. The order will be issued to miners who process the transactions and once they receive it, they have to just reject any movement of funds from the said frozen UTXOs or addresses. This means that Gold can turn to lead and the thief if gives it back to the owner, it can be made gold again by removal of the freeze. In fact, when the thieves try to spend the proceeds of a crime, on an exchange, their action will identify them due to their KYC done with the exchange and can be used as evidence in a court of law.

Why is the perception that this is not possible to do due to a blockchain being a decentralized system? Therein lies the issue, as not many people (including regulators) yet have reached the point where they have to test these blockchains with court cases but over time these things will start to come into being and implemented by the legal/regulatory bodies of a country.

# [Non-repudiation](#toc.xhtml#s295a)

Non-Repudiation is the process to ensure that the two parties who are doing a transaction cannot deny that a particular transaction has happened. In other words, Repudiation means deniability of ownership.

It means that it is not able to change (ownership, amount, etc.) once committed, typically used in legal settings when the authenticity of a signature is being challenged. The same idea in the Bitcoin world refers to the notion that once you have the private key you do own you're Bitcoin, but that is not true as private keys, they make a good security solution for accessing funds but they do not prove ownership of property rights.

The notion in the current ecosystem is that non-repudiation is possible with Bitcoin due to the nature of its technology but that is not the case when the law comes into being. It is quite similar to losing keys to your home, does not mean you lose ownership of your home, you just need to prove that you are the owner via the registration details and you still retain ownership of your home. So Non-Repudiation is possible but not because of private key ownership, but because you can prove ownership of the purchase of those coins (for ex.) in a court of law. Just like the court's decision on the Cryptopia hack, once the understanding dawns, this view will change as well. Merely protected by code will not be it when it comes to law and if needed a court can even enforce the miners to freeze funds, move funds, etc. as deemed necessary by the court of the land.

# [Fungibility](#toc.xhtml#s296a)

Fungibility in legal terms for money or any other asset is defined as the ability of an asset or a good to be interchanged with another individual's asset or goods of the same type. Basically, a USD 100 bill that Alice has is of the same value and worth as the USD 100 bill that Bob has and if they exchange their notes that will not change their value of money or the accountability of money that they possess. The property of being Fungible for assets is needed to simplify the exchange and trade processes, as fungibility implies equal value between the assets and it is so because the legal system or law makes it such.

The idea of Non-Repudiation and Fungibility is discussed a lot in the Bitcoin ecosystem. When it comes to Bitcoin, they are not fungible through technical measures to create non-repudiation (like private key ownership), they are fungible through law and property ownership procedures.

Fungibility comes when money is exchanged as consideration (and without knowledge of crime, etc.) with another for valid consideration. If a merchant accepts payment in consideration without prior knowledge of the wrongful nature of the coins, the merchant is safe no matter where the *coins* have originated. In other words, valid commerce (without knowledge) creates fungibility.

# [Alert key](#toc.xhtml#s297a)

The original code of Bitcoin back in 2010 had an alert system and this alert system allowed a court to issue a freezing order with minimal interference to the system. It was a mechanism that allowed people to simply report stolen Bitcoin and other proceeds of crime. It was built to ensure that Bitcoin blockchain works within the framework of law and a legal system to protect its users. This was again removed from the codebase in January 2017 by the reason that it added to the centralization of Bitcoin, needless to say, it does not redeem the miners from being liable to the crime-related transactions specifically even if the alert system does not exist. It merely requires now a good amount of extra work and research by individuals to find and trace the tainted Bitcoins increasing the overall cost for tracing. Miners still have the legal requirements like CDD, KYC, and AML (Customer due diligence, know your customer and anti-money laundering) which will apply whether an alert system is present or not.

This alert system is not yet activated even after the genesis upgrade in the Bitcoin blockchain, but it is planned to be activated again by reimplementing the code. This kind of alert system is to protect users on both sides, the ones who might receive the stolen funds and the ones who might unknowingly send funds to addresses that are covered by a freezing order. A primal version of Alert key was present during the initial code release of Bitcoin and it was what the miners could use to inform other miner nodes to for example freeze an address or not accept an invalid block.

# [Decentralization](#toc.xhtml#s298a)

There is a core idea propagated about blockchain which is used for arguing about its uniqueness and the reason behind why the existing laws do not apply: because it is decentralized.

By decentralization, it means that it is not controlled by any single entity, group, person, or government. This gave rise to the idea of issuing a token for every new blockchain project dubbed as ICOs and it was argued for a long period of time that due to blockchain's decentralized nature, it is free from any control. This was also an extension of the concept propagated termed as *code is the law* where since it is written in code, any activity that happens on the blockchain does not libel the developers who have written the code or the nodes that are processing the transaction (whether it is a POW system or a POS system) It's not just the laws, there are many arguments made for the uniqueness of a blockchain type system owing to it being decentralized like:

*   It is acceptable to be anonymous and implementation of technical solutions like Coin Mixers which makes an attempt to obfuscate the ownership and origin of the funds.
*   Create new cryptocurrencies out of thin air where these tokens are created by the implementation of a smart contract (ERC20 tokens) and no accountability or responsibility towards the reason for the underlying value of those tokens (either the project is never completed, or it is speculated in a pump and dump type of system).
*   Forks of a blockchain by changing the protocol or the rules of the chain but not acknowledging the financial responsibility of an Issuer of currency.
*   Creation of payment channels based side chains which do not tie back to the original chain (unlike overpool or local chain) like in the case of lightning network implementations.

The only way a protocol can be completely decentralized is by making it stable and fixed so that no one is able to change it in the future. Currently, most of the blockchain has a centralized developer group who are developing and maintaining the blockchains, which they can in their group quite easily decide to implement new rules and can implement then as well which was seen in the case of Ethereum chain rollback during the DAO hack incident. Most of these blockchains under the current law come under a common-law partnership structure which is a form of association where all members or partners are equally liable for the consequences and actions coming from one or any partner or all of their actions. Corporations provide shareholders and members with limited liability and partnerships can be constructed as LLP or limited liability partnership as well but a common-law partnership imposes equal responsibility to all for the actions of other partners.

# [Privacy and law](#toc.xhtml#s299a)

The laws related to money laundering are specifically made for tracing of large or small amount transactions that are originating from illegal proceeds and it stands as one of the most sought after problems by governments across the world. Banks and other **PSP (payment service providers)** have to spend a huge amount of time and money to create systems that can curb these transactions across the world.

We have already talked about Bitcoin being pseudonymous and the creation and protection of privacy in the Bitcoin network by separating identity from transactions, one of the other aspects when it comes to the law is traceability. Tracing allows for the recovery of assets when stolen or such. In most cases, the tracing law relies on **FIFO (First in first out)**. When a coin is proceeds of crime and a coin mixer is used to obfuscate the source of coins, they can be recovered using the FIFO principle of recovery on the order they were inputted.

The means used in tracing coins comes also from two things, reused addresses can be tied back to identity (could be from exchanges, wallets, or published over the internet) and second not accepting transactions which are from unknown sources. Enabling these features will ensure that only honest money is circulating in the network. We have already discussed a lot about the first but let's have a look at the second aspect.

As per law, if the money is originating from a wrongful source and it is known to the receiver that the source is wrongful, it is considered wrongful credit. To ensure that money is honest, a wallet should be provisioned by a filter/selection process of what coins you expect to receive. If a merchant (user of wallet) received a payment that is rightful without any prior knowledge of the wrongful source of the funds, the merchant is safe as the money is fungible. A good safety measure will be that a merchant quarantine the coins received for a set period to pass where no claim is made of the wrongful source of funds and if not then the money can be considered honest. In case there is a claim made, merchants can return the funds (minus miner fees). These features will need to be built by wallet providers that merchants will use.

**PII (personally identifiable information)** is needed to be built appropriately, one side of doing a proper needed KYC, and on the other side not exposing PII to stop unauthorized applications of it by malicious entities. There currently are security services which for a small fee provide credit monitoring as a service for anyone to ensure that their PII is not used for stealing funds for example but it requires an action on the behalf of the user to stop the unauthorized application/usage of PII after then event (by raising a dispute once credit monitoring service informs of an unauthorized transaction). This is because currently, it is very easy for anyone to get hold of PII, which should be protected when identities are separated from transactions as it is done in the Bitcoin protocol.

# [Permissionless](#toc.xhtml#s300a)

The biggest issue Bitcoin faced was that its early adopters were a myth that the Bitcoin blockchain is permissionless. This whole idea originated from the initial times of the Bitcoin blockchain network where the volume, users, and the value of coins all were quite low and the Bitcoin block size was artificially restricted to 1 MB. Those times, it was enough to use CPU or graphic cards in the home computer to do mining. What happened next was a huge amount of resistance overall from the Bitcoin Core developer groups and community to change anything from that inception model of Bitcoin blockchain, and users were convinced that even if their nodes are not mining on the chain, they are able to perform something that is impossible to in the current financial industry, the ability to verify your transaction by running Bitcoin node software.

This for some reason became a thing which gave a mirage of being in control to normal users who are not mining but still running a node to feel that they are part of a system of transaction verification but in factual terms, their verification does not do anything more than what a checksum does. The nodes that are using their hash power to generate new blocks and the competitors who are participating in this process are the ones who at the end will include or exclude any transaction in the candidate block. This is becoming clearer now that the blockchain size is grown to 100s of GB and still growing, that these non-mining nodes really are not adding any value and will slowly die off after the initial euphoria ends and understanding dawns. This same idea also was at the root of the notion of decentralization and both permissionless and decentralization were projected as the hallmark of blockchain technology and it being non-censorable, impossible to control by governments, and much more.

The fact of the matter is that users who are running nodes to validate transactions, do not have to do that, that is the beauty of the Bitcoin blockchain, it is a competitive system and miners are the nodes that are competing with each other (and in turn keeping things honest) and they are the ones who also need to make sure that the Bitcoin protocol once restored to the original version stays locked and stable which is mandatory to remove any permission or control to be added on later by any entity.

This is also quite clearly explained by none other than the monikar, Satoshi Nakamoto, in one of the early discussions where he explains that the then-current system where every user is a network node is not the intended configuration for large scale. The original thread is present at the below-mentioned link:

Original post: **[https://Bitcointalk.org/index.php?topic=532.msg6306#msg6306](https://Bitcointalk.org/index.php?topic=532.msg6306#msg6306)**

We have been looking at the myths that have been used to keep law and regulators at bay when it came to a public blockchain like Bitcoin. Let us look at a few other things, again from the lens of the regulator on how the public ledger of Bitcoin blockchain measures up.

# [Bitcoin Blockchain Ledger](#toc.xhtml#s301a)

Let us now look at some terms which are commonly used and what they mean when the test of regulation and law is applied to them.

# [Public commodity](#toc.xhtml#s302a)

The ledger space that Bitcoin blockchain provides and when it is open to all, becomes a commodity. Why? Because it becomes a resource pool which has its attributes (immutable public record, mode of exchange of money, and a whole other use cases that we have seen) which is available to use for anyone who is able to buy that leager space using a transaction which pays miner groups using a unit of account for the ledger called a satoshi. As long as a user is able to make an offer to miners that involve the required satoshis, it is possible for anyone and everyone to create an arrangement or a contract by making an offer with the transaction fees to miners. Miners can make a choice to enter into this Agreement by accepting the transaction into a block. And in exchange for writing an entry into the Bitcoin ledger miners receive payment in form of a mining reward that is formed using an integer value of the underlying token (satoshi).

# [Miners as Transaction Processors](#toc.xhtml#s303a)

As we have discussed in [chapter 6](#c06.xhtml) about miners as entities need to become professional businesses and act as transaction processors, there is work ongoing right now to reinvent this entity into a professional enterprise that is run complying with legal and regulatory requirements of the land. As that entity, miners will reinvent to become transaction processors who will open up to new business models of bulk transaction processing functions, dynamic rates (fees for transactions), and client tiring (with things like mutual contracts on bulk transaction processing). They will also be the ones who can emerge as the providers of blockchain cloud services, providing IoT agents and other blockchain-based software services. Two important updates to start doing such were done under the miner ID and merchant API projects released recently by a mining group (*Taal Distributed information technologies Inc.).*

While the miner ID will allow miners to take ownership of their identity and reputation (by identifying themselves) and owning the proof of work that they do to business in a traditional regulatory manner. This will be the first step towards removing the casualness associated with the mining industry and moving to a more professional system by creating a brand that can be trusted with the identity. One such usage will be providing a stream of high-quality random numbers generated during the mining process as a service that could be used in multiple things that needs pure unimpacted by environment random numbers including in advanced computational applications like AI modeling, medical tracking, financial simulations, etc. Taal blockchain has filed a patent on this:

**[https://webfiles.thecse.com/sedar\_filings/00036887/2004021816432817.pdf](https://webfiles.thecse.com/sedar_filings/00036887/2004021816432817.pdf)**

MinerID and MerchantAPI specifications:

**[https://Bitcoinsv.io/2020/04/03/miner-id-and-merchant-api-beta-release/](https://Bitcoinsv.io/2020/04/03/miner-id-and-merchant-api-beta-release/)**

One such example is a contract deal between a mining group known as Mempool and an application called weathersv which stores weather data on the blockchain. Mempool entered into a contract with weathersv to process its transactions at a reduced fee of 0.2 satoshis per byte (right now standard fee is 0.5 satoshi per byte) starting a new age of competitive pricing in the mining world. The obvious question arises here is why would other miners process these transactions for such a low fee, won't they be stranded in the mempool? Yes that is a possibility, that is why the contracts on fee will depend on the type and usage of the data and in this case, whether SV will not have a problem if they have to wait till the time Mempool wins the next block and certainly, other miners may not include these transactions in their blocks, but suppose if there are other miners offering similar rates to their exclusive clients and then they come to an agreement with Mempool that they will process each other's low fee transactions as well. There are many possibilities like this but all that involves the miners taking a more central position in the Bitcoin network.

# [Notary and Bitcoin](#toc.xhtml#s304a)

A notary provides typically an authentication service helping to secure a record. Using a blockchain can help in some of it but not with everything. Below is a summary of typically what a notary does from the UK notaries' society (**[https://www.thenotariessociety.org.uk/pages/what-a-notary-does](https://www.thenotariessociety.org.uk/pages/what-a-notary-does))**

Many notaries provide a service for commercial firms engaged in international trade, and for private individuals. The most common tasks include:

*   Preparing and authenticating powers of attorney for use overseas
*   Dealing with purchase or sale of land and property abroad
*   Authenticating foreign wills and providing documents to deal with the administration of the estates of people who are abroad, or owning property abroad
*   Authenticating personal documents and information for immigration or emigration purposes, or to apply to marry or to work abroad, such as education or professional qualifications or declarations of freedom to marry
*   Authenticating company and business documents and transactions or providing certificates as to the status of a company or the identity of its directors

As you can see from the above use cases, a blockchain can be used for some of them but not all. Just loading the hash for example of a document on the blockchain will just legally provide the evidence of the existence of the said document, authentication of the documents still will need to be done which only a notary could do. They will still have to validate the document, validate the hash that is created, validate the keys associated with the individuals or companies who seek to notarize the document and witness the process of signing and broadcasting of the transaction to the blockchain containing the hash. There is also the fact that keys are not identities, the obvious example being that you can be working for a company which holds keys of their clients and act on their behalf. That is why the identities associated with the keys also need to be authenticated and certified by the notary. Bitcoin or any other blockchain for that matter can be a tool for notary but can never be a notary by itself.

# [Immutability](#toc.xhtml#s305a)

Bitcoin is a public ledger which is immutable which has been quite established I would say, and that is overall the property of all blockchain, but the way it works is it is a WORM storage media, so it is written once, read many (WORM) which do not mean that it is never possible to update the record. The way it is done is, when you have to update the record, you create a new entry on the ledger, which replaces the older entry and this operation leaves an audit trail for this operation which makes it possible to update, but also immutable as an overall attribute of the ledger.

# [Taxation and Bitcoin](#toc.xhtml#s306a)

One of the initial usage that Bitcoin or any other cryptocurrency acquired was due to the notion that many thought they did not have to pay taxes on earnings. This is long refuted by many countries where it's already regulated and people have been mandated to pay taxes on it but that is not the purpose of this topic here. The fact of the matter is that Bitcoin blockchain provides a means to do fair taxation. It is possible to integrate the required tax for a transaction directly in a transaction which is not possible in today's system. Using the script and multiple outputs, you can create a transaction that automatically pays the VAT instantly on the sale of goods and services.

How does this works with Bitcoin, let us understand this by taking an example? First the main principle is that you need to be able to provide the evidence of where did you purchase the Bitcoin you have and at what price. If not then you can be held to have purchased it at zero making complete value taxable. It is also to note that you need to register your addresses where you have the Bitcoins, else proof of ownership (so that addresses that you are not liable for do not own or any alteration of records). With that, in the example, we have Alice, a customer, Bob is a merchant, Charlie is an employee working for Bob and is paid in Bitcoin and Mike is a miner.

Let us see how taxation will impact each of the four different people. Mike creates a new block with a transaction Tx(M0) that has a block reward and transaction fees totaling to 10 BSV. Suppose that the cost of mining to mike for a block comes to 5,000 USD and the block is valued at a market rate of 10,000 USD. The net profit for Mike for a block comes to 5,000 USD for which he has to pay taxes.

Now Alice wants to buy some Bitcoins and she decides to buy it from Mike. She also sees this as an investment hoping that the price will go up and she will profit from this investment. Alice buys 5 BSV from Mike at the price of 1000 USD per BSV with a total coming to 5000 USD. This is conducted with a transfer through Alice's Bank account to Mike's bank account of the mentioned funds.

However, both Alice and Mike care about privacy and want to keep the transaction private. What Mike will do is once he has the coins in Pub(M0) he splits the coins to multiple denominations:

*Pub(M0) -> Pub (M1) 3.0 BSV, Pub (M2) 3.0 BSV, Pub (M3) 3.0 BSV, Pub (M4) 1.0 BSV.*

Since Mike is a miner, he does not need to pay any fees. When he makes the transfer to Alice, he will also not send one but split the intended transactions into let's say, three when he sends coins to Alice. Doing so will ensure they both maintain maximum privacy.

The transfer uses set templates which could be provided by their wallets and one way to do these transactions is shown in *[Figure 15.1](#c15.xhtml#fig15_1):*

![](images/Figure-15.1.jpg)

**Figure 15.1:** A private method of transfer of coins from Mike to Alice

Mike will hold a total of 5 BSV at the end of the year (assuming he does not sell further on after Alice).

Mike ends up losing about 1,500 USD in the potential revenue when he is not keeping records of who he has sold coins to. Please note here that fees are still a thousandth of a cent which makes it quite simple and easy to decide that splitting of transactions can be done so that privacy is maintained for both transacting parties. This would become uneconomical if fees were many cents to a dollar. This is why the low fees supported by Bitcoin are one of the key elements in enabling microtransactions and a huge volume of private transactions. *[Figure 15.2](#c15.xhtml#fig15_2)* shows how his tax accounting will look like:

![](images/Figure-15.2.jpg)

**Figure 15.2:** Tax calculations for Mike in case he keeps a record and when he does not keeps the record in case of an audit

This is the reason why it is so important to keep records, especially for someone who is running a business. This does not end here if Alice sells her coins the next year, or any future years, Mike will be liable for taxes for all the increased price value of Bitcoin year on year for coins he doesn't have, so certainly it is in Mike's interest quite critically to make sure he keeps honest record keeping and ensure that he doesn't lose any records which incidentally will be great to store on blockchain as well by using invoices issued on-chain.

On the same lines let's take the case of Alice. Suppose Alice, using her coins, makes two purchases from Bob who is a merchant selling electronic goods. She buys a Television for 1000 USD when the Bitcoin price is 1,500 USD and then buys a speaker system for 400 USD when the Bitcoin price is 1750 USD. Like Mike, she and Bob both are incentivized to keep these records. Alice also cares about privacy so her transactions to Bob will be such that ensure it by splitting coins and sending to multiple addresses for the same purchase transaction of television and speaker system. Alice and Bobs transactions are shown in *[Figure 15.3](#c15.xhtml#fig15_3):*

![](images/Figure-15.3.jpg)

**Figure 15.3:** Alice making multiple purchases with Bob who owns an electronics store

Now suppose Alice also wants to make some profits from her investments in BSV and decides to sell the partial holding (2.5 BSV) she has after the shopping she has done. She sells the coins on a compliant and regulated exchange at a market price of 2,500 USD per BSV earning 6250 USD. The tax reporting for Alice is shown in *[Figure 15.4](#c15.xhtml#fig15_4)* below:

![](images/Figure-15.4.jpg)

**Figure 15.4:** Alice's accounting of funds and tax liabilities for her

As you can see from the above table, Alice ends up with a portfolio of new equipment, Cash in Bank, and remaining coins as per the calculations shown in *[Figure 15.4](#c15.xhtml#fig15_4).* She ensures to be tax compliant as she knows that in case either Mike or Bob are audited, they will be giving out her details to the tax office for validation and if she does not report correct taxes she is prone to be penalized by the tax department.

Continuing with our example, now Charlie is an employee of Bob and Bob wants to make sure that he is keeping records as Alice will report the transfer of coins to Bob and as shown in Mike's case, where unaccounted coins can be a taxation burden not just in the current year but every next year. So when Bob pays Charlie his salary in Bitcoin, he would be declaring it in this tax accounting and that will also make Charlie report correct accounting of coins in his tax accounts.

In the future, the wallets used by each of the entities can provide support towards tax reporting as well as making the complete process quite automated. In fact, if we see in the above figures where we have shown the transaction inputs and outputs, each output can have one more output which will be the VAT or applicable tax and can be paid instantly. This will reduce fraud immensely and also will reduce the current processes the government has to use for tax audits by being able to auto reconcile.

Tax Liability with Forks is one aspect which has been also ignored by most of the early adopters and finally now we have clarity from IRS regarding the same, and I quote:

*Q21. One of my cryptocurrencies went through a hard fork but I did not receive any new cryptocurrency. Do I have an income?*

*A21. A hard fork occurs when a cryptocurrency undergoes a protocol change resulting in a permanent diversion from the legacy distributed ledger. This may result in the creation of a new cryptocurrency on a new distributed ledger in addition to the legacy cryptocurrency on the legacy distributed ledger. If your cryptocurrency went through a hard fork, but you did not receive any new cryptocurrency, whether through an airdrop (a distribution of cryptocurrency to multiple taxpayers' distributed ledger addresses) or some other kind of transfer, you don't have taxable income.*

Read more at

**[https://www.irs.gov/individuals/international-taxpayers/frequently-asked-questions-on-virtual-currency-transactions#collapseCollapsible1570643294078](https://www.irs.gov/individuals/international-taxpayers/frequently-asked-questions-on-virtual-currency-transactions#collapseCollapsible1570643294078)**

To conclude, Bitcoin does not remove the liabilities of tax, it helps make taxation easier and automated so that a GST like system that is built on Bitcoin blockchain, could in theory remove the complete need of year-end reporting and reconciliation if done and adopted correctly.

Think of that system, it will not just reduce the huge amount of work burden for the tax department, but also for governments by enabling instant tax income, huge court case reduction due to tax disputes and much more in terms of benefit for the common man.

# [Permissioned Blockchains](#toc.xhtml#s307a)

Since the inception of the Bitcoin network, various enterprises that are valuing the potential of the distributed permanent ledgers are quite keen on finding out Use Cases that could benefit their current business/products or industry as a whole. There is an overwhelming view that a permanent record of the history of transactions is really valuable and emerging ideas like smart contracts implemented on distributed ledger offer immense potential for existing industries like payment settlement, trade and supply chain finance but not just limited to this, a lot is yet to be discovered. All in all, every leading business organization/enterprise who is seeing the potential of being disrupted by public blockchains is and justifiably so, exploring blockchain use cases in one form or another.

The elephant in the room when these organizations started exploring this new technology was, how can we develop and test these things in a public forum, being a responsible organization from a regulatory point of view or towards ethical and moral responsibility towards customers who trust these organizations with their data and its security, they had a bigger responsibility when compared to open source development communities that are mainly developing and governing the public blockchains.

This led them to come about a new concept called permission blockchain which sometimes is also referred to as DLT, distributed ledger technology. They are nothing but distributed systems who are available to only the trusted participating entities, so more like a security layer added to the blockchain to ensure only trusted and non-malicious participants have access to the data that could potentially be quite sensitive and the operations are properly governed under the approved regulatory framework that exists at this time. Hyperledger ecosystem projects like Fabric, Sawtooth, Iroha, and R3 lead EEA, Corda are some of the initiatives which are exploring the use cases. There are some properties which are common across these private blockchains which I will try and capture below:

*   Censorship resistance and Trust-less network as property are quite limited due to the extra layer of security that these enterprises most certainly need. But once these entities are approved they can participate freely in storing and manipulating the blockchain as per their business functions needs. They usually will also be using similar cryptographic tools and transaction signing capabilities which are still valuable in terms of ensuring the transaction ownership. However this means that all of the private blockchain now are governed under a trusted committee of corporations now in place of the existing system of multiple trusted 3rd parties. Again the checkpoints will be prone to vulnerabilities same as that are there right now for centralized certification systems those that exist for TLS/SSL server certificates.
*   Auditability is something that these blockchains retain and utilize in its entirety as they still are using most of the cryptographic tools (UTXO in Hyperledger for ex.) and cryptographically signed transaction to change the ledger and easy audibility of the whole history to find out how and who made the changes in the ledger. This is quite a huge use case for enterprises that are now facing the exponentially increasing size and volume of data that they need to store and the tools needed to be able to make the data and processing auditable. All this is provided in a blockchain as out of the box feature as compared to traditional systems. But again, just from this perspective, the auditability is still hidden in the same way currently the financial data resides in an organization's restricted by access database, and for getting access to audit, the same procedures need to be followed which defeats the purpose of using a blockchain.
*   Shared IT application as the scope and data needed for an enterprise is growing exponentially every next year. This combined with the cost of maintaining, developing and complying the systems with constantly changing business processes, regulations, environment, one of the trends that have emerged is many competing enterprises agree to build a common IT system/application which does the core processing and they focus and build on the user experience and customer services aspect. This is a huge cost saver and again a perfect use case for Blockchain implementation, and this might be the only valid case for all of these organizations forming a private permissioned blockchain. One of the issues that come in this setup is that the organizations that contribute most towards the development IP tend to become a central entity leading and can charge fees for the usage to other members. R3 and JP Morgan's Corda blockchain was one such case which saw later on the exodus of many of the initial members.

The above-mentioned limitations of the implementation of limited versions of what Bitcoin protocol was created are the main reasons that we see so much buzz about blockchain being a revolutionizing technology but till today we have not seen even a single large scale blockchain that has become mainstream in adoption for non-technical users.

There are few distinguished capabilities which can only be achieved with a protocol like Bitcoin making it only possible with that system to be able to achieve the famed revolutionary aspect of this technology as mentioned below:

*   Transaction validation using a Proof of work system.
*   Public recording of transactions making it an immutable system of record.
*   Security as property due to data being public and possible to verify when needed by any entity.
*   Scalability which is right now standing at the possibility of millions of transactions per second with the genesis upgrade of unlimited sized blocks. Teranode is an ongoing project which is re-architecting the application to support parallelization and take capacity to billions of transactions per second.
*   Availability and reliability due to the distributed node structure.

In short, the one main difference and probably the clinching point is that the entire security model for blockchain is based on publishing a hash, which contains a digital signature from the transacting entities, publicly. This means it locks down as a public immutable record for a particular entry. For example, an entry could be a document which was used to agree on a business contract, hashed and the hash uploaded in a transaction and that got recorded in the Bitcoin blockchain. In permission blockchain, this is not the case as the blockchain is private and not available for audit/accounting purposes any differently than what the databases currently are in an oracle or IBM RDBMS databases.

# [CBDC](#toc.xhtml#s308a)

Along with Permissioned blockchains, there is a considerable amount of interest on the idea of stable coins in terms of private or public blockchains issuing those, but also the overall culmination of this idea coming from central banks across the globe to issue digital money that is now being called, Central Bank Digital Currency. What are these, and how do they relate to Bitcoin blockchain or not, let us find out.

Stable coins are these digital assets issued as a token and priced fixed at the value of a legal tender. There have been many stable coin launches since the last many years including the infamous USDT (Tether) which was probably one of the first stablecoin and was the primary reason for the famous bull run of cryptocurrency markets in Nov-Dec 2017. Stable coins are meant to be backed by real currency on a 1:1 basis, but as per the admission of their own, USDT is only 76% backed and even less if you believe the various lawsuits that are ongoing with it.

But since then, there have been many attempts to create legitimate and honest stable coins like USDC, USDK, Paxos standard, TrueUSD, etc. (all backed 1:1 by USD and have few versions backing other currencies like Euro as well). These are however some which are not fully backed 100% by USD as will like USDT (which has a volume of about 8 Billion at the time of writing and is mainly the reason for most of the cryptocurrency prices and pump and dump cycles). A lot of usage of stablecoins was based on the incorrect understanding that if you do not convert your coins to fiat and keep it in stablecoins, that would not be taxable or not create a tax event as it is still in the digital currency form and this loophole was used by many (mostly leverage traders but many other early adopters) to play the market and use the stable price property of stablecoins when needed in place of government currency. Nonetheless, that is an incorrect conclusion, and hope is that when the regulations are put in place, these mistakes will be corrected and retrospective tax events will require these early adopters to tax liability.

When central banks started looking at blockchain, they were looking at creating the digital version of their currency. This is also expedited lately by many private companies like Facebook trying to launch private stablecoins which still has not happened as yet, but generates a sense of urgency for these central banks to act on creation of their version of Digital currency. This digital currency could also be thought as stablecoin but since it will be issued by central bank/governments it will be as legal and taxable as fiat is, just that the overall currency-issuing and management can be done on a blockchain-based ledger and government can also gain few benefits like few mentioned below but not limited to that:

*   The cost to print and distribute currency could go down significantly with digital currencies.
*   The cost of tracing and overall currency management can go down significantly.
*   It could also speed up central bank transactions with other banks, in a way if these are used for wholesale usage (restricted usage with specific agencies or interbank payments).

![](images/Figure-15.5.jpg)

**Figure 15.5:** Motivations of issuing wholesale CBDC from a research paper by BIS (Bank of international settlements), Source link: **[https://www.bis.org/publ/bppdf/bispap101.pdf](https://www.bis.org/publ/bppdf/bispap101.pdf)**

Most central banks are researching CBDC and many are progressing from conceptual work into experimentation and proofs-of-concept, including in cooperation with other central banks. At this stage, most central banks appear to have clarified the challenges of launching a CBDC but they are not yet convinced that the benefits will outweigh the costs.

However recent changes have seen China central bank, and an alliance made out of Chinese banks, government groups, and technology companies are set to launch a Blockchain-based Service network, or BSN, in April 2020. This platform will be maintained by China's government and will be a closed system for participation, more in line with a permissioned blockchain. France and England's central banks have issued a request for proposals to experiment with CBDCs and similar news is coming out of many other central banks of countries. Digital Euro is also being considered to be launched and in short every large economy’s central bank is either working on or exploring for creating the digital currency of their own.

How is this related to the Bitcoin blockchain? Actually not so much but CBDCs are a very valid use case for implementing a currency token. In fact, the tokenized protocol we looked at in [chapter 13](#c13.xhtml) has already some of the features available out of the box to implement a legal, traceable, and controllable version of CBDC. We will have to wait and watch over this space on what happens next.

# [Patents](#toc.xhtml#s309a)

One last subject which will complete this chapter is the current state of blockchain-related patents and Bitcoin. There is the start, where the Bitcoin whitepaper and the codebase were released with MIT license (open source). The main reason for that was that you cannot release something with a pseudonymous identity (Satoshi Nakamoto) and patent it. But since then that is not the case. Most of the technology and patents we have discussed in this book fall under an Open BSV license:

**[https://Bitcoinassociation.net/open-bsv-license/](https://Bitcoinassociation.net/open-bsv-license/)**

In short, this is very similar to Open or free for usage under the condition that it is used in Bitcoin (BSV) blockchain.

When it comes to patents of various technologies discussed in this book like threshold signatures, secure multiparty communication, etc. most of these patents are available for free to use if the usage is for BSV blockchain. nChain, the primary owner of most of these patents have as of October 2019 about 826 patents currently filed, 1450 in the pipeline, and approximately 200 granted or about to be. What this means is that most of the blockchain-based solutions and technology are now patented and available only for usage on the original Bitcoin, the BSV blockchain.

# [Conclusion](#toc.xhtml#s310a)

In this chapter, we have tried to cover the Bitcoin blockchain from the legal lens and covered various terms and topics that are relevant for any organization, developer or any individual who is looking to get involved in using Bitcoin blockchain for their application development, investment or for that matter, medium of exchange, and earnings. We have looked at why not just Bitcoin but any cryptocurrency is in legal/regulatory terms property and all the laws that apply to property apply the same for digital assets.

We hope to see the regulatory and legal system across the globe continue to evolve and make the use of a public blockchain like Bitcoin more and more regulated in terms of any trade that happens on it. This will usher an era of the true free market globally for the first time in the history of trade. Bitcoin will also at some point become a unit of value for data due to its storage capabilities. The fact that it can curb fake data by making people accountable and the currently exponentially increasing fake news and censorship across the globe do need a neutral and accountable platform where facts can be not just immutably stored, but traced to their owners for making them accountable and responsible. With this hope, we end the chapter, section, and the book.

# [Questions](#toc.xhtml#s311a)

1.  What is Bitcoin? A currency, money, or property?
2.  What is non-repudiation and why is it not possible to do on Bitcoin blockchain?
3.  What is the difference between a Permissionless and non-trusted permissioned system?
4.  Can Bitcoin act as a notary for international trade?
5.  What is the difference between permissioned and public blockchain and why is a permissioned blockchain not as secure as a public blockchain?

# [References and Links](#toc.xhtml#bm)

# *for further reading*

1.  Dr Craig Wright’s blog : **[https://craigwright.net](https://craigwright.net)**
2.  A lot of video presentations and also presentations from Coingeek conferences from various participants : **[https://www.youtube.com/channel/UC95\_Nqes9m5arhoT1lt1SFg](https://www.youtube.com/channel/UC95_Nqes9m5arhoT1lt1SFg)**
3.  Bitcoin Association links :  
    1.  **[https://bitcoinassociation.net/videos/welcome-to-bitcoin-association/](https://bitcoinassociation.net/videos/welcome-to-bitcoin-association/)**
    2.  **[https://www.youtube.com/channel/UCp6db-jgWGe5Ws35bRbI6Ig](https://www.youtube.com/channel/UCp6db-jgWGe5Ws35bRbI6Ig)**
4.  Bitcoin SV wiki : **[https://wiki.bitcoinsv.io/index.php/Main\_Page](https://wiki.bitcoinsv.io/index.php/Main_Page)**
5.  Bitcoin SV node software : **[https://bitcoinsv.io](https://bitcoinsv.io)**
6.  nChain : **[https://nchain.com](https://nchain.com)**
7.  Medium Blogs  
    1.  Unwriter : **[https://medium.com/@\_unwriter](https://medium.com/@_unwriter)**
    2.  Jack Davis : **[https://medium.com/@jack.d](https://medium.com/@jack.d)**
    3.  Sean Pollock : **[https://medium.com/@\_seanavery](https://medium.com/@_seanavery)**
    4.  Jerry Davis : **[https://medium.com/@digitsu](https://medium.com/@digitsu)**
    5.  Mr Scatman : **[https://medium.com/@bsmith12251960](https://medium.com/@bsmith12251960)**
    6.  Lorien Gamaroff : **[https://medium.com/@gamaroff](https://medium.com/@gamaroff)**
    7.  Roman Quesada : **[https://medium.com/@ramonquesada](https://medium.com/@ramonquesada)**
    8.  Ryan Charles : **[https://medium.com/@ryanxcharles](https://medium.com/@ryanxcharles)**
8.  Joshua Henslee blog and youtube channel  
    1.  **[https://www.yours.org/@joshuahenslee](https://www.yours.org/@joshuahenslee)**
    2.  **[https://www.youtube.com/user/jhenslee11](https://www.youtube.com/user/jhenslee11)**
9.  Coingeek : Bitcoin for beginners : [https://coingeek.com/bitcoin101/](https://coingeek.com/bitcoin101/)
10.  Bitcoin projects : **[https://www.bsvdevs.com](https://www.bsvdevs.com)**
11.  Bitcoin SV Education webinars : **[https://bitcoinassociation.net/bsv-academy/](https://bitcoinassociation.net/bsv-academy/)**
12.  Steve Shadders at yours.org : **[https://www.yours.org/@shadders](https://www.yours.org/@shadders)**
13.  Bitcoin Script engineering : **[https://medium.com/@Stas33496115](https://medium.com/@Stas33496115)**
14.  Xhliu’s blog : **[https://medium.com/@xiaohuiliu](https://medium.com/@xiaohuiliu)**
15.  Corner Murrey’s blog and youtube channel:  
     1.  **[https://medium.com/@Bitcoin\_Beyond](https://medium.com/@Bitcoin_Beyond)**
     2.  **[https://www.youtube.com/channel/UCYDriPidzNrbX9K58PsTVVw](https://www.youtube.com/channel/UCYDriPidzNrbX9K58PsTVVw)**
16.  Blog of ElectrumSV developer, focused a lot of wallet development : **[https://medium.com/@roger.taylor](https://medium.com/@roger.taylor)**
17.  Dr Craig S Wright explaining the theories behind bitcoin (youtube channel): **[https://www.youtube.com/channel/UC2qsCjXNXfiQfKYox339lZg](https://www.youtube.com/channel/UC2qsCjXNXfiQfKYox339lZg)**