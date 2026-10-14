
Newaz et al. (2020) presented an exhaustive survey on the security and privacy issues in modern health-care systems. They reported that the increasing use of technologies like IoTs, implantable medical devices (IMDs) and body area networks (BANs) in healthcare not only improved the quality of patient care and treatment; but had exposed the healthcare systems to numerous cyber threats breaching their integrity, confidentiality, availability, privacy and security. They listed different blockchain-based approaches, among other approaches, to counter the potential challenges. Research directions discussed include the develop-ment of lightweight and symmetric cryptographic protocols considering the emergency where communi-cation with unauthorized personnel may be required, development of standard communication protocols, fault-tolerant design, intrusion detection mechanism, fine-grained access control and privacy-preserving healthcare systems.

[Durneva et al. (2020](#ch52.xhtml#ref52_2)) reviewed the ongoing research for use of blockchain technology in patient care. They concluded that personal health records, mobile health and telemedicine, medical information systems, data preservation systems and social networks, health information exchanges and remote monitoring systems, and medical research systems were the major healthcare applications using blockchain technology. They reported various blockchain implementation challenges like security and privacy vulnerabilities, weak access control mechanisms, high computing power and implementation costs, latency issues, blockchain adoption issues, compatibility issues with existing healthcare systems, data storage limitations, etc. They advocated the use of smart contracts to build decentralized autonomous organizations (DAOs) and distributed applications (DApps) to disrupt patient care.

Patel (2019) proposed a blockchain-based crossdomain framework for secure and decentralized sharing of medical images and patient defined access permissions. The proposed framework eliminated third-party access to protected health information, facilitated interoperable health systems, and generalized to domains other than medical imaging. The complexity of the privacy and security models and an unclear regulatory environment were reported to be the major concerns. Moreover, the largescale feasibility of such an approach was still to be established.

Hassan et al. (2019) discussed the privacy challenges with the integration of blockchain technology in IoT applications. Different privacy preservation strategies and their weaknesses were discussed in blockchain-based IoT systems named as anonymization, encryption, private contract, mixing, and differential privacy. Highlighted future research directions include the development of lightweight privacy-preserving encryption approaches and application-specific use of improved blended strategies.

Thwin and Vasupongayya (2019) proposed a blockchain-based privacy-preserving access control model for the PHR system. It used hyperledger fabric – a private blockchain, cloud storage, and other cryptographic techniques consisting of proxy re-encryption, hashing, and digital signature to meet the set goals. It offered features such as enabling individuals to securely store and shares their PHR data, grant/ revoke access to individual PHR data, and establish the integrity of the PHR data. However, since the proposed model used the default hyperledger fabric parameter, its performance under configurable parameters was not established.

## Findings

It is evident from the literature survey that blockchain technology has also disrupted healthcare other than revolutionizing business, finance and other fields. Blockchain technology is being intermingled with almost every existing technology to harness its intrinsic features to improve healthcare. Though a lot of work has been done, still some issues remain to be addressed for it to be readily adoptable. [Table 52.1](#ch52.xhtml#tab52_1) shows the identified problematic areas with the frequency of publication highlighting them.

[Table 52.1. Frequency of identified problem areas.](#ch52.xhtml#R_tab52_1)

| Problem area || Frequency |
| --- | --- |
| Regulatory/ legal framework || 2 |
| Access control || 4 |
| Latency || 2 |
| Scalability || 4 |
| Privacy || 3 |
| Performance || 5 |
| Security || 3 |
| Interoperability || 5 |
| Integration || 3 |
| smart contract || 4 |
| Use of AI || 3 |
| Consensus protocol || 1 |
| Encryption || 1 |
| Search || 1 |

Major research gaps observed ([Figure 52.3](#ch52.xhtml#fig52_3)) from the literature reviewed are briefly discussed below:

![Figure 52.3  Identified research gaps](images/fig52_3_C.jpg)

[Figure 52.3  Identified research gaps](#ch52.xhtml#R_fig52_3)

*   Interoperability, the ability whereby a blockchain can freely interact to access/exchange data with other blockchains, among the various blockchain based healthcare systems is missing. This leads to completely isolated disparate healthcare systems, unable to communicate and exchange important healthcare information vital for saving precious lives ([ElRahman and Alluhaidan, 2021](#ch52.xhtml#ref52_4); [Fetjah et al., 2021](#ch52.xhtml#ref52_5); [Khatri et al., 2021](#ch52.xhtml#ref52_8); [Xie et al., 2021](#ch52.xhtml#ref52_16); [Lin et al., 2022](#ch52.xhtml#ref52_10)).

*   Blockchain based healthcare systems, as in other use cases, too are suffering from performance issues (Thwin and Vasupongayya, 2019; [Ejaz et al., 2021](#ch52.xhtml#ref52_3); [ElRahman and Alluhaidan, 2021](#ch52.xhtml#ref52_4); [Adere, 2022](#ch52.xhtml#ref52_1); [Lin et al., 2022](#ch52.xhtml#ref52_10)).

*   Data access control, especially in case of certain emergency, is still a challenge ([Durneva et al., 2020](#ch52.xhtml#ref52_2); Newaz et al., 2020; [Fetjah et al., 2021](#ch52.xhtml#ref52_5); [Liu et al., 2021](#ch52.xhtml#ref52_11)).

*   Scalability of blockchain based healthcare systems remains persistent ([Fetjah et al., 2021](#ch52.xhtml#ref52_5); [Khatri et al., 2021](#ch52.xhtml#ref52_8); Liang and Ji, 2021; [Xie et al., 2021](#ch52.xhtml#ref52_16)).

*   Blockchain-based healthcare systems cannot be seamlessly integrated with existing classical healthcare systems ([Yaqoob et al., 2021](#ch52.xhtml#ref52_17); [Adere, 2022](#ch52.xhtml#ref52_1); [Lin et al., 2022](#ch52.xhtml#ref52_10)).

*   Regulatory/legal framework for the use of blockchain based healthcare systems; nationwide and worldwide is not well defined ([Xie et al., 2021](#ch52.xhtml#ref52_16); [Yaqoob et al., 2021](#ch52.xhtml#ref52_17)).

## Work proposal

Contemporary blockchain based healthcare systems face many challenges and barriers hindering seamless implementation of the technology. These include privacy and security issues, consensus algorithms, computational power requirements, implementation costs and integration challenges with existing healthcare information system ([Durneva et al., 2020](#ch52.xhtml#ref52_2)).

Though the research is in progress to fix these issues, almost negligible attention is drawn toward interoperability aspect till present ([ElRahman and Alluhaidan, 2021](#ch52.xhtml#ref52_4); [Fetjah et al., 2021](#ch52.xhtml#ref52_5); [Khatri et al., 2021](#ch52.xhtml#ref52_8); [Xie et al., 2021](#ch52.xhtml#ref52_16); [Lin et al., 2022](#ch52.xhtml#ref52_10)). A variety of blockchains are used in healthcare systems to harness intrinsic benefits of the technology. All such implementations are being worked/reworked upon in isolation to fix/ improve any performance issues. But no work is being carried out to make such implementations to interoperate i.e., to communicate and exchange healthcare information, which may be vital for realizing effective healthcare for mankind.

Objective of the proposed research is to present a feasible solution for the problem of blockchain interoperability for effective healthcare.

## Methodology
