
#### 训练-测试集划分

```python
X_train, X_test, y_train, y_test = train_test_split(X, df['target'], shuffle=False)
```

#### 创建并训练决策树分类器

```python
clf = DecisionTreeClassifier(random_state=42)
clf.fit(X_train, y_train)
```

最后是模型测试，函数输出如下：

```python
from sklearn.metrics import classification_report
print(classification_report(clf.predict(X_test), y_test))
```

| | precision | recall | f1-score | support |
|---|---|---|---|---|
| -1.0 | 0.24 | 0.50 | 0.33 | 46 |
| 1.0 | 0.78 | 0.53 | 0.63 | 154 |
| accuracy | | | 0.53 | 200 |
| macro avg | 0.51 | 0.52 | 0.48 | 200 |
| weighted avg | 0.66 | 0.53 | 0.56 | 200 |

重要的是要注意，所有性能指标都是在算法训练期间无法访问的数据（`X_test`）上计算的。因此，它未使用这些数据进行训练。这些数据合理地说明了在新数据和未发布数据上的预期性能，例如在生产和实盘交易环境中可能遇到的情况。这是一个关键点。我们稍后将回过头来讨论我们面前的指标的含义和解读（越高越好）。

正类（`+1`：上涨期）的正确预测百分比远高于无信息的随机预测（抛硬币），后者在本例中为 0.5。事实上，精确率为 0.78。

然而，另一类（`-1`）并非如此。下跌期的预测效果不佳。

现在，我们需要将其与传统交叉系统的指标进行比较。实现交易规则以计算相关的性能指标。

正如简介中提到的，最简单的规则是交叉规则，可以表示如下：

#### 交叉规则：+1 MA(50 天) > MA(200)；-1：MA(50 天) < MA(200)

```python
ma_cross = np.where(X_test['MA_cross'] > 0, 1, -1)
print(classification_report(ma_cross, y_test))
```

```
              precision    recall  f1-score   support

          -1.0       0.55      0.46      0.50       114
           1.0       0.41      0.50      0.45        86

    accuracy                           0.48       200
   macro avg       0.48      0.48      0.47       200
weighted avg       0.49      0.47      0.48       200
```

在没有 ML 帮助的情况下，交叉系统并没有显著优于随机预测。指标徘徊在 50%（0.5）左右。

### 利用机器学习的元策略

元策略在机器学习领域内，指向一种被称为元学习的实践。这一概念也称为“学会学习”，是机器学习的一个小众子集。元学习的威力在于其能够根据实验获得的结果，通过修改学习算法的特定方面来提升该算法的性能。

元学习真正的卓越之处在于其能够用数据驱动方式学习得出的方法论，来替代人工设计的算法。

因此，当应用于交易策略时，元学习呈现为元策略的形式。该框架的作用是利用机器学习不仅优化，而且根据不断变化的市场动态来调整交易策略。这转化为一种适应性强且灵活的算法交易方法，能够与市场同步演进。

实际上，元策略有潜力从我们现有的交易策略中榨取更大的价值。由元学习驱动的交易元策略，是一种基于策略表现和不断变化的市场条件来优化和演进交易算法的动态方法。

其核心在于，元学习是一个使模型能够从过去经验中学习的过程。这意味着它不仅分析输入数据，还分析自身的表现，并根据获得的洞察调整其算法。当应用于交易系统时，这一概念演变为元策略。

#### 元策略实战

其工作原理如下：元策略不使用基于预定义规则运行的静态交易算法，而是使用一个学习算法。该学习算法评估交易策略在不同市场场景下的表现，了解其优势和劣势。然后根据这些习得的知识调整交易策略，使其更加稳健有效。

例如，一种交易策略可能在高波动时期表现良好，但在低波动时期却举步维艰。利用元学习的元策略会识别出这种模式并调整策略，或许通过在低波动时期减小仓位或改变进出场点位。

以这种方式，元策略可以持续优化交易系统，随着时间的推移并在各种市场条件下提升其性能。它们代表了算法交易的下一个层级，在那里交易系统不仅是自动化的，而且是自我改进和自适应的。

##### 元交易策略

让我们通过一个具体例子来尝试编写一个旨在补充现有策略的元策略。为此，让我们采用通过检测超买和超卖股票来回归均值的策略。我们在上一节中描述了该原则。

结合元学习的策略思路：

1.  检查策略的盈亏是否可以作为策略输入数据的函数进行预测。
2.  如果可以，我们将在交易前预测盈亏的符号，仅发送有希望的交易（即预测盈亏为正的交易）。

为实现这一点，元策略仅需对初始策略进行微小修改。

元策略以描述我们试图增强的策略的数据作为输入。这些数据如下：

- 策略的表现（盈亏）

![](img/Figure_1.8.jpg)

被分析策略的输入数据。

以下是计算机代码所需的步骤：

1.  我们需要保留每个周期的盈亏记录（`ar_pnl` 数组）。

```python
###### agregated PnL for each specific period :
ar_pnl = pd.DataFrame(np.zeros(len(ranked_ret.index)) , index = ranked_ret.index , columns=["agg_pnl"] )
```

2.  我们用每个周期的盈亏填充此表。

