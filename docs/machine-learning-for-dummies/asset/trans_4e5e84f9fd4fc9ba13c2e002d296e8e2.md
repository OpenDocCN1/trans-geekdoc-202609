

最终，有人将能够以足够详细的方式描述一个问题，以便专用程序能够使用合适的语言创建必要的算法。换句话说，普通人最终将开始根据他们拥有并想要尝试的想法来创建新的机器学习环境。与创建机器学习任务一样，创建未来环境的人将是其特定领域的专家，而不是计算机科学家或数据科学家。解决机器学习的科学最终将转变为一项工程练习，这将使任何有好主意的人都能获得所需的访问权限。

## 避免未来技术的潜在陷阱

任何新技术都伴随着潜在的陷阱。对该技术的期望越高，陷阱就越严重。不切实际的期望会给机器学习带来各种问题，因为人们认为电影中看到的就是现实世界中会得到的。记住[第 1 章](#c01.xhtml)中介绍的基本概念至关重要——即机器学习算法目前无法感受、独立思考或创造任何东西。与电影中的 AI 不同，机器学习算法精确地按照你的预期执行，不会多做任何事情。当然，一些结果令人惊叹，但将期望与实际技术能做的事情保持一致很重要。否则，你会承诺技术永远无法交付的东西，而你期待的那些拥护者将去寻找下一个大事件。

事实上，当今机器学习的用途相当狭窄。正如文章 [`https://www.linkedin.com/pulse/machine-learning-its-hard-problems-valuable-toby-coppel`](https://www.linkedin.com/pulse/machine-learning-its-hard-problems-valuable-toby-coppel) 中所述，`narrow AI`，例如企业利用 AI 从海量数据集中获取洞察的应用，依赖于过去十年公司开始采用的成熟技术。机器无法推断任何东西，这限制了机器的使用范围，仅限于开发人员或数据科学家为其设计的任务。事实上，当今算法的一个很好的比喻是它们就像一件量身定制的衬衫（有关更多详细信息，请参阅文章 [`https://www.computerworld.com/article/3006525/cloud-computing/why-microsofts-data-chief-thinks-machine-learning-tools-are-like-tailored-shirts.html`](https://www.computerworld.com/article/3006525/cloud-computing/why-microsofts-data-chief-thinks-machine-learning-tools-are-like-tailored-shirts.html)）。当今，你需要专业技能来创建满足特定需求的定制算法，但未来可能会出现能够处理几乎任何任务的算法。依赖窄 AI 的公司需要谨慎开发产品或服务。产品或服务的变化可能会使机器学习环境中使用的数据超出学习算法的领域，从而将机器学习算法的输出降低为乱码（或至少使其不可靠）。

在组织中使用机器学习还需要雇佣具备正确技能的人员并组建团队。在企业环境中，机器学习的结果意味着利润的改善，这是一个相对较新的领域。公司在组建合适的团队、制定合理的目标以及实际实现这些目标方面面临挑战。为了吸引世界级团队，你的公司必须提供一个足够令人兴奋的问题，以吸引来自其他组织所需的人才。这不是一项容易的任务，你需要将其视为制定创建机器学习环境目标的一部分。

# Part 2

# 准备你的学习工具

本部分内容…

创建 Python 设置

执行基本 Python 任务

使用 Google Colab

# 第 4 章

# 安装 Python 发行版

本章内容

![Bullet](images/check.png)**确定用于机器学习的 Python 发行版**

![Bullet](images/check.png)**在 Linux、Mac OS X 和 Windows 上进行安装**

![Bullet](images/check.png)**获取数据集和示例代码**

在你能够使用 Python 做太多事情或使用它来解决机器学习问题之前，你需要一个可用的安装。此外，你需要访问本书中使用的数据集和代码。本章将告诉你如何执行所需的 Python 设置和下载。下载示例代码（位于本书页面 [`www.dummies.com`](https://www.dummies.com/) 上）并将其安装在你的系统上，是从本书中获得良好学习体验的最佳方式。本章将帮助你设置系统，以便你可以轻松跟随本书其余部分中的示例。

![Remember](images/remember.png)使用可下载的源代码并不会阻止你自己输入示例、使用调试器跟踪它们、扩展它们或以各种方式处理代码。可下载的源代码旨在帮助你开始你的机器学习和 Python 学习体验。在你看到代码在正确输入和配置后的工作方式后，你可以尝试自己创建示例。如果你犯了错误，你可以将你输入的内容与可下载的源代码进行比较，并准确发现错误所在。你可以在 `ML4D2E; 04; Sample.ipynb` 和 `ML4D2E; 04; Dataset Load.ipynb` 文件中找到本章的可下载源代码。（简介告诉你在哪里下载本书的源代码。）

![Tip](images/tip.png)可下载的源代码还提供以 R 变体编写的示例的访问权限。虽然 Python 代码出现在可下载源代码的 `ML4D2E`（即《机器学习傻瓜书》第 2 版）文件夹中，但 R 代码出现在 `ML4D2ER`（即《机器学习傻瓜书》第 2 版，R 代码）文件夹中。R 示例并不总是精确地遵循 Python 示例，因为两种语言之间存在差异，但 R 示例有大量注释，因此你可以跟随学习。使用任何一种语言都将使你能够达到所需的结果。

## 使用 Anaconda 进行机器学习

你可以使用许多包来执行机器学习任务。事实上，存在太多包，无法在单个章节中充分讨论。为了让你更容易专注于机器学习而不是软件包，接下来的第一部分将告诉你如何获取你的 Anaconda 副本，即 Anaconda3-2020.07 版本。本书使用 Anaconda 有多种原因，如下一节所述。但是，如果你使用的平台安装过程不太好（或根本无法工作），你也可以按照第 6 章中描述的使用 Google Colab 来跟随本书的代码。接下来的各部分将为你简要介绍 Anaconda 作为产品的概况。

### 获取 Anaconda

基本的 Anaconda 包是免费下载的，你可以在 [`https://www.anaconda.com/products/individual`](https://www.anaconda.com/products/individual) 上获取。只需单击 Download 查看可用下载列表；然后单击适用于你平台的单独链接以获取免费产品。Anaconda 支持以下平台：

*   Windows 32 位和 64 位（安装程序可能只提供 64 位或 32 位版本，具体取决于它检测到的 Windows 版本）

*   Linux 64 位（x86 和 PowerPC 8/9 安装程序）

*   Mac OS X 64 位（图形和命令行安装程序）

在所有情况下，你都需要 Anaconda3-2020.07 版本的产品。如果你无法在主 Anaconda 页面上找到正确的版本，可以在 [`https://repo.anaconda.com/archive/`](https://repo.anaconda.com/archive/) 上获取它。

