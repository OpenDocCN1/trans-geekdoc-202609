
为这些函数提供适当的名称和参数，让它们去担心如何完成工作。换句话说，推卸责任和拖延是美德！

- 你在设计的每个层级上继续推卸责任。为了完成每个函数，你会想到调用其他函数，并传入适当的 arguments。
- 当你调用内置函数时，责任似乎就到此为止了。
- 尽管偶尔会有一些重叠，自顶向下设计中的子任务通常彼此不同，因此需要不同的函数来执行它们。

递归设计与自顶向下设计共享一些这些特征，但在重要方面也存在差异，正如你在下一小节中将看到的那样。

## Recursive Function Design

在递归设计中，问题被分解为形式相同的子问题。在这些情况下，你将每个子问题分配给与在更高层级解决该问题的函数相同的函数。这类函数称为递归函数。

例如，考虑从下界到上界的整数序列求和的问题。函数 summation(1, 4) 应该返回 1 + 2 + 3 + 4 的结果，即 10。设计此问题的解决方案的一种方法是认识到这个加法序列包含以下嵌套求和：

```
summation(1, 4) = 1 + summation(2, 4)
summation(2, 4) = 2 + summation(3, 4)
summation(3, 4) = 3 + summation(4, 4)
summation(4, 4) = 4
```

请注意，最后一种情况 summation(4, 4) 并不是由另一个求和组成，而是简单地返回其参数之一。图 7.2 显示了 summation(1, 4) 的调用图。

![](img/4dc3f6307b32ff815a6d58ec1c84708c_165_0.png)

图 7.2
summation(1, 4) 的调用图。

请注意，`summation` 函数的每次调用（最后一调用除外）都会再次调用 `summation`。这种调用称为函数的 *递归调用*。

`summation` 函数的最后一次调用不会进行递归调用，而是直接返回其中一个参数。这称为函数的 *基本情况*。

在函数的每次递归调用中，第一个参数会增加 1。随着该值增加，它最终会达到一个限制，从而停止递归过程。换句话说，这种调整使函数能够检测何时应停止递归并返回基本情况值。

现在，你能根据其递归描述为 `summation` 函数推导出一个通用公式吗？当然可以。你假设 `summation` 函数有两个参数，名为 `low` 和 `high`。正如它们的名字所暗示的，你还假设只要函数被调用，`low` 就小于或等于 `high`。因此，`summation` 函数的递归公式由两个方程表示。第一个方程表示当两个参数相等时（图 7.2 中的最后一次调用）的求和。第二个方程表示其他情况下的求和。以下是这两个方程：

`summation(low, high) = high, if low == high`
`summation(low, high) = low + summation(low + 1, high)`

你应该在继续之前查看图 7.2，以验证这两个方程是否描述了 `summation(1, 4)` 中包含的部分求和。

你可以通过定义一个名为 `summation` 的 Python 函数将此设计转化为实现。该函数在 docstring 中说明了参数的假设，然后使用双向 `if` 语句来表达设计中陈述的两个选项。以下是该函数的代码，嵌入在一个简短的测试程序中：

```
"""
File: recursion1.py
Define and test a recursive summation function.
"""

import sys

def summation(low, high):
    """Returns the summation of the integers
    from low to high.
    Precondition: low <= high."""
    if low == high:
        return high
    else:
        return low + summation(low + 1, high)
```

```
def main(low = 1, high = 4):
    if len(sys.argv) == 3:
        low = int(sys.argv[1])
        high = int(sys.argv[2])
    print("The summation of", low, "and", high,
          "is", summation(low, high))
if __name__ == "__main__":
    main()
```

请注意，此处的 main 函数包含 1 和 4 的默认值，这些值在程序启动时传递给 summation 函数。然后，你可以通过在 shell 中使用其他参数调用 main 来测试该函数，如下一会话所示：

```
>>>
The summation of 1 and 4 is 10
>>> main(1, 10)
The summation of 1 and 10 is 55
>>> main(2, 10)
The summation of 2 and 10 is 54
>>>
```

由于程序还检查命令行参数，你也可以在终端窗口中测试程序：

```
Madison:~ ken$ python3 recursion1.py
The summation of 1 and 4 is 10
Madison:~ ken$ python3 recursion1.py 1 10
The summation of 1 and 10 is 55
```

## Recursive Function Call Tracing

为了更好地理解递归函数的工作原理，追踪其调用是有帮助的。你将对 summation 函数执行此操作。你添加一个用于缩进边距的参数和打印语句，以追踪每次调用的两个参数和返回的值。每次调用中的第一个语句计算缩进，然后在打印两个参数时使用它。计算出的值也在每次调用返回之前使用此缩进打印。以下是带有追踪的 summation 函数的代码：

```python
def summation(low, high, margin = 0):
    """Returns the summation of the integers
    from low to high. Prints a trace of low,
    high, and the value returned for each call,
using the given margin.
Precondition: low <= high."""
    blanks = " " * margin
    print(blanks, low, high)
    if low == high:
        print(blanks, high)
        return high
    else:
        result = low + summation(low + 1, high, margin + 4)
        print(blanks, result)
        return result
```

请注意，表达式 " " * margin 构建一个字符串，其中包含 margin 操作数指定的空白字符数。该值在函数被调用时初始为 0，并在每次递归调用时增加 4。因此，随着递归向下进行到基本情况，每对参数的缩进会进一步向右移动。当控制权返回到每个调用者时，margin 的先前值会被恢复，因此随着递归展开，返回值的缩进会进一步向左移动。以下是 summation(1, 4) 的示例追踪：

```
>>>
  1 4
    2 4
      3 4
        4 4
          4
        7
      9
10
The summation of 1 and 4 is 10
>>>
```

正如你从此追踪中看到的，第一个参数的值在每次递归调用中都会增加，直到它等于第二个参数的值。随着递归调用的返回，求和的值会增加。

## Recursive Functions and Loops

到目前为止，你可能已经猜到递归函数会重复给定的过程，直到条件变为 False。如果你认为这听起来像一个循环，你是对的。原则上，你可以将任何递归函数改写为循环，也可以将任何循环改写为递归函数。递归与迭代之间的选择部分取决于程序员的喜好，部分取决于性能要求。

本节中开发的递归求和函数在视觉上可能显得优雅而流畅，但在运行时每次调用都需要额外的计算机内存来支持参数和返回值的存储。因此，运行此函数所需的内存量会随着被求和的数字范围的大小呈线性增长。对于较小的范围，这不是一个重要问题，但对于较大的范围，基于循环的求和提供了更好的替代方案。

基于循环的 summation 函数版本使用带有 range 函数的 for 循环，并将每个值添加到正在进行的总数中。总和初始设置为 0，并在循环结束时返回。以下是代码：

```
def summation(low, high):
    """Returns the summation of the integers
    from low to high.
    Precondition: low <= high."""
    total = 0
    for number in range(low, high + 1):
        total += number
    return total
```

为什么此版本的运行时性能比递归版本更好？基于循环的函数只调用一次，为两个参数 low 和 high 以及临时变量 total 和 number 分配内存。在循环的每次遍历中，这些存储中的值会被重置，但永远不会添加或需要新的存储。

那么你可能会问，“如果基于循环的函数似乎比递归函数性能更好，为什么我还要费心使用递归呢？” 仍然更喜欢递归替代方案的情况有两种。

你可能更喜欢递归的第一个原因是它允许你编写一些在运行时不会导致内存使用增长的递归函数。这些函数称为尾递归函数。在尾递归函数中，递归调用之后不会执行任何操作。根据此定义，前面定义的递归 summation 函数不是尾递归的。每次 summation 的递归调用返回后，其总和会与 low 参数的先前值相加，如以下语句所示：

```
return low + summation(low + 1, high)
```

要将此类函数转换为尾递归函数，你需要想办法将总和作为额外参数传递给每次函数调用。然后，你可以在每次递归调用之前而不是之后在运行时增加总和。对于 summation 函数的情况，
