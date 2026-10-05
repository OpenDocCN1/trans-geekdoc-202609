section on temporal difference. This final algorithm is to use an alternative way to estimate the value function using an off-policy approach for the estimation step from each visited state. That is, we check all actions from the state that we evaluate and update the value function with the maximal expected return.

**Q-learning:** $Q_{i+1}(s_i, a_i) = Q_i(s_i, a_i) + \alpha \left[r_{i+1} + \gamma \max_{a'} Q_i(s_{i+1}, a') - Q_i(s_i, a_i)\right]$
(10.22)

We have employ to explore the environment which follows the optimal estimated policy, with alone $e$-greedy or a softmax exploration strategy. The corresponding code for the Q-learning is

+   - Q-Learning:
Q values:
[[0. 1. 0.5 0.5. 0.]
 [0. 0.5 1. 2. 0.]]
policy:
[[0 -1 0]]

# 10.3.2 TD($\lambda$)

The example of the maze in the previous section has shown that the expectation of rewards backwards in each episode which requires multiple repetitions of the episodes to evaluate the value function. The reason for this is that we only give credit for making a step to a valuable state to the previous step and hence only update the corresponding value function. A different approach is to keep track of states which have been rewarded and assign the credit to each step that was visited. However, because we discount the reward proportional to the time it takes to get to the rewarded state, we also need to take this into account.