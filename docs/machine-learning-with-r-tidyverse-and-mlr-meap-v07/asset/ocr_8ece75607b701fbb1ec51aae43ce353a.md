# Clustering by finding hierarchies:  
hierarchical clustering

![](bbox=[0.628, 0.115, 0.947, 0.281])

# This chapter covers:

+   - What is hierarchical clustering and why would we use it?
+   - What linkage methods are and how they affect the hierarchy
+   - How can we measure the stability of a clustering result?

In the previous chapter, we saw how k-means clustering finds k-centroids in the feature space and iteratively updates them to find a set of clusters. Hierarchical clustering takes a different approach and, as its name suggests, can learn a hierarchy of clusters in a dataset. Instead of getting a "flat" output of clusters, hierarchical clustering gives us a tree of clusters within clusters. As a result, hierarchical clustering gives us more insight into complex grouping structures than flat clustering methods like k-means.

The tree of clusters is built iteratively by calculating the distance between each case or cluster, and every other case or cluster in the dataset at each step. Either the case/cluster pair that are most similar to each other are merged into a single cluster, or sets of cases/clusters that are most dissimilar from each other are split into separate clusters, depending on the algorithm. I’ll introduce both approaches to you later in the chapter.

By the end of this chapter, I hope you’ll understand how hierarchical clustering works. We’ll apply this method to our GvHD data from the last chapter to help you understand how hierarchical clustering differs to k-means. If you no longer have the gvhdScaled object defined in your global environment, just re-run code listings 16.1 and 16.4.