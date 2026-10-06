# 3. Segmentation with K-means Clustering

Then we are applying K-means Clustering, an unsupervised learning which works according to the following steps:

+   1. Start k=n centroids=number-of-clusters arbitrarily or strategically.
2. Based on Euclidean distance, assign each data point to the nearest centroid to create the groups.
3. Centers should be moved to the cluster's average of all points.
4. Repeat steps 2 and 3 until convergence.

The process evaluates the sum of squared distances between each cluster's center and clustered point as it iterates through the steps.(Figure.8)

![](bbox=[0.118, 0.355, 0.626, 0.574])

# 4. Hyper Parameter Tuning

Using the elbow technique, we will choose k while rejecting the K-means optimization criterion of inertia. With k values ranging from 1 to 15, we will develop multiple K-means models and store the related inertia values. Plotting inertia against the k values showed in below figure:(Figure.9)

Figure 9. Elbow curve

![](bbox=[0.335, 0.796, 0.626, 0.915])