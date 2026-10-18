
- 14.3.2 Population and Sampling
  - 14.3.2.1 Population
  - 14.3.2.2 Sample
- 14.3.3 Sources and Types of Data
- 14.3.4 Model for Analysis
  - 14.3.4.1 Big Data
  - 14.3.4.2 Big Data Analytics
  - 14.3.4.3 Insights for Action
  - 14.3.4.4 Predictive Analytics
- 14.3.5 Validity and Reliability
- 14.3.6 Summary of Research Methodology
- 14.3.7 Possible Outcomes
- 14.4 Analysis and Research Outcomes
  - 14.4.1 Overview
  - 14.4.2 Support Vector Machine
  - 14.4.3 KNN Algorithm
  - 14.4.4 Multilinear Discriminant Analysis (LDA)
  - 14.4.5 Random Forest Classifier
  - 14.4.6 Variable Importance
  - 14.4.7 Model Results
  - 14.4.8 Classification and Regression Trees (CART)
  - 14.4.9 Support Vector Machine
  - 14.4.10 Linear Discriminant Algorithm
  - 14.4.11 K-Nearest Neighbor
  - 14.4.12 Random Forest
  - 14.4.13 Challenges and Future Direction
    - 14.4.13.1 Model 1: Experimental/Prototype Model
    - 14.4.13.2 Model 2: Cloud Computing/Outsourcing
    - 14.4.13.3 Application of Big Data Analytics Models in Cyber Security
    - 14.4.13.4 Summary of Analysis
- 14.5 Conclusion
- References

## 14.1 INTRODUCTION

### 14.1.1 Background on Cyber Security and Machine Learning

Cyber security consolidates the confidentiality, integrity, and availability of computing resources, networks, software programs, and data into a coherent collection of policies, technologies, processes, and techniques in order to prevent the occurrence of attacks [1]. Cyber security refers to a combination of technologies, processes, and operations that are framed to protect information systems, computers, devices, programs, data, and networks from internal or external threats, harm, damage, attacks, or unauthorized access, such as ransomware or denial of service attacks [2]. The rapid advances in mobile computing, communications, and mass storage architectures have precipitated the new phenomena of big data and the Internet of Things (IoT). Outsider and insider threats can have serious ramifications on an institution, for example, failure to provide services, higher costs of operations, loss in revenue, and reputational damage [2, 3]. Therefore, an effective cyber security model must be able to mitigate cyber security events, such as unauthorized access, zero day attack, denial of service, data breach, malware attacks, social engineering (or phishing), fraud, and spam attacks, through intrusion detection and malware detection [4, 5].

The researcher identifies the primary variable that this study seeks to investigate as cyber security. Prior literature notes that the definition of cyber security differs among institutions and across nations [6]. However, in basic terms cyber security may be defined as a combination of technologies and processes that are set up to protect computer hosts, programs, networks, and data from internal and external threats, attacks, harm, damage, and unauthorized access [2]. The major cyber security applications are intrusion detection and malware detection. The transformation and expansion of the cyber space has resulted in an exponential growth in the amount, quality, and diversity of data generated, stored, and processed by networks and hosts [7]. These changes have necessitated a radical shift in the technology and operations of cyber security to detect and eliminate cyber threats so that cyber security remains relevant and effective in mitigating costs arising from computers, networks, and data breaches [2].

The strength of the overall security in cyber security is determined by the weakest link [10]. Access controls and security mechanisms should be encapsulated in the company objectives. It is common practice to give employees access to only what they are entitled to, with the appropriate compartmentalized security and access privileges to mitigate against any possible security breaches [10]. Firewall protection has proved to be inadequate because of gross limitations against external threats [11]. However, operating systems hardening can supplement the firewall protection, and this involves installing and patching the operating system and then hardening and/or configuring the operating system to adequately provide acceptable security measures.

Machine learning is a field within artificial intelligence (AI) that is the science and engineering of making intelligent machines. Machine learning algorithms require empirical data as input and then learn from this input. The amount of data provided is often more important than the algorithm itself. Computers are instructed to learn through the process called machine learning (ML). Machine learning (ML) algorithms, inspired by the central nervous system, are referred to as artificial neural networks (ANNs). Deep learning (DL), as a special category of ML, brings us closer to AI. ML algorithms as part of artificial intelligence (AI) can be clustered into supervised, unsupervised, semisupervised, and reinforcement learning algorithms. The main characteristic of ML is the automatic data analysis of large data sets and the production of models for the general relationships found among data. The three classes of ML are as illustrated on Figure 14.2 [12]:

![](img/efffc69cb8cda75bcf341884e3396898_328_0.png)

## FIGURE 14.2 Three levels of machine learning.

Source: [13].

- *Supervised learning*: Where the methods are given inputs labeled with corresponding outputs as training examples
- *Unsupervised learning*: Where the methods are given unlabeled inputs
- *Reinforcement learning*: where data is in the form of sequences of observations, actions, and rewards

Machine learning uses intelligent software to enable machines to perform their jobs proficiently, which is the backbone of machine intelligence [14]. Most industries are embracing artificial intelligence and machine learning in their customer relations strategies to ensure that their client’s experience is the best it can be. To succeed, one needs an investment strategy that adapts to deal with the new paradigm in markets.

Supervised learning models are grounded on generating functions that map big datasets (features) [15] into desired outputs [16]. Artificial intelligence is the simulation of human intelligence in machines through programming computers to think and act like human beings [17]. Big data analytics [18] has emerged as a discipline of ways to analyze, systematically extract/mine information from [76], or otherwise deal or work with enormous or complex datasets that are too large for traditional data-processing methodologies to deal with them [17]. Unsupervised learning is seen as a mathematical process of minimizing redundancy or categorizing huge datasets based on likeness [17]. Big data analytics is not only about the size of data but also hinges on volume, variety, and velocity of data [19]. It is important to note that machine learning is a technique of big data analytics that includes programming analytical model construction [20]. The output of a machine learning model often includes perceptions and/or decisions.

The greater risk of cyber attacks has stemmed mainly from the monotonic increase in the use of internet-connected systems [1]. The cyber attacks are becoming increasingly sophisticated with zero-day exploits and malware that evade security measures. Furthermore, commercial interest in cyber attacks has increased. The transformation and expansion of the cyber space have led to the generation, use, storage, and processing of big data, that is, large, diverse, complex, multidimensional, and usually multivariate datasets [21]. The characteristics of big data are volume, velocity, variety, veracity, vocabulary, and value [21]. *Volume* denotes big data as massive; *velocity* denotes the high speed of big data; *variety* denotes the diversity of big data; *veracity* denotes the degrees of trustworthiness in big data; *vocabulary* denotes conformity of big data to different schema, models, and ontologies; and *value* denotes the cost and worth of big data [21]. Big data has necessitated the development of big data mining tools and techniques widely referred to as big data analytics [22, 23]. Big data analytics [24] refer to a combination of well-known tools and techniques, for example machine learning, and data mining, that are capable of leveraging useful data usually hidden in big data [25] and creating an interface in the form of linear and visual analytics [21].

An artificial intelligence system uses computer technologies to perform tasks based on natural human problem-solving techniques. People’s daily lives and work have been impacted by the rapid development of computing technology and the internet. As some of its advantages, AI can discover new and sophisticated changes in attack flexibility. AI can handle the volume of data, and this means AI can enhance network security by developing autonomous security systems to detect attacks and respond to breaches. AI can offer assistance by expanding the monitoring and detection of suspicious activities. Some of the relevant common applications of AI include the following:
