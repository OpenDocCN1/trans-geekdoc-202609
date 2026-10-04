
# 第 V 部分：附录

然后，你可能需要通过另一个 `insert` 语句到另一个表来授予特定的权限。

如果你认为你可以用 Web 前端为这些函数编写脚本，这绝对是可能的。但你必须非常小心，因为脚本将拥有等同数据库 root 的权限，这可能非常不安全。

幸运的是，MySQL 有一些内置语句，可以让用户管理变得简单得多。掌握 `grant` 和 `revoke` 语句将让你避免必须发送单个查询。

# Grant (授予)

在介绍该语句的具体细节之前，先看一个授予用户 `jim` `guestbook` 数据库的所有权限的语句；`jim` 的密码将通过验证。

```mysql
mysql grant all on guestbook.* to jim@localhost identified by "password";
```

此命令将对 `user` 表和 `db` 表进行所有必要的更改。`grant` 语句的第一部分可以采用 `user` 表中列出的任何选项。通常情况下，你会授予使用 SQL 语句的权限（select, create, alter, delete, drop, index, insert 和 update）。

## 表 D-1 权限级别
| 标识符 | 含义 |
|---|---|
| grant all on .* | 通用权限；插入到 user 表中 |
| grant all on database.* | 适用于单个数据库中的所有表 |
| grant all on database.table_name | 权限适用于单个表 |
| grantall(col1, col2) on database.table_name | 权限仅适用于特定数据库和表中的特定列。 |

第三部分（示例中为 `to jim@localhost`）表示要授予访问权限的用户。正如我们之前提到的，MySQL 同时需要用户名和主机名。在 `grant` 语句中，它们通过 `@` 符号隔开。

最后，`identified by` 部分为用户提供了密码。
以下是几个 `grant` 语句的示例。

```mysql
grant select, update, insert on guestbook2k.guestbook to alvin@localhost identified by "pword":
```

前述语句允许 `alvin` 查看、更新并向 `guestbook2k` 数据库中的 `guestbook` 表中插入记录。

```mysql
grant select, update (name, url) on guestbook2k.guestbook to chipmunk@localhost identified by "Mell2068":
```

通过前述语句，用户 `chipmunk` 只能查看和更新两个列（name 和 URL）。不允许删除或插入。

```mysql
grant all on *.* from josh@localhost identified by "pword":
```

前述语句赋予该用户所有权限。这意味着 `josh@localhost` 甚至被允许向其他用户授予权限。

# Revoke (撤销)

如果你想移除用户的某些权限，可以使用 `revoke` 语句。要从像上面 `j` 这样已授予权限的用户处移除 `shutdown` 权限，你可以运行以下命令：

```mysql
revoke Shutdown on *.* from josh@localhost
```

注意 `revoke` 语句中使用的是 `from` 而不是 `to`。
否则，`revoke` 的工作方式与 `grant` 相同。

注意，要完全删除一个用户，你必须对 `user` 表运行 `delete` 语句。由于用户是通过用户名和主机名标识的，以下操作应该：

```sql
delete from user where user='user' and host='host'
```

# Viewing grants (查看授予权限)

从 3.23.4 版本开始，MySQL 引入了 `show grants` 语句，允许你查看当前可用的授权。你只需要知道用户名和主机名。

```mysql
mysql> show grants for jayg@localhost:
+----------------------------------------------------------------+
| Grants for jayg@localhost                                |
+----------------------------------------------------------------+
```

# Reloading grants (重新加载授予权限)

当 MySQL 守护进程启动时，权限表会被加载到内存中。对权限表所做的更改，如果没有使用 `grant` 命令完成，这些更改在重启程序或使用 `flush` 命令告诉 MySQL 重新加载表之前将不会生效。

只需运行：

```mysql
flush privileges
```

# 附录 E

# PHP 函数参考

在**此时**，PHP 包含的函数数量已经超出了本书可能列出的所有数量，而且函数列表每天都在增长。表 E-1 到 E-43 是某些可用函数的列表。请关注 www.php.net/manual 的在线手册以查看最新列表。

