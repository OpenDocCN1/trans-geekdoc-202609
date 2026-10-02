
```
word VARCHAR(100) NOT NULL,
reverse_word VARCHAR(100) NOT NULL,
soundex_word VARCHAR(100) NOT NULL,
contains_a ENUM('Y','N') NOT NULL DEFAULT 'N',
md5 CHAR(32) NOT NULL,
PRIMARY KEY(word),
INDEX (soundex_word),
UNIQUE INDEX (md5),
INDEX (reverse_word(10))
) ENGINE=InnoDB DEFAULT CHARSET latin1 COLLATE latin1_general_cs;
INSERT INTO wide_innodb (word,reverse_word,soundex_word,contains_a,md5)
SELECT DISTINCT c,REVERSE(c),SOUNDEX(c),IF(INSTR(c,'a')>0,'Y','N'),MD5(c)
FROM example_innodb;
```

```
SELECT table_name,table_rows,row_format,
      data_length/1024 AS data,index_length/1024 AS indx
FROM   INFORMATION_SCHEMA.TABLES
WHERE  table_name LIKE 'wide_%';
```

| table_name | table_rows | row_format | data | indx |
|------------|------------|------------|------|------|
| wide_innodb | 224025 | Compact | 23104.0000 | 39536.0000 |
| wide_myisam | 234936 | Dynamic | 15086.1836 | 20962.0000 |

从这个示例可以看出，InnoDB 表的总磁盘占用相比 MyISAM 增加了 70%；然而，索引部分大了 100%。当你如清单 3-8 所示引入 AUTO_INCREMENT 主键时，数据部分的磁盘占用减少了 10%。你还会看到索引空间减少了 5%，但你确实添加了一个额外的索引来模拟主键。

## 清单 3-8：wide-innodb-with-pk.sql

```
CREATE TABLE wide_innodb_with_pk (
  id INT UNSIGNED NOT NULL AUTO_INCREMENT,
  word VARCHAR(100) NOT NULL,
  reverse_word VARCHAR(100) NOT NULL,
  soundex_word VARCHAR(100) NOT NULL,
  contains_a ENUM('Y','N') NOT NULL DEFAULT 'N',
  md5 CHAR(32) NOT NULL,
  PRIMARY KEY(id),
  UNIQUE INDEX(word),
  INDEX (soundex_word),
  UNIQUE INDEX (md5),
  INDEX (reverse_word(10))
) ENGINE=InnoDB DEFAULT CHARSET latin1 COLLATE latin1_general_cs;

INSERT INTO wide_innodb_with_pk (word,reverse_word,soundex_word,contains_a,md5)
SELECT DISTINCT c,REVERSE(c),SOUNDEX(c),IF(INSTR(c,'a')>0,'Y','N'),MD5(c)
FROM example_innodb;
SELECT table_name,table_rows,row_format,
```
```
data_length/1024 AS data,index_length/1024 AS indx
FROM INFORMATION_SCHEMA.TABLES
WHERE table_name LIKE 'wide_%';
```

| table_name | table_rows | row_format | data | indx |
|---|---|---|---|---|
| wide_innodb | 243525 | Compact | 23104.0000 | 39536.0000 |
| wide_innodb_with_pk | 244771 | Compact | 21040.0000 | 39040.0000 |
| wide_myisam | 234936 | Dynamic | 15086.1836 | 20962.0000 |

随着你开始添加额外的索引，差异会变得更大。以 MyISAM 索引数据作为对照测试，结构相同的 InnoDB 表大 100%，而带有 AUTO_INCREMENT 主键的 InnoDB 表仅大 80%。尽管这些表很小，你仍可以看到单列更改的影响。

| table_name | table_rows | row_format | data | indx |
|---|---|---|---|---|
| wide_innodb | 239154 | Compact | 21056.0000 | 67408.0000 |
| wide_innodb_with_pk | 235054 | Compact | 22064.0000 | 59488.0000 |
| wide_myisam | 234936 | Dynamic | 16003.9023 | 32535.0000 |

使用 MyISAM 时，执行 SELECT COUNT(*) FROM TABLE 的应用程序会得到即时响应，而对于 InnoDB 则必须通过读取数据来计算。对于大型表，这可能导致较高的性能影响，因为磁盘 I/O 以及从内部缓冲池刷新数据会显著影响其他在线操作。使用索引检索部分行以执行 COUNT(*) 是克服应用程序全表扫描所需的必要更改。

