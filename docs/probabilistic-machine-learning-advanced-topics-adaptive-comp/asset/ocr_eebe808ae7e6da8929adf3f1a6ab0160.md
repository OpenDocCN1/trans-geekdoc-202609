# Posterior predictive

We now discuss how to predict future data by integrating out the parameters. If \(\mathbf{y} \sim \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma})\), where \((\boldsymbol{\mu}, \boldsymbol{\Sigma}|\mathcal{D}) \sim \text{NIW}(\tilde{\mathbf{m}}, \tilde{\kappa}, \tilde{\nu}, \tilde{\Psi})\), then one can show that the posterior predictive distribution, for a single observation vector, is as follows:

```
\(p(\mathbf{y}|\mathcal{D}) = \int \mathcal{N}(\mathbf{x}|\boldsymbol{\mu}, \boldsymbol{\Sigma})\text{NIW}(\boldsymbol{\mu}, \boldsymbol{\Sigma}|\tilde{\mathbf{m}}, \tilde{\kappa}, \tilde{\nu}, \tilde{\Psi})d\boldsymbol{\mu}d\boldsymbol{\Sigma}\)
\(= \mathcal{T}(\mathbf{y}| \tilde{\mathbf{m}}, \frac{\tilde{\Psi}(\tilde{\kappa}+1)}{\tilde{\kappa}\tilde{\nu}'}, \tilde{\nu}')\)
```

where \(\tilde{\nu}'=\tilde{\nu}-D+1\).

# 3.4.5 The exponential family model

We have seen that exact Bayesian analysis is considerably simplified if the prior is conjugate to the likelihood. Since the posterior must have the same form as the prior, and hence the same number of parameters, the likelihood function must have fixed-sized sufficient statistics, so that we can write \(p(\mathcal{D}|\boldsymbol{\theta}) = p(\mathbf{s}(\mathcal{D})|\boldsymbol{\theta})\). This suggests that the only family of distributions for which conjugate priors exist is the exponential family, a result proved in [DY79].\(^5\) In the sections below, we show how to perform conjugate analysis for a generic exponential family model.

# 3.4.5.1 Likelihood

Recall that the likelihood of the exponential family is given by

```
\(p(\mathcal{D}|\boldsymbol{\eta}) = h(\mathcal{D}) \exp(\boldsymbol{\eta}^{\mathsf{T}}\mathbf{s}(\mathcal{D}) - N A(\boldsymbol{\eta}))\)
```

where \(\mathbf{s}(\mathcal{D}) = \sum_{n=1}^N \mathbf{s}(\mathbf{x}_n)\) and \(h(\mathcal{D}) \triangleq \prod_{n=1}^N h(\mathbf{x}_n)\).

# 3.4.5.2 Prior

Let us write the prior in a form that mirrors the likelihood:

```
\(p(\boldsymbol{\eta}|\tilde{\boldsymbol{\gamma}}, \tilde{\nu}) = \frac{1}{Z(\tilde{\boldsymbol{\gamma}}, \tilde{\nu})} \exp(\tilde{\boldsymbol{\gamma}}^{\mathsf{T}}\boldsymbol{\eta} - \tilde{\nu} A(\boldsymbol{\eta}))\)
```

where \(\tilde{\nu}\) is the strength of the prior, and \(\tilde{\boldsymbol{\gamma}} / \tilde{\nu}\) is the prior mean, and \(Z(\tilde{\boldsymbol{\gamma}}, \tilde{\nu})\) is a normalizing factor. The parameters \(\tilde{\boldsymbol{\gamma}}\) can be derived from **virtual samples** representing our prior beliefs.

5. There are some exceptions. For example, the uniform distribution \(\text{Unif}(x|0,\theta)\) has finite sufficient statistics \((N, m = \max_i x_i)\), as discussed in Section 2.4.2.6; hence this distribution has a conjugate prior, namely the Pareto distribution (Section 2.2.3.5), \(p(\boldsymbol{\theta}) = \text{Pareto}(\boldsymbol{\theta}|\theta_0, \kappa)\), yielding the posterior \(p(\boldsymbol{\theta}|\mathbf{x}) = \text{Pareto}(\max(\boldsymbol{\theta}_0, m), \kappa + N)\).