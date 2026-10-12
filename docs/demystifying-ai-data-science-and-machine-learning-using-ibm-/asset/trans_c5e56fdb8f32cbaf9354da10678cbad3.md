

# 停止规则：选择“使用绝对值”

## CHAID 模型

### CHAID 1（默认）

在 **Build Options（构建选项）** 选项卡下：

*   **Objectives（目标）**：选择“Build a single tree（构建单棵树）”
*   **Basic（基本）**：树生长算法：`CHAID`
*   **Basic（基本）**：最大树深度：默认值 (5)
*   **Stopping rules（停止规则）**：选择“Use percentage（使用百分比）”

> **Note（注意）：** CHAID 没有剪枝选项。

### CHAID 2

在 **Build Options（构建选项）** 选项卡下：

*   **Objectives（目标）**：选择“Build a single tree（构建单棵树）”
*   **Basic（基本）**：树生长算法：`Exhaustive CHAID`
*   **Basic（基本）**：最大树深度：自定义 = 10
*   **Stopping rules（停止规则）**：选择“Use absolute value（使用绝对值）”

## C5.0 模型

### C5.0 1（默认）

在 **Model（模型）** 选项卡下：

*   选择“Use partition data（使用分区数据）”和“Build model for each split（为每个分区构建模型）”
*   **Output type（输出类型）**：Decision tree（决策树）
*   **Mode（模式）**：Simple（简单）
*   **Favor（偏向）**：Accuracy（准确率）

### C5.0 2

在 **Model（模型）** 选项卡下：

*   选择“Use partition data（使用分区数据）”和“Build model for each split（为每个分区构建模型）”
*   **Output type（输出类型）**：Decision tree（决策树）
*   **Mode（模式）**：选择 Expert（专家）
*   将剪枝严重度设置为 100
*   将每个子分支的最小记录数设置为 5
*   选择“Use global pruning（使用全局剪枝）”

## QUEST 模型

### QUEST 1（默认）

在 **Build Options（构建选项）** 选项卡下：

*   **Objectives（目标）**：选择“Build a single tree（构建单棵树）”
*   **Basic（基本）**：最大树深度：默认值 (5)
*   **Basic（基本）**：选择“Prune tree to avoid overfitting（剪枝以避免过拟合）”；Maximum surrogate（最大替代变量）= 5
*   **Stopping rules（停止规则）**：选择“Use percentage（使用百分比）”

### QUEST 2

在 **Build Options（构建选项）** 选项卡下：

*   **Objectives（目标）**：选择“Build a single tree（构建单棵树）”
*   **Basic（基本）**：最大树深度：自定义 = 10
*   **Basic（基本）**：选择“Prune tree to avoid overfitting（剪枝以避免过拟合）”；取消勾选“Set maximum difference in risk（设置最大风险差异）”；Maximum surrogate（最大替代变量）= 5
*   **Stopping rules（停止规则）**：选择“Use absolute value（使用绝对值）”

# 模型比较设置

