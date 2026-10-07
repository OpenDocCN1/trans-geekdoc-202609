# 2.74 implemented Backward Elimination with Adjusted R-Squared In Python:

Let's take again the case of Multiple Linear Regression, with 5 independent variables. Automated Backward Elimination including Adjusted R-Squared can be implemented this:

```
# libraries
import matplotlib as plt
import pandas as pd
import numpy as np

# import data
daset = pd.read_csv("50_Startups.csv")
X = dataset.iloc[:, :-1] # rows except last
y = dataset.iloc[:, 4] #5th row

# convert to numerical
from sklearn.preprocessing import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
colctm = ColumnTransformer([('Encoder', OneHotEncoder(), [0, 3])], remainder="passthrough")
x_encoded = colctm.fit_transform(X)
# Last column is replaced with dummy columns (1 col)

# Avoiding dummy variable: omit [1]
go = x_encoded[:, 1:] # select all columns starting from 2nd column
y_go = np.array(y) #converting DataFrame to Vector/Array

# split dataset to train and Test
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, size=0.2, random_state=0)

# fitting linear model regression on training set
from sklearn.linear_model import LinearRegression
regressor = LinearRegression()
regressor.fit(X_train, y_train)

# predict on the test-set X
y_pred = regressor.predict(X_test)

#checking the score
print(np.concatenate((y_test.reshape(len(y_test)),1), y_pred.reshape(len(y_test)),1)))
print("\n--- Train Score: " + regressor.score(X_train, y_train))\nprint("\n--- Test Score: " + regressor.score(X_test, y_test) + " ============\=")
============= building the optimal model using Backward elimination ==========

# Only P-value implement automatic Backward Elimination: No manual iteration is needed ---

import statsmodels.api as sm
def backward_elimination(X, y):
numVars = len(X)
for i in range(0, numVars):
    regressor = sm.OLS(y, sm.add_constant(X)).fit()
    # picking the max p-value
    maxP = max(regressor.pvalues).astype(float)
    if maxP > 0.05:
        for j in range(0, numVars - i):
            # deleting the column
            if (regressor.OLS.pvalues[j].astype(float) == maxP):
                X = np.delete(X, j, 1) # deletes j-th column. "1 is used for column". To delete row "0"
                print(regressor.OLS.summary())
                return X
return
Sl = 0.05
X_pre = np.append((arr = np.ones(shape=(50, 1)).astype(float), X_go, axis =1) # interchange the columns
X_opt = X_pre[:,0, 1, 2, 3, 4]
XModeled = backward_elimination(X_opt, Sl)


import statsmodels.api as sm
def backward_elimination(X, Sl):
numVars = len(X)
temp = np.zeros((0, 6)).astype(float)
for i in range(0, numVars):
regressor = sm.OLS(y, expog(x)).fit()
maxVar = max(regressor.pvalues).astype(float)
adjb_before = regressor.ols.squared_adj.astype(float)
```