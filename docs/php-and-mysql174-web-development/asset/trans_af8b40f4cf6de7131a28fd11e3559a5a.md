

# 第12章 高级 MySQL 管理

| 字段 | 类型 |
| --- | --- |
| File_priv | enum('N', 'Y') |
| Grant_priv | enum('N', 'Y') |
| References_priv | enum('N', 'Y') |
| Index_priv | enum('N', 'Y') |
| Alter_priv | enum('N', 'Y') |
| Show_db_priv | enum('N', 'Y') |
| Super_priv | enum('N', 'Y') |
| Create_tmp_table_priv | enum('N', 'Y') |
| Lock_tables_priv | enum('N', 'Y') |
| Execute_priv | enum('N', 'Y') |
| Repl_slave_priv | enum('N', 'Y') |
| Repl_client_priv | enum('N', 'Y') |
| Create_view_priv | enum('N', 'Y') |
| Show_view_priv | enum('N', 'Y') |
| Create_routine_priv | enum('N', 'Y') |
| Alter_routine_priv | enum('N', 'Y') |
| Create_user_priv | enum('N', 'Y') |
| Event_priv | enum('N', 'Y') |
| Trigger_priv | enum('N', 'Y') |
| Create_tablespace_priv | enum('N', 'Y') |
| ssl_type | enum('', 'ANY', 'X509', 'SPECIFIED') |
| ssl_cipher | blob |
| x509_issuer | blob |
| x509_subject | blob |
| max_questions | int(11) unsigned |
| max_updates | int(11) unsigned |
| max_connections | int(11) unsigned |
| max_user_connections | int(11) unsigned |
| plugin | char(64) |
| authentication_string | text |
| password_expired | enum('N', 'Y') |

# 详细了解权限系统

该表中的大多数行对应于来自特定主机（Host）并使用密码登录的用户的一组权限。这些是该表的*范围*（scope）字段，因为它们描述了*权限*（privilege）字段的范围。权限字段以 _priv 结尾。

此表中列出的权限（以及后续的其他表）对应于第 9 章中使用 GRANT 授予的权限。例如，Select_priv 对应于运行 SELECT 命令的权限。

如果用户拥有某个特定权限，则该列的值将为 Y。相反，如果用户没有被授予该权限，则值将为 N。

用户表中列出的所有权限都是全局的；也就是说，它们适用于系统中的所有数据库（包括 mysql 数据库）。因此，管理员在这些字段上全为 Y，但大多数用户应该全为 N。普通用户应该拥有适当数据库的权限，而不是所有表。

表中的另外两组字段是安全字段和资源控制字段。

安全字段是 `ssl_type`、`ssl_cipher`、`x5_issuer`、`x5_subject`、`plugin`、`authentication_string` 和 `password_expired`。`plugin` 字段默认为 NULL，但可以包含用于验证特定用户账户的身份验证插件。`authentication_string` 可能被插件使用。如果你启用了 SSL 连接，则使用 `ssl_type` 和 `ssl_cipher`。

## db 表

大多数普通用户的权限存储在 db 表中。

db 表决定了哪些用户可以从哪些主机访问哪些数据库。此表中列出的权限适用于特定某行中的特定数据库。

该表的结构如表 12.2 所示。

### 表 12.2 mysql 数据库中 db 表的结构

| 字段 | 类型 |
|---|---|
| Host | char(60) |
| Db | char(64) |
| User | char(16) |
| Select_priv | enum('N', 'Y') |
| Insert_priv | enum('N', 'Y') |
| Update_priv | enum('N', 'Y') |
| Delete_priv | enum('N', 'Y') |
| Create_priv | enum('N', 'Y') |
| Drop_priv | enum('N', 'Y') |
| Grant_priv | enum('N', 'Y') |
| References_priv | enum('N', 'Y') |
| Index_priv | enum('N', 'Y') |
| Alter_priv | enum('N', 'Y') |
| Create_tmp_tables_priv | enum('N', 'Y') |
| Lock_tables_priv | enum('N', 'Y') |
| Create_view_priv | enum('N', 'Y') |
| Show_view_priv | enum('N', 'Y') |
| Create_routine_priv | enum('N', 'Y') |
| Alter_routine_priv | enum('N', 'Y') |
| Execute_priv | enum('N', 'Y') |
| Event_priv | enum('N', 'Y') |
| Trigger_priv | enum('N', 'Y') |

### tables_priv, columns_priv, procs_priv 和 procs_priv 表

tables_priv、columns_priv、procs_priv 和 proxies_priv 表分别用于存储表级权限、列级权限、关于存储过程的权限以及代理相关的权限。

这些表的结构与 user 表和 db 表略有不同。tables_priv、columns_priv、procs_priv 表和 proxies_priv 表的结构分别在 12.3、12.4、12.5 节显示。

