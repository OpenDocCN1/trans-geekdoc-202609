

| Flag | Alternate Flag | Description |
|---|---|--|
| --add-drop-table | | 在 CREATE TABLE 语句之前添加一个 DROP TABLE IF EXISTS 语句。 |
| --allow-keywords | | 允许使用关键字作为列名。此选项通过在每个列名前面加上表名来实现。 |
| -c | --complete-insert | 使用完整的插入语句（带有列名）。 |
| --delayed | | 使用 INSERT DELAYED 命令插入行。 |
| -F | --flush-logs | 在开始转储之前，在 MySQL 服务器中刷新日志文件。 |
| -f | --force | 即使在导出表时遇到 SQL 错误也继续执行。 |
| -h | --host.. | 从指定主机上的 MySQL 服务器上导出数据。默认主机为 localhost。 |
| -l | --lock-tables | 在开始导出之前锁定所有表。 |
| -t | --no-create-info | 不写入表创建信息。 |
| -d | --no-data | 不为表写入任何行信息。 |
| --opt | | 等于 --quick --add-drop-table --add-locks-extended-insert --lock-tables。应该为你提供读取到 MySQL 服务器的最快转储速度。 |
| -p[...] | --password[...] | 连接到服务器时使用的密码。如果命令行上没有提供密码，将提示你输入。注意，如果使用短格式 '-p'，选项和密码之间不能有空格。 |
| -P | --port=port_num | 连接到主机时使用的 TCP/IP 端口号。 |

# 附录 C：MySQL Utilities 433

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -q | --quick | 不缓冲查询，直接转储到标准输出 (stdout)。 |
| -T path-to-some-directory | --tab-to-some-directory | 为每个表创建一个包含 SQL CREATE 命令的 table_name.sql 文件和一个包含表数据的 table_name.txt 文件。 |

以下是 Unix 安装上使用 -T 标志示例：

```
mysqldump -T tracking problems
```

这将在当前目录下创建两个文件（这就是它的含义）：'problems.sql' 和 'problems.txt''problems.sql' 将包含创建 'problems' 表的 SQL 语句。'problems.txt' 是 'tracking' 数据库中 'problems' 表当前数据的制表符分隔（默认格式）副本。

> 仅当 mysqldump 与 mysqld 守护进程运行在同一台机器上运行时有效。.txt 文件的格式是根据 --fields-xxx 和 --lines-xxx 选项生成的。

![](img/245156cc770929860a3ede93c01f9981_459_0.png)

表 C-9 列出了更多 mysqldump 命令行选项。

# 表 C-9 更多 MYSQLDUMP 命令行选项

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| --fields-terminated-by=... | | 这些选项的含义与 LOAD DATA INFILE 语句中的对应子句相同。 |
| --fields-enclosed-by=... | | | |
| --fields-optionally-enclosed-by=... | | | |
| --fields-escaped-by=... | | | |
| --lines-terminated-by=... | | | |

继续

# 434 第五部分：附录

# **表 C-9 更多 MYSQLDUMP 命令行选项（续）**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -u user_name, | --user=user_name | 连接到服务器时使用的 MySQL 用户名。 |
| -w | --where='where-condition' | 仅导出选定的记录；注意，引号是强制性的！<br><br>示例：<br>--where='user=*jim*' <br>--w='userid>1*' <br>--w='userid<1*' |

表 C-10 显示了 3.23 版本中新引入的 mysqldump 命令行选项。

# **表 C-10 3.23 版本新增的 MYSQLDUMP 命令行选项**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -A | --all-databases | 导出所有数据库。这与选了所有数据库的 --databases 相同。 |
| -B | --databases | 导出多个数据库。注意用法上的区别；在这种情况下，没有提供表。所有名称参数都被视为数据库名称。使用 db_name; 将在每个新数据库之前包含输出输出。 |
| -e | --extended-insert | 使用新的多行 INSERT 语法。 |

# 附录 C：MySQL Utilities 435

