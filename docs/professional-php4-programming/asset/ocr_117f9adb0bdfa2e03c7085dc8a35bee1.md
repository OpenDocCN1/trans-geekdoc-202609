To drop the num_booked and num_pages columns from the above details table, you would do something like this:

```
CREATE TABLE temp AS SELECT ISBN, price, num_of_books, series_ID FROM details;
DROP TABLE details;
CREATE TABLE details (
   ISBN    VARCHAR(13) PRIMARY KEY,
   price   FLOAT,
   num_of_books INT NOT NULL,
   series_ID INT NOT NULL
);
INSERT INTO details SELECT * FROM temp;
DROP TABLE temp;
```

# # DROP TABLE

```
DROP TABLE name [, ...]
```

This statement eliminates tables (including their data) from the database. If we wished to remove two tables named "formats" and "timezones":

```
library=# DROP TABLE formats, timezones;
DROP
```

# # DROP DATABASE

```
DROP DATABASE database_name
```

This statement eliminates an entire database, including all tables, indices, and data:

```
template1=# drop database library;
DROP DATABASE
```

> You should be out of the database (not logged into it) to DROP a database.

# # Data Manipulation and Retrieval Statements

These statements are used to get at your data in the database, as well as manipulate it.

# # INSERT

```
INSERT INTO table [(column [, ...])]
{DEFAULT VALUES | VALUES (expression [, ...]) | SELECT query}
```

INSERT is used to add new records to a table. Note that the character strings in the example below are quoted using single quotes. The SQL standard dictates that character values must always be quoted in this manner. Numeric types and the special keyword NULL are not quoted: