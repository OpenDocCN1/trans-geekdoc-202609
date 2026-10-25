aging the predictions across all the trees in the ensemble. For classification, a plurality vote among the individual trees is used.

Unfortunately, correlation limits the variance-reducing effect of averaging. Take the following example for illustration. Suppose $\{X_i\}_{i=1}^N \stackrel{iid}{\sim} (\mu, \sigma^2)$ is a random sample from some distribution with mean $\mu$ and variance $\sigma^2$. Let $\bar{X} = \sum_{i=1}^N X_i / N$ be the sample mean. If the observations are independent (as is the usual annotation of a random sample), then $\text{E}(\bar{X}) = \mu$ and $\text{V}(\bar{X}) = \sigma^2 / N$. In other words, the variance of the average is less than the variance of the sample elements. This of course assumes that the $X_i$ are uncorrelated. If the pairwise correlation between any two observations is $\rho = \rho(X_i, X_j) (i \neq j)$, then

$$ \text{V}(\bar{X}) = \rho \sigma^2 + \frac{1-\rho}{N} \sigma^2, $$

which converges to $\rho \sigma^2$ as $N \to \infty$. In other words, regardless of sample size, correlation limits the variance-reducing effect of averaging. This is illustrated in Figure 7.1, where each boxplot is constructed from 30,000 sample means, each of which is based on a sample of size $N = 30$ from a centered Gaussian distribution with specified pairwise correlation (x-axis); note the increasing variability in the sample means as we go from $\rho = 0$ to $\rho = 1$ (left to right).

![](bbox=[0.205, 0.52, 0.875, 0.785])

FIGURE 7.1: 100 simulated averages from samples of size $N = 30$ with pairwise correlation increasing from zero to one.