
![](img/ca72c1626f4850f058a9edc138c1ac73_124_0.png)

Looking at the form of the likelihood equation, Equation (3.151), we see that a natural conjugate prior has the form of a normal-inverse-Wishart or NIW distribution, defined as follows:

NIW(\mu, \Sigma | \tilde{m}, \tilde{\kappa}, \tilde{\Psi}, \tilde{\nu}) \triangleq \mathcal{N}(\mu | \tilde{m}, \frac{1}{\tilde{\kappa}}\Sigma) \times \text{IW}(\Sigma | \tilde{\Psi}, \tilde{\nu}) (3.153)
= \frac{1}{Z_{NIW}} |\Sigma|^{-\frac{1}{2}} \exp \left( -\frac{\tilde{\kappa}}{2} (\mu - \tilde{m})^T \Sigma^{-1} (\mu - \tilde{m}) \right) \times |\Sigma|^{-\frac{\tilde{\nu}+D+1}{2}} \exp \left( -\frac{1}{2} \text{tr}(\Sigma^{-1} \tilde{\Psi}) \right) (3.154)

where the normalization constant is given by

Z_{NIW} \triangleq 2^{\tilde{\nu} D/2} \Gamma_D(\tilde{\nu}/2) (2\pi / \tilde{\kappa})^{D/2} | \tilde{\Psi} |^{-\tilde{\nu}/2} (3.155)

The parameters of the NIW can be interpreted as follows: \tilde{m} is our prior mean for \mu, and \tilde{\kappa} is how strongly we believe this prior; \tilde{\Psi} is (proportional to) our prior mean for \Sigma, and \tilde{\nu} is how strongly we believe this prior.

## Posterior

To derive the posterior, let us first rewrite the scatter matrix as follows:

\mathbf{S} = \mathbf{Y}^T \mathbf{Y} - \frac{1}{N} (\sum_{n=1}^N \mathbf{y}_n) (\sum_{n=1}^N \mathbf{y}_n)^T = \mathbf{Y}^T \mathbf{Y} - N \bar{\mathbf{y}} \bar{\mathbf{y}}^T (3.156)

where \mathbf{Y}^T \mathbf{Y} = \sum_{n=1}^N \mathbf{y}_n \mathbf{y}_n^T is the sum of squares matrix.

- Note that our uncertainty in the mean is proportional to the covariance. In particular, if we believe that the variance is large, then our uncertainty in \mu must be large too. This makes sense intuitively, since if the data has large spread, it will be hard to pin down its mean.

Now we can multiply the likelihood and the prior to give

\( p(\boldsymbol{\mu}, \boldsymbol{\Sigma} | \mathcal{D}) \propto |\boldsymbol{\Sigma}|^{-\frac{N}{2}} \exp \left( -\frac{N}{2} (\boldsymbol{\mu} - \overline{\mathbf{y}})^\mathsf{T} \boldsymbol{\Sigma}^{-1} (\boldsymbol{\mu} - \overline{\mathbf{y}}) \right) \exp \left( -\frac{1}{2} \text{tr}(\boldsymbol{\Sigma}^{-1} \mathbf{S}) \right) \quad (3.157) \)

\( \times |\boldsymbol{\Sigma}|^{-\frac{\tilde{\nu}+D+1}{2}} \exp \left( -\frac{\tilde{\kappa}}{2} (\boldsymbol{\mu} - \tilde{\mathbf{m}})^\mathsf{T} \boldsymbol{\Sigma}^{-1} (\boldsymbol{\mu} - \tilde{\mathbf{m}}) \right) \exp \left( -\frac{1}{2} \text{tr}(\boldsymbol{\Sigma}^{-1} \tilde{\mathbf{\Psi}}) \right) \quad (3.158) \)

\( = |\boldsymbol{\Sigma}|^{-(N+\tilde{\nu}+D+1)/2} \exp \left( -\frac{1}{2} \text{tr}(\boldsymbol{\Sigma}^{-1} \mathbf{M}) \right) \quad (3.159) \)

where

\( \mathbf{M} \triangleq N(\boldsymbol{\mu} - \overline{\mathbf{y}})(\boldsymbol{\mu} - \overline{\mathbf{y}})^\mathsf{T} + \tilde{\kappa} (\boldsymbol{\mu} - \tilde{\mathbf{m}})(\boldsymbol{\mu} - \tilde{\mathbf{m}})^\mathsf{T} + \mathbf{S} + \tilde{\mathbf{\Psi}} \quad (3.160) \)

\( = (\tilde{\kappa} + N) \boldsymbol{\mu} \boldsymbol{\mu}^\mathsf{T} - \boldsymbol{\mu} (\tilde{\kappa} \tilde{\mathbf{m}} + N \overline{\mathbf{y}})^\mathsf{T} - (\tilde{\kappa} \tilde{\mathbf{m}} + N \overline{\mathbf{y}}) \boldsymbol{\mu}^\mathsf{T} + \tilde{\kappa} \tilde{\mathbf{m}} \tilde{\mathbf{m}}^\mathsf{T} + \mathbf{Y}^\mathsf{T} \mathbf{Y} + \tilde{\mathbf{\Psi}} \quad (3.161) \)

