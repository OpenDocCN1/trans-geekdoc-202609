# Table 3.2 Comparison of the most common evaluation parameters used for AI, ML, and DL

| Evaluation parameter | Formula | Object Classification | Object Regression | Object Detection | NLP | Objective |
| --- | --- | --- | --- | --- | --- | --- |
| Accuracy | $Accuracy = \frac{TP + TN}{TP + FP + FN}$ | ✓ | | | | Predict one of the multiple predefined classes. |
| Fl-score | $F1_{score} = 2 * \frac{Precision * Recall}{Precision + Recall}$ | ✓ | | | | Find the balance between precision and recall. |
| Recall | $Recall = \frac{TP}{TP + FN}$ | ✓ | | | | Evaluate a model's ability to identify all positive instances correctly. |
| Precision | $Precision = \frac{TP}{TP + FN}$ | ✓ | | | | Assess the quality of positive predictions. |
| Specificity | $Specificity = \frac{TN}{TP + FN}$ | ✓ | | | | Correctly identify negative instances. |
| AUC-ROC | $AUC = \sum_{i=1}^{N} Rank(TP*) - |TP*|(|TP*| + 1)/2$ | | | | | Assess model discrimination. |
| MAE | $MAE = \frac{1}{N} \sum_{i=1}^{N} |Y_i - \hat{Y}|$ | | ✓ | | | Evaluate the accuracy of the model. |
| MSE | $MSE = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (Y_i - \hat{Y})^2}$ | | ✓ | | | Assess the goodness of fit in the model. |
| RMSE | $RMSE = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (Y_i - \hat{Y})^2}$ | | ✓ | | | Interpretability of the error metric. |