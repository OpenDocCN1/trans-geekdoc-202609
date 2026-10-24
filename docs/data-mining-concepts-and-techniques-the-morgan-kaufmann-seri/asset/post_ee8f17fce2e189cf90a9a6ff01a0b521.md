
![](img/90c930779c8f928df6ff4481fc59f9a3_503_0.png)

## FIGURE 9.18

A graph and the similarity matrix showing the block/cluster structure. Source: adapted from Lee and Wilkinson Applied Network Science (2019) 4:122.

the cluster label agreement between neighbor vertices to identify clusters. Last, hybrid graphical models transform directed graphical models and undirected graphical models into a unified factor graph and detect clusters.

Let us use the well-known stochastic block model (SBM)-based methods as an example to illustrate the essential ideas. To understand the intuition, consider the graph G in Fig. 9.18(a), where there are three clusters. Fig. 9.18(b) shows the adjacency matrix, where the nodes are sorted according to the clusters to which they belong. A black dot in the adjacency matrix represents an edge connecting two vertices. As it shows, if we assign the nodes into clusters properly, then each cluster is a dense block in the adjacency matrix, since the nodes in a cluster are densely connected, whereas the edges crossing different clusters (i.e., blocks) are sparse. SBM tries to learn a generative model describing graph block structures from an observed graph, where a block corresponds to a cluster.

Let us describe the generation process of a graph G = (V, E), where V = {u1, ..., un} is the set of vertices, and E ⊆ V × V is the set of edges. Denote by A the adjacency matrix. Suppose we want to form K clusters in the graph. To model the assignments of vertices to clusters, for a vertex ui (1 ≤ i ≤ n), define a K-vector Zi, where all elements are 0 except the one that takes value 1 and represents the cluster to which ui belongs. For example, in Fig. 9.18(a), Z1 = [1 0 0]^T. Putting all Zi together, we have an n × K cluster membership matrix Z = [Z1 ... Zn]^T. To model the generation of edges, we define a K × K block matrix C, where Cij (1 ≤ i, j ≤ K) is the probability of occurrence of an edge between a vertex in cluster i and a vertex in cluster j. Clearly, Cii is the probability of occurrence of an edge within cluster i. Matrix C does not have to be symmetric. Indeed, an asymmetric block matrix can model directed edges between blocks.

SBM assumes that an edge that happens to two vertices \(u_i\) and \(u_j\) is conditionally independent given the cluster memberships \(\mathbf{Z}\). That is, \(\mathbf{A}_{ij}\) follows the Bernoulli distribution with success probability \(\mathbf{Z}_i^T \mathbf{C} \mathbf{Z}_j\) and is independent from \(\mathbf{A}_{i'j'}\) for \((i, j) \neq (i', j')\). This assumption is based on the concept of *stochastic equivalence*. Therefore the total number of edges between two blocks \(i\) and \(j\) is a random variable following the Binomial distribution with mean \(\mathbf{C}_{ij} \cdot b_i \cdot b_j\), where \(b_i\) and \(b_j\) are the number of vertices assigned to clusters \(i\) and \(j\), respectively.

Based on the above assumption, given a cluster memberships matrix \(\mathbf{Z}\) and a block matrix \(\mathbf{C}\), the likelihood of a graph adjacency matrix \(\mathbf{A}\) is given by

\(\pi(\mathbf{A}|\mathbf{Z}, \mathbf{C}) = \prod_{1 \le i < j \le n} \pi(\mathbf{A}_{ij}|\mathbf{Z}, \mathbf{C}) = \prod_{1 \le i < j \le n} [(\mathbf{Z}_i^T \mathbf{C} \mathbf{Z}_j)^{\mathbf{A}_{ij}} (1 - \mathbf{Z}_i^T \mathbf{C} \mathbf{Z}_j)^{1 - \mathbf{A}_{ij}}]. \quad (9.44)\)

If the graph is directed, we can simply replace the index in Eq. (9.44) from \(1 \le i < j \le n\) to \(1 \le i, j \le n, i \neq j\). Eq. (9.44) is also known as the *Bernoulli stochastic block model*.

To apply Eq. (9.44) to find clusters in a graph, we need to initialize \(\mathbf{Z}\) and \(\mathbf{C}\). Often, we assume that the assignments of different vertices into clusters are independent; that is, \(\mathbf{Z}_i\) and \(\mathbf{Z}_j\) are independent a priori. Moreover, by assuming a prior distribution of clusters \(\boldsymbol{\theta} = [\theta_1 \cdots \theta_K]^T\) such that \(\sum_{i=1}^K \theta_i = 1\), we have \(Pr(\mathbf{Z}_{ij}) = \theta_j\), that is, a vertex \(u_i\) is assigned to cluster \(j\) with probability \(\theta_j\). In other words, the cluster to which \(u_i\) is assigned follows the multinomial distribution with probabilities \(\boldsymbol{\theta}\) and thus

\(\pi(\mathbf{Z}|\boldsymbol{\theta}) = \prod_{i=1}^n \mathbf{Z}_i^T \boldsymbol{\theta} = \prod_{i=1}^n \boldsymbol{\theta}^T \mathbf{Z}_i = \prod_{i=1}^K \theta_i^{b_i}. \quad (9.45)\)

