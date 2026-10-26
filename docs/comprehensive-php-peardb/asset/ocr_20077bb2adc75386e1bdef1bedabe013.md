```
```php
<?php
// make a persistent connection to a MySQL
database, set optimize to 'portability', increase
debug level
$db = DB::connect(
    'mysql://db_user:pass@207.44.182.3/book_test',
    array('persistent' => true, 'optimize' =>
    'portability', 'debug' => 5) );
if (!DB::isError($db)) {
    print 'test 4 success<br>';
    $db->disconnect();
}
?>
```
```

**Code Listing 8: Examples of DB::connect()**

# Query

To perform a query against a database, use the **query()** method. A simple example of using the **query()** method is shown in Code Listing 4. Complete details about this method are given in the discussion of the **DB_common** class below.

# Fetch

After performing a query that returns a data set, there are two basic methods of retrieving the data, **fetchRow()** and **fetchInto()**. Both of these methods are described in detail in the discussion of the **DB_result** class starting on page 109. For a simple example of using **fetchRow()**, see Code Listing 4.

# Sequences

Sequences are a way of maintaining unique numeric IDs for data rows in a table. Several database servers