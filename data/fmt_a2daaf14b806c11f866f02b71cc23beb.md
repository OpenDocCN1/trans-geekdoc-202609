
设 $d, \mathcal{M} \in \mathbb{N}$，$R, L, \mathcal{R}, \varepsilon \in(0, \infty)$，设 $D \subseteq \mathbb{R}^{d}$ 为紧致集，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为概率空间，设 $X_{m}: \Omega \to D$，$m \in \{1, 2, \ldots, \mathcal{M}\}$，以及 $Y_{m}: \Omega \to \mathbb{R}$，$m \in \{1, 2, \ldots, \mathcal{M}\}$，为函数，假设 $(X_{m}, Y_{m})$，$m \in \{1, 2, \ldots, \mathcal{M}\}$，是独立同分布随机变量，设 $H = (H_{\theta})_{\theta \in [-R, R]^{d}}: [-R, R]^{d} \to C(D, \mathbb{R})$ 满足对于所有 $\theta, \vartheta \in [-R, R]^{d}$，$x \in D$ 有 $|H_{\theta}(x) - H_{\vartheta}(x)| \leq L \| \theta - \vartheta \|_{\infty}$，假设对于所有 $\theta \in [-R, R]^{d}$，$m \in \{1, 2, \ldots, \mathcal{M}\}$ 有 $|H_{\theta}(X_{m}) - Y_{m}| \leq \mathcal{R}$ 且 $\mathbb{E} | Y_{m} |^{2} < \infty$，设 $\mathcal{E}: C(D, \mathbb{R}) \to [0, \infty)$ 满足对于所有 $f \in C(D, \mathbb{R})$ 有 $\mathcal{E}(f) = \mathbb{E} | f(X_{1}) - Y_{1} |^{2}$，且设 $\mathfrak{E}: [-R, R]^{d} \times \Omega \to [0, \infty)$ 满足对于所有 $\theta \in [-R, R]^{d}$，$\omega \in \Omega$ 有：

$
\mathfrak{E}(\theta, \omega) = \frac{1}{\mathcal{M}} \left[ \sum_{m=1}^{\mathcal{M}} | H_{\theta}(X_{m}(\omega)) - Y_{m}(\omega) |^{2} \right].
$

（参见定义 3.9.4）。则 $\Omega \ni \omega \mapsto \sup_{\theta \in [-R, R]^{d}} | \mathfrak{E}(\theta, \omega) - \mathcal{E}(H_{\theta}) | \in [0, \infty]$ 是 $\mathcal{F}/\mathcal{B}([0, \infty])$-可测的，且

$
\mathbb{P}( \sup_{\theta \in [-R, R]^{d}} | \mathfrak{E}(\theta) - \mathcal{E}(H_{\theta}) | \ge \varepsilon ) \le 2 \max \left\{ 1, \left[ \frac{16 L \mathcal{R}^{2}}{\varepsilon} \right]^{d} \right\} \exp \left( \frac{-\varepsilon^{2} \mathcal{M}}{2 \mathcal{R}^{4}} \right).
$

### 命题 12.3.9 的证明

在整个证明过程中，设 $B \subseteq \mathbb{R}^{d}$ 满足 $B = [-R, R]^{d} = \{ \theta \in \mathbb{R}^{d}: \| \theta \|_{\infty} \leq R \}$，且设 $\delta: B \times B \to [0, \infty)$ 满足对于所有 $\theta, \vartheta \in B$ 有：

$
\delta(\theta, \vartheta) = \| \theta - \vartheta \|_{\infty}.
$

注意，$(X_{m}, Y_{m})$，$m \in \{1, 2, \ldots, \mathcal{M}\}$，是独立同分布随机变量的假设，以及对于所有 $\theta \in [-R, R]^{d}$，$H_{\theta}$ 是连续的假设，意味着对于所有 $\theta \in B$，$(H_{\theta}(X_{m}), Y_{m})$，$m \in \{1, 2, \ldots, \mathcal{M}\}$，是独立同分布随机变量。将此与对于所有 $\theta, \vartheta \in B$，$x \in D$ 都有 $|H_{\theta}(x) - H_{\vartheta}(x)| \leq L \| \theta - \vartheta \|_{\infty}$ 的假设，以及对于所有 $\theta \in B$，$m \in \{1, 2, \ldots, \mathcal{M}\}$ 都有 $|H_{\theta}(X_{m}) - Y_{m}| \leq \mathcal{R}$ 的假设，结合引理 12.3.8（在引理 12.3.8 的记号中应用，其中 $(E, \delta) \sim (B, \delta)$，$M \sim \mathcal{M}$，$\varepsilon \sim \varepsilon$，$L \sim L$，$D \sim \mathcal{R}$，$(\Omega, \mathcal{F}, \mathbb{P}) \sim (\Omega, \mathcal{F}, \mathbb{P})$，$(X_{x, m})_{x \in E, m \in \{1, 2, \ldots, \mathcal{M}\}} \sim (H_{\theta}(X_{m}))_{\theta \in B, m \in \{1, 2, \ldots, \mathcal{M}\}}$，$(Y_{m})_{m \in \{1, 2, \ldots, \mathcal{M}\}} \sim (Y_{m})_{m \in \{1, 2, \ldots, \mathcal{M}\}}$，$(\mathfrak{E}_{x})_{x \in E} \sim (\mathcal{E}(H_{\theta}))_{\theta \in B}$）确立了 $\Omega \ni \omega \mapsto \sup_{\theta \in B} | \mathfrak{E}(\theta, \omega) - \mathcal{E}(H_{\theta}) | \in [0, \infty]$ 是 $\mathcal{F}/\mathcal{B}([0, \infty])$-可测的，且

