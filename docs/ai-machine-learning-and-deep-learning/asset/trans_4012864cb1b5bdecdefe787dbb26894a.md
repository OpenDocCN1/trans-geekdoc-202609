
The main research question was:

## 哪些机器学习和大数据分析范式在开发网络安全系统方面最有效？

The subquestions are:

- 机器学习和大数据分析范式在网络安全中是如何使用的？
- 如何利用机器学习和大数据分析范式开发网络安全系统？

## 14.2 文献综述

### 14.2.1 概述

Computers, phones, internet, and all other information systems developed for the benefit of humanity are susceptible to criminal activity [10]。
计算机、手机、互联网以及所有为人类福祉而开发的其他信息系统都易受犯罪活动侵害 [10]。
Cyber crimes consist of offenses such as computer intrusions, misuse of intellectual property rights, economic espionage, online extortion, international money laundering, nondelivery of goods or services, etc. [11]。
网络犯罪包括计算机入侵、知识产权权利滥用、经济间谍、在线勒索、国际洗钱、货物或服务未交付等违法行为 [11]。
Today, “cyber crimes” has become known as a very common phrase, yet its definition has not been easy to compose as there are many variants to its classification。
如今，“网络犯罪”已成为一个非常常见的短语，但其定义并不容易制定，因为其分类存在许多变体。
In their varying and diverging definitions, the majority of the authors agree on two of the most important aspects: that it’s usually an unauthorized performance of an act on a computer network by a third party and that, usually, that party seeks to bring damage or loss to the organization。
在各不相同的定义中，大多数作者一致认为两个最重要的方面：通常是由第三方对计算机网络进行未经授权的行为，并且通常该方寻求对组织造成损害或损失。

On a daily basis, the amount of data processed and stored on computers as well as other digital technologies is increasing and human dependence on these computer networks is also increasing。
日常生活中，计算机以及其他数字技术上处理和存储的数据量不断增加，人类对这些计算机网络的依赖也在增加。
Intrusion detection and prevention systems (IDPS) include all protective actions or identification of possible incidents and analysing log information of such incidents [9]。
入侵检测和预防系统（IDPS）包括所有保护措施或对可能事件的识别以及对此类事件日志信息的分析 [9]。
In [11], the use of various security control measures in an organization was recommended。
在 [11] 中，建议在组织中使用各种安全控制措施。
Various attack descriptions from the outcome of the research by [37] are shown on Table 14.2。
[37] 研究结果中的各种攻击描述如表 14.2 所示。

## 表 14.2 各种攻击描述

| 攻击类型 | 描述 |
|---|---|
| DoS | Denial of service: an attempt to make a network resource unavailable to its intended users; temporarily interrupt services of a host connected to the Internet |
| Scan | A process that sends client requests to a range of server port addresses on a host to find an active port |
| Local access | The attacker has an account on the system in question and can use that account to attempt unauthorized tasks |
| User to root | Attackers access a user account on the system and are able to exploit some vulnerability to gain root access to the system |
| Data | Attackers involve someone performing an action that they may be able to do on a given computer system but that they are not allowed to do according to policy |

Source: [37]。
来源：[37]。

However, there is a clear distinction between cyber security and information security, as illustrated in Figure 14.3。
然而，网络安全与信息安全之间存在明显区别，如图 14.3 所示。

![](img/efffc69cb8cda75bcf341884e3396898_336_0.png)

## 图 14.3 信息安全与网络安全的区别。

Source: [45]。
来源：[45]。

The monotonic increase in an assortment of cyber threats and malwares amply demonstrates the inadequacy of the current countermeasures to defend computer networks and resources。
各类网络威胁和恶意软件的单调增加充分证明了当前防御计算机网络和资源对策的不足。
These issues demand the development of efficient solutions to cyber security。
这些问题要求开发网络安全的有效解决方案。
To alleviate the problems of the classic techniques of cyber security, research in artificial intelligence and more specifically in machine learning is sought after [1]。
为缓解网络安全经典技术的弊端，人工智能尤其是机器学习的研究备受关注 [1]。
Machine learning teaches the distinction between good and malicious files。
机器学习教会了区分良性和恶意文件。
Deep learning is a submodule of machine learning and is often referred to as deep neural networks (DNNs) [41]。
深度学习是机器学习的子模块，通常被称为深度神经网络（DNNs） [41]。
Deep learning doesn’t need any domain expert knowledge assistance to understand the importance of new input。
深度学习不需要任何领域专家知识的帮助来理解新输入的重要性。
To enhance the malware and cyber attack detection rate, one can apply deep learning architectures to cyber security [35]。
为了提高恶意软件和网络攻击的检测率，可以将深度学习架构应用于网络安全 [35]。
Experiments with classical machine learning algorithms are run on CPU-enabled machines, and deep learning architectures are run on GPU-enabled machines。
经典机器学习算法的实验在启用 CPU 的机器上运行，而深度学习架构在启用 GPU 的机器上运行。

### 14.2.2 经典机器学习（CML）

Machine learning is a field in artificial intelligence where computers learn like people。
机器学习是人工智能的一个领域，计算机像人一样学习。
We present and briefly discuss the most commonly used classical machine learning algorithms [46]。
我们介绍并简要讨论最常用的经典机器学习算法 [46]。

### 14.2.2.1 逻辑回归（LR）

As an idea obtained from statistics and created by [47], logistic regression is like linear regression, yet it averts the misclassification that may occur in linear regression。
作为从统计学中获得并由 [47] 提出的思想，逻辑回归类似于线性回归，但避免了线性回归中可能出现的误分类。
Unlike linear regression, logistic regression results are basically either 0 or 1。
与线性回归不同，逻辑回归的结果基本上是 0 或 1。
The efficacy of logistic regression is mostly dependent on the size of the training data。
逻辑回归的有效性主要取决于训练数据的大小。

