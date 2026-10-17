
# 全面 R 网络 (Comprehensive R Network)

## 下载并安装

基础系统和贡献包的预编译发行版，Windows 和 Mac 用户可能想要以下 R 版本之一：

- 下载 Linux 版本 (Fedor/RadHat, Ubuntu)
- 下载 Windows 版本

无论你使用什么平台，你都应该检查你的 R 软件包管理系统，以便将它们添加到下面的链接中。

### 所有平台的源代码

除非你想下载上方方框中列出的预编译二进制文件，否则源代码在使用的之前需要进行编译。如果你不知道该做什么，那你可能就不不想这样做！

最新版本是 2021-05-11 (Camp Petersen)。R 4.1.0 已经发布，请查看最新版本的更新内容。

alpha 和 beta 版本的来源（每日快照，仅在发布前的期间创建）。在提交功能请求或日志报告之前，请阅读我们的新功能和已知修复问题。

旧版本 R 的源代码在此可用。

### 贡献扩展包

关于 R 的问题

如果你对 R 有疑问，例如你想如何下载和安装软件，或者许可条款是什么，请在发送电子邮件之前阅读我们的支持和常见问题解答。

## 1.6 CRAN 网站。

![](img/2bc6b006fe018e0018b86f206ab98644_23_1.png)

## 1.7 RStudio 网站。

### 1.7.3 检查 R 和 RStudio 安装情况

现在，假设你已经安装了 R 和 RStudio。为了确保它们运行完美（或至少第一次运行），请检查：

- 你的机器加载 R 吗？根据你的操作系统，并启动 R。
- 你使用的是什么版本的 R？当 R 加载时，查看 R 的版本。
- 你有 RStudio 吗？根据你的操作系统，并启动 RStudio。

![](img/2bc6b006fe018e0018b86f206ab98644_24_0.png)

### 图 1.8

R Markdown。

- 你使用的是什么版本的 RStudio？当 RStudio 加载时，查看 R 的版本。如果你有多个 R 版本，可以通过进入 Tools（工具）、Global Options（全局选项）然后 General（常规）来选择你需要的 R 版本。
- 你需要更新 R 和 RStudio 吗？通过了解 R 和 RStudio 的版本，现在你知道是否需要更新两者或其中一个。

根据经验，随着 R 用户开发 R 技能，他们可能会发现将分析转换为 PDF 文档是很有吸引力的。如果他们想将在 R 中生成的输出转换为 PDF 格式，就有必要安装 LaTeX 编辑器。然而，如果他们不需要生成 PDF 文档，就不必安装。如果他们需要更大的灵活性来编辑 LaTeX 代码，他们可能会获取 MiTeX、MacTeX 或 Tex Live 等常见的 LaTeX 编辑器。

我们鼓励用户安装 TinyTeX。如果你只需要通过 TinyTeX 将你的 R 文档渲染为 PDF，那就足够了。要安装 TinyTeX，请遵循 `https://yihui.org/tinytex/` 的说明。对于 R 用户，只需运行这两个代码 `install.packages('tinytex')` 和 `tinytex::install_tinytex()` 即可完成安装。

如果你的机器使用的是 Windows 系统，请安装 MiTeX 作为你的 LaTeX 编辑器。如果你使用 macOS，请安装 MacTeX。

## 1.8 启动 RStudio

![](img/2bc6b006fe018e0018b86f206ab98644_25_0.png)

图 1.9

MiTeX 网页。

![](img/2bc6b006fe018e0018b86f206ab98644_25_1.png)

图 1.10

MacTeX 网页。

### 1.8 启动 RStudio

你可以登录 RStudio Cloud 并自动看到 RStudio 界面，或者通过加载它在本地机器上启动 RStudio。记住，要登录 RStudio Cloud，请访问 `https://rstudio.cloud`。会被要求输入用户名和密码。

点击此链接³

在你的机器上启动 R，如果你正在使用 Windows，在机器的开始栏中找到 RStudio 界面并启动它。你将看到一个像这样的界面

> ³`https://rstudio.cloud/spaces/156361/join?access_code=WtlXNuTM%2F7z7%2BBLb%2BFW2XnOw480%2BBTMmL4B%2FqYIR1g`

![](img/2bc6b006fe018e0018b86f206ab98644_26_0.png)

### 图 1.11

本书使用的 RStudio 云端。

![](img/2bc6b006fe018e0018b86f206ab98644_26_1.png)

### 图 1.12

带有 Vibrant Ink 主题的 RStudio 界面。

此界面与你在屏幕上看到的不同，因为我使用了 Vibrant Ink 主题。要选择你喜欢的主题，点击 Global Options，然后点击 Appearance（外观）。有几个主题供你选择。

