# Chapter 23

23.1 (a) r = .509, p = .044.

(b) t' (13.9) = -2.21, p = .044.

(c) We need one dummy variable because there are only two levels of Gender in this data (i) men = 1, women = -1 (or the reverse); (ii) men = 0, women = 1 (or the reverse).

(d) (i) Effect coding:

```
> summary(lm(data = dat,Y ~ Gender))
```

```
Call:
lm(formula = Y ~ Gender, data = dat)
```

Residuals:

| Min 1Q Median 3Q Max |
| -10.375 -3.875 1.312 3.969 7.000 |

Coefficients:

| Estimate Std. Error t value Pr(>|t|) |
| (Intercept) 28.188 1.442 19.55 1.47e-11 *** |
| Gender -3.188 1.442 -2.21 0.0442 * |

Signif. codes: 0 **** .001 *** .01 ** .05 * .01 ' 1

Residual standard error: 5.769 on 14 degrees of freedom
Multiple R-squared: 0.2587, Adjusted R-squared: 0.2057
F-statistic: 4.885 on 1 and 14 DF, p-value: 0.04424

(ii) Dummy Coding:

```
> summary(lm(data = dat,Y ~ Gender))
```

```
Call:
lm(formula = Y ~ Gender, data = dat)
```

Residuals:

| Min 1Q Median 3Q Max |
| -10.375 -3.875 1.312 3.969 7.000 |

Coefficients:

| Estimate Std. Error t value Pr(>|t|) |
| (Intercept) 31.375 2.040 15.38 3.64e-10 *** |
| Gender -6.675 2.884 -2.21 0.0442 * |

Signif. codes: 0 **** .001 *** .01 ** .05 * .01 ' 1

Residual standard error: 5.769 on 14 degrees of freedom
Multiple R-squared: 0.2587, Adjusted R-squared: 0.2057
F-statistic: 4.885 on 1 and 14 DF, p-value: 0.04424