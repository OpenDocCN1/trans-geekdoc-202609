
所有条件语句、循环以及执行逻辑结构的额外编程逻辑代码都被称为控制流语句。我们已经通过各种示例对条件语句和循环进行了广泛的介绍。现在，您应该记住，我们即将学习的控制流语句对于程序执行非常重要。如果使用得当，它们可以成功地跳过、终止或继续逻辑。现在让我们通过示例开始学习它们吧。开始！

## break 语句

`break` 语句用于一次性结束整个循环（当前循环体）。它前面带有一个逻辑判断。例如，下面是一个普通的循环：

```
for sample in range(10):
    print("-------")
    print sample
```

执行上述循环语句后，程序将按顺序输出 0 到 9 的整数。程序将不会停止运行，直到循环结束。此时，如果您希望程序仅输出 0 到 2 的数字，则需要在指定时间结束循环（执行完第三次循环语句后）。接下来，演示使用 `break` 结束循环的过程。

**示例：break 语句**

```
end=1
for end in range(10):
    end+=1
    print("-------")
    if end==3:
        break
    print(end)
```

在示例中，当程序进行到第三次循环时，因为 `end` 的值为 3，程序将停止并打印截至此时的循环。

## continue 语句

`continue` 的作用是结束本次循环，然后执行下一次循环。它将查看逻辑值并继续执行流程。接下来，通过一个案例演示 `continue` 语句的用法。

**示例：continue 语句**

```
sample=1
for sample in range(10):
    sample+=1
    print("-------")
    if sample==3:
        continue
    print(sample)
```

在示例中，当程序执行第三次循环时，因为 `sample` 的值为 3，程序将终止本次循环而不输出 `sample` 的值，并立即执行下一次循环。

**注意：**

1. `break`/`continue` 只能在循环中使用，否则不能单独使用。
2. `break`/`continue` 在嵌套循环中只作用于最近的一层循环。

## pass 语句

Python 中的 `pass` 是一个空语句，其出现是为了保持程序结构的完整性。`pass` 不执行任何操作，通常用作占位符。`pass` 语句的用法如下示例所示。

**示例：pass 语句**

```
for alphabet in 'University':
    if letter == 'v':
        pass
    print ('This is the statement')
    print ('Use this alphabet', letter)
print ("You can never see me again" )
```

在上述示例中，当程序执行 `pass` 语句时，因为 `pass` 是空语句，程序将忽略该语句并按顺序执行后续语句。

## else 语句

早些时候，在学习 `if` 语句时，`else` 语句被发现在 `if` 条件语法的作用域之外。事实上，除了判断语句外，Python 中的 `while` 和 `for` 循环也可以使用 `else` 语句。当在循环中使用时，`else` 语句仅在循环完成后执行，即 `break` 语句也会跳过 `else` 语句块。接下来，我们将通过一个案例演示，以便您更好地理解 `else` 代码块。

**示例：else 语句**

```
result = 0
while result < 5:
    print(result, " is less than 5")
    result = result + 1
else:
    print(result, " is not less than 5")
```

在示例中，`else` 语句在 `while` 循环终止后执行，即当 `result` 的值等于 5 时，程序执行 `else` 语句。

至此，我们完成了 Python 编程中控制流语句的简要介绍。仅在必要时使用控制流语句始终很重要。如果在没有任何用例的情况下使用它们，它们可能会在编程过程中开始制造不必要的阻碍。在下一章中，我们将简要介绍 Python 中的决策树。让我们开始吧！

# 第 14 章：Python 中的决策树

在上一章中，我们讨论了控制流语句，现在我们将讨论一个与控制流语句相关的概念。决策树是一种逻辑结构，可用于根据特定标准做出决策。树是一种基本数据结构，通常用于存储和排序事物。我们现在将详细讨论 Python 中的决策树。让我们开始吧！

## 什么是决策树？

决策树是 Python 中的一个编程概念，可用于做出决策。它们也用于根据给定的输入做出决策。决策树主要用于机器学习中，以创建回归和监督算法。我们可以使用包含大量算法的 `pandas` 库在 Python 中实现决策树。在下一节中，我们将详细讨论决策树的实现。请继续跟随！

## 决策树的实现

这些决策树通常通过依赖所提出的问题来工作。如果给定的逻辑满足条件，则做出决策。如果不满足，则传递给另一个存在的节点。

### 如何选择？

要选择一个节点，我们需要按如下方式操作。

```
if ( node logic) {
    If it statisfies then save()
    else proceed.next()
}
```

这段代码的目的是：语句块由各种复杂的逻辑实体进行检查。完成检查后，如果不满足条件，则将跳转到下一个节点执行相同的操作。如果满足条件，则将树的位置值存储在 error 中以供进一步评估。

