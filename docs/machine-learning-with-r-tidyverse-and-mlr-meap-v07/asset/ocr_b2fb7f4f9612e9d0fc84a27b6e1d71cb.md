![](bbox=[0.629, 0.115, 0.925, 0.28])

# Clustering based on the distribution of data: mixture model clustering

+   **This chapter covers:**
+   
+   - What is mixture model clustering and why is it useful?
+   - What’s the difference between hard and soft clustering?

Our final stop in unsupervised learning techniques brings us to an additional approach to finding clusters in data: mixture model clustering. Just like the other clustering algorithms we’ve covered, mixture model clustering aims to partition a dataset into a finite set of clusters.

In the last chapter, I showed you how the DBSCAN and OPTICS algorithms, and how they find clusters by learning regions of high and low density in the feature space. Mixture model clustering takes, yet another approach to identifying clusters. A mixture model is any model that describes a dataset by combining a mix of two or more probability distributions. In the context of clustering, mixture models help us to identify clusters by fitting a finite number of probability distributions to the data, and iteratively modifying the parameters of those distributions until they best fit the underlying data. Cases are then assigned to the cluster of the distribution under which they are most likely. The most common form of mixture modeling is *Gaussian mixture modeling*, which fits Gaussian (or normal) distributions to the data.

By the end of this chapter, I hope you’ll have a firm understanding of how mixture model clustering works and its differences and similarities to some of the algorithms we’ve already covered. We’ll apply this method to our Swiss banknote data from the last chapter to help you understand how mixture model clustering differs from density-based clustering. If you no longer have the swissTib object defined in your global environment, just re-run code listing 18.1.