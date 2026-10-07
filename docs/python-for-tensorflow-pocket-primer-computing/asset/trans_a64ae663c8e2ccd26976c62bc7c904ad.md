
用户输入可能会导致异常（取决于你的代码执行的操作），因此，包含异常处理代码是非常重要的。

列表 1.12 显示了 `UserInput.py` 的内容，该程序提示用户输入字符串，并尝试在 `try/except` 块中将该字符串转换为数字。

# 列表 1.12 UserInput.py

```
userInput = raw_input("Enter something: ")

try:
    x = 0 + eval(userInput)
    print 'you entered the number:',userInput
except:
    print userInput, 'is a string'
```

列表 1.12 在将用户输入转换为数字的结果加上了数字 0。如果转换成功，将显示包含用户输入内容的消息。如果转换失败，`except` 代码块将包含一个显示消息的 `print` 语句。

> 注意此代码示例使用了 `eval()` 函数，应该避免使用它，以防你的代码执行任意的（且可能具有破坏性的）命令。

列表 1.13 显示了 `UserInput3.py` 的内容，该程序提示用户输入两个数字，并尝试在一对 `try/except` 块中计算它们的和。

# 列表 1.13 UserInput3.py

```
sum = 0

msg = 'Enter a number:'

val1 = raw_input(msg)

try:
    sum = sum + eval(val1)
except:
    print val1,'is a string'

msg = 'Enter a number:'
val2 = raw_input(msg)

try:
    sum = sum + eval(val2)
except:
    print val2,val1,'and',val2,'is',sum

print 'The sum of',val1,'and',val2,'is',sum
```

列表 1.13 包含两个 `try` 块，每个块后面都跟着一个 `except` 语句。第一个 `try` 块尝试将用户提供的数字加上变量 `sum`，第二个 `try` 块尝试将第二个用户提供的数字加上之前输入的数字上。如果任何一个输入字符串不是有效数字，就会发生错误消息；如果两个都是有效数字，将显示一个包含输入数字及其和的消息。请务必阅读本章前面提到的关于 `eval()` 函数的警告。

# 命令行参数

Python 提供了一个 `getopt` 模块来解析命令行选项和参数，而 Python 的 `sys` 模块通过 `sys.argv` 访问任何命令行参数。这有两个作用：

-   `sys.argv` 是命令行参数的列表
-   `len(sys.argv)` 是命令行参数的数量

这里 `sys.argv[0]` 是程序名，所以如果 Python 程序被调用为 `test.py`，它就匹配 `sys.argv[0]` 的值。

现在，你可以在命令行上为 Python 程序提供输入值，而不是通过提示用户来提供输入值。

例如，考虑这里所示 `test.py` 脚本：

```python
#!/usr/bin/python
import sys
print 'Number of arguments:',len(sys.argv),'arguments'
print 'Argument List:', str(sys.argv)
```

现在按照以下方式运行上述脚本：

```
python test.py arg1 arg2 arg3
```

这将产生以下结果：

Number of arguments: 4 arguments.
Argument List: ['test.py', 'arg1', 'arg2', 'arg3']

```

从命令行指定输入值的能力提供了非常有用的功能。例如，假设你有一个自定义的 Python 类，它包含 `add` 和 `subtract` 方法，用于加和减一对数字。

你可以使用命令行参数来指定对一对数字执行哪种方法，如下所示：

```
python MyClass add 3 5
python MyClass subtract 3 5
```

此功能非常有用，因为你可以程序化地执行 Python 类中的不同方法，这意味着你可以编写单元测试。

列表 1.14 显示了 `Hello.py` 的内容，它通过 `sys.argv` 提供了有用的功能：

```python
import sys

def main():
    if len(sys.argv) >= 2:
        name = sys.argv[1]
    else:
        name = 'World'
    print 'Hello', name

if __name__ == '__main__':
    main()
```

列表 1.14 使用逻辑判断来对 `name` 赋值，然后打印 `name`。

本章展示了 `ndarray` 对象的有用功能，你学会了如何处理数字，并转换 `name`。

# 总结

本章展示了如何处理数字，以及字符串的操作。你学会了如何使用 NumPy 对数字进行数学运算。

# 练习

**练习 1**：使用公式 $F = C*9/5 + 32$ 将摄氏度转换为华氏度。

**练习 2**：扩展你写的脚本，支持华氏度转换为摄氏度。

**练习 3**：编写一个 Python 脚本，接收用户的输入并打印回文。

**练习 4**：编写一个 Python 脚本，接收用户的输入并打印其回文。

**练习 5**：编写一个 Python 脚本，接收用户的输入并检查该字符串是否是回文。