## 在 Python 中安装决策树

要安装或使用决策树，您需要安装 `pandas` 和 `scikit-learn` 并使用依赖项来使用它们。您可以使用 `pip` 来安装它们。格式如下：

```
pip install {Enter the platform name here}
```

## 决策树算法

对于任何数据结构，遵循提到的算法都很重要。现在，我们将根据 Python 编程语言详细解释决策树算法。请继续跟随！

**步骤 1：** 首先，您需要将所有存在的数据视为根集合。

**步骤 2：** 在下一步中，您需要了解存在的属性，并需要处理参数以显示结果。

**步骤 3：** 在此步骤中，您需要对用于比较的值执行递归操作。

**步骤 4：** 在最后一步中，您需要使用不同的统计和伪方法来理解节点计算。

## 决策树的数据导入

要导入用于决策树的数据，您需要使用 `pandas` 第三方库。您可以获取 URL 详细信息，也可以使用 CSV 格式发送信息。您甚至可以使用 `import` 语句来完成任务。

## 决策树的数据切片

一次性向决策树发送大量信息通常很难。为了解决这个问题，Python 提供了数据切片操作，可以根据您的需求划分数据。要执行出色的决策树操作，掌握基尼指数、熵等复杂的计算机科学主题非常重要，这些超出了本书的范围。如果您有兴趣构建自己的决策树算法，我们建议您深入学习信息增益机制。

至此，我们完成了关于 Python 中决策树的简要解释。在下一章中，我们将详细学习异常处理。让我们开始吧！

# 第 15 章：Python 基础编程

在 Python 中，处理错误对于使程序正常运行至关重要。每当 Python 程序因警告和错误而停止运行时，建议向最终用户展示停止的原因。Python 程序员应通过理解 Python 中异常处理的本质来培养这项技能，这对于使程序平稳运行非常关键。本章将结合示例详细讨论此内容。

## 异常简介

在 Python 中，程序执行期间产生的错误称为**异常**，例如列表索引越界、打开不存在的文件等。例如，运行以下程序代码时会发生错误：

```
open(data.txt)
FileNotFound { There is no such file: 'data.txt' }
```

## 异常类

在 Python 中，所有异常类都是 `Exception` 的子类。异常类定义在 `Exceptions` 模块中，该模块位于 Python 的内置命名空间中，可直接使用无需导入。

在前面的章节中，程序每次在执行时遇到错误都会抛出异常。如果异常对象未被处理和捕获，程序将带着回溯信息终止执行，回溯信息包括错误名称（如 `NameError`）、原因及发生错误的行号。

以下是一些常见的异常：

### 1. NameError

尝试访问未声明的变量会引发 `NameError`。例如：

```
print(dude)
```

错误信息如下：

```
NameError: There is no such namespace
```

上述信息表明解释器在任何命名空间中均未找到 `foo`。

### 2. ZeroDivisionError

当除数为零时，会抛出 `ZeroDivisionError` 异常。例如：

```
1/0
```

错误信息如下：

```
ZeroDivisionError: division by zero is not possible
```

任何数值除以零都会导致上述异常。

### 3. SyntaxError

当解释器发现 `SyntaxError` 时，会抛出语法错误异常。例如：

```
list = ["two","four","six"]
for result in list
print(result)
```

在上述示例中，由于 `for` 循环后缺少冒号，程序会报以下错误信息：

```
SyntaxError: This is not the correct syntax
```

`SyntaxError` 异常是唯一不在运行时发生的异常。它表示 Python 代码中不正确的结构，导致程序无法执行。这些错误通常发生在编译时，解释器无法将脚本转换为字节码。

### 4. IndexError

当使用序列中不存在的索引时，会抛出 `IndexError` 异常。例如：

```
example = []
example[0]
```

在上述示例中，列表中没有元素。当使用索引 0 访问列表的第一个元素时，会出现以下错误信息：

```
IndexError: There is no such index
```

上述信息表明列表的索引值超出了列表的范围。

### 5. KeyError

当在映射中使用不存在的键时，会抛出 `KeyError` 异常。例如：

```
Thisresult = {'number':'explain','port':7232}
Thisresult['interpret']
```

在上述示例中，`myDict` 字典中只有 `host` 和 `port` 两个键。当获取 `interpret` 键对应的值时，会出现以下错误信息：

```
KeyError: 'interpret'
```

上述信息表明字典中存在一个不存在的键 `server`。

### 6. FileNotFoundError

当尝试打开一个不存在的文件时，会抛出文件未找到 `IOError` 异常。例如：

```
second = open("test")
```

在上述示例中，使用 `open` 方法打开名为 `test` 的文件或目录，会出现以下错误信息：

```
FileNotFoundError: { There is nothing that exists with this name}
```

上述信息表明未找到名为 `test` 的文件或目录。

### 7. AttributeError

当尝试访问未知对象属性时，会抛出 `AttributeError` 异常。例如：

```
class Aeroplane(object):
    fly
flight = Aeroplane()
Aeroplane.color = "white"
```

在上述示例中，`Aeroplane` 类未定义任何属性和方法。创建 `Aeroplane` 类的实例后，`color` 属性被动态添加到 `flight` 引用的实例上，随后访问其 `color` 和 `name` 属性时出现以下错误信息：

```
AttributeError: 'Aeroplane' object has no attribute 'value'
```

上述信息表明 `color` 属性定义在 `Aeroplane` 实例中，因此可通过 `flight.color` 访问。然而 `name` 属性未定义，故访问 `name` 属性时会报错。

下一节将详细讨论异常处理。

## 异常处理

Python 处理异常的能力非常强大。它能准确反馈错误信息，帮助开发者精准定位问题的位置和原因。Python 使用 `try-except` 语句处理异常。其中 `try` 语句用于检测异常，`except` 语句用于捕获异常。

### 捕获简单异常

`try-except` 语句定义一段用于监控异常的代码，并提供处理异常的机制。最简单的 `try-except` 语句格式如下：

```
try:
    # Here is the place where logic goes
except:
    # Here we enter the error details
```

当 `try` 块中的语句发生错误时，程序将不再继续执行 `try` 块中的后续语句，而是直接执行 `except` 中处理异常的语句。

为便于读者理解，以下示例演示如何使用简单的 `try-except` 语句捕获两数相除可能引发的异常。

**示例：Simple Exceptions.py**

```
try:
    print("-"*64)
    first = input("You should enter the first entity")
    second = input("You should enter the second entity")
    print(int(first)/int(second))
    print("-"*64)
except ZeroDivisionError:
    print("Number 64 cannot be divided")
```

在该示例中，`try` 子句中的 `input` 函数接收用户输入的两个值，其中第一个值作为被除数，第二个值作为除数。如果除数为 0，程序将抛出 `ZeroDivisionError` 异常。此时 `except` 子句将捕获该异常并打印异常信息。

运行程序并在控制台输入第一个数 64、第二个数 5，结果将显示。通过仔细分析，你将理解异常处理的工作原理。从结果可以看出，当程序出现异常时，程序不会终止，而是会根据自定义的消息提醒用户。

注意：只要监控到错误，程序就会执行 `except` 语句，不再执行 `try` 中未执行的语句。

### 捕获异常的描述信息

一个 `except` 子句可捕获多个异常。将示例中的两个错误合并到一个 `except` 子句如下：

```
try:
    first = input("Enter the first entity")
    second = input("Enter the second entity")
    print(int(first)/int(second))
except (ZeroDivisionError, ValueError):
    print("Get a value")
```

此时，无论上述两个异常中的任意一个发生，都会打印 `except` 内的语句。但仅打印一条错误信息无助于区分不同错误。可使用 `as` 关键字获取系统反馈的错误信息。

### 捕获所有异常

即使程序能处理多个异常，也无法穷尽所有异常，仍可能有异常未被捕获。在示例中，若编写程序时将 `num1` 误写为 `nmn1`，将获得类似以下的错误信息：

```
NameError: name 'nmn1' is not defined
```

此种情况下，可在原有基础上捕获 `SyntaxError` 异常。若程序中有数十个错误，逐个捕获非常麻烦。为解决此问题，`except` 子句可不指定异常类型，从而处理任意类型的异常。

为便于读者理解，此处添加捕获所有异常的功能示例。

**示例：Captures All Exceptions**

```
# captures all exceptions
try:
    first = input("Use this as first entity")
    second = input("Use this as second entity")
    print(int(first)/int(second))
except:
    print("You got this error")
```

在该示例中，`except` 语句未指定异常类型，程序所有可能的错误均在该语句中统一处理。从两次运行结果可见，所有异常的提示信息相同。

捕获所有异常的另一种方式是在 `except` 语句后使用 `Exception` 类。由于 `Exception` 类是所有异常类的父类，因此可捕获所有异常。

### 未捕获异常时的处理

在 `if` 语句中，当所有条件均不满足时执行 `else` 语句。同理，若 `try` 语句未捕获任何错误信息，则不执行任何 `except` 语句，而是执行 `else` 语句。

为便于读者理解，我们在上述示例基础上添加 `else` 语句。

**示例：else statement.py**

```
try:
    first = input("Use this as first entity")
    second = input("Use this as second entity")
    print(int(first)/int(second))
except:
    print("You got this error")
else:
    print("The program runs normally and no exception is caught")
```
