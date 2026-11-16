+   1. It creates a new prepared statement on the database using the provided SQL statement. The database parses and compiles the statement, then stores it ready for execution.

+   2. In a second separate step, DB.Exec() passes the parameter values to the database. The database then executes the prepared statement using these parameters. Because the parameters are transmitted later, after the statement has been compiled, the database treats them as pure data. They can’t change the intent of the statement. So long as the original statement is not derived from untrusted data, injection cannot occur.

+   3. It then closes (or deallocates) the prepared statement on the database.

The placeholder parameter syntax differs depending on your database. MySQL, SQL Server and SQLite use the ? notation, but PostgreSQL uses the $N notation. For example, if you were using PostgreSQL instead you would write:

```
_,\ err := m.DB.Exec("INSERT INTO ... VALUES ($1, $2, $3)", ...)
```