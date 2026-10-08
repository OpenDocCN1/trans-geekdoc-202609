# Actual

| | High traffic | Low traffic | Total |
|---|---|---|---||
| Predicted | High stress | 67 | 8 | 75 |
| | Low stress | 19 | 45 | 64 |
| | Total | 86 | 53 | 139 |

**Figure 6.** Confusion matrix of the model using the traffic condition datasets.



In the second method for road type prediction, where driving in cities was recognized as a high stress state and highway as a low stress state, the statistical method reached 82.9% with sensitivity of 81%, specificity of 84%, and positive predictivity of 65%. Table 6 shows the developed model including all used predictors for road type segments.

**Table 6.** Model based on different types of road segments.

| Predictor | Coefficient | p-Value |
|---|---|--|
| Min OD | 0.011 | 0.031 |
| Max OD | 0.000 | 0.977 |
| Sum OD | | 0.378 |
| Mean OD | -0.009 | 0.240 |
| Mean OM | -128.868 | 0.604 |
| Max OM | -1.864 | 0.918 |
| Min OM | 18.381 | 0.976 |
| Sum OM | 4.682 | 0.176 |
| SD OM | 94.897 | 0.383 |
| N | -0.062 | 0.145 |
| Constant | 3.740 | 0.218 |

The binary logistic regression model for road type segments that Min OD is significant ($p < 0.05$). For road type model goodness of fit was presented by Cox and Snell and Nagelkerke R-square with values of 0.374 and 0.518, respectively. As the traffic condition model, pseudo-Rsquared was obtained through SPSS Statistics Software (Version 23). Figure 7 shows the confusion matrix of the model developed by the road types.

# Actual

| | City driving | Highway driving | Total |
|---|---|---|---||
| Predicted | High stress | 71 | 6 | 77 |
| | Low stress | 14 | 26 | 40 |
| | Total | 85 | 32 | 117 |

**Figure 7.** Confusion matrix of the model using the road type datasets.