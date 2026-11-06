
## 文本挖掘节点配置

### 3. 滚动到列表末尾。
所有未被拒绝的文本变量都列在一起。选择 `issue_level2` 和 `resolution`。

![图 1.1 部分 JMP 帮助选项](Images/Image1388.png)

在右侧窗格中，将角色从 Text 改为 Rejected。

![图 1.1 部分 JMP 帮助选项](Images/Image1400.png)

这确保只有 `verbatims` 变量被用作 `Text Mining` 节点的输入。

### 4. 返回 Starter Template 流水线。
(`Click` `Pipelines` 选项卡，然后 `select` `Starter Template`。)

### 5. 从左侧窗格拖放一个 `Text Mining` 节点，放置在 `Imputation` 节点和 `Logistic Regression` 节点之间。

![图 1.1 部分 JMP 帮助选项](Images/Image1407.png)

### 6. 右键单击 `Text Mining` 节点并选择 `Run`。

注意：要使用您的文本挖掘特征对新数据进行评分，您可能会发现保存包含 `Text Mining` 评分代码的 `ASTORE` 二进制文件很有用。保存 `ASTORE` 文件后，您可以使用它在 `SAS Studio` 中对新的文本数据进行评分。

### 7. 打开 `Text Mining` 节点的结果。
可用窗口很多，包括 `Kept Terms` 和 `Dropped Terms` 表。这些表分别包含文本分析期间使用的术语和被忽略的术语。

![图 1.1 部分 JMP 帮助选项](Images/Image1415.png)

停用词列表会自动包含并应用于 `Text Mining` 节点中的所有语言。

注意：单词旁边的加号表示词干提取（例如，`+service` 可能代表 service、services、serviced 等）。

### 8. 展开 `Topics` 表。
该表显示由 `Text Mining` 节点创建的主题。

主题是基于在多个文档中共同出现的术语组创建的。每个术语-文档对都会为每个主题分配一个分数。然后使用阈值来确定关联是否足够强，以考虑该文档或术语是否属于该主题。因此，术语和文档可以属于多个主题。

![图 1.1 部分 JMP 帮助选项](Images/Image1422.png)

由于发现了 15 个主题，因此创建了 15 个新的输入列。输出列包含可用于下游节点输入的 `SVD` 分数。

### 9. 单击 `Output Data` 选项卡。

![图 1.1 部分 JMP 帮助选项](Images/Demo3-2-.jpg)

### 10. 单击 `View Output Data`。

![图 1.1 部分 JMP 帮助选项](Images/Image1486.png)

### 11. 再次单击 `View Output Data`。
在此步骤中，您可以选择创建要查看的数据样本。

![图 1.1 部分 JMP 帮助选项](Images/Image1493.png)

### 12. 向右滚动，直到看到以 `Score for…` 开头的变量列标题。
这些列代表由 `Text Mining` 节点创建的主题。

`SVD` 系数（分数）针对数据集中每个观测值显示所发现的 15 个主题。这些列会传递给后续节点。

![图 1.1 部分 JMP 帮助选项](Images/Image1500.png)

### 13. 关闭 Results 窗口。

### 14. 或者，使用 `Manage Variables` 节点查看是否向数据添加了 15 个新的区间输入列。
右键单击 `Text Mining` 节点并选择 `Add child node`  `Data Mining Preprocessing`  `Manage Variables`。

当窗口出现时，在 `Run Node` 窗口中 `Click` `Close`。

![图 1.1 部分 JMP 帮助选项](Images/Image1510.png)

### 15. 运行 `Manage Variables` 节点，并在运行完成后查看结果。
展开 `Incoming Variables` 表。`Incoming Variables` 表顶部是 15 个新列，表示基于 `Text Mining` 节点发现的 15 个主题的 `SVD` 计算的维度。

![图 1.1 部分 JMP 帮助选项](Images/Image1519.png)

这 15 列（`COL1` 到 `COL15`）作为后续模型的新区间输入。

### 16. 恢复 `Incoming Variables` 表的视图并关闭结果。

