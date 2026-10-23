| $\hat{R}(s,a_1)$ | $\hat{R}(s,a_2)$ | $\pi_\epsilon(a|s_1)$ | $\pi_\epsilon(a|s_2)$ | $\pi_\tau(a|s_1)$ | $\pi_\tau(a|s_2)$ |
|---|---|---|---|---|---|
| 1.00 | 9.00 | 0.05 | 0.95 | 0.00 | 1.00 |
| 4.00 | 6.00 | 0.05 | 0.95 | 0.12 | 0.88 |
| 4.90 | 5.10 | 0.05 | 0.95 | 0.45 | 0.55 |
| 5.05 | 4.95 | 0.95 | 0.05 | 0.53 | 0.48 |
| 7.00 | 3.00 | 0.95 | 0.05 | 0.98 | 0.02 |
| 8.00 | 2.00 | 0.95 | 0.05 | 1.00 | 0.00 |

*Table 8.4: Comparison of ε-greedy policy (with ε = 0.1) and Boltzmann policy (with τ = 1) for a simple MDP with 6 states and 2 actions. Adapted from Table 4.1 of [GK19].*

# 8.3.8.3 Exploration bonuses

Exploration bonus is another simple yet sometimes effective heuristic. The idea is to add a bonus term, $b_t(s_t, a)$, to the reward estimate of action $a$, and then choose a greedy action accordingly: $a_t = \arg\max_a \hat{R}_t(s_t,a) + b_t(s_t, a)$. Typically, the bonus term is large for an action $a$ if it has not been chosen many times (i.e., $N_t(a)$ is small), and decays to 0 as $N_t(a)$ becomes large. These bonuses therefore encourage exploration of rarely selected actions. They are also related to the idea of **intrinsic motivation**, in which the agent performs actions in order to learn about the world, even if there is no external reward (see e.g., [AMH19] for a review).

# 8.4 Discussion

In this section, we discuss some “bigger picture” topics related to the decision theoretic approach to ML, which is the foundation of most approaches to AI (see e.g., [RN19]), and the approach we adopt in this book.

# 8.4.1 The separation principle and its limits

In Bayesian decision theory, we compute our beliefs about the world state, $p(h|x)$, without any knowledge of the loss function (and hence the ultimate “task”). We only use the loss function to decide how to act after we have finished performing inference. In control theory, this is known as the **separation principle**, and is provably optimal under many conditions (see e.g., [GL13]).

However, the separation of inference from decision making can be suboptimal in cases where we cannot perform exact inference [LJHG11; AS17]. For this reason, the recent trend in deep learning is towards **end-to-end learning**, in which we learn a mapping directly from input to optimal action, i.e., we learn policies of the form $a = \pi(x;\theta)$, bypassing explicit estimation of the hidden state.