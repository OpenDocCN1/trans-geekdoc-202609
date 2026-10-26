
Now we can sum over $t = 1$ to $t = T$, and obtain

$$\ln \frac{W_T}{W_0} \le \frac{\eta}{1-\gamma}\sum_{t=1}^T r_t(a_t) - \eta b\sum_{t=1}^T \tilde{\rho}_t(a_t) + \frac{c(\eta,b)\eta^2}{(1-\gamma)}\sum_{t=1}^T \frac{|r_t(a_t)-b|}{\hat{\pi}_t(a_t)}.$$

Note that $W_0 = 1$. We can take expectation with respect to the randomization of the algorithm, and obtain

$$\mathbb{E}\,\ln\mathbb{E}_{w\sim p_0(w)}\exp\left(\eta\sum_{t=1}^T \hat{r}_t(w,x_t,a_t)\right)$$

$$\le \frac{\eta}{1-\gamma}\mathbb{E}\sum_{t=1}^T r_t(a_t) - \eta T b + \frac{c(\eta,b)\eta^2}{(1-\gamma)}\mathbb{E}\sum_{t=1}^T\sum_{a=1}^K |r_t(a)-b|. \tag{17.7}$$

The derivation also used $\mathbb{E}\,\tilde{\rho}_t(a_t)=\mathbb{E}\,\mathbb{E}_{a_t\sim\hat{\pi}_t}\tilde{\rho}_t(a_t)=1$ and

$$\mathbb{E}\frac{|r_t(a_t)-b|}{\hat{\pi}_t(a_t)} = \mathbb{E}\,\mathbb{E}_{a_t\sim\hat{\pi}_t}\frac{|r_t(a_t)-b|}{\hat{\pi}_t(a_t)} = \mathbb{E}\sum_{a=1}^K |r_t(a)-b|.$$

We can lower bound the left-hand side of $(17.7)$ as:

$$\mathbb{E}\,\ln\mathbb{E}_{w\sim p_0(w)}\exp\left(\eta\sum_{t=1}^T \hat{r}_t(w,x_t,a_t)\right)$$

$$= \mathbb{E}\max_q\left[\mathbb{E}_{w\sim q}\eta\sum_{t=1}^T \hat{r}_t(w,x_t,a_t) - \mathrm{KL}(q\|p_0)\right]$$

$$\ge \max_q\left[\mathbb{E}_{w\sim q}\eta\mathbb{E}\sum_{t=1}^T \hat{r}_t(w,x_t,a_t) - \mathrm{KL}(q\|p_0)\right]$$

$$= \max_q\left[\mathbb{E}_{w\sim q}\eta[R_T(w)-bT] - \mathrm{KL}(q\|p_0)\right].$$

The first equality used Proposition 7.16. The last equation used $(17.3)$ and the definition of $R_T$. By plugging this estimate into the left-hand side of $(17.7)$, we obtain the desired result.

## Corollary 17.5

The following result is a direct consequence of Theorem 17.4. It can be regarded as a direct generalization of Theorem 16.17.

Let $\eta = \gamma/K$ and $b = 0$. Assume that the uniform random policy belongs to $\Omega$ and $|\Omega| = N < \infty$. Let $p_0(w)$ be the uniform prior over $\Omega$, then

$$G_* - \mathbb{E}\sum_{t=1}^T r_t(a_t) \le (e-1)\gamma G_* + \frac{K\ln N}{\gamma},$$

where the expectation is with respect to the randomization of the algorithm, and

$$G_* = \arg\max_w \sum_{t=1}^T \mathbb{E}\,\mathbb{E}_{a\sim\hat{\pi}_t(\cdot|w,x_t)}[r_t(a)].$$

**Proof**  We have $\hat r_t(w,x_t,a_t) \le 1$, and thus $c(\eta,b)=e-2$. Note that the uniform random policy belonging to $\Omega$ implies that

$$\frac{1}{K}\sum_{t=1}^{T}\sum_{a=1}^{K}r_t(a)\le G_*.$$

We consider Theorem 17.4, with $q$ defined as $q(w)=\mathbf{1}(w=w_*)$, where $w_*$ achieves the maximum of $G_*$. This implies

