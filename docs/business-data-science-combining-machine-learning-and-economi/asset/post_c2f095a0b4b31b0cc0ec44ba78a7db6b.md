
bootstrap, we would instead repeatedly draw data from estimates of an assumed model—say, $\boldsymbol{x} \sim \mathcal{N}(\boldsymbol{\hat{\mu}}, \boldsymbol{\hat{\sigma}}^{2})$—and use the standard deviation of the resulting sample means as an estimate of the standard error.

```r
> xbar <- mean(browser$spend)
> sig2 <- var(browser$spend)
> B <- 10000
> mub <- c()
> for(b in 1:B){
+   xsamp <- rnorm(1e4, xbar, sqrt(sig2))
+   mub <- c(mub, mean(xsamp))
+}
> sd(mub)
[1] 79.70425
> sqrt(sig2/1e4)
[1] 80.3861
```

Here, the results end up matching nearly exactly the earlier theoretical standard errors and the results from the nonparametric bootstrap. However, the parametric bootstrap makes a big assumption that we didn’t require for our other procedures: we’ve assumed that the data is normally distributed. The parametric bootstrap approximates the population distribution by using our estimate of a specific model. This allows it to work for higher-dimensional parameter targets—since we have a full probability model, we don’t need as much data to learn the population distribution—but our results will be sensitive to how well this model represents reality.

> Throughout the book, a black diamond denotes material that is more advanced and abstract. The main content of the book does not require understanding of this material.

❖ We close this section with an advanced topic: use of the bootstrap with biased estimators—that is, for procedures that produce $\hat{\boldsymbol{\beta}}$ where $\mathbb{E}[\hat{\boldsymbol{\beta}}] \neq \boldsymbol{\beta}$. You might not have previously encountered such estimators because, in a perfect world, bias is to be avoided. However, in business data science the world is not perfect, and you are often willing to introduce a little bit of bias in exchange for less noise in your estimation (e.g., see Chapter 3). If you are worried that your estimator might be biased, then you should replace Algorithm 1 with the slightly more complex bootstrap algorithm that targets confidence intervals directly (i.e., it avoids the intermediate step of calculating standard errors).

Algorithm 2 resembles closely our earlier bootstrap. The difference is that it targets the distribution for errors—how much larger or smaller the estimates are than the target—rather than the distribution for the estimates themselves. In this algorithm, the sample estimate $\hat{\beta}$ is your stand-in for the true (unknown) $\beta$. If the $\hat{\beta}_{b}$ values tend to be larger than $\beta$ using your estimation procedure, then you should assume that $\hat{\beta}$ is, in expectation, larger than $\beta$. Note that the bottom end of the interval in Equation 1.6 is defined by subtracting the largest (95th percentile) errors while the top end subtracts the smallest errors.

## ALGORITHM 2 Nonparametric Bootstrap for Confidence Intervals

Given data $\{z_i\}_{i=1}^n$ and full sample estimate $\hat{\beta}$ for parameter $\beta$, for $b = 1 \dots B$:

- Resample with-replacement $n$ observations $\{z_i^b\}_{i=1}^n$.
- Calculate your estimate, say, $\hat{\beta}_{b}$, using this resampled set.
- Calculate the error, say, $e_b = \hat{\beta}_{b} - \hat{\beta}$.

Then $\{e_b\}_{b=1}^B$ is an approximation to the distribution of errors between estimates and their target. To get the 90% confidence interval for the true $\beta$, you would calculate the 5th and 95th percentiles of $\{e_b\}_{b=1}^B$—say, $t_{0.05}$ and $t_{0.95}$—and set your interval as

$$ [\hat{\beta} - t_{0.95}, \hat{\beta} - t_{0.05}] \quad (1.6) $$

To see how this works in practice, recall that the sample variance, $s^2 = \sum_i (x_i - \bar{x})^2 / n$, is a *biased* estimate of the true population variance,

$$ \sigma^2 = \mathbb{E}[(x-\mu)^2]. $$

You can show this by taking the expectation of $s^2$, which demonstrates that $\mathbb{E}[s^2] \neq \sigma^2$:

$$ \mathbb{E}[s^2] = \mathbb{E}[(x-\mu)^2] - \mathbb{E}[(\bar{x} - \mu)^2] = \sigma^2 - \sigma^2/n. \quad (1.7) $$

This is the reason that it is common to use $\sqrt{s^2n/(n-1)}$ as an unbiased estimate of the sample standard deviation. Consider estimating the standard deviation of online spending using only a subsample of 100 browsers.