由于所有模型使用相同的输入和相同的字段名，请遵循 [第 7 章](#chapter7.xhtml) 中描述的方法连接所有模型粒以进行比较。如下图所示，使用 **Filler（填充）** 节点重命名模型，使用 **Analysis（分析）** 节点比较模型性能，并使用 **Evaluation Graph（评估图）** 节点为所有模型生成 ROC 图和 Lift 图（提升图）。

![Diagram](images/ufig8_25.jpg)

以下是 **Filler（填充）** 节点的设置，我们在其中重命名模型以反映其各自的配置。此步骤确保每个模型在后续分析中都有清晰的标签以供比较。

![Filler Node Settings](images/ufig8_26.jpg)

# 冠军模型

构建完八个模型后，下一步是比较它们的模型拟合指标以确定冠军模型。[表 8.5](#chapter8.xhtml#tbl8_5) 显示了使用测试样本结果对这些模型的比较。和以前一样，从 **Analysis（分析）** 节点提取 `ACC`、`MR`、基尼系数和 `AUC`（ROC 指数）。敏感度、特异度和 F1 分数可以从混淆矩阵中计算得出。[图 8.7](#chapter8.xhtml#fig8_7) 和 [8.8](#chapter8.xhtml#fig8_8) 提供了所有模型的 ROC 和 Lift 对比图。

**表 8.5** 决策树算法之间的模型比较（使用测试样本的结果） [返回正文.⏎](#chapter8.xhtml#b8tbl8_5)

| 指标 | C&R Tree 1 | C&R Tree 2 | CHAID 1 | CHAID 2 | C5.0 1 | C5.0 2 | QUEST 1 | QUEST 2 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| ACC | 78.70% | 79.30% | 79.00% | 77.70% | 79.00% | 79.20% | 74.50% | 78.00% |
| MR | 21.30% | 20.70% | 21.00% | 22.30% | 21.00% | 20.80% | 25.50% | 22.00% |
| Sensitivity or TPR | 0.964 | 0.952 | 0.924 | 0.883 | 0.912 | 0.949 | 0.814 | 0.915 |
| Specificity or TNR | 0.589 | 0.615 | 0.641 | 0.659 | 0.654 | 0.617 | 0.668 | 0.628 |
| F1 | 0.827 | 0.829 | 0.823 | 0.807 | 0.821 | 0.828 | 0.771 | 0.814 |
| Gini | 0.652 | 0.665 | 0.700 | 0.671 | 0.680 | 0.618 | 0.521 | 0.617 |
| AUC (ROC index) | 0.826 | 0.832 | 0.850 | 0.836 | 0.840 | 0.808 | 0.760 | 0.808 |
| Lift | 1.577 | 1.577 | 1.639 | 1.582 | 1.587 | 1.442 | 1.422 | 1.471 |

![FIGURE 8.7 ROC comparison chart. Return to text.⏎](images/fig8_7.jpg)

**图 8.7** ROC 对比图。 [返回正文.⏎](#chapter8.xhtml#b8fig8_7)

![FIGURE 8.8 Lift comparison chart. Return to text.⏎](images/fig8_8.jpg)

**图 8.8** Lift 对比图。 [返回正文.⏎](#chapter8.xhtml#b8fig8_8)

根据结果，CHAID 2、QUEST 1 和 QUEST 2 的表现不如其他模型，ACC 最低。在剩余模型中，C&R Tree 2 和 C5.0 2 表现优于其他模型，拥有最高的 ACC。我们可以将比较范围缩小到这两个模型，它们的性能非常接近。C&R Tree 2 的预测 ACC 略高，具有更好的 ACC、更低的 MR，以及改进的敏感度和 F1 分数。这两个模型的特异度几乎相同。此外，C&R Tree 2 的基尼系数和 ROC 指数优于 C5.0 2。

有趣的是，CHAID 1 表现出最高的基尼系数，并在 ROC 和 Lift 对比图中表现最好，在这些指标上优于其他模型。然而，CHAID 1 的预测 ACC 和 F1 分数低于 C&R Tree 2 和 C5.0 2。QUEST 1 的 ROC 和 Lift 表现最差，而 C5.0 2 和 QUEST 2 的 Lift 结果也非常差。

最终，C&R Tree 2 和 CHAID 1 是主要竞争者。虽然 CHAID 1 在基尼系数、ROC 和 Lift 方面表现出色，但 C&R Tree 2 在预测 ACC 和 F1 分数方面胜出。为了演示目的，我选择 C&R Tree 2 作为冠军模型，因为它具有更高的预测 ACC 和 F1 分数。此外，与 CHAID 1 相比，C&R Tree 2 生成的树更小、更精简，而 CHAID 1 倾向于生成更大的树，更容易过拟合，也更难解释。考虑到这些模型性能接近，C&R Tree 2 是演示的更好选择。

# 冠军模型的可靠性

C&R Tree 2 三个子样本的详细模型拟合指标见 [表 8.6](#chapter8.xhtml#tbl8_6)。结果显示所有三个样本的指标一致，差异小于 1%。这种一致性证明了模型的可靠性，并确认没有过拟合的迹象。

**表 8.6** 冠军模型的模型可靠性——C&R Tree 2 [返回正文.⏎](#chapter8.xhtml#b8tbl8_6)

| 指标 | 测试 | 训练 | 验证 |
| :--- | :---: | :---: | :---: |
| ACC | 79.30% | 79.20% | 79.50% |
| MR | 20.70% | 20.80% | 20.50% |
| Sensitivity or TPR | 0.952 | 0.950 | 0.951 |
| Specificity or TNR | 0.615 | 0.618 | 0.623 |
| F1 | 0.829 | 0.827 | 0.830 |
| Gini | 0.665 | 0.670 | 0.673 |
| AUC (ROC index) | 0.832 | 0.835 | 0.837 |

# 冠军模型的有效性

下一步是通过查看验证样本的完整模型拟合指标来评估冠军模型的有效性，该验证样本被保留用于最终评估。[表 8.7](#chapter8.xhtml#tbl8_7) 展示了 C&R Tree 2 的全套指标及其性能评估。

**表 8.7** 使用验证样本结果对冠军模型 C&R Tree 2 进行模型拟合评估 [返回正文.⏎](#chapter8.xhtml#b8tbl8_7)

| 指标 | 验证样本 | 评价 | Logistic 1 Model |
| :--- | :---: | :---: | :---: |
| ACC | 79.5% | 不佳 | 76.8% |
| MR | 20.5% | 不佳 | 23.2% |
| Sensitivity or TPR | 0.951 | 优秀 | 89.3% |
| Specificity or TNR | 0.623 | 不佳 | 63.0% |
| F1 | 0.830 | 可接受 | 80.2% |
| Gini | 0.673 | 良好 | 0.667 |
| AUC (ROC index) | 0.837 | 可接受 | 0.833 |

