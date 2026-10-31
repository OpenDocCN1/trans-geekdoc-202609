
这创建了两个文件，problems.sql 和 problems.txt。要从这些文件重新加载 problems 表，可以按如下操作：

```
mysql tracking <problems.sql
mysqlimport tracking problems.txt
```

一些最常用或有用的命令行选项显示在表 C-11 中。

## 表 C-11 mysqlimport 命令行选项

| 标志 | 替代标志 | 描述 |
|---|---|---|
| -? | --help | 显示帮助信息并退出。 |
| -d | --delete | 在导入文本文件前清空表。 |
| --fields-terminated-by=...<br>--fields-enclosed-by=...<br>--fields-optionally-enclosed-by=...<br>--fields-escaped-by=...<br>--lines-terminated-by=... |  | 这些选项的含义与 'LOAD DATA INFILE' 中对应的子句相同。 |
| -f | --force | 忽略错误。例如，如果文本文件的表不存在，则继续处理剩余文件。未指定 '--force' 时，若表不存在 mysqlimport 将退出。 |
| -h host_name | --host=host_name | 将数据导入指定主机上的 MySQL 服务器。默认主机为 'localhost'。 |
| -l | --lock-tables | 在处理任何文本文件前锁定所有表以供写入。这可确保服务器上的所有表同步。 |
| -L | --local | 从客户端读取输入文件。默认情况下，如果连接到 'localhost'（默认主机），则假定文本文件位于服务器上。 |
| -p[...] | --password[=...] | 连接服务器时使用的密码。如果命令行未提供密码，将提示输入。请注意，如果使用简写形式 `-p`，选项与密码之间不能有空格。 |
| -P port_num | --port=port_num | 用于连接到主机的 TCP/IP 端口号。（此设置用于除 'localhost' 外的主机连接，后者使用 Unix 套接字。） |
| -i<br>-r | --ignore<br>--replace | --replace 和 --ignore 选项控制对在唯一键值上重复现有记录的输入记录的处理方式。如果指定 --replace，则新行会替换具有相同唯一键值的现有行。如果指定 --ignore，则在唯一键值上重复现有行的输入行将被跳过。如果未指定任一选项，在发现重复键值时会发生错误，且文本文件的其余部分将被忽略。 |
| -s | --silent | 静默模式。仅在发生错误时写入输出。 |
| -u user_name | --user=user_name | 连接服务器时使用的 MySQL 用户名。默认值为你的 Unix 登录名。 |
| -c | --columns=... | 此选项接受以逗号分隔的字段名列表作为参数。字段列表会传递给 mysqlimport 调用 MySQL 执行的 LOAD DATA INFILE MySQL sql 命令。有关更多信息，请参阅 'LOAD DATA INFILE'。 |

## 其他实用工具

请检查 /bin 目录中随 MySQL 提供的其他实用工具。如果您使用的是 3.23，您会想要查看 myisamchk 和 myisampack。第一个修复损坏的表，第二个可确保表尽可能高效地设置。这些实用工具仅适用于 MyISAM 表。如果您使用的是 3.22，您将需要使用 isamchk 实用工具，它操作的是此版本 MySQL 中使用的 ISAM 表。

## 附录 D

### MySQL 用户管理

本附录将教你如何使用 MySQL 的授权表，这些表控制 MySQL 中的权限。

管理任何关系数据库管理系统（RDBMS）都需要一些工作。每个系统都有其独特的管理方法和在添加和删除用户账户、备份以及确保安全等任务方面的困难。管理 MySQL 并不是特别困难，但起初可能会有点令人困惑。

本书侧重于应用程序开发，而非服务器管理。因此，关于管理的详细内容超出了本书的范围。如果您负责服务器的备份和安全，您应该深入研究 MySQL 在线手册，重点关注第 21 章（备份）和第 6 章（安全）。

就本书而言，我们也希望对您——应用程序开发人员——而言，了解一些用户管理知识以及为用户分配权限的方法就足够了。

### 授权表

MySQL 用户权限存储在一系列随 MySQL 安装自动创建的表中。这些表保存在名为 mysql 的数据库中。如果您启动 MySQL 守护进程（使用 mysqld）和 MySQL 监视器（使用 mysql），并在安装后立即运行 show databases 查询，您将看到两个数据库，test 和 mysql。

在 mysql 数据库上运行 show tables 查询会列出存储用户权限的表。