**表 12.3 tables_priv 表的结构**

| 字段 | 类型 |
|---|---|
| Host | char(60) |
| Db | char(64) |
| User | char(16) |
| Table_name | char(64) |
| Grantor | char(77) |
| Timestamp | timestamp |
| Table_priv | set('Select', 'Insert', 'Update', 'Delete', 'Create', 'Drop', 'Grant', 'Index', 'Alter', 'Show view', 'Trigger') |

#### 表 12.4 columns_priv 表的结构

| 字段 | 类型 |
|---|---|
| Host | char(60) |
| Db | char(64) |
| User | char(16) |
| Table_name | char(64) |
| Column_name | char(64) |
| Timestamp | timestamp |
| Column_priv | set('Select', 'Insert', 'Update', 'References') |

#### 表 12.5 procs_priv 表的结构

| 字段 | 类型 |
|---|---|
| Host | char(60) |
| Db | char(64) |
| User | char(16) |
| Routine_name | char(64) |
| Routine_type | enum('FUNCTION', 'PROCEDURE') |
| Grantor | char(77) |
| Proc_priv | set('Execute', 'Alter Routine', 'Grant') |
| Timestamp | timestamp |

#### 表 12.6 proxies_priv 表的结构

| 字段 | 类型 |
| --- |---|
| Host | char(60) |
| User | char(16) |
| Proxied_host | char(60) |
| Proxied_user | char(16) |
| With_grant | tinyint(1) |
| Grantor | char(77) |
| Timestamp | timestamp |

tables_priv 和 procs_priv 表中的 `Grantor` 字段存储了授予该权限的用户。这些表中的 `Timestamp` 字段存储了授予权限的时间。在 proxies_priv 表中，这些字段目前未使用。

# 访问控制：MySQL 如何使用权限表

MySQL 通过两个阶段的过程使用权限表来确定用户允许的操作：

1. 链接验证。在这里，MySQL 根据 user 表中的信息检查你是否允许连接。这种验证基于用户名、主机名和密码。如果用户名为空，则匹配所有用户。主机名可以使用通配符 (%)。该字符可以作为整个字段（即 % 匹配所有），也可以作为主机名的一部分（例如，%.example.com 匹配所有以 example.com 结尾的主机）。如果密码为空，不需要密码。如果你有空用户、主机通配符和无密码用户，系统会更安全。如果主机名为空，实际上是一个通配符，优先级低于通配符。

2. 请求验证。每次你建立连接后，MySQL 都会检查你是否拥有执行该请求的相应权限。系统首先检查你的全局权限（在 user 表），如果不足，则检查 db 表。如果你仍然没有足够的权限，MySQL 会检查 tables_priv 表，最后会检查 columns_priv 表。如果操作使用了存储过程，MySQL 会检查 procs_priv 表而不是 tables_priv 和 columns_priv 表。如果你尝试代理另一个用户或为用户授予代理权限，MySQL 会检查 proxies_priv 表。

# 更新权限：更改何时生效？

MySQL 服务器在启动以及你执行 GRANT 和 REVOKE 语句时会自动读取权限表。然而，既然你已经知道了这些权限存储在哪里以及如何存储，就可以手动修改它们。当你手动更新它们时，MySQL 服务器不会注意到它们已经发生了变化。

你需要向服务器指出发生了更改，你可以通过三种方式实现。你可以在 MySQL 提示符下输入：

```
mysql> flush privileges;
```

（你需要以管理员身份登录才能此命令。）这是更新权限的最常用方法。

或者，你可以在操作系统中运行任意一个：

- > mysqladmin flush-privileges

或

- > mysqladmin reload

最后，MySQL 服务器在重启时将重新加载权限表。当用户下次连接时；在执行 use 语句时将检查数据库权限；在用户的下一次请求时，将检查表级和列级权限。

# 确保你的 MySQL 数据库安全

安全非常，特别是当你开始将 MySQL 数据库连接到你的网站时。以下章节解释了你应该保护数据库的基本预防措施。

# 从操作系统的角度看 MySQL

如果你运行类 Unix 操作系统，以 root 身份运行 MySQL 服务器 (mysqld) 是一个坏主意。这样做会赋予拥有全套权限的 MySQL 用户在操作系统任何地方进行读写操作。。这是一个重要但容易被忽视的点，它曾被著名的用来黑入 Apache 网站。（幸运的是，黑客是“白帽”[好人]，他们唯一的行动是加强了安全性。）

专门为运行 mysql 的目的设置一个 MySQL 用户是一个好主意。此外，你就可以使目录（存储物理数据的目录）仅供 MySQL 用户访问。在许多安装中，服务器被设置为以 mysql 用户、mysql 组运行。

