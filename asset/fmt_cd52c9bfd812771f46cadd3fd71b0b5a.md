
```
$ sha256sum Anaconda3-5.2.0-Linux-x86_64.sh
```

你将获得以下输出。

```
09f53738b0cd3bb96f5b1bac488e5528df9906be2480fe61df40e0e0d19e3d48  Anaconda3-5.2.0-Linux-x86_64.sh
```

### 4. 运行 Anaconda 脚本

第四步是运行 Anaconda 脚本，如下图所示。

```
$ bash Anaconda3-5.2.0-Linux-x86_64.sh
```

命令行将产生以下输出。系统将要求你查看许可协议。持续按 Enter 键直到到达末尾。

```
Output
Welcome to Anaconda3 5.2.0
In order to continue the installation process, please review the license agreement.
Please, press Enter to continue
>>>
...
Do you approve the license terms? [yes|No]
```

当你到达许可协议底部时输入 `Yes`。

### 5. 选择安装位置

同意许可协议后，安装程序将要求你选择安装位置。

直接按 Enter 选择默认位置。如果需要，也可以指定其他位置。

```
Output
Anaconda3 will now be installed on this location: /home/tola/anaconda3
- Press ENTER to confirm the location
- Press CTRL-C to abort the installation
- Or specify a different location below
[/home/tola/anaconda3] >>>
```

按下 Enter 后安装将继续。再次提醒，请耐心等待，因为安装过程需要一些时间才能完成。

### 6. 完成安装

安装完成后你将收到以下结果。如果你想使用 `conda` 命令，请输入 `Yes`。

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

### 2.1.4 使用 Google Colab 云环境

除了 Anaconda 等本地 Python 环境外，您还可以在 Google Colab 上运行深度学习应用，它是 Google 支持 GPU 的深度学习平台。本书中的所有代码均在 Google Colab 上运行。因此，我建议您也使用 Google Colab。

要通过 Google Colab 运行深度学习应用，您只需要一个 Google/Gmail 账号。拥有 Google/Gmail 账号后，您只需访问：<https://colab.research.google.com/>

接下来，点击 **File** -> **New notebook**（文件 -> 新建笔记本），如下截图所示。

![Image00026.jpg](img/Image00026.jpg)

接下来，要使用 GPU 运行代码，请从顶部菜单中选择 **Runtime** -> **Change runtime type**（运行时 -> 更改运行时类型），如下截图所示：

![Image00027.jpg](img/Image00027.jpg)

您应该会看到以下窗口。在此处，从下拉列表中选择 **GPU** 并点击 **Save**（保存）按钮。

![Image00028.jpg](img/Image00028.jpg)

为确保您运行的是最新版本的 TensorFlow，请在 Google Colab 笔记本单元格中执行以下脚本。以下脚本将更新您的 TensorFlow 版本。

```
pip install --upgrade tensorflow
```

要检查您是否真的在运行 TensorFlow 2.0 以上版本，请执行以下脚本。

![Image00029.jpg](img/Image00029.jpg)

使用 Google Cloud，您可以从 Google 云端硬盘导入数据集。执行以下脚本。并点击出现的链接，如下所示：

![Image00030.jpg](img/Image00030.jpg)

系统将提示您允许 Google Colab 访问您的 Google 云端硬盘。点击 **Allow**（允许）按钮，如下所示：

![Image00031.jpg](img/Image00031.jpg)

您将看到出现一个链接，如下图所示（此处链接已模糊处理）。

![Image00032.jpg](img/Image00032.jpg)

复制该链接，并将其粘贴到 Google Colab 单元格的空白字段中，如下所示：

![Image00033.jpg](img/Image00033.jpg)

这样，您就可以将数据集从 Google 云端硬盘导入到您的 Google Colab 环境中。

### 2.2 Python 快速入门

如果您熟悉 Python 编程语言的基本概念，可以跳过本节。对于 Python 绝对初学者，本节简要概述了 Python 的一些最基本概念。Python 是一门非常庞大的编程语言，本节绝非一本完整 Python 书籍的替代品。但是，如果您想了解各种操作和命令在 Python 中是如何执行的，欢迎继续学习本节的其余内容。

