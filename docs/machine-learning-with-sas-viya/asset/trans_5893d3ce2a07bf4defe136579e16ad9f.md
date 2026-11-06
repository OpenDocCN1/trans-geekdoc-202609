
# 评估选项卡

在 `Assessment tab` 中，您可以找到两张图表和一张表格，用于展示所有比较模型的性能和拟合统计量。第一个图表是 `Lift Reports`，默认显示 `Response Percentage`。从菜单中，您还可以选择基于 `Captured Response Percentage`、`Cumulative Captured Response Percentage`、`Cumulative Response Percentage`、`Cumulative Lift`、`Gain` 和 `Lift` 查看模型的性能。

![图 1.1 一些 JMP 帮助选项](Images/Image10321.png)

注意：必须展开图表才能显示图例，图例指示哪条彩色线代表哪个模型以及在哪个分区上。

`Lift Reports` 图表默认显示管道中所有模型在所有数据分区上的性能。您也可以通过展开它，将图表更改为仅显示单个模型的性能，或仅显示特定分区下所有模型的性能。

7\. 展开 `Lift Reports` 图表。

![图 1.1 一些 JMP 帮助选项](Images/Image10401.png)

首先，注意图例现在可见于绘图底部，指示与每个模型对应的线条颜色以及所在的分区。此外，从右侧的列中，您可以选择仅显示单个模型的结果，或基于单个分区显示所有模型的结果。做出不同的选择以查看图表如何受影响。

8\. 恢复 `Lift Reports` 图表。

第二个图表是 `ROC Reports`，默认基于 `Accuracy`。菜单提供选项，可让您从下拉菜单中基于 `F1 Score` 和 `ROC` 查看模型的性能。

![图 1.1 一些 JMP 帮助选项](Images/Image1048.png)

这是显示 `ROC` 的 `ROC Reports` 图表。

![图 1.1 一些 JMP 帮助选项](Images/Image1055.png)

注意：与 `Lift Reports` 图表一样，您可以展开 `ROC Reports` 图表以查看颜色图例。您也可以从展开视图中选择查看单个模型或某个分区。

最后，`Fit Statistics` 表格显示所有模型基于项目中定义的数据分区（`train`、`validate` 和 `test`）的性能，针对一系列拟合统计量，例如 `Area Under ROC`、`Average Squared Error`、`Gini Coefficient` 和 `KS`。

![图 1.1 一些 JMP 帮助选项](Images/Image1062.png)

9\. 关闭结果。

![演示结束](Images/Image889.png)

![图 1.1 一些 JMP 帮助选项](Images/Image733.png)

# Demo 12.2：跨管道比较多个模型并注册冠军模型

`Pipeline Comparison` 选项卡使您能够比较每个管道创建的最佳模型。此外，它还使您能够注册冠军模型并在 `Manage Models` 工具中使用它。

注意：本演示中忽略了在练习中构建的模型。

1\. 单击 `Pipeline Comparison`。

![图 1.1 一些 JMP 帮助选项](Images/Image1087.png)

在 `Pipeline Comparison` 选项卡顶部，您可以看到每个管道的冠军模型，以及在管道比较中被视为总体冠军的模型——即冠军中的冠军。此外，还提供了多个图表和表格，总结总体冠军模型的性能，显示模型变量重要性列表，提供训练和评分代码，并显示所选最佳模型的其他结果。`Pipeline Comparison` 的默认评估度量为 `Kolmogorov-Smirnov (KS)`。

![图 1.1 一些 JMP 帮助选项](Images/Image1098.png)

显示的所有结果仅针对总体冠军模型。可能需要对所示的每个模型进行模型比较。

2\. 选择结果页面顶部显示的所有模型旁边的复选框。您还可以选择表格顶部 `Champion` 旁边的复选框。

![图 1.1 一些 JMP 帮助选项](Images/Image1110.png)

3\. 当选择多个模型时，右上角的 `Compare` 按钮将被激活。单击 `Compare` 按钮。

![图 1.1 一些 JMP 帮助选项](Images/Image11171.png)

显示 `Compare` 结果，其中可以跨每个管道的所有冠军模型比较评估统计量和图形。

![图 1.1 一些 JMP 帮助选项](Images/Image11251.png)

注意：与管道内 Model Comparison 节点的图形显示一样，此处的图形显示也可以展开以查看图例并选择要显示的信息子集。

4\. 关闭 `Compare` 结果窗口，并在窗口顶部的表格中取消选择模型，直到仅选择总体冠军模型。总体项目冠军模型在 `Champion` 列中用星号符号表示。

![图 1.1 一些 JMP 帮助选项](Images/Image1132.png)

5\. 在冠军模型注册以准备部署之前，让我们查看 `Insights tab` 提供的汇总信息。单击 `Insights tab`。

![图 1.1 一些 JMP 帮助选项](Images/Image11401.png)

`Insights tab` 包含以报告形式提供的项目、冠军模型和任何挑战者模型的汇总信息。就 `Insights tab` 而言，冠军模型是总体项目冠军模型，而挑战者模型是管道冠军，但不是总体项目冠军。

报告顶部是项目的摘要和任何项目注释的列表。关于项目的汇总信息包括目标变量、冠军模型、事件率以及项目中的管道数量。

![图 1.1 一些 JMP 帮助选项](Images/Image11471.png)

6\. 最大化 `Most Common Variables Selected Across All Models` 绘图。该绘图通过显示变量最终出现在多少个管道冠军模型中来总结项目中使用的常见变量。仅显示在管道比较中使用的模型中出现的变量。

![图 1.1 一些 JMP 帮助选项](Images/Image1154.png)

该绘图显示许多变量被管道比较中的全部四个模型使用。这些变量列在绘图顶部。仅有一个变量在管道比较中仅被一个模型使用。该变量列在绘图底部。

7\. 恢复 `Most Common Variables Selected Across All Models` 绘图。

8\. 最大化 `Assessment for All Models` 绘图。该绘图总结了每个管道的冠军模型以及总体项目冠军的模型性能。

![图 1.1 一些 JMP 帮助选项](Images/Image1162.png)

该绘图显示总体项目冠军模型是梯度提升模型，来自管道 `Lesson 3`。该模型的 `KS` 值接近 0.6。模型旁边的橙色星号表示它是项目冠军。

9\. 恢复 `Assessment for All Models` 绘图。

10\. 最大化 `Most Important Variables for Champion Model` 绘图。该绘图显示最重要的变量，由使用实际总体冠军模型计算的相对重要性确定。

![图 1.1 一些 JMP 帮助选项](Images/Image1171.png)

该绘图显示总体冠军模型最重要的变量是 `Handset Age Group`。变量 `Total Days Over Plan` 的相对重要性约为 `Handset Age Group` 重要性的 87%。这意味着对于该模型，`Total Days Over Plan` 的重要性是 `Handset Age Group` 的 0.87 倍。

11\. 恢复 `Most Important Variables for Champion Model` 绘图。

12\. 最后，报告底部是 `Cumulative Lift for Champion Model` 绘图。该绘图显示总体项目冠军模型在训练和验证分区上的累积提升。

![图 1.1 一些 JMP 帮助选项](Images/Image1180.png)

13\. 现在我们对项目及其包含的模型有了额外的洞察，我们准备进行模型部署。通过单击 `Pipeline Comparison` 选项卡返回管道比较结果。

![图 1.1 一些 JMP 帮助选项](Images/Image1191.png)
