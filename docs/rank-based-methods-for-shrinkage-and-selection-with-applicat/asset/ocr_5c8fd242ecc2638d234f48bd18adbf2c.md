which is a scalar quantity, and

$\text{Var}(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}}) = \sigma^2(\mathbf{X}^\top\mathbf{X} + \lambda_2\mathbf{I}_p)^{-1}(\mathbf{X}^\top\mathbf{X})(\mathbf{X}^\top\mathbf{X} + \lambda_2\mathbf{I}_p)^{-1}, \quad (2.6.3)$

which is a matrix quantity (for which trace is taken), respectively.

The above expressions are cumbersome and difficult to gain any understanding. To simplify the analysis and to develop intuition, let $\mathbf{X}^\top\mathbf{X} = \mathbf{I}_p$. This yields

$\text{bias}^2(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}}) = \frac{\lambda_2^2}{(1+\lambda_2)^2}\boldsymbol{\beta}^\top\boldsymbol{\beta}, \quad (2.6.4)$

and

$\text{tr}(\text{Var}(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}})) = \frac{p\sigma^2}{(1+\lambda_2)^2}. \quad (2.6.5)$

Hence, the quadratic risk is given by

$\text{MSE}(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}}) \approx \frac{p\sigma^2}{(1+\lambda_2)^2} + \frac{\lambda_2^2}{(1+\lambda_2)^2}\boldsymbol{\beta}^\top\boldsymbol{\beta}. \quad (2.6.6)$

We see that if $\lambda_2 = 0$, then the bias is zero and the variance is given by $p\sigma^2$. Trying to enforce that the bias be zero may not lead to a desirable estimator due to the possibility of a large variance. In fact, as we increase $\lambda_2$, the bias increases while the variances decreases. As $\lambda_2 \rightarrow \infty$, the variance approaches zero while the bias converges to $\boldsymbol{\beta}^\top\boldsymbol{\beta}$, provided this quantity is bounded. This situation is also undesirable because the bias is now large. The optimal choice of $\lambda_2$ is then a balance between enough bias to avoid over-fitting and enough variance to avoid under-fitting. Our goal becomes finding the optimal value $\lambda_{2(\text{opt})}$ that minimizes the quadratic risk.

To obtain the optimal $\lambda_2$ for the orthonormal case, we take the partial derivative of Eq. (2.6.6) w.r.t. $\lambda_2$ and set it to zero. Solving for $\lambda_2$, we obtain

$\lambda_{2(\text{opt})}^O = \frac{p\sigma^2}{\boldsymbol{\beta}^\top\boldsymbol{\beta}}. \quad (2.6.7)$

For the Swiss data set, assume that $\hat{\boldsymbol{\beta}}_n^{\text{LS}}$ are the unbiased estimates, $p = 5$ and $\hat{\sigma}^2 = 50.1$. Then, the approximate value of the optimal $\lambda_2$ is

$\hat{\lambda}_{2(\text{opt})}^O = \frac{p\hat{\sigma}^2}{(\hat{\boldsymbol{\beta}}^{\text{LS}})^\top\hat{\boldsymbol{\beta}}^{\text{LS}}} = 123.7.$

If we examine Figure 2.5, we would place a vertical line at $\lambda_2 = 123.7$ in the bottom left panel labelled LS-ridge to obtain the ridge estimates. However, we