

## 引理 B.10 的证明。

对每个 $n$，令 $\mathcal{B}_n, \mathcal{B}'_n$ 分别表示 $E_n, E'_n$ 的 Borel $\sigma$-代数。根据 Dudley (2002, Theorem 2.5.7) 和 Kallenberg (1997, Lemma 1.2)，$\prod_{j=1}^n E'_j$ 和 $\prod_{j=1}^n E_j$ 分别是具有 Borel $\sigma$-代数 $\otimes_{j=1}^n \mathcal{B}'_j$ 和 $\otimes_{j=1}^n \mathcal{B}_j$ 的波兰空间。令 $\mu_n, \pi_n$ 分别表示 $Y_n$ 和 $(Y_1, ..., Y_n)$ 在 $(E'_n, \mathcal{B}'_n)$ 及 $(\prod_{j=1}^n E'_j, \otimes_{j=1}^n \mathcal{B}'_j)$ 上的分布。由于 $E_n$ 是波兰空间，根据第 B.2 节，已知给定 $\sigma(g_n(X_n))$ 时 $X_n$ 存在正则条件分布。等价地，在 $E_n$ 上存在一族概率分布 $(Q_y^n)_{y \in E'_n}$，满足注解 B.5 中的条件 (I) 和 (II)，其中取 $X := X_n, Y := g_n(X_n) \stackrel{d}{=} Y_n$ 以及 $P^Y := \mu_n$。根据注解 B.5(II)，对所有 $A \in \mathcal{B}_n$ 有 $\mathbb{P}(X_n \in A) = \int_{E'_n} Q_y^n(A) d\mu_n(y)$，并且还可以得到

\[
\int_{B'} \mathbb{1}_B(y) d\mu_n(y) = \mathbb{P}(g_n(X_n) \in B \cap B')
= \mathbb{P}(X_n \in g_n^{-1}(B), g_n(X_n) \in B')
= \int_{B'} Q_y^n(g_n^{-1}(B)) d\mu_n(y) \tag{B.4}
\]

对 $B, B' \in \mathcal{B}'_n$。因此，对所有 $B \in \mathcal{B}'_n$，对于 $\mu_n$-几乎处处的 $y \in E'_n$，有 $Q_y^n(g_n^{-1}(B)) = \mathbb{1}_B(y)$。

对每个 $n \in \mathbb{N}$，我们现在通过如下方式在 $(\prod_{j=1}^n E_j, \otimes_{j=1}^n \mathcal{B}_j)$ 上定义一个新测度 $\pi'_n$：

\[
\pi'_n(A) := \int_{\prod_{j=1}^n E'_j} \left( \int_{E_1} \cdots \int_{E_n} \mathbb{1}_A(x_1, ..., x_n) dQ_{y_n}^n(x_n) \cdots dQ_{y_1}^1(x_1) \right) d\pi_n(y_1, ..., y_n) \tag{B.5}
\]

对 $A \in \otimes_{j=1}^n \mathcal{B}_j$。这是一个良定义的概率测度，这由注解 B.5(III, IV) 和单调收敛定理得出。对每个 $n$，我们声称：

- (i) 对每个 $A \in \otimes_{j=1}^n \mathcal{B}_j$，有 $\pi'_{n+1}(A \times E_{n+1}) = \pi'_n(A)$；
- (ii) 对每个 $A_n \in \mathcal{B}_n$，有 $\mathbb{P}(X_n \in A_n) = \pi'_n(\prod_{j=1}^{n-1} E_j \times A_n)$；
- (iii) $\pi_n = \pi'_n \circ (g_1, ..., g_n)^{-1}$，其中 $(g_1, ..., g_n) : (\prod_{j=1}^n E_j, \otimes_{j=1}^n \mathcal{B}_j) \to (\prod_{j=1}^n E'_j, \otimes_{j=1}^n \mathcal{B}'_j)$ 表示可测映射 $(x_1, ..., x_n) \mapsto (g_1(x_1), ..., g_n(x_n))$。

属性 (i) 直接由 (B.5) 以及对于所有 $B \in \otimes_{j=1}^n \mathcal{B}'_j$ 都有 $\pi_{n+1}(B \times E'_n) = \pi_n(B)$ 这一事实得出。要验证 (ii)，注意

