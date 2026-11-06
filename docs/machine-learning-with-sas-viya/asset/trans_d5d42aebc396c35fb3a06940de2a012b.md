
### 间隔箱数
`Number of interval bins` 指定用于 `interval inputs` 的箱数。箱大小为 `(maximum value – minimum value) / interval bins`。你通常有很多 `interval inputs` 的形式为 `continuous values`。许多机器学习算法，包括 `decision trees`，仅在 `discrete search` 或 `variable space` 中操作。`Decision trees` 通常对 `interval inputs` 进行分箱以找到 `split points`。

![图 1.1 一些 JMP 帮助选项](Images/Image733.png)

# Demo 7.1：通过更改树结构参数改进决策树模型

在本演示中，您更改 Demo 6.1 流程中刚刚添加的 `Decision Tree` 节点的默认设置。您修改树结构参数并将此模型性能与之前构建的模型进行比较。

1. 回顾一下，基于默认设置的先前模型在 `VALIDATE` 分区上实现了 0.0661 的平均平方误差。
2. 通过修改决策树模型的一些设置来尝试改进模型的性能。在 `Decision Tree` 节点的属性窗格中展开 `Splitting Options` 属性。
3. 将 `Maximum depth` 从 10 增加到 14。

这指定 14 为节点中的最大世代数。原始节点 `generation 0` 称为 `root node`。`root node` 的子节点是第一代。可能的值范围为 1 到 50。
4. 将 `Minimum leaf size` 从 5 增加到 15。

这指定 15 为叶节点可以拥有的训练观测值的最小数量。
5. 将 `Number of interval bins` 从 20 增加到 100。

这指定 100 为用于 `interval inputs` 的箱数。箱大小为 `(maximum value – minimum value) / interval bins`。你通常有很多 `interval inputs` 的形式为 `continuous values`。许多机器学习算法，包括 `decision trees`，仅在 `discrete search` 或 `variable space` 中操作。`Decision trees` 通常对 `interval inputs` 进行分箱以找到 `split points`。

![图 1.1 一些 JMP 帮助选项](Images/Image737.png)

6. `Quantile` 是默认的 `interval bin` 方法，它对 `interval input` 变量进行分箱，使得每个箱中的观测值数量大致相等。`Bucket` 是另一种方法，它将 `interval input` 变量分箱为固定宽度的箱。运行 `Decision Tree` 节点。
7. 打开 `Decision Tree` 节点的结果。
8. 单击 `Assessment` 选项卡，并在 `Fit Statistics` 表中查看使用平均平方误差的模型性能。（您可能需要展开 `Fit Statistics` 表。）

![图 1.1 一些 JMP 帮助选项](Images/Image746.png)

调优决策树模型在 `VALIDATE` 分区上的平均平方误差为 0.0650。与使用默认设置的第一个模型相比，该拟合统计量略好（更小）。
9. 关闭结果窗口。

![图 1.1 一些 JMP 帮助选项](Images/Image889.png)

# 通过更改递归划分参数改进决策树模型

改进决策树模型最常见的方法是通过调整定义分割的递归划分参数来修改其生长。分割基本上由不纯度驱动。不纯度是节点上标签同质性的度量。使用了三种主要技术：

- `Gini Impurity`
- `Entropy`
- `Variance`

为了改进模型，请尝试更改划分参数。下面简要讨论了递归划分的工作原理，然后快速讨论了三种最常用的技术及其最佳使用时机。更多细节可在附录中找到。

## 详情：递归划分

递归划分是拟合决策树所使用的标准方法。递归划分是一种自上而下、贪婪的算法。贪婪算法是在每一步都做出局部最优选择的算法。从 `root node` 开始，会检查涉及单个输入的多个分割。找到 `root node` 的分割点是递归划分的第一步。对于 `interval inputs`，分割是输入值的互不相交范围。对于名义输入，分割是输入类别的互不相交子集。各种分割搜索策略可用于确定候选分割集。分割准则用于选择分割。分割准则衡量子节点中目标分布变异性的减少。目标是减少变异性，从而提高子节点中的纯度。然后根据所选分割对 `root node` 中的案例进行划分。

图 7.1：根节点分割

![图 1.1 一些 JMP 帮助选项](Images/Image7611.png)

`root-node` 分割对应于输入空间的划分，其中边界垂直于一个输入维度。结果是一棵深度为 1 的树（因此术语 `1-deep space`）。

图 7.2：1-深度空间

![图 1.1 一些 JMP 帮助选项](Images/Image769.jpg)

该过程重复进行。深度由停止规则控制，后面会讨论。

### Gini 不纯度或指数

Gini 不纯度是对分类数据的变异性度量（由著名意大利统计学家 Corrado Gini 于 1912 年提出）。简单来说，Gini 不纯度是节点中不纯度的度量。其公式为：

![图 1.1 一些 JMP 帮助选项](Images/Image778.png)

其中 `J` 是节点中存在的类别数，`p` 是节点中类别的分布。

实际上，我们会评估具有不同阈值值的连续变量和分类变量的所有水平的不同分割。然后选择在子节点中提供最低加权不纯度的分割。

### 熵

在决策树中分割节点的另一种流行方法是熵。熵是系统中随机性的度量。熵的公式为：

![](Images/Entropy_Formula.jpg)

其中 `C` 是节点中存在的类别数，`p` 是节点中类别的分布。

### 方差

Gini 不纯度和熵在分类场景中效果很好。但回归呢？在回归情况下，最常用的分割度量只是节点的加权方差。这也说得通。我们希望分割后节点中的变异最小。

![](Images/Variance_formula.jpg)

在图 7.3 中，目标具有 `interval` 测量水平，分割标准基于减少子节点中目标的方差。

图 7.3：方差减少

![图 1.1 一些 JMP 帮助选项](Images/Image785.png)

当目标具有 `interval` 测量水平时，分割标准可以基于减少子节点中目标的方差。还提出了其他更稳健的离散度度量，例如最小绝对偏差 (`LAD`)（Breiman et al. 1984）。有关不纯度减少度量的更多细节可在附录中找到。

| Model Studio：分割标准 |
| --- |
| 总之，这些是在 `Model Studio` 中生长决策树的选项。对于分类响应，可用的标准是 `CHAID`、`CHISQUARE`、`ENTROPY`、`GINI` 和 `IGR`（信息增益比）。默认值为 `IGR`。对于连续响应，可用的标准是 `CHAID`、`FTEST` 和 `VARIANCE`。默认值为 `VARIANCE`。`CHAID` 使用分类树的卡方统计量值或回归树的 F 统计量值。基于显著性水平，卡方或 F 统计量的值用于合并预测变量的相似水平，直到拟议分割中的子节点数达到指定为最大可能分支的数量。最终分割的 `p-values` 决定分割的变量。使用 `p-value` 的分割标准（卡方、`CHAID` 或 F 检验）可以在确定分割后请求对变量的 `p-value` 进行 Bonferroni 调整。`CHISQUARE` 使用卡方统计量来分割每个变量，然后使用对应于所得分割的 `p-values` 来确定分割变量。 |

