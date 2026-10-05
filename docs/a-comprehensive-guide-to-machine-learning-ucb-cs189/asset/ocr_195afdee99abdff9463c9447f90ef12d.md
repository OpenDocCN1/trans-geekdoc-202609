# Chapter 4

# Gradient Descent, Newton’s Method

# 4.1 Nonlinear Least Squares

All models we've seen so far are **linear** in the parameters we're trying to learn. That is, our prediction $\hat{y} = f(x; \theta)$ is some linear function of the parameters $	heta$. For example, in OLS, $	heta = w$ and the residuals $r_i$ are computed by $y_i - w^T x_i$, which is linear in the components of $w$. In the case of least-squares polynomial regression, the predicted value is not a linear function of the input $x$, but it is still a linear function of the parameters.

However, we may have need for models which are nonlinear function of their parameters. We consider a motivating example first.

# Noisy Distance Readings

Suppose we want to estimate the 2D position $\theta =(\theta_1, \theta_2)$ of some entity, for example a robot. The information we have with noisy distance estimates $Y_i \in \mathbb{R}$ from sensors whose positions $X_i \in \mathbb{R}^2$ are fixed and known. If we assume i.i.d. Gaussian noise as usual, our statistical model has the form

```
$Y_i = ||X_i - \theta|| + N_i, \quad N_i \overset{iid}{\sim} \mathcal{N}(0, \sigma^2), \quad i=1, \dots, m$
```

where

```
$||X_i - \theta|| = \sqrt{(X_{i1} - \theta_1)^2 + (X_{i2} - \theta_2)^2}$
```

Here our prediction is

```
$$\hat{y} = f(x; \theta) = ||x - \theta||$
```

which is clearly not linear in $\theta$.

# Formulation from MLE

More generally, let us assume a model similar to the one above, but where $f$ is now arbitrary differentiable function and $\theta \in \mathbb{R}^d$;

```
$Y_i = f(X_i; \theta) + N_i, \quad N_i \overset{iid}{\sim} \mathcal{N}(0, \sigma^2), \quad i=1, \dots, m$
```

Note that this implies $Y_i | X_i \sim \mathcal{N}(f(X_i; \theta), \sigma^2)$.