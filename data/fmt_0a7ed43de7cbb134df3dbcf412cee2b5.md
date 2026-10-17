
```sql
TRUNCATE TABLE trans_parent;
DROP TABLE IF EXISTS trans_child;
CREATE TABLE trans_child (
id	INT UNSIGNED NOT NULL AUTO_INCREMENT,
parent_id INT UNSIGNED NOT NULL,
created TIMESTAMP NOT NULL,
PRIMARY KEY (id),
INDEX (parent_id),
FOREIGN KEY (parent_id) REFERENCES trans_parent(id)
) ENGINE=InnoDB DEFAULT CHARSET latin1;
```

重复向这两个表插入记录的示例事务：

```sql
START TRANSACTION;
INSERT INTO trans_parent(val) VALUES('a');
INSERT INTO trans_child(parent_id,created) VALUES(999,NOW());

ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`chapter6`.`trans_child`, CONSTRAINT `trans_child_ibfk_1` FOREIGN KEY (`parent_id`) REFERENCES `trans_parent` (`id`))
ROLLBACK;
```

在此示例中，以前成功添加的数据现在失败了。这种完整性要求输入有效数据。例如：

```sql
START TRANSACTION;
INSERT INTO trans_parent(val) VALUES('a');
INSERT INTO trans_child(parent_id,created) VALUES(LAST_INSERT_ID(),NOW());
COMMIT;
```

此事务添加了一条父记录和一条子记录。现在尝试破坏这种完整性：

```sql
START TRANSACTION;
DELETE FROM trans_parent;
ERROR 1451 (23000): Cannot delete or update a parent row: a foreign key constraint fails (`chapter6`.`trans_child`, CONSTRAINT `trans_child_ibfk_1` FOREIGN KEY (`parent_id`) REFERENCES `trans_parent` (`id`))
ROLLBACK;
```

正如你所见，当子记录存在时，尝试删除父记录会导致错误。你可以通过提供级联约束来解决此问题：

```sql
ALTER TABLE trans_child
DROP FOREIGN KEY trans_child_ibfk_1,
ADD FOREIGN KEY (parent_id) REFERENCES trans_parent(id) ON DELETE CASCADE;
```

```sql
START TRANSACTION;
DELETE FROM trans_parent;
COMMIT;

SELECT * FROM trans_parent;
Empty set (0.00 sec)
SELECT * FROM trans_child;
Empty set (0.00 sec)
```

删除父数据时，使用外键约束级联删除，也会删除子记录。

## 隔离性

MySQL 提供了四种不同的隔离级别来支持多版本并发控制（MVCC）。这些都由 `InnoDB` 使用。如果你不熟悉隔离概念，可以将其理解为在单独的并发事务中保存的数据量，这些数据在当前事务中可用。

默认事务隔离级别是 `REPEATABLE-READ`。这意味着在事务期间，`SELECT` 中检索的值对于事务期间的所有重复 `SELECT` 语句都将保持一致，而不受其他已提交语句的影响。

隔离级别 `READ-COMMITTED` 使 `SELECT` 语句能够看到在当前事务执行期间在其他事务中发生的已提交数据。

> Oracle 数据库管理员经常误以为将默认隔离级别从 `REPEATABLE-READ` 改为 `READ-COMMITTED`。在 Oracle 中，默认事务级别是 `READ-COMMITTED`；然而，尽管该名称在 MySQL 中使用，其底层功能规范确实不同。

修改隔离级别会对 MySQL 复制产生影响。这将在下一节中详细讨论。最好的建议是不要将隔离级别值从默认的 `REPEATABLE_READ` 修改。

如列表 6-11 所示，你只需要一个表来演示各种选项。

### 列表 6-11：isolation-table.sql

```sql
DROP TABLE IF EXISTS transaction_test;
CREATE TABLE transaction_test(
  id INT UNSIGNED NOT NULL AUTO_INCREMENT,
  val VARCHAR(20) NOT NULL,
  created TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY(id)
) ENGINE=InnoDB DEFAULT CHARSET latin1;
```

从事务中用于参考的一些初始种子数据开始：

```sql
INSERT INTO transaction_test(val) VALUES ('a'),('b'),('c');
```

### 可重复读

执行这些测试时，你需要两个打开的 `mysql` 客户端会话。这些命令将并行运行。

在第一个会话中，运行以下命令：

```sql
SELECT @@global.tx_isolation, @@session.tx_isolation;
START TRANSACTION;
```

