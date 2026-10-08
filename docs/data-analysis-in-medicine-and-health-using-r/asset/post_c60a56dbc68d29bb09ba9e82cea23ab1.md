
# 9.7 Estimation

## Reference group is level 3 of the response
This is the model where hpt is the independent variable

```r
log_hpt <- vglm(cat_fbs - hpt,
   multinomial, data = ms)
summary(log_hpt)
```

## Call:
## vglm(formula = cat_fbs - hpt, family = multinomial, data = ms)
## Coefficients:
| Estimate | Std. Error | z value | Pr(|z|) |
| :--- | :--- | :--- | :--- |
| (Intercept):1 | -1.80412 | 0.04983 | -36.205 < 2e-16 *** |
| (Intercept):2 | -2.28830 | 0.06173 | -37.067 < 2e-16 *** |
| hptyes:1 | 1.00205 | 0.11823 | 8.475 < 2e-16 *** |
| hptyes:2 | 0.96743 | 0.14389 | 6.724 1.77e-11 *** |

## Signif. codes: 0 '***' 0.001 '**' 0.01 '*' 0.05 '.1' 1
## Names of linear predictors: log(mu,[1]/mu[3]), log(mu,[2]/mu[3])

## Residual deviance: 5637.16 on 8174 degrees of freedom
## Log-likelihood: -2818.58 on 8174 degrees of freedom
## Number of Fisher scoring iterations: 4
## No Hauck-Donner effect found in any of the estimates

## Reference group is level 3 of the response
And lastly, the independent variable is weight

```r
log_wt <- vglm(cat_fbs - weight,
   multinomial, data = ms)
summary(log_wt)
```

## Call:
## vglm(formula = cat_fbs - weight, family = multinomial, data = ms)

```r
## Coefficients:
| Estimate | Std. Error | z value | Pr(|z|) |
| :--- | :--- | :--- | :--- |
| (Intercept):1 | -3.214303 | 0.204303 | -15.733 < 2e-16 *** |
| (Intercept):2 | -3.672632 | 0.249121 | -14.742 < 2e-16 *** |
| weight:1 | 0.023860 | 0.002988 | 7.984 1.42e-5 *** |
| weight:2 | 0.023372 | 0.003627 | 6.444 1.16e-10 *** |
---
## Signif. codes: 0 '*** ' 0.001 '**' 0.01 '*' 0.05 '.' 1 '***'
##
## Names of linear predictors: log(mu[1]/mu[3]), log(mu[2]/mu[3])
##
## Residual deviance: 5638.998 on 8172 degrees of freedom
##
## Log-likelihood: -2819.49 on 8172 degrees of freedom
##
## Number of Fisher scoring iterations: 4
##
## Warning: Hauck-Donner effect detected in the following estimate(s):
## '(Intercept):2'
##
## Reference group is level 3 of the response
```

# 9.7.2 Multiple independent variables

We feel that chol, hpt and weight are all important independent variables. Hence, we want to fit a model with the three independent variables as the covariates.

```r
mlog <- vglm(cat_fbs ~ totchol + hpt + weight,
multinomial, data = ms)

summary(mlog)
```

```r
##
## Call:
## vglm(formula = cat_fbs ~ totchol + hpt + weight, family = multinomial,
## data = ms)
##
## Coefficients:
| Estimate | Std. Error | z value | Pr(|z|) |
| :--- | :--- | :--- | :--- |
| (Intercept):1 | -4.907874 | 0.303768 | -16.157 < 2e-16 *** |
| (Intercept):2 | -5.11290 | 0.366325 | -13.958 < 2e-16 *** |
| totchol:1 | 0.277217 | 0.035055 | 7.908 2.62e-05 *** |
| totchol:2 | 0.239413 | 0.042391 | 5.648 1.63e-08 *** |
| hptyes:1 | 0.899987 | 0.120451 | 7.472 7.91e-14 *** |
```

```r
## hptyes:2 0.087136 0.145569 5.957 2e-09 ***
## weight:1 0.022678 0.003074 7.378 1.61e-13 ***
## weight:2 0.021994 0.003710 5.928 3.07e-09 ***
## --
## Signif. codes: 0 '***' 0.001 '*' 0.01 '*' 0.05 '*' 0.1 '*' 1
##
## Names of linear predictors: log(mu[1]/mu[3]), log(mu[2]/mu[3])
##
## Residual deviance: 5476.397 on 8158 degrees of freedom
## --
## Log-likelihood: -2738.19 on 8158 degrees of freedom
## --
## Number of Fisher scoring iterations: 5
## --
## Warning: Hauck-Donner effect detected in the following estimate(s):
## '(Intercept):1, '(Intercept):2'
## --
## Reference group level 3 of the response
```

# 9.7.3 Model with interaction term between independent variables

Then, we hypothesize that there could be significant interaction between totchol and weight. To test the hypothesis, we extend the multivariable logistic regression by adding an interaction term. This interaction term is a product between totchol and weight.

