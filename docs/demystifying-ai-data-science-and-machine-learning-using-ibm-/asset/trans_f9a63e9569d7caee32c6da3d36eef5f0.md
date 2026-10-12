

### 388. 模型选择

我们选择了在[第 8 章](#chapter8.xhtml)和[第 9 章](#chapter9.xhtml)中开发的以下树模型和神经网络模型，基于这些章节中配置的算法构建集成模型。由于我们将为每个节点创建两个集成模型，因此选择了最佳树模型 `CHAID 1`，以及两个最佳神经网络模型 `MLP 2` 和 `MLP 3`。

选定的模型如下：

*   `CHAID 1` boosting
*   `CHAID 1` bagging
*   `MLP 2` boosting
*   `MLP 2` bagging
*   `MLP 3` boosting
*   `MLP 3` bagging
*   `MLP 4` boosting
*   `MLP 4` bagging

#### 操作步骤

1.  打开“**Boston_NN**”流，另存为“**Boston_Ensemble1**”。
2.  移除所有非选定节点，仅保留上述列出的神经网络节点。
3.  从“**Boston_Tree**”流复制 **CHAID 1 节点** 并粘贴到“**Boston_Ensemble1**”流中。
4.  确保这些节点在[第 8 章](#chapter8.xhtml)和[第 9 章](#chapter9.xhtml)中设置的所有配置保持不变。

完成后，你应该会得到一个包含选定决策树和神经网络节点的流，它们已准备好使用 boosting 和 bagging 方法构建集成模型。

![](images/ufig10_20.jpg)

### 构建集成模型的步骤

确保以下节点的隐藏层、隐藏节点和交互项与[第 9 章](#chapter9.xhtml)中的配置保持一致。

*   **为 CHAID 1 (boosting) 构建 boosting 集成模型：**
    1.  打开节点设置。
    2.  在 **Build Options** 选项卡下的 **Objective** 菜单中，选择 **Enhance model accuracy (boosting)**。
    3.  389. 在 **Ensembles** 菜单中，将 **Default combining rule for continuous targets** 设置为 **Mean**。将 **Number of component models** 设置为 **100**。
    4.  点击 Apply 和 Run。

*   **为 CHAID 1 (bagging) 构建 bagging 集成模型：**
    1.  打开节点设置。
    2.  在 **Build Options** 选项卡下的 **Objective** 菜单中，选择 **Enhance model stability (bagging)**。
    3.  在 **Ensembles** 菜单中，将 **Default combining rule for continuous targets** 设置为 **Mean**。将 **Number of component models** 设置为 **100**。
    4.  点击 Apply 和 Run。

对 `MLP 2`、`MLP 3` 和 `MLP 4` 遵循相同步骤设置 boosting 和 bagging 模型。所有模型配置并运行完成后，添加单独的 Analysis 节点以生成模型拟合结果。

### 模型对比

[表 10.7](#chapter10.xhtml#tbl10_7) 展示了模型对比。注意，准确度以关联模型的解释力 (EP) 衡量，仅针对训练样本报告。由于树节点不产生此输出，因此原始 `CHAID 1` 的准确度不可用。[第 8 章](#chapter8.xhtml)和[第 9 章](#chapter9.xhtml)中的原始模型也包含在内供参考。

**表 10.7 波士顿房价数据集模型对比** [返回文本.⏎](#chapter10.xhtml#b10tbl10_7)

| Models | EP (%) (Training) | MAE (Testing) | Linear Correlation (Testing) |
| :--- | :---: | :---: | :---: |
| CHAID 1 boosting | 93.3 | 2.558 | 0.859 |
| CHAID 1 bagging | 91.2 | 2.614 | 0.851 |
| CHAID 1 | — | 3.168 | 0.781 |
| MLP 2 boosting | 96.4 | 2.006 | 0.897 |
| MLP 2 bagging | 91.5 | 2.079 | 0.905 |
| MLP 2 | 84.0 | 2.515 | 0.889 |
| MLP 3 boosting | 96.9 | 2.027 | 0.892 |
| MLP 3 bagging | 91.5 | 2.069 | 0.892 |
| MLP 3 | 85.7 | 2.418 | 0.89 |
| MLP 4 boosting | 97.0 | 2.087 | 0.892 |
| MLP 4 bagging | 93.2 | 2.381 | 0.873 |
| MLP 4 | 87.0 | 2.693 | 0.877 |

结果显示：

*   在所有情况下，集成模型均优于原始模型。
*   在集成模型中，boosting 模型的拟合指标始终优于 bagging 模型。
*   基于测试样本结果，`MLP` boosting 模型表现最佳，具有最低的 MAE，且基于训练样本结果具有第二高的准确度。
*   该模型的质量图表（[图 10.8](#chapter10.xhtml#fig10_8)）也表明其优于参考模型，使其成为总体最佳模型。

![图 10.8 MLP 2 boosting 的集成结果模型摘要。返回文本.⏎](images/fig10_8.jpg)

**图 10.8** MLP 2 boosting 的集成结果模型摘要。[返回文本.⏎](#chapter10.xhtml#b10fig10_8)

这证明了使用 boosting 和 bagging 集成方法提高关联任务中模型性能的有效性。

### 变量重要性

390. [图 10.9](#chapter10.xhtml#fig10_9) 展示了该模型的变量重要性图表。结果表明，**Lsat (square root)** 是最重要的预测变量，其次是 **ZonePr (square root)**、**Tax** 和 **CrimePC (square root)**。相反，**Charles_River (square root)** 和 **LogDistance (log N)** 属于最不重要的预测变量。这种变量重要性排序有助于我们理解哪些特征对模型预测贡献最大，从而对结果进行更明智的解读。

![图 10.9 变量重要性图表—MLP 2 boosting。返回文本.⏎](images/fig10_9.jpg)

**图 10.9** 变量重要性图表—MLP 2 boosting。[返回文本.⏎](#chapter10.xhtml#b10fig10_9)

## 章节总结

391. 集成方法涉及组合多个模型以创建更准确、更稳健的预测模型。核心思想是多个模型的集体预测可以优于任何单个模型。集成技术多种多样，包括 bagging、boosting 和 stacking。

*   **Bagging 方法** 通过在不同的训练数据子集上独立训练多个模型，然后聚合其预测来创建集成。
*   **Boosting 方法** 迭代训练弱学习器，专注于纠正前一个模型的错误。
*   **Stacking** 将多个模型的预测作为输入传递给一个更高层级的模型，通常称为 **meta-learner**（元学习器）。

集成方法具有以下优势：

1.  **改进泛化能力**：通过组合多样化模型，集成方法减少过拟合，捕捉更广泛的数据模式，降低预测方差。
2.  **稳健性**：集成模型对噪声和异常值更具韧性。聚合预测有助于缓解由噪声数据引起的错误。
3.  **通用性**：它们可应用于各种机器学习任务，如分类、关联和异常检测。其成功案例跨越金融、医疗和自然语言处理等领域。

然而，必须记住集成模型并不总是优于单个模型。其成败取决于具体数据和数据挖掘项目的目标。如前所述，不存在完美的方法；最佳模型始终相对于数据而言。因此，将集成建模纳入流程以确定其对特定任务是否有益至关重要。此外，集成建模需要仔细调整配置，尤其是在组合来自不同机器学习方法的模型时。

总之，虽然集成建模并不总能保证是最佳方法，但它在构建多个预测模型以提高预测准确性和可靠性方面，仍是一个强大且可行的选择。

## 章节讨论题

1.  集成方法在预测性能和泛化能力方面与单个模型有何不同？
2.  与单一模型相比，使用集成方法的优缺点是什么？
3.  集成方法能否有效处理不平衡数据集？如果可以，它们如何解决类别不平衡问题？
4.  讨论集成方法中的模型多样性概念。多样性如何促进集成的整体性能？

