

### [3](#56_Chapter48.xhtml#rffa3)
考虑一个用于处理邮件列表中姓名和地址的系统。`Recipients` 类将作为此系统的一部分使用。邮件列表中的行存储在 `ArrayList<String>` 中，这是 `Recipients` 类的一个私有实例变量。邮件列表中分隔收件人的空行在此列表中存储为空字符串，且列表中的最后一个元素也是空字符串。

邮件列表的一部分如下所示，以及对应的 `ArrayList` 部分。

![images](images/f362-01.jpg)

处理这些数据的 `Recipients` 类如下所示。

![images](images/f363-01.jpg)

**(a)** 编写 `Recipients` 类的 `extractCity` 方法。在 `cityZip` 参数中，城市名后跟一个逗号，然后是一个空格，接着是两个大写字母的州缩写，然后是一个空格和一个 5 位数的邮政编码。例如，如果 `cityZip` 是 `“Ithaca, NY 14850”`，则方法调用 `extractCity(cityZip)` 应返回 `“Ithaca”`。

![images](images/f363-02.jpg)

完成 `extractCity` 方法。

![images](images/f364-01.jpg)

**(b)** 编写 `Recipients` 类的 `getAddress` 方法。该方法应返回一个仅包含与 `name` 参数对应地址的字符串。例如，如果 `name` 是 `“Jack S. Smith”`，则应返回一个包含他地址后续三行的字符串。该字符串应在适当的位置包含换行符，包括在最后一行地址之后。这确保了当客户端类打印时，地址将具有正确的地址格式。在给定的 `“Jack S. Smith”` 姓名示例中，其地址字符串的打印版本应如下所示：

![images](images/f364-02.jpg)

完成 `getAddress` 方法。

![images](images/f364-03.jpg)

### [4](#56_Chapter48.xhtml#rffa4)
在一个设有参赛者二维排列的大厅里举行一场解谜比赛。下图中的每个矩形代表一名参赛者。

![images](images/f364-04.jpg)

比赛中的参赛者可以用 `Contestant` 类表示，其部分实现如下。

![images](images/f365-01.jpg)

在 (a) 和 (b) 两部分中，你将编写 `ContestOrganizer` 类的两个方法，其部分实现如下。比赛组织者使用二维数组来跟踪参赛者。

![images](images/f365-02.jpg)

**(a)** 编写 `ContestOrganizer` 方法 `sortAllRows`。该方法应按分数对每一行中的参赛者进行排序，从低到高。

示例：假设参赛者如下图所示。

![images](images/f366-01.jpg)

调用 `sortAllRows` 后，参赛者将变为如下所示。

![images](images/f366-02.jpg)

编写 `sortAllRows` 时，你的方法*必须*使用 `ContestOrganizer` 方法 `sort`。你可以假设 `sort` 按指定方式工作。

完成 `sortAllRows` 方法。

![images](images/f366-03.jpg)

**(b)** 编写 `Contestant` 方法 `findWinnerName`，该方法返回得分最高的参赛者的姓名。例如，如果参赛者如上图所示，调用 `findWinnerName` 应返回 `“Harry”`。

编写 `findWinnerName` 时，你应该假设参赛者尚未按分数排序，并且只有一名参赛者得分最高。在编写解决方案时，你*必须*使用方法 `sortAllRows`。你可以假设 `sortAllRows` 按指定方式工作，无论你在 (a) 部分写了什么。

完成 `findWinnerName` 方法。

![images](images/f366-04.jpg)

**停止 考试结束**

### [答案解析](#05_Contents.xhtml#rsec180)

### 第一部分

**[1](#56_Chapter48.xhtml#ff1). (C)** 彻底测试程序并不能证明程序是正确的。对于大型程序，通常不可能测试每一组可能的输入数据。

**[2](#56_Chapter48.xhtml#ff2). (C)** 私有实例变量 `hourlyWage` 必须增加 `amt`。排除选项 E，它并没有使 `hourlyWage` *增加*；只是简单地用 `amt` *替换* 了它。选项 D 是错误的，因为不能将方法调用用作赋值语句的左侧。选项 A 和 B 是错误的，因为 `incrementWage` 方法是 void 类型，不应返回值。

**[3](#56_Chapter48.xhtml#ff3). (D)** 布尔实例变量 `isUnionMember` 的值必须改为其当前值的相反值。代码段 I 和 II 都能实现这一点。注意 `!true` 的值为 `false`，`!false` 的值为 `true`。如果 `isUnionMember` 当前值为 `false`，代码段 III 无法完成所需操作。

**[4](#56_Chapter48.xhtml#ff4). (C)** `computePay` 是客户端方法，因此无法访问类的私有变量。这排除了选项 A 和 D。必须使用点成员结构访问方法 `getHourlyWage()`；因此，选项 B 是错误的，选项 C 是正确的。选项 E 完全离谱——`hours` 不是 `Worker` 类的一部分，所以 `w.hours` 是无意义的。

**[5](#56_Chapter48.xhtml#ff5). (E)** 如果 `wordList` 中所有字符串的 `s.length() < 4`，则每次通过 `for` 循环都会打印 `SHORT WORD`。由于循环有 `wordList.size()` 次通过，`SHORT WORD` 最多可打印 `wordList.size()` 次。

**[6](#56_Chapter48.xhtml#ff6). (E)** ![images](images/f367-01.jpg)

**[7](#56_Chapter48.xhtml#ff7). (A)** `colors` 数组的声明进行了以下赋值：`colors[0] = “red”`，`colors[1] = “green”`，`colors[2] = “black”`。代码段 I 中的循环按正确顺序将这些值添加到 `colorList` 中。代码段 II 失败，因为 `colors` 是数组，因此不能使用 `get` 方法。该代码还混淆了列表。代码段 III 在第一次循环时，试图将 `colors[2]` 添加到 `colorList` 的索引位置 `2`。这将抛出 `IndexOutOfBoundsException`，因为索引位置 `0` 和 `1` 尚不存在！

**[8](#56_Chapter48.xhtml#ff8). (D)** 归并排序反复将一个包含 *n* 个元素的数组对半分割，直到得到 *n* 个各包含一个元素的数组。然后相邻数组依次合并，直到形成一个合并后的有序数组。二分查找反复将数组分成两半，缩小可能包含键的区域。然而，插入排序不进行数组分割。它一次取一个元素，在数组已排序的部分中找到其插入点。元素被移动以允许每个元素正确插入。尽管该算法将数组保持为两部分——已排序部分和待排序部分——但这并非分治法。

**[9](#56_Chapter48.xhtml#ff9). (B)** 静态变量由类的所有实例共享。“Static”意味着无论构造多少个 `Insect`，只会分配一个内存槽。所有 `Insect` 实例访问存储在该槽中的相同信息。创建 `Insect` 时，它将获得该内存槽中 `nextAvailableID` 的当前值作为标记，随后该值将为下一个创建的 `Insect` 递增。所有其他变量——`age`、`idNum`、`position`、`direction`——都特定于 `Insect` 的一个实例，因此应作为类中的私有实例变量。

**[10](#56_Chapter48.xhtml#ff10). (E)** 必须创建一个新的 `Address` 对象，用作 `Customer` 构造函数中的 `Address` 参数。要正确执行此操作，需要在 `Address` 构造函数前使用关键字 `new`。代码段 II 省略了 `new`，且未正确使用 `Address` 构造函数。（事实上，它在 `Customer` 构造函数的 `Address` 槽位插入了一个新的 `String` 对象。）

