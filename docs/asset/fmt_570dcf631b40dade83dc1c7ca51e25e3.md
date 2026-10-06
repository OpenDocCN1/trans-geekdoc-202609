
# Python 条件语句与循环控制

## if-elif-else 语句

```python
if (condition): # 条件为真时执行的语句集
elif (condition): # 当 if 为假且该 elif 为真时执行的语句集
elif (condition): # 当 if 和第一个 elif 为假且第二个 elif 为真时执行的语句集
else: # 当所有 if 和 elif 均为假时执行的语句集
```

### 示例 1：elif 梯

```python
my_marks = 89
if (my_marks < 35): print("Sorry!!! You failed in the exam")
elif(my_marks < 60): print("Passed in Second class")
elif(my_marks > 60 and my_marks < 85): print("Passed in First class")
else: print("Passed in First class with distinction")
```

输出：`Passed in First class with distinction`。

上面的示例描述了 `elif` 梯。控制器首先进入 `if` 语句并评估条件，如果条件为真，则执行 `if` 块内部的语句并跳过 `else` 块。剩余的 `elif` 语句继续类似的过程，如果所有 `if` 和 `elif` 条件均为假，则执行 `else` 块。

## 单行 If-else

在 Python 中，我们可以在一行内编写 `if` 语句、`if-else` 语句和 `elif` 语句，而无需担心缩进。

### 语法

```python
if (condition): # 条件为真时执行的语句
```

在 Python 中，允许将上述块写在一行，与上面的块类似。也可以包含多个语句，你只需要用分号（`;`）将它们分开。

### 语法

```python
if (condition): statement 1; statement 2; statement 3;…;statement n
```

如果条件为真，则执行 `statement 1`、`statement 2` 和 `statement n`。如果条件为假，则没有任何语句会被执行。

### 示例 1

```python
num = 7
if (num > 0): print("Number greater than Zero")
```

输出：`Number greater than Zero`。

### 示例 2

```python
if ('y' in 'python'): print('1'); print('2'); print('3')
```

输出：`1 2 3`

### 语法

```python
if (condition): # 条件为真时执行的语句
else: # 条件为假时执行的语句
```

在这里，条件将被评估为真或假。

## 嵌套 if

上面的语法表示 `if` 块将包含另一个 `if` 块。嵌套的 `if` 在 `if` 块内部，如果它为真，控制器进入嵌套的 `if` 块并执行语句，离开块并终止程序。

### 嵌套 if 示例 1

```python
num = 5
if(num > 0): print("number is positive")
if(num<10): print("number is less than 10")
```

输出：`number is positive number less than 10`。

在上面的示例中，我们声明了一个变量 `num` 值为 5。首先，它会检查第一个 `if` 语句，如果条件为真，则执行 `if` 条件内部的代码块；然后它会检查第二个 `if` 语句（如果第一个 `if` 语句为真），依此类推。

### 嵌套 if 示例 2

```python
num = 7
if (num != 0):
if (num > 0): print("Number greater than Zero")
```

输出：`Number greater than Zero`。

在上面的示例中，控制器检查给定数字是否为零，如果不是零，则进入第一个 `if` 块，然后在第二个 `if` 块中它会检查数字是否大于零，如果为真，控制器进入嵌套的 `if` 块并执行语句，离开块并终止程序。

### 嵌套 if 示例 3

```python
a = 7
b = 0
if (a < b): print("a smaller than b")
else: print("b smaller than a")
```

输出：`b smaller than a`。

在上面的代码中，`a` 小于 `b` 为假，因此执行 `else` 块，`if` 块中的语句被跳过。

## Python 一行编写 if 语句

### 语法

```python
if (condition):
    # 如果 condition 为真则执行的语句集合
elif (condition1):
    # 如果 condition1 为真则执行的语句集合
else:
    # 如果 condition 和 condition1 为假则执行的语句集合
```

上述 `elif` 块也可以写成如下形式。

