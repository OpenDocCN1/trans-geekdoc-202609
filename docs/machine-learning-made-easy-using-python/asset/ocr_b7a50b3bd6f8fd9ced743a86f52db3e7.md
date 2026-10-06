# K-Means Algorithm

We already know there are different types of clustering algorithms and K-Means algorithm is one of those. K-means clustering algorithm computes the centroids and iterates until it finds optimal centroid. While using this algorithm we always need to pass the number of cluster (n_clusters). It is also called flat clustering algorithm. The number of clusters identified from data by algorithm is represented by 'K' in K-means
We already used the K-Means algorithm in the previous example. So let's see how it worked
First of all it divided the dataset into n_clusters by dividing the number of datapoints in the dataset by it. In our case it created 4 clusters with 60 datapoints each

![](bbox=[0.166, 0.493, 0.715, 0.755])

The process of dividing these clusters is totally random. The algorithm takes K(n_clusters) datapoints from the sample and divide them into a cluster
Next it will compute the cluster centroids for each of the clusters formed

![](bbox=[0.574, 0.768, 0.856, 0.951])