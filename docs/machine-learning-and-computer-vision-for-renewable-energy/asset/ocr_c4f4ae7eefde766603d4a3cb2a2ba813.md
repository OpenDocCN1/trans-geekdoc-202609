# A Deep Learning Framework for Modeling Temporal Dependencies

Figure 9. Gaussian copula visualization of hierarchies

![](bbox=[0.172, 0.165, 0.868, 0.705])

subset. This allows for faster convergence, especially when dealing with large datasets. On the other hand, Fuzzy C-Means (FCM) allow data points to belong to multiple clusters with varying degrees of membership. Fuzzy C-Means assigns each data point a membership value for each cluster, indicating the degree to which the point belongs to each cluster. This approach is more flexible than traditional k-means, especially when cluster assignments are ambiguous.

We discovered that two clusters is the ideal number after applying the elbow approach and Silhouette to determine the ideal number of clusters. Refer to the appendix’s Figures 11 and 12. Table 5 presents the results of the three clustering techniques. It is evident that, in the case of k-means clustering, the Davies-Bouldin Index is given as 0.5011 (low), implying strong cluster separation, and the Silhouette