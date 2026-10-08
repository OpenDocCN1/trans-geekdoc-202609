# 10.5.6 Interaction

Now, we include a two-way interaction term between cigar_day and smoke_yrs. From the output, we noted that the interaction terms are not significant, the standard errors for cigar_day and the interaction terms are extremely large. This might point to a numerical issue with the model (Hosmer et al., 2013). So, we may drop the interaction term from our

```
pois_casex = glm(case - cigar_day * smoke_yrs, data = smoke,
family = "poisson", offset = log(person_yrs))
```

```
# Warning: glm.fit: fitted rates numerically @ occurred
```

```
summary(pois_casex)
```

```
##

## Call:

## glm(formula = case - cigar_day * smoke_yrs, family = "poisson",
## data = smoke, offset = log(person_yrs)

## Deviance Residuals:

## Min  1Q  Median Max
## -2.3232  -0.8816  -0.1886  0.4965  1.6851

## Coefficients:

## Estimate Std. Error z value Pr(|z|)
## (Intercept)  -9.2463  1.0000  -9.246 < 2e-16 ***
## cigar_day  -2.8137  319.6350  -0.009  0.992974
## smoke_yrs20-24  -0.7514  1.5114  -0.497  0.619084
## smoke_yrs25-29  -0.2539  1.3518  -0.188  0.851032
## smoke_yrs30-34  1.2493  1.1032  1.132  0.257489
## smoke_yrs35-39  0.5856  1.1660  0.502  0.615438
## smoke_yrs40-44  1.9076  1.0790  1.768  0.036708
## smoke_yrs45-49  2.1070  1.0982  1.919  0.055044
## smoke_yrs50-54  3.0710  1.0761  2.854  0.004318 ***
## smoke_yrs55-59  3.5704  1.0706  3.335  0.000853 ***
## cigar_day:smoke_yrs20-24  2.8609  319.6351  0.009  0.992859
## cigar_day:smoke_yrs25-29  2.8736  319.6350  0.009  0.992827
## cigar_day:smoke_yrs30-34  2.8736  319.6350  0.009  0.992827
## cigar_day:smoke_yrs35-39  2.8997  319.6350  0.009  0.992762
## cigar_day:smoke_yrs40-44  2.8845  319.6350  0.009  0.992980
## cigar_day:smoke_yrs45-49  2.8886  319.6350  0.009  0.992790
## cigar_day:smoke_yrs50-54  2.8869  319.6350  0.009  0.992844
## cigar_day:smoke_yrs55-59  2.8641  319.6350  0.009  0.992851
```