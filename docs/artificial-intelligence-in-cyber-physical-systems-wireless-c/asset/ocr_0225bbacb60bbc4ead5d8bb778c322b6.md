```
nb = MultinomialNB()
nb.fit(X_train_count, y_train)
y_pred = nb.predict(X_val_count)
print('naive bayes count vectors accuracy %s' % accuracy_score(y_pred, y_val))
```

naive bayes count vectors accuracy 0.7183828610919143

```
[63] lsvm = SGDClassifier(alpha=0.001, random_state=5, max_iter=65, tol=None)
lsvm.fit(X_train_count, y_train)
y_pred = lsvm.predict(X_val_count)
print('lsvm using count vectors accuracy %s' % accuracy_score(y_pred, y_val))
```

lsvm using count vectors accuracy 0.7829993089149966

```
[64] logreg = LogisticRegression(C=1, max_iter=5000)
logreg.fit(X_train_count, y_train)
y_pred = logreg.predict(X_val_count)
print('log reg count vectors accuracy %s' % accuracy_score(y_pred, y_val))
```

log reg count vectors accuracy 0.7125086385625432

FIGURE 1.6 Accuracy of different vectors.

![](bbox=[0.12, 0.54, 0.92, 0.87])

FIGURE 1.7 SVM detected emotions.