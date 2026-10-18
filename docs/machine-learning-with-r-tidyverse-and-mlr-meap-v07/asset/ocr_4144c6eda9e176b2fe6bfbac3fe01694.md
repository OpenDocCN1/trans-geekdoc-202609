# ## 18.1 What is density-based clustering?

In this section, I’ll show you how two of the most commonly used density-based clustering algorithms work:

+   - Density-based spatial clustering of applications with noise (DBSCAN)
+   - Ordering points to identify the clustering structure (OPTICS)

Aside from having names seemingly contrived to form interesting acronyms, DBSCAN and OPTICS both learn regions of high density, separated by regions of low density in a dataset. They achieve this in similar, but slightly different ways, but both have a few advantages over k-means and hierarchical clustering:

+   - they are not biased to finding spherical clusters, and can in fact find clusters of varying and complex shapes
+   - they are not biased to finding clusters of equal diameter, and can identify both very wide and very tight clusters in the same dataset
+   - they are seemingly unique among clustering algorithms in that cases that do not fall within regions of high enough density are put into a separate "noise" cluster. This is often a desirable property, because it helps to prevent overfitting the data, and allows us to focus on cases for which the evidence of cluster membership is stronger

> **TIP**
> 
> If the separation of cases into a noise cluster isn’t desirable for your application (but using DBSCAN or OPTICS is), you can use a heuristic method like classifying noise points based on their nearest cluster centroid, or adding them to the cluster of their k-nearest neighbors.

All three of these advantages can be seen in figure 18.1. The three subplots each show the same data, clustered using either DBSCAN, k-means (Hartigan-Wong algorithm), or hierarchical clustering (complete linkage). This dataset is certainly strange, and you might think it’s unlikely to encounter real-world data like it, but it illustrates the advantages of density-based clustering over k-means and hierarchical clustering. The clusters in the data have very different shapes (that certainly aren’t spherical) and diameters. While k-means and hierarchical clustering learn clusters which bisect and merge these real clusters, DBSCAN is able to faithfully find each shape as a distinct cluster. Additionally, notice that k-means and hierarchical clustering place every single case into a cluster? DBSCAN creates the cluster "0" into which it places any cases it considers to be noise. In this case, all cases outside of those geometrically-shaped clusters are placed into the noise cluster. If you look carefully though, you may notice there is a sine wave in the data that all three fail to identify as a cluster.