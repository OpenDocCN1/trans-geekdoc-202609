Iterative Update:

Follow these steps repeatedly until convergence:

+   First, for each state s ∋ S:

+   Compute the action-value function for each action a ∊ A:

![](bbox=[0.2, 0.28, 0.75, 0.32])

The value function can be updated by selecting the action that maximizes the action-value function:

Convergence Check:

![](bbox=[0.35, 0.47, 0.75, 0.5])

In order to attain the maximum number of iterations, keep repeating step 2 until the change in the value estimations becomes minimal.

The value iteration algorithm utilizes the Bellman equation, which states that the value of a state is equal to the maximum expected return achievable from that state:

![](bbox=[0.35, 0.66, 0.75, 0.69])

Here, the ideal state-value function is represented by V∗(s), while the ideal action-value function is represented by Q∗(s, a).

The algorithm modifies the value function after each iteration using the most recent estimates of the action-value function. When calculating the action-value function, the transition probabilities T(s, a, s) and immediate rewards R(s, a, s) linked to the state-action pairs are taken into consideration. The discount factor is used to rank future benefits [4].

# 5.4 Policy iteration

By repeatedly completing the stages of policy evaluation and policy improvement, the iterative technique known as “policy iteration” is used to solve MDPsMDPs. By revis-ing the policy until convergence, it seeks to identify the best course of action [5]. Here is a thorough description of policy iteration:

Initialization:

Initialize the policy π arbitrarily for all states s ∋ S.

Policy evaluation:

Conduct a policy evaluation to calculate the value function Vπ(s) for the present policy π. Continue iterating until the value estimations converge: