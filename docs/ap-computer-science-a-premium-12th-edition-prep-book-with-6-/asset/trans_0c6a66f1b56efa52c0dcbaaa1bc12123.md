

## [4](#50_Chapter42.xhtml#fn5-4). (C)

语句 `double x = Math.random();` 生成一个范围在 0 ≤ `x` < 1 的随机 `double` 值。假设 `probDeath` 为 0.67（即 67%）。假设随机 double 值在该区间内均匀分布，则可以预期 67% 的时间 `x` 将落在 0 ≤ `x` < 0.67 的范围内。因此，可以通过测试 `x` 是否在 0 和 0.67 之间（即 `x < 0.67`）来模拟死亡概率。因此，`x < probDeath` 是植物死亡的期望条件，排除了选项 A 和 B。选项 D 和 E 失败是因为 `(int) probDeath` 将 `probDeath` 截断为 0。测试 `x < 0` 永远为 false，而测试 `x == 0` 仅在随机数生成器恰好返回 0 时为 true，这是极不可能发生的事件！这两个选项都无法正确模拟死亡概率。

## [5](#50_Chapter42.xhtml#fn5-5). (A)

表达式

```
(int) (Math.random() * 50);
```

返回一个 0 到 49 的 `int` 值。因此，加 1 将范围移至 1 到 50，这正是题目要求的。

## [6](#50_Chapter42.xhtml#fn5-6). (D)

`Integer` 类没有可以改变 `i` 内容的方法。然而，`i` 可以被重新赋值使其引用另一个对象。这在片段 I 和 III 中都发生了。片段 II 是错误的，因为 `intValue` 是一个*访问器*——它不能用来改变对象 `i` 的值。

## [7](#50_Chapter42.xhtml#fn5-7). (C)

测试 I 和 II 都能通过编译。测试 I 通过编译是因为 `==` 测试*引用*是否相等。要测试值，应使用 `intValue`，测试 II 正确地做到了这一点。测试 III 失败是因为不能用 `int` 调用方法（本例中为 `equals`）。

## [8](#50_Chapter42.xhtml#fn5-8). (C)

调用了 `Integer` 类的 `toString` 方法，该方法返回一个表示 `intObj` 值的字符串：

```
System.out.println(intObj.toString());   // outputs 9
```

## [9](#50_Chapter42.xhtml#fn5-9). (C)

内存槽如下：

![images](images/f186-01.jpg)

语句 II 和 III 为真，因为 `s1` 和 `s2` 的内容相同，`s3` 和 `s2` 的内容也相同。语句 I 为假，因为 `s1` 和 `s2` 不是同一个引用。注意表达式 `s1 == s3` 将为真，因为 `s1` 和 `s3` *是*同一个引用。

## [10](#50_Chapter42.xhtml#fn5-10). (D)

注意 `“TOMATO”` 排在 `“tomato”` 和 `“tom”` 之前，因为 `“T”` 排在 `“t”` 之前。此外，`“tom”` 排在 `“tomato”` 之前，因为 `“tom”` 的长度小于 `“tomato”`。因此以下每一项均为真：

![images](images/f186-02.jpg)

所以

- 选项 A 为 T and F，结果为 F。
- 选项 B 为 F or F，结果为 F。
- 选项 C 为 F and T，结果为 F。
- 选项 D 为 T and T，结果为 T。
- 选项 E 为 T and F，结果为 F。

## [11](#50_Chapter42.xhtml#fn5-11). (A)

`x` 包含 `“m”` 在 `line` 中首次出现的索引——即 `2`。（记住 `“S”` 在索引 `0` 处。）方法调用 `line.substring(10,15)` 返回 `“silly”`，即从索引 10 开始、延伸至索引 14 的子串。方法调用 `line.substring(25,27)` 返回 `“st”`（不包含索引 27 处的字符！）。连接运算符 `+` 将它们连接起来。

## [12](#50_Chapter42.xhtml#fn5-12). (D)

姓氏的第一个字符位于空格后的第一个字符处。因此，`substring` 的 `startIndex` 必须是 `k+1`。这排除了表达式 I。表达式 II 取从位置 `k+1` 到 `fullName` 字符串末尾的所有字符，这是正确的。表达式 III 取从位置 `k+1` 到位置 `fullName.length()-1` 的所有字符，这也是正确的。

