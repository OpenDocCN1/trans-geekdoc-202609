

is called *广义费米信息熵*。对于该函数，定义域为 *m* 维平行六面体 `𝒩` = [`0`, `G`]，即容许宏观态的集合。若参数 `a` 和 `G` 满足条件

$$
\begin{array}{r} {G_{k}a_{k} = \text{const},\text{\quad\quad}N_{k} \ll G_{k},} \\ \end{array}
$$

则 `H[F]`(`N`) 可变换为熵函数

$$
\begin{array}{r} {H_{B}(\mathbf{N}) = - {\sum\limits_{k = 1}^{m}N_{k}}\ln\frac{N_{k}}{a_{k}G_{k}e},} \\ \end{array}
$$

其被称为 *广义玻尔兹曼信息熵*。该函数定义在非负象限 `𝒩` ∈ *R*[+](*m*) 上，表示容许宏观态的集合。

不可区分粒子在状态空间子集上的随机分布消耗 *r* 种资源（能量、时间、财务等）。这些资源的可用数量为 `q[1]`, …, `q[r]`。资源消耗由消耗函数 `Φ[1](t, N)`, …, `Φ[r](t, N)` 刻画，其具有参数 `t`（特定消耗率）并依赖于宏观态向量 `N`。

由于分布过程需要资源，只能实现满足条件的宏观态

$$
\begin{array}{r} {\Phi_{i}(\mathbf{t},\mathbf{N}) = q_{i},\quad i = \overline{1,s};\text{\quad\quad}\Phi_{i + s}(\mathbf{t},\mathbf{N}) = q_{i + s},\quad i = \overline{1,r-s}.} \\ \end{array}
$$

这些约束定义了所谓的资源集 `𝒟`。该集合与容许宏观态的相应集合的交集给出 *容许集*

$$
\begin{array}{r} {\mathcal{F} = \mathcal{N}{\cap \mathcal{D}}.} \\ \end{array}
$$

利用上述概念和术语，我们可以表述 *广义变分原理* 如下。*在宏观系统中实现的宏观态对应于广义信息熵的约束最大值*，即

$$
\begin{array}{r} \left. H(\mathbf{N})\Rightarrow\max\text{~subject~to~}\,\, \mathbf{N} \in \mathcal{F}. \right. \\ \end{array}
$$

## 5.2 用于概率密度函数的熵鲁棒估计算法

PDF 的估计算法构成了随机化机器学习程序的核心。它们面向随机化参数模型的相应类，即 RPM-Orig 模型和 RPM-Rel 模型。两类随机化模型存在技术差异。首先，将考虑 RPM-Orig 模型的估计算法，包括一般问题陈述和所得解的结构。然后将这些估计算法适配到 RPM-Rel 模型。

### 5.2.1 RPM-Orig 模型的估计算法

根据 (5.4, 5.12)，在时刻 `t[j]` 时 RPM-Orig 模型的观测输出由下式描述

$$
\begin{aligned} {\mathbf{v}(t_{j}) = \mathbf{y}\lbrack t_{j}} & \left| \, P(\mathbf{a})\rbrack + {\overline{\xi}}^{(j)}\lbrack Q_{j}({\overline{\xi}}^{(j)})\rbrack, \right. \\ \left. \mathbf{y}\lbrack t_{j}\, \middle| \, P(\mathbf{a})\rbrack = \mathcal{B}\lbrack\mathbf{x} \right. & \left. ((t_{j},\tau_{l}),\, \middle| \, l = \overline{1,(j-1)}),\mathbf{a}\rbrack, \right. \\ & {j = \overline{1,s}.} \\ \end{aligned}
$$

(5.19)

这里，`ℬ` 表示维数为 (*m* × *n*) 的矩阵泛函，其表征模型输出 `y(t[j])` 与由输入向量 `x(t[j], τ[1])`, …, `x(t[j], τ[(j − 1)])` 组成的数组之间的现有关系。测量误差由噪声向量 `${\overline{\xi}}^{(j)}.$` 模拟。RPM-Orig 模型输出 (5.2.1) 依赖于具有 PDF `P(a)` 的随机化参数 `a`，也依赖于具有 PDF `$Q_{j}({\overline{\xi}}^{(j)});$` 的随机化噪声向量 `${\overline{\xi}}^{(j)}$`；见 (5.2.1)。关于这些 PDF 的可用先验信息（如有）以先验 PDF `P[0](a)` 和 `$Q_{j}^{0}({\overline{\xi}}^{(j)}).$` 的形式表示。假设 PDF 属于 `ℂ¹` 类，即所有连续可微函数类。

*对于 RPM-Orig 模型 (5.4)，其参数和测量噪声的 PDF 的熵鲁棒估计问题* 制定如下：

