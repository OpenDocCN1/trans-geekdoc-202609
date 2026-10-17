
由于 `Φi = 1`，可得

$$
\begin{array}{r}
{1 = A(t_{i} - t_{0})(t_{i} - t_{1})\cdots(t_{i} - t_{i - 1})(t_{i} - t_{i + 1})\cdots(t_{i} - t_{n}).}
\\
\end{array}
$$

(2.54)

随后，

$$
\begin{array}{r}
{\Phi_{i}(t) = \frac{(t - t_{0})(t - t_{1})\cdots(t - t_{i - 1})(t - t_{i + 1})\cdots(t - t_{n})}{(t_{i} - t_{0})(t_{i} - t_{1})\cdots(t_{i} - t_{i - 1})(t_{i} - t_{i + 1})\cdots(t_{i} - t_{n})}.}
\\
\end{array}
$$

(2.55)

而拉格朗日插值多项式由下式给出

$$
\begin{aligned}
{\psi(t) = L_{n}(t)} & {= x(t_{0})\frac{(t - t_{1})\cdots(t - t_{n})}{(t_{0} - t_{1})\cdots(t_{0} - t_{n})} +}
\\
& {+ x(t_{1})\frac{(t - t_{0})(t - t_{2})\ldots(t - t_{n})}{(t_{1} - t_{0})(t_{1} - t_{2})\ldots(t_{1} - t_{n})} + \cdots +}
\\
& {+ x(t_{n})\frac{(t - t_{0})\ldots(t - t_{n - 1})}{(t_{n} - t_{0})(t_{n} - t_{1})\ldots(t_{n} - t_{n - 1})}.}
\\
\end{aligned}
$$

(2.56)

引入函数

$$
\begin{array}{r}
{\omega_{n}(t) = {\prod\limits_{i = 0}^{n}{(t - t_{i})}}}
\\
\end{array}
$$

(2.57)

并将拉格朗日插值多项式写为

$$
\begin{array}{r}
{L_{n}(t) = {\sum\limits_{i = 0}^{n}x}(t_{i})\frac{\omega_{n}(t)}{(t - t_{i})\omega_{n}^{\prime}(t_{i})}.}
\\
\end{array}
$$

(2.58)

在应用意义上，拉格朗日插值多项式有些不便，因为增加一个新节点需要形成一个新的多项式。这一缺点在牛顿表示的插值多项式中不存在。更具体地说，*牛顿插值多项式* 涉及如下的差商概念 [17]。

考虑 n + 1 个节点以及相同数量的函数 `x(t)` 的值，即 `x(t[0])`，…，`x(t[n])`。函数 `x(t)` 在节点 `t[i−1]`、`t[i]` 处的第一个差商为值

$$
\begin{array}{r}
{\Delta_{i - 1,i} = \frac{x(t_{i}) - x(t_{i - 1})}{t_{i} - t_{i - 1}}.}
\\
\end{array}
$$

(2.59)

高阶差商递归计算。m 阶差商的一般公式为

$$
\begin{array}{r}
{\Delta_{i - 1,i,i + 1,\ldots,i + m} = \frac{\Delta_{i,i + 1,\ldots,i + m} - \Delta_{i - 1,i,i + 1,\ldots,i + m - 1}}{t_{i + m} - t_{i}}.}
\\
\end{array}
$$

(2.60)

将拉格朗日插值多项式表示为

$$
\begin{array}{r}
{L_{n}(t) = L_{0}(t) + (L_{1}(t) - L_{0}(t)) + \ldots + (L_{n}(t) - L_{n - 1}(t)).}
\\
\end{array}
$$

(2.61)

显然，这就是恒等式 `Ln = Ln`。可以证明 [17]

$$
\begin{array}{r}
{L_{i}(t) - L_{i - 1}(t) = \Delta_{0,\ldots,i}\omega_{i}(t),}
\\
\end{array}
$$

(2.62)