你现在在 RStudio 上看到了什么？如果你第一次启动 RStudio，你应该看到三个面板；如果你以前用过 RStudio，你应该看到四个面板。

在 Console（控制台）选项卡中，我们将看到大部分从 RStudio 中的代码中生成的结果。

![](img/2bc6b006fe018e0018b86f206ab98644_27_0.png)

图 1.13

RStudio 面板。

![](img/2bc6b006fe018e0018b86f206ab98644_27_1.png)

图 1.14

Console 选项卡。

#### 1.8.2 文件、图形、包和帮助面板

在这个控制台中，你将看到：

- 对象的列表（记住，R 是面向环境的）
- 文件、数据集、帮助等。

## 1.9 R 和 RStudio Cloud

| Files (文件) | Plots (绘图) | Packages (包) | Viewer (查看器) |
| :--- | :--- | :--- | :--- |
| New (新建) | | | |
| Open (打开) | | | |
| Delete (删除) | | | |
| Rename (重命名) | | | |
| Size (大小) | | | |
| Modified (修改) | | | |
| Search (搜索) | | | |
| Help (帮助) | | | |
| Console (控制台) | | | |
| Environment (环境) | | | |
| Build (构建) | | | |
| Restart (重启) | | | |
| Clear (清除) | | | |
| Install (安装) | | | |
| More (更多) | | | |
| Help (帮助) | | | |

![](img/2bc6b006fe018e0018b86f206ab98644_28_0.png)

图 1.15

环境、历史和构建。

在环境、连接和构建中，你将看到

在 Source（源代码）面板中，你将看到

![](img/2bc6b006fe018e0018b86f206ab98644_29_0.png)

图 1.16

Source 面板。

## 1.9 总结

在本章中，我们学习了 R、RStudio 和 IDE。

我们介绍了：

- 编写简单的脚本
- 理解 R 包
- 安装 R 包
- 创建新的 R 项目

## 2 脚本与 R 包

![](img/2bc6b006fe018e0018b86f206ab98644_34_0.png)

### 拟合线性模型

描述

`lm` 用于拟合线性模型。它可以用于方差和协方差的简单回归分析（尽管 R 可能为这些分析提供更方便的接口）。

用法

```
lm(formula, data, subset, weights, na.action,
      method = "qr", x = TRUE, y = FALSE, qr = TRUE,
      singular.ok = TRUE, model = NULL, offset = ...)
```

参数

- `formula`: 一个类为 "formula" 的对象或可以连接到该类的对象；待拟合模型的符号描述。模型规范的细节见“详情（Details）”。
- `data`: 一个可选的数据框、列表或环境（可以强制转换为 data.frame），其中包含要分析的变量。如果未找到，则将从调用 `lm` 的环境中获取变量。
- `subset`: 拟合过程中使用的可选观测子集。
- `weights`: 拟合过程中使用的可选权重向量。应为 `NULL` 或数值向量；如果使用非普通权重，它们必须是正交的。
- `na.action`: 如果数据包含 NA，如何处理缺失值。默认值由选项的 `na.action` 设置，如果未设置则会报错。另一个可能的值是 na.omit，它会忽略包含缺失值的行。
- `method`: 用于拟合模型的方法。仅支持 "qr"；method = "qr" 产生的结果与 method = TRUE 完全相同；见下文。
- `model`: 返回拟合结果的拟合组成部分（模型公式、模型响应变量、残差）。
- `singular.ok`: 如果为 `false`（如果 S 拟合不是奇异拟合），则返回错误。
- `contrasts`: 一个可选列表。参见 `model.matrix.default` 的对比度。
- `offset`: 一个可选向量，用于调整在拟合过程中包含在线性预测器中的响应变量。这应该是数值或长度与用例数量相数值向量。

### 图 2.2

帮助页面。

如果用户想查看某些函数的更详尽指南，可以在函数前输入 `?`。例如，如果用户想更多地了解函数 `lm`，可以输入以下 R 代码。R 将打开一个帮助页面，提供更详细的描述、函数用法以及相关参数。

```
? lm
```

```
# starting httpd server ... done
```

以下是帮助页示例：

## 2.3 包

R 是一种编程语言。此外，R 软件运行在包之上。R 包是由社区开发的函数和数据集构成的集合。

## 2.4 包

![](img/2bc6b006fe018e0018b86f206ab98644_35_0.png)

### CRAN 任务。

通过添加新的代码来改进基础 R 代码和函数，从而增强 R 的功能。

如果用户想组织自己的工作并与他人分享，包是合适的一种组织方式。通常，一个包会包含：

- 代码（有时不仅是 R 代码，还有其他编程语言的代码）
- 包及其内部函数的文档，
- 某些检查一切是否都按预期运行的测试，以及
- 数据集。

用户可以在此处阅读更多关于 R 包的信息。

