

# 习题集

## 4. 代码段分析
参考以下代码段。假设数组 `arr1` 包含元素 `arr1[0]`、`arr1[1]`、...、`arr1[N-1]`，其中 `N` = `arr1.length`。

![images](images/f239-02.jpg)

如果数组 `arr1` 最初按顺序包含元素 0, 6, 0, 4, 0, 0, 2，那么代码段执行后 `arr2` 将包含什么？

(A) 6, 4, 2  
(B) 0, 0, 0, 0, 6, 4, 2  
(C) 6, 4, 2, 4, 0, 0, 2  
(D) 0, 6, 0, 4, 0, 0, 2  
(E) 6, 4, 2, 0, 0, 0, 0

## 5. 程序段分析
考虑此程序段。

![images](images/f240-01.jpg)

`SMALL` 最多可以打印多少次？

(A) `0`  
(B) `1`  
(C) `k - 1`  
(D) `k - 2`  
(E) `k`

## 6. 代码段输出
以下代码段将输出什么？假设它与 `doSomething` 方法在同一个类中。

![images](images/f240-02.jpg)
![images](images/f240-03.jpg)

(A) `0 0`  
(B) `2 4`  
(C) `1 3`  
(D) `0 2`  
(E) `0 3`

## 7. ArrayList 与数组的选择：文本文件读取
考虑编写一个程序，将任意文本文件的行读入到一个顺序行列表中。以下哪项是使用 `String` 对象的 `ArrayList` 而不是 `String` 对象数组来实现列表的充分理由？

(A) `ArrayList` 的 `get` 和 `set` 方法比数组的 `[]` 表示法更方便。  
(B) `ArrayList` 的 `size` 方法提供了对列表长度的即时访问。  
(C) `ArrayList` 可以包含任何类型的对象，从而带来更大的通用性。  
(D) 如果某个特定文本文件出乎意料地长，`ArrayList` 将自动调整大小。相比之下，数组可能会越界。  
(E) `String` 方法与 `ArrayList` 一起使用比与数组一起使用更容易。

## 8. 数组与 ArrayList 的选择：数值统计
考虑编写一个程序，为长数值数据列表生成统计信息。以下哪项是使用 `int`（或 `double`）数组而不是 `Integer`（或 `Double`）对象的 `ArrayList` 来实现每个列表的最佳理由？

(A) 基本数字类型的数组比包含数字的包装器对象的 `ArrayList` 操作效率更高。  
(B) 向列表中插入新元素，用数组编码比用 `ArrayList` 更容易。  
(C) 从列表中移除元素，用数组编码比用 `ArrayList` 更容易。  
(D) 访问列表中间的单个元素，用数组比用 `ArrayList` 更容易。  
(E) 在数组中访问所有元素比在 `ArrayList` 中更高效。

## 9-12 题参考类
请参考以下类来回答第 9-12 题。

![images](images/f242-01.jpg)

## 9. 生成名称列表
客户端方法具有以下声明，后跟初始化列表的代码。

![images](images/f243-01.jpg)

这是一段生成*仅名称*列表的代码段。

![images](images/f243-02.jpg)

哪一项是正确的 `/*` ***代码行*** `*/`？

(A) `System.out.println(Address[i].getName());`  
(B) `System.out.println(list[i].getName());`  
(C) `System.out.println(a[i].getName());`  
(D) `System.out.println(a.getName());`  
(E) `System.out.println(list.getName());`

## 10. 打印地址列表
以下代码段用于打印地址列表。

![images](images/f243-03.jpg)

哪一项是 `/*` ***更多代码*** `*/` 的正确替换？

I. ![images](images/f243-04.jpg)  
II. ![images](images/f243-05.jpg)  
III. ![images](images/f243-06.jpg)

(A) 仅 I  
(B) 仅 II  
(C) 仅 III  
(D) 仅 I 和 II  
(E) I、II 和 III

## 11. 生成学生姓名列表
客户端方法具有以下声明。

![images](images/f244-01.jpg)

这是一段生成 `Student` 姓名列表的代码段。（假设 `allStudents` 已初始化。）

![images](images/f244-02.jpg)

哪一项是 `/*` ***打印姓名列表的代码*** `*/` 的正确替换？

(A) `System.out.println(allStudents.getName());`  
(B) `System.out.println(student.getName());`  
(C) `System.out.println(student.getAddress().getName());`  
(D) `System.out.println(allStudents.getAddress().getName());`  
(E) `System.out.println(student[i].getAddress().getName());`

