# 17.4 Strengths and weaknesses hierarchical clustering

While it often isn’t easy to tell which algorithms will perform well for a given task, here are some strengths and weaknesses that will help you decide whether hierarchical clustering will perform well for your task.

The strengths of hierarchical clustering are:

+   - It learns a hierarchy that may, in of itself be interesting and interpretable
+   - It is quite simple to implement

The weaknesses of hierarchical clustering are:

+   - It cannot natively handle categorical variables. This is because calculating the euclidean distance on a categorical feature space isn’t meaningful
+   - It cannot select the optimal number of "flat" clusters
+   - It is sensitive to data on different scales
+   - It cannot predict cluster membership of new data
+   - Once cases have been assigned to a cluster, they cannot be moved
+   - It can become computationally expensive with large datasets
+   - It is sensitive to outliers

# EXERCISE 17.3

Use the `clusterboot()` function to bootstrap the Jaccard index for k-means clustering (with four clusters), just like we did for hierarchical. This time, the `clustermethod` should be equal to `kmeansCBI` (to use k-means), and you should replace the `method` argument with `algorithm = "Lloyd"`. Which method results in more stable clusters, k-means or hierarchical clustering?

# EXERCISE 17.4

Use the `diana()` function from the `cluster` package to perform divisive hierarchical clustering on the GvHD data. Save the output as an object, and plot the dendrogram by passing it into `as.dendrogram() %>% plot()`. Compare this to the dendrogram we got from agglomerative hierarchical clustering. WARNING: This took nearly 15 minutes on my machine!

# EXERCISE 17.5

Repeat our bootstrapping experiment with agglomerative hierarchical clustering, but this time fix the number of clusters to four, and compare the different linkage methods on each bootstrap. Which linkage method performs the best?