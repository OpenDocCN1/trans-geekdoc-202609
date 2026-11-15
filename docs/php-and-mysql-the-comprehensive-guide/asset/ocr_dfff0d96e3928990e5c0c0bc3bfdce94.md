# ## 20.2.4 Special Features

Although SQLite is a a rather small database—the C library consists of 200,000 lines of code (including comments), which is not much—it does offer some useful additional features, a few of which will be briefly presented here.

# ### Determine the Last Autovalue

The SQLite INTEGER PRIMARY KEY data type is an autovalue. This means that if you insert an element into a table with this value, it automatically receives a new ID. However, it is usually difficult to determine this ID—so difficult that some abstraction libraries do not even offer the functionality.

There are a few possible solutions, but they all have their pitfalls:

+   - Insert the new value and immediately afterward execute a SELECT statement in which you sort in descending order by ID. The last element added has the highest ID. Unfortunately, this does not work if, for example, another script also executes an INSERT statement directly after your INSERT statement: You will then receive the "other" ID.
+   - Create a transaction in which you execute first the INSERT statement and then the SELECT statement. This works if the database actually always increments the IDs. However, it is also possible that IDs that have become free (due to the deletion of data records) are used again later—even if primary keys should actually be permanently unique.
+   - Insert a value into the database and search for it using SELECT. This works so long as the values are all unique (rather unrealistic).
+   - Insert a value into the database and save a unique value in another database field—for example, a timestamp plus a few random characters. Then search for the value using SELECT.

This is sometimes quite complicated, but it can be much simpler. The lastInsertRowID() method returns the ID of the last inserted value for a database handle (see Figure 20.3)—if the table has an autovalue field at all.

```
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "INSERT INTO my_table (field) VALUES ('value3')";
    if ($db->exec($sql)) {
        $id = $db->lastInsertRowID();
        echo "Data with ID $id entered.";
    } else {
        echo "Error!";
    }
    $db->close();
}
```