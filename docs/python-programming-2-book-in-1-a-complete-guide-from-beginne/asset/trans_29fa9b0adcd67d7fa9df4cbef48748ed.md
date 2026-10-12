

# 第 7 章：Python 中的交互性

Python 是一种全面的语言，利用了大量组件。然而，你需要记住，Python 成功最重要的原因之一在于其交互性。每种编程语言都使用不同的方法提供交互性。而 Python 则以借助模块和包提供交互性而闻名。在本章中，我们将结合大量示例详细讨论这些功能。请继续跟随学习！

## 模块如何提供交互性？

在 Python 中，可以使用 `import` 关键字来导入模块。例如，可以导入 `math` 模块，使用 `import math`。使用 `import` 导入模块的基本格式如下：

```
import firstmodule,secondmodule...
```

此时，如果模块位于同一位置，将会自动导入该模块。如果要调用模块中的函数，必须这样引用：`模块名.{输入函数名}`。调用模块中的函数时要加上模块名，因为多个模块中可能存在同名函数。此时，如果仅使用函数名调用，解释器无法知道该调用哪个函数。因此，如果按上述方式导入模块，调用函数时必须加上模块名。具体示例如下：

```
import math
# 这被认为是错误的
print(sqrt(12))
# 只有这种方式才能正确输出结果
print({在此处输入模块名}.sqrt(12))
```

有时我们只需要使用模块中的某个函数，只需导入该函数。此时，可以应用以下格式：

```
from {实体名称} import 函数名 1, 函数名 2 ..
```

为便于您理解，这里有一个实例：

```
from fib import {在此处输入斐波那契实例}
```

以这种方式导入函数时，调用函数时只能给出函数名，不能给出模块名，但当两个模块包含同名函数时，后导入的会覆盖先导入的。也就是说，如果模块 A 中有函数 `function`，模块 B 中也有函数 `function`。如果先导入 A 中的函数，再导入 B 中的函数，则调用函数时，执行的是模块 B 中的函数。

您也可以使用以下语句一次性导入所有内容：

```
From module name import *
```

应当注意的是，虽然 Python 提供了一种导入模块中所有项目的简单方法，但您也应该使用其他的导入语句。

当我们使用 `import` 导入模块时，Python 解释器如何找到对应的文件？这涉及 Python 的搜索路径，它由一系列目录名组成，Python 解释器会依次从这些目录中搜索导入的模块。搜索路径在 Python 编译或安装时确定，安装新库时也应进行修改。可以使用 `sys` 模块中的 `PATH` 变量进行搜索操作，通过以下代码验证：

```
import provider
print(provider.path)
```

现在，在解释器的当前目录或 `sys.path` 中的某个目录下创建一个 `fibo.py` 文件，包含以下示例代码：

```
# 斐波那契数列模块
deffib (n): # 定义斐波那契数列直到 n
    first, second = 0, 1
    while second < n:
        print(second, end=' ')
        first, second = second, first+second
    print()

def fib2 (n): # 返回斐波那契数列直到 n
    result = []
    first, second = 0, 1
    while second < n:
        result.append(second)
        first, second = second, first+second
    return result
```

然后进入 Python 解释器，使用以下命令导入该模块：

```
import fibo
```

这样做，直接定义在 `fibo` 中的函数名称不会写入当前符号表，但模块名称 `fibo` 会被写入。您可以使用模块名来访问函数，示例代码如下：

```
import fibo
fibo.fib(1000)
fibo.fib2(100)
fibo.__name__
```

如果您打算频繁使用某个函数，可以将其赋值给一个局部名称。示例代码如下：

```
fib=fibo.fib
fib(500)
```

## 模块制作

在 Python 中，每个 Python 文件都可以作为一个模块，模块的名称即文件的名称。此时，如果想在 `main.py` 文件中使用 `test.py` 文件，可以使用 `from test import add` 来导入。

示例 `main.py`：

```
from test import add
result = test.add(11,22)
print(result)
```

在实际开发中，开发人员编写完模块后，为了使模块在项目中达到预期效果，会在 py 文件中添加一些测试信息。此时，如果该文件被导入到其他 py 文件中，请思考测试代码是否也会执行？测试文件被导入到 `main.py` 中，示例代码如下：

从上述结果可以看出，`test.py` 中的测试代码也在运行。然而，这是不合理的。测试代码应仅在单独执行 `test.py` 时运行，而不应在被其他文件引用时执行。为了解决这个问题，Python 提供了一个特殊属性。每个模块都有一个特殊属性。当其值为 `'__main__'` 时，表示模块自身在运行，否则表示被引用。因此，如果我们希望模块中的某个程序块在模块被导入时不执行，可以通过判断 `__name__` 属性的值来实现。

## 包

为了更好地组织模块，通常将多个模块放入一个包中。包是存放 Python 模块文件的目录，且该目录下必须存在 `__init__.py` 文件（文件内容可以为空）。此时，如果 `main.py` 想要引用 `package_a` 中的 `module_a1`，可以用以下语句实现：

```
from package_a import module_a1
import package_a.module_a1
```

至此，我们完成了关于使用模块实现 Python 交互性的简要说明。在下一章中，我们将详细讨论结构。请继续跟随学习！

