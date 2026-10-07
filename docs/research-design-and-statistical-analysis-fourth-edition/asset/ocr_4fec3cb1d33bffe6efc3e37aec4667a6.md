Solving for $\mu$, we have the upper bound:

$\mu \le \bar{Y} + 1.96\sigma_{ar{Y}}$

Similarly, we can solve for the lower bound. From the inequality

$(\bar{Y} - \mu) / \sigma_{ar{Y}} \le 1.96$

we arrive at

$\bar{Y} - 1.96\sigma_{ar{Y}} \le \mu$

Putting it all together, we have

$p(\bar{Y} - 1.96\sigma_{ar{Y}} \le \mu \le \bar{Y} + 1.96\sigma_{ar{Y}}) = .95$

Recall that $\bar{Y} = 224.684$ and $s = 31.302$. Dividing $s$ by the square root of $n$, $\sqrt{117}$, we have $2.894$, an estimate of $\sigma$. Because $n$ is large and $s$ is a reasonably confident estimate of $\sigma$, we expect $\mu$ to be very close to $\sigma$ and feel justified in using it in our calculations.$2$ Substituting into Equation 5.11, we find that the lower and upper bounds of the 95% CI for $\mu$

$CI = \bar{Y} \pm 1.96\sigma_{ar{Y}} = 224.684 \pm 5.672 = 219.012, 230.356$

In words, we can be 95% confident that, for over 50, the population mean TC falls between 219.01 and 230.356. Consistent with our earlier look at plots of the data, we see that the lower limit of the confidence interval, 219, is above the recommended TC of 200, but we are reasonably confident that the population mean is not dangerously high for the population of over-50 men from whom we have sampled.

What exactly do these numerical limits mean? In what sense do we have 95% confidence that the population mean is contained within them? We may not say that "the probability is $95\%$ that $\mu$ lies between 219 and 230" because $\mu$ is in this interval or not. Further, if we were to draw another sample from the same population of TC scores, the mean would change, giving rise to different limits. What 95% confidence means that if we draw many samples and the 95% confidence interval for each sample, in the long run, 95% of these intervals will contain $\mu$, or .95, or that the actual value of $\mu$ falls within the confidence interval we calculated.

The narrower the interval, the better our estimate of $\mu$. Returning to Equation 5.11, we see that the width of our interval depends on $s$; the smaller the variability of the sample mean, the smaller will be the distance between the two limits. Recalling that $\sigma_{ar{Y}} = \sigma / \sqrt{n}$, it follows that the width of the confidence interval decreases with sample size and with decreased variability. Therefore, we can increase the precision of our estimate by doing collecting as many observations as is to reduce variance as is practical.

A third factor, not obvious in Equation 5.11, also affects the width of the confidence interval: The confidence level we choose. The higher our confidence level, the wider the interval must be. Conceptually, this is like fishing with a large net versus a