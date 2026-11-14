
设置 `y` = |`x`| 可以使某些步骤更简单。这不会丢失关于 `x` 是正数、负数（或零）的信息，因为我们不改变输入值 `x`，并且始终可以回溯引用它。

如果 `y` = 0，返回由全 0 位组成的 `n` 位字符串，即 `0000`⋯`000`。在尝试查找阶码位之前，处理可能的 `NaR` 或 0 的情况非常重要。这也处理了 `y` ≥ `maxPos` 或 `y` ≤ `minPos` 的情况：

```
If y ≥ maxPos,
    Return the posit for maxPos times the sign of x,
Else if y ≤ minPos,
    Return the posit for minPos times the sign of x,
End if.
```

这也处理了舍入规则之一，即超出动态范围的幅度会饱和到（带符号的）最大值或最小值。此外，处理这些特殊情况可确保结束阶码的相反位能适应下一小节中构建的 `n` 位字符串。

### 3.4.3 编码阶码位

由于计算机环境通常支持无符号整数类型，因此很容易将 posit 位串视为无符号 `n` 位整数。既然已经处理了 `NaR` 和 0 的情况，阶码最多只能有 `n` - 1 位长。利用一个 `n` 位无符号整数 `p`，我们可以从最高有效位（`MSB`）开始存储阶码，因为我们不需要符号位，这样最后会多出一位，可用于正确舍入。

```
If y ≥ 1, the regime will be a string of 1 bits:
    Set p = 1 and i = 2. The number of posit bits found so far is i.
    While y ≥ uSeed and i < n,
        shift p left by one place and set the LSB to 1 (lengthen the regime).
        Divide y by uSeed and increment i.
    End while.
    Shift p left by one place to prepare for the next phase, and increment i.
Else y < 1, so the regime will be a string of 0 bits:
    Set p = 0 and i = 1 (off by 1 from the y ≥ 1 case, since we seek 1 ≤ y < uSeed).
    While y < 1 and i ≤ n,
        multiply y by uSeed and increment i.
    End while.
    Set p = 1 (the opposite bit ending the regime) and increment i.
End if.
```

“将 `p` 左移一位”会在最低有效位（`LSB`）处创建一个 `0`，当阶码是 `1` 位串时，这就是结束阶码的相反位。

### 3.4.4 编码指数位

将 `x` 转换为 posit 格式的过程是从左向右进行的，查找指数位也不例外。我们知道 1 ≤ `y` < `uSeed`。如果格式使用 `eS` = 0，则无需操作，直接跳到查找尾数位。否则，继续二分查找，从最高有效位到最低有效位确定指数位。计算 `uSeed` = 2²`eS` 对计算机来说其实很容易，因为将 `1` 位左移 `eS` 位得到 2^(`eS`) 的无符号整数，然后将 `1` 位左移该无符号整数位即得到 2²`eS`。在 C 语言中，可以简洁地表示为 `1 << (1 << eS)`。

因此，提取指数位的算法如下：

```
Set e = eS − 1.
While i < n and e > 0,
    Shift p left by one place to make a place for an exponent bit.
    Set scale = 1 << (1 << e).
    If y ≥ scale, set the LSB of p to 1 and set y = y / scale.
    Increment i, since we have used another posit bit for the exponent.
    Set e = e − 1.
End while.
Shift p left by one place to prepare for the next phase, and increment i.
```

如果位计数器 `i` 在 `e` 递减到 0 之前实际达到了 `n`，指数位将被截断，posit 将处于“暮光区”。否则，我们将得到尾数 `y`，满足 1 ≤ `y` < 2。

### 3.4.5 编码尾数位

既然 `y` 现在是介于 1 和 2 之间的定点数，其二进制位串总是以 `1` 位开头，因此无需存储该位。这个 `1` 是隐含的。因此，我们首先通过从 `y` 中减去 1 来得到尾数。然后通过将尾数加倍并测试其是否大于 1 来找到尾数的每一位；如果大于 1，在 posit 位串中安装一个 `1` 位，从 `y` 中减去 1，重复此过程，直到没有更多空间存放尾数位。

