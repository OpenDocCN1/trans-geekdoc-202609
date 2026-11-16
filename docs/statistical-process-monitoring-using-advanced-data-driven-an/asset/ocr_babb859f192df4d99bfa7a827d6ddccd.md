by trading-off bias and variance. The RR estimator is computed by minimizing the following objective function [17].

$$\min_{\beta} \left( \|\mathbf{X}\beta - \mathbf{y}\|_2^2 + \lambda \|\beta\|_2^2 \right),$$ (2.4)

$$\hat{\boldsymbol{\beta}}_{RR} = \left( \mathbf{X}^T \mathbf{X} + \lambda \mathbf{I} \right)^{-1} \mathbf{X}^T \mathbf{y},$$ (2.5)

where \(\lambda\) is a positive constant, and \(I \in \mathbb{R}^{m \times m}\) is the identity matrix. Note that from Eq. (2.5), the term \(\lambda \mathbf{I}\) added to \((\mathbf{X}^T \mathbf{X})\) enhances the conditioning of the estimation problem. Of course, the RR estimator, \(\hat{\boldsymbol{\beta}}_{RR}\), is basically a linear transformation of the OLS estimator \(\hat{\boldsymbol{\beta}}_{OLS}\). Eq. (2.5) can be rewritten as

$$\hat{\boldsymbol{\beta}}_{RR} = \left( \mathbf{X}^T \mathbf{X} + \lambda \mathbf{I} \right)^{-1} (\mathbf{X}^T \mathbf{X}) \hat{\boldsymbol{\beta}}_{OLS} = \mathbf{Z}_{\lambda} \hat{\boldsymbol{\beta}}_{OLS}.$$ (2.6)

Thus, the RR estimator is a biased estimator since

$$\mathbb{E}(\hat{\boldsymbol{\beta}}_{RR}) = \mathbb{E}(\mathbf{Z}_{\lambda} \hat{\boldsymbol{\beta}}_{OLS}) = \mathbf{Z}_{\lambda} \boldsymbol{\beta}.$$ (2.7)

The covariance matrix of \(\hat{\boldsymbol{\beta}}_{RR}\) is expressed as

$$V(\hat{\boldsymbol{\beta}}_{RR}) = \sigma^2 \left( \mathbf{X}^T \mathbf{X} + \lambda \mathbf{I} \right)^{-1} \mathbf{X}^T \left( \mathbf{X}^T \mathbf{X} + \lambda \mathbf{I} \right)^{-1}.$$ (2.8)

The basic concept when using RR is to select a value of \(\lambda\) that guarantees a greater decrease in the variance term than an increase in the squared bias. If this is accomplished, the MSE of \(\hat{\boldsymbol{\beta}}_{RR}\) will be less than the variance of \(\hat{\boldsymbol{\beta}}_{OLS}\). In [18], it has been demonstrated that there is a positive constant \(\lambda\) for which the MSE \(\hat{\boldsymbol{\beta}}_{RR}\) is less than the variance of \(\hat{\boldsymbol{\beta}}_{OLS}\).

In practice, various procedures have been developed to choose the value of \(\lambda\). For instance, in [18] the authors proposed to determine a suitable value of \(\lambda\) by inspecting the ridge trace, which is a plot of elements of \(\hat{\boldsymbol{\beta}}_{RR}\) versus \(\lambda\), where \(\lambda \in [0 \ 1]\). The aim is to determine a reasonably small value of \(\lambda\) for which the ridge estimates are stable. In [19], an appropriate selection of \(\lambda\) is given as, \(\kappa = \frac{m \hat{\sigma}^2}{\hat{\boldsymbol{\beta}}_{OLS}^T \hat{\boldsymbol{\beta}}_{OLS}}\), where \(\hat{\boldsymbol{\beta}}_{OLS}\) and \(\hat{\sigma}^2\) are determined using a least squares solution.

Of course, these models can be used as an alternative to mitigate the ill-conditioning problem. However, they are not easily interpretable, whereas an important purpose of data modeling is interpretability; see [15,16,18].

# 2.2.2 Latent variable regression (LVR) models

Multivariate statistical projection methods such as PCA, PCR, and PLS are commonly utilized to handle a high number of highly correlated process variables by conducting regression on a smaller number of transformed variables (i.e., latent