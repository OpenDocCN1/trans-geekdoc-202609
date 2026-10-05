# 11.2 Case study: Seattle house prices

#  11.2.5 Inference for multiple linear regression

Let's next check the results of our multiple linear regression on house prices using both theory-based and simulation-based methods with hypothesis testing.

Theory-based hypothesis testing for partial slopes

Recall the results of our theory-based inference that were shown when we interpreted the estimate column of get_regression_table(price_interaction) in Table 11.2 and are shown in what follows. We can now use these values to perform hypothesis tests on the partial slopes.

```
price_interaction <- lm(log10_price ~ log10_size * condition,
data = house_prices)
get_regression_table(price_interaction)
```

# TABLE 11.3: Regression table for interaction model

| term | estimate | std_error | p_value | lower_ci | upper_ci |
|---|---|---|---|---|---||
| intercept | 3.330 | 0.451 | 7.380 | 0.000 | 2.446 | 4.215 |
| log10_size | 0.690 | 0.148 | 4.652 | 0.000 | 0.399 | 0.980 |
| condition: 2 | 0.047 | 0.498 | 0.094 | 0.925 | -0.930 | 1.024 |
| condition: 3 | -0.367 | 0.452 | -0.812 | 0.417 | -1.253 | 0.519 |
| condition: 4 | -0.398 | 0.457 | -0.879 | 0.380 | -1.286 | 0.490 |
| condition: 5 | -0.883 | 0.453 | -1.931 | 0.053 | -1.286 | 0.013 |
| log10_sizecondition2 | -0.024 | 0.163 | -0.148 | 0.882 | -0.344 | 0.295 |
| log10_sizecondition3 | 0.133 | 0.148 | 0.893 | 0.372 | -0.158 | 0.424 |
| log10_sizecondition4 | 0.146 | 0.149 | 0.979 | 0.328 | -0.146 | 0.437 |
| log10_sizecondition5 | 0.310 | 0.150 | 2.067 | 0.039 | 0.016 | 0.604 |

For this model, we can perform hypothesis tests on the partial slopes with a significance level set to 0.05. For example, we can test the null hypothesis that the partial slope for log10_size is zero. Looking at the p-value in the row corresponding to log10_size we see a value of 0 and a large statistic of 4.652. With α = 0.05, log10_size is the only regressor with a statistically significant relationship with log10_price in this theory-based model.

# Simulation-based hypothesis testing for partial slopes

We can also perform hypothesis tests on the partial slopes using simulation-based methods. We can use the fit() function and some of the other verba to do so to check the results of our theory-based inference.