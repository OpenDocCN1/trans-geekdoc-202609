# Exercises

**17.1** In Algorithm 17.2 for stochastic linear contextual bandits, we consider a pure exploration scheme where we choose the arm in line 6 according to confidence as

$$a_t \in \arg\max_a \psi(x_t,a)^\top A_{t-1}^{-1}\psi(x_t,a).$$

Similar to Lemma 17.8, we would like to derive an upper confidence bound after step $T$, but instead of a uniform bound for all $u \in \mathbb{R}^d$, we consider a bound for any fixed vector $u \in \mathbb{R}^d$. Given any fixed $u \in \mathbb{R}^d$, show that with probability at least $1-\delta$,

$$\left|u^\top(w_* - w_T)\right| \le \widetilde{\beta}_T\sqrt{u^\top A_T^{-1}u}$$

for some $\widetilde{\beta}_T$ that is independent of $d$.

+   - Show that for appropriately defined $\gamma_t$,
+   
+     $$u^\top(w_* - w_T) = \lambda u^\top A_T^{-1}w_* + \sum_{t=1}^{T}\gamma_t\epsilon_t(x_t,a_t),$$
+   
+     where $\{\gamma_t\}$ and $\{\epsilon_t(x_t,a_t)\}$ are independent.

+   - Use Azuma’s inequality to obtain a concentration bound so that
+   
+     $$\Pr\left[\left|u^\top(w_* - w_T)\right| > \widetilde{\beta}_T\sqrt{u^\top A_T^{-1}u}\right] \le \delta,$$
+   
+     with appropriately chosen $\widetilde{\beta}_T$ independent of $d$. As in Lemma 17.8, we assume that $\|w_*\|_2 \le B$ with known $B$, and for all $t$, $r_t(x_t,d_t) \in [0,M]$.

+   - Assume we have $K$ arms. Define $\widetilde{\beta}_T$ so that with probability at least $1-\delta$, the following inequality holds uniformly for all $a \in \{1,\ldots,K\}$:
+   
+     $$\left|\psi(x_{T+1},a)^\top(w_* - w_T)\right| \le \widetilde{\beta}_T\sqrt{\psi(x_{T+1},a)^\top A_T^{-1}\psi(x_{T+1},a)}.$$
+   
+     Compare this bound to that of Lemma 17.8. Why can we not use this better $\widetilde{\beta}_T$ for $\beta_T$ in the original Algorithm 17.2?

**17.2** Consider stochastic linear bandit with $K=2^s$ arms and feature dimension $d$ with $s \le d$. Construct an example, so that the regret of any bandit algorithm is at least

$$\Omega(\sqrt{sdT}).$$

**17.3** Prove Proposition 17.16.

**17.4** Prove (17.10) by using the following inequality with $A_{t-1}=B^{-2}I+A_{t-1}$:

$$|f_t(x_t,a_t)-f_*(x_t,a_t)|^2 \le \left(\|w_t-w_*\|_{A_{t-1}}^2+1\right)\min\left(1,\|\psi(x_t,a_t)\|_{A_{t-1}^{-1}}^2\right).$$

**17.5** Compute the eluder coefficient of a function class under the conditions of Example 9.10.

**17.6** Use Theorem 13.22 to derive a lower bound for the construction in Theorem 17.33, and compare the result to that of Theorem 17.33.

**17.7** Show that the eluder coefficient $\operatorname{EC}(\epsilon,\mathcal{F},T)=\widetilde{O}(\operatorname{Edim}(\mathcal{F},\epsilon))$, where $\widetilde{O}$ hides a logarithmic factor.

**17.8** Assume that $\mathcal{F}$ is linearly embeddable with $\dim(\epsilon,\mathcal{F}) \le c_0/\epsilon^p$ for some $p,c_0>0$, and assume that $\mathcal{F}$ has $L_\infty(\mathcal{D})$ covering number $\mathcal{N}(\epsilon,\mathcal{F},L_\infty(\mathcal{D})) \le c_1/\epsilon^q$ for some $c_1,q>0$. Derive a regret bound for an appropriately designed bandit algorithm in the pure exploration setting.