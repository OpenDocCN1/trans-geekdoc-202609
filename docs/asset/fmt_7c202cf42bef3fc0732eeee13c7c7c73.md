
```python
print('They said, "We need a new team?"')  # 使用单引号转义
# 转义双引号
print("They said, \" We  need a new team\"")
```

## Python 的文档字符串（Docstring）

在 Python 中，`docstring` 指提供描述的文字，作为函数、模块、方法或类定义中的初始程序语句。（我们稍后会处理）。Python 中的 `docstrings` 使用三引号编写。

### 练习题

此练习将利用我们之前涵盖的几个概念。

a. 给定以下程序语句：`Color1=’red’; color1=’blue’; CoLor1=’yellow’`，解释为什么这三个在 Python 中会被视为三个不同的变量。

b. 考虑以下 Python 程序并识别其错误所在。

```python
student1_age=23                          # 这是第一个学生的年龄
student2_age=19                          # 这是学生的年龄
sotal_age=student1_age +student2_age      # 获取年龄的总和 
print(age)                               # 显示他们的年龄
```

# 第 10 部分：Python 中的运算符

![Part10](img/image00533.jpeg)

到为止，我们一直在使用加法（`+`）运算符，它同时也作为拼接运算符（附加语句）。然而，我们想要扩展运算符列表，这引导我们学习 Python 中的基础运算符。

### 算术运算符

乘法（`*`）、除法（`/`）、减法（`-`）和加法（`+`）是用于处理数字的算术运算符。

### 练习题

编写并运行以下程序

### 差

```python
number1=35                   #声明第一个数字
number2= 12                   #声明第二个数字
difference=number2-number1    #声明差值的作用
print(difference)
```

### 乘法

```python
number1=2                    #声明第一个数字
number2=15                   #声明第二个数字
product=number1*number2       #声明乘积
print(product)
```

### 除法

```python
number1=10                   #声明第一个数字
number2= 50                  #声明第二个数字
division=number2/number1     #声明除法
print(division)
```

### 取模

模运算符用于返回除法后的整数余数。

示例

```python
number1=2                    #声明第一个数字
number2=15                   #声明第二个数字
remainder=number2%number1     #声明余数
print(remainder)
```

### 平方与立方

### 平方

```python
number=3                     #声明数字并赋值
square=number**2
print(square)
```

### 立方

```python
number=5                     #声明数字并赋值
cube=number**3
print(cube)
```

### 练习题

编写并运行以下程序：

```python
I have realized
that programming is passion, 
```

## 字符串的运算符

在 Python 语言中，某些运算符用于帮助拼接。加号用于拼接字符串。

示例

```python
status="I am happy" + "how to write programs"
print(status)
```

```python
many_words="Great Programmer" * 5
print(many_words)
```

### 练习题

```

```

### 总结

我们涵盖了 Python 中变量的构成。变量是命名的存储位置，因此我们有了变量名。有数字变量字符串变量。这些被称为变量类型。在处理变量以及 Python 的任何其他方面，我们将遇到并使用特殊的单词，称为保留字或关键字。关键字是固定的，必须按照指定的方式输入。关键字不能作为变量名或标识符。注释（使用 `#` 或 `"""` 开头）是为了程序的可读性。Python 使用缩进来将代码行分组为块。不同类型的运算符（如算术运算符和字符串运算符）用于允许用户和 Python 内置函数支持的变量操作。

给定以下集合 `trial_set={1,1,2,3,1,5,8,9}`，在 Python 中修正并创建一个集合。

### 注意

在 Python 中，`{}` 会创建一个空字典。集合不需要索引，因为它们是无序的（注：原文此处 `ordered` 为笔误，应为 `unordered`）。

向集合中添加多个元素，我们使用 `update()` 方法。

向集合中添加单个元素，我们使用 `add()` 方法。处理集合时应避免重复项。

### 示例

启动 IDLE。
导航到 File 菜单并点击 New Window（新窗口）。

输入以下：

