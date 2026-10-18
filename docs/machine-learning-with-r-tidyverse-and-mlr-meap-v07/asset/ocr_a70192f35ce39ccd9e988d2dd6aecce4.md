+   Regularization is a set of techniques that prevent overfitting by shrinking model parameter estimates
+   There are three regularization techniques for linear models: ridge regression, LASSO, and elastic net
+   Ridge regression uses the L2 norm to shrink parameter estimates towards zero (but never exactly zero unless they were zero to begin with)
+   LASSO uses the L1 norm to shrink parameter estimates towards zero (and possibly exactly zero, resulting in feature selection)
+   Elastic net combines both L2 and L1 regularization, the ratio of which is controlled by the alpha hyperparameter
+   For all three, the lambda hyperparameter controls the strength of shrinkage