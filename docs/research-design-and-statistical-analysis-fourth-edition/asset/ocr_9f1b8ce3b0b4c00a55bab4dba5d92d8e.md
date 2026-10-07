# Additional Topics in Multiple Regression 603

![](bbox=[0.238, 0.096, 0.735, 0.323])

**Figure 22.4** Plot of percent addition accuracy vs grade using standard errors as error bars.

# 22.8 Including Interaction Terms in Multiple Regression

# **22.8.1 Introduction**

The regression equation $\hat{Y} = b_0 + b_1X_1 + b_2X_2$ is additive because the effect on $\hat{Y}$ of changing the values of either of the predictors does not depend on the value of the other predictor. This kind of model will be unrealistic whenever the relationship between Y and a predictor, $X_1$, is moderated by (i.e., it depends on the value taken on by) another variable $X_2$. In this case we would say we have an interaction between $X_1$ and $X_2$.

We dealt with interactions in detail when we discussed ANOVA. In the context of ANOVA, we have an interaction when the effect of a factor is different for different levels of a second factor. We can translate this thinking directly to multiple regression analyses. However, we can extend the concept when we work with multiple regression because we can deal not only with categorical factors, but with a mix of categorical and quantitative variables. Therefore, it is possible to construct models in which the effect of one factor is a specified function of the levels of a second factor.

# **22.8.2 Testing Interactions between Quantitative and Dichotomous Predictors**

Consider the regression of $TC$ on *age* and *sex* for participants in the *남자* who are not older than 65 and have BMI scores no larger than 40. In this data set, sex is coded as a dichotomous categorical variable with participants identifying as male having the value 0 and participants identifying as female having the value 1. The regression output is provided in Figure 22.5, which provides the coefficients for the regression equation

```
$\hat{TC} = 178.009 + 0.900 \ age - 8.645 \ sex$
```

Equation 22.7 is a misleading representation of the relationship of $TC$ on *age* and *sex* because the relationship between $TC$ and *age* differs for the male- and female-identifying