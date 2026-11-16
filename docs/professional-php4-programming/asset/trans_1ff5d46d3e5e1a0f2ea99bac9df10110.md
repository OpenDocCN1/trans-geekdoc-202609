

## allow_url_fopen

这将禁用对其他 Web 或 FTP 服务器上远程文件的打开。如果不需要访问其他 HTTP 或 FTP 站点上的文件，则请将此关闭。

## Safe Mode

为了解决共享服务器安全问题，PHP 具有一个名为安全模式（safe mode）的功能。该功能限制脚本可以执行的操作，从而限制可能存在恶意意图的脚本对服务器及服务器上他人工作所造成的损害。

当安全模式开启时，PHP 会检查当前脚本的所有者是否与尝试打开的任何文件的所有者相同。如果用户 ID 不匹配，PHP 将发出警告，告知用户此功能已受限。

php.ini 文件中还有几个与安全模式行为直接相关的设置。以下将对这些设置进行说明。

## safe_mode

此指令控制安全模式是开启还是关闭。默认情况下，它被设置为 off。

## safe_mode_gid

通常，当 safe_mode 打开文件时，文件所有者的用户 ID 必须与脚本的用户 ID 相同。如果启用此选项，则会稍微放宽此限制，只需组 ID 相同即可。默认情况下，此选项为 off。

## safe_mode_exec_dir

此指令是安全模式下用户可以执行程序的目录列表。如果程序不在此列表中的任何目录中，程序执行将失败。符号链接会被解析，因此无法通过使用符号链接来绕过此指令。

## safe_mode_allowed_env_vars

安全模式下用户可以设置的环境变量名称前缀列表。默认情况下，此项设置为 PHP_，因此只有以 PHP_ 开头的环境变量可以被设置。

## safe_mode_protected_env_vars

这是安全模式下受显式保护的变量列表。即使 safe_mode_allowed_env_vars 允许更改所有环境变量，此设置也会阻止此处列出的任何变量被更改。默认情况下，此项设置为 LD_LIBRARY_PATH。

## 保护 MySQL

MySQL 是最流行的开源数据库服务器之一。花些时间确保其安全是值得的。MySQL 的默认安装并不特别安全；以下步骤将帮助您进一步提升其安全性。

如果您已经安装了 MySQL 的默认版本，则可能希望从运行 MySQL 的计算机上浏览 http://www.canowhoopass.com/weav/wssig/nusphere/testnusphere.php。

和往常一样，保护 MySQL 需要您确切了解自己需要从中获得什么，以及需要向数据库授予什么权限。

## MySQL 与 Root 用户

以 root 身份运行 MySQL 可能会造成灾难性后果。这是导致 apache.org 被攻破的主要原因之一。最好创建一个 mysql 用户或等效用户，并在该用户下使用 mysqld_safe 包装器运行 MySQL。仅此一步就能极大地提升 MySQL 的安全性。

要实现此目标，我们需要确保此非特权用户可以访问 MySQL 数据目录，并且可以执行 MySQL 二进制文件。我们首先需要关闭服务器；为此，请发出以下命令：

```
mysqladmin -p -u root shutdown
```

假设 MySQL 的数据目录位于 /home/mysql/data，我们需要确保这些目录仅可供 mysql 用户访问（在以下命令中简称为 mysql 用户）。我们可以在 shell 中发出以下命令，以确保情况如此：

```
chown -R mysql /home/mysql/data
chmod -R go-rwx /home/mysql/data
```

如果这些目录中存在任何符号链接，请确保在符号链接的目标上运行相同的命令。

另外，请检查 unix 套接字是否不在数据目录中。为确保情况如此，请在编译时使用 –with-unix-socket-path 配置选项。

最后，重新启动 MySQL 服务器。我们使用 mysqld_safe 脚本来完成此操作，指示其以 mysql 用户身份运行：

```
mysqld_safe -user=mysql &
```

您可以在 my.cnf 文件的 [mysqld] 部分中指定此选项，以避免每次启动 mysql 时都使用 user 选项：

```
user=mysql
```

还需要采取的另一项安全预防措施是确保 /etc/my.cnf 文件安全。否则，没有什么能阻止有人将 User 指令设置为 root。该文件应由 root 拥有，但所有人都可读。以下命令应能实现此目标：

```
chown root /etc/my.cnf
chmod 644 /etc/my.cnf
```

## 清理

移除默认安装中包含的任何冗余内容也是个好主意。这包括：

