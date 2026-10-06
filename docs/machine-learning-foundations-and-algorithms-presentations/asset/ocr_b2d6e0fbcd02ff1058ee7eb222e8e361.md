# Basics: Gaussian Bayes rule

+   * Gaussian Bayes Rule 1: used for derivation with kernels
  - Mean: $\mu_{oldsymbol{x}|y} = \mu_{oldsymbol{x}} + \Sigma_{oldsymbol{x}}F^T(\sigma_y^2 I + F\Sigma_{oldsymbol{x}}F^T)^{-1}(oldsymbol{y} - F\mu_{oldsymbol{x}})$
  - Covariance: $\Sigma_{oldsymbol{x}|y} = \Sigma_{oldsymbol{x}} - \Sigma_{oldsymbol{x}}F^T(\sigma_y^2 I + F\Sigma_{oldsymbol{x}}F^T)^{-1}F\Sigma_{oldsymbol{x}}$

+   * Gaussian Bayes Rule 2: used for derivation with features
  - Mean: $\mu_{oldsymbol{x}|y} = \mu_{oldsymbol{x}} + (\sigma_y^2\Sigma_{oldsymbol{x}}^{-1} + F^T F)^{-1}F^T(oldsymbol{y} - F\mu_{oldsymbol{x}})$
  - Covariance: $\Sigma_{oldsymbol{x}|y} = \sigma_y^2(\sigma_y^2\Sigma_{oldsymbol{x}}^{-1} + F^T F)$

Do not remember exact equations... but remember their properties

+   * Both rules are mathematically equivalent...
* However, numerically it can be a huge difference
* Bayes rule 1: Invert a matrix with dimension $dim(y) \times dim(y)$
* Bayes rule 2: Invert a matrix with dimension $dim(x) \times dim(y)$

> Use Rule 1 if $dim(y) < dim(x)$, otherwise Rule 2