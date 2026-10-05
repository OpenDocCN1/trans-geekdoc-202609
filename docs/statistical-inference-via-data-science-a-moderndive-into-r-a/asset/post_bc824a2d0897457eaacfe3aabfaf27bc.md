
## 10.4 The multiple linear regression model

```r
coffee_data |
  select(aroma, flavor, moisture_percentage) |
  summary() |
  select(min, max)
```

| column | min | max |
|---|---|---|
| aroma | 6.50 | 8.58 |
| flavor | 6.75 | 8.50 |
| moisture_percentage | 0.00 | 13.50 |

As we see, only moisture_percentage includes zero in its range, and we would need to include numerical regressors in order for the intercept to have a special meaning in the context of the model. Observe that we have decided to use only a subset of regressors and construct a model without interactions. We discuss in Subsection 10.5 how we determine what is the best subset of regressors to use when many are available. We are now ready to discuss inference for multiple regression.

## Learning check

In a linear regression model, what does the coefficient $\eta_j$ represent?
- A. The intercept of the model.
- B. The standard error of the estimate.
- C. The total variance explained by the model.
- D. The partial slope related to other regressors.

Why is it necessary to convert continent_of_origin to a factor when preparing the coffee_data frame for regression?
- A. To allow the regression model to interpret continent_of_origin as a numerical variable.
- B. To create dummy variables representing different categories of continent_of_origin.
- C. To reduce the number of observations in the dataset.
- D. To ensure the variable is included in the correlation matrix.

What is the purpose of creating a scatterplot matrix in multiple linear regression?
- A. To identify outliers that need to be removed from the dataset.
- B. To test for normality of residuals.
- C. To examine relationships between variable pairs and identify multicollinearity.
- D. To determine the appropriate number of dummy variables.

In the multiple regression model for coffee_data, what is the role of dummy variables continent_of_origin?
- A. They are used to predict the values of numerical regressors.
- B. They modify the intercept based on the specific category of continent_of_origin.
- C. They serve to test the independence of residuals.
- D. They indicate which observations should be excluded from the model.

## 10.5 Theory-based inference for multiple linear regression

In this section, we introduce some of the conceptual framework needed to understand inference in multiple regression. We illustrate this framework using the coffee example and the R function `summary()` introduced in Subsection 10.2. Inference for multiple regression is a natural extension of inference for simple regression. Recall that the i-th observation is given by $y_i = \beta_0 + \beta_1 \cdot x_{i1} + \cdots + \beta_p x_{ip} + \epsilon_i$. We assume again that the error term is normally distributed with an expected value (mean) equal to zero and a standard deviation equal to $\sigma$: $\epsilon_i \sim \text{Normal}(0, \sigma)$. Since the error term is the only random element in the linear model, the response $y_i$ results from a constant $\beta_0 + \beta_1 \cdot x_{i1} + \cdots + \beta_p x_{ip}$ and a random variable: the error term $\epsilon_i$. Using properties of the normal distribution, the expected value, and the variance (and standard deviation), it can be shown that $y_i$ is also normally distributed with mean equal to $\beta_0 + \beta_1 \cdot x_{i1} + \cdots + \beta_p x_{ip}$ and standard deviation equal to $\sigma$: $y_i \sim \text{Normal}(\beta_0 + \beta_1 \cdot x_{i1} + \cdots + \beta_p x_{ip}, \sigma)$.

For $i=1,...,n$, we also assume that $\epsilon_i$ and $\epsilon_j$ are independent, and $y_i$ and $y_j$ are also independent for $i=j$. Moreover, the least-squares estimators $(\hat{b}_0, \hat{b}_1, \dots, \hat{b}_p)$ are linear combinations of the random variables $y_1, \dots, y_n$, which are normally distributed, as shown above. Again, following properties of the normal distribution, the expected value, and the variance it can be shown that:

