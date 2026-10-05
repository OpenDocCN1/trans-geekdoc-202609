simple_model |>
get_regression_points() |>
filter(ID = 57)

| ID | fert_rate | life_exp | fert_rate_hat | residual |
| 57 | 1.8 | 82.6 | 1.26 | 0.542 |

We retrieve this information for each observation. Here we show the first few rows:

simple_model |>
get_regression_points()

# A tibble: 183 x 5

| ID <int> | <dbl> | <dbl> | <dbl> | <dbl> |
| 1 | 4.3 | 53.65 | 5.237 | -0.937 |
| 2 | 1.4 | 79.47 | 1.687 | -0.287 |
| 3 | 2.7 | 78.03 | 1.885 | 0.815 |
| 4 | 5.0 | 62.11 | 4.074 | 0.926 |
| 5 | 1.6 | 77.78 | 1.916 | -0.316 |
| 6 | 1.9 | 78.31 | 1.846 | 0.054 |
| 7 | 1.6 | 76.13 | 2.146 | -0.546 |
| 8 | 1.6 | 83.09 | 1.189 | 0.411 |
| 9 | 1.5 | 82.27 | 1.302 | 0.198 |
| 10 | 1.6 | 74.15 | 2.418 | -0.818 |

# i 173 more rows

This concludes our review of material covered in Section 5.1. We now explain how to use this information for statistical inference.

# 10.1.2 The Model

As we did in Chapters 8 on confidence intervals and 9 on hypothesis testing, we present this problem in the context of a population and associated parameters of interest. We collect a random sample from this population and use it to estimate these parameters.

We assume that this population has a response variable (Y), an explanatory variable (X), and there is a statistical linear relationship between these variables, given by the linear model