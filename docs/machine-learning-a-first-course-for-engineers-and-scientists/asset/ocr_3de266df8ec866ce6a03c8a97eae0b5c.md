# 9 The Bayesian approach and Gaussian processes

Data: Training data $\mathcal{T} = \{x_i, y_i\}_{i=1}^n$, kernel $\kappa(x, \mathbf{x}')$, noise variance $\sigma^2$ and test input $\mathbf{x}_*$.
**Result:** Posterior predictive $p(\mathbf{x}_*|\mathbf{y}) = N(f(\mathbf{x}_*); m_*, s_*)$

1 Compute $m_*$ and $s_*$ according to (9.25)

# Method 9.2: Gaussian process regression.

# A nonparametric distribution over functions

![](bbox=[0.166, 0.237, 0.833, 0.413])

(a) The training data $\{x_i, y_i\}_{i=1}^n$ of a regression process is given to us.

(b) The underlying assumption when we regression is that there exists *some function* $f$, which describes the data $y_i = f(x_i) + e$. It is unknown, but the purpose of regression (no matter method is used) is to determine $f$.

![](bbox=[0.301, 0.533, 0.703, 0.653])

(c) The Gaussian process defines a distribution over $f$. We can condition on training data (that is, learning) and access for any input, say $x_*$ and $\mathbf{x}_*$. Then we make a prediction for $x_*$ and $\mathbf{x}_*$. The Gaussian process gives us a Gaussian distribution for $f(x_*)$ and $f(\mathbf{x}_*)$, illustrated by solid red lines. That distribution is heavily influenced by the choice of kernel, which is a design choice in the Gaussian process.

**Figure 9.8:** The Gaussian process defines a distribution over functions, which we can condition on training data and access in arbitrary points (such as $x_*$ and $\mathbf{x}_*$) to compute predictions.

As a supervised learning method we use the Gaussian process for making predictions, that is, computing the posterior predictive $p(f_*|\mathbf{y})$ or $p(y_*|\mathbf{y})$. However, unlike most other methods which only deliver a point predictive $	ilde{y}(\mathbf{x}_*)$, the posterior is a distribution. If we can compute the posterior predictive for any $\mathbf{x}_*$, the Gaussian process actually defines a *distribution over functions*, which we illustrate in Figure 9.8.

If we could derive a connection between Bayesian linear regression and L2 regularized regression, we also see a similar connection between the Gaussian process and kernel ridge regression. If we only consider the mean $m_*$ of the posterior, we recover kernel ridge regression. To take full advantage of the Bayesian perspective, we have to consider also the posterior predictive variance $s_*$. With most kernels, the predictive variance is smaller if there is a data point nearby,

Draft (April 30, 2021) of Machine Learning - A First Course for Engineers and Scientists. http://mlbook.org
Andreas Lindholm, Michaelisfter, Fredrik Strödin, and Thomas B. Schön (2021).