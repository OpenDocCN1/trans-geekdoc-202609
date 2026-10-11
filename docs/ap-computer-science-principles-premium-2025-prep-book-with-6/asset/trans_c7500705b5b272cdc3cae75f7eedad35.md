

## 18. 神秘过程分析

考虑以下名为 `mystery` 的过程，旨在显示数字 `target` 在列表中出现的次数。

以下哪项最能描述该过程的行为？

![Images](images/f0013-02.jpg)

**选择两个答案。**

(A) 如果目标不在列表中，程序正确显示计数。

(B) 程序从不正确显示 count 的正确值。

(C) 如果目标在列表中出现一次且也出现在列表末尾，程序正确显示计数。

(D) 程序总是正确显示 count 的正确值。

## 19. 合并列表上的二分查找

两个列表 `list1` 和 `list2` 包含 Lake Brantley 高中的唯一八位数学生 ID。学校管理员想要创建一个列表，以便可以使用二分查搜索该列表。

以下抽象可用于创建新的可搜索列表。

| **抽象** | **解释** |
| --- | --- |
| `Sort(list)` | 将列表按从低到高的数字排序 |
| `Combine(list1, list2)` | 通过合并 `list1` 的元素后跟 `list2` 的元素来创建一个新列表。 |
| `BinarySearch(list, value)` | 使用二分查找返回 `value` 在列表中的索引。如果值不在列表中，此抽象将返回 −1。 |

以下哪个代码段将正确使用二分查找搜索值？

(A)
```
list1 ← Sort(list1)
list2 ← Sort(list2)
resultList ← Combine(list1, list2)
BinarySearch(resultList, value)
```

(B)
```
resultList ← Combine(list1, list2)
BinarySearch(resultList, value)
```

(C)
```
resultList ← Combine(list1, list2)
resultList ← Sort(resultList)
BinarySearch(resultList, value)
```

(D)
```
BinarySearch(list1, value)
BinarySearch(list2, value)
```

## 20. 机器人移动概率

下面的问题使用网格方格中的机器人。机器人表示为三角形，最初面向网格顶部。

![Images](images/f0015-01.jpg)

以下哪些代码会使机器人有 1% 的概率向前移动一格？

**选择两个答案。**

(A)
```
IF(RANDOM(1, 100) = 4)
MOVE_FORWARD()
```

(B)
```
IF(RANDOM(0, 100) = 4)
MOVE_FORWARD()
```

(C)
```
IF(RANDOM(1, 100) < 2)
MOVE_FORWARD()
```

(D)
```
IF(RANDOM(1, 100) ≤ 2)
MOVE_FORWARD()
```

## 21. 二进制转十进制转换

在最低抽象级别之一，数字数据以二进制表示，即数字零和一的组合。

二进制数 “1001001” 转换为十进制 (DEC) 等于什么数字？

(A) 37

(B) 45

(C) 73

(D) 86

## 22. 二分查找迭代次数

使用二分查找，查找字母 *w* 需要多少次迭代？
`str ← [a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z]`

(A) 2

(B) 3

(C) 23

(D) 24

## 23. 线性查找迭代次数

使用线性查找，查找字母 *x* 需要多少次迭代？
`str ← [a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z]`

(A) 3

(B) 4

(C) 23

(D) 24

## 24. 流程图算法输出

流程图是以可视化方式表示算法的方法。下面的流程图使用以下构建块。

| **块** | **解释** |
| --- | --- |
| ![Images](images/f0016-01.jpg) | 算法的开始或结束 |
| ![Images](images/f0016-02.jpg) | 一个或多个处理步骤，例如给变量赋值的语句 |
| ![Images](images/f0016-03.jpg) | 条件或决策步骤，如果条件为真，执行流程转向标记为 `true` 的一边，否则转向标记为 `false` 的一边 |
| ![Images](images/f0016-04.jpg) | 显示消息 |

下面的算法将显示什么？

![Images](images/f0016-05.jpg)

(A) 6

(B) 8

(C) 10

(D) 由于无限循环，不显示任何数字

## 25. 算法构建块：选择

排序、选择和迭代是算法的构建块。以下哪项被视为选择？

