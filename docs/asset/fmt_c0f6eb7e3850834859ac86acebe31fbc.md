
```
\\begin{array}{r} {\\mathcal{V}^{k} = \\left\\{ \\max\_{i} \\middle| h\_{k}^{i} - h \\middle| < \\gamma \\right\\},} \\\\ \\end{array}
```

(7.110)

以及事件 𝒱[1], ..., 𝒱[*m*] 的并集

```
\\begin{array}{r} {\\mathcal{V} = {\\underset{k = 1}{\\overset{n}{\\cup}}\\mathcal{V}^{k}}.} \\\\ \\end{array}
```

(7.111)

这里 *γ* 指定一个很小的正值。事件 𝒱 的概率下界将在下面建立。

取 *γ* = *h*²，写出

```
\\begin{array}{r} \\left. \\max\_{i} \\middle| v^{i} - v \\middle| \\leq h^{(m - 1)}\\gamma = h^{(m + 1)}. \\right. \\\\ \\end{array}
```

(7.112)

因此，由 (7.106–7.108) 不等式

```
\\begin{array}{r} \\left| {\\sum\\limits\_{i = 1}^{N}{(v\_{i} - v)}}\\phi(\\zeta^{i},\\mathbf{z}) \\middle| \\leq N\\left( \\frac{l}{N} \\right)^{n + 1}\\,\\exp(G). \\right. \\\\ \\end{array}
```

(7.113)

以事件 (7.111) 的概率成立。

### 2.

求事件 (7.111) 概率的下界。考虑差值 |*h*[*k*]^((*i*))−*h*| 并取一个足够小的正值 *γ* 使得 |*h*[*k*]^((*i*))−*h*|>*γ* 对随机格点 $\hat{\mathbb{S}}$ 的所有步长 *h*[*k*]^((*i*)) 都成立。计算该事件的概率。若随机点数很大（*h* 很小）且它们均匀分布，则这些点之间的距离必须接近 *h*。

事件 max[*i*]|*h*[*k*]^((*i*))−*h*|>*γ* 意味着可以找到一对随机变量 (*ξ*, *η*) ∈ \[0, 1\] 具有以下性质：如果其中一个（例如 *ξ*）取值为 *y* ∈ \[0, 1\]，则另一个 *η* ≠ ℒ = \[*y* + *h* − *γ*, *y* + *h* + *γ*\]。因此，以 *y* + *h* 为中心的区间 ℒ，其长度为 2*γ*，为空。实际上，假设随机变量 *η* 落入区间 ℒ，即 *η* = *ξ* − *h* ± *δ*，其中 0 < *δ* < *γ*；在这种情况下，可得 |*h*[*k*]^((*i*))−*h*|<*γ*。

由于均匀分布随机变量的独立性，事件 max[*i*]|*h*[*k*]^((*i*))−*h*|>*γ* 的概率对向量 **a** 的所有元素相同且不超过 \[1 − 2*γ* + *ψ*(*N*)\]^(*N*)，其中 *ψ*(*N*) 给出特定随机生成器的经验概率修正，通过实验得出。对标准随机生成器的分析表明，函数 *ψ*(*N*) 从 *N* = 1000 开始几乎消失。因此，

$$\begin{array}{r} \left. \widetilde{P}(\max_{i} \middle| h_{k}^{(i)} - h \middle| > \gamma) = \widetilde{P}(\mathcal{V}^{k}) = {(1 - 2\gamma)}^{N}. \right. \\ \end{array}$$

(7.114)

事件 𝒱 (7.111) 的概率具有形式

$$\begin{array}{r} {\widetilde{P}(\mathcal{V}) = \widetilde{P}(N,n) = {(1 - 2\gamma)}^{Nn}.} \\ \end{array}$$

(7.115)

相反事件 $\underset{k = 1}{\overset{m}{\cup}}\left. (\max_{i} \middle| h_{k}^{(i)} - h \middle| < \gamma) \right.$ 的概率构成

$$\begin{array}{r} {P(\mathcal{V}) = 1 - {(1 - 2\gamma)}^{Nn}.} \\ \end{array}$$

(7.116)

取 *γ* = *h*²，由 (7.116) 可知事件 (7.111) 的概率为

$$\begin{array}{r} {P(\mathcal{V}) > 1 - ({\lbrack - 2\left( \frac{l}{N} \right)^{2}\rbrack}^{Nn}) = P(N,n).} \\ \end{array}$$

(7.117)

因此，不等式 (7.113) 以不小于 *P*(*N*, *m*) 的概率成立。

### 3.

考虑 (7.3) 中的第二项。以下估计成立：

$$\begin{array}{r} \left. v\left. \sum\limits_{i = 1}^{N} \right|\phi(\zeta^{i},\mathbf{z}) - \phi(\mathbf{w}^{i},\mathbf{z}) \middle| \leq \left( \frac{1}{N} \right)^{n}\,\max_{(\zeta,\mathbf{w}) \in I^{n}} \middle| \phi(\zeta,\mathbf{z}) - \phi(\mathbf{w},\mathbf{z}) \middle| . \right. \\ \end{array}$$

