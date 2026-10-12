
# References

*   [Sharma, T. K.](#ch17.xhtml#r352b) (2019, May 15). Quorum vs Hyperledger: The Ultimate Guide. Blockchain Council, [https://www.blockchain-council.org/hyperledger/quorum-vs-hyperledger-the-ultimate-guide/](https://www.blockchain-council.org/hyperledger/quorum-vs-hyperledger-the-ultimate-guide/).

*   [Shen, M.](#ch17.xhtml#r353b), Lieuhuang, Z., & Ke, X. (2020). Layered Data Sharing Architecture with Blockchain. Springer. [https://link.springer.com/chapter/10.1007/978-981-15-5939-6_3](https://link.springer.com/chapter/10.1007/978-981-15-5939-6_3)

*   [Shepherd, D.](#ch17.xhtml#r354b) (2015). Integrated Development Environment. Science Direct. [https://www.sciencedirect.com/topics/computer-science/integrated-development-environment](https://www.sciencedirect.com)

*   [Takyar, A.](#ch17.xhtml#r355b) (2021). Top Blockchain Platforms of 2021 [https://www.leewayhertz.com/blockchain-platforms-for-top-blockchain-companies/](https://www.leewayhertz.com/blockchain-platforms-for-top-blockchain-companies/)

*   [The Finance Buff](#ch17.xhtml#r356b). (2012, December 5). Transfer Money by ACH Push, Not Pull. [https://thefinancebuff.com/transfer-money-by-ach-push-not-pull.html](https://thefinancebuff.com)

*   [Vera.](#ch17.xhtml#r357b) (2020). Firmware VS Software: What's the Difference Between Them? Mini Tool. [https://www.minitool.com/news/firmware-vs-software.html](https://www.minitool.com)

*   [Walker, A.](#ch17.xhtml#r358b) (2018). What is an IDE (Integrated Development Environment)? Learning Hub. [https://learn.g2.com/ide](https://learn.g2.com)

*   [Wu, X.](#ch17.xhtml#r359b), & Sun, W. (2018). Blockchain Quick Start Guide: A Beginner's Guide to Developing Enterprise-Grade Decentralized Applications. Birmingham: Packt Publishing.

# 10 Testing and Auditing Blockchain Applications

Karen Akshatha Franklin, Philip Samuel Panneer Selvam and Samhitha Keshireddy

DOI: [10.1201/9781003211723-10](http://doi.org/10.1201/9781003211723-10)

## Abstract

This chapter is the last in the design/develop/test blockchain applications trilogy. Assuming adherence to sound blockchain design and development principles, tools and best practices, it is important to adhere to strict and thorough testing procedures during both the application development and the final testing stages. The discussion in this chapter starts with a discussion of over 10 different blockchain application testing procedures. While it will most likely be very time consuming and expensive to employ all of the discussed testing methodologies, information systems auditors and blockchain testing professionals need to employ a number of testing procedures in order to make sure that the blockchain application is fully functional prior to full deployment.

A discussion of the various types of bugs and a four-step strategy for successful bug management is also provided in this chapter. A number of blockchain testing applications and bug analysis tools are recommended, along with their download links. In addition, the foundation of testing management principles and related concepts are also presented and discussed.

The chapter concludes with a comprehensive blockchain application audit checklist, based on a framework developed by KPMG, India. This checklist should be a valuable tool for information system auditors in planning and conducting blockchain specifics audits.

## Why It Is Critical to Test a Blockchain Application

Blockchain applications do not exclusively exist in the digital domain of cryptocurrency. These applications require to be integrated with other software and systems in order to ensure that the blockchain solution provides access to real-world data and events like smart contracts. The immutability and distributed nature of the blockchain ledger, along with the inclusion of smart contracts, provides an attractive solution for enterprises. Considering how relatively recent the technology is, it does come with its own set of current drawbacks and vulnerabilities. Smart contract-based blockchain platforms have a lot to offer, but lack of testing, best practices and standards is what makes its architecture potentially vulnerable and exploitable by hackers. There are security vulnerabilities present in the technologies that are integrated with blockchain systems. Hence, all blockchain projects should be tested and evaluated for quality, compliance, governance and value at risk.

In 2016, the attack on Ethereum was announced by the Decentralized Autonomous Organization related to a vulnerability on the Ethereum platform being exploited by a hacker. The vulnerability was not present in a smart contract which caused a total loss of 150 million dollars. Such attacks on various blockchains prove what consequences could occur if the codes are not extensively tested for every potential threat [[23](#ch18.xhtml#r382)].

To roll out the blockchain solution successfully, it is very important that trust between participating stakeholders in joining the blockchain ecosystem is present. To ensure this trust, the blockchain components are tested to ensure that they work correctly and also determine if any application integrated with the blockchain framework interacts in a trusted fashion.

Therefore, testing of a blockchain application is critical to provide software quality to all the various components of the blockchain; therefore, testers should employ a best practice-based suite of testing approaches [[15](#ch18.xhtml#r374)].

## Popular Testing Tools for Blockchain

Original blockchain developers who have access to the actual system code use a process called `emulation`. Emulation is used to test the overall performance of different private, public and consortium blockchains. There are many emulation tools that are being used to test different platforms. A few are explained below.

*   **`Ethereum Tester`**: An Ethereum-driven open-source library, which helps to evaluate the initial performance for customer-oriented projects. The tool also analyzes the operation of API, web integration, smart contracts and other blockchain components, such as DApps.

*   **`Truffle`**: The first component of the Ethereum-based blockchain tool evaluation known as truffle suite. Deployment of smart contracts is performed along with compilation and testing in the development environment of truffle.

*   **`Corda Testing Tool`**: An open-source environment designed specifically for R3 Corda which provides a wide range of functionality for unit testing and integration testing.

*   **`Exonum Test Kit`**: An open-source framework which uses `Rust` programming language for creating blockchains with emphasis on testing the logic of transactions. The test kit used for testing provides a Java binding tool since it is a part of the software development kit (SDK).

*   **`BitcoinJ`**: An open-source Java-based framework. Designed using Java which implements the Bitcoin protocol (BTC network) to interact with the Bitcoin network and to perform other testing activities. The protocol provides access to maintain a wallet, which allows the user to send/receive the transactions without the need for a local Bitcoin core copy.

*   **`Hyperledger Composer`**: An open-source development toolset and framework provided by the Linux Foundation that supports interactive testing, automated unit testing and system testing. Hyperledger composer uses JavaScript to implement the transactions of blockchain [[21](#ch18.xhtml#r380)].

### Challenges in Testing Blockchain Implementation

Testing as a process is effectively performed in the software development lifecycle, as there are possibilities of bugs passing through the application. To achieve the flow of transaction in a blockchain, all autonomous systems in the distributed network are required to be in collaboration and coordination.