$$\mathbb{E}\sum_{t=1}^{T}r_t(a_t)\ge (1-\gamma)\left[G_* - \frac{K}{\gamma}\ln N\right]-(e-2)\gamma G_*.$$

This implies the bound.

**Example 17.6**  We can take $\gamma=0$ and $b=1$ in Algorithm 17.1. By noting that $\phi(z)$ is an increasing function of $z$ and $\eta(1-b)\le 0$, we may take

$$c(\eta,b)=0.5.$$

Theorem 17.4 implies that

$$\mathbb{E}\sum_{t=1}^{T}r_t(a_t)\ge \max_q\left[R_T(w)-\frac{1}{\eta}\mathrm{KL}(q\|p_0)\right]-0.5\eta KT.$$

In the finite policy case $|\Omega|=N$ with uniform prior,

$$G_* - \mathbb{E}\sum_{t=1}^{T}r_t(a_t)\le \frac{\ln N}{\eta}+0.5\eta KT.$$

By choosing $\eta=\sqrt{\ln N/(KT)}$, we obtain

$$G_* - \mathbb{E}\sum_{t=1}^{T}r_t(a_t)\le 2\sqrt{KT\ln N}.$$

We can compare EXP4 to its full information counterpart Hedge in Algorithm 14.4. We note that in the online setting of the Hedge algorithm, we observe the information for all arms $a\in\{1,\ldots,K\}$ even if $a$ is not pulled. In this case, it is possible to replace $\hat r_t(w,x_t,a_t)$ by $r_t(w,x_t)=-\ell_t(w_{t-1})$, and we do not have to explore in order to obtain rewards for different arms. This removes the $K$ dependency in the resulting online regret bound. Using the same notation of Theorem 17.4, we obtain the following Hedge online regret bound (in the full information case) from Theorem 14.15:

$$\mathbb{E}\sum_{t=1}^{T}r_t(a_t)\ge \max_q\left[R_T(w)-\frac{1}{\eta}\mathrm{KL}(q\|p_0)\right]-\frac{\eta T}{8}.$$

Assume that $|\Omega|=N<\infty$. Let $p_0(w)$ be the uniform prior over $\Omega$, then we obtain the following online regret bound for Hedge (in the full information case):

$$G_* - \mathbb{E}\sum_{t=1}^{T}r_t(a_t)\le \frac{\ln N}{\eta}+\frac{\eta T}{8}.$$

With $\eta = \sqrt{\ln N / T}$, we obtain the full information regret bound of

$G_* - \mathbb{E}\sum_{t=1}^{T} r_t(a_t) \le 2\sqrt{T \ln N}$

which does not contain the factor $K$.

## 17.2 Linear UCB for Stochastic Contextual Bandits

The EXP4 algorithm tries to find the best policy in a policy class. We can also design an algorithm that finds the best value function from a value function class. In particular, if $f_*(x, a)$ is a linear function, then we can directly generalize the UCB algorithm to find a near-optimal value function, and use its induced greedy policy to select an arm to pull. We first introduce the following definition, which generalizes stochastic linear bandit models in Section 16.4 to the contextual bandit setting.

### Definition 17.7

The stochastic linear contextual bandit (or stochastic contextual bandit with linear payoff) is a contextual bandit problem, where the reward at each time step $t$ is given by

$r_t(a) = r_t(x_t, a) = w_*^T \psi(x_t, a) + \epsilon_t(x_t, a), \quad (17.8)$

where $\epsilon_t(x, a)$ is a zero-mean random variable. We assume that $\mathcal{H}$ is a known inner product space, $w_* \in \mathcal{H}$ is the unknown model parameter, and the feature vector $\psi(x, a) \in \mathcal{H}$ is known.

In the stochastic linear bandit model, the number of arms can be either infinite or finite, and an UCB-style algorithm is presented in Algorithm 17.2. Note that the algorithm selects an arm that has the largest confidence bound adjusted reward. This methodology is referred to as optimism in the face of uncertainty, and is a direct generalization of upper confidence bound (UCB) for MAB. Therefore we call Algorithm 17.2 linear UCB, although it is also referred to as OFUL (optimism in the face of uncertainty linear) bandit in the literature (Abbasi-Yadkori et al., 2011).

