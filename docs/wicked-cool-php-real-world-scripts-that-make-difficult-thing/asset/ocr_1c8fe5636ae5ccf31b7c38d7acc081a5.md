There are two style classes here for table row tags (<tr>), row1 and row2. As with any CSS, you can place this inside a preexisting CSS file that your document includes or enclose it within <style> </style> tags in your document head.

Now let's define a function that alternately returns these classes. There's a little trick here—you pass an integer variable to this function by reference. The function automatically updates this variable so that you can make repeated calls without worrying about the current state of the table:

```
```php
function table_row_format(&$row_counter) {
    // Returns row class for a row
    if ($row_counter & 1) {
        $row_color = "row2";
    } else {
        $row_color = "row1";
    }
    $row_counter++;
    return $row_color;
}
```
```

Now let's see how to use this function. First, let's set up an SQL query to some rows of data from the table described in the appendix and start the table formatting:

```
```php
$sql = "SELECT product_name FROM product_info";
$result = @mysql_query($sql, $db) or die;

echo "<table>";
```
```

The rest is easy; we just need to initialize the row state variable (here, $i), repeatedly call table_row_format($i) to get the alternating row style classes, and then give each row the correct class attribute. Finally, we close the table:

```
```php
$i = 0;
while($row = mysql_fetch_array($result)) {
    /* Print results. */
    $row_class = table_row_format($i);
    echo "<tr class=\"$row_class\\"><td>$row[product_name]</td></tr>";
}
echo "</table>";
```
```

The key to using the table_row_format() function is understanding how it works. You always initialize an integer variable for the state, but it doesn't matter what the value is, because table_row_format() takes care of it for you.

# # Hacking the Script

There are a million cheap tricks you can do with the style sheet. For more details on CSS, consult the online resource of your choice, or take a look at Cascading Style Sheets: The Definitive Guide, 2nd Edition, by Eric Meyer (O'Reilly