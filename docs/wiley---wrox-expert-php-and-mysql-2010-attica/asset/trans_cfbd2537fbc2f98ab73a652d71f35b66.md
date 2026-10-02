
| id |
|----|
| 101 |

3. 在从服务器上，检查复制的状态：

```
beta>  SHOW SLAVE STATUS\G
*************************** 1. row ***************************
           Slave_IO_State: Waiting for master to send event
              Master_Log_File: binary-log.000003
          Read_Master_Log_Pos: 306
               Relay_Log_File: relay-bin.000013
                Relay_Log_Pos: 252
    Relay_Master_Log_File: binary-log.000003
         Slave_IO_Running: Yes
        Slave_SQL_Running: No
              Last_Errno: 1062
              Last_Error: Error 'Duplicate entry '101' for key 'PRIMARY'' on query. Default database: ''. Query: 'INSERT INTO chapter6.replication_test VALUES (101)'
          Skip_Counter: 0
    Exec_Master_Log_Pos: 106
```

4. 你现在可以看到复制中出现了一个错误，但原因已知，并且数据现在可能存在不一致。你之所以知道原因是因为这是一个模拟测试，但在生产环境中，这并不明显，需要对主服务器和从服务器上的底层数据进行适当的验证：

```
beta>  SET GLOBAL SQL_SLAVE_SKIP_COUNTER=1;
beta>  SLAVE START SQL_THREAD;
beta>  SHOW SLAVE STATUS\G
```

你现在应该可以看到一个正在运行的 MySQL 从服务器，如之前演示的那样。

> *如果你遵循这两种规则，你就可以消除用户引入的错误以及导致复制失败的最可能原因：*

- 始终以只读模式运行你的 MySQL 从服务器。
- 切勿使用具有 SUPER 权限的用户运行 DDL 或 DML 语句。

## 选择性使用复制

也可能运行不会被复制的命令。例如，你可以按命令选择性地禁用复制：

```
alpha>  SET SESSION SQL_LOG_BIN=FALSE;
alpha>  INSERT INTO chapter6.replication_test VALUES (201);
alpha>  SET SESSION SQL_LOG_BIN=TRUE;
```

```
alpha> INSERT INTO chapter6.replication_test VALUES (202);
alpha> SELECT * FROM chapter6.replication_test WHERE id > 200;
```

| id |
|----|
| 201 |
| 202 |

如你所见，并非所有插入的数据都被应用到从服务器：

```
beta> SELECT * FROM chapter6.replication_test WHERE id > 200;
```

| id |
|----|
| 202 |

> 你绝不应轻易使用这些命令。MySQL 无法提供任何确保数据库一致性的手段。通过选择性地禁用 MySQL，你引入了不一致，而 MySQL 也不提供任何识别或纠正它的工具。查看 Maatkit 工具包以获取执行此操作的选项。

你还可以配置主服务器或从服务器上的 MySQL 以选择性地记录或处理二进制日志事件。以下各种选项提供了选择某些操作的各种方法。我们不会详细讨论这些选项。有关详细说明，请参阅 MySQL 参考手册 http://dev.mysql.com/doc/refman/5.1/en/replication-options.html。

- replicate-do-db
- replicate-do-table
- replicate-ignore-db
- replicate-ignore-table
- replicate-wild-do-table
- replicate-wild-ignore-table

## MySQL 复制的问题

MySQL 复制存在两个主要问题，主要是由于该过程的异步性质。这些是：

- **Lag:** 异步复制的直接结果。重要的是你在拓扑中监控复制延迟，因为通常 MySQL 从服务器的用途是用于在线处理，例如读取扩展或用于 MySQL 备份。
- **Consistency:** 没有保证从服务器数据与主服务器一致。在之前的示例中，展示了两个可能产生不一致数据集的实例。

现在有多个补丁可用于提高一致性，并且作为副作用提高延迟。Google MySQL Patches http://code.google.com/p/google-mysql-tools/ 中提供的第一个补丁提供了半同步复制的级别。包括 Percona 性能构建在内的 MySQL 的其他移植版本现在包含类似的补丁。

不一致的可能性通常没有被考虑，尤其是在 MySQL 从服务器是主要备份过程时。MySQL 不提供通过表校验和等方式确保一致性的能力。流行的 Maatkit 工具包可在 http://maatkit.org 获取，具有一个非常好的用于执行表校验和的工具。

