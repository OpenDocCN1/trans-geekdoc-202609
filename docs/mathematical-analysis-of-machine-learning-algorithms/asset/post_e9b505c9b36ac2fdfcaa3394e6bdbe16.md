
Proof. Let

$$u_g^h = \int g^{h+1}(x^{h+1})\nu^h(x^{h+1}) d\mu^{h+1}(x^{h+1}).$$

We have

$$\mathbb{E}_{x^{h+1}|x^h,a^h} g^{h+1}(x^{h+1}) = \int g^{h+1}(x^{h+1})\langle\nu^h(x^{h+1}),\phi^h(x^h,a^h)\rangle d\mu^{h+1}(x^{h+1}) = \langle u_g^h,\phi^h(x^h,a^h)\rangle.$$

This implies that

$$(\mathcal{T}^h g)(x^h,a^h) = \langle\theta^h + u_g^h,\phi^h(x^h,a^h)\rangle \in \mathcal{F}.$$

Since $Q_*^h(x^h,a^h) = (\mathcal{T}^h Q_*)(x^h,a^h)$, we know $Q_*^h(x^h,a^h) \in \mathcal{F}$.

Similarly, since $(\mathcal{T}^h f)(x^h,a^h) \in \mathcal{F}$, we know that $f \in \mathcal{F}$ implies

$$\mathcal{E}^h(f,x^h,a^h) = f^h(x^h,a^h) - (\mathcal{T}^h f)(x^h,a^h) \in \mathcal{F}.$$

This proves the desired result. $\square$

Proposition 18.18 implies that if the feature map $\phi$ is known, then a linear MDP with linear function class is both realizable and complete.

### Algorithm 18.1 Bellman Error UCB Algorithm

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

### Definition 18.19 (Q-type Bellman eluder coefficient)

Given a candidate $Q$ function class $\mathcal{F}$, its $Q$-type Bellman eluder coefficient $\mathrm{EC}_{Q}(\epsilon,\mathcal{F},T)$ is the smallest number $d$ so that for any filtered sequence $\{f_t,(x_t,r_t,a_t)\sim\pi_{f_t}\}_{t=1}^{T}$,

$$\mathbb{E}\sum_{t=2}^{T}\sum_{h=1}^{H}\mathcal{E}^{h}(f_t,x_t^{h},a_t^{h})\leq\sqrt{d\,\mathbb{E}\sum_{h=1}^{H}\sum_{t=2}^{T}\left(\epsilon+\sum_{s=1}^{t-1}\mathcal{E}^{h}(f_t,x_s^{h},a_s^{h})^2\right)}.$$

One may also replace the sum $\sum_{s=1}^{t-1}\mathcal{E}^{h}(f_t,x_s^{h},a_s^{h})^2$ on the right-hand side of Definition 18.19 by

$$\sum_{s=1}^{t-1}\mathbb{E}_{(\tilde{x}_s,\tilde{a}_s)\sim\pi_{f_s}}\mathcal{E}^{h}(f_t,\tilde{x}_s^{h},\tilde{a}_s^{h})^2.$$

We will not consider this variant for the $Q$-type problem, but will employ this variant for the $V$-type problem in Definition 18.27.

For linear MDP, one can employ Proposition 17.20 and Proposition 15.8 to obtain an estimate of the eluder coefficient.

### Proposition 18.20

Assume that a *linear MDP* has (possibly unknown) feature maps $\phi^h(x^h,a^h)$ in inner product spaces $\{\mathcal{H}^h\}$, each with inner product $\langle\cdot,\cdot\rangle_{\mathcal{H}^h}$. Assume also that the candidate $Q$-function class $\mathcal{F}$ can be embedded into the linear function space $\mathcal{F}\subseteq\{w^h,\phi^h(x^h,a^h):w^h\in\mathcal{H}^h\}$, and there exists $B>0$ such that $\|\mathcal{E}^h(f,\cdot,\cdot)\|_{\mathcal{H}^h}\leq B$. Assume that $|\mathcal{E}^h(f,x^h,a^h)|\in[0,1]$, then

$$\mathrm{EC}_{Q}(1,\mathcal{F},T)\leq 2\sum_{h=1}^{H}\operatorname{entro}\left(1/(B^2T),\phi^h(\cdot,\cdot)\right),$$

where $\operatorname{entro}(\cdot)$ is defined in Proposition 15.8. In particular, if $\{\mathcal{H}^h\}$ are finite dimensional, then we have

$$\mathrm{EC}_{Q}(1,\mathcal{F},T)\leq 2\sum_{h=1}^{H}\dim(\mathcal{H}^h)\ln\left(1+T(BB')^2\right),$$

where $B'=\sup_h\sup_{x^h,a^h}\|\phi^h(x^h,a^h)\|_{\mathcal{H}^h}$.

We note that $\mathcal{F}$ may be nonlinear by itself, although it can be embedded into a linear function space. One may also choose a sufficiently large RKHS to realize such an embedding assumption. We can now prove a direct extension of Theorem 17.19 as follows. Similar to Theorem 17.19, the structural assumption of the MDP is characterized by Definition 18.19, which may include examples other than linear MDP. For simplicity, we state the result in expectation, and leave the high-probability bound as an exercise.

### Theorem 18.21

Assume that *Assumption 18.12* holds, $\mathcal{F}$ is complete with respect to $\mathcal{G}$, and $g^h(\cdot)\in[0,1]$ for all $g\in\mathcal{G}$. Assume also that $\beta_t$ is chosen in Algorithm 18.1 according to

$$\beta_t^2\geq\inf_{\epsilon>0}\left[4\epsilon t(4+\epsilon)H+2\ln\left(16M(\epsilon,\mathcal{F},\|\cdot\|_{\infty})^2M(\epsilon,\mathcal{G},\|\cdot\|_{\infty})/\delta^2\right)\right].$$

with $M(\cdot)$ denoting the $\|\cdot\|_{\infty}$ packing number, and $\|f\|_{\infty} = \sup_{h,x,a}|f^h(x,a)|$. Then

$$\mathbb{E}\sum_{t=2}^{T}\left[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)\right] \le \delta T+\sqrt{\operatorname{EC}_Q(\epsilon,\mathcal{F},T)\left(\epsilon HT+\delta HT^2+4\sum_{t=2}^{T}\beta_{t-1}^2\right)}.$$

*Proof.* For $t\ge 2$, we have

$$\begin{aligned} V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1) &= V_*^1(x_t)-f_t(x_t^1)+f_t(x_t^1)-V_{\pi_t}^1(x_t^1) \\ &\le \mathbf{1}(Q_*\notin\mathcal{F}_{t-1})+\left[f_t(x_t^1)-V_{\pi_t}^1(x_t^1)\right] \\ &= \mathbf{1}(Q_*\notin\mathcal{F}_{t-1})+\mathbb{E}_{(x_t,a_t,r_t)\sim\pi_t\mid x_t^1}\sum_{h=1}^{H}\mathcal{E}^h(f_t,x_t^h,a_t^h). \end{aligned}$$

The inequality used the fact that if $Q_*\in\mathcal{F}_{t-1}$, then $f_t(x_t^1)=\max_{f\in\mathcal{F}_{t-1}}f(x_t^1)\ge V_*^1(x_t^1)$, and if $Q_*\notin\mathcal{F}_{t-1}$, $V_*^1(x_t)-f_t(x_t^1)\le 1$. The last equation used Theorem 18.11.

Theorem 18.14 implies that $\Pr(Q_*\in\mathcal{F}_{t-1})\ge 1-\delta$. We thus have

$$\mathbb{E}\left[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)\right]\le \delta+\mathbb{E}\sum_{h=1}^{H}\mathcal{E}^h(f_t,x_t^h,a_t^h).$$

We can now obtain

$$\begin{aligned} \mathbb{E}\sum_{t=2}^{T}\left[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)\right] &\le \mathbb{E}\sum_{t=2}^{T}\sum_{h=1}^{H}\mathcal{E}^h(f_t,x_t^h,a_t^h)+\delta T \\ &\le \delta T+\sqrt{\operatorname{EC}_Q(\epsilon,\mathcal{F},T)\,\mathbb{E}\sum_{t=2}^{T}\sum_{h=1}^{H}\left(\epsilon+\sum_{s=1}^{t-1}\mathcal{E}^h(f_t,x_s^h,a_s^h)^2\right)} \\ &\le \delta T+\sqrt{\operatorname{EC}_Q(\epsilon,\mathcal{F},T)\left(\epsilon HT+\delta HT^2+4\sum_{t=2}^{T}\beta_{t-1}^2\right)}. \end{aligned}$$

The second inequality used Definition 18.19. The last inequality used the fact that for each $t$, Theorem 18.14 holds with probability $1-\delta$, and otherwise, $\mathcal{E}^h(f_t,x_s^h,a_s^h)^2\le 1$.

To interpret the theorem, we still consider the $d$-dimensional linear MDP with bounded $\mathcal{F}$ and $\mathcal{G}$. If the model coefficients at different step $h$ are different, then the metric entropy can be bounded (ignoring log factors) as $\widetilde{O}(H\ln(M_{\mathcal{F}}M_{\mathcal{G}}))=\widetilde{O}(Hd)$, and hence with $\epsilon=\delta=O(1/T^2)$, we have

$$\beta_t^2=\widetilde{O}(H\ln(M_{\mathcal{F}}M_{\mathcal{G}}))=\widetilde{O}(Hd).$$

Since $\operatorname{EC}_Q(\epsilon,\mathcal{F},T) = \tilde{O}(dH)$, we obtain a regret of

$$\mathbb{E}\sum_{t=2}^{T}[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)] = \tilde{O}\left(H\sqrt{dT\ln(M_{\mathcal{F}}M_{\mathcal{G}})} \right)=\tilde{O}\left(Hd\sqrt{T}\right). \tag{18.8}$$

If a Q function at different steps $h$ shares the same model coefficient, then we have $\beta_t^2 = \tilde{O}(\ln(M_{\mathcal{F}}M_{\mathcal{G}})) = \tilde{O}(d)$, which is independent of $H$. In this case the regret becomes

$$\mathbb{E}\sum_{t=2}^{T}[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)] = \tilde{O}\left(\sqrt{dHT\ln(M_{\mathcal{F}}M_{\mathcal{G}})} \right)=\tilde{O}(d\sqrt{HT}).$$

The resulting regret bound is optimal in its dependence on $d$ and $T$ (see Theorem 17.13), but suboptimal in the dependence on $H$. The $H$ dependency can be improved using weighted regression, where the weight is inversely proportional to an upper bound of the variance. The resulting procedure is more complex, and thus we will not consider it here.

## 18.3 Least Squares Value Iteration

It was shown in Theorem 18.21 that the UCB method in Algorithm 18.1 can handle linear MDP with $Q$-type Bellman eluder coefficients. However, it requires solving a minimax formulation with global optimism, which may be difficult computationally. This section shows that a computationally more efficient approach can also be used to solve linear MDP. In this approach, we are restricted to the case that the function class $\mathcal{F}$ can be factored as the product of $\mathcal{F}^h$, and we need to make a stronger assumption of Bellman completeness in (18.9), and a stronger form of Bellman eluder coefficient to control the point-wise confidence interval in (18.10).

### Assumption 18.22

Assume that the Q function class $\mathcal{F}$ can be factored as the product of $H$ function classes:

$$\mathcal{F}=\prod_{h=1}^{H}\mathcal{F}^h, \quad \mathcal{F}^h=\{\langle w^h,\phi^h(x^h,a^h)\rangle,w^h\in\mathcal{H}^h\},$$

so that for all $g^{h+1}(x^{h+1})\in[0,1]$,

$$(\mathcal{T}^h g^{h+1})(x^h,a^h)\in\mathcal{F}^h. \tag{18.9}$$

Assume for any $\epsilon>0$, there exists a function class $\mathcal{B}^h(\epsilon)$ so that for any sequence $\{(x_t^h,a_t^h,\hat f_t^h)\in\mathcal{X}\times\mathcal{A}\times\mathcal{F}^h:t=1,\dots,T\}$, we can construct a sequence of non-negative bonus functions $b_t^h(\cdot)\in\mathcal{B}^h(\epsilon)$ (each $\hat f_t^h$ and $b_t^h$ only depend on the historic observations up to $t-1$) such that
