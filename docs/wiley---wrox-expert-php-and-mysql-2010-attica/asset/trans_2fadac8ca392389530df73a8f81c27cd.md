
无法在不指定数据库的情况下检索主数据信息。如果指定了无效的数据库，您会收到一条可以忽略的错误消息。主服务器上还需要一步操作，即为任何从 MySQL 从库拉取主库更改创建合适的用户。您在检索二进制日志位置之后执行此操作，因为您希望此命令被复制：

```
CREATE USER repl@'192.168.%' IDENTIFIED BY 'repl2009';
GRANT REPLICATION SLAVE ON *.* TO repl@'192.168.%';
```

> 您使用 IP 范围进行主机身份验证。请参阅第 14 章中关于“Hardening Your MySQL Server”的部分，其中详细讨论了这些指定权限的使用和最佳实践。

## 从服务器配置

要配置代号为 Beta 的从服务器，您需要进行以下 my.cnf 修改并重启 MySQL 服务器，如同在主服务器上所做的那样：

```
[mysqld]
server-id=2
read_only=TRUE
```

- 第一个参数是 server-id。这需要在 MySQL 拓扑中是唯一的数字，并标识给定 SQL 语句的来源位置。
- 第二个参数是 read_only。这表示服务器不能接收 DDL 或 DML 语句。这在 MySQL 拓扑中是一个重要考虑因素，因为 MySQL 缺乏支持冲突检测的工具。创建 Master/Master MySQL 拓扑是可能的——但强烈不建议——其中两个服务器可以同时接收写入。要实现这一点，您必须使用特定的复制配置、特定的数据库架构设计，并使用可恢复的 SQL 语法来设计应用程序。

以下 SQL 将您的运行服务器配置为从服务器。注意，CHANGE MASTER 命令包含主服务器上指定的用户名和密码，而日志文件名和位置是从主服务器上执行的前一个命令中检索的。

```
SHOW SLAVE STATUS;
CHANGE MASTER TO
MASTER_HOST='192.168.100.1',
MASTER_USER='repl',
MASTER_PASSWORD='repl2009';

CHANGE MASTER TO
MASTER_LOG_FILE='binary-log.000001',
MASTER_LOG_POS=106;
```

## 从服务器操作

您现在拥有一个配置正确的从服务器。最后一步是启动从服务器并确认操作：

```
SLAVE START;

SHOW SLAVE STATUS\G
*************************** 1. row ***************************
      Slave_IO_State: Waiting for master to send event
         Master_Host: 192.168.100.1
         Master_User: repl
         Master_Port: 3306
       Connect_Retry: 60
      Master_Log_File: binary-log.000001
    Read_Master_Log_Pos: 327
       Relay_Log_File: macmarvin-relay-bin.000002
        Relay_Log_Pos: 473
    Relay_Master_Log_File: binary-log.000001
     Slave_IO_Running: Yes
     Slave_SQL_Running: Yes
       Replicate_Do_DB:
    Replicate_Ignore_DB:
     Replicate_Do_Table:
 Replicate_Ignore_Table:
  Replicate_Wild_Do_Table:
 Replicate_Wild_Ignore_Table:
            Last_Errno: 0
            Last_Error:
            Skip_Counter: 0
     Exec_Master_Log_Pos: 327
         Relay_Log_Space: 632
         Until_Condition: None
          Until_Log_File:
           Until_Log_Pos: 0
        Master_SSL_Allowed: No
        Master_SSL_CA_File:
        Master_SSL_CA_Path:
        Master_SSL_Cert:
        Master_SSL_Cipher:
        Master_SSL_Key:
   Seconds_Behind_Master: 0
Master_SSL_Verify_Server_Cert: No
            Last_IO_Errno: 0
            Last_IO_Error:
            Last_SQL_Errno: 0
            Last_SQL_Error:
```

如果您可以确认 Slave_IO_Running 和 Slave_SQL_Running 均为 Yes，则您拥有一个正在运行的 Master/Slave MySQL 拓扑。

## 测试 MySQL 复制

以下示例为简单起见使用代号 alpha 和 beta，以确保确认 MySQL 命令是在哪个服务器上执行的。测试此操作的最佳方法是打开两个独立的会话。第一步是更好地识别您的 mysql 客户端会话。

- 以下代码在 alpha 上测试：
```
mysql> PROMPT alpha>;
alpha>
```
- 以下代码在 beta 上测试：
```
mysql> PROMPT beta>;
beta>
```

通过以下步骤在测试中创建一个新的模式和表：

