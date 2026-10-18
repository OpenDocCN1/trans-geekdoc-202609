
## On Detecting Interest Flooding Attacks in Named Data Networking (NDN)–based IoT Searches

Hengshuo Liang, Lauren Burgess, Weixian Liao, Qianlong Wang, and Wei Yu

*Department of Computer and Information Sciences, Towson University, Maryland, USA*

DOI: [10.1201/9781003187158-20](https://doi.org/10.1201/9781003187158-20)

## Contents

- 16.1 Introduction
- 16.2 Preliminaries
- 16.2.1 Named Data Networking (NDN)
- 16.2.2 Internet of Things Search Engine (IoTSE)
- 16.2.3 Machine Learning (ML)
- 16.3 Machine Learning Assisted for NDN-Based IFA Detection in IoTSE
- 16.3.1 Attack Model
- 16.3.2 Attack Scale
- 16.3.3 Attack Scenarios
- 16.3.4 Machine Learning (ML) Detection Models
- 16.4 Performance Evaluation
- 16.4.1 Methodology
- 16.4.2 IFA Performance
- 16.4.2.1 Simple Tree Topology (Small Scale)
- 16.4.2.2 Rocketfuel ISP-like Topology (Large Scale)
- 16.4.3 Data Processing for Detection
- 16.4.4 Detection Results
- 16.4.4.1 ML Detection Performance in Simple Tree Topology
- 16.4.4.2 ML Detection in Rocketfuel ISP Topology
- 16.5 Discussion
- 16.6 Related Works
- 16.7 Final Remarks
- Acknowledgment
- References

## 16.1 INTRODUCTION

The Internet of Things (IoT) has drawn much attention in recent years [1, 2]. The volume of IoT is increased by the millisecond and will expand to 50 billion by 2025 [3]. To better manage IoT devices and such massive data traffic, the IoT search engine (IoTSE) is designed to meet those requirements [4]. Generally speaking, the IoTSE system consists of three components, as shown in Figure 16.1:

![](img/efffc69cb8cda75bcf341884e3396898_433_0.png)

FIGURE 16.1 Internet of Things search engine (IoTSE) structure.

- 1. *Users*: There are two types of users: human users and machine users (e.g., a smart vehicle).
- 2. *IoT searching engine (IoTSE)*: This has three logical layers:
  a. *Network communication layer*: This sets network communication protocols determined based on the type of network that the devices and users are on, such as a wired network or wireless network.
  b. *Data service layer:* This is the core layer of IoTSE, where the search engine is deployed. At this layer, the requests from the users are processed based on the request’s needs in data storage. It is then forwarded to the upper layer for any advanced requirements or sent back to the users.
  c. *Application layer:* This layer analyzes the requested data to extract insightful patterns and generate further decisions.
- 3. *Data source:* IoT devices generate data and send the data back to the data storage of IoTSE. In general, the user posts a request to IoTSE at the beginning. If the requested data exists in data storage, the IoTSE then returns it to the user. Otherwise, IoTSE requests data from IoT devices and sends it back to the user.

The most popular IoTSE is the web-crawler-based system that uses the TCP/IP network structure to transmit data. This type of website-based configuration raises some issues:

- 1. *Domain name system (DNS) issue:* As the number of connected IoT devices grows, so does the number of required IP assignments. The IP management is needed in both public and private networks, which significantly increases demands for network address translation (NAT) and DNS management.
- 2. *Network transferring issue:* Since TCP/IP is an end-to-end communication protocol, if a packet loss occurs during the process, the end user can only discover this issue after the time-out, and the end-user may not resend the request again until then.
- 3. *Vulnerability to IP-based flooding attack:* If the adversaries can spoof the IP address of interest, they can quickly launch a flooding attack to pollute the whole network by continuously transmitting junk data. Furthermore, the adversaries can even send crafted malicious data to a specific target to cause critical damage in the system.

To mitigate performance degradation caused by attacks, machine learning (ML) provides promising solutions. Even for high volumes of data traffic, ML can extract the key structures and features by analyzing internal relationships between data features [5]. This differs from traditional

methods that use the model to distinguish between data points as much as possible and use subjective guessing by simple mathematics models. The ML methods provide in-depth analysis and understanding of the relationship between data. Thus it can provide effective enhancement for analyzing network traffic based on the magnitude of the big data collected [6].

On the other hand, in recent years, a promising network structure, called named data networking (NDN), has been developed for replacing the current TCP/IP structure. Generally speaking, NDN is a user-driven, pull-requested communication architecture. Unlike traditional TCP/IP-based networks, all the object retrieval processes in NDN are based on data names instead of IP addresses. Naming in NDN is under a hierarchical scheme, where the request is defined in a tree manner with a backslash sign (/), such as “/USA/MD/Towson University/CS Department/Lab1.” Due to this human-readable data name, users can name the data freely without any location constraints. When users send a request to the network, it sends to all possible links. Each node records incoming and outgoing network interfaces. Once the request hits a data producer with the same namespace, the data producer sends the packet in the reverse way. In the whole process, there is no receiver address or sender address. Thus the adversary cannot launch any attack based on the address of the target. Even though NDN can stop all IP-based attacks, it can still be affected by namespace-spoofing-based attacks [7]. Therefore, in this study, we focus on detecting flooding attacks based on NDN-embedded IoTSE.

In this study, we make the following three contributions:

- 1. We summarize three different interest flooding attack methods based on the ratios between the number of attacking nodes and the data producers.
- 2. We create our dataset for further study of ML-based detection, using two different scenarios: small scale (one to one and many to one) and large scale (many to many). Using ns3, we design and create the attacking scenarios with different settings and collect raw traffic data that we then preprocess.
- 3. We use the collected dataset to train several ML-based detection schemes and compare their performance. Our experimental results show that our investigated attacks can be easily recognized by ML-based detection schemes.

The remainder of this chapter is organized as follows. In section 16.2, we briefly introduce NDN, IoTSE, and ML. In section 16.3, we present the framework design, our scenarios, and ML models used in our study. In section 16.4, we present performance evaluation and discuss the evaluation results. In section 16.5, we discuss some remaining issues for future research. In section 16.6, we review the existing research efforts that are relevant to our study. Finally, we conclude the chapter in section 16.7.

## 16.2 PRELIMINARIES

In this section, we first provide a brief introduction to NDN, IoTSE, and machine learning.

### 16.2.1 Named Data Networking (NDN)

NDN refers to one development of the future Internet paradigm designed by naming data [8–9]. Nowadays, the Internet architecture that utilizes Transmission Control Protocol/Internet Protocol (TCP/IP) typically is application specific, in which the content names of one application do not affect the content names of another application unless the applications need to exchange data [8–9]. Nonetheless, the current point-to-point driven network has some limitations and weaknesses. From a data-driven perspective, NDN tends to address these by utilizing two types of packets: interest and data packets [10–11].

The consumer applications send these interest packets for named data, which the routers then forward based on the names [9, 11]. Once these interest packets reach the data source, known as a producer, a proxy, or the in-network cache, the interest returns the data packet following the path in reverse [9–11]. NDN utilizes key components to send interest toward data producers: (1) the *forwarding information base (FIB)* contains a list of name-prefixes, finds the longest match based routing protocols, and can have multiple output interfaces for each prefix; (2) the *content store (CS)*
