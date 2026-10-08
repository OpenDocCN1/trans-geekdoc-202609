of the current model. This framework covers new data arriving through the pipeline. It also gives the possibility to add new basis functions to the model on the fly, incorporating a mechanism to avoid collinearity.

# 8.14 Gaussian Process

In the preceding sections, we have chosen the function space in which our model lies by specifying a finite dictionary of basis functions, and the model $f(\mathbf{x})$ being a linear combination of these basis functions. This is restrictive. The aim of this section is to look for the model in the unbelievably infinite space of functions. More specifically the model is a distribution over this space.

In the Dirichlet process, where we were confronted with infinitely many possibilities for the cluster parameters, the infinity is dealt with, because only a finite set of data is seen each maximum number of necessary parameters. All other infinitely possibilities are given one probability. Similarly here, infinitely many are manageable, since only a finite set of data is seen.

A stochastic process is a probability distribution over functions $f(\mathbf{x})$, where $\mathbf{x} \in \mathbb{R}^d$, such that when evaluated at any arbitrary set of points $\mathbfmathbfx}_1, \dots, \mathbf{x}_N$, the values $f(\mathbf{x}_1), \dots, f(\mathbf{x}_N)$ follow a specific joint, multivariate distribution. If this distribution is a normal, then it is known as a *Gaussian random field*. If $D=2$, it is also known as

Recall that so model was specified as

```
$f(\mathbf{x}) = \sum_{m=1}^{M} c_m d_m(\mathbf{x}).$$
```

Let $\mathbf{x}_1, \dots, \mathbf{x}_N$ be any set of points, and denote $f(\mathbf{x}_1), \dots, f(\mathbf{x}_N)^T$ by $f$. Then

```
$\mathbf{f} = \mathbf{D}\mathbf{c}.$
```

where $\mathbf{D}$ is the design matrix, where each column is a function evaluated at $\mathbf{x}_1, \dots, \mathbf{x}_N$ and $\mathbfmathbf{c}$ is the vector of coefficients as. The assumption is that $\mathbf{c}$ is normal. Since $f$ is a linear transformation of $\mathbf{c}$, it has a normal distribution. Our models so far are Gaussian processes.

The prior assumption is that $\mathbf{c}$ has zero mean, and hence $f$ also has zero mean. We consider the two cases, where the prior covariance matrix of $\mathbf{c}$ is either $\alpha^{-1}\mathbf{I}$, that is all coefficients have the same precision $\alpha$, or the diagonal-matrix $\mathbf{A}^{-1}$, where each coefficient has its own precision. The covariance of $f$ is then

```
$\text{var}[\mathbf{f}] = \mathbf{E}[\mathbf{f}\mathbf{f}^T] = \mathbf{E}[\mathbf{D}\mathbf{c}\mathbf{c}^T\mathbf{D}^T] = \mathbf{D}\mathbf{E}[\mathbf{c}\mathbf{c}^T]\mathbf{D}^T = \begin{cases} \alpha^{-1}\mathbf{DD}^T \ \mathbf{A}^{-1}\mathbf{DD}^T. \end{cases}$
```

Note that the covariance matrix of $f$ depends on the set $\mathbf{x}_1, \dots, \mathbf{x}_N$ via the design matrix. Different sets of points will give different