
**推论 9.8.4.** 设 $\varepsilon \in (0, \infty)$，$U \subseteq \mathbb{R}$，$\vartheta \in U$ 满足 $U = \{ \theta \in \mathbb{R} : |\theta - \vartheta| \le \varepsilon \}$，且设 $\mathscr{L} : U \rightarrow \mathbb{R}$ 满足对于所有 $\theta \in U$，有

$$\limsup_{K \to \infty} \left| \mathscr{L} (\theta) - \mathscr{L} (\vartheta) - \sum_{k=1}^{K} a_{k} (\theta - \vartheta)^{k} \right| = 0. \tag{9.99}$$

那么存在 $\delta \in (0, \varepsilon)$，$c \in (0, \infty)$，$\alpha \in (0, 1)$，使得对于所有 $\theta \in \{ \xi \in \mathbb{R} : |\xi - \vartheta| < \delta \}$，成立

$$|\mathscr{L} (\theta) - \mathscr{L} (\vartheta)|^{\alpha} \le c \, |\mathscr{L}^{\prime} (\vartheta)|. \tag{9.100}$$

*推论 9.8.4 的证明.* 在整个证明过程中，令 $V \subseteq \mathbb{R}$ 满足 $V = \{ \theta \in \mathbb{R} : |\theta| \le \varepsilon \}$，并令 $\mathcal{M} : V \rightarrow \mathbb{R}$ 满足对于所有 $\theta \in V$，有 $\mathcal{M}(\theta) = \mathscr{L} (\theta + \vartheta)$。注意到 (9.99) 以及对于所有 $\theta \in V$ 都有 $\theta + \vartheta \in U$ 这一事实，确保了对于所有 $\theta \in V$，成立

$$\begin{aligned} &\limsup_{K \to \infty} \left| \mathcal{M} (\theta) - \mathcal{M}(0) - \sum_{k=1}^{K} a_{k} \theta^{k} \right| \\ &= \limsup_{K \to \infty} \left| \mathscr{L}(\theta + \vartheta) - \mathscr{L} (\vartheta) - \sum_{k=1}^{K} a_{k} ((\theta + \vartheta) - \vartheta)^{k} \right| = 0. \end{aligned} \tag{9.101}$$

因此，推论 9.8.3 确立了存在 $\delta \in (0, \varepsilon)$，$c \in (0, \infty)$，$\alpha \in (0, 1)$，使得对于所有 $\theta \in \{ \xi \in \mathbb{R} : |\xi| < \delta \}$，成立

$$|\mathcal{M} (\theta) - \mathcal{M}(0)|^{\alpha} \le c \, |\mathcal{M}^{\prime} (0)|. \tag{9.102}$$

因此，对于所有 $\theta \in \{ \xi \in \mathbb{R} : |\xi| < \delta \}$，我们得到

$$|\mathscr{L}(\theta + \vartheta) - \mathscr{L} (\vartheta)|^{\alpha} \le c \, |\mathscr{L}^{\prime} (\vartheta)|. \tag{9.103}$$

这蕴含了 (9.100)。由此，推论 9.8.4 的证明完成。

**推论 9.8.5.** 设 $U \subseteq \mathbb{R}$ 是开集，设 $\mathscr{L} : U \rightarrow \mathbb{R}$ 是解析的，且设 $\vartheta \in U$（*参见* 定义 9.7.1）。那么存在 $\varepsilon, c \in (0, \infty)$，$\alpha \in (0, 1)$，使得对于所有 $\theta \in \{ \xi \in U : |\vartheta - \xi| < \varepsilon \}$，成立

$$|\mathscr{L} (\vartheta) - \mathscr{L} (\theta)|^{\alpha} \le c \, | (\nabla \mathscr{L}) (\vartheta)|. \tag{9.104}$$

*推论 9.8.5 的证明.* 注意到推论 9.8.4 确立了 (9.104)。由此，推论 9.8.5 的证明完成。

**推论 9.8.6.** 设 $\mathscr{L} : \mathbb{R} \rightarrow \mathbb{R}$ 是解析的（*参见* 定义 9.7.1）。那么 $\mathscr{L}$ 是一个标准 *KL* 函数（*参见* 定义 9.1.2）。

*推论 9.8.6 的证明.* 注意到 (9.2) 和推论 9.8.5 确立了 $\mathscr{L}$ 是一个标准 *KL* 函数（*参见* 定义 9.1.2）。由此，推论 9.8.6 的证明完成。

## 9.9 解析函数的标准 KL 不等式

**定理 9.9.1（解析函数的标准 KL 不等式）。** *设* $\mathfrak{d} \in \mathbb{N}$，*设* $U \subseteq \mathbb{R}^{\mathfrak{d}}$ *是开集，设* $\mathcal{L}: U \rightarrow \mathbb{R}$ *是解析的，且设* $\vartheta \in U$（*参见* 定义 9.7.1*）。* 那么存在 $\varepsilon, c \in (0, \infty)$，$\alpha \in (0, 1)$，使得对于所有 $\theta \in \{u \in U: \|\vartheta-u\|_2 < \varepsilon\}$，成立

$\left|\mathcal{L}(\vartheta)-\mathcal{L}(\theta)\right|^{\alpha} \leq c \|\nabla \mathcal{L}(\theta)\|_2\tag{9.105}$

（*参见* 定义 3.3.4*）。

*定理 9.9.1 的证明.* *注意到 Lojasiewicz* [281, Proposition 1] *证明了* (9.105)（*例如，另见 Biernstone & Milman* [38, Proposition 6.8]*）。*由此，定理 9.9.1 的证明完成。*

**推论 9.9.2.** *设* $\mathfrak{d} \in \mathbb{N}$ *且设* $\mathcal{L}: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ *是解析的（参见* 定义 9.7.1*）。* 那么 $\mathcal{L}$ *是一个标准* **KL** *函数（参见* 定义 9.1.2*）。

*推论 9.9.2 的证明.* *注意到* (9.2) *和* 定理 9.9.1 *确立了* $\mathcal{L}$ *是一个标准* **KL** *函数（参见* 定义 9.1.2*）。* 由此，*推论 9.9.2 的证明完成。*

## 9.10 反例

**例 9.10.1（一个不是标准 KL 函数的光滑函数的例子）。** *设* $\mathcal{L}: \mathbb{R} \rightarrow \mathbb{R}$ *满足对于所有* $x \in \mathbb{R}$，有

$\mathcal{L}(x)=\left\{\begin{array}{ll} \exp \left(-x^{-1}\right) & : x>0 \\ 0 & : x \leq 0 . \end{array}\right.\tag{9.106}$

*那么*
- * $(i)$* 成立 $\mathcal{L} \in C^{\infty}(\mathbb{R}, \mathbb{R})$，
- * $(ii)$* 对于所有 $x \in (0, \infty)$，成立 $\mathcal{L}^{\prime}(x)=x^{-2} \exp \left(-x^{-1}\right)$，
- * $(iii)$* 对于所有 $\alpha \in (0,1)$，$\varepsilon \in (0, \infty)$，成立

$\sup_{x \in(0, \varepsilon)}\left(\frac{\left|\mathcal{L}(x)-\mathcal{L}(0)\right|^{\alpha}}{\left|\mathcal{L}^{\prime}(x)\right|}\right)=\infty,\tag{9.107}$

*且*
- * $(iv)$* 成立 $\mathcal{L}$ *不是标准* **KL** *函数*

（*参见* 定义 9.1.2*）。

*例 9.10.1 的证明.* 在整个证明过程中，令

$P = \{f \in C((0, \infty), \mathbb{R}): f \text{ 是多项式}\}$ (9.108)

并且对于每个 $f \in C((0, \infty), \mathbb{R})$，令 $G_f: (0, \infty) \to \mathbb{R}$ 满足对于所有 $x \in (0, \infty)$，有

$G_f(x) = f(x^{-1}) \exp(-x^{-1}).$ (9.109)

注意到链式法则和乘法法则确保了对于所有 $f \in C^1((0, \infty), \mathbb{R})$ 和 $x \in (0, \infty)$，成立 $G_f \in C^1((0, \infty), \mathbb{R})$ 且

$\begin{aligned} (G_f)^{\prime}(x) = &-f^{\prime}(x^{-1})x^{-2} \exp(-x^{-1}) + f(x^{-1})x^{-2} \exp(-x^{-1}) \\ & = (f(x^{-1}) - f^{\prime}(x^{-1}))x^{-2} \exp(-x^{-1}). \end{aligned}$ (9.110)

因此，对于所有 $p \in P$，存在 $q \in P$ 使得

$(G_p)^{\prime} = G_q,$ (9.111)

结合这一点和 (9.110) 以及归纳法，确保了对于所有 $p \in P$ 和 $n \in \mathbb{N}$，成立

$G_p \in C^{\infty}((0, \infty), \mathbb{R}) \quad \text{ 和 } \quad (\exists q \in P: (G_p)^{(n)} = G_q).$ (9.112)

结合这一事实以及对于所有 $p \in P$ 都有 $\lim_{x \searrow 0} G_p(x) = 0$，确立了对于所有 $p \in P$，成立

$\lim_{x \searrow 0} (G_p)^{(n)}(x) = 0,$ (9.113)

$\mathscr{L}|_{(0, \infty)} = G_{|_{(0, \infty) \ni x \mapsto 1 \in \mathbb{R}}}$ 和 (9.110) 因此确立了条目 (i) 和条目 (iii)。注意到 (9.106) 以及对于所有 $y \in (0, \infty)$ 成立

$\exp(y) = \sum_{k=0}^{\infty} \frac{y^k}{k!} \geq \frac{y^3}{3!} = \frac{y^3}{6}$ (9.114)

确保了对于所有 $\alpha \in (0, 1)$，$\varepsilon \in (0, \infty)$，$x \in (0, \varepsilon)$，成立

$\begin{aligned} \frac{|\mathscr{L}(x) - \mathscr{L}(0)|^{\alpha}}{|\mathscr{L}^{\prime}(x)|} & = \frac{|\mathscr{L}(x)|^{\alpha}}{|\mathscr{L}^{\prime}(x)|} = \frac{x^2 |\mathscr{L}(x)|^{\alpha}}{|\mathscr{L}(x)|} = x^2 |\mathscr{L}(x)|^{\alpha-1} \\ & = x^2 \exp\left( \frac{(1-\alpha)}{x} \right) \geq \frac{x^2(1-\alpha)^3}{6x^3} = \frac{(1-\alpha)^3}{6x}. \end{aligned}$ (9.115)

因此，对于所有 $\alpha \in (0, 1)$，$\varepsilon \in (0, \infty)$，我们得到

$\sup_{x \in (0, \varepsilon)} \left( \frac{|\mathscr{L}(x) - \mathscr{L}(0)|^{\alpha}}{|\mathscr{L}^{\prime}(x)|} \right) \geq \sup_{x \in (0, \varepsilon)} \left( \frac{(1-\alpha)^3}{6x} \right) = \infty.$ (9.116)

由此，例 9.10.1 的证明完成。 □

**例 9.10.2**（一个不满足标准 **KL** 不等式的可微函数的例子）。*设* \(\mathcal{L} : \mathbb{R} \to \mathbb{R}\) *满足对于所有* \(x \in \mathbb{R}\)，有

\[ \mathcal{L}(x)= \int_{0}^{\max \{x, 0\}} y|\sin(y^{-1})| \, dy. \tag{9.117} \]

*那么*
- (i) 成立 \(\mathcal{L} \in C^{1}(\mathbb{R}, \mathbb{R})\)，
- (ii) 对于所有 \(c \in \mathbb{R}\)，\(\alpha, \varepsilon \in (0, \infty)\)，*存在* \(x \in (0, \varepsilon)\) *使得*

\[ |\mathcal{L}(x)-\mathcal{L}(0)|^{\alpha} > c|\mathcal{L}^{\prime}(x)|, \tag{9.118} \]

- (iii) 对于所有 \(c \in \mathbb{R}\)，\(\alpha, \varepsilon \in (0, \infty)\)，*不成立* \(\mathcal{L}\) *在* \([0, \varepsilon)\) *上以指数* \(\alpha\) *和常数* \(c\) *在* \(0\) *处满足标准* **KL** *不等式*

（*参见* 定义 9.1.1*）。

**例 9.10.2 的证明.** 在整个证明过程中，令 \(\mathcal{G}: \mathbb{R} \to \mathbb{R}\) 满足对于所有 \(x \in \mathbb{R}\)，有

\[ \mathcal{G}(x)= \begin{cases} x|\sin(x^{-1})| & : x > 0 \\[2pt] 0 & : x \leq 0. \end{cases} \tag{9.119} \]

注意到 (9.119) 证明了对于所有 \(k \in \mathbb{N}\)，成立

\[ \mathcal{G}((k \pi)^{-1})= (k \pi)^{-1}|\sin(k \pi)|= 0. \tag{9.120} \]

此外，观察到 (9.119) 表明对于所有 \(x \in (0, \infty)\)，

\[ |\mathcal{G}(x)-\mathcal{G}(0)|= |x\sin(x^{-1})| \leq |x|. \tag{9.121} \]

因此，我们得到 \(\mathcal{G}\) 是连续的。结合这一点、(9.117) 和微积分基本定理，确保了 \(\mathcal{L}\) 是连续可微的，且

\[ \mathcal{L}^{\prime}=\mathcal{G}. \tag{9.122} \]

结合这一点和 (9.120) 证明了对于所有 \(c \in \mathbb{R}\)，\(\alpha \in (0, \infty)\)，\(k \in \mathbb{N}\)，成立

\[ |\mathcal{L}((k \pi)^{-1})-\mathcal{L}(0)|^{\alpha}= |\mathcal{L}((k \pi)^{-1})|^{\alpha} > 0= c|\mathcal{G}((k \pi)^{-1})|= c|\mathcal{L}^{\prime}((k \pi)^{-1})|. \tag{9.123} \]

由此，例 9.10.2 的证明完成。 \(\quad\) \(\square\)

