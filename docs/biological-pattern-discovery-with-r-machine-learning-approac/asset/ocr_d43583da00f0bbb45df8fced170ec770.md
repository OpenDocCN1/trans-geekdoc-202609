# Biological Pattern Discovery with R

As usual, a control expression vector is denoted by **x** and a case
expression vector is denoted by **y**. A joint expression vector is composed
of all expressions and is denoted by **z = U(x,y)**. A tight Gaussian cluster
 is denoted by **z+**. A tight cluster box is defined as above, i.e., $\omega = [\mu - 2\hat{\sigma}, \mu + 2\hat{\sigma}]$ for 95% of a Gaussian confidence interval. A candidate
outlier set **z-⁻** is composed of all expressions which are not included in the
tight cluster set **z+** and is denoted by

```
$z^- = \{z_i^- | z_i^- \in \omega\}$ (6.18)
```

Based on the initial tight cluster **z+** and an initial candidate outlier set
**z-**, an adaptive learning process is implemented using the Bayesian
learning mechanism [Yang and Yang, 2013]. The likelihood function of
the Gaussian tight cluster is defined as below, where **i** is an identity vector
and $\beta = \sigma^{-2}

```
$\mathcal{L}(z^+|\mu, \beta) = \frac{\beta}{2\pi} \exp(-\frac{1}{2}(z^+ - \mu i)^2)$ (6.19)
```

For this Gaussian likelihood function, one *a priori* structure for the
inverse variance $\beta$ is defined as an inverse Gamma

```
$IG($\beta|a, b) = \frac{b^a}{\Gamma(a)} \beta^{-(1+a)}\exp(\frac{b}{\beta})$ (6.20)
```

A prior for the mean $\mu$ is defined as a Gaussian function,

```
$G(\mu|\mu_0, \sigma_0^2) = \frac{1}{\sqrt{2\pi\sigma_0^2}} \exp(-\frac{(\mu - \mu_0)^2}{2\sigma_0^2})$ (6.21)
```

The log-posterior of the likelihood combined with priors leads to the
following format, where the model parameter set is $\theta = (\mu, \beta)$ and
the hyper-parameter set is $\alpha = (\mu_0, \sigma_0^2, a, b)$,

```
$logP(\theta|z^+, \alpha) \propto \alpha log\mathcal{L}(z^+|\mu, \beta) + logIG($\beta|a, b)$ \n$+ logG($\mu|\mu_0, \sigma_0^2)$) (6.22)
```

In the equation above, the log-likelihood is simplified as below,