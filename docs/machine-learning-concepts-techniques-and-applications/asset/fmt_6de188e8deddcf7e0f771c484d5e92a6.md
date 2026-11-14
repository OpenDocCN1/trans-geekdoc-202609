
`dist (C1,C2) = max {d(a,c),d(a,d),d(a,e),d(b,c),d(b,d),d(b,e)} = min {2,3,4,3,2,5} = 5`

*   **Average link**:

```latex
\begin{array}{ll} {\text{dist}\ \left( C1,C2 \right)} & {= \frac{d\left( a,c \right) + d\left( a,d \right) + d\left( a,e \right) + d\left( b,c \right) + d\left( b,d \right) + d\left( b,e \right)}{6}} \\ & {= \frac{2 + 3 + 4 + 3 + 2 + 5}{6} = \frac{19}{6} = 3.2} \\ \end{array}
```

## 9.8 Agglomerative Algorithm

The agglomerative algorithm is a type of hierarchical clustering algorithm that can be carried out in three steps:

1.  Convert object attributes to distance matrix.
2.  Set each object as a cluster (thus if we have `N` objects, we will have `N` clusters at the beginning).
3.  Repeat until number of cluster is one (or known number of clusters).
    *   Merge two closest clusters.
    *   Update distance matrix.

## 9.9 Issues Associated with Hierarchical Clustering

As we have already seen, the key operation associated with hierarchical clustering is repeatedly combining the two nearest clusters. As you merge clusters, how do you represent the “location” of each cluster to tell which pair of clusters is closest? One solution is the **Euclidean case** where each cluster is associated with a **centroid** which is the average of its data points.

However, in the non-Euclidean case, we define a **clusteroid** to represent a cluster of data points. The clusteroid is defined as the data point closest to other points. The concept of closeness can be defined in various ways, such as smallest maximum distance to other points, smallest average distance, or smallest sum of squares of distances to other points. The **centroid** is the average of all (data) points in the cluster. This means the centroid is an “artificial” point. However, the clusteroid is an existing (data) point that is “closest” to all other points in the cluster.

When we are dealing with Euclidean space, we generally measure cluster distances or nearness of clusters by determining the distances between centroids of the clusters. In the non-Euclidean case the defined clusteroids are treated as centroids to find inter-cluster distances.

Another issue is the stopping criteria for combining clusters. Normally we can stop when we have `k` clusters. Another approach is to stop when there is a sudden jump in the cohesion value or the cohesion value falls below a threshold.

## 9.10 Partitional Algorithm

In the previous section we discussed hierarchical clustering where new clusters are found iteratively using previously determined clusters. In this section, we will be discussing another type of clustering called partitional clustering where we discover all the clusters at the same time. The `k-means` algorithm, an example of partitional clustering, is a popular clustering algorithm. In partitional clustering, the data points are divided into a finite number of **partitions**, which are disjoint subsets of the set of data points, that is, each data point is assigned to exactly one subset. This type of clustering algorithm can be viewed as a problem of iteratively relocating data points between clusters until an optimal partition of the data points has been obtained.

In the basic algorithm the data points are partitioned into `k` clusters, and the partitioning criterion is optimized using methods such as minimizing the squared error. In the case of the basic iterative algorithm of `k-means` or `k-medoids`, both of which belong to the partitional clustering category, the convergence is local and the globally optimal solution is not always guaranteed. The number of data points in any data set is finite, and the number of distinct partitions is also finite. It is possible to tackle the problem of local minima by using exhaustive search methods.

## 9.11 `k-means` Clustering

As the case with any partitional algorithm, basically the `k-means` algorithm is an iterative algorithm which divides the given data set into `k` disjoint groups. As already discussed, `k-means` is the most widely used clustering technique. This partitional method uses prototypes for representing the cluster. The `k-means` algorithm is a heuristic method where the centroid of the cluster represents the cluster and the algorithm converges when the centroids of the clusters do not change. Some of the common applications of `k-means` clustering are data mining, optical character recognition, biometrics, diagnostic systems, military applications, document clustering, and so on.

### 9.11.1 Steps of `k-means`

Initialize `k` values of centroids.

The following two steps are repeated until the data points do not change partitions and there is no change in the centroid.

*   Partition the data points according to the current centroids. The similarity between each data point and each centroid is determined, and the data points are moved to the partition to which it is most similar.
*   The new centroid of the data points in each partition is then calculated.

Initially the cluster centroids are chosen at random as we are talking about an unsupervised learning technique where we are not provided with the labelled samples. Even after the first round using these randomly chosen centroids, the complete set of data points is partitioned all at once. After the next round, the centroids have moved since the data points have been used to calculate the new centroids. The process is repeated, and the centroids are relocated until convergence occurs when no data point changes partitions.

`Figure 9.11a` shows the random selection of the initial centroids as `centroid 1 = (1,1)` for `cluster 1` and `centroid 2 = (2,1)` for `cluster 2`. We illustrate with `data point B` and calculate the distance of `C` with each of the randomly selected centroids (also sometimes called as seed points). We find that `C` is closer to `centroid 2`, and we assign `B` to that cluster. Now `Figure 9.11b` shows the assignment of each data point to one of the clusters. In our example only one data point is assigned to `cluster 1`, so its centroid does not change. However, `cluster 2` has three data points associated with it, and the new centroid `c[2]` now becomes `(3, 3.33)`. Now we compute the new assignments as shown in `Figure 9.11c`. `Figure 9.11c` shows the new values of `centroid 1` and `centroid 2`. `Figure 9.11c` shows the results after convergence.

![Figure 9.11 The iterations for the example in Figure 9.10.](images/fig9_11a_B.jpg)

`Figure 9.11 The iterations for the example in` `Figure 9.10`.

### 9.11.2 Issues Associated with the `k-means` Algorithm

Though `k-means` is considered as an important clustering algorithm, we will now discuss certain issues associated with this algorithm. The first question we need to address is to choose the correct value of `k`, that is, how many partitions we should have. One way of selecting `k` is to first try different values of `k` where the average of distances to the centroid changes rapidly until the right value of `k` when the changes are slow. Another issue associated with `k-means` clustering is the initial choice of the `k-centroids`. We have explained that these initial centroids can be chosen at random, but this may not lead to fast convergence. Therefore, this initial cluster problem needs to be addressed. One method is to use hierarchical clustering to determine the initial centroids. Another approach is to first select more than `k` initial centroids and then select among these initial centroids which are the most widely separated. Another method is carrying out preprocessing where we can normalize the data and eliminate outliers.
