
# 使用索引和选择修改数据

Pandas 提供了索引和选择技术，这些技术不仅允许选择数据，还允许修改 DataFrame 内部的数据。除了选择数据，这些技术还能对 DataFrame 中特定的数据子集进行更改，例如更新或替换值、添加或删除列或行等。这种数据操作的灵活性有助于各种数据分析任务，并允许用户高效地执行复杂操作。

以下是一些使用索引和选择方法修改数据的示例：

## 使用 `.at[]` 属性修改单个值

`.at[]` 属性可用于根据行和列标签修改 DataFrame 中的单个值。例如，假设您已将 `'CustomerId'` 列设置为索引：

```python
data.at[15745662, 'CreditScore'] = 750
```

这会将 ID 为 `15745662` 的客户的 `'CreditScore'` 值设置为 `750`。

## 使用 `.iat[]` 属性修改单个值

与 `.at[]` 属性类似，您可以使用 `.iat[]` 属性根据行和列位置修改 DataFrame 中的单个值：

```python
data.iat[0, 0] = 750
```

这会将第一行第一列的值设置为 `750`。

## 使用布尔索引修改列中的多个值

您可以使用布尔索引根据条件修改列中的多个值。例如，将所有年龄大于 `40` 的客户的 `'CreditScore'` 增加 `10` 分：

```python
mask = data['Age'] > 40
data.loc[mask, 'CreditScore'] += 10
```

## 使用 `.apply()` 方法修改列中的值

您可以使用 `.apply()` 方法将自定义函数应用于列中的每个值。例如，将 `'CreditScore'` 值四舍五入到最近的 `10` 的倍数：

```python
import numpy as np

def round_to_nearest_ten(x):
    return np.round(x, -1)

data['CreditScore'] = data['CreditScore'].apply(round_to_nearest_ten)
```

## 使用 `.applymap()` 方法修改多列中的值

您可以使用 `.applymap()` 方法将自定义函数应用于多列中的每个值。例如，将所有数值列四舍五入到最近的整数：

```python
numerical_columns = ['CreditScore', 'Age', 'Tenure', 'Balance', 'NumOfProducts', 'EstimatedSalary']
data[numerical_columns] = data[numerical_columns].applymap(np.round)
```

总之，您可以使用 Pandas 中的索引和选择技术，如 `.at[]`、`.iat[]`、布尔索引、`.apply()` 和 `.applymap()` 方法来修改 DataFrame 中的数据。这些技术对于各种数据分析、清洗和转换任务非常有用。

# 高级索引技术

## 截面 (`xs()`) 方法

`xs()` 方法允许您根据多级索引 DataFrame 的特定层级选择数据。当您拥有具有层次化索引的 DataFrame 时，这非常有用。让我们创建一个以 `'Geography'` 和 `'Gender'` 为索引层级的多级索引 DataFrame：

```python
multi_indexed_data = data.set_index(['Geography', 'Gender'])
```

现在，您可以使用 `xs()` 方法选择特定层级的数据：

```python
german_customers = multi_indexed_data.xs('Germany', level='Geography')
```

## `where()` 方法

`where()` 方法允许您根据条件筛选数据，同时保持 DataFrame 的原始形状。当您想要保留 DataFrame 结构或可视化数据时，这非常有用。例如，仅保留 `'Exited'` 等于 `1` 的行，并将其他行替换为 `NaN`：

```python
exited_customers = data.where(data['Exited'] == 1)
```

## `mask()` 方法

`mask()` 方法的工作方式与 `where()` 方法类似，但会反转条件。它不是保留满足条件的数据点，而是将它们替换为 `NaN` 或指定值。例如，将所有流失客户的 `'CreditScore'` 值替换为 `NaN`：

```python
data['CreditScore'] = data['CreditScore'].mask(data['Exited'] == 1)
```

## `isin()` 方法

`isin()` 方法允许您根据值是否在给定列表中来筛选数据。当您想要选择特定类别或组的数据时，这非常有用。例如，选择 `'Geography'` 为 `'France'` 或 `'Germany'` 的行：

```python
selected_countries = data[data['Geography'].isin(['France', 'Germany'])]
```

## `eval()` 方法

`eval()` 方法允许您计算涉及 DataFrame 列的复杂表达式。当您想要执行涉及多列的算术运算或布尔条件时，这非常有用。例如，计算每个客户的 `'Balance'` 与 `'EstimatedSalary'` 的比率：

```python
data['BalanceToSalaryRatio'] = data.eval("Balance / EstimatedSalary")
```

总之，Pandas 中的高级索引技术，如 `xs()`、`where()`、`mask()`、`isin()` 和 `eval()` 方法，可以帮助您更高效地访问和操作给定数据库中的数据。这些技术提供了更大的灵活性，对于各种数据分析、清洗和转换任务非常有用。

# 总结

我们讨论了 Pandas 中不同的索引和选择方法，包括 `.loc[]`、`.iloc[]` 和 `.at[]`。`.loc[]` 属性用于基于标签的索引，允许您通过行和列标签选择数据。`.iloc[]` 属性用于基于整数（位置）的索引，允许您通过行和列位置选择数据。`.at[]` 属性用于标量值的快速基于标签的索引，并针对访问单个数据点进行了优化。

然后我们讨论了使用索引和选择技术修改数据。`.at[]` 和 `.iat[]` 属性可用于根据行和列标签或位置修改 DataFrame 中的单个值。布尔索引允许您根据条件修改列中的多个值。`.apply()` 方法可用于将自定义函数应用于列中的每个值，而 `.applymap()` 方法可用于将自定义函数应用于多列中的每个值。

接下来，我们介绍了 Pandas 中的高级索引技术，包括 `xs()`、`where()`、`mask()`、`isin()` 和 `eval()` 方法。`xs()` 方法允许您根据多级索引 DataFrame 的特定层级选择数据。`where()` 方法根据条件筛选数据，同时保持 DataFrame 的原始形状。`mask()` 方法的工作方式与 `where()` 方法类似，但会反转条件，将满足条件的数据点替换为 `NaN` 或指定值。`isin()` 方法根据值是否在给定列表中筛选数据，适用于选择特定类别或组的数据。`eval()` 方法计算涉及 DataFrame 列的复杂表达式，适用于执行涉及多列的算术运算或布尔条件。

这些索引、选择和高级技术提供了灵活高效的方式来访问、操作和修改 Pandas DataFrame 中的数据。它们是数据分析、清洗和转换任务的必备工具。

# 第 4 章：数据操作与转换
