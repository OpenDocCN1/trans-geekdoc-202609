| SIGMA | C | ACCURACY | KAPPA | ACCURACY SD | KAPPA SD |
|---|---|---|---|---|---|
| 0.050398 | 1.00 | 0.791391 | 0.678694 | 0.080339 | 0.126466 |

# 14.4.10 Linear Discriminant Algorithm

# TABLE 14.9 Linear Discriminant Algorithm Performance

| ACCURACY | KAPPA | ACCURACYSD | KAPPASD |
|---|---|---|---|
| 0.8042399 | 0.7038131 | 0.1016816 | 0.159307 |

On the training dataset, the LDA achieved an accuracy level of 80% as in Table 14.9. The Kappa statistic and the Kappa SD were 70% and 0.16, respectively. On the test dataset, the algorithm achieved an accuracy level of 90% and a kappa of 84.64%. The algorithm only misclassified four instances as moderate whose performance is poor in comparison to the CART algorithm.

# 14.4.11 K-Nearest Neighbor

# TABLE 14.10 KNN Algorithm Performance

| K | ACCURACY | KAPPA | ACCURACY SD | KAPPA SD |
|---|---|---|---|---|
| 5 | 0.5988645 | 0.3698931 | 0.1280376 | 0.2158109 |
| 7 | 0.6268864 | 0.4072928 | 0.1564920 | 0.2703504 |
| 9 | 0.6621978 | 0.4715556 | 0.1747903 | 0.2881390 |

The level of accuracy on the training dataset was 66.2%. The best tune parameter for our model was k = 9, or 9 neighbors as shown on the accuracy curve in Figure 14.20. The Kappa statistic and the Kappa SD were 47.2% and 0.17, respectively. On the test dataset, the algorithm achieved an accuracy level of 67.5% and a kappa of 49%. The algorithm was not highly effective in classifying bank performance in comparison to other algorithms.