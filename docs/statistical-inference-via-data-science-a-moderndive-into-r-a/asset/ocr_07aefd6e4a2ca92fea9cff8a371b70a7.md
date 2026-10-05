# 6.1 One numerical and one categorical explanatory variable

```
# Fit regression model and get the coefficients of the model
model_int <- lm(fert_rate, life_exp * income, data = UN_data_ch6)
coef(model_int)
```

# TABLE 6.2: Regression table for interaction model

| | Coefficients | Values |
---|---|---|
| (Intercept) | b0 | 11.918 |
| incomeLower middle income | b02 | -1.504 |
| incomeUpper middle income | b03 | -1.893 |
| incomeHigh income | b04 | -6.580 |
| life_exp | b1 | -0.118 |
| incomeLower middle income:life_exp | b12 | 0.013 |
| incomeUpper middle income:life_exp | b13 | 0.011 |
| incomeHigh income:life_exp | b14 | 0.072 |

We can match the coefficients with the values computed: the fitted fertility rate
$y$ = fert rate for Low income countries is

> $fert \ rate = b_0 + b_1 \cdot x = 11.92 + (-0.12) \cdot x$,

which is the equation of the regression line in Figure 6.1 for low income countries.
The regression has an equation of 11.92 and a slope of -0.12. Since life expectancy
gre than zero for all countries, the intercept has no practical interpretation
 we only need to produce the most appropriate line. The interpretation of the
slope is: for Low income countries, every additional year of life expectancy reduces the
average fertility rate by 0.12 units.

As discussed earlier, the intercept and slope for all the other income groups are de-
terminated by taking into account the appropriate offsets. For, High income
countries $D_4 = 1$ and all other dummy variables are equal to zero. The regression
line becomes

> $y = fert rate = b_0 + b_1x + b_{04} + b_{14}x = (b_0 + b_{04}) + (b_1 + b_{14})x$

where $x$ is life expectancy, $life\_exp$. The intercept is (Intercept) + incomeHigh income

> $b_0 + b_{04} = 11.92 + (-6.58) = 5.34$,

and the slope for these High income countries is $life\_exp + life\_exp:incomeHigh income
corresponding to

> $b_1 + b_{14} = -0.12 + 0.07 = -0.05$.