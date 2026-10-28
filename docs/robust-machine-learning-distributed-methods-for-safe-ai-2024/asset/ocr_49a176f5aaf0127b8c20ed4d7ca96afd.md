If the aggregation $F$ is an $(f, \kappa)$-robust averaging, then, for $H \subseteq [n]$ comprising $n - f$ honest nodes, the following holds true:

$$\mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_{t+1}) - \mathcal{L}_H^*\right] \leq \left(1 - \frac{\mu}{2}\gamma_t\right)\mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_t) - \mathcal{L}_H^*\right]$$
$$+ \gamma_t^2 L\left(\frac{\sigma^2}{(n-f)b} + 4\kappa\frac{\sigma^2}{b} + \kappa\zeta\right) + \gamma_t\frac{\kappa}{2}\left(\frac{4\sigma^2}{b} + \zeta\right). \quad (4.31)$$

**Proof** Similarly to (4.27) in the proof of Theorem 4.1, under Assumptions 3.1, 3.2, and 4.1, we obtain that

$$\mathbb{E}_t\left[\mathcal{L}_H(\boldsymbol{\theta}_{t+1})\right] \leq \mathcal{L}_H(\boldsymbol{\theta}_t) - \gamma_t\left(\frac{1}{2} - L\gamma_t\right)\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\|^2 + \gamma_t^2\frac{L\sigma^2}{(n-f)b}$$
$$+ \gamma_t\left(\frac{1}{2} + L\gamma_t\right)\left(4\kappa\frac{\sigma^2}{b} + \kappa\zeta\right).$$

Taking total expectation on both sides and denoting $U_t := \mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_t) - \mathcal{L}_H^*\right]$, we obtain that

$$U_{t+1} \leq U_t - \gamma_t\left(\frac{1}{2} - L\gamma_t\right)\mathbb{E}\left[\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\|^2\right] + \gamma_t^2\frac{L\sigma^2}{(n-f)b}$$
$$+ \gamma_t\left(\frac{1}{2} + L\gamma_t\right)\left(4\kappa\frac{\sigma^2}{b} + \kappa\zeta\right).$$

As $0 < \gamma_t \leq \frac{1}{4L}$, from the above we obtain that

$$U_{t+1} \leq U_t - \frac{\gamma_t}{4}\mathbb{E}\left[\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\|^2\right] + \gamma_t^2\frac{L\sigma^2}{(n-f)b}$$
$$+ \gamma_t\left(\frac{1}{2} + L\gamma_t\right)\kappa\left(\frac{4\sigma^2}{b} + \zeta\right).$$

Due to Assumption 4.2, we have

$$\mathbb{E}\left[\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\|^2\right] \geq \mathbb{E}\left[2\mu\left(\mathcal{L}_H(\boldsymbol{\theta}_t) - \mathcal{L}_H^*\right)\right] = 2\mu U_t.$$