

# 探索性数据分析

这表明 75% 的无签名支票是欺诈性的，而只有 0.09% 的签名支票是欺诈性的。0.75 / 0.00092 = 822 的比例强烈暗示无签名支票具有更高的欺诈风险。如果我们构建一个预测模型，`check_signed` 将是一个很好的候选预测变量。

接下来，让我们探索 `check_amount` 以了解金额如何随欺诈结果变化。图 11.2 中的散点图可能会澄清它们的关系。

```python
sns.scatterplot(x='check_amount', y='is_fraud', data=df)
plt.grid() # 由 matplotlib 调用
```

![](img/7f40a2246fd3d2d5353d109f489c4e33_220_0.png)

图 11.2：按欺诈指标分类支票金额

网格线整合自 matplotlib。对于双变量图（也称为联合图），常用的指定的参数是 x、y 和 dataframe。x 和 y 的值是作为字符串输入的变量名，而 data 指的是 dataframe 对象。与单变量情况类似，可以通过交换图类型并包含相关参数来更改图形类型。

大多数支票都不是欺诈性的，它们的点被绘制在底部的水平网格线上。我们在 `is_fraud=1` 的顶部的水平网格线上看到了四张欺诈支票。支票金额似乎大致为 1000、4500、5000 和 10000。我们还可以检查数据集中的欺诈记录：

```python
df[df.is_fraud=1]
```

# 世界幸福报告

| checkid | check_amount | check_signed | is_fraud |
| :--- | :--- | :--- | :--- |
| 101 | 10000.00 | 1 | 1 |
| 510 | 5000.00 | 0 | 1 |
| 778 | 1000.00 | 0 | 1 |
| 901 | 4615.59 | 0 | 1 |

该表格确认了一个关键观察：在四个欺诈案例中的三个中，支票金额是 1000 的倍数。鉴于此，创建一个预测变量来指示每个支票金额是否为 1000 的倍是有意义的。我们可以将其命名为 `check_amount_mult_1000`。

从我们的探索性工作中，我们发现 `check_signed` 和 `check_amount` 是支票欺诈的有用预测变量。在得出这些见解时，我们产生了统计摘要、过滤了数据并创建了图表。我们需要创意并尝试不同的方法，因为预测变量并不是一而易见的。

# 11.2 世界幸福报告

《世界幸福报告》是对 117 个国家全球幸福状况的年度调查。我们将查看 2018 年报告的数据 [34]。更多信息可以在此处找到：

https://www.happiness.report/ed/2018/

数据集可以在此处找到：

https://www.kaggle.com/unsdsn/world-happiness

2018 年的数据保存在课程仓库中，我们将从那里加载它。

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

d = pd.read_csv('./datasets/Country_Happiness.csv')
df.head(2)
```

输出：

| Country | Happy | WH | WL | Dys | GDP | Social | Health | Free |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Finland | 7.632 | 7.695 | 7.569 | 2.595 | 1.305 | 1.592 | 0.874 | 0.681 |
| Norway | 7.594 | 7.657 | 7.530 | 2.383 | 1.465 | 1.582 | 0.861 | 0.686 |

每行代表一个唯一的国家，列名是缩写，某些列由于边距限制被隐藏。我们将关注作为目标的幸福评分（Happy），以及有助于提高生活的六个因素：经济生产（GDP）、社会支持（Social）、预期寿命（Health）、自由（Free）和对腐败的感知（Corruption）。受访者被要求从 0（最差）到 10（最好）对他们的幸福进行评分。假设是这六个因素有助于幸福评分，无论是直接地（它们同步上升）还是反地（它们相反移动）。

首先，让我们生成幸福评分和因素的直方图以了解其分布。代码所示，并带有直方图示例。

```python
# 排除我们不会绘制的变量
vars_exclude = ['Country','Whisker-high','Whisker-low']

# 遍历 dataframe 中的每个变量
for var in df.columns:
    # 如果变量不在排除列表中则执行
    if var not in vars_exclude:
        # 绘制变量的直方图
        sns.histplot(df[var])
        plt.show()
```

幸福评分范围从 2.91 到 7.63，大多数分数落在 4.5 到 6.5 之间。最低分远高于零，最高分远低于 10。![](img/7f40a2246fd3d2d5353d109f489c4e33_220_0.png)

图 11.3：幸福评分分布

社会支持因素范围从 0 到 1.64，且向左偏。这意味着分布在峰值的左侧较长，峰值出现在 1.3 左右。![](img/7f40a2246fd3d2d5353d109f489c4e33_223_0.png)

图 11.4：社会支持因素分布

腐败因素从 0 到 0.46。75% 的值低于 0.14，且向右偏。![](img/7f40a2246fd3d2d5353d109f489c4e33_223_1.png)

图 11.5：腐败因素分布

可视化数据分布另一个有用图是箱线图。图 11.6 显示了幸福评分的箱线图，带有五个数值：
- 最大值出现在顶部的水平线（7.63）
- 第 75 分位数形成箱体顶部（6.17）
- 中位数，或第 50 分位数，是箱体中的水平线（5.38）
- 第 25 分位数形成箱体底部（4.45）
- 最小值出现在底部的水平线（2.91）

![](img/7f40a2246fd3d2d5353d109f489c4e33_224_0.png)

图 11.6：幸福评分箱线图

箱线图提供的细节比直方图少，但更容易解释。此外，几个箱线图可以很容易比较。

```python
sns.boxplot(data=df['Happiness score'], width=0.4)
```

接下来，让我们查看数据的双变量图以理解因素与目标之间的关系。我们创建一个幸福与社会支持的散点图：

```python
sns.scatterplot(x='Explained by: Social support', y='Happiness score', data=df)
```

![](img/7f40a2246fd3d2d5353d109f489c4e33_224_1.png)

图 11.7：幸福评分与社会支持

# 世界幸福报告

图 11.7 显示了社会支持与幸福之间的直接关系；它们倾向于共同移动。相关性为 0.76，表明存在强正（线性）相关。

接下来，我们创建一个幸福与腐败的散点图：

```python
sns.scatterplot(x='Explained by: Perceptions of corruption', y='Happiness score', data=df)
```

![](img/7f40a2246fd3d2d5353d109f489c4e33_225_0.png)

图 11.8：幸福评分与腐败

这里没有明显的直接关系，右侧有一些离群值。0.41 的相关性表明直接关系较弱。

我们分别为基础变量了单变量图和散点图以查看它们的协方差。联合图（图 11.9）将散点图与基础变量的直方图相结合：

```python
sns.jointplot(x='Explained by: Social support', y='Happiness score', data=df)
```

注意我们通过将子图更改为 jointplot 将散点图改为联合图。seaborn 接口使得这非常简单。

使用 pandas 计算相关性非常直接。所有的两两相关性都可以在 `df.corr()` 命令在 dataframe 中计算。如果我们只需要目标列的相关性，可以对列进行子集：

```python
df.corr(['Happiness score'])
```

输出：

![](img/7f40a2246fd3d2d5353d109f489c4e33_226_0.png)

图 11.9：幸福评分与腐败的联合图

| | Happiness score |
| :--- | :--- |
| Happiness score | 1.000000 |
| Whisker-high | 0.999553 |
| Whisker-low | 0.999571 |
| Dystopia (1.92) + residual | 0.473606 |
| Explained by: GDP per capita | 0.807338 |
| Explained by: Social support | 0.764656 |
| Explained by: Healthy life expectancy | 0.777484 |
| Explained by: Freedom to make life choices | 0.562290 |
| Explained by: Generosity | 0.142030 |
| Explained by: Perceptions of corruption | 0.408650 |

这显示相关性性因素是 GDP，而慷慨的相关性最弱。

最后，seaborn 可以通过 `pairplot` 分别绘制所有两两和每对关系的联合及边缘分布。图 11.10 中的图数据密度很高，无法快速理解整体模式。由于列名很长，首先通过传递的“旧名：新名”对对对它们进行缩写。

```python
# 缩写列名
df.rename(columns={
'Country' : 'country',
'Happiness score' : 'happy',
'Whisker-high' : 'wh',
'Whisker-low' : 'wl',
})
```

