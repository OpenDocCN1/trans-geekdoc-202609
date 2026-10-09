

$(q^n - 1)(q^{n} - q) \cdot \cdot (q^n - q^{m-1})$ 种可能的选择。然而，一个确定的 $m$ 维子空间可以拥有不同的基。

根据上述推理，我们可以看到，一个 $m$ 维子空间拥有 $(q^{n} - 1)(q^{n} - q) \cdot \cdot (q^{n} - q^{m-1})$ 组不同的基。

因此，$\mathbb{F}_{q}^{n}$ 中 $m$ 维子空间的数目等于
$$\frac{(q^{n} - 1)(q^{n} - q) \cdot \cdot (q^{n} - q^{m-1})}{(q^{m} - 1)(q^{m} - q) \cdot \cdot (q^{m} - q^{m-1})} = \frac{(q^{n} - 1)(q^{n-1} - 1) \cdot \cdot (q^{n-(m-1)} - 1)}{(q^{m} - 1)(q^{m-1} - 1) \cdot \cdot (q - 1)} \text{ .}$$
已证明，$m$ 维子空间的数目等同于能够生成的 $m$ 个轨道的数目（即所使用的算子数目）。在学习过程中，为了区分每个子空间，它们被标记为特定的实数值。

**定义 2.15.** 设 $m$ 和 $n$ 为非负整数。引入记号
$$\left[\begin{array}{c}n\\m\end{array}\right]_{q} = \frac{(q^{n} - 1)(q^{n-1} - 1) \cdot \cdot (q^{n-(m-1)} - 1)}{(q^{m} - 1)(q^{m-1} - 1) \cdot \cdot (q - 1)} \text{, 若 } m > 0 \text{ ,}$$
以及
$$\left[\begin{array}{c}n\\0\end{array}\right]_{q} = 1$$
称它们为高斯系数。

**推论 2.1.** *对于非负整数* $k$，*存在* $\boldsymbol{R}$ *中的一个元素* $a_{k}$ *与之对应，它定义了非负整数集* $\mathbf{R}_{0} = \boldsymbol{R} \cup \{0\}$ *上的一个函数* $a$，*即*
$$\pmb{a} \colon \mathbb{N}_{0} \rightarrow \pmb{R},\ k \mapsto a_{k}$$
*对于非负整数* $n$，*令*
$$b_{n} = \sum_{k=0}^{n} \left[\begin{array}{c}n\\k\end{array}\right]_{q} a_{k} \text{ .} \tag{2.6}$$
*那么，*
$$a_{n} = \sum_{k=0}^{n} (-1)^{n-k} q^{\left(\begin{array}{c}n-k\\2\end{array}\right)} \left[\begin{array}{c}n\\k\end{array}\right]_{q} b_{k} \tag{2.7}$$
*反过来，假设* $b$ *是一个定义在* $\mathbb{N}_{0}$ *上且值域为* $\boldsymbol{R}$ *的函数：*
$$\pmb{b} \colon \mathbb{N}_{0} \rightarrow \pmb{R},\ k \mapsto b_{k}$$
*对于任意非负整数* $n$，*由 (2.7) 定义* $a_{n}$，*(2.6) 成立。*
*证明。* 设 $V$ 为 $\mathbb{F}_{q}$ 上的无穷维向量空间。对于 $V$ 的任意 $n$ 维子空间 $W$，定义 $\boldsymbol{R}$ 中的元素 $a_{n}$ 与之对应。这定义了一个定义在 $\mathrm{Lf}(V)$ 上且值域为 $\boldsymbol{R}$ 的函数。
$$\pmb{a} \colon \mathrm{Lf}\ (V) \rightarrow \pmb{R},\ \ W \mapsto \pmb{a}(W) = \pmb{a}_{d i m \ W}$$

对于任意 $W \in \mathrm{L}_{f}(V)$，设 $\dim W=n$。设 $U$ 为 $W$ 的子空间，并规定

$b(W)=\sum_{U \subseteq W} a(U)$

