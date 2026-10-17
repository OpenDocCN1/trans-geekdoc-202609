```
```text
#> 1 (Intercept)  4.62    0.00239      1932.  0
#> 2 log(LEAD)    0.00891 0.00118        7.53 5.34e-14
#> 3 AGE          0.00349 0.0000457     76.4  0
#> 4 SEXMale      0.0254  0.00155       16.4  2.06e-60
```
```

Another component that we may want to add to our model is an interaction term. For example, we may consider an interaction between sex and blood lead level. We add an interaction to the formula using a : between the two variables. The output shows that the coefficient for this interaction is indeed significant.

```
```r
model_interaction <- lm(log(SBP) ~ log(LEAD) + AGE + SEX +
                         SEX:log(LEAD), data=nhanes_df)

summary(model_interaction)
#>
#> Call:
#> lm(formula = log(SBP) ~ log(LEAD) + AGE + SEX + SEX:log(LEAD),
#>     data = nhanes_df)
#>
#> Residuals:
#>      Min       1Q   Median       3Q      Max
#> -0.6981 -0.0816 -0.0049  0.0752  0.6599
#>
#> Coefficients:
#>
#>                     Estimate Std. Error t value Pr(>|t|)
#> (Intercept)         4.62e+00   2.39e-03  1936.2  <2e-16 ***
#> log(LEAD)           2.36e-02   1.68e-03    14.1  <2e-16 ***
#> AGE                 3.45e-03   4.58e-05    75.3  <2e-16 ***
#> SEXMale             3.32e-02   1.67e-03    19.9  <2e-16 ***
#> log(LEAD):SEXMale  -2.66e-02   2.16e-03   -12.3  <2e-16 ***
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#>
#> Residual standard error: 0.128 on 30400 degrees of freedom
#> Multiple R-squared:  0.219, Adjusted R-squared:  0.219
#> F-statistic: 2.13e+03 on 4 and 30400 DF, p-value: <2e-16
```
```