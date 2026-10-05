# 10.6 Simulation-based inference for multiple linear regression

From these visualizations, we can discern that aroma and flavor are statistically significant, as their observed statistics fall far to the right of the null distribution. On the other hand, moisture_percentage is not statistically significant, as its observed test statistic falls within the null distribution. We can also compute the numerical p-values using the get_p_value() function.

```
null-distribution_mlr |
get_p_value(obs_stat = observed_fit, direction = "two-sided")
```

| term p_value |
| <chr> <dbl> |
|1 aroma 0.034 |
2 continent_of_originAsia 0.332 |
3 continent_of_originNorth America 0.56 |
4 continent_of_originSouth America 0.352 |
5 flavor 0 |
6 intercept 0 |
7 moisture_percentage 0.918 |

These results match up with our findings from the visualizations of the shaded p-values with the null distribution and in the regression table in Table 10.13. We reject the null hypothesis $H_0 : \beta_i = 0$ for aroma and flavor, but fail to reject it for moisture_percentage.

# Learning check

(LC10.23) Why might one prefer to use simulation-based methods (e.g., bootstrapping) for inference in multiple linear regression?

+   - A. Because simulation-based methods require larger sample sizes than theory-based methods.
- B. Because simulation-based methods are always faster to compute than theory-based methods.
- C. Because simulation-based methods guarantee the correct model is used.
- D. Because simulation-based methods do not rely on the assumptions of normality or large sample sizes.

(LC10.24) What is the purpose of constructing a bootstrap distribution for the partial slopes in multiple linear regression?