显然，若 $\dim W=\dim W'$，则 $b(W)=b(W')$。令 $b_{\dim W}=b(W)$。由于 $W$ 中 $k$ 维子空间的数目为 $\left[\begin{array}{l}n \\k\end{array}\right]_{q}$，则 (2.8) 等价于 (2.6)。

由 (2.8) 并根据命题 2.2，

$a(W)=\sum_{U \subseteq W} b(U) \mu(U, W)$

根据定义，$a(W)=a_{\dim W}$，$b(U)=b_{\dim U}$。当 $\dim W=n$，$\dim U=k$ 时，我们有 $\mu(U, W)=(-1)^{n-k} q^{\binom{n-k}{2}}$。因此，可以从 (2.9) 推导出 (2.7)。

相反，根据

$b: \operatorname{L}_{f}(V) \rightarrow R$，$W \mapsto b(W)=b_{\dim W}$，

定义一个定义在 $\mathrm{L}_{f}(V)$ 上且值域为 $R$ 的函数 $b$。对于任意 $W \in \mathrm{L}_{f}(V)$，通过 (2.9) 定义 $a(W)$，其中 $U$ 是 $W$ 的子空间。当 $\dim W=\dim W'$ 时，我们有 $a(W)=a(W')$。设 $\dim W=n$，$\dim U=k, 0 \leq k \leq n$。则 (2.9) 等价于 (2.7)，并根据命题 2.2，可以从 (2.9) 推导出 (2.8)，进而从 (2.8) 推导出 (2.6)。

**命题 2.4.** *设 $x$ 为未定元，$n$ 为非负整数。则，*

$\prod_{i=0}^{n-1}\left(x-q^{i}\right)=\sum_{m=0}^{n}(-1)^{n-m} q^{\binom{n-m}{2}}\left[\begin{array}{l}n \\m\end{array}\right]_{q} x^{m}$

**定义 2.16.** 设 $q$ 为素数幂，$n$ 为非负整数，$x$ 为不定元。多项式

$g_{n}(x)=(x-1)(x-q) \cdots(x-q^{n-1})$，若 $n \geq 1$，

以及

$g_{0}(x)=1$

称为高斯多项式。那么，

$g_{n}(x)=\sum_{m=0}^{n}(-1)^{n-m} q^{\binom{n-m}{2}}\left[\begin{array}{l}n \\m\end{array}\right]_{q} x^{m}$

基于高斯求反公式。

**命题 2.5.** 设 $q$ 为素数幂，$n$ 为非负整数，$x$ 为未定元。则，
$$x^{n}=\sum_{k=0}^{n}\left[\begin{array}{c} n \\ k \end{array}\right]_{q} g_{k}(x) .$$

**定义 2.17.** 设 $P$ 为一个包含最小元素 $0$ 的偏序集，且对于 $a \in P$，若 $l(0, a)$ 存在，即从 $0$ 到 $a$ 的链可以细化为一条极大链。若包含 $a$ 的极大链具有相同的有限长度，则称其为 $a$ 的秩，记为 $r(a)$。若任意 $x \in P$ 都有秩 $r(x)$，则称 $P$ 具有秩函数 $r: P \rightarrow \mathbb{N}_{0}$，其中 $\mathbb{N}_{0}$ 是所有非负整数的集合。我们有时说 $P$ 由 $r$ 赋予秩。

容易理解，包含若干样本的集合 $P$ 可以根据对偶假设用对偶性来表示，其中每个待学习的实例可以用特定值来表示。在这里，秩函数也可以被视为轨道极限的最大可能长度，轨道长度 $\leq r(x)$。

**命题 2.6.** 设 $P$ 为一个包含最小元素 $0$ 的偏序集，并假设对于任意 $a, b \in P$ 且 $a < b$，从 $a$ 到 $b$ 的链可以细化为一条极大链。若 $P$ 满足 ID 条件，则 $P$ 上存在秩函数 $r: P \rightarrow \mathbb{N}_{0}$。那么，(1) $r(0) = 0$，(2) 若 $a < b$，则 $r(b) = r(a) + 1$。反过来，若存在定义在 $P$ 上且值域为 $\mathbb{N}_{0}$ 的函数 $r$，且满足 (1)，(2)，则 $P$ 满足 ID 条件，且 $r$ 是 $P$ 上的秩函数。

