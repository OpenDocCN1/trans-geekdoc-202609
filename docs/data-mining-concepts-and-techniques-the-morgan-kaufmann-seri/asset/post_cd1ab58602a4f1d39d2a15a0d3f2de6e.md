
## 9.10.

We wish to partition the data tuples into two clusters. Let \( q \) be a cluster membership vector of length \( n \): \( q(i) = 1 \) if data tuple \( i \) belongs to Cluster A; and \( q(i) = -1 \) if it belongs to Cluster B. One way to find these two clusters is to minimize the so-called *cut-size*, which measures the total similarities across different clusters:

\[
q^* = \arg \min_{q \in \{-1, 1\}^n} J = \frac{1}{4} \sum_{i,j=1}^n (q(i) - q(j))^2 W(i, j). \tag{9.48}
\]

- a. Prove that the cut-size \( J = \frac{1}{2} q^T (D - W)q \), where \( D \) is the degree matrix of \( W \): \( D(i, i) = \sum_{j=1}^n W(i, j) \) and \( D(i, j) = 0 \) for \( j \neq i \); and \( ^T \) is the vector transpose.

- b. It is very difficult to directly optimize Eq. (9.48) since the cluster membership vector \( q \) is a binary vector. In practice, we relax \( q \) and allow it to take real numbers, and aim to solve the following optimization problem instead. Prove that the optimal solution of Eq. (9.49) is given by the eigenvector of \( D - W \) that corresponds to the second smallest eigenvalue.

\[
q^* = \arg \min_{q \in R^n} q^T (D - W)q \quad \text{s.t.} \quad \sum_{i=1}^n q(i)^2 = n \tag{9.49}
\]

## 9.11. SimRank is a similarity measure for clustering graph and network data.

- a. Prove \( \lim_{i \to \infty} s_i(u, v) = s(u, v) \) for SimRank computation.

- b. Show \( s(u, v) = p(u, v) \) for SimRank.

## 9.12. In a large sparse graph where on average each node has a low degree, is the similarity matrix using SimRank still sparse? If so, in what sense? If not, why? Deliberate on your answer.

## 9.13. Compare the SCAN algorithm (Section 9.5.3) with DBSCAN (Section 8.4.1). What are their similarities and differences?

## 9.14. Consider partitioning clustering and the following constraint on clusters: The number of objects in each cluster must be between \( \frac{n}{k}(1 - \delta) \) and \( \frac{n}{k}(1 + \delta) \), where \( n \) is the total number of objects in the data set, \( k \) is the number of clusters desired, and \( \delta \) in \( [0, 1) \) is a parameter. Can you extend the k-means method to handle this constraint? Discuss situations where the constraint is hard and soft.

## 9.9 Bibliographic notes

Höppner Klawonn, Kruse, and Runkler [HKKR99] provide a thorough discussion of fuzzy clustering. The fuzzy c-means algorithm (on which Example 9.7 is based) is proposed by Bezdek [Bez81]. Fraley and Raftery [FR02] give a comprehensive overview of model-based cluster analysis and probabilistic models. McLachlan and Basford [MB88] present a systematic introduction to mixture models and applications in cluster analysis.

Dempster, Laird, and Rubin [DLR77] are recognized as the first to introduce the EM algorithm and give it its name. However, the idea of the EM algorithm has been “proposed many times in special circumstances” before, as admitted in Dempster, Laird, and Rubin [DLR77]. Wu [Wu83] gives the correct analysis of the EM algorithm.

Mixture models and EM algorithms are used extensively in many data mining applications. Introductions to model-based clustering, mixture models, and EM algorithms can be found in recent textbooks on machine learning and statistical learning—for example, Bishop [Bis06a], Marsland [Mar09], and Alpaydin [Alp11].

The increase of dimensionality has severe effects on distance functions, as indicated by Beyer et al. [BGRS99]. It also has had a dramatic impact on various techniques for classification, clustering, and semisupervised learning (Radovanović, Nanopoulos, and Ivanović [RNI09]).

Kriegel, Kröger, and Zimek [KKZ09] present a comprehensive survey on methods for clustering high-dimensional data. Parsons, Haque, and Liu [PHL04] review subspace clustering for high-dimensional data. The CLIQUE algorithm is developed by Agrawal, Gehrke, Gunopulos, and Raghavan [AGGR98]. The PROCLUS algorithm is proposed by Aggarwal et al. [APW+99].

The technique of biclustering is initially proposed by Hartigan [Har72]. The term biclustering is coined by Mirkin [Mir98]. Cheng and Church [CC00] introduce biclustering into gene expression data analysis. There are many studies on biclustering models and methods. Madeira and Oliveira [MO04] and Tanay, Sharan, and Shamir [TSS04] present surveys on biclustering for biological data analysis. The notion of δ-p-Cluster is introduced by Wang, Wang, Yang, and Yu [WWYY02]. In this chapter, we introduce the δ-cluster algorithm by Cheng and Church [CC00] and MaPle by Pei et al. [PZC+03] as examples of optimization-based methods and enumeration methods for biclustering, respectively.

