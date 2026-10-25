

掌握Python编程语言知识，你应该能够看懂本节中的代码。你可以使用这些代码来构建一个系统。

本书的最后一章围绕商业智能的概念展开。我将解释什么是商业智能，以及它与机器学习和人工智能概念的相似之处。你将深入了解商业智能的流程。接着，我将介绍商业智能的不同功能。你将学习如何通过使用这些功能获益。随后，我将阐述商业智能的重要性。你将了解商业智能工作流程的基础架构。你还将学习当今谁在使用商业智能。本章最后全面解释了商业智能的不同优势。

我并不指望你精通Python编程才能阅读和理解这本书。你应该了解Python编程的基础知识。为方便使用，本书中包含了两章关于Python编程的内容。你可以利用这些知识来构建简单的面向对象编程，然后再着手构建深度学习模型。我建议你随身准备一本日记，记下每个重要知识点和你认为需要多练习的代码片段。一旦你在日记中记录了所有内容，就可以进入实践阶段。你练习得越多，构建程序以及理解深度学习模型的工作原理和优势的能力就越强。

应对这场深度学习热潮的最佳方法是，在打开计算机操作系统的同时阅读本书，以便你能够练习和研究遇到的任何有趣内容。别忘了在系统上安装Python 2.7或Python 3。本书中的大部分代码是用Python 2.7编写的。在Python 2.7和Python 3之间存在代码差异的地方，我都已注明。安装这两个版本将帮助你理解其中的细微差别。

## 第一章

### Python基础

本章将带你了解Python编程的基础知识，因为你需要这些知识来使用深度学习技术构建人工智能和机器学习模型。Python是深度学习模型的基础。第一步是检查你的计算机系统上是否已安装Python。如果没有，你需要在计算机操作系统上安装一个Python编辑器。文本编辑器是动态的，它们能识别Python代码，并在你编写时高亮显示不同部分。这使得理解代码结构变得容易。

第一步是了解Python环境。Python在不同操作系统上可能略有不同。通常，市面上有两个可用的Python版本。Python 2和Python 3在不同系统上很容易识别。Python仍在不断演进，因为每种编程语言都在随着新理念和新技术的不断涌现而发展。Python的开发者使这种语言变得强大且更加通用。大多数更改都被认为几乎不可察觉。随着操作系统的发展，较旧的Python版本（如Python 2）可能不如最新的Python 3功能完善。如果你的系统上预安装了这两个版本，建议使用Python 3。

Python 3中有一个解释器，也称为终端窗口。这允许你在不先保存然后运行程序的情况下尝试不同版本的Python。

Python是一种跨平台语言，这意味着你可以根据需要在不同操作系统上运行它。Windows不预装Python，因此你需要下载它并在系统上安装。完成后，你还需要下载并安装文本编辑器。

你需要检查系统上是否已安装Python。打开命令窗口并在“开始”菜单中输入命令。在终端窗口中输入小写的python。如果看到以下提示>>>，则表示系统上已安装Python。如果系统上未安装Python，屏幕上可能会显示错误消息。

如果系统上没有预安装Python，你需要访问www.python.org下载并安装Python。打开网站后，会有一系列可供下载的Python版本。选择你想在系统上安装的版本并点击下载。文件下载到系统后，应启动安装过程。你还应确保在安装过程结束时勾选“Add Python to PATH”选项。这将使系统上的配置过程变得轻松顺畅。

### Python变量

在本节中，你将学习Python程序中可处理的不同数据类型。你还将学习将数据存储在变量中的过程以及如何在程序中使用变量。Python最基本的特性之一是变量。在以下代码中，我将在Python中创建一个变量并为其赋值。

```
>>> x = " I am reading a book on deep learning techniques to build AI models."
>>> print(x)
I am reading a book on deep learning techniques to build AI models.
>>>
```

当我打印程序时，我分配给变量‘x’的同一行内容在我的计算机屏幕上显示出来。Python中的每个变量都保存着某个值，基本上就是与该变量关联的信息。现在我将进入Python编辑器，你将在那里进行实际编码。我将使用相同的变量和值，同时创建一个新变量并为其分配另一个值，以查看Python如何处理它们。

```python
x = " I am reading a book on deep learning techniques to build AI models."
y = " AI is revolutionizing different fields in the business world."
print (x)
print (y)
>>> ================= RESTART =================
>>>
I am reading a book on deep learning techniques to build AI models.
AI is revolutionizing different fields in the business world.
>>> 
```

你可以通过“文件”菜单点击“新建”来启动Python编辑器。将弹出一个新窗口，你可以将其用作Python编辑器。你可以在编辑器中编写代码，然后通过键盘上的F5按钮保存并运行它。代码结果将在Python IDLE屏幕上显示。

在使用Python变量时，你需要遵循一些指南和规则。如果违反其中一些规则，将会导致错误。其他指南将帮助你编写更易于阅读和理解的整洁代码。请确保遵循变量命名规则。变量名可以包含数字、字母和下划线。它们可以以下划线或字母开头，但绝不能以数字开头。例如，你可以将变量命名为x_1，但不能命名为1_x。变量名中不允许有额外的空格。但是，应使用下划线来分隔不同变量名中的单词。例如，x 1不应作为任何变量的名称。你必须避免使用Python中固有的关键字。例如，单词print是Python固有的。变量名必须简短，但应具有描述性。例如，如果你要创建一个描述学生的变量，必须写出完整的单词，而不是只写单词‘s’。Python变量应使用小写，不过即使使用大写字母命名也不会触发错误。最好尽可能避免使用大写字母。

### 数据类型

大多数程序会定义和收集不同种类的数据，然后有目的地使用它们。这使你能够对不同种类的数据进行分类。我将讨论的第一种数据类型称为字符串。字符串乍看之下非常简单。字符串是字符形式。任何包含在单引号或双引号内的内容都称为字符串。

```
x = " I am reading a book on deep learning techniques to build AI models."
y = ' AI is revolutionizing different fields in the business world.'
print (x)
print (y)
>>> ================= RESTART =================
>>> 
I am reading a book on deep learning techniques to build AI models.
```

