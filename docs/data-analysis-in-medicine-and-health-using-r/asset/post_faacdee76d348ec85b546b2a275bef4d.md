
## 10.5.5 Multivariable analysis

For the multivariable analysis, we included cigar_day and smoke_yrs as predictors of case.

```r
pois_case = glm(case - cigar_day + smoke_yrs, data = smoke,
    family = "poisson", offset = log(person_yrs))

summary(pois_case)
```

## Call:
## glm(formula = case - cigar_day + smoke_yrs, family = "poisson",
    data = smoke, offset = log(person_yrs))

## Deviances:
## Min 1Q Median 3Q Max
## -2.1066 -0.9440 -0.3337 0.4366 1.7439

## Coefficients:
## Estimate Std. Error z value Pr>|z|)
## (Intercept) -11.31762 1.007492 -11.233 < 2e-16 ***
##   cigar_day 0.064631 0.008601 10.054 < 2e-16 ***
##   smoke_yrs20-24 0.962417 1.015469 0.833 0.40457
##   smoke_yrs25-29 1.718894 1.028420 3.144 0.00167 **
##   smoke_yrs30-34 3.207676 1.020378 3.144 0.0017 **
##   smoke_yrs35-39 3.242776 1.024187 3.166 0.00154 *
##   smoke_yrs40-44 4.208631 1.013726 4.151 3.30e-05 ***
##   smoke_yrs45-49 4.448972 1.017054 4.374 1.22e-05 ***
##   smoke_yrs50-54 4.893674 1.019945 4.798 1.60e-06 ***
##   smoke_yrs55-59 5.372600 1.023404 5.250 1.52e-07 ***

## Signif. codes: 0 '***' 0.001 '** 0.01 * 0.05 . 0.1 1

## (Dispersion parameter for poisson family taken to be 1)

## Null dev: 445.089 on 62 degrees of freedom
## Residual dev: 68.015 on 53 degrees of freedom
## AIC: 207.86
```

From the output, both variables are significant predictors of the rate of lung cancer cases, although we noted the p-values are significant for smoke_yrs20-24 and smoke_yrs25-29 dummy variables as our primary model.

## 10.5.6 Interaction

Now, we include a two-way interaction term between cigar_day and smoke_yrs. From the output, we noted that the interaction terms are not significant, the standard errors for cigar_day and the interaction terms are extremely large. This might point to a numerical issue with the model (Hosmer et al., 2013). So, we may drop the interaction term from our

```r
pois_casex = glm(case - cigar_day * smoke_yrs, data = smoke,
family = "poisson", offset = log(person_yrs))
```

```r
# Warning: glm.fit: fitted rates numerically @ occurred
```

```r
summary(pois_casex)
```

## Call:
## glm(formula = case - cigar_day * smoke_yrs, family = "poisson",
## data = smoke, offset = log(person_yrs))

## Deviance Residuals:
## Min 1Q Median Max
## -2.3232 -0.8816 -0.1886 0.4965 1.6851

## Coefficients:
## Estimate Std. Error z value Pr(|z|)
## (Intercept) -9.2463 1.0000 -9.246 < 2e-16 ***
## cigar_day -2.8137 319.6350 -0.009 0.992974
## smoke_yrs20-24 -0.7514 1.5114 -0.497 0.619084
## smoke_yrs25-29 -0.2539 1.3518 -0.188 0.851032
## smoke_yrs30-34 1.2493 1.1032 1.132 0.257489
## smoke_yrs35-39 0.5856 1.1660 0.502 0.615438
## smoke_yrs40-44 1.9076 1.0790 1.768 0.036708
## smoke_yrs45-49 2.1070 1.0982 1.919 0.055044
## smoke_yrs50-54 3.0710 1.0761 2.854 0.004318 ***
## smoke_yrs55-59 3.5704 1.0706 3.335 0.000853 ***
## cigar_day:smoke_yrs20-24 2.8609 319.6351 0.009 0.992859
## cigar_day:smoke_yrs25-29 2.8736 319.6350 0.009 0.992827
## cigar_day:smoke_yrs30-34 2.8736 319.6350 0.009 0.992827
## cigar_day:smoke_yrs35-39 2.8997 319.6350 0.009 0.992762
## cigar_day:smoke_yrs40-44 2.8845 319.6350 0.009 0.992980
## cigar_day:smoke_yrs45-49 2.8886 319.6350 0.009 0.992790
## cigar_day:smoke_yrs50-54 2.8869 319.6350 0.009 0.992844
## cigar_day:smoke_yrs55-59 2.8641 319.6350 0.009 0.992851

## Signif. codes: 0 '***' 0.001 '** 0.01 * 0.05 . 0.1 1

## (Dispersion parameter for poisson family taken to be 1)

## Null dev: 445.089 on 62 degrees of freedom
## Residual dev: 68.015 on 53 degrees of freedom
## AIC: 207.86
## Number of Fisher iterations: 18

## 10.5.7 Model fit

Again, we assess the model by chi-square goodness-of-fit test, model-to-model AIC comparison and Pearson chi-square statistic and standardized residuals.

```r
dispersion(pois_case)
```

## "Goodness-of-fit test for Poisson assumption"
## $chisq 68.01514
## $df 53
## $p.value 0.080266

The p-value of chi-square goodness-of-fit is more than 0.05, which indicates the model has good fit.

```r
AIC(pois_case1, pois_case2, pois_case)
```

## df
## pois_case1 2 448.5549
## pois_case2 9 308.0129
## pois_case 10 207.8574

The comparison by AIC clearly shows that the multivariable model pois_case is the best as it has the lowest AIC.

## 10.5.8 Poisson Regression for Rate

```r
pois_case_sum = glm(case - cigar_day + smoke_yrs, data = smoke,
            family = "quasipoisson",
            offset = log(person_yrs))
