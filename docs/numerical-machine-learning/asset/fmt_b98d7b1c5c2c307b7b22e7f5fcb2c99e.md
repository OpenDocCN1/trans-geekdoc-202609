
In conclusion, machine learning is a rapidly evolving field with a rich history and an expanding range of applications across various industries. As a transformative technology, it has the potential to revolutionize numerous aspects of our lives. This book bridges the gap between abstract mathematical theories and the practical application of machine learning through easy-to-understand numerical examples and simple Python codes. This approach helps readers develop a more tangible understanding of machine learning algorithms, develop intuition about their behavior, and improve problem-solving skills. By working through numerical examples, readers/students can learn to approach various types of problems systematically and be better equipped to apply these algorithms to real-world challenges.

As machine learning continues to advance and become even more pervasive in the coming years, it is crucial for practitioners, researchers, and students to develop a strong foundation in the fundamental concepts and techniques of the field. By acquiring this knowledge and building upon it, they will be better positioned to contribute to the ongoing growth and development of machine learning and to harness its transformative potential to address a wide range of challenges and opportunities in various sectors.

## REFERENCES

| | |
| --- | --- |
| [1] | Fradkov A.L.. Early history of machine learning. IFAC-PapersOnLine 2020 53 2 1385 1390 10.1016/j.ifacol.2020.12.1888 |
| [2] | Goodfellow I., Bengio Y., Courville A.. Deep Learning. London, England MIT Press 2016 |
| [3] | Mueller J.P., Massaron L.. Machine Learning for Dummies. 2nd ed Nashville, TN John Wiley & Sons 2021 |
| [4] | Mueller A.C., Guido S.. Introduction to machine learning with python: A guide for data scientists. Sebastopol, CA O’Reilly Media 2016 |
| [5] | Park M., Wang Z., Li L., Wang X.. Multi-objective building energy system optimization considering EV infrastructure. Appl. Energy 2023 332 120504 10.1016/j.apenergy.2022.120504 |
| [6] | Raschka S.. Python Machine Learning. Birmingham, England Packt Publishing 2015 |

# Linear Regression

**Zhiyuan Wang**, **Sayed Ameenuddin Irfan**, **Christopher Teoh**, **Priyanka Hriday Bhoyar**

## Abstract

In this chapter, we delve into linear regression, a fundamental machine learning algorithm for predicting numerical values. While maintaining a concise overview of the mathematical theories, we prioritize an accessible approach by focusing on a concrete numerical example with a small dataset for predicting house sale prices. Through a step-by-step walkthrough, we illustrate the inner workings of linear regression and demonstrate its practical implementation. Additionally, we offer sample codes and a comparison with the linear regression model from `scikit-learn` to reinforce understanding. Upon completing this chapter, readers will gain a comprehensive understanding of linear regression's inner workings and its relationship to algorithm implementation and performance, and be better prepared to apply it to real-world projects.

**Keywords:** Linear Regression, Numerical Example, Small Dataset, Housing Price Prediction, Scikit-Learn.

## 2.1. INTRODUCTION TO LINEAR REGRESSION

Linear regression is a supervised machine learning algorithm that aims to determine the best-fit linear line between a dependent variable and one or more independent variables. It typically carries out regression tasks. It is one of the easiest, most well-understood, and most popular algorithms in many machine learning applications [[1](#9789815136982-C2.html#r1), [2](#9789815136982-C2.html#r2)]. It can be employed to predict the values of continuous numerical variables such as salary, sales revenue, dividend yield, greenhouse gas emission, and house price, to name a few.

Despite its simplicity, linear regression remains a powerful tool in the field of machine learning, providing a strong foundation for understanding the underlying input-output relationships between variables. It serves as an excellent starting point for beginners in the field, offering a straightforward and interpretable approach to modeling. Moreover, linear regression can act as a benchmark for evaluating the performance of more complex algorithms, allowing practitioners to gauge the effectiveness of their chosen models. While linear regression may not always be the most advanced or accurate method for every situation, its ease of use, interpretability, and versatility continue to make it a valuable asset in a variety of real-world applications and industries.

There are several fundamental assumptions associated with linear regression [[3](#9789815136982-C2.html#r3), [4](#9789815136982-C2.html#r4)]. Firstly, it is assumed that the dependent variable is linearly correlated to the independent variable(s). Secondly, when there is more than one independent variable, no correlation should exist between the independent variables (i.e., no multicollinearity). Thirdly, the errors between the true values and predicted values by the linear regression model should approximately conform to a normal distribution, with most having errors close to 0. Fourthly, the spread of the errors (i.e., the variance of the errors) ought to be constant along the values of the dependent variable. This is technically known as homoscedasticity, which can be checked by creating a scatterplot of errors versus the dependent variable.

## 2.2. MATHEMATICS OF LINEAR REGRESSION

The mathematics of linear regression starts from a simple linear equation, shown in Equation (2.1) and (Fig. **2.1**), where there is only one independent variable `X` and one dependent variable `Y`.

```
Y = b + wX
```

![Fig. (2.1)](Images/9789815136982-C2-F1.jpg)

Plot of simple linear equation Y=b+wX.

Variable `X` has an associated coefficient `w`, which is often used interchangeably with the terms: *weight*, *slope*, or *gradient*. In the context of machine learning, it is most often referred to as weight.

Likewise, `b` represents the intercept with *Y*-axis and is often known as *bias* in machine learning. The independent variable `X` is commonly called *input*, which is used interchangeably with the following terms: *input feature*, *attribute*, *characteristic*, *field*, and *column*. The dependent variable `Y` is commonly referred to as *output*, *target, class,* and *label*.

In reality, more often than not, we will have more than one independent variable, and Equation (2.1) would have to be updated to a general term Equation (2.2) to cater for this.

```
Y = b + Σ(wj * Xj) for j=1 to n
```

Here,

- `Y` is the dependent variable
- `b` is the bias
- `n` is the number of input features
- `wj` is the weight of the jth feature
- `Xj` is input value of the jth feature

The goal of linear regression is to find the best-fit linear equation model that maps the relationship between input `X` and output `Y`, in the form of Equation (2.2) with the optimal weights and bias, which produces the least error (synonymously known as loss in machine learning) between the known true output `Y` values and predicted output `Y` values by the model.

Let us use lowercase `xi` to denote the feature values of the ith sample (out of the total `m` rows of samples from the training dataset), then `xij` will be the value of the jth feature (out of the total `n` input features) at the ith sample, as shown in [Fig. (**2.2**)](#9789815136982-C2.html#f2.2). Lowercase `yi` is used to represent the known output value (i.e., true output value) of the ith sample, and `y^i` is used to denote the corresponding predicted output value by the linear equation model. Equation (2.2) is then updated to Equation (2.3).

```
y^i = b + Σ(wj * xij) for j=1 to n
```

![Fig. (2.2)](Images/9789815136982-C2-F2.jpg)

Illustration of notations using an exemplary training dataset.

Here,

- `i ∈ {1, ..., m}` `m` is the number of training samples
- `xij` is the value of the jth feature at the ith sample
- `b` is the bias
