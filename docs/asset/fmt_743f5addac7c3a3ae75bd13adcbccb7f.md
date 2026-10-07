
`exec index from select (update alphaHol: alpha/(count[pArray]+1-i)) from pArray where pIndividual<=alphaHol);`

让我们对 $\alpha_{family} = 0.05$ 且 $m$ 从 1 到 100 的情况进行数值化说明。图 12.6 描述了族性错误率 $\alpha_{family}$ 随单个错误率 $\alpha_{individual}$（后者为常数）变化的依赖关系。随着族规模的增大，族性错误率不断增加并趋于 1.0。对于规模为 100 的族，至少有一个测试失败的概率为 0.9940795，这是一个非常接近 1.0 的值。该图的数据生成如下：

```
aIndividual:0;
[familySize:1+til100; alphaIndividual:100*aIndividual; alphaFamily:1-(exp((1-aIndividual))]; each i+til100)
```

![](img/97f7581128bd0bdf85683d4c69d94242_247_0.png)

图 12.6 单个错误率 $\alpha_{individual}$（恒定虚线）和族性错误率 $\alpha_{family}$（增长虚线）关于族规模的函数。

在单个测试完全相关的情况下，我们会观察到：

$$\alpha_{family} = \alpha_{individual}. \quad (12.34)$$

无论族的大小 $m$ 如何。如果我们不能假设测试是独立的但并非完全相关的，通常会采用布尔不等式（并集界，union bound）——对于任何有限的测试集合，至少有一个测试失败的概率不大于各个单个错误率概率之和：

$$\alpha_{family} \leq \alpha_{individual}. \quad (12.35)$$

为了解决单个错误率与族性错误率之间的差异，我们提出了三种可能的解决方案。在下面的每种情况下，我们都假设一个包含 $m$ 个测试的族，且每个测试的零假设均成立。这是该问题的一个较弱的表述。对于每个测试，我们测量统计量并获得一组 $p$ 值 $p_i$，其中 $i = 1, \dots, m$。

### 12.3.8.1 费龙尼校正 (Bonferroni Correction)

族性错误率的经典解决方案是费龙尼校正，由 Dunn (1958) 引入。费龙尼校正定义如下：我们希望测试族的显著性水平设置为 $\alpha_{family}$，当 $p_i$ 满足以下条件时，拒绝单个测试：

$$p_i \leq \alpha_{Bonferroni} = \frac{\alpha_{family}}{m}. \quad (12.36)$$

对于每个 $i$。我们将拒绝零假设的校正显著性水平标记为 $\alpha_{Bonferroni}$。费龙尼校正的实现方式如下：

```
.quantQ.stats.pBonferroni:[alpha;m]

// alpha 族水平 alpha
// m 族的大小
// 返回 Bonferoni alpha
:alpha;
```

结果为：
`.quantQ.stats.pBonferroni[0.05;100]`

```
0.0005
```

### 12.3.8.2 Šidák 校正 (Šidák's Correction)

费龙尼校正的流行替代方案是 Šidák 校正，由 Šidák (1967) 引入。当所有测试在统计上独立时，该校正是精确的。当单个测试正相关时，结果是保守的；而对于负相关的测试，结果不严格且可能表现不。鉴于我们希望将测试族的显著性水平设置为 $\alpha_{family}$，当 $p_i$ 满足以下条件时，拒绝单个测试：

$p_i \le \alpha_{\text{Sidak}} = 1 - (1 - \alpha_{family})^m$，

对于每个 $i$。它的实现方式为：

```
quantQ.stats.pSidak:[[alpha;m]
// alpha -- 族水平 alpha
// m -- 族的大小
// 返回 Sidak 算法
// 1-exp[(1-alpha);1.0%m];
```

结果：

```
quantQ.stats.pSidak[.0.05;100]
0.0005128014
```

### 12.3.8.3 Holm 方法 (Holm Method)

Holm 方法由 Holm (1979) 引入，提供了一种确保族性错误率为 $\alpha_{family}$ 的算法。该方法的工作如下：

- 将所有单个假设的 $p$ 值按升序排序：$p_{(1)} \le p_{(2)} \le \dots \le p_{(m)}$。索引集 $i_{(k)}$ 据此对假设进行排序，即 $H_{i_{(k)}}$ 是 $p$ 值最低的一个。
- 对于每个索引 $i_k$，定义临界值 $\alpha_k = \frac{\alpha_{family}}{m + 1 - k}$。
- 找到使得 $p_{(k)} > \alpha_{(k)}$ 的最小索引。
- 拒绝假设 $H_{i_{(1)}}, \dots, H_{i_{(q)}}$。此外，$H_{i_{(q)}}$ 表示没有假设被拒绝。要实现 Holm 方法，我们需要提供一个包含 $m$ 个 $p$ 值的数组和族置信水平 $\alpha_{family}$。实现代码如下：

```
quantQ.stats.holm:[Array;alpha]
// alpha -- 族水平 alpha
// pArray -- m 维 p 值数组
// 返回被拒绝的假设的索引
exec index from select (update alphaHol: alpha/(count[pArray]+1-i)) from pArray where pIndividual<=alphaHol);
```

# 第 13 章
# 线性回归

