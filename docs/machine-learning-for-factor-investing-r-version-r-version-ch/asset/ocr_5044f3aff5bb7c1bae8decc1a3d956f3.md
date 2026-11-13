![](bbox=[0.1, 0.06, 0.9, 0.24])

# FIGURE 6.1: Elementary tree scheme; visualization of the splitting process.

The second step is to split the two clusters one level further. Since only one variable (size) is relevant, the secondary splits are straightforward. In the end, our stylized tree has four consistent clusters. The analogy with factor investing is simple: the color represents performance: red for high performance and blue for mediocre performance. The features (size and complexity of stars) are replaced by firm-specific attributes, such as capitalization, accounting ratios, etc. Hence, the purpose of the exercise is to find the characteristics that allow to split firms into the ones that will perform well versus those likely to fare more poorly.

We now turn to the technical construction of regression trees (splitting process). We follow the standard literature as exposed in Breiman et al. (1984) or in chapter 9 of Hastie et al. (2009). Given a sample of \((y_i, \mathbf{x}_i)\) of size \(I\), a regression tree seeks the splitting points that minimize the total variation of the \(y_i\) inside the two child clusters. These two clusters need not have the same size. In order to do that, it proceeds in two steps. First, it finds, for each feature \(x_i^{(k)}\), the best splitting point (so that the clusters are homogeneous in \(\mathbf{Y}\)). Second, it selects the feature that achieves the highest level of homogeneity.

Homogeneity in regression trees is closely linked to variance. Since we want the \(y_i\) inside each cluster to be similar, we seek to **minimize their variability** (or **dispersion**) inside each cluster and then sum the two figures. We cannot sum the variances because this would not take into account the relative sizes of clusters. Hence, we work with *total variation*, which is the variance times the number of elements in the clusters.

Below, the notation is a bit heavy because we resort to superscripts \(k\) (the index of the feature), but it is largely possible to ignore these superscripts to ease understanding. The first step is to find the best split for each feature, that is, solve \(\text{argmin}_{c^{(k)}} V_I^{(k)}(c^{(k)})\) with

```
\(V_I^{(k)}(c^{(k)}) = \underbrace{\sum_{x_i^{(k)} < c^{(k)}}}_{\text{Total dispersion of first cluster}} (y_i - m_I^{k,-}(c^{(k)}))^2 + \underbrace{\sum_{x_i^{(k)} > c^{(k)}}}_{\text{Total dispersion of second cluster}} (y_i - m_I^{k,+}(c^{(k)}))^2, \quad (6.1)\)
```