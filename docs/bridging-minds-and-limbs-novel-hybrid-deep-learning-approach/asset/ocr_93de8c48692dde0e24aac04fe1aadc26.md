# Table 2

Comparison of correctness of each algorithm.

| Subject | CSP + SVM | EEGNet | Kovnet | CNN | CNN-LSTM | Proposed | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | 0.58 | 0.157 | 0.34 | 0.71 | 0.42 | 0.263 | 0.73 | 0.526 |
| 1 | 0.455 | -0.019 | 0.163 | 0.46 | 0.012 | 0.252 | 0.675 0.638 |
| 2 | 0.532 | 0.068 | 0.623 | 0.751 | 0.492 | 0.152 | 0.718 | 0.737 |
| 3 | 0.484 | -0.036 | 0.629 | 0.722 | 0.218 | 0.619 | 0.685 | 0.743 | 0.412 |
| 4 | 0.526 | 0.064 | 0.778 | 0.628 | 0.541 | 0.551 | 0.623 | 0.668 | 0.758 |
| 5 | 0.591 | 0.016 | 0.684 | 0.232 | 0.709 | 0.451 | 0.651 | 0.675 | 0.721 |
| 6 | 0.548 | 0.147 | 0.602 | 0.378 | 0.513 | 0.227 | 0.642 | 0.652 | 0.722 | 0.432 |
| 7 | 0.545 | 0.106 | 0.718 | 0.242 | 0.377 | 0.553 | 0.648 | 0.246 | 0.708 | 0.471 |
| 8 | 0.558 | 0.056 | 0.621 | 0.269 | 0.333 | 0.648 | 0.706 | 0.397 | 0.416 |
| average | 0.538 | 0.095 | 0.627 | 0.261 | 0.305 | 0.296 | 0.638 | 0.741 | 0.436 |

# Table 3

Comparison of sensitivity of each algorithm.

| Subject | CSP + SVM | EEGNet | Kovnet | CNN | CNN-LSTM | |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | 0.622 | 0.668 | 0.691 | 0.573 | 0.674 |
| 1 | 0.622 | 0.601 | 0.559 | 0.667 | 0.689 |
| 2 | 0.553 | 0.669 | 0.603 | 0.653 | - |
| 3 | 0.514 | 0.617 | 0.566 | 0.672 | 0.695 |
| 4 | 0.544 | 0.619 | 0.560 | 0.671 | 0.691 |
| 5 | 0.538 | 0.623 | 0.563 | 0.673 | 0.698 |
| 6 | 0.553 | 0.629 | 0.568 | 0.676 | 0.701 |
| 7 | 0.551 | 0.628 | 0.564 | 0.674 | 0.696 |
| 8 | 0.545 | 0.621 | 0.562 | 0.661 | 0.692 |
| 10 | 0.538 | 0.611 | 0.618 | 0.561 | 0.669 |
| average | 0.549 | 0.614 | 0.623 | 0.569 | 0.675 |

# 3.3. Confusion matrix analysis

Fig. 9 presents the confusion matrix for classification algorithms applied across all subjects. This matrix illustrates the classification performance for left and right mirror imagery tasks, where the diagonal elements represent classified true (true positives), and the off-diagonal elements indicate misclassifications. Among all, the method with highest accuracy identified 71% of left trials and 74% of right trials. In contrast, traditional approaches like CSP + SVM show 56% accuracy for left trials and 53% for right trials, greatly differing in feature extraction. CNN-LSTM achieved 63% accuracy for both movements, while ConvNet significantly improves this performance with 64% and 67% accuracy.
KNN and CNN-LSTM exhibit moderate classification accuracy, with KNN classifying 58% of left trials and 62% of right trials, while CNN-LSTM exhibits 69% and 68% accuracy, respectively.

![](bbox=[0.11, 0.335, 0.89, 0.915])

Fig. 9. The cumulative confusion matrix of subject.