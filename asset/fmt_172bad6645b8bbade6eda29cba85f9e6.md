
Pandas 提供了索引和选择技术，这些技术不仅允许选择数据，还允许修改 DataFrame 内部的数据。除了选择数据，这些技术还能对 DataFrame 中特定的数据子集进行更改，例如更新或替换值、添加或删除列或行等。这种数据操作的灵活性有助于各种数据分析任务，并允许用户高效地执行复杂操作。

以下是一些使用索引和选择方法修改数据的示例：

### 使用 `.at[]` 属性修改单个值

`.at[]` 属性可用于根据行和列标签修改 DataFrame 中的单个值。例如，假设您已将 `'CustomerId'` 列设置为索引：

```python
data.at[15745662, 'CreditScore'] = 750
```

这会将 ID 为 `15745662` 的客户的 `'CreditScore'` 值设置为 `750`。

### 使用 `.iat[]` 属性修改单个值

与 `.at[]` 属性类似，您可以使用 `.iat[]` 属性根据行和列位置修改 DataFrame 中的单个值：

```python
data.iat[0, 0] = 750
```

这会将第一行第一列的值设置为 `750`。

### 使用布尔索引修改列中的多个值

您可以使用布尔索引根据条件修改列中的多个值。例如，将所有年龄大于 `40` 的客户的 `'CreditScore'` 增加 `10` 分：

```python
mask = data['Age'] > 40
data.loc[mask, 'CreditScore'] += 10
```

### 使用 `.apply()` 方法修改列中的值

您可以使用 `.apply()` 方法将自定义函数应用于列中的每个值。例如，将 `'CreditScore'` 值四舍五入到最近的 `10` 的倍数：

```python
import numpy as np

def round_to_nearest_ten(x):
    return np.round(x, -1)

data['CreditScore'] = data['CreditScore'].apply(round_to_nearest_ten)
```

### 使用 `.applymap()` 方法修改多列中的值

您可以使用 `.applymap()` 方法将自定义函数应用于多列中的每个值。例如，将所有数值列四舍五入到最近的整数：

```python
numerical_columns = ['CreditScore', 'Age', 'Tenure', 'Balance', 'NumOfProducts', 'EstimatedSalary']
data[numerical_columns] = data[numerical_columns].applymap(np.round)
```

总之，您可以使用 Pandas 中的索引和选择技术，如 `.at[]`、`.iat[]`、布尔索引、`.apply()` 和 `.applymap()` 方法来修改 DataFrame 中的数据。这些技术对于各种数据分析、清洗和转换任务非常有用。

## 高级索引技术

### 截面 (`xs()`) 方法

`xs()` 方法允许您根据多级索引 DataFrame 的特定层级选择数据。当您拥有具有层次化索引的 DataFrame 时，这非常有用。让我们创建一个以 `'Geography'` 和 `'Gender'` 为索引层级的多级索引 DataFrame：

```python
multi_indexed_data = data.set_index(['Geography', 'Gender'])
```

现在，您可以使用 `xs()` 方法选择特定层级的数据：

```python
german_customers = multi_indexed_data.xs('Germany', level='Geography')
```

### `where()` 方法

`where()` 方法允许您根据条件筛选数据，同时保持 DataFrame 的原始形状。当您想要保留 DataFrame 结构或可视化数据时，这非常有用。例如，仅保留 `'Exited'` 等于 `1` 的行，并将其他行替换为 `NaN`：

```python
exited_customers = data.where(data['Exited'] == 1)
```

### `mask()` 方法

`mask()` 方法的工作方式与 `where()` 方法类似，但会反转条件。它不是保留满足条件的数据点，而是将它们替换为 `NaN` 或指定值。例如，将所有流失客户的 `'CreditScore'` 值替换为 `NaN`：

```python
data['CreditScore'] = data['CreditScore'].mask(data['Exited'] == 1)
```

### `isin()` 方法

`isin()` 方法允许您根据值是否在给定列表中来筛选数据。当您想要选择特定类别或组的数据时，这非常有用。例如，选择 `'Geography'` 为 `'France'` 或 `'Germany'` 的行：

```python
selected_countries = data[data['Geography'].isin(['France', 'Germany'])]
```

### `eval()` 方法

`eval()` 方法允许您计算涉及 DataFrame 列的复杂表达式。当您想要执行涉及多列的算术运算或布尔条件时，这非常有用。例如，计算每个客户的 `'Balance'` 与 `'EstimatedSalary'` 的比率：

```python
data['BalanceToSalaryRatio'] = data.eval("Balance / EstimatedSalary")
```