**证明。** 假设 $P$ 满足 ID 条件。对于任意 $a \in P$，由于从 $0$ 到 $a$ 的链可以细化为极大链，且它们的长度相等；因此，$l(0, a)$ 必须存在。根据定义 2.17，$r(a) = l(0, a)$，且 $r: P \rightarrow \mathbb{N}_{0}$ 是 $P$ 上的秩函数。显然，(1) 成立。设 $a < b$。假设 $r(a) = n$ 且
$$0 < a_{1} < a_{2} < \cdots < a_{n} = a$$
是 $0, a$ 的极大链。那么，
$$0 < a_{1} < a_{2} < \cdots < a_{n} < b$$
是 $0, b$ 的极大链，$r(b) = n + 1 = r(a) + 1$，即 (2) 成立。

现在，设 $r: P \rightarrow \mathbb{N}_{0}$ 为满足 (1)，(2) 的函数。设 $a, b \in P$ 且 $a < b$。假设
$$a = a_{0} < a_{1} < a_{2} < \cdots < a_{n} = b,$$
$$a = a_{0}^{l} < a_{1}^{l} < a_{2}^{l} < \cdots < a_{m}^{l} < b$$
是两条 $a, b$ 的极大链。根据 (2)，
$$r(b) = r(a_{n}) = r(a_{n-1}) + 1 = \cdots = r(a_{0}) + n = r(a) + n,$$
$$r(b) = r(a_{m}^{l}) = r(a_{m-1}^{l}) + 1 = \cdots = r(a_{0}^{l}) + m = r(a) + m.$$

因此，$n=m$。这证明了 $P$ 满足 JD 条件。$P$ 的秩函数记为 $r'$。对于任意 $a \in P$，设
$0 < a_1 < a_2 < \cdots < a_n = a$
为 $0, a$ 的极大链。根据定义 2.17，$r'(a)=n$。由于 $r$ 满足 (1) 和 (2)，
$r(a) = r(a_n) = r(a_{n-1}) + 1 = \cdots = r(0) + n = n$
那么，$r=r'$，即 $r$ 是 $P$ 的秩函数。

样本数据集 $P$ 以矩阵形式表示。秩函数的计算，即计算对学习有用样本的数目，或在给定原始样本集经过某种映射变换后的数目，即新样本集 $P'$ 的成员数目，可以被获得。$\square$

**定义 2.18.** 设 $P$ 为一个具有最小元素 $0$ 和最大元素 $1$ 的有限偏序集，且设 $P$ 具有秩函数 $r$。那么，
$X(P, x) = \sum_{a \in P} \mu(0, a) x^{r(1) - r(a)} \qquad (2.11)$
称为 $P$ 上的特征多项式。

注：在此，特征多项式可以被理解为学习子空间中样本的多项式表示。

**命题 2.7.** 设 $V$ 为域 $\mathbb{F}_q$ 上的 $n$ 维向量空间。设 $L(V)$ 为 $V$ 中所有子空间的集合。对于 $U$，$W \in L(V)$，若 $U \supset W$，规定 $U \geq W$。那么，对于给定的偏序关系 $\geq$，我们有
$X(L(V), x) = \prod_{i=0}^{n-1} (x - q^i) = g_n(x) .$

### 2.1.5 LML 中的格

如第 1.1 节所述，学习子空间（具体学习问题）可以描述为包含若干节点的有向图或树。它是一种格结构，具有从初始状态到目标状态的路径（从根节点开始到叶节点的树分支）。路径上的节点关系不能任意交换。它体现在具体问题中，可以理解为节点中待学习的样本（分类），其中指定的算子是最优的，即有利于获得最优轨道。为了有效生成目标轨道，引入格（网格）的思想如下。

**定义 2.19.** 若 $L$ 中任意两个元素都有上界和下界，则 LML 中的样本数据按格排序。元素 $a$ 和

