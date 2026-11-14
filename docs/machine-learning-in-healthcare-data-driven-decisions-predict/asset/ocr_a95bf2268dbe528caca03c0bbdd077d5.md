The Insulin feature contains 186 unique values between 0 and 846. Although a mean value of 80 was specified for imputation, there were no missing values. The BMI feature has 248 unique values, with a range of 0.0–67.1. A mean value of 32 was used to handle seven missing entries. The DiabetesPedigreeFunction feature shows 517 unique values ranging from 0.078 to 2.42. The Age feature comprises 52 unique values, ranging from 21 to 81. A mean value of 33 was used to impute 21 missing values. Finally, the outcome feature is a binary target variable.

# ## 4.1 Experimental Setup

The mean imputation is carried out to resolve missing values, and the data is split into 70–30%, where 70% belongs to the training set and 30% belongs to the testing set. To measure the performance, there are four metrics used, which are accuracy, precision, recall, and F1 score.

Accuracy tells the proportion of total predictions that were correct, and precision tells how many positive predictions are correct, recall talks about how many positives are correctly predicted, and finally, the F1 score is the harmonic mean of precision and recall. The formula for calculating the metrics is given below:

```
Accuracy = TP + TN/TP + TN + FP + FN (1)
Precision = TP/TP + FP (2)
Recall = TP/TP + FN (3)
F1 = 2 × Precision × Recall/Precision + Recall (4)
```

# ## 4.2 Analysis on Base Models

The five classifiers are initially used to classify diabetes, and the results are LR achieved an accuracy of 76.62%, with a precision of 65.62%, a recall of 61.76%, and an F1 score of 63.64%. DT recorded an accuracy of 72.08%, a precision of 56.56%, a recall of 67.65%, and an F1 score of 61.61%. SVM reached an accuracy of 76.30%, a precision of 66.29%, a recall of 57.84%, and an F1 score of 61.78%. RF matched the highest accuracy at 76.62%, with a precision of 65.00%, a recall of 63.73%, and an F1 score of 64.36%. kNNs attained an accuracy of 75.00%, a precision of 63.16%, a recall of 58.82%, and an F1 score of 60.91%. Figure 1 shows the performance of all the models in terms of accuracy, precision, recall, and F1 score. The SHAP values of DT, SVM, LR, RF, and kNN are shown in Figures 2–5 and 6, respectively.

It is noted that RF gives better performance than others because the feature relationship is captured in both linear and nonlinear manner. The RF reduces overfitting and is less sensitive to noise and outliers.