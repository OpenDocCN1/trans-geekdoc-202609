
## Predict clusters

```
clusters = kmeans.predict(X)

print(clusters)  # Output: Cluster labels (e.g., [0, 0, 0, 1, 1])
```

### 15.18.3 Key Differences

| Aspect | Supervised Learning | Unsupervised Learning |
| --- | --- | --- |
| Data | Labeled (input and output are paired) | Unlabeled (only input data) |
| Goal | Predict outcomes for new data | Find patterns or structures in data |
| Examples | Classification, Regression | Clustering, Dimensionality Reduction |
| Algorithms | Linear Regression, Random Forest, Neural Networks | K-Means, DBSCAN, PCA |
| Use Case | Predictive modeling (e.g., spam detection) | Exploratory analysis (e.g., customer grouping) |

***

In a nutshell, supervised learning is especially beneficial when labeled datasets are available and the task is one of making predictions. Unsupervised learning is suitable for exploring hidden structures in unlabeled data. Both are fundamental approaches in the practice of data science, depending on the nature of the problem and whether or not labeled data is available.

# 15.19 Understanding Overfitting and Underfitting

Overfitting and underfitting are common challenges in machine learning that affect a model's ability to generalize well to new, unseen data. Striking a balance between these two issues is crucial for building effective and accurate models.

## 15.19.1 Overfitting

Overfitting happens when a model learns the noise and irrelevant details of the training data too well, leading to poor generalization on new, unseen data despite performing excellently on the training set. Essentially, overfitting is characterized by high accuracy on the training data but poor performance on validation or test data.

This issue is often the result of a model being overly complex, with too many features or parameters. Overfitting is particularly likely when the training data is insufficient relative to the model's complexity, or when overly complex algorithms are used without regularization techniques to prevent overfitting.

An example of overfitting is seen in decision tree models that have too many splits. While such a model may perfectly classify the training dataset, it struggles to make accurate predictions on new data, as it becomes overly sensitive to small variations in the training set.

To prevent overfitting, various strategies can be employed. Regularization techniques like L1 (Lasso) and L2 (Ridge) penalize models for being too complex, helping to improve generalization. Pruning, or reducing the depth of decision trees, simplifies the model, further aiding in its ability to generalize. Increasing the size of the training dataset allows the model to capture a broader range of representative data patterns, while cross-validation helps ensure that the model performs well across different subsets of data.

## 15.19.2 Underfitting

Underfitting occurs when a model lacks sufficient complexity to capture the underlying patterns in the data. As a result, the model fails to learn effectively from the training data, leading to poor performance on both the training and validation datasets. This is characterized by low accuracy across both sets and high bias, indicating that the model struggles to capture complex relationships.

Common causes of underfitting include using overly simplistic models for complex problems, such as applying linear regression to a non-linear dataset. It can also arise from insufficient training time or epochs, a lack of relevant features, or improper data preprocessing. These issues need to be addressed in order to improve the model's performance and ability to generalize.

For example, applying linear regression to a non-linear dataset may result in the model failing to capture the underlying curve in the data, leading to underfitting and poor predictive performance.

To resolve underfitting, one can employ more complex models or algorithms, such as polynomial regression or decision trees, which are better suited to capturing the data's structure. Additionally, improving feature selection, enhancing data preprocessing, and increasing training duration or dataset size can help the model learn more effectively and reduce underfitting.

## 15.19.3 Balancing Overfitting and Underfitting

To achieve a good balance between overfitting and underfitting, it is essential to build models that can generalize well. This involves finding the optimal model complexity and ensuring it learns just enough from the data without being overly specific or overly simplistic.

### Techniques to Balance

Regularization: Penalize overly complex models using techniques like L1 or L2 regularization.

Cross-Validation: Use k-fold cross-validation to ensure the model performs consistently on different subsets of the data.

Early Stopping: Stop training once the validation error starts increasing to prevent overfitting.

Model Selection: Choose a model with the right complexity for the problem (e.g., decision trees vs. random forests).

Data Augmentation: Increase the size of the training data by generating new samples or transforming existing ones.

Feature Engineering: Select relevant features and remove noisy or redundant ones.

## 15.19.4 Visualizing Overfitting and Underfitting

Learning curves are a useful tool for diagnosing whether a model is underfitting or overfitting. These curves plot the training and validation errors as a function of the number of examples or epochs, helping to visualize the model's learning progress. When underfitting occurs, both the training and validation errors remain high, indicating that the model is too simplistic to capture the underlying patterns in the data.

On the other hand, overfitting is characterized by low training error and high validation error. This suggests that the model has learned the training data too well, including its noise and irrelevant details, which hampers its ability to generalize to new data. Observing these patterns in learning curves helps guide adjustments to the model to improve its generalization performance.

Example with Python:

```
from sklearn.model_selection import learning_curve
import matplotlib.pyplot as plt

# Function to plot learning curve
def plot_learning_curve(estimator, X, y):
    train_sizes, train_scores, test_scores = learning_curve(estimator, X, y, cv=5)
    train_mean = train_scores.mean(axis=1)
    test_mean = test_scores.mean(axis=1)
    plt.plot(train_sizes, train_mean, label="Training Error")
    plt.plot(train_sizes, test_mean, label="Validation Error")
    plt.xlabel("Training Set Size")
    plt.ylabel("Score")
    plt.title("Learning Curve")
    plt.legend()
    plt.show()

# Example: Use this function with any estimator (e.g., LinearRegression())
```

### Summary

| Aspect | Overfitting | Underfitting |
| --- | --- | --- |
| Definition | Model fits training data too well. | Model fails to learn from training data. |
| Cause | Model too complex or too many features. | Model too simple or insufficient training. |
| Performance | High training accuracy, low test accuracy. | Low accuracy on both training and test data. |
| Solution | Regularization, pruning, cross-validation. | Use complex models, add features, train longer. |

It is the foundation of any robust machine learning model: striking a balance between overfitting and underfitting. You can ensure that your model generalizes well to new data by carefully tuning model complexity using techniques such as regularization, cross-validation, and feature engineering.

# 15.20 Hands-On: Your First Machine Learning Model with scikit-learn

Building your first machine learning model with scikit-learn, a powerful Python library, involves a few key steps. Let's walk through the process using a simple supervised learning example to predict housing prices based on features like area and number of bedrooms.

## 1. Importing Necessary Libraries

Start by importing essential libraries:

```
import numpy as np
```
