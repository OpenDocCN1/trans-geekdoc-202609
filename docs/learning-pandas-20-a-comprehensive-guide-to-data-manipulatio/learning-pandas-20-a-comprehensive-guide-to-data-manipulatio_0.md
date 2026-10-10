## Pandas 2.0 学习指南：面向数据科学家与机器学习专业人士的数据操作与分析综合指南







---















































































































































































































































































































## 前言

《Learning Pandas 2.0》（学习 Pandas 2.0）是任何想要驾驭 Python 首屈一指的数据操作库强大功能的人士的必备指南。借助这本全面的资源，你不仅将掌握 Pandas 2.0 的核心概念，还将学习如何运用其高级特性来执行高效的数据操作和分析。通读全书，你将深入理解 Pandas 2.0 的数据结构、索引和选择技术。获得从各种文件格式和来源加载、存储和清洗数据的专业技能，确保数据的完整性和一致性。随着学习的深入，你将探究高级数据转换、合并和聚合方法，以提取有意义的见解并生成富有洞察力的报告。《Learning Pandas 2.0》还涵盖了专门的数据处理需求，如时间序列数据、DateTime 操作和地理空间分析。此外，本书还演示了如何将 Pandas 2.0 与 Scikit-learn、TensorFlow 和 PyTorch 等机器学习库集成，以进行预测分析。这将使你能够构建强大的数据驱动模型来解决复杂问题并增强决策能力。让《Learning Pandas 2.0》区别于其他书籍的是其专注于大量实用示例，让你能够将新获得的技能应用到棘手的场景中。读完本书后，你将拥有使用 Pandas 2.0 执行高效稳健的数据分析所需的信心和知识，踏上成为数据分析高手的道路。

### 本书将教会你如何：

*   掌握 Pandas 2.0 的核心概念，包括用于高效数据操作的数据结构、索引和选择。
*   从各种文件格式和来源加载、存储和清洗数据，确保数据的完整性和一致性。
*   执行高级数据转换、合并和聚合技术，以进行深入分析和报告。
*   利用时间序列数据、DateTime 操作和地理空间分析满足专门的数据处理需求。
*   使用 Seaborn、Plotly 和高级地理空间可视化工具有效地可视化数据。
*   将 Pandas 2.0 与 Scikit-learn、TensorFlow 和 PyTorch 等机器学习库集成，以进行预测分析。
*   通过真实世界的案例研究获得实战经验，并学习高效稳健数据分析的最佳实践。

## GitforGits

## 先决条件

无论你是经验丰富的数据专业人士，还是刚刚踏上数据科学之旅的新手，《Learning Pandas 2.0》都是帮助你驾驭这个前沿库强大功能的完美资源。本书是 Pandas 2.0 在各种可能的数据操作和分析项目中实际实现的绝佳资源。

## 代码用法

你是否需要一些有用的代码示例来协助你的编程和文档工作？别再找了！我们的书提供了大量的补充材料，包括代码示例和练习。这本书不仅旨在帮助你完成工作，而且我们允许你在你的程序和文档中使用示例代码。但请注意，如果你要复制大量代码，我们确实要求你联系我们以获取许可。但别担心，在你的程序中使用本书中的几段代码，或者通过引用本书并引用示例代码来回答问题，并不需要许可。但如果你确实选择注明出处，署名通常包括书名、作者、出版社和 ISBN。例如，“Learning Pandas 2.0 by Matthew Rosch”。如果你不确定你打算如何使用代码示例是否属于合理使用或上述许可范围，请随时通过 support@gitforgits.com 联系我们。我们很乐意提供协助并澄清任何疑虑。

## 致谢

我要对 GitforGits 表达巨大的感激之情，感谢他们在撰写本书的整个过程中始终如一的热情和明智的建议。他们的知识和细致的编辑有助于确保本书对所有阅读水平和理解能力的人都有用。此外，我要感谢所有参与出版过程的人为使本书成为现实所做的努力。他们的努力，从文案编辑到广告宣传，成就了今天的项目。最后，我想向一生中给予我无条件的爱和鼓励的每一个人表达我的感激之情。他们的支持对完成这本书至关重要。感谢你对这项事业的帮助和对我职业生涯持续的关注。

## 第 1 章：PANDAS 2.0 简介





### 理解 Pandas

Pandas 是一个开源的 Python 库，提供了数据操作、分析和清洗工具，旨在使数据分析变得快速、简单且直观。由于其高性能、用户友好且易于理解的特性，它在数据科学和分析社区中获得了极大的普及。Pandas 代表 “Python Data Analysis Library”（Python 数据分析库），其主要数据结构 `DataFrame` 是仿照 R 编程语言的数据框设计的。Pandas 2.0 是该库的最新版本，与前代相比提供了显著的性能改进和新功能。

数据操作和分析是数据科学中的关键任务，Pandas 擅长提供高效且多功能的工具来执行这些任务。数据操作包括数据清洗、数据转换和数据聚合等任务。另一方面，数据分析包含数据探索、可视化和统计分析等任务。

#### 介绍 Pandas 2.0

Pandas 构建在 `NumPy` 库之上，后者是 Python 科学计算的重要库。这种依赖关系使 Pandas 能够利用 NumPy 数组的强大功能和效率，同时提供针对数据分析量身定制的附加功能。Pandas 提供的两个主要数据结构是 `Series` 和 `DataFrame`，两者均构建在 NumPy 数组之上。

`Series` 是一种一维的带标签数组，能够容纳任何数据类型。它类似于 Python 列表或 NumPy 数组，但拥有一个为每个元素提供标签的索引。该索引可以是基于整数的（如默认的 Python 列表），也可以是用户定义的自定义标签。

另一方面，`DataFrame` 是一种二维的、大小可变的、异构的表格数据结构，具有带标签的轴（行和列）。它本质上是 `Series` 对象的集合，其中每一列都是一个 `Series`。DataFrame 旨在处理各种数据类型，包括数值、分类和文本数据，使其成为数据操作和分析中极其多功能的工具。

#### 为什么选择 Pandas 进行数据操作与分析？

Pandas 提供了许多功能，使其成为数据操作和分析的必备库：

- **数据摄入**：Pandas 可以从各种文件格式（如 CSV、Excel、JSON 和 SQL 数据库）读取数据，使得从各种来源加载和解析数据变得容易。
- **数据清洗**：Pandas 提供了处理缺失数据的工具，例如使用默认值填充缺失值，或根据周围数据插值。它还允许用户筛选、重命名和删除列或行，使数据清洗和预处理变得简单。
- **数据转换**：Pandas 提供了强大的工具来重塑和透视 DataFrame，使数据易于转换为所需格式。它还提供了连接、合并和联接 DataFrame 的功能，允许用户组合和重构数据集。
- **数据聚合与汇总**：Pandas 支持多种聚合函数，如求和、平均值、中位数和标准差，以及自定义聚合函数。`GroupBy` 功能允许用户根据一列或多列对特定数据子集执行这些聚合操作。
- **时间序列功能**：Pandas 提供了处理时间序列数据的综合工具，包括重采样、滚动窗口以及按时间向前或向后移动数据。这使其特别适用于分析时间相关数据，如金融或传感器数据。
- **数据探索**：Pandas 提供了便捷的方法来筛选、排序和选择特定的数据子集。这使得探索和理解数据集变得容易。
- **数据可视化**：Pandas 与流行的数据可视化库（如 `Matplotlib`、`Seaborn` 和 `Plotly`）无缝集成，使用户能够创建各种可视化图表以更好地理解其数据。
- **性能**：Pandas 专为高性能设计，能高效处理大型数据集。它利用向量化操作和 Cython 优化函数提供快速的计算时间，即使对于复杂的数据操作任务也是如此。该库还支持并行和核外计算，使其适合大规模数据处理。
- **兼容性**：Pandas 与广泛的其他 Python 库和工具兼容，如 `scikit-learn`、`TensorFlow` 和 `PySpark`，能够无缝集成到数据科学工作流中。这使其成为构建端到端数据处理管道的绝佳选择。
- **社区与文档**：Pandas 拥有庞大且活跃的社区，为其开发和维护做出贡献。这确保了该库紧跟数据分析技术的最新进展。此外，Pandas 拥有详尽的文档和大量教程，使新手能够轻松学习和理解其功能。

总而言之，Pandas 是一个强大且多功能的 Python 库，在数据操作和分析中发挥着重要作用。其高效且用户友好的工具使其成为数据科学家和分析师的首选。通过提供无缝的数据摄入、清洗、转换、聚合、汇总、探索和可视化能力，Pandas 使整个数据分析过程更快、更简单、更直观。此外，其高性能特性、与其他 Python 库的兼容性以及活跃的社区支持，使 Pandas 成为任何希望利用 Python 力量进行数据分析任务的数据科学家或分析师的必备工具。





### 安装和配置 Pandas 2.0

要在您的 Python 环境中安装 Pandas 2.0 并对其进行配置，请遵循以下分步说明。请注意，这些步骤假设您的系统上已经安装了 Python。

#### 安装 pip

Pip 是 Python 的包安装程序。它用于安装和管理 Python 包，包括 Pandas。如果您尚未安装 pip，请遵循以下说明：

##### Windows 和 macOS

