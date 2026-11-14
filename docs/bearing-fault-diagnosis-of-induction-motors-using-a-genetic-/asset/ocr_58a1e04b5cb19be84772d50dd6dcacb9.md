classification algorithms. Specifically, 9520 data instances are utilized for training the machine learning algorithms, whereas the remaining previously unseen by the trained classifiers 4080 samples are applied for validating the final fault classification performance. To ensure consistency in the results, the training was repeated several times and almost the same test accuracy was achieved for each iteration. The schematic diagram of the proposed method is given in Figure 8.

![](bbox=[0.2, 0.18, 0.8, 0.61])

# Figure 8. Schematic diagram of the proposed methodology.

# 2.9. Model Evaluation

The feature set selected using GA is used as the input for the three different classifier algorithms discussed in the previous section. Of the different evaluation parameters, the confusion matrix, overall accuracy, sensitivity, specificity, prediction, and the F1-score are considered as the performance metrics in this work. The evaluation parameters are calculated by the equations provided in Table 4.

# Table 4. Performance evaluation parameters.

| Precision = \(\frac{TP}{TP + FP}\) | (18) | Sensitivity = \(\frac{TP}{TP + FN}\) | (19) |
| :--- | :--- | :--- | :--- |
| Specificity = \(\frac{TN}{FP + TN}\) | (20) | F1 = 2 x \(\frac{\text{Precision} \times \text{Sensitivity}}{\text{Precision} + \text{Sensitivity}}\) | (21) |
| Accuracy = \(\frac{TP + TN}{TP + FP + TN + FN}\) | (22) | | |