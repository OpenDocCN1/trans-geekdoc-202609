We can go one step further and incorporate the oracle property by replacing LASSO with aLASSO. Then, the above equation becomes

\(\hat{\beta}_j^{D-aENet} = (1 + \lambda_2) \frac{\text{sgn}(\hat{\beta}_j^{LS}) \left( |\hat{\beta}_j^{LS}| - \lambda_1' \frac{\text{Var}(\hat{\beta}_j^{LS})}{|\hat{\beta}_j^{LSEN}|} \right)^+}{1 + \lambda_2' \text{Var}(\hat{\beta}_j^{LS})}.\) (2.8.12)

We call this the adaptive elastic net for the diagonal case (D-aEnet). Because of the reasons cited earlier regarding the oracle property, this aEnet formulation could potentially be better than nEnet or sEnet. Of course, the caveat is that the least squares estimates are needed for aLASSO and they may not be available.

# 2.8.3 Enet in Machine Learning

For machine learning, the form of the objective function for LS-Enet is usually expressed using \(\lambda\) and \(\alpha\), rather than \(\lambda_1\) and \(\lambda_2\), as follows

\(J^{LS-Enet}(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X}\boldsymbol{\beta})^\top (\mathbf{y} - \mathbf{X}\boldsymbol{\beta}) + \lambda \left[ \frac{1-\alpha}{2} \boldsymbol{\beta}^\top \boldsymbol{\beta} + \alpha \sum_{j=1}^p |\beta_j| \right],\) (2.8.13)

where \(\lambda > 0\) is the standard tuning parameter and \(0 < \alpha < 1\) controls degree to which ridge or LASSO is applied.

Likewise, the form for R-Enet is

\(D^{R-Enet}(\boldsymbol{\beta}) = D_n(\boldsymbol{\beta}) + \lambda \left[ \frac{(1-\alpha)}{2} \boldsymbol{\beta}^\top \boldsymbol{\beta} + \alpha \sum_{j=1}^p |\beta_j| \right].\) (2.8.14)

Finally, the objective function of the rank-based adaptive Enet (R-aEnet) is given by

\(D^{R-aENet}(\boldsymbol{\beta}) = D_n(\boldsymbol{\beta}) + \lambda \left[ \frac{(1-\alpha)}{2} \boldsymbol{\beta}^\top \boldsymbol{\beta} + \alpha \sum_{j=1}^p \frac{|\beta_j|}{|\hat{\beta}_j^R|} \right].\) (2.8.15)

The tuning parameter \(\lambda\) controls the impact of the penalty function while \(\alpha\) controls the selection of ridge or aLASSO by setting it to 0 or 1. Other settings are possible but the most useful values are near 1. For example, the optimum value of \(\alpha = 0.95\) for the Swiss data set using a five-fold CV scheme which produces the estimates:

\(\hat{\boldsymbol{\beta}}_n^{R-aENet} = (A = -0.11, Ex = -0.0027, Ed = -0.94, C = 0.12, I = 1.14)^\top.\)

The estimate for variable Ex is small enough to remove, as was the case with R-aLASSO.