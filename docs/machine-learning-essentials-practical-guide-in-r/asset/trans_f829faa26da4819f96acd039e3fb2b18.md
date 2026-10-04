

![](Image00052.jpg)

Alboukadel KASSAMBARA

# Machine Learning Essentials

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

