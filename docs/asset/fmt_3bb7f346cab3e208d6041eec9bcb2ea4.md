
一个程序有一个 `String` 变量 `fullName`，它存储名字，后跟一个空格，再后跟姓氏。名字和姓氏中均不包含空格。以下是一些 `fullName` 值的示例：`"Anthony Coppola"`、`"Jimmy Carroll"` 和 `"Tom DeWire"`。考虑这段从 `fullName` 变量中提取姓氏并将其存储在 `lastName` 中（不包含周围空格）的代码片段：

![images](img/f172-01.jpg)

以下哪项是 `/*` **表达式** `*/` 的正确替换？

I. `fullName.substring(k);`

II. `fullName.substring(k + 1);`

III. `fullName.substring(k + 1, fullName.length());`

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) II 和 III

(E) I 和 III

####### 13

将英语转换为 Pig Latin（猪拉丁语）的规则之一是：如果一个单词以辅音开头，将该辅音移到单词末尾并加上 "ay"。因此 "dog" 变成 "ogday"，"crisp" 变成 "rispcay"。假设 `s` 是一个包含以辅音开头的英语单词的 `String`。假设声明如下，以下哪项能创建正确的对应 Pig Latin 单词？

![images](img/f172-05.jpg)

(A) `pigString = s.substring(0, s.length()) + s.substring(0,1) + ayString;`

(B) `pigString = s.substring(1, s.length()) + s.substring(0,0) + ayString;`

(C) `pigString = s.substring(0, s.length()-1) + s.substring(0,1) + ayString;`

(D) `pigString = s.substring(1, s.length()-1) + s.substring(0,0) + ayString;`

(E) `pigString = s.substring(1, s.length()) + s.substring(0,1) + ayString;`

####### 14

本题参考下面所示的 `getString` 方法。

![images](img/f173-01.jpg)

关于 `getString`，以下哪项描述是正确的？它可能返回一个字符串，该字符串

I. 等于 `s2`。

II. 与 `s2` 没有任何共同字符。

III. 等于 `s1`。

(A) 仅 I 和 III

(B) 仅 II 和 III

(C) 仅 I 和 II

(D) I、II 和 III

(E) 以上均不正确。

####### 15

考虑此方法。

![images](img/f173-02.jpg)

以下哪项是对 `doSomething` 行为最精确的描述？

(A) 它返回未改变的 `s`。

(B) 它返回移除了所有空格的 `s`。

(C) 它返回一个 `String`，该字符串等同于移除了所有空格的 `s`。

(D) 它返回 `s` 的一份精确副本 `String`。

(E) 它返回一个包含 `s.length()` 个空格的 `String`。

###### 第 16 和 17 题

请参考下面的 `Position` 和 `PositionTest` 类。

`public class Position`

![images](img/f174-01.jpg)

![images](img/f175-01.jpg)

####### 16

关于 `p1.compareTo(p2)` 的值，以下哪项为真？

(A) 它等于 `true`。

(B) 它等于 `false`。

(C) 它等于 `0`。

(D) 它等于 `1`。

(E) 它等于 `-1`。

####### 17

关于 `p1` 和 `p3` 的哪个布尔表达式为真？

I. `p1 == p3`

II. `p1.equals(p3)`

III. `p1.compareTo(p3) == 0`

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) II 和 III

(E) I、II 和 III

###### 第 18 和 19 题

涉及交换两个整数值的问题。提出了三种方法来解决该问题，分别使用基本类型 `int`、`Integer` 对象和 `IntPair` 对象，其中 `IntPair` 定义如下。

![images](img/f176-01.jpg)

####### 18

这里有三个不同的 `swap` 方法，每个都旨在用于客户端程序。

![images](img/f177-01.jpg)

当在客户端程序中正确使用并传入适当参数时，哪个方法能按预期交换两个整数？

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) II 和 III

(E) I、II 和 III

####### 19

考虑以下使用 `IntPair` 类的程序。

![images](img/f178-01.jpg)

以下哪项是 `/*` **交换** `x` **和** `y` **的代码** `*/` 的正确替换？

![images](img/f178-02.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) II 和 III

(E) 以上均不正确。

###### 第 20 和 21 题

请参考下面的 `Name` 类。

![images](img/f179-01.jpg)

####### 20

`compareTo` 方法实现了标准的姓名排序算法，即姓氏优先于名字。使用 `String` 的字典序或词典序。例如，姓名 Scott Dentes 排在 Nick Elser 之前，Adam Cooper 排在 Sara Cooper 之前。

