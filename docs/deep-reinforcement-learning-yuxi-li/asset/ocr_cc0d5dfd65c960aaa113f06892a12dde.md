| | | algorithm |
|---|---|---|---|---|---|---|---|---|
| | | TD($\lambda$) SARSA($\lambda$) | ADP | LSTD($\lambda$) LSPE($\lambda$) | Fitted-Q | Residual Gradient | GTD($\lambda$) GQ($\lambda$) |
| issue | linear computation | $\checkmark$ | $\checkmark$ | | | $\checkmark$ | $\checkmark$ |
| | nonlinear convergent | | | | $\checkmark$ | $\checkmark$ | $\checkmark$ |
| | off-policy convergent | | | $\checkmark$ | | $\checkmark$ | $\checkmark$ |
| | model-free, online | | | $\checkmark$ | | $\checkmark$ | $\checkmark$ |
| | converges to PBE = 0 | $\checkmark$ | $\checkmark$ | $\checkmark$ | $\checkmark$ | | $\checkmark$ |

Table 2: RL Issues vs. Algorithms, adapted from Sutton (2016)

# 2.4.10 POLICY OPTIMIZATION

In contrast to value-based methods like TD learning and Q-learning, policy-based methods optimize the policy $\pi(a|s; \theta)$ (with function approximation) directly, and update the parameters $\theta$ by gradient ascent. Comparing with value-based methods, policy-based methods usually have better convergence properties, are effective in high-dimensional or continuous action spaces, and can learn stochastic policies. However, policy-based methods usually converge to local optimum, are inefficient to evaluate, and encounter high variance (Silver, 2015). Stochastic policies are important since some problems have only stochastic optimal policies, e.g., in the rock-paper-scissors game, an optimal policy for each player is to take each action (rock, paper, or scissors) with probability 1/3.

For a differentiable policy $\pi(a|s; \theta)$, we can compute the policy gradient analytically, whenever it is non-zero,

$$
\nabla_\theta \pi(a|s; \theta) = \pi(a|s; \theta) \frac{\nabla_\theta \pi(a|s; \theta)}{\pi(a|s; \theta)} = \pi(a|s; \theta) \nabla_\theta \log \pi(a|s; \theta)
$$ (24)

We call $\nabla_\theta \log \pi(a|s; \theta)$ score function, or likelihood ratio. Policy gradient theorem (Sutton et al., 2000) states that for a differentiable policy $\pi(a|s; \theta)$, the policy gradient is,

$$
\mathbb{E}_{\pi_\theta} [\nabla_\theta \log \pi(a|s; \theta) Q^{\pi_\theta}(s, a)].
$$ (25)

We omit $\pi_\theta$ in value functions below for simplicity.

REINFORCE (Williams, 1992) updates $\theta$ in the direction of

$$
\nabla_\theta \log \pi(a_t|s_t; \theta) R_t,
$$ (26)

by using return $R_t$ as an unbiased sample of $Q(s_t, a_t)$. Usually a baseline $b_t(s_t)$ is subtracted from the return to reduce the variance of gradient estimate, yet keeping its unbiasedness, to yield the gradient direction,

$$
\nabla_\theta \log \pi(a_t|s_t; \theta) (Q(a_t, s_t) - b_t(s_t)).
$$ (27)

Using $V(s_t)$ as the baseline $b_t(s_t)$, we have the advantage function,

$$
A(a_t, s_t) = Q(a_t, s_t) - V(s_t).
$$ (28)

Algorithm 6 presents the pseudo code for REINFORCE in the episodic case.

In actor-critic algorithms, the critic updates action-value function parameters, and the actor updates policy parameters, in the direction suggested by the critic. Algorithm 7 presents the pseudo code for one-step actor-critic in the episodic case.

As summarized in Silver (2015), policy gradient may take various forms: $\nabla_\theta \log \pi(a|s; \theta) R_t$ for REINFORCE, $\nabla_\theta \log \pi(a|s; \theta) Q(s, a; w)$ for Q actor-critic, $\nabla_\theta \log \pi(a|s; \theta) A(s, a; w)$ for advantage actor-critic, $\nabla_\theta \log \pi(a|s; \theta) \delta$ for TD actor-critic, $\nabla_\theta \log \pi(a|s; \theta) \delta e$ for TD($\lambda$) actor-critic, and $G_\theta w$ for natural gradient decent, where $G_\theta = \mathbb{E}_{\pi_\theta} [\nabla_\theta \log \pi(a|s; \theta) \nabla_\theta \log \pi(a|s; \theta)^T]$ is the Fisher information matrix; and the critic may use Monte Carlo or TD learning for policy evaluation to estimate the value functions $Q, A$ or $V$.