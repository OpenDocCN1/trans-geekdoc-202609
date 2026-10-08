
and let $\mathcal{X}_n: E \times \Omega \to \mathcal{E}$, $n \in \mathbb{N}$, satisfy for all $n \in \mathbb{N}$, $x \in E$, $\omega \in \Omega$ that

$$\mathcal{X}_n(x, \omega)=X\left(P_{n}(x), \omega\right). \quad(11.54)$$

Note that (11.54) shows that for all $n \in \mathbb{N}$, $B \in \mathcal{B}(\mathcal{E})$ it holds that

$$
\begin{align*}
\left(\mathcal{X}_{n}\right)^{-1}(B) & =\{\{x, \omega\} \in E \times \Omega: \mathcal{X}_{n}(x, \omega) \in B\} \\
& =\bigcup_{y \in \operatorname{Im}\left(P_{n}\right)}\left(\left[\left(X_{n}\right)^{-1}(B)\right] \cap\left(\left(P_{n}\right)^{-1}(\{y\}) \times \Omega\right)\right) \\
& =\bigcup_{y \in \operatorname{Im}\left(P_{n}\right)}\left\{\{x, \omega\} \in E \times \Omega: \left[\mathcal{X}_{n}(x, \omega) \in B \text { and } x \in\left(P_{n}\right)^{-1}\left(\{y\}\right)\right]\right\} \\
& =\bigcup_{y \in \operatorname{Im}\left(P_{n}\right)}\left\{\{x, \omega\} \in E \times \Omega: \left[X\left(P_{n}(x), \omega\right) \in B \text { and } x \in\left(P_{n}\right)^{-1}\left(\{y\}\right)\right]\right\}.
\end{align*}
\tag{11.55}
$$

Item (ii) in Lemma 11.2.5 therefore implies that for all $n \in \mathbb{N}$, $B \in \mathcal{B}(\mathcal{E})$ it holds that

$$
\begin{align*}
\left(\mathcal{X}_{n}\right)^{-1}(B) & =\bigcup_{y \in \operatorname{Im}\left(P_{n}\right)}\left\{\{x, \omega\} \in E \times \Omega: \left[X\left(y, \omega\right) \in B \text { and } x \in\left(P_{n}\right)^{-1}\left(\{y\}\right)\right]\right\} \\
& =\bigcup_{y \in \operatorname{Im}\left(P_{n}\right)}\left(\left\{\{x, \omega\} \in E \times \Omega: X\left(y, \omega\right) \in B\right\} \cap\left(\left(P_{n}\right)^{-1}\left(\{y\}\right) \times \Omega\right)\right) \\
& =\bigcup_{y \in \operatorname{Im}\left(P_{n}\right)}\left(\underbrace{\left[E \times\left(X(y, \cdot)^{-1}(B)\right)\right]}_{\in \mathcal{B}(E) \otimes \mathbb{F}} \cap \underbrace{\left[\left(P_{n}\right)^{-1}\left(\{y\}\right) \times \Omega\right]}_{\in \mathcal{B}(E) \otimes \mathbb{F}}\right) \in\left(\mathcal{B}(\mathcal{E}) \otimes \mathbb{F}\right).
\end{align*}
\tag{11.56}
$$

This demonstrates that for all $n \in \mathbb{N}$ it holds that $\mathcal{X}_{n}$ is $(\mathcal{B}(\mathcal{E}) \otimes \mathbb{F}) / \mathcal{B}(\mathcal{E})$-measurable. Furthermore, observe that item (i) in Lemma 11.2.5 and the assumption that for all $\omega \in \Omega$ it holds that $E \ni x \mapsto X(x, \omega) \in \mathcal{E}$ is continuous ensure that for all $x \in E$, $\omega \in \Omega$ it holds that

$$\operatorname*{lim}_{n \rightarrow \infty} \mathcal{X}_{n}(x, \omega)=\operatorname*{lim}_{n \rightarrow \infty} X\left(P_{n}(x), \omega\right)=X(x, \omega). \quad(11.57)$$

