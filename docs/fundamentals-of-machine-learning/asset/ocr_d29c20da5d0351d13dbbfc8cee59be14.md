# Some advanced concepts | 129

a covariance matrix **$\Sigma = [Cov[X_i, X_j]]_{i=1,2,...,k;j=1,2,...,k}$** which must be symmetric and positive semidefinite with mean $\mu = (1\ 2)^T$ and covariance $\Sigma = (1\ 0.5; 0.5\ 1)$ is shown in Fig. 6.1.

![](bbox=[0.338, 0.193, 0.662, 0.355])

Fig. 6.1 Multivariate Gaussian with mean $\mu = (1\ 2)^T$ and covariance $\Sigma = (1\ 0.5; 0.5\ 1)$.

# 6.4 Some advanced concepts

# 6.4.1 Cumulative probability (density) function and the Gaussian error function

We have mainly discussed probabilities of single values as specified by the probability (density) functions. However, in many cases we need to know the probabilities of having values within a certain range. The probability of a specific value of a continuous variable is actually infinitesimally small (nearly zero), and only the probability of a range is finite and has a useful meaning of probability. This integrated version of a probability density is the probability of having a value $x$ for the random variable $X$ in the case of $x_1 \leq x \leq x_2$ and is given

```
$P(x_1 \leq X \leq x_2) = \int_{x_1}^{x_2} p(x)dx. \quad (6.19)$
```

A common what we often need to calculate is the probability that a normal (Gaussian) distributed variable has values between $x_1=0$ and $x_2=y$. The probability of Eign 6.19 then gives us a function of $y$. The **Gaussian error function**

```
$\frac{1}{\sqrt{2\pi}\sigma} \int_{-\infty}^{y} e^{-\frac{(x-\mu)^2}{2\sigma^2}}dx = \text{erf}(\frac{y-\mu}{\sqrt{2}\sigma}),. \quad (6.20)$
```

The name of this function comes from the fact that this integral occurs when calculating confidence intervals with Gaussian noise and is often abbreviated as erf. This Gaussian error function for normally distributed variables (Gaussian distribution with mean $\mu=0$ and variance $\sigma=1$) is commonly tabulated in books on statistics. Mathematical programming libraries usually include routines that return the values for specific arguments. In Python, this is implemented by the routine