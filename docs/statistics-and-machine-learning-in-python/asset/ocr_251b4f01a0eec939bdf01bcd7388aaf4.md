min Logistic ridge(w) = log L(w) + λ ||w||²  (13.11)
= Σ_{i}^{N} { y_i w^T x_i − log(1 + exp^{w^T x_i}) } + λ ||w||²  (13.12)
(13.13)

```
# Dataset
# Build a classification task using 3 informative features
from sklearn import datasets

X, y = datasets.make_classification(n_samples=100,
                                    n_features=20,
                                    n_informative=3,
                                    n_redundant=0,
                                    n_repeated=0,
                                    n_classes=2,
                                    random_state=0,
                                    shuffle=False)
```

```
from sklearn import linear_model
lr = linear_model.LogisticRegression(C=1)
# This class implements regularized logistic regression. C is the Inverse of regularization strength.
# Large value => no regularization.

lr.fit(X, y)
y_pred_lr = lr.predict(X)

errors = y_pred_lr != y
print("Nb errors=%i, error rate=%.2f" % (errors.sum(), errors.sum() / len(y)))
print(lr.coef_)
```

```
Nb errors=26, error rate=0.26
[[-0.12061092  0.7357655  -0.01842318 -0.10835785  0.25328562  0.4221318
   0.15152184  0.16522461  0.84404799  0.01962765 -0.15995078 -0.01925974
  -0.02807379  0.42939869 -0.06368702 -0.07922044  0.15529371  0.29963205
   0.54633137  0.03866807]]
```

```
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/linear_model/logistic.py:433:
FutureWarning: Default solver will be changed to 'lbfgs' in 0.22. Specify a solver to silence this warning.
FutureWarning)
```

# 13.7 Lasso logistic regression (L1-regularization)

The objective function to be minimized is now the combination of the logistic loss log L(w) with a penalty of the L1 norm of the weights vector. In the two-class case, using the 0/1 coding we obtain: