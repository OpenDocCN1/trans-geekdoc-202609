
(ii) $\mathcal{O}(\mathbf{F}) = 1$ 成立，

(iii) $\mathcal{H}(\mathbf{F}) = 0$ 成立，

(iv) $\mathcal{P}(\mathbf{F}) = d + 1$ 成立，

(v) $\|\mathcal{T}(\mathbf{F})\|_{\infty} \le \sup_{x \in [a,b]^d} |f(x)|$ 成立，且

(vi) $\sup_{x \in [a,b]^d} | (\mathcal{R}_v^\mathbf{N}(\mathbf{F}))(x) - f(x)| \le \frac{d L (b-a)}{2}$ 成立

（参见定义 1.2.4, 1.3.1, 1.3.4, 和 1.3.5）。

引理 4.3.5 的证明。注意，假设对于所有 $x, y \in [a,b]^d$ 都有 $|f(x) - f(y)| \le L \|x - y\|_1$ 成立，这保证了 $L \ge 0$。接下来观察，引理 2.3.2 保证了对于所有 $x \in \mathbb{R}^d$ 都有

$ (\mathcal{R}_v^\mathbf{N}(\mathbf{F}))(x) = f((a+b)/2, (a+b)/2, \dots, (a+b)/2). \qquad (4.93) $

对于所有 $x \in [a,b]$ 都有 $|x - (a+b)/2| \le (b-a)/2$ 成立，且假设对于所有 $x, y \in [a,b]^d$ 都有 $|f(x) - f(y)| \le L \|x - y\|_1$ 成立，因此确保对于所有 $x = (x_1, x_2, \dots, x_d) \in [a,b]^d$ 都有

$\begin{align*} &| (\mathcal{R}_v^\mathbf{N}(\mathbf{F}))(x) - f(x)| = | f((a+b)/2, (a+b)/2, \dots, (a+b)/2) - f(x)| \\ &\quad\le L \|((a+b)/2, (a+b)/2, \dots, (a+b)/2) - x\|_1 \\ &\quad= L \sum_{i=1}^d |(a+b)/2 - x_i| \le \sum_{i=1}^d \frac{L(b-a)}{2} = \frac{d L (b-a)}{2}. \end{align*} \qquad (4.94) $

结合 $\|\mathcal{T}(\mathbf{F})\|_{\infty} = |f((a+b)/2, (a+b)/2, \dots, (a+b)/2)| \le \sup_{x \in [a,b]^d} |f(x)|$ 这一事实，完成了引理 4.3.5 的证明。

命题 4.3.6. 设 $d \in \mathbb{N}$，$L, a \in \mathbb{R}$，$b \in (a, \infty)$，$r \in (0, d/4)$，设 $f: [a,b]^d \rightarrow \mathbb{R}$ 和 $\delta: [a,b]^d \times [a,b]^d \rightarrow \mathbb{R}$ 满足对于所有 $x, y \in [a,b]^d$，$|f(x) - f(y)| \le L \|x - y\|_1$ 且 $\delta(x, y) = \|x - y\|_1$，并设 $K \in \mathbb{N}$，$\mathbf{f}_1, \mathbf{f}_2, \dots, \mathbf{f}_K \in [a,b]^K$，$\mathbf{v} \in \mathbb{R}^K$，$\mathbf{F} \in \mathbb{N}^{\mathbb{R}^K}$ 满足 $K = \mathcal{C}(( [a,b]^d, \delta), (b-a) r )$，$\sup_{x \in [a,b]^d} [ \min_{k \in \{1, \dots, K\}_\mathbf{f}_k} \delta(x, \mathbf{f}_k) ] \le (b-a) r$，$\mathbf{v} = (f(\mathbf{f}_1), f(\mathbf{f}_2), \dots, f(\mathbf{f}_K))$，且

