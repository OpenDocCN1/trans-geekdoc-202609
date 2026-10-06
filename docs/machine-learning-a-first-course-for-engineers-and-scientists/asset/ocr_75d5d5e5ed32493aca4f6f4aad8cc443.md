# 5 Learning parametric models

![](bbox=[0.278, 0.076, 0.722, 0.26])

where $\epsilon$ is a user-chosen design parameter. This loss places a tolerance of $2\epsilon$ around the observed $y$ and behaves like the absolute error loss outside this region. The robustness properties of the $\epsilon$-insensitive loss are very similar to those of the absolute error loss. The $\epsilon$-insensitive loss turns out to be useful for support vector regression in Chapter 8. We illustrate all these loss functions for regression in Figure 5.1.

# Loss functions for binary classification

An intuitive loss for binary classification is provided by the missclassification loss,

```
$L(y, \widehat{y}) = \begin{cases} 0 & \text{if } y = \widehat{y}, \ 1 & \text{if } y \neq \widehat{y}. \end{cases} \quad (5.10)$
```

Even though a small missclassification loss might be the ultimate goal in practice, this loss is rarely used when training models. As mentioned in Section 5.1, there are at least two reasons for this. First, using a different loss can result in a model that generalizes better from the training data. The second reason is understanding that the final prediction $\widehat{y}$ does not reveal all aspects of the classifier. Intuitively we may prefer to have the decision boundary control the data points, even if they are correctly classified, but push the boundary further to have some margin. To achieve this we formulate the loss, not in terms of the hard prediction $\widehat{y}$, but based on the predicted probability $g(x)$ or more smoothly than the missclassification loss compute the class prediction. This is important, as it would result in a cost function that is piecewise constant. For a numerical optimization this is a difficult objective since the gradient is zero everywhere, except where it is undefined.

For a binary classifier that predicts probabilities $p(y=1|x)$ in terms of a function $g(x)$, the cross-entropy loss, as introduced in Chapter 3, is a natural choice:

```
$L(y, g(x)) = \begin{cases} \ln g(x) & \text{if } y = 1, \\ln(1-g(x)) & \text{if } y = -1. \end{cases} \quad (5.11)$
```

This loss was derived from a maximum likelihood estimate, but unlike regression (where we had to define a distribution for $\epsilon$) there is no user choice in the cross-entropy loss, other than what model to use for $g(x)$. For a binary classification problem the model $g(x)$ provides a complete statistical description of the conditional distribution of the output given.
While entropy is commonly used in practice, there are also other loss functions for binary classification that are useful. To define an entire family of loss functions, let us first introduce the concept of margins in binary classification. Many binary classifiers $\widehat{y}(x)$ can be constructed by thresholding some

Draft (April 30, 2021) of Machine Learning - A First Course for Engineers and Scientists. http://mlbook.org
 Andrew Lin, Nicholas Wahlund, Frederik Lin, and Thomas B. Schoen. 2021.