```
```php
$qry_result = mysql_query($query) or die(mysql_error());

//Build Result String
$display_string = "<table>";
$display_string .= "<tr>";
$display_string .= "<th>Name</th>";
$display_string .= "<th>Age</th>";
$display_string .= "<th>Sex</th>";
$display_string .= "<th>WPM</th>";
$display_string .= "</tr>";

// Insert a new row in the table for each person returned
while($row = mysql_fetch_array($qry_result)){
    $display_string .= "<tr>";
    $display_string .= "<td>$row[name]</td>";
    $display_string .= "<td>$row[age]</td>";
    $display_string .= "<td>$row[sex]</td>";
    $display_string .= "<td>$row[wpm]</td>";
    $display_string .= "</tr>";
}

echo "Query: " . $query . "<br />";
$display_string .= "</table>";
echo $display_string;
?>
```
```

Now enter a valid value in "Max Age" or any other box and then click Query MySQL button.

![](bbox=[0.123, 0.655, 0.877, 0.78])

If you have successfully completed this lesson, then you know how to use MySQL, PHP, HTML, and Javascript in tandem to write Ajax applications.