\[
\pi'_n(\prod_{j=1}^{n-1} E_j \times A_n) = \int_{\prod_{j=1}^n E'_j} \int_{E_n} \mathbb{1}_{A_n}(x_n) dQ_{y_n}^n(x_n) d\pi_n(y_1, \dots, y_n) = \int_{E'_n} Q_{y_n}^n(A_n) d\mu_n(y_n) = \mathbb{P}(X_n \in A_n),
\]

其中最后一个等式如上文所述由注解 B.5(II) 得出。至于 (iii)，固定 $1 \le j \le n$ 的 $B_j \in \mathcal{B}'_j$，并注意根据 (B.4) 和 (B.5)，我们有

\[
\pi'_n(\prod_{j=1}^n g_j^{-1}(B_j)) = \int_{\prod_{j=1}^n E'_j} Q_{y_1}^1(g_1^{-1}(B_1)) \cdots Q_{y_n}^n(g_n^{-1}(B_n)) d\pi_n(y_1, \dots, y_n) = \int_{\prod_{j=1}^n E'_j} \mathbb{1}_{B_1}(y_1) \cdots \mathbb{1}_{B_n}(y_n) d\pi_n(y_1, \dots, y_n) = \pi_n(\prod_{j=1}^n B_j).
\]

这意味着 $\pi_n$ 与 $\pi'_n \circ (g_1, \dots, g_n)^{-1}$ 在集合 $\{ \prod_{j=1}^n B_j : B_j \in \mathcal{B}'_j \text{ 对所有 } 1 \le j \le n \}$ 上一致，这是一个生成 $\otimes_{j=1}^n \mathcal{B}_j$ 的 $\pi$-系统，因此 (iii) 成立。

由于波兰空间 $E_1, E_1 \times E_2, \dots$ 上的分布 $\pi'_1, \pi'_2, \dots$ 满足一致性条件 (i)，根据 Daniell-Kolmogorov 扩展定理 (Kallenberg, 1997, Theorem 5.14) 和注解 B.11，存在一序列随机元素 $(X'_n)_{n \in \mathbb{N}}$，其中 $X'_n : \Omega \to E_n$，使得对每个 $n$，在 $\prod_{j=1}^n E_j$ 上有 $(X'_1, \dots, X'_n) \sim \pi'_n$。然后根据上述 (ii) 和 (iii)，对每个 $n$ 有 $X'_n \overset{d}{=} X_n$ 且 $(g_1(X'_1), \dots, g_n(X'_n)) \sim \pi'_n \circ (g_1, \dots, g_n)^{-1} = \pi_n$，其中 $\pi_n$ 被定义为 $(Y_1, \dots, Y_n)$ 的分布。因此，序列 $(g_n(X'_n))$ 和 $(Y_n)$ 具有相同的有限维分布；换句话说，它们的分布在集合 $\{ \prod_{j=1}^N B_j \times \prod_{j=N+1}^\infty E'_j : N \in \mathbb{N}, B_j \in \mathcal{B}'_j \text{ 对所有 } 1 \le j \le N \}$ 上一致，这是一组生成 $\prod_{n=1}^\infty E'_n$ 的柱形 $\sigma$-代数 $\mathcal{B}'$ 的柱面集。（根据 Kallenberg (1997, Lemma 1.2)，$\mathcal{B}'$ 是 $\prod_{n=1}^\infty E'_n$ 的 Borel $\sigma$-代数。）我们得出，作为取值在 $(\prod_{n=1}^\infty E'_n, \mathcal{B}')$ 上的随机序列，有 $(g_1(X'_1), g_2(X'_2), \dots) \overset{d}{=} (Y_1, Y_2, \dots)$。

