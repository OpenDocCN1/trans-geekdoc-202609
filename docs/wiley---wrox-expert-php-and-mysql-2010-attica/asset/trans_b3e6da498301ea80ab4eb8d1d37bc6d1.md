
## 启用事件调度器

凭借这些新知识，你确实可以确认调度器默认情况下被定义为未运行：

- 启用此项：
- 让调度器运行几分钟以查看你最初期望的输出：
- 如果你查看事件计划，你会发现现在只定义了一个：

```
SHOW GLOBAL VARIABLES LIKE 'event_scheduler';
+-----------------+-------+
| Variable_name   | Value |
+-----------------+-------+
| event_scheduler | OFF   |
+-----------------+-------+
SET GLOBAL event_scheduler = TRUE;
```

```
mysql> SELECT * FROM event_test;
+----+--------------------------------+----------------+------+
| id | created                        | action         | val  |
+----+--------------------------------+----------------+------+
|  1 | 2009-10-17 15:08:36            | 1 Minute       | 0836 |
|  2 | 2009-10-17 15:08:42            | Minute         | 0842 |
|  3 | 2009-10-17 15:09:42            | Minute         | 0942 |
|  4 | 2009-10-17 15:10:42            | Minute         | 1042 |
+----+--------------------------------+----------------+------+
```

```
mysql> SHOW EVENTS\G
*************************** 1. row ***************************
                  Db: chapter6
                Name: e_minute
             Definer: root@localhost
           Time zone: SYSTEM
                Type: RECURRING
          Execute at: NULL
      Interval value: 1
      Interval field: MINUTE
               Starts: 2009-10-17 14:51:42
                Ends: NULL
              Status: ENABLED
           Originator: 1
 character_set_client: latin1
 collation_connection: latin1_swedish_ci
  Database Collation: latin1_swedish_ci
```

## 修改事件

默认情况下，事件完成后会自动删除。你可以在定义事件时使用 ON COMPLETION PRESERVE 语法来覆盖此行为。对于现有的循环事件，你可以选择禁用或删除事件以停止操作：

```
ALTER EVENT e_minute DISABLE;
mysql> SHOW EVENTS\G
************************** 1. row **************************
Db: chapter6
Name: e_minute
Definer: root@localhost
Time zone: SYSTEM
Type: RECURRING
Execute at: NULL
Interval value: 1
Interval field: MINUTE
Starts: 2009-10-17 14:51:42
Ends: NULL
Status: DISABLED
Originator: 1
character_set_client: latin1
collation_connection: latin1_swedish_ci
Database Collation: latin1_swedish_ci
```

你也可以重新启用事件。然后你可以观察数据，以显示与事件被禁用时间相对应的数据间隙：

```
ALTER EVENT e_minute ENABLE;
SELECT SLEEP(60);
SELECT * FROM event_test;
```

| id | 创建时间 | 操作 | 值 |
|---|---|---|---|
| 1 | 2009-10-17 15:08:36 | 1 分钟 | 0836 |
| 2 | 2009-10-17 15:08:42 | 分钟 | 0842 |
| 3 | 2009-10-17 15:09:42 | 分钟 | 0942 |
| 4 | 2009-10-17 15:10:42 | 分钟 | 1042 |
| 5 | 2009-10-17 15:11:42 | 分钟 | 1142 |
| 6 | 2009-10-17 15:12:42 | 分钟 | 1242 |
| 7 | 2009-10-17 15:13:42 | 分钟 | 1342 |
| 8 | 2009-10-17 15:18:42 | 分钟 | 1842 |

正如你所见，每分钟运行的事件在五分钟内未运行。

为了结束生命周期，你可以使用 DROP 语法像其他数据库对象一样删除事件：

```
DROP event e_minute;
SHOW EVENTS\G
Empty set (0.00 sec)
```

## 事件权限

为了拥有创建或修改事件的权限，你需要额外的权限：EVENT 权限。你可以使用标准的 GRANT 和 REVOKE 命令为用户授予特定数据库模式或所有模式的此权限。例如：

```
GRANT EVENT ON chapter6.* TO wrox@localhost;
REVOKE EVENT on chapter6.* FROM wrox@localhost;
```

## 事件元数据

MySQL 事件信息可从两个来源获得：INFORMATION_SCHEMA 和 mysql 元模式。例如：

