

## AdaBoost Stumps 473

![](img/97f7581128bd0bdf85683d4c69d94242_497_0.png)

**图 23.1** 跨 AdaBoost 样本的 isPredicted 累加和

- 准确率 (accuracy) - 在所有测试案例中真例占的比例。
- 召回率 (recall) - 真正例数与 y = 1 的真例总数的比例。
- 精率 (precision) - 真正例数与预测为 ŷ = 1 的案例数的比例。
- 特异性 (specificity) - 真负例数与 y = -1 的真例总数的比例。
- F1分数 (F1score) - 精率和召回率的调和平均数。

该函数的实现如下：

```
quantq.ada.adaPredictionStats::[tabAdaAdaPrediction
// tabAdaPrediction - .quantq.ada.adaBoostPrediction 函数的输出
truePositive:sum (tabAdaPrediction[`y`]=tabAdaPrediction[`prediction`])
  and (tabAdaPrediction[`y`]=1);
trueNegative:sum (tabAdaPrediction[`y`]=tabAdaPrediction[`prediction`])
  and (tabAdaPrediction[`y`]=-1);
falsePositive:sum (tabAdaPrediction[`y`]=1) and (tabAdaPrediction[
  and `prediction`]=-1);
falseNegative:sum (tabAdaPrediction[`y`]=-1) and (tabAdaPrediction[
  and `prediction`]=1);
accuracy(`$truePositive+trueNegative`)*%f`($count tabAdaPrediction;
recall:(`$truePositive`)*%f`($truePositive+falsePositive);
precision:(`$truePositive`)*%f`($truePositive+falseNegative);
specificity:(`$trueNegative`)*%f`($falsePositive+trueNegative);
F1score:2.0::((1.0%%recall)%(1.0%%precision));
// 输出是包含所有测量量的字典
:truePositive`trueNegative`falsePositive`falseNegative`accuracy`recall`
  and precision`specificity
F1score:(truePositive;trueNegative;falsePositive;falseNegative;
  and accuracy;recall;
precision;specificity;F1score);
```

## 机器学习

并为正在检查的案例给出结果：

.quantQ.ada.adaPredictionStats[tabAdaPrediction]`(`truePositive`trueNegative`falsePositive`falseNegative`accuracy`recall` precision`specificity`fscore` |(37;37;18;0;0.672723;0.672723;0.672723;0.672723;0.672723)`

预测输出是非常对称的。算法并不倾向于两个类别中的任何一个。它旨在提供一个平衡的估计，这在我们的合成表中已经实现。此外，模型的分析是在样本内进行的。我们鼓励读者独立重复实验，并评估输出中遇到的对称性是巧合的还是数据集的特性（提示：通常是后者）。

让我们进一步说明，查看分类表所需的清晰信息可以通过如下获取：

```
select count res y, prediction from tabAdaPrediction
```

| y prediction | res |
|---|---|
| -1 -1 | 37 |
| -1 1 | 18 |
| 1 -1 | 18 |
| 1 1 | 37 |

如果我们调查表中纯粹随机的部分，我们得到：

```
select count res y, prediction from tabAdaPrediction where i>9
```

| y prediction | res |
|---|---|
| -1 -1 | 37 |
| -1 1 | 18 |
| 1 -1 | 18 |
| 1 1 | 27 |

表明真正例的划分对应于变量与自变量之间存在强关联的观测值。

### 23.5 给读者的建议

我们为读者提供了几种扩展方向：

- **随机特征 (Random feature)** – AdaBoost 算法的实现随机选择特征。使用与阈值选择相同的标准来选择最佳特征会更优化。
- **元参数选择 (Meta-parameter selection)** – 弱分类器的数量 $L_{AdaB}$ 由用户选择。这不一定能提供最优数量，可能会遇到过拟合。交叉验证是一种可以用于寻找 $L_{AdaB}$ 优值的技术；AdaBoost 可以封装进交叉验证工具中，该工具会将样本分成部分并进行样本外验证。
- **子采样 (Subsampling)** – 数据集可以分成批次，每个弱分类器可以在不同的批次上训练。这将增强该技术的威力。
- **回归 (Regression)** – 提供的方法仅用于二分类，AdaBoost 技术也可以很好地用于回归。因此，当前函数可以扩展到回归，并鼓励读者掌握他们的机器学习技能。

## 第24 章 树

在第 23 章中，我们引入了决策桩（decision stumps）的概念及其在 AdaBoost 算法中的应用。决策桩是决策树的最简单示例。在本章，我们将更详细地介绍决策树；该方向的说明请参见 Morgan 和 Quin (1963)，或者 Breiman 等人 (1984) 和 Loh (2011)。我们展示了适用于分类和回归的方法。我们从理论介绍开始，然后在 q 中进行实现。我们用于表示树的函数基于 Steiner 首次引入的树的概念。

### 24.1 树的引言

让我们考虑跨越 $x_1, \dots, x_N$ 的特征空间。基于树的方法将空间划分为矩形区域，并为每个区域分配一个模型。图 24.1 展示了 $N=2$ 的划分。

我们用粗体字体表示了“叶子”节点，即图 24.1 中所示的节点。我们可以使用上述结构来模型 $y$：

$\hat{y} = \hat{f}(x_1, x_2) = \sum_{i=1}^{7} c_i 1((x_1,x_2) \in \text{domain}_i). \quad (24.2)$

其中 $1()$ 是用于建模树域的指示函数。

