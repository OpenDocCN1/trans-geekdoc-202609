
boundary, either linear or nonlinear, that acts to separate members of one group from the other. For example, let's say a bank is giving out loans and wants to classify each potential customer as either worthy of getting a loan or not, based on a set of data associated with existing customers. Our target group would be those who received loans and paid them back, and the alternate group would be comprised of those who received loans and did not pay back. This is a classic binary classification problem since we want to identify the characteristics of the customers who tend to pay back loans as the criteria for giving out future loans.

Methods such as the perceptron algorithm, k-nearest neighbours (kNN) classification, random forest, logistic regression and support vector machines, to name the most prominent methods, have been developed to address this problem. Typically one group is labeled with 1 as being the target group while the other is labeled 0. For some methods, +1 and -1 may be more suitable labels. Either way, the objective is to find the separation boundary that allows for accurate prediction of the group to which any new data belongs.

As yet, binary classification problems have not been addressed using rank-based methods, and it is not clear how the approach would perform in this machine learning task. We will examine log-likelihood logistic regression and a new rank-based logistic regression in this chapter. The notion of an outlier in the context of binary classification will be established and methods to detect such outliers will be described using the rank-based approach. There are also some indications that it could establish the maximum accuracy of logistic regression on a training set. As such, it serves as another step towards robust data science and machine learning.

## 11.3.1 Log-likelihood Setup

Logistic regression is well-suited to binary classification problems and probability prediction (Hosmer and Lemeshow, 1989). We begin with a short description of basic logistic regression. We first define \(Y_i \in \{0, 1\}\) as the dichotomous dependent variable and \(\boldsymbol{x}_i = (1, x_{i1}, x_{i2}, \dots, x_{ip})^\top\) as a \((p + 1)\)-dimensional vector of explanatory variables for the \(i^{th}\) observation in a sample set, where \(i \in \{1, ..., n\}\). Then, the conditional probability of \(Y_i = 1\) given \(\boldsymbol{x}_i\) is

\(P(Y_i = 1|\boldsymbol{x}_i) = p(\boldsymbol{x}_i) = \left[ \frac{1}{1 + \exp(-\boldsymbol{x}_i^\top \boldsymbol{\beta})} \right], \quad (11.3.1)\)

where \(\boldsymbol{\beta} = (\beta_0, \beta_1, \dots, \beta_p)^\top\) is the length \(p\) vector of regression parameters of interest, with intercept \(\beta_0\). Rearranging the above, the logistic regression problem is given by

Figure 11.1 Sigmoid function.

![](img/f3b106d7e76ae3afcec8895afa28732c_367_0.png)

$$ \log \frac{p(\boldsymbol{x}_i)}{1 - p(\boldsymbol{x}_i)} = \beta_0 + x_{i1}\beta_1 + \dots + x_{ip}\beta_p. $$ (11.3.2)

The left-hand side is referred to as the logit link function, z, also known as the logarithm of the odds,

$$ z = \log \frac{p(\boldsymbol{x}_i)}{1 - p(\boldsymbol{x}_i)}. $$ (11.3.3)

Suppose we find estimates $\hat{\boldsymbol{\beta}}$ using a suitable estimator and want to predict the probability, $\hat{p}(\boldsymbol{x})$, of some new $\boldsymbol{x}$ that it has a response of $Y = 1$. This can be done in two steps. We first calculate $z$ using

$$ \hat{z} = \boldsymbol{x}^{\top}\hat{\boldsymbol{\beta}} = \hat{\beta}_0 + \hat{\beta}_1 x_1 + \dots + \hat{\beta}_p x_p. $$ (11.3.4)

Second, we predict the probability from the sigmoid function

$$ \hat{p}(\boldsymbol{x}) = \frac{1}{1 + \exp(-\boldsymbol{x}^{\top}\hat{\boldsymbol{\beta}})} = \frac{1}{1 + \exp(-\hat{z})} = p(\hat{z}). $$ (11.3.5)

It is instructive to examine the sigmoid function in more detail. A graph of the function $p(z)$ is shown in Figure 11.1. Note that for large positive values of z, the probability asymptotically approaches 1, whereas for large negative values it asymptotically approaches 0. The ground truth (i.e. true value) of the dependent variable $y$ is either 0 or 1 for any given $\boldsymbol{x}$. However, the predicted value $\hat{p}(\boldsymbol{x})$ lies between 0 and 1 but does not reach either value for reasons that should be clear from Eq. (11.3.5). For binary classification, the predicted value, $\hat{p}(\boldsymbol{x})$, is compared to 0.5. If $\hat{p}(\boldsymbol{x}) > 0.5$, we predict 1, whereas if $\hat{p}(\boldsymbol{x}) < 0.5$, we predict 0.

Alternatively, we could base the decision of 1 or 0 on a sign test using $\hat{z} = \boldsymbol{x}^{\top}\hat{\boldsymbol{\beta}}$. Conceptually, z represents a line or hyperplane that separates 0s from 1s. We note that $\hat{\beta}_0$ functions as a bias term in this expression. In other words, if $\boldsymbol{x} = 0$ then either $\hat{\beta}_0 > 0$ or $\hat{\beta}_0 < 0$ so there is a built-in bias due to $\hat{\beta}_0$. It effectively shifts the p-dimensional hyperplane in one direction or the other by an amount equal to the bias term. The rest of the coefficients, $\hat{\beta}_1, \dots, \hat{\beta}_p$, establish the actual hyperplane. The linear boundary in p dimensions (i.e. the hyperplane boundary) is positioned where

\hat{\beta}_0 + \hat{\beta}_1 x_1 + \cdots + \hat{\beta}_p x_p = 0.

