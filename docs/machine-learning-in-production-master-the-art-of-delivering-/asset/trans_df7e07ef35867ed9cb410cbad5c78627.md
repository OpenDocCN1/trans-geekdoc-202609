

```python
13.     print("Size: ", my_narray.size)
14.     Size: 1
```

```python
1. # Rank 1 Array (vector)
2. my_narray = np.array([4,5,6])
3. print(my_narray)
4. [4 5 6]
5. print("Dimension: ", my_narray.ndim)
6. Dimension: 1
7. print("Shape: ", my_narray.shape)
8. Shape: (3,)
9. print("Size: ", my_narray.size)
10.     Size: 3
```

```python
1. # Rank 2 Array (matrix)
2. my_narray = np.array([[1,2,3],[4,5,6]])
3. print(my_narray)
4. [[1 2 3]
5.  [4 5 6]]
6. print("Dimension: ", my_narray.ndim)
7. Dimension: 2
8. print("Shape: ", my_narray.shape)
9. Shape: (2, 3)
10.     print("Size: ", my_narray.size)
11.     Size: 6
```

```python
1. # Rank 3 Array
2. my_narray = np.array([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]]])
3. print(my_narray)
4. [[[ 1 2 3]
5.   [ 4 5 6]]
6.  [[ 7 8 9]
7.  [10 11 12]]]
8. print("Dimension: ", my_narray.ndim)
9. Dimension: 3
10.     print("Shape: ", my_narray.shape)
11.     Shape: (2, 2, 3)
12. print("Size: ", my_narray.size)
13. Size: 12
```

## 重塑数组

假设你想在不丢失数据的情况下更改 ndarray（N 维数组）的形状，可以使用 reshape() 或 flatten() 方法来完成。

### 示例：1.16 重塑 NumPy 数组

```python
1. # Rank 1 Array
2. my_1array = np.array([1,2,3,4,5,6])
3. print(my_1array)
4. [1 2 3 4 5 6]
```

```python
1. # converting Rank 1 array to Rank 2 array
2. my_2array = my_1array.reshape(2, 3)
3. print(my_2array)
4. [[1 2 3]
5. [4 5 6]]
```

```python
1. #converting Rank 2 array to Rank 1 array
2. my_1array = my_2array.flatten()
3. print(my_1array)
4. [1 2 3 4 5 6]
```

> 注意：在此，你可以使用 my_2array.reshape(6) 代替 flatten()。

## Pandas

Pandas 是一个开源的、BSD 许可的库，为 Python 编程语言提供高性能、易于使用的数据结构和数据分析工具。DataFrame 是一个二维标记数据结构，其列可能具有不同的类型。

你可以使用 pip 安装 Pandas 包：

```bash
pip install pandas
```

### 示例：1.17 Pandas DataFrame 用法

```python
1. import pandas as pd
2. df = pd.DataFrame(data={'fruit': ['apple', 'banana', 'orange',
3.       'mango',
4.       'size': ['large', 'medium', 'small',
5.       'medium']],
6.       'quantity': [5,4,8, 6]})
7.
8. print(df)
```

| 水果    | 大小    | 数量     |
|---------|---------|----------|
| 苹果    | 大      | 5        |
| 香蕉    | 中等    | 4        |
| 橙子    | 小      | 8        |
| 芒果    | 中等    | 6        |

在以下示例中，head() 检索 Pandas DataFrame 的顶部行。

### 示例：1.18 获取 DataFrame 的前 n 行

```python
1. df.head(2)
```

| 水果    | 大小    | 数量     |
|---------|---------|----------|
| 苹果    | 大      | 5        |
| 香蕉    | 中等    | 4        |

而 tail() 检索 Pandas DataFrame 的底部行。

### 示例：1.19 获取 DataFrame 的最后 n 行

```python
1. df.tail(2)
```

| 水果    | 大小    | 数量     |
|---------|---------|----------|
| 橙子    | 小      | 8        |
| 芒果    | 中等    | 6        |

在以下示例中，describe() 显示 DataFrame 数值列的快速统计摘要。

### 示例：1.20 获取基本统计信息

```python
1. df.describe()
```

| | 数量 |
|---|----------|
| 计数 | 4.000000 |
| 平均值 | 5.750000 |
| 标准差 | 1.707825 |
| 最小值 | 4.000000 |
| 25% | 4.750000 |
| 50% | 5.500000 |
| 75% | 6.500000 |
| 最大值 | 8.000000 |

```python
1. df['fruit']
2. 0 apple
3. 1 banana
4. 2 orange
5. 3 mango
6. Name: fruit, dtype: object
```

## loc - 按标签选择

loc 用于获取具有特定标签的行（和/或列）。要获取所有水果大小为中等的行，loc 的写法如下：

### 示例：1.21 按位置获取数据

```python
1. df.loc[df['size'] == 'medium']
```

| 水果    | 大小    | 数量     |
|---------|---------|----------|
| 香蕉    | 中等    | 4        |
| 芒果    | 中等    | 6        |

