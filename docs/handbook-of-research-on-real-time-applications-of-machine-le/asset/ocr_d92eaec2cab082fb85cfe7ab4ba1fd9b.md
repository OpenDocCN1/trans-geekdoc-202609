The trained values from implementing the CNN architecture is validated under various performance analysis measure. The CNN model helps in achieving ROC of 91.85% and average precision of 83.16% for a specificity of 90%. The various study of seizure detection in the literature available exert various datasets and also provide enormous number of evaluation measures. The performance measure for three classifiers is discussed in the given table which helps in detecting the epileptic activity in the brain.

# Table 1. Performance metrics for trained dataset

| Type of Classifier | Accuracy | Precision | Recall | F1Score | Specificity |
|---|---|---|---|---|---|
| Random Forest | 100.000% | 1.000 | 1.000 | 1.000 | 1.000 |
| Gradient Boosting | 99.111% | 0.993 | 0.989 | 0.991 | 0.993 |
| Decision tree | 97.793% | 0.998 | 0.958 | 0.977 | 0.998 |

# Table 2. Performance metrics for validation dataset

| Type of Classifier | Accuracy | Precision | Recall | F1Score | Specificity |
|---|---|---|---|---|---|
| Random Forest | 100.000% | 1.000 | 1.000 | 1.000 | 1.000 |
| Gradient Boosting | 100.000% | 1.000 | 1.000 | 1.000 | 1.000 |
| Decision tree | 99.072% | 0.997 | 0.955 | 0.975 | 0.999 |

# CONCLUSION

In this proposed study, a preliminary result has been automated for EEG seizure detection. It helps in classifying the best algorithm for epileptic seizure detection. The accuracy value obtained for the classifier chosen in extracting the time frequency and wavelet features from the EEG data values helps in analyzing the performance. When comparing the gradient boosting and decision tree random forest classifier have good performance metrics for trained dataset. CNN over comes the problem of choosing the local minimum value by involving different layers without setting the number of features to be small. In future, for artifact rejection that has been imposed in pre-processing, various algorithms can be imposed and incorporated to remove the false detection. It could be also implied in medical tasks using same data structure values, particular in sensing the health where the awareness is still identified as a major issue.