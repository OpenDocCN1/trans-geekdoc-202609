```
from sklearn.model_selection import cross_val_score

scores = cross_val_score(estimator=model, X=X, y=y, cv=5)
print("Test  r2:%.2f" % scores.mean())

# provide a cv
cv = KFold(n_splits=5, random_state=42)
scores = cross_val_score(estimator=model, X=X, y=y, cv=cv)
print("Test  r2:%.2f" % scores.mean())
```

Test  r2:0.73
Test  r2:0.73

# 15.2.2 CV for classification

With classification problems it is essential to sample folds where each set contains approximately the same percentage of samples of each target class as the complete set. This is called stratification. In this case, we will use StratifiedKFold with is a variation of k-fold which returns stratified folds.

Usually the error function L() are, at least, the sensitivity and the specificity. However other function could be used.

```
import numpy as np
from sklearn import datasets
import sklearn.linear_model as lm
import sklearn.metrics as metrics
from sklearn.model_selection import StratifiedKFold

X, y = datasets.make_classification(n_samples=100, n_features=100,
                                    n_informative=10, random_state=42)

model = lm.LogisticRegression(C=1, solver='lbfgs')

cv = StratifiedKFold(n_splits=5)
y_test_pred = np.zeros(len(y))
y_train_pred = np.zeros(len(y))

for train, test in cv.split(X, y):
    X_train, X_test, y_train, y_test = X[train, :], X[test, :], y[train], y[test]
    model.fit(X_train, y_train)
    y_test_pred[test] = model.predict(X_test)
    y_train_pred[train] = model.predict(X_train)

recall_test  = metrics.recall_score(y, y_test_pred, average=None)
recall_train = metrics.recall_score(y, y_train_pred, average=None)
acc_test = metrics.accuracy_score(y, y_test_pred)

print("Train  SPC:%.2f; SEN:%.2f" % tuple(recall_train))
print("Test   SPC:%.2f; SEN:%.2f" % tuple(recall_test))
print("Test   ACC:%.2f" % acc_test)
```