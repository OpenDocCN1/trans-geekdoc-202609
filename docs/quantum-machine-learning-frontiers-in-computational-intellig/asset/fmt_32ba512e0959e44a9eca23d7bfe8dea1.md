
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

# 1 Introduction to quantum machine learning

Sandip Dey Department of Computer Science, Sukanta Mahavidyalaya, Jalpaiguri, West Bengal, India Sourav De Department of Computer Science & Engineering, Cooch Behar Government Engineering College, Cooch Behar, West Bengal, India Siddhartha Bhattacharyya CHRIST (Deemed to be University), Department of Computer Science and Engineering, CHRIST (Deemed to be University), Bangalore, India, Hosur Road, 560029, Kolkata, Bangalore, Karnataka, India

## Abstract

Quantum Machine Learning (QML) is popularly known to be an integrative approach to learning of the Quantum Physics (QP) and Machine Learning (ML). In this chapter, an outline of the fundamental ideas and features related to quantum machine learning is laid out. The different facets of quantum algorithms are discussed in this chapter. In addition to this, the basic features of quantum reinforcement learning and quantum annealing are also provided in this chapter. Finally, the chapter deliberates about the advancement of quantum neural networks to through light in the direction of QML.

Keywords: machine learning, Grover’s Search Algorithm, reinforcement learning, quantum annealing, quantum neural networks,

### 1.1 Quantum machine learning