1. 从 [`bootstrap.pypa.io/get-pip.py`](https://bootstrap.pypa.io/get-pip.py) 下载 `get-pip.py` 文件
2. 打开终端（Windows 上的命令提示符或 macOS 上的终端）并导航到您下载文件的目录。
3. 运行以下命令：

```
python get-pip.py
```

##### Linux

打开终端并运行以下命令：

```
sudo apt-get install python3-pip
```

#### 创建虚拟环境

创建虚拟环境允许您为每个项目单独管理依赖项。这可以防止不同包及其依赖项之间的冲突。

1. 打开终端（Windows 上的命令提示符或 macOS/Linux 上的终端）。
2. 导航到您的项目目录或您想要创建虚拟环境的目录。
3. 运行以下命令以创建一个名为 "env" 的新虚拟环境：

```
python -m venv env
```

#### 激活虚拟环境

##### Windows 上：

```
env\Scripts\activate
```

##### macOS/Linux 上：

```
source env/bin/activate
```

#### 安装 Pandas 2.0

激活虚拟环境后，您现在可以使用 pip 安装 Pandas 2.0：

在终端中运行以下命令：

```
pip install pandas==2.0
```

#### 验证安装

要验证 Pandas 2.0 是否已成功安装，请执行以下步骤：

1. 在终端中运行 `python` 命令启动 Python 解释器。
2. 使用以下命令导入 Pandas：

```
import pandas as pd
```

3. 通过运行以下命令检查 Pandas 版本：

```
print(pd.__version__)
```

如果输出显示 "2.0"，则安装成功。

#### 配置 Pandas

Pandas 对大多数用例都有合理的默认设置。但是，您可能希望配置特定选项以满足您的需求。要配置 Pandas 选项，可以使用 `pd.set_option()` 函数。

以下是设置打印 DataFrame 时显示的最大行数的示例：

1. 在终端中运行 `python` 命令启动 Python 解释器。
2. 使用以下命令导入 Pandas：

```
import pandas as pd
```

3. 设置所需的选项，例如：

```
pd.set_option("display.max_rows", 500)
```

您可以在 Pandas 文档中找到更多选项：[`pandas.pydata.org/pandas-docs/stable/user_guide/options.html`](https://pandas.pydata.org/pandas-docs/stable/user_guide/options.html)

现在 Pandas 2.0 已安装并配置完毕，您可以开始在 Python 项目中使用它进行数据操作和分析。请记住，在 Python 脚本开头使用 `import pandas as pd` 导入 Pandas。





### Pandas 版本历史

Pandas 拥有丰富的开发历史，多年来发布了众多版本。每个版本都引入了新特性、性能改进和错误修复。以下是截至 1.3.x 版本的 Pandas 主要版本历史简述，随后是 Pandas 2.0 的详细介绍。

#### Pandas 0.1.x（2011 年 1 月）

Pandas 的初始版本为 `DataFrame` 和 `Series` 数据结构奠定了基础，同时提供了基本的 I/O 操作、时间序列功能和基础数据处理能力。

#### Pandas 0.2.x 至 0.9.x（2011-2012 年）

这些版本引入了许多新特性，例如 `MultiIndex`、透视表，以及对 Excel 和 HDF5 等多种文件格式的额外 I/O 支持。该库在性能、API 稳定性和文档方面进行了大幅改进。

#### Pandas 0.10.x 至 0.23.x（2013-2018 年）

在此期间，Pandas 持续扩展新功能，包括对分类数据的支持、窗口函数，以及对缺失数据的增强支持。现有 API 经历了持续的性能优化和改进。

#### Pandas 0.24.x 至 1.0.x（2019-2020 年）

这一阶段增加了扩展数组接口、可空整数和布尔数据类型，并改进了对自定义数据类型的支持。Pandas 1.0 在 API 稳定性和成熟度方面标志着一个重要里程碑，弃用了旧有和不常用的特性，同时优化了库的核心功能。

#### Pandas 1.1.x 至 1.3.x（2020-2021 年）

这些版本带来了更多性能改进、额外的 I/O 选项、新的字符串数据类型，以及与 `Dask` 和 `CuPy` 等其他 Python 库的改进兼容性。库的文档和测试基础设施也得到了显著增强。

#### Pandas 2.0（2023 年）

作为一个主要版本，Pandas 2.0 给库带来了重大变革，重点在于提升性能、解决长期存在的问题，并为现代数据分析需求提供更好的支持。Pandas 2.0 的一些关键特性和改进包括：

##### 性能改进

Pandas 2.0 具有显著的性能提升，特别是在处理大型数据集时。该库利用数组计算的进步、现代硬件能力和并行处理，提供更快、更高效的数据操作和分析运算。

##### 增强的类型系统

Pandas 2.0 中的类型系统经过优化，为可空数据类型、用户定义数据类型和扩展数组提供了更好的支持。这使用户能够处理更广泛的数据类型，并定制 Pandas 以更好地满足其特定需求。

##### 新 API 和功能

Pandas 2.0 引入了多个新 API 和特性，使数据操作和分析更加容易。这包括用于处理层级数据的新方法、高级窗口函数，以及对地理空间和时间序列数据处理的改进支持。

##### 改进的互操作性

Pandas 2.0 旨在提供与其他 Python 库和工具更好的互操作性，使 Pandas 更易于集成到数据科学和分析工作流中。这包括与 `Dask` 等库的增强兼容性（用于并行和分布式计算），以及与 `Matplotlib`、`Seaborn` 和 `Plotly` 等可视化库的更好集成。

##### 简化且更一致的 API

随着 Pandas 2.0 的发布，库的 API 已被简化并变得更加一致。这使得用户更容易学习和使用 Pandas，并减少了遇到意外行为的可能性。

##### 现代化的代码库

Pandas 2.0 的代码库已现代化并重构，以提高可维护性、可读性和可扩展性。这包括移除已弃用的特性和代码、采用现代 Python 语言特性，以及拥抱软件开发的最佳实践。因此，Pandas 2.0 更加健壮，也更易于开发者社区贡献代码。

##### 增强的文档和教程

Pandas 2.0 的文档和学习资源得到了扩展和改进，使用户更容易学习和理解库的特性与能力。更新后的文档包含更多示例、更清晰的解释，以及更直观的内容组织。

##### 改进的错误消息和调试

Pandas 2.0 提供了更具信息量的错误消息和更好的调试支持，帮助用户快速识别和解决代码中的问题。这包括更具描述性的错误消息、更好的回溯信息，以及对 `pdb` 等调试器的改进支持。

##### 新的弃用策略

随着 Pandas 2.0 的发布，该库采用了更结构化的弃用策略，为用户提供了清晰的未来变更路线图和更可预测的升级流程。这包括对即将发生变更的更透明沟通、更渐进的弃用过程，以及承诺在特定时期内保持向后兼容性。

##### 社区驱动的开发

Pandas 2.0 的开发是一项协作工作，汇集了更广泛的 Pandas 社区的意见和贡献。这带来了更多样化的特性和改进，满足了更广泛用户和用例的需求。

Pandas 2.0 代表了该库的重大演进，它在巩固优势的同时，解决了长期存在的局限性和挑战。其结果是一个更强大、灵活且用户友好的 Python 数据操作和分析工具。凭借改进的性能、增强的类型系统、新 API、更好的互操作性和现代化的代码库，Pandas 2.0 非常适合应对当今数据驱动世界中日益复杂的数据分析需求。





### Pandas 数据结构

Pandas 为数据操作和分析提供了两种主要数据结构：`Series` 和 `DataFrame`。这两种数据结构均构建在 NumPy 数组之上，从而实现高效且高性能的操作。以下是 `Series` 和 `DataFrame` 及其工作原理的详细解释。

#### Series

`Series` 是一种一维的、带标签的数组，能够容纳任何数据类型，包括整数、浮点数、字符串和 Python 对象。`Series` 的基本结构由两个组件构成：数据 和索引。

##### 数据

`Series` 中的数据是一个一维 NumPy 数组，用于存放实际的数据值。数据可以是多种类型，如整数、浮点数或字符串。

##### 索引

索引是一种类数组结构，用于标记数据数组中的每个元素。默认情况下，索引是一个从零开始的整数序列，但你也可以为索引提供自定义标签。这使得基于标签引用和操作数据元素变得非常容易。

要创建 `Series`，可以使用 `pd.Series()` 构造函数，并传入列表、字典或 NumPy 数组作为数据。你也可以提供可选的 `index` 参数来为数据元素指定自定义标签。

#### DataFrame

`DataFrame` 是一种二维的、大小可变的、异构的表格数据结构，拥有带标签的轴（行和列）。它可以被视为 `Series` 对象的集合，其中每一列都是一个 `Series`。`DataFrame` 旨在处理各种数据类型，使其成为数据操作和分析中通用且强大的工具。

`DataFrame` 的基本结构由三个组件构成：数据、索引 和列。

##### 数据

`DataFrame` 中的数据以一个或多个 `Series` 对象的集合形式存储，其中每一列代表一个独立的 `Series`。每个 `Series` 中的数据可以是多种类型，如整数、浮点数或字符串。

##### 索引

索引是一种类数组结构，用于标记 `DataFrame` 中的每一行。与 `Series` 索引类似，`DataFrame` 索引可以是一个从零开始的整数序列，也可以拥有自定义标签。

##### 列

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

### 加载与修改数据集

要访问并修改所提供 CSV 文件中的数据，请遵循以下分步说明：

#### 下载 CSV 文件

首先，从 GitHub 仓库将 `Customer_Churn_Modelling.csv` 文件下载到本地计算机。你可以通过在网页浏览器中访问以下 URL 来实现：

[`raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv`](https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv)

在页面上右键单击并选择“另存为”，将文件保存到所需位置。

#### 加载数据

要从 CSV 文件加载数据，你需要使用 Pandas 中的 `pd.read_csv()` 函数：

```python
import pandas as pd

# 将 'path/to/your/csv' 替换为本地计算机上的实际文件路径
file_path = 'path/to/your/csv/Customer_Churn_Modelling.csv'
data = pd.read_csv(file_path)
```

#### 检查数据

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

#### 访问与修改数据

现在你已了解数据情况，可以使用各种 Pandas 函数和方法来访问和修改数据。以下是一些示例：

##### 选择特定列

```python
# 选择 'Surname' 列
surname = data['Surname']

# 选择多列，如 'CreditScore' 和 'Age'
selected_columns = data[['CreditScore', 'Age']]
```

##### 使用切片选择特定行

```python
# 选择 DataFrame 的前 10 行
first_10_rows = data[:10]
```

##### 基于条件选择行

```python
# 选择 'Exited' 等于 1 的行（流失客户）
churned_customers = data[data['Exited'] == 1]
```

##### 修改数据值

```python
# 通过给每个值加 10 分来更新 'CreditScore' 列
data['CreditScore'] = data['CreditScore'] + 10
```

##### 添加新列

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

##### 删除列

```python
# 删除 'RowNumber' 列
data = data.drop('RowNumber', axis=1)
```

##### 将修改后的 DataFrame 保存到新的 CSV 文件

```python
##### 将修改后的 DataFrame 保存到新的 CSV 文件
data.to_csv('Modified_Customer_Churn_Modelling.csv', index=False)
```

以上仅是使用 Pandas 进行复杂数据操作任务时，如何访问和修改数据的几个示例。





### 摘要

在本章中，我们讨论了强大的 Python 库 Pandas 及其在数据操作和分析中的作用。我们首先简要介绍了 Pandas 及其在高效处理复杂数据集方面的重要性。随后，我们讲解了安装和配置 Pandas 的过程，强调了预先安装 Python 和 `pip` 的必要性。我们探讨了 Pandas 的版本历史，从最初的发布版本（`0.1.x`）到最新的主要版本（`2.0`）。我们重点介绍了 Pandas 2.0 的关键改进，例如性能增强、优化的类型系统、新增的 API、更好的互操作性、简化的 API、现代化的代码库、改进的文档、增强的错误消息、结构化的弃用策略以及社区驱动的开发流程。接下来，我们深入探讨了 Pandas 中的主要数据结构：`Series` 和 `DataFrame`。我们详细解释了它们的结构、组成部分及其工作原理。我们强调，`Series` 和 `DataFrame` 均提供了广泛的方法和功能用于数据操作和分析，使其成为数据科学任务的必备工具。最后，我们逐步演示了如何使用 Pandas 访问和修改 CSV 文件中的数据。我们演示了如何下载文件、使用 Pandas 加载文件、检查其结构和内容，以及使用各种函数和方法访问和修改数据。我们还展示了如何将修改后的 `DataFrame` 保存到新的 CSV 文件中。

## 第 2 章：数据读取、存储与文件格式

### 读取 CSV、Excel 和 JSON 数据

Pandas 提供了多个函数用于从多种格式读取数据，使其成为处理不同数据源的多功能工具。Pandas 支持的一些常用数据格式包括 CSV、JSON、Excel（XLS 和 XLSX）、SQL、HTML 等。现在，假设 `Customer_Churn_Modelling` 数据集以 JSON 和 XLS 格式提供。我们将逐步讲解如何从这些格式中读取数据。

#### 下载 JSON 和 XLS 格式的文件

首先，你需要拥有 JSON 和 XLS 格式的 `Customer_Churn_Modelling` 数据集。你可以使用在线转换器转换现有的 CSV 文件，或使用 Microsoft Excel 或 LibreOffice Calc 等工具将数据保存为所需格式。

#### 使用 Pandas 读取数据

##### 读取 JSON 数据

要从 JSON 文件读取数据，可以使用 Pandas 中的 `pd.read_json()` 函数：

```python
import pandas as pd
# 将 'path/to/your/json' 替换为本地机器上的实际文件路径
json_file_path = 'path/to/your/json/Customer_Churn_Modelling.json'
data_json = pd.read_json(json_file_path)
```

##### 读取 Excel (XLS 或 XLSX) 数据

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

#### 检查数据

加载数据后，你可以检查 DataFrame 以确保数据已正确读取：

```python
# 显示 JSON DataFrame 的前几行
print(data_json.head())
# 显示 Excel DataFrame 的前几行
print(data_xls.head())
```

#### 执行数据操作和分析

数据加载完成后，无论原始文件格式如何，你都可以使用前面讨论的相同 Pandas 函数和方法来操作和分析数据。总之，Pandas 提供了一种无缝的方式从各种文件格式读取数据，使用户能够毫不费力地处理不同的数据源。通过使用 `pd.read_json()` 和 `pd.read_excel()` 等适当的函数，你可以将 JSON 和 Excel 文件中的数据加载到 DataFrame 中，并根据需要执行数据操作和分析任务。

### 将数据写入不同格式

Pandas 允许你轻松地将 DataFrame 写入不同的文件格式。在本例中，我们假设你已将 `Customer_Churn_Modelling.csv` 数据集加载到一个名为 `data` 的 DataFrame 中。我们现在将演示如何将数据写入 JSON、Excel (XLSX) 和 HTML 等各种格式。

#### 写入 JSON 格式

要将 DataFrame 写入 JSON 文件，可以使用 `to_json()` 方法：

```python
# 将 'path/to/your/output' 替换为本地机器上的实际输出文件路径
json_output_path = 'path/to/your/output/Customer_Churn_Modelling_output.json'
data.to_json(json_output_path)
```

#### 写入 Excel (XLSX) 格式

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

#### 写入 HTML 格式

要将 DataFrame 写入 HTML 文件，可以使用 `to_html()` 方法：

```python
# 将 'path/to/your/output' 替换为本地机器上的实际输出文件路径
html_output_path = 'path/to/your/output/Customer_Churn_Modelling_output.html'
data.to_html(html_output_path, index=False)
```

这些只是 Pandas 支持的输出格式的几个示例。你还可以将 DataFrame 写入 Parquet、Stata 等其他格式。要写入这些格式，你需要使用相应的方法，如 `to_parquet()`、`to_stata()` 等，并安装必要的包。总之，Pandas 提供了一种简便的方法将 DataFrame 写入各种文件格式，使数据共享和存储变得简单。通过使用 `to_json()`、`to_excel()` 和 `to_html()` 等适当的方法，你可以根据需要将 DataFrame 中的数据保存到不同的格式中。





### 使用 Pandas 2.0 进行数据库交互

数据库交互是指使用编程语言或软件工具连接、查询和管理存储在数据库管理系统 (DBMS) 中数据的过程。Pandas 结合其他库，可以与各种数据库进行交互，例如 SQL 数据库（如 SQLite、MySQL、PostgreSQL）和 NoSQL 数据库（如 MongoDB），以读取和写入数据。在本示例中，我们将演示如何使用 Pandas 2.0 与 SQLite 数据库进行交互。SQLite 是一种轻量级、无服务器、自包含的 SQL 数据库引擎，易于设置，且无需单独的服务器进程。

#### 安装 sqlite3 包

首先，您需要安装 `sqlite3` 包，它是 Python 标准库的一部分，通常已经预装。

```
!pip install pysqlite3
```

此代码将使用 `pip` 安装 `sqlite3` 包及其依赖项。

#### 设置 SQLite 数据库

为了演示，我们将创建一个新的 SQLite 数据库和一张表，用于存储 `Customer_Churn_Modelling` 数据。

```
import sqlite3

# 连接到 SQLite 数据库（如果不存在，将创建一个名为 'churn.db' 的新文件）
conn = sqlite3.connect('churn.db')

# 创建一个游标对象以执行 SQL 命令
cursor = conn.cursor()

# 创建 'customer_churn' 表
create_table_query = '''
CREATE TABLE IF NOT EXISTS customer_churn (
    RowNumber INTEGER PRIMARY KEY,
    CustomerId INTEGER,
    Surname TEXT,
    CreditScore INTEGER,
    Geography TEXT,
    Gender TEXT,
    Age INTEGER,
    Tenure INTEGER,
    Balance REAL,
    NumOfProducts INTEGER,
    HasCrCard INTEGER,
    IsActiveMember INTEGER,
    EstimatedSalary REAL,
    Exited INTEGER
);
'''

cursor.execute(create_table_query)

# 提交更改并关闭游标
conn.commit()
cursor.close()
```

#### 将数据加载到 SQLite 数据库

现在，我们将 `Customer_Churn_Modelling` 数据（假设存储在名为 `data` 的 DataFrame 中）插入到 `customer_churn` 表中。

```
# 将 DataFrame 中的数据插入到 SQLite 表中
data.to_sql('customer_churn', conn, if_exists='replace', index=False)
```

#### 使用 Pandas 查询 SQLite 数据库

您可以使用 Pandas 在数据库上执行 SQL 查询，并将结果存储在 DataFrame 中。

```
# 定义 SQL 查询
sql_query = 'SELECT * FROM customer_churn WHERE Exited = 1'

# 执行查询并将结果存储在 DataFrame 中
churned_customers = pd.read_sql_query(sql_query, conn)
```

#### 执行数据操作与分析

数据加载到 DataFrame 后，您可以使用前文讨论的相同 Pandas 函数和方法来操作和分析数据。

#### 将数据写回 SQLite 数据库（可选）

如果您想将修改后的数据写回 SQLite 数据库，可以再次使用 `to_sql()` 方法。

```
# 假设 'modified_data' 是一个包含修改后数据的 DataFrame
modified_data.to_sql('customer_churn', conn, if_exists='replace', index=False)
```

#### 关闭连接

最后，关闭与 SQLite 数据库的连接。

```
conn.close()
```

总之，Pandas 允许您通过连接数据库、查询数据以及管理数据库中的数据来与数据库进行交互。通过使用其他库（如本例中的 `sqlite3`），您可以执行数据库交互任务，并使用 Pandas 从数据库读取和写入数据。这种集成使 Pandas 成为涉及数据库的数据操作和分析的强大工具。

### 连接 Web API

通过 Pandas 利用 Web API 可以获取最新信息，并将其无缝集成到 DataFrame 中，以便进行后续评估和操作。这种与 API 的集成简化了实时访问和处理数据的流程，为分析提供了更高效的方法。在本示例中，我们将演示如何使用 `requests` 库连接到公共 API 并将数据加载到 Pandas DataFrame 中。

#### 安装 HTTP 请求包

首先，您需要安装用于发送 HTTP 请求的 `requests` 包：

```
pip install requests
```

#### 发起 API 请求并检索数据

在本示例中，我们将使用 JSONPlaceholder 提供的公共 API，它以 JSON 格式返回一组虚拟帖子列表。

```
import requests

# 定义 API 端点
api_url = 'https://jsonplaceholder.typicode.com/posts'

# 向 API 发送 HTTP GET 请求
response = requests.get(api_url)

# 检查请求是否成功
if response.status_code == 200:
    # 解析 JSON 数据
    json_data = response.json()
else:
    print(f'Error: Unable to fetch data from the API (status code: {response.status_code})')
```

#### 将 JSON 数据加载到 Pandas DataFrame

获取 JSON 数据后，您可以使用 `pd.DataFrame()` 构造函数或 `pd.read_json()` 函数将其加载到 DataFrame 中。

```
import pandas as pd

# 将 JSON 数据加载到 DataFrame 中
data = pd.DataFrame(json_data)

# 或者，您可以使用 'pd.read_json()' 函数
# data = pd.read_json(api_url)
```

#### 执行数据操作与分析

现在数据已加载到 DataFrame 中，您可以使用前文讨论的相同 Pandas 函数和方法来操作和分析数据。

请记住，连接不同 API 的过程可能因特定 API 和所需的身份验证方法而异。您可能需要提供 API 密钥、令牌或使用 OAuth 进行身份验证。请务必查阅 API 文档，了解如何连接和检索数据的详细说明。

总之，您可以使用 `requests` 等库连接到 Web API 并检索实时数据，将数据加载到 Pandas DataFrame 中以进行操作和分析。这一功能使 Pandas 成为处理动态数据源和实时应用的强大工具。





### 数据抓取

从网站提取结构化数据是通过称为数据抓取的过程实现的。这涉及解析网站的 HTML 内容以收集信息。`Beautiful Soup` 是一个 Python 库，是网页抓取常用的工具。凭借其简单且用户友好的语法，它允许用户快速轻松地浏览和解析 HTML 和 XML 文档。`Beautiful Soup` 可用于从网站提取各种类型的数据，如文本、链接和图像。它还支持多种解析器，使其兼容不同的标记语言。在本示例中，我们将演示如何使用 `Beautiful Soup` 从网站抓取数据并将其加载到 Pandas `DataFrame` 中。

#### 安装 Beautiful Soup 包

首先，您需要安装 `Beautiful Soup` 和 `requests` 库：

```
pip install beautifulsoup4 requests
```

#### 从网站获取 HTML 内容

在本示例中，我们将从以下 URL 可用的简单 HTML 表格中抓取数据：<https://www.worldcoinindex.com/>

```
import requests

# 定义 URL
url = 'https://www.worldcoinindex.com/'

# 获取 HTML 内容
response = requests.get(url)

# 检查请求是否成功
if response.status_code == 200:
    html_content = response.text
else:
    print(f'Error: Unable to fetch data from the website (status code: {response.status_code})')
```

#### 使用 Beautiful Soup 解析 HTML 内容

接下来，我们将使用 `Beautiful Soup` 解析 HTML 内容以提取所需数据。

```
from bs4 import BeautifulSoup

# 解析 HTML 内容
soup = BeautifulSoup(html_content, 'html.parser')

# 查找包含我们要抓取数据的表格
table = soup.find('table', {'class': 'table'})
```

#### 从 HTML 表格中提取数据

现在，我们将从 HTML 表格中提取数据，包括表头和行数据。

```
# 提取表头
headers = [header.text for header in table.findAll('th')]

# 提取行
rows = []
for row in table.tbody.findAll('tr'):
    rows.append([col.text for col in row.findAll('td')])
```

#### 将数据加载到 Pandas DataFrame 中

一旦我们有了表头和行，就可以将数据加载到 `DataFrame` 中。

```
import pandas as pd

# 使用提取的表头和行创建 DataFrame
data = pd.DataFrame(rows, columns=headers)
```

#### 执行数据操作和分析

现在数据已加载到 `DataFrame` 中，您可以使用前面讨论的相同 Pandas 函数和方法来操作和分析数据。总之，您可以使用 `Beautiful Soup` 和 `Requests` 等库执行网页抓取，从网站提取结构化数据。一旦获得数据，您可以将其加载到 Pandas `DataFrame` 中以进行进一步处理和分析。这种能力使 Pandas 成为处理来自各种来源（包括动态网页内容）数据的强大工具。

#### 处理缺失数据

在数据清洗过程中，解决任何缺失数据至关重要。Pandas 提供了一系列技术来识别、评估和管理缺失数据。这些方法可以通过填补缺失值或删除不完整记录，帮助确保数据分析的准确性和可靠性。在本示例中，我们将假设您已经将 `Customer_Churn_Modelling.csv` 数据集加载到一个名为 `data` 的 `DataFrame` 中。

#### 识别缺失数据

首先，使用 `isna()` 或 `isnull()` 方法检测 `DataFrame` 中的缺失值。`isna()` 方法返回一个形状相同的 `DataFrame`，缺失值为 `True`，非缺失值为 `False`。

```
missing_values = data.isna()
```

您可以使用 `sum()` 方法计算每列的缺失值数量：

```
missing_value_counts = data.isna().sum()
print(missing_value_counts)
```

#### 处理缺失数据

在 `DataFrame` 中处理缺失数据有多种方法，例如删除或填充缺失值。选择取决于数据的性质和具体用例。

##### 删除缺失值

`dropna()` 方法从 `DataFrame` 中删除包含缺失值的行或列。默认情况下，它会删除至少包含一个缺失值的任何行：

```
data_cleaned = data.dropna()
```

要删除包含缺失值的列而不是行，请将 `axis` 参数设置为 `1`：

```
data_cleaned = data.dropna(axis=1)
```

##### 填充缺失值

`fillna()` 方法使用指定值或指定方法（如前向填充或后向填充）填充缺失值。

用常量值填充缺失值（例如 `0`）：

```
data_filled = data.fillna(0)
```

用各列的平均值填充缺失值：

```
data_filled = data.fillna(data.mean())
```

使用前向填充填充缺失值（将最后一个有效观测值向前传播）：

```
data_filled = data.fillna(method='ffill')
```

使用后向填充填充缺失值（将下一个有效观测值向后传播）：

```
data_filled = data.fillna(method='bfill')
```

#### 验证更改

处理缺失数据后，您可以再次使用 `isna().sum()` 方法确认 `DataFrame` 中不再有缺失值：

```
missing_value_counts_cleaned = data_cleaned.isna().sum()
print(missing_value_counts_cleaned)
```

总之，Pandas 提供了多种方法来处理 `DataFrame` 中的缺失数据。通过使用 `dropna()` 和 `fillna()` 等方法，您可以根据具体要求和数据性质高效地处理缺失值。





### 数据转换与清洗

有效的数据预处理涉及数据转换和清洗这两个关键阶段。这些过程确保收集到的数据经过适当组织、保持一致且可靠，从而带来更好的分析和决策。进行这些初始步骤至关重要，因为它们会显著影响最终输出的准确性和质量。不完整或错误的数据可能导致错误的结论，并对结果产生负面影响。

在本示例中，我们将使用 `Customer_Churn_Modelling.csv` 数据集，假设它已加载到一个名为 `data` 的 DataFrame 中。

#### 识别并处理缺失数据

请参阅前一节关于如何使用 Pandas 处理缺失数据的内容。根据您的具体需求，应用 `dropna()` 或 `fillna()` 方法。

#### 重命名列（可选）

如果您想为了更好的可读性或一致性而重命名列，可以使用 `rename()` 方法：

```
data = data.rename(columns={
    'NumOfProducts': 'Number_of_Products',
    'HasCrCard': 'Has_Credit_Card',
    'IsActiveMember': 'Is_Active_Member',
    'EstimatedSalary': 'Estimated_Salary'
})
```

#### 转换数据类型

确保每列的数据类型适合进一步分析。您可以使用 `dtypes` 属性检查数据类型：

```
print(data.dtypes)
```

如果您需要更改某列的数据类型，可以使用 `astype()` 方法：

```
data['Has_Credit_Card'] = data['Has_Credit_Card'].astype('bool')
data['Is_Active_Member'] = data['Is_Active_Member'].astype('bool')
```

#### 移除重复项

使用 `duplicated()` 和 `drop_duplicates()` 方法检查并移除数据集中的任何重复行：

```
duplicates = data.duplicated()
print(f'Number of duplicate rows: {duplicates.sum()}')
data = data.drop_duplicates()
```

#### 归一化数值列

归一化和标准化有助于将数值特征缩放到一个通用的范围或分布，这对某些机器学习算法很有用。

要归一化某列（将值缩放到 0 和 1 之间）：

```
data['CreditScore'] = (data['CreditScore'] - data['CreditScore'].min()) / (data['CreditScore'].max() - data['CreditScore'].min())
```

要标准化某列（将值缩放为均值为 0、标准差为 1）：

```
data['Age'] = (data['Age'] - data['Age'].mean()) / data['Age'].std()
```

##### 编码分类变量

如果您打算将数据用于机器学习，可能需要将分类变量编码为数值。您可以使用独热编码或标签编码等技术。

对于独热编码，使用 `get_dummies()` 函数：

```
data = pd.get_dummies(data, columns=['Geography', 'Gender'])
```

对于标签编码，您可以使用 scikit-learn 中的 `LabelEncoder` 类：

```
from sklearn.preprocessing import LabelEncoder
encoder = LabelEncoder()
data['Surname'] = encoder.fit_transform(data['Surname'])
```

#### 重排或删除列

根据需要重排或删除列，以便更好地组织数据或移除不必要的特征：

```
##### 重排列
data = data[['RowNumber', 'CustomerId', 'Surname', 'CreditScore', 'Age', 'Tenure', 'Balance', 'Number_of_Products', 'Has_Credit_Card', 'Is_Active_Member', 'Estimated_Salary', 'Geography_France', 'Geography_Germany', 'Geography_Spain', 'Gender_Female', 'Gender_Male', 'Exited']]

##### 删除不必要的列（例如 'RowNumber'、'CustomerId'、'Surname' 可能与您的分析无关）
data = data.drop(columns=['RowNumber', 'CustomerId', 'Surname'])
```

#### 验证更改

执行数据转换和清洗后，通过检查数据来验证更改至关重要：

```
print(data.head())
print(data.dtypes)
print(data.describe())
```

总之，您可以使用 Pandas 提供的各种方法来执行数据转换和清洗任务，例如处理缺失值、重命名列、转换数据类型、移除重复项、归一化或标准化数值列、编码分类变量，以及重排或删除列。这些步骤有助于确保数据准确、一致且结构良好，以便进行进一步分析或机器学习应用。

### 总结

我们讨论了使用 Pandas 从不同文件格式读取数据。Pandas 可以读取多种格式，如 CSV、JSON、Excel、SQL 数据库等。我们演示了如何使用 `pd.read_json()` 和 `pd.read_excel()` 函数从 `Customer_Churn_Modelling.csv` 数据集以 JSON 和 Excel (XLS) 格式读取数据。

接下来，我们介绍了将数据写入不同格式。Pandas 可以将 DataFrame 写入各种文件格式，包括 CSV、JSON、Excel 等。我们演示了如何使用 `to_json()` 和 `to_excel()` 方法将包含 `Customer_Churn_Modelling.csv` 数据集的 DataFrame 写入 JSON 和 Excel 文件。

随后，我们讨论了 Pandas 与数据库的交互。Pandas 允许您使用 `pd.read_sql()` 和 `to_sql()` 函数执行数据库操作。我们演示了如何连接到 SQLite 数据库，使用 `pd.read_sql()` 从表中读取数据到 DataFrame，以及使用 `to_sql()` 方法将数据从 DataFrame 写入表中。

然后，我们探讨了将 Web API 连接到 Pandas。通过使用 `requests` 库从 API 获取实时数据并将其加载到 DataFrame 中，您可以操作和分析动态数据源。我们提供了一个从 JSONPlaceholder API 获取数据并使用 `pd.DataFrame()` 构造函数将其加载到 DataFrame 的示例。

之后，我们讨论了使用 Beautiful Soup 进行网页抓取。通过从网站获取 HTML 内容，使用 Beautiful Soup 解析，提取结构化数据并将其加载到 DataFrame 中，您可以处理来自动态网页内容的数据。我们提供了一个从 World Coin Index 网站抓取表格数据并将其加载到 DataFrame 的示例。

接下来，我们解释了如何在 Pandas 中处理缺失数据。`isna()` 和 `isnull()` 方法有助于识别缺失值，而 `dropna()` 和 `fillna()` 方法则通过根据您的需求移除或填充缺失值来处理它们。

最后，我们介绍了使用 Pandas 进行数据转换和清洗。此过程包括处理缺失数据、重命名列、转换数据类型、移除重复项、归一化或标准化数值列、编码分类变量，以及重排或删除列。这些步骤确保数据准确、一致且结构良好，以便进行进一步分析或机器学习应用。

总体而言，本章涵盖了使用 Pandas 进行数据操作的各个方面，包括从不同格式读取和写入数据、数据库交互、连接 Web API 和网页抓取、处理缺失数据，以及执行数据转换和清洗。

## 第 3 章：索引与数据选择





### 索引与选择基础

高效的数据分析和操作在很大程度上依赖于在 DataFrame 中访问、筛选和修改特定数据点、行或列的能力。Pandas 提供了一系列用于执行这些基本操作的重要工具，例如索引和选择。这些工具不仅允许快速轻松地检索特定数据，还能以更高的准确性和速度执行数据清洗和转换任务。凭借 Pandas 强大的索引和选择功能，数据分析师和科学家可以高效地处理复杂数据集，并提取推动明智决策的洞察。

在本示例中，我们假设您已将 `Customer_Churn_Modelling.csv` 数据集加载到一个名为 `data` 的 DataFrame 中。

#### 选择列

您可以使用列名选择单个列：

```
credit_scores = data['CreditScore']
```

或通过提供列名列表来选择多个列：

```
selected_columns = data[['CreditScore', 'Age', 'Exited']]
```

#### 按索引选择行

您可以使用 `iloc[]` 和 `loc[]` 属性选择行。`iloc[]` 属性用于基于整数的索引，而 `loc[]` 属性用于基于标签的索引。

使用 `iloc[]` 选择第一行：

```
first_row = data.iloc[0]
```

使用 `iloc[]` 选择多行：

```
rows_2_to_4 = data.iloc[1:4]
```

使用 `loc[]` 按索引标签选择特定行（假设 DataFrame 具有自定义索引）：

```
row_with_label = data.loc['index_label']
```

#### 选择特定数据点

您可以结合行和列选择来访问特定数据点。

使用 `iloc[]` 选择第一行第一列的值：

```
first_value = data.iloc[0, 0]
```

使用 `loc[]` 按行和列标签选择值（假设 DataFrame 具有自定义索引）：

```
specific_value = data.loc['index_label', 'CreditScore']
```

#### 条件选择

您可以使用布尔条件根据特定标准筛选行。例如，选择 `'Exited'` 等于 1 的行：

```
exited_rows = data[data['Exited'] == 1]
```

您还可以使用 `&`（与）或 `|`（或）运算符组合多个条件：

```
exited_and_has_credit_card = data[(data['Exited'] == 1) & (data['Has_Credit_Card'] == True)]
```

#### 设置自定义索引

您可以使用 `set_index()` 方法设置自定义索引。例如，将 `'CustomerId'` 列设置为索引：

```
data = data.set_index('CustomerId')
```

请记住，此操作会创建一个具有自定义索引的新 DataFrame。如果您想修改现有的 DataFrame，请将 `inplace` 参数设置为 `True`：

```
data.set_index('CustomerId', inplace=True)
```

总之，索引和选择是 Pandas 中的基本操作，允许您访问和操作 DataFrame 中的特定数据点、行或列。通过使用 `iloc[]`、`loc[]` 和条件选择等方法，您可以高效地执行各种数据分析、清洗和转换任务。

### 多重索引与层次索引

层次索引，也称为多重索引，是 Pandas 的一项功能，它支持在单个 DataFrame 中创建多层索引。当处理复杂的多维数据集时，此功能特别有用，因为它允许以更有组织、更自然的方式处理数据。通过建立层次索引，用户可以根据特定的索引层级轻松切片和操作数据子集，从而实现更精确、更高效的分析。此外，层次索引有助于减少重塑和重组数据的需求，这可以在分析的数据准备阶段节省时间和精力。

假设您已将 `Customer_Churn_Modelling.csv` 数据集加载到一个名为 `data` 的 DataFrame 中。我们将基于 `'Geography'` 和 `'Gender'` 列创建一个多层索引。

#### 创建多层索引

您可以使用 `set_index()` 方法并提供列列表来创建多层索引：

```
data_multi = data.set_index(['Geography', 'Gender'])
```

现在，DataFrame 拥有基于 `'Geography'` 和 `'Gender'` 的多层索引。要查看 DataFrame 的前几行：

```
print(data_multi.head())
```

#### 使用多层索引访问数据

您可以使用 `loc[]` 属性访问多层索引中的数据。例如，访问 `'France'` 和 `'Female'` 组的所有数据：

```
france_female = data_multi.loc[('France', 'Female')]
```

#### 使用多层索引进行切片

使用 `slice(None)` 函数，您可以对多层索引执行切片操作。例如，选择 `'Geography'` 为 `'Germany'` 的所有行：

```
germany_data = data_multi.loc[(slice('Germany', 'Germany'), slice(None)), :]
```

#### 选择特定层级的数据

您可以使用 `xs()` 方法选择特定层级的数据。例如，选择 `'Gender'` 为 `'Male'` 的所有数据：

```
male_data = data_multi.xs('Male', level='Gender', axis=0)
```

#### 交换层级

您可以使用 `swaplevel()` 方法交换多层索引的层级。例如，交换 `'Geography'` 和 `'Gender'` 层级：

```
data_swapped = data_multi.swaplevel('Geography', 'Gender')
```

#### 对多层索引排序

您可以使用 `sort_index()` 方法根据索引层级对 DataFrame 进行排序。按 `'Geography'` 和 `'Gender'` 层级对 DataFrame 排序：

```
data_sorted = data_multi.sort_index(level=['Geography', 'Gender'])
```

#### 重置多层索引

要重置多层索引并将其转换回列，请使用 `reset_index()` 方法：

```
data_flat = data_multi.reset_index()
```

总之，Pandas 中的多重索引或层次索引允许您在单个 DataFrame 中拥有多个索引层级，为处理高维数据提供了更结构化、更直观的方式。通过使用 `set_index()` 方法创建多层索引，并使用 `loc[]`、`xs()`、`swaplevel()` 和 `sort_index()` 等各种方法，您可以高效地操作和访问多层索引中的数据。





### 使用布尔值和条件选择进行索引

使用布尔值和条件选择进行索引，可以根据特定条件对 DataFrame 中的行进行筛选。这些技术对于一系列数据分析、清洗和转换任务非常有价值。通过使用布尔索引，您可以选择满足特定标准的数据行，例如选择某个特定列满足特定条件的所有行。同样，条件选择允许您基于更复杂的标准筛选数据，例如选择多个列同时满足特定条件的所有行。这些技术是强大的数据操作工具，可应用于各种场景，如数据预处理、探索性数据分析和机器学习。

我们假设您已经将 `Customer_Churn_Modelling.csv` 数据集加载到了一个名为 `data` 的 DataFrame 中。

#### 布尔索引

布尔索引涉及创建一个布尔掩码，即一个与 DataFrame 具有相同索引的 Pandas Series，根据条件包含 `True` 或 `False` 值。当将此掩码应用于 DataFrame 时，仅选择值为 `True` 的行。

例如，让我们为 `'Exited'` 列等于 1 的行创建一个布尔掩码：

```
mask = data['Exited'] == 1
```

现在，将布尔掩码应用于 DataFrame 以筛选行：

```
exited_customers = data[mask]
```

您也可以直接应用掩码：

```
exited_customers = data[data['Exited'] == 1]
```

#### 多条件条件选择

您可以使用 `&`（与）或 `|`（或）运算符来组合多个条件。

例如，要选择 `'Exited'` 等于 1 **且** `'Age'` 大于 40 的行：

```
exited_and_age_above_40 = data[(data['Exited'] == 1) & (data['Age'] > 40)]
```

或者，要选择 `'Exited'` 等于 1 **或** `'Age'` 大于 40 的行：

```
exited_or_age_above_40 = data[(data['Exited'] == 1) | (data['Age'] > 40)]
```

#### 使用 `query()` 方法进行条件选择

执行条件选择的另一种方法是使用 `query()` 方法。此方法允许您将条件写为字符串表达式。

例如，要选择 `'Exited'` 等于 1 **且** `'Age'` 大于 40 的行：

```
exited_and_age_above_40 = data.query("Exited == 1 and Age > 40")
```

总之，Pandas 中的布尔索引和条件选择允许您根据特定条件筛选 DataFrame 中的行。通过创建布尔掩码、使用 `&` 或 `|` 运算符组合多个条件，或使用 `query()` 方法，您可以更高效地执行各种数据分析、清洗和转换任务。

### 使用 `.loc[]`、`.iloc[]` 和 `.at[]`

Pandas 中的 `.loc[]`、`.iloc[]` 和 `.at[]` 属性用于根据不同标准访问和选择 DataFrame 中的数据。它们对于数据分析、清洗和转换任务非常有用。

我们假设您已经将 `Customer_Churn_Modelling.csv` 数据集加载到了一个名为 `data` 的 DataFrame 中。

#### `.loc[]` 属性

`.loc[]` 属性用于**基于标签的索引**。您可以使用它通过行和列标签来选择数据。

例如，假设您已将 `'CustomerId'` 列设置为索引：

```
data = data.set_index('CustomerId')
```

要选择特定信用评分的数据：

```
customer_data = data.loc[15745662, 'CreditScore']
```

要使用 `.loc[]` 属性选择多行和多列，可以传入标签列表或切片：

```
selected_customers = data.loc[[15745662, 15734523], ['CreditScore', 'Age']]
selected_rows_columns = data.loc[15745662:15734523, 'CreditScore':'Age']
```

#### `.iloc[]` 属性

`.iloc[]` 属性用于**基于整数位置的索引**。您可以使用它通过行和列的位置来选择数据。

例如，要选择第一行第二列的数据：

```
first_row_second_column = data.iloc[0, 1]
```

要使用 `.iloc[]` 属性选择多行和多列，可以传入位置列表或切片：

```
selected_rows = data.iloc[[0, 1, 2], :]
selected_columns = data.iloc[:, [0, 1, 2]]
selected_rows_columns = data.iloc[0:3, 0:3]
```

#### `.at[]` 属性

`.at[]` 属性用于**标量值的快速基于标签的索引**。它类似于 `.loc[]`，但针对访问单个数据点进行了优化，使其在该特定用例下更快。

例如，要选择特定客户 ID 和列的数据：

```
customer_data = data.at[15745662, 'CreditScore']
```

请记住，`.at[]` 只能用于访问单个数据点，不能用于选择多行或多列。

总之，Pandas 中的 `.loc[]`、`.iloc[]` 和 `.at[]` 属性用于根据不同标准访问和选择 DataFrame 中的数据：`.loc[]` 和 `.at[]` 用于基于标签的索引，`.iloc[]` 用于基于整数位置的索引。通过使用这些属性，您可以高效地执行各种数据分析、清洗和转换任务。

### 切片和子集数据

Pandas 提供了切片和子集技术，使用户能够根据位置或索引标签从 DataFrame 中提取特定的行、列或数据点。这些方法对于数据分析、清洗和转换等任务非常有价值。通过使用切片，可以切分 DataFrame 并选择所需的行和列。子集化是另一种技术，涉及基于原始数据的子集创建新的 DataFrame。借助这些方法，用户可以轻松隔离相关数据并执行必要的修改，而不会影响原始数据。

现在，我们假设您已经将 `Customer_Churn_Modelling.csv` 数据集加载到了一个名为 `data` 的 DataFrame 中。

#### 切片行

您可以使用带有起始和结束索引的 `iloc[]` 属性按位置切片行。

例如，要选择索引 5 到 9 的行：

```
subset_rows = data.iloc[5:10]
```

#### 切片列

您也可以使用 `iloc[]` 属性按位置切片列。

例如，要选择前三列：

```
subset_columns = data.iloc[:, :3]
```

#### 同时切片行和列

您可以使用 `iloc[]` 属性结合行和列切片。

例如，要选择索引 5 到 9 的行以及前三列：

```
subset_data = data.iloc[5:10, :3]
```

#### 使用 `loc[]` 属性进行切片

如果您想基于索引标签而不是位置进行切片，可以使用 `loc[]` 属性。

例如，假设您已将 `'CustomerId'` 设置为索引，要选择索引标签从 15634602 到 15634606 的行：

```
subset_data_labels = data.loc[15634602:15634606, :]
```

#### 基于列名的子集数据

您可以通过提供列名列表来选择特定列。

例如，要仅选择 `'CreditScore'`、`'Age'` 和 `'Exited'` 列：

```
selected_columns = data[['CreditScore', 'Age', 'Exited']]
```

#### 使用条件进行子集数据选择（布尔索引）

您可以使用布尔索引根据特定条件选择行。

例如，要选择 `'Exited'` 等于 1 的行：

```
exited_customers = data[data['Exited'] == 1]
```

#### 使用 `query()` 方法进行子集数据选择

您可以使用 `query()` 方法根据以字符串形式表示的特定条件筛选行。

例如，要选择 `'Exited'` 等于 1 **且** `'Age'` 大于 40 的行：

```
exited_and_age_above_40 = data.query("Exited == 1 and Age > 40")
```

总之，Pandas 中的切片和子集数据选择允许您根据位置、索引标签或条件选择 DataFrame 中的特定行、列或数据点。通过使用 `iloc[]`、`loc[]`、布尔索引或 `query()` 方法等方法，您可以更高效地执行各种数据分析、清洗和转换任务。




### 使用索引和选择修改数据

Pandas 提供了索引和选择技术，这些技术不仅允许选择数据，还允许修改 DataFrame 内部的数据。除了选择数据，这些技术还能对 DataFrame 中特定的数据子集进行更改，例如更新或替换值、添加或删除列或行等。这种数据操作的灵活性有助于各种数据分析任务，并允许用户高效地执行复杂操作。

以下是一些使用索引和选择方法修改数据的示例：

#### 使用 `.at[]` 属性修改单个值

`.at[]` 属性可用于根据行和列标签修改 DataFrame 中的单个值。例如，假设您已将 `'CustomerId'` 列设置为索引：

```python
data.at[15745662, 'CreditScore'] = 750
```

这会将 ID 为 `15745662` 的客户的 `'CreditScore'` 值设置为 `750`。

#### 使用 `.iat[]` 属性修改单个值

与 `.at[]` 属性类似，您可以使用 `.iat[]` 属性根据行和列位置修改 DataFrame 中的单个值：

```python
data.iat[0, 0] = 750
```

这会将第一行第一列的值设置为 `750`。

#### 使用布尔索引修改列中的多个值

您可以使用布尔索引根据条件修改列中的多个值。例如，将所有年龄大于 `40` 的客户的 `'CreditScore'` 增加 `10` 分：

```python
mask = data['Age'] > 40
data.loc[mask, 'CreditScore'] += 10
```

#### 使用 `.apply()` 方法修改列中的值

您可以使用 `.apply()` 方法将自定义函数应用于列中的每个值。例如，将 `'CreditScore'` 值四舍五入到最近的 `10` 的倍数：

```python
import numpy as np

def round_to_nearest_ten(x):
    return np.round(x, -1)

data['CreditScore'] = data['CreditScore'].apply(round_to_nearest_ten)
```

#### 使用 `.applymap()` 方法修改多列中的值

您可以使用 `.applymap()` 方法将自定义函数应用于多列中的每个值。例如，将所有数值列四舍五入到最近的整数：

```python
numerical_columns = ['CreditScore', 'Age', 'Tenure', 'Balance', 'NumOfProducts', 'EstimatedSalary']
data[numerical_columns] = data[numerical_columns].applymap(np.round)
```

总之，您可以使用 Pandas 中的索引和选择技术，如 `.at[]`、`.iat[]`、布尔索引、`.apply()` 和 `.applymap()` 方法来修改 DataFrame 中的数据。这些技术对于各种数据分析、清洗和转换任务非常有用。

### 高级索引技术

#### 截面 (`xs()`) 方法

`xs()` 方法允许您根据多级索引 DataFrame 的特定层级选择数据。当您拥有具有层次化索引的 DataFrame 时，这非常有用。让我们创建一个以 `'Geography'` 和 `'Gender'` 为索引层级的多级索引 DataFrame：

```python
multi_indexed_data = data.set_index(['Geography', 'Gender'])
```

现在，您可以使用 `xs()` 方法选择特定层级的数据：

```python
german_customers = multi_indexed_data.xs('Germany', level='Geography')
```

#### `where()` 方法

`where()` 方法允许您根据条件筛选数据，同时保持 DataFrame 的原始形状。当您想要保留 DataFrame 结构或可视化数据时，这非常有用。例如，仅保留 `'Exited'` 等于 `1` 的行，并将其他行替换为 `NaN`：

```python
exited_customers = data.where(data['Exited'] == 1)
```

#### `mask()` 方法

`mask()` 方法的工作方式与 `where()` 方法类似，但会反转条件。它不是保留满足条件的数据点，而是将它们替换为 `NaN` 或指定值。例如，将所有流失客户的 `'CreditScore'` 值替换为 `NaN`：

```python
data['CreditScore'] = data['CreditScore'].mask(data['Exited'] == 1)
```

#### `isin()` 方法

`isin()` 方法允许您根据值是否在给定列表中来筛选数据。当您想要选择特定类别或组的数据时，这非常有用。例如，选择 `'Geography'` 为 `'France'` 或 `'Germany'` 的行：

```python
selected_countries = data[data['Geography'].isin(['France', 'Germany'])]
```

#### `eval()` 方法

`eval()` 方法允许您计算涉及 DataFrame 列的复杂表达式。当您想要执行涉及多列的算术运算或布尔条件时，这非常有用。例如，计算每个客户的 `'Balance'` 与 `'EstimatedSalary'` 的比率：

```python
data['BalanceToSalaryRatio'] = data.eval("Balance / EstimatedSalary")
```

总之，Pandas 中的高级索引技术，如 `xs()`、`where()`、`mask()`、`isin()` 和 `eval()` 方法，可以帮助您更高效地访问和操作给定数据库中的数据。这些技术提供了更大的灵活性，对于各种数据分析、清洗和转换任务非常有用。

### 总结

我们讨论了 Pandas 中不同的索引和选择方法，包括 `.loc[]`、`.iloc[]` 和 `.at[]`。`.loc[]` 属性用于基于标签的索引，允许您通过行和列标签选择数据。`.iloc[]` 属性用于基于整数（位置）的索引，允许您通过行和列位置选择数据。`.at[]` 属性用于标量值的快速基于标签的索引，并针对访问单个数据点进行了优化。

然后我们讨论了使用索引和选择技术修改数据。`.at[]` 和 `.iat[]` 属性可用于根据行和列标签或位置修改 DataFrame 中的单个值。布尔索引允许您根据条件修改列中的多个值。`.apply()` 方法可用于将自定义函数应用于列中的每个值，而 `.applymap()` 方法可用于将自定义函数应用于多列中的每个值。

接下来，我们介绍了 Pandas 中的高级索引技术，包括 `xs()`、`where()`、`mask()`、`isin()` 和 `eval()` 方法。`xs()` 方法允许您根据多级索引 DataFrame 的特定层级选择数据。`where()` 方法根据条件筛选数据，同时保持 DataFrame 的原始形状。`mask()` 方法的工作方式与 `where()` 方法类似，但会反转条件，将满足条件的数据点替换为 `NaN` 或指定值。`isin()` 方法根据值是否在给定列表中筛选数据，适用于选择特定类别或组的数据。`eval()` 方法计算涉及 DataFrame 列的复杂表达式，适用于执行涉及多列的算术运算或布尔条件。

这些索引、选择和高级技术提供了灵活高效的方式来访问、操作和修改 Pandas DataFrame 中的数据。它们是数据分析、清洗和转换任务的必备工具。

## 第 4 章：数据操作与转换



### 在 Pandas 中合并和连接 DataFrame

在 Pandas 中，基于公共列或索引组合两个或多个 DataFrame 的过程可以通过合并和连接来实现。这些操作在管理多个相关数据集方面起着关键作用，允许进行高效的数据分析和操作。通过合并 DataFrame，可以基于共享列组合数据，从而生成一个包含所有相关信息的单个 DataFrame。另一方面，连接 DataFrame 则基于其索引实现两个或多个 DataFrame 的组合。这两种技术都有助于简化数据管理、提高数据质量，并更好地理解数据集之间的关系。因此，理解如何在 Pandas 中合并和连接 DataFrame 是数据分析师和科学家的一项重要技能。

为了演示，假设您有另一个包含客户收入数据的数据集。我们将创建一个名为 `customer_income` 的小型 DataFrame，它与 `data` DataFrame 具有相同的 `CustomerId` 列：

```python
import pandas as pd
customer_income = pd.DataFrame({
    'CustomerId': [15745662, 15734523, 15698723],
    'AnnualIncome': [55000, 68000, 45000]
})
```

#### 使用 `merge()` 函数合并 DataFrame

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

#### 使用 `join()` 方法连接 DataFrame

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

### 连接和追加 DataFrame

在 Pandas 中，合并和添加 DataFrame 是指沿特定轴（水平或垂直）连接两个或多个 DataFrame 的过程。当您拥有具有相同行或列的多个数据集并希望将它们堆叠在一起时，此技术非常有用。连接和追加是 Pandas 中组合 DataFrame 的两种方法。连接用于将 DataFrame 堆叠在彼此之上或并排，而追加则向现有 DataFrame 添加新行。这两种方法在创建包含来自原始数据集所有必要信息的单个 DataFrame 时都很有用。

为了演示，假设您有两个数据集 `data1` 和 `data2`，它们是原始 `data` DataFrame 的子集：

```python
data1 = data.head(10)
data2 = data.tail(10)
```

#### 使用 `concat()` 函数连接 DataFrame

`concat()` 函数沿特定轴组合 DataFrame。默认情况下，它沿行（`axis=0`）连接 DataFrame。下面展示如何连接 `data1` 和 `data2`：

```python
concatenated_data = pd.concat([data1, data2])
```

要沿列连接 DataFrame，请将 `axis` 参数设置为 1：

```python
concatenated_data_columns = pd.concat([data1, data2], axis=1)
```

请记住，当沿列连接 DataFrame 时，它们拥有相同的索引至关重要。否则，结果中可能会出现缺失值。

#### 使用 `append()` 方法追加 DataFrame

`append()` 方法是沿行组合 DataFrame 的一种便捷方式，类似于使用 `concat()` 函数沿行连接。您可以按如下方式将 `data2` 追加到 `data1`：

```python
appended_data = data1.append(data2)
```

请注意，`append()` 方法不会修改原始 DataFrame；它会创建一个包含组合数据的新 DataFrame。

总之，Pandas 中的连接和追加 DataFrame 允许您沿特定轴（行或列）组合两个或多个 DataFrame。`concat()` 函数沿指定轴组合 DataFrame，而 `append()` 方法是沿行组合 DataFrame 的一种便捷方式。当您拥有具有相同列或行的多个数据集并希望将它们堆叠在一起时，这些操作非常有用。

#### 连接和追加的示例程序

让我们使用给定的 `Customer_Churn_Modelling.csv` 数据集创建另一个示例。我们将首先用原始数据的不同子集创建两个新 DataFrame，然后连接和追加它们。

##### 将原始数据拆分为两个子集

```python
# Read the original data
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")

# Create subsets of data for customers from France and Spain
data_france = data[data['Geography'] == 'France']
data_spain = data[data['Geography'] == 'Spain']
```

##### 连接 DataFrame

```python
# Concatenate the DataFrames along the rows (axis=0)
concatenated_data = pd.concat([data_france, data_spain])
```

##### 追加 DataFrame

```python
# Append 'data_spain' to 'data_france'
appended_data = data_france.append(data_spain)
```

`concatenated_data` 和 `appended_data` 都将包含原始 DataFrame 中来自法国和西班牙的客户的行。尽管在这个例子中连接和追加 DataFrame 沿行的结果相同，但这些技术可以根据您的需求用于不同的场景。请记住，`concat()` 可用于沿行或列组合 DataFrame，而 `append()` 专门用于沿行组合 DataFrame。




### 数据透视与熔化

在 Pandas 中，数据透视和熔化涉及通过改变数据结构来重塑数据，而不改变实际数据。透视将数据从长格式转换为宽格式，而熔化则执行相反的操作。

#### 使用 `pivot()` 方法透视 DataFrame

透视 DataFrame 意味着根据现有列设置索引、列和值来重塑它。`pivot()` 方法接受三个主要参数：`index`、`columns` 和 `values`。

例如，假设你想创建一个透视表，以显示给定数据集中每个地理区域和性别组合的平均信用评分：

```
# 计算每个地理区域和性别组合的平均信用评分
average_credit_score = data.groupby(['Geography', 'Gender'])['CreditScore'].mean().reset_index()

# 透视 DataFrame
pivot_data = average_credit_score.pivot(index='Geography', columns='Gender', values='CreditScore')
```

生成的 `pivot_data` DataFrame 将以 `Geography` 为索引，`Gender` 为列，平均信用评分为值。

#### 使用 `melt()` 函数熔化 DataFrame

熔化 DataFrame 意味着通过将多列移动到单个列中，将其从宽格式重塑为长格式。`melt()` 函数接受三个主要参数：`id_vars`、`value_vars` 和 `var_name`。

例如，让我们将 `pivot_data` DataFrame 熔化回长格式：

```
melted_data = pd.melt(pivot_data.reset_index(), id_vars='Geography', value_vars=['Female', 'Male'], var_name='Gender', value_name='AverageCreditScore')
```

生成的 `melted_data` DataFrame 将具有长格式，包含 `Geography`、`Gender` 和 `AverageCreditScore` 列。

总之，Pandas 中的数据透视和熔化是重塑数据而不改变实际数据的技术。透视涉及使用 `pivot()` 方法将数据从长格式转换为宽格式，而熔化涉及使用 `melt()` 函数将数据从宽格式转换为长格式。这些技术可以通过改变数据结构，帮助你更好地理解、可视化和分析数据。

### 数据转换函数：`apply()`、`map()` 和 `applymap()`

Pandas 提供了数据转换函数，包括 `apply()`、`map()` 和 `applymap()`，它们提供了将自定义函数应用于 DataFrame 或 Series 中的单个元素、行或列的能力。这些函数以高度适应性和高效的方式实现数据操作和转换。利用这些函数，数据可以被转换和操作以满足特定需求。`apply()` 将函数应用于 DataFrame 的每个元素或行/列，而 `map()` 将函数应用于 Series 的每个元素。`applymap()` 将函数应用于 DataFrame 的每个元素。这一系列函数提供了一个全面的工具包来转换和操作数据。

#### `apply()` 函数

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

#### `map()` 函数

`map()` 函数用于将函数应用于 Series 的每个元素。当你想对单个列执行逐元素转换时，它非常有用。

例如，假设你想将 `data` DataFrame 中的 `Geography` 列更新为大写值：

```
data['Geography'] = data['Geography'].map(lambda x: x.upper())
```

#### `applymap()` 函数

`applymap()` 函数用于将函数应用于 DataFrame 的每个元素。当你想对多列执行逐元素转换时，它非常有用。

例如，假设你想将 `data` DataFrame 中所有数值列四舍五入为整数：

```
numeric_cols = data.select_dtypes(include='number').columns
data[numeric_cols] = data[numeric_cols].applymap(lambda x: round(x))
```

总之，Pandas 中的数据转换函数如 `apply()`、`map()` 和 `applymap()` 允许你将特定函数应用于 DataFrame 或 Series 中的元素、行或列。`apply()` 函数用于沿 DataFrame 的轴或应用于 Series 应用函数，`map()` 函数用于将函数应用于 Series 的每个元素，`applymap()` 函数用于将函数应用于 DataFrame 的每个元素。这些函数帮助你以灵活高效的方式转换和操作数据。

### 数据分组与聚合

在 Pandas 中，分组和聚合数据的过程涉及使用 `groupby()` 函数根据一个或多个列对数据进行分组，随后对分组后的数据应用聚合函数。当根据特定类别或类别组合分析数据时，此技术非常有用。通过 `groupby()` 函数，可以将数据组织成具有相似值的组，并对这些组内的数据执行数学运算。分组和聚合数据有助于更好地理解数据集中的模式，并有助于识别原本可能不易察觉的趋势或洞察。

让我们使用 `Customer_Churn_Modelling.csv` 数据集演示一个示例。我们将按 `Geography` 和 `Gender` 对数据进行分组，并计算每组的平均信用评分。

#### 读取数据

```
import pandas as pd
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")
```

#### 使用 `groupby()` 分组数据

```
grouped_data = data.groupby(['Geography', 'Gender'])
```

这将创建一个按 `Geography` 和 `Gender` 分组数据的 `groupby` 对象。现在你可以对分组后的数据应用聚合函数。

#### 使用聚合函数聚合数据

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



### 自定义聚合函数

Pandas 提供了灵活性，允许定义并使用可应用于分组数据的自定义聚合函数。当内置聚合函数无法满足用户的特定需求，或用户希望对数据进行复杂计算时，此功能非常实用。通过定义自定义聚合函数，用户可以根据自身需求定制分析，从数据中获取有意义的见解。此功能增强了 Pandas 的通用性，赋予用户利用 Python 高效操作数据的能力。无论是简单计算还是复杂操作，自定义聚合函数都能让用户高效处理数据，最大化其价值。

让我们通过 `Customer_Churn_Modelling.csv` 数据集来演示一个示例。我们将按 `Geography` 和 `Gender` 对数据分组，并使用自定义聚合函数计算每组信用评分的极差（最大值-最小值）。

#### 读取数据

```python
import pandas as pd
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")
```

#### 定义自定义聚合函数

在本例中，我们将创建一个函数来计算给定 Series 的极差（最大值-最小值）：

```python
def credit_score_range(series):
    return series.max() - series.min()
```

#### 使用 `groupby()` 分组数据

```python
grouped_data = data.groupby(['Geography', 'Gender'])
```

这将创建一个按 `Geography` 和 `Gender` 分组的 `groupby` 对象。现在您可以将自定义聚合函数应用于分组数据。

#### 应用自定义聚合函数

在本例中，我们将使用 `agg()` 函数将自定义聚合函数 (`credit_score_range`) 应用于每组的 `CreditScore` 列：

```python
credit_score_ranges = grouped_data['CreditScore'].agg(credit_score_range)
```

`credit_score_ranges` 变量现在包含一个 Series，其中存储了每种 `Geography` 和 `Gender` 组合下的信用评分极差。

您还可以同时应用多个聚合函数，包括内置函数和自定义函数。例如，让我们计算每组信用评分的平均值和极差：

```python
credit_score_summary = grouped_data['CreditScore'].agg(['mean', credit_score_range])
```

`credit_score_summary` 变量现在包含一个 DataFrame，其中存储了每种 `Geography` 和 `Gender` 组合下的信用评分平均值和极差。

总之，Pandas 中的自定义聚合函数允许您创建自己的聚合函数并将其应用于分组数据。当内置聚合函数无法满足您的特定需求，或您想对数据执行更复杂的计算时，这非常有用。在给定示例中，我们创建了一个自定义聚合函数来计算信用评分的极差，并将其应用于按 `Geography` 和 `Gender` 分组的数据。

### 总结

在本章中，我们讨论了 Pandas 中的各种高级操作和技术，如下所示：

- **分组与聚合数据**：我们解释了如何使用 `groupby()` 函数根据一列或多列对数据进行分组，并对分组数据应用聚合函数。我们以 `Customer_Churn_Modelling.csv` 数据集为例，按 `Geography` 和 `Gender` 对数据分组，计算每组的平均信用评分。
- **自定义聚合函数**：我们讲授了如何创建自定义聚合函数并将其应用于分组数据。我们使用相同的数据集，创建了一个自定义聚合函数，根据 `Geography` 和 `Gender` 计算每组信用评分的极差（最大值-最小值）。
- **数据转换函数**：我们描述了 Pandas 中的 `apply()`、`map()` 和 `applymap()` 函数，它们允许您将特定函数应用于 DataFrame 或 Series 中的元素、行或列。我们提供了在给定数据集上使用这些函数执行各种任务的示例，例如计算数值列的值域、将 `Geography` 列更新为大写值，以及将所有数值列四舍五入为整数。
- **合并与连接 DataFrame**：我们解释了合并和连接 DataFrame 的概念，并提供了在给定数据集上执行这些操作的实际示例。
- **连接与追加 DataFrame**：我们解释了连接和追加 DataFrame 的概念，并提供了在给定数据集上执行这些操作的实际示例。
- **数据透视与熔化 DataFrame**：我们描述了数据透视和熔化 DataFrame 的概念，并提供了在给定数据集上执行这些操作的实际示例。

贯穿全章，我们专注于实际示例和分步说明，帮助您学习并将这些高级 Pandas 技术应用于 `Customer_Churn_Modelling.csv` 数据集。

## 第 5 章：时间序列与 DateTime 操作




### 时间序列数据简介

时间序列数据是按时间顺序、在固定的时间间隔内收集或记录的一系列数据点。这些数据点可以是感兴趣变量的观测值或测量值，例如股票价格、温度读数或销售数字。时间序列数据的主要特征是其固有的时间结构，这能提供关于模式、趋势、季节性以及不同变量随时间变化关系的洞察。分析时间序列数据使我们能够了解过去的行为、识别影响变量的因素，并预测未来的值。

时间序列分析在金融、经济、气象、医疗保健和社会科学等各个领域都有广泛的应用。`Pandas` 是 Python 中广泛使用的数据处理库，因其对处理和加工时间数据的广泛支持，已成为时间序列数据分析的首选工具。

使 `Pandas` 成为时间序列分析强大工具的一些关键特性包括：

*   **专为时间序列数据设计的数据结构**：`Pandas` 提供了 `Series` 和 `DataFrame` 数据结构，它们内置了对基于时间的索引的支持。这使得时间序列数据的高效灵活操作成为可能。
*   **基于时间的索引和切片**：`Pandas` 支持基于时间的索引，这使得根据日期和时间值选择、过滤和修改数据变得容易。你可以使用简单直观的语法执行基于范围的查询、选择特定时期，或以不同频率对数据进行重采样。
*   **日期和时间对象**：`Pandas` 与 Python 内置的 `datetime` 模块集成，并通过其自身的 `Timestamp`、`Period` 和 `Timedelta` 对象提供额外功能。这些对象简化了日期、时间和间隔的处理，使你能够轻松地执行计算、比较和转换。
*   **重采样和频率转换**：`Pandas` 提供了强大的重采样方法，使你能够更改数据的频率、将数据聚合到不同时间段，或插值缺失值。当你想在不同粒度级别分析数据或填补数据集中的空白时，这非常有用。
*   **时区处理**：时间序列数据通常来自不同时区的来源，管理这些时区可能是一项复杂的任务。`Pandas` 为时区转换、本地化和标准化提供了强大的支持，使处理来自多个时区的数据变得容易。
*   **滚动和扩展窗口函数**：`Pandas` 允许你将滚动和扩展窗口函数应用于时间序列数据，这有助于识别趋势、计算移动平均值或计算累积和。这些函数可以通过各种窗口类型和聚合函数进行自定义，以满足你的需求。
*   **数据平移和滞后**：时间序列分析通常涉及比较不同时间段的数据点或计算连续值之间的差异。`Pandas` 提供了用于数据平移和滞后的方法，使你能够高效准确地执行这些操作。
*   **与其他库的集成**：`Pandas` 与其他 Python 库（如 `NumPy`、`SciPy` 和 `scikit-learn`）无缝集成，允许你对时间序列数据执行高级统计分析、建模和机器学习。
*   **各种文件格式的输入/输出支持**：`Pandas` 支持从多种文件格式读取和写入数据，包括 CSV、Excel、JSON 和 SQL 数据库。这使得从不同来源和格式导入和导出时间序列数据变得容易。

总之，时间序列数据是按时间顺序、在固定的时间间隔内收集或记录的一系列数据点。分析时间序列数据能提供关于随时间变化的模式、趋势和关系的宝贵见解。`Pandas` 是 Python 中强大的数据处理库，因其对处理和加工时间数据的广泛支持，已成为时间序列数据分析的首选工具。

### DateTime 对象和函数

`Pandas` 中的 `DateTime` 对象和函数旨在高效地处理和操作日期和时间数据。该库扩展了 Python 内置 `datetime` 模块的功能，通过其 `Timestamp`、`Period` 和 `Timedelta` 对象提供额外支持。这些工具使用户能够轻松操作和管理基于时间的数据，使其成为许多数据分析和建模任务的必备工具。通过利用 `Pandas` 的强大功能，用户可以简化工作流程，并轻松从时间数据中获得洞察。

我们将详细讨论这些对象和函数，并演示如何结合 `Customer_Churn_Modelling.csv` 数据集使用它们。

#### Timestamp

`Timestamp` 对象代表单个时间点。它是 Python `datetime.datetime` 对象在 `Pandas` 中的等价物。你可以通过将日期或日期时间字符串传递给 `pd.Timestamp()` 函数来创建 `Timestamp` 对象。

```
import pandas as pd
timestamp_example = pd.Timestamp('2023-04-12 12:00:00')
print(timestamp_example)
```

#### Period

`Period` 对象代表一个时间跨度或持续时间，例如一天、一个月或一年。你可以通过将日期或日期时间字符串和频率传递给 `pd.Period()` 函数来创建 `Period` 对象。

```
period_example = pd.Period('2023-04', freq='M')
print(period_example)
```

#### Timedelta

`Timedelta` 对象代表两个日期或时间之间的差值。它是 Python `datetime.timedelta` 对象在 `Pandas` 中的等价物。你可以通过将持续时间字符串传递给 `pd.Timedelta()` 函数来创建 `Timedelta` 对象。

```
timedelta_example = pd.Timedelta('1 day')
print(timedelta_example)
```

现在让我们看看如何将这些 `DateTime` 对象和函数与 `Customer_Churn_Modelling.csv` 数据集结合使用。首先，我们将加载数据集：

```
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")
```

假设数据集有一个格式为 `'YYYY-MM-DD'` 的 `'Date'` 列，我们可以使用 `pd.to_datetime()` 函数将此列转换为 datetime 数据类型：

```
data['Date'] = pd.to_datetime(data['Date'])
```

现在 `'Date'` 列包含 `Timestamp` 对象，可用于基于时间的索引、切片和其他操作。例如，我们可以筛选特定日期范围的数据：

```
date_range_mask = (data['Date'] >= '2020-01-01') & (data['Date'] <= '2020-12-31')
filtered_data = data[date_range_mask]
```

我们还可以计算数据集中两个日期之间的差值：

```
date_difference = data['Date'].max() - data['Date'].min()
print(date_difference)
```

最后，我们可以使用 `DateTime` 对象和函数基于现有日期列创建新列。例如，让我们添加一列来表示 `'Date'` 列中每个日期的月份和年份：

```
data['Month_Year'] = data['Date'].apply(lambda x: pd.Period(x, freq='M'))
```

总之，`Pandas` 中的 `DateTime` 对象和函数（如 `Timestamp`、`Period` 和 `Timedelta`）提供了一种强大且灵活的方式来处理日期和时间数据。通过将这些对象和函数与 `Customer_Churn_Modelling.csv` 数据集结合使用，我们可以轻松地操作和分析时间序列数据，以完成各种任务，例如筛选、索引和基于现有日期列创建新列。




### 时间序列数据操作

时间序列数据操作涉及处理和转换基于时间的数据，以便于分析并获取洞察。在本节中，我们将通过一些实际示例，演示如何使用 Pandas 库和 `Customer_Churn_Modelling.csv` 数据集进行时间序列数据操作。

首先，让我们加载数据集并将 'Date' 列转换为 datetime 类型：

```python
import pandas as pd
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")
data['Date'] = pd.to_datetime(data['Date'])
```

假设数据集中的 'Date' 列代表记录客户数据的日期，我们可以执行各种时间序列数据操作任务：

#### 将日期列设置为索引

```python
data.set_index('Date', inplace=True)
```

#### 选择特定时间范围的数据

```python
selected_data = data['2020-01-01':'2020-12-31']
```

#### 将数据重采样为不同频率

将数据重采样为月度频率并计算均值：

```python
monthly_data = data.resample('M').mean()
```

将数据重采样为季度频率并计算总和：

```python
quarterly_data = data.resample('Q').sum()
```

#### 计算滚动统计量

计算 'CreditScore' 列的 7 天滚动平均值：

```python
data['CreditScore_7D_Rolling_Mean'] = data['CreditScore'].rolling(window=7).mean()
```

计算 'CreditScore' 列的 30 天滚动标准差：

```python
data['CreditScore_30D_Rolling_Std'] = data['CreditScore'].rolling(window=30).std()
```

计算连续值之间的差分（滞后）：

```python
data['CreditScore_Diff'] = data['CreditScore'].diff()
```

#### 在时间上向前或向后移动数据

将 'CreditScore' 列向前移动一个周期：

```python
data['CreditScore_Shifted_Forward'] = data['CreditScore'].shift(1)
```

将 'CreditScore' 列向后移动一个周期：

```python
data['CreditScore_Shifted_Backward'] = data['CreditScore'].shift(-1)
```

这些只是使用 Pandas 可以执行的时间序列数据操作任务的几个示例。通过将这些技术应用于 `Customer_Churn_Modelling.csv` 数据集，您可以随时间分析客户数据，识别趋势和模式，并获得关于客户行为和流失的宝贵洞察。

### 频率转换与重采样

在时间序列分析中，频率转换和重采样是常用技术，通过合并或估算原始数据点之间的值来修改数据频率。借助 Pandas，这些操作可以高效且灵活地执行。Pandas 提供了多种强大的工具来处理时间序列数据中的频率转换和重采样，有助于更好地理解和分析数据中的趋势和模式。在本节中，我们将演示如何使用 `Customer_Churn_Modelling.csv` 数据集进行频率转换和重采样。

首先，让我们加载数据集并将 'Date' 列转换为 datetime 类型：

```python
import pandas as pd
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")
data['Date'] = pd.to_datetime(data['Date'])
```

接下来，我们将 'Date' 列设置为索引：

```python
data.set_index('Date', inplace=True)
```

现在让我们对数据集执行频率转换和重采样：

#### 重采样

这涉及通过聚合数据点来改变数据频率。Pandas 中的 `resample()` 方法提供了一种执行重采样的简便方法。例如，让我们将数据重采样为月度频率并计算 'CreditScore' 列的均值：

```python
monthly_data_mean = data['CreditScore'].resample('M').mean()
```

同样，我们可以将数据重采样为季度频率并计算 'CreditScore' 列的总和：

```python
quarterly_data_sum = data['CreditScore'].resample('Q').sum()
```

#### 频率转换

这涉及在不聚合或插值数据点的情况下改变数据频率。Pandas 中的 `asfreq()` 方法可用于频率转换。例如，让我们将数据集的日频率转换为周频率：

```python
weekly_data = data.asfreq('W')
```

请记住，当您使用 `asfreq()` 执行频率转换时，如果新频率低于原始频率，可能会得到缺失值 (NaN)。

通过将频率转换和重采样技术与 `Customer_Churn_Modelling.csv` 数据集结合使用，您可以在不同时间频率下分析数据，识别趋势和模式，并深入了解客户行为和流失情况。这些技术使您能够执行更高级的时间序列分析，并基于数据做出更好的决策。

### 时区处理

时区处理是指对源自不同地理区域的时间相关信息进行管理，涉及时区间的时间转换以及在考虑时区差异的前提下执行各种基于时间的计算。它涉及准确解释和操作日期时间数据的能力，以确保在各种应用中显示、记录和使用正确的时间。这一过程对于旅游、金融和通信等行业至关重要，在这些行业中，时间是决策的关键因素，信息的准确性至关重要。在本节中，我们将演示如何使用 Pandas 库和 `Customer_Churn_Modelling.csv` 数据集进行时区处理。

#### 转换为 Datetime 类型

首先，让我们加载数据集并将 'Date' 列转换为 datetime 类型：

```python
import pandas as pd
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")
data['Date'] = pd.to_datetime(data['Date'])
```

#### 设置日期列为索引

接下来，我们将 'Date' 列设置为索引：

```python
data.set_index('Date', inplace=True)
```

现在让我们结合数据集探索时区处理：

默认情况下，datetime 索引是无时区感知的。我们可以使用 `tz_localize()` 方法将其本地化到特定时区。例如，让我们将索引本地化到 'US/Eastern' 时区：

```python
data_tz = data.tz_localize('US/Eastern')
```

#### 将 Datetime 索引转换为不同时区

一旦 datetime 索引被本地化，我们就可以使用 `tz_convert()` 方法将其转换为不同的时区。例如，让我们将 'US/Eastern' 时区的索引转换为 'Europe/London' 时区：

```python
data_tz_london = data_tz.tz_convert('Europe/London')
```

#### 使用有时区感知的数据执行基于时间的计算

有时区感知的数据可用于各种基于时间的计算，例如计算两个日期之间的时间差。例如，让我们计算数据集中最大日期和最小日期之间的时间差，同时考虑 'Europe/London' 时区：

```python
time_difference_london = data_tz_london.index.max() - data_tz_london.index.min()
print(time_difference_london)
```

通过结合 `Customer_Churn_Modelling.csv` 数据集执行时区处理，您可以确保分析考虑了时区差异，从而提供关于客户行为和流失的准确洞察。当处理来自不同地区的数据或应对夏令时变更时，这一点尤为重要，因为时区处理可以帮助您避免分析中的错误和不一致。



### 周期与周期运算

在 Pandas 库中，处理时间相关数据涉及使用 Periods（周期）和 Period Arithmetic（周期运算），这与处理特定时间点不同。Periods 表示一个时间跨度，例如一天、一个月或一年，从而允许对基于时间的数据进行更灵活的分析。通过 Period Arithmetic，可以在这些时间跨度之间执行计算和比较，使用户能够更高效地分析随时间变化的趋势和模式。例如，可以执行加减周期、确定两个周期之间的差异或比较两个周期是否重叠等算术运算。通过在 Pandas 中利用 Periods 和 Period Arithmetic，分析师可以更好地理解时间数据，并基于长期趋势和模式做出更明智的决策。

首先，让我们加载数据集并将 `Date` 列转换为 datetime 类型：

```python
import pandas as pd
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")
data['Date'] = pd.to_datetime(data['Date'])
```

接下来，我们将 `Date` 列设置为索引：

```python
data.set_index('Date', inplace=True)
```

现在让我们使用数据集探索 Periods 和 Period Arithmetic：

#### 创建 Period 对象

Period 对象表示一个时间跨度。让我们创建一个表示 2020 年 1 月的 Period 对象：

```python
january_2020 = pd.Period('2020-01', freq='M')
```

#### 执行周期运算

你可以使用 Period 对象执行算术运算，例如加减时间跨度。例如，让我们给 `january_2020` Period 对象加一个月：

```python
february_2020 = january_2020 + 1
```

#### 将 Datetime 索引转换为 PeriodIndex

要在 DataFrame 中使用周期，可以将 datetime 索引转换为 PeriodIndex。例如，让我们将每日 datetime 索引转换为月度 PeriodIndex：

```python
data_period = data.to_period(freq='M')
```

#### 使用 PeriodIndex 执行计算

你可以使用 PeriodIndex 执行各种计算。例如，让我们计算数据集中唯一月份的数量：

```python
unique_months = len(data_period.index.unique())
```

#### 按周期分组数据

PeriodIndex 可用于根据特定时间跨度对数据进行分组。例如，让我们按月分组数据并计算 `CreditScore` 列的平均值：

```python
monthly_data_mean = data_period.groupby(level=0)['CreditScore'].mean()
```

通过在 `Customer_Churn_Modelling.csv` 数据集中使用 Periods 和 Period Arithmetic，你可以按时间跨度而非特定时间点来分析基于时间的数据。这使你能够执行更高级的时间序列分析，并基于各种时间跨度（如月、季度或年）深入了解客户行为和流失情况。

### 高级时间序列技术

Pandas 提供了多种高级时间序列技术，可以帮助你更有效地分析和处理时间序列数据。让我们探索其中一些技术以及如何将它们应用于 `Customer_Churn_Modelling.csv` 数据集。

首先，让我们加载数据集并将 `Date` 列转换为 datetime 类型：

```python
import pandas as pd
data = pd.read_csv("https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv")
data['Date'] = pd.to_datetime(data['Date'])
```

接下来，我们将 `Date` 列设置为索引：

```python
data.set_index('Date', inplace=True)
```

现在，让我们探索一些高级时间序列技术：

#### 滚动窗口

Rolling windows（滚动窗口）可用于在移动的数据点窗口上计算各种统计量，如平均值、中位数或标准差。这对于平滑嘈杂数据或识别数据趋势非常有用。

```python
# Calculate the rolling mean of the 'CreditScore' column with a window size of 7 days
data['CreditScore_rolling_mean'] = data['CreditScore'].rolling(window='7D').mean()
```

#### 指数移动平均

Exponential Moving Average（指数移动平均，EMA）是一种加权移动平均，赋予近期数据点更高的重要性。这比简单移动平均能更有效地识别趋势。

```python
# Calculate the EMA of the 'CreditScore' column with a span of 7 days
data['CreditScore_ema'] = data['CreditScore'].ewm(span=7).mean()
```

#### 时间序列分解

Time Series Decomposition（时间序列分解）涉及将时间序列分解为其组成部分，如趋势、季节性和残差（噪声）。这有助于你更好地理解数据中的潜在模式。

```python
from statsmodels.tsa.seasonal import seasonal_decompose

# Decompose the 'CreditScore' time series data
decomposition = seasonal_decompose(data['CreditScore'], period=30, model='additive')

# Plot the decomposition components
decomposition.plot()
```

#### 时间序列预测

Time Series Forecasting（时间序列预测）涉及基于历史数据预测时间序列的未来值。存在多种预测技术，如自回归（AR）、移动平均（MA）和 ARIMA（自回归积分滑动平均模型）。

```python
from statsmodels.tsa.arima.model import ARIMA

# Fit an ARIMA model to the 'CreditScore' time series data
model = ARIMA(data['CreditScore'], order=(1, 1, 1))
model_fit = model.fit()

# Predict the next 5 days of 'CreditScore' values
predictions = model_fit.forecast(steps=5)
```

通过将这些高级时间序列技术与 `Customer_Churn_Modelling.csv` 数据集结合使用，你可以更深入地洞察客户行为和流失情况，识别趋势和模式，甚至预测未来的客户行为。这些技术可以帮助你基于数据分析做出更明智的决策。




### 摘要

在本章中，我们探讨了时间序列数据的概念，以及 `pandas` 库如何成为分析时间序列数据集的强大工具。我们还研究了 Pandas 2.0 中的 `DateTime` 对象和函数，包括如何使用它们来操作时间序列数据。我们涵盖了时间序列数据操作、频率转换与重采样、时区处理、周期与周期运算，以及高级时间序列技术。

我们首先加载了 `Customer_Churn_Modelling.csv` 数据集，并将 `Date` 列转换为 `datetime` 类型，随后将 `Date` 列设置为索引。然后我们探索了 `pandas` 中时间序列数据分析的不同方面，包括滚动窗口、指数移动平均、时间序列分解和时间序列预测。

我们首先介绍了滚动窗口，以及如何利用它们计算数据点移动窗口上的统计量。该技术可用于平滑嘈杂数据或识别数据中的趋势。我们演示了如何以 7 天的窗口大小计算 `CreditScore` 列的滚动平均值。

接下来，我们探讨了指数移动平均，这是一种加权移动平均，赋予近期数据点更高的重要性。与简单移动平均相比，该技术能更有效地识别趋势。我们展示了如何以 7 天的跨度计算 `CreditScore` 列的 EMA。

然后，我们介绍了时间序列分解，即将时间序列分解为其组成部分，如趋势、季节性和残差（噪声）。该技术有助于您更好地理解数据中的潜在模式。我们演示了如何分解 `CreditScore` 时间序列数据并绘制分解组件。

最后，我们研究了时间序列预测，即基于历史数据预测时间序列的未来值。我们介绍了各种预测技术，如自回归 (AR)、移动平均 (MA) 和 ARIMA (自回归积分滑动平均)。我们演示了如何将 ARIMA 模型拟合到 `CreditScore` 时间序列数据，并预测未来 5 天的 `CreditScore` 值。

通过将这些高级时间序列技术应用于 `Customer_Churn_Modelling.csv` 数据集，您可以更深入地洞察客户行为和流失情况，识别趋势和模式，甚至预测未来的客户行为。这些技术可以帮助您基于数据分析做出更明智的决策。

## 第 6 章：性能优化与扩展

### 内存与计算效率

内存与计算效率是数据分析和处理的关键方面，尤其是在处理大型数据集时。这些概念旨在最小化系统或应用程序消耗的资源，优化性能，并实现更快、更具扩展性的解决方案。理解内存与计算效率的重要性有助于您开发更高效、更健壮的应用程序。

以下是内存与计算效率重要的一些关键原因：

- **资源限制**：计算机拥有有限的资源，如内存 (RAM) 和 CPU 处理能力。高效的内存和计算使用使您能在这些约束内工作，防止系统崩溃或变慢。在处理大型数据集时，这一点尤为重要，因为如果管理不善，大型数据集很容易耗尽所有可用资源。
- **扩展性**：高效的内存和计算管理使您的应用程序能更有效地扩展，从而处理更大的数据集或同时处理更多请求。在大数据时代，这一点尤为重要，因为生成和处理的数据量在持续增加。
- **更快的处理**：优化内存和计算使用可显著加快您的数据处理和分析任务。更快的处理时间能带来更快的洞察和决策，这在许多行业和应用中至关重要。
- **成本节约**：高效利用资源可带来成本节约，特别是在按使用量计费的云计算环境中。通过优化内存和计算，您可以降低基础设施成本，使应用程序更具成本效益。
- **更好的用户体验**：针对内存和计算效率进行优化的应用程序通常性能更好，从而改善用户体验。用户通常对加载更快、响应用户输入更迅速、且能在不崩溃或变慢的情况下处理大量数据的应用程序有更积极的体验。
- **环境影响**：高效计算有助于减少能源消耗，对环境产生积极影响。随着数据处理需求的持续增长，寻找方法以最小化计算任务的能源足迹至关重要。

内存与计算效率在数据分析和处理中发挥着至关重要的作用。通过针对高效的内存和计算使用优化您的应用程序，您可以实现更好的性能、扩展性、成本节约和环境效益，最终获得更健壮、更有效的解决方案。

对于位于以下位置的客户流失建模数据库：[`github.com/kittenpub/database-repository/blob/main/Customer_Churn_Modelling.csv`](https://github.com/kittenpub/database-repository/blob/main/Customer_Churn_Modelling.csv)，内存与计算效率可通过以下方式应用：

#### 选择合适的数据类型

为 `DataFrame` 中的每一列选择合适的数据类型。`pandas` 会自动检测数据类型，但有时手动指定会更好，尤其是对于大型数据集。例如，您可以对唯一值数量有限的列使用 `category` 数据类型。

```python
import pandas as pd

dtypes = {'Geography': 'category', 'Gender': 'category'}
df = pd.read_csv('Customer_Churn_Modelling.csv', dtype=dtypes)
```

#### 分块加载

如果数据集非常大，请分块加载，而不是一次性全部读取。这有助于管理内存使用，并以更小、更易管理的片段执行数据操作。

```python
chunksize = 1000
chunks = []

for chunk in pd.read_csv('Customer_Churn_Modelling.csv', chunksize=chunksize):
    # 对数据块执行任何数据处理或筛选
    chunks.append(chunk)

df = pd.concat(chunks, axis=0)
```

#### 使用内置优化函数

`pandas` 提供了多种针对性能优化的向量化函数和方法。请使用这些函数，而非自定义或低效的替代方案。

#### 并行处理

如果您拥有多核处理器，可以使用并行处理来加速大型数据集上的计算。这可以通过 `Dask` 等库，或使用 `multiprocessing` 模块并行化代码来实现。

#### 使用原地操作

尽可能使用原地操作，以避免创建不必要的数据副本，从而节省额外的内存消耗。

```python
df.drop(columns=['Unwanted_Column'], inplace=True)
```

通过应用这些内存与计算效率技术，您可以确保在给定数据集上的数据分析任务更加高效，消耗更少资源，从而更轻松地处理大型数据集并执行复杂操作。




### 利用 Dask 进行并行和分布式计算

Dask 是一个功能强大的库，它在 Python 中实现了并行和分布式计算，使得处理可能无法放入内存的大型数据集变得更加容易。Dask 通过提供常见 Pandas 数据结构的并行化版本（例如 `Dask DataFrame`，它是由较小的 Pandas DataFrame 组成的大型并行 DataFrame）扩展了 Pandas 的功能。下文演示了如何使用 Dask 配合 Pandas 执行并行和分布式计算：

#### 安装 Dask

首先，你需要安装 Dask。你可以使用 pip 或 conda 来完成：

```
pip install dask[complete]
```

#### 导入 Dask

安装 Dask 后，你可以将其导入到你的 Python 脚本或笔记本中：

```
import dask.dataframe as dd
```

#### 读取数据

使用 Dask 而非 Pandas 读取你的数据集。Dask 提供了与 Pandas 类似的数据读取函数，例如 `read_csv`。通过使用 Dask 读取数据，你可以高效地处理超内存数据集：

```
ddf = dd.read_csv('large_dataset.csv')
```

#### 操作数据

使用 Dask 的 API 执行数据操作任务，其用法与 Pandas 相似。Dask 会自动并行化这些操作：

```
##### 筛选行
filtered_ddf = ddf[ddf['column_name'] > value]

##### 分组与聚合
grouped_ddf = ddf.groupby('group_column').agg({'value_column': 'mean'})
```

#### 计算结果

由于 Dask 操作默认是惰性的，你需要调用 `compute()` 方法来执行操作并将结果作为 Pandas DataFrame 返回：

```
result_df = grouped_ddf.compute()
```

#### 分布式计算

要使用 Dask 进行分布式计算，你可以使用 Dask 的分布式调度器设置一个 Dask 集群。首先，安装 `dask.distributed` 库，然后创建一个 Dask 客户端：

```
from dask.distributed import Client
client = Client()  # 这将默认创建一个本地集群
```

创建 Dask 客户端后，你使用 Dask 执行的任何操作都将自动分发到集群中可用的工作节点上。

总之，Dask 是一个强大的库，可以帮助你并行化和分发 Pandas 计算。通过使用与 Pandas 相似的 Dask API，你可以高效地处理大型数据集，并更快速、以更少的资源执行复杂的数据分析任务。

### 高效查询和筛选数据

要在 `Customer_Churn_Modelling` 数据库上高效地执行数据查询和筛选，你可以结合使用 Pandas 和 Dask 以提高内存和计算效率。下文演示了如何有效地筛选和查询数据的示例：

首先，你需要导入必要的库并读取数据集：

```
import pandas as pd
import dask.dataframe as dd

# 使用 Dask 读取数据集
ddf = dd.read_csv('https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv')
```

现在，假设你想根据特定标准筛选数据，例如信用分高于 700 且为活跃会员的客户：

```
# 根据条件筛选数据
filtered_ddf = ddf[(ddf['CreditScore'] > 700) & (ddf['IsActiveMember'] == 1)]
```

接下来，你可能想查询数据以找出每个唯一地区的平均余额：

```
# 按地区分组并计算平均余额
average_balance_by_geography = filtered_ddf.groupby('Geography')['Balance'].mean()
```

由于 Dask 操作默认是惰性的，你需要调用 `compute()` 方法来执行操作并将结果作为 Pandas DataFrame 获取：

```
result_df = average_balance_by_geography.compute()
```

现在，你得到了一个基于筛选数据的、包含每个唯一地区平均余额的 Pandas DataFrame。通过使用 Dask 执行这些筛选和查询任务，你可以高效地处理大型数据集并更快地执行复杂操作。此外，你还可以通过使用合适的数据类型、分块加载数据以及并行化计算（如前一节所述）来进一步优化性能。

### 向量化操作与性能

向量化操作是指对整个数组或数据结构执行操作，而不是在循环中对单个元素进行操作。在 Pandas 的语境下，向量化操作利用 NumPy（一个提供高效数组操作的底层库）应用于 Series 和 DataFrame。这些操作通常比使用传统循环更快，因为它们经过优化并在编译代码中执行。

向量化操作的优势包括：

- **性能提升**：向量化操作通常比循环快，因为它们利用了低层优化并消除了 Python 循环的开销。
- **更好的可读性**：向量化代码通常比等效的基于循环的代码更简洁、更易读。
- **更易于代码维护**：由于向量化代码更简洁，它通常更易于维护，且不易出错。

#### 执行向量化操作

下文演示了如何在给定的 `Customer_Churn_Modelling` 数据库上执行向量化操作：

首先，使用 Pandas 读取数据集：

```
import pandas as pd
url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)
```

假设你想计算每个客户的余额与预估薪资的比率。你可以通过将 `Balance` 列除以 `EstimatedSalary` 列来执行向量化操作：

```
df['BalanceToSalaryRatio'] = df['Balance'] / df['EstimatedSalary']
```

在这里，除法操作被逐元素地应用于 `Balance` 和 `EstimatedSalary` 列中对应的每个元素，从而在 DataFrame 中创建了一个新的 `BalanceToSalaryRatio` 列。

另一个例子是以向量化方式对列应用函数。假设你想根据年龄对客户进行分类：30 岁以下为“Young”（年轻），30 到 60 岁之间为“Adult”（成年），60 岁以上为“Senior”（老年）。你可以使用 `pd.cut()` 函数来执行此分类：

```
age_bins = [0, 30, 60, float('inf')]
age_labels = ['Young', 'Adult', 'Senior']
df['AgeCategory'] = pd.cut(df['Age'], bins=age_bins, labels=age_labels)
```

在这种情况下，`pd.cut()` 函数被应用于 `Age` 列，创建了一个带有适当年龄类别的新 `AgeCategory` 列。

通过在数据处理和分析任务中使用向量化操作，你可以提高代码的性能、可读性和可维护性。重要的是要尽可能利用这些操作，以充分发挥 Pandas 和 NumPy 提供的功能。





### 使用 Cython 和 Numba 提升速度

在数据分析操作中，速度问题可能源于多个因素，包括：

- **对大型数据集进行循环**：由于 Python 的解释性质以及循环带来的开销，使用 Python 循环迭代大型数据集可能会很慢。
- **低效的实现**：对大型数据集上的操作使用非向量化或非优化的实现，会导致处理时间变慢。
- **复杂的计算**：在大型数据集上执行复杂计算可能计算成本高昂且缓慢，特别是当这些计算难以轻松并行化或优化时。

`Cython` 和 `Numba` 是在 Python 中加速数据分析操作的两种流行解决方案：

#### Cython

`Cython` 是 Python 的超集，它允许你使用类 Python 的语法为 Python 编写 C 扩展。它让你可以对变量和函数进行静态类型声明，编译为 C 代码后可显著提升性能。当你有一段性能关键的代码，且能从 C 语言的速度中受益时，`Cython` 尤其有用。

#### Numba

`Numba` 是 Python 的即时（JIT）编译器，它能在运行时将 Python 和 NumPy 代码的一个子集翻译成机器码。`Numba` 允许你通过使用装饰器指定函数应由 `Numba` 编译，从而在 Python 中编写高性能函数。当你有计算成本高昂且难以使用 NumPy 或 Pandas 轻松向量化的函数时，`Numba` 尤其有帮助。

#### 安装 Cython 和 Numba

要安装 `Cython` 和 `Numba`，请使用 `pip`：

```
pip install cython numba
```

现在，让我们通过一个简单的示例来看看如何使用 `Cython` 和 `Numba` 来提升性能。请看下面这个计算一定范围内数字平方和的 Python 函数：

```
def sum_of_squares(n):
    total = 0
    for i in range(n):
        total += i ** 2
    return total
```

#### 使用 Cython 加速函数

首先，你需要在 Jupyter Notebook 中加载 `Cython` 扩展：

```
%load_ext cython
```

接下来，通过添加 `%%cython` 魔法命令并指定变量类型，使用 `Cython` 重写该函数：

```
%%cython
def cython_sum_of_squares(int n):
    cdef int total = 0
    cdef int i
    for i in range(n):
        total += i ** 2
    return total
```

#### 使用 Numba 加速函数

导入 `Numba` 并使用 `@jit` 装饰器指示该函数应由 `Numba` 编译：

```
from numba import jit

@jit(nopython=True)
def numba_sum_of_squares(n):
    total = 0
    for i in range(n):
        total += i ** 2
    return total
```

#### 性能对比

现在，你可以对比原始函数、`Cython` 优化版本和 `Numba` 优化版本的性能：

```
import timeit

n = 10_000
print("Python function:")
%timeit sum_of_squares(n)
print("\nCython function:")
%timeit cython_sum_of_squares(n)
print("\nNumba function:")
%timeit numba_sum_of_squares(n)
```

你应该会看到，`Cython` 和 `Numba` 的实现都比原始 Python 函数快得多。

总之，`Cython` 和 `Numba` 是优化 Python 数据分析操作性能的强大工具。通过使用这些工具，你可以显著加快代码运行速度，并提高数据处理任务的效率。根据你的具体需求、代码性质以及所需的优化类型，在 `Cython` 和 `Numba` 之间进行选择。





### 调试和分析性能问题

以下是使用 Pandas 时常见性能问题及其解决方案的详细阐述：

#### 内存使用

##### 分块加载数据

从文件或数据库读取数据时，可以使用 `chunksize` 参数以较小的块来读取数据。这有助于减少内存使用，并允许你增量处理数据。

```python
import pandas as pd

chunksize = 10 ** 5  # 根据系统内存调整块大小

for chunk in pd.read_csv("large_dataset.csv", chunksize=chunksize):
    # 对每个块执行操作
```

##### 删除不必要的列或行

最佳实践是尽早删除分析中不需要的任何列或行。这能减少内存使用并加快后续操作。

```python
#### 删除不必要的列
df = df.drop(['unnecessary_column1', 'unnecessary_column2'], axis=1)

###### 基于条件删除不必要的行
df = df[df['useful_column'] > threshold]
```

##### 使用合适的数据类型

读取数据时，Pandas 会自动推断每列的数据类型，这有时会导致内存使用效率低下。你可以通过指定正确的数据类型或将列转换为更高效的类型来减少内存使用。

```python
###### 读取数据时指定数据类型
dtypes = {'column1': 'int32', 'column2': 'category'}
df = pd.read_csv('dataset.csv', dtype=dtypes)

###### 将现有列转换为更高效的数据类型
df['column1'] = df['column1'].astype('int32')
df['column2'] = df['column2'].astype('category')
```

#### 非向量化操作

##### 向量化的 Pandas 或 NumPy 操作

只要可能，请使用 Pandas 和 NumPy 提供的向量化操作一次性对整列或 DataFrame 执行计算。这些操作经过优化，比遍历行要快得多。

```python
# 向量化加法示例
df['sum_column'] = df['column1'] + df['column2']
```

##### 使用 `apply()`

如果某操作难以轻松向量化，可以使用 `apply()` 方法沿 DataFrame 的特定轴（行或列）应用自定义函数。

```python
def custom_function(row):
    # 对行元素执行计算
    return result

df['new_column'] = df.apply(custom_function, axis=1)
```

##### 使用 Cython 或 Numba

如果非向量化操作仍存在性能问题，请考虑使用 Cython 或 Numba 优化自定义函数。这两种工具均可通过将 Python 代码编译为本机机器码或 C 代码，提供显著的速度提升。

#### 低效的操作链

##### 使用 `inplace` 参数

许多 Pandas 方法提供 `inplace` 参数，允许你就地修改 DataFrame 而无需创建新对象。

```python
df.drop(['column1', 'column2'], axis=1, inplace=True)
```

##### 使用 `query()` 或 `eval()`

Pandas 提供 `query()` 和 `eval()` 方法，允许你在单个步骤中执行多个操作，减少创建的中间对象数量。这些方法比链式操作更快且更节省内存。

```python
# 使用 query() 在一步中筛选并计算新列
df = df.query('column1 > 100 and column2 < 200')
df['new_column'] = df['column1'] * df['column2']

# 使用 eval() 在一步中执行多个计算
df['new_column'] = df.eval('column1 * column2')
```

#### 缓慢的 Groupby 和聚合操作

##### 使用 `sort=False`

默认情况下，执行 `groupby()` 操作时 Pandas 会对分组进行排序，这会拖慢过程。你可以通过设置 `sort=False` 来禁用排序。

```python
grouped = df.groupby('column1', sort=False)
```

##### 使用 `agg()` 方法

你可以使用 `agg()` 方法在一步中执行多个聚合，而不必链接多个聚合操作。

```python
result = grouped.agg({
    'column2': ['sum', 'mean'],
    'column3': ['max', 'min']
})
```

#### 缓慢的读取和写入操作

##### 使用 `compression`

读取或写入数据时，可以使用 `compression` 参数指定压缩算法，以减小文件大小和 I/O 时间。

```python
df = pd.read_csv('compressed_data.csv.gz', compression='gzip')
df.to_csv('compressed_output.csv.gz', compression='gzip')
```

##### 二进制格式

除了使用 CSV 等基于文本的格式，还可以考虑使用 Parquet 等二进制格式来读写大型 DataFrame。二进制格式在存储和 I/O 性能方面更高效。

```python
df = pd.read_parquet('data.parquet')
df.to_parquet('output.parquet')
```

通过采取这些切实可行的步骤，你可以解决 Pandas 中的常见性能问题，并针对大型数据集或复杂操作优化数据分析任务。使用 Pandas 时请牢记这些技巧，以确保代码高效且性能良好。

### 总结

在本章中，我们讨论了 Pandas 2.0 中的内存和计算效率，重点关注了针对数据分析任务优化性能的重要性。我们还探讨了 Dask 作为 Pandas 并行和分布式计算的解决方案，以及如何在给定的 `customer_chrn_modelling` 数据库上高效执行查询和筛选。接下来，我们了解了向量化操作，这对优化 Pandas 性能至关重要。这些操作允许你在整个数组或 DataFrame 上执行逐元素计算，而无需显式循环，从而产生更快、更高效的代码。我们还讨论了将这些操作应用到给定数据库的方法。

随后，我们探讨了数据分析过程中可能出现的速度问题，以及 Cython 和 Numba 如何帮助解决这些问题。Cython 和 Numba 均可通过将 Python 代码编译为本机机器码或 C 代码来加速性能。我们演示了安装和配置 Cython 与 Numba 的过程，并展示了如何用它们优化一个简单示例。

最后，我们讨论了使用 Pandas 时可能出现的常见性能问题及其切实可行的解决方法。这些问题包括内存使用、非向量化操作、低效的操作链、缓慢的 groupby 和聚合操作、低效的合并或连接操作，以及缓慢的读取和写入操作。通过采用分块加载数据、使用合适的数据类型、向量化操作、使用 `inplace` 参数、优化 `merge()` 方法、使用 Dask 以及选择高效文件格式等技术，你可以显著提高使用 Pandas 进行数据分析任务的效率和速度。

## 第 7 章：Pandas 2.0 机器学习





### 机器学习与 Pandas 简介

机器学习（ML）是人工智能（AI）的一个子领域，专注于开发算法和模型，使计算机能够基于输入数据进行学习并做出预测或决策，而无需显式编程。学习过程通常涉及使用训练数据集来“教导”算法如何识别数据中的模式、关系或结构，然后利用所学知识对新的、未见过的数据进行预测或决策。

#### 机器学习的类型

机器学习主要有三种类型：

##### 监督学习
算法获得带标签的训练数据，其中包含输入特征和相应的输出标签。目标是学习从输入特征到输出标签的映射，以便算法能够预测新输入数据的标签。监督学习任务的示例包括分类（例如，识别垃圾邮件）和回归（例如，预测房价）。

##### 无监督学习
算法获得无标签的训练数据，其中仅包含输入特征，没有相应的输出标签。目标是在没有任何关于输出的先验知识的情况下，发现数据中的模式、结构或关系。无监督学习任务的示例包括聚类（例如，根据购买行为对客户进行分组）和降维（例如，在保留数据底层结构的同时减少特征数量）。

##### 强化学习
算法通过与环境交互并以奖励或惩罚的形式接收反馈来学习。目标是学习一套最优策略以做出决策，从而使累积奖励随时间最大化。强化学习任务的示例包括游戏对弈（例如，训练智能体下棋）和机器人技术（例如，训练机器人走迷宫）。

#### Pandas 在机器学习中的应用

`Pandas` 是 Python 中一个流行的数据操作和分析库，它提供了处理结构化数据（如表格或时间序列）所需的数据结构和函数。虽然 `Pandas` 本身不是一个机器学习库，但它通过提供数据预处理、特征工程和数据分析的必要工具，在机器学习流程中发挥着重要作用。

##### Pandas 在 ML 中的角色

以下演示了 `Pandas` 如何为机器学习做出贡献：

- **数据预处理**：清洗和准备数据是机器学习流程中的关键步骤。使用 `Pandas`，您可以处理缺失值、删除不必要的列、根据条件筛选数据等。
- **特征工程**：创建新特征或转换现有特征有助于提高机器学习模型的性能。`Pandas` 提供了用于执行缩放、归一化、分箱和编码分类变量等操作的函数。
- **数据分析**：探索性数据分析（EDA）是理解数据并识别潜在问题或模式的关键步骤，这些信息可为机器学习算法的选择提供依据。`Pandas` 提供了描述性统计、数据可视化和相关性分析的工具。
- **数据分割**：在训练机器学习模型之前，您需要将数据分割为训练集和测试集。`Pandas` 使创建数据的随机分割或分层分割变得容易。

虽然 `Pandas` 本身不是机器学习库，但它通过提供数据操作和分析的必要工具，在机器学习流程中发挥着至关重要的作用。一旦您使用 `Pandas` 准备好数据，就可以使用 `Scikit-learn`、`TensorFlow` 或 `PyTorch` 等机器学习库来训练和评估您的模型。

### 机器学习的数据预处理

数据预处理是机器学习流程中的关键步骤，因为它涉及在将数据输入机器学习模型之前对其进行准备和清洗。我们将演示如何使用 `Pandas` 执行数据预处理。

首先，假设您已将数据集加载到 `Pandas` `DataFrame` 中：

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)
```

现在，让我们执行一些常见的数据预处理任务：

#### 检查数据

在预处理数据之前，了解数据集、其特征和潜在问题非常重要。

```python
# 显示 DataFrame 的前几行
print(df.head())

# 获取数值列的汇总统计信息
print(df.describe())

# 检查每列的数据类型
print(df.dtypes)

# 检查缺失值
print(df.isnull().sum())
```

##### 处理缺失值

根据缺失值的性质和数据集的情况，您可以选择用默认值填充、插值，或删除包含缺失值的行或列。

```python
# 用默认值填充缺失值（例如，该列的平均值）
df['column_with_missing_values'] = df['column_with_missing_values'].fillna(df['column_with_missing_values'].mean())

###### 插值填充缺失值
df.interpolate(method='linear', inplace=True)

# 删除包含缺失值的行
df.dropna(inplace=True)

###### 删除缺失值比例高的列
df.drop('column_with_high_missing_percentage', axis=1, inplace=True)
```

#### 将分类数据转换为数值

机器学习算法通常需要数值输入。因此，您需要使用独热编码或标签编码等技术将分类特征转换为数值。

```python
###### 独热编码
df = pd.get_dummies(df, columns=['categorical_column'])

###### 标签编码
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()
df['categorical_column'] = le.fit_transform(df['categorical_column'])
```

#### 删除不必要的列

某些列可能对您的分析没有用处，或者可能与其他特征高度相关。在这种情况下，您可以删除这些列以简化数据集。

```python
df.drop(['unnecessary_column1', 'unnecessary_column2'], axis=1, inplace=True)
```

##### 特征缩放

许多机器学习算法对输入特征的尺度敏感。为了确保所有特征具有相同的尺度，您可以对数据进行归一化或标准化。

```python
from sklearn.preprocessing import MinMaxScaler, StandardScaler

##### 归一化（最小-最大缩放）
min_max_scaler = MinMaxScaler()
df[['numerical_column1', 'numerical_column2']] = min_max_scaler.fit_transform(df[['numerical_column1', 'numerical_column2']])

##### 标准化（Z-score 缩放）
standard_scaler = StandardScaler()
df[['numerical_column1', 'numerical_column2']] = standard_scaler.fit_transform(df[['numerical_column1', 'numerical_column2']])
```

完成这些预处理步骤后，您的数据集应该已准备好用于机器学习模型。请记住，您选择应用的具体预处理步骤可能会因数据集和您试图解决的问题而异。




### 使用 Pandas 2.0 进行特征工程

特征工程是指在数据集中创建新特征或转换现有特征，以提高机器学习模型的性能和预测能力的过程。该过程涉及利用领域知识、统计技术和数据分析，从原始数据中提取更多信息，并为机器学习算法提供有意义的输入。有效的特征工程可带来更好的模型性能、降低复杂度并提高可解释性。

#### 特征工程的优势

- **提升模型性能**：精心设计的特征能够捕捉数据中的重要关系和模式，使机器学习模型更容易学习并泛化到新的、未见过的数据。
- **降低复杂度**：通过创建能更好地代表数据底层结构的特征，通常可以降低机器学习模型的复杂度，从而缩短训练时间并提升性能。
- **可解释性**：创建有意义的特征可以使最终模型更具可解释性，这在理解模型决策过程至关重要的特定应用中非常重要。
- **处理分类数据**：机器学习模型通常需要数值输入。特征工程技术（如独热编码或标签编码）可用于将分类数据转换为数值。
- **处理缺失值**：特征工程有助于处理缺失值，既可以通过创建捕捉缺失模式的新特征，也可以基于特征间的关系插补缺失值。
- **降维**：主成分分析（PCA）或其他特征提取方法等技术有助于减少数据集中的特征数量，缓解维度灾难并提高模型性能。

#### Pandas 在特征工程中的作用

Pandas 是一个功能强大的数据操作库，提供了各种函数和工具，使特征工程任务更易于执行。以下是特征工程中的一些关键函数及其用例：

##### 创建新特征

Pandas 允许您通过对现有特征应用数学运算、组合现有特征或使用自定义函数来创建新特征。

```python
###### 通过对现有特征应用数学运算来创建新特征
df['new_feature'] = df['existing_feature'] ** 2

###### 通过组合两个或多个现有特征来创建新特征
df['new_feature'] = df['feature1'] * df['feature2']

###### 使用自定义函数创建新特征
def custom_function(x):
    return x * 2

df['new_feature'] = df['existing_feature'].apply(custom_function)
```

##### 编码分类变量

Pandas 提供了 `get_dummies()` 和 `factorize()` 等函数，使用独热编码或标签编码将分类数据转换为数值。

```python
###### 独热编码
df = pd.get_dummies(df, columns=['categorical_column'])

###### 标签编码
df['categorical_column'], _ = pd.factorize(df['categorical_column'])
```

##### 分箱与离散化

您可以使用 Pandas 的 `cut()` 和 `qcut()` 等函数将连续变量离散化为分箱或类别，这有助于捕捉非线性关系并减少异常值的影响。

```python
###### 使用等宽分箱
df['binned_column'] = pd.cut(df['continuous_column'], bins=10)

###### 使用等频分箱
df['binned_column'] = pd.qcut(df['continuous_column'], q=10)
```

##### 处理缺失值

Pandas 提供了 `fillna()`、`interpolate()` 和 `dropna()` 等函数，通过填充默认值、插值或删除含缺失值的行或列等多种技术来处理数据集中的缺失值。

```python
###### 用默认值填充缺失值（例如列的平均值）
df['column_with_missing_values'] = df['column_with_missing_values'].fillna(df['column_with_missing_values'].mean())

###### 插值填充缺失值
df.interpolate(method='linear', inplace=True)

###### 删除含缺失值的行
df.dropna(inplace=True)

###### 删除缺失值比例高的列
df.drop('column_with_high_missing_percentage', axis=1, inplace=True)
```

##### 特征缩放

Pandas 可结合 Scikit-learn 的预处理工具对特征进行缩放或归一化，确保所有特征具有相同的尺度，防止因输入特征尺度不同而导致的问题。

```python
from sklearn.preprocessing import MinMaxScaler, StandardScaler

##### 归一化（最小-最大缩放）
min_max_scaler = MinMaxScaler()
df[['numerical_column1', 'numerical_column2']] = min_max_scaler.fit_transform(df[['numerical_column1', 'numerical_column2']])

##### 标准化（Z-score 缩放）
standard_scaler = StandardScaler()
df[['numerical_column1', 'numerical_column2']] = standard_scaler.fit_transform(df[['numerical_column1', 'numerical_column2']])
```

##### 特征选择

Pandas 可用于计算相关系数或其他指标，以帮助识别并移除高度相关或无关的特征，从而提高模型性能并减少过拟合。

```python
###### 计算相关性矩阵
corr_matrix = df.corr()

###### 识别高度相关的特征
highly_correlated_features = [column for column in corr_matrix.columns if any(abs(corr_matrix[column]) > 0.9)]

###### 删除高度相关的特征
df.drop(highly_correlated_features, axis=1, inplace=True)
```

总之，Pandas 是机器学习特征工程中必不可少的工具，它提供了广泛的函数和工具来创建、转换和操作特征。通过有效使用 Pandas，您可以从数据中提取更有意义的信息，并提升机器学习模型的性能。





### 处理不平衡数据

不平衡数据是指目标变量中各类别的分布不均等或严重偏斜的情况。换句话说，某一类别的样本数量显著多于其他类别。不平衡数据可能导致机器学习模型产生偏差，因为模型倾向于偏向多数类，导致在少数类上的表现不佳。

要在 `customer_chrn_modelling` 数据库中处理不平衡数据，请遵循以下步骤：

#### 加载数据集并探索目标变量

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)

# 假设 'target_column' 是目标变量的名称
print(df['target_column'].value_counts())
```

#### 识别不平衡数据

检查目标变量中各类别的分布。如果各类别的样本数量存在显著差异，则数据不平衡。

有多种技术可用于处理不平衡数据。一些常用方法包括：

- **重采样数据**：
  - **上采样少数类**：通过随机复制少数类样本来增加其数量。
  - **下采样多数类**：通过随机移除多数类样本来减少其数量。
- **使用合成数据生成方法**，如合成少数类过采样技术（`SMOTE`）或自适应合成采样（`ADASYN`），为少数类创建新的合成样本。
- **使用代价敏感学习**，为多数类和少数类分配不同的误分类代价，实际上是对模型误分类少数类施加更大的惩罚。
- **集成方法**，如 Bagging 和 Boosting，也有助于提升在不平衡数据集上的性能。

以下示例演示了如何应用其中一些技术：

```python
##### 导入必要的库
from sklearn.utils import resample
from imblearn.over_sampling import SMOTE

##### 分离多数类和少数类
df_majority = df[df['target_column'] == 0]
df_minority = df[df['target_column'] == 1]

##### 上采样少数类
df_minority_upsampled = resample(df_minority, replace=True, n_samples=len(df_majority), random_state=42)
df_upsampled = pd.concat([df_majority, df_minority_upsampled])

##### 下采样多数类
df_majority_downsampled = resample(df_majority, replace=False, n_samples=len(df_minority), random_state=42)
df_downsampled = pd.concat([df_majority_downsampled, df_minority])

##### 使用 SMOTE 为少数类生成合成样本
X = df.drop('target_column', axis=1)
y = df['target_column']
smote = SMOTE(random_state=42)
X_smote, y_smote = smote.fit_resample(X, y)
```

应用一种或多种这些技术后，您将获得一个更平衡的数据集，这有助于提高机器学习模型在少数类上的性能。请务必尝试不同的方法，并使用精确率、召回率、F1 分数或 ROC 曲线下面积等适当指标评估模型性能，因为在不平衡数据的情况下，准确率可能会产生误导。

### 特征缩放与归一化

特征缩放与归一化是用于标准化数据集中独立特征或变量范围的预处理技术。这些技术至关重要，因为许多机器学习算法对输入特征的尺度敏感。不同特征可能具有不同的单位和尺度，如果没有适当的缩放，算法可能会赋予数值幅度较大的特征更高的重要性，从而导致模型性能产生偏差或不佳。

最常用的两种特征缩放方法是归一化（最小-最大缩放）和标准化（Z-score 缩放）。

##### 归一化（最小-最大缩放）

归一化将特征缩放到 `[0, 1]` 的范围内。其计算公式如下：

`X_normalized = (X - X_min) / (X_max - X_min)`

其中 `X` 为原始特征值，`X_min` 和 `X_max` 分别为该特征的最小值和最大值。

##### 标准化（Z-score 缩放）

标准化将特征缩放为均值为 0、标准差为 1 的分布。其计算公式如下：

`X_standardized = (X - mean(X)) / std(X)`

其中 `X` 为原始特征值，`mean(X)` 为该特征的均值，`std(X)` 为该特征的标准差。

#### 实现特征缩放与归一化

要使用 Python 实现特征缩放与归一化，可以使用 Scikit-learn 库的预处理工具。

```python
import pandas as pd
from sklearn.preprocessing import MinMaxScaler, StandardScaler

##### 加载数据集
url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)

##### 列出要缩放的列
columns_to_scale = ['numerical_column1', 'numerical_column2']

##### 归一化（最小-最大缩放）
min_max_scaler = MinMaxScaler()
df[columns_to_scale] = min_max_scaler.fit_transform(df[columns_to_scale])

##### 标准化（Z-score 缩放）
standard_scaler = StandardScaler()
df[columns_to_scale] = standard_scaler.fit_transform(df[columns_to_scale])
```

请记住，对训练集和测试集应用相同的缩放方法以确保数据一致性。但请务必**仅在训练数据上拟合缩放器**，并使用同一个缩放器转换测试数据。这可以避免测试集数据泄露到训练集中。





### 训练-测试集划分与交叉验证

训练-测试集划分和交叉验证是用于评估机器学习模型性能并确保其能很好地泛化到未见数据的技术。

#### 训练-测试集划分

在训练-测试集划分中，数据集被分为两个独立的集合：训练集和测试集。训练集用于训练机器学习模型，而测试集用于评估模型的性能。训练-测试集划分的目的是提供模型在未见数据上表现如何的估计，并检查过拟合情况。

要使用 Scikit-learn 实现训练-测试集划分，请遵循以下步骤：

```python
import pandas as pd
from sklearn.model_selection import train_test_split

##### 加载数据集
url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)

##### 分离特征和目标变量
X = df.drop('target_column', axis=1)
y = df['target_column']

##### 执行训练-测试集划分
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

#### 交叉验证

交叉验证是一种评估模型性能更稳健的技术。它涉及将数据集划分为 'k' 个大小相等的折叠（fold），其中 'k' 是用户定义的参数。在每次迭代中，模型在 'k-1' 个折叠上训练，并在剩余的一个折叠上测试。此过程重复 'k' 次，每个折叠恰好被用作测试集一次。最终的性能指标计算为所有 'k' 次迭代的性能指标的平均值。交叉验证有助于降低过拟合的风险，并提供模型性能的更准确估计。

要使用 Scikit-learn 实现交叉验证，请遵循以下步骤：

```python
import pandas as pd
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LogisticRegression

##### 加载数据集
url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)

##### 分离特征和目标变量
X = df.drop('target_column', axis=1)
y = df['target_column']

##### 创建模型实例
model = LogisticRegression()

##### 执行 k=5 折的交叉验证
scores = cross_val_score(model, X, y, cv=5)

##### 计算平均性能指标
mean_score = scores.mean()
```

请记住，这两种技术应结合使用，以对模型进行全面评估。训练-测试集划分可用于模型选择和超参数调优，而交叉验证则提供模型在未见数据上性能的更可靠估计。

### 与 Scikit-learn、TensorFlow 和 PyTorch 的集成

将 Pandas 与 Scikit-learn、TensorFlow 和 PyTorch 集成，在使用这些机器学习库时，可实现无缝的数据处理和预处理。

#### Pandas 与 Scikit-learn 的集成

Scikit-learn 是 Python 中广泛使用的机器学习库。它与 Pandas 的集成非常无缝，因为 Scikit-learn 可以直接处理 Pandas DataFrame。下面给出了一个示例：

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression

##### 加载数据集
url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)

##### 分离特征和目标变量
X = df.drop('target_column', axis=1)
y = df['target_column']

##### 执行训练-测试集划分
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 创建模型实例并拟合模型
model = LogisticRegression()
model.fit(X_train, y_train)

# 评估模型
accuracy = model.score(X_test, y_test)
```

#### Pandas 与 TensorFlow 的集成

TensorFlow 是一个用于机器学习和深度学习任务的开源库。要将 Pandas DataFrame 与 TensorFlow 配合使用，需要将它们转换为 TensorFlow Dataset 或 NumPy 数组。下面演示了一个使用 TensorFlow Keras API 的示例：

```python
import pandas as pd
import tensorflow as tf
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

##### 加载数据集
url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)

##### 分离特征和目标变量
X = df.drop('target_column', axis=1).values
y = df['target_column'].values

##### 执行训练-测试集划分
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 缩放特征
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

# 使用 Keras 构建并训练模型
model = tf.keras.Sequential([
    tf.keras.layers.Dense(16, activation='relu', input_shape=(X_train.shape[1],)),
    tf.keras.layers.Dense(1, activation='sigmoid')
])
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
model.fit(X_train, y_train, epochs=10, batch_size=32, validation_split=0.1)

# 评估模型
_, accuracy = model.evaluate(X_test, y_test)
```

#### Pandas 与 PyTorch 的集成

PyTorch 是一个基于 Torch 的 Python 开源机器学习库。要将 Pandas DataFrame 与 PyTorch 配合使用，需要将它们转换为 PyTorch Tensor。下面是一个示例：

```python
import pandas as pd
import torch
from torch.utils.data import DataLoader, TensorDataset
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

##### 加载数据集
url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)

##### 分离特征和目标变量
X = df.drop('target_column', axis=1).values
y = df['target_column'].values

##### 执行训练-测试集划分
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 缩放特征
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

# 将 NumPy 数组转换为 PyTorch Tensor 并创建 DataLoader
train_dataset = TensorDataset(torch.Tensor(X_train), torch.Tensor(y_train))
test_dataset = TensorDataset(torch.Tensor(X_test), torch.Tensor(y_test))
train_loader = DataLoader(train_dataset, batch_size=32, shuffle=True)
test_loader = DataLoader(test_dataset, batch_size=32)

# 使用 PyTorch 构建并训练模型
model = torch.nn.Sequential(
    torch.nn.Linear(X_train.shape[1], 16),
    torch.nn.ReLU(),
    torch.nn.Linear(16, 1),
    torch.nn.Sigmoid()
)
criterion = torch.nn.BCELoss()
optimizer = torch.optim.Adam(model.parameters())

for epoch in range(10):
    for X_batch, y_batch in train_loader:
        y_pred = model(X_batch)
        loss = criterion(y_pred, y_batch.view(-1, 1))
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

# 评估模型
with torch.no_grad():
    correct = 0
    total = 0
    for X_batch, y_batch in test_loader:
        y_pred = model(X_batch)
        predicted = (y_pred > 0.5).float()
        total += y_batch.size(0)
        correct += (predicted == y_batch.view(-1, 1)).sum().item()
    accuracy = correct / total
```

总之，将 Pandas 与 Scikit-learn、TensorFlow 和 PyTorch 集成，使机器学习任务中的工作流更加流畅，因为 Pandas 提供了强大的数据操作工具，而这些库提供了先进的机器学习和深度学习功能。




### 总结

我们涵盖了与使用 pandas 进行机器学习相关的主题，包括数据预处理、特征工程、处理不平衡数据和特征缩放。我们还介绍了训练集-测试集划分和交叉验证的技术，并提供了使用 `Python` 和 `Scikit-learn` 实现它们的示例。此外，我们讨论了 pandas 与各种机器学习库（包括 `Scikit-learn`、`TensorFlow` 和 `PyTorch`）的集成，这使得在机器学习任务中能够无缝地进行数据处理和预处理。我们提供了如何将 pandas 与这些库集成并实现各种机器学习任务的示例。

机器学习的一个基本方面是特征工程，它涉及选择、转换和构造特征以提高模型性能。我们讨论了各种特征工程技术，如独热编码、特征缩放和降维，以及它们对机器学习的优势和益处。

此外，我们还谈到了处理不平衡数据，这是机器学习中的常见问题，尤其是在分类任务中。我们提供了使用 `Python` 和 `Scikit-learn` 识别和解决不平衡数据的分步说明。

最后，我们介绍了特征缩放和归一化，这些是用于标准化数据集中自变量或特征范围的预处理技术。我们讨论了特征缩放在机器学习中的重要性，并提供了使用 `Scikit-learn` 实现特征缩放和归一化的示例。

总体而言，本章涵盖了使用 pandas 进行机器学习的各种基本主题，包括数据预处理、特征工程、处理不平衡数据和模型评估技术。我们还演示了 pandas 与各种机器学习库的集成，这对于机器学习任务中的流程化工作流至关重要。

## 第 8 章：文本数据与自然语言处理



### 文本数据清洗与预处理

处理文本数据是数据分析的重要组成部分，因为许多数据集包含需要处理和分析的文本信息。文本数据可以有多种不同形式，例如客户评论、社交媒体帖子，甚至医疗记录。在数据分析中，处理文本数据涉及许多任务，包括清洗和预处理数据、提取相关信息，以及分析数据中的模式和趋势。为了完成这些任务，数据分析师通常会使用专门为处理文本数据而设计的专用工具和技术。

在 Python 中处理文本数据最强大的工具之一是 `Pandas` 库。`Pandas` 提供了许多专门设计用于在 `DataFrame` 或 `Series` 中处理文本数据的字符串方法。这些字符串方法使得操作和分析文本数据变得容易，让数据分析师能够快速轻松地提取相关信息并从数据中获得洞察。

以下是 `Pandas` 中用于处理文本数据的一些最常用字符串方法：

#### `str.contains()`

`str.contains()` 方法用于检查字符串是否包含指定的子字符串，并返回布尔值。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 检查 'text' 列是否包含子字符串 'cool'
df['contains_cool'] = df['text'].str.contains('cool')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | contains_cool |
| :--- | :--- |
| hello world | False |
| python is awesome | False |
| data science is cool | True |

正如你所见，`str.contains()` 方法向 `DataFrame` 添加了一列新列，指示 'text' 列中的每一行是否包含子字符串 'cool'。

#### `str.startswith()`

`str.startswith()` 方法用于检查字符串是否以指定的子字符串开头，并返回布尔值。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 检查 'text' 列是否以子字符串 'hello' 开头
df['starts_with_hello'] = df['text'].str.startswith('hello')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | starts_with_hello |
| :--- | :--- |
| hello world | True |
| python is awesome | False |
| data science is cool | False |

正如你所见，`str.startswith()` 方法向 `DataFrame` 添加了一列新列，指示 'text' 列中的每一行是否以子字符串 'hello' 开头。

#### `str.endswith()`

`str.endswith()` 方法用于检查字符串是否以指定的子字符串结尾，并返回布尔值。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 检查 'text' 列是否以子字符串 'world' 结尾
df['ends_with_world'] = df['text'].str.endswith('world')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | ends_with_world |
| :--- | :--- |
| hello world | True |
| python is awesome | False |
| data science is cool | False |

正如你所见，`str.endswith()` 方法向 `DataFrame` 添加了一列新列，指示 'text' 列中的每一行是否以子字符串 'world' 结尾。

#### `str.split()`

`str.split()` 方法用于根据指定的分隔符将字符串拆分为子字符串列表。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello,world', 'python,is,awesome', 'data,science,is,cool']})

# 使用逗号作为分隔符将 'text' 列拆分为子字符串列表
df['text_list'] = df['text'].str.split(',')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_list |
| :--- | :--- |
| hello,world | [hello, world] |
| python,is,awesome | [python, is, awesome] |
| data,science,is,cool | [data, science, is, cool] |

正如我们从前面的示例中所见，`str.split()` 方法根据逗号分隔符将 'text' 列拆分为子字符串列表。生成的列表随后存储在一个名为 'text_list' 的新列中。

#### `str.strip()`

`str.strip()` 方法用于移除字符串前导和尾随的空白字符。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['  hello world  ', '  python is awesome  ', '  data science is cool  ']})

