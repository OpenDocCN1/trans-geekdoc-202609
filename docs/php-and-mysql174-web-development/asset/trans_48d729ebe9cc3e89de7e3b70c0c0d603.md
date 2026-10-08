

对于普通用户而言，大多数权限在系统安全方面都是相对无害的。`ALTER` 权限可以通过重命名表来绕过权限系统，但用户通常需要它。安全性始终是可用性与安全性之间的权衡。在涉及 `ALTER` 时，你应该根据情况自行决定，但它通常会被授予用户。

除了表 9.1 列出的权限外，`GRANT` 权限在权限列表之外，还会带有 `GRANT OPTION` 被授予。

表 9.2 显示了适用于管理用户的权限。

# 表 9.2 管理员权限

| 权限 | 说明 |
| --- | --- |
| CREATE TABLESPACE | 允许管理员创建、修改或删除表空间。 |
| CREATE USER | 允许管理员创建用户（如前所述）。 |
| CREATE TEMPORARY TABLES | 允许管理员在 `CREATE` 语句中使用 `TEMPORARY` 关键字。 |
| FILE | 允许从文件中读取数据到表中，反之亦然。 |
| LOCK TABLES | 允许显式使用 `LOCK TABLES` 语句。 |
| PROCESS | 允许管理员查看所有用户的服务器进程。 |
| RELOAD | 允许管理员重新加载授权表并刷新权限、主机、日志和表。 |
| REPLICATION CLIENT | 允许在复制主从上使用 `SHOW STATUS`。复制机制将在第 12 章解释。 |
| REPLICATION SLAVE | 允许复制从机连接到主服务器。复制机制将在第 12 章解释。 |
| SHOW DATABASES | 允许通过 `SHOW DATABASES` 语句查看所有数据库。没有此权限，用户只能看到他们拥有其他权限的数据库。 |
| SHUTDOWN | 允许管理员关闭 MySQL 服务器。 |
| SUPER | 允许管理员杀死属于任何用户的线程。 |

你可以将这些权限授予非管理员用户，但如果你打算这样做，请务必极其小心。

`FILE` 权限是一个特殊情况。它对用户来说很有用，因为从文件加载数据可以节省每次重新输入数据到数据库的大量时间。然而，文件加载可用于加载 MySQL 服务器可见的任何文件，包括属于其他用户的数据库，并可能包括密码文件。请谨慎授予此权限，或者为用户提供加载数据。

还存在两个特殊权限，如表 9.3 所示。

# 表 9.3 特殊权限

| 权限 | 说明 |
| --- | --- |
| ALL | 授予表 9.1 和 9.2 中列出的所有权限。你也可以用 `ALL PRIVILEGES` 代替 `ALL`。 |
| USAGE | 不授予任何权限。此权限创建一个用户并允许其登录，但不允许用户执行任何操作。通常你之后会添加更多权限。使用 `GRANT` 创建具有 `USAGE` 权限的用户等同于 `CREATE USER` 语句。 |

# REVOKE 命令

`GRANT` 的反面是 `REVOKE`。你用它从用户处撤销权限。它的语法与 `GRANT` 相似：

```
REVOKE privileges [{columns}]
ON item
FROM user_name
```

如果你提供了 `WITH GRANT OPTION` 子句，可以通过添加以下内容撤销它（以及所有其他权限）：

```
REVOKE ALL PRIVILEGES, GRANT OPTION
FROM user_name
```

# 使用 GRANT 和 REVOKE 的示例

要设置管理员，你可以输入：

```
mysql> grant all
-> on *,
-> to 'fred' identified by mnb123
-> with grant option;
```

此命令向名为 fred 的用户授予所有数据库的权限，该用户从任何主机连接，密码为 mnb123，并允许其传递这些权限。

你可能不希望在你的系统中出现这种情况，所以请直接撤销其权限：

```
mysql> revoke all privileges, grant option
-> from 'fred';
```

现在，你可以设置一个没有权限的普通用户：

```
mysql> grant usage
-> on books.*
-> to 'sally'@'localhost' identified by magic123;
```

# 为 Web 设置用户

在与 Sally 交流并稍了解她想做什么之后，你可以授予她适当的权限：

```
mysql grant select, insert, update, delete, index, alter, create, drop
-> on books.*
-> to 'sally'@'localhost';
```

注意，在授予权限时不需要指定 Sally 的密码（如此处所示）。

如果你发现 Sally 已经在数据库中执行了某些操作，你可能决定减少她的权限：

```
mysql revoke alter, create, drop
-> on books.*
-> from 'sally'@'localhost';
```

稍后当她不再需要使用数据库时，你可以完全撤销权限：

```
mysql revoke all
-> on books.*
-> from 'sally'@'localhost';
```

# 使用正确的数据库

登录时，PHP 脚本连接 MySQL 时需要的第一步是指定数据库。你可以通过输入以下命令来实现：

```
mysql> use dbname;
```

其中 `dbname` 是你的数据库名称。或者，你可以在登录时指定数据库以避免使用 `use`：

```
mysql -D dbname
```

当你输入此命令时，MySQL 应该给出如下响应：

```
Database changed
```

如果在启动之前没有选择数据库，MySQL 会给出一个错误：

```
ERROR 1046 (3000): No Database Selected
```

# 创建数据库表

设置数据库的下一步是实际创建表。你可以使用 SQL 命令 `CREATE TABLE` 完成。`CREATE TABLE` 语句的标准形式为：

```
CREATE TABLE tableName(columns)
```

# 注意

你可能知道 MySQL 提供了多种表类型或存储引擎。我们将在第 13 章讨论表类型。目前，数据库中的所有表都使用默认存储引擎（对于 MySQL 5.5，是 InnoDB）。

你应该将 `tableName` 占符替换为你创建的表名，并将 `columns` 占符替换为表中逗号分隔的列列表。每个列都将有一个名称和一个数据类型。

以下是 Book-O-Rama 的架构：

```
Customers(CustomerID, Name, Address, City)
```

```
Orders(OrderID, CustomerID, Amount, Date)
```

```
Books(ISBN, Author, Title, Price)
```

```
Order_Items(OrderID, ISBN, Quantity)
```

```
列表 9.1 列表 9.1 显示了创建这些表的 SQL，假设你已经创建了 books 数据库。你可以在 `chapter9/bookorama.sql` 文件中找到这些 SQL。

你可以通过输入以下命令通过 MySQL 运行现有的 SQL 文件：

```
> mysql -h host -u bookoram -D books -p < bookorama.sql
```

（记得替换主机名并指定 bookorama.sql 文件的完整路径）

使用文件重定向对于此任务非常方便，这意味着你可以在执行 SQL 之前使用你任的文本编辑器对其进行编辑。

# 列表 9.1 bookorama.sql—为 Book-O-Rama 创建表的 SQL

```sql
CREATE TABLE Customers
(CustomerID INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
Name CHAR(50) NOT NULL,
Address CHAR(100) not null,
City CHAR(30) not null
);

CREATE TABLE Orders
(OrderID INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
CustomerID INT UNSIGNED NOT NULL,
Amount FLOAT(6,2),
Date DATE NOT NULL
);

CREATE TABLE Books
(ISBN VARCHAR(20),
Author VARCHAR(100),
Title VARCHAR(255),
Price FLOAT(6,2));

CREATE TABLE Order_Items
(OrderID INT UNSIGNED,
ISBN VARCHAR(20),
Quantity INT);

CREATE TABLE Book_Reviews
(ISBN VARCHAR(20),
Review TEXT);
```

