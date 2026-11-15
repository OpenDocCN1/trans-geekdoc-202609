![](bbox=[0.143, 0.1, 0.86, 0.228])

# Figure 20.2 All Entries in the Mini Database

Fans of modern PHP versions (hopefully all of them!) may object that this is all well and good, but PHP offers the concept of iterators. Wouldn't it have been great if the developers of the SQLite library for PHP had integrated them? Rejoice! The developers actually did think of this, so you can iterate through a result list using foreach(), as in the following listing.

```
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "SELECT * FROM my_table";
    $result = $db->query($sql);
    echo "<ul>";
    foreach ($result as $row) {
        echo "<li>" . htmlspecialchars($row["id"]) .
             ": " . htmlspecialchars($row["field"]) . "</li>" ;
    }
    echo "</ul>";
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

# Listing 20.5 Read Out Data via Iterator ("sqlite-read-iterator.php")

Finally, we would like to point out a special variant of the query that can bring an additional performance gain. We are talking about a SELECT query that only has a single return value (or where you are only interested in the values in the first column of the result).

PHP has a special method for both: querySingle() sends a query to the database and returns the value in the first column or (as an array) the complete first row.

If you execute querySingle() with "SELECT * FROM my_table" on the example table, you will receive the value from the first column—that is, the id column. If you are only interested in the first data record of the results list and want to get it back in full, you must pass true as the second parameter.