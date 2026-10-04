# Deaths due to Meningitis

from 1990 to 2021 in Sub-Saharan Africa

![](bbox=[0.136, 0.121, 0.863, 0.403])

+   - Central African Republic
- Eswatini
- Lesotho
- Malawi
- Zambia

**Figure 11.1** Deaths due to Meningitis from 1990 to 2021 in Sub-Saharan Africa. The solid ticker line represents the smooth line revealing the overall trend, while the other lines represent the death rates for each country.

To get an idea of the estimated average of death rates in the population, we can fit a simple linear regression model with lm() function, with the formula deaths - 1, which means that we are fitting a model with only an intercept (i.e., no predictors). Then we draw a Q-Q plot² (a scatterplot created by plotting two sets of quantiles against one another) to check the normality of the residuals.

```
mod0 <- lm(deaths - 1, data = meningitis)
summary(mod0)
#
# Call:
# lm(formula = 1, data = meningitis)
#
# Residuals:
# Min 1Q Median 3Q Max
# -17.092 -11.372 -3.745 6.822 32.369
#
# Coefficients:
# Estimate Std. Error t value Pr>|t|)
# (Intercept) 25.826 1.062 24.332 <2e-166 ***
#
# Signif. codes: 0 *** 0.001 ** 0.01 * 0.05 . .1 .
```

> ²-Q-Q Plot," March 20, 2025, https://en.wikipedia.org/w/index.php?title=Q%E2%80%93_plot&coldi=d=12831823.