### Algorithm 17.2 Linear UCB Algorithm

Input: $\lambda$, $T$, $\{\beta_t\}$

1 Let $A_0 = \lambda I$
2 Let $w_0 = 0$
3 Let $b_0 = 0$
4 for $t = 1, 2, \dots, T$ do
   5 Observe $x_t$
   6 Let $a_t \in \arg\max_a \left[ w_{t-1}^T \psi(x_t, a) + \beta_{t-1} \sqrt{\psi(x_t, a)^T A_{t-1}^{-1} \psi(x_t, a)} \right]$
   7 Pull arm $a_t$ and observe reward $r_t(x_t, a_t)$
   8 Let $b_t = b_{t-1} + r_t(x_t, a_t) \psi(x_t, a_t)$
   9 Let $A_t = A_{t-1} + \psi(x_t, a_t) \psi(x_t, a_t)^T$
   10 Let $w_t = A_t^{-1} b_t$

In order to analyze Algorithm 17.2, we need to obtain a uniform confidence interval for the linear bandit problem using either Theorem 13.7 or Theorem 13.10. The bound stated below holds uniformly for all arms (possibly infinitely many) and both for lower and upper confidence bounds.

### Lemma 17.8

Assume that in the stochastic linear bandit model, $||w_*||_{\mathcal H} \le B$ for some constant $B$, and in Algorithm 17.2, assume that $\{\beta_t\}$ is any sequence so that $\Pr\left[\forall 0 \le t \le T : \beta_t \ge \sqrt{\lambda}B + \left\|\sum_{s=1}^t \epsilon_s(x_s,a_s)\psi(x_s,a_s)\right\|_{A_t^{-1}}\right] \ge 1-\delta. \quad (17.9)$ Then with probability at least $1-\delta$, for all $t=0,\dots,T$ and $u \in \mathcal H$, $|u^\top(w_t - w_*)| \le \beta_t \sqrt{u^\top A_t^{-1} u}$.

### Proof

We have $u^\top(w_t - w_*) = u^\top A_t^{-1} \sum_{s=1}^t r_s(x_s,a_s)\psi(x_s,a_s) - u^\top w_* = u^\top A_t^{-1} \sum_{s=1}^t \epsilon_s(x_s,a_s)\psi(x_s,a_s) - \lambda u^\top A_t^{-1} w_* \le \|u\|_{A_t^{-1}} \left\|\sum_{s=1}^t \epsilon_s(x_s,a_s)\psi(x_s,a_s)\right\|_{A_t^{-1}} + \lambda \|u\|_{A_t^{-1}} \|w_*\|_{A_t^{-1}} \le \|u\|_{A_t^{-1}} \left[ \left\|\sum_{s=1}^t \epsilon_s(x_s,a_s)\psi(x_s,a_s)\right\|_{A_t^{-1}} + \sqrt{\lambda}B \right] \le \beta_t \|u\|_{A_t^{-1}}$. The second equality used (17.8). The first inequality used the Cauchy–Schwarz inequality. The last inequality used the definition of $\beta_t$. This implies the desired bound.

### Example 17.9

Assume that noise in (17.8) satisfies the sub-Gaussian conditions of Theorem 13.7, and assume that $d = \dim(\mathcal H)$ is finite dimensional, with $B' = \sup_{x,a} \|\psi(x,a)\|_{\mathcal H}$. Then in Lemma 17.8 we can set $\beta_t = \sqrt{\lambda}B + \sigma \sqrt{2\ln(1/\delta) + d\ln(1 + T(B')^2/d\lambda)}$ so that (17.9) holds. Note that Proposition 15.8 is used to obtain a bound on the log-determinant function.

### Example 17.10

Assume that noise in (17.8) satisfies the conditions of Theorem 13.10. Then in Lemma 17.8 we can set $\beta_t = \sqrt{\lambda}B + 2\alpha \sqrt{\ln(2/\delta)} + 1.2\sigma \sqrt{\text{entro}(\lambda/T, \psi(\mathcal X \times \mathcal A))}$ so that (17.9) holds. Note that entro$(\cdot)$ is defined in Proposition 15.8.
