
(B) `mystery("pig", ["cat", "pig", "snake"])`

(C) `mystery("pig", ["cat", "pig", "pig"])`

(D) `mystery("pig", ["pig", "elephant", "Cookie"])`

## 115

在下面的过程 "mystery" 中，参数 `number` 是正整数。

![Images](img/p0311-01.jpg)

以下哪项最能描述运行过程 "mystery" 的结果？

(A) 如果数字是偶数，过程将返回 0；如果数字是奇数，则返回 -1。

(B) 如果数字大于 3，过程将返回 -1；如果数字小于 3，则返回 0。

(C) 过程将对所有大于 0 的数字返回 -1。

(D) 该程序不会返回数字，因为它陷入了无限循环。

## 116

当参数 (A, B) 为布尔值时，下面的过程 "mystery" 将返回什么？

![Images](img/p0311-02.jpg)

(A) 无论 A 或 B 的值如何，输出均为 TRUE。

(B) 无论 A 或 B 的值如何，输出均为 FALSE。

(C) 如果输入 A 为 TRUE 则输出为 TRUE；否则为 FALSE。

(D) 如果输入 B 为 TRUE 则输出为 TRUE；否则为 FALSE。

## 117

当参数 (A, B) 为布尔值时，下面的过程 "mystery" 将返回什么？

![Images](img/p0312-01.jpg)

(A) 无论 A 或 B 的值如何，输出均为 TRUE。

(B) 无论 A 或 B 的值如何，输出均为 FALSE。

(C) 如果输入 A 为 TRUE 则输出为 TRUE；否则为 FALSE。

(D) 如果输入 B 为 TRUE 则输出为 TRUE；否则为 FALSE。

## 答案解析

### 59

**(A)** 过程 "mystery" 接收数字 4。在第 3 行，`num MOD 2` 将等于 0。因此将执行 "If" 语句并返回字符串 "even"。由于 "If" 语句为真，附带的 ELSE 语句将被跳过，程序结束。

### 60

**(B)** 过程 "mystery" 接收数字 7 作为参数，由过程称为 `num`。在第 3 行，`num MOD 2` 将等于 1。因此 "If" 语句中的条件将评估为 false，程序序列将跳到第 7 行的 ELSE 语句。第 9 行将返回字符串 "odd"。

### 61

**(B)**

| **num** | **Is num < 2?** | **Return** |
| --- | --- | --- |
| 3 | False |   |
| 2 | False |   |
| 1 | True |   |
|   |   | 1 |

### 62

**(D)** 在此过程中，`num` 永远不会小于 2。因此循环永远不会退出。

| **num** | **Is num < 2?** | **Return** |
| --- | --- | --- |
| 3 | False |   |
| 4 | False |   |
| 5 | True |   |
| 6 |   |   |

由于 `num` 持续变大，条件 `num < 2` 永远不会为真。

### 63

**(C)** 过程可以有多个参数。在这种情况下，过程 "mystery" 按顺序接收两个名为 `a` 和 `b` 的参数。

![Images](img/t0314-01.jpg)

### 64

**(D)**

![Images](img/t0314-02.jpg)

### 65

**(D)**

![Images](img/t0314-03.jpg)

### 66

**(A)** 注意 8 MOD 2 = 0。如果 `b` 是奇数，此过程将返回 1。如果 `b` 是偶数，将返回 0。

| **a** | **b** | **Return** |
| --- | --- | --- |
| 5 |   |   |
| 8 |   |   |
|   | 0 | 0 |

### 67

**(C)**

| **a** | **b** | **Return** |
| --- | --- | --- |
| 5 |   |   |
| 2 |   |   |
|   | 2 | 2 |

### 68

**(C)**

| **num** | **Is num < 3?** | **Return** |
| --- | --- | --- |
| 3 | No |   |
| 2 | Yes |   |
|   |   | 2 |

### 69

**(D)**

| **num** | **Is num < 5?** | **Return** |
| --- | --- | --- |
| 3 | No |   |
| 4 | No |   |
| 5 | No |   |
| 6 | Yes |   |
|   |   | 6 |

### 70

**(B)** 过程 "mystery" 按发送顺序设置参数。在这种情况下，`a` 等于 5 且 `b` 等于 2。注意 5 MOD 2 = 1。

## 71

**(C)** 过程 "mystery" 按发送顺序设置参数。在这种情况下，`a` 等于 2 且 `b` 等于 5。注意 2 MOD 5 = 2。

## 72

**(C)** 名为 `list` 的数据结构包含具有以下索引的数字。

![Images](img/t0315-01.jpg)

索引从 1 开始，而不是 0。

程序随后显示使用参数 `list` 调用过程 "mystery" 的结果。过程是一种抽象。

`FOR EACH` 循环将从索引 1 开始遍历列表直到列表末尾。

