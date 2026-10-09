
## FIGURE 1.1: Household spending. Notice that the distribution is roughly normal on the $log$ scale (look at the x-axis).

![](img/315929ad4bddd26368466d02e06e2385_36_0.png)

Consider the unconditional mean for the variable $\text{spend}$: the average amount of money spent online annually by households in the United States. You can estimate this mean—say, $\mu_{\text{spend}} = \mathbb{E}[\text{spend}]$—with its $sample$ $average$.

```
> mean(browser$spend)
[1] 1946.439
```

Here, you don’t think that $\mu_{\text{spend}}$ is exactly equal to $1946.439; rather, this is a good guess and the truth is ideally near to this value.

How near? Let’s review some basic statistics. Suppose you have $n$ independent random variables: $\{x_i\}_{i=1}^n$. In terms of our current example, this is saying that each household spends a specific amount without consideration of what the other households in the sample do online. The sample mean is then

$$\overline{x} = \frac{1}{n} \sum_{i=1}^{n} x_i \quad (1.1)$$

The variance of this statistic can be calculated as

$$\operatorname{var}(\overline{x})=\operatorname{var}\left(\frac{1}{n} \sum_{i=1}^{n} x_{i}\right)=\frac{1}{n^{2}} \sum_{i=1}^{n} \operatorname{var}\left(x_{i}\right)=\frac{\sigma^{2}}{n} \quad (1.2)$$

Here, $\sigma^{2}=\operatorname{var}(x)=\mathbb{E}\left[(x-\mu_{\text{spend }})^{2}\right]$ is the variance of a randomly drawn household’s online spending. Note that you are able to move $\operatorname{var}(\cdot)$ inside the sum only because of independence. So, we can estimate the variance for $\overline{X}$ here as follows:

```
> var(browser$spend) /1e4 # since we have 10,000 households
[1] 6461.925
```

This implies a standard deviation around $\sqrt{6462} \approx 80$.

The ever-important central limit theorem (CLT) states that the average of independent random variables becomes normally distributed (i.e., Gaussian or as a “bell curve”) if your sample size is “large enough.” Assuming $n=10,000$ is large enough, the end result is that the sample average for online spending is normally distributed with mean 1946 and standard deviation 80. We write this as $\overline{X} \sim \mathrm{N}(1946, 80^{2})$. Figure 1.2 plots the distribution.

![](img/315929ad4bddd26368466d02e06e2385_37_0.png)

## FIGURE 1.2: Sampling distribution for $\bar{X}$. This picture tells us that if we got a new sample of 10,000 households, we’d expect the new sample average spending to be around $1946 \pm 160$.

What is this distribution? It is our best guess at the sampling distribution. It captures the uncertainty described by the thought experiment: “If I was able to get a new sample of observations, from the same data-generating process, what is the probability distribution on the new sample average?" This is what is referred to as frequentist uncertainty. It is the sort of uncertainty you have seen in basic statistics classes. For example, consider this common description of a confidence interval:

> The poll predicts that 49% of eligible voters would currently vote yes; this number is accurate within ±3 percentage points 19 times out of 20.

This statement describes how an estimated total vote changes under the thought experiment of repeatedly polling a different random set of voters. Similarly, the familiar hypothesis-testing logic—"reject if p-value is less than 0.05"—corresponds to a rule that rejects a null hypothesis mean $\mu_0$ if it falls too far into the tails of the sampling distribution in Figure 1.2.

THE BOOTSTRAP is a computational algorithm for constructing sampling distributions. We will use the bootstrap because the theoretical sampling distributions that are relied upon for much of classical statistics—Gaussian distributions derived from the CLT, as in Figure 1.2—are not valid for the complex settings encountered in business data science. The need for a different approach arises mostly because there are stages of model building that aren't considered in the classical formulas (e.g., variable selection, computational approximation), and the uncertainty in these steps needs to be propagated through to your final analysis. In addition, when the number of model parameters is large relative to the number of observations, the CLT will give a poor representation of real-world performance.

