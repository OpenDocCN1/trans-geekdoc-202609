That is, the goal is to locate a hypothesis that best explains the observed data. This simplification provides the basis for an optimization procedure for searching for a model and set of parameters that best fits the data, referred to generally as density estimation.

# 17.3 Density Estimation

A common modeling problem involves how to estimate a joint probability distribution for a dataset. For example, given a sample of observations ($X$) from a domain ($x_1, x_2, x_3, \cdots, x_n$), where each observation is drawn independently from the domain with the same probability distribution (so-called independent and identically distributed, i.i.d., or close to it). Density estimation involves selecting a probability distribution function and the parameters of that distribution that best explains the joint probability distribution of the observed data ($X$). Often estimating the density is too challenging; instead, we are happy with a point estimate from the target distribution, such as the mean. There are many techniques for solving this problem, although two common approaches are:

+   - Maximum a Posteriori (MAP), a Bayesian method.
+   - Maximum Likelihood Estimation (MLE), a frequentist method.

Both approaches frame the problem as optimization and involve searching for a distribution and set of parameters for the distribution that best describes the observed data. In Maximum Likelihood Estimation (introduced in Chapter 11), we wish to maximize the probability of observing the data from the joint probability distribution given a specific probability distribution and its parameters, stated formally as:

$P(X; \theta)$
(17.4)

or

$P(x_1, x_2, x_3, \cdots, x_n; \theta)$
(17.5)

This resulting conditional probability is referred to as the likelihood of observing the data given the model parameters. The objective of Maximum Likelihood Estimation is to find the set of parameters ($\theta$) that maximize the likelihood function, e.g. result in the largest likelihood value.

$\max P(X; \theta)$
(17.6)

An alternative and closely related approach is to consider the optimization problem from the perspective of Bayesian probability.

A popular replacement for maximizing the likelihood is maximizing the Bayesian posterior probability density of the parameters instead.

> — Page 306, *Information Theory, Inference and Learning Algorithms*, 2003.

Let’s take a closer look at the Bayesian approach to solving this optimization problem.