
这些异常数据点通常预示着市场方向的重大转变：

## 通过移动平均线计算趋势

```python
def detect_trend(prices, window=20):
    ma = prices.rolling(window=window).mean()
    # 正斜率 ? -> 1 否则 -> -1
    trend = np.where(ma.diff() > 0, 1, -1)
    return trend
```

## 应用趋势检测器

```python
trend = detect_trend(stock_data['adjClose'], window)
```

当前市场趋势由短期移动平均线 (MA) 确定。MA 的负斜率表示下跌趋势，而正斜率表示上涨趋势。随后，如果市场当前处于上涨趋势且检测到异常，系统做空；如果市场处于下跌趋势且检测到异常，系统做多。

```python
for i in range(window, len(stock_data)):
    if anomalies[i] and clst_labels[i] in top_clusters:
        # 如果检测到异常，采取与趋势相反的仓位
        positions[i] = -trend[i]
```

作为参数，设定了 120 天的交易窗口，并定义了 2% 的止损以限制潜在损失。同样，我们不会优化参数。相反，我们的目标是验证核心概念的现状，并评估其即使在初始、未经打磨的形式下是否能产生有希望的结果：

## 应用策略

```python
window = 120
stop_loss = -2/100
positions, returns = trading_strategy(stock_data, anomalies, clst.labels_, list(top_clusters), window)
returns = np.where(returns < stop_loss, stop_loss, returns)
```

我们计算累积收益、总收益、年化收益和夏普比率：

## 计算累积收益

```python
cumulative_returns = np.cumsum(returns)
print(f"Total Return: {cumulative_returns[-1]:.2%}")
print(f"Annualized Return: {(1 + cumulative_returns[-1]) ** (252/len(returns)) - 1:.2%}")
print(f"Sharpe Ratio: {np.mean(returns) / np.std(returns) * np.sqrt(252):.2f}")
```

这段代码给出以下输出：

```text
Total Return: 28.45%
Annualized Return: 6.06%
Sharpe Ratio: 1.02
```

下图显示了策略（实线）和基准买入持有策略（虚线）的累积收益，后者由在期初买入并持有资产至整个周期结束组成：

![策略对比基准](images/fig-12-9.png)

基于异常的策略利用趋势反转获利，在避免长期回撤的同时实现稳健增值。与买入持有法相比，它能动态适应市场 regime 变化，强化了异常检测在交易决策中的价值。

与许多其他技术相比，此处使用的方法和算法参数更少且未经调优，属于无监督学习，与传统系统化交易策略相比，极大地降低了过拟合的风险。

无论如何，该策略都有显著的提升潜力：扩展至包含所有聚类而非仅主要聚类、优化异常区分方式而非一视同仁、以及改进趋势检测（因为当前的 MA 相当基础）。

无论如何，我们将介绍一个强大的数据科学工具，它将允许我们（除其他事情外）验证预定义的数据模式。该工具称为关联规则。

# 基于聚类并结合关联规则的策略

核心思路是保持聚类作为我们工作的基础，同时增加一个验证工具来挖掘数据并识别事件之间的关联，随后将其转化为可执行的交易策略。

## 关联规则

关联规则识别数据中不同事件间的关系，突显经常一起出现的模式。

关联规则挖掘是一个强大的工具，能将数据转化为有价值的洞察。以超市销售数据为例。通过分析这些数据，我们可以发现揭示购买习惯的模式。例如，我们可能会发现购买洋葱和土豆的顾客也倾向于购买汉堡肉：`{洋葱, 土豆} ⇒ {汉堡肉}`。这些模式可能并不显而易见，但通过挖掘交易数据，企业可以发掘隐藏关系并利用它们优化产品摆放、促销或推荐。

关联规则挖掘识别项目或事件之间频繁的共现。它是一种数据驱动的方法，各领域（包括零售和金融）的企业均可用其做出更明智的决策。

在金融领域，我们使用相同的方法来发掘市场行为之间隐藏的联系。通过识别反复出现的模式，例如成交量激增后跟随价格激增，我们可以将这些洞察转化为可执行的交易策略。

关联规则学习[^1]是一种无监督学习技术，能自动发掘隐藏关系。关联规则挖掘在没有预定义结果的情况下探索数据。它搜索经常一起出现的频繁项集，并提取称为规则的 if-then 关系。这些规则表达为：如果事件 A 发生，事件 B 很可能随之发生。我们寻找的不是适用于所有事件且永远正确的完美规则。重要的是要理解，关联规则只发现正确的相关性，而非完美的真理。

## 数据准备

我们将把关联规则挖掘应用于序列和聚类数据集，以提取可执行的规则，旨在发掘可转化为交易策略的隐藏关系。为此，我们需要将数据集中的数值转换为布尔 True/False 指示器。这是必要的，因为关联规则算法通过寻找二元变量之间的模式来工作。这种简单的转换是将数据输入关联规则库之前所需的唯一准备工作，使我们能够无缝发现可用于交易决策的有意义联系。

理想情况下，利用关联规则，我们希望关联诸如 `is_cluster_A -> positive_return` 之类的事件。在这个虚构示例中，该规则应解读为：属于聚类 A 的序列很可能后跟正收益。

在此示例中，`is_cluster_A` 是前件[^2]。它是必须首先发生的条件或事件。`positive_return` 是后件。后件是很可能随之发生的结果事件。

我们如何使用这条规则？显然，这条规则建议每当序列属于聚类 A 时买入（做多）。

为实施此方法，我们首先将数值转换为布尔（True、False）指示器，使关联规则算法能够识别有意义的模式，如下所示：

```python
lag = 1
# 计算日收益率
asset_ret = stock_data["close"].pct_change().shift(-lag)
# 布尔 True/False 指示器
asset1_bins_pos = asset_ret > 0
asset1_bins_neg = asset_ret < 0
```

我们使用滞后收益率（`lag = 1`），因为我们的目标是利用当前信息预测未来收益。我们标记了正负收益，并创建了一个包含其他显著因素的事件包，例如 `is_cluster_A` 到 `is_cluster_D`、`is_anomaly`、`is_trend` 和 `is_not_trend`：

```python
is_cluster_A = pd.Series(clst.labels_ == top_clusters[0])
is_anomaly = pd.Series(anomalies)
is_hurst_trend = stock_data['hurst_price'] > 0.5
is_hurst_notrend = stock_data['hurst_price'] < 0.5
```

这建立在我们之前利用这些特征构建序列的工作基础之上。现在，正如提到的，我们需要将这些特征转换为逻辑（True/False）指示器。这是应用关联规则算法中的人工环节，即决定哪些事件足够显著以纳入分析。必须仔细填充这个事件包，因为输入的质量直接影响输出（垃圾进，垃圾出）。准备就绪后，关联规则学习算法将广泛挖掘这些事件以揭示它们之间的相关性：

## 创建包含离散化收益的数据集
