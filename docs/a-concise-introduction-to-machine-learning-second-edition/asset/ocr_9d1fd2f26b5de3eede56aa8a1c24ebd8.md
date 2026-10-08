since $g$ and $g$ only differ by a multiplicative constant. Note that if the proposal distribution coincides with $f$, then we have $w_n = 1/N$.

As rejection sampling, it should be clear that the proposal distribution is crucial. Most importantly, it should not be in small regions where $f$ is large. The weighting which is useless if an actual sample is drawn from a region $g$.

*Sampling-importance-sampling (SIR)* combines from rejection sampling and importance sampling. $N$ samples $x_1, \dots, x_N$ are drawn from the proposal distribution $g$. Instead of rejecting $N$ samples with replacement are drawn from the discrete set $\{x_1, \dots, x_N\}$ according to the probabilities given by $w_1, \dots, w_N$. Thus a sample can feature several times in the final set, if its weight is larger than the weights of the other samples. If $g=f$, then all weights will equal $1/N$ and all samples are equally likely to be drawn.

# 3.4 Markov Chains

Markov chains are important building blocks for a class of sampling algorithms which can be applied to many different distributions and also scale with dimensionality.

*A Markov chain* is a series of random variables $x_1, \dots, x_N$ *called states*. The indices are associated with a sequence in time. A Markov chain of order $m$ satisfies the following

> $p(x_n|x_{n-1}, \dots, x_1) = p(x_n|x_{n-1}, x_{n-2}, \dots, x_{n-m})$

for $n = m+1, \dots, M$. In particular, the $n^{th}$ random variable only depends on the $m$ previous variables. A first-order Markov chain satisfies

> $p(x_n|x_{n-1}, x_{n-2}, \dots, x_1) = p(x_n|x_{n-1})$.

Each random variable depends only on its predecessor. We will only consider first-order Markov chains, since any Markov chain of order $m$ can be transcribed into a first-order Markov chain by the tuple $(y_n, \dots, y_{n-m+1})$, where $p(y_n|y_{n-1}, \dots, y_k) = p(y_n|y_{k-1})$.

The probability distribution of the variable $x_1$ needs to be specified. The probabilities $T_n(x_n|x_{n-1})$ are called transition probabilities from state $n-1$ to state $n$. If they are the same for all $n$, i.e. $T_n(x_n|x_{n-1}) = T(x_n|x_{n-1})$ for all, then the Markov chain is called homogeneous.

Graphically, a first-order Markov chain can be represented as

![](bbox=[0.257, 0.818, 0.742, 0.856])

The possible values $x_n$ can take form a state space. We distinguish between