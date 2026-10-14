
在下一章中，我们将了解回测和前向测试的具体细节，以及它们在算法交易中发挥的关键作用。随着内容的深入，我们将进一步理解如何有效地选择、处理和使用不同类型的数据，从而使你能够构建更稳健、潜在获利能力更强的交易策略。

***

**加入我们书籍的 Discord 社区**

加入书籍的 Discord 工作区，获取最新动态、优惠信息、全球科技动态、新书发布及作者专场活动：

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![](images/Discord.png)

# 第 3 章：优化交易系统、指标与自动化报告

## 简介

本章重点介绍如何优化交易系统以实现最大性能。通过利用 `Hyperopt` 等高级工具，交易者可以增强策略、尝试新方法，并发掘有价值的见解以改进模型。

指标的选择起着至关重要的作用，它指导交易者做出明智的决策。有效的风险管理和深思熟虑的指标选择对于全面评估模型和实现长期成功至关重要。

此外，通过 Python 库实现的自动化报告，能够高效地将交易数据转化为可执行的洞察。

## 结构

在本章中，我们将涵盖以下主题：

- [设计交易系统](#chap03.xhtml#h11)
- [改进交易系统](#chap03.xhtml#h12)
- [选择交易系统指标](#chap03.xhtml#h13)
- [自动化交易报告](#chap03.xhtml#h14)

## 目标

我们的主要重点在于设计和完善算法交易策略。我们的旅程始于选择一个分类器，该分类器负责熟练预测未来收益。

本章旨在通过利用分类器的能力、优化超参数以增强策略的稳健性、使用详细的风险和绩效指标分析策略表现，以及通过行业标准报告工具展示发现，为交易系统建立坚实的基础。

## 设计交易系统

本章将重点关注针对未来 K 线进行分类的算法。我们的旅程将涵盖整个流程，从数据获取到最终报告一个经过学习和评估的模型，该模型以其绩效和风险指标为特征。

路线图包括以下内容：

- 准备数据
- 进行特征工程
- 使用竞争性模型集合进行训练
- 通过绩效和风险指标评估模型
- 综合报告

### 准备数据

关于分析数据的一句话。我们选择使用微软（`MSFT` 代码）的数据作为研究基础，数据以 5 天为间隔记录，总共积累了 5000 天。报价间隔 5 天使我们能够探索周级别的时间跨度。数据源来自 Yahoo! Finance 库，我们已经多次使用过它。

下图展示了这些数据：

![](images/fig-3-1.png)

#### 进行特征工程

在此过程中，我们按顺序执行两个关键操作：

- `create_lag_past_values()`：此函数用前几个周期的滞后价格值扩充数据框。对于每一列价格（OHLC），都会添加一列包含这些滞后值的新列。这些新列的命名约定是在原始列名后附加一个表示滞后周期的后缀。例如，`_1` 表示滞后一期，`_2` 表示滞后两期，以此类推[1](#chap03.xhtml#footnote-143)。
- `return_past_values()`：此函数将所有价格数据转换为连续收益率。对于每一列价格，都会引入一列对应的收益率。这些新列通过在原始列名后附加后缀 `_ret` 进行恰当命名。

这两个操作结合在一起，融合了滞后值并计算收益率，构成了我们的特征工程步骤。这准备了我们的分析算法将用来预测未来收益率的模式。我们将在第 6 章《利用特征提升模型能力》（[Chapter 6](#chap06.xhtml)）中更深入地了解这一关键阶段，该章节专门致力于特征工程。

#### 特征相关性

在算法交易领域，理解特征相关性至关重要。相关特征会向数据中引入冗余，导致过拟合，并降低模型的泛化能力。

当算法遇到反映相似信息的特征时，可能会赋予这些交织在一起的特征过高的重要性，从而扭曲结果。这对于线性模型（如线性回归）和基于树的算法（如决策树和随机森林）尤为重要，因为在这些模型中，相关特征可能导致特征重要性出现偏差或虚高。为了确保稳健性并保持模型预测能力的完整性，识别并消除高度相关的特征至关重要，从而精简输入并提高模型效率。

#### 检测并消除相关特征

传统的皮尔逊相关系数仅能洞察线性关系，可能会遗漏非线性关联。此时引入斯皮尔曼等级相关系数，它能识别单调关系，以及互信息，它能捕捉线性和非线性依赖。这些替代指标至关重要，因为现实世界的金融数据通常表现出非线性行为。Scikit-learn 提供了 `VarianceThreshold` 和 `SelectKBest` 等特征选择工具，以及用于可视化检查的 `correlation_matrix`。此外，`feature-engine`[2](#chap03.xhtml#footnote-142) 等库还提供了处理相关变量的高级技术。采用这些策略并多样化相关性指标，可确保模型接收到最具信息量、非冗余的输入，从而优化其预测潜力。

以下代码显示了在消除相关特征阶段之前的相关性矩阵：

```python
import seaborn as sns

# Calculate the correlation matrix for the features
correlation_matrix = df_lag.corr()

# Create a mask for the upper triangle of the correlation matrix
mask = np.triu(np.ones_like(correlation_matrix, dtype=bool))

# Plot the correlation matrix
plt.figure(figsize=(15, 10))
sns.heatmap(correlation_matrix, mask=mask, cmap='coolwarm', vmax=1, vmin=-1, center=0, annot=False, fmt=".2f")
plt.title('Correlation Matrix of Features')
plt.show()
```

![](images/fig-3-2.png)

相关性矩阵突出了数据集中特征间的关系，红色渐变表示强正相关。高度相关的特征（由红色区域指示）提供了冗余信息。这些高度相关的变量被移除以减少多重共线性，并提高模型的可解释性和效率。

让我们继续进行剪枝算法，该算法旨在消除相关性超过允许值（阈值 0.9）的特征：

```python
# Identify features that are highly correlated
to_drop = []

for i in range(len(correlation_matrix.columns)):
    for j in range(i):
        if abs(correlation_matrix.iloc[i, j]) > 0.9:
            colname = correlation_matrix.columns[i]
            if colname not in to_drop and not colname.endswith('_ret'):
                to_drop.append(colname)

# Drop the highly correlated features
df_lag.drop(columns=to_drop, inplace=True)
```

通过前文讨论的相关特征矩阵来检验剪枝效果。即使仍存在一些相关性痕迹，我们可以在下图中看到，剩余的相关性比之前观察到的要可接受得多：

![](images/fig-3-3.png)

#### 缺失值与目标列

借助 Pandas 这样现代且强大的库，处理缺失值变成了一项快速简便的例行工作。
