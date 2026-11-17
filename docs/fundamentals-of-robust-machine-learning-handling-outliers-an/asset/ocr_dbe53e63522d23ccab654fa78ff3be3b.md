where the loss term is

```
\(\rho_H(r_i) = \left\{ \begin{array}{ll} r_i^2 / 2 & \text{if } |r_i| \le \delta \\ \delta \left( |r_i| - \frac{\delta}{2} \right) & \text{if } |r_i| > \delta \end{array} \right.\)
```

One issue to resolve when using Huber is that of specifying the value of \(\delta\). In many datasets with differing number of outliers, the value of \(\delta\) cannot be determined _a priori_. If there are no outliers, a large value of \(\delta\) is appropriate (between 4 and 5) whereas for cases with lots of outliers, a smaller value is warranted (between 0.1 and 0.5). However, as we saw in Chapter 3, choosing small values of \(\delta\) may lead to optimization problems. Therefore, it is common practice to use a fixed value of \(\delta = 1.345\) with penalty functions.

**Exercise:** In a linear regression problem, let _d_ = 2. The two parameters of interest are \(\beta_1\) and \(\beta_2\). Write the ridge penalty function in terms of these two parameters with a constraint _c_ applied.

**Ans.:** The expanded form of the ridge penalty with the constraint is

```
\(P(\beta) = \beta_1^2 + \beta_2^2 \le c.\)
```

For a two-dimensional case, the constrained optimization problem of Eq. (5.2.3) can be written as

```
\(\text{minimize}_{\beta \in \mathbb{R}^2} \sum_{i=1}^n \rho(\beta) \quad \text{subject to} \quad \beta_1^2 + \beta_2^2 \le c.\)
```

This implies that as _c_ decreases (which is equivalent to increasing \(\lambda\)), the two parameters are constrained to live in a tighter and tighter _circle_ around the origin. Therefore, the parameters will shrink in value as the constraint _c_ is made smaller.

# ## 5.4 LASSO Penalty

The ridge penalty is based on the _L_<sub>2</sub>-norm so it is natural to consider devising a penalty based on the _L_<sub>1</sub>-norm. Such a penalty function is referred to as LASSO (least absolute shrinkage and selection operator). The objective function combines the least squares loss with the LASSO penalty and is given by

```
\(J^{LS-LASSO}(\beta) = \frac{1}{2} \sum_{i=1}^n r_i^2 + \lambda \sum_{j=1}^d |\beta_j|.\)
```

An interesting and unique property of LASSO is that it can set some parameters to 0 effectively removing them from the regression procedure. This can be useful in many different data science problems, but particularly in high-dimensional problems with a large number of variables. In those situations, many of the variables do not affect the response and therefore can be set to 0. This process of removing unimportant variables is sometimes called _feature selection_ in machine learning.

The objective function with the log-cosh loss and LASSO is given by

```
\(J^{LC-LASSO}(\beta) = \frac{1}{a} \sum_{i=1}^n \log(\cosh(ar_i)) + \lambda \sum_{j=1}^d |\beta_j|.\)
```