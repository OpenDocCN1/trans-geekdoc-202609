Kullback-Leibler divergence (KL-divergence) or relative entropy, is one way to measure the dissimilarity of two probability distributions, p and q,

```
KL(p||q) \triangleq \sum_{k=1}^K p_k \log \frac{p_k}{q_k} \triangleq \sum_{k=1}^K p_k \log p_k - p_k \log q_k = -H(p) + H(p, q). \quad (3)
```

Here H(p, q) is the cross entropy. We have K L(p, q) \triangleq - \sum_{k=1}^K p_k \log q_k. See Murphy (2012).

Training error measures the error on the training data, minimizing which is an optimization problem. Generalization error, or test error, measures the error on new input data, which differentiates machine learning from optimization. A machine learning algorithm tries to make the training error, and the gap between training error and testing error small. A model is under-fitting if it can not achieve a low training error; a model is over-fitting if the gap between training error and test error is large.

A model's capacity measures the range of functions it can fit. Ockham's razor^4 states that, with the same expressiveness, simple models are preferred. Training error and generalization error vs. model capacity usually form a U-shape relationship. We find the optimal capacity to achieve low training error and small gap between training error and generalization error. Bias measures the expected deviation of the estimator from the true value; while variance measures the deviation of the estimator from the expected value, or variance of the estimator. As model capacity increases, bias tends to decrease, while variance tends to increase, yielding another U-shape relationship between generalization error vs. model capacity. We try to find the optimal capacity point, of which under-fitting occurs on the left and over-fitting occurs on the right. Regularization adds a penalty term to the cost function, to reduce the generalization error, but not training error. No free lunch theorem states that there is no universally best model, or best regularizer. An implication is that deep learning may not be the best model for some problems. There are model parameters, and hyperparameters for model capacity and regularization. Cross-validation is used to tune hyperparameters, to strike a balance between bias and variance, and to select the optimal model.

Maximum likelihood estimation (MLE) is a common approach to derive good estimation of parameters. For issues like numerical underflow, the product in MLE is converted to summation to obtain negative log-likelihood (NLL). MLE is equivalent to minimizing KL divergence, the dissimilarity between the empirical distribution defined by the training data and the model distribution. Minimizing KL divergence between two distributions corresponds to minimizing the cross-entropy between the distributions. In short, maximization of likelihood becomes minimization of the negative log-likelihood (NLL), or equivalently, minimization of cross entropy.

Gradient descent is a common way to solve optimization problems. Stochastic gradient descent extends gradient descent by working with a single sample each time, and usually with minibatches.

Importance sampling is a technique to estimate properties of a particular distribution, by samples from a different distribution, to lower the variance of the estimation, or when sampling from the distribution of interest is difficult.

There are mathematical analysis frameworks for machine learning algorithms. Kolmogorov complexity (Li and Vitányi, 2008), or algorithmic complexity, studies the notion of simplicity in Ockham's razor. In probably approximately correct (PAC) learning (Valiant, 1984), a learning algorithm aims to select a generalization function, to achieve low generalization error with high probability. VC dimension (Vapnik, 1998) measures the capacity of a binary classifier.

# 2.3 DEEP LEARNING

Deep learning is in contrast to "shallow" learning. For many machine learning algorithms, e.g., linear regression, logistic regression, support vector machines (SVMs), decision trees, and boosting, we have input layer and output layer, and the inputs may be transformed with manual feature engineering before training. In deep learning, between input and output layers, we have one or more hidden layers. At each layer except the input layer, we compute the input to each unit, as the weighted sum of units from the previous layer; then we usually use nonlinear transformation, or activation function, such as logistic, tanh, or more popularly recently, rectified linear unit (ReLU), to apply to the input of a unit, to obtain a new representation of the input from the previous layer. We

^4 "Occam's razor" is a popular misspelling (Russell and Norvig, 2009).