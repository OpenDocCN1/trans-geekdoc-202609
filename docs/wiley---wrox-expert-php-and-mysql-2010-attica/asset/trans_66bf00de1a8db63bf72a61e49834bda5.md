

| 视图 | 计数 |
|---|---|
| 表 | 431 |
| 视图 | 0 |
| 过程 | 10 |
| 函数 | 0 |
| 事件 | 0 |
| 触发器 | 0 |

## MySQL 状态表

也可通过以下各节介绍的表从 INFORMATION_SCHEMA 获取数据库系统状态信息：

### PROCESSLIST (5.1)

此表提供与 SHOW PROCESSLIST 命令相同的信息，只是使用 INFORMATION_SCHEMA 时，您可以运行查询并查找特定用户进程。此表的列为：

- **ID:** 给定进程的连接 ID。
- **USER:** 给定进程以其运行的数据库用户名。
- **HOST:** 进程运行所在的主机。
- **DB:** 进程运行的模式名称。
- **COMMAND:** 正在运行的命令（QUERY、CONNECT 等）。
- **TIME:** 进程已运行的时间（秒）。
- **STATE:** 命令的进程状态（即执行中、创建表、写入网络等）。存在大量可能的不同的线程状态。
- **INFO:** 列出该进程正在运行的实际查询。

代码如下：

```
select * from information_schema.processlist where USER = 'patg'\G
*************************** 1. row ***************************
      ID: 6016
    USER: patg
    HOST: localhost
      DB: test
 COMMAND: Query
    TIME: 0
   STATE: creating table
    INFO: create table bench_1224 (i int NOT NULL,d double,f float,
          s char(10),v varchar(100),primary key (i))
1 row in set (0.19 sec)
PROFILING
```

