
# 机器学习精要：R 实用指南

## Preface

### 0.1 What you will learn

每天在不同的领域，包括营销、生物医学和安全，都会记录大量数据。为了从这些数据中发现知识，你需要机器学习技术，它们可分为两类：

1. **无监督机器学习方法**：

这些方法主要包括 *聚类* 和 *主成分分析* 方法。聚类的目标是在感兴趣的数据集中识别模式或相似对象的组。主成分方法包括总结和可视化多变量数据集中包含的最重要信息。

这些方法之所以称为“无监督”，是因为我们没有事先的想法来指导哪些变量或样本属于哪些聚类或组。机器算法“学习”如何对数据进行聚类或汇总。

2. **监督机器学习方法**：

监督学习包括为预测未来观察结果的结局构建数学模型。预测模型可分为两大类：

* *回归分析* 用于预测连续变量。例如，你可能想根据社会经济指标预测预期寿命。

* *分类* 用于预测个体的类别（或组）。例如，你可能想根据患者的血浆葡萄糖浓度预测其患糖尿病的概率。

这些方法之所以称为监督，是因为我们基于已知的结局值构建模型。也就是说，机器从已知的观察结果中学习，以便预测未来案例的结果。

在本书中，我们提供了探索数据集以及构建预测模型的机器学习方法的实用指南。

你将学习每种方法的基本思想以及可重复的 R 代码，以便轻松计算大量机器学习技术。

### 0.2 Key features of this book

我们的目标是为每个人编写一份机器学习实用指南。

本书的主要部分包括：

* **无监督学习方法**，使用聚类和主成分方法探索和发现大型多变量数据集中的知识。你将学习层次聚类、k-means、主成分分析和对应分析方法。

* **回归分析**，使用线性回归和非线性回归策略预测定量结果值。

* **分类技术**，使用逻辑回归、判别分析、朴素贝叶斯分类器和支持向量机预测定性结果值。

* **高级机器学习方法**，使用 k-最近邻方法、决策树模型、集成方法（装袋、随机森林和提升）构建稳健的回归和分类模型

* **模型选择方法**，自动选择构建最优预测模型的预测变量的最佳组合。这些包括最佳子集选择方法、逐步回归和惩罚回归（岭回归、套索回归和弹性网络回归模型）。我们还介绍了基于主成分的回归方法，当数据包含多个相关的预测变量时很有用。

* **模型验证和评估技术** 用于衡量预测模型的性能。

* **模型诊断** 用于检测和修复预测模型中的潜在问题。

本书介绍了这些任务的基本原理并提供了 R 中的许多示例。本书为学生和研究人员的数据挖掘提供了坚实的指导。

主要特点：

* 涵盖机器学习算法和实现

* 关键数学概念得以呈现

* 简短、独立的章节，附带实用示例。这意味着你不必按顺序阅读不同章节。

在每章末尾，我们提供了 R 实验部分，在其中我们系统地研究了该章中讨论的各种方法的实际应用。

### 0.3 Book website

