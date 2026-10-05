# 10.5.2 Confidence intervals

A 95% confidence interval for any coefficient in multiple linear regression is constructed exactly the same way as we did for simple linear regression, but we should always interpret them as dependent on the model for which they were attained.

For example, the formula for a 95% confidence interval for $eta_1$ is given by $b_1 \pm q \cdot SE(b_1)$ where the critical value $q$ is determined by the level of confidence required, the sample size used $(n)$, and the corresponding degrees of freedom needed for the $t$-distribution $(n-p)$. In the coffee example, the $model\_mod\_mult$ contains

+   - three numerical regressors (aroma, flavor, and moisture_content),
- one factor (continent_of_origin),
- the confidence level is 95%,
- the sample size is $n=207,
- the number of regression coefficients is $p=7$:
- three partial slopes for aroma, flavor and moisture_content ($b_1, b_2,$ and $b_3$),
- three coefficients for the factor levels in the model ($b_{02}, b_{03},$ and $b_{04}$).

So the degrees of freedom are $n-p=207-7=200$.

The 95% confidence interval for the partial slope of $b_1$ aroma is determined

> $b_1 \pm q \cdot SE(b_1)
= 1.73 \pm 1.97 - 0.22
= (1.29, 2.17)$

The interpretation of this interval is the customary: “We are 95% confident that the population partial slope for aroma $(eta_1)$ in the model $mod\_mult$ is a number between 1.29 and 2.17."

We find these values using $regression\_table(mod\_mult, table)$. This time, however, we use the argument $conf.level=0.98$ to get 98% confidence intervals.

```
get_regression_table(mod_mult, conf.level = 0.98)
```

# TABLE 10.12: The regression table for mod_mult with 98% level

| term | estimate | std_error | statistic | p_value | lower_ci | upper_ci |
|---|---|---|---|---|---|--|
| intercept | 37.321 | 1.116 | 33.445 | 0.000 | 34.705 | 39.938 |
| aroma | 1.732 | 0.222 | 7.800 | 0.000 | 1.211 | 2.252 |
| flavor | 4.316 | 0.226 | 19.090 | 0.000 | 3.786 | 4.846 |
| moisture_percentage | -0.008 | 0.030 | -0.277 | 0.781 | -0.078 | 0.062 |
| continent_of_origin: Asia | -0.393 | 0.121 | -3.244 | 0.001 | -0.678 | -0.108 |
| continent_of_origin: North America | -0.273 | 0.127 | -2.153 | 0.035 | -0.571 | -0.025 |
| continent_of_origin: South America | -0.478 | 0.142 | -3.368 | 0.001 | -0.810 | -0.146 |