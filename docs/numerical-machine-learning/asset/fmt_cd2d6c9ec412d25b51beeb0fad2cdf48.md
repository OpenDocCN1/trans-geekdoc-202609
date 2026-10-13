
| [4] | | Bishop C.M.. Pattern Recognition and Machine Learning. New York, NY: Springer, 2006 |
| [5] | | Wang Z., Irfan S.A., Teoh C., Bhoyar P.H.. "Linear Regression" in Numerical Machine Learning. Chapter 2. Bentham Science, 2023 |
| [6] | | Wang Z., Irfan S.A., Teoh C., Bhoyar P.H.. "Logistic Regression" in Numerical Machine Learning. Chapter 4. Bentham Science, 2023 |

# Logistic Regression

**Zhiyuan Wang**, **Sayed Ameenuddin Irfan**, **Christopher Teoh**, **Priyanka Hriday Bhoyar**

## Abstract

This chapter delves into logistic regression, a widely used machine learning algorithm for classification tasks, with a focus on maintaining accessibility by minimizing abstract mathematical concepts. We present a concrete numerical example employing a small dataset to predict the ease of selling houses in the property market, guiding readers through each step of the process. Additionally, we supply sample codes and draw comparisons with the logistic regression model available in the `scikit-learn` library. Upon completion of this chapter, readers will have gained a comprehensive understanding of the inner workings of logistic regression, its relationship to algorithm implementation and performance, and the knowledge necessary to apply it to practical applications.

**Keywords:** Logistic Regression, Classification, Numerical Example, Small Dataset, Scikit-Learn.

## 4.1. Introduction to Logistic Regression

Logistic regression is a supervised machine learning algorithm for modeling the probability of a discrete output given input features [[1]](#9789815136982-C4.html#r1), [[2]](#9789815136982-C4.html#r2). Despite its name, logistic regression is more of a classification model than a regression model. It is commonly used to model a dichotomous (binary) output, *i.e.*, anything with two possible values/classes/labels, such as true/false, yes/no, 1/0, on/off, good/bad, malignant/benign, and pass/fail, to name a few. The foundation of logistic regression lies in its ability to model the relationship between input features and a categorical outcome by utilizing the logistic function, also known as the sigmoid function. This function ensures that the predicted probabilities lie within the range of 0 and 1, making it suitable for classification tasks. Logistic regression has gained immense popularity due to its simplicity, interpretability, and efficiency in various real-world applications. Some of these applications include spam filtering, customer churn prediction, medical diagnosis, and credit risk assessment.

Unlike linear regression, logistic regression does not require the assumption of a linear relationship between the independent (`X`) and dependent (`Y`) variables. Besides, the errors between the true and predicted outputs need not conform to a normal distribution. Moreover, the spread of the errors (*i.e.*, the variance of the errors) need not be constant along the values of dependent variables; that is, homoscedasticity is not required. However, there are still several essential assumptions for logistic regression [[3]](#9789815136982-C4.html#r3), [[4]](#9789815136982-C4.html#r4). Firstly, when there is more than one independent variable (`X`), it requires little or no correlation between the independent variables (*i.e.*, little or no multicollinearity). Secondly, it assumes that the independent variable(s) have a linear relationship with the logarithm of the odds; odds is just another way of expressing probability (`P`) and is defined as the ratio of the probability of an event occurring to the probability of an event not occurring (*i.e.*, `P/(1-P)`). Thirdly, by default, logistic regression is used to solve binary classification problems, requiring the dependent variable (`Y`) to be dichotomous. On the other hand, it is worth mentioning that with some modifications and improvements like the one-vs-rest (OvR) method, logistic regression can be scaled up for solving multi-class classification problems. Nevertheless, multi-class classification is outside the scope of the present chapter as it focuses on binary classification using the logistic regression algorithm.

## 4.2. Mathematics of Logistic Regression

Mathematically, the linear regression discussed in Chapter 2 can be upgraded to logistic regression after introducing a sigmoid function for mapping the linear output to probability and employing a different loss function.

In comparison with Equation (2.2) in Chapter 2 for linear regression, the only change made to Equation (4.1) here is to use a variable `Z` (rather than `Y`) to represent the linear output, which is just an intermediate result in the process of logistic regression.

```
Z = b + Σ(wj * Xj)  (j=1 to n)
```

Here,

- `Z` is the intermediate linear output
- `b` is the bias
- `n` is the number of input features
- `wj` is the weight of the jth feature
- `Xj` is input value of the jth feature

The sigmoid function for mapping the intermediate linear output to probability is defined as Equation (4.2) and plotted in [Fig. (1)](#9789815136982-C4.html#f1).

![Plot of the sigmoid function.](Images/9789815136982-C4-F1.jpg)

```
Y = 1 / (1 + e^(-Z))
```

Here,

- `Z` is the intermediate linear output from the linear Equation (4.1)
- `Y` is the mapped probability

As can be seen from [Fig. (1)](#9789815136982-C4.html#f1), the sigmoid function maps the linear output `Z` into a probability `Y` that is in the range of 0 to 1. The default threshold is 0.5, meaning that if `Y ≥ 0.5`, it will be rounded up to 1 and predicted as class 1; whereas, if `Y < 0.5`, it will be rounded down to 0 and predicted as class 0.

Similar to the notations used in Chapter 2 for linear regression, lowercase `xi` is used to denote the feature values of the ith sample (out of the total `m` rows of samples from the training dataset), then `xij` will be the value of the jth feature (out of the total `n` input features) at the ith sample, as shown in [Fig. (2)](#9789815136982-C4.html#f2). Lowercase `yi` is used to represent the known output (*i.e.*, true output) of the ith sample, and `ŷi` is used to denote the corresponding predicted output (*i.e.*, the mapped probability after the sigmoid function) by the logistic regression model. The general term Equations (4.1) and (4.2) are updated to Equations (4.3) and (4.4), respectively.

![Illustration of notations using an exemplary training dataset.](Images/9789815136982-C4-F2.jpg)

```
zi = b + Σ(wj * xij)  (j=1 to n)
```

Here,

- `i ∈ [1, m]`; `m` is the number of training samples
- `xij` is the value of the jth feature at the ith sample
- `b` is the bias
- `n` is the number of input features
- `wj` is the weight of the jth feature
- `zi` is the intermediate linear output for the ith sample

```
ŷi = 1 / (1 + e^(-zi))
```

Here,

- `i ∈ [1, m]`; `m` is the number of training samples
- `zi` is the intermediate linear output for the ith sample
- `ŷi` is the predicted output (*i.e.*, the mapped probability) for the ith sample

Cross-entropy loss function (also known as logistic loss or log loss function) is employed in logistic regression to quantify the error between the true and predicted outputs, which is defined in Equation (4.5).

```
Li = -[yi * log(ŷi) + (1 - yi) * log(1 - ŷi)]
```

Here,

- `i ∈ [1, m]`; `m` is the number of training samples
- `Li` is the loss for the ith sample
- `yi` is the true output for the ith sample
- `ŷi` is the predicted output (*i.e.*, the mapped probability) for the ith sample
- `log` used is the natural logarithm (*i.e.*, to the base `e`)

The mean loss of all samples is defined in Equation (4.6).

```
L = (1/m) * Σ(Li)  (i=1 to m)
```

Here,

- `Li` is the loss for the ith sample
- `L` is the mean loss
- `m` is the number of training samples
