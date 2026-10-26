Proof Let

$$u_g^h = \int g^{h+1}(x^{h+1})\nu^h(x^{h+1}) d\mu^{h+1}(x^{h+1}).$$

We have

$$\mathbb{E}_{x^{h+1}|x^h,a^h} g^{h+1}(x^{h+1}) = \int g^{h+1}(x^{h+1})\langle\nu^h(x^{h+1}),\phi^h(x^h,a^h)\rangle d\mu^{h+1}(x^{h+1}) = \langle u_g^h,\phi^h(x^h,a^h)\rangle.$$

This implies that

$$(\mathcal{T}^h g)(x^h,a^h) = \langle\theta^h + u_g^h,\phi^h(x^h,a^h)\rangle \in \mathcal{F}.$$

Since $Q_*^h(x^h,a^h) = (\mathcal{T}^h Q_*)(x^h,a^h)$, we know $Q_*^h(x^h,a^h) \in \mathcal{F}$.

Similarly, since $(\mathcal{T}^h f)(x^h,a^h) \in \mathcal{F}$, we know that $f \in \mathcal{F}$ implies

$$\mathcal{E}^h(f,x^h,a^h) = f^h(x^h,a^h) - (\mathcal{T}^h f)(x^h,a^h) \in \mathcal{F}.$$

This proves the desired result. \square

Proposition 18.18 implies that if the feature map $\phi$ is known, then a linear MDP with linear function class is both realizable and complete.

# Algorithm 18.1 Bellman Error UCB Algorithm

```
**Input:** $\lambda, T, \mathcal{F}, \mathcal{G}$
1 Let $\mathcal{F}_0 = \{f_0\}$
2 Let $\beta_0 = 0$
3 for $t = 1,2,\dots,T$ do
   4 Observe $x_t^1$
   5 Let $f_t \in \arg\max_{f\in\mathcal{F}_{t-1}} f(x_t^1)$.
   6 Let $\pi_t = \pi_{f_t}$
   7 Play policy $\pi_t$ and observe trajectory $(x_t, a_t, r_t)$
   8 Let
      $$\mathcal{F}_t = \left\{ f \in \mathcal{F} : \sup_{g\in\mathcal{G}} \sum_{h=1}^{H} \sum_{s=1}^{t} L^h\left(f,g,x_s^h,a_s^h,r_s^h,x_s^{h+1}\right) \le \beta_t^2 \right\}$$
      with appropriately chosen $\beta_t$, where $L^h(\cdot)$ is defined in (18.3).
9 return randomly chosen $\pi_t$ from $t = 1$ to $t = T$
```

We can generalize the UCB algorithm for contextual bandit to the UCB algorithm for reinforcement learning in Algorithm 18.1. It is again an implementation of the optimism in the face of uncertainty principle. Its analysis is similar to that of Algorithm 17.4. We may define an extension of the eluder coefficient as follows, which is similar to Definition 17.17. For convenience, we define it in terms of expectation, which is more general than the definition without expectation in Definition 17.17.