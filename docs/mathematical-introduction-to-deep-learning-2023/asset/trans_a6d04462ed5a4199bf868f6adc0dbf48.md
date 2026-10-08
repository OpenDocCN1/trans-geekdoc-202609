
此外，注意到 (13.38) 以及对于所有 $x_1, x_2, y \in \mathbb{R}$ 均成立的恒等式 $(x_1 - y)^2 - (x_2 - y)^2 = (x_1 - x_2)((x_1 - y) + (x_2 - y))$，这表明对于所有 $x, y \in E$ 和 $m \in \{1, 2, \ldots, M\}$，均成立：

$$
\begin{align*}
|\mathcal{Y}_{x,m} - \mathcal{Y}_{y,m}| &= |(X_{x,m} - Y_m)^2 - (X_{y,m} - Y_m)^2| \\
&\leq |X_{x,m} - X_{y,m}|(|X_{x,m} - Y_m| + |X_{y,m} - Y_m|) \\
&\leq 2b|X_{x,m} - X_{y,m}| \leq 2b\delta d(x, y).
\end{align*}
$$

由于对于所有 $x \in E$，$\mathcal{Y}_{x,m}$，$m \in \{1, 2, \ldots, M\}$，是相互独立的随机变量，结合 (13.42) 和推论 13.2.5（在推论 13.2.5 的记号下，分别取 $(\tilde{\mathcal{Y}}_{x,m})_{x \in E, m \in \{1, 2, \ldots, M\}}$ 和 $(\mathcal{Y}_{x,m})_{x \in E, m \in \{1, 2, \ldots, M\}}$，$L \lor 2b\breve{L}$，以及 $(Z_{z})_{z \in E} \lor (\Omega \ni \omega \mapsto \mathscr{R}(x, \omega) \in \mathbb{R})_{x \in E}$），由此可证明：

- (I) $\Omega \ni \omega \mapsto \sup_{x \in E}|\mathscr{R}(x, \omega) - \mathbf{R}(x)| \in [0, \infty]$ 是 $\mathcal{F}/\mathcal{B}([0, \infty])$-可测的；且
- (II) 对于所有 $p \in [2, \infty)$，$c \in (0, \infty)$，均成立：

$$
\left( \mathbb{E}\left[ \sup_{x \in E}|\mathscr{R}(x) - \mathbb{E}[\mathscr{R}(x)]|^p \right] \right)^{1/p} \leq \frac{2\sqrt{p-1}}{\sqrt{M}} \left( c^{(E,\delta)} \cdot \frac{cb^2 \sqrt{p-1}}{2L\sqrt{M}} \right)^{1/p} \left[ cb^2 + \sup_{x \in E} \max_{m \in \{1, \ldots, M\}} \left( \mathbb{E}\left[ |\mathcal{Y}_{x,m} - \mathbb{E}[\mathcal{Y}_{x,m}]|^p \right] \right)^{1/p} \right].
$$

注意到条目 (II)、(13.41)、(13.42) 和 (13.45) 表明，对于所有 $p \in [2, \infty)$，$c \in (0, \infty)$，均成立：

$$
\left( \mathbb{E}\left[ \sup_{x \in E}|\mathscr{R}(x) - \mathbf{R}(x)|^p \right] \right)^{1/p} \leq \frac{2\sqrt{p-1}}{\sqrt{M}} \left( c^{(E,\delta)} \cdot \frac{cb^2 \sqrt{p-1}}{2L\sqrt{M}} \right)^{1/p} \left[ cb^2 + b^2 \right]
$$

$$
= \left( c^{(E,\delta)} \cdot \frac{cb^2 \sqrt{p-1}}{2L\sqrt{M}} \right)^{1/p} \frac{\left[ 2(c+1)b^2 \sqrt{p-1} - 1 \right]}{\sqrt{M}}.
$$

结合条目 (I)，这证明了条目 (i) 和 (ii)。至此，引理 13.3.1 的证明结束。

### 命题 13.3.2.

