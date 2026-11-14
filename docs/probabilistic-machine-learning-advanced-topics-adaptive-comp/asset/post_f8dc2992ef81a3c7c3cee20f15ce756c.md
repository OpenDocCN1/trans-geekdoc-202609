
This is called the **ordinary least squares (OLS)** solution.

The MLE for the observation noise is given by

\(\hat{\sigma}^2_{mle} = \underset{\sigma^2}{\text{argmin}} \text{NLL}(\hat{w}, \sigma^2) = \frac{1}{N} \sum_{n=1}^N (y_n - x_n^T \hat{w})^2\)

This is just the mean squared error of the residuals, which is an intuitive result.

## 15.2.2 Conjugate priors

In this section, we derive the posterior for the parameters using a conjugate prior. We first consider the case where just $w$ is unknown (so the observation noise variance parameter $\sigma^2$ is fixed), and then we consider the general case, where both $\sigma^2$ and $w$ are unknown.

### 15.2.2.1 Noise variance is known

The conjugate prior for linear regression has the following form:

\(p(w) = \mathcal{N}(w \mid \tilde{w}, \tilde{\Sigma})\)

We often use $\tilde{w} = \mathbf{0}$ as the prior mean and $\tilde{\Sigma} = \tau^2 I_D$ as the prior covariance. (We assume the bias term is included in the weight vector, but often use a much weaker prior for it, since we typically do not want to regularize the overall mean level of the output.)

To derive the posterior, let us first rewrite the likelihood in terms of an MVN as follows:

\(\ell(w) = p(\mathcal{D}|w, \sigma^2) = \prod_{n=1}^N p(y_n | w^T x, \sigma^2) = \mathcal{N}(y | Xw, \sigma^2 I_N)\)

where $I_N$ is the $N \times N$ identity matrix. We can then use Bayes' rule for Gaussians (Equation (2.121)) to derive the posterior, which is as follows:

\(p(w | X, y, \sigma^2) \propto \mathcal{N}(w \mid \tilde{w}, \tilde{\Sigma}) \mathcal{N}(y | Xw, \sigma^2 I_N) = \mathcal{N}(w \mid \hat{w}, \hat{\Sigma})\)

\(\hat{w} \stackrel{\Delta}{=} \hat{\Sigma} (\tilde{\Sigma}^{-1} \tilde{w} + \frac{1}{\sigma^2} X^T y)\)

\(\hat{\Sigma} \stackrel{\Delta}{=} (\tilde{\Sigma}^{-1} + \frac{1}{\sigma^2} X^T X)^{-1}\)

where $\hat{w}$ is the posterior mean, and $\hat{\Sigma}$ is the posterior covariance.

Now suppose $\tilde{w} = 0$ and $\tilde{\Sigma} = \tau^2 I$. In this case, the posterior mean becomes

\(\hat{w} = \frac{1}{\sigma^2} \hat{\Sigma} X^T y = (\frac{\sigma^2}{\tau^2} I + X^T X)^{-1} X^T y\)

If we define $\lambda = \frac{\sigma^2}{\tau^2}$, we see this is equivalent to ridge regression, which optimizes

\(\mathcal{L}(w) = \text{RSS}(w) + \lambda ||w||^2\)

where RSS is the residual sum of squares:

\(\text{RSS}(w) = \frac{1}{2} \sum_{n=1}^N (y_n - w^T x_n)^2 = \frac{1}{2} ||Xw - y||_2^2 = \frac{1}{2} (Xw - y)^T (Xw - y)\)

### 15.2.2.2 Noise variance is unknown

In this section, we assume \(\boldsymbol{w}\) and \(\sigma^2\) are both unknown. The likelihood is given by

\(\ell(\boldsymbol{w}, \sigma^2) = p(\mathcal{D}|\boldsymbol{w}, \sigma^2) \propto (\sigma^2)^{-N/2} \exp \left( - \frac{1}{2\sigma^2} \sum_{n=1}^N (y_n - \boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n)^2 \right) \quad (15.52)\)

Since the regression weights now depend on \(\sigma^2\) in the likelihood, the conjugate prior for \(\boldsymbol{w}\) has the form

\(p(\boldsymbol{w}|\sigma^2) = \mathcal{N}(\boldsymbol{w}| \tilde{\boldsymbol{w}}, \sigma^2 \tilde{\boldsymbol{\Sigma}}) \quad (15.53)\)

For the noise variance \(\sigma^2\), the conjugate prior is based on the inverse gamma distribution, which has the form

\(\text{IG}(\sigma^2| \tilde{a}, \tilde{b}) = \frac{\tilde{b}^{\tilde{a}}}{\Gamma(\tilde{a})}(\sigma^2)^{-(\tilde{a}+1)} \exp(-\frac{\tilde{b}}{\sigma^2}) \quad (15.54)\)

(See Section 2.2.3.4 for more details.) Putting these two together, we find that the joint conjugate prior is the normal inverse gamma distribution:

\(\text{NIG}(\boldsymbol{w}, \sigma^2| \tilde{\boldsymbol{w}}, \tilde{\boldsymbol{\Sigma}}, \tilde{a}, \tilde{b}) \triangleq \mathcal{N}(\boldsymbol{w}| \tilde{\boldsymbol{w}}, \sigma^2 \tilde{\boldsymbol{\Sigma}}) \text{IG}(\sigma^2| \tilde{a}, \tilde{b}) \quad (15.55)\)

\(= \frac{\tilde{b}^{\tilde{a}}}{(2\pi)^{D/2} |\tilde{\boldsymbol{\Sigma}}|^{\frac{1}{2}} \Gamma(\tilde{a})} (\sigma^2)^{-(\tilde{a} + (D/2) + 1)} \times \exp \left[ - \frac{(\boldsymbol{w} - \tilde{\boldsymbol{w}})^\mathsf{T} \tilde{\boldsymbol{\Sigma}}^{-1} (\boldsymbol{w} - \tilde{\boldsymbol{w}}) + 2 \tilde{b}}{2\sigma^2} \right] \quad (15.56)\)

This results in the following posterior:

\(p(\boldsymbol{w}, \sigma^2 | \mathcal{D}) = \text{NIG}(\boldsymbol{w}, \sigma^2| \widehat{\boldsymbol{w}}, \widehat{\boldsymbol{\Sigma}}, \widehat{a}, \widehat{b}) \quad (15.57)\)

\(\widehat{\boldsymbol{w}} = \widehat{\boldsymbol{\Sigma}} \left( \tilde{\boldsymbol{\Sigma}}^{-1} \tilde{\boldsymbol{w}} + \mathbf{X}^\mathsf{T}\mathbf{y} \right) \quad (15.58)\)

\(\widehat{\boldsymbol{\Sigma}} = \left( \tilde{\boldsymbol{\Sigma}}^{-1} + \mathbf{X}^\mathsf{T}\mathbf{X} \right)^{-1} \quad (15.59)\)

\(\widehat{a} = \tilde{a} + N/2 \quad (15.60)\)

\(\widehat{b} = \tilde{b} + \frac{1}{2} \left( \tilde{\boldsymbol{w}}^\mathsf{T} \tilde{\boldsymbol{\Sigma}}^{-1} \tilde{\boldsymbol{w}} + \mathbf{y}^\mathsf{T}\mathbf{y} - \widehat{\boldsymbol{w}}^\mathsf{T} \widehat{\boldsymbol{\Sigma}}^{-1} \widehat{\boldsymbol{w}} \right) \quad (15.61)\)

The expressions for \(\widehat{\boldsymbol{w}}\) and \(\widehat{\boldsymbol{\Sigma}}\) are similar to the case where \(\sigma^2\) is known. The expression for \(\widehat{a}\) is also intuitive, since it just updates the counts. The expression for \(\widehat{b}\) can be interpreted as follows: it is the prior sum of squares, \(\tilde{b}\), plus the empirical sum of squares, \(\mathbf{y}^\mathsf{T}\mathbf{y}\), plus a term due to the error in the prior on \(\boldsymbol{w}\).

The posterior marginals are as follows. For the variance, we have

\(p(\sigma^2 | \mathcal{D}) = \int p(\boldsymbol{w}|\sigma^2, \mathcal{D}) p(\sigma^2 | \mathcal{D}) d\boldsymbol{w} = \text{IG}(\sigma^2| \widehat{a}, \widehat{b}) \quad (15.62)\)

For the regression weights, it can be shown that

\(p(\boldsymbol{w} | \mathcal{D}) = \int p(\boldsymbol{w}|\sigma^2, \mathcal{D}) p(\sigma^2 | \mathcal{D}) d\sigma^2 = \mathcal{T}(\boldsymbol{w}| \widehat{\boldsymbol{w}}, \frac{\widehat{b}}{\widehat{a}} \widehat{\boldsymbol{\Sigma}}, 2 \widehat{a}) \quad (15.63)\)

