

## 2.9 Bookdown

![](img/2bc6b006fe018e0018b86f206ab98644_41_0.png)

两本书的示例，它们既可以在 Bookdown 网站上免费访问，也可以以实体书的形式提供。

RStudio Cloud 上有很多资源。例如，在 YouTube 频道上，有教育版 RStudio Cloud https://www.youtube.com/watch?v=PviVimazpz8。YouTube 上的另一个优质资源是在云端使用 R 语言 https://www.youtube.com/watch?v=SFpzr21Pavgg

为了获取进一步的指导和帮助，用户可以注册并加入 RStudio Community³。用户还可以在 Stack Overflow⁴ 上提问。此外，还有特定主题的邮件列表组，但用户必须自行订阅它们。

RStudio 提供了一个网站来托管在线书籍，即 Bookdown⁵。Bookdown 上的书籍可以免费在线访问。有些书籍可以在亚马逊或其他或其他书店以实体书的形式出售，我们的书也是一样。

- ³https://community.rstudio.com/
- ⁴https://stackoverflow.com/
- ⁵https://bookdown.org/

## 2.10 总结

在本章中，我们描述了 R 脚本和 R 包。我们还展示了如何编写简单的 R 脚本，如何检查机器上是否有某个特定的 R 包，以及在如果没有时如何安装它。如果你是 R 语言初学者，我们建议使用 RStudio Cloud。工作目录有时会让新 R 用户感到困惑，因此我们也建议所有 R 用户为新的分析任务创建新的 RStudio 项目（Project）。有很多离线和在线资源可供，其中许多资源可以免费访问，特别是在 Bookdown⁶ 网站。

## 3 RStudio Project

在本章结束时，我们希望读者能够：

- 将他们的 RStudio 与我们的数据集关联。数据集存储在我们的 GitHub 仓库中。
- 使用我们的 GitHub 仓库创建一个 RStudio Cloud 项目。
- 使用我们的 GitHub 仓库在本地机器创建一个 RStudio 项目。

在本章中，我们将引导你建立一个与本书项目相似的文件夹和文件结构。这种文件夹和文件结构将帮助你以最小的错误风险运行代码。此外，为了实现这一点，我们将使用 RStudio Project。

在 RStudio Project 网页¹上，提到 RStudio 项目可以简单方便地将你的工作划分为多个上下文，每个上下文都有自己的工作目录、工作空间、历史记录和源文档。RStudio 项目与 R 工作目录相关。你可以创建一个 RStudio 项目：

- 在 RStudio Cloud 或你本地机器上的 RStudio 上。
- 在全新的目录中。
- 在已有 R 代码和数据的现有目录中。
- 通过克隆版本控制（Git 或 Subversion）仓库。

> ¹https://support.rstudio.com/hc/en-us/articles/20052607-Using-RStudio-Projects

## 3 RStudio Project

![](img/2bc6b006fe018e0018b86f206ab98644_44_0.png)

图 3.1
GitHub 上的数据集仓库。

![](img/2bc6b006fe018e0018b86f206ab98644_44_1.png)

图 3.2
RStudio Cloud。

## 3.3 Dataset Repository on GitHub

我们将使用包含本书数据集的 GitHub 仓库。仓库的名为 data-for-RMed。要进入仓库，请点击此链接²

> ²https://github.com/drkamarul/multivar_data_analysis.git

## 3.4 RStudio Project on RStudio or Posit Cloud

![](img/2bc6b006fe018e0018b86f206ab98644_45_0.png)

图 3.3
RStudio Cloud 登录页。

![](img/2bc6b006fe018e0018b86f206ab98644_45_1.png)

图 3.4
Rstudio Cloud、工作空间（Workspace）和新项目（New Project）。

![](img/2bc6b006fe018e0018b86f206ab98644_45_2.png)

图 3.5
来自 Git 仓库的新项目。

## 3.4 RStudio Project on RStudio or Posit Cloud

Rstudio 现在被称为 Posit Cloud。通过 RStudio 和 Posit Cloud，你可以轻松方便地访问 RStudio IDE。在本节中，我们将向你展示如何从我们 GitHub 上的书籍仓库复制一个 RStudio 或 Posit Cloud 项目。我们建议你遵循以下步骤：