设 $d \in \mathbb{N}$，$D \subseteq \mathbb{R}^d$，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为概率空间，设 $M \in \mathbb{N}$，设 $\overline{\mathbf{X}}_m = (X_m, Y_m) : \Omega \to (D \times \mathbb{R})$，$m \in \{1, 2, \ldots, M\}$，为独立同分布随机变量，设 $\alpha \in \mathbb{R}$，$\beta \in (\alpha, \infty)$，$\mathbf{d} \in \mathbb{N}$，设 $f = (f_\theta)_{\theta \in [\alpha, \beta]} : [\alpha, \beta] \to C(D, \mathbb{R})$，设 $L, b \in (0, \infty)$ 满足对于所有 $\theta, \vartheta \in [\alpha, \beta]^{\mathbf{d}}$，$m \in \{1, 2, \ldots, M\}$，$x \in D$ 有：

$$
|f_\theta(X_m) - Y_m| \leq b \quad \text{且} \quad |f_\theta(x) - f_\vartheta(x)| \leq L|\theta - \vartheta|_\infty,
$$

且设 $\mathbf{R} : [\alpha, \beta]^{\mathbf{d}} \to [0, \infty)$ 和 $\mathscr{R} : [\alpha, \beta]^{\mathbf{d}} \times \Omega \to [0, \infty)$ 满足对于所有 $\theta \in [\alpha, \beta]^{\mathbf{d}}$，$\omega \in \Omega$ 有：

$$
\mathbf{R}(\theta) = \mathbb{E}\left[ |f_\theta(X_1) - Y_1|^2 \right] \quad \text{且} \quad \mathscr{R}(\theta, \omega) = \frac{1}{M} \left[ \sum_{m=1}^{M} |f_\theta(X_m(\omega)) - Y_m(\omega)|^2 \right]
$$

（参见定义 3.3.4）。则

(i) $\Omega \ni \omega \mapsto \sup_{\theta \in [\alpha, \beta]^d} |\mathcal{R}(\theta, \omega) - \mathbf{R}(\theta)| \in [0, \infty]$ 是 $\mathcal{F}/\mathcal{B}([0, \infty])$-可测的；且

(ii) 对于所有 $p \in (0, \infty)$，均成立：

$$
\begin{align}
\mathbb{E}\left[\left(\sup_{\theta \in [\alpha, \beta]^d} |\mathcal{R}(\theta) - \mathbf{R}(\theta)|^p\right)^{1/p}\right] &\nonumber \\
\le \inf_{c, \varepsilon \in (0, \infty)} \left[ \frac{2(c+1)b^2 \max\{1, [2\sqrt{M} L (\beta - \alpha)(cb)^{-1}\varepsilon] \varepsilon \} \max\{1, p, \frac{A}{\varepsilon}\}}{\sqrt{M}} \right]^{1/p} \tag{13.51} \\
&\le \inf_{c \in (0, \infty)} \left[ \frac{2(c+1)b^2 \sqrt{e} \max\{1, p, \mathrm{d}\ln(4M L^2 (\beta - \alpha)^2 (cb)^{-2})\}}{\sqrt{M}} \right].
\end{align}
$$

#### 命题 13.3.2 的证明。

在整个证明过程中，令 $(\kappa_c)_{c \in (0, \infty)} \subseteq (0, \infty)$ 满足对于所有 $c \in (0, \infty)$ 有：

$$
\kappa_c = \frac{2\sqrt{M} L (\beta - \alpha)}{cb}, \quad (13.52)
$$

令 $\mathcal{X}_{\theta,m}\colon \Omega \to \mathbb{R}$，$m \in \{1, 2, \dots, M\}$，$\theta \in [\alpha, \beta]^d$，满足对于所有 $\theta \in [\alpha, \beta]^d$，$m \in \{1, 2, \dots, M\}$ 有：

$$
\mathcal{X}_{\theta,m} = f_\theta(X_m), \quad (13.53)
$$

且令 $\delta\colon [\alpha, \beta]^{\mathrm{d}} \times [\alpha, \beta]^{\mathrm{d}} \to [0, \infty)$ 满足对于所有 $\theta, \vartheta \in [\alpha, \beta]^{\mathrm{d}}$ 有：

$$
\delta(\theta, \vartheta) = \lVert \theta - \vartheta \rVert_\infty. \quad (13.54)
$$

