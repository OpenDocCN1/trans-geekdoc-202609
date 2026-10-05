
Let's visualize the $p$-value in the null distribution by comparing it to the observed test statistic of $b_1=c(duration=0.371095104397216)$ in Figure 10.15. We'll do this by adding a $shade\_p\_value()$ layer to the previous visualize() code.

## Simulation-Based Null Distribution

![](img/445742518041017e8f01f11b0c3190d9_424_0.png)

FIGURE 10.15: Null distribution and $p$-value.

If the observed fitted slope 0.371 falls far to the right of the shaded region and doesn't overlap it, we'll have a $p$-value of 0. For completeness, however, let's compute the numerical value of the $p$-value anyways using the $get\_p\_value()$ function. Recall that it takes the same inputs as the $shade\_p\_value()$ function:

```
null_distn_slope |>
get_p_value(obs_stat = direction = "both")
```

```
# A tibble: 1 x 1
p_value
<dbl>
1 0
```

This matches the $p$-value of 0 in the regression table. We therefore reject the null hypothesis $H_0: \beta_1=0$ in favor of the alternative hypothesis $H_A: \beta_1 \neq 0$. We thus have evidence that suggests there is a significant relationship between waiting time and duration values for eruptions of Old Faithful.

## 10.4 The multiple linear regression model

When the conditions for inference are met and the null distribution has a bell shape, we are likely to see similar results between the simulation-based results we just demonstrated and the theory-based results shown in the regression table.

## Learning check

(LC10.11) Repeat the inference but this time for the correlation coefficient instead of the slope. Note the implementation of stat = "correlation" in the calculate() function of the infer package.

(LC10.12) Why is it appropriate to use the bootstrap percentile method to construct a 95% confidence interval for the population slope $\beta_1$ in the Old Faithful data?

- A. Because it assumes the slope follows a normal distribution.
- B. Because it relies on resampling the residuals instead of the original data points.
- C. Because it requires the original data to be uniformly distributed.
- D. Because it does not require the bootstrap distribution to be normally distributed.

(LC10.13) What is the role of the permutation test in the hypothesis testing for the population slope $\beta_1$?

- A. It generates new samples to confirm the confidence interval boundaries.
- B. It assesses whether the observed slope could have occurred by chance under the null hypothesis of no relationship.
- C. It adjusts the sample size to reduce sampling variability.
- D. It ensures the residuals of the regression model are normally distributed.

(LC10.14) After generating a null distribution for the slope using infer, you find the $p$-value to be near 0. What does this indicate about the relationship between waiting and duration in the Old Faithful data?

- A. There is no evidence of a relationship between waiting and duration.
- B. The observed slope is likely due to random variation under the null hypothesis.
- C. The observed slope is significantly different from zero, suggesting a meaningful relationship between waiting and duration.
- D. The null hypothesis cannot be rejected because the $p$-value is too small.

## 10.4 The multiple linear regression model

### 10.4.1 The Model

The extension from a simple to a multiple regression model is discussed next. We assume that a population has a response variable $(Y)$ and two or more explanatory variables $(X_1)$

$Y = \beta_0 + \beta_1 \cdot X_1 + \dots + \beta_p \cdot X_p + \epsilon$

$\beta_0$ is the population intercept and $\beta_j$ is the population partial slope related to regressor $X_j$. The error term $\epsilon$ accounts for the portion of $Y$ that is not explained by the line. In some case, we assume that the expected value is $E(\epsilon) = 0$, the standard deviation is $SD(\epsilon) = \sigma$, and the variance $Var(\epsilon) = \sigma^2$. The variance and standard deviation are constant regardless of the value of $X_1, X_2, \dots, X_p$. If we to take a large number of observations from this population, we expect the error terms sometimes to be greater than zero and other times less than zero, but average equal to zero, or take $\sigma$ units away from zero.

### 10.4.2 Example: Coffee quality rating scores

