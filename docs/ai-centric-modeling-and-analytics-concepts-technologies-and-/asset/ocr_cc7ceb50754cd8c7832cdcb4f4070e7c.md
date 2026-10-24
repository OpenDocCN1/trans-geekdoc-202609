# TABLE 12.5
Sensitivity Results.

| Dataset size | Sensitivity (%) using forest fire prediction without ARIMA | Sensitivity (%) using forest fire prediction with ARIMA |
|---|---|---|
| 1000 | 72 | 75 |
| 2000 | 70 | 73.6 |
| 3000 | 65 | 73.2 |
| 4000 | 64 | 72 |
| 5000 | 63 | 71 |

# Sensitivity (%)

![](bbox=[0.08, 0.44, 0.92, 0.75])

# FIGURE 12.3 Sensitivity by Varying Dataset Size.

The last result is in the form of specificity, which is the result in terms of correctly negatively classified instances from the dataset. The specificity is given by Equation 12.3:

```
Specificity = TrueN / (TrueN + FalseP)  (12.3)
```

The results corresponding to specificity are given by Table 12.6.