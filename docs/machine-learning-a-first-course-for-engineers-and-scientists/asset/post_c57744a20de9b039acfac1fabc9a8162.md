
# Learning parametric models

growth for negative margins, compared to, for example, the linear asymptotic growth of the logistic loss.³3
We also have the hinge loss, which we use for support vector classification in Chapter 8,

```
$L(y \cdot f(x)) = \begin{cases} 1 - y \cdot f(x) & \text{for } y \cdot f(x) \le 1, \ 0 & \text{otherwise.} \end{cases}$ (5.17)
```

As we see in Chapter 8, the hinge loss has an attractive so-supported-vector property. However, a downside of the hinge loss is that it is not a *strictly* proper function, which means that it is not possible to interpret the learnt classification probabilistically when using this loss (we elaborate on this below). As a remedy, one might instead consider the **squared hinge loss**

```
$L(y \cdot f(x)) = \begin{cases} (1 - y \cdot f(x))^2 & \text{for } y \cdot f(x) \le 1, \ 0 & \text{otherwise.} \end{cases}$ (5.18)
```

which on the other hand is less robust than the hinge loss (instead of linear growth). A more aggressive alternative is the *Huberized squared hinge loss*

```
$L(y \cdot f(x)) = \begin{cases} -4y \cdot f(x) & \text{for } y \cdot f(x) \le -1, \ (1 - y \cdot f(x))^2 & \text{for } -1 \le y \cdot f(x) \le 1, \ \text{(squared hinge loss)} \ 0 & \text{otherwise.} \end{cases}$ (5.19)
```

whose name refers to its similarities to the Huber loss for regression, where the quadratic function is replaced with a linear function for margins < -1. The three functions presented above are all particularly interesting for support vector classification, to the fact that they are all exactly 0 for margins > 1.

We summarize the cascade of losses for binary classification in Figure 5.2, which illustrates all these losses as a function of the margin.

When learning for imbalanced or asymmetric problems, it is possible to modify the loss to account for the imbalance. For example, to reflect that predicting y = 1 is correct a "C times more severe than "not predicting y = -1", the misclassification can be modified by

```
$L(y, \hat{y}) = \begin{cases} 0 & \text{if } \hat{y} = y, \ 1 & \text{if } y \neq \hat{y} \text{ and } y = -1, \ C & \text{if } y \neq \hat{y} \text{ and } y = 1. \end{cases}$ (5.20)
```

The other losses can be modified in a similar fashion. For this example, simply duplicating all data point C in the training data, instead of modifying the loss

We have made some claims about robustness. Let us motivate them using Figure 5.2. A characterization of an outlier is a data point on the wrong side of and far away from the decision boundary. The robustness of a loss function is tightly connected to the shape of the loss function for large negative margins. The steeper the heavier penalty of large negative margins, the more sensitive it is to outliers. We can therefore tell that the exponential loss is more sensitive to outliers, due to its exponential growth, whereas even more robust is the Huberized squared hinge loss, the hinge loss and the logistic loss which have any asymmetric behavior which is. The most robust is the misclassification, but as we discussed already, that loss has many disadvantages.

For $y(x) < 0$ it holds that $\ln(1 + \exp(-y \cdot f(x))) = -y \cdot f(x)$.

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_86_0.png)

Figure 5.2: Comparison of some common loss functions for classification, plotted as a function of the margin.

## Multiclass classification

So far we have only discussed the binary classification problem with $M = 2$. The cross-entropy (equivalently, negative log-likelihood) is straightforward to generalize to the multiclass problem, that is $M > 2$, as we did in Chapter 3 for logistic regression. This is a useful property of the likelihood-based loss, as it allows us to treat both binary and multiclass classification in the coherent framework.

Generalizing the other loss functions discussed above requires a generalization of the margin to the multiclass problem. This is possible but we do not elaborate on it in this book. Instead we mean a pragmatic approach which is to reformulate the margin as several binary problems. This reformulation can be done using a one-versus-all or one-versus-one scheme.

The one-versus-rest (or one-versus-all or binary relevance) idea is to train $M$ binary classifiers. Each classifier in this scheme is trained for predicting one class against all the classes. To make a prediction for a test point, all $M$ classifiers are used, and the class, which is predicted with the largest margin is then the predicted class. This approach is a pragmatic solution, which may turn out to work for some problems.

The one-versus-one idea is to train classifiers for each pair of classes. If there are $M$ classes in total, there are $\frac{1}{2}M(M-1)$ pairs. To make a prediction each classifier predicts of its two classes, and the class which obtains most "votes" is chosen as the final prediction. The predicted margins can be used to break a tie if it happens. Compared to one-versus-rest, the one-versus-one approach has the disadvantage of involving $\frac{1}{2}M(M-1)$ classifiers, instead of $M$. On the other hand each of these classifiers is trained on smaller datasets (only the data points that belong to either of the classes) compared to one-versus-rest which uses the entire training dataset for all $M$ classes

# 5 Learning parametric models

### Likelihood-based models and the maximum likelihood approach

The maximum likelihood approach is a generic way of constructing a loss function based on a statistical model of the observed data. In general, maximizing the data likelihood is equivalent to minimizing a cost function based on the negative-log likelihood,

```
J(\theta) = -\frac{1}{n} \sum_{i=1}^{n} \ln p(y_i|\theta);
```

Hence, in all cases where we have a probabilistic model of the conditional distribution $p(y|x)$ the negative-log likelihood is a plausible function. For classification problems this takes a particularly simple form since $p(y|x)$ corresponds to probability over the $M$ classes. Hence, the likelihood becomes an integral part of the model and this approach lends itself naturally to training by maximum likelihood.

In generalized models (see Section 3.4) the likelihood is parameterized in a very particular way, but when working with nonparametric models this is not strictly necessary. A more direct approach to (nonlinear) likelihood-based parametric modeling is to

> model the conditional distribution $p(y|x)$ as a function parameterized by $\theta$

More specifically, if we have assumed a certain form for the likelihood (like a Gaussian, a Poisson, or some other distribution) its shape will be controlled by some parameters (such as the mean and the variance of a Gaussian, or the rate of a Poisson distribution). The idea is then to construct a parametric model $f(x)$, such that the output of this is a vector of parameters controlling the shape of the distribution $p(y|x)$.

As an example, if we are working with real-valued outputs and want to use a Gaussian likelihood, similarly to the regression model (5.2), however, the nature of data is such that the

> ^4This can be verified from the Laplace probability density function, which is an exponential of the negative absolute deviation from the mean.
