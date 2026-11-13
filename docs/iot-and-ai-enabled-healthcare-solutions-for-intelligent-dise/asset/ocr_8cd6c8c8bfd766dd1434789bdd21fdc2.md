# # 1.3.1.3 Measuring Accuracy

A confusion matrix is a key tool to evaluate a classification model. It gives you a breakdown of the model’s predictions so you can see the accuracy, precision, recall and other metrics in detail in Table 5.

+   - **True Positives (TP):** Where it finds out the exact position of class.
+   - **True Negatives (TN):** Where it finds out the negative nature of class.
+   - **False Positives (FP):** Where it finds out the negative class as positive.
+   - **False Negatives (FN):** Where it finds out the positive class as negative.

The Confusion Matrix has the following metrics in the classification report: accuracy, precision, recall, F1-score, and specificity. Accuracy is the percentage of values that were expected. Precision is the percentage of positive values that were correctly predicted. The recall can be described as the proportion of true positives and all positively forecasted cases while precision is the percentage of perfect positive forecasts among all positively anticipated instances. F1-Score is the Harmonic mean of precision and recall. The specificity represents the proportion of truly recognized negatives to actual negatives.

# **Table 5. Structure of confusion matrix.**

| | Positive Prediction | Negative Prediction |
|---|---|---|
| Actually Positive | TP = 48 | FN = 0 |
| Actually Negative | FP = 2 | TN = 25 |

# # 1.3.1.4 Classification Report

The Classification report is crucial for evaluating the effectiveness of a classification version across one-of-a-kind instructions. It enables to perceive which lessons the version is appearing well on and which training it struggles with, guiding further enhancements and tuning of the version. For instance, high precision but low recall is taking into account a category suggests the model is conservative in predicting magnificence, likely lacking a few actual positives. Conversely, bear in mind that low precision suggests the model captures most positives but additionally includes many false positives. By inspecting those metrics, statistics scientists can benefit from a deeper expertise in their model’s strengths and weaknesses, ensuring higher decision-making in model selection and optimization. In Table 6, there is a classification report corresponding to the dataset after applying the K-Nearest Neighbor Algorithm to the Cardiovascular disease dataset.

This algorithm has an accuracy score of 97% which is a significant value, making it outperform other classification algorithms.