### 14.2.2.2 朴素贝叶斯（NB）

Naïve Bayes (NB) classifier is premised on the Bayes theorem, which assumes the independence of features。
朴素贝叶斯（NB）分类器基于贝叶斯定理，该定理假设特征相互独立。
The independence assumptions in naïve Bayes classifier overcome the curse of dimensionality。
朴素贝叶斯分类器中的独立性假设克服了维度灾难。

### 14.2.2.3 决策树（DT）

A decision tree has a structure like flow charts, where the root node is the top node and a feature of the information is denoted by each internal node。
决策树具有类似流程图的结构，其中根节点为顶节点，每个内部节点表示信息的一个特征。
The algorithm might be biased and may end up unstable since a little change in the information changes the structure of the tree。
该算法可能存在偏差且可能不稳定，因为信息的一点变化就会改变树的结构。

### 14.2.2.4 K-最近邻（KNN）

K-nearest neighbor (KNN) is a nonparametric approach that uses similarity measure in terms of distance function classifiers other than new cases。
K-最近邻（KNN）是一种非参数方法，使用距离函数分类器以相似性度量来处理新案例。
KNN stores the entire training data, requires larger memory, and so is computationally expensive。
KNN 存储整个训练数据，需要更大的内存，因此计算成本高。

### 14.2.2.5 AdaBoost（AB）

The AdaBoost (AB) learning algorithm is a technique used to boost the performance of simple learning algorithms used for classification。
AdaBoost（AB）学习算法是一种用于提高分类中使用的简单学习算法性能的技术。
AdaBoost constructs a strong classifier using a combination of several weak classifiers。
AdaBoost 使用多个弱分类器的组合构建强分类器。
It is a fast classifier and at the same time can also be used as a feature learner。
它是一种快速分类器，同时也可以用作特征学习器。
This may be useful in tasks that use imbalanced data analysis。
这在不平衡数据分析任务中可能很有用。

### 14.2.2.6 随机森林（RF）

Random forest (RF), as an ensemble tool, is a decision tree derived from a subset of observations and variables。
随机森林（RF）作为一种集成工具，是从观测值和变量的子集派生的决策树。
The random forest gives better predictions than an individual decision tree。
随机森林比单个决策树给出更好的预测。
It uses the concept of bagging to create several minimal correlated decision trees。
它使用装袋的概念创建多个最小相关决策树。

### 14.2.2.7 支持向量机（SVM）

Support vector machine (SVM) belongs to the family of supervised machine learning techniques that can be used to solve classification and regression problems。
支持向量机（SVM）属于可用于解决分类和回归问题的监督机器学习技术家族。
SVM is a linear classifier, and the classifier is a hyperplane。
SVM 是一种线性分类器，分类器是一个超平面。
It separates the training set with maximal margin。
它以最大间隔分离训练集。
The points near the separating hyperplane are called support vectors, and they determine the position of the hyperplane。
靠近分离超平面的点称为支持向量，它们决定了超平面的位置。

## 14.2.3 现代机器学习

Deep learning is modern machine learning with the capability to take raw inputs and learn the optimal feature representation implicitly。
深度学习是现代机器学习，具有接受原始输入并隐式学习最优特征表示的能力。
This has performed well in various long-standing artificial intelligence tasks [41]。
这在各种长期的人工智能任务中表现良好 [41]。
The most commonly used deep learning architectures are discussed next in detail。
接下来将详细讨论最常用的深度学习架构。

### 14.2.3.1 深度神经网络（DNN）

An artificial neural network (ANN) is a computational model influenced by the characteristics of biological neural networks。
人工神经网络（ANN）是一种受生物神经网络特征影响的计算模型。
The family of ANN includes the feed-forward neural network (FFN), convolutional neural network, and recurrent neural network (RNN)。
ANN 家族包括前馈神经网络（FFN）、卷积神经网络和循环神经网络（RNN）。
FFN forms a directed graph in which a graph is composed of neurons group as a mathematical unit。
FFN 形成一个有向图，其中图由作为数学单元的神经元组组成。
Each neuron in the ith layer has a connection to all the neurons in i + 1th layer。
第 i 层中的每个神经元都与第 i + 1 层中的所有神经元相连。

Each neuron of the hidden layer denotes a parameter h that is computed by

h_i(x) = f(w_i^T x + b_i),  (14.2.1)
h_ii: R^{d_{i-1}} → R^{d_i},  (14.2.2)
f: R → R,  (14.2.3)

where w_i ∈ R^{d×d_{i-1}}, b_i ∈ R^{d_i}, d_i denotes the size of the input, f is a nonlinear activation function ReLU。
其中 w_i ∈ R^{d×d_{i-1}}，b_i ∈ R^{d_i}，d_i 表示输入的大小，f 是非线性激活函数 ReLU。

The traditional examples of machine learning algorithms include linear regression, logistic regression, linear discriminant analysis, classification and regression trees, naïve Bayes, K-nearest neighbor (KNN, K means clustering), learning vector quantization (LVQ), support vector machines (SVM), random forest, Monte Carlo, neural networks and Q-learning。
机器学习算法的传统示例包括线性回归、逻辑回归、线性判别分析、分类与回归树、朴素贝叶斯、K-最近邻（KNN，K 均值聚类）、学习向量量化（LVQ）、支持向量机（SVM）、随机森林、蒙特卡洛、神经网络和 Q 学习。

- *监督适应*: Adaptation is carried out in the execution of system at every iteration。
- *监督适应*：适应在系统的每次迭代执行中进行。