We can simplify the \(\mathbf{M}\) matrix using a trick called **completing the square**. Applying this to the above, we have

\( (\tilde{\kappa} + N) \boldsymbol{\mu} \boldsymbol{\mu}^\mathsf{T} - \boldsymbol{\mu} (\tilde{\kappa} \tilde{\mathbf{m}} + N \overline{\mathbf{y}})^\mathsf{T} - (\tilde{\kappa} \tilde{\mathbf{m}} + N \overline{\mathbf{y}}) \boldsymbol{\mu}^\mathsf{T} \quad (3.162) \)

\( = (\tilde{\kappa} + N) \left( \boldsymbol{\mu} - \frac{\tilde{\kappa} \tilde{\mathbf{m}} + N \overline{\mathbf{y}}}{\tilde{\kappa} + N} \right) \left( \boldsymbol{\mu} - \frac{\tilde{\kappa} \tilde{\mathbf{m}} + N \overline{\mathbf{y}}}{\tilde{\kappa} + N} \right)^\mathsf{T} \quad (3.163) \)

\( - \frac{(\tilde{\kappa} \tilde{\mathbf{m}} + N \overline{\mathbf{y}}) (\tilde{\kappa} \tilde{\mathbf{m}} + N \overline{\mathbf{y}})^\mathsf{T}}{\tilde{\kappa} + N} \quad (3.164) \)

\( = \tilde{\kappa} (\boldsymbol{\mu} - \tilde{\mathbf{m}}) (\boldsymbol{\mu} - \tilde{\mathbf{m}})^\mathsf{T} - \tilde{\kappa} \tilde{\mathbf{m}} \tilde{\mathbf{m}}^\mathsf{T} \quad (3.165) \)

Hence we can rewrite the posterior as follows:

\( p(\boldsymbol{\mu}, \boldsymbol{\Sigma} | \mathcal{D}) \propto |\boldsymbol{\Sigma}|^{-(\tilde{\nu}+D+1)/2} \exp \left( -\frac{1}{2} \text{tr} \left[ \boldsymbol{\Sigma}^{-1} \left( \widehat{\kappa} (\boldsymbol{\mu} - \widehat{\mathbf{m}}) (\boldsymbol{\mu} - \widehat{\mathbf{m}})^\mathsf{T} + \widehat{\mathbf{\Psi}} \right) \right] \right) \quad (3.166) \)

\( = \text{NIW}(\boldsymbol{\mu}, \boldsymbol{\Sigma} \mid \widehat{\mathbf{m}}, \widehat{\kappa}, \widehat{\nu}, \widehat{\mathbf{\Psi}}) \quad (3.167) \)

where

\( \widehat{\mathbf{m}} = \frac{\tilde{\kappa} \tilde{\mathbf{m}} + N \overline{\mathbf{y}}}{\widehat{\kappa}} = \frac{\tilde{\kappa}}{\tilde{\kappa} + N} \tilde{\mathbf{m}} + \frac{N}{\tilde{\kappa} + N} \overline{\mathbf{y}} \quad (3.168) \)

\( \widehat{\kappa} = \tilde{\kappa} + N \quad (3.169) \)

\( \widehat{\nu} = \tilde{\nu} + N \quad (3.170) \)

\( \widehat{\mathbf{\Psi}} = \tilde{\mathbf{\Psi}} + \mathbf{S} + \frac{\tilde{\kappa} N}{\tilde{\kappa} + N} (\overline{\mathbf{y}} - \tilde{\mathbf{m}}) (\overline{\mathbf{y}} - \tilde{\mathbf{m}})^\mathsf{T} \quad (3.171) \)

\( = \tilde{\mathbf{\Psi}} + \mathbf{Y}^\mathsf{T} \mathbf{Y} + \tilde{\kappa} \tilde{\mathbf{m}} \tilde{\mathbf{m}}^\mathsf{T} - \widehat{\kappa} \widehat{\mathbf{m}} \widehat{\mathbf{m}}^\mathsf{T} \quad (3.172) \)

This result is actually quite intuitive: the posterior mean \(\widehat{\mathbf{m}}\) is a convex combination of the prior mean and the MLE; the posterior scatter matrix \(\widehat{\mathbf{\Psi}}\) is the prior scatter matrix \(\tilde{\mathbf{\Psi}}\) plus the empirical scatter matrix \(\mathbf{S}\) plus an extra term due to the uncertainty in the mean (which creates its own virtual scatter matrix); and the posterior confidence factors \(\widehat{\kappa}\) and \(\widehat{\nu}\) are both incremented by the size of the data we condition on.

## Posterior marginals

We have computed the joint posterior

\( p(\boldsymbol{\mu}, \boldsymbol{\Sigma} | \mathcal{D}) = p(\boldsymbol{\mu} | \boldsymbol{\Sigma}, \mathcal{D}) p(\boldsymbol{\Sigma} | \mathcal{D}) = \mathcal{N}(\boldsymbol{\mu} | \widehat{\mathbf{m}}, \frac{1}{\widehat{\kappa}} \boldsymbol{\Sigma}) \text{IW}(\boldsymbol{\Sigma} | \widehat{\mathbf{\Psi}}, \widehat{\nu}) \quad (3.173) \)

