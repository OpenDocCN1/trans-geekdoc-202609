

因此，我们得出

$\lim_{n\to\infty} \inf \left[\prod_{k=1}^{n} \left[1 - \gamma_k\alpha \right]\right] \geq \left[\prod_{k=1}^{n-1} \left[1 - \gamma_k\alpha \right]\right] \exp \left( -2\alpha \sum_{k=1}^{\infty} \gamma_k \right) > 0. \hspace{2em} (7.82)$

这确立了第 (ii) 项。请注意，第 (i) 项和第 (ii) 项以及假设 $\xi \neq \varnothing$ 意味着

$\begin{split}
\lim_{n\to\infty} \inf \| \Theta_n - \vartheta \|_2 &= \lim_{n\to\infty} \inf \left\|\left[\prod_{k=1}^{n} \left(1 - \gamma_k\alpha \right) \right] \left( \xi - \vartheta \right) \right\|_2 \\
&= \lim_{n\to\infty} \inf \left( \left|\prod_{k=1}^{n} \left(1 - \gamma_k\alpha \right) \right| \| \xi - \vartheta \|_2 \right) \\
&= \| \xi - \vartheta \|_2 \left( \lim_{n\to\infty} \inf \left[\prod_{k=1}^{n} \left[1 - \gamma_k\alpha \right]\right] \right) > 0.
\end{split} \hspace{2em} (7.83)$

这证明了第 (iii) 项。至此，引理 7.2.13 的证明完成。$\square$

## 7.2.3 二次目标函数的 SGD 收敛速率

下面的例 7.2.14 特别提供针对 SGD 优化方法在特定随机优化问题情形下的误差分析（参见下文公式 (7.84)）。SGD 优化方法的更一般误差分析，例如可在 [221, 229] 及其参考文献中找到（参见下文第 7.2.3 节）。

**例 7.2.14 (SGD 过程的示例)。** 设 $\mathfrak{o} \in \mathbb{N}$，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为概率空间，设 $X_n \colon \Omega \to \mathbb{R}^\mathfrak{o}$，$n \in \mathbb{N}$，为独立同分布 (i.i.d.) 随机变量，且满足 $\mathbb{E}[\|X_1\|_2^2] < \infty$。设 $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^\mathfrak{o} \times \mathbb{R}^\mathfrak{o}} \colon \mathbb{R}^\mathfrak{o} \times \mathbb{R}^\mathfrak{o} \to \mathbb{R}$ 和 $\mathscr{L} \colon \mathbb{R}^\mathfrak{o} \to \mathbb{R}$ 满足对于所有 $\theta, x \in \mathbb{R}^\mathfrak{o}$ 有

$\ell(\theta, x) = \frac{1}{2} \| \theta - x \|_2^2 \qquad \text{且} \qquad \mathscr{L}(\theta) = \mathbb{E}\left[ \ell(\theta, X_1) \right], \hspace{2em} (7.84)$

并设 $\Theta \colon \mathbb{N}_0 \times \Omega \to \mathbb{R}^\mathfrak{o}$ 为满足对于所有 $n \in \mathbb{N}$ 有 $\Theta_0 = 0$ 的随机过程，且

$\Theta_n = \Theta_{n-1} - \frac{1}{n} \left\langle \nabla_\theta \ell \right\rangle \left( \Theta_{n-1}, X_n \right) \hspace{2em} (7.85)$

（参见定义 3.3.4）。则

- (i) 成立 $\{\theta \in \mathbb{R}^\mathfrak{o} \colon \mathscr{L}(\theta) = \inf_{w \in \mathbb{R}^\mathfrak{o}} \mathscr{L}(w) \} = \{\mathbb{E}[X_1]\}$，
- (ii) 对于所有 $n \in \mathbb{N}$，成立 $\Theta_n = \frac{1}{n}(X_1 + X_2 + \ldots + X_n)$，
- (iii) 对于所有 $n \in \mathbb{N}$，成立 (7.86)，
- (iv) 对于所有 $n \in \mathbb{N}$，成立 (7.87)。

**例 7.2.14 的证明。** 注意到假设 $\mathbb{E}[\|X_1\|_2^2] < \infty$ 和引理 7.2.3 表明对于所有 $\theta \in \mathbb{R}^\mathfrak{o}$，成立

(7.88)

这确立了第 (i) 项。请注意，引理 5.6.4 确保对于所有 $\theta, x \in \mathbb{R}^\mathfrak{o}$，成立