```python
your_set={6,7}
print(your_set)
your_set.add(4)
print(your_set)
your_set.update([9,10,13])
print(your_set)
your_set.update([23, 37],{11,16,18})
print(your_set)
```

## 从集合中移除元素

`discard(0)` 和 `remove()` 方法用于从集合中清除某个项目。

### 示例

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
set_mine={7,2,3,4,1}
print(set_mine)
set_mine.discard(2)
print(set_mine)        # 输出将为 {7,3,4,1}
set_mine.remove(1)
print(set_mine)        # 输出将为 {7,3,4}
```

## 使用 pop() 方法从集合中移除项目

由于集合是无序的，弹出元素的顺序是随机的。

也可以使用 Python 中的 `clear()` 方法移除集合中的所有项目。

### 示例

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
your_set=set("Today")
print(your_set)
print(your_set.pop())
your_set.pop()
print(your_set)
your_set.clear()
print(your_set)
```

## Python 中的集合操作

我们使用集合来计算集合的差集、交集和并集。

### 示例

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
C={5,6,7,8,9,11}
D={6,9,11,13,15}
```

## 集合并集

集合 `C` 和 `D` 的并集包含两个集合的元素。

在 Python 中，`|` 运算符生成集合的并集。`union()` 也会生成集合的并集。

### 示例

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
C={5,6,7,8,9,11}
D={6,9,11,13,15}
print(C|D)             # 输出: {5,6,7,8,9,11,13,15}
```

### 示例 2

使用 `union()`
启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
C={5,6,7,8,9,11}
D={6,9,11,13,15}
print(D.union(C))      # 输出:{5,6,7,8,9,11,13,15}
```

### 练习

将以下内容重写为集合并找到集合并集。

```python
A={1,2,3,4,4,5,12,14,15}
D={2,3,7,8,9,12,15}
```

## 集合交集

`A` 和 `D` 指两个集合共有的新项目。`&` 运算符用于执行交集操作。也可以使用 `intersection()` 函数。

### 示例

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
A = {11,12,13,14,15}
D= {14,15,16,17,18}
print(A&D)             # {14,15}
```

### 使用 intersection()

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
A = {11,12,13,14,15}
D= {14,15,16,17,18}
print(A.intersection(D))
```

## 集合差集

`A-D` 指仅在 `A` 中而不在 `D` 中的新项目。同样，`D-A` 是在 `D` 中不在 `A` 中的元素集合。`-` 运算符用于计算差集。也可以使用 `difference()` 方法。

### 示例 1

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
A = {11,12,13,14,15}
D= {14,15,16,17,18}
print(A - D)           # 输出:{11,12,13}
```

### 示例 2

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
A = {11,12,13,14,15}
D= {14,15,16,17,18}
print(A.difference(D))
```

### 示例 3

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
A = {11,12,13,14,15}
D= {14,15,16,17,18}
print(D-A)              # 输出为 {16,17}
```

## 对称差集

`A` 和 `D` 中除共同元素以外的集合被称为 `A` 和 `D` 的对称差集。`^` 运算符用于执行对称差集，也可以使用 `symmetric_difference()` 方法。

### 示例 1

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
A = {11,12,13,14,15}
D= {14,15,16,17,18}
print(A^D)              # 输出:{11,12,13,16,17}
```

### 示例 2

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
A = {11,12,13,14,15}
D= {14,15,16,17,18}
print(A.symmetric_difference(D)) # 输出:{11,12,13,16,17}
```

### 挑战

`A^D` 和 `D^A` 相同吗？

### 示例：在集合中添加元素

```python
paint_set = set()
paint_set.add("brown")
print(paint_set)
paint_set.update(["white", "violet"])
print(paint_set)
```

## 超集与子集

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
set1 = {"A", "M"}
set2 = {"M", "O"}
set3 = {"M"}
issub = set1 <= set2
print(issub)
isserset = set1 >= set1
print(isserset)
issub = set3 <= set2
print(issub)
isserset = set2 >= set3
print(isserset)
```

## 集合成员测试

### 示例

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
set_mine = set("pawpaw")
print('p' in set_mine)
```

