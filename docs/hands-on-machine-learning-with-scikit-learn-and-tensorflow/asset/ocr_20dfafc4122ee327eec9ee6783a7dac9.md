```
>>> y_train_knn_pred = cross_val_predict(knn_clf, X_train, y_multilabel, cv=3)
>>> f1_score(y_multilabel, y_train_knn_pred, average="macro")
0.976410265506065
```

This assumes that all labels are equally important, which may not be the case. In particular, if you have many pictures of Alice than Bob or Charlie, you may want to give more weight to the classifier's score of Alice. One simple option is to give each label a weight equal to its support (i.e., the number of instances with target label). To do this, simply set average="weighted" in the preceding code.⁴

# Multioutput Classification

The last type of classification task we are going to discuss here is called multioutputmulticlass classification (or simply multiloutput classification). It is a generalization of multilabel classification where each label can be multiclass (i.e., it can have more than two possible values).

To illustrate this, let's build a system that removes noise from images. It will take as input a noisy digit image, and it will (hopefully) output a clean digit image, represented as an array of pixel intensities, just like the MNIST images. Notice that the classifier's output is multilabel (one label per pixel) and each label can have multiple values (pixel intensity ranges from 0 to 255). It is then an example of a multioutput classification system.

> The line between classification and regression is sometimes blurry, such as in this example. Arguably, predicting pixel intensity is more akin to regression than classification. Moreover, multioutput systems are not limited to classification tasks; you could even have a system that outputs multiple labels per instance, including both class and label values.

Let us start by creating the training and test sets by adding noise to these pixel images using NumPy’s randInt() function. The target images will be the original images:

```
noise = np.random.randint(0, 100, (len(X_train), 784))
X_train_mod = X_train + noise
noise = np.random.randint(0, 100, (len(X_test), 784))
X_test_mod = X_test + noise
y_train_mod = X_train
y_test_mod = X_test
```

⁴ Scikit-Learn offers a few other averaging options and multilabel classifier metrics; see the documentation for more details.