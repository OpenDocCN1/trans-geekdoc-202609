As can be seen in Fig. II.4.13, in the first drop-down list the item selected corre- sponds to the primary key 2 of the catalogs table. Therefore, only the product2 list, whose value is ten, carries meaningful information. All other elements of the $ _POST array do not matter.

# II.4.10. Deleting Several Items Simultaneously

To delete several items from the products table, the following SQL query must be constructed:

```
DELETE FROM products WHERE id product IN (4, 6, 8, ..., 20)
```

This query removes all records with a value for the id_product primary key that matches one of the values in the IN operator.

# II.4.32. Deleting several items from the products table simultaneously

```
<?php
// Connecting to the database
require_once("config.php");

// Displaying a spare parts list
$query = "SELECT * FROM products
ORDER BY name";
$prd = mysql_query($query);
if(!$prd) exit(mysql_error($query));
// If the current catalog contains at least
// one item, displaying the item
if (mysql_num_rows($prd) > 0)
{
    echo "<table border = 1>
<<tr>
<td>&nbsp;</td>
<td>Name</td>
<td>Price</td>
<td>Grade</td>
<td>Qty</td>
</tr>";n    // ... loop continues
}

$i = 0;
```