以下哪项是 `/* more code */` 的正确替换？

![images](img/f180-01.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) I、II 和 III

###### 21

关于 `Name` 类的哪个陈述是错误的？

(A) `Name` 对象是不可变的。

(B) `Name` 中的方法有可能抛出 `NullPointerException`。

(C) 如果 `n1` 和 `n2` 是客户端类中的 `Name` 对象，则表达式 `n1.equals(n2)` 和 `n1.compareTo(n2) == 0` 必须具有相同的值。

(D) 如果参数为 null，`compareTo` 方法会抛出运行时异常。

(E) 既然 `Name` 类有 `compareTo` 方法，它*必须*提供 `equals` 方法的实现。

###### 22

以下代码段的输出是什么？

![images](img/f180-04.jpg)

(A) `1 3 2 3`

(B) `2 4 3 4`

(C) `1 5 8 12`

(D) `1 5 8 11`

(E) 因 `IndexOutOfBoundsException` 无输出

###### 23

考虑以下方法 `removeAll`，它创建并返回一个字符串，该字符串去除了输入短语中所有出现的单字符 `String` 参数 `ch`。

![images](img/f181-01.jpg)

该方法无法按预期工作。对 `removeAll` 方法进行以下哪项更改可使其按规范工作？

(A) 将第 10 行改为  

`while (pos >= -1)`

(B) 将第 12 行改为  

`str = str + newPhrase.substring(0, pos);`

(C) 将第 13 行改为  

`newPhrase = newPhrase.substring(pos);`

(D) 将第 14 行改为  

`pos = phrase.indexOf(ch);`

(E) 将第 16 行改为  

`str = str + newPhrase.substring(pos + 1);`

###### 24

一位程序员编写了一个程序，根据人类用户输入的语句与其"聊天"。程序包含一个方法 `findKeyWord`，用于在输入语句中搜索给定的关键字。`findKeyWord` 方法包含以下代码行。

`pos = statement.indexOf(word);`

假设 `pos` 的值 `>= 0`；即找到了 `word`。程序员现在想测试是否找到了一个完整的单词，而不是另一个单词的一部分。例如，如果"cat"是关键字，程序员需要检查它不是"catch"或"category"的一部分。以下是测试 `word` 是否为独立单词的代码。（你可以假设 `statement` 全为小写，且仅包含字母和空格。）

![images](img/f181-02.jpg)

哪项 `/* test */` 的替换将给出期望的结果？

(A) `(before < "a" || before > "z") && (after < "a" || after > "z")`

(B) `(before > "a" || before < "z") && (after > "a" || after < "z")`

(C) `(before.compareTo("a") < 0 && before.compareTo("z") > 0) || (after.compareTo("a") > 0 && after.compareTo("z") < 0)`

(D) `(before.compareTo("a") > 0 && before.compareTo("z") < 0) && (after.compareTo("a") > 0 && after.compareTo("z") < 0)`

(E) `(before.compareTo("a") < 0 || before.compareTo("z") > 0) && (after.compareTo("a") < 0 || after.compareTo("z") > 0)`

####### 25

一个模拟计算机与人类用户对话的程序会针对用户的评论生成随机回复。计算机可以生成的所有可能回复都存储在一个名为 `allResponses` 的 `String` 数组中。下面给出的方法 `getResponse` 从数组中返回一个随机回复字符串。

![images](img/f183-01.jpg)

哪项是正确的 `/* implementation */`？

(A) `int i = (int) (Math.random() * allResponses.length); return allResponses[i];`

(B) `return (String) (Math.random() * allResponses.length);`

(C) `int i = Math.random() * allResponses.length; return allResponses[i];`

(D) `int i = (int) (Math.random() * (allResponses.length - 1)); return allResponses[i];`

(E) `return (int) (Math.random() * allResponses.length);`

###### 第 26 和 27 题

一个单词创建游戏使用字母块，每个块上有一个字母和一个用于计分的点值。`Tile` 类用于表示一个字母块。

![images](img/f183-08.jpg)

####### 26

`Tile` 类包含一个 `toString` 方法，该方法创建一个包含 `Tile` 字母和点值的 `String`。字符串应采用以下格式。

![images](img/f184-01.jpg)

例如，

![images](img/f184-02.jpg)

考虑下面的 `toString` 方法。

![images](img/f184-03.jpg)

哪项 `/* code */` 会导致正确的输出？

(A) `Letter + "letter " + "(point value = " + pointValue + ")";`

(B) `"Letter " + letter + ("point value = " + pointValue);`

