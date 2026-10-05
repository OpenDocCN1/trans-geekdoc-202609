# 5 Simple Linear Regression

We can obtain the values of the intercept $b_0$ and the slope for $life\_exp$ $b_1$ by outputting the linear regression coefficients. This is done in two steps:

+   - We first "fit" the linear regression model using the lm() function and save it in demographics_model.
- We get the regression coefficients by applying coef() to demographics_model.

```
# Fit regression model:
demographics_model <- lm(fert_rate ~ life_exp,
                          data = UN_data_ch5)

# Get regression coefficients
coef(demographics_model)
```

We first focus on interpreting the regression coefficients, and later revisit the code that produced it. The coefficients are the intercept $b_0 = 12.599$ and the slope $b_1 = -0.137$ for $life\_exp$. Thus the equation of the regression line in Figure 5.3 follows:

> $$\hat{y} = b_0 + b_1 \cdot x$$
$$fertility\rate = b_0 + b_{life\expectancy} \cdot life\expectancy\n=12.599 + (-0.137) \cdot life\expectancy$$

The intercept $b_0 = 12.599$ is the average fertility rate $\hat{y} = fertility\_rate$ for countries that have a $life\_exp$ of 0. In graphical terms, where the line intersects the $y$ axis for $x = 0$. However, that while the intercept of the regression line has a $life\_exp$ of 0 is impossible. Furthermore, looking at the scatterplot with the regression line in Figure 5.3, no countries have a life expectancy anywhere near 0.

Of interest is the slope $b_1 = b_{life\_expectancy}$ for $life\_exp$ of -0.137. This measures the relationship between the fertility rate and life expectancy variables. Note that the sign is negative, suggesting a negative relationship between these two variables. This means countries with higher life expectancies tend to have lower fertility rates. Recall from earlier that the correlation coefficient is -0.812. They both have the same negative sign, but a different value. Recall further that the correlation's interpretation is the "strength of linear association." The slope's interpretation is a little different:

For every increase of 1 unit in $life\_exp$, there is an associated decrease of, on average, 0.137 units of $fert\_rate$.