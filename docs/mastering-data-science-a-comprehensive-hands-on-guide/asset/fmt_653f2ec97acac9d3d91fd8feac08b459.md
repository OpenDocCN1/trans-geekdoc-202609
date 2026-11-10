
C. When the model has high variance

D. When the dataset has missing values

## Question 24
What is the purpose of the test set in machine learning?
A. To fine-tune model parameters
B. To evaluate the model's generalization ability
C. To add more training examples
D. To increase the model's bias

## Question 25
What is the output of one-hot encoding?
A. A single column of numerical values
B. Multiple binary columns representing categorical variables
C. A list of frequency counts for each category
D. A single numerical value assigned to each category

# 15.22 Answers to Chapter Review Questions
1\. B. One that specifies the input, output, and performance measure
Explanation: A well-defined learning problem includes clear specifications of the `inputs`, `outputs`, and a measurable `performance metric` to evaluate the model.
2\. C. Training
Explanation: Training involves using labeled data to tune the parameters of a machine learning model.
3\. B. A possible model or function that explains the data
Explanation: In machine learning, a hypothesis represents a model or function that attempts to explain the patterns in the data.
4\. A. There is no relationship between the variables
Explanation: The `null hypothesis` assumes that there is no relationship or effect between variables being studied.
5\. B. Choosing an appropriate learning algorithm
Explanation: A key issue in designing a learning system is selecting an algorithm that is well-suited to the problem and dataset.
6\. A. Finds the most specific hypothesis consistent with the data
Explanation: The `Find-S` algorithm finds the most specific hypothesis that matches the training examples.
7\. A. Candidate Elimination Algorithm
Explanation: The `Candidate Elimination Algorithm` iteratively eliminates inconsistent hypotheses, narrowing the hypothesis space.
8\. A. The set of assumptions a model makes to generalize from the data
Explanation: `Inductive bias` refers to the assumptions a model uses to generalize from the training data to unseen data.
9\. C. Scikit-learn
Explanation: `Scikit-learn` is a widely used library in Python that provides tools for classification, regression, clustering, and preprocessing.
10\. C. The target outputs for prediction
Explanation: In machine learning, `labels` represent the target variable the model is trained to predict.
11\. B. To ensure all features are on the same scale for better model performance
Explanation: `Feature scaling` ensures that features have comparable ranges, improving the performance of algorithms sensitive to scale, like `gradient descent`.
12\. A. Supervised learning requires labeled data, while unsupervised learning does not
Explanation: The main distinction between `Supervised learning` and `Unsupervised learning` is the use of labeled data.
13\. B. When the model captures noise in the training data instead of the actual pattern
Explanation: `Overfitting` occurs when a model learns the noise and details of the training data, reducing its ability to generalize to new data.
14\. B. One-Hot Encoding
Explanation: `One-Hot Encoding` converts categorical variables into binary variables, creating a separate binary column for each category.
15\. B. The training set is used to train the model, and the test set evaluates the model's performance on unseen data
Explanation: The `training set` is for learning, and the `test set` evaluates how well the model generalizes to new, unseen data.
16\. C. To provide machine learning tools like classification, regression, and clustering
Explanation: `Scikit-learn` offers a range of tools for implementing and evaluating machine learning algorithms.
17\. B. The target variable the model predicts
Explanation: The dependent variable (target) is the variable that the machine learning model is trained to predict.
18\. B. To predict the output based on labeled input data
Explanation: `Supervised learning` aims to learn a mapping from input features to labeled outputs for prediction tasks.
19\. D. Using regularization techniques
Explanation: `regularization` helps prevent `Overfitting` by adding a penalty to the model for complexity, encouraging simpler models.
20\. B. Nominal data has no inherent order, while ordinal data does
Explanation: `Ordinal data` has a meaningful order (e.g., rankings), whereas `Nominal data` has no inherent ordering (e.g., colors).
21\. B. Learns patterns in data to make predictions or decisions
Explanation: A machine learning model learns from data to identify patterns and make predictions or decisions.
22\. C. K-means Clustering
Explanation: `K-means Clustering` is an `Unsupervised learning` algorithm that groups data points into clusters without predefined labels.
23\. B. When the model is too simple to capture the underlying data pattern
Explanation: `Underfitting` occurs when a model is too simplistic to learn the structure of the data, leading to poor performance on both training and test sets.
24\. B. To evaluate the model's generalization ability
Explanation: The `test set` is used to assess how well the model generalizes to new, unseen data.
25\. B. Multiple binary columns representing categorical variables
Explanation: `One-Hot Encoding` creates multiple binary columns for each category in a categorical variable, representing its presence or absence.

# Chapter 16. Data Pre-processing In Machine Learning
Data pre-processing is a crucial step in Machine Learning that ensures datasets are clean, structured, and ready for model training. This chapter covers the importance of data pre-processing, outlining key steps such as handling missing data, encoding categorical variables, and scaling features. A practical step-by-step example demonstrates how to import libraries, load datasets, apply `fit` and `transform` methods in `sklearn`, split data into training and test sets, create dummy variables, and perform feature scaling. By the end of this chapter, readers will understand how to effectively prepare data, improving the accuracy and efficiency of Machine Learning models.

## 16.1 Data Pre-processing
Data preprocessing is a crucial step in the machine learning pipeline. It involves transforming raw data into a clean and usable format, which enhances the quality of input data for machine learning models. Effective preprocessing ensures that the model can learn meaningful patterns and avoid biases or errors. Let's dive into the key steps and techniques:

### Understanding the Dataset
The process of understanding the dataset begins with problem analysis, where it is essential to grasp the nature of the problem and the type of data you are working with, whether it is structured, unstructured, or semi-structured. This foundational understanding helps shape the approach to data handling and modeling. Following this, exploratory data analysis (`EDA`) involves using descriptive statistics and visualization tools to uncover patterns, detect outliers, and identify anomalies in the dataset. This step provides critical insights that guide subsequent preprocessing and model-building decisions.

### Data Cleaning
Data cleaning is a critical step in preprocessing that addresses inconsistencies or errors in the dataset to ensure its quality. This process involves handling missing values through techniques like imputation, where missing data is replaced with statistical measures such as the `mean`, `median`, or `mode`, or by removing rows or columns with excessive missing entries. Managing outliers is also essential, and this can be done using statistical methods such as `z-scores` or interquartile range (`IQR`) to either cap or remove these extreme values. Removing duplicates is another important task, as redundant data can introduce bias into the model. Additionally, errors such as typos, inconsistent formats, or incorrect entries need to be corrected to ensure the data is accurate and reliable for analysis and modeling.

### Data Transformation