```sql
SELECT * FROM transaction_test;
SELECT SLEEP(20);
INSERT INTO transaction_test(val) VALUES (@@session.tx_isolation);
SELECT * FROM transaction_test;
COMMIT;
```

在第二个会话中，你需要在第一个会话运行时立即执行这些命令（即在此示例的 `SLEEP()` 部分期间）：

```sql
START TRANSACTION;
INSERT INTO transaction_test(val) VALUES ('x'),('y'),('z');
SELECT * FROM transaction_test;
```

| id | val | created |

|----|-----|---------|

| 1 | a | 2009-09-21 00:19:43 |

| 2 | b | 2009-09-21 00:19:43 |

| 3 | c | 2009-09-21 00:19:43 |

| 4 | x | 2009-09-21 00:21:00 |

| 5 | y | 2009-09-21 00:21:00 |

| 6 | z | 2009-09-21 00:21:00 |

COMMIT;

正如你所见，在第二个会话中，你在第一个会话事务完成之前添加了三行额外数据并提交了数据。现在查看第一个会话命令的结果，以比较表中可见数据的差异：

```sql
SELECT * FROM transaction_test;
```

| id | val | created |

|----|-----|---------|

| 1 | a | 2009-09-21 00:19:43 |

| 2 | b | 2009-09-21 00:19:43 |

| 3 | c | 2009-09-21 00:19:43 |

3 rows in set (0.00 sec)

```sql
SELECT SLEEP(20);
INSERT INTO transaction_test(val) VALUES (@@session.tx_isolation);
```

mysql> SELECT * FROM transaction_test;

| id | val | created |

|----|-----|---------|

| 1 | a | 2009-09-21 00:19:43 |

| 2 | b | 2009-09-21 00:19:43 |

| 3 | c | 2009-09-21 00:19:43 |

| 7 | REPEATABLE-READ | 2009-09-21 00:21:01 |

4 rows in set (0.00 sec)

第一个事务没有看到第二个已完成事务的结果。在第一个会话中执行 `COMMIT` 后，你可以通过运行以下查询查看完整结果：

```sql
mysql> SELECT * FROM transaction_test;
```

| id | val | created |

|----|-----|---------|

| 1 | a | 2009-09-21 00:19:43 |

| 2 | b | 2009-09-21 00:19:43 |

| 3 | c | 2009-09-21 00:19:43 |

| 4 | x | 2009-09-21 00:21:00 |

| 5 | y | 2009-09-21 00:21:00 |

| 6 | z | 2009-09-21 00:21:00 |

| 7 | REPEATABLE-READ | 2009-09-21 00:21:01 |

### 读已提交

你可以使用事务隔离级别设置为 `READ-COMMITTED` 重新运行相同的 SQL 语句。首先重置你的种子数据：

```sql
TRUNCATE TABLE transaction_test;
INSERT INTO transaction_test(val) VALUES ('a'),('b'),('c');
```

在会话 1 中，重新运行以下 SQL：

```sql
SET @@session.tx_isolation = 'READ-COMMITTED';
SELECT @@global.tx_isolation, @@session.tx_isolation;
START TRANSACTION;
SELECT * FROM transaction_test;
SELECT SLEEP(20);
INSERT INTO transaction_test(val) VALUES (@@session.tx_isolation);
SELECT * FROM transaction_test;
COMMIT;
```

在会话 2 中，重新运行以下 SQL：

```sql
START TRANSACTION;
INSERT INTO transaction_test(val) VALUES ('x'),('y'),('z');
SELECT * FROM transaction_test;
COMMIT;
```

如果我们现在查看会话 1 中 SQL 语句的实际输出，我们会看到此输出与 `REPEATABLE-READ` 示例之间的差异。

```sql
SET @@session.tx_isolation = 'READ-COMMITTED';
SELECT @@global.tx_isolation, @@session.tx_isolation;
```

| @@global.tx_isolation | @@session.tx_isolation |

|-----------------------|------------------------|

| REPEATABLE-READ | READ-COMMITTED |

```sql
START TRANSACTION;
SELECT * FROM transaction_test;
```

| id | 值 | 创建时间 |

|---|---|---|

| 1 | a | 2009-09-21 00:27:35 |

| 2 | b | 2009-09-21 00:27:35 |

| 3 | c | 2009-09-21 00:27:35 |

```sql
SELECT SLEEP(20);
```

```sql
mysql> SELECT * FROM transaction_test;
```

| id | 值 | 创建时间 |

|---|---|---|

| 1 | a | 2009-09-21 00:27:35 |

