

*   求数据在第一主成分上的投影及其方差；
*   若方差较大，则寻找与第一主成分正交的最大变化新主方向，如此继续。

该过程允许将初始数据矩阵 `X` 的维度为 (*s* × *m*) 替换为两个矩阵 `T` 和 `P`，其维度分别为 (*s* × *k*) 和 (*k* × *s*)，其中 *k* < *m*。该表示使用新的变量得到

$$
\begin{array}{r} {{\overset{\rightarrow}{t}}^{\mspace{2mu}(j)} = {\overset{\rightarrow}{p}}^{\mspace{2mu}(j,1)}{\overset{\rightarrow}{x}}^{(1)} + \cdots + {\overset{\rightarrow}{p}}^{\mspace{2mu}(j,m)}{\overset{\rightarrow}{x}}^{(m)},\quad j = \overline{1,k},} \\ \end{array}
$$

(3.10)

其中 ${\overset{\rightarrow}{t}}^{\mspace{2mu}(j)}$ 和 ${\overset{\rightarrow}{p}}^{\mspace{2mu}(j,i)},\ i = \overline{1,m},$ 分别表示矩阵 `T` 和 `P` 的列。新的变量 (3.10) 称为 *主成分*，矩阵 `T` 称为主成分矩阵。主成分的一个重要性质在于其正交性。因此，随着主成分数量的增加，矩阵 `T` 不会被重新配置。

利用这些变量，矩阵 `X` 可以写成

$$
\begin{array}{r} {X = \hat{X} + E = {\sum\limits_{j = 1}^{k}{\overset{\rightarrow}{t}}^{(j)}}{\lbrack{\overset{\rightarrow}{p}}^{(j)}\rbrack}^{\prime} + E,\quad\quad\hat{X} = T\, P^{\prime}.} \\ \end{array}
$$

(3.11)

这里 `E` 表示维度为 (*s* × *m*) 的残差矩阵。残差误差通过残差矩阵的某种数值特征来评估，例如相对方差

$$
\begin{array}{r} {D = 1 - \frac{\sum\limits_{j = 1}^{s}{\sum\limits_{i = 1}^{m}e_{ji}^{2}}}{\sum\limits_{j = 1}^{s}{\sum\limits_{i = 1}^{m}x_{ji}^{2}}},\quad e_{ji} = x_{ji} - {\hat{x}}_{ji}.} \\ \end{array}
$$

(3.12)

存在许多用于计算主成分的递归算法，它们针对初始信息的具体情况而设计，并采用不同的数据处理方法。首先，对矩阵 `X` 进行中心化，即对每一列计算平均值

$$
\begin{array}{r} {{\overline{x}}_{j} = \frac{1}{s}{\sum\limits_{i = 1}^{m}x_{i}^{(j)}}} \\ \end{array}
$$

(3.13)

和标准差

$$
\begin{array}{r} {\sigma_{j} = \frac{1}{s}\sqrt{\sum\limits_{i = 1}^{m}{(x_{ji} - {\overline{x}}_{j})}^{2}}.} \\ \end{array}
$$

(3.14)

用于计算主成分的修正数据矩阵 `X̃` 由元素构成

$$
\begin{array}{r} {{\widetilde{x}}_{ij} = \frac{x_{ij} - {\overline{x}}_{j}}{\sigma_{j}}.} \\ \end{array}
$$

(3.15)

寻找主成分的算法包括以下步骤。

1. 选择初始向量 $\overset{\rightarrow}{t}$ (3.10)。
2. 计算 ${\overset{\rightarrow}{p}}^{\mspace{2mu}\prime} = \frac{{\overset{\rightarrow}{t}}^{\mspace{2mu}\prime}E_{j}}{{\overset{\rightarrow}{t}}^{\prime}\overset{\rightarrow}{t}}.$
3. 计算 $\overset{\rightarrow}{p} = \frac{\overset{\rightarrow}{p}}{{({\overset{\rightarrow}{p}}^{\prime}\overset{\rightarrow}{p})}^{1/2}}.$
4. 计算 $\overset{\rightarrow}{t} = \frac{E_{j}\overset{\rightarrow}{p}}{{\overset{\rightarrow}{p}}^{\prime}\overset{\rightarrow}{p}}.$
5. 利用 (3.12) 求 `D` 并返回步骤 2。

