two principal components, the remaining variance is only 2.2%, hence visually the plot after removing two components looks like a straight line. In fact, when we check with the plots above, not only we see the points are crumbled, but the range in the x- and y-axes are also smaller as we removed the components. In terms of machine learning, we can consider using only one single feature for classification in this dataset, namely the first principal component. We should expect to achieve no less than 90% of the original accuracy as using the full set of features:

```
...
from sklearn.model_selection import train_test_split
from sklearn.metrics import f1_score
from collections import Counter
from sklearn.svm import SVC

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.33)
clf = SVC(kernel="linear", gamma='auto').fit(X_train, y_train)
print("Using all features, accuracy: ", clf.score(X_test, y_test))
print("Using all features, F1: ", f1_score(y_test, clf.predict(X_test), average="macro"))

mean = X_train.mean(axis=0)
X_train2 = X_train - mean
X_train2 = (X_train2 @ pca.components_[0]).reshape(-1,1)
clf = SVC(kernel="linear", gamma='auto').fit(X_train2, y_train)
X_test2 = X_test - mean
X_test2 = (X_test2 @ pca.components_[0]).reshape(-1,1)
print("Using PC1, accuracy: ", clf.score(X_test2, y_test))
print("Using PC1, F1: ", f1_score(y_test, clf.predict(X_test2), average="macro"))
```

Using all features, accuracy: 1.0
Using all features, F1: 1.0
Using PC1, accuracy: 0.96
Using PC1, F1: 0.9645191409897292

The other use of the explained variance is on compression. Given the explained variance of the first principal component is large, if we need to store the dataset, we can store only the projected values on the first principal axis (X · v), as well as the vector v of the principal axis. Then we can approximately reproduce the original dataset by multiplying them:

X ≈ (X · v) · vᵀ