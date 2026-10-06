In this function, the data are divided into increasing numbers of clusters and the Within Sum of Squares (wss) is computed—this being a measure of the variability within each cluster. It decreases greatly up about five clusters, after which it levels off and no much improvement is seen. This indicates that the data contains about five clusters.

In step 3, we perform a k-means clustering using the kmeans () function, providing main_components as the data for the max argument and setting the number of clusters to five. The values of nstart and iter.max arguments are reasonable options for most runs of the algorithm. We pass the kmeans_clust result object to fviz_cluster () and set some display options options. You should see something like Figure 11:12:

# k-Means Sample Clustering

![](bbox=[0.118, 0.313, 0.842, 0.545])

That's all we intended to do in this recipe!