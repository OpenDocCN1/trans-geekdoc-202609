
# 数据透视与熔化

在 Pandas 中，数据透视和熔化涉及通过改变数据结构来重塑数据，而不改变实际数据。透视将数据从长格式转换为宽格式，而熔化则执行相反的操作。

## 使用 `pivot()` 方法透视 DataFrame

透视 DataFrame 意味着根据现有列设置索引、列和值来重塑它。`pivot()` 方法接受三个主要参数：`index`、`columns` 和 `values`。

例如，假设你想创建一个透视表，以显示给定数据集中每个地理区域和性别组合的平均信用评分：

```
# 计算每个地理区域和性别组合的平均信用评分
average_credit_score = data.groupby(['Geography', 'Gender'])['CreditScore'].mean().reset_index()

# 透视 DataFrame
pivot_data = average_credit_score.pivot(index='Geography', columns='Gender', values='CreditScore')
```

生成的 `pivot_data` DataFrame 将以 `Geography` 为索引，`Gender` 为列，平均信用评分为值。

## 使用 `melt()` 函数熔化 DataFrame

熔化 DataFrame 意味着通过将多列移动到单个列中，将其从宽格式重塑为长格式。`melt()` 函数接受三个主要参数：`id_vars`、`value_vars` 和 `var_name`。

例如，让我们将 `pivot_data` DataFrame 熔化回长格式：

```
melted_data = pd.melt(pivot_data.reset_index(), id_vars='Geography', value_vars=['Female', 'Male'], var_name='Gender', value_name='AverageCreditScore')
```

生成的 `melted_data` DataFrame 将具有长格式，包含 `Geography`、`Gender` 和 `AverageCreditScore` 列。

总之，Pandas 中的数据透视和熔化是重塑数据而不改变实际数据的技术。透视涉及使用 `pivot()` 方法将数据从长格式转换为宽格式，而熔化涉及使用 `melt()` 函数将数据从宽格式转换为长格式。这些技术可以通过改变数据结构，帮助你更好地理解、可视化和分析数据。

# 数据转换函数：`apply()`、`map()` 和 `applymap()`

Pandas 提供了数据转换函数，包括 `apply()`、`map()` 和 `applymap()`，它们提供了将自定义函数应用于 DataFrame 或 Series 中的单个元素、行或列的能力。这些函数以高度适应性和高效的方式实现数据操作和转换。利用这些函数，数据可以被转换和操作以满足特定需求。`apply()` 将函数应用于 DataFrame 的每个元素或行/列，而 `map()` 将函数应用于 Series 的每个元素。`applymap()` 将函数应用于 DataFrame 的每个元素。这一系列函数提供了一个全面的工具包来转换和操作数据。

## `apply()` 函数

`apply()` 函数用于沿 DataFrame 的轴（行或列）或应用于 Series 应用函数。

例如，假设你想计算 `data` DataFrame 中每个数值列的极差（最大值-最小值）：

```
def col_range(col):
    return col.max() - col.min()

column_ranges = data.apply(col_range)
```

`apply()` 函数也可以与 lambda 函数一起使用。要获得与上述相同的结果：

```
column_ranges = data.apply(lambda col: col.max() - col.min())
```

## `map()` 函数

`map()` 函数用于将函数应用于 Series 的每个元素。当你想对单个列执行逐元素转换时，它非常有用。

例如，假设你想将 `data` DataFrame 中的 `Geography` 列更新为大写值：

```
data['Geography'] = data['Geography'].map(lambda x: x.upper())
```

## `applymap()` 函数

`applymap()` 函数用于将函数应用于 DataFrame 的每个元素。当你想对多列执行逐元素转换时，它非常有用。

例如，假设你想将 `data` DataFrame 中所有数值列四舍五入为整数：

```
numeric_cols = data.select_dtypes(include='number').columns
data[numeric_cols] = data[numeric_cols].applymap(lambda x: round(x))
```

总之，Pandas 中的数据转换函数如 `apply()`、`map()` 和 `applymap()` 允许你将特定函数应用于 DataFrame 或 Series 中的元素、行或列。`apply()` 函数用于沿 DataFrame 的轴或应用于 Series 应用函数，`map()` 函数用于将函数应用于 Series 的每个元素，`applymap()` 函数用于将函数应用于 DataFrame 的每个元素。这些函数帮助你以灵活高效的方式转换和操作数据。

# 数据分组与聚合

在 Pandas 中，分组和聚合数据的过程涉及使用 `groupby()` 函数根据一个或多个列对数据进行分组，随后对分组后的数据应用聚合函数。当根据特定类别或类别组合分析数据时，此技术非常有用。通过 `groupby()` 函数，可以将数据组织成具有相似值的组，并对这些组内的数据执行数学运算。分组和聚合数据有助于更好地理解数据集中的模式，并有助于识别原本可能不易察觉的趋势或洞察。

让我们使用 `Customer_Churn_Modelling.csv` 数据集演示一个示例。我们将按 `Geography` 和 `Gender` 对数据进行分组，并计算每组的平均信用评分。

## 读取数据

```
import pandas as pd
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")
```

## 使用 `groupby()` 分组数据

```
grouped_data = data.groupby(['Geography', 'Gender'])
```

这将创建一个按 `Geography` 和 `Gender` 分组数据的 `groupby` 对象。现在你可以对分组后的数据应用聚合函数。

## 使用聚合函数聚合数据

在本例中，我们将使用 `mean()` 函数计算每组的平均信用评分：

```
average_credit_scores = grouped_data['CreditScore'].mean()
```

`average_credit_scores` 变量现在包含一个 Series，其中存有每个 `Geography` 和 `Gender` 组合的平均信用评分。

你也可以使用 `agg()` 函数一次性应用多个聚合函数。例如，让我们计算每组的平均、最小和最大信用评分：

```
credit_score_summary = grouped_data['CreditScore'].agg(['mean', 'min', 'max'])
```

`credit_score_summary` 变量现在包含一个 DataFrame，其中存有每个 `Geography` 和 `Gender` 组合的平均、最小和最大信用评分。

总之，Pandas 中的分组和聚合数据涉及使用 `groupby()` 函数根据一个或多个列对数据进行分组，然后对分组后的数据应用聚合函数。这对于按特定类别或类别组合分析数据非常有用。在给定示例中，我们按 `Geography` 和 `Gender` 对数据进行分组，并计算了每组的平均信用评分。
