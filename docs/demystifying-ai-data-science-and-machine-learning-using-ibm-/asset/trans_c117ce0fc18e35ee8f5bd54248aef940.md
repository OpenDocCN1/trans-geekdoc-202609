

# 按照以下步骤创建 Multiplot 节点：

1.  打开“Airline_Explore”流。我们应该已经创建了数据节点和 Type 节点。

2.  向流中添加一个 `Multiplot` 节点，并将其连接到 `Type` 节点。

3.  打开 `Multiplot` 节点的设置窗口。

4.  在 **Plot（绘图）** 选项卡上，选择 **Age（年龄）** 作为 X 字段，然后选择 **Price sensitivity（价格敏感度）** 和 **Shopping amount at the airport（机场购物金额）** 作为 Y 字段。

![](images/ufig4_31.jpg)

1.  选择 **Sample（采样）**（为缩短运行时间，因为该节点使用所有数据运行时将需要更多时间）。

2.  单击 **Apply（应用）** 和 **Run（运行）**。

多图表如 [图 4.17](#chapter4.xhtml#fig4_17) 所示。在该图表中，我们可以观察到 **Price sensitivity（价格敏感度）** 信息未清晰呈现，图表似乎更强调 **Shopping amount at the airport（机场购物金额）**。出现此问题的原因是这两个 Y 字段具有不同的刻度，导致图表难以以有意义的方式同时显示这两个字段。

![FIGURE 4.17 Multiplot node for Price sensitivity and Shopping amount at the airport over Age (non-normalized). Return to text.⏎](images/fig4_17.jpg)

图 4.17 基于 **Age（年龄）** 的 **Price sensitivity（价格敏感度）** 和 **Shopping amount at the airport（机场购物金额）** Multiplot 节点（未归一化）。[返回正文.⏎](#chapter4.xhtml#b4fig4_17)

为解决此问题，我们需要对数据进行归一化，以确保 Y 字段处于同一刻度。在设置窗口中，勾选标记为 **Normalize（归一化）** 的复选框，然后再次运行 `Multiplot` 节点。结果如 [图 4.18](#chapter4.xhtml#fig4_18) 所示。正如您所见，Y 字段（**Shopping amount at airport（机场购物金额）** 和 **Price sensitivity（价格敏感度）**）的数据已归一化至相同刻度，范围为 0 到 1。此调整使我们能在同一图表中清晰地查看这两个变量在不同年龄段的模式。

![FIGURE 4.18 Multiplot node for Price sensitivity and Shopping amount at the airport over Age (normalized). Return to text.⏎](images/fig4_18.jpg)

图 4.18 基于 **Age（年龄）** 的 **Price sensitivity（价格敏感度）** 和 **Shopping amount at the airport（机场购物金额）** Multiplot 节点（已归一化）。[返回正文.⏎](#chapter4.xhtml#b4fig4_18)

## 使用 Data Audit 节点进行快速图表探索

![](images/ufig4_32.jpg)

您可能会问：如果我们想一次性查看数据集中所有变量的分布，以检查其分布情况和缺失值，该怎么办？SPSS Modeler 提供了一种使用 `Data Audit` 节点同时生成所有这些图表的方法，而无需像之前那样手动逐个创建图表。

`Data Audit` 节点可对数据进行全面审查。这些信息以矩阵形式呈现，易于理解、可排序，且有利于生成详细图表以及一系列数据准备节点。

*   **Audit（审计）** 选项卡呈现汇总统计、直方图和分布图，提供对数据的初步洞察。此外，报告还包含位于字段名称前的存储图标。

*   **Quality（质量）** 选项卡详细列出异常值、极端值和缺失值，并提供解决这些问题的工具。

![](images/ufig4_33.jpg)

当您需要快速可视化和评估多个变量的分布，而无需为每个变量创建单独的图表时，此功能特别有用。通过运行 `Data Audit` 节点，您可以高效地查看频率分布，并同时识别数据集中所有变量的潜在问题，如偏度或异常值。

按照以下步骤添加并设置 `Data Audit` 节点。

1.  打开“Airline_Explore”流。我们应该已经创建了数据节点和 `Type` 节点。

2.  从节点面板的 Output（输出）组中，向流中添加 `Data Audit` 节点，并将其连接到 `Type` 节点。

3.  打开 `Data Audit` 节点的设置窗口。

4.  在 **Settings（设置）** 选项卡上，保持 Default（默认）设置，这将在分析中包含所有字段。

5.  勾选 **Advanced statistics（高级统计）** 复选框。

    ![](images/ufig4_34.jpg)

6.  在 **Quality（质量）** 选项卡上，确保勾选 **Missing values: Count of records with valid values（缺失值：有效值记录计数）** 和 **Breakdown counts of records with invalid values（无效值记录细分计数）** 这两个复选框。

7.  单击 **Apply（应用）** 和 **Run（运行）**。

这种方法对于同时查看所有变量的分布非常有效。[图 4.19](#chapter4.xhtml#fig4_19) 显示了 **Airline recommendation（航空公司推荐）** 数据集的这些多图表结果。您可以看到跨多个窗口的所有变量的直方图和条形图。展开每个窗口以查看该变量的详细图表。请记住，条形图用于分类变量，而直方图用于连续变量。

![FIGURE 4.19 Results of the quick chart explorer. Return to text.⏎](images/fig4_19.jpg)

图 4.19 快速图表探索器的结果。[返回正文.⏎](#chapter4.xhtml#b4fig4_19)

## 使用 Data Audit 节点进行统计探索

![](images/ufig4_35.jpg)

数据可视化提供了多种图形工具，帮助我们直观呈现数据趋势和模式。然而，要选择合适的机器学习方法并确定预测建模的正确配置，探索数据的统计特征也至关重要。具体而言，我们需要查看所有变量的描述性统计，以了解其属性、识别潜在问题，并决定在 Modify（修改）步骤中是否需要进行数据转换。需考虑的关键描述性统计包括：

*样本量*

*   **针对分类变量**：每个层级的频数、百分比和缺失值。

*   **针对区间变量**：最小值、最大值、平均值、标准差、偏度、峰度和缺失值。

这些是统计学课程中涵盖的典型描述性统计。提醒一下，偏度和峰度能提供关于数据分布的洞察，以及数据是否遵循正态分布，这正是线性回归方法所要求的假设。

对于统计探索，我们在 SPSS Modeler 中使用 `Data Audit` 节点。这个多功能工具允许我们检查数据集中的变量分布和统计信息。

为进行说明，我们将运行之前创建的同一个 `Data Audit` 节点。在本例中，为了显示基本描述性统计，我在设置窗口中仅选择了“Basic statistics（基本统计）”选项。[图 4.20](#chapter4.xhtml#fig4_20) 显示了 **Audit（审计）** 选项卡下 `Data Audit` 节点的输出。它包含所有字段的度量。对于连续变量，输出显示最小值、最大值、平均值、标准差、偏度和有效案例数。对于分类变量，它显示唯一层级数和有效案例数。

![FIGURE 4.20 Descriptive statistics for all fields from the Data Audit node. Return to text.⏎](images/fig4_20.jpg)

图 4.20 来自 Data Audit 节点的所有字段的描述性统计。[返回正文.⏎](#chapter4.xhtml#b4fig4_20)

### 补充信息：缺失值、异常值和极端值

**Audit（审计）** 选项卡不直接显示无效案例（缺失值）。虽然可以使用 Excel 计算缺失案例，但 **Quality（质量）** 选项卡在“Null values（空值）”列下方便地呈现了缺失值。此信息可被复制并与描述性统计合并。此外，**Quality（质量）** 选项卡还会突出显示每个字段的异常值和极端值的数量。

![](images/ufig4_36.jpg)

## 示例：统计探索

![](images/ufig4_37.jpg)

我们使用 `Data Audit` 节点探索 **Airline recommendation（航空公司推荐）** 数据集中所有字段的描述性统计。通过结合 **Audit（审计）** 选项卡和 **Quality（质量）** 选项卡的结果，我们获得了所有字段的完整描述性统计，如 [表 4.7](#chapter4.xhtml#tbl4_7) 所示。