在较小的 MySQL 环境中，你可以找到用于文本搜索的 FULLTEXT 索引的使用。这种类型的索引仅在 MyISAM 中受支持。在这种情况下，通常的做法是在第二个表中复制列，该表仍为 MyISAM 表。这通常可以让你获得 InnoDB 的所有功能，以及 MyISAM 的 FULLTEXT 功能。这种方法存在数据完整性、性能和灾难恢复方面的影响。在重要的设计考虑方面应始终谨慎，以实现对整个系统的总体影响。

## 使用 InnoDB 优化 SQL

关于 InnoDB 讨论的最后一点是 SQL 优化。内部 MySQL 解析 SQL 查询，然后通过基于成本的优化器确定以最快时间满足查询的最佳方式。优化器使用表索引信息和列分布统计信息来确定最佳执行路径。MySQL 默认在 SQL 查询中每个表仅使用一个索引（有少数例外）。在连接多个表时，尤其是交叉表，仅使用一个索引。将表从 MyISAM 转换为 InnoDB 时，不能假设查询执行时使用相同的索引。重要的是通过 EXPLAIN 语法查看查询执行计划（QEP）。已经讨论了两种影响数据存储和检索的差异。对于 InnoDB，数据现在按主键顺序排列，这在使用主键时提供了顺序读取数据的能力。第二点是主键的值存储在二级索引中，从而在某些情况下可以将该值用作索引的第二个索引列。

与应用程序中的任何更改一样，重要的是在真实的生产条件下测试这些更改。在更改应用程序功能的同时将表从 `MyISAM` 转换为 `InnoDB`，当 MySQL 环境未适当调优，或包括所讨论的特定情况在内的情况未被理解并作为影响考虑时，可能导致性能变差。

## 内存

`Memory` 存储引擎，历史上也称为 `Heap` 存储引擎，是一种仅在内存中的表，不提供数据持久性。`Memory` 存储引擎实际上在需要临时表时由 mysql 内核内部使用。

### 关键特性
- 非常快，在内存中
- 非事务性
- 默认支持哈希索引
- 也支持 Btree 索引
- 非常适合主键查找

### 限制
- 不支持事务
- DML 和 DDL 语句上使用表级锁定
- 数据不持久
- 不支持 TEXT/BLOB 数据类型
- 固定行宽
- 无法限制所有 `Memory` 表的总内存量

### 重要参数
- `max_heap_table_size`：定义单个 `Memory` 表的最大大小。
- `tmp_table_size`：定义用作内部临时表时表的最大大小。
- `init_file`：定义在 MySQL 实例启动时执行的命令 SQL 文件。用于初始化 `Memory` 表的一种方式。

### 示例表用法

创建 `Memory` 表的语法（如清单 3-9 所示）与之前的示例相同。

## 清单 3-9：memory-example.sql

```
CREATE TABLE example_memory(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
    c VARCHAR(100) NOT NULL)
ENGINE=Memory;
```

Memory 表的大小受 max_heap_table_size 系统变量定义的表最大大小限制。清单 3-10 演示了表已满的错误消息，并根据比较 Fixed MyISAM 表大小来纠正最大大小，以显示 Memory 表中的数据。

## 清单 3-10：memory-load.sql

```
LOAD DATA INFILE '/usr/share/dict/words' INTO TABLE example_memory (c);
ERROR 1114 (HY000): The table 'example_memory' is full

SELECT table_name,table_rows,row_format,
    data_length/1024 AS data,index_length/1024 AS indx
FROM    INFORMATION_SCHEMA.TABLES
WHERE   table_name LIKE 'example_memory%';
```

| table_name | table_rows | row_format | data | indx |
|------------|------------|------------|------|------|
| example_memory | 144595 | Fixed | 15310.2539 | 1134.4219 |

```
SHOW GLOBAL VARIABLES LIKE 'max_heap_table_size';
```

| Variable_name | Value |
|---------------|-------|
| max_heap_table_size | 16777216 |

```
SET SESSION max_heap_table_size = 256*1024*1024;
TRUNCATE TABLE example_memory
LOAD DATA INFILE '/tmp/words' INTO TABLE example_memory (c);
Query OK, 234936 rows affected (0.37 sec)

SELECT table_name,table_rows,row_format,
    data_length/1024 AS data,index_length/1024 AS indx
FROM    INFORMATION_SCHEMA.TABLES
WHERE   table_name LIKE 'example_memory%';
```

| table_name | table_rows | row_format | data | indx |
|------------|------------|------------|------|------|
| example_memory | 234936 | Fixed | 24927.4258 | 1897.1172 |

使用大型内存表时，需要考虑表级锁定。虽然添加索引通常被认为是对 SQL 查询进行性能调优的方法，但对于内存表，你需要考虑内存表的大小、维护索引的成本以及索引的类型。对于
