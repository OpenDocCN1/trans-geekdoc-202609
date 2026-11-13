

请注意，我们没有授予任何额外权限（USAGE 权限除了允许用户登录之外，不允许用户做任何其他事情），但用户现有的权限保持不变。

现在让我们创建一个名为 jessica 的新用户，她将从 host.net 域中的各种机器连接。假设她负责保持数据库中用户的姓名和电子邮件地址为最新状态，但有时可能需要查阅其他数据库信息。因此，她将拥有 db 数据库的只读（即 SELECT）访问权限，但能够更新 Users 表的 name 和 email 列。以下是命令：

```sql
mysql> GRANT SELECT ON db.*
   -> TO jessica@%.host.net
   -> IDENTIFIED BY "jessrules";
mysql> GRANT UPDATE (name,email) ON db.Users
   -> TO jessica@%.host.net;
```

请注意在第一个命令中，我们如何在主机名中使用 %（通配符）字符来指示 Jessica 可以从哪里连接。还请注意，我们没有给她将权限传递给其他用户的能力，因为我们没有在命令末尾添加 WITH GRANT OPTION。第二个命令演示了如何为特定表列授予权限——它在被授予的权限后的括号中列出用逗号分隔的列。

## 使用 REVOKE

顾名思义，REVOKE 命令用于从用户中撤销之前授予的权限。该命令的语法如下：

```sql
mysql> REVOKE privileges [(columns)]
   -> ON what FROM user;
```

该命令中的所有字段的工作方式与上面 GRANT 中的相同。要撤销 Jessica 的同事的 DROP 权限（例如，如果他或她偶尔不小心删除表和数据库的习惯已被证明），您将使用此命令：

```sql
mysql> REVOKE DROP ON *.* FROM idiot@%.host.net;
```

撤销用户的登录权限几乎是唯一无法使用 GRANT 和 REVOKE 完成的事情。REVOKE ALL ON *.* 肯定会阻止用户除了登录之外做任何有后果的事情，但要完全删除用户，需要在 user 表中删除相应的条目：

```sql
mysql> DELETE FROM user
   -> WHERE User="idiot" AND Host="%.host.net";
```

## 访问控制提示

由于 MySQL 访问控制系统的工作方式，在开始创建用户之前，您应该了解一些特性。

当您创建只能从运行该服务器的计算机上登录到 MySQL 服务器的用户时（即，您要求他们使用 Telnet 或 SSH 登录到服务器并从那里运行 MySQL 客户端，或使用 PHP 等服务器端脚本进行通信），您可能会问自己 GRANT 命令的用户部分应该是什么。假设服务器运行在 www.host.net 上。您应该将用户设置为 username@www.host.net 还是 username@localhost？

答案是，您不能完全依赖其中任何一种来处理所有连接。理论上，如果用户在连接时指定主机名（无论是使用 mysql 客户端还是使用 PHP 的 mysql_connect 函数），该主机名都必须与访问控制系统中的条目匹配。但由于您可能不想强迫用户以特定方式指定主机名（事实上，mysql 客户端的用户可能根本不想指定主机名），因此最好使用一个权宜之计。

对于需要能够从运行 MySQL 服务器的同一台机器上连接的用户，最好在 MySQL 访问系统中创建两个用户条目：一个使用机器的实际主机名（例如 username@www.host.net），另一个使用 localhost（例如 username@localhost）。当然，您需要分别向这两个用户条目授予/撤销所有权限，但这是您真正可以依赖的唯一权宜之计。

MySQL 管理员面临的另一个常见问题是，主机名中包含通配符的用户条目（如上面的 jessica@%.host.net）无法正常工作。出现这种情况时，通常是由于 MySQL 对访问控制系统中条目排序优先级的方式造成的。具体来说，它会对条目进行排序，使更具体的主机名排在前面（例如，www.host.net 是完全具体的，%.host.net 不那么具体，% 则完全不具体）。

在全新安装中，MySQL 访问控制系统包含两个匿名用户条目（允许从本地主机使用任何用户名进行连接——这两个条目是为了支持从 localhost 和服务器实际主机名进行连接，如上所述），以及两个 root 用户条目。上述问题发生在匿名用户条目优先于我们的新条目时，因为它们的主机名更具体。

