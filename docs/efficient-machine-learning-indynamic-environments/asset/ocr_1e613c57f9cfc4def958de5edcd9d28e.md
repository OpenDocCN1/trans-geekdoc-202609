we need to formalize the access the player has to the loss function. We will formulate this in the following stochastic way.

# **Definition A.1.** An algorithm ORACLE is said to be a (\(\beta\), \(\delta\)) weak-gradient if

```
\(\langle \text{ORACLE}(f, p), \nabla_f F(f, p) \rangle \ge \beta\) (A.3)
```

with probability \(1 - \delta\).

Here \(\nabla_f\) denotes the functional gradient of \(F\). This notion is similar to the weak learning assumptions usually used in the boosting literature. Given such an oracle one can ask for methods similar to first order methods for convex optimization, such as gradient descent, to solve the minimax problem. These algorithms iteratively maintain candidate solutions for the both the players and update each of these using feedback from the state of the other player. In our particular setting, the hypothesis player updates using the vector \(h\) in Equation (2.3).

# **Motivating Example.**

Let \(\mathcal{F}\) be a class of hypotheses, let \(\mathcal{P}\) be the set of all distributions over a finite sample set \(\{x_1, \dots, x_n\}\) and let \(L\) be the 0-1 loss. Note that in this setting, the oracle from Definition A.1 is analogous to weak learning. In this setting, from the minimax theorem and the existence of a weak learner, we get that there is a single mixture of hypotheses of \(\sum_i \alpha_i f_i\) such that the loss under every distribution in \(\mathcal{P}\) corresponds to zero training error. Thus, we can think of boosting algorithms as approximating this minimax equilibrium algorithmically. Similarly, the weak learning condition in [118] is similar in spirit to the condition above.

With the condition from Definition A.1, one can consider many frameworks for solving minimax games. One general technique is to consider two no-regret algorithms for online convex optimization to play against each other. Let us briefly look at the definition of regret in this setting.

# **Definition A.2** (No-Regret). Let \(K, A\) be convex sets. At each time, a player observes a point \(x_t \in K\) and chooses an action \(a_t \in A\). The regret of the algorithm is defined as

```
\(R_T = \max_{a \in A} \sum_{t=1}^T \langle a, x_t \rangle - \sum_{t=1}^T \langle a_t, x_t \rangle.\) (A.4)
```

Online learning is a well-studied area of machine learning with a rich set of connections to various areas in mathematics and computer science. In particular, there are frameworks in order to construct algorithms such as follow-the-perturbed leader, follow-the-regularized leader and mirror descent. Our algorithm can be seen as a version of mirror descent with the entropy regularizer and Theorem 2.1 as a version