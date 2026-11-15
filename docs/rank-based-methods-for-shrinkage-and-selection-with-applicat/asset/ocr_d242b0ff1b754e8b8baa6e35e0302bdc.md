The linear dispersion function above was described at length in earlier chapters in this book. It can be shown that \(D_n(\beta)\) is a non-negative, continuous, and convex function of \(\beta\) and therefore is quite suitable to efficiently find the optimal value of \(\beta\). This was the essential breakthrough that made linear rank-based methods workable. Extension to multiple linear regression is straightforward as described in detail in earlier chapters. We now consider the nonlinear case.

# 11.3.3 Nonlinear Dispersion Function

A simple nonlinear model is as follows

\(\mathbf{y} = \mathbf{f}(\boldsymbol{\beta}; \mathbf{x}) + \boldsymbol{\epsilon},\) (11.3.24)

where \(\mathbf{f}(\boldsymbol{\beta}; \mathbf{x}) = (f(\boldsymbol{\beta}; \mathbf{x}_1), \dots, f(\boldsymbol{\beta}; \mathbf{x}_n))^T\) is a real-valued nonlinear function. A suitable estimator for \(\boldsymbol{\beta}\) is one that obtains \(\hat{\boldsymbol{\beta}}_n\) as the minimizer of the residual norm,

\(\hat{\boldsymbol{\beta}} = \operatorname{argmin}_{\boldsymbol{\beta}} ||\mathbf{y} - \mathbf{f}(\boldsymbol{\beta}; \mathbf{x})||.\) (11.3.25)

For the rank-based procedure, we again define a pseudo-norm given by

\(||\mathbf{y} - \mathbf{f}(\boldsymbol{\beta}; \mathbf{x})||_\phi = \sum_{i=1}^n (y_i - f(\mathbf{x}_i^T \boldsymbol{\beta})) a_n(R_{n_i}(y_i - \mathbf{x}_i^T \boldsymbol{\beta})).\) (11.3.26)

This is the nonlinear dispersion function associated with the simple nonlinear model of Eq. (11.3.24). Hettmansperger and McKean (2011) established consistency and asymptotic normality of the estimator based on the Wilcoxon score function. We adopt those results and assume that they hold in the extensions to follow.

The general multivariate nonlinear case follows from the discussion above as,

\(D_n(\boldsymbol{\beta}) = \sum_{i=1}^n (y_i - f(\mathbf{x}_i^T \boldsymbol{\beta})) a_n(R_{n_i}(\boldsymbol{\beta})),\) (11.3.27)

where the nonlinear function, \(f(\cdot)\), for the logistic regression case is given by

\(f(\mathbf{x}_i^T \boldsymbol{\beta}) = \frac{1}{1 + \exp(-\mathbf{x}_i^T \boldsymbol{\beta})}.\) (11.3.28)

The first term of \(D_n(\boldsymbol{\beta})\) is simply the residual for each observation. The second term, \(a_n(R_n(\boldsymbol{\beta}))\), is the score for each residual based on the Wilcoxon scoring function, \(\phi(u) = \sqrt{12}(u - 1/2)\). The complete scoring function of Eq. (11.3.23) is given by