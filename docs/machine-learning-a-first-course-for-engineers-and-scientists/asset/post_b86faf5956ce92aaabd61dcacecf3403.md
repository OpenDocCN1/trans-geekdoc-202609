
# Ensemble Methods: Bagging and boosting

a look at the AdaBoost algorithm which is one approach for filling in these missing details. AdaBoost was the first successful implementation of the boosting idea, so it is interesting in its own right, but also because it is simple enough to allow for closed form derivations. However, there are also more modern approaches to boosting, so after discussing AdaBoost we will introduce the more general framework of gradient boosting.

Throughout this section we will restrict our attention to binary classification, but boosting is applicable also for multiclass classification and regression problems.

# AdaBoost

What we have discussed so far is a general idea, but there are still a few technical design choices. Let us now derive an AdaBoost (Adaptive Boosting) algorithm for binary classification. AdaBoost was the first successful practical implementation of the boosting idea and lead the way for its popularity.

As outlined in Example 7.5 boosting attempt to construct a sequence of $B$ binary classifiers $\hat{y}^{(1)}(x), \hat{y}^{(2)}(x), \dots, \hat{y}^{(B)}(x)$. We will in this procedure consider the final 'hard' $\hat{y}(x)$ from the base models, and not their predicted class $g(x)$. Any classification model can be used as a base classifier—simple classification trees are common in practice. The individual predictions of the B ensemble are then combined into a final prediction. Unlike bagging, all ensemble members are not treated equally. Instead, we assign some positive coefficients $a^{(b)}_{b=1}^B$ and construct the boosted classifier using a weighted majority vote:

```
\hat{y}_{boost}^{(B)}(x) = \text{sign} \left( \sum_{b=1}^{B} a^{(b)} \hat{y}^{(b)}(x) \right).
```

Each member votes either -1 or +1, and thus the boosted classifier is +1 if the weighted sum of the individual votes is positive and -1 if it is negative. The coefficient $a^{(b)}$ can be thought of as a measure of confidence in the predictions by the $b$th ensemble member.

The construction of the AdaBoost classifier in (7.4) follows the general form of a binary classifier by thresholding a real-valued function $f(x)$ at zero, where in this case the function is given by the weighted sum of predictions made by all the members. In AdaBoost, the ensemble members and their coefficients $a^{(b)}$ are trained greedily by minimizing the exponential loss of the boosted classifier at each iteration. Recall from (5.16) that the exponential loss is given by:

```
L(y \cdot f(x)) = \exp(-y \cdot f(x)).
```

$y \cdot f(x)$ is the *margin* of the classifier. The ensemble members are added one at a time, and when member $b$ is added, this is to minimize the exponential loss (7.5) of the entire ensemble so far (that is, the boosted classifier consisting of $b$ members). The main reason for choosing the exponential loss, not one of the other loss functions discussed in Section 5.2, is that it results in closed form expressions (like the squared error loss in linear regression), as we will see when deriving the AdaBoost procedure.

Let us derive the boosted classifier after $b$ iterations $f^{(b)}(x) = \text{sign}(f^{(b)}(x))$ where we can express $f^{(b)}(x)$ iteratively:

```
f^{(b)}(x) = f^{(b-1)}(x) + a^{(b)} \hat{y}^{(b)}(x),
```

initialized with $f^{(0)}(x) = 0$. The ensemble members (and well the coefficients $a^{(b)}_{b=1}$) are constructed sequentially, meaning that at iteration $b$ of the function $f^{(b-1)}(x)$ is known and fixed. This is what this “construction” does. Consequently, what remains to be learned at iteration $b$ is ensemble member $\tilde{Y}^{(b)}(\mathbf{x})$ and its coefficient $\alpha^{(b)}$. We do this by minimizing the exponential loss of the training data:

```
$$\alpha^{(b)}, \tilde{Y}^{(b)} = \text{arg min}_{(\alpha, \tilde{y})} \sum_{i=1}^{n} L(y_i \cdot f^{(b-1)}(\mathbf{x})) \quad (7.7a)
$ = \text{arg min}_{(\alpha, \tilde{y})} \sum_{i=1}^{n} \exp(-y_i \cdot (f^{(b-1)}(\mathbf{x}) + \alpha \tilde{y}(\mathbf{x}))) \quad (7.7b)
$ = \text{arg min}_{(\alpha, \tilde{y})} \sum_{i=1}^{n} \exp(-y_i \cdot f^{(b-1)}(\mathbf{x}) - \alpha \tilde{y}(\mathbf{x}))) \quad (7.7c)
```

where the first equality we used the definition of the exponential loss (7.5) and the sequential structure of the boosted classifier (7.6). The last equality by rewriting the convenience of the exponential loss appears, namely by the fact that $\exp(a+b) = \exp(a)\exp(b)$. This allows us to define the quantities:

```
$W_i^{\text{def}} = \exp(-y_i \cdot f^{(b-1)}(\mathbf{x})),\quad (7.8)
```

which can be interpreted as weights for the individual data points in the dataset. Note that the weights $w_i^{(b)}$ are independent of $\tilde{y}$ and $\alpha$. That is, when learning $\tilde{y}^{(b)}(\mathbf{x})$ and its coefficient $\alpha^{(b)}$ by solving (7.7c) we can regard with respect to $w_i^{(b)}$ as constants. To solve (7.7) by rewriting the objective function:

