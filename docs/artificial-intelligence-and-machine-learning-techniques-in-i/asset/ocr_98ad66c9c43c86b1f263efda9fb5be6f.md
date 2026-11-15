![](bbox=[0.12, 0.14, 0.88, 0.33])

# FIGURE 3.11 SSGAN results for 400× magnification: (a) accuracy plot and (b) loss plot.

experiment was then stopped at 50% of labeled images since there was no improvement. For all experiments, this work utilized random 20% of data for testing. This evaluation is performed using various magnification factors and metrics listed in Table 3.5. This study proposes a method for breast cancer image classification using compact CNN. Our study compared SSGAN to CNN in order to demonstrate the minimally labeled image achieves good performance compared to the largest number of images labeled in CNN. CNN architecture used in this study was similar to that of the SSGAN discriminator.

# TABLE 3.4 Accuracy Comparisons for Labeled Data using SSGAN Approach.

| Magnifications | 30% | 40% | 50% | 60% |
|---|---|---|---|---|
| 40× | 0.79 | 0.83 | 0.87 | 0.87 |
| 100× | 0.78 | 0.83 | 0.88 | 0.88 |
| 200× | 0.82 | 0.86 | 0.87 | 0.87 |
| 400× | 0.81 | 0.88 | 0.88 | 0.89 |

# TABLE 3.5 SSGAN Performance Metrics for Multiclass Classification.

| Magnification factors | Accuracy | AUC | Specificity | F1-score |
|---|---|---|---|---|
| 40× | 0.87 | 0.92 | 0.86 | 0.87 |
| 100× | 0.88 | 0.94 | 0.88 | 0.86 |
| 200× | 0.87 | 0.92 | 0.87 | 0.86 |
| 400× | 0.88 | 0.95 | 0.87 | 0.87 |