总之，Pandas 中的高级索引技术，如 `xs()`、`where()`、`mask()`、`isin()` 和 `eval()` 方法，可以帮助您更高效地访问和操作给定数据库中的数据。这些技术提供了更大的灵活性，对于各种数据分析、清洗和转换任务非常有用。

## 总结

我们讨论了 Pandas 中不同的索引和选择方法，包括 `.loc[]`、`.iloc[]` 和 `.at[]`。`.loc[]` 属性用于基于标签的索引，允许您通过行和列标签选择数据。`.iloc[]` 属性用于基于整数（位置）的索引，允许您通过行和列位置选择数据。`.at[]` 属性用于标量值的快速基于标签的索引，并针对访问单个数据点进行了优化。

然后我们讨论了使用索引和选择技术修改数据。`.at[]` 和 `.iat[]` 属性可用于根据行和列标签或位置修改 DataFrame 中的单个值。布尔索引允许您根据条件修改列中的多个值。`.apply()` 方法可用于将自定义函数应用于列中的每个值，而 `.applymap()` 方法可用于将自定义函数应用于多列中的每个值。

接下来，我们介绍了 Pandas 中的高级索引技术，包括 `xs()`、`where()`、`mask()`、`isin()` 和 `eval()` 方法。`xs()` 方法允许您根据多级索引 DataFrame 的特定层级选择数据。`where()` 方法根据条件筛选数据，同时保持 DataFrame 的原始形状。`mask()` 方法的工作方式与 `where()` 方法类似，但会反转条件，将满足条件的数据点替换为 `NaN` 或指定值。`isin()` 方法根据值是否在给定列表中筛选数据，适用于选择特定类别或组的数据。`eval()` 方法计算涉及 DataFrame 列的复杂表达式，适用于执行涉及多列的算术运算或布尔条件。

这些索引、选择和高级技术提供了灵活高效的方式来访问、操作和修改 Pandas DataFrame 中的数据。它们是数据分析、清洗和转换任务的必备工具。

# 第 4 章：数据操作与转换

## 在 Pandas 中合并和连接 DataFrame

在 Pandas 中，基于公共列或索引组合两个或多个 DataFrame 的过程可以通过合并和连接来实现。这些操作在管理多个相关数据集方面起着关键作用，允许进行高效的数据分析和操作。通过合并 DataFrame，可以基于共享列组合数据，从而生成一个包含所有相关信息的单个 DataFrame。另一方面，连接 DataFrame 则基于其索引实现两个或多个 DataFrame 的组合。这两种技术都有助于简化数据管理、提高数据质量，并更好地理解数据集之间的关系。因此，理解如何在 Pandas 中合并和连接 DataFrame 是数据分析师和科学家的一项重要技能。

为了演示，假设您有另一个包含客户收入数据的数据集。我们将创建一个名为 `customer_income` 的小型 DataFrame，它与 `data` DataFrame 具有相同的 `CustomerId` 列：

```python
import pandas as pd
customer_income = pd.DataFrame({
    'CustomerId': [15745662, 15734523, 15698723],
    'AnnualIncome': [55000, 68000, 45000]
})
```

### 使用 `merge()` 函数合并 DataFrame

`merge()` 函数基于公共列组合 DataFrame。默认情况下，它执行内连接，这意味着只有在公共列中具有匹配值的行才会包含在结果中。

```python
merged_data = pd.merge(data, customer_income, on='CustomerId')
```

您可以通过使用 `how` 参数指定连接类型：

*   `'left'`：仅使用左侧 DataFrame 的键
*   `'right'`：仅使用右侧 DataFrame 的键
*   `'outer'`：使用两个 DataFrame 的键
*   `'inner'`：使用两个 DataFrame 键的交集（默认）

例如，执行左连接：

```python
merged_data_left = pd.merge(data, customer_income, on='CustomerId', how='left')
```

### 使用 `join()` 方法连接 DataFrame

`join()` 方法用于基于其索引组合 DataFrame。默认情况下，它执行左连接，这意味着它使用左侧 DataFrame 的索引并包含其所有行。

首先，让我们将 `CustomerId` 设置为两个 DataFrame 的索引：

```python
data = data.set_index('CustomerId')
customer_income = customer_income.set_index('CustomerId')
```

现在，您可以连接 DataFrame：

```python
joined_data = data.join(customer_income)
```

您也可以像使用 `merge()` 函数一样，使用 `how` 参数指定连接类型。

总之，Pandas 中的合并和连接 DataFrame 允许您基于公共列或索引组合两个或多个 DataFrame。`merge()` 函数基于公共列组合 DataFrame，而 `join()` 方法基于其索引组合 DataFrame。在处理多个相关数据集时，这些操作至关重要，并且可以调整为执行各种类型的连接（内连接、左连接、右连接和外连接），具体取决于您的需求。

