**Proof** Consider an arbitrary iteration $t > 1$. Substituting from (6.1), $\mathbf{m}_t^{\mathbf{H}} = \beta_t \mathbf{m}_{t-1}^{\mathbf{H}} + (1 - \beta_t) \mathbf{g}_t^{\mathbf{H}}$, in (6.17) we obtain that

$$\boldsymbol{\xi}_t = \beta_t \mathbf{m}_{t-1}^{\mathbf{H}} + (1 - \beta_t) \mathbf{g}_t^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t).$$

By adding and subtracting $\beta_t \nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1})$ on the right-hand side, we obtain that

$$\begin{aligned}
\boldsymbol{\xi}_t &= \beta_t \left( \mathbf{m}_{t-1}^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) \right) + (1 - \beta_t) \left( \mathbf{g}_t^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \right) \\
&\quad + \beta_t \left( \nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \right).
\end{aligned}$$

Recalling that $\mathbf{m}_{t-1}^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) = \boldsymbol{\xi}_{t-1}$ in the above, we have

$$\boldsymbol{\xi}_t = \beta_t \boldsymbol{\xi}_{t-1} + (1 - \beta_t) \left( \mathbf{g}_t^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \right) + \beta_t \left( \nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \right).$$

Thus, as $\|\mathbf{v}\|^2 = \langle \mathbf{v}, \mathbf{v} \rangle$ for a real-valued vector $\mathbf{v}$, we obtain that

$$\begin{aligned}
\|\boldsymbol{\xi}_t\|^2 &= \beta_t^2 \|\boldsymbol{\xi}_{t-1}\|^2 + (1 - \beta_t)^2 \big\|\mathbf{g}_t^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\big\|^2 \\
&\quad + \beta_t^2 \big\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\big\|^2 \\
&\quad + 2\beta_t(1 - \beta_t)\big\langle \boldsymbol{\xi}_{t-1}, \mathbf{g}_t^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \big\rangle \\
&\quad + 2\beta_t^2 \big\langle \boldsymbol{\xi}_{t-1}, \nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \big\rangle \\
&\quad + 2\beta_t(1 - \beta_t)\big\langle \mathbf{g}_t^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t), \nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \big\rangle.
\end{aligned}$$

Recall that $\boldsymbol{\xi}_{t-1}$, $\boldsymbol{\theta}_{t-1}$, and $\boldsymbol{\theta}_t$ are deterministic functions of $\mathcal{P}_t$, (defined in (3.6)) and that $\mathbb{E}_t[\mathbf{g}_t^{\mathbf{H}}] = \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)$. Thus, applying the conditional expectation $\mathbb{E}_t[\cdot]$ on both sides in the above, we obtain that

$$\begin{aligned}
\mathbb{E}_t\big[\|\boldsymbol{\xi}_t\|^2\big] &= \beta_t^2 \|\boldsymbol{\xi}_{t-1}\|^2 + (1 - \beta_t)^2 \mathbb{E}_t\Big[\big\|\mathbf{g}_t^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\big\|^2\Big] \tag{6.18}\\
&\quad + \beta_t^2 \big\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\big\|^2 + 2\beta_t^2 \big\langle \boldsymbol{\xi}_{t-1}, \nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \big\rangle.
\end{aligned}$$

Under Assumption 3.2, as honest nodes compute local mini-batch gradients independently (given the current model $\boldsymbol{\theta}_t$), similarly to 3.13 in the proof of Theorem 3.1, we have $\mathbb{E}_t\big[\|\mathbf{g}_t^{\mathbf{H}} - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\|^2\big] \le \frac{\sigma^2}{b(n - f)}$. Moreover, due to Lipschitz smoothness, i.e., Assumption 3.1, we have