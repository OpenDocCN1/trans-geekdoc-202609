| Wind speed (Y) (m/s) | Wind direction (X) (degree) |
|---|---|
| 6.51 | 240.7 |
| 6.63 | 237.1 |
| 7.31 | 238.2 |
| 6.45 | 238.9 |
| 6.21 | 240.3 |
| 5.99 | 238.9 |
| 5.64 | 240.1 |
| 5.97 | 249.8 |
| 6.27 | 252.4 |
| 5.46 | 253.3 |

# Table A.1 Wind speed and direction
data for linear regression.

# Example A.8. R codes for linear regression

```
lm.fit<-lm(speed ~ direction)
summary(lm.fit)
```

# Output

Call:
lm(formula = speed ~ direction)
Residuals:
Min 1Q Median 3Q Max
-2.1752 -0.7153 -0.2277 0.8084 3.0242
Coefficients:
Estimate Std. Error t value Pr(>|t|)
(Intercept) 1.87824 3.50950 0.535 0.595
direction 0.01925 0.01388 1.387 0.172
Residual standard error: 1.097 on 48 degrees of freedom
Multiple R-squared: 0.03852, Adjusted R-squared: 0.01849
F-statistic: 1.923 on 1 and 48 DF, p-value: 0.1719

From this R code output we can see that the wind speed is related to wind direction with a mathematical model given as (see Fig. A.5)

speed = 1.87824 + 0.01925 · direction. (A.4)

It is worth noting that the R² value for the current regression problem
is very small. The predictions can be improved further if we use more than
one independent variable.