```

The value of dispersion, i.e. the scaled chi-square statistic, is close to 1. This indicates that the model has good fit.

```r
std_res = residuals(pois_case)
abs(std_res) > 1.96
```

## 6 8 18
## -1.99530 -2.02555 -2.25382

Lastly, we noted only a few observations (number 6, 8 and 18) which have discrepancies between the observed and predicted cases. This shows how well the fitted regression model for rate explains the data at hand.

## Presentation and interpretation

Now, we decide on the final,

```r
pois_case_final = pois_case
```

and use tbl_regression() to come up with a table for the results. Again, interpretation, we exponentiate the coefficients to obtain the incidence rate ratio, IRR.

```r
tbl_regression(pois_case_final, exponentiate = TRUE)
```

| Characteristic | IRR | 95% CI | p-value |
|---|---|---|---|
| cigar_day smoke_yrs 15-19 | 1.07 | 1.05, 1.08 | < 0.001 |
| 20-24 | 2.62 | 0.34, 52.9 | 0.4 |
| 25-29 | 5.53 | 0.94, 1.05 | 0.11 |
| 30-34 | 24.7 | 5.23, 442 | 0.002 |
| 35-39 | 25.6 | 5.35, 459 | 0.002 |
| 40-44 | 67.2 | 14.6, 1,195 | < 0.001 |
| 45-49 | 85.5 | 18.3, 1,525 | < 0.001 |
| 50-54 | 133 | 28.3, 2,385 | < 0.001 |
| 55-59 | 215 | 45.1, 3,862 | < 0.001 |

> † Incidence Rate Ratio, CI = Confidence Interval

From this table, we interpret the IRR values as:

- Adding an additional cigar per day increases the risk of having lung cancer by 1.07 (95% CI: 1.05, 1.08), controlling for the other variables.
- Those who have been smoking from 30 to 34 years are at higher risk of having lung cancer with an IRR of 24.7 (95% CI: 5.2), controlling for the other variables.

We now present the final,

```r
write.csv(pois_case_final, "pois_case.csv")
```

We export it to the.

```r
round(summary(pois_case)$coefficients, 2)
```

## Estimate Std. Error z value Pr(|z|)
## (Intercept) -11.32 1.01 -11.23 < 2e-16 ***
## cigar_day 0.06 0.01 10.05 < 2e-16 ***
## smoke_yrs20-24 0.96 1.02 0.83 0.40457
## smoke_yrs25-29 1.72 1.03 3.144 0.00167 **
## smoke_yrs30-34 3.21 1.02 3.144 0.0017 **
## smoke_yrs35-39 3.24 1.02 3.166 0.00154 *
## smoke_yrs40-44 4.21 1.01 4.151 3.30e-05 ***
## smoke_yrs45-49 4.45 1.02 4.374 1.22e-05 ***
## smoke_yrs50-54 4.89 1.02 4.798 1.60e-06 ***
## smoke_yrs55-59 5.37 1.02 5.250 1.52e-07 ***

and put the values in the equation. Remember to include the offset in the equation.

```
ln(case) = ln(person_yrs) - 11.32 + 0.06 * cigar_day
+ 0.96 * smoke_yrs(20 - 24) + 1.71 * smoke_yrs(25 - 29)
+ 3.21 * smoke_yrs(30 - 34) + 3.24 * smoke_yrs(35 - 39)
+ 4.21 * smoke_yrs(40 - 44) + 4.45 * smoke_yrs(45 - 49)
+ 4.89 * smoke_yrs(50 - 54) + 5.37 * smoke_yrs(55 - 59)
```