| 2 | b | 2009-09-21 00:27:35 |

| 3 | c | 2009-09-21 00:27:35 |

| 4 | x | 2009-09-21 00:26:44 |

| 5 | y | 2009-09-21 00:26:44 |

| 6 | z | 2009-09-21 00:26:44 |

| 7 | READ-COMMITTED | 2009-09-21 00:26:54 |

```sql
COMMIT;
```

如你所见，事务中的数据结果在事务期间发生了变化，以反映已提交的事务。

虽然这只是一个演示，但你的应用程序可能永远不需要在事务期间多次选择相同的信息。

总之，`REPEATABLE-READ` 是使用最广泛且经过测试的隔离级别，因为它是默认值，应优先于 `READ-COMMITTED` 使用。

## 读取未提交

正如名称所示，`READ-UNCOMMITTED` 会显示脏数据，即未提交的数据。本节不会在此演示完整输出；然而，如果你运行上一节的 SQL 语句并排除第二个会话的 `COMMIT`，你将观察到与 `READ-COMMITTED` 示例中提供的相同输出的特征。然后，例如，你可以执行 `ROLLBACK`，但第一个事务仍会记录这些现在三个幻影行值 `x`、`y` 和 `z`。

In session 1:

```sql
SET @@session.tx_isolation = 'READ-UNCOMMITTED';
```

以下代码显示会话 1 的最后一部分：

```sql
SELECT * FROM transaction_test;
```

| id | 值 | 创建时间 |

|---|---|---|

| 1 | a | 2009-10-17 16:12:33 |

| 2 | b | 2009-10-17 16:12:33 |

| 3 | c | 2009-10-17 16:12:33 |

| 4 | x | 2009-10-17 16:12:49 |

| 5 | y | 2009-10-17 16:12:49 |

| 6 | z | 2009-10-17 16:12:49 |

| 7 | READ-UNCOMMITTED | 2009-10-17 16:13:02 |

以下代码显示带有 `ROLLBACK` 的会话 2 的最后一部分：

```sql
SELECT * FROM transaction_test;
```

| id | 值 | 创建时间 |

|---|---|---|

| 1 | a | 2009-10-17 16:12:33 |

| 2 | b | 2009-10-17 16:12:33 |

| 3 | c | 2009-10-17 16:12:33 |

| 4 | x | 2009-10-17 16:12:49 |

| 5 | y | 2009-10-17 16:12:49 |

| 6 | z | 2009-10-17 16:12:49 |

6 rows in set (0.00 sec)

### 等待第一个会话完成。

ROLLBACK;

```sql
SELECT * FROM transaction_test;
```

| id | 值 | 创建时间 |

|---|---|---|

| 1 | a | 2009-10-17 16:12:33 |

| 2 | b | 2009-10-17 16:12:33 |

| 3 | c | 2009-10-17 16:12:33 |

| 7 | READ-UNCOMMITTED | 2009-10-17 16:13:02 |

## 可序列化

最后的隔离级别是 `SERIALIZABLE`。在这种情况下，表实际上以共享模式锁定，这迫使事务阻塞其他事务。如果你像之前所示重复 `REPEATABLE_READ` 测试，你将看到第一个会话的相同最终输出。然而，影响是第二个会话中的 `INSERT` 会被延迟，直到第一个事务完成，然后你会看到来自第一个会话的行：

```sql
SET @@session.tx_isolation = 'SERIALIZABLE';
```

以下代码显示第一个会话的结束：

```sql
SELECT * FROM transaction_test;
```

| id | 值 | 创建时间 |

|---|---|---|

| 1 | a | 2009-10-17 16:15:34 |

| 2 | b | 2009-10-17 16:15:34 |

| 3 | c | 2009-10-17 16:15:34 |

| 7 | SERIALIZABLE | 2009-10-17 16:16:06 |

4 rows in set (0.00 sec)

```sql
COMMIT;
```

以下代码显示第二个会话的结束：

```sql
INSERT INTO transaction_test(val) VALUES ('x'),('y'),('z');
```

Query OK, 3 rows affected (14.02 sec)

```sql
mysql> SELECT * FROM transaction_test;
```

| id | 值 | 创建时间 |

|---|---|---|

| 1 | a | 2009-10-17 16:15:34 |

| 2 | b | 2009-10-17 16:15:34 |

| 3 | c | 2009-10-17 16:15:34 |

| 4 | x | 2009-10-17 16:15:52 |

| 5 | y | 2009-10-17 16:15:52 |
