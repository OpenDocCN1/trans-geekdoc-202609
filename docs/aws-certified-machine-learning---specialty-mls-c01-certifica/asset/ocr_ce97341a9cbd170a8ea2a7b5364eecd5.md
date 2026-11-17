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

# K-Means - Start iteration 1

![](bbox=[0.19, 0.535, 0.86, 0.81])

Figure 6.13 – Plotting the K-Means results before completing the first iteration

Here, you can’t see points A, B, and C since they overlap with cluster centroids, but don’t worry – they will appear soon. Next, you have to compute the distance of each data point to each cluster centroid, and then, you need to choose