```r
mlogi <- vglm(cat_fbs ~ totchol + hpt + weight + totchol * weight,
multinomial, data = ms)

summary(mlogi)
```

```r
##
## Call:
## vglm(formula = cat_fbs ~ totchol + hpt + weight + totchol * weight, family = multinomial, data = ms)
##
## Coefficients:
| Estimate | Std. Error | z value | Pr(|z|) |
| :--- | :--- | :--- | :--- |
| (Intercept):1 | -5.125325 | 0.967180 | -5.299 1.16e-07 *** |
| (Intercept):2 | -7.050684 | 1.119570 | -6.298 3.02e-10 *** |
| totchol:1 | 0.315574 | 0.160532 | 1.996 0.0493 * |
| totchol:2 | 0.574724 | 0.178790 | 3.059 0.00222 * |
| hptyes:1 | 0.8984459 | 0.1204878 | 7.457 8.87e-14 *** |
| hptyes:2 | 0.8643701 | 0.1455478 | 5.939 2.87e-09 *** |
| weight:1 | 0.0260899 | 0.0142834 | 1.827 0.0676 |
| weight:2 | 0.0514503 | 0.0165054 | 3.117 0.00183 |
| totchol:weight:1 | -0.0006015 | 0.0023804 | -0.253 0.80052 |
| totchol:weight:2 | -0.0051091 | 0.0028023 | -1.823 0.0628 |
---
## Signif. codes: 0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 1
##
## Names of linear predictors: log(mu[1]/mu[3]), log(mu[2]/mu[3])
##
## Residual deviance: 5473.004 on 8166 degrees of freedom
##
## Log-likelihood: -2736.50 on 8166 degrees of freedom
##
## Number of Fisher scoring iterations: 5
##
## Warning: Hauck-Donner effect detected in the following estimate(s):
## '(Intercept):1', '(Intercept):2'
##
## Reference group is level 3 of the response
```

# 9.8 Inferences

For the inference, we will calculate the 95% CI (interval estimates). There is no `broom::tidy()` function to generate confidence intervals, so we use the `coef()` and `conf()` functions to produce a rather nice table. We are going to follow these steps:

- set the number of digits to 2 to limit the decimal numbers
- return the coefficients for all β as an object named b_fitlog2
- return the confidence intervals for all β as an object named ci_fitlog2
- combine the β and the corresponding 95% CIs

# TABLE 9.1
Log odds from multinomial logistic regression

| log odds | Lower CI | Upper CI |
| :--- | :--- | :--- |
| (Intercept):1 | -4.91 | -5.50 | -4.31 |
| (Intercept):2 | -5.11 | -5.83 | -4.40 |
| totchol:1 | 0.28 | 0.21 | 0.35 |
| totchol:2 | 0.24 | 0.16 | 0.32 |
| hptyes:1 | 0.90 | 0.66 | 1.14 |
| hptyes:2 | 0.87 | 0.58 | 1.15 |
| weight:1 | 0.02 | 0.02 | 0.03 |
| weight:2 | 0.02 | 0.01 | 0.03 |

# TABLE 9.2
Log odds and RRR from multinomial logistic regression

| lower b | upper b | RRR | lower RRR | upper RRR |
| :--- | :--- | :--- | :--- | :--- |
| (Intercept):1 | -4.91 | -5.50 | -4.31 | 0.01 | 0.01 |
| (Intercept):2 | -5.11 | -5.83 | -4.40 | 0.01 | 0.01 |
| totchol:1 | 0.28 | 0.21 | 0.35 | 1.32 | 1.23 | 1.41 |
| totchol:2 | 0.24 | 0.16 | 0.32 | 1.27 | 1.17 | 1.38 |
| hptyes:1 | 0.90 | 0.66 | 1.14 | 2.46 | 1.94 | 3.11 |
| hptyes:2 | 0.87 | 0.58 | 1.15 | 2.38 | 1.79 | 3.17 |
| weight:1 | 0.02 | 0.02 | 0.03 | 1.02 | 1.02 | 1.03 |
| weight:2 | 0.02 | 0.01 | 0.03 | 1.02 | 1.01 | 1.03 |

Afterwards, we will exponentiate the coefficients to obtain the **relative-risk ratio**. We then combine the results to the previous table. Finally, we will name the columns of the object `tab_fitmlog`.

```r
b_model <- coef(mlog)
ci_model <- conf(mlog)
b_ci <- data.frame(b_model, ci_model) %>%
rename("log odds" = b_model, "Lower CI" = X2.5.., "Upper CI" = X97.5..) %>%
kbl(digits = 2, booktabs = T, caption = "Log odds from multinomial logistic
regression") %>% kable_styling(position = "center")
```

```r
rr_mlog <- exp(b_ci)
tab_mlog <- cbind(b_ci, rrr_mlog)
colnames(tab_mlog) <- c('b', 'lower b', 'upper b', 'RRR', 'lower RRR', 'upper RRR')
```

# 9.9 Prediction

We can calculate the predicted probability of each category of outcome by using the `predict()` function. Below are the result for the top 10 p-values.
