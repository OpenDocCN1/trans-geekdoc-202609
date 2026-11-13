Expected SARSA is less volatile than SARSA because the latter is strongly impacted by the random choice of \(a_{i+1}\). In expected SARSA, the average smoothes the learning process.

# 16.2 The curse of dimensionality

Let us first recall that reinforcement learning is a framework that is not linked to a particular algorithm. In fact, different tools can very well co-exist in a RL task (AlphaGo combined both tree methods and neural networks, see Silver et al. (2016)). Nonetheless, any RL attempt will always rely on the three key concepts: the states, actions and rewards. In factor investing, they are fairly easy to identify, though there is always room for interpretation. Actions are evidently defined by portfolio compositions. The states can be viewed as the current values that describe the economy: as a first-order approximation, it can be assumed that the feature levels fulfill this role (possibly conditioned or complemented with macro-economic data). The rewards are even more straightforward. Returns or any relevant performance metric\(^2\) can account for rewards.

A major problem lies in the dimensionality of both states and actions. Assuming an absence of leverage (no negative weights), the actions take values on the simplex

```
\(\mathbb{S}_N = \left\{ \mathbf{x} \in \mathbb{R}^N \, \sum_{n=1}^N x_n = 1, x_n \ge 0, \, \forall n=1, \dots, N \right\}\) (16.13)
```

and assuming that all features have been uniformized, their space is \([0, 1]^{NK}\). Needless to say, the dimensions of both spaces are numerically impractical.

A simple solution to this problem is discretization: each space is divided into a small number of categories. Some authors do take this route. In Yang et al. (2018), the state space is discretized into three values depending on volatility, and actions are also split into three categories. Bertoluzzo and Corazza (2012) and Xiong et al. (2018) also choose three possible actions (buy, hold, sell). In Almahdi and Yang (2019), the learner is expected to yield binary signals for buying or shorting. García-Galicia et al. (2019) consider a larger state space (8 elements) but restrict the action set to 3 options.\(^3\) In terms of the state space, all articles assume that the state of the economy is determined by prices (or returns).

One strong limitation of these approachable is the marked simplification they imply. Realistic discretizations are numerically intractable when investing in multiple assets. Indeed, splitting the unit interval in \(h\) points yields \(h^{NK}\) possibilities for feature values. The number of options for weight combinations is exponentially increasing \(N\). As an example: just 10 possible values for 10 features of 10 stocks yield \(10^{100}\) permutations.

The problems mentioned above are of course not restricted to portfolio construction. Many solutions have been proposed to solve Markov Decision Processes in continuous spaces. We refer for instance to Section 4 in Powell and Ma (2011) for a review of early methods (outside finance).