## 12. 查找最高 ID 的学生
这是一个定位具有最高 `idNum` 的 `Student` 的方法。

![images](images/f245-01.jpg)

以下哪项可以替换 `/*` ***方法体*** `*/` 以使方法按预期工作？

![images](images/f245-02.jpg)

(A) 仅 I  
(B) 仅 II  
(C) 仅 III  
(D) 仅 I 和 III  
(E) 仅 II 和 III

## 13-15 题参考类
第 13-15 题参考下面的 `Ticket` 和 `Transaction` 类。

![images](images/f246-01.jpg)

## 13. Transaction 构造器初始化
以下哪项正确替换 `Transaction` 构造器中的 `/*` ***更多代码*** `*/` 以初始化 `tickList` 数组？

(A) `tickList[i] = new Ticket(getRow(), getSeat(), getPrice());`  
(B) `tickList[i] = new Ticket(theRow, theSeat, thePrice);`  
(C) `tickList[i] = new tickList(getRow(), getSeat(), getPrice());`  
(D) `tickList[i] = new tickList(theRow, theSeat, thePrice);`  
(E) `tickList[i] = new tickList(numTicks);`

## 14. totalPaid 方法计算金额
以下哪项代表 `totalPaid` 方法中 `/*` ***计算金额的代码*** `*/` 的正确代码？

![images](images/f247-01.jpg)

## 15. 票务交易列表声明
假设需要保留所有票务交易的列表。假设有 `NUMSALES` 笔交易，合适的声明将是

(A) `Transaction[] listOfSales = new Transaction[NUMSALES];`  
(B) `Transaction[] listOfSales = new Ticket[NUMSALES];`  
(C) `Ticket[] listOfSales = new Transaction[NUMSALES];`  
(D) `Ticket[] listOfSales = new Ticket[NUMSALES];`  
(E) `Transaction[] Ticket = new listOfSales[NUMSALES];`

## 16. 查找最小值代码修正
以下代码片段旨在找到 `arr[0]` ... `arr[n-1]` 中的最小值，但无法按预期工作。

![images](images/f248-01.jpg)

为了使该片段按预期工作，可以进行以下哪些修改？

![images](images/f248-02.jpg)

(A) 仅 I  
(B) 仅 II  
(C) 仅 III  
(D) 仅 I 和 II  
(E) I、II 和 III

## 17. match 方法循环断言
参考下面的 `match` 方法。

![images](images/f249-01.jpg)

假设该方法尚未退出，在 `while` 循环的每次执行结束时，以下哪个断言为真？

![images](images/f249-02.jpg)

## 18. 增强 for 循环修改对象
考虑此类。

![images](images/f250-01.jpg)

客户端程序具有此声明。

![images](images/f250-02.jpg)

假设 `bookList` 已初始化，列表中的每个 `Book` 都有标题、作者和借阅状态。编写以下代码片段，其目的是更改 `bookList` 中每本书的借阅状态。

![images](images/f250-03.jpg)

关于这段代码，哪项是正确的？

(A) 执行后 `bookList` 数组将保持不变。  
(B) `bookList` 数组中的每本书都将按预期更改其借阅状态。  
(C) 可能会发生 `NullPointerException`。  
(D) 将发生运行时错误，因为无法使用增强 `for` 循环修改对象。  
(E) 将发生逻辑错误，因为如果不访问数组中对象的索引，就无法修改数组中的对象。

## 19-20 题参考类
请参考此类来回答第 19 和 20 题。

![images](images/f251-01.jpg)

模拟宾果游戏的程序声明一个 `BingoCard` 数组。该数组有 `NUMPLAYERS` 个元素，每个元素代表不同玩家的卡片。这是一段创建游戏中所有宾果卡片的代码段。

![images](images/f251-02.jpg)

## 19. 创建 BingoCard 替换代码
以下哪项是对下列内容的正确替换？

![images](images/f251-03.jpg)

(A) ![images](images/f251-04.jpg)  
(B) ![images](images/f251-05.jpg)  
(C) ![images](images/f251-06.jpg)  
(D) ![images](images/f251-07.jpg)  
(E) ![images](images/f251-08.jpg)

## 20. 构造每个 BingoCard
假设 `players` 已声明为 `BingoCard` 数组，`/*` ***构造每个 BingoCard*** `*/` 的正确替换是什么？

