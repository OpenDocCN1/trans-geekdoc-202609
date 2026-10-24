
## Active and interactive learning for semisupervised clustering

Background knowledge like must-link and cannot-link constraints is helpful for semisupervised clustering. However, a user may have difficulty in specifying must-link and cannot-link constraints on a large set of objects to be clustered. To tackle this challenge, active and interactive learning for semisupervised clustering is explored.

Active learning can be conducted to obtain important must-link and cannot-link constraints. For example, one idea is to get at least one object from each cluster with a small number of requests to users for providing pairwise relationship information. One possible approach is to pick an object that is farthest from all the other points and another object in an existing cluster and ask a user to judge whether a must-link constraint should be put on those two objects. If so, then the farthest point is assigned to the cluster. If not, a new cluster is created for the farthest point. This process continues until we have enough initial clusters.

User feedback can be accommodated not only at the beginning of the clustering, but can be taken interactively during the whole iterative clustering process. For example, a user can interactively provide feedback about the quality of clusters in the intermediate results. The types of feedback may include (1) an object is put in a wrong cluster; (2) an object should be moved to a more appropriate cluster; (3) two objects should be put in the same cluster (similar to a must-link constraint); and (4) two objects should be put in different clusters (similar to a cannot-link constraint). A clustering algorithm can take the feedback and update the clusters by either directly adjusting the cluster assignment or adjusting the similarity measure and rerunning the clustering process.

## 9.7 Summary

- In conventional cluster analysis, an object is assigned to one cluster exclusively. However, in some applications, there is a need to assign an object to one or more clusters in a fuzzy or probabilistic way. **Fuzzy clustering** and **probabilistic model-based clustering** allow an object to belong to one or more clusters. A **partition matrix** records the membership degree of objects belonging to clusters.

- **Probabilistic model-based clustering** assumes that a cluster is a parameterized distribution. Using the data to be clustered as the observed samples, we can estimate the parameters of the clusters.

- A **mixture model** assumes that a set of observed objects is a mixture of instances from multiple probabilistic clusters. Conceptually, each observed object is generated independently by first choosing a probabilistic cluster according to the probabilities of the clusters, and then choosing a sample according to the probability density function of the chosen cluster.

- An **expectation-maximization algorithm** is a framework for approaching maximum likelihood or maximum a posteriori estimates of parameters in statistical models. Expectation-maximization algorithms can be used to compute fuzzy clustering and probabilistic model-based clustering.

- **High-dimensional data** poses grand challenges for cluster analysis, including how to model high-dimensional clusters and how to search for such clusters. The **curse of dimensionality** is mainly caused by many **irrelevant or correlated attributes**, **data sparsity**, **distance concentration effect of similarity measures**, and **difficulty in optimization**.

- There are two different kinds of subspaces that clustering methods may target at, namely **axis-parallel subspaces** and **arbitrarily-oriented subspaces**. There are two major categories of clustering methods for high-dimensional data: **clustering methods** and **dimensionality reduction methods**. Clustering methods search for clusters in subspaces of the original space and can be further categorized into subspace clustering methods, projected clustering methods, and biclustering methods. Dimensionality reduction methods create a new space of lower dimensionality and search for clusters there.

- Biclustering methods cluster objects and attributes simultaneously. Types of biclusters include biclusters with constant values, constant values on rows/columns, coherent values, and coherent evolutions on rows/columns. Two major types of biclustering methods are optimization-based methods and enumeration methods.

- Dimensionality reduction transforms a high-dimensional data set into a low-dimensional space so that the low-dimensional representation retains meaningful properties of the original data, ideally approaching the intrinsic dimensions of the underlying structures.

- There are many dimensionality reduction methods. Principal component analysis (PCA) is frequently used to identify the most meaningful basis to re-express a data set. Nonnegative matrix factorization (NMF) decomposes a data set X ≈ HW, where the entries in H and W are nonnegative. H and W represent how objects are assigned to clusters and the “centers” of clusters, respectively. Spectral clustering constructs new dimensions using an affinity matrix.

- Clustering graph and network data have many applications, such as social network analysis and web search. The major challenges include how to measure the similarity between objects in a graph and how to design clustering models and methods for graph and network data.

- Geodesic distance is the number of edges between two vertices on a graph. It can be used to measure similarity. Alternatively, similarity in graphs, such as social networks, can be measured using structural context and random walk. SimRank is a similarity measure that is based on both structural context and random walk. Some other similarity measures for graphs include personalized PageRank and topical PageRank.

