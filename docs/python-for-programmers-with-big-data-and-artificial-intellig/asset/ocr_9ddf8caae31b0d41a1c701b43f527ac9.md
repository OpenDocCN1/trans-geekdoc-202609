![](bbox=[0.126, 0.016, 0.946, 0.468])

# 14.7.4 Using a KMeans Estimator

In this section, we’ll use k-means clustering via scikit-learn’s KMeans estimator (from the sklearn.cluster module) to place each sample in the Iris dataset into a cluster. As with the other estimators you’ve used, the KMeans estimator hides from you the algorithm’s complex mathematical details, making it straightforward to use.

# Creating the Estimator

Let’s create the KMeans object:

lick here to view code image

```
In [22]: from sklearn.cluster import KMeans

In [23]: kmeans = KMeans(n_clusters=3, random_state=11)
```

The keyword argument n_clusters specifies the k-means clustering algorithm’s hyperparameter k, which KMeans requires to calculate the clusters and label each sample. When you train a KMeans estimator, the algorithm calculates for each cluster a centroid representing the cluster’s center data point.