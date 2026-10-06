
Robustness is a very important property in applications where the training data is contaminated with outliers. It is not a binary property, and loss functions can be robust to a greater or smaller degree. Some of the commonly used loss functions, including the squared error, are unfortunately not particularly robust, and it is therefore important for the user to make an active and informed decision before resorting to these "default" options.

From a statistical perspective we can link the loss function to the statistical properties of the model. First, the maximum likelihood approach provides a formal connection between the loss function and the probabilistic assumptions (the noise in the data). Secondly, for loss functions that are not derived from a likelihood perspective, we can relate the so-called asymptotic minimizer of the loss function to the statistical properties. The asymptotic minimizer refers to the model that minimizes the expected loss when over the true data generating distribution. Equivalently, we can think about the asymptotic minimizer as the solution to the optimization problem (5.4) when most of training data $n \to \infty$ (hence the name "asymptotic"). If there is a unique asymptotic minimizer from which we can recover the true conditional distribution $p(y|x)$, then the loss function is said to be strictly proper. We will return to this concept briefly, in the context of binary classification.

## Loss functions for regression

In Chapter 3 we introduced the squared error loss

```
$L(y, \bar{y}) = (y - \bar{y})^2,$$
```

which is the default choice for linear regression since it simplifies the training to only solving the normal equations. The squared error loss is also used for other regression models, such as neural networks. Another common choice is the absolute error loss,

```
$L(y, \bar{y}) = |y - \bar{y}|.$
```

The absolute error is more robust to outliers than the squared error loss since it grows slower for larger errors, see Figure 5.1. In Chapter 3 we introduced the maximum likelihood motivation of the squared error by assuming the output is measured with additive noise $\epsilon$ from a Gaussian distribution, $\epsilon \sim \mathcal{N}(0,\sigma^2)$. We may consider the absolute error by assuming $\epsilon$ follows a Laplace distribution, $\epsilon \sim \mathcal{L}(0,b)$. We elaborate on the idea of deriving the loss function from the maximum likelihood objective and certain statistical assumptions below. There are also some commonly used loss functions for regression which are not natural to derive from a maximum likelihood perspective.

It is sometimes argued that the squared error is a good choice because of its quadratic shape penalizes small errors ($\epsilon < 1$) linearly. However, the Gaussian distribution assumption (at least approximately) quite often in nature. However, the quadratic shape for large errors ($\epsilon > 1$) is reason for its non-robustness, and the Huber loss has been suggested as a hybrid between the absolute and squared error loss:

Another extension to the absolute error loss is the e-insensitive loss,

```
$L(y, \bar{y}) = \begin{cases} (y - \bar{y})^2 & \text{if } |y - \bar{y}| < 1, \ |y - \bar{y}| - \frac{1}{2} & \text{otherwise.} \end{cases}$
```

```
$L(y, \bar{y}) = \begin{cases} 0 & \text{if } |y - \bar{y}| < \epsilon, \ |y - \bar{y}| - \epsilon & \text{otherwise.} \end{cases}$
```

> As you might have noticed, the argument for the loss function of $y$ and $\bar{y}$ varies with context. The reason for this is that different loss functions are most naturally expressed in terms of different quantities, for example the prediction $y$, the predicted conditional probability $p(y|x)$, the classifier margin, and

# 5 Learning parametric models

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_83_0.png)

where $\epsilon$ is a user-chosen design parameter. This loss places a tolerance of $2\epsilon$ around the observed $y$ and behaves like the absolute error loss outside this region. The robustness properties of the $\epsilon$-insensitive loss are very similar to those of the absolute error loss. The $\epsilon$-insensitive loss turns out to be useful for support vector regression in Chapter 8. We illustrate all these loss functions for regression in Figure 5.1.

## Loss functions for binary classification

An intuitive loss for binary classification is provided by the misclassification loss,

```
$L(y, \widehat{y}) = \begin{cases} 0 & \text{if } y = \widehat{y}, \ 1 & \text{if } y \neq \widehat{y}. \end{cases} \quad (5.10)$
```