[`http://www.sthda.com/english`](http://www.sthda.com/english)

## 1 About the author

Alboukadel Kassambara 是生物信息学和癌症生物学博士。他多年来一直从事基因组数据分析和可视化工作（阅读更多：[`http://www.alboukadel.com/`](http://www.alboukadel.com/) ）。

他在统计和计算方法方面拥有工作经验，用于通过整合分析大规模基因组和临床数据集来识别预后和预测性生物标志物特征。

他创建了一个生物信息学网络工具 GenomicScape（`www.genomicscape.com`），这是一个易于使用的网络工具，用于基因表达数据分析和可视化。

他还开发了一个数据科学培训网站，名为 STHDA（高通量数据分析的统计工具，`www.sthda.com/english`），其中包含许多使用 R 软件和包进行数据分析和可视化的教程。

他是许多流行的 R 包的作者：

* 多变量数据分析（**factoextra**，[`http://www.sthda.com/english/rpkgs/factoextra`](http://www.sthda.com/english/rpkgs/factoextra) ）

* 生存分析（**survminer**，[`http://www.sthda.com/english/rpkgs/survminer/`](http://www.sthda.com/english/rpkgs/survminer/) ）

* 相关性分析（**ggcorrplot**，[`http://www.sthda.com/english/wiki/ggcorrplot-visualization-of-a-correlation-matrix-using-ggplot2`](http://www.sthda.com/english/wiki/ggcorrplot-visualization-of-a-correlation-matrix-using-ggplot2) ）

* 在 R 中创建出版就绪的图表（**ggpubr**，[`http://www.sthda.com/english/rpkgs/ggpubr`](http://www.sthda.com/english/rpkgs/ggpubr) ）。

最近，他出版了几本关于数据分析和可视化的书籍：

1. Practical Guide to Cluster Analysis in R（[`https://goo.gl/yhhpXh`](https://goo.gl/yhhpXh) ）

2. Practical Guide To Principal Component Methods in R（[`https://goo.gl/d4Doz9`](https://goo.gl/d4Doz9) ）

3. R Graphics Essentials for Great Data Visualization（[`https://goo.gl/oT8Ra6`](https://goo.gl/oT8Ra6) ）

4. Network Analysis and Visulization in R（[`https://goo.gl/WBdn4n`](https://goo.gl/WBdn4n) ）

## 2 Introduction to R

R 是一款免费且强大的统计软件，用于分析和可视化数据。

在本章中，你将学习如何安装 R 和所需包，以及如何将数据导入 R。

### 2.1 Install R and RStudio

RStudio 是 R 的集成开发环境，使使用 R 变得更容易。R 和 RStudio 可安装在 Windows、MAC OSX 和 Linux 平台上。

1. R 可从 Comprehensive R Archive Network（CRAN）网页下载和安装（[`http://cran.r-project.org/`](http://cran.r-project.org/) ）

2. 安装 R 软件后，还请安装 RStudio 软件，网址为：[`http://www.rstudio.com/products/RStudio/`](http://www.rstudio.com/products/RStudio/) 。

3. 启动 RStudio 并开始在 R studio 中使用 R。

### 2.2 Install and load required R packages

R 包是一组扩展基础 R 功能的功能集合。为了使用本书提供的 R 代码，你应安装以下 R 包：

* `tidyverse` 用于轻松的数据操作和可视化。

* `caret` 包用于轻松的机器学习工作流程。

1. **Installing packages**：

```
```

3. **Load required packages**. 安装后，你必须先加载包才能使用包中的函数。函数 `library()` 用于此任务。例如，输入以下内容：

```
```

现在，我们可以使用这些包中的 R 函数。

如果你想了解更多关于某个函数的信息，例如 `mean()`，在 R 控制台中输入：`?mean`。

### 2.3 Data format

你的数据应为矩形格式，其中列为变量，行为观察值（个体或样本）。

* 列名应与 R 的命名规范兼容。避免列名中包含空白字符和特殊字符。好的列名：`long_jump` 或 `long.jump`。不好的列名：`long jump`。

* 避免以数字开头列名。请改用字母。好的列名：`sport_100m` 或 `x100m`。不好的列名：`100m`。

* 用 `NA` 替换缺失值（表示 not available）

例如，你的数据应如下所示：

```
    Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
44           5.0         3.5          1.6         0.6     setosa
118          7.7         3.8          6.7         2.2  virginica
61           5.0         2.0          3.5         1.0 versicolor
130          7.2         3.0          5.8         1.6  virginica
```

阅读更多内容：[将数据文件导入 R 的最佳实践](http://www.sthda.com/english/wiki/best-practices-in-preparing-data-files-for-importing-into-r)

### 2.4 在 R 中导入你的数据

首先，将你的数据保存为 txt 或 csv 文件格式并按如下方式导入它（你将被要求选择文件）：

```

```

阅读有关如何将数据导入 R 的更多信息，请访问此链接：[`www.sthda.com/english/wiki/importing-data-into-r`](http://www.sthda.com/english/wiki/importing-data-into-r)

### 2.5 示例数据集

R 附带了多个用于练习 R 函数的示例数据集。最常用的 R 示例数据集包括 `iris`。要加载示例数据集，请使用函数 `data()` 如下。函数 `head()` 用于检查数据。

```

```

```
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 1          5.1         3.5          1.4         0.2  setosa
## 2          4.9         3.0          1.4         0.2  setosa
## 3          4.7         3.2          1.3         0.2  setosa
```

要了解更多关于 iris 数据集的信息，输入以下内容：

```

```

输入上述 R 代码后，你将看到 `iris` 数据集的描述。

### 2.6 数据操作

在 R 中导入数据后，你可以使用 [`tidyverse` 包](http://r4ds.had.co.nz/transform.html)轻松操作它。

加载 tidyverse 后，你可以使用以下 R 函数：

* `filter()` : 根据其值挑选行（观测值/样本）。

* `distinct()` : 删除重复行。

* `arrange()` : 重新排序行。

* `select()` : 按名称选择列（变量）。

* `rename()` : 重命名列。

* `mutate()` : 添加/创建新变量。

* `summarise()` : 计算统计摘要（例如计算均值或总和）

* `group_by()` : 对数据集的子集进行操作。

请注意，tidyverse 包允许使用前向管道链式操作符（`%>%`）来组合多个操作。例如，`x %>% f` 等价于 `f(x)`。使用管道（`%>%`），每个操作的输出会传递给下一个操作。这使得 R 编程变得简单。

阅读更多内容：[`r4ds.had.co.nz/transform.html`](http://r4ds.had.co.nz/transform.html)。

### 2.7 数据可视化

R 中有不同的图形包可用于可视化你的数据。在本书中，我们主要使用属于 tidyverse 包的 `ggplot2` 系统来创建图形。

如果你是 `ggplot2` 的初学者，请阅读我们的教程 [R Graphics Essantials](http://www.sthda.com/english/articles/32-r-graphics-essentials/)。

### 2.8 关闭你的 R/RStudio 会话

每次关闭 R/RStudio 时，系统会询问你是否要保存 R 会话中的数据。如果你决定保存，数据将在未来的 R 会话中可用。

## 3 引言

`Regression analysis`（或 `regression model`）由一组 *machine learning* 方法组成，允许我们基于一个或多个预测变量（`x`）的值来预测连续结果变量（`y`）。

简而言之，回归模型的目的是建立一个数学方程，将 `y` 定义为 `x` 变量的函数。接下来，该方程可用于基于预测变量（`x`）的新值来预测结果（`y`）。

`Linear regression` 是预测连续变量最简单、最流行的技术。它假设结果与预测变量之间存在线性关系。参见第 4 章。

线性回归方程可以写成 `y = b0 + b*x`，其中：

* `b0` 是截距，

* `b` 是与预测变量 `x` 相关的回归权重或系数。

从技术上讲，线性回归系数是这样确定的，使得预测结果值的误差最小化。这种计算 beta 系数的方法称为 `Ordinary Least Squares` 方法。

当你有多个预测变量时，例如 `x1` 和 `x2`，回归方程可以写成 `y = b0 + b1*x1 + b2*x2`。在某些情况下，一些预测变量之间可能存在 `interaction effect`，也就是说，例如，增加预测变量 `x1` 的值可能会提高预测变量 `x2` 在解释结果变量变化方面的有效性。参见第 5 章。

还要注意，线性回归模型可以同时包含连续和 `categorical predictor variables`。参见第 6 章。

当你构建线性回归模型时，你需要 `diagnostic` 线性模型是否适合你的数据。参见第 9 章。

在某些情况下，结果与预测变量之间的关系不是线性的。在这些情况下，你需要构建 `non-linear regression`，例如 *polynomial and spline regression*。参见第 7 章。

当回归模型中有多个预测变量时，你可能希望选择最佳的预测变量组合来构建最佳预测模型。此过程称为 `model selection`，包括比较包含不同预测变量集的多个模型，以便选择性能最佳且预测误差最小的模型。线性模型选择方法包括 `best subsets regression`（第 17 章）和 `stepwise regression`（第 18 章）

在某些情况下，例如在基因组学领域，你可能拥有包含一些相关预测变量的大型多变量数据集。在这种情况下，原始数据集中的信息可以汇总为少数新变量（称为主成分），它们是原始变量的线性组合。这些少数主成分可用于构建线性模型，这可能对你的数据更有效。这种方法被称为 `principal component-based methods`（第 20 章），其中包括：`principal component regression` 和 `partial least squares regression`。

简化大型多变量模型的另一种方法是使用 `penalized regression`（第 19 章），它对模型拥有过多变量进行惩罚。最著名的惩罚回归包括 `ridge regression` 和 `lasso regression`。

你可以将所有这些不同的回归模型应用于你的数据，比较模型并最终选择解释数据良好的最佳方法。为此，你需要一些统计指标来比较不同模型在解释数据和预测新测试数据结果方面的性能。

最佳模型被定义为预测误差最低的模型。比较回归模型最流行的指标包括：

**均方根误差**，用于衡量模型预测误差。它对应于结果的观测已知值与模型预测值之间的平均差异。`RMSE` 计算为 `RMSE = mean((observeds - predicteds)²) %>% sqrt()`。`RMSE` 越低，模型越好。

**调整后 R 平方**，表示数据中变异（即信息）的比例由模型解释。这对应于模型的整体质量。调整后 `R2` 越高，模型越好

请注意，以上提到的指标应在未用于训练（即构建）模型的新的测试数据上计算。如果您有一个包含大量记录的大型数据集，可以随机将数据拆分为训练集（用于构建预测模型，80%）和测试集或验证集（用于评估模型性能，20%）。

估计模型性能最稳健且最流行的方法之一是 **k 折交叉验证**。即使在小数据集上也可以应用。k 折交叉验证的工作方式如下：

1. 随机将数据集拆分为 k 个子集（或 k 折）（例如 5 个子集）

2. 保留一个子集并在所有其他子集上训练模型

3. 在保留的子集上测试模型并记录预测误差

4. 重复此过程，直到 k 个子集中的每一个都作为测试集使用。

5. 计算记录的 k 个误差的平均值。这称为交叉验证误差，作为模型的性能指标。

综合起来，最佳模型是交叉验证误差最低、`RMSE` 最低的模型。

在本部分中，您将学习回归分析的不同方法，我们将在 **R** 中提供实际示例。以下技术进行了描述：

* 普通最小二乘

    * 简单线性回归

    * 多元线性回归

* 模型选择方法：

    * 最佳子集回归（Chapter 17）

    * 逐步回归（Chapter 18）
