![](bbox=[0.147, 0.085, 0.852, 0.315])

Figure 5-10. SVM Regression

Adding more training instances within the margin does not affect the model's predictions; thus, the model is said to be *ε-insensitive*.

You can use Scikit-Learn's LinearSVR class to perform linear SVM Regression. The following code produces the model represented on the left of Figure 5-10 (the training data should be scaled and centered first):

```
```from sklearn.svm import LinearSVR```
```

```
```svm_reg = LinearSVR(epsilon=1.5)
v_reg.fit(X, y)```
```

To tackle nonlinear regression tasks, you can use a kernelized SVM model. For example, Figure 5-11 shows SVM on a random quadratic training set, using a $2^{nd}$-degree polynomial kernel. There is little regularization on the left plot (i.e., a large C value), and much more regularization on the right plot (i.e., a small C value).

![](bbox=[0.147, 0.643, 0.852, 0.863])

Figure 5-11. SVM regression using a $2^{nd}$-degree polynomial kernel

SVM Regression | 165

WOW! eBook
www.wowebookbook.org