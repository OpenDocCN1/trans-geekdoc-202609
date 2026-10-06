# 3.4 Generalized linear models

modified version of the normal equations,

```
$$(X^T X + n\lambda I_{p+1})\hat{	heta} = X^T y.$$
```

where $I_{p+1}$ is the identity matrix of size $(p+1) \times (p+1)$. This particular application of $L^2$ regularization is referred to as ridge regression.

Regularization is not restricted to linear regression, however the same $L^2$ penalty can be applied to any method that involves optimizing a cost function. For instance, for logistic regression we get the optimization problem

```
$$\hat{	heta} = \arg\min_{\theta} \sum_{i=1}^n \ln(1 + \exp(-y_i^T x_i)) + \lambda|\theta||_2^2.$
```

It is common to learn linear regression using (3.50) of (3.29). One reason is to decrease issues with overfitting, as discussed above. Another reason is for the non-regularized cost function (3.29), the optimal $\hat{	heta}$ is not found if the training data is linearly separable (meaning there exists a linear boundary which separates the classes perfectly). In practice it means that the logistic regression diverges with some datasets, (3.50) with $\lambda > 0$ is used instead of (3.29). The regularization term implies that there is a unique solution to the optimization problem, despite the fact that the softmax model is overparameterized as discussed.

# 3.4 Generalized linear models

In this chapter we have introduced two parametric models for regression and classification, linear regression and logistic regression. The latter was presented as a way of adapting linear regression to the categorical nature of the output encountered in a classification problem. This was done by passing the linear regression through a nonlinear (in this case logistic) function, allowing us to interpret the output as a probability.

The same principle can be generalized to adapt the linear model other properties of the output and is referred to as generalized linear models. In the discussion we have focused on two specific problems containing two types of output data, real-valued regression ($y \in \mathbb{R}$) and classification ($y \in \{1,...,M\}$). These are most common instances of supervised regression problems and, indeed, they will be central to discuss of the methods and methods presented in this book.

In various applications we might encounter data with other output, not well described by either of the two standards. For instance, imagine the output corresponds to the count of earthquakes in a certain area during a fixed time, the number of people with a specific illness in a certain region, or the number of patients presented to a certain test. In such cases $y$ is a count taking one of the values $0, 1,...,$ (formally $y \in \mathbb{N}$), count data, being numerical in nature, is not well described by a linear regression of the form (3.2). The reason is that the linear regression model is not restricted to discrete values, neither whether to be non-negative, however we know that this is the case for the actual output $y$ that we are trying to predict. Neither this scenario fits a classification setting, where $y$ is numerical (that the values can be ordered) or there is no upper limit on how large $y$ can be.

To address this issue we extend our use of parametric models to encompass various probability distribution that can be used to model the conditional distribution $p(y|\mathbf{x})$. The first step is to choose a suitable form for the conditional distribution. This is part of the model design, guided by the properties of the data. Specifically, we select a distribution with support corresponding to that of the data (such as the natural numbers). Naturally, we still want to allow the distribution to depend on the input variable $\mathbf{x}$—modeling the relationship between the input and output variables is the fundamental task of supervised learning after all. However, this can be accomplished by first computing

> Simply adding the additive noise $\epsilon$ is discrete is not enough, though the regression function itself $\theta^T x$ can take arbitrary values.

This material will be published by Cambridge Press. This pre-publication version is free to view and for personal use only. Not for re-publication, re-sale or use in derivative works.

Andreas Lindholm, Nikolai Wahlström, Fredrik Ljungquist, and Thomas B. Schön 2021.