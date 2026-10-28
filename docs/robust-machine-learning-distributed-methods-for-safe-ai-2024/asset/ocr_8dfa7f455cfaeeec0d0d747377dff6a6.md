$$+ z\kappa (1 - \beta_t)^2 \frac{\sigma^2}{b} + z(1 - \beta_t)\kappa \zeta$$
$$- \gamma_{t-1} \left( \frac{1}{2} - 2\gamma_{t-1}L \right) \mathbb{E} \left[ \|\nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2 \right]$$
$$+ 8Lz\gamma_{t-1}\beta_t^2 \mathbb{E} \left[ \|\nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2 \right].$$

Recall that, due to Assumption 4.2, $\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2 \geq 2\mu \left( \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \mathcal{L}_H^* \right)$. Using this and rearranging the terms, we obtain that

$$\mathbb{E}[V_t] \leq \left( 1 - 2\mu\gamma_{t-1}\left( \frac{1}{2} - 2\gamma_{t-1}L - 8Lz\beta_t^2 \right) \right) \mathbb{E} \left[ \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \mathcal{L}_H^* \right]$$
$$+ \left( 2\gamma_{t-1} + z(1 + 6L\gamma_{t-1})\beta_t^2 \right) \mathbb{E} \left[ \|\boldsymbol{\xi}_{t-1}\|^2 \right]$$
$$+ z(1 - \beta_t)^2 \left( \kappa + \frac{1}{n-f} \right) \frac{\sigma^2}{b}$$
$$+ \kappa \left( 2\gamma_{t-1} + z4L\beta_t^2\gamma_{t-1} + z\beta_t \right) \mathbb{E} \left[ M_{t-1}^H \right] + z\kappa(1 - \beta_t)\zeta. \quad (6.53)$$

Let us denote

$$A_t := 2\gamma_{t-1} + z(1 + 6L\gamma_{t-1})\beta_t^2, \quad \text{and} \quad B_t := 2\gamma_{t-1} + z4L\beta_t^2\gamma_{t-1} + z\beta_t.$$

Substituting from above in (6.53), we can rewrite

$$\mathbb{E}[V_t] \leq \left( 1 - 2\mu\gamma_{t-1}\left( \frac{1}{2} - 2\gamma_{t-1}L - 8Lz\beta_t^2 \right) \right) \mathbb{E} \left[ \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \mathcal{L}_H^* \right]$$
$$+ A_t \mathbb{E} \left[ \|\boldsymbol{\xi}_{t-1}\|^2 \right] + B_t\kappa \mathbb{E} \left[ M_{t-1}^H \right] + z(1 - \beta_t)^2 \left( \kappa + \frac{1}{n-f} \right) \frac{\sigma^2}{b}$$
$$+ z(1 - \beta_t)\kappa\zeta.$$

Note that, as $z = \frac{1}{64L}$, $\beta_t \leq 1$, and $\frac{1}{144L}$, we have

$$\frac{1}{2} - 2\gamma_{t-1}L - 8Lz\beta_t^2 \geq \frac{1}{2} - 2\gamma_{t-1}L - \frac{1}{8} \geq \frac{1}{8}.$$