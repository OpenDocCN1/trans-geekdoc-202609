
被除数是 4，除数是 3。3 可以进 4 一次。在顶部写 1，并乘以除数：1 乘以 3 等于 3。然后用 4 减去 3。得到 4 减 3 等于 1，即为余数。余数 1 即为答案。

![image](img/common.jpg)

### 示例七

`8 MOD 2`

![Images](img/f0190-02.jpg)

被除数是 8，除数是 2。2 可以进 8 四次。在顶部写 4，并乘以除数：4 乘以 2 等于 8。然后用 8 减去 8。得到 8 减 8 等于 0，即为余数。余数 0 即为答案。

![image](img/common.jpg)

### 示例八

`6 MOD 2`

![Images](img/f0190-03.jpg)

被除数是 6，除数是 2。2 可以进 6 三次。在顶部写 3，并乘以除数：2 乘以 3 等于 6。然后用 6 减去 6。得到 6 减 6 等于 0，即为余数。余数 0 即为答案。

![image](img/common.jpg)

### 示例九

`5 MOD 2`

![Images](img/f0190-04.jpg)

被除数是 5，除数是 2。2 可以进 5 两次。在顶部写 2，并乘以除数：2 乘以 2 等于 4。然后用 5 减去 4。得到 5 减 4 等于 1，即为余数。余数 1 即为答案。

![image](img/common.jpg)

### 示例十

`13 MOD 2`

![Images](img/f0191-01.jpg)

被除数是 13，除数是 2。2 可以进 13 六次。在顶部写 6，并乘以除数：6 乘以 2 等于 12。然后用 13 减去 12。得到 13 减 12 等于 1，即为余数。余数 1 即为答案。

![image](img/common.jpg)

### 示例十一

`4 MOD 6`

![Images](img/f0191-02.jpg)

被除数是 4，除数是 6。6 可以进 4 零次。在顶部写 0，并乘以除数：0 乘以 4 等于 0。然后用 4 减去 0。得到 4 减 0 等于 4，即为余数。余数 4 即为答案。

![image](img/common.jpg)

### 示例十二

`3 MOD 4`

![Images](img/f0191-03.jpg)

被除数是 3，除数是 4。4 可以进 3 零次。在顶部写 0，并乘以除数：0 乘以 4 等于 0。然后用 3 减去 0。得到 3 减 0 等于 3，即为余数。余数 3 即为答案。

## 赋值运算符

![Images](img/p0191-01.jpg)

### 注意

首先对表达式求值。然后将变量设置为该表达式计算出的值。

![image](img/common.jpg)

### 示例十三

表达式求值后 `a` 的值是多少？

| `a ← 3` | | `a = 3` |
| --- | --- | --- |

`a` 等于 3。

![image](img/common.jpg)

### 示例十四

表达式求值后 `a` 的值是多少？

| ![Images](img/p0192-01.jpg) | | `a = 26` |
| --- | --- | --- |

首先将 4 乘以 5 得到 20，然后加上 6 得到 26。

![image](img/common.jpg)

### 示例十五

表达式求值后 `a` 的值是多少？

| ![Images](img/p0192-02.jpg) | | `a = 0` |
| --- | --- | --- |

因为 2 可以进 26 共 13 次，且 26 减 26 等于 0，所以 `a` 等于 0。

![image](img/common.jpg)

### 示例十六

表达式求值后 `a` 的值是多少？

| ![Images](img/p0192-03.jpg) | | `a = 1` |
| --- | --- | --- |

因为 2 可以进 17 共 8 次，且 16 减 17 等于 1（注：原文逻辑为 17-16=1），`a` 等于 1。

![image](img/common.jpg)

### 示例十七

表达式求值后 `a` 的值是多少？

| ![Images](img/p0192-04.jpg) | | `a = 0` |
| --- | --- | --- |

因为 1 可以进 33 共 33 次，且 33 减 33 等于 0，所以 `a` 等于 0。

## 列表

列表是一种数据抽象，它通过给一组数据命名而不引用表示的具体细节，降低了程序的复杂度。列表的元素通过索引访问，索引从 1 开始。许多编程语言从索引 0 开始，但 College Board 伪代码语言从索引 1 开始。

正如 AP 参考指南（在 AP 考试中提供给学生）所示，创建列表的正确格式如下：

![Images](img/t0193-01.jpg)

![image](img/common.jpg)

### 示例十八

![Images](img/p0193-01.jpg)

元素是列表中的单个值，并被分配了一个唯一的索引。对于所有列表操作，如果列表索引小于 1 或大于列表的长度，则会产生错误消息，程序将终止。

![image](img/common.jpg)

### 示例十九

```
namesOfMyDogs ← [ “Waffles”, “Novack the 3rd”, “Benji”]
newList = namesOfMyDogs
a ← newList [0]
```

这段代码会导致错误。此索引将越界，因为 `newList` 只有索引 1、2 和 3。

![Images](img/p0194-01.jpg)

这段代码会导致错误。此索引将越界，因为 `newList` 只有索引 1、2 和 3。

## 显示运算符

![Images](img/t0194-01.jpg)

