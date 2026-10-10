

# 摘要

在本章中，我们讨论了强大的 Python 库 Pandas 及其在数据操作和分析中的作用。我们首先简要介绍了 Pandas 及其在高效处理复杂数据集方面的重要性。随后，我们讲解了安装和配置 Pandas 的过程，强调了预先安装 Python 和 `pip` 的必要性。我们探讨了 Pandas 的版本历史，从最初的发布版本（`0.1.x`）到最新的主要版本（`2.0`）。我们重点介绍了 Pandas 2.0 的关键改进，例如性能增强、优化的类型系统、新增的 API、更好的互操作性、简化的 API、现代化的代码库、改进的文档、增强的错误消息、结构化的弃用策略以及社区驱动的开发流程。接下来，我们深入探讨了 Pandas 中的主要数据结构：`Series` 和 `DataFrame`。我们详细解释了它们的结构、组成部分及其工作原理。我们强调，`Series` 和 `DataFrame` 均提供了广泛的方法和功能用于数据操作和分析，使其成为数据科学任务的必备工具。最后，我们逐步演示了如何使用 Pandas 访问和修改 CSV 文件中的数据。我们演示了如何下载文件、使用 Pandas 加载文件、检查其结构和内容，以及使用各种函数和方法访问和修改数据。我们还展示了如何将修改后的 `DataFrame` 保存到新的 CSV 文件中。

# 第 2 章：数据读取、存储与文件格式

## 读取 CSV、Excel 和 JSON 数据

Pandas 提供了多个函数用于从多种格式读取数据，使其成为处理不同数据源的多功能工具。Pandas 支持的一些常用数据格式包括 CSV、JSON、Excel（XLS 和 XLSX）、SQL、HTML 等。现在，假设 `Customer_Churn_Modelling` 数据集以 JSON 和 XLS 格式提供。我们将逐步讲解如何从这些格式中读取数据。

### 下载 JSON 和 XLS 格式的文件

首先，你需要拥有 JSON 和 XLS 格式的 `Customer_Churn_Modelling` 数据集。你可以使用在线转换器转换现有的 CSV 文件，或使用 Microsoft Excel 或 LibreOffice Calc 等工具将数据保存为所需格式。

### 使用 Pandas 读取数据

#### 读取 JSON 数据

要从 JSON 文件读取数据，可以使用 Pandas 中的 `pd.read_json()` 函数：

```python
import pandas as pd
# 将 'path/to/your/json' 替换为本地机器上的实际文件路径
json_file_path = 'path/to/your/json/Customer_Churn_Modelling.json'
data_json = pd.read_json(json_file_path)
```

#### 读取 Excel (XLS 或 XLSX) 数据

要从 Excel 文件读取数据，可以使用 Pandas 中的 `pd.read_excel()` 函数。请注意，读取 XLSX 文件需要安装 `openpyxl` 包，读取 XLS 文件需要安装 `xlrd` 包。

```bash
# 使用 pip 安装 openpyxl 和 xlrd
pip install openpyxl xlrd
```

```python
import pandas as pd
# 将 'path/to/your/xls' 替换为本地机器上的实际文件路径
xls_file_path = 'path/to/your/xls/Customer_Churn_Modelling.xls'
data_xls = pd.read_excel(xls_file_path)
```

### 检查数据

加载数据后，你可以检查 DataFrame 以确保数据已正确读取：

```python
# 显示 JSON DataFrame 的前几行
print(data_json.head())
# 显示 Excel DataFrame 的前几行
print(data_xls.head())
```

### 执行数据操作和分析

数据加载完成后，无论原始文件格式如何，你都可以使用前面讨论的相同 Pandas 函数和方法来操作和分析数据。总之，Pandas 提供了一种无缝的方式从各种文件格式读取数据，使用户能够毫不费力地处理不同的数据源。通过使用 `pd.read_json()` 和 `pd.read_excel()` 等适当的函数，你可以将 JSON 和 Excel 文件中的数据加载到 DataFrame 中，并根据需要执行数据操作和分析任务。

## 将数据写入不同格式

Pandas 允许你轻松地将 DataFrame 写入不同的文件格式。在本例中，我们假设你已将 `Customer_Churn_Modelling.csv` 数据集加载到一个名为 `data` 的 DataFrame 中。我们现在将演示如何将数据写入 JSON、Excel (XLSX) 和 HTML 等各种格式。

### 写入 JSON 格式

要将 DataFrame 写入 JSON 文件，可以使用 `to_json()` 方法：

```python
# 将 'path/to/your/output' 替换为本地机器上的实际输出文件路径
json_output_path = 'path/to/your/output/Customer_Churn_Modelling_output.json'
data.to_json(json_output_path)
```

### 写入 Excel (XLSX) 格式

要将 DataFrame 写入 Excel 文件，可以使用 `to_excel()` 方法。请确保已安装 `openpyxl` 包以写入 XLSX 文件。

```bash
# 使用 pip 安装 openpyxl
pip install openpyxl
```

```python
# 将 'path/to/your/output' 替换为本地机器上的实际输出文件路径
xlsx_output_path = 'path/to/your/output/Customer_Churn_Modelling_output.xlsx'
data.to_excel(xlsx_output_path, index=False, engine='openpyxl')
```

### 写入 HTML 格式

要将 DataFrame 写入 HTML 文件，可以使用 `to_html()` 方法：

```python
# 将 'path/to/your/output' 替换为本地机器上的实际输出文件路径
html_output_path = 'path/to/your/output/Customer_Churn_Modelling_output.html'
data.to_html(html_output_path, index=False)
```

这些只是 Pandas 支持的输出格式的几个示例。你还可以将 DataFrame 写入 Parquet、Stata 等其他格式。要写入这些格式，你需要使用相应的方法，如 `to_parquet()`、`to_stata()` 等，并安装必要的包。总之，Pandas 提供了一种简便的方法将 DataFrame 写入各种文件格式，使数据共享和存储变得简单。通过使用 `to_json()`、`to_excel()` 和 `to_html()` 等适当的方法，你可以根据需要将 DataFrame 中的数据保存到不同的格式中。

