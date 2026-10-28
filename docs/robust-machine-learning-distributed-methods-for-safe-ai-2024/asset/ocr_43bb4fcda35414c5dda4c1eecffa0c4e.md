# 3.2 Convergence of Distributed Mini-batch Gradient Descent (DMGD)

$(1 - \mu\gamma) \in [0, 1)$. Then, upon executing the DMGD algorithm for $T$ iterations, applying Theorem 3.2 recursively from $t = T$ to $t = 1$, we get

$$\mathbb{E}\left[\mathcal{L}(\boldsymbol{\theta}_{\mathbf{T}+1}) - \mathcal{L}^*\right] \leq (1 - \mu\gamma)^T \left(\mathcal{L}(\boldsymbol{\theta}_1) - \mathcal{L}^*\right) + \sum_{k=0}^{T-1} (1 - \mu\gamma)^k \frac{L\sigma^2}{2nb} \gamma^2.$$

(3.19)

As $(1 - \mu\gamma) \in [0, 1)$, the sum of the geometric series on the right-hand side of (3.19), i.e., $\sum_{k=0}^{T-1} (1 - \mu\gamma)^k$, is upper bounded by $\frac{1}{\mu\gamma}$. Using this in the above, we obtain that

$$\mathbb{E}\left[\mathcal{L}(\boldsymbol{\theta}_{\mathbf{T}+1}) - \mathcal{L}^*\right] \leq (1 - \mu\gamma)^T \left(\mathcal{L}(\boldsymbol{\theta}_1) - \mathcal{L}^*\right) + \frac{L\sigma^2}{2\mu nb} \gamma.$$

(3.20)

Although the above inequality provides a first characterization of the convergence rate of DMGD in the strongly convex case, we note that as $T$ increases, the right-hand side of (3.20) does not go to 0, as might be expected. Specifically, we have a residual error of $\frac{L\sigma^2}{2\mu nb}$, even when the number of iterations $T$ approaches infinity. This means that we cannot guarantee convergence of the algorithm to the optimal model $\boldsymbol{\theta}^* := \arg\min_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{\theta})$. To circumvent this shortcoming, we use a more refined scheduling of the learning rates, derived with the help of Lemma 3.1 presented below. The proof of Lemma 3.1 can be found in Appendix B.

**Lemma 3.1** Let $\alpha_1, \alpha_2, \alpha_3$ be real values such that $\alpha_1 > 0$, $\alpha_2 \geq 0$, and $\alpha_3 \geq 0$. Let $T > 2$ be an even number. Consider two positive real-valued sequences $(\gamma_1, \dots, \gamma_T)$ and $(U_1, \dots, U_{T+1})$ such that for all $t \in [T]$,

$$\gamma_t = \begin{cases} \gamma_o & , \ t < T/2 \\ \frac{2}{\alpha_1 (s_o + t - \frac{T}{2})} & , \ t \geq T/2 \end{cases}, \quad \text{and} \quad U_{t+1} \leq (1 - \alpha_1\gamma_t) U_t + \alpha_2\gamma_t^2 + \alpha_3\gamma_t,$$

where $\gamma_o$ and $s_o$ are positive real values such that $\gamma_o = \frac{2}{\alpha_1 s_o} < \frac{1}{\alpha_1}$. Then,

$$U_{T+1} \leq (s_o - 1)^2 U_1 \frac{4e^{-\frac{\alpha_1\gamma_o}{2}(T-2)}}{T^2} + \frac{4(\alpha_2\gamma_o + \alpha_3)(s_o - 1)^2}{\alpha_1 T^2} + \frac{8\alpha_2}{\alpha_1^2 T} + \frac{2\alpha_3}{\alpha_1}.$$

We use Lemma 3.1 to define an appropriate sequence of learning rates for DMGD and combine that with the observation on the dynamics of DMGD in Theorem 3.2 to obtain the following result for the convergence rate of DMGD to the minimum point of the loss function.