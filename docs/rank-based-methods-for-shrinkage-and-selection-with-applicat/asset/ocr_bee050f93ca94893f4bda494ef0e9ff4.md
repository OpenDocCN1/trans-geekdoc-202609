The numerical optimization technique used in logistic regression is usually some form of gradient descent. We will describe only the simplest form for our purposes here. Basically, we compute the loss function using an initial guess, \(\boldsymbol{\beta}^{(0)}\), and then take a step in the gradient direction to reduce the value of \(J(\boldsymbol{\beta})\). The process is repeated until the minimum is found. This iterative method requires partial derivatives of \(J(\boldsymbol{\beta})\) in Eq. (11.3.10) with respect to \(\boldsymbol{\beta}\).

Consider again the case where there is only one observation, \(\boldsymbol{x}\), and one known binary response, y. Starting with the loss function, \(J(\boldsymbol{\beta})\), we can apply the chain rule to obtain the needed gradients. For some parameter, \(\beta_j\), we have that

```
\(\frac{\partial J(\boldsymbol{\beta})}{\partial \beta_j} = \frac{\partial J(y, p(\boldsymbol{x}))}{\partial p(\boldsymbol{x})} \frac{\partial p(\boldsymbol{x})}{\partial \beta_j} = (p(\boldsymbol{x}) - y)x_j.\)
```

This comes from the partial derivative in the first term,

```
\(\frac{\partial J(y, p(\boldsymbol{x}))}{\partial p(\boldsymbol{x})} = -\frac{y}{p(\boldsymbol{x})} + \frac{1-y}{1-p(\boldsymbol{x})},\)
```

and the second term, which involves the partial derivative of the sigmoid function,

```
\(\frac{\partial p(\boldsymbol{x})}{\partial \beta_j} = \frac{\exp(-\boldsymbol{x}^{\text{T}}\boldsymbol{\beta})}{(1+\exp(-\boldsymbol{x}^{\text{T}}\boldsymbol{\beta}))^2} x_j = p(\boldsymbol{x})(1-p(\boldsymbol{x}))x_j.\)
```

Next, consider the case with \(n\) observations. We have to sum up such quantities in Eq. (11.3.12) associated with each observation for every parameter. Combining the steps above, an update equation for each \(\beta_j, j = 0, ..., p\), to compute the next iteration values is given by

```
\(\beta_j^{(t+1)} = \beta_j^{(t)} - \ell \times \frac{\partial J(\boldsymbol{\beta})}{\partial \beta_j} = \beta_j^{(t)} - \ell \sum_{i=1}^n (p(\boldsymbol{x}_i) - y_i)x_{ij},\)
```

where \(\ell\) is a tuning parameter called the learning rate that controls the step size needed in each iteration to produce a smooth yet rapid convergence to the global solution. This is for one observation only.

The equations can be formulated conveniently using matrix notation as follows. We start with \(\boldsymbol{X}\), an \(n \times (p+1)\) matrix. The \(n\) logit values are computed using an initial \(\boldsymbol{\beta}_n^{(0)}\) value as

```
\(\boldsymbol{z} = \boldsymbol{X}\boldsymbol{\beta}_n^{(0)}.\)
```

The \(n\) predicted responses are computed using the sigmoid function

```
\(p(\boldsymbol{X}) = \frac{1}{1 + \exp(-\boldsymbol{z})}.\)
```