Combining this with the fact that for all $n \in \mathbb{N}$ it holds that $\mathcal{X}_{n}: E \times \Omega \to \mathcal{E}$ is $(\mathcal{B}(E) \otimes \mathbb{F}) / \mathcal{B}(E)$-measurable establishes that $X: E \times \Omega \to \mathcal{E}$ is $(\mathcal{B}(E) \otimes \mathbb{F}) / \mathcal{B}(\mathcal{E})$-measurable. The proof of Lemma 11.2.6 is thus complete. $\square$

## 11.2.3 Strong convergence rates for the optimization error

**Proposition 11.2.7.** *Let* $d, K \in \mathbb{N}$, $L, \alpha \in \mathbb{R}$, $\beta \in (\alpha, \infty)$, *let* $(\Omega$, $\mathcal{F}$, $\mathbb{P}$) *be a probability space, let* $\Re: [\alpha, \beta]^{\mathrm{d}} \times \Omega \rightarrow \mathbb{R}$ *be a random field, assume for all* $\theta, \vartheta \in [\alpha, \beta]^{\mathrm{d}}$, $\omega \in \Omega$ *that* $|\Re(\theta, \omega) - \Re(\vartheta, \omega)| \leq L\|\theta - \vartheta\|_{\infty}$, *let* $\Theta_{\mathbf{k}} : \Omega \to [\alpha, \beta]^{\mathrm{d}}$, $\mathbf{k} \in \{1, 2, \ldots, K\}$, *be i.i.d. random variables, and assume that* $\Theta_{\mathbf{i}}$ *is continuously uniformly distributed on* $[\alpha, \beta]^{\mathrm{d}}$ *(cf. Definition 3.3.4). Then*

(i) it holds that $\mathscr{R}$ is $(\mathcal{B}([\alpha, \beta]^\mathbf{d}) \otimes \mathcal{F}) / \mathcal{B}(\mathbb{R})$-measurable and

(ii) it holds for all $\theta \in [\alpha, \beta]^\mathbf{d}$, $p \in (0, \infty)$ that

$$
\left( \mathbb{E}\left[ \min_{k \in \{1,2,\ldots,K\}} |\mathscr{R}(\Theta_k) - \mathscr{R}(\theta)|^p \right] \right)^{1/p}
\leq \frac{L(\beta-\alpha) \max \left\{1, (p/\alpha)^{1/d} \right\}}{K^{1/d}}
\leq \frac{L(\beta-\alpha) \max \left\{1, p \right\}}{K^{1/d}}.
$$
(11.58)

