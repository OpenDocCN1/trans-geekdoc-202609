
... 软件包并归属于 Posit Software¹，Posit Soft PBC 是一家开源数据科学公司，此前名为 RStudio PBC。Posit Software 持续支持开源数据科学倡议，并分发极其出色的 RStudio IDE⁴。在编写本书时，我们使用了 R 4.2.2 版本和 RStudio 版本 2022.07.2 Build 576。

本书的源代码可以在我们的 GitHub 仓库⁵中找到，同时在 GitHub 的 `data` 文件夹中也提供了数据集⁶。我们非常感谢 George Knott 博士，他是 Chapman & Hall (CRC Press) 的统计编辑，在我们追赶书籍截止日期期间，他给予了巨大的支持和理解。我们还感谢 Nivedita Menon 的帮助，在 George 离开 Chapman & Hall (CRC Press) 职位后，由她接手了出版任务。此外，Chapman & Hall (CRC Press) 非常慷慨，允许我们在 bookdown 网站⁷上发布这本书的在线版本。总而言之，我们希望大家喜欢这这本书！

# Kamarul Imran Musa⁸

# Wan Nor Arifin Wan Mansor⁹

# Tengku Muhammad Hanis¹⁰

马来西亚理科大学医学院 (Universiti Sains Malaysia)

2023-04-22

## R, RStudio 和 RStudio Cloud

在本章结束时，读者将：

- 了解 R 编程语言
- 了解 RStudio IDE
- 了解 RStudio Cloud。RStudio Cloud 是一个用户可以在云端运行 RStudio 的平台
- 能够在本地机器上安装 R
- 能够在本地机器上安装 RStudio IDE
- 了解如何安装 LaTeX 编辑器（Miktex 或 Tex Live 以及 MacTeX）。LaTeX 编辑器是可选的，但如果用户想要渲染 PDF 输出，则是必须的
- 了解 R 脚本的工作结构
- 了解 R 软件包和 R Taskview

R 是一种用于统计计算和图形图形语言和环境。它是一个 GNU 项目，类似于在贝尔实验室开发的 S 语言和环境。R 提供了各种统计技术（线性和非线性建模、经典统计检验、时间序列分析、分类、聚类）和图形技术，并具有高度的可扩展性。

R 的优势之一是能够轻松生成设计良好的出版级图表，包括在需要时包含数学符号和公式。R 根据自由软件基金会的 GNU 通用公共许可证条款以源代码形式作为自由软件提供。它可以在各种 UNIX 平台和类似系统（包括 FreeBSD 和 Linux）、Windows 和 macOS 上编译和运行。

## RStudio IDE

RStudio 是一个用于 R 的集成开发环境 (IDE)。它包含一个控制台和一个语法高亮编辑器，支持直接执行代码，以及用于绘图、历史记录、调试和工作空间管理的工具。

RStudio 提供开源版和商业版，可以在桌面端（Windows、Mac 和 Linux）运行或在连接到 RStudio Server 或 RStudio Workbench（Debian/Ubuntu、Red Hat/CentOS 和 SUSE Linux）的浏览器中运行。

## RStudio Cloud

RStudio Cloud 便于了 R 的学习。任何人都可以注册并开始在云端使用 RStudio。这是学习 R 最快的方法之一。

使用 RStudio Cloud，我们不需要在本地机器上安装 R。RStudio Cloud 允许 R 老师和学生之间的协作。它还可以帮助同事在 R 项目上共同工作。

R 将其描述为一种轻量级的基于云的解决方案，允许任何人在线分享、教学和学习数据科学。它还补充道，通过此平台，我们可以：

- 直接从浏览器使用 RStudio IDE 分析我们的数据
- 与我们的团队、课程、工作坊或世界共享项目
- 使用 R 向我们的学生或同事教授数据科学
- 在导师引导的环境或通过交互式教程学习数据科学

RStudio Cloud 有免费版和商业版（遗憾的是价格非常实廉）。要开始使用 RStudio Cloud，请访问 https://rstudio.cloud/。在页面上点击“Sign Up”（注册）。

使用 RStudio Cloud 几乎不需要任何配置，你不需要专用的硬件、安装或年度购买合同。个人用户、教师和学生只需要一个浏览器就可以进行、分享、教学和学习数据科学。

## 1.4 RStudio Cloud

![](img/2bc6b006fe018e0018b86f206ab98644_19_0.png)

图 1.1
RStudio Cloud 注册页面。

![](img/2bc6b006fe018e0018b86f206ab98644_19_1.png)

图 1.2
RStudio Cloud 网页。

### 1.4.1 RStudio Cloud 注册

这是 RStudio Cloud 的注册和登录页面。

### 1.4.2 注册并登录

继续注册。如果你有 Google 账号或 GitHub 账号，可以使用其中任何一个进行快速注册。完成注册后，你就可以登录 RStudio Cloud。

## R, RStudio 和 RStudio Cloud

![](img/2bc6b006fe018e0018b86f206ab98644_20_0.png)

图 1.3
RStudio 注册页面。

R 有多个 GUI 版本，也称为 GUI。其界面类似于流行的统计软件。例如，有：

- Blue Statistics https://www.positstudio.com/
- jamovi https://www.jamovi.org/

Blue Statistics 可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低 学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

Blue Statistics 也可以帮助用户：

- 从昂贵的统计应用程序迁移到 R
- 降低学习曲线

## 1.7 在本地机器上安装 R 和 RStudio

要在本地机器上安装 R，你需要拥有运行 R 的的权限。我们建议你按以下顺序安装：

- 首先安装 R，
- 然后安装 RStudio

### 1.7.1 安装 R

虽然你可以使用原生 R 软件（你刚刚安装的）运行 R 代码，但我们强烈建议使用 R 集成开发环境 (IDE)。我们将逐步演示。首先，让我们在机器上安装 R。要安装 R，我们需要检查适用于你机器操作系统的 R 版本。例如，对于 Windows OS，链接是 https://cran.r-project.org/windows/base/R-4.3.1-win.exe。对于 Mac OS，链接是 https://cran.r-project.org/bin/macos/big-x86_64/R-4.3.1.pkg。同样，如果你使用 Linux，请按照列出的步骤操作。

始终建议用户安装最新版本的 R。在本书期间，最新版本是 R 4.2.1 版本，被称为“看起来有趣的孩子”版本，于 2022 年 6 月 23 日发布。用户可以在本地机器上拥有多个 R 版本。你不需要卸载旧 R 即可安装新的 R 版本。

### 1.7.2 安装 RStudio IDE

现在，要安装 RStudio IDE，访问 RStudio 下载页面。选择适用于你机器操作系统的平台。下载大小将为 90–110 MB。

> 1 https://cran.r-project.org/
> 2 https://www.rstudio.com/products/rstudio/download/#download

