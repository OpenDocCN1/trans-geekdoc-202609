# ## 12.3 Maximum Likelihood Estimation

Maximum Likelihood Estimation, or MLE for short, is a probabilistic framework for estimating the parameters of a model (introduced in Chapter 11). In Maximum Likelihood Estimation, we wish to maximize the conditional probability of observing the data \((X)\) given a specific probability distribution and its parameters \((\theta)\), stated formally as:

$$P(X;\theta) \tag{12.4}$$

Where \(X\) is, in fact, the joint probability distribution of all observations from the problem domain from 1 to \(n\).

$$P(x_1,x_2,x_3,\ldots,x_n;\theta) \tag{12.5}$$

This resulting conditional probability is referred to as the likelihood of observing the data given the model parameters and written using the notation \(L()\) to denote the likelihood function. For example:

$$L(X;\theta) \tag{12.6}$$

The joint probability distribution can be restated as the multiplication of the conditional probability for observing each example given the distribution parameters. Multiplying many small probabilities together can be unstable; as such, it is common to restate this problem as the sum of the natural log conditional probability.

$$\sum_{i=1}^{n}\log P(x_i;\theta) \tag{12.7}$$

Given the common use of log in the likelihood function, it is referred to as a log-likelihood function. It is also common in optimization problems to prefer to minimize the cost function rather than to maximize it. Therefore, the negative of the log-likelihood function is used, referred to generally as a Negative Log-Likelihood (NLL) function.

$$\min -\sum_{i=1}^{n}\log P(x_i;\theta) \tag{12.8}$$

The Maximum Likelihood Estimation framework can be used as a basis for estimating the parameters of many different machine learning models for regression and classification predictive modeling. This includes the linear regression model.

# ## 12.4 Linear Regression as Maximum Likelihood

We can frame the problem of fitting a machine learning model as the problem of probability density estimation. Specifically, the choice of model and model parameters is referred to as a modeling hypothesis \(h\), and the problem involves finding \(h\) that best explains the data \(X\). We can, therefore, find the modeling hypothesis that maximizes the likelihood function.

$$\max\sum_{i=1}^{n}\log P(x_i;h) \tag{12.9}$$