changing the diagonal values of the covariance matrix, that is, make it diagonally dominant. But how can one do that without violating the original LS problem? The key is that we are mostly interested in the prediction error on test sets so we are permitted to do anything sensible to fine-tune the model parameters as long as the prediction error of the resulting model is reduced.

The most well-known modification of the LS formation is

```
\(\hat{\beta}^{\text{LS-ridge}} = (X^T X + \lambda I)^{-1} X^T y\), (5.2.2)
```

where **_I_** is the identity matrix and \(\lambda\) is a tuning hyperparameter that is adjusted to make the matrix invertible. In this new formulation, all we have done is add \(\lambda\) to the diagonals of \(X^T X\) such that the matrix becomes diagonally dominant and hence invertible for a sufficiently large value of \(\lambda\). The problem of multicollinearity can be mitigated by virtue of this simple change in formulation. However, this adjustment will not produce the same set of LS estimates as in Eq. (5.2.1) and, as a result, it is given a different name, specifically ridge regression.

A natural question to ask is, what happens to the estimates as a function of \(\lambda\)? In fact, the **estimates will be shrinking as** \(\lambda\) **is increased** relative to the LS estimates. The use of ridge acts as a penalty on the original LS formulation since it reduces the estimates. The follow-up question then arises regarding the quality of the estimates if the new ridge formulation is used. Is it better or worse? The answer lies in the fact that **the variance is reduced and the bias is increased as** \(\lambda\) **is increased**. Then \(\lambda\) is chosen to balance the two such that the prediction error is minimized. Hence, an overall benefit can be achieved using ridge. The procedure used to find the best \(\lambda\) is called _regularization_. With these basic facts understood, it is appropriate to take a deeper dive into penalty estimation.

# 5.2.2 Penalized Loss Functions

In machine learning, the closed-form LS solution is rarely used because it is not suitable for large problems, the matrix may not be invertible and other penalty functions are difficult to incorporate. Instead, the standard approach is to apply gradient descent to some objective function and minimize it to obtain the model. A number of loss functions of the form \(\sum_{i=1}^n \rho(\beta)\) were presented in Chapters 2 and 3. With that in mind, we need to create an objective function composed of a loss function and a penalty function. In this context, it is better to view penalty estimation as a constrained minimization problem as follows:

```
\(\text{minimize}_{\beta \in \mathbb{R}^d} \sum_{i=1}^n \rho(\beta) \quad \text{subject to} \quad P(\beta) \le c.\) (5.2.3)
```

That is, the original loss function is penalized by a function \(P(\beta)\) which is constrained by \(c\). The constant \(c\) limits the range of the possible solutions during optimization. To apply the constraint in the form of a single objective function, we can reformulate the problem as a Lagrange multiplier as follows:

```
\(J^{\text{loss-penalty}}(\beta) = \sum_{i=1}^n \rho(\beta) + \lambda P(\beta) = \sum_{i=1}^n \rho(\beta) + \lambda \sum_{j=1}^d p(\beta_j).\) (5.2.4)
```

In the above, the first term is the loss function and the second term is the penalty function. In linear regression, the loss function can be seen as a “coarse-grain tuner” because it broadly adjusts the model to fit the data. The penalty function acts as a “fine-grain tuner” by making more subtle adjustments to