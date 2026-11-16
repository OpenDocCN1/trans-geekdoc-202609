where \(\theta_i\) are parameters of the \(Q\)-network at iteration \(i\), \(\theta_i^-\) are parameters of the target network at iteration \(i\). The target network parameters \(\theta_i^-\) are updated periodically, and held fixed in between. We present DQN pseudo code in Algorithm 8.

```
**Input:** the pixels and the game score
**Output:** Q action value function (from which we obtain a policy and select actions)

initialize replay memory D
initialize action-value function Q with random weight \(\theta\)
initialize target action-value function \(\hat{Q}\) with weights \(\theta^- = \theta\)
**for** _episode = 1 to M_ **do**
  initialize sequence _s_<sub>1</sub> = {_x_<sub>1</sub>} and preprocessed sequence \(\phi_1 = \phi(s_1)\)
  **for** _t = 1 to T_ **do**
    following \(\epsilon\)-greedy policy, select \(a_t = \left\{\begin{array}{ll} \text{a random action} & \text{with probability } \epsilon \\ \arg\max_a Q(\phi(s_t), a; \theta) & \text{otherwise} \end{array}\right.\)
    execute action _a<sub>i</sub>_ in emulator and observe reward _r<sub>t</sub>_ and image _x_<sub>_t_+1</sub>
    set _s_<sub>_t_+1</sub> = _s<sub>t</sub>_, _a<sub>t</sub>_, _x_<sub>_t_+1</sub> and preprocess \(\phi_{t+1} = \phi(s_{t+1})\)
    store transition \((\phi_t, a_t, r_t, \phi_{t+1})\) in _D_
    // experience replay
    sample random minibatch of transitions \((\phi_j, a_j, r_j, \phi_{j+1})\) from _D_
    set \(y_j = \left\{\begin{array}{ll} r_j & \text{if episode terminates at step } j+1 \\ r_j + \gamma \max_{a'} \hat{Q}(\phi_{j+1}, a'; \theta^-) & \text{otherwise} \end{array}\right.\)
    perform a gradient descent step on \((y_j - Q(\phi_j, a_j; \theta))^2\) w.r.t. the network parameter \(\theta\)
    // periodic update of target network
    in every _C_ steps, reset \(\hat{Q} = Q\), i.e., set \(\theta^- = \theta\)
  **end**
**end**
```

# Algorithm 8: Deep Q-Network (DQN), adapted from Mnih et al. (2015)

DQN has a preprocessing step to reduce the input dimensionality. DQN also uses error clipping, clipping the update \(r + \gamma \max_{a'} Q(s', a'; \theta_i^-) - Q(s, a, \theta_i)\) in \([-1, 1]\), to help improve stability. (This is not reflected in the pseudocode.) Mnih et al. (2015) also present visualization results using t-SNE (van der Maaten and Hinton, 2008).

DQN makes a breakthrough by showing that Q-learning with non-linear function approximation, in particular, deep convolutional neural networks, can achieve outstanding results over many Atari games. Following DQN, many work improve DQN in various aspects, e.g., in the following, we will discuss over-estimation in Q-learning, prioritized experience replay, and a dueling network to estimate state value function and associated advantage function, and then combine them to estimate action value function. We also discuss an integration method called Rainbow to combine several techniques together.

In later chapters, we will discuss more extensions, like asynchronous advantage actor-critic (A3C) (Mnih et al., 2016) in Section 4.2, better exploration strategy to improve DQN (Osband et al., 2016) in Chapter 7, and hierarchical DQN in Chapter 11, etc. Experience replay uses more memory and computation for each interaction, and it requires off-policy RL algorithms. This motivates the asynchronous methods as we will discuss in Section 4.2.

See more work as the following. Ansel et al. (2017) propose to reduce variability and instability by an average of previous Q-values estimates. Farebrother et al. (2018) study generalization and regularization in DQN. Guo et al. (2014) combine DQN with offline Monte-Carlo tree search (MCTS) planning. Hausknecht and Stone (2015) propose deep recurrent Q-network (DRQN) to add recurrency to DQN for the partial observability issue in Atari games. He et al. (2017) propose to accelerate DQN by optimality tightening, a constrained optimization approach, to propagate reward faster, and to improve accuracy over DQN. Kansky et al. (2017) propose schema networks and empirically study variants of Breakout in Atari games. Liang et al. (2016) propose to replicate