# 8 Nonlinear input transformations and kernels

The assumption that the model is linear in both parameters and features, $\theta^T \phi(\mathbf{x})$, is indeed crucial for Theorem 8.1. That is not an issue when we consider models of linear regression type, but of model not all to apply to, for example, logistic regression we find a linear formulation of such model. Not all models are possible to formulate as linear, but logistic regression can be treated of (3.29a) to be understood as a linear model predicting the so-called log-odds, $\theta^T \phi(\mathbf{x}) = \ln\left(\frac{p(\mathbf{x})}{1-p(\mathbf{x})}\right)$,$, and the representer theorem is furthermore applicable to it. Furthermore support vector classification is also a linear model if we consider the function $c(\mathbf{x}) = e^{\theta^T \phi(\mathbf{x})}$ rather than the predicted label $\hat{y}(\mathbf{x})$.

# 8.B Derivation of support vector classification

We will derive (8.35) from (8.34),

```
minimize_{\theta} \frac{1}{n} \sum_{i=1}^n \max\0, 1-y_i\theta^T \phi(\mathbf{x}_i)\} + \lambda|\theta||^2.
```

by first re-introduce it into an equivalent formulation using slack variables $\xi = [\xi_1...\xi_n]^T$,

```
minimize_{\theta} \frac{1}{n} \sum_{i=1}^n \xi_i^2 + \lambda|\theta||^2, (8.39a)
subject to   \xi_i \ge 1-y_i\theta^T \phi(\mathbf{x}_i), (8.39b)
\xi_i \ge 0. (8.39c)
```

The Lagrangian for (8.39) is then

```
$L(\theta, \xi, \gamma) = \frac{1}{n} \sum_{i=1}^n \xi_i^2 + \lambda|\theta||^2 - \sum_{i=1}^n \beta_i(y_i+\theta^T \phi(\mathbf{x}_i)-1) - \sum_{i=1}^n \gamma_i\xi_i$ (8.40)
```

with Lagrange multipliers $\beta_i \ge 0$ and $\gamma_i \ge 0$. According to Lagrange duality, instead of solving (8.34) we can minimize (8.40) with respect to $\theta$ and maximize it with respect to $\beta$ and $\gamma$. Two necessary conditions for optimality of (8.40) are

```
$$\frac{\partial L}{\partial \theta}(\theta, \xi, \gamma) = 0,$ (8.41a)
$\frac{\partial L}{\partial \xi}(\theta, \xi, \gamma) = 0.$ (8.41b)
```

In more detail (8.41a) gives using that $|\theta||^2 = \theta^T \theta$, and hence $\frac{\partial}{\partial \theta},\theta|^2=2\theta$

```
$$\theta = \frac{1}{2\lambda} \sum_{i=1}^n y_i\beta_i\phi(\mathbf{x}_i),$ (8.41c)
```

and (8.41b) gives

```
$$\gamma_i = \frac{1}{n}-\beta_i,$ (8.41d)
```

Inserting (8.41c) and (8.41d) into (8.40) and scaling it with $\frac{1}{2}$, we seek to maximize

```
$$\bar{L}(\beta) = \sum_{i=1}^n \frac{1}{2\lambda}y_i\beta_i^2 - \sum_{i,j=1}^n \frac{1}{2}\frac{\beta_i\beta_j}{4\lambda^2}y_iy_j\phi^T(\mathbf{x}_j).$ (8.42)
```

Draft (April 30, 2021) of Machine Learning - A First Course for Engineers and Scientists. https://mmlbook.org
* Andreas Lindholm, Nils Wahlström, Fredrik Linde, and Thomas B. Schön. 2021.