

### 10.3.4 数值示例

#### 1. 四维对象的分类

考虑由四个属性表征的对象，即向量 `e` 和 `t` 的元素。

设学习样本由三个对象组成，每个对象由四个属性描述（见 [表 10.1](#chapter10.xhtml#t10_1)）。

[表 10.1](#chapter10.xhtml#t10_1b)

|  |
| --- |
| *i* || `e[1]^{(i)}` || `e[2]^{(i)}` || `e[3]^{(i)}` || `e[4]^{(i)}` |
|  |
| --- |
| 1 || 0.11 || 0.75 || 0.08 || 0.21 |
| 2 || 0.91 || 0.65 || 0.11 || 0.81 |
| 3 || 0.57 || 0.17 || 0.31 || 0.91 |
|  |

随机决策规则模型 (10.16, 10.17) 的参数为 `α` = 1.0 和 `Δ` = 0。学习答案向量为 `y` = {0.18; 0.81; 0.43}（同前，`y[i]` < 0.5 对应第二类，`y[i]` ≥ 0.5 对应第一类）。熵最优 PDF (10.23) 的拉格朗日乘子取值为 `${\overline{\theta}}^{*} = \left\{ 0.2524;\, 1.7678;\, 1.6563 \right\}.$` 参数属于区间 `a_i ∈ [ - 10,10], i = \overline{1,4}.`

对于此学习子集，熵最优 PDF 的形式为

$$
\begin{aligned}
& {\quad P^{*}(\mathbf{a},\overline{\theta}) = \frac{\exp\left( {- {\sum\limits_{i = 1}^{3}\theta_{i}}y_{i}(\mathbf{a})} \right)}{\mathcal{P}(\overline{\theta})},} \\
& {y_{i}(\mathbf{a}) = \left( {1 + \exp( - {\sum\limits_{k = 1}^{4}e_{k}^{(i)},a_{k})} \right)^{( - 1)}.} \\
\end{aligned}
$$

(10.26)

PDF `P*(a, \overline{\theta}*)` 在第三和第四维度固定值下的二维截面在 [图 10.2](#chapter10.xhtml#f10_2) 中示出。

![Figure 10.2: Two-dimensional cutset of entropy-optimal PDF P^{*}(\mathbf{a},{\overline{\theta}}^{*}).](images/fig10_2.jpg)

[图 10.2：](#chapter10.xhtml#f10_2b) 熵最优 PDF $P^{*}(\mathbf{a},{\overline{\theta}}^{*})$ 的二维截面。

让我们演示如何使用已学习模型为新对象获得预测。在此阶段，利用对象子集 `𝕋` = {`t[1]`,…,`t[r]`}，其中每个元素由向量 `t^{(j)}` ∈ `R^{(4)}` 表征。首先生成一个由 (500 × 4) 维度的四维随机向量 `t^{(i)}, i = \overline{1,500},` 组成的数组，其元素在区间 [0, 1] 上独立均匀分布。然后应用测试阶段小节中描述的分类算法。

对象 `t[i]` 属于第一类和第二类的经验概率 `p[1]^{(i)}`、`p[2]^{(i)}` 在 [图 10.3](#chapter10.xhtml#f10_3) 中给出。

![Figure 10.3: Empirical probabilities of belonging to different classes for Example 1.](images/fig10_3.jpg)

[图 10.3：](#chapter10.xhtml#f10_3b) 示例 1 中属于不同类的经验概率。

对于每个复制体，软分类过程已分配对象属于第一类和第二类的概率。注意，对于每个对象，这些概率之和为 1。

进一步的决策制定（硬分类，即将每个对象分配到适当类）可以通过引入“可靠分类”的阈值来实现。例如，选择 0.75 的阈值；然后所有以高于 0.75 的概率属于第一类的对象（或以低于 0.25 的概率属于第二类的对象）将被分配到前者类，具有一定的可靠性水平。

可靠性水平针对每个新的分类问题单独指定。它是算法的超参数之一，通常使用交叉验证或滑动控制 [118, 187] 进行调整。

#### 2. 二维对象的分类

考虑二维随机对象分类的更直观示例。

设来自示例 1 的学习样本对象的对象由其属性描述的前两个分量表征。学习样本由三个对象组成，每个对象由两个属性描述（见 [表 10.1](#chapter10.xhtml#t10_1)）。参数 `α` 和 `Δ` 以及随机参数 `a` 的区间与示例 1 相同。

求解方程组 (10.22) 并使用熵最优 PDF (10.23) 得到拉格朗日乘子 `${\overline{\theta}}^{*} = \left\{ 9.6316, - 18.5996 \right.$, 16.7502}.` 对于此学习子集，熵最优 PDF `P*(a | \overline{\theta})` 的形式为

$$
\begin{aligned}
& {\quad P^{*}(\mathbf{a}) = \frac{\exp\left( {- {\sum\limits_{i = 1}^{3}\theta_{i}}y_{i}(\mathbf{a})} \right)}{\mathcal{P}(\overline{\theta})},} \\
& {y_{i}(\mathbf{a}) = \left( {1 + \exp( - {\sum\limits_{k = 1}^{2}e}{(i)}_{k},a_{k})} \right)^{( - 1)}.} \\
\end{aligned}
$$

(10.27)

熵最优 PDF `P*(a, \overline{\theta}*)` 在 [图 10.4](#chapter10.xhtml#f10_4) 中示出。

![Figure 10.4: Two-dimensional entropy-optimal PDF P^{*}(\mathbf{a},{\overline{\theta}}^{*}).](images/fig10_4.jpg)

[图 10.4：](#chapter10.xhtml#f10_4b) 二维熵最优 PDF $P^{*}(\mathbf{a},{\overline{\theta}}^{*})$。

与示例 1 类似，使用 500 个随机对象的样本，由二维向量描述，在区间 [0, 1] 上具有独立均匀分布。其他参数与示例 1 相同。对象 `t[i]` 属于第一类和第二类的经验概率 `p[1]^{(i)}`、`p[2]^{(i)}` 在 [图 10.5](#chapter10.xhtml#f10_5) 中给出。

![Figure 10.5: Empirical probabilities of belonging to different classes for Example 2.](images/fig10_5.jpg)

[图 10.5：](#chapter10.xhtml#f10_5b) 示例 2 中属于不同类的经验概率。

与示例 1 类似，[图 10.5](#chapter10.xhtml#f10_5) 中的图具有经验归属概率的相当大的离散。这是由故意较小的学习样本大小引起的。然而，这些结果比随机猜测要好得多。

为此，将所有待分类的随机对象放在同一图表上，并为其硬分类选择可靠性水平。红色将用于所有与第一类相关的对象，绿色将用于与第二类相关的对象。此外，颜色强度将指示在软分类情况下给定对象的经验概率有多大。对象的硬分类结果在 [图 10.6](#chapter10.xhtml#f10_6) 中给出，阈值分别为 0.5（上）和 0.4（下）。

![Figure 10.6: Classification diagram for Example 2.](images/fig10_6.jpg)

[图 10.6：](#chapter10.xhtml#f10_6b) 示例 2 的分类图。

该图上的分类结果证明，对象组之间的界限根据可靠性水平而得到细化。这使我们能够分离出亮红色和绿色点的区域（第一类和第二类）。在两种情况下，对应类的对象都位于学习对象周围的黑色圆圈内。

因此，可靠性水平的适当变化为熵软分类结果的统计处理提供了一种可能的机制。

# 第 11 章 动态回归与预测问题中的随机机器学习

DOI: [10.1201/9781003306566-11](https://doi.org/10.1201/9781003306566-11)

