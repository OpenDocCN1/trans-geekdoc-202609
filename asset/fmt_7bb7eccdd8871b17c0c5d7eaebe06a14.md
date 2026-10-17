
由于 `continue` 接下来跳到循环顶部，你不必将 `print` 语句嵌套在 `if` 测试中；只有在 `continue` 未运行时才会到达 `print`。如果这听起来像其他语言中的“goto”，那应该是。Python 没有“goto”语句，但既然 `continue` 让你能在程序中跳来跳去，你可能听过的许多关于“goto”的可读性和可维护性警告也适用于此。`continue` 可能应该谨慎使用，尤其是当你刚开始学习 Python 时。例如，如果将 `print` 嵌套在 `if` 下，最后一个示例可能会更清晰：

```
x = 10
while x:
    x = x - 1
    if x % 2 == 0:        # 偶数？- 打印
        print(x, end=' ')
```

### Break

`break` 语句导致立即退出循环。由于如果到达 `break`，循环内后面的代码不会执行，你有时也可以通过使用 `break` 来避免嵌套。例如，这里有一个简单的交互式循环，它使用 `input` 输入数据，并在用户在姓名提示符处输入 "stop" 时退出：

```
>>> while True:
...     name = input('Enter name:')
...     if name == 'stop': break
...     age = input('Enter age: ')
...     print('Hello', name, '=>', int(age) ** 2)
...
Enter name: bob
Enter age: 40
Hello bob => 1600
Enter name: sue
Enter age: 30
Hello sue => 900
Enter name: stop
```

请注意，这段代码在将年龄输入平方之前，使用 `int` 将其转换为整数；正如你所记得的，这是必要的，因为 `input` 将用户输入作为字符串返回。你会注意到 `input` 在文件结束时也会引发异常（例如，如果用户在 Windows 上输入 `Ctrl-Z` 或在 Unix 上输入 `Ctrl-D`）；如果这很重要，请用 `try` 语句包装输入。

### 循环 Else

当与循环 `else` 子句结合使用时，`break` 语句通常可以消除其他语言中使用的搜索状态标志的需求。例如，以下代码通过搜索大于 1 的因子来确定正整数 `y` 是否为质数：

```
x = y // 2
while x > 1:
    if y % x == 0:        # 余数
        print(y, 'has factor', x)
        break             # 跳过 else
    x -= 1
else:                     # 正常退出
    print(y, 'is prime')
```

它不是设置一个标志在循环退出时测试，而是在找到因子的地方插入 `break`。这样，循环 `else` 子句可以假设只有在未找到因子时才会执行；如果你没有遇到 `break`，该数字就是质数。跟踪这段代码看看它是如何工作的。

如果循环体从未执行，循环 `else` 子句也会运行，因为在这种情况下你也不会运行 `break`；在 `while` 循环中，如果头部的测试一开始就是假，就会发生这种情况。因此，在前面的示例中，如果 `x` 最初小于或等于 1（例如，如果 `y` 是 2），你仍然会得到 "is prime" 消息。

此示例确定质数，但只是非正式地。根据严格的数学定义，小于 2 的数不被视为质数。为了完全精确，此代码对于负数也会失败，对于没有小数位的浮点数则会成功。另请注意，由于 `/` 迁移到了“真除法”（我们需要整数除法来截断余数，而不是保留它们！），其代码在 Python 3.X 中必须使用 `//` 而不是 `/`。如果你想尝试这段代码，请务必查看将它包装在函数中以供重用的练习。

总之，我们已经成功讨论了 Python 中的循环。这使你作为程序员的工作变得更轻松。接下来要讨论的是 Python 编程中的函数。下一章更多的是为你作为程序员准备的，而不是编程本身。让我们抚摸下面的知识吧。

## 第 10 章 – Python 编程中的用户自定义函数

Python 最大的重要性之一在于用户友好的函数。在 Python 中，用户友好的函数是一组执行特定任务的声明 —— 一种典型的组织组件，它使你能够在程序的不同部分重复使用一段代码。函数的使用提高了程序的清晰度和可理解性，并通过减少代码重复和将复杂任务分解为更易管理的片段，使编程变得更加高效。函数也称为例程、子程序、方法或子程序。它们可以作为参数传递、赋值给变量或存储在集合中。

客户端特性的 Python 函数由 `def` 语句创建或定义，并遵循以下语法：