$\mathbf{F} = \mathbb{M}_{K} \bullet \mathbf{A}_{- L1_{K},\mathbf{v}} \bullet \mathbf{P}_{K} (\mathbb{I}_{d} \bullet \mathbf{A}_{\mathbf{l}_d - \mathbf{f}_1,\mathbb{I}_d} \bullet \mathbf{A}_{\mathbf{l}_d - \mathbf{f}_2, \dots, \mathbb{I}_d \bullet \mathbf{A}_{\mathbf{l}_d - \mathbf{f}_K} ) \bullet \mathbb{T}_{d,K} \qquad (4.95) $

（参见定义 1.3.1, 1.5.5, 2.1.1, 2.2.1, 2.3.1, 2.4.6, 3.3.4, 4.2.1, 4.2.5, 和 4.3.2）。则

(i) $\mathcal{T}(\mathbf{F}) = d$ 成立，

(ii) $\mathcal{O}(\mathbf{F}) = 1$ 成立，

(iii) $\mathcal{H}(\mathbf{F}) \le \lceil d \log_2 (\frac{3d}{4 r}) \rceil + 1$ 成立，

(iv) $\mathbb{D}_{1}(\mathbf{F}) \leq 2d \big( \frac{3d}{4r} \big)^{d}$ 成立，

(v) 对于所有 $i \in \{2, 3, 4, \ldots\}$，$\mathbb{D}_{i}(\mathbf{F}) \leq 3 \big[ \big( \frac{3d}{4r} \big)^{d} \frac{1}{2^{i-1}} \big] $ 成立，

(vi) $\mathcal{P}(\mathbf{F}) \leq 35 \big( \frac{3d}{4r} \big)^{2d} 2^{d}$ 成立，

(vii) $\| \mathcal{T}(\mathbf{F}) \|_{\infty} \leq \max \{ 1, L, |a|, |b|, 2 \| \sup_{x \in [a,b]} |f(x)| \} \}$ 成立，且

(viii) $\sup_{x \in [a,b]^{d}} | (\mathcal{R}_{r}^{\mathbf{N}}(\mathbf{F}))(x) - f(x) | \leq 2L(b-a)r$ 成立。

（参见定义 1.2.4, 1.3.4, 1.3.5, 和 4.2.6）。

**命题 4.3.6 的证明。** 注意，假设对于所有 $x, y \in [a, b]^{d}$ 都有 $|f(x) - f(y)| \leq L \|x - y\|_{1}$ 成立，这保证了 $L \geq 0$。接下来观察，(4.95)、引理 4.2.9 和命题 4.3.1 表明：

(I) $\mathcal{I}(\mathbf{F}) = d$ 成立，

(II) $\mathcal{O}(\mathbf{F}) = 1$ 成立，

(III) $\mathcal{H}(\mathbf{F}) = \lceil \log_{2}(K) \rceil + 1$ 成立，

(IV) $\mathbb{D}_{1}(\mathbf{F}) = 2dK$ 成立，

(V) 对于所有 $i \in \{2, 3, 4, \ldots\}$，$\mathbb{D}_{i}(\mathbf{F}) \leq 3 \big[ \frac{K}{2^{i-1}} \big]$ 成立，

(VI) $\| \mathcal{T}(\mathbf{F}) \|_{\infty} \leq \max \{ 1, L, \max_{k \in \{1, 2, \ldots, K\}} \| \mathbf{f}_{k} \|_{\infty}, 2 \| \max_{k \in \{1, 2, \ldots, K\}} |f(\mathbf{f}_{k})| \} \}$ 成立，且

(VII) $\sup_{x \in [a, b]^{d}} | (\mathcal{R}_{r}^{\mathbf{N}}(\mathbf{F}))(x) - f(x) | \leq 2L \big[ \sup_{x \in [a,b]^{d}} ( \min_{k \in \{1, \ldots, K\}} \delta(x, \mathbf{f}_{k}) ) \big]$ 成立

（参见定义 1.2.4, 1.3.4, 1.3.5, 和 4.2.6）。注意，条目 (I) 和 (II) 建立了条目 (i) 和 (ii)。接下来观察，引理 4.3.4 以及事实 $\frac{d}{2r} \geq 2$ 意味着：

$K = \mathcal{C}^{([a, b]^{d}, \delta), (b-a)r} \leq \bigg[ \frac{\lceil \frac{d(b-a)}{2(b-a)r} \rceil}{ } \bigg]^{d} = \big( \lceil \frac{d}{2r} \rceil \big)^{d} \leq \big( \frac{3}{2} \big( \frac{d}{2r} \big) \big)^{d} = \big( \frac{3d}{4r} \big)^{d}$.  (4.96)

将此与条目 (III) 结合，保证了：

$\mathcal{H}(\mathbf{F}) = \lceil \log_{2}(K) \rceil + 1 \leq \bigg[ \log_{2} \bigg( \big( \frac{3d}{4r} \big)^{d} \bigg) \bigg] + 1 = \big[ d \log_{2} \big( \frac{3d}{4r} \big) \big] + 1$.  (4.97)

这建立了条目 (iii)。此外，注意 (4.96) 和条目 (IV) 意味着：

$\mathbb{D}_{1}(\mathbf{F}) = 2dK \leq 2d \big( \frac{3d}{4r} \big)^{d}$.  (4.98)

这建立了条目 $(\mathbf{iv})$。另外，观察条目 $(\mathbf{V})$ 和 (4.96) 建立了条目 $(\mathbf{v})$。接下来注意，条目 $(\mathbf{III})$ 确保了对于所有 $i \in \mathbb{N} \cap (1, \mathcal{H}(\mathbf{F}))$ 都有：

