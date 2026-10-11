

# Python 程序设计基础

## 使用 if..else 进行流程控制

编写一个程序，使用 `if..else` 流程控制语句检查非闰年并显示相应场景。包含注释和缩进以增强程序的可读性。

## Python 中的 for 循环

在 Python 中，缩进用于分隔 `for` 循环的主体。

**注意**：简单线性列表采用以下语法：

```python
Variable_name = [values separated by a comma]
```

### 示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
numbers = [12, 3, 18, 10, 7, 2, 3, 6, 1]  # 存储列表的变量名
sum = 0                                      # 使用前初始化 sum，非常重要
for cumulative in numbers:                   # 遍历列表
    sum = sum + cumulative
print("The sum is", sum)
```

### 练习

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

编写一个 Python 程序，使用 `for` 循环对以下列表求和。

a. `marks = [3, 8, 19, 6, 18, 29, 15]`
b. `ages = [12, 17, 14, 18, 11, 10, 16]`
c. `mileage = [15, 67, 89, 123, 76, 83]`
d. `cups = [7, 10, 3, 5, 8, 16, 13]`

## Python 中的 range() 函数

Python 中的 `range()` 函数可用于生成数字。请记住，在编程中第一个项目的索引是 0。

因此，`range(11)` 将生成从 0 到 10 的数字。

### 示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
print(range(7))
```

输出将是 `0, 1, 2, 3, 4, 5, 6`。

### 练习

不编写和运行 Python 程序，以下表达式的输出是什么？

a. `range(16)`
b. `range(8)`
c. `range(4)`

## 使用 range()、len() 和索引

### 解决示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
# 假设此处为图片所示代码逻辑
# 图片路径: Images/image00234.gif
```

该程序的输出将是：

```text
I prefer omelet
I prefer fish
I prefer jazz
```

### 练习

编写一个 Python 程序，遍历以下列表并包含消息 "I listen to"（每种音乐流派）。使用 `for` 循环、`len()` 和 `range()`。参考前面的示例语法。

```python
folders = ['Rumba', 'House', 'Rock']
```

## 使用带 else 子句的 for 循环

可以选择性地在 `for` 循环后包含 `else` 子句。当序列中的项目耗尽时，将执行 `else` 块。

### 示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
marks = [12, 15, 17]
for i in marks:
    print(i)
else:
    print("No items left")
```

### 挑战

编写一个 Python 程序，打印 1 到 50 之间的所有素数。

## Python 中的 while 循环

在 Python 中，`while` 循环用于在测试条件保持 `True` 时迭代执行一块程序代码。`while` 循环用于用户不知道所需循环周期的场景。

如前所述，`while` 循环主体通过缩进来确定。

### 示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
# 假设此处为图片所示代码逻辑
# 图片路径: Images/image00235.gif
```

**警示**：未包含计数器的值将导致无限循环。

### 练习

a. 编写一个 Python 程序，利用 `while` 流程控制语句显示 1 到 10 之间所有奇数的和。
b. 编写一个 Python 程序，采用 `while` 流程控制语句显示 11 到 21 之间所有数字的和。
c. 编写一个 Python 程序，结合 `while` 流程控制语句显示 1 到 10 之间所有偶数的和。

## 使用带 else 子句的 while 循环

如果条件为假且未发生 `break`，则运行 `while` 循环的 `else` 部分。

### 示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
track = 0
while track < 4:
    print("Within the loop")
    track = track + 1
else:
    print("Now within the else segment")
```

## Python 的 break 和 continue 语句

让我们用一个现实生活中的类比，即我们必须在迭代完全求值之前强制停止。想想使用简单字典攻击破解/破译密码时，会循环遍历所有可能的字符组合，一旦找到搜索的密码，你会希望程序立即停止，而不必完成剩余过程。再想想使用恢复软件恢复意外删除的照片时，一旦在指定范围内找到项目，你会希望恢复立即停止遍历文件。Python 中的 `break` 和 `continue` 语句以类似的方式工作。

### 示例：break 语句

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
for tracker in "bring":
    if tracker == "i":
        break
    print(tracker)
print("The End")
```

## Python 中的 continue 语句

当使用 `continue` 语句时，解释器仅跳过当前迭代中循环内的其余代码，循环不会终止。循环继续进行下一次迭代。

### Python continue 的语法

```python
continue
```

### 示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
for tracker in "bring":
    if tracker == "i":
        continue
    print(tracker)
print("Finished")
```

该程序的输出将是：

```text
b
r
n
g
Finished
```

**类比**：假设你正在运行数据恢复软件并指定了跳过 Word 文件（`.doc`、`.docx` 扩展名）。程序将不得不在跳过 Word 文件后继续迭代。

### 练习

a. 编写一个使用 `for` 循环的 Python 程序，在字符串 "Oliver" 中遇到 "v" 时中断。
b. 编写一个 Python 程序，在字符串 "Lemon" 中跳过 "m" 后继续。

## Python 中的 pass 语句

像注释一样，`pass` 语句不会影响程序，因为它不执行任何操作。

### pass 的语法

```python
pass
```

设想一段你计划将来使用但目前不需要的程序代码。你可以将其编写为 `pass` 语句，而不必在将来插入该代码。

### 示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
my_list = {'k', 'i', 'n'}
for tracker in my_list:
    pass
```

## Python 中的函数

Python 中的函数有助于将大型代码拆分为较小的单元。函数使程序更有条理且易于管理。

Python 函数将采用以下语法形式：

```python
def name_of_function(arguments):
    """docstring"""
    statement(s)
```

### 示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
def welcome(salute):
    """The Python function welcomes you to
    the individual passed in as
    parameter"""
    print("Welcome " + salute + ". Lovely Day!")
```

## 在 Python 中调用函数

一旦定义了函数，我们就可以从另一个函数或程序中调用它。

调用函数只需键入函数名并附上合适的参数。

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
welcome('Brenda')
```

输出将是 `"Welcome Brenda. Lovely Day!"`。

### 练习

编写一个函数，调用时输出 `"Hello (student name), kindly submit your work by Sunday"`。

## 文档字符串

文档字符串放在函数头之后作为第一条语句，简要解释函数的功能。文档字符串应始终放在三引号之间以容纳多行字符串。

### 调用/引用之前输入的文档字符串

#### 示例

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
print(welcome.__doc__)
```

输出将是：

```text
This function welcomes you to
the individual passed in as
parameter
```

调用/引用文档字符串的语法是：

```python
print(function_name.__doc__)
```

## Python 函数返回语句

### 返回语法

```python
return [list of expressions]
```

### 说明

`return` 语句可以返回一个值或 `None` 对象。

### 示例：返回 None

```python
print(welcome("Richard"))  # 传递参数并调用函数
# Welcome Richard. Lovely Day!
# None                     # 返回的值
```

### 示例：返回非 None 值

1. 启动 IDLE。
2. 导航到 **File** 菜单并点击 **New Window**。
3. 输入以下代码：

```python
# 假设此处为图片所示代码逻辑
# 图片路径: Images/image00236.gif
```

