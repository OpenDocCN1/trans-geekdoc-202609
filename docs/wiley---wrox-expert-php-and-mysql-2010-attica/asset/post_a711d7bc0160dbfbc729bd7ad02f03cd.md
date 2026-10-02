
| Views | cnt |
|---|---|
| Tables | 431 |
| Views | 0 |
| Procedures | 10 |
| Functions | 0 |
| Events | 0 |
| Triggers | 0 |

## MYSQL STATUS TABLES

It is also possible to obtain database system status information from the INFORMATION_SCHEMA through the tables presented in the following sections:

### PROCESSLIST (5.1)

This table provides the same information as the command SHOW PROCESSLIST, except with INFORMATION_SCHEMA, you can run queries and find out specific user processes. The columns of this table are:

- **ID:** The connection ID for a given process.
- **USER:** The name of the database user that a given process is running as.
- **HOST:** The host from where the process is being run.
- **DB:** The name of the schema for which the process is running.
- **COMMAND:** The command being run (QUERY, CONNECT, and so on).
- **TIME:** The amount of time the process has been running in seconds.
- **STATE:** The process state of the command (that is, executing, creating table, writing to net, and so on). There are a large number of possible different thread states.
- **INFO:** Lists the actual query being run for this process.

The code is as follows:

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

The MySQL profiler was originally written by Jeremy Cole from Proven Scaling (http://www.provenscaling.com/). This is an invaluable diagnostic utility that allows you to analyze the exact steps of the internal server execution of your queries. This can allow you to find any inefficiencies with your queries and in turn tune those queries to have better performance. The columns for this table are listed in Table 13-2:

### TABLE 13-2: Profiling Table Columns

| COLUMN | DESCRIPTION |
|---|---|
| QUERY_ID | The ID for the given query being profiled |
| SEQ | The sequence or step number of the listed execution |
| STATE | The process state of the command |
| DURATION | The time the listed execution took, in seconds |
| CPU_USER | The amount of time spent on the execution of the command (user CPU time) |
| CPU_SYSTEM | The amount of time the CPU spends on system calls for the kernel on behalf of the process |
| CONTEXT_VOLUNTARY | Not currently implemented |
| CONTEXT_INVOLUNTARY | Not currently implemented |
| BLOCK_OPS_IN | Not currently implemented |
| BLOCK_OPS_OUT | Not currently implemented |
| MESSAGES_SENT | Not currently implemented |
| MESSAGES_RECEIVED | Not currently implemented |
| PAGE_FAULTS_MAJOR | Not currently implemented |
| PAGE_FAULTS_MINOR | Not currently implemented |
| SWAPS | Not currently implemented |
| SOURCE_FUNCTION | The source code function the particular execution was issued by. |
| SOURCE_FILE | The source file from where the particular execution originated |
| SOURCE_LINE | The line in the source file from where the particular execution originated |

To use the profiler and be able to utilize this table, you must first issue:

```
set profiling = 1;
```

From this point on, any queries you issue for your session will be captured by the profiler and hence viewable via the PROFILING table. You can issue queries against this table, such as how long it takes for a given query to execute:

```
select sum(duration), sum(cpu_user), sum(cpu_system)
from  information_schema.profiling where query_id = 3;
+----------------+----------------+----------------+
| sum(duration) | sum(cpu_user) | sum(cpu_system) |
+----------------+----------------+----------------+
|     0.795895 |      0.000362 |      0.003601 |
+----------------+----------------+----------------+
```

You can also use the profiler to find out how MySQL processes a query and gain insight into how MySQL works:

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

When you are done with using the profiler, you can of course run:

```
set profiling = 0;
```

## SESSION_STATUS/GLOBAL_STATUS (5.1)

These tables contain values of MySQL status variables for the given session or system, respectively. Their columns are:

- **VARIABLE_NAME**: Name of the status variable.
- **VARIABLE_VALUE**: Value of the status variable.

For instance, you can find out the SQL commands that have been executed on your MySQL instance:

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

| VARIABLE_NAME | VARIABLE_VALUE |
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

Or you could find out index status variables for your given session:

```sql
select * from information_schema.session_status
where variable_name like 'KEY%';
```

| VARIABLE_NAME | VARIABLE_VALUE |
|---|---|
| KEY_BLOCKS_NOT_FLUSHED | 0 |
| KEY_BLOCKS_UNUSED | 7245 |
| KEY_BLOCKS_USED | 7245 |
| KEY_READ_REQUESTS | 119528769 |
| KEY_READS | 1197779 |
| KEY_WRITE_REQUESTS | 7783921 |
| KEY_WRITES | 3869884 |

## SESSION_VARIABLES/GLOBAL_VARIABLES (5.1)

These tables contain the values of MySQL system variables for the given session or system, respectively. The columns are:

- **VARIABLE_NAME**: The name of the variable.
- **VARIABLE_VALUE**: The value of the variable.

For instance, one query you could perform to find out what features and/or storage engines are supported would be the following:

```sql
select * from information_schema.global_variables
where variable_name like 'have_%';
```

| VARIABLE_NAME | VARIABLE_VALUE |
|---|---|
| HAVE_CRYPT | YES |
| HAVE_OPENSSL | NO |
| HAVE_SYMLINK | YES |
| HAVE_CSV | YES |
| HAVE_GEOMETRY | YES |

| VARIABLE_NAME | VARIABLE_VALUE |
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

You could also find out the location of various system directory locations by the following query:

```
select * from information_schema.global_variables
where variable_name like '%DIR%';
```

| VARIABLE_NAME | VARIABLE_VALUE |
|---|---|
| CHARACTER_SETS_DIR | /usr/local/maria/share/mysql/charsets/ |
| BASEDIR | /usr/local/maria/ |
| SLAVE_LOAD_TMPDIR | /var/tmp/ |
| TMPDIR | /var/tmp/ |
| MARIA_SYNC_LOG_DIR | NEWFILE |
| DATADIR | /usr/local/maria/var/ |
| PLUGIN_DIR | /usr/local/maria/lib/mysql/plugin |

## MYSQL META DATA TABLES

The INFORMATION_SCHEMA provides several tables that provide metadata information particularly having to do with character sets and collation:

### CHARACTER_SETS

This table lists the character sets that are available on your instance of MySQL. The columns are:

- CHARACTER_SET_NAME: The name of the character set. This is the value you would specify when creating a table.
- DEFAULT_COLLATE_NAME: The default name of the collation of the character set. You will see that collation names can end in _cs or _ci. This corresponds to case-sensitive or case-insensitive.
- DESCRIPTION: A canonical description of the character set.
- MAXLEN: The length of the character set in bytes.

The code is as follows:

```
select * from information_schema.character_sets;
```

| CHARACTER_SET_NAME | DEFAULT_COLLATE_NAME | DESCRIPTION | MAXLEN |
|---|---|
| dec8 | dec8_swedish_ci | DEC West European | 1 |
