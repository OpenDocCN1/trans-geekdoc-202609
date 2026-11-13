# 15.4 Nearest neighbors

To the best of our knowledge, nearest neighbors are not used in large-scale portfolio choice applications. The reason is simple: computational cost. Nonetheless, the concept of neighbors is widespread in unsupervised learning and can be used locally in complement to interpretability tools. Theoretical results on k-NN relating to bounds for error rates on classification tasks can be found in section 6.2 of Ripley (2007). The rationale is the following. If:

+   1. the training sample is able to accurately span the distribution of \((\mathbf{y}, \mathbf{X})\); and

+   2. the testing sample follows the same distribution as the training sample (or close enough);

then the neighborhood of one instance \(\mathbf{x}_i\) from the testing features computed on the training sample will yield valuable information on \(y_i\).

In what follows, we thus seek to find neighbors of one particular instance \(\mathbf{x}_i\) (a \(K\)-dimensional row vector). Note that there is a major difference with the previous section: the clustering is intended at the observation level (row) and not at the predictor level (column).

Given a dataset with the same (corresponding) columns \(\mathbf{X}_{i,k}\), the neighbors are defined via a similarity measure (or distance)

```
\(D(\mathbf{x}_j, \mathbf{x}_i) = \sum_{k=1}^K c_k d_k(x_{j,k}, x_{i,k}),\) (15.9)
```

where the distance functions \(d_k\) can operate on various data types (numerical, categorical, etc.). For numerical values, \(d_k(x_{j,k}, x_{i,k}) = (x_{j,k} - x_{i,k})^2\) or \(d_k(x_{j,k}, x_{i,k}) = |x_{j,k} - x_{i,k}|\). For categorical values, we refer to the exhaustive survey by Boriah et al. (2008) which lists 14 possible measures. Finally the \(c_k\) in Equation (15.9) allow some flexibility by weighting features. This is useful because both raw values (\(x_{i,k}\) versus \(x_{i,k}\)) or measure outputs (\(d_k\) versus \(d_k\)) can have different scales.

Once the distances are computed over the whole sample, they are ranked using indices \(l_1^i, \dots, l_I^i\):

```
\(D \mathbf{x}_{l_1^i}, \mathbf{x}_i \le D \mathbf{x}_{l_2^i}, \mathbf{x}_i \le \dots \le D \mathbf{x}_{l_I^i}, \mathbf{x}_i\)
```

The nearest neighbors are those indexed by \(l_m^i\) for \(m = 1, \dots, k\). We leave out the case when there are problematic equalities of the type \(D \mathbf{x}_{l_m^i}, \mathbf{x}_i = D \mathbf{x}_{l_{m+1}^i}, \mathbf{x}_i\) for the sake of simplicity and because they rarely occur in practice as long as there are sufficiently many numerical predictors.

Given these neighbors, it is now possible to build a prediction for the label side \(y_i\). The rationale is straightforward: if \(\mathbf{x}_i\) is close to other instances \(\mathbf{x}_j\), then the label value \(y_i\) should also be close to \(y_j\) (under the assumption that the features carry some predictive information over the label \(y\)).