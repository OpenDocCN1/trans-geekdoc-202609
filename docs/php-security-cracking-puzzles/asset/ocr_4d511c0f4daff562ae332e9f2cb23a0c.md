# Chapter II.4: MySQL and SQL Injections 209

```
// If there are items for the given
// letter, displaying them
if (mysql_num_rows($prd) > 0)
{
    while ($product = mysql_fetch_array($prd))
    {
        echo "<a href=\$SERVER[PHP_SELF]?letter=$product[letter]'>$product[letter]</a>";
    }
}
```

```
// If a one-letter parameter was passed,
// displaying the contents of the table
if (preg_match("^[a-z]$/i, $_GET['letter']))
{
    // Displaying a spare parts list
    $query = "SELECT * FROM products
    WHERE SUBSTRING(name,1,1) = '$GET[letter]'
    ORDER BY price";
    $prd = mysql_query($query);
    if(!$prd) exit (mysql_error());
    // If the current directory contains least
    // one item, displaying the item
    if (mysql_num_rows($prd) > 0)
    {
        echo "<br><table> border=1>
        <tr>
        <td>Product Name</td>
        <td>Price</td>
        </tr>";
        while($product = mysql_fetch_array($prd))
        {
            echo "<tr>
            <td>$product[name]</td>
            <td>$product[price]</td>
        </tr>";
        }
        echo "</table>";
    }
}
```