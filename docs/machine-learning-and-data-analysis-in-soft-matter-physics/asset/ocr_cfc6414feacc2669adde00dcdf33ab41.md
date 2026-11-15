![](bbox=[0.19, 0.1, 0.82, 0.4])

Figure 9: Graphical representation of the multi-objective reward function.

# Transition Probability Function

Given the state, $s_v$, at the current time step, the agent needs to select the action, $a_v$, within the action space, that will lead to the largest value, $Q(s_t, a_t)$, where $Q(s_t, a_t)$, is defined as the total expected future reward if $a_t$ is chosen. The transition probability function, also called the value function, maps state-action tuples, $(s_t, a_t)$, to values for each action. If $Q(s_t, a_t)$, is known for all actions at a given state, then selecting the argmax($a_t$) is the best action. However, even for a simple representation of the TO environment with 6x6 topologies, the number of possible states for a single load case is large (≈6.87×10^10) which makes the value function challenging to model. Therefore, $Q(s_t, a_t)$ is approximated using a deep neural network (DNN). The value function is found using the Double Q-learning algorithm , as shown in Eq. (9):

```
$Q(s_t, a_t) = r(s_t, a_t) + \gamma max_a Q(s_{t+1}, argmax Q(s_{t+1}, a_t))$
(9)
```

where $r(s_v, a_v)$ is the reward for taking the action, $a_v$ at the current state, $s_v$ and $G$ is the future reward discount factor. Double Q learning uses two DNN models, a main and an auxiliary model. The main model selects the action to take by predicting the action with the largest value, $Q(s_t, a_t)$. The auxiliary model predicts the value of the next state if that maximum value action was taken, $max_a Q'(s_{t+1}, argmax Q(s_{t+1}, a_t))$. The auxiliary model helps to address the overestimation of future value,