让我们看看在向我们虚构的 MySQL 服务器 www.host.net 添加了 Jessica 的条目后，user 表的精简内容。以下行按 MySQL 服务器在验证连接时考虑它们的顺序排序：

| 主机 | 用户 | 密码 |
|---|---|---|
| localhost | root | (加密值) |
| www.host.net | root | (加密值) |
| localhost | | |
| www.host.net | | |
| %.host.net | jessica | (加密值) |

如您所见，由于 Jessica 的条目具有最不具体的主机名，它排在列表的最后。当 Jessica 尝试从 www.host.net 连接时，MySQL 服务器会将其连接尝试与一个匿名用户条目匹配（空 User 值匹配任何人）。由于这些匿名条目不需要密码，而 Jessica 显然输入了她的密码，MySQL 会拒绝连接尝试。即使 Jessica 设法在没有密码的情况下连接，她也将获得分配给匿名用户的（非常有限的）权限，而不是分配给她在访问控制系统中的条目的权限。

解决这个问题的办法是，要么将 MySQL 管理员的首要任务定为删除那些匿名用户条目（DELETE FROM user WHERE User=""），要么为所有需要从 localhost 连接的用户再提供两个条目（即针对 localhost 和服务器实际主机名的条目）：

| 主机 | 用户 | 密码 |
|---|---|---|
| localhost | root | (加密值) |
| www.host.net | root | (加密值) |
| localhost | jessica | (加密值) |
| www.host.net | jessica | (加密值) |
| localhost | | |
| www.host.net | | |
| %.host.net | jessica | (加密值) |

为每个用户维护三个用户条目（以及三组权限）过于繁琐，因此我建议您删除匿名用户，除非您特别需要他们：

| 主机 | 用户 | 密码 |
|---|---|---|
| localhost | root | (加密值) |
| www.host.net | root | (加密值) |
| %.host.net | jessica | (加密值) |

## 被锁定？

就像把钥匙锁在车里一样，在花一个小时安装和调试新 MySQL 服务器后忘记密码，可以说是相当尴尬。幸运的是，如果您对运行 MySQL 服务器的计算机拥有 root 访问权限，或者可以以您设置用于运行 MySQL 服务器的用户身份登录（如果您遵循第 1 章中的说明，则为 mysqlusr），那么一切尚未失去。接下来的程序将使您重新控制服务器。

首先，您必须关闭 MySQL 服务器。由于您通常会使用 mysqladmin 执行此操作，而 mysqladmin 需要您忘记的密码，因此您将不得不终止服务器进程来关闭它。使用 ps 命令，或查看服务器的 PID 文件（在 MySQL 数据目录中）以确定 MySQL 服务器的进程 ID，然后使用此命令终止它：

```
% kill pid
```

pid 是 MySQL 服务器的进程 ID。这应该足以停止服务器。除非万不得已，否则请勿使用 kill -9，因为这可能会损坏您的表文件。但是，如果您被迫这样做，下一节提供了随后检查和修复这些文件的说明。

既然服务器已关闭，您可以通过运行 safe-mysqld（mysqld-opt.exe、mysqld-nt.exe 或您在 Windows 下决定使用的任何服务器可执行文件）并带上 --skip-grant-tables 命令行选项来重新启动它。这指示 MySQL 服务器允许任何人无限制访问。显然，您会希望尽可能少地以这种模式运行服务器，以避免固有的安全风险。

连接后，将您的 root 密码更改为您能记住的内容：

```sql
mysql> USE mysql;
mysql> UPDATE user SET Password=PASSWORD("newpassword")
-> WHERE User="root";
```

最后，断开连接，并指示 MySQL 服务器重新加载授权表以开始要求密码：

```
% mysqladmin flush-privileges
```

搞定——没人需要知道您做了什么。至于把钥匙锁在车里，那您就得自己想办法了。

## 检查和修复 MySQL 数据文件

在停电、需要 kill -9 MySQL 服务器进程的情况，或者当 Jessica 的朋友 idiot@%.host.net 把插头从墙上踢掉时，MySQL 数据文件可能会损坏。这可能会

