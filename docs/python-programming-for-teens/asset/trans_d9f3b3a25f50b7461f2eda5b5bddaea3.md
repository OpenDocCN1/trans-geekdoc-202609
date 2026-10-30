
表 3.2 逻辑合取和逻辑析取的真值表

| A | B | A 与 B | A 或 B |
|---|---|---|---|
| 真 | 真 | 真 | 真 |
| 真 | 假 | 假 | 真 |
| 假 | 真 | 假 | 真 |
| 假 | 假 | 假 | 假 |

你可能不会经常使用逻辑运算。但如果需要帮助，你可以随时查阅这些表格以了解其求值规则，然后在 shell 中尝试你的表达式。

## 选择：选择语句

在你确定如何询问关于某个条件的是/否问题后，你必须决定如何处理答案。有时如果答案是“是”就采取行动，如果是“否”则什么也不做。例如，如果整数除法的余数不为 0，你会输出余数；否则，之前已输出的商的输出就足够了。

其他时候，如果问题的答案是“是”就执行一个动作，如果答案是“否”就执行另一个动作。例如，如果密码被识别，你可以执行请求的服务；否则，你会向用户输出错误信息。

还有其他时候，可能有许多不同的选项可用，但只有一个是输入的。你必须将输入与每个可能的选项进行比较，直到找到匹配项，然后执行相关联的动作。命令菜单需要这种类型的多路决策。

在本节中，你将探索 Python 用于进行单向、双向和多向决策的不同类型的选择语句。

### 单向 if 语句

你使用单向 if 语句来进行单向决策。其形式为

```
if BooleanExpression:
    Statements
```

其中 Statements 是一个或多个语句的序列。注意嵌套语句前的缩进。与 for 循环一样，if 语句中的缩进是重要的。它挑选出在布尔表达式为 True 时运行的语句。如果布尔表达式为 False，则跳过这些语句，计算在整个 if 语句之后继续进行。图 3.2 显示了这种选择语句中的控制流。

![](img/4dc3f6307b32ff815a6d58ec1c84708c_92_0.png)

图 3.2

单向 if 语句中的控制流。

以下是前面提到的整数除法的示例：

```
>>> divisor = 10
>>> divisor = 3
>>> dividend = 10
>>> quotient = dividend // divisor
>>> remainder = dividend % divisor
>>> print("The quotient is", quotient)
The quotient is 3
>>> if remainder != 0:
    print("The remainder is", remainder)
```

余数是 1

正如你所见，如果除数是 2 或被除数是 9，余数 0 就根本不会被输出。

单向 if 语句很少见，但你应该尝试一个，以防某天你需要它。

### 双向 if 语句

双向决策，如路上的岔路，是常见的。你根据在选择点检查的条件选择其中一条路。用于做出这种选择的双向 if 语句的形式为

```
if BooleanExpression:
    ConsequentStatements
else:
    AlternativeStatements
```

再次，嵌套语句的缩进反映了这种控制结构的逻辑。如果布尔表达式为 True，则运行结果语句，然后跳到整个 if-else 语句的末尾。否则，跳过结果语句并运行 else 关键字之后的替代语句。图 3.3 显示了这种选择语句中的控制流。

![](img/4dc3f6307b32ff815a6d58ec1c84708c_93_0.png)

图 3.3
双向 if 语句中的控制流。

以下是如何使用 if-else 语句接受或拒绝用户输入数字的示例：

```
>>> import math
>>> number = input("Enter a positive number: ")
>>> if number > 0:
    print("The square root is", math.sqrt(number))
else:
    print("Error: the number must be greater than 0")
```

### 使用 random.randint 的概率选项

在第 1 章中，你看到了如何使用 Python 的 random.choice 函数与列表来模拟抛硬币：

```
>>> import random
>>> coin = ["heads", "tails"]
>>> random.choice(coin)
'tails'
```