# 移除 'text' 列前导和尾随的空白字符
df['text_stripped'] = df['text'].str.strip()

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_stripped |
| :--- | :--- |
| hello world | hello world |
| python is awesome | python is awesome |
| data science is cool | data science is cool |

正如我们从输出中所见，`str.strip()` 方法移除了 'text' 列前导和尾随的空白字符，并将清洗后的文本存储在一个名为 'text_stripped' 的新列中。

#### `str.replace()`

`str.replace()` 方法用于将指定的子字符串替换为另一个子字符串。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 在 'text' 列中将 'world' 替换为 'universe'
df['text_replaced'] = df['text'].str.replace('world', 'universe')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_replaced |
| :--- | :--- |
| hello world | hello universe |
| python is awesome | python is awesome |
| data science is cool | data science is cool |

正如我们从输出中所见，`str.replace()` 方法在 'text' 列中将子字符串 'world' 替换为 'universe'，并将更新后的文本存储在一个名为 'text_replaced' 的新列中。

#### `str.lower()`

`str.lower()` 方法用于将字符串转换为小写。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['Hello World', 'Python is Awesome', 'Data Science is Cool']})

# 将 'text' 列转换为小写
df['text_lower'] = df['text'].str.lower()

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_lower |
| :--- | :--- |
| Hello World | hello world |
| Python is Awesome | python is awesome |
| Data Science is Cool | data science is cool |