$
\mathbb{P}( \sup_{\theta \in B} | \mathfrak{E}(\theta) - \mathcal{E}(H_{\theta}) | \ge \varepsilon ) \le 2 \mathcal{C}^{(B, \delta), \frac{16 L \mathcal{R}^{2}}{\varepsilon}} \exp \left( \frac{-\varepsilon^{2} \mathcal{M}}{2 \mathcal{R}^{4}} \right).
$

（参见定义 4.3.2）。此外，请注意，命题 12.2.24（在命题 12.2.23 的符号意义下，取 $d \hookrightarrow \mathfrak{d}$，$a \hookrightarrow -R$，$b \hookrightarrow R$，$r \hookrightarrow \frac{\varepsilon}{8 L \mathcal{R}}$，$\delta \hookrightarrow \delta$ 时）证明了：

$$\mathfrak{C}^{(B, \delta), \frac{\varepsilon}{8 L \mathcal{R}}} \leq \max \left\{1,\left(\frac{16 L R \mathcal{R}}{\varepsilon}\right)^{\mathfrak{d}}\right\} .$$

这与 (12.174) 共同证明了 (12.172)。命题 12.3.9 的证明至此完成。$\square$

### 推论 12.3.10

设 $\mathfrak{d}, M, L \in \mathbb{N}$，$u \in \mathbb{R}$，$v \in (u, \infty)$，$R \in [1, \infty)$，$\varepsilon, b \in (0, \infty)$，$l=(l_{0}, l_{1}, \ldots, l_{L}) \in \mathbb{N}^{L+1}$ 满足 $l_{L}=1$ 且 $\sum_{k=1}^{L} l_{k}(l_{k-1}+1) \leq \mathfrak{d}$。设 $D \subset [-b, b]^{0}$ 是一个紧集，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 是一个概率空间。设函数 $X_{m}: \Omega \rightarrow D$，$m \in\{1,2,\ldots, M\}$，以及 $Y_{m}: \Omega \rightarrow [u, v]$，$m \in\{1,2,\ldots, M\}$ 成立。假设 $(X_{m}, Y_{m})$，$m \in\{1,2,\ldots, M\}$，是独立同分布的随机变量。设 $\mathcal{E}: C(D, \mathbb{R}) \rightarrow [0, \infty)$ 满足对于所有 $f \in C(D, \mathbb{R})$，有 $\mathcal{E}(f)=\mathbb{E}[f(X_{1})-Y_{1}]^{2}$。设 $\mathfrak{C}:[-R, R]^{\mathfrak{d}} \times \Omega \rightarrow [0, \infty)$ 满足对于所有 $\theta \in [-R, R]^{\mathfrak{d}}$ 和 $\omega \in \Omega$，有

$$\mathfrak{C}(\theta, \omega)=\frac{1}{M}\left[\sum_{m=1}^{M}\left|\mathcal{K}_{u, v}^{\theta, l}\left(X_{m}(\omega)\right)-Y_{m}(\omega)\right|^{2}\right]$$

（参见定义 4.4.1）。那么

- (i) 成立 $\Omega \ni \omega \mapsto \sup _{\theta \in[-R, R]^{\mathfrak{d}}} \left|\mathfrak{C}(\theta, \omega)-\mathcal{E}\left(\mathcal{K}_{u, v}^{\theta, l} |D\right)\right| \in [0, \infty)$ 是 $\mathcal{F}/\mathcal{B}([0, \infty])$-可测的，并且

- (ii) 成立

