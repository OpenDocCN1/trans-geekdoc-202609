
## User-defined Exception

Sometimes a user may need to create own exceptions that best align with your programming needs and these are known as user-defined exceptions.

A user has to make a new class and derive from the class, `Exception` class.

## Summary

Files are used for future storage. To read from a file we need to open it and once through with it, we have to close it to free the resources tied with the file in Python. The inbuilt function `open()` in Python is used to launch a file. When this function is invoked, a file object is accessed and loaded sometimes referred to as a handle and it is used to modify or read the file accordingly. For the `readlines()` method, it will scan the entire file lines. After reading the entire file, the reading method will report empty status. The reason for empty status is because there are no more arguments for the method to process. The `read()` will go through each line in the file until there are no more lines to scan.

The `r` is used to launch the file for reading and is the default. The `w` is preferred when launching a file for writing. For exclusive file creation, we use the `x` mode. The operation will be unsuccessful if the file already we want already exists. The other mode, `a` is used to launch a file for adding data at the file end while retaining earlier content. The `a` model will create a new file in case it does not exist. For the `t` mode, it will launch the file in default text mode. The `b` mode is used to launch the file in binary mode. Lastly, the `+` mode is used for launching the file to allow reading and writing.

# Chapter 2: Main Concepts of Machine Learning

What is a ML workflow? What are the core steps of a typical ML workflow?

This chapter discusses the workflow of a ML project this includes all the steps required to build the proper ML project from scratch.

We will also go over data pre-processing, data cleaning, feature exploration and feature engineering and show the impact that it has on ML Model Performance. We will also cover a couple of the pre-modeling steps that can help to improve the model performance.

Python Libraries that would need to achieve the task:

*   `Numpy`
*   `Pandas`
*   `Sci-kit Learn`
*   `Matplotlib`

## Overview of the Workflow of ML

### Understanding the ML workflow

We can define the ML workflow in 3 stages.

1.  Gathering data
2.  Data pre-processing
3.  Researching the model that will be best for the type of data
4.  Training and testing the model
5.  Evaluation

Okay but first let’s start from the basics

### What is the ML Model?

The ML model can be defined as a piece of program which a data scientist or an engineer makes it smart by training it using data. So, for example, if you feed the model with garbage it will produce garbage meaning that the trained model provides wrong or false predictions if fed with invalid data or garbage.

#### Data pre-processing

It is one of the essential procedures in ML. It is the most important step that helps in making ML models more accurately. In ML, there is an 80/20 rule. Every data scientist should spend 80% time for data pre-processing and 20% time to perform the analysis.

### What is data pre-processing?

Data pre-processing refers to a process of cleaning the raw data. The data which is collected in the real world is usually converted to a clean set of data. Whenever the data is collected from varying sources, it is usually in a raw form, and this data is not feasible for the analysis phase.

Consequently, specific procedures are followed to turn the data into a reduced clean set of data; this process is known as pre-processing of data.

#### Researching the model that will be best for the type of data

Our main goal is to train the best performing model possible, using the pre-processed data.

##### Supervised Learning

In Supervised learning, an Artificial Intelligent system is presented with labeled information or data, which means that each data tagged with the correct label.

The supervised learning is categorized into two other categories which are Regression and Classification

###### Classification

The classification problem is when the target variable is categorical (meaning that the output could be classified-it belongs to either Class A or B or something else).

A classification problem refers to when an output variable is a group, such as blue or red, no disease or disease or not spam or spam.

These some most used classification algorithms.

*   `KNN`
*   `Naive Bayes`
*   `Random Forest`
*   `Logistic`

###### Regression

A regression problem happens when the targeted variable is continuous (meaning that the output is numeric).

Regression

As shown in the above representation, we can imagine that the graph’s X-axis is the `Test scores` and the Y-axis represents `IQ.` So we try to create the [best fit line](https://mathbits.com/MathBits/TISection/Statistics1/LineFit.htm) in the given graph so that we can use that line to predict any approximate IQ that is not present in the given data.

These some most used regression algorithms.

*   `Linear`
*   `Support Vector`
*   `Decision Trees`
*   `Gaussian Progresses`
*   `Ensemble Methods`

##### Unsupervised Learning

For unsupervised learning an Artificial Intelligence system is fed with un-categorized and unlabeled data and the algorithms of the system process the data before any training. The resultant output depends on the programmed or coded algorithms. Exposing a system to unsupervised learning is one of the ways of testing Artificial Intelligence.

The unsupervised learning is divided into two other groups known as Clustering and Association.

###### Clustering

A set of inputs is divided into groups. As opposed to classification, the groups are not known at the beginning, making this an unsupervised process or task.

Methods used for clustering are:

*   `K-Means`
*   `Gaussian`
*   `Boosting`
*   `Hierarchical`
*   `Spectral`

### Overview of models under categories

### Training and testing the model on data

For training a model we initially split the model into 3 three sections which are training data, validation data and testing data.

The classifier is usually trained using the training set of data, make sure you prepare the needed parameters using the validation set of data and then test the functioning of the classifier using an unseen test set of data. An essential thing to note is that when you are training the classifier only the training and validation set of data is available. The test set of data should not be used when training the classifier. The test set is normally available when testing the classifier.

If I had to summarize the main highlights of ML advances in 2018 in a few headlines, these are the ones that I would probably come up with:

*   AI hype and fear mongering cool down.
*   More focus on concrete issues like fairness, interpretability, or causality.
*   Deep learning is here to stay and is useful in practice for more than image classification (particularly for NLP).
*   The battle on the AI frameworks front is heating up, and if you want to be someone you better publish a few frameworks of your own.
