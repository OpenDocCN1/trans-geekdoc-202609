

print(f"You have written the number {number}")

## 分支: if ... else ...

if ... else ... 控制结构允许程序在满足条件时执行一组指令，在条件不满足时执行另一组指令。“If”表示“是”（条件满足），“else”表示“否”。Python 中的语法如下：

if ... else ... 结构的语法如下：

```
if condition:
    here are the orders that are executed if the condition is true
    and that can occupy several lines
else:
    and here are the orders that are executed if the condition is
    false and that can also occupy several lines
```

该结构的执行过程如下：

- 条件始终会被求值。
- 如果结果为 True，仅执行语句块 1
- 如果结果为 False，仅执行语句块 2。

第一行包含要求值的条件。该行必须始终以冒号 (:) 结尾。

接下来是当条件满足（即条件为真时）执行的指令块。需要注意的是，该块必须缩进，因为 Python 使用缩进来识别构成指令块的行。Python 中通常使用的缩进是四个空格，但也可以使用更多或更少的空格。当你在行尾写上两个点 (:) 时，IDLE 会自动缩进随后的行。要结束一个块，只需将光标移回行首。

接下来是包含 else 命令的行，它告诉 Python 当条件不满足（即为假时）必须执行接下来的块。该行也必须始终以冒号 (:) 结尾。包含 else 命令的行不能包含 else 和冒号以外的任何内容。

最后是与 else 对应的缩进指令块。

## if ... else ... 条件语句的流程图

以下流程图展示了 if ... else ... 语句的执行过程：

开始

条件

假

真

块 2

块 1

结束

## 带有 if ... else ... 条件语句的示例程序

让我们看一个示例。以下程序会询问用户年龄，并将答案存储在“age”变量中。然后检查年龄是否小于 18 岁。如果此比较为真，程序会输出是未成年人，如果为假则输出是法定成年人。最后，程序总是说再见，因为最后一条指令不在任何块中，因此始终会被执行。以下可以看到该程序的两个逐步执行示例：

### "if" ... "else" ... 示例 1

```
age = int(input("How old are you? "))
if age < 18:
    print("Are you a minor")
else:
    print("Are you of legal age")
print("Goodbye!")
```

### "if" ... "else" ... 示例 2

```
age = int(input("How old are you? "))
if age < 18:
    print("Are you minor")
else:
    print("Are you of legal age")
print("Goodbye!")
```

虽然不建议这样做，但你可以使用两个 "if" 块来代替一个 "if ... else" 块编写程序...

```
age = int(input("How old are you? "))
if age < 18:
    print("Are you minor")
if age >= 18:
    print("Are you of legal age")
print("Goodbye!")
```

出于两个原因，最好不要这样做：

使用两个 "if" 块会强制 Python 始终求值两个条件，而在 "if ... else" 块中只会求值一个条件。在简单程序中，差别不明显，但在执行大量比较的程序中，影响可能会明显。

使用 else 可以省去编写一个条件（此外，编写条件时可能会出错，但编写 else 不会）。

如果出于任何原因你不想在任何块中执行任何指令，则该指令块至少应包含 pass 语句（该语句告诉 Python 不需要执行任何操作）。

```
age = int(input("How old are you? "))
if age < 120:
    pass
else:
    print("I don't believe it!")
print(f"You say that you have {age} years.")
```

显然，通过更改不等式可以简化此程序。这只是一个示例，用于展示 pass 语句的用法。

```
age = int(input("How old are you? "))
if age >= 120:
    print("I don't believe it!")
print(f"You say that you have {age} years.")
```

## 不止两个替代方案: if ... elif ... else ...

if ... else ... 结构可以通过添加 elif 指令来扩展：

elif 是 else if 的缩写。Python 中的语法如下：

### if ... elif ... else ... 条件语句语法

if ... elif ... else ... 结构的语法如下：

```
if condition_1:
    block 1
elif condition_2:
    block 2
else:
    block 3
```

- 如果满足条件 1，执行块 1
- 如果条件 1 不满足但条件 2 满足，执行块 2
- 如果条件 1 和条件 2 都不满足，执行块 3。

该结构等效于以下嵌套的 if ... else ... 结构：

```
if condition_1:
    block 1
else:
    if condition_2:
        block 2
    else:
        block 3
```

你可以编写任意数量的 elif 块。else 块（可选）在没有满足上述任何条件时执行。

![](img/6308792a7b2c124d01547ee394b31561_73_0.png)

### if ... elif ... else ... 条件语句的流程图

在 if ... elif ... else ... 结构中，编写情况的顺序很重要，通常可以通过合理排序情况来简化条件。

我们可以区分两种情况：

### 1- 当情况互斥时

考虑一个询问年龄并根据接收到的值输出不同消息的程序。例如，我们可以区分三种情况：

- 如果值为负数，则是错误
- 如果值在 0 到 17 之间，则是未成年人
- 如果值大于或等于 18，则是法定成年人

情况是互斥的，因为一个值只能属于其中一种情况。

可能的程序如下：

```python
age = int(input("How old are you? "))
if age >= 18:
    print("Are you of legal age")
elif age < 0:
    print("You cannot have a negative age")
else:
    print("You are a minor")
```

之前的程序可以正常工作，但情况比较杂乱。最好按顺序编写，以确保不会遗漏任何可能的情况。例如，我们可以从未成年人到老年人编写，尽管这迫使我们编写其他条件：

```python
age = int(input("How old are you? "))
if age < 0:
    print("You cannot have a negative age")
elif age >= 0 and age < 18:
    print("Are you a minor")
else:
    print("Are you legal age")
```

在之前的程序中，比较可以简化：

```python
age = int(input("How old are you? "))
if age < 0:
    print("You cannot have a negative age")
elif age < 18:
    print("Are you a minor")
else:
    print("Are you of legal age")
```

这两个程序是等价的，因为在 "if ... elif ... else" 结构中，当某个 Python 比较满足后，就不再求值后续条件。在此例中，如果程序需要检查第二个比较（elif 中的），那是因为第一个（if 中的）未满足。如果第一个未满足，说明 age 大于 0，因此在第二个条件中无需再次检查。

但需要小心，因为如果按相反顺序排列之前程序的情况并保持条件不变，程序将无法按预期工作，因为输入负值将显示消息 "Are you a minor"。

```
# This program does not work properly
age = int(input("How old are you?"))
if age < 18:
    print("Are you a minor")
elif age < 0:
    print("You cannot have a negative age")
else:
    print("Are you of legal age")
```

