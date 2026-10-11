
# Split the dataset into training and testing sets

```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

# Create a Random Forest classifier

```python
random_forest_classifier = RandomForestClassifier(n_estimators=100, random_state=42)
```

# Fit the classifier on the training data

```python
random_forest_classifier.fit(X_train, y_train)
```

# Make predictions on the test data

```python
y_pred = random_forest_classifier.predict(X_test)
```

# Compute various performance measures

```python
accuracy = accuracy_score(y_test, y_pred)
conf_matrix = confusion_matrix(y_test, y_pred)
precision, recall, _, _ = precision_recall_fscore_support(y_test, y_pred, average='weighted')
classification_rep = classification_report(y_test, y_pred)
```

# Print performance measures

```python
print(f'Accuracy: {accuracy:.2f}')
print('\nConfusion Matrix:')
print(conf_matrix)
print('\nPrecision: {:.2f}'.format(precision))
print('Recall: {:.2f}'.format(recall))
print('\nClassification Report:')
print(classification_rep)
```

Refer to [Figure 4.13](#ch04.xhtml#fig4-13) for the output of the code:

![](images/4.13.png)

Figure 4.13: Output of code 4.10

In this code, we calculate various evaluation metrics for a classification model trained on the Iris dataset. You can replace the classifier and dataset with your specific data and model. The code covers accuracy, confusion matrix, precision, recall, and F1-Score.

## Conclusion

In this chapter, we have discussed supervised learning with its second type ‘classification’ in detail. We have thoroughly discussed logistic regression for classification tasks with its sigmoid function. Thereafter, we elaborated on KNN with its diagram and working principles. We shed light on the decision tree with its split algorithm Gini index and ID3. Then random forest, Naïve Bayes and SVM classifiers are described in detail with their respective advantages, working principles and Python codes. At the end of the chapter various evaluation metrics are elucidated with code. In the next chapter, we will explore unsupervised learning techniques.

## Programming exercises

1. Implement a logistic regression model from scratch using Python and NumPy.
2. Use a logistic regression model to classify a binary dataset. Evaluate the accuracy and visualize the decision boundary.
3. Write a function to implement the K-nearest neighbors algorithm.
4. Apply KNN to a dataset and tune the value of `k` for optimal performance.
5. Implement a basic decision tree classifier using Python.
6. Extending the decision tree implementation to handle categorical features.
7. Create a simple random forest classifier using multiple decision trees.
8. Implement the `ID3` algorithm for constructing a decision tree from a dataset.
9. Develop a function to calculate information gain and use it to determine optimal splits in a dataset.
10. Build a naive Bayes classifier for a text classification problem.
11. Extend the naive Bayes implementation to handle continuous features.
12. Implement a basic SVM classifier using a linear kernel.
13. Extend the SVM implementation to use a non-linear kernel (for example, polynomial or radial basis function).

## Questions

1. What is logistic regression, and in what type of Machine Learning problems is it commonly used?
2. Explain the logistic function (sigmoid) and how it is utilized in logistic regression.
3. What is the purpose of the odds ratio in logistic regression?
4. How do you interpret the coefficients in a logistic regression model?
5. Describe scenarios where logistic regression is more suitable than linear regression.
6. What is the K-nearest neighbors algorithm, and how does it make predictions?
7. Explain the impact of choosing the value of `k` in KNN.
8. How does KNN handle categorical features and missing values?
9. Discuss the concept of the curse of dimensionality and its relevance to KNN.
10. What are some advantages and disadvantages of the KNN algorithm?
11. Explain the decision tree algorithm and how it makes decisions based on features.
12. What is information gain, and how is it used in the `ID3` algorithm for decision tree construction?
13. What are the advantages of using an ensemble method like Random Forest over a single decision tree?
14. Discuss the concept of feature importance in the context of decision trees and random forests.
15. How does the random forest algorithm address overfitting?
16. Explain the concept of split algorithms in decision trees.
17. What is `ID3`, and how does it construct decision trees using information gain?
18. Discuss the challenges of using `ID3` with continuous and categorical features.
19. How does pruning contribute to improving decision tree performance?
20. Compare and contrast different split criteria used in decision tree algorithms.
21. What is the assumption of independence in the naive Bayes algorithm?
22. Explain how the naive Bayes classifier works for text classification problems.
23. How does naive Bayes handle continuous and categorical features?
24. Discuss situations where naive Bayes may perform well and where it may struggle.
25. What is Laplace smoothing, and why is it used in naive Bayes?
26. What is the main objective of support vector machines in classification?
27. Explain the concept of a hyperplane in SVM.
28. How does the choice of the kernel function impact the SVM algorithm?
29. What is the significance of the cost parameter in SVM?
30. Discuss scenarios where SVM is particularly useful, and when it might face challenges.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![](images/fm1.png)

# CHAPTER 5 Unsupervised Learning: Clustering

## Introduction

Clustering is a fundamental technique in unsupervised Machine Learning that involves grouping similar data points into clusters or groups based on their intrinsic properties. In clustering, data points within the same cluster are more like each other as compared to the data points in other clusters. Clustering algorithms aim to discover hidden patterns and structures within the data without any prior labels or target values.

## Structure

The chapter covers the following topics:

* Need for clustering
* Applications of clustering
* Partition-based clustering methods
* Hierarchical clustering
* Density-based clustering
* Principal component analysis

## Objectives

At the end of this chapter, you will be able to understand about unsupervised learning using clustering methods. You will learn and implement various types of clustering techniques like k means clustering, hierarchical clustering, and density-based clustering by using Density-Based Spatial Clustering of Applications with Noise (`DBSCAN`) and `OPTICS`, and principal component analysis with their in-depth explanation by using Python code. Thereafter, you will learn and implement various anomaly detection and prevention techniques along with code.

## Need for clustering

Clustering is a crucial part of Machine Learning. Its need is described as follows:

* **Pattern discovery**: Clustering helps to identify natural groupings or patterns within the data. It is especially useful when you do not have prior knowledge of the underlying structure.
* **Data exploration**: Clustering can be used as an exploratory data analysis tool to gain insights into your data. It can reveal relationships and trends that may not be apparent otherwise.
