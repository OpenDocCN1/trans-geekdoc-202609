where IW is the inverse Wishart distribution. Unfortunately, $\boldsymbol{\mu}$ and $\boldsymbol{\Sigma}$ appear together in a non-factorized way in the likelihood in Eq. (7.117) (see the first exponent term), so the factored prior in Eq. (7.118) is not conjugate to the likelihood.

The above prior is sometimes called **conditionally conjugate**, since both conditionals, $p(\boldsymbol{\mu}\mid\boldsymbol{\Sigma})$ and $p(\boldsymbol{\Sigma}\mid\boldsymbol{\mu})$, are individually conjugate. To create a fully conjugate prior, we need to use a prior where $\boldsymbol{\mu}$ and $\boldsymbol{\Sigma}$ are dependent on each other. We will use a joint distribution of the form $p(\boldsymbol{\mu},\boldsymbol{\Sigma})=p(\boldsymbol{\mu}\mid\boldsymbol{\Sigma})p(\boldsymbol{\Sigma})$. Looking at the form of the likelihood equation, Eq. (7.117), we see that a natural conjugate prior has the form of a **Normal-inverse-Wishart** or **NIW** distribution, defined as follows:

$$\operatorname{NIW}(\boldsymbol{\mu},\boldsymbol{\Sigma}\mid\tilde{\mathbf m},\tilde{\kappa},\tilde{\nu},\tilde{\mathbf S}) \triangleq \mathcal N\left(\boldsymbol{\mu}\mid\tilde{\mathbf m},\frac{1}{\tilde{\kappa}}\boldsymbol{\Sigma}\right)\times\operatorname{IW}(\boldsymbol{\Sigma}\mid\tilde{\mathbf S},\tilde{\nu})$$

$$=\frac{1}{Z_{\mathrm{NIW}}}|\boldsymbol{\Sigma}|^{-\frac{1}{2}}\exp\left(-\frac{\tilde{\kappa}}{2}(\boldsymbol{\mu}-\tilde{\mathbf m})^\top\boldsymbol{\Sigma}^{-1}(\boldsymbol{\mu}-\tilde{\mathbf m})\right)$$

$$\times |\boldsymbol{\Sigma}|^{-\frac{\tilde{\nu}+D+1}{2}}\exp\left(-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Sigma}^{-1}\tilde{\mathbf S})\right)$$

where the normalization constant is given by

$$Z_{\mathrm{NIW}} \triangleq 2^{\tilde{\nu}D/2}\Gamma_D(\tilde{\nu}/2)(2\pi/\tilde{\kappa})^{D/2}|\tilde{\mathbf S}|^{-\tilde{\nu}/2}$$

The parameters of the NIW can be interpreted as follows: $\tilde{\mathbf m}$ is our prior mean for $\boldsymbol{\mu}$, and $\tilde{\kappa}$ is how strongly we believe this prior; $\tilde{\mathbf S}$ is (proportional to) our prior mean for $\boldsymbol{\Sigma}$, and $\tilde{\nu}$ is how strongly we believe this prior.³

# Posterior

To derive the posterior, let us define the sum-of-squares matrix

$$\mathbf S_0 \triangleq \sum_{n=1}^{N}\mathbf y_n\mathbf y_n^\top=\mathbf Y^\top\mathbf Y$$

so we can rewrite the scatter matrix as follows:

$$\mathbf S_{\mathbf y}=\mathbf S_0-\frac{1}{N}\left(\sum_{n=1}^{N}\mathbf y_n\right)\left(\sum_{n=1}^{N}\mathbf y_n\right)^\top=\mathbf S_0-N\bar{\mathbf y}\bar{\mathbf y}^{\top}$$

Now we can multiply the likelihood and the prior to give

$$p(\boldsymbol{\mu},\boldsymbol{\Sigma}\mid\mathcal D)\propto |\boldsymbol{\Sigma}|^{-N/2}\exp\left(-\frac{N}{2}(\boldsymbol{\mu}-\bar{\mathbf y})^\top\boldsymbol{\Sigma}^{-1}(\boldsymbol{\mu}-\bar{\mathbf y})\right)\exp\left(-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Sigma}^{-1}\mathbf S_{\mathbf y})\right)$$

$$\times |\boldsymbol{\Sigma}|^{-\frac{\tilde{\nu}+D+1}{2}}\exp\left(-\frac{\tilde{\kappa}}{2}(\boldsymbol{\mu}-\tilde{\mathbf m})^\top\boldsymbol{\Sigma}^{-1}(\boldsymbol{\mu}-\tilde{\mathbf m})\right)\exp\left(-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Sigma}^{-1}\tilde{\mathbf S})\right)$$

$$=|\boldsymbol{\Sigma}|^{-\frac{N+\tilde{\nu}+D+2}{2}}\exp\left(-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Sigma}^{-1}\mathbf M)\right)$$

². Using the language of directed graphical models, we see that $\boldsymbol{\mu}$ and $\boldsymbol{\Sigma}$ become dependent when conditioned on $\mathcal D$ due to explaining away. See Fig. 7.15(a).

³. Note that our uncertainty in the mean is proportional to the covariance. In particular, if we believe that the variance is large, then our uncertainty in $\boldsymbol{\mu}$ must be large too. This makes sense intuitively, since if the data has large spread, it will be hard to pin down its mean.