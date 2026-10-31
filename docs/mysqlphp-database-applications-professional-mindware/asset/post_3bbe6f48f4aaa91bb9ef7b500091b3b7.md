
## TABLE C-7 MYSQLADMIN COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
|---|---|---|
| -? | --help | Display help and exit. |
| -# | --debug=... | Output debug log. Often this is d:t:o,filename. |
| -f | --force | Don't ask for confirmation on drop database; with multiple commands, continue even if an error occurs. |
| -h | --host=# | Connect to host. |
| -p[...] | --password[=...] | Password to use when connecting to server. If password is not given on the command line, you will be prompted for it. Note that if you use the short form -p you can't have a space between the option and the password. |
| -P | --port=... | Port number to use for connection. |
| -i | --sleep=sec | Execute commands again and again with a sleep between. |
| -r | --relative | Show difference between current and previous values when used with -i. Currently works only with extended-status. |
| -s | --silent | Silently exit if one can't connect to server. |
| -t | --timeout=... | Timeout for connection to the mysqld server. |
| -w | --wait[=retries] | Wait and retry if connection is down. |
| -W (Windows only) | --pipe | Use named pipes to connect to server. |
| -E | --vertical | Print output vertically. Is similar to -relative, but prints output vertically. |

## mysqldump

This is the command-line utility for dumping out schema information and data from your databases. This is what you would use to back up your database, or move it from one machine to another.

The output from mysqldump will most commonly be a script of SQL commands, to create tables and then insert data into them. mysqldump can also create plain data files (i.e., a tab-delimited file) from your tables.

Syntax:

```
mysqldump [OPTIONS] database [tables]
```

or, as of 3.23:

```
mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
mysqldump [OPTIONS] --all-databases [OPTIONS]
```

A typical use of mysqldump would look like this:

```
mysqldump --opt mydatabase > backup-file.sql
```

You can read this back into MySQL with the mysql command-line tool:

```
mysql mydatabase < backup-file.sql
```

or, as of 3.23:

```
mysql -e "source /path-to-backup/backup-file.sql" mydatabase
```

You could also use it to copy data from one MySQL server to another:

```
mysqldump --opt mydatabase | mysql --host=remote-host mydatabase
```

Table C-8 lists the command-line options:

## TABLE C-8 MYSQLDUMP COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
|---|---|---|
| -? | --help | Display this help message and exit. |
| -a | --all | Include all MySQL specific create options. |
| --add-locks |  | Add LOCK TABLES before and UNLOCK TABLE after each table dump (to get faster inserts into MySQL). |

Continued

## TABLE C-8 MYSQLDUMP COMMAND-LINE OPTIONS (Continued)

| Flag | Alternate Flag | Description |
|---|---|---|
| --add-drop-table |  | Add a DROP TABLE IF EXISTS statement before each CREATE TABLE statement. |
| --allow-keywords |  | Allow creation of column names that are keywords. This option works by prefixing each column name with the table name. |
| -c | --complete-insert | Use complete insert statements (with column names). |
| --delayed |  | Insert rows with the INSERT DELAYED command. |
| -F | --flush-logs | Flush log file in the MySQL server before starting the dump. |
| -f | --force | Continue even if you get a SQL error during a table dump. |
| -h | --host=.. | Dump data from the MySQL server on the named host. The default host is localhost. |
| -l | --lock-tables | Lock all tables before starting the dump. |
| -t | --no-create-info | Don't write table creation info. |
| -d | --no-data | Don't write any row information for the table. |
| --opt |  | Same as --quick --add-drop-table --add-locks --extended-insert --lock-tables. Should give you the fastest possible dump for reading into a MySQL server. |
| -p[...] | --password[=...] | Password to use when connecting to server. If password is not given on the command line, you will be prompted for it. Note that if you use the short form `-p` you can't have a space between the option and the password. |
| -P | --port=port_num | The TCP/IP port number to use for connecting to a host. |

| Flag | Alternate Flag | Description |
|---|---|---|
| -q | --quick | Don't buffer query, dump directly to stdout. |
| -T path-to-some-directory, | --tab=path-to-some-directory | For each table, creates a table_name.sql file containing the SQL CREATE commands, and a table_name.txt file containing the data from the table. |

Here's an example of the -T flag on a Unix installation:

```
mysqldump -T . tracking problems
```

This will create two files in the current directory (that's what '.' means): 'problems.sql' and 'problems.txt.' 'problems.sql' will have the SQL statements to create the 'problems' table. 'problems.txt' is a tab-delimited (the default format) copy of the data now in the 'problems' table in the 'tracking' database.

![](img/de0823012275cf4ceebdb822a56e6b71_459_0.png)

This only works if mysqldump is run on the same machine as the mysqld daemon. The format of the .txt file is made according to the --fields-xxx and --lines-xxx options.

Table C-9 lists more mysqldump command-line options.

## TABLE C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
|---|---|---|
| --fields-terminated-by=... |  | These options have the same meaning as the corresponding clauses for the LOAD DATA INFILE statement. |
| --fields-enclosed-by=... |  |  |
| --fields-optionally-enclosed-by=... |  |  |
| --fields-escaped-by=... |  |  |
| --lines-terminated-by=... |  |  |

Continued

## TABLE C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS (Continued)

| Flag | Alternate Flag | Description |
|------|----------------|-------------|
| `-u user_name` | `--user=user_name` | The MySQL user name to use when connecting to the server. |
| `-w` | `--where='where-condition'` | Dump only selected records; Note that QUOTES are mandatory! Example: `--where=user='jimf'` `"-wuserid>1"` `"-wuserid<1"` |

Table C-10 displays the mysqldump command line options that are new to version 3.23.

## TABLE C-10 MYSQLDUMP COMMAND-LINE OPTIONS NEW IN VERSION 3.23

| Flag | Alternate Flag | Description |
|------|----------------|-------------|
| `-A` | `--all-databases` | Dump all the databases. This is the same as `--databases` with all databases selected. |
| `-B` | `--databases` | Dump several databases. Note the difference in usage; in this case no tables are given. All name arguments are regarded as database names. USE db_name; will be included in the output before each new database. |
| `-e` | `--extended-insert` | Use the new multiline INSERT syntax. |

| Flag | Alternate Flag | Description |
| -n | --no-create-db | 'CREATE DATABASE IF NOT EXISTS db_name;' will not be put in the output. The above line will be added otherwise, if --databases or --all-databases option was given. |
| --tables |  | Overrides option --databases (-B). |
| -O |  | net_buffer_length=#, where # < 24M When creating multi-row-insert statements (as with option --extended-insert or --opt), mysqldump will create rows up to net_buffer_length length. If you increase this variable, you should also ensure that the max_allowed_packet variable in the MySQL server is bigger than the net_buffer_length. |

## mysqlimport

The mysqlimport tool provides a command line interface to the 'LOAD DATA INFILE' SQL statement. Most options to mysqlimport correspond directly to the same options to 'LOAD DATA INFILE'.

Syntax:

```
mysqlimport [options] database textfile1 [textfile2...]
```

For each text file named on the command line, mysqlimport strips any extension from the filename and uses the result to determine which table to import the file's contents into. For example, files named patient.txt, patient.text, and patient would all be imported onto a table named patient.

You typically use mysqlimport to bring data into a MySQL database from some other source—another DBMS, a spreadsheet, or the like. You can also use it together with the mysqldump tool. Take the example I gave earlier:

```
mysqldump -T . tracking problems
```