```python
###### Calculate transaction cost
###### transaction cost in basis point:
###### transaction_cost_amount = (open_price + close_price) * quantity * transaction_cost
###### transaction cost per share (broker fee : minimum 1$):
transaction_cost_amount = max(quantity * transaction_cost , 1)
profit_loss = (close_price - open_price) * quantity - transaction_cost_amount
### apply stop loss
profit_loss = np.max([profit_loss , stp_loss])
lst_pnl.append(profit_loss)
total_profit_loss = total_profit_loss + profit_loss
ar_pnl['agg_pnl'].loc[date] = ar_pnl['agg_pnl'].loc[date] + profit_loss
```

3.  接下来，我们获取策略的特征（`X`），即收益率和这些收益率的排名（根据收益率大小分配给每个资产的排名）。

```python
###### features : we merge the ranked returns and array of returns
X = pd.concat([ret , ranked_ret] , axis =1)
```

4.  目标是学会预测。这是一个二元目标（`y`），取决于产生的盈亏是否为正。

```python
###### target : agregated PnL for each specific period -> ar_pnl
y = np.sign(ar_pnl.shift(-1))
###### binary sign is either 1 or -1 not 0
y[y == 0] = -1
###### last period, zero to clean missing value
y.iloc[-1] = -1
y = np.ravel(y)
```

5.  学习阶段：

```python
###### Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y , test_size =0.025,shuffle = False)
clf = RandomForestClassifier()
clf.fit(X_train , y_train)
```

以下是与预测盈亏符号相关的指标：

| | precision | recall | f1-score | support |
|---|---|---|---|---|
| -1.0 | 0.40 | 0.61 | 0.48 | 36 |
| 1.0 | 0.67 | 0.46 | 0.54 | 61 |
| accuracy | | | 0.52 | 97 |
| macro avg | 0.53 | 0.54 | 0.51 | 97 |
| weighted avg | 0.57 | 0.52 | 0.52 | 97 |

该算法为正类别（`+1`：正盈亏）找到了预测模式。正确预测与错误预测的比率等于 2/3 (0.67)，这高于平均水平，当然也高于随机预测。

剩下的就是接入由元规则形成的过滤器。

在每笔交易前，我们检查该交易是否有机会产生正利润。具体操作如下：将即将进行的交易信息发送给与训练好的算法关联的预测函数（`predict_proba`）。该函数返回该交易产生利润的概率。该概率充当交易过滤器（元规则），仅允许具有盈利潜力的交易通过。我们仅发送超过 50% 阈值（产生正利润的概率）的盈亏：

```python
###### open a trade if the ML model allows it ....
if clf.predict_proba(pd.DataFrame(X.loc[date].values.reshape(1,-1) , columns=X.columns))[0,1] > 0.5:
    print("ML OK for this trade")
    lst_pnl_meta_strat.append(profit_loss)
else:
    lst_pnl_meta_strat.append(0)
```

同时，我们记录未经过元规则过滤的策略盈亏（非元曲线）。我们在下图中得到了这两条权益曲线：

![](img/fig-1-9.png)

元规则生效了。经过过滤的策略回撤更低，利润更高。两条曲线的差异并不惊人，但再次强调，这里并未寻找最优参数或进行微调。

## 结论

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

[`discord.bpbonline.com`](https://discord.bpbonline.com)

![Discord](img/Discord.png)

# 第 2 章：数据源、回测与前向测试

## 简介

在本章中，我们将讨论结合机器学习的算法交易的关键方面，重点关注用于输入 AI 算法的数据类型，以及回测和前向测试的核心原则。

它指出经济和基本面数据，以及在市场上交易的金融资产价格（如最高价、最低价、收盘价和开盘价）是至关重要的输入。它强调了交易中使用的可变时间间隔，凸显了算法模型所需的适应性。此外，它敦促读者跳出传统数据源的思维定势，考虑非正统数据，从社交媒体情绪到地缘政治事件，这些数据可能为市场行为提供独特且具有预测性的洞见。

它强调了数据预处理的重要性，即在将数据输入模型前对其进行精炼的过程，包括处理缺失数据和异常值以及对分类数据进行编码。

## 结构

在本章中，我们将涵盖以下主题：

- 数据源
- 世界银行 API
- 美联储经济数据
- Financial modeling prep 基本面数据 API

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

全球宏观交易策略以宏观经济数据为主要原料。这些策略由对冲基金和投资基金实施。这些基金青睐的投资工具是指数。这些可以是股票、债券、货币、房地产或其他指数。这意味着这些基金不[¹] 投资于个别公司，而是投资于经济板块或国家。最常见的宏观策略包括管理期货、全球战术资产配置和货币套利交易。

我们现在将介绍一些可通过 API 免费访问的宏观经济数据源，以供您的自动化系统使用。我们从世界银行开始，接着是美联储经济数据，最后以 Quandl 结束这趟优质数据提供商之旅。

### 世界银行 API

让我们看一个世界银行 API[²] 的示例。目的是展示如何查询这个免费、高质量的数据源，以检索美国的经济数据。

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
##### 设置数据参数
indicator = {'FP.CPI.TOTL.ZG': 'Inflation'}
country = {'USA': 'United States'}

##### 检索数据
data = wbdata.get_dataframe(indicator, country=country)

##### 按时间顺序排列
data = data.reindex(index=data.index[::-1])
data.info()
```

`info()` 函数给出了该数据集的摘要信息：
