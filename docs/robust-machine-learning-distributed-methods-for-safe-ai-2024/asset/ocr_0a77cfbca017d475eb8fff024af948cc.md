then, provided that $T \ge \frac{16(n-f)bL\Delta_H}{\sigma^2}$, the following holds true:

$$\frac{1}{T}\sum_{t=1}^{T}\mathbb{E}\left[\|\nabla \mathcal{L}_H(\theta_t)\|^2\right] \le 8\sqrt{\frac{L\sigma^2\Delta_H}{(n-f)bT}}+3\kappa\left(\frac{4\sigma^2}{b}+\zeta\right).$$

**Proof** Note that all the conditions stated in Theorem 4.1 hold true. Therefore, from Theorem 4.1, we obtain that

$$\frac{1}{T}\sum_{t=1}^{T}\mathbb{E}\left[\|\nabla \mathcal{L}_H(\theta_t)\|^2\right] \le \frac{4(\mathcal{L}_H(\theta_1)-\mathcal{L}_H^*)}{\gamma T}+\frac{4L\sigma^2}{(n-f)b}\gamma+3\kappa\left(\frac{4\sigma^2}{b}+\zeta\right).$$

As $\mathcal{L}_H(\theta_1)-\mathcal{L}_H^*\le \Delta_H$ in the above, we have

$$\frac{1}{T}\sum_{t=1}^{T}\mathbb{E}\left[\|\nabla \mathcal{L}_H(\theta_t)\|^2\right] \le \frac{4\Delta_H}{\gamma T}+\frac{4L\sigma^2}{(n-f)b}\gamma+3\kappa\left(\frac{4\sigma^2}{b}+\zeta\right).$$

(4.29)

As it is assumed that $T \ge \frac{16(n-f)bL\Delta_H}{\sigma^2}$, by the definition of $\gamma$ in (4.28), we have

$$\gamma=\sqrt{\frac{(n-f)b\Delta_H}{\sigma^2LT}}.$$

Substituting from the above in (4.29) concludes the proof. $\square$

The corollary implies that if the server samples a model randomly from the set of all models generated during the execution of Robust DMGD, then (in expectation) the model approximates a stationary point of $\mathcal{L}_H$ with a bounded error, despite the presence of up to $f$ adversarial nodes. Specifically, under the conditions stated in Corollary 4.1 and upon executing $T$ iterations of the Robust DMGD algorithm, if the server outputs $\tilde{\theta}$ chosen uniformly from the set of intermediate models $\{\theta_1,\ldots,\theta_T\}$, then we achieve $(f,\epsilon)$-stationary resilience (as