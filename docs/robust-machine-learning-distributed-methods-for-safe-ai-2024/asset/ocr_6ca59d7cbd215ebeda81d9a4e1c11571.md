**Bound on \(\|\xi_t\|^2\).** From Lemma 6.3, we have

\[\mathbb{E}_t\left[\|\xi_t\|^2\right] \le (1 + 5L\gamma_{t-1} + 4L^2\gamma_{t-1}^2)\beta_t^2 \|\xi_{t-1}\|^2 + (1 - \beta_t)^2\frac{\sigma^2}{b(n-f)}\]

\[+ 2L\gamma_{t-1}(1 + \gamma_{t-1}L)\beta_t^2 \|\delta_{t-1}\|^2 + 4L\gamma_{t-1}(1 + \gamma_{t-1}L)\beta_t^2 \|\nabla\mathcal{L}_H(\theta_{t-1})\|^2.\]

Similarly to above, as \(\gamma_t \le \frac{1}{14L}\) for all \(t \in [T]\), we have \(1 + 5L\gamma_{t-1} + 4L^2\gamma_{t-1}^2 \le 1 + 5L\gamma_{t-1} + L\gamma_{t-1} = 1 + 6L\gamma_{t-1}\) and \(1 + \gamma_{t-1}L \le 2\). Using these in the above, we obtain that

\[\mathbb{E}_t\left[\|\xi_t\|^2\right] \le (1 + 6L\gamma_{t-1})\beta_t^2 \|\xi_{t-1}\|^2 + (1 - \beta_t)^2\frac{\sigma^2}{b(n-f)}\]

\[+ 4L\gamma_{t-1}\beta_t^2 \|\delta_{t-1}\|^2 + 8L\gamma_{t-1}\beta_t^2 \|\nabla\mathcal{L}_H(\theta_{t-1})\|^2.\]

Recall that, as \(F\) is \((f, \kappa)\)-robust averaging, \(\|\delta_t\|^2 \le \kappa M_t^H\) for all \(t \in [T]\). Using these in the above, and taking total expectation \(\mathbb{E}[\cdot]\), we obtain that

\[\mathbb{E}\left[\|\xi_t\|^2\right] \le (1 + 6L\gamma_{t-1})\beta_t^2 \mathbb{E}\left[\|\xi_{t-1}\|^2\right] + (1 - \beta_t)^2\frac{\sigma^2}{b(n-f)}\tag{6.51}\]

\[+ 4L\kappa\beta_t^2\gamma_{t-1}\mathbb{E}\left[M_{t-1}^H\right] + 8L\gamma_{t-1}\beta_t^2\mathbb{E}\left[\|\nabla\mathcal{L}_H(\theta_{t-1})\|^2\right].\]

**Bound on \(\mathbb{E}\left[M_t^H\right]\).** Lastly, from Lemma 6.6, we have

\[\mathbb{E}\left[M_t^H\right] \le \beta_t\mathbb{E}\left[M_{t-1}^H\right] + (1 - \beta_t)^2\frac{\sigma^2}{b} + (1 - \beta_t)\zeta.\tag{6.52}\]

Upon applying the total expectation \(\mathbb{E}[\cdot]\) in (6.49), and then substituting from (6.50), (6.51), and (6.52), we obtain that

\[\mathbb{E}[V_t] \le \mathbb{E}\left[\mathcal{L}_H(\theta_{t-1}) - \mathcal{L}_H^*\right] + 2\gamma_{t-1}\mathbb{E}\left[\|\xi_{t-1}\|^2\right]\]

\[+ 2\kappa\gamma_{t-1}\mathbb{E}\left[M_{t-1}^H\right] + z(1 + 6L\gamma_{t-1})\beta_t^2\mathbb{E}\left[\|\xi_{t-1}\|^2\right]\]

\[+ z(1 - \beta_t)^2\frac{\sigma^2}{b(n-f)}\]

\[+ z4\kappa\beta_t^2\gamma_{t-1}\mathbb{E}\left[M_{t-1}^H\right] + z\kappa\beta_t\mathbb{E}\left[M_{t-1}^H\right]\]

(continued)