## 表 E-1 PHP 信息函数
| 函数 | 返回 | 操作 |
| --- | --- | --- |
| phpinfo(void) | void | 输出关于 PHP 和当前请求的有用信息页面 |
| phpversion(void) | string | 返回当前的 PHP 版本 |
| phpcreds(void) | void | 打印贡献过 PHP 项目的人员 |

## 表 E-2 变量类型函数
| 函数 | 返回 | 操作 |
| --- | --- | --- |
| intval(mixed var [ , int base]) | int | 使用可选的基数获取变量的整数值 |
| doubleval(mixed var) | double | 获取变量的双倍精度值 |
| strval(mixed var) | string | 获取变量的字符串值 |
| gettype(mixed var) | string | 返回变量类型 |

## 表 E-2 变量类型函数（继续）
| 函数 | 返回 | 操作 |
| --- | --- | --- |
| settype(string var, string type) | int | 设置变量的类型。如果转换成功则返回 1 |
| is_bool(mixed var) | bool | 如果变量是布尔值则返回 true |
| is_long(mixed var) | bool | 如果变量是长整数（整数）则返回 true |
| is_double(mixed var) | bool | 如果变量是双精度浮点数则返回 true |
| is_string(mixed var) | bool | 如果变量是字符串则返回 true |
| is_array(mixed var) | bool | 如果变量是数组则返回 true |
| is_object(mixed var) | bool | 如果变量是对象则返回 true |
| is_numeric(mixed var) | bool | 如果变量是数字则返回 true |

## 表 E-3 引号设置函数
| 函数 | 返回 | 操作 |
| --- | --- | --- |
| set_magic_quotes_runtime(int new_setting) | int | 设置魔幻引号并返回之前的设置 |
| get_magic_quotes_runtime(void) | int | 获取当前的魔幻引号设置 |
| get_magic_quotes_gpc |

# 附录 E：PHP 函数参考

## 表 E-4 时间函数
| 函数 | 返回 | 操作 |
|---|---|---|
| time(void) | int | 返回当前时间 |
| mktime(int hour, int min, int sec, int month, int day, int year) | int | 将日期和时间转换为时间戳 |
| date(string format [, int timestamp]) | string | 格式化本地时间 |
| gmdate(string format [, int timestamp]) | string | 格式化 GMT 时间 |
| strtotime(string format [, int timestamp]) | int | 将字符串格式的日期时间转换为时间戳 |
| microtime(void) | string | 返回包含当前秒数的字符串 |
| gettimeofday(void) | array | 返回当前时间的数组 |
| getrusage([int who]) | array | 返回来自用法统计的数组 |

## 表 E-5 目录函数
| 函数 | 返回 | 操作 |
| --- | --- | --- |
| opendir(string path) | int | 打开目录并返回句柄 |
| dir(string directory) | class | 返回具有三个方法（read, rewind, close）和两个属性（handle 和 path）的对象 |
| closedir([int dir_handle]) | void | 关闭由句柄标识的目录连接 |
| chdir(string directory) | int | 更改当前目录 |
| getcwd(void) | string | 获取当前目录 |
| reindir([int dir_handle]) | void | 将句柄重置到开头 |
| readdir([int dir_handle]) | string | 从句柄读取目录项 |

## 表 E-6 文件系统函数
| 函数 | 返回 | 操作 |
| --- | --- | --- |
| diskfreespace(string path) | double | 获取路径所在文件系统的可用磁盘空间，单位为字节 |
| chown(string filename, mixed user) | bool | 更改文件所有者。成功返回 true，否则返回 false |
| chgrp(string filename, mixed group) | bool | 更改文件组。成功返回 true，否则返回 false |
| chmod(string filename, int mode) | bool | 更改文件模式。成功返回 true，否则返回 false |
| touch(string filename [, int time]) | bool | 设置文件的修改时间 |
| clearstatcache(void) | void | 清除文件状态缓存 |
| fileperms(string filename) | int | 获取八进制格式的文件权限 |
| inode(string filename) | int | 获取文件 inode |
| filesize(string filename) | int | 获取文件大小 |
