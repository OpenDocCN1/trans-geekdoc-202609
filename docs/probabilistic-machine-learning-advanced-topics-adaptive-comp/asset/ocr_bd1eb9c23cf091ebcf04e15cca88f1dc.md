by running an RL algorithm on synthetic experiences generated from the model, or by running a planning algorithm on the model directly (Section 34.6). In practice, we often interleave the model learning and planning phases, so we can use the partially learned policy to decide what data to collect. We discuss model-based RL in more detail in Section 35.4.

# 35.1.5 Exploration-exploitation tradeoff

A fundamental problem in RL with unknown transition and reward models is to decide between choosing actions that the agent knows will yield high reward, or choosing actions whose reward is uncertain, but which may yield information that helps the agent get to parts of state-action space with even higher reward. This is called the **exploration-exploitation tradeoff**, which has been discussed in the simpler contextual bandit setting in Section 34.4. The literature on efficient exploration is huge. In this section, we briefly describe several representative techniques.

# 35.1.5.1 \(\epsilon\)-greedy

A common heuristic is to use an \(\epsilon\)-greedy policy \(\pi_\epsilon\), parameterized by \(\epsilon \in [0, 1]\). In this case, we pick the greedy action wrt the current model, \(a_t = \text{argmax}_a \hat{R}_t(s_t, a)\) with probability \(1 - \epsilon\), and a random action with probability \(\epsilon\). This rule ensures the agent's continual exploration of all state-action combinations. Unfortunately, this heuristic can be shown to be suboptimal, since it explores every action with at least a constant probability \(\epsilon / |\mathcal{A}|\).

# 35.1.5.2 Boltzmann exploration

A source of inefficiency in the \(\epsilon\)-greedy rule is that exploration occurs uniformly over all actions. The **Boltzmann policy** can be more efficient, by assigning higher probabilities to explore more promising actions:

```
\(\pi_\tau(a|s) = \frac{\exp(\hat{R}_t(s_t, a)/\tau)}{\sum_{a'} \exp(\hat{R}_t(s_t, a')/\tau)}\) (35.1)
```

where \(\tau > 0\) is a temperature parameter that controls how entropic the distribution is. As \(\tau\) gets close to 0, \(\pi_\tau\) becomes close to a greedy policy. On the other hand, higher values of \(\tau\) will make \(\pi(a|s)\) more uniform, and encourage more exploration. Its action selection probabilities can be much “smoother” with respect to changes in the reward estimates than \(\epsilon\)-greedy, as illustrated in Table 35.2.

# 35.1.5.3 Upper confidence bounds and Thompson sampling

The upper confidence bound (UCB) (Section 34.4.5) and Thompson sampling (Section 34.4.6) approaches may also be extended to MDPs. In contrast to the contextual bandit case, where the only uncertainty is in the reward function, here we must also take into account uncertainty in the transition probabilities.

As in the bandit case, the UCB approach requires to estimate an upper confidence bound for all actions’ Q-values in the current state, and then take the action with the highest UCB score. One way to obtain UCBs of the Q-values is to use **count-based exploration**, where we learn the optimal