- the (least-squares) estimators follow a normal distribution,
- the estimators are unbiased, meaning the expected value for each estimator is the parameter they are estimating; for example $E(\hat{b}_1) = \beta_1$, or in general $E(\hat{b}_j) = \beta_j$ for $j=0,1,...,p$.
- the variance and standard deviation of each estimator $(\hat{b}_j)$ is a function of $\sigma$, and the observed data for the explanatory variable (the values of the regressors in the sample). For simplicity, the standard deviation of the estimator $\hat{b}_j$ is denoted by $SD(\hat{b}_j)$ but remember that it is a function of the standard deviation of the response $(\sigma)$.
- Using the information above, the distribution of the (least-squares) estimator $\hat{b}_j$ is given by:

$$\hat{b}_j \sim Normal(\beta_j, SD(\hat{b}_j))$$

for $j=1,...,p$. Note also that $\sigma$ is typically unknown, and it is estimated using the estimated standard deviation $s$ instead of $\sigma$. The estimated standard deviation for $b_j$ is called the standard error of $b_j$ and written as $SE(b_j)$. Again, remember that the standard error is a function of $s$.

The standard errors are shown when applying the `get_regression_table()` function on a regression model. This is the output for `mod_mult`:

```r
get_regression_table(mod_mult)
```

#### TABLE 10.9: The regression table for mod_mult
| term | estimate | std_error | statistic | p_value | lower_ci | upper_ci |
|---|---|---|---|---|---|---|
| (Intercept) | 37.321 | 1.116 | 33.445 | 0.000 | 35.121 | 39.521 |
| aroma | 1.732 | 0.222 | 7.800 | 0.000 | 1.294 | 2.170 |
| flavor | 4.316 | 0.226 | 19.090 | 0.000 | 3.870 | 4.762 |
| moisture_percentage | -0.068 | 0.030 | -2.267 | 0.023 | -0.127 | 0.051 |
| continent_of_origin: Asia | -0.393 | 0.121 | -3.240 | 0.001 | -0.632 | -0.154 |
| continent_of_origin: North America | -0.273 | 0.127 | -2.150 | 0.033 | -0.524 | -0.023 |
| continent_of_origin: South America | -0.478 | 0.142 | -3.380 | 0.001 | -0.757 | -0.199 |

## 10.5.1 Model dependency

Many inference methods and results for multiple regression are a direct extension of the methods and results for simple regression. The most important difference is the fact that the least-squares estimators represent partial slopes and their values are dependent on the other regressors. If we change the set of regressors used in a model, the least-squares estimates and its standard errors will likely change as well. And these changes will lead to different confidence interval limits, different test statistics for hypothesis tests, and potentially different conclusions about regressors.

Using the coffee_data example, suppose that we consider the model:

$y_i = \beta_0 + \beta_1 \cdot x_{i1} + \beta_2 \cdot x_{i2} + \beta_3 \cdot x_{i3} + \epsilon_i$

$\beta_1, \beta_2$, and $\beta_3$, are the parameters for the partial slopes of aroma, flavor, and moisture_percentage, respectively. Recall that we assume that the parameters $\beta_1, \beta_2$, and $\beta_3$ are constants, unknown to us, but constants. We use multiple regression and find the least-square estimates $b_1, b_2$, and $b_3$, respectively. The results using the coffee_data are calculated and stored in the object mod_mult_1 and shown below:

```r
# Fit regression model:
mod_mult_1 <- lm(total_cup_points ~ aroma + flavor + moisture_percentage,
data = coffee_data)
```

```r
# Get the coefficients of the model
coef(mod_mult_1)
sigma(mod_mult_1)
```

#### TABLE 10.10: Coffee example linear regression coefficients

| | Coefficients | |
|---|---|---|
| (Intercept) | b0 | 36.778 |
| aroma | b1 | 1.800 |
| flavor | b2 | 4.285 |
| moisture_percentage | b3 | -0.015 |
| | s | 0.521 |
