
## 21.2 Microsoft SQL Server Driver for PHP

Microsoft has been active at PHP conferences for many years, promoting web servers (IIS), databases (SQL Server), and cloud technology (Azure) from Redmond, among other things. The company's position is of course somewhat delicate, as it also produces ASP.NET, one of PHP's main competitors.

However, many of Microsoft's contributions to PHP development are very well received by the community. These include the significantly improved Windows builds. Microsoft SQL Server Driver for PHP is not part of the PHP core itself but is nevertheless an exciting extension. This is Microsoft's own PHP extension for working with its own SQL Server. Sensationally, this extension runs not only on Windows, but also on macOS and Linux! The source code for the extension has also been available on GitHub at https://github.com/Microsoft/msphpsql for some time now.

In this section, we will briefly show you how the current version 5.12.0 of the driver works. This supports PHP versions from 8.1 to 8.3. You can find these and older (and possibly newer!) versions of the extension for download at https://github.com/Microsoft/msphpsql/releases, somewhat hidden under Assets (see Figure 21.2).

![](img/ae7820c36e8f24c1623d26668b28e80e_621_0.png)

Figure 21.2 Download the Extension for SQL Server on GitHub

In the following examples, we use the Windows package. The archive contains extensions for 32-bit (x86) and 64-bit (x64) PHP versions. Here are the files for PHP 8.3:

- php_pdo_sqlsrv_83_nts_x86.dll
- php_pdo_sqlsrv_83_nts_x64.dll
- php_pdo_sqlsrv_83_ts_x86.dll
- php_pdo_sqlsrv_83_ts_x64.dll
- php_sqlsrv_83_nts_x86.dll
- php_sqlsrv_83_nts_x64.dll
- php_sqlsrv_83_ts_x86.dll
- php_sqlsrv_83_ts_x64.dll

As you can see from the file names, you have to make two decisions:

- The type of web server. Here, `ts` stands for *thread-safe*, `nts` for *not thread-safe*. If you use the IIS as a web server, you can use the non-thread-safe versions. These are more performant than the thread-safe versions that you need for Apache, for example.
- Whether you use PDO (the first two files) or go directly to the SQL server via an extension.

Copy the appropriate file for your system into the PHP extension directory and add a corresponding instruction to `php.ini`–for example:

```
extension=php_sqlsrv_83_nts_x64.dll
```

You also need the Microsoft ODBC Driver for SQL Server in at least version 13 (the current version is 18). The corresponding link is http://s-prs.co/v60226.

If everything went well, you will find an entry for the `sqlsrv` extension in the output of `phpinfo()` (see Figure 21.3).

![](img/ae7820c36e8f24c1623d26668b28e80e_622_0.png)

Figure 21.3 The Microsoft Extension Is Installed

> **Note: Functions or Methods?**
> Installation instructions for other operating systems and further information can be found on the aforementioned project page at https://github.com/Microsoft/msphpsql.

### 21.2.1 Connection Setup

The API of the sqlsrv extension is similar to that of other database extensions such as mysqli, but there are a few differences. This can already be seen when establishing a connection. The function responsible for this, sqlsrv_connect(), expects only two parameters: the server name and an array with connection options. In the simplest case, you simply specify the server name; the current Windows user under which the PHP script is running then only requires the corresponding database authorizations:

```
sqlsrv_connect("(local)\\SQLEXPRESS")
```

You must specify the database you want to access in the second parameter:

```
sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"]);
```

If you do want to connect to the server using a user name and password, you can use the following syntax:

```
sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["UID" => "user", "PWD" => "password"]);
```

The following listing shows a simple example that only establishes a connection to the server.

