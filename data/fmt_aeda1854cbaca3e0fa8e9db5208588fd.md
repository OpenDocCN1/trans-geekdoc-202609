
091119 1:54:34 [Note] `/usr/local/mysql/libexec/mysqld`: ready for connections.

Version: '5.1.35-maria-beta1'  socket: '/tmp/mysql.sock'

port: 3306  Source distribution

你有时也会看到各种错误。例如，以下输出显示加载 MySQL 的 Memcached 函数（UDF）时出错。特定问题是由于 UDF 插件共享库未正确安装，导致此错误消息：

```
091118 10:56:53 [ERROR] Can't open shared library 'libmemcached_functions_mysql.so' (errno: 0 dlopen(/usr/local/maria/lib/mysql/plugin/libmemcached_functions_mysql.so, 2): Symbol not found: _memcached_pool_behavior_get
```

或者在崩溃的情况下，你可以看到这条不受欢迎但有用的消息：

```
091023  8:54:34 - mysqld got signal 11 ;

This could be because you hit a bug. It is also possible that this binary or one of the libraries it was linked against is corrupt, improperly built, or misconfigured. This error can also be caused by malfunctioning hardware. We will try our best to scrape up some info that will hopefully help diagnose the problem, but since we have already crashed, something is definitely wrong and this may fail.

key_buffer_size=8384512

read_buffer_size=131072

max_used_connections=1

max_threads=153

threads_connected=0

It is possible that mysqld could use up to

key_buffer_size + (read_buffer_size + sort_buffer_size)*max_threads = 342071 K

bytes of memory

Hope that's ok; if not, decrease some variables in the equation.

thd: 0x0

Attempting backtrace. You can use the following information to find out

where mysqld died. If you see no messages after this, something went

terribly wrong...stack_bottom = 0x0 thread_stack 0x48000

0  mysqld  0x0032db8d my_print_stacktrace + 40

1  mysqld  0x000ce0c1 handle_segfault + 10252

    libSystem.B.dylib  0x932bf2bb __sigtramp + 43

3  ???  0xffffffff 0x0 + 4294967295

4  ha_federatedx.so  0x00d4cd08 _ZN13ha_federatedx5closeEv + 72

5  mysqld  0x0012d464 _Z8closefrmP8st_tableb + 244

6  mysqld  0x00127181 _Z11lock_tablesP3THDP10TABLE_LISTjPb + 1809

7  mysqld  0x003232ee my_hash_delete + 711

8  mysqld  0x00129c9c _Z19close_cached_tablesP3THDP10TABLE_LISTbbb + 588

9  mysqld  0x0012a10c _Z16table_cache_freev + 76

10 mysqld  0x000cbee4 print_signal_warning + 324

11 mysqld  0x000d3609 _Z34create_thread_to_handle_connectionP3THD + 2121

12 mysqld  0x000d3632 kill_server_thread + 18

13 libSystem.B.dylib  0x93284155 _pthread_start + 321

14 libSystem.B.dylib  0x93284012 thread_start + 34

The manual page at http://dev.mysql.com/doc/mysql/en/crashing.html contains

information that should help you find out what is causing the crash.
```

尽管你不想看到这样的消息，但它非常有用，因为它包含崩溃跟踪，你可以将其发送给 MySQL 开发者。

### Slow Query Log

如果你打开慢查询日志，任何慢查询——耗时过长的查询——都会记录到此文件中，这对于识别写得不好的查询——潜在需要优化的查询非常有用。要指定慢查询日志，你可以在 `my.cnf` 中添加：

```
log-slow-queries = /var/log/mysql/mysql-slow.log

long_query_time = 2

log-queries-not-using-indexes
```

这里请注意，你指定了日志，以及 `long_query_time`，即查询执行所花费的秒数，同时还会记录未使用索引的查询。日志中的条目包含有关这些慢查询的有用信息：

```
# Query_time: 3  Lock_time: 0  Rows_sent: 140  Rows_examined: 280

SELECT acl_actions .*, acl_roles_actions.access_override

        FROM acl_actions

        LEFT JOIN acl_roles_users ON acl_roles_users.user_id = ''

AND  acl_roles_users.deleted = 0

        LEFT JOIN acl_roles_actions ON acl_roles_actions.role_id = acl_roles_users.role_id AND acl_roles_actions.action_id = acl_actions.id AND acl_roles_actions.deleted=0

        WHERE acl_actions.deleted=0  ORDER BY category,name;

# Time: 091125 11:23:07# User@Host: root[root] @ localhost []

# Query_time: 2  Lock_time: 0  Rows_sent: 0  Rows_examined: 67

select * from leads where account_name like '%foo%';
```

这段代码显示了查询花费了多长时间，表被锁定的时间，以及查询发送的行数，还有产生结果时检查的行数。

## 进程列表

你工具箱中想要的一些工具是 `SHOW PROCESSLIST` 以及更详细的 `SHOW FULL PROCESSLIST`，它会列出 MySQL 中正在运行的查询。列表包括以下内容：

- Query id
- Username running the query
- Host the query is initiated from
- Database/schema the query is running against
- Command
- Time the command has been running
- Query being executed and full text of the query if FULL is specified

以下显示输出：

