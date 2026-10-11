
# Chapter 15: An Implementation of Decentralized Secured Tweeting Platform

## Security of a Tweeting App

**Authors:**
- Sumathi Pawar, Information Science & Engineering, NMAMIT, Nitte, India
- K. Suma, Mangalore Institute of Technology and Management, Moodabidri, India
- Ankitha P., Information Science & Engineering, NMAMIT, Nitte, India
- Vandana B. S., Information Science & Engineering, NMAMIT, Nitte, India
- RajaLakshmi Samaga, Information Science & Engineering, NMAMIT, Nitte, India

## Abstract

A decentralized secured tweeting platform utilizes blockchain technology to distribute control and data across a network of participants, challenging the centralized model. It provides enhanced privacy, reduced content manipulation, and resistance to centralized control of user content. This system represents a decentralized tweeting social media platform with the objective of furnishing users with a communication environment that is both secure and characterized by transparency. Through the integration of smart contracts, users can transact directly and securely without the need for intermediaries. `ReactJS` empowers a responsive and user-friendly interface, fostering real-time interaction among users to create a decentralized social media platform, enhancing security and transparency to unprecedented levels. Blockchain technology confirms that data is securely stored, immutable and transparent. The proposed system enables users to post tweets, follow other users, like and comment on posts and engage in real-time messaging. This article also presents the implementation of the system.

## Introduction

This article aims to develop a secure tweeting app utilizing blockchain Web 3.0, employing `Solidity`, `Next.js`, and `Sanity.io`. The system mimics Twitter's functionality, providing a secure platform for tweeting. It redistributes control and data ownership to users, avoiding the risks of censorship and data leaks in day-to-day social media. Decentralized system utilizes distributed ledger technology, smart contracts and peer-to-peer networks to ensure user-centric digital social media application. The front end is built with `Next.js` and styled using `Tailwind CSS`. Additionally, a custom smart contract is created with `Solidity`. As Zheng et al. (2017) have noted, blockchain, the primary network for cryptocurrency, supports the app, while Twitter remains a popular social media platform for cryptocurrency enthusiasts to share their thoughts in short posts.

Creating a smart contract for a tweeting app using blockchain involves writing the contract in `Solidity`, the programming language for Ethereum. An example of a basic smart contract that enables users to post tweets and retrieve them is given in the implementation section. This contract includes basic functionality for posting and viewing tweets. According to Valeti Deepika and Lalitha Bhaskari (2020), `Truffle` is utilized for deploying the smart contract on the `Ubuntu (Debian)` OS. This project offers enhanced security compared to a standard Twitter app. Smart contracts, which are programmable digital agreements, improve communication and facilitate long-term asset tracking. They are also valuable for maintaining relationships with consumers.

In this application, an instance of the `Web3 API` is created for connecting to the local blockchain network. This system also uses the `Web3 API` to interact with the smart contract by creating a contract instance and calling its methods to create tweets, like tweets and retrieve tweets.

`Web3.js` is a JavaScript library designed to facilitate interaction with the Ethereum blockchain. Sumathi and Manjula (2023) highlight the open-source APIs provided by `Web3.js` for linking the blockchain, initiating transactions, and engaging with smart contracts. `Ethers.js` is another JavaScript library that allows interaction with the Ethereum blockchain. It provides a simpler API compared to `Web3.js` and has better support for `TypeScript`.

`IPFS` (Interplanetary File System) is a distributed storage system for files, enabling storage and sharing across a distributed network of computers. It provides an API that facilitates the storage and retrieval of files from the `IPFS` network. `Solidity` is a programming language needed to write smart contracts on the Ethereum blockchain. It is used to define the business logic of an app and is executed on the `Ethereum Virtual Machine (EVM)`. This application uses the `Solidity API` to define the smart contract for the tweet structure that represents a tweet and provides methods for creating tweets, liking tweets, and retrieving tweets.

`Open Zeppelin` is a library of reusable smart contracts that provide security and modularity to the app. It offers a range of smart contracts, from simple ones like ownership contracts to more complex ones like multi-signature wallets. This application uses `React-Bootstrap` to create UI components such as forms, buttons, and list groups.

In this article, Section 2 discusses the literature review, Sections 3 and 4 cover various methods for securing this app and Sections 4 and 5 focus on implementation and results.

## Literature Review

The goal of decentralized tweeting systems is to counter the algorithmic bias, privacy issues, and data breaches that come with centralized platforms (Marx & Cheong, 2023). The decentralization of social media platforms poses new difficulties in terms of adoption, control, privacy, operation and security. Decentralization offers consumers and content creators, security and stability by shifting trust from closed corporate rules to open blockchain technologies (Bhusare et al., 2023). Decentralized systems lose some of the privacy protections provided by central parties due to the lack of a single point of data aggregation, which increases the risk of privacy invasion through metadata (Greschbach et al., 2012).

## References

Tournier, J., Lesueur, F., Le Moue¨l, F., Guyon, L., & Ben-Hassine, H. (2021). A survey of IoT protocols and their security issues through the lens of a generic IoT stack. *Internet of Things: Engineering Cyber Physical Human Systems*, 16, 100264. DOI: [10.1016/j.iot.2020.100264](http://dx.doi.org/10.1016/j.iot.2020.100264)

Venkatraman, S., & Overmars, A. (2020, November). IoT Authentication and Security Challenges. In *Proceedings of the 3rd International Conference on Research in Applied Science*, Munich, Germany (pp. 6-8).

Wang, N., Wang, P., Alipour-Fanid, A., Jiao, L., & Zeng, K. (2019). Physical-layer security of 5G wireless networks for IoT: Challenges and opportunities. *IEEE Internet of Things Journal*, 6(5), 8169–8181. DOI: [10.1109/JIOT.2019.2927379](http://dx.doi.org/10.1109/JIOT.2019.2927379)

Yu, D., Zhang, L., Chen, Y., Ma, Y., & Chen, J. (2020). Large-scale IoT devices firmware identification based on weak password. *IEEE Access: Practical Innovations, Open Solutions*, 8, 7981–7992. DOI: [10.1109/ACCESS.2020.2964646](http://dx.doi.org/10.1109/ACCESS.2020.2964646)

Yu, M., Zhuge, J., Cao, M., Shi, Z., & Jiang, L. (2020). A survey of security vulnerability analysis, discovery, detection, and mitigation on IoT devices. *Future Internet*, 12(2), 27. DOI: [10.3390/fi12020027](http://dx.doi.org/10.3390/fi12020027)

Yugha, R., & Chithra, S. (2020). A survey on technologies and security protocols: Reference for future generation IoT. *Journal of Network and Computer Applications*, 169, 102763. DOI: [10.1016/j.jnca.2020.102763](http://dx.doi.org/10.1016/j.jnca.2020.102763)
