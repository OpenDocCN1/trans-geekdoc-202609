How to predict: Next we determine y, the value is determined by taking the average of the values in a terminal-leaf (the last iteration) i.e. just take the average of y for all points of the leaf and that'll be the value that will be assigned to any new point that falls in that.
The whole point of this exercise is to add more information into our chart into our system to better predict.
Our machine learning algorithm just takes the average across all of the points and whatever is wherever you point the new element of data, is to add a data set wherever it falls.

So, we split our diagram up into terminal leaves and the machine learning algorithm has added information nurture into our system. So that we can more accurately predict the value or assign to a new element. Following is our completed decision tree.

![](bbox=[0.247, 0.215, 0.752, 0.465])

# 2.5.2 Decision Tree Regression Model practice with Python

# Practiced version

```
# Library
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Data Extract
dataset = pd.read_csv("Position_Salaries.csv")nX = dataset.iloc[:, 1:2].values
y = dataset.iloc[:, 2].values

# Feature-Scaling
from sklearn.preprocessing import StandardScaler
sc_x = StandardScaler()
sc_y = StandardScaler()
X_scaled = sc_x.fit_transform(X)
y_scaled = sc_y.fit_transform(y.reshape(-1, 1))

# Data Split : No need for this example
# Fit dataset to model
from sklearn.tree import DecisionTreeRegressor
regressor = DecisionTreeRegressor(random_state=0)
regressor.fit(X_scaled, y_scaled)

# Predict
```