# # The PDO Class

You probably noticed in the previous example that there’s no “connect” method in PDO, nor is there any “disconnect” method. This is quite deliberate. The act of instantiating a new instance of the global PDO class establishes a connection to the database. Disconnecting happens automatically at the end of the script or, alternatively, when the class is destroyed by setting it to null.

As a result, connecting to the database is a simple as the following:

```
$objPDO = new PDO($strDSN);
```

Disconnecting is as simple as this:

```
$objPDO = NULL;
```

As such, the PDO class itself is best described as a symbolic representation of a database connection; an instance of the class can only exist once a connection has been established.

You'll doubtlessly notice the single parameter you are passing to the constructor of the PDO class. This is known as a database source name (DSN). This is a concatenated string that describes the protocol, hostname, username, password, port, and database name. In some cases, other parameters can be passed, and in other cases, parameters can be omitted and the default assumed (such as in the case of TCP/IP port, which in the case of PostgreSQL is usually 5432).

PDO supports a handful of formats for valid DSN strings, but the following is the most common:

```
protocol:key=value;key=value;key=value [etc]
```

Here, protocol refers to the PDO driver to use — pgsql for PostgreSQL, mysql for MySQL, mssql for MS SQL Server, and oci for Oracle.

Each key/value pair is used to specify a particular attribute for the connection. They are many and varied, but the following are most commonly used:

+   - host — Hostname of the database (or IP address)
+   - user — Username
+   - password — Password (plain text)
+   - port — TCP/IP port (only supported if not connecting to localhost)
+   - dbname — Database name

For a full list of parameters for the database of your choice, refer to the PHP manual’s database of supported drivers at www.php.net/manual/en/pdo.drivers.php. After choosing your driver, you will see a list of supported parameters enumerated.