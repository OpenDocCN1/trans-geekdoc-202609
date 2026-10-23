been different. The expected degree of variation in any estimator is a source of error that we want to quantify.

The standard error of the mean is given by

$$\mathrm{SE}(\hat{\mu}_m)=\sqrt{\mathrm{Var}\left[\frac{1}{m}\sum_{i=1}^{m}x^{(i)}\right]}=\frac{\sigma}{\sqrt{m}},\qquad(5.46)$$

where $\sigma^2$ is the true variance of the samples $x^i$. The standard error is often estimated by using an estimate of $\sigma$. Unfortunately, neither the square root of the sample variance nor the square root of the unbiased estimator of the variance provide an unbiased estimate of the standard deviation. Both approaches tend to underestimate the true standard deviation but are still used in practice. The square root of the unbiased estimator of the variance is less of an underestimate. For large $m$, the approximation is quite reasonable.

The standard error of the mean is very useful in machine learning experiments. We often estimate the generalization error by computing the sample mean of the error on the test set. The number of examples in the test set determines the accuracy of this estimate. Taking advantage of the central limit theorem, which tells us that the mean will be approximately distributed with a normal distribution, we can use the standard error to compute the probability that the true expectation falls in any chosen interval. For example, the 95 percent confidence interval centered on the mean $\hat{\mu}_m$ is

$$\left(\hat{\mu}_m - 1.96\,\mathrm{SE}(\hat{\mu}_m),\,\hat{\mu}_m + 1.96\,\mathrm{SE}(\hat{\mu}_m)\right),\qquad(5.47)$$

under the normal distribution with mean $\hat{\mu}_m$ and variance $\mathrm{SE}(\hat{\mu}_m)^2$. In machine learning experiments, it is common to say that algorithm $A$ is better than algorithm $B$ if the upper bound of the 95 percent confidence interval for the error of algorithm $A$ is less than the lower bound of the 95 percent confidence interval for the error of algorithm $B$.

# Example: Bernoulli Distribution

We once again consider a set of samples $\{x^{(1)},\dots,x^{(m)}\}$ drawn independently and identically from a Bernoulli distribution (recall $P(x^{(i)};\theta)=\theta^{x^{(i)}}(1-\theta)^{(1-x^{(i)})}$). This time we are interested in computing the variance of the estimator $\hat{\theta}_m = \frac{1}{m}\sum_{i=1}^{m}x^{(i)}$.

$$\mathrm{Var}\left(\hat{\theta}_m\right)=\mathrm{Var}\left(\frac{1}{m}\sum_{i=1}^{m}x^{(i)}\right)\qquad(5.48)$$