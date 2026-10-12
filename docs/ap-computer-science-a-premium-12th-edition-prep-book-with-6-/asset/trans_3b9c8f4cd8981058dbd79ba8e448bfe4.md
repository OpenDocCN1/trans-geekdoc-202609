
[40](#56_Chapter48.xhtml#ff40).**(E)** 必须进行所有三项更改！为了将所有 `Card` 元素移动到临时 `ArrayList` 中，`for` 循环必须执行 `size` 次。如果从 `1` 开始让 `j` 循环，循环将只执行 `size-1` 次。第 7 行的错误比较隐蔽。随着循环的每次迭代，`cards ArrayList` 的大小减少 1，因此随机索引的范围变得越来越小。如果使用 `size`（即*原始* `cards` 列表的长度），就不会发生这种情况。你必须使用 `cards.size()`，即当前较短列表的长度。如果不进行更正 III，随机元素将不会从 `cards` 中移除。它将（错误地）保留在那里，而它的一个副本将被添加到 `temp` 中。如果不纠正此错误，执行该方法很可能会导致 `temp` 列表持有给定卡片的多个副本！

### 第二部分

[1](#56_Chapter48.xhtml#ffa1).![images](images/f373-01.jpg)

### 注意

• 对于 (b) 部分，通过第一个 `else if` 测试，所有少于 5 个字符的密码已被处理。通过第二个 `else if` 测试，所有少于 8 个字符的密码已被处理。因此，第二个 `else if` 测试仅处理具有 8 个或更多字符的密码，你无需显式测试字符数量。

### 评分标准：密码检查器

![images](images/f373-02.jpg)

[2](#56_Chapter48.xhtml#ffa2).![images](images/f374-01.jpg)

### 注意

• `Owl.getFood()` 方法被重写以展示 `SnowyOwl` 的特定进食习惯。

• 在构造器中，必须使用 `super`，因为无法直接访问 `Bird` 类的私有实例变量。新变量 `isMale` 必须在构造器中初始化。

• 注意 `Owl` 的噪音将始终是 `“hoot”`。因此，`SnowyOwl` 构造器中不需要将噪音作为参数提供。

### 评分标准：雪鸮

![images](images/f375-01.jpg)

[3](#56_Chapter48.xhtml#ffa3).![images](images/f375-02.jpg)

### 注意

• (b) 部分首先找到与参数匹配的名称，然后利用组成地址的接下来两行或三行构建一个字符串。同样，空字符串标志着地址的结束。

• 转义字符串 `“\n”` 在字符串中插入一个换行符。

### 评分标准：邮件列表

![images](images/f376-01.jpg)

[4](#56_Chapter48.xhtml#ffa4).![images](images/f375-02.jpg)

### 注意

• (a) 部分使用了 Java 的特性：二维数组是数组的数组。因此，每一行（即 `Contestant` 数组）都可以使用辅助方法 `sort` 进行排序。

• (b) 部分利用了这样一个事实：在对所有参赛者行进行排序后，获胜参赛者将位于参赛者矩阵的最后一列。当你遍历循环寻找比当前最大值更高的分数时，务必存储与该分数对应的姓名！

### 评分标准：二维竞赛组织器

![images](images/f377-01.jpg)

## 如何计算你的（近似）AP 计算机科学 A 分数

### 选择题

![images](images/f380-01.jpg)

### 简答题

![images](images/f380-02.jpg)

### 最终分数

![images](images/f380-03.jpg)

## [练习测试 2](#05_Contents.xhtml#rsec181)

## 计算机科学 A

## [第一部分](#05_Contents.xhtml#rsec182)

**时间——1 小时 30 分钟**

**40 道题**

**说明：** 确定以下各题或不完整陈述的答案，可利用可用空间进行必要的草稿工作。然后判断哪个是给定选项中最好的，并在答题卡上填涂相应的椭圆。不要在任何一道题上花费太多时间。

**注意：**

![](images/sq1.jpg) 假设快速参考中的类已在需要的地方导入。

![](images/sq1.jpg) 假设变量和方法声明在包含类的上下文中。

![](images/sq1.jpg) 假设没有对象或类名前缀、且未显示在完整类定义中的方法调用，出现在包含类的上下文中。

![](images/sq1.jpg) 假设方法调用中的参数不为 `null`，除非另有说明。

[1](#59_Chapter51.xhtml#ff1). 以下代码行产生什么输出？

`System.out.println(“\”This is\n very strange\””);`

(A) `\This is\n very strange\`

(B) `“This is very strange”`

(C) `This is very strange`

(D) `\“This is very strange\”`

(E) `“This is very strange”`

[2](#59_Chapter51.xhtml#ff2). 某个类 `SomeClass` 包含一个具有以下头部的方法。

`public int getValue(int n)`

假设现在向 `SomeClass` 添加了具有以下头部的方法。

I. `public int getValue()`

II. `public double getValue(int n)`

III. `public int getValue(double n)`

以下哪个头部会导致错误？

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 I 和 III

[3](#59_Chapter51.xhtml#ff3). 考虑以下语句。

`int num = /* expression */;`

以下哪项替换 `/* expression */` 可在 `num` 中创建一个 2 到 50（包括 2 和 50）之间的随机整数？

(A) `(int)(Math.random() * 50) - 2`

(B) `(int)(Math.random() * 49) - 2`

(C) `(int)(Math.random() * 49) + 2`

(D) `(int)(Math.random() * 50) + 2`

(E) `(int)(Math.random() * 48) + 2`

[4](#59_Chapter51.xhtml#ff4). 考虑以下代码段。

![images](images/f382-02.jpg)

执行此语句的结果是什么？

(A) 将抛出 `ArithmeticException`。

(B) 将发生语法错误。

(C) 将执行 `statement1`，但不执行 `statement2`。

(D) 将执行 `statement2`，但不执行 `statement1`。

(E) `statement1` 和 `statement2` 均不执行；控制权将传递给 `if` 语句之后的第一条语句。

[5](#59_Chapter51.xhtml#ff5). 以下洗牌算法用于打乱一个 `int` 值数组 `nums`。

![images](images/f383-01.jpg)

假设 `nums` 的初始状态为 `8`、`7`、`6`、`5`、`4`，执行方法时生成的 `randPos` 值依次为 `3`、`2`、`0`、`0`。执行后 `nums[2]` 将包含什么元素？

(A) `8`

(B) `7`

(C) `6`

(D) `5`

(E) `4`

[6](#59_Chapter51.xhtml#ff6). 考虑同一个类中的以下实例变量和 `assignValues` 方法。

![images](images/f383-03.jpg)

以下哪个代码段将正确地为 `mat` 中的每个槽位赋值 `100`？你可以假设实例变量均已正确初始化。

![images](images/f383-06.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 I 和 III

[7](#59_Chapter51.xhtml#ff7). 考虑以下继承层次结构。

![images](images/f384-01.jpg)

以下哪个声明不会导致错误？你可以假设上述每个类都有一个无参构造器。

I. `WheatCereal w = new Cereal();`

II. `Cereal c1 = new Cereal();`

III. `Cereal c2 = new RiceCereal();`

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 II 和 III

(E) I、II 和 III

第 8 和 9 题参考以下类定义。`public Class1`

![images](images/f385-01.jpg)

[8](#59_Chapter51.xhtml#ff8). 假设 `Class1`、`Class2` 和 `Class3` 都有无参构造器，以下哪项在客户端类中是有效的？

I. `Class1 c1 = new Class2();`

II. `Class2 c2 = new Class3();`

III. `Class1 c3 = new Class3();`

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) I、II 和 III

[9](#59_Chapter51.xhtml#ff9). 考虑客户端类中的以下声明。

![images](images/f385-07.jpg)

哪些方法调用是合法的？

I. `ob3.method1();`

II. `ob2.method3(ob3);`

III. `ob3.method3(ob2);`

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 II 和 III

(E) I、II 和 III

[10](#59_Chapter51.xhtml#ff10). 请参考以下程序段。

