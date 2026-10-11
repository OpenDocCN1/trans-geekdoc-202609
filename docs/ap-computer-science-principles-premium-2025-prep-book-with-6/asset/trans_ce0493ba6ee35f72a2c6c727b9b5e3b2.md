
元素是列表中的单个值，并被分配了一个唯一的索引。对于所有列表操作，如果列表索引小于 1 或大于列表的长度，则会产生错误消息，程序将终止。

![image](images/common.jpg)

### 示例十九

```
namesOfMyDogs ← [ “Waffles”, “Novack the 3rd”, “Benji”]
newList = namesOfMyDogs
a ← newList [0]
```

这段代码会导致错误。此索引将越界，因为 `newList` 只有索引 1、2 和 3。

![Images](images/p0194-01.jpg)

这段代码会导致错误。此索引将越界，因为 `newList` 只有索引 1、2 和 3。

## 显示运算符

![Images](images/t0194-01.jpg)

![image](images/common.jpg)

### 示例二十

以下程序将显示什么？

```
a ← 3
b ← 17
a ← b
DISPLAY(a)
```

如下图所示，在 `a` 被打印之前，所有变量都必须初始化。注意 `a` 初始化为值 3，`b` 设置为 17。下一步将 `a` 的值设置为 `b` 的值，即 17。

![Images](images/p0194-01a.jpg)

**答案：17**

![image](images/common.jpg)

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

![image](images/common.jpg)

### 示例二十二

以下程序将显示什么？

![Images](images/p0195-01.jpg)

| *a* | *b* | DISPLAY |
| --- | --- | --- |
| 5 + 8 = 13 | 4 MOD 5 = 4 | 17 |

**答案：17**

## 输入运算符

| 文本：`INPUT()` 代码块：`INPUT` | 接受来自用户的值并返回它。 |
| --- | --- |

![image](images/common.jpg)

### 示例二十三

如果 `INPUT` 函数读取一个偶数（如 4），以下程序将显示什么？

```
a ← INPUT()
a ← a MOD 2
DISPLAY(a)
```

对于 4（或任何偶数）除以 2，余数将始终为 0。

**答案：0**

![image](images/common.jpg)

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

![image](images/common.jpg)

### 示例二十五

以下程序将显示什么？

![Images](images/p0196-02.jpg)

| ***a*** | *b* | DISPLAY |
| --- | --- | --- |
| 3 | 3 MOD 5 = 3 | true |

`a` 初始化为 3；`b` 初始化为 3 除以 5 的余数。因为 3 等于 3，程序将显示 true。

**答案：True**

![image](images/common.jpg)

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

| 文本：`RANDOM(a, b)` 代码块：![Images](images/p0197-02.jpg) | 计算结果为从 `a` 到 `b` 的随机整数，包括 `a` 和 `b`。例如，`RANDOM(1, 3)` 可能计算结果为 1、2 或 3。 |
| --- | --- |

![image](images/common.jpg)

### 示例二十七

如果执行下面的代码多次，预期显示“true”的百分比是多少？

![Images](images/p0197-03.jpg)

`RANDOM` 可以选取 1 或 2。选中 1 的概率是 1/2 或 50%。

**答案：50%**

![image](images/common.jpg)

### 示例二十八

如果执行下面的代码多次，预期显示“false”的百分比是多少？

![Images](images/p0197-04.jpg)

数字 1、2、3 和 4 都是可能的选择。选中 3 的概率是 1/4 或 25%。未选中 3 的概率是 3/4，即 75%。

**答案：75%**

![image](images/common.jpg)

### 示例二十九

如果执行下面的代码多次，预期显示“true”的百分比是多少？

![Images](images/p0198-01.jpg)

数字 1、2、3、4、5、6、7、8、9 和 10 都可以被选中。因为 `a ≤ 3` 包括 1、2 和 3，答案是 3/10 = 30%。

**答案：30%**

### 布尔表

| **指令** | **解释** |
| --- | --- |
| 文本：`NOT condition` 代码块：![Images](images/p0198-02.jpg) | 如果条件为 false，则计算结果为“true”；否则计算结果为“false”。 |
| 文本：`condition1 AND condition2` 代码块：![Images](images/p0198-03.jpg) | 如果 condition1 和 condition2 都为 true，则计算结果为“true”；否则计算结果为“false”。 |
| 文本：`condition1 OR condition2` 代码块：![Images](images/p0198-04.jpg) | 如果 condition1 为 true 或 condition2 为 true，或两者都为 true，则计算结果为“true”；否则计算结果为“false”。 |

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

![Images](images/t0199-01.jpg)
