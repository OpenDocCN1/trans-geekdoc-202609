occur. It is also used for multi-class classification. We will look at both types of classification in the context of image recognition. Both LNNs and RNNs have some advantages over support vector machines (SVMs), as described in Chapter 11, in that they both provide probability prediction and handle multi-class problems directly. Further, we will demonstrate that RNNs will out-perform LNNs in image classification with outliers present and will provide equivalent performance when they are not present. We will present the loss functions for both methods that are used to estimate the parameters of the network. Optimization of these types of networks is carried out using gradient descent but they are usually accelerated using “momentum”, which will also be described. The method of creating the gradient terms through back propa-gation will also be included. In addition, accuracy metrics suitable for binary and multi-class classification will also be presented. Finally, three different applications will be used to compare and contrast RNNs and LNNs.

# 12.2 Set-up for Neural Networks

We begin with what appears to be a short review of logistic regression but actually forms the basis of neural networks. Recall that \(Y_i \in \{0, 1\}\) is the dichotomous dependent variable and \(\boldsymbol{x}_i = (1, x_{i1}, ..., x_{ip})^T\) is the \((p + 1)\)-dimensional vector of independent variables for the \(i\)th observation. Then, the conditional probability of \(Y_i = 1\) given \(\boldsymbol{x}_i\) is

\(P(Y_i = 1 | \boldsymbol{x}_i) = (1 + \exp(-\boldsymbol{x}_i^\top \boldsymbol{\beta}))^{-1},\) (12.2.1)

where \(\boldsymbol{\beta} = (\beta_0, \beta_1, ..., \beta_p)^T\) is the (p+1)-dimensional vector of regression parameters. The corresponding logistic regression model is as follows

\(\log \frac{p(\boldsymbol{x}_i)}{1 - p(\boldsymbol{x}_i)} = \beta_0 + x_{i1}\beta_1 + ... + x_{ip}\beta_p,\) (12.2.2)

where the sigmoid function is

\(p(\boldsymbol{x}_i) = \frac{1}{1 + \exp(-\boldsymbol{x}_i^\top \boldsymbol{\beta})}.\) (12.2.3)

We can develop an estimator for \(\boldsymbol{\beta}\) using maximum likelihood principles starting with

\(\mathcal{L}(\boldsymbol{\beta}) = \prod_{i=1}^n (p_i)^{y_i} (1 - p_i)^{(1-y_i)},\) (12.2.4)