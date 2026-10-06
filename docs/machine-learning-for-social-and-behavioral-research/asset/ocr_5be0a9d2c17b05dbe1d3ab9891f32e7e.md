# Regularized Regression

predictors, this is a manageable 32 models. However, for 20 requires running 1,048,576 models, and 100 predictors requires over a quintillion models (> 1e³⁰). This is simply not possible, or advisable, to attempt unless the number of variables is more manageable. Heuristic algorithms, as genetic algorithms, tabu search, or simulated annealing, have been proposed to overcome this limitation of subsets, these methods are often quite computationally intensive as well.

Although computationally burdensome, stepwise selection methods have a long history of use and abuse in the social and behavioral sciences. Most notably, the adaptive nature of the algorithms has a tendency to capitalize on change, if researchers try and interpret the p-values from the best fitting model. Used correctly, both backward and forward stepwise selection methods perform well in selecting close to the optimal number of predictors. However, confusion over proper use of this method (particularly that it is atheoretical technique), and the recent development of a host of more flexible techniques, cause us to not recommend its use. Instead, we discuss the use of regularization and how it can be applied in a number of ways to perform variable selection.

# 4.4.1 Regularization Formulation

Estimating coefficients in a regression model that are shrunken toward 0, relative to that of ordinary least squares, is called many names including shrinkage, regularization, or penalized estimation. This involves placing constraints (penalties) on the coefficients in a regression model. The two most common forms of penalized regression are the ridge (Hoeler & Kenyon, 1970) and the least absolute shrinkage and selection operator (lasso; Tibshirani, 1996). Both methods add a penalty to the ordinary least squares fit. Given an outcome $y$ and a matrix of predictors $X$, ordinary least squares estimation can be defined as minimizing the residual sum of squares (RSS),

```
RSS = \argmin_{i=1}^{N} \sum (y_i - \beta_0 - \sum_{j=1}^{P} x_{ij}\beta_j)^2, \quad (4.3)
```

where $b_0$ is the intercept, and $eta_j$ is the regression coefficient for $x_j$. In this, our aim is to minimize the discrepancy between our actual $(y_i)$ and the predicted outcome $(\hat{y}_i)$. Given that certain assumptions are met, the estimated coefficients $\hat{eta}_0$ and $\hat{eta}_1$ will be unbiased estimates of their population parameter counterparts. To perform regularization, we add a penalty term to the equation for the RSS that will bias the parameter towards 0. For ridge regularization, this is defined as