| Flag | Alternate Flag | Description |
|---|---|---|
| -n | --no-create | | |
| --create-info | | 不导出表结构。 |
| --data | --no-data | 不导出数据。 |
| --quick | | 逐行转储行，而不是在内存中缓冲整个表。 |
| --master-data | | 导出主服务器的二进制日志信息。 |
| --routines | | 导出存储过程和函数。 |
| --triggers | | 导出触发器。 |
| --extended-insert | | 使用扩展插入语法。 |
| --single-transaction | | 在单个事务中导出每个表。 |
| --hex-blob | | 将二进制列导出为十六进制字符串。 |
| --skip-insert | | 不包含 INSERT 语句。 |
| --skip-comments | | 不包含注释。 |
| --skip-create-db | | 不包含 CREATE DATABASE。 |
| --skip-create-info | | 不包含 CREATE TABLE。 |
| --skip-triggers | | 不包含触发器。 |
| --skip-events | | 不包含事件。 |
| --set-charset= | 使用特定的字符集。 |
| --set-client-character= | 使用特定的客户端字符集。 |
| --set-server-character= | 使用特定的服务器字符集。 |
| --default-character-set= | 设置默认字符集。 |
| --result-file= | | 将结果输出到文件。 |
| --error= | | 将错误输出到文件。 |
| --log= | | 将日志输出到文件。 |
| --add-drop-table | | 在 CREATE TABLE 语句之前添加一个 DROP TABLE IF EXISTS 语句。 |
| --add-createlock | | 为每个表添加 DELETE 语句。 |
| --add-locks | | 在每个 INSERT 之前添加 LOCK TABLE 语句。 |
| --add-locks-extended-insert | | 使用扩展插入 LOCK TABLE。 |
| --allow-keywords | 允许使用关键字作为列名。此选项通过在每个列名前面加上表名来实现。 |
| -c | --complete-insert | 使用完整的插入语句（带有列名）。 |
| --delayed | 使用 INSERT DELAYED 命令插入行。 |
| -F | --flush-logs | 在开始导出之前，在 MySQL 服务器中刷新日志文件。 |
| -f | --force | 即使在导出表时遇到 SQL 错误也继续执行。 |
| -h | --host.. | 从指定主机上的 MySQL 服务器上导出数据。默认主机为 localhost。 |
| -l | --lock-tables | 在开始导出之前锁定所有表。 |
| -t | --no-create-info | 不写入表创建信息。 |
| -d | --no-data | 不为表写入任何行信息。 |
| --opt | | 等于 --quick --add-drop-table --add-locks-extended-insert --lock-tables。应该为你提供读取到 MySQL 服务器的最快转储速度。 |
| -p[...] | --password[...] | 连接到服务器时使用的密码。如果命令行上没有提供密码，将提示你输入。注意，如果使用短格式 '-p'，选项和密码之间不能有空格。 |
| -P | --port=port_num | 连接到主机时使用的 TCP/IP 端口号。 |

mysqldump 是一个用于 MySQL 数据库逻辑备份的客户端程序。它创建一个包含 SQL 语句的文件，用于重建数据库结构和数据，可以执行该文件来恢复数据库或任何部分。

mysqldump 命令有许多选项。

--ignore 和 --replace 选项控制对与现有记录重复的输入记录的处理。如果你指定 --replace，则替换具有相同唯一键值的行。如果你指定 --ignore，则跳过与唯一键值重复的行。如果你没有指定任何一个，当发现重复键值时会发生错误，并忽略剩余文本。

mysqldump 的语法为：

```
mysqldump [options] db_name [table_name ...]
```

[options] 部分可以包含下面列出的任何选项。db_name 是要导出的数据库名称，[table_name ...] 是该数据库中特定表的可选名称。如果没有指定表，则导出数据库中的所有表。

一些最常用的选项：

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -q | --quick | 不缓冲查询，直接转储到标准输出 (stdout)。 |
| -T path-to-some-directory | --tab-path-to-some-directory | 为每个表创建一个包含 SQL CREATE 命令的 table_name.sql 文件和一个包含表数据的 table_name.txt 文件。 |

以下是 Unix 安装上使用 -T 标志示例：

```
mysqldump -T tracking problems
```

这将在当前目录下创建两个文件（这就是它的含义）：'problems.sql' 和 'problems.txt''problems.sql' 将包含创建 'problems' 表的 SQL 语句。'problems.txt' 是 'tracking' 数据库中 'problems' 表当前数据的制表符分隔（默认格式）副本。

> 仅当 mysqldump 与 mysqld 守护进程运行在同一台机器上运行时有效。.txt 文件的格式是根据 --fields-xxx 和 --lines-xxx 选项生成的。

![](img/245156cc770929860a3ede93c01f9981_459_0.png)

