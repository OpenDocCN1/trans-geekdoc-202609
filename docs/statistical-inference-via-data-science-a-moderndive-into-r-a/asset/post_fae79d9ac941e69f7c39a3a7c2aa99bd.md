
## 8.2 Estimation with the bootstrap

```r
percentile_ci <- bootstrap_means |
get_confidence_interval(level = 0.95, type = "percentile")
percentile_ci
```

```r
# A tibble: 1 x 2
lower_ci upper_ci
<dbl> <dbl>
1 3.61198 3.756
```

Alternatively, we can visualize the interval (3.61, 3.76) by piping the bootstrap_means data frame into the visualize() function and adding a shade_confidence_interval() layer. We set the endpoints to be percentile_ci.

```r
visualize(bootstrap_means) +
shade_confidence_interval(endpoints = percentile_ci)
```

![](img/445742518041017e8f01f11b0c3190d9_313_0.png)

FIGURE 8.21: Percentile method 95% confidence interval shaded corresponding to potential values.

Observe in Figure 8.21 that 95% of the sample means stored in the stat variable bootstrap_means fall between the two endpoints marked with the darker lines, 2.5% of the sample means to the left of the shaded area and 2.5% of the sample means to the right. You also have the option to change the colors of the shading using the color and fill arguments.

The infer package has incorporated a shorter named function shade_ci() that produces the same results. Try out the following code:

```r
visualize(bootstrap_means) +
shade_ci(endpoints = percentile_ci, color = "hotpink", fill = "khaki")
```

### Standard error method

In Subsection 8.1.3 we introduced theory-based confidence intervals. We show that a 95% confidence interval can be constructed as

$(\bar{x} - 1.96 \cdot SE(\bar{x})) \quad \bar{x} + 1.96 \cdot SE(\bar{x}))$

$\bar{x}$ is the sample mean of the original sample, $n$ is the number of standard errors around the mean needed to account for 95% of the area under the density curve (when the distribution is normal), and $SE(\bar{x})$ is the standard error of the sample mean that can be computed as $\sigma/\sqrt{n}$ if the population standard deviation is known, or estimated as $s/\sqrt{n}$ if we use the sample standard deviation, $s$, and the sample size, $n$.

We use the same structure to construct confidence intervals but using the bootstrap sample means to estimate the standard error of $\bar{x}$. Thus, the 95% confidence interval for the population mean, $\mu$, using the standard error estimated via bootstrapping, $SE_{boot}$, is:

$(\bar{x} - 1.96 \cdot SE_{boot}) \quad \bar{x} + 1.96 \cdot SE_{boot})$

We can compute this confidence interval using dplyr. First, we calculate the estimated standard error:

```r
SE_boot <- bootstrap_means |>
  summarize(SE = sd(stat)) |>
  pull(SE)
SE_boot
# [1] 0.0357
```

and then use the original sample mean to calculate 95% confidence interval:

```r
almonds_sample_100 |>
  summarize(lower_bound = mean(weight) - 1.96 * SE_boot,
            upper_bound = mean(weight) + 1.96 * SE_boot)
```

```r
# A tibble: 1 x 2
lower_bound upper_bound
<dbl> <dbl>
1 3.61210 3.75190
```

Alternatively, computation of 95% confidence interval can be done again via infer. We find the sample mean of the original sample and store it in variable x_bar:

```r
x_bar <- almonds_sample_100 |>
  specify(response = weight) |
  calculate(stat = "mean")
x_bar
# Response: weight (numeric)
# A tibble: 1 x 1
stat
<dbl>
1 3.6822
```

Now, we pipe the bootstrap_means data frame we created into the get_confidence_interval() function. We set the type argument to be "se" and specify the point_estimate argument to be x_bar in order to set the center of the confidence interval to the mean of the original sample.

```r
standard_error_ci <- bootstrap_means |
  get_confidence_interval(type = "se", point_estimate = x_bar, level = 0.95)
standard_error_ci
```

```r
# A tibble: 1 x 2
lower_ci upper_ci
<dbl> <dbl>
1 3.61210 3.75190
```

The results are the same whether dplyr or infer is used, but as explained earlier, the latter provides more flexibility. If we would like to visualize the interval (3.61, 3.75), we can once again pipe the bootstrap_means data frame into the visualize() function and add a shade_confidence_interval() layer to our plot. The resulting standard-error method based on 95% confidence interval for $\mu$ can be seen in Figure 8.22.

