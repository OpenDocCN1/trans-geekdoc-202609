
在以下示例中，我们将实现隔离森林（即机器学习方法）进行异常检测，重点分析成交量以检测早期价格变动。特征包括每日成交量、滚动平均成交量和成交量比率。这种无监督方法特别擅长识别罕见事件或异常值，并可能在重大价格变动前检测到异常的成交量激增。

隔离森林是一个很好的起点，原因如下。它需要调整的超参数很少，且计算效率高，使得训练和预测更快，尤其是在大型数据集上。它能有效处理较小的数据集，且不需要标记数据，这对许多异常检测任务来说是一个挑战。结果具有可解释性，并且无需大量特征工程即可处理高维数据。此外，它为每个数据点提供内置的异常分数。`Scikit-learn`[7](#chap12.xhtml#footnote-009) 库中提供了隔离森林的实现，无需复杂设置即可使用。

隔离森林通过分割数据点来隔离观测值。它通过构建树[8](#chap12.xhtml#footnote-008) 来工作，其中异常点（罕见且不同）能以更少的分割更快地被隔离。算法根据数据点被隔离的速度为其分配异常分数，使其能有效检测高维数据集中的异常值。其高效性和简洁性使其成为异常检测中广泛使用的工具。

要在数据上实现隔离森林算法，我们创建一组用于成交量分析的特征。我们将使用每日成交量、滚动平均成交量和成交量比率作为隔离森林的特征：

```python
# Calculate rolling averages and volume ratios
stock_data['Rolling Volume Mean'] = stock_data['volume'].rolling(window=10).mean()

# Ratio of current volume to rolling mean
stock_data['Volume Ratio'] = stock_data['volume'] / stock_data['Rolling Volume Mean']

# Drop NaN values (caused by rolling calculations)
stock_data.dropna(inplace=True)

# Select features for Isolation Forest
features = stock_data[['volume', 'Rolling Volume Mean', 'Volume Ratio']].values
```

然后，我们拟合隔离森林模型：

```python
isolation_forest = IsolationForest(contamination=0.1, random_state=42)
```

我们通过应用 `fit_predict()` 函数明确标示异常：

```python
stock_data['Anomaly Score'] = isolation_forest.fit_predict(features)
```

下图显示了隔离森林检测到的异常，标记为红色 X 号：

![](images/fig-12-4-isolation-forest-anomalies-detected.png)

为了进一步分析成交量异常与价格变动的关系，我们绘制了调整后收盘价以及检测到的成交量异常：

![](images/fig-12-5-prices-related-to-anomalies.png)

在显著价格变动前出现了多个成交量异常，表明这些异常可能预示着即将到来的价格变化。例如，2023 年中检测到一系列成交量异常，随后价格明显上涨；同年晚些时候（2023 年 11 月底至 2024 年 1 月初）价格下跌前也观察到类似模式。

在关键价格拐点（如 2024 年初）周围存在异常聚类，此时观察到价格急剧下跌。这表明在重大价格变动前市场活动增加或出现异常交易模式。值得注意的是，跌价后立即出现几个异常，可能预示着市场动态的转变和即将到来的反弹。该模式表明，隔离森林检测到的成交量异常可作为趋势反转和潜在复苏阶段的早期预警信号。

对隔离森林算法的探索至此结束了我们对异常检测技术的介绍。我们现在已很好地理解了该领域的不同方法，包括统计方法和机器学习算法。

接下来，我们的重点将转向集成方法的实现。该方法将时间序列聚类与降维算法相结合。

## 时间序列聚类与投影用于异常检测

目标是根据正常和异常序列在拟议投影空间中的位置对其进行映射。我们提出的混合技术旨在利用序列聚类和降维的优势，以改进异常检测。区分金融时间序列是我们的主要目标。为了有效映射这些序列，我们首先构建能捕捉时间模式的有意义特征。

### 特征工程

正如 [第 6 章](#chap06.xhtml) "Improve Model Capability with Features" 中所述，赫斯特指数提供了一种基于趋势持久性表征市场的有效方法。我们将把这一信息纳入时间价格序列（第 1 天、第 2 天、第 3 天等）中。

选择赫斯特指数作为特征符合其根本目的。该指标根据趋势持久性将时间序列分为三种潜在状态：趋势性、纯随机性或反持久性（均值回归）。因此，每个时间序列都将与其对应周期计算出的赫斯特指数配对。

让我们开始计算赫斯特指数：

```bash
!pip install -q hurst
```

```python
from hurst import compute_Hc

window_size = 100  # Set a window size >= 100

# Make sure to apply the rolling only on windows with enough data
stock_data['hurst_price'] = stock_data['adjClose'].rolling(window=window_size).apply(
    lambda x: compute_Hc(x, simplified=True)[0] if len(x) >= 100 else np.nan, raw=False
)
```

我们绘制赫斯特指数的计算结果，如下所示：

![](images/fig-12-6.png)

第一张图显示了随时间变化的赫斯特指数（记为 H，窗口大小为 100 天），在 0.3 和 0.9 之间波动，表明存在不同时期的均值回归行为（H < 0.5）和趋势行为（H > 0.5）。2021 年中左右赫斯特值出现明显峰值，表明市场趋势强劲持久，随后下降，意味着随机性增加或均值回归。

第二张图显示了调整后收盘价（黑线）和成交量（蓝线）。成交量有几个显著峰值，特别是 2024 年初，可能预示着重要市场事件或交易活动增加。

总体而言，赫斯特指数和成交量的综合分析表明市场状态交替变化，趋势行为之后跟随随机性，但价格对高成交量峰值的反应保持稳定。

然后我们创建一组滞后特征[9](#chap12.xhtml#footnote-007)。其目的是用历史信息和记忆丰富数据集（OHLC 值），从而捕捉时间模式和趋势。我们将为几个关键指标生成滞后版本（收盘价、收盘价百分比变化、Z 分数、成交量百分比变化和赫斯特指数值）：

```python
for i in range(1, 4):
    stock_data[f'close_{i}'] = stock_data['adjClose'].shift(i)
    stock_data[f'close_pct{i}'] = np.round(stock_data['adjClose'].pct_change().shift(i), 3)
    stock_data[f'zscore_{i}'] = np.round(stock_data['Z-Score'].shift(i), 2)
    stock_data[f'volume_pct{i}'] = np.round(stock_data['volume'].pct_change().shift(i), 3)
    stock_data[f'hurst_{i}'] = np.round(stock_data['hurst_price'].shift(i), 2)
```

特征集包含以下元素：

```python
lst_col = [
    'open', 'high', 'low', 'close', 'adjClose', 'volume', 'Z-Score', 'hurst_price',
    'close_1', 'close_pct1', 'zscore_1', 'volume_pct1', 'hurst_1',
    'close_2', 'close_pct2', 'zscore_2', 'volume_pct2', 'hurst_2',
    'close_3', 'close_pct3', 'zscore_3', 'volume_pct3', 'hurst_3'
]
```
