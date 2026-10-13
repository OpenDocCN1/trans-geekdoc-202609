
*   [SQL3] [American National](#ch02.xhtml#Cref2_16) Standards Institute [https://datacadamia.com/data/type/relation/sql/ansi](https://datacadamia.com)

*   [STON1974] [M. Stonebraker](#ch02.xhtml#Cref2_17), E. Wong, Access Control in a Relational Database Management System by Query Modification, *Proceedings of the ACM Annual Conference*, ACM Press, NY, 1974.

*   [THUR1987] [B. Thuraisingham](#ch02.xhtml#Cref2_18), Security Checking in Relational Database Management Systems Augmented with Inference Engines, Computers and Security, Volume 6, #6, 1987, 479–492.

*   [THUR1989] [B. Thuraisingham](#ch02.xhtml#Cref2_19), P. Stachour, SQL Extensions for Security Assertions, Computer Standards and Interface Journal, Volume 11, #1, 1989, 5–14.

*   [THUR1993] [B. Thuraisingham](#ch02.xhtml#Cref2_20), W. Ford, M. Collins, Design and Implementation of a Database Inference Controller, Data and Knowledge Engineering Journal, Volume 11, #3, 1993, 5–14.

*   [THUR1994] [B. Thuraisingham](#ch02.xhtml#Cref2_21), Security Issues for Federated Database Systems, Computers & Security, Volume 13, #6, 1994, 509–525.

*   [THUR1997] [B. Thuraisingham](#ch02.xhtml#Cref2_22), Data Management Systems: Evolution and Interoperation, CRC Press, Boca Raton, FL, 1997.

*   [THUR2005a] [B. Thuraisingham](#ch02.xhtml#Cref2_23), Database Security, Integrating Database Systems and Information Security, CRC Press, 2005.

*   [THUR2005b] [B.M. Thuraisingham](#ch02.xhtml#Cref2_24), Privacy Constraint Processing in a Privacy-enhanced Database Management System, Data & Knowledge Engineering, Volume 55, #2, 2005, 159–188.

*   [THUR2007] [B. Thuraisingham](#ch02.xhtml#Cref2_25), Building Trustworthy Semantic Webs, CRC Press, 2007.

*   [THUR2017] [B. Thuraisinghan](#ch02.xhtml#Cref2_26), P. Pallabi, M. Masud, L. Khan, Big Data Analytics with Applications in Insider Threat Detection CRC Press, 2017.

# 3 Data Mining and Security

DOI: [10.1201/9781003081845-5](https://doi.org/10.1201/9781003081845-5)

## 3.1 Introduction

Data mining (as well as machine learning) can be considered to be a key aspect of data science. We have used data mining and analytics techniques in several of our efforts for various applications such as intrusion detection systems and social media systems. For example, in our previous book [THUR2016](#ch03.xhtml#ref3_23) we discussed algorithms for location-based data mining that will extract the locations of the various social media (e.g., Twitter) users. These algorithms can be extended to extract other demographics data. Our prior research has also developed data mining tools for sentiment analysis as well as for cyber security applications. For example, in one of our previous books, we discuss data mining tools for malware detection [MASU2011](#ch03.xhtml#ref3_14). In this chapter, we provide some background information about general data mining techniques as well as their applications to cyber security so that the reader can have an understanding of the field. In addition, we will also discuss aspects of attacks to the data mining techniques as well as privacy considerations.

Data mining outcomes (also called tasks) include classification, clustering, forming associations as well as detecting anomalies. Our tools have mainly focused on classification as the outcome and we have developed classification tools. The classification problem is also referred to as supervised learning in which a set of labeled examples is learned by a model, and then a new example with unknown labels is presented to the model for prediction.

There are many prediction models that have been used such as Markov model, decision trees, artificial neural networks (ANN), support vector machines (SVM), association rule mining (ARM), among others. Each of these models has its strengths and weaknesses. However, there is a common weakness among all of these techniques, which is the inability to suit all applications. The reason that there is no such ideal or perfect classifier is that each of these techniques was initially designed to solve specific problems under certain assumptions.

In this chapter, we discuss the data mining techniques that have been commonly used. Specifically, we present the Markov model, SVM, ANN, ARM, the problem of multi-classification as well as image classification, which is an aspect of image mining. In our research and development, we have designed hybrid models to improve the prediction accuracy of data mining algorithms in various applications, namely, intrusion detection, social media analytics, WWW prediction and image classification [AWAD2009](#ch03.xhtml#ref3_4).

Data mining has many applications in security, including in national security (e.g., surveillance) as well as in cyber security (e.g., malware detection). The threats to national security include attacking buildings, destroying critical infrastructures such as power grids and telecommunication systems [BOLZ2005](#ch03.xhtml#ref3_6). Data mining techniques are being investigated to find out who the suspicious people are and who is capable of carrying out terrorist activities [THUR2003](#ch03.xhtml#ref3_20). Cyber security is involved with protecting the computer and network systems against corruption due to Trojan horses and viruses. Data mining is also being applied to provide solutions such as intrusion and malware detection and auditing [MASU2011](#ch03.xhtml#ref3_14). In this chapter, we will focus mainly on data mining for cyber security applications.

The organization of this chapter is as follows. In [Section 3.2](#ch03.xhtml#sec3_2), we provide an overview of data mining. We start with a discussion of data mining tasks in [Section 3.2.1](#ch03.xhtml#sec3_002_001) and then provide some details on data mining techniques that we have utilized in our work. Some of these techniques are also utilized in [Parts II](#part_02.xhtml#part2) and [III](#part_03.xhtml#part3) of our book (e.g., support vector machines, decision trees). In particular, we discuss various data mining techniques such as SVM, Markov models, ARM, and decision trees which will be described in [Sections 3.2.2](#ch03.xhtml#sec3_002_002) through [3.2.6](#ch03.xhtml#sec3_002_006). In [Section 3.3](#ch03.xhtml#sec3_3), we will discuss data mining for cyber security applications. In particular, we will discuss cyber threats and applications of data mining to detect such threats. Attacks to the data mining techniques as well as the privacy implications of data mining will be discussed in Section 3.3.4. [Section 3.4](#ch03.xhtml#sec3_4) summarizes this chapter. [Figure 3.1](#ch03.xhtml#fig3_1a) illustrates the concepts in this chapter.

![Figure 3.1 Data mining and security.](images/fig3_1.jpg)

[Figure 3.1 Data mining and security.](#ch03.xhtml#Ffig3_1)

## 3.2 Data Mining Techniques

### 3.2.1 Overview

Before we discuss data mining techniques, we provide an overview of some of the data mining tasks (also known as data mining outcomes). Then we will discuss the techniques. In general, data mining tasks can be grouped into two categories: predictive and descriptive. Predictive tasks essentially predict whether an item belongs to a class or not. Descriptive tasks, in general, extract patterns from the examples. One of the most prominent predictive tasks is classification. In some cases, other tasks such as anomaly detection can be reduced to a predictive task such as whether a particular situation is an anomaly or not. Descriptive tasks, in general, include making associations and forming clusters. Therefore, classification, anomaly detection, making associations, and forming clusters are also thought to be data mining tasks.