首先，注意到假设对于所有 $\theta \in [\alpha, \beta]^d$，$m \in \{1, 2, \dots, M\}$ 均有 $|f_\theta(X_m) - Y_m| \le b$，这意味着对于所有 $\theta \in [\alpha, \beta]^d$，$m \in \{1, 2, \dots, M\}$ 有：

$$
|\mathcal{X}_{\theta,m} - Y_m| = |f_\theta(X_m) - Y_m| \le b. \quad (13.55)
$$

此外，注意到假设对于所有 $\theta, \vartheta \in [\alpha, \beta]^d$，$x \in D$ 均有 $|f_\theta(x) - f_\vartheta(x)| \le L \lVert \theta - \vartheta \rVert_\infty$，这确保了对于所有 $\theta, \vartheta \in [\alpha, \beta]^d$，$m \in \{1, 2, \dots, M\}$ 有：

$$
\begin{align}
|\mathcal{X}_{\theta,m} - \mathcal{X}_{\vartheta,m}| = |f_\theta(X_m) - f_\vartheta(X_m)| & \le \sup_{x \in D} |f_\theta(x) - f_\vartheta(x)| \le L \lVert \theta - \vartheta \rVert_\infty = L \delta(\theta, \vartheta). \tag{13.56}
\end{align}
$$

由于对于所有 $\theta \in [\alpha, \beta]^d$，$(\mathcal{X}_{\theta,m}, Y_m)$，$m \in \{1, 2, \dots, M\}$，是独立同分布随机变量，结合 (13.55) 和引理 13.3.1（在引理 13.3.1 的记号下，将 $p$ 替换为 $q$，$C$ 替换为 $C$，$(E, \delta)$ 替换为 $(\alpha, \beta)^d, \delta)$，$(X_{x,m})_{x \in E, m \in \{1, \dots, M\}}$ 替换为 $(\mathcal{X}_{\theta,m})_{\theta \in [\alpha, \beta]^d, m \in \{1, \dots, M\}}$，其中 $p \in [2, \infty)$，$C \in (0, \infty)$），因此确保了对于所有 $p \in [2, \infty)$，$c \in (0, \infty)$，$\Omega \ni \omega \mapsto \sup_{\theta \in [\alpha, \beta]^d} |\mathcal{R}(\theta, \omega) - \mathbf{R}(\theta)| \in [0, \infty]$ 是 $\mathcal{F}/\mathcal{B}([0, \infty])$-可测的，且

$$
\mathbb{E}\left[\left(\sup_{\theta \in [\alpha, \beta]^d} |\mathcal{R}(\theta) - \mathbf{R}(\theta)|^p\right)^{1/p}\right] \le \left(C^{([\alpha, \beta]^d, \delta), \frac{cb\sqrt{p-1}}{2L\sqrt{M}}} \right)^{1/p} \left[\frac{2(c+1)b^2\sqrt{p-1}}{\sqrt{M}}\right] \tag{13.57}
$$

（参见定义 4.3.2）。这就建立了条目 (i)。注意，命题 12.2.24（在命题 12.2.24 的记号下，将 $d$ 替换为 $\bm{d}$，$a$ 替换为 $\alpha$，$b$ 替换为 $\beta$，$r$ 替换为 $r$，其中 $r \in (0, \infty)$）表明，对于所有 $r \in (0, \infty)$，均成立：

$$
\begin{align}
\mathcal{C}^{([\alpha, \beta], \delta), r} & \leq \mathbb{I}_{[0, r]}\big(\frac{\beta - \alpha}{2}\big) + \big(\frac{\beta - \alpha}{r}\big)^{\bm{d}} \mathbb{I}_{(r, \infty)}\big(\frac{\beta - \alpha}{2}\big) \nonumber \\
& \leq \max \big\{ \mathbb{I}, \big(\frac{\beta - \alpha}{r}\big)^{\bm{d}} \big\} \big( \mathbb{I}_{[0, r]}\big(\frac{\beta - \alpha}{2}\big) + \mathbb{I}_{(r, \infty)}\big(\frac{\beta - \alpha}{2}\big) \big\} \nonumber \\
& = \max \big\{ \mathbb{I}, \big(\frac{\beta - \alpha}{r}\big)^{\bm{d}} \big\}.
\end{align}
$$

