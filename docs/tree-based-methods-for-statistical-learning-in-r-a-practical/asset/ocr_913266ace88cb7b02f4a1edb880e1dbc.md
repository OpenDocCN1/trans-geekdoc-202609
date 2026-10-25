# 2.5.2 Cross-validation

Once the sequence \(\alpha_1, \alpha_2, ..., \alpha_{k-1}\) has been found, we still need to estimate the overall risk/quality of the corresponding sequence of nested subtrees, \(R_{\alpha_i}(\mathcal{T})\), for \(i = 1, 2, ..., k - 1\). Breiman et al. [1984, Chap. 11] suggested picking \(\alpha\) using a separate validation set or \(k\)-fold cross-validation. The latter is more computational, but tends to be preferred since it makes use of all available data, and both tend to lead to similar results. The procedure described in Algorithm 2.1 below follows the implementation in the **rpart** package in R (see the “Introduction to Rpart” vignette):

# Algorithm 2.1 \(K\)-fold cross-validation for cost-complexity pruning.

+   1) Fit the full model to the learning sample to obtain \(\alpha_1, \alpha_2, ..., \alpha_{k-1}\).

+   2) Define \(\beta_i\) according to

\(\beta_i = \left\{ \begin{array}{ll} 0 & i = 1 \\ \sqrt{\alpha_{i-1}\alpha_i} & i = 2, 3, ..., m - 1 \\ \infty & i = m \end{array} \right.\)

Since any value of \(\alpha\) in the interval \((\alpha_i, \alpha_{i+1}]\) results in the same subtree, we instead consider the sequence of \(\beta_i\)’s, which represent typical values within each range using the geometric midpoint.

+   3) Divide the data into \(k\) groups (or folds), \(D_1, D_2, ..., D_k\), with approximately \(k/N\) observations in each (\(N\) being the number of rows in the learning sample). For \(i = 1, 2, ..., k\), do the following:

+   a) Fit the full model to the learning sample, but omit the subset \(D_i\), and find the sequence of optimal subtrees \(\mathcal{T}_{\beta_1}, \mathcal{T}_{\beta_2}, ..., \mathcal{T}_{\beta_k}\).

+   b) Compute the prediction error from each tree on the validation set \(D_i\).

+   4) For each subtree, aggregate the results by averaging the \(k\) out-of-sample prediction errors.

+   5) Return \(\mathcal{T}_\beta\) from the initial sequence of trees based on the full learning sample, where \(\beta\) corresponds to the \(\beta_i\) associated with the smallest prediction error in step 4).