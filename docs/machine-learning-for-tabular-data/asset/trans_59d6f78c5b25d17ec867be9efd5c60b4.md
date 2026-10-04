

# 第 4 章 表格数据的经典算法

图 4.1 所示的分布极度右偏，许多离群值（绘图值）高达 10,000。然而，在 2,000 之前，很难区分出任何表示此类频率的条形。通过绘制箱线图（boxplot），这一点变得更加明显，当人们想要可视化变量分布的核心部分时，箱线图是一个非常有用的工具。变量的箱线图是将分布的关键测量值描绘为一个带有“须线”的箱子：须线是箱子外的两条线，延伸到变量分布的预期范围。箱体由四分位距（IQR）界定，由第 25 分位数和第 75 分位数确定，并被中位数线分为两部分。须线上下延伸到 IQR 的 1.5 倍。边缘以上或以下的所有内容都被视为离群值：即异常或意料之外的值。让我们使用 pandas DataFrame 的内置方法 `boxplot` 方法为价格变量绘制箱线图（见 4.2）：

![](img/def89cc476fa39f4c54bd34e78d91674_124_0.png)

并不意外的是，箱体和须线被挤在图表的下半部分，几乎相互不可分。一长串离群值从箱线图上端的上限延伸出来。这是一个明显的偏态分布案例。在这种情况下，修复变量的标准解决方案是对目标进行对数变换（logarithmic transformation）。通常做法是添加一个常数，将值偏移到正数范围，以便处理零及以下的值。在我们的案例中，这是没有必要的，因为所有值都是正数且大于零。在下面的代码段中，我们通过应用对数变换表示转换后的价格特征（见图 4.3 和 4.4）：

```python
np.log1p(data['price'])
```

![](img/def89cc476fa39f4c54bd34e78d91674_125_0.png)

图 4.3 对数变换后 Price 特征更加对称的直方图

![](img/def89cc476fa39f4c54bd34e78d91674_125_1.png)

图 4.4 对数变换后 Price 特征的箱线图，表明分布两端仍然存在极值

现在，由新直方图和箱线图表示的分布更加对称，尽管显然分布的两侧都有离群观测值。由于我们的目的是为了说明性，我们可以忽略原始分布并关注有意义的目标。例如，我们可以只保留低于 1,000 的价格值（见图 4.5）。在下面的代码段中，我们生成了一个只关注 1,000 以下价格值的直方图：

```python
data[["price"]][data.price <= 1000].hist(bins=20)
```

![](img/def89cc476fa39f4c54bd34e78d91674_126_0.png)

这里代表的分布仍然是右偏，但它类似于电子商务或其他具有长尾产品销售场景中常见的分布。此外，如果我们关注 50 到 200 之间的范围，分布将看起来更加均匀（见图 4.6）。在下面的代码段中，我们进一步将关注范围限制在 50 到 200 之间的价格，并绘制生成的直方图：

```python
data["price"][(data.price >= 50) & (data.price <= 200)].hist(bins=20)
```

![](img/def89cc476fa39f4c54bd34e78d91674_126_1.png)

因此，我们可以创建两个由布尔值掩码变量，可以帮助我们根据想要使用的算法类型过滤目标。`price_capped` 变量在演示某些机器学习算法如何轻松处理长尾时将非常有用：

```python
price_capped = data.price >= 1000
price_window = (data.price >= 50) & (data.price <= 200)
```

图 4.7 显示了相对于封顶价格的箱线图，它呈现出右侧离群值，但至少箱线图是可见的。

![](img/def89cc476fa39f4c54bd34e78d91674_127_0.png)

图 4.8 显示了相对于窗口价格的箱线图，没有任何离群值的迹象：

```python
data["price"] [price_window].boxplot()
```

![](img/def89cc476fa39f4c54bd34e78d91674_127_1.png)

在完成对预测变量和目标的探索后，我们准备了四个不同的目标将我们的示例：

```python
target_mean = (data["price"] > data["price"].mean()).astype(int)
target_median = (data["price"] > data["price"].median()).astype(int)
target_multiclass = pd.qcut(data["price"], q=5, labels=False)
target_regression = data["price"]
```

# 第 4 章 表格数据的经典算法

我们准备了两个二分类目标 `target_mean` 和 `target_median`，以及一个基于分位数具有五个不同类别的多分类目标用于分类。

特别重要的是，我们要注意到我们的 `target_median` 是一个平衡二分类目标。因此，我们可以安全地使用准确率（accuracy）作为良好的性能衡量。作为测试，如果你尝试计算这些值，你会得到正负类的案例数量几乎相等：

```python
target_median.value_counts()
```

你得到结果

```
0 24472
1 24423
```

相反，如果你对 `target_mean` 目标变量尝试相同的操作，你会得到

```python
target_mean.value_counts()
```

你将获得一个向负例倾斜的不平衡分布；也就是说，由于我们之前观察到的偏态分布，低于平均值的情况更多：

```
0 34016
1 14879
```

在这种情况下，评估机器学习分类器的结果时，我们倾向于使用受试者工作曲线下面积（ROC-AUC）或平均精确率（Average Precision）等指标。最后，对于多分类目标，计数显示它们也是平衡的：

```python
target_multiclass.value_counts()
```

该命令返回结果

```
0 10063
1 9835
2 9804
3 10809
4 8384
```

对于回归目标，`target_regression` 是原始转换的原始。然而，我们使用子集并根据我们将演示的机器学习算法对其转换。

在完成对预测变量、目标以及在下一节中基础特征选择的探索后，我们准备好了四个不同的目标。使用构建方法，我们将准备一些

# 探索并处理 Airbnb 数据集的特征

配合我们对表格数据机器学习选项发现的管道

## 4.2.2 管道准备

我们将使用之前过的 `Pipeline` 和 `ColumnTransformer` 类来准备管道。在构建块方法中，我们首先创建适用于数据类型的不同操作。

下面的代码定义了可以重复使用的三个过程：

- 类别特征独热编码——类别特征被转换为二进制特征。如果某个值从未出现过，它将被忽略。
- 数值透传——使用零填充数值值。
- 数值标准化——在填充缺失值后，通过减去平均值并除以标准差对数值进行缩放。

定义这些过程的代码如下所示：

| 列表 4.2 为表格学习管道设置构建块 |
| :--- |
| from sklearn.pipeline import Pipeline |
| sklearn.compose import ColumnTransformer |
| sklearn.preprocessing import OneHotEncoder |
| sklearn.preprocessing import OrdinalEncoder |
| sklearn.impute import SimpleImputer |
| sklearn.preprocessing import StandardScaler |

```python
categorical_onehot_encoding = OneHotEncoder(
    handle_unknown='ignore')
numeric_passsthrough = SimpleImputer(
    strategy='constant', fill_value=0)
numeric_standardization = Pipeline(
    ('imputation', SimpleImputer(strategy='median')),
    ('standardization', StandardScaler())
))
```

> 将类别特征转换为独热格式

> 将数值值替换为零

> 管道替换缺失值并标准化特征

此时，我们可以根据每个机器学习算法的需求组合转换管道。例如，在这个例例中，我们设置了一个管道，它会对类别特征进行编码，并对数值特征仅填充缺失值为零。这样的管道由 `ColumnTransformer` 函数创建，它是一个同时对不同特征集进行操作的胶水函数。对于大多数机器学习模型来说，这都是极佳的转换策略：

```python
column_transform = ColumnTransformer(
    ['categories',
```

