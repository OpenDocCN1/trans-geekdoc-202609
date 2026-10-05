
# 8.4 Estimation, Confidence Intervals, and Bootstrapping

random variable that follows a normal distribution can take any values in the real line, but those values (on the X-axis) that correspond to the peak of the density curve are more likely than those corresponding to the tails. The density curve drawn with a solid line has the same mean as the one with a dotted line, $\mu=5$, but the former exhibits less dispersion, measured by the standard deviation $\sigma=2$, than the latter, $\sigma=5$. Since the total area under any density curve is equal to 1, the wider curve has to be shorter in height to preserve this property. On the other hand, density curve drawn with a solid line has the same standard deviation as the one drawn with a dashed line, $\sigma=2$, but the latter has a greater mean, $\mu=15$, than the former, $\mu=5$, so they do look the same but the latter is centered farther to the right on the X-axis than the former.

## The standard normal distribution

A special normal distribution has mean $\mu=0$ and standard deviation $\sigma=1$. It is called the standard normal distribution, and it is represented by a density curve z-curve. If a random variable $Z$ follows the standard normal distribution, a realization of this random variable is called a standard value or z-value. The z-value represents the number of standard deviations above the mean, if positive, or below the mean, negative. For example, if $z=5$, the value observed represents five standard deviations above the mean, $\mu=0$.

## Linear transformations of random variables that follow the normal distribution

A linear transformation of a random variable transforms the original variable into a new random variable by adding, subtracting, multiplying, or dividing constants to the original values. The resulting random variable could have a different mean and standard deviation. The most interesting transformation is turning a random variable into another with $\mu=0$ and $\sigma=1$. When this happens we say that the random variable has been standardized.

A property of the normal distribution is that any linear transformation of a random variable that follows the normal distribution also follows a normal distribution, potentially with different mean and standard deviation. In particular, we can turn any random variable into a random variable that follows the standard normal distribution. For example, if a value $x=11$ comes from a normal distribution with mean $\mu=5$ and standard deviation $\sigma=2$, the z-value

```
$z = \frac{x-\mu}{\sigma} = \frac{11-5}{2} = 3$
```

is the corresponding value in a standard normal curve. Moreover, we have determined that $x=11$ for this example is precisely 3 standard deviations above the mean.

## 8.1 Tying the sampling distribution to estimation

### Finding probabilities under a density curve

When a random variable can be represented by a density curve, the probability that the random variable takes a value in any given interval (on the X-axis) is equal to the area under the density curve for interval. If we know the equation that represents the density curve, we could use the mathematical technique of calculus known as integration to determine this. In the case of the normal curve, the integral for any interval does not have a close-form solution, and the solution is calculated using numerical approximations.

We assume that a random variable Z follows a standard normal distribution. We would like to know how likely it is for this random variable to take a value that is within one standard deviation from the mean. Equivalently, what is the probability that the observed value z (in the X-axis) is between -1 and 1 as shown in Figure 8.3?

![](img/445742518041017e8f01f11b0c3190d9_279_0.png)

**FIGURE 8.3:** Normal area within one standard deviation.

Calculations show that this area is 0.6827 or about 68.27% of the total area under the curve. This is equivalent to saying that the probability of getting a value between -1 and 1 on a standard normal is 68.27%. This also means that if a random variable representing an experiment follows a normal distribution, the probability that the outcome of this experiment is within one standard deviation from the mean is 68.27%. Similarly, the area under the standard normal density curve between -2 and 2 is shown in Figure 8.4.

![](img/445742518041017e8f01f11b0c3190d9_279_1.png)

**FIGURE 8.4:** Normal area within two standard deviations.

Calculations show that this area is equal to 0.9545 or 95.46%. If a random representing an experiment follows a normal distribution, the probability that the outcome of this experiment is within two standard deviations from the mean is 95.45%. It is also common practice to use the exact number of standard deviations that correspond to an area around the mean exactly equal to 95% (instead of 95.45%).

The result is that the area under the density curve around the mean is exactly equal to 0.95, or 95%, which is the area within 1.96 standard deviation from the mean. Remember this number as it will be used a few times in future sections.

In summary, the possible outcomes of an experiment can be expressed as a random variable that follows the normal distribution, the probability of getting a result that is within one standard deviation from the mean is about 68.27%, within 2 deviations form the mean is 95.45%, within 1.96 standard deviations from the mean is 95%, and within 3 standard deviations from the mean is about 99.73%, to name a few. Spend a few moments grasping this idea; observe, for example, it is almost impossible to observe an outcome represented by a number that is five standard deviations above the mean as the chances of that happening are near zero. We are now ready to return to our main goal: how to find an interval estimate of the population mean based on a single sample.

## Learning check

(LC8.3) What does the population mean (μ) represent in the context of the almond activity?

- A. The average weight of 100 randomly sampled almonds.
- B. The weight of the heaviest almond in the bowl.
- C. The average weight of all 5,000 almonds in the bowl.
- D. The total weight of all almonds in the bowl.

(LC8.4) Which of the following statements describes the population standard deviation (σ) in the almond activity?

- A. It measures the average difference between almond's weight and the sample mean.
- B. It measures the average difference between almond's weight and the population mean.
- C. It is equal to the square root of the sample variance.
- D. It is always smaller than the population mean.

(LC8.5) Why do we use the sample mean to estimate the population mean?

### 8.1 Tying the sampling distribution estimation

- A. Because the sample mean is always larger than the population mean.
- B. Because the sample mean is a good estimator of the population mean due to its unbiasedness.
- C. Because the sample mean requires less computational effort than the population mean.
- D. Because the sample mean eliminates all sampling variation.

### 8.1.3 The confidence interval

We continue using the example where we try to estimate the population mean weight of almonds with a random sample of 100 almonds. We showed in Chapter 7 that the sampling distribution of the sample mean weight of almonds approximates a normal distribution with expected value equal to

$SE(\bar{x}) = \frac{\sigma}{\sqrt{100}}$

In Subsection 8.1.1 we showed that for the population of almonds, $\mu = 3.645$ grams and $\sigma = 0.32$, so the standard error for the sampling distribution is

$SE(\bar{x}) = \frac{\sigma}{\sqrt{100}} = \frac{0.392}{\sqrt{100}} = 0.039$

grams. In Figure 8.5 we plot the density curve for this distribution using these values.

![](img/445742518041017e8f01f11b0c3190d9_281_0.png)

**FIGURE 8.5:** Normal density curve for the sample mean weight of almonds.

The horizontal axis (X-axis) represents the sample means that we can determine from all the possible random samples of 100 almonds. The left dot represents the expected value of the sampling distribution, $\mu = 3.64$, located on the X-axis at the center of
