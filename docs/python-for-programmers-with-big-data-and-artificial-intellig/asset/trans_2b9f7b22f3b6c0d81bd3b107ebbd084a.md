

你可以在以下位置查看标准库模块的完整列表：

2 《Python 教程》将此称为“自带电池”（batteries included）方法。

```
https://docs.python.org/3/library/
```

你已经使用了 decimal、statistics 和 random 模块中的功能。在下一节中，你将使用 math 模块中的数学功能。在本书的示例中，你将看到许多其他 Python 标准库模块，包括下表中的许多模块：

| Module | Description |
|---|---|
| math | 常见数学常数和运算。 |
| os | 与操作系统交互。 |
| profile, pstats, timeit | 性能分析。 |
| random | 伪随机数。 |
| re | 用于模式匹配的正则表达式。 |
| sqlite3 | SQLite 关系型数据库访问。 |
| statistics | 数学统计函数，如 mean、median、mode 和 variance。 |
| string | 字符串处理。 |
| sys | 命令行参数处理；标准输入、标准输出和标准错误流。 |
| collections | 除列表、元组、字典和集合之外的数据结构。 |
| Cryptography modules | 用于安全传输加密数据的模块。 |
| csv | 处理逗号分隔值文件（类似于 Excel 中的文件）。 |
| datetime | 日期和时间操作。还包括 time 和 calendar 模块。 |
| decimal | 定点和浮点算术，包括货币计算。 |
| doctest | 在 docstring 中嵌入验证测试和预期结果，以进行简单的单元测试。 |
| gettext and locale | 国际化和本地化模块。 |
| json | 用于 Web 服务和 NoSQL 文档数据库的 JavaScript 对象表示法 (JSON) 处理。 |
| tkinter | 图形用户界面 (GUI) 和基于画布的图形。 |
| turtle | 海龟图形。 |
| webbrowser | 用于在 Python 应用中方便地显示网页。 |

## 4.7 MATH 模块函数

math 模块定义了用于执行各种常见数学计算的函数。回顾前一章，以下形式的 `import` 语句使你能够通过模块名和点号 (.) 使用模块的定义：

```
In [1]: import math
```

例如，以下代码片段通过调用 `math` 模块的 `sqrt` 函数来计算 900 的平方根，该函数将结果作为 `float` 值返回：

```
In [2]: math.sqrt(900)
Out[2]: 30.0
```

同样，以下代码片段通过调用 `math` 模块的 `fabs` 函数来计算 -10 的绝对值，该函数将结果作为 `float` 值返回：

```
In [3]: math.fabs(-10)
Out[3]: 10.0
```

下面总结了一些 `math` 模块函数——你可以在以下位置查看完整列表：

| Function | Description | Example |
| :--- | :--- | :--- |
| `ceil(x)` | 将 x 舍入到不小于 x 的最小整数 | `ceil(9.2)` is `10.0`<br>`ceil(-9.8)` is `-9.0` |
| `floor(x)` | 将 x 舍入到不大于 x 的最大整数 | `floor(9.2)` is `9.0`<br>`floor(-9.8)` is `-10.0` |
| `sin(x)` | x 的三角正弦值（x 以弧度为单位） | `sin(0.0)` is `0.0` |
| `cos(x)` | x 的三角余弦值（x 以弧度为单位） | `cos(0.0)` is `1.0` |
| `tan(x)` | x 的三角正切值（x 以弧度为单位） | `tan(0.0)` is `0.0` |
| `exp(x)` | 指数函数 e^x | `exp(1.0)` is `2.718282`<br>`exp(2.0)` is `7.389056` |
| `log(x)` | x 的自然对数（底数为 e） | `log(2.718282) is 1.0`<br>`log(7.389056) is 2.0` |
| `log10(x)` | x 的对数（底数为 10） | `log10(10.0) is 1.0`<br>`log10(100.0) is 2.0` |
| `pow(x, y)` | x 的 y 次幂 | `pow(2.0, 7.0) is 128.0`<br>`pow(9.0, .5) is 3.0` |
| `sqrt(x)` | x 的平方根 | `sqrt(900.0) is 30.0`<br>`sqrt(9.0) is 3.0` |
| `fabs(x)` | x 的绝对值——始终返回 float。Python 还内置 abs 函数，根据其参数返回 int 或 float。 | `fabs(5.1) is 5.1`<br>`fabs(-5.1) is 5.1` |
| `fmod(x, y)` | x/y 的余数，作为浮点数返回 | `fmod(9.8, 4.0) is 1.8` |

