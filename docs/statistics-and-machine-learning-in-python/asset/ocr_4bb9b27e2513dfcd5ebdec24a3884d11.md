\mathcal{S}(f) = \frac{1}{K} \sum_{k}^{K} \mathcal{S}_{k}(f).

\mathcal{S}(f) = \frac{1}{K} \sum_{k}^{K} \frac{1}{N_{k}} \sum_{i \in k} \mathcal{L}\left( y_{i}, f(\boldsymbol{x}_{-k(i)}, \boldsymbol{y}_{-k(i)}) \right).

these two measures (an average of average vs. a global average) are generaly similar. They may differ slightly is folds are of different sizes.

This validation scheme is known as the K-Fold CV. Typical choices of K are 5 or 10, [Kohavi 1995]. The extreme case where K = N is known as leave-one-out cross-validation, LOO-CV.

# 15.2.1 CV for regression

Usually the error function \mathcal{L}() is the r-squared score. However other function could be used.

```
%matplotlib inline
import warnings
warnings.filterwarnings(action='once')
```

```
import numpy as np
from sklearn import datasets
import sklearn.linear_model as lm
import sklearn.metrics as metrics
from sklearn.model_selection import KFold

X, y = datasets.make_regression(n_samples=100, n_features=100,
                                n_informative=10, random_state=42)
model = lm.Ridge(alpha=10)

cv = KFold(n_splits=5, random_state=42)
y_test_pred = np.zeros(len(y))
y_train_pred = np.zeros(len(y))

for train, test in cv.split(X):
    X_train, X_test, y_train, y_test = X[train, :], X[test, :], y[train], y[test]
    model.fit(X_train, y_train)
    y_test_pred[test] = model.predict(X_test)
    y_train_pred[train] = model.predict(X_train)

print("Train r2:%.2f" % metrics.r2_score(y, y_train_pred))
print("Test  r2:%.2f" % metrics.r2_score(y, y_test_pred))
```

/home/edouard/anaconda3/lib/python3.6/site-packages/_pytest/fixtures.py:844:
DeprecationWarning: The convert argument is deprecated in favor of converter.
It will be removed after 2019/01.
    params = attr.ib(convert=attr.converters.optional(tuple))

```
Train r2:0.99
Test  r2:0.72
```

Scikit-learn provides user-friendly function to perform CV: