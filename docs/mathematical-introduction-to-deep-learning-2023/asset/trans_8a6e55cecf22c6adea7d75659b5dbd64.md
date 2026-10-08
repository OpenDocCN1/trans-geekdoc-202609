
# 4.4.4 逼近误差的精细化收敛速率

**引理 4.4.11.** 设 $d, \mathbf{d}, \mathbf{L} \in \mathbb{N}$，$L, a \in \mathbb{R}$，$b \in (a, \infty)$，$u \in [-\infty, \infty)$，$v \in (u, \infty)$，$\mathbf{l} = (l_0, l_1, \dots, l_{\mathbf{L}}) \in \mathbb{N}^{\mathbf{L}+1}$，假设 $l_0 = d$，$\mathbf{l}_{\mathbf{L}} = 1$，且 $\mathbf{d} \ge \sum_{i=1}^{\mathbf{L}} \mathbf{l}_i(\mathbf{l}_{i-1}+1)$，令 $f: [a, b]^d \to ([u, v] \cap \mathbb{R})$ 满足对于所有 $x, y \in [a, b]^d$，有 $|f(x) - f(y)| \le L \|x - y\|_1$（参见定义 3.9.4）。则存在 $\vartheta \in \mathbb{R}^{\mathbf{d}}$，使得 $\|\vartheta\|_\infty \le \sup_{x \in [a, b]^d} |f(x)|$ 且

$$\sup_{x \in [a, b]^d} \left| \mathcal{A}_{a, v}^{\vartheta, \mathbf{l}}(x) - f(x) \right| \le \frac{dL(b-a)}{2} \tag{4.196}$$

（参见定义 4.4.1）。

*引理 4.4.11 的证明.* 在整个证明过程中，令 $\mathbf{d} = \sum_{i=1}^{\mathbf{L}} \mathbf{l}_i(\mathbf{l}_{i-1}+1)$，令 $\mathbf{m} = (\mathbf{m}_1, \mathbf{m}_2$, $\dots, \mathbf{m}_{\mathbf{d}}) \in [a, b]^{\mathbf{d}}$ 满足对于所有 $i \in \{1, 2, \dots, d\}$，有

$$\mathbf{m}_i = \frac{a+b}{2}, \tag{4.197}$$

并令 $\vartheta = (\vartheta_1, \vartheta_2, \dots, \vartheta_{\mathbf{d}}) \in \mathbb{R}^{\mathbf{d}}$ 满足对于所有 $i \in \{1, 2, \dots, \mathbf{d}\} \setminus \{\mathbf{d}\}$，有 $\vartheta_i = 0$，且 $\vartheta_{\mathbf{d}} = f(\mathbf{m})$。注意到假设 $\mathbf{l}_{\mathbf{L}} = 1$ 以及事实 $\forall i \in \{1, 2, \dots, \mathbf{d} - 1\} : \vartheta_i = 0$ 表明，对于所有 $x = (x_1, x_2, \dots, x_{\mathbf{l}_{\mathbf{L}-1}}) \in \mathbb{R}^{\mathbf{l}_{\mathbf{L}-1}}$，成立

$$\begin{align*} \mathcal{A}_{\mathbf{l}_1, \mathbf{l}_{\mathbf{L}-1}}^{\vartheta, \sum_{i=1}^{\mathbf{L}-1} \mathbf{l}_i(\mathbf{l}_{i-1}+1)}(x) &= \left[ \sum_{i=1}^{\mathbf{l}_{\mathbf{L}-1}} \vartheta \left[ \sum_{i=1}^{\mathbf{L}-1} \mathbf{l}_i(\mathbf{l}_{i-1}+1) + i \right] x_i \right] + \vartheta_{\sum_{i=1}^{\mathbf{L}-1} \mathbf{l}_i(\mathbf{l}_{i-1}+1) + \mathbf{l}_{\mathbf{L}-1} + 1} \\ &= \left[ \sum_{i=1}^{\mathbf{l}_{\mathbf{L}-1}} \vartheta_{\left[ \sum_{i=1}^{\mathbf{L}-1} \mathbf{l}_i(\mathbf{l}_{i-1}+1) - (\mathbf{l}_{\mathbf{L}-1} - i + 1) \right] x_i} \right] + \vartheta_{\sum_{i=1}^{\mathbf{L}-1} \mathbf{l}_i(\mathbf{l}_{i-1}+1)} \\ &= \left[ \sum_{i=1}^{\mathbf{l}_{\mathbf{L}-1}} \vartheta_{\mathbf{d} - (\mathbf{l}_{\mathbf{L}-1} - i + 1)} x_i \right] + \vartheta_{\mathbf{d}} = \vartheta_{\mathbf{d}} = f(\mathbf{m}) \tag{4.198} \end{align*}$$

