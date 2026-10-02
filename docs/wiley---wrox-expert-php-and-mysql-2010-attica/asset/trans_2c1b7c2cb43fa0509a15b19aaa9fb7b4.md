
确保 ACID 合规性的 Consistency 部分。虽然可以使用手动程序来维护数据完整性，但这是一种不太理想的方法。

在当前生产版 MySQL 5.1 中，外键仅在 InnoDB 存储引擎中受支持。一些额外的第三方存储引擎也支持外键。请参阅第 3 章了解更多信息。

MySQL 参考手册定义了可在 CREATE TABLE 或 ALTER TABLE 中使用的 FOREIGN KEY 语法如下：

```
[CONSTRAINT [symbol]] FOREIGN KEY
    [index_name] (index_col_name, ...)
    REFERENCES tbl_name (index_col_name,...)
    [ON DELETE reference_option]
    [ON UPDATE reference_option]

reference_option:
    RESTRICT | CASCADE | SET NULL | NO ACTION
```

如先前的连接示例所示，countries 表中包含一个无效的颜色。如果您使用外键定义了表，就不会遇到此数据完整性问题。这提供了一个代码示例，说明了纠正不良数据所需的步骤。首先，您应尝试创建缺失的外键完整性约束，如清单 1-41 所示。

### LISTING 1-41: foreign-key-alter.sql

```
mysql> ALTER TABLE flags
    -> ADD FOREIGN KEY (color)
    -> REFERENCES colors (color)
    -> ON DELETE CASCADE;
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails ('chapter1'.`#sql-86f_1928bd`, CONSTRAINT `#sql-86f_1928bd_ibfk_1` FOREIGN KEY (`color`) REFERENCES `colors` (`color`) ON DELETE CASCADE)
```

由于该错误，您现在需要在父表或子表中识别出问题数据。您可以使用子查询来识别，或者如前所示，使用外连接来检索无效数据。由于样本数据量小，我们知道颜色 Yellow 是导致失败的原因。您是否：

- 删除包含无效数据的违规行？这随后会为瑞典国旗产生无效且一致的数据。
- 删除瑞典的所有旗帜数据？这将删除您可能使用或在其他地方可能有价值的潜在有效数据。
- 向 colors 基表添加缺失的数据？

这些是重要的设计决策，会影响应用程序的运行方式。在清单 1-42 中，我们决定采用最后一个选项，并将缺失的颜色 Yellow 添加到 colors 表中，以成功添加外键。

### LISTING 1-42: foreign-key-yellow.sql

```
mysql> INSERT INTO colors (color,is_primary,is_dark,is_rainbow)
    VALUES ('Yellow','no','no','yes');

mysql> ALTER TABLE flags
    ADD FOREIGN KEY (color)
    REFERENCES colors (color)
    ON DELETE CASCADE;

mysql> SELECT *
    FROM colors
    WHERE color='Yellow';
```

| 颜色 | 是否主色 | 是否深色 | 是否彩虹色 |
|---|---|---|---|
| Yellow | no | no | yes |

```
mysql> SELECT *
    FROM flags
    WHERE country IN (SELECT country
                      FROM flags
                      WHERE color='Yellow');
```

| 国家 | 颜色 |
|---|---|
| Sweden | Blue |
| Sweden | Yellow |

您现在已在 colors 表和 flags 表之间定义了一个 FOREIGN KEY，其中旗帜的颜色必须存在于 colors 表中。您还定义了此规则具有级联 DELETE 规则，即如果删除一种颜色，也将删除所有使用该颜色的行。清单 1-43 显示了一个示例：

### LISTING 1-43: foreign-key-delete.sql

```
mysql> DELETE FROM colors WHERE color='Yellow';
mysql> SELECT * FROM flags WHERE color='Yellow';
Empty set (0.00 sec)

mysql> SELECT *
    FROM flags
    WHERE country IN (SELECT country
                      FROM flags
                      WHERE color='Yellow');

mysql> SELECT *
    FROM flags
    WHERE country = 'Sweden';
```

| 国家 | 颜色 |
|---|---|
| Sweden | Blue |

尽管 FOREIGN KEY 约束已在行级别确保了数据完整性，但它并未执行您所期望的那种完整性。使用 FOREIGN KEY 约束无法确保您理想希望达到的应用程序完整性级别。

> 在添加任何数据之前定义外键定义是一项非常重要的架构设计决策。以后删除约束比以后添加约束容易得多。

InnoDB 外键约束的另一个好处是要求 from 表和 to 表中的两列必须使用相同的数据类型。这提高了数据库的数据完整性。

您可以在 http://dev.mysql.com/doc/refman/5.0/en/innodb-foreign-key-constraints.html 找到有关 InnoDB 中外键的更多信息。

在 MySQL 中，可以使用 SET foreign_key_checks = 0|1 选项禁用外键约束。这会进一步混淆数据库的完整性，因为通过 DML 语句操作数据的权限可以通过 SET 命令在 SESSION 或 GLOBAL 级别被覆盖。

> 使用级联外键约束和 REPLACE 命令时，数据库可能会表现出意外的行为或性能。REPLACE 命令通常被理解并描述为对匹配行的 UPDATE。如果未找到行，则 INSERT 命令会插入该行。然而在实现中，REPLACE 实际上是对现有行的 DELETE，然后是对新行的 INSERT。在添加使用级联语法的约束时，请注意 REPLACE 的此执行路径。

## 使用服务器 SQL 模式

最早在 4.1 中引入并在 5.0 中增强，服务器 SQL 模式提供了各种功能，包括不同类型的关系完整性。MySQL 默认情况下对数据完整性非常宽松，这可能导致意外的结果。例如，请查看清单 1-44。

### LISTING 1-44: no-sql-mode.sql

```
mysql> CREATE TABLE example (
    ->  i TINYINT UNSIGNED NOT NULL,
    ->  c CHAR(2) NULL
    -> ) ENGINE=InnoDB DEFAULT CHARSET latin1;

