
正如我们之前提到的，使用微服务架构的一个显著缺点是随之而来的运维开销。依我之见，这是微服务在之前不流行的主要原因。ROI（即投资回报率）不值得！云计算技术在许多方面让我们的生活变得更加简单，但主要体现在运维领域。因此，利用云计算资源构建微服务架构突然听起来像是一个不错的 ROI。

接下来我们要关注的趋势是 Docker Engine。

通常，容器化技术在 Docker 之前很久就已发明。Docker 是推动我们使用容器化的关键参与者；如今，它变得如此简单易用。Docker 于 2013 年推出，并立即广受欢迎。*图 1.6* 展示了 Google Trends 统计的 Docker 搜索趋势：

![](OEBPS/images/Figure-1.6.jpg)

**图 1.6：** Google Trends 统计的 Docker 网络搜索趋势

微服务的核心优势之一是它们可以交付独立的工作负载/部署。Docker 旨在将软件作为隔离的容器交付。微服务旨在交付隔离的软件，无论采用何种方式，使用 Docker Engine 运行容器都是完美的选择。

最后我们要讨论的趋势是 DevOps 方法论。称其为方法论很奇怪，但它确实如此。如今，它已成为一个职位名称。还有从事类似工作的非常相似的职位，如 SRE、生产工程师等。同样，正如我们之前提到的，微服务的主要缺点是运维开销。DevOps 方法论旨在解决它，或者至少减少它。

# [Golang 的流行度](#toc.xhtml#s19a)

我们可以跟踪的一个指标是 Golang 用户（开发者，或称 Gophers）的增长，以此来衡量 Go 的流行度。Golang 开发者的昵称是 Gophers。Gopher 是一种动物，作为 Golang 编程语言的官方吉祥物。这里有一个来自 StackOverflow Insights 的友好仪表盘，我们可以在其中看到想要学习 Golang 并成为专业 Go 开发者的开发者百分比。

![](OEBPS/images/Figure-1.7.jpg)

**图 1.7：** StackOverflow Insights 统计的最想学习语言排行

此外，我们还想跟踪的另一个指标是用 Go 编写的包的数量。截至 2023 年 7 月，用 Go 编写的包数量已超过 100 万个（数据来源见本章末尾参考文献链接的优秀网站，该网站收集开源洞察数据，强烈建议查看）。如果我们将 Go 的年龄和包数量与 Java、Python 或 C# 等其他语言进行比较，Go 紧随 JavaScript 之后排名第二。这令人难以置信。如此疯狂的 Go 包数量源于强大的 Golang 社区。

# [结论](#toc.xhtml#s20a)

在本章中，我们简要游览了微服务领域。我们回顾了它的历史，以及促使微服务如今如此流行的趋势（敏捷、云计算、Docker、DevOps）。我们了解了微服务的替代方案，如 SOA、单体架构和无服务器架构。市场上还有其他替代方案，但这些是最流行的。我们对比了微服务与其他架构的优缺点。

在下一章中，我们将讨论 Golang 的易用性。我们将探讨社区情况，并详细说明为什么我们认为以及社区认为 Go 近年来变得如此流行。我们将涵盖 Go 的生态系统，并深入探讨这门语言最初发明的原因，以及从那时至今的历史。最后，我们将讨论使用 Go 的优缺点。

# [参考文献](#toc.xhtml#s21a)

*   [https://deps.dev/](https://deps.dev/)
*   [https://insights.stackoverflow.com/survey/2021?_ga=2.236209345.190202062.1628102352-126161871.1625855113#most-loved-dreaded-and-wanted-language-want](https://insights.stackoverflow.com/survey/2021?_ga=2.236209345.190202062.1628102352-126161871.1625855113#most-loved-dreaded-and-wanted-language-want)
*   [https://trends.google.com/trends/explore?date=all&q=microservices&hl=en-GB](https://trends.google.com/trends/explore?date=all&q=microservices&hl=en-GB)
*   [https://agilemanifesto.org/](https://agilemanifesto.org/)
*   [https://trends.google.com/trends/explore?date=all?q=docker&hl=en-GB](https://trends.google.com/trends/explore?date=all?q=docker&hl=en-GB)

# [第 2 章](#toc.xhtml#c02)

# [Go 的易用性](#toc.xhtml#c02)

# [简介](#toc.xhtml#s22a)

在本章中，我们将深入探索 Go 的精彩世界。我们将深入研究基础知识，考察其历史，并理解发明者创建这门语言的初衷。创建这门语言的意图是什么？它旨在解决什么问题？

为了理解 Go，我们旨在理解其核心原则、范式、目的等。通过理解它们，我们将拥有在编写 Go 代码时洞察全局的能力。许多缺乏经验的 Go 开发者开始编写 Go 代码后，会对错误处理技术感到恼火。如果他们清楚地理解核心原则，就会意识到 Go 当前的错误处理方式才是精确的解决方案。

我们将详细阐述每一条核心原则，理解其意图，并从中获益。然后，我们将观察新手接触该语言的过程，从入职到将代码部署到生产环境。

接着，我们将探索 Golang 生态系统。生态系统是一个由众多社区和 Gophers 组成的庞大有机体。由于 Golang 是由 Google 维护的开源项目，加入社区的门槛非常低。

无需具备 Go 的先验知识。建议在积累更多 Go 开发经验后重读本章。我们将涵盖的许多观点届时会与你产生更强的共鸣。引用自《Effective Go》：“*换句话说，要写好 Go，理解其特性和习惯用法非常重要。*”

# [结构](#toc.xhtml#s23a)

在本章中，我们将讨论以下主题：

*   Go 的发明
*   核心原则与范式
*   简洁性与极简设计方法
*   适合云的高性能语言
*   Go 的可维护性
*   从入职到生产
*   Go 的生态系统——社区及更远

# [Go 的发明](#toc.xhtml#s24a)

那么这门语言是如何开始的？一切始于 Google。2007 年，Google 的三位工程师决定创建一门新语言。该语言由 Ken Thompson、Rob Pike 和 Robert Griesemer 设计，他们各自带来了独特且相关的背景。他们参与了 UTF-8、Unix、C 编程语言等重大技术发明。该语言的全称是 Golang，由“go”+“lang”组合而成，其中“lang”是 language 的缩写。不过，他们更倾向于称其为 Go 而非 Golang，以强调该语言旨在简单易记。“Go”是一个常见的英语单词，暗示着移动、进步和效率，这与该语言为软件开发提供简单高效方法的目的相一致。此外，“Go”也是 Google 的前两个字母。

在获得 Google 批准后，他们开始开发这门语言。他们的核心内部协议之一是：仅包含他们所有人都认同的编程原则。尽管这门语言发明于 2007 年，但它主要受 C 编程语言（创建于 1972 年）影响，而非 C++、Java、C# 等较新语言。Go 和 C 编程语言有许多相似之处。确实，一些人将 Go 称为 C 语言的现代版本。

他们开始使用 Go、C++ 和汇编语言编写这门编程语言。
