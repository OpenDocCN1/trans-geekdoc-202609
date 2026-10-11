
In this chapter, we have discussed data pre-processing in detail. Datasets and their types and formats are explained in depth. Various sources to obtain datasets and the need for data pre-processing are discussed. All the steps of pre-processing such as data cleaning, data transformation, data integration and aggregation, data splitting, handling imbalanced data, normalization, and scaling, and text processing (NLP) are elaborated with their respective codes and output.

## Programming exercises

1.  Create a Python function that takes a `DataFrame` as input and returns a new `DataFrame` with missing values filled using an appropriate strategy (mean, median, forward fill, or backward fill).

2.  Write a script to identify and remove duplicate rows from a given `DataFrame` while preserving the first occurrence.

3.  Develop a function that takes a `DataFrame` and a column containing categorical data, and returns the `DataFrame` with the categorical data encoded using one-hot encoding.

4.  Write a script to normalize a numerical column in a `DataFrame` using Min-Max scaling, and then standardize another numerical column using z-score normalization.

5.  Create a function that takes a `DataFrame` and generates a new feature by combining or transforming existing features (for example, calculating ratios or creating interaction terms).

6.  Develop a script to identify and remove outliers from a numeric column using the Inter Quartile Range (IQR) method.

7.  Write a function to preprocess a text column in a `DataFrame` by removing stop words, converting text to lowercase, and removing punctuation.

8.  Create a script that takes a `DataFrame` with a column of date strings and converts it to a `datetime` object. Then, extract the day of the week and add it as a new column.

9.  Implement a function that takes a `DataFrame` with imbalanced classes and applies the Synthetic Minority Over-sampling Technique (SMOTE) to balance the class distribution.

10.  Write a script to perform data binning on a numeric column in a `DataFrame`, dividing it into custom bins and adding a new column with bin labels.

## Questions

1.  How do you identify and handle missing data in a dataset?

2.  What are some common strategies for imputing missing values, and when would you choose one over another?

3.  Explain the importance of removing duplicate rows from a dataset.

4.  How would you identify and eliminate duplicates in a `DataFrame` using Python?

5.  What is the significance of encoding categorical data in Machine Learning?

6.  Compare and contrast label encoding and one-hot encoding. When would you use each?

7.  Why is it essential to scale or normalize numerical features?

8.  Describe the difference between Min-Max scaling and standardization (z-score normalization).

9.  What is feature engineering, and why is it important in the context of Machine Learning?

10.  Provide examples of feature engineering techniques you might apply to a dataset.

11.  Why are outliers problematic in statistical analysis and Machine Learning models?

12.  Describe a method for detecting and handling outliers in a numerical dataset.

13.  What are some common pre-processing steps for cleaning text data?

14.  How would you remove stop words from a text column in a `DataFrame` using Python?

15.  Explain the importance of parsing date and time information in a dataset.

16.  How would you convert a column of date strings to a `datetime` object in Python?

17.  What is data binning, and when might you use it in data pre-processing?

18.  Describe the process of implementing data binning in a numerical column using Python.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![fm1](images/fm1.png)

# CHAPTER 3 Supervised Learning: Regression

## Introduction

Supervised learning, a widely recognized form of Machine Learning, involves utilizing a labelled dataset to instruct an algorithm on mapping input data to a desired target output.

In supervised learning, the algorithm is supervised because it is trained on a dataset where both the input and the desired output are provided, allowing the algorithm to learn and make predictions or decisions without human intervention. The goal of supervised learning is to learn a mapping function from input to output so that the algorithm can generalize and provide predictions for newly generated data.

Applications of supervised learning are widespread and encompass areas such as Natural Language Processing (NLP), Computer Vision (CV), medical diagnosis, recommendation systems, fraud detection, and more. It is one of the foundational paradigms of Machine Learning and forms the basis for many real-world applications where decision-making and prediction are required.

## Structure

The chapter covers the following topics:

*   Key characteristics of supervised learning
*   Regression
*   Need for regression
*   Simple linear regression
*   Multiple linear regression
*   Polynomial Regression
*   Ridge regression
*   Lasso regression

## Objectives

By the end of this chapter, you will be able to understand supervised learning and its most significant type of regression. You will implement various types of regression techniques. You will also learn simple linear regression, multiple linear regression, polynomial regression, ridge regression, and lasso regression comprehensively, detailing their objective functions and including Python code examples. Thereafter, you will learn and implement various performance metrics to evaluate models.

## Key characteristics of supervised learning

Supervised learning exhibits various characteristics which are given as follows:

In supervised learning, the training data consists of labelled examples. Each example includes an input (features) and a corresponding output (target or label). The algorithm utilizes this labelled data to understand the correlation between inputs and outputs.

*   **Prediction**: After training on the labelled data, the algorithm can make predictions or decisions on new, unseen data based on the learned patterns and relationships it has identified during training.
*   **Objective**: The objective of supervised learning can vary, depending on the problem. It could entail regression tasks, aimed at forecasting continuous values (such as predicting house prices), or classification tasks, focused on categorizing data into predetermined classes or labels (like email spam detection or image classification).
*   **Evaluation**: Supervised learning models are evaluated based on their ability to correctly predict or classify new data. Key evaluation metrics commonly used include accuracy, mean squared error, precision, recall, and F1 score, among various others.

Supervised learning commonly employs algorithms such as linear regression, logistic regression, support vector machines, decision trees, random forests, neural networks, and more. Each algorithm is designed to address specific types of problems. This chapter will provide an in-depth discussion of regression.

## Regression

Regression is a statistical and Machine-Learning technique called regression, it is used to predict the connection between one or more independent variables and a dependent variable. Its goal is to use the values of the independent variables to predict or estimate the value of the dependent variable. Regression essentially enables us to comprehend the relationship between changes in the independent and dependent variables.

The key components of regression are mentioned below:
