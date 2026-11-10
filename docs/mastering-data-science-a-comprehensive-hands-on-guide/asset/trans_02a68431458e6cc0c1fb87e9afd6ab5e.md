
# Jupyter Notebook 基础

## 错误处理

当在 Jupyter 中运行 Python 代码时，错误会显示在单元格的输出区域。这有助于你快速识别问题。

错误处理示例：

```
x = 10 / 0  # This will raise a ZeroDivisionError
```

错误输出：

```
ZeroDivisionError: division by zero
```

调试技巧：使用 `print()` 语句检查变量。利用 `%debug` 魔法命令在发生错误时进入交互式调试会话。它允许你在程序失败的点检查程序状态。

`%debug` 示例：运行导致错误的代码。在新单元格中执行 `%debug` 以访问调试器界面。

## 使用魔法命令

Jupyter Notebook 包含魔法命令，它们提供超出标准 Python 的特殊功能。

常用魔法命令：

`%timeit`：测量 Python 代码的执行时间。

```
%timeit sum(range(1000))
```

`%matplotlib inline`：确保 Matplotlib 的绘图在笔记本中内联显示。

```
%matplotlib inline
import matplotlib.pyplot as plt
plt.plot([1, 2, 3], [4, 5, 6])
```

其他有用的魔法命令：

`%run`：执行 Python 脚本。
`%lsmagic`：列出所有可用的魔法命令。
`%store`：存储变量以便在笔记本之间使用。

## 导入库和模块

在 Jupyter Notebook 中，你可以在单元格或笔记本开头轻松导入 Python 库或模块。这对于数据科学任务尤其有帮助，因为像 NumPy、Pandas 和 Matplotlib 这样的库经常被使用。

示例：

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

安装缺失的库：如果需要安装库，可以直接在笔记本单元格中使用 `!` 运算符运行 shell 命令进行安装：

```
!pip install seaborn
```

## Jupyter 中的实用工作流程

- 在单独的单元格中编写小块代码，以便更好地组织和调试。
- 使用 Markdown 单元格记录你的代码和发现。
- 利用魔法命令简化计时和可视化等任务。

# 用于文档的 Markdown

Markdown 是一种轻量级标记语言，用于以结构化的方式格式化文本。在 Jupyter Notebook 中，Markdown 单元格允许你在代码旁边添加文档、注释和解释性文本。这使你的笔记本更易读、更专业且可共享。

## 在 Markdown 单元格中编写文本

Markdown 单元格用于编写纯文本，可以使用简单语法进行格式化。要创建 Markdown 单元格：

- 从工具栏将单元格类型更改为“Markdown”或使用键盘快捷键 `Esc + M`。
- 使用 Markdown 语法编写文本。
- 运行单元格（`Shift + Enter`）以渲染格式化的文本。

## 格式化文本（标题、列表、强调）

标题：标题是通过在文本前添加井号（`#`）创建的。井号的数量对应标题级别：

使用 markdown 单元格。

```
# Heading 1
## Heading 2
### Heading 3
```

列表

- 无序列表：使用 `-` 或 `*` 表示项目符号。
- 有序列表：使用数字后跟句点。

使用 markdown 单元格。

```
- Item 1
- Item 2
1. First item
2. Second item
```

强调

- 斜体：用单星号（`*text*`）或下划线（`_text_`）包裹文本。
- 粗体：用双星号（`**text**`）或双下划线（`__text__`）包裹文本。
- 粗体和斜体：组合两种样式（`***text***`）。

![一台计算机的屏幕截图 AI 生成的内容可能不正确。](image_rsrcF3G.jpg)

## 添加链接、图片和表格

链接：使用以下语法创建可点击的超链接：

`[Link Text](URL)`

示例：

使用 markdown 单元格。

```
[Visit Jupyter](https://jupyter.org)
```

图片：使用类似的语法嵌入图片，但以感叹号开头：

`![Alt Text](Image_URL_or_Path)`

示例：

使用 markdown 单元格。

```
![Jupyter Logo](https://jupyter.org/assets/homepage/main-logo.svg)
```

表格：使用竖线（`|`）和连字符（`-`）创建表格：

使用 markdown 单元格。

```
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data 1   | Data 2   | Data 3   |
| Data 4   | Data 5   | Data 6   |
```

## 使用 LaTeX 插入方程

Jupyter Notebook 支持使用 LaTeX 编写数学方程。使用美元符号（`$`）插入行内方程，双美元符号（`$$`）用于块方程。

行内示例：

使用 markdown 单元格。

```
The formula for a circle's area is $A = \pi r^2$.
```

渲染为：圆面积公式为 A=πr 2

块示例：

使用 markdown 单元格。

```
$$E = mc^2$$
```

渲染为：E=mc2

# 数据探索与可视化

Jupyter Notebook 是执行数据探索和可视化任务的强大工具，为分析数据、生成洞察和创建可视化表示提供了无缝环境。以下是提到的关键主题的讨论：

## 使用 Pandas 加载数据集

Pandas 是一个用于数据操作和分析的多功能 Python 库。你可以从各种格式加载数据集，例如 CSV、Excel、JSON、SQL，甚至直接从 Web API 加载。

示例：加载 CSV 文件

```
import pandas as pd
# Load dataset
data = pd.read_csv("dataset.csv")
# Display the first few rows
print(data.head())
```

![一台计算机的屏幕截图 AI 生成的内容可能不正确。](image_rsrcF3H.jpg)

示例：`dataset.csv`

```
Name,Age,Salary,Department
Alice,25.0,50000,HR
Bob,30.0,60000,Finance
Charlie,35.0,70000,IT
David,40.0,80000,Marketing
Eve,,90000,Finance
```

（如果您正在动手跟随，请将其保存为 `dataset.csv` 在您的 jupyter notebook 位置的目录中）

Pandas 为其他格式提供了类似 `pd.read_excel()`、`pd.read_json()` 和 `pd.read_sql()` 的函数。加载后，数据集表示为 `DataFrame`，易于操作。

## 基础数据分析

Jupyter Notebook 允许使用 Pandas 方法快速探索数据集。一些常用函数包括：

`head()`：显示数据集的前几行。
`info()`：提供数据集的概览，包括数据类型和非空计数。
`describe()`：使用均值、中位数、标准差等统计数据汇总数值列。

示例：基础分析

```
# View first 5 rows
print(data.head())
# Summary of the dataset
print(data.info())
# Statistics for numerical columns
print(data.describe())
```

![一个带白色边框的白色矩形物体 AI 生成的内容可能不正确。](image_rsrcF3J.jpg)

这些方法有助于识别模式、异常值和数据类型，这对进一步分析至关重要。

## 在 Jupyter Notebook 中清理数据

数据清理涉及处理缺失值、删除重复项以及纠正数据集中的错误。

常见数据清理步骤：

处理缺失值：

```
# Fill missing values with a default value
data.fillna(0, inplace=True)
# Drop rows with missing values
data.dropna(inplace=True)
```

删除重复项：

```
data = data.drop_duplicates()
```

更改数据类型：

```
data['column_name'] = data['column_name'].astype('int')
```

Jupyter Notebook 允许迭代清理和测试，使其成为此任务的首选。

## 使用 Matplotlib 和 Seaborn 可视化数据

可视化对于理解数据和识别趋势或模式至关重要。

Matplotlib：一个用于创建静态、动画和交互式可视化的多功能库。
Seaborn：基于 Matplotlib 构建，简化了有吸引力的统计图表的创建。

示例：使用 Matplotlib 进行基础绘图

```
import matplotlib.pyplot as plt
# Create a line plot
plt.plot(data['column_name'])
plt.title("Line Plot")
plt.show()
```

![一台计算机的屏幕截图 AI 生成的内容可能不正确。](image_rsrcF3K.jpg)

示例：使用 Seaborn 进行统计绘图

```
import seaborn as sns
import matplotlib.pyplot as plt
# Create a scatter plot
sns.scatterplot(x='column1', y='column2', data=data)
plt.show()
```

![一台计算机的屏幕截图 AI 生成的内容可能不正确。](image_rsrcF3M.jpg)
