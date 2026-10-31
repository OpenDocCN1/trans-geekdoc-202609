
该语句对 Jay 来说运行良好，但对 Brad 来说会出现问题，因为他未婚，其 spouse_id 字段为 null。即使查询的目标是获取 contacts 表中的所有人员以及如果存在的话其关联配偶，他也不会出现在结果集中。

再次，这只是一个预览，是 null 如此重要的一个例子。在第 3 章中，你将看到外连接如何解决这类问题。

## 索引

可以说，关系型数据库的单一最大优势就是查询和排序海量信息时的速度。为了实现这些高速，MySQL 以及所有其他数据库服务器都使用称为索引的优化数据存储机制。

索引允许数据库服务器创建一个列的表示形式，以便其能够以惊人的速度进行搜索。索引在从大型表中查找单行或一组行时特别有帮助。它们还可以加快连接和聚合函数（如 min() 和 max()）的速度，我们将在第 3 章中介绍这些函数。

鉴于这些优势，为什么不为每个表的每列都创建索引呢？有一些非常好的理由。首先，索引实际上会减慢某些操作。数据库服务器维护索引需要时间。你不希望为服务器创建最终对你没有好处的开销。也有索引本身更慢的情况。如果需要遍历表中的每一行，实际上最好不要使用索引。此外，不必要的索引会占用大量磁盘空间。

表的 primary key 通常是搜索的对象（原因显而易见）。因此，在表定义中，你声明为 primary key 的列或列将自动被索引。

本章后面将详细介绍创建索引的内容。

## 创建数据库语句

在创建表之前，你需要创建数据库。这应该只需要一秒钟。基本的 Create 语法相当简单，可以从任何具有 MySQL 访问权限的界面运行。

一般语法是：

```
create database database_name
```

![](img/de0823012275cf4ceebdb822a56e6b71_58_0.png)

如果好奇的话，运行此命令后 MySQL 会创建一个文件夹，在其中存储数据库所需的所有文件。在我的 Linux 机器上，数据库文件夹存储在 /var/lib/mysql/ 中。

在命名数据库时，或者说列或索引时，避免使用将来会引起混淆的名称。在文件名区分大小写的操作系统上，例如大多数 Unix 系统，数据库名称也区分大小写。制定你打算坚持的约定，例如对表和列使用全小写名称。不允许使用空格。虽然 MySQL 可以绕过潜在的糟糕选择，但你应避免使用 MySQL 在其业务过程中使用的词。例如，将表命名为“Select”是一个非常糟糕的主意。在 MySQL 参考手册的第 7 章中，有超过 150 个保留字的列表。如果你避开 SQL 或 MySQL 函数使用的词，应该没问题。

从 MySQL 命令行客户端，你可以简单地输入：

```
create database database_name;
```

![](img/de0823012275cf4ceebdb822a56e6b71_59_0.png)

MySQL 命令行客户端位于你的 MySQL 安装的 /bin 目录中，文件名是 mysql（在 Unix 上）或 DOS/Windows 上的 mysql.exe。

从 PHP 中，你可以使用 mysql_create_db() 或 mysql_query() 函数。下面的代码片段将创建两个数据库。请记住，你需要以具有适当权限的用户登录 MySQL，代码才能工作。

```
$conn = mysql_connect("localhost","username", "password")
    or die ("Could not connect to localhost");

mysql_create_db("my_database") or
    die ("Could not create database");
$string = "create database my_other_db";
mysql_query($string) or
    die(mysql_error());
```

## 使用数据库语句

在 MySQL 中开始创建表之前，你必须选择一个已创建的数据库。如果你通过 mysql 命令行客户端访问 MySQL，你必须输入以下语句：

```
use database_name
```

如果你通过 PHP 访问数据库，请使用 mysql_select_db() 函数。

```
$conn = mysql_connect("localhost","username", "password")
    or die ("Could not connect to localhost");

mysql_select_db("test", $conn) or
    die ("Could not select database");
```

