Exercise: An estimator is used on N = 5 datasets and each dataset produces a different estimate as follows: 0.25, 0.27, 0.29, 0.23, and 0.24. Estimate the variance.

Ans.: The mean is \(\overline{\hat{\theta}} = 0.256\). The unbiased estimate of variance uses \(N - 1\) instead of \(N\) as the divisor. Then, \(\text{Var}(\hat{\theta}) = \frac{1}{4} \sum_{i=1}^5 (\hat{\theta}_i - \overline{\hat{\theta}})^2 = ((0.25 - 0.256)^2 + (0.27 - 0.256)^2 + (0.29 - 0.256)^2 + (0.23 - 0.256)^2 + (0.24 - 0.256)^2)/4 = 0.00058\).

We generally seek estimators with the lowest QR and Eq. (6.3.4) tells us there will be a different bias–variance trade-off in each estimator. Ideally, we would like the bias to be 0 and the variance to be 0 but the equation does not permit this because if we reduce the variance, the bias will increase, and vice versa. The best we can do is strike a balance between the two quantities.

Example: The bias–variance trade-off was derived using a shortcut earlier in this section. The proper derivation proceeds as follows. Starting with the definition of the quadratic risk, we use the linearity of expectations to produce the desired form of the equation:

```
QR = E[(θ̂ - θ)²]
= E[(θ̂ - E[θ̂] + E[θ̂] - θ)²]
= E[(θ̂ - E[θ̂])² + 2(θ̂ - E[θ̂])(E[θ̂] - θ) + (E[θ̂] - θ)²]
= E[(θ̂ - E[θ̂])²] + 2E[(θ̂ - E[θ̂])(E[θ̂] - θ)] + E[(E[θ̂] - θ)²]
= E[(θ̂ - E[θ̂])²] + 2E[(θ̂ - E[θ̂])](E[θ̂] - θ) + E[(E[θ̂] - θ)²]
= var(θ̂) + 0 + bias²(θ̂)
= var(θ̂) + bias²(θ̂).
```

In the fifth line of the above derivation, the first term is the definition of the variance, the last term is the bias squared, and the middle term is 0. Since (E[θ̂] - θ) is a number, it can be moved outside the expectation of the middle term, and then we have that E[θ̂ - E[θ̂]]] = E[θ̂] - E[E[θ̂]] = E[θ̂] - E[θ̂] = 0. Note that the QR equation is true in the limit, but not necessarily at finite values of N.

# 6.4 Regularization with Ridge

The term regularization of a model refers to the adjustment of model parameters to obtain the lowest quadratic risk using the hyperparameter λ associated with a penalty function. First we develop a simple strategy in a well-defined context with closed-form expressions for the bias and variance. Then, based on this experience, we can formalize the procedure in a real-world setting for machine learning.

Our starting point is the least squares estimator,

```
\(\hat{\beta}^{LS} = (X^T X)^{-1} X^T y,\) (6.4.1)
```