Proof of Proposition 11.2.7. Throughout this proof, assume without loss of generality that $L > 0$, let $\delta : ([\alpha, \beta]^\mathbf{d}) \times ([\alpha, \beta]^\mathbf{d} \rightarrow [0, \infty)$ satisfy for all $\theta, \vartheta \in [\alpha, \beta]^\mathbf{d}$ that

$$
\delta(\theta, \vartheta) = \|\theta - \vartheta\|_\infty, 
$$
(11.59)

let $\mathbb{B} : (0, \infty)^2 \rightarrow (0, \infty)$ satisfy for all $x, y \in (0, \infty)$ that

$$
\mathbb{B}(x, y) = \int_0^1 t^{x-1}(1-t)^{y-1}\,\mathrm{d}t,
$$
(11.60)

and let $\Theta_{1,1}, \Theta_{1,2}, \ldots, \Theta_{1,\mathbf{d}} : \Omega \rightarrow [\alpha, \beta]$ satisfy $\Theta_1 = (\Theta_{1,1}, \Theta_{1,2}, \ldots, \Theta_{1,\mathbf{d}})$. First, note that the assumption that for all $\theta, \vartheta \in [\alpha, \beta]^\mathbf{d}$, $\omega \in \Omega$ it holds that

$$
|\mathscr{R}(\theta, \omega) - \mathscr{R}(\vartheta, \omega)| \leq L\|\theta - \vartheta\|_\infty
$$
(11.61)

proves that for all $\omega \in \Omega$ it holds that $[\alpha, \beta]^\mathbf{d} \ni \theta \mapsto \mathscr{R}(\theta, \omega) \in \mathbb{R}$ is continuous. Combining this with the fact that $([\alpha, \beta]^\mathbf{d}, \delta)$ is a separable metric space, the fact that for all $\theta \in [\alpha, \beta]^\mathbf{d}$ it holds that $\Omega \ni \omega \mapsto \mathscr{R}(\theta, \omega) \in \mathbb{R}$ is $\mathcal{F}/\mathcal{B}(\mathbb{R})$-measurable, and Lemma 11.2.6 establishes item (1). Observe that the fact that for all $\theta \in [\alpha, \beta]$, $\varepsilon \in [0, \infty)$ it holds that

$$
\begin{aligned}
& \min \left\{ \theta + \varepsilon, \beta \right\} - \max \left\{ \theta - \varepsilon, \alpha \right\}
= \min \left\{ \theta + \varepsilon, \beta \right\} + \min \left\{ \varepsilon - \theta, - \alpha \right\} \\
& = \min \left\{ \theta + \varepsilon + \min \left\{ \varepsilon - \theta, - \alpha \right\}, \beta + \min \left\{ \varepsilon - \theta, - \alpha \right\} \right\} \\
& = \min \left\{ \min \left\{ 2\varepsilon, \theta - \alpha + \varepsilon \right\}, \min \left\{ \beta - \theta + \varepsilon, \beta - \alpha \right\} \right\} \\
& \geq \min \left\{ \min \left\{ 2\varepsilon, \alpha - \alpha + \varepsilon \right\}, \min \left\{ \beta - \beta + \varepsilon, \beta - \alpha \right\} \right\} \\
& = \min \left\{ 2\varepsilon, \varepsilon, \varepsilon, \beta - \alpha \right\}
= \min \left\{ \varepsilon, \beta - \alpha \right\}
\end{aligned}
$$
(11.62)

and the assumption that $\Theta_1$ is continuously uniformly distributed on $[\alpha, \beta]^\mathbf{d}$ show that for all $\boldsymbol{\theta} = (\theta_1, \theta_2, \dots, \theta_d) \in [\alpha, \beta]^\mathbf{d}$, $\varepsilon \in [0, \infty)$ it holds that

$$
\begin{aligned}
& \mathbb{P}(\|\Theta_1 - \theta\|_\infty \le \varepsilon) = \mathbb{P}(\max_{i \in \{1, \dots, d\}}|\Theta_{1, i} - \theta_i| \le \varepsilon) \\
& = \mathbb{P}(\forall i \in \{1, 2, \dots, \mathbf{d}\}\!\!: -\varepsilon \le \Theta_{1, i} - \theta_i \le \varepsilon) \\
& = \mathbb{P}(\forall i \in \{1, 2, \dots, \mathbf{d}\}\!\!: \theta_i - \varepsilon \le \Theta_{1, i} \le \theta_i + \varepsilon) \\
& = \mathbb{P}(\forall i \in \{1, 2, \dots, \mathbf{d}\}\!\!: \max\{\theta_i - \varepsilon, \alpha\} \le \Theta_{1, i} \le \min\{\theta_i + \varepsilon, \beta\}) \\
& = \mathbb{P}\bigl(\Theta_1 \in \bigl[\prod_{i=1}^d \bigl[\max\{\theta_i - \varepsilon, \alpha\}, \min\{\theta_i + \varepsilon, \beta\}\bigr] \bigr) \\
& = \frac{1}{(\beta - \alpha)^d} \prod_{i=1}^d \bigl( \min\{\theta_i + \varepsilon, \beta\} - \max\{\theta_i - \varepsilon, \alpha\} \bigr) \\
& \ge \frac{1}{(\beta - \alpha)^d} \bigl[\min\{\varepsilon, \beta - \alpha\} \bigr]^d = \min \bigg\{ 1, \frac{\varepsilon^d}{(\beta - \alpha)^d} \bigg\}.
\end{aligned}
\tag{11.63}
$$

Hence, we obtain for all $\boldsymbol{\theta} \in [\alpha, \beta]^\mathbf{d}$, $p \in (0, \infty)$, $\varepsilon \in [0, \infty)$ that

$$
\begin{aligned}
& \mathbb{P}(\|\Theta_1 - \theta\|_\infty > \varepsilon^{1/p}) = 1 - \mathbb{P}(\|\Theta_1 - \theta\|_\infty \le \varepsilon^{1/p}) \\
& \le 1 - \min \bigg\{ 1, \frac{\varepsilon^{d/p}}{(\beta - \alpha)^d} \bigg\} = \max \bigg\{ 0, 1 - \frac{\varepsilon^{d/p}}{(\beta - \alpha)^d} \bigg\}.
\end{aligned}
\tag{11.64}
$$

This, item **(i)**, the assumption that for all $\theta, \vartheta \in [\alpha, \beta]^\mathbf{d}$, $\omega \in \Omega$ it holds that

$$
|\mathfrak{R}(\theta, \omega) - \mathfrak{R}(\vartheta, \omega)| \le L \|\theta - \vartheta\|_\infty,\tag{11.65}
$$

the assumption that $\Theta_k$, $k \in \{1, 2, \dots, K\}$, are i.i.d. random variables, and Lemma **11.1.2** (applied with $(E, \delta) \curvearrowright ([\alpha, \beta]^\mathbf{d}, \delta)$, $(X_k)_{k \in \{1, 2, \dots, K\}} \curvearrowright (\Theta_k)_{k \in \{1, 2, \dots, K\}}$ in the notation of Lemma **11.1.2**) imply that for all $\boldsymbol{\theta} \in [\alpha, \beta]^\mathbf{d}$, $p \in (0, \infty)$ it holds that

$$
\begin{aligned}
& \mathbb{E}\bigl[ \min_{k \in \{1, 2, \dots, K\}} |\mathfrak{R}(\Theta_k) - \mathfrak{R}(\theta)|^p \bigr] \le L^p \int_0^\infty \bigl[ \mathbb{P}(\|\Theta_1 - \theta\|_\infty > \varepsilon^{1/p}) \bigr]^K \, \mathrm{d}\varepsilon \\
& \le L^p \int_0^\infty \bigg[ \max \bigg\{ 0, 1 - \frac{\varepsilon^{d/p}}{(\beta - \alpha)^d} \bigg\} \bigg]^K \, \mathrm{d}\varepsilon = L^p \int_0^{(\beta - \alpha)^p} \bigg( 1 - \frac{\varepsilon^{d/p}}{(\beta - \alpha)^d} \bigg)^K \, \mathrm{d}\varepsilon \\
& = \frac{p}{d} L^p (\beta - \alpha)^p \int_0^1 t^{p/d - 1} (1 - t)^K \, \mathrm{d}t = \frac{p}{d} L^p (\beta - \alpha)^p \int_0^1 t^{p/d - 1} (1 - t)^{K + 1 - 1} \, \mathrm{d}t \\
& = \frac{p}{d} L^p (\beta - \alpha)^p \, \mathbb{B}(p/d, K + 1).
\end{aligned}
\tag{11.66}
$$

Corollary **11.2.4** (applied with $x \curvearrowright n/d$, $y \curvearrowright K + 1$ for $p \in (0, \infty)$ in the notation of (**11.34** in Corollary **11.2.4**) therefore demonstrates that for all $\boldsymbol{\theta} \in [\alpha, \beta]^\mathbf{d}$, $p \in (0, \infty)$ it holds that

$$
\begin{aligned}
& \mathbb{E}\bigl[ \min_{k \in \{1, 2, \dots, K\}} |\mathfrak{R}(\Theta_k) - \mathfrak{R}(\theta)|^p \bigr] \le \frac{2}{d} \frac{L^p (\beta - \alpha)^p \max\{1, (p/d)^{p/d}\}}{p^d \bigl( K + 1 + \min\{p/d - 1, 0\} \bigr)^{p/d}} \\
& \le \frac{L^p (\beta - \alpha)^p \max\{1, (p/d)^{p/d}\}}{K^{p/d}}.
\end{aligned}
\tag{11.67}
$$
