
## 搜索与替换 (Searching and Replacing)

程序通常需要搜索并替换数据，正如搜索和替换功能在你的处理器中存在一样。
字符串可以通过 `find()` 和 `index()` 方法进行搜索。

`find()` 方法在未找到子字符串时返回 `-1`。
`index()` 方法在未找到时会返回错误。

## 搜索字符串的特定部分 (Searching a Specific Section of a String)

`find()` 和 `index()` 方法可以从字符串开始搜索子字符串。
你还可以定义起始和结束索引来只检查字符串的一部分。

## 如何反向搜索字符串 (How to Search Backwards Through a String)

`rfind()` 和 `rindex()` 方法的工作方式与 `find()` 和 `index()` 相同，区别是从字符串末尾反向搜索。

## 文本居中 (Centering Text)

`s.center(w, [pad])` 将文本在宽度为 `w` 的字段内居中。
可选的 `pad` 字符将位于字符串两侧。

## 第四章：条件执行 (Chapter 4: Conditional Execution)

生活中某些情况下，决定是不可避免的。这与编程没有区别。每个程序都是如此，必须评估相关问题。如果不在流中应用分支，就无法编程。

大多数编程语言中。它决定了给定的语句是否应该执行。当语句检查给定的条件且发现其为真时，就会执行内部呈现的代码集。
`if` 条件计算一个布尔表达式，并且仅当布尔表达式为 **TRUE（真）**时执行代码块。
根据语句的语法，条件将具体实现为一个布尔表达式（真或假）。如果条件为真，则执行 `if` 块内部的语句；当条件为假时，`if` 块中的程序将不会被执行。
以下是 `if` 语句的流程图：

![](img/43582740ac1227a817786ef73e0f3772_323_0.png)

如果你查看上面的流程图，第一个计数器将到达一个 `if` 条件并判断条件是否为真，如果是，则将执行语句；否则，将执行块内的代码。

## If-else 语句

该语句本身表示，如果发现给定的条件为真，则执行 `if` 块内部的语句；如果条件为假，则执行 `else` 块。
`else` 块只有在条件变为假时才会运行；这是你在条件不成立时执行某些操作的语句块。

`If-else` 语句计算布尔表达式，如果条件为真，则实现 `if` 块内部的代码块，并在条件变为假时执行 `else` 块中的代码块。

其语法是：

`If` (`布尔表达式`):
代码块
`else`:
代码块

在这种情况下，条件将执行执行为布尔表达式。如果发现条件为真，则将执行 `if` 块内部的语句；如果条件为假，则将执行程序内部的语句。

![](img/43582740ac1227a817786ef73e0f3772_324_0.png)

让我们探索上面的流程图。
如果你仔细观察，你会发现第一个计数器将到达 `if` 条件并检查 `if` 条件是否为真，如果为真，则将执行 `if` 块的语句；否则，将执行该块，随后将执行 `if-else` 块外部的剩余代码。

## 嵌套 if–else 语句

嵌套的 `if-else` 语句指的是位于另一个 `if` 或 `if-else` 块内部的 `if` 语句或 `if-else` 语句。Python 也提供了这种属性；这可以帮助我们在给定的程序中确认多个条件。位于另一个 `if` 语句内部的 `if` 语句内部的 `if` 语句依此类推。

### 嵌套 if 语法

语法如下：

```
If (condition):

# 如果条件为真则运行的语句

If (condition):

# 如果条件为真则执行的语句

# 嵌套结束
```

上面的语法清楚地显示了 `if` 块内部将包含另一个块，依此类推。`if` 块内部可以包含 `n` 个 `if` 块。考虑以下程序：

```
Number =10

if (number >0):

    print("this number is greater than 10")

if (number <10):

    print("This number is less than 10")
```

在上面的示例中，声明了一个变量 `number` 且值为 `10`。首先，它将确认第一个语句为真，然后执行第一个语句内部的代码块，接着它将判断第二个语句是否为真，依此类推。

## Elif 梯

你已经学习了 `elif` 语句，但还没有学过 `elif` 梯（`elif` ladder）。这个名称意味着程序有一个以梯子形式结构化的 `elif` 语句链。

```
if (condition):

    # 如果条件为真则执行的语句

elif (condition):

    # 当条件为假且 elif 条件为真时执行的语句

elif (condition):

    # 当 if 和第一个 elif 条件都为假且第二个 elif 条件为真时执行的语句集

elif (condition):

# 当 if、第一个 elif 和第二个 elif 条件都为假且第三个 elif 语句为真时执行的语句集

else:

    # 当所有 if 和 elif 条件都为假时执行的语句集
```
当当你想要测试多个表达式时，该语句非常方便。

