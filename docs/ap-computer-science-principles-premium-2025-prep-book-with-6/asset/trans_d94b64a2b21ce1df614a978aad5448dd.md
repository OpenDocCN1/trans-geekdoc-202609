

# 示例四十四

将上图所示的第一个数据结构交换到第二个数据结构中，成功的算法需要哪些步骤？

**步骤 1：** 创建一个临时变量，并用它来存储列表中第一个项目的值。

```
temp = animals[1]
```

![Images](images/f0219-02.jpg)

**步骤 2：** 用列表中的第三个项目替换列表中的第一个项目。

```
animals[1] = animals[3]
```

![Images](images/f0219-03.jpg)

**步骤 3：** 用存储在临时变量中的项目替换列表中的第三个项目。

```
animals[3] = temp
```

![Images](images/f0220-01.jpg)

## 搜索

可以执行几种不同类型的搜索。

### 线性搜索

线性搜索（或顺序搜索）是一种在列表中查找元素的算法。此搜索从列表的开头开始，按顺序检查列表的每个元素，直到找到匹配项或搜索完整个列表仍未找到该元素。线性搜索可用于**已排序列表**或**未排序列表**。

如果列表有 *n* 个元素，搜索次数的最坏情况将是 *n*。例如，如果列表有 50 个元素，最坏情况将是 50 次比较。然而，最好情况是你要找的元素在第一次比较时就被找到。

![Images](images/p0220-01.jpg)

**示例四十五**

![Images](images/p0220-02.jpg)

使用线性搜索，找到数字 11 需要多少次比较？

**答案：** 1 次比较。这是线性搜索的最好情况。

**示例四十六**

![Images](images/p0220-03.jpg)

使用线性搜索，找到数字 180 需要多少次比较？

![Images](images/f0221-01.jpg)

**答案：** 10 次比较。这是包含 10 个元素的列表进行线性搜索的最坏情况。

### 二分搜索

二分搜索是一种搜索算法，在每次比较后将需要搜索的元素数量减半。要使用二分搜索，**列表必须已排序**。此搜索将列表的中间元素与目标值进行比较。如果它们不相等，则排除目标不可能存在的那一半。

**示例四十七**

![Images](images/f0221-02.jpg)

二分搜索查找数字 300 需要哪些步骤？

**步骤 1：** 比较中间元素。

![Images](images/f0221-03.jpg)

由于 76 不等于目标值，且 300 不可能在列表的左侧，我们丢弃列表的左侧。

![Images](images/f0221-04.jpg)

**步骤 2：** 比较剩余数字的中间元素。

![Images](images/f0221-05.jpg)

由于 900 不等于目标值，且 300 不可能在列表的右侧，我们丢弃列表的右侧。

![Images](images/f0221-06.jpg)

**步骤 3：** 比较剩余数字的中间元素（向下取整）。

![Images](images/f0221-07.jpg)

## 算法与编程题

**说明：** 下面每个问题或未完成的陈述后面都有四个建议答案或补全选项。在每种情况下选择最佳的一项。

