# 10.6 Simulation-based inference for multiple linear regression

# 10.6.2 Hypothesis testing for the partial slopes using infer

We can also conduct hypothesis tests for the partial slopes in multiple linear regression. We use the permutation test to null the hypothesis $H_0 : eta_i = 0$ versus the alternative hypothesis $H_A : eta_i 
eq 0$ for each of the partial slopes. The infer package constructs the null distribution of the partial slopes under the null hypothesis of independence.

# Null distribution for the partial slopes

We can also compute the null distribution for the partial slopes using the infer workflow. We will shuffle the values of the response variable total_cup_points across the values of the regressors continent_of_origin, aroma, flavor, and moisture_percentage in the coffee_data dataset. This is done under the assumption of independence between the response and the regressors. The syntax is similar to constructing the bootstrap distribution, but we use type="permute" and set hypothesis to null="independence". We set our pseudo-random number generation to 2024 in order for the reader to get the results with the shuffling.

```
set.seed(2024)
null_distribution_mlr <- coffee_quality |>
specific(total_cup_points - continent_of_origin + aroma +
flavor + moisture_percentage) |>
hypothesize(null = "independence") |>
generate(reps = 1000, type = "permute") |>
fit()
ull_distribution_mlr
```

```
# A tibble: 7,000 x 3
# Groups: replicate [1,000]
replicate term                 estimate
<int> <chr>                    dbl
1 1 intercept                   82.3301
2 1 continent_of_originAsia   -0.193739
3 1 continent_of_North America  -0.371403
4 1 continent_of_originSouth America  -0.0830304
5 1 aroma                      -1.21891
6 1 flavor                    1.52397
7 1 moisture_percentage      -0.0747986
8 2 intercept                   82.0068
9 2 continent_of_originAsia   -0.239054
10 2 continent_of_North America  -0.617409
# i 6,990 more rows
```