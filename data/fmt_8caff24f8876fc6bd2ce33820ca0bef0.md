
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

![](img/00003.jpeg)

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

![](img/00004.jpeg)

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

你可以使用下面的代码通过使用“head ( )”函数查看“Pandas DataFrame”中可用的记录或前五行的前五行，以及使用“tail ( )”函数查看最后五行。例如，要查看数据的最初三行，可以使用下面的代码：

```
df.head(3)   # Display first 3 Rows
```

#### Pandas Series

它可以被定义为“一种能够容纳任何类型数据（一维带标签数组（整数、字符串、浮点数、python 对象））”。简单来说，它就像 Excel 电子表格中的一列。要从数组生成“Pandas Series”，必须导入并使用“NumPy”模块以及“array ()”函数，如下面的代码所示：

```
# import pandas as pd
import pandas as pd
```

```
# import numpy as np
import numpy as np
```

```
# simple array
data = np.array (['m','a','c','h','I','n','e'])
```

```
ser = pd.Series(data)
print(ser)
```

### Seaborn (data visualization)

Seaborn 源自 Matplotlib 库，是一款极受欢迎的可视化库。它是一个高级库，可以生成特定类型的图表，包括热力图、时间序列和箱形图。

### TensorFlow

TensorFlow 可以被定义为一个机器学习平台，提供端到端服务，拥有各种免费和开源资源。它具有多层节点系统，允许快速构建、训练和部署具有大型数据集的人工神经网络。它被誉为“一种简单灵活的架构，可以快速将新想法从概念到代码再到最先进的模型并发表”。例如，Google 在其图像识别和语音识别工具和技术中使用 TensorFlow 库。

更高级别的 API 如 `tf.estimator` 可用于指定预定义架构，例如 `linear regressors` 或 `neural networks.` 下图显示了 TensorFlow 工具包现有的层级结构：

![](img/00005.jpeg)

下图所示的图片提供了不同层级的用途：

![](img/00006.jpeg)

TensorFlow 的两个基本组件是：

1. 一个 `graph protocol buffer`
2. 一个 `runtime` 可以执行图

上面提到的两个组件类似于 `Python` 代码和 `Python interpreter.` 就像 `Python interpreter` 可以在多个硬件系统上运行 Python 代码一样，TensorFlow 可以在各种硬件系统上运行，如 CPU、GPU 和 TPU。

为了决定应使用哪种 API(s)，你必须考虑提供最高抽象级别来解决目标问题的 API。更易于使用，但（按设计）灵活性较低的是更高的抽象级别。建议首先从最高级别的 API 开始，让一切正常工作。如果对于某些独特的建模问题，你需要额外的灵活性，则向下移动一个级别。请注意，每个级别都是建立在较低级别的 API 之上。因此，降低层级应该非常简单。

对于大多数机器学习模型的发展，我们将使用 `tf.estimator` API，这大大减少了开发所需的代码行数。此外，`tf.estimator` 与 Scikit-Learn API 兼容。

![](img/00007.jpeg)

# Chapter 3: Predictive Modeling, Data Visualization and Creation of Training Data Set

## Machine Learning

人工智能是机器具有类人智能的想法的体现，并且能够模仿人类思维处理和学习能力，以适应新输入并在无需人工协助的情况下执行任务。机器学习是人工智能概念不可或缺的一部分。机器学习可以被定义为人工智能技术的一个概念，主要关注机器通过识别数据模式来学习和自我训练的工程能力，以改进底层算法并做出独立决策。机器学习假设现代计算机具有一种能力，可以使用可以轻松定制以满足所需功能性的训练数据集进行训练。机器学习由模式识别技术驱动，其中机器记录并重新审视过去的交互和结果，这些交互和结果被认为与其当前情况一致。鉴于机器需要处理无尽的数据量，并且新数据不断涌入，它们必须能够适应新数据而无需由人类编程，这体现了机器学习的迭代方面。

机器能够通过利用先前的计算和底层算法进行学习和自我训练，从而产生高质量且易于重现的决策和结果。机器学习的概念已经存在数十年，但机器学习算法的最新进展使得机器能够处理和分析大数据成为可能。这是通过以高速和高频率应用高级和复杂的数学计算，使用自动化来实现的。

