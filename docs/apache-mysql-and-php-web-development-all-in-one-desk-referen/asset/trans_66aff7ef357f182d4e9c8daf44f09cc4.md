
要分配这些权限，请执行以下步骤：

- 1. 首先，如果尚未创建 jessica 数据库，请创建它。

为此，请进入 mysql 实用程序并键入以下内容：

```
create database jessica;
```

- 2. 如果尚未为 MySQL 创建 jessica 用户名，请一次性创建用户名并设置权限，如下所示：

```
grant all privileges on jessica.* to jessica@localhost
identified by 'jessicapass';
```

或者，如果您已经为 MySQL 创建了 jessica 用户名，可以按照以下步骤限制权限：

- a. 撤销主系统的权限：

```
revoke all on *.* from jessica@localhost;
```

- b. 如果您之前给 Jessica 授予了其他数据库（例如 phpbase 数据库）的权限，您也可以按照以下方式撤销这些权限：

```
revoke all on phpbase.* from jessica@localhost;
```

- c. 现在授予 Jessica 使用 jessica 数据库的权限：

```
grant all privileges on jessica.* to jessica@localhost;
```

下面是一个使用用户名 jessica 的示例会话，演示她只能访问名为 jessica 的数据库：

```
mysql -u jessica -p
Enter password: *********
Welcome to the MySQL monitor.
mysql> show databases;
+----------+
| Database |
+----------+
| jessica  |
| mysql    |
| phpbase  |
+----------+
3 rows in set (0.02 sec)
mysql> use menagerie;
ERROR 1044: Access denied for user: 'jessica@localhost'
to database 'menagerie'
mysql> use jessica;
Database changed
```

## 将数据库移动到另一台计算机

如果要将数据库移动到另一台计算机，我建议直接复制文件。这显然是最简单的方法。移动数据库的不同方法取决于您的操作系统，如下所示：

- 在 Linux 中：转到 mysql 安装目录，查看 data 目录下的内容。您将看到一个名为 data 的目录，其中包含每个数据库的单独子目录。您可以将该子目录复制到共享文件系统，从而将其复制到另一台计算机。如果未看到 data 目录，请尝试在 /var/lib/mysql 中查找，这是查找数据库子目录的另一个常见位置。

- 在 Windows 中：转到目录 c:\mysql\data（或者您放置 mysql 的任何位置，对我来说，data 目录是 C:\Program Files\mysql\data）。在该目录中，查找与您的数据库同名的子目录。将该子目录及其所有内容复制到磁盘、CD-ROM、共享驱动器，或者星际薯子波网络连接（等他们发明该技术时）。然后切换到另一台计算机，进入该计算机相同的 mysql\data 目录，并将数据库目录复制到 data 目录中。确保在复制过程中创建数据库目录（或手动创建它）。

## 管理表

要创建表，您需要一个数据库。在此数据库中，您可以创建任意数量的表。

表是以行形式存储的数据集合，这些行有些人称为记录。每条记录由一组列组成，这些列有些人称为字段。以下是名为 candy 的表的描述示例：

- name 是 varchar(30)。
- weight 是 double。
- price 是 int。
- quantity 是 int。

candy 表中的每行信息都包含名称、重量、价格和数量。名称的类型为 varchar(30)（varchar(30) 表示最长 30 个字符的字符串）。重量是 double（即双精度浮点数）。价格以美分表示的整数（永远不要对美元使用浮点变量；相反，应使用美分的整数，因为整数数学比浮点数学更准确），数量是整数。

在接下来的章节中，我将向您展示如何在 MySQL 中创建此表、获取表的信息、删除表，以及查看其他可用表。

在接下来的章节中，您将使用名为 phpbase 的数据库。要使用该数据库，请先以 root 身份登录 mysql，然后键入以下内容：

```
use phpbase
```

现在您可以继续进行示例操作了。

尽管以下示例使用 mysql 命令行实用程序，但请记住，您键入的语句是 SQL 语言语句，您可以在独立于 mysql 实用程序运行的程序中使用这些语句。

### 创建表

创建表很简单。以下是流程概要：

- 您使用一个称为 `create table` 的专用 SQL 关键字。（好吧，那是两个关键字。）
- 您提供表名，并在括号中提供表中列的描述。
- 您以分号结尾。

假设您已启动 mysql 实用程序并正在使用数据库 phpbase，您可以在 mysql 提示符下键入以下行：

```
create table candy (
   name varchar(30),
   weight double,
   price int,
   quantity int
);
```

在您键入每行并按 Enter 键时，mysql 实用程序会识别出您尚未键入分号，因此会用以下字符开始下一行：

```
->
```

这些字符表示您可以继续键入命令。（您在此处看到的 `create table` 命令跨越了多行。）

运行此命令后，您会看到一条快乐、友好（虽然几乎毫无意义）的消息：

```
Query OK, 0 rows affected (0.01 sec)
```

此消息表示您已成功创建表。

### 向表中添加行

如果您有一个表，您可能不想让它无所事事地闲置着。相反，您想往里面放一些数据。（嘿，你做了这个东西——不妨用起来。）在第 VI 卷第 3 章中，我讨论了可以放入表中的数据类型以及如何将表相互关联。目前，我继续使用我在上一节“创建表”中创建的名为 candy 的表。

candy 表中的每行都包含字符串形式的名称、双精度浮点变量形式的重量，以及整数形式的价格和数量。以下是如何从 mysql 实用程序向此表添加一行数据（确保您正在使用 phpbase 数据库）：

```
insert into candy values(
 'OozingPeanutbutterExplosion',
 6.95,
 275,
 100,
 );
```

此代码向 candy 表添加了一行新数据，包括名称 'OozingPeanutbutterExplosion'（真好吃）、重量 6.95（我猜是盎司，这已经很多了）、以 275 美分表示的 2.75 美元价格，以及数量 100，这代表即将进入我肚子的数量。

此代码只添加了一行（或记录）。您可以使用不同的名称和值添加更多行。如果不想，也不需要将行拆分为多行：

```
insert into candy values('ChunkableCrunchableChocolate', 2.80, 75, 50);
```

### 查看表中的数据

如果您有一个（例如名为 candy 的）包含数据的表，可以使用 mysql 命令行实用程序查看表中的数据。为此，您需要使用 select 语句。（select 一词是 SQL 语言的一部分，我将在第 VI 卷第 5 章中讨论。）

确保您正在运行 mysql 实用程序并使用 phpbase 数据库。然后，通过键入以下命令查看 candy 表：

```
select * from candy;
```

数据会以整齐漂亮的表格形式打印出来，如下所示：

| 名称 | 重量 | 价格 | 数量 |
|---|---|---|---|
| OozingPeanutbutterExplosion | 6.95 | 275 | 100 |
| ChunkableCrunchableChocolate | 2.8 | 75 | 50 |

2 行，用时 0.00 秒

此表包含两行，一行是关于 Oozing 什么的，下一行是关于 Chunkable Chocolate 什么的。

如果您愿意，可以通过将前面 select 语句中的星号替换为用逗号分隔的列名，只查看几个列：

```
select quantity, weight from candy;
```

该语句的输出结果如下：

| 数量 | 重量 |
|---|---|
| 100 | 6.95 |
| 50 | 2.8 |

2 行，用时 0.00 秒

此处我只查看数量和重量列。请注意，它们按我在 select 语句中输入的顺序出现在列表中：我先输入了 quantity，再输入了 weight，尽管表中先存储 weight，后存储 quantity。

排序信息的快捷方法是将 order by 放入语句中，如下所示：

```
select price, weight, quantity
from candy
order by price;
```
