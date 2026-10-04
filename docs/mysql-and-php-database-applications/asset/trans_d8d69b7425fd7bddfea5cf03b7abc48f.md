

# 其他工具

请检查 `/bin` 目录查看 MySQL 自带的其它工具。如果你使用的是 3.23 版本，你可能需要查看 `myisamchk` 和 `myisampack`。第一个用于修复损坏的表，第二个则可以确保表以最高效率进行设置。这些工具仅对 MyISAM 表有效。如果你使用的是 3.22 版本，你将需要使用 `isamchk` 工具，它用于该版本 MySQL 中使用的 ISAM 表。

## 附录 D

## MySQL 用户管理

本附录将教你如何使用 MySQL 的权限表，这些表控制着 MySQL 中的权限。

管理任何关系型数据库管理系统（RDBMS）都需要一些工作。每个系统在处理添加和删除用户账户、备份以及确保安全等任务时，都有其独特的管理方法和困难。管理 MySQL 并不特别困难，但起初可能会感到有些困惑。

本书侧重于应用程序开发。

对于本书的目的而言（我们也希望对你而言如此），对于应用程序开发，稍微了解用户管理以及为用户分配权限的方法就足够了。

## 权限表

MySQL 用户权限存储在随 MySQL 安装时自动创建的一系列表中。这些表保留在名为 `mysql` 的数据库中。如果你启动 MySQL 守护进程（使用 `mysqld`）和 MySQL 监器（使用 `mysql`），并在安装后运行查询 `show databases`，你将看到两个数据库：test 和 mysql。

在 `mysql` 数据库上运行 `show tables` 查询会列出所有包含用户权限的表。

```
mysql> use mysql
```

```
Database changed
mysql> show tables;
+----------------+
| Tables in mysql |
+----------------+
| columns_priv |
| db |
| func |
| host |
| tables_priv |
| user |
+----------+
6 rows in set (0.00 sec)
```

```
mysql>
```

这些表每一个都对应一个访问控制级别。你可以创建任意数量的用户，并允许用户从各种主机访问。对于每个用户/主机组合，你可以授予整个数据库的权限、数据库内特定表的权限，或者表内某些列的权限。此外，这些表还授予管理权限。可以赋予用户添加和删除表的权限，或者授予其他权限的权限。

在实践中，你可能想要授予比实际更多的权限。你希望保护数据免受过度活跃或无能人员的影响。使用 MySQL 实现此点的最佳方法是在分配权限时使用正确的权限表，并记住以下几：权限是按层次授予的。在 `user` 表中授予的权限是通用的。如果在 `user` 表中授予某个用户 `drop` 权限，该用户将能够删除 MySQL 安装中任何数据库的任何表。

然后是 `db` 表，它是基于特定数据库授予权限的。使用此表，你可以授予整个数据库的权限。对于任何一个或一组表，你可以使用 `tables_priv` 表。最后，`columns_priv` 表允许你授予表内特定列的权限。如果你不需要向整个表授予权限，请查看如何在 `columns_priv` 表中分配权限。

MySQL 的最新版本使用了一些方便的命令，可以相当容易地创建用户并分配权限。在初步查看 `user`、`db`、`tables_priv` 和 `columns_priv` 表之后，我将讨论这些方法。

### user 表

每一位需要访问 MySQL 的人都必须列在此表中。权限可以在其他地方授予，但如果没有在这里列出，用户将无法连接到数据库服务器。以下是 `user` 表中的列列表。

```
mysql> show columns from user:
```

| Field | Type | Null | Key | Default | Extra |
|------ |------ | ---- | ----- | --------- |------- |
| Host | char(60) | | PRI | | |
| User | char(16) | | PRI | | |
| Password | char(16) | | | | |
| Select_priv | enum('N','Y') | N | | |
| Insert_priv | enum('N','Y') | N | | |
| Update_priv | enum('N','Y') | N | | |
| Delete_priv | enum('N','Y') | N | | |
| Create_priv | enum('N','Y') | N | | |
| Drop_priv | enum('N','Y') | N | | |
| Reload_priv | enum('N','Y') | N | | |
| Shutdown_priv | enum('N','Y') | N | | |
| Process_priv | enum('N','Y') | N | | |
| File_priv | enum('N','Y') | N | | |
| Grant_priv | enum('N','Y') | N | | |
| References_priv | enum('N','Y') | N | | |
| Alter_priv | enum('N','Y') | N | | |

