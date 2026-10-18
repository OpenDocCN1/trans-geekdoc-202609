NOTE
If you wish to obtain more than one field you can do so by listing them in the SQL statement separated by a comma, for example:

SELECT Surname,Firstname FROM customers

# Selecting a certain number of records

We can also modify the SELECT statement so that it uses the LIMIT option. We can use LIMIT to select a certain number of records from a table:

```
SELECT * FROM customers LIMIT 3,4
```

The LIMIT option has two parameters: the first one represents the starting row (where 0 is the first row) and the second represents the number of records to be selected after the starting row. So in the above example, the first record retrieved will be the fourth record and only four will be obtained from that point. Here is the statement in a script:

```
<?php
// File: example15-9.php

require_once("database2.php");

$dbRecords = mysql_query("SELECT * FROM customers LIMIT 3,4", $dbLocalhost)
    or die("Problem reading table: " . mysql_error() );

while ($arrRecords = mysql_fetch_array($dbRecords) ) {
    echo "<p>" . $arrRecords["Id"] . " ";
    echo $arrRecords["Title"] . " ";
    echo $arrRecords["Surname"] . " ";
    echo $arrRecords["Firstname"] . "</p>";
}
?>
```

The output from the above script is illustrated in Figure 15.5.

# FIGURE 15.5 Limiting the records retrieved

![](bbox=[0.08, 0.74, 0.79, 0.94])