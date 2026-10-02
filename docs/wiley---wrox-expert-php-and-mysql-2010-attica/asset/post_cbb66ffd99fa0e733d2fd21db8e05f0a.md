
Notice here that you specify the log, as well as the long_query_time, which is the number of seconds a query takes to execute, as well as logging any queries where indexes aren’t used. The entries in the log contain useful information about these slow queries:

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

This code shows how long a query took, how long the table was locked, and the number of rows sent from the query, as well as the number of rows examined to produce the result.

## Processlist

Some tools you will want in your arsenal are SHOW PROCESSLIST and the even more verbose SHOW FULL PROCESSLIST, which gives you a listing of the queries running within MySQL. The listing includes the following:

- Query id
- Username running the query
- Host the query is initiated from
- Database/schema the query is running against
- Command
- Time the command has been running
- Query being executed and full text of the query if FULL is specified

The following shows the output:

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

As you can see, the output shows a lot of useful information to spot a troublesome query that’s taking a lot of time to execute, which in some cases would affect the PHP application’s overall performance. Whenever an application is taking a while to display or load data, you want to display the processlist to see if there’s something obvious that you can fix. Also, if a process is hung, you can kill it:

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

which in this case killed a sleeping process. But in some cases it could be a query that has been running for minutes resulting in a blank page for one of your users!

## Other Commands

You have a number of other commands at your disposal but detailing them is beyond the scope of this book. Here a quick list:

- **SHOW STATUS/SHOW GLOBAL STATUS:** Shows the complete status of a given session or database as a whole, and provides a wealth of information pertaining to the running status of your MySQL instance.
- **SHOW TABLE STATUS:** Shows the status of tables on your MySQL instance.
- **SHOW INNODB STATUS:** Shows the status of the InnoDB storage engine. For any tables where you are using InnoDB, this provides information pertaining to how those tables function.
- **SHOW MASTER STATUS:** Shows you the status of your binary log, if turned on.
- **SHOW SLAVE STATUS:** Shows you the status of the slave — information such as which relay log the SQL slave thread is reading and which binary position the IO slave thread is reading on the master, and the lag that exists between the slave and master, as well as other information pertaining to the running state of replication.

Do remember that you can find all SHOW commands information in the INFORMATION_SCHEMA database. For more complete information, please consult with the MySQL user’s manual at http://dev.mysql.com/.

## Using a Debugger with MySQL

Another tool that really shows how MySQL functions as well as tracks down the cause of bugs (if you want to become a MySQL hacker yourself!) is GDB — the GNU Debugger. To really make use of this, you need to install GDB and the source distribution of MySQL. For more information, refer to your operating system information and the MySQL user’s manual. You can also find information by joining mailing lists and IRC channels #mysql, #mysql-dev on Freenode.

To use GDB to track down a crash, you would find the process id of your running MySQL instance as root or the mysql user:

```
yourhost:~ root# ps auxw|grep mysqld|grep -v mysqld_safe|grep -v grep
_mysql 26456 0.0 0.3 109232 14624 s003 S 10:18AM 0:00.08
/usr/local/mysql/libexec/mysqld --basedir=/usr/local/maria
--datadir=/usr/local/mysql/var --user=mysql
--log-error=/usr/local/mysql/var/yourhost.local.err
--pid-file=/usr/local/mysql/var/yourhost.local.pid
```

In this case, the process ID is 26456. You can attach to this process with GDB:

```
yourhost:~ root# gdb /usr/local/maria/libexec/mysqld 26456
<extra text removed>
Attaching to program: `/usr/local/maria/libexec/mysqld', process 26456.
Reading symbols for shared libraries +++....
(gdb)
```

At the (gdb) prompt, you type continue to tell MySQL to continue running:

```
(gdb) continue
Continuing.
```

If, for instance, there’s a query that’s causing MySQL to crash, you run that query in another window. Then you will see something like this appear in GDB:

```
Program received signal SIGUSR1, User defined signal 1.
[Switching to process 26456 thread 0x2507]
0x932532ce in semaphore_wait_signal_trap ()
To see what caused the problem and have something you could submit to a mailing list, you can run backtrace:
(gdb) backtrace
#0  0x932532ce in semaphore_wait_signal_trap ()
#1  0x9325ada5 in pthread_mutex_lock ()
#2  0x0032e74f in thr_end_alarm ()
#3  0x0025b437 in mysql_real_connect ()
#4  0x00d53ef0 in federatedx_io_mysql::actual_query ()
#5  0x00d54846 in federatedx_io_mysql::query ()
#6  0x00d4da3d in test_connection ()
#7  0x00d4fcf9 in ha_federatedx::create ()
#8  0x001d1610 in ha_create_table ()
#9  0x0019512c in rea_create_table ()
#10 0x001ddc39 in mysql_create_table_no_lock ()
#11 0x001de1be in mysql_create_table ()
#12 0x000e6cde in mysql_execute_command ()
#13 0x000e7626 in mysql_parse ()
#14 0x000e8135 in dispatch_command ()
#15 0x000e9079 in do_command ()
#16 0x000d7834 in handle_one_connection ()
#17 0x93284155 in _pthread_start ()
#18 0x93284012 in thread_start ()
(gdb)
```

The code shows that there is something wrong with the FederatedX storage engine. This is the type of trace you could provide the developer of the FederatedX storage engine (one of the authors of this book, Patrick Galbraith!). Or if you feel adventurous and greatly hailed in the open source community, you could even fix this bug!

## SUMMARY

Performance is a key characteristic of a successful application. By using the techniques to optimize your queries and inspecting state in your PHP code, your application will operate faster and more efficiently and lead to higher throughput.
