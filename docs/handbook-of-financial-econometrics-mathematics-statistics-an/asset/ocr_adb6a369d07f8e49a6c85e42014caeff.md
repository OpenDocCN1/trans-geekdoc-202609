# Table 44.2: Results of experiments with the ES-based AL_q G-SVM on ACD.

| Fold number | T1 (%) | T2 (%) | T (%) | Optimized (λ, σ², q) |
|---|---|---|---|---|
| 1 | 95.45 | 88.46 | 91.67 | (1.26, 0.85, 1.02) |
| 2 | 86.36 | 86.54 | 86.46 | (1515.35, 1.00, 2.00) |
| 3 | 86.36 | 92.31 | 89.58 | (11.38, 2.98, 2.00) |
| 4 | 93.18 | 86.54 | 89.58 | (1.00, 1.00, 2.00) |
| 5 | 100.00 | 84.62 | 91.67 | (1.00, 260.62, 2.00) |
| Average | 92.27 | 87.69 | 89.79 |  |

# Table 44.3: Results of experiments with the ES-based AL_q G-SVM on GCD.

| Fold number | T1 (%) | T2 (%) | T (%) | Optimized (λ, σ², q) |
|---|---|---|---|---|
| 1 | 75.00 | 90.00 | 79.41 | (1.00, 1.00, 2.00) |
| 2 | 70.83 | 95.00 | 77.94 | (7.18, 17.01, 1.80) |
| 3 | 70.83 | 85.00 | 75.00 | (1.00, 1.00, 2.00) |
| 4 | 65.63 | 85.00 | 71.32 | (1.50, 1.62, 1.00) |
| 5 | 64.58 | 82.50 | 69.85 | (53.75, 1.00, 1.00) |
| Average | 69.38 | 87.50 | 74.71 |  |

of the five training subsets of each dataset, penalty forms and total accuracies of every UCI dataset are not robust. This means data structures of these data sets are not robust.

We compare our model with 11 other paper major credit analysis models in the two UCI datasets, i.e., linear discriminant analysis (LDA), decision-based See5, logistic regression (LogR), decision tree (DT), k-nearest neighbor classifier (k-NN) with k = 10, MCCQP, SVM light, GA-based SVM, MK-MCP and CBA. Results of LDA, See5, LogR, DT, k-NN, MCCQP, SVM light, GA-based SVM are from (e.g., see Li et al., 2011; Peng et al., 2008), MK-MCP are from (e.g., see Wei, 2008) and CBA are from (e.g., see Liu et al., 1998).

Table 44.4 summarizes the results of the two UCI datasets compared with other popular models with fixed penalty forms. With respect to ACD, ES-based AL_q G-SVM performs best in Total accuracy and Type 1 accuracy, i.e., 89.79% and 92.27%; Type 2 accuracy is 87.69%, which is also competitive. With respect to GCD, the results of ES-based AL_q G-SVM are also satisfactory. Though Type 1 accuracy is a little lower, Type 2 accuracy and Total accuracy are satisfactory. Type 2 accuracy is 87.5% which is the best; Total accuracy is 74.71%, which is better than the popular LDA, QDA, See5, DT, k-NN, MCCQP, SVM light and CBA. In general, the experiment results