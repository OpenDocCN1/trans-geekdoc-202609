
In case there’s an update to the code, it will be updated on the existing GitHub repository.

# Errata

We take immense pride in our work at **Orange Education Pvt Ltd** and follow best practices to ensure the accuracy of our content to provide an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at:

**[errata@orangeava.com](mailto:errata@orangeava.com)**

Your support, suggestions, and feedback are highly appreciated.

# Did You Know

Did you know that Orange Education Pvt Ltd offers eBook versions of every book published, with PDF and ePub files available? You can upgrade to the eBook version at **[www.orangeava.com](http://www.orangeava.com)** and as a print book customer, you are entitled to a discount on the eBook copy. Get in touch with us at: **[info@orangeava.com](mailto:info@orangeava.com)** for more details.

At **[www.orangeava.com](http://www.orangeava.com)**, you can also read a collection of free technical articles, sign up for a range of free newsletters, and receive exclusive discounts and offers on AVA™ Books and eBooks.

# Piracy

If you come across any illegal copies of our works in any form on the internet, we would be grateful if you would provide us with the location address or website name. Please contact us at **[info@orangeava.com](mailto:info@orangeava.com)** with a link to the material.

# Are You Interested in Authoring with Us?

If there is a topic that you have expertise in, and you are interested in either writing or contributing to a book, please write to us at **[business@orangeava.com](mailto:business@orangeava.com)**. We are on a journey to help developers and tech professionals to gain insights on the present technological advancements and innovations happening across the globe and build a community that believes Knowledge is best acquired by sharing and learning with others. Please reach out to us to learn what our audience demands and how you can be part of this educational reform. We also welcome ideas from tech experts and help them build learning and development content for their domains.

# Reviews

Please leave a review. Once you have read and used this book, why not leave a review on the site that you purchased it from? Potential readers can then see and use your unbiased opinion to make purchase decisions. We at Orange Education would love to know what you think about our products, and our authors can learn from your feedback. Thank you!

For more information about Orange Education, please visit **[www.orangeava.com](http://www.orangeava.com)**.

# Chapter 1: Blockchain Evolution

## Introduction

This chapter will introduce blockchain and distributed ledger technology, focusing on prior implementations and challenges to overcome. We will look at the landmark Bitcoin whitepaper and how it ushered in a new era of digital currencies. Next, we will introduce the Ethereum whitepaper, how the concept of smart contracts was born, and the problems that Ethereum was addressing. This chapter will also review the key takeaways from the famous Charles whiteboard video that led many to dig deeper into the Cardano ecosystem. We will then explore the classic Blockchain Trilemma of decentralization, security, and scalability. There will also be a review of tokenomics and Cardano’s native currency, Ada. Finally, we will finish the chapter discussing the Cardano roadmap and blockchain use cases.

## Structure

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

## Distributed Ledger Technology

The concept of using a ledger to record credit and debit transactions has existed for thousands of years.[¹](#c01.xhtml#ftn1) With the advent of distributed computing, the concept of the ledger was extended, where multiple parties can see and update a ledger using computers connected to a network. The difference between a centralized and a decentralized distributed ledger, as shown in *[Figure 1.1](#c01.xhtml#fig1_1)*, is that you no longer have a single central authority. The issue, however, is that you still need a way to ensure the correct ordering of immutable transactions. In 1991, **Stuart Haber** and **W. Scott Stornetta** wrote “*How to Time-Stamp a Digital Document,*” which described an approach using timestamps and cryptographic hashes to prove when a digital document had been created or if it had been modified.[²](#c01.xhtml#ftn2) This approach was used to check for immutability.

![](images/Figure-1.1.jpg)

**Figure 1.1:** Types of Ledgers

## Byzantine Generals Problem

Another core aspect of distributed ledger technology is ensuring the data stored on each node is correct in a network that may include malicious or unavailable nodes. This problem is known as the Byzantine Generals Problem (BGP).[³](#c01.xhtml#ftn3) BGP describes a scenario where generals surround a castle for an attack and must communicate and coordinate with each other via messengers. The attack will only succeed if all generals attack simultaneously, using the messengers to signal the attack. The risk, however, is that the attack signal may or may not be received correctly by all generals because the messengers may have been killed or bribed. A network resistant to these types of failures is called Crash Fault-Tolerant (CFT) and Byzantine Fault-Tolerant (BFT), respectively.

The paper “*Building Secure File Systems Out of Byzantine Storage*” by **Mazières** and **Shasha** introduces a Byzantine fault-tolerant (**BFT**) algorithm that allows a distributed network to reach a consensus on the state of data in an untrusted network.[⁴](#c01.xhtml#ftn4) The authors created a consistency protocol called **SUNDR** (Secure Untrusted Data Repository) by leveraging redundancy to handle Byzantine failures and using digital signatures. If a discrepancy is discovered, the protocol will detect malicious behavior and partition file system data blocks into forks.

## Network Consensus

For a network to agree on a common state, it needs to use a consensus algorithm that has two key properties:

*   **Liveness**: Must continue to make progress in deciding the network state.
*   **Safety**: Once honest nodes have confirmed the network state, they must remain committed to this decision.

When dealing with decentralized ledger networks, it is vital for the network’s security that the majority of nodes participating in the consensus algorithm are honest. If not, then this is known as a 51% attack, where a single entity controls the majority of nodes. When this happens, the attacker can control the consensus outcome and undo past (or deny future) transactions that may benefit the attacker.
