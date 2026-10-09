For classification, the following evaluation metrics are commonly used:

+   * Accuracy: This measures the proportion of correctly classified instances (both true positives and true negatives) out of the total instances.

+   * Precision: This measures the proportion of true positive predictions out of all positive predictions, focusing on the accuracy of positive predictions.

+   * Recall: This measures the proportion of true positive predictions out of all actual positive instances, focusing on the model's ability to identify all positive instances.

+   * F1 Score: This is the harmonic or weighted mean of precision and recall, providing a balance between precision and recall, especially when dealing with imbalanced classes.

+   * ROC-AUC: Receiver Operating Characteristic Area Under the Curve (ROC-AUC) measures the area under the ROC curve, which plots the true positive rate (sensitivity) against the false positive rate (1 - specificity). It provides an aggregate measure of the model's ability to discriminate between positive and negative classes across different thresholds.

+   * Matthews Correlation Coefficient (MCC): MCC is a correlation coefficient between the observed and predicted binary classifications, considering all four confusion matrix values (true positives, true negatives, false positives, false negatives). It ranges from -1 to 1, with 1 indicating perfect predictions, 0 indicating random predictions, and -1 indicating total disagreement between predictions and observations.