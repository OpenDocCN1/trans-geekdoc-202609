

调用函数时，可以使用关键字参数以任意顺序传递参数。为演示关键字参数，我们重新定义 rectangle_area 函数——这次没有默认参数值：

点击此处查看代码图像

```
In [1]: def rectangle_area(length, width):
    ...:     """Return a rectangle's area."""
    ...:     return length * width
    ...:
```

调用中的每个关键字参数均采用 parametername=value 形式。以下调用表明关键字参数的顺序无关紧要——它们不需要与函数定义中对应参数的位置匹配：

点击此处查看代码图像

```
In [2]: rectangle_area(width=5, length=10)
Out[3]: 50
```

在每个函数调用中，必须将关键字参数放在函数的位置参数之后——即，任何未指定参数名的参数。此类参数根据参数列表中的参数位置，从左到右分配给函数的参数。关键字参数还有助于提高函数调用的可读性，尤其是对于参数众多的函数。

## 4.11 任意参数列表

具有任意参数列表的函数（如内置函数 min 和 max）可以接收任意数量的参数。考虑以下 min 调用：

```
min(88, 75, 96, 55, 83)
```

该函数的文档说明 min 有两个必需参数（名为 arg1 和 arg2）以及一个形式为 *args 的可选第三个参数，表明该函数可以接收任意数量的额外参数。参数名前的 * 告诉 Python 将任何剩余参数打包为一个元组，并传递给 args 参数。在上述调用中，参数 arg1 接收 88，参数 arg2 接收 75，参数 args 接收元组 (96, 55, 83)。

### 定义具有任意参数列表的函数

让我们定义一个可以接收任意数量参数的 `average` 函数：

```
In [1]: def average(*args):
    ...:     return sum(args) / len(args)
    ...:
```

按照惯例，参数名使用 `args`，但你可以使用任何标识符。如果函数有多个参数，则 `*args` 参数必须是 *最右侧* 的参数。

现在，让我们使用不同长度的任意参数列表多次调用 `average`：

```
In [2]: average(5, 10)
Out[2]: 7.5

In [3]: average(5, 10, 15)
Out[3]: 10.0

In [4]: average(5, 10, 15, 20)
Out[4]: 12.5
```

要计算平均值，请用 `args` 元组的元素总和（由内置函数 `sum` 返回）除以元组的元素数量（由内置函数 `len` 返回）。请注意，在我们的 `average` 定义中，如果 `args` 的长度为 0，则会发生 `ZeroDivisionError`。在下一章中，你将看到如何在不解包元组元素的情况下访问它们。

### 将可迭代对象的各个元素作为函数参数传递

你可以解包元组、列表或其他可迭代对象的元素，以将它们作为单独的函数参数传递。在函数调用中，当对可迭代参数应用 * 运算符时，会解包其元素。以下代码创建一个包含五个元素的 `grades` 列表，然后使用表达式 `*grades` 将其元素解包为 `average` 的参数：

```
In [5]: grades = [88, 75, 96, 55, 83]

In [6]: average(*grades)
Out[6]: 79.4
```

上述调用等效于 average(88, 75, 96, 55, 83)。

## 4.12 方法：属于对象的函数

方法只是你使用以下形式在对象上调用的函数：

```
object_name.method_name(arguments)
```

例如，以下会话创建字符串变量 s 并将其赋值为字符串对象 'Hello'。然后会话调用对象的 lower 和 upper 方法，这些方法生成包含原字符串全小写和全大写版本的新字符串，而 s 保持不变：

```
In [1]: s = 'Hello'

In [2]: s.lower() # call lower method on string object s
Out[2]: 'hello'

In [3]: s.upper()
Out[3]: 'HELLO'

In [4]: s
Out[4]: 'Hello'
```

Python 标准库参考位于

```
https://docs.python.org/3/library/index.html
```

描述了内置类型和 Python 标准库中类型的方法。在“面向对象编程”章节中，你将创建称为类的自定义类型，并定义可在这些类的对象上调用的自定义方法。

## 4.13 作用域规则

每个标识符都有一个作用域，决定了你在程序中可以在哪里使用它。对于程序的那部分，该标识符被认为“在作用域内”。

### 局部作用域

局部变量的标识符具有局部作用域。它仅从定义处到函数块结束时“在作用域内”。当函数返回到其调用者时，它“超出作用域”。因此，局部变量只能在定义它的函数内部使用。

### 全局作用域

在任何函数（或类）之外定义的标识符具有全局作用域——这些可能包括函数、变量和类。具有全局作用域的变量称为全局变量。具有全局作用域的标识符可以在定义后，在 .py 文件或交互会话中的任何位置使用。

### 从函数中访问全局变量

你可以在函数内部访问全局变量的值：

```
In [1]: x = 7

In [2]: def access_global():
    ...:     print('x printed from access_global:', x)
    ...:

In [3]: access_global()
x printed from access_global: 7
```

但是，默认情况下，你不能在函数中修改全局变量——当你首次在函数块中为变量赋值时，Python 会创建一个新的局部变量：

```
In [4]: def try_to_modify_global():
    ...:     x = 3.5
    ...:     print('x printed from try_to_modify_global:', x)
    ...:

In [5]: try_to_modify_global()
x printed from try_to_modify_global: 3.5
```

```
In [6]: x
Out[6]: 7
```

在函数 try_to_modify_global 的块中，局部 x **遮蔽**了全局 x，使其在函数块的作用域内不可访问。片段 [6] 显示，在函数 try_to_modify_global 执行后，全局变量 x 仍然存在并保持其原始值 (7)。

要在函数块中修改全局变量，必须使用 **global** 语句声明该变量在全局作用域中定义：

```
In [7]: def modify_global():
    ...:     global x
    ...:     x = 'hello'
    ...:     print('x printed from modify_global:', x)

In [8]: modify_global()
x printed from modify_global: hello

In [9]: x
Out[9]: 'hello'
```

### 块与套件

你现在已定义函数 *块* 和控制语句 *套件*。在块中创建变量时，该变量是该块 *局部* 的。但是，在控制语句的套件中创建变量时，变量的作用域取决于控制语句的定义位置：

- 如果控制语句位于全局作用域，则在控制语句中定义的任何变量都具有全局作用域。
- 如果控制语句位于函数块中，则在控制语句中定义的任何变量都具有局部作用域。

我们将在介绍自定义类时，在“面向对象编程”章节中继续讨论作用域。

### 函数遮蔽

在前几章中，对值求和时，我们将和存储在名为 total 的变量中。这样做的原因是 sum 是内置函数。如果你定义一个名为 sum 的变量，它将遮蔽内置函数，使其在你的代码中不可访问。当你执行以下赋值时，Python 将标识符 sum 绑定到包含 15 的 int 对象。此时，标识符 sum 不再引用内置函数。因此，当你尝试将 sum 用作函数时，会发生 TypeError：

```
In [10]: sum = 10 + 5

In [11]: sum
Out[11]: 15

In [12]: sum([10, 5])
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last
ipython-input-12-1237d97a65fb> in <module>()
----> 1 sum([10, 5])

TypeError: 'int' object is not callable
```

### 全局作用域中的语句

在迄今为止你看到的脚本中，我们在全局作用域中编写了一些函数外的语句，以及一些函数块内的语句。全局作用域中的脚本语句会在解释器遇到它们时立即执行，而块中的语句仅在调用函数时执行。

## 4.14 导入：深入探讨

你已使用类似以下的语句导入模块（例如 math 和 random）：

```
import module_name
```

然后通过每个模块的名称和一个点 (.) 访问其功能。此外，你已使用类似以下的语句从模块中导入特定标识符（例如 decimal 模块的 Decimal 类型）：

```
from module_name import identifier
```