* 最大化广义玻尔兹曼信息熵泛函 [[149](#refbib.xhtml#r149)]

$$
\begin{aligned} {\mathcal{H}\lbrack P(\mathbf{a}),\overline{Q}(\xi)\rbrack =} & {- {\int_{\mathcal{A}}P}(\mathbf{a})\,\ln\frac{P(\mathbf{a})}{P_{0}(\mathbf{a})}\, d\,\mathbf{a} -} \\ {- {\sum\limits_{j = 1}^{s}\,}{\int_{\Xi_{j}}Q_{j}}({\overline{\xi}}^{(j)})} & \left. \ln\frac{Q_{j}({\overline{\xi}}^{(j)})}{Q_{j}^{0}({\overline{\xi}}^{(j)})}d{\overline{\xi}}^{(j)}\Rightarrow\min_{P,Q_{1},...,Q_{s}} \right. \\ \end{aligned}
$$

(5.20)

* 约束条件为：

  * –PDF 的归一化条件，即

$$
\begin{array}{r} {{\int_{\mathcal{A}}P}(\mathbf{a})d\mathbf{a} = 1,\quad{\int_{\Xi_{j}}Q_{j}}({\overline{\xi}}^{(j)})\,\ d{\overline{\xi}}^{(j)} = 1,\quad j = \overline{1,s},} \\ \end{array}
$$

(5.21)

和

  * –RPM-Orig 模型 (5.14) 输出的 *k*-均值与对象输出测量的平衡约束，即

$$
\begin{array}{r} {\mathbf{m}^{(k)}\lbrack P(\mathbf{a}),Q_{j}({\overline{\xi}}^{(j)}),j\rbrack = \mathbf{y}(t_{j}),\quad j = \overline{1,s}.} \\ \end{array}
$$

(5.22)

由于 (5.13)，这些等式约束中的向量 `$\mathbf{m}^{(k)}\lbrack P(\mathbf{a}),Q_{j}({\overline{\xi}}^{(j)}),j\rbrack$` 的分量为

$$
\begin{aligned} & {m_{i}^{(k)}\lbrack j\rbrack = \left\lbrack {\int_{\mathcal{A}}P}(\mathbf{a})y_{i}^{k}\lbrack t_{j}\, \middle| \, P(\mathbf{a})\rbrack\, d\mathbf{a} \right\rbrack^{1/k} +} \\ & {\text{\quad\quad} + \left\lbrack {{\int_{\Xi_{j}}\,}Q_{j}({\overline{\xi}}^{(j)})\,{\lbrack\xi_{i}^{(j)}\rbrack}^{k}\, d\xi_{i}^{(j)}} \right\rbrack^{1/k},} \\ & {\quad\text{\quad\quad}\text{\quad\quad}i = \overline{1,m},\, j = \overline{1,s}.} \\ \end{aligned}
$$

(5.23)

考虑平衡约束涉及 RPM-Orig 模型输出的 1-均值的情况：

$$
\begin{aligned} \left\lbrack {\int_{\mathcal{A}}P}(\mathbf{a})\mathbf{y}\lbrack t_{j}\, \middle| \, P(\mathbf{a})\rbrack\, d\mathbf{a} \right\rbrack & {+ \left\lbrack {{\int_{\Xi_{j}}\,}Q_{j}({\overline{\xi}}^{(j)})\,{\overline{\xi}}^{(j)}\, d{\overline{\xi}}^{(j)}} \right\rbrack = \mathbf{y}(t_{j}),} \\ & { \quad j = \overline{1,s}.} \\ \end{aligned}
$$

(5.24)

在此优化问题中，泛函约束从 `ℂ¹` 类中提取所有容许函数的子集 `$\Omega\lbrack P(\mathbf{a}),Q(\overline{\xi})\rbrack$`，其中 `$Q(\overline{\xi}) = \left\{ Q_{1}({\overline{\xi}}^{(1)}),\ldots,Q_{s}({\overline{\xi}}^{(s)}) \right\},$`。事实上，问题 (5.2.1)–(5.24) 是一个泛函熵-线性规划问题 [149]。它属于 Lyapunov 型优化问题类 [77, [174](#refbib.xhtml#r174)]，其中容许函数集由线性积分泛函系统描述。

*对于 RPM-Orig 模型，熵鲁棒 RML 算法* 的形式为

$$
\begin{array}{r} {\left\lbrack {P(\mathbf{a}),Q(\overline{\xi})} \right\rbrack^{\*} = \arg\max_{\lbrack P(\mathbf{a}),Q(\overline{\xi})\rbrack}\left\{ \mathcal{H},\, \middle| \,\lbrack\mathcal{P}(\mathbf{a}),\mathcal{Q}(\overline{\xi})\rbrack \in \Omega \right\},} \\ \end{array}
$$

(5.25)

