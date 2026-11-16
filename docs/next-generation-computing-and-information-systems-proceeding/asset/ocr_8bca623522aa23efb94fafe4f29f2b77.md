At first, the values of the parameters such as accuracy, recall, precision, as well as F1 score for the entire dataset have been generated based on the confusion matrix values to evaluate the performance of the employed algorithms (Table 2).

# Table 2. Analysis of classifiers using hypertension dataset.

| Classifiers | Accuracy | Precision | Recall | F1Score |
| :--- | :--- | :--- | :--- | :--- |
| Voting Classifier | 95.39 | 0.96 | 0.95 | 0.95 |
| Gradient Boosting | 98.43 | 0.99 | 0.98 | 0.98 |
| Adaboost | 91.56 | 0.92 | 0.91 | 0.91 |
| XGBoost | 100 | 1.00 | 1.00 | 1.00 |
| CatBoost | 100 | 1.00 | 1.00 | 1.00 |
| LGBM | 100 | 1.00 | 1.00 | 1.00 |
| MLP | 89.86 | 0.92 | 0.89 | 0.89 |

The Voting Classifier exhibits an accuracy of 95.39%, with balanced precision, recall, and F1 score values at 0.96, 0.95, and 0.95, respectively. Gradient Boosting surpasses others with an impressive accuracy of 98.43% and outstanding precision at 0.99, recall at 0.98, and F1 score at 0.98. AdaBoost, whereas having a relatively lower accuracy at 91.56%, still maintains good precision of 0.92, F1 score and recall of 0.91. CatBoost, XGBoost, and LGBM demonstrate flawless performance with a perfect accuracy of 100% and impeccable precision, recall, and F1 score all at 1.00. Lastly, the MLP model lags behind others with an accuracy of 89.86% and slightly lower precision, recall, and F1 score at 0.92, 0.89, and 0.89. In summary, Gradient Boosting, XGBoost, CatBoost, and LGBM stand out as top performers by achieving a perfect accuracy and optimal precision, recall, and F1 score. Besides, the execution of the algorithms have been evaluated for different two classes of the dataset i.e. hypertensive (class 1) and non-hypertensive (class 0) whose results are mentioned in Table 3.

# Table 3. Examining the performance of classifiers for different classes of hypertension dataset.

| Classifiers | Precision | Recall | F1Score | Precision | Recall | F1Score |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| | \multicolumn{3}{c}{Hypertensive} | \multicolumn{3}{c}{Non-hypertensive} |
| Voting Classifier | 0.96 | 0.93 | 0.94 | 0.94 | 0.97 | 0.95 |
| Gradient Boosting | 1.00 | 0.96 | 0.98 | 0.97 | 1.00 | 0.99 |
| Adaboost | 0.91 | 0.90 | 0.91 | 0.92 | 0.93 | 0.92 |
| XGBoost | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| CatBoost | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| LGBM | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| MLP | 0.99 | 0.78 | 0.87 | 0.85 | 0.99 | 0.92 |

Voting classifier performed well with hypertensive and non-hypertensive class of the dataset by computing 0.96 and 0.97 as a precision, 0.93 and 0.97 as a recall , which results in 0.94 and 0.95 F1 score respectively. Likewise, Gradient Boosting achieved a perfect precision (1.00) for hypertensive case and high recall (0.96), leading to a strong F1 score of 0.98. For non-hypertensive cases, it exhibits perfect recall and slightly lower precision, resulting in a F1 score of 0.99. Adaboost performed reasonably well with balanced precision and recall for both classes, leading to an F1 score of 0.91 for hypertensive and 0.92 for non-hypertensive cases. XGBoost, CatBoost, and LGBM outperform with perfect precision, recall, and F1 score for both classes which indicates their flawless performance in classifying both