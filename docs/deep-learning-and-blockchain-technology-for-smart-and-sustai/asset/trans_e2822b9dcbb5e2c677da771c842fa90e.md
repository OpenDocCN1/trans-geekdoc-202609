

technology with the IoT such as smart home applications. Numerous surveys about the combination of BC technology with the IoT have been released recently. With the classification of several use cases, Banerjee et al. [4] provide a thorough literature study on blockchain for IoT. A survey of IoT security and an investigation into the possibility of blockchain technology as remedies are presented in the work of Reyna et al. [5]. Fernández-Caramés and Fraga-Lamas [6] looked at the potential and research challenges of blockchain-IoT convergence. Ali et al. [7], Panarello et al. [8], and Johnson et al. [9] focus on applications of integrating blockchain with IoT. Nevertheless, the majority of the surveys that are now in use have the following drawbacks:

- 1. A general architecture for BC and IoT has not yet been proposed.
- 2. BC technology for fifth generation (5G) networks beyond the IoT has not been examined in any study. Still, the advancement of IoT greatly depends on this topic.
- 3. The majority of the surveys that are currently in place omit other crucial topics, such as the life cycle of smart contracts.

## 4.1.2 Integration of Blockchain with IoT

Blockchain is basically a perfect accompaniment to IoT with the enhanced privacy, interoperability, security, scalability and reliability. In this part, we examine into a novel approach for blockchain with IoT integration, named as Blockchain with Internet of things (BCIoT). BCIoT offers the following benefits:

- 1. Interoperability: The capacity to communicate with physical systems and exchange data among IoT systems is called interoperability and it applies to IoT devices and industrial sectors. This could be accomplished by using an overlay peer-to-peer (P2P) network with consistent access across various IoT systems, layered on top of a blockchain composite layer.
- 2. Traceability: The capacity to track and validate the geographical and chronological details of a data block stored in a blockchain is called traceability of IoT data. Since a historical timestamp is appended to every data block stored in a blockchain, data traceability is guaranteed.
- 3. Reliability: The trait of being dependable in IoT data is known as reliability. It can be protected by the integrity maintained by cryptographic techniques, which are built into blockchains and include digital signatures, hash functions, and asymmetric encryption algorithms.
- 4. Interactions: It describes an IoT system’s ability to communicate with itself without the help of a reliable third party. Blockchain-enabled smart contracts can help attain this autonomy. Specifically, smart contract provisions will execute automatically upon the fulfillment of a predetermined circumstance.

While BCIoT offers an opportunity to enhance IoT, a few challenges must be solved before BCIoT's full potential can be achieved. This study attempts to offer a thorough outline of the most recent developments and issues in BCIoT.

## 4.1.3 Contributions

Considering previous research, our objectives are to:

- i. offer a conceptual overview of blockchain and IoT technologies;
- ii. provide an in-depth investigation of opportunities for integrating BC technology into the IoT; and
- iii. explore the applications of BCIoT.

In brief, the main aids of this study are emphasized as follows:

- 1. After a succinct introduction to the IoT, a list of its salient features is provided. IoT research problems are listed in the interim.
- 2. Following is a description of the main features of blockchains, a taxonomy of the current blockchain systems, and an overview of the major blockchain technologies.
- 3. The confluence of blockchain and IoT is the main topic of this article. In this regard, the potential for fusing BC technology with the IoT is first explored. Next, a proposed and illustrated BCIoT architecture is presented.
- 4. The building of the BCIoT infrastructure is aided by the 5G-beyond networks. There is also discussion of blockchain research challenges for 5G-beyond wireless networks in IoT.
- 5. The article additionally identifies the open research issues in BCIoT and provides a summary of its applications.

## 4.1.4 Convergence of Blockchain and IoT

In this part, first discuss the Prospects for Combining BC Technology with IoT in Section A. We then present the architecture for the integration of BC with IoT (namely BCIoT) in Section B. We next discuss the Applications on BCIoT in Section C.

### A. Prospects for Combining Blockchain Technology with Internet of Things

IoT systems can use from blockchain technologies’ increased interoperability, privacy, and security. Furthermore, the scalability and dependability of IoT systems can also be improved by blockchain [6]. This kind of blockchain-IoT integration is known as BCIoT.

Compared to existing IoT systems, BCIoT offers the potential advantages listed below:

- 1. **Improved Interoperability**: Blockchain basically makes IoT systems more interoperable by converting and storing IoT data in blockchains. In this process, diverse forms of IoT data are transformed and retrieved, then compressed. After that, they are ultimately saved on blockchain platforms. Furthermore, blockchains are made on top of Peer-to-Peer overlay networks, which enable universal Internet access. Another indication of interoperability is how easily they can navigate various kinds of fragmented networks.
- 2. **IoT Security Systems Enhancement**: Since IoT data is kept as blockchain transactions that are encrypted and digitally signed using cryptographic keys (such as the elliptic curve digital signature algorithm, ECDSA), blockchains can provide security for it [9]. Additionally, by automatically updating IoT device firmware to fix any breaches, the integration of blockchain technologies (such as smart contracts) with IoT systems can help to improve system security [10].
- 3. **Traceability and Reliability**: Anywhere, at any time, blockchain data may be recognized and validated. As for earlier transactions, they are all traceable and kept on the blockchains. For example, a blockchain-based product traceability has been established by Lu and Xu [11] to offer traceable services to suppliers and merchants. This allows for scrutiny and proof of the products’ uniqueness and quality. Furthermore, as it is very hard to change or invent any transaction recorded in a blockchain, the immutability of blockchains further ensures the accuracy of IoT data.
- 4. **Autonomic Interactions**: BC technology can enable automatic communication between IoT devices or subsystems. For example, Zhang and Wen [12] offer to automate transactions in which traditional responsibilities such as governments or firms are not involved in the payment process, and distributed autonomous corporations (DACs) are utilized. Smart contracts enable DACs to function autonomously, eliminating the need for human interaction and resulting in cost savings.

The blockchain data may be stored in its entirety or in part on cloud servers and edge servers, whereas IoT devices might just retain a piece of the BC data. IoT and BC may interact in a number of paths, including the implementation of BCIoT [7]:

- 1. In a direct link between IoT and BC infrastructure, IoT devices are able to access BC data kept at servers at the edge co-located with IoT gateways, small BSs, or Macro BSs (MBSs).
- 2. Direct communication between IoT nodes, allowing them to share or access partial BC data through device-to-device connections.
- 3. IoT devices can interconnect with blockchain data using hybrid interaction, which combines cloud and edge servers.

## 4.2 5G Beyond in IoT Using Blockchain

IoT maintains huge potential for blockchain technology, but before blockchain is fully integrated with IoT, many research issues want to be resolved. This is particularly true for next-generation networks that is 5G-beyond or 6G networks, which are vital for building the infrastructure needed for blockchains. The opportunities that blockchain offers to 5G-beyond networks are shown in Figure 4.1 from the lookouts of computation management, network management, and communications. We provide more detail about them in the following sections.

![](img/96b9fa3db3bfeef3ca6e7362a69b2849_83_0.png)

Figure 4.1 5G beyond in IoT using blockchain.