(7.118)

求和号下的表达式定义了函数 *ϕ*(**w**, **z**) 的连续模；参见 \[61\]。由于该函数可微，

$$\begin{array}{r} \left. \max_{(\zeta,\mathbf{w}) \in I^{n}} \middle| \phi(\zeta,\mathbf{z}) - \phi(\mathbf{w},\mathbf{z}) \middle| \leq \max_{\mathbf{w} \in I^{n};\mspace{2mu} k \in \lbrack 1,n\rbrack} \middle| \frac{\partial\phi(\mathbf{w},\mathbf{z})}{\partial w_{k}} \middle| \,\max_{(\zeta,\mathbf{w}) \in I^{n}}\|\zeta - \mathbf{w}\|. \right. \\ \end{array}$$

(7.119)

任意随机点与其最近邻之间的距离不超过基本立方体的对角线，即

$$\begin{aligned} {\max_{(\zeta^{i},\mathbf{w}^{i}) \in I^{n};i \in \lbrack 1,N\rbrack}\|\zeta^{i} - \mathbf{w}^{i}\|} & {\leq \sqrt{\sum\limits_{k = 1}^{n}{(\zeta_{k}^{i} - w_{k}^{i})}^{2}} \leq \sqrt{n}\max_{k}\delta_{k}^{i},} \\ & {\delta_{k}^{i} = \zeta_{k}^{i} - w_{k}^{i}.} \\ \end{aligned}$$

(7.120)

取一个足够小的正值 *γ*。根据 (7.100) 以及 *ζ*^(*i*) 作为非均匀随机格点基本立方体中心点的定义，考虑不等式链

$$\begin{array}{r} {\max_{k}\delta_{k}^{i} < \max_{k}h_{k}^{i} < \gamma.} \\ \end{array}$$

(7.121)

令 *γ* = *h*²，其中 *h* 为均匀格点的步长。后一个不等式以概率 *P*(*N*) (7.117) 成立。

估计值

$$\begin{array}{r} {\frac{\partial\phi}{\partial w_{k}} = - E(\mathbf{w},\mathbf{z})\exp( - E(\mathbf{w},\mathbf{z}))\frac{\partial E}{\partial w_{k}},} \\ \end{array}$$

(7.122)

其中

$$\begin{array}{r} {\frac{\partial E}{\partial w_{k}} = {\sum\limits_{t = 1}^{T}{\sum\limits_{(n_{1},\ldots,n_{t}) = 1}^{n}A_{(n_{1},\ldots,n_{t})}}}(\mathbf{z}){\prod\limits_{r = 1,n_{r} \neq k}^{t}x_{n_{r}}}.} \\ \end{array}$$

(7.123)

利用 (7.106–7.108)，写出

$$\begin{array}{r} \left. \max_{\mathbf{w} \in I^{n}}\max_{k} \middle| \frac{\partial\phi}{\partial w_{k}} \middle| \leq G^{2}\exp(G). \right. \\ \end{array}$$

(7.124)

则估计式 (7.119) 取形式

$$\begin{array}{r} \left. \max_{(\zeta,\mathbf{w}) \in I^{n}} \middle| \phi(\zeta,\mathbf{z}) - \phi(\mathbf{w},\mathbf{z}) \middle| \leq \sqrt{m}\left( \frac{l}{N} \right)^{2 + n}G^{2}\exp(G) = \frac{n}{N}\sqrt{n}G^{2}\exp(G). \right. \\ \end{array}$$

(7.125)

将 (7.107) 和 (7.119) 代入 (7.3) 可知不等式

$$\begin{array}{r} \left| \mathbb{B}(\mathbf{z}) - \widetilde{\mathbb{B}}(\mathbf{z}) \middle| \leq N\exp(G)\left( \frac{l}{N} \right)^{m}\left\lbrack {1 + \sqrt{m}\left( \frac{l}{N} \right)^{2}G^{2}} \right\rbrack = \widetilde{\epsilon}(N,m) \right. \\ \end{array}$$

(7.126)

以不小于 *P*(*N*, *m*) (7.117) 的概率成立。

### 4.

现在转向不等式 (7.3)。它们在结构上与不等式 (7.3) 相似，唯一的区别在于函数 *φ*(**w**, **z**) (7.98)。因此，

$$\begin{array}{r} \left. \left. \sum\limits_{i = 1}^{N} \right|v^{i} - v \middle| \middle| \varphi(\zeta,\mathbf{z}) \middle| \leq \max_{\zeta \in I^{n}} \middle| \varphi(\zeta,\mathbf{z}) \middle| \left. \sum\limits_{i = 1}^{N} \right|v^{i} - v \middle| \leq N\left( \frac{l}{N} \right)^{n + 1}\max_{\zeta \in I^{n}} \middle| \varphi(\zeta,\mathbf{z}) \middle| . \right. \\ \end{array}$$