```
<?php
if ($db = sqlsrv_connect("(local)\\SQLEXPRESS")) {
    echo "Connection successful.";
    sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

Listing 21.1 Connection Setup with the Microsoft Driver ("sqlsrv-connect.php")

> Tip
> As in the previous chapters, we have dispensed with "proper" error handling for reasons of clarity. The sqlsrv_errors() function, for example, returns all error information.

### 21.2.2 Queries

To send a query to the SQL server database, use the sqlsrv_query() function. Two arguments are required: the database connection (returned by sqlsrv_connect()) and the SQL command. You can see an example in the following listing.

```
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
$sql = "CREATE TABLE my_table (
    id INT IDENTITY NOT NULL,
    field VARCHAR(255)
)";
if (sqlsrv_query($db, $sql)) {
    echo "Table created.<br />";
} else {
    echo "Error!";
}
$sql = "INSERT INTO my_table (field) VALUES ('Value1')";
if (sqlsrv_query($db, $sql)) {
    echo "Data entered.<br />";
} else {
    echo "Error!";
}
$sql = "INSERT INTO my_table (field) VALUES ('Value2')";
if (sqlsrv_query($db, $sql)) {
    echo "Data entered.";
} else {
    echo "Error!";
    die(print_r( sqlsrv_errors(), true));
}
sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

Listing 21.2 Create and Fill Table with the Microsoft Driver ("sqlsrv-query.php")

### 21.2.3 Return Values

When reading return values, the while loop is used again, which iterates over the returns from a database function. This function is called sqlsrv_fetch_array() in the sqlsrv extension. This leads to the code in the following listing.

```
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
$sql = "SELECT * FROM my_table";
if ($result = sqlsrv_query($db, $sql)) {
echo "<ul>";
while ($row = sqlsrv_fetch_array($result)) {
    echo "<li>" . htmlspecialchars($row["id"]) .
         ": " . htmlspecialchars($row["field"]) . "</li>";
}
echo "</ul>";
sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

Listing 21.3 All Query Data as an Associative Array with the Microsoft Driver ("sqlsrv-read.php")

Reading using objects is very similar, but the function name changes from sqlsrv_fetch_array() to sqlsrv_fetch_object() and the access from $row["column"] to $row->column.

```
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
    $sql = "SELECT * FROM my_table";
    if ($result = sqlsrv_query($db, $sql)) {
        echo "<ul>";
        while ($row = sqlsrv_fetch_object($result)) {
            echo "<li>" . htmlspecialchars($row->id) .
                 ": " . htmlspecialchars($row->field) . "</li>";
        }
        echo "</ul>";
    }
    sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

Listing 21.4 All Query Data as Object ("sqlsrv-read-object.php")

### Alternative Fetch Method

There is another method for reading data, sqlsrv_fetch(), which reads in a data record from the results list but does not initially offer a return value. However, you can then use sqlsrv_get_field() to access individual columns of the data set via their number, as follows:

```
while (sqlsrv_fetch($result)) {
 echo "<li>" . htmlspecialchars(sqlsrv_get_field($result, 0)) .
 " : " . htmlspecialchars(sqlsrv_get_field($result, 1)) . "</li>";
}
```

### 21.2.4 Special Features

In addition to the "classic" use cases shown previously, the sqlsrv extension also offers numerous advanced features, the most important of which are presented ahead, each with a short code example.

### Prepared Statements

Of course, the sqlsrv extension also offers parameterized queries. For this, you must first create a command object. Use question marks as placeholders in the SQL code:

```
$sql = "INSERT INTO my_table (field) VALUES (?)";
```

With sqlsrv_prepare(), you create the command object. You pass the values for the placeholders as an array, even if you only use one placeholder as in the example. Note that the values in the array must be transferred as a reference or you will receive a warning:

```
$value = "123";
$stmt = sqlsrv_prepare($db, $sql, [&$value]);
```

In the last step, execute the command with sqlsrv_execute():

```
sqlsrv_execute($stmt);
```

The following listing shows a related example that allows users to add additional values to the database using a small HTML form.

```
<?php
if (isset($_POST['value']) && is_string($_POST['value'])) {
 if ($db = sqlsrv_connect(
     "(local)\\SQLEXPRESS",
     ["Database" => "PHP"])) {
     $sql = "INSERT INTO my_table (field) VALUES (?)";
     $stmt = sqlsrv_prepare($db, $sql, [&$_POST['value']]);
     if (sqlsrv_execute($stmt)) {
         echo "Data entered.<br />";
     } else {
         echo "Error!";
     }
}
```
