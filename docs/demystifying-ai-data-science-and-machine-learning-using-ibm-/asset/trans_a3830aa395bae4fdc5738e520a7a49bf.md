
请参考下面的屏幕截图来设置数据分区。它将数据集划分为上述三个子样本。训练样本（占数据的 60%）用于训练模型，测试样本（20%）用于测试模型，验证样本（20%）用于最终模型评估。

![](images/ufig7_42.jpg)

253. 如[图 7.12](#chapter7.xhtml#fig7_12)和[图 7.13](#chapter7.xhtml#fig7_13)所示，Partition 节点根据 60-20-20 的比例将数据分成三个子样本。两个字段——`airline recommendation` 和 `passenger class`——各水平之间的不平衡比率在各子样本中保持一致。您也可以为其他字段创建额外的图表。因此，我们可以得出结论：这些子样本具有代表性，能代表完整数据集。

![图 7.12 推荐航空公司字段的数据分区结果。返回正文。⏎](images/fig7_12.jpg)

图 7.12 字段 `recommendation the airline` 的数据分区结果。[返回正文。⏎](#chapter7.xhtml#b7fig7_12)

![图 7.13 乘客等级字段的数据分区结果。返回正文。⏎](images/fig7_13.jpg)

图 7.13 字段 `passenger class` 的数据分区结果。[返回正文。⏎](#chapter7.xhtml#b7fig7_13)

### 建模

254. 我们的目标是构建并运行一个逻辑回归模型，目标字段为 airline recommendation。由于这是一个二元字段，我们将使用二项逻辑回归，而不是用于具有多个水平的目标字段的多项回归。

构建模型有多种方法，涉及不同的数据转换选项和 SPSS Modeler 工具。为了探索最佳方法，我将构建四个不同的逻辑回归模型并进行比较，以确定哪一个提供最佳的预测能力。[表 7.20](#chapter7.xhtml#tbl7_20) 提供了每个模型的描述和配置。

表 7.20 回归模型的描述和配置 [返回正文。⏎](#chapter7.xhtml#b7tbl7_20)

| 逻辑回归模型 | 描述 | 配置 | SPSS Modeler 工具 |
| --- | --- | --- | --- |
| Logistic 1 | 使用带有插补的数据集 | * **插补**：对 `departure delay`、`arrival delay` 和 `flight time` 进行均值插补。<br>* 对 `price sensitivity` 进行中程插补。<br>* **模型**：使用**前向逐步**方法的二项逻辑回归。 | Logistic 1 节点（建模组下的 Logistic 节点），位于 SuperNode“Missing Value Imputation”和 Partition 节点之后。 |
| Logistic 2 | 使用带有缺失值的数据集（无插补） | * 无插补（四个字段有缺失值）。<br>* **模型**：使用**前向逐步**方法的二项逻辑回归。 | Logistic 2 节点（建模组下的 Logistic 节点），位于 Filter 节点和 Partition 节点之后。 |
| Logistic 3 | 平衡速度和准确性——使用 Auto Data Prep 节点 | * **Auto Data Prep 节点**用于插补缺失值、处理异常值和标准化所有连续字段。<br>* **目标**：平衡速度和准确性（不处理异常值）。<br>* **模型**：使用**前向逐步**方法的二项逻辑回归。 | Logistic 3 节点（建模组下的 Logistic 节点），位于 Filter 节点、Auto Data Prep 节点和 Partition 节点之后。 |
| Logistic 4 | 优化准确性——使用 Auto Data Prep 节点 | * **Auto Data Prep 节点**用于插补缺失值、处理异常值和标准化所有连续字段。<br>* **Auto Data Prep 节点**用于标准化所有字段。<br>* **目标**：优化准确性（处理异常值）。<br>* **模型**：使用**前向逐步**方法的二项逻辑回归。 | Logistic 4 节点（建模组下的 Logistic 节点），位于 Filter 节点、Auto Data Prep 节点和 Partition 节点之后。 |

有了这四个回归模型，我们将创建一个综合流程，展示节点的流向和数据挖掘过程的步骤。我将提供每个模型设置配置的说明。

255. 一个重要提示：如果我们在运行分析时将 `Partition` 节点直接连接到 `Logistic` 节点，SPSS Modeler 将返回一条错误消息，指出分类输入字段的值不正确（由于字符串格式）。因此，我们需要使用 `Auto Data Prep` 节点来重新格式化这些字段。

![](images/ufig7_43.jpg)

#### 构建 Logistic 模型 1 的步骤

1. 打开 SPSS Modeler 并创建一个新流程。将流程命名为 `Airline_Regression`。
2. 将数据源文件 `AirlineRecommendation.sav` 添加到流程中。
3. 向流程中添加一个 `Type` 节点并将其连接到数据源。打开 `Type` 节点设置。
4. 256. 仔细核对 `field names`、`measurement scales` 和 `roles` 的准确性。
5. 将字段 `recommendation` 的 `role` 设置为 `Target`。所有其他字段应设置为 `Input`。
6. 使用 `Filter node` 执行替换，将 `price sensitivity` 字段中的零值替换为缺失值（参考[第 5 章](#chapter5.xhtml)）。
7. 按照前面的描述，使用 `SuperNodes` 执行插补（参考[第 5 章](#chapter5.xhtml)）。完成此步骤后，您应该会有一个名为 `Missing Value Imputation` 的 SuperNode 用于处理缺失值。
8. 向流程中添加另一个 `Type` 节点并将其连接到 SuperNode `Missing Value Imputation`。打开 `Type` 节点设置并仔细核对字段、度量和角色。
9. 向流程中添加一个 `Partition` 节点并将其连接到 `Type` 节点。打开 `Partition` 节点设置。
10. 选择 `Train, test, and validation`，并将 `training partition` 大小设置为 `60%`，`testing partition` 大小设置为 `20%`，`validation partition` 大小设置为 `20%`（有关更多详细信息，请参阅数据分区步骤）。
11. 单击 `Apply`，然后单击 `OK`。
12. 向流程中添加一个 `Auto Data Prep` 节点并将其连接到 `Partition` 节点。
13. 在 `Settings` > `Prepare Inputs & Target` 下，勾选 `Reorder nominal fields to have the smallest category first, largest last` 的复选框，并取消勾选所有其他复选框。这可确保分类输入字段具有运行 `Logistic` 节点所需的正确数字格式。

     ![](images/ufig7_44.jpg)

14. 单击 `Apply`，然后单击 `Analyze Data`。
15. 257. 向流程中添加另一个 `Type` 节点并将其连接到 `Auto Data Prep` 节点。打开 `Type` 节点设置。

     ![](images/ufig7_45.jpg)

16. 确认所有分类输入字段均已转换（我使用 `_t` 后缀表示转换后的字段）。

     ![](images/ufig7_46.jpg)

17. 从 `Modeling` 组中，向流程中添加一个 `Logistic` 节点。将其命名为 `Logistic 1` 并将其连接到 `Type` 节点。打开 `Logistic` 节点设置。
18. 在 `Model` 选项卡下，选择 `Use partition data` 和 `Build model for each split`。
19. `Procedure` 选择 `Binomial`。
20. `Method` 选择 `Forward Stepwise`。
21. 258. 选择并添加所有 `categorical inputs` 到模型中。`Base Category` 列显示这些分类输入的参考水平。您可以将其更改为 `First` 或 `Last` 水平。对于本示例，所有字段均保留 `First` 设置。

     ![](images/ufig7_47.jpg)

22. 在 `Analyze` 选项卡下，选择 `Calculate predictor importance`。
23. 单击 `Apply` 和 `Run`。
24. SPSS Modeler 将运行分析并将 `model nugget`（结果节点）添加到流程中。如果运行期间出现错误，软件将显示错误消息。
