![](bbox=[0.25, 0.095, 0.78, 0.46])

FIGURE 3.3 Normalized confusion matrix for decision tree feature selection with random forest classification.

After picking the features, we tackle any uneven class spread by evening out the dataset using SMOTE. This balancing step makes sure the random forest classifier learns from an equal number of each class, which is key to building a trustworthy and fair model.

After this, we use this balanced dataset to train the random forest classifier. We use a normalized confusion matrix to visualize how accurate the model is, which helps us evaluate its performance. This matrix gives us a thorough analysis of how well the classifier does, showing us the number of false positives, false negatives, true positives, and true negatives. By normalizing the confusion matrix, we can compare the model's performance across different classes more easily, which helps us identify where the model shines and where it falls short. Figure 3.3 highlights the normalized confusion matrix for decision tree feature selection with random forest classification.

# 3.11 RESULTS AND DISCUSSION

Examining the different feature selection and classification methods using the SECOM dataset gives us fresh insights into their effectiveness for spotting defects in semiconductor manufacturing. We applied SVC, logistic regression, and decision trees to select features and then used random forest models to classify them. This approach helped us gain a deep understanding of how various techniques affect performance.