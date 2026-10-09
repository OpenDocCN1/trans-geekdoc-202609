![](bbox=[0.19, 0.09, 0.52, 0.4])

![](bbox=[0.54, 0.09, 0.87, 0.4])

FIGURE 7.22: OOS prediction results for (left) PLS as a function of $K$ and (right) lasso as a function of $\lambda$.

+   1. $K$-means is only one way to fit mixture models. One big improvement can come by accounting for uncertainty about each $k_{i}$ when updating the $\boldsymbol{\hat{\mu}}_{k}$ centers; this leads to the EM (expectation-maximization) algorithm.
2. Even though $K$ nearest neighbors and $K$-means have similar names, they have almost nothing to do with each other beyond the fact that both require careful scaling of inputs.
3. You can use $\boldsymbol{\hat{\mu}}_{k} = n_{i}/n$ to estimate the mixture component weights.
4. K. Rieder and L. Wasserman. Practical Bayesian density estimation using mixtures of normals. *Journal of the American Statistical Association*, **92**: 894-902, 1997.
5. The geographic pattern in **Figure 7.7** is striking, but these first two factors only explain $0.45\%$ of the original genetic variation. Don't be misled into overemphasizing the importance of geography on genes.
6. If you are familiar with linear algebra, $\phi_{1}$ is solvable as the first $eigenvector$ of the covariance matrix $X^{T}X$. Since arbitrary shifts and scales of $v_{i}$ will give the same $R_{i}$ after adjustment to $\phi_{j}$, we add the restriction $\sum_{j}^{I} \phi_{j}^{2} = 1$ to nail down scale.
7. If you work through the details, this definition for $v_{k}$ will be a shifted and rescaled version of the PC scores implied by the algorithms we've described elsewhere. Since the $v$'s are latent and have no inherent units, these definitions are all essentially equivalent.
8. Keith T. Poole. *Spatial Models of Parliamentary Voting*. Cambridge University Press, New York, 2005.