```
$$\sum_{i=1}^{n} w_i^{(b)} \exp(-y_i \cdot (f^{(b-1)}(\mathbf{x}) + \alpha \tilde{y}(\mathbf{x}))) = e^{-\alpha} \sum_{i=1}^{n} w_i^{(b)}\{y_i = \tilde{y}(\mathbf{x})\} + e^{\alpha} \sum_{i=1}^{n} w_i^{(b)}\{y_i \neq \tilde{y}(\mathbf{x})\}\quad (7.9)
```

where we have used the indicator function to split the sum into two parts: the first over all data points classified by $\tilde{y}$ and the second over all points classified by $\alpha$. Because $\tilde{y}$ is the ensemble member we are learning at this, for notational simplicity we define $W^+$ and $W^-$ for the sum of weights of correctly classified and erroneously classified data points, respectively. Furthermore, let $W = W^+ + W^-$ be the total weight, $W = \sum_{i=1}^{n} w_i^{(b)}$. Minimizing (7.7) is done in two stages, first with respect to $\tilde{y}$ and then with respect to $\alpha$. This is possible since the minimizing argument in $\alpha$ turns out to be the actual value $\alpha > 0$, another convenient effect of using the exponential loss function. To do this, we can write the function (7.9) as:

```
$e^{-\alpha}W^+ + e^{\alpha}W^-\quad (7.10)
```

Since the total weight $W$ is independent of $\tilde{y}$ and since $e^{-\alpha} - e^{\alpha} > 0$ for any $\alpha > 0$, minimizing this expression with respect to $\tilde{y}$ is equivalent to minimizing with respect to $\alpha$, that is:

```
$$\alpha^{(b)} = \text{arg min}_{\alpha} \sum_{i=1}^{n} w_i^{(b)}\{y_i \neq \tilde{y}(\mathbf{x})\}\quad (7.11)$$
```

In words, the $b^{th}$ ensemble member should be trained by minimizing the weighted misclassification loss, where each data point $(\mathbf{x}_i, y_i)$ is assigned a weight $w_i^{(b)}$. The intuition for these weights is that, at iteration $b$, we should focus attention on the data points previously classified in order to “correct” the mistakes made by the ensemble of the first $b-1$ classifiers.

# # Ensemble methods: Bagging and boosting

> **Time to reflect 7.2:** In AdaBoost, we use the exponential loss for the boosting ensemble. How come we end up training the individual ensemble members using a weighted misclassification loss (and not the weighted exponential loss)?

How the problem (7.11) is solved in practice depends on the choice of base classifier that we use, that is, on the restrictions that we put on the function $\hat{y}$ (for example a classification tree). However, solving (7.11) is almost our standard classification problem, except for the weights $w_i^{(b)}$. Training the ensemble member $b$ on a weighted classification problem is, for most base classifiers, straightforward.

With the $b^{th}$ member, $\hat{y}^{(b)}(\mathbf{x})$, having been trained for the weighted classification problem (7.11) it remains to learn its confidence $\alpha^{(b)}$. This is done by solving (7.7), which amounts to minimizing (7.10) once $\hat{y}$ has trained. By differentiating (7.10) with respect to $\alpha$ and setting the derivative to zero we get:

```
$-\alpha e^{-\alpha}W^+ + e^{\alpha}W^- = 0 \Rightarrow e^{2\alpha} = W^+/W^- \Rightarrow \alpha = \frac{1}{2}\ln\left(\frac{W^+}{W^-}\right)$
```

Thus, by

```
$E_{train}^{(b)} \text{def } \frac{W^-}{W} = \sum_{i=1}^{n} \frac{w_i^{(b)}}{w_i^{(b)}} \mathbb{I}(y_i \neq \hat{y}^{(b)}(\mathbf{x})),\quad (7.12)
```

to be the weighted misclassification error for the $b^{th}$ classifier, we can express the optimal value for:

```
$$\alpha^{(b)} = \frac{1}{2}\ln\left(\frac{1-E_{train}^{(b)}}{E_{train}^{(b)}}\right),\quad (7.13)$$
```

The fact that $\alpha^{(b)}$ depends on the training error of the $b^{th}$ ensemble member is natural, as mentioned above, we can interpret $\alpha^{(b)}$ as the confidence in this member's predictions. This completes the derivation of the AdaBoost algorithm, which is summarized in Method 7.2. In the algorithm we exploit the fact that the weights $(7.8)$ can be computed recursively using the expression (7.6) in line 6 of the learning. Furthermore, we have added error normalization (line 7) which is convenient in practice and does not affect the derivation of the method above. The derivation of AdaBoost assumes that all coefficients $\alpha^{(b)}$ are positive. To see this we note that $\alpha$ will be positive as long as the weighted training error for the $b^{th}$ classifier, $E_{train}^{(b)}$, is less than 0.5. That is, the classifier just has to be slightly better than a coin flip, which is always the case in practice (note that $E_{train}^{(b)}$ is the training error. Indeed, if $E_{train}^{(b)}>0.5$, then we could simply flip the sign of all predictions by $\hat{y}^{(b)}(\mathbf{x})$ to reduce the error below 0.5).