```
mysql> show full processlist\G

******************************* 1. row *******************************

      Id: 1

    User: system user

    Host:

      db: NULL

Command: Connect

    Time: 650731

   State: Waiting for master to send event

    Info: NULL

******************************* 2. row *******************************

      Id: 139282

```
```

User: dbuser

    Host: 192.168.0.99:62623

    db: NULL

Command: Binlog Dump

    Time: 595445

    State: Has sent all binlog to slave; waiting for binlog to be updated

    Info: NULL

******************************* 3. row *******************************

    Id: 184194

    User: system user

    Host:

    db: NULL

Command: Connect

    Time: 2

    State: Has read all relay log; waiting for the slave I/O thread to update it

    Info: NULL

< output truncated to save trees >

******************************* 122. row *******************************

    Id: 14608817

    User: exporter

    Host: 192.168.0.50:22012

    db: export?

Command: Query

    Time: 130

    State: NULL

    Info: LOAD DATA LOCAL INFILE 'data/data_info99.txt' REPLACE INTO TABLE carexport.extraint_results_sets  FIELDS TERMINATED BY '|' (        rcust_id,

    user_id,        dept_id,        all_constraints,        passed,

failed,    addedby ) SET dateadded = NOW()  ******************************* 123. row *******************************

      Id: 14160644

    User: uioda

    Host: 192.168.1.5:42241

    db: ioda?

Command: Query

    Time: 0

    State: Sending data

    Info: SELECT count(distinct books.book_id) from books.publish_queue pbq

WHERE books.book_id = '8953' AND (book.status = 'review' OR book.status =

'sold' ) AND book.type = 'technical' AND (book_id IS NULL OR book_id !=

'30497')
```

正如你所见，输出显示了大量有用的信息，可以发现执行时间很长的麻烦查询，在某些情况下会影响 PHP 应用的整体性能。每当应用程序显示或加载数据花费较长时间时，你都希望显示进程列表，看看是否有明显可以修复的问题。此外，如果某个进程挂起，你可以将其杀掉：

```
******************************* 7. row *******************************

    Id: 1245

    User: cacti

    Host: localhost

    db: cacti

Command: Sleep

    Time: 93

```
```

State:

    Info: NULL

7 rows in set (0.00 sec)

mysql> kill 1245;

Query OK, 0 rows affected (0.00 sec)
```

这在这种情况下杀掉了一个休眠进程。但在某些情况下，它可能是一个运行了几分钟的查询，导致你的某个用户出现空白页面！

## 其他命令

你还有许多其他命令可用，但详细介绍它们超出了本书的范围。这里是一个快速列表：

- `SHOW STATUS`/`SHOW GLOBAL STATUS`: 显示给定会话或整个数据库的完整状态，并提供有关 MySQL 实例运行状态的丰富信息。
- `SHOW TABLE STATUS`: 显示 MySQL 实例上表的状态。
- `SHOW INNODB STATUS`: 显示 InnoDB 存储引擎的状态。对于使用 InnoDB 的任何表，这提供了有关这些表如何工作的信息。
- `SHOW MASTER STATUS`: 显示你的二进制日志状态，如果已开启。
- `SHOW SLAVE STATUS`: 显示从服务器的状态——信息例如 SQL 从服务器线程正在读取哪个中继日志，以及 IO 从服务器线程在主服务器上读取的哪个二进制位置，以及从服务器和主服务器之间存在的延迟，以及有关复制运行状态的其他信息。

请记住，你可以在 `INFORMATION_SCHEMA` 数据库中找到所有 `SHOW` 命令的信息。有关更完整的信息，请参阅 MySQL 用户手册 at http://dev.mysql.com/。

## 使用调试器调试 MySQL

另一个真正展示 MySQL 如何工作以及追踪错误原因的工具，如果你想自己成为 MySQL 黑客！是 GDB — GNU 调试器。要真正使用它，你需要安装 GDB 和 MySQL 的源代码分发版。有关更多信息，请参阅你的操作系统信息和 MySQL 用户手册。你也可以通过加入邮件列表和 IRC 频道 `#mysql`、`#mysql-dev` on Freenode 找到信息。

要使用 GDB 追踪崩溃，你需要以 root 或 mysql 用户身份找到正在运行的 MySQL 实例的进程 ID：

```
yourhost:~ root# ps auxw|grep mysqld|grep -v mysqld_safe|grep -v grep

_mysql 26456 0.0 0.3 109232 14624 s003 S 10:18AM 0:00.08

/usr/local/mysql/libexec/mysqld --basedir=/usr/local/maria

--datadir=/usr/local/mysql/var --user=mysql

--log-error=/usr/local/mysql/var/yourhost.local.err

--pid-file=/usr/local/mysql/var/yourhost.local.pid
```

在这种情况下，进程 ID 为 `26456`。你可以用 GDB 附加到此进程：

```
yourhost:~ root# gdb /usr/local/maria/libexec/mysqld 26456

<extra text removed>

Attaching to program: `/usr/local/maria/libexec/mysqld', process 26456.

Reading symbols for shared libraries +++....

(gdb)
```

在 `(gdb)` 提示符下，你输入 `continue` 来告诉 MySQL 继续运行：

```
(gdb) continue

Continuing.
```

例如，如果有一个查询导致 MySQL 崩溃，你在另一个窗口运行该查询。然后你会在 GDB 中看到类似这样的内容出现：

```
Program received signal SIGUSR1, User defined signal 1.

[Switching to process 26456 thread 0x2507]

0x932532ce in semaphore_wait_signal_trap ()

To see what caused the problem and have something you could submit to a mailing list, you can run backtrace:

(gdb) backtrace
```
