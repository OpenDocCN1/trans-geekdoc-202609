# 10.6 Simulation-based inference for multiple linear regression

# Getting the observed fitted model

We will revisit our full model on the coffee_data with the factor of content_of_origin and three numerical regressors in aroma, flavor, and moisture_percentage. As we did with hypothesis testing in Chapter 9 and in Section 10.3.2, we can retrieve the observed statistic. In this case, we get the observed coefficients of the model using the specify() function on our full model with formula syntax combined with fit():

```
observed_fit <- coffee_data |>
specify(
  total_cup_points ~ aroma + flavor + moisture_percentage +
continent_of_origin
 |>
fit()
oberved_fit
```

```
# A tibble: 7 x 2
term estimate
<chr> <dbl>
1 intercept 37.3214
2 aroma 1.73160
3 flavor 4.31600
4 moisture_percentage -0.00807976
5 continent_of_originAsia -0.392936
6 continent_of_originNorth America -0.273427
7 continent_of_originSouth America -0.478137
```

As we would expect, these values match up with the values of mod_mult_table given in the first two columns there:

mod_mult_table

# TABLE 10.16: The regression table for mod_mult

| | estimate | std_error | statistic | p_value | lower_ci | upper_ci |
|---|---|---|---|---|---||}{
| intercept | 37.321 | 1.116 | 33.45 | 0.000 | 34.705 | 39.938 |
| aroma | 1.732 | 0.222 | 7.80 | 0.000 | 1.211 | 2.252 |
| flavor | 4.316 | 0.226 | 19.09 | 0.000 | 3.786 | 4.846 |
| moisture_percentage | -0.008 | 0.030 | -0.27 | 0.787 | -0.078 | 0.062 |
| continent_of_origin: Asia | -0.393 | 0.121 | -3.24 | 0.001 | -0.678 | -0.108 |
| continent_of_origin: North America | -0.273 | 0.127 | -2.15 | 0.033 | -0.571 | 0.025 |
| continent_of_origin: South America | -0.478 | 0.142 | -3.38 | 0.001 | -0.810 | -0.146 |