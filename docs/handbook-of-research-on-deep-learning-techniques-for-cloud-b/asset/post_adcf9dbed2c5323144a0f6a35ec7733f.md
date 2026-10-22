
## Intrusion Detection on NF-BoT-IoT Dataset Using Artificial Intelligence

## INTRODUCTION

The Internet of Things (IoT) is a collection of interconnected IoT nodes that operate autonomously to collect and exchange data with other nodes over an Internet connection. IoT is a widely used technology that is expanding quickly in automated network systems. Security for IoT nodes needs to be decided upon early in the design and implementation process. Even basic gadgets may now connect and share huge volumes of data with other nodes due to the IoT nodes’ quick spread. The security of the data must be taken into account because of the vast amount of data being carried across the network. Modern security measures should be used on the network to protect IoT nodes.

Among the most significant security concerns in the IoT are botnet-based attacks like Distributed Denial of Service (DDoS), Denial of Service (DoS), and others (Ge et al., 2019) where attackers infect nodes with malicious code or overload node information and impair performance. Botnet-based assaults are one of the biggest dangers to IoT nodes.

To handle this kind of difficulty, the IoT node should require specialized standards and communication protocols. The Constrained Application Protocol (CoAP), the Advanced Message Queuing Protocol (AMQP), the Message Queue Telemetry Transport (MQTT), and the Extensible Messaging Presence Protocol (XMPP) are just a few of the messaging and communication protocols that are used to ensure reliable and secure data communication between IoT nodes. Because of its low bandwidth requirements, low memory requirements, and low packet loss, MQTT is the most widely used protocol. MQTT is an IoT-focused communication protocol that is an OASIS standard. There are four crucial parts to the publish/subscribe messaging protocol: clients, brokers, topics, and messages. Data exchange between MQTT-Client (IoT nodes) and Broker (Central node). The broker enables IoT nodes to post and subscribe to subjects simultaneously, subject to node capability. MQTT topics are a form of structured, hierarchical addressing, similar to the forward slash (/) delimiter used in file systems. It includes communications, including data collected by various IoT nodes and messages from various networks.

TCP and UDP are the most often utilized transport protocols in the majority of applications. However, depending on the necessity, multiple message distribution functions and compatible standards are required for IoT applications. The majority of Internet of Things (IoT) nodes use the MQTT communication protocol, which runs on top of TCP, to send and receive data between IoT nodes.

The IoT nodes should use quicker and more effective security measures to detect network traffic irregularities. Firewalls, antivirus software, and intrusion detection systems (IDSs) are examples of cyber security measures. These techniques defend against both active and passive attacks on the data. Without interfering with the system’s operation, a passive attacker just watches and copies data, which typically involves listening in, traffic analysis, etc. IDS is one of the crucial types of detection systems that are used to track abnormalities, in the states of the hardware and the software running in the network, whereas active attackers try to manipulate the content of the data; some of them are DDoS, DoS, etc.

Now, research is concentrated on developing IDS utilising various supervised and unsupervised learning methods. Machine learning is a sort of AI that can extract data from huge databases. Furthermore, neural networks are the basis of deep learning algorithms, which are a subfield of machine learning. Many cyber security activities, such as botnet identification, network traffic analysis, and intrusion detection, involve machine learning and deep learning techniques.

Artificial intelligence techniques are used to recognise and investigate both normal and aberrant situations. By being trained on meaningful data, machine learning and deep learning approaches can identify and predict threats. Numerous artificial intelligence approaches are used in this work to discriminate between normal and abnormal data from the publicly accessible dataset “NF-BoT-IoT.”

The upcoming content of the paper is organized into multiple sections as follows: Section (II) provides various types of cyber security attacks related to the NF-BoT-IoT dataset for implementing machine learning algorithms. Section (III) provides a detailed overview of the machine learning algorithms used. Section (IV) describes the dataset and different ML models used in the experiment, including feature extraction, pre-processing steps, and various evaluation metrics are used. Then in Section (V) the performance evaluation and analysis of the result is discussed. Finally, Section (VI) presents the conclusion and future enhancement of the paper.

## RELATED WORKS

Discuss the related works that are pertinent to IDSs in this section. These studies use machine learning techniques to validate IoT datasets. The most popular IoT datasets are BoT-IoT, UNSW-NB15 dataset, etc., and they are used by many academics for machine learning analysis and testing. The author gives a quick review of the many kinds of intrusion detection attacks, as well as the various kinds of machine learning methods, and demonstrates how the dataset is very helpful for analyzing, rating, and testing the performance of the Model.

Leevy et al. (2021) use the publicly available BoT-IoT dataset, to train and test the model by cross-validation technique, to identify the normal and the information theft traffic. The authors used different ensemble techniques and non-ensembles techniques, to evaluate and analyze the outcome of the data, and to determine the best model.