## iloc - 按位置选择

iloc 用于获取索引位置处的行（和/或列）。要获取索引为 2 的行，iloc 的写法如下：

### 示例：1.22 按位置获取数据

```python
1. df.iloc[2]
2. fruit orange
3. size small
4. quantity 8
5. Name: 2, dtype: object
```

要检索从索引 2 到 3 和列 0 到 1 的行，iloc 的写法如下：

```python
1. df.iloc[2:4, 0:2]
```

| 水果    | 大小    |
|---------|---------|
| 橙子    | 小      |
| 芒果    | 中等    |

你可以调用 groupby() 并传递 size，即要对其进行分组的列，然后使用 sum() 聚合方法。

### 示例：1.23 对数据分组，然后使用聚合函数

```python
1. df.groupby(['size'])['quantity'].sum()
```

| 大小   | 数量 |
|--------|------|
| 大     | 5    |
| 中等   | 10   |
| 小     | 8    |

名称：数量，数据类型：int64

## 保存和加载 CSV 文件

### 示例：1.24 保存和加载 CSV 文件

```python
1. df.to_csv("fruit.csv")
2. df = pd.read_csv("fruit.csv")
```

## 保存和加载 Excel 文件

### 示例：1.25 保存和加载 Excel 文件

```python
1. df.to_excel("fruit.xlsx", sheet_name="Sheet1")
2. df = pd.read_excel("fruit.xlsx", "Sheet1", index_col=None)
```

有关更多信息，可以参考 https://pandas.pydata.org/docs/ 上的官方文档。

## 结论

本章通过示例讨论了 Python 语言的基本概念。在本章开头，你学习了如何在系统中安装 Python。随后，你通过示例学习了 Python 中的常见数据结构和面向对象编程概念。接着，使用 NumPy 和 Pandas 等包介绍了数据预处理命令，这些命令在开发机器学习模型中将发挥重要作用。

在下一章中，你将通过示例学习 git 和 GitHub。

## 要点

- 确保在整个机器学习项目中使用相同的 Python 版本。
- 类中的 __init__() 方法用于自动初始化数据成员和方法。但是，这不是强制性的。
- 元组是不可变的，即它们不可更改，但如果它们包含类似列表的元素，那么列表是可变的，而整个元组则不是。

## 选择题

- 1. np.array([[1,2,3],[4,5,6]]) 的输出是什么？
- a) 秩 1 数组
- b) 秩 2 数组
- c) 秩 3 数组
- d) 以上皆是

- 2. 集合可以包含 _______ 元素。
- a) 异质
- b) 同质
- c) 仅整数
- d) 仅字符串

## 答案

- 1. b
- 2. a

## 问题

- 1. 列表和元组有什么区别？
- 2. __init__() 的用途是什么？
- 3. 何时应该使用 pass 语句？

## 关键术语

**面向对象编程**：它是一种基于对象概念的编程范式，对象可以包含数据和方法。

## 加入我们的图书 Discord 空间

加入图书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的交流会议：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_40_0.png)

## 第 2 章 Git 和 GitHub 基础

### 简介

在团队中工作时，维护文件的多个版本很困难。Git 通过允许开发人员与其他团队成员协作和共享文件来解决这个问题。本章介绍了构成本书基础的最基本 Git 和 GitHub 概念。它解释了 Git 配置、分叉 Git 仓库、将代码库推送到 GitHub 以及克隆过程。此外，还介绍了 GitHub Actions、常用 Git 命令及其语法和示例。在团队中工作时，维护文件的多个版本可能很困难，但 Git 是解决方案。

### 结构

本章将涵盖以下主题：

- Git 概念
- 常用 Git 工作流
- 安装 Git 并创建 GitHub 帐户
- 常用 Git 命令
- 让我们开始使用 Git

### 目标

学习本章后，你应该知道如何执行 Git 命令并连接到远程 GitHub 仓库。理解并执行 Git 流程。你应该知道如何将更改推送、获取和恢复到远程 Git 仓库，并且你应该熟悉如何在你的计算机或服务器上安装和执行 Git 的基本配置。

### Git 概念

Git 是一种开源的分布式版本控制系统（DVCS）。版本控制系统允许你记录一段时间内对文件的更改。

Git 用于维护源代码的历史版本和当前版本。在项目中，开发人员拥有存储在中央服务器上的所有代码版本的副本。

Git 允许开发人员执行以下操作：

- 跟踪更改、谁进行了更改以及何时进行更改
- 回滚/恢复更改
- 允许多个开发人员协调并在同一文件上工作
- 在远程和本地级别维护文件副本

下图描绘了 Git 作为团队中的 VCS，开发人员可以同时在同一文件上工作并跟踪谁进行了更改。这里，F1、F2 和 F3 是文件名。

![](img/cc4299656808e62a294f1843a1e18e72_42_0.png)

图 2.1：团队中的 Git 场景