17 rows in set (0.00 sec)

如你所见，`mysql_connect()` 函数需要三个参数：用户名、主机和密码。前面的代码中使用了相应的字段名。例如，对于连接到 MySQL 的每个主机，用户可以拥有不同的权限集。如果你的 PHP 脚本从本地机器访问 MySQL，其他列是直观地命名的。正如你可以看到的，`Host`、`User` 和 `Password` 列只允许 `Y` 或 `N` 值。如前面提到的，任何设置为 `Y` 的权限将授予每个数据库的每个表。

`user` 表还包含一组授予管理权限的列。这些列是 `File_priv`、`Grant_priv`、`Process_priv`、`Reload_priv` 和 `Shutdown_priv`。以下是这些列的简单说明。如果你注重安全，请谨慎地授予这些权限。
- `File_priv`: 如果授予，此权限允许数据库服务器从文件系统读写文件。向数据库加载文件时经常使用它。
- `Grant_priv`: 拥有此权限的用户可以向其他用户授予权限。
- `Process_priv`: 此权限允许用户查看并杀死所有运行中的进程和线程。
- `Reload_priv`: 本书未涵盖此列授予的大多数权限。此权限通常配合 `mysqladmin` 工具的 `flush` 命令使用。
- `Shutdown_priv`: 允许使用 `mysqladmin shutdown` 关闭守护进程。

### db 表

对于特定数据库的权限，`db` 表是你大部分工作的地方。以下是 `db` 表的列列表：

```
mysql> show columns from db:
```

| Field | Type | Null | Key | Default | Extra |
| --- | --- | --- | --- | --- | --- |
| Host | char(60) | | PRI | | |
| Db | char(32) | | PRI | | |
| User | char(16) | | | | |
| Select_priv | enum('N','Y') | N | | |
| Insert_priv | enum('N','Y') | N | | | |
| Update_priv | enum('N','Y') | N | | | |
| Delete_priv | enum('N','Y') | N | | | |
| Create_priv | enum('N','Y') | N | | | |
| Drop_priv | enum('N','Y') | N | | | |
| Grant_priv | enum('N','Y') | N | | | |
| References_priv | enum('N','Y') | N | | | |
| Index_priv | enum('N','Y') | N | | | |
| Alter_priv | enum('N','Y') | N | | | |

13 rows in set (0.01 sec)

```
mysql>
```

它的工作方式与 `user` 表类似，权限仅对列中指定的数据库有效。

### tables_priv 和 columns_priv

对于仅访问数据库内单表或一组表的用户，确切的权限将在此表中。注意 `table_priv` 和 `columns_priv` 表使用了 `set` 列类型。特定用户可获得的所有权限都将挤在这单元格中。

```
mysql> show columns from tables_priv:
```

| Field | Type | Null | Key | Default | Extra |
| --- | --- | --- | --- | --- | --- |
| Host | char(60) | | PRI | | |
| Db | char(60) | | PRI | | |
| User | char(16) | | PRI | | |
| Table_name | char(60) | | PRI | | |
| Grantor | char(77) | MUL | | | |
| Timestamp | timestamp(14) | NULL | | | |
| Table_priv | set('Select', 'Insert', 'Update', 'Delete', 'Create', 'Drop', 'Grant', 'References', 'Index', 'Alter') | | | |
| Column_priv | set('Select', 'Insert', 'Update', 'References') | | | |

8 rows in set (0.00 sec)

> 在本书的几处，我们建议使用 `set` 列类型。事实上，`db` 表是使用 `set` 有意义的良好示例。该列的潜在值很少，且潜在值的数量不太改变。

## Grant 和 Revoke 语句

由于上述表是普通的 MySQL 表，你可以使用已经熟悉的 SQL 语句来修改它们。但想象一下那将是怎样的噩梦。如果你想授予新用户表级访问权限，你首先需要使用类似这样的 SQL 语句向 `user` 数据库中插入一行：

```
INSERT INTO user (Host, User, Password, Select_priv, Insert_priv, Update_priv, Delete_priv, Create_priv, Drop_priv, Reload_priv, Shutdown_priv, Process_priv, File_priv, Grant_priv, References_priv, Index_priv, Alter_priv) VALUES ('localhost', 'juan', 'password', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N', 'N');
```