(C) `Letter + this.letter + " (point value = " + pointValue + ")";`

(D) `"Letter " + letter + " (point value = " + (String) pointValue + ")";`

(E) `"Letter " + letter + " (point value = " + pointValue + ")";`

####### 27

在单词游戏中，任意两个具有相同字母的块也具有相同的点值，但反之不一定成立。例如，所有元音的点值均为 1。如果两个块具有相同的字母，则称它们匹配。考虑 `Tile` 类的以下 `matches` 方法。

![images](img/f184-05.jpg)

哪些 `/* code */` 的替换会返回期望的结果？注意：你不能假设 `Tile` 类有自己的 `equals` 方法。

I. `letter == otherTile.letter`

II. `this.equals(otherTile)`

III. `letter.equals(otherTile.letter)`

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 II 和 III

(E) 仅 I 和 III

###### 答案解析

####### 1

**(B)** `Math` 类的所有方法都是静态方法，这意味着你不能使用调用该方法的 `Math` 对象。该方法通过类名 `Math` 加上点运算符来调用。因此片段 II 正确，片段 I 不正确。片段 III 会导致错误：由于 `pow` 的参数类型为 `double`，结果应存储在 `double` 中。

####### 2

**(B)** `Math.sqrt` 方法必须在基本类型 `double` 上调用，但在该行中自动拆箱处理了这一点：

`double x = d;`

该方法的返回类型是 `Double`，自动装箱在以下语句中处理了这一点：

`return x;`

片段 III 失败，因为如果不使用关键字 `new`，就不能使用 `Double` 构造函数来创建新对象。

####### 3

**(C)** 值 −4.67 必须舍入为 −5。减去 0.5 得到 −5.17。转型为 `int` 会截断数字（切掉小数部分），留下 −5 的值。其他选项均不产生 −5。选项 A 给出 `d` 的绝对值：4.67。选项 B 是 `Random` 的错误用法。`nextInt` 的参数应为整数 *n*，*n* ≥ 2。该方法随后返回一个随机 `int` *k*，其中 0 ≤ *k* < *n*。选项 D 是将*正*实数舍入到最接近整数的方法。在实际情况下它产生 −4。选项 E 给出 −5 的绝对值——即 5。

###### 4. (C)

语句 `double x = Math.random();` 生成一个范围在 0 ≤ `x` < 1 的随机 `double` 值。假设 `probDeath` 为 0.67（即 67%）。假设随机 double 值在该区间内均匀分布，则可以预期 67% 的时间 `x` 将落在 0 ≤ `x` < 0.67 的范围内。因此，可以通过测试 `x` 是否在 0 和 0.67 之间（即 `x < 0.67`）来模拟死亡概率。因此，`x < probDeath` 是植物死亡的期望条件，排除了选项 A 和 B。选项 D 和 E 失败是因为 `(int) probDeath` 将 `probDeath` 截断为 0。测试 `x < 0` 永远为 false，而测试 `x == 0` 仅在随机数生成器恰好返回 0 时为 true，这是极不可能发生的事件！这两个选项都无法正确模拟死亡概率。

###### 5. (A)

表达式

```
(int) (Math.random() * 50);
```

返回一个 0 到 49 的 `int` 值。因此，加 1 将范围移至 1 到 50，这正是题目要求的。

###### 6. (D)

`Integer` 类没有可以改变 `i` 内容的方法。然而，`i` 可以被重新赋值使其引用另一个对象。这在片段 I 和 III 中都发生了。片段 II 是错误的，因为 `intValue` 是一个*访问器*——它不能用来改变对象 `i` 的值。

###### 7. (C)

测试 I 和 II 都能通过编译。测试 I 通过编译是因为 `==` 测试*引用*是否相等。要测试值，应使用 `intValue`，测试 II 正确地做到了这一点。测试 III 失败是因为不能用 `int` 调用方法（本例中为 `equals`）。

###### 8. (C)

调用了 `Integer` 类的 `toString` 方法，该方法返回一个表示 `intObj` 值的字符串：

```
System.out.println(intObj.toString());   // outputs 9
```

###### 9. (C)

内存槽如下：

![images](img/f186-01.jpg)

语句 II 和 III 为真，因为 `s1` 和 `s2` 的内容相同，`s3` 和 `s2` 的内容也相同。语句 I 为假，因为 `s1` 和 `s2` 不是同一个引用。注意表达式 `s1 == s3` 将为真，因为 `s1` 和 `s3` *是*同一个引用。

###### 10. (D)
