
Perform a sample transaction that inserts records into these two tables:

```
START TRANSACTION;
INSERT INTO trans_parent (val) VALUES('a');
INSERT INTO trans_child (parent_id,created) VALUES(LAST_INSERT_ID(),NOW());

INSERT INTO trans_parent (val) VALUES('a');
ERROR 1062 (23000): Duplicate entry 'a' for key 'val'
ROLLBACK;
Query OK, 0 rows affected (0.01 sec)

SELECT * FROM trans_parent;
Empty set (0.00 sec)

SELECT * FROM trans_child;
Empty set (0.00 sec)
```

As you can see, no data has been recorded as part of the failing transaction.

## Consistency

Consistency ensures that the integrity of the entire database data remains consistent as the result of a given transaction. The following is an example where the data is consistent based on the defined referential integrity rules:

```
START TRANSACTION;
INSERT INTO trans_parent(val) VALUES('a');
INSERT INTO trans_child(parent_id,created) VALUES(999,NOW());
COMMIT;
```

SELECT * FROM trans_parent;

| id | val |
|----|-----|
| 3  | a   |

mysql> SELECT * FROM trans_child;

| id | parent_id | created |
|----|-----------|---------|
| 2  | 999       | 2009-09-21 23:53:02 |

In this example, you obviously created a child record with an invalid and non-existing parent_id; however, you have not defined any constraints to enforce this consistency. So, in Listing 6-10, create the tables with these additional constraints.

### LISTING 6-10: trans-table-fk.sql

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_275_0.png)

```
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

Repeat the sample transaction that inserts records into these two tables:

```
START TRANSACTION;
INSERT INTO trans_parent(val) VALUES('a');
INSERT INTO trans_child(parent_id,created) VALUES(999,NOW());

ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`chapter6`.`trans_child`, CONSTRAINT `trans_child_ibfk_1` FOREIGN KEY (`parent_id`) REFERENCES `trans_parent` (`id`))
ROLLBACK;
```

In this example, the data that was previously successfully added now fails. This integrity requires valid data to be entered. For example:

```
START TRANSACTION;
INSERT INTO trans_parent(val) VALUES('a');
INSERT INTO trans_child(parent_id,created) VALUES(LAST_INSERT_ID(),NOW());
COMMIT;
```

This transaction added a parent record and a child record. Now try to break this integrity:

```
START TRANSACTION;
DELETE FROM trans_parent;
ERROR 1451 (23000): Cannot delete or update a parent row: a foreign key constraint fails (`chapter6`.`trans_child`, CONSTRAINT `trans_child_ibfk_1` FOREIGN KEY (`parent_id`) REFERENCES `trans_parent` (`id`))
ROLLBACK;
```

As you can see, an attempt to delete the parent record, when a child record exists, results in an error. You can address this by providing a cascading constraint:

```
ALTER TABLE trans_child
DROP FOREIGN KEY trans_child_ibfk_1,
ADD FOREIGN KEY (parent_id) REFERENCES trans_parent(id) ON DELETE CASCADE;
```

```
START TRANSACTION;
DELETE FROM trans_parent;
COMMIT;

SELECT * FROM trans_parent;
Empty set (0.00 sec)
SELECT * FROM trans_child;
Empty set (0.00 sec)
```

The deletion of the parent data, with a foreign key constraint to cascade the delete, also deletes the child records.

## Isolation

MySQL provides four different isolation levels to support multiversion concurrency control (MVCC). These are all used by InnoDB. If you are unfamiliar with the isolation concept, you can think of this as the amount of data that has been saved in separate concurrent transactions, which is available in the current transaction.

The default transaction isolation level is REPEATABLE-READ. This means that during a transaction the values retrieved in a SELECT will remain consistent for all repeating SELECT statements during the transaction irrespective of other committed statements.

The isolation level READ-COMMITTED enables SELECT statements to see committed data that has occurred in other transactions during the execution of the current transaction.

> It is often the misconception of Oracle Database administrators to change the default isolation level from REPEATABLE-READ to READ-COMMITTED. In Oracle, the default transaction level is READ-COMMITTED; however, though the name is used in MySQL, its underlying functional specification is indeed different.

The modification of the isolation level has an impact on MySQL replication. This is discussed in detail in the following section. The best advice is to not modify the isolation level value from the default of REPEATABLE_READ.

You only need one table to demonstrate the various options as shown in Listing 6-11.

### LISTING 6-11: isolation-table.sql

```
DROP TABLE IF EXISTS transaction_test;
CREATE TABLE transaction_test(
  id INT UNSIGNED NOT NULL AUTO_INCREMENT,
  val VARCHAR(20) NOT NULL,
  created TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY(id)
) ENGINE=InnoDB DEFAULT CHARSET latin1;
```

Start with some initial seeded data for reference within the transaction:

```
INSERT INTO transaction_test(val) VALUES ('a'),('b'),('c');
```

### Repeatable Read

To perform these tests you will need two open mysql client sessions. These commands will be run in parallel.

In the first session, run the following commands:

```
SELECT @@global.tx_isolation, @@session.tx_isolation;
START TRANSACTION;
```

```
SELECT * FROM transaction_test;
SELECT SLEEP(20);
INSERT INTO transaction_test(val) VALUES (@@session.tx_isolation);
SELECT * FROM transaction_test;
COMMIT;
```

In the second session, you need to execute these commands immediately while the first session is running (i.e. during the SLEEP() portion of this example):

```
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

As you can see, in the second session you added three additional rows and committed the data before the first session transaction completed. Look at the results of the first session commands now for comparison of the data visible in the table:

```
SELECT * FROM transaction_test;
```

| id | val | created |
|----|-----|---------|
| 1 | a | 2009-09-21 00:19:43 |
| 2 | b | 2009-09-21 00:19:43 |
| 3 | c | 2009-09-21 00:19:43 |

3 rows in set (0.00 sec)

```
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

The first transaction did not see the results of the second completed transaction. After the COMMIT has been executed in the first session, you can see the complete results by running the following query:

```
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

### Read Committed

You can rerun the same SQL statements with the transaction isolation level set to READ-COMMITTED. First reset your seed data:

```
TRUNCATE TABLE transaction_test;
INSERT INTO transaction_test(val) VALUES ('a'),('b'),('c');
```

In session 1, re-run the following SQL:

```
SET @@session.tx_isolation = 'READ-COMMITTED';
SELECT @@global.tx_isolation, @@session.tx_isolation;
START TRANSACTION;
SELECT * FROM transaction_test;
SELECT SLEEP(20);
INSERT INTO transaction_test(val) VALUES (@@session.tx_isolation);
SELECT * FROM transaction_test;
COMMIT;
```

In session 2, re-run the following SQL:

```
START TRANSACTION;
INSERT INTO transaction_test(val) VALUES ('x'),('y'),('z');
SELECT * FROM transaction_test;
COMMIT;
```

If we now look at the actual output of the SQL statements in session 1, we will see a difference between this output and that of the REPEATABLE-READ example.

```
SET @@session.tx_isolation = 'READ-COMMITTED';
SELECT @@global.tx_isolation, @@session.tx_isolation;
```

| @@global.tx_isolation | @@session.tx_isolation |
|-----------------------|------------------------|
| REPEATABLE-READ | READ-COMMITTED |

```
START TRANSACTION;
SELECT * FROM transaction_test;
```
