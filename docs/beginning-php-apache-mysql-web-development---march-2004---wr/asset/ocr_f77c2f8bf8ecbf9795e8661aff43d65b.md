# Online Selling: A Quick Way to E-Commerce

```
echo "<td>\necho "<form method='POST' action='delete.php'>
<input type='hidden' name='prodnum'
value='$prodnum'>
<input type='hidden' name='qty' value='$qty'>
<input type='hidden' name='hidden'
value='$hidden'>
<input type='hidden' name='sessid'
value='$sessid'>\necho "<input type='submit' name='Submit'
value='Delete Item'>
</form></td>";
```

We give customers the option of proceeding to the checkout or going back to the main page for more shopping with these lines:

```
<form method='POST' action='checkout.php'>
<input type='submit' name='Submit' value='Proceed to Checkout'>
</form>
<a href='cbashop.php'>Go back to the main page</a>
```

# Try Out Changing Items in the Cart

Let's go ahead and type change.php:

```
<?php
session_id();
session_start();
$connect = mysql_connect('localhost', 'root', '$mysqlpass') or
die ('Hey loyser, check your server connection.');
mysql_select_db ('ecommerce');
$qty = $_POST['qty'];
$hidden = $_POST['hidden'];
$sess = $_POST['sessid'];

$query = 'UPDATE cart temp
SET quan = '$qty'
WHERE hidden = '$hidden';
$results = mysql_query($query)
or die(mysql_error($results));

echo "Quantity Updated.<br>\ninclude(\'cart.php');";
?>
```

And delete.php:

```
<?php
session_id();
session_start();
$connect = mysql_connect('localhost', 'root', '$mysqlpass') or
die ('Hey loyser, check your server connection.');
mysql_select_db ('ecommerce');
$qty = $_POST['qty'];
```