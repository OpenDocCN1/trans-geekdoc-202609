# # Prepared Statements

In database-based applications, many times the same query will be executed repeatedly using just slightly different parameters. For example, a query that paginates some results varies in its LIMIT clause:

```
```sql
SELECT * FROM tablename LIMIT 0, 20
SELECT * FROM tablename LIMIT 20, 20
SELECT * FROM tablename LIMIT 40, 20
```
```

An INSERT query varies in the values being inserted:

```
```sql
INSERT INTO tablename (column1, column2) VALUES ('value1', 'value2')
INSERT INTO tablename (column1, column2) VALUES ('valueX', 'valueY')
```
```

Unlike those five queries, which include the table references and the data to be used, a prepared statement separates the static content from the dynamic values, using placeholders for the latter:

```
```sql
SELECT * FROM tablename LIMIT ?, 20
INSERT INTO tablename (column1, column2) VALUES (?, ?)
```
```

The database is then asked to “prepare” the statement, at which point the database will confirm that the query is syntactically valid (assuming that values will later be provided for each placeholder). There can be a performance benefit to this approach, since the database can cache the preparation of the query, making subsequent uses of the same prepared statement faster. The next steps provide a value for all the placeholders and execute the query.

In terms of your PHP code, this is how you go about using a prepared statement...

**tip**

This query comes from Chapter 4, “User Accounts.”

Start by defining the query, using question marks to indicate the values to be provided later. For example, if the site had a login functionality, its query might look like:

```
```php
$q = 'SELECT id, username, type, IF(date_expires >= NOW(), true, false)
   FROM users WHERE (email=? and password=?);';
```
```

Then, call the mysqli_prepare() function, providing it with the database connection and the query:

```
```php
$stmt = mysqli_prepare($dbc, $q);
```
```

**note**

It’s very important that you don’t quote any placeholders, even if their values will be strings.

This function returns a MySQLi_STMT object, which will be used by later functions.