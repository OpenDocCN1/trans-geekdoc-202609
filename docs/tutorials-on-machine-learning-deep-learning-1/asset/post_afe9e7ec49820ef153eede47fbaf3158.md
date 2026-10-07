
# Chapter 8 : Part 4

# Deep Learning

# ANN: Artificial Neural Network

Python Implementation

- Here in the first branch of deep learning (ANN), we are going to study this classification problem ANN.
- In the next chapter we study CNN (convolutional neural networks) another branch of deep learning which could work well for computer vision tasks unlike artificial neural networks (ANN).

## 8.4.1 Business Problem Description

**Deep learning** is one of the most fascinating and the most powerful/branch of Machine Learning. We will build a powerful ML model based on **Deep Neural Networks.**

Today deep learning is used for many of demanding and highly intensive tasks, for example computer vision (like recognizing faces and pictures) or medicine (recognizing tumors in some brain images).

In deep learning it can be used for making predictions (regression) or classifications for Business Problems.

And it is also used for recommended systems with the use of Boltzmann machines.

| Rownumber | CustomerID | Surname | CreditScore | Geography | Gender | Age | Tenure | Balance | NumOfProduct/Card | IsActiveMember | MonthlySalary | EstimatedSalary |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1566002 | Harvard | 619 | France | Female | 42 | 2 | 83807.0 | 2 | 1 | 101348.8 | 10134.8 |
| 2 | 1566885 | Mitchell | 680 | Germany | Male | 37 | 2 | 150668.0 | 3 | 1 | 11951.5 | 11951.5 |
| 3 | 1567039 | Gonzalez | 502 | Spain | Female | 52 | 4 | 159660.5 | 3 | 1 | 11951.7 | 11951.7 |
| 4 | 1567444 | Gomez | 610 | France | Male | 38 | 4 | 125510.5 | 2 | 1 | 7098.4 | 709.84 |
| 5 | 1572788 | Martinez | 530 | Germany | Female | 43 | 3 | 0.0 | 1 | 1 | 14973.1 | 1497.31 |
| 6 | 1579446 | Taylor | 600 | France | Male | 50 | 5 | 144612.5 | 2 | 1 | 10006.8 | 1000.68 |
| 7 | 1579551 | Bartlett | 822 | France | Male | 50 | 5 | 0.0 | 2 | 1 | 821.52 | 82.152 |
| 8 | 1579613 | Clark | 540 | Spain | Female | 39 | 4 | 110481.5 | 2 | 1 | 811.52 | 81.152 |
| 9 | 1579365 | Heck | 501 | France | Male | 40 | 4 | 142005.7 | 2 | 1 | 79466.5 | 7946.65 |
| 10 | 1580110 | Brown | 694 | France | Female | 34 | 4 | 114016.2 | 2 | 1 | 1245.6 | 1245.62 |
| 11 | 1581678 | Lee | 528 | UK | Male | 34 | 6 | 60016.2 | 2 | 1 | 80018.2 | 8001.82 |
| 12 | 1582317 | White | 487 | Spain | Female | 41 | 5 | 0.0 | 2 | 0 | 0 | 0 |
| 13 | 1583444 | Gray | 544 | UK | Male | 24 | 5 | 0.0 | 2 | 0 | 26260.9 | 2626.09 |
| 14 | 1584995 | May | 550 | France | Female | 25 | 5 | 0.0 | 2 | 1 | 190857.9 | 19085.79 |
| 15 | 1569383 | Chen | 549 | France | Female | 35 | 5 | 0.0 | 2 | 1 | 6991.5 | 699.15 |
| 16 | 1500682 | Scott | 650 | - | - | - | - | - | - | - | - | 6991.65 | - |

Data-set: We have a dataset containing: RowNumber, CustomerID, Surname, Geography(country), and some other... ... customers of the bank. A dependent variable, **Exited**, it indicates if a customer **leaves** a bank or not. The data-set contains data of 10000 customers.

- The bank has been using unusually **high churn rates**. Churn is when people **leave** the bank. They want to understand what the problem is. We are to use learning on this data-set and give them some insights.

This fictional bank operates in Europe across three countries **France, Spain** and **Germany**. They have lots of customers so they use this sample of 10000 customers and they measured six months ago before they knew about them,

- Their **CustomerID**, their **Surname**, **CreditScore**, **Geography**, **Gender**, **Age Tenure** (how long they have been with the bank).

- The **Balance** of the accounts that they had in time, the **NumberOfProduct/Card** that they had in time (i.s. savings account, credit card or loan), and **HasCard** (did the customer have a credit card or not).

**IsActiveMember** (active or not active member can be measured by different organizations. It could be whether the customer not logged into their **online banking** in the past month after a **transaction** in the past two months or other measurement like that.

**EstimatedSalary** (the salary of the customers but based on the other things they know could estimate a salary for them).

- So six months ago they measured all of these things and they waited six months and observed which customer is leaving the bank and stayed. Here **1** means that in the data-set, the **Exited** tells you whether or not the person left the bank within those six months. **0** means the person **stayed** in the bank.

Churn rate: Churn rate, in its broadest sense, is a measure of the number of individuals or moving out of a collective group over a specific period.

- Our goal is to create a Geodemographic segmentation model to tell the bank which of its customers are at highest risk of leaving; we are to solve this problem by using Artificial Neural Networks.

- Other applications: For a customer centric organization is going to be valuable, it doesn't have to be for churn.

## 8.4.2 Data Preprocessing

We already know that we are to deal with a classification problem. We have independent variables: CustomerID, CreditScore, Surname, Geography, Gender, Age, Tenure. We will predict which customers are leaving the bank.

Installing Libraries: We need to install 3 libraries: Theano, TensorFlow, Keras.

- Theano is a Python library that allows you to define and efficiently evaluate mathematical expressions multi-dimensional arrays. Primarily developed by the Montreal Institute for Learning Algorithms (MILA) at the Université de Montreal.
- What is also great about this library is it can run on CPU or GPU. TensorFlow is another open source numerical-computation library that runs very fast. It was originally developed by the Google brain team and it's now under the Apache 2.0 license.
- These libraries Theano and TensorFlow are used mostly for research and development purposes. You have to use these to build a Neural Network from scratch with many lines of code. If you want to do some research to improve the Deep Neural Networks or develop a new kind of Neural Network or any other kind of Deep Learning Models.
- Keras We are not going to use Theano and TensorFlow directly; we are going to use another library Keras that in some ways wraps the two libraries. Keras helps to build Deep Neural Networks in a few lines of code. We will use Keras to build Deep Learning Models effectively by using scikit-learn.

Tensorflow download & setup: TensorFlow runs on 64bit OS. You might need python 3.7 or 3.8 and then you use this command: `pip install tensorflow`. command prompt to install following:

| Anaconda Environment for TF | Conda Environment: You might need to re-install scipy in the created environment. Also install scikit-learn, matplotlib |
|---|---|
| Create environment for TF. Choose the Python version. Execute on cmd. | conda create --name tensorflow=3.8 activate tensorflow |
| After that install using pip. | Above will install tensorflow |

```
pip install scikit-learn
pip install numpy
pip install matplotlib
pip install statsmodels
```

Following might be useful

- conda install scipy
- pip install tensorflow-gpu
- pip install tensorflow

```
conda update -n base -c defaults conda
```

Install Keras and Theano:

- pip install keras
- pip install Theano

Choose and install using GPU or CPU.
Finish the installation command
