# 5 Learning parametric models

As $L^2$ regularization, the regularization parameter $\lambda$ is to be chosen by the user, and has a similar meaning: $\lambda=0$ gives the least squares solution and $\lambda\to\infty$ gives $\theta=0$. Between these extremes, however, $L^1$ and $L^2$ give different solutions. Whereas $L^2$ pushes all parameters towards small (but not exactly zero), $L^1$ tends to favor sparse solutions where only a few of the parameters are non-zero, and the rest are zero. Thus, $L^1$ regularization can effectively 'switch off' some (by setting the regularization parameter $	heta_i$ to zero) and it can therefore be used as an input (or feature) selection method

# Example 5.2: Regularization for car stopping distance

Consider again the car stopping distance regression problem. We use the 10th order polynomial that was considered meaningless in Example 3.5 and apply $L^2$ and $L^1$ regularization to it, respectively. With manually chosen $\lambda$, we obtain the following models

![](bbox=[0.133, 0.319, 0.843, 0.459])

Both models suffer less from overfitting than the non-regular 10th order polynomial in Example 3.5. The two models are here, not identical. While all parameters are relatively small but non-zero in the $L^2$-regularized model (left panel), only 4 (out of 11) parameters are non-zero in the $L^1$-regularized model (right panel). It is typical for $L^1$ regularization to give sparse models, where some parameters are set exactly zero.

# General explicit regularization

The $L^1$ and $L^2$ regularization are two common examples of what we refer to as explicit regularization since they are both formulated as modifications of the cost function. They suggest a general pattern on how explicit regularization can be formulated,

> $$\hat{\theta} = \arg\min_{\theta} J(\theta;\mathbf{x,y}) + \lambda R(\theta). \quad (5.27)$

This expression contains three important elements:

+   (i) the cost function

In this view, that explicit regularization modifies the properties of fitting to the training data (minimizing $E_{train}$) into something else, which happily minimizes $E_{new}$. The actual design of the regularization term $R(\theta)$ can be in many ways. As a combination of the $L^1$ and $L^2$ terms, one option is $R(\theta) = ||\theta||_1 + ||\theta||^2$, which is often referred to as elastic regularization. Regardless of the exact expression of the regularization term, its purpose is to encourage small parameter values and thereby decrease the flexibility of the model, which may improve the performance and lower $E_{new}$.

Draft (April 30, 2021) of Machine Learning - A First Course for Engineers and Scientists. http://mlbook.org
Andreas Linholm, Nikolai Wshlin, Fredrik Indstedt, and Thomas B. Schön. 2021.