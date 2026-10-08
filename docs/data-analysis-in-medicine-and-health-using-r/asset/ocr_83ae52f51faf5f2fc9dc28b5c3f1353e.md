# 120 7 Linear Regression

```
## Call:
```

```
## glm(formula = chol - dbp, data = coronary)
```

```
##
```

```
## Deviance Residuals:
```

```
## Min 1Q Median 3Q Max
```

```
## -1.9967 -0.8304 -0.1292 0.7734 2.8470
```

```
##
```

```
## Coefficients:
```

```
## (Intercept) 2.995134 0.402092 6.087 5.88e-09 ***
```

```
## dbp 0.038919 0.005907 6.589 3.92e-10 ***
```

```
##
```

```
## Signif. codes: 0 **** 0.001 ** 0.01 * 0.05 . .1 ' 1
```

```
## (Dispersion parameter for gaussian family taken to be 1.154763)
```

```
##
```

```
## Null deviance: 278.77 on 199 degrees of freedom
```

```
## Residual deviance: 228.64 on 198 degrees of freedom
```

```
## AIC: 600.34
```

```
##
```

```
## Number of Fisher scoring iterations: 2
```

We can use the glm output and obtain the 95% confidence interval (CI) tidy() from the broom package,

```
tidy(slr_chol, conf.int = TRUE)
```

```
## A tibble: 2 x 7
```

```
## term estimate.error statistic p.value conf.low conf.high
```

```
## <chr> dbl dbl dbl dbl dbl dbl
```

```
## (Intercept) 3.00 0.492 6.09 5.88e- 9 2.03 3.96
```

```
## dbp 0.038919 0.005901 6.589 3.92e-10 0.0273 0.0505
```

From the output, b – column attention at these results:

+   - coefficients estimate.
- 95% CI – columns conf.low and conf.high.
- p-value – column p.value.

# 7.5.4 Model fit assessment

It is important to assess well the SLR model reflects the data. First, we can assess this by R², which is the percentage of the variance for the outcome that is explained by the predictor. In simpler words, to what extent the variation in the values of the outcome is caused/explained by the predictor. This ranges from 0% (the