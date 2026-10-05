# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 53

$Var(X) = \frac{(b-a)^2}{12} \quad (2.58b)$

![](bbox=[0.275, 0.185, 0.765, 0.455])

A special uniform distribution for which $a=0, b=1$, called the standard uniform distribution, is very useful in generating random samples from any probability distribution function. Also, if $Y=Asin X$, where $X$ is a uniformly distributed random variable, the distribution of $Y$ is said to be a sinusoidal distribution.

# 2.5.2 Exponential Distribution

This distribution, also known as *negative exponential distribution*, is important because of its relationship to the Poisson distribution. It is frequently used in simulation of queueing systems to describe the interval or interdeparture times of customers at a server. Its frequent use is due to the lack of conditioning of remaining time on past time expended. This peculiar characteristic is known variably as Markov, *forgetfulness*, or *lack of memory* property. For a given Poisson process, the time interval $X$ between occurrence of events has an exponential distribution with the following PDF

$f_X(x) = \lambda e^{-\lambda x} u(x) \quad (2.59)$