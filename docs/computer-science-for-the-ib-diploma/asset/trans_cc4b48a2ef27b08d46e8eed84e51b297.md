

- 10 在观察者设计模式中，“Subject”的作用是什么？
  - a 通知所有观察者有关任何更改
  - b 跟踪所有依赖项
  - c 更新各个主题的状态
  - d 请求观察者的更新
- 11 描述为什么继承被认为是面向对象编程的强大特性。
- 12 讨论多态性如何增强软件可维护性。
- 13 讨论抽象类相对于使用普通继承提供的两个好处。
- 14 列举一个示例（不基于本书中给出的任何示例），以说明组合与聚合之间的区别。
- 15 描述工厂设计模式并给出其使用示例。

## 编程练习

有些练习需要你下载文件进行处理或计算。这些文件可从以下网址下载：https://bit.ly/paulbaumgarten/hodder-ibdp-computerscience

### 1 扩展银行账户

实现第 B3.1 节末尾提供的银行账户示例，并在继续之前调试任何转录错误，以确保其按预期运行。

- [ ] 从 Github 仓库的 B3 文件夹下载以下文件：
  - names.txt
  - bank-transactions.txt
- [ ] 使用第 B2.5 节的文件读取技术，将每个文件读入字符串数组（每行文件为一个字符串）。
- [ ] 从 names.txt 文件创建一个银行账户数组，数组中每个人对应一个账户。
- [ ] 处理 bank-transactions.txt 中的交易列表。
- [ ] 对所有账户应用利息计算。
- [ ] 打印所有账户的最终余额。

你的账户持有人是否得到了如下所示的正确最终余额？

| 账户 1001: Eustolia 余额为 $5571.3 | 账户 1014: Hilma 余额为 $258.3 |
|---|---|
| 账户 1002: Nathan 余额为 $9515.1 | 账户 1015: Irving 余额为 $76.65 |
| 账户 1003: Melissa 余额为 $61.95 | 账户 1016: Carie 余额为 $2654.4 |
| 账户 1004: Willie 余额为 $1912.05 | 账户 1017: Nicky 余额为 $297.15 |
| 账户 1005: Hoyt 余额为 $4697.7 | 账户 1018: Adele 余额为 $3287.55 |
| 账户 1006: Alexandria 余额为 $2461.2 | 账户 1019: Carlene 余额为 $882.0 |
| 账户 1007: Clelia 余额为 $3311.7 | 账户 1020: Hermina 余额为 $2.1 |
| 账户 1008: Alpha 余额为 $1942.5 | 账户 1021: Ayana 余额为 $586.95 |
| 账户 1009: Delbert 余额为 $4670.4 | 账户 1022: Frederica 余额为 $261.45 |
| 账户 1010: Boyd 余额为 $547.05 | 账户 1023: Arianna 余额为 $541.8 |
| 账户 1011: Milton 余额为 $2331.0 | 账户 1024: Zandra 余额为 $725.55 |
| 账户 1012: Vivan 余额为 $1275.75 | 账户 1025: Vina 余额为 $2553.6 |
| 账户 1013: Constance 余额为 $2983.05 | |

### 2 航班预订系统

你正在为一家廉价航空公司构建票务预订系统。这家航空公司没有座位等级（没有头等舱或商务舱——所有人都坐经济舱），也不接受座位预订。航空公司唯一关心的是确保每个航班上有足够的座位出售。

你正在接替另一位程序员的工作，他为你开始设计类。以下是他创建的 UML。

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_447_0.png)

### UML 航班和票务

- 在代码中创建 Ticket 类和 Flight 类，以遵守以下规则：
- Flight 构造函数中的 capacity 变量表示给定航班上可用的座位数。使用此变量来确定 tickets 数组的大小。
- 实现 addTicket() 和 removeTicket() 以向 tickets 数组添加或删除票。每当添加新票时，ticketsSold 应该递增，每当删除票时，ticketsSold 应该递减。有关如何实现此功能的提示，请参阅第 B3.1.3 节中的 CollectionOfThings 示例。
- getSeatsAvailable() 应该只是 capacity 减去 ticketsSold 的结果。
- printPassengerList() 应该打印给定航班的所有票的姓名列表。

以下代码是用于测试结果的示例主代码，并指示输出应该是什么样子。

