
作为索引，我们有了 `listing_id`，在列中，包含了我们为该问题所准备的所有特征，如图 7.6 所示。

| listing_id | 坐标 | 房间类型 | 最小高度 | 评论数量 | days_sin |
|---|---|---|---|---|---|
| 196777 | 港区 | 20028 | 整个套公寓/公寓 | 3 | 173 | 30.0 |
| 776070 | 北区 | 22026 | 私人房间 | 3 | 243 | 9.0 |
| 905944 | 涩区 | 20022 | 整个套公寓/公寓 | 3 | 186 | 3.0 |
| 1016831 | 世田谷区 | 14022 | 私人房间 | 1 | 244 | 28.0 |
| 1196177 | 足立区 | 23027 | 私人房间 | 2 | 95 | 199.0 |

图 7 预测数据集的前几行

此时，我们可以开始详细检查数据，并找出是否有任何需要修复的问题，或者可能对我们开发 `XGBoost` 模型起至关重要作用的其他洞察。

# 7.1.5 探索并修复你的数据

在完成所有特征汇装后，下一步是详细检查数据，并确定是否有其他需要修复的问题，或者可能对我们开发 `XGBoost` 模型起至关重要的其他洞察。

# 7.8 绘制数值特征的箱线图

```python
import matplotlib.pyplot as plt
```

```python
numeric = ['minimum_nights', 'number_of_reviews', 
    'days_since_last_review', 'reviews_per_month', 
    'calculated_host_listings_count', 'availability_365', 'score',
    'number_of_reviews_ltm', 'number_of_reviews_ltm_ratio',
    'number_of_bedrooms', 'number_of_beds',
    'number_of_baths', 'imperial_palace_distance',
    'nearest_conven_store',
    'nearest_train_station', 'nearest_airport',
    'nearest_bus_station']
```

```python
num_plots = len(numeric)
num_rows = (num_plots + 2) // 3
num_cols = min(num_plots, 3)
```

```python
fig, axes = plt.subplots(
    num_rows,
    num_cols,
    figsize=(8, 12)
)
axes = axes.flatten()
```

```python
for i, feat in enumerate(numeric):
    X[feat].boxplot(ax=axes[i])
```

```python
plt.tight_layout()
plt.show()
```

图 7.7 显示了图表结果。通过检查箱须之外的值（以空心点表示），我们立即注意到几乎所有分布都有右偏尾，其值远大于平均值。对于距离类特征，这种极端值可能是合理的，因为大东京圈的延伸；但对于最小晚数和评论数量等特征，极端值可能代表远离分布核心的离群值。我们可以使用缩尾处理（winsorizing）来解决此类问题，使用我们在第 2 章提出的解决方案。

在列表 7.9 中，使用 Scipy 包中的 `winsorize` 函数，我们对 `minimum_nights` 特征分布的上部 0.1% 进行缩尾处理。超过 0.999 分位数的所有值将被更改为 0.999 分位数的值，从而消除了极端值。

# 准备并探索你的数据

263

![](img/def89cc476fa39f4c54bd34e78d91674_285_0.png)

**图 7.7** 箱线图面板，展示了大多数数值型特征的偏态分布

# 第 7 章 使用 XGBoost 的端到端示例

# 列表 7.9 对极值进行盖缩比例处理 (Winsorizing)

```python
from scipy.stats.m import winsorize
lower_cut_percentile = 0.00
upper_cut_percentile = 0.001
X['minimum_nights'] = winsorize(X['minimum_nights'].values,
limits=(lower_cut_percentile,upper_cut_percentile))
X['minimum_nights'].boxplot()
```

表示在缩尾处理过程中，低于此百分位数的值将不会被改变

表示在缩尾处理过程中，高于此百分位数的值将不会被改变

图 7.8 显示最大值为 120，不再像以前那样超过 1,000。

![](img/def89cc476fa39f4c54bd34e78d91674_286.png)

**图 7.8** 缩尾处理后的 `minimum_nights` 特征箱线图

我们对 `number_of_reviews` 特征进行相同的百分位数处理：

```python
X['number_of_reviews'] = winsorize(X['number_of_reviews'],
limits=(lower_cut_percentile,upper_cut_percentile))
X['number_of_reviews'].boxplot()
```

图 7.9 显示该特征仍然存在右尾，极值被压缩到了 500 以下。

![](img/def89cc476fa39f4c54bd34e78d91674_287.png)

**图 7.9** 缩尾处理后的 `number_of_reviews` 特征箱线图

完成对数据集的缩尾处理后，我们可以继续进入下一节查看目标变量本身。

## 7.1 探索你的目标

在处理探索性数据分析 (EDA) 时，检查目标变量的百分位数至关重要，对于我们的示例，我们只需要查看目标值的最小值、平均值和最大值，以及它们之间的关系：

```python
print(f"minimum: {y.min()}")
print(f"average: {y.mean()}")
print(f"maximum: {y.max()}")
```

这些命令将输出目标变量的：

- 最小值：1450
- 平均值：36573
- 最大值：130650

我们立即注意到最大值与平均值相比非常大。估计百分位数可以帮助理解是否存在极值或偏态分布。通过关注分布的边缘可以更好地理解极值的存在：

```python
perc = [1, 5, 10, 25, 50, 75, 90, 95, 99]
for p in perc:
    print(f"percentile {p}: {np.percentile(y, p):.2f}")
```

我们得到了百分位输出，并确认了目标值的 99 百分位数仍然远离最大值，报告如下：

- 1 百位数：3000.0
- 5 百位数：5198.2
- 10 百位数：7325.67
- 25 百位数：11870.0
- 50 百位数：19830.78
- 75 百位数：37741.64
- 90 百位数：83936.03
- 95 百位数：84857.11
- 99 百位数：304531.4

最大值不仅远离 99 百分位数，而且在 95 和 99 百分位数之间存在一个巨大的差距。我们的决定是通过丢弃分布的 10%（即上下各 5%）来关注分布的核心部分。我们通过使用布尔选择变量来实现：

```python
valid_samples = (y >= 5200) & (y <= 84857)
```

在确定定义选择之前，我们绘制分布图。

# 列表 7.10 绘制目标分布图

```python
import matplotlib.pyplot as plt
import seaborn as sns
valid_y = y[valid_samples]
sns.kdeplot(valid_y, fill=True)
median = np.median(valid_y)
plt.axvline(median, color='r', linestyle='--', linewidth=2, label='Median')
plt.xlabel('Value')
plt.ylabel('Density')
plt.title('Distribution with Median')
plt.legend()
plt.show()
```

![](img/def89cc476fa39f4c54bd34e78d91674_288.png)

结果在图 7.10 显示了。

![](img/def89cc476fa39f4c54bd34e78d91674_289.png)

结果在图 7.10 显示了。

![](img/def89cc476fa39f4c54bd34e78d91674_290.png)

# 构建并优化你的模型

```python
change_list[row.index[0]] = more_than_30.index[idx, 0]
```

```python
X["neighbourhood_more_30"] = (
    X["neighbourhood"].replace(change_list))
```

遍历每个计数少于 30 的社区，并查询 KDTree 以找到计数大于 30 的最近社区

> 根据 `change_list` 中的映射，将原始社区替换为新的社区值

运行代码后，你可以通过执行以下命令来检查映射的执行情况，并查看生成的聚合结果是否包含房源少于 30 个的社区区域：

```python
print(change_list)
print(X["neighbourhood_more_than_30"].value_counts())
```

在评估了合适的区域划分方案后，我们现在可以继续在下例列表中定义我们的分层交叉验证策略：

# 列表 7.12 定义分层策略 KFold

```python
from sklearn.model_selection import StratifiedKFold
```

```python
cv = StratifiedKFold(5, shuffle=True, random_state=0)
cv_splits = cv.split(X, y=X["neighbourhood_more_than_30"])
```

定义一个五折分层随机划分

在生成交叉验证划分的同时，保持每个折中房源多于 30 个的社区分布相同

运行后，`cv_splits` 是一个生成器，你可以使用以下命令对其进行检查：

```python
print(cv_splits)
```

输出是对象的类型：

```python
<generator object _BaseKFold.split at 0x78356223c66>
```
