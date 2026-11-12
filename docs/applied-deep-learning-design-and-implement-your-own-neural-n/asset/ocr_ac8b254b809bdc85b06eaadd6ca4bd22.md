not identified correctly, and the recall is the number of true positive results divided by the number of all samples that should have been identified as positive.

Example 7: Suppose we have infinite data elements of Class 1 and a single element of Class 2, and the machine learning model predicts Class 1 for all the instances of the test data. Table 2.10 represents the confusion matrix with predicted and actual values.

| N=150 | Predicted--"No" | Predicted--"Yes" |
|---|---|---|
| Actual--"No" | 50 | 10 |
| Actual--"Yes" | 5 | 85 |

Table 2.10: Confusion matrix

Rewriting table 2.10 in confusion matrix form in table 2.11:

| N=150 | Predicted--"No" | Predicted--"Yes" | Total |
|---|---|---|---|
| Actual--"No" | TN = 50 | FP = 10 | 60 |
| Actual--"Yes" | FN = 5 | TP = 85 | 90 |
| Total | 55 | 95 | |

Table 2.11: Revised confusion matrix

+   Accuracy:

A = \frac{TN + TP}{TN + TP + FN + FP}
= \frac{50 + 85}{50 + 85 + 5 + 10}
\Rightarrow \frac{135}{150} = 0.9

+   Precision:

P = \frac{TP}{TP + FP}
\Rightarrow \frac{85}{85 + 10} \Rightarrow \frac{85}{95} = 0.8947