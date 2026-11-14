![](bbox=[0.38, 0.1, 0.63, 0.32])

Figure 2.11: Illustration of injective and surjective functions.

Hence the normalization constant is given by

\( Z = \sum_{\mathbf{x}} q(\mathbf{x}) \exp \left( - \sum_k \lambda_k f_k(\mathbf{x}) \right) \) (2.256)

This has exactly the form of the exponential family, where \(\mathbf{f}(\mathbf{x})\) is the vector of sufficient statistics, \(-\boldsymbol{\lambda}\) are the natural parameters, and \(q(\mathbf{x})\) is our base measure.

For example, if the features are \(f_1(x) = x\) and \(f_2(x) = x^2\), and we want to match the first and second moments, we get the Gaussian distribution.

# ## 2.5 Transformations of random variables

Suppose \(\mathbf{x} \sim p_x(\mathbf{x})\) is some random variable, and \(\mathbf{y} = f(\mathbf{x})\) is some deterministic transformation of it. In this section, we discuss how to compute \(p_y(\mathbf{y})\).

# ### 2.5.1 Invertible transformations (bijections)

Let \(f\) be a bijection that maps \(\mathbb{R}^n\) to \(\mathbb{R}^n\). (A bijection is a function that is injective, or one-to-one, and surjective, as illustrated in Figure 2.11; this means that the function has a well-defined inverse.)

Suppose we want to compute the pdf of \(\mathbf{y} = f(\mathbf{x})\). The change of variables formula tells us that

\(p_y(\mathbf{y}) = p_x \left( f^{-1}(\mathbf{y}) \right) | \det [\mathbf{J}_{f^{-1}}(\mathbf{y})] |\) (2.257)

where \(\mathbf{J}_{f^{-1}}(\mathbf{y})\) is the Jacobian of the inverse mapping \(f^{-1}\) evaluated at \(\mathbf{y}\), and \(|\det \mathbf{J}|\) is the absolute value of the determinant of \(\mathbf{J}\). In other words,

\(\mathbf{J}_{f^{-1}}(\mathbf{y}) = \begin{pmatrix} \frac{\partial x_1}{\partial y_1} & \dots & \frac{\partial x_1}{\partial y_n} \\ \vdots & & \vdots \\ \frac{\partial x_n}{\partial y_1} & \dots & \frac{\partial x_n}{\partial y_n} \end{pmatrix}\) (2.258)