

AP 考试使用的语言是 Java。考试只会测试 Java 语言的一个子集。不过，在编写自由回答题的解答时，你可以使用任何 Java 特性，包括那些不在 AP 子集中的特性。有关此子集的完整说明，请访问 College Board 网站。除非另有明确说明，否则本书中的每个语言主题都是 AP Java 子集的一部分。请注意，整个子集都在本书中涵盖了。

对于考试的选择题和自由回答题部分，附录中都会提供一份快速参考。你可以通过查阅 College Board 网站上的 "AP Computer Science A Java Quick Reference" 文档提前查看该参考。

## 诊断测试

后面的测试与实际 AP 考试使用的格式相同。你可以通过两种方式使用它：

1. 作为开始复习前的诊断测试。答案后附有一张诊断图表，将每道题目与你应复习的章节相关联。
2. 作为复习完成后的模拟测试。

选择题和自由回答题的每个解答都提供了完整的解释。

### 如何计算你的（近似）AP Computer Science A 分数

#### 选择题

![images](images/f004-01.jpg)

#### 自由回答题

![images](images/f004-02.jpg)

## 诊断测试

## COMPUTER SCIENCE A（计算机科学 A）

## SECTION I（第一部分）

**Time—1 hour and 30 minutes（时间——1 小时 30 分钟）**

**40 Questions（40 道题）**

**DIRECTIONS（说明）：** 确定以下各题或未完成陈述的答案，利用可用空间进行任何必要的草稿工作。然后判断所给选项中哪个是最佳答案，并在答题卡上填涂相应的椭圆。不要在任何一道题上花费太多时间。

**NOTES（注意）：**

* 假设快速参考中的类已在需要的地方导入。
* 假设变量和方法声明在包含类的上下文中。
* 假设没有对象或类名前缀的方法调用，且未显示在完整的类定义中，出现在包含类的上下文中。
* 假设方法调用中的参数不是 `null`，除非另有说明。

