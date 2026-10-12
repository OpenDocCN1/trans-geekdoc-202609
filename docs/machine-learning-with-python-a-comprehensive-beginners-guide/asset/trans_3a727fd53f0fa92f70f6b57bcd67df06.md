

# 第 11 章 – Python 中的类与面向对象编程

在本章中，你将了解如何在 Python 中进行“分类”，即对项目进行分组。这至关重要，因为你需要将本应列出的单词进行分组。Python 是一门**面向对象编程语言**，这意味着它操作并处理称为**对象**的数据结构。对象可以是 Python 中可命名的任何事物——数字、函数、浮点数、字符串、类、方法等。这些对象在 Python 中具有同等地位。它们可以用在任何需要对象的地方。你可以将它们赋值给变量、列表或字典。它们也可以作为参数传递。每个 Python 对象都是一个类。类本质上是一种用于组织、管理和创建具有相似属性和方法的对象的方式。在本书中，Python 中的函数远不止是给编译器看的代码生成规范——Python 函数是彻头彻尾的对象，存储在各自独立的内存块中。因此，它们可以在程序中自由传递并间接调用。它们还支持与调用关系不大的操作——属性存储和注释。既然 Python 函数是对象，你就可以编写常规生成它们的程序。函数对象可以赋值给不同的名称、传递给其他函数、嵌入数据结构、从一个函数返回到另一个函数，等等，就像它们是简单的数字或字符串一样。函数对象还碰巧支持一项特殊任务：可以通过在函数表达式后的括号中列出参数来调用它们。即便如此，函数仍与其他对象属于同一大类。这通常被称为**一等对象模型**；它在 Python 中无处不在，也是函数式编程的重要组成部分。我们将在本章和下一章更全面地探讨这种编程模式；因为其主题建立在应用函数的理念之上，所以函数必须被视为数据。我们在前面的示例中已经看到了函数的一些常规用例，但快速回顾一下可以强化对象模型。

例如，`def` 语句中使用的名称实际上没有什么特别之处：它只是当前作用域中赋值的一个变量，就好像它出现在了 `=` 号的左侧。`def` 运行后，函数名只是对一个对象的引用——你可以随意将该对象重新赋值给不同的名称，并通过任何引用来调用它：

```
>>> def echo(message): # 名称 echo 赋值给函数对象
...     print(message)
>>> echo('Direct call') # 通过原始名称调用对象
Direct call
>>> x = echo # 现在 x 也引用该函数
>>> x('Indirect call!') # 通过名称加 () 调用对象
Indirect call!
```

由于参数是通过赋值对象来传递的，将函数作为参数传递给其他函数同样简单。“被调用者”随后只需在括号中加上参数即可调用传入的函数：

```
>>> def indirect(func, arg):
...     func(arg) # 通过加上 () 调用传入的对象
>>> indirect(echo, 'Argument call!') # 将函数传递给另一个函数
Argument call!
```

你甚至可以将函数对象塞进数据结构中，就像它们是整数或字符串一样。例如，以下代码将函数嵌入元组列表中两次，作为一种活动表。由于 Python 的复合类型（如这些）可以包含任何类型的对象，这里也没有特殊情况：

```
>>> schedule = [ (echo, 'Spam!'), (echo, 'Ham!') ]
>>> for (func, arg) in schedule:
...     func(arg) # 调用嵌入在容器中的函数
Spam!
Ham!
```

这段代码只是遍历 `schedule` 列表，每次循环用一个参数调用 `echo` 函数（请看 for 循环头部的元组解包赋值）。函数也可以被创建并返回以供他处使用——这种模式下创建的闭包还保留了外围作用域的状态：

```
>>> def make(label): # 创建一个函数但不调用它
...     def echo(message):
...         print(label + ':' + message)
...     return echo
>>> F = make('Spam') # 外围作用域中的标签被保留
>>> F('Ham!') # 调用返回的函数
Spam: Ham!
>>> F('Eggs!')
Spam: Eggs!
```

