```
plt.contour(X1, X2, classifier.predict(np.array([X1.ravel(), X2.ravel()])).reshape(X1.shape),
plt.contour(X1, X2, alpha=0.25, cmap=ListedColormap(['red', 'green']))
plt.xlim(X1.min(), X1.max())
for i, j in enumerate(y_set):
    plt.scatter(X_set[y_set == j][:,0], j=1, c = ListedColormap(['yellow', 'blue'])(i), label = j)
plt.title('Logistic Regression (Test set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

We will get the dataset as output. Consider the given image:

![](bbox=[0.255, 0.255, 0.745, 0.575])

# New Template for Classification Problem

```
# Library
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Data Extract
dataset = pd.read_csv("Social_Network_Ads.csv")
X = dataset.iloc[:, [2,3]].values
y = dataset.iloc[:, -1].values

# Feature-Scaling after Data Split
# Data Split
from sklearn.model_selection import train_split
# We split the dataset into train and test set
X_train, X_test, y_train, y_test = train_split(X, y, test_size=0.25, random_state=0)

# Feature-Scaling
from sklearn.preprocessing import StandardScaler
# y need not be scaled: categorical variable
sc = StandardScaler()
X_sc = sc.fit_transform(X)
st_sc=StandardScaler()
```