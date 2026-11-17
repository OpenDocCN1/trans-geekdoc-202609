
| A | 1 | 1 |
|---|---|---|
| B | 2 | 2 |
| C | 5 | 5 |
| D | 5 | 6 |
| E | 1 | 5 |
| F | 2 | 6 |
| Cluster 1 | 1 | 1 |
| Cluster 2 | 2 | 2 |
| Cluster 3 | 5 | 5 |

Table 6.8 – Iteration input data for K-Means

Table 6.8 contains three clusters with the following centroids: (1,1), (2,2), (5,5). The number of clusters (3) was defined a priori and the centroid for each cluster was randomly defined. Figure 6.13 shows the stage of the algorithm that you are at right now.

## K-Means - Start iteration 1

![](img/87c29232224b00f5a8bba6a66a391700_170_0.png)

Figure 6.13 – Plotting the K-Means results before completing the first iteration

Here, you can’t see points A, B, and C since they overlap with cluster centroids, but don’t worry – they will appear soon. Next, you have to compute the distance of each data point to each cluster centroid, and then, you need to choose the cluster that is the closest to each point.

| xc1 | yc1 | xc2 | yc2 | xc3 | yc3 | distance-c1 | distance-c2 | distance-c3 | Cluster |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | 2 | 2 | 5 | 5 | 0.0 | 1.4 | 5.7 | Cluster 1 |
| 1 | 1 | 2 | 2 | 5 | 5 | 1.4 | 0.0 | 4.2 | Cluster 2 |
| 1 | 1 | 2 | 2 | 5 | 5 | 5.7 | 4.2 | 0.0 | Cluster 3 |
| 1 | 1 | 2 | 2 | 5 | 5 | 6.4 | 5.0 | 1.0 | Cluster 3 |
| 1 | 1 | 2 | 2 | 5 | 5 | 4.0 | 3.2 | 4.0 | Cluster 2 |
| 1 | 1 | 2 | 2 | 5 | 5 | 5.1 | 4.0 | 3.2 | Cluster 3 |
| Legend | | | | | | | | | |
| xc1 = x value of cluster 1 | | | | | | | | | |
| yc1 = y value of cluster 1 | | | | | | | | | |

## Table 6.9 – Processing iteration 1

Table 6.9 contains the following elements:

- Each row represents a data point.
- The first six columns represent the centroid axis (x and y) of each cluster.
- The next three columns represent the distance of each data point to each cluster centroid.
- The last column represents the clusters that are the closest to each data point.

Looking at data point _A_ (first row), you can see that it was assigned to cluster 1 because the distance from data point _A_ to cluster 1 is 0 (do you remember that they were overlapping?). The same calculation happens to all other data points to define a cluster for each data point.

Before you move on, you might want to see how those Euclidean distances between the clusters and the data points were computed. For demonstration purposes, the following simulation will consider the distance from data point _A_ to cluster 3 (the first row in _Table 6.9_, column `distance-c3`, value 5.7).

First of all, the following formula was used to calculate the Euclidean distance:

![](img/87c29232224b00f5a8bba6a66a391700_171_0.png)

Here, you have the following:

- _x_<sub>1</sub> = x of data point _A_ = 1
- _y_<sub>1</sub> = y of data point _A_ = 1
- _x_<sub>2</sub> = x of cluster 3 = 5
- _y_<sub>2</sub> = y of cluster 3 = 5

Figure 6.14 applies the formula, step by step.

```
√(((1 - 5)² + (1 - 5)²)
√(((4)² + (4)²)
√(16 + 16)
√32

5.656 or ~5.7
```

Figure 6.14 – Computing the Euclidean distance step by step

That is just fantastic, isn’t it? You have almost completed the first iteration of K-Means. In the very last step of iteration 1, you have to refresh the cluster centroids. Remember: initially, they were randomly defined, but now, you have just assigned some data points to each cluster, which means you should be able to identify where the central point of the cluster is.

In this example, the linkage method will be used to refresh the cluster centroids. This is a very simple step, and the results are presented in Table 6.10.

| Point | x | y |
|---|---|---|
| A | 1 | 1 |
| B | 2 | 2 |
| C | 5 | 5 |
| D | 5 | 6 |
| E | 1 | 5 |
| F | 2 | 6 |
| Cluster 1 | 1 | 1 |
| Cluster 2 | 1.5 | 3.5 |
| Cluster 3 | 4 | 5.7 |

