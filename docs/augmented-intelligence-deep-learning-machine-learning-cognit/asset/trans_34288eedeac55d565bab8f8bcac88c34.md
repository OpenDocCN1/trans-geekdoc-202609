

## a. JRip（Ripper）概述

RIPPER 由 Cohen [63] 提出。它用于对初始规则集进行全局优化。该算法的动机是逐个放置或修改每条规则，以提高规则集的准确率 [64]。

该技术遵循三个步骤：生长、剪枝和优化。算法2展示了 RIPPER 的概要。

## 算法2：JRip 算法的高级伪代码。

```
Algorithm: JRip algorithm
Input: - A sequence of m instances S = {(x₁, y₁)...(xₘ, yₘ)} where xᵢ ∈ Xₖ with labels yᵢ ∈ Y={0,1} from Polish bankruptcy dataset,
- F: Number of folds (optional),
- O: Number of optimization (optional)
- N: Number of minimal weights (optional)
- E: Check error rate (default: check) (optional)
- P: pruning check (default: prune) (optional)
Output: final rule set RS
Initialize: a rule set RS = {}
1- For each class:
2- [Building Stage]: Generate an initial rule set RI
3- Repeat:
4- Grow phase: grow one rule by adding conditions that satisfy the highest information gain: p(log(p/t)-log(P/T)) until the rule is 100% accurate
5- Prune phase: prune each rule according to the pruning metric: p/(p+n)
6- Until error rate >= 0.5 or there are no more positive instances or the description length (DL) of the ruleset is 64 bits greater than the smallest DL
7- [Optimization Stage]:
8- From RI, generate two variants A and B (A from an empty rule and B from the full rule) using the grow phase
9- Prune A and B on a metric: (TP+TN)/(P+N)
10- Compute the original rule according to the description length DL of A and B
11- Select the variant with the minimal DL for RI
12- If there are residual positives:
13- ([Building Stage])
14- Else:
15- ([Deletion Stage])
16- [Deletion Stage]:
17- Delete the rules from the ruleset that would increase the DL of the whole ruleset
18- Add resultant ruleset to RS
19- End For
```

如算法2所示，JRip 是 RIPPER 算法的一种基于 Java 的实现。该方法初始化一个空规则集 RS，并开始遍历每个类别，从较不占优势的类别到最频繁的类别。规则生成过程包含三个阶段。构建阶段分为两个阶段：生长阶段计算每个属性的每个取值。选择具有最高信息增益的条件。通过贪婪地追加条件来生长一条规则，直到该规则达到 100% 准确率。剪枝阶段根据特定的剪枝度量对生成的每条规则进行增量剪枝。这两个阶段会重复，直到满足其中一个停止条件（错误率超过 0.5，或不再出现正例，或规则集的描述长度（DL）超过计算的最小 DL。该阶段生成初始规则集 RI，供第二阶段使用。优化阶段使用生长和剪枝阶段从随机化数据生成两个变体。一个变体必须从空规则创建，另一个变体通过向初始条件贪婪地追加前件来创建。算法选择具有最小 DL 的变体作为 RI 中的一个示例。如果检查完 RI 后仍然存在正样本，则使用构建阶段生长新规则。否则，RIPPER 进入最后阶段，该阶段删除可能增加整个规则集 DL 的条件。然后，它将生成的规则集添加到 RS 中，RS 将作为算法的最终输出。

## a. AdaBoost 概述

对于二分类问题，最常用的提升算法是 AdaBoost。该算法由 Freund 和 Schapire [65] 提出。以下伪代码描述了该技术的运行方式。

## 算法3：AdaBoost 算法的高级伪代码。

```
Algorithm: AdaBoost algorithm
Input: -A sequence of m instances S = {(x₁, y₁)...(xₘ, yₘ)} where xᵢ ∈ Xₖ with labels yᵢ ∈ Y={0,1}
from Polish bankruptcy dataset,
-Weak learner
-T (number of iterations)
Output: The final classifier with hypothesis Hx=sign(∑t=1 T αt htx)
Initialize: D₁(i)=1/m for all i =1,.....,m
1-For t = 1 to T
2- Call Weak learner using distribution Dₜ
3- Get Weak classifier and obtain hypothesis ht: X→{-1,+1}
4- Calculate the error rate ε_t = ∑i=1 m D_ti [h_t(x_i)≠y_i] of h_t
5- If ε_t > 0.5 then T=t-1 and abort loop
6- set α_t = ½ ln[(1-ε_t)/ε_t]
7- Update D_{t+1}(i)= D_t(i) exp[-α_t y_i h_t(i)] / Z_t (Z is a normalization factor)
```