$\frac{K}{2^{i-1}} \ge \frac{K}{2^{\mathcal{H}(\mathbf{F})-1}} = \frac{K}{2^{[\log_{2} K]}} \ge \frac{K}{2^{[\log_{2} K]+1}} = \frac{K}{2K} = \frac{1}{2}.$ (4.99)

因此，条目 $(\mathbf{V})$ 和 (4.96) 表明对于所有 $i \in \mathbb{N} \cap (1, \mathcal{H}(\mathbf{F}))$ 都有：

$\mathbb{D}_{i}(\mathbf{F}) \le \frac{K}{2^{i-1}} \le \frac{3K}{2^{i-1}} \le \left( \frac{3d}{4r} \right)^{d} \frac{3}{2^{i-2}}.$ (4.100)

此外，注意对于所有 $x \in [a, b]^{d}$ 都有 $\|x\|_{\infty} \le \max\{|a|, |b|\}$ 成立这一事实以及条目 $(\mathbf{VI})$ 意味着：

$\begin{aligned} \| \mathcal{T}(\mathbf{F}) \|_{\infty} \le & \max\{1, L, \max_{k \in \{1, \ldots, K\}} \|\mathbf{f}_{k}\|_{\infty}, 2[\max_{k \in \{1, \ldots, K\}} |f(\mathbf{f}_{k})|]\} \\ \le & \max\{1, L, |a|, |b|, 2[\sup_{x \in [a, b]^{d}} |f(x)|]\} . \end{aligned}$ (4.101)

这建立了条目 $(\mathbf{vii})$。此外，观察假设

$\sup_{x \in [a, b]^{d}} \left[ \min_{k \in \{1, \ldots, K\}} \delta(x, \mathbf{f}_{k}) \right] \le (b-a)r$ (4.102)

以及条目 $(\mathbf{VII})$ 证明了：

$\sup_{x \in [a, b]^{d}} |(\mathcal{R}_{r}^{\mathbf{N}}(\mathbf{F}))(x) - f(x)| \le 2L \left[ \sup_{x \in [a, b]^{d}} \left( \min_{k \in \{1, \ldots, K\}} \delta(x, \mathbf{f}_{k}) \right) \right] \le 2L(b-a)r.$ (4.103)

这建立了条目 $(\mathbf{viii})$。因此，剩下需要证明的是条目 $(\mathbf{vi})$。为此，注意条目 $(\mathbf{I})$ 和 $(\mathbf{II})$，以及 (4.98) 和 (4.100) 保证了：

$\begin{aligned} \mathcal{P}(\mathbf{F}) &= \sum_{i=1}^{\mathcal{L}(\mathbf{F})} \mathbb{D}_{i}(\mathbf{F})(\mathbb{D}_{i-1}(\mathbf{F})+1) \\ &\le 2d \left( \frac{3d}{4r} \right)^{d}(d+1) + \left( \frac{3d}{4r} \right)^{d} 3 \left( 2d \left( \frac{3d}{4r} \right)^{d}+1 \right) \\ &\quad + \left[ \sum_{i=3}^{\left[ \frac{\mathcal{L}(\mathbf{F})-1}{\mathcal{L}(\mathbf{F})-1} \right]} \left( \frac{3d}{4r} \right)^{d} \frac{3}{2^{i-2}} \left( \left( \frac{3d}{4r} \right)^{d} \frac{3}{2^{i-3}}+1 \right) + \left( \frac{3d}{4r} \right)^{d} \frac{3}{2^{\mathcal{L}(\mathbf{F})-3}}+1 \right] . \end{aligned}$ (4.104)

接下来注意，事实 $\frac{3d}{4r} \ge 3$ 确保了：

$\begin{aligned} & 2d \left( \frac{3d}{4r} \right)^{d}(d+1) + \left( \frac{3d}{4r} \right)^{d} 3 \left( 2d \left( \frac{3d}{4r} \right)^{d}+1 \right) + \left( \frac{3d}{4r} \right)^{d} \frac{3}{2^{\mathcal{L}(\mathbf{F})-3}}+1 \\ \le & \left( \frac{3d}{4r} \right)^{2d} \left( 2d(d+1) + 3(2d+1) + \frac{3}{2^{\mathcal{L}(\mathbf{F})-3}}+1 \right) \\ \le & \left( \frac{3d}{4r} \right)^{2d} d^{2}(4+9+12+1) = 26 \left( \frac{3d}{4r} \right)^{2d} d^{2}. \end{aligned}$ (4.105)

