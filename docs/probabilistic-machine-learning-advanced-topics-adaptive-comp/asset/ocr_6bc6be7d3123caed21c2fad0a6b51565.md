resulting in faster and more robust optimization. The natural policy gradient can be approximated using the KFAC method (Section 6.4.4), as done in [Wu+17].

Other than TRPO, another approach inspired by Equation (35.34) is to use the KL-divergence as a penalty term, replacing the factor $2\epsilon\gamma/(1-\gamma)^2$ by a tuning parameter. However, it often works better, and is simpler, by using the following clipped objective, which results in the **proximal policy optimization** or PPO method [Sch+17]:

```
$J^{\text{PPO}}(\pi') \triangleq \frac{1}{1-\gamma} \mathbb{E}_{p_{\pi(a|s)}^\infty(s)\pi(a|s)} \left[ \kappa_\epsilon \left( \frac{\pi'(a|s)}{\pi(a|s)} \right) A_\pi(s,a) \right]$
```

where $\kappa_\epsilon(x) \triangleq \text{clip}(x, 1-\epsilon, 1+\epsilon)$ ensures $|\kappa(x)-1| \le \epsilon$. This method can be modified to ensure monotonic improvement as discussed in [WHT19], making it a true bound optimization method.

# 35.3.5 Deterministic policy gradient methods

In this section, we consider the case of a deterministic policy, that predicts a unique action for each state, so $a_t = \mu_\theta(s_t)$, rather than $a_t \sim \pi_\theta(s_t)$. We assume the states and actions are continuous, and define the objective as

```
$J(\mu_\theta) \triangleq \frac{1}{1-\gamma} \mathbb{E}_{p_{\mu_\theta}^\infty(s)} [R(s, \mu_\theta(s))]$
```

The deterministic policy gradient theorem [Sil+14] provides a way to compute the gradient:

```
$\nabla_\theta J(\mu_\theta) = \frac{1}{1-\gamma} \mathbb{E}_{p_{\mu_\theta}^\infty(s)} [\nabla_\theta Q_{\mu_\theta}(s, \mu_\theta(s))]$
```

```
$= \frac{1}{1-\gamma} \mathbb{E}_{p_{\mu_\theta}^\infty(s)} [\nabla_\theta \mu_\theta(s) \nabla_a Q_{\mu_\theta}(s, a)|_{a=\mu_\theta(s)}]$
```

where $\nabla_\theta \mu_\theta(s)$ is the $M \times N$ Jacobian matrix, and $M$ and $N$ are the dimensions of $\mathcal{A}$ and $\theta$, respectively. For stochastic policies of the form $\pi_\theta(a|s) = \mu_\theta(s) + \text{noise}$, the standard policy gradient theorem reduces to the above form as the noise level goes to zero.

Note that the gradient estimate in Equation (35.40) integrates over the states but not over the actions, which helps reduce the variance in gradient estimation from sampled trajectories. However, since the deterministic policy does not do any exploration, we need to use an off-policy method, that collects data from a stochastic behavior policy $\beta$, whose stationary state distribution is $p_\beta^\infty$. The original objective, $J(\mu_\theta)$, is approximated by the following:

```
$J_b(\mu_\theta) \triangleq \mathbb{E}_{p_\beta^\infty(s)} [V_{\mu_\theta}(s)] = \mathbb{E}_{p_\beta^\infty(s)} [Q_{\mu_\theta}(s, \mu_\theta(s))]$
```

with the off-policy deterministic policy gradient approximated by (see also Section 35.5.1.2)

```
$\nabla_\theta J_b(\mu_\theta) \approx \mathbb{E}_{p_\beta^\infty(s)} [\nabla_\theta [Q_{\mu_\theta}(s, \mu_\theta(s))]] = \mathbb{E}_{p_\beta^\infty(s)} [\nabla_\theta \mu_\theta(s) \nabla_a Q_{\mu_\theta}(s, a)|_{a=\mu_\theta(s)} ds]$
```

where we have dropped a term that depends on $\nabla_\theta Q_{\mu_\theta}(s, a)$ and is hard to estimate [Sil+14].

To apply Equation (35.42), we may learn $Q_w \approx Q_{\mu_\theta}$ with TD, giving rise to the following updates:

```
$\delta = r_t + \gamma Q_w(s_{t+1}, \mu_\theta(s_{t+1})) - Q_w(s_t, a_t)$
```

```
$\mathbf{w}_{t+1} \leftarrow \mathbf{w}_t + \eta_w \delta \nabla_w Q_w(s_t, a_t)$
```

```
$\boldsymbol{\theta}_{t+1} \leftarrow \boldsymbol{\theta}_t + \eta_\theta \nabla_\theta \boldsymbol{\mu}_\theta(s_t) \nabla_a Q_w(s_t, a)|_{a=\boldsymbol{\mu}_\theta(s_t)}$
```