(A) 按照语句给出的顺序应用算法的每一步

(B) 使用布尔条件确定算法的哪一部分被使用

(C) 重复算法的一部分，直到满足条件或达到指定的次数

(D) 决定使用高级计算语言来评估算法

## 26. 搜索未排序列表

如果你的算法需要搜索一个未排序的单词列表，你会使用哪种搜索类型？

(A) 线性搜索

(B) 二分搜索

(C) 冒泡排序

(D) 插入排序

## 27. 疾病诊断代码段

下面的代码段是一个测试程序，旨在根据用户输入的 `fatigue_present` 和 `has_cough` 诊断幼儿患有的疾病。

![Images](images/f0017-01.jpg)

如果所有变量的值均为 `TRUE`，运行显示的代码段后显示什么结果？

(A) `Flu`

(B) `Cold`

(C) `Flu Healthy`

(D) `Flu Cold Healthy`

## 28. 数字数据表示权衡

以下哪项权衡在将信息表示为数字数据时是正确的？

I. 模拟信号必须经过采样并转换为数字，然后作为位存储在数字设备中。

II. 读取数据和更新数据具有不同的存储要求。

III. 有损数据压缩以只能重建原始数据的近似值为代价，减少了存储或传输的位数。

(A) 仅 I 和 II

(B) 仅 II 和 III

(C) 仅 I 和 III

(D) I、II 和 III

## 29. 代码段输出范围

运行此代码段后，可能显示的值是什么？

![Images](images/f0018-01.jpg)

(A) −11

(B) −5

(C) 5

(D) 20

## 30. 容错网络路由

这是一个通过容错冗余互联网连接的设备网络。

![Images](images/f0018-02.jpg)

设备 C 必须与至少多少个其他设备连接才能与 D 通信？

(A) 1

(B) 2

(C) 3

(D) 4

## 31. 循环输出序列

以下代码段将显示什么？

![Images](images/f0018-03.jpg)

(A) 1 4 7 10 13

(B) 35

(C) 13 10 7 4 1

(D) 1 4 7 1 4 7

## 32. 嵌套循环输出

以下代码段将显示什么？

![Images](images/f0019-01.jpg)

(A) 由于错误，不会显示任何内容。

(B) 3

(C) 6

(D) 11

## 33. 算法输出计算

运行以下算法后显示什么？

![Images](images/f0019-02.jpg)

(A) −98

(B) −4

(C) 0

(D) 76

## 34. 算法输出计算

运行以下算法后显示什么？

![Images](images/f0019-03.jpg)

(A) −98

(B) −76

(C) −1

(D) 0

## 35. 算法输出计算

运行以下算法后显示什么？

![Images](images/f0020-01.jpg)

(A) −98

(B) −76

(C) −1

(D) 0

## 36. 求偶数和过程

过程 `getTotalEven` 旨在显示列表中所有偶数的和。以下哪个过程将正确显示列表中偶数的总和？

(A)
![Images](images/f0020-02.jpg)

(B)
![Images](images/f0020-03.jpg)

(C)
![Images](images/f0021-01.jpg)

(D)
![Images](images/f0021-02.jpg)

## 37. 机器人着陆概率

机器人落在星星上的百分比几率是多少？

![Images](images/f0021-03.jpg)
![Images](images/f0021-04.jpg)

(A) 0%

(B) 25%

(C) 50%

(D) 100%

## 38. 算法输出计算

运行以下算法后显示什么？

![Images](images/f0022-01.jpg)

(A) 35

(B) 43

(C) 68

(D) 73

## 39. 机器人导航至目标

以下问题使用网格方格中的机器人。机器人表示为三角形，最初位于左下角的方格并面向右侧。

以下哪个代码段将机器人放置在灰色目标位置？

![Images](images/f0022-02.jpg)
![Images](images/p0022-01.jpg)

(A)
```
MoveForward(4)
TurnRight(1)
MoveForward(4)
TurnRight(1)
MoveForward(1)
TurnRight(1)
MoveForward(1)
```

(B)
```
MoveForward(4)
TurnRight(3)
MoveForward(4)
TurnRight(1)
```

