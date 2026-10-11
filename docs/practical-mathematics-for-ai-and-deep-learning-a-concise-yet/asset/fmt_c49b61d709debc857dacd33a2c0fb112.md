
## 代码示例：计算样本点间的距离

```text
4. mhl_dist_sqr_smp1 = mahalanobis_dist_sqr(cluster_mean, cluster_smp, clust_cov_inv)
5. eucl_dist_sqr_smp1 = euclidean_dist_sqr(cluster_mean, cluster_smp)
6. # cluster mean vs cluster outlier
7. mhl_dist_sqr_smp2 = mahalanobis_dist_sqr(cluster_mean, outlier_smp, clust_cov_inv)
8. eucl_dist_sqr_smp2 = euclidean_dist_sqr(cluster_mean, outlier_smp)
```

**Code 7.3:** *Measuring distances between two sample points*

The preceding code would output the following information. *[Table 7.2](#c07.xhtml#tab7_2)* contains the square of distances of samples from the mean:

| *With respect to* `cluster_mean` | *Mahalanobis distance square* | *Euclidean distance square* |
| --- | --- | --- |
| `cluster_smp` | 1.04 | 214.9 |
| `outlier_smp` | 3.14 | 122.5 |

**Table 7.2:** *Mahalanobis and Euclidean distance of two samples from the cluster mean*

Euclidean distance was not able to find the outlier with respect to cluster distribution. In fact, Euclidean value indicates that the outlier sample is nearer to the cluster mean than the cluster sample. On the other hand, Mahalanobis distance is clearly indicating that outlier sample is far as compared to the cluster sample. These samples are captured in *[Figure 7.3](#c07.xhtml#fig7_3)*:

![](images/Image44650.jpg)

**Figure 7.3:** *Plotting of data samples with special markers on cluster’s mean, a data sample in cluster and outlier*

# Cluster quality

Challenges to evaluate these unsupervised clustering algorithms are different as compared to supervised algorithms. Clustering algorithms are used to extract natural patterns from the unlabeled data. As these patterns are not known before, algorithms would extract patterns based on the approach or heuristics. Most times, we cannot decide whether the extracted patterns are right or wrong.

Evaluation of clustering algorithms can be categorized into internal and external. *Internal evaluation* is based on the assumption that data samples belonging to one cluster should be more similar as compared to data samples belonging to different clusters. External evaluation is performed on the labeled data set. This labeled data set is not seen by the algorithms. Most times, these kinds of labeled datasets are created by humans who are experts in the problem domain we are solving. These are also called *benchmarks*. The process of evaluating algorithms using standard labeled dataset is called *external evaluation*.

# Internal evaluation

Internal evaluation techniques assign higher score to algorithms that produces clusters with high similarity within a cluster and low similarity between clusters. However, we should keep in mind that these indicators don’t imply that the algorithms produce valid/invalid results.

For example: Consider that an indicator assumes natural clusters are convex in shape then this indicator would score high for algorithms that work on similar heuristics. Definitely, this indicator will score low for algorithms that do not assume convex patterns in the data.

# Davies-Bouldin indicator

Let there be *n* clusters denoted as ![](images/2093.jpg). Let us use centroid to represent a cluster (group of similar data samples) with a single vector. *Centroid of a cluster* is defined as arithmetic mean of all samples belonging to the cluster. Let the centroid of these clusters be denoted as ![](images/2094.jpg). Let ![](images/2095.jpg) denote the average distance of all data samples belonging to cluster, and let ![](images/2096.jpg) denote the average distance of all data samples belonging to cluster ![](images/2097.jpg). Let the distance metric between two centroids be denoted as ![](images/2098.jpg). Distance function can be any one of the distance metrics. *Davies-Bouldin indicator* is defined as follows:

![](images/2099.jpg)

# Dunn indicator

Dunn indicator helps us in identifying the algorithm that extracts dense and well-separated clusters. It is calculated as the ratio between minimum inter-cluster distance and the maximum intra-cluster distance. It is defined as follows:

![](images/2100.jpg)

Where ![](images/2101.jpg) measures the distance between cluster ![](images/2102.jpg) and ![](images/2103.jpg) and ![](images/2104.jpg) measures intra-cluster distance of cluster ![](images/2105.jpg). Choice of these distance functions can vary based on the problem domain. Algorithms produce clusters with high Dunn indicator value is preferred.

# Silhouette coefficient

Silhouette coefficient measure of each data sample depends on how similar the data sample is to its assigned cluster, called *cohesion*, and how dissimilar the data sample is compared to data samples belonging to other clusters, called *separation*. Cohesion and separation with respect to one data sample is shown in *[Figure 7.4](#c07.xhtml#fig7_4)*:

![](images/Image44659.jpg)

**Figure 7.4:** ***(left)*** *cohesion: with in the cluster* ***(right)*** *separation: outside the cluster*

Consider a data sample ![](images/2106.jpg) belonging to the ![](images/2107.jpg) cluster ![](images/2108.jpg). ![](images/2109.jpg) represents the count of data samples assigned to the cluster ![](images/2110.jpg). Then, similarity or cohesion of the data point ![](images/2111.jpg) with respect to the other data samples of the same cluster is defined as follows:

![](images/2112.jpg)

Value ![](images/2113.jpg) signifies how well it is assigned to the cluster ![](images/2114.jpg); a smaller value indicates better assignment. Dissimilarity or separation of the data sample ![](images/2115.jpg) with respect to the samples of the other clusters ![](images/2116.jpg), where ![](images/2117.jpg) is defined as follows:

![](images/2118.jpg)

Value ![](images/2119.jpg) signifies the smallest mean distance/dissimilarity of the point ![](images/2120.jpg) to all other points in any other cluster ![](images/2121.jpg). Cluster the smallest mean dissimilarity with data sample ![](images/2122.jpg) is called the neighbor cluster for the data sample.

Using the terms of similarity and dissimilarity, silhouette value is defined as follows:

![](images/2123.jpg)

Silhouette value ranges \[–1, 1\]. A higher value indicates that the data sample is well matched to the cluster it is assigned to and more dissimilar to a neighbor cluster. A higher value is preferrable for the data sample. A larger percentage of data samples having high silhouette value is preferred. This evaluation indicator can be used with any distance metric. Using the silhouette value of all *N* data samples, we can define **Silhouette Coefficient** (**SC**) as follows:

![](images/2124.jpg)

Plotting *silhouette coefficient* of data samples will help us in deciding the right number of clusters. The right number of clusters occur when the SC score of all data samples is near to the overall average SC score. For more information, refer to the link stated in *References \[2\]*.

# External evaluation

External evaluation of the algorithms is performed on standard labeled data set. As the data set is labeled, we can identify whether the test samples are correctly clustered. After the application of any algorithm on test data, which is already labeled (ground truth), we have clusters containing this labeled data. Clusters formed by the selected algorithm may be different from the ground truth. Evaluation of the selected algorithm will be performed by comparing the clusters formed by the algorithm and the ground truth (labeled test data). Consider one cluster out of all clusters produced by the selected algorithm, and then we define the following terms:

*   **True Positive - TP**: Data samples that belong to the cluster ![](images/2125.jpg) and are correctly assigned to the cluster ![](images/2126.jpg).
*   **True Negative - TN**: Data samples that belong to another cluster are rightly not assigned to ![](images/2127.jpg).
