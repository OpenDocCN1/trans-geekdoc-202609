describe the cross-section of expected returns, and we compare it, in terms of pricing performance, with SDFs that are sparse in characteristics.

To construct the PC factors, we use the eigendecomposition of the factor covariance matrix,

$$\mathbf{\Sigma}=\mathbf{Q}\mathbf{\Lambda}\mathbf{Q}'\quad\text{with}\quad\mathbf{\Lambda}=\operatorname{diag}(\lambda_1,\lambda_2,\dots,\lambda_H),\qquad(4.5)$$

where $\mathbf{Q}$ is the matrix of eigenvectors of $\mathbf{\Sigma}$, and $\mathbf{\Lambda}$ is the diagonal matrix of eigenvalues ordered in decreasing magnitude. Using the eigenvectors as portfolio weights, we obtain the PC factors

$$p_t=\mathbf{Q}'f_t.\qquad(4.6)$$

Using all PCs, and with knowledge of population moments, we could express the SDF as

$$M_t=1-b_p'(p_t-\mathbb{E}[p_t]),\qquad\text{with}\quad b_p=\mathbf{\Lambda}^{-1}\mathbb{E}[p_t].\qquad(4.7)$$

# 4.2 Supervised Learning Approach

We now describe the supervised learning approach to estimate the SDF parameter vector $\boldsymbol{b}$ (or $b_P$ in the case where we use the PC factors). The method is a variant of the Bayesian regression that we discussed in Chapters 2 and 3.

Consider a sample with size $T$. We denote

$$\bar{\boldsymbol{\mu}}=\frac{1}{T}\sum_{t=1}^{T}f_t,\qquad(4.8)$$

$$\bar{\mathbf{\Sigma}}=\frac{1}{T}\sum_{t=1}^{T}(f_t-\bar{\boldsymbol{\mu}})(f_t-\bar{\boldsymbol{\mu}})',\qquad(4.9)$$

A natural, but naïve, estimator of the coefficients $\boldsymbol{b}$ of the SDF in (4.1) could be constructed based on the sample moment conditions

$$\bar{\boldsymbol{\mu}}-\frac{1}{T}\sum_{t=1}^{T}f_t=0,\qquad(4.10)$$

$$\frac{1}{T}\sum_{t=1}^{T}M_t(\hat{\boldsymbol{b}},\bar{\boldsymbol{\mu}})f_t=0.\qquad(4.11)$$

Solving for $\hat{\boldsymbol{b}}$, the resulting estimator is the sample version of (4.3):

$$\hat{\boldsymbol{b}}=\bar{\mathbf{\Sigma}}^{-1}\bar{\boldsymbol{\mu}}.\qquad(4.12)$$