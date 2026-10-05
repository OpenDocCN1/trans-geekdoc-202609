
## 10.5 Theory-based inference for multiple linear regression

Using multiple regression we compute the least-square estimates $b'_1$ and $b'_3$, respectively, with the $'$ denoting potentially different coefficient values in this different model. The results using the $coffee\_data$ are calculated and stored in the $mod\_mult\_2$ and shown below:

```r
# Fit regression model:
mod_mult_2 <- lm(
  total_cup_points ~ aroma + moisture_percentage, data = coffee_data)
```

```r
# Get the coefficients of the model
coef(mod_mult_2)
sigma(mod_mult_2)
```

**TABLE 10.11:** Coffee example linear regression coefficients

| (Intercept) | | | |
|---|---|---|---|
| | b'0 | 44.010 | |
| aroma | b'1 | 5.227 | |
| moisture_percentage | b'3 | -0.062 | |
| | s' | 0.857 | |

We focus on the partial slope for aroma using both models. Observe that in $mod\_mult\_1$, the partial slope for aroma is $b_1 = 1.8$. In model $mod\_mult\_2$, the slope for aroma is $b'_1 = 5.23$. The results are truly different because the models used in each case are different. Similarly, every other coefficient found is different, and it is possible the inferential results for confidence intervals or hypothesis tests are different too!

Any results, conclusions, and interpretations of a regressor are only valid for the model used. For example, interpretations or conclusions about aroma and its effects or influence in $total\_cup\_points$ are entirely dependent on whether we have used $mod\_mult\_1, mod\_mult\_2$, or another model. Never assume that a conclusion from one model can translate to a different model.

In addition, it is important to determine which model is the most adequate. Clearly, not both $mod\_mult\_1$ and $mod\_mult\_2$ are correct, and we would like to use the one that is most appropriate. What if neither $mod\_mult\_1$ nor $mod\_mult\_2$ are adequate, and we should use another model instead? There are two areas in inferential statistics that address these questions. The first area involves comparisons between regressors from the other, as in the coffee example where $mod\_mult\_1$ used the regressors aroma and moisture\_percentage while $mod\_mult\_2$ used only two of these regressors: aroma and moisture\_percentage. We discuss methods addressing this comparison in Subsection 10.5.3. The second area is called model selection or variable selection and uses alternative methods to determine which model, out of the possible available is the most adequate.

### 10.5.2 Confidence intervals

A 95% confidence interval for any coefficient in multiple linear regression is constructed exactly the same way as we did for simple linear regression, but we should always interpret them as dependent on the model for which they were attained.

For example, the formula for a 95% confidence interval for $\beta_1$ is given by $b_1 \pm q \cdot SE(b_1)$ where the critical value $q$ is determined by the level of confidence required, the sample size used $(n)$, and the corresponding degrees of freedom needed for the $t$-distribution $(n-p)$. In the coffee example, the $model\_mod\_mult$ contains:

- three numerical regressors (aroma, flavor, and moisture_content),
- one factor (continent_of_origin),
- the confidence level is 95%,
- the sample size is $n=207$,
- the number of regression coefficients is $p=7$:
- three partial slopes for aroma, flavor and moisture_content ($b_1, b_2,$ and $b_3$),
- three coefficients for the factor levels in the model ($b_{02}, b_{03},$ and $b_{04}$).

So the degrees of freedom are $n-p=207-7=200$.

The 95% confidence interval for the partial slope of $b_1$ aroma is determined:

$b_1 \pm q \cdot SE(b_1) = 1.73 \pm 1.97 - 0.22 = (1.29, 2.17)$

The interpretation of this interval is the customary: “We are 95% confident that the population partial slope for aroma $(\beta_1)$ in the model $mod\_mult$ is a number between 1.29 and 2.17."

We find these values using $regression\_table(mod\_mult, table)$. This time, however, we use the argument $conf.level=0.98$ to get 98% confidence intervals.

```r
get_regression_table(mod_mult, conf.level = 0.98)
```

**TABLE 10.12:** The regression table for mod_mult with 98% level

| term | estimate | std_error | statistic | p_value | lower_ci | upper_ci |
|---|---|---|---|---|---|---|
| intercept | 37.321 | 1.116 | 33.445 | 0.000 | 34.705 | 39.938 |
| aroma | 1.732 | 0.222 | 7.800 | 0.000 | 1.211 | 2.252 |
| flavor | 4.316 | 0.226 | 19.090 | 0.000 | 3.786 | 4.846 |
| moisture_percentage | -0.008 | 0.030 | -0.277 | 0.781 | -0.078 | 0.062 |
| continent_of_origin: Asia | -0.393 | 0.121 | -3.244 | 0.001 | -0.678 | -0.108 |
| continent_of_origin: North America | -0.273 | 0.127 | -2.153 | 0.035 | -0.571 | -0.025 |
| continent_of_origin: South America | -0.478 | 0.142 | -3.368 | 0.001 | -0.810 | -0.146 |

The interpretation for the coefficient for flavor, for example, is: "We are 98% confident the value of $\beta_2$ (the population partial slope for flavor) is between 3.79 and 4.85."

### 10.5.3 Hypothesis test for a single coefficient

The hypothesis test for one coefficient, say $\beta_1$ in the model, is similar to the one for simple linear regression. The general formula for a two-sided test is:

$H_0: \beta_1 = B$ with $\beta_0, \beta_2, \dots, \beta_p$ given arbitrary.
$H_A: \beta_1 \neq B$ with $\beta_0, \beta_2, \dots, \beta_p$ given and arbitrary.

where $B$ is the hypothesized value for $\beta_1$. We make emphasis in stating that $\beta_0, \beta_2, \dots, \beta_p$ are given arbitrary to acknowledge that. Any results, conclusions, and interpretations of a regressor are only valid for the model used. For example, interpretations or conclusions about aroma and its effects or influence in $total\_cup\_points$ are entirely dependent on whether we have used $mod\_mult\_1, mod\_mult\_2$, or another model. Never assume that a conclusion from one model can translate to a different model.

In addition, it is important to determine which model is the most adequate. Clearly, not both $mod\_mult\_1$ and $mod\_mult\_2$ are correct, and we would like to use the one that is most appropriate. What if neither $mod\_mult\_1$ nor $mod\_mult\_2$ are adequate, and we should use another model instead? There are two areas in inferential statistics that address these questions. The first area involves comparisons between regressors from the other, as in the coffee example where $mod\_mult\_1$ used the regressors aroma and moisture\_percentage while $mod\_mult\_2$ used only two of these regressors: aroma and moisture\_percentage. We discuss methods addressing this comparison in Subsection 10.5.3. The second area is called model selection or variable selection and uses alternative methods to determine which model, out of the possible available is the most adequate.

The interpretation for the coefficient for flavor, for example, is: "We are 98% confident the value of $\beta_2$ (the population partial slope for flavor) is between 3.79 and 4.85.
