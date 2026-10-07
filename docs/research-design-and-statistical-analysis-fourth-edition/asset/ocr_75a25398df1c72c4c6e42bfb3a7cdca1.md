# 502 Research Design and Statistical Analysis

students and obtain values of X (pretest score) and Y (final exam score) from each student, so that both X and Y are random variables.

We regressed Y (reaction time) on X (display size) using the methods described in Section 17.6.6. The results from R are shown in Figure 19.2; Although the reports are organized differently, the analyses agree. We see that the bivariate regression equation best predicts reaction time (Y) from array size (X) is

```
Ŷ = 381.90 + 23.92X₁
```

(In the SPSS output, these coefficients are in the column labeled "Unstandardized B.") The regression reports also display t tests for the significance of b₀ and b₁ᵢ; in each case the t statistic is the ratio of the coefficient to its standard error. We see that both the slope and the intercept are significantly different from zero at p < .001. SPSS standardized the coefficients as well; these values are the intercept and slope of the regression of z_y on z_x. Because the line must pass through the origin when the variables are standardized, the intercept must be 0. The standardized slope, or beta coefficient, has the same value as the correlation coefficient in bivariate regression.

In the model table of the SPSS output, we see the multiple correlation coefficient, R_yx = Corr (Y, YŶ) = .873. This is the correlation between the actual value of Y and YŶ the value of Y predicted from the regression equation. For bivariate regression, the multiple correlation is the absolute value of r_xy, because the magnitude of a correlation is unchanged by a linear transformation. Note that the multiple correlation coefficient can never be negative. The R output does not include R_xy but provides its square, Multiple R-squared.

```
Call:
lm(formula = Time ~ Size, data = dat)
```

Residuals:

| Min 1Q Median 3Q Max |
|---|---|---|---|---|
| -59.58 -22.75 -2.16 21.24 46.42 |

Coefficients:

| Estimate Std. Error t value Pr(>|t|) |
|---|---|---|---|---|
| (Intercept) 381.900 17.227 22.169 1.2e-14 *** |
| Size 23.920 3.145 7.605 5.00e-07 *** |

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * 0.1 . 1

Residual standard error: 31.45 on 18 degrees of freedom
Multiple R-squared: 0.7627, Adjusted R-squared: 0.7495
F-statistic: 57.84 on 1 and 18 DF, p-value: 5e-07

Figure 19.2 Regression output for the search experiment example, using the summary and lm functions in R.