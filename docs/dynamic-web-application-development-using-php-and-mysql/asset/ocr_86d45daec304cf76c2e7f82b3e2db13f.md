# Sorting records

The ORDER BY attribute can be used to sort the order in which records are obtained, for example:

```
SELECT * FROM customers ORDER BY Surname DESC
```

The ORDER BY attribute is followed by the data field on which to sort the record. In the above example, this is Surname. The attributes DESC or ASC can be specified to indicate whether the sort should be in ascending or descending order. In other words from high to low or low to high.

The following script illustrates the use of the ORDER BY attribute:

```
```php
<?php
// File: example15-12.php

require_once("database2.php");

$dbRecords = mysql_query("SELECT * FROM customers WHERE Title = 'Mr'
ORDER BY Surname DESC", $dbLocalhost)
    or die("Problem reading table: " . mysql_error() );

while ($arrRecords = mysql_fetch_array($dbRecords) ) {
    echo "<p>" . $arrRecords["Id"] . " ";
    echo $arrRecords["Title"] . " ";
    echo $arrRecords["Surname"] . " ";
    echo $arrRecords["Firstname"] . "</p>";
}
?>
```
```

FIGURE 15.8 Sorted output

![](bbox=[0.2, 0.63, 0.9, 0.93])