As $\gamma_t = \gamma \leq \frac{1}{4L}$ for all $t$, we have $\frac{1}{2} - L\gamma_t \geq \frac{1}{4}$. Moreover, $\left(\frac{1}{2} + L\gamma_t\right) \leq \left(\frac{1}{2} + \frac{L}{4L}\right) = \frac{3}{4}$. Thus, we have

$$\frac{1}{4}\mathbb{E}\left[\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\|^2\right] \leq \frac{\mathbb{E}[\mathcal{L}_H(\boldsymbol{\theta}_t)] - \mathbb{E}[\mathcal{L}_H(\boldsymbol{\theta}_{t+1})]}{\gamma_t} + \gamma_t \frac{L\sigma^2}{(n-f)b} + \frac{3}{4}\left(4\kappa\frac{\sigma^2}{b} + \kappa\zeta\right).$$

Upon substituting $\gamma_t = \gamma$ in the above, and then taking average on both sides over $t = 1$ to $t = T$, we obtain that

$$\frac{1}{T}\sum_{t=1}^T \mathbb{E}\left[\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\|^2\right] \leq \frac{4\left(\mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H(\boldsymbol{\theta}_{T+1})\right]\right)}{\gamma T} + \frac{4L\sigma^2}{(n-f)b}\gamma + 3\left(4\kappa\frac{\sigma^2}{b} + \kappa\zeta\right).$$

As $\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H(\boldsymbol{\theta}_{T+1}) \leq \mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H^*\text{,}^b$ and the initial model $\boldsymbol{\theta}_1$ is given to us, we have $\mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H(\boldsymbol{\theta}_{T+1})\right] \leq \mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H^*\right] = \mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H^*$. This concludes the proof.

$\square$

$^a$We can reason the same using the Jensen’s inequality on the square function $(\cdot)^2$.
$^b$Refer to the proof of Theorem 3.1 for the reasoning.

# **Stationary Resilience Property**

Upon selecting an appropriate value for the learning rate $\gamma$ in Theorem 4.1, we obtain the following corollary, which consequently enables us to characterize the stationary resilience property of Robust DMGD.

**Corollary 4.1** *Suppose Assumptions 3.1, 3.2 and 4.1. Consider T iterations of the Robust DMGD algorithm with batch-size $b \in [1, m)$ and an $(f, \kappa)$-robust averaging rule F. Let H be an arbitrary set of $n - f$ honest nodes and $\Delta_H$ be a real value such that $\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H^* \leq \Delta_H$. If*

$$\gamma_t = \gamma = \min\left\{\frac{1}{4L}, \sqrt{\frac{(n-f)b\Delta_H}{\sigma^2LT}}\right\}, \forall t \in [T],$$