在本章中，我们将引入线性回归的概念并在 q 中对其实现。对于几乎任何想要在某一侧的因素与另一侧因变量之间建立关系的问题，线性回归模型都应该是一个起点。线性回归接近于理解变量之间的相关性。为什么我们从对系统线性响应进行建模的线性模型开始呢？根据著名物理学家、诺贝尔奖得主理查德·费曼（Richard Feynman）的精神，最简单直接的答案是：“因为我们可以解决它们”。

线性回归对应于基于点 $x_0$ 邻域的一阶泰勒展开的函数建模：

```
$f(x) = f(x_0) + \sum_{i=1}^n \frac{\partial}{\partial x_i}f(x_0)(x_i - x_0) + residual, \quad (13.1)$
```

这最终可以重写为线性模型：

```
$f(x) \approx A_0 + A_1X_1 + A_2X_2 + \cdots + A_nX_n, \quad (13.2)$
```

其中

```
$A_0 = f(x_0) + \sum_{i=1}^n \frac{\partial}{\partial x_i}f(x_0)(-x_i),$
$A_1 = \frac{\partial}{\partial x_1}f(x_0).$
```

在物理学中，使线性近似成为一个开始探索新物理问题或解释观测现象的合适工具。既然我们提到了理查德·费曼，例如 Veltman 等人（1994），描述亚原子粒子相互作用的费曼图是相互作用哈密顿量在小参数内（称为扰动展开）展开的图形表示。展开中的线性项通常能提供足够的洞察，以做出合理的物理断言。

# 数据科学

线性模型易于操作、易于解释，并为我们提供数据的初步洞察。它是金融、经济学和社会科学中应用最广泛的技术之一。让我们引用 Montgomery 等人（2012）的一的话：

回归分析是分析多因素数据最广泛的技术之一。其广泛的吸引力和用性源于一种概念逻辑过程，即使用方程来表示感兴趣的变量（响应变量）与一组相关的预测变量之间的关系。回归分析在理论上也是有趣的，因为其具有优雅的数学和完善的统计理论。成功使用回归需要同时理解理论，并理解当该技术应用于现实世界数据时通常会出现实际问题。

“回归”（regression）一词出现在 1886 年的一篇关于遗传学、进化和自然选择的论文《遗传状态中向平庸的回归》（*Regression towards Mediocrity in Hereditary State*），Galton (1886)。Galton 在“向均值回归”或更直白地说“向平庸回归”中使用了这个词。Galton 是统计学的先驱。他通过计算关系来解释实证数据，并广泛使用了后来被称为回归线的术语（Bulmer, 2003）。

在本章中，我们提供了线性回归模型的底层理论并讨论了它的局限性。在下一章中，我们将扩展本章介绍的内容并引入正则化技术。正则化可以被看作一种扩展，有助于我们使模型在未知样本上表现得更好。这是一个必须引入的重要元素，我们鼓励读者不要停步于本章，而是直接进入下一章。这些章节共同构成了一个完整且简洁的工具箱。

## 13.1 线性回归

让我们从线性回归模型的定义开始。我们使用矩阵形式来展示模型。令 $n \in \mathbb{N}$ 为数据点数量，$p \in \mathbb{N}$ 为特征数量，$i \in [1, \dots, n]$ 为观测值索引。真实的底层数据生成过程为：

```
$y_i = \beta_1 x_{i1} + \dots + \beta_p x_{ip} + \epsilon_i, \ (13.3)$
```

其中方程中的变量为：

- $x_i$ 被称为输入，也称为回归变量、独立变量或解释变量。
- $y_i$ 被称为输出，也称为被回归变量或因变量。
- $\epsilon_i$ 被称为扰动，也称为噪声或误差项。

### 线性回归

我们可以以类似的矩阵形式表示该模型：

$y = \begin{pmatrix} y_1 \\ y_2 \\ \vdots \\ y_n \end{pmatrix}, \quad X = \begin{pmatrix} x_{11} & x_{12} & \dots & x_{1p} \\ x_{21} & x_{22} & \dots & x_{2p} \\ \vdots & \vdots & \ddots & \vdots \\ x_{n1} & x_{n2} & \dots & x_{np} \end{pmatrix}, \quad \beta = \begin{pmatrix} \beta_1 \\ \beta_2 \\ \vdots \\ \beta_n \end{pmatrix}, \quad \varepsilon = \begin{pmatrix} \varepsilon_1 \\ \varepsilon_2 \\ \vdots \\ \varepsilon_n \end{pmatrix}. \ (13.5)$

$p$ 的值决定了命名：$p=1$ 时，模型称为简单线性回归；当 $p>1$ 时，模型称为多元回归。变量 $y$ 和 $X$ 是给定的，即它们分别排列在向量和矩阵中。相反，$\varepsilon$ 由随机变量组成。

让我们关注误差项以及扰动残差的性质。注意在 (13.4) 中，项 $\varepsilon$ 是一个随机变量，用于对回归变量 $y$ 与确定性函数 $X\beta$ 之间的差异进行建模。由于 $y$ 依赖于 $X$，因此是一个随机变量。当我们给定 $y$ 和 $X$ 作为数据时，我们计算

```
$\varepsilon = y - X\beta. \ (13.6)$
```
