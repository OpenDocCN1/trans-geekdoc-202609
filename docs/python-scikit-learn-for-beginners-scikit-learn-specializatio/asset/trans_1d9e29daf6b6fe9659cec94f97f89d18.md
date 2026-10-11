

# Python 运算符与控制流

## 算术运算符
算术运算符用于在 Python 中执行算术运算。下表总结了 Python 支持的算术运算符。假设 `X = 20`，`Y = 10`。

![Arithmetic Operators Table](Image00041.jpg)

以下是带有输出的算术运算符示例：

**脚本 3：**
![Script 3 Code](Image00042.jpg)

**输出：**
```
30
10
200
2.0
10240000000000
```

## 逻辑运算符
逻辑运算符用于在 Python 中执行逻辑与、或、非运算。下表总结了逻辑运算符。此处，`X` 为 `True`，`Y` 为 `False`。

![Logical Operators Table](Image00043.jpg)

以下示例解释了 Python 逻辑运算符的用法。

**脚本 4：**
![Script 4 Code](Image00044.jpg)

**输出：**
1. `False`
2. `True`
3. `True`

## 比较运算符
顾名思义，比较运算符用于比较两个或多个操作数。根据操作数之间的关系，比较运算符返回布尔值。下表总结了 Python 中的比较运算符。此处，`X` 为 `20`，`Y` 为 `35`。

![Comparison Operators Table](Image00045.jpg)

以下示例演示了比较运算符的实际应用：

**脚本 5**
![Script 5 Code](Image00046.jpg)

**输出：**
`False` `True` `False` `True` `False` `True`

## 赋值运算符
赋值运算符用于将值赋给变量。下表总结了赋值运算符。此处，`X` 为 `20`，`Y` 等于 `10`。

![Assignment Operators Table](Image00047.jpg)

请查看脚本 6 以了解 Python 赋值运算符的实际应用。

**脚本 6：**
![Script 6 Code](Image00048.jpg)

**输出：**
```
30
30
10
200
2.0
0
10240000000000
```

## 成员运算符
成员运算符用于判断某项是否为项目集合的成员。成员运算符有两种：`in` 运算符和 `not in` 运算符。以下脚本演示了 `in` 运算符的用法。

**脚本 7：**
![Script 7 Code](Image00049.jpg)

**输出：**
`True`

以下是 `not in` 运算符的示例。

**脚本 8：**
![Script 8 Code](Image00050.jpg)

**输出：**
`True`

## 条件语句
Python 中的条件语句用于实现条件逻辑。条件语句帮助你决定是否执行特定的代码块。Python 中主要有三种类型的条件语句：

1.  **If 语句**
2.  **If-else 语句**
3.  **If-elif 语句**

### If 语句
如果你只需检查单个条件，且不关心备选条件，可以使用 `if` 语句。例如，如果你想检查 `10` 是否大于 `5`，并据此打印一条语句，可以使用 `if` 语句。`if` 语句求值的条件返回布尔值。如果 `if` 语句求值的条件为真，则执行 `if` 语句后面的代码块。值得注意的是，在 Python 中，新代码块从新行开始，并相对于外层块缩进（通常为一个制表符或四个空格）。在下面的示例中，条件 `10 > 5` 求值为真。因此，`if` 语句后面的代码块执行，并在控制台打印一条消息。

**脚本 9：**
![Script 9 Code](Image00051.jpg)

**输出：**
`Ten is greater than 5`

### If-Else 语句
当你想在 `if` 语句的条件返回假时执行备选代码时，`if-else` 语句非常有用。例如，在下面的示例中，条件 `5 > 10` 将返回假。因此，`else` 语句后面的代码块将执行。

**脚本 10：**
![Script 10 Code](Image00052.jpg)

**输出：**
`10 is greater than 5`

### If-Elif 语句
当你需要求值多个条件时，`if-elif` 语句非常方便。例如，在下面的示例中，我们首先检查 `5 > 10`，其求值为假。接下来，`elif` 语句求值条件 `8 < 4`，这也返回假。因此，最后一个 `else` 语句后面的代码块执行。

**脚本 11：**
![Script 11 Code](Image00053.jpg)

**输出：**
`5 is not greater than 10 and 8 is not smaller than 4`

## 迭代语句
迭代语句（也称为循环）用于迭代执行特定代码片段。Python 中主要有两种类型的迭代语句：

1.  **For 循环**
2.  **While 循环**