## 迭代

Python 通常使用 `for` 控制语句持续扫描集合。

### 示例

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
for letter in set("pawpaw"):
    print(letter)
```

## 集合内置函数

### Python 不变集合

就像元组一样，不可变集合是不可变的。为了创建不可变集合，我们使用 `frozenset()` 函数。

### 示例

启动 IDLE。
导航到 File 菜单并点击 New Window。

输入以下：

```python
A = frozenset([11,12,13,14])
D = frozenset([13,14,15,16])
```

### 总结

Python 中的 `Set` 是与数学中的集合等效的数据结构。它可以由各种元素组成；集合中元素的顺序是未定义的。你可以添加和删除集合元素，可以迭代集合元素，对集合执行标准操作（并集、交集、差集）。

# 第 12 部分：Python 字典

![Part12](img/image00535.jpeg)

虽然 Python 中的许多事物都是可迭代的，但并不是所有的都是序列，字典就属于这一类。在本文中，我们将讨论什么是 Python 字典、它是如何工作的以及它的常见应用。

## 什么是 Python 字典？

获取清洁且可操作的数据是数据分析的主要挑战之一。你无法对不可用的数据构建和拟合模型。Python 字典使得读取和更改数据变得更容易，从而使预测建模更具操作性。

Python 字典包含一个 `key: value` 对。Python 字典经过优化，允许在已知键时访问值。

在 Python 字典中，每个键之间用逗号分隔，而每个键值对之间用冒号分隔。此外，虽然字典的键必须是唯一的且不可变的（元组、字符串、整数等），但键值可以是任何类型，并且可以重复任意次数。下面是一个 Python 字典的示例：

## Python 字典是如何工作的？

虽然有许多 Python 字典方法，但有一些需要掌握的基础操作。我们将在本节中介绍其中最重要的部分。

## 创建 Python 字典

要创建一个 Python 字典，你需要将项目（每个项目都有一个键和一个对应的值，表示为 `key: value`）放在大括号内。每个项目都需要用逗号与下一个项目隔开。如上所述，值可以重复并可以是任何类型。相反，键是唯一的且不可变的。还有一个内置函数 `dict()` 可以用它来创建字典。为了方便理解，请注意在本书的其余部分该内置函数写为 `diction()`。以下是一些示例：

## 访问 Python 字典中的项目

在 Python 中访问字典中的项非常简单。你只需要将项的键名放在方括号内即可。这很重要，因为键是唯一的且不可重复的。

### 示例

要获取 `model` 键的值：

```python
k = thisdiction["model"]
```

你也可以使用 Python 字典的另一个方法 `get()` 来访问项。它的样子像所示：

```python
k = thisdiction.get("model")
```

## 如何修改 Python 字典中的值

要更改项的值，你再次需要引用键名。这里有一个示例。

如果你必须将 `year` 键的值从 1890 更改为 2025：

```python
thisdiction = {
  "brand": "Mitsubishi", 
  "model": "Toyota", 
  "year": 1890
}
thisdiction["year"] = 2025
```

## 如何遍历 Python 字典

你可以使用 `for` 循环函数来遍历 Python 中的字典。默认情况下，遍历字典时的返回值将是字典的键。然而，还有其他方法可以返回值。

打印键名：

```python
for k in thisdiction:
  print(k)
```

逐个打印字典中的值：

```python
for k in thisdiction:
  print(thisdiction[k])
```

使用 `values()` 函数返回值的另一种方法：

```python
for k in thisdiction.values():
  print(k)
```

如果你想同时遍历键和值，可以使用 `items()` 函数：

```python
for k, m in thisdiction.items():
  print(k, m)
```

## 如何检查键是否存在于字典

以下是判断某个特定键是否实际存在于 Python 字典的方法：

假设你需要检查字典中是否存在 `model` 键：

```python
thisdiction = {
  "brand": "Mitsubishi", 
  "model": "Toyota", 
  "year": 1890
}
```
