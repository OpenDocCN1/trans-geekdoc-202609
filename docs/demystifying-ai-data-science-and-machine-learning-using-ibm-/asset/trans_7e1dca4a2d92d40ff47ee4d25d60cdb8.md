
首先，让我们比较这两个模型生成的树。要从 **C&R Tree 1** 模型中提取树，请打开标记为 **C&R Tree 1** 的模型块。在 **Viewer** 选项卡下，您将找到该树。为了使树结构更易于查看，我以图形形式显示了带有频率信息的树（[图 8.5](#chapter8.xhtml#fig8_5)）。对模型块 **C&R Tree 1 Non-Pruned** 重复此步骤。这将为我们提供完整的、未剪枝的树（[图 8.6](#chapter8.xhtml#fig8_6)）。

![图 8.5 CART（剪枝后）的层级结构。返回正文。](images/fig8_5.jpg)

图 8.5 CART（剪枝后）的层级结构。[返回正文。](#chapter8.xhtml#b8fig8_5)

![图 8.6 完整 CART（未剪枝）的层级结构。返回正文。](images/fig8_6.jpg)

图 8.6 完整 CART（未剪枝）的层级结构。[返回正文。](#chapter8.xhtml#b8fig8_6)

那么，这两棵树在层级结构上有何不同？正如您所见，未剪枝的树更大，包含 34 个节点和 18 个叶子。由于其复杂性，分析每个分支和节点将相当具有挑战性。相比之下，剪枝后的树更紧凑且易于解释，仅包含 14 个节点和 8 个叶子。

![](images/ufig8_23.jpg)

我们使用验证结果比较了两棵树的模型拟合指标，以评估它们的差异。ACC、误分类率 (MR)、基尼系数和 AUC 直接由 Analysis 节点的输出提供。灵敏度、特异性和 F1 分数基于混淆矩阵计算得出。使用测试样本的这些结果，模型比较呈现在 [表 8.3](#chapter8.xhtml#tbl8_3) 中。

表 8.3 完整 CART 树与剪枝 CART 树的模型比较 [返回正文。](#chapter8.xhtml#b8tbl8_3)

| Metrics | Full CART Tree 1 (Non-pruned) | Pruned CART Tree 1 |
| --- | --- | --- |
| ACC | 0.786 | 0.786 |
| MR | 0.214 | 0.214 |
| Sensitivity or TPR | 0.937 | 0.960 |
| Specificity or TNR | 0.617 | 0.591 |
| F1 | 0.822 | 0.826 |
| Gini | 0.680 | 0.652 |
| AUC (ROC index) | 0.840 | 0.826 |

正如您所见，完整树和剪枝树之间的指标非常相似。两棵树显示相同的 ACC 和 MR。然而，剪枝树在灵敏度和 F1 分数方面表现略好，而其特异性略低。完整树在基尼系数和 AUC（ROC 指数）方面略占优势。总体而言，两棵树的模型拟合指标非常接近。

因此，构建完整树并不比剪枝树提供显著优势。此外，完整树大得多，使其更难解释，需要更多计算时间，并增加过拟合的风险。基于这些原因，使用剪枝树是更务实的选择。

### 场景 2：带缺失值的 CART 模型 vs. 插补数据

在本场景中，我们将比较一个保留缺失值的 CART 模型与一个使用插补数据的模型。一般来说，决策树处理缺失值的能力优于回归算法。由于决策树基于规则而非统计，它们通常不需要完整数据集即可运行。决策树通过将数据分割到不同的箱中工作，因此它们提供了多种处理缺失值的选项，而不会干扰模型构建过程。这些选项包括忽略缺失值、使用替代分割、将缺失值视为单独类别、分配默认值或应用概率加权。因此，在构建决策树时，使用插补并不一定提供任何优势。事实上，插补可能会引入偏差或增加预测误差。同样，数据归一化和异常值处理对于决策树算法可能也不是必需的。

在本场景中，我们将比较三棵构建方式不同的剪枝 CART，并评估它们的性能：

*   **C&R Tree 1**：使用插补数据，无归一化或异常值处理。
*   **C&R Tree 2**：保留缺失值，无归一化或异常值处理。
*   **C&R Tree 3**：使用目标为 **Optimize for accuracy** 的 Auto Data Prep 节点，该节点插补缺失值、调整字段刻度、归一化数据并处理异常值。

遵循我们之前使用的相同步骤，使用指定配置将 **C&R Tree 2** 和 **C&R Tree 3** 添加到流中。您的流应类似于下图所示。

![](images/ufig8_24.jpg)

运行所有三个 CART 模型，并使用 Analysis 节点提取每个模型的拟合指标。如前所述，您可以直接从 Analysis 节点的输出获得 ACC、MR、基尼系数和 AUC。要基于混淆矩阵计算灵敏度、特异性和 F1 分数，请参阅 [第 6 章](#chapter6.xhtml) 中讨论的公式。请务必使用测试样本的结果进行模型比较。[表 8.4](#chapter8.xhtml#tbl8_4) 展示了场景 2 的模型比较结果。

表 8.4 C&R Tree 1、C&R Tree 2 和 C&R Tree 3 之间的模型比较 [返回正文。](#chapter8.xhtml#b8tbl8_4)

| Metrics | CART Model Using Imputed Data (C&R Tree 1) | CART Model with Missing Values (C&R Tree 2) | CART Model Using Auto Data Prep (C&R Tree 3) |
| --- | --- | --- | --- |
| ACC | 0.786 | 0.787 | 0.786 |
| MR | 0.214 | 0.213 | 0.214 |
| Sensitivity or TPR | 0.960 | 0.964 | 0.960 |
| Specificity or TNR | 0.591 | 0.589 | 0.591 |
| F1 | 0.826 | 0.827 | 0.826 |
| Gini | 0.652 | 0.652 | 0.652 |
| AUC (ROC index) | 0.826 | 0.826 | 0.826 |

比较结果显示，**C&R Tree 1** 和 **C&R Tree 3** 具有相同的模型拟合指标，表明数据归一化和异常值处理并未提升模型性能。此外，**C&R Tree 2**（保留缺失值）略优于其他模型，具有更高的准确率、更好的灵敏度和更高的 F1 分数。这表明决策树算法通过树算法的内置方法处理缺失值比传统插补更有效。因此，保留缺失值似乎是最佳方法，我们将在第三个场景中采用它。

### 场景 3：CART vs. CHAID vs. C5.0 vs. QUEST

在本场景中，我们将比较使用四种不同算法开发的决策树模型：CART、CHAID、C5.0 和 QUEST。目标是确定哪种算法和配置最适合航空公司推荐数据集。从前面的场景中，我们确定剪枝树并在数据集中保留缺失值是构建决策树的最佳选择。因此，在本场景中，我们将仅使用包含原始缺失值的数据构建剪枝树。对于每种算法，我们将构建两棵树：一棵使用树深度、剪枝和停止规则的默认设置，另一棵使用修改后的设置以查看性能是否改进。

以下是每个模型的具体配置。遵循这些设置来设置树。然后将比较这些模型以确定表现最佳的模型。

#### CART 模型

*   **C&R Tree 1 (default)**
    *   在 **Build Options** 选项卡下：
        *   Objectives：选择 “Build a single tree”
        *   Basic：Maximum tree depth：Default (5)
        *   Basic：选择 “Prune tree to avoid overfitting”；Maximum surrogate = 5
        *   Stopping rules：选择 “Use percentage”

*   **C&R Tree 2**
    *   在 **Build Options** 选项卡下：
        *   Objectives：选择 “Build a single tree”
        *   Basic：Maximum tree depth：Custom = 10
        *   Basic：选择 “Prune tree to avoid overfitting”；取消选择 “Set maximum difference in risk”；Maximum surrogate = 5
