# # DROP DATABASE

```
DROP DATABASE database_name;
```

This statement eliminates an entire database, including all tables, indices, and data. For example, to drop the database, Library:

```
mysql> DROP DATABASE Library;
Query OK, 0 rows affected (0.01 sec)
```

# # Data Manipulation and Retrieval Statements

These statements are used to get at your data in the database, as well as manipulate it.

# # INSERT

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
VALUES (’1861005156’, ’Beginning Databases with PostgreSQL’);
Query OK, 1 row affected (0.00 sec)
```

Note that the character strings in the above example are quoted using single quotes (apostrophes). The SQL standard dictates that character values must always be quoted in this manner. Numeric types and the special keyword NULL are not quoted.

If you attempt to insert a new entry that contains the same primary key value as an existing entry, the insertion attempt will fail.

# # REPLACE

```
REPLACE [LOW_PRIORITY | DELAYED] [IGNORE]
[INTO] tbl_name [(col_name,...)]
VALUES (expression,...),(....),....
```