
[⁵](#chap1.xhtml#fn5) A. Goswami, P. Borasi, and V. Kumar. “Global Insurtech Market: Opportunities and Forecast, 2021–2030”. Allied Market Research, [https://www.alliedmarketresearch.com/insurtech-market-A12373](https://www.alliedmarketresearch.com/insurtech-market-A12373). Accessed: Nov 20, 2021.

[⁶](#chap1.xhtml#fn6) “Sustainable Finance”. Monetary Authority of Singapore, [https://www.mas.gov.sg/development/sustainable-finance](https://www.mas.gov.sg/development/sustainable-finance). Accessed: Nov 20, 2021.

[⁷](#chap1.xhtml#fn7) As the first and second lines generally have more funding to buy commercial software and/or hire more (internal and/or external) developers, the tools may be more “advanced” than the `ad hoc` auditing’s automation tool. However, since the tools are still operated by humans, auditing work may spend more time on the implementation and operation effectiveness. IA may also be involved from system design and implementation phase.

© 2022 World Scientific Publishing Company

[https://doi.org/10.1142/9789811250903_0002](https://doi.org/10.1142/9789811250903_0002e)

# Chapter 2

# The Technical Foundations of FinTech: ABCDI and More

**Jun Xu**

## 2.1 Background

Driven by Artificial Intelligence (AI), Blockchain, Cloud, Big Data, and Internet of Things (IoT), technologies truly impact all aspects of financial services, and build the foundation of FinTech. These different technologies generally share some common features and depend on each other. For example, all of them have dedicated algorithms (software), chips, and devices (hardware) to fulfill certain functions. In another example, as illustrated in [Figure 2.1](#chap2.xhtml#fig2-1), AI may gain intelligence support from other technologies, IoT collects data as the “food” for AI, Cloud may provide computing and storage resource to train and serve the model, Blockchain protects data privacy in the process, and finally Big Data platform acts as data `ETL` (Extract, Transform, and Load) and injection tools for AI.

For simplicity, we denote these five major technologies, AI, Blockchain, Cloud, Big Data, and IoT, as A, B, C, D, I, respectively, in this chapter. Besides `ABCDI`, there are many others that nurture the growth of FinTech, which is summarized in [Figure 2.2](#chap2.xhtml#fig2-2). This chapter aims to provide a comprehensive introduction on the technical background of FinTech, and towards the end of this chapter, our readers will be able to have general conceptual and architectural understanding on how these technologies work for FIs. We will start with the basic concept and features of each technology, and then discuss their functionalities via a comparative study. In addition to the five major technologies, we will also briefly touch on other technologies, such as quantum computing and metaverse.

![](images/p38.jpg)

**Figure 2.1.** Relation between AI and BCDI

![](images/p38-1.jpg)

**Figure 2.2.** Technologies for FinTech

### 2.1.1 Artificial Intelligence (AI)

Artificial Intelligence (AI) is the intelligence demonstrated by machines, i.e., a machine performs or make decisions in a human-like manner. It is a broader concept of machines’ capability in accomplishing tasks in a way that we would consider “intelligent”. It brings tons of benefits to financial institutions (FIs), for example:

*   Improve operational efficiency through greater automation and better insights to reduce the operational cost and risk, such as robotic process automation (RPA) and optical character recognition (OCR);
*   Make faster business decisions, such as those relating to loan and credit;
*   Generate new models for both business and operation processes, such as price prediction and analysis, claim processing, wealth management advisory services, and investment process automation;
*   Create highly customized and personalized financial products and services using recommendation engines and chatbots to enhance customer experiences; and
*   Enhance the overall risk management system by fraud detection, regulatory compliance, cybersecurity monitoring, etc.

As shown in [Figure 2.1](#chap2.xhtml#fig2-1), AI is closely related to BCDI technologies. Almost all the major FIs have their AI strategies and have adopted many applications (see examples in [Figure 2.3](#chap2.xhtml#fig2-3)). In [Chapter 3](#chap3.xhtml), we will discuss AI theories and applications in the context of financial services. Given the increasing importance of ethics for responsible and sustainable AI adoption, [Chapter 4](#chap4.xhtml) will discuss AI bias and fairness in a Machine Learning (ML) experimental way.

### 2.1.2 Blockchain/DLT

Blockchain creates shared ledger databases, and is also known as Distributed Ledger Technology (DLT). In this book, we interchangeably use Blockchain and DLT, although some definitions claim they are different.^([1](#chap2.xhtml#rfn1)) It has the following key characteristics:

![](images/p40.jpg)

**Figure 2.3.** AI in financial applications

*   **Immutable.** All validated records are irreversible and cannot be changed. For some Blockchains such as Bitcoin, it is changeable unless someone can take control over 51% of nodes simultaneously.
*   **Distributed and decentralized.** All the participated nodes have a copy of the ledger. Centralized node is unnecessary, and the data can be recorded, stored, and updated on a distributed basis.
*   **Transparent.** As all nodes have a copy of the ledger with its involvement for any data access, it is transparent to all nodes for trust.
*   **Programmable.** Some Blockchains support built-in programming protocols, such as smart contract.

![](images/p41.jpg)

**Figure 2.4.** The relation between Blockchain and ACDI

*   **Open Source.** Most Blockchain codes are open to everyone for trust purpose. Some Blockchains even make their records public so that people can use it to create any relevant application.
*   **Autonomy.** As the consensus protocol makes the data transfer or update safely and all records are individually encrypted, the Blockchain system can be generally autonomous.
*   **Anonymity.** The consensus mechanism with time stamps solves the trust problem between node to node, so data transfer or even transaction can be anonymous or pseudonymous, i.e., use Blockchain address instead of individual identity.

[Figure 2.4](#chap2.xhtml#fig2-4) briefly explains the relation between Blockchain and ACDI. [Chapters 6](#chap6.xhtml) and [7](#chap7.xhtml) will present more details on its applications, such as digital assets and cryptocurrencies.

### 2.1.3 Cloud and Fog/Edge

The Cloud provides on-demand services of IT resources over the Internet. These resources include but not limited to computing, storage, networking, databases, software, analytics, virtual machine and intelligence over the Internet, where computing, storage, and networking are the three major services. Usually, customers use the cloud services in the mode of pay-as-you-go, which is flexible and scalable depending on the usage and requirements. [Table 2.1](#chap2.xhtml#tab2-1) lists some major features of Cloud.

The Cloud has three major service models, i.e., Infrastructure-as-a-Service (IaaS), Platform-as-a-Service (PaaS), and Software-as-a-Service (SaaS). Many FIs are adopting the so-called “Cloud First” strategy by moving the original on-premise infrastructure to the Cloud. The majority concern is the data security in cloud (e.g., in-transit and on-rest data policy using tokenization and encryption for sensitive data). [Chapter 9](#chap9.xhtml) will discuss some technologies and strategies when applying Cloud infrastructure for data integration.
