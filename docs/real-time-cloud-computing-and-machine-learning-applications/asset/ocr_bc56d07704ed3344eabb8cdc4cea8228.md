# Machine Learning Algorithms

$x_p$ - data element
$m_i^{(t)}$ - mean of the cluster (centroid of the cluster)
$m_j^{(t)}$ - mean of all other centroids

The expression implies that cluster $i$ contains data elements that are closer to the center of cluster than to the mean of all other centroids [13].

+   4. The centroids are recalculated such that they lie in the middle of each of the clusters using equation (3.2).

```
$m_i^{(t+1)} = \frac{1}{|S_i^{(t)}}|} \sum_{x_j \in S_i^{(t)}} x_j$
```

+   5. Proceed to the next iteration in which Step 3 and 4 are repeated.
6. Iterations are stopped when the centroids stop changing, when the data elements remain in the same clusters for multiple iterations or when the defined maximum number of iterations is reached.

# Short-hand Example 1

In this example, six cars are grouped into two clusters based on their weights and usages using K-Means clustering. The data about the six cars are given in Table 3.2:

# Table 3.2. K-Means clustering- Car details

| Car | Weight (Pounds) | Mileage (Miles per Gallon) |
|---|---|--|
| A | 1835 | 26 |
| B | 4341 | 15 |
| C | 2372 | 24 |
| D | 3086 | 14 |
| E | 3504 | 18 |
| F | 1970 | 31 |

As the number of clusters, K=2, two random cars are selected as centroids of each cluster. Car A and car E are selected as the centroids of clusters 1 and 2 respectively.

The Euclidean distances between each car and the centroids of each cluster are then calculated and are given in Table 3.3: