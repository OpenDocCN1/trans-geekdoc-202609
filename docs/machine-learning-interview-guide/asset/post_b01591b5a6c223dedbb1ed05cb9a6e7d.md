
## Join our book’s Discord space

Join the book’s Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

https://discord.bpbonline.com

![](img/8df331ebfe0697d3dcbca8b91e1e54bf_19_0.png)

## Table of Contents

### 1. **Data Processing for Machine Learning**
- Introduction
- Structure
- Objectives
- Supervised learning
- Clustering and dimensionality reduction
- Time series analysis
- Natural language processing
- Conclusion

### 2. **Classification**
- Introduction
- Structure
- Objectives
- Logistic regression
- K-nearest neighbors
- Decision tree
- Random forest
- Support vector machine
- Model evaluation
- Conclusion

### 3. **Regression**
- Introduction
- Structure
- Objectives
- Linear regression
- Gradient-boosted trees
- Adaptive boosted trees
- Support vector regressor
- Model evaluation
- Conclusion

## 4. Clustering and Dimensionality Reduction
- Introduction
- Structure
- Objectives
- K-means
- Gaussian mixture model
- Principal component analysis
- T-distributed Stochastic Neighbor Embedding
- Density-based spatial clustering of applications with noise
- Conclusion

## 5. Time Series
- Introduction
- Structure
- Objectives
- Moving average
- Exponential moving average
- Autoregressive Integrated Moving Average
- Variations of Autoregressive Integrated Moving Average
- Multivariate time series
- Conclusion

## 6. Natural Language Processing
- Introduction
- Structure
- Objectives
- N-grams and normalization
- Term frequency-inverse document frequency
- Bag of words model
- Part-of-speech tagging
- Named entity recognition
- Word embeddings and word representation
- Naïve Bayes
- Miscellaneous
- Conclusion

## Index

- Time series analysis
- Natural language processing

## Objectives

This chapter will delve into fundamental data concepts using interview questions. The chapter is structured into four subsections as outlined in the structure. Upon completion of all sections, readers will acquire an understanding of data fundamentals and proficiency in data wrangling for ML.

## Supervised learning

Supervised learning is a class of machine learning that involves the usage of training data that is labeled. This means that every training example is associated with a correct answer. In this way, the model acquires the capability to find the relationship between inputs and outputs by reducing the error margin. The advantages of such an approach is primarily the ability to make accurate predictions and classifications when it concerns certain tasks, such as identifying objects in images, filtering spam messages, or diagnosing diseases. Supervised learning is also important in machine learning to acquire a fundamental understanding of how to build and improve predictive models to achieve maximum effectiveness in many fields.

## Question 1: Why is data preprocessing important in supervised learning?

Answer: Data preprocessing is one of the most important steps to perform analysis for any kind of ML problem or solve any type of ML use case, as no model can directly process the raw data efficiently. Most well-known models cannot handle missing data or string values. If these things are present in the data, it will throw an error. However, just solving this will not help the model, and in turn, it will produce an unsatisfactory result as the data is not properly engineered according to the model. For example, some models cannot handle non-scaled data, and some can. As a general practice, we all tend to perform the basic data preprocessing and feature engineering for most of the models.

The key components for labeled data include the following:

- Features
- Labels

The preceding two are the only major key components of the labeled data. There can be an n number of features but only one corresponding label for them.

Along with this, we have some information like the source of the data, how was the data collected, whether any data preprocessing happened after the data collection took place, why was the data collected, and what were some of the assumptions about the data then the quality of the data can be improved further in the next steps.

## Question 2: What is the difference between categorical and numerical data?

Answer: Numerical data refers to a continuous form of data that can be both positive and negative.

Categorical data generally refers to data categorized/grouped and represented in some form of string or number.

Here are some of the examples of the numerical and categorical data:

- A classic example of numerical data is the price of a stock, house, or other item.
- Gender, race, religion, and education level are some popular examples of categorical variables.
- Age range is generally considered as numerical data, and if it is binned into *Child*, *Teenager*, *Adult*, and *Elderly*, then this data becomes categorical.

## Question 3: How do you handle categorical data in supervised learning?

Answer: This might seem odd, but most of the models cannot handle string categorical data in its raw form. It has to be converted to some kind of numerical representation. The bare minimum data processing that needs to be performed is to have a mapping table and replace the categorical value with a numerical value. This process is known as label encoding. There are other techniques, like one-hot encoding, which can be leveraged so that the model can process the categorical variable.

Let us take an example that we have three categories for a feature namely, CAT_1, CAT_2, CAT_3. ML models cannot understand the string, so it has to be converted to a readable form. For label encoding, there is a map CAT_1 | 0, CAT_2 | 1, CAT_3 | 2. For one hot encoding, we have to break down the features into individual categories like FeatureA_CAT_1, FeatureA_CAT_2, and FeatureA_CAT_3, and each will be either true or false.

## Question 4: What is the significance of handling missing values in a dataset?

Answer: Like string categorical data, missing data cannot be handled by most of the models. We need to analyze why and what kind of values are missing and if there is any kind of relation or pattern in their missing values, this can lead to some additional interesting information which might help in the modelling process. This will help us to understand the data in more depth. There are a variety of techniques, like average filling, forward filling, etc, which can be used to fill the missing values.

## Question 5: Explain the concept of imputation for missing data and some strategies to handle it.

Answer: The concept of imputation is replacing the missing data with a certain value and it is very critical as it helps to keep the volume of data the same or similar, as missing values sometimes can be extremely high in volume which will lead to changes in the characteristics of the entire data.

There are multiple strategies to handle missing values. Some of the popular ones are as follows:

We can remove the entire row where we encountered missing values. This method can be hazardous if the volume of the data removed is very high. This will lead to a change in the data characteristics as the rest of the features with data will take a hit.

If we notice that the volume of the missing values is quite high and the feature is not that significant, we can drop the feature altogether to increase the data quality.

We can fill the missing values with the average or mean of the entire column or the average of some logical subsection which can be found after some data analysis.

Instead of filling with average, it can be filled with min value, max value, mode value, etc.

Note that handling missing values takes time to analyze and constant back and forth with the domain expert.

## Question 6: What are outliers in a dataset, and how can they affect supervised learning?

Answer: Outliers are defined as some data points that are out of the general data distribution or some abnormal points