As in the case of simple linear regression we use a random sample to estimate the parameters in the population. To illustrate these methods, we use the coffee_quality data frame from the modernize package. This dataset from the Coffee Quality Institute contains information about coffee rating scores based on ten different attributes: aroma, flavor, aftertaste, acidity, body, balance, uniformity, clean_cup, sweetness, and overall. In addition, the data frame contains other information such as the moisture_percentage and the coffee's country and continent_origin. We can assume that this is a random sample. We plan to regress total_cup_points (response variable) on the numerical variables aroma, flavor, and moisture_percentage and the categorical explanatory variables with four categories: Africa, Asia, North America, and South America. Before proceeding, we construct a data frame called coffee_data by keeping the variables of interest. In addition, the variable continent_origin has been read into R with type character, and we want to make it factor. We do this by using dplyr and the command mutate() inside to make continent_origin a factor with the ordering of "Africa", "Asia", "North America", and "South America".

```
coffee_data <- coffee_quality |>
  select(aroma, flavor, moisture_percentage, continent_origin, total_cup_points) |>
  mutate(continent_origin = as.factor(continent_origin))
```

The first rows of coffee_data are shown here:

coffee_data
# A tibble: 207 x 5

| aroma | flavor | moisture_percentage | continent_origin | total_cup_points |
|---|---|---|---|---|---|
| 1 | 8.58 | 8.5 | 11.8 | South America | 89.33 |
| 2 | 8.5 | 8.5 | 10.5 | Asia | 87.58 |
| 3 | 8.33 | 8.42 | 10.4 | Asia | 87.42 |
| 4 | 8.08 | 8.17 | 11.8 | North America | 87.17 |
| 5 | 8.33 | 8.33 | 11.6 | South America | 87.08 |
| 6 | 8.33 | 8.33 | 10.7 | North America | 87 |
| 7 | 8.33 | 8.17 | 9.1 | Asia | 86.92 |
| 8 | 8.25 | 8.25 | 10 | Asia | 86.75 |
| 9 | 8.08 | 8.08 | 10.8 | Asia | 86.67 |
| 10 | 8.08 | 8.17 | 11 | Africa | 86.5 |

* 197 more rows

By looking at the fourth row we can tell, for example, that the total_cup_points 87.17 with aroma score equal to 8.08 points, flavor score equal to 8.17 points, moisture_percentage equal to 1.8%, and North America is the country_origin. We also display the summary for these variables:

```
coffee_data |>
  tidy_summary()
```

TABLE 10.7: Summary of coffee data

| column | n | type | min | Q1 | mean | median | Q3 | max | sd |
|---|---|---|---|---|---|---|---|---|---|
| aroma | 207 | numeric | 6.50 | 7.58 | 7.72 | 7.67 | 7.92 | 8.58 | 0.288 |
| flavor | 207 | numeric | 6.75 | 7.58 | 7.75 | 7.75 | 7.92 | 8.50 | 0.280 |
| moisture_percentage | 207 | numeric | 0.00 | 10.10 | 10.80 | 11.50 | 13.50 | 13.0 | 1.247 |
| total_cup_points | 207 | numeric | 78.00 | 82.58 | 83.71 | 83.75 | 84.83 | 89.33 | 1.730 |
| continent_of_origin | 23 | factor | | | | | | | |
| continent_of_origin | 84 | factor | | | | | | | |
| continent_of_origin | 67 | factor | | | | | | | |
| continent_of_origin | 33 | factor | | | | | | | |

Observe that we have a sample of 207 observations, the total_cup_points ranges from 6.5 to 8.18, the average aroma score was 7.745, and the median flavor score was 10.8. Note that each observation is composed of $p+1$ values: the values for the explanatory variables $(X_1, \dots, X_p)$ and the value for the response $(Y)$. The sample takes the form:

$(x_{11}, x_{12}, \dots, x_{1p}, y_1)$
$(x_{21}, x_{22}, \dots, x_{2p}, y_2)$
$(x_{n1}, x_{n2}, \dots, x_{np}, y_n)$

where $(x_{i1}, x_{i2}, \dots, x_{ip}, y_i)$ are the values of the $ith$ observation in the sample for $i=1, \dots, n$. Using this notation, for example, $x_{i2}$ is the value of the $ith$ observation in the data for the second explanatory variable $X_2$. In the coffee example $n=207$
