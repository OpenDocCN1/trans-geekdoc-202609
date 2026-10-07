

## 掌握机器学习分类算法

执行图 Annex1.2 所示的步骤后，屏幕将显示图 Annex1.3 所示的内容：

![](img/11af2c4c7dddfed06ed008516c0c6dfb_295_0.png)

图 Annex1.3：创建了一个新的 Notebook

- 3. 注意到新 Notebook 被命名为 Untitled.ipynb。可以通过右键点击右侧面板上的 Notebook 名称，并在弹出的菜单中选择“重命名”（Rename）选项来更改 Notebook 的名称。

## 在 notebook 中添加 markdown

Notebook 可以包含代码和 markdown。要添加 markdown，请点击附图 Annexure1.4 中 **1** 所示的 Notebook 单元格。一旦光标进入单元格，点击如附图 Annexure1.4 中 **2** 所示的“Markdown”：

![](img/11af2c4c7dddfed06ed008516c0c6dfb_296_0.png)

***附图 Annexure1.4：添加 Markdown 的步骤***

## 在 notebook 中添加代码

Notebook 最需的功能是编写并执行代码。要添加代码，请将光标置于需要添加代码的单元格中。确保单元格类型如附图 Annexure1.5 所示为 **Code**（代码）：

![](img/11af2c4c7dddfed06ed008516c0c6dfb_297_0.png)

图 Annex1.5：在 notebook 中添加代码

## 运行 notebook

在 **Run**（运行）菜单选项下（如 **图 Annex1.6** 所示），提供了运行 Notebook 的所有选项。选择合适的选项来运行整个 notebook 或部分 notebook。

## 结论

Jupyter notebook 使用非常简单。本附录讨论了使用本书提供的 Notebook 所需的 Jupyter Notebook 核心功能。通过一些经验，应该充分利用 Jupyter notebook 的所有功能。

![](img/11af2c4c7dddfed06ed008516c0c6dfb_298_0.png)

## 注意事项

- 安装 Jupyter Notebook 的最新信息可以从 Jupyter 网站获取。²

- 最好使用 Jupyter Lab，因为可以使用 Jupyter Lab 同时处理多个 Jupyter Notebook。

- 从网站³ 获取的 Anaconda 包含了 Jupyter Lab 以及其他用于数据科学项目的相关工具。

> 2 https://www.jupyter.org.
> 3 https://www.anaconda.org.

## 加入我们书籍的 Discord 空间

加入书籍的 Discord 工作空间以获取最新更新、优惠、全球科技动态、新发布以及与作者的面对面会议：

https://discord.bpbonline.com

![](img/11af2c4c7dddfed06ed008516c0c6dfb_299_0.png)

## 附录 2

## Python

书中所有的代码都是使用 Python 语言编写的。Python 是一种强大且流行的编程语言，特别是用于开发数据科学应用。本书预期读者已经接触过 Python 编程。然而，如果读者在 Python 编程方面存在知识空白，本附录作为一个桥梁。假设读者具有软件编程经验，并使用过一或多种编程语言。

本附录介绍了 Python 编程的关键细节，因为理解书中的代码是需要这些的。Python 是一门充满活力的语言，需要大量的学习。书中使用了 Python 编程的基础特征，以便代码易于理解。建议对深入学习 Python 编程感兴趣的读者搜索相关的材料。

## 结构

在本章中，我们将讨论以下主题：

- 数据类型
  - 序列数据类型
  - 集合数据类型

### 布尔数据类型

- 运算符
  - 算术运算符
  - 赋值运算符
  - 比较运算符
  - 逻辑运算符
- 语句
  - 条件语句
  - 循环语句

在 Python 中使用库

## 数据类型

Python 是一种动态编程语言。与 C、C++ 或 Java 等语言不同，不需要声明类型。解释器会在运行时确定类型。让我们看看 Python 中的基础数据类型：

### 整数 (Integer)
整数是整数，可以是正数、负数或零，没有小数。

```python
x = 10
y = -5
```

### 浮点数 (Float)
浮点数带有小数点的。

```python
x = 10.5
y = -2.0
```

### 布尔值 (Boolean)
布尔值表示两个值之一：True 或 False。

```python
is_active = True
is_finished = False
```

### 字符串 (String)
字符串是用单引号或双引号括的字符序列。

```python
name = "Alice"
message = 'Hello World'
```

### 列表 (List)
列表是有序的、可变的集合。它可以包含不同的数据类型。

```python
my_list = [1, "apple", 3.14]
```

### 元组 (Tuple)
元组是有序的、不可变的集合。一旦创建，无法更改。

```python
my_tuple = (1, "apple", 3.14)
```

### 字典 (Dictionary)
字典是无序的（Python 3.7 之后）键值对集合。

```python
my_dict = {"name": "Alice", "age": 25}
```

### 集合 (Set)
集合是无序的唯一项目集合。它不允许重复值。

```python
my_set = {1, 2, 3, 3}  # 结果将是 {1, 2, 3}
```

