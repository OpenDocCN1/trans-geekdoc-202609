```
## Coefficients:
## Estimate Std. Error z value Pr(|z|)
## (Intercept):1 -3.214303 0.204303 -15.733 < 2e-16 ***
## (Intercept):2 -3.672632 0.249121 -14.742 < 2e-16 ***
## weight:1 0.023860 0.002988 7.984 1.42e-5 ***
## weight:2 0.023372 0.003627 6.444 1.16e-10 ***
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

We feel that colch, hpt and weight are all important independent variables. Hence, we want to fit a model with the three independent variables as the covariates.

```
mlog <- vglm(cat_fbs ~ totchol + hpt + weight,
multinomial, data = ms)

summary(mlog)
```

```
##
## Call:
## vglm(formula = cat_fbs ~ totchol + hpt + weight, family = multinomial,
## data = ms)
##
## Coefficients:
## Estimate Std. Error z value Pr(|z|)
## (Intercept):1 -4.907874 0.303768 -16.157 < 2e-16 ***
## (Intercept):2 -5.11290 0.366325 -13.958 < 2e-16 ***
## totchol:1 0.277217 0.035055 7.908 2.62e-05 ***
## totchol:2 0.239413 0.042391 5.648 1.63e-08 ***
## hptyes:1 0.899987 0.120451 7.472 7.91e-14 ***
```