(7.127)

由函数 *φ*(**a**, **z**) (7.98) 的定义，

$$\begin{array}{r} \left. \max_{\zeta \in I^{n}} \middle| \varphi(\zeta,\mathbf{z}) \middle| \leq \max_{\mathbf{w} \in I^{n}} \middle| E(\mathbf{w},\mathbf{z}) \middle| \exp(E(\mathbf{w},\mathbf{z})) = G\exp(G), \right. \\ \end{array}$$

(7.128)

其中 *G* 由等式 (7.108) 给出。对于 (7.3) 中的第二项，估计式取形式

$$\begin{array}{r} \left. \max_{(\zeta,\mathbf{w})} \middle| \varphi(\zeta,\mathbf{z}) - \varphi(\mathbf{w},\mathbf{z}) \middle| \leq \max_{\mathbf{w} \in I^{n},\mspace{2mu} k \in \lbrack 1,n\rbrack}\, \middle| \frac{\partial\varphi}{\partial w_{k}} \middle| \max_{(\zeta,\mathbf{w}) \in I^{n}}\|\zeta - \mathbf{w}\|. \right. \\ \end{array}$$

(7.129)

根据函数 *φ*(**w**, **z**) (7.98) 的定义，还写出

$$\begin{array}{r} {\frac{\partial\varphi}{\partial w_{k}} = \frac{\partial E(\mathbf{w},\mathbf{z})}{\partial w_{k}}\exp( - E(\mathbf{w},\mathbf{z}))(1 - E^{2}(\mathbf{w},\mathbf{z})),} \\ \end{array}$$

(7.130)

由此得到估计

$$\begin{array}{r} \left. \max_{\mathbf{w} \in I^{n},\mspace{2mu} k \in \lbrack 1,n\rbrack}\, \middle| \frac{\partial\varphi}{\partial w_{k}} \middle| \leq G(1 + G^{2})\, \exp(G). \right. \\ \end{array}$$

(7.131)

因此，不等式

$$

\begin{array}{r}

\left| \mathbb{G}(\mathbf{z}) - \widetilde{\mathbb{G}}(\mathbf{z}) \middle| \leq N\left( \frac{l}{N} \right)^{n + 1}G\exp(G)\left\lbrack {1 + \frac{l}{N}(1 + G^{2})} \right\rbrack = \widetilde{\kappa}(N,n)

\right.

\\

\end{array}

$$

(7.132)

以不小于 *P*(*N*, *m*) (7.117) 的概率成立。

上界 *N*（或 *M*）的值可由条件计算得出

$$

\begin{array}{r}

{N^{\*} = \max(\widetilde{\epsilon}(N,n) = \delta;\,\, \widetilde{\kappa}(N,n) = \delta).}

\\

\end{array}

$$

(7.133)

## 7.4 具有 *p*-活动变量的乘性算法

RML 和 ML 程序中出现的许多问题都归结为非线性方程组，例如平衡方程 (7.9–7.12)。让我们说明一种求解此类方程的方法，这些方程与多面体上的熵最大化问题相关 [140]。

考虑一组等式，将其解释为数据 **q** ∈ *R*^(*r*) 与线性参数模型输出 **y** ∈ *R*^(*n*) 之间的平衡约束：

$$

\begin{array}{r}

{T\mathbf{y} = \mathbf{q},\quad(T,\mathbf{y}) \geq 0,\,\,\mathbf{q} \geq \varepsilon > 0,\text{\quad\quad}r < n.}

\\

\end{array}

$$

(7.134)

这里 *T* 表示秩为 *r* 的满秩矩阵。对于系统 (7.134)，存在解集，并且在其中存在唯一解，该解最大化熵

$$

\begin{array}{r}

{H(\mathbf{y}) = - {\sum\limits_{i = 1}^{n}y_{i}}\ln\frac{y_{i}}{ea_{i}},\text{\quad\quad}e = 2.71,}

\\

\end{array}

$$

(7.135)

其中 *a*[1], …, *a*[*n*] 作为参数起作用。

考虑熵 (7.135) 的以下约束优化问题：

$$

\begin{aligned}

& \left. H(\mathbf{y})\Rightarrow\max, \right.

\\

& {T\,\mathbf{y} = \mathbf{q}.}

\\

\end{aligned}

$$

(7.136)

相应的拉格朗日函数具有形式

$$

\begin{array}{r}

{L(\mathbf{y},\overline{\lambda}) = H(\mathbf{y}) + {\sum\limits_{k = 1}^{r}\lambda_{k}}\left( {q_{k} - {\sum\limits_{i = 1}^{n}t_{ki}}y_{i}} \right).}

\\

\end{array}

$$

(7.137)

一阶最优性条件为

$$

\begin{aligned}
