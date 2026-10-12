
*   Wang, Q., Huang, J., Wang, S., Chen, Y., Zhang, P., & He, L. (2019). A Comparative Study of Blockchain Consensus Algorithms. 2nd International Symposium on Big Data and Applied Statistics, 1437.

*   [Zetzsche, D.](#ch20.xhtml#r446b), Buckley, R., & Arner, D. (2017). The Distributed Liability of Distributed Ledgers: Legal Risks of Blockchain. SSRN Electronic Journal. doi:[10.2139/ssrn.3018214](http://dx.doi.org/10.2139/ssrn.3018214)

# 13 Blockchain User, Network and System-Level Attacks and Mitigation

Nishtha Baria, Dharmil Parmar and Vidhi Panchal

DOI: [10.1201/9781003211723-13](http://doi.org/10.1201/9781003211723-13)

## Abstract

This chapter is the first of two chapters providing a security and assurance technical discussion of currently known blockchain technology attacks. Whereas, in the next chapter, the focus is placed solely on smart contract vulnerabilities and attacks, this chapter covers blockchain vulnerabilities and ensuing attacks at the user, system and network level.

The user-level attacks include stolen private keys and the use of blockchain-specific malware to initiate a security breach at the user-level. Readers are reminded that while all blockchain nodes are users, not all users are nodes. Node-level attacks stem primarily due to vulnerabilities associated with shared vulnerabilities and membership service provider (`MSP`) vulnerabilities.

Furthermore, a total of eight node/network-level attacks and four system-level attacks are also presented and discussed. The chapter also provides readers with some suggested mitigation techniques for the various attacks discussed at each level (user/node/network/system).

The chapter concludes with a discussion of some security best practices for each discussed attack, as well as a quick discussion of Ethereum, Hyperledger and Corda inherent security measures.

## Introduction

Blockchain technology has been expanding and changing since its beginnings, circa 2009. By generating additional value, blockchain has the potential to disrupt sectors and reshape business structures in the same way that the Internet did in the 1990s. The positive result of blockchain is due to a large extent to its distributed and decentralized ledger feature; however, every coin has two sides, and that is also the case with blockchain technology as well. Attackers have used various means to conduct a variety of assaults due to the decentralized nature of blockchain's operating environment. As blockchain technology is evolving so are the attacks related to this technology. In short, the growing popularity of blockchain raises new security and privacy concerns.

Blockchain attacks are divided into four levels. User-level attacks include attacks initiated by or due to users' mistakes. Network-level attacks are attacks that are due to errors in the network's properties or improper controls over the network. Node-level attacks are attacks that are caused due to corrupt tasks on nodes. Finally, system-level attacks are the result of common system coding errors. Attacks and mitigation go hand in hand and so, the necessary mitigation techniques are also discussed in this chapter.

## Blockchain User, Network and System-Level Attacks and Mitigation

### User-Level Attacks

User-level attacks are attacks that are caused due to interactions between users. Often, these user-level attacks occur due to the carelessness of the users, hence resulting in compromise of the private key. User-level attacks may also be a result of the presence of malware. In addition, user-oriented attacks may occur when software is not regularly updated, resulting in unwanted bugs. Placing adequate focus on user-level security may help prevent some of these user-level attacks [[16](#ch21.xhtml#r462)].

### Stolen Private Key

As discussed in [Chapter 2](#ch10.xhtml#c2), two keys are needed to encrypt data. One is the public key (available to everyone), and the other is the private key (restricted only to a specific user). Public-key cryptography uses a pair of keys for the encryption process, beginning with the encryption of the data with the help of the public key, after which the encrypted data can only be decrypted with the help of the private key. Private-key cryptography works the other way around, by encrypting the information using the private key and decrypting the data using the public key. In the event of a key's compromise or theft, there is an increased likelihood that the user's blockchain account will also be compromised, thereby facilitating unauthorized transactions from the compromised account [[16](#ch21.xhtml#r462)].

### Mitigation

*   **Hardware wallets** are hardware devices that maintain keys and the various wallet public addresses related to blockchains. Technically, hardware wallets are USB-type drives used in storing transaction details which can be operated without the use of batteries [[33](#ch21.xhtml#r479)]. Hardware wallets are one of the more secure and appropriate methods of storing a private key. Some of the hardware wallet brands include `Ledger`, `Ledger Nano S`, `Ledger Nano X`, `Trezor`, etc. [[21](#ch21.xhtml#r467)].

*   **Software wallets** are computer programs that can be installed on an operating system. Software wallets are sometimes referred to as **desktop wallets** and offer improved privacy, ease of use, absence of third-party involvement and secrecy [[33](#ch21.xhtml#r479)]. Software wallets can also be downloaded to a mobile device, a desktop or a laptop computer. The keys maintained in the software wallets are connected to the Internet and therefore are susceptible to theft if the wallet gets hacked. Desktop wallets are typically used for holding smaller amounts of cryptocurrency needed for frequent trading or other transactional purposes, due to their higher user-friendliness. Software wallet brands include `Coinbase`, `Gemini` and `Blockfi` [[20](#ch21.xhtml#r466)].

*   **Paper wallets** are wallets that are typically printed on paper in the form of QR codes. Paper wallets are prone to many dangers due to several inherent flaws; some notable ones being the inability to transfer partial funds and reusability. Typically, paper wallets are mostly used for cold storage purposes [[33](#ch21.xhtml#r479)]. Some of the paper wallet brands include `Bitcoin Paper wallet`, `Wallet Generator` and `Mycelium`, etc. [[4](#ch21.xhtml#r450)].

*   **Cloud wallets** are available online and can be accessed over the Internet with the private keys being stored on a cloud. Cloud wallets are of two types – **hosted** and **non-hosted**. Non-hosted wallets keep the funds and assets under the program's control. Cloud wallets, although vulnerable to DDoS attacks, are useful for handling smaller balances and transactions. Some cloud wallet brands include `Coinbase`, `Binance` and `Meta Mask` [[33](#ch21.xhtml#r479)].

### Malware

Users communicate with the blockchain network through computers vulnerable to various malware. The presence of malware on a user's machine can compromise the blockchain's protective measures in several ways. The malware could take control of the user's account if the user's private key is saved on the device. Malware infecting a user's machine could gain access to other blockchain users' IP addresses and could use this information to target those users. Infected computers may also be used for crypto-jacking – where malware exploits a computer's computing resources to perform proof of work calculations for the attacker's gain [[26](#ch21.xhtml#r472)].

The following sections describe the attributes of some popular blockchain-related malware.

#### ElectroRAT