```
mysql> select * from mysql.event\G
******************************* 1. row *******************************
          db: chapter6
        name: e_minute
        body: INSERT INTO event_test (action,val)
              VALUES ('Minute',DATE_FORMAT(NOW(),'%i:%s'))
     definer: root@localhost
   execute_at: NULL
 interval_value: 1
 interval_field: MINUTE
      created: 2009-10-17 14:51:42
     modified: 2009-10-17 14:51:42
 last_executed: 2009-10-17 19:12:42
      starts: 2009-10-17 18:51:42
        ends: NULL
      status: ENABLED
 on_completion: DROP
     sql_mode:
     comment: Perform event every minute
   originator: 1
    time_zone: SYSTEM
character_set_client: latin1
collation_connection: latin1_swedish_ci
    db_collation: latin1_swedish_ci
     body_utf8: INSERT INTO event_test (action,val)
                 VALUES ('Minute',DATE_FORMAT(NOW(),'%i:%s'))
```

```
mysql> SELECT * FROM INFORMATION_SCHEMA.EVENTS\G
******************************* 1. row *******************************
  EVENT_CATALOG: NULL
  EVENT_SCHEMA: chapter6
    EVENT_NAME: e_minute
      DEFINER: root@localhost
    TIME_ZONE: SYSTEM
    EVENT_BODY: SQL
EVENT_DEFINITION: INSERT INTO event_test (action,val)
                  VALUES ('Minute',DATE_FORMAT(NOW(),'%i:%s'))
      EVENT_TYPE: RECURRING
    EXECUTE_AT: NULL
  INTERVAL_VALUE: 1
  INTERVAL_FIELD: MINUTE
      SQL_MODE:
       STARTS: 2009-10-17 15:23:59
         ENDS: NULL
       STATUS: ENABLED
 ON_COMPLETION: NOT PRESERVE
      CREATED: 2009-10-17 15:23:59
  LAST_ALTERED: 2009-10-17 15:23:59
LAST_EXECUTED: 2009-10-17 15:23:59
EVENT_COMMENT: Perform event every minute
ORIGINATOR: 1
CHARACTER_SET_CLIENT: latin1
COLLATION_CONNECTION: latin1_swedish_ci
DATABASE_COLLATION: latin1_swedish_ci
```

## 摘要

本章涵盖了你在其他关系数据库产品中会找到的许多 SQL 高级功能，以及一些 MySQL 特定的高级功能，你可以在软件开发实践中使用它们来丰富产品的功能。

事务的使用是正常应用程序开发的关键组成部分，而只了解 MySQL 的用户可能不会利用这一重要的业务功能。事务提供的 ACID 能力、引用约束、MVCC 和自动崩溃恢复的额外好处是 MySQL 应用程序的关键考虑因素。默认情况下，应用程序应以事务为出发点进行编写。使用存储过程、存储函数和触发器提供了一种在更接近数据库的层提供业务逻辑的替代方法，并且与前端开发技术无关。MySQL 中的视图可以为应用层提供抽象和简化层，以及为底层信息提供不同的读取安全手段。

最后，MySQL 复制通过提供数据的额外副本来扩展对数据的操作。它用于许多目的，包括备份、读取扩展和数据库维护，MySQL 复制是 PHP 和 MySQL 专家必备的高级功能。

## 7

## 使用用户定义函数扩展 MySQL

### 本章内容？

- MySQL UDF 应用程序编程接口 (API) 的介绍
- 设计、实现、测试和调试 UDF 的完整步骤
- 使用 GNU 调试器 gdb 的介绍

你是否曾经被分配一个项目，该项目需要 MySQL 中的某些功能，而这些功能并未包含，或者编写存储过程或函数并不能完全实现你需要的功能？也许你有一个自定义库或 C 程序，你希望从 MySQL 内部访问它，你可以在应用程序对数据库的调用中使用它，并且利用你的库提供的任何性能优势？

MySQL 作为一个灵活的系统，为你提供了一种扩展服务器并创建自己的函数的方法——不同于存储过程或函数——它们像 MySQL 中包含的标准内置函数一样执行。MySQL 提供了编写 *用户定义函数* 的 API，否则也称为 *UDFs*，它们是用 C 或 C++ 编写的函数，可以做用户需要它们做的任何事情，在功能方面仅受想象力的限制。虽然本书面向 PHP 程序员，但通过使用 UDF API 用 C 或 C++ 编写 UDF 来扩展 MySQL 是相当直接的，结果非常有用。任何具有编程思维的经验丰富的 PHP 开发人员都应该能够轻松掌握如何实现一个 UDF——并且在过程中更深入地了解 MySQL 的某些内部结构以及获得 C 或 C++ 的复习！

本章演示如何实现一个功能齐全、有用的 UDF。在阅读本文时，你可能会对自己说：“嘿，我以为这本应该是 PHP 书！”然而，
