# Appendix C: MySQL Utilities 433

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -q | --quick | Don't buffer query, dump directly to stdout. |
| -T path-to-some-directory | --tab-path-to-some-directory | For each table, creates a table_name.sql file containing the SQL CREATE commands, and a table_name.txt file containing the data from the table. |

Here's an example of the -T flag on a Unix installation:

```
mysqldump -T tracking problems

This will create two files in the current directory (that's what means): 'problems.sql and 'problems.txt'. 'problems.sql will have the SQL statements to create the 'problems' table. 'problems.txt' is a tab-delimited (the default format) copy of the data now in the 'problems' table in the 'tracking' database.
```

> This only works if mysqldump is run on the same machine as the mysqld daemon. The format of the .txt file is made according to the --fields-xxx and --lines-xxx options.

![](bbox=[0.181, 0.526, 0.231, 0.574])

Table C-9 lists more mysqldump command-line options.

# Table C-9 MORE MYSQLUMP COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| --fields-terminated-by=... | | These options have the same meaning as the corresponding clauses for the LOAD DATA INFILE statement. |
| --fields-enclosed-by=... | | |
| --fields-optionally-enclosed-by=... | | |
| --fields-escaped-by=... | | |
| --lines-terminated-by=... | | |

Continued