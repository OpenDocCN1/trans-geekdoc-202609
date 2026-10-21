![](bbox=[0.1, 0.12, 0.9, 0.36])

FIGURE 12.2 Important features of dataset.

the training package. The test set, which is used to assess how well the model is presented, involves tests that are not a part of the developing experience. To ensure an impartial assessment, it is essential to use unseen data in order to evaluate the model's quality. First, to create an X variable to store the individual attributes of the dataset. To store only the destination variable (Churn), and also create a variable called y. Next, sklearn. model_selection. train_test_split in the package may be used to create both training and test sets.

The number of observations that are correctly and wrongly categorized using the confusion matrix, also known as the confusion matrices, is used to evaluate the I-GBDT model. The expected classes are in each row of the matrix, and the real classes are in each column. Except for the diagonal, the confusing matrix will contain all zeros in a perfect ranking. Each of the components contributes to the misclassification of the principal oblique address. The perplexing matrix facilitates the examination of patterns of misclassification, keeping in mind the underlying principles.

The confusion matrix has four individual metrics that can be found based on the information: True Positive (TP), True Negative (TN), False Positive (FP) and False Negative (TN).

# 12.4 RESULTS AND DISCUSSION

# 12.4.1 Evaluation Measures

The important measure is precision, which is calculated by dividing the true positives by all that have been predicted to be positive. The precision is the preferable one than recall.

```
precision = TP / (TP + FP)
```

The second metric recall is computed by dividing the real positives by everything that should have been predicted as positive.