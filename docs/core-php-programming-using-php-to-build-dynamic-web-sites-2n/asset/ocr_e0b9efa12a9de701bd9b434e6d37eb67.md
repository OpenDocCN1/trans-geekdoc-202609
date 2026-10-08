# Core PHP Programming

The pg_options function returns the options used when the connection was opened. See pg_exec for an example of use.

# integer pg_connect(string host, string port, string options, string tty, string database)

The pg_connect function operates identically to pg_connect, except that a persistent connection is created. This connection will last as long as the server process, so it may be recycled. This saves the overhead time of opening a connection.

```
<?\n$Connection = pg_connect(", "", "", "leon");
?>
```

# integer pg_port(integer connection)

The pg_port function returns the port number used in the pg_connect function. See pg_exec for an example of use.

# string pg_result(integer result, integer row, string field)

Use pg_result to get the value of a specific field in a result set. Rows and fields are numbered from zero, but fields may also be specified by name. See pg_exec for an example of use.

# string pg_tty(integer connection)

The pg_tty function returns the tty name used for debugging and supplied with the pg_connect function. See pg_exec for an example of use.

# Sybase

Sybase offers an industrial-strength database that stands among other big competitors like Oracle, Informix, and IBM's DB. Unlike these other databases, Sybase is more available to developers with small budgets because of partnerships with application vendors. InterShop's ecommerce server comes with a Sybase database. Microsoft's SQL Server 6.5 is a dressed-up version of Sybase. In fact, PHP's Sybase functions are able to connect to SQL Server databases. For the sake of code readability, there are function aliases for all the Sybase functions that start with msql_ instead of sybase_, but I've left them out of the reference to save space. Table 13.13 lists all msql_ aliases.

| Table 13.11. MSSQL Functions |
|---|
| mssql_close |