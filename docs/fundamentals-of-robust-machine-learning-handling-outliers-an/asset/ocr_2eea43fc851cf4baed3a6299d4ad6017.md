![](bbox=[0.12, 0.11, 0.55, 0.35])

![](bbox=[0.12, 0.38, 0.55, 0.63])

**Figure 1.11** k-means and k-medians clustering.

introduced due to a typographical error. The results of k-means are shown graphically in the upper panel of Figure 1.13. One large cluster is created with all the data and another cluster is created containing only the outlier. The outlier cluster is not shown in Figure 1.13 at the scale of the plot but it is clear that one of the cluster centers is forced outside of the region of the data by the k-means algorithm because only one is visible in the diagram. The two centers are

\(\hat{\mu}^{(1)} = (-400, -400)^\top \quad \text{and} \quad \hat{\mu}^{(2)} = (1.10, 0.6)^\top.\)

The first cluster has a center that is well outside the cluster region located at (-400, -400). The other center is located in the middle of the true data. It is evident that even a single outlier in the dataset can significantly impact k-means clustering. We saw this effect in an earlier section regarding the mean vs. the median and we see it here again in the clustering problem.