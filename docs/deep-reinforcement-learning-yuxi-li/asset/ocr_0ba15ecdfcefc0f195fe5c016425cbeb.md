```
Input: policy \(\pi(a|s, \theta)\), \(\hat{v}(s, w)\)
Parameters: step sizes, \(\alpha > 0, \beta > 0\)
Output: policy \(\pi(a|s, \theta)\)

initialize policy parameter \(\theta\) and state-value weights \(w\)
for true do
    generate an episode \(s_0, a_0, r_1, \cdots, s_{T-1}, a_{T-1}, r_T\), following \(\pi(\cdot|\cdot, \theta)\)
    for each step \(t\) of episode \(0, \cdots, T-1\) do
        \(G_t \leftarrow\) return from step \(t\)
        \(\delta \leftarrow G_t - \hat{v}(s_t, w)\)
        \(w \leftarrow w + \beta \delta \nabla_w \hat{v}(s_t, w)\)
        \(\theta \leftarrow \theta + \alpha \gamma^t \delta \nabla_\theta \log \pi(a_t|s_t, \theta)\)
    end
end
```

# Algorithm 6: REINFORCE with baseline (episodic), adapted from Sutton and Barto (2018)

```
Input: policy \(\pi(a|s, \theta)\), \(\hat{v}(s, w)\)
Parameters: step sizes, \(\alpha > 0, \beta > 0\)
Output: policy \(\pi(a|s, \theta)\)

initialize policy parameter \(\theta\) and state-value weights \(w\)
for true do
    initialize \(s\), the first state of the episode
    \(I \leftarrow 1\)
    for \(s\) is not terminal do
        \(a \sim \pi(\cdot|s, \theta)\)
        take action \(a\), observe \(s'\), \(r\)
        \(\delta \leftarrow r + \gamma \hat{v}(s', w) - \hat{v}(s, w)\) (if \(s'\) is terminal, \(\hat{v}(s', w) \doteq 0\))
        \(w \leftarrow w + \beta \delta \nabla_w \hat{v}(s_t, w)\)
        \(\theta \leftarrow \theta + \alpha I \delta \nabla_\theta \log \pi(a_t|s_t, \theta)\)
        \(I \leftarrow \gamma I\)
        \(s \leftarrow s'\)
    end
end
```

# Algorithm 7: Actor-Critic (episodic), adapted from Sutton and Barto (2018)

# 2.4.11 DEEP RL

We obtain deep reinforcement learning (deep RL) methods when we use deep neural networks to represent the state or observation, and/or to approximate any of the following components of reinforcement learning: value function, \(\hat{v}(s; \theta)\) or \(\hat{q}(s, a; \theta)\), policy \(\pi(a|s; \theta)\), and model (state transition function and reward function). Here, the parameters \(\theta\) are the weights in deep neural networks. When we use "shallow" models, like linear function, decision trees, tile coding and so on as the function approximator, we obtain "shallow" RL, and the parameters \(\theta\) are the weight parameters in these models. Note, a shallow model, e.g., decision trees, may be non-linear. The distinct difference between deep RL and "shallow" RL is what function approximator is used. This is similar to the difference between deep learning and "shallow" machine learning. We usually utilize stochastic gradient descent to update weight parameters in deep RL. When off-policy, function approximation, in particular, non-linear function approximation, and bootstrapping are combined together, instability and divergence may occur (Tsitsiklis and Van Roy, 1997). However, recent work like deep Q-network (Mnih et al., 2015) and AlphaGo (Silver et al., 2016a) stabilize the learning and achieve outstanding results. There are efforts for convergence proof of control with non-linear function approximation, e.g., Dai et al. (2018b); Nachum et al. (2018).