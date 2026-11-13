# # Performing a Query

To execute a SQL query through the DB class, you use the query method. The return value depends on the type of query being executed, but in the event of any error, a DB_Error object is returned, and the error can be detected and diagnosed in the same way as can connection errors.

The following example executes the query stored in $sql with error checking:

```
```php
$res = $db->query($sql);
if (DB::isError($res)) {
    echo "Query error " . $res->getMessage();
    exit;
}
```
```

If the query submitted is an INSERT , UPDATE , or DELETE statement, the return value is the constant DB_OK . You can find out the number of rows affected by the statement by calling the affectedRows method on the database object itself, as shown in the following example:

```
```php
$sql = "UPDATE mytable SET col2 = 'newvalue' WHERE coll > 5";
$res = $db->query($sql);
echo $db->affectedRows() . " row(s) were affected";
```
```

# # Retrieving Selected Data

If you issue a SELECT statement, the return value from the query is a DB_Result object, which can then be used to access records from the result data set.

To view the number of rows and columns in the data set, you use the numRows and numCols methods, respectively, as in this example:

```
```php
$sql = "SELECT * FROM mytable";
$res = $db->query($sql);
echo "Query found " . $res->numRows . " row(s) ".
    "and " . $res->numCols . " column(s)";
```
```

You can use the fetchRow method on a DB_Result object to return a row of data at a time in an array structure. The result pointer is then increased so that each subsequent call to fetchRow returns the next row of data, in order. The following code shows how you can fetch all the rows returned by a query by using fetchRow in a loop:

```
```php
$sql = "SELECT coll, col2 FROM mytable";
$res = $db->query($sql);
while ($row = $res->fetchRow()) {
    echo "coll = " . $row[0] . ", ";
    echo "col2 = " . $row[1] . "<br>";
}
```
```