## [13](#50_Chapter42.xhtml#fn5-13). (E)

假设 `s` 包含 `“cat”`。你想要 `pigString = “at” + “c” + “ay”`。字符串 `“at”` 是 `s` 从位置 1 开始、到位置 `s.length()-1` 结束的子串。该部分正确的子串调用是 `s.substring(1,s.length())`，这排除了选项 A、C 和 D。（回忆：第一个参数是起始位置，第二个参数是子串最后一个索引的下一个位置。）单词的第一个字母——示例中的 `“c”`——从位置 0 开始、到位置 0 结束。正确的表达式是 `s.substring(0,1)`，这排除了选项 B。

## [14](#50_Chapter42.xhtml#fn5-14). (A)

每当 `s2` 出现在 `s1` 中时，语句 I 为真。例如，若字符串 `s1 = “catastrophe”` 且 `s2 = “cat”`，则 `getString` 返回 `“cat”`。语句 II 永远不会发生。如果 `s2` 不包含在 `s1` 中，`indexOf` 调用将返回 `-1`。将负整数作为 `substring` 的第一个参数将导致 `StringIndexOutOfBoundsException`。每当 `s1` 等于 `s2` 时，语句 III 为真。

## [15](#50_Chapter42.xhtml#fn5-15). (C)

`String temp` 表示 `s` 的单字符子串。该方法检查 `s` 中的每个字符，如果是非空白字符，则将其追加到 `str`（初始为空）。每次赋值 `str += temp` 都会给 `str` 赋予一个新的引用。因此，`str` 最终成为 `s` 的一个副本，但去除了空白。返回了对最终 `str` 对象的引用。选项 A 虽然正确指出 `s` 保持不变，但这不是对该方法功能的*最佳*描述。选项 B 不精确，因为对象参数永远不会被修改：任何更改（如果有）都是在副本上进行的。选项 D 和 E 错误，因为该方法移除的是空白。

## [16](#50_Chapter42.xhtml#fn5-16). (E)

`compareTo` 方法返回 `int`，因此可以排除选项 A 和 B。在 `compareTo` 的实现中，适用于该特定示例的代码段为：

![images](images/f187-01.jpg)

因为 2 < 4，所以返回值 `−1`。

## [17](#50_Chapter42.xhtml#fn5-17). (C)

表达式 III 为真：`compareTo` 方法实现为当两个 `Position` 对象具有相同的行和列时返回 `0`。表达式 I 为假，因为 `object1 == object2` 仅在 `object1` 和 `object2` 是*同一个引用*时才返回 `true`。表达式 II 比较棘手。你希望 `p1` 和 `p3` 相等，因为它们具有相同的行和列值。然而，这不会自动发生。必须为 `Position` 类显式重写 `equals` 方法。如果未重写，从 `Object` 类继承的默认 `equals` 方法仅在 `p1` 和 `p3` 是同一个引用时返回 true，事实并非如此。

## [18](#50_Chapter42.xhtml#fn5-18). (C)

回忆一下，基本类型和对象引用都是按值传递的。这意味着实际参数的副本被创建。任何更改都是针对*副本*进行的。实际参数保持不变。因此，在方法 I 和 II 中，参数将保留其原始值并保持未交换状态。

为了说明方法 II 为何失败，请考虑测试它的以下代码片段：

![images](images/f187-02.jpg)

调用 `swap` 前的内存槽：

![images](images/f187-03.jpg)

调用 `swap` 时的内存槽：

![images](images/f188-01.jpg)

退出 `swap` 方法前的内存槽：

![images](images/f188-02.jpg)

退出后，`xObject` 和 `yObject` 保留了其原始值：

![images](images/f188-03.jpg)

方法 III 之所以有效，是因为改变的是对象的*内容*，而不是对象引用。因此，退出方法后，`IntPair` 引用保持不变，但 first 和 second 的值已互换。（有关内存槽的图示，请参阅下一题的解释。）在本题中，`IntPair` 被用作需要交换值的一对整数的包装类。

