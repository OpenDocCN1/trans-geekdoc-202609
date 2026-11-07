
$$Z\\left( x \\right) = \\frac{1}{2}\\left\\lbrack {\\frac{P\\left\\lbrack {TR} \\middle| x \\right\\rbrack}{P\\left\\lbrack T \\right\\rbrack} + \\frac{P\\left\\lbrack {CN} \\middle| x \\right\\rbrack}{P\\left\\lbrack C \\right\\rbrack} - \\frac{P\\left\\lbrack {TN} \\middle| x \\right\\rbrack}{P\\left\\lbrack T \\right\\rbrack} - \\frac{P\\left\\lbrack {CR} \\middle| x \\right\\rbrack}{P\\left\\lbrack C \\right\\rbrack}} \\right\\rbrack.$$  
(9.1)

方程 (9.1) 仅在随机实验中有效，其中 `P(T)`，或 `P(C)` = 1 − `P(T)`，是由活动设计驱动的已知常数。例如，按设计，我们可能有一个随机实验，其中 80% 为处理组，20% 为对照组。这意味着，给定目标群体，每个个体的处理分配概率为 0.8。这种随机化过程对每个人都有已知且相同的处理概率。然而，在非随机实验（或观察数据）中，`P(T)` 或 `P(C)` 不再是常数，因为某些个体接受处理的概率较高或较低，这取决于某些特征（例如通过自我选择偏差）。本文介绍的方法论很简单，即用 `P(T|x)` 或 `P(C|x)` 替换 `P(T)` 或 `P(C)`，这意味着处理分配概率现在是某些预测变量（或协变量）的函数：

$$Z\\left( x \\right) = \\frac{1}{2}\\left\\lbrack {\\frac{P\\left\\lbrack {TR} \\middle| x \\right\\rbrack}{P\\left\\lbrack T \\middle| x \\right\\rbrack} + \\frac{P\\left\\lbrack {CN} \\middle| x \\right\\rbrack}{P\\left\\lbrack C \\middle| x \\right\\rbrack} - \\frac{P\\left\\lbrack {TN} \\middle| x \\right\\rbrack}{P\\left\\lbrack T \\middle| x \\right\\rbrack} - \\frac{P\\left\\lbrack {CR} \\middle| x \\right\\rbrack}{P\\left\\lbrack C \\middle| x \\right\\rbrack}} \\right\\rbrack~\\left( 9.6 \\right).$$  
(9.6).

方程 (9.6) 是公式 (9.1) 的简单扩展。因此，公式 (9.6) 可被视为修改后的 KLZ 或修改后的 KLZ（针对非实验数据修改）。这里，`P(T|x)` 只是 `PS`，可使用逻辑回归或任何可预测二元结果的方法进行估计。

`P(T|x)` = `P(TR|x)` + `P(TN|x)`  
(9.7a)

and

`P(C|x)` = 1 − `P(T|x)`.  
(9.7b)

然后，可以使用公式 (9.6) 以及公式 (9.7a) 和 (9.7b) 轻松计算预测的提升值。

上述描述仅适用于二元响应变量。对于观察数据的连续响应变量怎么办？由 [Athey 和 Imbens (2015)](#chapter9.xhtml#ref9_2) 提出了一种针对观察数据的连续响应变量的转换：

$${R\_{i}}^{\*} = ~R\_{i}\\frac{T\_{i} - P\\left( T \\middle| x\_{i} \\right)}{P\\left( T \\middle| x\_{i} \\right)\\left( {1 - P\\left( T \\middle| x\_{i} \\right)} \\right)},$$  
(9.8)

其中 `P(T|x[i])` 只是可估计的 `PS`。请注意，公式 (9.8) 是公式 (9.4) 对于观察数据的自然扩展，其中包含了预测变量（或协变量）。

### 9.4.3 观察数据提升建模示例

**示例 9.2（[示例 6.1](#chapter6.xhtml#secex6_1)的延续）**

回顾第 6.7.1 节中 [示例 6.1](#chapter6.xhtml#secex6_1) 的内容，响应变量 `Donated` 由一组变量驱动。假设我们再次拥有与 [示例 6.1](#chapter6.xhtml#secex6_1) 中相同的协变量集。此外，我们假设在模拟中，处理分配是 `spent`（过去平均捐赠金额）和 `frequency`（过去捐赠次数）的逻辑函数。

遵循 [第 9.4 节](#chapter9.xhtml#sec9_4) 之前概述的方法：
1. 我们首先拟合逻辑回归，以使用整个数据集恢复处理分配与混杂因素（本例中为 `spent` 和 `frequency`）之间的关系。
2. 对训练数据进行评分以确定每个观测值的 `PS`。
3. 我们接下来应用公式 (9.5) 使用基于上一步计算的 `PS` 的 IPW 方法构建一组权重。
4. 我们然后遵循 [第 9.4.1 节](#chapter9.xhtml#sec9_4_1) 中概述的重叠分析和 windsorization 步骤来处理权重。
5. 接下来，这组权重与各种提升建模方法结合使用以拟合训练数据。
6. 最后，使用保留样本来评估 [第 9.4.1 节](#chapter9.xhtml#sec9_4_1) 和 [第 9.4.2 节](#chapter9.xhtml#sec9_4_2) 中提到的各种提升建模方法（两模型方法、处理虚拟变量方法和修改后的 KLZ），其中保留样本与训练样本一样，也必须使用 IPW 方法加权以计算无偏提升估计。

遵循公式 (9.5)，应用以下 SAS 语句构建权重：
```
if trt = 1 then wei = 0.8033/ps; else wei = 0.1967/(1 - ps);
```

我们在 [表 9.3](#chapter9.xhtml#tbl9_3)、[图 9.4a](#chapter9.xhtml#fig9_4a) 和 [图 9.4b](#chapter9.xhtml#fig9_4b) 中总结了处理组和对照组的 `PS` 分布。由于两个分布几乎完全重叠（最小值和最大值相似），因此没有丢弃任何数据点。如 [第 9.4.1 节](#chapter9.xhtml#sec9_4_1) 中所述，`PS` 的高变异性一直是文献中的讨论点，因此执行 windsorization 步骤，将数据限制在 95 百分位和 5 百分位，本例中分别为 1.51 和 0.5，本质上将权重限制为每个观测值不超过 50% 的增减。

表 9.3 倾向得分的汇总统计量 [⏎](#chapter9.xhtml#b9tbl9_3)

| 分析变量：ps |
| --- |
| trt || N || 均值 || 标准差 || 最小值 || 最大值 |
| 0 || 59008 || 0.707418 || 0.146591 || 0.268396 || 0.99723 |
| --- | --- | --- | --- | --- | --- |
| 1 || 240992 || 0.826781 || 0.124055 || 0.268396 || 0.999999 |

![图 9.4a 治疗组（trt = 1）和对照组（trt = 0）的倾向得分箱线图。⏎](images/fig9_4a.jpg)

图 9.4a 治疗组（trt = 1）和对照组（trt = 0）的倾向得分箱线图。 [⏎](#chapter9.xhtml#b9fig9_4a)

![图 9.4b 治疗组（trt = 1）和对照组（trt = 0）的倾向得分频率分布。⏎](images/fig9_4b.jpg)

图 9.4b 治疗组（trt = 1）和对照组（trt = 0）的倾向得分频率分布。 [⏎](#chapter9.xhtml#b9fig9_4b)

权重构建完成后，我们现在可以使用权重应用各种提升建模方法。

表 9.4 模型性能汇总 [⏎](#chapter9.xhtml#b9tbl9_4)

|  || Gini || Gini 15% || Gini 5% || Gini 可重复性 (R²) (%) |
| --- | --- | --- | --- | --- |
| 基线 || 5.4611 || 0.5714 || 0.0635 || 78.21 |
| --- | --- | --- | --- | --- |
| 两模型方法 || 4.7428 || 0.5464 || 0.0943 || 78.63 |
| 处理虚拟变量 ([Lo (2002)](#chapter9.xhtml#ref9_25)) || 4.7556 || 0.5459 || 0.0924 || 78.66 |
| 修改后的四象限方法 (KLZ (2014)) || 4.8431 || 0.5445 || 0.0897 || 80.49 |

![图 9.5a 观察数据提升建模示例的提升图。⏎](images/fig9_5a.jpg)

图 9.5a 观察数据提升建模示例的提升图。 [⏎](#chapter9.xhtml#b9fig9_5a)

![图 9.5b 观察数据提升建模示例的收益图。](images/fig9_5b.jpg)

图 9.5b 观察数据提升建模示例的收益图。

## 9.5 直接响应建模与直接响应和提升建模的整合
