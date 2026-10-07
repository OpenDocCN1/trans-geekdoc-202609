Training the hierarchical clustering: As we know the optimal number of clusters, we can now train our model.

```
from sklearn.cluster import AgglomerativeClustering
hrcl_cluster_genrt = AgglomerativeClustering(n_clusters=5, affinity='euclidean', linkage='ward')
y_hrcl = hrcl_cluster_genrt.fit_predict(X)
```

In the code above, we have imported the AgglomerativeClustering class of cluster module of scikit learn library.

Then we created the object of this class as hrcl_cluster_genrt. The AgglomerativeClustering class takes the following parameters:

+   * n_clusters=5: It defines the number of clusters, and we have taken 5 because it is the optimal number of clusters.
* affinity='euclidean': It is a metric to compute the linkage
* linkage='ward': It defines the linkage criteria, we have used the ward linkage. This method is the popular linkage method that we have already used for creating the Dendrogram. It reduces the variance in each cluster.

In the last line, we created the dependent variable y_hrcl to fit or train the model we used fit-means clustering. It does not train only the model but also returns the clusters to which each data point belongs.

After executing the lines of code, if we use the variable explorer in our Spyder IDE, we can check the y_pred (in our case y_hrcl). We can compare the original dataset with the y_pred array. Consider the following image:

![](bbox=[0.147, 0.431, 0.852, 0.715])

As we can see in the figure, the y_pred shows the clusters value, which means the customer id1 belongs to the 5th cluster (indexing starts from 0, 4 means 5th cluster, the customer id2 belongs to 4th cluster, and so on).

Visualizing the Clusters: We will use the same lines of code as we did in k-means clustering, except we will not plot the centroid that we did in k-means, because we use dendrogram to determine the optimal number of clusters. The code is given below:

Notice there is no centroid here.

```
# plotting the cluster
plt.scatter(X_hrcl[:, 0], X_hrcl[:, 0], s=100, c='red', label='cluster 1')
plt.scatter(X_hrcl[:, 1], X_hrcl[:, 1], s=100, c='blue', label='cluster 2')
plt.scatter(X_hrcl[:, 2], X_hrcl[:, 2], s=100, c='green', label='cluster 3')
plt.scatter(X_hrcl[:, 3], X_hrcl[:, 3], s=100, c='cyan', label='cluster 4')
```