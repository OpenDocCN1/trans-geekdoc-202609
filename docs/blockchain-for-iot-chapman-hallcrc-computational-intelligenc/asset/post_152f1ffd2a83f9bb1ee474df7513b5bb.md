
## REFERENCES

- [1] G. Gürkanaynak, İ. Yilmaz, B. Yeşilaltay, and B. Bengi, “Intellectual Property Law and Practice in the Blockchain Realm,” Comput. Law Secur. Rev., vol. 34, no. 4, pp. 847–862, Aug. 2018, doi: 10.1016/j.clsr.2018.05.027.
- [2] V. Gupta, “A Brief History of Blockchain,” 2017. https://hbr.org/2017/02/a-brief-history-of-blockchain (accessed May 04, 2021).
- [3] “Ethereum Foundation|ethereum.org,” 2021. https://ethereum.org/en/foundation/ (accessed May 04, 2021).
- [4] A. van Wirdum, “Segregated Witness Activates on Bitcoin: This is What to Expect—Bitcoin Magazine: Bitcoin News, Articles, Charts, and Guides,” 2017. https://bitcoinmagazine.com/technical/segregated-witness-activates-bitcoin-what-expect (accessed May 04, 2021).
- [5] L. M. (UCL) Nejc Novak, “EU Introduces Crypto Anti-Money Laundering Regulation|by Nejc Novak, LL.M. (UCL)|Medium,” 2018. https://medium.com/@nejcnovaklaw/eu-introduces-crypto-anti-money-laundering-regulation-d6ab0ddedd3 (accessed May 04, 2021).
- [6] C. Zheng Er Low, “Execution of Judgements on the Blockchain—A Practical Legal Commentary,” Harv. J.L. Tech. Dig., 2021, [Online]. Available: https://jolt.law.harvard.edu/digest/execution-of-judgements-on-the-blockchain-a-practical-legal-commentary.
- [7] L. Donahue, “A Primer on Using Artificial Intelligence in the Legal Profession—Harvard Journal of Law & Technology,” 2018. https://jolt.law.harvard.edu/digest/a-primer-on-using-artificial-intelligence-in-the-legal-profession (accessed May 04, 2021).
- [8] H. Son, “JPMorgan Software Does in Seconds What Took Lawyers 360,000 Hours”[The Independent]|The Independent”, 2017. https://www.independent.co.uk/news/business/news/jp-morgan-software-lawyers-coin-contract-intelligence-parsing-financial-deals-seconds-legal-working-hours-360000-a7603256.html (accessed May 05, 2021).
- [9] “Machine Learning Contract Search, Review and Analysis Software|Kira Systems,” https://www.kirasystems.com/ (accessed May 05, 2021).
- [10] “Homepage—LawGeex.” https://www.lawgeex.com/ (accessed May 05, 2021).
- [11] P. Callister, “Law, Artificial Intelligence, and Natural Language Processing: A Funny Thing Happened on the Way to My Search Results,” Law Libr. J., vol. 112, p. 161, Oct. 2020.
- [12] A. Nazarenko and A. Wyner, “Legal NLP Introduction,” Assoc. pour le Trait. Autom. des Langues, 2017.
- [13] H. Zhong, C. Xiao, C. Tu, T. Zhang, Z. Liu, and M. Sun, “How Does NLP Benefit Legal System: A Summary of Legal Artificial Intelligence,” arXiv, Apr. 2020, accessed May 05, 2021. [Online]. Available: http://arxiv.org/abs/2004.12158.

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## An ML-Driven SDN Agent for Blockchain-Based Data Authentication for IoT Network

Rohit Kumar Das
VIT-AP University, Andhra Pradesh, India

Sudipta Roy
Assam University, Assam, India

| Section | Page |
|---|---|
| 8.1 Introduction | 155 |
| 8.1.1 Motivation | 157 |
| 8.1.2 Contribution | 158 |
| 8.2 Related Work | 158 |
| 8.3 Proposed Architecture | 159 |
| 8.4 Potential Research Scope | 161 |
| 8.5 Conclusion | 163 |
| References | 163 |

### 8.1 INTRODUCTION

In recent years, the Internet of Things (IoT) network has gained much attention in terms of its usability and durability. The IoT network has changed the working procedure of various day-to-day applications in today’s world [1]. Being a part of a wireless sensor network (WSN), the easy installation, openness, and low-cost sensor nodes have changed the perception of using WSN. The IoT network uses resource-constraint sensor devices to collect the data and transmit them to the centralized cloud server for further analysis. Though an IoT network can be implemented with limited resources, it still faces some prominent challenges such as reliability, availability, scalability, interoperability, security, and privacy [2].

