Substituting from (6.55) and (6.56) in (6.54), we obtain that

$$\mathbb{E}\left[V_t\right] \le \left(1-\frac{\mu}{4}\gamma_{t-1}\right)\left(\mathbb{E}\left[\mathcal{L}_H\left(\boldsymbol{\theta}_{t-1}\right)-\mathcal{L}_H^*\right]\right) + z\mathbb{E}\left[\left\|\boldsymbol{\xi}_{t-1}\right\|^2\right] + \kappa z\mathbb{E}\left[M_{t-1}^H\right]) + z\left(1-\beta_t\right)^2\left(\kappa+\frac{1}{n-f}\right)\frac{\sigma^2}{b} + z\left(1-\beta_t\right)\kappa\zeta.$$

Recall that, by definition of $V_t$ in (6.49), $\mathbb{E}\left[\mathcal{L}_H\left(\boldsymbol{\theta}_{t-1}\right)-\mathcal{L}_H^*\right] + z\mathbb{E}\left[\left\|\boldsymbol{\xi}_{t-1}\right\|^2\right] + \kappa z\mathbb{E}\left[M_{t-1}^H\right] = \mathbb{E}\left[V_{t-1}\right]$. Therefore, the above can be written as

$$\mathbb{E}\left[V_t\right] \le \left(1-\frac{\mu}{4}\gamma_{t-1}\right)\mathbb{E}\left[V_{t-1}\right] + z\left(1-\beta_t\right)^2\left(\kappa+\frac{1}{n-f}\right)\sigma^2 + z\left(1-\beta_t\right)\kappa\zeta.$$

Substituting $\beta_t = 1-144L\gamma_{t-1}$ and $z = \frac{1}{64L}$ in the above concludes the proof.          $\square$

# Convergence Result

Note that the growth of the sequence $(\mathbb{E}\left[V_t\right])_{t \in [T+1]}$ presented in Theorem 6.2 corresponds to that of $(U_t)_{t \in [T+1]}$ in Lemma 3.1 with $U_t := \mathbb{E}\left[V_t\right]$ and $\alpha_1, \alpha_2, \alpha_3$ set as follows:

$$\alpha_1 := \frac{\mu}{4}, \alpha_2 := 324L\left(\kappa+\frac{1}{n-f}\right)\frac{\sigma^2}{b} \text{ and } \alpha_3 := \frac{9}{4}\kappa\zeta. \qquad (6.57)$$

Upon observing that $\mathcal{L}_H\left(\boldsymbol{\theta}_t\right)-\mathcal{L}_H^* \le V_t$ for each iteration $t$, owing to Theorem 6.2 above, we can thus obtain the sublinear convergence of Algorithm 6 in the strongly convex case similar to that of Algorithm 5. Essentially, upon combining the result of Theorem 6.2 with that of Lemma 3.1, we obtain the following corollary. For simplicity, we will state the corollary in terms of parameters $\alpha_2$ and $\alpha_3$ defined above in (6.57).

**Corollary 6.2** *Suppose Assumptions 3.1, 3.2, 4.1, and 4.2. Let $T$ be an even integer greater than 2. Consider $T$ iterations of Algorithm 6 with batch-size $b \in [1, m]$, an $(f, \kappa)$-robust aggregation rule $F$, a sequence of learning rates $(\gamma_t)_{t \in [T]}$ defined by*

$$\gamma_t = \begin{cases} \gamma_o & , \ t < T/2 \\ \frac{8}{\mu(s_o+t-\frac{T}{2})} & , \ t \ge T/2 \end{cases}, \qquad (6.58)$$