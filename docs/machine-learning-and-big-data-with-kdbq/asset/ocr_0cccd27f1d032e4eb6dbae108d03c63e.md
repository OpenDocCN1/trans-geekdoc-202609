# Eigensystem and PCA 343

where $\mathbf{x}_i$ is the $i$-th row of the data matrix $\mathbf{X}$ written as a column vector and $ar{\mathbf{x}}$ is the sample mean, also written as a column vector. We are still modelling $\mathbf{x}_i$ as a random variable, but now we have a data sample; for a concrete data sample (a concrete data matrix $\mathbf{X}$), we could obtain a specific matrix $\mathbf{Q}$ and use it as an estimator of the covariance matrix $	ext{Cov}[\mathbf{x}]$ of the hypothetical random variable $\mathbf{x}$.

Thus the sample covariance matrix is a generalised of the sample covariance, whereas the covariance matrix is a generalised of the variance of a random variable. However, people often use the term “covariance matrix” for both these things, so beware of the confusion!

The sample covariance matrix is symmetric and positive semidefinite. We will leave it to the reader to construct proof of this assertion. Please keep in mind that we use sums over all realisations in the sample data $X$. Another important feature of the sample covariance matrix is to be an unbiased estimator of the true covariance matrix $	ext{Cov}[\mathbf{x}] , \mathbf{x}]$. This assertion follows from:

```
$$\mathbb{E}[\mathbf{Q}] = \frac{1}{n-1} \sum_{i=1}^n (\mathbf{x}_i - ar{\mathbf{x}})(\mathbf{x}_i - ar{\mathbf{x}})^T$\n= \frac{1}{n-1} \sum_{i=1}^n [\mathbf{x}_i\mathbf{x}_i^T - nar{\mathbf{x}}\mathbf{x}_i^T - \mathbf{x}_iar{\mathbf{x}}^T + nar{\mathbf{x}}ar{\mathbf{x}}^T]$\n= \frac{1}{n-1} \sum_{i=1}^n \mathbb{E}[\mathbf{x}_i\mathbf{x}_i^T] - n\mathbb{E}[ar{\mathbf{x}}ar{\mathbf{x}}^T]$\n= \frac{1}{n-1} \sum_{i=1}^n (\boldsymbol{\Sigma} + \boldsymbol{\mu}\boldsymbol{\mu}^T) - n (\frac{1}{n} \boldsymbol{\Sigma} + \boldsymbol{\mu}\boldsymbol{\mu}^T)$$\n= \frac{1}{n-1} [n\boldsymbol{\Sigma} + n\boldsymbol{\mu}\boldsymbol{\mu}^T - \boldsymbol{\Sigma} - n\boldsymbol{\mu}\boldsymbol{\mu}^T] = \boldsymbol{\Sigma}$
```

So $\mathbf{Q}$ is an unbiased estimator of $oldsymbol{\Sigma}$.

Further, closely related to the covariance matrix is the correlation matrix. The correlation-relation, matrix of Pearson product-moment correlation coefficients between each element in the relation vector, $\mathbf{x}$, can be written as:

```
$$\text{Cor}[\mathbf{x}] = (\boldsymbol{\Sigma}^{(	ext{diag})})^{-\frac{1}{2}} \boldsymbol{\Sigma} (\boldsymbol{\Sigma}^{(	ext{diag})})^{-\frac{1}{2}}$
```

where $oldsymbol{\Sigma}^{(	ext{diag})}$ is the matrix of the diagonal elements of $oldsymbol{\Sigma}$, i.e. a diagonal matrix of the variances of $\mathbf{x}$, for each $i$-th element of $\mathbf{x}$. The sample correlation matrix is obtained accordingly from the sample covariance matrix. By construction, the correlation matrix and the sample covariance matrix are also symmetric and positive semidefinite. Furthermore, all diagonal entries in these matrices are equal to 1. If the variances of all elements of $\mathbf{x}$ were equal to 1, then the covariance matrix would be equal to the variance matrix. The correlation matrix is thus a rescaling of the covariance matrix forcing all element variances to be equal.

It is worth establishing a connection between the sample covariance matrix and Gram matrix, $(\mathbf{X}^T)\mathbf{X}$. In particular, when the data is centered $(X = \mathbf{X}^T)$, the unbiased