### elif 梯的示例

`my_marks = 89`

```
if (my_marks < 35):

    print("Sorry!!! You are failed in the exam")
```

```
elif(my_marks < 60): print("Passed in Second class") 

elif(my_marks > 60 and my_marks < 85):

    print("Passed in First class")
```

```
else:

    print("Passed in First class with distinction")
```

此程序演示了 `elif` 梯。首先，控制进入 `if` 语句并判断条件是否为真，如果为真，则将执行 `if` 块内部的语句集；它将被跳过，计数器将来到第一个 `elif` 块并计算条件。

同样的过程将适用于所有剩余的 `elif` 语句，如果发现所有 `if` 和 `elif` 条件都为假，则将执行 `else` 块。

## 单行中的 if-else

在 Python 中，仍然可以在不担心缩进的情况下在一行中编写语句和 `elif` 语句。

### 单行中的 if 语句

我们知道可以如下所示编写语句：

`If` (`condition`):
# 如果条件为真则执行的语句集

在 Python 中，将上述代码块写在单行是可以的。例如：

`If` (`condition`): `语句1`; `语句2`; ...`语句n`
如果条件为真，则执行这些语句。

### 单行中的 elif 语句

可以在单行内编写 `elif` 语句如下：

`if(condition)`: # 当条件为真时执行的语句
`elif(condition1)`: # 当条件为假时执行的语句
`else`: # 当所有条件为假时执行的语句

然而，如果条件为假，则将执行这些语句。

### 单行中的 elif

这种块可以写成如下：

`if(condition)`: # 当条件为真时执行的语句
`elif(condition1)`: # 当条件为假时执行的语句
`else`: # 当所有条件为假时执行的语句

这种块也可以写成如下：

`if(condition)`: # 当条件为真时执行的语句
`elif(condition1)`: # 当条件为假时执行的语句
`else`: # 当所有条件为假时执行的语句

## 语句中的多个条件

你可以在 `if` 语句中简单地评估多个条件，如下：

```
num_1=10

num_2 = 20

num_3 =30

if (num_1==10 and num_2 == 20 and num_3==30):

    print("All conditions are true")
```
在这个示例中，`if` 语句使用了 `AND` 运算符，这意味着如果所有条件都为真，将执行内部的语句。

也可以指定 `OR` 运算符。例如：

```
namefruit = "Apple"

if (namefruit == "Mango" or namefruit == "Apple" or namefruit == "Grapes"):

    print("One of the conditions is true")
```
在这个示例中，三个条件中只有一个为真，这就是 `OR` 运算符的规则。如果任何一个条件为真，块内部的语句将被执行。

让我们探索一个真实的场景来确定月份的天数。你知道在闰年天数会改变。将通过 `if`、`elif` 和 `else` 语句以编程的方式看到这一点。

```
currentYear = int("Enter the year: ")

month = int("Enter the month: ")

if (currentYear % 4 == 0 and (currentYear % 100 != 0) or (currentYear % 400 == 0)):

    print("Leap Year")

    if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10 or month == 12):

        print("There are 31 days in this month")

    elif (month == 4 or month == 6 or month == 9 or month == 11):

        print("There are 30 days in this month")

    elif (month == 2):

        print("There are 29 days in this month")

    else:

        print("Invalid month")

elif ((currentYear % 4 != 0 and (currentYear % 100 != 0)) or (currentYear % 400 == 0)):

    if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10 or month == 12):

        print("There are 31 days in this month")

    elif (month == 4 or month == 6 or month == 9 or month == 11):

        print("There are 30 days in this month")

    elif (month == 2):

        print("There are 28 days in this month")

    else:

        print("Invalid month")

else:

    print("Invalid Year")
```

输出：

输入年份：2020
输入月份：4
该月有 30 天

输出：2

输入年份：2020
输入月份：1
该月有 31 天

输出：3

输入年份：2019
输入月份：2
该月有 28 天

输出：4

输入年份：2020
输入月份：2
该月有 29 天

## 布尔表达式

布尔表达式可能包含两个可能的取值之一：真（`true`）或假（`false`）。最简单的布尔表达式由 `False`（假）和 `True`（真）组成。比较数值表达式是否相等的表达式被称为布尔表达式。布尔表达式的最简单形式包含关系运算符，用于创建两个表达式之间的比较。

诸如 `< 10` 这样的表达式是合法的，但意义不大，因为它始终为真。这种表达式不太可能引起读者的困惑。它们在程序实现过程中持有的值将会发生变化。

## 迭代