$$\mathbb{P}\left(\sup _{\theta \in[-R, R]^{\mathfrak{d}}} \left|\mathfrak{C}(\theta)-\mathcal{E}\left(\mathcal{K}_{u, v}^{\theta, l} |D\right)\right| \geq \varepsilon\right) \leq 2 \max \left\{1,\left[\frac{16 L \max \left\{1, b\right\}\left(\|l\|_{\infty}+1\right)^{L} R^{L}\left(v-u\right)}{\varepsilon}\right]\right\} \exp \left(\frac{-\varepsilon^{2} M}{2(v-u)^{4}}\right) .$$

#### 推论 12.3.10 的证明

在整个证明过程中，设 $\mathfrak{L} \in(0, \infty)$ 满足

$$\mathfrak{L}=L \max \left\{1, b\right\}\left(\|l\|_{\infty}+1\right)^{L} R^{L-1} .$$

注意到，将推论 11.3.7（在推论 11.3.7 的符号意义下，取 $a \hookrightarrow -b$，$b \hookrightarrow b$，$u \hookrightarrow u$，$v \hookrightarrow v$，$\mathfrak{d} \hookrightarrow \mathfrak{d}$，$L \hookrightarrow L$，$l \hookrightarrow l$ 时）与假设 $D \subset [-b, b]^{0}$ 结合，表明对于所有 $\theta, \vartheta \in [-R, R]^{\mathfrak{d}}$，有

$$\begin{aligned}\sup _{x \in D}\left|\mathcal{K}_{u, v}^{\theta, l}(x)-\mathcal{K}_{u, v}^{\vartheta, l}(x)\right| & \\

\leq \sup _{x \in [-b, b]^{0}}\left|\mathcal{K}_{u, v}^{\theta, l}(x)-\mathcal{K}_{u, v}^{\vartheta, l}(x)\right| & \\

\leq L \max \left\{1, b\right\}\left(\|l\|_{\infty}+1\right)^{L}\left(\max \left\{1,\|\theta\|_{\infty},\|\vartheta\|_{\infty}\right\}\right)^{L-1}\|\theta-\vartheta\|_{\infty} & \\

\leq L \max \left\{1, b\right\}\left(\|l\|_{\infty}+1\right)^{L} R^{L-1}\|\theta-\vartheta\|_{\infty}=\mathfrak{L}\|\theta-\vartheta\|_{\infty} .\end{aligned}$$

此外，注意到对于所有 $\theta \in \mathbb{R}^3$ 和 $x \in \mathbb{R}^{\ell_0}$，成立 $\mathcal{N}^{\theta, \ell}_{u, v}(x) \in [u, v]$，以及假设对于所有 $m \in \{1, 2, \dots, M\}$ 和 $\omega \in \Omega$，成立 $Y_m(\omega) \in [u, v]$。这表明对于所有 $\theta \in [-R, R]^3$ 和 $m \in \{1, 2, \dots, M\}$，成立

$$\left|\mathcal{N}_{u, v}^{\theta, \ell}(X_m) - Y_m\right| \leq v - u. \quad (12.180)$$

结合此结果与 (12.179) 以及命题 12.3.9（在命题 12.3.9 的符号意义下，取 $d \hookrightarrow \ell_0$，$\mathfrak{d} \hookrightarrow \mathfrak{d}$，$M \hookrightarrow M$，$R \hookrightarrow R$，$L \hookrightarrow \mathfrak{L}$，$\mathcal{R} \hookrightarrow v-u$，$\mathfrak{e} \hookrightarrow \varepsilon$，$D \hookrightarrow D$，$(\Omega, \mathcal{F}, \mathbb{P}) \hookrightarrow (\Omega, \mathcal{F}, \mathbb{P})$，$(X_m)_{m \in \{1, 2, \dots, M\}} \hookrightarrow (X_m)_{m \in \{1, 2, \dots, M\}}$，$(Y_m)_{m \in \{1, 2, \dots, M\}} \hookrightarrow ((\Omega \ni \omega \mapsto Y_m(\omega) \in \mathbb{R}))_{m \in \{1, 2, \dots, M\}}$，$\mathcal{H} \hookrightarrow ([-R, R]^3 \ni \theta \mapsto \mathcal{N}_{u, v}^{\theta, \ell}|_D \in C(D, \mathbb{R}))$，$\mathcal{E} \hookrightarrow \mathcal{E}$，$\mathfrak{E} \hookrightarrow \mathfrak{E}$ 时），可以确立 $\Omega \ni \omega \mapsto \sup_{\theta \in [-R, R]^3} |\mathfrak{E}(\theta, \omega) - \mathcal{E}(\mathcal{N}_{u, v}^{\theta, \ell}|_D)| \in [0, \infty]$ 是 $\mathcal{F}/\mathcal{B}([0, \infty])$-可测的，并且