In the above SBM model, the adjacency matrix \(\mathbf{A}\) is the input, the block matrix \(\mathbf{C}\) and the cluster prior distribution \(\boldsymbol{\theta}\) are parameters, the cluster memberships matrix \(\mathbf{Z}\) is the result. To inference \(\mathbf{Z}\), we need to assign priors to \(\mathbf{C}\) and \(\boldsymbol{\theta}\) before we can conduct inference. We can assume that \(\mathbf{C}\) has an independent Beta prior, that is, \(\mathbf{C}_{ij} \sim \text{Beta}(\mathbf{P}_{ij}, \mathbf{Q}_{ij})\), where \(\mathbf{P}\) and \(\mathbf{Q}\) are \(K \times K\) matrices of all positive hyperparameters. We also assume that \(\boldsymbol{\theta}\) is from the Dirichlet(\(\alpha \mathbf{1}_K\)) distribution, where parameter \(\alpha\) is from a Gamma(\(a, b\)) prior. Then, the joint posterior of \(\mathbf{Z}\), \(\boldsymbol{\theta}\), \(\mathbf{C}\), and \(\alpha\) satisfy the following.

\(\pi(\mathbf{Z}, \boldsymbol{\theta}, \mathbf{C}, \alpha|\mathbf{A}) \propto \pi(\mathbf{A}, \mathbf{Z}, \boldsymbol{\theta}, \mathbf{C}, \alpha)\)
\(= \pi(\mathbf{A}|\mathbf{Z}, \boldsymbol{\theta}, \mathbf{C}, \alpha) \cdot \pi(\mathbf{Z}|\boldsymbol{\theta}, \mathbf{C}, \alpha) \cdot \pi(\boldsymbol{\theta}|\mathbf{C}, \alpha) \cdot \pi(\mathbf{C}|\alpha)\)
\(= \pi(\mathbf{A}|\mathbf{Z}, \mathbf{C}) \cdot \pi(\mathbf{Z}|\boldsymbol{\theta}) \cdot \pi(\boldsymbol{\theta}|\alpha) \cdot \pi(\alpha)\)
\(\propto \prod_{1 \le i < j \le n} [(\mathbf{Z}_i^T \mathbf{C} \mathbf{Z}_j)^{\mathbf{A}_{ij}} (1 - \mathbf{Z}_i^T \mathbf{C} \mathbf{Z}_j)^{1 - \mathbf{A}_{ij}}] \cdot \prod_{i=1}^n \mathbf{Z}_i^T \boldsymbol{\theta}\)
\(\cdot [\Gamma(K\alpha) \mathbf{1}\{\sum_{i=1}^K \theta_i = 1\} \prod_{i=1}^K \frac{\theta_i^{\alpha-1}}{\Gamma(\alpha)}]\)
\(\cdot \prod_{1 \le i \le j \le K} [\mathbf{C}_{ij}^{\mathbf{P}_{ij}-1} (1 - \mathbf{C}_{ij})^{\mathbf{Q}_{ij}-1}] \cdot \alpha^{a-1} e^{-b\alpha} \quad (9.46)\)

We can use a Markov chain Monte Carlo method to conduct inference according to Eq. (9.46).

There are many variants of stochastic block models that incorporate different constraints and background knowledge. Please refer to the bibliography section for the related references.

## 9.6 Semisupervised clustering

In the conventional setting of clustering analysis, the data objects to be clustered are not labeled. However, in some application scenarios, we may have some domain knowledge that may help us in clustering analysis. Let us consider an example.

### Example 9.20. Clustering with partially labeled data.

Imagine that you want to build a malware detector. You collect a large number of images of host systems. You and some of your colleagues label a small number of such images into two categories: malware and benign. However, there is no hope that all or even a fair portion of such images are labeled properly and timely. What should you make good use of the data?

An immediate idea is to use the labeled data to build a classifier. However, the proportion of labeled data is very small. A classifier built on such a small amount of data may not be effective and cannot use a large amount of unlabeled data. In other words, the vast majority of the data available cannot be used by a classification method.

The semisupervised clustering approaches address the clustering analysis scenarios where some domain knowledge is available. Those methods build on the clustering methods and incorporate different types of domain knowledge to strengthen the clustering results. In this section, we discuss different types of semisupervised clustering methods according to different types of domain knowledge available in addition to the unlabeled data.

### 9.6.1 Semisupervised clustering on partially labeled data

Example 9.20 illustrates the situation where a small portion of data to be clustered comes with labels. How can we make good use of the small amount of labeled data to strengthen an existing clustering method, such as k-means?

Let \(D = \{x_1, \dots, x_n\}\) be a set of objects to be clustered and \(K\) be the target number of clusters. In addition, let \(S_1, \dots, S_K \subset D\) be \(K\) exclusive subsets of labeled objects such that \(x_i \in S_j (1 \le i \le n, 1 \le j \le K)\) implies that object \(x_i\) is known to belong to cluster \(C_j\), and \(S_j \cap S_{j'} = \emptyset (1 \le j < j' \le K)\). Let \(S = \cup_{j=1}^K S_j\).

The constrained \(k\)-means method extends the classical \(k\)-means algorithm to make good use of the labeled data. The central idea is to use the labeled data to produce the initial means of the clusters. The constrained \(k\)-means algorithm works in the following steps.

- 1. For each cluster \(j (1 \le j \le K)\), compute the mean \(c_j\) of the labeled subset \(S_j\). That is, \(c_j = \frac{\sum_{x_i \in S_j} x_i}{|S_j|}\).

- 2. Assign all objects in \(D\) to clusters. For each object \(x_i \in D\), there are two cases. If \(x_i \in S\), then there exists a labeled subset \(S_j (1 \le j \le K)\) such that \(x_i \in S_j\). We assign \(x_i\) to cluster \(C_j\). If \(x_i \notin S\), then we assign \(x_i\) to the cluster \(C_j\) whose mean is closest to \(x_i\), that is, \(j = \arg \min_k \{dist(x_i, c_k)\}\).
