![](mark_cov_9783110670646.png)

![epub-cover-image](mark_cov_9783110670646.png)

Quantum Machine Learning

De Gruyter Frontiers in Computational Intelligence

Edited by

Siddhartha Bhattacharyya 

Volume 6

# Quantum Machine Learning

Edited by

Siddhartha Bhattacharyya

Indrajit Pan

Ashish Mani

Sourav De

Elizabeth Behrman

Susanta Chakraborti

![](de-gruyter.png)

# 

ISBN 9783110670646

e-ISBN (PDF) 9783110670707

e-ISBN (EPUB) 9783110670721

Bibliographic information published by the Deutsche Nationalbibliothek

The Deutsche Nationalbibliothek lists this publication in the Deutsche Nationalbibliografie; detailed bibliographic data are available on the Internet at [http://dnb.dnb.de](http://dnb.dnb.de).

© 2020 Walter de Gruyter GmbH, Berlin/Boston  

# Übersicht

1.  
2.  [bodymatter](#bodymatter-001.xhtml)

# Contents

1.  [List of Contributors](#dedication.xhtml#d6288e184)
2.  [Preface](#dedication.xhtml#d6288e371)
3.  [Sandip Dey, Sourav De, Siddhartha Bhattacharyya 1 Introduction to quantum machine learning](#bodymatter-001.xhtml#d6288e470) 
    1.  [1.1 Quantum machine learning](#bodymatter-001.xhtml#d6288e614)
    2.  [1.2 Grover search algorithm](#bodymatter-001.xhtml#d6288e681)
    3.  [1.3 Quantum reinforcement learning](#bodymatter-001.xhtml#d6288e1096)
    4.  [1.4 Quantum annealing](#bodymatter-001.xhtml#d6288e1190)
    5.  [1.5 Quantum neural networks](#bodymatter-001.xhtml#d6288e1268)
    6.  [1.6 Conclusion](#bodymatter-001.xhtml#d6288e1318)
4.  [Bruce J. MacLennan 2 Topographic representation for quantum machine learning](#bodymatter-002.xhtml#d6288e1878) 
    1.  [2.1 Introduction](#bodymatter-002.xhtml#d6288e1989)
    2.  [2.2 Topographic representation in the brain](#bodymatter-002.xhtml#d6288e2032)
    3.  [2.3 Topographic basis maps](#bodymatter-002.xhtml#d6288e2218) 
        1.  [2.3.1 Bijections](#bodymatter-002.xhtml#d6288e2756)
        2.  [2.3.2 Non-surjective Injections](#bodymatter-002.xhtml#d6288e4279)
        3.  [2.3.3 Non-injective surjections](#bodymatter-002.xhtml#d6288e6586)
        4.  [2.3.4 Arbitrary functions](#bodymatter-002.xhtml#d6288e11993)
    4.  [2.4 Topographic qubit maps](#bodymatter-002.xhtml#d6288e16934) 
        1.  [2.4.1 Representation](#bodymatter-002.xhtml#d6288e16940)
        2.  [2.4.2 Unary functions](#bodymatter-002.xhtml#d6288e17549)
        3.  [2.4.3 Binary functions](#bodymatter-002.xhtml#d6288e21235)
    5.  [2.5 Conversions between representations](#bodymatter-002.xhtml#d6288e24613)
    6.  [2.6 Applications to quantum machine learning](#bodymatter-002.xhtml#d6288e25028)
    7.  [2.7 Conclusions](#bodymatter-002.xhtml#d6288e25194)
5.  [Ashish Mani, Siddhartha Bhattacharyya, Amlan Chatterjee 3 Quantum optimization for machine learning](#bodymatter-003.xhtml#d6288e25486) 
    1.  [3.1 Introduction](#bodymatter-003.xhtml#d6288e25639)
    2.  [3.2 Related work](#bodymatter-003.xhtml#d6288e25783)
    3.  [3.3 Adiabatic quantum computation](#bodymatter-003.xhtml#d6288e25921) 
        1.  [3.3.1 Oracle](#bodymatter-003.xhtml#d6288e27277)
    4.  [3.4 Grover’s adaptive search](#bodymatter-003.xhtml#d6288e27321)
    5.  [3.5 Problem formulation](#bodymatter-003.xhtml#d6288e28991)
    6.  [3.6 AQC based quantum search](#bodymatter-003.xhtml#d6288e29498)
    7.  [3.7 AQC based minimum searching algorithm](#bodymatter-003.xhtml#d6288e31645)
    8.  [3.8 Adiabatic quantum optimization algorithm](#bodymatter-003.xhtml#d6288e32460) 
        1.  [3.8.1 Discussions](#bodymatter-003.xhtml#d6288e32961)
    9.  [3.9 Conclusions](#bodymatter-003.xhtml#d6288e33048)
6.  [Arit Kumar Bishwas, Ashish Mani, Vasile Palade 4 From classical to quantum machine learning](#bodymatter-004.xhtml#d6288e33612) 
    1.  [4.1 Introduction](#bodymatter-004.xhtml#d6288e33756)
    2.  [4.2 Overview of quantum computing](#bodymatter-004.xhtml#d6288e33871) 
        1.  [4.2.1 Hilbert space & Dirac notation](#bodymatter-004.xhtml#d6288e33877)
        2.  [4.2.2 Quantum bits and gates](#bodymatter-004.xhtml#d6288e34427)
        3.  [4.2.3 Superposition](#bodymatter-004.xhtml#d6288e35232)
        4.  [4.2.4 Entanglement](#bodymatter-004.xhtml#d6288e35407)
        5.  [4.2.5 Quantum adiabatic model](#bodymatter-004.xhtml#d6288e36196)
        6.  [4.2.6 SWAP-test](#bodymatter-004.xhtml#d6288e36618)
        7.  [4.2.7 Quantum algorithms](#bodymatter-004.xhtml#d6288e36726)
    3.  [4.3 Essential foundations for building a quantum machine learning framework](#bodymatter-004.xhtml#d6288e36756) 
        1.  [4.3.1 Grover’s search algorithm](#bodymatter-004.xhtml#d6288e36768)
        2.  [4.3.2 Quantum random access memory](#bodymatter-004.xhtml#d6288e37056)
        3.  [4.3.3 Quantum dot product](#bodymatter-004.xhtml#d6288e37315)
        4.  [4.3.4 The HHL algorithm](#bodymatter-004.xhtml#d6288e38532)
        5.  [4.3.5 Quantum principal component analysis](#bodymatter-004.xhtml#d6288e39000)
    4.  [4.4 Quantum machine learning approaches](#bodymatter-004.xhtml#d6288e39251) 
        1.  [4.4.1 HHL or quantum amplitude based approaches](#bodymatter-004.xhtml#d6288e39257)
        2.  [4.4.2 Grover’s search-based approaches](#bodymatter-004.xhtml#d6288e39328)
        3.  [4.4.3 Quantum annealing based approaches](#bodymatter-004.xhtml#d6288e39350)
    5.  [4.5 Recent progress in quantum machine learning algorithms](#bodymatter-004.xhtml#d6288e39364) 
        1.  [4.5.1 Quantum binary least square support vector machine](#bodymatter-004.xhtml#d6288e39373)
        2.  [4.5.2 Quantum multiclass support vector machine](#bodymatter-004.xhtml#d6288e39773)
        3.  [4.5.3 Quantum K-means clustering](#bodymatter-004.xhtml#d6288e41304)
        4.  [4.5.4 Quantum deep learning](#bodymatter-004.xhtml#d6288e42857)
    6.  [4.6 Recent progress in the implementation of quantum machine learning](#bodymatter-004.xhtml#d6288e42886)
    7.  [4.7 Conclusion](#bodymatter-004.xhtml#d6288e42954)
7.  [Alokananda Dey, Sandip Dey, Siddhartha Bhattacharyya, Jan Platos, Vaclav Snasel 5 Quantum inspired automatic clustering algorithms: A comparative study of Genetic algorithm and Bat algorithm](#bodymatter-005.xhtml#d6288e43542) 
    1.  [5.1 Introduction](#bodymatter-005.xhtml#d6288e43737)
    2.  [5.2 Overview of Genetic algorithm](#bodymatter-005.xhtml#d6288e44369)
    3.  [5.3 Overview of Bat algorithm](#bodymatter-005.xhtml#d6288e44446)
    4.  [5.4 Fundamental idea of quantum computing](#bodymatter-005.xhtml#d6288e45746)
    5.  [5.5 Cluster validity index](#bodymatter-005.xhtml#d6288e46768)
    6.  [5.6 Quantum inspired Genetic algorithm](#bodymatter-005.xhtml#d6288e47409) 
        1.  [5.6.1 Proposed methodology for QIGA](#bodymatter-005.xhtml#d6288e47415)
    7.  [5.7 Quantum inspired Bat algorithm](#bodymatter-005.xhtml#d6288e50352) 
        1.  [5.7.1 Proposed methodology for QIBA](#bodymatter-005.xhtml#d6288e50358)
    8.  [5.8 Experiment and result analysis](#bodymatter-005.xhtml#d6288e54979) 
        1.  [5.8.1 Representation scheme of cluster centroids](#bodymatter-005.xhtml#d6288e54991)
        2.  [5.8.2 Experimental result analysis](#bodymatter-005.xhtml#d6288e55192)
        3.  [5.8.3 Simulation of work](#bodymatter-005.xhtml#d6288e57318)
        4.  [5.8.4 Dataset used](#bodymatter-005.xhtml#d6288e57517)
    9.  [5.9 Conclusion](#bodymatter-005.xhtml#d6288e57545)
8.  [Siddhartha Bhattacharyya 6 Conclusion](#bodymatter-006.xhtml#d6288e58002)
9.  [Index](#index.xhtml#d6288e58275)

1.  [V](#dedication.xhtml#page-V)
2.  [VI](#dedication.xhtml#page-VI)
3.  [IX](#dedication.xhtml#page-IX)
4.  [X](#dedication.xhtml#page-X)
5.  [XI](#dedication.xhtml#page-XI)
6.  [XII](#dedication.xhtml#page-XII)
7.  [XIII](#dedication.xhtml#page-XIII)
8.  [XIV](#dedication.xhtml#page-XIV)
9.  [1](#bodymatter-001.xhtml#page-1)
10.  [2](#bodymatter-001.xhtml#page-2)
11.  [3](#bodymatter-001.xhtml#page-3)
12.  [4](#bodymatter-001.xhtml#page-4)
13.  [5](#bodymatter-001.xhtml#page-5)
14.  [6](#bodymatter-001.xhtml#page-6)
15.  [7](#bodymatter-001.xhtml#page-7)
16.  [8](#bodymatter-001.xhtml#page-8)
17.  [9](#bodymatter-001.xhtml#page-9)
18.  [11](#bodymatter-002.xhtml#page-11)
19.  [12](#bodymatter-002.xhtml#page-12)
20.  [13](#bodymatter-002.xhtml#page-13)
21.  [14](#bodymatter-002.xhtml#page-14)
22.  [15](#bodymatter-002.xhtml#page-15)
23.  [16](#bodymatter-002.xhtml#page-16)
24.  [17](#bodymatter-002.xhtml#page-17)
25.  [18](#bodymatter-002.xhtml#page-18)
26.  [19](#bodymatter-002.xhtml#page-19)
27.  [20](#bodymatter-002.xhtml#page-20)
28.  [21](#bodymatter-002.xhtml#page-21)
29.  [22](#bodymatter-002.xhtml#page-22)
30.  [23](#bodymatter-002.xhtml#page-23)
31.  [24](#bodymatter-002.xhtml#page-24)
32.  [25](#bodymatter-002.xhtml#page-25)
33.  [26](#bodymatter-002.xhtml#page-26)
34.  [27](#bodymatter-002.xhtml#page-27)
35.  [28](#bodymatter-002.xhtml#page-28)
36.  [29](#bodymatter-002.xhtml#page-29)
37.  [30](#bodymatter-002.xhtml#page-30)
38.  [31](#bodymatter-002.xhtml#page-31)
39.  [32](#bodymatter-002.xhtml#page-32)
40.  [33](#bodymatter-002.xhtml#page-33)
41.  [34](#bodymatter-002.xhtml#page-34)
42.  [35](#bodymatter-002.xhtml#page-35)
43.  [36](#bodymatter-002.xhtml#page-36)
44.  [37](#bodymatter-002.xhtml#page-37)
45.  [39](#bodymatter-003.xhtml#page-39)
46.  [40](#bodymatter-003.xhtml#page-40)
47.  [41](#bodymatter-003.xhtml#page-41)
48.  [42](#bodymatter-003.xhtml#page-42)
49.  [43](#bodymatter-003.xhtml#page-43)
50.  [44](#bodymatter-003.xhtml#page-44)
51.  [45](#bodymatter-003.xhtml#page-45)
52.  [46](#bodymatter-003.xhtml#page-46)
53.  [47](#bodymatter-003.xhtml#page-47)
54.  [48](#bodymatter-003.xhtml#page-48)
55.  [49](#bodymatter-003.xhtml#page-49)
56.  [50](#bodymatter-003.xhtml#page-50)
57.  [51](#bodymatter-003.xhtml#page-51)
58.  [52](#bodymatter-003.xhtml#page-52)
59.  [53](#bodymatter-003.xhtml#page-53)
60.  [54](#bodymatter-003.xhtml#page-54)
61.  [55](#bodymatter-003.xhtml#page-55)
62.  [56](#bodymatter-003.xhtml#page-56)
63.  [57](#bodymatter-003.xhtml#page-57)
64.  [58](#bodymatter-003.xhtml#page-58)
65.  [59](#bodymatter-003.xhtml#page-59)
66.  [60](#bodymatter-003.xhtml#page-60)
67.  [61](#bodymatter-003.xhtml#page-61)
68.  [62](#bodymatter-003.xhtml#page-62)
69.  [63](#bodymatter-003.xhtml#page-63)
70.  [64](#bodymatter-003.xhtml#page-64)
71.  [65](#bodymatter-003.xhtml#page-65)
72.  [67](#bodymatter-004.xhtml#page-67)
73.  [68](#bodymatter-004.xhtml#page-68)
74.  [69](#bodymatter-004.xhtml#page-69)
75.  [70](#bodymatter-004.xhtml#page-70)
76.  [71](#bodymatter-004.xhtml#page-71)
77.  [72](#bodymatter-004.xhtml#page-72)
78.  [73](#bodymatter-004.xhtml#page-73)
79.  [74](#bodymatter-004.xhtml#page-74)
80.  [75](#bodymatter-004.xhtml#page-75)
81.  [76](#bodymatter-004.xhtml#page-76)
82.  [77](#bodymatter-004.xhtml#page-77)
83.  [78](#bodymatter-004.xhtml#page-78)
84.  [79](#bodymatter-004.xhtml#page-79)
85.  [80](#bodymatter-004.xhtml#page-80)
86.  [81](#bodymatter-004.xhtml#page-81)
87.  [82](#bodymatter-004.xhtml#page-82)
88.  [83](#bodymatter-004.xhtml#page-83)
89.  [84](#bodymatter-004.xhtml#page-84)
90.  [85](#bodymatter-004.xhtml#page-85)
91.  [86](#bodymatter-004.xhtml#page-86)
92.  [87](#bodymatter-004.xhtml#page-87)
93.  [89](#bodymatter-005.xhtml#page-89)
94.  [90](#bodymatter-005.xhtml#page-90)
95.  [91](#bodymatter-005.xhtml#page-91)
96.  [92](#bodymatter-005.xhtml#page-92)
97.  [93](#bodymatter-005.xhtml#page-93)
98.  [94](#bodymatter-005.xhtml#page-94)
99.  [95](#bodymatter-005.xhtml#page-95)
100.  [96](#bodymatter-005.xhtml#page-96)
101.  [97](#bodymatter-005.xhtml#page-97)
102.  [98](#bodymatter-005.xhtml#page-98)
103.  [99](#bodymatter-005.xhtml#page-99)
104.  [100](#bodymatter-005.xhtml#page-100)
105.  [101](#bodymatter-005.xhtml#page-101)
106.  [102](#bodymatter-005.xhtml#page-102)
107.  [103](#bodymatter-005.xhtml#page-103)
108.  [104](#bodymatter-005.xhtml#page-104)
109.  [105](#bodymatter-005.xhtml#page-105)
110.  [106](#bodymatter-005.xhtml#page-106)
111.  [107](#bodymatter-005.xhtml#page-107)
112.  [108](#bodymatter-005.xhtml#page-108)
113.  [109](#bodymatter-005.xhtml#page-109)
114.  [110](#bodymatter-005.xhtml#page-110)
115.  [111](#bodymatter-005.xhtml#page-111)
116.  [112](#bodymatter-005.xhtml#page-112)
117.  [113](#bodymatter-005.xhtml#page-113)
118.  [115](#bodymatter-006.xhtml#page-115)
119.  [116](#bodymatter-006.xhtml#page-116)
120.  [117](#index.xhtml#page-117)
121.  [118](#index.xhtml#page-118)

Siddhartha Bhattacharyya would like to dedicate this book to the memory of the deceased Jawans in Pulawama incident.

Indrajit Pan would like to dedicate this book to his research guides Prof. (Dr.) Hafizur Rahaman and Dr. Tuhina Samanta, who have always mentored him during his doctoral research.

Ashish Mani would like to dedicate this book to Most Revered Prof. Prem Saran Satsangi, Emeritus Chairman, Advisory Committee on Education, Dayalbagh Educational Institutions, India.

Sourav De would like to dedicate this book to his loving wife Debolina Ghosh and beloved son Aishik De.

Elizabeth Behrman would like to dedicate this book to EJB, JFB, and JPK; and to the memory of CFB.

Susanta Chakraborti would like to dedicate this book to his father Late Santosh Kr. Chakraborty.

# List of Contributors

**Siddhartha Bhattacharyya**

Department of Computer Science and Engineering

CHRIST (Deemed to be University)

Bangalore, India

[dr.siddhartha.bhattacharyya@gmail.com](mailto:dr.siddhartha.bhattacharyya@gmail.com)

**Arit Kumar Bishwas**

AIIT, Amity University, Noida

Uttar Pradesh, India

[aritkumar.official@gmail.com](mailto:aritkumar.official@gmail.com)

**Amlan Chatterjee**

Computer Science

California State University

Dominguez Hills, USA

[achatterjee@csudh.edu](mailto:achatterjee@csudh.edu)

**Sourav De**

Department of Computer Science and Engineering

Cooch Behar Government Engineering College

Cooch Behar, West Bengal, India

[dr.sourav.de79@gmail.com](mailto:dr.sourav.de79@gmail.com)

**Alokananda Dey**

RCC Institute of Information Technology

Kolkata, West Bengal, India

[alokananda\_22@yahoo.co.in](mailto:alokananda_22@yahoo.co.in)

**Sandip Dey**

Department of Computer Science

Sukanta Mahavidyalaya, Sukanta Nagar

Dhupguri, Jalpaiguri, West Bengal, India

[dr.ssandip.dey@gmail.com](mailto:dr.ssandip.dey@gmail.com)

**Bruce J. MacLennan**

University of Tennessee, Knoxville

Tennessee, USA

[maclennan@utk.edu](mailto:maclennan@utk.edu)

**Ashish Mani**

ASET, Amity University UP

Noida, Uttar Pradesh, India

[amani@amity.edu](mailto:amani@amity.edu)

**Vasile Palade**

Faculty of Engineering and Computing Coventry University

Coventry, United Kingdom

[vasile.palade@coventry.ac.uk](mailto:vasile.palade@coventry.ac.uk)

**Jan Platos**

VSB Technical University of Ostrava

Czech Republic

[jan.platos@vsb.cz](mailto:jan.platos@vsb.cz)

**Vaclav Snasel**

VSB Technical University of Ostrava

Czech Republic

[vaclav.snasel@vsb.cz](mailto:vaclav.snasel@vsb.cz)

# Preface

Imparting intelligence to the machines has always been a challenging thoroughfare. Over the years, several intelligent tools have been invented or proposed to deal with the uncertainties encountered by human beings with the advent of the soft computing paradigm. However, it has been observed that even the soft computing tools often fall short in offering a reliable and reasonable solution in real time. Hence, scientists employed hybrid intelligent techniques using the combination of several soft computing tools to overcome the shortcomings.

Quantum computing has evolved from the studies of Feynman and Deutsche who evolved efficient searching techniques in the quantum domain. These searching techniques outperform the classical techniques both in terms of time and space. Inspired by this, researchers are on the spree for conjoining the existing soft computing tools with the quantum computing paradigm to evolve more robust and time efficient intelligent algorithms. The resultant algorithms are immensely useful for solving several scientific and engineering problems, which includes data processing and analysis, machine vision, social networks, big data analytics, flow shop scheduling problems to name a few.

Quantum machine learning is an emerging interdisciplinary research area which resorts to the principles of quantum physics applied to machine learning. Quantum machine learning algorithms helps to improve classical methods of machine learning by taking the advantages offered by quantum computation. Given the inherent parallelism offered due to the features of quantum computing, researchers have evolved different intelligent tools and techniques which are more robust and efficient in performance.

Quantum-enhanced machine learning refers to quantum algorithms that solve tasks in machine learning, thereby improving a classical machine learning method. Such algorithms typically require one to encode the given classical dataset into a quantum computer, so as to make it accessible for quantum information processing. After this, quantum information processing routines can be applied and the result of the quantum computation is read out by measuring the quantum system. For example, the outcome of the measurement of a qubit could reveal the result of a binary classification task. While many proposals of quantum machine learning algorithms are still purely theoretical and require a full-scale universal quantum computer to be tested, others have been implemented on small-scale or special purpose quantum devices.

This book comprises six well versed chapters from leading quantum machine learning researchers.

Chapter 1 provides an overview of the basic concepts and principles pertaining to quantum machine learning. Apart from throwing light on different aspects of quantum algorithms, the chapter also provides a bird’s eye view on the principles of quantum reinforcement learning and quantum annealing. The evolution of quantum neural networks with special mention to the pioneering works in this direction is also touched upon to enlighten the readers.

One of the most common information representations in the brain is the topographic or computational map, in which neurons are arranged systematically according to the values they represent. By representing quantitative relationships spatially, computational maps enable the brain to compute complex, nonlinear functions to the accuracy required. Chapter 2 proposes two approaches to quantum computation for machine learning by means of topographic representation. It shows how to construct unitary operators, implementable on quantum computers, that implement arbitrary (including nonlinear) functions via computational maps.

Training in machine learning techniques often requires solving a difficult optimization problem, which is the most expensive step in the entire mode-building process and its applications. One of the possible solutions in near future for reducing execution time of training process in Machine learning techniques is to implement them on quantum computers instead of classical computers. Chapter 3 discusses a global optimization technique based on Adiabatic Quantum Computation (AQC) to solve minimization of loss function without any restriction on its structure and the underlying model, which is being learned. Further, it is also shown that in the proposed framework AQC based approach would be superior to circuit-based approach in solving global optimization problems.

In Chapter 4, the authors discuss the transition from classical machine learning to quantum machine learning (QML) and explore the recent progress in this domain. QML is not only associated with the development of high-performance machine learning algorithms that can run on a quantum computer with significant performance improvements but also has a very diverse meaning in other aspects. The chapter tries to touch those aspects in brief too, but the main focus is on the advancements in the field of developing machine learning algorithms that will run on a quantum computer.

Chapter 5 is intended to present two automatic clustering techniques of image datasets, based on quantum inspired framework with two different meta-heuristic algorithms, viz., Genetic Algorithm (GA) and Bat Algorithm (BA). This work provides two novel techniques to automatically identify the optimal number of clusters present in an image dataset and also provides a comparative study between the Quantum Inspired Genetic Algorithm (QIGA) and Quantum Inspired Bat Algorithm (QIBA). A comparison is also presented between this quantum inspired algorithms with their classical counterparts. During the experiment, it is observed that the quantum inspired techniques outperform over their classical counterparts. The comparison is prepared based on the mean values of the fitness, standard deviation, standard error of the computed fitness of the cluster validity index and the optimal computational time. Finally, the superiority of the algorithms is verified in terms of the p-value which was computed from the statistical superiority test (t-test) and ranking of the proposed procedures was produced by the Friedman test. During the computation, the betterment of the fitness was judge by a well-known cluster validity index, named, DB index. The experiments are carried out on four Berkeley image and two real life grey scale image datasets.

Chapter 6 draws a line of conclusion discussing the achievable from the book. The chapter also throws light on the future trends of quantum machine learning involving multilevel quantum systems.

The editors feel that this book would come in good stead to the undergraduate and postgraduate students of computer science, information science and electronics engineering for a part of their curricula. The editors would also like to take this opportunity to render their heartfelt gratitude to De Gruyter publishing house for consenting to publish this book.

Bangalore, Kolkata, New Delhi, Kansas

November, 2019

Siddhartha Bhattacharyya

Indrajit Pan

Ashish Mani

Sourav De

Elizabeth Behrman

Susanta Chakrabarti

# 1 Introduction to quantum machine learning

Sandip Dey Department of Computer Science, Sukanta Mahavidyalaya, Jalpaiguri, West Bengal, India Sourav De Department of Computer Science & Engineering, Cooch Behar Government Engineering College, Cooch Behar, West Bengal, India Siddhartha Bhattacharyya CHRIST (Deemed to be University), Department of Computer Science and Engineering, CHRIST (Deemed to be University), Bangalore, India, Hosur Road, 560029, Kolkata, Bangalore, Karnataka, India 

#### Abstract

Quantum Machine Learning (QML) is popularly known to be an integrative approach to learning of the Quantum Physics (QP) and Machine Learning (ML). In this chapter, an outline of the fundamental ideas and features related to quantum machine learning is laid out. The different facets of quantum algorithms are discussed in this chapter. In addition to this, the basic features of quantum reinforcement learning and quantum annealing are also provided in this chapter. Finally, the chapter deliberates about the advancement of quantum neural networks to through light in the direction of QML.

Keywords:  machine learning,  Grover’s Search Algorithm,  reinforcement learning,  quantum annealing,  quantum neural networks,  

## 1.1 Quantum machine learning

Machine learning has become an emerging discipline in the recent technologies. It can be used in a variety of fields, such as computational biology, computer vision, computer security and many others. Data analysis (DA) is an equally important part in the modern industry. The ML and DA analyze data by applying statistical methods and they provide computers learning capabilities on the basis of the analysis of observed data. On the basis of learning style, Machine learning algorithms (MAA) are basically classified into different groups, viz., supervised learning (SL), unsupervised learning (UL) and semi-supervised learning (SSL). The foremost shortcomings of using ML techniques are generally known to be computational time and storage, especially which involve bulky amounts of data. In addition to these, when the current deep learning algorithms are used, the training time can turn out to be even longer. In the subsequent generation, researchers got a viable alternative by utilizing the power of quantum computers method which can be smarter enough to reduce the storage and computational time as mentioned above.

Many ML problems use linear algebra to figure out matrix operations by expressing the data in matrices. Quantum computing (QC) is able to make several linear algebra computations more fast, which unreservedly improve classical ML tasks \[[1](#bodymatter-001.xhtml#b_9783110670707-001_ref_001), [2](#bodymatter-001.xhtml#b_9783110670707-001_ref_002)\]. Numerical methods for optimization are well admired field of research, which intend to improve the computations of the said optimization procedures. Like classical optimization, quantum optimization, a branch of QC, attempts to improve the said techniques even further. Two renowned methods of this kind are Quantum Gradient Descent (QGD) \[[3](#bodymatter-001.xhtml#b_9783110670707-001_ref_003)\] and Quantum Approximate Optimization Algorithm (QAOA) \[[4](#bodymatter-001.xhtml#b_9783110670707-001_ref_004)\]. These methods are efficiently applied in quantum neural networks (QNN) like Quantum Boltzman Machines \[[5](#bodymatter-001.xhtml#b_9783110670707-001_ref_005)\].

Of late, the quantum machine learning, a very new field of emerging inter-disciplinary research area, has come out, with the objective of coalescing the theory of machine learning with the properties of quantum computing. Quantum machine learning (QML) is intended for implementing machine learning algorithms (MLLs) in quantum atmosphere (systems) \[[6](#bodymatter-001.xhtml#b_9783110670707-001_ref_006)\], by applying quantum features such as quantum superposition and quantum entanglement for solving different problems with high efficacy. Basically, QML is known to be a sub-discipline of quantum research of information processing, with the objective of introducing quantum algorithms that generally learn from data with the aim of improving existing approaches in ML. Hence, the purpose is to develop quantum applications of various MLLs, having the influence of quantum computers as well as the flexibility and learning ability of MLLs.

Several quantum algorithms have been introduced for a variety of machine learning models which include neural networks (NN), graphical models, support vector machines (SVM) so on and so forth. QML explores more basic questions about the thought of learning from the quantum perspective. In some occasions, the QML is extensively defined by researchers to apply ML to quantum information.

Besides the implicit methodologies used in QML, there exists few quantum versions of classical ML algorithms. Quantum Support Vector Machines (QSVM) \[[1](#bodymatter-001.xhtml#b_9783110670707-001_ref_001)\], which is basically applied for linear classification, is a popular example of this type. In addition to that, Quantum Principle Component Analysis (QPCA) \[[7](#bodymatter-001.xhtml#b_9783110670707-001_ref_007)\], a popular approach for dimensionality reduction, Quantum Guassian Mixture Models \[[8](#bodymatter-001.xhtml#b_9783110670707-001_ref_008)\], another renowned approach for estimating clustering and density. An emerging sub-discipline of ML is called Deep Learning (DL). These days, quantum computers are employed for DL applications, which involve significant storage and time. Some popular examples of these applications are Quantum Boltzmann Machines \[[5](#bodymatter-001.xhtml#b_9783110670707-001_ref_005)\], Quantum Generative Adversarial Networks \[[9](#bodymatter-001.xhtml#b_9783110670707-001_ref_009)\], Quantum Convolutional Neural Networks \[[10](#bodymatter-001.xhtml#b_9783110670707-001_ref_010)\] and Quantum Variational Autoencoders \[[11](#bodymatter-001.xhtml#b_9783110670707-001_ref_011)\]. Additionally, a more enlightened field inside ML is known as Reinforcement Learning (RL). RL can be described as learning as time continues by exploring the environment.

## 1.2 Grover search algorithm

Grover’s Search Algorithm (GAA) is a very popular quantum search algorithm \[[12](#bodymatter-001.xhtml#b_9783110670707-001_ref_012)\]. This algorithm finds a group of elements which satisfy a certain condition. For performing this task, a black box, usually known as an oracle, having the capability of identifying the elements, must satisfy the criteria that are required to find. Let us suppose that the group has *N* elements, the oracle is called *O(M)* times for classical computations to get all elements that satisfy the above-mentioned criteria. Using quantum mechanics, this algorithm is able to attain the same result by using $O(\\sqrt{M)}$ calls to the oracle.

The algorithm has the capability to make several calls to the oracle simultaneously by exploiting a special feature of quantum computing, called parallel processing. Let us assume that a search list has *N* number of elements. GAA uses a Hilbert space of dimension *N* to represent them, which can be achieved with *n = logM (base 2) qubits*. Each *el*∈*N* with index *y* is denoted by an orthonormal vector, called |*y*⟩ in the qubits’s state space. The objective is to identify the index *z of* that particular element satisfying the given search criteria.

At the outset, the oracle is being employed, in which a unitary operation having features given by

(1.1a)1.  *i**f* *y* = *z*, *U*[*z*]|*y*⟩=−|*y*⟩ (1.1b)2.  *i**f* *y* ≠ *z*, *U*[*z*]|*y*⟩=|*y*⟩ 

The [eqs. (1.1a)](#bodymatter-001.xhtml#b_9783110670707-001_eq_001) and [(1.1b)](#bodymatter-001.xhtml#b_9783110670707-001_eq_001) can also be expressed as follows:

(1.2)*U*[*z*] = *I* − 2|*z*⟩⟨*z*| 

where, *I* denotes the identity operator. The GAA simultaneously uses the last oracle operator and the Grover diffusion operators, as defined by

(1.3)*U*[*p*] = 2|*p*⟩⟨*p*| − *I* 

where, $|p\\rangle = \\frac{1}{\\sqrt{N}}\\sum\_{y = 1}^{N}y$. The [eq. (1.2)](#bodymatter-001.xhtml#b_9783110670707-001_eq_002) and [(1.3)](#bodymatter-001.xhtml#b_9783110670707-001_eq_003) are utilized as follows.

At initial, the qubits’ state is being initialized to the |*p*⟩ state. Thereafter, *U*[*z*] and *U*[*p*] are successively applied iteratively for *r(N)* number of times. Afterwards, the system is assessed, which provides the eigenvalue (*λ*[*z*]), which may conclude the said index (*z*).

## 1.3 Quantum reinforcement learning

Besides supervised and unsupervised learning, reinforcement learning (RL) is also a popular category of learning method. In contrast to SL and UL, RL employs a scalar value called reward to assess the input-output pairs and uses the policy of trial-and error to interact with the environment for learning a mapping from states to actions. Since the year of 1980, RL has gradually become a significant approach to ML \[[5](#bodymatter-001.xhtml#b_9783110670707-001_ref_005)\]. So far, it has been extensively applied in artificial intelligence (AI), particularly in robotics \[[13](#bodymatter-001.xhtml#b_9783110670707-001_ref_013), [14](#bodymatter-001.xhtml#b_9783110670707-001_ref_014), [15](#bodymatter-001.xhtml#b_9783110670707-001_ref_015), [16](#bodymatter-001.xhtml#b_9783110670707-001_ref_016), [17](#bodymatter-001.xhtml#b_9783110670707-001_ref_017)\]. It is due to the fact that it shows an excellent performance in on-line adaptation, and in addition, it has a prevailing learning ability to any complex nonlinear systems.

There may have some complicated problems while dealing with practical applications, such as the exploration strategy, slow learning speed; in particular handling complex problems. It can be observed, especially whilst the state-action space grows to be gigantic and the number of parameters that are to be learned grows up exponentially with the increase of dimension. So far, several methods have been introduced in the recent years to combat this situation.

Different learning paradigms are united for optimizing RL. Smith \[[18](#bodymatter-001.xhtml#b_9783110670707-001_ref_018)\] proposed a novel model to represent and generalize in model-less RL on the basis of self-organizing map (SOM) and benchmark Q-learning. In addition, for the sake of adaptation of fuzzy inference systems with Watkins’ Q-learning for problems having large/continuous state-action spaces is also presented \[[17](#bodymatter-001.xhtml#b_9783110670707-001_ref_017), [19](#bodymatter-001.xhtml#b_9783110670707-001_ref_019), [20](#bodymatter-001.xhtml#b_9783110670707-001_ref_020)\]. Different RL methods have been improved in practice \[[21](#bodymatter-001.xhtml#b_9783110670707-001_ref_021), [22](#bodymatter-001.xhtml#b_9783110670707-001_ref_022), [23](#bodymatter-001.xhtml#b_9783110670707-001_ref_023), [24](#bodymatter-001.xhtml#b_9783110670707-001_ref_024)\].

Two significant quantum algorithms, called the Shor algorithm \[[25](#bodymatter-001.xhtml#b_9783110670707-001_ref_025), [26](#bodymatter-001.xhtml#b_9783110670707-001_ref_026)\] and the Grover algorithm \[[27](#bodymatter-001.xhtml#b_9783110670707-001_ref_027), [28](#bodymatter-001.xhtml#b_9783110670707-001_ref_028)\], have been introduced. Rigatos and Tzafestas \[[29](#bodymatter-001.xhtml#b_9783110670707-001_ref_029)\] applied the theory of quantum computing to get the benefit of parallelization of fuzzy-logic control algorithm (FCA), whose objective is to speed up the fuzzy inference. Quantum-inspired evolutionary algorithms (QIEA) have been developed to enhance the performance of the existing evolutionary algorithms (EA) \[[30](#bodymatter-001.xhtml#b_9783110670707-001_ref_030)\]. Later, Hogg and Portnov \[[31](#bodymatter-001.xhtml#b_9783110670707-001_ref_031)\] introduced a quantum algorithm to solve combinatorial optimization problem having over constrained satisfiability and asymmetric traveling salesman. In recent times, the quantum search method has been applied to dynamic programming \[[32](#bodymatter-001.xhtml#b_9783110670707-001_ref_032)\]. Taking into account the spirit of computation, Dong et al. \[[33](#bodymatter-001.xhtml#b_9783110670707-001_ref_033)\] have developed the concept of Quantum Reinforcement Learning (QRL) inspired by the basic concept of quantum computing, called state superposition principle and parallelism. QRL was developed to speed-up learning and attaining a trade-off between exploitation and exploration of RL in the course of simulated experiments.

## 1.4 Quantum annealing

In statistical mechanics, quantum annealing (QA) that is applied in the field of quantum-mechanical fluctuations is the quantum version of the simulated annealing (SA) \[[34](#bodymatter-001.xhtml#b_9783110670707-001_ref_034), [35](#bodymatter-001.xhtml#b_9783110670707-001_ref_035)\]. It is also known as Quantum Stochastic Optimization algorithm. Like the SA, quantum annealing is also successfully applied to solve the hard optimization problem. It works on the principal of the quantum adiabatic evolution in the active field of the quantum computation and it is a profitable hybridization between classical and quantum technology. QA is applied in different fields as computer science \[[36](#bodymatter-001.xhtml#b_9783110670707-001_ref_036)\], machine learning \[[37](#bodymatter-001.xhtml#b_9783110670707-001_ref_037), [38](#bodymatter-001.xhtml#b_9783110670707-001_ref_038)\], graph theory \[[39](#bodymatter-001.xhtml#b_9783110670707-001_ref_039)\], communications \[[40](#bodymatter-001.xhtml#b_9783110670707-001_ref_040), [41](#bodymatter-001.xhtml#b_9783110670707-001_ref_041), [42](#bodymatter-001.xhtml#b_9783110670707-001_ref_042)\], finance \[[43](#bodymatter-001.xhtml#b_9783110670707-001_ref_043)\], aeronautics \[[44](#bodymatter-001.xhtml#b_9783110670707-001_ref_044)\] and any others real world problems.

In simulated annealing \[[45](#bodymatter-001.xhtml#b_9783110670707-001_ref_045)\], a temperature dependent random walk of a statistical-mechanical system is employed as the cost function of a given optimization problem. This function determines the potential energy profile of the solution space and thermal fluctuations avoid that the exploration gets stuck in a local minimum \[[46](#bodymatter-001.xhtml#b_9783110670707-001_ref_046)\]. It is expected that the system will stay close to thermal equilibrium during time evolution. It can happen if the rate of decrease of temperature is sufficiently slow, and thus lead in the end to the zero-temperature equilibrium state, the lowest-energy state \[[47](#bodymatter-001.xhtml#b_9783110670707-001_ref_047)\]. Due to the general applicability, reasonable performance, and relatively easy implementation in most cases, SA is employed effectively in many real life applications. When a problem requires an infinitely long time to derive the exact solution by keeping the system close to thermal equilibrium, SA is applied to obtain the approximate solution within a measurable computation time. The quantum fluctuations are induced in QA by introducing artificial degrees of quantum nature, non-commutative operators. The strength of the quantum fluctuations are controlled to reach the ground state by slowly reducing the temperature.

Like the finding the minimization of a cost function of a optimization problem, it can be considered as finding the ground state of a classical Ising Hamiltonian H0 \[[48](#bodymatter-001.xhtml#b_9783110670707-001_ref_048)\]. Different types of practical problems have cost functions with large number of local minima. Similarly, Ising Hamiltonians are remindful of classical spin glasses \[[49](#bodymatter-001.xhtml#b_9783110670707-001_ref_049), [50](#bodymatter-001.xhtml#b_9783110670707-001_ref_050)\]. For these types of characteristics, it is very tough to find the global minima for classical algorithms. This problem can be overcame with the idea to elevate the classical Ising Hamiltonian H0 to the quantum domain. Based on the adiabatic theorem of quantum mechanics, the ground state of the classical Ising model can be derived by formatting the system in the ground state of some initial Hamiltonian H1 \[[51](#bodymatter-001.xhtml#b_9783110670707-001_ref_051), [52](#bodymatter-001.xhtml#b_9783110670707-001_ref_052)\]. It is easy to develop both theoretically and experimentally. H1 is selected in such a way it does not exchange with H0. The Hamiltonian changes gradually from H1 to H0 as the system parameters modified sufficiently slowly.

## 1.5 Quantum neural networks

Quantum neural networks (QNNs) are incarnations of neural network models entailing the principles of quantum mechanics. From the computational point of view \[[53](#bodymatter-001.xhtml#b_9783110670707-001_ref_053), [54](#bodymatter-001.xhtml#b_9783110670707-001_ref_054)\], one class of quantum neural network combine artificial neural network models and embed the features of quantum computing inside to evolve more robust and efficient models. The basic philosophy behind these efforts is to circumvent the limitations of classical neural networks in handling big data by resorting to the features of quantum parallelism, interference and entanglement. However, most of the QNN models try to replace the classical binary or the McCulloch-Pitts neurons with qubits (also called “qurons”) manifested with quantum mechanical principles.

In 1995, Subhash Kak \[[55](#bodymatter-001.xhtml#b_9783110670707-001_ref_055)\] and Ron Chrisley \[[56](#bodymatter-001.xhtml#b_9783110670707-001_ref_056)\] put forward the idea of a quantum neural model by establishing the similarity of the neural activation function with the quantum mechanical Eigenvalue equation. Ajit Narayanan and Tammy Menneer introduced a photonic implementation of a quantum neural network using the many-universe theory which collapses into the desired states on application of quantum measurement \[[57](#bodymatter-001.xhtml#b_9783110670707-001_ref_057)\]. Since then, a lot of efforts have been invested to find the quantum version of the perceptron. However, the advances in this direction was impeded due to the fact that the characteristic neural nonlinear activation functions seldom follow the mathematical structure of quantum theory due to the inherent linear operations in a quantum system. After much effort, Schuld, Sinayskiy and Petruccione used the quantum phase estimation algorithm \[[58](#bodymatter-001.xhtml#b_9783110670707-001_ref_058)\] to implement the activation function. Apart from this, lots of quantum-inspired models have come up to implement a fuzzy logic based neural network \[[59](#bodymatter-001.xhtml#b_9783110670707-001_ref_059)\].

Elizabeth Behrman and Jim Steck \[[60](#bodymatter-001.xhtml#b_9783110670707-001_ref_060)\] proposed a novel quantum computing setup comprising a number of qubits with tunable mutual interactions. In their model, the interaction strengths are updated using a training set of desired input-output relations following the classical back-propagation algorithm thereby enabling the quantum network to learn an algorithm.

The quantum associative memory was introduced by Dan Ventura and Tony Martinez in 1999 \[[61](#bodymatter-001.xhtml#b_9783110670707-001_ref_061)\]. The authors proposed an algorithm to emulate an associative memory for a circuit-based quantum computer. In this algorithm, the memory states are envisaged as a superposition of quantum states. A quantum search algorithm is then used to retrieve the memory state closest to a given input. This emulation promises an exponential storage capacity of memory states.

## 1.6 Conclusion

This chapter provides an overview of the basic concepts and principles pertaining to quantum machine learning. Apart from throwing light on different aspects of quantum algorithms, the chapter also provides a bird’s eye view on the principles of quantum reinforcement learning and quantum annealing. The evolution of quantum neural networks with special mention to the pioneering works in this direction is also touched upon to enlighten the readers.

## References

\[1\]Harrow, A. W., Hassidim, A., & Lloyd, S. Quantum algorithm for solving linear systems of equations. Physical review letters. 2009, 15(103), 150502. [a](#bodymatter-001.xhtml#xref_d6256e645), [b](#bodymatter-001.xhtml#xref_d6256e673)

\[2\]Rebentrost, P., Mohseni, M., & Lloyd, S. Quantum support vector machine for big data classification. Physical review letters. 2014, 113(13), p. 130503. [→](#bodymatter-001.xhtml#xref_d6256e648)

\[3\]Kerenidis, I., & Prakash, A. Quantum gradient descent for linear systems and least squares. 2017. arXiv:1704.04992 \[quant-ph\]. [→](#bodymatter-001.xhtml#xref_d6256e651)

\[4\]Farhi, E., Goldstone, J., & and Gutmann, S. A quantum approximate optimization algorithm. 2014. arXiv:1411.4028 \[quant-ph\]. [→](#bodymatter-001.xhtml#xref_d6256e654)

\[5\]Amin, M. H., Andriyash, E., Rolfe, J., Kulchytskyy, B., & Melko, R. Quantum boltzmann machine. Physical review letters. 2018, 8, 021050. [a](#bodymatter-001.xhtml#xref_d6256e657), [b](#bodymatter-001.xhtml#xref_d6256e682), [c](#bodymatter-001.xhtml#xref_d6256e1161)

\[6\]Schuld, M., Sinayskiy, I., & Petruccione, F. An introduction to quantum machine learning. Contemporary Physics. 2015, 56(2),172–185. [→](#bodymatter-001.xhtml#xref_d6256e663)

\[7\]Lloyd, S., Mohseni, M., & Rebentrost, P. Quantum principal component analysis. Nature Physics. 2014, 10(9),631–633. [→](#bodymatter-001.xhtml#xref_d6256e676)

\[8\]Rahman M., & and Geiger, D. Quantum clustering and gaussian mixtures. 2016. arXiv:1612.09199v1 \[stat.ML\]. [→](#bodymatter-001.xhtml#xref_d6256e679)

\[9\]Lloyd, S., & Weedbrook, C. Quantum generative adversarial learning. Physical review letters, 2018, 040502. [→](#bodymatter-001.xhtml#xref_d6256e685)

\[10\]Cong, I., Choi, S., & Lukin, M. D. Quantum convolutional neural networks. 2018. arXiv:1810.03787v1 \[quant-ph\]. [→](#bodymatter-001.xhtml#xref_d6256e689)

\[11\]Khoshaman, A., Vinci, W., Denis, B., Andriyash, E., & Amin, M. H. Quantum variational autoencoder. 2018. arXiv:1802.05779v1 \[quant-ph\]. [→](#bodymatter-001.xhtml#xref_d6256e692)

\[12\]Lavor, C., Manssur, L. R. U., & Portugal, R. Grover’s Algorithm: Quantum Database Search. 2003. arXiv:quant-ph/0301079. [→](#bodymatter-001.xhtml#xref_d6256e709)

\[13\]Beom, H. R., & Cho, H. S. A sensor-based navigation for a mobile robot using fuzzy logic and reinforcement learning. IEEE Transactions on Systems, Man, and Cybernetics. 1995, 25(3),464–477. [→](#bodymatter-001.xhtml#xref_d6256e1164)

\[14\]Connolly, C. I. Harmonic functions and collision probabilities. Int. J. Rob. Res. 1997, 16(4),497–507. [→](#bodymatter-001.xhtml#xref_d6256e1167)

\[15\]Smart, W. D., & Kaelbling, L. P. Effective reinforcement learning for mobile robots. Proceedings – IEEE International Conference on Robotics and Automation. 2002, 3404–3410. [→](#bodymatter-001.xhtml#xref_d6256e1170)

\[16\]Kondo,T., & Ito, K. A reinforcement learning with evolutionary state recruitment strategy for autonomous mobile robots control. Robotics and Autonomous Systems. 2004, 46(2),111–124. [→](#bodymatter-001.xhtml#xref_d6256e1174)

\[17\]Tzafestas, S. G., & Rigatos, G. G. Fuzzy reinforcement learning control for compliance tasks of robotic manipulators. IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics). 2002, 32(1),107–113. [a](#bodymatter-001.xhtml#xref_d6256e1177), [b](#bodymatter-001.xhtml#xref_d6256e1189)

\[18\]Smith, A. J. Applications of the self-organising map to reinforcement learning. Neural Netw. 2002, 15(8/9), 1107–1124. [→](#bodymatter-001.xhtml#xref_d6256e1186)

\[19\]Glorennec, P. Y, & Jouffe, L. Fuzzy Q-learning. Proceedings of 6th International Fuzzy Systems Conference. 1997, 659–662. [→](#bodymatter-001.xhtml#xref_d6256e1192)

\[20\]Er, M. J, & Deng, C. Online tuning of fuzzy inference systems using dynamic fuzzy Q-learning. IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics). 2004, 34(3),1478–1489. [→](#bodymatter-001.xhtml#xref_d6256e1195)

\[21\]Chen, C. L., Li, H. X., & Dong, D. Y. Hybrid control for Robot Navigation: A hierarchical Q-learning algorithm. IEEE Robotics & Automation Magazine. 2008, 15(2),37–47. [→](#bodymatter-001.xhtml#xref_d6256e1198)

\[22\]Whiteson, S., & Stone, P. Evolutionary function approximation for reinforcement learning. Journal of Machine Learning Research. 2006, 7, 877–917. [→](#bodymatter-001.xhtml#xref_d6256e1202)

\[23\]Kaya, M., & Alhajj, R. A novel approach to multiagent reinforcement learning: Utilizing OLAP mining in the learning process. IEEE Transactions on Systems, Man, and Cybernetics, Part C (Applications and Reviews). 2005, 35(4),582–590. [→](#bodymatter-001.xhtml#xref_d6256e1205)

\[24\]Vengerov, D., Bambos, N., & Berenji, H. A fuzzy reinforcement learning approach to power control in wireless transmitters IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics). 2005, 35(4),768–778. [→](#bodymatter-001.xhtml#xref_d6256e1208)

\[25\]Shor, P. W. Algorithms for quantum computation: Discrete logarithms and factoring. Proceedings 35th Annual Symposium on Foundations of Computer Science. 1994, 124–134. [→](#bodymatter-001.xhtml#xref_d6256e1215)

\[26\]Ekert, A., Jozsa, R. Quantum computation and Shor’s factoring algorithm. Rev. Mod. Phys. 1996, 68(3),733–753. [→](#bodymatter-001.xhtml#xref_d6256e1218)

\[27\]Grover, L. K. A fast quantum mechanical algorithm for database search. Proceedings of the twenty-eighth annual ACM symposium on Theory of Computing. 1996, 212–219. [→](#bodymatter-001.xhtml#xref_d6256e1221)

\[28\]Grover, L. K. Quantum mechanics helps in searching for a needle in a haystack. Phys. Rev. Lett. 1997, 79(2),325–327. [→](#bodymatter-001.xhtml#xref_d6256e1224)

\[29\]Rigatos, G. G., & Tzafestas, S. G. Parallelization of a fuzzy control algorithm using quantum computation. IEEE Trans. Fuzzy Syst. 2002, 10(4),451–460. [→](#bodymatter-001.xhtml#xref_d6256e1227)

\[30\]Sahin, M., Atav, U., & Tomak, M. Quantum genetic algorithm method in self-consistent electronic structure calculations of a quantum dot with many electrons International Journal of Modern Physics C. 2005, 16(9),1379–1393. [→](#bodymatter-001.xhtml#xref_d6256e1231)

\[31\]Hogg, T., & Portnov, D. Quantum optimization. Information Sciences. 2000, 128(3),81–197. [→](#bodymatter-001.xhtml#xref_d6256e1234)

\[32\]Naguleswaran, S., White, L., & Fuss, I. Quantum search in stochastic planning. Proceedings of the Sixteenth International Conference on Automated Planning and Scheduling. 2005, 34–45. [→](#bodymatter-001.xhtml#xref_d6256e1237)

\[33\]Dong, D. Y., Chen, C. L., & Chen, Z. H. Quantum reinforcement learning. Proceedings of the 1st International Conference on Natural Computing. 2005, 3611, 686–689. [→](#bodymatter-001.xhtml#xref_d6256e1240)

\[34\]Matsuda, Y., Nishimori, H., & Katzgraber, H. G. Ground-state statistics from annealing algorithms: Quantum vs classical approaches. 2009. arXiv:0808.0365. [→](#bodymatter-001.xhtml#xref_d6256e1255)

\[35\]Santoro, G. E., Martonak, R., Tosatti, E., & Car, R. Theory of quantum annealing of an Ising spin glass. Science. 2002, 295(5564),2427–2430. [→](#bodymatter-001.xhtml#xref_d6256e1258)

\[36\]Choi, V. Adiabatic Quantum Algorithms for the NP-Complete Maximum-Weight Independent Set. Exact Cover and 3SAT Problems. 2010. [http://arxiv.org/abs/1004.2226](http://arxiv.org/abs/1004.2226). [→](#bodymatter-001.xhtml#xref_d6256e1264)

\[37\]Adachi S. H., & Henderson, M. P. Application of Quantum Annealing to Training of Deep Neural Networks. 2015. [https://arxiv.org/abs/1510.06356](https://arxiv.org/abs/1510.06356). [→](#bodymatter-001.xhtml#xref_d6256e1267)

\[38\]Amin, M. H., Andriyash, E., Rolfe, J., Kulchytskyy, B., & Melko, R. Quantum Boltzmann Machine. 2016. [https://arxiv.org/abs/1601.02036](https://arxiv.org/abs/1601.02036). [→](#bodymatter-001.xhtml#xref_d6256e1271)

\[39\]Vinci, W., Markström, K., Boixo, S., Roy, A., Spedalieri, F. M., Warburton, P. A., & Severini, S. Hearing the Shape of the Ising Model with a Programmable Superconducting-Flux Annealer. Scientific Reports. 2014, 4(5703). doi:10.1038/srep05703. [→](#bodymatter-001.xhtml#xref_d6256e1274)

\[40\]Chancellor, N., Szoke, S., Vinci, W., Aeppli, G., & Warburton, P. A. Maximum-Entropy Inference with a Programmable Annealer. Scientific Reports. 2016, 6(22318). doi: 10.1038/srep22318. [→](#bodymatter-001.xhtml#xref_d6256e1277)

\[41\]Otsubo, Y., Inoue, J. I., Nagata, K., & Okada, M. Effect of quantum fluctuation in error-correcting codes. Physical Review E. 2012, 86(051138). doi:10.1103/PhysRevE.86.051138. [→](#bodymatter-001.xhtml#xref_d6256e1280)

\[42\]Otsubo, Y., Inoue, J. I., Nagata, K., & Okada, M. Code-division multiple-access multiuser demodulator by using quantum fluctuations. Physical Review E. 2014, 90(012126). doi:10.1103/PhysRevE.90.012126. [→](#bodymatter-001.xhtml#xref_d6256e1283)

\[43\]Marzec, M. Portfolio Optimization: Applications in Quantum Computing. Social Science Research Network Technical Report. 2014. doi:10.2139/ssrn.2278729. [→](#bodymatter-001.xhtml#xref_d6256e1286)

\[44\]Coxson, G. E., Hill, C. R., & Russo, J. C. Adiabatic quantum computing for finding low-peak-sidelobe codes. High Performance Extreme Computing conference, IEEE 7. 2014, 3910–3916. doi:10.1039/b509983h. [→](#bodymatter-001.xhtml#xref_d6256e1290)

\[45\]Kirkpatrik, S., Gelatt Jr., C. D., & Vecchi, M. P. Optimization by simulated annealing. Science. 1983, 220, 671–680. [→](#bodymatter-001.xhtml#xref_d6256e1296)

\[46\]de Falco, D., & Tamascelli, D. An introduction to quantum annealing RAIRO – Theoretical Informatics and Applications. 2011, 45, 99–116. [→](#bodymatter-001.xhtml#xref_d6256e1299)

\[47\]Morita, S., & Nishimori, H. Mathematical Foundation of Quantum Annealing. 2011. [https://arxiv.org/abs/0806.1859v1](https://arxiv.org/abs/0806.1859v1). [→](#bodymatter-001.xhtml#xref_d6256e1302)

\[48\]Lucas, A. Ising formulations of many NP problems. Front. Physics. 2014, 12(5). [→](#bodymatter-001.xhtml#xref_d6256e1308)

\[49\]Young, A. P. (Ed). Spin Glasses and Random Fields. Singapore: World Scientific. 1998. [→](#bodymatter-001.xhtml#xref_d6256e1311)

\[50\]Nishimori, H. Statistical Physics of Spin Glasses and Information Processing: An Introduction. Oxford University Press, 2001. [→](#bodymatter-001.xhtml#xref_d6256e1314)

\[51\]Amin, M. H. Physical Review Letters. 102, 220401, ISSN 0031-9007. [→](#bodymatter-001.xhtml#xref_d6256e1317)

\[52\]Jansen, S., Ruska, M. B., & Seiler, R. Journal of Mathematical Physics. 2007, 48, 102111, ISSN 00222488. [→](#bodymatter-001.xhtml#xref_d6256e1320)

\[53\]da Silva, A. J., Ludermir, T. B., & de Oliveira, W. D. Quantum perceptron over a field and neural network architecture selection in a quantum computer. Neural Networks. 2016, 76, 55–64. [→](#bodymatter-001.xhtml#xref_d6256e1335)

\[54\]Panella, M., Martinelli, G. Neural networks with quantum architecture and quantum learning. International Journal of Circuit Theory and Applications. 2011, 39, 61–77. [→](#bodymatter-001.xhtml#xref_d6256e1338)

\[55\]Kak, S. On quantum neural computing. Advances in Imaging and Electron Physics. 1995, 94(259). [→](#bodymatter-001.xhtml#xref_d6256e1347)

\[56\]Chrisley, R. Quantum Learning. New directions in cognitive science: Proceedings of the international symposium, Saariselka, 4–9 August 1995, Lapland, Finland. Pylkkänen, P., & Pylkkö, P. (Eds). Finnish Association of Artificial Intelligence, Helsinki. 1995, 77–89. [→](#bodymatter-001.xhtml#xref_d6256e1350)

\[57\]Narayanan, A., & Menneer, T. Quantum artificial neural network architectures and components. Information Sciences. 2000, 128, 231–255. [→](#bodymatter-001.xhtml#xref_d6256e1353)

\[58\]Schuld, M., Sinayskiy, I., & Petruccione, F. Simulating a perceptron on a quantum computer. 2014. ArXiv:1412.3635. [→](#bodymatter-001.xhtml#xref_d6256e1356)

\[59\]Purushothaman, G., & Karayiannis, N. Quantum Neural Networks (QNN’s): Inherently Fuzzy Feedforward Neural Networks. IEEE Transactions on Neural Networks. 1997, 8(3),679. [→](#bodymatter-001.xhtml#xref_d6256e1359)

\[60\]Behrman, E. C., Steck, J. E., Kumar, P., & Walsh, K. A. Quantum Algorithm design using dynamic learning. Quantum Information and Computation. 2008, 8(1&2),12–29. [→](#bodymatter-001.xhtml#xref_d6256e1365)

\[61\]Ventura, D., & Martinez, T. A quantum associative memory based on Grover’s algorithm. Proceedings of the International Conference on Artificial Neural Networks and Genetics Algorithms. 1999, 22–27. [→](#bodymatter-001.xhtml#xref_d6256e1372)

# 2 Topographic representation for quantum machine learning

Bruce J. MacLennan University of Tennessee, Dept. of Electrical Eng. and Computer Science, 1520, Middle Dr., 37996, Knoxville, Tennessee, USA 

#### Abstract

One of the most common information representations in the brain is the *topographic* or *computational map*, in which neurons are arranged systematically according to the values they represent. By representing quantitative relationships spatially, computational maps enable the brain to compute complex, nonlinear functions to the accuracy required. This chapter proposes two approaches to quantum computation for machine learning by means of topographic representation. It shows how to construct unitary operators, implementable on quantum computers, that implement arbitrary (including nonlinear) functions via computational maps.

Keywords: computational map,  neural network,  quantum computation,  quantum machine learning,  quantum neural network,  topographic map,  topographic representation,  

## 2.1 Introduction

This chapter proposes a brain-inspired approach to quantum machine learning with the goal of circumventing many of the complications of other approaches. The fact that quantum processes are unitary presents both opportunities and challenges. A principal opportunity is that a large number of computations can be carried out in parallel in linear superposition, that is, with quantum parallelism. There are of course many technical challenges in quantum computing, but the principal theoretical challenge in quantum machine learning is the fact that quantum processes are linear whereas most approaches to machine learning depend crucially on nonlinear operations. Artificial neural networks, in particular, require a nonlinear activation function, such as a logistic sigmoid function, for nontrivial machine learning. Fortunately, the situation is not hopeless, for we know that nonlinear processes can be embedded in unitary processes, as is familiar from the circuit model of quantum computation \[[1](#bodymatter-002.xhtml#b_9783110670707-002_ref_001)\].

Despite the complications of quantum machine learning, it presents a tantalizing approach to implementing large-scale machine learning in a post-Moore’s law technological era. However, there are many approaches to machine learning and several approaches to quantum computation (e.g., circuit model, annealing), and it is not obvious which combinations are most likely of success. Schuld, Sinayskiy, and Petruccione \[[2](#bodymatter-002.xhtml#b_9783110670707-002_ref_002), [3](#bodymatter-002.xhtml#b_9783110670707-002_ref_003)\] provide useful recent reviews of some approaches to quantum neural networks and quantum machine learning more generally. They conclude that none of the proposals for quantum neural networks succeed in combining the advantages of artificial neural networks and quantum computing. They argue that open quantum systems, which involve dissipative interactions with the environment, are the most promising approach. Moreover, few of the proposals include an actual theory of quantum machine learning.

This chapter explores an approach to the quantum implementation of machine learning involving nonlinear functions operating on information represented topographically, as is common in neural cortex. However, there are many approaches to neurocomputing, that is, to brain-inspired computing, some of which may be more amenable to quantum implementation than others, and so we must say a few words about the alternatives. For the brain may be modelled at many different levels, and models at each of these levels may provide a basis for machine learning. For example, in recent years spiking neural network models have become popular once again, largely due to their power advantages when implemented in hardware \[e.g., [4](#bodymatter-002.xhtml#b_9783110670707-002_ref_004), [5](#bodymatter-002.xhtml#b_9783110670707-002_ref_005)\]. Such models mimic the “all or none” action potential generation by biological neurons without addressing the detailed dynamics of the action potential. On the other hand, most contemporary applications of artificial neural networks, including those used in deep learning, use a higher level, rate-based model. That is, the real values passed between the units (neuron analogs) represent the rate of neural spiking rather than individual spikes. It has been argued that this is the appropriate level for modeling neural information processing, since there are many stochastic effects on the generation and reception of action potentials, and because the fundamental units of information processing are *microcolumns* comprising about 100 neurons \[\[[6](#bodymatter-002.xhtml#b_9783110670707-002_ref_006)\], chapter 2\]. Therefore it is most fruitful to view neural computation as a species of massively parallel analog computation. Since quantum computation makes essential use of complex–valued probability amplitudes, it is also fruitful to treat it as a species of analog computation, and so analog information representation provides one point of contact between quantum computation and artificial neural networks \[[7](#bodymatter-002.xhtml#b_9783110670707-002_ref_007)\].

## 2.2 Topographic representation in the brain

Another respect in which information processing in the brain differs from most artificial neural network models is that biological neural networks are spatially organized, with connectivity dependent on spatial organization. Although artificial neural networks are typically organized in layers, there is generally no spatial relationship among the neurons in each layer;[¹](#fn1)

One of the most common spatial information organizations used by the brain is the *topographic representation* or *computational map*. In such representations, distinct points **x** in some abstract space 𝒳 are mapped systematically to physical locations **r** = *µ*(**x**) in a two-dimensional region of cortex; that is, spatial relationships among the neurons are correlated with topological relationships in the abstract space. These maps are especially common in motor areas \[[8](#bodymatter-002.xhtml#b_9783110670707-002_ref_008)\] and sensory areas \[\[[6](#bodymatter-002.xhtml#b_9783110670707-002_ref_006)\], ch. 6\]. For example, tonotopic maps have the neurons that respond to different pitches arranged in order by pitch. Retinotopic maps have a spatial organization that mirrors the organization of the retina and visual field. Neurons in primary visual cortex that respond to edges are arranged systematically according to the orientation of the edges. There are many other examples throughout the brain, and this is perhaps the single most common information representation used by the brain.

In these topographic maps, a particular value **x** is represented by an activity peak in the corresponding cortical location *µ*(**x**). The strength of the activity reflects the value’s degree of presence, importance, or probability. Moreover, multiple simultaneous values, with differing relative strengths or probabilities, are represented by multiple simultaneous activity peaks of differing amplitudes. Therefore, such cortical maps can represent superpositions of values, each with its own amplitude.

Topographic maps provide another point of contact between artificial neural networks and quantum computation, because the computational maps in the brain are large and dense enough that they can be usefully treated mathematically as *fields*, that is, as continuous distributions of continuous quantity \[[9](#bodymatter-002.xhtml#b_9783110670707-002_ref_009)\]. Such representations are suggestive of quantum mechanical wave functions, which are also continuous distributions of continuous quantity (the complex probability amplitude). In both cases these fields are treated mathematically as continuous functions on a continuous domain, and Hilbert spaces provide the mathematical framework for describing them \[[7](#bodymatter-002.xhtml#b_9783110670707-002_ref_007)\]. In this chapter we exploit this analogy to implement brain-inspired approaches to quantum machine learning.

Because of their spatial representation of values, topographic maps can be used to implement arbitrary functions in the brain, essentially by a kind of table lookup. Suppose the brain needs to implement a (possibly nonlinear) transformation, **y** = *f*(*x*). This can be accomplished by neural connections from locations **r **\= *µ*(**x**) in the input map to corresponding locations **s** = *μ*^′(**y**) = *μ*^′\[*f*(**x**)\] in the output map that represents the result space. Thus activity representing **x** in the input map will cause corresponding activity representing **y** in the output map. Moreover, a superposition of input values will lead to a corresponding superposition of output values. Therefore, topographic representations allow the computation of nonlinear functions in linear superposition \[[9](#bodymatter-002.xhtml#b_9783110670707-002_ref_009), [10](#bodymatter-002.xhtml#b_9783110670707-002_ref_010), [11](#bodymatter-002.xhtml#b_9783110670707-002_ref_011), [12](#bodymatter-002.xhtml#b_9783110670707-002_ref_012), [13](#bodymatter-002.xhtml#b_9783110670707-002_ref_013)\], which suggests their usefulness in quantum computation \[[7](#bodymatter-002.xhtml#b_9783110670707-002_ref_007)\]. On the other hand, topographic maps make relatively inefficient use of representational resources, because every represented value has to have a location in the map \[although this can be mitigated by means of *coarse coding*, by which precise values are represented by a population of broadly tuned neurons with overlapping receptive fields \[[14](#bodymatter-002.xhtml#b_9783110670707-002_ref_014), [15](#bodymatter-002.xhtml#b_9783110670707-002_ref_015)\]\]. Therefore, use of topographic representations will require a reasonably scalable quantum computing technology. In this chapter we explore two topographic approaches to quantum computation with a focus on machine learning.

## 2.3 Topographic basis maps

In the brain, the state of a topographic map is a real-valued function defined over a (typically two-dimensional) space Ω. To apply these ideas in quantum computation, we consider a quantum state |*ψ*⟩ in which the probability amplitude *ψ*(**r**) at location **r** ∈ Ω represents the amplitude (presence, importance, etc.) of the value **x** via the correspondence **r **\= *µ*(**x**). Here **r** ∈ Ω may be a continuous index representing, for example, spatial location, or the index of a discrete quantum state, such as a wavelength or the state of a qubit register. The states |*r*⟩ form a discrete basis or continuous pseudo-basis for the input and output quantum states. In the continuous case, the input value **x** is represented by a continuous basis state |*μ*(**x**)⟩, which is a Dirac unit impulse at **r **\= *µ*(**x**), that is, |**r**⟩ = *δ***[r]** where *δ***[r]**(**s**) = *δ*(**s **− **r**). Similarly an output value **y** is represented by the continuous basis state |*μ*^′(**y**)⟩=|*μ*^′\[*f*(**x**)\]⟩ = *δ*[*μ*^′(**y**)]. We call such a representation (whether discrete or continuous) a *topographic basis map*.

For such a continuous basis we can define a Hilbert-Schmidt linear operator:

$T\_{f} = \\int\\limits\_{\\mathcal{X}}^{}d\\mathbf{x}\\left| {\\mu^{\\prime}\\left\\lbrack {f\\left( \\mathbf{x} \\right)} \\right\\rbrack} \\right.\\rangle\\langle\\mu\\left( x \\right)|,$ 

where 𝒳 is the space of input values. (We write *T *\= *T[f]* when *f* is clear from context.) This operator has the desired behavior: *T*|*μ*(**x**)⟩=|*μ*^′\[*f*(**x**)\]⟩ for all **x** ∈ 𝒳. In this manner the linear operator *T* computes the nonlinear function *f* via the computational maps. We call such an operator a *graph kernel* because it uses the explicit *graph* of *f* \[that is, the set of pairs (*μ*^′\[*f*(**x**)\], *μ*(**x**)) for all **x** ∈ 𝒳\] to do a kind of table lookup.[²](#fn2)

Notice that if the input map is a superposition of input values, |*ψ*⟩=*a*|*μ*(**x**)⟩ + *b*|*μ*(**x**^′)⟩, then the output map will be a superposition of the corresponding results: *T*|*ψ*⟩=*a*|*μ*^′\[*f*(**x**)\]⟩ + *b*|*μ*^′\[*f*(**x**^′)\]⟩. Therefore, continuous topographic basis maps permit nonlinear functions to be computed in linear superposition (quantum parallelism). This is a step toward quantum computation, but *T* might not be unitary, and we have more work to do.

The reader might question the use of a continuous basis. First, note that for separable Hilbert spaces, the continuous basis can always be replaced by an infinite discrete basis, for example, by a discrete series of sinusoids or complex exponentials of the appropriate dimension. Second, the infinite discrete basis can be approximated by a finite discrete basis, for example, by band-limited sinusoids or complex exponentials. Such an approximation is especially appropriate for neural network machine learning, which requires only low-precision calculation.

### 2.3.1 Bijections

We proceed to show several examples of nonlinear computations performed via quantum computational maps, beginning with a simple case and proceeding to more complex ones. For simplicity, we will ignore the representation map *µ* and consider computations from one quantum state to another. We consider both one-dimensional continuous domains, *Ω* = \[*x*[*l*], *x*[*u*]\] and discrete domains, *Ω* = {*x*[1],…, *x*[*n*]}. Typically the values would be evenly spaced, for example, *Ω* = {0,*Δ**x*,2*Δ**x*,…, (*n*−1)*Δ**x*}, but this is not required, and other spacings, such as logarithmic, might be useful. (Logarithmic maps are found in some sensory regions of the cortex.) In both cases the vectors {|*x*⟩| *x*∈𝒳} are an orthonormal basis (composed of unit vectors in ℂ^(*n*) for the discrete case and of delta functions in ℒ²(*Ω*) for the continuous case). For example, in the discrete case, the values *x*[1]*, …, x[n]* might be represented by the composite state of an *N*\-qubit register, where *n *\= 2*^N*. This might seem to require a large number of qubits, but even in the absence of coarse coding, seven qubits would be sufficient to represent values with 1% precision, which is adequate for many machine learning applications.

We begin with a bijective scalar function *f* : *Ω* → *Ω*, where *Ω* = \[−1,1\]. The hyperbolic tangent (appropriately restricted),[³](#fn3)

(2.1)$T = \\!\\!\\int\\limits\_{\\Omega}^{}dx|f\\left( x \\right)\\rangle\\langle x|.$ 

Since *f* is bijective, the adjoint of *T* is

(2.2) $T^{\\dagger} = \\int\\limits\_{\\Omega}^{}dx|x\\rangle\\langle f\\left( x \\right)| = \\int\\limits\_{\\Omega}^{}dy|f^{- 1}\\left( y \\right)\\rangle\\langle y|.$ 

It is easy then to show that *T* is unitary and therefore amenable to quantum computation. In general, we have:

#### Proposition 1

The graph kernel *T* of a continuous bijection *f* : *Ω* → *Ω*^′ is unitary.

#### Proof:

Substituting [eqs. (2.1)](#bodymatter-002.xhtml#b_9783110670707-002_eq_001) and ([2.2](#bodymatter-002.xhtml#b_9783110670707-002_eq_002)), observe:

$\\begin{matrix} {T^{\\dagger}T} & {= \\left( {\\int\\limits\_{\\Omega^{\\prime}}\\left| {f^{- 1}\\left( y \\right)\\rangle\\langle y} \\right|dy} \\right)\\left( {\\int\\limits\_{\\Omega}\\left| {f\\left( x \\right)\\rangle\\langle x} \\right|dx} \\right)} \\\\ & {= \\int\\limits\_{\\Omega}^{}\\int\\limits\_{\\Omega^{\\prime}}^{}\\left| {f^{- 1}\\left( y \\right)\\rangle\\langle y|f\\left( x \\right)\\rangle\\langle x} \\right|\\ dydx} \\\\ & {= \\int\\limits\_{\\Omega}^{}\\int\\limits\_{\\Omega^{\\prime}}^{}\\left| {f^{- 1}\\left( y \\right)\\rangle\\langle y|f\\left( x \\right)\\rangle dy\\rangle dy\\langle x} \\right|dx} \\\\ & {= \\int\\limits\_{\\Omega}^{}\\left| {f^{- 1}\\left( {f\\left( x \\right)} \\right)\\rangle\\langle x} \\right|dx} \\\\ & {= I\_{\\Omega}.} \\\\ \\end{matrix}$ 

The fourth line follows from the “sifting” property of the Dirac delta: $\\int\\limits\_{\\Omega^{\\prime}}^{}\\left| {{F\\left( y \\right)\\rangle\\langle y|a}\\rangle} \\right.dy = \\left| {F\\left( a \\right)\\rangle} \\right.$. Likewise,

$\\begin{matrix} {TT^{\\dagger}} & {= \\left( {\\int\\limits\_{\\Omega}^{}|f\\left( x \\right)\\rangle\\langle x|dx} \\right)\\left( {\\int\\limits\_{\\Omega^{\\prime}}^{}\\left| {f^{- 1}(y)\\rangle\\langle y} \\right|dy} \\right)} \\\\ & {= \\int\\limits\_{\\Omega^{\\prime}}^{}\\int\\limits\_{\\Omega}^{}\\left| {f\\left( x \\right)\\rangle\\langle x|f^{- 1}\\left( y \\right)\\rangle\\langle y} \\right|\\ dxdy} \\\\ & {= \\int\\limits\_{\\Omega^{\\prime}}^{}|f\\left( {f^{- 1}\\left( y \\right)} \\right)\\rangle\\langle y|dy = I\_{\\Omega^{\\prime}}.} \\\\ \\end{matrix}$ 

Therefore *T* is unitary.

In the discrete basis case, let *y[i] *\= *f* (*x[i]*), where *f* is bijective. The unit vectors |*x*[*i*]⟩ are a basis for ℂ^(*n*), and the unit vectors |*y*[*i*]⟩ are also a (possibly different) basis for ℂ^(*n*). The graph kernel is

(2.3)$T = \\sum\\limits\_{i = 1}^{n}|y\_{i}\\rangle\\langle x\_{i}| = \\sum\\limits\_{i = 1}^{n}|f\\left( x\_{i} \\right)\\rangle\\langle x\_{i}|,$ 

which is also easily proved to be unitary. More directly, we can observe that *T* is a permutation matrix on the basis elements and therefore orthogonal.

If the input is a weighted superposition of values, |*ψ*⟩ = ∫[*Ω*]^()*d**x* *p*(*x*)|*x*⟩, then applying the kernel \[[eq. (2.1)](#bodymatter-002.xhtml#b_9783110670707-002_eq_001)\] will give a corresponding superposition of the outputs: *T*|*ψ*⟩ = ∫[*Ω*]^()*d**x* *p*(*x*)|*f*(*x*)⟩. The same applies, of course, in the discrete case. Moreover, since the graph kernel is unitary, its adjoint computes the inverse function. Therefore, if |*ϕ*⟩ = ∫[*Ω*^′]^()*d**y* *q*(*y*)|*y*⟩, then *T*^†|*ϕ*⟩ = ∫[*Ω*^′]^()*d**y* *q*(*y*)|*f*^( − 1)(*y*)⟩. That is, applying the adjoint to a superposition of outputs will compute a corresponding superposition of inputs.

### 2.3.2 Non-surjective Injections

As a further step towards the quantum computation of arbitrary functions by means of computational maps, we consider a relatively simple case: non-surjective injections (that is, one-to-one non-onto functions). We restrict our attention to finite domains and codomains. Therefore, let *Ω* = {*x*[1],…,*x*[*n*]} and *Ω*^′ = {*y*[1],…,*y*[*m*]}, where *n < m*, and consider an injection *f* : *Ω* → *Ω*^′. Input maps will be in an *n*\-dimensional Hilbert space ℋ(*Ω*) and output maps will be in an *m*\-dimensional Hilbert space ℋ(*Ω*^′). Since *n < m*, ancillary constants will need to be provided from a space ℋ[*C*], and so the complete input space will be in ℋ(*Ω*) ⊗ ℋ[*C*]. Our implementation will also generate “garbage” output in a space *H*[*G*], and so the complete output space will be in ℋ(*Ω*^′)⊗ ℋ[*G*]. The input and output dimensions must be equal, and the simplest way to accomplish this is to make ℋ[*C*] *m*\-dimensional and ℋ[*G*], *n*\-dimensional, so that our operator is an *mn*\-dimensional Hilbert-space transformation. Let {|*w*[1]⟩,…,|*w*[*m*]⟩} be an orthonormal (ON) basis for ℋ[*C*] and let {|*v*[1]⟩,…,|*v*[*n*]⟩} be an ON basis for ℋ[*G*]. (We could in fact use the ℋ(*Ω*^′) basis for ℋ[*C*] and the ℋ(*Ω*) basis for ℋ[*G*], but here we develop a more general result.)

Our goal will be to define a unitary *U* so that *U*|*x*⟩|*w*[1]⟩ = |*f*(*x*)⟩|*γ*⟩, where |*w*[1]⟩ is an ancillary constant and |*γ*⟩ is garbage. As we will see, *U* can be implemented by an appropriate permutation of the input basis into the output basis, which can be expressed as the sum of several operators:

(2.4)$U\\overset{def}{=}{T + S + R + Q}.$ 

The work of the function *f* is accomplished by the *T* component, which maps |*x*[*j*]⟩ to |*f*(*x*[*j*])⟩:

(2.5)$T\\overset{def}{=}\\sum\\limits\_{j = 1}^{n}\\left| {f\\left( x\_{j} \\right)\\rangle} \\right|v\_{1}\\rangle\\langle x\_{j}|\\langle w\_{1}|.$ 

Note that *T*|*x*[*j*]⟩|*w*[1]⟩ = |*f*(*x*[*j*])⟩|*v*[1]⟩ and *T* is a bijection of the *n*\-dimensional subspace ℋ(*Ω*) ⊗ ℋ({|*w*[1]⟩}). However, *T* is not unitary since it is not a surjection. See [Figure 2.1](#bodymatter-002.xhtml#b_9783110670707-002_fig_001).

![Figure 2.1: Permutation of basis vectors to implement non-surjective injections. After each component of the kernel, the number of basis vectors that it maps is indicated in parentheses; for example, R maps \\left( {m - 1} \\right)\\left( {n - 1} \\right) basis vectors. T maps function inputs to outputs, S maps zero amplitudes to non-range codomain elements, and R and Q bijectively map the remaining basis elements.](graphic/converted/b_9783110670707-002_fig_001.jpg)

Figure 2.1: Permutation of basis vectors to implement non-surjective injections. After each component of the kernel, the number of basis vectors that it maps is indicated in parentheses; for example, *R* maps (*m*−1)(*n*−1) basis vectors. *T* maps function inputs to outputs, *S* maps zero amplitudes to non-range codomain elements, and *R* and *Q* bijectively map the remaining basis elements.

The *S* component ensures that non-range elements of the codomain have preimages in the domain. Therefore, let *m*[*n**r*] be the number of codomain elements that are not in the range of *f*, that is, *m*[*n**r*]\= |*Ω*^′  ∖ *I**m* *f*|  = *m* − *n*. Call these non-range codomain elements {*z*[1],…,*z*[*m*[*n**r*]]} ⊂ *Ω*^′. Then the *S* component is defined:

(2.6) $S\\overset{def}{=}\\sum\\limits\_{i = 1}^{m\_{nr}}\\left| {z\_{i}\\rangle} \\right|v\_{1}\\rangle\\langle x\_{1}|\\langle w\_{i + 1}|.$ 

Therefore, *S* is a bijection of an *m*[*n**r*]\-dimensional subspace and each non-range element |*z*[*i*]⟩|*v*[1]⟩ has a unique preimage |*x*[1]⟩|*w*[*i* + 1]⟩.

Note that *T* transforms *n* basis vectors (those for which the second register is |*w*[1]⟩), and *S* transforms *m*[*n**r*] basis vectors (those for which the first register is |*x*[1]⟩ and the second register is one of |*w*[2]⟩, …, |*w*[*m*[*n**r*] + 1]⟩), for a total of *n* + *m*[*n**r*] = *m* basis elements, but the input space has a total of *mn* basis elements, and the remainder must be bijectively mapped. Therefore, to complete the unitary operator we add the following additional components:

(2.7) $R\\overset{def}{=}\\sum\\limits\_{i = 2}^{m}\\sum\\limits\_{j = 2}^{n}\\left| {y\_{i}\\rangle} \\right|v\_{j}\\rangle\\langle x\_{j}|\\langle w\_{i}|,$ (2.8)$Q\\overset{def}{=}\\sum\\limits\_{j = 1}^{n - 1}\\left| {y\_{1}\\rangle} \\right|v\_{j + 1}\\rangle\\langle x\_{1}|\\langle w\_{m\_{nr} + j}|.$ 

*R* maps (*m*−1)(*n*−1) basis elements: those for *i* ≠ 1 and *j* ≠ 1, that is, those with neither |*x*[1]⟩ in the first register nor |*w*[1]⟩ in the second. *Q* maps the remaining *n* − 1 basis elements: those which have |*x*[1]⟩ in the first register and |*w*[*m*[*n**r*] + 1]⟩ to |*w*[*m*[*n**r*] + *n*]⟩ in the second (recall that *m* = *m*[*n**r*] + *n*).

Notice that *U* maps every input basis vector into exactly one output basis vector and vice versa (see [Figure 2.1](#bodymatter-002.xhtml#b_9783110670707-002_fig_001)). Summing the numbers of basis vector dyads for *T, S, R, Q* gives:

*n* + *m*[*n**r*] + (*m*−1)(*n*−1) + (*n*−1) = *m* + (*m*−1)(*n*−1) + *n* − 1 = *m**n*. 

#### Proposition 2

Let *Ω* and *Ω*^′ be finite sets with *n* = |*Ω*|, *m* = |*Ω*^′|, and *m* > *n*. Let *f* : *Ω* → *Ω*^′ be a non-surjective injection. Let ℋ[*C*] and ℋ[*G*] be Hilbert spaces of dimension *m* and *n*, respectively (representing ancillary constant inputs and garbage outputs). Let |*ω*⟩ be a fixed basis vector of ℋ[*C*] and |*υ*⟩ be a fixed basis vector of ℋ[*G*]. Then there is a unitary operator *U* ∈ ℒ\[ℋ(*Ω*) ⊗ ℋ[*C*], ℋ(*Ω*^′)⊗ ℋ[*G*]\] such that for all *x* ∈ *Ω*,

(2.9)*U*(|*x*⟩⊗|*ω*⟩) = |*f*(*x*)⟩⊗|*υ*⟩. 

#### Proof:

The proposition follows from the construction preceding the proposition.

If the input to *U* is a (normalized) superposition, |*ψ*⟩ = ∑[*k*]*p*[*k*]|*x*[*k*]⟩, then the output will be a superposition of the corresponding function results: *U*|*ψ*⟩|*ω*⟩ = ∑[*k*]*p*[*k*]|*f*(*x*[*k*])⟩|*υ*⟩.

The dimension of the input and output spaces of this implementation is *mn*. A more resource-efficient but also more complicated implementation operates on a space of dimension *L**C**M*(*m*, *n*). The principle is the same: a permutation of the basis vectors.

### 2.3.3 Non-injective surjections

Next we consider functions *f* : *Ω* → *Ω*^′ that are surjections but not injections; that is, *f* maps onto *Ω*^′ but might not be one-to-one. This includes many useful functions, such as non-injective squashing functions and Gaussians, but also binary functions such as addition and multiplication (as explained later).

A non-injective function loses information, and thus for quantum computation it must be embedded in a larger injective function, which moreover must be unitary. In particular, if *f* is non-injective (e.g., *f*(*x*) = *f*(*x*^′) for some *x* ≠ *x*^′), then the corresponding graph kernel will also be non-injective: *T*|*x*⟩=|*y*⟩ = *T*|*x*^′⟩ for |*x*⟩ ≠ |*x*^′⟩. Therefore *T*(|*x*⟩ − |*x*^′⟩)= 0, which implies that |*x*⟩−|*x*^′⟩ is in the null space of *T*, which we write 𝒩(*T*). Therefore there is a bijection between the orthogonal complement of the null space, 𝒩(*T*)^⊥, and the range of the operator, Im *T*. Hence we will implement the non-injective operation by decomposing the input |*ψ*⟩ into orthogonal components |*ψ*⟩=|*μ*⟩ + |*ν*⟩, where |*μ*⟩∈ 𝒩(*T*)^⊥ and |*ν*⟩∈ 𝒩(*T*). The |*μ*⟩ component is sufficient to determine the output, so there is a bijection |*μ*⟩↦*T*|*ψ*⟩, and the |*ν*⟩ component preserves the information to differentiate the inputs that map to this output.

To explain how this separation can be accomplished, we consider the finite-dimensional case, but it is easily extended. Let *Ω* = {*x*[1],…,*x*[*n*]} and *Ω*^′  = {*y*[1],…,*y*[*m*]}; since *f* is surjective, *m *≤ *n*.

The desired operator *T* is in ℒ(ℋ, ℋ^′), where ℋ = ℋ(*Ω*) is an *n*\-dimensional Hilbert space with basis {|*x*[1]⟩,…,|*x*[*n*]⟩}. The output space ℋ^′ is also *n*\-dimensional, and *m* of its basis vectors {|*y*[1],…,|*y*[*m*]} are used to represent a topographic map of the function’s codomain (which is also its range), Im *f *\= *Ω*^′ = {*y*[1],…,*y*[*m*]}. Therefore ℋ(*Ω*^′) is a subspace of ℋ^′. Let {|*w*[1]⟩,…,|*w*[*n* − *m*]⟩} be a basis for ℋ(*Ω*^′)^⊥, the orthogonal complement of ℋ(*Ω*^′) in ℋ^′. (This subspace will represent “garbage” with no computational relevance.)

We will define {|*u*[1]⟩,…,|*u*[*m*]⟩} to be any ON basis for 𝒩(*T*)^⊥ (the row space of *T*), where *m* is the rank of *T*, and we will define {|*v*[1]⟩,…,|*v*[*n*[*o*]]⟩} to be any ON basis for 𝒩(*T*), where *n[o] *\= *n *− *m* is the nullity of *T*. These bases will determine the orthogonal components |*μ*⟩∈ 𝒩(*T*)^⊥ and |*ν*⟩∈ 𝒩(*T*) into which any input is separated.

An example will make this clearer. Suppose *Ω* = {*k**Δ**x*|−*N*<*k*<*N*} and *Ω*^′ = {*k**Δ**x*|0≤*k*<*N*}. Let *a**b**s*: *Ω* → *Ω*^′ be the absolute value function (a noninjective surjection between these sets). A basis for the nonnull space 𝒩(*T*)^⊥ comprises |*u*[0]⟩  = |0⟩ and the vectors $|u\_{k}\\rangle = \\left( {|{- k\\Delta x\\rangle} + |{k\\Delta x\\rangle}} \\right)/\\sqrt{2}$ (for *k* = 1, …, *N* − 1). (Note that | − *k**Δ**x*⟩ and |*k**Δ**x*⟩ are orthogonal vectors for *k* ≠ 0.) These *N* basis vectors are in a one-to-one relation with the codomain elements |*k**Δ**x*⟩ (for *k* = 0, …, *N* − 1). The nullity is *n*[*o*] = (2*N*−1) − *N* = *N* − 1 and the basis vectors of the null space are:

$|v\_{k}\\rangle = \\left( {|k\\Delta x\\rangle - | - k\\Delta x\\rangle} \\right)/\\sqrt{2}\\quad\\left( {{for\\ }k = 1,\\ldots,N - 1} \\right).$ 

Projection onto this space keeps the information necessary to distinguish the specific preimage that maps to a given output. In this case, it remembers the sign of the input: note that $\\langle v\_{k}|k\\Delta x\\rangle = + 1/\\sqrt{2}$ and $\\langle v\_{k}| - k\\Delta x\\rangle = - 1/\\sqrt{2}$. Therefore, for input |*k**Δ**x*⟩, the orthogonal components are $\\left| {\\mu\\rangle =} \\right|u\_{k}\\rangle/\\sqrt{2}$ and $\\left| {\\nu\\rangle =} \\right|v\_{k}\\rangle/\\sqrt{2}$; and for input |−*k**Δ**x*⟩, they are $\\left| {\\mu\\rangle =} \\right|u\_{k}\\rangle/\\sqrt{2}$ and $\\left| {\\nu\\rangle = -} \\right|v\_{k}\\rangle/\\sqrt{2}$. This completes the example and we return to the construction for an arbitrary non-injective surjection.

For each *y*[*i*] ∈ *Ω*^′, let *f*^( − 1){*y*[*i*]} = {*x*|*f*(*x*) = *y*[*i*]} be the inverse image of *y*[*i*]; these are disjoint subsets of the domain *Ω* and correspond to orthogonal subspaces of ℋ. Let *n*[*i*] = |*f*^( − 1){*y*[*i*]}| be the *preimage multiplicity* of *y[i]*, where *n* = *n*[1] + ⋯ + *n*[*m*]. Because different *y[i]* ∈ Im *T* have different preimage multiplicities, it will be convenient to separate *f* into *m* constant functions *f*[*i*]: *f*^( − 1){*y*[*i*]} → {*y*[*i*]} with corresponding graph kernels:

(2.10)$T\_{i}\\overset{def}{=}\\frac{1}{\\sqrt{n\_{i}}}\\sum\\limits\_{x\_{j} \\in f^{- 1}{\\{ y\_{i}\\}}}|y\_{i}\\rangle\\langle x\_{j}|\\, = \\,|y\_{i}\\rangle\\frac{1}{\\sqrt{n\_{i}}}\\sum\\limits\_{x\_{j} \\in f^{- 1}{\\{ y\_{i}\\}}}\\langle x\_{j}|\\, = \\,|y\_{i}\\rangle\\langle u\_{i}|,$ 

where we have defined the following normalized basis vectors of 𝒩(*T*)^⊥:

(2.11)$|u\_{i}\\rangle\\overset{def}{=}\\frac{1}{\\sqrt{n\_{i}}}\\sum\\limits\_{x\_{j} \\in f^{- 1}{\\{ y\_{i}\\}}}|x\_{j}\\rangle,\\quad i = 1,\\ldots,m.$ 

The constant maps *T[i]* operate independently on orthogonal subspaces of ℋ.

Note that ⟨*u*[*i*]|*x*[*j*]⟩ ≠ 0 if and only if *y*[*i*] = *f*(*x*[*j*]), and in this case *T*[*i*]|*x*[*j*]⟩ = *n*[*i*]^( − 1/2)|*y*[*i*]⟩. (The *n*[*i*]^( − 1/2) factor is required for normalization of the |*u*[*i*]⟩.) Clearly {|*u*[1]⟩,…,|*u*[*m*]⟩} is an ON set, since its elements are normalized linear combinations of disjoint sets of the basis vectors. Therefore there is a one-to-one correspondence between the output vectors |*y*[*i*]⟩ and the basis vectors |*u*[*i*]⟩ of 𝒩(*T*)^⊥.

Next we characterize 𝒩(*T*) and 𝒩(*T*)^⊥. Observe that |*ψ*⟩∈ 𝒩(*T*[*i*]) if and only if 0 = *T*[*i*]|*ψ*⟩=|*y*[*i*]⟩ ⟨*u*[*i*]|*ψ*⟩, that is, if and only if ⟨*u*[*i*]|*ψ*⟩ = 0. Therefore, 𝒩(*T*[*i*]) is the *n* − 1 dimensional subspace orthogonal to |*u*[*i*]⟩ and 𝒩(*T*[*i*])^⊥ is the one-dimensional subspace spanned by {|*u*[*i*]⟩}. Therefore 𝒩(*T*)^⊥ is spanned by {|*u*[1]⟩,…,|*u*[*m*]⟩}.

The operation *T* is implemented in two parts, one that handles the components representing the null space and the other that handles the components representing its orthogonal complement, the nonnull space. The first part generates “garbage,” but is required for the operation to be invertible and hence unitary; the second part does the work of computing *f*.

We have |*v*[*j*]⟩ ∈ ℋ, the basis vectors for the 𝒩(*T*) subspace of the domain, which has dimension *n*[*o*] = *n* − *m*. Let {|*w*[*j*] ⟩|*j*\=1,…,*n*[*o*]} be any basis for ℋ(*Ω*^′)^⊥, the orthogonal complement of ℋ(*Ω*^′) in ℋ^′, which also has dimension *n* − *m*. We define *N* ∈ ℒ(ℋ, ℋ^′) to map the null space components down to this *n[o]*\-dimensional subspace:

(2.12)$N\\overset{def}{=}\\sum\\limits\_{j = 1}^{n\_{o}}|w\_{j}\\rangle\\langle v\_{j}|.$ 

Since there is a one-one correspondence between basis vectors |*u*[*i*]⟩ and output vectors |*y*[*i*]⟩, we implement the function *f* by an operator *M* ∈ ℒ(ℋ, ℋ^′) defined:

(2.13)$M\\overset{def}{=}\\sum\\limits\_{i = 1}^{m}|y\_{i}\\rangle\\langle u\_{i}|.$ 

This maps the *n*\-dimensional input into an *m*\-dimensional output subspace. As a result the operator

(2.14)*T* = *M* + *N* ∈ ℒ(ℋ, ℋ^′) 

maps an input |*x*⟩ to the correct output |*f*(*x*)⟩, but with a scale factor and additional “garbage.” Specifically, for *x[j]* ∈ *f* ^(−1){*y[i]*},

(2.15)*T*|*x*[*j*]⟩=(*M*+*N*)|*x*[*j*]⟩ = *M*|*x*[*j*]⟩+*N*|*x*[*j*]⟩ = *n*[*i*]^( − 1/2)|*y*[*i*]⟩+|*γ*[*j*]⟩. 

where |*γ*[*j*]⟩ = *N*|*x*[*j*]⟩ and $\\parallel {|\\gamma\_{j}\\rangle} \\parallel = \\sqrt{\\frac{n\_{i} - 1}{n\_{i}}}$. Note that the garbage |*γ*[*j*]⟩ is superimposed on the desired output. Subsequent computations operate on the ℋ(*Ω*^′) subspace and ignore the orthogonal subspace, which contains the garbage (which nevertheless must be retained, since it is entangled with the computational results).

The *T* operator is just a transformation from the {|*x*[1]⟩,…,|*x*[*n*]⟩} basis to the {|*y*[1]⟩,…,|*y*[*m*]⟩,|*w*[1]⟩,…,|*w*[*n* − *m*]⟩} basis, and is obviously unitary:

(*M*+*N*)^†(*M*+*N*) = *M*^†*M* + *N*^†*M* + *M*^†*N* + *N*^†*N* = *I*[𝒩(*T*)^⊥] + 0 + 0 + *I*[𝒩(*T*)] = *I*[ℋ], (*M*+*N*)(*M*+*N*)^† = *M**M*^† + *N**M*^† + *M**N*^† + *N**N*^† = *I*[ℋ(*Ω*^′)] + 0 + 0 + *I*[ℋ(*Ω*^′)^⊥] = *I*[ℋ^′]. 

Since the *T* operator is unitary, it can be approximated arbitrarily closely by a combination of *H* (Hadamard), CNOT (conditional NOT), and *T* (*π/*8) gates \[\[[1](#bodymatter-002.xhtml#b_9783110670707-002_ref_001)\], §4.5\], or any other universal set of quantum gates.

Unfortunately, the output vectors |*y*[*i*]⟩ have amplitudes that depend on their preimage multiplicities. That is, if *y*[*i*] = *f*(*x*[*j*]), then *T*|*x*[*j*]⟩ = *n*[*i*]^( − 1/2)|*y*[*i*]⟩ + |*γ*[*j*]⟩, and we get different scale factors *n*[*i*]^( − 1/2) depending on the preimage multiplicity. For *y*[*i*] = *f*(*x*[*j*]), we define $s\_{i}\\overset{def}{=}n\_{i}^{- 1/2}$ to be this scale factor so that *T*|*x*[*i*]⟩=*s*[*i*]|*y*[*i*]⟩ + |*γ*[*j*]⟩. We would like to equalize the differing amplitudes but there does not seem to be a unitary means for doing so.

It might seem that something like a Grover iteration \[[16](#bodymatter-002.xhtml#b_9783110670707-002_ref_016)\] could be used to rotate the state vector from *s*[*i*]|*y*[*i*]⟩+|*γ*[*j*]⟩ to |*y*[*i*]⟩, but different *s*[*i*] require different numbers of iterations. Something like Grover’s algorithm with an unknown number of solutions could be used, but this would require trying multiple rotations. Therefore, it seems better to accept the unwanted scale factors and work with them. This means that any |*y*[*i*]⟩ with positive amplitudes are considered outputs from the computation, and therefore all positive amplitudes are treated the same.

If we ignore the relative magnitudes of positive amplitudes, then a quantum state |*ψ*⟩ = ∑[*j*]*p*[*j*]|*x*[*j*]⟩ (with *p*[*j*] ≥ 0) can be interpreted as representing the set of all *x*[*j*] with positive amplitudes: {*x*[*j*]∈*Ω* | *p*[*j*]\>0}, where we assume of course that ∑[*j*]*p*[*j*]² ≤ 1. Moreover, the sum can be strictly less than one only if there are additional ancillary states that make up the difference (like |*γ*[*j*]⟩ in the previous example). Applying *T* to such a state computes a state representing the image of the input set. That is, *T*|*ψ*⟩ = ∑[*j*]*p*[*j*]*s*[*j*]|*f*(*x*[*j*])⟩, which represents the set {*f*(*x*[*j*])∈*Ω*|*p*[*j*]\>0}. If *S* ⊆ *Ω* is the set represented by |*ψ*⟩, then *T* |*ψ*⟩ represents its image *f* \[*S*\]. Since zero amplitudes will always map to zero amplitudes and positive amplitudes will map to positive amplitudes, set membership will be appropriately mapped from the domain to the codomain. The preceding construction gives us:

#### Proposition 3

Let *Ω* = {*x*[1],…,*x*[*n*]} and *Ω*^′  = {*y*[1],…,*y*[*m*]} be finite sets with *n* ≥ *m*. Suppose {|*x*[1]⟩,…,|*x*[*n*]⟩} is an ON basis for a Hilbert space ℋ and {|*y*[1]⟩,…,|*y*[*m*]⟩} is an ON basis for a subspace ℋ(*Ω*^′) of ℋ. For any surjective function *f*:*Ω*↠*Ω*^′ there is a unitary operator *T* ∈ ℒ(ℋ, ℋ) such that for any *x* ∈ *Ω*,

(2.16) $T|x\\rangle = \\frac{1}{\\sqrt{n\_{x}}}\\left| {f\\left( x \\right)\\rangle + \\left| {\\gamma\\rangle,} \\right.} \\right.$ 

where *n*[*x*] = |*f*^( − 1){*f*(*x*)}|, |*γ*⟩ ∈ ℋ(*Ω*^′)^⊥, and $|||{\\gamma\\rangle}|| = \\sqrt{\\frac{n\_{x} - 1}{n\_{x}}}$.

#### Proof:

As previously shown \[[eqs. (2.12)](#bodymatter-002.xhtml#b_9783110670707-002_eq_014)–([2.14](#bodymatter-002.xhtml#b_9783110670707-002_eq_014))\], this operator is given explicitly by

$T = \\sum\\limits\_{i = 1}^{m}|{y\_{i}\\rangle\\langle u\_{i}|} + \\sum\\limits\_{k = 1}^{n - m}|{w\_{k}\\rangle\\langle v\_{k}|},$ 

where $|u\_{i}\\rangle\\overset{def}{=}\\frac{1}{\\sqrt{n\_{i}}}\\sum\_{x\_{j} \\in f^{- 1}{\\{ y\_{i}\\}}}|x\_{j}\\rangle$, *n*[*i*] = |*f*^( − 1){*y*[*i*]}|, the |*v*[*k*]⟩ are an ON basis for the orthogonal complement of the space spanned by the |*u*[*i*]⟩, and the |*w*[*k*]⟩ are an ON basis for ℋ(*Ω*^′)^⊥.

### 2.3.4 Arbitrary functions

In the preceding, we have assumed for convenience that the function is either non-injective or non-surjective, but not both. The solutions are easily extended to arbitrary functions, since every function can be factored as a composition of an injection and a surjection. More directly, we can combine Prop. 3 to implement a surjection onto its range with Prop. 2 to inject its range into its codomain.

Let the domain *Ω* = {*x*[1],…,*x*[*n*]}, where *n* = |*Ω*|, and let {|*x*[1]⟩,…,|*x*[*n*]⟩} be the standard basis of ℋ(*Ω*). Let *x*[0]∉ Ω be an additional value and define the extended domain *Ω*^∘ = {*x*[0]} ∪ *Ω*. Then ℋ(*Ω*^∘) has basis {|*x*[0]⟩,|*x*[1]⟩, …, |*x*[*n*]⟩}. (For example, ℋ(*Ω*^∘) may be the state space of *N* qubits, where *n *+ 1 = 2*^N*.) The additional *x*[0] input dimension will carry the null space “garbage” from previous computations. Similarly, let the codomain *Ω*^′ = {*y*[1],…,*y*[*m*]}, where *m* = | *Ω*^′|, and let {|*y*[1]⟩,…,|*y*[*m*]⟩} be the standard basis of ℋ(*Ω*^′). Let *y*[0] ∉ *Ω*^′ be an additional value and define the extended codomain *Ω*^(\*) = {*y*[0]} ∪ *Ω*^′. Then ℋ(*Ω*^(\*)) has basis {|*y*[0]⟩,|*y*[1]⟩, …, |*y*[*m*]⟩}. The *y*[0] component carries the garbage in the output state.

Let $\\left\\{ {r\_{1},\\ldots,r\_{m\_{r}}} \\right\\}\\overset{def}{=}{Im\\ }f$ and $\\left\\{ {z\_{1},\\ldots,z\_{m\_{nr}}} \\right\\}\\overset{def}{=}\\Omega^{\\prime}\\smallsetminus{Im}f$ be the range of *f* and its complement, respectively; since every codomain element is either a range element or not, *n* = *m*[*r*] + *m*[*n**r*]. As before, an *n*\-dimensional input |*x*[*j*]⟩ will be projected into orthogonal subspaces (the nonnull and null spaces) of dimension *m*[*r*] and *n*[*o*] = *n* − *m*[*r*], with basis vectors |*u*[*i*]⟩, *i* = 1, …, *m*[*r*], and |*v*[*k*]⟩, *k* = 1, …, *n*[*o*], respectively.

An additional input quantum register will be used to provide the constant zero amplitudes for non-range elements for non-surjective functions. The *m* + 1 dimensional state of this ancillary register will be in, for convenience, ℋ[*C*] = ℋ(*Ω*^(\*)) with basis {|*y*[0]⟩,|*y*[1]⟩, …, |*y*[*m*]⟩}. There will also be an additional output quantum register to hold the null space garbage for non-injective functions. Its *n* + 1 dimensional state is in, for convenience, ℋ[*G*] = ℋ(*Ω*^∘) with basis {|*x*[0]⟩,|*x*[1]⟩, …, |*x*[*n*]⟩}. Note that both the input and output spaces have dimension (*m*+1)(*n*+1). This is because the ancillary input register is in the same space as the regular output register, and the ancillary output register is in the same space as the regular input register. This can be confusing because, as will be seen, we use the extra *output* vector |*y*[0]⟩ as a constant in the ancillary *input* register, and the extra *input* vector |*x*[0]⟩ appears in the ancillary *output* register.

Our goal is to define unitary *U* ∈ ℒ\[ℋ(*Ω*^∘) ⊗ ℋ[*C*], ℋ(*Ω*^(\*)) ⊗ ℋ[*G*]\] so that

(2.17)*U*\[(*s*|*x*[*j*]⟩ + *t*|*x*[0]⟩) ⊗ |*y*[0]⟩\] = (*s*^′|*f*(*x*[*j*]⟩) + *t*^′|*y*[0]⟩) ⊗ |*γ*⟩, 

for scalars *s*, *s*^′, *t*, *t*^′ and for |*γ*⟩ ∈ ℋ[*G*]. That is, the input register is initialized to the input |*x*[*j*]⟩ with some positive amplitude *s*, possibly with superimposed garbage with amplitude *t*; the ancillary input register is initialized to constant |*y*[0]⟩. After computation, the output register will contain the function’s value |*f*(*x*[*j*])⟩ with some positive amplitude *s*^′; and superimposed garbage with amplitude *t*^′. The ancillary output register may also contain garbage. In other words, the argument to *f* is in the first input register \[corresponding to ℋ(*Ω*^∘)\], and its result is in the first output register \[corresponding to  ℋ(*Ω*^(\*))\], possibly with garbage in both its input |*x*[0]⟩ component and its output |*y*[0]⟩ component. The input ancillary register is initialized to a constant |*y*[0]⟩.

The work of computing *f* is done by the graph kernel *M*, which will map the |*u*[*i*]⟩|*y*[0]⟩ vectors into corresponding (*m*+1)(*n*+1) dimensional result vectors |*r*[*i*]⟩|*x*[0]⟩ in the output space ℋ(*Ω*^(\*)) ⊗ ℋ[*G*]. (The ancillary |*x*[0]⟩ ∈ ℋ[*G*] output is required so that the input and output spaces have the same dimension.) To accomplish this mapping, define *M* as follows:

(2.18)$M\\,\\overset{def}{=}\\,\\sum\\limits\_{i = 1}^{m\_{r}}\\left| {r\_{i},x\_{0}} \\right.\\rangle\\langle\\left. {u\_{i},y\_{0}} \\right|.$ 

It maps *m*[*r*] of the basis vectors of ℋ(*Ω*^∘) ⊗ ℋ[*C*] into *m*[*r*] of the basis vectors of ℋ(*Ω*^(\*)) ⊗ ℋ[*G*] (see [Figure 2.2](#bodymatter-002.xhtml#b_9783110670707-002_fig_002)). Specifically it is a bijection between the nonnull subspace of ℋ(*Ω*^∘) ⊗ ℋ({|*y*[0]⟩}) and the output subspace of ℋ(*Ω*^(\*)) ⊗ ℋ({|*x*[0]⟩}).

![Figure 2.2: Permutation of basis vectors to implement arbitrary function. After each component of the kernel, the number of basis vectors that it maps is indicated in parentheses. For example, R maps mn basis vectors. The shapes labeled u\_{i} and v\_{k} represent projection onto the basis vectors of the nonnull and null spaces, respectively.](graphic/converted/b_9783110670707-002_fig_002.jpg)

Figure 2.2: Permutation of basis vectors to implement arbitrary function. After each component of the kernel, the number of basis vectors that it maps is indicated in parentheses. For example, *R* maps *mn* basis vectors. The shapes labeled *u*[*i*] and *v*[*k*] represent projection onto the basis vectors of the nonnull and null spaces, respectively.

Another component of the transform will map the *n*[*o*] null space basis vectors |*v*[*k*]⟩|*y*[0]⟩ of the *m* + 1 dimensional |*y*[0]⟩ subspace of the input space:

(2.19)$N\\,\\overset{def}{=}\\,\\sum\\limits\_{k = 1}^{n\_{o}}\\left| {y\_{0},x\_{k}\\rangle\\langle\\left. {v\_{k},y\_{0}} \\right|} \\right..$ 

It maps them to *n*[*o*] of the basis vectors |*y*[0],*x*[*k*]⟩ of the *m* + 1 dimensional |*y*[0]⟩ subspace of the output space. *M* and *N* together handle non-injective functions by mapping *m*[*r*] + *n*[*o*] = *n* basis vectors.

For non-surjective functions, zero amplitudes are copied from the ancillary register |*x*[0]⟩|*y*[*i*]⟩ into the appropriate non-range codomain components |*z*[*i*]⟩|*x*[0]⟩:

(2.20)$S\\,\\overset{def}{=}\\,\\sum\\limits\_{i = 1}^{m\_{nr}}\\left| {z\_{i},x\_{0}} \\right.\\left. {\\rangle\\langle x\_{0},y\_{i}} \\right|.$ 

This is a mapping of *m*[*n**r*] basis vectors between the |*x*[0]⟩ subspaces of the input and output spaces. The three operators *M, N, S* handle the mapping of *f* (and disposal of the null space).

We have to be careful, however, to handle all the |*x*[0]⟩|*y*[*i*]⟩ basis vectors since *m*[*n**r*] might be less than *n* (see [Figure 2.2](#bodymatter-002.xhtml#b_9783110670707-002_fig_002)). We map the remaining basis vectors of the |*x*[0]⟩ subspace that were not used in the *S* map to components of the |*y*[0]⟩ subspace that are unfilled by *N*:

(2.21)$Q\\,\\overset{def}{=}\\,\\sum\\limits\_{k = 1}^{m\_{r}}\\left| {y\_{0},x\_{n\_{o} + k}\\rangle\\langle\\left. {x\_{0},y\_{m\_{nr} + k}} \\right|} \\right..$ 

Note that *n*[*o*] + *m*[*r*] = *n* = *m*[*n**r*] + *m*[*r*] so that all these vectors are bijectively mapped.

It remains to handle the other basis vectors of the input space in a unitary way. The preceding maps have either |*x*[0]⟩ or |*y*[0]⟩, but not both, in the input register. The *R* operator maps the *m**n* basis vectors with neither, |*x*[*j*]⟩|*y*[*i*]⟩, for *i*, *j* ≠ 0, into their reverses:

(2.22)$R\\,\\overset{def}{=}\\,\\sum\\limits\_{i = 1}^{m}\\sum\\limits\_{j = 1}^{n}\\left| {y\_{i},x\_{j}\\rangle\\langle} \\right.\\left. {x\_{j},y\_{i}} \\right|.$ 

The state |*x*[0]⟩|*y*[0]⟩ remains, and it maps to its reverse:

(2.23)$P\\,\\overset{def}{=}\\,\\left| {y\_{0},x\_{0}\\rangle\\langle\\left. {x\_{0},y\_{0}} \\right|} \\right..$ 

In summary, *M* bijectively maps *m*[r] basis vectors, *N* maps *n*[o] basis vectors, *S* maps *m*[nr], *R* maps *mn*, *Q* maps *m*[r], and *P* maps one basis vector, which accounts for all of the (*n *+ 1)(*m *+ 1) basis vectors (see [Figure 2.2](#bodymatter-002.xhtml#b_9783110670707-002_fig_002)):

$\\begin{matrix} {m\_{r} + n\_{o} + m\_{nr} + mn + m\_{r} + 1} & {= \\left( {m\_{r} + n\_{o}} \\right) + \\left( {m\_{nr} + m\_{r}} \\right) + mn + 1} \\\\ & {= n + m + mn + 1 = \\left( {m + 1} \\right)\\left( {n + 1} \\right).} \\\\ \\end{matrix}$ 

The unitary operator to compute *f* is the sum of these linear maps \[[eqs. (2.18)](#bodymatter-002.xhtml#b_9783110670707-002_eq_018)–([2.23](#bodymatter-002.xhtml#b_9783110670707-002_eq_023))\]:

(2.24)$U\\;\\overset{def}{=}\\; M + N + S + R + Q + P.$ 

#### Proposition 4

Suppose *f*: *Ω* → *Ω*^′. Let *n* = |*Ω*| and *m* = |*Ω*^′|. Let ℋ(*Ω*^∘) be an *n* + 1 dimensional Hilbert space with basis {|*x*[0]⟩,…,|*x*[*n*]⟩}, and let ℋ(*Ω*^(\*)) be an *m* + 1 dimensional space with basis {|*y*[0]⟩,…,|*y*[*m*]⟩}. Then there a unitary operator *U* ∈ ℒ\[ℋ(*Ω*^∘) ⊗ ℋ(*Ω*^(\*)), ℋ(*Ω*^(\*))⊗ℋ(*Ω*^∘)\] so that for scalars *s*, *t* (with |*s*|² + |*t*|² = 1) and *x* ∈ *Ω*:

(2.25)*U*\[(*s*|*x*⟩+*t*|*x*[0]⟩)⊗|*y*[0]⟩\] = *s**s*^′|*f*(*x*), *x*[0]⟩ + *t*^′|*y*[0], *γ*⟩, 

where $s^{\\prime}\\;\\overset{def}{=}\\; n\_{x}^{- 1/2}$, where *n*[*x*] = |*f*^( − 1){*f*(*x*)}|, and |*s**s*^′|² + |*t*^′|² = 1.

#### Proof:

By construction \[[eqs. (2.18)](#bodymatter-002.xhtml#b_9783110670707-002_eq_018) and ([2.19](#bodymatter-002.xhtml#b_9783110670707-002_eq_019))\] we know:

$\\begin{matrix} {U\\left| {{x\_{j},y\_{0}}\\rangle} \\right.} & {= \\left( {M + N} \\right)\\left| {{x\_{j},y\_{0}}\\rangle} \\right.} \\\\ & {= \\left( {\\sum\\limits\_{i = 1}^{m\_{r}}\\left| {r\_{i},x\_{0}\\rangle} \\right.\\langle\\left. {u\_{i},y\_{0}} \\right|} \\right)\\left| {x\_{j},y\_{0}\\rangle} \\right. + \\left( {\\sum\\limits\_{k = 1}^{n\_{o}}\\left| {y\_{0},x\_{k}\\rangle\\langle} \\right.\\left. {v\_{k},y\_{0}} \\right|} \\right)\\left| {x\_{j},y\_{0}} \\right.\\rangle} \\\\ & {= \\left| {f\\left( x\_{j} \\right),x\_{0}} \\right.\\rangle\\langle u\_{i}|x\_{j}\\rangle + \\left| {y\_{0}\\rangle} \\right.\\sum\\limits\_{k = 1}^{n\_{o}}\\left| {x\_{k}\\rangle\\langle} \\right.v\_{k}|x\_{j}\\rangle} \\\\ & {= s\_{j}\\left| {f\\left( x\_{j} \\right),x\_{0}\\rangle} \\right. + \\left| {y\_{0},\\gamma} \\right.\\rangle,} \\\\ \\end{matrix}$ 

where $\\left| {\\gamma\\rangle} \\right. = \\left( {\\sum\_{k = 1}^{n\_{o}}|{x\_{k}\\rangle\\langle\\left. v\_{k} \\right|}} \\right)\\left| {x\_{j}\\rangle} \\right.$ and $||\\,|y\_{0},\\gamma\\rangle|| = \\sqrt{n\_{j} - 1}/\\sqrt{n\_{j}}$. Furthermore, by [eq. (2.23)](#bodymatter-002.xhtml#b_9783110670707-002_eq_023),

*U*|*x*[0], *y*[0]⟩ = *P*|*x*[0], *y*[0]⟩ = |*y*[0], *x*[0]⟩. 

Therefore, in the general case where the input register is *s*|*x*[*j*]⟩ + *t*|*x*[0]⟩ (with |*s*|² + |*t*|² = 1) we have:

$\\begin{matrix} {U\\left\\lbrack {\\left( {s\\left| x\_{j} \\right.\\rangle + t\\left| x\_{0} \\right.\\rangle} \\right) \\otimes \\left| {y\_{0}\\rangle} \\right.} \\right\\rbrack} & {= sU\\left| {x\_{j},y\_{0}} \\right.\\rangle + tU\\left| {x\_{0},y\_{0}} \\right.\\rangle} \\\\ & {= s\\left( {s\_{j}\\left| {f\\left( x\_{j} \\right),x\_{0}\\rangle} \\right. + \\left| {y\_{0},\\gamma\\rangle} \\right.} \\right) + t\\left| {y\_{0},x\_{0}\\rangle} \\right.} \\\\ & {= ss\_{j}\\left| {f\\left( x\_{j} \\right),x\_{0}\\rangle} \\right. + \\left| {y\_{0}\\rangle} \\right.\\left( {s\\left| {\\gamma\\rangle} \\right. + t\\left| {x\_{0}\\rangle} \\right.} \\right).} \\\\ \\end{matrix}$ 

As a consequence, the result that we want is in the first \[ℋ(*Ω*^(\*))\] quantum register, but its |*y*[0]⟩ component is garbage and should be ignored in subsequent computations. Furthermore, the amplitude of the desired result will decrease through successive computation stages as a result of attenuation by successive $1/\\sqrt{n\_{j}}$ factors.

As discussed previously, quantum states with |*x*[*j*]⟩ components with positive amplitudes represent sets of the corresponding *x*[*j*] (*j* ≠ 0). Applying *U* to such a state yields a quantum state with positive amplitudes for the corresponding |*f*(*x*[*j*])⟩, which represents the set of corresponding outputs *f*(*x*[*j*]). Thus, *U* can be applied to a (crisp) set of values with quantum parallelism.

## 2.4 Topographic qubit maps

### 2.4.1 Representation

To further explore quantum computation by topographic maps, in this section we present an alternative representation of the maps and a circuit-based implementation of arbitrary functions on a finite domain. In these *topographic qubit maps*, each domain value *x*[*j*] ∈ *Ω* = {*x*[1],…,*x*[*n*]} or codomain value *y*[*i*] ∈ *Ω*^′ = {*y*[1],…,*y*[*m*]} is assigned a separate qubit, whose state, for example, |*ψ*[*j*]⟩ = *p*[*j*]^′|0⟩ + *p*[*j*]|1⟩, where |*p*[*j*]^′|² + |*p*[*j*]|² = 1, represents the activity level of neuron *x*[*j*] by the amplitude *p*[*j*]. This topographic representation can be contrasted with a binary representation such as that proposed by Chen, Wang, and Charbon \[[17](#bodymatter-002.xhtml#b_9783110670707-002_ref_017)\]. Our one-out-of-*n* (or “one-hot”) representation might seem unrealistically inefficient, but (1) we are assuming a scalable qubit implementation, which permits arrays of many thousands of qubits, and (2) neural computations typically require only low precision \[in the brain perhaps as little as one digit: \[[18](#bodymatter-002.xhtml#b_9783110670707-002_ref_018)\]\]. Therefore a quantity can be represented by a few tens of qubits; that is, our *m* and *n* will typically be small (*m, n < *100).

Like the topographic basis maps, these topographic qubit maps can also be viewed as representations of subsets of the domain; for *S* ⊆ Ω:

$\\left| {S\\rangle} \\right. = \\sum\\limits\_{x\_{j} \\in S}\\left| {1\\rangle}\_{j} \\right. + \\sum\\limits\_{x\_{j} \\notin S}\\left| {0\\rangle}\_{j} \\right..$ 

That is, the *x*[*j*] qubit is in state |1⟩ if *x*[*j*] is in *S* and is in state |0⟩ if it is not. Therefore we use the notation |{*x*[*j*]}⟩ for the topographic map representing just the number *x*[*j*]. The set of representations of all possible subsets of Ω is then an ON basis for the 2*^n*\-dimensional Hilbert space of these qubits. The basis can be written:

{|*k*⟩|*k*∈2^(*n*)} = {|*S*⟩|*S*⊆2^(*Ω*)}, 

where on the left **2***^n* is the set of *n*\-bit binary strings, and on the right **2**^Ω is the powerset of Ω. Therefore, the sets are basis states and as a consequence topographic qubit maps permit *multiple* sets to be processed in quantum superposition. Moreover, because the sets are represented by computational basis vectors, they can be copied without violating the no-cloning theorem.

By using amplitudes other than 0 and 1, we can represent fuzzy sets. Suppose *S* is a fuzzy set with membership function *µ*: *S* → \[0, 1\], and let *m[j] *\= *µ*(*x[j]*). Then *S* is represented by the topographic qubit map

$|S\\rangle = \\sum\\limits\_{j = 1}^{n}m\_{j}|1\\rangle\_{j} + \\sqrt{1 - m\_{j}^{2}}\\ |0\\rangle\_{j}.$ 

Fuzzy sets cannot, in general, be copied (nor can arbitrary superpositions of crisp sets).

With the topographic qubit representation, the transformations between computational maps will be implemented by the quantum circuit model, and so one might ask whether it would be simpler to implement ordinary binary digital quantum computation. The answer is that computation on topographic maps can be implemented by a few relatively simple operations (described in the following subsections), so that computational maps buy a simpler quantum implementation at the cost of greater representational expense (number of qubits). We expect topographic quantum computation to be more simply implemented than a full-scale digital quantum arithmetic-logic unit.

### 2.4.2 Unary functions

An example will illustrate how to implement an arbitrary finite function *f*: *Ω* → *Ω*^′ by a unitary operator on topographic qubit maps. For any *y*[*i*] not in the range of *f*, we set its state |*ϕ*[*i*]⟩ = |0⟩ supplied as an ancilla. If *y*[*i*] is in the range of *f*, then it might be the image of a single domain element, *x*[*j*], that is, *y*[*i*] = *f*(*x*[*j*]), in which case we implement directly |*ϕ*[*i*]⟩ = |*ψ*[*j*]⟩, transferring the state |*ψ*[*j*]⟩ of input qubit *j* to output qubit *i*. If there are two domain values mapping into *y*[*i*], say *f*(*x*[*j*]) = *y*[*i*] = *f*(*x*[*k*]), then we make |*ϕ*[*i*]⟩ the logical OR of |*ψ*[*j*]⟩ and |*ψ*[*k*]⟩. This is accomplished with the two-input OR[2] gate:

(2.26)$OR\_{2}\\overset{def}{=}{CCNOT}\\left( {X\\, \\otimes \\, X\\, \\otimes \\, I} \\right),$ 

where CCNOT is the conditional-conditional-not or Toffoli gate. The result of ORing the input states is:

(2.27)*O**R*[2](|*ψ*[*j*]⟩ ⊗ |*ψ*[*k*]⟩ ⊗ |1⟩) = *X*|*ψ*[*j*]⟩ ⊗ *X*|*ψ*[*k*]⟩ ⊗ |*ϕ*[*i*]⟩. 

The |1⟩ input is a constant ancilla. The result of the OR is in the third output qubit, and the first two output qubits, in which the negated inputs remain, are considered garbage. If |*ψ*[*j*]⟩ = *p*^′|0⟩ + *p*|1⟩ and |*ψ*[*k*]⟩ = *q*^′|0⟩ + *q*|1⟩, then OR[2] transfers the probability amplitudes as follows:

$\\begin{matrix} {OR\_{2}\\left| \\psi\_{j} \\right.\\rangle\\left| {\\psi\_{k}\\rangle} \\right.\\left| {1\\rangle} \\right.} & {= OR\_{2}\\left( {p^{\\prime}\\left| {0\\rangle} \\right. + p\\left| {1\\rangle} \\right.} \\right)\\left( {q^{\\prime}\\left| {0\\rangle} \\right. + q\\left| {1\\rangle} \\right.} \\right)\\left| {1\\rangle} \\right.} \\\\ & {= \\ p^{\\prime}q^{\\prime}OR\_{2}\\left| {001\\rangle} \\right. + p^{\\prime}qOR\_{2}\\left| {011\\rangle} \\right. + pq^{\\prime}OR\_{2}\\left| {101\\rangle} \\right. + pqOR\_{2}\\left| {111\\rangle} \\right.} \\\\ & {= \\ p^{\\prime}q^{\\prime}|110\\rangle + p^{\\prime}q|101\\rangle + pq^{\\prime}|011\\rangle + pq|001\\rangle.} \\\\ \\end{matrix}$ 

Therefore, the third output qubit is the OR of the first two input qubits with the amplitudes shown. If we interpret the squares of the amplitudes as probabilities, then OR[2] computes the correct probabilities for the third output qubit. The first two output qubits are considered garbage but must be retained, for they are entangled with the third output.

If more than two domain values map into a single codomain value, then we use the multiple argument OR*[n]*, which can be defined recursively in terms of OR[2]:

(2.28)$OR\_{n}|\\psi\_{1}\\rangle\\cdots|\\psi\_{n}\\rangle|1\\rangle^{\\otimes {({n - 1})}}\\overset{def}{=}OR\_{n - 1}\\left\\lbrack {\\left( {OR\_{2}|\\psi\_{1}\\rangle|\\psi\_{2}\\rangle|1\\rangle} \\right) \\otimes |\\psi\_{3}\\rangle\\cdots|\\psi\_{n}\\rangle|1\\rangle^{\\otimes {({n - 2})}}} \\right\\rbrack\\quad(n > 2).$ 

For completeness, we define $OR\_{1}\\overset{def}{=}I$.

With the preceding motivation, we can give the construction for computing an arbitrary finite function by topographic qubit maps:

#### Proposition 5

Suppose *f*: *Ω* → *Ω*^′, where *Ω* = {*x*[1],…,*x*[*n*]} and *Ω*^′ = {*y*[1],…,*y*[*n*]}. Let $m\_{nr}\\overset{def}{=}n - \\left| {{Im\\,}f} \\right|$ be the number of codomain elements that are not in the range of *f*. Let *n*[b] be the number of injective domain elements, and let $n\_{n}\\;\\overset{def}{=}\\; n - n\_{b}$ be the number of non-injective domain elements. Let $m\_{n}\\overset{def}{=}\\left| {{Im\\,}f} \\right| - n\_{b}$ be the number of non-injective range elements (i.e., those that are the image of two or more domain elements). Then there is an 2*n*[*n*] + *n*[*b*] + *m*[*n**r*] − *m*[*n*] dimensional unitary operator *U[f]* that computes *f* by topographic qubit maps as follows:

(2.29)*U*[*f*] |{*x*}⟩ |0⟩^( ⊗ *m*[*n**r*]) |1⟩^( ⊗ (*n*[*n*] − *m*[*n*])) = |{*f*(*x*)}⟩|*γ*⟩, 

where |*γ*⟩ is 2(*n*[n] − *m*[n]) qubits of garbage.

#### Proof:

The inputs are the *n* elements of the input map, *m*[nr] constant |0⟩ ancillae (for the non-range elements), and *n*[n] − *m*[n] constant |1⟩ ancillae for the OR[2] gates that map multiple domain elements to the same range element. The latter are required because each of the non-injective range elements requires a number of OR[2] gates that is one less than the number of its preimages; hence the *m*[*n*] non-injective range elements require *n*[n] − *m*[n] OR[2] gates. Therefore there are

*n* + *m*[*n**r*] + *n*[*n*] − *m*[*n*] = (*n*[*b*]+*n*[*n*]) + *m*[*n**r*] + *n*[*n*] − *m*[*n*] = 2*n*[*n*] + *n*[*b*] + *m*[*n**r*] − *m*[*n*] 

input qubits. The *m*[nr] constant |0⟩s are passed directly to the output qubits for non-range codomain elements. The *n*[b] qubits for injective inputs are passed to the same number of output qubits, permuted as required. The outputs of the ORs project onto the *m*[n] qubits that represent range values with more than one preimage. Each OR[2] also generates two garbage qubits, for a total of 2(*n*[n] − *m*[n]). Therefore the total number of output qubits is

*m*[*n**r*] + *n*[*b*] + *m*[*n*] + 2(*n*[*n*]−*m*[*n*]) = 2*n*[*n*] + *n*[*b*] + *m*[*n**r*] − *m*[*n*], 

which is equal to the number of input qubits, as it should be. Next we define *U[f]* explicitly as the tensor product of three operators:

(2.30)$U\_{f}\\;\\overset{def}{=}\\; U\_{b} \\otimes U\_{nr} \\otimes U\_{n}.$ 

We will use the notation |1⟩[*q*] to represent a |1⟩ state in qubit *q*, and |0⟩[*q*] to represent a |0⟩ state in the qubit *q*.

The *U*[nr] operator is an identity operation copying constant |0⟩ ancillae into the codomain elements that are not in the range of *f*. Therefore, let {*c*[1],…, *c*[*m*[*n**r*]]} ⊆ *Ω*^′ − *I**m* *f* be this subset, and let |*z*[*i*]⟩ be ancillae qubits to provide constant |0⟩s. Then *U*[*n**r*] ∈ ℒ(ℋ^(*m*[*n**r*]),ℋ^(*m*[*n**r*])) is defined:

(2.31)$U\_{nr}\\;\\overset{def}{=}\\;\\sum\\limits\_{i = 1}^{m\_{nr}}\\left| {0\\rangle} \\right.\_{c\_{i}}\\langle 0|\_{z\_{i}} + \\left| {1\\rangle} \\right.\_{c\_{i}}\\langle 1|\_{z\_{i}}.$ 

That is, the states of the *z*[*i*] input qubits (intended to be |0⟩) are transferred to the *c*[*i*] output qubits. This operator can be abbreviated by the following bracket notation:

(2.32)$U\_{nr}\\overset{def}{=}\\left\\lbrack {c\_{1},\\ldots,c\_{m\_{nr}}} \\right\\rbrack\\leftarrow\\left\\lbrack {z\_{1},\\ldots,z\_{m\_{nr}}} \\right\\rbrack.$ 

It is just a permutation of the qubits, which could be implemented by qubit SWAP operations.

The *U*[b] operator handles the domain elements that are mapped injectively to their images. Therefore, let {*v*[1], …, *v*[*n*[*b*]]} ⊆ *I**m* *f* be the injective domain elements, and let *u[i] *\= *f* (*v[i]*) be the corresponding range elements. Then *U*[*b*] ∈ ℒ(ℋ^(*n*[*b*]),ℋ^(*n*[*b*])) is a permutation of this subset of the topographic map elements:

(2.33)$U\_{b}\\overset{def}{=}\\left\\lbrack {u\_{1},\\ldots,u\_{n\_{b}}} \\right\\rbrack\\leftarrow\\left\\lbrack {v\_{1},\\ldots,v\_{n\_{b}}} \\right\\rbrack.$ 

For *U*[n] we must OR together the domain elements that correspond to each range element with more than one preimage. Therefore we define *U*[*n*] as a tensor product of operators for each such range element:

(2.34)$U\_{n}\\;\\overset{def}{=}\\; \\otimes \\,\_{i = 1}^{m\_{n}}V\_{i}\\left( {y\_{i},f^{- 1}\\left\\{ y\_{i} \\right\\}} \\right),$ 

where these *y*[*i*] each have more than one preimage element; for example, *f*^( − 1){*y*[*i*]} = {*x*[1],…, *x*[*n*[*i*]]}, where *n*[*i*] = |*f*^( − 1){*y*[*i*]}| ≥ 2. The output state |*ψ*[*i*]⟩ for such a range element is the OR of the input states |*ξ*[*j*]⟩ (*j* = 1, …, *n*[*i*]) of its preimage elements:

|*ψ*[*i*]⟩|*γ*⟩ = *O**R*[*n*[*i*]]|*ξ*[1]⟩⋯|*ξ*[*n*[*i*]]⟩|1⟩^( ⊗ (*n*[*i*] − 1)), 

where *O**R*[*n*[*i*]] is a cascade of *n*[*i*] − 1 *O**R*[2] gates and |*γ*⟩ is 2(*n*[*i*] − 1) dimensional garbage. This is accomplished by the operators *V*[*i*](*y*[*i*],{*x*[1],…, *x*[*n*[*i*]]}) ∈ ℒ(ℋ^(2*n*[*i*] − 1),ℋ^(2*n*[*i*] − 1)):

(2.35)$V\_{i}\\left( {y\_{i},\\left\\{ {x\_{1},\\ldots,\\ x\_{n\_{i}}} \\right\\}} \\right)\\overset{def}{=}\\left\\lbrack {y\_{i},\\gamma\_{1},\\ldots,\\ \\gamma\_{2{({n\_{i} - 1})}}} \\right\\rbrack\\leftarrow OR\_{n\_{i}}\\ \\left\\lbrack {x\_{1},\\ldots,\\ x\_{n\_{i}};\\ o\_{1},\\ldots,\\ o\_{n\_{i} - 1}} \\right\\rbrack,$ 

where *o*[1], …, *o*[*n*[*i*] − 1] are the qubits that provide ancillary |1⟩s for the ORs, and the garbage outputs *γ*[1], …, *γ*[2(*n*[*i*] − 1)] receive the negated inputs and intermediate OR outputs. The bracket notation identifies the qubits that are the inputs and outputs of *O**R*[*n*[*i*]]. This completes the construction of *U*[*f*] \[[eq. (2.29)](#bodymatter-002.xhtml#b_9783110670707-002_eq_029)\].

There are more efficient ways to compute *U[f]*, but the above construction is easier to understand. This basic approach can be used to approximate a variety of unary functions useful in neural networks, such as sigmoid functions, including non-injective, non-surjective squashing functions. However, neural networks also require non-unary functions such as addition and multiplication, to which we now turn.

### 2.4.3 Binary functions

In sensory cortical areas there are many topographic maps that represent two or more dimensions of a stimulus (e.g., retinal position and edge orientation); localized activity in these maps represent conjunctions of values on these dimensions. Similarly, quantum computational maps can represent conjunctions of values as inputs or outputs of functions.

Suppose we want to compute a function *f* : *Ω* × *Ω* → *Ω*^′, where *Ω* = {*x*[1],…,*x*[*n*]} and *Ω*^′ = {*y*[1],…,*y*[*n*]}. We will represent the input to the function by a two-dimensional array of qubits for each (*x[j], x[k]*) pair. (They do not have to be physically arranged as a two-dimensional array so long as there is a qubit for each pair of values.) This will require *n*² qubits, but we are assuming that *n* is small because low precision is adequate for neural networks. Therefore we expect the 2D map to comprise typically several thousand qubits. The qubits representing the (*x[j], x[k]*) pairs are then mapped to the qubits representing the outputs *f* (*x[j], x[k]*) by the method described in Prop. 5.

The *n*² conjunctions are computed by *n*² CCNOT gates, each of which requires a |0⟩ ancilla and generates two extra qubits (containing the inputs) in addition to the conjunction. However, these extra qubits are passed along the rows and columns to be used in other conjunctions, and so there are only 2*n* total garbage qubits. In summary, there are 2*n* + *n*² input qubits (including *n*² ancillae) and *n*² + 2*n* output qubits (including 2*n* garbage). That is, if |*ϕ*[*j*]⟩ is the state of element *j* of one input map, and |*ψ*[*k*]⟩ is the state of element *k* of the other input map, then the state |*χ*[*j**k*]⟩ of element (*j, k*) of the two-dimensional map is computed by

(2.36)|*ϕ*[*j*]⟩|*ψ*[*k*]⟩|*χ*[*j**k*]⟩ = *C**C**N**O**T*|*ϕ*[*j*]⟩|*ψ*[*k*]⟩|0⟩. 

*I**f* |*ϕ*[*j*]⟩ = *p*^′|0⟩ + *p*|1⟩ and |*ψ*[*k*]⟩ = *q*^′|0⟩ + *q*|1⟩, then the result of CCNOT is

|*ϕ*[*j*]⟩|*ψ*[*k*]⟩|*χ*[*j**k*]⟩ = *p*^′*q*^′|000⟩ + *p*^′*q*|100⟩ + *p**q*^′|010⟩ + *p**q*|111⟩. 

The qubits are entangled, but the conjunction computes probability-like amplitudes if we interpret the squares of the amplitudes as probabilities.

Based on the foregoing, we define a unitary operator *U*[OP] on a *n*² + 2*n* dimensional Hilbert space that does what amounts to an outer product on two one-dimensional maps to compute a two-dimensional map:

(2.37)|*φ*⟩|*ψ*⟩|*χ*⟩ = *U*[*O**P*] |*φ*⟩|*ψ*⟩|0⟩^( ⊗ *n*²), 

where inputs |*φ*⟩ and |*ψ*⟩ are *n*\-dimensional, and output |*χ*⟩ is *n*²\-dimensional and computed by [eq. (2.36)](#bodymatter-002.xhtml#b_9783110670707-002_eq_054).

To illustrate the use of computational maps to implement binary operations, we will use a simple, useful function, addition. We want to define *s**u**m* : *Ω* × *Ω* → *Ω*^′ so that *s**u**m*(*x*, *y*) = *x* + *y*, but we have a problem, since the maximum value of *x* + *y* is greater than the maximums of *x* and *y*. Since the range of numbers represented by our maps is quite limited, this is a more serious problem than overflow in binary addition. One solution is to make the codomain map large enough; for example, if *Ω* = {0,*Δ**x*,2*Δ**x*,…, (*n*−1)*Δ**x*}, then let *Ω*^′ = {0,*Δ**x*,2*Δ**x*,…,2(*n*−1)*Δ**x*}. Generally, however, it is more convenient to have the codomain map be the same as the domain maps, since this facilitates composing functions. Therefore, another solution is to scale either the inputs or the output so that we compute, for example, h*s**u**m*(*x*, *y*) = (*x*+*y*)/2; this is often useful if we know that we are going to scale the quantities anyway. A third option is to compose addition with a squashing function, so that we compute, for example, the truncated tsum(*x*, *y*) = min (*x*+*y*, *x*[*n*]), where *x*[*n*] = max *Ω*. This is the solution that we will use for illustration.

If *Ω* = {0,*Δ**x*,…,(*n*−1)*Δ**x*}, then the (*j, k*) element of the two-dimensional qubit map will represent the pair of inputs ((*j*−1)*Δ**x*,(*k*−1)*Δ**x*). This will be mapped to the sum (*j*+*k*−2)*Δ**x* if *j* + *k* − 2 < *n* − 1, and to the maximum value (*n*−1)*Δ**x* otherwise. Therefore the constant *j* + *k* anti-diagonals above the *j* + *k* = *n* + 1 anti-diagonal each map to one value, (*j*+*k*−2)*Δ**x*, which is the sum of (*j*−1)*Δ**x* and (*k*−1)*Δ**x*. The elements below the  *j* + *k* = *n* + 1 anti-diagonal all map to the same (*n*−1)*Δ**x* value, since the sum is above the maximum representable value in the topographic map.

Proposition 5 shows how to implement the truncated addition, but it treats it as a unary function on an *n*²\-dimensional space, which is wasteful since the intended output (the sum) is *n*\-dimensional and the remaining *n*² − *n* elements are garbage. Therefore, we implement a unitary operator that directly maps the input pairs to the corresponding outputs.

To compute the outer product we require *n*² constant |0⟩ ancillae, and this computation also passes the two *n*\-dimensional inputs through as garbage output. The qubit representing (0, 0) maps bijectively to the output qubit *y*[1] representing 0. Each of the other *n* − 1 output qubits *y*[*i*] (*i* = 2, …, *n*) has two or more domain pairs mapping to it. As before, let *n*[*i*] be the preimage multiplicity of output *i* and note that $\\sum\_{i = 1}^{n}n\_{i} = n^{2}$. Each of these non-injective outputs receives its value from an *O**R*[*n*[*i*]] operation, which requires *n*[*i*] − 1 input |1⟩ ancillae and generates 2*n*[*i*] − 2 qubits of output garbage (*n*[*i*] for the negated inputs and *n*[*i*] − 1 for the intermediate disjunctions). Therefore, the total number of |1⟩ ancillae is

$\\sum\\limits\_{i = 2}^{n}\\left( {n\_{i} - 1} \\right) = \\sum\\limits\_{i = 2}^{n}n\_{i} - \\left( {n - 1} \\right) = \\left( {n^{2} - 1} \\right) - n + 1 = n^{2} - n.$ 

Moreover, the complete input dimension is 2*n* + *n*² + *n*² − *n* = 2*n*² + *n*.

This is also the complete output dimension, for we have *n* qubits for the function value, 2*n* qubits for the passed-through input arguments (garbage), and the garbage output from the OR gates, which is:

$\\sum\\limits\_{i = 2}^{n}\\left( {2n\_{i} - 2} \\right) = 2\\left( {n^{2} - n} \\right).$ 

That is, the complete output dimension is 3*n* + 2(*n*²−*n*) = 2*n*² + *n*.

In summary, there is a unitary operator *U*[*t**s**u**m*] ∈ ℒ(ℋ^(2*n*² + *n*),ℋ^(2*n*² + *n*)) so that

(2.38)*U*[*t**s**u**m*] |{*x*}⟩ |{*y*}⟩ |0⟩^( ⊗ *n*²) |1⟩^( ⊗ *n*(*n* − 1)) = |{*t**s**u**m*(*x*, *y*)}⟩ |{*x*}⟩ |{*y*}⟩ |*γ*⟩, 

where the garbage |*γ*⟩ has dimension 2*n*(*n*−1) (the passed-through inputs may also be considered garbage).

Based on this example, we state a more general result.

#### Proposition 6

Suppose *f* : *Ω* × *Ω* → *Ω*, and let *n* = |*Ω*|. Let $m\_{nr}\\overset{def}{=}n - \\left| {{Im\\,}f} \\right|$ be the number of codomain elements that are not in the range of *f*. Then there is a unitary operator *U*[*f*] ∈ ℒ(ℋ,ℋ), where ℋ is 2*n*² + *n* + 2*m*[*n**r*] dimensional Hilbert space, such that:

(2.39)*U*[*f*] |{*x*}⟩ |{*y*}⟩ |0⟩^( ⊗ (*n*² + *m*[*n**r*])) |1⟩^( ⊗ (*n*² − *n* + *m*[*n**r*])) = |{*f*(*x*, *y*)}⟩ |{*x*}⟩ |{*y*}⟩ |*γ*⟩, 

where the garbage |*γ*⟩ has dimension 2(*n*²−*n*+*m*[*n**r*]) (the 2*n* passed-through inputs may also be considered garbage).

#### Proof:

The operator is constructed very similarly to *U*[*t**s**u**m*], but we also have to consider non-range codomain elements for non-surjective functions, which didn’t occur in that case. As before, the computation of the outer product will require *n*² ancillary |0⟩ inputs and it will generate 2*n* qubits containing the passed-through inputs. We can consider disjoint subsets of the codomain. Codomain elements that are not in the range of *f* will need to be sent a |0⟩ state, for which we need an additional *m*[*n**r*] ancillary |0⟩ inputs. Let *n*[*b*] be the number of input pairs that are mapped one-to-one to the corresponding outputs; they neither require ancillary constants nor generate garbage. The remaining codomain elements are range elements with *n*[*i*] ≥ 2; let *m*[*n*] = *n* − *m*[*n**r*] − *n*[*b*] be the number of them. Each of these will receive the OR of the corresponding (preimage) domain elements. As we saw previously, the *O**R*[*n*[*i*]] operation requires *n*[*i*] − 1 ancillary |1⟩ qubits and produces 2*n*[*i*] − 2 qubits of garbage. Therefore, the total number of |1⟩ qubits required for the *n*² − *n*[*b*] input pairs mapping to the *m*[*n*] non-injectively mapped range elements is:

(2.40)$\\sum\\limits\_{i = 1}^{m\_{n}}\\left( {n\_{i} - 1} \\right) = \\sum\\limits\_{i = 1}^{m\_{n}}n\_{i} - m\_{n} = n^{2} - n\_{b} - m\_{n} = n^{2} - n + m\_{nr},$ 

since *m*[*n*] = *n* − *m*[*n**r*] − *n*[*b*]. The garbage generated by the ORs is then

(2.41)$\\sum\\limits\_{i = 1}^{m\_{n}}\\left( {2n\_{i} - 2} \\right) = 2\\left( {n^{2} - n + m\_{nr}} \\right).$ 

The complete input dimension is 2*n* (arguments) + (*n*² + *m*[*n**r*]) (for |0⟩ ancillae) + (*n*² − *n* + *m*[*n**r*]) \[for |1⟩ ancillae, [eq. (2.40)](#bodymatter-002.xhtml#b_9783110670707-002_eq_040)\] ​ = 2*n*² + *n* + 2*m*[*n**r*]. The output dimension is 3*n* (arguments and result) + 2(*n*²−*n*+*m*[*n**r*]) \[garbage, [eq. (2.41)](#bodymatter-002.xhtml#b_9783110670707-002_eq_041)\] ​ = 2*n*² + *n* + 2*m*[*n**r*].

The same approach can be used for operations with more than two arguments, but the number of qubits increases exponentially with the number of arguments.

## 2.5 Conversions between representations

Ordinary binary representations can be translated to topographic qubit maps by a unitary demultiplexer *U*[demux] that operates on an *m*\-qubit binary number |*k*⟩ and directs a |1⟩ qubit to the *k*^(th) of *n *\= 2*^m* output qubits (the remainder receiving |0⟩). Let |{*k*}⟩ be the resulting computational qubit map. Then:

(2.42)*U*[*d**e**m**u**x*]|*k*⟩|1⟩|0⟩^( ⊗ (*n* − 1)) = |*k*⟩|{*k*}⟩. 

*U*[demux] operates on an *m* + *n* = *m* + 2^(*m*) dimensional Hilbert space. A demultiplexer can be implemented with CSWAP (Fredkin) gates \[[19](#bodymatter-002.xhtml#b_9783110670707-002_ref_019)\].

The opposite translation, from a computational map to a binary representation, is more complicated. First, we must decide what we want it to do, for in general a topographic qubit map represents multiple values with different amplitudes, $|{\\psi\\rangle = \\otimes\_{j = 1}^{n}({p\_{j}^{\\prime}\\left| {0\\rangle} \\right. + p\_{j}|{1\\rangle}})}$, where |*p*[*j*]^′|² + |*p*[*j*]|² = 1. Which *x[j]* should it produce? The one with the maximum amplitude? (And what if several have the same maximum amplitude?) An *x[j]* chosen probabilistically based on |*p*[*j*]|²? The binary representation of a weighted average, $n^{- 1}\\sum\_{j = 1}^{n}p\_{j}x\_{j}$? A normalized superposition of all the values? The answer is not apparent, so we leave the question open.[⁴](#fn4)

## 2.6 Applications to quantum machine learning

Given this general ability to compute non-unitary and even nonlinear functions by means of topographic qubit maps, it is possible to do the operations useful for machine learning such as inner products and sigmoid nonlinearities. For example, an inner product of *N*\-dimensional vectors requires *N* multiplications and *N* − 1 additions. If |Ω| = *n*, then each multiplication and addition will require approximately 2*n*² qubits (Prop. 6), for a total of approximately 2*N*²*n*².

For one layer of a neural network, with say *N* neurons projecting through an *M* × *N* weight matrix into *M* neurons, we must do *M* inner products with the input. Since crisp sets are represented by computational maps that are basis vectors in the computational basis, they can be copied. Therefore, the *N*\-dimensional input vector can be copied *M* − 1 times to do the *M* inner products. (This requires *M* − 1 CNOT gates and (*M*−1)*n* ancillary |0⟩ qubits. Overall, one layer requires about 2*M**N*²*n*² qubits for the computation (not including ancillary qubits).

## 2.7 Conclusions

Topographic (computational) maps are widely used in the brain to implement simultaneous nonlinear vector transformations on multiple inputs. In this chapter we have explored two approaches to quantum topographic computing with a focus on brain-inspired machine learning applications. The first, called a topographic basis map, assigns locations in the map to state vectors in a continuous or discrete basis for a quantum Hilbert space. Arbitrary functions can be implemented on such maps, which can be interpreted as representing crisp sets of inputs, but there is an unavoidable data-dependent attenuation of the result (relative to a “garbage” state) that is not easily avoidable. The second approach, called a topographic qubit map, assigns a separate qubit to each location in the map and uses the relative amplitude of the |1⟩ and |0⟩ states to represent the presence of values in the (crisp or fuzzy) set represented by the map. Arbitrary functions on these maps are implemented by well-known quantum logic gates. In particular, computational maps enable the implementation of the functions commonly used in artificial neural networks.

## References

\[1\]Nielsen, M. A. and Chuang, I. L. 2010. *Quantum computation and quantum information* (10th Anniversary Edition ed.). Cambridge, UK: Cambridge Univ. Press. [a](#bodymatter-002.xhtml#xref_d6256e3555), [b](#bodymatter-002.xhtml#xref_d6256e12665)

\[2\]Schuld, M., Sinayskiy, I., and Petruccione, F. 2014. The quest for a quantum neural network. *Quantum Information Processing* 13:2567–2586. [https://doi.org/10.1007/s11128-014-0809-8](https://doi.org/10.1007/s11128-014-0809-8) [→](#bodymatter-002.xhtml#xref_d6256e3564)

\[3\]Schuld, M., Sinayskiy, I., and Petruccione, F. 2015. An Introduction to quantum machine learning. *Contemporary Physics* 56:172–185. [https://doi.org/10.1080/00107514.2014.964942](https://doi.org/10.1080/00107514.2014.964942) [→](#bodymatter-002.xhtml#xref_d6256e3567)

\[4\]Furber, E. F., Lester, D. R., Plana, L. A., Garside, J. D., Painkras, E., Temple, S., and Brown, A. D. 2013. Overview of the SpiNNaker system architecture. *IEEE Transactions on Computers* 62:2454–2467. [https://doi.org/10.1109/TC.2012.142](https://doi.org/10.1109/TC.2012.142) [→](#bodymatter-002.xhtml#xref_d6256e3573)

\[5\]Neftci, E., Binas, J., Rutishauser, U., Chicca, E., Indiveri, G., and Douglas, R. J. 2013. Synthesizing cognition in neuromorphic electronic systems. *Proceedings of the National Academy of Sciences of the United States of America* 110:E3468–E3476. [http://dx.doi.org/10.1073/pnas.1212083110](http://dx.doi.org/10.1073/pnas.1212083110) [→](#bodymatter-002.xhtml#xref_d6256e3576)

\[6\]O’Reilly, R. C., Munakata, Y., Frank, M. J., Hazy, T. E., and contributors. 2014. *Computational cognitive neuroscience* (2nd ed.). [http://ccnbook.colorado.edu/](http://ccnbook.colorado.edu/) (accessed January 12, 2019) [a](#bodymatter-002.xhtml#xref_d6256e3582), [b](#bodymatter-002.xhtml#xref_d6256e3644)

\[7\]MacLennan, B. J. 2017. Field computation: A framework for quantum-inspired computing. In *Quantum Inspired Computational Intelligence: Research and Applications*, ed. S. Bhattacharyya, U. Maulik, and P. Dutta, 85–110. Cambridge, MA: Morgan Kaufmann / Elsevier. [a](#bodymatter-002.xhtml#xref_d6256e3585), [b](#bodymatter-002.xhtml#xref_d6256e3669), [c](#bodymatter-002.xhtml#xref_d6256e3770)

\[8\]Morasso, P. G., and Sanguineti, V. 1997. *Self-organization, computational maps and motor control*. Amsterdam: North-Holland. [→](#bodymatter-002.xhtml#xref_d6256e3641)

\[9\]MacLennan, B. J. 1999. Field computation in natural and artificial intelligence. *Information Sciences* 119:73–89. [a](#bodymatter-002.xhtml#xref_d6256e3666), [b](#bodymatter-002.xhtml#xref_d6256e3754)

\[10\]Eliasmith, C., Stewart, T. C., Choo, X., Bekolay, T., DeWolf, T., Tang, Y., and Rasmussen, D. 2012. A large-scale model of the functioning brain. *Science* 338:1202–1205. [http://doi.org/10.1126/science.1225266](http://doi.org/10.1126/science.1225266) [→](#bodymatter-002.xhtml#xref_d6256e3757)

\[11\]MacLennan, B. J. 1997. Field computation in motor control. In *Self-Organization, Computational Maps and Motor Control*, ed. P. G. Morasso and V. Sanguineti, 37–73. Amsterdam: North-Holland. [→](#bodymatter-002.xhtml#xref_d6256e3760)

\[12\]MacLennan, B. J. 2009. Field computation in natural and artificial intelligence. In *Encyclopedia of Complexity and System Science*, ed. R. Meyers et al., Chapter 6, entry 199, 3334–3360. New York: Springer. [→](#bodymatter-002.xhtml#xref_d6256e3764)

\[13\]MacLennan, B. J. 2014. The promise of analog computation. *International Journal of General Systems* 43:682–696. [→](#bodymatter-002.xhtml#xref_d6256e3767)

\[14\]Rumelhart, D. E., McClelland, J. L., and PDP Research Group. 1986. *Parallel distributed processing: Explorations in the microstructure of cognition, volume 1: Foundations*. Cambridge, MA: MIT Press. [→](#bodymatter-002.xhtml#xref_d6256e3776)

\[15\]Sanger, T. D. 1996. Probability density estimation for the interpretation of neural population codes. *Journal of Neurophysiology* 76:2790–2793. [→](#bodymatter-002.xhtml#xref_d6256e3779)

\[16\]Høyer, P. 2000. Arbitrary phases in quantum amplitude amplification. *Physical Review A* 62:052304. [https://doi.org/10.1103/PhysRevA.62.052304](https://doi.org/10.1103/PhysRevA.62.052304) [→](#bodymatter-002.xhtml#xref_d6256e12928)

\[17\]Chen, J., Wang, L., and Charbon, E. 2017. A quantum-implementable neural network model. *Quantum Information Processing* 16:245. [http://doi.org/10.1007/s11128-017-1692-x](http://doi.org/10.1007/s11128-017-1692-x) [→](#bodymatter-002.xhtml#xref_d6256e19594)

\[18\]McClelland, J. L., Rumelhart, D. E., and PDP Research Group. 1986. *Parallel distributed processing: Explorations in the microstructure of cognition, volume 2: Psychological and biological models*. Cambridge, MA: MIT Press. [→](#bodymatter-002.xhtml#xref_d6256e19600)

\[19\]Fredkin, E. F. and Toffoli, T. 1982. Conservative logic. *International Journal of Theoretical Physics* 21:219–253. [→](#bodymatter-002.xhtml#xref_d6256e27667)

## Notes

# 3 Quantum optimization for machine learning

Ashish Mani ASET, Amity University UP, EEE, ASET, G012A, E-I Block, Sector 125, 201303, Noida, Uttar Pradesh, India Siddhartha Bhattacharyya Department of Computer Science and Engineering, CHRIST (Deemed to be University), Hosur Road, Bangalore, Karnataka, India Amlan Chatterjee California State University Dominguez Hills, Computer Science, California State University, 1000, E Victoria, 90747, Dominguez Hills, California, USA 

#### Abstract

Machine learning is a branch of Artificial Intelligence that seeks to make machines learn from data. It is being applied for solving real world problems with huge amount of data. Though, Machine Learning is receiving wide acceptance, however, execution time is one of the major concerns in practical implementations of Machine Learning techniques. It largely comprises of a set of techniques that trains a model by reducing the error between the desired or actual outcome and an estimated or predicted outcome, which is often called as loss function. Thus, training in machine learning techniques often requires solving a difficult optimization problem, which is the most expensive step in the entire model-building process and its applications. One of the possible solutions in near future for reducing execution time of training process in Machine learning techniques is to implement them on quantum computers instead of classical computers. It is conjectured that quantum computers may be exponentially faster than classical computers for solving problems which involve matrix operations. Some of the machine learning techniques like support vector machines make extensive use of matrices, which can be made faster by implementing them on quantum computers. However, their efficient implementation is non-trivial and requires existence of quantum memories. Thus, another possible solution in near term is to use a hybrid of Classical Quantum approach, where a machine learning model is implemented in classical computer but the optimization of loss function during training is performed on quantum computer instead of classical computer. Several Quantum optimization algorithms have been proposed in recent years, which can be classified as gradient based and gradient free optimization techniques. Gradient based techniques require the nature of optimization problem being solved to be convex, continuous and differentiable otherwise if the problem is non-convex then they can find local optima only whereas gradient free optimization techniques work well even with non-continuous, non-linear and non-convex optimization problems. This chapter discusses a global optimization technique based on Adiabatic Quantum Computation (AQC) to solve minimization of loss function without any restriction on its structure and the underlying model, which is being learned. Further, it is also shown that in the proposed framework, AQC based approach would be superior to circuit-based approach in solving global optimization problems.

Keywords:  Artificial Intelligence,  quantum computing,  non-convex optimization,  

## 3.1 Introduction

Humanity has been enamored with the creation of artificially intelligent machines since the advent of programmable electronic computing devices in last century. In 1956, the term ‘Artificial Intelligence’ was coined for ‘thinking machines’ in the workshop held at Dartmouth \[[1](#bodymatter-003.xhtml#b_9783110670707-003_ref_001)\]. Several proposals have been made to make machines behave intelligently \[[2](#bodymatter-003.xhtml#b_9783110670707-003_ref_002)\], but most of them suffered from non-availability of technology required to implement them efficiently. Learning is considered as manifestation of the intelligent behavior, so a machine which can learn a difficult task will be treated at least artificially intelligent. The discipline which deals with the learning techniques involving data is called as Machine learning. It tries to make a computer learn from past experiences represented in from of data and make reliable decisions from it. These techniques can fine tune their performance as fresh experiences are gathered. It helps in building a data driven model rather than a static precise model and is widely used in classification, clustering and pattern recognition etc. It is being widely used in real world fields like financial services \[[3](#bodymatter-003.xhtml#b_9783110670707-003_ref_003)\], health services \[[4](#bodymatter-003.xhtml#b_9783110670707-003_ref_004)\], marketing and sales \[[5](#bodymatter-003.xhtml#b_9783110670707-003_ref_005)\], social network analysis \[[6](#bodymatter-003.xhtml#b_9783110670707-003_ref_006)\], and virtual personal assistants \[[7](#bodymatter-003.xhtml#b_9783110670707-003_ref_007)\] etc.

Some popular Machine Learning algorithms are Artificial Neural Networks (ANN) \[[8](#bodymatter-003.xhtml#b_9783110670707-003_ref_008)\], Support Vector Machines (SVM) \[[9](#bodymatter-003.xhtml#b_9783110670707-003_ref_009)\], K-means Clustering \[[10](#bodymatter-003.xhtml#b_9783110670707-003_ref_010)\], Regression \[[11](#bodymatter-003.xhtml#b_9783110670707-003_ref_011)\], Decision trees \[[12](#bodymatter-003.xhtml#b_9783110670707-003_ref_012)\] etc. The generic steps involved in any machine learning project are as follows:

Data collection: This step involves collecting data pertaining to the problem to be solved. The data should be of high quality, which is necessary for a high quality model. There are several measures available to evaluate the quality of data \[[13](#bodymatter-003.xhtml#b_9783110670707-003_ref_013)\]. Low quality of data will generally result in low quality of model and subsequently predictions or decisions.

Model selection: This step involves selection of a specific technique like ANN or SVM etc. Further, it also involves selecting the structure of the model i.e. in case of ANN, number of hidden layers, no. of neurons in each hidden layer, activation functions etc.

Training: In this step, the parameters of the model are decided i.e. in case of ANN and SVM, weights are determined using some loss function i.e., a loss function which represents the performance of the model on training data set is used to search / compute the weights.

Validation: In this step, the performance of the model on testing data set is determined and compared with other existing models.

Deployment: Finally the model is deployed so that it can be used for making predictions or decisions in real situations.

The first step is specific to the problem being solved by using machine learning, but can be automated in most cases, to make data collection process reliable, quick and cheap. The second step of Model selection usually requires past experience and trial and error approach, which can be translated into a heuristic \[[13](#bodymatter-003.xhtml#b_9783110670707-003_ref_013)\]. The selection of the model is often done more than once and is typically based on the empirical evidence regarding the performance of the model, which is known after the validation. The third step of training is usually the most compute intensive approach of all the other steps and depending on the complexity of model, it can be efficient also if the underlying process is linear, then its modelling results in well-behaved loss function i.e., loss function is convex, continuous and differentiable in the region of interest. However, most loss functions are often not well behaved due to the underlying nonlinear process which is generating the data and in such cases, the optimization of loss function becomes a key challenge in successful implementation of machine learning technique. It has been often experienced that when loss function is well-behaved, the model is less useful \[[14](#bodymatter-003.xhtml#b_9783110670707-003_ref_014)\] and when loss function is difficult to optimize, then the resulting model is more powerful \[[15](#bodymatter-003.xhtml#b_9783110670707-003_ref_015)\]. Validation and deployment are usually computationally less expensive as the trained model takes input and gives output in the form of predictions or decisions. In this chapter, we will primarily focus on making training more efficient in machine learning through quantum optimization.

Optimization is applied routinely in almost all types of machine learning techniques and its applications. Chambers dictionary describes optimization as an act of ‘making the most or best of anything’. Therefore, performing optimization in training stage of machine learning means finding the most or best suitable parameters of the model. There are machine learning models like linear SVM whose weights can be determined by matrix inversion techniques \[[16](#bodymatter-003.xhtml#b_9783110670707-003_ref_016)\], which can be implemented efficiently in case of gate model of quantum computation, thus showing exponential speed-up. However, such techniques often require existence of quantum RAM \[[17](#bodymatter-003.xhtml#b_9783110670707-003_ref_017)\] and data to be generated from a linear process with low noise. In real world problems, the assumption of linearity is often violated and thus most popular techniques are non-linear and convexity cannot be guaranteed. If the optimization problem is convex then gradient based techniques are guaranteed to find the global optima regardless of the initialization \[[18](#bodymatter-003.xhtml#b_9783110670707-003_ref_018)\]. So many optimization techniques try to simplify the problem so that they appear linear or convex \[[13](#bodymatter-003.xhtml#b_9783110670707-003_ref_013)\]. Alternatively, they try to solve the problem approximately by using techniques like stochastic gradient descent \[[19](#bodymatter-003.xhtml#b_9783110670707-003_ref_019)\], which are iterative and not the desired single shot techniques. Thus, these techniques are usually computationally time-consuming as the nature of the problem they are trying to solve is non-linear, non-differentiable, multi-dimensional, multi-modal, and stochastic. Several quantum enhanced approaches have been proposed to solve computational issues in machine learning, of which global optimization using adiabatic quantum computation (AQC) is a promising technique, especially for problems which are non-linear, non-differentiable, multi-dimensional, and multi-modal. Efforts have also been made to solve quadratic unconstrained binary optimization problems on AQC model \[[20](#bodymatter-003.xhtml#b_9783110670707-003_ref_020)\]. In this chapter, we propose an adiabatic quantum computing based iterative global optimizer for minimizing the loss function of machine learning techniques, which would be useful when the optimization problem is non-linear, non-differentiable, multi-dimensional, and multi-modal, where gradient based techniques like \[[19](#bodymatter-003.xhtml#b_9783110670707-003_ref_019)\] and single shot techniques \[[21](#bodymatter-003.xhtml#b_9783110670707-003_ref_021)\] are not computationally efficient or relevant. Further, there are some Variational Quantum computing proposals, where they are focusing on implementing function evaluation on a near term quantum computing device and implementing a traditional gradient free optimization technique like Nelder-Meads method on classical computer \[[19](#bodymatter-003.xhtml#b_9783110670707-003_ref_019)\], however, our proposal is different from such proposals as the entire optimization step will be run on a future Adiabatic Quantum Computer. This chapter is further organized as follows: Related work about the development of AQC based algorithms is discussed in [Section 3.2](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_002). The theoretical underpinning of Adiabatic Quantum Computing is discussed in [Section 3.3](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_003). [Section 3.4](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_004) presents the development of Grover’s Adaptive Search. Problem formulation is described in [Section 3.5](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_005). [Section 3.6](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_006) presents quantum search based on AQC. Minimum finding algorithm based on AQC is described in [Section 3.7](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_007). [Section 3.8](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_008) discusses the framework for implementing quantum optimization algorithm based on AQC. Conclusions and some directions for future work are presented in [Section 3.9](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_009).

## 3.2 Related work

Adiabatic quantum algorithms were introduced by Farhi et al. \[[22](#bodymatter-003.xhtml#b_9783110670707-003_ref_022)\] based on the adiabatic conditions derived from Folk theorem. These algorithms have a Hamiltonian constructed for the problem being solved which is called as Problem Hamiltonian (H[fin]). The ground state of the H[fin] can be expressed as the optimal solution of the problem. Further, initially the system is prepared in the ground state of an initial Hamiltonian, which is easy to build. Subsequently, the initial Hamiltonian is changed progressively towards the H[fin] so that the probability of finding the solution is large at the end of the evolution. However, the change from initial Hamiltonian to final Hamiltonian i.e. H[fin] cannot be instantaneous or even lesser than the minimum time required according to the adiabatic theorem. If the system is evolved slowly enough then adiabatic theorem guarantees that system will remain in the ground state of the instantaneous Hamiltonian, thus the evolution time of varying the Hamiltonian from initial to problem is a measure of complexity of the AQC based algorithm. Several constraint satisfaction problems along with optimization problems can be represented by an aggregated set of local Hamiltonians H = ∑i H i where Hi represents a local constraint. The ground state of H would satisfy the maximum possible number of such constraints and represents a desired optimal solution amongst other possible optimal solutions in case of multimodal problems, i.e. the problems having more than one optima solutions. The system stays in the instantaneous ground state of the evolving Hamiltonian as it will remain close to the ground state provided the rate of change of Hamiltonian from initial to H[fin] remains within the bounds specified by the adiabatic theorem. The bounds on the evolution time is dependent on the energies of the initial and problem Hamiltonian as well as on the inverse gap of the instantaneous Hamiltonians H(t). The energy difference between the ground state of a Hamiltonian and its first excited state represents the gap of the Hamiltonian. That is when Hamiltonian is presented as a matrix then the gap is the difference between Hamiltonian’s smallest and second smallest eigenvalue. Farhi et al. \[[22](#bodymatter-003.xhtml#b_9783110670707-003_ref_022)\] have proposed and investigated AQC based algorithms for NP-complete problems like 3SAT. However, the key challenge in AQC based algorithm for solving a specific problem is analytical calculation of the Hamiltonian gap, which is not known for most of the problems till date. The other approach is to numerically simulate the system but the computational cost of simulating quantum mechanical system on classical computers is very expensive so the number of qubits in numerical simulations is limited. However, the numerical simulation performed in \[[22](#bodymatter-003.xhtml#b_9783110670707-003_ref_022)\] on small sized problems did show that the time required to solve NP-complete problems scaled only polynomially with the problem size. But later work \[[23](#bodymatter-003.xhtml#b_9783110670707-003_ref_023)\] gave strong negative evidence for the speed up shown in \[[22](#bodymatter-003.xhtml#b_9783110670707-003_ref_022)\] for AQC based algorithms. It was shown that the performance of adiabatic algorithms is even sensitive to the choice of initial Hamiltonian and it can fail if the selection of initial Hamiltonian is not performed according to the structure of the problem \[[23](#bodymatter-003.xhtml#b_9783110670707-003_ref_023)\]. Further, some investigations were made in \[[24](#bodymatter-003.xhtml#b_9783110670707-003_ref_024)\] by mapping the H[fin] of certain instances of 3-SAT to an Ising model and it was shown that the Hamiltonian gap is exponentially small in some problem instances. Further, some special instances of 3-SAT were also constructed in \[[25](#bodymatter-003.xhtml#b_9783110670707-003_ref_025)\] which were hard for the AQC based algorithm. Subsequently, it was shown in \[[26](#bodymatter-003.xhtml#b_9783110670707-003_ref_026), [27](#bodymatter-003.xhtml#b_9783110670707-003_ref_027)\] that local minimum of some optimization problems can cause very small gaps in the spectrum of the Hamiltonian. These studies had designed hard instances of problems to highlight the weakness of AQC based algorithms. But in \[[28](#bodymatter-003.xhtml#b_9783110670707-003_ref_028)\], randomly generated instances of the NP-complete problem Exact Cover 3 (EC3), also known as 1-in-3 SAT were used to test AQC based algorithm and it was shown that failure probability of AQC based algorithm was high. Altshuler et al. argued that their study provided strong evidence against adiabatic quantum optimization, i.e. hard instances of NP-complete problems are difficult for AQC based algorithm but the basis for this conclusion depends on some common properties shared by other NP-complete problems such as 3-SAT. However, initially Choi \[[29](#bodymatter-003.xhtml#b_9783110670707-003_ref_029)\] and later Dickson and Amin \[[30](#bodymatter-003.xhtml#b_9783110670707-003_ref_030)\] challenged the argument against AQC in \[[28](#bodymatter-003.xhtml#b_9783110670707-003_ref_028)\]. Choi’s argued that a failure of a specific instance of AQC based algorithm is not sufficient to conclude that a problem is hard for adiabatic quantum computation / optimization in general. An AQC based algorithm comprise of three variable components, namely, initial Hamiltonian, problem Hamiltonian and evolution path. Thus, there are many combinations possible of these three components for designing an AQC based algorithm. He further argued that if it is to be proved that adiabatic quantum computation is inefficient even for a particular problem then, it has to be shown that there exists no polynomial-time adiabatic quantum algorithms for the problem, which requires testing all combinations possible for designing AQC based algorithms and not just few instances. Further, Dickson and Amin \[[30](#bodymatter-003.xhtml#b_9783110670707-003_ref_030)\] analytically showed that there always exist adiabatic paths for the NP-hard problem of maximum independent set along which no such crossings of local minima of the final Hamiltonian with its global minimum occur, thus the Hamiltonian gap need not be vanishingly small and hence designing of efficient AQC based algorithm is possible. Therefore, in order to prove that adiabatic quantum optimization fails for any NP-complete problem, one must prove that it is impossible to find any such path along with combination of initial and problem / final Hamiltonian in polynomial time. Therefore, it is still an open problem whether AQC can solve NP complete problems efficiently. However, it is becoming increasingly clear that there may not exit one unique path for solving all the NP complete problems.

Quantum unstructured search has been implemented adiabatically by Farhi et al. \[[31](#bodymatter-003.xhtml#b_9783110670707-003_ref_031)\]. This implementation was based on global evolution model and had a computational complexity of O(N), where N is the size of the database. Later Roland and Cerf showed that quadratic speed up is possible in adiabatic version also by continuously adjusting the rate with which the initial Hamiltonian is switched to final Hamiltonian by only fulfilling locally, the conditions of adiabaticity \[[32](#bodymatter-003.xhtml#b_9783110670707-003_ref_032)\]. The adiabatic quantum search has been rigorously studied by Rezakhani et al. \[[33](#bodymatter-003.xhtml#b_9783110670707-003_ref_033)\] where the results relating the accuracy and the run time of the AQC based algorithm has been determined. It has also been demonstrated that AQC based algorithm shows two discernible regimes with respect to error i.e., the error reduces exponentially for short times and then reduces polynomially for longer times, under fairly general conditions.

In \[[34](#bodymatter-003.xhtml#b_9783110670707-003_ref_034)\], it was demonstrated that a partial adiabatic search algorithm on quantum circuit model could be implemented and the performance of the algorithm was same as that of the local adiabatic algorithm for the case where a single element is marked i.e. M = 1 by investigating the minimum energy gap between the first excited state and the ground state of the system Hamiltonian. Moreover, the algorithm keeps the advantages of global adiabatic algorithms without losing the speedup of the local adiabatic search algorithm by evolving globally only for a small interval during evolution from initial to final / problem Hamiltonian.

In \[[22](#bodymatter-003.xhtml#b_9783110670707-003_ref_022)\], it was shown that quantum circuit models can simulate efficiently an arbitrary AQC based algorithm. Subsequently, it has also been shown in \[[35](#bodymatter-003.xhtml#b_9783110670707-003_ref_035)\] that an appropriate AQC based algorithm can efficiently simulate any quantum circuit model. Further a simple proof of equivalence between adiabatic quantum computation and quantum computation in the circuit model has been provided by Mizel et al. \[[36](#bodymatter-003.xhtml#b_9783110670707-003_ref_036)\]. Therefore, AQC and Quantum Circuit models of computation are essentially equivalent, which implies that a quantum algorithm can be designed in either of the two models for solving difficult problems. Brady and Van Dam has also investigated the necessary run-time required for AQC based optimization \[[37](#bodymatter-003.xhtml#b_9783110670707-003_ref_037)\] and showed that nonadiabatic speedup does not occur for general cases but only for special case. Recently, Quantum Approximate Optimization Algorithm (QAOA) \[[38](#bodymatter-003.xhtml#b_9783110670707-003_ref_038), [39](#bodymatter-003.xhtml#b_9783110670707-003_ref_039)\] and the Variational Quantum Eigensolver \[[40](#bodymatter-003.xhtml#b_9783110670707-003_ref_040)\] have been proposed to address classical combinatorial optimization and quantum chemistry problems, respectively.

In this chapter, a framework based on Adiabatic Quantum Computation for solving global optimization problem has been proposed in [Section 3.4](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_004)., which would be helpful in training of Machine Learning techniques which models non-linear processes unlike their computationally efficient counterparts. Further, constrained optimization using AQC was discussed in \[[41](#bodymatter-003.xhtml#b_9783110670707-003_ref_041)\].

## 3.3 Adiabatic quantum computation

Adiabatic quantum computation \[[42](#bodymatter-003.xhtml#b_9783110670707-003_ref_042)\] is an alternative approach to quantum computing that has been shown to be equivalent to the quantum circuit model, but appears to have some advantages over the circuit model \[[31](#bodymatter-003.xhtml#b_9783110670707-003_ref_031)\]. It is based on a well-known technique in quantum mechanics, called adiabatic approximation \[[43](#bodymatter-003.xhtml#b_9783110670707-003_ref_043)\]. It is used for determining approximate solutions of Schrodinger equation subject to the condition that the Hamiltonian governing the dynamics of the system is changing slowly with time. This implies that if a quantum system is prepared in its nth eigenstate, then it will stay in the nth eigenstate throughout the evolution provided the neighborhood energy gaps are large enough and its Hamiltonian varies slowly enough.

Let a quantum system in state |φ〉 evolve according to the Schrodinger’s equation:

(3.1)$i\\hslash\\frac{d}{dt}|\\Phi\\left( t \\right)\\rangle = {}H\\left( t \\right)|\\Phi\\left( t \\right)\\rangle$ 

where H(t) is the Hamiltonian of the quantum system and ћ is reduced Planck’s constant \[[31](#bodymatter-003.xhtml#b_9783110670707-003_ref_031)\]. Let H[ini] be the Hamiltonian of the system in its initial state i.e. at t = 0 and H[fin] be the Hamiltonian of the system in its final state i.e. at t = T, where

(3.2)*H*(*t*) = (1 − *s*(*t*)) *H*[*i**n**i*] + *s*(*t*)*H*[*f**i**n*] 

where s(t) is a continuous function with s(0) = 0 and s(T) = 1. The instantaneous eigenstates associated with H[i] are denoted by |*ψ*[*i*]⟩. In general, let eigenstates of H(t) be |*ψ*[*k*](*t*)⟩ such that:

(3.3)*H*(*t*)|*ψ*[*k*](*t*)⟩ = *E*[*k*](*t*)|*ψ*[*k*](*t*)⟩ 

where *E[k]*(*t*) are the corresponding eigenvalues and *k* labels the eigenstates (*k *\= 0 indicates the ground state).

The minimum gap between the lowest two eigenvalues is defined as follows:

(3.4)$g\_{min} = \\min\\limits\_{0 \\leq t \\leq T}\\lbrack E\_{1}\\left( t \\right) - E\_{0}\\left( t \\right)\\rbrack$ 

The maximum value of the matrix element of *dH*/*dt* between the two corresponding eigenstates is given by the following equation:

(3.5)$D\_{max} = \\max\\limits\_{0 \\leq t \\leq T}\\left| \\left\\langle \\frac{dH}{dt} \\right\\rangle\_{1,0} \\right|$ 

where $\\left\\langle \\frac{dH}{dt} \\right\\rangle\_{1,0} = \\langle\\psi\_{1}\\left( t \\right)\\left| \\frac{dH}{dt} \\right|\\psi\_{0}\\left( t \\right)\\rangle$

The adiabatic theorem states that if the system at time *t *\= 0 is in its ground state |*ψ*[*i**n**i*]⟩ = |*ψ*[0](0)⟩ and let it evolve under the Hamiltonian *H*(*t*), then

(3.6)|⟨*ψ*[0](*T*)|*Φ*(*T*)⟩| ≥ 1 − *ε*² 

provided:

(3.7)$\\frac{D\_{max}}{g\_{min}^{2}} \\leq \\varepsilon$ 

where 0 < *ε* ≪ 1,

and

(3.8)$\\left| \\frac{\\langle\\psi\_{1}\\left( t \\right)\\left| \\frac{dH}{dt} \\right|\\psi\_{0}\\left( t \\right)\\rangle}{\\left\\lbrack {E\_{1}\\left( t \\right) - E\_{0}\\left( t \\right)} \\right\\rbrack^{2}} \\right| < \\varepsilon,t\\ \\epsilon\\ \\left\\lbrack {0,T} \\right\\rbrack.$ 

where *ε* ≪ 1.

The above conditions for adiabatic computation are based on Folk theorem, which has come under criticism recently \[[44](#bodymatter-003.xhtml#b_9783110670707-003_ref_044)\]. These conditions do not guarantee general applicability of Adiabatic approximation. A number of attempts have been made to rigorously study Adiabatic Theorem and provide new conditions for generic applicability of adiabatic approximation \[[45](#bodymatter-003.xhtml#b_9783110670707-003_ref_045)\]. Tong et al. have also proposed a set of conditions, which are sufficient for verifying the validity of adiabatic approximation \[[46](#bodymatter-003.xhtml#b_9783110670707-003_ref_046)\]. These are three conditions:

(3.9) $\\!\\!\\!\\! I.\\quad\\quad\\left| \\frac{\\langle\\psi\_{n}\\left( t \\right)|\\psi\_{\\!\\! m}^{\\prime}\\left( t \\right)\\rangle}{E\_{n}\\left( t \\right) - E\_{m}\\left( t \\right)} \\right| \\ll 1,{}t\\ \\epsilon\\ {}{}\\left\\lbrack {0,T} \\right\\rbrack$ (3.10) ${II}.\\quad\\;\\;\\int\\limits\_{0}^{T}\\left| {\\left( \\frac{\\langle\\psi\_{n}\\left( t \\right)|\\psi\_{\\!\\! m}^{\\prime}\\left( t \\right)\\rangle}{E\_{n}\\left( t \\right) - E\_{m}\\left( t \\right)} \\right)^{\\prime}} \\right|dt \\ll 1$ (3.11) $\\quad\\quad\\quad\\quad\\;{III}.\\quad\\int\\limits\_{0}^{T}\\left| \\left( \\frac{\\langle\\psi\_{n}\\left( t \\right)|\\psi\_{\\!\\! m}^{\\prime}\\left( t \\right)\\rangle}{E\_{n}\\left( t \\right) - E\_{m}\\left( t \\right)} \\right)^{\\prime} \\right|\\left| {\\langle\\psi\_{n}\\left( t \\right)|\\psi\_{l}\\!^{\\prime}\\left( t \\right)\\rangle} \\right|dt \\ll 1$ 

where m ≠ l, n ≠ m, T is total evolution time, |*ψ*[*k*](*t*)⟩ and *E[k]*(*t*) are eigenvectors and corresponding eigenvalues of H at time t, k = 1,…,N (N is the size of state space of the system, which includes l, m and n). *ψ′*[m] is first derivative of *ψ*[m].

A rigorous study has been made of applicability of adiabatic approximation on the basis of these three conditions in case of Grover’s Quantum Search under AQC framework in \[[46](#bodymatter-003.xhtml#b_9783110670707-003_ref_046)\]. It has been found that the results obtained originally by Folk theorem is still valid. As this chapter, primarily uses Grover’s search, so for rest of the chapter, the results of Folk theorem will be applied.

Grover’s Quantum Search algorithm \[[47](#bodymatter-003.xhtml#b_9783110670707-003_ref_047)\] and its variants can be used as a subroutine in designing algorithms for solving optimization problems. The variants of Grover’s search algorithm, which do not require prior knowledge of the number of target entities like Boyer’s proposal \[[48](#bodymatter-003.xhtml#b_9783110670707-003_ref_048)\] and fixed point schemes \[[49](#bodymatter-003.xhtml#b_9783110670707-003_ref_049)\], are especially suited for such problems. Durr and Høyer proposed an algorithm in \[[50](#bodymatter-003.xhtml#b_9783110670707-003_ref_050)\] for finding minimum value in a database by employing the algorithm proposed in \[[48](#bodymatter-003.xhtml#b_9783110670707-003_ref_048)\] as a subroutine.

The quantum algorithm for locating minima searches for the minimum entry in an un-arranged table ‘D’ of K items, where every item has a value belonging to an ordered set. The pseudo code for quantum minimum searching algorithm is as follows:

1.  Randomly select a threshold index J[in] ∈ \[0,K−1\].
    
2.  Repeat till the total running time is more than 22.5√K + 1.4 lg² K.
    
    1.  Apply the Boyer et al. quantum searching algorithm \[48\].
        
    2.  Observe the first register: let D\[J[in^′]\] be the outcome.
        
    3.  If D\[J[in^′]\] < D \[J[in]\], then set threshold index J[in] to J[in^′].
        
    
3.  Return J[in].
    

The quantum minimum searching algorithm finds the index of the minimum value and it forms the inspiration for further developing optimization algorithms and heuristics, so in a way, was a path breaking research.

### 3.3.1 Oracle

A classical oracle of a function f(x) can be implemented reversibly as shown in the [Figure 3.1](#bodymatter-003.xhtml#b_9783110670707-003_fig_001). Similarly regular quantum oracle can be implemented as shown in [Figure 3.2](#bodymatter-003.xhtml#b_9783110670707-003_fig_002) \[[51](#bodymatter-003.xhtml#b_9783110670707-003_ref_051)\]. However, it differs from the reversible oracle as it may be given input in some superposition of basis states and produces output that may be entangled and in some superposition of basis states.

![Figure 3.1: Reversible implementation of Classical Oracle.](graphic/converted/b_9783110670707-003_fig_001.png)

Figure 3.1: Reversible implementation of Classical Oracle.

![Figure 3.2: Quantum Oracle.](graphic/converted/b_9783110670707-003_fig_002.png)

Figure 3.2: Quantum Oracle.

## 3.4 Grover’s adaptive search

Baritompa et al. generalized the quantum minimum search algorithm for solving finite global optimization problems, which have been formulated as follows \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\]:

(3.12) *O**p**t**i**m**i**z**e* *f*(*α*), *α* ∈ *A* 

where f is a real valued function on a finite set A.

Let the cardinality of set A be N. Let *a[1]* *< a[2] < a[3] … < a[L]* be ‘L’ distinct values of the objective function f(α) for all α in A. Therefore, L should be less than or equal to N i.e. if L would be equal to N then for every value of α in set A, there would be a distinct objective function value of f. Let there be a uniform probability measure λ on A, such that ϒ be the range measure given by a stochastic vector (ϒ[1], ϒ[2], …, ϒ[L]) induced by f, so that ϒ[j] = |f^(−1)(a[j])|/N for j = 1, 2, …, L. Let P[j] = $\\sum\_{i = 0}^{j}\\Upsilon\_{j}$, the probability that a random point has value of ‘a[j]’ or less, i.e. P[L] = 1. Therefore, there is an improving region corresponding to all values of objective function f(α), which belongs to a sub-set of A, where f(α) has strictly better value \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\]. The measure of improving region under λ is denoted as improving fraction P. So if we choose a particular value for objective function, say ‘θ’, then the improving region would comprise of set of all the point whose objective function values are better than ‘θ’.

The algorithm proposed by Baritompa et al. is known as Grover Adaptive search (GAS), which takes a sequence of rotation counts and an objective function value threshold as the input. Its pseudo code is as follows \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\]:

1.  Select α[1] in A, and set θ[1] = f(α[1]).
    
2.  Set count nc = 1.
    
3.  While (termination condition is not met)
    

*   {
    
*   a. Perform a Grover search of r[nc] rotations on f with threshold V[nc], and denote the outputs by α and θ.
    
*   b. If v < V[nc], set θ[nc+1 ]\= α and V[nc +1 ]\= v; otherwise, set θ[nc+1 ]\= θ[nc] and V[nc +1 ]\= V[nc].
    
*   c. nc = nc + 1.
    
*   }
    

GAS has been studied using an adaptive search framework developed in \[[53](#bodymatter-003.xhtml#b_9783110670707-003_ref_053), [54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054), [55](#bodymatter-003.xhtml#b_9783110670707-003_ref_055)\] which has been applied for theoretically analyses of convergence properties of optimization methods that use stochastic global search. One of the underlying assumptions of the adaptive algorithms is that search can find better (“improving”) solutions (at some cost). GAS is based on an oracular function that can find better solutions than the current one with a finite probability in every iteration, if one exists. This oracle takes an input string α ∈ A, computes f(α), compares f(α) with current threshold and outputs zero or one depending on the result of comparison and the type of optimization problem being solved i.e. whether it is a minimization or maximization problem. Such oracles can be implemented using reversible / quantum circuits as shown in [Section 3.3.1](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_003_s_001).

Thus, GAS generates a series of domain solutions, which are uniformly distributed in the improving region of the previous solution. Further, according Theorem 1 and Corollary 6 given in \[[54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054)\], such a series converges to a global optimal solution rapidly; e.g., a unique optimal solution in a domain of size *K* can be located after 1 + ln(*K)* such improvements, in expectation \[[54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054)\].

Theorem 1 \[[54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054)\]. *The expected number of iterations, I, required for solving the finite optimization problem described by* [eq. (3.12)](#bodymatter-003.xhtml#b_9783110670707-003_eq_012) *is:* 

1.  $I = 1 + \\sum\\limits\_{i = 2}^{N}\\frac{\\Upsilon\_{i}}{P\_{i}}$ *for strong Pure Adaptive Search.*
    
2.  $I = 1 + \\sum\\limits\_{i = 2}^{N}\\frac{\\Upsilon\_{i}}{P\_{i - 1}}$ *for weak Pure Adaptive Search.*
    

where Strong Pure Adaptive Search implies that each iteration of the search algorithm should sample objective function value from a strictly improving region. The weak Adaptive search implies that each iteration of the search algorithm should sample objective function value that is either equal or better. 

### Corollary 6

\[[54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054)\]. *The expected number of iterations, I, for solving finite global optimization described by* [eq. (3.12)](#bodymatter-003.xhtml#b_9783110670707-003_eq_012)*, and given a uniform distribution on the objective function values, is:*

1.  *bounded above by 1 + logN for strong Pure Adaptive Search.*
    
2.  *bounded above by 2 + log(N*−*1) for weak Pure Adaptive Search.*
    

GAS corresponds to the weaker version of Pure Adaptive search as it cannot be guaranteed that after application of Grover Search, an strictly better solution would be found. It can be argued that Grover Search can return an objective function value, which is less than the threshold and so it does not corresponds to Pure Adaptive Search Framework, but, in such a case, the inferior value would be discarded and the current threshold would be treated as the output of the algorithm for the particular iteration. Thus, the overall GAS corresponds to weaker version of Pure Adaptive Search.

An important design decision of Grover’s Adaptive Search is determination of the rotation count sequence. It is possible to determine the optimal rotation count ‘r’ for every iteration of the GAS provided the information regarding improving fraction ‘P’ of the domain is available. Thus, if the optimal rotation count is used for every run of Grover’s Search, then a better (improved) solution will almost certainly be found in every iteration of the GAS. However, in real world problems, the improving fraction *P* is often unknown. An estimate of the improving fraction P can always be made by using all the information available at the end of an iteration and considering the nature of the problem. That is a Bayesian approach can be applied by tracking the improving fraction at every iteration through the sequence of posterior distributions, which will be subsequently used for choosing rotation count at the particular iteration. However, this kind of approach might be very complicated and cumbersome \[[56](#bodymatter-003.xhtml#b_9783110670707-003_ref_056)\]. Thus, other methods have been devised to strike a balance between ease of implementation and optimality of rotation count selection, which includes method based on Boyer et al. \[[48](#bodymatter-003.xhtml#b_9783110670707-003_ref_048)\] used by Durr and Hoyer illustrated in \[[50](#bodymatter-003.xhtml#b_9783110670707-003_ref_050)\].

Another method proposed by Baritompa et al. is based on maximizing the benefit to cost ratio denoted by parameter b in the heuristic \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\]. The benefit has been taken to be the expected decrease in the improving fraction of the domain, which is difficult to ascertain without knowing the nature of the problem being solved. The cost is dependent on the rotation count. The pseudo code for heuristic is as follows:

1.  Initialize *u*[0](*Ω*)  = *Ω* // u[0] is a polynomial
    
2.  For *i*\= 1, 2, …, do: // Generating rotation count r for ith iteration
    
    1.  *E*[*u**i*] = 1 − ∫[0]¹*u*[*i*](*Ω*)*d**Ω*
        
    2.  *β*\= 0
        
    3.  For *r*\= 0, 1, … , until *E*[*u**i*]/(*r*+ 1) < 2*β*, do:
        
        1.  $v\\left( \\Omega \\right) = u\_{i}\\left( \\Omega \\right) + \\Omega\\int\_{\\Omega}^{1}\\frac{g\_{r}\\left( P \\right)}{P}du\_{i}\\left( P \\right)\\ //g\_{r}(P) = sin^{2}((2r + 1)sin^{- 1}\\sqrt{}P)$
            
        2.  *E*[*v*] = 1 − ∫[0]¹*v*(*Ω*)*d**Ω*
            
        3.  $b = \\frac{\\left( {E\_{ui} - E\_{v}} \\right)}{r + 1}$
            
        4.  If *b* > *β*, then
            
            1.  ȓ = *r*
                
            2.  *β* = *b*
                
            3.  *u*[*i* + 1](*Ω*) = *v*(*Ω*)
                
            
        
    4.  Output ȓ
        
    

The sequence of rotation counts produced by the heuristic is independent of the particular optimization problem and is as follows for first 33 entries \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\]:

**0,** **0, 0, 1, 1, 0, 1, 1, 2, 1, 2, 3, 1, 4, 5, 1, 6, 2, 7, 9, 11, 13, 16, 5, 20, 24, 28, 34, 2, 41, 49, 4, 60*, … .***

Recently, the above heuristic method has been further studied and improved by Liu and Koehler \[[56](#bodymatter-003.xhtml#b_9783110670707-003_ref_056)\]. One improvement has been to simplify the calculations involved in computing distributions by employing Chebyshev polynomials, which considerably reduced the computation time. The other improvement has been to convert the above heuristic into a dynamic one, which takes into account whether the Grover search in a particular iteration was successful or not. This has been made possible by using Bayes Law to update the distribution after one complete round of Grover Search depending on success or failure of finding a better solution. The heuristic for computing dynamic rotation schedule is as follows:

1.  Initialize *u*[0](*Ω*)  = *Ω*
    
2.  For *i*\= 1, 2, …, do: // Generating rotation count r for ith iteration
    
    1.  $E\_{ui} = 1 - \\int\\limits\_{0}^{1}u\_{i}\\left( \\Omega \\right)d\\Omega$
        
    2.  *β*\= 0
        
    3.  For *r*\= 0, 1, … , until *E*[*u**i*]/(*r*+ 1) < 2*β*, do:
        
        1.  $b = \\int\\limits\_{0}^{1}Pg\_{r}\\left( P \\right)du\_{i}\\left( P \\right)$
            
        2.  If *b* > *β*, then
            
            1.  $\\overset{\\frown}{r} = \\, r$
                
            2.  *β* = *b*
                
            
        
    4.  Output ȓ
        
    5.  If (Search\_outcome = Success)
        
         $u\_{i + 1}\\left( \\Omega \\right) = {}\\frac{\\int\_{0}^{y}g\_{r}\\left( P \\right)du\_{i}\\left( P \\right) + \\!\\int\_{y}^{1}\\frac{y}{P}g\_{r}\\left( P \\right)du\_{i}\\left( P \\right)}{\\int\_{0}^{1}g\_{r}\\left( P \\right)du\_{c}\\left( P \\right)}$ 
        
        Else
        
        $u\_{i + 1}\\left( {y\\Omega} \\right) = {}\\frac{u\_{i}\\left( \\Omega \\right) - \\!\\int\_{0}^{y}g\_{r}\\left( P \\right)du\_{i}\\left( P \\right)}{1 - \\!\\int\_{0}^{1}g\_{r}\\left( P \\right)du\_{c}\\left( P \\right)}$ 
    

Liu and Koehler have reported that formal derivation of the expected time required by the proposals, made by Durr and Hoyer \[[50](#bodymatter-003.xhtml#b_9783110670707-003_ref_050)\] (based on Boyer et al. algorithm \[[48](#bodymatter-003.xhtml#b_9783110670707-003_ref_048)\]), Baritompa et al. \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\] and their own improved and dynamic version \[[56](#bodymatter-003.xhtml#b_9783110670707-003_ref_056)\] of quantum algorithms for global optimization, is hard to derive. This is because the basic subroutine employed for searching needs knowledge of the distribution function of the improving fraction. Therefore, numerical simulations have been used to compare the methods. However, such simulation studies are computationally very expensive as they require digital computer to simulate a quantum computer. Thus, the performance of such algorithms could be investigated on only problems of small size, which have not much practical significance.

This chapter identifies that basic problem in the above global optimization algorithms is due to the dependence of basic search subroutine on the improving fraction to determine the rotation count in a particular iteration. This problem can be solved by changing quantum computation model from quantum circuit model to Adiabatic Quantum Computation (AQC) model.

AQC provides a distinct advantage over quantum circuit model on Grover’s Search i.e. it eliminates the problem of overshooting. This is possible because the solution is encoded as the ground state of the Problem Hamiltonian, therefore, even if the system is evolved for time period longer than required, the system remains in the ground state of the problem Hamiltonian. This feature of AQC makes it possible to formally derive the expected running time of Global Optimization Algorithm based on AQC.

## 3.5 Problem formulation

Optimization problems that are regularly solved in machine learning and engineering domain are mostly in continuous domain. Such problems are classified as unconstrained and constrained global optimization problems. The unconstrained global optimization problems (UCOP) in continuous variables are generally formulated as follows:

Optimize f(x) where x = (x[1], x[2], ...., x[E]) *ε* *R*^(*E*),

(3.13)$\\begin{matrix} & {Such\\, that:} \\\\ & {x\_{il} < x\_{i} < x\_{iu}{;\\, where}\\ x\_{i}{\\ {is\\, the}}\\ i^{th}\\ {variable\\ with}\\, x\_{il}\\,{and}\\, x\_{iu}\\;{as\\ its\\ lower\\ and\\ upper\\ limits}.} \\\\ \\end{matrix}$ 

The objective function f(x) as well as the inequality and the equality constraints are often nonlinear, non-convex, non-differentiable, multimodal and of high dimension. Thus, optimization techniques, which are efficient by being deterministic, like gradient based methods and exhaustive search, are often rendered ineffective for solving such ill-defined problems \[[57](#bodymatter-003.xhtml#b_9783110670707-003_ref_057)\]. Calculus based methods typically perform local optimization by using search space domain information like local gradient \[[58](#bodymatter-003.xhtml#b_9783110670707-003_ref_058)\]. Enumerative Strategies suffer from the curse of dimensionality i.e. the runtime complexity increases exponential with the dimension of the problem \[[59](#bodymatter-003.xhtml#b_9783110670707-003_ref_059)\].

It has been shown in [Section 3.4](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_004) that Quantum global optimization algorithms can be used for solving finite search domain problems. The search domain of any real variables problem is infinite. In order to overcome this limitation of quantum algorithms, the real variables search space in \[[60](#bodymatter-003.xhtml#b_9783110670707-003_ref_060)\] has been discretized. That is a variable is represented by a finite number of qubits, which determines the resolution and the level of discretization. For example, the decision variables, x[i], in continuous domain are bounded by x[il] and x[iu]. The search space for variable x[i] can be discretized by taking n[i] qubits, so that there will be 2^(ni) distinct values of x[i] which can be selected between the range of \[x[il], x[iu]\]. The maximum discretization error, Δe[i], is as follows:

(3.14)*Δ**e*[*i*] = (*x*[*i**u*]−*x*[*i**l*])/2^((*n**i* + 1)) 

This discretization error is present even in computation performed with classical digital computers. The total number of qubits, nq, required to map the discretized solution space is as follows:

(3.15)*n**q* = ∑[*i*]*n*[*i*] 

The larger the number of qubits more is the accuracy, however, it also increases the running time of the quantum algorithm. Therefore, there is a trade-off involved between accuracy and computation time. An output or auxiliary qubit is also required which evolves according to the result of the computation of the objective function implemented by a reversible circuit \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\].

## 3.6 AQC based quantum search

Adiabatic Quantum Computation is analog analogue of discrete gate-based quantum computing, which is a generic framework that depends on Hamiltonian and Adiabatic theorem \[[31](#bodymatter-003.xhtml#b_9783110670707-003_ref_031)\]. A Problem Hamiltonian (H[fin]) is designed for the problem being solved such that it is a time independent Hamiltonian, and the ground state of H[fin], |*ψ*[*f**i**n*]⟩, represents a solution of the problem. The quantum system is evolved by a time dependent Hamiltonian, H(t). H(0) corresponds to a time independent Hamiltonian known as initial Hamiltonian (H[ini]), whose ground state is easy to construct. Hamiltonian H(t) is time-varying and governs the evolution of the system and it varies according to the bounds given by adiabatic theorem, from H[ini] to H[fin], so that the quantum system stays near the ground state of the instantaneous Hamiltonian H(t) till it reaches H[fin]. Thus, Adiabatic Quantum Algorithm has following main steps:

1.  Determine the number of qubits, nq, required to represent the problem in the quantum system.
    
2.  Find an easily constructible initial ground state and construct its corresponding H[ini].
    
3.  Design the H[fin] according to the problem being solved.
    
4.  Construct the time dependent Hamiltonian H(t), which will govern the evolution of the system for time T:
    
    *H*(*t*) = *H*[*i**n**i*] \* (1−*t*/*T*) + *H*[*f**i**n*] \* (*t*/*T*), 
    
    or,
    
    (3.16)*Ĥ*(*s*) = *H*[*i**n**i*] \* (1−*s*) + *H*[*f**i**n*] \* (*s*), 
    
    where s = t/T and s(0) = 0 and s(T) = 1.
    

1.  Estimate total evolution time T.
    
2.  Evolve the Quantum System according to Schrodinger’s Equation for time T:
    
    (3.17)$i\\hslash\\frac{d|\\psi\\left( t \\right)\\rangle}{dt} = H\\left( t \\right)|\\psi\\left( t \\right)\\rangle$ 
    
    where ħ = 1.
    
3.  Perform Measurement on the Quantum system after time T to obtain the solution of the problem.
    

Search for a marked element in an unstructured database with N[e] elements was also attempted by Farhi et al. in \[[31](#bodymatter-003.xhtml#b_9783110670707-003_ref_031)\] by using global version of the Adiabatic Theorem for their quantum algorithm. This resulted in a running time of the order of N i.e. O(N), which was no better than a classical algorithm. Roland and Cerf improved the performance of Adiabatic Quantum Algorithm for this problem by using local adiabatic evolution approach \[[32](#bodymatter-003.xhtml#b_9783110670707-003_ref_032)\]. Thus, Adiabatic version of Grover’s search also has the same complexity as that of Circuit model. This chapter employs local version of Adiabatic evolution proposed by Roland and Cerf in \[[32](#bodymatter-003.xhtml#b_9783110670707-003_ref_032)\] for Grover’s Search to design a quantum algorithm for solving optimization problems in continuous domain.

The algorithm starts with initial state as |φ[0]〉, which is in equal superposition of all the basis states, N[e] (j represents index of elements in unsorted database):

(3.18)$\\left| \\phi\_{0} \\right.\\rangle = \\frac{1}{{\\sqrt{N}}\_{e}}\\sum\\limits\_{j = 0}^{Ne - 1}|j\\rangle$ 

The beginning Hamiltonian, H[ini], of the system is chosen as:

(3.19)*H*[*i**n**i*] = *I*− |*ϕ*[0]⟩⟨*ϕ*[0]|, 

where I is the Identity matrix and |φ[0]〉 is its ground state with zero energy. Therefore, the H[ini], for quantum search algorithm is independent of the problem. Let us assume that there exist a problem Hamiltonian H[fin], which can be represented as follows:

(3.20)$H\_{fin} = I - \\sum\\limits\_{M \\in m\_{e}}\\left| {\\phi\_{M}\\rangle\\langle\\phi\_{M}} \\right|,$ 

where m[e] is the ensemble of solutions and |φ[M]〉 represents the ground state, and is a solution. H[fin] can be applied without explicitly knowing |φ[M]〉, by using an oracle to tell whether the solution has been found or not. It is implemented as follows:

(3.21)*H*[*f**i**n*]|*ϕ*[*i*]⟩ = *f**p**b*(*ϕ*[*i*])|*ϕ*[*i*]⟩ 

where function fpb(φ[i]) has been implemented as follows:

*I**f*(|*ϕ*[*i*]⟩ ∈ {|*ϕ*[*M*]⟩}) *f**p**b*(*ϕ*[*i*]) = 0 

else

*f**p**b*(*ϕ*[*i*]) = 1 

That is, if |φ[i]〉 is the marked state, then fpb(φ[i]) is equal to zero, corresponding to the ground state, i.e. lowest energy and if |φ[i]〉 is not the marked state, then fpb(φ[i]) is equal to one, i.e. having higher energy level than the ground state. The fpb(φ[i]) can be reversibly implemented by using the same technique as described for oracles in [Section 3.3.1](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_003_s_001).

The time dependent Hamiltonian that evolves the system under initial Hamiltonian to final Hamiltonian is as follows:

(3.22)*H*(*t*) = (1 − *s*(*t*)) *H*[*i**n**i*] + *s*(*t*)*H*[*f**i**n*] 

where s(t) is a continuous function with s(0) = 0 and s(T) = 1. Let eigenstates of H(t) be |*ψ*[*k*](*t*)⟩ such that:

(3.23)$\\begin{matrix} & {{fpb}\\left( q \\right){= 0;}} \\\\ & {{fpb}\\left( q \\right){= 1;}} \\\\ \\end{matrix}$ 

where *E[k]*(*t*) are the corresponding eigenvalues and *k* labels the eigenstates (*k *\= 0 indicates the ground state).

The gap between the lowest two eigenvalues, E[0] and E[1], is described by the following equation \[[32](#bodymatter-003.xhtml#b_9783110670707-003_ref_032)\]:

(3.24)$g\\left( s \\right) = \\sqrt{1 - 4\\left( {1 - \\frac{m\_{e}}{N\_{e}}} \\right)s\\left( t \\right)\\left( {1 - s\\left( t \\right)} \\right)}$ $g\_{min} = \\ \\sqrt{}\\left( {m\_{e}/N\_{e}} \\right){\\, and\\, occurs\\ at\\, s = 1/2}.$ 

The matrix element of *dH*/*dt* in [eq. (3.5)](#bodymatter-003.xhtml#b_9783110670707-003_eq_005) can be alternately expressed as follows:

(3.25)${\\langle\\frac{dH}{dt}\\rangle\_{1,0}} = \\frac{ds}{dt}{\\langle\\frac{d\\widetilde{H}}{ds}\\rangle\_{1,0}}$ 

Using [eqs. (3.5)](#bodymatter-003.xhtml#b_9783110670707-003_eq_005) and (3.[25](#bodymatter-003.xhtml#b_9783110670707-003_eq_025)), for all times t, we get new condition

(3.26)$\\left| \\frac{ds}{dt} \\right| \\leq \\varepsilon\\frac{g^{2}\\left( s \\right)}{\\left| {\\langle\\frac{d\\widetilde{H}}{ds}\\rangle}\_{1,0} \\right|}$ 

Using [eq. (3.26)](#bodymatter-003.xhtml#b_9783110670707-003_eq_026) and bounding $|{\\langle\\frac{d\\widetilde{H}}{ds}\\rangle}\_{1,0}| \\leq 1$, the Hamiltonian H(t) is evolved at a following rate:

(3.27)$\\frac{ds}{dt} = \\varepsilon g^{2}\\left( s \\right) = \\varepsilon\\left\\{ {1 - 4\\left( {1 - \\frac{m\_{e}}{N\_{e}}} \\right)s\\left( {1 - s} \\right)} \\right\\}$ 

After integration, we get:

(3.28)$t = \\frac{1}{2\\varepsilon}\\left\\{ \\frac{N\_{e}}{\\sqrt{m\_{e}(N\_{e} - m\_{e}}} \\right\\}\\left\\lbrack {\\tan^{- 1}\\left\\{ {\\left( \\sqrt{\\frac{N\_{e} - m\_{e}}{m\_{e}}} \\right)\\left( {2s - 1} \\right)} \\right\\} + \\tan^{- 1}\\left( \\sqrt{\\frac{N\_{e} -}{m\_{e}}} \\right)} \\right\\rbrack$ 

And from the above [eq. (3.28)](#bodymatter-003.xhtml#b_9783110670707-003_eq_028), s(t) can be obtained as follows:

(3.29)$s\\left( t \\right) = \\frac{1}{2}\\left\\{ {\\left( \\sqrt{\\frac{m\_{e}}{N\_{e} - m\_{e}}} \\right)\\tan\\left\\lbrack {2\\varepsilon\\left\\{ \\frac{\\sqrt{m\_{e}\\left( {N\_{e} - m\_{e}} \\right)}}{N\_{e}} \\right\\} t - \\tan^{- 1}\\left( \\sqrt{\\frac{N\_{e} - m\_{e}}{m\_{e}}} \\right)} \\right\\rbrack + 1} \\right\\}$ 

Therefore, the total computation time T can be calculated by equating s = 1 in [eq. (3.28)](#bodymatter-003.xhtml#b_9783110670707-003_eq_028), we get:

(3.30)$T = \\frac{1}{\\varepsilon}\\left\\{ \\frac{N\_{e}}{\\sqrt{m\_{e}\\left( {N\_{e} - m\_{e}} \\right)}} \\right\\}\\tan^{- 1}\\left( \\sqrt{\\frac{N\_{e} - m\_{e}}{m\_{e}}} \\right)$ (3.31)$\\max\\left\\{ {\\tan^{- 1}\\left( \\sqrt{\\frac{N\_{e} - m\_{e}}{m\_{e}}} \\right)} \\right\\} \\leq \\;\\frac{\\pi}{2}\\,\\forall\\; N\_{e} > m\_{e}$ (3.32)$\\left\\{ \\frac{N\_{e}}{\\sqrt{m\_{e}\\left( {N\_{e} - m\_{e}} \\right)}} \\right\\} \\leq \\left\\{ {\\sqrt{2}\\left( \\sqrt{\\frac{N\_{e}}{m\_{e}}} \\right)} \\right\\}\\;\\forall\\; m\_{e} \\leq \\frac{N\_{e}}{2}$ 

Using above three equations i.e. from (3.30) to (3.32), we can conclude that

(3.33)$T \\leq \\frac{\\pi\\sqrt{2}}{2\\varepsilon}\\left( \\sqrt{\\frac{N\_{e}}{m\_{e}}} \\right)\\;\\forall\\; m\_{e} \\leq \\frac{N\_{e}}{2}$ 

The above result is very useful from the point of quantum search based on AQC for solving optimization problems, which have been attempted in \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\]. Further, the result in \[[32](#bodymatter-003.xhtml#b_9783110670707-003_ref_032)\] was derived for cases in which m[e] ≪ N[e]. Thus, the bounds provided here are applicable to more generic cases.

One observation, which shows that AQC is a better model than Quantum Circuit model for implementing canonical Grover’s search is that, it does not overshoot the marked element if the system is evolved for time longer than required i.e. if the rate of evolution given by [eq. (3.27)](#bodymatter-003.xhtml#b_9783110670707-003_eq_027) is slower than necessary, there is no overshooting involved as the system remains in the eigenstate of the final Hamiltonian. That is if the system is evolved at g[min] = 1/√N[e] instead of g[min ]\= √(m[e]/N[e]), where m[e] > 1, then it just takes more time to evolve than necessary, but the solution is still reached, unlike Grover’s search on circuit model in which if more rotations than required are given to the state vector, then it overshoots the target state. However, in such cases, the overall computational complexity is O(√N[e]) instead of O(√(N[e]/m[e])), which when m[e] is large would be a substantial slow down.

## 3.7 AQC based minimum searching algorithm

The algorithm presented by Durr and Hoyer \[[50](#bodymatter-003.xhtml#b_9783110670707-003_ref_050)\] on quantum circuit model can be modified to fit into AQC framework as follows:

1.  Set m[e] = N[e]/2 and termination counter I = 0.
    
2.  Select the initial threshold, Yth, by randomly taking a sample.
    
3.  Initialize H[ini] as given in [eq. (3.19)](#bodymatter-003.xhtml#b_9783110670707-003_eq_019).
    
4.  Let H[fin] be as given by eq. (3.20).
    
    where function fpb (φ[i]) has been implemented as follows:
    
    *I**f*(*D*\[*ϕ*[*i*]\] < *Y**t**h*) // *D* *i**s* *t**h**e* *t**a**b**l**e* *f**p**b*(*ϕ*[*i*]) = 0 
    
    else
    
    *f**p**b*(*ϕ*[*i*]) = 1 
5.  Employ Hamiltonian Ĥ(s) = (1-s(t))\*H[ini] + s(t)\*H[fin], where s(t) is as given [eq. (3.29)](#bodymatter-003.xhtml#b_9783110670707-003_eq_029).
    
6.  Perform evolution of the system for time T as per [eq. (3.1)](#bodymatter-003.xhtml#b_9783110670707-003_eq_001). The time T is given by [eq. (3.33)](#bodymatter-003.xhtml#b_9783110670707-003_eq_033).
    
7.  Measure the qubits in |Ψ(T)〉 to find the solution of the problem and present result by classical evaluation as objective function value, y.
    
8.  If D\[y\] is less than threshold Yth, then
    
    *Y**t**h* = *D*\[*y*\] 
9.  If I > T[tot], then Stop
    
10.  I = I + T
     
11.  m[e] = m[e]−1
     
12.  Go to c.
     

Theorem 1: The above algorithm finds the minimum in a database in O(√N[e]) time with error probability ε² in expectation. 

### Proof:

Let us rank all the elements in the database with rank 1 assigned to the element with minimum value and rank N[e] assigned to the element with maximum value. All other elements are also ranked according to their position, if there are several elements with same value, then rank them sequentially as they appear without breaking order with elements having different values.

The above algorithm would move through a succession of points before finding the minima, therefore, assume that it starts with the element as threshold, whose rank is N[e]/2, (which can be found by either randomly choosing the threshold by sampling the database a few times) then the total running time, T[tot], of the algorithm is as follows;

(3.34)$T\_{tot} = \\sum\\limits\_{r = 1}^{N/2}\\left\\{ {P\\left( {N\_{e},r\_{n}} \\right)T\\left( {N\_{e},r\_{n} - 1} \\right)} \\right\\}$ 

where P(N[e],r[n]) is the probability of the element with rank r[n] ever being selected and T(N[e],r[n]−1) is the expected time required to evolve the system for finding an element with a better rank than r[n].

The P(N[e],r[n]) has been shown to be independent of the database size in lemma 1 of \[[50](#bodymatter-003.xhtml#b_9783110670707-003_ref_050)\] and is dependent only on its rank r[n].

(3.35)*P*(*N*[*e*],*r*[*n*]) = 1/*r*[*n*] 

The T(N[e], r[n]−1) can be found by inserting the value of r[n] in [eq. (3.33)](#bodymatter-003.xhtml#b_9783110670707-003_eq_033):

(3.36)$T\\left( {N\_{e},r\_{n} - 1} \\right) = \\frac{\\pi\\sqrt{2}}{2\\varepsilon}\\left( \\sqrt{\\frac{N\_{e}}{r\_{n} - 1}} \\right)$ 

Therefore,

(3.37)$T\_{tot} = \\sum\\limits\_{r\_{n} = 2}^{\\frac{N\_{e}}{2}}\\left\\lbrack {\\frac{1}{r\_{n}}\\left\\{ {\\frac{\\pi\\sqrt{2}}{2\\varepsilon}\\left( \\sqrt{\\frac{N\_{e}}{r\_{n} - 1}} \\right)} \\right\\}} \\right\\rbrack = \\left( \\frac{\\pi\\sqrt{2}}{2\\varepsilon} \\right){\\sqrt{N}}\_{e}\\sum\\limits\_{r\_{n} = 1}^{\\frac{N\_{e}}{2}}\\left\\lbrack {\\left( \\frac{1}{r\_{n} + 1} \\right)\\left( \\frac{1}{{\\sqrt{r}}\_{n}} \\right)} \\right\\rbrack$ (3.38)$T\_{tot} = \\left( \\frac{5\\pi\\sqrt{2}}{4\\varepsilon} \\right){\\sqrt{N}}\_{e}$ 

Thus, the AQC based minimum finding algorithm can be analyzed analytically and has a better running time in expectation.

## 3.8 Adiabatic quantum optimization algorithm

The Adiabatic quantum optimization algorithm has been developed for solving unconstrained optimization problems, which have been described in [Section 3.5](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_005). The AQC based minimum finding algorithm has been used as the underlying framework for developing the optimization algorithm.

The unconstrained optimization problems in continuous domain can be converted into a finite global optimization problem as shown in [Section 3.5](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_005). Each domain point can be ranked on the basis of its objective function value i.e. the point with best objective function value can be assigned RANK 1 and the point with worst objective function value can be assigned RANK N[e]. The rest of points can similarly be assigned a suitable rank. If two or more points have same objective function value then they would be assigned different ranks, randomly chosen within the range, while maintaining their relative position with rest of the points. Thus, the points are now analogues to the index of the database, so, the optimization algorithm can be designed on the same framework as the minimum finding algorithm described in [Section 3.5](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_005).

Adiabatic quantum optimization algorithm for solving Unconstrained Global Optimization problem is as follows:

1.  Set m[e] = N[e]/2 and termination counter I = 0.
    
2.  Compute Yth by taking a random sample of domain point x.
    
3.  Construct Beginning Hamiltonian H[ini], which would be same for all the UCOP problems.
    

*H*[*i**n**i*]\= ∑ *H*[*i**n**i*\_*i*], where

*H*[*i**n**i*] [*i*]  = *I* − |*ψ*[*i*]⟩⟨*ψ*[*i*]|,where

$|\\psi\_{i}\\rangle\\,\\, = \\,\\,\\left( {1/\\sqrt{}2} \\right) \\ast \\left( {0\\rangle\\,\\, + \\,\\,\\left( {1/\\sqrt{}2} \\right)} \\right)$ 

d.
: 

Make Problem Hamiltonian H[fin], which is specific to the particular UCOP, however the structure would remain same irrespective of the UCOP.

H[fin]|q[1]q[2]q[3]…q[n]〉 = fpb (q[1]q[2]q[3]…q[n]) |q[1]q[2]q[3]…q[n]〉

where fpb(q[1]q[2]q[3]…q[n]) is a Boolean function, which models the problem and can be constructed reversibly as follows:

If (f(q) ≥ Yth) … … for Minimization

*f**p**b*(*q*) = 0; 

else

*f**p**b*(*q*) = 1; 

where |q[1]q[2]q[3]…q[n]〉 are n qubits representing the decision variables of the UCOP being solved given eq. (3.13) and q = q[1]q[2]q[3]…q[n]. The fpb(q) would be implemented in an Oracle and so its outcome would be reflected in the state of ancilla qubit, qo. Yth is the threshold value computed from the objective function of the UCOP being solved. The first value of Yth may be assigned randomly or seeded by meta-heuristics techniques \[[57](#bodymatter-003.xhtml#b_9783110670707-003_ref_057)\].

1.  Employ Hamiltonian Ĥ(s) = (1-s(t))\*H[ini] + s(t)\*H[fin], where s(t) is as given [eq. (3.29)](#bodymatter-003.xhtml#b_9783110670707-003_eq_029).
    
2.  Perform evolution of the system for time T as per [eq. (3.1)](#bodymatter-003.xhtml#b_9783110670707-003_eq_001). The time T is given by [eq. (3.33)](#bodymatter-003.xhtml#b_9783110670707-003_eq_033).
    
3.  Measure the qubits in |Ψ(T)〉 to find the solution of the problem and present result by classical evaluation as objective function value, y.
    
4.  If y is less than threshold Yth, then
    

Yth = y – Δy where Δy ≥ 0 for minimization problem

i.
: 

If I > T[tot], then Stop, where T[tot] is given by [eq. (3.38)](#bodymatter-003.xhtml#b_9783110670707-003_eq_038)

j.
: 

I = I + T

k.
: 

m[e] = m[e]−1

l.
: 

Go to c.

### 3.8.1 Discussions

The nucleus of the proposed algorithm is a search routine designed on AQC framework to find optimal value. It adapts the evolution rate to local adiabatic condition based on local adiabatic evolution, which has O(√N[e]) run-time complexity and is asymptotically optimal as shown in \[[32](#bodymatter-003.xhtml#b_9783110670707-003_ref_032)\].

The termination of the run of algorithm for solving a particular instance of the problem is also supported by the laws of Quantum mechanics (i.e. Adiabatic Theorem) that is if no improvement is made even after considering m[e] = 1, then the search can be terminated with conclusion that no better points exists with probability 1-ε², where ε ≪ 1. This consideration makes the proposed algorithm a global optimizer.

The working of the algorithm is further illustrated with the help of an example. Let us Minimize f(x) = x² such that −1.0 < x < 1.0

The variable x is discretized between \[−1.0, 1.0\] by using 10 qubits i.e. n = 10.

The total number of domain points in search space, N = 2^n = 2^(10) = 1024.

For first iteration: Let ε = 0.707, x = 0.5; Y[th] = (0.5)² = 0.25, m[e] = 512, therefore T = 2.22 time units. If the run is successful, a new threshold would be found or else with the earlier threshold, and after reducing m[e] by 1, the second iteration would be executed, so on and so forth. Subsequently, say, after 256 iterations, lf |x| > 0.25, then it would have a high chance of success run as T for which it would be evolved is larger than required, whereas if |x| < 0.25, then T is less than required but in next few iterations, the T would become equal or larger (as m[e] is reduced) than required for a success run. Moreover, when |x| < 0.25, the performance of the algorithm is better than expected. Therefore, if the algorithm fails, it is because its performance is better than expected otherwise it is almost guaranteed to produce a good result. Thus, after running the algorithm for T[tot] time, it can be re-run for m[e] = 1 and if no improvement is found in threshold then it can be said that global optimal has been found with failure probability at most ε².

The actual running time of the algorithm can be improved further by doing some additional processing like counting the successful and unsuccessful iterations and for updating the value of m[e] as the [eq. (3.38)](#bodymatter-003.xhtml#b_9783110670707-003_eq_038) gives an average case result. However, the analytical analysis of such adaptive schemes would be difficult and is left for future studies.

AQC optimization algorithm is better than the Quantum circuit implementation of Grover Adaptive Search as the rotation count is no longer required to be guessed or randomly / heuristically assigned. Further, even if the quantum system were evolved for time duration larger than the minimum time, the system would only get closer to the ground state and would not overshoot the marked state containing the solution.

## 3.9 Conclusions

Machine learning is a branch of Artificial intelligence, which tries to develop techniques that have ability to learn from experiences. These experiences are articulated as data generated from underlying models. The goal of any machine learning technique is to abstract the underlying model reliably for specific tasks like prediction and decision making. Optimization problems are ubiquitous in machine learning and other domains like engineering and a number of specialized techniques for efficiently solving specific problems have been developed. However, general purpose techniques like enumerative strategies have run time complexity of O(N), where N is the number of domain points. Grover’s quantum search algorithm provides quadratic speed up over its classical counter parts. Baritompa et al. integrated ideas from Grover’s search into the framework of Pure adaptive search and called the new framework as Grover Adaptive search. It was further improved by Liu and Koehler. However, GAS was essentially an optimization heuristic due to which analytical analysis was difficult.

A novel quantum optimization algorithm based on Adiabatic Quantum Computation framework, which employs local evolution instead of global evolution, has been proposed. It is also inspired by the application of Grover’s Search algorithm for finding minimum solution in a database, however, the proposed algorithm solves real domain optimization problems, which are routinely solved in Machine learning algorithms. Further, the proposed algorithm has been analytically analyzed and has been shown to have the same signature of quadratic speed up of Grover’s search algorithm. Baritompa et al. had made a similar effort on gate-based quantum computation model for solving unconstrained global optimization problem. However, the proposed AQC based algorithm is conceptually better than gate-based model as there is no fear of overshooting the optima, which is a major concern in gate-based models, when a priori knowledge of the number of optimal solutions is not available, whereas the optimal solutions are encoded as the ground state of the problem Hamiltonian. The problem of overshooting in gate-based model could further increase convergence time in real world implementations.

In future, we would like to develop a simulator and architecture of a hybrid Classical and Adiabatic Quantum Computer on which we can demonstrate operations of our proposal of Quantum Optimization Algorithm for Machine Learning techniques, which would require addressing several challenging issues like implementation of loss function on a quantum computer and weights updating in learning mechanism.

## References

\[1\]Kline, R. R. Cybernetics, Automata Studies and the Dartmouth Conference on Artificial Intelligence. IEEE Annals of the History of Computing, October–December, 2011, IEEE Computer Society. [→](#bodymatter-003.xhtml#xref_d6256e29109)

\[2\]Russell, S., & Norvig, P. Artificial Intelligence: A Modern Approach, 3rd ed. Prentice Hall Press Upper Saddle River, NJ, USA, 2009. [→](#bodymatter-003.xhtml#xref_d6256e29112)

\[3\]Columbus, L. Why AI Is The Future of Financial Services. August, 2019. [https://www.forbes.com/sites/louiscolumbus/2019/08/15/why-ai-is-the-future-of-financial-services/#452381ba3847](https://www.forbes.com/sites/louiscolumbus/2019/08/15/why-ai-is-the-future-of-financial-services/23%452381ba3847) [→](#bodymatter-003.xhtml#xref_d6256e29115)

\[4\]Insight Team. AI And Healthcare: A Giant Opportunity. Februrary, 2019. [https://www.forbes.com/sites/insights-intelai/2019/02/11/ai-and-healthcare-a-giant-opportunity/#35e679924c68](https://www.forbes.com/sites/insights-intelai/2019/02/11/ai-and-healthcare-a-giant-opportunity/23%35e679924c68) [→](#bodymatter-003.xhtml#xref_d6256e29118)

\[5\]Grühn, B., Kässer, M., Köstring, J., Padhi, A., & Tschiesner, A. Winning tomorrow’s car buyers using artificial intelligence in marketing and sales. February, 2019. [https://www.mckinsey.com/industries/automotive-and-assembly/our-insights/winning-tomorrows-car-buyers-using-artificial-intelligence-in-marketing-and-sales](https://www.mckinsey.com/industries/automotive-and-assembly/our-insights/winning-tomorrows-car-buyers-using-artificial-intelligence-in-marketing-and-sales) [→](#bodymatter-003.xhtml#xref_d6256e29121)

\[6\]Teich, D. A. Artificial Intelligence Can Address Social Media Risks And Rewards. March, 2019. [https://www.forbes.com/sites/davidteich/2019/03/27/artificial-intelligence-can-address-social-media-risks-and-rewards/#295c4dc9686c](https://www.forbes.com/sites/davidteich/2019/03/27/artificial-intelligence-can-address-social-media-risks-and-rewards/23%295c4dc9686c) [→](#bodymatter-003.xhtml#xref_d6256e29125)

\[7\]Hoy, M. B. Alexa, Siri, Cortana, and More: An Introduction to Voice Assistants. Medical Reference Services Quarterly. 2018, 37(1),81–88. doi:10.1080/02763869.2018.1404391. PMID 29327988 [→](#bodymatter-003.xhtml#xref_d6256e29128)

\[8\]Zhang, G., Patuwo, B. E., & Hu, M. Y. Forecasting with artificial neural networks: The state of the art. International Journal of Forecasting, 1998, 14(1),35–62, ISSN 0169-2070. https://doi.org/10.1016/S0169-2070(97)00044-7 [→](#bodymatter-003.xhtml#xref_d6256e29134)

\[9\]Chang, C., & Ling, C. LIBSVM: A library for support vector machines. ACM Transactions on Intelligent Systems and Technology. 2011, 2(3). 10.1145/1961189.1961199 [→](#bodymatter-003.xhtml#xref_d6256e29137)

\[10\]Jain, A. K. Data clustering: 50 years beyond K-means. Pattern Recognition Letters. 2010, 31(8),651–666, ISSN 0167-8655. https://doi.org/10.1016/j.patrec.2009.09.011 [→](#bodymatter-003.xhtml#xref_d6256e29140)

\[11\]Liu, H., Miao, E. M., Wei, X. Y., & Zhuang, X. D. Robust modeling method for thermal error of CNC machine tools based on ridge regression algorithm. International Journal of Machine Tools and Manufacture. 2017, 113, 35–48, ISSN 0890-6955. https://doi.org/10.1016/j.ijmachtools.2016.11.001 [→](#bodymatter-003.xhtml#xref_d6256e29143)

\[12\]Garg, P., Neider, D., Madhusudan, P., & Roth, D. Learning invariants using decision trees and implication counterexamples. Proceedings of the 43rd Annual ACM SIGPLAN-SIGACT Symposium on Principles of Programming Languages (POPL ‘16). ACM, New York, NY, USA, 2016, 499–512. [https://doi.org/10.1145/2837614.2837664](https://doi.org/10.1145/2837614.2837664) [→](#bodymatter-003.xhtml#xref_d6256e29146)

\[13\]Tangirala, A. K. Principles of System Identification: Theory and Practice 1st Edition. CRC Press, 2014. [a](#bodymatter-003.xhtml#xref_d6256e29152), [b](#bodymatter-003.xhtml#xref_d6256e29174), [c](#bodymatter-003.xhtml#xref_d6256e29195)

\[14\]LeCun, Y., Bengio, Y., & and Hinton, G. Deep learning. Nature. 2015, 521, 436–444. [→](#bodymatter-003.xhtml#xref_d6256e29177)

\[15\]Poplin, R., Varadarajan, A. V., Blumer, K., Liu, Y., McConnell, M. V., Corrado, G. S., Peng, L., & Webster, D. R. Prediction of cardiovascular risk factors from retinal fundus photographs via deep learning. Nature Biomedical Engineering. 2018, 2, 158–164. [→](#bodymatter-003.xhtml#xref_d6256e29180)

\[16\]Rebentrost, P., Mohseni, M., & Lloyd, S. Quantum support vector machine for big data classification. Phys. Rev. Lett. 2014, 113, 130503. [→](#bodymatter-003.xhtml#xref_d6256e29186)

\[17\]Giovannetti, V., Lloyd, S., & Maccone, L. Quantum Random Access Memory. Phys. Rev. Lett. 2008, 100, 160501. [→](#bodymatter-003.xhtml#xref_d6256e29189)

\[18\]Optimization for Machine Learning. Sra, S., Nowozin, S., & Wright, S. J. (Eds). The MIT Press, 2011. [→](#bodymatter-003.xhtml#xref_d6256e29192)

\[19\]Rebentrost, P., Schuld, M., Wossnig, L., Petruccione, F., & Lloyd, S. Quantum gradient descent and Newton’s method for constrained polynomial optimization. New J. Phys. 2019, 21, 073023. [a](#bodymatter-003.xhtml#xref_d6256e29198), [b](#bodymatter-003.xhtml#xref_d6256e29208), [c](#bodymatter-003.xhtml#xref_d6256e29214)

\[20\]Klymko, C., Sullivan, B. D., & Humble, T. S. Adiabatic quantum programming: minor embedding with hard faults. Quantum Inf Process. 2014, 13(709). https://doi.org/10.1007/s11128-013-0683-9 [→](#bodymatter-003.xhtml#xref_d6256e29202)

\[21\]Harrow, A. W., Hassidim, A., & Lloyd, S. Quantum algorithm for linear systems of equations. Phys. Rev. Lett. 2009, 103, 150502. [→](#bodymatter-003.xhtml#xref_d6256e29211)

\[22\]Farhi, E., Goldstone, J., Gutmann, S., Lapan, J., Lundgren, A., & Preda, D. A quantum adiabatic evolution algorithm applied to random instances of an NP-complete problem. Science. 2001, 292(5516),472–476. [a](#bodymatter-003.xhtml#xref_d6256e29255), [b](#bodymatter-003.xhtml#xref_d6256e29277), [c](#bodymatter-003.xhtml#xref_d6256e29280), [d](#bodymatter-003.xhtml#xref_d6256e29286), [e](#bodymatter-003.xhtml#xref_d6256e29349)

\[23\]Farhi, E., Goldstone, J., Gutmann, S., & Nagaj, D. How to Make the Quantum Adiabatic Algorithm Fail. International Journal of Quantum Information. 2008, 6(503). [a](#bodymatter-003.xhtml#xref_d6256e29283), [b](#bodymatter-003.xhtml#xref_d6256e29290)

\[24\]Reichardt, B. The quantum adiabatic optimization algorithm and local minima. Proceedings of the 36th Annual Symposium on the Theory of Computing (IEEE). Computer Society Press, New York, 2004, 279–287. [→](#bodymatter-003.xhtml#xref_d6256e29293)

\[25\]van Dam, W., Mosca, M., & Vazirani, U. How powerful is adiabatic quantum computation? Proceedings of 42nd Annual IEEE Symposium on Foundations of Computer Science. 2001, 279–287. [→](#bodymatter-003.xhtml#xref_d6256e29299)

\[26\]Amin, M. H. S. Effect of Local Minima on Adiabatic Quantum Optimization. Physical Review Letters. 2008, 100, 130503. [→](#bodymatter-003.xhtml#xref_d6256e29302)

\[27\]Farhi, E., Goldstone, J., Gutmann, S., Meyer, H. B., & Shor, P. Quantum Adiabatic Algorithms, Small Gaps, and Different Paths. 2009. arXiv:0909.4766v2 \[quant-ph\] [→](#bodymatter-003.xhtml#xref_d6256e29305)

\[28\]Altshuler, B., Krovi, H., & Roland, J. Anderson localization makes adiabatic quantum optimization fail. Proceedings of National Academy of Science. USA, 2010, 107(28),12446–12450. [a](#bodymatter-003.xhtml#xref_d6256e29309), [b](#bodymatter-003.xhtml#xref_d6256e29318)

\[29\]Choi, V. Different Adiabatic Quantum Optimization Algorithms for the NP-Complete Exact Cover and 3SAT Problems. 2011. arXiv:1010.1221v3 [→](#bodymatter-003.xhtml#xref_d6256e29312)

\[30\]Dickson, N. G., Amin, M. H. S. Does Adiabatic Quantum Optimization Truly Fail for NP-complete problems? 2011. arXiv:1010.0669 [a](#bodymatter-003.xhtml#xref_d6256e29315), [b](#bodymatter-003.xhtml#xref_d6256e29324)

\[31\]Farhi, E., Goldstone, J., Gutmann, S., & Sipser, M., Quantum Computation by Adiabatic Evolution. 2000. arΧiv:quant-ph/0001106v1 [a](#bodymatter-003.xhtml#xref_d6256e29330), [b](#bodymatter-003.xhtml#xref_d6256e29398), [c](#bodymatter-003.xhtml#xref_d6256e29469), [d](#bodymatter-003.xhtml#xref_d6256e33108), [e](#bodymatter-003.xhtml#xref_d6256e33456)

\[32\]Roland, J. & Cerf, N. Quantum search by local adiabatic evolution, Physical Review A. 2002, 65(4), 042308. [a](#bodymatter-003.xhtml#xref_d6256e29333), [b](#bodymatter-003.xhtml#xref_d6256e33462), [c](#bodymatter-003.xhtml#xref_d6256e33465), [d](#bodymatter-003.xhtml#xref_d6256e34181), [e](#bodymatter-003.xhtml#xref_d6256e35274), [f](#bodymatter-003.xhtml#xref_d6256e36695)

\[33\]Rezkhani, A. T., Pimachev, A. K., & Lidar, D. A. Accuracy versus run time in an adiabatic quantum search. Physical Review A. 2010, 82, 052305. [→](#bodymatter-003.xhtml#xref_d6256e29336)

\[34\]Zhang, Y.Y & Lu, S.F. Quantum search by partial adiabatic evolution. Phys. Rev. A. 2010, 82, 034304. [→](#bodymatter-003.xhtml#xref_d6256e29342)

\[35\]Aharonov, D., Dam, W. van Kempe, J., Landau, Z., Lloyd, S., & Regev O. Adiabatic quantum computation is equivalent to standard quantum computation. Proceedings of 45th Annual IEEE Symposium on Foundations of Computer Science. 2004, 42–51. [→](#bodymatter-003.xhtml#xref_d6256e29352)

\[36\]Mizel, A., Lidar, D. A., & Mitchell, M. W. Simple proof of equivalence between adiabatic quantum computation and the circuit model. Phys. Rev. Lett. 2007, 99, 070502. [→](#bodymatter-003.xhtml#xref_d6256e29355)

\[37\]Brady, L. T. & van Dam, W. Necessary adiabatic run times in quantum optimization. Phys. Rev. 2017, A 95, 032335. [→](#bodymatter-003.xhtml#xref_d6256e29358)

\[38\]Guerreschi, G. G. & Matsuura, A. Y. QAOA for Max-Cut requires hundreds of qubits for quantum speed-up. Scientific Reports. 2019, 9, 6903. [→](#bodymatter-003.xhtml#xref_d6256e29365)

\[39\]Farhi, E., Goldstone, J., & Gutmann, S. A Quantum Approximate Optimization Algorithm. 2014. [http://arxiv.org/abs/1411.4028v1](http://arxiv.org/abs/1411.4028v1) [→](#bodymatter-003.xhtml#xref_d6256e29368)

\[40\]McClean, J. R., Romero, J., Babbush, R., & and Aspuru-Guzik, A. The theory of variational hybrid quantum-classical algorithms. New J. Phys. 2016, 18, 023023. [→](#bodymatter-003.xhtml#xref_d6256e29371)

\[41\]Mani, A. & and Patvardhan, C. Some Investigations for Solving Constrained Optimization Problems using Adiabatic Quantum Computation. 2011 Eighth International Conference on Information Technology: New Generations. Las Vegas, NV, 2011, 1101–1102. doi:10.1109/ITNG.2011.218 [→](#bodymatter-003.xhtml#xref_d6256e29380)

\[42\]Albash, T. & Lidar, D. A. Adiabatic quantum computation. Rev. Mod. Phys. 2018, 90, 015002. [→](#bodymatter-003.xhtml#xref_d6256e29395)

\[43\]Kato, T. On the Adiabatic Theorem of Quantum Mechanics. Journal of the Physical Society of Japan. 1950, 5(6),435–439. [→](#bodymatter-003.xhtml#xref_d6256e29401)

\[44\]Marzlin, K. P. & Sanders, B. C. Inconsistency in the application of the adiabatic theorem. Phys. Rev. Lett. 2004, 93, 160408. [→](#bodymatter-003.xhtml#xref_d6256e30247)

\[45\]Amin, M. H. S. Consistency of the Adiabatic Theorem. Physical Review Letters. 2009, 102, 220401. [→](#bodymatter-003.xhtml#xref_d6256e30250)

\[46\]Tong, D. M., Singh, K., Kwek, L. C., & Oh, C. H. Sufficiency Criterion for the Validity of the Adiabatic Approximation. Phys. Rev. Lett. 2007, 98, 150402. [a](#bodymatter-003.xhtml#xref_d6256e30253), [b](#bodymatter-003.xhtml#xref_d6256e30675)

\[47\]Grover, L. K. Quantum Mechanics helps in searching for a needle in a haystack. Phys. Rev. Lett. 1997, 78(2),325–328. [→](#bodymatter-003.xhtml#xref_d6256e30682)

\[48\]Boyer, M., Brassard, G., Hoyer, P., & Tapp, A. Tight bounds on quantum searching. Fortschr. Phys. 1998, 46, 493–506. [a](#bodymatter-003.xhtml#xref_d6256e30685), [b](#bodymatter-003.xhtml#xref_d6256e30694), [c](#bodymatter-003.xhtml#xref_d6256e31309), [d](#bodymatter-003.xhtml#xref_d6256e32560)

\[49\]Tulsi, T. A., Grover, L. K., & Patel, A. A new algorithm for fixed point quantum search. Quantum information & computation. 2006, 6, 483–494. arXiv: quantph/0505007 [→](#bodymatter-003.xhtml#xref_d6256e30688)

\[50\]Dürr, C. & Hoyer, P. A Quantum Algorithm for Finding the Minimum. [http://lanl.arxiv.org/abd/quant-ph/9607014](http://lanl.arxiv.org/abd/quant-ph/9607014) [a](#bodymatter-003.xhtml#xref_d6256e30691), [b](#bodymatter-003.xhtml#xref_d6256e31312), [c](#bodymatter-003.xhtml#xref_d6256e32557), [d](#bodymatter-003.xhtml#xref_d6256e35332), [e](#bodymatter-003.xhtml#xref_d6256e35788)

\[51\]Kenigsberg, D. Grover’s Quantum Search Algorithm and Mixed States. M.Sc. Thesis. Israel Institute of Technology, October, 2001. [→](#bodymatter-003.xhtml#xref_d6256e30814)

\[52\]Baritompa, W. P., Bulger, D. W., & Wood, G. R. Grover’s Quantum Algorithm applied to Global Optimization. SIAM J. OPTIM. 2005, 15(4),1170–1184. [a](#bodymatter-003.xhtml#xref_d6256e30854), [b](#bodymatter-003.xhtml#xref_d6256e30991), [c](#bodymatter-003.xhtml#xref_d6256e30997), [d](#bodymatter-003.xhtml#xref_d6256e31318), [e](#bodymatter-003.xhtml#xref_d6256e31904), [f](#bodymatter-003.xhtml#xref_d6256e32563), [g](#bodymatter-003.xhtml#xref_d6256e33090), [h](#bodymatter-003.xhtml#xref_d6256e35271)

\[53\]Zabinsky, Z. B. & Smith, R. L. Pure adaptive search in global optimization. Math. Programming. 1992, 53, 323–338. [→](#bodymatter-003.xhtml#xref_d6256e31089)

\[54\]Zabinsky, Z. B, Wood, G. R., Steel, M. A., & Baritompa, W. P. Pure adaptive search for finite global optimization. Math. Programming. 1995, 69, 443–448. [a](#bodymatter-003.xhtml#xref_d6256e31092), [b](#bodymatter-003.xhtml#xref_d6256e31104), [c](#bodymatter-003.xhtml#xref_d6256e31113), [d](#bodymatter-003.xhtml#xref_d6256e31124), [e](#bodymatter-003.xhtml#xref_d6256e31265)

\[55\]Bulger, D. W., Alexander, D. L. J., Baritompa, W. P., Wood, G. R., & Zabinsky, Z. B. Expected hitting time for backtracking adaptive search. Optimization. 2004, 53, 189–202. [→](#bodymatter-003.xhtml#xref_d6256e31095)

\[56\]Liu, Y., Koehler, G. J. Using modifications to Grover’s Search algorithm for quantum global optimization. European Journal of Operational Research. 2010, 207(2),620–632. [a](#bodymatter-003.xhtml#xref_d6256e31306), [b](#bodymatter-003.xhtml#xref_d6256e31922), [c](#bodymatter-003.xhtml#xref_d6256e32566)

\[57\]Michalewicz, Z. Genetic Algorithms + Data Structures = Evolution Programs. 3rd ed., Berlin, Springer-Verlag, 1996. [a](#bodymatter-003.xhtml#xref_d6256e32903), [b](#bodymatter-003.xhtml#xref_d6256e36591)

\[58\]Goldberg, D. Genetic Algorithms in Search, Optimization and Machine Learning. Addison-Wesley Publishing Company, Inc., NY, USA, 1989. [→](#bodymatter-003.xhtml#xref_d6256e32906)

\[59\]Bellman, R. Adaptive Control Processes: A Guided Tour, Princeton University Press, 1961. [→](#bodymatter-003.xhtml#xref_d6256e32909)

\[60\]Protopopescu, V., Barhen, J. Quantum Algorithms for Continuous Global Optimization. Proceedings of the 34th Workshop on Optimization and Control with Applications, Erice, Sicily, July 9–17, 2001. [→](#bodymatter-003.xhtml#xref_d6256e32918)

# 4 From classical to quantum machine learning

Arit Kumar Bishwas AIIT, Amity University, Information Technology, Noida, Uttar Pradesh, India Ashish Mani EEE, ASET, Amity University, EEE, ASET, G012A, E-I Block, Sector 125, 201303, Noida, Uttar Pradesh, India Vasile Palade Coventry University, Faculty of Engineering and Computing, Coventry University, Coventry, UK 

#### Abstract

In recent years, Machine Learning (ML) has started to be ubiquitously applied to practically most of the human activity domains. Although traditional, or classical machine learning (CML) approaches are useful in solving many complex tasks, there are still many challenges that such approaches are facing. One issue is the limitation in the processing speed of current silicon technology based computers, which made researchers look to the underlying quantum theory principles and try to run complex quantum computing experiments. In future, in order to develop more complex artificial intelligence systems, we will have to process huge amounts of data at high speed, and the existing classical computing will probably not serve well this purpose, due to silicon technology limitations. A different technology that can handle huge volumes of data and at high speed is needed. In recent years, the progress in quantum computing research seems to provide hopeful answers to overcome the speed processing barrier. This is very important for the training of many computational intensive machine learning models. The latest advancements in quantum technology appear to be promising, which can boost the field of machine learning overall. In this chapter, we discuss the transition from classical machine learning to quantum machine learning (QML) and explore the recent progress in this domain. QML is not only associated with the development of high-performance machine learning algorithms that can run on a quantum computer with significant performance improvements but also has a very diverse meaning in other aspects. The chapter tried to touch those aspects in brief too, but the main focus is on the advancements in the field of developing machine learning algorithms that will run on a quantum computer.

Keywords:  quantum algorithm,  quantum random access memory (QRAM),  quantum deep learning,  quantum computation,  

## 4.1 Introduction

Machine learning is an important and popular field of study these days when Artificial Intelligence and intelligent algorithms have become embedded in our everyday life. Machine learning models are trained with large amounts of data using some mathematical and statistical based algorithms. Machine learning algorithms are categorized into two broad classes – supervised and unsupervised learning algorithms. In supervised learning, data are provided in the form of labelled data. In the case of unsupervised learning, the datasets are not labelled. In recent years, machine learning has demonstrated great visibility and publicity in applications to many important domains of real life, such as medical image processing, online product recommendation systems, financial modelling and prediction, risk evaluation, human language processing, etc. The recent advancements in deep learning research opened even more possibilities for solving complex problems. In machine learning, data play a vital role. Some problems can be solved well with less data, but deep learning requires huge volumes of data. Apart from the issue of availability of big datasets, another crucial factor is the processing and learning speed of the system. Deep learning algorithms are computationally very intensive. Although by using GPUs and high-performance computing systems, this problem can be somehow alleviated, it still takes a long time to perform machine learning (and especially deep learning) on big data. The rule of thumb is that, in order to train with more data, we would require more processing power. To develop more complex future artificial intelligence systems that process a huge amount of data, the existing classical computing technologies will probably not be sufficient, due to the limitations related to the silicon-based technology. We need a different technology, which can handle the processing speed issue and which can process huge volumes of data. Classical computers are now part of our lives and help us in solving complex problems, but still, there are great challenges in solving some of the problems (for example optimization problems) whose computational complexities increases at a very high scale with a small increase in inputs. These kind of problems are very difficult or not possible to solve with the classical computers. Quantum computing is the answer to overcome these processing issues. Quantum computer’s computational power scales significantly as the system size grows due to its unique properties which are not found in classical systems, and two of the most important properties are – superposition & entanglement. Section 3 discusses these properties in detail.

The term quantum machine learning (QML) mostly refers to classical machine learning algorithms \[[1](#bodymatter-004.xhtml#b_9783110670707-004_ref_001), [2](#bodymatter-004.xhtml#b_9783110670707-004_ref_002)\] that can be run on a quantum computer. This involves mostly researchers working on developing quantum versions of classical machine learning algorithms, concerned mainly with the speed-up factors for the training procedure. Apart from this, the term QML also has a general connotation. Developing a fully functional commercial quantum computer is a very active field, but it is still not clear if we can have one to work in the near future. In recent time, researchers focused on developing small quantum subroutines/devices which can combine with classical machine learning approaches to get the quantum advantages to some ex-tent \[[3](#bodymatter-004.xhtml#b_9783110670707-004_ref_003)\]. These quantum subroutines/devices can be designed to solve some of the complex tasks which are computationally difficult in the classical domain \[[4](#bodymatter-004.xhtml#b_9783110670707-004_ref_004), [5](#bodymatter-004.xhtml#b_9783110670707-004_ref_005), [6](#bodymatter-004.xhtml#b_9783110670707-004_ref_006)\].

Some recent works have also exhibited that by using quantum algorithms we can analyze quantum states \[[7](#bodymatter-004.xhtml#b_9783110670707-004_ref_007)\]. The term QML is also associated with analyzing the data generated from quantum experiments. Applying machine learning in analyzing quantum phase transitions is a very classic example of this \[[8](#bodymatter-004.xhtml#b_9783110670707-004_ref_008), [9](#bodymatter-004.xhtml#b_9783110670707-004_ref_009), [10](#bodymatter-004.xhtml#b_9783110670707-004_ref_010), [11](#bodymatter-004.xhtml#b_9783110670707-004_ref_011)\].

Another active research field in QML is to understand the structural and operational similarities between certain physical systems and deep learning. Deep leaning uses some mathematical and numerical techniques that are inspired by quantum formulation, and in the same way, deep learning explores some structural and procedural equivalences with quantum systems \[[12](#bodymatter-004.xhtml#b_9783110670707-004_ref_012), [13](#bodymatter-004.xhtml#b_9783110670707-004_ref_013), [14](#bodymatter-004.xhtml#b_9783110670707-004_ref_014)\].

Big companies like D-Waves \[[15](#bodymatter-004.xhtml#b_9783110670707-004_ref_015)\], IBM \[[16](#bodymatter-004.xhtml#b_9783110670707-004_ref_016)\], and Google \[[17](#bodymatter-004.xhtml#b_9783110670707-004_ref_017)\] demonstrated some progress in building a quantum computer. Here, the D-Wave’s model is based on the adiabatic quantum process \[[18](#bodymatter-004.xhtml#b_9783110670707-004_ref_018)\] and the IBM \[[16](#bodymatter-004.xhtml#b_9783110670707-004_ref_016)\] is working on mostly non-adiabatic models. IBM released the IBM-Q quantum computer to be accessed and used freely (with the restriction of 5 qubits system access at the time). Apart from the progress in quantum hardware, there is very active research going on in the area of developing quantum algorithms. Some of the most notable quantum algorithms are Grover’s search \[[10](#bodymatter-004.xhtml#b_9783110670707-004_ref_010)\], Shor’s algorithm \[[19](#bodymatter-004.xhtml#b_9783110670707-004_ref_019)\], HLL \[[20](#bodymatter-004.xhtml#b_9783110670707-004_ref_020)\], etc., which demonstrated significant speed-up gains insolving computational problems. In recent years, the advancement in quantum technologies has involved some state-of-the-art machine learning approaches \[[21](#bodymatter-004.xhtml#b_9783110670707-004_ref_021), [22](#bodymatter-004.xhtml#b_9783110670707-004_ref_022), [23](#bodymatter-004.xhtml#b_9783110670707-004_ref_023), [24](#bodymatter-004.xhtml#b_9783110670707-004_ref_024), [25](#bodymatter-004.xhtml#b_9783110670707-004_ref_025)\]. These quantum machine learning algorithms are exponentially faster than their classical counterparts.

In this chapter, our focus will be on a category of classical machine learning algorithms that can run on a quantum computer. At first, we discuss quantum computing basics in brief, including some well-known techniques that are useful in the advancement of quantum machine learning algorithms, followed by the recent advancements in the field of quantum machine learning algorithms.

## 4.2 Overview of quantum computing

### 4.2.1 Hilbert space & Dirac notation

A Hilbert space ℂ^(*n*) is an abstract vector space which is very useful for representing a quantum system. The Dirac notation \[[26](#bodymatter-004.xhtml#b_9783110670707-004_ref_026)\] is a very convenient way of defining vectors in the Hilbert space, named after the Nobel laureate Paul Dirac. In Dirac notation, a vector *V* is represented as:

(4.1)$V = \\begin{bmatrix} v\_{0} \\\\ v\_{1} \\\\ \\vdots \\\\ v\_{n} \\\\ \\end{bmatrix} = |V\\rangle$ 

Here, |*V*⟩ is known as “ket *V*”. In the same context, the dual vector of |*V*⟩ is known as “bra *V*” and represented as:

(4.2)$\\langle V| = \\left\\lbrack {\\overset{‾}{v\_{0}}\\ \\overset{‾}{v\_{1}}\\ldots\\overset{‾}{v\_{n}}} \\right\\rbrack = \\overset{‾}{V^{T}}$ 

We define the inner product of vectors U and V in Dirac notation as:

(4.3)$\\langle U|V\\rangle = \\left\\lbrack {\\overset{‾}{u\_{0}}\\ \\overset{‾}{u\_{1}}\\ldots\\overset{‾}{u\_{n}}} \\right\\rbrack\\begin{bmatrix} v\_{0} \\\\ v\_{1} \\\\ \\vdots \\\\ v\_{n} \\\\ \\end{bmatrix} = \\ \\overset{‾}{U^{T}}V$ 

Also, the length of the vector in the Hilbert space, known as “Norm”, is defined as:

(4.4)${\\parallel {|V\\rangle} \\parallel} = \\sqrt{\\langle V|V\\rangle}$ 

Similarly, the outer product can be defined as follows with the Dirac notation:

(4.5)$\\left| {V\\rangle\\langle U} \\right| = \\begin{bmatrix} v\_{0} \\\\ v\_{1} \\\\ \\vdots \\\\ v\_{n} \\\\ \\end{bmatrix}\\left\\lbrack {\\overset{‾}{u\_{0}}\\ \\overset{‾}{u\_{1}}\\ldots\\overset{‾}{u\_{m}}} \\right\\rbrack = \\begin{bmatrix} {v\_{0}\\overset{‾}{u\_{0}}} & \\cdots & {v\_{0}\\overset{‾}{u\_{m}}} \\\\ \\vdots & \\ddots & \\vdots \\\\ {v\_{n}\\overset{‾}{u\_{0}}} & \\cdots & {v\_{n}\\overset{‾}{u\_{m}}} \\\\ \\end{bmatrix}$ 

### 4.2.2 Quantum bits and gates

In classical computation, the fundamental unit for the building block of any computation is the bit. In the same context, the fundamental component of any quantum computation is known as a qubit. In classical computation, a base-2 number known as a bit can be either 0 or 1, but a qubit can also be in both states, 0 and 1, at the same time. Mathematically we represent a qubit as a two-dimensional state space in ℂ² with orthogonal basis vectors |0⟩ & |1⟩ as,

(4.6) |*ψ*⟩ = *a*[0]|0⟩ + *a*[1]|1⟩; |*a*[0]|² + |*a*[1]|²\= 1 

The states |0⟩ & |1⟩ are in superposition (this will be covered in detail in the [next section](#bodymatter-004.xhtml#b_9783110670707-004_s_004_s_002)) and the complex scalar amplitudes *a*[0]  &  *a*[1] are the probabilities of obtaining the values |0⟩ & |1⟩ upon measurement, respectively.

A single qubit is of no significant use, but a bunch of qubits can involve much more practical usability. Like a classical computer, the quantum register is the collection of qubits. In the quantum register, a qubit in a register can be in a superposition of |0⟩ & |1⟩, and upon measurement collapse to a bit. So, if there is a *n* qubits register, then there will be 2^(*n*) possible states in superposition. For example, suppose we have a 3 qubits register, then there will be 2³ = 8 states in superposition as shown:

(4.7)$\\begin{matrix} & {|\\psi\_{3}\\rangle = \\sum\\limits\_{i = 0}^{2^{3} - 1}a\_{i}|i\\rangle = a\_{0}|000\\rangle + a\_{1}|001\\rangle + a\_{2}|010\\rangle + a\_{3}|011\\rangle + a\_{4}|100\\rangle + a\_{5}|101\\rangle} \\\\ & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, + a\_{6}|110\\rangle + a\_{7}|111\\rangle} \\\\ \\end{matrix}$ 

Like classical computing, we have quantum gates too, which are used to perform some kind of operations on qubits and registers. The followings are some of the most important quantum gates:

*   a.Hadamard gate (*H*) – This is a very important quantum gate. The Hadamard gate transforms a qubit into a superposition of qubits as shown:
    
*   (4.8)$H|0\\rangle = \\frac{|0\\rangle + |1\\rangle}{\\sqrt{2}}$ 
*   (4.9)$H|1\\rangle = \\frac{|0\\rangle - |1\\rangle}{\\sqrt{2}}$ 
*   b.Pauli-X quantum gate (*X*) – Pauli–X is quantum equivalent to classical NOT gate. It swaps the amplitudes of the |0⟩ & |1⟩.
    
*   c. Pauli-Y quantum gate (*Y*) – It swaps the amplitudes of |0⟩ & |1⟩, multiplies each amplitude by *i*, and then negates the amplitude of |1⟩.
    

d.Pauli-Z quantum gate (*Z*) – When applying a Pauli-Z quantum gate to a qubit, it negates the amplitude of the qubit if it is |1⟩, otherwise, it performs no action if the qubit is |0⟩.

### 4.2.3 Superposition

The Quantum superposition \[[27](#bodymatter-004.xhtml#b_9783110670707-004_ref_027)\] is a phenomenon in the quantum world in which quantum particles appear to exist in multiple states simultaneously. It is the fundamental principle of quantum mechanics. When the particle is measured in superposition, the superposition collapses and results in correspond to only one of the possible states.

Thus, at any instance, a qubit can be in a superposition of both states |0⟩ and |1⟩ simultaneously, such as:

(4.10)$\\left| {W\\rangle = a} \\right|0\\rangle + b|1\\rangle = \\begin{pmatrix} a \\\\ b \\\\ \\end{pmatrix}$ 

where the coefficients *a* and *b* are complex numbers and the amplitudes of the components |0⟩ and |1⟩ respectively, possessing the following property:

(4.11)|*a*|² + |*b*|² = 1 

### 4.2.4 Entanglement

Quantum entanglement \[[28](#bodymatter-004.xhtml#b_9783110670707-004_ref_028)\] is a very important property of quantum mechanics, in which qubits interact with each other instantaneously irrespective of the distances between them through an unknown way of communication that is not limited to the speed of light. Correlated particles remain entangled as long as they are isolated irrespective of the distance between them.

If we cannot factor a multi-qubit state into the direct product of a definite state for each qubit individually, then the states are entangled. Hence, a pair of qubits *A* and *B* are entangled if and only if we cannot write the joint state |*ψ*[*A**B*]⟩ as the product of a state for qubit A and a state for qubit B, i.e., if and only if |*ψ*[*A**B*]⟩=|*ψ*[*A*]⟩ ⊗ |*ψ*[*B*]⟩ for any choice of states |*ψ*[*A*]⟩ and |*ψ*[*B*]⟩.

We are considering two non-interacting systems *A* and *B*, with respect to finite dimensional Hilbert spaces *H*[*A*] and *H*[*B*].

*H*[*A*] ⊗ *H*[*B*] is the tensor product of the composite system in the Hilbert space. The state of the composite system is |*ψ*[*A*]⟩ ⊗ |*ψ*[*B*]⟩, where the first system is in state |*ψ*[*A*]⟩ and the second in the state |*ψ*[*B*]⟩.

The above represented states of the composite system are separable states. But, all states are not, in general, the separable states.

By fixing a basis |*i*[*A*]⟩ for *H*[*A*] and a basis | *j*[*B*]⟩ for *H*[*B*], the most general state in *H*[*A*] ⊗ *H*[*B*] is of the form:

(4.12)$|\\psi\_{AB}\\rangle = \\sum\\limits\_{i,j}c\_{ij}\\left| {i\_{A}\\rangle\\; \\otimes \\;} \\right|j\_{B}\\rangle$ 

This state is separable if

(4.13)*c*[*i**j*] = *c*[*i*]^(*A*)*c*[*j*]^(*B*) 

yielding:

(4.14)$|{\\psi\_{A}\\rangle = \\sum\\limits\_{i,j}c\_{i}^{A}|{i\_{A}\\rangle\\;{and}}\\;|\\psi\_{B}\\rangle = \\sum\\limits\_{j}c\_{i}^{B}}|j\_{B}\\rangle\\ $ 

It is inseparable if

(4.15)*c*[*i**j*] ≠ *c*[*i*]^(*A*)*c*[*j*]^(*B*) 

If a state is not separable, it is known as entangled state.

For example, the following composite state is an entangled state:

(4.16)$\\frac{1}{\\sqrt{2}}\\left( {\\left| {0\_{A}\\rangle\\; \\otimes \\;} \\right|1\_{B}\\rangle - \\left| {1\_{A}\\rangle\\; \\otimes \\;} \\right|0\_{B}\\rangle} \\right),$ 

where |0[*A*]⟩ & |1[*A*]⟩ are two basis vectors of *H*[*A*] and |0[*B*] & |1[*B*] are two basis vectors of *H*[*B*].

### 4.2.5 Quantum adiabatic model

If a quantum system is set in the ground state of a Hamiltonian *H*, the system remains in this state. According to the adiabatic theorem \[[18](#bodymatter-004.xhtml#b_9783110670707-004_ref_018)\], the system will still stay close to the ground state as long as the variation is very slow enough. Suppose that |*E*[0]; *t*⟩ & |*E*[1]; *t*⟩ are the ground and first excited states of the Hamiltonian *H*(*t*), where *E*[0](*t*) and *E*[1](*t*) are the energies corresponding to the ground and first excited states, respectively. We then define the minimum gap between these two eigenvalues as:

(4.17)$g\_{min} = \\min\\limits\_{0 \\leq t \\leq T}\\left\\lbrack {E\_{1}\\left( t \\right) - E\_{0}\\left( t \\right)} \\right\\rbrack$ 

So, when we prepared the system at time *t* = 0 in its ground state |*E*[0]; 0 and allow it to evolve under the Hamiltonian *H*(*t*), we find:

(4.18)|⟨*E*[0];*T*|*ψ*(*T*)⟩|² ≥ 1 − *ε*² 

where $1 \\gg \\varepsilon \\geq \\frac{\\max\\limits\_{0 \\leq t \\leq T}\\left| \\left\\langle \\frac{dH}{dt} \\right\\rangle\_{1,0} \\right|}{g\_{min}^{2}}$, and $\\left\\langle \\frac{dH}{dt} \\right\\rangle\_{1,0} = \\left\\langle {E\_{1};\\, t|\\frac{dH}{dt}|E\_{0};\\, t} \\right\\rangle$

### 4.2.6 SWAP-test

A SWAP-test estimates |⟨*ψ*[1]|*ψ*[2]⟩|², when given two input quantum states |*ψ*[1]⟩ and |*ψ*[2]⟩, with precision $O\\left( \\frac{1}{\\sqrt{M}} \\right)$, where *M* is the number of times the measurement has been done.

### 4.2.7 Quantum algorithms

Quantum algorithms are the special type of algorithms that are written for running on a quantum computer. These algorithms are based on the principles of quantum mechanics. This is one very active research area, and recent research works show that many of the quantum versions of classical algorithms are way more efficient in terms of computational complexity, with some of them being exponentially faster than the classical counterparts. Some of the most known quantum algorithms are Grover’s search algorithm \[[10](#bodymatter-004.xhtml#b_9783110670707-004_ref_010)\], Shore’s algorithm \[[19](#bodymatter-004.xhtml#b_9783110670707-004_ref_019)\], quantum support vector machine \[[21](#bodymatter-004.xhtml#b_9783110670707-004_ref_021), [23](#bodymatter-004.xhtml#b_9783110670707-004_ref_023), [24](#bodymatter-004.xhtml#b_9783110670707-004_ref_024)\], and the HHL algorithm \[[20](#bodymatter-004.xhtml#b_9783110670707-004_ref_020)\].

## 4.3 Essential foundations for building a quantum machine learning framework

In this section, we discuss the essential foundations to develop quantum machine learning algorithms. These foundational concepts are very important. No single concept can be used to develop a quantum machine algorithm, and different concepts are used to cultivate different algorithms. In this section, we explain some of the very key foundational concepts which provide support in building quantum machine learning algorithms. We have discussed how different approaches used these concepts to articulate a variety of quantum machine algorithms in Section 4.4 & [4.5](#bodymatter-004.xhtml#b_9783110670707-004_s_004_s_005).

### 4.3.1 Grover’s search algorithm

Grover’s search algorithm \[[10](#bodymatter-004.xhtml#b_9783110670707-004_ref_010)\] is a quantum search algorithm which performs the search to find a unique item from an unordered set of *N* items with $O(\\sqrt{N})$ run time complexity. The best counter classical search algorithm performs with *O*(*N*) runtime complexity. The algorithm is as follows \[[29](#bodymatter-004.xhtml#b_9783110670707-004_ref_029)\]:

#### Algorithm 1:

Grover’s Search Algorithm

1.  Initialize quantum state |0⟩^( ⊗ *n*)
    
2.  Apply the Hadamard transformation to all the qubits
    

$|\\psi\\rangle = H^{\\otimes n}|0\\rangle^{\\otimes n} = \\frac{1}{\\sqrt{2^{n}}}\\sum\\limits\_{y = 0}^{2^{n} - 1}|y\\rangle$ 

1.  Apply the Grover iteration function R $\\approx \\frac{\\pi}{4}\\sqrt{2^{n}}$ times
    

\[(2|*ψ*⟩⟨*ψ*|−*I*)𝒪\]^(*R*)|*ψ*⟩≈|*y*[0] 

1.  Perform the measurement for output, *y*[0]
    

### 4.3.2 Quantum random access memory

Quantum random access memory (QRAM) \[[30](#bodymatter-004.xhtml#b_9783110670707-004_ref_030)\] is the random access memory in a quantum paradigm. It encompasses the output and the address registers which are composed of qubits. The QRAM permits to access the data quantum mechanically and access the memory in coherent quantum superposition. The address register embraces a superposition of addresses. The data register *D**R* stores the output of the QRAM as a superposition of data, which is associated with the address register *R*[*A**D**R*],

(4.19)∑[*j*]*ψ*[*j*]|*j*⟩[*R*[*A**D**R*]]→ ∑[*j*]*ψ*[*j*]|*j*⟩[*A**D**R*]|*D*[*j*]⟩[*D**R*] 

where *R*[*A**D**R*] holds a superposition of addresses ∑[*j*]*ψ*[*j*]|*j*⟩[*R*[*A**D**R*]], and *D*[*j*] is the *j*^(*t**h*) memory cell content. Reconstructing any quantum state from QRAM takes *O*(*l**o**g* *N*) steps, where *N* is the complex vector dimension.

### 4.3.3 Quantum dot product

We discuss a quantum-based process for dot product evaluation \[[31](#bodymatter-004.xhtml#b_9783110670707-004_ref_031)\] of two training inputs (normalized),  ∥ *X⃗*[*i*]⟩ &  ∥ *X⃗*[*j*]⟩ (in the quantum arrangement), in a linear kernel. For calculating a dot product of  ∥ *X⃗*[*i*]⟩ &  ∥ *X⃗*[*j*]⟩, at first, we generate two quantum states  ∥ *ψ*⟩ *a**n**d*  ∥ *ϕ*⟩ using an ancilla variable. Next, we estimate the squared norms sum of the two training inputs, say parameter *Z* = |*X⃗*[*i*]|² + |*X⃗*[*j*]|². At last, we execute a swap test to implement a projective measurement on the ancilla alone.

Initially, by querying the QRAM, we construct a quantum state |*ψ*⟩:

(4.20)$|\\psi\\rangle = \\frac{1}{\\sqrt{2}}\\left( {\\left| {0\\rangle} \\right|{\\overrightarrow{X}}\_{i}\\rangle + \\left| {1\\rangle} \\right|{\\overrightarrow{X}}\_{j}\\rangle} \\right)$ 

Let us assume another quantum state:

(4.21)$|\\xi\\rangle = \\left( {\\frac{1}{\\sqrt{2}}\\left( {\\left| {0\\rangle -} \\right|1\\rangle} \\right)\\; \\otimes \\;|0\\rangle} \\right)$ 

We put on a unitary transformation \[[32](#bodymatter-004.xhtml#b_9783110670707-004_ref_032)\] *e*^( − *i**H**t*) to the state |*ξ*⟩, where *H* = (( ∥ *X⃗*[*i*] ∥ |0⟩⟨0| +  ∥ *X⃗*[*j*] ∥ |1⟩⟨1|) ⊗ *σ*[*x*]) is a Hamiltonian. This outcomes the following state,

(4.22)$\\begin{matrix} & \\left\\lbrack {\\frac{1}{\\sqrt{2}}\\left( {cos\\left( {{\\parallel {\\overrightarrow{X}}\_{i} \\parallel}t} \\right)\\left| {0\\rangle - cos\\left( {{\\parallel {\\overrightarrow{X}}\_{j} \\parallel}t} \\right)} \\right|1\\rangle} \\right) \\otimes |0\\rangle} \\right\\rbrack \\\\ & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, - \\left\\lbrack {\\frac{i}{\\sqrt{2}}\\left( {sin\\left( {{\\parallel {\\overrightarrow{X}}\_{i} \\parallel}t} \\right)\\left| {0\\rangle - sin\\left( {\\parallel {\\overrightarrow{X}}\_{j} \\parallel} \\right)} \\right|1\\rangle} \\right) \\otimes |1\\rangle} \\right\\rbrack} \\\\ \\end{matrix}$ 

With an appropriate choice of *t*,  we now measure the ancilla bit, where  *X⃗*[*i*]*t*, *X⃗*[*j*]*t* ≪ 1, which outcomes in the state:

(4.23)$|\\phi\\rangle = \\frac{1}{\\sqrt{\\left( {{\\parallel {\\overrightarrow{X}}\_{i} \\parallel}^{2} + {\\parallel {\\overrightarrow{X}}\_{j} \\parallel}^{2}} \\right)}}\\left( {{\\parallel {\\overrightarrow{X}}\_{i} \\parallel}\\left| {0\\rangle - {\\parallel {\\overrightarrow{X}}\_{j} \\parallel}} \\right|1\\rangle} \\right),$ 

with probability $\\frac{1}{2}{\\lbrack{({{\\parallel {\\overrightarrow{X}}\_{i} \\parallel}^{2} + {\\parallel {\\overrightarrow{X}}\_{j} \\parallel}^{2}})t}\\rbrack^{2}}$.

This sanctions the estimation of the squared norms sum of |*X⃗*[*i*] ⟩ &  |*X⃗*[*j*]⟩. By applying quantum counting, we can estimate ( ∥ *X⃗*[*i*]∥² +  ∥ *X⃗*[*j*]∥²) and generate the quantum state |*ϕ*⟩ with accuracy *ϵ*. The complexity will be *O* (*ϵ*^( − 1)). Using an ancilla alone, we then execute a swap test with states |*ψ*⟩ & |*ϕ*⟩. If |*ψ*⟩ & |*ϕ*⟩ are equal then the measurement gives us a zero. Thus, the overall complexity in evaluating a single dot product of the training instances, considering the QRAM access \[[30](#bodymatter-004.xhtml#b_9783110670707-004_ref_030)\], estimating ( ∥ *X⃗*[*i*]∥² +  ∥ *X⃗*[*j*]∥²), and fabricating the quantum state |*ϕ*⟩ is *O* (*ϵ*^( − 1) *l**o**g* *N*).

### 4.3.4 The HHL algorithm

Harrow, Hassidim, and Lloyd \[[20](#bodymatter-004.xhtml#b_9783110670707-004_ref_020)\] developed the HHL algorithm which quantum mechanically inverts a system of linear equations. This algorithm is one of the most significant and fundamental quantum algorithms, and the base for constructing many QML algorithms. The algorithm pursues to solve the system of equations  *A**x⃗* = *b⃗* in a quantum computer. Quantum mechanically it is represented as *A*|*x*⟩ = |*b*⟩, where *A* is a Hermitian matrix. *b⃗* is expressed as a quantum state |*b*⟩ = ∑[*n*]*b*[*n*]|*E*[*n*]⟩ over *l**o**g*[2]*N* qubits where *E*[*n*] is an eigenvector of *A* with eigenvalue *λ*[*n*] ≥ *Λ*, and *x⃗* is stated as |*x*⟩. The algorithm aims to solve |*x*⟩ = *A*^( − 1)|*b*⟩, where *A*^( − 1) is the inverse of the *A*. We then compute *λ*[*n*] by applying the phase estimation. By uncomputing the phase-estimation we get $\\sum\_{n}b\_{n}|E\_{n}\\rangle\\left( {\\frac{\\Lambda}{\\lambda\_{n}}|1\\rangle + \\sqrt{1 - \\frac{\\Lambda^{2}}{\\lambda\_{n}^{2}}}|0\\rangle} \\right)$, where $\\frac{\\Lambda}{\\lambda\_{n}}$ is the angle of arcsin through which an ancillary qubit is rotated. To succeed, we apply *O*(||*A*||/*Λ*) number of times the state preparation circuit after applying amplitude amplification.

As compared to the classical counterpart, the algorithm claims exponential speed-up gain under certain problem statements. The algorithm takes *O*((*l**o**g**N*)²) quantum states to output, whereas it takes *O*(*N**l**o**g**N*) steps to output in a classical computer.

### 4.3.5 Quantum principal component analysis

Principal component analysis (PCA) \[[33](#bodymatter-004.xhtml#b_9783110670707-004_ref_033)\] is a very important technique for dimensionality reduction. In a more formal way, we can define that PCA operates by diagonalizing the covariance matrix *C* = ∑[*j*]*v⃗**v⃗*[*j*]^(*T*) of the data, where *T* is the transpose operation. The covariance matrix encapsulates the correlations between data’s different components. The covariance matrix in the form of eigenvectors and eigenvalues can be represented as *C* = ∑[*k*]*e*[*k*]*c⃗*[*k*]*c⃗*[*k*]^†, where *e*[*k*] are the eigenvalues correspond to the eigenvectors *c⃗*[*k*] of *C*. The few eigenvalues which are large as compared to the rests, are known as the principal components. Each of the principal components are then considered as the new feature vectors. The classical algorithm for PCA works in *O*(*d*²) runtime complexity, where *d* is the dimension of the Hilbert space. In quantum PCA \[[33](#bodymatter-004.xhtml#b_9783110670707-004_ref_033)\], a randomly chosen data vector is mapped into a quantum state using QRAM \[[30](#bodymatter-004.xhtml#b_9783110670707-004_ref_030)\]. The resulting state has a density matrix $\\rho = \\frac{1}{N}\\sum\_{j}\\left| {v\_{j}\\rangle\\langle v\_{j}} \\right|$, where N is the cardinality of the data vector set. Using density matrix exponentiation \[[34](#bodymatter-004.xhtml#b_9783110670707-004_ref_034)\] with the quantum phase estimation algorithm \[[35](#bodymatter-004.xhtml#b_9783110670707-004_ref_035)\], and repeating the data sampling, allow us to decompose the data vectors into principal components. The quantum PCA algorithm works in *O*((*l**o**g**d*)²) runtime complexity.

## 4.4 Quantum machine learning approaches

### 4.4.1 HHL or quantum amplitude based approaches

The objective of amplitude encoding based machine learning algorithms \[[9](#bodymatter-004.xhtml#b_9783110670707-004_ref_009), [11](#bodymatter-004.xhtml#b_9783110670707-004_ref_011), [20](#bodymatter-004.xhtml#b_9783110670707-004_ref_020), [33](#bodymatter-004.xhtml#b_9783110670707-004_ref_033), [36](#bodymatter-004.xhtml#b_9783110670707-004_ref_036), [37](#bodymatter-004.xhtml#b_9783110670707-004_ref_037), [38](#bodymatter-004.xhtml#b_9783110670707-004_ref_038), [39](#bodymatter-004.xhtml#b_9783110670707-004_ref_039), [40](#bodymatter-004.xhtml#b_9783110670707-004_ref_040)\] is to articulate quantum machine learning algorithms whose resources grow in polynomial runtime with the  *n* qubits, and expands to a logarithmic growth with amplitudes and thus the input dimension. Many QML algorithms based on this approach uses the speedup advantages by solving a system of linear equations quantum mechanically \[[20](#bodymatter-004.xhtml#b_9783110670707-004_ref_020)\]. Quantum matrix inversion is one of the main core processes in solving the system of linear equations exponentially faster than the classical counterpart. Some of the notable quantum machine learning algorithms based on amplitude encoding approach are the quantum support vector machine \[[21](#bodymatter-004.xhtml#b_9783110670707-004_ref_021), [22](#bodymatter-004.xhtml#b_9783110670707-004_ref_022), [23](#bodymatter-004.xhtml#b_9783110670707-004_ref_023)\] and least-square linear regression \[[37](#bodymatter-004.xhtml#b_9783110670707-004_ref_037), [38](#bodymatter-004.xhtml#b_9783110670707-004_ref_038)\].

### 4.4.2 Grover’s search-based approaches

Machine learning algorithms based on Grover’s search algorithms, which use the technique of amplitude amplification to unfold an unstructured search problem with a quadratic runtime speedup, apply Grover’s search subroutine to solve a larger problem. Quantum K-Means \[[25](#bodymatter-004.xhtml#b_9783110670707-004_ref_025)\], K-Median \[[41](#bodymatter-004.xhtml#b_9783110670707-004_ref_041)\], and k-nearest neighbors \[[42](#bodymatter-004.xhtml#b_9783110670707-004_ref_042)\] are some of the machine learning algorithms which use Grover’s search algorithms as a subroutine to solve the machine learning task. Another recent use of the Grove’s search subroutine is in training the perceptron \[[43](#bodymatter-004.xhtml#b_9783110670707-004_ref_043)\].

### 4.4.3 Quantum annealing based approaches

Very recently, some experiments have been done based on quantum annealing \[[44](#bodymatter-004.xhtml#b_9783110670707-004_ref_044)\]. In this work, the researchers used a quantum annealer to classify and rank the transcription factors binding to study how the proteins (in a gene) identify and specifically bind to their DNA targets. The researchers used the D-Wave system to implement the quantum annealing algorithm. Here, the machine learning techniques have been the effective tools to disclose interaction mechanism at the genetic level.

## 4.5 Recent progress in quantum machine learning algorithms

The research in developing quantum machine learning algorithms has exponentially grown in recent years, and day by day new interesting quantum machine learning algorithms are being published. Here, we are covering the most ground-breaking and popular algorithms which demonstrated significant state-of-the-art performances as compared to their classical counterparts.

### 4.5.1 Quantum binary least square support vector machine

The quantum binary least square support vector machine is a break-through in the field of QML, where the authors, Rebentrost et al. \[[21](#bodymatter-004.xhtml#b_9783110670707-004_ref_021)\], demonstrated an exponential speedup gain in support vector machine formulation.

In the least square SVM, the optimization problem is transformed into a system of linear equations which encompasses the kernel matrix for solving the optimization problem. We solve the system of linear equations in a much faster way by solving the least squares formulation and speeding up the kernel matrix calculations. The following areas where we take the quantum advantages to improve the performance of the SVM are:

1.  Data preparation with quantum random access memory (QRAM) – One of the challenging tasks in quantum machine learning is to prepare the data set for feeding into the quantum systems for processing. QRAM helps in preparing the classical data set into the quantum form. QRAM takes *O*(*l**o**g*[2] *d*) steps to query the information from memory for reconstructing a state, where *d* is the dimension of the feature vector.
    
2.  Kernel matrix calculation – The dot product evaluation plays the main role in the kernel matrix calculation. So, if we get the speed up advantages in the dot product evaluation in the quantum formulation, it will imply overall speedup gain in the kernel matrix calculation. In \[[35](#bodymatter-004.xhtml#b_9783110670707-004_ref_035)\], authors have discussed the faster way to do dot product calculation with the help of quantum properties. Also, the exponentiation of the inverse of the normalized kernel matrix *K*^( − 1) is performed in a quantum paradigm. As we have discussed earlier, QRAM takes only *O*(*l**o**g*[2]*d*) steps to query for reconstructing a state, thus a single dot product with QRAM takes *O* (*ϵ*^( − 1) *l**o**g*[2] *d*) steps, where *ϵ* is the accuracy.
    
3.  Least square formulation – The speedup gain is possible during the training phase because of the quantum mechanical implementation of the exponentially faster eigenvector formulation in the non-sparse density matrices \[[35](#bodymatter-004.xhtml#b_9783110670707-004_ref_035)\], the sparse matrix simulation \[[45](#bodymatter-004.xhtml#b_9783110670707-004_ref_045)\], and the matrix inversion algorithm \[[35](#bodymatter-004.xhtml#b_9783110670707-004_ref_035)\].
    

The least square SVM is represented as the following formulation:

(4.24)$\\widehat{F}(\\left| {b,\\ \\overrightarrow{\\alpha}\\rangle) =} \\right|\\overrightarrow{y}\\rangle,\\ \\widehat{F} = \\begin{bmatrix} 0 & 1^{T} \\\\ 1 & {K + \\gamma^{- 1}I} \\\\ \\end{bmatrix},$ 

where $\\widehat{F} = \\frac{F}{trF}$ is the normalized *F*, and *t**r**F* is a trace of *F*. The target is to solve the optimization problem, *F̂*(|*b*, *α⃗*⟩)=|*y⃗*⟩, for the parameters *b* and *α⃗*. Here, *K* is the kernel matrix.

### 4.5.2 Quantum multiclass support vector machine

The SVM is a binary class classification algorithm. To handle multiclass classification, we use *one-against-all* and *all-pair* algorithms. The quantum multiclass support vector machine (SVM) is the generalized version of the quantum binary SVM. In \[[23](#bodymatter-004.xhtml#b_9783110670707-004_ref_023)\], the authors discussed two techniques: the quantum version of the *one-against-all* as well as the quantum version of *all-pair* algorithms. In *one-against-all*, we first construct and train *k* binary classifiers and then each of these classifiers classify a given unknown input. The class for which the corresponding classifier’s probability confidence score is the highest, is selected as the predicted class. In *all-pair*, we construct *k*(*k*−1)/2 classifiers. Each classifier is trained with a dataset which contains one primary class data and the rest of the data for another class, i.e., we make pairwise datasets and train the classifiers, resulting in *k*(*k*−1)/2 total classifiers. When an unknown input is to get predicted, these all *k*(*k*−1)/2 classifiers predict the class for the given input and by applying voting mechanism we select the class to be predicted. The following algorithms show the quantum version of these two approaches, for detail explanations please refer to \[[22](#bodymatter-004.xhtml#b_9783110670707-004_ref_022), [23](#bodymatter-004.xhtml#b_9783110670707-004_ref_023)\].

#### Algorithm 2:

Quantum One-Against-All Algorithm

1.  *initialize the index* *I*[*i**n**d**e**x*] = *a**n**y* *r**a**n**d**o**n* *e**l**e**m**e**n**t*, 1 ≤ *I*[*i**n**d**e**x*] ≤ *k*
    
2.  *initialize* |*V*[*q**n*]⟩ *as the vector of all classified class probabilities in QRAM*
    
3.  *while* (*P*[*m*] < *P*[*t**h**r**e**s**h**o**l**d*])
    
4.  *initialize the memory as* $|\\Psi\\rangle = \\frac{1}{\\sqrt{k}}\\sum\_{r}|r\\rangle|I\_{index}\\rangle$
    
5.  *GROVER-QUANTUM-SEARCH*  (|*Ψ*⟩,|*V*[*q**n*]⟩, *I*[*i**n**d**e**x*])
    
6.  *if* (|*V*[*q**n*]⟩\[*I*[*i**n**d**e**x*\_*n**e**w*]\] > |*V*[*q**n*]⟩\[*I*[*i**n**d**e**x*]\])
    
7.  *I*[*i**n**d**e**x*]\= *I*[*i**n**d**e**x*\_*n**e**w*]
    
8.  *return* *I*[*i**n**d**e**x*]
    

#### Algorithm 3:

Quantum All-Pair Algorithm

1.  *initialize* *c**l**a**s**s* = *a**n**y* *r**a**n**d**o**m* *e**l**e**m**e**n**t*, 1 ≤ *c**l**a**s**s*\_*i**n**d**e**x* ≤ *k*
    
2.  *initialize* |*V*[*q*]⟩ *as the vector of all classified classes*
    
3.  *initialize frequency estimate* *s*[*c**l**a**s**s*\_*i**n**d**e**x*] *with any very small value*
    
4.  *INITIAL-FREQUENCY-COUNT* ( *c**l**a**s**s*\_*i**n**d**e**x*, *s*[*c**l**a**s**s*[*i**n**d**e**x*]])
    
5.  *while* (*t**o**t**a**l* *r**u**n**n**i**n**g* *t**i**m**e*<*O* (*l**o**g**k*))
    
6.  *initialize the memory* |*C*[*i*]⟩ = ∑[*j*]*β*[*i*, *j*]|*j*⟩
    
7.  *initialize the memory as*
    

$|\\psi\_{c}\\rangle = \\sum\\limits\_{i = 0}^{k - 1}|i\\rangle|C\_{i}\\rangle|class\\\_ index\\rangle|s\_{class\\\_ index}\\rangle$ 

1.  *GROVER-QUANTUM-SEARCH* (|*ψ*[*c*]⟩,|*V*[*q*]⟩, *c**l**a**s**s*\_*i**n**d**e**x*, *s*[*c**l**a**s**s*\_*i**n**d**e**x*])
    
2.  *MEASURE-REGISTER* (|*ψ*[*c*]⟩)
    
3.  *if* $\\left( {s\_{class\\\_ index\\\_ new} > s\_{class\\\_ index} + \\frac{\\varepsilon}{2k}} \\right)$
    
4.  *c**l**a**s**s*\_*i**n**d**e**x*\= *c**l**a**s**s*\_*i**n**d**e**x*[*n**e**w*]
    
5.  *s*[*c**l**a**s**s*\_*i**n**d**e**x*]\= *s*[*c**l**a**s**s*\_*i**n**d**e**x*\_*n**e**w*]
    
6.  *return* |*V*[*q*]⟩\[*c**l**a**s**s*\_*i**n**d**e**x*\]
    

### 4.5.3 Quantum K-means clustering

Clustering is a very important problem in machine learning and more generally falls under unsupervised learning. Clustering algorithm groups the unlabeled dataset into multiple categories based on their similar features. The *K*\-Means clustering algorithm is a very popular and simple clustering algorithm. *K*\-Means groups the unlabelled dataset into *k* categories, however, we have to specify *K*  in advance. In \[[25](#bodymatter-004.xhtml#b_9783110670707-004_ref_025)\], authors show the formulation of a *K*\-Means clustering algorithm in the quantum paradigm. In the quantum *K*\-Means, the closest centroids are calculated in the same way as in the classical version, but by using the Grover’s search \[[10](#bodymatter-004.xhtml#b_9783110670707-004_ref_010)\]. The quantum version of *k*\-Means has been claimed to be exponentially faster in runtime complexity as compared to the classical counterpart. The quantum *K*\-Means is based on an adiabatic quantum process.

Suppose the output of the quantum *K*\-Means clustering algorithm is in the following quantum state:

(4.25)$|\\xi\\rangle = M^{- 1/2}\\sum\\limits\_{l}|c\_{l}\\rangle|l\\rangle = M^{- 1/2}\\sum\\limits\_{c,l\\epsilon c}|c\\rangle|l\\rangle$ 

We construct the above output quantum state with *O* (*ϵ*^( − 1)*K* *l**o**g*(*K**M**N*)) runtime complexity, where *ϵ* is the accuracy, and with *O* (^( − 1)*l**o**g*  (*K**M**N*)) runtime complexity when the clusters are well separated. The adiabatic gap in this case is  *O*(1).

Let us first select *K* objects with labels *i*[*c*] as initial seeds. We begin with the state:

(4.26)$\\left\\{ {(MK)}^{- 1/2} \\right\\}\\sum\\limits\_{c^{\\prime}l}\\left| {c^{\\prime}\\rangle} \\right|l\\rangle\\left\\{ {\\left( K^{- 1/2} \\right)\\sum\\limits\_{c}\\left| {c\\rangle} \\right|i\_{c}\\rangle} \\right\\}^{\\otimes D}$ 

Here, *D* copies of the state permit us to evaluate the distances |*x⃗*[*l*] − *x⃗*[*i*[*c*^′]]|² in the *c*^′*l* superposition component. By applying the adiabatic algorithm with the initial Hamiltonian

(4.27)$H\_{0} = 1 - |{\\phi\\rangle\\langle\\phi}|,|{\\phi\\rangle = K^{- 0.5}\\sum\\limits\_{c^{\\prime}}}|c^{\\prime}\\rangle$ 

The initial clustering is:

(4.28)$|\\psi\_{1}\\rangle = M^{- 1/2}\\sum\\limits\_{c,l\\epsilon c}|c\\rangle|l\\rangle$ 

We evolve the initial Hamiltonian *H*[0] slow enough to the Hamiltonian:

(4.29)$H\_{2} = \\sum\\limits\_{c^{\\prime}l}\\left\\{ \\left| {{\\overrightarrow{x}}\_{l} - {\\overrightarrow{x}}\_{i\_{c^{\\prime}}}} \\right|^{2} \\right\\}\\left| {c^{\\prime}\\rangle\\langle c^{\\prime}\\left| \\otimes \\right|l\\rangle\\langle l} \\right|$ 

We can construct the separate cluster |*ϕ*[1]^(*c*) = *M*^( − 0.5)∑[*l**ϵ**c*]|*l*⟩, assuming we have *D* copies of |*ψ*[1]⟩. We can now estimate the number of quantum states *M*[*c*] in the cluster *c*. With *D* copies of |*ψ*[1]⟩ together with the clusters |*ϕ*[1]^(*c*)⟩, we evaluate the average distance between *x*[*l*] and the individual cluster’s mean

(4.30)${|{{\\overrightarrow{x}}\_{l} - {(M\_{c})}^{- 1}\\sum\\limits\_{K\\epsilon c^{\\prime}}{\\overrightarrow{x}}\_{K}}|^{2}} = \\left| {{\\overrightarrow{x}}\_{l} - {\\overrightarrow{x}}\_{c}} \\right|^{2},$ 

by applying a phase *e*^( − *i*|*x⃗*[*l*] − *x⃗*[*c*^′]|²*δ**t*) to each component |*c*^′|*l*⟩ of the superposition using the following Hamiltonian,

(4.31)$H\_{F} = \\sum\\limits\_{c^{\\prime}l}\\left\\{ \\left| {{\\overrightarrow{x}}\_{l} - {\\overrightarrow{x}}\_{c^{\\prime}}} \\right|^{2} \\right\\}\\left| {c^{\\prime}\\rangle\\langle c^{\\prime}\\left| \\otimes \\right|l\\rangle\\langle l} \\right| \\otimes I^{D}$ 

With the initial Hamiltonian *H*[0] = 1 − |*ϕ*⟩⟨*ϕ*| at the ground state, we initiate the adiabatic evolution on the state {(*M**K*)^( − 0.5)}∑[*c*^′, *l*]|*c*^′|*l*⟩|*Ω*[1]⟩^( ⊗ *D*), where |*ϕ*⟩ = *K*^( − 0.5)∑[*c*^′]|*c*^′⟩ is the superposition of the cluster centroids. We get the final state:

(4.32)$\\left\\{ {\\left( M \\right)^{- 0.5}\\sum\\limits\_{c^{\\prime}l \\in c^{\\prime}}\\left| {c^{\\prime}\\rangle} \\right|l\\rangle} \\right\\}|\\Omega\_{1}\\rangle^{\\otimes D} = \\left| {\\Omega\_{2}\\rangle} \\right|\\Omega\_{1}\\rangle^{\\otimes D}$ 

By repeating the final state *D* times, we construct *D* copies of |*Ω*[2] and keep on iterating the cluster assignment procedure until it gets converged to |*ξ*⟩.

### 4.5.4 Quantum deep learning

Deep learning (DL) revolutionized the world of machine learning with its performance for a large domain of applications. DL is an efficient and effective tool for machine learning modeling. With the development of GPUs, a very wide area opened for developing highly complex machine learning models using deep learning, which was not possible earlier without large availability of high-performance computing. Deep learning requires a large amount of training data. Processing such a huge volume of datasets is a computationally complex task, this inspired the exploration of the quantum advantages for DL algorithms. Recent progress in developing programmable photonic circuits and quantum annealers \[[46](#bodymatter-004.xhtml#b_9783110670707-004_ref_046), [47](#bodymatter-004.xhtml#b_9783110670707-004_ref_047), [48](#bodymatter-004.xhtml#b_9783110670707-004_ref_048)\] open up the possibilities of developing a quantum framework for deep learning algorithms.

The latest research on Boltzmann machine formulation in a quantum paradigm \[[49](#bodymatter-004.xhtml#b_9783110670707-004_ref_049)\] demonstrated very strong footsteps towards quantum deep learning. The current results are focusing on developing quantum deep learning algorithms which do not require a fully functional quantum computer. These quantum DL algorithms can run with quantum annealers, which are special-purpose quantum information processors and they are very easy to construct as compared to larger quantum computers.

## 4.6 Recent progress in the implementation of quantum machine learning

We discuss here some of the significant developments on implementing quantum machine learning algorithms.

In 2003 \[[50](#bodymatter-004.xhtml#b_9783110670707-004_ref_050)\], a group of researches discussed that image data can be very efficiently encoded in quantum states. This may reduce the resources to some order of magnitude to perform some specific and challenging image processing tasks. During the year of 2009 \[[51](#bodymatter-004.xhtml#b_9783110670707-004_ref_051)\], D-Wave demonstrated some remarkable results with their adiabatic D-Wave quantum system. Using regularized boosting with a non-convex objective function, researchers conducted experiments in the D-Wave system to identify cars in images. In the same year (2009), another research group showed mapping an input data and memorized the data with a Hamiltonian using a quantum Hopfield network with adiabatic quantum computation \[[52](#bodymatter-004.xhtml#b_9783110670707-004_ref_052)\].

Since 2013 \[[53](#bodymatter-004.xhtml#b_9783110670707-004_ref_053), [54](#bodymatter-004.xhtml#b_9783110670707-004_ref_054)\], NASA, Google research, and the University Space Research Association are working on exploring the D-Wave quantum computer for solving complex optimization problems, which may have an impact in solving some of the machine learning algorithms with the help of advantages offered by quantum properties. In 2015, researchers demonstrated the classification between the digit ‘6’ and ‘9’ by implementing a quantum support vector machine algorithm with an NMR (Nuclear magnetic resonance) technology on a liquid-state quantum computer \[[55](#bodymatter-004.xhtml#b_9783110670707-004_ref_055)\]. Another important result came in the same year 2015 when a research team implemented an all-optical linear classifier using non-linear photonics \[[56](#bodymatter-004.xhtml#b_9783110670707-004_ref_056)\].

Recently, IBM launched an online framework for access to their quantum computer (named IBM Q), and the system supports around 32 + qubits to work with. They allow free access up to 5 qubits to work on the real quantum computer. We can run small specific quantum routines (e.g., Grover’s search, Hadamard gate, quantum SWAP test, etc.) into this system, which can help in solving complex machine learning use cases by using the outputs of these specific small quantum subroutines \[[16](#bodymatter-004.xhtml#b_9783110670707-004_ref_016)\]. A fully functional quantum neural network is possible by implementing nonlinear interactions in the quantum dynamics, recently claimed by a research team in 2016 \[[57](#bodymatter-004.xhtml#b_9783110670707-004_ref_057)\].

Very recently, in 2017 \[[58](#bodymatter-004.xhtml#b_9783110670707-004_ref_058)\], the researchers demonstrated that their model is able to generate handwritten digits. The model is a probabilistic generative model based on arbitrary pairwise connectivity. Also in 2017, researchers encoded image information with the quantum image in a quantum system and discussed some interesting challenges on this topic \[[59](#bodymatter-004.xhtml#b_9783110670707-004_ref_059)\]. In 2017, a very interesting research work by Yao et.al. discussed the implementation of quantum image processing and its applications for detecting edges \[[60](#bodymatter-004.xhtml#b_9783110670707-004_ref_060)\].

In July 2018, Google announced the first public alpha of Cirq, an open source framework at the First International Workshop on Quantum Software and Quantum Machine Learning (QSML). This will allow developers to build quantum algorithms, which may include some simple quantum machine learning algorithms with small scale data sets, without requiring a quantum physics background \[[61](#bodymatter-004.xhtml#b_9783110670707-004_ref_061)\]. In 2020, Google announced TensorFlow Quantum which is a quantum machine learning library for rapid prototyping of hybrid quantum-classical ML models \[62\].

## 4.7 Conclusion

Quantum machine learning is a fast emerging field of research that opens new horizons for artificial intelligence based research and applications. We are seeing active research developments in this area, and with the advancement of quantum computers and quantum devices, it may solve some of the most challenging problems that are difficult to solve with classical machine learning like clustering and classification training with big data in reasonable time period. Recent advancements in deep learning helped us train complex machine learning models with the help of GPUs and high-performance computing, which demonstrated remarkable speed ups and improved accuracies. More complex machine learning problems require high volumes of data and tremendous computational power, and, due to the limitations of silicon-based chip technology, we have significant constraints on the upper bound of the computational power. Quantum based systems promise significant improvements in speed up factors as compared to the classical systems. Some of the quantum machine learning algorithms, such as the quantum binary/multiclass SVM, quantum K-Means clustering, and the quantum Boltzmann machine, have revealed substantial performance improvements with big data. However, we have important challenges that need to be addressed in order to make effective and efficient quantum machine learning algorithms, such as: how to transform classical big data into quantum form in a very efficient way; the hardware where such quantum algorithms will be run is still at initial stages of development, so proper testing and validation of these theoretical quantum machine learning models is still an issue. Also, the QML opens new doors for exploring other domains like understanding the processing of neural network based algorithms like deep learning, understanding the quantum experiments data analysis with the classical machine learning. Small quantum devices are easier to develop as compared to fully functional quantum computers. It is believed these small specific quantum devices can speed up the merging of quantum terminologies and methods with the machine learning ones and can solve many domain-specific complex problems in a hybrid framework, where such small quantum devices are used to solve a small complex task in a big complex problem domain.

## References

\[1\]Alpaydin, E. Introduction to Machine Learning. Adaptive Computation and Machine Learning. MIT Press, Cambridge, MA, 2004. [→](#bodymatter-004.xhtml#xref_d6256e39003)

\[2\]Wikipedia, cite\_note 5-2. [→](#bodymatter-004.xhtml#xref_d6256e39006)

\[3\]Schuld, M., Sinayskiy, I., & Petruccione, F. An in-troduction to quantum machine learning. Contemporary Physics. 2014, 56(2),172–185. [→](#bodymatter-004.xhtml#xref_d6256e39009)

\[4\]Benedetti, M., Realpe-Gómez, J., Biswas, R., & Perdomo-Ortiz, A. Quantum-Assisted Learning of Hard-ware-Embedded Probabilistic Graphical Models. Physical Review X. ISSN 2160-3308. 2017, 7(4),041052. arXiv:1609.02542. doi:10.1103/PhysRevX.7.041052 [→](#bodymatter-004.xhtml#xref_d6256e39012)

\[5\]Farhi, E. & Neven, H. Classification with Quantum Neural Networks on Near Term Processors. 2018-02-16. arXiv:1802.06002. [→](#bodymatter-004.xhtml#xref_d6256e39015)

\[6\]Schuld, M., Bocharov, A., Svore, K., & Wiebe, N. Circuit-centric quantum classifiers. 2018-04-02. arXiv:1804.00633. [→](#bodymatter-004.xhtml#xref_d6256e39019)

\[7\]Yu, S., Albarran-Arriagada, F., Retamal, J. C., Wang, Y. -T., Liu, W., Ke, Z.-J., Meng, Y., Li, Z.-P., and Tang, J.-S. Reconstruction of a Photonic Qubit State with Quantum Rein-forcement Learning. 2018-08-28. [→](#bodymatter-004.xhtml#xref_d6256e39027)

\[8\]Broecker, P., Assaad, F. F., & Trebst, S. Quantum phase recognition via unsupervised machine learning. 2017-07-03. arXiv:1707.00663 [→](#bodymatter-004.xhtml#xref_d6256e39030)

\[9\]Huembeli, P., Dauphin, A., & Wittek, P. Identifying Quantum Phase Transitions with Adversarial Neural Networks. Physical Review B. 2018, 97(13),134109. arXiv:1710.08382. doi:10.1103/PhysRevB.97.134109. ISSN 2469-9950 [a](#bodymatter-004.xhtml#xref_d6256e39033), [b](#bodymatter-004.xhtml#xref_d6256e44884)

\[10\]Grover, L. K. A fast quantum mechanical algorithm for database search. Proceedings, 28th Annual ACM Symposium on the Theory of Computing. May 1996, 212. [a](#bodymatter-004.xhtml#xref_d6256e39036), [b](#bodymatter-004.xhtml#xref_d6256e39074), [c](#bodymatter-004.xhtml#xref_d6256e42186), [d](#bodymatter-004.xhtml#xref_d6256e42232), [e](#bodymatter-004.xhtml#xref_d6256e47105)

\[11\]Melnikov, A. A., Nautrup, H. P., Krenn, M., Dunjko, V., Tiersch, M., Zeilinger, A., & Briegel, H. J. Active learning machine learns to create new quantum experiments. Proceedings of the National Academy of Sciences. ISSN 0027-8424. PMC 5819408. PMID 29348200. 2018. 115(6),1221–1226. arXiv:1706.00868. doi:10.1073/pnas.1714936115 [a](#bodymatter-004.xhtml#xref_d6256e39039), [b](#bodymatter-004.xhtml#xref_d6256e44887)

\[12\]Huggins, W., Patel, P., Whaley, K. B., & Stoudenmire, E. M. Towards Quantum Machine Learning with Tensor Networks. 2018. arXiv:1803.11537 [→](#bodymatter-004.xhtml#xref_d6256e39046)

\[13\]Carleo, G., Nomura, Y., & Imada, M. Constructing exact representations of quantum many-body systems with deep neural networks. 2018-02-26. arXiv:1802.09558 [→](#bodymatter-004.xhtml#xref_d6256e39049)

\[14\]Bény, C. Deep learning and the renormalization group. 2013-01-14. arXiv:1301.3124 [→](#bodymatter-004.xhtml#xref_d6256e39052)

\[15\][https://www.dwavesys.com/quantum-computing](https://www.dwavesys.com/quantum-computing) [→](#bodymatter-004.xhtml#xref_d6256e39058)

\[16\][https://quantumexperience.ng.bluemix.net/qx/experience](https://quantumexperience.ng.bluemix.net/qx/experience) [a](#bodymatter-004.xhtml#xref_d6256e39061), [b](#bodymatter-004.xhtml#xref_d6256e39070), [c](#bodymatter-004.xhtml#xref_d6256e48746)

\[17\][https://ai.google/research/teams/applied-science/quantum-ai/](https://ai.google/research/teams/applied-science/quantum-ai/) [→](#bodymatter-004.xhtml#xref_d6256e39064)

\[18\]Adiabatic Quantum Computation. Adiabatic quantum computation, Wikipedia, the free encyclopedia, 2016-06-20. [a](#bodymatter-004.xhtml#xref_d6256e39067), [b](#bodymatter-004.xhtml#xref_d6256e41625)

\[19\]Shor, P. W. AT&T Research. arxiv.org/abs/quant-ph/9508027 [a](#bodymatter-004.xhtml#xref_d6256e39077), [b](#bodymatter-004.xhtml#xref_d6256e42189)

\[20\]Harrow, A. W., Hassidim, A., & Lloyd, S. Quantum Algorithm for Linear Systems of Equations. Phys. Rev. Lett. 2009, 103, 150502. [a](#bodymatter-004.xhtml#xref_d6256e39080), [b](#bodymatter-004.xhtml#xref_d6256e42202), [c](#bodymatter-004.xhtml#xref_d6256e44093), [d](#bodymatter-004.xhtml#xref_d6256e44890), [e](#bodymatter-004.xhtml#xref_d6256e44926)

\[21\]Rebentrost, P., Mohseni, M., Lloyd, S. Quantum support vector machine for big data classification. 2014. arXiv:1307.0471v3 [a](#bodymatter-004.xhtml#xref_d6256e39083), [b](#bodymatter-004.xhtml#xref_d6256e42192), [c](#bodymatter-004.xhtml#xref_d6256e44930), [d](#bodymatter-004.xhtml#xref_d6256e45010)

\[22\]Bishwas, A. K. Big Data Classification with Quantum Multiclass SVM and Quantum One-Against-All Approach. Conference Proceedings to IEEE 2nd International Conference on Contemporary Computing and Informatics (IC3I). 2016. DOI: 10.1109/IC3I.2016.7918805 [a](#bodymatter-004.xhtml#xref_d6256e39086), [b](#bodymatter-004.xhtml#xref_d6256e44933), [c](#bodymatter-004.xhtml#xref_d6256e45551)

\[23\]Bishwas, A. K. An All-Pair Approach for Big Data Multiclass Classification with Quantum SVM. Springer Nature’s Quantum Information Processing Journal. September 2018. doi.org/10.1007/s11128-018-2046-z [a](#bodymatter-004.xhtml#xref_d6256e39089), [b](#bodymatter-004.xhtml#xref_d6256e42195), [c](#bodymatter-004.xhtml#xref_d6256e44936), [d](#bodymatter-004.xhtml#xref_d6256e45449), [e](#bodymatter-004.xhtml#xref_d6256e45554)

\[24\]Bishwas, A. K. Quantum Supervised Clustering Algorithm for Big Data. IEEE 2018 3rd International Conference for Convergence in Technology (I2CT). April 2018. DOI: 10.1109/I2CT.2018.8529799 [a](#bodymatter-004.xhtml#xref_d6256e39093), [b](#bodymatter-004.xhtml#xref_d6256e42198)

\[25\]Lloyd, S., Mohseni, M., Rebentrost, P. Quantum algorithms for supervised and unsupervised machine learning. 2013. arxiv.org/abs/1307.0411 [a](#bodymatter-004.xhtml#xref_d6256e39096), [b](#bodymatter-004.xhtml#xref_d6256e44959), [c](#bodymatter-004.xhtml#xref_d6256e47079)

\[26\][https://en.wikipedia.org/wiki/Bra%E2%80%93ket\_notation](https://en.wikipedia.org/wiki/Bra%25E2%2580%2593ket_notation) [→](#bodymatter-004.xhtml#xref_d6256e39138)

\[27\][https://en.wikipedia.org/wiki/Quantum\_superposition](https://en.wikipedia.org/wiki/Quantum_superposition) [→](#bodymatter-004.xhtml#xref_d6256e40567)

\[28\][https://en.wikipedia.org/wiki/Quantum\_entanglement](https://en.wikipedia.org/wiki/Quantum_entanglement) [→](#bodymatter-004.xhtml#xref_d6256e40763)

\[29\][https://people.cs.umass.edu/~strubell/doc/quantum\_tutorial.pdf](https://people.cs.umass.edu/~strubell/doc/quantum_tutorial.pdf) [→](#bodymatter-004.xhtml#xref_d6256e42281)

\[30\]Giovannetti, V., Lloyd, S., Maccone, L. Quantum random access memory. Phys. Rev. Lett. 2008, 100, 160501. arXiv: 0708.1879 [a](#bodymatter-004.xhtml#xref_d6256e42540), [b](#bodymatter-004.xhtml#xref_d6256e43971), [c](#bodymatter-004.xhtml#xref_d6256e44776)

\[31\][https://peterwittek.com/understanding-quantum-svms.html](https://peterwittek.com/understanding-quantum-svms.html) [→](#bodymatter-004.xhtml#xref_d6256e42821)

\[32\]Schuster, D. I., Sears, A. P., Ginossar, E., DiCarlo, F., Frunzio, L., Morton, J. J. L., Wu, H., Briggs, G. A. D., Buckley, B. B., Awschalom, D. D., & Schoelkopf, R. J. High-Cooperativity Coupling of Electron-Spin Ensembles to Superconducting Cavities. Phys. Rev. Lett. 2019, 105, 140501. [→](#bodymatter-004.xhtml#xref_d6256e43157)

\[33\]Lloyd, S., Mohseni, M., Rebentrost, P. Quantum principal component analysis. 2013. arxiv.org/abs/1307.0401 [a](#bodymatter-004.xhtml#xref_d6256e44603), [b](#bodymatter-004.xhtml#xref_d6256e44773), [c](#bodymatter-004.xhtml#xref_d6256e44893)

\[34\]Lloyd, S., Mohseni, M., Rebentrost, P. Quantum principal component analysis. Nat. Phys. 2014, 10(631). [→](#bodymatter-004.xhtml#xref_d6256e44823)

\[35\]Harrow, A. W., Hassidim, A., & Lloyd, S. Quantum Algorithm for Linear Systems of Equations. Phys. Rev. Lett. 2009, 103, 150502. [a](#bodymatter-004.xhtml#xref_d6256e44826), [b](#bodymatter-004.xhtml#xref_d6256e45069), [c](#bodymatter-004.xhtml#xref_d6256e45170), [d](#bodymatter-004.xhtml#xref_d6256e45176)

\[36\]Krenn, M. Automated Search for new Quantum Experiments. Physical Review Letters. PMID 26991161. 2016, 116(9),090405. arXiv:1509.02749. Bibcode:2016PhRvL.116i0405K. doi:10.1103/PhysRevLett.116.090405 [→](#bodymatter-004.xhtml#xref_d6256e44896)

\[37\]Wiebe, N., Braun, D., & Lloyd, S. Quantum Algorithm for Data Fitting. Physical Review Letters. PMID 23006156. 2012, 109(5), 050505. arXiv:1204.5242. Bibcode:2012PhRvL.109e0505W. doi:10.1103/PhysRevLett.109.050505 [a](#bodymatter-004.xhtml#xref_d6256e44900), [b](#bodymatter-004.xhtml#xref_d6256e44939)

\[38\]Schuld, M., Sinayskiy, I., & Petruccione, F. Prediction by linear regression on a quantum computer. Physical Review A. 2016, 94(2), 022342. arXiv:1601.07823. Bib-code:2016PhRvA.94b2342S. doi:10.1103/PhysRevA.94.02234 [a](#bodymatter-004.xhtml#xref_d6256e44903), [b](#bodymatter-004.xhtml#xref_d6256e44942)

\[39\]Zhao, Z., Fitzsimons, J. K., & Fitzsimons, J. F. Quantum assisted Gaussian process regression. 2015. arXiv:1512.03929 [→](#bodymatter-004.xhtml#xref_d6256e44906)

\[40\]Berry, D. W., Childs, A. M., & Kothari, R. Hamiltonian simulation with nearly optimal dependence on all parameters. 56th Anual Symposium on Foundations of Computer Science. IEEE. 2015, 792–809. arXiv:1501.01715. doi:10.1109/FOCS.2015.54 [→](#bodymatter-004.xhtml#xref_d6256e44909)

\[41\]Aïmeur, E., Brassard, G., & Gambs, S. Quantum speed-up for unsupervised learning. Machine Learning. ISSN 0885-6125. 2013, 90(2),261–287. doi:10.1007/s10994-012-5316-5 [→](#bodymatter-004.xhtml#xref_d6256e44962)

\[42\]Wiebe, N., Kapoor, A., & and Svore, K. Quantum Algorithms for Nearest-Neighbor Methods for Supervised and Unsupervised Learning. Quantum Information & Computation. 2014, 15(3),0318–0358. arXiv:1401.2142 [→](#bodymatter-004.xhtml#xref_d6256e44965)

\[43\]Wiebe, N., Kapoor, A., & Svore, K. M. Quantum Perceptron Models. Advances in Neural Information Processing Systems. 2016, 29, 3999–4007. arXiv:1602.04799 [→](#bodymatter-004.xhtml#xref_d6256e44968)

\[44\][https://www.nature.com/articles/s41534-018-0060-8](https://www.nature.com/articles/s41534-018-0060-8) [→](#bodymatter-004.xhtml#xref_d6256e44983)

\[45\]Berry, D. W., Ahokas, G., Cleve, R., Sanders, B. C. Efficient quantum algorithms for simulating sparse Hamiltonians. Communications in Mathematical Physics. 2007, 270, 359–371. [→](#bodymatter-004.xhtml#xref_d6256e45173)

\[46\]Adachi, S. H., Henderson, M. P. Application of quantum annealing to the training of deep neural networks. 2015. arXiv:1510.06356 \[quant-ph\] [→](#bodymatter-004.xhtml#xref_d6256e48684)

\[47\]Denil, M., de Freitas, N. Toward the implementation of a quantum rbm. NIPS Deep Learning and Unsupervised Feature Learning Workshop. 2011, 5. [→](#bodymatter-004.xhtml#xref_d6256e48687)

\[48\]Dumoulin V., Goodfellow, I. J., Courville, A., Bengio, Y. On the challenges of physical implementations of RBMs. 2013. arXiv:1312.5258 \[stat.ML\] [→](#bodymatter-004.xhtml#xref_d6256e48690)

\[49\]Amin, M. H., Andriyash, E., Rolfe, J., Kulchytskyy, B., Melko, R. Quantum Boltzmann machine. 2016. arXiv:1601.02036 \[quant-ph\] [→](#bodymatter-004.xhtml#xref_d6256e48696)

\[50\]Wadcock, J., Allen, E., Day, M., Frick, S., Hinchliff, J., Johnson, M., Morley-Short, S., Pallister, S., Price, A., & Stanisic, S. Advances in quantum machine learning. 2015. arXiv:1512.02900 [→](#bodymatter-004.xhtml#xref_d6256e48718)

\[51\]Neven, H., Denchev, V., Drew-Brook, M., Zhang, J., & Macready, W. NIPS 2009 Demonstration: Binary Classification using Hardware Implementation of Quantum Annealing. 2010. [→](#bodymatter-004.xhtml#xref_d6256e48721)

\[52\]Neigovzen, R., Neves, J. L., Sollacher, R., & Glaser, S. J. Quantum pattern recognition with liquid-state nuclear magnetic resonance. Physical Review A. 2009, 79(4), 042321. arXiv:0802.1592. doi:10.1103/PhysRevA.79.042321 [→](#bodymatter-004.xhtml#xref_d6256e48724)

\[53\]Google Quantum A.I. Lab Team. Google Plus. 31 January 2017. [→](#bodymatter-004.xhtml#xref_d6256e48730)

\[54\]NASA Quantum Artificial Intelligence Laboratory, NASA. 31 January 2017. [→](#bodymatter-004.xhtml#xref_d6256e48733)

\[55\]Li, Z., Liu, X., Xu, N., & Du, J. Experimental Realization of a Quantum Support Vector Machine. Physical Review Letters. PMID 25910101. 2015, 114(14), 140504. arXiv:1410.1054, doi:10.1103/PhysRevLett.114.140504 [→](#bodymatter-004.xhtml#xref_d6256e48736)

\[56\]Tezak, N. & Mabuchi, H. A coherent perceptron for all-optical learning. EPJ Quantum Technology. 2015, 2. arXiv:1501.01608. doi:10.1140/epjqt/s40507-015-0023-3 [→](#bodymatter-004.xhtml#xref_d6256e48739)

\[57\]Li, Y., Holloway, G., Benjamin, S., Briggs, G. Baugh, J., & Mol, J. A simple and robust quantum memristor. Physical Review B. 2017, 96(7),075446. arXiv:1612.08409. doi:10.1103/PhysRevB.96.075446 [→](#bodymatter-004.xhtml#xref_d6256e48749)

\[58\]Benedetti, M., Realpe-Gómez, J., Biswas, R., & Perdomo-Ortiz, A. Quantum-assisted learning of graphical models with arbitrary pairwise connectivity. Physical Review X. 2017, 7(4), 041052. arXiv:1609.02542. doi:10.1103/PhysRevX.7.041052 [→](#bodymatter-004.xhtml#xref_d6256e48755)

\[59\]Yan, F., Iliyasu, A., & Le, P. Quantum image processing: A review of advances in its security technologies. International Journal of Quantum Information. 2017, 15(3), 1730001. [→](#bodymatter-004.xhtml#xref_d6256e48758)

\[60\]Yao, X. W., Wang, H., Liao, Z., Chen, M. C., Pan, J., Li, J., Zhang, K., Lin, X., Wang, Z., Luo, Z., Zheng, W., Li, J., Zhao, M., Peng, X., & Suter, D. Quantum Image Processing and Its Application to Edge Detection: Theory and Experiment. Physical Review X. 2017, 7(3), 031041. arXiv:1801.01465 [→](#bodymatter-004.xhtml#xref_d6256e48761)

\[61\][https://ai.googleblog.com/2018/07/announcing-cirq-open-source-framework.html](https://ai.googleblog.com/2018/07/announcing-cirq-open-source-framework.html) [→](#bodymatter-004.xhtml#xref_d6256e48770)

\[62\][https://www.tensorflow.org/quantum](https://www.tensorflow.org/quantum) 

# 5 Quantum inspired automatic clustering algorithms: A comparative study of Genetic algorithm and Bat algorithm

Alokananda Dey RCC Institute of Information Technology, Canal South Road, Beliaghata, 700015, Kolkata, West Bengal, India. Sandip Dey Sukanta Mahavidyalaya, Jalpaiguri, West Bengal, India. Siddhartha Bhattacharyya CHRIST (Deemed to be University), RCC Institute of Information Technology, Department of Computer Science and Engineering, Hosur Road, 560029, Bangalore, Karnataka, India. Jan Platos VSB Technical University of Ostrava, Ostrava, Czech Republic. Vaclav Snasel VSB Technical University of Ostrava, Ostrava, Czech Republic. 

#### Abstract

This article is intendant to present two automatic clustering techniques of image datasets, based on quantum inspired framework with two different meta-heuristic algorithms, viz., Genetic Algorithm (GA) and Bat Algorithm (BA). This work provides two novel techniques to automatically find out the optimum clusters present in images and also provides a comparative study between the Quantum Inspired Genetic Algorithm (QIGA) and Quantum Inspired Bat Algorithm (QIBA). A comparison is also presented between these quantum inspired algorithms with their analogous classical counterparts. During the experiment, it was perceived that the quantum inspired techniques beat their classical techniques. The comparison was prepared based on the mean values of the fitness, standard deviation, standard error of the computed fitness of the cluster validity index and the optimal computational time. Finally, the supremacy of the algorithms was verified in terms of the *p*\-value which was computed by *t-test* (statistical superiority test) and ranking of the proposed procedures was produced by the Friedman test. During the computation, the betterment of the fitness was judge by a well-known cluster validity index, named, DB index. The experiments were carried out on four Berkeley image and two real life grey scale images.

Keywords:  automatic clustering,  quantum computing,  meta-heuristic algorithm,  genetic algorithm,  bat algorithm,  DB Index,  statistical test (*t-test*),  Friedman test,  

## 5.1 Introduction

Clustering \[[1](#bodymatter-005.xhtml#b_9783110670707-005_ref_001), [2](#bodymatter-005.xhtml#b_9783110670707-005_ref_002)\] is a process of separating a heterogeneous dataset of different types of objects into some meaningful sets of homogeneous objects. Mathematically clustering can be described as follows. A dataset *D**S* of *K* number of points can be represented as follows.

*D**S* = {*d**p*[1], *d**p*[2], *d**p*[3],…, *d**p*[*K*]}, in which, each *d**p*[*i*] represents a single point of the specific dataset  *D**S*, where *i* = {1, 2,…, *K*}. Now, in order to achieve a successful cluster *C**N* of the dataset *D**S* into *p* number of partition namely, {*C*[*N*][1], *C*[*N*][2],…, *C*[*N*][*p*]} the following properties must be hold.

*C*[*N*][*i*] ≠ ⌀, ∀*i* = {1, 2,…, *p*}. *C*[*N*][*i*]  ∩ *C*[*N*][*j*] = ⌀, ∀*i*, *j* = {1, 2,…, *p*} *a**n**d* *i* ≠ *j*. $\\sum\_{i = 1}^{p}{C\_{N}}\_{i} = DS.$ 

Clustering can be achieved in several ways and researchers are involved to design several methods for successful clustering, viz., K-means \[[3](#bodymatter-005.xhtml#b_9783110670707-005_ref_003)\], Partitioning methods \[[4](#bodymatter-005.xhtml#b_9783110670707-005_ref_004)\], Hierarchical clustering \[[5](#bodymatter-005.xhtml#b_9783110670707-005_ref_005)\], Model-based clustering \[[6](#bodymatter-005.xhtml#b_9783110670707-005_ref_006)\], Fuzzy clustering \[[7](#bodymatter-005.xhtml#b_9783110670707-005_ref_007)\], Density-based clustering \[[8](#bodymatter-005.xhtml#b_9783110670707-005_ref_008)\], etc. It is seen that among these methods, the K-means \[[3](#bodymatter-005.xhtml#b_9783110670707-005_ref_003)\] out performs over others. In case of K-means algorithm an *apriori* knowledge is always required about the existing number of clusters within a dataset. On the other hand, an automatic clustering technique can be developed to discover the optimum number of clusters present in the dataset, in spite of knowing very less information or without having any information about the inspected dataset, which may yields usefulness in order to solve the purpose of segmentation as well as classification problem, which influenced the researchers to explore this field of clustering with automation.

Nature inspired meta-heuristic algorithms are very much useful for providing an optimal solution from a simple or complex optimization problems within a smallest time stamp. Some renowned nature inspired population based meta-heuristic algorithms are genetic algorithm (GA) \[[9](#bodymatter-005.xhtml#b_9783110670707-005_ref_009)\], particle swarm optimization (PSO) \[[10](#bodymatter-005.xhtml#b_9783110670707-005_ref_010)\], differential evolution (DE) \[[11](#bodymatter-005.xhtml#b_9783110670707-005_ref_011)\], bacterial foraging optimization (BFO) \[[12](#bodymatter-005.xhtml#b_9783110670707-005_ref_012)\], ant colony optimization (ACO) \[[13](#bodymatter-005.xhtml#b_9783110670707-005_ref_013)\], bat algorithm \[[14](#bodymatter-005.xhtml#b_9783110670707-005_ref_014), [15](#bodymatter-005.xhtml#b_9783110670707-005_ref_015)\] etc. Some nature inspired meta-heuristic algorithms used for automatic clustering techniques are available in the literature \[[16](#bodymatter-005.xhtml#b_9783110670707-005_ref_016), [17](#bodymatter-005.xhtml#b_9783110670707-005_ref_017), [18](#bodymatter-005.xhtml#b_9783110670707-005_ref_018), [19](#bodymatter-005.xhtml#b_9783110670707-005_ref_019), [20](#bodymatter-005.xhtml#b_9783110670707-005_ref_020)\]. Though, these algorithms can be able to identify a solution from a population within a minimum time frame still they may suffer from early convergence. In order to resolve the premature convergence problem, researchers are very much interested to associate the nature inspired meta-heuristic algorithms with the silent features of quantum computing, which yields the quantum inspired techniques to flourish day by day. Various kinds of computational problems can be solved by using the effects of different quantum mechanical phenomena which are presented in \[[21](#bodymatter-005.xhtml#b_9783110670707-005_ref_021)\]. Several quantum inspired techniques associated with various meta-heuristic algorithms are invented till now and the efficiency of the quantum inspired techniques over their corresponding classical counterparts is established based on convergence, superior value of fitness and other related parameters \[[23](#bodymatter-005.xhtml#b_9783110670707-005_ref_023), [24](#bodymatter-005.xhtml#b_9783110670707-005_ref_024), [25](#bodymatter-005.xhtml#b_9783110670707-005_ref_025), [26](#bodymatter-005.xhtml#b_9783110670707-005_ref_026), [27](#bodymatter-005.xhtml#b_9783110670707-005_ref_027), [28](#bodymatter-005.xhtml#b_9783110670707-005_ref_028), [29](#bodymatter-005.xhtml#b_9783110670707-005_ref_029), [30](#bodymatter-005.xhtml#b_9783110670707-005_ref_030), [31](#bodymatter-005.xhtml#b_9783110670707-005_ref_031), [32](#bodymatter-005.xhtml#b_9783110670707-005_ref_032), [33](#bodymatter-005.xhtml#b_9783110670707-005_ref_033)\]. These type of quantum inspired algorithms are developed for solving various kinds of optimization problems like mathematical function optimization \[[34](#bodymatter-005.xhtml#b_9783110670707-005_ref_034)\], combinational optimization problem (knapsack problem) \[[35](#bodymatter-005.xhtml#b_9783110670707-005_ref_035)\], multilevel image thresh holding \[[23](#bodymatter-005.xhtml#b_9783110670707-005_ref_023), [24](#bodymatter-005.xhtml#b_9783110670707-005_ref_024), [25](#bodymatter-005.xhtml#b_9783110670707-005_ref_025), [26](#bodymatter-005.xhtml#b_9783110670707-005_ref_026), [27](#bodymatter-005.xhtml#b_9783110670707-005_ref_027)\], image analysis \[[22](#bodymatter-005.xhtml#b_9783110670707-005_ref_022)\], automatic clustering \[[28](#bodymatter-005.xhtml#b_9783110670707-005_ref_028), [29](#bodymatter-005.xhtml#b_9783110670707-005_ref_029), [30](#bodymatter-005.xhtml#b_9783110670707-005_ref_030), [31](#bodymatter-005.xhtml#b_9783110670707-005_ref_031), [32](#bodymatter-005.xhtml#b_9783110670707-005_ref_032)\] and task scheduling in distributed system \[[36](#bodymatter-005.xhtml#b_9783110670707-005_ref_036)\], to name a few.

In this article, two different quantum inspired meta-heuristic algorithms, viz., QIGA and QIBA are proposed for automatic clustering technique of image datasets and also a comparison was produced between two different classical algorithms, viz., the classical genetic algorithm and the classical bat algorithm with their corresponding quantum influenced counterparts. The computed fitness values of the mean, standard deviation of that fitness, standard error of that fitness and the minimum computational time were the yardstick for adjudging the efficacy of these quantum inspired techniques over their analogous classical counterparts. Though, the experimental results are in favor of the quantum inspired techniques, still a statistical superiority test, viz., the unpaired *t-test* \[[37](#bodymatter-005.xhtml#b_9783110670707-005_ref_037)\] was conducted and the corresponding evaluated *p* value establishes the efficacy of these quantum inspired techniques. Finally, Friedman test \[[38](#bodymatter-005.xhtml#b_9783110670707-005_ref_038), [39](#bodymatter-005.xhtml#b_9783110670707-005_ref_039)\] was conducted among all the proposed procedure to judge the superiority of a procedure over another. The cluster validity index namely, DB index \[[40](#bodymatter-005.xhtml#b_9783110670707-005_ref_040)\] was used as an objective function to compute the validity of the clustering.

The rest of the article is organized as follows. The overview of the genetic algorithm and the overview of the bat algorithm are summarized in [Section 5.2](#bodymatter-005.xhtml#b_9783110670707-005_s_005_s_002) and [5.3](#bodymatter-005.xhtml#b_9783110670707-005_s_005_s_003) respectively. The fundamental idea of Quantum Computing is discussed in [Section 5.4](#bodymatter-005.xhtml#b_9783110670707-005_s_005_s_004). The [Section 5.5](#bodymatter-005.xhtml#b_9783110670707-005_s_005_s_005) presents the overview of the Cluster Validity Index (DB-Index). The steps involved in the proposed Quantum Inspired Genetic Algorithm and Quantum Inspired Bat Algorithm are presented in [Section 5.6](#bodymatter-005.xhtml#b_9783110670707-005_s_005_s_006) and [5.7](#bodymatter-005.xhtml#b_9783110670707-005_s_005_s_007) respectively. The experimental outcomes and analysis are discussed in [Section 5.8](#bodymatter-005.xhtml#b_9783110670707-005_s_005_s_008). Finally, a conclusion is drawn in [Section 5.9](#bodymatter-005.xhtml#b_9783110670707-005_s_005_s_009).

## 5.2 Overview of Genetic algorithm

The well-known nature inspired meta-heuristic algorithm named, Genetic Algorithm (GA) is a kind of evolutionary algorithm based on the concept of Darwin’s theory of evolution. John Holland is known as the inventor of GA, who proposed this algorithm in the year 1975 \[[9](#bodymatter-005.xhtml#b_9783110670707-005_ref_009)\].

GA is a very useful population based adaptive searching process, in which each individual in a population is called a chromosome. In order to achieve the optimal solution GA basically explores the entire search space. During the search process the current population evolves to a same sized next population by applying three genetic operations, such as selection, crossover and mutation. In the successive iteration, the best chromosomes are selected among all the participating chromosomes from the previous pool and the selection is carried over depending upon their computed fitness value. Several methods can be used for the purpose of selection, such as Boltzmann selection, Roulette Wheel selection, Rank selection, Tournament selection etc. The crossover operation is used to produce a new pair of chromosomes by combining the portions of two or more randomly selected parent chromosomes which lead to produce a population by replacing the parent chromosomes by the new one. During the crossover operation one or multiple points can be selected as the partitioning points from each of the individual in the population. In order to ensure the genetic diversity in the population mutation operation takes place in which a randomly selected position of a randomly selected chromosome is altered depending upon a predefined value called mutation probability. This kind of alteration may be performed on a single point or multiple points of one or more randomly selected individuals in the population. In order to achieve faster convergence it is recommended to perform elitism at each generation. GA was already successfully applied in many applications like data clustering \[[17](#bodymatter-005.xhtml#b_9783110670707-005_ref_017), [18](#bodymatter-005.xhtml#b_9783110670707-005_ref_018)\], portfolio management \[[41](#bodymatter-005.xhtml#b_9783110670707-005_ref_041)\], image processing \[[42](#bodymatter-005.xhtml#b_9783110670707-005_ref_042)\] and many more.

Basic steps involved in Genetic algorithm are presented as follows.

1.  Population of chromosomes is initialized randomly.
    
2.  Fitness of each of the chromosome is evaluated.
    
3.  Selection of chromosomes for next generation is done.
    
4.  Do the following steps until the termination condition are satisfied.
    
5.  Crossover is accomplished between a pair of randomly selected parent chromosomes to get child chromosomes, depending upon a predefined crossover probability.
    
6.  Mutation is applied on the randomly selected offspring/ chromosome to introduce diversity in the population, depending upon a predefined mutation probability.
    
7.  Selection is carried out for generating the next generation population.
    
8.  End Loop.
    

## 5.3 Overview of Bat algorithm

In the year 2010, an efficient nature inspired population based meta-heuristic algorithm, viz., Bat algorithm and this algorithm was initially developed by Yang \[[14](#bodymatter-005.xhtml#b_9783110670707-005_ref_014)\]. This algorithm is capable to identify the optimal solution or near optimal solution from a given problem, which can be an optimization problem of simple or complex type. Bats generally use echolocation for sensing the prey and recognizing their roosting crevices at the dark. They can also avoid their upcoming obstacles by using echolocation. Generally, bats can be able to produce a very loud sound pulse and listen for the bounced back echo from their surroundings. Depending upon the loudness of the response and the time delay from the emission to the reflection they can understand the shape, size and the velocity of the prey and can navigate accordingly. It is known that the high frequency emitted sound pulses influence them to give detailed information about their close environment so that they are able to detect the position of the prey precisely and allow them to move shorter distances. But, if the emitted sound pulses have low frequency then they travel longer distance and provide rough information about their surroundings. Also the higher values of the loudness of the echolocation indicate that they are nearer to the prey and produce sound pulse very quickly. The following process describes the basic steps involved in the hunting strategy of the bats.

1.  All bats are able to detect the distance between the prey/food and the obstacles of their surroundings by using the echolocation characteristics.
    
2.  Bats are able to fly randomly from a position *P*[i] with the velocity *V*[i], a fixed frequency *F*[*m**i**n*], with varying wavelength *λ* and loudness *L*[0] to search the prey.
    
3.  Their loudness can be changed from a large number *L*[0] to a minimum constant number *L*[min] and also the frequency can vary from *F*[*m**i**n*] to *F*[*m**a**x*].
    

Let us considered in a search space, *n* numbers of bats are flying randomly. In a time stamp *t*, they are initiated their search from the position *P[i]* having initial velocity *V[i]*, frequency *F*[*m**i**n*], pulse rate *r[i]* and loudness *L[0]*. At time stamp *t *+ 1, they may change their next position and velocity by using the following equations.

(5.1)*F*[*i*] = *F*[*m**i**n* ] + (*F*[*m**i**n*]−*F*[*m**a**x*])*β* (5.2)*V*[*i*]^(*t* + 1) = *V*[*i*]^(*t*) + (*P*[*i*]^(*t* + 1)−*P*[*b**e**s**t*])*F*[*i*] (5.3)*P*[*i*]^(*t* + 1) = *P*[*i*]^(*t*) + *V*[*i*]^(*t* + 1) 

where, *β* ∈ \[0, 1\]. The minimum and the maximum frequencies are *F*[*m**i**n* ] = 0 and *F*[*m**a**x* ] = 2 respectively. Here, *P*[*b**e**s**t*] signifies the global best bat’s location among the positions of the *n* numbers of bats in the current population. After evaluating the fitness of all solutions in the population, the position of the best solution among them is identified as the global best position. Now, it remains to check whether the bats are near or far away from the prey by using their pulse rates. A low pulse rate *r*[i] with high probability (*rand[1]* > *r[i]*) indicates that the bats will fly near to the current superior bat before carrying out a short random fly there. Otherwise, it is considered that the bats are nearer to the prey and they will do a random fly around their current position. Here, *rand[1]* is a uniformly distributed random number between \[0, 1\]. The following equation is used to represent the new positions of the bats.

(5.4)*P*[*n**e**w*] = *P*[*o**l**d*] + *ε**L*^(*t*) 

where, *ε* ∈ \[ − 1, 1\] and at the time stamp *t*, the average loudness of *n* bats is computed by $L^{t} = \\frac{1}{n}\\sum\_{i = 1}^{n}L\_{i}^{t}$. After the random fly, if a bat is able to achieve a better position than the current global best position and its emitted sound is loud enough and also better than a random number (*rand[2]*[ ]< *L*[*i*]), then it is considered that the bat will fly to this new position and the current global best position value will be updated with the newly generated position value. Here *rand[2]* is a random number which is distributed uniformly between \[0, 1\]. Now, the pulse rate (*r[i]*) of the bats are increased and the loudness (*L*[*i*]) of the bats are decreased simultaneously by the following equations.

(5.5)*r*[*i*]^(*t* + 1)\= *r*[*i*]⁰(1−*e*^( − *γ**t*)) (5.6)*L*[*i*]^(*t* + 1)\= *α**L*[*i*]^(*t*) 

where, *r*[*i*]⁰ ∈ \[0, 1\] represents the initial pulse rate in which *γ* (0 < *γ* < 1) and *α* (0 < *α* < 1) are constants. Now, the current *P*[*b**e**s**t*] is selected by computing the fitness of all the bats.

Basic steps involved in Bat algorithm are presented as follows.

1.  Bat population 𝒫 is initialized randomly.
    
2.  Pulse frequency (ℱ), velocity (𝒱), pulse rate (*r*[*i*]) and loudness (ℒ[0]) are initialized for each of the individual.
    
3.  Fitness *f*[*n*]  of each individual is computed.
    
4.  Do the following steps until the iteration number (*J*[*n*]) reach to the specified maximum iteration number (*M**a**x**J*).
    
5.  New bat population 𝒫[*n*] is generated by adjusting the frequency (ℱ[*n*]) and velocity (𝒱[*n*]) of each individual. ([eqs. (5.1)–(5.3)](#bodymatter-005.xhtml#b_9783110670707-005_eq_004)).
    
6.  *i**f* (*r**a**n**d*\>*r*[*i*])*t**h**e**n*
    
7.  Among all the best solutions, a single solution is selected and a local solution is produced around this selected solution (best solution). ([eq. (5.4](#bodymatter-005.xhtml#b_9783110670707-005_eq_004)))
    
8.  *e**n**d* *i**f*
    
9.  By producing a random fly, a new solution is generated.
    
10.  *i**f*(*r**a**n**d*<ℒ[0*i*] *a**n**d* *f*[*n*](𝒫[*i*])<*f*[*n*](𝒫[*b**e**s**t*]))*t**h**e**n*
     
11.  The new solution is accepted.
     
12.  Pulse rate (*r*[*i*]) is increased. ([eq. (5.5](#bodymatter-005.xhtml#b_9783110670707-005_eq_005)))
     
13.  Loudness (ℒ[0*i*]) is decreased. ([eq. (5.6](#bodymatter-005.xhtml#b_9783110670707-005_eq_006)))
     
14.  *e**n**d* *i**f*
     
15.  The current best bat is identified.
     
16.  *e**n**d* *l**o**o**p*
     

## 5.4 Fundamental idea of quantum computing

A classical computer is capable to hold a single binary bit 0 or 1 at a time. Unlike classical computer, a quantum computer is capable to store a unit of information which is called quantum bit or *qubit*, in which a single *qubit* is able to store the numbers zero (0) and one (1) at the same moment, which referred as the superposition state in quantum computing \[[24](#bodymatter-005.xhtml#b_9783110670707-005_ref_024), [25](#bodymatter-005.xhtml#b_9783110670707-005_ref_025), [26](#bodymatter-005.xhtml#b_9783110670707-005_ref_026)\]. It is known that the *qubits* are able to accomplish numerous processes simultaneously which yields fastest execution of process. In a two-dimensional Hilbert space, a *qubit* are represented by a unit vector and are considered as a two state quantum-mechanical phenomena. In QC, the superpositions of the basis states are represented by the following equation.

$|\\Psi\\rangle = \\sum\\limits\_{i = 1}^{n}\\mathcal{C}\_{i}|\\mathcal{V}\_{i}\\rangle$ (5.7)|*Ψ*⟩ = 𝒞[1]|𝒱[1]⟩+ 𝒞[2]|𝒱[2]⟩ + …+ 𝒞[*n*]|𝒱[*n*]⟩ 

where, 𝒱[*i*] is the *i*^(*t**h*) quantum states and 𝒞[*i*] ∈ ℂ. For a two states quantum bit or qubit, [eq. (5.7)](#bodymatter-005.xhtml#b_9783110670707-005_eq_007) can be denoted by a linear superposition as |*Ψ*⟩=𝒞[1]|0⟩ + 𝒞[2]|1⟩, in which, the state |0⟩ is acknowledged as “ground state” and |1⟩ is acknowledged as “excited state”, and 𝒞[*i*] belongs to the set of complex number which should satisfy the following normalization condition.

(5.8)$\\sum\\limits\_{i = 1}^{n}|\\mathcal{C}\_{i}|^{2} = 1$ 

In QC, there exist two striking features, viz., Coherence and Decoherence. Coherence is represented by the linear superposition (|*Ψ*⟩) of the basis states whereas, decoherence is occurred when a forceful destruction is happened on the previously defined linear superposition. Quantum computing generally uses quantum logic gates as hardware devices.

A predefined unitary operator is used to update the *qubits* within a fixed time period. Mathematically, the unitary *U* operator quantum gates hold the relation *U*^† = *U*^( − 1) and *U**U*^† = *U*^†*U* = *I*.

In quantum computer a *n* qubit quantum register is able to store 2^(*n*) states simultaneously. As for example the eight states |000〉, |001〉, |010〉, |011〉, |100〉, |101〉, |110〉 and |111〉 require three quantum registers in which the three qubit system can be represented as $\\left\\lbrack {\\begin{matrix} \\alpha\_{1} \\\\ {\\ \\beta\_{1}\\ } \\\\ \\end{matrix}\\ \\begin{matrix} \\alpha\_{2} \\\\ {\\ \\beta\_{2}\\ } \\\\ \\end{matrix}\\begin{matrix} \\alpha\_{3} \\\\ {\\ \\beta\_{3}\\ } \\\\ \\end{matrix}} \\right\\rbrack$ where *α*[*i*]² + *β*[*i*]² = 1, *i* = 1, 2, 3.

But in case of classical computer in order to store these eight states eight registers are required.

There are several quantum gates exists, such as Rotation Gate, Pauli – X Gate or NOT Gate, C-NOT Gate, Toffoli Gate, Fredkin Gate and Hadamard Gate \[[24](#bodymatter-005.xhtml#b_9783110670707-005_ref_024), [25](#bodymatter-005.xhtml#b_9783110670707-005_ref_025), [26](#bodymatter-005.xhtml#b_9783110670707-005_ref_026)\] etc. and they can be used in several ways in different types of problems.

Rotation gate strategy can be used to update the values of (*α*[*i*], *β*[*i*]) of the *i*^(*t**h*) qubit by the following equation.

(5.9)$\\begin{pmatrix} \\alpha\_{i}^{\\prime} \\\\ \\beta\_{i}^{\\prime} \\\\ \\end{pmatrix} = \\ \\left( {\\begin{matrix} {\\cos\\theta\_{i}} \\\\ {\\sin\\theta\_{i}} \\\\ \\end{matrix}\\ \\begin{matrix} {- \\sin\\theta\_{i}} \\\\ {{cos}\\theta\_{i}} \\\\ \\end{matrix}} \\right)\\ \\begin{pmatrix} \\alpha\_{i} \\\\ \\beta\_{i} \\\\ \\end{pmatrix}$ 

Here, the rotation angle for each of the *qubit* is represented by *θ*[*i*], which is chosen according to specific problem. If *α*[*i*] and *β*[*i*] represent the probability amplitude of a *qubit* before rotation then after rotation they become *α*[*i*]^′ and *β*[*i*]^′ respectively and can be achieved by the following way.

(5.10) $\\begin{pmatrix} \\alpha\_{i}^{\\prime} \\\\ \\beta\_{i}^{\\prime} \\\\ \\end{pmatrix} = \\ \\begin{pmatrix} {\\cos\\left( {\\theta + \\ \\delta} \\right)\_{i}} \\\\ {\\sin\\left( {\\theta + \\ \\delta} \\right)\_{i}} \\\\ \\end{pmatrix}$ 

where $\\begin{pmatrix} \\alpha\_{i} \\\\ \\beta\_{i} \\\\ \\end{pmatrix} = \\begin{pmatrix} {\\cos\\delta\_{i}} \\\\ {\\sin\\delta\_{i}} \\\\ \\end{pmatrix}$

## 5.5 Cluster validity index

In the year 1979, David L. Davies and Donald W. Bouldin introduced an efficient cluster validity index, named, Davies-Bouldin (DB) Index \[[40](#bodymatter-005.xhtml#b_9783110670707-005_ref_040)\], which was used in this article as an objective function to compute the fitness of each individual. The optimum number of clusters within a given dataset is determined by the calculated value of the *D**B* index \[[40](#bodymatter-005.xhtml#b_9783110670707-005_ref_040)\], where, minimum value of *D**B* index \[[40](#bodymatter-005.xhtml#b_9783110670707-005_ref_040)\] is taken for consideration. It can be considered as a function of the ratio between the sum of within-cluster scatter and the cluster separation. Let us consider the cluster similarity measure is *C**M*[*i**j*] between two different clusters *C**l*[*i*] and *C**l*[*j*]. It is given by:

(5.11)$\\ CM\_{ij} = \\frac{dM\_{i} + \\ dM\_{j}}{d\_{ci\\\_ cj}}$ 

Here *d**M*[*i*] be the dispersion measure of *i*^(*t**h*) cluster and is denoted as

$dM\_{i} = \\left\\lbrack {\\frac{1}{tn\\\_ o\_{i}}\\sum\_{k = 1}^{tn\\\_ o\_{i}}{\\parallel {Dp\_{k}^{(i)} - Cc\_{i}} \\parallel}^{2}} \\right\\rbrack^{\\frac{1}{2}}$ 

such that, *t**n*\_*o*[*i*] denotes the total number of objects and *C**c*[*i*] denotes the *i*^(*t**h*) cluster center in cluster *C**l*[*i*] and ∀*D**p*[*k*]^((*i*))∈ *C**l*[*i*].

The distance between the clusters *C**l*[*i*] and *C**l*[*j*] and can be defined as

*d*[*c**i*\_*c**j*] =  ∥ *C**c*[*i*] − *C**c*[*j*]∥. 

The following equation is used to define the Davies – Bouldin (DB) index \[[40](#bodymatter-005.xhtml#b_9783110670707-005_ref_040)\].

(5.12)$DB\\\_ I = \\frac{1}{no\_{c}}\\sum\_{i = 1}^{no\_{c}}H\_{i}$ 

Where $H\_{i} = \\max\\limits\_{j = 1,2,\\ldots,no\_{c},\\; i \\neq j}\\left( {CM\_{ij}} \\right),\\; i = 1,2,\\ldots,\\; no\_{c}$

## 5.6 Quantum inspired Genetic algorithm

### 5.6.1 Proposed methodology for QIGA

In this section, the operational strategy of quantum inspired GA algorithm is discussed. In order to recognize the optimum number of cluster presents within images, the proposed method was experimented on image dataset.

At first, a population (*P**c*) was initialized with *N* number of chromosomes. Each individual chromosome was of length *L**n* from the population was considered as a solution of the problem. (Line 1).

Now, the population (*P**c*) was encoded to produce the quantum states *Q*^(*s*). The encoding process is discussed as follows.

Initially for each of the chromosome of the population a state *θ*[*i*, *j*]^(*s*)(0≤*θ*[*i*, *j*]^(*s*)≤2*π*) was created randomly. Using the value of *θ*[*i*, *j*] the quantum state *Q*^(*s*) was created. For a particular *t*^(*t**h*) generation the quantum state *Q*^(*s*)(*t*) was represented as follows. *Q*^(*s*)(*t*) = {*q*[1]^(*s**t*), *q*[2]^(*s**t*), …, *q*[*N*]^(*s**t*)},

where, *q*[*i*]^(*s**t*)(*i*\=1,2,…,*N*) denotes the arbitrary elements of *Q*^(*s*)(*t*) and can be denoted as

$q\_{i}^{st} = \\begin{bmatrix} {\\alpha\_{i,1}^{st}\\left| {\\alpha\_{i,2}^{st}\\left| \\ldots \\right|\\alpha\_{i,m}^{st}} \\right|} \\\\ {\\beta\_{i,1}^{st}\\left| \\beta\_{i,2}^{st} \\right|\\ldots\\left| \\beta\_{i,m}^{st} \\right|} \\\\ \\end{bmatrix}\\,\\,,\\, here\\, m = Ln$ 

and *α*[*i*, *j*]^(*s**t*) = cos *θ*[*i*, *j*]^(*s**t*) and *β*[*i*, *j*]^(*s**t*) = sin *θ*[*i*, *j*]^(*s**t*) was computed from the random value of *θ*[*i*, *j*]^(*s**t*), where *i* = {1,2,…,*N*} *a**n**d* *j* = {1,2,…,*L**n*}.(Line 2).

Now, in order to generate the active cluster points a selection procedure was applied on the population and the selection process was guided by the state *Q*^(*s*)(*t*) to produce a binary solution *B**c*(*t*). The binary solution *B**c*(*t*) = {*b**c*[1]^(*t*),*b**c*[2]^(*t*),…,*b**c*[*N*]^(*t*)} was produced by observing the state *Q*^(*s*)(*t*) in the initial generation  *t* = 1.

Each of the binary solution *b**c*[*i*]^(*t*)  was generated as follows.

$bc\_{i,j}^{t} = \\{\\begin{matrix} {1,\\ If\\ \\beta\_{i,j}^{st} > \\ \\alpha\_{i,j}^{st}} \\\\ {\\ 0,\\ Otherwise} \\\\ \\end{matrix},\\ s.t.\\ i = \\left\\{ {1,\\ 2,\\ldots,\\ N} \\right\\}\\ and\\ j = \\left\\{ {1,2,\\ldots,\\ Ln} \\right\\}.$ 

The criteria *b**c*[*i*, *j*]^(*t*) = 1 was set to identify the activated cluster points from the population *P**c*(*t*) for the *t*^(*t**h*) generation, where *i* = {1,2,…,*N*} *a**n**d* *j* = {1,2,…,*L**n*}. (Line 3–8).

Now, the fitness of each individual chromosome from the quantum population was computed by an objective function (DB index \[[40](#bodymatter-005.xhtml#b_9783110670707-005_ref_040)\] – [eq. (5.12)](#bodymatter-005.xhtml#b_9783110670707-005_eq_012)).

The best chromosomes from the quantum population were chosen for generating the next generation population. (Line 9).

Now, a quantum rotation gate *G**s*[*i*, *j*]^(*t*)(*ϕ*) was used for updating each quantum state *Q*^(*s*)(*t*), which can be denoted as follows.

 $Gs\_{i,j}^{t}\\left( \\phi \\right) = \\left\\lbrack {\\begin{matrix} {\\cos\\phi\_{i,j}^{st}\\ } \\\\ {\\sin\\phi\_{i,j}^{st}} \\\\ \\end{matrix}\\begin{matrix} {- {sin}\\phi\_{i,j}^{st}} \\\\ {\\cos\\phi\_{i,j}^{st}} \\\\ \\end{matrix}} \\right\\rbrack,$ 

where, the rotation angle *ϕ*[*i*, *j*]^(*s**t*)  was chosen randomly between (−0.5, 0.5).

The updated quantum state *Q*^(*n**e**w*)(*t*) was identified by the [eq. (5.10)](#bodymatter-005.xhtml#b_9783110670707-005_eq_009).(Line 11).

In case of quantum inspired genetic algorithm, the probability amplitude (*α*, *β*) of qubits were used to encode the chromosomes. After that quantum rotation gate was used to update (*α*, *β*), which lead to realize the genetic operation for generating the offspring instead of determining them from their parents as the chromosomes were in superposition or entangled state. In general, rotation influences the search space to extend as it is able to produce 2^(*n*) number of states from *n* qubit chromosome. The different values of (*α*, *β*) were responsible for generating the states (Lines 12–18).

A predefined mutation probability was used to perform the quantum mutation operation. The probability amplitude *α* would be converted to *β* and *β* would be converted to *α* for the greater value of the predefined mutation probability from a random number between (0,1). The following quantum NOT gate strategy was used to alter the probability amplitude (*α*, *β*) to (*β*, *α*).

$\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\!\\begin{bmatrix} 0 & 1 \\\\ 1 & 0 \\\\ \\end{bmatrix}\\ \\begin{bmatrix} \\alpha\_{i,j} \\\\ \\beta\_{i,j} \\\\ \\end{bmatrix}$\=$\\begin{bmatrix} \\beta\_{i,j} \\\\ \\alpha\_{i,j} \\\\ \\end{bmatrix}$

$\\begin{bmatrix} 0 & 1 \\\\ 1 & 0 \\\\ \\end{bmatrix}\\ \\begin{bmatrix} {\\cos\\theta\_{i,j}} \\\\ {\\sin\\theta\_{i,j}} \\\\ \\end{bmatrix}$\=$\\begin{bmatrix} {\\sin\\theta\_{i,j}} \\\\ {\\cos\\theta\_{i,j}} \\\\ \\end{bmatrix}$ (Lines 19–26).

The generation number *t* was updated by *t* = *t* + 1 and perform the above mentioned procedure for a predefined number of generation or until it met the stopping criteria. (Lines 10–27).

The best chromosome was identified and preserved along with its fitness and number of cluster.(Line 28).

The working principle for QIGA is presented as follows.

#### Algorithm:

Quantum Inspired Genetic Algorithm for automatic clustering

Input Parameter:

Maximum number of generation: *M**x**G*

Size of population: *N*

Mutation probability: **μ**

Output parameter:

Optimum cluster number: 𝒪\_𝒩[𝒞]

Optimum fitness value: 𝒪\_ℱ[𝒯]

1.  At the beginning, a population *P**c* was created randomly from an image dataset with *N* number of chromosomes where each chromosome was considered as a solution of the problem. During this process, the intensity value of each pixel of the input image was normalized. The length of each chromosome was taken as *L**n*.The maximum pixel intensity value of the input image first passed through the square root function then was assigned to *L**n*. The image was also normalized between 0 & 1 and named it as *I*[*n**o**r**m**a**l*].
    
2.  Now quantum state *Q*^(*P*)(*t*) was created and each chromosome of *P**c* was encoded to produce *P*^(*α*) and *P*^(*β*) using the information of the quantum state.
    
3.  *f**o**r* *i* = 1 *t**o* *N* *d**o*
    
4.  *f**o**r* *j* = 1 *t**o* *L**n* *d**o*
    
5.  𝒩[𝒞][*i*] numbes of active cluster centers were created from *P**c*[*i*] by using the condition *P*[*i**j*]^(*β*) > *P*[*i**j*]^(*α*) and stored the cluster centers in *C**P*[*i*].
    
6.  Now, the fitness ℱ[𝒯][*i*] was computed from *C**P*[*i*] with the help of a cluster validity index, named, *D**B* − *I**n**d**e**x*. \[[eq. (5.12)](#bodymatter-005.xhtml#b_9783110670707-005_eq_012)\]
    
7.  *e**n**d* *f**o**r*
    
8.  *e**n**d* *f**o**r*
    
9.  The best chromosome was identified and preserved along with its fitness value ℱ[𝒯] ∈ ℱ[𝒯][*i*], ∀*i* ∈ *N* and its corresponding number of cluster point 𝒩[𝒞].
    
10.  *f**o**r* *t* = 1 *t**o* *M**x**G* *d**o*
     
11.  The quantum state  *Q*^(*N*)(*t*)  was created by applying the rotation gate on *Q*^(*P*)(*t*).
     
12.  Continued step – 2 for the newly created quantum state *Q*^(*N*)(*t*).
     
13.  Continued steps- (3–8) for identifying the best chromosome.
     
14.  *I**f* the best chromosome was identified in the population for the quantum state  *Q*^(*N*)(*t*) *t**h**e**n*
     
15.  The value of the quantum state was updated by *Q*^(*N*)(*t*)
     
16.  Otherwise
     
17.  The previous value of the quantum state *Q*^(*P*)(*t*) was preserved
     
18.  *e**n**d* *i**f*
     
19.  *f**o**r* *i* = 1 *t**o* *N* *d**o*
     
20.  *I**f* the current chromosome was not the best chromosome *t**h**e**n*
     
21.  *j* = *r**a**n**d*(0, *L**n*)
     
22.  *I**f**μ* > *r**a**n**d*(0,1) *t**h**e**n*
     
23.  Exchanged *P*[*i**j*]^(*α*) *a**n**d* *P*[*i**j*]^(*β*)
     
24.  *e**n**d* *i**f*
     
25.  *e**n**d* *i**f*
     
26.  *e**n**d* *f**o**r*
     
27.  *e**n**d* *f**o**r*
     
28.  Finally, the algorithm produced and reported the optimum number of cluster 𝒪\_𝒩[𝒞] along with its associated value of fitness 𝒪\_ℱ[𝒯].
     

## 5.7 Quantum inspired Bat algorithm

### 5.7.1 Proposed methodology for QIBA

Now a day, the bat algorithm is widely applied in several types of complex optimization problems as it follows an easy mechanism for implementation and its quick convergence rate which sometimes leads a premature convergence. The premature convergence can be occurred for several reasons like the bats may be trapped into local optima due to the decreasing diversity of the bats or the most promising bat falls into the local optima then it influences all other bats to follow the same trajectory as other bats are instructed to follow the current optimal solution and moreover in bat algorithm there is no specified ways to get rid of the local optima. In order to solve this problem a quantum inspired bat algorithm was proposed in this article. The diversity of the bat population was achieved through quantum rotation gates which helped the proposed algorithm to avoid premature convergence without affecting the convergence speed though the efficiency of the proposed algorithm in terms of computational time was guaranteed \[[43](#bodymatter-005.xhtml#b_9783110670707-005_ref_043)\].

The anticipated algorithm is established on the framework of bat algorithm with the flavor of c quantum computing. In order to control the exploitation and exploration, the parameters ℬ*R* and ℬ*A* are used and they are updated for guiding the local and global search process. Though, the new velocity and positions of each of the candidates are updated through the following equation.

(5.13)$V\_{i}^{t + 1} = \\left\\{ \\begin{matrix} {V\_{i}^{t},if(\\delta{}\_{i},\\delta{}\_{best}) = \\left( {0,0} \\right)} \\\\ {V\_{i}^{t} + \\left( {P\_{i}^{t + 1} - P\_{best}} \\right),if(\\delta{}\_{i},\\delta{}\_{best}) = \\left( {1,1} \\right)} \\\\ {V\_{i}^{t} + \\left( {P\_{i}^{t + 1} - P\_{best}} \\right)rand,if(\\delta{}\_{i},\\delta{}\_{best}) = \\left\\{ {\\left( {1,0} \\right)or\\left( {0,1} \\right)} \\right\\}} \\\\ \\end{matrix} \\right.$ (5.14)*P*[*i*]^(*t* + 1)\= *P*[*i*]^(*t*)+ *V*[*i*]^(*t* + 1) 

Where *δ*[*i*] and  *δ*[*b**e**s**t*] represents the quantum state of the current bat and the local best bat respectively and *r**a**n**d* is a random number between 0 and 1. If the state of both the current bat and the best bat are 0 it indicates that this current bat will not influence the search process during that point of time so there is no need to change the velocity of that position. If the state of both the current bat and the best bat are 1 it indicates that this current bat will very much influence the search process as it is close to the current optimal solution so it will change its current velocity using the information of the current optimal position. And if the state value of the current bat is just opposite of the state value of the best bat then it indicates that it is far away from the current optimal solution so it will like to make a random fly near the current best solution and update its velocity by using the information of the current optimal solution along with a random value between 0 and 1. Finally the new position of the current bat was computed by using the newly generated velocity of it.

During the search process the positions of each bat were updated as follows.

(5.15) $P\_{new} = {}\\{\\begin{matrix} {P\_{old} + \\varepsilon AL^{t}\\,\\,\\,\\, if\\,\\, rand > p} \\\\ {P\_{old} + \\varepsilon\\left( {AL^{t} - P\_{old}} \\right)\\,\\,\\, otherwise} \\\\ \\end{matrix}{}$ 

Where, *ε* ∈ \[−1, 1\] and at the time stamp *t,* $AL^{t} = \\frac{1}{n}\\sum\_{i = 1}^{n}AL\_{i}^{t}$ represents the average loudness of *n* bats and *p**τ* represents the pulse rate.

If the pulse rate *p**τ* is low than a probability (*r**a**n**d* > *p**τ*) then it indicates that the bats will fly near to the current superior bat before carrying out a short random fly there. Otherwise, it is considered that the bats are nearer to the prey and they will do a random fly around their current position. Here *r**a**n**d* is a uniformly distributed random number which is chosen between \[0, 1\] during the computation.

The pulse rate (*p**τ*[*i*]) is increased and the loudness ( *A**L*[*i*]) of the bats is decreased by the following equations.

(5.16) *p**τ*[*i*]^(*t* + 1) = *p**τ*[*i*]⁰(1−*e*^( − *γ**t*)) (5.17)*A**L*[*i*]^(*t* + 1) = *α* *A**L*[*i*]^(*t*) 

Where, the constant term *γ* and the preliminary pulse rate *p**τ*[*i*]⁰ both were chosen between 0 and 1. Subsequently, the fitness values of every bats were estimated and the current *P*[*b**e**s**t*] was selected. Here *α* was considered as a contraction – expansion and can be defined as follows.

(5.18) $\\alpha = \\ \\alpha\_{i} - \\frac{\\alpha\_{i} - \\ \\alpha\_{\\ell}}{\\mathcal{T}}\\ t$ 

Here *α*[*i*] defines the initial value and *α*[ℓ] defines the last value of *α*. The highest number of iteration is denoted by 𝒯. During the execution *α*[*i*] = 1 and *α*[ℓ] = 0.5 is set for increasing the performance of the algorithm \[[43](#bodymatter-005.xhtml#b_9783110670707-005_ref_043), [44](#bodymatter-005.xhtml#b_9783110670707-005_ref_044)\].

This section describes the process to identify the optimum number of clusters belong to the dataset of an image by the quantum inspired BAT algorithm.

Initially, the bat population *P*\_*B**A**T* was initialized and considering the size of the population was *P**s**i**z**e*, in which each of the solution was of length *B**L**n* and each of the solution from the population was considered as a solution of the problem. The initialization was carried out with the normalized pixel intensity value of the input image, which was chosen randomly. The maximum intensity value of the input image first passed through the square root function then it was considered as the length of each particle (*B**L**n*). Another variable *I*[*n**o**r**m**a**l*] was used to store the normalized value (between 0 and 1) of each pixel intensity of the input image (Line 1).

Now, quantum state *Q*^(ℬ*A**T*) was created for each of the elements of *P*\_*B**A**T*. And *P*\_*B**A**T* was encoded by *P*\_*B**A**T*^(*α*) and *P*\_*B**A**T*^(*β*) the [eq. (5.8)](#bodymatter-005.xhtml#b_9783110670707-005_eq_008) should be satisfied. The encoding process is shown as follows.

Initially, *θ*[*i*, *j*](0≤*θ*[*i*, *j*]≤2*π*) was created randomly for each of the particle of the solution of the population, which was used to produce the quantum state namely, *Q*^(ℬ*A**T*). For a particular *t*^(*t**h*) generation the quantum state *Q*^(ℬ*A**T*)(*t*) was represented as follows.

 *Q*^(ℬ*A**T*)(*t*) = {*q*[1]^(ℬ*A**T**t*), *q*[2]^(ℬ*A**T**t*), …, *q*[*N*]^(ℬ*A**T**t*)}, where *q*[*i*]^(ℬ*A**T**t*) (*i*\=1, 2,…, *P**s**i**z**e*) denotes the arbitrary elements of  *Q*^(ℬ*A**T*)(*t*)  and can be represented as

$q\_{i}^{\\mathcal{B}ATt} = \\ \\begin{bmatrix} {\\alpha\_{i,1}^{\\mathcal{B}ATt}\\ \\left| {\\ \\alpha\_{i,2}^{\\mathcal{B}ATt}\\ \\left| \\ldots \\right|\\alpha\_{i,m}^{\\mathcal{B}ATt}} \\right|} \\\\ {\\ \\beta\_{i,1}^{\\mathcal{B}ATt}\\left| {\\ \\beta\_{i,2}^{\\mathcal{B}ATt}\\ } \\right|\\ldots\\left| {\\ \\beta\_{i,m}^{\\mathcal{B}ATt}} \\right|} \\\\ \\end{bmatrix},\\ \\left( {s.t.\\ m = BLn} \\right)$ 

here, each value of *α*[*i*, *j*]^(*s**t*) and *β*[*i*, *j*]^(*s**t*) were computed by

$\\begin{pmatrix} \\alpha\_{i,j}^{\\mathcal{B}ATt} \\\\ {\\ \\beta\_{i,j}^{\\mathcal{B}ATt}} \\\\ \\end{pmatrix} = \\begin{pmatrix} {\\cos\\theta\_{i,j}^{\\mathcal{B}ATt}} \\\\ {\\sin\\theta\_{i,j}^{\\mathcal{B}ATt}} \\\\ \\end{pmatrix},\\ {where}\\ i = \\left\\{ {1,2,\\ldots,P\\, size} \\right\\}\\ and\\ j = \\left\\{ {1,2,\\ldots,BLn} \\right\\}$ 

and the corresponding values of them are preserved in *P*\_*B**A**T*[*i*, *j*]^(*α*) and *P*\_*B**A**T*[*i*, *j*]^(*β*) respectively. (Line 2).

The frequency (ℬℱ[*i*]) and velocity (ℬ𝒱[*i*]), Pulse Rate (ℬ*R*[*i*]) and Loudness (ℬ*A*[*i*]) were initialized for every quantum solutions inside the quantum population (Lines 3–4).

Now, in order to generate the active cluster points a selection procedure was applied on the population and the selection process was guided by the quantum state *Q*^(ℬ*A**T*)(*t*) to produce a binary solution *B**s*(*t*). The binary solution *B**s*(*t*) = {*b**s*[1]^(*t*), *b**s*[2]^(*t*),…, *b**s*[*N*]^(*t*)} was produced by perceiving the state *Q*^(ℬ*A**T*)(*t*) in the initial generation  *t* = 1.

Each of the binary solution *b**c*[*i*]^(*t*)  was generated as follows.

$bs\_{i,j}^{t} = \\left\\{ \\begin{matrix} {1,\\,\\, IfP\\\_ BAT\_{ij}^{\\beta t} > P\\\_ BAT\_{ij}^{\\alpha t}} \\\\ {0,Otherwise} \\\\ \\end{matrix} \\right.,\\,\\, st.i = \\left\\{ {1,2,\\ldots,P\\, size} \\right\\}\\,\\, and\\,\\, j = \\left\\{ {1,2,\\ldots,BLn} \\right\\}$ 

The criteria *b**s*[*i*, *j*]^(*t*) = 1 was set to identify the activated cluster points from the population *P*\_*B**A**T* (*t*) ([Figure 5.1](#bodymatter-005.xhtml#b_9783110670707-005_fig_001)) for the *t*^(*t**h*) generation, where *i* = {1,2,…,*P**s**i**z**e*} and *j* = {1,2,…,*B**L**n*}. It was considered that the excited states are influenced to make the active cluster centroids from each of the solutions of the population and are denoted by 𝒩[𝒞][*i*] for each of the solution of the population. The 𝒩[𝒞][*i*] number of activated unique cluster points was stored in ℬ*C**P*[*i*].

![Figure 5.1: Cluster Centroid Representation Scheme.](graphic/converted/b_9783110670707-005_fig_001.png)

Figure 5.1: Cluster Centroid Representation Scheme.

Now, from ℬ*C**P*[*i*], the fitness (ℱ[𝒯][*i*]) of each solution was evaluated with the help of a cluster validity index namely, *D**B* − *I**n**d**e**x*. \[[eq. (5.12)](#bodymatter-005.xhtml#b_9783110670707-005_eq_012)\]. (Lines 5–10).

Now, the best fitness value 𝒪\_ℱ[𝒯] was identified from all computed fitness values (𝒪\_ℱ[𝒯][*i*]) and saved along with the respective number of cluster points 𝒪\_𝒩[𝒞]. (Line 11).

Using rotation gate ([eq. (5.10)](#bodymatter-005.xhtml#b_9783110670707-005_eq_010)) strategy another set of populations *P*\_*B**A**T*[*n**e**w*]^(*α*) and *P*\_*B**A**T*[*n**e**w*]^(*β*) were created. Update the values of *P*\_*B**A**T*^(*α*) and *P*\_*B**A**T*^(*β*) by using their earlier values or by using their recently created values of *P*\_*B**A**T*[*n**e**w*]^(*α*) and *P*\_*B**A**T*[*n**e**w*]^(*β*) on the basis of the best value of fitness. Now, if the recently created values were not able to make better fitness values then the current set of values were rejected and the old set of values were preserved in the population otherwise the new set of values were accept. Now, it was possible to create a novel quantum population as it produces the diversity in the solution space (Line 12).

The rotation gate updating process was applied which yielded the best fitness value (ℬℱ[𝒯]) and the respective cluster points were preserved in ℬ*C**P* and ℬ*n**c* conserved the total number of cluster points (Line 13).

During each execution of the main loop, the quantum positions and velocities were updated by the [eqs. (5.13)](#bodymatter-005.xhtml#b_9783110670707-005_eq_021) and [(5.14)](#bodymatter-005.xhtml#b_9783110670707-005_eq_022) (Line 16).

The rotation gate strategy was responsible for the improvement of the best quantum solutions (Line 17).

The best solution was selected from the computed fitness of the updated positions and a local solution was generated by using the [eq. (5.15)](#bodymatter-005.xhtml#b_9783110670707-005_eq_015). (Lines 18–20).

Next, the new quantum solutions were estimated and by applying rotation gate strategy each value of the state  *Q*^(ℬ*A**T*)(*t*)[*J*], *P*\_*B**A**T*[*J*]^(*α*) and *P*\_*B**A**T*[*J*]^(*β*) were updated. (Lines 21–22).

Now the new solution was accepted and the pulse rate of each bat was increased and the loudness of each bat was decreased by the [eqs. (5.16)](#bodymatter-005.xhtml#b_9783110670707-005_eq_016) and ([5.17](#bodymatter-005.xhtml#b_9783110670707-005_eq_017)). (Lines 23–26).

The best quantum solutions was determined and saved (Line 27).

In order to achieve the best solution the main loop was continued for a predefined number of times (Lines 14–29).

Finally, the best quantum solution was determined and the optimum number of cluster was identified along with its associated value of fitness. (Line 30).

The working principle for QIBA is presented as follows.

#### Algorithm:

Quantum Inspired Bat Algorithm for automatic clustering

Input parameter:

Maximum number of Iteration: *M**I*

Size of population: *P**s**i**z**e*

Output parameter:

Optimum cluster number: 𝒪\_𝒩[𝒞]

Optimum fitness value: 𝒪\_ℱ[𝒯]

1.  A population *P*\_*B**A**T* having *P**s**i**z**e* number of particles (bat) was initialized.
    
2.  Quantum state *Q*^(ℬ*A**T*)(*t*) was created for each of the elements of *P*\_*B**A**T*. And in order to encode *P*\_*B**A**T* the information of the quantum state was used and produce *P*\_*B**A**T*^(*α*) and *P*\_*B**A**T*^(*β*).
    
3.  The frequency (ℬℱ)[*i*] and velocity (ℬ𝒱[*i*]) were initialized for every solution of the population.
    
4.  The loudness (ℬ*A*[*i*]) and the pulse rates (ℬ*R*[*i*]) were also initialized.
    
5.  *f**o**r* *i* = 1 *t**o* *P**s**i**z**e* *d**o*
    
6.  *f**o**r* *j* = 1 *t**o* *B**L**n* *d**o*
    
7.  𝒩[𝒞][*i*] numbers of cluster points from *P*\_*B**A**T*[*i*] were created by satisfying the condition *P*\_*B**A**T*[*i**j*]^(*β*) > *P*\_*B**A**T*[*i**j*]^(*α*) and the cluster points were stored in ℬ*C**P*[*i*].
    
8.  Now, the fitness ℱ[𝒯][*i*] was evaluated from ℬ*C**P*[*i*] by using the cluster validity index (*D**B* − *I**n**d**e**x*).
    
9.  *e**n**d* *f**o**r*.
    
10.  *e**n**d* *f**o**r*.
     
11.  The best solution in terms of the best fitness value 𝒪\_ℱ[𝒯] was identified.
     
12.  Now, the quantum state *Q*^(ℬ*A**T*)(*t*) was updated by using quantum rotation gate to generate new set of values of *P*\_*B**A**T*^(*α*) and *P*\_*B**A**T*^(*β*).
     
13.  The steps 5 to 12 were continued until a predefined condition was satisfied in order to identify the best fitness value ℬℱ[𝒯].
     
14.  *f**o**r* *I* = 1 *t**o* *M**I* *d**o*
     
15.  *f**o**r* *J* = 1 *t**o* *P**s**i**z**e* *d**o*
     
16.  The velocity and location of every particles in *P*\_*B**A**T*[*J*] were modified by using the [eqs. (5.13)](#bodymatter-005.xhtml#b_9783110670707-005_eq_013) and ([5.14](#bodymatter-005.xhtml#b_9783110670707-005_eq_014)).
     
17.  Each value of the state *Q*^(ℬ*A**T*)(*t*)[*J*], *P*\_*B**A**T*[*J*]^(*α*) and *P*\_*B**A**T*[*J*]^(*β*) were updated using the rotation gate strategy in order to achieve a better solution from the population.
     
18.  *i**f* (*R**a**n**d* (0,1)>ℬ*R*[*i**j*]) then
     
19.  The best solution was selected after calculating the fitness of all bats from their updated positions and a native solution was generated with the help of the [eq. (5.15)](#bodymatter-005.xhtml#b_9783110670707-005_eq_015).
     
20.  *e**n**d* *i**f*.
     
21.  Now, new solution was evaluated.
     
22.  Each value of the state *Q*^(ℬ*A**T*)(*t*)[*J*], *P*\_*B**A**T*[*J*]^(*α*) and *P*\_*B**A**T*[*J*]^(*β*) were updated by using the rotation gate strategy in order to achieve a better solution from the population.
     
23.  *i**f* (*R**a**n**d* (0,1)<ℬ*A*[*i*]&ℬℱ[𝒯][*n**e**w*]<ℬℱ[𝒯][*B**e**s**t*]) then
     
24.  New solution was accepted.
     
25.  ℬ*R*[*i*]  was increased and ℬ*A*[*i*] was decreased by using the [eqs. (5.16)](#bodymatter-005.xhtml#b_9783110670707-005_eq_016) and ([5.17](#bodymatter-005.xhtml#b_9783110670707-005_eq_017)).
     
26.  *e**n**d* *i**f*.
     
27.  The best solution was chosen.
     
28.  *e**n**d* *f**o**r*.
     
29.  *e**n**d* *f**o**r*
     
30.  Finally, the algorithm produced and reported the optimal number of cluster points 𝒪\_𝒩[𝒞] with its associated fitness value 𝒪\_ℱ[𝒯].
     

## 5.8 Experiment and result analysis

The aim of this article is to propose two different quantum inspired algorithms combined with the working procedure of two dissimilar meta heuristic algorithms namely, Genetic algorithm and Bat algorithm, which were accomplished to recognize the optimum number of clusters present within a given image. In order to accomplish the experiment, the DB – Index \[[40](#bodymatter-005.xhtml#b_9783110670707-005_ref_040)\] was used as an objective function. The optimal result was realized for the minimum value obtained from the computation. The following subsections presents the results obtained from the experiment.

### 5.8.1 Representation scheme of cluster centroids

The cluster centroids within a given image dataset were used to automatically recognize the optimal number of cluster points present in that dataset. During the execution of the process, the following equation was used to choose the cluster centroids.

(5.19)$\\ \\delta\_{i} = \\ \\{\\begin{matrix} {1\\ if\\ \\beta\_{i} > \\ \\alpha\_{i}\\ } \\\\ {0\\ Otherwise} \\\\ \\end{matrix}$ 

where, *δ*[*i*](1 < *i* < *n*) was the activation threshold. By observing the value of *δ*[*i*], the cluster centroids were chosen from a single solution. Here *α*[*i*]  and *β*[*i*] were the complex coefficients and *δ*[*i*] was considered similar to the state of the quantum bit. A value of 1 for *δ*[*i*] represents the activated cluster center implies that the quantum bit is in excited state otherwise it is in the ground state. The following [Figure 5.1](#bodymatter-005.xhtml#b_9783110670707-005_fig_001) is showing the Cluster Centroid representation scheme.

### 5.8.2 Experimental result analysis

In this article two different population based quantum inspired meta-heuristic algorithms, viz., quantum inspired genetic algorithm and quantum inspired bat algorithm are presented. The experiment was performed over four Berkeley images and two real life images. The performance of any meta-heuristic algorithm is very much dependent upon the settings of the parameter i.e., an appropriate selection of parameters can influence the convergence speed of the meta-heuristic algorithm to a great level.

The parameters for QIGA were chosen as Number of generations was considered for the range of values 100 to 500; Population size was taken from 25 to 50. Mutation probability was chosen as 0.01. And for CGA the number of generations was considered from 100 to 500. Population size was taken from 25 to 50. Crossover and Mutation probability was chosen as 0.9 and 0.01 respectively. The parameters for QIBA and CBA were chosen as number of iterations from 100 to 300, Population size was taken from 25 to 50, *γ* = *α* = 0.5, initially pulse rate could be denoted as *r*[*i*]⁰ ∈ \[0, 1\], the wavelength range was \[*λ*[*m**i**n*], *λ*[*m**a**x* ]\] = \[0, 1\], and the range of frequency was \[*F*[*m**i**n*], *F*[*m**a**x* ]\] = \[0, 1\] and the loudness *L*[0 ]\= 0.5.

During the Experiment it was seen that the quantum inspired methods can produce a good result without having a large population or large number of iteration than their corresponding classical methods. Due to the probability amplitude (*α*, *β*) of qubits a single solution may generate several solutions which may lead to increase the size of a small population. So in case of quantum inspired methods the search can start with a small population. For each of the specific settings of parameters each procedure was run for 30 times. The mean value of the fitness was computed from several runs. The computed valued from several runs was presented in the following tables.

The optimal number of clusters along with their associated optimal fitness value for all the implemented algorithms like QIGA, CGA, QIBA and CBA were presented in [Table 5.1](#bodymatter-005.xhtml#b_9783110670707-005_tab_001). From [Table 5.1](#bodymatter-005.xhtml#b_9783110670707-005_tab_001) it can be stated that the computed fitness value from the method QIBA was providing the best fitness value (minimum value) among all other implemented methods for every image datasets and it was also seen that the better fitness values were achieved from quantum inspired methods than their classical counterparts. In [Table 5.2](#bodymatter-005.xhtml#b_9783110670707-005_tab_002) the optimal execution time for all the implemented methods was presented which shows that the quantum inspired methods were taking less time than their classical counterparts and the processing time taken by QIBA was the minimal among other methods. [Table 5.3](#bodymatter-005.xhtml#b_9783110670707-005_tab_003) provides the computed mean value, standard deviation and standard error from QIGA and CGA. Here it is seen that QIGA is providing more promising results than CGA in terms of mean, standard deviation and standard error. Similarly QIBA is providing more promising results than CBA which is presented in [Table 5.4](#bodymatter-005.xhtml#b_9783110670707-005_tab_004). From these two tables it is seen that QIBA has the minimum error among all other. The statistical superiority test named unpaired *t- test* was performed between QIGA and CGA and between QIBA and CBA which is presented in [Table 5.5](#bodymatter-005.xhtml#b_9783110670707-005_tab_005). From [Table 5.5](#bodymatter-005.xhtml#b_9783110670707-005_tab_005) it is seen that out of six results three results are extremely significant and remaining three results are very significant for the comparison between QIGA and CGA. And for QIBA and CBA, out of six results four results are extremely significant, one result is very significant and one result is significant. This analysis indicates that the quantum inspired methods are much more superior to their classical counterparts. Finally, the result of Friedman test for QIGA, CGA, QIBA and CBA is presented in [Table 5.6](#bodymatter-005.xhtml#b_9783110670707-005_tab_006). As per the ranking QIBA is being the most preferable method as it has achieved the first rank.

Table 5.1:Optimal value of the cluster number (𝒪\_𝒩[𝒞]), Optimal fitness value (𝒪\_ℱ[𝒯]) for QIGA, CGA, QIBA and CBA.

 
| Dataset  || QIGA  || CGA  || QIBA  || CBA  |
| --- | --- | --- | --- | --- |
|  || *O*\_**N**[*C*]  || 𝒪**\_**ℱ[𝒯]  || 𝒪**\_**𝒩[𝒞]  || 𝒪\_ℱ[𝒯]  || 𝒪\_𝒩[𝒞]  || 𝒪\_ℱ[𝒯]  || 𝒪\_𝒩[𝒞]  || 𝒪\_ℱ[𝒯]  |
| **#86000**  || 4  || 0.241241  || 3  || 0.310025  || 5  || 0.202196  || 5  || 0.239741  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **#92059**  || 4  || 0.225393  || 4  || 0.297862  || 4  || 0.191752  || 4  || 0.226332  |
| **#94079**  || 4  || 0.250224  || 5  || 0.319232  || 4  || 0.222669  || 5  || 0.241601  |
| **#97017**  || 5  || 0.307631  || 3  || 0.350092  || 5  || 0.300434  || 5  || 0.337940  |
| **couple**  || 5  || 0.146938  || 5  || 0.197734  || 5  || 0.119231  || 5  || 0.148203  |
| **clown**  || 6  || 0.244835  || 5  || 0.244303  || 6  || 0.185826  || 6  || 0.209202  |

Table 5.2:Optimal execution time (𝒪\_𝒯[ℰ]) in second for QIGA, CGA, QIBA and CBA.

| Dataset || QIGA (𝒪\_𝒯[ℰ]) || CGA  (𝒪\_𝒯[ℰ]) || QIBA (𝒪\_𝒯[ℰ]) || CBA (𝒪\_𝒯[ℰ]) |
| --- | --- | --- | --- | --- |
| **#86000** || 49.83 || 74.17 || 12.66 || 38.91 |
| --- | --- | --- | --- | --- |
| **#92059** || 55.56 || 102.89 || 22.36 || 63.87 |
| **#94079** || 53.81 || 97.95 || 21.18 || 49.77 |
| **#97017** || 56.22 || 111.31 || 17.45 || 40.33 |
| **couple** || 123.09 || 238.87 || 68.23 || 97.29 |
| **clown** || 130.11 || 251.69 || 72.37 || 95.82 |

Table 5.3:Mean value of fitness (ℱ[*μ*]), Standard deviation of fitness (ℱ[*σ*]) and Standard error of fitness (𝒮[ℰ]) for QIGA, CGA.

 
| Dataset  || QIGA  || CGA  |
| --- | --- | --- |
|  || ℱ[*μ*]  || ℱ[*σ*]  || 𝒮[ℰ]  || ℱ[*μ*]  || ℱ[*σ*]  || 𝒮[ℰ]  |
| **#86000**  || 0.259923  || 0.031113  || 0.007723  || 0.318324  || 0.061119  || 0.102001  |
| --- | --- | --- | --- | --- | --- | --- |
| **#92059**  || 0.248769  || 0.043454  || 0.009898  || 0.301971  || 0.054612  || 0.009933  |
| **#94079**  || 0.280010  || 0.048452  || 0.009336  || 0.335100  || 0.052379  || 0.006150  |
| **#97017**  || 0.322167  || 0.062244  || 0.008253  || 0.374516  || 0.074216  || 0.012001  |
| **couple**  || 0.156938  || 0.056512  || 0.012636  || 0.214296  || 0.069995  || 0.017591  |
| **clown**  || 0.259843  || 0.034047  || 0.009269  || 0.276215  || 0.045183  || 0.013615  |

Table 5.4:Mean value of fitness (ℱ[*μ*]), Standard deviation of fitness (ℱ[*σ*]) and Standard error of fitness (𝒮[ℰ]) for QIBA and CBA.

 
| Dataset  || QIBA  || CBA  |
| --- | --- | --- |
|  || ℱ[*μ*]  || ℱ[*σ*]  || 𝒮[ℰ]  || ℱ[*μ*]  || ℱ[*σ*]  || 𝒮[ℰ]  |
| **#86000**  || 0.217982  || 0.022745  || 0.006546  || 0.287976  || 0.027456  || 0.007126  |
| --- | --- | --- | --- | --- | --- | --- |
| **#92059**  || 0.221745  || 0.025513  || 0.008571  || 0.293700  || 0.036889  || 0.009193  |
| **#94079**  || 0.228774  || 0.045474  || 0.007238  || 0.277012  || 0.064098  || 0.010117  |
| **#97017**  || 0.315692  || 0.038725  || 0.007321  || 0.371454  || 0.047451  || 0.009676  |
| **couple**  || 0.116231  || 0.043081  || 0.009347  || 0.165203  || 0.048741  || 0.014862  |
| **clown**  || 0.199537  || 0.024239  || 0.005364  || 0.214552  || 0.025914  || 0.006518  |

Table 5.5:Result of unpaired *t* − *t**e**s**t* (𝒫 − *v**a**l**u**e*) between QIGA and CGA and between QIBA and CBA.

 
| Dataset  || QIGA & CGA  || QIBA & CBA  |
| --- | --- | --- |
|  || 𝒫 − **v****a****l****u****e**  || Significant Level  || 𝒫 − *v**a**l**u**e*  || Significant Level  |
| **#86000**  || <0.0001  || 1  || <0.0001  || 1  |
| --- | --- | --- | --- | --- |
| **#92059**  || 0.0002  || 2  || 0.0451  || 3  |
| **#94079**  || 0.0001  || 2  || 0.0001  || 2  |
| **#97017**  || <0.0001  || 1  || <0.0001  || 1  |
| **couple**  || 0.0016  || 2  || <0.0001  || 1  |
| **clown**  || <0.0001  || 1  || <0.0001  || 1  |
| Level of Significance: 1 – Extremely Significant, 2 – Very Significant, 3 – Significant  |

Table 5.6:Result of Friedman test for QIGA, CGA, QIBA and CBA. The rank for each procedure is shown within the parenthesis.

| Dataset || QIGA || CGA || QIBA || CBA |
| --- | --- | --- | --- | --- |
| **#86000** || 0.24 (3) || 0.31 (4) || 0.20 (1) || 0.23 (2) |
| --- | --- | --- | --- | --- |
| **#92059** || 0.22 (2.5) || 0.29 (4) || 0.19 (1) || 0.22 (2.5) |
| **#94079** || 0.25 (3) || 0.31 (4) || 0.20 (1) || 0.24 (2) |
| **#97017** || 0.30 (1.5) || 0.35 (4) || 0.30 (1.5) || 0.33 (3) |
| **couple** || 0.14 (2.5) || 0.19 (4) || 0.10 (1) || 0.14 (2.5) |
| **clown** || 0.24 (3.5) || 0.24 (3.5) || 0.18 (1) || 0.20 (2) |
| **Average Rank** || 2.66 || 3.91 || 1.08 || 2.33 |

### 5.8.3 Simulation of work

Python environment was used to carry out the experimental process. The experiment was done on four Berkeley images, two of dimensions 80 × 120 and other two of dimensions 120 × 80 and two real life images of dimensions 512 × 512. The development environment was consisting of Windows 7 with the configuration facility of DELL Intel(R) Core(TM) i3, 2.00 GHz and 4.00 GB RAM.

The efficiency of the suggested methods over their classical counterparts was proved depending upon computed mean fitness value, standard deviation, standard error and smallest computation time. Moreover, the competence of the quantum inspired algorithms over their classical algorithms was justified by performing the *t – test* (statistical superiority test). The optimal number of cluster (𝒪\_𝒩[𝒞]) and its associated optimal fitness value (𝒪\_ℱ[𝒯]) for all the algorithms (QIGA, CGA, QIBA and CBA) were reported in [Table 5.1](#bodymatter-005.xhtml#b_9783110670707-005_tab_001). The optimal execution time (𝒪\_𝒯[ℰ]) in second for all the algorithms (QIGA, CGA, QIBA and CBA) were shown in [Table 5.2](#bodymatter-005.xhtml#b_9783110670707-005_tab_002). The mean fitness value (ℱ[*μ*]), standard deviation (ℱ[*σ*]) and standard error (𝒮[ℰ]) of the algorithms QIGA and CGA and were demonstrated in [Table 5.3](#bodymatter-005.xhtml#b_9783110670707-005_tab_003) and the same things for the algorithms QIBA and CBA were demonstrated in [Table 5.4](#bodymatter-005.xhtml#b_9783110670707-005_tab_004). Finally, the result of *t* − *t**e**s**t* \[[37](#bodymatter-005.xhtml#b_9783110670707-005_ref_037)\] was presented in [Table 5.5](#bodymatter-005.xhtml#b_9783110670707-005_tab_005) which was performed with 95% confidence level. During the test, the 𝒫 − *v**a**l**u**e* is checked. If it is less than 0.05 then null hypotheses is considered for rejection against the alternative hypothesis. Finally, Friedman test \[[38](#bodymatter-005.xhtml#b_9783110670707-005_ref_038), [39](#bodymatter-005.xhtml#b_9783110670707-005_ref_039)\] was performed among the participating procedure and was enlisted in [Table 5.6](#bodymatter-005.xhtml#b_9783110670707-005_tab_006). The obtained rank from the proposed algorithms QIGA, CGA, QIBA and CBA are 2.66, 3.91, 1.08 and 2.33 respectively. According to the rank value, QIBA can be considered as the superior algorithm as it has the minimum rank value.

### 5.8.4 Dataset used

The following images ([Figure 5.2](#bodymatter-005.xhtml#b_9783110670707-005_fig_002)) were used during the experiment and during the accomplishment of the process the normalized values between (0,1) were considered for the images.

![Figure 5.2: Test Images: (a) #86000 of size 80 × 120, (b) #92059 of size 80 × 120, (c) #94079 of size 120 × 80, (d) #97017 of size 120 × 80, (e) couple of size 512 × 512, (f) clown of size 512 × 512.](graphic/converted/b_9783110670707-005_fig_002.png)

Figure 5.2: Test Images: (a) #86000 of size 80 × 120, (b) #92059 of size 80 × 120, (c) #94079 of size 120 × 80, (d) #97017 of size 120 × 80, (e) couple of size 512 × 512, (f) clown of size 512 × 512.

## 5.9 Conclusion

This article is envisaged an automatic clustering technique to recognize the optimal number of cluster points present in an image dataset, which shows a new way to combine the features of quantum computing with two different meta-heuristic algorithms, viz., Genetic algorithm and Bat algorithm. These proposed techniques were found superior over their classical counterparts as they out performed over corresponding classical counterparts for automatically identifying the optimal number of cluster points present in an image dataset within a significantly small time frame. Also the effectiveness of the quantum inspired algorithms were judged and presented depending upon the computed value of optimal fitness, mean fitness value, standard deviation of the fitness, standard error of the fitness and more over the computed *p* − *v**a**l**u**e*  from the statistical superiority test *t* − *t**e**s**t*. Finally, Friedman test were performed to identify the superior technique between the quantum inspired versions with their classical version. Moreover, it was seen that the quantum inspired Bat algorithm was the best performing procedure among the others. All the computed results were presented in the previous tables in order to proof the effectiveness of the quantum inspired methods over their classical counterparts as well as prove the superiority of QIBA. So far, only gray level images were used for experimental purpose and the proposed techniques were developed to satisfy only one objective at a time.

Currently authors are involved to explore the realm of quantum computing to resolve the concerned multi objective optimization problems effectively and efficiently within a smaller time frame and also trying to take care of the true colour images for this direction of the research.

## References

\[1\]Jain, A., & Dubes, R. Algorithms for Clustering Data. Prentice Hall, 1988. [→](#bodymatter-005.xhtml#xref_d6256e51083)

\[2\]Jain, A. K., Murty, M. N., & Flynn, P. J. Data clustering: A review. ACM Computing Surveys. 1999, 31(3),264–323. [→](#bodymatter-005.xhtml#xref_d6256e51086)

\[3\]Yadav, J. & Sharma, M. A Review of K-mean Algorithm. International Journal of Engineering Trends and Technology (IJETT). July 2013, 4(7). [a](#bodymatter-005.xhtml#xref_d6256e51534), [b](#bodymatter-005.xhtml#xref_d6256e51553)

\[4\]Saket, S., Pandya, J, S. An Overview of Partitioning Algorithms in Clustering Techniques. International Journal of Advanced Research in Computer Engineering & Technology (IJARCET). June 2016, 5(6). [→](#bodymatter-005.xhtml#xref_d6256e51537)

\[5\]Pestunov, I., Rylov, S. A., & Berikov, V. Hierarchical clustering algorithms for segmentation of multispectral images. Optoelectronics, Instrumentation and Data Processing. 2015, 51, 329–338. [→](#bodymatter-005.xhtml#xref_d6256e51540)

\[6Wehrens, R., Buydens, L., Fraley, C., & Raftery, A. Model-Based Clustering for Image Segmentation and Large Datasets via Sampling. Journal of Classification. 2004, 21(2), 231–253. [→](#bodymatter-005.xhtml#xref_d6256e51543)

\[7\]Chen, M. & Ludwig, S. A. Color Image Segmentation Using Fuzzy C-Regression Model. Hindawi Advances in Fuzzy Systems. 2017, 4582948, 15. [→](#bodymatter-005.xhtml#xref_d6256e51546)

\[8\]Ye, Q., Gao, W, & Zeng, W. Color image segmentation using density-based clustering. 2003 International Conference on Multimedia and Expo. ICME ‘03. Proceedings. Baltimore, MD, USA, 2003, 03TH8698, II–401. [→](#bodymatter-005.xhtml#xref_d6256e51550)

\[9\]Holland, J. Adaptation in Natural and Artificial Systems: An Introductory Analysis with Applications to Biology, Control and Artificial Intelligence. The University of Michigan Press, August 1975, 53. [a](#bodymatter-005.xhtml#xref_d6256e51562), [b](#bodymatter-005.xhtml#xref_d6256e51746)

\[10\]Hui-liana, F. & and Xian-lib, L. Discrete particle swarm optimization for TSP based on neighborhood. Application Research of Computers. 2011, 2, 030. [→](#bodymatter-005.xhtml#xref_d6256e51565)

\[11\]Storn, R. & Price, K. Differential evolution – a simple and efficient heuristic for global optimization over continuous spaces. Technical Report TR-95-012, ICSI, 1995. [→](#bodymatter-005.xhtml#xref_d6256e51568)

\[12\]Passino, K. M. Bacterial foraging optimization. Innovations and Devel-opments of Swarm Intelligence Applications. 2012, 219–233. [→](#bodymatter-005.xhtml#xref_d6256e51571)

\[13\]Odili, J. B., Deng, H., Yang, C., Sun, Y., et al. Application of Ant Colony Optimization to Solving the Traveling Salesman’s Problem. Science Journal of Electrical & Electronic Engineering. 2013, 2013. [→](#bodymatter-005.xhtml#xref_d6256e51574)

\[14\]Yang, X.-S. A new metaheuristic bat-inspired algorithm. Studies in Computational Intelligence. 2010, 284, 65–74. [a](#bodymatter-005.xhtml#xref_d6256e51578), [b](#bodymatter-005.xhtml#xref_d6256e51825)

\[15\]Alihodzic, A. & Tuba, M. Improved hybridized bat algorithm for global numerical optimization. Proceedings of the 16th IEEE International Conference on Computer Modelling and Simulation (UKSim-AMSS ‘14). March 2014, 57–62. [→](#bodymatter-005.xhtml#xref_d6256e51581)

\[16\]Liuabcd, Y., Wud, X., Shenb, Y. Automatic clustering using genetic algorithms. Applied Mathematics and Computation, 15 October 2011, 218 (4), 1267–1279. [→](#bodymatter-005.xhtml#xref_d6256e51584)

\[17\]Raposo, C., Antunes, C. H., Barreto, J. P. Automatic Clustering Using a Genetic Algorithm with New Solution Encoding and Operators. Automatic Clustering Using a Genetic Algorithm with New Solution Encoding and Operators. Murgante, B. et al. (Eds.). Computational Science and Its Applications – ICCSA 2014. Lecture Notes in Computer Science, Springer, 2014, 8580. [a](#bodymatter-005.xhtml#xref_d6256e51587), [b](#bodymatter-005.xhtml#xref_d6256e51755)

\[18\]Garai, G., Chaudhuri, B. B. A novel genetic algorithm for automatic clustering. Journal Pattern Recognition Letters Archive. Elsevier Science Inc. New York, NY, USA, 19 January 2004, 25(2),173–187. [a](#bodymatter-005.xhtml#xref_d6256e51590), [b](#bodymatter-005.xhtml#xref_d6256e51758)

\[19\]Das, S., Ajith, A., & Konar, A. Automatic Clustering Using an Improved Differential Evolution Algorithm. Systems, Man and Cybernetics, Part A: Systems and Humans, IEEE Transactions, 2008, 38, 218–237. 10.1109/TSMCA.2007.909595 [→](#bodymatter-005.xhtml#xref_d6256e51593)

\[20\]Abubaker, A., Baharum, A., Alrefaei, M. Automatic Clustering Using Multi-objective Particle Swarm and Simulated Annealing. 1 July 2015, 10(7), e0130995. doi: 10.1371/journal.pone.0130995 [→](#bodymatter-005.xhtml#xref_d6256e51597)

\[21\]McMohan, D. Quantum Computing Explained. John Wiley & Sons, Inc., Hoboken, New Jersey, 2008. [→](#bodymatter-005.xhtml#xref_d6256e51600)

\[22\]Dey, S., Bhattacharyya, S., & Maullik, U. Quantum Behaved Swarm Intelligent Techniques for Image Analysis: A Detailed Survey. Handbook of Research on Swarm Intelligence in Engineering. 2015. [→](#bodymatter-005.xhtml#xref_d6256e51660)

\[23\]Dey, S., Saha, I., Bhattacharyya, S., & Maulik, U. Multi-level thresholding using quantum inspired meta-heuristics. Knowledge-Based Systems. 2014, 67, 373–400. [a](#bodymatter-005.xhtml#xref_d6256e51603), [b](#bodymatter-005.xhtml#xref_d6256e51644)

\[24\]Dey, S., Bhattacharyya, S., & Maullik, U. Optimum Gray Level Image Thresholding using a Quantum Inspired Genetic Algorithm. Advanced Research on Hybrid Intelligent Techniques and Applications. 2015, 201. [a](#bodymatter-005.xhtml#xref_d6256e51606), [b](#bodymatter-005.xhtml#xref_d6256e51647), [c](#bodymatter-005.xhtml#xref_d6256e53219), [d](#bodymatter-005.xhtml#xref_d6256e53860)

\[25\]Dey, S., Bhattacharyya, S., & Maulik, U. Quantum inspired genetic algorithm and particle swarm optimization using chaotic map model based interference for gray level image thresholding. Swarm and Evolutionary Computation. 2014, 15, 38–57. [a](#bodymatter-005.xhtml#xref_d6256e51609), [b](#bodymatter-005.xhtml#xref_d6256e51650), [c](#bodymatter-005.xhtml#xref_d6256e53222), [d](#bodymatter-005.xhtml#xref_d6256e53863)

\[26\]Dey, S., Bhattacharyya, S., & Maullik, U. Efficient quantum inspired meta-heuristics for multi-level true color image thresholding. Applied Soft Computing. 2017, 56, 472–513. [a](#bodymatter-005.xhtml#xref_d6256e51612), [b](#bodymatter-005.xhtml#xref_d6256e51654), [c](#bodymatter-005.xhtml#xref_d6256e53225), [d](#bodymatter-005.xhtml#xref_d6256e53866)

\[27\]Dey, S., Bhattacharyya, S., & Maullik, U. New quantum inspired meta-heuristic techniques for multi-level color image thresholding. Applied Soft Computing. 2016, 46, 677–702. [a](#bodymatter-005.xhtml#xref_d6256e51616), [b](#bodymatter-005.xhtml#xref_d6256e51657)

\[28\]Dey, S., Bhattacharyya, S., & Maullik, U. Quantum inspired automatic clustering for multi-level image thresholding. Proceedings of International Conference On Computational Intelligence and Communication Networks (ICCICN 2014), RCCIIT, Kolkata, India. 2014, 247–251. [a](#bodymatter-005.xhtml#xref_d6256e51619), [b](#bodymatter-005.xhtml#xref_d6256e51663)

\[29\]Dey, S., Bhattacharyya, S., & Maullik, U. Quantum inspired automatic clustering for multi-level image thresholding. Proceedings of International Conference On Computational Intelligence and Communication Networks (ICCICN 2014), RCCIIT, Kolkata, India. 2014, 242–246 [a](#bodymatter-005.xhtml#xref_d6256e51622), [b](#bodymatter-005.xhtml#xref_d6256e51666)

\[30\]Dey, S., Bhattacharyya, S., Snasel, V., Dey, A., & Sarkar, S. PSO and DE based novel quantum inspired automatic clustering techniques. 2017, 285–290. 10.1109/ICRCICN.2017.8234522 [a](#bodymatter-005.xhtml#xref_d6256e51625), [b](#bodymatter-005.xhtml#xref_d6256e51669)

\[31\]Dey, A., Dey, S., Bhattacharyya, S., Snasel, V., & Hassanien, A. E. Simulated Annealing Based Quantum Inspired Automatic Clustering Technique. Hassanien, A., Tolba, M., Elhoseny, M., Mostafa, M. (Eds.). The International Conference on Advanced Machine Learning Technologies and Applications (AMLTA2018). Advances in Intelligent Systems and Computing. Springer, Cham, 2018, 723. [a](#bodymatter-005.xhtml#xref_d6256e51628), [b](#bodymatter-005.xhtml#xref_d6256e51673)

\[32\]Dey, S., Bhattacharyya, S., & Maullik, U. Quantum-Inspired Automatic Clustering Technique Using Ant Colony Optimization Algorithm. Quantum-Inspired Intelligent Systems for Multimedia Data Analysis. 2018. 10.4018/978-1-5225-5219-2.ch002 [a](#bodymatter-005.xhtml#xref_d6256e51631), [b](#bodymatter-005.xhtml#xref_d6256e51676)

\[33\]Narayanan, A. & Moore, M. Quantum-inspired genetic algorithms. Proc. IEEE Evolutionary Computation. 1996, 61–66. [→](#bodymatter-005.xhtml#xref_d6256e51635)

\[34\]Yang, Y., Kuo, S., Lin, F., Liu, I., & Chou, Y. Improved Quantum-Inspired Tabu Search Algorithm for Solving Function Optimization Problem. 2013 IEEE International Conference on Systems, Man, and Cybernetics, Manchester. 2013, 823–828. [→](#bodymatter-005.xhtml#xref_d6256e51638)

\[35\]Han, K.-H., & Kim, J.-H. Quantum-inspired evolutionary algorithm for a class of combinatorial optimization. IEEE Transactions on Evolutionary Computation. December 2002, 6(6),580–593. [→](#bodymatter-005.xhtml#xref_d6256e51641)

\[36\]Alam, T., Gandhi, T., & Nitin, N. Quantum Genetic Algorithm with Rotation Angle Refinement for Dependent Task Scheduling on Distributed Systems. 2017. 10.1109/IC3.2017.8284295 [→](#bodymatter-005.xhtml#xref_d6256e51679)

\[37\]Flury, B. A First Course in Multivariate Statistics. Springer-Verlag, Berlin, Germany, 1997. [a](#bodymatter-005.xhtml#xref_d6256e51690), [b](#bodymatter-005.xhtml#xref_d6256e65659)

\[38\]Friedman, M. The use of ranks to avoid the assumption of normality implicit in the analysis of variance. Journal of the American Statistical Association. 1937, 32, 674–701. [a](#bodymatter-005.xhtml#xref_d6256e51696), [b](#bodymatter-005.xhtml#xref_d6256e65689)

\[39\]Friedman, M. A comparison of alternative tests of significance for the problem of m rankings. Annals of Mathematical Statistics. 1940, 11, 86–92. [a](#bodymatter-005.xhtml#xref_d6256e51699), [b](#bodymatter-005.xhtml#xref_d6256e65692)

\[40\]Maulik, U., & Bandyopadhyay, S. Performance evaluation of some clustering algorithms and validity indices. IEEE PAMI. 2002, 24, 1650–1654. [a](#bodymatter-005.xhtml#xref_d6256e51703), [b](#bodymatter-005.xhtml#xref_d6256e54298), [c](#bodymatter-005.xhtml#xref_d6256e54314), [d](#bodymatter-005.xhtml#xref_d6256e54330), [e](#bodymatter-005.xhtml#xref_d6256e54801), [f](#bodymatter-005.xhtml#xref_d6256e56137), [g](#bodymatter-005.xhtml#xref_d6256e63047)

\[41\]Aranha, C. Portfolio management by genetic algorithm with error modeling. Information Sciences. 2007, 459–465. [→](#bodymatter-005.xhtml#xref_d6256e51761)

\[42\]Paulinas, M., & Usinskas, A. A survey of genetic algorithms applications for image enhancement and segmentation. Information Technology and Control. 2007, 36, 278–284. [→](#bodymatter-005.xhtml#xref_d6256e51764)

\[43\]Dey, A., Bhattacharyya, S., Dey, S., Platos, J., & Snasel, V. Quantum-Inspired Bat Optimization Algorithm for Automatic Clustering of Grayscale Images. Recent Trends in Signal and Image Processing. 2019, 89–101. 10.1007/978-981-13-6783-0\_9 [a](#bodymatter-005.xhtml#xref_d6256e58137), [b](#bodymatter-005.xhtml#xref_d6256e59288)

\[44\]Sun, J., Fang, W., Wu, X., Palade, V., & Xu, W. Quantum-Behaved Particle Swarm Optimization: Analysis of Individual Particle Behavior and Parameter Selection. Evolutionary Computation. September 2012, 20(3),349–393. [→](#bodymatter-005.xhtml#xref_d6256e59291)

# 6 Conclusion

Siddhartha Bhattacharyya 

Machine learning is a branch of Artificial intelligence, which tries to develop techniques that have ability to learn from experiences. These experiences are articulated as data generated from underlying models. The goal of any machine learning technique is to abstract the underlying model reliably for specific tasks like prediction and decision making. Enticed by the versatility of quantum mechanics, scientists have embarked on evolving machine learning algorithms based on the principles of quantum mechanics. As a result, different incarnations of the classical machine learning algorithms have come up enveloped within the quantum computing mechanisms. This book intends to throw a light on some of the recent advancements in this direction.

The book first introduces to the readers the basics of quantum machine learning with reference to the well-known quantum algorithms in the form of Grover’s search algorithm \[[1](#bodymatter-006.xhtml#b_9783110670707-006_ref_001)\], quantum reinforcement learning \[[2](#bodymatter-006.xhtml#b_9783110670707-006_ref_002), [3](#bodymatter-006.xhtml#b_9783110670707-006_ref_003), [4](#bodymatter-006.xhtml#b_9783110670707-006_ref_004), [5](#bodymatter-006.xhtml#b_9783110670707-006_ref_005), [6](#bodymatter-006.xhtml#b_9783110670707-006_ref_006)\] and quantum annealing \[[7](#bodymatter-006.xhtml#b_9783110670707-006_ref_007), [8](#bodymatter-006.xhtml#b_9783110670707-006_ref_008)\]. A bird’s eye view on the evolution of quantum neural networks \[[9](#bodymatter-006.xhtml#b_9783110670707-006_ref_009), [10](#bodymatter-006.xhtml#b_9783110670707-006_ref_010), [11](#bodymatter-006.xhtml#b_9783110670707-006_ref_011), [12](#bodymatter-006.xhtml#b_9783110670707-006_ref_012), [13](#bodymatter-006.xhtml#b_9783110670707-006_ref_013), [14](#bodymatter-006.xhtml#b_9783110670707-006_ref_014), [15](#bodymatter-006.xhtml#b_9783110670707-006_ref_015), [16](#bodymatter-006.xhtml#b_9783110670707-006_ref_016), [17](#bodymatter-006.xhtml#b_9783110670707-006_ref_017)\] is also presented. The information processing capabilities of quantum algorithms depends on the quantum implementation of machine learning algorithms involving nonlinear functions operating on information represented topographically, as is common in neural cortex. Several approaches to quantum computation for machine learning by means of topographic representation have been proposed. These approaches show ways to construct unitary operators, implementable on quantum computers, that implement arbitrary (including nonlinear) functions via computational maps.

Optimization problems are ubiquitous in machine learning and other domains like engineering and a number of specialized techniques for efficiently solving specific problems have been developed. A novel quantum optimization algorithm based on Adiabatic Quantum Computation through local evolution and inspired by the ideas from Grover’s Search algorithm \[[1](#bodymatter-006.xhtml#b_9783110670707-006_ref_001)\] can be evolved for finding minimum and employed in solving unconstrained optimization problems.

As a transition from the classical paradigm to quantum paradigm, several researchers are involved in developing quantum inspired algorithms to bridge the gap between the two paradigms. Notable among them include the quantum inspired metaheuristic algorithms capable of delivering outputs in real time. Different incarnations of the quantum inspired metaheuristic algorithms have come up, thanks to the relentless efforts on the part of the scientists. These algorithms are efficient enough to obtain stable outputs by emulating the quantum mechanical principles on classical computers. In most of the cases, it is found that the quantum inspired versions of the metaheuristic algorithms outperform their classical counterparts.

Although most of the quantum machine learning algorithms are based on the bilevel qubits, of late, much work is being carried out using multilevel quantum systems (using qutrits or qudits), which promise more efficiency.

## References

\[1\]Lavor, C., Manssur, L.R.U., & Portugal, R. Grover’s Algorithm: Quantum Database Search. arXiv:quant-ph/0301079. [a](#bodymatter-006.xhtml#xref_d6256e67433), [b](#bodymatter-006.xhtml#xref_d6256e67489)

\[2\]Beom, H. R., & Cho, H. S. A sensor-based navigation for a mobile robot using fuzzy logic and reinforcement learning. IEEE Transactions on Systems, Man, and Cybernetics. 1995, 25(3), 464–477. [→](#bodymatter-006.xhtml#xref_d6256e67436)

\[3\]Connolly, C. I. Harmonic functions and collision probabilities. The International Journal of Robotics Research. 1997,16(4), 497–507. [→](#bodymatter-006.xhtml#xref_d6256e67439)

\[4\]Smart, W. D., & Kaelbling, L. P. Effective reinforcement learning for mobile robots. Proceedings – IEEE International Conference on Robotics and Automation. 2002, 3404–3410. [→](#bodymatter-006.xhtml#xref_d6256e67442)

\[5\]Kondo, T., & and Ito, K. A reinforcement learning with evolutionary state recruitment strategy for autonomous mobile robots control. Robotics and Autonomous Systems. 2004, 46(2),111–124. [→](#bodymatter-006.xhtml#xref_d6256e67445)

\[6\]Tzafestas, S. G., & Rigatos, G. G. Fuzzy reinforcement learning control for compliance tasks of robotic manipulators. IEEE Transactions on Systems, Man, and Cybernetics. 2002, 32(1),107–113. [→](#bodymatter-006.xhtml#xref_d6256e67449)

\[7\]Matsuda, Y., Nishimori, H. & Katzgraber, H. G. Ground-state statistics from annealing algorithms: Quantum vs classical approaches. 2009. arXiv:0808.0365. [→](#bodymatter-006.xhtml#xref_d6256e67452)

\[8\]Santoro, G. E., Martonak, R., Tosatti, E. & Car, R. Theory of quantum annealing of an Ising spin glass. Science. 2002, 295(5564),2427–2430. [→](#bodymatter-006.xhtml#xref_d6256e67455)

\[9\]da Silva, A. J., Ludermir, T. B., & de Oliveira, W. R. Quantum perceptron over a field and neural network architecture selection in a quantum computer. Neural Networks. 2016, 76, 55–64. [→](#bodymatter-006.xhtml#xref_d6256e67458)

\[10\]Panella, M., & Martinelli, G. Neural networks with quantum architecture and quantum learning. International Journal of Circuit Theory and Applications. 2011, 39, 61–77. [→](#bodymatter-006.xhtml#xref_d6256e67461)

\[11\]Kak, S. On quantum neural computing. Advances in Imaging and Electron Physics. 1995, 94, 259. [→](#bodymatter-006.xhtml#xref_d6256e67464)

\[12\]Chrisley, R. Quantum Learning. New directions in cognitive science: Proceedings of the international symposium, Saariselka, 4–9 August 1995, Lapland, Finland. Pylkkänen, P. & Pylkkö, P. (Eds.). Finnish Association of Artificial Intelligence, Helsinki, 1995, 77–89. [→](#bodymatter-006.xhtml#xref_d6256e67468)

\[13\]Narayanan, A., & Menneer, T. Quantum artificial neural network architectures and components. Information Sciences. 2000, 128, 231–255. [→](#bodymatter-006.xhtml#xref_d6256e67471)

\[14\]Schuld, M., Sinayskiy, I., & Petruccione, F. Simulating a perceptron on a quantum computer. 2014. ArXiv:1412.3635. [→](#bodymatter-006.xhtml#xref_d6256e67474)

\[15\]Purushothaman, G., & Karayiannis, N. Quantum Neural Networks (QNN’s): Inherently Fuzzy Feedforward Neural Networks. IEEE Transactions on Neural Networks. 1997, 8(3), 679. [→](#bodymatter-006.xhtml#xref_d6256e67477)

\[16\]Behrman, E. C., Steck, J. E., Kumar, P., & Walsh, K. A. Quantum Algorithm design using dynamic learning. Quantum Information and Computation. 2008, 8(1&2), 12–29. [→](#bodymatter-006.xhtml#xref_d6256e67480)

\[17\]Ventura, D., & Martinez, T. A quantum associative memory based on Grover’s algorithm. Proceedings of the International Conference on Artificial Neural Networks and Genetics Algorithms. 1999, 22–27. [→](#bodymatter-006.xhtml#xref_d6256e67483)

# Index

*   *   adiabatic
    *   Amplitude
    *   analog computation
    *   Analysis
    *   ancilla
    *   Automatic clustering

*   *   Bat Algorithm
    *   Berkeley image
    *   brain-inspired computation

*   *   CCNOTToffoli gate
    *   Chromosomes
    *   Classical counterparts
    *   Cluster centroids
    *   Cluster Validity Index
    *   CNOT
    *   coarse coding
    *   Coherence
    *   computational maptopographic map
    *   Convergence
    *   crisp set
    *   Crossover
    *   CSWAPFredkin gate

*   *   DB index
    *   Decoherence
    *   Deep Learning
    *   demultiplexer
    *   Dirac delta
    *   Dirac notation
    *   Diversity

*   *   Echolocation
    *   Entangled
    *   Evolutionary

*   *   field computation
    *   Fitness
    *   Fredkin gateCSWAP
    *   Frequency
    *   Friedman test
    *   Fuzzy clustering
    *   fuzzy set

*   *   Gates
    *   Generations
    *   Genetic Algorithm
    *   graph kernel
    *   Grover iteration
    *   Grover’s algorithm
    *   Grover’s search

*   *   Hadamard gate
    *   Hamiltonian
    *   Heterogeneous
    *   HHL algorithm
    *   Hilbert space
    *   Hilbert-Schmidt linear operator
    *   Homogeneous

*   *   Image dataset
    *   Intensity

*   *   K-Means

*   *   least square SVM
    *   Loudness

*   *   Machine learning
    *   Mean
    *   Meta-heuristic
    *   Methods
    *   Mutation

*   *   Nature inspired
    *   neural network,quantum neural network, spiking neural network
    *   Normalized

*   *   Optimal number

*   *   Pauli
    *   Population
    *   precision
    *   preimage
    *   preimage multiplicity
    *   Prey
    *   Principal component analysis
    *   Probability
    *   Pulses

*   *   Quantum algorithms
    *   quantum annealing
    *   Quantum Approximate Optimization Algorithm
    *   Quantum Boltzmann Machines
    *   quantum computation
    *   Quantum computing
    *   Quantum Deep Learning
    *   Quantum Generative Adversarial Networks
    *   Quantum Gradient Descent Algorithm
    *   Quantum inspired
    *   quantum machine learning
    *   Quantum matrix inversion
    *   quantum multiclass support vector machine
    *   quantum neural network
    *   Quantum NOT gate
    *   quantum parallelismsuperposition
    *   Quantum random access memory
    *   quantum register
    *   Quantum state
    *   Quantum Support Vector Machines
    *   *Qubit*

*   *   Randomly
    *   reinforcement learning
    *   Results
    *   Rotation angle
    *   Rotation gate

*   *   Searching
    *   Selection
    *   setcrisp set, fuzzy set
    *   Shor algorithm
    *   spiking neural network
    *   Standard deviation
    *   Standard error
    *   Statistical
    *   superposition
    *   supervised learning
    *   Support Vector Machines

*   *   Table
    *   Time
    *   Toffoli gateCCNOT
    *   topographic basis map
    *   topographic maptopographic basis map, topographic qubit map, computational map
    *   topographic qubit map
    *   topographic representationtopographic map

*   *   unsupervised learning

*   *   vector space

*   *   wave function

* * *

1.   
    
    They are numerically indexed, of course, but interchangeable in terms of their pattern of connections before learning.[↩](#fnref1)
    
2.   
    
    It is not the same as the graph kernels used in machine learning applied to graph theory.[↩](#fnref2)
    
3.   
    
    For example, *f*(*x*) = \[*t**a**n**h* *x*/*t**a**n**h* 1\]|[\[ − 1, 1\]].[↩](#fnref3)
    
4.   
    
    It is easy however to produce the binary representation of either the maximum or minimum number with unit amplitude (*p*[*j*] = 1, *p*[*j*]^′ = 0) in a map.[↩](#fnref4)