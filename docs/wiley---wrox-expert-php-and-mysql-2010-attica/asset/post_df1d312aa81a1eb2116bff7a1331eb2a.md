
The preceding code shows that both queries give the same results; however, the optimizer shows that the second query uses fewer operations and executes faster. With this list, you can now delete these records using the join in a DELETE statement:

```
delete from child using child left join parent on (parent.id = child.parent_id)
where parent.id is NULL;
Query OK, 4 rows affected (0.00 sec)
```

And the four rows were deleted!

## Optimizing INSERT

Generally, no optimization is necessary for an INSERT because the result of your SQL is one inserted row. You can, however, optimize multiple INSERT statements on the same table using multiple VALUES clauses, otherwise known as a bulk insert. This can actually save you time when you insert multiple records in a single operation. For example:

```
INSERT INTO t1(c1,c2,c3,d) VALUES ('a','b','c',CURDATE());
INSERT INTO t1(c1,c2,c3,d) VALUES ('1','2','3',CURDATE());
INSERT INTO t1(c1,c2,c3,d) VALUES ('x','y','z',CURDATE());
```

This is actually three individual INSERT statements, which incur three network round trips to the database. If you rewrite as shown in the previous code, you actually reduce this network communications from three to one network round trip. The other benefit of this optimization is that MySQL only needs to produce one execution plan for the INSERT statement. It can then utilize that same execution plan for multiple values. One caveat when you work with bulk inserts: if the single insert fails, all the records specified in the multiple VALUES clauses will also fail to be inserted.

```
INSERT INTO t1(c1,c2,c3,d) VALUES
('a','b','c',CURDATE()),
('1','2','3',CURDATE()),
('x','y','z',CURDATE());
```

## Optimizing REPLACE

The MySQL REPLACE command is actually implemented internally as a DELETE and an INSERT. The REPLACE command, however, can cause fragmentation at the disk data level due to the unexpected DELETE operation. If possible, you should consider using alternative means of inserting or updating your data, as shown next with the INSERT ... ON DUPLICATE KEY UPDATE statement.

## INSERT ... ON DUPLICATE KEY UPDATE

As stated, REPLACE is inefficient because it is internally implemented using a DELETE and INSERT. You have another way to have a replace-like functionality when you use the INSERT ... ON DUPLICATE KEY UPDATE statement. This statement results in a record being updated if the record exists for the primary key value and any of the record's columns' values are different than the existing specified record. If the record does not yet exist, it is inserted. If the record exists but none of the values have changed, nothing happens. This behavior is preferable to using REPLACE which deletes the record and then re-inserts it.

Using the sakila database, which — to say the least — contains interesting geek-humor for data, and, in particular, the film table — which contains records for films — an existing record demonstrates the use of the INSERT ... ON DUPLICATE KEY UPDATE statement:

```
mysql> select * from film where film_id = 500\G
*************************** 1. row ***************************
        film_id: 500
        title: KISS GLORY
        description: A Lackluster Reflection of a Girl And a Husband who must
        Find a Robot in The Canadian Rockies
        release_year: 2006
        language_id: 1
        original_language_id: NULL
        rental_duration: 5
        rental_rate: 4.99
        length: 163
        replacement_cost: 11.99
        rating: PG-13
        special_features: Trailers,Commentaries,Behind the Scenes
        last_update: 2006-02-15 05:03:42
```

In the following query, you see what appears to be a regular insert, but with the additional specification to update the record if the unique key (the primary key film_id) is a value of an existing record, you will see that this record is updated:

```
INSERT INTO film (film_id, description, title)
VALUES (500,
'Epic story featuring Krishna and Arjuna on the battlefield of Kurukshetra',
'Mahabarata')
ON DUPLICATE KEY UPDATE
film_id = 500,
title = 'Mahabarata',
description = 'Epic story featuring Krishna and Arjuna on the Battlefield
of Kurukshetra';
Query OK, 2 rows affected, 1 warning (0.01 sec)
```

Note that two rows have been affected and a warning issued. This is because a SET value for language_id was not specified and language_id does not have a default value specified in the table definition, as the SHOW WARNINGS output shows in the following code.

```
mysql> show warnings;
```

| Level | Code | Message |
|---|---|---|
| Warning | 1364 | Field 'language_id' doesn't have a default value |

Next, a query shows that the record was indeed updated:

```
mysql> select * from film where film_id = 500\G
*************************** 1. row ***************************
        film_id: 500
        title: Mahabarata
        description: Epic story featuring Krishna and Arjuna on the Battlefield
        of Kurukshetra
        release_year: 2006
        language_id: 1
        original_language_id: NULL
        rental_duration: 5
        rental_rate: 4.99
        length: 163
        replacement_cost: 11.99
        rating: PG-13
        special_features: Trailers,Commentaries,Behind the Scenes
        last_update: 2009-11-23 16:40:56
```

## DEBUGGING MYSQL

You can debug MySQL in a number of ways. In this section, you see that when you use the various logs, view process lists, and use the Gnu Debugger, gdb, you can receive all the information you could ever need to debug a problem. You can get useful information in order to report a crash to the developer community.

### Error Log

Whenever you have an issue, you first want to view the error log. This is specified by the log-error directive in the my.cnf, or if not specified, you'll most likely find the error log in your data directory where the data files for MySQL are stored, and the error log is often named using the hostname of your server:

```
ls /usr/local/mysql/var/*err
/usr/local/mysql/var/patrick-galbraiths-macbook-pro.local.err
```

In this log file, you can see normal operations such as startup and shutdown as well as possible problems. The startup and shutdown messages appear as:

```
091119 1:54:28 [Note] /usr/local/mysql/libexec/mysqld: Normal shutdown
091119 01:54:34 mysqld_safe mysqld restarted
091119 1:54:34 [Warning] Setting lower_case_table_names=2 because file system for /usr/local/maria/var/ is case insensitive
091119 1:54:34 [Note] Event Scheduler: Loaded 0 events
091119 1:54:34 [Note] /usr/local/mysql/libexec/mysqld: ready for connections.
Version: '5.1.35-maria-beta1'  socket: '/tmp/mysql.sock'
port: 3306  Source distribution
```

You'll also see various errors from time to time. For example, the following output shows an error loading the Memcached Functions for MySQL (UDFs). The particular problem is due to the UDF plugin shared library not being installed correctly, resulting in this error message:

```
091118 10:56:53 [ERROR] Can't open shared library 'libmemcached_functions_mysql.so' (errno: 0 dlopen(/usr/local/maria/lib/mysql/plugin/libmemcached_functions_mysql.so, 2): Symbol not found: _memcached_pool_behavior_get
```

Or in the case of a crash, you can see this unwanted but useful message:

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

As much as you don’t want to see a message like this, it is very useful because it contains a crash trace that you can send to MySQL developers.

### Slow Query Log

If you turn on the slow query log, any slow queries — queries that take an excessive amount of time — are logged to this file, which is extremely useful to identify badly written queries — potential queries to optimize. To specify the slow query log, you can add to your my.cnf:

```
log-slow-queries = /var/log/mysql/mysql-slow.log
long_query_time = 2
log-queries-not-using-indexes
```