Dimensionality reduction is a topic involving many areas. For informative surveys, please see [CG15]. Nonnegative matrix factorization is developed by Paatero and Tapper [PT94] and Lee and Seung [LS99]. Donath and Hoffman [DH73] and Fiedler [Fie73] pioneer spectral clustering. In this chapter, we use an algorithm proposed by Ng, Jordan, and Weiss [NJW01] as an example. For a thorough tutorial on spectral clustering, see Luxburg [Lux07] and Filippone et al. [FCMR08].

Clustering graph and network data is an important and fast-growing topic. Schaeffer [Sch07], Nascimento and de Carvalho [Nd11], Aggarwal and Wang [AW10], and Malliaros and Vazirgiannis [MV13] provide several surveys. The SimRank measure of similarity is developed by Jeh and Widom [JW02]. PageRank and personalized PageRank are proposed by Page, Brin, Motwani, and Winograd [PBMW98]. Bahmani, Chowdhury, and Goel [BCG10] discuss fast incremental and personalized PageRank. Xu et al. [XYFS07] propose the SCAN algorithm. Arora, Rao, and Vazirani [ARV09] discuss the sparsest cuts and approximation algorithms. Stochastic block models are first proposed by Holland, Laskey, and Leinhardt [HLL83]. Rohe, Chatterjee, and Yu [RCY11] discuss spectral clustering and high-dimensional stochastic block models.

Semisupervised clustering has been extensively studied [BBM02,BBM04,GCB04,Bai13]. Constrained k-means is developed by Wagstaff, Cardie, Rogers, and Schrödl [WCRS01]. Basu, Banerjee, and Mooney [BBM02] develop seeded k-means. The COP-k-means algorithm is given by Wagstaff et al. [WCRS01]. Clustering with constraints has been extensively studied. Davidson, Wagstaff, and Basu [DWB06] propose the measures of informativeness and coherence. Zheng and Li [ZL11] propose a framework for semisupervised hierarchical clustering. Settles [Set10] presents a thorough review on active learning literature. Cohn, Caruana, and McCallum [CCM03] discuss interactive learning for semisupervised clustering.

This page intentionally left blank

## Deep learning 10

In this chapter, you will learn deep learning, a powerful family of techniques based on artificial neural networks with broad applications in computer vision, natural language processing, machine translation, social network analysis, and so on. It has been used in a variety of data mining tasks, including classification, clustering, outlier detection, and reinforcement learning. We start with the basic concepts (Section 10.1). Then, we introduce key algorithmic techniques for training an effective deep learning model (Section 10.2), and commonly used deep learning model architectures, including convolutional neural networks (Section 10.3), recurrent neural networks (Section 10.4), and graph neural networks (Section 10.5).

## 10.1 Basic concepts

### 10.1.1 What is deep learning?

Deep learning is based on artificial neural networks (ANNs) (or neural networks for short). Fig. 10.1 shows an illustrative example of neural network, and we will dive into details in a minute. Roughly speaking, a neural network is a set of connected input-output units in which each connection has a weight associated with it. During the learning phase, the network learns by adjusting the weights in order to predict the correct target values (e.g., class labels) of the input tuples.

A neural network is made up of interconnected units. So, what is a unit? Actually, we have already seen it! Recall that in Chapter 6, we introduced some basic classifiers, such as perceptron and logistic regression. Consider a data tuple X with n attributes: X = (X1, X2, ..., Xn). Both perceptron and logistic regression classifier first take a linear weighted sum of different attributes or features \sum_{i=1}^{n} X_i w_i + b, where w_i (i = 1, ..., n) are the weights and b is the bias scalar. Then, perceptron predicts the class label based on the sign of the linear weighted sum \hat{y} = sign(\sum_{i=1}^{n} X_i w_i + b), where sign(z) = 1 if z \ge 0 and sign(z) = 0 otherwise; logistic regression predicts the class posterior probability based on the sigmoid function of the linear weighted sum P(y = 1|X) = \sigma(\sum_{i=1}^{n} X_i w_i + b), where \sigma(z) = \frac{1}{1+exp(-z)} is the sigmoid function. In the neural network terminology, both perceptron and logistic regression can be viewed as a unit.

Formally, a unit is a mathematical function that (1) takes a linear weighted sum of the input, and then (2) passes the sum through an activation function f(\cdot). The activation function f(\cdot) is typically a nonlinear function, such as the sign function in perceptron and the sigmoid function \sigma(\cdot) in logistic regression. Many other choices for the activation function exist, and we will introduce some of them in Section 10.2. For the deep learning algorithms, it is convenient to introduce two additional notations. The first one is the net input I = \sum_{i=1}^{n} X_i w_i + b of the activation function. The second is the output of the unit O = f(I). A pictorial illustration of a unit is presented in Fig. 10.2.
