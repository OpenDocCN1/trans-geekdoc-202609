

(D) `Clown c = list.remove(list.size());`

(E) `list.add(-1, new Clown());`

请参考以下类来回答第 13 和 14 题。

![images](images/f014-01.jpg)

[13](#45_Chapter37.xhtml#fn0-13). 对 `Tester` 对象调用 `firstTestMethod` 将产生什么输出？

(A) `3 4 5`

(B) `4 5 6`

(C) `5 6 7`

(D) `0 0 0`

(E) 不会产生输出。将抛出 `ArrayIndexOutOfBoundsException`。

[14](#45_Chapter37.xhtml#fn0-14). 假设 `testArray` 包含 `3,4,5`，对 `Tester` 对象调用 `secondTestMethod` 将产生什么输出？

(A) `3 4 5`

(B) `4 5 6`

(C) `5 6 7`

(D) `0 0 0`

(E) 不会产生输出。将抛出 `ArrayIndexOutOfBoundsException`。

第 15-17 题参考以下 `Point`、`Quadrilateral` 和 `Rectangle` 类。

![images](images/f015-01.jpg)

![images](images/f016-01.jpg)

[15](#45_Chapter37.xhtml#fn0-15). 关于 `Point`、`Quadrilateral` 和 `Rectangle` 类，以下哪些陈述是错误的？

I. `Point` 是 `Quadrilateral` 的子类。

II. `Point` 是 `Rectangle` 的子类。

III. `Rectangle` 类继承了 `Quadrilateral` 的构造方法。

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) I、II 和 III

[16](#45_Chapter37.xhtml#fn0-16). 以下哪项代表 `Rectangle` 构造方法的正确 `/* implementation code */`？

I. `super(theLabels);`

II. `super(theLabels, theTopLeft, theBotRight);`

III. `super(theLabels); topLeft = theTopLeft; botRight = theBotRight;`

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 II 和 III

[17](#45_Chapter37.xhtml#fn0-17). 请参考下面的 `Parallelogram` 和 `Square` 类。

![images](images/f017-01.jpg)

考虑一个 `ArrayList<Quadrilateral> quadList`，其元素类型为 `Rectangle`、`Parallelogram` 或 `Square`。

请参考以下方法 `writeAreas`：

![images](images/f017-02.jpg)

执行此方法会产生什么效果？

(A) 将打印 `quadList` 中每个 `Quadrilateral` 的面积。

(B) 将为 `quadList` 的每个元素打印值 `0`。

(C) 将发生编译时错误，指出在 `Rectangle`、`Parallelogram` 或 `Square` 类中没有 `getLabels` 方法。

(D) 将抛出 `NullPointerException`。

(E) 将发生 `ConcurrentModificationException`。

[18](#45_Chapter37.xhtml#fn0-18). 请参考下面的 `doSomething` 方法。

![images](images/f018-01.jpg)

以下哪项最能描述 `doSomething` 的**后置条件**？

(A) 从 `list` 中移除索引为 `i` 和 `j` 的对象

(B) 在 `list` 中用索引为 `j` 的对象替换索引为 `i` 的对象

(C) 在 `list` 中用索引为 `i` 的对象替换索引为 `j` 的对象

(D) 在 `list` 中用 `temp` 替换索引为 `i` 和 `j` 的对象

(E) 在 `list` 中交换索引为 `i` 和 `j` 的对象

[19](#45_Chapter37.xhtml#fn0-19). 请考虑下面的 `NegativeReal` 类，它定义了一个负实数对象。

![images](images/f019-01.jpg)

以下是一些舍入示例：

![images](images/f019-02.jpg)

哪个 `/* implementation */` 的 `getRounded` 能产生所需的后置条件？

(A) `return (int) (getValue() - 0.5);`

(B) `return (int) (getValue() + 0.5);`

(C) `return (int) getValue();`

(D) `return (double) (getValue() - 0.5);`

(E) `return (double) getValue();`

[20](#45_Chapter37.xhtml#fn0-20). 请考虑以下方法。

![images](images/f020-01.jpg)

方法调用 `whatsIt(347)` 的输出结果将是什么？

(A) `74`

(B) `47`

(C) `734`

(D) `743`

(E) `347`

[21](#45_Chapter37.xhtml#fn0-21). 一个大量数字列表需要按升序排序。假设“数据移动”是指元素的交换或重新赋值，以下哪项陈述是正确的？

(A) 如果数组最初按降序排序，则插入排序将比选择排序更高效。

(B) 选择排序的比较次数与元素的初始排列无关。

(C) 插入排序的比较次数与元素的初始排列无关。

(D) 选择排序中的数据移动次数取决于元素的初始排列。

(E) 插入排序中的数据移动次数与元素的初始排列无关。

[22](#45_Chapter37.xhtml#fn0-22). 请参考下面 `ClassOne` 和 `ClassTwo` 的定义。

![images](images/f021-01.jpg)

请考虑客户端类中的以下声明。你可以假设 `ClassOne` 和 `ClassTwo` 都有无参构造方法。

`ClassOne c1 = new ClassOne();`

`ClassOne c2 = new ClassTwo();`

以下哪个方法调用会导致错误？

I. `c1.methodTwo();`

II. `c2.methodTwo();`

III. `c2.methodOne();`

(A) 无

(B) 仅 I

(C) 仅 II

(D) 仅 III

(E) 仅 I 和 II

[23](#45_Chapter37.xhtml#fn0-23). 请考虑代码段

![images](images/f022-01.jpg)

假设给定片段被重写为以下形式

![images](images/f022-02.jpg)

已知 `n` 和 `k` 为整数，且重写后的代码执行与原代码相同的任务，以下哪项可用作

![images](images/f022-03.jpg)

[24](#45_Chapter37.xhtml#fn0-24). 以下哪项将**不**抛出异常即可执行？

![images](images/f022-04.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 II 和 III

[25](#45_Chapter37.xhtml#fn0-25). 如果三个数 *a*、*b* 和 *c* 中有两个数的平方和等于第三个数的平方，则称这三个数为*勾股数*。程序员编写了一个方法 `isPythTriple` 来测试其三个参数是否构成勾股数：

![images](images/f023-01.jpg)

当使用已知的勾股数测试该方法时，`isPythTriple` 有时会错误地返回 `false`。导致该错误最可能的原因是什么？

(A) 由浮点数计算引起的舍入误差。

(B) 过时版本的 Java 无法识别 `boolean` 类型。

(C) 因输入数字过大而导致的溢出错误。

(D) 在测试相等性之前，`c` 和 `d` 应先强制转换为整数。

(E) 选择了不良的测试数据。

[26](#45_Chapter37.xhtml#fn0-26). 请参考包含 `mystery` 方法的以下类。

![images](images/f023-02.jpg)

以下哪项最能描述 `mystery` 方法的功能？

(A) 它对 `arr` 的元素求和。

(B) 它对乘积 `10*arr[0]` + `10*arr[1]` + ••• + `10*arr[arr.length-1]` 求和。

(C) 它构建一个形式为 *d*[1]*d*[2]*d*[3] ... *d[n]* 的整数，其中 *d*[1] = `arr[0]`，*d*[2] = `arr[1]`，...，*d[n]*[] = `arr[arr.length-1]`。

(D) 它构建一个形式为 *d*[1]*d*[2]*d*[3] ... *d[n]* 的整数，其中 *d*[1] = `arr[arr.length-1]`，*d*[2] = `arr[arr.length-2]`，...，*d[n]*[] = `arr[0]`。

(E) 它将 `arr` 的元素转换为十进制。

第 27 和 28 题参考下面 `Searcher` 类中的 `search` 方法。

![images](images/f024-01.jpg)

[27](#45_Chapter37.xhtml#fn0-27). 在每次执行 `while` 循环之前，以下哪个断言为真？

(A) `arr[first]` < `key` < `arr[last]`

(B) `arr[first]` ≤ `key` ≤ `arr[last]`

(C) `arr[first]` < `key` < `arr[last]` 或 `key` 不在 `arr` 中

(D) `arr[first]` ≤ `key` ≤ `arr[last]` 或 `key` 不在 `arr` 中

(E) `key` ≤ `arr[first]` 或 `key` ≥ `arr[last]` 或 `key` 不在 `arr` 中

[28](#45_Chapter37.xhtml#fn0-28). 考虑数组 `a`，其值为

4, 7, 19, 25, 36, 37, 50, 100, 101, 205, 220, 271, 306, 321

其中 4 是 `a[0]`，321 是 `a[13]`。假设使用 `first` = `0` 和 `last` = `13` 调用 `search` 方法来查找 `key` 205。为了找到它，必须执行 `while` 循环多少次迭代？

(A) 3

(B) 4

(C) 5

(D) 10

(E) 13

[29](#45_Chapter37.xhtml#fn0-29). 请考虑以下 `RandomList` 类。

![images](images/f025-01.jpg)

哪项代表正确的 `/* code to add integer to list */`？

(A) `list[i] = (int) (Math.random() * 101);`

(B) `list.add((int) (Math.random() * 101));`

