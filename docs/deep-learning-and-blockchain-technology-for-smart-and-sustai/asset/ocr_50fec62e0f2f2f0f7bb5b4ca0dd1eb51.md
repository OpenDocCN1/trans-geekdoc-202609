for the training dataset, the same model has been applied to the test dataset for classification of emails into spam or ham.

Several metrics, including accuracy, recall, F-score, Error rate, and support, are used to calculate each of the four classifiers’ performance. Calculating these measures involves using a confusion matrix. To create a confusion matrix, four terms are used: True Positive, True Negative, False Negative, and False Positive. The inferences of all four algorithms on test data with proposed methodologies are listed in Table 2.1.

# Table 2.1 Inferences of All SVM, MNB, GNB, and BNB Algorithms

| Classification Algorithms | Predicted as Ham | Predicted as Spam |
|---|---|---|
| SVM Actual ham | 975 | 12 |
| Actual spam | 23 | 74 |
| MNB Actual ham | 968 | 19 |
| Actual spam | 30 | 67 |
| GNB Actual ham | 924 | 63 |
| Actual spam | 64 | 33 |
| BNB Actual ham | 919 | 68 |
| Actual spam | 69 | 28 |

Recall is the ratio of genuine positives to all positives, whereas precision is the relationship between true positives and projected positives. The percentage of spam emails that are truly identified as spam among all expected positives is determined by precision. Recall calculates the proportion of spam emails that are truly anticipated to be spam out of all spam emails that are projected to be ham and spam. For our dataset, recall and precision are crucial metrics. However, accuracy isn’t necessarily a good metric for email datasets, particularly if the dataset is skewed. The mean precision and recall value is known as the F1-score. False positive rate, a crucial metric that is determined using FP and TN, is computed.