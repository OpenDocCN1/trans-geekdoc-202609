
## 128 Blockchain and Artificial Intelligence-Based Solution

to it, does not benefit from it, and even be harmed by it. Although data double spending is not necessarily illegal, many would consider it unethical, and it could have a ‘chilling’ effect on individuals’ willingness to share their health data for socially beneficial purposes. Even if individuals are, themselves, not concerned about double spending, possibly because they are not fully aware of the practice or the harms that could arise from it, government agencies in liberal democracies charged with protecting their citizens against online threats are showing concern [22].

## 6.1.3 CHAPTER OUTLINE AND CONTRIBUTIONS

This chapter seeks to contribute to research on the issue of data double spending. The chapter first describes two marketplaces designed and implemented for individuals to share their data for purposes of AI-driven health research. Case study describes a solution design and implementation that uses the Hyperledger Aries Protocol, the ‘Self-Sovereign’ data marketplace. The chapter then presents a second case study, which is an Ethereum-based solution ‘Ocean Protocol’ data marketplace. Based on a comparison of implementations of both marketplaces, this chapter evaluates the strengths and weaknesses of each solution vis-a-vis the principles of fairness in the processing of personally data. The chapter concludes with a consideration of the extent to which each case operates to achieve fair data processing and protect individuals from data double spending, with the aim of contributing to a clearer articulation of the issue of data double spending, an assessment of how well each solution addresses the issue, and possible directions for future research aimed at countering data double spending.

## 6.2 OVERVIEW OF THE CASE STUDY DATA MARKETPLACES

In this section, we present an overview of our two case study marketplaces preliminary to an analysis of how well each marketplace works to meet principles of fair data processing and prevents data double spending.

## 6.2.1 CASE ONE: SELF-SOVEREIGN DATA MARKETPLACE

### 6.2.1.1 Introduction

Blockchain-based decentralized identity has emerged as a new privacy-preserving approach to identity management. Decentralized identity management provides for individuals to have full control over the use of their own digital identity data. While current identity-based solutions are almost exclusively used for identity or certification authentication, decentralized identity systems have the potential to enable individuals with control over a much wider range of personal data for use beyond identity authentication, a capability that can be leveraged to address the data double-spending problem.

To ensure that the blockchain contains a consistent set of transactions, and that they are ordered correctly, each blockchain has its own consensus mechanism. To determine how the nodes come to an agreement about the contents, ordering, and insertion of transactions in a blockchain, as well as to determine how any changes to has written to the ledger be detectable, a consensus mechanism must be implemented. The Bitcoin protocol achieves transaction blocks using proof-of-work, which must be proportional to the network's total computing power, to ensure a smooth and competitive operation. However, for such a large network to synchronize, the maximum throughput is restricted to a few transactions per second. Correspondingly, the Byzantine Fault Tolerance (BFT) consensus in permitted blockchains arose from the need to protect distributed systems from the threat of ‘Byzantine failure’, where individual nodes in the network may be delayed in receiving new information from other nodes or may be sent-constructed information from malicious nodes. Existing BFT protocols demonstrate thousands of transactions per second with dozens of nodes. The Redundant Byzantine Fault Tolerance project was used as the consensus mechanism in the Hyperledger Indy blockchain project, which operates as a decentralized public key registry in the SSI stack, because of its resilience and fast recovery properties.

SSI credential-based solutions have privacy guarantees that other recording methods. SSI systems tackle with recordkeeping that affects other types of dributed ledgers (i.e., personal information leakage from recording transactions on ledger). When clinical trial transactions are maintained on a blockchain, records frequently contain personally information or metadata that could lead to reidentification of an individual, putting compliance with privacy and data protection at risk. SSI systems that do not record transactions on a ledger are designed to be highly privacy-preserving and comply with data protection legislation (e.g., the EU’s General Data Protection Regulation) since they do raise the prospect of having delete identifiable data from a ledger.

On the other hand, how to consume data while being able to protect data privacy and security prevent leakage of sensitive information is a major challenge in data science today. Confidential computing was born to solve this problem [23]. Privacy-enhancing cryptography-based technology in the field of confidential computing, known as Fully Homomorphic Encryption (FHE) [24], was introduced in 2009. FHE allows computations on encrypted data while preserving the features and the format of the plain text. Thus, sensitive data, such as genetic and health data, can be stored in an encrypted form without losing the utility of the data.

This case studies a new design and implementation of a decentralized and privacy-preserving usage control infrastructure aimed at overcoming the limitations of centralized data usage wherein (I) formulation of the data usage policies (i.e., licensing) and subsequent data usage is under the control of the individual data subject, (2) the data subject receives compensation for the use of their data, and (3) secondary use of the data that has not authorized by the data subject is prevented. The solution was first presented in Kang and Lemieux [18]. It integrates a new individual-centered digital management model with the use of decentralized distributed identifiers (DIDs) and verifiable credentials (VCs) to establish a self-sovereign-oriented distributed trust architecture. FHE capabilities achieve additional privacy and data usage control. The solution design allows for data holders (who we envision also to be the data subjects) to configure a license for their data, integrates a payment system, uses VCs to provide data to consumers with data, and uses FHE to protect the privacy of data and prevent unauthorized secondary use, aimed at achieving a balance between value acquisition and the process of data sharing.

## 6.2.2 SOLUTION OVERVIEW

### 6.2.2.1 Preliminaries

As a foundation for understanding the solution design, we present some preliminary concepts and technical primitives as follows:

- Decentralized identifiers (DIDs), an emerging W3C standard for decentral-ized public key infrastructure that establishes decentralized trust roots.
- DIDComm protocol, a transport-independent protocol that uses DIDs to form and communicate over a cryptographically secure connection.
- Wide Web Consortium (W3C) Verifiable Credentials, standard for cryptographically verifiable digital credentials.

### 6.2.2.2 Roles

Five roles are incorporated into this particular solution design:

- Data Issuer, the issuer of individual's data credentials.
- Individual, a person who is the controller of their own data and provides it, or shares it, with a consumer. In traditional data protection frameworks, this person might also be referred to as the ‘data subject’.
- Distributor, the issuer of license credentials to consumers.
- Data Manager stores individual's data securely and provides the access token of the data.
- Consumer, person or entity with limited use of individual data under auth-ized conditions.

In this decentralized solution architecture, there can be multiple instances of each role (i.e., multiple participating Users, Individuals, Distributors, Data Managers, and Consumers). The basic interactions are as follows: The data is issued to the individual by means of VCs, and the data is encrypted by AES and FHE. The individual shares data by presenting a proof to the data manager. The data manager stores encrypted data in the cloud, and issues a storage creden-t with the access token of the data. The individual sets up the data license using the distributor through the distributor. Only after verifying the license credential, the individual provides the consumer with the token used to access the data and the key used to decrypt the data (AES only; the data always remains fully homomorphically encrypted) using a verifiable credential. Figure 6.1 shows the overview of roles and process flows as a Business Process Model and Notation diagram. Note that in this diagram the individual is identified as the ‘Client.’

### 6.2.2.3 System Architecture

For ease of presenting the design, the architecture is divided into two parts. First, the data licens-ing and consumption architecture is presented. Secondly, Figure 6.2 shows the architecture of data sharing and storage. The data issuer and data manager use a web app that