因为有两个可供选择的选项，随机挑选一个会导致在多次抛掷过程中每个选项大约被选择 50% 的时间。为了演示这一点，你可以运行以下代码片段，它们在 50 次抛掷中统计正面和反面的数量：

```
>>> headCount = 0
>>> tailCount = 0
>>> for count in range(50):
    result = (random.choice(coin))
    if result == "heads":
        headCount += 1
    else:
        tailCount += 1

>>> headCount
22
>>> tailCount
28
```

正如你所见，从长远来看，抛硬币正面朝上的时间大约占一半，反面朝上的时间大约占一半。用数学术语来说，硬币的每一面出现的概率为 .5。按规则，如果一个事件的概率为 1，意味着它必然发生（100% 的时间）。较小的概率值对应较小的百分比。

偶尔，你会想基于给定的概率值选择一个选项。假设该选项的概率为 .25（4 分之 1）。而不是构建一个包含四个值的 Python 列表，你可以使用函数 random.randint 从整数范围内挑选一个随机整数。该函数期望两个参数：范围的下界和上界。因此，要选择概率为 .25 的选项，你可以调用 random.randint(1, 4)

并将结果与给定数字，例如 1 进行比较。从长远来看，你应该看到这个数字大约 25% 的时间被返回，如下一个 shell 会话所示：

```
>>> total = 0
>>> for count in range(50):
    result = random.randint(1, 4)
    if result == 1:
        total += 1

>>> total
13
>>> 4 * 13
52
```

这种方法对于 ½、¼ 等分数形式的概率效果很好，但对于具有较大分子数的分数，如 ¾ 呢？这意味着你正在寻找 4 个给定数字中的任意 3 个。用英语表达，你想查看 1 到 4 之间的随机数是否在 1 到 3 的范围内。以下是此测试的 Python 代码：

```
>>> random.randint(1, 4) in range(1, 4)
False
```

要验证此表达式四分之三的时间返回 True，像本节中所示的其他示例一样在循环中测试它。

使用这些技术，你应该能够以问题所需所需的任何给定概率在代码中执行操作。练习给你机会进行更多关于概率的实验。

### 多向 if 语句

当有超过两种可能的行动路径时，你必须做出多向决策。（毕竟，大多数传统的叉子有四个叉。）因此，在这种情况下必须检查至少两个条件。Python 为此目的提供了多向 if 语句。其形式为

```
if BooleanExpression:
    statements
elif BooleanExpression:
    statements
.
.
else:
    statements
```

在 if 子句中提出第一个问题后，你可以根据需要使用 as many elif 子句提出 as many 问题。尾部的 else 子句是可选的，处理所有问题的答案都为 False 或“否”的情况。请注意，只有一个语句序列被选中并运行。

以下代码片段演示了一个简单的算术命令解释器：

```
>>> x = float(input("Enter the first number: "))
Enter the first number: 3.44
>>> y = float(input("Enter the second number: "))
Enter the second number: 45.6
>>> command = input("Enter an arithmetic operator [+ , - , * , /]: ")
Enter an arithmetic operator [+ , - , * , /]: *
>>> if command == "+":
    print("The sum is", x + y)
elif command == "-":
    print("The difference is", x - y)
elif command == "*":
    print("The product is", x * y)
elif command == "/":
    print("The quotient is", x / y)
else:
    print("Error: unrecognized operator")
The product is 156.864
```

你将在本章后面看到选择语句在 turtle 绘图程序中的使用。

## 使用选择控制迭代

前面检查的 for 循环相当僵化。它迭代固定次数，遍历某个固定序列的值。这种类型的循环设计简单，对于许多问题效果很好。然而，一些情况需要更灵活的循环类型：一种无法预知将执行多少次迭代的循环。这种类型的循环必须能够提出问题：“我应该继续还是不继续？”并且在答案为“否”时能够退出。这种类型的循环称为不定循环，在本节中，你将探索如何为各种情况设计不定循环。
