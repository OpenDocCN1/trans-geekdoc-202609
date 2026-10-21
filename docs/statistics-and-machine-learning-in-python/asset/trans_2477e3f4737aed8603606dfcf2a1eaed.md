
进程 = 地址空间 + 执行上下文（控制线程）

进程地址空间（段）：

- 代码。
- 数据（静态/全局）。
- 堆（动态内存分配）。
- 栈。

执行上下文：

- 数据寄存器。
- 栈指针（SP）。
- 程序计数器（PC）。
- 工作寄存器。

操作系统进程调度：上下文切换（即 保存/加载 执行上下文）

## 优缺点

- 上下文切换开销大。
- （潜在地）复杂的数据共享（不一定为真）。
- 协作进程 - 无需内存保护（独立地址空间）。
- 与内存分配的并行计算相关。

## 线程

- 线程共享相同的地址空间（数据寄存器）：可访问代码、堆和（全局）数据。
- 独立的执行栈、PC 和工作寄存器。

## 优缺点

- 更快的上下文切换，仅涉及 SP、PC 和工作寄存器。
- 可利用细粒度并发
- 通过共享地址空间实现简单的数据共享。
- 必须采取预防措施，否则两个线程会同时写入同一内存。这就是全局解释器锁（GIL）的用途。
- 与 GUI、I/O（网络、磁盘）并发操作相关

## 在 Python 中

- threading 模块使用线程。
- multiprocessing 模块使用进程。

## 多线程

```
import time
import threading
```

```
def list_append(count, sign=1, out_list=None):
    if out_list is None:
        out_list = list()
    for i in range(count):
        out_list.append(sign * i)
        sum(out_list) # do some computation
    return out_list

size = 10000  # Number of numbers to add

out_list = list() # result is a simple list
thread1 = threading.Thread(target=list_append, args=(size, 1, out_list, ))
thread2 = threading.Thread(target=list_append, args=(size, -1, out_list, ))

starttime = time.time()
# Will execute both in parallel
thread1.start()
thread2.start()
# Joins threads back to the parent process
thread1.join()
thread2.join()
print("Threading elapsed time ", time.time() - starttime)

print(out_list[:10])
```

输出：

```
Threading elapsed time  1.7804272174835205
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## 多进程

```
import multiprocessing

# Sharing requires specific mechanism
out_list1 = multiprocessing.Manager().list()
p1 = multiprocessing.Process(target=list_append, args=(size, 1, None))
out_list2 = multiprocessing.Manager().list()
p2 = multiprocessing.Process(target=list_append, args=(size, -1, None))

starttime = time.time()
p1.start()
p2.start()
p1.join()
p2.join()
print("Multiprocessing elapsed time ", time.time() - starttime)

# print(out_list[:10]) is not available
```

输出：

```
Multiprocessing elapsed time  0.3432891368865967
```

## 使用 Managers 在进程间共享对象

Managers 提供了一种创建可在不同进程之间共享的数据的方式，包括在不同机器上运行的进程之间通过网络共享。管理器对象控制一个服务器进程，该进程管理共享对象。

```
import multiprocessing
import time

size = int(size / 100)  # Number of numbers to add

# Sharing requires specific mechanism
out_list = multiprocessing.Manager().list()
p1 = multiprocessing.Process(target=list_append, args=(size, 1, out_list))
p2 = multiprocessing.Process(target=list_append, args=(size, -1, out_list))

starttime = time.time()

p1.start()
p2.start()

p1.join()
p2.join()

print(out_list[:10])

print("Multiprocessing with shared object elapsed time ", time.time() - starttime)
```

输出：

```
[0, 1, 2, 3, 4, 5, 0, 6, -1, 7]
Multiprocessing with shared object elapsed time  0.6759169101715088
```

## 3.9 脚本和参数解析

示例，词计数脚本

```
import os
import os.path
import argparse
import re
import pandas as pd

if __name__ == "__main__":
    # parse command line options
    output = "word_count.csv"
    parser = argparse.ArgumentParser()
    parser.add_argument('-i', '--input',
                        help='list of input files.',
                        nargs='+', type=str)
    parser.add_argument('-o', '--output',
                        help='output csv file (default %s)' % output,
                        type=str, default=output)
    options = parser.parse_args()

    if options.input is None :
        parser.print_help()
        raise SystemExit("Error: input files are missing")
    else:
