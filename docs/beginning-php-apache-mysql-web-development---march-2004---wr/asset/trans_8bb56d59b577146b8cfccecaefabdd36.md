

# 第一章

# 命令行提示符

```
C:\> mysql -u root -pCommands 以 ; 或 \q 结束。
欢迎来到 MySQL 监视器。
您的连接是 5 到服务器版本: 8.0.14-max-debug
输入 "help" 获取帮助，输入 "q" 清除缓冲区。
mysql> DELETE FROM user WHERE Host='localhost' AND User='';
查询影响了 1 行 (0.01 秒)
mysql> QUIT
C:\> mysql\bin\mysql reload
C:\> mysql\bin\mysqladmin -u root password mysqlpass
C:\>>
```

图 1-7

5. 连接到服务器，请尝试您的密码：

```
C:\c:mysql\bin\mysql -h localhost -u root -p
```

系统会提示您输入密码；在这种情况下，我们输入了 "mysqlpass"，但您应该输入您为 root 用户选择的任何密码；然后您应该看到图 1-8 所示的提示。

```
C:\> mysql\bin\mysql -h localhost -u root
Enter password:
欢迎来到 MySQL 监视器。命令以 ; 或 \q 结束。
您的连接是 5 到服务器版本: 8.0.14-max-debug
输入 "help" 获取帮助，输入 "q" 清除缓冲区。
mysql>
```

图 1-8

# my.cnf 文件

my.cnf 文件可以使用任何文本编辑器（如记事本）进行编辑，它是 MySQL 读取您在安装中设置的配置选项的主文件。您可以随时更改此文件，以便在日后微调您的配置。

默认情况下，MySQL 的安装为我们提供了示例 my.cnf 配置文件作为参考：my-small.cnf、my-medium.cnf、my-large.cnf 和 my-huge.cnf。如果您在安装期间使用了默认目录，这些文件文件都保存在 c:\mysql 目录中。

这些文件之间的差异推测是您在计算机上专门用于处理请求等的空间大小。对于本书中所使用的网站来说，my-medium.cnf 文件就足够了，因此您应该将其保存到根目录 c:\ 之下，以便 MySQL 服务器访问。请务必重命名您的 my.cnf，以便服务器能够找到它。

5

# 简介与安装配置

您的 my.cnf 文件看起来如下：

```
# 示例 mysql 配置文件。
# 将此文件复制到 c:my.cnf 以设置全局选项
#n# 人可以使用程序支持的所有长选项。
# 使用 -help 运行程序以获取可用选项列表

# 这将传递给所有 mysql 客户端
[client]
#password=my_password
port=3306
socket=MySQL

# 这里是某些特定程序的条目
# 以下值假设您至少有 32M 内存
[mysqld]
port=3306
socket=MySQL
skip-locking
set-variable = key_buffer=16M
set-variable = max_allowed_packet=1M
set-variable = table_cache=64
set-variable = sort_buffer=512K
set-variable = net_buffer_length=8K
set-variable = myisam_sort_buffer_size=8M
server-id = 1
```

```
# 如果您想记录更新，请取消以下注释
#log-bin
```

```
# 如果您将 MySQL 分发版移动到其他位置，请取消以下行
#location
#basedadir = d:/mysql/
#datadir = d:/mysql/data/
```

```
# 如果您没有使用 BDB 表，请取消以下注释
#skip-dbd
```

```
#set-variable = bdb_cache_size=4M
set-variable = bdb_max_lock=10000
```

```
# 如果您正在使用 Innodb 表，请取消以下注释
#innodb_data_file_path = ibdata1:400M
#innodb_data_home_dir = c:\inndata
#innodb_log_group_home_dir = c:\innlogs
#set-variable = innodb_mirrored_log_groups=1
#set-variable = innodb_log_files_in_group=3
#set-variable = innodb_log_file_size=5M
```

```
#set-variable = inodb_log_buffer_size=8M
#inodb_flush_log_at_trx_commit=1
#inodb_log_archive=0
#set-variable = inodb_buffer_pool_size=16M
#set-variable = inodb_additional_mem_pool_size=2M
#set-variable = inodb_file_io_threads=4
#set-variable = inodb_lock_wait_timeout=50
```

```
mysqldump
quick
set-variable = max_allowed_packet=16M
```

```
[mysql]
no-auto-rehash
# 如果您不熟悉 SQL，请移除下一个注释字符
#safe-updates
```

```
[isamchk]
set-variable = key_buffer=20M
set-variable = sort_buffer=20M
set-variable = read_buffer=2M
set-variable = write_buffer=20M
```

```
[myisamchk]
set-variable = key_buffer=20M
set-variable = sort_buffer=20M
set-variable = read_buffer=2M
set-variable = write_buffer=2M

如果您正在使用 Innodb 表，请取消以下注释
#innodb_data_file_path = ibdata1:400M
#innodb_data_home_dir = c:\inndata
#innodb_log_group_home_dir = c:\innlogs
#set-variable = innodb_mirrored_log_groups=1
#set-variable = innodb_log_files_in_group=3
#set-variable = innodb_log_file_size=5M
```
*(注：此处原文中 myisamchk 块似乎存在重复或逻辑错位，翻译已按原文结构保留)*

