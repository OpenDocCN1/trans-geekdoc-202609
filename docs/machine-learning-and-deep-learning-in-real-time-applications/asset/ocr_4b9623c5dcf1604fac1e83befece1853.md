Confusion Matrix: The confusion matrix can be represented as follows:

| | Predicted/Classified | | |
|---|---|---|
| Actual | Negative | Positive |
| Negative | True Negative (TN) | False Positive (FP) |
| Positive | False Negative (FN) | True Positive (TP) |

Where -
True Positive (TP) = Number of positive instances correctly classified as positive.
False Positive (FP) = Number of positive instances incorrectly classified as negative.
True Negative (TN) = Number of negative instances correctly classified as negative.
False Negative (FN) = Number of negative instances incorrectly classified as positive

+   * Accuracy: Accuracy indicates the closeness of a predicted or classified value to its real value. The state of being correct is Accuracy. It can be calculated as:

Accuracy= (TP+TN)/(TP+TN+FP+FN)

+   * Precision: Precision can be defined as the number of relevant items selected out of the total number of items selected. It represents the probability that an item is relevant. It can be calculated as:

Precision = TP/(FP+TP)

Precision is the measure of exactness.

+   * Recall: The Recall can be defined as the ratio of relevant items selected to relevant items available. The recall represents a probability that a relevant item is selected. It can be calculated as:

Recall = TP/(FN+TP)

The recall is the measure of completeness.

+   * F1-Measure: F1-Measure is the harmonic mean between Precision and Recall as described below:

F1-Measure= 2 * (Precision * Recall) / (Precision+Recall)

It creates a balance between precision and recall. Accuracy may be affected by class imbalance but F1 Measure is not affected by class imbalance. So with accuracy F1-measure is also used for evaluation of classification algorithms.