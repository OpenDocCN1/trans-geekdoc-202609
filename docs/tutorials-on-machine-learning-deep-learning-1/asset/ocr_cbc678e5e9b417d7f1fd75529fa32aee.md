```
x_train = st_x.fit_transform(x_train)
x_test = st_x.transform(x_test)
```

```
# Feature-Scaling before Data Split
```
# Feature-Scaling
# from sklearn.preprocessing import StandardScaler
# y may not need to be scaled: categorical variable
sc_x = StandardScaler()
x_scaled = sc_x.fit_transform(x_train)

# Data Split
# from sklearn.model_selection import train_test_split
# 0.25 test_size means "1/4" of the total observation
x_train, x_test, y_train, y_test = train_test_split(x_scaled, y, test_size = 0.25, random_state = 0)
```
```

```
# Fit train set to Model Classifier
from sklearn._ import Classifier
clf = Classifier()
clf.fit(x_train, y_train) # fit the dataset
```

```
# Predict
y_pred = clf.predict(x_test)

# Making the confusion matrix use the function "confusion_matrix"
# Class in labels text: functions are small letters
# from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_true=y_test, y_pred=y_pred)
# parameters of cm: y_true: Real values, y_pred: Predicted value
```

```
# Visualizing the training set results
from matplotlib.colors import ListColormap
x_set, y_set = x_train, y_train
x1, x2 = np.meshgrid(np.arange(x_set[:,0].min(), x_set[:,0].max() + 0.01, step = 0.01), np.arange(x_set[:,1].min(), x_set[:,1].max() + 0.01, step = 0.01))
plt.contour(x1, x2, clf.predict(np.array((x_set[:,0].ravel(), x_set[:,1].ravel())).T).reshape(x1.shape), alpha=0.75, cmap=ListColormap(['red', 'green']))
plt.xlim(x1.min(), x1.max())
plt.ylabel(x2.min(), x2.max())
for i, j in enumerate(np.unique(y_set)):
    plt.scatter(x_set[y_set==j,0], x_set[y_set==j,1], c=ListColormap(['yellow', 'blue'])(i), label=j)
plt.title('Logistic Regression (Training set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary\')
plt.legend()
plt.show()
```

```
# Visualizing the testing set results
from matplotlib.colors import ListColormap
x_set, y_set = x_test, y_test
x1, x2 = np.meshgrid(np.arange(x_set[:,0].min(), x_set[:,0].max() + 0.01, step = 0.01), np.arange(x_set[:,1].min(), x_set[:,1].max() + 0.01, step = 0.01))
plt.contour(x1, x2, clf.predict(np.array((x_set[:,0].ravel(), x_set[:,1].ravel())).T).reshape(x1.shape), alpha=0.75, cmap=ListColormap(['red', 'green']))
plt.xlim(x1.min(), x1.max())
plt.ylabel(x2.min(), x2.max())
for i, j in enumerate(np.unique(y_set)):
    plt.scatter(x_set[y_set==j,0], x_set[y_set==j,1], c=ListColormap(['yellow', 'blue'])(i), label=j)
plt.title('Logistic Regression (Test set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary\')
plt.legend()
plt.show()
```