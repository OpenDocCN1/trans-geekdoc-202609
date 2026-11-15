
}
echo "Value entered!";
sqlsrv_close($db);
} else {
echo "Error!";
}
}
?>
<form method="post" action="">
<input type="text" name="value" />
<input type="submit" value="Enter" />
</form>

## Listing 21.5 Parameterized Queries with the Microsoft Driver ("sqlsrv-parameter.php")

## Last Inserted Autovalue

Because MSSQL offers an autovalue via IDENTITY, it is naturally obvious to wonder how the last autovalue inserted can be determined. The command is SELECT @@IDENTITY FROM my_table. However, you should make sure that you perform the insertion and readout in one go—for example, in a transaction (this is done by the sqlsrv_begin_transaction() and sqlsrv_commit() functions). As an example, however, it is also sufficient to send two commands in succession. The following code inserts another value into the test table and reads the autovalue. In the SELECT command, we do not use an alias via AS, so we need the query to be returned as a numeric array.

## Listing 21.6 Read Out the Last Autovalue ("sqlsrv-read-autovalue.php")

```php
<?php
if ($db = sqlsrv_connect(
"(local)\\SQLEXPRESS",
["Database" => "PHP"])) {
$sql = "SELECT * FROM my_table";
$sql = "INSERT INTO my_table (field) VALUES ('value3')";
if (sqlsrv_query($db, $sql)) {
echo "Data entered.<br />";
} else {
echo "Error!";
}
$sql = "SELECT @@IDENTITY FROM my_table";
if ($result = sqlsrv_query($db, $sql)) {
sqlsrv_fetch($result);
$id = sqlsrv_get_field($result, 0);
echo "Data entered with ID $id.";
} else {
echo "Error!";
}
sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

## Information about the Result

After a SQL statement, you can use other auxiliary functions to obtain further information about the result of the query. For example, sqlsrv_rows_affected() returns the number of database rows affected by the query (i.e., the number of rows updated by UPDATE or deleted by DELETE or inserted by INSERT). For SELECT *, sqlsrv_num_rows() returns the number of fields in the result list (see also the “Other Useful Functions” section ahead).

## Stored Procedures

With stored procedures, which some people refer to as embedded procedures, it is possible to encapsulate several database queries directly within the database in blocks. This is common practice in many web agencies: a database administrator is the only person who has full access to the database; web applications (and their developers) are only allowed to call special stored procedures. This avoids a lot of trouble during development.

The previous example with the insertion and return of the autovalue is implemented in a stored procedure as follows procedure:

```sql
CREATE PROCEDURE pr_insert (
@value VARCHAR(50)
)
AS
INSERT INTO my_table (field) VALUES (@value)
SELECT @@IDENTITY FROM my_table
GO
```

You can insert this stored procedure using a tool—or you can also have it inserted by a PHP script, as in the following listing.

## Listing 21.7 Create the Stored Procedure ... ("sqlsrv-sp-create.php")

To execute the stored procedure, execute it in the SQL code with EXEC or CALL, as in the following complete listing.

## Listing 21.8 ... and Call ("sqlsrv-sp-call.php")

```php
<?php
if ($db = sqlsrv_connect(
"(local)\\SQLEXPRESS",
["Database" => "PHP"])) {
$sql = "call pr_insert(?)";
$value = "value4";
$parameter = [
    [$value, SQLSRV_PARAM_IN]
];
if ($result = sqlsrv_query($db, $sql, $parameter)) {
echo "Stored procedure called.";
} else {
echo "Error!";
}
sqlsrv_close($db);
} else {
echo "Error!";
}
?>
```

## Other Useful Functions

The SQL Server Driver for PHP API is of course more extensive than previously presented. Here are some more useful functions:

- **sqlsrv_has_rows()** Determines whether a results list contains any data at all
- **sqlsrv_num_rows()** The number of rows in the result list
- **sqlsrv_server_info()** Information about the database (as an associative array with version number and so on)

There is potential in the Microsoft driver, as it is being developed very actively, unlike the mssql extension. However, the question remains whether it will eventually become an official part of PHP or whether it will remain a proprietary Microsoft "product" as the code is open source.

## 21.3 Application Example

The chapter concludes with the obligatory guestbook example. The same advice we gave in the previous chapters applies here, as well: set the authorizations correctly and adjust the parameters of `sqlsrv_connect()` if necessary.

### 21.3.1 Create Table

To create the table, it is best to send the associated statement directly to the database using `sqlsrv_query()`. Alternatively, you can also use the Management Studio or a comparable tool.

## Listing 21.9 The Table Is Created ("gb-create.php")

```php
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
    $sql = "CREATE TABLE guestbook (
    id INT IDENTITY NOT NULL,
    heading VARCHAR(1000),
    entry VARCHAR(5000),
    author VARCHAR(50),
    email VARCHAR(100),
    date DATETIME,
    PRIMARY KEY (id)
    )";
    if (sqlsrv_query($db, $sql)) {
    echo "Table created.<br />";
    } else {
    echo "Error!";
    }
    sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

### 21.3.2 Enter Data

To enter the data into the database, create a prepared statement to avoid SQL injection. With SELECT @@IDENTITY, the autovalue of the insertion process is determined (and output).

The following listing shows the code for manual insertion.

## Listing 21.10 Data Can Be Entered ("gb-enter.php")

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
isset($_POST["Email"]) &&
isset($_POST["Heading"]) &&
isset($_POST["Comment"])) {
if ($db = sqlsrv_connect(
"(local)\\SQLEXPRESS",
["Database" => "PHP"])) {
$sql = "INSERT INTO guestbook
(heading,
entry,
author,
email,
date)
VALUES (?, ?, ?, ?, ?)";
$date = date("Y-m-d H:i:s");
$parameter = [
&$_POST["Heading"],
&$_POST["Comment"],
&$_POST["Name"],
&$_POST["Email"],
$date,
];
if ($command = sqlsrv_prepare($db, $sql, $parameter)) {
if (sqlsrv_execute($command)) {
$result = sqlsrv_query($db, "SELECT @@IDENTITY");
sqlsrv_fetch($result);
$id = sqlsrv_get_field($result, 0);
echo "Entry added.
<a href=\"gb-edit.php?id=$id\">Edit</a>";
} else {
echo "Error!";
}
} else {
echo "Error!";
}
sqlsrv_close($db);
} else {
echo "Error!";
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /> <br />
Email address <input type="text" name="Email" /> <br />
Heading <input type="text" name="Heading" /> <br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

### 21.3.3 Output Data

To output the data, you can use one of the sqlsrv_fetch_* functions. We use the object variant here, but how you proceed is purely a matter of taste.

## Listing 21.11 The Guestbook Data Is Output ("gb-show.php")

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
    $sql = "SELECT * FROM guestbook ORDER BY date DESC";
    $result = sqlsrv_query($db, $sql);
    while ($row = sqlsrv_fetch_object($result)) {
        printf("<p><a href=\"mailto:%s\">%s</a> wrote on/at %s:</p>
<h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
            urlencode($row->email),
            htmlspecialchars($row->author),
            htmlspecialchars($row->date->format("Y-m-d H:i:s")),
            htmlspecialchars($row->heading),
            nl2br(htmlspecialchars($row->entry)));
    }
    sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
</body>
</html>
```

### Figure 21.4 The Entries in the Guestbook

![](img/ae7820c36e8f24c1623d26668b28e80e_633_0.png)
