

```python
print("Cost at epoch", j, cost)
```

```python
# Plot cost versus # of iterations
print("W = ", W, "& b = ", b)
plt.plot(costs)
plt.xlabel('iterations (per tens)')
plt.show()
```

将列表 2.24 的新内容（**加粗显示**）与列表 2.23 的内容进行比较；变化非常小，主要的区别在于外层循环的每次迭代执行内层循环 100 次，而外层循环也执行了 100 次。列表 2.24 的输出如下：

```
(Cost at epoch', 1, ' = ', 0.071617249862147)
(Cost at epoch', 2, ' = ', 0.030073922512586938)
(Cost at epoch', 3, ' = ', 0.02541558299288472)
(Cost at epoch', 4, ' = ', 0.02422782633767794)
(Cost at epoch', 5, ' = ', 0.02346421967071181)
(Cost at epoch', 6, ' = ', 0.022827707922883803)
(Cost at epoch', 7, ' = ', 0.02228426269654064)
(Cost at epoch', 8, ' = ', 0.02181573175317663)
(Cost at epoch', 9, ' = ', 0.021416050179776294)
(Cost at epoch', 10, ' = ', 0.02107112540934884)
 details omitted for brevity
(Cost at epoch', 90, ' = ', 0.018960749188368278)
(Cost at epoch', 91, ' = ', 0.01896074755776306)
(Cost at epoch', 92, ' = ', 0.018960746155697425)
(Cost at epoch', 93, ' = ', 0.0189607449551148113)
(Cost at epoch', 94, ' = ', 0.018960743915559485)
(Cost at epoch', 95, ' = ', 0.018960740254513313)
(Cost at epoch', 96, ' = ', 0.018960742260386375)
(Cost at epoch', 97, ' = ', 0.018960741602798474)
('Cost at epoch', 98, ' = ', 0.018960741037589136)
('Cost at epoch', 99, ' = ', 0.018960740551780944)
('W = ', 0.6764145874436108, '& b = ', 0.09976839618922698)
```

图 2.13 显示了列表 2.24 的代价随迭代变化的图表。

![](img/55c2af1cab44d6186a8b2008b93f459f_109_0.png)

图 2.13 代价随迭代变化的图。

注意，图 2.13 的横轴上有 10,000 次迭代，而图 2.12 的横轴上只有 100 次迭代。

# 总结

本章向你介绍了 Python 的 NumPy 包。你学习了如何编写包含循环、数组和列表的 Python 脚本。你还学习了如何处理点积、使用 Matplotlib 绘图（将在第 4 章中详细讨论）以及线性回归。然后，你学习了如何处理数组的子集，这两者对于提取数据集的部分都非常有用。接下来，你学习了如何使用 NumPy 计算均方误差（MSE），以及如何使用 `linspace()` 计算 MSE。

本章的第一部分简要介绍了 Pandas 以及 Pandas 的一些实用功能，这些功能对于涉及数据集“切片和处理”的机器学习和深度学习任务非常有用。本章的第一部分介绍了你可以创建的各种类型的 DataFrame，例如数值和布尔 DataFrame。本章的第二部分展示了如何通过各种操作处理 DataFrame 的内容。章节的第三节概述了你可以使用 Pandas 执行的重要数据清洗任务。本章的最后一部分介绍了 Jupyter，这是一个基于 Python 的应用程序，可以在浏览器中显示并执行 Python 代码。你还将学习 Google Colaboratory，它是完全在线的并支持免费使用 GPU。

# 第 3 章

# Pandas 简介

Pandas 是一个 Python 包，与 NumPy、Matplotlib 等其他 Python 包兼容。在许多方面，Pandas 包具有电子表格的语义，它还可以与 xls、html 和 csv 文件一起工作。Pandas 提供了一种名为 DataFrame 的数据类型（类似于 Python 字典），具有极其强大的功能，将在下一节中讨论。Pandas DataFrames 支持多种输入类型，如数组、列表、字典或 Series。Pandas 还提供了另一种名为 Pandas Series 的数据类型（在本章中简要讨论）；这种结构为数据管理提供了另一种机制。

# Pandas DataFrame

简单来说，Pandas DataFrame 是一个二维数据结构，从行和列的角度考虑这种数据结构非常方便。DataFrame 可以被标记（行作为列），列可以包含不同的数据类型。类比，将 DataFrame 视为电子表格的对应物可能会有用，这使其成为 Pandas 相关 Python 脚本中非常有用的数据类型。数据集来源可以是数据文件、数据库表、网络服务等。Pandas DataFrame 的特性包括：

- DataFrame 方法
- DataFrame 统计
- 分组、透视和重塑
- 处理缺失数据
- 合并 DataFrame

# DataFrame 和数据清洗任务

你需要执行特定任务取决于数据集的结构和内容。通常你会按照以下步骤执行工作流（不一定按顺序），所有这些都可以通过 Pandas 完成：

- 将数据读入 dataframe
- 显示 dataframe 顶部
- 显示列数据类型
- 显示非缺失值
- 将 NA 替换为某个值
- 遍历列
- 每列的统计信息
- 查找缺失值
- 总缺失值
- 缺失值百分比
- 排序表格
- 打印摘要信息
- 缺失大于 50% 的列
- 重命名列

# 有标签的 Pandas DataFrame

列表 3.1 展示了 pandas-labeled-df.py 内容，如何定义一个行列都有标签的 Pandas DataFrame。

# 列表 3.1：pandas-labeled-df.py

```python
import numpy
import pandas as pd
myarray = numpy.array([[10,30,20], [50,40,60], [1000,2000,3000]])

rownames = ['apples', 'oranges', 'beer']
columns = ['January', 'February', 'March']

mydf = pd.DataFrame(myarray, index=rownames, columns=columns)

print(mydf)
print(mydf.describe())
```

列表 3.1 包含两个重要的语句，后面跟着变量 `myarray`，这是一个 3x3 的 NumPy 数组。变量 `rownames` 和 `columns` 分别为 `myarray` 中的行和列提供名称。接下来，初始化变量 `mydf` 为指定数据源的 Pandas DataFrame。

你可能会惊讶地发现输出的第一部分只需要一个打印语句（只需显示 mydf 的内容）。第二部分是通过调用任何 NumPy DataFrame 都可用的 `describe()` 方法生成的。`describe()` 方法非常有用；你会看到各种统计量，例如均值、标准差、最小值和最大值，这些都是按列（而不是按行）执行的，

