
深层网络的每一层都是单独训练的，使用前一层的输出，或在第一层的情况下使用训练输入。然后，将单独训练的各层的权重用于初始化整个深层网络，并对所有层在原始训练示例上再次同时进行训练。当使用许多输入与数量少得多的隐藏单元结合时，作为隐藏单元输出提取的特征是对训练示例到低维空间的非线性投影。此类特征可以高度预测训练示例的类别标签。

特征提取的一个明显缺点是，模型实际的输入相对于业务问题不再有意义。然而，你可以简单地将其视为对原始输入的另一种转换，以提供给模型，在模型部署时，这必须作为评分过程的一部分予以考虑。

## 处理极端或不寻常的值

可以通过拉伸或压缩变量来改变其分布的形状，从而减少异常值或厚尾的影响，或将输入标准化到相同的范围和尺度。进行输入转换的另一个主要原因是减少模型预测中的偏差。

### 图 4.4：输入转换

![图 1.1 一些 JMP 帮助选项](Images/Image764.png)

输入变量的转换是常见的数据预处理任务。在机器学习中，常用的有两种变量转换类型：
● 数学转换，例如平方、平方根、对数或倒数
● 分箱，例如桶分箱、分位数分箱或基于树的分箱

`Log`、`Log10`、`Square root` 和 `Inverse square root` 会为变量添加偏移量以确保正值。`Inverse` 和 `Inverse square` 会为变量添加偏移量以确保非零值。这可以防止在输入变量值为零时转换过程中产生缺失值。

### 转换输入：数学函数

下图中的简单示例显示了一个变量分布，该分布呈正偏态。

### 图 4.5：转换输入：数学函数

![图 1.1 一些 JMP 帮助选项](Images/Image771.png)

对数转换可减少其偏度。分布对称或接近对称时，通常比偏态分布更容易处理和解释。极端的输入分布在预测建模中通常存在问题。一种更简单且 arguably 更有效的方法是对有问题的输入进行转换或正则化以消除极端值。然后，可以使用转换后的输入代替原始输入准确拟合预测模型。这不仅减轻了极端情况的影响，而且还在原始输入尺度上创建了输入与目标之间期望的渐近关联。

### 转换输入：分箱

下方的简单示例显示了一个变量 `Age`，其范围从 0 到无穷大。（实际上，`Age` 不会完全等于零也不会接近无穷大，但此示例用于说明如何将具有较大范围的连续变量转换为分箱。）`Age` 变量被转换为一个新变量，该变量仅取四个值，由 1 到 4 的分箱表示。当原始 `Age` 变量落入某个年龄范围时，分箱后的 `Age` 版本 simply 取其所属分箱的值。

### 图 4.6：转换输入：分箱

![图 1.1 一些 JMP 帮助选项](Images/Image779.png)

分箱可以有多种方式。在一种情况下，分箱本身宽度相等，但每个分箱内的频数可以变化。（这种类型的分箱称为桶分箱。）另一种方法是使分箱的宽度不同，但每个分箱中观测值的频数保持一致。（这种类型的分箱称为分位数分箱。）

分箱可以出于多种原因进行。它可用于对变量的缺失值进行分类，减少异常值对模型可能产生的影响，或说明变量之间的非线性关系。变量的分箱版本也比原始数值变量具有更小的方差。

### Model Studio：“最佳”转换

| Model Studio：“最佳”转换 |
| --- |
| “Best” 并不是真正的转换，而是一种方法或流程，用于为区间输入选择最佳转换。在 `Transformations node`（Demo 4.1 中显示）中，此方法可通过 Default interval inputs method 属性选择“Best”来访问。指定后，`Best` 方法将应用于进入该节点的所有区间输入，除非通过 `Data tab` 或 `Manage Variables node` 在元数据中识别的特定变量转换所覆盖。有关更多信息，请参阅 `https://communities.sas.com/t5/SAS-Communities-Library/Best-transformation-a-new-feature-in-SAS-Model-Studio-8-3/ta-p/489604` 处的“Best transformation – a new feature in SAS Model Studio 8.3”。 |

![图 1.1 一些 JMP 帮助选项](Images/Image733.png) Demo 4.1：转换输入

在此演示中，您使用 `Transformations node` 对输入变量应用数值转换。

1. 通过单击其选项卡打开 Data Exploration 流程。
![图 1.1 一些 JMP 帮助选项](Images/Image826.png)
2. 运行 Data Exploration 节点。（由于在 Data tab 上应用了元数据规则，因此流程需要重新运行。）
3. 右键单击 Data Exploration 节点并选择 Results。
4. 展开 Interval Variable Moments 表。注意，其中三个 `MB_Data_Usg_M` 变量具有高度偏态。为什么只列出了三个？数据集中总共有六个。
![图 1.1 一些 JMP 帮助选项](Images/Image834.png)
5. 恢复 Interval Variable Moments 表的视图。
6. 展开 Important Inputs 图表。注意，相同的 `MB_Data_Usg_M` 变量已被选为重要变量。只有六个 `MB_Data_Usg_M` 变量中的三个列在 Interval Variable Moments 表中，因为默认情况下，Data Exploration 节点的结果中仅对发现为重要的变量进行汇总。重要性由使用 `PROC TREESPLIT` 的决策树定义。您应该转换这三个输入。
![图 1.1 一些 JMP 帮助选项](Images/Image8421.png)
注意：上图未显示整个图表。
7. 恢复 Important Variables 表的视图。
8. 关闭 Results 窗口。转换规则在 Data tab 上分配。（或者，转换规则也可以使用 Manage Variables node 分配。在 Manage Variables 窗口中，New Transform 列默认隐藏，但可以显示并使用。单击 Manage Variables 表右上角的 Manage Columns 按钮。从 Manage Columns 窗口中，New Transform 列可以从 Hidden columns 列表移动到 Displayed columns 列表。然而，请记住，如果流程保存到 Exchange，则在 Manage Variables node 中建立的规则不会被保存。）
9. 单击 Data tab。确保取消选择任何已选择的变量。如果该列当前未排序，按 Variable Name 列排序可能会有所帮助。
10. 向下滚动直到看到 `MB_Data_Usg_M` 变量。虽然在 Data Exploration 节点中只有三个被认为重要，但我们将对全部六个应用 Log 转换。
11. 通过选择其名称旁边的复选框选择全部六个 `MB_Data_Usg_M` 变量。
注意：确保选择正确的变量名，这些变量名使用大写字母。存在非常相似的变量名，使用小写字母。请勿选择使用小写字母的变量名。
![图 1.1 一些 JMP 帮助选项](Images/Image849.png)
