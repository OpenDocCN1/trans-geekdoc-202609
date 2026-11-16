DQN with shallow features w.r.t. spatial invariance, non-Markovian features, and object detection, together with basic tile-coding features. Zahavy et al. (2018) study action elimination.

See a blog at `https://deepmind.com/research/dqn/`. See Chapter 16 in Sutton and Barto (2018) for a detailed and intuitive description of Deep Q-Network. See Chapter 11 in Sutton and Barto (2018) for more details about the deadly triad.

# DOUBLE DQN

van Hasselt et al. (2016) propose Double DQN (D-DQN) to tackle the over-estimate problem in Q-learning (van Hasselt, 2010). In standard Q-learning, as well as in DQN, the parameters are updated as follows:

```
$$\theta_{t+1} = \theta_t + \alpha(y_t^Q - Q(s_t, a_t; \theta_t))\nabla_{\theta_t} Q(s_t, a_t; \theta_t), \quad (31)$$
```

where

```
$$y_t^Q = r_{t+1} + \gamma \max_a Q(s_{t+1}, a; \theta_t), \quad (32)$$
```

so that the max operator uses the same values to both select and evaluate an action. As a consequence, it is more likely to select over-estimated values, and results in over-optimistic value estimates. van Hasselt et al. (2016) propose to evaluate the greedy policy according to the online network, but to use the target network to estimate its value. This can be achieved with a minor change to the DQN algorithm, replacing $y_t^Q$ with

```
$$y_t^{D-DQN} = r_{t+1} + \gamma Q(s_{t+1}, \arg \max_a Q(s_{t+1}, a; \theta_t); \theta_t^-), \quad (33)$$
```

where $\theta_t$ is the parameter for online network and $\theta_t^-$ is the parameter for target network. For reference, $y_t^Q$ can be written as

```
$$y_t^Q = r_{t+1} + \gamma Q(s_{t+1}, \arg \max_a Q(s_{t+1}, a; \theta_t); \theta_t). \quad (34)$$
```

# PRIORITIZED EXPERIENCE REPLAY

In DQN, experience transitions are uniformly sampled from the replay memory, regardless of the significance of experience. Schaul et al. (2016) propose to prioritize experience replay, so that important experience transitions can be replayed more frequently, to learn more efficiently. The importance of experience transitions are measured by TD errors. The authors design a stochastic prioritization based on the TD errors, using importance sampling to avoid the bias in the update distribution. The authors use prioritized experience replay in DQN and D-DQN, and improve their performance on Atari games. In planning, prioritized sweeping (Moore and Atkeson, 1993) is used to set priorities for state action pairs according to TD errors to achieve more efficient updates.

# DUELING ARCHITECTURE

Wang et al. (2016b) propose the dueling network architecture to estimate state value function $V(s)$ and the associated advantage function $A(s, a)$, and then combine them to estimate action value function $Q(s, a)$, to converge faster than Q-learning. In DQN, a CNN layer is followed by a fully connected (FC) layer. In dueling architecture, a CNN layer is followed by two streams of FC layers, to estimate value function and advantage function separately; then the two streams are combined to estimate action value function. Usually we use the following to combine $V(s)$ and $A(s, a)$ to obtain $Q(s, a)$,

```
$$Q(s, a; \theta, \alpha, \beta) = V(s; \theta, \beta) + (A(s, a; \theta, \alpha) - \max_{a'} A(s, a'; \theta, \alpha)) \quad (35)$$
```

where $\alpha$ and $\beta$ are parameters of the two streams of FC layers. Wang et al. (2016b) propose to replace max operator with average as below for better stability,

```
$$Q(s, a; \theta, \alpha, \beta) = V(s; \theta, \beta) + (A(s, a; \theta, \alpha) - \frac{1}{|\mathcal{A}|} A(s, a'; \theta, \alpha)) \quad (36)$$
```

Dueling architecture implemented with D-DQN and prioritized experience replay improves previous work, DQN and D-DQN with prioritized experience replay, on Atari games.