```r
visualize(bootstrap_means) +
shade_confidence_interval(endpoints = standard_error_ci)
```

![](img/445742518041017e8f01f11b0c3190d9_316_0.png)

FIGURE 8.22: Standard-error method 95% confidence interval.

Because we are using bootstrap to construct these intervals, we call the percentile and standard error methods simulation-based methods. We can compare the 95% confidence intervals using both simulation-based methods as well as the theory-based method described in 8.1.3:

- Percentile method: (3.61, 3.76)
- Standard error method: (3.61, 3.75)
- Theory-based method: (3.61, 3.76)

### Learning check

- (LC14) Construct a 95% confidence interval for the median weight of almonds. Would it be appropriate to also use the bootstrap method?
- (LC15) What are the advantages of using the infer package for constructing confidence intervals?
- (LC16) What is the main purpose of bootstrapping in statistical inference?
  - A. To visualize data distributions and identify outliers.
  - B. To generate multiple samples from the original data for estimating population parameters and constructing confidence intervals.
  - C. To replace missing data points with the mean of the dataset.
  - D. To validate the assumptions of a regression model.
- (LC17) Which function in the infer package is primarily used to denote the interests of statistical inference?
  - A. rep_sample_n()
  - B. calculate()
  - C. specify()
  - D. visualize()
- (LC18) What is a key difference between the percentile method and the standard error method for constructing confidence intervals using bootstrap samples?
  - A. The percentile method requires the population standard deviation, while the standard error method does not.
  - B. The percentile method uses the middle 95% of bootstrap sample statistics, while the standard error method uses an estimated standard error from bootstrap samples.
  - C. The standard error method always results in a narrower confidence interval than the percentile method.
  - D. The percentile method requires more bootstrap samples than the standard error method.

![](img/445742518041017e8f01f11b0c3190d9_317_0.png)

## 8.3 Additional remarks about the bootstrap

This section expands explanations on the bootstrap-methods, provides historical context, gives a comparison between the theory-approach and the simulation-based approach when working with confidence intervals, and provides reasons for using the bootstrap. The presentation is more theoretical than other sections in this chapter, and you are welcome to skip to Section 8.4 if you want to go directly another application of the bootstrap methods in R. Additional theoretical explanations are available in the Appendices of the online version of the book¹.

### 8.3.1 The bootstrap and other resampling methods

The bootstrap is one of resampling methods. Chernick and LaBudde noted that the bootstrap's roots trace back to the development of similar techniques like permutations and the jackknife (Chernick and LaBudde, 2011). The bootstrap was initially conceived as an approximation to another resampling method called the jackknife.

¹ https://moderndive.com/v2/appendixa

jackknife but quickly gained recognition for its broader applicability and efficiency. Since then, it has been shown in multiple contexts that the bootstrap performs at least as well as traditional methods in estimating standard errors, constructing confidence intervals, performing hypothesis testing, and many other statistical techniques.

Furthermore, the 1980s (but even more in the last two decades), the use of simulations to compare advanced bootstrap methods against other techniques, such as cross-validation, further established its superiority in specific contexts, particularly when dealing with small sample sizes. The use of the bootstrap and bootstrap-related methods has become a cornerstone in modern statistics.

### 8.3.2 Confidence intervals and rate of convergence

We want to compare how the bootstrap performs when building intervals with respect to the theory-based method. The formal comparison requires mathematical concepts beyond the scope of this book, and it is not pursued. Instead, we provide just enough elements to help you with the intuition of how this is made.

Let's start with an illustration using the theory-based confidence interval. A 95% confidence interval for $\mu$, when a sample size of $n = 100$ is used, is given by

$\mu \pm 1.96\frac{\sigma}{\sqrt{n}}$

when $\sigma$ is unknown or

$\mu \pm 1.98\frac{s}{\sqrt{n}}$

when $\sigma$ is unknown. We use 95% and $n = 100$ for this illustration, but the exposition is also true with any other confidence level or other sample sizes. We understand that 95% of all the possible samples would lead to an interval that contains $\mu$. This statement is exactly true if the distribution of $\bar{X}$ is precisely normal, and we say that 95% is the true coverage probability. In reality, we do not know what the distribution of the population is, but because of the Central Limit Theorem we know that for a large sample size $n$ the distribution of $\bar{X}$ is approximately normal. In this case, the 95% is an approximate coverage probability.