![](img/2bc6b006fe018e0018b86f206ab98644_46_0.png)

图 3.6
将数据集仓库克隆到 RStudio Cloud。

![](img/2bc6b006fe018e0018b86f206ab98644_46_1.png)

图 3.7
通过粘贴 HTTPS 链接将 GitHub 仓库克隆到 RStudio 或 Posit Cloud。

- 进入你的 RStudio Cloud 页面。
- 接下来，使用你的凭据登录 RStudio 或 Posit Cloud。
- 进入工作空间后，点击 **New Project**（新项目）。
- 点击 **New Project from Git**（来自 Git 的新项目）。

## 3.4 RStudio Project on RStudio or Posit Cloud

![](img/2bc6b006fe018e0018b86f206ab98644_47_0.png)

图 3.8
一个新的 RStudio Cloud 项目。

![](img/2bc6b006fe018e0018b86f206ab98644_47_1.png)

图 3.9
你机器上的 RStudio。

- 在点击 New Project 后，返回我们 GitHub 上的 data-for-RMed 仓库。
- 点击 **Clone**（克隆）。
- 点击 HTTPS。
- 粘贴 HTTPS 链接。
- 你已将仓库克隆到 RStudio 或 Posit Cloud。

## 3.5 RStudio Project on Machine

![](img/2bc6b006fe018e0018b86f206ab98644_48_0.png)

图 3.10
一个新的 RStudio Cloud 项目。

![](img/2bc6b006fe018e0018b86f206ab98644_48_1.png)

图 3.11
你机器上的 RStudio。

- 在点击 New Project 后，返回我们 GitHub 上的 data-for-RMed 仓库。
- 点击 **Clone**。
- 点击 HTTPS。
- 粘贴 HTTPS 链接。
- 你已将仓库克隆到 RStudio 或 Posit Cloud。

这些是本地机器上的 RStudio 项目。

![](img/2bc6b006fe018e0018b86f206ab98644_49_0.png)

图 3.12
项目向导。

![](img/2bc6b006fe018e0018b86f206ab98644_49_1.png)

图 3.13
来自 Git。

- 启动你的 RStudio IDE。
- 在菜单中，点击 **File**，然后点击 **New Project**。
- 接下来，点击 **Project**，然后点击 **Version Control**。
- 之后，点击 **Git**。
- 正如你之前在步骤中复制了 GitHub 链接，这里也一样；从 **data-for-RMed** 仓库复制。

![](img/2bc6b006fe018e0018b86f206ab98644_50_0.png)

图 3.14
克隆仓库。

![](img/2bc6b006fe018e0018b86f206ab98644_50_1.png)

图 3.15
RStudio 项目。

- 现在，你可以粘贴 HTTPS 链接（参见图 3.14）。你会发现项目目录将自动填充。
- 接下来你可以点击 **Browse**（浏览），以便选择你喜欢的任何文件夹作为工作目录。

如果你使用的是 Windows 操作系统，我们建议使用主目录（例如 **Documents**）。

你会发现 RStudio 将在你的本地机器上创建一个新目录。该工作目录包含了与我们的 仓库相同的文件夹和文件结构：

## 3.6 Summary

在本章中，我们向读者展示了如何设置 R 环境，以便他们的 RStudio 工作目录产生与我们相同的文件夹和文件结构。通过这种策略，我们将最大限度地减少读者在使用书中的 R 代码时产生的错误。我们还展示了数据集的位置。它们最初存储在本书的 GitHub 仓库中。然后我们为读者提供了说明，让他们能够在 Posit Cloud（原 RStudio Cloud）远程以及在本地机器的 RStudio IDE 上创建新的 RStudio 项目。

![](img/2bc6b006fe018e0018b86f206ab98644_52_0.png)

## 4 Data Visualization

在本章中，读者将：

- 了解数据可视化概念
- 理解良好图表的要素
- 能够使用 ggplot 包生成图表
- 能够以不同的格式和图形设置保存图表

在我们的实体书中，图表将以黑白文字出版。因此，ggplot2 自带的某些 R 代码将包含一行额外的代码，例如 `scale_colour_grey() + scale_line_grey()`，以确保图表适合我们实体书内部的黑白文字。我们书在书网站上的在线版本¹将以彩色显示图表。