filenames = [f for f in options.input if os.path.isfile(f)]

# Match words
regex = re.compile("[a-zA-Z]+")

count = dict()
for filename in filenames:
    fd = open(filename, "r")
    for line in fd:
        for word in regex.findall(line.lower()):
            if not word in count:
                count[word] = 1
            else:
                count[word] += 1

fd = open(options.output, "w")

# Pandas
df = pd.DataFrame([[k, count[k]] for k in count], columns=["word", "count"])
df.to_csv(options.output, index=False)
```

## 3.10 网络

```
# TODO
```

### 3.10.1 FTP

```
# Full FTP features with ftplib
import ftplib
ftp = ftplib.FTP("ftp.cea.fr")
ftp.login()
ftp.cwd('/pub/unati/people/educhesnay/pystatml/datasets')
ftp.retrlines('LIST')

fd = open(os.path.join(tmpdir, "readme1.rst"), "wb")
ftp.retrbinary('RETR readme.rst', fd.write)
fd.close()
ftp.quit()

# File download urllib
import urllib.request
ftp_url = 'ftp://ftp.cea.fr/pub/unati/people/educhesnay/pystatml/datasets/readme.rst'
urllib.request.urlretrieve(ftp_url, os.path.join(tmpdir, "readme2.rst"))
```

输出：

```
-rw-r--r--  1 ftp ftp      5166 Dec 04  2017 Advertising.csv
-rw-r--r--  1 ftp ftp      4955 Feb 22  2018 birthwt.csv
-rw-r--r--  1 ftp ftp      1357 Feb 22  2018 birthwt_info.txt
-rw-r--r--  1 ftp ftp   5539328 Sep 13  2016 default of credit card clients.xls
-rw-r--r--  1 ftp ftp      2443 Sep 13  2016 eurodist.csv
-rw-r--r--  1 ftp ftp      3858 Sep 13  2016 iris.csv
-rw-r--r--  1 ftp ftp 152 Sep 13 2016 readme.rst
-rw-r--r--  1 ftp ftp 77352 Sep 20 2016 s_curve.csv
-rw-r--r--  1 ftp ftp 840 Sep 13 2016 salary_table.csv
```

### 3.10.2 HTTP

```
# TODO
```

### 3.10.3 Sockets

```
# TODO
```

### 3.10.4 xmlrpc

```
# TODO
```

## 3.11 模块和包

一个模块是 Python 文件。包是一个目录，必须包含一个名为 __init__.py 的特殊文件

要导入，请扩展变量 PYTHONPATH：

```
export PYTHONPATH=path_to_parent_python_module:${PYTHONPATH}
```

或

```
import sys
sys.path.append("path_to_parent_python_module")
```

__init__.py 文件可以为空。但你可以通过覆盖 __all__ 变量来设置包作为 API 导出的模块，同时保持其他模块内部，如下所示：

parentmodule/__init__.py 文件：

```
from . import submodule1
from . import submodule2

from .submodule3 import function1
from .submodule3 import function2

__all__ = ["submodule1", "submodule2",
    "function1", "function2"]
```

用户可以导入：

```
import parentmodule.submodule1
import parentmodule.function1
```

## Python 单元测试

## 3.12 面向对象编程（OOP）

## 来源

- http://python-textbook.readthedocs.org/en/latest/Object_Oriented_Programming.html

## 原则

- **封装** 数据（属性）和代码（方法）到对象中。
- **类** = 可用于创建对象的模板或蓝图。
- 一个 **对象** 是类的特定实例。
- **继承：** OOP 允许类从其他类继承常用的状态和行为。减少代码重复
- **多态：** （通常通过多态获得）调用代码对对象是否属于父类或其后代不敏感（抽象、模块化）。对两个不同类的两个对象调用相同的方法会表现出不同的行为。

```python
import math

class Shape2D:
    def area(self):
        raise NotImplementedError()

# __init__ is a special method called the constructor

# Inheritance + Encapsulation
class Square(Shape2D):
    def __init__(self, width):
        self.width = width

    def area(self):
        return self.width ** 2

class Disk(Shape2D):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return math.pi * self.radius ** 2

shapes = [Square(2), Disk(3)]

# Polymorphism
print([s.area() for s in shapes])

s = Shape2D()
try:
    s.area()
except NotImplementedError as e:
    print("NotImplementedError")
```

输出：

