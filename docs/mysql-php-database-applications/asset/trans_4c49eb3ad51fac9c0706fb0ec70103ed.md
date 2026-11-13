

## 索引

可以说，关系型数据库最伟大的优势之一，莫过于其查询和排序海量信息的速度。为了实现这一惊人的速度，MySQL 以及所有其他数据库服务器都采用了名为 *索引* 的优化数据检索机制。

索引允许数据库服务器创建一个列的表示形式，以便以惊人的速度进行搜索。索引在从大型表中查找单行或一组行时尤其有用。它们还可以加速连接和聚合函数，如 `min()` 和 `max()`，我们将在第 3 章中介绍。

鉴于这些优势，为什么不为表中的每一列都创建索引呢？这里有几个非常充分的理由。首先，索引实际上可能会减慢某些操作。您的数据库服务器需要花费时间来维护索引。您不会想要为服务器创造无益的开销，这些开销未来不会对您有帮助。另外，在某些情况下，索引本身也更慢。如果您需要遍历表中的每一行，实际上不使用索引更好。此外，不必要的索引会占用大量磁盘空间和内存。

表的主键通常是搜索的对象（原因显而易见）。因此，在表定义中声明为主键的列或列会自动被索引。

我们将在本章后面更多地讨论创建索引。

## create database 语句

在创建表之前，您需要先创建一个数据库来存放它们。这应该只需要一秒钟。基本的 `create database` 语句非常简单，可以从任何可以访问 MySQL 的界面中运行。

一般语法如下：

```sql
create database database_name
```

> **注意** 如果您在想，运行此命令后，MySQL 会创建一个文件夹，用于存储数据库所需的所有文件。在我们的 Linux 机器上，数据库文件夹存储在 /usr/local/mysql/lib。

在命名数据库时，或者同样地，命名列或索引时，避免使用将来会引起混淆的名称。在文件名区分大小写的操作系统上（例如大多数 Unix 系统），数据库名也将区分大小写。制定您打算遵循的命名约定，例如对表和列都使用全小写名称。不允许使用空格。

尽管 MySQL 可以绕过潜在的错误选择，但您应避免使用 MySQL 在其业务过程中使用的单词。例如，将表命名为“Select”是一个非常糟糕的主意。MySQL 参考手册第 6 章列出了 150 多个保留字。如果您避开 SQL 或 MySQL 函数中使用的单词，您应该没问题。

从 MySQL 命令行客户端，您可以直接输入以下命令：

```sql
mysql> create database my_database;
```

> **提示** MySQL 命令行客户端位于 MySQL 安装目录的 bin/ 目录中，文件名为 mysql（Unix 中）或 mysql.exe（DOS/Windows 中）。

从 PHP，您可以使用 mysql_query() 函数。以下代码将创建两个数据库。（请记住，您需要以具有适当权限的用户身份登录 MySQL，代码才能正常工作。）

```php
$conn = mysql_connect("localhost","username", "password")
or die ("Could not connect to localhost");

mysql_query(" CREATE DATABASE IF NOT EXISTS my_database ") or
die ("Could not create database");
```

## use database 语句

在开始在 MySQL 中创建表之前，您必须选择一个已创建的数据库。虽然您可以在单独的 SELECT 语句中执行此操作，但使用 use 命令定义默认工作数据库更为简单。如果您通过 MySQL 命令行客户端访问 MySQL，则需要输入此语句：

```sql
use database_name
```

如果您通过 PHP 访问数据库，请使用 mysql_select_db() 函数：

```php
$conn = mysql_connect("localhost","username", "password")
or die ("Could not connect to localhost");

mysql_select_db("test", $conn) or
die ("Could not select database");
```

## create table 语句

一旦您创建并选择了数据库，就可以创建表了。基本的 create table 语句非常简单，采用以下基本形式：

```sql
create table table_name
(
    column_name_1 column_type column_attributes,
    column_name_2 column_type column_attributes,
    primary key (column_name),
    index index_name(column_name)
)type=table_type
```

