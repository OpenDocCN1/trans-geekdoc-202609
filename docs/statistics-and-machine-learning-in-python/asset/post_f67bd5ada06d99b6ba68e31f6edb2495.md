
![](img/c2ad4b400bf63af9804b2d44510f76a6_196_0.png)

Fig. 13.5: Linear large margin classifiers

- 2. If 1 > y_i(w·x_i) ≥ 0 then the point lies inside the margin and on the correct side of the decision boundary. In this case 0 < ξ_i ≤ 1. The constraint is active for this point. It does contribute to the prediction as a support vector.
- 3. If 0 < y_i(w·x_i) then the point is on the wrong side of the decision boundary (misclassification). In this case ξ_i > 1. The constraint is active for this point. It does contribute to the prediction as a support vector.

This loss is called the hinge loss, defined as:

max(0, 1 − y_i (w·x_i))

So linear SVM is close to Ridge logistic regression, using the hinge loss instead of the logistic loss. Both will provide very similar predictions.

```python
from sklearn import svm

svmlin = svm.LinearSVC()
# Remark: by default LinearSVC uses squared_hinge as loss
svmlin.fit(X, y)
y_pred_svmlin = svmlin.predict(X)

errors = y_pred_svmlin != y
print("Nb errors=%i, error rate=%.2f" % (errors.sum(), errors.sum() / len(y_pred_svmlin)))
print(svmlin.coef_)
```

```
Nb errors=26, error rate=0.26
[[-0.05604866  0.31187658  0.00275339 -0.05153703  0.09938239  0.17724479
   0.06520118  0.08921076  0.35336289  0.00599675 -0.06201396 -0.00742017
  -0.02159905  0.18271488 -0.02164397 -0.04061358  0.0720389   0.13085078
   0.23720691  0.00826935]]
```

```
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/svm/base.py:931:
→ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
"the number of iterations.", ConvergenceWarning)
```

## 13.9 Lasso linear Support Vector Machine (L1-regularization)

Linear SVM for classification (also called SVM-C or SVC) with l1-regularization

min  F_{Lasso linear SVM}(w) = λ ||w||_1 + C ∑_i^N ξ_i
with  ∀i               y_i(w·x_i) ≥ 1 - ξ_i

```python
from sklearn import svm

svmlinl1 = svm.LinearSVC(penalty='l1', dual=False)
# Remark: by default LinearSVC uses squared_hinge as loss

svmlinl1.fit(X, y)
y_pred_svmlinl1 = svmlinl1.predict(X)

errors = y_pred_svmlinl1 != y
print("Nb errors=%i, error rate=%.2f" % (errors.sum(), errors.sum() / len(y_pred_svmlinl1)))
print(svmlinl1.coef_)
```

```
Nb errors=26, error rate=0.26
[[-0.05334026  0.29934473  0.         -0.03541313  0.09261404  0.16763294
   0.05808033  0.07587505  0.34065177  0.         -0.05558916 -0.00194123
  -0.01312461  0.1686629  -0.01450446 -0.02500537  0.06074148  0.11738861
   0.22485536  0.00473342]]
```

## 13.10 Exercise

Compare predictions of Logistic regression (LR) and their SVM counterparts, ie.: L2 LR vs L2 SVM and L1 LR vs L1 SVM

- Compute the correlation between pairs of weights vectors.
- Compare the predictions of two classifiers using their decision function:
  - Give the equation of the decision function for a linear classifier, assuming that their is no intercept.
  - Compute the correlation decision function.
  - Plot the pairwise decision function of the classifiers.
- Conclude on the differences between Linear SVM and logistic regression.

## 13.11 Elastic-net classification (L2-L1-regularization)

The objective function to be minimized is now the combination of the logistic loss log L(w) or the hinge loss with combination of L1 and L2 penalties. In the two-class case, using the 0/1 coding we obtain:

min Logistic enet(w) = log L(w) + α ( ρ ||w||_1 + (1 - ρ) ||w||_2^2 )      (13.16)
  min Hinge enet(w) = Hinge loss(w) + α ( ρ ||w||_1 + (1 - ρ) ||w||_2^2 )      (13.17)

