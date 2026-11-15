typically using metrics such as Mean Decrease Gini (MDG) or Mean Decrease Accuracy (MDA) [35,36]. This method effectively selects important features while retaining the benefits of the Random Forest's robustness against overfitting.

# 3.3.3. Least Absolute Shrinkage and Selection Operator (LASSO)

LASSO is a regression analysis technique that combines both variable selection and regularization to improve the prediction accuracy and interpretability of a statistical model. It works by minimizing a specific objective function, which includes a regularization term. In LASSO regression, L1 regularization is applied, which adds a penalty to the model based on the absolute values of the coefficients. This regularization encourages sparsity in the model by pushing the coefficients of less important features towards zero. As the regularization parameter increases, more coefficients are driven towards zero, effectively removing less relevant predictors from the model. The result is a simpler and more interpretable model that tends to generalize better when applied to unseen data. This makes LASSO a powerful tool for feature selection and model simplification [37].

# 3.3.4. K-Best Feature Selection

K-Best is a filter-based feature selection method that assesses the relevance of each feature with respect to the target variable. The process starts by evaluating all features in the dataset using statistical tests like the Chi-squared test, ANOVA F-value, or mutual information. The goal is to identify the top k features that provide the most useful information for predicting the target variable. The selection process can be outlined as follows:

+   1. For each feature, compute a score using a chosen statistical measure.
+   2. Sort the features based on their scores in descending order.
+   3. Select the top k features with the highest scores.

K-Best feature selection helps reduce the dimensionality of the dataset by removing less informative features. This results in improved model performance while retaining the most relevant features for predictive modeling [28].

# 3.4. Overview of Machine Learning Techniques

This section presents the list of ML techniques we have utilized in this study including Logistic Regression (LR), Random Forest (RF), Support Vector Machine (SVM), Extreme Gradient Boosting (XGB), and Ada Boost (ADB).

# 3.4.1. Logistic Regression

Logistic regression is a statistical method used for binary classification, where it models the relationship between a dependent binary variable and one or more independent variables. The method estimates probabilities using the logistic function [38]. In this model, the probability that the target variable is equal to 1, given the features, is calculated. The coefficients for each feature are estimated by maximizing the likelihood function, which measures how well the model fits the observed outcomes [39]. Logistic Regression can be used to classify miRNA expression data by estimating the probability that a given miRNA profile corresponds to a specific disease class. Its simplicity and ability to handle binary outcomes make it a valuable tool for predicting the presence of disease based on miRNA expression levels.

# 3.4.2. Random Forest

Random Forest is an ensemble learning method used for classification. It builds multiple decision trees from bootstrapped samples of the dataset and averages their predictions [40]. For a given dataset, a Random Forest creates multiple decision trees, each using