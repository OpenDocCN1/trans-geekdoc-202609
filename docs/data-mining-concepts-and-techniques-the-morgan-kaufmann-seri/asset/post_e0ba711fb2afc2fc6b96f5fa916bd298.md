
**Table 8.1 A set of objects, the clustering ground truth, and two clusterings.**

| Object | a | b | c | d | e | f | g | h | i | j | k |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Ground truth \(\mathcal{G}\) | \(G_1\) | \(G_1\) | \(G_1\) | \(G_1\) | \(G_1\) | \(G_1\) | \(G_2\) | \(G_2\) | \(G_2\) | \(G_2\) | \(G_3\) |
| Clustering \(C_1\) | \(C_1\) | \(C_1\) | \(C_1\) | \(C_1\) | \(C_2\) | \(C_2\) | \(C_3\) | \(C_3\) | \(C_3\) | \(C_3\) | \(C_4\) |
| Clustering \(C_2\) | \(C_1\) | \(C_1\) | \(C_2\) | \(C_2\) | \(C_2\) | \(C_3\) | \(C_1\) | \(C_2\) | \(C_2\) | \(C_1\) | \(C_3\) |

## Information theory–based methods

A clustering assigns objects to clusters and thus can be regarded as a compression of the information carried by the objects. In other words, a clustering can be regarded as a compressed representation of a given set of objects. Therefore we can use information theory to compare a clustering and the ground truth as representations. This is the general idea behind the information theory–based methods.

For example, we can measure the amount of information needed to describe the ground truth given the distribution of a clustering output by a method. Better the clustering results approach the ground truth, less amount information is needed. This leads to a natural approach using conditional entropy. Concretely, according to information theory, the entropy of a clustering \(\mathcal{C}\) is

\(H(\mathcal{C}) = -\sum_{i=1}^m \frac{|C_i|}{n} \log \frac{|C_i|}{n},\)

and the entropy of the ground truth is

\(H(\mathcal{G}) = -\sum_{i=1}^l \frac{|G_i|}{n} \log \frac{|G_i|}{n}.\)

The conditional entropy of \(\mathcal{G}\) given cluster \(C_i\) is

\(H(\mathcal{G}|C_i) = -\sum_{j=1}^l \frac{|C_i \cap G_j|}{|C_i|} \log \frac{|C_i \cap G_j|}{|C_i|}.\)

The conditional entropy of \(\mathcal{G}\) given clustering \(\mathcal{C}\) is

\(H(\mathcal{G}|\mathcal{C}) = \sum_{i=1}^m \frac{|C_i|}{n} H(\mathcal{G}|C_i) = -\sum_{i=1}^m \sum_{j=1}^l \frac{|C_i \cap G_j|}{n} \log \frac{|C_i \cap G_j|}{|C_i|}.\)

In addition to the simple conditional entropy, more sophisticated information theory–based measures may be used, such as normalized mutual information and variation of information.

Taking the case in Table 8.1 as an example, we can calculate

\(H(\mathcal{G}|C_1) = -(\frac{4}{11} \log \frac{4}{4} + \frac{2}{11} \log \frac{2}{2} + \frac{4}{11} \log \frac{4}{4} + \frac{1}{11} \log \frac{1}{1}) = 0\)

and

\( H(\mathcal{G}|\mathcal{C}_2) = -(\frac{2}{11} \log \frac{2}{4} + \frac{2}{11} \log \frac{2}{4} + \frac{2}{11} \log \frac{3}{5} + \frac{3}{11} \log \frac{3}{5} + \frac{2}{11} \log \frac{2}{11} + \frac{1}{11} \log \frac{1}{2}) \)
\( = 0.297 \).

Clustering \(\mathcal{C}_1\) has better quality than \(\mathcal{C}_2\) in terms of conditional entropy. Again, although \( H(\mathcal{G}|\mathcal{C}_1) = 0 \), conditional entropy cannot detect the issue that \(\mathcal{C}_1\) splits the objects in \( G_1 \) into two clusters.

## Pairwise comparison-based methods

The pairwise comparison-based methods treat each group in the ground truth as a class. For each pair of objects \( o_i, o_j \in D (1 \le i, j \le n, i \neq j) \), if they are assigned to the same cluster/group, the assignment is regarded as positive, and otherwise, negative. Then, depending on assignments of \( o_i \) and \( o_j \) into clusters \( C(o_i), C(o_j), G(o_i), \) and \( G(o_j) \), we have four possible cases.

| | \( C(o_i) = C(o_j) \) | \( C(o_i) \neq C(o_j) \) |
|---|---|---|
| \( G(o_i) = G(o_j) \) | true positive | false negative |
| \( G(o_i) \neq G(o_j) \) | false positive | true negative |

