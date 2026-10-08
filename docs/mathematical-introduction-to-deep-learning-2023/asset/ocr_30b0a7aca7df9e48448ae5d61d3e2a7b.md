Moreover, note that (13.38) and the fact that for all $x_1, x_2, y \in \mathbb{R}$ it holds that $(x_1 - y)^2 - (x_2 - y)^2 = (x_1 - x_2)((x_1 - y) + (x_2 - y))$ show that for all $x, y \in E$, $m \in \{1, 2, \ldots, M\}$ it holds that

$\begin{align*} |\mathcal{Y}_{x,m} - \mathcal{Y}_{y,m}| &= |(X_{x,m} - Y_m)^2 - (X_{y,m} - Y_m)^2| \\ &\leq |X_{x,m} - X_{y,m}|(|X_{x,m} - Y_m| + |X_{y,m} - Y_m|) \\ &\leq 2b|X_{x,m} - X_{y,m}| \leq 2b\delta d(x, y). \end{align*}$

The fact that for all $x \in E$ it holds that $\mathcal{Y}_{x,m}$, $m \in \{1, 2, \ldots, M\}$, are independent random variables, (13.42), and Corollary 13.2.5 (applied with $(\tilde{\mathcal{Y}}_{x,m})_{x \in E, m \in \{1, 2, \ldots, M\}}$ and $(\mathcal{Y}_{x,m})_{x \in E, m \in \{1, 2, \ldots, M\}}$, $L \lor 2b\breve{L}$, $(Z_{z})_{z \in E} \lor (\Omega \ni \omega \mapsto \mathscr{R}(x, \omega) \in \mathbb{R})_{x \in E}$ in the notation of Corollary 13.2.5) hence establish that

+   (I) it holds that $\Omega \ni \omega \mapsto \sup_{x \in E}|\mathscr{R}(x, \omega) - \mathbf{R}(x)| \in [0, \infty]$ is $\mathcal{F}/\mathcal{B}([0, \infty])$-measurable and

+   (II) it holds for all $p \in [2, \infty)$, $c \in (0, \infty)$ that

$\left( \mathbb{E}\left[ \sup_{x \in E}|\mathscr{R}(x) - \mathbb{E}[\mathscr{R}(x)]|^p \right] \right)^{1/p} \leq \frac{2\sqrt{p-1}}{\sqrt{M}} \left( c^{(E,\delta)} \cdot \frac{cb^2 \sqrt{p-1}}{2L\sqrt{M}} \right)^{1/p} \left[ cb^2 + \sup_{x \in E} \max_{m \in \{1, \ldots, M\}} \left( \mathbb{E}\left[ |\mathcal{Y}_{x,m} - \mathbb{E}[\mathcal{Y}_{x,m}]|^p \right] \right)^{1/p} \right] .

Observe that item (II), (13.41), (13.42), and (13.45) demonstrate that for all $p \in [2, \infty)$, $c \in (0, \infty)$ it holds that

$\left( \mathbb{E}\left[ \sup_{x \in E}|\mathscr{R}(x) - \mathbf{R}(x)|^p \right] \right)^{1/p} \leq \frac{2\sqrt{p-1}}{\sqrt{M}} \left( c^{(E,\delta)} \cdot \frac{cb^2 \sqrt{p-1}}{2L\sqrt{M}} \right)^{1/p} \left[ cb^2 + b^2 \right]$

$= \left( c^{(E,\delta)} \cdot \frac{cb^2 \sqrt{p-1}}{2L\sqrt{M}} \right)^{1/p} \frac{\left[ 2(c+1)b^2 \sqrt{p-1} - 1 \right]}{\sqrt{M}} .

This and item (I) prove items (i) and (ii). The proof of Lemma 13.3.1 is thus complete.

**Proposition 13.3.2.** Let $d \in \mathbb{N}$, $D \subseteq \mathbb{R}^d$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $M \in \mathbb{N}$, let $\overline{\mathbf{X}}_m = (X_m, Y_m) : \Omega \to (D \times \mathbb{R})$, $m \in \{1, 2, \ldots, M\}$, be i.i.d. random variables, let $\alpha \in \mathbb{R}$, $\beta \in (\alpha, \infty)$, $\mathbf{d} \in \mathbb{N}$, let $f = (f_\theta)_{\theta \in [\alpha, \beta]} : [\alpha, \beta] \to C(D, \mathbb{R})$, let $L, b \in (0, \infty)$ satisfy for all $\theta, \vartheta \in [\alpha, \beta]^{\mathbf{d}}$, $m \in \{1, 2, \ldots, M\}$, $x \in D$ that

$|f_\theta(X_m) - Y_m| \leq b \quad \text{ and } \quad |f_\theta(x) - f_\vartheta(x)| \leq L|\theta - \vartheta|_\infty,$

and let $\mathbf{R} : [\alpha, \beta]^{\mathbf{d}} \to [0, \infty)$ and $\mathscr{R} : [\alpha, \beta]^{\mathbf{d}} \times \Omega \to [0, \infty)$ satisfy for all $\theta \in [\alpha, \beta]^{\mathbf{d}}$, $\omega \in \Omega$ that

$\mathbf{R}(\theta) = \mathbb{E}\left[ |f_\theta(X_1) - Y_1|^2 \right] \quad \text{ and } \quad \mathscr{R}(\theta, \omega) = \frac{1}{M} \left[ \sum_{m=1}^{M} |f_\theta(X_m(\omega)) - Y_m(\omega)|^2 \right]$

(cf. Definition 3.3.4). Then