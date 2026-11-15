
![](img/f3b106d7e76ae3afcec8895afa28732c_106_0.png)

Figure 2.9 The first-order nature of shrinkage due to LASSO.

In order to incorporate the oracle property into LS regression, a weight is introduced into the penalty function, as follows

$J^{LS-aLASSO}(\beta) = (y - X\beta)^T(y - X\beta) + \lambda_1 \sum_{j=1}^p w_j |\beta_j|.$ (2.7.13)

The effect of individual weights, \(w_j\), on each parameter can be seen in the geometric interpretation of Figure 2.10. Weights effectively re-shape the diamond from a symmetrical one in LASSO (Figure 2.9) to an asymmetrical one in aLASSO (Figure 2.10). The asymmetry is due to the differences in weights. In the case of LASSO in Figure 2.9, the trajectory starting from “x” could reach either \(\beta_1 = 0\) or \(\beta_2 = 0\) since the diamond is symmetric. However, aLASSO would likely reach the \(\beta_2 = 0\) corner first, which is the nearest corner, assuming the geometry in Figure 2.10. Then, the asymmetric diamond would continue to shrink in size as indicated by \(\lambda_1 > 0\) and \(\lambda_2 > \lambda_1\), etc., and eventually reach \(\beta_1 = 0\) before or at \(\lambda = \infty\). This sequence would imply that \(\beta_1\) is more important than \(\beta_2\) because aLASSO set \(\beta_2 = 0\) first (i.e. because it is less important). The aLASSO trace captures the actual trajectory of each parameter. In particular, the zero-crossing order of the parameters in an aLASSO trace is a key feature of this oracle penalty function and we will explore this further in this chapter, and in more detail in subsequent chapters.

The method of incorporating the oracle property requires a suitable selection of the weights. Zou (2006) proposes the use of \(w_j = 1/|\hat{\beta}_j^{LS}|\) and indeed this does provide the much desired oracle property. We stipulate here that the

![](img/f3b106d7e76ae3afcec8895afa28732c_107_0.png)

Figure 2.10 Diamond-warping effect of weights in the aLASSO estimator for \( p = 2 \).

LS (or rank) estimates must be known in advance but that is not an onerous requirement assuming that multicollinearity is not present. In that case, the loss function of aLASSO is given by

\( J^{\text{LS-aLASSO}}(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X}\boldsymbol{\beta})^{\top}(\mathbf{y} - \mathbf{X}\boldsymbol{\beta}) + 2\lambda \sum_{j=1}^p \frac{|\beta_j|}{|\hat{\beta}_j^{\text{LS}}|}, \) \(\text{(2.7.14)}\)

where each \( |\beta_j| \) is divided by \( |\hat{\beta}_j^{\text{LS}}| \). Again, we assume that \( \hat{\boldsymbol{\beta}}^{\text{LS}} \) is available implying that \( \mathbf{C} = \mathbf{X}^{\top}\mathbf{X} \) is invertible. Then, the estimates, assuming a diagonal \( \mathbf{C} \) matrix, using aLASSO are given by

\( \hat{\beta}_j^{\text{D-aLASSO}} = \text{sgn}(\hat{\beta}_j^{\text{LS}}) \left( |\hat{\beta}_j^{\text{LS}}| - \lambda_1 \frac{\sigma^2 C^{jj}}{|\hat{\beta}_j^{\text{LS}}|} \right)^+. \) \(\text{(2.7.15)}\)

Since \(\sigma^2 C^{jj}\) are the variances of each \(\hat{\beta}_j^{\text{LS}}\), we can view the individual weights as simply the variance divided by the magnitude of each \(\hat{\beta}_j^{\text{LS}}\) as follows

\(\hat{\beta}_j^{\text{D-aLASSO}} = \text{sgn}(\hat{\beta}_j^{\text{LS}}) \left( |\hat{\beta}_j^{\text{LS}}| - \lambda_1 \frac{\text{Var}(\hat{\beta}_j^{\text{LS}})}{|\hat{\beta}_j^{\text{LS}}|} \right)^+ . \quad (2.7.16)\)

The weight is effective at guiding the aLASSO solution to the corners of the asymmetric diamond shape in an order determined by the size of the variance as compared to the size of \(\hat{\beta}_j^{\text{LS}}\). In fact, the oracle property will force the solution of aLASSO to visit the least important parameters first (in an attempt to set them to zero as in Figure 2.10) and eventually make its way to the most important parameters as \(\lambda_1\) is increased from 0 to \(\infty\).

