# 284
Smart Healthcare Systems

# TABLE 20.1
Outcomes of Hyperparameter Tuning

| Batch size | Optimizer | Loss function | Accuracy | Precision | Recall | F1-score |
|---|---|---|---|---|---|---||
| 100 | Adam | Categorical Cross-Entropy | 97.78 | 95.78 | 94.62 | 95.45 |
| | | Mean Squared Error | 91.43 | 92.57 | 93.48 | 92.19 |
| 200 | Random GD | Categorical Cross-Entropy | 89.61 | 88.49 | 84.53 | 86.34 |
| | | Mean Squared Error | 84.58 | 83.27 | 84.31 | 89.52 |
| | Adam | Categorical Cross-Entropy | 87.51 | 89.43 | 89.46 | 86.61 |
| | | Mean Squared Error | 84.27 | 81.28 | 82.39 | 88.37 |
| | Random GD | Categorical Cross-Entropy | 86.19 | 85.27 | 83.48 | 87.42 |
| | | Mean Squared Error | 84.39 | 82.35 | 85.45 | 86.68 |

![](bbox=[0.118, 0.395, 0.882, 0.715])

FIGURE 20.4 The model's predictions and true labels from the test generated ROC curve.

Residual network (ResNet) (Sermanet et al., 2013) is created to solve the issue of disappearing gradients in deep networks. To do this, they skip connections, which let the network learn residual functional residuals rather than direct mappings.

ROC curves for the four models are shown in Figure 20.4 to assess how well the binary classifiers perform detecting faults. The classifier's total effectiveness is gauged by the Area Under the ROC Curve (AUC), where 0.75 as the AUC value of the proposed framework indicates better performance than the others. Since it