## Table 6.10 – K-Means results after iteration 1

Table 6.10 shows the same data points (A to F) that you are dealing with (by the way, they will never change), and the centroids of clusters 1, 2, and 3. Those centroids are quite different from what they were initially, as shown in Table 6.8. This is because they were refreshed using average linkage! The method got the average value of all the x and y values of the data points of each cluster. In the next simulation, have a look at how (1.5, 3.5) were obtained as centroids of cluster 2.

If you look at Table 6.9, you will see that cluster 2 only has two data points assigned to it: B and E. These are the second and fifth rows in that figure. If you take the average values of the x axis of each point, then you will have (2 + 1) / 2 = 1.5 and (2 + 5) / 2 = 3.5.

With that, you are done with iteration 1 of K-Means and you can view the results in Figure 6.15.

## K-Means - Finish iteration 1

![](img/87c29232224b00f5a8bba6a66a391700_173_0.png)

Figure 6.15 – Plotting the K-Means results after the first iteration

Now, you can see almost all the data points, except for data point A because it is still overlapping with the centroid of cluster 1. Moving on, you have to redo the following steps:

- Recalculate the distance between each data point and each cluster centroid and reassign clusters, if needed.
- Recalculate the cluster centroids.

You do those two tasks many times until the cluster centroids converge and they don’t change anymore, or you reach the maximum number of allowed iterations, which can be set as a hyperparameter of K-Means. For demonstration purposes, after four iterations, your clusters will look like Figure 6.16.

## K-Means - Finish iteration 4

![](img/87c29232224b00f5a8bba6a66a391700_174_0.png)

Figure 6.16 – Plotting the K-Means results after the fourth iteration

On the fourth iteration, all the cluster centroids look pretty consistent, and you can clearly see that all data points could be grouped according to their proximity.

## IMPORTANT NOTE

In this example, you have only set two dimensions for each data point (dimensions x and y). In real use cases, you can see far more dimensions, and that is why clustering algorithms play a very important role in identifying groups in the data in a more automated fashion.

Hopefully, you have enjoyed how to compute K-Means from scratch! This knowledge will be beneficial for the exam and for your career as a data scientist. By the way, as advised many times, data scientists must be sceptical and curious, so you might be wondering why three clusters were defined in this example and not two or four. You may also be wondering how you measure the quality of the clusters.

You didn’t think this explanation wouldn’t be provided, did you?

## Defining the number of clusters and measuring cluster quality

Although K-Means is a great algorithm for finding patterns in your data, it will not provide the meaning of each cluster, nor the number of clusters you have to create to maximize cluster quality.

In clustering, cluster quality means that you want to create groups with a high homogeneity among the elements of the same cluster, and a high heterogeneity among the elements of different clusters. In other words, the elements of the same clusters should be close/similar, whereas the elements of different clusters should be well separated.

One way to compute the cluster’s homogeneity is by using a metric known as the sum of square errors, or SSE for short. This metric will compute the sum of squared differences between each data point and its cluster centroid. For example, when all the data points are located at the same point where the cluster centroid is, then the SSE will be 0. In other words, you want to minimize the SSE. The following equation formally defines the SSE:

```
SSE = \sum_{i=1}^{n} (x_i - x_p)^2
```

Now that you know how to check the cluster quality, it is easier to understand how to define the number of appropriate clusters for a given dataset. All you have to do is find the optimal number of clusters to minimize the SSE. A very popular method that works around that logic is known as the **elbow method**.

The elbow method proposes executing the clustering algorithm many times. In each execution, you will test a different number of clusters, _k_. After each execution, you compute the SSE related to _k_ number of clusters. Finally, you can plot these results and select the number of _k_ where the SSE stops to drastically decrease.

## IMPORTANT NOTE

*Adding more clusters will naturally decrease the SSE. In the elbow method, you want to find the point where that change becomes smoother, which means that the addition of new clusters will not bring too much value.*

In the previous example, three clusters were created. Figure 6.17 shows the elbow analysis that supports this decision.

![](img/87c29232224b00f5a8bba6a66a391700_175_0.png)

Figure 6.17 – The elbow method

You can conclude that adding more than three or four clusters will add unnecessary complexity to the clustering process.

Of course, you should always consider the business background while defining the number of clusters. For example, if you are creating a customer segmentation model and your company has prepared the commercial team and business processes to support four segments of customers, there is no harm in setting up four clusters instead of three.
