# 15 Generalized linear models

# 15.1 Introduction

A generalized linear model or GLM [MN89] is a conditional version of an exponential family distribution (Section 2.4). More precisely, the model has the following form:

```
p(y_n|\mathbf{x}_n, \mathbf{w}, \sigma^2) = \exp \left[ \frac{y_n \eta_n - A(\eta_n)}{\sigma^2} + \log h(y_n, \sigma^2) \right]
```

where \(\eta_n = \mathbf{w}^\mathsf{T} \mathbf{x}_n\) is the natural parameter for the distribution, \(A(\eta_n)\) is the log normalizer, \(\mathcal{T}(y) = y\) is the sufficient statistic, and \(\sigma^2\) is the dispersion term. Based on the results in Section 2.4.3, we can show that the mean and variance of the response variable are as follows:

```
\mu_n \triangleq \mathbb{E} \left[ y_n | \mathbf{x}_n, \mathbf{w}, \sigma^2 \right] = A'(\eta_n) \triangleq \ell^{-1}(\eta_n)\\ \mathbb{V} \left[ y_n | \mathbf{x}_n, \mathbf{w}, \sigma^2 \right] = A''(\eta_n) \sigma^2
```

We will denote the mapping from the linear inputs to the mean of the output using \(\mu_n = \ell^{-1}(\eta_n)\), where the function \(\ell\) is known as the **link function**, and \(\ell^{-1}\) is known as the **mean function**. This relationship is usually written as follows:

```
\ell(\mu_n) = \eta_n = \mathbf{w}^\mathsf{T} \mathbf{x}_n
```

GLMs are quite limited in their predictive power, due to the assumption of linearity (although we can always use basis function expansion on \(\mathbf{x}_n\) to improve the flexibility). However, the main use of GLMs in the statistics literature is not for prediction, but for hypothesis testing, as we explain in Section 3.10.3. This relies on the ability to compute the posterior, \(p(\mathbf{w}|\mathcal{D})\), which we discuss in Section 15.1.4. We can use this to draw conclusions about whether any of the inputs (e.g., representing different groups) have a significant effect on the output.

# 15.1.1 Some popular GLMs

In this section, we give some examples of widely used GLMs.

# 15.1.1.1 Linear regression

Recall that linear regression has the form

```
p(y_n|\mathbf{x}_n, \mathbf{w}, \sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp(-\frac{1}{2\sigma^2}(y_n - \mathbf{w}^\mathsf{T} \mathbf{x}_n)^2)
```