Python 通用的一等对象模型和无类型声明造就了一种极其灵活的编程语言。在 Python 中，你可以定义自己的类，从自己定义的类或内置类继承，并实例化定义的类。

## 类语法

要定义一个类，可以使用 `class` 这一保留关键字，后跟类名和一个冒号。按照惯例，所有类名均以大写字母开头。例如：

```
class Students:
    pass
```

要创建一个继承自 `object` 的类（新式类写法）：

```
class Students(object):
```

## `__init__()` 方法

创建类的实例后，需要调用 `__init__()` 函数。该函数初始化它所创建的对象。它至少接受参数 `self`，这是 Python 的约定，用于标识正在创建的对象。

示例：

```
class Students:
    def __init__(self):

class Employees(object):
    def __init__(self, name, rate, hours):
```

在类中使用的函数称为**方法**。因此，当 `__init__()` 函数用于初始化类时，它就是一个方法。

## 实例变量

当你向 `def __init__()` 添加除 `self` 以外的参数时，你需要包含实例变量，以便该类的任何实例对象都与你创建的实例相关联。例如：

```
class Employees(object):
    def __init__(self, name, rate, hours):
        self.name = name
        self.rate = rate
        self.hours = hours
```

在上面的示例中，`self.name`、`self.rate` 和 `self.hours` 是实例变量。当你创建 `Employees` 类的实例时，每个成员都将拥有通过 `__init__` 方法初始化的变量。为了演示，你可以创建或“实例化”`Employees` 类的新成员：

```
staff = Employees("Wayne", 20, 8)
manager = Employees("Dwight", 35, 8)
supervisor = Employees("Melinda", 100, 8)
```

然后你可以使用 print 命令查看与 `Employees` 类成员关联的实例变量：

```
print(staff.name, staff.rate, staff.hours)
print(supervisor.name, supervisor.rate, supervisor.hours)
print(manager.name, manager.rate, manager.hours)
```

Python Shell 将显示此输出：

```
Wayne 20 8
Dwight 35 8
Melinda 100 8
```

以下是整个代码在编辑器/文件窗口中的编写方式：

文件窗口：`employees.py`

这是输出：

## 继承

**继承**是一种 Python 机制，允许一个类采用另一个类的方法和属性。此功能使用户能够创建越来越复杂的类，这些类从其父类或基类继承方法或变量，并使编程更加高效。以下是定义一个继承父类所有变量和函数的类的语法：

```
class ChildClass(ParentClass):
```

为了演示，你可以创建另一个类 `Resigned`，它将从 `Employees` 类继承并接受一个额外的变量 `status`：

```
class Employees(object):
    def __init__(self, name, rate, hours):
        self.name = name
        self.rate = rate
        self.hours = hours

staff = Employees("Wayne", 20, 8)
manager = Employees("Dwight", 35, 8)
manager = Employees("Melinda", 100, 8)

print(staff.name, staff.rate, staff.hours)
print(supervisor.name, supervisor.rate, supervisor.hours)
print(manager.name, manager.rate, manager.hours)

class Resigned(Employees):
    def __init__(self, name, rate, hours, status):
        self.name = name
        self.rate = rate
        self.hours = hours
        self.status = status

exemp_1 = Resigned("Dorothy", 32, 8, "resigned")
exemp_2 = Resigned("Malcolm", 48, 8, "surrendered")

print(exemp_1.name, exemp_1.rate, exemp_1.hours, exemp_1.status)
print(exemp_2.name, exemp_2.rate, exemp_2.hours, exemp_2.status)
```

当代码执行时，Python Shell 上的输出将如下所示。总而言之，Python 让每个人的事情变得更简单；其中之一已在本章中解释。你不需要继续列出大量单词，因为没时间做那种事。当你为一个致力于餐饮或烹饪的网站编写代码时，这最有效。下一章将带你了解如何专门使用 Python 生成器。诸如“我如何使编码自动化？”、“我在哪里可以找到函数及其用法？”等问题将得到解决。让我们一起进入下一章；全都是 Python 编程语言。

