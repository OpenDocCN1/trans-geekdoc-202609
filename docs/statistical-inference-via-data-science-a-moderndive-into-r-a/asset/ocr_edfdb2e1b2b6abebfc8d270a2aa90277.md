# 5.3.3 get_regression_x() functions

Recall in this chapter we introduced a wrapper function from the moderndive package:

+   - get_regression_points() that returns point-by-point information from a regression model in Subsection 5.1.3.

What is going on behind the scenes with the get_regression_points() function? We mentioned in Subsection 5.1.2 that this was an example of a wrapper function. Such functions take other pre-existing functions and "wrap" into single functions that hide the user from their inner workings. This all the user needs to worry about is what the inputs look like and what the outputs look like. In this subsection, we'll "get under the hood" of these functions and see how the "engine" of these wrapper functions.

The get_regression_points() function is a wrapper function, returning information about the individual points involved in a regression model like the fitted values, observed values and the residuals. get_regression_points() uses the augment() function in the broom package³ to produce the data shown in Table 5.9. Additionally, it uses clean_names() from the janitor package⁴ (Firke, 2023) to clean up the variable names.

```
library(broom)
library(janitor)
demographics_model |>
augment() |>
mmutate_if(is.numeric, round, digits = 3) |>
clean_names() |>
select(-c("std_resid", "hat", "sigma", "cooksd", "std_resid"))
```

# Table 5.9: Regression points using augment() from broom package

| fert_rate | life_exp | fitted | resid |
|---|---|---|---|
| 4.3 | 53.6 | 5.23 | -0.934 |
| 1.4 | 79.5 | 1.69 | -0.289 |
| 2.7 | 78.0 | 1.89 | 0.813 |
| 5.0 | 62.1 | 4.07 | 0.928 |
| 1.6 | 77.8 | 1.92 | -0.318 |
| 1.9 | 78.3 | 1.85 | 0.052 |
| 1.6 | 76.1 | 2.15 | -0.548 |
| 1.6 | 83.1 | 1.19 | 0.408 |
| 1.5 | 82.3 | 1.30 | 0.195 |
| 1.6 | 74.2 | 2.42 | -0.819 |

> ³https://broom.tidyverse.org/
⁴https://github.com/sfarke/janitor