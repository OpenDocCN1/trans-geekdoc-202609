time steps. At each step $t \ge 1$, $S_t = S_{t-1}$. For every node $v$ that is not active at $t-1$, find all nodes $u$ that may influence $v$ (i.e., incoming edges to $v$) and execute *activation attempt*, which is performed by a Bernoulli trial using probability $p$. If $u$'s activation attempt succeeds, add $v$ to $S_t$, that is, node $u$ influences (i.e., activates) $v$ at time $t$. If there are multiple nodes that may activate $v$, the result is similar irrespective of which one activates $v$. Since activation attempts of nodes are independent, the model is an independent, cascade model. When no more activation is possible, the network stays the same, and the set of activated nodes becomes the *final* $S$. At some point, no new activations are possible. All nodes are either activated or not. We call this *saturation*. An interesting property of ICM is that the capacity for diffusion is the same for all seed set nodes known as the *submodularularity principle*. Another property of ICM is that the set state is invariant to the seed size known as the *monotonicity principle*.

A *fixed threshold model* is one where each node $v$ has an individual threshold $\theta \in [0, 1]$. Our example in Chapter 6 showed how iPhone 5S was adopted as a fixed threshold model.

*A voter model* (Clifford and Sudbury, 1973) uses an undirected graph, where each node possesses a binary state 0 or 1. Iteratively, at each step, a node $v$ at time $t$ selects a random neighbor $u$ to mimic it $t-1$. To state more formally, states of node $\vec{x}_i$ probability that it is in state 1 (as opposed to being in state 0) is denoted by $\bar{x}_i(t)$, and $\bar{x}_i(0)$ is the state of node $i$ at $t=0$. Equation 7.1 is the update function for changes in node $i$'s state. $M$ is the stochastic transition matrix, where $M_{ij}=1/d_i$ and $d_i$ is the degree of node $i$. Dynamics of the voter model is summarized in Equation 7.2. When $t \to \infty$, the state ceases to change and $\bar{x}_i$ approaches a steady state. The voter model is adapted for use on many recent influence diffusion models (Li et al., 2013).

```
\bar{x}(i) = \sum_{j} M_{ij} \bar{x}_{t-1}(j)
```

```
\bar{x}_t = M \bar{x}_{t-1}
```

In a Markov random field model, each node of an undirected graph is a random variable $X_i$. According to the Markov property, $X_i$