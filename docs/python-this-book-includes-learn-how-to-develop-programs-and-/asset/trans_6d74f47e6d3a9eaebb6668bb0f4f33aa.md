

## 4. 添加返回语句 (return statement)

示例：
```python
def hello():
    print("Hello World")
    return
```

不要忘记，你可以为你的自定义函数定义一个或多个函数参数。

## 返回语句 (Return Statement)

```python
def hello():
    print("Hello World")
    return("hello")
```

```python
def hello_noreturn():
    print("Hello World")
    # 将 `hello()` 的输出乘以 2
    hello() * 2
    # (尝试将 `hello_noreturn()` 的输出乘以 2
    hello_noreturn() * 2
```

第二个函数会报错，因为无法对 `None` 值进行操作。因此，如果你运行这段代码，将得到一个 `TypeError`，通知你无法使用 `NoneType` 完成乘法运算。

函数一旦遇到 `return` 语句就会立即终止。

```python
def run():
    for x in range(10):
        if x == 2:
            return
    print("Run!")
run()
```

返回语句可以显示多个值。元组（Tuples）允许你返回多个语句。
请看以下示例以学习如何返回多个值。

## 定义 `plus()`
```python
def plus(a,b):
    sum = a + b
    return (sum, a)
```

## 调用 `plus()` 并解包变量
```python
sum, a = plus(3,4)
# 打印 `sum()`
print(sum)
```

## 调用函数 (Calling a Function)

在之前的示例中，你学习了如何调用函数。调用函数顾如其名，意味着你直接从 Python 提示符或从另一个函数中执行该函数。
你通过运行 `hello()` 来调用你的 `hello()` 函数。

## 在 Python 函数中添加文档字符串 (Docstring)

定义 Python 函数最关键的属性是文档字符串（docstring）。
创建 Python 函数的另一个基本特性是文档字符串。docstrings 描述了你的函数执行的任务，例如它们的返回值。这些描述充当函数的文档，以便任何人都能理解函数的 docstring，而无需监控函数定义内部所有的代码。

函数 docstring 紧跟在函数头之后出现，并包含在三引号内。`hello()` 函数的正确 Docstring 会打印“Hello World”。

```python
def hello():
    """Prints "Hello World"

    Returns:
        None
    """
    print("Hello World")
    return
```

记住 docstring 可以比这里展示的更多。如果你想进一步学习 docstring，你应该查看 Python 库的 Github 仓库，你可以在那里找到很多示例。

## Python 函数参数 (Arguments)

开始时，你阅读了参数（arguments）和形式（parameters）的区别。简单来说，参数是指给任何函数或方法调用的内容，而函数或方法代码通过它们的参数名称引用这些参数。Python 自定义函数可以接受四类参数：

- 关键字参数 (Keyword arguments)
- 默认参数 (Default arguments)
- 强制参数 (Required arguments)
- 可变参数 (Variable number of arguments)

## 关键字参数 (Keyword Arguments)

如果你想按顺序调用参数，可以在函数调用中包含关键字参数 `#`。示例：

```python
# 定义 `plus()` 函数
def plus(a,b):
    return a + b
# 使用参数调用 `plus()` 函数
plus(2,3)
# 使用关键字参数调用 `plus()` 函数
plus(a=1, b=2)
```

通过使用关键字参数，你可以变换参数的顺序，并在运行函数时仍获得相同的结果。

## 定义 `plus()` 函数
```python
def plus(a,b):
    return a + b
# 使用关键字参数调用 `plus()` 函数
plus(b=2, a=1)
```

## 强制参数 (Required Arguments)

顾如名，这些是必须存在的参数。这些参数需要在函数调用期间传递，并且必须按照完全正确的顺序，如下例所示：

## 带强制参数的 `plus()`
```python
def plus(a,b):
    return a + b
```

## 全局变量和局部变量 (Global and Local Variables)

在函数体内定义的变量具有全局作用域。换句话说，局部变量定义在函数块内部，只能在该函数内部被访问；而全局变量可以被脚本中的所有函数获取。

## 全局变量 `init`
```python
init = 1
# 定义接受可变参数的 `plus()` 函数
```

```python
def plus(*args):
    # 局部变量 `sum()`
    total = 0
    for i in args:
        total += i
    return total

# 访问全局变量
print('this is the initialized value ' + str(init))
# (尝试)访问局部变量
print('this is the sum ' + str(total))
```

你会发现，当你尝试显示在函数体内定义的局部变量 `total` 时，会得到一个 `NameError`，显示名称‘total’未定义。相反，`init` 变量可以无任何问题地显示。

## Python 中的匿名函数 (Anonymous Functions)

匿名函数也称为 lambda，因为它们使用了 `lambda`。
示例：
```python
double = lambda x: x*2
double(5)
```

这个函数的特殊之处在于它没有像你在本章第一部分遇到的之前的示例那样命名。
当你需要一个短期用途的无名函数时，就会使用 lambda 函数。在处理 `filter()`、`map()` 和 `reduce()` 时，这些特定的上下文相关：
- functools import reduce
- filter(x, list)
- map(x, list)

## Main 函数

```python
def main():
    print("This is main")

if __name__ == "__main__":
    main()
```

如果你想按正确的顺序调用参数，可以在函数调用中包含关键字参数 `#`。

```python
if __name__ == "__main__":
    main()
```

除了 `__main__` 函数，还有 `__init__` 函数用于初始化实例。

## 第 6 章：Python 运算符 (Operators)

Python 运算符对值和变量执行操作。运算符可以修改项目并输出结果。数据项目被称为操作数。运算符使用关键字或唯一字符表示。

## 算术运算符 (Arithmetic operators)

这些执行不同的计算，如减法、除法、加法、幂等。Python 中有不同的算术计算方法，你可以声明变量。

```python
b = 4
c = 5
print (b + c)
```

仍然，你可以使用除法、减法和乘法算术运算符。

## Python 逻辑运算符 (Logical operators)

Python 中有 3 种逻辑运算符。

or, and, not
示例：
```python
a or b
a and b
not a
not b
```

## 运算符优先级 (Operator precedence)

Python 运算符根据一组优先级进行计算。下表显示了 Python 中的运算符优先级。

| 描述 | 运算符 |
|---|---|
| 1 | 幂 | ** |
| 2 | 取反、一元加和负号 | ~, +, - |
| 3 | 乘法、除法、取模和整除 | *, /, %, // |
| 4 | 加法和减法 | + - |
| 5 | 右移和左移 | >>, << |
| 6 | 位与“与” | & |
| 7 | 普通“或”和位异异“或” | |, ^ |
| 8 | 比较运算符 | <= <> >= |
| 9 | 等于运算符 | == != |= |
| 10 | 赋值运算符 | =, +=, -=, *, %, //= |
| 11 | 标识运算符 | is, is not |
| 12 | 成员运算符 | in, not in |
| 13 | 逻辑运算符 | or, and, not |

