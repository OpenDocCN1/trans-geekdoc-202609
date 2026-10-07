
如果 $x_i$ 是数据集中的最小值，则该值变为 0。如果 $x_i$ 是数据集中的最大值，则该值变为 1。这种技术将不同变量缩放到 0 到 1 的范围，这非常有用。

# Z 分数归一化 (Z-Score Normalization)

Z-score 使用平均值 $\bar{x}$ 和标准差 $s$ 来缩放变量 $x$：

$$z_i = \frac{x_i - \bar{x}}{s}$$

生成的 Z-score 表示数据点偏离平均值的多少个标准差。在图 4.8 中，你可以看到经过 Z-score 缩放的训练数据集。

![](img/f240d449191f5add983daf6c380e4fe3_92_0.png)

**图 4.8** Z 归一化变量酸度和硫

Z-score 归一化保留了数据的分布，并且不依赖于最大值最小值。这些属性使得 Z-score 归一化成为在用于 `k-最近邻` 之前缩放变量的良好选择。

# 4.7 使用 Tidymodels 进行 k-最近邻分析

本节将使用 R 和 k-最近邻模型仅根据两种化学属性（酸度和硫）对葡萄酒进行分类。在第 4.9 节中，你将参与一个交互项目并使用更多属性扩展分析。

## 4.7.1 tidymodels 包

在本书的后续章节中，我们将利用 R `tidymodels` 包进行分析。在开发第一个机器学习模型之前，我们将提供该包的简要概述。

`tidymodels` 包为各种机器学习模型和数据工程任务提供了具有标准语法的工作流。这避免了每次使用新模型时都要学习新的命令和工作流。

- 将观测值随机划分为训练和测试的 `recipes`（配方）。
- 使用 `recipes` 预处理数据——每个 `recipe` 包含一个或多个 `step_commands`，以完全相同的方式处理训练和测试数据。这些 `step_commands` 可用于各种任务。例如，用于 Z 归一化的 `step_naomit()`，可以使用 `step_normalize()`。你可以在此处找到数据处理步骤的列表：https://tidymels.org/find/recipes/
- 仅使用标准化命令创建机器学习模型设计。在编写本书时，Tidymodels 支持超过 40 种不同的模型。与其单独构建和编码这些模型，不如 `tidymodels` 包对现有的机器学习包及其模型进行了封装。封装器在内部将 `tidymodels` 命令翻译为相关包所需的代码，然后执行模型。你可以在此处找到可用模型列表：https://www.tidymodels.org/find/parnip/#models

## 4 k-近邻算法 — 入门

接下来的章节将涵盖所有这些任务，参数调优除外，后者将在第 6 章中详细介绍。

`tidymodels` 的开发者 Kuhn 和 Silge 提供了一份关于 `tidymodels` 及其功能和设计理念的全面指南（参见 Kuhn and Silge (2023)）。

### 4.7.2 加载与划分数据

在下面的代码块中，我们首先从加载所需的 R 包 `rio` 和 `tidymodels` 开始。

请注意，`tidymodels` 是一个包含许多包的元包（meta-package），因此通常不需要单独加载 `tidymverse` 包。

加载这些包后，我们使用与第 4.5 节中相同的葡萄酒数据集，并仅选择预测变量 `TotalSulfurDioxide`（重命名为 `Sulfur`）和 `Acidity` 来预测结果 `WineColor`（参见 `import()` 和 `select()`）。

许多执行分类的机器学习模型（包括 k-近邻算法）要求结果必须是 R 因子变量（关于 R 因子变量的详情请参见第 3.5.1 节）。在数据集中，`WineColor` 是字符变量。因此，我们必须使用 `mutate` 和 `factor()` 将 `WineColor` 转换为因子变量：

```r
library(rio); library(janitor); library(tidymodels)
DataWine<-import("https://ai-analytics.com/data/WineData.rds") |
 clean_names("upper_camel") |
 select(WineColor,TotalSulfurDioxide, Acidity) |
 mutate(WineColoras_factor, factor(WineColor))
```

|  | WineColor | Sulfur | Acidity |
|---|---|---|---|
| 1 | red | 37 | 18.8 |
| 2 | white | 213 | 6.4 |
| 3 | wine | 139 | 9.4 |
| 4 | white | 90 | 8.2 |
| 5 | white | 183 | 6.4 |
| 6 | red | 38 | 6.7 |