#### 2.2.1 编写您的第一个程序

您已经在计算机上安装了 Python，并以 Anaconda 的形式建立了一个独特的环境。现在，是时候编写您的第一个程序了，即 Hello World！

要在 Anaconda 中编写程序，您必须启动 Anaconda Navigator。在 Windows 搜索框中搜索 **Anaconda Navigator**。现在，点击 **Anaconda Navigator** 应用程序图标，如下图所示。

![Image00034.jpg](img/Image00034.jpg)

点击应用程序后，Anaconda 的仪表板将打开。仪表板为您提供了编写代码的无数工具。我们将使用其中最流行的 **Jupyter Notebook**，在本书中编写和解释代码。

![Image00035.jpg](img/Image00035.jpg)

**Jupyter Notebook** 位于仪表板顶部往下的第二个位置。即使您无法访问互联网，也可以使用 **Jupyter Notebook**，因为它直接在您的默认浏览器中运行。打开 **Jupyter Notebook** 的另一种方法是在 Windows 搜索栏中输入 **Jupyter Notebook**。随后，点击 **Jupyter Notebook** 应用程序。该应用程序将在浏览器的新标签页中打开。

![Image00036.jpg](img/Image00036.jpg)

**Jupyter Notebook** 自身仪表板右上角有一个 **New**（新建）按钮，您需要点击它以打开新文档。将出现一个包含多个选项的下拉菜单。点击 **Python 3**。

![Image00037.jpg](img/Image00037.jpg)

一个新的 Python 笔记本将出现供您编写程序。如下所示。

![Image00038.jpg](img/Image00038.jpg)

**Jupyter Notebook** 由单元格组成，从上图可以明显看出，其布局非常简单直接。您将在这些单元格中编写代码。让我们在 **Jupyter Notebook** 中编写我们的第一个 Python 程序。

![Image00039.jpg](img/Image00039.jpg)

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

#### 2.2.2 Python 变量和数据类型

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

![Image00040.jpg](img/Image00040.jpg)

**输出：**

`<class 'str'>` `<class 'int'>` `<class 'float'>` `<class 'bool'>` `<class 'list'>` `<class 'tuple'>` `<class 'dict'>`

#### 2.2.3 Python 运算符

Python 编程语言包含以下类型的运算符：

1.  算术运算符
2.  逻辑运算符
3.  比较运算符
4.  身份运算符
5.  成员运算符

### Python 运算符与控制流

#### 算术运算符

算术运算符用于在 Python 中执行算术运算。下表总结了 Python 支持的算术运算符。假设 `X = 20`，`Y = 10`。

![Arithmetic Operators Table](img/Image00041.jpg)

以下是带有输出的算术运算符示例：

**脚本 3：**

![Script 3 Code](img/Image00042.jpg)

**输出：**

```
30
10
200
2.0
10240000000000
```

#### 逻辑运算符

逻辑运算符用于在 Python 中执行逻辑与、或、非运算。下表总结了逻辑运算符。此处，`X` 为 `True`，`Y` 为 `False`。

![Logical Operators Table](img/Image00043.jpg)

以下示例解释了 Python 逻辑运算符的用法。

**脚本 4：**

![Script 4 Code](img/Image00044.jpg)

**输出：**

1. `False`
2. `True`
3. `True`

#### 比较运算符

顾名思义，比较运算符用于比较两个或多个操作数。根据操作数之间的关系，比较运算符返回布尔值。下表总结了 Python 中的比较运算符。此处，`X` 为 `20`，`Y` 为 `35`。

![Comparison Operators Table](img/Image00045.jpg)

以下示例演示了比较运算符的实际应用：

**脚本 5**

![Script 5 Code](img/Image00046.jpg)

**输出：**

`False` `True` `False` `True` `False` `True`

#### 赋值运算符

赋值运算符用于将值赋给变量。下表总结了赋值运算符。此处，`X` 为 `20`，`Y` 等于 `10`。

![Assignment Operators Table](img/Image00047.jpg)

请查看脚本 6 以了解 Python 赋值运算符的实际应用。

**脚本 6：**

![Script 6 Code](img/Image00048.jpg)

**输出：**

