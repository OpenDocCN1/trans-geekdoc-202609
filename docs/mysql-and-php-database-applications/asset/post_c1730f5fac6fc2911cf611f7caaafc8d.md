
| Flag | Alternate Flag | Description |
|---|---|--|
| --add-drop-table | | Add a DROP TABLE IF EXISTS statement before CREATE TABLE statement. |
| --allow-keywords | | Allow creation of column names that are keywords.This option works by prefixing each column name with the table name. |
| -c | --complete-insert | Use complete insert statements (with column names). |
| --delayed | | Insert rows with the INSERT DELAYED command. |
| -F | --flush-logs | Flush log file in the MySQL server before starting the dump. |
| -f | --force | Continue even if you get a SQL error during a table dump. |
| -h | --host.. | Dump data from the MySQL server on the named host. The default host is localhost. |
| -l | --lock-tables | Lock all tables before starting the dump. |
| -t | --no-create-info | Don't write table creation info. |
| -d | --no-data | Don't write any row information for the table. |
| --opt | | Same as --quick --add-drop-table --add-locks-extended-insert --lock-tables. Should give you the fastest dump for reading into a MySQL server. |
| -p[...] | --password[...] | Password to use when connecting to server. If password is not given on the command line, you will be prompted for it. Note that if you use the short form '-p' you can't have a space between the option and the password. |
| -P | --port=port_num | The TCP/IP port number to use for connecting to a host. |

# Appendix C: MySQL Utilities 433

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -q | --quick | Don't buffer query, dump directly to stdout. |
| -T path-to-some-directory | --tab-to-some-directory | For each table, creates a table_name.sql file containing the SQL CREATE commands, and a table_name.txt file containing the data from the table. |

Here's an example of the -T flag on a Unix installation:

```
mysqldump -T tracking problems
```