在导入葡萄酒数据并选择分析变量后，我们需要将数据集划分为训练集和测试集。在下面的代码中，我们首先通过 `set.seed(876)` 初始化随机数生成器，以确保随机化过程的可重复性。我们使用 `initial_split()` 命令来定义划分方式。通过设置 `prop=0.7`，

## 4.7 使用 Tidymodels 进行 k-近邻算法

R 将随机将 70% 的观测值分配到训练集，其余部分分配到测试集。参数 `strata=WineColor` 使用 `WineColor` 作为分层变量，以确保红酒和白葡萄酒在训练和测试数据中的比例一致。

最后，我们从 R 对象 `Split7030` 中提取训练数据和测试数据，并将其分别赋值给 `DataTrain` 和 `DataTest`：

```r
set.seed(8786)
Split7030 <- initial_split(DataWine, prop=0.7, strata=WineColor)
DataTrain=training(Split7030)
DataTest=testing(Split7030)
```

|  | WineColor | Sulfur | Acidity |
|---|---|---|---|
| 1 | red | 37 | 18.8 |
| 2 | red | 38 | 6.7 |
| 3 | red | 12 | 7.5 |
| 4 | red | 25 | 7.1 |
| 5 | red | 114 | 8.0 |
| 6 | red | 66 | 7.6 |

上方打印了 `DataTrain` 的前几记录供参考。如果你想查看将数据集划分为训练集和测试集的细节，请前往第 4.3 节。

请记住，我们需要初始化 R 的随机数生成器，以确保每次运行代码时随机生成的训练集和测试集都是相同的（更多详情请参见第 4.3 节）。

在本节以及整本书中，我们将使用 `tidymodels` 包中的 `recipes` 来对数据进行预处理。这将简化数据预处理过程，并清晰地展示预处理结构。

你可以将 `tidymodels` 的 `recipe` 比作食谱中的菜谱。首先列出配料，然后找到使用这些配料烹饪菜肴的步骤。

```r
RecipeWine=recipe(WineColor=Acidity+Sulfur, data=DataTrain) |
step_normalize(all_predictors())
step_naomit()
```

类似的，`tidymodels` 的 `recipe` 以 `recipe()` 命令开始，该命令选取了分析中使用的所有变量（配料）。结果变量通过波浪号 (`~`) 与预测变量隔开。为了区分不同的预测变量，使用了加号 (`+`)。必须理解的是 `+` 号与任何类型的加法运算无关，它仅用作分隔预测变量的符号。

第二个 `tidymodels` 的 `recipe` 以 `recipe()` 命令开始，该命令选取了分析中使用的所有变量（配料）。结果变量通过波浪号 (`~`) 与预测变量隔开。为了区分不同的预测变量，使用了加号 (`+`)。必须理解的是 `+` 号与任何类型的加法运算无关，它仅用作分隔预测变量的符号。

第二个 `tidymodels` 的 `recipe` 以 `recipe()` 命令开始，该命令选取了分析中使用的所有变量（配料）。结果变量通过波浪号 (`~`) 与预测变量隔开。为了区分不同的预测变量，使用了加号 (`+`)。必须理解的是 `+` 号与任何类型的加法运算无关，它仅用作分隔预测变量的符号。

第二个 `tidymodels` 的 `recipe` 以 `recipe()` 命令开始，该命令选取了分析中使用的所有变量（配料）。结果变量通过波浪号 (`~`) 与预测变量隔开。为了区分不同的预测变量，使用了加号 (`+`)。必须理解的是 `+` 号与任何类型的加法运算无关，它仅用作分隔预测变量的符号。

必须理解的是 `+` 号与任何类型的加法运算无关，它仅用作分隔预测变量的符号。

```r
RecipeWine=recipe(WineColor=Acidity+Sulfur, data=DataTrain) |
step_normalize(all_predictors())
step_naomit()
```

第二个 `tidymodels` 的 `recipe` 以 `recipe()` 命令开始，该命令选取了分析中使用的所有变量（配料）。结果变量通过波浪号 (`~`) 与预测变量隔开。为了区分不同的预测变量，使用了加号 (`+`)。必须理解的是 `+` 号与任何类型的加法运算无关，它仅用作分隔预测变量的符号。
