
## TABLE 3-1 (continued)

| CHARACTERISTIC | DESCRIPTION |
|---|---|
| Queries and Results | A query on a Federated table internally produces an entire result set from a table on a remote server, and as such, if that table contains a lot of data, all of that data will be retrieved. One way to deal with huge result sets is to define an index on a column of the Federated table, even if that column is not indexed on the remote table, and try to use any means to limit the result set. However, note that `LIMIT` does not affect the size of the result set from the remote table. |
| Remote Table | The remote table must be in existence prior to creating the Federated table that references it. |
| Index Support | The Federated storage engine supports indexes insofar as the column that is defined as an index is specified in a `WHERE` clause in the SQL query the table generates, and that the column it specifies is an index on the remote table. This means that you could have a Federated table with an index on a column that is not an index on the remote table, which is not a problem, and in fact can be used to reduce result set size. |
| Referencing Another Federated Table | The manual states a Federated table can reference a Federated table. This is a bad idea. Don't do it. |
| Transactions | Transactions aren't supported in Federated, but are supported with FederatedX if using a transactional engine (InnoDB, MariaDB, Falcon, and so on) as the remote data source. |
| What Federated Supports | Federated supports `SELECT`, `INSERT`, `UPDATE`, and `DELETE`. However, `ALTER TABLE` cannot be used to change the remote table's definition (this would violate the very definition of a Federated table), but it can be used to modify the local Federated table's definition. |
| Using `DROP TABLE` | This only drops the local Federated table. |

It's worthwhile to mention that although the Federated storage engine may not support some features such as transactions as well as other enhancements, there is a fork of Federated called FederatedX, which is a more active development branch of Federated initiated by the authors of Federated: Patrick Galbraith and Antony Curtis.

## Creating a Federated Table

As with other storage engines, creating a Federated table involves setting `ENGINE=FEDERATED`. Also necessary with Federated is specifying a connection string of either a connection URL or a server name (the next subsection covers more about Federated servers):

```
CONNECTION=scheme://user:password@host/schema/table
CONNECTION=server
CONNECTION=server/tablename.
```

The following shows the creation of a non-Federated table on a remote data source, and then the creation of a Federated table.

The remote server is 192.168.1.118, and the schema is remote:

```
mysql> CREATE TABLE `t1` (
    ->  `id` int(3) NOT NULL auto_increment,
    ->  `name` varchar(32) NOT NULL default '',
    ->  PRIMARY KEY  (`id`)
    -> );

mysql> INSERT INTO t1 (name) VALUES ('first'), ('second'), ('hello world');
```

Then on a local server, 192.168.1.100, in a schema named federated:

```
mysql> CREATE TABLE `t1` (
    ->  `id` int(3) NOT NULL auto_increment,
    ->  `name` varchar(32) NOT NULL default '',
    ->  PRIMARY KEY  (`id`)
    -> ) ENGINE=FEDERATED
    -> CONNECTION='mysql://feduser:feduser@192.168.1.118/remote/t1';
Query OK, 0 rows affected (0.07 sec)
```

```
mysql> SELECT * FROM t1;
+----+---------------+
| id | name          |
+----+---------------+
|  1 | first         |
|  2 | second        |
|  3 | hello world   |
+----+---------------+
```

```
mysql> INSERT INTO t1 (name) VALUES ('hello federated');
```

```
mysql> SELECT * FROM t1;
+----+---------------+
| id | name          |
+----+---------------+
|  1 | first         |
|  2 | second        |
|  3 | hello world   |
|  4 | hello federated |
+----+---------------+
```

Then back on the remote server:

```
mysql> SELECT * FROM t1;
+----+---------------+
| id | name          |
+----+---------------+
|  1 | first         |
|  2 | second        |
|  3 | hello world   |
|  4 | hello federated |
+----+---------------+
```

This means there has been a successful Federated table creation.

## Federated Servers

As you’ve seen in the preceding example, a URL-like string was specified to give the necessary information for the Federated table in order to connect to the remote data source. In cases where there is a large number of Federated tables, changing these tables’ connection information can be cumbersome and requires altering all of the tables with a modified connection string. For instance, if you needed to change what server 1000 Federated tables connect to, you would have to alter each one of those tables to have a new server in its connection string.

To devise a better solution, in MySQL 5.1, the idea of a Federated Server was developed. This concept was part of the SQL/MED specification. It essentially lets you create a named database object called a SERVER that is associated with various connection meta-data information. The other half of this functionality is that the Federated storage engine can merely specify the server name (as well as table if it is desired to name the table differently than the Federated table). This means you can change the connection information of the table that one or more Federated tables use to connect to their remote data source with a single SQL statement against the SERVER. So, in the 1000-table scenario, not a single table would have to be changed!

The syntax for a Federated Server is straightforward:

```
CREATE SERVER
server_name
FOREIGN DATA WRAPPER wrapper_name
OPTIONS (option [, option] ...)
```

In this example, to use a Federated server, you would create it as:

```
mysql> CREATE SERVER
-> 'servera' FOREIGN DATA WRAPPER 'mysql'
-> OPTIONS
-> (HOST '192.168.1.118',
->   DATABASE 'remote',
->   USER 'feduser',
->   PASSWORD 'feduser',
->   PORT 3306,
->   SOCKET '',
->   OWNER 'root' );
```

Then, to use this server with the previously created table, you would have to drop the table first (this is the Federated standard method; the engine does not support ALTER on the remote table) and then re-create it, using the server name that was just created instead of a URL connection string:

```
mysql> DROP TABLE t1 ;
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> CREATE TABLE `t1` (
->   `id` int(3) NOT NULL AUTO_INCREMENT,
->   `name` varchar(32) NOT NULL DEFAULT '',
->   PRIMARY KEY (`id`)
-> ) ENGINE=FEDERATED DEFAULT CHARSET=latin1 CONNECTION='servera';

mysql> SELECT * FROM t1;
```

| id | name |
|---|---|
| 1 | first |
| 2 | second |
| 3 | hello world |
| 4 | hello federated |

A table name could have been specified in this example and would be separated from the server name with a forward slash '/' .

```
CONNECTION= 'servera/t1'
```

This would be useful if the remote table name and Federated table name differed.

## Federated under the Hood

To gain a little insight to how Federated works, you can observe several things. First, as mentioned before, Federated accesses its data not from a local file, but from a remote data source through the MySQL client library. This means there will only be one file created for a Federated table, the .frm file, which is the table definition file. For Federated, this file merely contains the connection information for the Federated table:

```
ishvara:/home/mysql/var/federated # ls
db.opt  t1.frm
```

The other revealing thing to look at is the SQL log, if it is turned on, on the remote server. On the server with the Federated table, you issue:

```
mysql> SELECT * FROM t1;
```

The query log on the remote server shows:

```
080823 11:17:56        181 Connect      feduser@arjuna on remote
181 Query      SET NAMES latin1
181 Query      SHOW TABLE STATUS LIKE 't1'
181 Query      SELECT `id`, `name` FROM `t1`
```

As you can see:

- The first command the server with the Federated table sends is `SET NAMES <character set>`. This is to ensure that the character set of the Federated table is set on the remote server.
- The second command sent is `SHOW TABLE STATUS`. This command obtains information on the remote table, which Federated then uses to set values for the local Federated table, such as the number of records in the table.
