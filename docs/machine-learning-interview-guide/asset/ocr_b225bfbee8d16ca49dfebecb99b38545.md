of data.

In conclusion, although k-means and hierarchies are applied for clustering analysis, they are distinct in grouping method, conceptualization of the cluster structure, selection of the number of the clusters, and the computation load. The approach used should be utilized when a clear clustering pattern is present in the data, although the decision between spectral clustering and the other three methods depends on the specific characteristics of the dataset, the desired clustering result, and considerations of computational complexity.

# Question 8: How can we determine the optimal number of clusters (K) in k-means?

**Answer**: Determining the optimal number of clusters (K) in k-means can be done using the following methods:

+   - **Elbow method**: Draw the within-cluster sum of squares also known as **inertia** against different values of *K* and then find out the value of *K* at which inertia starts to decrease at a slower rate. More precisely, the curve of the within-cluster sum of squares is drawn against different numbers of clusters, and the point in the graph where the rate of decrease of the within-cluster sum of squares is slowest is known as the **elbow point**.
+   - **Silhouette score**: Compute the silhouette for various values of *K*, and the silhouette score gives the difference between clustering coefficient of each object and the smallest clustering coefficient of objects in different clusters. In the preceding equations, choose the value of *K* that decides the silhouette score to be maximum.
+   - **Gap statistics**: Coupled with the given within-cluster sum of squares of the k-means clustering, compare it