正如我们从输出中所见，`str.lower()` 方法将 'text' 列转换为小写，并将小写文本存储在一个名为 'text_lower' 的新列中。

#### `str.upper()`

`str.upper()` 方法用于将字符串转换为大写。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['Hello World', 'Python is Awesome', 'Data Science is Cool']})

# 将 'text' 列转换为大写
df['text_upper'] = df['text'].str.upper()

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_upper |
| :--- | :--- |
| Hello World | HELLO WORLD |
| Python is Awesome | PYTHON IS AWESOME |
| Data Science is Cool | DATA SCIENCE IS COOL |

正如我们从输出中所见，`str.upper()` 方法将 'text' 列转换为大写，并将大写文本存储在一个名为 'text_upper' 的新列中。

#### `str.len()`

`str.len()` 方法用于返回字符串的长度。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 获取 'text' 列中每个字符串的长度
df['text_length'] = df['text'].str.len()

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_length |
| :--- | :--- |
| hello world | 11 |
| python is awesome | 18 |
| data science is cool | 22 |

正如我们从输出中所见，`str.len()` 方法返回了 'text' 列中每个字符串的长度，并将结果存储在一个名为 'text_length' 的新列中。

#### `str.isnumeric()`

`str.isnumeric()` 方法用于检查字符串是否仅由数字字符组成，并返回布尔值。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['12345', '1a2b3c4d5e', '123 45']})

