# Employee Churn Management Using AI 189

when we tested the model with the unseen data or test data then we got an accuracy of 0.987733333333334 which is slightly lower than train data.

# 11.4 COMPARISON

To compare the performance of these algorithms we used various parameters like Confusion Matrix and F1 score (Table 11.2). Confusion matrix is 2-dimensional having 4 distinct parameters like True positive, True Negative, False positive and False negative.

Confusion Matrix is shown in Figure 11.10.

+   TP: Model predicted Positive and its True
TN: Model predicted Negative and its True
FP: Model predicted Positive but its False
FN: Model predicted Negative but it False

# TABLE 11.2 Model performance comparison

| Accuracy | Confusion Matrix | F1 Score |
|---|---|--|
| KNN | 0.9586 | [2766 88] [67 829] | 0.9145 |
| Random Forest | 0.9864 | [2846 8] [43 853] | 0.9709 |
| XGBoost | 0.9877 | [2863 8] [38 841] | 0.9733 |

![](bbox=[0.273, 0.654, 0.726, 0.896])

FIGURE 11.10 Confusion Matrix.