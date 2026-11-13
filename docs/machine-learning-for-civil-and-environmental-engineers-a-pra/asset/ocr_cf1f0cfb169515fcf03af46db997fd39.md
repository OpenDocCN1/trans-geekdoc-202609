Step 5: Check out the results of the analysis.67 Note that the Random forest leads the board. Also note the close performance between the Random forest and the Gradient Boosted Trees.

![](bbox=[0.09, 0.13, 0.89, 0.5])

| Name | Trained | Train time | Sample weights variable | Accuracy | Precision | Recall | F1 Score | Log Loss | ROC AUC | Calibration Loss |
|---|---|---|---|---|---|---|---|---|---|---|
| Random forest (s2) | 2022-07-28 09:35:47 | 2s | - | 0.87 | 0.87 | 0.90 | 0.88 | 0.40 | 0.99 | 0.23 |
| Gradient Boosted Trees (s2) | 2022-07-28 09:35:05 | 1s | - | 0.90 | 0.91 | 0.92 | 0.91 | 0.29 | 0.99 | 0.22 |
| K Nearest Neighbors (k=5) (s2) | 2022-07-28 09:35:17 | 0s | - | 0.85 | 0.62 | 0.83 | 0.62 | 1.58 | 0.90 | 0.22 |
| Extra trees (s2) | 2022-07-28 09:35:57 | 1s | - | 0.86 | 0.73 | 0.78 | 0.75 | 0.62 | 0.98 | 0.25 |
| SVM (s2) | 2022-07-28 09:40:08 | 0s | - | 0.79 | 0.76 | 0.87 | 0.80 | 0.47 | 0.98 | 0.23 |