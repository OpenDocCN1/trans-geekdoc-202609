```
from sklearn.svm import SVR
regressor = SVR(kernel='rbf')
regressor.fit(X, y)
```

```
# Visualising the SVR results
plt.scatter(X, color='red')
plt.plot(X, predict(X), color='blue')
```

```
# prediction
Here we will predict the output for level 6.5
because the candidate has 4+ years' experience as a regional manager,
so he must be somewhere between 7 and 6.
y_prd = regressor.predict([[6.5]]) # [[6.5]], Param mut must be 2-D array
print(y_prd)
# python prct_svr.py
```

**Feature needed:** SVR does not apply automatic Feature-Scaling as Simple and Multiple linear Model. **SVR** is not a common class as _Linearregression*

# Feature Scaling applied:

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
# Importing the Dataset, preview problem of "Bluff Detection"
dataSet = pd.read_csv('Position_Salaries.csv')
X = dataSet.iloc[:, 1:2]
y = dataSet.iloc[:, 2].values
```

```
# Splitting the dataset into the Training and Test set: No need here
```

```
# Feature Scaling
from sklearn.preprocessing import StandardScaler
sc_x = StandardScaler()
sc_y = StandardScaler()
X_scaled = sc_x.fit_transform(X.reshape(-1, 1))
y_scaled = sc_y.fit_transform(y)
```

**New prediction:** We don't use `fit_transform()` because model is already fitted. We only use `transform()`

```
sc_X.transform(np.array([[6.5]]))
```

**Transform 6.5 to array:** Expecting 2-d array we need to pass 6.5 as array. The result y_prd is also scaled output.

**Reverse Scaling (inverse transformation):** Since is applied and we passed 6.5 as scaled array. The result y_prd is also scaled output.

```
y_prd = regressor.predict(sc_X.transform(np.array([[6.5]]))
print('prediction under scaled data : ', y_prd)
y_inv_sc = sc_y.inverse_transform(y_prd)
print('Reverse prediction :', y_inv_sc)
```

Notice in "Visualizing the SVR results" all scaled-dada is used to plot the model.

SVR fitted to the place where most observations appear.