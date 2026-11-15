
![](img/46da2aabc253ed283db238584dfa3d21_145_0.png)

Figure 1. Overview of the methodology.

## 3.2. Feature Selection

Feature selection, also known as feature reduction or variable subset selection, is the process of identifying a minimal subset of the most relevant features from a larger set of features in a dataset [12,24]. When working with high-dimensional data, such as miRNA data, it becomes essential to select a small, optimal subset that captures the critical information of the entire dataset without significant loss of detail. This process is fundamental in building robust learning models. The importance of feature selection has been widely studied in fields like bioinformatics and pattern recognition [25,26]. In general, feature selection techniques are designed to minimize overfitting and enhance model performance, leading to improved predictive accuracy in supervised classification and better cluster detection in clustering tasks. Furthermore, they contribute to the creation of faster and more cost-efficient models while also providing valuable insights into the underlying processes that produced the data [16,27].

In the realm of classification, feature selection methods can be classified into three categories based on their selection strategy of the features: filter methods, wrapper methods, and embedded methods. Filter methods select the relevance of features based on certain properties such as statistical significance. Features are selected before choosing any machine learning model. These techniques are computationally efficient and help eliminate irrelevant features, allowing for a simplified model without risking overfitting [28]. Wrapper methods involve using a specific machine learning algorithm to evaluate the performance of different feature subsets by training the model repeatedly. This approach often yields better feature selection tailored to the model, but it can be computationally expensive [29]. Embedded methods integrate feature selection within the model training process, allowing for simultaneous feature selection and model optimization. This approach typically results in models that are both efficient and accurate, as they consider feature interactions during the selection process [30].

When working with miRNA expression profile datasets, selecting the most relevant features (miRNAs) is essential for constructing accurate and interpretable models [12]. Due to the high dimensionality of miRNA datasets and the typically small sample sizes, effective feature selection methods can greatly enhance model performance and mitigate the risk of overfitting [24]. Research has shown that ensemble feature selection methods combined with cross-validation techniques can effectively identify an optimal minimal subset of features. This approach enhances model performance and ensures robust validation on unseen data while reducing the risk of overfitting, outperforming single-feature selection techniques [15]. In this study, we propose an ensemble feature selection approach combined with nested cross-validation to identify the minimal miRNA feature set for classification.

## 3.3. Ensemble Feature Selection Algorithms

Ensemble feature selection identifies an optimal feature set by combining results from multiple individual feature selection algorithms [31]. This approach differs from single-feature selection strategies, which identify key features using a singular method. For example, single methods might filter out low-variance features or recursively eliminate those that do not contribute to model performance. In contrast, ensemble selection integrates optimal feature sets from various techniques to find the best overall feature set. Previous studies shows that ensemble learning results in more robust classification outcomes and produces a superior optimal feature set compared to single-feature selection approaches [12,15–17,20–22]. In this study, we selected four distinct feature selection methods, each representing a different category of techniques, to ensure a comprehensive approach to feature selection. Recursive Feature Elimination (RFE), taken from wrapper methods, Random Forest feature importance (RF), an embedded method, the k-best method (k-best), a filter technique, and Least Absolute Shrinkage and Selection Operator (LASSO) to introduce regularization by penalizing certain coefficients.

### 3.3.1. Recursive Feature Elimination

Recursive Feature Elimination (RFE) is a wrapper-based feature selection method that iteratively selects the most important features by recursively removing the least important ones [32]. The principle of RFE involves training a model using all available features, evaluating their importance scores, and then recursively eliminating the least important features until the desired number of features is reached [33]. The goal of RFE is to identify an optimal subset of features from the complete list of features in the dataset. Initially, a supervised learning model is trained using the full feature set to predict the target values. Afterward, the importance of each feature is evaluated based on the model’s learned parameters, with less important features identified by their scores. The feature with the lowest importance score is then eliminated from the dataset. This process continues iteratively, with the model being retrained after each removal, until the desired number of features is selected.

### 3.3.2. Random Forest Feature Importance

Random Forest (RF) feature importance belong to embedded feature selection family that evaluates the significance of each feature based on its contribution to the prediction in a Random Forest model [34]. The primary goal of RF feature importance is to identify and rank features based on their predictive power, allowing for the selection of the most influential features. A Random Forest model is trained by constructing multiple decision trees using bootstrap samples from the dataset. During the training process, the importance of each feature is evaluated based on its contribution to the model’s predictive accuracy, typically using metrics such as Mean Decrease Gini (MDG) or Mean Decrease Accuracy (MDA) [35,36]. This method effectively selects important features while retaining the benefits of the Random Forest's robustness against overfitting.

### 3.3.3. Least Absolute Shrinkage and Selection Operator (LASSO)

LASSO is a regression analysis technique that combines both variable selection and regularization to improve the prediction accuracy and interpretability of a statistical model. It works by minimizing a specific objective function, which includes a regularization term. In LASSO regression, L1 regularization is applied, which adds a penalty to the model based on the absolute values of the coefficients. This regularization encourages sparsity in the model by pushing the coefficients of less important features towards zero. As the regularization parameter increases, more coefficients are driven towards zero, effectively removing less relevant predictors from the model. The result is a simpler and more interpretable model that tends to generalize better when applied to unseen data. This makes LASSO a powerful tool for feature selection and model simplification [37].

### 3.3.4. K-Best Feature Selection

K-Best is a filter-based feature selection method that assesses the relevance of each feature with respect to the target variable. The process starts by evaluating all features in the dataset using statistical tests like the Chi-squared test, ANOVA F-value, or mutual information. The goal is to identify the top k features that provide the most useful information for predicting the target variable. The selection process can be outlined as follows:

- 1. For each feature, compute a score using a chosen statistical measure.
- 2. Sort the features based on their scores in descending order.
- 3. Select the top k features with the highest scores.

K-Best feature selection helps reduce the dimensionality of the dataset by removing less informative features. This results in improved model performance while retaining the most relevant features for predictive modeling [28].

## 3.4. Overview of Machine Learning Techniques

This section presents the list of ML techniques we have utilized in this study including Logistic Regression (LR), Random Forest (RF), Support Vector Machine (SVM), Extreme Gradient Boosting (XGB), and Ada Boost (ADB).

### 3.4.1. Logistic Regression

Logistic regression is a statistical method used for binary classification, where it models the relationship between a dependent binary variable and one or more independent variables. The method estimates probabilities using the logistic function [38]. In this model, the probability that the target variable is equal to 1, given the features, is calculated. The coefficients for each feature are estimated by maximizing the likelihood function, which measures how well the model fits the observed outcomes [39]. Logistic Regression can be used to classify miRNA expression data by estimating the probability that a given miRNA profile corresponds to a specific disease class. Its simplicity and ability to handle binary outcomes make it a valuable tool for predicting the presence of disease based on miRNA expression levels.

### 3.4.2. Random Forest

Random Forest is an ensemble learning method used for classification. It builds multiple decision trees from bootstrapped samples of the dataset and averages their predictions [40]. For a given dataset, a Random Forest creates multiple decision trees, each using
