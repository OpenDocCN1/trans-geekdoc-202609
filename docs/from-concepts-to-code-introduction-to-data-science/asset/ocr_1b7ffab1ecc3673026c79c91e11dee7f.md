# Descriptive Statistics

```
z = stats.norm.rvs(size=200)
sns.boxplot(z, orient='v', whis=1000)
```

The standard deviation is a measure of spread based on the deviation of each data point $x_i$ from the sample mean; the deviations are computed as $x_i - ar{x}$. For aggregating the deviations, the choice is to add to the sum of squared deviations $(x_i - ar{x})^2$; adding them would produce zero due to sign cancellations. The sample standard deviation is denoted $s$ and defined as

```
$s = \sqrt{\frac{\sum_{i=1}^n(x_i - ar{x})^2}{n-1}}$
```

The sample standard deviation is an estimate of the population standard deviation, denoted $\sigma$. Squaring the sample standard deviation produces the sample variance denoted $s^2$ and defined as

```
$s^2 = \frac{\sum_{i=1}^n(x_i - ar{x})^2}{n-1}$
```

The variance is particularly useful when combining the spread of several variables, as variances can be added directly; this is not the case with standard deviations, as they involve square roots. The divisor $n-1$ provides an unbiased estimate of $s^2$. This means if we draw random samples from the population, the average value of $s^2$ taken over the random samples will be equal to $\sigma^2$, the population variance.

# Covoment

It is particularly useful in prediction to understand how two variables move together. Given equally sized samples of two random variables $X$ and $Y$, we can compute statistics whose measure their movement. The sample covariance between $X$ and $Y$ is denoted $s_{xy}$ and computed in a similar way to the sample variance. The sample variance uses a squared term $(x_i - ar{x})(y_i - ar{y})$ where $ar{x}$ and $ar{y}$ represent the sample means of $x$ and $y$, respectively. The sample covariance may be defined as

```
$s_{xy} = \frac{\sum_{i=1}^n(x_i - ar{x})(y_i - ar{y})}{n-1}$
```

The sample covariance $s_{xy}$ is an estimate of the population covariance denoted $\sigma_{xy}$. The sign and magnitude of the covariance indicates the average tendency of the variables to move together in the same direction, while a large, negative covariance indicates movement move in the opposite direction. A covariance of zero indicates no relationship between the variables.