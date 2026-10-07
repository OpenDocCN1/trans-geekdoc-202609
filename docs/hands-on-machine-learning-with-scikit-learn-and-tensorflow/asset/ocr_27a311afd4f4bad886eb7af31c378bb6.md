Scikit-Learn detects when you try to use a binary classification algorithm for a multi-class classification task, and it automatically runs OvA (except for SVM classifiers which uses OVo). Let's try this with the SGDClassifier:

```
>>> sgd_clf.fit(X_train, y_train) # using y_train, not y_train_5
>>> sgd_clf.predict(some_digit)
array([5], dtype=uint8)
```

That was easy! This code trains the SGDClassifier on the training set using original target classes from 0 to 9 (y_train), instead of the 5-versus-all target classes (y_train.5). Under the hood, Scikit-Learn actually trained 10 binary classifiers, got their decision scores for the image, and selected the class with the highest score.

To see that this is indeed, you can call the decision_function() method. Instead of returning one score per instance, it returns 10 scores, per class:

```
>>> some_digit_scores = sgd_clf.decision_function([some_digit])
>>> some_digit_scores
array([-19555.226784, -30880.9269175, -13326.66694897,
5732.5692379, -17680.6846644, 2412.53175101,
-25526.8649156, -12290.1570409, -7946.0520523,
-10631.35885499])
```

The highest score is indeed the one corresponding to class 5:

```
>>> np.argmax(some_digit_scores)
5
>>> sgd_clf.classes_
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9], dtype=uint8)
>>> sgd_clf.classes_[5]
5
```

When a classifier is trained, it stores the list of target classes in its classes_ attribute, ordered by the index of each class in classes_. In this case, array_ conveniently matches the class itself (e.g. the index of 5 is class 5), but in general you won't be so lucky.

![](bbox=[0.173, 0.626, 0.259, 0.706])

If you want to force Scikit-Learn to use one-vs-one or one-vs-all, you can use the OneVsOneClassifier or OneVsRestClassifier. For example, this code creates a multi-class classifier using the OvO strategy, based on a SGDClassifier:

Multiclass Classification | 103

WOW! eBook
www.wowobook.org