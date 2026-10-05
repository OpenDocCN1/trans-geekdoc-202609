

# Python 2.7 编程教程 219

```python
>>> type(oi)
<type 'function'>
>>>
```

当 Python 启动时，总是会定义三个变量：`__builtins__`、`__doc__` 和 `__name__`。这些变量用于高级工作，我们现在不需要关心。

注意，当我们定义一个变量（`frankness`）时，下次调用 `dir()` 时，`frankness` 会出现在结果列表中。当我们定义一个函数（`oi`）时，它的名称也会被添加。注意，你也可以使用 `type(function)` 来查找任何已定义名称类型：`frankness` 的类型为 `float`，而 `oi` 的类型为 `function`。

现在让我们看看当我们将 `math` 模块导入到全局命名空间时会发生什么：

```python
>>> from math import *
>>> dir()
['__builtins__', '__doc__', '__name__', 'acos', 'asin', 'atan', 'atan2', 'ceil', 'cos', 'cosh', 'degrees', 'e', 'exp', 'fabs', 'floor', 'fmod', 'frankness', 'frexp', 'hypot', 'ldexp', 'log', 'log10', 'modf', 'oi', 'pi', 'pow', 'radians', 'sin', 'sinh', 'tan', 'tanh']
>>> sqrt(64)
8.0
>>> pi*10.0
31.415926535897931
>>> cos(0.0)
>>>
```

如你所示，我们定义的名称（`oi` 和 `frankness`）仍然在那里，但 `math` 模块所有的变量和函数现在都在全局命名空间中了，我们可以像使用 `sqrt()` 和 `pi` 那样使用它们。

通常情况下，这种形式的导入语句会将模块中的所有函数和变量复制到当前命名空间：

```python
from someModule import *
```

然而，你也可以选择要导入哪些项。使用这种形式的语句：

```python
from someModule import item1, item2, ...
```

其中关键字 `import` 后面跟着一个逗分隔分隔列表。

这是另一个例子。假设你刚刚启动了一个全新的 Python 会话，并且只想导入 `sqrt()` 函数和常量 `pi`：

```python
>>> dir()
['__builtins__', '__doc__', '__name__']
>>> math import sqrt, pi
>>> dir()
['__builtins__', '__doc__', '__name__', 'pi', 'sqrt']
>>> sqrt(25.0)
5.0
>>> cos(0.0)
Traceback (most recent call last):
File "stdin>", line 1, in <module>
NameError: name 'cos' is not defined
```

我们没有请求 `cos()` 函数，所以它不在全局命名空间中。

# 导入整个模块

某些模块内部包含几百个不同的项。在这种情况下，你可能不想让所有项弄乱你的全局命名空间。另一种导入模块的方法。这里是通用形式：

```python
import moduleName
```

该语句只向当前命名空间添加一个名称——模块本身的名称。然后你可以使用这种形式的表达式来引用该模块内的任何项：

```python
moduleName.itemName
```

这是一个示例，再次使用内置的 `math` 模块。假设你刚刚启动了一个新的 Python 会话，并且还没有向命名空间添加任何内容。

```python
>>> dir()
['__builtins__', '__doc__', '__name__']
```

```python
>>> import math
>>> dir()
['__builtins__', '__doc__', '__name__', 'math']
>>> type(math)
<type 'module'>
>>> math.sqrt(121.0)
11.0
>>> math.pi
3.1415926535897931
>>> math.cos(0.0)
1.0
```

如你所示，使用这种形式的导入只向命名空间添加一个名称，该名称的类型为 `module`。

我们还应该提到另一个的一个额外功能。如果你想导入整个模块 $M_1$，但你想用另一个名称 $M_2$ 来引用它的内容，请使用这种形式的语句：

```python
import $M_1$ as $M_2$
```

一个示例：
```python
>>> dir()
['__builtins__', '__doc__', '__name__']
>>> import math as crunch
>>> dir()
['__builtins__', '__doc__', '__name__', 'crunch']
>>> type(crunch)
<type 'module'>
>>> crunch.pi
3.1415926535897931
>>> crunch.sqrt(888.888)
29.81422479287362
```

你可以将 Python 内置的 `dir()` 函数应用于模块对象，以查找其内部定义的名称：

```python
>>> import math
>>> dir()
['__builtins__', '__doc__', '__name__', 'math']
>>> dir(math)
['__doc__', '__file__', '__name__', 'acos', 'asin', 'atan', 'atan2', 'ceil', 'cos', 'cosh', 'degrees', 'e', 'exp', 'fabs', 'floor', 'fmod', 'frexp', 'hypot', 'ldexp', 'log', 'log10', 'modf', 'pi', 'pow', 'radians', 'sin', 'sinh', 'tan', 'tanh']
```

（注：原文后半部分似乎存在重复或乱码文本，已根据指令要求翻译并确保逻辑对应）

