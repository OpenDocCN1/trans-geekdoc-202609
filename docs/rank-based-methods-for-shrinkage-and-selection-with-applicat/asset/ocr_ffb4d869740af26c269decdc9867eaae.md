# Figure 11.1 Sigmoid function.

![](bbox=[0.555, 0.113, 0.892, 0.223])

$$ \log \frac{p(\boldsymbol{x}_i)}{1 - p(\boldsymbol{x}_i)} = \beta_0 + x_{i1}\beta_1 + ... + x_{ip}\beta_p. $$ (11.3.2)

The left-hand side is referred to as the logit link function, z, also known as the logarithm of the odds,

$$ z = \log \frac{p(\boldsymbol{x}_i)}{1 - p(\boldsymbol{x}_i)}. $$ (11.3.3)

Suppose we find estimates $\hat{\boldsymbol{\beta}}$ using a suitable estimator and want to predict the probability, $\hat{p}(\boldsymbol{x})$, of some new $\boldsymbol{x}$ that it has a response of $Y = 1$. This can be done in two steps. We first calculate $z$ using

$$ \hat{z} = \boldsymbol{x}^{\top}\hat{\boldsymbol{\beta}} = \hat{\beta}_0 + \hat{\beta}_1 x_1 ... , \hat{\beta}_p x_p. $$ (11.3.4)

Second, we predict the probability from the sigmoid function

$$ \hat{p}(\boldsymbol{x}) = \frac{1}{1 + \exp(-\boldsymbol{x}^{\top}\hat{\boldsymbol{\beta}})} = \frac{1}{1 + \exp(-\hat{z})} = p(\hat{z}). $$ (11.3.5)

It is instructive to examine the sigmoid function in more detail. A graph of the function $p(z)$ is shown in Figure 11.1. Note that for large positive values of z, the probability asymptotically approaches 1, whereas for large negative values it asymptotically approaches 0. The ground truth (i.e. true value) of the dependent variable $y$ is either 0 or 1 for any given $\boldsymbol{x}$. However, the predicted value $\hat{p}(\boldsymbol{x})$ lies between 0 and 1 but does not reach either value for reasons that should be clear from Eq. (11.3.5). For binary classification, the predicted value, $\hat{p}(\boldsymbol{x})$, is compared to 0.5. If $\hat{p}(\boldsymbol{x}) > 0.5$, we predict 1, whereas if $\hat{p}(\boldsymbol{x}) < 0.5$, we predict 0.

Alternatively, we could base the decision of 1 or 0 on a sign test using $\hat{z} = \boldsymbol{x}^{\top}\hat{\boldsymbol{\beta}}$. Conceptually, z represents a line or hyperplane that separates 0s from 1s. We note that $\hat{\beta}_0$ functions as a bias term in this expression. In other words, if $\boldsymbol{x} = 0$ then either $\hat{\beta}_0 > 0$ or $\hat{\beta}_0 < 0$ so there is a built-in bias due to $\hat{\beta}_0$. It effectively shifts the p-dimensional hyperplane in one direction or the other by an amount equal to the bias term. The rest of the coefficients, $\hat{\beta}_1, ..., \hat{\beta}_p$, establish the actual hyperplane. The linear boundary in p dimensions (i.e. the hyperplane boundary) is positioned where