# # Weakly supervised learning

It is a type of machine learning technique which is designed to use a limited or less amount of labeled data or, we can say, very less use of training examples. It is also called the self-learning or bootstrapping method. It starts by taking a few training sets, then training of the classifier takes place and also it uses some testing examples.

And with an increase in training sets, the performance of the classifier also improves, which leads to self-learning.

# ## Maximum Likelihood Estimation (MLE)

Maximum Likelihood Estimation (MLE) is the most common method for the estimation of the parameters, such as mean, variance, and so on, of a model that best describes the observation.

Let be the parameter of the model and be the observation.

The probability of \(\theta\) given \(Y\) can be calculated by using Naïve Bayes theorem.

\(P(\theta \mid Y) = \frac{P(Y|\theta)P(\theta)}{P(Y)}\) (1.24)

Let us consider that the data is **independent and identically distributed (IID)**. Here, identical distribution means that the data comes from a common distribution with the same type of parameters.

But now, we want to calculate the probability of new observations given the value of the parameter, that is, to calculate the likelihood of "\(\theta\)". For IID \(Y\), likelihood function of "\(\theta\)" can be written as the product of the probability for every data point.

\(L_Y(\theta) = \pi_{y \in Y} p(y|\theta)\) (1.25)

To calculate log-likelihood, take the log of the preceding equation 1.20:

\(L_Y(\theta) = \Sigma_{y \in Y} log[p(y|\theta)]\) (1.26)

Differentiate the preceding equation to calculate the maximum log-likelihood.

Let us take an example of a Bernoulli trial-coin flipping. Bernoulli distribution is a discrete probability distribution which takes the value of *success* as \(p\) and of *failure* as \(q=1-p\).

The **probability mass function (PMF)** of the distribution over possible outcomes \(l\) is given as follows:

\(f(l; p) = p^l(1 - p)^{1-l}\) (1.27)