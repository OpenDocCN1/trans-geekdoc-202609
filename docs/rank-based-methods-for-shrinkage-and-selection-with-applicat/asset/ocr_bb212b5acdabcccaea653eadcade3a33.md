Using this formulation, a constraint, given by c, is imposed by the penalty function as follows,

$|\beta_1| + |\beta_2| \le c.$

(1.7.15)

The resulting constraint geometry is a diamond shape in two dimensions rather than the circle, as shown in Figure 1.9. The adjustment of \(\lambda > 0\) has the effect of decreasing the size of the diamond. If \(\lambda_0 = 0\), we obtain the unbiased estimates. As \(\lambda\) is increased, the diamond shrinks in size, as do the resulting parameters so it is a shrinkage estimator. Eventually, when \(\lambda = \infty\), the origin is reached, as was the case in ridge regression.

The hypothetical trajectory for LASSO starts at the unbiased LSE or rank estimates ("X") on diamond 0 and terminates on diamond 1 with \(\lambda = \lambda_1 > 0\). Both estimates shrink but neither one is 0 yet. However, when \(\lambda = \lambda_2 > \lambda_1\) and the path lands on one corner of diamond 2, where \(\beta_2 = 0\), and we are left with a model with only \(\beta_1 \neq 0\). We can now remove \(\beta_2\) and keep \(\beta_1\). As such, LASSO is a subset selection estimator. Further increases in \(\lambda\) eventually forces \(\beta_1 = 0\) at the origin.

# (b) LASSO Regression

![](bbox=[0.25, 0.49, 0.8, 0.86])

# Figure 1.9 Geometric interpretation of LASSO.