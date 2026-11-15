# Figure 8. Hard and soft clustering

![](bbox=[0.19, 0.13, 0.81, 0.28])

The hard and soft clustering algorithms are visualized in Figure 6. In the hard clustering algorithm, one data point belongs to a single cluster. On the other hand, the soft clustering algorithms allow a data point that belongs to multiple clusters with a weight or belongingness.

# Figure 9. The pseudo-code of k-means

```
1. Initialize cluster centroids \(\mu_1, \mu_2, \dots, \mu_k \in \mathbb{R}^n\) randomly.

2. Repeat until convergence: {

    For every \(i\), set
    
    \(c^{(i)} := \arg\min_j \|x^{(i)} - \mu_j\|^2.\)

    For each \(j\), set
    
    \(\mu_j := \frac{\sum_{i=1}^m 1\{c^{(i)} = j\}x^{(i)}}{\sum_{i=1}^m 1\{c^{(i)} = j\}}.\)

}
```

The pseudo-code of the k-means algorithm is displayed in Figure 7. We would like to cluster the data into k-clusters. To do that, we first initialize randomly k centroids, then iteratively assign each data points to the closet centroids, then we recompute the centroids as the center points of all the points of a cluster. The algorithm stops when it reaches convergence.