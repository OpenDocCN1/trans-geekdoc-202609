
我们之前讨论的所有分类技术都使用单一算法来预测未知记录的类别标签。通过使用一组分类器而不是单一分类器，我们可以获得更高的分类准确率。这种技术称为集成分类技术或集成分类模型。集成模型由若干基分类器组成，每个基分类器都单独从训练数据中构建。整体预测过程通过对基分类器的预测进行投票来完成。

数学上，例如，如果 `CE` 是集成模型，`Ci` 是单个基分类器，那么对于记录 `X`，其输出 `CE(X)` 由

`C[E] (X) = MajorityVote {C[1] (X), C[2] (X), …, C[K] (X)}`

多数投票是通过统计整个集合中每个类别标签出现的次数得到的。出现次数最多的类别标签作为最终预测结果返回。

我们将简要讨论一种构建分类器集合的技术。

## Bagging

Bagging，即 Bootstrap Aggregating，是一种集成技术，它反复从整个训练数据集中随机抽取样本，并为每个样本集构建多个分类器。抽样是基于均匀概率分布进行的。例如，如果我们有一个包含 1000 条记录的数据集，Bagging 的工作流程如下：

1. 从数据集中随机抽取十个每个包含 100 条记录的子样本。
2. 为每个子样本训练并构建十个不同的基分类器。
3. 对于新记录，通过取十个基分类器预测结果的众投票来确定其类别标签。

Bagging 通过降低模型中的方差来减少过拟合问题。Bagging 的性能取决于基础分类器的稳定性。子采样过程有助于减少基础分类器中的不稳定性。

## RandomForest 模型

它是一种基于 Bagging 的集成模型，由多个决策树作为基础分类器组成。普通的 Bagging 决策树模型存在的问题是会生成一组相互关联的决策树。它在构建树时会考虑数据集的所有特征。RandomForest 方法则通过采取特殊步骤使基础分类器之间的关联性降低。具体做法是为每个基础模型从数据集中选择一个特征子集。RandomForest 工作流的典型视图如下：

![](img/Picture42.jpg)

**Figure 2.43:** 典型随机森林模型的工作流程

从 *Figure 2.43* 可以看出，RandomForest 是一种分叉-汇聚技术。分叉发生在使用独立训练数据集构建模型时，汇聚则是指预测过程，它将所有输出结果组合在一张量。

## RandomForest 的 Python 实现

`scikit-learn` 提供了一个内置的 RandomForest 模型，使用方法与其他模型完全相同。与决策树一样，RandomForest 不需要对变量进行缩放。只需进行一热编码（one-hot-encoding）转换作为预处理即可。我们将继续使用相同的数据集，并使用之前创建的 `CategoricalVariableEncoder` 类进行一热编码。

下面展示如何创建并训练管道：

![](img/Picture43.jpg)

**Figure 2.44:** 带随机森林的管道代码片段

准确率可以通过以下方式计算：

![](img/Picture44.jpg)

**Figure 2.45:** 准确率计算的代码片段

决策树和 RandomForest 的超参数在概念上非常相似；它们是相同的。但 RandomForest 特别有一个超参数 `n_estimator`（如上代码所示），它决定森林中的基础分类器树的数量，即“超模型”。默认值为 `scikit-learn`（版本 0.21.3）中的 10。

## 多标签分类模型

迄今为止，我们看到的类标签是互斥的。数学上，目标变量 Y 只能从大小为 *K* 的类标签集合 {*C*1, *C*2, …, *CK*} 中取一个类标签。这称为单标签分类，并在前文中详细讨论。但如果 Y 可以从定义的集合中取多于一个类标签呢？数学上是可能的，实际上也是有意义的。考虑电影类型预测问题：一部电影可以同时属于多个（一个或多个）类别。例如，一部电影可能同时拥有动作、喜剧和爱情这三种类型。这属于多标签分类问题。

## 问题形式化

一热编码将离散变量转换为多个连续的二进制变量，生成类似 010..0 的二进制字符串。对于单标签分类，目标变量可以这样转换，只有一位为 1，其余为 0。但多标签问题中，多个位应设为 1，例如 0100110..0。多标签目标变量中 1 的数量 N 满足 1 ≤ N ≤ K，其中 K 为类别总数。二进制字符串的长度也为 K。单标签分类器只能预测 0 或 1 中的一个，传统的单标签分类器无法预测多标签问题中的 N 个 1。

## 问题分解及伞分类方案（Umbrella classification scheme）

在多标签分类中，我们可以将目标变量二进制字符串的每一位视为不同问题的结果。因此，主问题可以分解为一组子分类问题，每个子问题都是二分类任务。以电影类型预测为例，若有 K 种可选类别，则目标变量为长度为 K 的二进制字符串。若类别包括动作、喜剧、恐怖、科幻、爱情等，则有 K 个独立的二分类子问题：

*   1) 电影是否属于动作类？ 0 或 1
*   2) 电影是否属于喜剧类？ 0 或 1
*   …
*   K) 电影是否属于爱情类？ 0 或 1

