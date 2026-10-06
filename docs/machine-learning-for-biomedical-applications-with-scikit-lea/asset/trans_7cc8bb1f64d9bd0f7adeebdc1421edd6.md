

```python
def mysum(x,y):
    return x+y
```

```python
def mult(x,y):
    return x+y
```

```python
def divide(x,y):
    return x/y
```

这个例子显然是冗余的，但它可以作为一个简单的解释，因为我们现在可以想象通过 `sm @ load module` 来加载 simplemath。

```python
import simplemath as sm @ load module
```

```python
@ define variables
x=2; y=5
```

```python
print('output sum of x and y:', sm.mysum(x,y))
print('output product:', sm.mult(x,y))
print('output quotient:', sm.divide(x,y))
```

注意通过执行 `import`，模块函数对任何脚本都可用。在这里，模块的名称必须与代码存储的 .py 文件中的定义完全一致。一旦导入，模块中的函数就可以通过在函数函数名前加上导入时赋予模块的名称（使用 `sm`）来简单地调用。也可以使用 `from` 语法从模块中选择函数：

```python
from simplemath import divide
```

```python
print('output sum of x/y:', divide(x,y))
```

# 标准模块

某些模块随 Python 一起附带作为标准库.¹¹² 有用的示例包括：`copy`，之前提到过的作为内存中复制变量的方法；`os`，它支持与操作系统的交互（允许定义文件路径并更改当前工作目录）。还有 `sys`，它允许从 Python 搜索路径中添加和删除路径；因此，当你需要添加用户设计模块的位置时它是很有用的：

> 12 https://docs.python.org/3/tutorial/stdlib.html.

# 1.8.3 包

```python
import sys
sys.path.append('/some/path/')
```

最后，`math` 是 Python 的标准数学模块，包括其他函数外，向上取整或向下取整的操作：

```python
import math
x=2.2 ; y=4
round_up=math.ceil(x)
round_up=math.floor(x)
```

Python 包是相关类和模块的集合，旨在解决某些大类任务。为了满足各种高级编程需求，存在大量由外部支持且文档齐全的包。本模块将包含的一些示例包括：

- *NumPy[32]¹³—一个用于科学计算的包，具有快速操作数组的功能和强大的数值计算工具 [19]*
- *Matplotlib[20]¹⁴—一个绘图库，旨在模拟 MATLAB 的绘图行为；
- *Scikit Learn¹⁵—一个强大的工具箱，具有广泛的机器学习方法实现和直观的 API [6,34]；
- *Pandas¹⁶—用于创建和处理复杂表格数据表的工具 [50]；
- *Nibabel¹⁷—一个读取和写入医学图像文件格式的库。

我们将在适当的时候学习更多这些包，从后续第 1.9 节的 NumPy 开始。注意，当代码使用此类包时，在生成的项目和论文中引用它们是非常重要的。

# 安装包

假设你已经安装了 Anaconda，那么所有列出的包（Nibabel 除外）应该已经安装。然而，对于其他包（如 Nibabel），有两种安装方法：要么通过 Anaconda：

```bash
conda install -c conda nibabel
```

> ¹³ http://www.NumPy.org/
¹⁴ https://matplotlib.org/
¹⁵ https://scikit-learn.org/
¹⁶ https://pandas.pydata.org/
¹⁷ http://nipy.org/nibabel/
¹⁸ https://www.scipy.org/citing.html.

或者通过 python 安装包 pip：

```bash
pip install nibabel
```

这些命令应该在你的本地系统的终端（或 cmd）窗口中输入。在这里，`conda-forge` 代表一个独立的社区资源，它是通过 Anaconda 安装的流行 Python 仓库。一些非常流行的包也可以通过运行 `conda install <package>` 从主 Anaconda 安装获取。要更新包，请使用 `pip install <package> --upgrade` 或 `conda update <package>`

# 1.8.4 类

进一步，Python 是一种面向对象的语言，允许将代码结构化为类。这支持整洁高效的编码风格，进一步提高了代码的可读性和重用性。Python 类的基本结构可以写成：

```python
class ClassName:
<statement-1>
.
<statement-N>
```

其中有必要用构造函数（实例化函数）开始类，例如：

```python
class MyClass:
def __init__(self): # 构造函数
self.data = []
```

```python
x=MyClass() @ 创建类的新实例。
```

构造函数的任务是创建类的实例，并对代码其他地方使用的类属性进行初始化（赋值）。在 Python 中，构造函数由 `__init__()` 方法组成，并且在创建对象时总是被调用。构造函数之外，类还包含属性和方法（函数）定义：

```python
class MyClass:

# 创建一个类属性
my_class_attribute="bananas"
def __init__(self):
    self.data = []
    # 创建一个实例属性
    self.instance_attr = random.randint(1, 100)
```

```python
def f(self):    函数 -> 对象方法
    return 'hello world'
```

在这里，属性可以在构造函数之外定义（如 `my_class_attribute` 所示）。这对于类的每一个实例来说都都是相同的（'bananas'）。或者，每个实例可以有它自己的“属性”，例如 `self.instance_attr`，在构造函数或类方法内部定义；这些描述了正在创建的对象的属性，例如下一节中 NumPy 矩阵的形状、大小、ndim 和 dtype。

理解 Python 类的格式是开发和利用 Python 包的必经知识。然而，在本书中，我们将坚持相对简单的脚本。因此，我们将对高级特性的研究留给读者。

# 1.9 NumPy

NumPy（"Numerical" 的缩写）是基于 NumPy 基础的，由外部支持且文档齐全的库。在计算中，NumPy 通常被导入为：

```python
import numpy as np
```

# 1.9.1 数组

在术语中，数组是数据结构，使用 `arange([start], [stop], [step])` 在范围内均匀采样，例如 `np.arange(50,85)` 在 [50-80) 范围内以步长为 5 进行采样。注意，当采样所有整数时，只需要定义范围的终点，例如，`np.arange(5)` 返回 [0,1,2,3,4]。当，替代，寻求范围范围内的数量时，使用 `np.linspace(start,end,num)`。在这里，`num` 决定了样本的数量和间隔的大小。

# 1.9.2 创建数组

有些用于数组生成的填充方法：

```python
zeros=np.zeros((3,3))
ones=np.ones((3,3))
identity = np.eye(3)
empty=np.empty((3,3))
```

在这里，`zeros` 创建全 0 3x3 数组；`ones` 创建全 1 数组；`eye` 创建单位矩阵，`empty` 创建未初始化的数组。注意在每种情况下返回的数组大小都是 33；然而，函数的区别取决于形状是作为元组传递还是每个维度作为单独参数传递。

# 1.9.3 从列表初始化

NumPy 数组也可以从列表初始化：

```python
# 创建 1D 数组
my_array=np.array([1,2,3,4,5,6])
# 创建 2D 数组
my_matrix=np.array([[1,2,3,4,5,6],[7,8,9,10,11,12]])
```

# 1.9.4 随机数生成

NumPy 还有一个子模块 `np.random`，¹ 创建遵循特定随机分布的数组，包括 [0,1) 范围内的均匀分布样本：

```python
rand1=np.random.random(3,3)
```

从标准正态分布采样的浮点数

```python
rand2=np.random.randn(3,3)
```

以及某些范围内的随机整数，例如 [5,20):

```python
rand3=np.random.randint(5,20,(3,3))
```

