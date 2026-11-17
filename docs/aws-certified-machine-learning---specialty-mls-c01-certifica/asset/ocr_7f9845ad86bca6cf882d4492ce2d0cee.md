+   * x₂ = x of cluster 3 = 5
+   * y₂ = y of cluster 3 = 5

Figure 6.14 applies the formula, step by step.

```
√(((1 - 5)² + (1 - 5)²)
√(((4)² + (4)²)
√(16 + 16)
√32

5,656 or ~5,7
```

Figure 6.14 – Computing the Euclidian distance step by step

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
| Cluster 2 | 1,5 | 3,5 |
| Cluster 3 | 4 | 5,7 |