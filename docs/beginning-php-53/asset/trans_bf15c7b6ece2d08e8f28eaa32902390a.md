
- 5. 为 root 用户添加密码 — 输入以下行，将 mypass 替换为要使用的密码，将 mattscomputer 替换为计算机的主机名（在表格的 Host 列中显示），并在每行后按 Enter：

```
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('mypass');
SET PASSWORD FOR 'root'@'mattscomputer' = PASSWORD('mypass');
SET PASSWORD FOR 'root'@'127.0.0.1' = PASSWORD('mypass');
```

您只需输入表格中显示的根条目对应的行。例如，如果表格不包含 127.0.0.1 主机的行，则可以省略第三个 SET PASSWORD 行。

确保选择安全的密码。至少，密码应至少 7 个字符长，并包含字母和数字的组合。

- 6. 检查密码是否已设置 — 重新输入步骤 4 中的 SELECT 行并按 Enter。您应该看到三个 root 用户的 Password 列现已设置：

| 主机 | 用户 | 密码 |
|---|---|---|
| localhost | root | *D8DECEC305209EEFEC43008E1D420E1AA06B19E0 |
| mattscomputer | root | *D8DECEC305209EEFEC43008E1D420E1AA06B19E0 |
| 127.0.0.1 | root | *D8DECEC305209EEFEC43008E1D420E1AA06B19E0 |
| localhost | | |
| mattscomputer | | |

- 7. 退出 MySQL 命令行工具 — 输入 exit 然后按 Enter 以返回 shell 提示符。

现在您已为 root 账户添加了密码，您的 MySQL 服务器相对安全。要测试新密码，请再次运行 mysql 命令，但这次在命令行末尾添加 -p（连字符后跟 "p"），如下所示：

```
mysql -u root -p # Ubuntu, Windows
./mysql -u root -p # Mac OS X
```

MySQL 将提示您输入之前输入的 root 密码。现在输入它，然后按 Enter。如果一切顺利，您应该回到 mysql> 提示符。再次，输入 exit 并按 Enter 以退出程序。

> 如果收到“Access denied”错误，请重试。如果仍无法访问，可能需要重新安装 MySQL 服务器。或者，您可能能够重置 root 密码。请参阅 MySQL 参考手册中标题为“How to Reset the Root Password”的章节，网址为 http://dev.mysql.com/doc/refman/5.1/en/resetting-permissions.html。

您现在可以使用此 root 用户在 MySQL 系统中创建和操作数据库。您稍后创建的 PHP 脚本也将使用 root 用户连接到 MySQL 数据库。虽然这对于开发和测试目的可以接受，但不应在实时服务器上的 PHP 脚本中使用 root 用户。相反，创建一个仅具有脚本所需权限的新 MySQL 用户。（如果您在共享服务器上运行网站，您的托管公司可能会为您提供用户名和密码。）

创建其他 MySQL 用户超出了本书的范围，但您可以在 MySQL 手册的账户管理语句部分中找到相关操作方法（http://dev.mysql.com/doc/refman/5.1/en/account-management-sql.html）。

mysql 程序会存储您最近输入的语句列表。（按向上键可以回退查看列表中的项目。）出于安全考虑，在设置 root 密码后最好删除此列表，因为密码会出现在此列表的 SET PASSWORD FOR 行中。在 Ubuntu 和 Mac OS X 上执行此操作：退出命令行工具，删除主目录中的 .mysql_history 文件（rm ~/.mysql_history）。在 Windows 上，只需退出命令行工具，然后关闭命令提示符窗口。

*顺便说一句，如果您不习惯使用命令行工具，还有许多图形应用程序可用于管理和访问 MySQL 服务器。尝试免费的 MySQL Administrator 和 MySQL Query Browser 程序，可从 http://dev.mysql.com/downloads/gui-tools/5.0.html 获取。一个不错的基于 Web 的工具是 phpMyAdmin（http://www.phpmyadmin.net/），它也随 WampServer 在 Windows 上捆绑提供（单击 WampServer 任务栏图标即可访问）。*

## 与 MySQL 快速上手

现在您已设置 MySQL root 用户，可以开始使用数据库。在以下部分中，您将创建新数据库、向数据库添加表并向表中添加数据。您还将学习如何查询数据库和表、更新表中的数据，以及删除数据、表和数据库。

*以下部分中的大多数示例都显示使用全大写字母输入命令、语句和其他 SQL 关键字。尽管 SQL 关键字传统上采用大写，但 MySQL 也允许您使用小写输入关键字。因此，如果您偏好小写，可以使用小写。*

### 创建新数据库

