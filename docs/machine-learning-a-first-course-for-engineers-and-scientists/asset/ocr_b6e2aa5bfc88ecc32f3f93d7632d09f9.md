# 10 Generative models and learning from unlabeled data

computing the mean vector for the $m$th class in (10.3b), for instance, we do not know which data points should be included in the sum.

However, a possible way around this is to first learn a GMM, which is then used to predict the missing values $\{y_i\}_{i=1}^n$, and thereafter these predictions are used to update the model. Doing this iteratively in the following algorithm:

+   (i) Learn the GMM from the $n$ labeled input-output pairs $(x_i, y_i)_{i=1}^n$,

+   (ii) Use the GMM to predict (as a QDA classifier) the missing outputs to $\{x_i\}_{i=n+1}^n$,

+   (iii) Update the GMM using the predicted outputs from (ii),
 then repeat until convergence.

At first light this looks an *ad hoc* procedure and it is far from obvious that it could be anything else. It turns out that it is a widely used statistical tool referred to the expectation-maximization (EM) algorithm. We study the EM algorithm and its validity in more detail in Section 10.2. We simply note that, when applied to the maximum likelihood procedure (10.9), it boils down to the procedure outlined above, as we pay attention to a few important details: From step (ii) we return the predicted class probabilities $p(y=m|x,\hat{	heta})$ (and not the class prediction $y(\hat{x}_i)$) using the current parameter estimates $\hat{	heta}$, and in step (iii) we make use of the predicted class probabilities by introducing the notation

```
$w_i(m) = \begin{cases} p(y=m|x_i,\hat{	heta}) & \text{if } y_i \text{ is missing} \ 1 & \text{if } y_i = m \ 0 & \text{otherwise} \end{cases}$
```

and update the parameters as

```
$\hat{\mu}_m = \frac{1}{\sum_{i=1}^n w_i(m)},
```

```
$\hat{\Sigma}_m = \frac{1}{\sum_{i=1}^n w_i(m)} \sum_{i=1}^n w_i(m)(x_i - \hat{\mu}_m)(x_i - \hat{\mu}_m)^	op$.
```

Note that we use the current parameter estimate $\hat{	heta}$ in step (ii), which is then updated in step (iii), so we go back to (i) for the next iteration the class probabilities will be computed using a new value of $\hat{	heta}$. When computing the parameters for class $m$ according to (10.10), the unlabeled data points counts proportionally to the current estimates of the classes that they belong to. Note that this is a generalization of the supervised case, (10.3) is a special case of (10.10) when no labels $y_i$ are available. With these modifications it can be shown (Section 10.2) that the procedure discussed above converges to a stationary point of (10.9) in the semi-supervised setting. We summarize the procedure as Method 10.2, and illustrate it in Figure 10.6 by applying it to the semi-supervised data introduced in Figure 10.5.

We have devised a way to handle semi-supervised classification problems using the GMM, and thus in the semi-supervised setting when some output $y_i$ are from the training data.

It is not clear why we have chosen to introduce the semi-supervised problem in connection to generative models. Alternatively, we could think of using a discriminative model (instead of the GMM) for iteratively predicting the missing $y_i$ and updating the model using these predictions. This is possible and such discriminative label-imputation methods can work well in many challenging semi-supervised cases. The generative modeling paradigm provides us with a more principled