
请确保你理解基本类型和用户定义类型之间的区别，以及以下类型运算符之间的区别：算术、关系、逻辑和赋值。了解哪些条件会导致什么类型的错误。

你应该能够处理数字——知道如何比较它们，并了解可能导致舍入误差的条件。

你应该知道 `Integer` 常量 `Integer.MIN_VALUE` 和 `Integer.MAX_VALUE`。

熟悉以下每种控制结构：条件语句、`for` 循环、`while` 循环和增强型 `for` 循环。

了解 AP 考试关于输入和输出的期望。

学习属于 AP Java 子集一部分的未检查异常。

### 关于 Java 语言入门特性的选择题

**1.** 以下哪对声明会导致错误消息？

I. `double x = 14.7; int y = x;`

II. `double x = 14.7; int y = (int) x;`

III. `int x = 14; double y = x;`

(A) 无

(B) 仅 I

(C) 仅 II

(D) 仅 III

(E) I 和 III

**2.** 以下代码将产生什么输出？

![images](images/f081-04.jpg)

(A) `* This is not a comment *`

(B) `\* This is not a comment *\`

(C) `* This is not a comment *`

(D) `\\* This is not a comment *\\`

(E) `\* This is not a comment *\`

**3.** 考虑以下代码段。

![images](images/f081-09.jpg)

如果 `n` 为 `int` 类型，且在执行该段代码时值为 `0`，将会发生什么？

(A) 将抛出 `ArithmeticException`。

(B) 将发生语法错误。

(C) 将执行 `statement1`，但不执行 `statement2`。

(D) 将执行 `statement2`，但不执行 `statement1`。

(E) `statement1` 和 `statement2` 均不执行；控制权将传递给 `if` 语句之后的第一条语句。

**4.** 参考以下代码片段。

![images](images/f081-10.jpg)

输出为

![images](images/f081-11.jpg)

程序员预期的输出为

![images](images/f081-12.jpg)

以下哪项作为第一行代码的替换**无法**修复该问题？

(A) `double answer = (double) 13 / 5;`

(B) `double answer = 13 / (double) 5;`

(C) `double answer = 13.0 / 5;`

(D) `double answer = 13 / 5.0;`

(E) `double answer = (double) (13 / 5);`

**5.** 如果

![images](images/f081-13a.jpg)

`result` 中存储的值是多少？

(A) −5

(B) 0

(C) 13

(D) −1

(E) 12

**6.** 假设加法和减法的优先级高于乘法和除法。那么表达式

![images](images/f081-15.jpg)

将计算为以下哪项？

(A) 11

(B) 12

(C) 5

(D) 9

(E) −4

**7.** 鉴于 `x` 是 `double` 类型的变量，以下布尔表达式哪项描述是正确的？

![images](images/f082-01.jpg)

(A) 它将始终计算为 false。

(B) 对于某些 `x` 的值，它可能计算为 false。

(C) 仅当 `x` 为零时，它才计算为 false。

(D) 仅当 `x` 非常大或非常接近零时，它才计算为 false。

(E) 它将始终计算为 true。

**8.** 设 `x` 为正数的 `double` 类型变量。程序包含布尔表达式 `(Math.pow(x,0.5) == Math.sqrt(x))`。尽管 *x*^(1/2) 在数学上等同于 ![images](images/Root-x.jpg)，但上述表达式在学生的程序中返回值 `false`。以下哪项是最可能的原因？

(A) `Math.pow` 返回 `int`，而 `Math.sqrt` 返回 `double`。

(B) `x` 在之前的程序语句中计算不精确。

(C) 计算机用 32 位字存储浮点数。

(D) 计算 `pow` 和 `sqrt` 函数时存在舍入误差。

(E) 计算 `pow` 函数时存在溢出错误。

**9.** 如果 `num` 的输入值为 `22`，以下格式不佳的程序段的输出将是什么？

![images](images/f082-02.jpg)

(A) `22`

(B) `4`

(C) `2 is negative`

(D) `22 is negative`

(E) 无任何输出。

**10.** 执行以下程序段后，`x` 和 `y` 中存储的值分别是多少？

![images](images/f082-03.jpg)

(A) `x = 30 y = 90`

(B) `x = 30 y = -30`

(C) `x = 30 y = 60`

(D) `x = 3 y = -3`

(E) `x = 30 y = 40`

**11.** 以下哪项仅当布尔表达式 `A`、`B` 和 `C` **全为 false** 时才计算为 true？

(A) `!A && !(B && !C)`

(B) `!A || !B || !C`

(C) `!(A || B || C)`

(D) `!(A && B && C)`

(E) `!A || !(B || !C)`

**12.** 假设 `a` 和 `b` 为整数。布尔表达式

![images](images/f082-06.jpg)

在以下哪个条件下将始终计算为 `true`？

(A) `a = b`。

(B) `a > b`。

(C) `a < b`。

(D) `a > b` 且 `b > 0`。

(E) `a > b` 且 `b < 0`。

**13.** 已知 `a`、`b` 和 `c` 为整数，考虑布尔表达式

![images](images/f083-01.jpg)

以下哪项将保证该表达式为 `true`？

(A) `c < a` 为 `false`。

(B) `c < a` 为 `true`。

(C) `a < b` 为 `false`。

(D) `c == a * b` 为 `true`。

(E) `c == a * b` 为 `true`，且 `c < a` 为 `true`。

**14.** 在以下代码段中，你可以假设 `a`、`b` 和 `n` 均为 `int` 类型。

![images](images/f083-03.jpg)

如果 `a == b` 为 false，将会发生什么？

(A) 将执行 `/* statement 1 */`。

(B) 将执行 `/* statement 2 */`。

(C) 将执行 `/* statement 1 */` 或 `/* statement 2 */` 中的一个。

(D) 将发生编译时错误。

(E) 将抛出异常。

**15.** 已知 `n` 和 `count` 均为 `int` 类型，关于以下代码段哪项陈述是正确的？

![images](images/f083-03a.jpg)

(A) 对于所有输入值 `n`，I 和 II 完全等价。

(B) 对于所有输入值 `n` ≥ `1`，I 和 II 完全等价，但当 `n` ≤ `0` 时不同。

(C) 仅当 `n` = `0` 时，I 和 II 完全等价。

(D) 仅当 `n` 为偶数时，I 和 II 完全等价。

(E) 对于任何 `n` 的输入值，I 和 II 都不等价。

**16.** 以下片段旨在让用户在键盘输入一系列正整数，并用哨兵值终止列表。

![images](images/f083-04.jpg)

该片段不正确。以下哪项陈述是正确的？

(A) 哨兵值被处理了。

(B) 列表中输入的最后一个非哨兵值未能被处理。

(C) `SENTINEL` 值的不当选择导致循环在处理完所有值之前终止。

(D) 代码将始终处理一个不在列表中的值。

(E) 将 `SENTINEL` 值作为第一个值输入会导致运行时错误。

**17.** 考虑此代码段。

![images](images/f084-01.jpg)

执行此代码段后将输出什么？

(A) `1 6`

(B) `7 12`

(C) `-3 12`

(D) `4 12`

(E) `-3 6`

第 18 和 19 题参考以下方法 `checkNumber`，该方法检查其四位整数参数的有效性。

![images](images/f085-01.jpg)

程序通过以下语句调用方法 `checkNumber`：

![images](images/f085-02.jpg)

**18.** 以下哪个 `num` 值将导致 `valid` 的值为 `true`？

(A) `6143`

(B) `6144`

(C) `6145`

(D) `6146`

(E) `6147`

**19.** 局部变量 `nRemaining` 的目的是什么？

(A) 如果没有临时变量的帮助，无法将 `n` 分离为各个数字。

(B) `nRemaining` 防止参数 `n` 被修改。

(C) `nRemaining` 增强了算法的可读性。

(D) 退出方法时，`nRemaining` 的值可能被重用。

(E) `nRemaining` 作为整数除法左侧操作数是必需的。
