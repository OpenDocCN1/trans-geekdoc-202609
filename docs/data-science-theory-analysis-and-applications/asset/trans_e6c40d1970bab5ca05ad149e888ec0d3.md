

![](img/5025594f89449de2a74e5b325b1e84ef_248_0.png)

**图 10.3** 整体所提工作的流程图。

![](img/5025594f89449de2a74e5b325b1e84ef_249_0.png)

**图 10.4** 情绪状态转换机模型。

图 10.3 中的工作。我们实现了情绪状态转换机的转换函数算法，并在图 10.4 中描述了情绪状态转换机的模型。

我们将所提工作分为两部分：

1. 使用 SVM、KNN 和随机森林对人类的不同情绪状态进行分类，以选择一种高效的情绪分类模型。
2. 实现一个新的状态转换机，用于在特定时间间隔内改变人类的不同情绪状态。为取得结果，我们使用了 Kaggle 情绪数据集 [22]。

在图 10.3 中，我们描述了整个所提工作的流程图，该图将数据集分为两部分：训练数据和测试数据。训练集用于训练分类模型（SVM、KNN、随机森林），然后使用测试数据集对模型进行测试。在图 10.3 中，我们展示了分类、性能分析和情绪状态转换机三个过程之间的流程。如果分类模型输出任何错误，我们就返回开始阶段。

## 10.3.1 分类过程

### 10.3.1.1 SVM 分类器

采用“一对多”方法的 SVM 多类分类使用一组二分类器，每个分类器经过训练后将一个类别与所有其他类别分开。然后，每个数据对象被分类到判定值最大的特定类别中（Hsu 和 Lin，2002）[23,24]。该方法训练四个 SVM（其中四是类的数量）和四个决策函数。其基本思想是将多类问题简化为一组二分类 SVM 问题。简要地说，该方法如下所示：

```text
{x_i,y_i}, i=1,2,..N, where N is the number of training samples.
For each c in (c1, c2, c3, c4)
y_i ∈ {-1, +1}, where N is the number of training samples, y_i=+1 for class c and y_i=-1 for class (c, rest of c_i)
    Find hyperplane between two classes defined by vector w with scalar b: w.x + b=0.
        Find the distance between the hyperplane: 2 / |w|
    y_i [w^T. x_i + b] ≥1; i =1,2..N.
Apply a Lagrangian formulation
Use polynomial kernel: K (x_i, xj) = (γ x_i^T x_j + r) ^d, γ >0; γ, r and d are kernel parameters.
end
```

训练数据由 {x_i, y_i}（i = 1, 2, ..., N）表示，c1、c2、c3 和 c4 分别代表积极、消极、抑郁与和谐四类。在实现时，我们可以使用 Python 中广泛使用的 SVM 库 [25]，即 scikit-learn [26]。

### 10.3.1.2 KNN 分类器

KNN 也被称为懒惰学习分类器。决策树和基于规则的分类器旨在一旦训练数据可用，就学习一个将输入属性映射到类标签的模型，因此它们被称为急切学习分类器。与急切学习分类器不同，KNN 不会从数据中构建分类模型，而是通过将测试实例与 K 个训练样本进行匹配，并根据与 K 个最近邻的相似性来决定其类别。简要地说，该方法如下所示：

```text
Let (X_i, C_i) where i = 1, 2..., n be data points. X_i denotes feature values and C_i denotes labels for X_i for each i.
Assuming the number of classes as 'c'.
c_i ∈ {1, 2, 3, ......, c} for all values of i.
Let x be a point for which label is not known, and we would like to find the label class using KNN algorithms.
For i = 1 to n do
    d(x,x_i)=√(∑_{1}^{i} (x - x_i)^2)   (finding Euclidean distance)
End for
Sort n Euclidean distances in non-decreasing order.
Let k be a positive integer, take the first k distances from this sorted list.
Find those k-points corresponding to these k-distances.
Let k_i denotes the number of points belonging to the i^th class among k points i.e. k ≥ 0.
If k_i >k_j ∀i ≠ j then put x in class i.
```

### 10.3.1.3 随机森林分类器

简要地说，该方法如下所示：

```text
Precondition: A training set S := (x_1, y_1), . . . , (x_n, y_n),
features F, and number of trees in forest B.

function RandomForest(S, F)
    H ← ∅
    for i ∈ 1, . . . , B do
        S (i) ← A bootstrap sample from S
        hi ← RandomizedTreeLearn(S (i), F)
        H ← H ∪ {hi}
    end for
    return H
end function
function RandomizedTreeLearn (S, F)
    At each node:
        f ← very small subset of F
        Split on best feature in f
    return The learned tree
end function
```