当今的先进计算机器能够快速分析庞大的数据量并提供更快、更准确的结果。采用机器学习算法的公司具有增强的灵活性，可以修改训练数据集以满足其业务需求并相应地训练机器。这些定制的机器学习算法使企业能够识别潜在风险以及增长机会。机器学习算法通常与人工智能技术和认知技术协同使用，以使机器在处理大量数据或大数据时非常有效和高效，并产生高度准确的结果。

鉴于人工智能和机器学习之间固有的联系，为了使本书更易于理解，我们今后将互换使用“机器学习”和“人工智能”这两个术语。

目前有四种类型的机器学习算法：

### Supervised Machine Learning Algorithms

这些算法广泛用于预测性大数据分析，由于其能够评估并将从先前迭代和交互中学习到的经验应用到新的输入数据集中。例如，人类可以将机器编程为将数据点标记为“R”（运行）、“N”（负）或“P”（正）。机器学习算法将根据编程对输入数据进行标记，并接收具有相应正确输出的数据输入。算法将对其自身生成的输出与“预期或正确”输出进行比较，以识别可以进行的潜在改进和可以修复的错误，以使模型更准确、更智能。

通过应用“回归”、“预测”、“分类”和“成分提升”等方法来很好地训练机器学习算法，任何新的输入数据都可以作为“目标”数据集输入到机器中，以按需编排学习程序。这个“已知的训练数据集”启动了分析过程，其后是学习算法以产生“推断函数”，该函数可用于根据输出值对未来事件进行预测和预测。例如，金融机构和银行严重依赖监督式机器学习算法来检测欺诈性信用卡交易并预测潜在信用卡客户未能按时支付信用卡款项的可能性。

### Unsupervised Machine Learning Algorithms

公司经常遇到需要生成标记和分类的训练数据集的数据源不可用的情况。在这些情况下，使用无监督机器学习算法是理想的。无监督机器学习算法用于识别机器如何创建“推断函数”以从未标记和未分类的数据堆中阐明隐藏结构的方法。这些算法能够探索数据以在信息量中识别结构。

与监督机器学习算法不同，无监督算法在识别正确输出方面失败，尽管它们在探索输入数据和进行推断方面与监督学习算法一样高效。这些算法可用于识别数据异常值、生成定制和个性化产品推荐，以及使用诸如 `self-organizing maps`、`singular value decomposition` 和 `k-means clustering` 等技术对文本主题进行分类。例如，识别具有共同购物属性的客户，可将其细分为特定群体，并针对其实施相似的营销策略和活动。因此，无监督学习算法在在线营销领域极受欢迎。

### 半监督机器学习算法

半监督机器学习算法具有高度的通用性，能够利用标记和未标记数据集进行学习和自我训练。这些算法是监督学习和无监督学习算法的“混合”。通常，训练数据集主要由未标记数据组成，并包含少量标记数据。分析方法包括 `prediction`、`regression` 和 `classification` 与半监督学习算法相结合使用，可使机器显著提高其学习准确性和训练能力。

这些算法广泛用于从原始数据生成标记训练数据集高度资源密集且对公司而言成本效益较低的情况。因此，为了避免额外的人力和设备成本，公司在其系统中使用半监督学习算法。例如，人脸识别应用程序需要大量分散在多个输入源中的人脸数据。从网络摄像头等来源获取的原始数据的预处理、处理、分类和标记需要大量人力，以及数千小时的工作才能用作训练数据集。

### 强化机器学习算法

强化机器学习算法的独特性在于它从环境中学习。这些算法执行操作并勤勉地记录每次操作的结果，该结果要么是失败导致错误，要么是成功执行后的奖励。区分强化学习算法的两个主要特征是 `trial and error` 研究方法和 `delayed reward`。机器通过使用各种计算反复分析输入数据，并为每次正确或预期的输出发送强化信号，最终优化最终结果。系统开发了简单的动作和奖励反馈循环，以评估、记录和学习哪些操作是成功的并在更短时间内导致准确结果。这些算法的使用使系统能够在特定上下文的约束条件下自动确定理想行为，从而提高其能力和最大化其性能。因此，强化机器学习算法在游戏行业、机器人工程以及导航系统中被广泛使用。

## 大数据分析 vs. 机器学习

`Machine learning`、`Big Data` 以及 `Big Data Analytics` 都属于 `Artificial Intelligence` 技术范畴，而后者归入 `Data Science` 领域。以下是机器学习与大数据或大数据分析之间的一些关键区别：

### 应用
