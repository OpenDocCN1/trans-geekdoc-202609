Usually, tree-based, Classification machine learning algorithms like Decision Trees, Random Forest, Gradient Boosting, etc. are made use of to attain constraint-based clustering. A tree is constructed by splitting without the interference of the constraints or clustering labels. Then, the leaf nodes of the tree are combined together to form the clusters while incorporating the constraints and using suitable algorithms.

# 4.1.3 Types of Clustering Algorithms

Clustering algorithms are used in exploring data, anomaly detection, finding outliers, or detecting patterns in the data. Clustering is an unsupervised learning technique like neural network and reinforcement learning. The available data is highly unstructured, heterogeneous, and contains noise. So the choice of algorithm depends upon how the data looks like. A suitable clustering algorithm helps in finding valuable insights for the industry. Let’s explore the different types of clustering in machine learning in detail.

+   - K-Means clustering
+   - Mini batch K-Means clustering algorithm
+   - Mean Shift
+   - Divisive Hierarchical Clustering
+   - Hierarchical Agglomerative clustering
+   - Gaussian Mixture Model
+   - DBSCAN
+   - OPTICS
+   - BIRCH Algorithm

# 1. K-Means Clustering

K-Means is a partition-based clustering technique that uses the distance between the Euclidean distances between the points as a criterion for cluster formation. Assuming there are ‘n’ numbers of data objects, K-Means groups them into a predetermined ‘k’ number of clusters.

Each cluster has a cluster center allocated and each of them is placed at farther distances. Every incoming data point gets placed in the cluster with the closest cluster center. This process is repeated until all the data points get assigned to any cluster. Once all the data points are covered the cluster centers or centroids are recalculated. After having these ‘k’ new centroids, a new grouping is done between the nearest new centroid and the same data set points. Iteratively, there may be a change