```python
if (condition):
    # 如果 condition 为真则执行的语句集合
elif (condition1):
    # 如果 condition1 为真则执行的语句集合
else:
    # 如果 condition 和 condition1 为假则执行的语句集合
```

也可以包含多个语句，你只需要用分号（`;`）将它们分隔开。

```python
if (condition):
    statement 1; statement 2; statement 3;...;statement n
elif (condition):
    statement 1; statement 2; statement 3;...;statement n
else:
    statement 1; statement 2; statement 3;...;statement n
```

### 示例 1

```python
num = 7
if (num < 0):
    print("Number is smaller than Zero")
elif (num > 0):
    print("Number is greater than Zero")
else:
    print("Number is Zero")
```

**输出：** `Number is greater than Zero`

### 示例 2

```python
if ('a' in 'fruits'):
    print("Apple");
    print("Orange")
elif ('u' in 'fruits'):
    print("Mango");
    print("Grapes")
else:
    print("No fruits available")
```

**输出：**

Mango

Grapes

## if 语句中的多条件

并不是说在 `if` 语句内部只能写一个条件，我们也可以像下面这样在 `if` 语句中评估多个条件。

### 示例 1

```python
num1 = 10
num2 = 20
num3 = 30
if (num1 == 10 and num2 == 20 and num3 == 30):
    print("All the conditions are true")
```

**输出：** `All the conditions are true`

在这里，我们在 `if` 语句中使用 `AND` 运算符检查了多个条件，这意味着只有当所有条件都为真时，`if` 块中的语句才会被执行。我们也可以指定 `OR` 运算符。

### 示例

```python
fruitName = "Apple"
if (fruitName == "Mango" or fruitName == "Apple" or fruitName == "Grapes"):
    print("It’s a fruit")
```

**输出：** `It’s a fruit`

在这里，在 `if` 语句的三个条件中，只有一个条件为真，因为这是 `OR` 运算符的规则。只要任何一个条件为真，条件就会变为真，`if` 块内部的语句就会执行。

让我们考虑一个实际场景来查找某个月的天数，我们知道在闰年天数会发生。我们将使用 `if`、`elif` 和 `else` 语句以编程的方式来实现这一点。

### 示例

```python
currentYear = int(input("Enter the year: "))
month = int(input("Enter the month: "))
if ((currentYear % 4) == 0 and (currentYear % 100) != 0 or (currentYear % 400) == 0):
    print ("Leap Year")
if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10 or month == 12):
    print ("There are 31 days in this month")
elif (month == 4 or month == 6 or month == 9 or month == 11):
    print("There are 30 days in this month")
elif (month == 2):
    print("There are 29 days in this month")
else:
    print("Invalid month")
elif ((currentYear % 4) != 0 or (currentYear % 100) != 0 or (currentYear % 400) != 0):
    print ("Non Leap Year")
if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10 or month == 12):
    print ("There are 31 days in this month")
elif (month == 4 or month == 6 or month == 9 or month == 11):
    print("There are 30 days in this month")
elif (month == 2):
    print("There are 28 days in this month")
else:
    print("Invalid month")
```

**输出：**

Enter the year: 2020

Enter the month: 4

There are 30 days in this month

Enter the year: 2020

Enter the month: 1

There are 31 days in this month

Enter the year: 2019

Enter the month: 2

There are 28 days in this month

Enter the year: 2020

Enter the month: 2

Invalid month

## 总结

总结一下，我们学习了 Python 中的条件语句。这些是改变程序控制流的语句。我们有不同类型的条件语句，如 `if`、`if-else`、`elif`、嵌套 `if` 和嵌套 `if-else` 语句，它们控制着程序的执行。如果语句评估布尔表达式为真或假，如果条件为真，则执行 `if` 块中的语句；如果条件为假，则只有在你写了 `else` 块的情况下，才会执行 `else` 块中的语句。我们还有另一种名为 `elif` 的语句，其中 `else` 语句与 `if` 语句结合，其执行取决于之前的 `if` 或 `elif` 语句。

# 循环是如何运作的？

