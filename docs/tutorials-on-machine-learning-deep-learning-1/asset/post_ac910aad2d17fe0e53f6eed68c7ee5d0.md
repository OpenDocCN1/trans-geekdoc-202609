
$p(h|v) = \frac{p(v,h)}{p(v)} = \frac{e^{-\frac{1}{T}E(v,h)}}{\sum_{h'} e^{-\frac{1}{T}E(v,h')}} \quad (10)$

Note that this expression of equality (9) is the difference of two expectations: the expected values of the energy function under the model distribution and under the conditional distribution of the hidden variables given the training example. Directly calculating this sum, which run over all values of the respective variables, leads to a computational complexity which is general exponential in the number of variables of the MRF. To avoid this computational burden the expectations can be approximated by samples drawn from the corresponding distributions based on MCMC techniques.

## 3 Markov Chains and Monte Carlo Techniques

Markov chains play an important role in RBM training because they provide a method to draw samples from 'complex' probability distributions like the Gibbs distribution of an MRF. This section will serve as an introduction to some fundamental concepts of Markov chain theory. A detailed introduction can be found, for example, in [6] and the aforementioned textbooks [5, 22]. The section will describe Gibbs sampling as an MCMC technique often used for MRF training and in particular for training RBMs.

### 3.1 Definition of a Markov Chain and Convergence to Stationarity

A Markov chain is a discrete stochastic process for which the Markov property holds, that is, a family of random variables $X = \{X^{(k)}|k \in \mathbb{N}_0\}$ which takes values in a (in the following conditions) set $\Omega$ and for which $\forall k \geq 0$ and $v_{j,i_0,\dots,i_k} \in \Omega$ is called

$p_j^{(k)} = P(X^{(k)} = j|X^{(k-1)} = i_{k-1}, \dots, X^{(0)} = i_0) \quad (11)$

$= P(X^{(k)} = j|X^{(0)} = i) \quad (12)$

This means that the next state of the system depends only on the current state and not on the sequence of events that preceded it. If for all $k \geq 0$ the $p_j^{(k)}$ the chain is called homogeneous and the matrix $\mathbf{P} = (p_{ij})_{i,j\in\Omega}$ is called transition matrix of the homogeneous Markov chain.

If the starting distribution $\mu^{(0)}$ (i.e. the probability distribution of $X^{(0)}$) is given by the probability vector $\mu^{(0)} = (\mu^{(0)}(i))_{i\in\Omega}$, with $\mu^{(0)}(i) = P(X^{(0)} = i)$, the distribution $\mu^{(k)}$ of $X^{(k)}$ is given by $\mu^{(k)} = \mu^{(0)}\mathbf{P}^k$

A distribution $\pi$ for which it holds $\pi^*$ is called stationary distribution. If the Markov chain for any time $k$ reaches the stationary distribution $\mu^{(k)} = \pi$ for all subsequent states will be distributed accordingly, that is, $\mu^{(k+n)} = \pi$ for all $n \in \mathbb{N}$. A sufficient (but not necessary) condition for a distribution $\pi$ to be stationary w.r.t. a Markov chain described by the transition probabilities $p_{ij}, i, j \in \Omega$ is that $\forall i, j \in \Omega$ it holds:

$$\pi(i)p_{ij} = \pi(j)p_{ji} . \quad (13)$$

This is called the **detailed balance condition**.

Specially relevant are Markov chains for which it is known that there exists an unique stationary distribution. For finite $\Omega$ this is the case if the Markov chain is *irreducible*. A Markov chain is irreducible if one can get from one state in $\Omega$ to any other in a finite number of transitions or more formally $\forall i, j \in \Omega$ $\exists k > 0$ with $P(X^{(k)} = j | X^{(0)} = i) > 0$.

A Markov chain is called aperiodic if for all $i \in \Omega$ the greatest common divisor of $\{k | P(X^{(k)} = i | X^{(0)} = i)\}$ is 1. One can show that an aperiodic Markov chain on a finite state space is guaranteed to converge to its stationary distribution (see, e.g., [6]). That is, for an arbitrary distribution $\mu$ it

$$\lim_{t \to \infty} d((\mu^{(t)}, \pi) = 0 . \quad (14)$$

where $d$ is the *distance of variation*. For two distributions $\alpha$ and $\beta$ on a finite state space $\Omega$, the distance of variation is defined as

$d_V(\alpha, \beta) = \frac{1}{2} \sum_{x \in \Omega} |\alpha(x) - \beta(x)| . \quad (15)$$

To clarify the notation, we allow both row and column probability vectors as arguments of the functions in (15).

Markov chain Monte Carlo methods make use of this convergence theorem for obtaining samples from certain probability distribution by setting up a Markov chain that converges to the desired distributions. Suppose you want to sample from a distribution $q$ with a finite state space. Then you construct an irreducible and aperiodic Markov chain with stationary distribution $\pi = q$. This is a non-trivial task. If $t$ is large, $X^{(t)}$ from the constructed chain is then approximately sample from $\pi$ and therefore from $q$. Gibbs Sampling [13] is such a MCMC method and will be described in the following section.

### 3.2 Gibbs Sampling

Gibbs Sampling belongs to the class of Metropolis-Hastings algorithms [14]. It is a simple MCMC algorithm for drawing samples from the joint probability distribution of multiple random variables. The basic idea is to update each variable subsequently based on its conditional distribution giving the state of the others. We will describe it in detail explaining how Gibbs sampling can be used to simulate the Gibbs distribution of MRF.

We consider an MRF $X = (X_1, \dots, X_N)$ w.r.t. a graph $G = (V, E)$, where $V = \{1, \dots, N\}$ for the sake of clarity of notation. The random variables $X_i, i \in V$ take values in a finite set $\mathcal{A}$ and $\pi(x) = \frac{1}{Z}e^{-E(x)}$ is the joint probability distribution of **X**. Furthermore, if we assume the MRF changes its state during time, we can consider $X$ as a Markov chain taking values in $\Omega = A^V$. At each step we pick a random variable $X_i, i \in V$ with a probability $q(i)$ and a new value for $X_i$, based on its conditional distribution given the state of the others $(x_{v\setminus\{i\}})$. The transition probability $p_{xy}$ for two states $x, y$ of the MRF with $x \neq y$ is given by

$$p_{xy} = \begin{cases} \pi(y_i|(x_{v\setminus\{i\}}}}) & \exists i \in V \text{ such that } x_v = y_v \\ 0, & \text{else} \end{cases}$$
(16)

And the probability that the state of the MRF stays the same, is given by:

$$p_{xx} = \sum_{i \in V} q(i) \pi(x_i|(x_{v\setminus\{i\}}})$$
(17)

It is easy to see that the joint distribution $\pi$ of the MRF is the stationary distribution of the Markov chain by showing the detailed balance condition (13): For $x = y$ if differ in the value of more than one variable it follows that if $x$ and $y$ differ then $p_{xy} = p_{yx} = 0$. Assume that $x$ and $y$ differ only in the state of exactly one variable $X_i$, i.e. $x_j = y_j$ for $j \neq i$ and $y_i \neq x_i$, then it holds that:

$$\pi(x)p_{xy} = \pi(x)q(i) \pi(y_i|(x_{v\setminus\{i\}})) = \pi((x_{v\setminus\{i\}})) q(i) = \pi(y_i,(x_{v\setminus\{i\}})) \pi(x_i|(x_{v\setminus\{i\}})) = \pi((y_{v\setminus\{i\}})) = \pi(y)p_{yx}$$
(18)
