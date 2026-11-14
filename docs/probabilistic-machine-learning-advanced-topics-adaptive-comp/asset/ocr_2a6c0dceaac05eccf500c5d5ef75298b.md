In the case of the Bernoulli model, we showed that the posterior is a beta distribution. The variance of the beta posterior is given by

```
\(\mathbb{V} [\theta | \mathcal{D}] = \frac{\tilde{\alpha}\tilde{\beta}}{(\tilde{\alpha} + \tilde{\beta})^2(\tilde{\alpha} + \tilde{\beta} + 1)} = \frac{(\tilde{\alpha} + N_1)(\tilde{\beta} + N_0)}{(\tilde{\alpha} + N_1 + \tilde{\beta} + N_0)^2(\tilde{\alpha} + N_1 + \tilde{\beta} + N_0 + 1)}\)
```

If \(N \gg \tilde{\alpha} + \tilde{\beta}\), this simplifies to

```
\(\mathbb{V} [\theta | \mathcal{D}] \approx \frac{N_1 N_0}{(N_1 + N_0)^2(N_1 + N_0)} = \frac{N_1}{N} \frac{N_0}{N} \frac{1}{N} = \frac{\hat{\theta}(1 - \hat{\theta})}{N}\)
```

where \(\hat{\theta} = N_1/N\) is the MLE. Hence the standard error is given by

```
\(\sigma = \sqrt{\mathbb{V} [\theta | \mathcal{D}]} \approx \sqrt{\frac{\hat{\theta}(1 - \hat{\theta})}{N}}\)
```

We see that the uncertainty goes down at a rate of \(1/\sqrt{N}\). We also see that the uncertainty (variance) is maximized when \(\hat{\theta} = 0.5\), and is minimized when \(\hat{\theta}\) is close to 0 or 1. This makes sense, since it is easier to be sure that a coin is biased than to be sure that it is fair.

# 3.2.1.7 Credible intervals

A posterior distribution is (usually) a high dimensional object that is hard to visualize and work with. A common way to summarize such a distribution is to compute a point estimate, such as the posterior mean or mode, and then to compute a **credible interval**, which quantifies the uncertainty associated with that estimate. (A credible interval is not the same as a confidence interval, which is a concept from frequentist statistics which we discuss in Section 3.3.5.1.)

```
\(C_\alpha(\mathcal{D}) = (\ell, u) : P(\ell \le \theta \le u | \mathcal{D}) = 1 - \alpha\)
```

There may be many intervals that satisfy Equation (3.18), so we usually choose one such that there is \((1 - \alpha)/2\) mass in each tail; this is called a **central interval**. If the posterior has a known functional form, we can compute the posterior central interval using \(\ell = F^{-1}(\alpha/2)\) and \(u = F^{-1}(1 - \alpha/2)\), where \(F\) is the cdf of the posterior, and \(F^{-1}\) is the inverse cdf. For example, if the posterior is Gaussian, \(p(\theta | \mathcal{D}) = \mathcal{N}(0, 1)\), and \(\alpha = 0.05\), then we have \(\ell = \Phi^{-1}(\alpha/2) = -1.96\), and \(u = \Phi^{-1}(1 - \alpha/2) = 1.96\), where \(\Phi\) denotes the cdf of the Gaussian. This justifies the common practice of quoting a credible interval in the form of \(\mu \pm 2\sigma\), where \(\mu\) represents the posterior mean, \(\sigma\) represents the posterior standard deviation, and 2 is a good approximation to 1.96.

A problem with central intervals is that there might be points outside the central interval which have higher probability than points that are inside, as illustrated in Figure 3.2(a). This motivates an alternative quantity known as the **highest posterior density** or **HPD** region, which is the set of points which have a probability above some threshold. More precisely we find the threshold \(p^*\) on the pdf such that

```
\(1 - \alpha = \int_{\theta : p(\theta | \mathcal{D}) > p^*} p(\theta | \mathcal{D}) d\theta\)
```