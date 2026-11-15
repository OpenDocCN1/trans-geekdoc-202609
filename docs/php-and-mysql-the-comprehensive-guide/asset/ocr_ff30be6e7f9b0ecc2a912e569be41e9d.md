| Module | Function |
| :--- | :--- |
| MySQL | mysqli_real_escape_string()/MySQLi::real_escape_string() |
| SQLite | SQLite3::escapeString() |
| MSSQL | - |
| PostgreSQL | pg_escape_string() |
| Oracle | - |

Table 32.1 Functions for Escaping Special Characters

As you can see, things look rather bleak for some database systems—but fortunately, these offer the preferred prepared statements as a secure approach anyway. The following listing shows an example in MySQL using the mysqli extension of PHP.

```
<?php
$entry = $_POST["entry"] ?? "";

if ($db = mysqli_connect("server", "user", "password",
    "guestbook")) {
if ($stmt = mysqli_prepare($db,
    "INSERT INTO entries (entry) VALUES (?)")) {
    mysqli_stmt_bind_param($stmt, "s", $entry);
    mysqli_stmt_execute($stmt);
    mysqli_stmt_close($stmt);
}
    mysqli_close($db);
}
?
<html>
<head>
    <title>Guestbook</title>
</head>
<body>
    <form method="post" action="">
        Comment: <textarea name="entry" cols="" rows=""></textarea><br />
        <input type="submit" value="Enter" />
    </form>
</body>
</html>
```

Listing 32.4 A Better Script for Entering ("gb-enter-2.php")