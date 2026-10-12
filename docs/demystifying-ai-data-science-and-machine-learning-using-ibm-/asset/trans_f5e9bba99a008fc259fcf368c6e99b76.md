

## 7. 229. 执行如上所述的使用 `SuperNodes` 进行的插补和转换。完成这些步骤后，你应该拥有用于插补的 `SuperNode Missing Value Imputation` 和用于归一化的 `SuperNode Supernode_Transform`。

## 8. 向流中添加另一个 `Type` 节点并将其连接到 `SuperNode Supernode_Transform`。打开 `Type` 节点设置。

## 9. 由于转换后的数据用于大多数字段（`Imv`、`Age` 和 `Tax` 除外）来训练回归模型，请将 `unused fields`（未使用字段）的角色设置为 `None`。此步骤可确保 SPSS Modeler 在下一次分析中不使用这些字段。预定义的 `Target`（目标）和 `Input`（输入）字段将传递给下一个节点进行分析。

![](images/ufig7_24.jpg)

## 10. 单击“应用”，然后单击“确定”。

## 11. 230. 向流中添加一个 `Partition` 节点并将其连接到此 `Type` 节点。打开 `Partition` 节点设置。

## 12. 选择 `Train and test`（训练和测试），并将 `training partition size`（训练分区大小）设置为 `60`，将 `testing partition size`（测试分区大小）设置为 `40`（详情请参阅上文的数据分区步骤）。

## 13. 单击“应用”，然后单击“确定”。

## 14. 从 `Modeling`（建模）组中，向流中添加一个 `Regression` 节点，将其命名为 `Regression 1`，并将其连接到 `Partition` 节点。打开 `Regression` 节点设置。

![](images/ufig7_25.jpg)

## 15. 在 `Model`（模型）选项卡下，选择 `Use partition data`（使用分区数据）、`Build model for each split`（为每个分割构建模型）和 `Include constant in equation`（在方程中包含常数项）。

## 16. 将 `Method`（方法）选择为 `Stepwise`（逐步法）。

## 17. 在 `Analyze`（分析）选项卡下，选择 `Calculate predictor importance`（计算预测变量重要性）。

## 18. 单击“应用并运行”。

## 19. SPSS Modeler 将运行并向流中添加模型粒子（结果节点）。如果运行模型时出现错误，软件将显示错误消息。

![](images/ufig7_26.jpg)

## 20. 231. 从 `Output`（输出）组中，向流中添加一个 `Analysis` 节点并将其连接到模型粒子 `Regression 1`。此节点将比较训练样本和测试样本之间的模型性能。打开 `Analysis` 节点设置。

## 21. 在 `Analysis` 选项卡下，选择 `Performance evaluation`（性能评估）、`Evaluation metric`（评估指标）、`Confidence figures`（置信度数值）和 `Separate by partition`（按分区分离）。

![](images/ufig7_27.jpg)

## 22. 单击“应用并运行”。

## 提取模型拟合结果

Analysis 节点的结果显示了模型在训练样本和测试样本上的性能。在此输出中，字段 `$E-Imv` 代表目标字段的 `predicted value`（预测值），而 `Imv` 是目标字段的 `actual (observed) value`（实际/观测值）。大多数指标都很直观。请记住，`error`（误差）指的是观测值与预测值之间的差异。

以下是关键指标的简要说明：

*   **Minimum error**（最小误差）：最小的误差值。
*   **Maximum error**（最大误差）：最大的误差值。
*   **Mean error**（平均误差）：所有记录误差的平均值，指示模型中是否存在潜在的系统性偏差。
*   **Mean absolute error (MAE)**（平均绝对误差）：所有记录绝对误差的平均值，显示误差的平均幅度。
*   **232. Standard deviation**（标准差）：误差的标准差。
*   **Linear correlation**（线性相关）：预测值与实际值之间的线性相关性，范围从 -1 到 1。
*   **Occurrences**（案例数/频数）：样本量。在本例中，304 条记录用于训练模型，202 条记录用于测试模型。

正如 [第 6 章](#chapter6.xhtml) 所述，仅凭这些指标并不足以理想地评估模型性能和进行比较。具体而言，对于关联模型，建议使用 `RMSE`、`MAPE`、`RSE` 和 `EP` 等指标。此外，应使用线性回归特有的指标——包括 `F-test`（F 检验）、`R²` 和 `adjusted R²`（调整后 R 平方）。然而，由于 SPSS Modeler 不通过 Analysis 节点输出直接提供 `RMSE`、`MAPE`、`RSE` 和 `EP`，我们需要将预测输出导出到 Excel 并单独计算这些指标（请参阅本章后面的“将 Regression 1 输出导出到 Excel 的步骤”部分）。

有一点需要注意：回归特有的指标，如 `F-test`、`R²` 和 `adjusted R²`，仅针对训练样本提供。虽然这些可用于回归模型的初步评估，但它们不适合模型比较和可靠性评估。

## 提取 F 检验、R² 和调整后 R²

要从 SPSS Modeler 中提取 `F-test`、`R²` 和 `adjusted R²`，这些值存储在模型粒子中，而非 Analysis 节点中。你可以访问模型粒子以查看这些回归特有的指标。

请按照以下步骤提取 `Regression 1` 模型的 `F-test`、`R²` 和 `adjusted R²`。请注意，这些结果基于训练样本，我们可将其用于模型比较。

1.  双击流中的模型粒子 `Regression 1`。Regression 1 结果窗口将打开。
2.  在 `Advanced`（高级）选项卡下，选择 `Regression/Model Summary`（回归/模型摘要）。你将看到算法在逐步过程中运行了九个模型以找到最终模型。模型 9 是最终模型，其 `R² = 0.735`，`adjusted R² = 0.727`。

![](images/ufig7_28.jpg)

3.  选择 `ANOVA tab`（ANOVA 选项卡），你可以在其中查看模型 9 的 `F-test`，其值为 `90.629`。

如前所述，在线性回归中，`R²` 等同于 `EP`，而 `RSE` 可计算为 `1 − EP`。因此，我们得到 `EP = R² = 0.735` 和 `RSE = 1 − EP = 1 − 0.735 = 0.265`。换句话说，基于训练样本结果，该模型的 `EP 为 73.5%`，意味着它可以根据预测变量的方差解释目标字段（`Imv`）73.5% 的方差。

这就是提取这些指标的方法。一旦我们确定了 `champion model`（冠军模型），我将深入探讨回归模型的细节。

## 回归模型 2、3 和 4 设置

**233.** 按照为 `Regression 1` 概述的相同步骤，设置和配置 `Regression Models 2, 3, and 4`，使用 [表 7.10](#chapter7.xhtml#tbl7_10) 中描述的配置和节点。具体如下：

### Regression 2

*   使用未归一化的插补数据。
*   使用 `Regression node`（回归节点）并采用 `Stepwise method`（逐步法）。

### Regression 3

*   使用 `Auto Data Prep node`（自动数据准备节点），目标设置为 `Balance speed and accuracy`（平衡速度与准确性）（无异常值处理）。
*   使用 `Regression node` 并采用 `Stepwise method`。

### Regression 4

*   使用 `Auto Data Prep node`，目标设置为 `Optimize for accuracy`（优化准确性）（含异常值处理）。
*   使用 `Regression node` 并采用 `Stepwise method`。

## 运行模型

分别运行每个模型，并添加 `Analysis` 节点，如 `Regression 1` 所述。模型运行完成后，按照相同步骤从测试样本的 `Analysis` 节点提取模型拟合指标。

![](images/ufig7_29.jpg)

## 冠军模型

为了模型比较，我将使用基于测试样本结果的 `MAE` 和 `linear correlation`。此外，我将包含 `F-test`、`R²` 和 `adjusted R²`，但我们必须记住，这些指标仅源自训练样本。[表 7.11](#chapter7.xhtml#tbl7_11) 展示了模型比较结果。

**表 7.11 模型比较** [返回正文.⏎](#chapter7.xhtml#b7tbl7_11)

| 模型拟合指标 | 样本 | Regression 1 | Regression 2 | Regression 3 | Regression 4 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| MAE | Testing | 3.437 | 3.976 | 3.976 | 4.406 |
| Linear correlation | Testing | 0.783 | 0.735 | 0.735 | 0.677 |
| RSE (same as R²) | Training | 0.265 | 0.434 | 0.434 | 0.484 |
| EP | Training | 0.735 | 0.566 | 0.566 | 0.516 |
| F-test | Training | 90.629 | 64.645 | 64.645 | 160.277 |
| R² | Training | 0.735 | 0.566 | 0.566 | 0.516 |

