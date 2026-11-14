"actor" refers to the policy, and the term "critic" refers to the value function. The use of bootstrapping in TD updates allows more efficient learning of the value function compared to MC. In addition, it allows us to develop a fully online, incremental algorithm, that does not need to wait until the end of the trajectory before updating the parameters (as in Algorithm 35.2).

Concretely, consider the use of the one-step TD(0) method to estimate the return in the episodic case, i.e., we replace $G_t$ with $G_{t:t+1} = r_t + \gamma V_w(s_{t+1})$. If we use $V_w(s_t)$ as a baseline, the REINFORCE update in Equation (35.25) becomes

```
$$ \theta \leftarrow \theta + \eta \sum_{t=0}^{T-1} \gamma^t (G_{t:t+1} - V_w(s_t)) \nabla_\theta \log \pi_\theta(a_t|s_t) $$
```

```
$$ = \theta + \eta \sum_{t=0}^{T-1} \gamma^t (r_t + \gamma V_w(s_{t+1}) - V_w(s_t)) \nabla_\theta \log \pi_\theta(a_t|s_t) $$
```

# ### 35.3.3.1 A2C and A3C

Note that $r_{t+1} + \gamma V_w(s_{t+1}) - V_w(s_t)$ is a single sample approximation to the advantage function $A(s_t, a_t) = Q(s_t, a_t) - V(s_t)$. This method is therefore called **advantage actor critic** or **A2C** (Algorithm 35.3). If we run the actors in parallel and asynchronously update their shared parameters, the method is called **asynchronous advantage actor critic** or **A3C** [Mni+16].

```
Algorithm 35.3: Advantage actor critic (A2C) algorithm
1 Initialize actor parameters $\theta$, critic parameters $w$
2 repeat
3   Sample starting state $s_0$ of a new episode
4   for $t = 0, 1, 2, \dots$ do
5     Sample action $a_t \sim \pi_\theta(\cdot|s_t)$
6     Observe next state $s_{t+1}$ and reward $r_t$
7     $\delta = r_t + \gamma V_w(s_{t+1}) - V_w(s_t)$
8     $w \leftarrow w + \eta_w \delta \nabla_w V_w(s_t)$
9     $\theta \leftarrow \theta + \eta_\theta \gamma^t \delta \nabla_\theta \log \pi_\theta(a_t|s_t)$
10 until converged
```

# ### 35.3.3.2 Eligibility traces

In A2C, we use a single step rollout, and then use the value function in order to approximate the expected return for the trajectory. More generally, we can use the $n$-step estimate

```
$$ G_{t:t+n} = r_t + \gamma r_{t+1} + \gamma^2 r_{t+2} + \dots + \gamma^{n-1} r_{t+n-1} + \gamma^n V_w(s_{t+n}) $$
```

and obtain an $n$-step advantage estimate as follows:

```
$$ A_{\pi_\theta}^{(n)}(s_t, a_t) = G_{t:t+n} - V_w(s_t) $$
```