```python
from sklearn import datasets
from sklearn import linear_model as lm
import matplotlib.pyplot as plt

X, y = datasets.make_classification(n_samples=100,
                                    n_features=20,
                                    n_informative=3,
                                    n_redundant=0,
                                    n_repeated=0,
                                    n_classes=2,
                                    random_state=0,
                                    shuffle=False)

enetloglike = lm.SGDClassifier(loss="log", penalty="elasticnet",
                               alpha=0.0001, l1_ratio=0.15, class_weight='balanced')
enetloglike.fit(X, y)

enethinge = lm.SGDClassifier(loss="hinge", penalty="elasticnet",
                             alpha=0.0001, l1_ratio=0.15, class_weight='balanced')
enethinge.fit(X, y)
```

```
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/linear_model/stochastic_gradient.py:166: FutureWarning: max_iter and tol parameters have been added in SGDClassifier in 0.19. If both are left unset, they default to max_iter=5 and tol=None. If tol is not None, max_iter defaults to max_iter=1000. From 0.21, default max_iter will be 1000, and default tol will be 1e-3. FutureWarning)
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/linear_model/stochastic_gradient.py:166: FutureWarning: max_iter and tol parameters have been added in SGDClassifier in 0.19. If both are left unset, they default to max_iter=5 and tol=None. If tol is not None, max_iter defaults to max_iter=1000. From 0.21, default max_iter will be 1000, and default tol will be 1e-3. FutureWarning)
```

```
SGDClassifier(alpha=0.0001, average=False, class_weight='balanced',
               early_stopping=False, epsilon=0.1, eta0=0.0, fit_intercept=True,
               l1_ratio=0.15, learning_rate='optimal', loss='hinge', max_iter=None,
               n_iter=None, n_iter_no_change=5, n_jobs=None, penalty='elasticnet',
               power_t=0.5, random_state=None, shuffle=True, tol=None,
               validation_fraction=0.1, verbose=0, warm_start=False)
```

### 13.11.1 Exercise

Compare predictions of Elastic-net Logistic regression (LR) and Hinge-loss Elastic-net

- Compute the correlation between pairs of weights vectors.
- Compare the predictions of two classifiers using their decision function:
  - Compute the correlation decision function.
  - Plot the pairwise decision function of the classifiers.
- Conclude on the differences between the two losses.

## 13.12 Metrics of classification performance evaluation

### 13.12.1 Metrics for binary classification

source: https://en.wikipedia.org/wiki/Sensitivity_and_specificity

Imagine a study evaluating a new test that screens people for a disease. Each person taking the test either has or does not have the disease. The test outcome can be positive (classifying the person as having the disease) or negative (classifying the person as not having the disease). The test results for each subject may or may not match the subject’s actual status. In that setting:

- True positive (TP): Sick people correctly identified as sick
- False positive (FP): Healthy people incorrectly identified as sick
- True negative (TN): Healthy people correctly identified as healthy
- False negative (FN): Sick people incorrectly identified as healthy
- Accuracy (ACC):
  - ACC = (TP + TN) / (TP + FP + FN + TN)
- Sensitivity (SEN) or recall of the positive class or true positive rate (TPR) or hit rate:
  - SEN = TP / P = TP / (TP+FN)
- Specificity (SPC) or recall of the negative class or true negative rate:
  - SPC = TN / N = TN / (TN+FP)
- Precision or positive predictive value (PPV):
  - PPV = TP / (TP + FP)
- Balanced accuracy (bACC) is a useful performance measure which avoids inflated performance estimates on imbalanced datasets (Brodersen, et al. (2010). “The balanced accuracy and its posterior distribution”). It is defined as the arithmetic mean of sensitivity and specificity, or the average accuracy obtained on either class:
  - bACC = 1/2 * (SEN + SPC)
- F1 Score (or F-score) which is a weighted average of precision and recall are useful to deal with imbalanced datasets

The four outcomes can be formulated in a 2×2 contingency table or confusion matrix https://en.wikipedia.org/wiki/Sensitivity_and_specificity

For more precision see: http://scikit-learn.org/stable/modules/model_evaluation.html

```python
from sklearn import metrics
y_pred = [0, 1, 0, 0]
y_true = [0, 1, 0, 1]

metrics.accuracy_score(y_true, y_pred)

# The overall precision and recall
metrics.precision_score(y_true, y_pred)
metrics.recall_score(y_true, y_pred)

# Recalls on individual classes: SEN & SPC
```
