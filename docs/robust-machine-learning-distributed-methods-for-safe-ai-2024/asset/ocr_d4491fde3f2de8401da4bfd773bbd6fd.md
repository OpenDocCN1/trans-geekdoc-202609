Note that we can rewrite the above as

$$\mathbb{E}_t\Big[\big\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{(j)}\big\|^2\Big] \le \beta_t \big\|\mathbf{m}_{t-1}^{(i)} - \mathbf{m}_{t-1}^{(j)}\big\|^2 + (1 - \beta_t)\big\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_j(\boldsymbol{\theta}_t)\big\|^2 + 2(1 - \beta_t)^2\frac{\sigma^2}{b}. $$

Applying Jensen’s inequality, from the above, we obtain that

$$\mathbb{E}_t\Big[\big\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{(j)}\big\|^2\Big] \le \beta_t \big\|\mathbf{m}_{t-1}^{(i)} - \mathbf{m}_{t-1}^{(j)}\big\|^2 + (1 - \beta_t)\big\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_j(\boldsymbol{\theta}_t)\big\|^2 + 2(1 - \beta_t)^2\frac{\sigma^2}{b}. $$

Taking the total expectation $\mathbb{E}[\cdot]$ on both sides, we have

$$\mathbb{E}\Big[\big\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{(j)}\big\|^2\Big] \le \beta_t \mathbb{E}\Big[\big\|\mathbf{m}_{t-1}^{(i)} - \mathbf{m}_{t-1}^{(j)}\big\|^2\Big] + (1 - \beta_t)\mathbb{E}\Big[\big\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_j(\boldsymbol{\theta}_t)\big\|^2\Big] + 2(1 - \beta_t)^2\frac{\sigma^2}{b}. $$

Recall that $i$ and $j$ in the above are chosen arbitrarily from $H$. Therefore, by taking the average on both sides over all the pairs $(i, j) \in H$, we obtain that

$$\frac{1}{|H|^2}\sum_{i,j\in H}\mathbb{E}\Big[\big\|\mathbf{m}_t^{(i)} - \mathbf{m}_t^{(j)}\big\|^2\Big] \le \beta_t\frac{1}{|H|^2}\sum_{i,j\in H}\mathbb{E}\Big[\big\|\mathbf{m}_{t-1}^{(i)} - \mathbf{m}_{t-1}^{(j)}\big\|^2\Big] + (1 - \beta_t)\frac{1}{|H|^2}\sum_{i,j\in H}\mathbb{E}\Big[\big\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_j(\boldsymbol{\theta}_t)\big\|^2\Big] + 2(1 - \beta_t)^2\frac{\sigma^2}{b}. $$

Recall, from Remark 4.5, that for a set of $m$ vectors $\mathbf{v}_1,\dots,\mathbf{v}_m$, we have $\sum_{i,j\in[m]}\|\mathbf{v}_i - \mathbf{v}_j\|^2 = 2m\sum_{i\in[m]}\Big\|\mathbf{v}_i - \frac{1}{m}\sum_{j\in[m]}\mathbf{v}_j\Big\|^2$. Using this in the