# 检查 'text' 列中的每个字符串是否仅由数字字符组成
df['is_numeric'] = df['text'].str.isnumeric()

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | is_numeric |
| :--- | :--- |
| 12345 | True |
| 1a2b3c4d5e | False |
| 123 45 | False |

正如我们从输出中所见，`str.isnumeric()` 方法检查了 'text' 列中的每个字符串是否仅由数字字符组成，并将结果存储在一个名为 'is_numeric' 的新列中。

#### `str.capitalize()`

`str.capitalize()` 方法用于将字符串的首字母大写。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 将 'text' 列中每个字符串的首字母大写
df['text_capitalized'] = df['text'].str.capitalize()

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_capitalized |
| :--- | :--- |
| hello world | Hello world |
| python is awesome | Python is awesome |
| data science is cool | Data science is cool |

正如我们从输出中所见，`str.capitalize()` 方法将 'text' 列中每个字符串的首字母大写，并将结果存储在一个名为 'text_capitalized' 的新列中。

#### `str.title()`

`str.title()` 方法用于将字符串中每个单词的首字母大写。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 将 'text' 列中每个字符串的每个单词首字母大写
df['text_title'] = df['text'].str.title()

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_title |
| :--- | :--- |
| hello world | Hello World |
| python is awesome | Python Is Awesome |
| data science is cool | Data Science Is Cool |

