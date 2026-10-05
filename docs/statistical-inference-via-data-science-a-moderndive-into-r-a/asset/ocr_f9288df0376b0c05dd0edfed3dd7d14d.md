# 326 9 Hypothesis Testing

A p-value is the probability of obtaining a test statistic such as or more extreme than the observed test statistic assuming the null hypothesis $H_0$ is true.

So judging the shaded region in Figure 9.9, it seems somewhat rarely observe differences in popularity rates of 0.034 = 3.4% or more in a hypothesized universe of no difference in genre popularity. In other words, the p-value is somewhat small. Hence, we would be inclined to reject this hypothesized universe, or using statistical language we would "reject $H_0$."

What fraction of the null distribution is shaded? In other words, what is the exact value of the p-value? We can compute using the get_p_value() function with the same arguments as the previous shade_p_value() code:

```
null_distribution |
get_p_value(obs_stat = obs_diff_prop, direction = "right")
```

+   # A tibble: 1 x 1
p_value
<dbl>
1 0.065

Keeping the definition of a p-value as 0.034 = 3.4% due to sampling variation alone in the null distribution is rates as large as 0.065 = 6.5%. Since this p-value is smaller than our pre-specified significance level $\alpha = 0.1$, we reject the null hypothesis $H_0 : P_m - P_d = 0$. In other words, the p-value is sufficiently small to reject our hypothesized universe of no difference in genre popularity. We instead have enough evidence to change our mind in favor of difference in genre popularity being a likely culprit here. Observe whether we reject the null hypothesis $H_0$ or not depends in large part on our choice of significance level $\alpha$. We will discuss this more in Subsection 9.5.3.

# 9.4.2 Comparison with confidence intervals

One of the great things about the infer package is that we can jump seamlessly between conducting hypothesis tests and constructing confidence intervals with minimal changes! Recall the code from the previous section that creates the null distribution, which in turn is needed to compute the p-value: