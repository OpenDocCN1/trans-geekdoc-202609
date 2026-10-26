$$r_t(a)=r_t(x_t,a)=f_*(x_t,a)+\epsilon_t(x_t,a),$$
where $\epsilon_t(x,a)$ is a zero-mean random variable, where we assume that $f_*(x,a)\in\mathcal{F}$ for a known function class $\mathcal{F}: \mathcal{X}\times\mathcal{A}\to\mathbb{R}$. Given any $f(x,a)\in\mathcal{F}$, we also define
$$f(x)=\max_{a\in\mathcal{A}}f(x,a),$$
and the greedy policy of $f$ as: $\pi_f(x)\in\arg\max_{a\in\mathcal{A}}f(x,a)$.

For the stochastic nonlinear bandit model, we may generalize Algorithm 17.2 as in Algorithm 17.4. In general, we say $\mathcal{F}_t$ is a version space if $f_*\in\mathcal{F}_t$ with high probability. Choosing the optimal $f_t$ in a properly defined version space is a natural generalization of upper confidence bound. The algorithm directly implements the optimism in the face of the uncertainty principle.

**Algorithm 17.4 Version Space UCB Algorithm**
**Input:** $\lambda, T, f_0\in\mathcal{F}$
1 Let $\mathcal{F}_0=\{f_0\}$
2 **for** $t=1,2,\dots,T$ **do**
   3 Observe $x_t$
   4 Let $f_t\in\arg\max_{f\in\mathcal{F}_{t-1}}f(x_t)$
   5 Let $a_t\in\arg\max_a f_t(x_t,a)$
   6 Pull arm $a_t$ and observe reward $r_t(x_t,a_t)\in[0,1]$
   7 Let $\mathcal{F}_t$ be an appropriate version space based on $\mathcal{S}_t=\{(x_s,a_s)\}_{s=1}^t$.

The following result shows that with an appropriately defined version space, Algorithm 17.4 is a generalization of Algorithm 17.2. We leave its proof to an exercise.

# **Proposition 17.16**  Assume that $\mathcal{F}=\{f(w,x,a)=w^\top\psi(x,a):w\in\mathbb{R}^d\}$. Let

$$\mathcal{F}_t=\{f(w,\cdot):\phi_t(w)\le\phi_t(w_t)+\beta_t^2\},$$
where $w_t=\arg\min_w\phi_t(w)$, and
$$\phi_t(w)=\sum_{s=1}^t\big(w^\top\psi(x_s,a_s)-r_s(x_s,a_s)\big)^2+\lambda\|w\|_2^2.$$
Then Algorithm 17.4 is equivalent to Algorithm 17.2. In particular, we have
$$\mathcal{F}_{t-1}=\{f(w,x,a):\|w-w_{t-1}\|_{A_{t-1}}\le\beta_{t-1}\},$$
and
$$\max_{f\in\mathcal{F}_{t-1}}f(x_t,a)=w_{t-1}^\top\psi(x_t,a)+\beta_{t-1}\|\psi(x_t,a)\|_{A_{t-1}^{-1}}.$$

In general, the version space $\mathcal{F}_t$ in Algorithm 17.4 contains functions that fit well on historic data $\mathcal{S}_t$. In order to analyze such a version space algorithm, we need to introduce the concept of eluder coefficient.