# 6.2.2.1 Linear Units for Gaussian Output Distributions

One simple kind of output unit is based on an affine transformation with no nonlinearity. These are often just called linear units.

Given features $\bm{h}$, a layer of linear output units produces a vector $\bm{\hat{y}} = \bm{W}^{\top}\bm{h} + \bm{b}$. Linear output layers are often used to produce the mean of a conditional Gaussian distribution:

$$p(\bm{y} \mid \bm{x}) = \mathcal{N}(\bm{y}; \bm{\hat{y}}, \bm{I}). \tag{6.17}$$

Maximizing the log-likelihood is then equivalent to minimizing the mean squared error.

The maximum likelihood framework makes it straightforward to learn the covariance of the Gaussian too, or to make the covariance of the Gaussian be a function of the input. However, the covariance matrix be constrained to be a positive definite matrix for all inputs. It is difficult to satisfy such constraints with a linear output layer, so typically other output units are used to parametrize the covariance. Approaches to modeling the covariance are described shortly, in section 6.2.2.4.

Because linear units do not saturate, they pose little difficulty for gradient-based optimization algorithms and may be used with a wide variety of optimization algorithms.

# 6.2.2.2 Sigmoid Units for Bernoulli Output Distributions

Many tasks require predicting the value of a binary variable $y$. Classification problems with two classes can be cast in this form.

The maximum likelihood approach is to define a Bernoulli distribution over $y$ conditioned on $\bm{x}$. A Bernoulli distribution is defined by just a single number. The neural net needs to predict only $P(y = 1 \mid \bm{x})$. For this number to be a valid probability, it must lie in the interval $[0, 1]$.

Satisfying this constraint requires some careful design effort. Suppose we were to use a linear unit and threshold its value to obtain a valid probability:

$$P(y = 1 \mid \bm{x}) = \max \left\{ 0, \min \left\{ 1, \bm{w}^{\top}\bm{h} + b \right\} \right\}. \tag{6.18}$$

This would indeed define a valid conditional distribution, but we would not be able to train it very effectively with gradient descent. Any time that $\bm{w}^{\top}\bm{h} + b$ strayed