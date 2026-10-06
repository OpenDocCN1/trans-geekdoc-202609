# Multiple Linear Regression

Multiple Linear Regression or MLR is the type of regression in which we predict a value using two or more features like predicting the weight of a person using the age and height values. Here, the regression line is calculated using the following formula:

```
h(x_i) = b_0 + b_1x_{i1} + ... + b_px_{ip} + e_i
```

p is the number of the features, h(x_i) is the predicted value, b_0, b_1, etc. are regression coefficients and e_i are the residual errors i.e. errors in the data. This also gives rise to the following formula

```
y_i = h(x_i) + e_i
```

y is the actual value or the dependent variable

The training process for a MLR model is as same as we did before, but this time we have more features from which predictions will be made. Let's create a model to predict the salary of person if we get the age and gender as input. You can download the dataset from here

We need to need to import the same things as we did before

```
import pandas
from sklearn import linear_model
from sklearn import metrics
from matplotlib import pyplot
from sklearn.model_selection -
-import train_test_split
```

we will import train_test_split before

![](bbox=[0.645, 0.696, 0.854, 0.876])