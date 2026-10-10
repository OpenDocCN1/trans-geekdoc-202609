
# TensorFlow 的 Python 入门指南

![](img/55c2af1cab44d6186a8b2008b93f459f_0_0.png)

> 我想将这本书献给我的父母——愿这能给他们的生活带来快乐和幸福。

## 序言

### 什么是 Jupyter？

- Matplotlib 中的随机数据点
- 将 Python 数组转换为 TF Array
- TensorFlow `batch()` 运算符 (1)

## 前言

### 目标是什么？

本书的目标是向高级学者展示各种 Python 库的代码示例，这些示例对于用 Python 编写 TensorFlow 程序非常有用。前四章包含 Python 相关的材料，第五章介绍了 TensorFlow。然而，第五章并不包含任何展示如何在 TensorFlow 中解决机器学习问题（如线性回归、逻辑回归等）的代码示例。

如果你已经达到了此处所学内容的极限，并希望获取关于 TensorFlow 1.x 的更深层次的技术知识，请考虑在本序言前面提到的推荐书籍，以及即将出版的关于 TensorFlow 2 的书籍。

书中出现的代码示例和图表可以通过发送邮件至出版者 `info@merclearning.com` 来获取。

---

## 第 5 章 TensorFlow 简介

### 什么是 TensorFlow？

- TensorFlow 架构（高视角）
- TensorFlow 特性

### TensorFlow 用例

- 其他基于 TensorFlow 的工具包
- TensorFlow 2 怎么样？
- 为什么使用 TF 1.x 而不是 TF 2？

### 什么是 TensorFlow Tensor（张量）？

- TensorFlow 数据类型
- TensorFlow 原始类型
- TensorFlow 图
- TensorFlow 版本号
- 使用 `tf.Session()` 的 TensorFlow 图
- TF Session 中的占位符 `Placeholders` 和 `feed_dict`
- TF Session 中的常量和变量
- TensorFlow 中的常量（回顾）
- `tf.rank()` API
- TF Tensor 的形状 `Shape`
- TensorFlow 中的占位符（回顾）
- TF 占位符和 `feed_dict`
- TensorFlow 中的变量（回顾）
- TF Variable 与 TF Tensor
- TensorFlow 图中的变量初始化
- TensorFlow 图执行
- TF 图中的算术运算
- TF 图与内置函数
- 在 TF 中计算三角值
- 在 TF 中计算指数值
- 在 TF 中使用 for 循环
- 在 TF Eager 执行模式下使用 for 循环
- 在 Eager 执行模式下使用循环
- while 循环中的 `tf.less()` API
- TF `one_hot()` API
- TensorFlow 中的数组 (1)
- TensorFlow 中的数组 (2)
- TensorFlow 中的数组 (3)
- TF 中两个数组相乘 (CPU)
- TF 中两个数组相乘 (GPU)
- 将 Python 数组转换为 TF Array

### 什么是 TensorBoard？

- Google Colaboratory
- 其他云平台
- GCP SDK

### 总结

## 第 6 章 TensorFlow 数据集

- TensorFlow 数据集
- TensorFlow 数据集的的基本步骤
- 简单的 TensorFlow 数据集
- TensorFlow Ragged Constants（不规则常量）与张量（可选）
- 什么是 Lambda 表达式？
- TensorFlow 中的 Lambda 表达式
- 什么是迭代器？
- TensorFlow 迭代器
- TensorFlow 可复迭代器
- TensorFlow `filter()` 运算符
- TensorFlow `TextLineDataset` (1)
- TensorFlow `TextLineDataset` (2)
- TensorFlow `TextLineDataset` (3)
- TensorFlow `batch()` 运算符 (1)
- TensorFlow `batch()` 运算符 (2)
- TensorFlow `map()` 运算符 (1)
- TensorFlow `map()` 运算符 (2)
- TensorFlow `flatmap()` 运算符 (1)
- TensorFlow `flatmap()` 运算符 (2)
- TensorFlow `flat_map()` 和 `filter()` 运算符
- TensorFlow `repeat()` 运算符
- TensorFlow `take()` 运算符
- 结合 `map()` 和 `take()` 运算符
- 结合 `zip()` 和 `batch()` 运算符
- 结合 `zip()` 和 `take()` 运算符
- TF 数据集与随机数 (1)
- TF 数据集与随机数 (2)
- 来自 CSV 文件的 TF 数据集
- 使用 `tf.estimators` 和 `tf.layers`（可选）
- 什么是 TF Estimators？
- TF Estimators 与 `tf.data.Dataset`（可选）
- 什么是 `tf.layers`？
- TensorFlow 的其他有用部分
- 什么是 TFRecord？
- 简单的 TFRecord
- 总结