Using the statistics on pairwise comparison, we can assess the quality of the clustering results approaching the ground truth. For example, we can use the Jaccard coefficient, which is defined as

\( J = \frac{\text{true positive}}{\text{true positive + false negative + false positive}} \).

Many other measures can be built based on the pairwise comparison statistics, such as Rand statistic, Fowlkes-Mallows measure, BCubed precision, and recall. The pairwise comparison results can be further used to conduct correlation analysis. For example, we can form a binary matrix \( G \) according to the ground truth, where element \( v_{ij} = 1 \) if \( G(o_i) = G(o_j) \), and otherwise 0. A binary matrix \( C \) can also be constructed in a similar way based on a clustering \( C \). We can analyze the element-wise correlation between the two matrixes and use the correlation to measure the quality of the clustering results. Clearly, the more correlated the two matrixes, the better the clustering results.

## 8.5.4 Intrinsic methods

When the ground truth of a data set is not available, we have to use an intrinsic method to assess the clustering quality. Unable to reference any external supervision information, the intrinsic methods have to come back to the fundamental intuition in clustering analysis, that is, examining how compact clusters are and how well clusters are separated. Many intrinsic methods take the advantage of a similarity or distance measure between objects in the data set.

For example, the **Dunn index** measures the compactness of clusters by the maximum distance between two points that belong to the same cluster, that is, \( \Delta = \max_{C(o_i)=C(o_j)} \{ d(o_i, o_j) \} \). It measures the degree of separation among different clusters by the minimum distance between two points that belong to different clusters, that is \( \delta = \min_{C(o_i) \neq C(o_j)} \{ d(o_i, o_j) \} \). Then, the Dunn index is simply the ratio \( DI = \frac{\delta}{\Delta} \). The larger the ratio, the farther away the clusters are separated comparing to the compactness of the clusters.

The Dunn index uses the extreme distances to measure the cluster compactness and intercluster separation. The measures \(\delta\) and \(\Delta\) may be affected by the outliers. Many methods consider the average situations. The **silhouette coefficient** is such a measure. For a data set, \(D\), of \(n\) objects, suppose \(D\) is partitioned into \(k\) clusters, \(C_1, ..., C_k\). For each object \(o \in D\), we calculate \(a(o)\) as the average distance between \(o\) and all other objects in the cluster to which \(o\) belongs. Similarly, \(b(o)\) is the minimum average distance from \(o\) to all clusters to which \(o\) does not belong. Formally, suppose \(o \in C_i (1 \le i \le k)\). Then,

\(a(o) = \frac{\sum_{o' \in C_i, o \neq o'} dist(o, o')}{|C_i| - 1}\)

and

\(b(o) = \min_{C_j: 1 \le j \le k, j \neq i} \left\{ \frac{\sum_{o' \in C_j} dist(o, o')}{|C_j|} \right\}\)

The **silhouette coefficient** of \(o\) is then defined as

\(s(o) = \frac{b(o) - a(o)}{\max\{a(o), b(o)\}}\)

The value of the silhouette coefficient is between \(-1\) and \(1\). The value of \(a(o)\) reflects the compactness of the cluster to which \(o\) belongs. The smaller the value, the more compact the cluster. The value of \(b(o)\) captures the degree to which \(o\) is separated from other clusters. The larger \(b(o)\) is, the more separated \(o\) is from other clusters. Therefore when the silhouette coefficient value of \(o\) approaches \(1\), the cluster containing \(o\) is compact and \(o\) is far away from other clusters, which is the preferable case. However, when the silhouette coefficient value is negative (i.e., \(b(o) < a(o)\)), this means that, in expectation, \(o\) is closer to the objects in another cluster than to the objects in the same cluster as \(o\). In many cases, this is a bad situation and should be avoided.

To measure a cluster's fitness within a clustering, we can compute the average silhouette coefficient value of all objects in the cluster. To measure the quality of a clustering, we can use the average silhouette coefficient value of all objects in the data set. The silhouette coefficient and other intrinsic measures can also be used in the elbow method to heuristically derive the number of clusters in a data set by replacing the sum of within-cluster variances.

## 8.6 Summary

- A **cluster** is a collection of data objects that are _similar_ to one another within the same cluster and are _dissimilar_ to the objects in other clusters. The process of grouping a set of physical or abstract objects into classes of _similar_ objects is called **clustering**.

- Cluster analysis has extensive **applications**, including business intelligence, image pattern recognition, Web search, biology, and security. Cluster analysis can be used as a standalone data mining tool to gain insight into the data distribution or as a preprocessing step for other data mining algorithms operating on the detected clusters.

- Clustering is a dynamic field of research in data mining. It is related to **unsupervised learning** in machine learning.
