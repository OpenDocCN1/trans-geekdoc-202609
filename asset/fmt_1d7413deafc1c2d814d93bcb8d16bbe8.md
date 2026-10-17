
- [一般问题：给定一支棒球队的球员名单，找出球队的打击率。](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**理查德·费曼**。

**精炼问题**：你得到一份棒球运动员的列表。每个棒球运动员知道自己的安打数和上垒次数。球队平均值是先计算安打总数和上垒次数总和，然后用总安打数除以总上垒次数得到的。编写一个方法，计算球队的打击率。

**最终问题**：编写一个名为 `findTeamAverage` 的方法，它接受一个 `BaseballPlayer` 数组作为参数。该方法应返回一个 `double`，表示球队的打击率。通过将总安打数除以总上垒次数来计算球队平均值。确保在处理玩家之前先检查玩家是否存在。此外，在计算球队平均值之前，要检查对零的检查。如果球队的总上垒次数为 0，则返回球队打击率为 0.0。最后，使你的算法适应于处理 `ArrayList` 的 `BaseballPlayer` 对象。

**算法**：

步骤 1：创建一个名为 `totalHits` 的变量，并将其设置为 0。

步骤 2：创建一个名为 `totalAtBats` 的变量，并将其设置为 0。

步骤 3：查看名单上的每个球员。

步骤 4：获取球员的安打数，并将其加到 `totalHits` 上。

步骤 5：获取球员的上垒次数，并将其加到 `totalAtBats` 上。

步骤 6：继续，直到到达列表的末尾。

步骤 7：通过将 `totalHits` 除以 `totalAtBats` 计算 `teamBattingAverage`。

步骤 8：返回 `teamBattingAverage`。

**伪代码**：

![Image](img/f0249-01.jpg)

**Java 代码 1：使用 `ArrayList`（`for` 循环）的 Java 代码**

![Image](img/f0247-01.jpg)

**Java 代码 2：使用 `ArrayList`（`for-each` 循环）的 Java 代码**

![Image](img/f0247-02.jpg)

![Image](img/f0248-01.jpg)

### 高级算法：寻找最高分

**一般问题**：给定一支棒球队的球员名单，找出打击率最高的球员姓名。

**精炼问题**：你得到一份棒球运动员的列表。每个棒球运动员都知道如何计算自己的打击率。编写一个方法，计算列表中每个球员的打击率，并找出打击率最高的球员姓名。

**最终问题**：编写一个名为 `findBestPlayer` 的方法，它接受一个 `BaseballPlayer` 数组作为参数。该方法应返回一个字符串，表示打击率最高的球员姓名。确保在处理玩家之前先检查玩家是否存在。如果两名球员的打击率相同且最高，只选择第一个球员。此外，使你的算法适应于处理 `ArrayList` 的 `BaseballPlayer` 对象。

**注意**：我们将使用前面的示例中的 `BaseballPlayer` 类。

**算法**：

步骤 1：创建一个名为 `highestAverage` 的变量，并将其赋予一个非常小的数值。

步骤 2：创建一个名为 `bestPlayer` 的变量，并将其赋予空字符串。

步骤 3：查看名单上的每个球员。

步骤 4：如果球员的打击率大于 `highestAverage`，则将 `highestAverage` 设置为该球员的平均值，并将 `bestPlayer` 设置为该球员的姓名。

步骤 5：继续，直到到达列表的末尾。

步骤 6：返回 `bestPlayer` 的姓名。

**伪代码**：

![Image](img/f0249-01.jpg)

**Java 代码 1：返回打分最高的一个球员**

![Image](img/f0249-02.jpg)

**Java 代码 2：返回每个打分最高的球员**

![Image](img/f0250-01.jpg)

`示例：Runner 程序`

![Image](img/f0250-02.jpg)

![Image](img/f0251-01.jpg)

### Twitter 情感分析高级算法

Twitter 非常流行，Twitter 情感分析也日益流行。Twitter 情感分析的核心是从推文中提取情绪或得出结论。大量的推文可以用来对人们对某事物的感受做出一般性结论。推文中重要的词汇会与词库中的词汇进行比对，从而为推文赋予情感评分。

处理推文的第一步是删除所有不添加实质意义的词汇。这些词汇被称为**停用词**，这一步通常属于**预处理**阶段。对于本题，你的任务是从推文中删除所有停用词。虽然有许多方法可以找到无意义的词汇，但在此示例中，停用词是指长度为三个字符或更少的所有词汇。

**一般问题**：给定一条推文，删除所有无意义的词汇。

**精炼问题**：你得到一条推文作为单词列表。找出列表中长度大于三个字符的所有词汇，并将它们添加到新列表中。保持原始推文不变。新列表将包含所有非停用词。

**最终问题**：编写一个名为 `removeStopWords` 的方法，它接受一个 `ArrayList` 的 `String` 作为参数。该方法应返回一个新的 `ArrayList` 的 `String`，仅包含长度大于三个字符的原始列表中的单词。不要修改原始 `ArrayList`。同时，修改代码以适应于处理 `String` 数组。

#### 解决方案 1：使用 `ArrayList`

**算法 1**：

步骤 1：创建一个名为 `longWords` 的列表。

步骤 2：查看原始列表中的每个单词。

步骤 3：如果单词长度大于三个字符，将该单词添加到 `longWords` 中。

步骤 4：继续，直到到达原始列表的末尾。

步骤 5：返回 `longWords`。

**伪代码 1**：

![Image](img/f0251-02.jpg)

##### Java 代码 1：使用 `ArrayList`（`for-each` 循环）的 Java 代码

![Image](img/f0252-01.jpg)

#### 解决方案 2：使用数组

此解决方案比 `ArrayList` 解决方案需要更多工作，因为我们不知道数组的大小，需要在创建它之前统计长度大于三个字符的单词数量。

**算法 2**：

步骤 1：创建一个计数器，并将其设置为零。

步骤 2：查看原始列表中的每个单词。

步骤 3：如果单词长度大于三个字符，则将计数器加一。

步骤 4：继续，直到到达列表的末尾。

步骤 5：创建一个名为 `longWords` 的数组，长度等于计数器。

步骤 6：创建一个变量，用于作为 `longWords` 的索引，并将其设置为零。

步骤 7：查看原始列表中的每个单词。

步骤 8：如果单词长度大于三个字符，则将单词添加到 `longWords`，并将用于 `longWords` 的索引加一。

步骤 9：继续，直到到达列表的末尾。

步骤 10：返回 `longWords` 数组。

**伪代码 2**：

![Image](img/f0252-02.jpg)

##### Java 代码 2：使用数组（使用 `for-each` 循环和 `for` 循环）的 Java 代码

![Image](img/f0253-01.jpg)

### 示例

使用 `ArrayList`：

![Image](img/f0253-02.jpg)

**最终问题**：编写一个名为 `searchForTitle` 的方法，该方法包含两个参数：一个字符串数组和一个表示搜索目标的字符串。该方法应在找到目标字符串时返回其索引，未找到时返回 -1。注意：我提供了两种解决方案并随后比较它们的效率。

![Image](img/power.jpg)

**搜索目标**

当你在列表中查找特定项目时，你要找的项目通常被称为搜索目标。如果目标未找到，通常会返回 -1 的值。

#### 解决方案 1：遍历列表中的每一项。

**算法 1：**

步骤 1：创建一个名为 `foundIndex` 的变量，并将其设置为 -1。

步骤 2：逐个查看数组中的标题。

步骤 3：将每个标题与目标标题进行比较。

步骤 4：如果标题等于目标标题，则将 `foundIndex` 设置为当前索引的值。

步骤 5：继续查找直到到达列表的末尾。

步骤 6：返回 `foundIndex` 的值。

**伪代码 1：**

![Image](img/f0254-01.jpg)

##### Java 代码

![Image](img/f0255-01.jpg)

你是否注意到例子中使用了 for 循环？这有意为之。记住，如果你需要访问数组或 `ArrayList` 中元素的索引，则不能使用 foreach 循环。

#### 解决方案 2：找到搜索目标后停止查找。

**算法 2：**

步骤 1：逐个查看数组中的标题。

步骤 2：将搜索目标与每个标题进行比较。

步骤 3：如果标题等于目标标题，则停止查找并返回当前索引。

步骤 4：继续查找直到到达列表的末尾。

步骤 5：返回 -1。

**伪代码 2：**

![Image](img/f0255-02.jpg)

**Java 代码**

![Image](img/f0256-01.jpg)

#### 效率

分析用于查找歌曲标题的两种解决方案。

第二种算法比第一种算法 *更高效*，因为该方法在找到目标标题后立即停止查找。第一种算法比第二种算法 *效率更低*，因为它在找到目标标题后仍继续比较列表中的每个标题与搜索目标。

**效率**

高效的算法在最快的方式下完成工作。高效的程序会优化 CPU（中央处理单元）时间和内存使用。

### 数据排序

排序的概念对于人类来说很容易理解。相比之下，教会计算机自己对项目进行排序可能是一个挑战。多年来，数百种排序算法被开发，并且它们都因效率和内存使用而受到批评。AP 计算机科学 A 考试要求你能够阅读和分析使用三种主要排序算法的代码：插入排序、选择排序和合并排序（将在 Unit 10 讨论）。

最重要的是要记住，不同的排序算法适用于不同的情况。有些算法易于编写，有些算法能高效利用 CPU，有些算法能高效利用内存，有些算法擅长在已排序列表中添加元素，有些则不在乎列表是否已排序。在我们这三种算法中，合并排序是最快的，但它使用的内存最多。

#### 交换算法

回顾 Unit 6 中学到的交换算法：Array。它在某些排序算法中被使用。

![Image](img/power.jpg)

### AP 计算机科学 A 考试上的排序算法

你不需要在 Free-Response Section（自由回答部分）中编写任何排序例程的完整代码。但是，你应该理解每种算法的工作原理，因为它们可能会出现在选择题中。

### 插入排序

**插入排序** 算法类似于人们自然对数字列表进行排序的方式。例如，如果你一张张给人数字卡片，这个人可以边接收卡片边立即将卡片插入到正确的位置，从而“边排序”。插入排序被认为是相对简单的排序，并且在非常小的数据集上效果最好。

编写能够自动化此过程的代码需要一个进行大量比较的算法。让我们用一个例子展示插入排序如何对数字列表从小到大进行排序。

![Image](img/f0257-01.jpg)

该算法使用一个临时变量，我称之为 `temp`。第一步是将第二位置的数字放入临时变量 (`temp`)。然后比较 `temp` 与第一位置的数字。如果 `temp` 小于第一位置的数字，则将第一位置的数字移动到第二位置，并将 `temp` 放入第一位置。第一次遍历完成，前两个数字已从小到大排序。

接下来，将第三位置的数字放入 `temp`。比较 `temp` 与列表中第二位置的数字。如果 `temp` 小于第二位置的数字，则将第二位置的数字移动到第三位置，并比较 `temp` 与第一位置的数字。如果 `temp` 小于第一位置的数字，则将第一位置的数字移动到第二位置，并将 `temp` 移动到第一位置。第二次遍历完成，列表的前三个数字已从小到大排序。继续此过程，直到最后一个数字与其他所有数字比较并插入到正确的位置。

**一次遍历**

在编程中，**一次遍历** 是一个过程的一个迭代。这些排序算法在完成排序前会进行一系列的遍历。

高效的算法使用最少的遍历次数。

#### 实现

以下类包含一个方法，该方法使用插入排序算法对整数数组从小到大进行排序。注意，也可以使用 `ArrayList`。还需注意，数组/ArrayList 可以存储任何类型的数据。下面的例子使用 int 类型。

![Image](img/f0258-01.jpg)

### 选择排序

**选择排序** 算法通过反复查找列表中的最小项并将其放入其正确位置来形成一个已排序的列表。

![Image](img/f0259-01.jpg)

要使用选择排序对数字列表从小到大进行排序，请遍历整个列表以查找最小项，选择它，并将其与列表的第一项进行交换（这两个数字交换位置）。这完成了第一次遍历。接下来，在不包括第一项的剩余列表中查找最小项，选择它，并将其与第二位置的项进行交换。这完成了第二次遍历。然后，在不包括第一项和第二项的剩余列表中查找最小项，选择它，并将其与第三位置的项进行交换。重复此过程，直到列表的最后一项成为（自动）列表中的最大项。

#### 实现

以下类包含一个方法，该方法使用选择排序算法对整数数组从小到大进行排序。注意，也可以使用 `ArrayList`。还需注意，数组/ArrayList 可以存储任何类型的数据。下面的例子使用 int 类型。

![Image](img/f0260-01.jpg)

![Image](img/arrow1.jpg) **快速回顾**

#### `ArrayList`

• `ArrayList` 是一个复杂的数据结构，可以存储对象列表。

• 声明 `ArrayList` 的两种常见形式：

![Image](img/f0260-03.jpg)

• `ArrayList` 只能存储对象列表，不能存储原始数据类型。

• 使用 `Integer` 或 `Double` 类来创建 `int` 或 `double` 值的 `ArrayList`。

• `ArrayList` 的初始大小为 0。

• `add(E object)` 方法将对象追加到 `ArrayList` 的末尾。它还返回 true。

• “追加”意味着将项目添加到列表的末尾。

• The `add(int index, E object)` 方法在指定位置 **index**（注意：index 必须在 [0,size] 范围内）插入对象 **object**。插入后，位于 **index** 及其后的元素会向 0 索引方向移动 1 个索引位置。

• The `get(int index)` 方法返回索引 **index** 处的对象的引用。

• The `set(int index, E object)` 方法将位置 **index** 的元素替换为 **object**，并返回原来位于 **index** 的元素。

• The `remove(int index)` 方法删除位置 **index** 的元素，随后将 **index + 1** 及其以后元素的索引各减 1，并返回被删除的元素。

• The `size()` 方法返回当前 `ArrayList` 中元素的数量。

• `ArrayList` 的大小会随着元素的添加或删除而增长或缩小。

• `size()` 方法会随元素的增删而相应调整。

• 使用超出 `ArrayList` 范围的索引会抛出 `IndexOutOfBoundsException`。

• `ArrayList` 需要导入语句，因为它不在标准库中，但这在 AP Computer Science A 考试中永远不会被要求。

#### Traversing an `ArrayList`

• 遍历 `ArrayList` 意味着访问列表中的每个元素。

• 虽然有很多遍历方式，但最常用的是从头开始、逐个访问直到列表末尾。

• 使用普通 `for` 循环遍历时，需要调用 `get()` 方法来获取每个元素。

• 使用增强 `for` 循环遍历时，不需要调用 `get()`，因为循环会自动按顺序取出每个对象。

• 若需从 `ArrayList` 中删除元素，建议从列表末尾开始遍历并向前移动。

#### Sequential (or Linear) Search Algorithm

• 顺序搜索算法在列表中按顺序查找目标元素。

• 它逐个比较列表中的每个元素与搜索目标。

• 找到目标时，返回其下标。

• 未找到时通常返回 -1。

#### Insertion Sort

• 插入排序算法通过反复比较列表中下一个数与已排序部分的数，并将其插入到适当位置来实现排序。

#### Selection Sort

• 选择排序算法通过反复找出列表中最小的数并与当前元素交换来实现排序。

### ![Image](img/arrow1.jpg)Review Questions

## Basic Level

**1.** Assume that `cities` is an `ArrayList<String>` that has been correctly constructed and populated with the following items.

![Image](img/f0262-01.jpg)

Consider the following code segment.

```
cities.remove(2);
cities.add("Detroit");
cities.remove(4);
cities.add("Cleveland");
```

What items does `cities` contain after executing the code segment?

![Image](img/f0262-02.jpg)

**2.** Consider the following code segment.

```
ArrayList<String> subjects = new ArrayList<String>();
subjects.add("French");
subjects.add("History");
subjects.set(1, "English");
subjects.add("Art");
subjects.remove(1);
subjects.set(2, "Math");
subjects.add("Biology");
System.out.println(subjects);
```

What is printed as a result of executing the code segment?

![Image](img/f0262-03.jpg)

Questions 3-6 refer to the following information.

Array `arr` has been defined and initialized as follows

```
int[] arr = {5, 3, 8, 1, 6, 4, 2, 7};
```

**3.** Which of the following shows the elements of the array in the correct order after the first pass through the outer loop of the Insertion Sort algorithm?

![Image](img/f0262-04.jpg)

**4.** Which of the following shows the elements of the array in the correct order after the fourth pass through the outer loop of the Insertion Sort algorithm?

![Image](img/f0263-01.jpg)

**5.** Which of the following shows the elements of the array in the correct order after the first pass through the outer loop of the Selection Sort algorithm?

![Image](img/f0263-02.jpg)

**6.** Which of the following shows the elements of the array in the correct order after the fourth pass through the outer loop of the Selection Sort algorithm?

![Image](img/f0263-03.jpg)

### Advanced Level

**7.** Consider the following code segment.

![Image](img/f0263-04.jpg)

What is printed as a result of executing the code segment?

(A) `34`

(B) `37`

(C) `46`

(D) `47`

(E) `49`

**8.** Assume that `msg` is an `ArrayList<String>` that has been correctly constructed and populated with the following items.

![Image](img/f0264-03.jpg)

Which code segment removes all `String` objects starting with a letter from the second half of the alphabet (n–z) from the `ArrayList`?

Precondition: all `String` objects will be lowercase

Postcondition: msg will contain only `String` objects from the first half of the alphabet (a–m)

![Image](img/f0264-01.jpg)

(A) I only

(B) I and II only

(C) II and III only

(D) I and III only

(E) I, II, and III

**9.** Consider the following code segment that implements the Insertion Sort algorithm.

![Image](img/f0264-02.jpg)

Which of the following can be used to replace `/* condition */` so that `insertionSort` will work as intended?

![Image](img/f0265-01.jpg)

**10.** Determine if the numbers in an `ArrayList` are always increasing.

Write a method that determines if the values in an `ArrayList` are always increasing. The method takes one parameter: an `ArrayList` of `Integer`. The method returns true if the elements in the array are continually increasing and false if the elements are not continually increasing.

![Image](img/f0265-02.jpg)

For example, if the ArrayList passed to the method is:

![Image](img/f0265-03.jpg)

then the value true is returned

![Image](img/f0265-04.jpg)

**11.** Determine if the rate is increasing.

If a stock price is increasing, that means the value of it is going up. If the *rate* that the stock price is increasing is increasing, it means that the price is rising at a faster rate than it was the day before. Write a method that determines if the rate at which a stock price increases is increasing. The method has one parameter: an `ArrayList` of `Double` values that represent the stock prices. Return true if the rate that the stock is increasing is increasing, and false if the rate is not increasing.

![Image](img/f0265-05.jpg)

For example, if stockPrices contains the following:

![Image](img/f0265-06.jpg)

then the value true is returned

![Image](img/f0265-07.jpg)

**12.** Count the empty lockers.

A high school has a specific number of lockers so students can store their belongings. The office staff wants to know how many of the lockers are empty so they can assign these lockers to new students. Consider the following classes and complete the implementation for the `countEmptyLockers` method.

![Image](img/f0266-01.jpg)

### 2D 数组

## 摘要

我们之前处理过的数据结构都是一维数组，因为它们存储的是简单的一列数据值。有时使用数组或 `ArrayList` 还不够。二维数组存储值的方式类似于表格中的行和列。在本单元中，我们将讨论二维数组，并回顾之前编写的代码，将其修改以适配二维数组。

![Images](img/idea.jpg)

### 关键要点

![image](img/star.jpg)二维数组是一个数组的数组。

![image](img/star.jpg)二维数组模拟了一个矩形网格，每个位置根据行和列的坐标进行定位。

![image](img/star.jpg)2D 数组可以使用行优先顺序或列优先顺序进行遍历。

![image](img/star.jpg)所有标准的数组或 `ArrayList` 算法都可以应用于 2D 数组。

### 2D 数组

#### 2D 数组的定义

一个 `二维 (2D) 数组` 是一种复杂的数据结构，可以被视为由 `行` 和 `列` 组成的矩形 `网格`。技术上，它是 `一个数组的数组`。它可以在其槽中存储任何类型的数据；然而，每个数据块必须是相同的数据类型。

二维数组在实际操作中很有趣，并且在创建网格式游戏时非常实用。许多棋盘游戏基于网格：检 ers、国际象棋、Scrabble 等。许多应用程序也基于网格：CandyCrush、2048、Ruzzle。相信你还能想到其他例子。

#### 使用预定义数据列表初始化 2D 数组的声明和初始化

当你知道想要在 2D 数组中存储的值时，你可以声明数组并立即存储这些值。此操作与我们对一维数组的操作相同。**两对括号**，`[ ] [ ]`，用于告诉计算机这不是普通变量。

使用初始化列表创建 2D 数组的通用形式

![Image](img/f0274-01.jpg)

注意：使用大括号 `{}` wrapping 第一行，然后是第二行，以此类推。仔细观察此视觉，你会看到 2D 数组实际上是一个数组的数组。

### 示例

声明一个表示糖果 Crush 棋盘的 2D 数组，包含四行三列。注意行号从 0 到 3，列号从 0 到 2。

![Image](img/f0274-02.jpg)

这是 `candyBoard` 数组在计算机内部的视觉表示。

![Image](img/f0274-03.jpg)

#### 2D 数组的行和列

2D 数组中的每个单元格都有一个坐标对，基于行号和列号。第一对括号表示行号，第二对括号表示列号。行和列都从 0 开始，并以行数或列数减 1 结束，这与数组和 ArrayList 的行为相同。

### 示例

将“洛ゼ”在行 2、列 0 改为“Lemon Drop”。

```
candyBoard[2][0] = "Lemon Drop";
```

![Image](img/f0275-01.jpg)

#### 使用 `new` 关键字声明 2D 数组

2D 数组对象可以使用 **new** 关键字创建。2D 数组的每个单元格都会被填充为其数据类型的默认值。

使用 `new` 创建 2D 数组的通用形式

```
dataType[][] nameOfArray = new dataType[numberOfRows][numberOfColumns];
```

### 示例

声明一个表示数独棋盘的 2D 数组，包含九行九列。在行 2、列 7 放入数字 6：

![Image](img/f0275-02.jpg)

![Image](img/f0275-03.jpg)

![images](img/power.jpg)

#### 在 2D 数组中访问行和列

位置 `myBoard[0][5]` 读作 *行 0，列 5*。

位置 `myBoard[3][0]` 读作 *行 3*，*列 0*。

#### 使用 `length` 字段获取行数和列数

2D 数组的行数通过访问 `length` 字段获得。2D 数组的列数通过在数组名称上访问 `length` 字段并结合任意一行来获取（具体是哪一行不重要）。

##### 示例 1

从 2D 数组中获取行数：

![Image](img/f0276-01.jpg)

##### 示例 2

从 2D 数组中获取列数：

![Image](img/f0276-02.jpg)

![images](img/power.jpg)

#### 从 2D 数组内访问一维数组

考虑以下 2D 数组声明：

```
double[][] myBoard = new double[8][3];
```

`myBoard[0]` 是一个一维数组，包含索引为 0 的行。

`myBoard[5]` 是一个一维数组，包含索引为 5 的行。

#### 在行优先顺序中遍历 2D 数组

遍历 2D 数组意味着访问网格中的每个单元格。这可以通过多种方式实现，但对于 AP 计算机科学 A 考试，你需要了解两种特定的方式。

**行优先顺序** 是遍历 2D 数组的方式，类似于英语使用者阅读书籍的方式。从左上角单元格开始，向右沿第一行移动直到行末，然后从下一行的左侧单元格开始，向右移动直到该行末。重复此过程，直到访问所有单元格，最后到达右下角单元格。

### 示例

按行优先顺序遍历数组。从行 0 开始，到最后一行结束。对于每一行，从列 0 开始，到该行的最后一列结束。

##### Java 代码 1：使用嵌套 for 循环

![Image](img/f0276-03.jpg)

##### Java 代码 2：使用增强 for 循环

![Image](img/f0277-01.jpg)

#### 在列优先顺序中遍历 2D 数组

**列优先顺序** 是通过从左上角单元格开始，向下移动直到第一列的底部，然后转到下一列的顶部，向下移动直到该列底部，以此类推，直到访问所有单元格，最后到达右下角单元格。

### 示例

使用嵌套 `for` 循环按列优先顺序遍历数组。从列 0 开始，到最后一列结束。对于每一列，从行 0 开始，到该列的最后一行结束。

![Image](img/f0277-02.jpg)

`ArrayIndexOutOfBoundsException`

与一维数组一样，如果使用的索引不在 2D 数组范围内，将得到 `ArrayIndexOutOfBoundsException`。

![image](img/fun.jpg)

趣味事实：*Java* 支持多维数组，例如 3D 数组；但 AP 计算机科学 A 考试不要求你了解它们。

### 更多算法

所有标准的数组/`ArrayList` 算法都可以应用于 2D 数组。让我们重新回顾一下它们，分别来自 单元 6 和 单元 7。

### 累加算法

记得在 单元 6 中的棒球场景，我们计算了球队在一场比赛（一维数组）中的总安打数。我们将进行修改，使其能够计算整个赛季（2D 数组）中球队的总安打数。

**一般问题**：累加棒球队的所有安打。

**细化问题**：编写一个方法，计算 2D 数组中所有安打的总和。

**最终问题**：编写名为 `findSum` 的方法，包含一个参数：一个整数 2D 数组。该方法应返回数组中所有元素的总和。

**算法**：

步骤 1：创建一个名为 `sum` 的变量，并将其设置为 0。

步骤 2：遍历列表中的每个元素。

步骤 3：将元素添加到 `sum` 中。

步骤 4：继续，直到遍历完列表的末尾。

步骤 5：返回 `sum`。

**伪代码**：

![Image](img/f0278-01.jpg)

##### 使用 2D 数组（行优先顺序）的 Java 代码

![Image](img/f0278-02.jpg)

### 查找最高分算法

你最喜欢的视频游戏中最高的分数是多少？随着更多人玩游戏，计算机如何找出列表中的最高分数？

**一般问题**：在所有视频游戏分数中找到最高分。

**细化问题**：编写一个方法，找出分数列表中的最高分。

**最终问题**：编写名为 `findHigh` 的方法，包含一个参数：一个 2D 数组。该方法应返回数组中的最大值。

#### 解决方案：让最高分是列表中的第一个元素。

**算法**：

步骤 1：创建一个名为 `high` 的变量，并将其设置为列表中的第一个元素。

步骤 2：遍历列表中的每个分数。

步骤 3：如果分数大于 `high`，则将其设为新的最高分。

步骤 4：继续，直到遍历完列表的末尾。

步骤 5：返回最高分。

**伪代码**：

![Image](img/f0279-01.jpg)

##### 使用 2D 数组（行优先顺序）的 Java 代码

- [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**Richard Feynman**。

1. 运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。