在编写时，CRAN 包仓库拥有 12784 个包。可用的 R 包列在 CRAN 任务视图（Task Views）网站上。

CRAN 任务视图旨在提供指导，说明 CRAN 上哪些包与特定主题相关的任务相关。它们提供了包含包的简要概述，并可以使用 `ctv view` 自动安装。

这些视图旨在具有明确的焦点，以便清晰地说明包含了哪些包（或排除了哪些包），它们并不是为特定任务推荐“最佳”包。

#### 2.4.2 检查 R 包的可用性

要检查所需的包是否在用户的机器上可用，用户可以在 R 控制台中进行此操作：

```
library(tidyverse)

## -- 挂载核心 tidyverse 包 ------------------------------ tidyverse 2.0.0 -

## v dplyr 1.1.1 v readr 2.1.4
## v forcats 1.0.0 v stringr 1.5.0
## v ggplot2 3.4.2 v tibble 3.2.1
## v lubridate 1.9.2 v tidyr 1.3.0
## v purrr 1.0.1
##                                     Conflicts
tidyverse_conflicts() --
## x dplyr::filter()掩盖了 stats::filter()
## x dplyr::lag()掩盖了 stats::lag()
## i 使用 conflicted 包强制所有冲突变为错误 (<http://conflicted.lib.org/>)。
```

用户不应收到任何错误信息。没有安装该包的用户将收到错误信息。此外，它会告诉他们包在他们的 R 中不可用。默认情况下，包存储在“我的文档”或 HOME 目录下的 R 文件夹中。

```
.libPaths()

## [1] "C:/Users/drkim/AppData/Local/R/win-library/4.2"
## [2] "C:/Program Files/R/R-4.2.3/library"
```

#### 2.4.3 安装 R 包

安装包有两种方法：

1. 从 CRAN
2. 从本地文件或 GitHub

## 图 2.4

![](img/2bc6b006fe018e0018b86f206ab98644_37_0.png)

## 图 2.5

![](img/2bc6b006fe018e0018b86f206ab98644_37_1.png)

## 图 2.6

![](img/2bc6b006fe018e0018b86f206ab98644_38_0.png)

### 2.5 工作目录

工作目录是 R 查找文件和保存输出的文件夹。了解你的工作目录很重要。输入以下命令定位当前工作目录：

```
getwd()
# [1] "C:/Users/drkim/Downloads"
```

#### 2.5.1 启动新项目

启动新项目有两种：

- 从 RStudio IDE
- 使用 `setwd()` 函数设置工作目录

#### 2.5.2 创建新项目

我们强烈建议用户创建新项目。这样做可以转到：

- 文件 -> 新建项目

#### 2.5.3 数据集的位置

许多数据分析师使用存储在本地机器上的数据。R 将读取数据并通常将其存储在内存中。当你将数据读入 RStudio 时，你会将其保存在环境面板中。一旦关闭 RStudio，内存中的数据就会消失。源数据集留在原始位置，除非你保存内存中的数据框并替换原始文件，否则原始数据不会更改。然而，我们不建议这样做。

#### 2.5.4 内存

RAM（随机存存储器）是 R 在处理期间存放数据的临时存储器。你必须知道电脑内存的大小。内存越大，R 读取和存储的数据就越多。

## 2.6 上传数据到 RStudio Cloud

如果用户想在 RStudio Cloud 中数据数据，他们可能将数据上传。他们也可以使用 RStudio Cloud 从 Dropbox 文件夹或 Google Drive 文件夹读取数据。

## 2.9 Bookdown

![](img/2bc6b006fe018e0018b86f206ab98644_41_0.png)

两本书的示例，它们既可以在 Bookdown 网站上免费访问，也可以以实体书的形式提供。

RStudio Cloud 上有很多资源。例如，在 YouTube 频道上，有教育版 RStudio Cloud `https://www.youtube.com/watch?v=PviVimazpz8`。YouTube 上的另一个优质资源是在云端使用 R 语言 `https://www.youtube.com/watch?v=SFpzr21Pavgg`

为了获取进一步的指导和帮助，用户可以注册并加入 RStudio Community³。用户还可以在 Stack Overflow⁴ 上提问。此外，还有特定主题的邮件列表组，但用户必须自行订阅它们。

RStudio 提供了一个网站来托管在线书籍，即 Bookdown⁵。Bookdown 上的书籍可以免费在线访问。有些书籍可以在亚马逊或其他或其他书店以实体书的形式出售，我们的书也是一样。

- ³`https://community.rstudio.com/`
- ⁴`https://stackoverflow.com/`
- ⁵`https://bookdown.org/`

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

> ¹`https://support.rstudio.com/hc/en-us/articles/20052607-Using-RStudio-Projects`

## 3 RStudio Project
