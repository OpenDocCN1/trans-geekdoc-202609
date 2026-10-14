

```python
clf_blend = VotingClassifier(voting='hard', estimators=lst_clf_opt)

clf_blend.fit(X_train, y_train)

clf_blend.score(X_test, y_test)
```

我们现已完成第二阶段，即对每个预测器进行微调并协调其集体运作。让我们来看看以下结果：

| | precision | recall | f1-score | support |
|---|---|---|---|---|
| -1 | 0.44 | 0.15 | 0.22 | 103 |
| 1 | 0.59 | 0.87 | 0.70 | 146 |
| accuracy | | | 0.57 | 249 |
| macro avg | 0.52 | 0.51 | 0.46 | 249 |
| weighted avg | 0.53 | 0.57 | 0.50 | 249 |

总之，精确率为 59% 对比 44%，模型在识别 1 类（正收益）方面表现远优于 -1 类（负收益），1 类的召回率高达 87%。然而，其对 -1 类的精确率有待提高。此外，我们的系统不会持续用新数据更新。考虑到我们正用一个基于四年前数据训练的系统来评估 2023 年的数据。这种方法有助于衡量系统的韧性。

## 权益曲线

要可视化策略的权益曲线，我们只需加入一些额外要素。具体而言，我们必须考虑经纪费用（通常每笔交易约 3 个基点）以及多头和空头交易的收益：

```python
# broker fee in basis point
fee = 3 / 100 / 100

stop_loss = -4 / 100

target_ret = df_lag.loc[y_test.index, 'Close_ret'].shift(-lag_predict)

# Calculate cumulative returns for long trades (+1 predictions)
long_returns = np.where(pred_blend == 1, target_ret, 0)

# apply stop loss
long_returns = np.where(long_returns < stop_loss, stop_loss, long_returns)

cumulative_long_returns = np.cumsum(long_returns)

# Calculate cumulative returns for short trades (-1 predictions)
short_returns = np.where(pred_blend == -1, -target_ret, 0)  # We inverse the returns for short trades

# apply stop loss
short_returns = np.where(short_returns < stop_loss, stop_loss, short_returns)

cumulative_short_returns = np.cumsum(short_returns)

# pay fee each time position change (detect with np.diff)
brk_fee = np.where(np.diff(pred_blend) != 0, fee, 0)

# adjust dimension with pad (add one element (zero), at the beginning)
brk_fee = np.pad(brk_fee, pad_width=(1, 0))
```

![](images/fig-3-5.png)

该策略看起来非常有趣。绿线代表我们的策略，虚线代表买入持有（B&H）策略[6](#chap03.xhtml#footnote-138)。此外，我们可以轻松应用更保守的止损策略，以平滑此类低频策略（周频）不可避免的回撤。

作为最终评估，我们实施了与微软日线股份相同的策略，结合了元策略[7](#chap03.xhtml#footnote-137)，正如第一章所详述。结果显示如下：

采用堆叠分类器的机器学习策略，在时间线的很大一部分中似乎优于 B&H 策略。这表明 `ML` 模型成功捕捉并预测了价格走势。

![](images/fig-3-6.png)

与 B&H 和 ML 策略相比，元策略显示出显著的超额表现。这表明元策略可能利用了额外信息，或采用了更动态的交易方法，使其能把握更多交易机会并更有效地管理风险。该策略脱颖而出，成为最有效的策略，表明在此背景下策略组合可带来卓越表现。

我们对所取得的成果感到满意。事实上，该策略从周频过渡到日频毫无困难。

我们现在将利用现代风险管理的适当工具，对此进行严格检验。

## 交易系统指标的选择

策略的成功不仅关乎更高的收益。它关乎理解所承担的风险、收益的持续性，以及共同描绘出全面绩效图景的各个其他侧面。

本节探讨评估交易策略的本质，从年化收益等基础指标过渡到 `CAGR`、`VaR` 和 `Sharpe ratio` 等专业衡量标准。最后，你将掌握每个指标的意义、理想基准及其相互作用。

### 策略评估指标的排序标准

交易策略评估要求系统性分析，以产生有价值的见解和有意义的比较。绩效指标涵盖从基本衡量到复杂的机构指标，各自服务于特定的分析需求。

按类别理解以下指标，有助于投资者选择与其目标和风险偏好相匹配的评估方法：

- **基础**：提供策略绩效整体感知的指标，适合所有层级的投资者
- **风险调整收益**：考量为实现收益所承担风险的指标。这能区分收益相同但风险截然不同的策略
- **回撤**：围绕理解损失幅度和持续时间的指标
- **统计显著性**：评估策略绩效是否可能归因于运气的指标
- **风险指标**：提供策略可能面临的尾部风险和极端事件洞察的指标
- **一致性与稳定性**：分析策略收益随时间变化的一致性和稳定性的指标
- **专业**：机构投资者常用于深度分析和剖析策略绩效的高级指标

### 评估交易策略的统计指标列表

以下统计指标代表了策略评估的关键量化工具，按复杂度和用途组织。每个指标揭示交易绩效的不同侧面，从基础指标开始，经风险调整衡量，终于机构级分析。

- **基础统计**
  - **总收益**：策略的总体收益
  - **年化收益**：平均每年收益
  - **波动率（标准差）**：收益的离散程度

- **风险调整收益**
  - **夏普比率**：每单位总风险所实现的收益
  - **索提诺比率**：每单位下行风险所实现的收益
  - **卡尔马比率**：年化收益与最大回撤之比

- **回撤**
  - **最大回撤**：从峰值到谷值的最大跌幅
  - **平均回撤**：所有回撤的平均值
  - **回撤持续时间**：从回撤中恢复所需的时间长度

- **统计显著性**
  - **T 统计量**：评估策略收益在统计上是否显著不同于零
  - **P 值**：观测收益归因于偶然的概率

- **风险指标**
  - **风险价值**：在给定概率下不被超过的最大损失
  - **条件风险价值**：给定损失超过 `VaR` 时的预期损失
  - **偏度**：衡量收益分布的不对称性
  - **峰度**：衡量尾部风险或极端收益

- **一致性与稳定性**
  - **胜率**：盈利交易的百分比
  - **平均盈亏比**：盈利交易的平均利润与亏损交易的平均亏损之比
  - **盈亏比**：总盈利与总亏损之比

- **专业**
  - **Omega 比率**：收益与下行风险之比
  - **信息比率**：主动收益与主动风险之比
  - **Beta 系数**：策略对市场波动的敏感度
  - **Alpha 系数**：调整 Beta 后的超额收益
  - **R 平方**：策略跟随市场的紧密程度
  - **特雷诺比率**：超额收益与 Beta 之比
  - **复合年增长率 (CAGR)**：提供恒定收益率的几何级数比率
  - **下行标准差**：负收益的波动率
  - **上行潜力**：衡量收益分布的上行空间

