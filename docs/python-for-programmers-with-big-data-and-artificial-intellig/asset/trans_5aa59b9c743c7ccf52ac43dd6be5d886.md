

- IPython交互环境中的单个代码段。
- 完整的应用程序，称为脚本。
- Jupyter Notebooks——一种方便的交互式、基于Web浏览器的环境，您可以在其中编写和执行代码，并将代码与文本、图像和视频混合。

我们将在1.5节的试驾中逐一演示每种方式。

`examples`文件夹为每个章节包含一个子文件夹。这些文件夹名为`ch##`，其中`##`是两位数的章节编号`01`到`16`——例如`ch01`。除了`Chapters 13, 15 and 6`，每个章节的文件夹包含以下项目：

- `snippets_ipynb`——包含该章节Jupyter Notebook文件的文件夹。
- `snippets_py`——包含Python源代码文件的文件夹，其中我们展示的每个代码段之间用空行隔开。您可以将这些代码段复制并粘贴到IPython或您创建的新Jupyter Notebook中。
- 脚本文件及其支持文件。

`Chapter 13`包含一个应用程序。`Chapters 15 and 6`分别说明了在`ch15`和`ch16`文件夹中查找所需文件的位置。

## 安装ANACONDA

我们在本书中使用易于安装的Anaconda Python发行版。它几乎包含您使用我们示例所需的一切，包括：

- IPython解释器，
- 我们使用的大多数Python和数据科学库，
- 本地Jupyter Notebooks服务器，以便您加载和执行我们的笔记本，以及
- 各种其他软件包，例如Spyder集成开发环境（IDE）——本书中我们仅使用IPython和Jupyter Notebooks。

从以下网址下载适用于Windows、macOS或Linux的Python 3.x Anaconda安装程序：https://www.anaconda.com/download/。

下载完成后，运行安装程序并按照屏幕上的说明操作。为确保Anaconda运行正确，安装后请勿移动其文件。

## 更新ANACONDA

接下来，确保Anaconda已更新。在您的系统上按如下方式打开命令行窗口：

- 在macOS上，从**应用程序**文件夹的**实用程序**子文件夹中打开**终端**。
- 在Windows上，从“开始”菜单中打开**Anaconda提示符**。在这样做以更新Anaconda（如您在此处所做）或安装新包（稍后讨论）时，请通过右键单击并选择**更多 > 以管理员身份运行**以*管理员*身份执行**Anaconda提示符**。（如果在开始菜单中找不到Anaconda提示符，只需在屏幕底部的**此处键入以搜索**字段中搜索即可。）
- 在Linux上，打开您系统的**终端**或shell（这因Linux发行版而异）。

在系统的命令行窗口中，执行以下命令将Anaconda的已安装包更新到最新版本：

- 1. `conda update conda`
- 2. `conda update --all`

## 包管理器

上面使用的`conda`命令调用**conda包管理器**——您在本书中将使用的两个关键Python包管理器之一。另一个是`pip`。包包含安装给定Python库或工具所需的文件。在整本书中，您将使用`conda`安装其他包，除非这些包无法通过`conda`获得，在这种情况下您将使用`pip`。有些人偏好独家使用`pip`，因为它目前支持更多包。如果您使用`conda`安装包时遇到问题，请改用`pip`。

## 安装PROSPECTOR静态代码分析工具

您可能希望使用Prospector分析工具分析Python代码，该工具会检查代码中的常见错误并帮助您改进代码。要安装Prospector及其使用的Python库，请在命令行窗口中运行以下命令：

```
pip install prospector
```

## 安装JUPYTER-MATPLOTLIB

我们使用名为Matplotlib的可视化库实现了多个动画。要在Jupyter Notebooks中使用它们，必须安装名为ipympl的工具。在您先前打开的终端、Anaconda命令提示符或shell中，逐个执行以下命令：

https://github.com/matplotlib/jupyter-matplotlib。

```
conda install -c conda-forge ipympl
conda install nodejs
jupyter labextension install @jupyter-widgets/jupyterlab-manager
jupyter labextension install jupyter-matplotlib
```

## 安装其他包

Anaconda为您附带了大约300个流行的Python和数据科学包，例如NumPy、Matplotlib、pandas、Regex、BeautifulSoup、requests、Bokeh、SciPy、SciKit-Learn、Seaborn、Spacy、sqlite、statsmodels等更多包。在整本书中，您需要安装的其他包数量将很少，我们会按需提供安装说明。当您发现新包时，其文档将说明如何安装。

## 获取Twitter开发者账户

如果您打算使用我们的“Twitter数据挖掘”章节和后续章节中的任何基于Twitter的示例，请申请Twitter开发者账户。Twitter现在要求注册才能访问其API。要申请，请在以下网址填写并提交申请表：

https://developer.twitter.com/en/apply-for-access

Twitter审核每个申请。撰写本文时，个人开发者账户正在立即获批，而公司账户申请需要数天到数周时间。批准不保证。

## 某些章节需要互联网连接

使用本书时，您需要互联网连接来安装各种其他Python库。在某些章节中，您将为基于云的服务注册帐户，主要是为了使用其免费层。有些服务需要信用卡来验证您的身份。在少数情况下，您将使用非免费的服务。在这些情况下，您将利用供应商提供的货币信用额度，以便在不产生费用的情况下试用其服务。注意：某些基于云的服务在设置后会产生费用。使用此类服务完成我们的案例研究时，请务必及时删除您分配的资源。

## 程序输出的细微差异

执行我们的示例时，您可能会注意到我们显示的结果与您自己的结果之间存在一些差异：

- 由于跨操作系统在执行浮点数字计算（例如-123.45、7.5或0.0236937）时存在差异，您可能会看到输出中的微小差异，尤其是小数点右侧远处的数字。
- 当我们显示出现在单独窗口中的输出时，我们会裁剪窗口以删除其边框。

## 获取问题解答

在线论坛使您能够与其他Python程序员交流并获得Python问题的解答。流行的Python和一般编程论坛包括：

- python-forum.io
- StackOverflow.com
- https://www.dreamincode.net/forums/forum/29-python/

此外，许多供应商为其工具和库提供论坛。您在本书中将使用的大多数库都在github.com上进行管理和维护。某些库维护者通过特定库的GitHub页面上的Issues选项卡提供支持。

如果无法在网上找到问题的答案，请参阅本书的网页：http://www.deitel.com ²

² 我们的网站正在进行重大升级。如果您找不到需要的内容，请直接写信至deitel@deitel.com与我们联系。

您现在已准备好开始阅读《Python for Programmers》。希望您喜欢这本书！

## 1. 计算机与Python简介

### 学习目标

在本章中，您将：

- 了解计算领域的激动人心的最新进展
- 回顾面向对象编程基础知识
- 了解Python的优势
- 了解本书中将使用的关键Python和数据科学库
- 试驾IPython解释器的交互模式以执行Python代码
- 执行一个为柱状图添加动画的Python脚本
- 创建并试驾一个基于Web浏览器的Jupyter Notebook以执行Python代码
- 了解“大数据”有多大，以及它增长得有多快
- 阅读关于流行移动导航应用的大数据案例研究
- 了解人工智能——计算机科学与数据科学的交叉点

### 大纲

- 1. 简介
- 2. 对象技术基础知识快速回顾
- 3. Python
- 4. 关键在于类库！
  - 4.1 Python标准库
  - 4.2 数据科学库