We will need to identify the zero-crossings of aLASSO traces because it contains useful variable ordering information for subset selection. A first-order estimate for the zero-crossings can be performed quickly by setting the \((\cdot)^+\) term to zero in Eq. (2.7.16). Therefore, for a strictly diagonal design matrix, we can use

\(\lambda_j^0 = \frac{|\beta_j|^2}{\text{Var}(\hat{\beta}_j^{\text{LS}})} \approx \frac{|\beta_j|^2}{\text{s.e.}^2(\hat{\beta}_j^{\text{LS}})} = (t_j)^2 . \quad (2.7.17)\)

The zero-crossing of \(\beta_j\) is simply its \(t\) statistic squared, i.e. \((t_j)^2\). If \((t_j)^2\), or equivalently \(|t_j|\), are ordered, then a reasonable sequence of variables (although not necessarily oracle) is obtained\(^7\). This ordering assumes no correlation between variables, which is unlikely and hence not oracle, but it does provide a good first-order assessment of the importance of each variable.

If we compare the zero-crossings for LASSO and aLASSO for the orthonormal case, we find that \(\lambda_{0,j}^{\text{LASSO}} = |\hat{\beta}_j^{\text{LS}}|\), and \(\lambda_{0,j}^{\text{aLASSO}} = |\hat{\beta}_j^{\text{LS}}|^2\). Therefore the variable ordering would be the same for both and hence both have the oracle property for the orthonormal case. Once you introduce the diagonal case with \(\text{Var}(\hat{\beta}_j^{\text{LS}})\), the two may no longer agree on the ordering since \(\lambda_j^{\text{LASSO}} = |\hat{\beta}_j^{\text{LS}}| / \text{Var}(\hat{\beta}_j^{\text{LS}})\) and \(\lambda_{0,j}^{\text{aLASSO}} = |\hat{\beta}_j^{\text{LS}}|^2 / \text{Var}(\hat{\beta}_j^{\text{LS}})\). And finally, with the full \(C^{-1}\) matrix, the correlations between variables may change the ordering significantly.

To summarize, LASSO has the oracle property only in the orthonormal case, whereas aLASSO retains it theoretically in all cases. Of course, in practice, the zero-crossings are data-dependent but generally have the capability of producing a near-optimal ordering in most cases, assuming enough observations.

## 2.7.4 R-estimation with LASSO and aLASSO

For R-estimation, we formulate the objective function for the R-LASSO estimator as

$D^{\text{R-LASSO}}(\boldsymbol{\beta}) = D_n(\boldsymbol{\beta}) + \lambda_1 \sum_{j=1}^p |\beta_j|.$ (2.7.18)

If R-LASSO is applied to the Swiss data set using a five-fold cross-validation scheme, as described earlier, the following estimates are produced:

\(\hat{\boldsymbol{\beta}}_n^{\text{R-LASSO}} = (A = -0.16, Ex = -0.23, Ed = -0.80, C = 0.10, I = 1.07)^\top.\)

Note that none of the parameters have been set to 0. Hence, for this example, LASSO does not perform subset selection.

The R-aLASSO objective function is

$D^{\text{R-aLASSO}}(\boldsymbol{\beta}) = D_n(\boldsymbol{\beta}) + \lambda_1 \sum_{j=1}^p \frac{|\beta_j|}{|\hat{\beta}_j^{\text{R}}|}.$ (2.7.19)

Again, applying a five-fold cross-validation scheme using the Swiss data set produces the following estimates:

\(\hat{\boldsymbol{\beta}}_n^{\text{R-aLASSO}} = (A = -0.11, Ex = -0.003, Ed = -0.94, C = 0.11, I = 1.13)^\top.\)

This time, the variable Ex has been set to a value that is almost 0. This variable is effectively removed from the parameter set and we can observe the subset selection feature of aLASSO in this case. The important combination of rank loss with aLASSO penalty has robustness while ordering the variables so that optimal subset selection can be carried out. We will describe this in more detail shortly.

But first, to illustrate the oracle feature of aLASSO, we need to examine the traces associated with LASSO and aLASSO⁸. This is provided in Figure 2.11 for the Swiss data set. The number of models built is m = 40, one for each selected λ₁. The first thing to notice is that the traces all reach 0 well before λ₁ = ∞. These points are called the “zero-crossings” of the traces. This is a major feature difference between ridge and LASSO (or aLASSO). We again note that LS and rank are very similar, owing to the importance of C⁻¹ in the trajectory of the traces in both sets. The differences in the values along the log(λ₁) axis are due to the magnitude of the LS vs. rank loss functions, as described earlier for ridge.
