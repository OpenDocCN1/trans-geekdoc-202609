
## 条件概率计算

| $\left. P\text{(Humidity} = \text{high} \middle| \text{play}\,\text{tennis} = \text{yes)} = \frac{3}{9} \right.$ | | $\left. P\text{(Humidity} = \text{high} \middle| \text{play}\,\text{tennis} = \text{no)} = \frac{4}{5} \right.$ |
|---|---|---|
| $\left. P\text{(Humidity} = \text{normal} \middle| \text{play}\,\text{tennis} = \text{yes)} = \frac{6}{9} \right.$ | | $\left. P(\text{Humidity} = \text{normal} \middle| \text{play}\,\text{tennis} = \text{no}) = \frac{1}{5} \right.$ |
| $\left. P(\text{Wind} = \text{weak} \middle| \text{play}\,\text{tennis} = \text{yes}) = \frac{6}{9} \right.$ | | $\left. P(\text{Wind} = \text{weak} \middle| \text{play}\,\text{tennis} = \text{no)} = \frac{2}{5} \right.$ |
| $\left. P(\text{Wind} = \text{strong} \middle| \text{play}\,\text{tennis} = \text{yes)} = \frac{3}{9} \right.$ | | $\left. P\text{(Wind} = \text{strong} \middle| \text{play}\,\text{tennis} = \text{no)} = \frac{3}{5} \right.$ |

现在，给定一个测试实例，每个属性都有可能取值，我们可以应用贝叶斯定理来确定给定的实例属于 `yes` 还是 `no` 类。

设测试实例为

`t = {Sky = sunny, Temp = cool, Humidity = high, wind = strong}`

我们需要确定这个测试实例是否允许玩家打网球。

`p(t) = max(p(t|yes), p(t|no))`

`P(sunny|yes) × P(cool|yes) × p(high|yes) × p(strong|yes) × p(yes)`

$\left. \Rightarrow\frac{2}{9} \times \frac{3}{9} \times \frac{3}{9} \times \frac{3}{9} \times \frac{9}{14} = 0.0053 \right.$

`P(sunny|no) × P(cool|no) × p(high|no) × p(strong|no) × p(no)`

$\left. \Rightarrow\frac{3}{5} \times \frac{1}{5} \times \frac{4}{5} \times \frac{3}{5} \times \frac{5}{14} = 0.0205 \right.$

对于给定的实例，`p(t|no) > p(t|yes)` 因此 `play tennis = no`

这种方法的最大缺点是它是一个耗时过程，如果假设空间非常大则不实用。虽然不实用，但它为比较其他概念学习算法的性能设定了标准。

为了进一步简化，我们在以下假设下进行公式化：