![image](img/common.jpg)

### 示例二十

以下程序将显示什么？

```
a ← 3
b ← 17
a ← b
DISPLAY(a)
```

如下图所示，在 `a` 被打印之前，所有变量都必须初始化。注意 `a` 初始化为值 3，`b` 设置为 17。下一步将 `a` 的值设置为 `b` 的值，即 17。

![Images](img/p0194-01a.jpg)

**答案：17**

![image](img/common.jpg)

### 示例二十一

以下程序将显示什么？

```
a ← 3
b ← 14
c ← 5
a ← c
b ← a
DISPLAY(a)
DISPLAY(b)
DISPLAY(c)
```

**答案：5 5 5**

| *a* | *b* | *c* |
| --- | --- | --- |
| ~~3~~ | ~~14~~ | 5 |
| 5 | 5 |   |

![image](img/common.jpg)

### 示例二十二

以下程序将显示什么？

![Images](img/p0195-01.jpg)

| *a* | *b* | DISPLAY |
| --- | --- | --- |
| 5 + 8 = 13 | 4 MOD 5 = 4 | 17 |

**答案：17**

## 输入运算符

| 文本：`INPUT()` 代码块：`INPUT` | 接受来自用户的值并返回它。 |
| --- | --- |

![image](img/common.jpg)

### 示例二十三

如果 `INPUT` 函数读取一个偶数（如 4），以下程序将显示什么？

```
a ← INPUT()
a ← a MOD 2
DISPLAY(a)
```

对于 4（或任何偶数）除以 2，余数将始终为 0。

**答案：0**

![image](img/common.jpg)

### 示例二十四

如果 `INPUT` 函数读取一个奇数（如 5），以下程序将显示什么？

```
a ← INPUT()
a ← a MOD 2
DISPLAY(a)
```

奇数除以 2 的余数始终为 1。

**答案：1**

## 关系和布尔运算符

| 文本和代码块： | 关系运算符 `=`、`≠`、`>`、`<`、`≥` 和 `≤` 用于测试两个变量、表达式或值之间的关系。 |
| --- | --- |
| `a = b` | 如果 `a` 和 `b` 相等，`a = b` 的值为 true；否则为 false。例如，当 `a` 为 3 且 `b` 为 3 时，`a = b` 的值为 true。然而，当 `a` 为 3 且 `b` 为 5 时，`a = b` 的值为 false。 |
| `a ≠ b` | 如果 `a` 和 `b` 不相等，`a ≠ b` 的值为 true；否则为 false。 |
| `a > b` | 如果 `a` 大于 `b`，`a > b` 的值为 true；否则为 false。 |
| `a < b` | 如果 `a` 小于 `b`，`a < b` 的值为 true；否则为 false。 |
| `a ≥ b` | 如果 `a` 大于或等于 `b`，`a ≥ b` 的值为 true；否则为 false。 |
| `a ≤ b` | 如果 `a` 小于或等于 `b`，`a ≤ b` 的值为 true；否则为 false。 |

![image](img/common.jpg)

### 示例二十五

以下程序将显示什么？

![Images](img/p0196-02.jpg)

| ***a*** | *b* | DISPLAY |
| --- | --- | --- |
| 3 | 3 MOD 5 = 3 | true |

`a` 初始化为 3；`b` 初始化为 3 除以 5 的余数。因为 3 等于 3，程序将显示 true。

**答案：True**

![image](img/common.jpg)

### 示例二十六

以下程序将显示什么？

```
a ← 4 * (3 + 6)
b ← 4 * 3 + 6
DISPLAY (a ≤ b)
```

| *a* | *b* | DISPLAY |
| --- | --- | --- |
| 36 | 18 | false |

根据运算顺序，由于括号的存在加法先发生，`a` 将初始化为 36。注意 `b` 将初始化为 18，因为根据运算符优先级乘法先发生。因为 36 不小于或等于 18，该程序显示 false。

**答案：False**

### 数值过程

| 文本：`RANDOM(a, b)` 代码块：![Images](img/p0197-02.jpg) | 计算结果为从 `a` 到 `b` 的随机整数，包括 `a` 和 `b`。例如，`RANDOM(1, 3)` 可能计算结果为 1、2 或 3。 |
| --- | --- |

![image](img/common.jpg)

### 示例二十七

如果执行下面的代码多次，预期显示“true”的百分比是多少？

![Images](img/p0197-03.jpg)

`RANDOM` 可以选取 1 或 2。选中 1 的概率是 1/2 或 50%。

**答案：50%**

![image](img/common.jpg)

### 示例二十八

如果执行下面的代码多次，预期显示“false”的百分比是多少？

![Images](img/p0197-04.jpg)

数字 1、2、3 和 4 都是可能的选择。选中 3 的概率是 1/4 或 25%。未选中 3 的概率是 3/4，即 75%。

**答案：75%**

![image](img/common.jpg)

### 示例二十九

如果执行下面的代码多次，预期显示“true”的百分比是多少？

![Images](img/p0198-01.jpg)

数字 1、2、3、4、5、6、7、8、9 和 10 都可以被选中。因为 `a ≤ 3` 包括 1、2 和 3，答案是 3/10 = 30%。

