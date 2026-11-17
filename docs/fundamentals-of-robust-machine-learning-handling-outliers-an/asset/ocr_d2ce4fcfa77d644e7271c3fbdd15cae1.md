![](bbox=[0.11, 0.1, 0.57, 0.37])

Figure 1.12 Data with 1 outlier at (-400, -400).

Running the k-medians algorithm produces the following centers:

\(\hat{\mu}^{(1)} = (-1.89, 1.33)^\top \quad \hat{\mu}^{(2)} = (5.48, 0.30)^\top\).

Unlike the k-means case, the centers have not changed very much. This is highly desirable because it indicates that the outlier has not affected the outcome of clustering. This is shown graphically in lower panel of Figure 1.13 where the same two clusters are produced. The k-medians results are relatively stable compared to k-means. This is a key point to emphasize: using a robust method produces superior results in the presence of outliers and similar results with no outliers.

# 1.10.3 Detection and Removal of Outliers

One way to produce better results using k-means is to detect and remove outliers. This requires some techniques that are themselves robust in nature since the non-robust methods fail to address the issue. Consider the dataset with 1 outlier as described in the previous section. We must first run k-medians clustering since the results from k-means results are not meaningful. More generally, in order to find outliers, a robust method is always part of the methodology.

Once we have the results of robust clustering, we can apply simple rules to remove outliers. One approach is to use the “3-sigma edit” rule. This rule is used to detect and delete any points that are greater than 3\(\sigma_j\) away from the center of cluster \(C_j\), where \(j = 1, ..., K\). This rule uses the criteria that, if point \(\mathbf{x}^{(i)}\) is in matrix \(\mathbf{C}_j\),

delete \(\mathbf{x}^{(i)}\) if \(\|\mathbf{x}^{(i)} - \hat{\mu}^{(j)}\|_2 > 3\hat{\sigma}_j\) for \(i = 1, ..., n\),

where \(\hat{\mu}^{(j)}\) and \(\hat{\sigma}_j\) are the mean and standard deviation of the points in cluster \(j\). Unfortunately, the computation of the cluster mean and standard deviation will be skewed by outliers so they cannot be trusted.

A better approach is to use a robust form of the 3-sigma edit rule. Since the mean and variance cannot be computed reliably under outlier conditions, robust statistics can be used in their place. Data will only