distribution of **X**. Furthermore, if we assume the MRF changes its state during time, we can consider $X = \{X^{(k)} \in \mathbb{N}_0\}$ as a Markov chain taking values in $\Omega = A^V$ where $X^{(k)} = (\dots, X^{(k)})$ describes the state of the MRF at time $k=0$. At each step we now pick a random variable $X_i$, $i \in V$ with a probability $q(i)$ given by a strictly positive distribution $q$ on $V$ and a new value for $X_i$, based on its conditional probability distribution given the state $(x_v)_{V\setminus\{i\}}$ of all other $(x_v)_{V\setminus\{i\}}$, i.c. based on $\pi((x_v)_i | (x_v)_{V\setminus\{i}}) = \pi((x_v)_{V\setminus\{i\}})$. The transition probability $p_{xy}$ for two states $x, y$ of the MRF with $x 
eq y$ is given by

```
$p_{xy} = \begin{cases} \pi(y_i|(x_{V\setminus\{i\}}}}) & \exists i \in V \text{ such that } \forall v \neq i: x_v = y_v \ 0, & \text{else} \end{cases}$
```

(16)

And the probability, that the state of the MRF stays the same, is given by:

```
$p_{xx} = \sum_{i \in V} q(i) \pi(x_i|(x_{v})_{V\setminus\{i\}})$
```

(17)

It is easy to see that the joint distribution $\pi$ of the MRF is the stationary distribution of the Markov chain defined by these transition probabilities by showing the detailed balance condition (13): For $x = y$ if differ in the value of more than one random variable it follows that if $x$ and $y$ differ then $p_{xy} = p_{yx} = 0$. Assume that $x$ and $y$ differ only in the state of exactly one variable $X_i$, i.e. $x_j = y_j$ for $j 
eq i$ and $y_i 
eq x_i$, then it holds that:

```
$\pi(x)p_{xy} = \pi(x)q(i) \pi(y_i|(x_{v})_{V\setminus\{i\}}) = \pi((x_{v})_{V\setminus\{i\}}) q(i) \n\ = \pi(y_i,(x_{v})_{V\setminus\{i\}}) \pi(x_i|(x_{v})_{V\setminus\{i\}}) \n\ = \pi((y_{v})_{V\setminus\{i\}}) = \pi(y)p_{yx}$
```

(18)

Since $\pi$ is strictly positive so are the conditional distributions of the single variables. Thus, if every single variable $x_i \in A$ can take every state in a single transition and every state of the whole MRF can reach any $A^V$ in a finite number of steps and the Markov chain is irreducible it follows from the positivity of the conditional distributions that $p_{xy} > 0$ for all $x \in A^V$ and that the Markov chain is aperiodic. Aperiodicity and irreducibility guarantee that the chain converges to the stationary distribution $\pi$.

In practice the single random variables to be updated are usually not chosen at random based on a distribution $q$ but subsequently in predefined order. The corresponding algorithm is often referred to as **periodic Gibbs Sampler**. If $P$ is the transition matrix of the Gibbs chain, the convergence rate of the