(7.89)

结合此与 (7.85) 可知，对于所有 $n \in \mathbb{N}$，成立

(7.90)

接下来我们声称，对于所有 $n \in \mathbb{N}$，成立

(7.91)

我们现在通过对 $n \in \mathbb{N}$ 进行归纳法证明 (7.91)。对于基础情况 $n=1$，注意 (7.90) 意味着

(7.92)

这确立了基础情况 $n=1$ 时的 (7.91)。对于归纳步骤，注意 (7.90) 表明对于所有 $n \in \{2, 3, 4, \ldots\}$，若 $\Theta_{n-1} = \frac{1}{(n-1)}(X_1 + X_2 + \ldots + X_{n-1})$，则成立

(7.93)

因此归纳法意味着 (7.91) 成立。此外，注意 (7.91) 证明了第 (ii) 项。请观察，引理 7.2.6 的第 (ii) 项以及事实 $(X_n)_{n \in \mathbb{N}}$ 是满足

$\mathbb{E}[\|X_1\|_2^2] < \infty$ 的独立同分布随机变量，表明对于所有 $n \in \mathbb{N}$，成立

(7.94)

这确立了第 (iii) 项。因此，余下工作为证明第 (iv) 项。为此注意，(7.88) 和 (7.94) 确保对于所有 $n \in \mathbb{N}$，成立

(7.95)

这证明了第 (iv) 项。例 7.2.14 的证明至此完成。$\square$

下一个结果，即下文的定理 7.2.15，根据学习率序列的渐近行为，指定了 **SGD** 优化方法的强收敛和弱收敛速率。定理 7.2.15 的陈述和证明可在 Jentzen 等人 [229, 定理 1.1] 中找到。

**定理 7.2.15 (依赖学习率的收敛速率)。** 设 $\mathfrak{o} \in \mathbb{N}$，$\alpha, \gamma, \nu \in (0, \infty)$，$\xi \in \mathbb{R}^\mathfrak{o}$，设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为概率空间，设 $X_n: \Omega \to \mathbb{R}^\mathfrak{o}$，$n \in \mathbb{N}$，为独立同分布随机变量，且满足 $\mathbb{E}[\|X_1\|_2^2] < \infty$ 和 $\mathbb{P}(X_1 = \mathbb{E}[X_1]) < 1$。设 $(r_{\varepsilon,i})_{(\varepsilon,i) \in (0, \infty) \times \{0,1\}} \subseteq \mathbb{R}$ 满足对于所有 $\varepsilon \in (0, \infty)$，$i \in \{0, 1\}$ 有

$r_{\varepsilon,i} = \begin{cases} \nu/2 & : \nu < 1 \\ \min\{1/2, \gamma\alpha + (-1)^i \varepsilon\} & : \nu = 1 \\ 0 & : \nu > 1, \end{cases}$

设 $\ell = (\ell(\theta, x))_{(\theta,x) \in \mathbb{R}^\mathfrak{o} \times \mathbb{R}^\mathfrak{o}}: \mathbb{R}^\mathfrak{o} \times \mathbb{R}^\mathfrak{o} \to \mathbb{R}$ 和 $\mathscr{L}: \mathbb{R}^\mathfrak{o} \to \mathbb{R}$ 为满足对于所有 $\theta, x \in \mathbb{R}^\mathfrak{o}$ 有

$\ell(\theta, x) = (\alpha/2)\|\theta - x\|_2^2 \quad \text{且} \quad \mathscr{L}(\theta) = \mathbb{E}[\ell(\theta, X_1)],$

的函数，并设 $\Theta: \mathbb{N}_0 \times \Omega \to \mathbb{R}^\mathfrak{o}$ 为满足对于所有 $n \in \mathbb{N}$ 有

$\Theta_0 = \xi \quad \quad \text{且} \quad \quad \Theta_n = \Theta_{n-1} - \frac{\gamma}{n^\nu} (\nabla_{\vartheta} \mathscr{L}) (\Theta_{n-1}, X_n). \tag{7.98}$

*的随机过程。则*

- (i) *存在唯一的* $\vartheta \in \mathbb{R}^\mathfrak{o}$ *满足* $\{\theta \in \mathbb{R}^\mathfrak{o}: \mathscr{L}(\theta) = \inf_{w \in \mathbb{R}^\mathfrak{o}} \mathscr{L}(w)\} = \{\vartheta\}$，
- (ii) *对于每个* $\varepsilon \in (0, \infty)$ *，存在* $c_0, c_1 \in (0, \infty)$ *使得对于所有* $n \in \mathbb{N}$ *，成立*

