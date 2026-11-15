Similarly, if $h_i^t = 0$ for $i \in \mathcal{V}$, it follows that

$$y_i^{t+1} = \sum_{j=1}^m b_{ij} y_j^t + \varepsilon_i^t.$$ (8.A.2)

By applying (8.A.1) and (8.A.2), and taking the conditional expectation with respect to $\mathcal{F}^t$, we obtain for any $i \in \mathcal{V}$, $i \in \mathcal{V}$,

$$\mathbb{E} [y_i^{t+1} | \mathcal{F}^t] = \sum_{j=1}^m b_{ij} y_j^t + \varepsilon_i^t - \eta_i \gamma_i^t \frac{p_i^t - d_i}{[z_i^t]_i},$$ (8.A.3)

where $\eta_i$ represents the probability that $h_i^t = 1$. Based on the definitions of $\varepsilon_i^t$ and $\gamma_i^t$, it follows that $\lim_{t \to \infty} \varepsilon_i^t = 0$ and $\lim_{t \to \infty} \gamma_i^t = 0$ for every $i \in \mathcal{V}$. Considering the facts that $0 \le \eta_i \le 1$, $|p_i^t - d_i| \le C$, and $\kappa^{-1} \le [z_i^t]_i \le 1$ for all $i \in \mathcal{V}$, we conclude that

$$\lim_{t \to \infty} |\varepsilon_i^t - \eta_i \gamma_i^t \frac{p_i^t - d_i}{[z_i^t]_i}| \le \lim_{t \to \infty} (\varepsilon_i^t + \eta_i \kappa C \gamma_i^t) = 0.$$ (8.A4)

Thus by applying Lemma 4 in [47], we obtain that $\lim_{t \to \infty} |y_i^t - \bar{y}^t| = 0$ almost surely for all $i \in \mathcal{V}$, completing the proof.

# Appendix 8.B Proof of Lemma 8.5

For any $i \in \mathcal{V}$, if $h_i^t = 1$, it follows for any $v \in \mathbb{R}$ that

$$|y_i^{t+1} - v|^2
= |v_i^t + \varepsilon_i^t - v|^2 + |\gamma_i^t \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i}|^2 + 2(v_i^t + \varepsilon_i^t - v)\gamma_i^t \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i}
\le \sum_{j=1}^m b_{ij} |y_j - v|^2 + 2\varepsilon_i^t (v_i^t - v) + |\varepsilon_i^t|^2 + |\gamma_i^t \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i}|^2
+ 2\gamma_i^t (v_i^t - v) \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i} + 2\varepsilon_i^t \gamma_i^t \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i},$$ (8.B.1)

where the inequality arises from the row-stochasticity of $B$ and the application of Jensen's inequality for the convex function $|\cdot|^2$. We can further infer that for all $t \ge \hat{t}$,

$$2\gamma_i^t \nabla Q_i(v_i^t)(v_i^t - v)
= 2(\gamma_i^t - \frac{1}{t \eta_i})\nabla Q_i(v_i^t)(v_i^t - v) + \frac{2}{t \eta_i} \nabla Q_i(v_i^t)(v_i^t - v)$$