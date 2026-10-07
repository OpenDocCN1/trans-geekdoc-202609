Final conclusion: 4th and 5th iteration, we inspected the p-values. At 4th iteration, we end-up with RBD spend is definitely a very powerful predictor of has a high statistical effect on the dependent variable.
And as the second independent variable with enough statistical impact is Marketing Spend, we can see that the p-value is 0.06 in 6th.
But Marketing Spend quite actually slightly above the 5% significance level that we set. If we set another SL of 1% for example, we would have kept this independent variable.
If you want to strip the framework like the Backward Elimination Algorithm we need to remove this independent variable.

We will use later other metrics to make a better decision about that, when we will talk about Improving the Models Performance. In future we will use R-squared and Adj. R-squared to calculate this significance. [Section 7: Evaluating Results].

# NOTE:

We do not have a p-value because it's so small like 0.00001 type number.

# All code at Once

```
# Fundamental libraries
import matplotlib as plt
import pandas as pd
import numpy as np

# Import dataset
dataset = pd.read_csv("Startups.csv")\ = dataset.iloc[:, :-1] # all rows except last
y = dataset.iloc[:, [-1]] # the last row

# categorical to numerical
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
colTransformer = ColumnTransformer(transformers=("encoder", OneHotEncoder(), [3]]), remainder="passthrough")
X_encoded = np.array(colTransformer.fit_transform(X))
# X_encoded is now replaced with dummy columns (1st columns)

# Avoiding dummy-var trap: drop only the first dummy column variable
X_go = X_encoded[:, 1:] # select all columns starting from 2nd column
y_go = np.array(y) #converting Dataframe to Vector/Array

# split dataset to Train and Test
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X_go, y_go, test_size=0.2, random_state=0)

# Fitting Linear Regression on regression on test set
from sklearn.linear_model import LinearRegression
regressor = LinearRegression()
regressor.fit(X_train, y_train)

# predict on the test-set X test
y_pred = regressor.predict(X_test)

#Checking the score
print(np.concatenate((y_test.reshape(len(y_test)), y_pred.reshape(len(y_pred))), 1)))
print(f"\n- Train Score: {regressor.score(X_train, y_train)}
- Test Score: {regressor.score(X_test, y_test)}")

################################################# building the optimal model using Backward Elimination
################################################
# step 1: Preprocess for OLS
# import statsmodels.formula.api as smf
X_opt = np.append(X_go, y_go, np=np.opt.shape=(50, 1)).astype(int), axis=1)
# drop first and last column (row, column)
# convert to int type
# set axis=0
X_pred = np.append(y=np.opt.shape=(50, 1)).astype(int), values=X_go, axis=1) # interchange the columns

# iteration 1

# step 2: fit with OLS
X_opt = X_opt[:, [0, 1, 2, 3, 4]] # .new vector which will be optimized
```