# 222 | Reinforcement learning

Listing 10.15 RL.ipynb (Part 15)

```
print('-->TD(lambda)_for_Q-learning : ')

Q=np.zeros([5,2])
alpha=1
error = []
eligibility=np.zeros([5,2])
lam=0.7

for trial in range(200):
    policy=calc.policy(Q)
    s=2
    for t in range(0,5):
        if np.random.random()<0.1: a=-np.random #greedy
        TD=Q[s,a]+gamma+max(Q[tau(s,a),0],Q[tau(s,a),1])-Q[s,a]
        idx=a
        eligibility[s,idx]+=gamma
        eligibility[s,idx(a)]=1
        for ai in range(2):
            Q[si,ai]=Q[si,ai]+alpha*TD+eligibility[si, ai]
Q[0]=Q[0:4]=0
error.append(np.sum(np.sum(np.abs(np.subtract(Q,Q)))))

print('Values:\n',', np.transpose(Q))
print('Policy:\n\n', np.transpose(policy))
plt.plot(error, 'r')
plt.xlabel('iteration'); plt.ylabel('error')
```

--> TD(lambda) for Q-learning

| | | | | |
|---|---|---|---||}{
| Q: | 0.9999999 | 0.9999994 | 0.9998045 | 0. | |
| 0. | 0.25 | 1. | 2. | 0. | |
| policy: | | | | |
| -1 | 1 | 0 | | |

TD(lambda) made famous by Gerald Tesauro in early 1990s for achieving human level performance in playing backgammon. In addition, Tesauro's solution used neural networks as a function approximator which is important for capturing the high-dimensional state-action space. This will be discussed in the next section.

# 10.4 Deep reinforcement learning

# 10.4.1 Value-function approximation with ANN

Up to this point we have outlined the basic ideas behind reinforcement learning algorithms. We will now move on to an important topic to scale these ideas to real-world applications. The previous method we used tables for the values for functions. For example, the value function in the above programs were look-up tables or arrays in programming terms that specified the value function for each discrete state and action. Corresponding, this lead to tables for the policy. Such algorithms are now commonly referred to as tabular RL. The problem with this approach is that