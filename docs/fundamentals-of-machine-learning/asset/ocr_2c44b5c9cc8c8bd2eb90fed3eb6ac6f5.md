Model-free reinforcement learning | 217

# 10.3 Model-free reinforcement learning

# 10.3.1 Temporal difference method for value iteration

Above we assumed a model of the environment by an explicit knowledge of the functions $	au(s, a)$ and $ho(s, a)$. While the Bellman equations have been known since the 1950s, their usefulness has been limited by the fact that finding the environmental functions can be difficult. This is one of the reasons that such RL techniques have not gained more applications at present. We could use modeling techniques and sample these functions with machine learning techniques and then use model-based RL as described above to find the optimal policy. For example, we can use demonstrations of actions by a teacher as a form of supervised learning for the models. As mentioned earlier, supervised learning is commonly called imitation learning in the context of robotics and RL. We are not following this line of thought but will instead consider sampling directly with reinforcement learning by exploring the environment. This approach has helped apply RL to many applications. We do not need to know the environmental functions, this approach is called model-free.

We will start with a version for a specific policy by choosing a policy and estimate the $Q$-function for this policy. As the iterative methods earlier, we want to minimize the difference between the left- and right-hand sides of the Bellman equation. But we can not connect the right-hand side since we do not know the transition and reward function. However, we can just take a step according to our policy $u = \pi(s)$ and observe a reward $r_{i+1}$ and the next state $s_{i+1}$. Now, since this is only one sample, we use this as an update of the value function only with a small learning rate $\alpha$. The following algorithm is

```
SARSA: $Q_{i+1}(s_i, a_i) = Q_i(s_i, a_i) + \alpha [(r_{i+1} + \gamma Q_i(s_{i+1}, a_{i+1}) - Q_i(s_i, u_i)]$.
(10.19)
```

The name comes from fact that we are in a state where we take an action and observe a reward and then go to the next state and take action:

```
$s \rightarrow r \rightarrow s \rightarrow a$.
```

The term in square brackets on the right-hand side of Eqn10.19 is called the temporal difference because it is the difference between the expected value at some point and the next estimate from the actual reward and the following estimate at the next evaluation point. Note that we are following the policy, and the methods is therefore an on-policy method.

The next step is to use the estimate of the $Q$-function to improve policy. However, since we are mainly interested in the optimal policy, we should improve the policy by taking the steps that maximizes the reward. However, one problem in this scheme is we have to estimate the $Q$-values by sampling so that we have to make sure we trade off exploitation with exploration. A common way to choose the policy in this scheme is

```
$\epsilon$-greedy policy: $p (\arg \max Q(s, a)) = 1 - \epsilon$.
(10.20)
```

We are really evaluating the optimal policy that requires us to make the exploration 0 at the end, $\epsilon \rightarrow 0$.