在编程中，迭代意味着代码行的重复。它是计算机编程中的一项基本属性，有助于找到问题的解决方案。迭代和条件执行是算法开发的主要根源。

让我们从以下开始：

## While 语句

假设你想写一个可以数到 10,000 的程序。你会如何处理这个问题呢？你会坐下来写 10,000 条打印语句吗？虽然你可以这样做，但这将消耗你大量的时间。然而，计数在计算机中非常频繁，事实上，计算机可以计算非常大的数值。因此，一定有一种办法。你需要的是打印变量的值，并重复这一过程直到达到 10,000。重复执行代码的方法被称为循环。Python 语言有两个特殊的语句 `while` 和 `for` 用来处理迭代。

这是一个使用 `while` 语句的程序示例。

```python
num = 2

while num <= 5:

    print(num)

    num += 1
```

上述程序中的 `while` 语句会定期显示变量 `num`。程序随后执行此代码段 4 次。

在每次输出后，程序会将 `num` 加 1。执行四次代码后，条件将变为假，因此代码块不再执行。

`while num <= 5:` 这一行开启了 `while` 语句。`while` 关键字之后的下一个表达式是条件，用于评估是否应该执行代码块。只要条件的结果为真，程序将继续运行该代码块。但一旦条件求值为为假，循环就会终止。

此外，如果在开始时发现条件为假，程序将退出。

`while` 语句的标准语法包含：

```python
while condition:

    block
```

`while` 术指的是一个 Python 保留关键字，用于开启 `while` 语句。

条件指示体是否将被执行。条件后面跟着一个冒号（`:`）。

代码块由一个或多个语句组成，当条件为真时需要执行。所有完成代码块的语句必须比 `while` 语句的第一行多缩进一层。通常情况下，代码块是 `while` 语句的成员。

`while` 语句与 `if` 语句相似，因此初学者很容易混淆两者。有时，他们会在想用 `while` 语句时使用了 `if`。因此，新手程序员应该关注 `while` 语句和 `if` 语句的应用。

对于 `while` 语句，运行的程序在执行 `while` 块之前会实现条件，然后在 `while` 块之后验证条件。嗯，如果条件保持为真，程序将继续执行 `while` 块中的代码，直到达到条件为假的情况。在这一点上，循环停止执行。

## 确定循环和不确定循环

让我们探索以下代码段：

```python
n = 1

while n <= 10:

    print(n)

    n += 1
```

让我们找到上述程序段的迭代次数。如果你仔细评估这段代码，你会发现这里有 10 次迭代。因此，这个循环被称为确定循环，因为你可以准确地确定循环迭代的次数。

现在，考虑以下代码：

```python
c = 1

terminate = int(input())

print(n)

n += 1
```

对于这段代码，很难判断迭代次数。这个数字取决于用户的输入。然而，当用户输入内容并在下一次执行之前，你可以数出 `while` 循环将重复的次数……

通常，`while` 语句最适合不确定循环。

## for 语句

`while` 循环适用于不确定循环。最初，一个 `while` 循环用于执行确定循环，例如：

```python
n = 1

while n < 10:

    print(n)

    n += 1
```

在代码段中，`print` 语句只会执行 10 次。这段代码需要三个关键部分来控制循环。即初始化、检查和更新。

Python 有一种方便的方法来显示确定循环。该语句在系列值上重复。这里为了说明一个应用于元组（`tuple`）的序列。例如：

```python
for n in 1, 2, 3, 4, 5, 6, 7:

    print(n)
```

代码的运行方式与上一节中的 `while` 循环完全相同。在这个例子，`print` 语句执行了 7 次。代码将打印 1，然后是 2，依此类推。打印的最后一个值是 7。

`for` 语句与 `while` 语句的区别在于，它期望一组将要重复的特征。例如，你可能需要一个遍历不同数字的循环，例如从 1 到 10 的整数值。在 `while` 循环内部定义一个计数器来确保这种发生是可能的，但该语句的设计是为了轻松且高效地处理这类情况。以一个你好，世界程序为例。该程序将使用 `for` 循环打印 5 次字符串。为了实现这一点，你将学习 `range` 函数。

```python
for x in range(5):

    print("Hello, World!")
```

`range` 提供了一种高效访问不同数字的方法。当它与 `for` 语句结合时，它会计算出一个执行固定次数的循环。上述程序将打印 5 次 "Hello, World!"。它是通过在循环的每次迭代中为请求范围内的新变量 `x` 分配特定值来实现的。如果你能记住如何使用字符串字符位置计算以下索引，你就会记得这些索引从零开始。为了说明这一点，请查看代码：

```python
for x in range(5):

    print("The value of x is {0}".format(x))
```
