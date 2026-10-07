# 554 Research Design and Statistical Analysis

3. The R output includes the Residual standard error, 33.6, near the bottom of the report in Figure 20.7. That is the standard error of the estimate. The standard error provides a measure of how well the regression equation predicts cholesterol level. The equation provides a prediction, $\hat{Y}$, for each combination of $X_1$ and $X_2$. The standard error of the estimate, $s_e$, is the square root of the sum of the squared deviations of the actual cholesterol levels from the predicted levels, divided by the $df$, so that

```
$s_e = \sqrt{\frac{\sum(Y_i - \hat{Y}_i)^2}{df}} = \sqrt{\frac{SS_{residual}}{df}}$
```

For the general case in which Y is regressed on p predictor variables, it can be expressed as

```
$s_e = \sqrt{\frac{(1-R^2_{12..p})SS_Y}{N-1-p}}$ (20.10)
```

If the underlying model for the population is $Y_i = \beta_0 + \beta_1X_1 + \beta_2X_2 + \dots + \beta_pX_p + \varepsilon_i$, the standard error of the estimate provides an estimate of the standard deviation of $\varepsilon$.
4. The ANOVA table from R, shown in Figure 20.9, allows us to calculate the total sum of squares accounted with cholesterol levels, 276,210. We also see that it can be partitioned into two components: the sum of squares accounted for by the regression, $SS_{regression}$ equals the sum of $SS$ for *age* and for BMI, and the sum of squares unaccounted for, $SS_{residual}$ where

```
$SS_{regression} = \sum(Y_i - \hat{Y}_i)^2 = R^2SS_Y = 75,221$
```

and

```
$SS_{residual} = \sum(Y_i - \hat{Y}_i)^2 = (1-R^2)SS_Y = 200,989$
```

> > anova(tc.age.bmi)
Analysis of Variance Table

| Response: tc |
| D Sq Mean Sq F value Pr(>F) | |
|---|---|---|---|---||
| age | 1 | 66808 | 66808 | 59.1664 | 9.512e-13 | *** |
| bmi | 1 | 8413 | 8413 | 7.4053 | 0.00698 | ** |
| Residuals | 178 | 200989 | | | 1129 |

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * 0.1 * 1

Figure 20.9 ANOVA table for the regression of total cholesterol level (TC) on age and BMI.