Therefore, we would say we have a predicted response of 1 if

\hat{\beta}_0 + \hat{\beta}_1 x_1 + \cdots + \hat{\beta}_p x_p > 0,

and a predicted response of 0 if

\hat{\beta}_0 + \hat{\beta}_1 x_1 + \cdots + \hat{\beta}_p x_p \le 0.

This can also be understood by examining values of z in Figure 11.1. If z is positive, we can declare it as 1 whereas if z is negative, we declare it as 0. To summarize, we can either use \hat{z} or p(\hat{z}) to decide the binary response of a given \mathbf{x}.

In order to determine the estimates, we use maximum likelihood estimation which can be formulated in a number of ways. We will find it convenient to use

\mathcal{L}(\mathbf{y}, \mathbf{p}) = \prod_{i=1}^n (p_i)^{y_i} (1 - p_i)^{(1-y_i)},

where p_i = p(\mathbf{x}_i) is the i\text{th} element of \mathbf{p} = (p(\mathbf{x}_1), \dots, p(\mathbf{x}_n))^T, and y_i is the i\text{th} element of \mathbf{Y} = (y_1, \dots, y_n)^T. It is more common to minimize the negative log-likelihood (LL) form of the loss function to obtain the estimates, \hat{\beta}, as follows

J(\boldsymbol{\beta}) = J(\mathbf{y}, \mathbf{p}) = - \sum_{i=1}^n [y_i \log p_i + (1 - y_i) \log(1 - p_i)].

For one observation, \mathbf{x}, the loss function is simply

J(y, p(\mathbf{x})) = -y \log p(\mathbf{x}) - (1 - y) \log(1 - p(\mathbf{x})).

This function can be interpreted intuitively by noting that y can only be 0 or 1. If y = 0, the first term can be ignored and the loss is given by the second term, which simplifies to minimizing \log(1 - p(\mathbf{x})). If y = 1, then the second term can be ignored, which simplifies to minimizing \log(p(\mathbf{x})). Therefore, the function in Eq. (11.3.10) has the desired characteristics for logistic regression. More importantly, J(\boldsymbol{\beta}) is a convex function in terms of \boldsymbol{\beta} which facilitates convergence to the global minimum. Hence, the log-likelihood logistic regression (LLR) estimator is given by

\hat{\boldsymbol{\beta}}_n^{\text{LLR}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ - \sum_{i=1}^n [y_i \log p_i + (1 - y_i) \log(1 - p_i)] \right\}.

However, as we shall see shortly, using this loss function has certain limitations that may affect the prediction accuracy of the estimates.

The numerical optimization technique used in logistic regression is usually some form of gradient descent. We will describe only the simplest form for our purposes here. Basically, we compute the loss function using an initial guess, \(\boldsymbol{\beta}^{(0)}\), and then take a step in the gradient direction to reduce the value of \(J(\boldsymbol{\beta})\). The process is repeated until the minimum is found. This iterative method requires partial derivatives of \(J(\boldsymbol{\beta})\) in Eq. (11.3.10) with respect to \(\boldsymbol{\beta}\).

Consider again the case where there is only one observation, \(\boldsymbol{x}\), and one known binary response, y. Starting with the loss function, \(J(\boldsymbol{\beta})\), we can apply the chain rule to obtain the needed gradients. For some parameter, \(\beta_j\), we have that

\(\frac{\partial J(\boldsymbol{\beta})}{\partial \beta_j} = \frac{\partial J(y, p(\boldsymbol{x}))}{\partial p(\boldsymbol{x})} \frac{\partial p(\boldsymbol{x})}{\partial \beta_j} = (p(\boldsymbol{x}) - y)x_j.\)

This comes from the partial derivative in the first term,

\(\frac{\partial J(y, p(\boldsymbol{x}))}{\partial p(\boldsymbol{x})} = -\frac{y}{p(\boldsymbol{x})} + \frac{1-y}{1-p(\boldsymbol{x})},\)

and the second term, which involves the partial derivative of the sigmoid function,

\(\frac{\partial p(\boldsymbol{x})}{\partial \beta_j} = \frac{\exp(-\boldsymbol{x}^{\text{T}}\boldsymbol{\beta})}{(1+\exp(-\boldsymbol{x}^{\text{T}}\boldsymbol{\beta}))^2} x_j = p(\boldsymbol{x})(1-p(\boldsymbol{x}))x_j.\)

Next, consider the case with \(n\) observations. We have to sum up such quantities in Eq. (11.3.12) associated with each observation for every parameter. Combining the steps above, an update equation for each \(\beta_j, j = 0, \dots, p\), to compute the next iteration values is given by

\(\beta_j^{(t+1)} = \beta_j^{(t)} - \ell \times \frac{\partial J(\boldsymbol{\beta})}{\partial \beta_j} = \beta_j^{(t)} - \ell \sum_{i=1}^n (p(\boldsymbol{x}_i) - y_i)x_{ij},\)

where \(\ell\) is a tuning parameter called the learning rate that controls the step size needed in each iteration to produce a smooth yet rapid convergence to the global solution. This is for one observation only.

The equations can be formulated conveniently using matrix notation as follows. We start with \(\boldsymbol{X}\), an \(n \times (p+1)\) matrix. The \(n\) logit values are computed using an initial \(\boldsymbol{\beta}_n^{(0)}\) value as

\(\boldsymbol{z} = \boldsymbol{X}\boldsymbol{\beta}_n^{(0)}.\)

The \(n\) predicted responses are computed using the sigmoid function

\(p(\boldsymbol{X}) = \frac{1}{1 + \exp(-\boldsymbol{z})}.\)