## 4.8 使用 IPython Tab 补全进行探索

你可以在 IPython 交互模式中通过 Tab 键补全查看模块文档——这是一项加速编码和探索过程的发现功能。在输入标识符的一部分并按下 Tab 键后，IPython 会为你补全该标识符，或提供以你迄今所输入内容开头的标识符列表。这可能因你的操作系统平台以及已导入 IPython 会话的内容而异：

单击此处查看代码图像

```
In [1]: import math

In [2]: ma<Tab>
        map                %macro              %%markdown
        math               %magic              %matplotlib
        max()              %man
```

你可以使用上下箭头键浏览标识符。在此过程中，IPython 会高亮显示一个标识符，并在 In [ ] 提示符右侧显示它。

### 查看模块中的标识符

要查看模块中定义的标识符列表，请输入模块名和一个点号 (.)，然后按下 Tab 键：

单击此处查看代码图像

```
In [3]: math.<Tab>
        acos()             atan()              copysign()            e                   expml()
        acosh()            atan2()             cos()                 erf()               fabs()
        asin()             atanh()             cosh()                erfc()              factorial() >
        asinh()            ceil()              degrees()             exp()               floor()
```

如果要显示的标识符数量多于当前显示的数量，IPython 会在右侧边缘（在某些平台上）显示 > 符号，在这里是 factorial() 的右侧。你可以使用上下箭头键浏览列表。在标识符列表中：

- 后跟括号的是函数（或方法，稍后你将了解）。
- 以大写字母开头的单词标识符（如 Employee）以及每个单词都以大写字母开头的多单词标识符（如 CommissionEmployee）表示类名（前面的列表中没有）。Python 代码风格指南推荐的这种命名约定称为 CamelCase，因为大写字母像骆驼的驼峰一样突出。
- 没有括号的小写标识符（如 pi（未在前面的列表中显示）和 e）是变量。标识符 pi 的值为 3.141592653589793，标识符 e 的值为 2.718281828459045。在 math 模块中，pi 和 e 分别代表数学常数 π 和 e。

Python 没有常数，尽管 Python 中的许多对象都是不可变（不可修改）的。因此，尽管 pi 和 e 是现实世界中的常数，你也不应给它们赋予新值，因为这会更改它们的值。为了帮助将常数与其他变量区分开来，风格指南建议使用全大写字母命名自定义常数。

### 使用当前高亮的函数

在浏览标识符时，如果想要使用当前高亮的函数，只需开始在括号中输入其参数即可。IPython 随后会隐藏自动补全列表。如果需要关于当前高亮项目的更多信息，可以在名称后输入问号 (?) 并按 Enter 键查看帮助文档。以下显示了 fabs 函数的文档字符串：

单击此处查看代码图像

```
In [4]: math.fabs?
Docstring:
fabs(x)

Return the absolute value of the float x.
Type:	builtin_function_or_method
```

上面显示的 builtin_function_or_method 表明 fabs 是 Python 标准库模块的一部分。此类模块被视为内置于 Python。在此示例中，fabs 是 math 模块的一个内置函数。

## 4.9 默认参数值

定义函数时，可以指定参数具有**默认参数值**。在调用函数时，如果省略了带有默认参数值的参数的实参，则会自动传递该参数的默认值。让我们定义一个带有默认参数值的函数 `rectangle_area`：

单击此处查看代码图像

```
In [1]: def rectangle_area(length=2, width=3):
...:     """Return a rectangle's area."""
...:     return length * width
...:
```

指定默认参数值的方法是在参数名后跟一个 = 和一个值——在此示例中，`length` 和 `width` 的默认参数值分别为 2 和 3。任何带有默认参数值的参数都必须出现在参数列表中无默认值参数的*右侧*。

以下对 `rectangle_area` 的调用没有实参，因此 IPython 使用两个默认参数值，就好像你调用了 `rectangle_area (2, 3)` 一样：

```
In [2]: rectangle_area()
Out[2]: 6
```

以下对 `rectangle_area` 的调用只有一个实参。实参从左到右分配给参数，因此 10 被用作 `length`。解释器为 `width` 传递默认参数值 3，就好像你调用了 `rectangle_area (10, 3)` 一样：

```
In [3]: rectangle_area(10)
Out[3]: 30
```

以下对 `rectangle_area` 的调用同时为 `length` 和 `width` 提供了实参，因此 IPython 忽略默认参数值：

```
In [4]: rectangle_area(10, 5)
Out[4]: 50
```

## 4.10 关键字参数