[1](#13_Chapter04.xhtml#ans4-1). 以下算法将显示什么？

![Images](images/f0222-01.jpg)

(A) 2 14 17
(B) 13 17 5
(C) 2 12 2
(D) 14 17 2

[2](#13_Chapter04.xhtml#ans4-2). 以下算法将显示什么？

![Images](images/f0222-02.jpg)

(A) 13
(B) 17
(C) 18
(D) 19

[3](#13_Chapter04.xhtml#ans4-3). 以下算法将显示什么？

![Images](images/f0223-01.jpg)

(A) 0
(B) 42
(C) 84
(D) 126

[4](#13_Chapter04.xhtml#ans4-4). 以下算法将显示什么？

![Images](images/f0222-02a.jpg)

(A) Milk
(B) Milk Cookies Soda
(C) put them in a bag and they stay crisp
(D) Milk Cookies Soda Chips put them in a bag so you know they stay crisp

[5](#13_Chapter04.xhtml#ans4-5). 程序运行后显示的值是什么？

![Images](images/f0224-01.jpg)

(A) a 8
(B) a 6
(C) 8 6
(D) 16 4

[6](#13_Chapter04.xhtml#ans4-6). 程序运行后显示的值是什么？

![Images](images/f0224-01.jpg)

(A) a 8
(B) a c
(C) 8 6
(D) 16 4

[7](#13_Chapter04.xhtml#ans4-7). 以下算法将显示什么？

![Images](images/f0224-02.jpg)

(A) 26
(B) 13
(C) 1
(D) 0

[8](#13_Chapter04.xhtml#ans4-8). 以下算法将显示什么？

![Images](images/f0224-03.jpg)

(A) 26
(B) 13
(C) 1
(D) 0

[9](#13_Chapter04.xhtml#ans4-9). 以下算法将显示什么？

![Images](images/f0225-01.jpg)

(A) 26
(B) 13
(C) 8
(D) 1

[10](#13_Chapter04.xhtml#ans4-10). 以下算法将显示什么？

![Images](images/f0225-02.jpg)

(A) 26
(B) 13
(C) 8
(D) 0

[11](#13_Chapter04.xhtml#ans4-11). 以下算法将显示什么？

![Images](images/f0225-03.jpg)

(A) 26
(B) 13
(C) 2
(D) 0

[12](#13_Chapter04.xhtml#ans4-12). 以下算法将显示什么？

![Images](images/f0225-04.jpg)

(A) 26
(B) 13
(C) 1
(D) 0

[13](#13_Chapter04.xhtml#ans4-13). 以下算法将显示什么？

![Images](images/f0226-01.jpg)

(A) 26
(B) 13
(C) 1
(D) 0

[14](#13_Chapter04.xhtml#ans4-14). 以下代码段将显示什么？

![Images](images/f0226-02.jpg)

(A) 13 5
(B) 5 13
(C) a b
(D) 13 13

[15](#13_Chapter04.xhtml#ans4-15). 如果此语句执行多次，大约有多少百分比的时间会显示 `true`？

![Images](images/f0226-03.jpg)

(A) 9%
(B) 10%
(C) 60%
(D) 100%

[16](#13_Chapter04.xhtml#ans4-16). 如果此语句执行多次，大约有多少百分比的时间会显示 `true`？

![Images](images/f0227-01.jpg)

(A) 10%
(B) 20%
(C) 60%
(D) 100%

[17](#13_Chapter04.xhtml#ans4-17). 如果此语句执行多次，大约有多少百分比的时间会显示 `true`？

![Images](images/f0227-02.jpg)

(A) 0%
(B) 20%
(C) 60%
(D) 100%

[18](#13_Chapter04.xhtml#ans4-18). 如果此语句执行多次，大约有多少百分比的时间会显示 `true`？

![Images](images/f0227-03.jpg)

(A) 0%
(B) 20%
(C) 60%
(D) 100%

[19](#13_Chapter04.xhtml#ans4-19). 如果此语句执行多次，大约有多少百分比的时间会显示 `true`？

![Images](images/f0227-04.jpg)

(A) 0%
(B) 20%
(C) 60%
(D) 100%

[20](#13_Chapter04.xhtml#ans4-20). 如果此语句执行多次，大约有多少百分比的时间会显示 `true`？

![Images](images/f0228-01.jpg)

(A) 9%
(B) 10%
(C) 60%
(D) 100%

[21](#13_Chapter04.xhtml#ans4-21). 如果此语句执行多次，大约有多少百分比的时间会显示 `true`？

![Images](images/f0228-02.jpg)

(A) 20%
(B) 40%
(C) 60%
(D) 100%

[22](#13_Chapter04.xhtml#ans4-22). 如果此语句执行多次，大约有多少百分比的时间会显示 `true`？

![Images](images/f0228-03.jpg)

(A) 0%
(B) 40%
(C) 60%
(D) 100%

[23](#13_Chapter04.xhtml#ans4-23). 此算法显示 `true` 的百分比是多少？

![Images](images/f0228-04.jpg)

(A) 0%
(B) 40%
(C) 60%
(D) 100%

[24](#13_Chapter04.xhtml#ans4-24). 下面的算法有 60% 的时间显示 `true`。

![Images](images/f0229-01.jpg)

什么可以替换缺失的条件，使代码段按预期工作？

(A) `x < 10`
(B) `x ≤ 10`
(C) `x > 10`
(D) `x ≥ 10`

[25](#13_Chapter04.xhtml#ans4-25). 算法运行后显示的值是什么？

![Images](images/f0229-02.jpg)

(A) 0
(B) 1
(C) 10
(D) 13

[26](#13_Chapter04.xhtml#ans4-26). 算法运行后显示的值是什么？

![Images](images/f0229-03.jpg)

(A) 0
(B) 1
(C) 10
(D) 12

[27](#13_Chapter04.xhtml#ans4-27). 算法运行后显示的值是什么？

![Images](images/f0230-01.jpg)

(A) 0
(B) 1
(C) 9
(D) 12

[28](#13_Chapter04.xhtml#ans4-28). 算法运行后显示的值是什么？

![Images](images/f0230-02.jpg)

(A) 0
(B) 1
(C) 10
(D) 由于无限循环，未显示任何内容。