# PYTHON 导论

本章将对 Python 进行快速介绍，并提供用于安装 Python 模块的工具，以及如何在 Python 中处理某些数据类型的示例。本章不包含任何关于 Python 的历史信息，也不包含诸如创建 Python 类、继承、线程或任何超出介绍性材料的主题。原因非常简单：本章的目的是为了让你熟悉足够的 Python 知识，以便你能够学习后续章节中的内容。

本章的第一部分涵盖了 Python 的安装、一些 Python 环境变量以及如何使用 Python 解释器。你将看到 Python 代码示例，以及如何将 Python 代码保存为文本文件，并从命令行中启动这些文件。本章的第二部分将向你展示如何处理简单的数据类型，如数字、分数和字符串。本章的最后部分讨论了异常以及如何在 Python 脚本中使用它们。

如果你喜欢阅读文档，最好的第三方文档出版物之一是 Doug Hellman 编写的 pymotw（“每周 Python 模块”），他的主页地址为：

`http://pymotw.com/2/`

> 注意：书中的 Python 脚本适用于 Python 2.7.5，尽管它们的大部分可能可能与 Python 2.6 兼容，但这些脚本需要经过某种程度的转换（例如 `print()` 命令的语法）才能与 Python 3 兼容。

# PYTHON 工具

Anaconda Python 分发版适用于 Windows、Linux 和 Mac，可以在此处下载：

`http://continuum.io/downloads`

Anaconda 非常适合如 NumPy 和 SciPy 等模块（将在第 2 章和第 4 章中讨论），如果你是 Windows 用户，Anaconda 看起来是更好的替代方案。

## easy_install 和 pip

当你需要安装 Python 模块时，`easy_install` 和 `pip` 都非常易于使用。

每当你需要安装 Python 模块时（书中有很多这样的模块），请使用以下语法运行 `easy_install` 或 `pip`：

```
easy_install <module-name>
pip install <module-name>
```

> **注意**：基于 Python 的模块更容易安装，而用 C 编写代码的模块通常更快，但在安装方面更困难。

## virtualenv

`virtualenv` 工具允许你创建隔离的 Python 环境，其主页在此：

`http://virtualenv.org/en/latest/virtualenv.html`

`virtualenv` 解决了为不同应用程序保留正确依赖项和版本（间接地保留权限）的问题。如果你是 Python 初学者，现在可能不需要 `virtualenv`，但请记住这个工具。

## IPython

另一个非常好工具是 `IPython`（曾获得 Jolt 奖），它的主页在这里：

`http://ipy.org/install.html`

`IPython` 的两个非常棒的功能是制表扩展（tab expansion）和“?”

制表扩展的示例如下：

```python
Python 2.7.5 -- Anaconda 1.6.1 (x86_64) -- (default, Jun 28
              2013, 22:20:13)
Type "copyright", "credits" or "license" for more
Information.
```

```
IPython 0.13.2 -- An enhanced Interactive Python.
? -> Introduction and overview of IPython's features.
%quickref -> IPython's own help system.
help
object? -> Details about 'object', use 'object??' for
              extra details.
```

```
[1] di divmod
%dirs dir divmod
```

在之前的会话中，如果你输入字符 `di`，`IPython` 将显示：

```
[1] di divmod
%dirs dir divmod
```

如果你在提示符下输入 `dir`，`IPython` 会显示：

```
[1] dir divmod
%dirs dir divmod
```

## 伴侣文件

书中出现的代码示例和图表可以通过发送邮件至出版者 `info@merclearning.com` 来获取。
