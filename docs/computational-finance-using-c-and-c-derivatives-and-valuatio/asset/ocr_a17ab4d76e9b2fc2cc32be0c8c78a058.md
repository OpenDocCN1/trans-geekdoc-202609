Generation of Multivariate Distributions: Independent Variates Section | 3.3 43

# 3.3.2 Lognormal Distribution

The lognormal distribution can be generated from the normal distribution discussed in the previous section by means of a simple transformation. If $y \sim N(\mu, \sigma^2)$ and $y = \log(x)$ then $x = \exp(y)$, and we say that the variable $x$ has the lognormal distribution $A(\mu, \sigma^2)$.

The lognormal density function is

```
$f(x) = \frac{1}{x\sigma(2\pi)^{1/2}} \times \exp\left(\frac{-(\log x - \mu)^2}{2\sigma^2}\right) \quad (3.3.7)
```

If $z_i, i = 1, \dots, p$ are independent normal variates $N(\mu_i, \sigma_i^2), i = 1, \dots, p$, then lognormal variates $\ell_{i,i} = 1, \dots, p$ can be generated using the transformation

```
$\ell_i = \exp(z_i), \quad i = 1, \dots, p. \quad (3.3.8)
```

where the mean of the $i$th normal variate is

```
$E[x_i] = \tilde{m}_i = \exp(\mu_i + \frac{\sigma_i^2}{2}) \quad (3.3.9)
```

and the variance is

```
$Var[x_i] = s_i^2 = \exp(2\mu_i + \sigma_i^2)(\exp(\\sigma_i^2) - 1). \quad (3.3.10)
```

The ratio of variance to the mean squared is therefore

```
$\frac{s_i^2}{\tilde{m}_i^2} = \exp(\\sigma_i^2) - 1 \quad (3.3.11)
```

or equivalently

```
$\sigma_i^2 = \log(1 + \frac{s_i^2}{\tilde{m}_i^2}) \quad (3.3.12)
```

A lognormal distribution consisting of $p$ independent variates with means $\tilde{m}_i, i = 1, \dots, p$ and variances $s_i^2, i = 1, \dots, p$ can be generated using the following procedure.

First, generate the $p$ independent normal variates

```
$z_i \sim N(\mu_i, \sigma_i^2), \quad i = 1, \dots, p.$
```

where

```
$\mu_i = \log(\tilde{m}_i) - \frac{\sigma_i^2}{2} \quad (3.3.13)
```

and

```
$\sigma_i^2 = \log(1 + \frac{s_i^2}{\tilde{m}_i^2}) \quad (3.3.14)
```

Then create the independent lognormal variates using

```
$\ell_i = \exp(z_i), \quad i = 1, \dots, p.$
```