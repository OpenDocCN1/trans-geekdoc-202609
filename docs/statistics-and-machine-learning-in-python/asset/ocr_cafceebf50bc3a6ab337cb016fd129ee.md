# 7.2 Main distributions

# 7.2.1 Normal distribution

The normal distribution, noted $\mathcal{N}(\mu, \sigma)$ with parameters: $\mu$ mean (location) and $\sigma > 0$ std-dev. Estimators: $\bar{x}$ and $\sigma_x$.

The normal distribution, noted $\mathcal{N}$, is useful because of the central limit theorem (CLT) which states that: given certain conditions, the arithmetic mean of a sufficiently large number of iterates of independent random variables, each with a well-defined expected value and well-defined variance, will be approximately normally distributed, regardless of the underlying distribution.

```
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import norm
%matplotlib inline

mu = 0 # mean
variance = 2 #variance
sigma = np.sqrt(variance) #standard deviation\n",
x = np.linspace(mu-3*variance,mu+3*variance, 100)
plt.plot(x, norm.pdf(x, mu, sigma))
```

```
[<matplotlib.lines.Line2D at 0x7fc56b189cf8>]
```

![](bbox=[0.18, 0.49, 0.75, 0.77])

# 7.2.2 The Chi-Square distribution

The chi-square or $\chi^2_n$ distribution with $n$ degrees of freedom (df) is the distribution of a sum of the squares of $n$ independent standard normal random variables $\mathcal{N}(0,1)$. Let $X \sim \mathcal{N}(\mu, \sigma^2)$, then, $Z = (X - \mu)/\sigma \sim \mathcal{N}(0,1)$, then:

+   - The squared standard $Z^2 \sim \chi^2_1$ (one df).