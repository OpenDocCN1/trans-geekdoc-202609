To create and delete a database, you should have admin privilege. It's very easy to create a new MySQL database. PHP uses **mysql_query** function to create a MySQL database. This function takes two parameters and returns TRUE on success or FALSE on failure.

# ## Syntax

```
bool mysql_query( sql, connection );
```

| Sr.No | Parameter & Description |
|---|---|
| 1 | **sql**<br>Required - SQL query to create a database |
| 2 | **connection**<br>Optional - if not specified, then the last opened connection by mysql_connect will be used. |

# ## Example

Try the following example to create a database –

```
<?php
$dbhost = 'localhost:3036';
$dbuser = 'root';
$dbpass = 'rootpassword';
$conn = mysql_connect($dbhost, $dbuser, $dbpass);
if(! $conn ) {
  die('Could not connect: ' . mysql_error());
}
echo 'Connected successfully';
$sql = 'CREATE Database test_db';
$retval = mysql_query( $sql, $conn );
if(! $retval ) {
  die('Could not create database: ' . mysql_error());
}
```