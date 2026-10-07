Let's use Softmax Regression to classify the iris flowers into all three classes. ScikitLearn's LogisticRegression uses one-versus-all by default when you train it on more than two classes, but you can set the multi_class hyperparameter to "multinomial" to switch to Softmax instead. You must also specify a solver that supports Softmax Regression, such as the "lbfgs" solver (see Scikit-Learn's documentation for details). It also applies l2 regularization by default, which you can control using the hyperparameter C.

```
X = iris['data'][:, [2, 3]] # petal length, petal width
y = iris['target']
```

```
softmax_reg = LogisticRegression(multi_class="multinomial",solver="lbfgs", C=10)
softmax_reg.fit(X, y)
```

So next time you find an iris with 5 cm length and 2 cm width, you can ask your model to tell you what type of iris it is, and it will answer Iris-Virginica (class 2) with 94.2% probability (Iris-Versicolor with 5.8% probability):

```
>>> softmax_reg.predict([[5, 2]])
array([[2]])
>>> softmax_reg.predict_prob([[5, 2]])
array([[6.3801486e-07, 5.7492995e-02, 9.24506362e-01]])
```

**Figure 4-25** shows the decision boundaries, represented by the background colors. Notice that the decision boundaries between any two classes are linear. The figure also shows the probabilities for the Iris-Versicolor class, represented by the curved lines (e.g., the line labeled with 0.450 represents the 45% probability boundary). Notice that the model can predict a class that has an estimated probability below 50%. For example, at the point where all decision boundaries meet, all classes have an equal estimated probability of 33%.

![](bbox=[0.148, 0.592, 0.851, 0.809])

Figure 4-25. Softmax Regression decision boundaries