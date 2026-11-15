true negatives is what is intended to increase so as to influence the accuracy [18]. Therefore, the accuracy is calculated as follows:

```
\frac{TP+TN}{TP+FP+FN+TN} (2.1)
```

Further, for the regression models, we will be using the mean absolute error (MAE) and mean squared error (MSE) determinants. The two values are calculated as follows:

```
MAE=\frac{1}{n}\sum_{i=1}^n|y_i-\hat{y}_i| (2.2)
```

```
MSE=\frac{1}{n}\sum_{i=1}^n(y_i-\hat{y}_i)^2 (2.3)
```

In Equations 2.2 and 2.3, $n$ is the total number of instances, $y_i$ is the predicted value of instance $i$, and $\hat{y}_i$ is the real target value of $i$. The lower the value of MAE and MSE, the better the model [19].

Within all the supervised learning and unsupervised learning algorithms alike, the dataset variation over testing and training, the ratio of balance, and the type of scaling affect the accuracy of the data. For instance, within the classification LR, StandardScaler gives an accuracy of 0.82, while the MinMaxScaler raises the accuracy to 0.93, which is quite the accuracy jump, given the use of the same algorithm.

# 2.4.1.1 Linear Regression

A fundamental statistical method for figuring out the relationship between two continuous variables is linear regression. It assumes that there is a straight line between the independent and dependent variables. An unknown value can be predicted using linear regression analysis based on an analogous unknown value [20]. The variable that a researcher hopes to predict is known as the dependent variable. The variable that is used to predict the value of the other variable is known as the independent variable. Figure 2.8 illustrates the accuracy for linear regression.

In Figure 2.8, two terms help determine the accuracy; MAE and MSE are the accuracy calculators for regression models. The closer the two values are to 0, the

![](bbox=[0.25, 0.74, 0.74, 0.88])

FIGURE 2.8 Accuracy for linear regression.