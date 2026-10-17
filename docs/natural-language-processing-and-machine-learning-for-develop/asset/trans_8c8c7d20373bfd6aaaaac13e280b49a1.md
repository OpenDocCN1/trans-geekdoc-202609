
向量空间可以看作一维向量空间。向量 `i` = \[1,0\] 是一个单位向量，它是该向量空间的所谓基向量，因为该空间中的任意其他向量都是该向量的倍数。

欧几里得平面可以看作二维向量空间。单位向量 `i` = \[1,0\] 和 `j` = \[0,1\] 是单位向量，它们构成该向量空间的基，因为该空间中的任意其他向量都是 `i` 和 `j` 的线性组合。请注意，向量 `i` 和 `j` 的点积为 0，这意味着它们是正交的。然而，集合 {2\***i**, 3\***j**} 中的向量不是单位向量，但它们仍然构成欧几里得平面的基。

再举一个例子，集合 {**i**+**j**, **i**} 中的向量也构成一个基，尽管它们不正交，且其中一个向量不是单位向量。然而，任何基可以转换为给定向量空间中另一个基，这意味着任何基都可以转换为由正交单位向量组成的基（请在线上搜索此说法的证明）。

在三维欧几里得空间中，向量集合 {`i`,`j`,`k`} 构成一个正交单位基，其中单位向量 `i`、`j` 和 `k` 分别为 \[1,0,0\]、\[0,1,0\] 和 \[0,0,1\]。

在一般的 n 维向量空间 V 中，基本集 S 由 n 个正交单位向量组成。如果你创建一个矩阵 M，其行是基中向量的集合，那么矩阵 M 的逆矩阵存在，因为其行是线性独立的。

事实上，若 n 个未知数的 n 条线性方程的系数矩阵 M 是可逆的（当且仅当），则该方程组有唯一解。统计软件包中包含一个或多个用于解决线性方程组的算法。

# A P P E N D I X B

# INTRODUCTION TO PYTHON

本附录介绍 Python，包含有关安装 Python 模块的有用工具、基本 Python 构造以及如何在 Python 中处理某些数据类型的信息。

本附录的第一部分介绍如何安装 Python、一些 Python 环境变量以及如何使用 Python 解释器。你将看到 Python 代码示例，以及如何在命令行中保存 Python 代码文件并运行它们。本附录的第二部分展示如何处理简单的数据类型，如数字、分数和字符串。本附录的最后部分讨论异常处理及其在 Python 脚本中的使用。

## **NOTE**

*Python 3.x* 的代码示例适用于 Python 3.x。

## **Python 工具**

Anaconda Python 发行版可用于 Windows、Linux 和 Mac，并可在此处下载：

*[http://continuum.io/downloads](http://continuum.io/downloads)*

Anaconda 特别适合用于 NumPy（在第 [1](#ch01.xhtml) 节中讨论) 和 scipy（本书未讨论）等模块，如果你是 Windows 用户，Anaconda 似乎是更好的选择。

### **easy_install 和 pip**

当你需要安装 Python 模块（本书中有许多模块）时，可以使用 easy\_install 或 pip，语法如下：

easy\_install <module-name> pip install <module-name> 

## **NOTE**

Python\-*基础的模块更易安装，而使用 C 编写的模块通常运行更快，但安装更为复杂。

### **virtualenv**

virtualenv 工具用于创建隔离的 Python 环境，其主页位于：

*[http://www.virtualenv.org/en/latest/virtualenv.html](http://www.virtualenv.org/en/latest/virtualenv.html)*

该工具解决了不同应用程序保持正确的依赖关系和版本（间接影响权限）的问题。如果你是 Python 新手，目前可能不需要 virtualenv，但请记住这个工具。

### **IPython**

另一个非常好的工具是 IPython（曾获得 Jolt 奖），其主页位于：

*[http://ipython.org/install.html](http://ipython.org/install.html)*

在命令行中输入 `ipython` 即可启动 IPython：

`ipython`

该命令的输出如下：

Python 3.9.1 (default, Feb  3 2021, 07:04:15) Type 'copyright', 'credits' or 'license' for more information IPython 7.22.0 -- An enhanced Interactive Python. Type '?' for help.   In \[1\]: 

在 IPython 提示符中输入问号（“?”）可以看到以下信息：

IPython -- An enhanced Interactive Python \=========================================   IPython 提供与标准 Python 解释器完全兼容的替代，并具备便捷的 shell 功能、特殊命令、命令历史机制以及输出结果缓存。在系统命令行中输入 'ipython -h' 可查看可用的命令行选项。本文档仅描述交互功能。   **GETTING HELP** \------------   在 IPython 中，有多种方式获取帮助：     ?         -> 介绍 IPython 的功能（此屏幕）。   object?   -> 关于 'object' 的详细信息。   object??  -> 更详细、详细的关于 'object' 的信息。   %quickref -> IPython 特定语法和魔法命令的快速参考。   help      -> 调用 Python 自带的帮助系统。 如果在终端中使用 IPython，按 'q' 可以退出此界面。

最后，在命令行提示符中输入 quit 即可退出 IPython 交互环境。

下一节展示如何检查机器上是否已安装 Python，以及在哪里可以下载 Python。

## **Python 安装**

在下载任何内容之前，先检查机器上是否已安装 Python（如果你使用的是 Macbook 或 Linux 机器，可能已经安装）。在命令行中输入以下命令：

`python -V`

Macbook 的输出示例如下：

Python 3.9.1 

## **NOTE**

*请在你的机器上安装 Python 3.9（或尽可能接近该版本），以确保与本书中测试的 Python 版本一致。*

如果需要在机器上安装 Python，请访问 Python 官网并选择下载链接，或直接访问以下网站：

*[http://www.python.org/download](http://www.python.org/download)*

此外，PythonWin 为 Windows 提供，其主页位于：

*[http://www.cgl.ucsf.edu/Outreach/pc204/pythonwin.html](http://www.cgl.ucsf.edu/Outreach/pc204/pythonwin.html)*

使用任何可以创建、编辑和保存文本文件的文本编辑器保存 Python 脚本。

安装并配置好 Python 后，你即可使用本书中的 Python 脚本。

## **设置 PATH 环境变量（仅限 Windows）**

