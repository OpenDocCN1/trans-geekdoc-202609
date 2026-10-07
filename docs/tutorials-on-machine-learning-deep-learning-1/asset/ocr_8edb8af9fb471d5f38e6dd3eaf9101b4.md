```
from sklearn.model_selection import train_split
# 0.25 size means "1/4" of the total observation
x_train, x_test, y_train, y_test = train_split(X, y, test_size=0.25, random_state=0)

# Feature Scaling
from sklearn.preprocessing import StandardScaler
# y need not to be scaled: categorical variable
sc_x = StandardScaler()
X_scaled = sc_x.fit_transform(X)
st_x = StandardScaler()
x_train = st_x.fit_transform(X_train)
test = st_x.transform(X_test)
```

```
-----
# Feature-Scaling
from sklearn.preprocessing import StandardScaler
# y need not to be scaled: categorical variable
sc_x = StandardScaler()
X_scaled = sc_x.fit_transform(X)
```

```
# Data Split
from sklearn.model_selection import train_test_split
# 0.25 size means "1/4" of the total observation
x_train, x_test, y_train, y_test = train_split(X_scaled, y, test_size=0.25, random_state=0)
```

```
# Fit dataset to Logistic regression
from sklearn.linear_model import LogisticRegression # Import class
# instead of "regressor" we now use "classifier"
classifier = LogisticRegression(random_state=0) # create object
classifier.fit(X_train, y_train) # fit the dataset
```

```
# Predict
y_pred = classifier.predict(X_test)
```

```
# Making the confusion matrix use the function "confusion_matrix"
# Class in capital letters, functions in small letters
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_true=y_test, y_pred=y_pred)
# parameters of cm: y_true: Real values, y_pred: Predicted value
```

```
# Visualising the training set results
from matplotlib.colors import ListedColormap
X_set, y_set = X_train, y_train
X1, X2 = np.meshgrid(np.arange(X_set[:,0].min(), X_set[:,0].max()+0.01, step=0.01), np.arange(X_set[:,1].min(), X_set[:,1].max()+0.01, step=0.01))
plt.contour(X1, X2, classifier.predict(np.array([X1.ravel(), X2.ravel()]).T).reshape(X1.shape), alpha=0.5, cmap=ListedColormap(['red', 'green']))
plt.xlim(X_set[:,0].min(), X_set[:,0].max())
plt.ylim(X_set[:,1].min(), X_set[:,1].max())
for i, j in enumerate(y_set=j):
    plt.scatter(X_set[j,0], X_set[j,1], c=ListedColormap(['yellow', 'blue'])(j), label=j)
plt.title('Logistic Regression (Training set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

```
# Visualising the test set results
from matplotlib.colors import ListedColormap
X_set, y_set = X_test, y_test
X1, X2 = np.meshgrid(np.arange(X_set[:,0].min(), X_set[:,0].max()+0.01, step=0.01), np.arange(X_set[:,1].min(), X_set[:,1].max()+0.01, step=0.01))
```