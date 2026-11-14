
[Figure 9.3 Confusion matrix.](#ch9.xhtml#R_fig9_3)

In [Figure 9.3](#ch9.xhtml#fig9_3) `a` corresponds to the number of attributes with the value of 0 for both data points `x[i]` and `x[j]`, `b` corresponds to 0 for `x[i]` and 1 for `x[j]`, `c` corresponds to 1 for `x[i]` and 0 for `x[j]`, while `d` corresponds to the number of attributes with the value of 1 for both data points `x[i]` and `x[j]`.

The confusion matrix can be used if both states (0 and 1) have equal importance and carry the same weights. Then the distance function is the proportion of mismatches of their value (Equation 9.1):

(9.1)
```
dist(x[i], x[j]) = (b + c) / (a + b + c + d)
```

However, sometimes the binary attributes are asymmetric where one of the states is more important than the other. We assume that state 1 represents the important state, in which case the Jaccard measure using the confusion matrix can be defined as follows (Equation 9.2):

(9.2)
```
JDist(x[i], x[j]) = (b + c) / (a + b + c)
```

For text documents, normally we use cosine similarity, which is a similarity measure, not a distance measure. Cosine similarity is a measure of similarity between two vectors obtained by measuring the cosine of the angle between them ([Figure 9.4](#ch9.xhtml#fig9_4)). The similarity between any two given documents `d[j]` and `d[k]`, represented as vectors is given as (Equation 9.3):

(9.3)
$$
{sim}\left( d_{j},d_{k} \right) = \frac{{\overline{d}}_{j} \cdot {\overline{d}}_{k}}{\mid {\overline{d}}_{j} \mid \mid {\overline{d}}_{k} \mid} = \frac{\sum_{i = 1}^{n}w_{i,j}w_{i,k}}{\sqrt{\sum_{i = 1}^{n}w_{i,j}^{2}}\sqrt{\sum_{i = 1}^{n}w_{i,k}^{2}}}
$$

![Figure 9.4 The cosine angle between vectors.](images/fig9_4_B.jpg)

[Figure 9.4 The cosine angle between vectors.](#ch9.xhtml#R_fig9_4)

In this case `w[i]` is a weight probably based on the frequency of words in the documents.

The result of the cosine function is equal to 1 when the angle is 0, and it is less than 1 when the angle is of any other value. As the angle between the vectors decreases, the cosine value approaches 1, that is, the two vectors are closer, and the similarity between the documents increases.

## 9.7 Methods of Clustering

The basic method of clustering is the hierarchical method, which is of two types, agglomerative and divisive. Agglomerative clustering is a bottom-up method where initially we assume that each data point is by itself a cluster. Then we repeatedly combine the two nearest clusters into one. On the other hand, divisive clustering is a top-down procedure where we start with one cluster and recursively split the clusters until no more division is possible. We normally carry out point assignment where we maintain a set of clusters and allocate points to the nearest cluster.

### 9.7.1 Hierarchical Clustering

In the hierarchical clustering approach, we carry out partitioning of the data set in a sequential manner. The approach creates partitions one layer at a time by grouping objects into a tree of clusters ([Figure 9.5](#ch9.xhtml#fig9_5)). In this context there is no need to know the number of clusters in advance. In general, the distance matrix is used as the clustering criteria.

![Figure 9.5 Hierarchical clustering.](images/fig9_5_B.jpg)

[Figure 9.5 Hierarchical clustering.](#ch9.xhtml#R_fig9_5)

### 9.7.2 Types of Hierarchical Clustering

Hierarchical clustering methods can be further classified as either agglomerative or divisive, depending on whether the hierarchical decomposition is formed in a bottom-up (merging) or top-down (splitting) fashion. As we have discussed, the hierarchical approach sequentially partitions the data points and constructs a tree of clusters. The following are two sequential clustering strategies for constructing the tree of clusters. The important issues in both cases are cluster distance to be considered and the termination condition to be used.

#### 9.7.2.1 Agglomerative Clustering

In agglomerative clustering initially each data point forms its own (atomic) cluster and hence follows the bottom-up strategy. We then merge these atomic clusters into larger and larger clusters based on some distance metric. The algorithm terminates when all the data points are in a single cluster, or merging is continued until certain termination conditions are satisfied. Most hierarchical clustering methods belong to this category. Agglomerative clustering on the data set `{a, b, c, d, e}` is shown in [Figure 9.6](#ch9.xhtml#fig9_6).

![Figure 9.6 Agglomerative and divisive hierarchical clustering.](images/fig9_6_B.jpg)

[Figure 9.6 Agglomerative and divisive hierarchical clustering.](#ch9.xhtml#R_fig9_6)

#### 9.7.2.2 Divisive Clustering

Divisive clustering is a top-down strategy which does the reverse of agglomerative hierarchical clustering, where initially all data points together form a single cluster. It subdivides the clusters into smaller and smaller pieces until it satisfies certain termination conditions, such as a desired number of clusters or the diameter of each cluster is within a certain threshold ([Figure 9.6](#ch9.xhtml#fig9_6)).

### 9.7.3 Hierarchical Clustering: The Algorithm

Hierarchical clustering takes as input a set of points. It then creates a tree or dendogram in which the points are leaves and the internal nodes club similar points together. The method initially places all points in separate clusters. Then as long as there is more than one cluster, the closest pair of clusters is merged.

#### 9.7.3.1 Hierarchical Clustering: Merging Clusters

Now an important criterion for merging clusters is the cluster distance. There are three different ways in which this cluster distance can be defined.

| Cluster Distance Measures | Pictorial Representation |
| --- | --- |
| **Single link**: Distance between two clusters is the distance between the closest points in the clusters ([Figure 9.7a](#ch9.xhtml#fig9_7a)) for single link. This method is also called neighbor joining. The cluster distance `d(C[i], C[j])` between the clusters `C[i]` and `C[j]` in the case of single link is given as the minimum distance between the data points `x[ip]` and `x[jq]` in the two clusters (Equation 9.4). (9.4) `d(C[i], C[j]) = min{d(x[ip], x[jq])}` | ![Figure 9.7a](images/fig9_7a_B.jpg) [Figure 9.7a](#ch9.xhtml#R_fig9_7a) |
| **Average link**: Distance between two clusters is the distance between the cluster centroids ([Figure 9.7b](#ch9.xhtml#fig9_7b)) for average link. The cluster distance `d(C[i], C[j])` between the clusters `C[i]` and `C[j]` in the case of single link is given as the average distance between the data points `x[ip]` and `x[jq]` in the two clusters (Equation 9.5). (9.5) `d(C[i], C[j]) = avg{d(x[ip], x[jq])}` | ![Figure 9.7b](images/fig9_7b_B.jpg) [Figure 9.7b](#ch9.xhtml#R_fig9_7b) |
| **Complete link**: Distance between two clusters is the distance between the farthest pair of points ([Figure 9.7c](#ch9.xhtml#fig9_7c)) for complete link. The cluster distance `d(C[i], C[j])` between the clusters `C[i]` and `C[j]` in the case of single link is given as minimum distance between the data points `x[ip]` and `x[jq]` in the two clusters (Equation 9.6). (9.6) `d(C[i], C[j]) = max{d(x[ip], x[jq])}` | ![Figure 9.7c](images/fig9_7c_B.jpg) [Figure 9.7c](#ch9.xhtml#R_fig9_7c) |

*   **Single link**:
```
dist(C1, C2) = min{d(a, c), d(a, d), d(a, e), d(b, c), d(b, d), d(b, e)} = min{2, 3, 4, 3, 2, 5} = 2
```
*   **Complete link**:
