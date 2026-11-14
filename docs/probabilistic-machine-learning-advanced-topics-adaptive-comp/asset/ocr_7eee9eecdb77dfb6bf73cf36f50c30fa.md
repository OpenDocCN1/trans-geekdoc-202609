# 15.2.2.3 Posterior predictive distribution

In machine learning we usually care more about uncertainty (and accuracy) of our predictions, not our parameter estimates. Fortunately, one can derive the posterior predictive distribution in closed form. In particular, one can show that, given $N'$ new test inputs $\tilde{\mathbf{X}}$, we have

```
\(p(\tilde{\mathbf{y}}|\tilde{\mathbf{X}}, \mathcal{D}) = \iint p(\tilde{\mathbf{y}}|\tilde{\mathbf{X}}, \boldsymbol{w}, \sigma^2)p(\boldsymbol{w}, \sigma^2|\mathcal{D})d\boldsymbol{w}d\sigma^2\)
\(= \iint \mathcal{N}(\tilde{\mathbf{y}}|\tilde{\mathbf{X}}\boldsymbol{w}, \sigma^2\mathbf{I}_{N'})\text{NIG}(\boldsymbol{w}, \sigma^2|\widehat{\boldsymbol{w}}, \widehat{\boldsymbol{\Sigma}}, \bar{a}, \bar{b})d\boldsymbol{w}d\sigma^2\)
\(= \mathcal{T}(\tilde{\mathbf{y}}|\tilde{\mathbf{X}}\widehat{\boldsymbol{w}}, \frac{\bar{b}}{\bar{a}}(\mathbf{I}_{N'} + \tilde{\mathbf{X}}\widehat{\boldsymbol{\Sigma}}\tilde{\mathbf{X}}^\mathsf{T}), 2\bar{a})\)
```

The posterior predictive mean is equivalent to “normal” linear regression, but where we plug in \(\widehat{\boldsymbol{w}} = \mathbb{E}[\boldsymbol{w}|\mathcal{D}]\) instead of the MLE. The posterior predictive variance has two components: \(\bar{b}/\bar{a}\mathbf{I}_{N'}\) due to the measurement noise, and \(\bar{b}/\bar{a}\tilde{\mathbf{X}}\widehat{\boldsymbol{\Sigma}}\tilde{\mathbf{X}}^\mathsf{T}\) due to the uncertainty in \(\boldsymbol{w}\). This latter term varies depending on how close the test inputs are to the training data. The results are similar to using a Gaussian prior (with fixed \(\hat{\sigma}^2\)), except the predictive distribution is even wider, since we are taking into account uncertainty about \(\sigma^2\).

# 15.2.3 Uninformative priors

A common criticism of Bayesian inference is the need to use a prior. This is sometimes thought to “pollute” the inferences one makes from the data. We can minimize the effect of the prior by using an uninformative prior, as we discussed in Section 3.5. Below we discuss various uninformative priors for linear regression.

# 15.2.3.1 Jeffreys prior

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