Swarna Sugi and Ratna (2020) have investigated and analyzed the performance of the developed Intrusion Detection System for recognizing assaults using the model in BoT-IoT dataset. To analyze the model’s performance, the authors used Long Short-Term Memory (LSTM) and K-Nearest Neighbor (KNN).

Alshamkhany et al. (2020) identifies harmful assaults on data using the UNSW-NB15. To analyze the performance of the best-fit model, the authors used a variety of supervised learning techniques, including Naive Bayes, K-Nearest Neighbor, Support Vector Machine, and Decision Trees.

Dwibedi et al. (2020) has compared the CSE-CIC-IDS2018, Bot-IoT, and UNSW-NB15 datasets, analyzing the dataset’s performance using Machine Learning and Deep Learning approaches.

In Idrissi et al. (2021), by using the supervised and unsupervised learning techniques on the BoT-IoT dataset, the malicious activities are validated by using different metrics.

Zeeshan et al. (2022) has proposed a new Protocol Based Deep Intrusion Detection (PB-DID) architecture on the UNSWNB15 and BoT-IoT dataset, to identify the anomalous and non-anomalous activities.

Ullah and Mahmoud (2021) has developed Convolutional Neural Network in three dimensions and validated on the BoT-IoT, IoT Network Intrusion, MQTT-IoT-IDS2020, and IoT-23 intrusion detection datasets, with various performance metrics like accuracy, precision, recall, and F1-Score.

Shafiq et al. (2021) has proposed a new framework model, based on the feature selection on BoT-IoT dataset to evaluate metrics by using machine learning techniques and identify malicious activities.

Shafiq et al. (2020) has designed a feature selection algorithm using the wrapper technique on BoT-IoT dataset, for detecting malicious threats on the IoT network by using various performance metrics.

Table 1 gives details about the different papers, where the authors discussed the performance of intrusion detection using various Machine Learning and Deep Learning Methods.

### Types of Attacks

- 1. **Denial of Service (DoS):** The target network or the nodes cannot be used normally as a result. To hinder the system’s performance or crash the main node so that users cannot access it, it will transmit more packets over the network’s capacity (Thomas & Bhat, 2021).
- 2. **Distributed Denial of Service (DDoS):** A DDoS attack is one in which several devices are used to launch a coordinated DoS attack against a single targeted node.
- 3. **Botnet (BoT):** It makes use of a network of bots, which consists of nodes with malware or viruses that may be activated to launch various assaults on other nodes, such as spam email or DoS, or DDoS. DoS and DDoS attacks, as well as other attacks like theft and reconnaissance, are present in the NF-BoT-IoT dataset.
- 4. **Theft:** It’s a type of group attack in which private information is taken by compromising the security of the main node.

Table 1. Details about the dataset and various ML and DL techniques used by different authors

| Author, Title, and Year of the Paper | Dataset Details | Machine Learning Model Used |
|---|---|---|
| Jeffrey L. Leevy et al., “Detecting Information Theft Attacks in the Bot-IoT Dataset”, 2021 (Leevy et al., 2021) | The model for identifying legitimate and information theft traffic using the cross-validation approach is trained and tested using the BoT-IoT dataset. The result is then evaluated and looked at to choose the best Model. | Non-Ensembles Techniques and Ensemble Techniques. |
| S. Shinly Swarna Sugi; S. Raja Ratna, “Investigation Of Machine Learning Techniques In Intrusion Detection System For Iot Network”, 2020 (Swarna Sugi & Ratna, 2020) | The effectiveness of the developed intrusion detection system is tested and assessed for identifying assaults with the Model using the BoT-IoT dataset. | K-Nearest Neighbor (KNN) and Long Short-Term Memory (LSTM) |
| Mustafa Alshamkhany et al., “Botnet Attack Detection Using Machine Learning”, 2020 (Alshamkhany et al., 2020) | The UNSW-NB15 dataset, which is openly available, has 82,000 records that were used to identify the malicious assaults. | Naïve Bayes, K-Nearest Neighbor, Decision Trees and Support Vector Machine. |
| Smirti Dwibedi et al., “A Comparative Study On Contemporary Intrusion Detection Datasets For Machine Learning Research”, 2020 (Dwibedi et al., 2020) | Comparing the CSE-CIC-IDS2018, UNSW-NB15 and Bot-IoT datasets using various machine learning techniques, and evaluating how the dataset selection influences performance. | Random Forest (RF), XGBoost, Keras Deep Learning models, and Support Vector Machines (SVMs). |
| Idrissi, I., Boukabous, M., Azizi, M. et al., “Toward a deep learning-based intrusion detection system for IoT against botnet attacks”, 2021 (Idrissi et al., 2021) | The BoT-IoT dataset is analysed using various validation measures utilizing deep learning methods. | Convolution Neural Network, Recurrent Neural Network, Long Short-Term Memory, Gated Recurrent Unit. |
