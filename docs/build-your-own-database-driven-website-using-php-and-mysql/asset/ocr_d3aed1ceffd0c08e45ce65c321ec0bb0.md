DISTINCTROW (they have the same effect) specify that duplicate rows should be eliminated from the result set.

select_expression defines a column of the result set to be returned by the query. Typically, this is a table column name, and may be specified as col_name, tbl_name.col_name, or db_name.tbl_name.col_name, depending on how specific you need to be for MySQL to know which particular column you are referring to. select_expressions need not refer to a database column - a simple mathematical formula such as 1 + 1 or a complex expression calculated with MySQL functions may also be used. Here's an example of the latter, which will give the date one month from now in the form "January 1st, 2002":

```
SELECT DATE_FORMAT(DATE_ADD(CURDATE(), INTERVAL 1 MONTH), '%M %D, %Y')
```

select_expressions may also contain an alias, or assigned name for the result column if the expression is followed with [AS] alias (the AS is entirely optional). This expression must be used when referring to that column elsewhere in the query (e.g. in WHERE and ORDER BY clauses), as follows:

```
SELECT JokeDate AS JD FROM Jokes ORDER BY JD ASC
```

MySQL lets you use an INTO clause to output the results of a query into a file instead of returning them to the client. The most typical use of this is to export the contents of a table into a text file containing comma-separated values (CSV). Here's an example:

```
SELECT * INTO OUTFILE "/home/user/myTable.txt"
FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
LINES TERMINATED BY "\n"
FROM mytable
```

The file to which the results are dumped must not exist beforehand, or this query will fail. This prevents an SQL query from being used to overwrite critical operating system files. The created file will also be world-readable on systems that support file security, so consider this before you export sensitive data to a text file that anyone on the system can read.

DUMPFILE may be used instead of OUTFILE to write to the file only a single row, without row or column delimiters. This can be used, for example, to dump a BLOB stored in the table to a file (SELECT blobCol INTO DUMPFILE ...).

For complete information on the INTO clause, see the MySQL Reference Manual at http://www.mysql.com. For information on reading data back from a text file, see the LOAD DATA INFILE query on page 184.