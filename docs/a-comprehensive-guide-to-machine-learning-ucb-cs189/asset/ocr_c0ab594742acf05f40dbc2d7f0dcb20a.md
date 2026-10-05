The maximum likelihood estimator is given by

```
$$\hat{	heta}_{MLE} = \arg\max_{\theta} \log P(y_1, \dots, y_m \mid x_1, \dots, x_m; \theta, \sigma)$$
= \arg\max_{\theta} \log \prod_{i=1}^{m} P(y_i \mid x_i; \theta, \sigma)$$
= \arg\max_{\theta} \sum_{i=1}^{m} \log P(y_i \mid x_i; \theta, \sigma)$$
= \arg\max_{\theta} \sum_{i=1}^{m} \log \left( \frac{1}{\sqrt{2\pi\sigma^2}} \exp \left( -\frac{(y_i - f(x_i; \theta))^2}{2\sigma^2} \right) \right)$$
= \arg\min_{\theta} \sum_{i=1}^{m} \left[ -\frac{1}{2}\log(2\pi\sigma^2) - \frac{1}{2\sigma^2}(y_i - f(x_i; \theta))^2 \right]$
```

Observe the objective function is a sum of squared residuals as we've seen before, even though the function $f$ is nonlinear in general. For this reason the method is called **nonlinear least squares**.

Unfortunately, there is no closed-form solution for $\hat{	heta}_{MLE}$ in general. Later we will see an iterative method for computing it.

# Solutions to Nonlinear Least Squares

Motivated by the MLE formulation, we consider the following optimization problem:

```
$$\min_{\theta} \ell_S(\theta) = \min_{\theta} \sum_{i} (y_i - f(x_i; \theta))^2$$
```

One way to minimize a function is to use calculus. We know that the objective function at any minimum must be zero, if it isn't, we can take a sufficiently small step in the direction of the negative gradient that the objective function's value will be reduced.

Thus, the **first-order optimality condition** that needs to be satisfied:

```
$$\nabla_{\theta}\ell_{LS} = 2 \sum_{i} (y_i - f(x_i; \theta))\nabla_{\theta}f(x_i; \theta) = 0$$
```

In compact matrix notation:

where

```
$F(\	heta) = \begin{bmatrix} f(x_1; \theta) \ \vdots \ f(x_n; \theta) \end{bmatrix}$$
$$J(\	heta)^T(Y - F(\theta)) = 0$$
```