In the above plot, Salary is the dependent variable that is on (Y-axis) and the independent variable is on X-axis that is Experience. More experience means more salary. The regression line can be written as:

Y1 = a0 + a1X + ε

Where coefficients are a0 and a1 and the error term is ε.

Linear regression can have independent variables that are continuous or may be discrete in nature but have continuous dependent variables. The best fit line in linear regression is calculated using mean squared error that finds out the relationship between dependent that is Y and independent that is X. There is always a linear relationship that is present between both the two.

Linear regression only has one independent variable whereas in multiple regression there can be more than one independent variable.

Let us go through a regression problem. We will use the Boston dataset from Scikit-learn, this dataset holds information about the house value of different houses in Boston. Other variables that are present in the dataset are Crime, areas of non-retail business in the town (INDUS), and other variables.

# Step 1:

In the first step, we are going to import all the important libraries and most importantly, we have to import the dataset from sklearn.datasets.

```
from sklearn.linear_model import LinearRegression
from sklearn.datasets import load_boston
from sklearn.model_selection import train_test_split
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
boston = load_boston()
boston.data.shape, boston.target.shape
((506,13), (506, ))
```

# Step 2

We are going to visualize the dataset with the help of a python library called pandas, we will name features of the dataset and afterward, we are going to create a data frame with the help of the pandas’ library.