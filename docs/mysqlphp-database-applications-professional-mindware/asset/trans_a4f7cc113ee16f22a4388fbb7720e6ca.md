
## 表 C-7 MYSQLADMIN 命令行选项

| Flag | Alternate Flag | Description |
|---|---|---|
| -? | --help | 显示帮助并退出。 |
| -# | --debug=... | 输出调试日志。通常这是 d:t:o,filename。 |
| -f | --force | 不在删除数据库时询问确认；在多个命令中，即使发生错误也继续。 |
| -h | --host=# | 连接到主机。 |
| -p[...] | --password[=...] | 连接到服务器时使用的密码。如果命令行中未提供密码，将提示您输入。注意，如果使用简写 -p，则选项和密码之间不能有空格。 |
| -P | --port=... | 连接使用的端口号。 |
| -i | --sleep=sec | 在两次执行之间休眠，重复执行命令。 |
| -r | --relative | 与 -i 一起使用时显示当前值与之前值之间的差异。目前仅适用于 extended-status。 |
| -s | --silent | 如果无法连接到服务器，则静默退出。 |
| -t | --timeout=... | 连接到 mysqld 服务器的超时时间。 |
| -w | --wait[=retries] | 如果连接中断则等待并重试。 |
| -W (仅 Windows) | --pipe | 使用命名管道连接到服务器。 |
| -E | --vertical | 垂直打印输出。与 -relative 类似，但垂直打印输出。 |

## mysqldump

这是用于转储数据库架构信息和数据的命令行实用程序。这就是您用于备份数据库或将其从一台机器移动到另一台机器时使用的工具。

mysqldump 的输出最常见的是 SQL 命令脚本，用于创建表然后向其中插入数据。mysqldump 还可以从表中创建纯数据文件（即制表符分隔文件）。

语法：

```
mysqldump [OPTIONS] database [tables]
```

或者，从 3.23 开始：

```
mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
mysqldump [OPTIONS] --all-databases [OPTIONS]
```

mysqldump 的典型用法如下：

```
mysqldump --opt mydatabase > backup-file.sql
```

你可以使用 mysql 命令行工具将其读回 MySQL：

```
mysql mydatabase < backup-file.sql
```

或者，从 3.23 开始：

```
mysql -e "source /path-to-backup/backup-file.sql" mydatabase
```

你也可以用它将数据从一台 MySQL 服务器复制到另一台：

```
mysqldump --opt mydatabase | mysql --host=remote-host mydatabase
```

表 C-8 列出了命令行选项：

## 表 C-8 MYSQLDUMP 命令行选项

| Flag | Alternate Flag | Description |
|---|---|---|
| -? | --help | 显示此帮助信息并退出。 |
| -a | --all | 包含所有 MySQL 特定的创建选项。 |
| --add-locks |  | 在每个表转储之前添加 LOCK TABLES，并在之后添加 UNLOCK TABLE（以便更快地插入 MySQL）。 |

继续

## 表 C-8 MYSQLDUMP 命令行选项（继续）

| Flag | Alternate Flag | Description |
|---|---|---|
| --add-drop-table |  | 在每个 CREATE TABLE 语句之前添加 DROP TABLE IF EXISTS 语句。 |
| --allow-keywords |  | 允许创建名称为关键字的列。此选项通过在每个列名前加上表名前缀来工作。 |
| -c | --complete-insert | 使用完整的插入语句（带列名）。 |
| --delayed |  | 使用 INSERT DELAYED 命令插入行。 |
| -F | --flush-logs | 在开始转储前刷新 MySQL 服务器中的日志文件。 |
| -f | --force | 即使在表转储期间出现 SQL 错误也继续。 |
| -h | --host=.. | 从指定主机上的 MySQL 服务器转储数据。默认主机为 localhost。 |
| -l | --lock-tables | 在开始转储前锁定所有表。 |
| -t | --no-create-info | 不写入表创建信息。 |
| -d | --no-data | 不为表写入任何行信息。 |
| --opt |  | 与 --quick --add-drop-table --add-locks --extended-insert --lock-tables 相同。应为您提供读取到 MySQL 服务器的最快可能的转储。 |
| -p[...] | --password[=...] | 连接到服务器时使用的密码。如果命令行中未提供密码，将提示您输入。注意，如果使用简写 `-p`，则选项和密码之间不能有空格。 |
| -P | --port=port_num | 连接到主机时使用的 TCP/IP 端口号。 |

