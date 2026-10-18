Let's also visualize the number and size of the clusters returned y each permutation.

Pass our swissClustersGathered object to ggplot() with the following aesthetic mappings:

+   • x = reorder(Permutation, Cluster)
+   • y = fill = as.factor(Cluster)

and add a geom_bar() layer. Now draw the same plot again, but this time add a coord_polar() layer. Change the x aesthetic mapping to just Permutation. Can you see what the reorder() function was doing?

So how are we going to choose the best-performing combination of epsilon and minPts? Well as we saw in the previous chapter, visually checking to make sure the clusters are sensible is important, but we can also calculate internal cluster metrics to help guide our choice.

In the previous chapter, we defined our own function that would take the data and the cluster membership from a clustering model, and calculate the Davies-Bouldin and Dunn indices, and the pseudo F-statistic. Let’s redefine this function to refresh our memory of it.



```
cluster_metrics <- function(data, clusters, dist_matrix) {
list(db = clusterSim::index.DB(data, clusters)$DB,
G1 = clusterSim::index.G1(data, clusters),
dunn = clValid::dunn(dist_matrix, clusters),
clusters = length(unique(clusters))
}
```

To help us select which of our clustering models best captures the structure in the data, we’re going to take bootstrap samples from our dataset, and run DBSCAN using all 81 combinations of epsilon and minPts, on each bootstrap sample. We can then calculate the mean of each of our performance metrics. and see how stable they are.



Recall from the previous chapter that a bootstrap sample is created by sampling cases from the original data, with replacement, to create a new sample the same size as the original.

Let’s start by generating 10 bootstrap sampels from our swissScaled dataset. I do this just like I did in the last chapter, using the sample_n() function and setting the replace argument equal to TRUE.