- 所有假设的概率相等，即 $P\left( h \right) = \frac{1}{\left| H \right|}\forall h \in H$
- 似然概率定义为 $P\left( {D\text{|}h} \right) = \left\{ \begin{matrix} {1,} & {\text{if}\, h\left( x_{i} \right) = c_{i}} \\ {0,} & \text{else} \\ \end{matrix} \right.$

如果 `h(x[i]) = c[i]` 则我们称该假设是一致的，否则它是不一致的。

基于假设，很明显对于所有不一致的假设，`P(h|D) = 0`。

对于一致的假设，按如下计算

$\left. P\left( {h\text{|}D} \right) = \frac{\text{Likelihood} \times \text{Prior}}{\text{Evidence}}\Rightarrow\frac{1 \times \frac{1}{\left| H \right|}}{P\left( D \right)} \right.$

证据按如下计算

$P\left( D \right) = \sum\limits_{h_{i} \in H}P\left( {D\text{|}h_{i}} \right)P\left( h_{i} \right)$

假设空间中的每个假设要么是一致的，要么是不一致的。

设 `H[1]` 表示所有一致假设的集合，`H[2]` 表示所有不一致假设的集合。设 `n[1]` 表示 `H[1]` 的基数，`n[2]` 表示 `H[2]` 的基数。则，

$P\left( D \right) = \sum\limits_{h_{i} \in H_{1}}P\left( {D\text{|}h_{i}} \right)P\left( h_{i} \right) + \sum\limits_{h_{i} \in H_{2}}P\left( {D\text{|}h_{i}} \right)P\left( h_{i} \right)$

$\left. \Rightarrow\sum\limits_{h_{i} \in H_{1}}1 \times \frac{1}{\left| H \right|} + \sum\limits_{h_{i} \in H_{2}}0 \times \frac{1}{\left| H \right|} \right.$

$\left. \Rightarrow\sum\limits_{h_{i} \in H_{1}}\frac{1}{\left| H \right|} \right.$

$\left. \Rightarrow\frac{n_{1}}{\left| H \right|} \right.$

因此，我们可以写出一致假设的后验概率为

$\left. P\left( {h\text{|}D} \right) = \frac{\text{Likelihood} \times \text{Prior}}{\text{Evidence}}\Rightarrow\frac{1 \times \frac{1}{\left| H \right|}}{P\left( D \right)}\Rightarrow\frac{1 \times \frac{1}{\left| H \right|}}{\frac{n_{1}}{\left| H \right|}}\Rightarrow\frac{1}{n_{1}} \right.$

## 8.5.4.1 Bayes’ Optimal Classifier

贝叶斯定理用于计算条件概率。同样的方法也用于确定最大后验概率（`MAP`）。出现的一个普遍问题是“最可能的假设是什么？”或“新实例最可能的分类是什么？”。为了解答这些问题，使用了贝叶斯最优分类器。

设训练集表示为 `D`，测试集表示为 `V`。设 `v[i] ∈ V` 为测试数据集 `V` 的一个实例。使用贝叶斯最优分类器对新实例 `v[i]` 的最优分类确定为

(8.12)

$\left. \begin{matrix} {\arg\max} \\ {v_{i} \in V} \\ \end{matrix}\sum\limits_{h_{j} \in H}P\left( v_{i} \middle| h_{j} \right)P(h_{j} \middle| D) \right.$

考虑三个假设 `h[1]`、`h[2]`、`h[3]`，其后验概率分别为 0.45、0.3 和 0.25，其中 `h[1]` 属于正类，而 `h[2]` 和 `h[3]` 属于负类。由于 `h[1]` 的后验概率较高，`h[MAP]` 一个新实例 `x` 被识别为 `x ∈ h[1]`。

`P(h[1]|D)=0.45`; `P(positive|h[1])=1`; `P(negative|h[1])=0`

`P(h[2]|D)=0.3`; `P(positive|h[2])=0`; `P(negative|h[2])=1`

`P(h[3]|D)=0.25`; `P(positive|h[3])=0`; `P(negative|h[3])=1`

$\left. \sum\limits_{h_{i} \in H}P\left( {\text{positive}\left| h_{i} \right.} \right)P(h_{i} \middle| D) = 0.45 \right.$

$\left. \sum\limits_{h_{i} \in H}P\left( {\text{negative}\left| h_{i} \right.} \right)P(h_{i} \middle| D) = 0.55 \right.$

然而，根据贝叶斯最优分类器，可以确定为

$\left. \begin{matrix} {\arg\max} \\ {v_{i} \in V} \\ \end{matrix}\sum\limits_{h_{j} \in H}P\left( v_{i} \middle| h_{j} \right)P(h_{j} \middle| D)\Rightarrow\begin{matrix} {\arg\max} \\ {v_{i} \in V} \\ \end{matrix}\left( {0.45,0.55} \right) = 0.55 \right.$

贝叶斯最优分类器表明新实例 `x` 属于负类。

## 8.5.4.2 贝叶斯信念网络

朴素贝叶斯分类器假设对于给定的目标值，所有变量或属性都是条件独立的，而贝叶斯信念网络允许对变量子集进行条件独立。贝叶斯信念网络或简称为贝叶斯网络提供了一组变量上的概率分布。

设 `X = (X[1], X[2], ..., X[n])` 表示一组随机变量，其中每个 `X[i] ∈ V(X[i])`。贝叶斯网络是一个有向无环图，它将 `X` 上的联合分布指定为每个节点上的条件分布的乘积。它表示为

(8.13)

$\left. P\left( {X_{1} = x_{1},X_{2} = x_{2},\cdots,X_{n} = x_{n}} \right) = \prod\limits_{i = 1}^{n}p(x_{i} \middle| \text{parents}\left( x_{i} \right)) \right.$

考虑一个简单的贝叶斯网络（Fig. 8.10）。

![](img/f8-10.jpg)

Figure 8.10 简单贝叶斯信念网络的示例

`P(A,B,C) = P(C|A,B)P(A)P(B)`

对于贝叶斯网络，存在两个组成部分——一个图形结构用于显示条件独立性假设，以及每个变量给定其父节点的概率值。有向边表示直接依赖。任意两个变量之间不存在边表示条件独立。

如果假设图仅有三个节点 `A`、`B` 和 `C` 且没有任何边，则表示所有变量 `A`、`B` 和 `C` 都是条件独立的。在这种情况下，边际独立性使用联合概率分布定义（概率的交叉乘积规则）为

`P(A,B,C) = P(A)P(B)P(C)`

考虑贝叶斯网络，其中 `B` 和 `C` 在给定 `A` 的条件下独立（Fig. 8.11）。

![](img/f8-11.jpg)

Figure 8.11 B 和 C 在给定 A 的条件下独立的贝叶斯网络

`P(A,B,C) = P(B|A)P(C|A)P(A)`

例如，`X` 在家中安装了报警器以检测其不在时发生的盗窃。报警器有时即使行人经过房屋也会响应。`Y` 和 `Z` 是 `X` 的邻居，他们向他保证当报警器响起时会打电话（Fig. 8.12）。

![](img/f8-12.jpg)

Figure 8.12 表示不同事件或状态的随机变量 T、PD、A、Y 和 Z

`P(T, PD, A, Y, Z) = P(Y|A)P(Z|A)P(A|T, PD)P(T)P(PD)`

给定条件独立性表为

`P(T = True) = 0.002 ⇒ P(T = False) = 0.998`

`P(PD = True) = 0.001 ⇒ P(PD = False) = 0.999`

### Table 8.16 Table with random variables T, PD, and P(A)

| T | PD | P(A = True) | P(A = False) |
|---|---|---|---|
| True | True | 0.94 | 0.06 |
| True | False | 0.95 | 0.05 |
| False | True | 0.69 | 0.31 |
| False | False | 0.001 | 0.999 |

### Table 8.17 Table with random variables Y and P(Y)

| A | P(Y = True) | P(Y = False) |
|---|---|---|
| True | 0.91 | 0.09 |
| False | 0.05 | 0.95 |

### Table 8.18 Table with random variables A and P(Z)

| A | P(Z = True) | P(Z = False) |
|---|---|---|
| True | 0.75 | 0.25 |
| False | 0.02 | 0.98 |

**问题陈述**：计算在无盗窃且无行人，但 `Y` 和 `Z` 给 `X` 打电话的情况下 `A` 的概率。

`P(Y, Z, A, ¬T, ¬PD) = P(Y|A)P(Z|A)P(A|¬T, ¬PD)P(¬T)P(¬PD)`

⇒ `P(Y, Z, A, ¬T, ¬PD) = 0.91 × 0.75 × 0.001 × 0.998 × 0.999 = 0.00068045`

因此，贝叶斯信念网络是一个表示联合分布的有向无环图。该网络中的推理或推理能够高效地计算适当的条件概率。

## 8.5.4.3 期望最大化算法

期望最大化（`EM`）和贝叶斯信念网络（`BBNs`）都是概率建模和统计推断领域中的两种强大框架。`EM` 是一种迭代方法，用于在统计模型依赖于未观测的潜在变量时寻找参数的最大似然或 `MAP` 估计。`BBNs` 另一方面是一种概率图模型，通过有向无环图表示一组变量及其条件依赖关系。`EM` 与 `BBNs` 之间的关系在于 `EM` 可用作在复杂 `BBNs` 中执行高效参数估计的计算方法，尤其是在处理不完整数据集时。

数据集包含两组变量，即观测变量和未观测变量。观测变量是直接测量的。未观测或隐藏变量是从观测变量推断出来的。隐藏变量也称为潜在变量。定义在同时具有观测变量和未观测变量的数据集上的模型称为潜在变量模型。

`EM` 算法可用于多种目的，如预测数据集中缺失值、寻找局部最大似然参数等。

### 步骤

**输入**：不完整数据

**步骤 1：初始化**：用初始值初始化所有参数。然后提供不完整数据。我们假设数据来自概率分布。

**步骤 2：期望**：基于观测数据猜测缺失数据的值。

**步骤 3：最大化**：将期望步骤中生成的数据补全以更新参数值。

**步骤 4：收敛检查**：如果值未收敛，则转到步骤 2 并重复直到收敛。

假设有两枚硬币，`C1` 和 `C2`。用 `C1` 抛硬币得到正面的概率为 `θ[1]`，用 `C2` 抛硬币得到正面的概率为 `θ[2]`。我们需要通过进行各种实验来找到 `θ[1]` 和 `θ[2]` 的值。

设每枚硬币抛 10 次，我们选择重复实验 5 次。每枚硬币在每次试验中的结果在 Table 8.19 中给出。

### Table 8.19 两个硬币（C1 和 C2）各抛掷 10 次的五次实验

| Experiment | Coin | Toss 1 | Toss 2 | Toss 3 | Toss 4 | Toss 5 | Toss 6 | Toss 7 | Toss 8 | Toss 9 | Toss 10 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Experiment – 1 | C1 | H | T | T | T | H | H | T | H | T | H |
| Experiment – 2 | C2 | H | H | H | H | T | H | H | H | H | H |
| Experiment – 3 | C1 | H | T | H | H | H | H | H | T | H | H |
| Experiment – 4 | C2 | H | T | H | T | T | T | H | H | T | T |
| Experiment – 5 | C1 | T | H | H | H | T | H | H | H | T | H |

$\theta_{1} = \frac{\text{Number of times head occurred using C1}}{\text{Total number of times C1 is tossed}}$

$\theta_{2} = \frac{\text{Number of times head occurred using C2}}{\text{Total number of times C2 is tossed}}$

### Table 8.20 两个硬币（C1 和 C2）各抛掷 10 次的五次实验（汇总视图）
