![](bbox=[0.16, 0.11, 0.6, 0.34])

![](bbox=[0.16, 0.35, 0.6, 0.59])

Figure 2.6 MSE Derivative plot to find optimal \(\lambda_2\) for the diagonal case.

# 2.6.2 K-fold Cross-validation Scheme

In machine learning applications, we do not compute the optimal \(\lambda_2\) in the manner described in the previous section. Instead, a cross-validation scheme is used to produce estimates that are suitable for prediction. If our goal is to produce a generalized model, then we should use the data set in a way that reflects this goal. Given a data set, we first divide it into a training set and a test set (which we view as an “unseen” or “hold-out” test set). The test set cannot be used to select \(\lambda_2\) but can be used to assess our final prediction accuracy. We do not want to inadvertently tune \(\lambda_2\) to this specific test set since the prediction accuracy may not generalize to other test sets. Instead, it is common to further subdivide the training set into \(K\) disjoint sets, called cross-validation sets or “folds”, as discussed below. These sets will be used to select the optimal \(\lambda_2\).