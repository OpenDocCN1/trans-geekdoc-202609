```
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

# Listing 21.3 All Query Data as an Associative Array with the Microsoft Driver ("sqlsrv-read.php")

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

# Listing 21.4 All Query Data as Object ("sqlsrv-read-object.php")

# Alternative Fetch Method

There is another method for reading data, sqlsrv_fetch(), which reads in a data record from the results list but does not initially offer a return value. However, you can