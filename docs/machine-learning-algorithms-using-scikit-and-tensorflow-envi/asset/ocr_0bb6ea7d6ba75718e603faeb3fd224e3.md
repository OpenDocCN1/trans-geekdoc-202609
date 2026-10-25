# 2. Label Assignment Results

Initially raw dataset contains nearly fifty-one thousand data, after assigning class labels nearly ten thousand data is labeled as depressed, thirty-six thousand data is labeled as non-depressed and five thousand data is labeled as neutral. Figure 2 presents the count of each class after assigning class labels for the unstructured dataset.

Figure 2. Histogram of labels assignment

![](bbox=[0.263, 0.296, 0.763, 0.55])

# 3. Classification Results

These results show the confusion matrix of each classifier and compare the predicted and actual values of each classifier. In this matrix, Diagonal elements represent the True Positive values, the sum of corresponding column excluding TP value is called False Positive, the sum of corresponding row exclude the TP value is called False Negative and rest diagonal elements are considered as True Negative.

+   - The confusion matrix of multinomial Naive Bayes classifier is indicated in Table 2.
+   - The confusion matrix of SVM Classifier is indicated in Table 3.
+   - The confusion matrix of ANN classifier is indicated in Table 4.
+   - Figure 3 presents the Precision, Recall and F1 score of classifiers like NB, SVM, ANN these values are obtained from the confusion matrix of corresponding classifiers.
+   - The accuracy obtained by each classifier algorithm is indicated in Table 5.