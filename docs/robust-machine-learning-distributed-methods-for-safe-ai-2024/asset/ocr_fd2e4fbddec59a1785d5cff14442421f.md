As $\frac{m-b}{m-1} \le 1$, using Assumption 3.2 in the above implies that, for all $i \in [n]$,

$$\mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \nabla \mathcal{L}_i(\boldsymbol{\theta}_t)\right\|^2\right] \le \frac{\sigma^2}{b}.$$

Using this in (3.12) and subsequently in (3.11), we obtain that

$$\mathbb{E}_t\left[\left\|\bar{\mathbf{g}}_t - \nabla \mathcal{L}(\boldsymbol{\theta}_t)\right\|^2\right] \le \frac{\sigma^2}{nb}. \qquad (3.13)$$

As $\langle \mathbb{E}_t[\bar{\mathbf{g}}_t] - \nabla \mathcal{L}(\boldsymbol{\theta}_t),\ \nabla \mathcal{L}(\boldsymbol{\theta}_t)\rangle = 0$ (see (3.9)), due to (3.13), the following holds true.

$$\mathbb{E}_t\left[\|\bar{\mathbf{g}}_t\|^2\right] = \mathbb{E}_t\left[\|\bar{\mathbf{g}}_t - \nabla \mathcal{L}(\boldsymbol{\theta}_t)\|^2\right] + \|\nabla \mathcal{L}(\boldsymbol{\theta}_t)\|^2 \le \frac{\sigma^2}{nb} + \|\nabla \mathcal{L}(\boldsymbol{\theta}_t)\|^2.$$

Substituting from the above in (3.10), taking total expectation $\mathbb{E}[\cdot]$ on both sides, and rearranging the terms yield the following:

$$\mathbb{E}\left[\mathcal{L}(\boldsymbol{\theta}_{t+1})\right] \le \mathbb{E}\left[\mathcal{L}(\boldsymbol{\theta}_t)\right] - \gamma_t \left(1 - \frac{L}{2}\gamma_t\right)\mathbb{E}\left[\|\nabla \mathcal{L}(\boldsymbol{\theta}_t)\|^2\right] + \frac{L\sigma^2}{2nb}\gamma_t^2, \qquad (3.14)$$

which can equivalently be written as (recalling that $\gamma_t > 0$)

$$\left(1 - \frac{L}{2}\gamma_t\right)\mathbb{E}\left[\|\nabla \mathcal{L}(\boldsymbol{\theta}_t)\|^2\right] \le \frac{\mathbb{E}\left[\mathcal{L}(\boldsymbol{\theta}_t)\right] - \mathbb{E}\left[\mathcal{L}(\boldsymbol{\theta}_{t+1})\right]}{\gamma_t} + \frac{L\sigma^2}{2nb}\gamma_t.$$

Lastly, recall that for all $t \in [T]$, we have $\gamma_t = \gamma \le \frac{1}{L}$, hence $1 - \frac{L}{2}\gamma_t \ge \frac{1}{2}$. Thus, upon substituting $\gamma_t = \gamma$ in the above and summing both sides from $t = 1$ to $t = T$, we obtain that

$$\sum_{t=1}^T \mathbb{E}\left[\|\nabla \mathcal{L}(\boldsymbol{\theta}_t)\|^2\right] \le \frac{2\mathbb{E}\left[\mathcal{L}(\boldsymbol{\theta}_1) - \mathcal{L}(\boldsymbol{\theta}_{T+1})\right]}{\gamma} + \frac{L\sigma^2}{nb}\gamma T. \qquad (3.15)$$

Note that as $\mathcal{L}(\boldsymbol{\theta}) \ge \mathcal{L}^*$ for all $\boldsymbol{\theta} \in \mathbb{R}^d$, we have $\mathcal{L}(\boldsymbol{\theta}_1) - \mathcal{L}(\boldsymbol{\theta}_{T+1}) = \mathcal{L}(\boldsymbol{\theta}_1) - \mathcal{L}^* + \mathcal{L}^* - \mathcal{L}(\boldsymbol{\theta}_{T+1}) \le \mathcal{L}(\boldsymbol{\theta}_1) - \mathcal{L}^*$. Using this in (3.15), and dividing both sides by $T$, concludes the proof. $\square$

The convergence result shown in Theorem 3.1 tells us that, upon selecting an appropriate learning rate $\gamma$, the DMGD algorithm generates a sequence of models