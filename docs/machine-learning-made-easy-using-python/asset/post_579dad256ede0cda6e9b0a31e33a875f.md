
## SUPPORT VECTOR MACHINES

In [5]: Z = SvcModel.predict(X_plot)
z = Z.reshape(xx.shape)
plt.figure(figsize=(15, 5))
plt.subplot(121)
plt.contour(xx, yy, Z, alpha=0.3)
plt.scatter(X[:, 0], X[:, 1], c=y)
plt.xlim(xx.min(), xx.max())

Out[5]: (3.3, 8.88272727272751)

![](img/d75fea3635f5553f1cb0585b39b1b4b_171.png)

Similarly we can create SVC using the Radial Basis Function kernel.

```
In [10]: RbfSvc = svm.Svc(kernel='rbf', C=1.0).fit(X, y)
Z = RbfSvc.predict(X_plot)
z = Z.reshape(xx.shape)
plt.figure(figsize=(15, 5))
plt.subplot(121)
plt.contour(xx, yy, Z, alpha=0.3)
plt.scatter(X[:, 0], X[:, 1], c=y)
plt.xlim(xx.min(), xx.max())
```

You can observe both of the plots using the linear and rbf and notice a clear difference in lines and curves

```
Out[10]: (3.3, 8.88272727272751)
```

![](img/d75fea3635f5553f1cb0585b39b1b4b_172.png)

## CLUSTERING ALGORITHM

- K-Means
- Mean shift
- Hierarchical

![](img/d75fea3635f5553f1cb0585b39b1b4b_173.png)

## CLUSTERING

Clustering is a case of unsupervised machine learning. The clustering algorithms learn relations in the data and classifies it into groups according to number of groups provided or not.

![](img/d75fea3635f5553f1cb0585b39b1b4b_174.png)

The findings are the different types of clustering:

- Density-based: clusters are formed as dense regions. These algorithms have good accuracy and capability to merge two clusters together. Density-Based Spatial Clustering of Applications with Noise (DBSCAN), Ordering Points to identify Clustering (OPTICS).
- Hierarchical-based: clusters are formed in a hierarchical tree which has Agglomerative (Bottom up approach) and Divisive (Top down approach). Clustering using Representatives (CURE), Balanced iterative Clustering using Hierarchies (BIRCH).
- Partitioning: clusters are formed by partitioning the objects into k, number of clusters will be equal to partitions. K-Means
- Grid: clusters are formed as grid. This method is fast and independent on the number of objects. Statistical Information Grid (STING), Clustering CLIQUE

Until now we have calculated the accuracy of supervised learning with the predicted values and actual values, how can we do so for unsupervised learning when we are dealing with unlabeled data?

There are some metrics that can be used to evaluate the performance or quality of different unsupervised learning algorithms by the changes in clusters. Silhouette analysis used to check the quality of clustering model by measuring the distance between the clusters. It basically provides us a way to assess parameters like number of clusters with the help of Silhouette score.

The silhouette score ranges from -1 to 1. The different numbers represent the following:

- 1 is the situation when the cluster is far away from its neighbouring cluster.
- 0 is the situation when the cluster is very close or on the decision boundary itself i.e separating the clusters.
- -1 is the situation when cluster aren't formed correctly.

the silhouette score can be calculated using the following formula:

Silhouette Score = p - q / max(p, q)

with p is the mean distance to the points in the nearest cluster and q is the mean intra-cluster distance to all the points.

Next we can use the Davis-Bouldin Index to know whether the clusters are well spaced from each other or not and the density of the clusters. We can calculate the DB index using the following formula:

![](img/d75fea3635f5553f1cb0585b39b1b4b_175.png)

## CLUSTERING

$DB = \frac{1}{n} \max_{j\neq i} \left(\frac{\sigma_i + \sigma_j}{d(c_i, c_j)}\right)$

$n$ is the number of clusters, $\sigma^i$ is the average distance of all points in cluster $i$ from the cluster centroid $c_i$.

Lower values indicate good performance, where $\theta$ is the minimum value.

Dunn index is another metric that can be used to evaluate the performance of a clustering algorithm. It is similar to the DB index but the difference are:

- It considers only the clusters close together whereas DB index considers all of the clusters.
- Lower Dunn indexes indicates bad performance whereas lower the DB index higher the performance of the algorithm.

The Dunn index can be calculated using the following formula:

$D = \frac{\min_{i \neq j} P(i,j)}{\max_{k} q(k)}$

$i,j,n$ are indices for clusters, $P$ is the inter-cluster distance and $q$ is the intra-cluster distance.

The Dunn index increases with the performance of the clustering algorithm.

We can evaluate the performance of different clustering algorithm (not accuracy of one algorithm) with the following metrics:

- Silhouette Score
- Davis-Boulden Index
- Dunn Index

Let’s see the clustering in action. We use the make_blobs() function.

```python
from sklearn.cluster import KMeans
from sklearn.datasets import make_blobs
from matplotlib import pyplot
```

dt, y = make_blobs(n_samples=240, centers=4, std=0.6)

```python
kmeans = KMeans(n_clusters=4)
kmeans.fit(dt)
pred = kmeans.predict(dt)
centers = kmeans.cluster_centers_
```

```python
plt.figure(figsize=(15, 5))
plt.subplot(121)
plt.scatter(dt[:,0], dt[:,1], c=pred, s=30)
plt.plot(centers[:,0], centers[:,1], c='x', s=100)
plt.show()
```

```python
plt.figure(figsize=(15, 5))
plt.subplot(121)
plt.contour(xx, yy, Z, alpha=0.3)
plt.scatter(X[:, 0], X[:, 1], c=y)
plt.xlim(xx.min(), xx.max())
```

```python
pred = kmeans.predict(dt)
centers = kmeans.cluster_centers_
```

```python
plt.scatter(dt[:,0], dt[:,1], c=pred, s=30)
plt.plot(centers[:,0], centers[:,1], c='x', s=100)
```

## K-Means Algorithm

We already know there are different types of clustering and K-Means algorithm is one of those. The number of clusters is specified by K. In our case it created 4 clusters with 60 datapoints each.

The process of dividing these clusters is totally random. The algorithm computes the centroids for each cluster formed.

## Mean-Shift Algorithm

The Mean-Shift algorithm assigns datapoints to clusters iteratively by shifting points towards the highest density of datapoints. The number of clusters is evaluated by the algorithm upon receiving the data and analyzing it.
