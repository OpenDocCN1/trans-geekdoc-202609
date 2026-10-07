# Difference between Regression and Classification:

| Regression Algorithm | Classification Algorithm |
|---|---|
 i. In *Regression*, the output variable must be of continuous nature or real value. | ii. In *Classification*, the output variable must be of discrete value. |
 iii. The task of the **regression algorithm** is to **map** the inputvalue(x) with the continuous outputvariable(y). | iv. The task of the **classification algorithm** is to map the inputvariable(s) with the *discrete* outputvariable(y). |
 v. Regression Algorithms are used with *continuous data*. | vi. Classification Algorithms are used with *discrete data*. |
 vii. In *Regression*, we try to find the *best fit line*, which can predict the output more accurately. | viii. In *Classification*, we try to find the **decision boundary**, which can divide the dataset into different classes. |
 ix. Regression algorithms can be used to solve the regression problems such as Weather Prediction, House price prediction, etc. | x. Classification Algorithms can be used to solve classification problems such as identification of spam cells, Speech Recognition, identification of cancer cells, etc. |
 xi. The regression algorithm can be further divided into *Linear* and *Non-linear Regression*. | xii. The Classification algorithms can be divided into *Binary* and *Multi-class Classifier*.

# **Does regression mean prediction?**

Using regression to make predictions doesn't necessarily involve *predicting* the future. Instead, you *predict* the mean of the dependentvariablegiven specific values of the independentvariable(s).

# 3.1.2 Introduction to Classification problem

# Logistic Regression

This is new:
Action (Y/N)

We know this:
Salary ($)

![](bbox=[0.223, 0.584, 0.775, 0.696])

We already know how to deal with data in the Right side (with regression). But how do we deal with the data in the Left side? In the Left side data, assume the problem as: Action of buying a product, from the left side we can see there is actually a correlation, where "older people usually takes action - Yes younger people actually doesn't take actions".

We can see that the *observations* on the bottom they're a bit more to the *left* and *observations* on the *top* are a bit more to the right implying, that "probably older people are more likely to take action on the shopping offer".

# Action (Y/N)

![](bbox=[0.563, 0.805, 0.853, 0.946])

Use Linear Regression first: We try our existing method in our toolkit which is the linear regression, it doesn't look like the best approach and not the best method to solve this problem.

Let's draw a horizontal line y = 1. Now, we want to predict for that person of certain we want to predict whether they will take up the offer or not.

To do that, we will try the probability rules that will state a probability or a likelihood of that person taking that offer.