| sum = 0 |
| --- |
| sum = sum + 11 = 0 + 11 = 11 |
| sum = sum + 35 = 11 + 35 = 46 |
| sum = sum + 6 = 46 + 6 = 52 |
| sum = sum + 0 = 52 + 0 = 52 |

`LENGTH(list)` 命令等于列表的大小。在这种情况下，`LENGTH(list)` = `4`。

过程的最后一行返回 `sum/LENGTH(list)` = `52/4` = `13`。

## 73

**(D)** 名为 `list` 的数据结构包含具有以下索引的数字。

![Images](img/t0316-01.jpg)

程序随后显示使用参数 `list` 调用过程 "mystery" 的结果。过程是一种抽象。

# 算法与数据结构习题解析

## 最大值/最小值查找算法

当尝试查找最大值或最小值时，应将初始数字设置为列表中的第一个元素，而不是 0。

```
max = list(1) = 11
```

`FOR EACH` 循环将从索引 1 开始遍历列表直到末尾。

| 条件判断 | 结果 |
| --- | --- |
| If(11 > max) | no |
| If(35 > max) | yes, max = 35 |
| If(6 > max) | no |

**返回值：35**

---

## 第 74 题 (A)

此问题涉及两个数据结构。

![Images](img/t0316-02.jpg)

| list2 |
| --- |
| index |

`FOR EACH` 循环将从索引 1 开始遍历列表直到末尾。

如果项目 MOD 2 = 0（偶数），该项目将被追加到 `list2` 末尾。

| 条件判断 | 结果 |
| --- | --- |
| If(1 MOD 2 = 0) | false |
| If(1 MOD 2 = 0) | false |
| If(35 MOD 2 = 0) | false |
| If(6 MOD 2 = 0) | true, list2(6) |
| If(76 MOD 2 = 0) | true, list2(6, 76) |
| If(4 MOD 2 = 0) | true, list2(6, 76, 4) |
| If(98 MOD 2 = 0) | true, list2(6, 76, 4, 98) |

过程运行后，`list2` 将包含以下元素：[6, 76, 4, 98]。

---

## 第 75 题 (B)

名为 `list` 的数据结构包含以下索引的数字。

![Images](img/t0317-01.jpg)

- **第 2 行**：显示对过程 `mystery` 的调用，参数为列表 `[11, 35, 6, 1]`。

- **第 6 行**：`sum = list(1)` → `sum = 11`

- **第 7 行**：`count = 1`

- **第 8 行**：抽象 `LENGTH(list)` 等于列表大小，此处为 4。`n = 4`

- **第 9 行**：`REPEAT` 循环将迭代 4 次。

| 迭代 | 操作 | 结果 |
| --- | --- | --- |
| 1st pass | `sum = sum + list(1)`<br>`count = count + 1` | `sum = 11 + 11 = 22`<br>`count = 1 + 1 = 2` |
| 2nd pass | `sum = sum + list(2)`<br>`count = count + 1` | `sum = 22 + 35 = 57`<br>`count = 2 + 1 = 3` |
| 3rd pass | `sum = sum + list(3)`<br>`count = count + 1` | `sum = 57 + 6 = 63`<br>`count = 3 + 1 = 4` |
| 4th pass | `sum = sum + list(3)`<br>`count = count + 1` | `sum = 63 + 2 = 65`<br>`count = 4 + 1 = 5` |

**返回值**：`sum/count = 65/5 = 13`

> **注意**：此过程不返回平均值。要返回平均值，`sum` 应初始化为 0 而非列表第一个元素。且应除以列表大小（4），而非 5。

---

## 第 76 题 (B)

此问题涉及两个数据结构。

![Images](img/t0317-02.jpg)

| list2 |
| --- |
| index |

`FOR EACH` 循环将从索引 1 开始遍历列表直到末尾。

如果项目 MOD 2 = 1（奇数），该项目将被追加到 `list2` 末尾。

| 条件判断 | 结果 |
| --- | --- |
| If(1 MOD 2 = 1) | true, list2(1) |
| If(1 MOD 2 = 1) | true, list2(1, 1) |
| If(35 MOD 2 = 1) | true, list2(1, 1, 35) |
| If(6 MOD 2 = 0) | false |
| If(76 MOD 2 = 0) | false |
| If(4 MOD 2 = 0) | false |
| If(98 MOD 2 = 0) | false |

过程运行后，`list2` 将包含以下元素：[1, 1, 35]。

---

## 第 77 题 (D)

此问题涉及两个数据结构。

![Images](img/t0318-01.jpg)

| list2 |
| --- |
| index |

`FOR EACH` 循环将从索引 1 开始遍历列表直到末尾。

