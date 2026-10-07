
## Additional Topics in Multiple Regression 601

X is referred to as centering. If we subtract the mean from each value of X, Equation 22.2 becomes

```
$\hat{Y} = b_0^c + b_1^c(X - \bar{X}) + b_2^c(X - \bar{X})^2$  (22.5)
```

If we expand this equation and compare it term-by-term with Equation 22.2, we find that $b_2^c = b_2$. That is, the coefficient of the squared term is the same regardless of whether mean is subtracted from X before the regression is performed. This is a general finding. In any kind of polynomial, the regression coefficient of the higher-order term will be the same whether not a constant is subtracted from X. We can also show that the slope of $\hat{Y}$ vs X is $b_1' + 2b_2'(X - \bar{X})$, so we can interpret that the slope at $X = \bar{X}$ is $b_1'$. The significance test allows us to determine whether the slope differs significantly from zero at $X = \bar{X}$.

The mean BMI score for all women in the data set aged 65 years or less with cholesterol level is 26.599. If we let $BMI = BMI - 26.599$ and regress on TC and $BMI^c$, we find that

```
$\tilde{TC} = 26.047 + 2.114 \ BMI - 0.187$  (22.6)
```

Both coefficients for BMI and $BMI^c$ differ significantly from zero; $b_1 = 2.144, t(18) = 3.459, p = .001$; $b_2 = -0.112, t(18) = 3.735, p = .007$. Equations 22.4 and 22.6 are consistent with one another. In Equation 22.4, the constant and coefficient of BMI represent the value of predicted TC and the slope of predicted TC vs BMI = 0 - not useful information, considering that no BMI in the data set have been centered, so the constant and coefficient of BMI represent the values of predicted TC and the slope at the mean of BMI. Centering the predictor also results in lower correlations among the polynomial terms. For example, the correlations between BMI and $BMI^2$, BMI and $BMI^c$, and BMI and $BMI^2$ are .986, .943, and .985, respectively. If BMI is centered, however, the corresponding correlations are .696, .677, and .951. Note that though the constant subtracted from each value of X is usually the mean, any other constant C, may be subtracted, so that the regression coefficient of X - C is the slope at X = C. We can now go on test whether there is a cubic component (so that the curve has two bends), adding $X^3$ to a regression that already contains X and $X^2$. We would get a cubic function, for example, the value of the response variable rise or fall as the value of the predictor increased. In principle, we can test whether curves with two bends by adding larger powers of X to the regression. However, making meaningful predictions about functions with three or more bends, we can test them by adding higher-order polynomial components to the regression.

## 22.7 Testing for Curvilinear Using Quantitative Variables

### Trend Analysis

We have described tests for curvilinear when the predictor(s), $X_1, \dots, X_p$, are continuous variables like BMI. We can also use multiple regression to assess the same type of patterns when the predictors are ordered categorical variables, like age group, grade, or cancer stage; in this case we call it trend analysis. To do, we regress Y first on X, then on $X^2$, then on $X^3$, and so on, to test the increments in variability added to regressions that already contain lower-order components. For example, consider the addition scores for grade one to five in the Royer data that are presented in Table 22.1 and plotted in Figure 22.4. We would expect to find both a linear trend, because the best-fitting line has a positive slope, and a quadratic trend, because we have a negatively curved. The steps in the analysis are illustrated in Table 22.1. If we regress (Y) on grade (X), the variability accounted for by regression is $R^2_{Y,X}=SS_{linear}=4,690.170$. If we regress Y on X and $X^2$, the increment is $SS_{regression}$ that results when $X^2$ is added to a regression equation that already contains X. Similarly, if we regress Y on X, $X^2$, and $X^3$, the increment is $SS_{regression}$ that results when $X^3$ is added to a regression equation that already contains X and $X^2$. All of these trend components have 1 df and can be tested against the groups-within error $MS_{error}$. The ANOVA table in Panel b of Table 22.1 presents the results of the tests. We expect, with $F(1,135)=8.495, p=.004$, respectively. We should note that there are five levels of grade, and 4 df if we treat grade as a categorical variable, the regression of Y on X, $X^2$, and $X^3$ must account for all of the variability in the group means; that is, $R^2_{Y,X,X^2,X^3}SS_{Y}=6,626.772=SS_{Between}$. Just as any two points can be perfectly fit a straight line, all of these trend means can be fit by a fourth-degree polynomial.

Table 22.1 An example of trend analysis with output from SPSS

(a) Percent addition as a function of grade by Royer data

| Grade (X) | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| n | 19 | 28 | 32 | 30 | 26 |
| $\hat{Y}$ | 71.82 | 84.66 | 91.97 | 92.34 | 91.98 |
| s | 30.23 | 15.26 | 8.24 | 7.30 | 9.20 |

(b) Trend analysis for the data in b
$SS_{linear}=R^2_{Y,X}SS_{Y}=4,690.170$
$SS_{quadratic}=(R^2_{Y,X,X^2}-R^2_{Y,X})SS_{Y}=6,553.310-4,690.170=1,863.140$
$SS_{cubic}=(R^2_{Y,X,X^2,X^3}-R^2_{Y,X,X^2})SS_{Y}=6,617.710-6,553.310=64.391$
$SS_{quartic}=(R^2_{Y,X,X^2,X^3,X^4}-R^2_{Y,X,X^2,X^3})$

| Grade | df | MS | F | p |
|---|---|---|---|---|
| Grade | 4 | 6,626.772 | 8.495 | .004 |
| linear | 1 | 4,690.170 | 7.554 | .000 |
| quadratic | 1 | 1,863.140 | 21.385 | .000 |
| cubic | 1 | 64.391 | 0.294 | .589 |
| quartic | 1 | 9.071 | 0.041 | .840 |
| Error | 130 | 219.318 | | |

## 2.8 Including Interaction Terms in Multiple Regression

### 2.8.1 Introduction

The regression equation $\hat{Y} = b_0 + b_1X_1 + b_2X_2$ is additive because the effect on $\hat{Y}$ of changing the values of either predictor does not depend on the value of the other predictor. This kind of model will be unrealistic whenever the relationship between Y and a predictor, $X_1$, is moderated by (i.e., it depends on) another variable $X_2$. In this case we would say we have an interaction between $X_1$ and $X_2$.

We dealt with interactions in detail when we discussed ANOVA. In the context of ANOVA, we have an interaction when the effect of a factor is different for different levels of a second factor. We can translate this thinking directly to multiple regression analyses. However, we can extend the concept when we work with multiple regression because we can deal not only with categorical factors, but with a mix of categorical and quantitative variables. Therefore, it is possible to construct models in which the effect of one factor is a specified function of the levels of a second factor.

### 2.8.2 Testing Interactions between Quantitative and Dichotomous Predictors

Consider the regression of $TC$ on *age* and *sex* for participants in the *남자* who are not older than 65 and have BMI scores no larger than 40. In this data set, sex is coded as a dichotomous categorical variable with participants identifying as male having the value 0 and participants identifying as female having the value 1. The regression output is provided in Figure 22.5, which provides the coefficients for the regression equation

```
$\hat{TC} = 178.009 + 0.900 \ age - 8.645 \ sex$
```
