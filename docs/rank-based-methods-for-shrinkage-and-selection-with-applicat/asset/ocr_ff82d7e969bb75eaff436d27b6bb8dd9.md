# 2.6 Selection of Ridge Parameter \(\lambda_2\)

Naturally, questions arise as to how to set the proper value of \(\lambda_2\) and the nature of the trade-off as we shrink the estimates and their variances. In short, we are trading off bias against variance (i.e. under-fitting vs. over-fitting), and the proper value of \(\lambda_2\) is based on a desired prediction performance of our model. We now delve deeper into each question in the context of LS, which will be similar to rank. Note that an optimal \(\lambda_2\) value is unique to an estimator and generally cannot be compared or transferred between estimators. Additionally, the optimal \(\lambda_2\) usually lies in a range of values in practice, as opposed to being one unique value.

# 2.6.1 Quadratic Risk

We start by describing the infamous *bias-variance trade-off* which is at the heart of selecting the optimal \(\lambda_2\). We know the meaning of variance – the degree of uncertainty associated with an estimate. A working definition of the bias is the difference between the expected value of a given estimator, \(\mathbb{E}(\hat{\boldsymbol{\beta}}_n)\), and the true value, \(\boldsymbol{\beta}\). An estimator is said to be unbiased if \(\text{if } \mathbb{E}(\hat{\boldsymbol{\beta}}_n) = \boldsymbol{\beta}\). When we decrease the variance, we tend to increase the bias. We seek to balance the two by choosing the appropriate \(\lambda_2\).

It is well known that LSE provides the minimum variance of a set of linear unbiased estimates so it would appear that we cannot improve it. However, the variance may still be rather large if there is strong correlation between variables, i.e. a certain amount of collinearity exists among the columns of the design matrix. By applying a penalty function, we increase the bias and decrease the variance until the estimates minimize a given statistic.

Consider the use of the mean-square error (MSE) (Montgomery et al., 2012), also referred to as quadratic risk (and ADL\(_2\)-risk in Chapter 3), for the purposes of finding the optimal \(\lambda_2\) to balance the bias and variance. The MSE of the estimates given by

```
MSE(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}}) = \text{tr}(\text{Var}(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}})) + \text{bias}^2(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}})
```

where tr(\(\boldsymbol{M}\)) is the trace of some matrix, \(\boldsymbol{M}\), which involves adding up the diagonal terms of \(\boldsymbol{M}\), and let bias\(^2(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}}) = \text{bias}^\top(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}})\text{bias}(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}})\). The formulas for bias and variance for LS-ridge are given by

```
bias^2(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}}) = \lambda_2^2 \boldsymbol{\beta}^\top (\mathbf{X}^\top \mathbf{X} + \lambda_2 \mathbf{I}_p)^{-2} \boldsymbol{\beta},
```