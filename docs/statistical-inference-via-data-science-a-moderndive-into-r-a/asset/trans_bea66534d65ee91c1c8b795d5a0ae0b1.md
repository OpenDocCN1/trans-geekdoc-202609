

# 作者简介

| Chester Ismay | Albert Y. Kim | Arturo Valdivia |
| :--- | :--- | :--- |

![](img/445742518041017e8f01f11b0c3190d9_33_0.png)

**Chester Ismay** 是一位自由职业数据科学家、顾问和教育者。他还在波特兰州立大学的高管与专业教育中心任教。他于 2013 年在亚利桑那州立大学获得统计学博士学位。他曾担任过多种角色，包括在斯卡代尔保险公司（现为 Nationwide ERS/Specialty）担任精算师，以及在里彭学院、里德学院和太平洋大学工作。他拥有在线教育工作经验，此前曾担任 DataRobot 的数据科学布道者，在那里他负责为 DataRobot 大学通过线下和虚拟研讨会数据科学、机器学习和数据工程教学。除了为 *ModernDive* 工作外，他还是 infer^52 R 包的初始开发者，以及 theirs^53 R 包的作者和维护者。

- 网页：https://chester.rbind.io/
- GitHub：https://github.com/ismayc

**Albert Y. Kim** 是马萨诸塞州诺森普史密斯学院的统计与数据科学副教授。他于 2011 年在华盛顿大学获得统计学博士学位。他曾在谷歌公司搜索广告指标团队工作，并在里德学院、米德伯学院和阿默斯特学院工作。除了为 *ModernDive* 工作外，他还是 resampleddata^54 和 SpatialEpi^55 R 包的合著者。

> ^52https://cran.r-project.org/package/infer
> 53https://github.com/ismayc/theisdown
> 54https://cran.r-project.org/package=resampleddata
> 55https://cran.r-project.org/package=SpatialEpi

Kim 博士和 D. Ismay 以及 Jennifer Chunn^56 是数据新闻网站 FiveThirtyEight.com^58 发布的 fifty-eight^57 代码包和数据集的合作者。

- 网页：http://rudeboybert.rbind.io/
- GitHub：https://github.com/rudeboybert

**Arturo Valdivia** 是印第安纳大学布卢明分校统计系高级讲师。他于 2013 年在亚利桑那州立大学获得统计学博士学位。他的研究兴趣是统计教育，探索创新方法帮助学生清晰地理解复杂概念。在职业生涯中，他教授了广泛的统计课程，从入门级到高级课程，涵盖了超过 1,800 名本科生以及超过 900 名追求统计学、数据科学及其他学科的硕士博士研究生。因其卓越的教学表现，他于 2023 年获得了印第安纳大学信托基金教学奖。

- 网页：https://avaldivi6.github.io
- GitHub：https://github.com/avaldivi6

> 56https://github.com/jchunn
> 57https://fiftirtyyeight-r.netlify.app/
> 58https://fiftirtyyeight.com/

# 1 开始在 R 中处理数据

在我们开始在 R 中探索数据之前，首先需要理解一些关键概念：

1. R 和 RStudio 是什么？
2. 我如何在 R 中编写代码？
3. 什么是 R 包？

我们将在接下来的第 1.1–1.3 节介绍这些概念。如果你已经对这些概念比较熟悉，可以随时跳到第 1.4 节，届时我们将介绍第一个数据集：2023 年从纽约市（NYC）三个主要机场起飞的所有国内航班。我们将在本书的大部分内容中深入探索这个数据集。

## 1.1 R 和 RStudio 是什么？

在本书中，我们假设你正在通过 RStudio 使用 R。初次用户往往会混淆两者。简单来说，R 就像汽车的引擎，而 RStudio 就像是汽车的仪表盘，如图 1.1 所示。

![](img/445742518041017e8f01f11b0c3190d9_35_0.png)

图 1.1：R 与 RStudio 区别的类比。

## 2 开始在 R 中处理数据

更准确地说，R 是一种运行计算的编程语言，而 RStudio 是一个集成开发环境（IDE），它通过添加许多方便的功能和工具来提供界面。因此，就像拥有速度表、后视镜和导航系统让驾驶变得简单得多，使用 RStudio 的界面也会让 R 变得简单得多。

### 1.1.1 安装 R 和 RStudio

> 关于 RStudio Server 或 RStudio Cloud 的说明：如果你的导师为你提供了 RStudio Server 或 RStudio Cloud 的链接和访问权限，你可以跳过本节。不过，我们建议在在使用 RStudio Server/Cloud 几个月后，返回查看这些说明，在你自己的电脑上安装该软件。

你首先需要在你的电脑上下载并安装 R 和 RStudio（桌面版）。先安装 R 再安装 RStudio 非常重要。

- **你必须先执行这一步：** 访问 https://cloud.r-project.org/ 下载并安装 R。
- 如果你是 Windows 用户：点击 "Download R for Windows"。
- 对于 macOS 用户：点击 "Download R for macOS"，并选择合适的安装包。
- 如果你是 Linux 用户：点击 "Download R for Linux"，并选择你的发行版。
- **你必须后执行这一步：** 访问 https://posit.co/products/rstudio-desktop/ 下载并安装 RStudio。

### 1.1.2 通过 RStudio 使用 R

回顾我们之前的汽车类比。我们并不直接操作引擎，而是通过仪表盘来操作。当你安装了 R 和 RStudio 后，就可以通过界面进行操作。图 1.2 显示了你可以使用的界面。

| R：打开它 | RStudio：打开它 |
| :--- | :--- |
| ![R Icon](...) | ![RStudio Icon](...) |

图 1.2：R 与 RStudio 的图标。

![](img/445742518041017e8f01f11b0c3190d9_37_2.png)

RStudio 界面。注意三个面板：控制台面板、文件面板和环境面板。

## 1.2 如何在 R 中设置

现在你已经有了 R 和 RStudio，你可能在问自己：“好的，我该如何使用 R？”首先需要注意的是，与 Excel、SPSS 或 Minitab 等点击式统计程序不同，R 是一种解释型语言，这意味着你必须通过代码输入的命令。换句话说，我们将交叉使用“编码”和“编程”这两个词。虽然使用 R 不需要成为资深代码程序员，但仍有一些基础编程概念需要理解。

### 1.2.1 基础编程概念和术语

我们介绍一些编程概念和术语。我们并不是要求你现在记住所有的概念和术语，我们会引导你“在做中学会”。为了帮助学习，我们将使用不同的字体来区分普通文本和计算机代码。

- 基础：
- 控制台面板：你输入命令的地方。
- 运行代码：通过控制台输入命令让 R 执行操作。
- 对象：R 中存储值的地方。我们将教你如何为对象赋值以及如何显示对象的内容。
- 数据类型：双精度/数值、逻辑型、字符。整数如 -1, 0, 2, 4092。双精度或数值是一个更大的集合，包含了整数，还包含了分数和小数，如 -24.932 和 0.8。逻辑型为 `TRUE` 或 `FALSE`，而字符则是文本，如 "cabbage”、“Hamilton”、“The Wire 是最棒的剧”以及“这碗拉面很好吃”。注意字符通常用引号括起来。

- 向量：一系列值。它们使用 `c()` 函数创建，其中 `c()` 代表“组合”或“连接”。例如，`c(6, 11, 13, 31, 90, 92)` 创建了一个由正整数组成的序列。

¹https://en.wikipedia.org/wiki/Point_and_click
²https://en.wikipedia.org/wiki/interpreted_language
³https://jamesclear.com/deliberate-practice-theory