```
if __name__ == "__main__":
    cx619 = Flight("CX 619", 280) # Cathay - HKG-SIN
    aa6914 = Flight("AA 6914", 266) # American - JFK-LHR
    ek89 = Flight("EK 89", 354) # Emirates - DXB-GVA
    jordan = Ticket("Jordan Deckard")
    cx619.addTicket(Ticket("Taylor Ripley"))
    cx619.addTicket(jordan)
    cx619.addTicket(Ticket("Casey Neo"))
    aa6914.addTicket(Ticket("Cameron Quaid"))
    aa6914.addTicket(Ticket("Phoenix Andor"))
    cx619.printPassengerList()
    print(cx619.getSeatsAvailable())
    cx619.removeTicket(jordan)
    cx619.printPassengerList()
```

**Java**

```java
class Main {
    public static void main(String[] args) {
        Flight cx619 = new Flight("CX 619", 280); // Cathay - HKG-SIN
        Flight aa6914 = new Flight("AA 6914", 266);
        // American - JFK-LHR
        Flight ek89 = new Flight("EK 89", 354); // Emirates - DXB-GVA
        Ticket jordan = Ticket("Jordan Deckard");
        cx619.addTicket(new Ticket("Taylor Ripley"));
        cx619.addTicket(jordan);
        cx619.addTicket(new Ticket("Casey Neo"));
        aa6914.addTicket(new Ticket("Cameron Quaid"));
        aa6914.addTicket(new Ticket("Phoenix Andor"));
        cx619.printPassengerList();
        System.out.println(cx619.getSeatsAvailable());
        cx619.removeTicket(jordan);
        cx619.printPassengerList();
        System.out.println(cx619.getSeatsAvailable());
    }
}
```

预期输出：

```
Flight CX 619 has passengers:
Taylor Ripley
Jordan Deckard
Casey Neo
277
Flight CX 619 has passengers:
Taylor Ripley
Casey Neo
278
```

### 3 学校入学和成绩簿

实现第 B3.1 节末尾提供的学生和成绩示例，并在继续之前调试任何转录错误，以确保其按预期运行。

将场景扩展到包含一个名为 "Course" 的新类，该类包含已注册其课程的学生数组。

- [ ] Course 应该包含 addStudent() 和 removeStudent() 方法。

- [ ] Course 应该具有以下附加函数：

  - printClassList() 生成所有学生姓名的列表（按姓名排序顺序）

  - getClassAverage() 返回所有学生分数的平均值。

### 4 图书馆系统

创建一个系统来管理图书馆的图书借阅。

```
Book
- isbn : String
- title : String
- author : String
- publisher : String
- publicationDate : String
+ Book(String, String, String, String, String)
+ getISBN() : String
+ getTitle() : String
+ getAuthor() : String
+ getPublisher() : String
+ getPublicationDate() : String

Patron
- name : String
- books : Book[]
- booksOnLoan : int
+ Patron(String)
+ borrowBook(Book) : Boolean
+ returnBook(Book) : Boolean
+ getBooksOnLoan() : int
+ printBooksOnLoan() : void
```

### UML 图书和读者

- 按照 UML 图创建 Book 类和 Patron 类。
- 从 Github 仓库的 B3 文件夹下载以下文件：
  - names.txt
  - books.txt 或 books.csv
  - library-transactions.txt
- 使用第 B2.5 节的文件读取技术，将每个文件读入字符串数组。
- 从 names.txt 文件创建一个读者数组，数组中每个名字对应一个读者，并根据 books.txt 中的数据创建一个图书数组。
- 处理 library-transactions.txt 中的交易列表，遵循以下规则：
  - 每个读者同时最多只能借阅三本书。
  - 如果读者尝试借阅第四本书，应予以拒绝。
  - 一本书可以同时被多次借阅（想象每本书都有无限副本）。

```
Person Eustolia has these books:
9780141030142 Memory Keeper's Daughter,The
9780099387916 Birdsong
9780006498407 Angela's Ashes:A Memoir of a Childhood
Person Nathan has these books:
9780099419785 To Kill a Mockingbird
9781904994497 Guinness World Records 2010
9780140237504 Catcher in the Rye,The
Person Melissa has these books:
9780701181840 Nigella Express
9780099450252 Curious Incident of the Dog in the Night-time,The
Person Willie has these books:
9780563384304 Delia's How to Cook:(Bk.1)
9780590112895 Subtle Knife,The:His Dark Materials
9780747581109 Harry Potter and the Half-Blood Prince
```

有人尝试超过限额借阅图书多少次？你应该得到 1125。
序列结束时有多少本书正在借阅中？你应该得到 51。