$c_0 n^{-r_{\varepsilon,0}} \le \big( \mathbb{E} \big[ \| \Theta_n - \vartheta \|_2^2 \big] \big)^{1/2} \le c_1 n^{-r_{\varepsilon,1}}, \tag{7.99}$

*且*
- (iii) *对于每个* $\varepsilon \in (0, \infty)$ *，存在* $e_0, e_1 \in (0, \infty)$ *使得对于所有* $n \in \mathbb{N}$ *，成立*

$e_0 n^{-2r_{\varepsilon,0}} \le \mathbb{E} [ \mathscr{L} (\Theta_n) ] - \mathscr{L} (\vartheta) \le e_1 n^{-2r_{\varepsilon,1}}. \tag{7.100}$

*定理 7.2.15 的证明。注意 Jentzen 等人 [229, 定理 1.1] 确立了第* (i)*、*(ii)* 和* (iii) *项。定理 7.2.15 的证明至此完成。* \hfill $\square$

## 7.2.4 强制性目标函数的 SGD 收敛速率

下一个结果，即下文的定理 7.2.16，其陈述和证明可在 Jentzen 等人 [221, 定理 1.1] 中找到。

**定理 7.2.16。** *设* $\mathfrak{o} \in \mathbb{N}$，$p, \alpha, \kappa, c \in (0, \infty)$，$\nu \in (0, 1)$，$q = \min (\{ 2, 4, 6, \ldots \} \cap [\mathfrak{o}, \infty) )$，$\xi, \vartheta \in \mathbb{R}^\mathfrak{o}$。*设* $(\Omega, \mathcal{F}, \mathbb{P})$ *为概率空间，设* $(S, \mathcal{S})$ *为可测空间，设* $X_n: \Omega \to S$，$n \in \mathbb{N}$，*为* i.i.d. *随机变量，设* $\ell = (\ell (\theta, x))_{\theta \in \mathbb{R}^\mathfrak{o}, x \in S}: \mathbb{R}^\mathfrak{o} \times S \to \mathbb{R}$ *为* $(\mathcal{B} (\mathbb{R}^\mathfrak{o}) \times \mathcal{S}) / \mathcal{B} (\mathbb{R})$-*可测函数。假设对于所有* $x \in S$ *，有* $(\mathbb{R}^\mathfrak{o} \ni \theta \mapsto \ell (\theta, x) \in \mathbb{R}) \in C^1 (\mathbb{R}^\mathfrak{o}, \mathbb{R})$，*假设对于所有* $\theta \in \mathbb{R}^\mathfrak{o}$ *，有*

$\mathbb{E} [ \ell (\theta, X_1) ] + \| (\nabla_{\vartheta} \ell) (\theta, X_1) \|_2 < \infty, \tag{7.101}$

$\langle \theta - \vartheta, \mathbb{E} [ (\nabla_{\vartheta} \ell) (\theta, X_1) ] \rangle \ge c \max \{ \| \theta - \vartheta \|_2^2, \| \mathbb{E} [ (\nabla_{\vartheta} \ell) (\theta, X_1) ] \|_2^2 \}, \tag{7.102}$

*且* $\mathbb{E} \big[ \| (\nabla_{\vartheta} \ell) (\theta, X_1) - \mathbb{E} [ (\nabla_{\vartheta} \ell) (\theta, X_1) ] \|_2^q \big] \le \kappa (1 + \| \vartheta \|_2^q), \tag{7.103}$ *设* $\mathcal{L}: \mathbb{R}^\mathfrak{o} \to \mathbb{R}$ *满足对于所有* $\theta \in \mathbb{R}^\mathfrak{o}$ *有* $\mathcal{L} (\theta) = \mathbb{E} [ \ell (\theta, X_1) ]$，*并设* $\Theta: \mathbb{N}_0 \times \Omega \to \mathbb{R}^\mathfrak{o}$ *为满足对于所有* $n \in \mathbb{N}$ *有*

$\Theta_0 = \xi \quad \quad \text{且} \quad \quad \Theta_n = \Theta_{n-1} - \frac{\alpha}{n^\nu} (\nabla_{\vartheta} \ell) (\Theta_{n-1}, X_n) \tag{7.104}$

*的随机过程（参见定义 1.4.7 和 3.3.4）。则*