如果项目 MOD 2 = 0（偶数）**且**项目 MOD = 1（奇数），该项目将被追加到 `list2` 末尾。因为没有数字能同时是偶数和奇数，所以 `list2` 将不会追加任何元素。

最终 `list2` 包含 `[ ]`。

---

## 第 78 题 (C)

此问题涉及两个数据结构。

![Images](img/t0318-02.jpg)

| list2 |
| --- |
| index |

`FOR EACH` 循环将从索引 1 开始遍历列表直到末尾。

如果项目 MOD 2 = 0（偶数）**或**项目 MOD = 1（奇数），该项目将被追加到 `list2` 末尾。因为数字总是偶数或奇数，所以 `list2` 将包含所有数字。

最终 `list2` 包含 `[1, 1, 35, 6, 76, 4, 98]`。

---

## 第 79 题 (D)

此问题涉及一个数据结构。

![Images](img/t0319-01.jpg)

`max = 1`

`FOR EACH` 循环将从索引 1 开始遍历列表直到末尾。

| 条件判断 | 结果 |
| --- | --- |
| If(1 > max) | false, max = 1 |
| If(1 > max) | false |
| If(35 > max) | true, max = 35 |
| If(6 > max) | false |
| If(76 > max) | true, max = 76 |
| If(4 > max) | false |
| If(98 > max) | true, max = 98 |

程序将显示 **98**。

---

## 第 80 题 (A)

虽然程序显示正确答案，但并非在所有情况下都有效。正确格式是将 `max` 设置为列表第一个元素，而不是 0。如果测试用例全为负数，程序将包含逻辑错误。

| 条件判断 | 结果 |
| --- | --- |
| 1 > 0 true | max = 1 |
| 1 > 1 false | no change |
| 35 > 1 true | max = 35 |
| 6 > 35 false | no change |
| 76 > 35 true | max = 76 |
| 4 > 76 false | no change |
| 98 > 76 true | max = 98 |

程序将显示 **98**。

---

## 第 81 题 (A)

**当 `p = 0` 时：**

![Images](img/f0320-01.jpg)

**当 `p = 1` 时：**

![Images](img/f0320-02.jpg)

**当 `p = 3` 时：**

![Images](img/f0320-03.jpg)

**当 `p = 4` 时：**

![Images](img/f0320-04.jpg)

**当 `p = 5` 时：**

![Images](img/f0321-01.jpg)

如果 `p` 大于 5，机器人将重复上述模式。

---

## 第 82 题 (D)

如果机器人向左旋转然后向前移动，将移出网格并导致错误。

**当 `p = 1` 时：**

![Images](img/f0321-02.jpg)

---

## 第 83 题 (B)

**当 `p = 1` 时：**

![Images](img/f0321-03.jpg)

**当 `p = 2` 时：**

![Images](img/f0321-04.jpg)

**当 `p = 3` 时：**

![Images](img/f0322-01.jpg)

**当 `p = 4` 时：**

![Images](img/f0322-02.jpg)

---

## 第 84 题 (D)

程序旨在返回最大数字但返回了最小数字。要按预期工作，条件应为 `item > result`。从 `result = 0` 开始可避免负数问题。

| Result | List | Is Item Less than Result? |
| --- | --- | --- |
| 0 | 1 | False |
| −2 | −2 | True |
| −2 | 3 | False |
| −2 | 0 | False |
| −7 | −7 | True |

---

## 第 85 题 (A)

程序旨在返回列表中最小数字；`result` 在循环执行前正确设置为列表第一项。

| Result | List | Is Item Less than Result? |
| --- | --- | --- |
| 1 |   |   |
| 1 | 1 | False |
| −2 | −2 | True |
| −2 | 3 | False |
| −2 | 10 | False |
| −7 | −7 | True |

---

## 第 86 题 (A)

程序旨在返回列表中最小数字；循环执行前 `result` 设置为 0。

![Images](img/t0323-01.jpg)

---

## 第 87 题 (C)

旨在返回列表中最大数字；循环执行前 `result` 设置为列表第一个元素。若 `result` 设为 0，程序将无法按预期工作。

| Result | Item | Is Item Greater than Result? |
| --- | --- | --- |
| −3 |   |   |
| −3 | −3 | False |
| −3 | −5 | False |
| −3 | −200 | False |
| −1 | −1 | True |

---

## 第 88 题 (D)

`Rotate left` 使机器人逆时针旋转 90 度。旋转后，机器人向前移动一格。

**步骤 1**：机器人向左旋转 6 次。

**起始状态：**

![Images](img/f0323-01.jpg)

**第 1 次左旋：**

![Images](img/f0324-01.jpg)

**第 2 次左旋：**

![Images](img/f0324-02.jpg)

**第 3 次左旋：**

![Images](img/f0324-03.jpg)

**第 4 次左旋：**

![Images](img/f0324-04.jpg)

**第 5 次左旋：**
