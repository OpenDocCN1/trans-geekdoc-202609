# 3 Basic parametric models and a statistical perspective on learning

![](bbox=[0.137, 0.07, 0.862, 0.303])

**Figure 3.5:** In binary classification (y = -1 or 1) logistic regression predicts $g(x_*)$ ($x$ is two-dimensional here), which is an attempt to determine... This implicitly gives a prediction for $p(y=-1|x_*)$ as $1-g(x_*)$. To turn these probabilities into actual class predictions $\hat{y}(x_*)$ (which is either -1 or 1), the class which is modeled to have the highest probability can be taken as the prediction, as in Equation (3.36). The point($x$) where the prediction changes from one class to another is the decision boundary (gray plane).

than falsely predict the positive class (by mistake predict a healthy patient as sick). For such a problem, minimizing the misclassification rate might not lead to the desired performance. Furthermore, the medical diagnosis problem could be imbalanced if the disorder is very rare, meaning that the vast majority of the data points (false) implicitly value accurate predictions of the negative class higher than accurate predictions of the positive class. simply because considering the misclassification rate in such a situation simply because the negative class is more common in the data. We will discuss how we can evaluate such situations systematically in Section 4.5. In the however, the decision threshold $r$ is a choice that the user has to make.

The decision boundary for binary classification can be computed by solving the equation

```
g(x*) = 1 - g(x). (3.37)
```

The solutions to this equation are points in the input space for which two classes are predicted to be equally probable. These points lie on the decision boundary. For binary logistic regression, this

means

```
e^(0x*) / (1 + e^(0x*)) ⇔ e^(0x*) = 1 ⇔ θTx = 0. (3.38)
```

The equation $	heta^Tx = 0$ is a (linear) hyperplane. Hence, the decision boundaries in logistic regression always has the shape of a (linear) hyperplane.

From the derivation above it can be noted that the sign of the expression $	heta^Tx$ determines if the positive or the negative class, we can compactly write (3.36), with the threshold $r=0.5$, as

```
ŷ(x*) = sign(θT x*). (3.39)
```

In general we distinguish between different types of classifiers by the shape of their decision boundaries.

+   A classifier whose decision boundaries are linear hyperplanes is a linear classifier.

All other classifiers are nonlinear classifiers. Logistic regression is an example of a linear classifier, whereas k-NN and decision trees are nonlinear classifiers. Note that the term "linear" is used in a different sense

Draft (April 30, 2021) of Machine Learning - A First Course for Engineers and Scientists. http://mlbook.org

* Andreas Lindholm, Nikolai Wahlström, Fredrik Lindsten, and Thomas B. Schön. 2021.

3