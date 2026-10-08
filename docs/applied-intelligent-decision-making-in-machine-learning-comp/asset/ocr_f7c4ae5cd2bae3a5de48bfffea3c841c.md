# Applied Intelligent Decision Making in Machine Learning

TABLE 2.4

the kNN Model Evaluation Confusion Matrix and Performance Parameters for Identification of Grassy and Clover Species Dataset

# Confusion Matrix

| Actual/Predicted | Grassy | Clover |
|---|---|--|
| Grassy | 33 | 4 |
| Clover | 3 | 32 |
| Performance | Grassy | Clover | Macro-Average | Weighted Average |
|---|---|---|---|--|
| Support* | 36 | 36 | 72 | 72 |
| Precision | 0.92 | 0.88 | 0.90 | 0.90 |
| Recall | 0.89 | 0.91 | 0.90 | 0.90 |
| F-score | 0.90 | 0.89 | 0.90 | 0.90 |
| Accuracy | 90% | | | |

Note: Refer to Figure 2.9 for details.
Support is the number of samples in each class.

# Problem

How to classify weed species that have similar color?

![](bbox=[0.128, 0.481, 0.293, 0.552])

Accuracy = 90%

![](bbox=[0.513, 0.563, 0.853, 0.762])

# Solution

+   * Input features (train and test data)
* Diameter range
* Feret aspect ratio
* Solidity

![](bbox=[0.335, 0.648, 0.433, 0.712])

FIGURE 2.9 The kNN classification of grassy and clover weed species using the features, such as diameter range, Feret aspect ratio, and solidity.

The precision and F-score (Equations (2.20) and (2.22)) were the highest for the grassy class with values at 0.92 and 0.90, respectively, while the recall (Equation (2.21)) value was the highest for the clover class at 0.91. The macro- and weighted average for precision, recall, and F-score were the same at 0.90. Misclassification was observed in both the weed species; however, it was less than 10%. As the model