正如我们从输出中所见，`str.title()` 方法将 'text' 列中每个字符串的每个单词首字母大写，并将结果存储在一个名为 'text_title' 的新列中。

这些只是 `Pandas` 中可用于处理文本数据的众多字符串方法中的一部分。通过使用这些方法，数据分析师可以快速轻松地在 `DataFrame` 或 `Series` 中清洗、预处理和分析文本数据。




### 提取和转换文本特征

以下示例演示如何对 CSV 文件中的训练数据进行文本数据清洗和预处理。数据文件位于：`https://github.com/kittenpub/database-repository/blob/main/pandas_training_testdata.csv`

```python
import pandas as pd

# load the training data into a DataFrame
df = pd.read_csv('https://raw.githubusercontent.com/kittenpub/database-repository/main/pandas_training_testdata.csv')

# check the shape of the DataFrame
print("Shape of the DataFrame:", df.shape)

# check the first few rows of the DataFrame
print("First few rows of the DataFrame:")
print(df.head())

# check for missing values
print("Number of missing values in each column:")
print(df.isnull().sum())

# remove rows with missing values
df.dropna(inplace=True)

# convert text to lowercase
df['text'] = df['text'].str.lower()

# remove punctuation
import string
df['text'] = df['text'].apply(lambda x: x.translate(str.maketrans('', '', string.punctuation)))

# remove numbers
df['text'] = df['text'].str.replace('\d+', '')

# remove stopwords
import nltk
nltk.download('stopwords')
from nltk.corpus import stopwords
stop_words = stopwords.words('english')
df['text'] = df['text'].apply(lambda x: ' '.join([word for word in x.split() if word not in stop_words]))

# remove short words
df['text'] = df['text'].apply(lambda x: ' '.join([word for word in x.split() if len(word) > 3]))

# lemmatize the text
nltk.download('wordnet')
from nltk.stem import WordNetLemmatizer
lemmatizer = WordNetLemmatizer()
df['text'] = df['text'].apply(lambda x: ' '.join([lemmatizer.lemmatize(word) for word in x.split()]))

# check the first few rows of the cleaned DataFrame
print("First few rows of the cleaned DataFrame:")
print(df.head())

# save the cleaned DataFrame to a new CSV file
df.to_csv('cleaned_data.csv', index=False)
```