Even though a small misclassification loss might be the ultimate goal in practice, this loss is rarely used when training models. As mentioned in Section 5.1, there are at least two reasons for this. First, using a different loss can result in a model that generalizes better from the training data. The second reason is understanding that the final prediction $\widehat{y}$ does not reveal all aspects of the classifier. Intuitively we may prefer to have the decision boundary control the data points, even if they are correctly classified, but push the boundary further to have some margin. To achieve this we formulate the loss, not in terms of the hard prediction $\widehat{y}$, but based on the predicted probability $g(x)$ or more smoothly than the misclassification loss compute the class prediction. This is important, as it would result in a cost function that is piecewise constant. For a numerical optimization this is a difficult objective since the gradient is zero everywhere, except where it is undefined.

For a binary classifier that predicts probabilities $p(y=1|x)$ in terms of a function $g(x)$, the cross-entropy loss, as introduced in Chapter 3, is a natural choice:

```
$L(y, g(x)) = \begin{cases} \ln g(x) & \text{if } y = 1, \\ln(1-g(x)) & \text{if } y = -1. \end{cases} \quad (5.11)$
```

This loss was derived from a maximum likelihood estimate, but unlike regression (where we had to define a distribution for $\epsilon$) there is no user choice in the cross-entropy loss, other than what model to use for $g(x)$. For a binary classification problem the model $g(x)$ provides a complete statistical description of the conditional distribution of the output given. 
While entropy is commonly used in practice, there are also other loss functions for binary classification that are useful. To define an entire family of loss functions, let us first introduce the concept of margins in binary classification. Many binary classifiers $\widehat{y}(x)$ can be constructed by thresholding some

## 5.2 Loss functions and likelihood-based models

real-valued function $f(x)$ at 0. That is, we can write the class prediction

$$$\tilde{y}(x) = \sin\{f(x)\}$$

Logistic regression, for example, can be brought into this form by simply using $f(x) = \theta^T x$, as shown in (3.39). More generally, for a nonlinear generalization of the logistic regression model where the probability of the positive class is modeled as in (5,3), the prediction (5.12) corresponds to the most likely class. Not all classifiers use a probabilistic interpretation, however, they can still be expressed in (5.12) for some underlying function $f(x)$.

The decision boundary for any classifier is given by $f(x) = 0$. The margin is a measure of certainty it follows that if $y$ and $f(x)$ have the same sign, meaning that the classification is correct, then the margin is positive. Otherwise, if an incorrect classifier $y$ and $f(x)$ have different signs the margin is negative. We can now define loss functions for classification in the term, by assigning a small loss to positive margins (correct classifications) and a large loss to negative margins (misclassifications). We can, instance, re-formulate the loss in

$$$L(y \cdot f(x)) = \begin{cases} 1 & y \cdot f(x) < 0 \\ 0 & \text{otherwise.} \end{cases}$$$

More important, that the margin-view allows us to easily come up other loss functions with possibly favorable priors. In principle, any decreasing function is a candidate loss. However, most loss functions used in practice are also convex which is useful when optimizing the training numerical

One example is the exponential loss, defined as

$$$L(y \cdot f(x)) = \exp(-y \cdot f(x))$$$$

where in linear regression. Analogously to the development of the logistic loss in Chapter 3, this is another way of writing the cross entropy (or negative log-likelihood) (5.11), assuming that the probability of the positive class is modeled after (5.3). However, from an alternative point of view we can consider (5.14) as a generic margin-based loss, without linking it to the probabilistic model. That is, we postulate a classifier according to (5.12) and learn the parameters of $f(x)$ by minimizing (5.14). This is of course equivalent to logistic regression, except for the fact that we have lost the notion of a class probability estimate $g(x)$ and only have a "hard" prediction $\tilde{y}(x)$. However, we recover the class probability estimate when we discuss the misclassification loss in terms of the logistic loss. We can also re-formulate the loss in

$$$L(y \cdot f(x)) = \begin{cases} 1 & y \cdot f(x) < 0 \\ 0 & \text{otherwise.} \end{cases}$$$

The downside of the exponential loss is that it is not robust against outliers, by to its exponential

> In the general function $f(x)$ depends on the parameters $\theta$, but in the presentation we will drop this dependence from the notation for brevity.