mysql> INSERT INTO example (i) VALUES (0), (-1),(255), (9000);
Query OK, 4 rows affected, 2 warnings (0.00 sec)

mysql> SHOW WARNINGS;
```

| 级别 | 代码 | 消息 |
|---|---|---|
| Warning | 1264 | Out of range value for column 'i' at row 2 |
| Warning | 1264 | Out of range value for column 'i' at row 4 |

2 rows in set (0.00 sec)

```
mysql> INSERT INTO example (c) VALUES ('A'),('BB'),('CCC');
Query OK, 3 rows affected, 2 warnings (0.00 sec)

mysql> SHOW WARNINGS;
```

| 级别 | 代码 | 消息 |
|---|---|---|
| Warning | 1364 | Field 'i' doesn't have a default value |
| Warning | 1265 | Data truncated for column 'c' at row 3 |

2 rows in set (0.00 sec)

```
mysql> SELECT * FROM example;
```

| i | c |
|---|---|
| 0 | NULL |
| 0 | NULL |
| 255 | NULL |
| 255 | NULL |
| 0 | A |
| 0 | BB |
| 0 | CC |

7 rows in set (0.00 sec)

在这些前面的 SQL 语句中，您会发现数据中存在许多实际错误，但实际上并未发生错误。

MySQL 仅发出警告，而大多数应用程序开发人员实际上会忽略这些警告，从不执行 SHOW WARNINGS 来识别这些静默的数据截断。您期望插入值为 9,000；然而，只存储了 255。您期望插入一个三字符的字符串，但只记录了两个字符。您未为 NOT NULL 列指定值，但仍记录了默认值。

解决方案是使用自 MySQL 5.0 起可用的严格 SQL 模式。MySQL 提供了两种严格类型：STRICT_ALL_TABLES 和 STRICT_TRANS_TABLES。为了确保所有表的数据完整性，本节仅讨论 STRICT_ALL_TABLES。当您重新运行之前的 SQL 语句时，您会看到清单 1-45 中的代码：

### LISTING 1-45: sql-mode-traditional.sql

```
mysql> TRUNCATE TABLE example;
Query OK, 0 rows affected (0.00 sec)

mysql> SET SESSION sql_mode='TRADITIONAL';
Query OK, 0 rows affected (0.00 sec)

mysql> INSERT INTO example (i) VALUES (0), (-1),(255), (9000);
ERROR 1264 (22003): Out of range value for column 'i' at row 2
mysql> INSERT INTO example (c) VALUES ('A'),('BB'),('CCC');
ERROR 1364 (HY000): Field 'i' doesn't have a default value
mysql> SELECT * FROM example;
Empty set (0.00 sec)

mysql> INSERT INTO example (i) VALUES (0);
mysql> INSERT INTO example (i) VALUES (-1);
ERROR 1264 (22003): Out of range value for column 'i' at row 1
mysql> INSERT INTO example (i) VALUES (255);
mysql> INSERT INTO example (i) VALUES (9000);
ERROR 1264 (22003): Out of range value for column 'i' at row 1
mysql> INSERT INTO example (c) VALUES ('A');
ERROR 1364 (HY000): Field 'i' doesn't have a default value
mysql> INSERT INTO example (i,c) VALUES (1,'A');
mysql> INSERT INTO example (i,c) VALUES (1,'BB');
mysql> INSERT INTO example (i,c) VALUES (1,'CCC');
ERROR 1406 (22001): Data too long for column 'c' at row 1
mysql> SELECT * FROM example;
```

| i | c |
|---|---|
| 0 | NULL |
| 255 | NULL |
| 1 | A |
| 1 | BB |

4 rows in set (0.00 sec)

您现在会注意到更传统的数据库系统所期望的错误。您还会注意到多个 INSERT VALUES 语句会无条件失败。可以通过使用 MyISAM 等非事务存储引擎来改变此行为，并进一步混淆可能缺乏数据完整性的情况。清单 1-46 显示了一个示例。

### LISTING 1-46: sql-mode-traditional-myisam.sql

```
mysql> ALTER TABLE example ENGINE=MyISAM;
mysql> TRUNCATE TABLE example;
```
