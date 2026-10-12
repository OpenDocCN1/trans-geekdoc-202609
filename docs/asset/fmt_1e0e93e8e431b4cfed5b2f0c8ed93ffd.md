
![images](img/f340-01.jpg)

假设 `mat` 最初为

![images](img/f340-03.jpg)

方法调用 `printSomething(mat)` 后，输出将为

![images](img/f340-04.jpg)

(E) 将没有输出。将抛出 `ArrayIndexOutOfBoundsException`。

### 16. 考虑两种不同的存储非负整数集合的方式，其中没有重复项。

**方法一：** 将整数显式存储在一个数组中，其中元素数量是已知的。例如，使用此方法，集合 {6, 2, 1, 8, 9, 0} 可以表示如下。

![images](img/f341-01.jpg)

**方法二：** 假设整数的范围是 0 到 MAX。使用一个从 0 到 MAX 索引的布尔数组。索引值代表集合中可能的值。换句话说，从 0 到 MAX 的每个可能整数由数组中的不同位置表示。数组中的 true 值意味着相应的整数在集合中；false 值意味着该整数不在集合中。例如，使用此方法表示相同的集合 {6, 2, 1, 8, 9, 0}，表示如下（T = true，F = false）。

![images](img/f341-02.jpg)

将对整数集合执行以下操作。

I. 在集合中搜索目标值。

II. 打印集合的所有元素。

III. 返回集合中的元素数量。

哪个陈述是正确的？

(A) 如果集合使用方法一存储，操作 I 更高效。

(B) 如果集合使用方法二存储，操作 II 更高效。

(C) 如果集合使用方法一存储，操作 III 更高效。

(D) 操作 I 对方法一和方法二的效率相同。

(E) 操作 III 对方法一和方法二的效率相同。

### 17. 一个求 *N* 个数平均值的算法是

![images](img/f341-03.jpg)

其中 *N* 和 sum 都是整数。在一个使用此算法的程序中，程序员忘记包含一个检查 *N* 是否等于零的测试。如果 *N* 为零，何时会检测到错误？

(A) 编译时

(B) 编辑时

(C) 只要输入 *N* 的值

(D) 运行时

(E) 当输出不正确的结果时

### 18. 考虑一个包含 64 个不同 `int` 值的数组 `arr`，它们按升序排序。数组的第一个元素 `arr[0]` 等于 `5`，最后一个元素 `arr[63]` 等于 `200`。将使用二分查找算法来定位各种关键值。以下哪项是正确的陈述？

I. 如果 `5` 是关键值，将恰好需要 7 次搜索循环迭代来定位它。

II. 如果 `2` 是关键值，将恰好需要 7 次搜索循环迭代来确定 `2` 不在 `arr` 中。

III. 如果 `100` 是键，且 `100` 等于 `arr[62]`，则定位该键所需的搜索循环迭代次数将少于 7 次。

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 II 和 III

### 19. 考虑下面的 `getCount` 方法。

![images](img/f342-01.jpg)

方法调用 `getCount("a carrot and car", "car")` 将返回什么？

(A) `0`

(B) `1`

(C) `2`

(D) `3`

(E) 无返回值。该方法陷入无限循环。

### 20. 考虑一个处理不同车辆各种组件的程序。以下哪项是该程序可能包含的某些类之间关系的合理表示？注意：开放的向上箭头表示继承关系，向下箭头表示组合关系。

![images](img/f343-01.jpg)

### 21. 考虑以下程序段。

![images](img/f344-01.jpg)

以下哪项是该程序段的最佳后置条件？（你可以假设 `a[0]...a[-1]` 表示一个空数组。）

(A) `a[0]...a[n-1]` 不包含正整数。

(B) `a[0]...a[n-1]` 不包含负整数。

(C) `a[0]...a[n-1]` 不包含非负整数。

(D) `a[0]...a[n-1]` 不包含零。

(E) `n` 的更新值小于或等于执行该程序段前 `n` 的值。

### 22. 如果 `a`、`b` 和 `c` 是整数，以下哪个条件足以保证表达式

![images](img/f344-07.jpg)

的值为 true？

(A) `a < c`

(B) `a < b`

(C) `a > b`

(D) `a == b`

(E) `a == c`

### 23. Airmail Express 按重量的整数值收取小包裹运费。重量为 *w* 磅的包裹收费标准如下。

![images](img/f344-08.jpg)

该公司不接受重量超过 20 磅的包裹。以下哪项代表了测试计算运费程序的最佳数据集（重量）？

(A) 0, 2, 5, 20

(B) 1, 4, 16

(C) -1, 1, 2, 3, 5, 16, 20

(D) -1, 0, 1, 2, 3, 5, 16, 20, 22

(E) 从 -1 到 22 的所有整数

### 24. 考虑同一个类中的以下实例变量和方法。

