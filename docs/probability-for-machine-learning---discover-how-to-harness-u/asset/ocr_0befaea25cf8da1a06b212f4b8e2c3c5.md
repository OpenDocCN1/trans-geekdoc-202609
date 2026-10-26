# 14.2 Problem of Latent Variables for Maximum Likelihood

A common modeling problem involves how to estimate a joint probability distribution for a dataset. Density estimation involves selecting a probability distribution function and the parameters of that distribution that best explain the joint probability distribution of the observed data. There are many techniques for solving this problem, although a common approach is called maximum likelihood estimation, or simply maximum likelihood. Maximum Likelihood Estimation involves treating the problem as an optimization or search problem, where we seek a set of parameters that results in the best fit for the joint probability of the data sample (introduced in Chapter 11).

A limitation of maximum likelihood estimation is that it assumes that the dataset is complete, or fully observed. This does not mean that the model has access to all data; instead, it assumes that all variables that are relevant to the problem are present. This is not always the case. There may be datasets where only some of the relevant variables can be observed, and some cannot, and although they influence other random variables in the dataset, they remain hidden. More generally, these unobserved or hidden variables are referred to as latent variables.

> Many real-world problems have hidden variables (sometimes called latent variables), which are not observable in the data that are available for learning.
> 
> — Page 816, Artificial Intelligence: A Modern Approach, 3rd edition, 2009.

Conventional maximum likelihood estimation does not work well in the presence of latent variables.

> ... if we have missing data and/or latent variables, then computing the [maximum likelihood] estimate becomes hard.
> 
> — Page 349, Machine Learning: A Probabilistic Perspective, 2012.

Instead, an alternate formulation of maximum likelihood is required for searching for the appropriate model parameters in the presence of latent variables. The Expectation-Maximization algorithm is one such approach.

# 14.3 Expectation-Maximization Algorithm

The Expectation-Maximization Algorithm, or EM algorithm for short, is an approach for maximum likelihood estimation in the presence of latent variables.

> A general technique for finding maximum likelihood estimators in latent variable models is the expectation-maximization (EM) algorithm.
> 
> — Page 424, Pattern Recognition and Machine Learning, 2006.

The EM algorithm is an iterative approach that cycles between two modes. The first mode attempts to estimate the missing or latent variables, called the estimation-step or E-step. The second mode attempts to optimize the parameters of the model to best explain the data, called the maximization-step or M-step.