
by running an RL algorithm on synthetic experiences generated from the model, or by running a planning algorithm on the model directly (Section 34.6). In practice, we often interleave the model learning and planning phases, so we can use the partially learned policy to decide what data to collect. We discuss model-based RL in more detail in Section 35.4.

## 35.1.5 Exploration-exploitation tradeoff

A fundamental problem in RL with unknown transition and reward models is to decide between choosing actions that the agent knows will yield high reward, or choosing actions whose reward is uncertain, but which may yield information that helps the agent get to parts of state-action space with even higher reward. This is called the **exploration-exploitation tradeoff**, which has been discussed in the simpler contextual bandit setting in Section 34.4. The literature on efficient exploration is huge. In this section, we briefly describe several representative techniques.

### 35.1.5.1 \(\epsilon\)-greedy

A common heuristic is to use an \(\epsilon\)-greedy policy \(\pi_\epsilon\), parameterized by \(\epsilon \in [0, 1]\). In this case, we pick the greedy action wrt the current model, \(a_t = \text{argmax}_a \hat{R}_t(s_t, a)\) with probability \(1 - \epsilon\), and a random action with probability \(\epsilon\). This rule ensures the agent's continual exploration of all state-action combinations. Unfortunately, this heuristic can be shown to be suboptimal, since it explores every action with at least a constant probability \(\epsilon / |\mathcal{A}|\).

### 35.1.5.2 Boltzmann exploration

A source of inefficiency in the \(\epsilon\)-greedy rule is that exploration occurs uniformly over all actions. The **Boltzmann policy** can be more efficient, by assigning higher probabilities to explore more promising actions:

```
\(\pi_\tau(a|s) = \frac{\exp(\hat{R}_t(s_t, a)/\tau)}{\sum_{a'} \exp(\hat{R}_t(s_t, a')/\tau)}\) (35.1)
```

where \(\tau > 0\) is a temperature parameter that controls how entropic the distribution is. As \(\tau\) gets close to 0, \(\pi_\tau\) becomes close to a greedy policy. On the other hand, higher values of \(\tau\) will make \(\pi(a|s)\) more uniform, and encourage more exploration. Its action selection probabilities can be much “smoother” with respect to changes in the reward estimates than \(\epsilon\)-greedy, as illustrated in Table 35.2.

### 35.1.5.3 Upper confidence bounds and Thompson sampling

The upper confidence bound (UCB) (Section 34.4.5) and Thompson sampling (Section 34.4.6) approaches may also be extended to MDPs. In contrast to the contextual bandit case, where the only uncertainty is in the reward function, here we must also take into account uncertainty in the transition probabilities.

As in the bandit case, the UCB approach requires to estimate an upper confidence bound for all actions’ Q-values in the current state, and then take the action with the highest UCB score. One way to obtain UCBs of the Q-values is to use **count-based exploration**, where we learn the optimal

| \(\hat{R}(s, a_1)\) | \(\hat{R}(s, a_2)\) | \(\pi_\epsilon(a|s_1)\) | \(\pi_\epsilon(a|s_2)\) | \(\pi_\tau(a|s_1)\) | \(\pi_\tau(a|s_2)\) |
|---|---|---|---|---|---|
| 1.00 | 9.00 | 0.05 | 0.95 | 0.00 | 1.00 |
| 4.00 | 6.00 | 0.05 | 0.95 | 0.12 | 0.88 |
| 4.90 | 5.10 | 0.05 | 0.95 | 0.45 | 0.55 |
| 5.05 | 4.95 | 0.95 | 0.05 | 0.53 | 0.48 |
| 7.00 | 3.00 | 0.95 | 0.05 | 0.98 | 0.02 |
| 8.00 | 2.00 | 0.95 | 0.05 | 1.00 | 0.00 |

Table 35.2: Comparison of \(\epsilon\)-greedy policy (with \(\epsilon = 0.1\)) and Boltzmann policy (with \(\tau = 1\)) for a simple MDP with 6 states and 2 actions. Adapted from Table 4.1 of [GK19].