### 17. 要运行整个流水线，请单击 `Run pipeline`。

### 18. 打开 `Model Comparison` 节点的结果。

![图 1.1 部分 JMP 帮助选项](Images/Image1530.png)

模型不一定会改进。探索最终回归模型的结果，查看是否包含其中一个文本变量。

### 19. 关闭 `Model Comparison` 节点的结果。

### 20. 打开 `Logistic Regression` 模型的结果。

### 21. 在结果中向下滚动，直到看到 `Output` 窗口。展开窗口。

### 22. 在 `Output` 窗口中向下滚动，直到看到 `Selection Summary` 表。
该表显示，由 `Text Mining` 节点创建的列之一（`COL12`）在逐步选择过程中确实进入了模型，但在对保留样本进行复杂度优化后最终被从模型中移除。该变量在第 22 步进入，但最终模型来自第 19 步，基于最小 `SBC`。

![图 1.1 部分 JMP 帮助选项](Images/Image1543.png)

### 23. 恢复 `Output` 窗口的视图并关闭 Results 窗口。

![图 1.1 部分 JMP 帮助选项](Images/Image1114.png)

## 测验

1. 下列关于 `Text Mining` 节点的陈述中，哪一项是正确的？

a. 它使您能够处理媒体集合中的音频/视频数据。

b. 它不允许术语和文档属于多个主题。

c. 它使用奇异值分解（`SVD`）转换词-文档频率矩阵以提供二进制值。

d. 它根据在多个文档中共同出现的术语组创建主题。每个术语-文档对都会为每个主题分配一个分数。

# 第 4 章：准备您的数据：提取特征

[引言](#Chapter_4.xhtml#_idTextAnchor071)

[提取特征](#Chapter_4.xhtml#_idTextAnchor072)

[Model Studio：特征提取节点](#Chapter_4.xhtml#_idTextAnchor074)

[主成分分析（PCA）](#Chapter_4.xhtml#_idTextAnchor075)

[稳健主成分分析](#Chapter_4.xhtml#_idTextAnchor076)

[自动编码器](#Chapter_4.xhtml#_idTextAnchor077)

[处理极端或异常值](#Chapter_4.xhtml#_idTextAnchor078)

[转换输入：数学函数](#Chapter_4.xhtml#_idTextAnchor079)

[转换输入：分箱](#Chapter_4.xhtml#_idTextAnchor080)

[Model Studio：“最佳”转换](#Chapter_4.xhtml#_idTextAnchor081)

[演示 4.1：转换输入](#Chapter_4.xhtml#_idTextAnchor082)

[特征选择](#Chapter_4.xhtml#_idTextAnchor084)

[详情：维度灾难](#Chapter_4.xhtml#_idTextAnchor085)

[特征选择策略](#Chapter_4.xhtml#_idTextAnchor086)

[Model Studio：特征选择](#Chapter_4.xhtml#_idTextAnchor087)

[演示 4.2：选择特征](#Chapter_4.xhtml#_idTextAnchor088)

[演示 4.3：将流水线保存到 Exchange](#Chapter_4.xhtml#_idTextAnchor089)

[变量聚类](#Chapter_4.xhtml#_idTextAnchor090)

[演示 4.4：聚类输入以减少数据](#Chapter_4.xhtml#_idTextAnchor091)

[测验](#Chapter_4.xhtml#_idTextAnchor092)

## 引言

通常，原始特征的初始（结构化）数据集可能过大且难以有效管理，需要不合理数量的计算资源。或者，数据集可能过于庞大，导致分类算法过拟合，并在出现新观测值时提供较差的外推。本章讨论如何在限制特征数量或降低输入数据维度的同时提取有用信息。

## 提取特征

特征提取是将现有特征转换到低维空间的过程，通常生成由现有特征组合而成的新特征。`SVD` 就是我们已经讨论过的一种技术。还有许多其他技术通过此类转换过程降低维度，包括本章讨论的那些技术。

| Model Studio：特征提取节点 |
| --- |

