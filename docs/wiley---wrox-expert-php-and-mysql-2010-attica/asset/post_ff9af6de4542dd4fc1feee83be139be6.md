
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

You see from this example that the total disk footprint of the InnoDB table is an increase of 70 percent over MyISAM; however, the index portion is 100 percent larger. When you introduce an AUTO_INCREMENT primary key as shown in Listing 3-8 you see a reduction in disk footprint of the data portion by 10 percent. You also see a 5 percent reduction in index space, but you have indeed added an additional index to simulate the primary key.

## LISTING 3-8: wide-innodb-with-pk.sql

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

As you start to add additional indexes you get to see a greater difference. Using the MyISAM index data as a control test, the InnoDB table with the same structure is 100 percent larger, whereas the InnoDB table with the AUTO_INCREMENT primary key is only 80 percent larger. Although these tables are small, you can see the impact of a single column change.

| table_name | table_rows | row_format | data | indx |
|---|---|---|---|---|
| wide_innodb | 239154 | Compact | 21056.0000 | 67408.0000 |
| wide_innodb_with_pk | 235054 | Compact | 22064.0000 | 59488.0000 |
| wide_myisam | 234936 | Dynamic | 16003.9023 | 32535.0000 |

Applications that use SELECT COUNT(*) FROM TABLE when using MyISAM will find an instant response, whereas for InnoDB this must be calculated by reading the data. For large tables this can cause a high performance impact as disk I/O, and flushing of data from the internal buffer pool affects other online operations significantly. Using an index to retrieve a portion of rows to perform a COUNT(*) is the necessary alteration to overcome a full table scan for your application.

In smaller MySQL environments you can find the use of the FULLTEXT index for text searching. This type of index is only supported in MyISAM. In this situation is it generally the approach to duplicate the columns in a second table that remains a MyISAM table. This generally gives you all the features of InnoDB, as well as the FULLTEXT feature of MyISAM. There are data integrity, performance, and disaster recovery impacts with this approach. Care should always be taken with important design considerations to realize the total impact for your entire system.

## Optimizing SQL Using InnoDB

The final point for discussion about InnoDB is that of SQL optimizations. Internally MySQL parses a SQL query and then determines via a cost-based optimizer the best means of satisfying the query in the quickest time. The optimizer uses information about table indexes and the statistics of column distribution to determine the best execution path. MySQL by default uses only one index per table in an SQL query (with a few minor exceptions). When joining multiple tables, especially intersection tables, only one index is used. When converting a table from MyISAM to InnoDB, you cannot assume the same indexes will be used when your query is executed. It is important that you review the Query Execution Plan (QEP) via the EXPLAIN syntax. Two differences that affect how data is stored and retrieved have already been discussed. With InnoDB data is now in primary key order, and this provides for sequential reading of data when using a primary key. The second point is that the value
of the primary key is stored in a secondary index, allowing for this value to be used in some situations as if it were a second indexed column of the index.

As with any changes in your application it is important that you test these changes under realistic production conditions. Converting tables from `MyISAM` to `InnoDB` while changing application functionality can result in worse performance when the MySQL environment is not tuned appropriately, or particular situations including those discussed are not understood and considered as impacts.

## Memory

The `Memory` storage engine, also known historically as the `Heap` storage engine, is an in-memory only table that does not provide data persistence. The `Memory` storage engine is actually used internally by the mysql kernel when a temporary table is required.

### Key Features
- Very fast, in memory
- Non-transactional
- Supports the hash index by default
- Btree indexes also supported
- Ideal for primary key lookups

### Limitations
- Does not support transactions
- Table level locking on DML and DDL statements
- Data not persistent
- Does not support TEXT/BLOB data types
- Fixed row width
- No ability to limit the total amount of memory for all `Memory` tables

### Important Parameters
- `max_heap_table_size`: Defines the maximum size of a single `Memory` table.
- `tmp_table_size`: Defines the maximum size of the table when used for internally temporary tables.
- `init_file`: Defines a SQL file of commands that are executed when the MySQL instance is started. Used as a means to seed `Memory` tables.

### Example Table Usage

The syntax for creating a `Memory` table (as shown in Listing 3-9) is identical to previous examples.

## LISTING 3-9: memory-example.sql

```
CREATE TABLE example_memory(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
    c VARCHAR(100) NOT NULL)
ENGINE=Memory;
```

Memory tables are confined to a maximum table size as defined by the max_heap_table_size system variable. Listing 3-10 demonstrates the table full error message, and corrects the maximum size, based on the size of the comparison Fixed MyISAM table size to show the data in a Memory table.

## LISTING 3-10: memory-load.sql

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

When using large memory tables, a consideration is table-level locking. While adding an index is generally considered a method for performance tuning SQL queries, with memory tables you need to factor the size of the memory table, the cost of maintaining the index, and the type of index. For
