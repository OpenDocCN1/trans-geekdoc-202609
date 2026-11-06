
## 关于 `Create Validation from Training` 的说明

注：`Create Validation from Training` 属性初始时默认被选中，但滑块按钮要到选择了另一种方法后才会被激活。该属性指定是否应从传入的训练数据中创建验证样本。即使数据已分区，也建议创建此验证集，以便仅使用训练分区进行变量选择，而原始验证分区可用于建模。

## 变量选择过程

4. 运行 `Variable Selection` 节点，并在完成后查看结果。

5. 展开 `Variable Selection` 表。该表包含每个变量的输出角色。表的顶部是节点选择的输入变量。这些变量在 `Reason` 列中有一个空白单元格。

![图 1.1 一些 JMP 帮助选项](Images/Image1060.png)

6. 在 `Variable Selection` 表中向下滚动。它显示了节点拒绝的变量。拒绝原因显示在 `Reason` 列中。下面仅显示被拒绝变量的一部分。

![图 1.1 一些 JMP 帮助选项](Images/Image1069.png)

`Variable Selection` 表显示了因变量选择和预筛选过程（本例中已关闭）而被拒绝的变量，以及拒绝原因。这除了 `Variable Selection` 节点未处理的其他变量之外。

请记住，执行的是顺序选择（默认），并且被无监督方法拒绝的任何变量都不会被后续的监督方法使用。被监督方法拒绝的变量在 `Reason` 列中以组合准则（本例中为至少一个）表示。如果您想查看它们是否被每种方法选中或拒绝，请查看 `Variable Selection Combination Summary` 表。

7. 恢复 `Variable Selection` 表的视图。

8. 展开 `Variable Selection Combination Summary` 表。对于每个变量，该表包括所使用每种方法的結果（`Input` 或 `Rejected`）、每种结果的总计数以及最终输出角色（`Input` 或 `Rejected`）。最后，结果中还提供了每种选择方法的具体输出。下面仅显示部分变量。

![图 1.1 一些 JMP 帮助选项](Images/Image1081.jpg)

表中第一个变量同时被快速监督选择和线性回归选中，因此被选为输入（上图所示）。对于被两种方法都拒绝的任何变量，其输出角色为 `Rejected`。如果一个变量仅被其中一种选择方法选中，而未被另一种选中，则其输出角色为 `Input`。这是因为属性 `Combination criterion` 被设置为 `Selected by at least 1`。

9. 恢复 `Variable Selection Combination Summary` 表的视图并关闭结果。

10. 通过点击 `Run pipeline` 按钮运行管道。

11. 打开 `Model Comparison` 节点的结果。

![图 1.1 一些 JMP 帮助选项](Images/Image1093.png)

12. 关闭 `Model Comparison` 节点的结果。

![图 1.1 一些 JMP 帮助选项](Images/Image11001.png)

![图 1.1 一些 JMP 帮助选项](Images/Image733.png)

## Demo 4.3：保存管道到 Exchange

当前的 `Starter Template` 管道用于多个机器学习算法演示。在本演示中，您将 `Starter Template` 管道保存到 `Exchange`，以便其他用户可以使用。

1. 点击名称 `Starter Template` 旁边的 `Options` 按钮。选择 `Save to The Exchange`。

![图 1.1 一些 JMP 帮助选项](Images/Image1115.png)

2. 将管道名称更改为 `CPML demo pipeline`，并在描述中输入 `This pipeline was created in the CPML class. It includes a logistic regression model and some data preparation.` 点击 `Save`。

![图 1.1 一些 JMP 帮助选项](Images/Image1123.png)

3. 要在 The Exchange 中查看已保存的管道，请点击位于 `Data` 选项卡旁边的快捷按钮。

![图 1.1 一些 JMP 帮助选项](Images/Image1130.png)

4. 在左侧窗格中，展开 `Pipelines` 并选择 `Data Mining and Machine Learning`。

![图 1.1 一些 JMP 帮助选项](Images/Image1137.png)

新保存的 `CPML demo pipeline` 已添加到管道模板列表中。

![图 1.1 一些 JMP 帮助选项](Images/Image1144.png)

要打开管道，请右键单击其名称并选择 `Open`。或者，您也可以双击管道名称来打开它。

注：当您将管道保存到 `Exchange` 时，实际上是从管道创建了一个新模板。因此，它也将在管道模板列表中可用。

5. 要退出 `Exchange` 并返回到 `Demo` 项目，请点击名称 `The Exchange` 旁边的 `Projects` 快捷按钮。

![图 1.1 一些 JMP 帮助选项](Images/Image1152.png)

![图 1.1 一些 JMP 帮助选项](Images/Image1114.png)

## 变量聚类

另一种变量缩减方法是变量聚类。聚类是将数据集划分为称为簇的组，其中单个簇内的数据点非常相似，而不同簇中的点则不同。变量聚类将数值变量（默认）划分为不相交或层次化的簇。不同簇中的变量在给定各自簇的情况下是条件独立的。对于包含一个以上变量的每个簇，选择对该簇变异贡献最大的变量作为代表变量。所有其他变量都被拒绝。

### 图 4.12：变量聚类

![图 1.1 一些 JMP 帮助选项](Images/Image1175.png)

默认情况下，变量聚类仅对数值输入变量执行。为了使变量聚类包含分类输入变量，必须打开属性 `Include Class Inputs`。

变量聚类是一种有用的数据缩减技术，因为它能找到最适合分析的变量。它消除了共线性，降低了变量冗余，并有助于揭示数据集中输入变量的潜在结构，因为变量组揭示了数据的主要维度。

![图 1.1 一些 JMP 帮助选项](Images/Image733.png)

## Demo 4.4：聚类输入以减少数据

在本演示中，您使用 `Variable Clustering` 节点来减少建模的输入数量。

1. 返回到 `Demo` 项目并通过点击其选项卡打开 `Data Exploration` 管道。

![图 1.1 一些 JMP 帮助选项](Images/Image1194.png)

2. 在 `Data Exploration` 管道中，右键单击 `Data` 节点并选择 `Add child node > Data Mining Preprocessing > Variable Clustering`。您的管道应如下所示：

![图 1.1 一些 JMP 帮助选项](Images/Image1202.png)

3. 选择 `Variable Clustering` 节点。在属性中，您可以选择是否在分析中包含分类变量。通过选中 `Include class inputs` 框打开该选项。这意味着类别变量也用于变量聚类。

此外，清除 `Export class level indicators` 框。这指定不导出类别层级指标来替换原始类别变量。

![图 1.1 一些 JMP 帮助选项](Images/Image1209.png)

您可以使用 `Cluster identifier prefix` 属性来指定用于命名变量簇标识符的前缀，以及在 `Cluster representation` 设置为 `Cluster component` 时用于命名簇成分变量的名称。

注：在 `Model Studio` 中，类别变量的处理方式不同。单个二进制类别层级变量用于聚类过程，但原始类别变量在选择过程中会被保留或丢弃。此选择取决于包含在簇中的变量以及从每个簇中选择的变量或变量层级。
