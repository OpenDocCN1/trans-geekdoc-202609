
3.  [Zeng, W., Meng, Q., and Li, R.](#ch22.xhtml#R_ref22_3) (2019). Design of intelligent classroom attendance system based on face recognition. 2019 IEEE 3^(rd) Information Technology, Networking, Electronic and Automation Control Conference (ITNEC), pp. 611-615.
4.  [Gurucharan, M. K.](#ch22.xhtml#R_ref22_4) (2020). Machine learning basics: support vector machine (`SVM`) classifier. `https://towardsdatasci-ence.com/machine-learning-basics-support-vector-machine-svm-classification-205ecd28a09d` (Not accessible as of \[03/08/2024\])
5.  [Saha, S.](#ch22.xhtml#R_ref22_5) (2018). A comprehensive guide to convolutional neural network, article in towards data science. `https://to-wardsdatascience.com/a-comprehensive-guide-to-convolutional-neural-networks-the-eli5-way-3bd2b1164a53` (Not accessible as of \[03/08/2024\])
6.  [Zhaoqing, S., Su, Z., and Zhicheng, L. I.](#ch22.xhtml#R_ref22_6) (2010). Face Images Recognition Research Based on Smooth Filter and Support Vector Machine. pp. 2760–2764.
7.  [Balcoh, N. K., Yousaf, M. H., Ahmad, W., and Baig, M. I.](#ch22.xhtml#R_ref22_7) (2012). Algorithm for efficient attendance management: face recognition based approach. International Journal of Computer Science Issues, 9(4), 146–150.
8.  [Roshantharanga, J. G., Samarakoon, S. M. S. C. T., Karunarathne, A. P., Liyanage, K. L. P. M., Gamage, M. P. A. W., and Perera, D.](#ch22.xhtml#R_ref22_8) (2013). Smart attendance using real time face recognition. Res. Symp. Eng. Adv. 41–44.
9.  Anggo, M. and Arapu, L. (2018). Face recognition using Fisher face method. Journal of Physics: Conference Series, 1028(1).
10.  [Arsenovic, M., Sladojevic, S., Anderla, A., and Stefanovic, D.](#ch22.xhtml#R_ref22_10) (2017). Face time - deep learning based face recognition attendance system. IEEE 15th International Symposium on Applied Machine Intelligence and Informatics, pp. 53–57.

# 23 Arrangement and capturing of malevolent packets in network using machine learning

Rakesh Kumar Yadav^([^(22)](#fn22))

DOI: [10.1201/9781003534136-23](https://dx.doi.org/10.1201/9781003534136-23)

## Abstract

The importance of cyber security and cyber warfare has grown in a world where digitalization is rapidly expanding and developing. Malware, or malicious software, has emerged as a major problem in the modern digital age. The rapid proliferation of malware is a major danger to online safety. Therefore, steps taken to secure the network are crucial in warding off these cyber dangers. Using a network analyzer to gather instances of botched and artificially created benign packets, the authors of the current paper collected data for a network traffic classifier using a random forest (`RF`) machine learning approach. The suggested classifier can determine whether or not a given piece of traffic (`HTTP`, `TCP`, `UDP`, `IPv4-v6`) is safe to proceed with. The experimental findings show that the suggested model using the `RF` classifier is more accurate than the baseline.

**Keywords:** Malware, network traffic, packets capturing, random forest, web traffics

## Introduction

Malware is a growing problem that threatens system and network integrity, privacy, authentication, and control, as well as functionality, as internet use continues to rise \[[1](#ch23.xhtml#ref23_1)\]. Malware can be broadly defined to include viruses, logic bombs, worms, spyware, and any other type of malicious software that causes harm to a computer or network \[[2](#ch23.xhtml#ref23_2), [3](#ch23.xhtml#ref23_3) and [4](#ch23.xhtml#ref23_4)\]. Recent years have seen a huge increase in the yearly amount of network security incidents due in large part to the frequency of malware assaults in the network. Cyber security researchers face a challenging problem in figuring out how to stop these attacks, as they draw attention to the fragility of networks and computers. Malware of today uses encrypted web traffic (`HTTPs`) to communicate and carry out its destructive tasks. The encrypted data sent between the client and server is the primary function of the `HTTPs` protocol. However, malware developers utilise encryption for malicious or unlawful purposes, whereas a genuine user benefits from its use. Encryption decreases the efficiency of pattern matching technologies, such as signature-based antivirus, making them ineffective against malware in `HTTPs` (encrypted) traffic. The use of machine learning techniques in the analysis and identification of malware has recently gained popularity among researchers. The proposed study applies machine learning and statistical computing to the subject of network security, with a primary focus on this area. Classifying `HTTPs` and `IPv4-v6` traffic using a machine learning-based categorization model is the primary contribution of our work. Additionally, `RF` classifier is used throughout model construction, training, and evaluation, leading to improved accuracy and a decreased false positive rate (`FPR`).

The given paper is organized into following sections. Section 2 provides review of studies conducted in the context of protocol and network packets classification. Section 3 presents the methodology and details of our proposed approach. It involves identification of benign and malicious packets in `HTTP`’s and `IPv4-v6` traffic. Section 4 presents analysis of results. Section 5 presents summary of the findings and proposes recommendations for further research.

## Literature Review

When it comes to malware detection in `HTTPS` traffic, \[[5](#ch23.xhtml#ref23_5), [6](#ch23.xhtml#ref23_6)\] cites considerable use of machine learning-based network traffic categorization algorithms. We see a classifier proposed to discover families of malware linked to unsecured `HTTP` connections \[[7](#ch23.xhtml#ref23_7), [8](#ch23.xhtml#ref23_8)\]. To improve malware detection in `HTTPS` traffic while decreasing false positives, a metric index `KNN` classification algorithm is applied to a small dataset of very dimensional network traffic descriptors. Although the authors have addressed the issue of identifying rogue servers, they have not demonstrated the typical accuracy of classifiers in doing so. Researchers \[[9](#ch23.xhtml#ref23_9), [10](#ch23.xhtml#ref23_10)\] created and investigated an `LSTM`-based malware detection approach that makes use of just the observable characteristics of `HTTPS` traffic. Speech recognition, translation, and other NLP applications make heavy use of `LSTM` networks \[[11](#ch23.xhtml#ref23_11)\]. This new technique allows for the collection of massive amounts of both hostile and innocuous network traffic for model assessment. By analyzing the traffic on a network in relation to things like host addresses, timestamps, and data volumes, malicious software can be identified. Using machine learning techniques, the authors \[[12](#ch23.xhtml#ref23_12), [13](#ch23.xhtml#ref23_13)\] created a behaviour testing approach to isolate `HTTP` and `HTTPs` network traffic, however they didn’t bother with any form of validation.

## Proposed Methodology

### A Proposed Network Traffic Model Based on Machine Learning
The proposed classification scheme is illustrated in [Figure 23.1](#ch23.xhtml#fig23_1). The primary goal of the proposed model is to use a machine learning approach to distinguish between legitimate and malicious `HTTPs`, `TCP`, and `IPv4-v6` network traffic.

![Figure 23.1 Workflow of the proposed approach](images/fig23_1_B.jpg)

[Figure 23.1 Workflow of the proposed approach](#ch23.xhtml#R_fig23_1)

### A. Capturing of Packets

During this stage, we faked harmful network activity and gathered malware samples. Specifically, we use a tool called `Wireshark` \[[14](#ch23.xhtml#ref23_14)\] to examine statistical characteristics of network traffic. The attributes like as IP addresses, ports, protocols, and timestamps are used to characterize flow duration.

### B. Categorization of Packets