## 创建表语句

一旦你创建并选择了数据库，就准备好创建表了。基本的 Create Table 语法相当简单，基本形式如下。

```
create table table_name
(
    column_1 column_type column attributes,
    column_2 column_type column attributes,
    primary key (column_name),
    index index_name(column_name)
)
```

列类型、列属性和索引的详细信息将在以下章节中介绍。在此之前，有两个简单的列属性需要讨论：

- null | not null
- default

第一个让你有机会禁止或允许 null 值。如果你未指定 "null" 或 "not null"，则假定允许 null 值。第二个，如果声明，则在插入行到表时如果未声明值，则设置一个值。

下面是一个 create 语句的示例，你可以看到这两个属性以及其他一些属性的使用。这个示例取自第 12 章并稍作修改。

```
create table topics2 (
    topic_id      integer not null auto_increment,
    parent_id     integer default 0 not null,
    root_id       integer default 0,
    name          varchar(255),
    description   text null,
    create_dt     timestamp,
    modify_dt     timestamp,
    author        varchar(255) null,
    author_host   varchar(255) null,
    primary key(topic_id),
    index my_index(parent_id)
)
```

该语句创建了一个名为“topics”的表，包含九列和两个索引，一个用于 primary key，一个用于 parent_id 列。在上面的语句中使用了四种列类型：integer、varchar、text 和 timestamp。这些以及许多其他列类型将在下面更详细地讨论。在着手创建表之前，你应该很好地了解所有可用的列类型以及创建索引的方法。

要从命令行客户端创建表，请键入整个命令。从 PHP 中，使用 mysql_query() 函数。

```
$conn = mysql_connect("localhost","username", "password") or
    die ("Could not connect to localhost");

mysql_select_db("test", $conn) or
    die("could not select database");
$query = "create table my_table (
    col_1 int not null primary key,
    col_2 text
)";
mysql_query($query) or
    die(mysql_error());
```

## 列类型

MySQL 提供了多种列类型。其中一些相似，但存在细微却重要的差异。请阅读本节，并在为表决定列类型时仔细选择。

### 文本列类型

MySQL 有七种适合存储文本字符串的列类型：

- char
- varchar
- tinytext
- text
- mediumtext
- longtext
- enum

### CHAR

用法：char(length)

char 列类型的最大长度为 255 个字符。这是一个定长类型，意味着当插入的值字符数少于列的最大长度时，字段将用空格右填充。因此，如果列定义为 char(10) 且你想存储值“happy”，MySQL 实际上会存储“happy”然后是五个空格。当从表中检索值时，这些空格会被从结果中移除。

### VARCHAR

用法：varchar(length)

这几乎与 char 相同，并在许多相同的地方使用。它的最大长度也为 255。不同之处在于 varchar 是变长列类型。值不会用空格填充。相反，MySQL 会为每个 varchar 字段添加一个字符，用于存储字段的长度。MySQL 会从 varchar 字段中的字符串末尾移除空格。

### 使用 CHAR 或 VARCHAR

在大多数情况下，char 和 varchar 之间几乎没有实际区别。你决定使用哪一个将取决于哪一个需要更多空间，char 列中的尾随空格还是 varchar 中的单个字符。如果你的字段存储类似姓氏的内容，你可能希望允许 25 个字符，以确保安全。如果你使用 char 列类型，而某人的姓氏是 Smith，你的列将包含 20 个尾随空格。这没有必要；你最好使用 varchar 并让 MySQL 跟踪列的大小。然而，当你想存储五到七个字符的密码时，使用 varchar 来跟踪列的大小是浪费的。每次更新 varchar 字段时，MySQL 都必须检查字段的长度并更改存储字段长度的字符。你最好使用 char(7)。

![](img/de0823012275cf4ceebdb822a56e6b71_62_0.png)

> 如果你将列定义为 varchar 且列长度小于四，MySQL 将自动把列更改为 char 类型。