```
30
30
10
200
2.0
0
10240000000000
```

#### 成员运算符

成员运算符用于判断某项是否为项目集合的成员。成员运算符有两种：`in` 运算符和 `not in` 运算符。以下脚本演示了 `in` 运算符的用法。

**脚本 7：**

![Script 7 Code](img/Image00049.jpg)

**输出：**

`True`

以下是 `not in` 运算符的示例。

**脚本 8：**

![Script 8 Code](img/Image00050.jpg)

**输出：**

`True`

#### 条件语句

Python 中的条件语句用于实现条件逻辑。条件语句帮助你决定是否执行特定的代码块。Python 中主要有三种类型的条件语句：

1.  **If 语句**
2.  **If-else 语句**
3.  **If-elif 语句**

##### If 语句

如果你只需检查单个条件，且不关心备选条件，可以使用 `if` 语句。例如，如果你想检查 `10` 是否大于 `5`，并据此打印一条语句，可以使用 `if` 语句。`if` 语句求值的条件返回布尔值。如果 `if` 语句求值的条件为真，则执行 `if` 语句后面的代码块。值得注意的是，在 Python 中，新代码块从新行开始，并相对于外层块缩进（通常为一个制表符或四个空格）。在下面的示例中，条件 `10 > 5` 求值为真。因此，`if` 语句后面的代码块执行，并在控制台打印一条消息。

**脚本 9：**

![Script 9 Code](img/Image00051.jpg)

**输出：**

`Ten is greater than 5`

##### If-Else 语句

当你想在 `if` 语句的条件返回假时执行备选代码时，`if-else` 语句非常有用。例如，在下面的示例中，条件 `5 > 10` 将返回假。因此，`else` 语句后面的代码块将执行。

**脚本 10：**

![Script 10 Code](img/Image00052.jpg)

**输出：**

`10 is greater than 5`

##### If-Elif 语句

当你需要求值多个条件时，`if-elif` 语句非常方便。例如，在下面的示例中，我们首先检查 `5 > 10`，其求值为假。接下来，`elif` 语句求值条件 `8 < 4`，这也返回假。因此，最后一个 `else` 语句后面的代码块执行。

**脚本 11：**

![Script 11 Code](img/Image00053.jpg)

**输出：**

`5 is not greater than 10 and 8 is not smaller than 4`

#### 迭代语句

迭代语句（也称为循环）用于迭代执行特定代码片段。Python 中主要有两种类型的迭代语句：

1.  **For 循环**
2.  **While 循环**

##### For 循环

`for` 循环用于迭代执行一段代码特定的次数。当您确切知道想要运行代码的迭代或重复次数时，应使用 `for` 循环。`for` 循环会遍历项目集合。在下面的示例中，我们使用 `range()` 方法创建了一个包含五个整数的集合。接下来，`for` 循环迭代五次并打印集合中的每个整数。

**脚本 12：**

```
![](img/Image00054.jpg)
```

**输出：**

```
0 1 2 3 4
```

##### While 循环

`while` 循环会持续执行特定的一段代码，除非评估条件变为 false。例如，下面脚本中的 `while` 循环会持续执行，除非变量 `c` 变得大于 10。

**脚本 13：**

```
![](img/Image00055.jpg)
```

**输出：**

```
0 1 2 3 4 5 6 7 8 9
```

### 2.2.6 函数

任何编程语言中的函数都用于实现需要在代码的不同位置多次执行的代码片段。在这种情况下，您无需反复编写冗长的代码片段，只需定义一个包含该代码片段的函数，然后即可在代码中任何需要的地方调用该函数。

要在 Python 中创建函数，需使用 `def` 关键字，后跟函数名称以及一对左括号和右括号。函数定义后，必须调用它才能执行函数体内的代码。要调用函数，只需指定函数名称，后跟一对左括号和右括号即可。

在下面的脚本中，我们创建了一个名为 `myfunc` 的函数，它使用 `print()` 方法在控制台打印一条简单语句。

**脚本 14：**

```
![](img/Image00056.jpg)
```

**输出：**

```
This is a simple function
```

您也可以向函数传递值。这些值在函数调用的括号内传递。但是，您也必须在函数定义中指定参数名。