（0 表示否，1 表示是）

这些 K 个二分类模型可以使用任何标准分类模型（如前文讨论的决策树、逻辑回归、朴素贝叶斯等）或其他集成模型来构建。通常选择一种模型，并为多个子问题构建多个实例。例如，若选择逻辑回归作为模型，则需要构建 K 个逻辑回归模型。

在上述基础分类模型之上，有两种**伞分类方案（Umbrella classification schemes）**可应用：

## 二元相关性方案（Binary relevance scheme）

二元相关性是一种简单的方案，每个模型仅针对单个类别标签进行训练，忽略其他标签。它类似于之前讨论的多类逻辑回归的“一对所有”（one-vs-rest）方法。每个模型的输出为 0 或 1，1 表示该类别标签在数据实例中存在，0 表示不存在。最终，所有模型中标记为 1 的类别标签即为最终预测结果。例如，若预测结果为 11000…0，则表示该电影属于动作类和喜剧类。

## 分类链方案（Classifier chain scheme）

该方案利用前序分类器的输出作为后续分类器的额外特征。这些特征会累加，最后一个分类器在原有特征之外会拥有 K-1 个额外特征。一般而言，第 i 个分类器会有 i-1 个额外特征（1 ≤ i ≤ K）。下图展示了该方案的架构：

![](img/Picture45.jpg)

**Figure 2.46:** 分类链方案的架构

上图的结构类似于链表（LinkedList）数据结构。Y[1], Y[2], …, Y[N] 分别代表每个分类器的响应变量。前序分类器的输出被作为下一分类器的额外特征加入，因此第 i 个分类器在构建时会使用完整的特征集 f[1], f[2], …, f[n] 以及 Y[1], Y[2], …, Y[i-1]。

关于分类链的顺序问题，即哪个分类器排第 1、第 2、第 3 等，有以下统计方法：

*   **分类链的集合（The ensemble of Classifier Chains）**：这是基于随机抽样的分类链集合。随机选择不同的链，最后采用多数投票策略进行预测，类似于 RandomForest 模型。
*   **蒙特卡罗分类链（Monte-Carlo Classifier Chains）**：利用蒙特卡罗模拟生成最优的分类器序列。

上述两种方法的详细讨论超出本文范围。

## 标签子集方案（Label powerset scheme）

-   二元相关性（Binary Relevance）和分类链（Classifier Chain）的基本概念相同，都是基于一系列子分类器的输出。但 `Label Powerset` 不将问题分解为子问题。它把数据集中出现的每一个目标变量值的唯一组合视为一个独立的单一类别标签，并在其上构建一个单一分类器。例如，`(1100…0)`、`(010…0)`、`(00…110)` 被视为整体的独立类别标签。在电影类型预测的情境下，`Label Powerset` 会把诸如 (`action`, `comedy`)、(`comedy`, `romance`) 和 (`science-fiction`) 这样的组合视为独立的类别标签，前提是这些组合在数据集中已经出现。该技术不会把数据集中不存在的任意组合视为类别标签。因此，对未知数据实例的预测标签始终是训练数据集中已有的组合。

## 各方案对比

*   `Binary Relevance` 是一种极其简单的方法，适用于所有类别标签相互独立的情况，即一个标签的出现不影响另一个标签的出现。它不考虑标签间的依赖关系，常常无法发现隐藏的关联。
*   `Classifier Chain` 能够处理标签间的依赖关系。它把前一个分类器的输出当作后续分类器的输入特征，从而保留了关系信息。它适合存在父子类标签关系的场景，即子标签只能在父标签出现时才能出现。但该方案的复杂度随类空间（class space）的规模而增长，尤其是类空间很大时，复杂度会显著上升。
*   `Label Powerset` 适用于数据集中出现的唯一标签组合数量相对类别数量较少的情况。与前两种方案不同，这里不需要进行详细的、分解的分析。

## 准确率指标

多标签分类器的性能有多种度量指标。常用的度量是预测正确的记录数与总记录数的比值，这在多标签场景中称为 `子集准确率（subset accuracy）`，但它并不完全可靠。例如，若真实电影类别为 `science-fiction`、`action`、`adventure`，而预测类别为 `action`、`adventure`、`romance`，则无法断定预测完全正确还是完全错误，它既不全对也不全错。因此需要别的指标来捕捉部分正确性。

## Hamming loss 指标

`Hamming loss` 用于衡量多标签分类器预测的部分正确性。它计算二进制位串（即类别标签）在预测过程中的平均损失。具体做法是对每个实例，对原始二进制位串与预测位串执行 XOR 操作，得到该实例的损失，然后取全体实例损失的平均值。其表达式如下：

![](img/p95.jpg)

`Hamming loss` 的取值范围是 0 到 1，作为损失度量，值越小表示表现越好。

我们也可以使用 F1 分数来衡量准确率，方法与多类场景相同。应根据类别不平衡情况选择宏观（macro）或微观（micro）策略。对每个独立类别计算 F1 分数，然后再用宏观或微观策略汇总得到最终得分。当存在类别不平衡时，使用 F1 分数通常更合适。