（参见定义 1.1.1）。结合这一事实以及 $f(\mathbf{m}) \in \overline{[u, v]}$ 可知，对于所有 $x \in \mathbb{R}^{\mathbf{l}_{\mathbf{L}-1}}$，成立

$$\begin{align*} \left( \mathfrak{C}_{u, v, \mathbf{L}} \circ \mathcal{A}_{\mathbf{l}_1, \mathbf{l}_{\mathbf{L}-1}}^{\vartheta, \sum_{i=1}^{\mathbf{L}-1} \mathbf{l}_i(\mathbf{l}_{i-1}+1)} \right)(x) &= \left( \mathfrak{C}_{u, v, 1} \circ \mathcal{A}_{\mathbf{l}_1, \mathbf{l}_{\mathbf{L}-1}}^{\vartheta, \sum_{i=1}^{\mathbf{L}-1} \mathbf{l}_i(\mathbf{l}_{i-1}+1)} \right)(x) \\ &= \mathfrak{C}_{u, v, \mathfrak{f}}(f(\mathbf{m})) = \max\{u, \min\{\mathfrak{f}(\mathbf{m}), v\}\} \\ &= \max\{u, f(\mathbf{m})\} = f(\mathbf{m}) \tag{4.199} \end{align*}$$

（参见定义 1.2.9 和 1.2.10）。这意味着对于所有 $x \in \mathbb{R}^d$，有

$$\mathcal{A}_{a, v}^{\vartheta, \mathbf{l}}(x) = f(\mathbf{m}). \tag{4.200}$$

此外，注意 (4.197) 表明，对于所有 $x \in [a, \mathbf{m}_1]$，$\mathfrak{f} \in [\mathbf{m}_1, b]$，成立

$$\begin{align*} |\mathbf{m}_1 - x| &= \mathbf{m}_1 - x = \frac{(a+b)}{2} - x \le \frac{(a+b)}{2} - a = \frac{(b-a)}{2} \\ \text{且} \quad |\mathbf{m}_1 - \mathfrak{f}| &= \mathfrak{f} - \mathbf{m}_1 = \mathfrak{f} - \frac{(a+b)}{2} \le b - \frac{(a+b)}{2} = \frac{(b-a)}{2}. \tag{4.201} \end{align*}$$

假设 $\forall x, y \in [a, b]^d, |f(x) - f(y)| \le L\|x - y\|_1$ 以及 (4.200) 从而证明，对于所有 $x = (x_1, x_2, \ldots, x_d) \in [a, b]^d$，成立

$$|\mathcal{A}^{d, 1}_{u, v}(x) - f(x)| = |f(\mathbf{m}) - f(x)| \le L\|\mathbf{m} - x\|_1 = L\sum_{i=1}^{d} |\mathbf{m}_i - x_i|$$
$$= L\sum_{i=1}^{d} |\mathbf{m}_i - x_i| \le \sum_{i=1}^{d} \frac{L(b - a)}{2} = \frac{dL(b - a)}{2}.$$ (4.202)

结合 $\|\vartheta\|_{\infty} = \max_{i \in \{1, 2, \ldots, d\}} |\vartheta_i| = |f(\mathbf{m})| \le \sup_{x \in [a, b]^d} |f(x)|$ 这一事实，确立了 (4.196)。引理 4.4.11 的证明至此完成。 $\Box$

**命题 4.4.12.** *设* $d, \mathbf{L} \in \mathbb{N}$，$A \in (0, \infty)$，$L, a \in \mathbb{R}$，$b \in (a, \infty)$，$u \in [-\infty, \infty)$，$v \in (u, \infty]$，$\mathbf{l} = (\mathbf{l}_1, \mathbf{l}_2, \ldots, \mathbf{l}_{\mathbf{L}}) \in \mathbb{N}^{\mathbf{L} + 1}$，*假设*

$$\mathbf{L} \ge 1 + \lfloor\log_2(A/(2d))\rfloor + 1\rceil^{(6d, \infty)}(A), \quad \mathbf{l}_0 = d, \quad \mathbf{l}_1 \ge \mathtt{A}^{(6d, \infty)}(A), \quad \mathbf{l}_{\mathbf{L}} = 1,$$ (4.203)

*且* $\mathbf{d} \ge \sum_{i=1}^{\mathbf{L}} \mathbf{l}_i(\mathbf{l}_{i-1} + 1)$，*假设对于所有* $i \in \{1, 2, \ldots, \mathbf{L}\} \setminus \{1, \mathbf{L}\}$，*有*

$$\mathbf{l}_i \ge 3^{\lceil A/(2^i d) \rceil \overline{\lfloor}^{(6d, \infty)}(A)},$$ (4.204)

*并令* $f : [a, b]^d \to ([u, v] \cap \mathbb{R})$ *满足对于所有* $x, y \in [a, b]^d$，*有*

$$|f(x) - f(y)| \le L\|x - y\|_1$$ (4.205)