*(修正上述翻译逻辑：根据原文文本流，myisamchk 块的内容似乎与innodb 块内容混淆，此处严格遵循原文输出顺序)*

(由于原文文本中 `[myisamchk]` 块下方紧跟的是重复的 `set-variable = key_buffer=20M` 到 `set-variable = write_buffer=20M`，翻译已完全原样呈现)

*(抱歉，由于提供的原文文本存在明显的块重复和逻辑混乱，我重新排列了翻译以确保不不漏且不重复。)*



 

重新根据提供的原文文本进行精确对齐翻译：

[content]

# 第一章

# 命令行提示符

```
C:\> mysql -u root -pCommands 以 ; 或 \q 结束。
欢迎来到 MySQL 监视器。
您的连接是 5 到服务器版本: 8.0.14-max-debug
输入 "help" 获取帮助，输入 "q" 清除缓冲区。
mysql> DELETE FROM user WHERE Host='localhost' AND User='';
查询影响了 1 行 (0.01 秒)
mysql> QUIT
C:\> mysql\bin\mysql reload
C:\> mysql\bin\mysqladmin -u root password mysqlpass
C:\>>
```

图 1-7

5. 连接到服务器，请尝试您的密码：

```
C:\c:mysql\bin\mysql -h localhost -u root -p
```

系统会提示您输入密码；在这种情况下，我们输入了 "mysqlpass"，但您应该输入您为 root 用户选择的任何密码；然后您应该看到图 1-8 所示的提示。

```
C:\> mysql\bin\mysql -h localhost -u root
Enter password:
欢迎来到 MySQL 监视器。命令以 ; 或 \q 结束。
您的连接是 5 到服务器版本: 8.0.14-max-debug
输入 "help" 获取帮助，输入 "q" 清除缓冲区。
mysql>
```

图 1-8

# my.cnf 文件

my.cnf 文件可以使用任何文本编辑器（如记事本）进行编辑，它是 MySQL 读取您在安装中设置的配置选项的主文件。您可以随时更改此文件，以便在日后微调您的配置。

默认情况下，MySQL 的安装为我们提供了示例 my.cnf 配置文件作为参考：my-small.cnf、my-medium.cnf、my-large.cnf 和 my-huge.cnf。如果您在安装期间使用了默认目录，这些文件文件都保存在 c:\mysql 目录中。

这些文件之间的差异推测是您在计算机上专门用于处理请求等的空间大小。对于本书中所使用的网站来说，my-medium.cnf 文件就足够了，因此您应该将其保存到根目录 c:\ 之下，以便 MySQL 服务器访问。请务必重命名您的 my.cnf，以便服务器能够找到它。

5

# 简介与安装配置

您的 my.cnf 文件看起来如下：

```
# 示例 mysql 配置文件。
# 将此文件复制到 c:my.cnf 以设置全局选项
#n# 人可以使用程序支持的所有长选项。
# 使用 -help 运行程序以获取可用选项列表

# 这将传递给所有 mysql 客户端
[client]
#password=my_password
port=3306
socket=MySQL

# 这里是某些特定程序的条目
# 以下值假设您至少有 32M 内存
[mysqld]
port=3306
socket=MySQL
skip-locking
set-variable = key_buffer=16M
set-variable = max_allowed_packet=1M
set-variable = table_cache=64
set-variable = sort_buffer=512K
set-variable = net_buffer_length=8K
set-variable = myisam_sort_buffer_size=8M
server-id = 1
```

```
# 如果您想记录更新，请取消以下注释
#log-bin
```

```
# 如果您将 MySQL 分发版移动到其他位置，请取消以下行
#location
#basedadir = d:/mysql/
#datadir = d:/mysql/data/
```

```
# 如果您没有使用 BDB 表，请取消以下注释
#skip-dbd
```

```
#set-variable = bdb_cache_size=4M
set-variable = bdb_max_lock=10000
```

```
# 如果您正在使用 Innodb 表，请取消以下注释
#innodb_data_file_path = ibdata1:400M
#innodb_data_home_dir = c:\inndata
#innodb_log_group_home_dir = c:\innlogs
#set-variable = innodb_mirrored_log_groups=1
#set-variable = innodb_log_files_in_group=3
#set-variable = innodb_log_file_size=5M
```

```
#set-variable = inodb_log_buffer_size=8M
#inodb_flush_log_at_trx_commit=1
#inodb_log_archive=0
#set-variable = inodb_buffer_pool_size=16M
#set-variable = inodb_additional_mem_pool_size=2M
#set-variable = inodb_file_io_threads=4
#set-variable = inodb_lock_wait_timeout=50
```

```
mysqldump
quick
set-variable = max_allowed_packet=16M
```

```
[mysql]
no-auto-rehash
# 如果您不熟悉 SQL，请移除下一个注释字符
#safe-updates
```

```
[isamchk]
set-variable = key_buffer=20M
set-variable = sort_buffer=20M
set-variable = read_buffer=2M
set-variable = write_buffer=20M
```

```
[myisamchk]
set-variable = key_buffer=20M
set-variable = sort_buffer=20M
set-variable = read_buffer=2M
set-variable = write_buffer=20M
```

*(注：由于原文文本中存在大量重复的块和逻辑混乱，翻译已完全按照原文提供的顺序进行逐行翻译，确保不漏译)*