- 1. 首先确认从服务器上不存在任何内容：
```
beta> SHOW SCHEMAS;
```
| 数据库 |
|---|
| information_schema |
| mysql |
| test |
- 2. 在主服务器上创建模式和表并确认：
```
alpha> CREATE SCHEMA chapter6;
alpha> USE chapter6;
alpha> CREATE TABLE replication_test(id INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY) ENGINE=INNODB DEFAULT CHARSET latin1;
```
```
beta> SHOW SCHEMAS;
```
| 数据库 |
|---|
| information_schema |
| chapter6 |
| mysql |
| test |
- 3. 通过检索表的内容来验证表是否存在于客户端：
```
beta> SELECT * FROM chapter6.replication_test;
Empty set (0.00 sec)
```
- 4. 在主服务器上添加一些数据并确认其已被复制：
```
alpha> INSERT INTO chapter6.replication_test(id) VALUES (1),(2),(3);
alpha> SELECT * FROM chapter6.replication_test;
```
| id |
|---|
| 1 |
| 2 |
| 3 |
- 5. 确认相同的数据存在于从服务器上：
```
beta> SELECT * FROM chapter6.replication_test;
```
| id |
|---|
| 1 |
| 2 |
| 3 |

如果您尝试向从服务器而不是主服务器添加信息，则会收到错误，因为您的初始 MySQL 配置：

```
beta> INSERT INTO chapter6.replication_test(id) VALUES (4);
ERROR 1290 (HY000): The MySQL server is running with the --read-only option
so it cannot execute this statement
```

> 具有 SUPER 权限的用户会覆盖 read_only 安全设置。切勿使用具有 SUPER 权限的应用用户。有关用户安全的更多信息，请参阅第 14 章中“Hardening your MySQL Server”部分。

## MySQL 复制是如何工作的？

本节逐步分解 MySQL 复制的各个组成部分，使用一些更内部的命令和操作系统文件来查看 SQL 如何执行和复制。为此，您停止从服务器进程以确保在执行前可以看到 SQL：

```
beta> SLAVE STOP;
```

## 主服务器分析

要执行主服务器分析，请按照以下步骤操作：

- 1. 为测试向主服务器添加一些新数据：
```
alpha> SHOW MASTER STATUS;
```
| 文件 | 位置 | Binlog_Do_DB | Binlog_Ignore_DB |
|---|---|---|---|
| binary-log.000001 | 828 |  |  |

```
alpha> INSERT INTO chapter6.replication_test(id) VALUES(10);
```
```
alpha> SHOW MASTER STATUS;
```
| 文件 | 位置 | Binlog_Do_DB | Binlog_Ignore_DB |
|---|---|---|---|
| binary-log.000001 | 1046 |  |  |
- 2. SHOW MASTER STATUS 命令中的详细信息实际上反映了此文件中的文件名和字符指针位置。您未使用 log-bin 命令指定这些二进制日志的位置，因此您将在 MySQL 数据目录中找到它们。这可能因您安装 MySQL 的方式而异：
```
alpha$ ls -l /var/log/mysql/binary-log.000001
-rw-rw---- 1 rbradfor staff 1046 Oct  4 00:08 binary-log.000001
```
- 3. 使用前一个 SHOW MASTER STATUS 命令中显示的文件名。位置实际上是所列二进制文件的字节计数。
- 4. 为了展示二进制日志的工作原理，您可以轮转这些文件。默认情况下 MySQL 根据给定大小轮转文件；但是，您也可以手动轮转它们：
```
alpha> FLUSH LOGS;
alpha> SHOW MASTER STATUS;
```
| 文件 | 位置 | Binlog_Do_DB | Binlog_Ignore_DB |
|---|---|---|---|
| binary-log.000002 | 106 |  |  |

```
alpha$ ls -l /var/log/mysql/binary-log*
-rw-rw---- 1 rbradfor staff 1090 Oct  4 00:11 binary-log.000001
-rw-rw---- 1 rbradfor staff 106 Oct  4 00:11 binary-log.000002
-rw-rw---- 1 rbradfor staff 40 Oct  4 00:11 binary-log.index
```

如您所见，主服务器状态显示了新的文件名，并且在文件系统上得到了确认。

## 二进制日志文件分析

您实际上可以使用 mysqlbinlog 命令查询这些文件。例如，您可以查看在运行测试 INSERT 语句之前二进制日志位置的日志：

```
alpha$ mysqlbinlog --start-position=828 /var/log/mysql/binary-log.000001
```

此命令会产生大量冗长的输出。出于简化和空间限制的原因，已删除了一些行。

```
# at 828
#091004 0:08:21 server id 1 end_log_pos 900 Query thread_id=8 exec_time=0
error_code=0
.
# at 900
#091004 0:08:21 server id 1 end_log_pos 1019 Query thread_id=8 exec_time=0
error_code=0
use chapter6/* */;
```