This will create two files in the current directory (that's what it means): 'problems.sql and 'problems.txt'. 'problems.sql will have the SQL statements to create the 'problems' table. 'problems.txt' is a tab-delimited (the default format) copy of the data now in the 'problems' table in the 'tracking' database.

> This only works if mysqldump is run on the same machine as the mysqld daemon. The format of the .txt file is made according to the --fields-xxx and --lines-xxx options.

![](img/245156cc770929860a3ede93c01f9981_459_0.png)

Table C-9 lists more mysqldump command-line options.

# Table C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| --fields-terminated-by=... | | These options have the same meaning as the corresponding clauses for the LOAD DATA INFILE statement. |
| --fields-enclosed-by=... | | |
| --fields-optionally-enclosed-by=... | | |
| --fields-escaped-by=... | | |
| --lines-terminated-by=... | | |

Continued

# 434 Part V: Appendixes

# **TABLE C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS (Continued)**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -u user_name, | --user=user_name | The MySQL user name to use when connecting to the server. |
| -w | --where='where-condition' | Dump only selected records; Note that QUOTES are mandatory! <br><br>Example:<br>--where='user=*jim*' <br>--w='userid>1*' <br>--w='userid<1*' |

Table C-10 displays the mysqldump command line options that are new to version 3.23.

# **TABLE C-10 MYSQLDUMP COMMAND-LINE OPTIONS NEW IN VERSION 3.23**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -A | --all-databases | Dump all the databases. This is the same as --databases with all databases selected. |
| -B | --databases | Dump several databases. Note the difference in usage; in this case no tables are given. All name arguments are regarded as database names. Use db_name; will be included in the output before each new database. |
| -e | --extended-insert | Use the new multiline INSERT syntax. |

# Appendix C: MySQL Utilities 435

| Flag | Alternate Flag | Description |
|---|---|---|
| -n | --no-create | |
| --create-info | | Don't dump table structure. |
| --data | --no-data | Don't dump data. |
| --quick | | Use dump row-by-row instead of buffering entire table in memory. |
| --master-data | | Dump binary log information for master server. |
| --routines | | Dump stored procedures and functions. |
| --triggers | | Dump triggers. |
| --extended-insert | | Use extended insert syntax. |
| --single-transaction | | Dump each table in a single transaction. |
| --hex-blob | | Dump binary columns as hex strings. |
| --skip-insert | | Do not include INSERT statements. |
| --skip-comments | | Do not include comments. |
| --skip-create-db | | Do not include CREATE DATABASE. |
| --skip-create-info | | Do not include CREATE TABLE. |
| --skip-triggers | | Do not include triggers. |
| --skip-events | | Do not include events. |
| --set-charset= | Use a specific character set. |
| --set-client-character= | Use a specific client character set. |
| --set-server-character= | Use a specific server character set. |
| --default-character-set= | Set the default character set. |
| --result-file= | | Output results to a file. |
| --error= | | Output errors to a file. |
| --log= | | Output log to a file. |
| --add-drop-table | | Add a DROP TABLE IF EXISTS statement before CREATE TABLE statement. |
| --add-createlock | | Add DELETE statements for each table. |
| --add-locks | | Add LOCK TABLE statements before each INSERT. |
| --add-locks-extended-insert | | Use extended insert with LOCK TABLE. |
| --allow-keywords | | Allow creation of column names that are keywords.This option works by prefixing each column name with the table name. |
| -c | --complete-insert | Use complete insert statements (with column names). |
| --delayed | | Insert rows with the INSERT DELAYED command. |
| -F | --flush-logs | Flush log file in the MySQL server before starting the dump. |
| -f | --force | Continue even if you get a SQL error during a table dump. |
| -h | --host.. | Dump data from the MySQL server on the named host. The default host is localhost. |
| -l | --lock-tables | Lock all tables before starting the dump. |
| -t | --no-create-info | Don't write table creation info. |
| -d | --no-data | Don't write any row information for the table. |
| --opt | | Same as --quick --add-drop-table --add-locks-extended-insert --lock-tables. Should give you the fastest dump for reading into a MySQL server. |
| -p[...] | --password[...] | Password to use when connecting to server. If password is not given on the command line, you will be prompted for it. Note that if you use the short form '-p' you can't have a space between the option and the password. |
| -P | --port=port_num | The TCP/IP port number to use for connecting to a host. |

# Appendix C: MySQL Utilities 433

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -q | --quick | Don't buffer query, dump directly to stdout. |
| -T path-to-some-directory | --tab-path-to-some-directory | For each table, creates a table_name.sql file containing the SQL CREATE commands, and a table_name.txt file containing the data from the table. |

Here's an example of the -T flag on a Unix installation:

```
mysqldump -T tracking problems
```

This will create two files in the current directory (that's what it means): 'problems.sql and 'problems.txt'. 'problems.sql will have the SQL statements to create the 'problems' table. 'problems.txt' is a tab-delimited (the default format) copy of the data now in the 'problems' table in the 'tracking' database.

> This only works if mysqldump is run on the same machine as the mysqld daemon. The format of the .txt file is made according to the --fields-xxx and --lines-xxx options.

![](img/245156cc770929860a3ede93c01f9981_459_0.png)

Table C-9 lists more mysqldump command-line options.

# Table C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| --fields-terminated-by=... | | These options have the same meaning as the corresponding clauses for the LOAD DATA INFILE statement. |
| --fields-enclosed-by=... | | |
| --fields-optionally-enclosed-by=... | | |
| --fields-escaped-by=... | | |
| --lines-terminated-by=... | | | |

Continued

# 434 Part V: Appendixes

# **TABLE C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS (Continued)**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -u user_name, | --user=user_name | The MySQL user name to use when connecting to the server. |
| -w | --where='where-condition' | Dump only selected records; Note that QUOTES are mandatory! <br><br>Example:<br>--where='user=*jim*' <br>--w='userid>1*' <br>--w='userid<1*' |

Table C-10 displays the mysqldump command line options that are new to version 3.23.

# **TABLE C-10 MYSQLDUMP COMMAND-LINE OPTIONS NEW IN VERSION 3.23**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -A | --all-databases | Dump all the databases. This is the same as --databases with all databases selected. |
| -B | --databases | Dump several databases. Note the difference in usage; in this case no tables are given. All name arguments are regarded as database names. Use db_name; will be included in the output before each new database. |
| -e | --extended-insert | Use the new multiline INSERT syntax. |

# Appendix C: MySQL Utilities 435

mysqldump is a client program used for logical backups of MySQL databases. It creates a file containing SQL statements to recreate the database structure and data, which can be executed to restore the database or any of it.

The mysqldump command has many options.

The --ignore --replace options control handling of input records that duplicate existing records on unique key values. If you specify --replace replace existing rows that have the same unique key value. If you specify --ignore, rows that duplicate an existing row on a unique key value are skipped. If you don't specify either, an error occurs when a duplicate key value is found, and the rest of the text is ignored.

Syntax for mysqldump is:

```
mysqldump [options] db_name [table_name ...]
```

The [options] part can include any of the options listed below. The db_name is the name of the database to dump, and [table_name ...] are the optional names of specific tables within that database. If no tables are specified, all tables in the database are dumped.

Some of the most common options:

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -q | --quick | Don't buffer query, dump directly to stdout. |
| -T path-to-some-directory | --tab-path-to-some-directory | For each table, creates a table_name.sql file containing the SQL CREATE commands, and a table_name.txt file containing the data from the table.

Here's an example of the -T flag on a Unix installation:

```
mysqldump -T tracking problems
```

This will create two files in the current directory (that's what it means): 'problems.sql and 'problems.txt'. 'problems.sql will have the SQL statements to create the 'problems' table. 'problems.txt' is a tab-delimited (the default format) copy of the data now in the 'problems' table in the 'tracking' database.

> This only works if mysqldump is run on the same machine as the mysqld daemon. The format of the .txt file is made according to the --fields-xxx and --lines-xxx options.

![](img/245156cc770929860a3ede93c01f9981_459_0.png)

Table C-9 lists more mysqldump command-line options.

# Table C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| --fields-terminated-by=... | | These options have the same meaning as the corresponding clauses for the LOAD DATA INFILE statement. |
| --fields-enclosed-by=... | | |
| --fields-optionally-enclosed-by=... | | |
| --fields-escaped-by=... | | |
| --lines-terminated-by=... | | | |

Continued

# 434 Part V: Appendixes

# **TABLE C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS (Continued)**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -u user_name, | --user=user_name | The MySQL user name to use when connecting to the server. |
| -w | --where='where-condition' | Dump only selected records; Note that QUOTES are mandatory! <br><br>Example:<br>--where='user=*jim*' <br>--w='userid>1*' <br>--w='userid<1*' |

Table C-10 displays the mysqldump command line options that are new to version 3.23.

# **TABLE C-10 MYSQLDUMP COMMAND-LINE OPTIONS NEW IN VERSION 3.23**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -A | --all-databases | Dump all the databases. This is the same as --databases with all databases selected. |
| -B | --databases | Dump several databases. Note the difference in usage; in this case no tables are given. All name arguments are regarded as database names. Use db_name; will be included in the output before each new database. |
| -e | --extended-insert | Use the new multiline INSERT syntax. |

mysqldump is a client program used for logical backups of MySQL databases. It creates a file containing SQL statements to recreate the database structure and data, which can be executed to restore the database or any of it.

The mysqldump command has many options.

The --ignore --replace options control handling of input records that duplicate existing records on unique key values. If you specify --replace replace existing rows that have the same unique key value. If you specify --ignore, rows that duplicate an existing row on a unique key value are skipped. If you don't specify either, an error occurs when a duplicate key value is found, and the rest of the text is ignored.

Syntax for mysqldump is:

```
mysqldump [options] db_name [table_name ...]
```

The [options] part can include any of the options listed below. The db_name is the name of the database to dump, and [table_name ...] are the optional names of specific tables within that database. If no tables are specified, all tables in the database are dumped.

Some of the most common options:

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -q | --quick | Don't buffer query, dump directly to stdout. |
| -T path-to-some-directory | --tab-path-to-some-directory | For each table, creates a table_name.sql file containing the SQL CREATE commands, and a table_name.txt file containing the data from the table. |

Here's an example of the -T flag on a Unix installation:

```
mysqldump -T tracking problems
```

This will create two files in the current directory (that's what it means): 'problems.sql and 'problems.txt'. 'problems.sql will have the SQL statements to create the 'problems' table. 'problems.txt' is a tab-delimited (the default format) copy of the data now in the 'problems' table in the 'tracking' database.

> This only works if mysqldump is run on the same machine as the mysqld daemon. The format of the .txt file is made according to the --fields-xxx and --lines-xxx options.

![](img/245156cc770929860a3ede93c01f9981_459_0.png)

Table C-9 lists more mysqldump command-line options.

# Table C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| --fields-terminated-by=... | | These options have the same meaning as the corresponding clauses for the LOAD DATA INFILE statement. |
| --fields-enclosed-by=... | | | |
| --fields-optionally-enclosed-by=... | | | |
| --fields-escaped-by=... | | | |
| --lines-terminated-by=... | | | |

mysqldump is a client program used for logical backups of MySQL databases. It creates a file containing SQL statements to recreate the database structure and data, which can be executed to restore the database or any of it.

The mysqldump command has many options.

The --ignore --replace options control handling of input records that duplicate existing records on unique key values. If you specify --replace replace existing rows that have the same unique key value. If you specify --ignore, rows that duplicate an existing row on a unique key value are skipped. If you don't specify either, an error occurs when a duplicate key value is found, and the rest of the text is ignored.

Syntax for mysqldump is:

```
mysqldump [options] db_name [table_name ...]
```

The [options] part can include any of the options listed below. The db_name is the name of the database to dump, and [table_name ...] are the optional names of specific tables within that database. If no tables are specified, all tables in the database are dumped.

Some of the most common options:

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -q | --quick | Don't buffer query, dump directly to stdout. |
| -T path-to-some-directory | --tab-path-to-some-directory | For each table, creates a table_name.sql file containing the SQL CREATE commands, and a table_name.txt file containing the data from the table. |

Here's an example of the -T flag on a Unix installation:

```
mysqldump -T tracking problems
```

This will create two files in the current directory (that's what it means): 'problems.sql and 'problems.txt'. 'problems.sql will have the SQL statements to create the 'problems' table. 'problems.txt' is a tab-delimited (the default format) copy of the data now in the 'problems' table in the 'tracking' database.

> This only works if mysqldump is run on the same machine as the mysqld daemon. The format of the .txt file is made according to the --fields-xxx and --lines-xxx options.

![](img/245156cc770929860a3ede93c01f9981_459_0.png)

Table C-9 lists more mysqldump command-line options.

# Table C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| --fields-terminated-by=... | | These options have the same meaning as the corresponding clauses for the LOAD DATA INFILE statement. |
| --fields-enclosed-by=... | | | |
| --fields-optionally-enclosed-by=... | | | |
| --fields-escaped-by=... | | | |
| --lines-terminated-by=... | | | |
