ensure that $T \ge 2$. Next note that the assumption that

$$\inf_{n \in \{m \in \mathbb{N}_0: \ \forall k \in \mathbb{N}_0 \cap [0,m] \: \Theta_k \in \mathbb{B}\}} \mathcal{L} (\Theta_n) \ge \mathcal{L}(\vartheta)$$ (9.223)

demonstrates for all $n \in \mathbb{N}_0 \cap [0, T)$ that

$$\mathbb{L} (n) \ge 0.$$ (9.224)

Furthermore, observe that the fact that $\mathbb{B} \subseteq \mathbb{R}^3$ is open and convex, Corollary 9.12.3, and (9.217) demonstrate for all $n \in \mathbb{N}_0 \cap [0, T-1)$ that

$\begin{align*}\mathbb{L}(n+1) - \mathbb{L}(n) &= \mathcal{L}(\Theta_{n+1}) - \mathcal{L}(\Theta_n) \le -\frac{\gamma}{2}\|\mathcal{G}(\Theta_n)\|_2^2 = -\frac{1}{2}\|\mathcal{G}(\Theta_n)\|_2\|\gamma \mathcal{G}(\Theta_n)\|_2 \\
&= -\frac{1}{2}\|\mathcal{G}(\Theta_n)\|_2\|\Theta_{n+1} - \Theta_n\|_2 \le -(2\mathfrak{C})^{-1}[\mathcal{L}(\Theta_n) - \mathcal{L}(\vartheta)]^{\alpha}\|\Theta_{n+1} - \Theta_n\|_2 \\
&= -(2\mathfrak{C})^{-1}[\mathbb{L}(n)]^{\alpha}\|\Theta_{n+1} - \Theta_n\|_2 \le 0.\end{align*}$ (9.225)

Hence, we obtain that

$$\mathbb{N}_0 \cap [0, T) \ni n \to \mathbb{L} (n) \in [0, \infty)$$ (9.226)

is non-increasing. Combining this with (9.220) ensures for all $n \in \mathbb{N}_0 \cap [\tau, T)$ that

$$\mathbb{L}(n) = 0.$$ (9.227)

This and (9.225) demonstrate for all $n \in \mathbb{N}_0 \cap [\tau, T-1)$ that

$$0 = \mathbb{L}(n+1) - \mathbb{L}(n) \le -\frac{\gamma}{2}\|\mathcal{G}(\Theta_n)\|_2^2 \le 0.$$ (9.228)

The fact that $\gamma > 0$ therefore establishes for all $n \in \mathbb{N}_0 \cap [\tau, T-1)$ that $\mathcal{G}(\Theta_n) = 0$. Hence, we obtain for all $n \in \mathbb{N}_0 \cap [\tau, T)$ that

$$\Theta_n = \Theta_\tau.$$ (9.229)

Moreover, note that (9.220) and (9.225) ensure for all $n \in \mathbb{N}_0 \cap [0, \tau) \cap [0, T-1)$ that

$\begin{align*}\|\Theta_{n+1} - \Theta_n\|_2 &\le \frac{2\mathfrak{C}(\mathbb{L}(n) - \mathbb{L}(n+1))}{[\mathbb{L}(n)]^{\alpha}} = 2\mathfrak{C}\int_{\mathbb{L}(n+1)}^{\mathbb{L}(n)} [\mathbb{L}(n)]^{-\alpha} \, \mathrm{d}u \\
&\le 2\mathfrak{C}\int_{\mathbb{L}(n+1)}^{\mathbb{L}(n)} u^{-\alpha} \, \mathrm{d}u = \frac{2\mathfrak{C}([\mathbb{L}(n)]^{1-\alpha} - [\mathbb{L}(n+1)]^{1-\alpha})}{1-\alpha}.\end{align*}$ (9.230)

This and (9.229) show for all $n \in \mathbb{N}_0 \cap [0, T-1)$ that

$$\|\Theta_{n+1} - \Theta_n\|_2 \le \frac{2\mathfrak{C}([\mathbb{L}(n)]^{1-\alpha} - [\mathbb{L}(n+1)]^{1-\alpha})}{1-\alpha}.$$ (9.231)