![images](img/f345-01.jpg)

假设 `matrix` 当前的值为

![images](img/f345-02.jpg)

在同一个类中，以下方法调用将返回什么？

![images](img/f345-03.jpg)

(A) `9`

(B) `8`

(C) `7`

(D) `4`

(E) 编译时错误。无返回值。

---

### Questions 25–26

基于以下类声明。

![images](img/f346-01.jpg)

### 25. 本题涉及下面的 `findCheapest` 方法，该方法位于一个拥有 `AutoPart` 数组作为私有数据字段的类中。

![images](img/f347-01a.jpg)

`findCheapest` 方法检查一个 `AutoPart` 数组，并返回描述与 `partDescription` 参数匹配且价格最低的 `AutoPart` 的零件编号。例如，多个 `AutoPart` 元素的描述字段可能都是 `"headlight"`。不同的大灯在价格和零件编号上均有差异。如果 `partDescription` 参数是 `"headlight"`，则 `findCheapest` 将返回最便宜大灯的零件编号。

![images](img/f347-01.jpg)

以下哪项可替换 `/*` **more code** `*/` 以找到正确的零件编号？

![images](img/f347-03.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 I 和 III

### 26. 考虑以下方法。

![images](img/f348-01.jpg)

同一个类中的一个方法包含以下声明。

![images](img/f348-02.jpg)

以下哪条语句会导致错误？

![images](img/f348-03.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 II 和 III

### 27. 本题基于以下声明。

![images](img/f348-07.jpg)

已知在字母顺序中所有大写字母都在小写字母之前，以下哪项为真？

(A) `strA.compareTo(strB) < 0 && strB.compareTo(strC) > 0`

(B) `strC.compareTo(strB) < 0 && strB.compareTo(strA) < 0`

(C) `strB.compareTo(strC) < 0 && strB.compareTo(strA) > 0`

(D) `!(strA.compareTo(strB) == 0) && strB.compareTo(strA) < 0`

(E) `!(strA.compareTo(strB) == 0) && strC.compareTo(strB) < 0`

### 28. 一位程序员有一个姓名文件。她正在设计一个程序，向列表上的每个人发送垃圾邮件。为了让信件听起来个性化且友好，她将从姓名字符串中提取每个人的名。她计划创建一个仅包含名的并行文件。例如，

![images](img/f349-01.jpg)

这是一个旨在从全名字符串中提取名的方法。

![images](img/f349-02.jpg)

![images](img/f349-03.jpg)

以下哪项代表了正确的 `/*` **code to extract first name** `*/`？

![images](img/f349-05.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) I、II 和 III

---

### Questions 29–31

参考下面的 `ThreeDigitInteger` 和 `ThreeDigitCode` 类。

![images](img/f350-01.jpg)

![images](img/f350-02.jpg)

### 29. 关于所示类，以下哪项陈述是正确的？

(A) `ThreeDigitInteger` 类从 `ThreeDigitCode` 类继承了 `isValid` 方法。

(B) `ThreeDigitCode` 类从 `ThreeDigitInteger` 类继承了所有公共访问器方法。

(C) `ThreeDigitCode` 类从 `ThreeDigitInteger` 类继承了构造器。

(D) `ThreeDigitCode` 类可以直接访问 `ThreeDigitInteger` 类的所有私有变量。

(E) `ThreeDigitInteger` 类可以访问 `ThreeDigitCode` 类的 `isValid` 实例变量。

### 30. 以下哪项是 `ThreeDigitCode` 构造器的正确 `/*` **implementation code** `*/`？

![images](img/f351-01a.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 III

(E) I、II 和 III

### 31. 参考客户端程序中的以下声明。

![images](img/f351-03.jpg)

以下哪项后续测试不会导致错误？

![images](img/f351-02.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 I 和 III

### 32. 考虑一个类层次结构。

![images](img/f352-01.jpg)

假设每个类都有一个有效的无参构造器，以下哪项在客户端程序中的声明是正确的？

![images](img/f352-02.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 II 和 III

(E) I、II 和 III

### 33. 考虑一个数组 `arr` 和一个列表 `list`（类型为 `ArrayList<String>`）。`arr` 和 `list` 均已用字符串值初始化。以下哪个代码段能正确地将 `arr` 中的所有字符串追加到 `list` 的末尾？

![images](img/f352-03.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 III

(E) I、II 和 III

### 34. 参考下面的 `nextIntInRange` 方法。

![images](img/f353-01.jpg)

哪个 `/*` **expression** `*/` 将始终返回满足后置条件的值？

(A) `(int) (Math.random() * high) + low;`

(B) `(int) (Math.random() * (high - low)) + low;`

(C) `(int) (Math.random() * (high - low + 1)) + low;`

(D) `(int) (Math.random() * (high + low)) + low;`

(E) `(int) (Math.random() * (high + low - 1)) + low;`

### 35. 考虑同一个 `Sorter` 类中的以下 `mergeSort` 方法和私有实例变量 `a`。

![images](img/f353-02.jpg)

方法 `mergeSort` 调用方法 `merge`，其方法头如下。

![images](img/f353-03.jpg)

如果对 `mergeSort` 的首次调用是 `mergeSort(0,3)`，在数组 `b[0]...b[3]` 排序完成之前，将会有多少次对 `mergeSort` 的**进一步**调用？

(A) 2

(B) 3

(C) 4

### 选择题

### 36. 一家大型医院维护一份无特定顺序的患者记录列表。要查找给定患者的记录，以下哪种方法是可行的最高效方法？

(A) 在记录的姓名字段上进行顺序查找。

(B) 在记录的姓名字段上进行二分查找。

(C) 使用插入排序按姓名按字母顺序对记录排序；然后在记录的姓名字段上进行顺序查找。

(D) 使用归并排序按姓名按字母顺序对记录排序；然后在记录的姓名字段上进行顺序查找。

(E) 使用归并排序按姓名按字母顺序对记录排序；然后在记录的姓名字段上进行二分查找。

### 37-38 题背景信息

下图展示了用于绘制带有块字母横幅的程序中部分类之间的关系。

![images](img/f354-01.jpg)

图示表明 `Banner` 类使用 `BlockLetter` 对象，且 `BlockLetter` 类有 26 个子类，分别代表从 A 到 Z 的块字母。

![images](img/f354-01a.jpg)

每个子类都以独特的方式实现 `draw` 方法来绘制其特定的字母。`Banner` 类获取一个 `BlockLetter` 数组，并拥有一个绘制该数组中所有字母的方法。

以下是 `Banner` 类的部分实现。

![images](img/f354-02.jpg)

![images](img/f355-01.jpg)

### 37. 已知 `Banner` 和 `BlockLetter` 是程序中使用的两个类。以下哪项结论关于这些类是正确的？

I. `BlockLetter` 继承 `Banner` 的所有方法。

II. `Banner` 至少包含一个 `BlockLetter` 对象。

III. 每个子类 `LetterA`、`LetterB`、`LetterC` ... `LetterZ` 都有一个被重写的 `draw` 方法。

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) II 和 III

(E) I、II 和 III

### 38. 关于 `drawLetters` 方法，以下哪项陈述是正确的？

(A) 它是 `Banner` 类中的一个重载方法。

(B) 它是 `Banner` 类中的一个重写方法。

(C) 它利用多态性来绘制正确的字母。

(D) 它会导致逻辑错误，因为 `BlockLetter` 类的 `draw` 方法与其子类的 `draw` 方法不同。

(E) 它会导致运行时错误，因为 `Banner` 类中没有 `draw` 方法。

### 39. 观察下面的 `method1` 和 `method2`，它们除了倒数第二行代码外完全相同。每个方法都根据输入矩阵 `mat` 返回一个新矩阵。

![images](img/f356-01.jpg)

![images](img/f356-01r.jpg)

假设 `method1` 和 `method2` 使用相同的输入矩阵，`method1` 的输出为 `matrix1`，`method2` 的输出为 `matrix2`。关于 `matrix1` 和 `matrix2`，以下哪项陈述是正确的？

(A) `matrix1` 与 `matrix2` 相同。

(B) `matrix1` 的行是 `matrix2` 的列。

(C) `matrix1` 是 `matrix2` 关于任一矩阵边缘垂直线的反射。

(D) `matrix1` 是 `matrix2` 关于任一矩阵底部或顶部边缘水平线的反射。

(E) `matrix1` 的行是 `matrix2` 的行的逆序。

### 40. 考虑一个需要洗牌的 `Card` 对象 `ArrayList cards`。使用以下算法进行洗牌。

![images](img/f357-01.jpg)

以下是实现该算法的方法。

![images](img/f357-02.jpg)

该方法无法按预期工作。对 `shuffle` 进行以下哪项更改可确保其正确工作？

![images](img/f357-03.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) I 和 III

(E) I、II 和 III

**第一部分结束**

## 计算机科学 A

### 第二部分

**时间——1 小时 30 分钟**

**4 道题**

**说明：** 展示所有解题过程。请记住，程序段必须用 Java 编写。

将答案写在单独提供的自由回答答题册中。

### 注意事项：

![images](img/sq1.jpg) 假设快速参考中的类已在适当处导入。

![images](img/sq1.jpg) 除非题目另有说明，假设方法调用中的参数不为 `null`，且方法仅在满足前置条件时被调用。

![images](img/sq1.jpg) 在编写每道题的解答时，可以使用该题中定义的类中列出的所有可访问方法。编写大量可被调用这些方法之一替代的代码将无法获得满分。

### 1