We now discuss how to compute the posterior marginals, \(p(\boldsymbol{\Sigma} | \mathcal{D})\) and \(p(\boldsymbol{\mu} | \mathcal{D})\).

It is easy to see that the posterior marginal for \(\boldsymbol{\Sigma}\) is

\(p(\boldsymbol{\Sigma} | \mathcal{D}) = \int p(\boldsymbol{\mu}, \boldsymbol{\Sigma} | \mathcal{D}) d\boldsymbol{\mu} = \text{IW}(\boldsymbol{\Sigma} | \widehat{\mathbf{\Psi}}, \widehat{\nu}) \quad (3.174)\)

For the mean, one can show that

\(p(\boldsymbol{\mu} | \mathcal{D}) = \int p(\boldsymbol{\mu}, \boldsymbol{\Sigma} | \mathcal{D}) d\boldsymbol{\Sigma} = \mathcal{T}(\boldsymbol{\mu} | \widehat{\mathbf{m}}, \frac{\widehat{\mathbf{\Psi}}}{\widehat{\kappa}\widehat{\nu}'}, \widehat{\nu}') \quad (3.175)\)

where \(\widehat{\nu}' = \widehat{\nu} - D + 1\). Intuitively this result follows because \(p(\boldsymbol{\mu} | \mathcal{D})\) is an infinite mixture of Gaussians, where each mixture component has a value of \(\boldsymbol{\Sigma}\) drawn from the IW distribution; by mixing these altogether, we induce a Student distribution, which has heavier tails than a single Gaussian.

## Posterior mode

The maximum a posteriori (MAP) estimate of \(\boldsymbol{\mu}\) and \(\boldsymbol{\Sigma}\) is the mode of the posterior NIW distribution with density

\(p(\boldsymbol{\mu}, \boldsymbol{\Sigma} | \mathbf{Y}) = \mathcal{N}(\boldsymbol{\mu} | \widehat{\boldsymbol{\mu}}, \widehat{\kappa}^{-1} \boldsymbol{\Sigma}) \text{IW}(\boldsymbol{\Sigma} | \widehat{\nu}, \widehat{\mathbf{\Psi}}) \quad (3.176)\)

To find the mode, we firstly notice that \(\boldsymbol{\mu}\) only appears in the conditional distribution \(\mathcal{N}(\boldsymbol{\mu} | \widehat{\boldsymbol{\mu}}, \widehat{\kappa}^{-1} \boldsymbol{\Sigma})\), and the mode of this normal distribution equals its mean, i.e., \(\boldsymbol{\mu} = \widehat{\boldsymbol{\mu}}\). Also notice that this holds for any choice of \(\boldsymbol{\Sigma}\). So we can plug \(\boldsymbol{\mu} = \widehat{\boldsymbol{\mu}}\) in Equation (3.176) and derive the mode of \(\boldsymbol{\Sigma}\). Notice that

\(-2 * \log p(\boldsymbol{\mu} = \widehat{\boldsymbol{\mu}}, \boldsymbol{\Sigma} | \mathbf{Y}) = (\widehat{\nu} + D + 1) \log(|\boldsymbol{\Sigma}|) + \text{tr}(\widehat{\mathbf{\Psi}} \boldsymbol{\Sigma}^{-1}) + c \quad (3.177)\)

where \(c\) is a constant irrelevant to \(\boldsymbol{\Sigma}\). We then take the derivative over \(\boldsymbol{\Sigma}\):

\(\frac{\partial \log p(\boldsymbol{\mu} = \widehat{\boldsymbol{\mu}} | \boldsymbol{\Sigma} | \mathbf{Y})}{\partial \boldsymbol{\Sigma}} = (\widehat{\nu} + D + 1) \boldsymbol{\Sigma}^{-1} - \boldsymbol{\Sigma}^{-1} \widehat{\mathbf{\Psi}} \boldsymbol{\Sigma}^{-1} \quad (3.178)\)

By setting the derivative to 0 and solving for \(\boldsymbol{\Sigma}\), we see that \((\widehat{\nu} + D + 1)^{-1} \widehat{\mathbf{\Psi}}\) is the matrix that maximizes Equation (3.177). By checking that \(\widehat{\mathbf{\Psi}}\) is a positive definite matrix, we conclude that \(\widehat{\mathbf{\Psi}}\) is the MAP estimate of the covariance matrix \(\boldsymbol{\Sigma}\).

In conclusion, the MAP estimate of \(\{ \boldsymbol{\mu}, \boldsymbol{\Sigma} \}\) are

\(\hat{\boldsymbol{\mu}} = \frac{\tilde{\kappa} \tilde{\boldsymbol{\mu}} + N \bar{\mathbf{y}}}{\tilde{\kappa} + N} \quad (3.179)\)

\(\hat{\boldsymbol{\Sigma}} = \frac{1}{\widehat{\nu} + D + 1} \widehat{\mathbf{\Psi}} \quad (3.180)\)
