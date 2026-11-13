+   ORDER BY col_name

Lets you sort the entries in a table by a particular column. This is not a persistent state, however: as soon as new entries are added to the table, or existing entries modified, the ordering can no longer be guaranteed. The only practical use of this action would be to increase performance of a table that you regularly sorted in a certain way in your application's SELECT queries. Under some circumstances, arranging the rows in (almost) the right order to begin with will make sorting quicker.

+   table_options

Using the same syntax as in the CREATE TABLE query, this action allows you to set and change advanced table options. These options are fully documented in the MySQL Reference manual.

# ANALYZE TABLE

```
ANALYZE TABLE tbl_name[, tbl_name, ...]
```

This function updates information that's used by the SELECT query in the optimization of queries that take advantage of table indices. It pays in performance to periodically run this query on tables whose contents change a lot over time. The table(s) in question are locked “read-only” while the analysis runs.

# CREATE DATABASE

```
CREATE DATABASE [IF NOT EXISTS] db_name
```

This action simply creates a new database with the given name (db_name). This query will fail if the database already exists (unless IF NOT EXISTS is specified), or if you don't have the required privileges.

# CREATE INDEX

```
CREATE [UNIQUE | FULLTEXT] INDEX index_name ON tbl_name (col_name[(length)], ...)
```