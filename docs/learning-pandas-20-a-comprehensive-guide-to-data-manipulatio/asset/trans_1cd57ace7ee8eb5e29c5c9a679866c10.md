

# Pandas 数据结构

Pandas 为数据操作和分析提供了两种主要数据结构：`Series` 和 `DataFrame`。这两种数据结构均构建在 NumPy 数组之上，从而实现高效且高性能的操作。以下是 `Series` 和 `DataFrame` 及其工作原理的详细解释。

## Series

`Series` 是一种一维的、带标签的数组，能够容纳任何数据类型，包括整数、浮点数、字符串和 Python 对象。`Series` 的基本结构由两个组件构成：数据 和索引。

### 数据

`Series` 中的数据是一个一维 NumPy 数组，用于存放实际的数据值。数据可以是多种类型，如整数、浮点数或字符串。

### 索引

索引是一种类数组结构，用于标记数据数组中的每个元素。默认情况下，索引是一个从零开始的整数序列，但你也可以为索引提供自定义标签。这使得基于标签引用和操作数据元素变得非常容易。

要创建 `Series`，可以使用 `pd.Series()` 构造函数，并传入列表、字典或 NumPy 数组作为数据。你也可以提供可选的 `index` 参数来为数据元素指定自定义标签。

## DataFrame

`DataFrame` 是一种二维的、大小可变的、异构的表格数据结构，拥有带标签的轴（行和列）。它可以被视为 `Series` 对象的集合，其中每一列都是一个 `Series`。`DataFrame` 旨在处理各种数据类型，使其成为数据操作和分析中通用且强大的工具。

`DataFrame` 的基本结构由三个组件构成：数据、索引 和列。

### 数据

`DataFrame` 中的数据以一个或多个 `Series` 对象的集合形式存储，其中每一列代表一个独立的 `Series`。每个 `Series` 中的数据可以是多种类型，如整数、浮点数或字符串。

### 索引

索引是一种类数组结构，用于标记 `DataFrame` 中的每一行。与 `Series` 索引类似，`DataFrame` 索引可以是一个从零开始的整数序列，也可以拥有自定义标签。

### 列

列是一种类数组结构，用于标记 `DataFrame` 中的每一列。列标签用于引用和操作 `DataFrame` 中的特定列。

要创建 `DataFrame`，可以使用 `pd.DataFrame()` 构造函数，并传入多种数据类型，如字典、字典列表、二维 NumPy 数组，甚至 `Series` 列表。你也可以提供可选的 `index` 和 `columns` 参数来指定自定义的行和列标签。

`Series` 和 `DataFrame` 均提供了广泛的方法和功能用于数据操作和分析。这些功能包括：

*   **数据选择**：你可以使用索引、切片和布尔条件，在 `DataFrame` 或 `Series` 中选择特定的行、列或元素。
*   **数据清洗**：你可以处理缺失数据、删除不需要的行或列，以及替换 `DataFrame` 或 `Series` 中的特定值。
*   **数据转换**：你可以对 `DataFrame` 或 `Series` 中的元素应用函数、创建新列，或重塑数据结构。
*   **数据聚合与汇总**：你可以在 `DataFrame` 或 `Series` 上执行各种聚合函数，如 `sum`、`mean` 或 `count`。你还可以使用 `GroupBy` 功能根据特定标准对数据分组，并对每个组执行聚合操作。
*   **排序与排名**：你可以根据索引或列值对 `DataFrame` 或 `Series` 进行排序，并根据特定标准对数据元素进行排名。
*   **时间序列功能**：你可以处理时间序列数据、按不同频率重采样数据，以及在 `DataFrame` 或 `Series` 上执行滚动窗口计算。

通过理解 `Series` 和 `DataFrame` 的结构与功能，你可以在 Pandas 中高效地操作和分析数据，从而应对各种数据相关任务。

# 加载与修改数据集

要访问并修改所提供 CSV 文件中的数据，请遵循以下分步说明：

## 下载 CSV 文件

首先，从 GitHub 仓库将 `Customer_Churn_Modelling.csv` 文件下载到本地计算机。你可以通过在网页浏览器中访问以下 URL 来实现：

[https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv](https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv)

在页面上右键单击并选择“另存为”，将文件保存到所需位置。

## 加载数据

要从 CSV 文件加载数据，你需要使用 Pandas 中的 `pd.read_csv()` 函数：

```python
import pandas as pd

# 将 'path/to/your/csv' 替换为本地计算机上的实际文件路径
file_path = 'path/to/your/csv/Customer_Churn_Modelling.csv'
data = pd.read_csv(file_path)
```

## 检查数据

在修改数据之前，了解其结构和内容至关重要。你可以使用各种 Pandas 函数来检查 `DataFrame`：

```python
# 显示 DataFrame 的前几行
print(data.head())

# 显示 DataFrame 的形状（行数和列数）
print(data.shape)

# 显示 DataFrame 中每列的数据类型
print(data.dtypes)

# 显示数值列的汇总统计信息
print(data.describe())
```

## 访问与修改数据

现在你已了解数据情况，可以使用各种 Pandas 函数和方法来访问和修改数据。以下是一些示例：

### 选择特定列

```python
# 选择 'Surname' 列
surname = data['Surname']

# 选择多列，如 'CreditScore' 和 'Age'
selected_columns = data[['CreditScore', 'Age']]
```

### 使用切片选择特定行

```python
# 选择 DataFrame 的前 10 行
first_10_rows = data[:10]
```

### 基于条件选择行

```python
# 选择 'Exited' 等于 1 的行（流失客户）
churned_customers = data[data['Exited'] == 1]
```

### 修改数据值

```python
# 通过给每个值加 10 分来更新 'CreditScore' 列
data['CreditScore'] = data['CreditScore'] + 10
```

### 添加新列

```python
# 根据 'CreditScore' 值添加新列 'CreditScore_Categories'
def credit_score_category(score):
    if score < 300:
        return 'Bad'
    elif score < 600:
        return 'Poor'
    elif score < 700:
        return 'Fair'
    elif score < 800:
        return 'Good'
    else:
        return 'Excellent'

data['CreditScore_Categories'] = data['CreditScore'].apply(credit_score_category)
```

### 删除列

```python
# 删除 'RowNumber' 列
data = data.drop('RowNumber', axis=1)
```

### 将修改后的 DataFrame 保存到新的 CSV 文件

```python
# 将修改后的 DataFrame 保存到新的 CSV 文件
data.to_csv('Modified_Customer_Churn_Modelling.csv', index=False)
```

以上仅是使用 Pandas 进行复杂数据操作任务时，如何访问和修改数据的几个示例。