To further strengthen the working of IoT networks, there has been an effort made to use the advantage of software-defined network (SDN) with IoT networks. SDN can help monitor the network with limited intervention. SDN separates the data plane and the control plane of any network entity. The controller is kept at the control layer responsible for network maneuvering, whereas the data plane has the functionality to transmit data according to the rules provided by the controller [3]. As shown in Figure 8.1, the recent development in the SDN is multiple controllers in the control plane. The data plane of the SDN network consists of OpenFlow switches that are programmable and store the flow rules. The flow rules are installed on the OpenFlow switch by the controller through the southbound interface (SBI). In case any alternation is required, a user can access the network using the northbound interface (NBI) and perform the necessary actions.

![](img/73e16681f7c79384b117f947ee8dd11a_176_0.png)

FIGURE 8.1 A typical SDN-based IoT network architecture [4].

As the IoT devices are connected over the internet, they are accessible from anywhere in the world. This gives rise to the issue of authenticity and integrity of the data being transmitted by the connected IoT devices. Because of the resource-constrained nature of the IoT devices, traditional security mechanisms are not suitable, as they require more resources [5]. Moreover, due to the prominent challenges of IoT networks such as reliability, availability, scalability, and interoperability, it becomes a challenging task to provide a global optimal solution for the security of the data.

### 8.1.1 Motivation

The transmission of data from the IoT gateway node to the cloud infrastructure can be vulnerable to intruders. As discussed earlier, due to the resource-constrained nature of IoT devices, it is not feasible to host security applications directly with the IoT devices [6]. The SDN controller is powerful and has the capability to host the necessary security mechanism. The SDN controller and the IoT gateway device [7] can be configured to limit the unauthorized third party’s access to data.

Blockchain was introduced as a scalable security solution for the IoT network. Blockchain is a distributed ledger technology (DLT) that enables distributed computing facilities with storage, authenticity, and integrity of different transactions made in the network [8]. Furthermore, incorporating Blockchain with distributed SDN controllers can significantly increase the security of IoT networks [9].

Machine learning algorithms have proved to be an adequate measure that can enhance the security level of IoT data through proper validation of data using variously supervised and unsupervised learning approaches [10]. Based on the type of attacks, counterdefense policies can be designed for the IoT system, and the intruder can be detected at the early stage [11]. Reinforcement learning in IoT [12] is one such approach that monitors the environment continuously and generates feedback. Based on the feedback, it can make decisions of how to deal with the associated challenge.

The volume of data generated by IoT systems is inherently high, and maintenance of this volume becomes a challenging task [13]. To overcome this issue, deep learning has shown promising results, which ensures proper validation of data by incorporating testing and training models [14]. The deep learning application can be hosted at the cloud layer where the required amount of resources can be provided for further processing.

### 8.1.2 Contribution

In this chapter, we propose a Blockchain-based distributed SDN architecture for the IoT network. It can help overcome most of the challenges faced by the traditional IoT network. The use of Blockchain and SDN resources for IoT networks can significantly improve network performance. Moreover, to make the network self-sustainable and intelligent, a machine learning (ML) approach has been introduced. The ML-Agent will run along with the SDN controllers that will be responsible for authentication of the data. The proper validation of the data will be carried out by the Blockchain network.

The rest of the chapter is organized as follows. Section 8.2 reviews the related work in this domain. The proposed architecture with an ML-driven SDN agent is presented in Section 8.3. Potential research scope is presented in Section 8.4. Section 8.5 offers a conclusion.

### 8.2 RELATED WORK

There have been efforts made by various researchers and practitioners to provide efficient security measures for an IoT network.

BlockSecIoTNet [15] is an IoT architecture that provides security measures for IoT networks using Blockchain. It monitors for anomalous traffic flows by using SDN controllers that are placed in the distributed Fog network. The cloud layer is responsible for further data processing, which is transmitted to the SDN controller to take necessary actions. The architecture provides security features in the Fog layer by using a Blockchain module that instructs the SDN switches to detect specious flows in the network.

The authors of [16] offer a provision of data traffic classification in SDN networks using ML. It classifies and provides the accuracy of prediction for the flows using support vector machine (SVM), Naive Bayes, and nearest centroid approaches. The study also focuses on incorporating reinforcement learning in the SDN network where the controller acts as an agent that learns the behavior of the network from the collected flows. The proposed model uses the collected data from the various applications and performs offline classification.

BFF-IDS [17] was proposed for intrusion detection in SDN-enabled vehicular networks. Blockchain in BFF-IDS is used for storing the locations and hash values of the vehicles. The control layer consists of Blockchain miner nodes that create blocks, and verification is processed via proof-of-authority. The architecture intends to provide security using