其中 `ωi = (t−t[0])⋯(t−t[i])`。则拉格朗日插值多项式的牛顿表示 `Nn` 可写为

$$
\begin{aligned}
& {L_{n}(t) = N_{n}(t) = x(t_{0}) + \Delta_{0,1}(t - t_{1}) + \ldots +}
\\
& {\quad\quad + \Delta_{0,\ldots,n}(t - t_{0})(t - t_{1})\cdots(t - t_{n - 1}).}
\\
\end{aligned}
$$

(2.63)

再次指出，有兴趣的读者可从专著 [17] 中获得关于插值多项式的深入知识。

### 2.3.2 辅助动态模型

在本小节中，我们描述一种基于数据源数学模型的缺失数据（在时间尺度上）恢复方法。令 `𝒳[h]^(N) = {x[0],x[h],…,x[N h]}` 为绑定到步长为 `h` 的时间尺度上的数值数据包。利用这些数据，构造阶梯函数 `x̃(t)`，其形式为

$$
\begin{array}{r}
{\widetilde{x}(t) = x\lbrack ih\rbrack\quad\text{for~}ih \leq t < (i + 1)h,\quad i = \overline{0,N-1}.}
\\
\end{array}
$$

(2.64)

考虑一个以上述阶梯函数为输入、输出 `y(t)` 形式为的动态系统

$$
\begin{array}{r}
\left. y\lbrack nh\rbrack = \mathcal{L}(x\lbrack ih\rbrack,\mathbf{a}\, \middle| \, 0 \leq i < n). \right.
\\
\end{array}
$$

(2.65)

在该表达式中，ℒ 表示一个泛函，其表征了具有参数 **a** ∈ *R*^(*m*) 的系统的动态特性，其中 *m* 是参数向量的维数。参数 **a** 实际上会影响函数 *y*(*t*)，即 *y*(*t*, **a**)。对于向量 **a** 的元素取某些值时，系统在离散时刻 *ih* 输出数据包 𝒴[*h*]^(*N*) = {*y*\[0,**a**\],*y*\[*h*,**a**\],…,*y*\[(*N*−1)*h*,**a**\]}。

定义数据包 𝒳[*h*]^(*N*)、𝒴[*h*]^(*N*) 之间的总残差为

$$
\begin{array}{r}
{J(\mathbf{a}) = \sum\limits_{i = 0}^{N}{(x\lbrack ih\rbrack - y\lbrack ih,\mathbf{a}\rbrack)}^{2}.}
\\
\end{array}
$$

(2.66)

该残差的最小值给出最优参数，在该参数下，以上所述数据包在 *h*\-尺度的节点处的差异尽可能小（以泛函 *J* (2.66) 为准），即

$$
\begin{array}{r}
{\mathbf{a}^{\*} = \arg\min J(\mathbf{a}).}
\\
\end{array}
$$

(2.67)

将最优参数代入 (2.65) 得到数据包 𝒴[*s*]^(*N**r*) = {*y*^(\*)\[0\],*y*^(\*)\[*s*\],…,*y*^(\*)\[(*l*−1)*s*\],*y*^(\*)\[*h*\],*y*\[*h*+*s*\],…,*y*^(\*)\[*h*+(*l*−1)*s*\];*y*^(\*)\[2*h*\],*y*^(\*)\[2*h*+*s*\],…,*y*^(\*)\[*N**h*\]}，其中 *s* < *h*，*h*/*s* = *r* 且 *r* 为整数。

该方法将以具有脉冲响应 *w*(*t*, **a**)、*t* ≥ 0 的线性动态系统为例进行说明。设

$$
\begin{array}{r}
{w(t) = a_{1}\exp( - a_{2}t),}
\\
\end{array}
$$

(2.68)

其中 *a*[1]、*a*[2] 为区间型未知参数，即分别属于某些区间 0 < *a*[1] ≤ *a*[1]^+ 和 *a*[2]^− ≤ *a*[2] ≤ *a*[2]^+ 的参数。一般而言，这些区间的极限是未知的。求得它们的一种可能方法是在 *a*[1]^+、*a*[2]^− 和 *a*[2]^+ 上对 *J* (2.66) 进行全局最小化（或若全局最小值不存在则计算一个可接受的小值）。

向该系统的输入供给阶跃函数 *x̃*(*t*) 以产生输出

$$
\begin{array}{r}
{y(t) = a_{1}\int\limits_{0}^{t}\exp( - a_{2}(t - \tau))\widetilde{x}(\tau)d\tau.}
\\
\end{array}
$$

(2.69)

区间 \[0,*t*\] 包含整数个子区间 *N* = {*t*/*h*} 且 *t* = *N**h* + *μ*，其中 0 ≤ *μ* < (*N* + 1)*h*。于是表达式 (2.69) 可写为