如算法3所示，AdaBoost 将来自波兰破产数据集的 m 个样本的训练集作为输入，以进行二分类。它初始化一个权重函数 Dₜ(x)，该函数为所有训练样本分配相同的权重。在每次迭代 t 中，使用弱学习器创建一个带有假设 hₜ 的分类器，该假设计算训练样本的错误率 eₜ。算法使用错误率来调整概率分布 Dₜ(x)。这种调整会为错误分类的训练样本分配更多权重，而为上一次迭代中正确分类的样本分配更少权重。这个过程在 T 次迭代中依次构建多个弱分类器。算法最终输出一个带有假设 H 的分类器，该假设是通过对之前的各个分类器进行加权投票获得的。每个分类器的权重由它们所使用的分布 Dₜ 的准确率决定。

以下伪代码代表了我们针对问题陈述所提出的自适应模型的概要。

算法4展示了针对我们问题陈述的自适应算法的结构，我们将其称为 SBSAda-Rip。该算法使用数据的 70% 并进行 T 轮迭代。该方法以分布 D₁ 和空规则集 RS 初始化。在每一轮 t 中，AdaBoost 使用分布 Dₜ 调用 JRip 分类器。JRip 分类器要经过一系列阶段。它从构建阶段开始。它逐一构建规则（同时满足最高信息增益：p(log(p/t)-log(P/T))）并逐一剪枝（根据剪枝度量：p/(p+n)）。当达到其中一个终止标准时，它会创建初始规则集 RI。优化阶段使用 RI 来拆分规则，并通过重新生长和重新剪枝（使用 (TP+TN)/(P+N)）来优化这些规则。选择最佳规则并重新添加到 RI 中。最后阶段，即删除和选择阶段，使用新的 RI 生成最终规则集 RS。该阶段删除阻碍规则集的条件，并将生成的规则集添加到 RS。从 JRip 分类器执行的计算中，AdaBoost 获得假设 hₜ。然后计算该假设的错误率，如果错误率大于 0.5，则更新分布 Dₜ₊₁。整个过程重复进行，直到数据中不再有错误分类的样本。最终，我们获得带有假设 H(x) 及其规则集的最合适的分类器。

## 5.4.3. 测试子阶段

该阶段使用测试数据来衡量训练模型的性能。我们从选定的最佳假设和规则集中获得所提出的模型，我们将其视为最优选项。

## 5.5. 验证

为了评估我们算法生成预测规则的性能，本节探讨两个主要研究问题。

## 算法4：增强型 Boosting 模型的高级伪代码。

```
Algorithm: SBSAda-rip algorithm
Input: -A sequence of m instances S = {(x₁, y₁)...(xₘ, yₘ)} where xᵢ ∈ Xₖ (Xₖ the subset obtained from SBS) with labels yᵢ ∈ Y={0,1} from Polish bankruptcy dataset
-JRip algorithm
-T (number of iterations)
Output: The final classifier with hypothesis H(x) and its final rule set RS
Initialize: D_t(i)=1/m for all i=1,...,m, a rule set RS = {}
1-For t = 1 to T
2- Call JRip using distribution D_t:
3- For each class:
4- [Building Stage]: Generate an initial rule set RI
5- Repeat:
6- Grow phase: grow one rule by adding conditions that satisfy the highest information gain: p(log(p/t)-log(P/T)) until the rule is 100% accurate
7- Prune phase: prune each rule according to the pruning metric: p/(p+n)
8- Until error rate >= 0.5 | no more positive instances | description length (DL) of the ruleset is 64 bits greater than the smallest DL
9- [Optimization Stage]:
10- from RI, generate two variants, A and B (A from an empty rule and B from the full rule) using the grow phase
11- prune A and B on metric: (TP+TN)/(P+N)
12- compute the original rule according to the description length DL of A and B
13- select the variant with the minimal DL for RI
14- If there are residual positives:
15- ([Building Stage])
16- [Deletion Stage]:
17- Delete the rules from the ruleset that would increase the DL of the whole ruleset
18- Add resultant ruleset to RS
19- End For
20- Get JRip classifier and obtain hypothesis h_t
21- Calculate the error rate e_t = Σ_i=1^m D_ti [h_t(x_i)≠y_i] of h_t
22- If e_t > 0.5 then T=t-1 and abort loop
23- set α_t = ½ ln [(1-e_t)/e_t]
24- Update D_{t+1}(i)= D_t(i) exp[-α_t y_i h_t(i)] / Z_t (Z is a normalization factor)
```

## 5.5.1. 研究问题

RQ 01：与其他方法相比，所提出的方法能在多大程度上从给定数据集中发现准确的分类模型？

RQ02：现有模型与所提出的模型之间的显著比较是什么？

## 5.5.2. 实验数据库描述

为了验证我们的工作，我们使用了波兰公司的财务信息，这些信息位于