在本例中，我们首先使用 `read_csv()` 方法将训练数据加载到 `DataFrame` 中。随后检查 `DataFrame` 的形状 (`shape`) 以及前几行数据 (`head()`) 以了解数据概况。

接着，使用 `isnull()` 方法检查缺失值，并使用 `dropna()` 方法删除包含缺失值的行。

然后，我们对 `DataFrame` 的 `'text'` 列执行一系列文本清洗和预处理步骤：
- 使用 `lower()` 方法将文本转为小写。
- 使用 `translate()` 方法移除标点符号。
- 使用 `str.replace()` 方法移除数字。
- 使用 NLTK 库的 `stopwords` 语料库移除停用词。
- 使用 `lambda` 函数移除短词（长度 <= 3）。
- 使用 NLTK 库的 `WordNetLemmatizer` 进行词形还原。

最后，检查清洗后 `DataFrame` 的前几行，并使用 `to_csv()` 方法将结果保存到新的 CSV 文件中。





### 使用文本数据进行情感分析

情感分析是分析并提取一段文本中所表达的情感或情绪的过程。它也被称为观点挖掘或情感 AI。情感分析的目标是确定一段文本中表达的情感是积极、消极还是中性。

从本质上讲，情感分析包含两个主要步骤：文本预处理和情感分类。文本预处理涉及清洗和转换原始文本数据，使其适合分析。这可能涉及分词、移除停用词、词干提取或词形还原等任务。情感分类涉及将机器学习或自然语言处理模型应用于预处理后的文本，以将其分类为积极、消极或中性。

`Pandas` 可用于加载和预处理文本数据，但情感分类需要更高级的机器学习或自然语言处理库，例如 `Scikit-learn`、`NLTK` 或 `spaCy`。

以下是使用 `Pandas` 和 `Scikit-learn` 进行情感分析实战演示的分步解释：

#### 将数据加载到 Pandas DataFrame 中

```python
import pandas as pd
# 将数据加载到 DataFrame 中
df = pd.read_csv('https://raw.githubusercontent.com/kittenpub/database-repository/main/sentiment_analysis_data.csv')
```

在此步骤中，我们使用 `Pandas` 的 `read_csv()` 方法读取包含文本数据的 CSV 文件到 DataFrame 中。

#### 预处理文本数据

```python
import string
import nltk
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer

# 将文本转换为小写
df['text'] = df['text'].str.lower()

# 移除标点符号
df['text'] = df['text'].apply(lambda x: x.translate(str.maketrans('', '', string.punctuation)))

# 移除停用词
stop_words = stopwords.words('english')
df['text'] = df['text'].apply(lambda x: ' '.join([word for word in x.split() if word not in stop_words]))

# 对文本进行词形还原
lemmatizer = WordNetLemmatizer()
df['text'] = df['text'].apply(lambda x: ' '.join([lemmatizer.lemmatize(word) for word in x.split()]))
```

在此步骤中，我们对 DataFrame 的 `'text'` 列执行多个预处理步骤。我们首先使用 `lower()` 方法将文本转换为小写。然后使用 `string` 模块的 `translate()` 方法移除标点符号。我们使用 `nltk` 库的 `stopwords` 语料库移除停用词。最后，我们使用 `nltk` 库的 `WordNetLemmatizer` 对文本进行词形还原。

#### 将文本数据转换为词频稀疏矩阵

```python
from sklearn.feature_extraction.text import CountVectorizer

# 创建 CountVectorizer 对象
vectorizer = CountVectorizer()

# 在文本数据上拟合向量化器以学习词汇表
vectorizer.fit(df['text'])

#### 将文本数据转换为词频稀疏矩阵
X = vectorizer.transform(df['text'])
```

在此步骤中，我们从 `Scikit-learn` 创建一个 `CountVectorizer` 对象，将文本数据转换为词频稀疏矩阵。我们在 DataFrame 的 `'text'` 列上拟合向量化器以学习词汇表，然后使用 `transform()` 方法将 `'text'` 列转换为词频稀疏矩阵。

#### 将数据拆分为训练集和测试集

```python
from sklearn.model_selection import train_test_split

#### 将数据拆分为训练集和测试集
X_train, X_test, y_train, y_test = train_test_split(X, df['sentiment'], test_size=0.2, random_state=42)
```

在此步骤中，我们使用 `Scikit-learn` 的 `train_test_split()` 方法将数据拆分为训练集和测试集。我们使用 80% 的数据进行训练，20% 进行测试。

#### 在训练数据上训练机器学习模型

```python
from sklearn.naive_bayes import MultinomialNB

# 在训练数据上训练多项式朴素贝叶斯分类器
clf = MultinomialNB()
clf.fit(X_train, y_train)
```

在此步骤中，我们使用 `Scikit-learn` 的 `MultinomialNB()` 类在训练数据上训练一个 `Multinomial Naive Bayes`（多项式朴素贝叶斯）分类器。

#### 进行预测并评估模型准确率

```python
from sklearn.metrics import accuracy_score

# 在测试数据上进行预测
y_pred = clf.predict(X_test)

# 评估模型的准确率
accuracy = accuracy_score(y_test, y_pred)
print("Accuracy:", accuracy)
```

在此步骤中，我们使用训练好的分类器的 `predict()` 方法在测试数据上进行预测。然后我们使用 `Scikit-learn` 的 `accuracy_score()` 方法评估模型的准确率。准确率得分代表测试数据中正确分类实例的百分比。

#### 可视化结果

```python
import matplotlib.pyplot as plt
import seaborn as sns

# 创建混淆矩阵
from sklearn.metrics import confusion_matrix
conf_mat = confusion_matrix(y_test, y_pred)

# 绘制混淆矩阵
sns.heatmap(conf_mat, annot=True, cmap='Blues', fmt='d',
            xticklabels=['negative', 'neutral', 'positive'],
            yticklabels=['negative', 'neutral', 'positive'])
plt.xlabel('Predicted label')
plt.ylabel('True label')
plt.title('Confusion matrix')
plt.show()
```

在此步骤中，我们使用 `Scikit-learn` 的 `confusion_matrix()` 方法创建预测标签和真实标签的混淆矩阵。然后我们使用 `seaborn` 库的 `heatmap()` 方法将混淆矩阵可视化为热力图。

总体而言，上述步骤演示了如何使用 `Pandas` 和 `Scikit-learn` 执行情感分析。这些步骤包括将数据加载到 `Pandas` DataFrame 中、预处理文本数据、将文本数据转换为词频稀疏矩阵、将数据拆分为训练集和测试集、在训练数据上训练机器学习模型、在测试数据上进行预测以及评估模型的准确率。结果还可以使用混淆矩阵进行可视化。





### 主题建模

主题建模和文本聚类是自然语言处理中用于分析和组织大量文本数据的两种常用技术。这两种技术都用于从文本数据中提取有用信息，使其更易于理解和分析。

主题建模是一种用于识别大量文本文档集合中存在的主题或话题的技术。主题建模的目标是在没有任何先验主题知识的情况下，自动识别一组文档中讨论的潜在主题。主题建模算法使用统计方法将文档中经常共同出现的词语分组，并识别可由这些词组描述的主题。

用于主题建模的最流行算法之一是**潜在狄利克雷分布（LDA）**。LDA 是一种生成概率模型，它假设每个文档是主题的混合体，而每个主题是词语上的一个分布。LDA 通过迭代估计词语的概率分布，来估计每个文档和主题的主题分布和词语分布。

#### 实施主题建模的过程

使用**潜在狄利克雷分布（LDA）**执行主题建模的过程包含以下几个步骤：

#### 加载并预处理文本数据

第一步是将文本数据加载为适合分析的格式。这可能涉及清洗文本数据、移除停用词、词干提取或词形还原等。预处理后的文本数据通常表示为文档集合，其中每个文档是一个词语列表。

#### 创建文档-词项矩阵

下一步是创建文档-词项矩阵，它表示每个词项（词语）在每个文档中的频率。该矩阵通常表示为稀疏矩阵以节省内存。

##### 选择主题数量

在应用 LDA 算法之前，必须确定文本数据中的主题数量。这通常通过领域知识或试错法来完成。

#### 训练 LDA 模型

使用迭代算法在文档-词项矩阵上训练 LDA 模型。模型通过迭代估计词语的概率分布，来估计每个文档和主题的主题分布和词语分布。LDA 模型的输出是一组主题，每个主题表示为词语上的一个分布。

#### 评估 LDA 模型

可以使用一致性或困惑度等指标来评估 LDA 模型的质量。一致性度量主题中词语之间的语义相似度，而困惑度度量模型预测未见数据的能力。

#### 解释主题

最后一步是解释主题，并根据每个主题中最高频的词语为其分配人类可读的标签。此步骤可能涉及对主题的人工检查和一些领域知识。

LDA 是一种强大的技术，用于识别大量文本文档集合中存在的主题或话题，可用于信息检索、数据挖掘和内容分析等多种应用。

### 使用潜在狄利克雷分布 (LDA) 执行主题建模

以下是使用 **Pandas 2.0** 中的**潜在狄利克雷分布 (LDA)** 执行主题建模的实践演示：

#### 加载并预处理文本数据

```python
import pandas as pd
import string
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer

# load the data into a DataFrame
df = pd.read_csv('https://raw.githubusercontent.com/kittenpub/database-repository/main/topic_modeling_data.csv')

# convert the text to lowercase
df['text'] = df['text'].str.lower()

# remove punctuation
df['text'] = df['text'].apply(lambda x: x.translate(str.maketrans('', '', string.punctuation)))

# remove stop words
stop_words = stopwords.words('english')
df['text'] = df['text'].apply(lambda x: ' '.join([word for word in x.split() if word not in stop_words]))

# lemmatize the text
lemmatizer = WordNetLemmatizer()
df['text'] = df['text'].apply(lambda x: ' '.join([lemmatizer.lemmatize(word) for word in x.split()]))
```

在此步骤中，我们使用 `Pandas` 的 `read_csv()` 方法将数据加载到 `DataFrame` 中。然后我们对 `DataFrame` 的 `'text'` 列执行多个预处理步骤。我们使用 `lower()` 方法将文本转换为小写。然后我们使用 `string` 模块的 `translate()` 方法移除标点符号。我们使用 `nltk` 库的 `stopwords` 语料库移除停用词。最后，我们使用 `nltk` 库的 `WordNetLemmatizer` 对文本进行词形还原。

#### 创建文档-词项矩阵

```python
from sklearn.feature_extraction.text import CountVectorizer

# create a CountVectorizer object
vectorizer = CountVectorizer()

# fit the vectorizer on the text data to learn the vocabulary
vectorizer.fit(df['text'])

# transform the text data into a document-term matrix
doc_term_matrix = vectorizer.transform(df['text'])
```

在此步骤中，我们从 `Scikit-learn` 创建一个 `CountVectorizer` 对象，将文本数据转换为文档-词项矩阵。我们在 `DataFrame` 的 `'text'` 列上拟合向量化器以学习词汇表，然后使用 `transform()` 方法将 `'text'` 列转换为文档-词项矩阵。

#### 训练 LDA 模型

```python
# choose the number of topics
num_topics = 5

# create an LDA model
lda_model = LatentDirichletAllocation(n_components=num_topics, random_state=42)

# fit the LDA model on the document-term matrix
lda_model.fit(doc_term_matrix)
```

在此步骤中，我们选择文本数据中的主题数量（本例中为 5），并使用 `Scikit-learn` 的 `LatentDirichletAllocation` 类创建一个 LDA 模型。我们使用 `fit()` 方法在文档-词项矩阵上拟合 LDA 模型。

#### 解释主题

```python
# print the top 10 words in each topic
feature_names = vectorizer.get_feature_names()
for topic_idx, topic in enumerate(lda_model.components_):
    print(f"Topic {topic_idx}:")
    print(" ".join([feature_names[i] for i in topic.argsort()[:-10 - 1:-1]]))
    print()
```

在此步骤中，我们通过打印每个主题中前 10 个词语来解释主题。我们使用 `CountVectorizer` 对象的 `get_feature_names()` 方法获取特征名称列表（即词语），然后使用 `argsort()` 方法按词语频率对主题进行排序。最后，我们打印每个主题中前 10 个词语。

#### 评估 LDA 模型

```python
# print the perplexity score
print("Perplexity:", lda_model.perplexity(doc_term_matrix))
```

在此步骤中，我们通过使用训练好的 LDA 模型的 `perplexity()` 方法打印困惑度得分来评估 LDA 模型。困惑度得分衡量模型预测未见数据的能力，得分越低表示模型越好。

总体而言，上述步骤演示了如何在 **Pandas 2.0** 中使用 LDA 执行主题建模。这些步骤包括加载和预处理文本数据、创建文档-词项矩阵、训练 LDA 模型、解释主题以及评估模型。




### 文本聚类

另一方面，文本聚类是一种根据文档内容将相似文档归为一组的技术。文本聚类的目标是自动识别出共享共同主题或话题的文档组。文本聚类算法使用无监督机器学习技术，根据文档内容对相似文档进行分组。用于文本聚类的最流行算法之一是 K-means 聚类。K-means 聚类是一种迭代算法，它根据内容的相似性将文档分成 K 个簇。该算法根据距离度量（如欧氏距离或余弦相似度）迭代地将每个文档分配给最近的簇。主题建模和文本聚类在信息检索、数据挖掘和内容分析等多种应用中均很有用。它们可用于识别大量文本数据集中的模式和趋势，根据内容对文档进行分类，并总结大量文档集中包含的信息。

#### 文本聚类流程

使用 K-means 执行文本聚类的过程包含以下几个步骤：

#### 加载并预处理文本数据

第一步是将文本数据加载为适合分析的格式。这可能涉及清洗文本数据、移除停用词、词干提取或词形还原等。预处理后的文本数据通常表示为文档集合，其中每个文档是一个单词列表。

#### 创建文档-词项矩阵

下一步是创建文档-词项矩阵，该矩阵表示每个词项（单词）在每个文档中出现的频率。该矩阵通常表示为稀疏矩阵以节省内存。

##### 选择簇的数量

在应用 K-means 算法之前，必须确定文本数据中的簇的数量。这通常通过领域知识或试错法来完成。

#### 训练 K-means 模型

K-means 模型使用迭代算法在文档-词项矩阵上进行训练。该算法根据距离度量（如欧氏距离或余弦相似度）迭代地将每个文档分配给最近的簇。K-means 模型的输出是一组簇，每个簇表示为一个质心向量。

#### 评估 K-means 模型

可以使用轮廓系数或惯性等指标来评估 K-means 模型的质量。轮廓系数衡量实例聚类得有多好，而惯性衡量实例聚类得有多紧密。

#### 解读簇

最后一步是解读簇，并根据每个簇中最高频的单词为其分配人类可读的标签。此步骤可能涉及对簇的人工检查和一些领域知识。

K-means 是一种基于内容将相似文档归为一组的强大技术，可用于信息检索、数据挖掘和内容分析等多种应用。

### 使用 K-means 执行文本聚类

以下是使用 Pandas 2.0 执行 K-means 文本聚类的实操演示：

#### 加载并预处理文本数据

```python
import pandas as pd
import string
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer

# load the data into a DataFrame
df = pd.read_csv('https://raw.githubusercontent.com/kittenpub/database-repository/main/text_clustering_data.csv')

# convert the text to lowercase
df['text'] = df['text'].str.lower()

# remove punctuation
df['text'] = df['text'].apply(lambda x: x.translate(str.maketrans('', '', string.punctuation)))

# remove stop words
stop_words = stopwords.words('english')
df['text'] = df['text'].apply(lambda x: ' '.join([word for word in x.split() if word not in stop_words]))

# lemmatize the text
lemmatizer = WordNetLemmatizer()
df['text'] = df['text'].apply(lambda x: ' '.join([lemmatizer.lemmatize(word) for word in x.split()]))
```

在此步骤中，我们使用 `Pandas` 的 `read_csv()` 方法将数据加载到 `DataFrame` 中。然后我们对 `DataFrame` 的 `'text'` 列执行多个预处理步骤。我们使用 `lower()` 方法将文本转换为小写。然后我们使用 `string` 模块的 `translate()` 方法移除标点符号。我们使用 `nltk` 库的 `stopwords` 语料库移除停用词。最后，我们使用 `nltk` 库的 `WordNetLemmatizer` 对文本进行词形还原。

#### 创建文档-词项矩阵

```python
from sklearn.feature_extraction.text import CountVectorizer

# create a CountVectorizer object
vectorizer = CountVectorizer()

# fit the vectorizer on the text data to learn the vocabulary
vectorizer.fit(df['text'])

# transform the text data into a document-term matrix
doc_term_matrix = vectorizer.transform(df['text'])
```

在此步骤中，我们从 `Scikit-learn` 创建一个 `CountVectorizer` 对象，将文本数据转换为文档-词项矩阵。我们在 `DataFrame` 的 `'text'` 列上拟合向量化器以学习词汇表，然后使用 `transform()` 方法将 `'text'` 列转换为文档-词项矩阵。

#### 训练 K-means 模型

```python
from sklearn.cluster import KMeans

# choose the number of clusters
num_clusters = 3

# create a K-means model
kmeans_model = KMeans(n_clusters=num_clusters, random_state=42)

# fit the K-means model on the document-term matrix
kmeans_model.fit(doc_term_matrix)
```

在此步骤中，我们选择文本数据中的簇数量（在本例中为 3），并使用 `Scikit-learn` 的 `KMeans` 类创建 K-means 模型。我们使用 `fit()` 方法在文档-词项矩阵上拟合 K-means 模型。

#### 解读簇

```python
# get the top 10 terms in each cluster
feature_names = vectorizer.get_feature_names()
for i in range(num_clusters):
    print(f"Cluster {i}:")
    top_terms = [feature_names[idx] for idx in kmeans_model.cluster_centers_[i].argsort()[:-10 - 1:-1]]
    print(", ".join(top_terms))
    print()
```

在此步骤中，我们通过打印每个簇中前 10 个词项来解读簇。我们使用 `CountVectorizer` 对象的 `get_feature_names()` 方法获取特征名称列表（即单词），然后使用训练好的 K-means 模型的 `argsort()` 方法和 `cluster_centers_` 属性按各词项在每个簇中的频率对其进行排序。最后，我们打印每个簇中的前 10 个词项。

#### 评估 K-means 模型

```python
from sklearn.metrics import silhouette_score

# calculate the silhouette score
silhouette_score = silhouette_score(doc_term_matrix, kmeans_model.labels_)
print("Silhouette Score:", silhouette_score)
```

在此步骤中，我们通过使用 `Scikit-learn` 的 `silhouette_score()` 方法计算轮廓系数来评估 K-means 模型。轮廓系数衡量实例聚类得有多好，分数越高表示模型越好。

总体而言，上述步骤演示了如何在 Pandas 2.0 中使用 K-means 执行文本聚类。步骤包括加载和预处理文本数据、创建文档-词项矩阵、训练 K-means 模型、解读簇以及评估模型。K-means 是一种基于内容将相似文档归为一组的强大技术，可用于信息检索、数据挖掘和内容分析等多种应用。




### 摘要

在本章中，我们涵盖了使用 `Pandas 2.0` 进行文本数据分析的几个主题。我们首先讨论了文本数据清洗与预处理，这涉及多个步骤，例如将文本转换为小写、移除标点符号、移除停用词以及词形还原。我们演示了如何使用 `Pandas 2.0` 对示例数据集执行文本数据清洗与预处理。随后我们转向情感分析，这涉及确定给定文本的情感倾向（积极、消极或中性）。我们解释了使用 `Pandas 2.0` 执行情感分析的过程，包括加载和预处理文本数据、训练机器学习模型以及评估模型性能。我们演示了如何使用 `Pandas 2.0` 和 `Scikit-learn` 对示例数据集执行情感分析。接下来，我们讨论了主题建模和文本聚类，这些是基于文档内容将相似文档归类在一起的技术。我们解释了使用隐含狄利克雷分布（`LDA`）进行主题建模以及使用 K-means 进行文本聚类的过程，这些过程涉及多个步骤，如创建文档-词项矩阵、训练机器学习模型和解读结果。我们演示了如何使用 `Pandas 2.0` 和 `Scikit-learn` 对示例数据集执行主题建模和文本聚类。

## 第 9 章：地理空间数据分析

### 地理空间数据与 Pandas 2.0 简介

地理空间数据，也称为空间数据或地理数据，是指附带位置成分的任何数据。地理空间数据可以采用点（例如经纬度坐标）、线（例如道路和河流）或多边形（例如地块和行政边界）的形式。地理空间数据可来自各种来源，如 `GPS` 设备、卫星图像和地图。

在数据分析中处理地理空间数据涉及多个步骤。第一步是获取地理空间数据并将其加载为适合分析的格式。这可能涉及将数据转换为标准格式，如 `GeoJSON` 或 Shapefile。下一步是预处理数据，这可能涉及清洗数据、移除重复项以及处理缺失或无效值。预处理后的地理空间数据通常表示为一个 DataFrame，其列包含位置坐标、属性和其他元数据。

数据预处理完成后，下一步是可视化数据以获取洞察并识别模式。这可能涉及使用 `matplotlib`、`seaborn` 和 `folium` 等库创建地图、热力图和其他类型的可视化。可视化地理空间数据使分析师能够识别模式和趋势，例如某些要素密度高或低的区域，并基于这些洞察做出明智决策。

处理地理空间数据的另一个重要步骤是空间分析，这涉及分析空间要素与属性之间的关系。这可能涉及执行空间查询，例如选择特定距离或区域内的要素，或基于属性聚合要素。空间分析可使用 `GeoPandas`、`Shapely` 和 `PySAL` 等库执行。

地理空间数据分析可用于多种应用，如城市规划、交通、生态学和地质学。例如，城市规划师可以利用地理空间数据分析交通模式并规划新的交通路线。生态学家可以利用地理空间数据研究动植物物种及其栖息地的分布。地质学家可以利用地理空间数据研究岩石和矿物等地质要素的形成与分布。

#### 用于地理空间分析的 Pandas

##### 对 GeoDataFrame 的支持

`Pandas 2.0` 提供对 `GeoDataFrame` 的支持，后者是包含几何列的 `DataFrame` 对象的扩展。几何列可存储各类空间数据，如点、线和多边形。`GeoDataFrame` 对象允许用户使用 `Shapely` 和 `GeoPandas` 等各种 Python 库对数据执行空间操作和分析。

##### 与其他 Python 地理空间库的集成

`Pandas 2.0` 可轻松与 `GeoPandas`、`Shapely` 和 `folium` 等其他 Python 地理空间库集成。这些库为地理空间分析提供了额外功能，如空间连接、缓冲区分析和交互式地图可视化。通过结合使用 `Pandas 2.0` 和这些库，用户能高效且有效地执行复杂的地理空间分析任务。

##### 灵活的数据操作能力

`Pandas 2.0` 提供强大的数据操作能力，如筛选、聚合和透视，这些同样适用于地理空间数据。这些操作可用于从地理空间数据中提取洞察和模式，并为进一步的分析和可视化准备数据。

##### 对时间序列分析的支持

`Pandas 2.0` 内置了对时间序列分析的支持，这对于随时间分析和可视化地理空间数据非常有用。例如，用户可以按时间间隔聚合地理空间数据并创建时间序列图，以直观展示随时间变化的趋势和模式。

总体而言，`Pandas 2.0` 为地理空间数据分析提供了一个强大且灵活的框架。通过利用其对 `GeoDataFrame` 的支持、与其他 Python 地理空间库的集成、数据操作能力以及时间序列分析，用户能高效且有效地执行复杂的地理空间分析任务。

### 处理地理空间数据格式

`Pandas 2.0` 支持数据分析中常用的多种地理空间数据格式：

#### GeoJSON

`GeoJSON` 是一种流行的地理空间数据格式，用于编码点、线和多边形等各种几何类型。它是一种轻量级格式，易于使用和阅读。`Pandas 2.0` 分别支持使用 `read_json()` 和 `to_json()` 方法读取和写入 `GeoJSON` 数据。

