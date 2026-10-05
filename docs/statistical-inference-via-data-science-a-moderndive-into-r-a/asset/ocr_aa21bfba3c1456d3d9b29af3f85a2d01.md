# 6.1 One numerical and one categorical explanatory variable

dummy variable, $D_1$. This does not mean that are losing information of the first level $D_1$. If a country is part of the *Low income* level, $D_1 = 1, D_2 = D_3 = D_4 = 0$, so most of the terms in the regression are zero and the linear regression becomes:

$$\hat{y} = \text{fert rate} = b_0$$

The intercept represents the average fertility rate when a country is a *Low income* country. Similarly, if another country is part of the *High middle income* level, then $D_1=D_2=D_4=0$ and $D_3=1$ so the linear regression becomes:

$$\hat{y} = \text{fert rate} = b_0 + b_3$$

The average fertility rate for a *High middle income* country is $b_0 + b_3$. Observe that $b_3$ is an offset for life expectancy between the baseline level and the *High middle income* level. The same logic applies to the model for each possible income category.

We calculate the regression coefficients using the $lm()$ function and the command $coef()$ to retrieve the coefficients of the linear regression:

```
one_factor_model <- lm(fert_rate ~ income, data = UN_data_ch6)
coef(one_factor_model)
```

We present these results on a table with the mathematical notation used above:

| Coefficients | Values |
|---|---||
| (Intercept) | b0 | 4.28 |
| incomeLower income | b2 | -1.30 |
| incomeUpper middle income | b3 | -2.25 |
| incomeHigh income | b4 | -2.65 |

The first level, *Low income*, is the "baseline" group. The average fertility rate for Low income UN members is 4.28. Similarly, the average fertility rate for Upper middle income members is 4.28 + (-2.25) = 2.03.

We are now ready to study the multiple linear regression model with interactions shown in Figure 6.1. In this figure we identify three different effects. First, for any fixed level of life expectancy, observe that there are four different fertility rates. They represent the effect of the categorical explanatory variable. Second, for any given regression, the slope represents the change in average fertility rate to changes on life expectancy. This is the effect of the numerical explanatory variable $life\_exp$. Third, observe that the slope of the line depends on the income level; as an illustration, observe for *high income* member states the slope is less steep than for Low income members. When the slope changes to changes in the explanatory variable, we call this an **interaction** effect.

The mathematical formulation of the linear regression model with two explanatory variables, one numerical and one categorical, and interactions is: