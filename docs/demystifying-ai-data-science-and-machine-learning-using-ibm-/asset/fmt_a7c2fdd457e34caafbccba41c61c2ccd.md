
除了直方图之外，另一个用于指示数据偏度和识别潜在异常值的有用图形工具是箱线图，也称为须图。箱线图以图形方式表示数据集的五数概括，包括最小值、下四分位数（Q1）、中位数、上四分位数（Q3）和最大值。此外，箱线图还会突出显示任何被视为异常值的观测值。

![](images/ufig4_25.jpg)

让我们创建两个与航空公司会员等级相关的箱线图。第一个将展示按航空公司会员等级划分的年龄分布。要使用 Graphboard 节点创建箱线图，请遵循以下步骤：

1. 打开“Airline_Explore”流。我们应该已经创建了数据节点、Type 节点和 Graphboard 节点。

2. 打开 **Graphboard** 节点的设置窗口。

3. 在 **Basic** 选项卡上，在左侧选择 **Age** 和 **Airline status** 字段（按住 Shift 键可同时选择两者），然后在右侧选择 **Boxplot** 图表选项。

4. 点击 **Apply** 和 **Run**。

如 [Figure 4.10](#chapter4.xhtml#fig4_10) 所示，中位数和四分位距（箱体）居中，表明数据呈对称分布。四分位距在四个航空公司会员等级中似乎保持一致。值得注意的是，Silver 乘客类别仅有一个异常值（须线外的数据点）。

![FIGURE 4.10 Box plots for Age by Airline status. Return to text.⏎](images/fig4_10.jpg)

FIGURE 4.10 Box plots for **Age** by **Airline status**. [Return to text.⏎](#chapter4.xhtml#b4fig4_10)

如果我们遵循相同的步骤，但选择 **Number of years flying** 和 **Airline status** 字段，将生成另一个箱线图，如 [Figure 4.11](#chapter4.xhtml#fig4_11) 所示。该图显示了按航空公司会员等级划分的每年航班数量分布。您可能会观察到中位数和箱体略微偏离中心，提示数据存在不对称性。Blue 乘客的箱体比其他等级略大，表明数据方差存在差异。

![FIGURE 4.11 Box plots for Age and Average number of years flying by Airline status. Return to text.⏎](images/fig4_11.jpg)

FIGURE 4.11 Box plots for **Age** and **Average number of years flying** by **Airline status**. [Return to text.⏎](#chapter4.xhtml#b4fig4_11)

### 饼图

![](images/ufig4_26.jpg)

饼图是以百分比形式呈现分类变量数据的有效方式，通过饼图的切片直观地表示每个类别的比例。这种格式易于理解和解读。例如，[Figure 4.12](#chapter4.xhtml#fig4_12) 显示了一个饼图，说明了乘客航空公司会员等级的百分比分布。该图表表明，大多数乘客拥有 Blue 等级，其次是 Silver、Gold 和 Platinum 等级。

![FIGURE 4.12 Pie chart for Airline status. Return to text.⏎](images/fig4_12.jpg)

FIGURE 4.12 Pie chart for **Airline status**. [Return to text.⏎](#chapter4.xhtml#b4fig4_12)

请遵循以下步骤创建饼图：

1. 打开“Airline_Explore”流。我们应该已经创建了数据节点、Type 节点和 Graphboard 节点。

2. 打开 Graphboard 节点的设置窗口。

3. 在左侧选择 **Airline status** 字段，然后在右侧选择 **Pie of Counts** 图表选项。

4. 点击 **Apply** 和 **Run**。

要显示每个航空公司会员等级的百分比，您可以获取图表数据并使用 Excel 计算百分比（参见 [Table 4.7](#chapter4.xhtml#tbl4_7)）。如表所示，大多数乘客拥有 Blue 等级（67.08%），其次是 Silver（20.86%）、Gold（8.71%）和 Platinum（3.35%）。

TABLE 4.7 Graph Data for Airline Status [Return to text.⏎](#chapter4.xhtml#b4tbl4_7)

| Airline Status | Count | Percent |
| --- | --- | --- |
| Blue | 83,490 | 67.08 |
| Silver | 25,967 | 20.86 |
| Gold | 10,837 | 8.71 |
| Platinum | 4,170 | 3.35 |

### 折线图——趋势分析

![](images/ufig4_27.jpg)

在分析随时间收集的数据时，折线图是可视化事件或事故趋势的绝佳选择。折线图用线条连接一系列数据点，呈现顺序值，有助于识别趋势。在此图表类型中，x 轴代表值的顺序进展。

例如，[Figure 4.13](#chapter4.xhtml#fig4_13) 说明了从 2020 年 1 月 1 日到 2022 年 3 月 1 日国内和国际航班的趋势。观察可知，当 COVID-19 大流行于 2020 年初开始时，两类航班数量均大幅减少。进入 2021 年末，随着疫苗接种工作在全国范围内扩大，旅行需求激增，导致每日航班增加。这种上升趋势持续到 2022 年，上半年记录的航班更多。折线图使我们能够分析随时间变化的数据趋势，监控事件或事故的变化，并检测数据中的噪声。在本例中，两个变量绘制在同一张图表上以供比较。显而易见，国际航班始终低于国内航班，且随时间的波动较小。

![FIGURE 4.13 Line chart for domestic and international flights over time. Return to text.⏎](images/fig4_13.jpg)

FIGURE 4.13 Line chart for domestic and international flights over time. [Return to text.⏎](#chapter4.xhtml#b4fig4_13)

值得注意的是，折线图需要两个变量：一个用于 x 轴，一个用于 y 轴。在本例中，时间表示在 x 轴上，而航班数量（国内和国际）表示在 y 轴上。

由于 **Airline recommendation** 数据集未按日期或年份组织，因此基于可用变量类型，折线图的应用在一定程度上受到限制。不过，我将使用该数据集演示两个折线图示例。

### 散点图

![](images/ufig4_29.jpg)

在分析两个变量之间的关系时，散点图是一种高效的图形工具。散点图显示数据点的二维分布，使用标记表示数据，并展示数据点在图表上的分散情况。

例如，考虑出发延误时间和到达延误时间之间的关系。如 [Figure 4.16](#chapter4.xhtml#fig4_16) 所示，这两个变量之间存在正相关：当航班出发延误时，往往也会到达延误。散点图显示，对于 500 分钟或更少的延误时间，这种相关性特别强，这由该范围内较高的数据点密度所表明。

![FIGURE 4.16 Scatter plot for Arrival delay by Departure delay. Return to text.⏎](images/fig4_16.jpg)

FIGURE 4.16 Scatter plot for **Arrival delay** by **Departure delay**. [Return to text.⏎](#chapter4.xhtml#b4fig4_16)

请遵循以下步骤创建该散点图：

1. 打开“Airline_Explore”流。我们应该已经创建了数据节点、Type 节点和 Graphboard 节点。

2. 打开 Graphboard 节点的设置窗口。

3. 在 **Basic** 选项卡上，在左侧选择 **Departure delay** 和 **Arrival delay** 字段（按住 Control 键可同时选择两者），然后在右侧选择 **Line chart** 选项。

4. 在 **Detailed** 选项卡上，将 X 设为 **Departure delay**，将 Y 设为 **Arrival delay**。

5. 点击 **Apply** 和 **Run**。

### Multiplot 节点

Multiplot 节点允许将多个 Y 字段绘制在单个 X 字段上。此功能可让您在单个图表中创建多个绘图，从而更轻松地同时比较不同变量。例如，如果您想在同一张图表中绘制 **Price sensitivity** 和 **Shopping amount at the airport** 随 **Age** 的变化，通常需要使用前面讨论的工具创建两个单独的图表。然而，通过使用 Multiplot 节点，您可以将这些变量组合到单个图表中。