#### ESRI Shapefile

`ESRI Shapefile` 是一种广泛使用的地理空间数据格式，用于存储点、线和多边形等各类空间数据。它由多个文件组成，共同表示空间要素的几何形状和属性。`Pandas 2.0` 分别支持使用 `read_file()` 和 `to_file()` 方法读取和写入 Shapefile 数据。

#### GPS 交换格式 (GPX)

`GPX` 是一种在各种应用程序和设备之间交换 `GPS` 数据的标准文件格式。它采用基于 XML 的格式，存储轨迹、路线和航点等各类 `GPS` 数据。`Pandas 2.0` 支持使用 `xml.etree.ElementTree` 模块的 `read_xml()` 方法读取 `GPX` 数据。

#### Keyhole 标记语言 (KML)

`KML` 是一种用于存储点、线和多边形等各类地理空间数据的文件格式。它是一种基于 XML 的格式，常用于创建地图和可视化。`Pandas 2.0` 支持使用 `xml.etree.ElementTree` 模块的 `read_xml()` 方法读取 `KML` 数据。

#### GeoTIFF

`GeoTIFF` 是一种栅格地理空间数据格式，广泛用于存储卫星图像和地形模型等各类空间数据。它是一种基于 TIFF 的格式，包含坐标参考系统和地理配准信息等额外的空间元数据。`Pandas 2.0` 支持使用 `gdal` 库读取 `GeoTIFF` 数据。

总体而言，`Pandas 2.0` 支持数据分析中常用的多种地理空间数据格式。通过利用其对这些格式的支持，用户可以轻松加载和预处理各种格式的地理空间数据，并使用 `Shapely` 和 `GeoPandas` 等其他 Python 库进行分析和可视化。





### 加载、探索、转换和保存地理空间数据

以下是从 IndiaGIS 数据集加载、探索、转换和保存地理空间数据的步骤：

#### 下载并解压数据集

IndiaGIS 数据集以压缩 ZIP 文件的形式提供。从提供的链接下载文件，并将其内容解压到本地目录。

#### 使用 GeoPandas 加载数据

GeoPandas 是一个 Python 库，它扩展了 Pandas 的功能以支持地理空间数据。如果尚未安装，请使用 `pip install geopandas` 安装 GeoPandas。然后，使用 GeoPandas 的 `read_file()` 方法加载数据集：

```python
import geopandas as gpd
#### 加载数据
india_gdf = gpd.read_file('path/to/indiaGIS.shp')
```

这会将 Shapefile 数据加载到一个名为 `india_gdf` 的 `GeoDataFrame` 对象中。

#### 探索数据

数据加载后，您可以使用 `GeoDataFrame` 对象的各种方法和属性来探索其属性和几何信息。例如，您可以使用 `head()` 方法查看数据的前几行：

```python
print(india_gdf.head())
```

您还可以使用 `plot()` 方法创建数据的基本可视化：

```python
india_gdf.plot()
```

这将创建一张印度地图，显示数据集中要素的几何形状。

#### 转换数据

您可以使用 GeoPandas 的方法和函数对数据执行各种转换。例如，您可以使用 `to_crs()` 方法将数据的坐标参考系统 (CRS) 转换为不同的 CRS：

```python
# 将 CRS 转换为 EPSG:4326
india_gdf = india_gdf.to_crs(epsg=4326)
```

这会将数据的 CRS 转换为常用的 WGS84 CRS，其 EPSG 代码为 4326。

#### 保存数据

您可以使用 `GeoDataFrame` 对象的 `to_file()` 方法以新格式保存数据。例如，您可以使用以下代码将数据保存为 GeoJSON 文件：

```python
# 将数据保存为 GeoJSON 文件
india_gdf.to_file('path/to/indiaGIS.geojson', driver='GeoJSON')
```

这会将数据保存为指定目录下的 GeoJSON 文件。

总体而言，上述步骤演示了如何使用 GeoPandas 加载、探索、转换和保存地理空间数据。GeoPandas 为地理空间数据分析提供了一个强大且灵活的框架，并可结合 `Shapely`、`folium` 和 `matplotlib` 等其他 Python 库用于高级分析和可视化。

### 高级地理空间操作

以下是使用 GeoPandas 进行的一些更高级的地理空间操作和数据转换技术：

#### 空间连接

空间连接是地理空间分析中使用的一项重要技术，它有助于根据数据的位置和空间关系将两个或多个数据集组合起来。从本质上讲，空间连接使您能够叠加地理空间数据，以识别在单独考虑数据集时可能不明显的模式、关系和趋势。

最常见的空间连接类型之一是点在多边形连接。这种连接涉及将点数据集与多边形数据集结合，以确定哪些点落在每个多边形内。这对于分析特定地理区域或区域内事件（如犯罪事件）的分布非常有用。

其他类型的空间连接包括多边形对多边形、线对多边形和点对线连接。这些连接允许您基于其他空间关系组合数据集，例如确定哪些多边形相交或哪些线与多边形相交。

空间连接常用于广泛的应用中，包括城市规划、自然资源管理和环境监测。通过组合地理空间数据集，您可以更深入地了解不同变量之间的关系，并就如何在特定区域管理和分配资源做出更明智的决策。

#### 执行空间连接操作

要在给定数据库上执行空间连接，您需要一个像 GeoPandas 这样的地理空间库，它扩展了 Pandas 的功能以处理地理空间数据。在本示例中，我们假设您有两个数据集——一个来自 `indiaGIS.zip` 文件，另一个包含一些地理空间信息。我们将使用 Python 和 GeoPandas 库来完成此任务。

首先，安装所需的库：

```bash
pip install geopandas
```

导入必要的库：

```python
import pandas as pd
import geopandas as gpd
from shapely.geometry import Point
```

将 indiaGIS 数据集加载为 `GeoDataFrame`：

```python
# 假设数据采用 CSV 格式，包含 'latitude' 和 'longitude' 列
data = pd.read_csv('path/to/your/indiaGIS.csv')
# 通过创建 'geometry' 列将 DataFrame 转换为 GeoDataFrame
geometry = [Point(xy) for xy in zip(data.longitude, data.latitude)]
data_gdf = gpd.GeoDataFrame(data, geometry=geometry)
```

将第二个数据集加载为 `GeoDataFrame`。将 `'your_second_dataset.shp'` 替换为适当的文件路径和格式（例如 Shapefile、GeoJSON）。

```python
second_dataset_gdf = gpd.read_file('path/to/your/second_dataset.shp')
```

执行空间连接：

```python
# 您可以选择 'inner'、'left' 或 'right' 作为连接类型
joined_gdf = gpd.sjoin(data_gdf, second_dataset_gdf, how='inner', op='intersects')
```

在 `gpd.sjoin()` 函数中，`how` 参数定义连接类型（inner、left 或 right），`op` 参数定义用于连接的空间操作类型（intersects、within 或 contains）。

保存空间连接的结果：

```python
joined_gdf.to_file('path/to/your/joined_data.shp')
```

此示例演示了如何使用 Python 中的 GeoPandas 库执行空间连接。请确保将文件路径和格式替换为适合您数据集的适当值。

#### 缓冲区分析

缓冲区分析是地理信息系统 (GIS) 中用于分析和可视化空间数据的常用技术。它涉及在特定要素或要素集（如道路、河流、建筑物或兴趣点）周围创建缓冲区。缓冲区代表要素周围的特定距离或半径，可用于识别落在此距离内的区域。

缓冲区分析在城市规划、环境研究和应急管理中特别有用。例如，城市规划师可以使用缓冲区分析来确定拟建新开发项目对现有基础设施的影响。环境科学家可以使用缓冲区分析来识别关键栖息地区域或模拟污染物的扩散。应急管理人员可以使用缓冲区分析来识别面临洪水或其他自然灾害风险的区域。

GIS 软件（如 ArcGIS 和 QGIS）提供了一系列用于执行缓冲区分析的工具。这些工具允许用户指定要缓冲的要素、缓冲距离和缓冲区类型（例如圆形、方形或自定义多边形）。生成的缓冲区随后可用于进一步分析，例如与其他数据集叠加或生成统计数据。





#### 执行缓冲区分析

要对给定数据库执行缓冲区分析，我们将使用 Python 和 GeoPandas 库。

如果尚未安装所需库，请先安装：

```
pip install geopandas
```

导入必要的库：

```
import pandas as pd
import geopandas as gpd
from shapely.geometry import Point
```

将 `indiaGIS` 数据集加载为 GeoDataFrame：

```
# 假设数据为 CSV 格式，包含 'latitude' 和 'longitude' 列
data = pd.read_csv('path/to/your/indiaGIS.csv')

# 通过创建 'geometry' 列将 DataFrame 转换为 GeoDataFrame
geometry = [Point(xy) for xy in zip(data.longitude, data.latitude)]
data_gdf = gpd.GeoDataFrame(data, geometry=geometry)
```

定义缓冲区距离：

```
buffer_distance = 1000  # 米，或根据数据集 CRS 而定的其他单位
```

执行缓冲区分析：

```
# 确保数据处于单位为米的投影坐标系中
# 如果不是，则需要在缓冲前将其重投影到合适的 CRS
data_gdf_projected = data_gdf.to_crs("EPSG:32643")  # 示例：UTM Zone 43N (WGS 84)

# 在点周围创建缓冲区多边形
buffered_gdf = data_gdf_projected.copy()
buffered_gdf['geometry'] = data_gdf_projected.buffer(buffer_distance)
```

如果您想执行进一步的空间分析，请将缓冲后的数据集重投影回原始 CRS：

```
buffered_gdf_original_crs = buffered_gdf.to_crs(data_gdf.crs)
```

将缓冲区多边形保存为新的地理空间文件：

```
buffered_gdf_original_crs.to_file('path/to/your/indiaGIS_buffered.shp')
```

此示例演示了如何使用 Python 中的 GeoPandas 库执行缓冲区分析。请务必将文件路径和格式替换为适合您数据集的相应值，并根据需要调整缓冲区距离和 CRS。

#### 融合

融合 是一项至关重要的地理空间操作，广泛用于地理信息系统 (GIS) 和地理空间数据分析。它涉及合并数据集中共享公共属性或特征（如区域或城市）的要素。该过程融合这些要素的几何图形并聚合其属性，从而生成具有新属性集的单个要素。融合操作可用于多种目的，例如简化复杂数据集、创建汇总统计或生成新的空间数据图层。例如，如果您有一张显示州界和人口数据的美国地图，可以使用融合将人口低于特定阈值的所有州合并为单个区域。此过程简化了数据，使其更易于分析。

#### 执行融合操作

要对给定数据库执行融合操作，我们将使用 Python 和 GeoPandas 库。

如果尚未安装所需库，请先安装：

```
pip install geopandas
```

导入必要的库：

```
import pandas as pd
import geopandas as gpd
from shapely.geometry import Point
```

将 `indiaGIS` 数据集加载为 GeoDataFrame：

```
# 假设数据为 CSV 格式，包含 'latitude' 和 'longitude' 列
data = pd.read_csv('path/to/your/indiaGIS.csv')

# 通过创建 'geometry' 列将 DataFrame 转换为 GeoDataFrame
geometry = [Point(xy) for xy in zip(data.longitude, data.latitude)]
data_gdf = gpd.GeoDataFrame(data, geometry=geometry)
```

选择用于融合操作的属性。在给定示例中，我们将使用 `group_column` 属性。请将 `group_column` 替换为数据集中合适的列名：

```
dissolve_column = 'group_column'
```

执行融合操作：

```
dissolved_gdf = data_gdf.dissolve(by=dissolve_column)
```

默认情况下，融合操作将通过取每组中的第一个值来聚合其他属性。如果您需要应用不同的聚合函数，可以使用 `aggfunc` 参数：

```
dissolved_gdf = data_gdf.dissolve(by=dissolve_column, aggfunc={'column1': 'sum', 'column2': 'mean'})
```

将 `column1` 和 `column2` 替换为数据集中合适的列名，并选择最适合您需求的聚合函数（例如 `sum`、`mean`、`max`、`min`）。

将融合后的数据集保存为新的地理空间文件：

```
dissolved_gdf.to_file('path/to/your/indiaGIS_dissolved.shp')
```

此示例演示了如何使用 Python 中的 GeoPandas 库执行融合操作。请务必将文件路径、格式和列名替换为适合您数据集的相应值。

#### 叠加分析

叠加分析 是一种通过执行几何集合运算（如并集、交集或差集）来组合和分析地理空间数据的过程。该技术常用于 GIS（地理信息系统）中，以从不同数据集中提取相关信息，并获得关于它们之间关系的新见解。

要执行叠加分析，我们可以使用 Python 和 GeoPandas 库，后者提供了一套用于处理地理空间数据的工具和函数。借助 GeoPandas，我们可以加载和操作地理空间数据集，执行各种空间运算，并使用 matplotlib 或其他绘图库可视化结果。

例如，如果我们有一个建筑物数据集和一个地块数据集，可以使用叠加分析来确定哪些建筑物位于每个地块内，或者哪些地块与特定建筑物相邻。此信息可用于各种应用，如城市规划、环境分析或房地产管理。

#### 执行叠加分析

假设您有两个数据集——一个来自 `indiaGIS.zip` 文件，另一个包含某些地理空间信息，请遵循以下步骤：

如果尚未安装所需库，请先安装：

```
pip install geopandas
```

导入必要的库：

```
import pandas as pd
import geopandas as gpd
from shapely.geometry import Point
```

将 `indiaGIS` 数据集加载为 GeoDataFrame：

```
# 假设数据为 CSV 格式，包含 'latitude' 和 'longitude' 列
data = pd.read_csv('path/to/your/indiaGIS.csv')

# 通过创建 'geometry' 列将 DataFrame 转换为 GeoDataFrame
geometry = [Point(xy) for xy in zip(data.longitude, data.latitude)]
data_gdf = gpd.GeoDataFrame(data, geometry=geometry)
```

将第二个数据集加载为 GeoDataFrame。请将 `your_second_dataset.shp` 替换为合适的文件路径和格式（例如 Shapefile、GeoJSON）。

```
second_dataset_gdf = gpd.read_file('path/to/your/second_dataset.shp')
```

确保两个数据集具有相同的 CRS（坐标参考系）。如果不同，请将其中一个数据集重投影以匹配另一个：

```
second_dataset_gdf = second_dataset_gdf.to_crs(data_gdf.crs)
```

执行叠加分析。在本示例中，我们将执行交集运算：

```
overlay_gdf = gpd.overlay(data_gdf, second_dataset_gdf, how='intersection')
```

您可以更改 `how` 参数以执行其他集合运算，例如 `union` 或 `difference`。

保存叠加分析的结果：

```
overlay_gdf.to_file('path/to/your/indiaGIS_overlay.shp')
```

此示例演示了如何使用 Python 中的 GeoPandas 库执行叠加分析。请务必将文件路径、格式和列名替换为适合您数据集的相应值。

总的来说，使用 GeoPandas 的这些高级地理空间操作和数据转换技术有助于对地理空间数据执行复杂的分析和建模任务。





#### 地理编码与反向地理编码

地理编码和反向地理编码是用于在不同格式之间转换地理数据的技术，具体来说是在人类可读的地址和地理坐标之间进行转换。

##### 地理编码

地理编码是将位置描述（如街道地址、邮政编码或地名）转换为地理坐标的过程。它涉及通过将特定地址或地点转换为纬度和经度值，来识别其在地球表面上的空间位置。

地理编码是一种至关重要的工具，广泛应用于物流、制图和导航系统、社交媒体平台以及基于 Web 的服务等众多领域。地理编码使用户能够在地图上定位特定点、基于位置数据做出明智决策，并分析空间模式。

地理编码利用地理空间数据和算法的组合，来精确确定特定位置的地理坐标。地理编码过程包含多个步骤，始于数据获取、标准化和匹配。

- **数据获取** 涉及收集包含位置信息的数据源，例如邮政编码目录、街道地图和卫星影像。
- **标准化** 是通过纠正拼写错误、缩写和其他不一致之处，来规范化位置信息的过程。
- **匹配** 涉及将标准化后的数据与地理参考数据库进行比对，以准确识别该位置的纬度和经度。

##### 反向地理编码

反之，反向地理编码是将地理坐标转换为人类可读的地址或地名的过程。当用户拥有某位置的经纬度值，但需要知道其物理地址时，反向地理编码非常有用。反向地理编码也用于用户希望获取特定位置信息的应用程序中，例如天气预报、附近餐厅或旅游景点。

反向地理编码涉及的过程与地理编码类似，但顺序相反。该过程始于获取某位置的地理坐标，然后将其与地理参考数据库匹配，以确定对应的地址或地名。反向地理编码通常使用与地理编码相同的地理空间数据和算法，只是反向操作。反向地理编码的准确性取决于所用地理空间数据的质量和匹配算法。

##### 实现地理编码与反向地理编码

地理编码和反向地理编码在交通、物流、营销和房地产等各个行业有着广泛的应用。

- 在 **交通** 领域，地理编码和反向地理编码用于路线优化、车队管理和车辆追踪。
- 在 **物流** 领域，地理编码和反向地理编码用于仓库选址优化、货物追踪和配送路线规划。
- 在 **营销** 领域，地理编码和反向地理编码用于定向广告和基于位置的促销活动。
- 在 **房地产** 领域，地理编码和反向地理编码用于房产估值、选址和市场分析。

要在给定数据库上实现地理编码和反向地理编码，请遵循以下步骤：

1.  从提供的链接下载并解压 `indiaGIS.zip` 文件。解压后的数据应为地理空间文件格式，如 GeoJSON、Shapefile，或包含纬度和经度列的 CSV 文件。
2.  选择一种编程语言和一个库来执行地理编码和反向地理编码。本例中，我们将使用 Python 和 `geopy` 库。
3.  安装所需的库：
    ```
    pip install geopy
    ```
4.  导入必要的模块并读取地理空间数据：
    ```python
    import pandas as pd
    from geopy.geocoders import Nominatim
    from geopy.extra.rate_limiter import RateLimiter

    # 假设数据为 CSV 格式，包含 'latitude' 和 'longitude' 列
    data = pd.read_csv('path/to/your/indiaGIS.csv')
    ```
5.  创建地理定位器实例和速率限制器：
    ```python
    geolocator = Nominatim(user_agent="your_app_name")
    rate_limiter = RateLimiter(geolocator.geocode, min_delay_seconds=1)
    ```
6.  实现地理编码：
    ```python
    def geocode_address(address):
        location = rate_limiter(address)
        if location:
            return location.latitude, location.longitude
        else:
            return None, None

    data['coordinates'] = data['address'].apply(geocode_address)
    data[['latitude', 'longitude']] = pd.DataFrame(data['coordinates'].tolist(), index=data.index)
    ```
    将 `'address'` 替换为数据集中包含地址的相应列名。
7.  实现反向地理编码：
    ```python
    def reverse_geocode(coordinates):
        location = geolocator.reverse(coordinates, exactly_one=True)
        if location:
            return location.address
        else:
            return None

    data['reverse_geocoded_address'] = data['coordinates'].apply(reverse_geocode)
    ```
8.  保存更新后的数据：
    ```python
    data.to_csv('path/to/your/indiaGIS_updated.csv', index=False)
    ```

本示例演示了如何使用 `geopy` 库对数据集执行地理编码和反向地理编码。请注意，`geopy` 库使用 OpenStreetMap 的 `Nominatim` 服务进行地理编码，该服务有使用限制。请务必查阅其使用政策并予以遵守。您也可以使用其他地理编码服务，如 Google Maps API、Bing Maps API 或 Mapbox，但这些可能需要 API 密钥且有不同的使用限制。





### 概要

本章讨论了地理空间数据分析的各个方面，包括数据格式、`Pandas` 的作用，以及使用 `Python` 和 `GeoPandas` 进行的多种地理空间操作。

地理空间数据格式存储地理要素的位置和形状信息，以及其属性。常见格式包括 Shapefile、`GeoJSON`，以及包含经纬度列的 `CSV` 文件。这些格式支持在各类应用中对空间数据进行存储、可视化和操作。

尽管 `Pandas` 并非专为地理空间数据设计，但它通过提供 `DataFrame` 等高效数据结构来管理表格数据（包括地理空间属性），从而为地理空间分析做出贡献。不过，对于更高级的地理空间操作，建议使用扩展了 `Pandas` 功能的 `GeoPandas`。

本章涵盖了使用 `Python` 和 `GeoPandas` 进行的一系列地理空间操作：

#### 空间连接

空间连接根据几何对象之间的空间关系将两个数据集结合起来。本章介绍了如何使用 `GeoPandas` 库执行空间连接：将数据集加载为 `GeoDataFrame`，并使用 `sjoin()` 函数。

#### 缓冲区分析

缓冲区分析根据指定距离在数据集的特定要素周围创建区域。本章演示了如何使用 `GeoPandas` 进行缓冲区分析：将 `DataFrame` 转换为 `GeoDataFrame`，并使用 `buffer()` 函数。

#### 融合操作

融合是一种地理空间操作，用于根据公共属性合并要素，将其几何图形合并并聚合其属性。本章展示了如何使用 `GeoPandas` 执行融合操作：将数据集加载为 `GeoDataFrame`，并使用 `dissolve()` 函数。

#### 叠加分析

叠加分析通过对几何图形执行集合运算（如相交、并集或差集），将两个或多个数据集结合起来。本章演示了如何使用 `GeoPandas` 进行叠加分析：将数据集加载为 `GeoDataFrame`，确保它们具有相同的 `CRS`，并使用 `overlay()` 函数。

#### 地理编码与逆地理编码

地理编码是将地址或地名转换为地理坐标（经纬度）的过程，而逆地理编码则是相反的过程。本章演示了如何使用 `geopy` 库实现这些过程。

贯穿全章，我们提供了使用 `Python`、`Pandas` 和 `GeoPandas` 库对给定数据集执行这些地理空间操作的示例。这些知识使用户能够有效地操作和分析地理空间数据，使其适用于地理空间领域的广泛应用。

谢谢

## 后记

合上《Learning Pandas 2.0》（学习 Pandas 2.0）的书页，你不禁会因所获得知识的深度和广度而感到充满力量。这本全面的指南带你深入探索了流行的用于数据操作和分析的 `Python` 库最新版本的内部运作机制。

你学会了如何释放 `Pandas 2.0` 及其新特性的全部潜力，并获得了宝贵的见解和实战经验，确保你具备驾驭它的知识和技能。

你从 `Pandas 2.0` 的核心概念入手，涵盖从数据结构到高级索引技术，探索了加载、存储和操作数据的无数方法。你在时间序列和 `DateTime` 操作方面积累了专业知识，并使用 `Seaborn` 和 `Plotly` 等强大工具可视化数据。

你还学会了如何通过优化策略和使用 `Dask` 进行并行计算来提升 `Pandas` 代码的性能。

随着学习深入，你还学会了如何通过将 `Pandas 2.0` 与 `Scikit-learn`、`TensorFlow` 和 `PyTorch` 集成来释放机器学习的威力。你掌握了处理不平衡数据和特征缩放的技术，并利用 `Pandas 2.0` 深入探索了文本数据和自然语言处理的世界。

此外，你还拓展了地理空间数据分析与可视化的知识，并通过金融、社交媒体、电子商务、`IoT`（物联网）和医疗保健等领域的真实案例研究应用所学技能。这些实战练习帮助你获得将 `Pandas 2.0` 应用于真实场景的宝贵经验，让你做好准备在职业生涯中应对复杂的数据分析任务。

最后，本书还提供了关于 `Pandas 2.0` 最佳实践和未来趋势的见解，指引你成为 `Pandas` 专家。你对自己驾驭这一前沿库的能力充满信心，并渴望将新获得的知识应用到未来的数据分析项目中。

放下这本书，你不禁对这本无所不包的指南《Learning Pandas 2.0》心生感激。无论你是经验丰富的数据专业人士，还是刚刚踏上数据科学之旅的新手，本书都是助你提升数据分析技能的完美资源。凭借其循序渐进的说明、真实案例和宝贵见解，你现在已完全具备掌握 `Pandas 2.0` 并释放其全部潜力的能力。

