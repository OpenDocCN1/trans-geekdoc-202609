C steps. Temporal Ensemble method is suitable for the algorithms which use a target network for updating and training. Temporal ensemble uses the previous K learned networks to produce the value estimate and builds up K ∈N complete networks with K distinct memory buffers. The recent Q-value function is trained according to its own target network Q(s, a; θt). So each one of Q-value functions Q1, Q2,..., Qk represents temporally extended estimate of Q- value function.

Note that the more recent target network is likely to be more accurate at the beginning of the training and the accuracy of the target networks is increasing as the training goes on. So we denote a learning rate parameter λ ∈ (0, 1] here for target network. The weight of ith target network is wi = λ^(i-1) / Σ λ^(i-1).

So the learned Q-value function by temporal ensemble can be described as follows:

$$Q^T(s, a; \theta) = \sum_{i=1}^N \left( \frac{\lambda^{i-1} Q_i(s, a; \theta_i)}{\sum_{i=1}^N \lambda^{i-1}} \right).$$ (4)

As \(\lim_{\lambda \to 1} \lambda^{i-1} / \sum_{i=1}^N \lambda^{i-1} = 1/N\), we can see that the target networks have the same weights when \(\lambda\) equals 1. Tis formula indicates that the closer the target networks are, the greater the target networks' weight is. As target networks become more accurate, their weights become equal. The loss function remains the same as in DQN and so does the parameter update equation:

$$y_i^T = r_t + \gamma \max_{a'} \sum_{i=1}^N w_i Q^T (s', a'; \theta^T),$$ (5)

$$\theta_{t+1} \leftarrow \theta_t + \alpha \left( y_i^T - Q \left( s_t, a_t; \theta_t \right) \right) \nabla_\theta Q \left( s_t, a_t; \theta_t \right).$$

In every iteration, the parameters of the oldest ones are removed from the target network buffer and the newest ones are added to the buffer. Note that the Q-value functions are inaccurate at the beginning of training. So the parameter \(\lambda\) may be a function of time and even the state space.

# Ensemble of Target Values

The traditional ensemble reinforcement learning algorithms maintain multiple tabular algorithms in memory space [4, 16], and majority voting, rank voting, Boltzmann addition, and so forth are used to combine these