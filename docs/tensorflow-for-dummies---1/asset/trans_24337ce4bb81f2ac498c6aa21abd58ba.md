

Keras 的简洁性源于其小巧的 API 和直观的函数集合。这些函数专注于完成机器学习中的标准任务，这使得 Keras 非常适合该领域的初学者，但对于想要自定义操作的人来说价值有限。

François Chollet 在 MIT 许可证下发布了 Keras，而 Google 已将其界面整合到 TensorFlow 中。因此，许多 TensorFlow 开发者更喜欢使用 Keras 来编写神经网络。

### TensorFlow

顾名思义，本书以 TensorFlow 为中心，TensorFlow 是 Google 赠予机器学习世界的礼物。Google Brain 团队于 2015 年发布了 TensorFlow 1.0，而截至本文撰写时，当前版本为 1.4。它采用 Apache 2.0 开源许可证发布，这意味着你可以自由使用、修改并分发你的修改版本。

TensorFlow 的主要接口是 Python，但与 Caffe 类似，其核心功能是用 C++ 编写以提高性能。与 Theano 类似，TensorFlow 将操作存储在图中，该图可以部署到 GPU、远程系统或远程系统网络。此外，TensorFlow 还提供了一个名为 TensorBoard 的实用工具，可实现对图及其操作的可视化。

与其他框架一样，TensorFlow 支持在 CPU 和 GPU 上执行。此外，TensorFlow 应用程序可以在 Google Cloud Platform (`GCP`) 上执行。`GCP` 以相对较低的成本提供世界级的处理能力，在我看来，`GCP` 处理是 TensorFlow 最重要的优势。 [Chapter 13](#19_9788126592555-ch13.xhtml) 详细讨论了这一重要主题。

# Getting Your Feet Wet

IN THIS CHAPTER

![check](images/check.png)**Obtaining and installing TensorFlow**

![check](images/check.png)**Exploring the TensorFlow package**

![check](images/check.png)**Running a simple application**

![check](images/check.png)**Understanding style conventions**

本书的许多章节介绍了复杂的专业主题和冗长的数学公式。但本章不是。本章非常简单，其目标是引导你完成安装 TensorFlow 并运行第一个 TensorFlow 应用程序的过程。

完整的 TensorFlow 安装包含大量文件和目录。本章将探讨安装过程并解释众多文件和文件夹的用途。讨论涉及 TensorFlow 的许多包及其提供的模块。

安装完 TensorFlow 工具包后，开始编写和运行应用程序就变得很容易。本章末尾提供了一个基本应用程序，为 TensorFlow 开发提供热情的欢迎。

## Installing TensorFlow

Google 提供了两种安装 TensorFlow 的方法，而更简单的方法是安装预编译的包。本讨论介绍了安装这些包的三步流程：

1.  **在开发系统上安装 Python。**
2.  **安装 pip 包管理器。**
3.  **使用 pip 安装 TensorFlow。**

第二种安装方法涉及从源代码编译 TensorFlow。这种方法耗时费力，但你可以获得更好的性能，因为你的 TensorFlow 包将充分利用处理器的功能。 [Chapter 12](#18_9788126592555-ch12.xhtml) 解释了如何获取和编译 TensorFlow 的源代码。

### Python and pip/pip3

TensorFlow 支持使用 Java 和 C++ 进行开发，但本书专注于 Python。我在示例代码中使用 Python 3，但你也可以使用 Python 2。正如我在即将到来的 “[Setting the Style](#06_9788126592555-ch02.xhtml#c02-sec-0012)” 部分中解释的那样，TensorFlow 应用程序应可供两个版本使用。

Python 的官方包管理器是 *pip*，这是一个递归缩写，代表“pip installs Python”。要安装像 TensorFlow 这样的包，你可以在 Python 2 系统上使用 `pip`，或在 Python 3 系统上使用 `pip3`。包管理命令的格式如下：

`pip <command-name> <command-options>`

`pip` 和 `pip3` 接受类似的命令并执行类似的操作。例如，执行 `pip list` 或 `pip3 list` 会打印系统上安装的所有 Python 包。 [Table 2-1](#06_9788126592555-ch02.xhtml#c02-tbl-0001) 列出了此命令和其他五个命令。

[TABLE 2-1](#06_9788126592555-ch02.xhtml#rc02-tbl-0001) Package Management Commands

| **Command Name** || **Description** |

| --- | --- |

| `install` || Installs a specified package |

| --- | --- |

| `uninstall` || Uninstalls a specified package |

| `download` || Downloads a package, but doesn't install it |

| `list` || Lists installed packages |

| `show` || Prints information about a specified package |

| `search` || Searches for a package whose name or summary contains the given text |

对于本讨论，最重要的命令是 `pip install` 和 `pip3 install`。但请记住，`pip`/`pip3` 可以执行许多其他操作。

![tip](images/tip.png)如果使用预编译包执行 TensorFlow 应用程序，你可能会收到类似“TensorFlow 库未编译为使用 *XYZ* 指令，但这些指令在你的机器上可用，并且可以加快 CPU 计算速度”的消息。要关闭这些消息，请创建一个名为 `TF_CPP_MIN_LOG_LEVEL` 的环境变量，并将其值设置为 3。

### Installing on Mac OS

许多版本的 Mac OS 已预装 Python，但我建议获取并安装新的 Python 包。如果访问 [`www.python.org/downloads`](http://www.python.org/downloads)，你会看到一个用于 Python 2 的按钮和一个用于 Python 3 的按钮。如果点击其中一个按钮，你的浏览器将下载一个用作 Python 安装程序的 PKG 文件。

启动安装程序后，Python 安装对话框会出现。要安装该包，请按照以下五个步骤操作：

1.  **在 Introduction 页面，点击标有 Continue 的按钮。**
2.  **在 Read Me 页面，点击标有 Continue 的按钮。**
3.  **在 License 页面，点击标有 Continue 的按钮，然后点击 Agree 以接受软件许可协议。**
4.  **在 Installation Type 页面，点击 Install 开始安装过程，如有必要，输入你的密码。**
5.  **安装完成后，点击 Close 关闭对话框。**

如果安装成功完成，你可以在命令行上运行 `pip` 或 `pip3`。你可以使用以下命令安装 TensorFlow：

`pip install tensorflow`

该命令指示包管理器下载 TensorFlow、TensorBoard 以及一系列依赖项。其中一个依赖项是 `six`，它支持 Python 2 和 3 之间的兼容性。如果由于预安装的 `six` 包导致安装失败，你可以通过执行以下命令修复该问题：

`pip install --ignore-installed six`

该命令指示 `pip` 在现有安装之上安装 `six`。此安装完成后，你应该能够在不报错的情况下运行 `pip install tensorflow`。在我的系统上，安装程序将 TensorFlow 文件存储在 `/Library/Frameworks/Python.framework/Versions/<ver>/lib/python<ver>/site-packages/tensorflow` 目录中。

### Installing on Linux

许多流行的 Linux 发行版基于 Debian，包括 Ubuntu 和 Linux Mint。这些发行版依赖高级打包工具 (`APT`) 来管理包，你可以通过在命令行输入 `apt-get` 来访问它。本讨论解释了如何在这些和类似的操作系统上安装 TensorFlow。

大多数 Linux 发行版已预装 Python，但最好安装完整的开发版本和 `pip`/`pip3`。以下命令为 Python 2 安装两者：

`sudo apt-get install python-pip python-dev`

或者，以下命令为 Python 3 执行安装：

`sudo apt-get install python3-pip python3-dev`