创建新 MySQL 数据库非常简单。首先，使用更改 root 密码时采用的相同方法启动 MySQL 命令行工具。打开 shell 提示符，切换到正确的文件夹（如果使用 Windows 或 Mac OS X），然后在 Ubuntu 或 Windows 上输入：

```
mysql -u root -p
```

在 Mac 上输入：

```
./mysql -u root -p
```

按 Enter。现在输入之前指定的 root 密码，然后再次按 Enter。您应该看到提示符出现：

```
mysql>
```

要创建新数据库，只需使用 CREATE DATABASE 命令。输入以下内容以创建名为 mydatabase 的新数据库：

```
CREATE DATABASE mydatabase;
```

按 Enter，MySQL 将创建新数据库。您可以键入命令 SHOW DATABASES 来查看系统中所有数据库的列表（包括新数据库）：

```
mysql> SHOW DATABASES;
+--------------------+
| Database         |
+--------------------+
| information_schema |
| mydatabase       |
| mysql            |
+--------------------+
3 rows in set (0.00 sec)
```

按 Enter 之前，请不要忘记在命令或语句末尾输入分号。

您可以看到此系统有三个数据库。information_schema 和 mysql 与 MySQL 本身的操作相关，mydatabase 是您刚刚创建的数据库。

### 创建表

如您所知，表是实际存储数据的地方。首先，您将创建一个非常简单的表 fruit，包含三个字段：id（主键）、name（水果名称）和 color（水果颜色）。

首先要做的是选择刚刚创建的数据库。选择数据库后，您输入的任何数据库操作命令都将作用于该数据库。输入以下内容：

```
USE mydatabase;
```

按 Enter，您应该看到：

```
Database changed
mysql>
```

现在创建您的表。在 mysql> 提示符处输入以下内容：

```
mysql> CREATE TABLE fruit (
->   id       SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
->   name     VARCHAR(30) NOT NULL,
->   color    VARCHAR(30) NOT NULL,
->   PRIMARY KEY (id)
-> );
```

每行末尾按 Enter。不要输入 "->" 箭头；每次按 Enter 时，MySQL 都会自动显示这些箭头，以通知您语句正在新一行继续。

如果一切顺利，您应该看到类似下面的响应：

```
Query OK, 0 rows affected (0.06 sec)
```

您现在已创建表。要查看数据库中的表列表，请使用 `SHOW TABLES` 命令：

```
mysql> SHOW TABLES;
+-----------------------+
| Tables_in_mydatabase  |
+-----------------------+
| fruit                 |
+-----------------------+
1 row in set (0.00 sec)
```

您甚至可以使用 `EXPLAIN` 命令查看新创建表的结构，如下所示：

```
mysql> EXPLAIN fruit;
+-------+-------------------------+------+-----+---------+----------------+
| Field | Type                    | Null | Key | Default | Extra          |
+-------+-------------------------+------+-----+---------+----------------+
| id    | smallint(5) unsigned    | NO   | PRI | NULL    | auto_increment |
| name  | varchar(30)             | NO   |     | NULL    |                |
| color | varchar(30)             | NO   |     | NULL    |                |
+-------+-------------------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)
```

您创建了一个包含以下三个字段的表：

- `id` 是主键。它唯一标识表中的每一行。您将 `id` 字段创建为 `SMALLINT UNSIGNED`，这意味着它可以容纳最大 65,535 的整数值（这对即使是最狂热的水果爱好者来说也足够了）。您使用了关键字 `NOT NULL`，这意味着该字段不允许 `NULL` 值。您还指定了关键字 `AUTO_INCREMENT`。这样可以确保，每当向表中添加新行时，`id` 字段会自动获得一个新的唯一值（从 1 开始）。这意味着您在插入数据时无需指定该字段的值。

- `name` 将存储每种水果的名称。它创建为 `VARCHAR(30)`，这意味着它可以容纳长度最多 30 个字符的字符串。同样，`NOT NULL` 关键字指定不允许此字段的 `NULL` 值。

- `color` 的创建方式与 `name` 相同，将用于存储每种水果的颜色。

*顺便说一句，如果您想为表中的字段创建常规键（而非主键），请使用关键字 `KEY` 或 `INDEX` 代替 `PRIMARY KEY`。因此，如果您想为 `name` 字段添加索引（因为您的表包含大量水果记录，并且经常想按名称查找水果），您可以使用（同样，不要输入箭头）：*

```
mysql> CREATE TABLE fruit (
->     id        SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
->     name      VARCHAR(30) NOT NULL,
->     color     VARCHAR(30) NOT NULL,
->     PRIMARY KEY (id),
->     KEY (name)
-> );
```