Instead of relying on theoretical approximation, the bootstrap uses resampling from your current sample to mimic the sampling distribution. Recall our definition for the sampling distribution: it is the distribution on an estimator—say, $\hat{\beta}$—that we get by re-estimating $\beta$ on each of multiple datasets of size $n$ from the population. Figure 1.3 illustrates this process.

![](img/315929ad4bddd26368466d02e06e2385_39_0.png)

## FIGURE 1.3: Illustration of the sampling distribution. Each middle-row histogram is a sample from the population, and the bottom histogram is the distribution of resulting estimates $\hat{\beta}$.

The bootstrap in Algorithm 1 mimics the process in **Figure 1.3** by replacing samples from the population with *resamples* from your sample. The *with-replacement* sampling here is essential. It implies that each observation can be chosen more than once for inclusion in the resampling. For example, if we are sampling with-replacement five items from the set $\{1, 2, 3, 4, 5\}$, possible resamples would include $\{1, 1, 3, 3, 4\}$ and $\{2, 2, 2, 3, 5\}$. Using the common analogy of “drawing balls out of a bucket,” we are putting the ball back in after each draw. This type of sampling is what introduces *variability* in our resamples: in this example, without-replacement sampling would *always* yield the set $\{1, 2, 3, 4, 5\}$.

### ALGORITHM 1 The Nonparametric Bootstrap

Given data $\{z_i\}_{i=1}^n$, for $b = 1 \dots B$:

- Resample *with-replacement* $n$ observations $\{z_i^b\}_{i=1}^n$.
- Calculate your estimate, say, $\hat{\beta}_b$, using this resampled set.

Then $\{\hat{\beta}_b\}_{b=1}^B$ is an approximation to the sampling distribution for $\hat{\beta}$.

The resulting “bootstrap sample” can be used for all of the same purposes as your usual theoretical sampling distribution. For example, an approximate standard error—the standard deviation of your sampling distribution—can be approximated by the standard deviation of this bootstrap sample:

$$\operatorname{se}(\hat{\beta}) \approx \operatorname{sd}(\hat{\beta}_b) = \sqrt{\frac{1}{B} \sum_b (\hat{\beta}_b - \hat{\beta})^2} \quad (1.3)$$

Here, $\hat{\beta}$ (without subscript) is the estimated parameter you get using the full original sample. So long as the estimator is *unbiased*, which means that $\mathbb{E}[\hat{\beta}] = \beta$, then you can use this standard error to build your usual 95% confidence interval:

$$\beta \in \hat{\beta} \pm 2\operatorname{sd}(\hat{\beta}_b) \quad (1.4)$$

Revisiting our online spending example, we can write a simple bootstrap for the sampling distribution.

```
> B <- 1000 # number of bootstrap samples
> mub <- c() # a vector to contain the sampled means
> for (b in 1:B) {
+   samp_b <- sample.int(nrow(browser), replace=TRUE)
+   mub <- c(mub, mean(browser$spend[samp_b]))
+ }
> sd (mub)
[1] 80.23819
```

At the end of this loop, we are left with a set of $\bar{x}_b$ values mub, each corresponding to a different data resample. Note that the `replace=TRUE` flag yields with-replacement sampling on the observation indices.

```
> sort(samp_b) [1:10]
[1] 1 1 2 2 4 4 5 7 8 9
```

Figure 1.4 shows the resulting bootstrap estimate of the sampling distribution. We see that it matches closely with the theoretical Gaussian sampling distribution that is implied by the central limit theorem (and the bootstrap standard deviation of 80 matches the theoretical standard error). This makes sense: we have a large sample ($n = 10,000$) and are targeting a simple statistic ($\bar{x}$), so the CLT applies and the theoretical distribution is correct. The advantage of the bootstrap is that it will work in many settings where this theory is unavailable or incorrect.
