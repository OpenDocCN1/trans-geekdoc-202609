```
wei.mod.ph <- flexsurreg(Survtime, status) - age + surgery + marital,
data = d1, dist = 'weibullPH'
wei.mod.ph
```

```
## Call:
## flexsurreg(formula = Surv(survivtime, status) - age + surgery +
## marital, data = d1, dist = "weibullPH")
## Estimates:
```

| | | L95% | U95% |
|---|---|---|---||
| shape | NA | 0.812800 | 0.772768 | 0.854907 |
| scale | NA | 0.003912 | 0.002645 | 0.005786 |
| age | 48.937500 | 0.042836 | 0.037872 | 0.047499 |
| surgeryYes | | 0.082217 | -0.508126 | -0.608572 | -0.335662 |
| maritalSeparated/divorced/widowed | | 0.148026 | 0.081578 | -0.088939 | 0.252095 |
| maritalSingle | | 0.228618 | 0.288029 | 0.126030 | 0.450028 |
| | | | | |
| exp(list) | L95% | U95% |
| shape | | 0.020945 | NA | NA | NA |
| scale | | 0.000781 | NA | NA | NA |
| age | | 0.002532 | 1.043767 | 1.038599 | 1.048960 |
| surgeryYes | | 0.087991 | 0.601624 | 0.506322 | 0.714865 |
| maritalSeparated/divorced/widowed | | 0.087000 | 1.084998 | 0.914900 | 1.286718 |
| maritalSingle | | 0.082654 | 1.337916 | 1.134316 | 1.568356 |

```
## N = 1824, Events: 989, Censored: 835
## Total time at risk = -5365.418, df = 6
## AIC = 1072.84
```

# 12.4.1 Interpretation of for proportional hazard metric

+   - The log hazard ratio for death among OA patients who underwent surgery to those who did not go for surgery was -0.508 which equals to hazard ratio of 0.60. It means the hazard for death was 39.9% lower in OA patients who went for surgery compared to OA patients who did not undergo surgery, adjusted for age and marital status. The reduction in risk for ranges between 29% and 50% (Adj. HR = 0.601, 95% CI = 0.50,0.71).

+   - An increase of 1 year of age would increase the hazard for death by 0.043 or the risk (hazard) by death by 4.4% when adjusted for marital status and surgery status. The risk for death could increase between 3.9% and 4.9% (Adj. HR = 1.043, 95% CI = 1.039, 1.049).

+   - OA Patients who were separated or divorced had higher risk (hazard) for death by 8.5% as compared to OA patients who were married, adjusted