主成分的数量通过将相对方差 (3.12) 与允许误差进行比较来确定。

如前所述，矩形矩阵的奇异分解 (3.2) 与主成分分析相关联。这种关系的形式为

$$
\begin{array}{r} {T = US,\quad P = V.} \\ \end{array}
$$

(3.16)

主成分分析及其改进在大量文献中被讨论，主要应用于分类和回归问题 \[188\]。

### 3.1.3 随机投影方法

与主成分分析类似，通过随机投影进行降维涉及一个线性变换 `f`:ℝ^(*n*)→ℝ^(*k*) 对数据矩阵进行变换，并应用于对象由多维欧几里得空间中的点表示的问题 \[[20](#refbib.xhtml#r20)\]。

随机投影方法的思想基于 Johnson–Lindenstrauss 引理 \[[83](#refbib.xhtml#r83)\]：对于高维多维空间中的点集 `X`，存在一个维度较小但仍相当高的子空间，使得投影到该子空间上能够在平均意义上保持所有点之间的相对距离。变换的误差由值 `ε` ∈ (0, 1) 描述：

$$
\begin{array}{r} {\left( {1 - \varepsilon} \right)\left\| {x_{1} - x_{2}} \right\|^{2} \leq \left\| {f(x_{1}) - f(x_{2})} \right\|^{2} \leq \left( {1 + \varepsilon} \right)\left\| {x_{1} - x_{2}} \right\|^{2}} \\ \end{array}
$$

(3.17)

对所有向量 `x[1]`、 `x[2]` ∈ `X` 成立。

此外，原引理还给出了 `k` 的下界，即对象被投影到的子空间的维度。例如，对于 `N` 个点的集合，值 `k` 必须满足条件

$$
\begin{array}{r} {k > \frac{8\ln N}{\varepsilon^{2}}.} \\ \end{array}
$$

(3.18)

换句话说，投影子空间的最小可能维度不依赖于原始空间的维度，而仅取决于被投影对象的数量和变换误差。在各种特殊情况下，`k` 值的下界在 \[[82](#refbib.xhtml#r82), [86](#refbib.xhtml#r86)\] 中得到了改进。

考虑用于将对象从集合 `X` 投影的线性变换 `f`:ℝ^(*n*)→ℝ^(*k*)。它由维度为 [*k* × *n*] 的矩形矩阵 `R` (*k* <  < *n*) 定义，形式为

$$
\begin{array}{r} {X_{k \times N}^{RP} = R_{k \times n}X_{n \times N}.} \\ \end{array}
$$

(3.19)

事实证明，这种变换的矩阵 `R` 的元素可以由随机变量组成，这使得投影是随机的。在早期关于随机投影方法的著作 \[[30](#refbib.xhtml#r30), [76](#refbib.xhtml#r76), [108](#refbib.xhtml#r108)\] 中，建议使用标准高斯分布 `N(0, 1)` 的随机变量，并构造矩阵 `R` 使其行向量正交且长度为单位。

后来在 \[[8](#refbib.xhtml#r8)\] 中证明，矩阵 `R` 可以使用均匀分布获得，在由数据库中信息存储和整数计算决定的某些约束下。在这种情况下，建议由随机元素 `r[i j]` 组成矩阵 `R`，其形式为

$$
\begin{array}{r} {r_{ij} = \sqrt{3} \times \left\{ \begin{aligned} {+ 1} & {\text{with~probability~}\frac{1}{6},} \\ 0 & {\text{with~probability~}\frac{2}{3},} \\ {- 1} & {\text{with~probability~}\frac{1}{6}.} \\ \end{aligned}~ \right.} \\ \end{array}
$$

(3.20)

因此，为了计算投影 `X^(RP)`，需要将矩阵 `R` 和 `X` 相乘，该变换的复杂度为 𝒪(`k n N`)。在主成分分析中，投影矩阵是维度为 [*n* × *n*] 的方阵，投影变换的复杂度为 𝒪(`n² N`)。因此，就计算效率而言，对于降维，随机投影方法优于主成分分析。

