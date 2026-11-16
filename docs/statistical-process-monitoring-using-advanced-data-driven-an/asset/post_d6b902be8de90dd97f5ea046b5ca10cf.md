
other clusters. Clustering algorithms have been largely exploited in data analysis. Conventional clustering techniques can be classified into different categories of clustering algorithms including partition-based, density-based and hierarchy-based clustering. In this section, we briefly present the basic idea of common clustering.

## 6.2.1 Partition-based clustering techniques

The essence of the clustering techniques based on the partition concept consists of considering the center of data as the center of the correspondent cluster. The two commonly used partition-based clustering techniques are k-means [15] and k-medoids [16]. Generally speaking, in the k-means algorithm, the center of the cluster is updated iteratively in such a way that a selected criterion for convergence is met. To handle discrete data, k-medoids has been developed as an enhancement of k-means. Various partition-based clustering algorithms have been developed, including partitioning around medoids (PAM) [17], clustering for large applications (CLARA) [17], and clustering large applications based on randomized search (CLARANS) [18]. More details about partition-based clustering can be found in [19–21].

### 6.2.1.1 k-Means clustering

The k-means procedure is an iterative, data-partitioning algorithm that aims to attribute n observations to one cluster of the k clusters characterized by centroids [22]. The number of clusters k is a priori selected in such a way that every cluster has its own centroid. Each observation is attributed to the cluster with the closest centroid, and each cluster updates its own centroid according to new included observations. The assignments and updates are repeated until stabilization of structure where no centroid updates are possible (Fig. 6.1). The principal steps of the algorithm are as follows:

- 1. Take k observations randomly as centroids (cluster centers)
- 2. Attribute each observation to the nearest cluster by computing its distance to each centroid
- 3. Find a new cluster center by computing the average of the observations including the assigned points
- 4. Iterate steps 2 and 3 until the assignment of clusters is not changing any more

![](img/aa2f42c739937b682075082233e335bb_205_0.png)

FIGURE 6.1 Conceptual illustration of the k-means clustering.

In summary, the main appeal of the partition-based clustering methods is their high computational efficacy with moderate time-complexity. However, they are not suited for nonconvex data, sensitive to outliers, and easily fall into local optimum. In addition, in such methods, the number of clusters should be specified a priori defined, and the obtained results are highly sensitive to the number of clusters.

## 6.2.2 Hierarchy-based clustering techniques

As discussed above, the aim of clustering techniques as unsupervised learning techniques is to group a set of observations into distinguished subsets. Hierarchy-based clustering is one of the frequently used clustering techniques. The key concept of this type of clustering is based on the construction of the hierarchical relationships among data to cluster it [23]. At first, we assume that each of the observed data points represents a single cluster, we then merge the closest clusters in a new cluster until only one cluster is left. There are several existing hierarchy-based clustering procedures in the literature, such as balanced iterative reducing and clustering using hierarchies (BIRCH) [24,25], CURE [26], ROCK [27], and Chameleon [28]. Essentially, hierarchy-based clustering methods have the advantage of handling datasets having arbitrary shape and attributes of arbitrary type. In addition, the hierarchical relationship between clusters can easily be identified. However, the disadvantage of using hierarchy-based clustering is its high cost and the fact that the number of clusters should be a priori defined. For more details about hierarchy-based clustering methods, refer to [29–31].

### 6.2.2.1 BIRCH (hierarchical)

BIRCH is a hierarchy-based clustering procedure introduced to deal with streaming data or large datasets [25]. Basically, BIRCH clusters the data by building the clustering feature tree (CF tree), in which a subcluster is represented by one node. Specifically, the CF is a triple that summarizes the maintained information on a cluster. In fact, the CF tree will dynamically rise when a new observation arrives, and this incrementally improves the quality of subclusters. However, to obtain a good clustering performance, BIRCH needs the cluster count as input. More details about BIRCH algorithm can be found in [24,25].

The following describes the main steps in implementing the BIRCH clustering approach:

- 1. Construct a CF tree structure after a scan of the whole training data
- 2. Optimize the initial CF tree and create a compressed version of it
- 3. Perform global clustering by applying an existing clustering procedure on the leaves of the CF tree
- 4. Refine and improve the clustering quality with an additional full scan

### 6.2.2.2 Agglomerative clustering

Hierarchical clustering procedures generate a nested sequence of clusters that can be visualized as a hierarchical tree [32]. The agglomerative hierarchical scheme is a nonparametric clustering that does not require the number of the clusters as input. The essence of this scheme is to merge clusters that are similar. The procedure is repeated until the intended number of clusters is achieved or the distance between the two closest clusters exceeds a certain threshold distance (see Fig. 6.2). The basic procedure of agglomerative clustering is outlined as follows:

![](img/aa2f42c739937b682075082233e335bb_207_0.png)

FIGURE 6.2 Illustrative example of agglomerative clustering (dendrogram).

- Consider each data point as a cluster and compute the proximity matrix
- Compute similarity/dissimilarity between each pair of data points
- Based on linkage function, group data points into a hierarchical cluster tree
- Combine closer clusters and update the proximity matrix

## 6.2.3 Density-based approach

The essence of the density-based clustering is to consider the data in a zone with a high density of the data points to be in the same cluster [33]. Thus, clustering procedures based on density possess the ability to uncover clusters with arbitrary shape and have the advantage of making less assumptions about the data without needing the number of clusters to be provided a priori. There are several clustering procedures in the literature designed using the density-based concept, such as DBSCAN [34], OPTICS [35], and mean-shift [36,37]. For further details on density-based clustering, we refer to [33,37,38]. The key benefit of this type of clustering is the greater capability to cluster data points with arbitrary shape. But, this approach achieves low clustering efficiency in the case when the density of data space isn’t uniform. Its additional disadvantage is that it requires big memory when the volume of the data is large, and the clustering outcome is largely sensitive to the parameters.

Mean shift clustering is one of the commonly used density-based clustering procedures that will be briefly introduced next.

![](img/aa2f42c739937b682075082233e335bb_208_0.png)

### 6.2.3.1 Mean shift clustering

Mean shift clustering is a nonparametric recursive hierarchy-based method. It is designed based on the concept of kernel density estimation (KDE). This scheme does not need a prefixed number of clusters. Essentially, the modes of a density estimate are used as indicators for the densest regions of the data, and these modes could be suitable cluster center estimates. The main idea of mean shift clustering is to shift all points belonging to the same region to the mean or the center of the area, and to repeat this task till convergence (Fig. 6.3). In KDE, the mean shift clustering is performed via a simple gradient procedure to estimate the modes of the KDE. There are different kernels to use in the mean shift clustering procedure, including Gaussian, exponential, Tophat, and Epanechnikov. Essentially, in the mean shift clustering, the kernel bandwidth plays a significant role in the clustering result. Indeed, if a large bandwidth is selected, then fewer clusters will be formed in the mean shift clustering, and vice versa. Accordingly, the bandwidth selection is a crucial step in the mean shift clustering procedure because it has a direct impact on the quality of the density estimation, and thus heavily impacts mean shift clustering. Specifically, selecting a poor bandwidth estimate leads to modes that do not appropriately represent the dense regions of the data. Various schemes have been designed to address the problem of bandwidth selection [36,39,40]. For more information about mean shift procedure, we refer to [37,38].

The main steps needed for implementing mean shift clustering are the following:

- 1. Define a window (i.e., bandwidth of the kernel) and place it on a data point
- 2. Calculate the mean of all observations within the window
- 3. Move the center of the window to the position of the mean
- 4. Iterate steps 2 and 3 until convergence
