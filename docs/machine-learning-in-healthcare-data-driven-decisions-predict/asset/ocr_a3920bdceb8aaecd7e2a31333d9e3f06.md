Table 2: The performance of all models averaged over five folds.

| Model | Accuracy (%) | Precision (%) | Recall (%) | F1-score (%) | AUC-ROC (%) |
|---|---|---|---|---|---|
| HRAB (proposed) | 98.1 | 97.8 | 98.5 | 97.9 | 99.2 |
| Random forest | 95.6 | 94.3 | 96.2 | 95.1 | 96.7 |
| XGBoost | 96.4 | 95.5 | 96.9 | 96.1 | 97.4 |
| GBM | 94.1 | 93.2 | 94.8 | 93.9 | 95.2 |
| AdaBoost | 94.6 | 92.7 | 93.4 | 93.0 | 94.6 |
| SVM (RBF) | 92.3 | 91.1 | 90.5 | 90.8 | 92.9 |

Table 3: The HRAB model confusion matrix in one representative fold.

| | Predicted CKD | Predicted non-CKD |
|---|---|---|
| Actual CKD | 118 | 2 |
| Actual non-CKD | 3 | 77 |

uates the model's ability to discriminate. The confusion matrix provided insights into correct and incorrect classifications, and calibration plots assessed the extent to which predicted probabilities agreed with actual outcomes. Finally, individual predictions and feature contributions on the global and local levels were explained using SHAP values.

From Tables 2 and 3, with merely five misclassifications in all, it can be seen with this confusion matrix that the HRAB model was correctly classifying most CKD and non-CKD patients. It proved its capability to handle CKD-positive as well as CKD-negative samples with an approximated recall (sensitivity) of 118/(118 + 2) = 98.3% and specificity of 77/(77 + 3) = 96.2%. The predicted probability strongly correlated with actual outcomes. This characteristic is especially important in clinical practice, where conclusions often are based on anticipated levels of risk rather than pure binary results.

The HRAB model was also explained by evaluating feature contributions via SHAP values as shown in Figure 2. The most significant features for CKD classification, based on a summary bar plot of SHAP values, were BP, albumin, hemoglobin, SC, and eGFR. Specifically, reduced CKD risk was associated with increased eGFR and albumin, while the prevalence of CKD was highly predicted by increased SC and decreased hemoglobin. These findings affirmed the credibility of the model with accepted clinical practice. Figure 3 shows the confusion matrix.

From Figure 4, at 0.97 AUC, the ROC curve of HRAB model further reveals its better discriminative power. This implies that little is lost in terms of true positive versus false positive when employing HRAB to distinguish between CKD and non-CKD instances. Its high sensitivity and specificity are evident in the curve's steep beginning rise and tight closeness to the top-left corner of the graph. The HRAB model correctly clas-