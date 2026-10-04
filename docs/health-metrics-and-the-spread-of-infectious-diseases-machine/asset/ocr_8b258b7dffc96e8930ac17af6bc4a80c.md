# Measures of Machine Learning Models

+   **Precision:** The proportion of true predictions out of all positive predictions made by the model. It is a measure of the model's ability to avoid false positives.

```
$Precision = \frac{TP}{TP + FP} \quad (6.25)$
```

+   **Recall (Sensitivity):** The proportion of true predictions out of all active positive instances in the dataset. It is a measure of the model's ability to identify all positive instances.

```
$Recall = \frac{TP}{TP + FN} \quad (6.26)$
```

+   **Confusion Matrix:** A table that summarises the performance of a classification model, showing the number of true positive (TP), true negative (TN), false positive (FP), and false negative (FN) predictions. It is used to calculate metrics such as accuracy, precision, recall, and specificity.

+   **F1 Score:** The harmonic mean of precision and recall, providing a balanced measure of a model's performance. It is particularly useful when dealing with imbalanced datasets.

```
$F1 = 2 \frac{Precision \times Recall}{Precision + Recall} \quad (6.27)$
```

+   **Receiver Operating Characteristic (ROC):** A graphical representation of the trade-off between true positive rate (sensitivity) and false positive rate (1-specificity) across different thresholds. It is used to evaluate the performance of binary classification models.

```
$TPR = \frac{TP}{TP + FN}; FPR = \frac{FP}{FP + TN} \quad (6.28)$
```

+   **Area Under the Curve (AUC):** The area under the ROC curve, which provides a single value to summarise the model's performance. An AUC of 0.5 indicates a random classifier, while an AUC of 1.0 indicates a perfect classifier.

```
$AUC = \int_{0}^{1} TPR(FPR)dFPR \quad (6.29)$
```

These are only a few of the most common loss functions and evaluation metrics to provide insights into the model's performance to generalize to new data and make accurate predictions.

# 6.4.3 Public Health Loss Functions

“The public may be less interested in environmental quality than in economic prosperity.”
Dubos

In the field of public health the measures of cost mortality and morbidity are used to evaluate the outcome of health and well-being of a population.

The most common analyses methods:¹⁰

+   - Cost-utility, using quality-adjusted life years (QALYs)
- Cost-effectiveness, for specific outcomes, such as life expectancy or medical outcomes.

> ¹⁰Marja Hult et al., “Cost-Effectiveness Calculators for Health, Well-Being and Safety Promotion: A Systematic Review,” The European Journal of Public Health 31, no. 5 (May 2021): 997–1003, doi:10.1093/eurpub/ckab068.