```r
> smallsamp <- browser$spend[sample.int(nrow(browser), 100)]
> S <- sd(smallsamp) # sample standard deviation
> S
[1] 7572.442
> sd(browser$spend)
[1] 8038.61
> S/sd(browser$spend)
[1] 0.9420089
```

We find that the small sample standard deviation, $s$, is more than $5\%$ smaller than the full sample standard deviation (which, with 10,000 observations, is close to the true $\sigma$). You can use the CI bootstrap of Algorithm 2 to obtain a confidence interval for $\sigma$ that is based on $s$ but corrects for this bias.

```r
> eb <- c()
> for (b in 1:B){
+    sb <- sd(smallsamp[sample.int(100, replace=TRUE)])
+    eb <- c(eb, sb-s)
+ }
> mean(eb)
[1] -407.8306
```

Note that the mean of the bootstrap errors, $\frac{1}{B-1}\sum_b e_b = -408$, is nowhere close to zero. This indicates that we are working with a biased estimator. But when these errors are subtracted from our full sample estimator $s$, we are effectively *subtracting this bias*. That is, we have been able to estimate the bias and correct for it. For example, the mean of $s - e_b$ is now relatively close to the full sample standard deviation (our best guess at $\sigma$).

```r
> mean(s-eb)
[1] 7980.273
> sd(browser$spend)
[1] 8038.61
```

Moreover, the resulting 90% confidence interval is centered around $\sigma$:

```r
> tvals <- quantile(eb, c(0.05, 0.95))
> tvals
     5%      95% 
-4667.349 3161.858
> s - tvals[2:1] # 90% CI
[1] 4410.584 12239.792
```

Although this is the first chapter of this book, bootstrapping is a fairly advanced topic. Don’t worry if this material feels a bit unintuitive. One of the reasons that we introduce it at this early stage is that it gives you a way to *simulate* from sampling distributions and hence to actually observe uncertainty in practice. I encourage you to do this simulation while working through the rest of the book; it will help you to understand the stability of the algorithms and what to expect when you apply them in the real world.

## HYPOTHESIS TESTING AND FALSE DISCOVERY RATE CONTROL

Looking again at the output of the regression, there are two columns beyond the `Estimate` and `Std. Error` values that characterize the sampling distribution.

### Coefficients:

| | Estimate | Std. Error | t value | Pr(>|t|) |
|:----|:----|:----|:----|:----|
| (Intercept) | 5.68508 | 0.04403 | 129.119 | <2e-16 *** |
| broadband | 0.55285 | 0.04357 | 12.689 | <2e-16 *** |
| anychildren | 0.08216 | 0.03380 | 2.431 | 0.0151 * |

What do t value and Pr(> | t |) mean? Why the ***? Most readers will recognize these as the artifacts of *hypothesis testing*.

P(event) is how R denotes a probability function that maps from an event to its probability. We write this as p(event). We overload notation and use the same “p” symbol for both probability mass functions (for discrete events) and for probability density functions (for continuous events).

A hypothesis test is a tool for deciding between two qualitatively different realities. One option will be the *null* hypothesis, which should be your “safe bet.” It is the status quo or stable option and typically corresponds to setting a parameter equal to zero. The *alternative* hypothesis will be a set of possible values. When you “reject the null” in favor of the alternative, you will end up working with the sample estimate for some parameter.

The decision between null and alternative hypotheses is based upon a *sample statistic* that measures the distance between the null reality and your sampled parameter estimates. For a test of the null hypothesis $\beta = 0$ versus the alternative hypothesis $\beta \neq 0$, your test statistic is $z_\beta = \hat{\beta} / se(\hat{\beta})$. It tells you how far away your sample estimate is from zero as measured in standard errors (i.e., standard deviations of the sampling distribution). This is what is labeled as t value in the regression output, but we’ll call it a z *statistic*.

A hypothesis test translates this test statistic into a probability called a *p*-value that represents how rare, or strange, your sample would be *if* the null hypothesis is true. This *p*-value gives you the probability of seeing a larger test statistic than what you’ve observed. Or, from another perspective, it is the proportion of times that you would wrongly reject your safe null if the test statistic you’ve observed is enough to lead you to adopt the alternative.

In the regression example, the *p*-value is p ($|Z| > |z_\beta|$) where $Z \sim N(0, 1)$. The normality of Z comes again from the central limit theorem: the standard deviation is equal to 1 because we’ve divided by the standard error, and the center at 0 is our null hypothesis assumption. As illustrated in *Figure 1.8*, the *p*-value measures the probability mass in the tails past your observed test statistic.
