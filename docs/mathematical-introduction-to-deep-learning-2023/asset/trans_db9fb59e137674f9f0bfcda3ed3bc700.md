

# 4.3 多维函数的 ANN 逼近结果

## 4.3.1 构造性 ANN 逼近结果

**命题 4.3.1.** *设 $d, K \in \mathbb{N}$，$L \in [0, \infty)$，设 $E \subseteq \mathbb{R}^{d}$ 为一个集合，设 $\mathbf{f}_{1}, \mathbf{f}_{2}, \ldots, \mathbf{f}_{K} \in E$，设 $f: E \rightarrow \mathbb{R}$ 满足对所有 $x, y \in E$ 都有 $|f(x) - f(y)| \leq L \|x - y\|_{1}$，且设 $\mathbf{y} \in \mathbb{R}^{K}$，$\Phi \in \mathbb{N}$ 满足 $\boldsymbol{\eta} = (f(\mathbf{f}_{1}), f(\mathbf{f}_{2}), \ldots, f(\mathbf{f}_{K}))$ 以及*

$$\Phi = \mathbb{M}_{K} \bullet \mathbf{A}_{-L1K,n} \bullet \mathbf{P}_{K}\big(\mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{1}}, \mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{2}}, \ldots, \mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{K}}\big) \bullet \mathbb{T}_{d,K} \quad (4.77)$$

*(参见定义 1.3.1, 1.5.5, 2.1.1, 2.2.1, 2.3.1, 2.4.6, 3.3.4, 4.2.1, 和 4.2.5)。则*