[1](#45_Chapter37.xhtml#fn0-1). 考虑这个继承层次结构，其中 `Novel` 和 `Textbook` 是 `Book` 的子类。

![images](images/f005-01.jpg)

关于图中所示类的以下陈述哪一项是错误的？

(A) `Textbook` 类可以拥有既不在 `Book` 也不在 `Novel` 中的私有实例变量。
(B) `Book`、`Novel` 和 `Textbook` 每个类都可以有一个 `computeShelfLife` 方法，其中 `Book` 和 `Novel` 中的代码相同，但与 `Textbook` 中的代码不同。
(C) 如果 `Book` 类有私有实例变量 `title` 和 `author`，则 `Novel` 和 `Textbook` 不能直接访问它们。
(D) `Novel` 和 `Textbook` 都继承 `Book` 中的构造器。
(E) 如果 `Book` 类有一个名为 `readFile` 的私有方法，则该方法不能在 `Novel` 或 `Textbook` 类中访问。

[2](#45_Chapter37.xhtml#fn0-2). 一位程序员正在设计一个程序来编目图书馆中的所有书籍。她计划创建一个 `Book` 类来存储每本书的特征：`author`、`title`、`isOnShelf` 等，并包含 `getAuthor`、`getTitle`、`getShelfInfo` 和 `setShelfInfo` 等操作。另一个类 `LibraryList` 将存储一个 `Book` 对象数组。`LibraryList` 类将包含 `listAllBooks`、`addBook`、`removeBook` 和 `searchForBook` 等操作。`LibraryList` 类和 `Book` 类之间是什么关系？

(A) 组合
(B) 继承
(C) 独立类
(D) 多态
(E) `ArrayList`

[3](#45_Chapter37.xhtml#fn0-3). 考虑以下代码段，其目的是在每次满足特定条件时向 `list` 末尾添加零。你可以假设 `list` 是一个包含至少一个元素的 `ArrayList<Integer>`。

![images](images/f006-01.jpg)

最可能发生以下哪种错误？

(A) `ArrayIndexOutOfBoundsException`
(B) `IndexOutOfBoundsException`
(C) `NullPointerException`
(D) `ConcurrentModificationException`
(E) `ArithmeticException`

第 4 题和第 5 题参考下面所示的 `Card` 和 `Deck` 类。

![images](images/f008-01.jpg)

[4](#45_Chapter37.xhtml#fn0-4). 以下哪项代表了 `Card` 类构造器中正确的 `/* implementation */` 代码？

(A) `suit = cardSuit; value = cardValue;`
(B) `cardSuit = suit; cardValue = value;`
(C) `Card = new Card(suit, value);`
(D) `Card = new Card(cardSuit, cardValue);`
(E) `suit = getSuit(); value = getValue();`

[5](#45_Chapter37.xhtml#fn0-5). 考虑添加到 `Deck` 类中的 `writeDeck` 方法的实现。

![images](images/f009-02.jpg)

以下哪项是正确的 `/* implementation code */`？

I. `System.out.println(deck);`
II. `for (Card card : deck) System.out.println(card);`
III. `for (Card card : deck) System.out.println((String) card);`

(A) 仅 I
(B) 仅 II
(C) 仅 III
(D) 仅 I 和 III
(E) 仅 II 和 III

[6](#45_Chapter37.xhtml#fn0-6). 参考以下在数组中查找最小值的方法。

![images](images/f010-01.jpg)

哪个替换 `/* some value */` 的选项将始终导致 `findMin` 方法正确执行？

I. `Integer.MIN_VALUE`
II. `Integer.MAX_VALUE`
III. `arr[0]`

(A) 仅 I
(B) 仅 II
(C) 仅 III
(D) 仅 I 和 III
(E) 仅 II 和 III

[7](#45_Chapter37.xhtml#fn0-7). 考虑以下循环，其中 `n` 是某个正整数。

![images](images/f011-01.jpg)

用 `n` 表示，哪个 Java 表达式代表 `/* perform some action */` 可能执行的最大次数？

(A) `n / 2`
(B) `(n + 1) / 2`
(C) `n`
(D) `n - 1`
(E) `(n - 1) / 2`

[8](#45_Chapter37.xhtml#fn0-8). 要编写一个方法来搜索数组中比给定项大的值并返回其索引。问题规范未说明如果数组中有多个这样的值应返回什么。以下哪种做法最好？

(A) 该方法应基于数组中只有一个值比给定项大的假设来编写。
(B) 该方法应编写为返回每个较大值出现的索引。
(C) 应修改规范，以说明如果存在多个较大值的索引该怎么办。
(D) 该方法应编写为如果找到多个较大值则输出一条消息。
(E) 该方法应编写为在返回合适的索引后删除所有后续的较大项。

[9](#45_Chapter37.xhtml#fn0-9). 方法 `whatIsIt` 在什么情况下会导致栈溢出（即耗尽计算机内存）？

![images](images/f012-01.jpg)

(A) 仅当 `x` < `y` 时
(B) 仅当 `x` ≤ `y` 时
(C) 仅当 `x` > `y` 时
(D) 对所有 `x` 和 `y` 的值
(E) 该方法永远不会导致栈溢出。

[10](#45_Chapter37.xhtml#fn0-10). 布尔表达式 `a[i] == max || !(max != a[i])` 可以简化为

(A) `a[i] == max`
(B) `a[i] != max`
(C) `a[i] < max || a[i] > max`
(D) `true`
(E) `false`

[11](#45_Chapter37.xhtml#fn0-11). 考虑以下代码段。

![images](images/f012-02.jpg)

执行代码段后 `sum` 的值是多少？

(A) 9
(B) 11
(C) 13
(D) 20
(E) 33

[12](#45_Chapter37.xhtml#fn0-12). 考虑一个具有无参构造器的 `Clown` 假设列表 `ArrayList<Clown> list` 已初始化。以下哪项不会导致抛出 `IndexOutOfBoundsException`？

(A) `for (int i = 0; i <= list.size(); i++) list.set(i, new Clown());`
(B) `list.add(list.size(), new Clown());`
(C) `Clown c = list.get(list.size());`

