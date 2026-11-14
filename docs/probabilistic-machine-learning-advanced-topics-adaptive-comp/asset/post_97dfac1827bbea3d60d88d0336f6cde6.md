
## Posterior predictive

We now discuss how to predict future data by integrating out the parameters. If \(\mathbf{y} \sim \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma})\), where \((\boldsymbol{\mu}, \boldsymbol{\Sigma}|\mathcal{D}) \sim \text{NIW}(\tilde{\mathbf{m}}, \tilde{\kappa}, \tilde{\nu}, \tilde{\Psi})\), then one can show that the posterior predictive distribution, for a single observation vector, is as follows:

```
\(p(\mathbf{y}|\mathcal{D}) = \int \mathcal{N}(\mathbf{x}|\boldsymbol{\mu}, \boldsymbol{\Sigma})\text{NIW}(\boldsymbol{\mu}, \boldsymbol{\Sigma}|\tilde{\mathbf{m}}, \tilde{\kappa}, \tilde{\nu}, \tilde{\Psi})d\boldsymbol{\mu}d\boldsymbol{\Sigma}\)
\(= \mathcal{T}(\mathbf{y}| \tilde{\mathbf{m}}, \frac{\tilde{\Psi}(\tilde{\kappa}+1)}{\tilde{\kappa}\tilde{\nu}'}, \tilde{\nu}')\)
```

