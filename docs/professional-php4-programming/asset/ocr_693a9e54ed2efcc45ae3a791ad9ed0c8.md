In this table, the primary key is composed of two fields – ISBN and auth_ID:

```
mysql> CREATE TABLE series (
   series_ID INT (11) NOT NULL AUTO_INCREMENT,
   book_series VARCHAR (64) NOT NULL,
   PRIMARY KEY (series_ID)
 );
Query OK, 0 rows affected (0.00 sec)
```

```
mysql> CREATE TABLE users (
   username CHAR (32) NOT NULL,
   password CHAR (32) NOT NULL,
   PRIMARY KEY (username)
 );
Query OK, 0 rows affected (0.00 sec)
```

This last table definition uses two CHAR fields instead of VARCHAR fields. VARCHAR fields are variable length character types that have a maximum length. The database only has to make room for the number of characters in the actual string stored in the field, however, so a string "ELEPHANT" will only use eight characters worth of space in the database, even though the maximum size of the VARCHAR field may be a number greater than eight. This can lead to large space savings, but there is also a slight performance penalty associated with managing variable length fields.

On the other hand, CHAR fields reserve space up to their maximum length at all times. The extra character spaces are generally padded with NULL values. While this may seem like a waste of space, it is faster for the database to access the CHAR field because it is of a known, fixed size.

> Some DBMSs like MySQL automatically upgrade CHAR fields to VARCHAR fields if the table contains any other variable-length field types. Mixing CHAR and VARCHAR fields in the same table definition will result in all character fields becoming VARCHARs.

# ALTER TABLE

```
ALTER [IGNORE] TABLE tbl_name alter_spec [, alter_spec ...]
```

The alter_spec:

```
ADD [COLUMN] create_definition [FIRST | AFTER column_name ]
or ADD [COLUMN] (create_definition, create_definition,...)
or ADD INDEX (index_name) (index_col_name,...)
or ADD PRIMARY KEY (index_col_name,...)
or ADD UNIQUE [index_name] (index_col_name,...)
or ADD FULLTEXT [index_name] (index_col_name,...)
or ADD [CONSTRAINT symbol] FOREIGN KEY index_name (index_col_name,...)
   [reference_definition]
or ALTER [COLUMN] col_name {SET DEFAULT literal | DROP DEFAULT}
or CHANGE [COLUMN] old_col_name create_definition
or MODIFY [COLUMN] create_definition
or DROP [COLUMN] col_name
```