- [ ] 移除测试数据库
- [ ] 移除远程访问
- [ ] 移除无需用户名的访问
- [ ] 确保 root 登录已设置密码

为此，请从命令行登录到您的数据库服务器：

```
mysql -u root -p
```

这将以 root 用户身份登录到您的数据库服务器。如果 root 用户没有密码，则不应使用 -p 选项，否则将不授予访问权限。如果在此过程中遇到问题，请参阅 MySQL 文档。我们的首要任务是移除测试数据库。我们根本不需要它，而且和往常一样，它的存在可能会使您面临攻击风险：

```
mysql> DROP DATABASE test;
```

上述 SQL 命令将为您完成此操作。现在，我们需要稍微整理一下允许的访问权限。MySQL 使用 mysql 数据库来存储关于访问权限和服务器上其他数据库的信息。因此，我们必须选择 mysql 数据库作为要操作的数据库。以下 SQL 将完成此操作：

```
mysql> USE mysql;
```

现在我们要完成移除测试数据库、移除远程访问、移除无需用户名的访问，并为我们的 root 登录设置密码：

```
mysql> DELETE FROM db WHERE Db LIKE 'test%';
```

这将从权限表中移除任何关于测试数据库的条目。我们现在使用以下 SQL 命令移除对 MySQL 服务器的远程访问：

```
mysql> DELETE FROM user WHERE host='%';
```

接下来，我们移除任何没有用户名的用户条目：

```
mysql> DELETE FROM user WHERE User='';
```

我们要确保 root 已设置密码。请确保选择一个安全的密码——字母数字字符和标点符号的组合是不错的选择：

```
mysql> UPDATE user SET Password = PASSWORD("jgt4*92smck") WHERE User = 'root';
```

最后，我们需要确保 MySQL 重新加载其权限表，以便识别更改。我们通过发出以下 SQL 命令来完成此操作：

```
mysql> FLUSH PRIVILEGES;
```

## 管理 MySQL 用户

在清理了我们的安装并使其相当安全后，我们需要考虑用户实际需要什么访问权限。最常见的是对整个数据库拥有读取权限，以及对数据库中可能只有的一两个表拥有写入权限；我们将此用户称为 webuser。我们可能还有一个受密码身份验证保护的管理 PHP 脚本，它需要能够读写我们数据库中的所有表；我们将此用户称为 adminuser。

在此示例中，我们假设有一个名为 web site 的数据库，包含三个表 - users、news 和 log_tbl。users 表用于存储在网站上注册的用户的信息。因此，webuser 需要对此表拥有 SELECT、INSERT 和 UPDATE 权限。news 表用于存放新闻条目。新的新闻条目只能由管理员插入或更新，因此 webuser 只需要对此表拥有 SELECT 访问权限。最后，log_tbl 表用于记录每次网站访问的信息。因此，两个用户都需要对此表拥有 SELECT 或 INSERT 访问权限，但两个用户都不应拥有 UPDATE 或 DELETE 访问权限。

我们将看到如何按照上述详细信息设置两个用户。

首先，登录到 mysql 服务器：

```
mysql -uroot -p
Enter password: ******
```

现在我们需要创建两个用户，最初将给予他们对整个 web site 数据库的 SELECT 访问权限：

```
mysql> GRANT SELECT ON web site.* TO webuser@localhost IDENTIFIED BY
'secure_password';
mysql> GRANT SELECT ON web site.* TO adminuser@localhost IDENTIFIED BY
'secure_password2';
```

webuser 还需要对 users 表拥有 INSERT 和 UPDATE 权限，以及对 log_tbl 表拥有 INSERT 权限。我们使用以下 SQL 命令授予这些权限：

```
mysql> GRANT INSERT, UPDATE ON web site.users TO webuser@localhost;
mysql> GRANT INSERT ON web site.log TO webuser@localhost;
```

adminuser 需要对 users 表拥有 INSERT、UPDATE 和 DELETE 权限，对 news 表拥有 INSERT 和 UPDATE 权限，以及对 log_tbl 表拥有 INSERT 权限。我们使用以下 SQL 命令完成此操作：

```
mysql> GRANT INSERT, UPDATE, DELETE ON web site.users TO adminuser@localhost;
mysql> GRANT INSERT, UPDATE ON web site.news TO adminuser@localhost;
mysql> GRANT INSERT ON web site.log_tbl TO adminuser@localhost;
```

