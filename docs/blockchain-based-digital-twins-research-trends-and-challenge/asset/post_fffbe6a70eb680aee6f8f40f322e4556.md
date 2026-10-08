
- 18. Tranquillini, A. (2016). Blockchain yes, blockchain NO: An outsider (non-IT expert) view. Journal of Securities Operations & Custody, 8(4), 287–291.
- 19. Chaudhry, N., & Yousaf, M. M. (2018). Consensus algorithms in the blockchain: Comparative analysis, challenges, and opportunities. 2018 12th International Conference on Open-Source Systems and Technologies (ICOSST), Lahore, Pakistan, 54–63.

## CHAPTER 4
## Open-Source Platforms for Implementing Blockchain-Based Digital Twins

V. KARPAGAM¹, P. V. KAVITHA¹, and P. V. DEEPA²

- 1 Department of Artificial Intelligence and Data Science, Sri Ramakrishna Engineering College, Coimbatore, Tamil Nadu, India
- 2 Department of Electronics and Communication Engineering, Arunachal College of Engineering for Women, Kanyakumari, Tamil Nadu, India

## ABSTRACT

A twin is a virtual software system that simulates the workings of an actual object or process. The majority of digital twin information is centralized and not adequately support data management security, integrity maintenance, or trustworthiness and precision of time-consuming processes. It is imperative that blockchain be integrated with digital twins to address these restrictions. With blockchains, digital twin data can be shared across secured connection systems with confidence in terms of both accuracy and transmission speed. Blocks of data that track network transactions make up blockchains. These blockchains are maintained on distributed ledgers and are incorporated into the chain as new blocks. Several open-source frameworks of Blockchain such as Hyperledger Fabric, Ethereum, Corda, Quorum, Solidity, Geth, Remix, Mist, Solium, Truffle, Parity, DApp Board, Embark, MyEtherWallet, etc., were explored. Digital Twin open-source tools such as Ansys Digital Twin Builder, Ditto, Kafka, AWS Digital Twin, AWS IoT TwinMaker, Twinbase, etc., were discussed. Also, various open-source platforms such as Dovetail, EtherTwin, SmartTwin, Remix, Solidity, TIBCO Cloud™ Live Apps, Watson IoT Platform, etc., for building Blockchain-based Digital Twin frameworks were discussed.

The chapter discusses the conceptual framework of blockchain-based digital twin and its significance in the industry sector. It explores the open-source platforms for implementing blockchain-based digital twins. This chapter will be useful for researchers, academics, and industry practitioners to understand the amalgamation of blockchain-based digital twins.

Blockchain-Based Digital Twins: Research Trends and Challenges.
A. Prasanth, Vandana Sharma, Rajesh Kumar Dhanaraj, Peturhu Raj (Eds.).
© 2025 Apple Academic Press, Inc. Co-published with CRC Press (Taylor & Francis)

## 4.1 INTRODUCTION

A promising technique called the “digital twin” can significantly improve distributed manufacturing by delivering current functional data representations of actual assets, assisting in decision-making, and reducing potential dangers in such systems. Dispersed manufacturing systems must also work together to anticipate hazards and arrive at consensus-based decision-making [1]. However, due to centralized attack and connection, data interoperability, authentication, and scalability suffer from a single failure.

To mitigate the aforementioned challenges, the adoption of Blockchain technology with Digital Twin enables safe data sharing and interoperability among numerous stakeholders, including manufacturers, suppliers, service providers, and users. Blockchains are digital databases or ledgers that consist of growing lists of records, named as a chain of blocks, each containing a list of transactions or data entries.

Blockchain and Digital Twins alter industry-oriented applications and guarantee data management security. Blockchain and Digital Twin technologies can deliver useful data and a host of advantages for decision-making and data management without the aid of a central authority. Furthermore, Blockchain-based technologies provide Digital Twins with security and integrity. As a result, merging Blockchain with Digital Twins improves corporate efficiency and legitimacy. Blockchain-based Digital Twin has the potential to change several sectors due to the growth in market share and requirements, and it also aids enterprises in broadening their horizons. Businesses can gather pertinent data about their products and processes by fusing blockchain technology and digital twins. Additionally, it motivates companies to produce more genuine and distinctive goods, giving them a competitive edge over rivals who might use analogous procedures for their goods. Indeed, combining digital twins with blockchain technology can greatly improve security, data privacy, and solution credibility in terms of product design and process outcomes. Although blockchain enables them to keep information, digital twins are created using conventional technology.

## 4.2 INTRODUCTION TO DIGITAL TWIN

Digital twin explores the simulated representation of an actual object or thing [2]. A thing can be a car, an engine, a building, or a flyover. The data can be gathered from sensors connected with these actual assets and converted into a virtual system. Because of digital twins, people can view important information about how an actual object performs in the real world. The addition of various cutting-edge domains like Intelligent Systems, Data Science, the Internet of Things, Sensors, Simulation, and Connectivity significantly enhanced the sophistication and capabilities of digital twins [3].

### 4.2.1 FEATURES OF DIGITAL TWIN

1. **Connectivity**: It is the basis of a digital twin. It establishes a link between the actual element and its digital counterpart. Sensors provide the connectivity of physical objects by acquiring, integrating, and communicating data through different integration techniques.
2. **Homogenization**: Data homogeneity is both the result and the enabler of digital twins. It allows data to be separated from its actual form.
3. **Re-Programmability**: Digital twins provide programmability automatically via artificial intelligence techniques, sensors, and predictive analysis.
4. **Digital Traces**: These are left by digital twin technology. In the event of a machine failure, the trails can be used to locate the source of the problem.
5. **Modularity**: It refers to the design and customization of products and industrial modules. Modularity added to functional models allows producers to fine-tune machinery and models. Digital twin features are represented in Figure 4.1.

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_131_0.png)

FIGURE 4.1 Digital twin features.

## 4.2.2 WORKING OF DIGITAL TWIN

A digital twin contains three main components. They are:

- **Past Data:** It includes historical information, precise systems, and complete processes.
- **Present Data:** Sensor data, outputs from production platforms, and pertinent information from systems along the distribution chain are all included.
- **Future Data:** This is predicted data and insights from input and machine learning models.

The following are three working steps of digital twin [4]:

- **Step 1: Data Gathering and Simulation:** The data is gathered and then simulated into a virtual model. Locally or on a distributed cloud, the gathered information is stored.
- **Step 2: Applying Cognitive Insights:** When simulation data is received, parameters are applied to tangible assets and merged for precise virtual representation. The data is reviewed to determine its variations and tolerances. To better understand the dynamics of the information being presented, natural language processing, machine-to-machine communication, acoustical video analytics, and other approaches are used.
- **Step 3: Dynamic Recalibration:** The environment around that particular gadget is dynamically recalibrated using the gathered information and cognition. This impacts the phases of design, build, and operation. The performance of tangible assets is enhanced by integrating data into both real-world and digital representations.

The process of digital twins is illustrated in the given Figure 4.2.