where \(\tilde{\nu}'=\tilde{\nu}-D+1\).

## 3.4.5 The exponential family model

We have seen that exact Bayesian analysis is considerably simplified if the prior is conjugate to the likelihood. Since the posterior must have the same form as the prior, and hence the same number of parameters, the likelihood function must have fixed-sized sufficient statistics, so that we can write \(p(\mathcal{D}|\boldsymbol{\theta}) = p(\mathbf{s}(\mathcal{D})|\boldsymbol{\theta})\). This suggests that the only family of distributions for which conjugate priors exist is the exponential family, a result proved in [DY79].\(^5\) In the sections below, we show how to perform conjugate analysis for a generic exponential family model.

### 3.4.5.1 Likelihood

Recall that the likelihood of the exponential family is given by

```
\(p(\mathcal{D}|\boldsymbol{\eta}) = h(\mathcal{D}) \exp(\boldsymbol{\eta}^{\mathsf{T}}\mathbf{s}(\mathcal{D}) - N A(\boldsymbol{\eta}))\)
```

where \(\mathbf{s}(\mathcal{D}) = \sum_{n=1}^N \mathbf{s}(\mathbf{x}_n)\) and \(h(\mathcal{D}) \triangleq \prod_{n=1}^N h(\mathbf{x}_n)\).

### 3.4.5.2 Prior

Let us write the prior in a form that mirrors the likelihood:

```
\(p(\boldsymbol{\eta}|\tilde{\boldsymbol{\gamma}}, \tilde{\nu}) = \frac{1}{Z(\tilde{\boldsymbol{\gamma}}, \tilde{\nu})} \exp(\tilde{\boldsymbol{\gamma}}^{\mathsf{T}}\boldsymbol{\eta} - \tilde{\nu} A(\boldsymbol{\eta}))\)
```

where \(\tilde{\nu}\) is the strength of the prior, and \(\tilde{\boldsymbol{\gamma}} / \tilde{\nu}\) is the prior mean, and \(Z(\tilde{\boldsymbol{\gamma}}, \tilde{\nu})\) is a normalizing factor. The parameters \(\tilde{\boldsymbol{\gamma}}\) can be derived from **virtual samples** representing our prior beliefs.

5. There are some exceptions. For example, the uniform distribution \(\text{Unif}(x|0,\theta)\) has finite sufficient statistics \((N, m = \max_i x_i)\), as discussed in Section 2.4.2.6; hence this distribution has a conjugate prior, namely the Pareto distribution (Section 2.2.3.5), \(p(\boldsymbol{\theta}) = \text{Pareto}(\boldsymbol{\theta}|\theta_0, \kappa)\), yielding the posterior \(p(\boldsymbol{\theta}|\mathbf{x}) = \text{Pareto}(\max(\boldsymbol{\theta}_0, m), \kappa + N)\).

### 3.4.5.3 Posterior

The posterior is given by

\( p(\boldsymbol{\eta}|\mathcal{D}) = \frac{p(\mathcal{D}|\boldsymbol{\eta})p(\boldsymbol{\eta})}{p(\mathcal{D})} \)
\( = \frac{h(\mathcal{D})}{Z(\bar{\boldsymbol{\tau}}, \bar{\nu})p(\mathcal{D})} \exp \left( (\tilde{\boldsymbol{\tau}} + \boldsymbol{s}(\mathcal{D}))^\top \boldsymbol{\eta} - (\tilde{\nu} + N)A(\boldsymbol{\eta}) \right) \)
\( = \frac{1}{Z(\bar{\boldsymbol{\tau}}, \bar{\nu})} \exp \left( \bar{\boldsymbol{\tau}}^\top \boldsymbol{\eta} - \bar{\nu} A(\boldsymbol{\eta}) \right) \)

where

\( \tilde{\boldsymbol{\tau}} = \bar{\boldsymbol{\tau}} + \boldsymbol{s}(\mathcal{D}) \)
\( \tilde{\nu} = \bar{\nu} + N \)
\( Z(\tilde{\boldsymbol{\tau}}, \tilde{\nu}) = \frac{Z(\bar{\boldsymbol{\tau}}, \bar{\nu})}{h(\mathcal{D})} p(\mathcal{D}) \)

We see that this has the same form as the prior, but where we update the sufficient statistics and the sample size.

The posterior mean is given by a convex combination of the prior mean and the empirical mean (which is the MLE):

\( \mathbb{E} [\boldsymbol{\eta}|\mathcal{D}] = \frac{\tilde{\boldsymbol{\tau}}}{\tilde{\nu}} = \frac{\tilde{\boldsymbol{\tau}} + \boldsymbol{s}(\mathcal{D})}{\tilde{\nu} + N} = \frac{\tilde{\nu}}{\tilde{\nu} + N} \frac{\tilde{\boldsymbol{\tau}}}{\tilde{\nu}} + \frac{N}{\tilde{\nu} + N} \frac{\boldsymbol{s}(\mathcal{D})}{N} \)
\( = \lambda \mathbb{E} [\boldsymbol{\eta}] + (1 - \lambda) \hat{\boldsymbol{\eta}}_{\text{mle}} \)

where \( \lambda = \frac{\tilde{\nu}}{\tilde{\nu} + N} \).

### 3.4.5.4 Marginal likelihood

From Equation (3.190) we see that the marginal likelihood is given by

\( p(\mathcal{D}) = \frac{Z(\bar{\boldsymbol{\tau}}, \bar{\nu})h(\mathcal{D})}{Z(\tilde{\boldsymbol{\tau}}, \tilde{\nu})} \)

See Section 3.2.1.9 for a detailed example in the case of the beta-Bernoulli model.

### 3.4.5.5 Posterior predictive density

We now derive the predictive density for future observables \(\mathcal{D}' = (\tilde{\boldsymbol{x}}_1, \dots, \tilde{\boldsymbol{x}}_{N'})\) given past data \(\mathcal{D} = (\boldsymbol{x}_1, \dots, \boldsymbol{x}_N)\):