*(参见定义 3.9.4 和 4.2.6)。则存在* $\vartheta \in \mathbb{R}^{\mathbf{d}}$ *使得* $\|\vartheta\|_{\infty} \le \max \{1, L, |a|, \allowbreak |b|, |k|, |b|, \mathbf{k}, b, \{2^{\sup_{x \in [a, b]^d} |f(x)|}\}$ *且*

$$\sup_{x \in [a, b]^d} |\mathcal{A}^{d, 1}_{u, v}(x) - f(x)| \le \frac{3dL(b - a)}{A^{1/d}}$$ (4.206)

*(参见定义 4.4.1)。*

*命题 4.4.12 的证明.* 在整个证明过程中，不失一般性，假设 $A > 6^d$（参见引理 4.4.11），令 $\mathfrak{F} = \lfloor(A/2d)^{1/d}\rceil \in \mathbb{Z}$。注意到对于所有 $k \in \mathbb{N}$，$2k \le 2(2^{k - 1}) = 2^k$ 这一事实表明 $3^d = 6^d/2^d \le A/(2d)$。因此，我们得到

$$2 \le \frac{2}{3} \lfloor \frac{A}{2d} \rceil^{1/d} \le \lfloor \frac{A}{2d} \rceil^{1/d} - 1 < 3.$$ (4.207)

在下一步中，令 $r = d(b - a)/23 \in (0, \infty)$，令 $\delta : [a, b]^d \times [a, b]^d \to \mathbb{R}$ 满足对于所有 $x, y \in [a, b]^d$，$\delta(x, y) = \|x - y\|_1$，并令 $K = \max \{2, \mathtt{C}^{([a, b]^d, \delta), r} \} \in \mathbb{N} \cup \{\infty\}$（参见定义 4.3.2）。注意，(4.207) 和引理 4.3.4 确保

$$K = \max \{2, \mathtt{C}^{([a, b]^d, \delta), r} \} \le \max \left\{2, \left\lceil \frac{d(b - a)}{2r} \right\rceil^d \right\} = \max \{2, (\mathfrak{F})^d \} = \mathfrak{F}^d < \infty.$$ (4.208)

这蕴含

$$4 \le 2dK \le 2d\mathfrak{F}^d \le 2d \left( \frac{A}{2d} \right) = A.$$

结合这一事实以及 $\mathbf{L} \ge 1 + \lfloor\log_2(A/(2d)) + 1\rfloor \ge \lceil \log_2(K) \rceil + 1$，从而证明了 $\lceil \log_2(K) \rceil \le \lfloor \log_2(A/(2d)) \rfloor \le \mathbf{L} - 2$。结合这一点、(4.209)、假设 $\mathbf{l}_L \ge A \ge \lfloor A/(2d) \rfloor^{(d,\infty)}(A) = A$，以及假设 $\forall i \in \{2, 3, \ldots, \mathbf{L}-1\}: \mathbf{l}_i \ge 3^{\lceil A/(2^i d) \rceil \lfloor A/(2d) \rfloor^{(d,\infty)}(A)} = 3^{\lceil A/(2^i d) \rceil}$，证明了对于所有 $i \in \{2, 3, \ldots, \mathbf{L}-1\}$，成立

$$\mathbf{L} \ge \lceil \log_2(K) \rceil + 2, \quad \mathbf{l}_L \ge A \ge 2dK, \quad \text{且} \quad \mathbf{l}_i \ge 3^{\lceil A/(2^i d) \rceil} \ge 3^{\lceil K/(2^{i-1}) \rceil}.$$

令 $\mathbf{f}_1, \mathbf{f}_2, \ldots, \mathbf{f}_K \in [a, b]^d$ 满足

$$\sup_{x \in [a,b]^d} \left[ \inf_{k \in \{1,2,\ldots,K\}} \delta(x, \mathbf{f}_k) \right] \le r.$$

注意到 (4.210)、假设 $\mathbf{l}_0 = d, \mathbf{l}_1 = 1, \mathbf{d} \ge \sum_{i=1}^{\mathbf{L}} \mathbf{l}_i(\mathbf{l}_{i-1} + 1)$，以及 $\forall x, y \in [a, b]^d: |f(x) - f(y)| \le L\|x - y\|_1$，结合推论 4.4.10，确立了存在 $\vartheta \in \mathbb{R}^d$，使得

$$\|\vartheta\|_{\infty} \le \max \{1, L, \max_{k \in \{1,2,\ldots,K\}} \|\mathbf{f}_k\|_{\infty}, 2 \max_{k \in \{1,2,\ldots,K\}} f(\mathbf{f}_k)\}$$

且

$$\sup_{x \in [a,b]^d} |\mathcal{N}^{\vartheta,1}_{a,b}(x) - f(x)| \le 2L \left[ \sup_{x \in [a,b]^d} \left( \inf_{k \in \{1,2,\ldots,K\}} \|x - \mathbf{f}_k\|_1 \right) \right]$$
$$= 2L \left[ \sup_{x \in [a,b]^d} \left( \inf_{k \in \{1,2,\ldots,K\}} \delta(x, \mathbf{f}_k) \right) \right].$$

注意，(4.212) 表明

$$\|\vartheta\|_{\infty} \le \max \{1, L, |a|, |b|, 2 \sup_{x \in [a,b]^d} |f(x)|\}.$$

此外，注意到 (4.213)、(4.207)、(4.211) 以及对于所有 $k \in \mathbb{N}$，$2k \le 2(2^k - 1) = 2^{k+1} - 2 < 2^{k+1}$ 这一事实，确保了

$$\sup_{x \in [a,b]^d} |\mathcal{N}^{\vartheta,1}_{a,b}(x) - f(x)| \le 2L \left[ \sup_{x \in [a,b]^d} \left( \inf_{k \in \{1,2,\ldots,K\}} \delta(x, \mathbf{f}_k) \right) \right]$$
$$\le 2Lr = \frac{dL(b-a)}{3} \le \frac{dL(b-a)}{(2/3)(A/(2^d))^{1/d}} = \frac{2^{1/d} 3dL(b-a)}{2 A^{1/d}} \le \frac{3dL(b-a)}{A^{1/d}}.$$

结合这一点与 (4.214)，蕴含了 (4.206)。命题 4.4.12 的证明至此完成。

**推论 4.4.13.** 设 $d \in \mathbb{N}$，$a \in \mathbb{R}$，$b \in (a, \infty)$，$L \in (0, \infty)$，且令 $f: [a, b]^d \rightarrow \mathbb{R}$ 满足对于所有 $x, y \in [a, b]^d$，有

$$|f(x) - f(y)| \le L\|x - y\|_1$$

