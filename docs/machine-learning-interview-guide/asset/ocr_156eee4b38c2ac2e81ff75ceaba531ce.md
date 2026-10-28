Answer: DBSCAN primary objective is to partition a set of data points into areas called clusters that have high densities and differentiate between noisy points and clusters with different shapes and sizes. DBSCAN can find clusters of any shape and have no assumption of the shape and density of the clusters as most of the clustering algorithms have. This is done in a way that clusters the highly similar data points together while at the same time putting apart the dissimilar data points known as noise or outliers. In other words, the goal of DBSCAN is to cluster data in such a way that outcomes dense regions surrounded by sparse boundaries, making the method rather adaptive and stable.

# Question 2: How does DBSCAN differ from other clustering algorithms like k-means?

Answer: DBSCAN differs from k-means and other clustering algorithms in the following key ways:

+   - Cluster shape: DBSCAN does not require a specific number of clusters and can even delineate clusters that are of any shape, while k-means always presume that the clusters are spherical and of equal variance. DBSCAN is more versatile and performs better on clusters with a complex shape.
+   
+   - Number of clusters: DBSCAN does not pre-empt that the number of clusters should be determined, such as the case with k-means; it just requires density to be defined. This algorithm can independently decide the number of clusters to form by using the density of the dataset and the distance restriction set by the user.
+   
+   - Handling noise: DBSCAN also marks noise points as outlying data, while all the points are categorized into clusters.