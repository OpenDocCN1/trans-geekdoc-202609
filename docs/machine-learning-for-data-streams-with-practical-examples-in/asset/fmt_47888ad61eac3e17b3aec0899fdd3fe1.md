
We start by discussing the evaluation problem in clustering and review the popular `k`-means method. We then discuss three incremental methods that are inspired more or less distantly by `k`-means: Birch, BICO, and CLUSTREAM. After that, we look at two density-based methods, starting with DBSCAN for nonstreaming data, which leads to Den-Stream for the streaming setting. Finally, we describe two more recent and state-of-the-art tree-based streaming methods, ClusTree and StreamKM++. We provide references and brief discussions of other methods in the closing section 9.7.

# 9.1 Evaluation Measures

Evaluating a clustering is unfortunately not as unambiguous as evaluating a classifier. There are many different measures of clustering quality described in the literature, maybe too many, which formalize different expectations of what a "good clustering" should achieve.

Measures can be categorized into two distinct groups: structural or internal measures, and ground-truth-based ones, called external measures. The first kind are strictly based on the data points and the clustering obtained. An extensive study of thirty internal measures can be found in [178], and other studies of external measures include [57, 231, 250]. Some examples are:

*   **Cohesion:** The average distance from a point in the dataset to its assigned cluster centroid. The smaller the better.
*   **SSQ:** The sum of squared distances from data points to their assigned centroids. Closely related to cohesion. The smaller the better.
*   **Separation:** Average distance from a point to the points assigned to other clusters. The larger the better.
*   **Silhouette coefficient:** Roughly speaking, the ratio between cohesion and the average distances from the points to their second-closest centroid. It rewards clusterings where points are very close to their assigned centroids and far from any other centroids, that is clusterings with good cohesion and good separation.

External measures, on the other hand, require knowledge of the "true" clustering of the data points, or ground truth, which by definition is almost always unknown in real scenarios. However, when evaluating new clusterers, one often creates synthetic datasets from a known generator, so it is possible to compare the clustering obtained by the algorithm with the true model. Some measures in these cases are similar to others applied in classification or information retrieval:

*   **Accuracy:** Fraction of the points assigned to their "correct" cluster.
*   **Recall:** Fraction of the points of a cluster that are in fact assigned to it.
*   **Precision:** Fraction of the points assigned to a cluster that truly belong to it.
*   **Purity:** In a maximally pure clustering, all points in the cluster belong to the same ground-truth class or cluster. Formally, purity is

![](images/pg151-in-1.png)(number of points in cluster `c` in the majority class for `c`):

*   **Cluster Mapping Measure (CMM):** A measure introduced by Kremer et al. [151], specifically designed for evolving data streams, which takes into account the fact that mergers and splits of clusters over time may create apparent errors.

The measures listed above can be easily maintained incrementally storing a constant number of values, if the centroids remain fixed. When the centroids evolve over time, we can resort to turning these values into EWMA accumulators or to evaluating on a sliding window.

# 9.2 The `k`-means Algorithm

The `k`-means (also called Lloyd's) algorithm is one of the most used methods in clustering, due to its simplicity. [Figure 9.1](#chapter_9.xhtml#fig9-1) shows its pseudocode.

![Figure 9.1 The k-means clustering algorithm, or Lloyd's algorithm.](images/Fig9-1.png)

[**Figure 9.1**](#chapter_9.xhtml#rfig9-1)

The `k`-means clustering algorithm, or Lloyd's algorithm.

The `k`-means assumes that the set of points `P` is a subset of ℜ^(`d`) for some dimension `d`, so that points can be added and averaged. The algorithm starts selecting `k` centroids in an unspecified way—for example, at random. After that, two steps are iterated: first, each instance is assigned to the nearest centroid; second, centroids are recomputed as the mean or center of mass of the examples assigned to it. The process typically stops when no point changes centroid, or after a maximum number of iterations has been performed. The `k` centroids produced determine the `k` clusters found by the algorithm.

The greedy heuristic implicit in `k`-means only guarantees convergence to a local minimum, and the quality of the solution found and the speed of convergence of `k`-means notoriously depend on the initial random assignment step. `k`-means++ [19] improves the stability of the method over the purely random one, using a new initialization step:

```
1        choose center c[1] to be p[1]
2        for i = 2,…,k
3              do select c[i] = p ∈ P with probability d(p,C)/cost(C,P).
```

In words, the initial center is selected at random, but all subsequent centers are selected with probability proportional to their distance to already selected centers. Spreading out the `k` initial cluster centers helps in that it leads to faster convergence to better local minima. The stream clustering method StreamKM++ also employs this strategy.

Converting `k`-means to the streaming setting is not straightforward, since it iterates repeatedly over the dataset. We will see that most stream clustering methods have two phases, one online and one offline. The online phase updates statistics of the data, producing some form of summary or sketch, usually represented as a reduced number of points called `microclusters`. The offline phase then uses these summaries to compute a final clustering efficiently, either at regular time intervals, or on demand.

# 9.3 BIRCH, BICO, and CLUSTREAM

These three algorithms are incremental and share a common idea for summarizing the stream in microclusters, in order to cluster them in the offline phase.

Balanced Iterative Reducing and Clustering using Hierarchies (BIRCH) is due to Zhang et al. [258]. It is the first method for incremental clustering that proposes to use so-called `clustering feature` (CF) vectors to represent microclusters. Assuming dataset points are vectors of `d` real numbers, a CF is a triple (`N, LS, SS`) composed of the following items:

*   `N`: number of data points in the CF
*   `LS`: `d`-dimensional sum of the `N` data points
*   `SS`: `d`-dimensional sum of squares of the `N` data points.

CFs have the following useful properties:

*   They are additive: `CF[1] + CF[2] = (N[1] + N[2], LS[1] + LS[2], SS[1] + SS[2])`.
*   The distance from a point to a cluster, the average intercluster distance, and the average intracluster distance are easy to compute from the CF.

Another feature of BIRCH is its use of `CF trees`, a height-balanced tree similar to the classical `B+` tree data structure. It is defined with two parameters: the branching factor `B`, or maximum number of children that any given node may have, and the leaf radius threshold `R`. The algorithm maintains the property that all points represented by a leaf fall in a ball of radius `R` of the centroid there. Every leaf and also every inner node contains a CF vector.

The BIRCH algorithm comprises up to four phases:

> Phase 1: Scan all data and build an initial in-memory CF tree
>
> Phase 2: Condense the CF tree into a smaller one (optional)
>
> Phase 3: Cluster globally
>
> Phase 4: Refine clusters (optional and offline, as it requires more passes).