## Python 多标签分类器实现

有一个名为 `scikit-multilearn` 的独立库，提供多标签分类器的模块和函数。完整的使用示例在 *第 9 章：案例研究与叙事（Chapter 9: Case Studies and Storytelling）* 中给出，用于预测电影类型。读者可参考该章节获取完整实现。

## 结论

本章讨论了分类问题的数学表达、不同分类器及其理论基础，以及使用开源数据集和 Python 实现的案例。我们还学习了类别不平衡问题、替代度量指标以及解决机制，以及使用 Python `scikit-learn` 构建管道的方法。这些知识将在后续章节的讨论中派上用场。

下一章我们将探讨当目标变量为连续值时，如何构建机器学习模型。

# CHAPTER 3

## 回归（Regression）

我们在前面讨论了如何从特征集合中预测类别目标变量，即典型的分类问题。现在，如果要对数值 / 连续目标变量进行同样的预测，该如何进行？首先，这称为 *回归问题*。我们以软件行业为例，问题描述是：能否根据软件工程师的工作经验年限、所掌握的技术、变动公司的次数等特征来预测其薪资？这里的薪资是一个连续变量，取值为实数（正数）。因此，需要利用其他特征来估计薪资，这正是回归问题的典型表现。本章将详细探讨该主题。

## 结构

本章将讨论：

*   回归的数学形式：线性 vs. 非线性关系
*   使用 OLS（最小二乘）和梯度下降方法求解线性回归
*   特征选择技术：前向和后向
*   正则化技术：Lasso 和 Ridge
*   基于回归树的方法

## 目标

完成本章后，我们能够：

*   使用适当的特征选择技术构建线性和多项式回归模型。
*   根据不同使用场景判断哪种回归模型更合适。
*   解释每个特征变化对目标变量的重要性和影响。

## 回归问题的数学定义

在导入部分，我们讨论了软件工程师薪资的估计问题。现在尝试用代数方程表示这个问题：

*salary = 1.5* \* *years of exp + 1.7* \* *technology stack + 2* \* *no of companies + 0.4* \* *city*

从我们迄今的机器学习认知来看，`years of Exp`、`technology stack` 等都是自变量，`salary` 是因变量。但这些真实数值——1.5、1.7、2 以及更多——是什么？它们是系数或权重。如何获得这些权重将在后续章节中讨论。从上述方程可以直接得到软件工程师的薪资估计，只要提供自变量的数值即可。

我们可以把上述方程写成更通用的形式，如下图所示：

![](img/Ch_3_1.jpg)

这是典型线性回归的方程。`b[0]` 称为 **截距（intercept）**，`b[1]`、`b[2]` 等为自变量 `x[1]`、`x[2]`、…、`x[n]` 的系数。

## 线性 vs.非线性关系

前面讨论的方程是线性关系。为什么叫线性？我们简化问题，只保留一个因变量 *x*，并把方程写成 *b*[0] = 3、`b`[1] = 10 的形式：

*y* = 3 + 10*x*

可以通过随机生成 *X* 的一些值并计算对应的 *Y* 值来绘制 *Y* 与 *X* 的关系图。下面的 Python 代码片段可以帮助完成此操作。

![](img/Picture1_2.jpg)

**Figure 3.1:** 一个样本线性关系的示意图

Though we did a scatter plot, but it clearly shows the shape of a straight line. Gradient or Slop of this type of linear relationship is constant. This is for just two variables. But if we consider *n* number of feature variables like *X*, then what will happen? Then this straight line will become a hyperplane in n-dimension.

Now, let's change the equation and consider the following:

*y* = 3 + 10*x*²

And the plot will look like a curve below:

![](img/Picture2_2.jpg)

**Figure 3.2:** Plot of a non-linear sample relationship

This curve will become a Sphere and hypersphere for 3-*D* and *n*\-*D* case, respectively. Here gradient is 10*x*, which is a variable itself. So, we can say that the above equation is for a non-linear relationship between *Y* and *X*.

The main difference between linear and non-linear relationship is the gradient (constant vs. variable). And we can say that these relationships are always with respect to other variables and of very relative nature.

## Conversion between linear and non-linear relationships

If we change/transform one variable, then the relationship changes drastically. A nonlinear one becomes linear and vice-versa.

For the previous equation, if we consider *w* as *x*[2] and the equation becomes:

*y* = 3 + 10*w*

Plotting above equation will produce below a line like below:

![](img/Picture3_2.jpg)

**Figure 3.3:** Plot of a sample transformed non-linear relationship

So, transforming one variable to others can change the nature of the relationships. A non-linear can become linear and vice versa.

## Building a linear regression model

We saw the formal algebraic form of Linear Regression, which is an equation. Now, the question is, how can we build the model and find optimal values of coefficients *b*[0], *b*[1], *b*[2], …., *b*[n]. There are different techniques fordoing it. We will discuss one of them in the next section.
