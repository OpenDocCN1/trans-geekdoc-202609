the explicit coding of the transition matrix. Iterative approaches will be used in all further methods discussed later. Note that we have only used three iterations to converge on the correct solution. Here we will set the number of iterations by hand, in practice we iterate until the changes in the values are sufficiently small.

# 10.2.2 Policy iteration

The goal of the RL is of course to find the policy that maximizes the return. So far we have only used a method to calculate the value for a given policy. However, we can start with an arbitrary policy and use the corresponding value function to improve the policy by defining a new policy which is given by the actions from each state that gives us the best return value,

```
Policy iteration: $\pi(s) \leftarrow \arg_{a} Q^*(s,a)$. (10.14)
```

For the new policy, we can then calculate the corresponding Q-function and use this Q-function to improve the policy again. Iterating over the policy gives us

```
Optimal policy: $\pi^*(s)$. (10.15)
```

The corresponding value function is $Q^*$. In the maze we can see that the maximum in each column of the Q-matrix is the policy we started with. This is the optimal policy, as we stated earlier.
The corresponding code for our maze example is

+   Listing 10.11 RL.ipynb (Part 11)

```
print('-->Policy_iteration')
Q = np.zeros([5,2])
policy = calc_policy(Q)
for iter in range(3):
  for s in range(5):
    for a in range(-1,2,2):
      act = np.int(policy[tau(s,a)])
      Q[s,idx] = rho(s,a)+gamma*Q(tau(s,a),act)
  policy = calc_policy(Q)

print('Q.values:\n',np.transpose(Q))
print('policy:\n',np.transpose(policy))\n
> Policy iteration
Q values:
[[0. 1. 0.5 0.5 0. ]
[0. 0.5 1. 2. 0. ]
policy:
[0. -1 1 1 0]]
```

leading to the correct result. Note that in this example, we could and should iterate three times over the policies. In principle, order to converge to a stable estimate for this $Q^*$. However, the improvements will lead very quickly to a stable state, at least in this simple example.