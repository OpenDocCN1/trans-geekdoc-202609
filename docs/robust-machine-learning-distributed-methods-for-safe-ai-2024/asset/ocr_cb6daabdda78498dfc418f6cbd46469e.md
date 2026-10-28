Upon substituting $A_t$ (from (4.17)) in the above, we obtain that

$$\mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \mathbf{g}_t^H\right\|^2\right] \le 2\mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \nabla\mathcal{L}_i(\boldsymbol{\theta}_t)\right\|^2\right] + 2\mathbb{E}_t\left[\left\|\nabla\mathcal{L}_H - \mathbf{g}_t^H\right\|^2\right]$$

$$+ \mathbb{E}_t\left[\left\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right].$$

Recall, from the proof of Theorem 3.1, that under Assumption 3.2, we have $\mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \nabla\mathcal{L}_i(\boldsymbol{\theta}_t)\right\|^2\right] \le \frac{\sigma^2}{b}$. Consequently, as the honest nodes compute independently their local gradients, and $|H| = n - f$, we have $\mathbb{E}_t\left[\left\|\nabla\mathcal{L}_H - \mathbf{g}_t^H\right\|^2\right] \le \frac{\sigma^2}{(n-f)b} \le \frac{\sigma^2}{b}$. Using these observations in the above, we obtain that

$$\mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \mathbf{g}_t^H\right\|^2\right] \le \frac{4\sigma^2}{b} + \mathbb{E}_t\left[\left\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right].$$

The above holds true for each node $i \in H$. Therefore,

$$\frac{\sum_{i \in H} \mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \mathbf{g}_t^H\right\|^2\right]}{n - f} \le \frac{4\sigma^2}{b} + \frac{\sum_{i \in H} \mathbb{E}_t\left[\left\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right]}{n - f}.$$

Due to Assumption 4.1, $\frac{1}{n-f} \sum_{i \in H} \mathbb{E}_t\left[\left\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right] \le \zeta$. Thus, from above we obtain that

$$\frac{1}{n-f} \sum_{i \in H} \mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \mathbf{g}_t^H\right\|^2\right] \le \frac{4\sigma^2}{b} + \zeta.$$

Applying the conditional expectation $\mathbb{E}_t[\cdot]$ on both sides in (4.16) and then substituting from the above conclude the proof. $\square$

The above upper bound for $\delta_t$ plays a crucial role in the following analyses on the convergence of robust DSGD. We begin by considering the case where the loss function is a non-convex function, as we did in Chap. 3. Some of the results derived for this case later prove useful, when dealing with strongly convex loss function.