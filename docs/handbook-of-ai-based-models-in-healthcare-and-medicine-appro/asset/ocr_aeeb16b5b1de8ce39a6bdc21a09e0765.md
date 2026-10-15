# (i) Ultrasound

As observed from the accuracy and loss plots of Figure 8.5, it is evident that ResNet-50 resulted in better validation of ultrasound data classification than the other two networks. The confusion matrix in Figure 8.4 is used to extract the performance measures in Table 8.2. From Table 8.2, it is significant that the ensemble model has yielded better performance than the other individual networks. For the ultrasound dataset, the precision of ResNet-50 is next-best to the ensemble model.

![](bbox=[0.12, 0.35, 0.92, 0.48])

# FIGURE 8.3 Confusion of MRI data classification.

# TABLE 8.1
Performance Measures of MRI Data Classification.

| Model | Class | Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|---|
| VGG-16 | Malignant | 91.6 | 0.94 | 0.89 | 0.91 |
|  | Benign |  | 0.90 | 0.94 | 0.92 |
| ResNet-50 | Malignant | 80.6 | 0.80 | 0.79 | 0.79 |
|  | Benign |  | 0.81 | 0.82 | 0.81 |
| Inception V3 | Malignant | 78.2 | 0.73 | 0.84 | 0.78 |
|  | Benign |  | 0.84 | 0.73 | 0.77 |
| Ensemble | Malignant | 95.9 | 0.96 | 0.95 | 0.95 |
|  | Benign |  | 0.95 | 0.96 | 0.95 |

![](bbox=[0.12, 0.82, 0.92, 0.93])

# FIGURE 8.4 Confusion of ultrasound data classification.