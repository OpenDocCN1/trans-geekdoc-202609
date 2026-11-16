
要了解 IPython 的功能，在任何 In [] 提示符处输入 ?，按 Enter，然后阅读帮助文档概览。

## 4.3 带多个参数的函数

让我们定义一个最大值函数，用于确定并返回三个值中最大的值——下面的会话分别使用整数、浮点数和字符串三次调用该函数。

点击此处查看代码图片

```
In [1]: def maximum(value1, value2, value3):
    ...:     """Return the maximum of three values."""
    ...:     max_value = value1
    ...:     if value2 > max_value:
    ...:         max_value = value2
    ...:     if value3 > max_value:
    ...:         max_value = value3
    ...:     return max_value
    ...: 
In [2]: maximum(12, 27, 36)
Out[2]: 36
In [3]: maximum(12.3, 45.6, 9.7)
Out[3]: 45.6
In [4]: maximum('yellow', 'red', 'orange')
Out[4]: 'yellow'
```

我们没有在 if 语句上下放置空行，因为在交互模式下在空行按 Return 会完成函数的定义。

你也可以使用混合类型调用 maximum，例如 int 和 float：

```
In [5]: maximum(13.5, -3, 7)
Out[5]: 13.5
```

调用 maximum(13.5, 'hello', 7) 会导致 TypeError，因为字符串和数字不能使用大于运算符 (>) 相互比较。

### 函数 maximum 的定义

函数 maximum 在逗号分隔的列表中指定三个参数。片段 [2] 的参数 12、27 和 36 分别赋给参数 value1、value2 和 value3。

要确定最大值，我们一次处理一个值：

- 首先，我们假设 value1 包含最大值，因此将其赋给局部变量 max_value。当然，value2 或 value3 可能包含实际的最大值，因此我们仍必须将它们各自与 max_value 比较。

- 第一个 if 语句随后测试 value2 > max_value，如果该条件为 True，则将 value2 赋给 max_value。

- 第二个 if 语句随后测试 value3 > max_value，如果该条件为 True，则将 value3 赋给 max_value。

现在，max_value 包含最大值，因此我们返回它。当控制权返回给调用者时，函数块中的参数 value1、value2 和 value3 以及变量 max_value——它们都是局部变量——不再存在。

### Python 的内置 max 和 min 函数

对于许多常见任务，你需要的功能在 Python 中已存在。例如，内置的 max 和 min 函数知道如何分别确定其两个或多个参数中的最大值和最小值：

```
In [6]: max('yellow', 'red', 'orange', 'blue', 'green')
Out[6]: 'yellow'

In [7]: min(15, 9, 27, 14)
Out[7]: 9
```

这些函数中的每一个也可以接收可迭代参数，例如列表或字符串。使用内置函数或 Python 标准库模块中的函数，而不是编写自己的函数，可以缩短开发时间并提高程序的可靠性、可移植性和性能。有关 Python 内置函数和模块的列表，请参阅

https://docs.python.org/3/library/index.html

## 4.4 随机数生成

我们现在暂时转向一种流行的编程应用类型——模拟和游戏。你可以通过 Python 标准库的 **random 模块** 引入 **偶然性**。

### 掷六面骰子

让我们生成 1 到 6 范围内的 10 个随机整数，以模拟掷六面骰子：

点击此处查看代码图片

```
In [1]: import random

In [2]: for roll in range(10):
    ...:     print(random.randrange(1, 7), end=' ')

    ...:
4 2 5 5 4 6 4 6 1 5
```

首先，我们导入 `random` 以便使用该模块的功能。**randrange** 函数从第一个参数值生成一个整数，一直到但 _不_ 包含第二个参数值。让我们使用上方向键调用 `for` 语句，然后按 _Enter_ 重新执行它。请注意，显示 _不同_ 的值：

点击此处查看代码图片

```
In [3]: for roll in range(10):
    ...:     print(random.randrange(1, 7), end=' ')

    ...:
4 5 4 5 1 4 1 4 6 5
```

有时，你可能希望保证随机序列的 **可重复性**——例如，用于调试。在本节末尾，我们将使用 `random` 模块的 `seed` 函数来实现这一点。

### 掷六面骰子 6,000,000 次

如果 `randrange` 真正随机生成整数，那么其范围内的每个数字每次调用时都有相等的 **概率**（或 _机会_ 或 _可能性_）被返回。为了展示骰子面 1–6 出现的可能性相等，以下脚本模拟了 6,000,000 次骰子滚动。运行脚本时，每个骰子面应出现约 1,000,000 次，如示例输出所示。

点击此处查看代码图片

```
# fig04_01.py
"""Roll a six-sided die 6,000,000 times."""
import random

# face frequency counters
frequency1 = 0
frequency2 = 0
frequency3 = 0
frequency4 = 0
frequency5 = 0
frequency6 = 0

# 6,000,000 die rolls
for roll in range(6_000_000): # note underscore  separators
    face = random.randrange(1, 7)

    # increment appropriate face counter
    if face == 1:
        frequency1 += 1
    elif face == 2:
        frequency2 += 1
    elif face == 3:
        frequency3 += 1
    elif face == 4:
        frequency4 += 1
    elif face == 5:
        frequency5 += 1
    elif face == 6:
        frequency6 += 1

print(f'Face{"Frequency":>13}')
print(f'{1:>4}{frequency1:>13}')
print(f'{2:>4}{frequency2:>13}')
print(f'{3:>4}{frequency3:>13}')
print(f'{4:>4}{frequency4:>13}')
print(f'{5:>4}{frequency5:>13}')
print(f'{6:>4}{frequency6:>13}')
```

点击此处查看代码图片

| 面值   |   频数 |
|:-------|------------:|
| 1      |      998686 |
| 2      |     1001481 |
| 3      |      999900 |
| 4      |     1000453 |
| 5      |      999953 |
| 6      |      999527 |

该脚本使用 *嵌套* 控制语句（在 `for` 语句中嵌套的 `if elif` 语句）来确定每个骰子面出现的次数。`for` 语句迭代 6,000,000 次。我们使用了 Python 的下划线 (_) 数字分隔符，使值 6000000 更易读。表达式 `range (6, 000, 000)` 是不正确的。逗号分隔函数调用中的参数，因此 Python 会将 `range (6, 000, 000)` 视为带有 *三个* 参数 6、0 和 0 的 `range` 调用。

对于每次骰子滚动，脚本向适当的计数器变量加 1。运行程序并观察结果。该程序可能需要几秒钟才能完成执行。如你所见，每次执行都会产生 *不同* 的结果。请注意，我们没有在 `if elif` 语句中提供 `else` 子句。

### 为随机数生成器设置种子以实现可重复性

函数 `randrange` 实际上生成 *伪随机数*，其基于从名为 **种子** 的数值开始的内部计算。反复调用 `randrange` 会产生一系列 *看起来* 随机的数字，因为每次启动新的交互会话或执行使用 `random` 模块函数的脚本时，Python 在内部都会使用 *不同* 的种子值。1 在调试使用随机生成数据的程序中的逻辑错误时，在使用其他值测试程序之前，使用 *相同* 的随机数序列直到消除逻辑错误会很有帮助。为此，你可以使用 random 模块的 **seed** 函数自己 **播种随机数生成器**——这会强制 `randrange` 从你指定的种子开始计算其伪随机数序列。在以下会话中，片段 [5] 和 [8] 产生相同的结果，因为片段 [4] 和 [7] 使用相同的种子（32）：

1 根据文档，Python 根据系统时钟或依赖于操作系统的随机源来设置种子值。对于需要安全随机数的应用程序（例如密码学），文档建议使用 `secrets` 模块，而不是 `random` 模块。

点击此处查看代码图片

```
In [4]: random.seed(32)

In [5]: for roll in range(10):
   ...:     print(random.randrange(1, 7), end=' ')

...:
1 2 3 6 2 4 1 6 1
In [6]: for roll in range(10):
   ...:     print(random.randrange(1, 7), end=' ')
```
