# 436 Part V: Appendixes

This created two files, problems.sql and problems.txt. To reload the problems table from these files, you could do as:

```
mysql tracking <problems.sql
mysqlimport tracking problems.txt
```

Some of the most common or useful command-line options are shown in Table C-11.

# Table C-11 MYSQLIMPORT COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -? | --help | Display a help message and exit. |
| -d | --delete | Empty the table before importing the text file. |
| --fields-terminated-by=... | | These options have the same meaning as the corresponding clauses for 'LOAD DATA INFILE': |
| --fields-enclosed-by=... | | |
| --fields-optionally-enclosed-by=... | | |
| --fields-escaped-by=... | | |
| --lines-terminated-by=... | | |
| -f | --force | Ignore errors. For example, if a table for a text file doesn't exist, continue processing any remaining files. Without '--force', mysqlimport exits if a table doesn't exist. |
| -h host_name | --host=host_name | Import data to the MySQL server on the named host. The default host is 'localhost'. |
| -l | --lock-tables | Lock all tables for writing processing any text files. ensures that all tables are synchronized on the server. |
| -L | --local | Read input files from the client. By default, text files are assumed to be on the server if you connect to 'localhost' (the default host). |