$$
\begin{array}{r}
{y(t) = \frac{a_{1}}{a_{2}}\exp( - a_{2}t)\,\sum\limits_{i = 0}^{N}x\lbrack ih\rbrack\exp(a_{2}ih)\left( \exp(a_{2}h) - 1 \right).}
\\
\end{array}
$$

(2.70)

系统在 *h*\-尺度节点处的输出为

$$
\begin{array}{r}
{y\lbrack ih\rbrack = \frac{a_{1}}{a_{2}}\left( \exp(a_{2}h) - 1 \right)\exp( - a_{2}ih)\,\sum\limits_{j = 0}^{i}x\lbrack jh\rbrack\exp(a_{2}jh).}
\\
\end{array}
$$

(2.71)

因此，总残差泛函 (2.66) 的形式为

$$
\begin{array}{r}
\left. J(a_{1},a_{2}) = \sum\limits_{i = 0}^{N}\sum\limits_{j = 0}^{i}\left( {A_{i,j}(a_{1},a_{2})x\lbrack jh\rbrack} \right)^{2}\right\}\Rightarrow\min, \right.
\\
\end{array}
$$

(2.72)

其中

$$
\begin{array}{r}
{A_{i,j} = \left\{ \begin{aligned}
{\frac{a_{1}}{a_{2}}\left( \exp(a_{2}h) - 1 \right)\exp(a_{2}h(j - i))} & {\text{for}\, j < i,}
\\
{\frac{a_{1}}{a_{2}}\left( \exp(a_{2}h) - 1 \right) - 1} & {\text{~for}\, j = i.}
\\
\end{aligned}~ \right.}
\\
\end{array}
$$

(2.73)

注意，泛函 (2.72) 具有相当复杂的结构，不利于对其性质如唯一最小值、凸性（凹性）等进行解析研究。因此，在应用中应使用数值全局最小化方法来恢复（或与其它数据包同步）缺失数据。

一旦参数 *a*[1] 和 *a*[2] 计算出来，步长为 *s* 的缺失数据可由下式恢复

$$
\begin{aligned}
{y\lbrack ih + ks\rbrack} & {= \frac{a_{1}}{a_{2}}\exp( - a_{2}(ih + ks))\,\sum\limits_{i = 0}^{N}x\lbrack ih\rbrack\exp(a_{2}ih)\left( \exp(a_{2}h) - 1 \right),}
\\
i & {= \overline{0,N},\, k = \overline{0,M},\, M = \left\{ h/s \right\}.}
\\
\end{aligned}
$$

(2.74)

### 2.3.3 空间熵分解

如前所述，由政府统计部门形成的数据与一定的空间单元（区域）相关联，每个区域都有一组属性，即指标。此类区域的维度和这些指标的值信息之间往往相互关联。在许多情况下，研究的区域越小，其指标信息的可及性就越差。这导致了一个相当紧迫的“传播”问题，即利用关于后者的一些间接信息，将大区域的可用国家指标传播到其内部的小区。

考虑由 *I* 个区域组成的经济空间 𝔼。每个区域 *i* 包含 *M*[*i*] 个区，如 Fig. 2.8 所示。设区域 *i* 及其内部的区 (*i*, *j*) 由唯一的齐次指标 *S*[*i*] 和 *S*[*i**j*] 表征，分别。例如，可能的指标列表包括人口规模、生产密度、服务配备等。区域和区指标 *S*[*i*] 和 *S*[*i**j*] 满足平衡约束

$$
\begin{array}{r}
{S_{i} = \sum\limits_{j = 1}^{M_{i}}S_{ij},\text{\quad\quad}i = \overline{1,I}.}
\\
\end{array}
$$

(2.75)

![Figure 2.8](img/fig2_8.jpg)

Figure 2.8

每个区域因此每个区都生产 *r* 种类型的商品或处置 *r* 种类型的资源。假设对于每种商品（资源）类型 *k*，区域 *i* 的生产函数依赖于所有区域的状态指标，即 $\overset{\rightarrow}{S} = \left\{ S_{1},\ldots,S_{I} \right\}.$ 用 $Q_{ik}(\overset{\rightarrow}{S}),\, i = \overline{1,I},\, k = \overline{1,r}.$ 表示这些函数。同一假设也适用于区；用 *q**i**j**k* 表示其生产函数，其中 𝕊 = {*S*[11],…,*S*[1, *M*[1]];…;*S*[*I*, 1],…,*S*[*I*, *M*[*I*]]}。于是资源约束具有形式

$$
\begin{array}{r}
{\sum\limits_{j = 1}^{M_{i}}q_{ijk}(\mathbb{S}) = Q_{ik}(\mathbf{S}),\text{\quad\quad}i = \overline{1,I},\, k = \overline{1,r}.}
\\
\end{array}
$$

(2.76)

假设区域指标 **S** 已知而区指标 𝕊 未知。问题是求出区指标，同时考虑由 (2.75) 和 (2.76) 给出的平衡和资源约束。区指标的总数量为 $m = \sum\limits_{i = 1}^{I}M_{i},$ 因为按假设每个区和区域都有单一指标。此外，问题共包含 (*r* + 1)*I* 个平衡和资源约束，且 *m* > (*r* + 1)*I*。因此，满足等式 (2.75, 2.76) 的区指标集合众多。

获得唯一的区指标集合的一种方法源于熵最大化原理。事实上，熵是区域指标在相应区之间分布的不确定性度量 \[138\]，即

$$
\begin{array}{r}
{H(\mathbb{S}) = - \sum\limits_{i = 1,j = 1}^{I,M_{i}}S_{ij}\ln\frac{S_{ij}}{a_{ij}e},}
\\
\end{array}
$$

(2.77)

其中 𝕊 是表征区指标分布的矩阵，其元素为 *S*[*i**j*]。具有最高不确定性的分布 **S** 对应于在平衡和资源约束 (2.75, 2.76) 下熵 *H* 的最大值。关于感兴趣区域内各区的任何先验信息均可纳入熵函数 *H* 的参数 *a*[*i**j*] 中。

因此，区域指标在各区间的分布，称为*熵分解*，是优化问题的解

$$
\begin{array}{r}
\left. H(\mathbb{S})\Rightarrow\max,\quad\mathbb{S} \in D, \right.
\\
\end{array}
$$

(2.78)

其中

$$
\begin{array}{r}
{D = \left\{ S_{ij} \middle| \sum\limits_{j = 1}^{M_{i}}S_{ij} = S_{i};\,\sum\limits_{j = 1}^{M_{i}}q_{ijk}(\mathbb{S}) = Q_{ik}(S),\quad i = \overline{1,I},\, k = \overline{1,r} \right\}.}
\\
\end{array}
$$

(2.79)

在此一般表述中，所有区域和区都通过相应的生产函数相互关联。另一个极端情况是所有区域和区都是孤立的，即区域和区生产函数仅依赖于其自身区域或区的状态指标：
