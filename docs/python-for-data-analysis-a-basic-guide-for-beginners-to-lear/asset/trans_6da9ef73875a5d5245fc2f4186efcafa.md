

在 Python 上开发 `SciPy` 的另一个优势是，在开发高级程序和特定应用时，可以方便地使用强大的编程语言。 使用 `SciPy` 的科学应用受益于全球开发者的贡献，在无数软件生态位中开发额外的模块。 一切成果都已对 Python 程序员开放，从数据库子程序和类到 `parallel programming to the web`。 这些强大的工具与 `SciPy` 数学库一起提供。

### IPython (增强交互式控制台)

`IPython (Interactive Python)` 是用于交互式计算的接口或命令 shell，可使用多种编程语言。 `IPython` 最初专门为 Python 创建，支持 introspection、富媒体、shell 语法、tab 补全和历史记录。 `IPython` 提供的一些功能包括：`interactive shells (terminal and Qt-based)`；基于浏览器的 notebook 界面，支持代码、文本、数学、内联绘图和其他媒体；支持交互式数据可视化和使用 GUI 工具包；可嵌入到您自己的项目中的灵活解释器；并行计算工具。 `IPython` 的架构提供 `parallel and distributed computing.` `IPython` 允许开发、执行、调试和交互式监控并行应用程序，因此 `I (Interactive) in IPython.` 底层架构可以轻松分离并行性，使 `IPython` 能够协助多种并行风格，包括：`Single program, various information (SPMD) parallelism`，`Multiple programs, various data (MIMD) parallelism`，`Message passing using MPI`，`Task parallelism`，`Data parallelism`，这些方法的组合甚至自定义用户定义策略。

并行计算功能已在 `ipyparallel python package` 下变为可选，并在 `IPython 4.0` 的实现中。

`IPython` 通常源自 `SciPy stack libraries`，例如 `NumPy` 和 `SciPy`，经常与各种 `Scientific Python distributions` 之一组合安装。 `IPython` 也可以与选定的 `SciPy stack libraries` 集成，主要为 `matplotlib`，在使用 `Jupyter notebook` 时会生成内联图表。 为了自定义富对象显示，Python 库可以实现 `IPython-specific hooks.` 例如，如果在 `IPython` 上下文中使用，`SymPy` 可以实现 `rendering of mathematical expressions as rendered LaTeX.`

### SymPy (符号数学)

由 Ondřej Čertík 和 Aaron Meurer 开发，`SymPy` 是 `an open-source Python library for symbolic computation.` 它作为独立应用和/或作为库以及通过 `SymPy Live` 或 `SymPy Gamma` 在线应用，为其他应用提供代数计算能力。 `SymPy` 易于安装和测试，因为它完全用 Python 开发，依赖有限。 `SymPy` 涉及从微积分、代数、离散数学和量子物理到基本符号算术的特性。 计算结果可以格式化为 `LaTeX` 代码。 结合在广泛使用的编程语言中简单、可扩展的代码库，`SymPy` 提供的易用性使其成为一个入门门槛相对较低的计算机代数系统。

### Pandas (数据结构和分析)

`Pandas` 提供高度直观且用户友好的高级数据结构。 `Pandas` 在机器学习算法开发者社区中获得了流行，内置了数据聚合、分组和过滤技术以及时间序列分析结果。 Pandas 库有两个主要结构：一维 `Series` 和二维 `Data Frames.`

下面列出了 `Pandas` 提供的一些关键特性：

* 快速高效的 `Data Frame object`，具有嵌入式索引，可用于数据操作活动。
* 在内部内存数据结构与多种文件格式之间读取和写入数据的工具，例如 `CSV` 和文本，`Microsoft Excel`，`SQL databases`，以及快速 `HDF5 format`。
* 智能数据对齐和对不完整数据的集成管理，通过实现自动标签驱动的计算对齐并轻松将无序数据整理为有序方式。
* 灵活重构和透视数据集。
* 基于标签的智能切片和索引大型数据集，以及创建数据子集。
* 可以向数据结构添加和删除列以实现数据库的所需大小。
* 使用复杂的 `Group By` 系统对数据进行聚合或转换，使其能够在数据上执行 `split-apply-combine` 技术。
* 数据集的高效合并和连接功能。
* `Hierarchical axis indexing` 提供了一种简单的方法，即使在高维数据中也能在低维数据结构中工作。
* 时间序列功能，包括 `date range generation and frequency conversion, moving window statistics, moving window linear regressions, date shifting, and lagging.` 还有 `domain-specific time offsets` 的创建以及在不丢失数据的情况下连接时间序列的能力。
* 由于大部分底层代码使用 `Cython` 或 `C` 编写，Pandas 具有高性能和效率。
* Python 结合 Pandas 被广泛应用于金融服务、统计学、神经生物学、经济学、市场营销和广告、在线数据分析等学术和工业领域。

Pandas 提供的两种数据类型结构为：`Pandas DataFrame` 和 `Pandas Series.`

#### Pandas DataFrame

它被定义为 `2-D labeled data structure with columns of a potentially different type`。 它与 Excel 电子表格非常相似，如下图所示，具有用于分析、修改和从数据中提取有价值见解的多个相似功能。 您可以通过输入来自 `Excel`、`CSV` 和 `MySQL database` 等的数据集来创建 `Pandas DataFrame`。

![](images/00003.jpeg)

例如，在上图中，假设 `Keys` 由列名表示，`Values` 由该列中的项目列表表示。 可以使用 `Python dictionary` 来表示，如下面的代码所示：

```
my_dict = { 
     'name' : ["a", "b", "c", "d", "e","f", "g"],
     'age' : [20,27, 35, 55, 18, 21, 35],
     'designation': ["VP", "CEO", "CFO", "VP", "VP", "CEO", "MD"]}
```

可以使用下面的代码从该字典创建 `Pandas DataFrame`：

```
import Pandas as PD
df = pd.DataFrame(my_dict)
```

生成的 `DataFrame` 如下面图所示，类似于 Excel 电子表格：

![](images/00004.jpeg)

如果您想为行定义索引值，则需要在 `DataFrame ( )` 子句中添加 `index` 参数，如下所示：

```
df = pd.DataFrame(my_dict, index=[1,2,3,4,5,6,7])
```

要获取数据的 `string` 索引而不是数字，请使用下面的代码：

```
df = pd.DataFrame(
     my_dict, 
     index=["First", "Second", "Third", "Fourth", "Fifth", "Sixth", "Seventh"])
```

现在，由于这些索引值是统一的，您可以执行下面的代码以使用 `NumPy arrays` 作为索引值：

```
np_arr = np.array([10,20,30,40,50,60,70])
df = pd.DataFrame(my_dict, index=np_arr)
```

与 `NumPy` 类似，`DataFrame` 的列也是同质的。 您可以使用类似字典的语法或添加列名与 `DataFrame` 来查看列的数据类型，如下面的代码所示：

```
df['age'].dtype    # Dict Like Syntax
df.age.dtype       # DataFrame.ColumnName
df.name.dtype      # DataFrame.ColumnName
```

