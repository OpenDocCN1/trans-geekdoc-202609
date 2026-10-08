# 3.3 Actor-Critic Methods and Policy Gradient

In the used actor-critic approach, the Q value is learned by the “critic network,” which estimates the value function in form of the state-value Eq. (2) and the action-value Eq. (3).

The “actor network” updates the policy distribution in the direction suggested by the “critic network” using policy gradients. For this, both critic and actor functions are parameterized with neural networks over the augmented embedding space.

```
$V_{\pi}(s) = \sum_{a} \pi(a|s) \sum_{s'} P^{sa}(r(s,a) + \gamma V_{\pi}(s'))$
```

```
$Q_{\pi}(s,a) = \sum_{s'} P^{sa}(r(s,a) + \gamma \sum_{a'} \pi(a'|s') Q_{\pi}(s',a'))
```

Policy gradients [28] are used to optimize the actor's probability distribution of embedding space displacement amounts. The goal is to learn a policy (π) that maximizes the cumulative future reward from current time t to terminal time T. If r(t+1) is the reward for performing action a(t) at state s(t),

```
$r(t+1) = R(s(t), a(t))
```

+   1. Reward and performance prediction: To learn the incremental improvement achieved when modifying the network. A target domain of supervised classification, a direct way to capture reward is in terms of the expected accuracy of the target network after modification. To reduce the need for re-training target networks and to allow planning, the architecture includes a performance prediction [20] component that predicts network performance using previously trained problems. To limit task-specific training, the input to this network again contains, besides the network embedding, problem specific features to facilitate generalization across tasks.

# 3.4 Twin-Delayed Deep Deterministic Policy Gradient (TD3)

The twin-delayed deterministic policy gradient (TD3, [5]) algorithm is a model-free, off-policy reinforcement learning method. It is an extension of DDPG (Deep Deterministic Policy Gradient) algorithm [29] and reduces value function estimation bias and overfitting spikes by using two function learners and utilizing delayed actor updates. The basic operation of TD3 is shown in Fig. 3.

TD3 agents use a deterministic policy actor π(S) and one or more Q-value function critics Q(S, A). During training, a TD3 agent utilizes a circular experience