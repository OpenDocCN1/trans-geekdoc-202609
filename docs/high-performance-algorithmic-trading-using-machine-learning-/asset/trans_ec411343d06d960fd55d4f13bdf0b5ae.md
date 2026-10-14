
读完本章，我们希望您已在算法交易及机器学习在此领域的作用方面打下坚实基础。我们回顾了算法交易的诞生与演变，了解其类型与策略，进而认识到机器学习的重要性及其对交易实践的影响。

我们探讨了从动量策略到统计套利策略的各类方法，识别了机器学习识别趋势与均值回归模式的潜力，甚至涉足了新兴的元学习领域。这种理解为您深入探究机器学习在算法交易语境下的应用奠定了基础。

在下一章中，我们将探讨算法交易中 AI 算法所用的数据谱系，重点关注经济与基本面数值数据以及非传统数据来源。本章的一个核心重点将是揭示回测的基本原理，这是评估和优化交易策略的关键环节。旨在让读者扎实掌握这些原理与数据的适当使用相结合，如何增强算法交易系统的有效性。

## 参考文献

1. *Statistical arbitrage: Algorithmic Trading Insights and Techniques*, Andrew Pole.
2. *Algorithmic trading*, Whiley Trading Series, Ernest P. Chan.
3. *Pairs trading: Quantitative Methods and Analysis*, Whiley Finance, Ganapathy Vidyamurthy.
4. *A Machine Learning based Pair Trading Investment Strategy*, Springer, Sarmento and Horta.
5. *Optimal mean reversion trading: Mathematical Analysis and Practical Applications*, Tim Siu-Tang, Xin Li.

***

**加入我们的图书 Discord 社区**

加入图书的 Discord 工作区，获取最新动态、优惠、全球科技动态、新书发布及作者专场活动：

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![Discord](images/Discord.png)

# 第 2 章：数据源、回测与前向测试

## 简介

在本章中，我们将讨论结合机器学习的算法交易的关键方面，重点关注用于输入 AI 算法的数据类型，以及回测和前向测试的核心原则。

它指出经济和基本面数据，以及在市场上交易的金融资产价格（如最高价、最低价、收盘价和开盘价）是至关重要的输入。它强调了交易中使用的可变时间间隔，凸显了算法模型所需的适应性。此外，它敦促读者跳出传统数据源的思维定势，考虑非正统数据，从社交媒体情绪到地缘政治事件，这些数据可能为市场行为提供独特且具有预测性的洞见。

它强调了数据预处理的重要性，即在将数据输入模型前对其进行精炼的过程，包括处理缺失数据和异常值以及对分类数据进行编码。

## 结构

在本章中，我们将涵盖以下主题：

- [数据源](#chap02.xhtml#h07)
- [世界银行 API](#chap02.xhtml#h08)
- [美联储经济数据](#chap02.xhtml#h09)
- [Financial modeling prep 基本面数据 API](#chap02.xhtml#h10)

## 目标

本章讨论数据源、回测和前向测试的基础知识。从理解数据源在金融分析中的作用入手，本章导航至宏观经济和基本面数据源。认识到 API 在数据检索中日益增加的集成度，它重点介绍了世界银行 API、美联储经济数据 API 和 Quandl 经济数据 API 等知名平台的特性。

探索延伸至基本面数据，讨论了 Tiingo 基本面数据 API 和 Financial Modelling Prep 基本面数据 API 等工具的属性和优势。一个值得注意的部分介绍了量化基本面投资模型的原则，强调了数据源与量化基本面策略之间的共生关系。

本章还强调了开高低收（OHLC）价格数据在金融工作中的相关性。向前看，它涉及利用报告、研究和非结构化数据的重要性和挑战。整个讨论旨在作为一份综合指南，帮助读者理解金融数据的多面世界。

## 数据源

算法交易的世界极其多元，由构成交易算法骨干的海量数据源作为支撑。构建稳健可靠的交易模型的一个关键方面，在于理解并选择最合适的数据类型。

算法交易中使用的主要数据源可大致分为经济和基本面数值数据。这些数据集提供了可量化、可衡量的经济格局和公司特定绩效指标洞见，构成了许多交易策略的基石。

作为机器学习算法输入的另一种最常见数据类型，是金融市场上交易的资产价格（开盘价和收盘价）及其基本描述性统计，如记录的最高价和最低价。

我们将在以下段落更详细地描述这两类数据。让我们从经济数据和基本面数据开始。

### 宏观经济与基本面数据

经济数据是指反映一国经济健康状况和趋势的宏观经济指标。这些指标包括国内生产总值（GDP）、通货膨胀率、失业率、消费者信心指数、工业生产等。在金融市场中，这些数字受到密切关注，因为它们可以提供央行未来政策行动的信号，例如利率变动，这会显著影响资产价格。

全球宏观交易策略以宏观经济数据为主要原料。这些策略由对冲基金和投资基金实施。这些基金青睐的投资工具是指数。这些可以是股票、债券、货币、房地产或其他指数。这意味着这些基金不[^1] 投资于个别公司，而是投资于经济板块或国家。最常见的宏观策略包括管理期货、全球战术资产配置和货币套利交易。

我们现在将介绍一些可通过 API 免费访问的宏观经济数据源，以供您的自动化系统使用。我们从世界银行开始，接着是美联储经济数据，最后以 Quandl 结束这趟优质数据提供商之旅。

## 世界银行 API

让我们看一个世界银行 API[^2] 的示例。目的是展示如何查询这个免费、高质量的数据源，以检索美国的经济数据。

首先，如果您还没有安装世界银行的 API `wbdata`，请先安装：

```python
try:
    import wbdata
except ModuleNotFoundError as e:
    print(e)
    !pip install wbdata

import wbdata
```

以下代码获取美国（国家代码：`USA`）的通货膨胀数据（代码：`FP.CPI.TOTL.ZG`），并将其存储在一个名为 `data` 的 DataFrame 中：

```python
# 设置数据参数
indicator = {'FP.CPI.TOTL.ZG': 'Inflation'}
country = {'USA': 'United States'}

# 检索数据
data = wbdata.get_dataframe(indicator, country=country)

# 按时间顺序排列
data = data.reindex(index=data.index[::-1])
data.info()
```

`info()` 函数给出了该数据集的摘要信息：

```
<class 'wbdata.api.WBDataFrame'>
Index: 63 entries, 1960 to 2022
Data columns (total 1 columns):
  #   Column     Non-Null Count  Dtype
---  ------     --------------  -----
  0   Inflation  63 non-null     float64
dtypes: float64(1)
memory usage: 1008.0+ bytes
```