\( p(\mathcal{D}'|\mathcal{D}) = \int p(\mathcal{D}'|\boldsymbol{\eta})p(\boldsymbol{\eta}|\mathcal{D}) d\boldsymbol{\eta} \)
\( = \int h(\mathcal{D}') \exp(\boldsymbol{\eta}^\top \boldsymbol{s}(\mathcal{D}') - N' A(\boldsymbol{\eta})) \frac{1}{Z(\tilde{\boldsymbol{\tau}}, \tilde{\nu})} \exp(\boldsymbol{\eta}^\top \tilde{\boldsymbol{\tau}} - \tilde{\nu} A(\boldsymbol{\eta})) d\boldsymbol{\eta} \)
\( = h(\mathcal{D}') \frac{Z(\tilde{\boldsymbol{\tau}} + \boldsymbol{s}(\mathcal{D}) + \boldsymbol{s}(\mathcal{D}'), \tilde{\nu} + N + N')}{Z(\tilde{\boldsymbol{\tau}} + \boldsymbol{s}(\mathcal{D}), \tilde{\nu} + N)} \)

### 3.4.5.6 Example: Bernoulli distribution

As a simple example, let us revisit the Beta-Bernoulli model in our new notation. The likelihood is given by

```
p(\mathcal{D}|\theta) = (1-\theta)^N \exp \left( \log(\frac{\theta}{1-\theta}) \sum_i x_n \right)
```

Hence the conjugate prior is given by

```
p(\theta|\nu_0, \tau_0) \propto (1-\theta)^{\nu_0} \exp \left( \log(\frac{\theta}{1-\theta})\tau_0 \right)
= \theta^{\tau_0}(1-\theta)^{\nu_0-\tau_0}
```

If we define \alpha = \tau_0 + 1 and \beta = \nu_0 - \tau_0 + 1, we see that this is a beta distribution.
We can derive the posterior as follows, where s = \sum_i \mathbb{I}(x_i = 1) is the sufficient statistic:

```
p(\theta|\mathcal{D}) \propto \theta^{\tau_0+s}(1-\theta)^{\nu_0-\tau_0+n-s}
= \theta^{\tau_n}(1-\theta)^{\nu_n-\tau_n}
```

We can derive the posterior predictive distribution as follows. Assume p(\theta) = Beta(\theta|\alpha, \beta), and let s = s(\mathcal{D}) be the number of heads in the past data. We can predict the probability of a given sequence of future heads, \mathcal{D}' = (\tilde{x}_1, ..., \tilde{x}_m), with sufficient statistic s' = \sum_{n=1}^m \mathbb{I}(\tilde{x}_i = 1), as follows:

```
p(\mathcal{D}'|\mathcal{D}) = \int_0^1 p(\mathcal{D}'|\theta)\text{Beta}(\theta|\alpha_n, \beta_n)d\theta
= \frac{\Gamma(\alpha_n + \beta_n)}{\Gamma(\alpha_n)\Gamma(\beta_n)} \int_0^1 \theta^{\alpha_n+s'-1}(1-\theta)^{\beta_n+m-s'-1}d\theta
= \frac{\Gamma(\alpha_n + \beta_n) \Gamma(\alpha_{n+m})\Gamma(\beta_{n+m})}{\Gamma(\alpha_n)\Gamma(\beta_n) \Gamma(\alpha_{n+m} + \beta_{n+m})}
```

where

```
\alpha_{n+m} = \alpha_n + s' = \alpha + s + s'
\beta_{n+m} = \beta_n + (m - s') = \beta + (n - s) + (m - s')
```

## 3.4.6 Beyond conjugate priors

We have seen various examples of conjugate priors, all of which have come from the exponential family (see Section 2.4). These priors have the advantages of being easy to interpret (in terms of sufficient statistics from a virtual prior dataset), and being easy to compute with. However, for most models, there is no prior in the exponential family that is conjugate to the likelihood. Furthermore, even where there is a conjugate prior, the assumption of conjugacy may be too limiting. Therefore in the sections below, we briefly discuss various other kinds of priors. (We defer the question of posterior inference with these priors until Section 7.1, where we discuss algorithmic issues, since we can no longer use closed-form solutions when the prior is not conjugate.)