```
mysql> use mysql

Database changed
mysql> show tables;
+----------------+
| Tables in mysql |
+----------------+
| columns_priv   |
| db |
| func |
| host |
| tables_priv |
| user |
+----------------+
6 rows in set (0.00 sec)

mysql>
```

这些表中的每个表都对应一个访问控制级别。您可以创建任意数量的用户，并且用户可以从各种主机访问。对于每个用户/主机组合，您可以授予对整个数据库、数据库中的特定表或表中的若干列的访问权限。此外，这些表还授予管理权限。用户可以被授予添加和删除数据库的权限，或授予向其他用户授予权限的权限。

实际上，您只想授予必要的权限。您希望保护您的数据免受过度热情和无能之人的侵害。使用 MySQL 做到这一点的最好方法是使用适当的授权表来分配权限，同时牢记以下几点：权限以分层方式授予。在 user 表中授予的权限将是通用的。如果在 user 表中授予用户 drop 权限，该用户将能够删除该 MySQL 安装中任何数据库中的任何表。

然后是 db 表，它按数据库特定方式授予权限。使用此表，您可以为整个数据库授予权限。对于任何一个表或一组表，请使用 tables_priv 表。最后，columns_priv 表允许您在表内授予对特定列的权限。如果您不需要为整个表授予权限，请确保权限在 columns_priv 表中分配。

MySQL 的最新版本使用了一些非常方便的命令，使创建用户和分配权限变得相当容易。我将在简要介绍 user、db、tables_priv 和 columns_priv 表之后讨论这些命令。

### user 表

每个需要访问 MySQL 的用户都必须列在此表中。权限可能在其他地方授予，但如果此处没有列出，用户将被拒绝连接到数据库服务器。以下是 user 表中列的列表。

```
mysql> show columns from user;
+-------------------+------------------+------+-----+---------+-------+
| Field             | Type             | Null | Key | Default | Extra |
+-------------------+------------------+------+-----+---------+-------+
| Host              | char(60)         |      | PRI |         |       |
| User              | char(16)         |      | PRI |         |       |
| Password          | char(16)         |      |     |         |       |
| Select_priv      | enum('N','Y') |       |   | N |   |   |
| Insert_priv      | enum('N','Y') |       |   | N |   |   |
| Update_priv      | enum('N','Y') |       |   | N |   |   |
| Delete_priv      | enum('N','Y') |       |   | N |   |   |
| Create_priv      | enum('N','Y') |       |   | N |   |   |
| Drop_priv        | enum('N','Y') |       |   | N |   |   |
| Reload_priv      | enum('N','Y') |       |   | N |   |   |
| Shutdown_priv    | enum('N','Y') |       |   | N |   |   |
| Process_priv     | enum('N','Y') |       |   | N |   |   |
| File_priv        | enum('N','Y') |       |   | N |   |   |
| Grant_priv       | enum('N','Y') |       |   | N |   |   |
| References_priv  | enum('N','Y') |       |   | N |   |   |
| Index_priv       | enum('N','Y') |       |   | N |   |   |
| Alter_priv       | enum('N','Y') |       |   | N |   |   |
+------------------+----------------+-------+---+---+---+---+
17 rows in set (0.00 sec)

mysql>
```

正如您现在所见，PHP mysql_connect() 函数接受三个参数：用户名、主机和密码。在前面的代码中您会看到对应的字段名。MySQL 通过用户名和主机的组合来识别用户。例如，用户 jay 可以为他用来连接 MySQL 的每个主机设置不同的权限集。如果您或您的 PHP 脚本从本地机器访问 MySQL，您通常会将主机指定为 localhost。

其他列的命名很直观。如您所见，除了 Host、User 和 Password 列外，所有列的值只能为 Y 或 N。如前所述，任何设置为 Y 的权限都将授予每个数据库的每个表。大多数列的名称对应于 SQL 语句（例如 delete、create 等）。

user 表还包含一组授予管理权限的列。这些列是 File_priv、Grant_priv、Process_priv、Reload_priv 和 Shutdown_priv。以下是这些列含义的简要说明。如果您注重安全，请谨慎授予这些权限。

- File_priv — 如果授予，此权限允许数据库服务器从文件系统读取和写入文件。您在将文件加载到数据库表时最常使用它。
- Grant_priv — 拥有此权限的用户将能够将其权限分配给其他用户。
- Process_priv — 此权限使用户能够查看和终止所有正在运行的进程和线程。
