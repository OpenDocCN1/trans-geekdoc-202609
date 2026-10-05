# 232 DATA SCIENCE

+   - for all $i, j \in [1, \dots, n], i 
eq j$, the $\epsilon_i$ are uncorrelated, $	ext{Cov}[\epsilon_i, \epsilon_j] = 0$;n- the regressors are non-random and observable;
- the regressors are not perfectly correlated with each other.

The ordinary least squares, or OLS, is constructed as follows: we aim to find such a $eta$ in

```
$y = Xeta + \epsilon, \quad (13.8)$
```

which will minimise a certain loss function of the residual $\hat{\epsilon} := y - \hat{y}$. We use the squared error, which we'll now call the residual sum of squares (RSS)

```
$RSS = \hat{\epsilon}^T\hat{\epsilon} = (y - X\hat{eta})^T(y - X\hat{eta}). \quad (13.9)$
```

We will refer to the estimate as $\hat{eta}$ that will give us the estimate of $y$,

```
$\hat{y} := X\hat{eta}. \quad (13.10)$
```

The OLS estimator is given as:

```
$\hat{eta} = (X^TX)^{-1}X^Ty. \quad (13.11)$
```

We can prove this by first rewriting the RSS:

```
$RSS = \hat{\epsilon}^T\hat{\epsilon} = (y - X\hat{eta})^T(y - X\hat{eta}) = y^Ty - 2y^TXeta + eta^TX^Teta. \quad (13.12)$
```

Using the denominator for vector-vector and scalar-by-vector derivatives,

```
$\nabla_{eta}RSS = \frac{\partial RSS}{\partial \beta} = -2X^Ty + 2X^TX\beta. \quad (13.13)$
```

When $
abla_{eta}RSS = 0$, we get $X^TX\hat{eta} = X^Ty$ (this is the so-called normal equation), we obtain the solution $eta = (X^TX)^{-1}X^Ty$. To check that this critical point is a minimum, we examine the Hessian matrix

```
$\frac{\partial}{\partial \beta} \left(\frac{\partial RSS}{\partial \beta}\right) = 2X^TX. \quad (13.14)$
```

If $X$ is full rank (i.e. has $p+1$ if we allow the intercept and $p$ if we don't; if $X$ is skinny or square), then $X^TX$ is positive definite and the critical point is indeed a minimum.

The important feature of the OLS estimator is that it is unbiased, i.e. conditional expectation of the estimator is its true value:

```
$E[\hat{eta} | X] = E[(X^TX)^{-1}X^Ty | X] \quad (13.15)$
```

```
= (X^TX)^{-1}X^TE[y | X] \quad (13.16)$
```

```
= (X^TX)^{-1}X^T\beta = \beta. \quad (13.17)$
```