### 15.2.2.3 Posterior predictive distribution

In machine learning we usually care more about uncertainty (and accuracy) of our predictions, not our parameter estimates. Fortunately, one can derive the posterior predictive distribution in closed form. In particular, one can show that, given $N'$ new test inputs $\tilde{\mathbf{X}}$, we have

```
\(p(\tilde{\mathbf{y}}|\tilde{\mathbf{X}}, \mathcal{D}) = \iint p(\tilde{\mathbf{y}}|\tilde{\mathbf{X}}, \boldsymbol{w}, \sigma^2)p(\boldsymbol{w}, \sigma^2|\mathcal{D})d\boldsymbol{w}d\sigma^2\)
\(= \iint \mathcal{N}(\tilde{\mathbf{y}}|\tilde{\mathbf{X}}\boldsymbol{w}, \sigma^2\mathbf{I}_{N'})\text{NIG}(\boldsymbol{w}, \sigma^2|\widehat{\boldsymbol{w}}, \widehat{\boldsymbol{\Sigma}}, \bar{a}, \bar{b})d\boldsymbol{w}d\sigma^2\)
\(= \mathcal{T}(\tilde{\mathbf{y}}|\tilde{\mathbf{X}}\widehat{\boldsymbol{w}}, \frac{\bar{b}}{\bar{a}}(\mathbf{I}_{N'} + \tilde{\mathbf{X}}\widehat{\boldsymbol{\Sigma}}\tilde{\mathbf{X}}^\mathsf{T}), 2\bar{a})\)
```

The posterior predictive mean is equivalent to “normal” linear regression, but where we plug in \(\widehat{\boldsymbol{w}} = \mathbb{E}[\boldsymbol{w}|\mathcal{D}]\) instead of the MLE. The posterior predictive variance has two components: \(\bar{b}/\bar{a}\mathbf{I}_{N'}\) due to the measurement noise, and \(\bar{b}/\bar{a}\tilde{\mathbf{X}}\widehat{\boldsymbol{\Sigma}}\tilde{\mathbf{X}}^\mathsf{T}\) due to the uncertainty in \(\boldsymbol{w}\). This latter term varies depending on how close the test inputs are to the training data. The results are similar to using a Gaussian prior (with fixed \(\hat{\sigma}^2\)), except the predictive distribution is even wider, since we are taking into account uncertainty about \(\sigma^2\).

## 15.2.3 Uninformative priors

A common criticism of Bayesian inference is the need to use a prior. This is sometimes thought to “pollute” the inferences one makes from the data. We can minimize the effect of the prior by using an uninformative prior, as we discussed in Section 3.5. Below we discuss various uninformative priors for linear regression.

### 15.2.3.1 Jeffreys prior

From Section 3.5.3.1, we know that the Jeffreys prior for the location parameter has the form \(p(\boldsymbol{w}) \propto 1\), and from Section 3.5.3.2, we know that the Jeffreys prior for the scale factor has the form \(p(\sigma) \propto \sigma^{-1}\). We can emulate these priors using an improper NIG prior with \(\tilde{\boldsymbol{w}}=\mathbf{0}\), \(\tilde{\boldsymbol{\Sigma}}=\infty\mathbf{I}\), \(\bar{a}=-D/2\) and \(\bar{b}=0\). The corresponding posterior is given by

```
\(p(\boldsymbol{w}, \sigma^2|\mathcal{D}) = \text{NIG}(\boldsymbol{w}, \sigma^2|\widehat{\boldsymbol{w}}, \widehat{\boldsymbol{\Sigma}}, \bar{a}, \bar{b})\)
\(\widehat{\boldsymbol{w}} = \widehat{\boldsymbol{w}}_{\text{mle}} = (\mathbf{X}^\mathsf{T}\mathbf{X})^{-1}\mathbf{X}^\mathsf{T}\boldsymbol{y}\)
\(\widehat{\boldsymbol{\Sigma}} = (\mathbf{X}^\mathsf{T}\mathbf{X})^{-1} \triangleq \mathbf{C}\)
\(\bar{a} = \frac{\nu}{2}\)
\(\bar{b} = \frac{s^2\nu}{2}\)
\(s^2 \triangleq \frac{\|\boldsymbol{y}-\widehat{\boldsymbol{y}}\|^2}{\nu}\)
\(\nu = N - D\)
```
