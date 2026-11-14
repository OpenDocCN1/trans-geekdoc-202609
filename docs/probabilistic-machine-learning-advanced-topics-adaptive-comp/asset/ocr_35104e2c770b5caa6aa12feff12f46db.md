# 34.4.1 Types of bandit

In a multi-armed bandit problem (MAB) there is an agent (decision maker) that can choose an action from some policy \(a_t \sim \pi_t\) at each step, after which it receives a reward sampled from the environment, \(r_t \sim p_R(a_t)\), with expected value \(R(s, a) = \mathbb{E}[R|a]\).

We can think of this in terms of an agent at a casino who is faced with multiple slot machines, each of which pays out rewards at a different rate. A slot machine is sometimes called a one-armed bandit, so a set of \(K\) such machines is called a multi-armed bandit; each different action corresponds to pulling the arm of a different slot machine, \(a_t \in \{1, \dots, K\}\). The goal is to quickly figure out which machine pays out the most money, and then to keep playing that one until you become as rich as possible.

We can extend this model by defining a contextual bandit, in which the input to the policy at each step is a randomly chosen state or context \(s_t \in \mathcal{S}\). The states evolve over time according to some arbitrary process, \(s_t \sim p(s_t|s_{1:t-1})\), independent of the actions of the agent. The policy now has the form \(a_t \sim \pi_t(a_t|s_t)\), and the reward function now has the form \(r_t \sim p_R(r_t|s_t, a_t)\), with expected value \(R(s, a) = \mathbb{E}[R|s, a]\). At each step, the agent can use the observed data, \(\mathcal{D}_{1:t}\) where \(\mathcal{D}_t = (s_t, a_t, r_t)\), to update its policy, to maximize expected reward.

In the finite horizon formulation of (contextual) bandits, the goal is to maximize the expected cumulative reward:

```
J \triangleq \sum_{t=1}^T \mathbb{E}_{p_R(r_t|s_t, a_t) \pi_t(a_t|s_t) p(s_t|s_{1:t-1})} [r_t] = \sum_{t=1}^T \mathbb{E}[r_t]
```

(Note that the reward is accrued at each step, even while the agent updates its policy; this is sometimes called "earning while learning".) In the infinite horizon formulation, where \(T = \infty\), the cumulative reward may be infinite. To prevent \(J\) from being unbounded, we introduce a discount factor \(0 < \gamma < 1\), so that

```
J \triangleq \sum_{t=1}^\infty \gamma^{t-1} \mathbb{E}[r_t]
```

The quantity \(\gamma\) can be interpreted as the probability that the agent is terminated at any moment in time (in which case it will cease to accumulate reward).

Another way to write this is as follows:

```
J = \sum_{t=1}^\infty \gamma^{t-1} \mathbb{E}[r_t] = \sum_{t=1}^\infty \gamma^{t-1} \mathbb{E}\left[ \sum_{a=1}^K R_a(s_t, a_t) \right]
```

where we define

```
R_a(s_t, a_t) = \begin{cases} R(s_t, a) & \text{if } a_t = a \\ 0 & \text{otherwise} \end{cases}
```

3. This is known as a stochastic bandit. It is also possible to allow the reward, and possibly the state, to be chosen in an adversarial manner, where nature tries to minimize the reward of the agent. This is known as an adversarial bandit.