通常情况下，语句是按顺序执行的：函数中的第一个语句首先执行，然后是第二个语句，依此类推。在某些情况下，你可能需要多次执行一段代码块。编程语言提供了各种控制结构，允许更复杂的执行路径。循环语句允许我们多次执行一个语句或一组语句。为了处理代码中的细小部分，使用了循环。Python 编程语言提供了以下类型的循环来处理循环需求。Python 提供了三种执行循环的方式；这些 `for` 循环、`while` 循环和嵌套循环。虽然所有方式都提供相似的基本功能，但它们在语法和条件检查时间上有所不同。Python 语言提供了以下类型的循环来处理循环需求：

- `While loop`：当给定条件为真时，重复执行语句或一组语句。它在执行循环体之前会测试条件。
- `For 循环`：多次执行一个语句序列，并缩短管理循环变量的代码。
- `嵌套循环`：你可以在任何其他 `while`、`for` 或 `do..while` 循环内部使用一个或多个循环。

## 循环控制语句

循环控制语句会改变其正常执行顺序。当执行离开作用域时，在该作用域创建的所有自动对象都会被销毁。Python 支持以下控制语句。让我们简要介绍循环控制语句：

- `Break 语句`：终止循环语句，并将执行转移到循环之后的后续语句。
- `Continue 语句`：导致循环跳过其主体的剩余部分，并在再次迭代之前立即重新开始条件检查。
- `Pass 语句`：Python 中的 `pass` 语句用于语法上需要一个语句但你不想执行任何命令或代码的情况。

### Python break 语句

它终止当前循环并在下一个语句恢复执行，就像 C 语言中的 break 语句一样。`for` break 最常见的用法是当触发某些外部条件时快速退出循环。如果你正在使用嵌套循环，`break` 语句会在块之后终止内层循环。

**for break 的语法：**

```python
for letter in 'Python':
    if letter == 'h':
        break
    print('Current Letter :', letter)
var = 10
while var > 0:
    print('Current variable :', var)
    var = var - 1
    if var == 5:
        break
print("Good bye!") 
```

当执行上述代码时，会产生以下结果：

Current Letter : P

Current Letter : y

Current Letter : t

Current variable : 10

Current variable : 9

Current variable : 8

Current variable : 7

### Python continue 语句

它将控制权返回到 while 循环的开头。`continue` 语句跳过循环当前迭代的所有语句，并将控制移回循环。该语句同时用于 while 和 for 循环。

**continue 语法：**

```python
for letter in 'Python':
    if letter == 'h':
        continue
    print('Current Letter :', letter)
var = 10
while var > 0:
    print('Current variable :', var)
    var = var - 1
    if var == 5:
        continue
    print("Good bye!")
```

当执行上述代码时，会产生以下结果：

Current Letter : P

Current Letter : y

Current Letter : t

Current Letter : o

Current Letter : n

Current variable : 10

Current variable : 9

Current variable : 8

Current variable : 7

Current variable : 6

Current variable : 4

Current variable : 3

Current variable : 2

Current variable : 1

### Python pass 语句

它用于语法上需要一个语句但你不想执行任何命令或代码的情况。`pass` 语句是一个空操作；执行它时什么都不会发生。`pass` 也适用于你的代码最终将要去但尚未编写的地方（例如在存根方法中）。

**pass 语法：**

```python
for letter in 'Python':
    if letter == 'h':
        pass
    print('This is pass block')
    print('Current Letter :', letter)
print("Good bye!")
```

当执行上述代码时，会产生以下结果：

Current Letter : P

Current Letter : y

Current Letter : t

This is pass block

Current Letter : h

Current Letter : o

Current Letter : n

## 理解 For 循环

For 循环用于迭代序列。在 Python 中，`for` 循环用于列表、元组、字符串、字典或集合等可迭代对象。`for` 循环获取序列中的每个项目，并使用该项目执行代码块。

**for 循环的语法：**

```python
for item in sequence:
    # code to execute
```

# 在代码中编写异常