Q-function with an **exploration bonus** added to the reward in a transition \((s, a, r, s')\):

```
\(\tilde{r} = r + \alpha / \sqrt{N_{s,a}}\) (35.2)
```

where \(N_{s,a}\) is the number of times action \(a\) has been taken in state \(s\), and \(\alpha \ge 0\) is a weighting term that controls the degree of exploration. This is the approach taken by the **MBIE-EB** method [SL08] for finite-state MDPs, and in the generalization to continuous-state MDPs through the use of hashing [Bel+16]. Other approaches also explicitly maintain uncertainty in state transition probabilities, and use that information to obtain UCBs. Examples are **MBIE** [SL08], **UCRL2** [JOA10], and **UCBVI** [AOM17], among many others. Thompson sampling can be similarly adapted, by maintaining the posterior distribution of the reward and transition model parameters. In finite-state MDPs, for example, the transition model is a categorical distribution conditioned on the state. We may use the conjugate prior of Dirichlet distributions (Section 3.4) for the transition model, so that the posterior distribution can be conveniently computed and sampled from. More details on this approach are found in [Rus+18]. Both UCB and Thompson sampling methods have been shown to yield efficient exploration with provably strong regret bounds (Section 34.4.7) [JOA10], or related PAC bounds [SLL09; DLB17], often under necessary assumptions such as finiteness of the MDPs. In practice, these methods may be combined with function approximation like neural networks and implemented approximately.

### 35.1.5.4 Optimal solution using Bayes-adaptive MDPs

The Bayes optimal solution to the exploration-exploitation tradeoff can be computed by formulating the problem as a special kind of POMDP known as a **Bayes-adaptive MDP** or **BAMDP** [Duf02]. This extends the Gittins index approach in Section 34.4.4 to the MDP setting. In particular, a BAMDP has a **belief state** space, \(\mathcal{B}\), representing uncertainty about the reward model \(p_R(r|s, a, s')\) and transition model \(p_T(s'|s, a)\). The transition model on this augmented MDP can be written as follows:

```
\(T^+(s_{t+1}, b_{t+1}|s_t, b_t, a_t, r_t) = T^+(s_{t+1}|s_t, a_t, b_t)T^+(b_{t+1}|s_t, a_t, r_t, s_{t+1})\) (35.3)
\(= \mathbb{E}_{b_t} [T(s_{t+1}|s_t, a_t)] \times \mathbb{I}(b_{t+1} = p(R, T|\mathbf{h}_{t+1}))\) (35.4)
```

where \(\mathbb{E}_{b_t} [T(s_{t+1}|s_t, a_t)]\) is the posterior predictive distribution over next states, and \(p(R, T|\mathbf{h}_{t+1})\) is the new belief state given \(\mathbf{h}_{t+1} = (s_{1:t+1}, a_{1:t+1}, r_{1:t+1})\), which can be computed using Bayes' rule.

Similarly, the reward function for the augmented MDP is given by

$$R^+(r|s_t, b_t, a_t, s_{t+1}, b_{t+1}) = \mathbb{E}_{b_{t+1}} [R(s_t, a_t, s_{t+1})]$$ (35.5)

For small problems, we can solve the resulting augmented MDP optimally. However, in general this is computationally intractable. [Gha+15] surveys many methods to solve it more efficiently. For example, [KN09] develop an algorithm that behaves similarly to Bayes optimal policies, except in a provably small number of steps; [GSD13] propose an approximate method based on Monte Carlo rollouts. More recently, [Zin+20] propose an approximate method based on meta-learning (Section 19.6.4), in which they train a (model-free) policy for multiple related tasks. Each task is represented by a task embedding vector m, which is inferred from $h_t$ using a VAE (Section 21.2). The posterior $p(m|h_t)$ is used as a proxy for the belief state $b_t$, and the policy is trained to perform well given $s_t$ and $b_t$. At test time, the policy is applied to the incrementally computed belief state; this allows the method to infer what kind of task this is, and then to use a pre-trained policy to quickly solve it.

## 35.2 Value-based RL

In this section, we assume the agent has access to samples from $p_T$ and $p_R$ by interacting with the environment. We will show how to use these samples to learn optimal $Q$-functions from which we can derive optimal policies.

### 35.2.1 Monte Carlo RL

Recall that $Q_\pi(s, a) = \mathbb{E} [G_t | s_t = s, a_t = a]$ for any $t$. A simple way to estimate this is to take action $a$, and then sample the rest of the trajectory according to \(\pi\), and then compute the average sum of discounted rewards. The trajectory ends when we reach a terminal state, if the task is episodic, or when the discount factor \(\gamma^t\) becomes negligibly small, whichever occurs first. This is the Monte Carlo estimation of the value function.

We can use this technique together with policy iteration (Section 34.6.2) to learn an optimal policy. Specifically, at iteration \(k\), we compute a new, improved policy using \(\pi_{k+1}(s) = \text{argmax}_a Q_k(s, a)\), where \(Q_k\) is approximated using MC estimation. This update can be applied to all the states visited on the sampled trajectory. This overall technique is called Monte Carlo control.

To ensure this method converges to the optimal policy, we need to collect data for every (state, action) pair, at least in the tabular case, since there is no generalization across different values of \(Q(s, a)\). One way to achieve this is to use an \(\epsilon\)-greedy policy. Since this is an on-policy algorithm, the resulting method will converge to the optimal \(\epsilon\)-soft policy, as opposed to the optimal policy. It is possible to use importance sampling to estimate the value function for the optimal policy, even if actions are chosen according to the \(\epsilon\)-greedy policy. However, it is simpler to just gradually reduce \(\epsilon\).

### 35.2.2 Temporal difference (TD) learning

The Monte Carlo (MC) method in Section 35.2.1 results in an estimator for \(Q_\pi(s, a)\) with very high variance, since it has to unroll many trajectories, whose returns are a sum of many random rewards generated by stochastic state transitions. In addition, it is limited to episodic tasks (or finite horizon