列类型、列属性以及索引的详细信息将在后续章节中介绍。在进入那些内容之前，我们应该提及两个简单的列属性：

- null | not null
- default

第一个属性让您有机会允许或禁止 null 值。如果您不指定 null 或 not null，则默认允许 null 值。第二个属性，如果声明了，则在您向表中插入一行但未声明值时设置一个值。（如果将列定义为“not null”且未指定默认值，MySQL 将根据其数据类型为该列分配一个默认值。详情请参阅在线 MySQL 语言参考手册中的“CREATE TABLE Syntax”部分。）

以下是一个示例 create 语句，演示了这两个属性以及其他一些属性。

```sql
create table topics (
    topic_id         integer not null auto_increment,
    parent_id        integer default 0 not null,
    root_id          integer default 0,
    name             varchar(255),
    description      text null,
    create_dt        timestamp,
    modify_dt        timestamp,
    author           varchar(255) null,
    author_host      varchar(255) null,
    primary key(topic_id),
    index my_index(parent_id)
)type=myisam;
```

此语句创建一个名为 topics 的表，包含九个列和两个索引，一个用于主键，一个用于 parent_id 列。在上述语句中，使用了四种列类型：integer、varchar、text 和 timestamp。这些及许多其他列类型将在后续示例中进一步详细讨论。在着手创建表之前，您应该充分了解所有可用的列类型以及创建索引的方法。

要从命令行客户端创建表，请输入整个命令。从 PHP，请按以下方式使用 mysql_query() 函数：

```php
$conn = mysql_connect("localhost","username","password") or
die ("Could not connect to localhost");
mysql_select_db("test", $conn) or
die("could not select database");
$query = "create table my_table (
col_1 int not null primary key,
col_2 text
);";
mysql_query($query) or
die(mysql_error());
```

## 列类型

MySQL 为您提供一系列列类型。虽然其中几种相似，但它们之间存在微妙而重要的差异。阅读本节，并在决定表的列类型时谨慎选择。

### 字符串列类型

八种 MySQL 列类型适合存储文本字符串：

- char
- varchar
- tinytext/tinyblob
- text/blob
- mediumtext/mediumblob
- longtext/longblob
- enum
- set

### char
用法：char(length)

char 列类型的最大长度为 255 个字符。这是一种固定长度类型，这意味着当插入的值字符数少于列的最大长度时，字段会在右侧用空格填充。因此，如果某列定义为 char(10)，而您想要存储值 happy，MySQL 实际上会存储 happy 后跟五个空格。当从表中检索值时，这些空格会从结果中移除。长度超过列宽度的值会被截断。

### varchar
用法：varchar(length)

这种类型几乎与 char 相同，并在许多相同的场景中使用。它的最大长度也是 255 个字符。区别在于，varchar 是可变长度列类型，这意味着值不会用空格填充。相反，MySQL 会在每个 varchar 字段中添加一个字符来存储字段的长度。

MySQL 会移除 varchar 字段中字符串末尾的空格，但这种行为在未来的语言版本中可能会更改。

> 如果您定义一个列为 varchar 且列长度小于四，MySQL 会自动将该列更改为 char 类型。同样，如果您尝试混合使用长度超过四的 char 和 varchar，它们都会变成 varchars。

### 使用 char 或 varchar

在大多数情况下，char 和 varchar 之间几乎没有实际区别。您决定使用哪一个，将取决于哪一种占用的空间更多：char 列末尾的空格，还是 varchar 中的大小字节。如果您的字段存储类似姓氏的内容，您可能希望允许 25 个字符，以确保安全。如果您使用 char 列类型，而某人的姓氏是 Smith，那么您的列将包含 20 个末尾空格。没有必要这样做；您使用 varchar 并让 MySQL 跟踪列大小会好得多。然而，当您想要存储五到七个字符的密码时，使用 varchar 来跟踪列大小将是一种浪费。每次更新 varchar 字段时，MySQL 都必须检查字段长度并更改存储字段长度的字符。您最好使用 char(7)。