- Graph clustering can be modeled as computing graph cuts. A sparsest cut may lead to a good clustering, whereas modularity can be used to measure the clustering quality. Computing graph cuts on large graphs faces several challenges, including high computational cost, sophisticated graphs, high dimensionality, and sparsity.

- The generic graph clustering methods extract a similarity matrix from a graph using a similarity measure and then apply a generic clustering method on the similarity matrix to discover clusters. SCAN is a graph clustering algorithm that searches graph structures to identify well-connected components as clusters. Probabilistic graphical model-based methods regard a graph as a set of observations generated by a probabilistic model and use some heuristics on community generation to find clusters as communities in a graph. The stochastic block model (SBM) is an example.

- Semisupervised clustering uses domain knowledge to improve clustering results. The domain knowledge may take the form of partially labeled data, pairwise constraints on objects, and some other types. Some classical clustering algorithms can be extended to accommodate those constraints.

## 9.8 Exercises

- 9.1. Traditional clustering methods are rigid in that they require each object to belong exclusively to only one cluster. Explain why this is a special case of fuzzy clustering. You may use k-means as an example.

- **9.2.** An e-commerce company carries 1000 products, $P_1, ..., P_{1000}$. Consider customers Ada, Bob, and Cathy such that Ada and Bob purchase three products in common, $P_1, P_2$, and $P_3$. For the other 997 products, Ada and Bob independently purchase seven of them randomly. Cathy purchases 10 products, randomly selected from the 1000 products. In Euclidean distance, what is the probability that $dist(\text{Ada, Bob}) > dist(\text{Ada, Cathy})$? What if Jaccard similarity (Chapter 2) is used? What can we learn from this example?

- **9.3.** Can you show that the $k$-medoids method can also be implemented in the EM algorithm framework?

- **9.4.** In the EM algorithm for mixture models, if for all univariate Gaussian distributions $\Theta_j (1 \le j \le k)$, $\sigma_j = \sigma$, that is, all have the standard deviation. Can you simplify the calculation in the E-step and the M-step accordingly?

- **9.5.** Show that $I \times J$ is a bicluster with coherent values if and only if, for any $i_1, i_2 \in I$ and $j_1, j_2 \in J$, $e_{i_1 j_1} - e_{i_2 j_1} = e_{i_1 j_2} - e_{i_2 j_2}$.

- **9.6.** In soft projected clustering method LAC, explain how the weights and the clusters can be computed using the EM algorithm.

- **9.7.** Compare the MaPle algorithm (Section 9.3) with the frequent closed itemset mining algorithm, CLOSET (Pei, Han, and Mao [PHM00]). What are the major similarities and differences?

- **9.8.** Given 20 data points in 2-D space whose first principal component is $u = (\frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}})'$.
  - a. Suppose we add one more data point at $(2, 2)'$; how would that affect the first principal component?
  - b. Suppose we add one more data point at $(3, 0)'$; how would that affect the first principal component?
  - c. Suppose we add an *infinite* number of data points at $(5, 0)'$; how would that affect the first principal component?

- **9.9.** Given $n$ data tuples in $d$-dimensional space, we can represent them as an $n \times d$ matrix $X$, where the rows of $X$ are for different data tuples and columns are for different features. NMF introduced in Section 9.4.2 performs matrix low-rank approximation with the constraint that both low-rank matrices must be nonnegative. In this exercise, we will learn that $k$-Means clustering can also be viewed as a special form of matrix low-rank approximation. Based on that, we will compare the similarity and difference between these two clustering methods.
  - a. Prove that K-Means clustering can be viewed as a special form of matrix low-rank approximation. That is, the optimization objective of K-Means is equivalent to
    $$\{W^*, H^*\} = \text{argmin}_{W,H} \|X - HW\|_{fro}^2,$$ (9.47)
    where $\|.\|_{fro}$ is the matrix Frobenius norm, $H$ and $W$ are two low-rank matrices with appropriate constraints. In particular, what is the size constraint on $H$ and $W$, respectively? What are additional constraints we need to impose on $H$ and/or $W$, so that Eq. (9.47) is equivalent to the optimization objective of K-Means?
  - b. Based on the above analysis, what are the commonalities between NMF and K-Means? What are the difference between them?

- **9.10.** In this exercise, we will learn about the mathematical details underlying many spectral clustering methods (Section 9.4.3). Given an $n \times n$ similarity matrix $W$ whose elements are the similarities between the corresponding data tuples (i.e., $W(i, j)$ measures the similarity between tuples $i$ and
