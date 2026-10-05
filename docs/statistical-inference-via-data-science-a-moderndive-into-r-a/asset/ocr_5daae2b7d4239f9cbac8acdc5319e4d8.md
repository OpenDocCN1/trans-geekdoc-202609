328

9 Hypothesis Testing

```
visualize(bootstrap_distribution) + shade_confidence_interval(endpoints = percentile_ci)
```

# Simulation-Based Bootstrap Distribution

![](bbox=[0.118, 0.193, 0.882, 0.413])

FIGURE 9.10: Percentile-based 95% confidence interval.

A key value that is not included in the 95% confidence interval for $p_m-p_d$: the value 0 (but just barely!). In other words, a difference of 0 is not included in our net, suggesting that $p_m$ and $p_d$ are truly different! Furthermore, observe how the entirety of the 95% confidence interval for $p_m-p_d$ lies above 0, suggesting that this difference is in favor of metal.

# Learning check

(LC9.1) Why does the following code produce an error? In other words, what about the response and predictor variables make this not a possible computation with the infer package?

```
library(modernverse)
library(infer)
null_distribution_mean <- spotify_metal_dephouse |
specify(formula = popular_or ~ track_genre, success = "popular") |nhypothesis(null = "independence") |
generate(reps = 1000, type = "permute") |>
calculate(stat = "diff in means", order = c("metal", "deep-house"))
```