该算法的工作原理如下：对于森林中的每棵树，我们从 S 中选择一个 bootstrap 样本，其中 S(i) 表示第 i 个 bootstrap 样本。然后，我们使用改进的决策树学习算法来学习一棵决策树。改进如下：在树的每个节点，不是检查所有可能的特征划分，而是随机选择特征 f ⊆ F 的某个子集，其中 F 是特征集合。然后该节点基于 f 中的最佳特征进行划分，而不是基于 F。在实践中，f 比 F 小得多。决定划分哪个特征通常是决策树学习中最耗计算量的方面。通过缩小特征集合，我们显著加快了决策树的学习速度。

在 KNN 中，输入特征向量的预测输出是特征空间中所有“K”个邻居的输出值的平均值。KNN 被用于脑机接口（BCI）中的脑波平衡应用，以对频谱图图像进行分类。它也用于通过 EEG 信号对正常脑活动进行分类。该算法曾被用于对慢性精神压力进行分类，并获得了令人满意的准确性和敏感性分析结果。KNN 算法也被用于对来自 EEG 信号的左右手运动想象特征进行分类。

SVM 使用最优超平面来分离两个类别之间的特征向量。有多种核函数可用于特征分类。SVM 中的高斯核函数已被应用于 BCI，以对 P300 诱发电位进行分类。SVM 已实现于多类别通道分析的 EEG 信号中。在一项类似的工作中，半监督 SVM 显著减少了基于 P300 的 BCI 拼写器的训练工作量。

在数据科学中，我们常常会面对成百上千甚至数百万个特征，并且希望创建一种只包含最重要特征的模型。这有三个好处。首先，它使模型更容易解释。其次，我们可以减少模型的方差，从而减少过拟合。最后，我们可以降低训练模型的计算成本（和时间）。只识别最相关特征的过程被称为“特征选择”。随机森林常被用于数据科学工作流中的特征选择，原因是随机森林使用的基于树的策略会天然地按照特征对节点纯度的提升程度进行排序。这是所有树上杂质减少的平均值。节点纯度减少最大的位置发生在树的起始处，而纯度减少最小的位置发生在树的末端。因此，通过修剪特定节点以下的树，我们可以创建最重要特征的子集。

## 10.3.2 状态转换机

机器（M）可以用以下六元组来描述。

$$M = [Q, \Sigma, \Gamma_{old}, \Gamma_{new}, F, T]$$

其中：

- $Q$ = 有限数量的情绪状态：{Neutral（中性）, Harmony（和谐）, Depressed（抑郁）, PositiveEmotion（积极情绪）, NegativeEmotion（消极情绪）等}
- $\Sigma$ = 有限数量的通道：{FP1, FP2, T7, T8, F3, F4, F7, F8, PO7}。
- $\Gamma_{old}$ = 通道的旧值。
- $\Gamma_{new}$ = 在固定的（“T”）时间间隔后的通道新值。
- $F$ = 转换函数，描述如下。
- $F$: $(q_1 * \Sigma^* * \Gamma_{old} * \Gamma_{new} * T) \rightarrow q_2$，其中 $q_1, q_2 \subset Q$，当前状态 = $q_1$，下一状态 = $q_2$。
- $T$ = 状态变化的固定时间间隔。

在情绪状态转换机模型中，“中性（Neutral）”是情绪的起始状态，从该状态出发，人类情绪可以基于大脑半球特定区域中 alpha/beta/gamma/delta 波的激活而转变为不同状态。系统在固定时间间隔内捕获特定通道信号值的增强或减弱，然后将当前状态、通道当前值和新值传递给转换函数。接着，机器的转换函数调用所提出的转换函数算法，该算法将根据给定输入决定状态是否改变。图 10.4 展示了一个情绪状态转换机的模型。

其中：

- {Happy, Joy} ⊂ PositiveEmotion（积极情绪）
- {Fear, Sad, Anxiety} ⊂ NegativeEmotion（消极情绪）
- {Love, Serenity} ⊂ Harmony（和谐）

该机器没有预定义的最终状态，因为人的情绪可以在固定时间间隔后从中性状态转变为任何状态（积极、消极、抑郁和和谐），而在该特定时间实例下，该状态就是机器的最终状态。

### 10.3.2.1 基于通道值在固定时间间隔内进行情绪状态转换的所提算法

- **输入：** 当前状态和新状态、时间间隔、通道名称及其相应的当前值和新值（固定时间间隔后）。
- **输出：** 对于正确的输入，机器将转移到下一状态；对于错误的输入，则保持原状态。

