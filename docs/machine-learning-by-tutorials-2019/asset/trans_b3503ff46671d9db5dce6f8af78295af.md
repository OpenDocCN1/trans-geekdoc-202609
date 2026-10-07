

## 第 4 章：上手 Python 与 Turi Create

作者：Audrey Tam & Matthijs Hollemans

**更新说明：** 本章已针对 iOS 13、Xcode 11 和 Swift 5.1 更新。

恭喜你！如果你已经走了这里，说明你为吸收机器学习材料打下了坚实的基础。然而，在继续之前，我们需要解决那个“显而易见的问题”……Python。到目前为止，你一直在使用 Xcode 和 Swift 过日，但如果你打算认真学习机器学习，那么最好准备好学习 Python。在本章中：

- 你将学习如何设置和使用 Python 生态系统中的工具来完成数据科学和机器学习（ML）工作。
- 你将安装 **Anaconda**，这是一个非常流行的 Python（以及 R）发行版。
- 你将使用终端命令来创建机器学习环境，这些环境将在贯穿全书中使用。
- 最后，你将使用 **Jupyter Notebooks**（它与 Swift Playgrounds 非常相似）来探索 Python 语言、数据科学库以及 Apple 的机器学习即服务工具 **Turi Create**。

## 启动文件夹

本章的启动文件夹包含：

- 一个 **notebook 文件夹**：示例 Jupyter Notebook 数据文件。
- **.yaml 文件**：用于导入预配置的环境，如果你想跳过手动配置环境的说明。

## Python

Python 是数据科学和机器学习领域为主的编程语言。因此，Python 社区有大量的工具来支持数据科学和机器学习开发。这些工具包括：

- **数据科学库**：Matplotlib, NumPy, Pandas, SciPy 等。
- **机器学习库**：Caffe, Keras, Microsoft Cognitive Toolkit, PyTorch, TensorFlow, scikit-learn 等。
- **机器学习即服务 (ML-as-a-Service)**：Amazon Machine Learning, Google ML Kit, IBM Watson, Microsoft Azure Machine Learning Studio, Turi Create 等。
- **工具**：coremltools, pip, Anaconda, Docker, Jupyter notebooks, Google Collaboratory 等。

如果你熟悉 Swift 编程语言，你会发现尽管 Python 大大不同，但它与 Swift 有一些相似之处。例如：

- 导入模块的方式相似。
- 它在基本类型、元组、列表、字典、运算符、循环和条件判断方面具有相似的概念。
- 你可以创建对象、类和函数。

当然，存在一些差异。例如：

- Python 是解释型的，而不是编译型的。
- 你使用缩进而不是 `{ ... }` 来定义闭包、函数和类。
- 命名规范倾向于简短的缩写，类似于 C 语言。
- 模块和函数名使用蛇形命名法（snake_case），而类名和异常名使用驼峰命名法（PascalCase）。
- 注释以 # 开头，而不是 //。
- 多行注释以 """ 开始和结束，而不是 /* 和 /，且结尾的 """ 独占一行。这与 Swift 中的多行字符串相似。
- 使用 True/False，而不是 true。
- 动态类型，不支持常量；没有 let 或 var。
- 有枚举（Enumerations），但没有 switch 语句（现使用 match）。

在设置好工具后，你将在学习库的同时尝试使用 Python。如果你需要一些练习或信息，这里有两个非常有帮助的资源：

- Michael Kennedy 在 2014 年 11 月发布的 Python 与 Swift 语法对比：bit.ly/2AXQ1UF。
- Jason Brownlee 在 2016 年 5 月为机器学习开发者的 Python 快速课程，使用了 NumPy、Matplotlib 和 Pandas 示例：bit.ly/2MqBCWD。

## 包与环境

macOS 已经安装了 Python。然而，使用此安装可能会导致版本冲突，因为有些人使用 Python 2.7，而另一些人使用 Python 3.x，它们是同一语言的不兼容分支。为了进一步完成工作，机器学习项目需要集成正确版本的软件库（也称为“包”）。

> 注意：Python 团队将于 2020 年停止支持 Python 2.7，因此主要的开源 Python 包已承诺在 2020 年之前停止对 Python 2.7 的支持。

大多数人会创建环境，在其中安装特定版本的 Python 和所需的包。你可以在同一台电脑上拥有多个此类环境，每个环境都有自己的 Python 解释器和自己的 Python 包。

最基础的工具集包括环境管理器 `virtualenv` 和包管理器 `pip`。除了设置环境，你仍然需要确定需要哪些版本的包——这是一个非常手动的过程，极可能会令人挫败。

有一种更好的方法！

## Conda

科学社区开发了 Conda 来让生活变得简单。Conda 处理 Python 语言版本、Python 包以及相关的原生库。它既是环境管理器，也是包管理器。而且，如果你需要一个 Conda 不包含的包，你可以在 conda 环境中使用 `pip` 来获取该包。

Conda 共有两种发行版本：

- Miniconda：仅包含运行 Conda 所需的包（400 MB）。
- Anaconda：包含机器学习所需的所有标准包（GB级）。

你将在本章中使用 Anaconda。安装它并不费时间，而且方便得多！

## 安装 Anaconda

在浏览器中，导航到 https://www.anaconda.com/download/#macos，并下载 64 位命令行版本。

| Python 3.7 版本 | Python 2.7 版本 |
| :--- | :--- |
| [下载] | [下载] |
| 64 位图形安装程序 (653 MB) | 64 位图形安装程序 (634 MB) |
| 64 位命令行安装程序 (435 MB) | 64 位命令行安装程序 (408 MB) |

在写作时，下载的文件名为 Anaconda3-2019.07-MacOSX-x86_64.sh。下载后，打开 **Terminal**（终端）并进入下载文件目录。通过以下命令运行安装程序：

```bash
sh Anaconda3-2019.07-MacOSX-x86_64.sh
```

你必须接受许可协议，然后指定安装 Anaconda 的目录（或接受默认位置）。一旦开始安装，可能需要一段时间。

在等待安装完成期间，滚动到“Get Started”链接并仔细查看：

| 文档 | Anaconda 博客 | 社区支持 | Anaconda 网络研讨会 | 培训 |
| :--- | :--- | :--- | :--- | :--- |
| Anaconda 发行版的安装和用户指南 | 新闻、开发者和最佳实践 | 社区解决方案与问题 | Anaconda 的行业趋势和解决方案 | 在 DataCamp 学习 Python |
| 更多 | 更多 | 更多 | 更多 | 开始学习 |

这些是关于使用 Python 进行机器学习的视频。部分免费。

如果提示运行 `conda init`，输入 yes。安装完成后，重启终端。重启后，你可以运行以下命令检查安装是否成功：

```bash
conda --version
```

如果上述命令失败并提示“command not found”，可能你需要将 Anaconda 路径添加到全局路径环境变量中。这意味着，你需要编辑主目录下的 `.bashrc` 或 `.zshrc` 文件（通常位于 /Users/<username>）。如果该文件不存在，你需要根据当前正在使用的 shell 创建它。

无论是哪种情况，打开或创建 `.zshrc` 或 `.bashrc` 文件，查找或添加类似下行的内容。假设你将 Anaconda 安装在主目录下，该行可能如下：

```bash
export PATH="Users/<username>/anaconda3/bin":"$PATH"
```

在此行代码中，你将 Anaconda 的安装路径置于现有路径之前。两个需要注意的重要点包括路径中包含 `bin` 目录，以及使用冒号分隔安装路径与现有的 PATH 变量。