$$\operatorname{sup}_{x \in E}|(\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(x) - f(x)| \leq 2L \big[\operatorname{sup}_{x \in E}(\min_{k \in \{1, \ldots, K\}} \|x - \mathbf{f}_{k}\|_{1})\big] \quad (4.78)$$

*(参见定义 1.2.4 和 1.3.4).*

*命题 4.3.1 的证明。在整个证明过程中，设 $F: \mathbb{R}^{d} \rightarrow \mathbb{R}$ 满足对所有 $x \in \mathbb{R}^{d}$ 都有*

$$F(x) = \max_{k \in \{1, \ldots, K\}}(f(\mathbf{f}_{k}) - L\|x - \mathbf{f}_{k}\|_{1}). \quad (4.79)$$

注意到推论 4.1.4、公式 (4.79) 以及假设条件“对所有 $x, y \in E$ 都有 $|f(x) - f(y)| \leq L\|x - y\|_{1}$”保证了

$$\operatorname{sup}_{x \in E}|F(x) - f(x)| \leq 2L \big[\operatorname{sup}_{x \in E}(\min_{k \in \{1, \ldots, K\}}\|x - \mathbf{f}_{k}\|_{1})\big]. \quad (4.80)$$

此外，请注意引理 4.2.9 确保了对所有 $x \in E$，都有 $F(x) = (\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(x)$。将此与 (4.80) 结合即证明了 (4.78)。命题 4.3.1 的证明至此完成。

*习题 4.3.1。证明或反驳以下陈述：存在 $\Phi \in \mathbb{N}$ 使得 $\mathcal{I}(\Phi) = 2$，$\mathcal{O}(\Phi) = 1$，$\mathcal{P}(\Phi) < 20$，并且*

$$\sup_{v = (x,y) \in [0,2]^{2}} \big| x^{2} + y^{2} - 2x - 2y + 2 - (\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(v) \big| \leq \frac{3}{8}. \quad (4.81)$$

## 4.3.2 覆盖数估计

**定义 4.3.2** (覆盖数)。*设 $(E, \delta)$ 为一个度量空间，设 $r \in [0, \infty)$。则我们用 $\mathcal{C}^{(E,\delta),r} \in \mathbb{N}_{0} \cup \{\infty\}$（我们用 $\mathcal{C}^{E,r} \in \mathbb{N}_{0} \cup \{\infty\}$）表示由下式给出的扩展实数*

$$\mathcal{C}^{(E,\delta),r} = \min \bigg( \big\{n \in \mathbb{N}_{0} \colon \big[\exists A \subseteq E \colon \big[(|A| \leq n) \land (\forall x \in E \colon \exists a \in A \colon \delta_{(a,x)} \leq r)\big]\big] \big\} \cup \{\infty\} \bigg) \quad (4.82)$$

*并称 $\mathcal{C}^{(E,\delta),r}$ 为 $(E, \delta)$ 的 $r$-覆盖数（称 $\mathcal{C}^{E,r}$ 为 $E$ 的 $r$-覆盖数）。*

**引理 4.3.3.** 设 $(E,\delta)$ 为一个度量空间，设 $r \in [0, \infty]$。则

$$\mathcal{C}_{(E,\delta), r} = \begin{cases} \emptyset & : X = \emptyset \\ \inf \left( \left\{ n \in \mathbb{N} : \left( \exists x_1, x_2, \dots, x_n \in E : \right. \left. E \subseteq \bigcup_{m=1}^n \{ v \in E : d(x_m, v) \leq r \} \right) \right\} \cup \{ \infty \} \right) & : X \neq \emptyset \end{cases} \tag{4.83}$$

(参见定义 4.3.2)。

*引理 4.3.3 的证明。在整个证明过程中，不失一般性，假设 $E \neq \emptyset$。注意到引理 12.2.4 确立了公式 (4.83)。引理 4.3.3 的证明至此完成。 $\Box$

*习题 4.3.2。证明或反驳以下陈述：对于每个度量空间 $(X, d)$，每个 $Y \subseteq X$，以及每个 $r \in [0, \infty]$，都有 $\mathcal{C}_{(Y, d|_{Y \times Y}), r} \leq \mathcal{C}_{(X, d), r}$。*

*习题 4.3.3。证明或反驳以下陈述：对于每个度量空间 $(E,\delta)$，都有 $\mathcal{C}_{(E,\delta), \infty} = 1$。*

*习题 4.3.4。证明或反驳以下陈述：对于每个度量空间 $(E,\delta)$ 和每个满足 $\mathcal{C}_{(E,\delta), r} < \infty$ 的 $r \in [0, \infty)$，都有 $E$ 是有界的。（注：当且仅当存在 $r \in [0, \infty)$ 使得对所有 $x, y \in E$ 都有 $\delta(x, y) \leq r$ 时，度量空间 $(E,\delta)$ 是有界的。）*

*习题 4.3.5。证明或反驳以下陈述：对于每个有界度量空间 $(E,\delta)$ 和每个 $r \in [0, \infty)$，都有 $\mathcal{C}_{(E,\delta), r} < \infty$。*

**引理 4.3.4.** 设 $d \in \mathbb{N}$，$a \in \mathbb{R}$，$b \in (a, \infty)$，$r \in (0, \infty)$，且对于每个 $p \in [1, \infty)$，设 $\delta_p : ([a, b]^d \times ([a, b]^d) \to [0, \infty)$ 满足对所有 $x, y \in [a, b]^d$ 都有 $\delta_p(x, y) = \| x - y \|_p$（参见定义 3.3.4）。则对于所有 $p \in [1, \infty)$，都有

$$\mathcal{C}_{([a,b]^d,\delta_p),r} \leq \left( \frac{d^{1/p}(b-a)}{2r} \right)^d \leq \begin{cases} 1 & : r \geq \frac{d^{1/p}(b-a)}{2} \\ \left( \frac{d(b-a)}{r} \right)^d & : r < \frac{d^{1/p}(b-a)}{2}. \end{cases} \tag{4.84}$$

(参见定义 4.2.6 和 4.3.2)。

*引理 4.3.4 的证明。在整个证明过程中，设 $(\mathfrak{N}_p)_{p \in [1, \infty)} \subseteq \mathbb{N}$ 满足对所有 $p \in [1, \infty)$ 都有*

$$\mathfrak{N}_p = \left\lceil \frac{d^{1/p}(b-a)}{2r} \right\rceil, \tag{4.85}$$

对于每个 $N \in \mathbb{N}$，$i \in \{ 1, 2, \dots, N \}$，设 $g_{N, i} \in [a, b]$ 由下式给出*

$$g_{N, i} = a + \frac{(i-1/2)(b-a)}{N} \tag{4.86}$$

*且对于每个 $p \in [1, \infty)$，设 $A_p \subseteq [a, b]^d$ 由下式给出*

$$A_p = \{g_{\mathfrak{N}_p,1}, g_{\mathfrak{N}_p,2}, \dots, g_{\mathfrak{N}_p,\mathfrak{N}_p}\}^d \tag{4.87}$$

*(参见定义 4.2.6)。注意到对于所有 $N \in \mathbb{N}$，$i \in \{1, 2, \dots, N\}$，$x \in [a + \frac{(i-1)(b-a)}{N}, g_{N,i}]$，都有*

$$|x - g_{N,i}| = a + \frac{(i-1/2)(b-a)}{N} - x \leq a + \frac{(i-1/2)(b-a)}{N} - \left(a + \frac{(i-1)(b-a)}{N}\right) = \frac{b-a}{2N}. \tag{4.88}$$

*此外，注意到对于所有 $N \in \mathbb{N}$，$i \in \{1, 2, \dots, N\}$，$x \in [g_{N,i}, a + \frac{i(b-a)}{N}]$，都有*

$$|x - g_{N,i}| = x - \left(a + \frac{(i-1/2)(b-a)}{N}\right) \leq a + \frac{i(b-a)}{N} - \left(a + \frac{(i-1/2)(b-a)}{N}\right) = \frac{b-a}{2N}. \tag{4.89}$$

*将此与 (4.88) 结合可知，对于所有 $N \in \mathbb{N}$，$i \in \{1, 2, \dots, N\}$，$x \in [a + \frac{(i-1)(b-a)}{N}, a + \frac{i(b-a)}{N}]$，都有 $|x - g_{N,i}| \leq \frac{(b-a)}{2N}$。这证明了对于每个 $N \in \mathbb{N}$，$x \in [a, b]$，存在 $y \in \{g_{N,1}, g_{N,2}, \dots, g_{N,N}\}$ 使得*

$$|x - y| \leq \frac{b-a}{2N}. \tag{4.90}$$

*这确立了对于每个 $p \in [1, \infty)$，$x = (x_1, x_2, \dots, x_d) \in [a, b]^d$，存在 $y = (y_1, y_2, \dots, y_d) \in A_p$ 使得*

$$\delta_p(x, y) = \|x - y\|_p = \left(\sum_{i=1}^d |x_i - y_i|^p\right)^{1/p} \leq \left(\sum_{i=1}^d \left(\frac{(b-a)}{2\mathfrak{N}_p}\right)^p\right)^{1/p} = \frac{d^{1/p}(b-a)}{2\mathfrak{N}_p} \leq \frac{d^{1/p}(b-a)2^r}{2d^{1/p}(b-a)} = r. \tag{4.91}$$

*将此与 (4.82)、(4.87)、(4.85) 以及事实“$\forall x \in [0, \infty) : [x] \leq \mathbb{1}_{(0,1]}(x) + 2x\mathbb{1}_{[1,\infty)}(x) = \mathbb{1}_{(0,r]}(rx) + 2rx\mathbb{1}_{(r,\infty)}(rx)$” 结合可知，对于所有 $p \in [1, \infty)$，都有*

$$\mathcal{C}^{([a,b]^d, \delta_p), r} \leq |A_p| = |\mathfrak{N}_p|^d = \left(\left[\frac{d^{1/p}(b-a)}{2r}\right]\right)^d \leq \left(\left[\frac{d(b-a)}{2r}\right]\right)^d$$

$$\begin{aligned} &\leq \left(\mathbb{1}_{(0,r]}\left(\frac{d(b-a)}{2}\right) + \frac{2d(b-a)}{2r}\mathbb{1}_{(r,\infty)}\left(\frac{d(b-a)}{2}\right)\right)^d \\ &= \mathbb{1}_{(0,r]}\left(\frac{d(b-a)}{2}\right) + \left(\frac{d(b-a)}{r}\right)^d \mathbb{1}_{(r,\infty)}\left(\frac{d(b-a)}{2}\right) \end{aligned}$$

*(参见定义 4.3.2)。引理 4.3.4 的证明至此完成。*

## 4.3.3 逼近误差的收敛速率

**引理 4.3.5.** 设 $d \in \mathbb{N}$，$L, a \in \mathbb{R}$，$b \in (a, \infty)$，设 $f: [a, b]^d \to \mathbb{R}$ 满足对所有 $x, y \in [a, b]^d$ 都有 $|f(x) - f(y)| \leq L \|x - y\|_1$，且设 $\mathbf{F} = \mathbf{A}_{0, f([a+b)/2, (a+b)/2]^{\times d}} \in \mathbb{R}^{1 \times d} \times \mathbb{R}^1$（参见定义 2.3.1 和 3.3.4）。则

(i) 成立 $\mathcal{I}(\mathbf{F}) = d$，

