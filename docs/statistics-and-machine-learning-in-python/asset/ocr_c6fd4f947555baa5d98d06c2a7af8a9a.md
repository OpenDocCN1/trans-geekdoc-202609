contribution to all classes sum to one $\sum_k p(k\mid x_i)=1$. This contribution is the conditional probability of class $k$ given $x$: $p(k\mid x)$ (sometimes called the posterior). It can be computed using Bayes’ rule:

$p(k\mid x)=\frac{p(x\mid k)p(k)}{p(x)}$  (11.2)
$=\frac{\mathcal{N}(x\mid \mu_k,\Sigma_k)p(k)}{\sum_{k=1}^{K}\mathcal{N}(x\mid \mu_k,\Sigma_k)p(k)}$  (11.3)

Since the class parameters, $p(k)$, $\mu_k$ and $\Sigma_k$, depend on the responsibilities $p(k\mid x)$ and the responsibilities depend on class parameters, we need a two-step iterative algorithm: the expectation-maximization (EM) algorithm. We discuss this algorithm next.

# 11.3.1 The expectation-maximization (EM) algorithm for Gaussian mixtures

Given a Gaussian mixture model, the goal is to maximize the likelihood function with respect to the parameters (comprised of the means and covariances of the components and the mixing coefficients).

Initialize the means $\mu_k$, covariances $\Sigma_k$ and mixing coefficients $p(k)$

+   1. **E step.** For each sample $i$, evaluate the responsibilities for each class $k$ using the current parameter values
+   
+   $p(k\mid x_i)=\frac{\mathcal{N}(x_i\mid \mu_k,\Sigma_k)p(k)}{\sum_{k=1}^{K}\mathcal{N}(x_i\mid \mu_k,\Sigma_k)p(k)}$
+   
+   2. **M step.** For each class, re-estimate the parameters using the current responsibilities
+   
+   $\mu_k^{\text{new}}=\frac{1}{N_k}\sum_{i=1}^{N}p(k\mid x_i)x_i$  (11.4)
+   
+   $\Sigma_k^{\text{new}}=\frac{1}{N_k}\sum_{i=1}^{N}p(k\mid x_i)(x_i-\mu_k^{\text{new}})(x_i-\mu_k^{\text{new}})^T$  (11.5)
+   
+   $p^{\text{new}}(k)=\frac{N_k}{N}$  (11.6)
+   
+   3. Evaluate the log-likelihood
+   
+   $\sum_{i=1}^{N}\ln\left\{\sum_{k=1}^{K}\mathcal{N}(x\mid \mu_k,\Sigma_k)p(k)\right\}$

and check for convergence of either the parameters or the log-likelihood. If the convergence criterion is not satisfied return to step 1.

```
import numpy as np
from sklearn import datasets
import matplotlib.pyplot as plt
import seaborn as sns  # nice color
import sklearn
from sklearn.mixture import GaussianMixture
```