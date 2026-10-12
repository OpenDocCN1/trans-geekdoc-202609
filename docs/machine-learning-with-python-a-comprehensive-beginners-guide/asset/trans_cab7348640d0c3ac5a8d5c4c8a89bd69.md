
# 第 8 章 – Python 条件语句

在本章中，你将了解可用于在编码时进行修改的条件语句。由于它们的重要性无法从理论上看出，只能在使用中体会。条件语句是编程语言中的基础，它们用于根据条件判断为真或假来执行活动或计算。

## if-then-else 语句

关于 if-then-else 语句，解释或限制性语句是编程语言的基本特征，它们使程序对用户更有帮助。Python 中的 if else 语句具有以下基本结构：

```
If condition1:
    block1_statement
elif condition2:
    block2_statement
else:
    block3_statement
```

该结构将按如下方式评估/执行：

- 如果 `condition1` 为 True，Python 将执行 `block1_statement`。
- 如果 `condition1` 为 False，将评估 `condition2`。
- 如果 `condition2` 评估为 True，将执行 `block2_statement`。
- 如果 `condition2` 结果为 False，Python 将执行 `block3_statement`。

为了演示，这里有一个在函数 `the_hope` 内部构建的 if else 示例：

```
def the_hope(answer):
    if answer > 5:
        print("The best world.")
    elif answer <= 5 and answer > 1:
        print("This is Press club!")
    else:
        print("You are the best on earth.")

print(the_hope(6))
print(the_hope(3))
print(the_hope(1))
print(the_hope(0))
```

你将在 Python Shell 中得到如下输出：

```
The best world.
None
This is Press club!
None
You are the best on earth.
None
You are the best on earth.
None
```

请注意，条件语句可能分支出多个 `elif` 分支，但末尾只能有一个 `else` 分支。使用相似的代码块，可以插入另一个 `elif` 语句以容纳新闻俱乐部的特殊成员：两岁儿童。

```
def the_hope(answer):
    if answer > 5:
        print("The best world.")
    elif answer <= 5 and answer > 2:
        print("This is Press club!")
    elif answer == 2:
        print("This is Press club!")
    else:
        print("You are the best on earth.")

print(the_hope(6))
print(the_hope(3))
print(the_hope(1))
print(the_hope(0))
print(the_hope(2))
```

```
The best world.
None
This is Press club!
None
You are the best on earth.
None
You are the best on earth.
None
This is Press club!
None
```

## IF 语句

简单来说，Python if 语句选择要执行的活动。连同其外观搭档 `else`，它是 Python 中主要的选择工具，代表了 Python 程序逻辑的重要部分。这也是我们的第一个复合语句。像所有复合 Python 语句一样，if 声明可能包含其他语句，包括其他的不确定性（指嵌套 if）。事实上，Python 允许你在程序中连续连接声明（以便它们依次执行），并以主观嵌套设计（以便它们仅在特定条件下执行，例如选择和循环）。

### IF 语句的通用格式

Python if 声明是大多数过程式语言中 if 语言的典型代表。它表现为一个 if 测试，后跟至少一个可选的 `elif` ("else if") 测试和一个最终可选的 else 块。测试和 else 部分各自都有一个相关的嵌套声明块，缩进在标题行之下。每当 if 声明运行时，Python 执行与第一个评估为真的测试相关的代码块，如果所有测试都为假，则执行 else 块。if 解释的一般形式如下：

```
Conditionaltest1:          # if 测试
    statements1            # 关联块
elif test2:                # 可选的 elifs
    statements2
else:                      # 可选的 else
    statements3
```

### 基本示例

为了说明，我们应该看几个 if 声明工作的简单实例。除最初的 if 测试及其相关语句外，所有部分均为可选。因此，在最简单的情况下，其他部分被省略，请看：

```
>>> if 1:
...     print('true')
...
true
```

注意当你在基本交互界面中直观地编写时，提示符如何变为 `...` 以表示续行；在 IDLE 中，你只会简单地换行到缩进行（按退格键可回退）。一个空行（按两次 Enter 键可得）结束并运行整个声明。请记住 `1` 是布尔真值（稍后我们将看到，单词 `True` 是其等价物），所以该语句的测试持续成功。要处理假结果，编写 else 将是：

```
>>> if not 1:
...     print('true')
... else:
...     print('false')
...
false
```

### 多路分支

你必须理解一种将 if 和条件语句结合执行的方法。现在这里有一个更复杂的 if 声明示例，包含其所有可选部分：

