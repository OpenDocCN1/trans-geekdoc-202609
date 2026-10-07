State—A mathematical representation of what the agent is noticing at some particular time in the environment.
Action—This is the input which the agent provides to the environment and calculated by doing an application policy to the present state.
Reward—A responsive signal from the environment reflecting the agent's good performance to the goals of the game.

The Bellman Equation is given by:

```
V(s) = max_a [R(s, a) + γV(s')]
```

V(s)—this is the value for being in a particular state
V(s')—this is the value of being in the next state after taking an action
y—this is the discount factor
max—this is the value we want the maximum of action (which maximizes the value) so that the agent is in the optimal solution.

# 6.3 Deep Q-Learning

Deep Q-Learning algorithm is one of the most important concepts in Reinforcement Learning [4]. Basically, in deep Q Learning, we take the help of a neural network to guess the Q-value function. The state is considered as the input and the Q-value of every possible action is generated as the output [5]. The comparison between Q-Learning & deep Q-Learning is explained properly in the diagram below-
So, there are some steps involved in reinforcement learning using Q-Learning networks—

+   i) The user stores the past experience in memory.
ii) The maximum output of the Q-Network decides the next action.
iii) The loss function is the mean squared error of (the predicted Q-value and the target Q-value) - Q*. Actually, it is a regression problem.

```
Q(Sₜ, Aₜ) ← Q(Sₜ, Aₜ) + ∞ [Sₜ₊₁ + γ max_a Q(Sₜ₊₁, a) ] - Q(Sₜ, Aₜ)
```