最后，我们应用 Kallenberg (1997, Corollary 5.11)，取 $T = \prod_{n=1}^\infty E_n, S = \prod_{n=1}^\infty E'_n, \eta = (X'_n), \xi = (Y_n)$ 以及 $f : T \to S$ 由 $f(x_1, x_2, \dots) = (g_1(x_1), g_2(x_2), \dots)$ 给出；注意 $T, S$ 是波兰空间（例如 Dudley, 2002, Theorem 2.5.7），且 $f$ 是 Borel 可测的。既然已经证明了 $f(\eta) \stackrel{d}{=} \xi$，根据 Kallenberg (1997, Corollary 5.11) 可知，存在 $(\tilde{X}_n) \equiv \tilde{\eta} \stackrel{d}{=} \eta = (X'_n)$，使得几乎处处有 $(g_n(\tilde{X}_n)) = f(\tilde{\eta}) = \xi = (Y_n)$，正如所要求的。

在提议 A.16(a, c) 的证明中，我们应用下面关于独立高斯随机变量之伪 Lipschitz 函数和的浓度不等式。

## 引理 B.12。

存在一个普遍常数 $C > 0$，使得对所有 $n \in \mathbb{N}$、$r \ge 2$ 和 $t \ge 0$ 都有：若 $Z_1, \dots, Z_n \stackrel{\mathrm{iid}}{\sim} N(0, 1)$，$L \equiv (L_1, \dots, L_n) \in (0, \infty)^n$ 且对 $1 \le i \le n$ 有 $f_i \in \mathrm{PL}_1(r, L_i)$，那么

\[
\mathbb{P}\left(\left|\frac{1}{n}\sum_{i=1}^n \{f_i(Z_i) - \mathbb{E}(f_i(Z_i))\}\right| \ge t\right) \le \exp\left(1 - \min \left\{ \left(\frac{nt}{(Cr)^r \|L\|_2}\right)^2, \left(\frac{nt}{(Cr)^r \|L\|_\infty}\right)^{2/r} \right\}\right). \tag{B.6}
\]

证明。我们先考虑 $n=1$ 的情况。对任意 $r \ge 2$ 和 $L > 0$，我们可以不失一般性地假设 $f \equiv f_1 \in \mathrm{PL}(r, L)$ 满足 $f(0) = 0$，从而对所有 $x \in \mathbb{R}$ 有 $|f(x)| = |f(x) - f(0)| \le L(|x| + |x|^r) \le 2L(|x| \vee |x|^r)$。因此，若 $Z \sim N(0, 1)$，则

\[
\mathbb{P}(|f(Z)| \ge s) \le \mathbb{P}(|Z| \vee |Z|^r \ge s/(2L)) \le e^{-\frac{1}{2} \min \left\{ (\frac{s}{2L})^2, (\frac{s}{2L})^{2/r} \right\}} \tag{B.7}
\]

对所有 $s \ge 0$，且

\[
\frac{\mathbb{E}(|f(Z)|)}{L} \le \mathbb{E}(|Z| + |Z|^r) = \left( \sqrt{\frac{2}{\pi}} + \frac{2^{r/2}}{\sqrt{\pi}} \Gamma\left(\frac{r+1}{2}\right) \right) =: v_r
\]

通过直接计算得出。现在，根据 Stirling 公式的一个非渐近版本，对所有 $x > 0$ 有 $\Gamma(x) < e^{1/(12x)}(x/e)^x \sqrt{2\pi/x}$；参见例如 Gordon (1994, Theorem 5) 和 Dümbgen et al. (2021, Lemma 10)。由于 $r \ge 2$，我们有 $(r+1)/e < r$ 且 $(\sqrt{2}-1)r^{r/2} \ge 2(\sqrt{2}-1) > 1/\sqrt{\pi}$。因此，

\[
\frac{v_r}{2} \le \frac{1}{\sqrt{2}} \left( \frac{1}{\sqrt{\pi}} + \left( \frac{r+1}{e} \right)^{r/2} e^{\frac{1}{6(r+1)} - \frac{1}{2}} \right) \le \frac{1}{\sqrt{2}} \left( \frac{1}{\sqrt{\pi}} + r^{r/2} \right) < r^{r/2}. \tag{B.8}
\]

因此，对于 \( t \ge Lv_r \)，根据 (B.7) 和 (B.8) 可得

\[
\begin{aligned}
\mathbb{P}\{|f(Z) - \mathbb{E}(f(Z))| \ge t\} \le \mathbb{P}\{|f(Z)| \ge t - \mathbb{E}(|f(Z)|)\} \\
\le e^{-\frac{1}{2} \min\left\{(\frac{t}{2L} - \frac{v_r}{2})^2, \, (\frac{t}{2L} - \frac{v_r}{2})^{2/r}\right\}} \\
\le e^{\frac{1}{2} - \frac{1}{2}(\frac{t}{2L} - \frac{v_r}{2})^{2/r}} \\
\le e^{\frac{1+r}{2} - \frac{1}{2}(\frac{t}{2L})^{2/r}} \\
\le e^{1 - (\frac{t}{2L})^{2/r} \frac{1}{r+1}},
\end{aligned}
\]

其中第三个不等式来自如上所述的事实：对 $r \ge 2$ 和任意 $a, b \ge 0$ 有 $a^{2/r} \le |a - b|^{2/r} + b^{2/r}$。由于根据 (B.8)，对所有 $t \in [0, Lv_r)$ 都有 $1 - (r + 1)^{-1}\{t/(2L)\}^{2/r} > 1 - (r + 1)^{-1}(v_r/2)^{2/r} > 0$，因此 (B.9) 平凡成立，所以当 $n=1$ 时 (B.6) 在 $C = 3$ 处成立。

我们现在借助 Kuchibhotla and Chakrabortty (2018) 中的 Theorem 3.1 和 Proposition A.3 推导一般 $n \ge 2$ 的 (B.6)；另参见 Bakhshizadeh et al. (2020) 中的 Theorem 1 和 Corollary 2。如同在 Kuchibhotla and Chakrabortty (2018) 的第 2 和 3 节中一样，我们首先为每个 $\beta > 0$ 定义 $\vartheta_\beta: [0, \infty) \to [0, \infty)$ 为 $\vartheta_\beta(x) := \exp(x^\beta) - 1$。此外，对于 $\beta, \lambda > 0$，令 $\vartheta_{\beta, \lambda}: [0, \infty) \to [0, \infty)$ 为连续严格递增函数，其反函数对 $t \ge 0$ 给出为 $\vartheta_{\beta, \lambda}^{-1}(t) := \log^{1/2}(1 + t) + \lambda \log^{1/\beta}(1 + t)$。对于随机变量 $X$ 和满足 $g(0) = 0$ 的严格递增函数 $g: [0, \infty) \to [0, \infty)$，我们记 $\Xi_g(X) := \inf\{\theta > 0 : \mathbb{E}(g(|X|/\theta)) \le 1\} \in [0, \infty]$，按惯例令 $\inf \emptyset = \infty$。注意，当 $g$ 为凸函数时，$\Xi_g(X)$ 正是 $X$ 的 $g$-Orlicz 范数，但当 $g$ 不是凸函数时（例如下面证明中的 $g = \vartheta_\beta$ 且 $\beta \in (0, 1)$），$\Xi_g$ 通常不定义范数。

对于任意 $n \ge 2$、$r \ge 2$ 和 $L \equiv (L_1, \dots, L_n) \in (0, \infty)^n$，令 $f_1, \dots, f_n \in \text{PL}(r, L_i)$ 和 $Z_1, \dots, Z_n \stackrel{\text{iid}}{\sim} N(0, 1)$，并不失一般性地假设对所有 $1 \le i \le n$ 有 $X_i := f_i(Z_i)$ 满足 $\mathbb{E}(X_i) = 0$。取 $\beta := 2/r \in [0, 1]$ 及对 $1 \le i \le n$ 的 $\theta_i := 2\{4(r + 1)\}^{r/2} L_i$，我们