## 连接和追加 DataFrame

在 Pandas 中，合并和添加 DataFrame 是指沿特定轴（水平或垂直）连接两个或多个 DataFrame 的过程。当您拥有具有相同行或列的多个数据集并希望将它们堆叠在一起时，此技术非常有用。连接和追加是 Pandas 中组合 DataFrame 的两种方法。连接用于将 DataFrame 堆叠在彼此之上或并排，而追加则向现有 DataFrame 添加新行。这两种方法在创建包含来自原始数据集所有必要信息的单个 DataFrame 时都很有用。

为了演示，假设您有两个数据集 `data1` 和 `data2`，它们是原始 `data` DataFrame 的子集：

```python
data1 = data.head(10)
data2 = data.tail(10)
```

### 使用 `concat()` 函数连接 DataFrame

`concat()` 函数沿特定轴组合 DataFrame。默认情况下，它沿行（`axis=0`）连接 DataFrame。下面展示如何连接 `data1` 和 `data2`：

```python
concatenated_data = pd.concat([data1, data2])
```

要沿列连接 DataFrame，请将 `axis` 参数设置为 1：

```python
concatenated_data_columns = pd.concat([data1, data2], axis=1)
```

请记住，当沿列连接 DataFrame 时，它们拥有相同的索引至关重要。否则，结果中可能会出现缺失值。

### 使用 `append()` 方法追加 DataFrame

`append()` 方法是沿行组合 DataFrame 的一种便捷方式，类似于使用 `concat()` 函数沿行连接。您可以按如下方式将 `data2` 追加到 `data1`：

```python
appended_data = data1.append(data2)
```

请注意，`append()` 方法不会修改原始 DataFrame；它会创建一个包含组合数据的新 DataFrame。

总之，Pandas 中的连接和追加 DataFrame 允许您沿特定轴（行或列）组合两个或多个 DataFrame。`concat()` 函数沿指定轴组合 DataFrame，而 `append()` 方法是沿行组合 DataFrame 的一种便捷方式。当您拥有具有相同列或行的多个数据集并希望将它们堆叠在一起时，这些操作非常有用。

### 连接和追加的示例程序

让我们使用给定的 `Customer_Churn_Modelling.csv` 数据集创建另一个示例。我们将首先用原始数据的不同子集创建两个新 DataFrame，然后连接和追加它们。

#### 将原始数据拆分为两个子集

```python
# Read the original data
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")

# Create subsets of data for customers from France and Spain
data_france = data[data['Geography'] == 'France']
data_spain = data[data['Geography'] == 'Spain']
```

#### 连接 DataFrame

```python
# Concatenate the DataFrames along the rows (axis=0)
concatenated_data = pd.concat([data_france, data_spain])
```

#### 追加 DataFrame

```python
# Append 'data_spain' to 'data_france'
appended_data = data_france.append(data_spain)
```

`concatenated_data` 和 `appended_data` 都将包含原始 DataFrame 中来自法国和西班牙的客户的行。尽管在这个例子中连接和追加 DataFrame 沿行的结果相同，但这些技术可以根据您的需求用于不同的场景。请记住，`concat()` 可用于沿行或列组合 DataFrame，而 `append()` 专门用于沿行组合 DataFrame。

## 数据透视与熔化

在 Pandas 中，数据透视和熔化涉及通过改变数据结构来重塑数据，而不改变实际数据。透视将数据从长格式转换为宽格式，而熔化则执行相反的操作。

### 使用 `pivot()` 方法透视 DataFrame

透视 DataFrame 意味着根据现有列设置索引、列和值来重塑它。`pivot()` 方法接受三个主要参数：`index`、`columns` 和 `values`。

例如，假设你想创建一个透视表，以显示给定数据集中每个地理区域和性别组合的平均信用评分：

```python
# 计算每个地理区域和性别组合的平均信用评分
average_credit_score = data.groupby(['Geography', 'Gender'])['CreditScore'].mean().reset_index()

# 透视 DataFrame
pivot_data = average_credit_score.pivot(index='Geography', columns='Gender', values='CreditScore')
```

生成的 `pivot_data` DataFrame 将以 `Geography` 为索引，`Gender` 为列，平均信用评分为值。

### 使用 `melt()` 函数熔化 DataFrame

熔化 DataFrame 意味着通过将多列移动到单个列中，将其从宽格式重塑为长格式。`melt()` 函数接受三个主要参数：`id_vars`、`value_vars` 和 `var_name`。

例如，让我们将 `pivot_data` DataFrame 熔化回长格式：
