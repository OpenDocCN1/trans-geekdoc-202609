

## 输出

安装完成。您是否希望安装程序将 Anaconda3 的安装位置添加到您的 `/home/tola/.bashrc` 的 PATH 中？ `[yes|no]` `[no]`>>>

此时，您还将有下载 Visual Studio Code 的选项。输入 `yes` 或 `no` 分别选择安装或拒绝。

### 7. 激活安装

使用以下命令激活您全新的 Anaconda3 安装。

```
$ source ~/.bashrc
```

### 8. 测试安装

您也可以使用 `conda` 命令测试安装。

```
$ conda list
```

恭喜。您已成功在 Linux 系统上安装了 Anaconda。

## 2.1.4 使用 Google Colab 云环境

除了 Anaconda 等本地 Python 环境外，您还可以在 Google Colab 上运行深度学习应用，它是 Google 支持 GPU 的深度学习平台。本书中的所有代码均在 Google Colab 上运行。因此，我建议您也使用 Google Colab。

要通过 Google Colab 运行深度学习应用，您只需要一个 Google/Gmail 账号。拥有 Google/Gmail 账号后，您只需访问：<https://colab.research.google.com/>

接下来，点击 **File** -> **New notebook**（文件 -> 新建笔记本），如下截图所示。

![Image00026.jpg](Image00026.jpg)

接下来，要使用 GPU 运行代码，请从顶部菜单中选择 **Runtime** -> **Change runtime type**（运行时 -> 更改运行时类型），如下截图所示：

![Image00027.jpg](Image00027.jpg)

您应该会看到以下窗口。在此处，从下拉列表中选择 **GPU** 并点击 **Save**（保存）按钮。

![Image00028.jpg](Image00028.jpg)

为确保您运行的是最新版本的 TensorFlow，请在 Google Colab 笔记本单元格中执行以下脚本。以下脚本将更新您的 TensorFlow 版本。

```
pip install --upgrade tensorflow
```

要检查您是否真的在运行 TensorFlow 2.0 以上版本，请执行以下脚本。

![Image00029.jpg](Image00029.jpg)

使用 Google Cloud，您可以从 Google 云端硬盘导入数据集。执行以下脚本。并点击出现的链接，如下所示：

![Image00030.jpg](Image00030.jpg)

系统将提示您允许 Google Colab 访问您的 Google 云端硬盘。点击 **Allow**（允许）按钮，如下所示：

![Image00031.jpg](Image00031.jpg)

您将看到出现一个链接，如下图所示（此处链接已模糊处理）。

![Image00032.jpg](Image00032.jpg)

复制该链接，并将其粘贴到 Google Colab 单元格的空白字段中，如下所示：

![Image00033.jpg](Image00033.jpg)

这样，您就可以将数据集从 Google 云端硬盘导入到您的 Google Colab 环境中。

## 2.2 Python 快速入门

如果您熟悉 Python 编程语言的基本概念，可以跳过本节。对于 Python 绝对初学者，本节简要概述了 Python 的一些最基本概念。Python 是一门非常庞大的编程语言，本节绝非一本完整 Python 书籍的替代品。但是，如果您想了解各种操作和命令在 Python 中是如何执行的，欢迎继续学习本节的其余内容。

### 2.2.1 编写您的第一个程序

您已经在计算机上安装了 Python，并以 Anaconda 的形式建立了一个独特的环境。现在，是时候编写您的第一个程序了，即 Hello World！

要在 Anaconda 中编写程序，您必须启动 Anaconda Navigator。在 Windows 搜索框中搜索 **Anaconda Navigator**。现在，点击 **Anaconda Navigator** 应用程序图标，如下图所示。

![Image00034.jpg](Image00034.jpg)

点击应用程序后，Anaconda 的仪表板将打开。仪表板为您提供了编写代码的无数工具。我们将使用其中最流行的 **Jupyter Notebook**，在本书中编写和解释代码。

![Image00035.jpg](Image00035.jpg)

**Jupyter Notebook** 位于仪表板顶部往下的第二个位置。即使您无法访问互联网，也可以使用 **Jupyter Notebook**，因为它直接在您的默认浏览器中运行。打开 **Jupyter Notebook** 的另一种方法是在 Windows 搜索栏中输入 **Jupyter Notebook**。随后，点击 **Jupyter Notebook** 应用程序。该应用程序将在浏览器的新标签页中打开。

![Image00036.jpg](Image00036.jpg)

**Jupyter Notebook** 自身仪表板右上角有一个 **New**（新建）按钮，您需要点击它以打开新文档。将出现一个包含多个选项的下拉菜单。点击 **Python 3**。

![Image00037.jpg](Image00037.jpg)

一个新的 Python 笔记本将出现供您编写程序。如下所示。

![Image00038.jpg](Image00038.jpg)

**Jupyter Notebook** 由单元格组成，从上图可以明显看出，其布局非常简单直接。您将在这些单元格中编写代码。让我们在 **Jupyter Notebook** 中编写我们的第一个 Python 程序。

![Image00039.jpg](Image00039.jpg)

上述脚本基本上使用 `print()` 方法在输出中打印一个字符串值。`print()` 方法用于将传递给它的任何字符串打印到控制台。如果您看到以下输出，则表示您已成功运行第一个 Python 程序。

**输出：** Welcome to Data Visualization with Python

现在，让我们从变量和数据类型开始探索其他一些重要的 Python 概念。

> **要求 – Anaconda、Jupyter 和 Matplotlib**
>
> *   本书中的所有脚本均通过 **Jupyter notebook** 执行。因此，您应该安装了 **Jupyter notebook**。
> *   不用说，我们将使用 **Matplotlib** 库。
> *   在本章之前，还应安装 **Numpy** 和 **Pandas** 库。
>
> **动手时间 – 源代码**
>
> 本章所有脚本的源代码 IPython 笔记本均可在 SharePoint 存储库中找到。我建议您亲自编写本章中的所有代码，并查看是否能获得本章提到的相同输出。

### 2.2.2 Python 变量和数据类型

编程语言中的数据类型是指该语言能够处理的数据类型。Python 支持的主要数据类型如下：

1.  字符串
2.  整数
3.  浮点数
4.  布尔值
5.  列表
6.  元组
7.  字典

变量是存储实际数据的内存地址的别名。存储在内存地址中的数据或值可以通过变量名进行访问和更新。与 C++、Java 和 C# 等其他编程语言不同，Python 是弱类型（动态类型）语言，这意味着您在创建变量时不必指定数据类型。相反，数据类型在运行时确定。

以下示例演示了如何创建不同的数据类型以及如何将它们存储在相应的变量中。该脚本还通过 `type()` 函数打印变量的类型。

**脚本 2：**

![Image00040.jpg](Image00040.jpg)

**输出：**
`<class 'str'>` `<class 'int'>` `<class 'float'>` `<class 'bool'>` `<class 'list'>` `<class 'tuple'>` `<class 'dict'>`

### 2.2.3 Python 运算符

Python 编程语言包含以下类型的运算符：

1.  算术运算符
2.  逻辑运算符
3.  比较运算符
4.  身份运算符
5.  成员运算符

