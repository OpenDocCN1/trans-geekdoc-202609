# Introducing MySQL's Privilege System 227

The columns placeholder is optional. You can use it to specify privileges on a column-by-column basis. You can use a single column name or a comma-separated list of column names.

The item placeholder is the database or table to which the new privileges apply. You can grant privileges on all the databases by specifying * as the item. This is called granting global privileges. You can also do this by specifying * if you are not using any particular database. More commonly, you can specify all tables in a database as dbname.*, on a single table as dbname.tablename, or on specific columns by specifying dbname.tablename and These examples represent the three levels of privilege available: database, table, and column, respectively. If you are using a specific database when you issue this command, tableName on its own will be interpreted as a table in the current database.

The REQUIRE clause allows you to specify that the user must connect via Secure Socket Layer (SSL) and specify SSL options. For more information on SSL connections to MySQL, refer to the MySQL manual.

The WITH GRANT OPTION option, if specified, allows the specified user to grant his or her own privileges to others.

You can instead specify the WITH clause as

```
MAX_QUERIES_PER_HOUR n
```

or

```
MAX_UPDATES_PER_HOUR n
```

or

```
MAX_CONNECTIONS_PER_HOUR n
```

or

These clauses allow you to limit the number of queries, updates per hour or simultaneous connections a user may make. They can be useful for limiting individual user load on shared systems.

Privileges are stored in six system tables, in the database mysql. These six tables are called mysql.user, mysql.db, mysql.host, mysql.tables_priv, mysql.columns_priv, and mysql.process_priv. As an alternative to GRANT, you can alter these tables directly. We discuss exactly how these tables work and how you can alter them in Chapter 12, "Advanced MySQL Administration."

# Types and Levels of Privileges

Three basic types of privileges in MySQL: privileges suitable for granting to regular users, privileges suitable for administrators, and a couple of special privileges. Any user can be granted any of these privileges, it's usually sensible to restrict the administrator type privileges to administrators, according to the principle of least privilege.