**答案：30%**

### 布尔表

| **指令** | **解释** |
| --- | --- |
| 文本：`NOT condition` 代码块：![Images](img/p0198-02.jpg) | 如果条件为 false，则计算结果为“true”；否则计算结果为“false”。 |
| 文本：`condition1 AND condition2` 代码块：![Images](img/p0198-03.jpg) | 如果 condition1 和 condition2 都为 true，则计算结果为“true”；否则计算结果为“false”。 |
| 文本：`condition1 OR condition2` 代码块：![Images](img/p0198-04.jpg) | 如果 condition1 为 true 或 condition2 为 true，或两者都为 true，则计算结果为“true”；否则计算结果为“false”。 |

布尔值是一种只有两个可能值的数据类型：true 或 false。在你的 AP 考试中，你将接受三个布尔运算符的测试。这些运算符是 `AND`、`OR` 和 `NOT`。

如果你能用非计算机科学术语来思考，布尔问题就会变得简单。例如，如果你是个挑食者，只有当你同时拥有两种最爱的食物（披萨 `AND` 山药）时才会开心，问问自己在以下条件下你是否开心。

| 对……满意 | 披萨 `AND` 山药 = 开心 |
| --- | --- |
|   | True `AND` True = True |
| 对……满意 | 披萨 `AND` 花生 = 不开心 |
|   | True `AND` False = False |
| 对……满意 | 豌豆 `AND` 花生 = 不开心 |
|   | False `AND` False = False |
| 对……满意 | 金枪鱼 `AND` 披萨 = 不开心 |
|   | False `AND` True = False |
| 实际上 |   |
| 对……满意 | 金枪鱼 `AND` 世界上任何东西 = 不开心 |
|   | False `AND` 世界上任何东西 = False |

现在假设你不是挑食者，只要拥有最爱的食物中的一种（披萨 `OR` 山药）就会开心。问问自己在以下条件下你是否开心。

| 对……满意 | 披萨 `OR` 山药 = 开心 |
| --- | --- |
|   | True `OR` True = True |
| 对……满意 | 披萨 `OR` 花生 = 开心 |
|   | True `OR` False = True |
| 对……满意 | 豌豆 `OR` 花生 = 不开心 |
|   | False `OR` False = False |
| 对……满意 | 金枪鱼 `OR` 披萨 = 开心 |
|   | False `OR` True = True |
| 实际上 |   |
| 对……满意 | 披萨 `OR` 世界上任何东西 = 开心 |
|   | True `OR` 世界上任何东西 = True |

运算符 `NOT` 会反转布尔值。

`NOT` 开心 = 不开心

`NOT` True = False

`NOT` 不开心 = 开心

`NOT` False = True

上述结果总结在下面的布尔表中。

![Images](img/t0199-01.jpg)

## 示例三十至三十七

注意，示例三十到三十七各自展示了 AP 考试询问布尔问题的两种可能格式之一。这与布尔表中显示的信息相同，只是呈现方式不同。

![image](img/common.jpg)

### 示例三十

![Images](img/f0200-01.jpg)

![image](img/common.jpg)

### 示例三十一

![Images](img/f0200-02.jpg)

![image](img/common.jpg)

### 示例三十二

![Images](img/f0200-03.jpg)

![image](img/common.jpg)

### 示例三十三

![Images](img/f0200-04.jpg)

![image](img/common.jpg)

### 示例三十四

![Images](img/f0201-01.jpg)

![image](img/common.jpg)

### 示例三十五

![Images](img/f0201-02.jpg)

![image](img/common.jpg)

### 示例三十六

![Images](img/f0201-03.jpg)

![image](img/common.jpg)

### 示例三十七

![Images](img/f0201-04.jpg)

## 机器人

| 指令 | 说明 |
| :--- | :--- |
| **Robot** | |
| 如果机器人尝试移动到一个非开放的方格或超出网格边缘，机器人将停留在当前位置，程序将终止。 | |
| 文本：`MOVE_FORWARD()`<br>块：![Images](img/p0202-01.jpg) | 机器朝其面对的方向向前移动一格。 |
| 文本：`ROTATE_LEFT()`<br>块：![Images](img/p0202-02.jpg) | 机器人原地逆时针旋转 90 度（即原地左转）。 |
| 文本：`ROTATE_RIGHT()`<br>块：![Images](img/p0202-03.jpg) | 机器人原地顺时针旋转 90 度（即原地右转）。 |
| 文本：`CAN_MOVE(direction)`<br>块：![Images](img/p0202-04.jpg) | 如果机器人面对方向相对的某个方向上有一个开放的方格，则求值为 `"true"`；否则求值为 `"false"`。`direction` 的值可以是 `left`、`right`、`forward` 或 `backward`。 |

AP 考试中的机器人同时具有方向和位置。方向可以是朝左、朝右、朝上或朝下。机器人的位置是机器人当前所在的网格行和列。

如果要求机器人移出网格，机器人将结束任何程序。

机器人可以通过使用下表中列出的四个抽象来改变其方向和位置。