因此，对于所有 $c \in (0, \infty)$，$p \in [2, \infty)$，我们得到：

$$
\begin{align}
\bigg( \mathcal{C}^{([\alpha, \beta], \bm{d}, c), \frac{\bm{c}_p \vee \bm{1}}{2L \vee M}} \bigg)^{1/p} & \leq \max \bigg\{ \mathbb{I}, \big(\frac{2(\beta - \alpha)L \vee \sqrt{M}}{c\beta \vee \mathbb{1}}\big)^{\bm{d}/p} \bigg\} \nonumber \\
& \leq \max \bigg\{ \mathbb{I}, \big(\frac{2(\beta - \alpha)L \vee \sqrt{M}}{c\beta} \big)^{\bm{d}/p} \bigg\} = \max \big\{ \mathbb{I}, (\kappa_c)^{\bm{d}/p} \big\}.
\end{align}
$$

结合上述结果、(13.57) 和 Jensen 不等式，表明对于所有 $c, \varepsilon, p \in (0, \infty)$，均成立：

$$
\begin{align}
& \big( \mathbb{E}\big[ \sup_{\bm{\theta} \in [\alpha, \beta]^{\bm{d}}} | \mathfrak{R}(\bm{\theta}) - \bm{R}(\bm{\theta}) |^{p} \big] \big)^{1/p} \nonumber \\
& \leq \big( \mathbb{E}\big[ \sup_{\bm{\theta} \in [\alpha, \beta]^{\bm{d}}} | \mathfrak{R}(\bm{\theta}) - \bm{R}(\bm{\theta}) |^{\max \{2p, \bm{d}/\varepsilon\}} \big] \big)^{\frac{1}{\max \{2p, \bm{d}/\varepsilon\}}} \nonumber \\
& \leq \max \bigg\{ \mathbb{I}, (\kappa_c)^{\frac{\bm{d}}{\max \{2p, \bm{d}/\varepsilon\}}} \bigg\} \frac{2(c+1)b^{2} \sqrt{\max \{2, p, \frac{\bm{d}}{\varepsilon}\} - 1}}{\sqrt{M}} \nonumber \\
& = \max \big\{ \mathbb{I}, (\kappa_c)^{\min \{4/2, \bm{d}/p, \bm{d}/\varepsilon\}} \big\} \frac{2(c+1)b^{2} \sqrt{\max \{\mathbb{I}, p - 1, \bm{d}/\varepsilon - 1\}}}{\sqrt{M}} \nonumber \\
& \leq \frac{2(c+1)b^{2} \max \{\mathbb{I}, (\kappa_c)^{\varepsilon}\} \sqrt{\max \{\mathbb{I}, p, \bm{d}/\varepsilon\}}}{\sqrt{M}}.
\end{align}
$$

此外，注意到对于所有 $a \in (1, \infty)$，$a^{1/(2 \ln(a))} = e^{\ln(a)/(2 \ln(a))} = e^{1/2} = \sqrt{e} \geq 1$ 这一事实证明了：对于所有 $c, p \in (0, \infty)$ 且 $\kappa_c > 1$，均成立：

$$
\begin{align}
& \inf_{\varepsilon \in (0, \infty)} \bigg[ \frac{2(c+1)b^{2} \max \{\mathbb{I}, (\kappa_c)^{\varepsilon}\} \sqrt{\max \{\mathbb{I}, p, \frac{\bm{d}}{\varepsilon}\}}}{\sqrt{M}} \bigg] \nonumber \\
& \leq \frac{2(c+1)b^{2} \max \{ \mathbb{I}, (\kappa_c)^{1/(2 \ln(\kappa_c))} \} \sqrt{\max \{ \mathbb{I}, p, 2 \bm{d} \ln(\kappa_c) \}}}{\sqrt{M}} \nonumber \\
& = \frac{2(c+1)b^{2} \sqrt{e} \max \{ \mathbb{I}, p, \bm{d} \ln([\kappa_c]^2) \}}{\sqrt{M}}.
\end{align}
$$

