# Chapter 2 : Section 4
Support Vector Regression (SVR)

# 2.4.1 Implementation of SVR in Python

+   Data Preparation: We continue with our previous problem of "Bluff Detection"

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# data preprocessing
# Importing the dataset. previous problem of "Bluff Detection"
dataSet = pd.read_csv("Position_Salaries.csv")
X = dataSet.iloc[:, 1].values
y = dataSet.iloc[:, 2].values
```

+   Fitting SVR to the dataset:
We'll implement SVR from the sclearn library because SVR is actually a vector machine SVM for regression.

```
# Fitting SVR to the dataset
from sklearn.svm import SVR
regressor = SVR(kernel="rbf")
regressor.fit(X, y)
```

+   Choosing kernel:
We have many parameters for many ML models. The most important parameter that we need to focus on is the kernel. The kernel is whether you use a linear SVR or a polynomial SVR or Gaussian SVR. 'linear', 'poly', 'rbf', 'sigmoid', 'precomputed' as the most common kernel.

+   The one we want to use is the 'rbf' kernel. Why not that? Because our problem is non-linear. The linear kernel/would make a linear machine model that would not be appropriate for a nonlinear problem.

+   And then we have the choice 'poly' and 'rbf', both these kernels could work for our problem. We're going to choose the most common which is the Gaussian kernel and therefore 'rbf' here.

+   Prediction without scaling:
In y_pred, we use [[6.5]]. Since Parameter must be 2-D array

```
y_pred = regressor.predict([[6.5]]) # [[6.5]], since Parameter must be 2-D array
print(y_pred)
```

# Before scaling is applied

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# data preprocessing
# Importing the dataset. previous problem of "Bluff Detection"
dataSet = pd.read_csv("Position_Salaries.csv")
X = dataSet.iloc[:, 1].values
y = dataSet.iloc[:, 2].values

# Splitting the dataset into the Training set and test set: No need here

# Feature Scaling

# Fitting SVR to the dataset
```