```
def function_name(parameter list):
    Function Body/Explanations
```

缩进的声明构成了函数体，并在调用函数时执行。调用函数时，圆括号内的参数变为实参。函数体可以包含多个 `return` 语句，它们可以放置在函数块的任何位置。`return` 语句结束函数调用，并返回 `return` 关键字后面表达式的值。不带表达式的 `return` 语句返回特殊值 `None`。如果函数体内没有 `return` 语句，则函数结束时通过返回值 `None` 来表示。

`docstring` 是函数标题后的一个可选说明，用于解释函数的功能。虽然不是必需的，但使用 `docstring` 记录代码是一种良好的编程习惯。

下面是一个打印“我爱披萨！”的基本函数：

```
def love_pizza():
    print "I cherish Pizza!"
```

下面是一个带有参数和 `return` 关键字的函数：

```
def absolute_value(number):
    if number >= 0:
        return number
    else:
        return - number

print(absolute_value(8))
print(absolute_value(- 7))
```

在上面的示例中，`number` 是函数 `absolute_value` 的参数。它充当变量名并保存传入实参的值。

执行上述代码时的结果如下：

```
8
-7
```

下面是一个包含 if-else 语句的函数示例：

```
def shutdown(yn):
    if yn.lower() == "y":
        return("Closing scrapes and closing down")
    elif yn.lower() == ("n"):
        return("Shutdown dropped")
    else:
        return("Please check your reaction.")

print(shutdown("y"))
print(shutdown("n"))
print(shutdown("x"))
```

Python Shell 将显示：

```
Shutting scrapes and closing down
Shutdown dropped
If it's not too much trouble check your reaction.
```

函数可以接受多个参数并将它们用于计算：

```
def calculator(x, y):
    return x * y + 2

print(calculator(3,2))
print(calculator(4,6))
```

运行代码，你将得到输出：

```
8
26
```

### 函数可以调用其他函数

函数可以执行各种类型的操作，例如进行简单计算和打印内容。它们也可以调用另一个函数。例如：

```
def members_total(n):
    return n * 3

def org_total(m):
    return members_total(m) + 5
```

要查看代码的作用，请输入以下打印指令：

```
print(org_total(4))
print(org_total(8))
print(org_total(5))
```

你将得到以下结果：

```
17
29
20
```

### 局部变量的作用域和生命周期

变量的作用域是指程序中能够识别该变量的部分。在函数内部定义的变量和参数具有局部作用域，从函数外部不可见。另一方面，变量的生命周期是指它在内存中存在的时间。其生命周期与函数的执行相对应，当你从函数返回时结束。一旦到达 `return` 语句，变量的值就会被丢弃，函数将无法回顾变量之前的值。

在本章结束时，你已经从程序员或用户的角度了解了 Python 语言。我确信如果我说 Python 是最好的编程语言，你会同意我的观点。在种种可能性中，你已经看到了 Python 中扩展的工作方式。在下一章中，你将学习如何在 Python 中进行分组。分组是必要的，因为当你编程处理相关复杂对象的列表时，不需要真正区分它们。唯一要做的就是使用类自动化。这很神奇，对吧？让我们进入下一章。

## 第 11 章 – Python 中的类与面向对象编程

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

### 类语法

要定义一个类，可以使用 `class` 这一保留关键字，后跟类名和一个冒号。按照惯例，所有类名均以大写字母开头。例如：

```
class Students:
    pass
```

要创建一个继承自 `object` 的类（新式类写法）：

```
class Students(object):
```

### `__init__()` 方法

创建类的实例后，需要调用 `__init__()` 函数。该函数初始化它所创建的对象。它至少接受参数 `self`，这是 Python 的约定，用于标识正在创建的对象。

示例：

```
class Students:
    def __init__(self):

class Employees(object):
    def __init__(self, name, rate, hours):
```

在类中使用的函数称为**方法**。因此，当 `__init__()` 函数用于初始化类时，它就是一个方法。

### 实例变量

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

### 继承

**继承**是一种 Python 机制，允许一个类采用另一个类的方法和属性。此功能使用户能够创建越来越复杂的类，这些类从其父类或基类继承方法或变量，并使编程更加高效。以下是定义一个继承父类所有变量和函数的类的语法：

```
class ChildClass(ParentClass):
```

为了演示，你可以创建另一个类 `Resigned`，它将从 `Employees` 类继承并接受一个额外的变量 `status`：
