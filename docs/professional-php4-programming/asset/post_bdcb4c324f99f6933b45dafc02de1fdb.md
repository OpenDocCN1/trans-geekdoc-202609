
- or DROP PRIMARY KEY
- or DROP INDEX index_name
- or RENAME [TO] new_tbl_name
- or ORDER BY col
- or table_options

ALTER TABLE allows you to change the structure of a table. For example, to add a column to the details table, the statement would be:

```
mysql> ALTER TABLE details ADD COLUMN pages INT (11) UNSIGNED AFTER price;
Query OK, 0 rows affected (0.01 sec)
Records: 0 Duplicates: 0 Warnings: 0

mysql> DESCRIBE details;
+-------+-------------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| ISBN | varchar(13) | | | PRI | | |
| price | float | YES | | NULL | | |
| pages | int(11) unsigned | YES | | NULL | | |
| num_of_books | int(11) unsigned | | | 0 | | |
| num_booked | int(11) unsigned | | | 0 | | |
| series_ID | int(11) | | | 0 | | |
+-------+-------------+------+-----+---------+-------+
6 rows in set (0.00 sec)
```

Dropping a column is even easier:

```
mysql> ALTER TABLE details DROP COLUMN pages;
Query OK, 0 rows affected (0.01 sec)
Records: 0 Duplicates: 0 Warnings: 0
```

## DROP TABLE

```
DROP TABLE table_name [, table_name, ...];
```

This statement eliminates tables (including their data) from the database. If we wished to remove two tables named Formats and TimeZones:

```
mysql> DROP TABLE Formats, TimeZones;
Query OK, 0 rows affected (0.01 sec)
```

MySQL has a handy extension to the DROP TABLE syntax. You can request a table be dropped only if it already exists using the following command:

```
mysql> DROP TABLE IF EXISTS Formats;
Query OK, 0 rows affected (0.01 sec)
```

This is useful for writing SQL scripts that re-initialize an existing database by combining the above command with a CREATE TABLE block.

## DROP DATABASE

```
DROP DATABASE database_name;
```

This statement eliminates an entire database, including all tables, indices, and data. For example, to drop the database, Library:

```
mysql> DROP DATABASE Library;
Query OK, 0 rows affected (0.01 sec)
```

## Data Manipulation and Retrieval Statements

These statements are used to get at your data in the database, as well as manipulate it.

## INSERT

```
INSERT [LOW_PRIORITY | DELAYED] [IGNORE]
[INTO] tbl_name [(col_name,...)]
VALUES (expression,...),(....),....
```

or

```
INSERT [LOW_PRIORITY | DELAYED] [IGNORE]
[INTO] tbl_name [(col_name,...)]
SELECT ...
```

or

```
INSERT [LOW_PRIORITY | DELAYED] [IGNORE]
[INTO] tbl_name
SET col_name=expression, col_name=expression, ...
```

INSERT is used to add records to a table:

```
mysql> INSERT INTO title
VALUES ('1861005156', 'Beginning Databases with PostgreSQL');
Query OK, 1 row affected (0.00 sec)
```

Note that the character strings in the above example are quoted using single quotes (apostrophes). The SQL standard dictates that character values must always be quoted in this manner. Numeric types and the special keyword NULL are not quoted.

If you attempt to insert a new entry that contains the same primary key value as an existing entry, the insertion attempt will fail.

## REPLACE

```
REPLACE [LOW_PRIORITY | DELAYED] [IGNORE]
[INTO] tbl_name [(col_name,...)]
VALUES (expression,...),(....),....
```

```
REPLACE [LOW_PRIORITY | DELAYED] [IGNORE]
[INTO] tbl_name [(col_name,...)]
SELECT ...
```

```
REPLACE [LOW_PRIORITY | DELAYED] [IGNORE]
[INTO] tbl_name
SET col_name=expression, col_name=expression, ...
```

REPLACE differs from INSERT in only one way – it first checks the old records in the table to determine whether a record already exists with the same primary or other unique key as the new record. If a match is found, the new record replaces the old record. If it does not find a match, then the new record is simply inserted.

Here, REPLACE behaves exactly like INSERT, since we do not already have a record with the value 1861003730 as the primary key:

```
mysql> REPLACE INTO title
VALUES ('1861003730', 'Beginning PHP4');
Query OK, 1 row affected (0.00 sec)
```

Here, REPLACE finds that there already is a record whose primary key is 1861003730, so it replaces the old record with the new:

```
mysql> REPLACE INTO title
VALUES ('1861003730', 'Some Other Title');
Query OK, 1 row affected (0.00 sec)
```

REPLACE is vendor-specific and may not exist in all RDBMSs. The use of vendor specific SQL extensions that are not part of the ANSI SQL standard can make an application faster, simpler, and more powerful.

Unfortunately, straying from the standard also has its disadvantages – it binds the application to a specific RDBMS. For example, to port an application from MySQL to Oracle or DB2, those non-standard features that initially saved us so much time will now cause headaches. We'll discuss these issues further in the Database Abstraction section later in the chapter.

## DELETE

```
DELETE [LOW_PRIORITY] FROM tbl_name
[WHERE where_definition]
[LIMIT rows]
```

DELETE is used to remove records from a table. The WHERE clause is an important component of DELETE, UPDATE, and SELECT queries. It allows us to specify conditions that determine which records the query will affect. This query will only delete records that have a value of 1861003730 in the ISBN field:

```
mysql> DELETE FROM title WHERE ISBN = '1861003730';
Query OK, 1 row affected (0.00 sec)
```

> If you omit the WHERE clause from a DELETE statement, every record in the table will be deleted (unless you restrict the SQL statement with LIMIT).

## UPDATE

```
UPDATE [LOW_PRIORITY] [IGNORE] tbl_name
SET col_name1=expr1, [col_name2=expr2, ...]
[WHERE where_definition]
[ORDER BY ...]
[LIMIT ]
```

UPDATE is used to change the data in existing records in the database. Previously, we used the REPLACE statement to change a book's title. With a REPLACE statement, however, a complete set of values must be provided for the row. Changing the value of a single field is more commonly accomplished with UPDATE:

```
mysql> UPDATE title
SET book_title='A New Title'
WHERE ISBN='1861003730';
Query OK, 1 row affected (0.00 sec)
Rows matched: 1 Changed: 1 Warnings: 0
```

It is important to specify the WHERE condition carefully. The query above only affected one row, but it has the potential to change many rows if more than one record has the same ISBN. It is impossible in this particular example because ISBN is a primary key.

> If you omit the WHERE clause from an UPDATE statement, every record in the table will be updated (unless you restrict the SQL statement with LIMIT).

## SELECT

```
SELECT [STRAIGHT_JOIN] [SQL_SMALL_RESULT] [SQL_BIG_RESULT]
[SQL_BUFFER_RESULT] [HIGH_PRIORITY]
[DISTINCT | DISTINCTROW | ALL]
select_expression,...
[INTO {OUTFILE | DUMPFILE} 'file_name' export_options]
[FROM table_references
[WHERE where_definition]
[GROUP BY {unsigned_integer | col_name | formula} [ASC | DESC], ...]
[HAVING where_definition]
[ORDER BY {unsigned_integer | col_name | formula} [ASC | DESC] , ...]
[LIMIT [offset,] rows]
[PROCEDURE procedure_name]
]
```

SELECT is used to retrieve rows of data from one or more tables. It is possible for these queries to become rather complex; but we will start simply. The select_expression may contain a list of fields to be selected:

```
mysql> SELECT ISBN, price FROM details;
+---------+--------+
| ISBN    | price  |
+---------+--------+
| 1861003730 | 39.95 |
| 1861005156 | 39.95 |
| 1861005083 | 29.95 |
| 1861002092 | 49.95 |
| 1861005334 | 24.95 |
+---------+--------+
5 rows in set (0.09 sec)
```

To indicate "all fields", use an asterisk (*):

```
mysql> SELECT * FROM details;
+---------+--------+-------------+------------+-----------+
| ISBN    | price  | num_of_books | num_booked | series_ID |
+---------+--------+-------------+------------+-----------+
| 1861003730 | 39.95 | 10          | 10         | 1         |
| 1861005156 | 39.95 | 10          | 10         | 1         |
| 1861005083 | 29.95 | 10          | 10         | 1         |
| 1861002092 | 49.95 | 10          | 10         | 1         |
| 1861005334 | 24.95 | 10          | 10         | 1         |
+---------+--------+-------------+------------+-----------+
5 rows in set (0.01 sec)
```

The LIMIT clause enables you to restrict the number of records returned. This can be especially useful for search functionality. LIMIT is specific to MySQL. Other RDBMSs, such as Sybase and Microsoft SQL Server, use TOP or some other syntax to achieve similar results. To restrict our results to records 2 through 4, we set the offset to 1 and rows to 3:

```
mysql> SELECT ISBN, price FROM details LIMIT 1, 3;
+---------+--------+
| ISBN    | price  |
+---------+--------+
| 1861005156 | 39.95 |
| 1861005083 | 29.95 |
| 1861002092 | 49.95 |
+---------+--------+
3 rows in set (0.00 sec)
```

The WHERE clause is used the same way in SELECT statements as it is in DELETE and UPDATE statements. To select only the records that have a price value greater than or equal to 39.95, we specify a condition:
