# Table 12.6 Confusion matrices for RNN and LNN (test size = 35).

| | RNN (\(\lambda = 0\)) | True-0 | True-1 |
|---|---|---|---|
| Predict-0 | | 12 | 2 |
| Predict-1 | | 4 | 17 |
| | LNN (\(\lambda = 0\)) | True-0 | True-1 |
|---|---|---|---|
| Predict-0 | | 10 | 2 |
| Predict-1 | | 6 | 17 |

# Table 12.7 Accuracy metrics for RNN vs. LNN (test size = 35).

| | Train accuracy | Test accuracy | Recall | Precision | \(F_1\) score | Iterations |
|---|---|---|---|---|---|---|
| RNN | 100% | 82% | 0.89 | 0.81 | 0.85 | 18000 |
| LNN | 99% | 77% | 0.89 | 0.73 | 0.80 | 8000 |

![](bbox=[0.11, 0.505, 0.835, 0.68])

Figure 12.16 ROC plots for LLN and RNN (test size = 35).

obtained for \(\lambda = 2.0\) and this case delivers a test accuracy of 82.0% along with the highest \(F_1\) score of 0.85. This implies that 82% of the test images were correctly identified. However, increasing the value of \(\lambda\) further does not improve the test accuracy and, in fact, it begins to degrade at very high values.

A rather interesting result is obtained for RNN as shown in Table 12.9. As \(\lambda\) is increased from 0.0 to 1.0, the train accuracy remains at 100%, while the test accuracy and the \(F_1\) score decreases. The optimal result is obtained for \(\lambda = 0.0\) and this case delivers a test accuracy of 82.0% along with the highest \(F_1\) score of 0.85. Therefore, it appears that ridge regression on RNN is not effective in the