```
>>> x = 'animal kingdom'
>>> if x == 'jack':
...     print("look very well")
... elif x == 'lion':
...     print("How are they?")
... else:
...     print('Run for your dear life!')
...
Run for your dear life!
```

这个多行声明从 if 行延伸到 else 下嵌套的块。当它运行时，Python 执行第一个为真的测试下嵌套的声明，如果所有测试都为假，则执行 else 部分（在本例中，它们都是假）。实际上，`elif` 和 `else` 部分都可以省略，并且每个部分中可以嵌套多条语句。请注意，单词 `if`、`elif` 和 `else` 通过垂直对齐、具有相同的缩进而相关联。如果你用过 C 或 Pascal 等语言，你可能有兴趣知道 Python 中没有 switch 或 case 语句根据变量的值选择活动。相反，你通常将多路分支编写为一系列 if/elif 测试，如前面的示例所示，有时通过字典或查找列表。由于字典和列表可以在运行时动态构建，它们有时比脚本中硬编码的 if 逻辑更灵活：

```
>>> decision = 'swing'
>>> print({'leave': 5.75,      # 基于字典的 'switch'
...        'swing': 2.00,      # 使用 has_key 或 get 获取默认值
...        'fish': 1.99,
...        'goat': 1.20}[choice])
2.00
```

尽管第一次看到这可能需要几分钟才能领会，但这个字典就是一个多路分支——根据键 `decision` 索引到一组值中的一个，很像 C 语言中的 switch。一个功能几乎相等但更冗长的 Python if 声明可能如下所示：

```
>>> if decision == 'leave':      # 等效的 if 声明
...     print(5.75)
... elif decision == 'swing':
...     print(2.00)
... elif decision == 'fish':
...     print(1.20)
... elif decision == 'goat':
...     print(3.00)
... else:
...     print('unpleasant decision')
...
1.99
```

尽管它可能更清晰，但这种 if 的潜在缺点是，除非将其作为字符串构建并使用像 `exec` 这样的工具运行，否则你无法像字典那样轻松地在运行时构建它。在日益独特的项目中，数据结构提供了额外的灵活性。

### 处理 Switch 默认值

为了处理 switch 默认值，请注意此处 if 上的 else 子句，用于在没有键匹配时处理默认情况。字典默认值可以在语句中编码，使用 get 方法调用，或使用引入的 try 语句捕获异常。所有类似的过程都可以用于在基于字典的多路分支中编码默认活动。作为对此用例的回顾，这里是 get 方案带默认值的工作示例：

```
>>> branch = {'leave': 5.75,
...           'swing': 1.99,
...           'eggs': 0.99}
>>> print(branch.get('leave', 'Unforeseen decision'))
5.75
>>> print(branch.get('goat', 'Unforeseen decision'))
Unforeseen decision
```

if 声明中的成员资格测试可以具有相同的默认效果：

```
>>> decision = 'goat'
>>> if decision in branch:
...     print(branch[decision])
... else:
...     print('Bad decision')
...
Unforeseen decision
```

此外，try 语句是通过捕获并处理它们原本会引发的异常来处理默认值的通用方法：

```
>>> try:
...     print(branch[decision])
... except KeyError:
...     print('Bad decision')
...
Bad decision
```

### 处理更大的活动

字典适合将值与键关联，但对于你可以在与 if 语句关联的声明块中编码的更复杂活动呢？你会发现字典也可以包含函数来表示更复杂的分支活动并执行通用跳转表。此类函数作为字典值出现，它们可以编码为函数名或内联 lambda，并通过添加括号来触发其活动。这里有一个独特的采样器，但请继续关注，等我们熟悉了函数定义之后：

```
def work():
    ...

def default():
    ...

branch = {
    'leave': lambda: ...,      # 可调用函数对象表
    'swing': work,
    'fish': lambda: ...
}
branch.get(choice, default)()
```

尽管基于字典的多路分支在处理动态数据的项目中很有用，但大多数软件工程师可能会发现编写 if 语句是执行多路分支最清晰的方法。作为编码中的一条经验法则，如果拿不准，就倾向于简单性和清晰度；这是“Python 风格”的方式。

哇！越来越有趣了，希望你跟着软件实践操作了；不要只读不练，自己执行代码。本章大致探讨了 Python 中的条件语句；它们通常用于标记代码。是时候磨练自己作为程序员的技能了。是的，你现在是一名程序员了。在自我提升方面，下一章有更多内容等着你。享受吧！