| Flag | Alternate Flag | Description |
|---|---|---|
| -q | --quick | 不缓冲查询，直接转储到 stdout。 |
| -T path-to-some-directory, | --tab=path-to-some-directory | 对于每个表，创建一个包含 SQL CREATE 命令的 table_name.sql 文件，以及包含表数据的 table_name.txt 文件。 |

以下是 -T 标志在 Unix 安装上的一个示例：

```
mysqldump -T . tracking problems
```

这将在当前目录中创建两个文件（'.' 就是指此含义）：'problems.sql' 和 'problems.txt.' 'problems.sql' 将包含创建 'problems' 表的 SQL 语句。'problems.txt' 是 'tracking' 数据库中 'problems' 表中数据的制表符分隔（默认格式）副本。

![](img/de0823012275cf4ceebdb822a56e6b71_459_0.png)

这仅在 mysqldump 在与 mysqld 守护进程相同的机器上运行时才有效。.txt 文件的格式是根据 --fields-xxx 和 --lines-xxx 选项制定的。

表 C-9 列出了更多 mysqldump 命令行选项。

## 表 C-9 更多 MYSQLDUMP 命令行选项

| Flag | Alternate Flag | Description |
|---|---|---|
| --fields-terminated-by=... |  | 这些选项与 LOAD DATA INFILE 语句的相应子句具有相同的含义。 |
| --fields-enclosed-by=... |  |  |
| --fields-optionally-enclosed-by=... |  |  |
| --fields-escaped-by=... |  |  |
| --lines-terminated-by=... |  |  |

继续

## 表 C-9 更多 MYSQLDUMP 命令行选项（继续）

| Flag | Alternate Flag | Description |
|------|----------------|-------------|
| `-u user_name` | `--user=user_name` | 连接到服务器时使用的 MySQL 用户名。 |
| `-w` | `--where='where-condition'` | 仅转储选定的记录；注意 QUOTES 是强制性的！示例：`--where=user='jimf'` `"-wuserid>1"` `"-wuserid<1"` |

表 C-10 显示了版本 3.23 中新增的 mysqldump 命令行选项。

## 表 C-10 版本 3.23 中新增的 MYSQLDUMP 命令行选项

| Flag | Alternate Flag | Description |
|------|----------------|-------------|
| `-A` | `--all-databases` | 转储所有数据库。这与选择所有数据库的 `--databases` 相同。 |
| `-B` | `--databases` | 转储多个数据库。注意使用上的区别；在此情况下不提供表。所有名称参数都被视为数据库名称。USE db_name; 将在每个新数据库之前包含在输出中。 |
| `-e` | `--extended-insert` | 使用新的多行 INSERT 语法。 |

| Flag | Alternate Flag | Description |
| -n | --no-create-db | 'CREATE DATABASE IF NOT EXISTS db_name;' 不会放入输出中。否则，如果给出 --databases 或 --all-databases 选项，则会添加上述行。 |
| --tables |  | 覆盖选项 --databases (-B)。 |
| -O |  | net_buffer_length=#，其中 # < 24M 在创建多行插入语句时（如使用 --extended-insert 或 --opt 选项），mysqldump 将创建长达 net_buffer_length 的行。如果您增加此变量，还应确保 MySQL 服务器中的 max_allowed_packet 变量大于 net_buffer_length。 |

## mysqlimport

mysqlimport 工具为 'LOAD DATA INFILE' SQL 语句提供命令行接口。mysqlimport 的大多数选项直接对应于 'LOAD DATA INFILE' 的相同选项。

语法：

```
mysqlimport [options] database textfile1 [textfile2...]
```

对于命令行上命名的每个文本文件，mysqlimport 会从文件名中去掉任何扩展名，并使用结果来确定将文件内容导入到哪个表中。例如，名为 patient.txt、patient.text 和 patient 的文件都将被导入到名为 patient 的表上。

你通常使用 mysqlimport 将数据从其他来源——另一个 DBMS、电子表格或类似的东西——带入 MySQL 数据库。你也可以将其与 mysqldump 工具一起使用。以下是我前面给出的示例：

```
mysqldump -T . tracking problems
```
