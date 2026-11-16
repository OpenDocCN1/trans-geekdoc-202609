
降序或根本没有特定顺序。

每一列代表一个不同的数据属性。表中的行（按主键）是唯一的，但特定列值在行之间可能重复。例如，Employee 表的 Department 列中有三个不同的行包含数字 413。

## 选择数据子集

不同的数据库用户通常关注不同的数据以及数据之间的不同关系。大多数用户只需要行和列的子集。查询指定从表中选择哪些数据子集。您使用结构化查询语言（SQL）来定义查询。例如，您可以从 Employee 表中选择数据，以创建一个显示每个部门位置的结果，并按部门编号递增顺序排列数据。结果如下所示。我们稍后将讨论 SQL。

点击此处查看代码图像

| 部门 | 地点 |
|---|---|
| 413 | 新泽西 |
| 611 | 奥兰多 |
| 642 | 洛杉矶 |

## SQLite

第 16.2 节其余部分的代码示例使用随 Python 包含的开源 SQLite 数据库管理系统，但大多数流行的数据库系统都支持 Python。每个系统通常提供一个遵守 Python 数据库应用程序编程接口 (DB-API) 的模块，该接口指定用于操作任何数据库的常见对象和方法名称。

## 16.2.1 图书数据库

在本节中，我们将介绍一个包含多本书籍信息的图书数据库。我们将通过 Python 标准库的 sqlite3 模块在 SQLite 中设置数据库，使用 ch16 示例文件夹的 sql 子文件夹中提供的脚本。然后，我们将介绍数据库的表。我们将在 IPython 会话中使用此数据库来介绍各种数据库概念，包括创建、读取、更新和删除数据的操作——即所谓的 CRUD 操作。在介绍表时，我们将使用 SQL 和 pandas DataFrames 向您展示每个表的内容。然后，在接下来的几个部分中，我们将讨论其他 SQL 特性。

## 创建图书数据库

在您的 Anaconda 命令提示符、终端或 shell 中，切换到 ch16 示例文件夹的 sql 子文件夹。以下 sqlite3 命令创建一个名为 books.db 的 SQLite 数据库并执行 books.sql SQL 脚本，该脚本定义如何创建数据库的表并用数据填充它们：

```
sqlite3 books.db < books.sql
```

符号 < 表示 books.sql 是输入到 sqlite3 命令的。当命令完成时，数据库即可使用。开始一个新的 IPython 会话。

### 在 Python 中连接到数据库

要在 Python 中操作数据库，首先调用 sqlite3 的 **连接函数** 以连接到数据库并获取一个 **Connection** 对象：

点击此处查看代码图像

```
In [1]: import sqlite3

In [2]: connection = sqlite3.connect('books.db')
```

### authors 表

数据库有三个表——authors、author_ISBN 和 titles。authors 表存储所有作者，并有三列：

- **id**—作者的唯一 ID 号。此整数列定义为 **自动递增**——对于表中插入的每一行，SQLite 将 id 值加 1 以确保每一行都有一个唯一值。此列是表的主键。
- **first**—作者的名（字符串）。
- **last**—作者的姓（字符串）。

### 查看 authors 表的内容

让我们使用 SQL 查询和 pandas 来查看 authors 表的内容：

点击此处查看代码图像

```
In [3]: import pandas as pd

In [4]: pd.options.display.max_columns = 10

In [5]: pd.read_sql('SELECT * FROM authors', connection,
   ....:               index_col=['id'])
   ....:
```

| id | 名 | 姓 |
|---|---|---|
| 1 | Paul | Deitel |
| 2 | Harvey | Deitel |
| 3 | Abbey | Deitel |
| 4 | Dan | Quirk |
| 5 | Alexander | Wald |

Pandas 函数 **read_sql** 执行 SQL 查询并返回包含查询结果的 **DataFrame**。该函数的参数为：

- 表示要执行的 SQL 查询的字符串，
- SQLite 数据库的 **Connection** 对象，在此例中
- 一个 index_col 关键字参数，指示哪一列应被用作 DataFrame 的行索引（在此例中为作者的 id 值）。

如您稍后将看到，当未传递 index_col 时，从 0 开始的索引值将出现在 DataFrame 行的左侧。

SQL SELECT 查询从数据库中的一个或多个表获取行和列。在查询中：

```
SELECT * FROM authors
```

星号 (*) 是通配符，表示查询应获取 authors 表的所有列。我们将稍后详细讨论 SELECT 查询。

### titles 表

titles 表存储所有书籍，并有四列：

- isbn—图书的 ISBN（字符串）是本表的主键。ISBN 是“International Standard Book Number”的缩写，这是出版商用于为每本书赋予唯一标识号的编号方案。
- title—图书标题（字符串）。
- edition—图书版本号（整数）。
- copyright—图书版权年份（字符串）。

让我们使用 SQL 和 pandas 来查看 titles 表的内容：

点击此处查看代码图像

```
In [6]: pd.read_sql('SELECT * FROM titles', connection)
```

| ISBN | 标题 | 版本 | 版权年份 |
|---|---|---|---|
| 0135404673 | Intro to Python for CS and DS | 1 | 2020 |
| 0132151006 | Internet & WWW How to Program | 5 | 2012 |
| 0134743350 | Java How to Program | 11 | 2018 |
| 0133976890 | C How to Program | 8 | 2016 |
| 0133406954 | Visual Basic 2012 How to Program | 6 | 2014 |
| 0134601548 | Visual C# How to Program | 6 | 2017 |
| 0136151574 | Visual C++ How to Program | 2 | 2008 |
| 0134448235 | C++ How to Program | 10 | 2017 |
| 0134444302 | Android How to Program | 3 | 2017 |
| 0134289366 | Android 6 for Programmers | 3 | 2016 |

### author_ISBN 表

author_ISBN 表使用以下列将 authors 表中的作者与 titles 表中的他们的书籍相关联：

- id—作者的 id（整数）。
- isbn—图书的 ISBN（字符串）。

`id` 列是一个 **外键**，即本表中与另一表中的 *主键* 列匹配的列——具体来说，是 `authors` 表的 `id` 列。`isbn` 列也是一个外键——它匹配 `titles` 表的 `isbn` 主键列。数据库可能有很多表。设计数据库时的一个目标是 *尽量减少数据重复*。为此，每个表代表一个特定实体，外键有助于链接 *多个* 表中的数据。在创建数据库表时（在我们的情况中，在 `books.sql` 脚本中）指定主键和外键。

本表中的 `id` 和 `isbn` 列共同形成一个 *复合主键*。本表中的每一行都 *唯一* 地将 *一位作者* 与 *一本书的 ISBN* 匹配。本表包含许多条目，因此让我们使用 SQL 和 pandas 仅查看前五行：

点击此处查看代码图像

```
In [7]: df = pd.read_sql('SELECT * FROM author_ISBN', connection)

In [8]: df.head()
```

| id | ISBN |
|---|---|
| 0 | 0134289366 |
| 2 | 0134289366 |
| 5 | 0134289366 |
| 1 | 0135404673 |
| 2 | 0135404673 |

每个外键值必须作为另一表中某行的主键值出现，以便 DBMS 可以确保外键值有效。这称为 **参照完整性规则**。例如，DBMS 通过检查 `authors` 表中是否存在以该 `id` 为主键的行，来确保特定 `author_ISBN` 行的 `id` 值有效。

外键还允许从多个表中的 *相关数据* 被 *选取* 并合并——这称为 **连接** 数据。主键与相应外键之间存在 **一对多关系**——一位作者可以编写多本书，同样，一本书可以由多位作者编写。因此，外键可以在其表中出现 *多次*，但在另一张表中只出现 *一次*（作为主键）。例如，在 `books` 数据库中，ISBN 0134289366 出现在多个 `author_ISBN` 行中，因为此书有多位作者，但它仅在 `titles` 中作为主键出现一次。

### 实体-关系 (ER) 图

以下是 `books` 数据库的 **实体-关系 (ER) 图**，显示了数据库的 *表* 以及它们之间的 *关系*：

![](img/34b7fc2f1ee27beb73bca14927d42340_737_0.png)