一旦填满所有 `n` + 1 位，判断转换是否精确非常简单：`y` > 0 吗？如果是，则 `ubit` 为 `1`，因为最后一位之后还有更多位。但如果 `y` = 0，则转换精确落在一个 posit 值上，所以 `ubit` 为 `0`。记住，`ubit` 是银行家舍入法所需的。

```
Set y = y − 1.
While i < n,
    Shift p left by one place. This puts a 0 in the LSB position.
    Set y = 2 × y.
    If y ≥ 1, set the LSB of p to 1 and set y = y − 1.
    Increment i, since we've used another posit bit for the fraction.
End while.
```

经过此步骤后，`i = n`，所以我们得到一个包含 `n` 位的位串。但它没有符号位，所以比舍入后的值多一位。称之为 `b`[−1]。

### 3.4.6 舍入并应用 `x` 的符号

*银行家舍入法*是将值 `x` 舍入到最近的可表示数 `p`，如果有两个同样接近 `x` 的 `p` 可能性，规则是选择具有*偶数*表示的那个。在二进制中，偶数以 `0` 结尾，奇数以 `1` 结尾。“遇半进偶”规则的原因是它使舍入*无偏差*。想象一家银行需要计算数十亿美元交易的精确到分的利息；即使是最轻微的向上或向下偏差也可能迅速积累成一笔巨款。曾有利用舍入来“白得”利益的方案。

银行家舍入法是 posit 格式的舍入模式，也是*唯一*的舍入模式。无论你是舍入整数格式、定点数、浮点数还是 posit，原则都是一样的。银行家舍入算法只需要*三个位*，下图展示了 8 位格式的情况：

![银行家舍入法所需的三个位](images/pg51_1.jpg)

银行家舍入法所需的三个位

对于 `n` 位格式，我们的约定是用下标从 0（`LSB`）到 `n` - 1（`MSB`）标记位。我们需要的三个位是 `LSB`、一个称为*舍入位*的 `b`[−1] 位，以及我们在[第 1 章](#chapter1.xhtml)见过的 `ubit`。如果 `ubit` = `1`，表示在 `b`[−1] 之后还有更多有效数字，就像在数字最后一位后写“⋯”一样。

如果 `b`[−1] 是 `1` 且 `ubit` 是 `0`，该值处于临界点；它是如果多一位所能表示的值。为了使舍入值为偶数，如果 `b`[0] 是 0，则不做任何操作（即向下舍入，忽略 `b`[−1]）；但如果 `b`[0] 是 `1`，则向 `LSB` 加 `1` 并向左传播进位。使用 posit 格式，不存在溢出的可能性。

如果 `b`[−1] 是 `1` 且 `ubit` 是 `1`，意味着在 `b`[−1] 位之后还有 `1` 位，则该值高于临界点，需要向上舍入。将值 `x` 舍入为 posit 的四种情况如下：

*   如果 `x` 是 0 或 `NaR`，返回代表该值的相应 posit。
*   如果 |`x`| ≥ `maxPos`，返回带有 `x` 相同符号的 `maxPos` 的 posit。
*   如果 |`x`| ≤ `minPos`，返回带有 `x` 相同符号的 `minPos` 的 posit。
*   如果 `minPos` < |`x`| < `maxPos`，将 `x` 编码为 `n` + 1 位；如果该表示精确，将 `ubit` 设为 `0`，否则设为 `1`。如果 `b`[−1] 是 `1` 且（`b`[0] 是 `1` 或 `ubit` 是 `1`），向 `b`[0] 位置加 1 并传播任何进位。

如果你喜欢数字硬件设计并能看懂电路图，下图展示了带有额外 `b`[−1] 位和临时存储中一些尾随位的数字的银行家舍入逻辑。

![银行家舍入法的逻辑电路](images/pg52_1.jpg)

银行家舍入法的逻辑电路