MySQL 性能分析器最初由 Proven Scaling (http://www.provenscaling.com/) 的 Jeremy Cole 编写。这是一个无价的诊断工具，可让您分析查询的内部服务器执行的确切步骤。这可以帮助您找到查询中的任何低效之处，并进而调整这些查询以获得更好的性能。此表的列在表 13-2 中列出：

### 表 13-2：性能分析表列

| 列 | 描述 |
|---|---|
| QUERY_ID | 正在分析的查询的 ID |
| SEQ | 所列执行的序列或步骤编号 |
| STATE | 命令的进程状态 |
| DURATION | 所列执行花费的时间，单位为秒 |
| CPU_USER | 花在命令执行上的时间（用户 CPU 时间） |
| CPU_SYSTEM | CPU 代表进程为内核执行系统调用所花费的时间 |
| CONTEXT_VOLUNTARY | 目前未实现 |
| CONTEXT_INVOLUNTARY | 目前未实现 |
| BLOCK_OPS_IN | 目前未实现 |
| BLOCK_OPS_OUT | 目前未实现 |
| MESSAGES_SENT | 目前未实现 |
| MESSAGES_RECEIVED | 目前未实现 |
| PAGE_FAULTS_MAJOR | 目前未实现 |
| PAGE_FAULTS_MINOR | 目前未实现 |
| SWAPS | 目前未实现 |
| SOURCE_FUNCTION | 特定执行由其发出的源代码函数 |
| SOURCE_FILE | 特定执行起源的源文件 |
| SOURCE_LINE | 特定执行起源的源文件中的行 |

使用性能分析器并能够使用此表，您必须首先发出：

```
set profiling = 1;
```

从此时起，您为会话发出的任何查询都将被性能分析器捕获，因此可以通过 PROFILING 表查看。您可以针对此表发出查询，例如给定查询的执行时间：

```
select sum(duration), sum(cpu_user), sum(cpu_system)
from  information_schema.profiling where query_id = 3;
+----------------+----------------+----------------+
| sum(duration) | sum(cpu_user) | sum(cpu_system) |
+----------------+----------------+----------------+
|     0.795895 |      0.000362 |      0.003601 |
+----------------+----------------+----------------+
```

您还可以使用性能分析器了解 MySQL 如何处理查询并深入了解 MySQL 的工作原理：

```
select distinct(source_function), source_file
from  information_schema.profiling where query_id = 3;
+----------------------+------------------+
| source_function      | source_file      |
+----------------------+------------------+
| NULL                 | NULL             |
| open_tables          | sql_base.cc      |
| mysql_lock_tables    | lock.cc          |
| mysql_select         | sql_select.cc    |
| optimize             | sql_select.cc    |
| exec                 | sql_select.cc    |
| mysql_execute_command| sql_parse.cc     |
| mysql_parse          | sql_parse.cc     |
| log_slow_statement   | sql_parse.cc     |
| dispatch_command     | sql_parse.cc     |
+----------------------+------------------+
```

使用完性能分析器后，您当然可以运行：

```
set profiling = 0;
```

## 会话状态/全局状态 (5.1)

这些表分别包含给定会话或系统的 MySQL 状态变量的值。其列为：

- **VARIABLE_NAME**: 状态变量的名称。
- **VARIABLE_VALUE**: 状态变量的值。

例如，您可以查出在 MySQL 实例上已执行的 SQL 命令：

```
select * from information_schema.global_status
where  variable_name like 'COM%'
and    variable_value > 0;
+----------------------+----------------+
| VARIABLE_NAME        | VARIABLE_VALUE |
+----------------------+----------------+
| COM_ALTER_TABLE      | 191            |
+----------------------+----------------+
```

| 变量名 | 变量值 |
|---|---|
| COM_CREATE_INDEX | 8 |
| COM_CREATE_TABLE | 30043 |
| COM_DELETE | 10147 |
| COM_DROP_INDEX | 8 |
| COM_DROP_TABLE | 60083 |
| COM_INSERT | 554780 |
| COM_INSERT_SELECT | 2 |
| COM_SELECT | 1740554 |
| COM_SET_OPTION | 6022 |
| COM_SHOW_DATABASES | 4 |
| COM_SHOW_FIELDS | 107 |
| COM_SHOW_PROCESSLIST | 1 |
| COM_SHOW_STATUS | 10 |
| COM_SHOW_TABLES | 11 |
| COM_UPDATE | 450773 |

或者您可以查出给定会话的索引状态变量：

```sql
select * from information_schema.session_status
where variable_name like 'KEY%';
```

| 变量名 | 变量值 |
|---|---|
| KEY_BLOCKS_NOT_FLUSHED | 0 |
| KEY_BLOCKS_UNUSED | 7245 |
| KEY_BLOCKS_USED | 7245 |
| KEY_READ_REQUESTS | 119528769 |
| KEY_READS | 1197779 |
| KEY_WRITE_REQUESTS | 7783921 |
| KEY_WRITES | 3869884 |

## 会话变量/全局变量 (5.1)

这些表分别包含给定会话或系统的 MySQL 系统变量的值。列为：

- **VARIABLE_NAME**: 变量的名称。
- **VARIABLE_VALUE**: 变量的值。

例如，您可以执行以下查询来了解支持哪些功能和/或存储引擎：

```sql
select * from information_schema.global_variables
where variable_name like 'have_%';
```

| 变量名 | 变量值 |
|---|---|
| HAVE_CRYPT | YES |
| HAVE_OPENSSL | NO |
| HAVE_SYMLINK | YES |
| HAVE_CSV | YES |
| HAVE_GEOMETRY | YES |

| 变量名 | 变量值 |
|---|---|
| HAVE_PARTITIONING | NO |
| HAVE_QUERY_CACHE | YES |
| HAVE_DYNAMIC_LOADING | YES |
| HAVE_SSL | NO |
| HAVE_NDBCLUSTER | NO |
| HAVE_COMMUNITY_FEATURES | YES |
| HAVE_INNODB | NO |
| HAVE_RTREE_KEYS | YES |
| HAVE_COMPRESS | YES |

您也可以通过以下查询了解各种系统目录位置：

```
select * from information_schema.global_variables
where variable_name like '%DIR%';
```

| 变量名 | 变量值 |
|---|---|
| CHARACTER_SETS_DIR | /usr/local/maria/share/mysql/charsets/ |
| BASEDIR | /usr/local/maria/ |
| SLAVE_LOAD_TMPDIR | /var/tmp/ |
| TMPDIR | /var/tmp/ |
| MARIA_SYNC_LOG_DIR | NEWFILE |
| DATADIR | /usr/local/maria/var/ |
| PLUGIN_DIR | /usr/local/maria/lib/mysql/plugin |

## MySQL 元数据表

INFORMATION_SCHEMA 提供了几个表，提供有关字符集和排序规则的元数据信息：

### 字符集

此表列出 MySQL 实例上可用的字符集。列为：

- CHARACTER_SET_NAME: 字符集的名称。创建表时您将指定此值。
- DEFAULT_COLLATE_NAME: 字符集的默认排序规则名称。您会看到排序规则名称可以以 _cs 或 _ci 结尾。这对应于区分大小写或不区分大小写。
- DESCRIPTION: 字符集的规范描述。
- MAXLEN: 字符集的字节长度。

代码如下：

```
select * from information_schema.character_sets;
```

| 字符集名称 | 默认排序规则名称 | 描述 | 最大长度 |
|---|---|
| dec8 | dec8_swedish_ci | DEC 西欧 | 1 |