> > 尽管本书中未讨论，有一个 MySQL 产品提供同步复制来克服这两个问题。MySQL Cluster 可以像 MySQL 复制一样运行；然而，它实际上是一个不同的产品。尽管它可能通过 SQL 接口看起来像 MySQL 运行，但它具有不同的功能以及相对的优势和局限性。请参阅官方 MySQL 产品页面获取更多信息 http://www.mysql.com/products/database/cluster/。

## MySQL 复制的好处

重要的是认识到 MySQL 的优势并最大化这些优势，同时最小化弱点。尽管一些问题首先被列出，MySQL 的好处很容易超过局限性。MySQL 复制已成功用于当今许多主要网站中。结合其他产品，如 memcached，以及诸如分片之类的原则，组合可以提供强大且可扩展的解决方案。

> > MySQL Sandbox (http://mysqlsandbox.net/)，最初由 MySQL 社区成员 Giuseppe Maxia 创建，是学习 MySQL 复制的宝贵工具。有了这个工具，你可以在完全隔离的环境中用于测试的几秒钟内创建和部署各种不同类型的 MySQL 复制拓扑。

## 事件

事件是 MySQL 5.1 的新功能。事件使在 MySQL 数据库内调度一次性或循环工作成为可能，类似于在 Linux 系统上使用 cron 调度的过程。为了演示事件，创建一个你将用作验证的测试表（清单 6-14）：

### 清单 6-14: event-table.sql

```sql
DROP TABLE IF EXISTS event_test;
CREATE TABLE event_test(
    id      INT UNSIGNED NOT NULL AUTO_INCREMENT,
created  TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
action    VARCHAR(10) NOT NULL,
val       VARCHAR(10) NOT NULL,
PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET latin1;
```

## 创建事件

要创建你的第一个事件，请按照以下步骤操作：

1. 创建一个每分钟运行一次的事件（清单 6-15）：

### 清单 6-15: every-min-event.sql

```
CREATE EVENT e_minute
ON SCHEDULE EVERY 1 MINUTE
COMMENT 'Perform event every minute'
DO
  INSERT INTO event_test (action,val)
  VALUES ('Minute',DATE_FORMAT(NOW(), '%i%s'));
```

2. 确认目前还没有发生任何事情：

```
SELECT * FROM event_test;
Empty set (0.00 sec)
```

```
SELECT NOW();
```

| NOW() |
|-------|
| 2009-10-17 14:52:23 |

3. 创建一个只运行一次的事件（清单 6-16）：

### 清单 6-16: once-off-event.sql

```
CREATE EVENT e_nextminute
ON SCHEDULE AT CURRENT_TIMESTAMP + INTERVAL 1 MINUTE
COMMENT 'Perform event just once'
DO
  INSERT INTO event_test (action,val)
  VALUES ('1 Minute',DATE_FORMAT(NOW(), '%i%s'));
```

4. 你可以使用 SHOW EVENTS 命令查看事件的调度信息：

```
mysql> SHOW EVENTS\G
*************************** 1. row ***************************
Db: chapter6
Name: e_minute
Definer: rbradfor@localhost
Time zone: SYSTEM
Type: RECURRING
Execute at: NULL
Interval value: 1
Interval field: MINUTE
Starts: 2009-10-17 14:51:42
Ends: NULL
Status: ENABLED
Originator: 0
character_set_client: latin1
collation_connection: latin1_swedish_ci
Database Collation: latin1_swedish_ci
******************************** 2. row ********************************
Db: chapter6
Name: e_nextminute
Definer: rbradfor@localhost
Time zone: SYSTEM
Type: ONE TIME
Execute at: 2009-10-17 15:00:07
Interval value: NULL
Interval field: NULL
Starts: NULL
Ends: NULL
Status: ENABLED
Originator: 0
character_set_client: latin1
collation_connection: latin1_swedish_ci
Database Collation: latin1_swedish_ci
2 rows in set (0.00 sec)
```

5. 现在几分钟过去了，查看已插入的数据：

```
SELECT * FROM event_test;
Empty set (0.00 sec)
```

表中没有信息。SHOW EVENTS 的输出未指示任何问题。审查 MySQL 错误日志也没有提供任何错误。问题是事件调度程序默认未启用。当作者首次在 5.1.6 版本中测试事件时，这不是必需的。MySQL 参考手册确认事件的默认行为在不同版本中发生了变化。

> 切勿假设给定 MySQL 配置变量的默认值。默认值可能在版本之间发生变化，并且有许多此类情况。重要的是仔细阅读文档，并确保你阅读的版本与特定 MySQL 产品的小版本发布以及各种 MySQL 连接器一致。

