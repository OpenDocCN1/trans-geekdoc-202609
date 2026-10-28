Therefore, we note that both the sequences $(\gamma_t)_{t\in[T]}$ and $(U_t)_{t\in[T+1]}$ satisfy the condition stated in Lemma 3.1, with a value for $\alpha_1$ as defined above, and for $\alpha_2, \alpha_3$ defined as

$$\alpha_2 = 324L \left( \kappa + \frac{1}{n-f} \right) \frac{\sigma^2}{b} \quad \text{and} \quad \alpha_3 = \frac{9}{4}\kappa\zeta \,. \tag{6.59}$$

Lastly, owing to Lemma 3.1, we obtain that

$$\begin{aligned} U_{T+1} &\le (s_o - 1)^2 U_1 \frac{4 e^{-\alpha_1 \gamma_o \frac{(T-2)}{T^2}}}{T^2} \\ &+ \frac{4(\alpha_2\gamma_o + \alpha_3)(s_o - 1)^2}{\alpha_1 T^2} \\ &+ \frac{8\alpha_2}{\alpha_1^2 T} + \frac{2\alpha_3}{\alpha_1}\,. \end{aligned}$$

As $U_1 = \mathbb{E}[V_1]$, from the definition of $V_t$ in (6.48), we have

$$\begin{aligned} U_1 &= \left( \mathcal{L}_H(\pmb{\theta}_1) - \mathcal{L}_H^* \right) \\ &+ \frac{1}{64L} \left( \mathbb{E}\left[\|\pmb{\xi}_1\|^2\right] + \kappa \frac{1}{|H|} \sum_{i\in H} \mathbb{E}\left[\left\|\mathbf{m}_1^{(i)} - \mathbf{m}_1^H\right\|^2\right] \right)\,. \end{aligned}$$

Simply using Lemmas 6.3 and 6.6 in the above with $\beta_1 = 0$, we get

$$U_1 \le \left( \mathcal{L}_H(\pmb{\theta}_1) - \mathcal{L}_H^* \right) + \frac{1}{64L} \left( \frac{\sigma^2}{b(n-f)} + \kappa \left( \frac{\sigma^2}{b} + \zeta \right) \right) = \frac{\Delta_0}{(s_o - 1)^2}\,.$$

Replacing $\alpha_1$ in the above, and then noting that $\mathbb{E}\left[\mathcal{L}_H\left(\pmb{\theta}_{T+1}\right) - \mathcal{L}_H^*\right] \le U_{T+1} := \mathbb{E}[V_{T+1}]$ (by definition of $V_t$ in (6.48)), concludes the proof. $\square$

# **Resilience of Algorithm 6**

Similarly to the non-convex case, we use the above corollary to deduce the resilience properties of Robust DMHB. Recall that, in the case of strong convexity, the output model denoted by $\hat{\pmb{\theta}}$ is taken to be equal to the last iterate of the algorithm, i.e., $\hat{\pmb{\theta}} = \pmb{\theta}_{T+1}$. According to Corollary 6.1, upon executing $T$ iterations of Algorithm 6, under the conditions stated in Corollary 6.2, if the server outputs $\hat{\pmb{\theta}} = \pmb{\theta}_{T+1}$, despite